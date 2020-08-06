---
title: 使用标记的事务 (完整恢复模式) 中一致地恢复相关的数据库 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- transaction marks [SQL Server]
- marked transactions [SQL Server]
- database restores [SQL Server], inserting transaction marks for
- recovery [SQL Server], related databases
- restoring databases [SQL Server], related database recovery
- database restores [SQL Server], related databases
- marked transactions [SQL Server], creating
- BEGIN TRAN...WITH MARK statement
- two-phase commit
ms.assetid: 50a73574-1a69-448e-83dd-9abcc7cb7e1a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8dd368ad14f6e521fb8d504bdea774e3088c2522
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691753"
---
# <a name="use-marked-transactions-to-recover-related-databases-consistently-full-recovery-model"></a><span data-ttu-id="97447-102">使用标记的事务一致地恢复相关的数据库的事务（完全恢复模式）</span><span class="sxs-lookup"><span data-stu-id="97447-102">Use Marked Transactions to Recover Related Databases Consistently (Full Recovery Model)</span></span>
  <span data-ttu-id="97447-103">本主题仅与使用完整恢复模式或大容量日志恢复模式的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库相关。</span><span class="sxs-lookup"><span data-stu-id="97447-103">This topic is relevant only for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases that are using the full or bulk-logged recovery models.</span></span>  
  
 <span data-ttu-id="97447-104">在对两个或更多数据库（“相关数据库”  ）进行相关更新时，可以使用事务标记将它们恢复到逻辑上一致的点。</span><span class="sxs-lookup"><span data-stu-id="97447-104">When you make related updates to two or more databases, *related databases*, you can use transaction marks to recover them to a logically consistent point.</span></span> <span data-ttu-id="97447-105">但是，此恢复将丢失在作为恢复点的标记之后提交的所有事务。</span><span class="sxs-lookup"><span data-stu-id="97447-105">However, this recovery loses any transaction that is committed after the mark that was used as the recovery point.</span></span> <span data-ttu-id="97447-106">只有您在测试相关数据库或不介意丢失近期提交的事务时，标记事务才适用。</span><span class="sxs-lookup"><span data-stu-id="97447-106">Marking transactions is suitable only when you are testing related databases or when you are willing to lose recently committed transactions.</span></span>  
  
 <span data-ttu-id="97447-107">在每个相关数据库中定期标记相关事务将在数据库中建立一系列公用恢复点。</span><span class="sxs-lookup"><span data-stu-id="97447-107">Routinely marking related transactions in every related database establishes a series of common recovery points in the databases.</span></span> <span data-ttu-id="97447-108">事务标记将记录在事务日志中并包括在日志备份中。</span><span class="sxs-lookup"><span data-stu-id="97447-108">The transaction marks are recorded in the transaction log and included in log backups.</span></span> <span data-ttu-id="97447-109">发生灾难时，可以将各数据库还原到相同的事务标记，从而将它们恢复到一致的点。</span><span class="sxs-lookup"><span data-stu-id="97447-109">In the event of a disaster, you can restore each of the databases to the same transaction mark to recover them to a consistent point.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="97447-110">可以对不同的数据库独立创建各日志备份，而无需同时创建。</span><span class="sxs-lookup"><span data-stu-id="97447-110">Log backups on the different databases can be created independently of each other and do not have to be simultaneous.</span></span>  
  
 <span data-ttu-id="97447-111">对于以下情况，若要恢复相关数据库，则必须先对各相关数据库中的事务进行标记：</span><span class="sxs-lookup"><span data-stu-id="97447-111">Recovering related databases in the following scenarios requires that you have already marked transactions in every related database:</span></span>  
  
-   <span data-ttu-id="97447-112">一个或多个事务日志已破坏。</span><span class="sxs-lookup"><span data-stu-id="97447-112">One or more transaction logs are destroyed.</span></span> <span data-ttu-id="97447-113">需要将数据库集还原到上次进行日志备份时的一致状态。</span><span class="sxs-lookup"><span data-stu-id="97447-113">You have to restore the set of databases to a consistent state at the time of your last log backup.</span></span>  
  
-   <span data-ttu-id="97447-114">需要将整个数据库集还原到某个更早时间点的相互一致状态。</span><span class="sxs-lookup"><span data-stu-id="97447-114">You have to restore the entire set of databases to a mutually consistent state at some earlier point in time.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="97447-115">您仅可以将相关数据库恢复为标记事务，而不是特定时间点。</span><span class="sxs-lookup"><span data-stu-id="97447-115">You can recover related databases only to a marked transaction, not to a specific point in time.</span></span>  
  
 <span data-ttu-id="97447-116">有关如何创建标记事务的信息，请参阅本主题后面的“创建标记事务”。</span><span class="sxs-lookup"><span data-stu-id="97447-116">For information about how to create marking transactions, see "Creating the Marked Transactions," later in this topic.</span></span>  
  
## <a name="typical-scenario-for-using-marked-transactions"></a><span data-ttu-id="97447-117">使用标记事务的典型方案</span><span class="sxs-lookup"><span data-stu-id="97447-117">Typical Scenario for Using Marked Transactions</span></span>  
 <span data-ttu-id="97447-118">使用标记事务的典型方案包括以下步骤：</span><span class="sxs-lookup"><span data-stu-id="97447-118">A typical scenario for using marked transactions includes the following steps:</span></span>  
  
1.  <span data-ttu-id="97447-119">创建每个相关数据库的完整数据库备份或差异数据库备份。</span><span class="sxs-lookup"><span data-stu-id="97447-119">Create a full or differential database backup of each of the related databases.</span></span>  
  
2.  <span data-ttu-id="97447-120">在所有数据库中标记事务块。</span><span class="sxs-lookup"><span data-stu-id="97447-120">Mark a transaction block in all the databases.</span></span>  
  
3.  <span data-ttu-id="97447-121">备份所有数据库的事务日志。</span><span class="sxs-lookup"><span data-stu-id="97447-121">Back up the transaction log for all the databases.</span></span>  
  
4.  <span data-ttu-id="97447-122">用 WITH NORECOVERY 还原数据库备份。</span><span class="sxs-lookup"><span data-stu-id="97447-122">Restore database backups WITH NORECOVERY.</span></span>  
  
5.  <span data-ttu-id="97447-123">用 WITH STOPATMARK 还原日志。</span><span class="sxs-lookup"><span data-stu-id="97447-123">Restore logs WITH STOPATMARK.</span></span>  
  
## <a name="considerations-for-using-marked-transactions"></a><span data-ttu-id="97447-124">使用标记事务的注意事项</span><span class="sxs-lookup"><span data-stu-id="97447-124">Considerations for Using Marked Transactions</span></span>  
 <span data-ttu-id="97447-125">在将已命名的标记插入事务日志之前，请注意以下事项：</span><span class="sxs-lookup"><span data-stu-id="97447-125">Before inserting named marks into the transaction log, consider the following:</span></span>  
  
-   <span data-ttu-id="97447-126">由于事务标记会消耗日志空间，应只对在数据库恢复策略中起重要作用的事务使用标记。</span><span class="sxs-lookup"><span data-stu-id="97447-126">Because transaction marks consume log space, use them only for transactions that play a significant role in the database recovery strategy.</span></span>  
  
-   <span data-ttu-id="97447-127">标记的事务提交之后，在 [msdb](/sql/relational-databases/system-tables/logmarkhistory-transact-sql) 的 **logmarkhistory**表中插入一行。</span><span class="sxs-lookup"><span data-stu-id="97447-127">After a marked transaction commits, a row is inserted in the [logmarkhistory](/sql/relational-databases/system-tables/logmarkhistory-transact-sql) table in **msdb**.</span></span>  
  
-   <span data-ttu-id="97447-128">如果一个标记的事务跨同一数据库服务器或不同服务器上的多个数据库，这些标记将记录在所有受影响的数据库的日志内。</span><span class="sxs-lookup"><span data-stu-id="97447-128">If a marked transaction spans multiple databases on the same database server or on different servers, the marks must be recorded in the logs of all the affected databases.</span></span>  
  
## <a name="creating-the-marked-transactions"></a><span data-ttu-id="97447-129">创建标记事务</span><span class="sxs-lookup"><span data-stu-id="97447-129">Creating the Marked Transactions</span></span>  
 <span data-ttu-id="97447-130">若要创建标记事务，请使用 [BEGIN TRANSACTION](/sql/t-sql/language-elements/begin-transaction-transact-sql) 语句和 WITH MARK [*description*] 子句。</span><span class="sxs-lookup"><span data-stu-id="97447-130">To create a marked transaction, use the [BEGIN TRANSACTION](/sql/t-sql/language-elements/begin-transaction-transact-sql) statement and the WITH MARK [*description*] clause.</span></span> <span data-ttu-id="97447-131">可选内容 *description* 是关于标记的文字说明。</span><span class="sxs-lookup"><span data-stu-id="97447-131">The optional *description* is a textual description of the mark.</span></span> <span data-ttu-id="97447-132">必须为事务指定标记名称。</span><span class="sxs-lookup"><span data-stu-id="97447-132">A mark name for the transaction is required.</span></span> <span data-ttu-id="97447-133">标记名称可以重复使用。</span><span class="sxs-lookup"><span data-stu-id="97447-133">A mark name can be reused.</span></span> <span data-ttu-id="97447-134">事务日志记录标记名称、描述、数据库、用户、日期时间信息以及日志序列号 (LSN)。</span><span class="sxs-lookup"><span data-stu-id="97447-134">The transaction log records the mark name, description, database, user, datetime information, and the log sequence number (LSN).</span></span> <span data-ttu-id="97447-135">日期时间信息与标记名称一起使用，以便对标记进行唯一标识。</span><span class="sxs-lookup"><span data-stu-id="97447-135">The datetime information is used along with the mark name to uniquely identify the mark.</span></span>  
  
 <span data-ttu-id="97447-136">**在数据库集中创建标记事务：**</span><span class="sxs-lookup"><span data-stu-id="97447-136">**To create marked transactions in a set of databases:**</span></span>  
  
1.  <span data-ttu-id="97447-137">用 BEGIN TRAN 语句命名事务，并使用 WITH MARK 子句。</span><span class="sxs-lookup"><span data-stu-id="97447-137">Name the transaction in the BEGIN TRAN statement and use the WITH MARK clause</span></span>  
  
     <span data-ttu-id="97447-138">你可以在现有事务中嵌套 BEGIN TRAN *new_mark_name* WITH MARK 语句。</span><span class="sxs-lookup"><span data-stu-id="97447-138">You can nest the statement BEGIN TRAN *new_mark_name* WITH MARK within an existing transaction.</span></span> <span data-ttu-id="97447-139">即使事务拥有事务名称， *new_mark_name* 的值也是事务的标记名称。</span><span class="sxs-lookup"><span data-stu-id="97447-139">The value of *new_mark_name* is the mark name for the transaction, even if the transaction possesses a transaction name.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="97447-140">如果执行第二个嵌套 BEGIN TRAN...WITH MARK，那么将跳过该语句，但会导致出现警告消息。</span><span class="sxs-lookup"><span data-stu-id="97447-140">If you issue a second nested BEGIN TRAN...WITH MARK, that statement is skipped but causes a warning message.</span></span>  
  
2.  <span data-ttu-id="97447-141">对数据库集中的所有数据库进行更新。</span><span class="sxs-lookup"><span data-stu-id="97447-141">Run an update against all of the databases in the set.</span></span>  
  
     <span data-ttu-id="97447-142">将仅在执行 BEGIN TRAN...WITH MARK 语句的服务器实例上的事务日志中插入特定事务的标记。</span><span class="sxs-lookup"><span data-stu-id="97447-142">The mark for a specific transaction is inserted into transaction logs only on the server instance where the BEGIN TRAN...WITH MARK statement is executed.</span></span> <span data-ttu-id="97447-143">事务标记放置在由该服务器实例上的标记事务更新过的各数据库的事务日志中。</span><span class="sxs-lookup"><span data-stu-id="97447-143">The transaction mark is placed in the transaction log of every database updated by the marked transaction on that server instance.</span></span> <span data-ttu-id="97447-144">如果数据库位于不同的服务器实例上，则必须在各服务器实例上创建相同的标记。</span><span class="sxs-lookup"><span data-stu-id="97447-144">If the databases reside on different server instances, identical marks must be created on each of the server instances.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="97447-145">示例</span><span class="sxs-lookup"><span data-stu-id="97447-145">Examples</span></span>  
 <span data-ttu-id="97447-146">下面的示例将事务日志还原到名为 `ListPriceUpdate`的标记事务中的标记处。</span><span class="sxs-lookup"><span data-stu-id="97447-146">The following example restores the transaction log to the mark in the marked transaction named `ListPriceUpdate`.</span></span>  
  
```sql  
USE AdventureWorks  
GO  
BEGIN TRANSACTION ListPriceUpdate  
   WITH MARK 'UPDATE Product list prices';  
GO  
  
UPDATE Production.Product  
   SET ListPrice = ListPrice * 1.10  
   WHERE ProductNumber LIKE 'BK-%';  
GO  
  
COMMIT TRANSACTION ListPriceUpdate;  
GO  
  
-- Time passes. Regular database   
-- and log backups are taken.  
-- An error occurs in the database.  
USE master  
GO  
  
RESTORE DATABASE AdventureWorks  
FROM AdventureWorksBackups  
WITH FILE = 3, NORECOVERY;  
GO  
  
RESTORE LOG AdventureWorks  
   FROM AdventureWorksBackups   
   WITH FILE = 4,  
   RECOVERY,   
   STOPATMARK = 'ListPriceUpdate';  
```  
  
## <a name="forcing-a-mark-to-spread-to-other-servers"></a><span data-ttu-id="97447-147">强制将标记分布到其他服务器</span><span class="sxs-lookup"><span data-stu-id="97447-147">Forcing a Mark to Spread to Other Servers</span></span>  
 <span data-ttu-id="97447-148">事务分散到其他服务器时，事务标记名称不会自动分布到其他服务器。</span><span class="sxs-lookup"><span data-stu-id="97447-148">A transaction mark name is not automatically distributed to another server as the transaction spreads there.</span></span> <span data-ttu-id="97447-149">若要强制标记分散到其他服务器，必须编写包含 BEGIN TRAN *名称* WITH MARK 语句的存储过程。</span><span class="sxs-lookup"><span data-stu-id="97447-149">To force the mark to spread to the other servers, a stored procedure must be written that contains a BEGIN TRAN *name* WITH MARK statement.</span></span> <span data-ttu-id="97447-150">然后，必须在发起服务器上的事务作用域下，在远程服务器上执行该存储过程。</span><span class="sxs-lookup"><span data-stu-id="97447-150">That stored procedure must then be executed on the remote server under the scope of the transaction in the originating server.</span></span>  
  
 <span data-ttu-id="97447-151">例如，假设多个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例上存在分区数据库。</span><span class="sxs-lookup"><span data-stu-id="97447-151">For example, consider a partitioned database that exists on multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="97447-152">每个实例上都有一个名为 `coyote`的数据库。</span><span class="sxs-lookup"><span data-stu-id="97447-152">On each instance is a database named `coyote`.</span></span> <span data-ttu-id="97447-153">首先，在每个数据库中创建一个存储过程，例如， `sp_SetMark`。</span><span class="sxs-lookup"><span data-stu-id="97447-153">First, in every database, create a stored procedure, for example, `sp_SetMark`.</span></span>  
  
```sql  
CREATE PROCEDURE sp_SetMark  
@name nvarchar (128)  
AS  
BEGIN TRANSACTION @name WITH MARK  
UPDATE coyote.dbo.Marks SET one = 1  
COMMIT TRANSACTION;  
GO  
```  
  
 <span data-ttu-id="97447-154">然后，创建包含在每个数据库中放置标记的事务的存储过程 `sp_MarkAll` 。</span><span class="sxs-lookup"><span data-stu-id="97447-154">Next, create stored procedure `sp_MarkAll` containing a transaction that places a mark in every database.</span></span> <span data-ttu-id="97447-155">`sp_MarkAll` 可以从任意实例中运行。</span><span class="sxs-lookup"><span data-stu-id="97447-155">`sp_MarkAll` can be run from any of the instances.</span></span>  
  
```sql  
CREATE PROCEDURE sp_MarkAll  
@name nvarchar (128)  
AS  
BEGIN TRANSACTION  
EXEC instance0.coyote.dbo.sp_SetMark @name  
EXEC instance1.coyote.dbo.sp_SetMark @name  
EXEC instance2.coyote.dbo.sp_SetMark @name  
COMMIT TRANSACTION;  
GO  
```  
  
### <a name="two-phase-commit"></a><span data-ttu-id="97447-156">两阶段提交</span><span class="sxs-lookup"><span data-stu-id="97447-156">Two-Phase Commit</span></span>  
 <span data-ttu-id="97447-157">提交分布式事务分为两个阶段：准备和提交。</span><span class="sxs-lookup"><span data-stu-id="97447-157">Committing a distributed transaction occurs in two phases: prepare and commit.</span></span> <span data-ttu-id="97447-158">提交标记事务时，标记事务中每个数据库的提交日志记录都放在日志的某一点处，以使任何日志中不存在有疑问的事务。</span><span class="sxs-lookup"><span data-stu-id="97447-158">When a marked transaction is committed, the commit log record for each database in the marked transaction is placed in the log at a point where there are no in-doubt transactions in any of the logs.</span></span> <span data-ttu-id="97447-159">此点保证不存在这样的事务：在一个日志中显示为已提交，在另一个日志中显示为未提交。</span><span class="sxs-lookup"><span data-stu-id="97447-159">At this point, it is guaranteed that there are no transactions that appear as committed in one log, but not committed in another log.</span></span>  
  
 <span data-ttu-id="97447-160">为此，可在提交标记事务的过程中执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="97447-160">The following steps accomplish this during the commit of a marked transaction:</span></span>  
  
1.  <span data-ttu-id="97447-161">标记事务的准备阶段停止所有新的准备和提交。</span><span class="sxs-lookup"><span data-stu-id="97447-161">Prepare phase of a marking transaction stalls all new prepares and commits.</span></span>  
  
2.  <span data-ttu-id="97447-162">仅允许继续提交准备好的事务。</span><span class="sxs-lookup"><span data-stu-id="97447-162">Only commits of already prepared transactions are allowed to continue.</span></span>  
  
3.  <span data-ttu-id="97447-163">标记事务将等待耗尽所有准备好的事务（带超时设置）。</span><span class="sxs-lookup"><span data-stu-id="97447-163">Marking transaction then waits for all prepared transactions to drain (with time-out).</span></span>  
  
4.  <span data-ttu-id="97447-164">准备并提交标记事务。</span><span class="sxs-lookup"><span data-stu-id="97447-164">Marked transaction is prepared and committed.</span></span>  
  
5.  <span data-ttu-id="97447-165">取消停止新的准备和提交。</span><span class="sxs-lookup"><span data-stu-id="97447-165">The stall of new prepares and commits is removed.</span></span>  
  
 <span data-ttu-id="97447-166">由跨多个数据库的标记事务产生的停止会降低服务器的事务处理性能。</span><span class="sxs-lookup"><span data-stu-id="97447-166">The stalls generated by marked transactions that span multiple databases can reduce the transaction processing performance of the server.</span></span>  
  
 <span data-ttu-id="97447-167">建议不要运行并发标记事务。</span><span class="sxs-lookup"><span data-stu-id="97447-167">We recommend that you do not run concurrent marked transactions.</span></span> <span data-ttu-id="97447-168">虽然很少见，但分布式标记事务有可能与其他同时提交的分布式标记事务发生死锁。</span><span class="sxs-lookup"><span data-stu-id="97447-168">It is rare but possible for the commit of a distributed marked transaction to deadlock with other distributed marked transactions that are committing at the same time.</span></span> <span data-ttu-id="97447-169">出现这种情况时，正在标记的事务将被选作死锁牺牲品并回滚。</span><span class="sxs-lookup"><span data-stu-id="97447-169">When this happens, the marking transaction is chosen as the deadlock victim and is rolled back.</span></span> <span data-ttu-id="97447-170">出现此错误时，应用程序会重试标记事务。</span><span class="sxs-lookup"><span data-stu-id="97447-170">When this error occurs, the application can retry the marked transaction.</span></span> <span data-ttu-id="97447-171">多个标记事务尝试同时提交时，发生死锁的可能性较大。</span><span class="sxs-lookup"><span data-stu-id="97447-171">When multiple marked transactions try to commit concurrently, there is a higher probability of deadlock.</span></span>  
  
## <a name="recovering-to-a-marked-transaction"></a><span data-ttu-id="97447-172">恢复到标记的事务</span><span class="sxs-lookup"><span data-stu-id="97447-172">Recovering to a Marked Transaction</span></span>  
 <span data-ttu-id="97447-173">有关如何将包含标记事务的数据库恢复到特定标记或仅恢复到特定标记之前，请参阅 [包含标记事务的相关数据库恢复](recovery-of-related-databases-that-contain-marked-transaction.md)。</span><span class="sxs-lookup"><span data-stu-id="97447-173">For information about how to recover a database that contains marked transactions to or just before a particular mark, see [Recovery of Related  Databases That Contain Marked Transaction](recovery-of-related-databases-that-contain-marked-transaction.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97447-174">另请参阅</span><span class="sxs-lookup"><span data-stu-id="97447-174">See Also</span></span>  
 <span data-ttu-id="97447-175">[BEGIN DISTRIBUTED TRANSACTION (Transact-SQL)](/sql/t-sql/language-elements/begin-distributed-transaction-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="97447-175">[BEGIN DISTRIBUTED TRANSACTION &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/begin-distributed-transaction-transact-sql) </span></span>  
 <span data-ttu-id="97447-176">[备份和还原系统数据库 (SQL Server)](back-up-and-restore-of-system-databases-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="97447-176">[Back Up and Restore of System Databases &#40;SQL Server&#41;](back-up-and-restore-of-system-databases-sql-server.md) </span></span>  
 <span data-ttu-id="97447-177">[BEGIN TRANSACTION (Transact-SQL)](/sql/t-sql/language-elements/begin-transaction-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="97447-177">[BEGIN TRANSACTION &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/begin-transaction-transact-sql) </span></span>  
 <span data-ttu-id="97447-178">[应用事务日志备份 (SQL Server)](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="97447-178">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 <span data-ttu-id="97447-179">[完整数据库备份 (SQL Server)](full-database-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="97447-179">[Full Database Backups &#40;SQL Server&#41;](full-database-backups-sql-server.md) </span></span>  
 <span data-ttu-id="97447-180">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="97447-180">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="97447-181">包含标记的事务的相关数据库的恢复</span><span class="sxs-lookup"><span data-stu-id="97447-181">Recovery of Related  Databases That Contain Marked Transaction</span></span>](recovery-of-related-databases-that-contain-marked-transaction.md)  
  
  
