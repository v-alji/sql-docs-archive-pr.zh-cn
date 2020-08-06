---
title: 内存优化表上事务的重试逻辑指南 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: f2a35c37-4449-49ee-8bba-928028f1de66
author: stevestein
ms.author: sstein
ms.openlocfilehash: c9ffaccefb8d4e0a3044c4858a06029fd4350354
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690038"
---
# <a name="guidelines-for-retry-logic-for-transactions-on-memory-optimized-tables"></a><span data-ttu-id="a2f4a-102">内存优化表事务重试逻辑准则</span><span class="sxs-lookup"><span data-stu-id="a2f4a-102">Guidelines for Retry Logic for Transactions on Memory-Optimized Tables</span></span>
  <span data-ttu-id="a2f4a-103">有一些与访问内存优化表的事务有关的错误情形。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-103">There are error conditions that occur with transactions that access memory-optimized tables.</span></span>  
  
-   41302. <span data-ttu-id="a2f4a-104">当前事务尝试更新自事务启动以来已更新过的记录。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-104">The current transaction attempted to update a record that has been updated since the transaction started.</span></span>  
  
-   41305. <span data-ttu-id="a2f4a-105">因某个可重复读取验证失败，当前事务无法提交。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-105">The current transaction failed to commit due to a repeatable read validation failure.</span></span>  
  
-   41325. <span data-ttu-id="a2f4a-106">因某个序列化读取验证失败，当前事务无法提交。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-106">The current transaction failed to commit due to a serializable validation failure.</span></span>  
  
-   41301. <span data-ttu-id="a2f4a-107">当前事务所依赖的前一事务已终止，当前事务无法再提交。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-107">A previous transaction that the current transaction took a dependency on has aborted, and the current transaction can no longer commit.</span></span>  
  
 <span data-ttu-id="a2f4a-108">这些错误通常是由并发执行的事务相互干扰而产生的。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-108">A common cause of these errors is interference between concurrently executing transaction.</span></span> <span data-ttu-id="a2f4a-109">常见的纠正措施是重试事务。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-109">The common corrective action is to retry the transaction.</span></span>  
  
 <span data-ttu-id="a2f4a-110">有关这些错误情况的详细信息，请参阅[内存优化表的事务](../relational-databases/in-memory-oltp/memory-optimized-tables.md)中的冲突检测、验证和提交依赖项检查部分。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-110">For more information about these error conditions, see the section on Conflict Detection, Validation, and Commit Dependency Checks in [Transactions in Memory-Optimized Tables](../relational-databases/in-memory-oltp/memory-optimized-tables.md).</span></span>  
  
 <span data-ttu-id="a2f4a-111">内存优化表不会产生死锁（错误代码为 1205）。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-111">Deadlocks (error code 1205) cannot occur for memory-optimized tables.</span></span> <span data-ttu-id="a2f4a-112">内存优化表不使用锁。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-112">Locks are not used for memory-optimized tables.</span></span> <span data-ttu-id="a2f4a-113">但是，如果应用程序已包含死锁重试逻辑，则可能会扩展现有逻辑，以包含新的错误代码。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-113">However, if the application already contains retry logic for deadlocks, the existing logic could be extended to include the new error codes.</span></span>  
  
## <a name="considerations-for-retrying"></a><span data-ttu-id="a2f4a-114">有关重试的注意事项</span><span class="sxs-lookup"><span data-stu-id="a2f4a-114">Considerations for Retrying</span></span>  
 <span data-ttu-id="a2f4a-115">应用程序通常会遭遇事务相互冲突，而需要实现重试逻辑以解决这些冲突。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-115">Applications will typically encounter conflicts between transactions and need to implement retry logic to resolve those conflicts.</span></span> <span data-ttu-id="a2f4a-116">遭遇冲突的次数取决于若干因素：</span><span class="sxs-lookup"><span data-stu-id="a2f4a-116">The number of conflicts encountered depends on a number of factors:</span></span>  
  
-   <span data-ttu-id="a2f4a-117">个别行争用。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-117">Contention for individual rows.</span></span> <span data-ttu-id="a2f4a-118">随着事务尝试更新同一行的次数的增加，发生冲突的可能性也会增加。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-118">The potential for conflicts increases as the number of transactions attempting to update the same row increases.</span></span>  
  
-   <span data-ttu-id="a2f4a-119">REPEATABLE READ 事务读取的行数。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-119">Number of rows read by REPEATABLE READ transactions.</span></span> <span data-ttu-id="a2f4a-120">读取的行数越多，这些行中的某些行被并发事务更新的几率就越大。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-120">The more rows read, the greater the chance that some of these rows are updated by concurrent transactions.</span></span> <span data-ttu-id="a2f4a-121">这将导致重复性读取验证失败。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-121">This causes repeatable read validation failures.</span></span>  
  
-   <span data-ttu-id="a2f4a-122">SERIALIZABLE 事务使用的扫描范围的大小。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-122">Size of the scan ranges used by SERIALIZABLE transactions.</span></span> <span data-ttu-id="a2f4a-123">扫描范围越大，并发事务引入虚拟行的几率就越大，从而导致序列化验证失败。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-123">The larger the scan ranges, the higher the chance that concurrent transactions will introduce phantom rows, causing serializable validation failures.</span></span>  
  
     <span data-ttu-id="a2f4a-124">应用程序很难避免此类冲突，因而需要重试逻辑。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-124">It is difficult for an application to avoid these conflicts, requiring retry logic.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a2f4a-125">访问内存优化表的读/写事务需要重试逻辑。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-125">Read-write transactions that access memory-optimized tables require retry logic.</span></span>  
  
### <a name="considerations-for-read-only-transactions-and-natively-compiled-stored-procedures"></a><span data-ttu-id="a2f4a-126">有关只读事务和本机编译存储过程的注意事项</span><span class="sxs-lookup"><span data-stu-id="a2f4a-126">Considerations for Read-Only Transactions and Natively Compiled Stored Procedures</span></span>  
 <span data-ttu-id="a2f4a-127">延续本机编译存储过程单次执行的只读事务不需要 REPEATABLE READ 和 SERIALIZABLE 事务验证。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-127">Read-only transactions that span a single execution of a natively compiled stored procedure do not require validation for REPEATABLE READ and SERIALIZABLE transactions.</span></span> <span data-ttu-id="a2f4a-128">只读事务不会造成写入冲突。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-128">Write conflicts cannot occur due to a transaction being read-only.</span></span>  
  
 <span data-ttu-id="a2f4a-129">但是，依赖关系失败仍可能发生。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-129">However, dependency failures can still occur.</span></span> <span data-ttu-id="a2f4a-130">依赖关系失败没有冲突造成的错误那样常见。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-130">Dependency failures are rarer than errors resulting from conflicts.</span></span> <span data-ttu-id="a2f4a-131">因此，在许多情况下，延续本机编译存储过程单次执行的只读事务不需要特定的重试逻辑。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-131">Therefore, in many cases, specific retry logic is not required for read-only transactions that span single executions of natively compiled stored procedures.</span></span>  
  
### <a name="considerations-for-read-only-transactions-and-cross-container-transactions"></a><span data-ttu-id="a2f4a-132">有关只读事务和跨容器事务的注意事项</span><span class="sxs-lookup"><span data-stu-id="a2f4a-132">Considerations for Read-Only Transactions and Cross-Container Transactions</span></span>  
 <span data-ttu-id="a2f4a-133">如果所有内存优化表都是在 SNAPSHOT 隔离的情况下访问的，则只读跨容器事务（即在本机编译存储过程上下文之外启动的事务）不执行验证。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-133">Read-only cross-container transactions, which are transactions that are started outside the context of a natively compiled stored procedure, do not perform validation if the memory-optimized tables are all accessed under SNAPSHOT isolation.</span></span> <span data-ttu-id="a2f4a-134">但是，当在 REPEATABLE READ 或 SERIALIZABLE 隔离下访问内存优化表时，将在提交时间执行验证。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-134">However, when memory-optimized tables are accessed under REPEATABLE READ or SERIALIZABLE isolation, validation is performed at commit time.</span></span> <span data-ttu-id="a2f4a-135">在这种情况下，可能需要重试逻辑。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-135">In this case, retry logic may be required.</span></span>  
  
 <span data-ttu-id="a2f4a-136">有关详细信息，请参阅[事务隔离级别](../../2014/database-engine/transaction-isolation-levels.md)中有关跨容器事务的部分。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-136">For more information, see the section on Cross-Container Transactions in [Transaction Isolation Levels](../../2014/database-engine/transaction-isolation-levels.md).</span></span>  
  
## <a name="implementing-retry-logic"></a><span data-ttu-id="a2f4a-137">实现重试逻辑</span><span class="sxs-lookup"><span data-stu-id="a2f4a-137">Implementing Retry Logic</span></span>  
 <span data-ttu-id="a2f4a-138">就像访问内存优化表的所有事务一样，您需要考虑使用重试逻辑来处理可能出现的失败，例如写入冲突（错误代码 41302）或依赖关系错误（错误代码 41301）。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-138">As with all transactions that access memory-optimized tables, you need to consider retry logic to handle potential failures, such as write conflicts (error code 41302) or dependency failures (error code 41301).</span></span> <span data-ttu-id="a2f4a-139">在大多数应用程序中，失败率很低，但仍有必要通过重试事务来处理失败。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-139">In most applications the failure rate will be low, but it is still necessary to handle failures by retrying the transaction.</span></span> <span data-ttu-id="a2f4a-140">建议通过两种方法实现重试逻辑：</span><span class="sxs-lookup"><span data-stu-id="a2f4a-140">Two suggested ways of implementing retry logic are:</span></span>  
  
-   <span data-ttu-id="a2f4a-141">客户端重试。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-141">Client-side retries.</span></span> <span data-ttu-id="a2f4a-142">客户端重试是一般情况下实现重试逻辑的首选方法。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-142">Client-side retries is the preferred way to implement retry logic in the general case.</span></span> <span data-ttu-id="a2f4a-143">客户端应用程序捕获事务抛出的错误，并重试该事务。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-143">The client application catches the error thrown by the transaction, and retries the transaction.</span></span> <span data-ttu-id="a2f4a-144">如果现有的客户端应用程序有处理死锁的重试逻辑，可以扩展该应用程序以处理新错误代码。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-144">If an existing client application has retry logic to handle deadlocks, you can extend the application to handle the new error codes.</span></span>  
  
-   <span data-ttu-id="a2f4a-145">使用包装存储过程。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-145">Using a wrapper stored procedure.</span></span> <span data-ttu-id="a2f4a-146">客户端调用解释型 [!INCLUDE[tsql](../includes/tsql-md.md)] 存储过程，它将调用本机编译的存储过程或执行该事务。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-146">The client calls an interpreted [!INCLUDE[tsql](../includes/tsql-md.md)] stored procedure that calls the natively compiled stored procedure or executes the transaction.</span></span> <span data-ttu-id="a2f4a-147">然后，包装过程使用 try/catch 逻辑捕获错误并重试过程调用（如果需要）。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-147">The wrapper procedure then uses try/catch logic to catch the error and retry the procedure call if needed.</span></span> <span data-ttu-id="a2f4a-148">有可能结果已在失败前返回到客户端，所以客户端不会知道要放弃它们。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-148">It is possible that results are returned to the client before the failure, and the client would not know to discard them.</span></span> <span data-ttu-id="a2f4a-149">因此，为安全起见，最好在此方法中仅使用不向客户端返回任何结果集的本机编译的存储过程。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-149">Therefore, to be safe, it is best to use this method only with natively compiled stored procedures that do not return any result sets to the client.</span></span>  
  
 <span data-ttu-id="a2f4a-150">重试逻辑可在 [!INCLUDE[tsql](../includes/tsql-md.md)] 或中间层中的应用程序代码中实现。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-150">The retry logic can be implemented either in [!INCLUDE[tsql](../includes/tsql-md.md)] or in the application code in the mid-tier.</span></span>  
  
 <span data-ttu-id="a2f4a-151">考虑重试逻辑时的两个可能因素有：</span><span class="sxs-lookup"><span data-stu-id="a2f4a-151">Two possible reasons to consider the retry logic are:</span></span>  
  
-   <span data-ttu-id="a2f4a-152">客户端应用程序具有针对其他错误代码的重试逻辑，如 1205，可以加以扩展。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-152">The client application has retry logic for other error codes, such as 1205, which you can extend.</span></span>  
  
-   <span data-ttu-id="a2f4a-153">冲突不常见，而借助准备好的执行减少端到端延迟很重要。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-153">Conflicts are rare, and it is important to reduce end-to-end latency by using prepared execution.</span></span> <span data-ttu-id="a2f4a-154">有关直接执行本机编译存储过程的详细信息，请参阅[本机编译的存储过程](../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-154">For more information about executing natively compiled stored procedures directly, see [Natively Compiled Stored Procedures](../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md).</span></span>  
  
 <span data-ttu-id="a2f4a-155">下面的示例演示解释型 [!INCLUDE[tsql](../includes/tsql-md.md)] 存储过程中的重试逻辑，它包含对本机编译存储过程或跨容器事务的调用。</span><span class="sxs-lookup"><span data-stu-id="a2f4a-155">The following sample shows retry logic in an interpreted [!INCLUDE[tsql](../includes/tsql-md.md)] stored procedure that contains a call either to a natively compiled stored procedure or to a cross-container transaction.</span></span>  
  
```sql  
CREATE PROCEDURE usp_my_procedure @param1 type1, @param2 type2, ...  
AS  
BEGIN  
  -- number of retries - tune based on the workload  
  DECLARE @retry INT = 10  
  
  WHILE (@retry > 0)  
  BEGIN  
    BEGIN TRY  
  
      -- exec usp_my_native_proc @param1, @param2, ...  
  
      --       or  
  
      -- BEGIN TRANSACTION  
      --   ...  
      -- COMMIT TRANSACTION  
  
      SET @retry = 0  
    END TRY  
    BEGIN CATCH  
      SET @retry -= 1  
  
      -- the error number for deadlocks (1205) does not need to be included for   
      -- transactions that do not access disk-based tables  
      IF (@retry > 0 AND error_number() in (41302, 41305, 41325, 41301, 1205))  
      BEGIN  
        -- these error conditions are transaction dooming - rollback the transaction  
        -- this is not needed if the transaction spans a single native proc execution  
        --   as the native proc will simply rollback when an error is thrown   
        IF XACT_STATE() = -1  
          ROLLBACK TRANSACTION  
  
        -- use a delay if there is a high rate of write conflicts (41302)  
        --   length of delay should depend on the typical duration of conflicting transactions  
        -- WAITFOR DELAY '00:00:00.001'  
      END  
      ELSE  
      BEGIN  
        -- insert custom error handling for other error conditions here  
  
        -- throw if this is not a qualifying error condition  
        ;THROW  
      END  
    END CATCH  
  END  
END  
```  
  
## <a name="see-also"></a><span data-ttu-id="a2f4a-156">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a2f4a-156">See Also</span></span>  
 <span data-ttu-id="a2f4a-157">[了解内存优化表上的事务](../../2014/database-engine/understanding-transactions-on-memory-optimized-tables.md) </span><span class="sxs-lookup"><span data-stu-id="a2f4a-157">[Understanding Transactions on Memory-Optimized Tables](../../2014/database-engine/understanding-transactions-on-memory-optimized-tables.md) </span></span>  
 <span data-ttu-id="a2f4a-158">[内存优化表中的事务](../relational-databases/in-memory-oltp/memory-optimized-tables.md) </span><span class="sxs-lookup"><span data-stu-id="a2f4a-158">[Transactions in Memory-Optimized Tables](../relational-databases/in-memory-oltp/memory-optimized-tables.md) </span></span>  
 [<span data-ttu-id="a2f4a-159">内存优化表事务隔离级别准则</span><span class="sxs-lookup"><span data-stu-id="a2f4a-159">Guidelines for Transaction Isolation Levels with Memory-Optimized Tables</span></span>](../../2014/database-engine/guidelines-for-transaction-isolation-levels-with-memory-optimized-tables.md)  
  
  
