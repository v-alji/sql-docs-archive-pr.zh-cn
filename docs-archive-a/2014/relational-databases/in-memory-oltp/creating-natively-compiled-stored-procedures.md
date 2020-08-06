---
title: 创建本机编译的存储过程 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: e6b34010-cf62-4f65-bbdf-117f291cde7b
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3e8e8139427c7f2ad92eea856be8da542f65e344
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579582"
---
# <a name="creating-natively-compiled-stored-procedures"></a><span data-ttu-id="d9e39-102">创建本机编译的存储过程</span><span class="sxs-lookup"><span data-stu-id="d9e39-102">Creating Natively Compiled Stored Procedures</span></span>
  <span data-ttu-id="d9e39-103">本机编译的存储过程未实现完整 [!INCLUDE[tsql](../../includes/tsql-md.md)] 可编程性和查询外围应用。</span><span class="sxs-lookup"><span data-stu-id="d9e39-103">Natively compiled stored procedures do not implement the full [!INCLUDE[tsql](../../includes/tsql-md.md)] programmability and query surface area.</span></span> <span data-ttu-id="d9e39-104">某些 [!INCLUDE[tsql](../../includes/tsql-md.md)] 构造不能在本机编译的存储过程内使用。</span><span class="sxs-lookup"><span data-stu-id="d9e39-104">There are certain [!INCLUDE[tsql](../../includes/tsql-md.md)] constructs that cannot be used inside natively compiled stored procedures.</span></span> <span data-ttu-id="d9e39-105">有关详细信息，请参阅[本机编译的存储过程中支持的构造](../in-memory-oltp/supported-features-for-natively-compiled-t-sql-modules.md)。</span><span class="sxs-lookup"><span data-stu-id="d9e39-105">For more information, see [Supported Constructs in Natively Compiled Stored Procedures](../in-memory-oltp/supported-features-for-natively-compiled-t-sql-modules.md).</span></span>  
  
 <span data-ttu-id="d9e39-106">但是，有几个 [!INCLUDE[tsql](../../includes/tsql-md.md)] 功能，仅本机编译的存储过程支持这些功能：</span><span class="sxs-lookup"><span data-stu-id="d9e39-106">There are, however, several [!INCLUDE[tsql](../../includes/tsql-md.md)] features that are only supported for natively compiled stored procedures:</span></span>  
  
-   <span data-ttu-id="d9e39-107">原子块。</span><span class="sxs-lookup"><span data-stu-id="d9e39-107">Atomic blocks.</span></span> <span data-ttu-id="d9e39-108">有关详细信息，请参阅 [Atomic Blocks](atomic-blocks-in-native-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="d9e39-108">For more information, see [Atomic Blocks](atomic-blocks-in-native-procedures.md).</span></span>  
  
-   <span data-ttu-id="d9e39-109">本机编译存储过程中参数和变量上的 `NOT NULL` 约束。</span><span class="sxs-lookup"><span data-stu-id="d9e39-109">`NOT NULL` constraints on parameters of and variables in natively compiled stored procedures.</span></span> <span data-ttu-id="d9e39-110">不能将 `NULL` 值分配给声明为 `NOT NULL` 的参数或变量。</span><span class="sxs-lookup"><span data-stu-id="d9e39-110">You cannot assign `NULL` values to parameters or variables declared as `NOT NULL`.</span></span> <span data-ttu-id="d9e39-111">有关详细信息，请参阅 [DECLARE @local_variable (Transact-SQL)](/sql/t-sql/language-elements/declare-local-variable-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="d9e39-111">For more information, see [DECLARE @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-local-variable-transact-sql).</span></span>  
  
-   <span data-ttu-id="d9e39-112">本机编译存储过程的架构绑定。</span><span class="sxs-lookup"><span data-stu-id="d9e39-112">Schema binding of natively compiled stored procedures.</span></span>  
  
 <span data-ttu-id="d9e39-113">使用 [CREATE PROCEDURE (Transact-SQL)](/sql/t-sql/statements/create-procedure-transact-sql) 创建本机编译的存储过程。</span><span class="sxs-lookup"><span data-stu-id="d9e39-113">Natively compiled stored procedures are created using [CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql).</span></span> <span data-ttu-id="d9e39-114">下面的示例显示内存优化表以及用于将行插入表的本机编译存储过程。</span><span class="sxs-lookup"><span data-stu-id="d9e39-114">The following example shows a memory-optimized table and a natively compiled stored procedure used for inserting rows into the table.</span></span>  
  
```sql  
create table dbo.Ord  
(OrdNo integer not null primary key nonclustered,   
 OrdDate datetime not null,   
 CustCode nvarchar(5) not null)   
 with (memory_optimized=on)  
go  
  
create procedure dbo.OrderInsert(@OrdNo integer, @CustCode nvarchar(5))  
with native_compilation, schemabinding, execute as owner  
as   
begin atomic with  
(transaction isolation level = snapshot,  
language = N'English')  
  
  declare @OrdDate datetime = getdate();  
  insert into dbo.Ord (OrdNo, CustCode, OrdDate) values (@OrdNo, @CustCode, @OrdDate);  
end  
go  
```  
  
 <span data-ttu-id="d9e39-115">在代码示例中，`NATIVE_COMPILATION` 指示此 [!INCLUDE[tsql](../../includes/tsql-md.md)] 存储过程是本机编译的存储过程。</span><span class="sxs-lookup"><span data-stu-id="d9e39-115">In the code sample, `NATIVE_COMPILATION` indicates that this [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure is a natively compiled stored procedure.</span></span> <span data-ttu-id="d9e39-116">以下选项是必需的：</span><span class="sxs-lookup"><span data-stu-id="d9e39-116">The following options are required:</span></span>  
  
|<span data-ttu-id="d9e39-117">选项</span><span class="sxs-lookup"><span data-stu-id="d9e39-117">Option</span></span>|<span data-ttu-id="d9e39-118">说明</span><span class="sxs-lookup"><span data-stu-id="d9e39-118">Description</span></span>|  
|------------|-----------------|  
|`SCHEMABINDING`|<span data-ttu-id="d9e39-119">本机编译存储过程必须绑定到其引用的对象的架构。</span><span class="sxs-lookup"><span data-stu-id="d9e39-119">Natively compiled stored procedures must be bound to the schema of the objects it references.</span></span> <span data-ttu-id="d9e39-120">这意味着不能删除该过程引用的表。</span><span class="sxs-lookup"><span data-stu-id="d9e39-120">This means that table references by the procedure cannot be dropped.</span></span> <span data-ttu-id="d9e39-121">此过程中引用的表必须包括其架构名称，并且 \* 在查询中不允许使用通配符 () 。</span><span class="sxs-lookup"><span data-stu-id="d9e39-121">Tables referenced in the procedure must include their schema name, and wildcards (\*) are not allowed in queries.</span></span> <span data-ttu-id="d9e39-122">此版本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中的本机编译存储过程仅支持 `SCHEMABINDING`。</span><span class="sxs-lookup"><span data-stu-id="d9e39-122">`SCHEMABINDING` is only supported for natively compiled stored procedures in this version of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>|  
|`EXECUTE AS`|<span data-ttu-id="d9e39-123">本机编译的存储过程不支持 `EXECUTE AS CALLER`，这是默认执行上下文。</span><span class="sxs-lookup"><span data-stu-id="d9e39-123">Natively compiled stored procedures do not support `EXECUTE AS CALLER`, which is the default execution context.</span></span> <span data-ttu-id="d9e39-124">因此，需要指定执行上下文。</span><span class="sxs-lookup"><span data-stu-id="d9e39-124">Therefore, specifying the execution context is required.</span></span> <span data-ttu-id="d9e39-125">支持选项 `EXECUTE AS OWNER` 、 `EXECUTE AS` *用户*和 `EXECUTE AS SELF` 。</span><span class="sxs-lookup"><span data-stu-id="d9e39-125">The options `EXECUTE AS OWNER`, `EXECUTE AS`*user*, and `EXECUTE AS SELF` are supported.</span></span>|  
|`BEGIN ATOMIC`|<span data-ttu-id="d9e39-126">本机编译的存储过程正文必须由恰好一个原子块构成。</span><span class="sxs-lookup"><span data-stu-id="d9e39-126">The natively compiled stored procedure body must consist of exactly one atomic block.</span></span> <span data-ttu-id="d9e39-127">原子块确保存储过程的原子执行。</span><span class="sxs-lookup"><span data-stu-id="d9e39-127">Atomic blocks guarantee atomic execution of the stored procedure.</span></span> <span data-ttu-id="d9e39-128">如果在活动事务的上下文外调用该过程，它将开始一个新事务，这个新事务在原子块的末尾提交。</span><span class="sxs-lookup"><span data-stu-id="d9e39-128">If the procedure is invoked outside the context of an active transaction, it will start a new transaction, which commits at the end of the atomic block.</span></span> <span data-ttu-id="d9e39-129">本机编译存储过程中的原子块具有两个必需的选项：</span><span class="sxs-lookup"><span data-stu-id="d9e39-129">Atomic blocks in natively compiled stored procedures have two required options:</span></span><br /><br /> <span data-ttu-id="d9e39-130">`TRANSACTION ISOLATION LEVEL`.</span><span class="sxs-lookup"><span data-stu-id="d9e39-130">`TRANSACTION ISOLATION LEVEL`.</span></span> <span data-ttu-id="d9e39-131">请参阅支持的隔离级别的[事务隔离级别](../../database-engine/transaction-isolation-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="d9e39-131">See [Transaction Isolation Levels](../../database-engine/transaction-isolation-levels.md) for supported isolation levels.</span></span><br /><br /> <span data-ttu-id="d9e39-132">`LANGUAGE`.</span><span class="sxs-lookup"><span data-stu-id="d9e39-132">`LANGUAGE`.</span></span> <span data-ttu-id="d9e39-133">存储过程的语言必须设置为可用语言或语言别名之一。</span><span class="sxs-lookup"><span data-stu-id="d9e39-133">The language for the stored procedure must be set to one of the available languages or language aliases.</span></span>|  
  
 <span data-ttu-id="d9e39-134">通过 `EXECUTE AS` 进行模拟可能会导致 `EXECUTE AS` 和 Windows 登录名出错。</span><span class="sxs-lookup"><span data-stu-id="d9e39-134">Regarding `EXECUTE AS` and Windows logins, an error can occur because of the impersonation done through `EXECUTE AS`.</span></span> <span data-ttu-id="d9e39-135">如果用户帐户使用 Windows 身份验证，则用于 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例的服务帐户与 Windows 登录名所在的域之间必须存在完全信任。</span><span class="sxs-lookup"><span data-stu-id="d9e39-135">If a user account uses Windows Authentication, there must be full trust between the service account used for the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance and the domain of the Windows login.</span></span> <span data-ttu-id="d9e39-136">如果没有完全信任，则在创建本机编译的存储过程时返回以下错误消息：消息15404、无法获取有关 Windows NT 组/用户 "username" 的信息，错误代码0x5。</span><span class="sxs-lookup"><span data-stu-id="d9e39-136">If there is not full trust, the following error message is returned when creating a natively compiled stored procedure: Msg 15404, Could not obtain information about Windows NT group/user 'username', error code 0x5.</span></span>  
  
 <span data-ttu-id="d9e39-137">若要解决此错误，请使用以下选项之一：</span><span class="sxs-lookup"><span data-stu-id="d9e39-137">To resolve this error, use one of the following:</span></span>  
  
-   <span data-ttu-id="d9e39-138">使用与 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服务的 Windows 用户处于相同域中的帐户。</span><span class="sxs-lookup"><span data-stu-id="d9e39-138">Use an account from the same domain as the Windows user for the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service.</span></span>  
  
-   <span data-ttu-id="d9e39-139">如果 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 正在使用 Network Service 或 Local System 等计算机帐户，则包含 Windows 用户的域必须信任该计算机。</span><span class="sxs-lookup"><span data-stu-id="d9e39-139">If [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is using a machine account such as Network Service or Local System, the machine must be trusted by the domain containing the Windows user.</span></span>  
  
-   <span data-ttu-id="d9e39-140">使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 身份验证。</span><span class="sxs-lookup"><span data-stu-id="d9e39-140">Use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="d9e39-141">在创建本机编译的存储过程时还可能会看到错误 15517。</span><span class="sxs-lookup"><span data-stu-id="d9e39-141">You may also see error 15517 when creating a natively compiled stored procedure.</span></span> <span data-ttu-id="d9e39-142">有关详细信息，请参阅[MSSQLSERVER_15517](../errors-events/mssqlserver-15517-database-engine-error.md)。</span><span class="sxs-lookup"><span data-stu-id="d9e39-142">For more information, see [MSSQLSERVER_15517](../errors-events/mssqlserver-15517-database-engine-error.md).</span></span>  
  
## <a name="updating-a-natively-compiled-stored-procedure"></a><span data-ttu-id="d9e39-143">更新本机编译的存储过程</span><span class="sxs-lookup"><span data-stu-id="d9e39-143">Updating a Natively Compiled Stored Procedure</span></span>  
 <span data-ttu-id="d9e39-144">不支持对本机编译的存储过程执行更改操作。</span><span class="sxs-lookup"><span data-stu-id="d9e39-144">Performing alter operations on natively compiled stored procedures is not supported.</span></span> <span data-ttu-id="d9e39-145">修改本机编译的存储过程的一种方法是删除再重新创建该存储过程：</span><span class="sxs-lookup"><span data-stu-id="d9e39-145">One way to modify a natively compiled stored procedure is to drop and recreate the stored procedure:</span></span>  
  
1.  <span data-ttu-id="d9e39-146">生成对该存储过程的权限的脚本。</span><span class="sxs-lookup"><span data-stu-id="d9e39-146">Generate script for the permissions on the stored procedure.</span></span>  
  
2.  <span data-ttu-id="d9e39-147">生成该存储过程的脚本并另存为备份（可选）。</span><span class="sxs-lookup"><span data-stu-id="d9e39-147">Optional, generate script for the stored procedure and save as a backup.</span></span>  
  
3.  <span data-ttu-id="d9e39-148">删除该存储过程。</span><span class="sxs-lookup"><span data-stu-id="d9e39-148">Drop the stored procedure.</span></span>  
  
4.  <span data-ttu-id="d9e39-149">创建更改后的存储过程。</span><span class="sxs-lookup"><span data-stu-id="d9e39-149">Create the altered stored procedure.</span></span>  
  
5.  <span data-ttu-id="d9e39-150">将脚本化的权限重新应用到该存储过程。</span><span class="sxs-lookup"><span data-stu-id="d9e39-150">Re-apply the scripted permissions to the stored procedure.</span></span>  
  
 <span data-ttu-id="d9e39-151">此方法的缺点是从步骤 3 开始到步骤 5 结束应用程序将会脱机。</span><span class="sxs-lookup"><span data-stu-id="d9e39-151">The disadvantage to this procedure is the application will be offline from the start of step 3 through the completion of step 5.</span></span> <span data-ttu-id="d9e39-152">这可能需要几秒钟时间，并且使用应用程序的客户端可能看到错误消息。</span><span class="sxs-lookup"><span data-stu-id="d9e39-152">This may take a few seconds and the client using the application may see error messages.</span></span>  
  
 <span data-ttu-id="d9e39-153">另一种高效修改本机编译的存储过程的方法是首先创建存储过程的新版本。</span><span class="sxs-lookup"><span data-stu-id="d9e39-153">Another way to (effectively) modify a natively compiled stored procedure is to first create a new version of the stored procedure.</span></span> <span data-ttu-id="d9e39-154">此处，本机编译的存储过程具有一个关联的版本号。</span><span class="sxs-lookup"><span data-stu-id="d9e39-154">Here, the natively compiled stored procedure has an associated version number.</span></span> <span data-ttu-id="d9e39-155">我们将旧版本称为 SP_Vold，将新版本称为 SP_Vnew。</span><span class="sxs-lookup"><span data-stu-id="d9e39-155">We will call the old version SP_Vold and the new version SP_Vnew.</span></span>  
  
1.  <span data-ttu-id="d9e39-156">为 SP_Vold 上的权限生成脚本。</span><span class="sxs-lookup"><span data-stu-id="d9e39-156">Generate script for the permissions on SP_Vold.</span></span>  
  
2.  <span data-ttu-id="d9e39-157">创建 SP_Vnew。</span><span class="sxs-lookup"><span data-stu-id="d9e39-157">Create SP_Vnew.</span></span>  
  
3.  <span data-ttu-id="d9e39-158">将 SP_Vold 的权限应用到 SP_Vnew。</span><span class="sxs-lookup"><span data-stu-id="d9e39-158">Apply the permissions of SP_Vold to SP_Vnew.</span></span>  
  
4.  <span data-ttu-id="d9e39-159">更新对 SP_Vold 的引用以指向 SP_Vnew。</span><span class="sxs-lookup"><span data-stu-id="d9e39-159">Update references to SP_Vold to point to SP_Vnew.</span></span> <span data-ttu-id="d9e39-160">这可以通过不同方式实现，例如：</span><span class="sxs-lookup"><span data-stu-id="d9e39-160">This can be accomplished in different of ways, for example:</span></span>  
  
     <span data-ttu-id="d9e39-161">使用一个包装（基于磁盘的）存储过程，并修改该过程以指向 SP_Vnew。</span><span class="sxs-lookup"><span data-stu-id="d9e39-161">Use a wrapper (disk-based) stored procedure, and alter that procedure to point to SP_Vnew.</span></span> <span data-ttu-id="d9e39-162">此方法的缺点是间接影响性能。</span><span class="sxs-lookup"><span data-stu-id="d9e39-162">The disadvantage of this approach is the performance impact of the indirection.</span></span>  
  
    ```sql  
    ALTER PROCEDURE dbo.SP p1,...,pn  
    AS  
      EXEC dbo.SP_Vnew p1,...,pn  
    GO  
    ```  
  
5.  <span data-ttu-id="d9e39-163">删除 SP_Vold（可选）。</span><span class="sxs-lookup"><span data-stu-id="d9e39-163">Optional, drop SP_Vold.</span></span>  
  
 <span data-ttu-id="d9e39-164">此方法的优势在于应用程序不会脱机。</span><span class="sxs-lookup"><span data-stu-id="d9e39-164">The advantage of this approach is that the application does not go offline.</span></span> <span data-ttu-id="d9e39-165">但是，需要做更多的工作来维护引用并确保它们始终指向存储过程的最新版本。</span><span class="sxs-lookup"><span data-stu-id="d9e39-165">However, more work is required to maintain the references and make sure they always point to the latest version of the stored procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9e39-166">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d9e39-166">See Also</span></span>  
 [<span data-ttu-id="d9e39-167">本机编译的存储过程</span><span class="sxs-lookup"><span data-stu-id="d9e39-167">Natively Compiled Stored Procedures</span></span>](natively-compiled-stored-procedures.md)  
  
  
