---
title: ATOMIC 块 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 40e0e749-260c-4cfc-a848-444d30c09d85
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ca8f5b4d767ef0fe836cd260f8d12dd5b40c75d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578199"
---
# <a name="atomic-blocks"></a><span data-ttu-id="ee624-102">ATOMIC 块</span><span class="sxs-lookup"><span data-stu-id="ee624-102">Atomic Blocks</span></span>
  <span data-ttu-id="ee624-103">`BEGIN ATOMIC` 属于 ANSI SQL 标准。</span><span class="sxs-lookup"><span data-stu-id="ee624-103">`BEGIN ATOMIC` is part of the ANSI SQL standard.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ee624-104">仅在本机编译存储过程的顶级支持原子块。</span><span class="sxs-lookup"><span data-stu-id="ee624-104">supports atomic blocks only at the top-level of natively compiled stored procedures.</span></span>  
  
-   <span data-ttu-id="ee624-105">每个本机编译的存储过程都恰好包含一个 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句块。</span><span class="sxs-lookup"><span data-stu-id="ee624-105">Every natively compiled stored procedure contains exactly one block of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="ee624-106">这个语句块是原子块。</span><span class="sxs-lookup"><span data-stu-id="ee624-106">This is an ATOMIC block.</span></span>  
  
-   <span data-ttu-id="ee624-107">非本机的解释型 [!INCLUDE[tsql](../../includes/tsql-md.md)] 存储过程和即席批处理不支持原子块。</span><span class="sxs-lookup"><span data-stu-id="ee624-107">Non-native, interpreted [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedures and ad hoc batches do not support atomic blocks.</span></span>  
  
 <span data-ttu-id="ee624-108">原子块在事务内执行（以原子方式）。</span><span class="sxs-lookup"><span data-stu-id="ee624-108">Atomic blocks are executed (atomically) within the transaction.</span></span> <span data-ttu-id="ee624-109">或者块中的整个语句都成功，或者整个块都将回滚到在块的开始处创建的保存点。</span><span class="sxs-lookup"><span data-stu-id="ee624-109">Either all statements in the block succeed or the entire block will be rolled back to the savepoint that was created at the start of the block.</span></span> <span data-ttu-id="ee624-110">此外，会话设置对于原子块而言是固定的。</span><span class="sxs-lookup"><span data-stu-id="ee624-110">In addition, the session settings are fixed for the atomic block.</span></span> <span data-ttu-id="ee624-111">以不同设置在会话中执行相同的原子块将导致相同的行为，与当前会话的设置无关。</span><span class="sxs-lookup"><span data-stu-id="ee624-111">Executing the same atomic block in sessions with different settings will result in the same behavior, independent of the settings of the current session.</span></span>  
  
## <a name="transactions-and-error-handling"></a><span data-ttu-id="ee624-112">事务和错误处理</span><span class="sxs-lookup"><span data-stu-id="ee624-112">Transactions and Error Handling</span></span>  
 <span data-ttu-id="ee624-113">如果某个事务已在会话上存在（因为某一批处理执行了 `BEGIN TRANSACTION` 语句并且该事务保持活动状态），则开始一个原子块将在该事务中创建一个保存点。</span><span class="sxs-lookup"><span data-stu-id="ee624-113">If a transaction already exists on a session (because a batch executed a `BEGIN TRANSACTION` statement and the transaction remains active), then starting an atomic block will create a savepoint in the transaction.</span></span> <span data-ttu-id="ee624-114">如果该原子块退出且没有异常，将创建用于块提交的保存点，但在该事务在会话级别提交前该事务将不提交。</span><span class="sxs-lookup"><span data-stu-id="ee624-114">If the block exits without an exception, the savepoint that was created for the block commits, but the transaction will not commit until the transaction at the session level commits.</span></span> <span data-ttu-id="ee624-115">如果该块引发一个异常，则该块的影响将被回滚，但处于会话级别的事务将继续，除非该异常是注定事务终止的。</span><span class="sxs-lookup"><span data-stu-id="ee624-115">If the block throws an exception, the effects of the block are rolled back but the transaction at the session level will proceed, unless the exception is transaction-dooming.</span></span> <span data-ttu-id="ee624-116">例如，写入冲突是注定事务终止的，但不是类型转换错误。</span><span class="sxs-lookup"><span data-stu-id="ee624-116">For example a write conflict is transaction-dooming, but not a type casting error.</span></span>  
  
 <span data-ttu-id="ee624-117">如果在会话上没有处于活动状态的事务，则 `BEGIN ATOMIC` 将开始一个新事务。</span><span class="sxs-lookup"><span data-stu-id="ee624-117">If there is no active transaction on a session, `BEGIN ATOMIC` will start a new transaction.</span></span> <span data-ttu-id="ee624-118">如果在该块的作用域外未引发异常，则在该块的末尾将提交该事务。</span><span class="sxs-lookup"><span data-stu-id="ee624-118">If no exception is thrown outside the scope of the block, the transaction will be committed at the end of the block.</span></span> <span data-ttu-id="ee624-119">如果该块引发异常（也就是说，未在该块内捕获和处理异常），则该事务将被回滚。</span><span class="sxs-lookup"><span data-stu-id="ee624-119">If the block throws an exception (that is, the exception is not caught and handled within the block), the transaction will be rolled back.</span></span> <span data-ttu-id="ee624-120">对于跨单个原子块的事务（单个本机编译的存储过程），您无需编写显式的 `BEGIN TRANSACTION` 和 `COMMIT` 或 `ROLLBACK` 语句。</span><span class="sxs-lookup"><span data-stu-id="ee624-120">For transactions that span a single atomic block (a single natively compiled stored procedure), you do not need to write explicit `BEGIN TRANSACTION` and `COMMIT` or `ROLLBACK` statements.</span></span>  
  
 <span data-ttu-id="ee624-121">本机编译的存储过程支持使用 `TRY`、`CATCH` 和 `THROW` 构造进行错误处理。</span><span class="sxs-lookup"><span data-stu-id="ee624-121">Natively compiled stored procedures support the `TRY`, `CATCH`, and `THROW` constructs for error handling.</span></span> <span data-ttu-id="ee624-122">不支持 `RAISERROR`。</span><span class="sxs-lookup"><span data-stu-id="ee624-122">`RAISERROR` is not supported.</span></span>  
  
 <span data-ttu-id="ee624-123">下面的示例说明针对原子块和本机编译存储过程的错误处理行为：</span><span class="sxs-lookup"><span data-stu-id="ee624-123">The following example illustrates the error handling behavior with atomic blocks and natively compiled stored procedures:</span></span>  
  
```sql  
-- sample table  
CREATE TABLE dbo.t1 (  
  c1 int not null primary key nonclustered  
)  
WITH (MEMORY_OPTIMIZED=ON)  
GO  
  
-- sample proc that inserts 2 rows  
CREATE PROCEDURE dbo.usp_t1 @v1 bigint not null, @v2 bigint not null  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS  
BEGIN ATOMIC  
WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english', DELAYED_DURABILITY = ON)  
  
  INSERT dbo.t1 VALUES (@v1)  
  INSERT dbo.t1 VALUES (@v2)  
  
END  
GO  
  
-- insert two rows  
EXEC dbo.usp_t1 1, 2  
GO  
  
-- verify we have no active transaction  
SELECT @@TRANCOUNT  
GO  
  
-- verify the rows 1 and 2 were committed  
SELECT c1 FROM dbo.t1  
GO  
  
-- execute proc with arithmetic overflow  
EXEC dbo.usp_t1 3, 4444444444444  
GO  
-- expected error message:  
-- Msg 8115, Level 16, State 0, Procedure usp_t1  
-- Arithmetic overflow error converting bigint to data type int.  
  
-- verify we have no active transaction  
SELECT @@TRANCOUNT  
GO  
  
-- verify rows 3 was not committed; usp_t1 has been rolled back  
SELECT c1 FROM dbo.t1  
GO  
  
-- start a new transaction  
BEGIN TRANSACTION  
  -- insert rows 3 and 4  
  EXEC dbo.usp_t1 3, 4  
  
  -- verify there is still an active transaction  
  SELECT @@TRANCOUNT  
  
  -- verify the rows 3 and 4 were inserted  
  SELECT c1 FROM dbo.t1 WITH (SNAPSHOT)   
  ORDER BY c1  
  
  -- catch the arithmetic overflow error  
  BEGIN TRY  
    EXEC dbo.usp_t1 5, 4444444444444  
  END TRY  
  BEGIN CATCH  
    PRINT N'Error occurred: ' + error_message()  
  END CATCH  
  
  -- verify there is still an active transaction  
  SELECT @@TRANCOUNT  
  
  -- verify rows 3 and 4 are still in the table, and row 5 has not been inserted  
  SELECT c1 FROM dbo.t1 WITH (SNAPSHOT)   
  ORDER BY c1  
  
COMMIT  
GO  
  
-- verify we have no active transaction  
SELECT @@TRANCOUNT  
GO  
  
-- verify rows 3 and 4 has been committed  
SELECT c1 FROM dbo.t1  
ORDER BY c1  
GO  
```  
  
 <span data-ttu-id="ee624-124">以下特定于内存优化表的错误消息是注定事务终止的。</span><span class="sxs-lookup"><span data-stu-id="ee624-124">The following error messages specific to memory-optimized tables are transaction dooming.</span></span> <span data-ttu-id="ee624-125">如果它们在原子块的作用域中发生，将导致中止事务：10772、41301、41302、41305、41325、41332 和 41333。</span><span class="sxs-lookup"><span data-stu-id="ee624-125">If they occur in the scope of an atomic block, they will cause the transaction to abort: 10772, 41301, 41302, 41305, 41325, 41332, and 41333.</span></span>  
  
## <a name="session-settings"></a><span data-ttu-id="ee624-126">会话设置</span><span class="sxs-lookup"><span data-stu-id="ee624-126">Session Settings</span></span>  
 <span data-ttu-id="ee624-127">在编译存储过程时原子块中的会话设置是固定的。</span><span class="sxs-lookup"><span data-stu-id="ee624-127">The session settings in atomic blocks are fixed when the stored procedure is compiled.</span></span> <span data-ttu-id="ee624-128">某些设置可使用 `BEGIN ATOMIC` 指定，而其他设置则始终固定为相同值。</span><span class="sxs-lookup"><span data-stu-id="ee624-128">Some settings can be specified with `BEGIN ATOMIC` while other settings are always fixed to the same value.</span></span>  
  
 <span data-ttu-id="ee624-129">以下选项对于 `BEGIN ATOMIC` 而言是必需的：</span><span class="sxs-lookup"><span data-stu-id="ee624-129">The following options are required with `BEGIN ATOMIC`:</span></span>  
  
|<span data-ttu-id="ee624-130">必需设置</span><span class="sxs-lookup"><span data-stu-id="ee624-130">Required Setting</span></span>|<span data-ttu-id="ee624-131">说明</span><span class="sxs-lookup"><span data-stu-id="ee624-131">Description</span></span>|  
|----------------------|-----------------|  
|`TRANSACTION ISOLATION LEVEL`|<span data-ttu-id="ee624-132">支持的值为 `SNAPSHOT`、`REPEATABLEREAD` 和 `SERIALIZABLE`。</span><span class="sxs-lookup"><span data-stu-id="ee624-132">Supported values are `SNAPSHOT`, `REPEATABLEREAD`, and `SERIALIZABLE`.</span></span>|  
|`LANGUAGE`|<span data-ttu-id="ee624-133">确定日期和时间格式以及系统消息。</span><span class="sxs-lookup"><span data-stu-id="ee624-133">Determines date and time formats and system messages.</span></span> <span data-ttu-id="ee624-134">支持 [sys.syslanguages (Transact-SQL)](/sql/relational-databases/system-compatibility-views/sys-syslanguages-transact-sql) 中的所有语言和别名。</span><span class="sxs-lookup"><span data-stu-id="ee624-134">All languages and aliases in [sys.syslanguages &#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-syslanguages-transact-sql) are supported.</span></span>|  
  
 <span data-ttu-id="ee624-135">以下设置是可选的：</span><span class="sxs-lookup"><span data-stu-id="ee624-135">The following settings are optional:</span></span>  
  
|<span data-ttu-id="ee624-136">可选设置</span><span class="sxs-lookup"><span data-stu-id="ee624-136">Optional Setting</span></span>|<span data-ttu-id="ee624-137">说明</span><span class="sxs-lookup"><span data-stu-id="ee624-137">Description</span></span>|  
|----------------------|-----------------|  
|`DATEFORMAT`|<span data-ttu-id="ee624-138">支持所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 日期格式。</span><span class="sxs-lookup"><span data-stu-id="ee624-138">All [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] date formats are supported.</span></span> <span data-ttu-id="ee624-139">指定后，`DATEFORMAT` 将取代与 `LANGUAGE` 相关联的默认日期格式。</span><span class="sxs-lookup"><span data-stu-id="ee624-139">When specified, `DATEFORMAT` overrides the default date format associated with `LANGUAGE`.</span></span>|  
|`DATEFIRST`|<span data-ttu-id="ee624-140">指定后，`DATEFIRST` 将取代与 `LANGUAGE` 相关联的默认设置。</span><span class="sxs-lookup"><span data-stu-id="ee624-140">When specified, `DATEFIRST` overrides the default associated with `LANGUAGE`.</span></span>|  
|`DELAYED_DURABILITY`|<span data-ttu-id="ee624-141">支持的值为 `OFF` 和 `ON`。</span><span class="sxs-lookup"><span data-stu-id="ee624-141">Supported values are `OFF` and `ON`.</span></span><br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ee624-142">事务提交可以是完全持久、默认或延迟的持久。有关详细信息，请参阅[控制事务持久性](../logs/control-transaction-durability.md)。</span><span class="sxs-lookup"><span data-stu-id="ee624-142">transaction commits can be either fully durable, the default, or delayed durable.For more information, see [Control Transaction Durability](../logs/control-transaction-durability.md).</span></span>|  
  
 <span data-ttu-id="ee624-143">下面的 SET 选项对于所有本机编译存储过程中的所有原子块具有相同的系统默认值：</span><span class="sxs-lookup"><span data-stu-id="ee624-143">The following SET options have the same system default value for all atomic blocks in all natively compiled stored procedures:</span></span>  
  
|<span data-ttu-id="ee624-144">Set 选项</span><span class="sxs-lookup"><span data-stu-id="ee624-144">Set Option</span></span>|<span data-ttu-id="ee624-145">原子块的系统默认值</span><span class="sxs-lookup"><span data-stu-id="ee624-145">System Default for Atomic Blocks</span></span>|  
|----------------|--------------------------------------|  
|<span data-ttu-id="ee624-146">ANSI_NULLS</span><span class="sxs-lookup"><span data-stu-id="ee624-146">ANSI_NULLS</span></span>|<span data-ttu-id="ee624-147">ON</span><span class="sxs-lookup"><span data-stu-id="ee624-147">ON</span></span>|  
|<span data-ttu-id="ee624-148">ANSI_PADDING</span><span class="sxs-lookup"><span data-stu-id="ee624-148">ANSI_PADDING</span></span>|<span data-ttu-id="ee624-149">ON</span><span class="sxs-lookup"><span data-stu-id="ee624-149">ON</span></span>|  
|<span data-ttu-id="ee624-150">ANSI_WARNING</span><span class="sxs-lookup"><span data-stu-id="ee624-150">ANSI_WARNING</span></span>|<span data-ttu-id="ee624-151">ON</span><span class="sxs-lookup"><span data-stu-id="ee624-151">ON</span></span>|  
|<span data-ttu-id="ee624-152">ARITHABORT</span><span class="sxs-lookup"><span data-stu-id="ee624-152">ARITHABORT</span></span>|<span data-ttu-id="ee624-153">ON</span><span class="sxs-lookup"><span data-stu-id="ee624-153">ON</span></span>|  
|<span data-ttu-id="ee624-154">ARITHIGNORE</span><span class="sxs-lookup"><span data-stu-id="ee624-154">ARITHIGNORE</span></span>|<span data-ttu-id="ee624-155">OFF</span><span class="sxs-lookup"><span data-stu-id="ee624-155">OFF</span></span>|  
|<span data-ttu-id="ee624-156">CONCAT_NULL_YIELDS_NULL</span><span class="sxs-lookup"><span data-stu-id="ee624-156">CONCAT_NULL_YIELDS_NULL</span></span>|<span data-ttu-id="ee624-157">ON</span><span class="sxs-lookup"><span data-stu-id="ee624-157">ON</span></span>|  
|<span data-ttu-id="ee624-158">IDENTITY_INSERT</span><span class="sxs-lookup"><span data-stu-id="ee624-158">IDENTITY_INSERT</span></span>|<span data-ttu-id="ee624-159">OFF</span><span class="sxs-lookup"><span data-stu-id="ee624-159">OFF</span></span>|  
|<span data-ttu-id="ee624-160">NOCOUNT</span><span class="sxs-lookup"><span data-stu-id="ee624-160">NOCOUNT</span></span>|<span data-ttu-id="ee624-161">ON</span><span class="sxs-lookup"><span data-stu-id="ee624-161">ON</span></span>|  
|<span data-ttu-id="ee624-162">NUMERIC_ROUNDABORT</span><span class="sxs-lookup"><span data-stu-id="ee624-162">NUMERIC_ROUNDABORT</span></span>|<span data-ttu-id="ee624-163">OFF</span><span class="sxs-lookup"><span data-stu-id="ee624-163">OFF</span></span>|  
|<span data-ttu-id="ee624-164">QUOTED_IDENTIFIER</span><span class="sxs-lookup"><span data-stu-id="ee624-164">QUOTED_IDENTIFIER</span></span>|<span data-ttu-id="ee624-165">ON</span><span class="sxs-lookup"><span data-stu-id="ee624-165">ON</span></span>|  
|<span data-ttu-id="ee624-166">ROWCOUNT</span><span class="sxs-lookup"><span data-stu-id="ee624-166">ROWCOUNT</span></span>|<span data-ttu-id="ee624-167">0</span><span class="sxs-lookup"><span data-stu-id="ee624-167">0</span></span>|  
|<span data-ttu-id="ee624-168">TEXTSIZE</span><span class="sxs-lookup"><span data-stu-id="ee624-168">TEXTSIZE</span></span>|<span data-ttu-id="ee624-169">0</span><span class="sxs-lookup"><span data-stu-id="ee624-169">0</span></span>|  
|<span data-ttu-id="ee624-170">XACT_ABORT</span><span class="sxs-lookup"><span data-stu-id="ee624-170">XACT_ABORT</span></span>|<span data-ttu-id="ee624-171">OFF</span><span class="sxs-lookup"><span data-stu-id="ee624-171">OFF</span></span><br /><br /> <span data-ttu-id="ee624-172">未捕获的异常导致原子块回滚，但不会导致事务中止，除非错误是注定事务终止的。</span><span class="sxs-lookup"><span data-stu-id="ee624-172">Uncaught exceptions cause the atomic block to roll back, but not cause the transaction to abort unless the error is transaction dooming.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ee624-173">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ee624-173">See Also</span></span>  
 [<span data-ttu-id="ee624-174">本机编译的存储过程</span><span class="sxs-lookup"><span data-stu-id="ee624-174">Natively Compiled Stored Procedures</span></span>](natively-compiled-stored-procedures.md)  
  
  
