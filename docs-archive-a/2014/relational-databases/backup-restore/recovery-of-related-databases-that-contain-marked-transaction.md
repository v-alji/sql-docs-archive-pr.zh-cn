---
title: 包含标记的事务的相关数据库的恢复 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- transaction logs [SQL Server], marks
- STOPBEFOREMARK option [RESTORE statement]
- STOPATMARK option [RESTORE statement]
- point in time recovery [SQL Server]
- restoring databases [SQL Server], point in time
- recovery [SQL Server], databases
- restoring [SQL Server], point in time
- transactions [SQL Server], recovering to a mark
- database recovery [SQL Server]
- marked transactions [SQL Server], restoring
- database restores [SQL Server], point in time
ms.assetid: 77a0d9c0-978a-4891-8b0d-a4256c81c3f8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b968322f92c7a135adb5fd0733b5774e7562bc39
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691758"
---
# <a name="recovery-of-related--databases-that-contain-marked-transaction"></a><span data-ttu-id="ef4aa-102">包含标记事务的相关数据库恢复</span><span class="sxs-lookup"><span data-stu-id="ef4aa-102">Recovery of Related  Databases That Contain Marked Transaction</span></span>
  <span data-ttu-id="ef4aa-103">本主题仅适用于那些包含标记事务和使用完整或大容量日志恢复模式的数据库。</span><span class="sxs-lookup"><span data-stu-id="ef4aa-103">This topic is relevant only for databases that contain marked transactions and that use the full or bulk-logged recovery models.</span></span>  
  
 <span data-ttu-id="ef4aa-104">有关还原到特定恢复点的要求的详细信息，请参阅 [将 SQL Server 数据库还原到某个时间点（完整恢复模式）](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)。</span><span class="sxs-lookup"><span data-stu-id="ef4aa-104">For information about the requirements for restoring to a specific recovery point, see [Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md).</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ef4aa-105">支持将命名标记插入到事务日志中，以便恢复到该特定标记。</span><span class="sxs-lookup"><span data-stu-id="ef4aa-105">supports inserting named marks into the transaction log to allow recovery to that specific mark.</span></span> <span data-ttu-id="ef4aa-106">日志标记因事务而异，并且只有在提交与其关联的事务时才会插入。</span><span class="sxs-lookup"><span data-stu-id="ef4aa-106">Log marks are transaction specific and are inserted only if their associated transaction commits.</span></span> <span data-ttu-id="ef4aa-107">因此可将标记绑定到特定的工作上，而且可恢复到包含或排除此工作的点。</span><span class="sxs-lookup"><span data-stu-id="ef4aa-107">As a result, marks can be tied to specific work, and you can recover to a point that includes or excludes this work.</span></span>  
  
 <span data-ttu-id="ef4aa-108">将命名标记插入事务日志之前，请先考虑以下事项：</span><span class="sxs-lookup"><span data-stu-id="ef4aa-108">Before you insert named marks into the transaction log, consider the following:</span></span>  
  
-   <span data-ttu-id="ef4aa-109">由于事务标记会消耗日志空间，应只对在数据库恢复策略中起重要作用的事务使用标记。</span><span class="sxs-lookup"><span data-stu-id="ef4aa-109">Because transaction marks consume log space, use them only for transactions that play a significant role in the database recovery strategy.</span></span>  
  
-   <span data-ttu-id="ef4aa-110">标记的事务提交之后，在 [msdb](/sql/relational-databases/system-tables/logmarkhistory-transact-sql) 的 **logmarkhistory**表中插入一行。</span><span class="sxs-lookup"><span data-stu-id="ef4aa-110">After a marked transaction commits, a row is inserted in the [logmarkhistory](/sql/relational-databases/system-tables/logmarkhistory-transact-sql) table in **msdb**.</span></span>  
  
-   <span data-ttu-id="ef4aa-111">如果一个标记的事务跨同一数据库服务器或不同服务器上的多个数据库，这些标记将记录在所有受影响的数据库的日志内。</span><span class="sxs-lookup"><span data-stu-id="ef4aa-111">If a marked transaction spans multiple databases on the same database server or on different servers, the marks must be recorded in the logs of all the affected databases.</span></span> <span data-ttu-id="ef4aa-112">有关详细信息，请参阅 [使用标记的事务一致地恢复相关的数据库的事务（完全恢复模式）](use-marked-transactions-to-recover-related-databases-consistently.md)。</span><span class="sxs-lookup"><span data-stu-id="ef4aa-112">For more information, see [Use Marked Transactions to Recover Related Databases Consistently &#40;Full Recovery Model&#41;](use-marked-transactions-to-recover-related-databases-consistently.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ef4aa-113">有关如何标记事务的信息，请参阅 [使用标记的事务一致地恢复相关的数据库的事务（完全恢复模式）](use-marked-transactions-to-recover-related-databases-consistently.md)。</span><span class="sxs-lookup"><span data-stu-id="ef4aa-113">For information about how to mark transactions, see [Use Marked Transactions to Recover Related Databases Consistently &#40;Full Recovery Model&#41;](use-marked-transactions-to-recover-related-databases-consistently.md).</span></span>  
  
## <a name="transact-sql-syntax-for-inserting-named-marks-into-a-transaction-log"></a><span data-ttu-id="ef4aa-114">在事务日志中插入命名标记的 Transact-SQL 语法</span><span class="sxs-lookup"><span data-stu-id="ef4aa-114">Transact-SQL Syntax for Inserting Named Marks into a Transaction Log</span></span>  
 <span data-ttu-id="ef4aa-115">若要将标记插入到事务日志中，请使用 [BEGIN TRANSACTION](/sql/t-sql/language-elements/begin-transaction-transact-sql) 语句和 WITH MARK [*description*] 子句。</span><span class="sxs-lookup"><span data-stu-id="ef4aa-115">To insert marks into the transaction logs, use the [BEGIN TRANSACTION](/sql/t-sql/language-elements/begin-transaction-transact-sql) statement and the WITH MARK [*description*] clause.</span></span> <span data-ttu-id="ef4aa-116">标记的名称与事务的名称相同。</span><span class="sxs-lookup"><span data-stu-id="ef4aa-116">The mark is named the same as the transaction.</span></span> <span data-ttu-id="ef4aa-117">可选的 *description* 是标记的文本说明而不是标记名。</span><span class="sxs-lookup"><span data-stu-id="ef4aa-117">The optional *description* is a textual description of the mark, not the mark name.</span></span> <span data-ttu-id="ef4aa-118">例如，在以下 `BEGIN TRANSACTION` 语句中创建的事务和标记的名称均为 `Tx1`：</span><span class="sxs-lookup"><span data-stu-id="ef4aa-118">For example, the name of both the transaction and the mark that is created in the following `BEGIN TRANSACTION` statement is `Tx1`:</span></span>  
  
```wmimof  
BEGIN TRANSACTION Tx1 WITH MARK 'not the mark name, just a description'    
```  
  
 <span data-ttu-id="ef4aa-119">事务日志记录了标记名（事务名）、说明、数据库、用户、`datetime` 信息和日志序列号 (LSN)。</span><span class="sxs-lookup"><span data-stu-id="ef4aa-119">The transaction log records the mark name (transaction name), description, database, user, `datetime` information, and the log sequence number (LSN).</span></span> <span data-ttu-id="ef4aa-120">`datetime` 信息与标记名一起用于唯一地标识标记。</span><span class="sxs-lookup"><span data-stu-id="ef4aa-120">The `datetime` information is used with the mark name to uniquely identify the mark.</span></span>  
  
 <span data-ttu-id="ef4aa-121">有关如何将标记插入跨多个数据库的事务的信息，请参阅 [使用标记的事务一致地恢复相关的数据库的事务（完全恢复模式）](use-marked-transactions-to-recover-related-databases-consistently.md)。</span><span class="sxs-lookup"><span data-stu-id="ef4aa-121">For information about how to insert a mark into a transaction that spans multiple databases, see [Use Marked Transactions to Recover Related Databases Consistently &#40;Full Recovery Model&#41;](use-marked-transactions-to-recover-related-databases-consistently.md).</span></span>  
  
## <a name="transact-sql-syntax-for-recovering-to-a-mark"></a><span data-ttu-id="ef4aa-122">恢复到某个标记的 Transact-SQL 语法</span><span class="sxs-lookup"><span data-stu-id="ef4aa-122">Transact-SQL Syntax for Recovering to a Mark</span></span>  
 <span data-ttu-id="ef4aa-123">使用[RESTORE LOG](/sql/t-sql/statements/restore-statements-transact-sql)语句将某个标记的事务作为目标时，可以使用以下子句之一在标记处或在紧邻其之前的位置处停止：</span><span class="sxs-lookup"><span data-stu-id="ef4aa-123">When you target a marked transaction by using a[RESTORE LOG](/sql/t-sql/statements/restore-statements-transact-sql)statement, you can use one the following clauses to stop at or immediately before the mark:</span></span>  
  
-   <span data-ttu-id="ef4aa-124">使用 WITH STOPATMARK = **' *`<mark_name>`* '** 子句将标记事务指定为恢复点。</span><span class="sxs-lookup"><span data-stu-id="ef4aa-124">Use the WITH STOPATMARK = **'*`<mark_name>`*'** clause to specify that the marked transaction is the recovery point.</span></span>  
  
     <span data-ttu-id="ef4aa-125">STOPATMARK 前滚到标记处，并在前滚中包含标记的事务。</span><span class="sxs-lookup"><span data-stu-id="ef4aa-125">STOPATMARK rolls forward to the mark and includes the marked transaction in the roll forward.</span></span>  
  
-   <span data-ttu-id="ef4aa-126">使用 WITH STOPBEFOREMARK = **' *`<mark_name>`* '** 子句来指定紧靠在标记之前的日志记录是恢复点。</span><span class="sxs-lookup"><span data-stu-id="ef4aa-126">Use the WITH STOPBEFOREMARK = **'*`<mark_name>`*'** clause to specify that the log record that is immediately before the mark is the recovery point.</span></span>  
  
     <span data-ttu-id="ef4aa-127">STOPBEFOREMARK 前滚到标记处，但在前滚中不包含标记的事务。</span><span class="sxs-lookup"><span data-stu-id="ef4aa-127">STOPBEFOREMARK rolls forward to the mark and excludes marked the transaction from the roll forward.</span></span>  
  
 <span data-ttu-id="ef4aa-128">STOPATMARK 和 STOPBEFOREMARK 选项均支持可选的 AFTER *datetime* 子句。</span><span class="sxs-lookup"><span data-stu-id="ef4aa-128">The STOPATMARK and STOPBEFOREMARK options both support an optional AFTER *datetime* clause.</span></span> <span data-ttu-id="ef4aa-129">使用 *datetime* 时，标记名不必是唯一的。</span><span class="sxs-lookup"><span data-stu-id="ef4aa-129">When *datetime* is used, mark names do not have to be unique.</span></span>  
  
 <span data-ttu-id="ef4aa-130">如果省略了 AFTER *datetime* ，则前滚操作将于达到含有指定名称的第一个标记处停止。</span><span class="sxs-lookup"><span data-stu-id="ef4aa-130">If AFTER *datetime* is omitted, roll forward stops at the first mark that has the specified name.</span></span> <span data-ttu-id="ef4aa-131">如果指定了 AFTER *datetime* ，则前滚操作将于达到 *datetime*时或之后在具有指定名称的第一个标记处停止。</span><span class="sxs-lookup"><span data-stu-id="ef4aa-131">If AFTER *datetime* is specified, roll forward stops at the first mark that has the specified name, exactly at or after *datetime*.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ef4aa-132">对于所有时点还原操作而言，如果数据库正在执行成批记录的操作，则不允许恢复到标记。</span><span class="sxs-lookup"><span data-stu-id="ef4aa-132">As in all point-in-time restore operations, recovering to a mark is disallowed when the database is undergoing operations that are bulk-logged.</span></span>  
  
 <span data-ttu-id="ef4aa-133">**还原到标记的事务**</span><span class="sxs-lookup"><span data-stu-id="ef4aa-133">**To restore to a marked transaction**</span></span>  
  
 [<span data-ttu-id="ef4aa-134">将数据库还原到标记的事务 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="ef4aa-134">Restore a Database to a Marked Transaction &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-to-a-marked-transaction-sql-server-management-studio.md)  
  
 [<span data-ttu-id="ef4aa-135">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ef4aa-135">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
### <a name="preparing-the-log-backups"></a><span data-ttu-id="ef4aa-136">为日志备份做准备</span><span class="sxs-lookup"><span data-stu-id="ef4aa-136">Preparing the Log Backups</span></span>  
 <span data-ttu-id="ef4aa-137">在此示例中，适合这两个相关数据库的备份策略如下：</span><span class="sxs-lookup"><span data-stu-id="ef4aa-137">For this example, an appropriate backup strategy for these related databases would be the following:</span></span>  
  
1.  <span data-ttu-id="ef4aa-138">对于这两个数据库，使用完整恢复模式。</span><span class="sxs-lookup"><span data-stu-id="ef4aa-138">Use the full recovery model for both databases.</span></span>  
  
2.  <span data-ttu-id="ef4aa-139">创建每个数据库的完整备份。</span><span class="sxs-lookup"><span data-stu-id="ef4aa-139">Create a full backup of each database.</span></span>  
  
     <span data-ttu-id="ef4aa-140">可以按顺序或同时备份数据库。</span><span class="sxs-lookup"><span data-stu-id="ef4aa-140">The databases can be backed up sequentially or simultaneously.</span></span>  
  
3.  <span data-ttu-id="ef4aa-141">备份事务日志之前，标记在所有数据库中执行的事务。</span><span class="sxs-lookup"><span data-stu-id="ef4aa-141">Before backing up the transaction log, mark a transaction that executes in all databases.</span></span> <span data-ttu-id="ef4aa-142">有关如何创建标记事务的详细信息，请参阅 [使用标记的事务一致地恢复相关的数据库的事务（完全恢复模式）](use-marked-transactions-to-recover-related-databases-consistently.md)。</span><span class="sxs-lookup"><span data-stu-id="ef4aa-142">For information about how to create the marked transactions, see [Use Marked Transactions to Recover Related Databases Consistently &#40;Full Recovery Model&#41;](use-marked-transactions-to-recover-related-databases-consistently.md).</span></span>  
  
4.  <span data-ttu-id="ef4aa-143">备份每个数据库中的事务日志。</span><span class="sxs-lookup"><span data-stu-id="ef4aa-143">Back up the transaction log on each database.</span></span>  
  
### <a name="recovering-the-database-to-a-marked-transaction"></a><span data-ttu-id="ef4aa-144">将数据库恢复到标记事务</span><span class="sxs-lookup"><span data-stu-id="ef4aa-144">Recovering the Database to a Marked Transaction</span></span>  
 <span data-ttu-id="ef4aa-145">**还原备份**</span><span class="sxs-lookup"><span data-stu-id="ef4aa-145">**To restore the backup**</span></span>  
  
1.  <span data-ttu-id="ef4aa-146">如有可能，创建未损坏的数据库的 [结尾日志备份](tail-log-backups-sql-server.md) 。</span><span class="sxs-lookup"><span data-stu-id="ef4aa-146">Create [tail-log backups](tail-log-backups-sql-server.md) of the undamaged databases, if possible.</span></span>  
  
2.  <span data-ttu-id="ef4aa-147">还原每个数据库最近的完整数据库备份。</span><span class="sxs-lookup"><span data-stu-id="ef4aa-147">Restore the most recent full database backup of each database.</span></span>  
  
3.  <span data-ttu-id="ef4aa-148">标识可用于所有事务日志备份的最新标记事务。</span><span class="sxs-lookup"><span data-stu-id="ef4aa-148">Identify the most recent marked transaction that is available in all of the transaction log backups.</span></span> <span data-ttu-id="ef4aa-149">此信息存储在每个服务器的 **msdb** 数据库中的 **logmarkhistory** 表中。</span><span class="sxs-lookup"><span data-stu-id="ef4aa-149">This information is stored in the **logmarkhistory** table in the **msdb** database on each server.</span></span>  
  
4.  <span data-ttu-id="ef4aa-150">标识包含此标记的所有相关数据库的日志备份。</span><span class="sxs-lookup"><span data-stu-id="ef4aa-150">Identify the log backups for all related databases that contain this mark.</span></span>  
  
5.  <span data-ttu-id="ef4aa-151">还原每个日志备份，在标记事务处停止。</span><span class="sxs-lookup"><span data-stu-id="ef4aa-151">Restore each log backup, stopping at the marked transaction.</span></span>  
  
6.  <span data-ttu-id="ef4aa-152">恢复每个数据库。</span><span class="sxs-lookup"><span data-stu-id="ef4aa-152">Recover each database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef4aa-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ef4aa-153">See Also</span></span>  
 <span data-ttu-id="ef4aa-154">[BEGIN TRANSACTION (Transact-SQL)](/sql/t-sql/language-elements/begin-transaction-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ef4aa-154">[BEGIN TRANSACTION &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/begin-transaction-transact-sql) </span></span>  
 <span data-ttu-id="ef4aa-155">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ef4aa-155">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="ef4aa-156">[应用事务日志备份 (SQL Server)](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ef4aa-156">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 <span data-ttu-id="ef4aa-157">[使用标记的事务一致地恢复相关的数据库的事务（完全恢复模式）](use-marked-transactions-to-recover-related-databases-consistently.md) </span><span class="sxs-lookup"><span data-stu-id="ef4aa-157">[Use Marked Transactions to Recover Related Databases Consistently &#40;Full Recovery Model&#41;](use-marked-transactions-to-recover-related-databases-consistently.md) </span></span>  
 <span data-ttu-id="ef4aa-158">[还原和恢复概述 (SQL Server)](restore-and-recovery-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ef4aa-158">[Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span></span>  
 <span data-ttu-id="ef4aa-159">[将 SQL Server 数据库还原到某个时间点（完整恢复模式）](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="ef4aa-159">[Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md) </span></span>  
 [<span data-ttu-id="ef4aa-160">计划和执行还原顺序（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="ef4aa-160">Plan and Perform Restore Sequences &#40;Full Recovery Model&#41;</span></span>](plan-and-perform-restore-sequences-full-recovery-model.md)  
  
  
