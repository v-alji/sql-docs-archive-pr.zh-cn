---
title: 应用事务日志备份 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- restoring [SQL Server], log backups
- transaction log backups [SQL Server], applying backups
- online restores [SQL Server], log backups
- transaction log backups [SQL Server], quantity needed for restore sequence
- backups [SQL Server], log backups
ms.assetid: 9b12be51-5469-46f9-8e86-e938e10aa3a1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 54c91106f8ca6f15539b4103220860143882c3ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581335"
---
# <a name="apply-transaction-log-backups-sql-server"></a><span data-ttu-id="ab769-102">应用事务日志备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ab769-102">Apply Transaction Log Backups (SQL Server)</span></span>
  <span data-ttu-id="ab769-103">本主题只与完整恢复模式或大容量日志恢复模式相关。</span><span class="sxs-lookup"><span data-stu-id="ab769-103">The topic is relevant only for the full recovery model or bulk-logged recovery model.</span></span>  
  
 <span data-ttu-id="ab769-104">本主题介绍在还原 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库过程中应用事务日志备份。</span><span class="sxs-lookup"><span data-stu-id="ab769-104">This topic describes applying transaction log backups as part of restoring a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="ab769-105">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="ab769-105">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="ab769-106">还原事务日志备份的要求</span><span class="sxs-lookup"><span data-stu-id="ab769-106">Requirements for Restoring Transaction Log Backups</span></span>](#Requirements)  
  
-   [<span data-ttu-id="ab769-107">恢复和事务日志</span><span class="sxs-lookup"><span data-stu-id="ab769-107">Recovery and Transaction Logs</span></span>](#RecoveryAndTlogs)  
  
-   [<span data-ttu-id="ab769-108">使用日志备份来还原故障点</span><span class="sxs-lookup"><span data-stu-id="ab769-108">Using Log Backups to Restore to the Point of Failure</span></span>](#PITrestore)  
  
-   [<span data-ttu-id="ab769-109">相关任务</span><span class="sxs-lookup"><span data-stu-id="ab769-109">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="requirements-for-restoring-transaction-log-backups"></a><a name="Requirements"></a><span data-ttu-id="ab769-110">还原事务日志备份的要求</span><span class="sxs-lookup"><span data-stu-id="ab769-110">Requirements for Restoring Transaction Log Backups</span></span>  
 <span data-ttu-id="ab769-111">若要应用事务日志备份，必须满足下列要求：</span><span class="sxs-lookup"><span data-stu-id="ab769-111">To apply a transaction log backup, the following requirements must be met:</span></span>  
  
-   <span data-ttu-id="ab769-112">**为还原顺序准备足够的日志备份：** 必须备份足够的日志记录，才能完成还原顺序。</span><span class="sxs-lookup"><span data-stu-id="ab769-112">**Enough Log Backups for a Restore Sequence :** You must have enough log records backed up to complete a restore sequence.</span></span> <span data-ttu-id="ab769-113">必要的日志备份（需要时包含 [结尾日志备份](tail-log-backups-sql-server.md) ）必须在还原顺序开始之前可用。</span><span class="sxs-lookup"><span data-stu-id="ab769-113">The necessary log backups, including the [tail-log backup](tail-log-backups-sql-server.md) where required, must be available before the start of the restore sequence.</span></span>  
  
-   <span data-ttu-id="ab769-114">**正确的还原顺序：** 必须先还原上一个完整数据库备份或差异数据库备份。</span><span class="sxs-lookup"><span data-stu-id="ab769-114">**Correct restore order:**  The immediately previous full database backup or differential database backup must be restored first.</span></span> <span data-ttu-id="ab769-115">然后，在完整数据库备份或差异数据库备份后创建的所有事务日志必须按时间顺序还原。</span><span class="sxs-lookup"><span data-stu-id="ab769-115">Then, all transaction logs that are created after that full or differential database backup must be restored in chronological order.</span></span> <span data-ttu-id="ab769-116">如果此事务日志链中的事务日志备份丢失或损坏，则您只能还原丢失的事务日志之前的事务日志。</span><span class="sxs-lookup"><span data-stu-id="ab769-116">If a transaction log backup in this log chain is lost or damaged, you can restore only transaction logs before the missing transaction log.</span></span>  
  
-   <span data-ttu-id="ab769-117">**数据库尚未恢复：** 除非已应用最后的事务日志，否则无法恢复数据库。</span><span class="sxs-lookup"><span data-stu-id="ab769-117">**Database not yet recovered:**  The database cannot be recovered until after the final transaction log has been applied.</span></span> <span data-ttu-id="ab769-118">如果要在还原其中一个中间事务日志备份之后恢复数据库，则在日志链结束之前，除非从完整数据库备份开始重新启动整个还原顺序，否则，将无法还原该点之前的数据库。</span><span class="sxs-lookup"><span data-stu-id="ab769-118">If you recover the database after restoring one of the intermediate transaction log backups, that before the end of the log chain, you cannot restore the database past that point without restarting the complete restore sequence, starting with the full database backup.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="ab769-119">最佳方法是还原所有日志备份 (RESTORE LOG *database_name* WITH NORECOVERY)。</span><span class="sxs-lookup"><span data-stu-id="ab769-119">A best practice is to restore all the log backups (RESTORE LOG *database_name* WITH NORECOVERY).</span></span> <span data-ttu-id="ab769-120">还原上一次日志备份后，用单独的操作恢复数据库 (RESTORE DATABASE *database_name* WITH RECOVERY)。</span><span class="sxs-lookup"><span data-stu-id="ab769-120">Then, after restoring the last log backup, recover the database in a separate operation (RESTORE DATABASE *database_name* WITH RECOVERY).</span></span>  
  
##  <a name="recovery-and-transaction-logs"></a><a name="RecoveryAndTlogs"></a><span data-ttu-id="ab769-121">恢复和事务日志</span><span class="sxs-lookup"><span data-stu-id="ab769-121">Recovery and Transaction Logs</span></span>  
 <span data-ttu-id="ab769-122">当您完成还原操作并恢复数据库后，恢复将回滚所有未完成的事务。</span><span class="sxs-lookup"><span data-stu-id="ab769-122">When you finish the restore operation and recover the database, recovery rolls back all incomplete transactions.</span></span> <span data-ttu-id="ab769-123">此步骤称为“撤消阶段” \*\*。</span><span class="sxs-lookup"><span data-stu-id="ab769-123">This is known as the *undo phase*.</span></span> <span data-ttu-id="ab769-124">回滚对还原数据库的完整性是必需的。</span><span class="sxs-lookup"><span data-stu-id="ab769-124">Rolling back is required to restore the integrity of the database.</span></span> <span data-ttu-id="ab769-125">回滚后，数据库将进入联机状态，不能再将其他事务日志备份应用到数据库。</span><span class="sxs-lookup"><span data-stu-id="ab769-125">After rollback, the database goes online, and no more transaction log backups can be applied to the database.</span></span>  
  
 <span data-ttu-id="ab769-126">例如，一系列事务日志备份包含一个运行时间长的事务。</span><span class="sxs-lookup"><span data-stu-id="ab769-126">For example, a series of transaction log backups contain a long-running transaction.</span></span> <span data-ttu-id="ab769-127">该事务的起点记录在第一个事务日志备份中，终点记录在第二个事务日志备份中。</span><span class="sxs-lookup"><span data-stu-id="ab769-127">The start of the transaction is recorded in the first transaction log backup, but the end of the transaction is recorded in the second transaction log backup.</span></span> <span data-ttu-id="ab769-128">第一个事务日志备份中没有任何关于提交或回滚操作的记录。</span><span class="sxs-lookup"><span data-stu-id="ab769-128">There is no record of a commit or rollback operation in the first transaction log backup.</span></span> <span data-ttu-id="ab769-129">如果在应用第一个事务日志备份后运行恢复操作，则运行时间长的事务被视为未完成，并且将回滚事务的第一个事务日志备份中记录的数据修改。</span><span class="sxs-lookup"><span data-stu-id="ab769-129">If a recovery operation runs when the first transaction log backup is applied, the long-running transaction is treated as incomplete, and data modifications recorded in the first transaction log backup for the transaction are rolled back.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ab769-130">不允许在此点后应用第二个事务日志备份。</span><span class="sxs-lookup"><span data-stu-id="ab769-130">does not allow for the second transaction log backup to be applied after this point.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ab769-131">某些情况下可以在日志还原期间显式添加文件。</span><span class="sxs-lookup"><span data-stu-id="ab769-131">In some circumstances, you can explicitly add a file during log restore.</span></span>  
  
##  <a name="using-log-backups-to-restore-to-the-point-of-failure"></a><a name="PITrestore"></a><span data-ttu-id="ab769-132">使用日志备份还原到故障点</span><span class="sxs-lookup"><span data-stu-id="ab769-132">Using Log Backups to Restore to the Point of Failure</span></span>  
 <span data-ttu-id="ab769-133">假设有下列事件顺序。</span><span class="sxs-lookup"><span data-stu-id="ab769-133">Assume the following sequence of events.</span></span>  
  
|<span data-ttu-id="ab769-134">时间</span><span class="sxs-lookup"><span data-stu-id="ab769-134">Time</span></span>|<span data-ttu-id="ab769-135">事件</span><span class="sxs-lookup"><span data-stu-id="ab769-135">Event</span></span>|  
|----------|-----------|  
|<span data-ttu-id="ab769-136">上午 8:00</span><span class="sxs-lookup"><span data-stu-id="ab769-136">8:00 A.M.</span></span>|<span data-ttu-id="ab769-137">备份数据库以创建完整数据库备份。</span><span class="sxs-lookup"><span data-stu-id="ab769-137">Back up database to create a full database backup.</span></span>|  
|<span data-ttu-id="ab769-138">中午</span><span class="sxs-lookup"><span data-stu-id="ab769-138">Noon</span></span>|<span data-ttu-id="ab769-139">备份事务日志。</span><span class="sxs-lookup"><span data-stu-id="ab769-139">Back up transaction log.</span></span>|  
|<span data-ttu-id="ab769-140">下午 4:00</span><span class="sxs-lookup"><span data-stu-id="ab769-140">4:00 P.M.</span></span>|<span data-ttu-id="ab769-141">备份事务日志。</span><span class="sxs-lookup"><span data-stu-id="ab769-141">Back up transaction log.</span></span>|  
|<span data-ttu-id="ab769-142">下午 6:00</span><span class="sxs-lookup"><span data-stu-id="ab769-142">6:00 P.M.</span></span>|<span data-ttu-id="ab769-143">备份数据库以创建完整数据库备份。</span><span class="sxs-lookup"><span data-stu-id="ab769-143">Back up database to create a full database backup.</span></span>|  
|<span data-ttu-id="ab769-144">晚上 8:00</span><span class="sxs-lookup"><span data-stu-id="ab769-144">8:00 P.M.</span></span>|<span data-ttu-id="ab769-145">备份事务日志。</span><span class="sxs-lookup"><span data-stu-id="ab769-145">Back up transaction log.</span></span>|  
|<span data-ttu-id="ab769-146">晚上 9:45</span><span class="sxs-lookup"><span data-stu-id="ab769-146">9:45 P.M.</span></span>|<span data-ttu-id="ab769-147">出现故障。</span><span class="sxs-lookup"><span data-stu-id="ab769-147">Failure occurs.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="ab769-148">有关此示例备份顺序的说明，请参阅[事务日志备份 (SQL Server)](transaction-log-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ab769-148">For an explanation of this example sequence of backups, see [Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md).</span></span>  
  
 <span data-ttu-id="ab769-149">若要将数据库还原到晚上 9:45（故障点）时的状态，</span><span class="sxs-lookup"><span data-stu-id="ab769-149">To restore the database to its state at 9:45 P.M.</span></span> <span data-ttu-id="ab769-150">可以使用以下两种备选过程：</span><span class="sxs-lookup"><span data-stu-id="ab769-150">(the point of failure), either of the following alternative procedures can be used:</span></span>  
  
 <span data-ttu-id="ab769-151">**替换选项 1：使用最新的完整数据库备份还原数据库**</span><span class="sxs-lookup"><span data-stu-id="ab769-151">**Alternative 1: Restore the database by using the most recent full database backup**</span></span>  
  
1.  <span data-ttu-id="ab769-152">失败时创建当前活动事务日志的结尾日志备份。</span><span class="sxs-lookup"><span data-stu-id="ab769-152">Create a tail-log backup of the currently active transaction log as of the point of failure.</span></span>  
  
2.  <span data-ttu-id="ab769-153">不要还原上午 8:00 的</span><span class="sxs-lookup"><span data-stu-id="ab769-153">Do not restore the 8:00 A.M.</span></span> <span data-ttu-id="ab769-154">所需的时间长。</span><span class="sxs-lookup"><span data-stu-id="ab769-154">full database backup.</span></span> <span data-ttu-id="ab769-155">相反，应还原下午 6:00 的</span><span class="sxs-lookup"><span data-stu-id="ab769-155">Instead, restore the more recent 6:00 P.M.</span></span> <span data-ttu-id="ab769-156">这一时间更近的完整数据库备份，然后应用晚上 8:00 的</span><span class="sxs-lookup"><span data-stu-id="ab769-156">full database backup, and then apply the 8:00 P.M.</span></span> <span data-ttu-id="ab769-157">日志备份和结尾日志备份。</span><span class="sxs-lookup"><span data-stu-id="ab769-157">log backup and the tail-log backup.</span></span>  
  
 <span data-ttu-id="ab769-158">**替换选项 2：使用较早的完整数据库备份还原数据库**</span><span class="sxs-lookup"><span data-stu-id="ab769-158">**Alternative 2: Restore the database by using an earlier full database backup**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ab769-159">如果出现问题，使您无法使用下午 6:00 的完整数据库备份，</span><span class="sxs-lookup"><span data-stu-id="ab769-159">This alternative process is useful if a problem prevents you from using the 6:00 P.M.</span></span> <span data-ttu-id="ab769-160">所需的时间长。</span><span class="sxs-lookup"><span data-stu-id="ab769-160">full database backup.</span></span> <span data-ttu-id="ab769-161">此过程比从下午 6:00 的完整数据库备份还原</span><span class="sxs-lookup"><span data-stu-id="ab769-161">This process takes longer than restoring from the 6:00 P.M.</span></span> <span data-ttu-id="ab769-162">所需的时间长。</span><span class="sxs-lookup"><span data-stu-id="ab769-162">full database backup.</span></span>  
  
1.  <span data-ttu-id="ab769-163">失败时创建当前活动事务日志的结尾日志备份。</span><span class="sxs-lookup"><span data-stu-id="ab769-163">Create a tail-log backup of the currently active transaction log as of the point of failure.</span></span>  
  
2.  <span data-ttu-id="ab769-164">还原上午 8:00 的</span><span class="sxs-lookup"><span data-stu-id="ab769-164">Restore the 8:00 A.M.</span></span> <span data-ttu-id="ab769-165">完整数据库备份，然后按顺序还原所有四个事务日志备份。</span><span class="sxs-lookup"><span data-stu-id="ab769-165">full database backup, and then restore all four transaction log backups in sequence.</span></span> <span data-ttu-id="ab769-166">所有完成的事务都将前滚到晚上 9:45。</span><span class="sxs-lookup"><span data-stu-id="ab769-166">This rolls forward all completed transactions up to 9:45 P.M.</span></span>  
  
     <span data-ttu-id="ab769-167">此备选过程指出了冗余安全性，该安全性通过维护一系列完整数据库备份中的事务日志链备份来获得。</span><span class="sxs-lookup"><span data-stu-id="ab769-167">This alternative points out the redundant security offered by maintaining a chain of transaction log backups across a series of full database backups.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ab769-168">某些情况下，您还可以使用事务日志将数据库还原到特定的时间点。</span><span class="sxs-lookup"><span data-stu-id="ab769-168">In some cases, you can also use transaction logs to restore a database to a specific point in time.</span></span> <span data-ttu-id="ab769-169">有关详细信息，请参阅 [将 SQL Server 数据库还原到某个时间点（完整恢复模式）](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)。</span><span class="sxs-lookup"><span data-stu-id="ab769-169">For more information, [Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="ab769-170">相关任务</span><span class="sxs-lookup"><span data-stu-id="ab769-170">Related Tasks</span></span>  
 <span data-ttu-id="ab769-171">**应用事务日志备份**</span><span class="sxs-lookup"><span data-stu-id="ab769-171">**To apply a transaction log backup**</span></span>  
  
-   [<span data-ttu-id="ab769-172">还原事务日志备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ab769-172">Restore a Transaction Log Backup &#40;SQL Server&#41;</span></span>](restore-a-transaction-log-backup-sql-server.md)  
  
 <span data-ttu-id="ab769-173">**还原到恢复点**</span><span class="sxs-lookup"><span data-stu-id="ab769-173">**To restore to your recovery point**</span></span>  
  
-   [<span data-ttu-id="ab769-174">在完整恢复模式下将数据库还原到故障点 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ab769-174">Restore a Database to the Point of Failure Under the Full Recovery Model &#40;Transact-SQL&#41;</span></span>](restore-database-to-point-of-failure-full-recovery.md)  
  
-   [<span data-ttu-id="ab769-175">将 SQL Server 数据库还原到某个时间点（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="ab769-175">Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;</span></span>](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)  
  
-   <span data-ttu-id="ab769-176"><xref:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="ab769-176"><xref:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore%2A> (SMO)</span></span>  
  
-   [<span data-ttu-id="ab769-177">包含标记的事务的相关数据库的恢复</span><span class="sxs-lookup"><span data-stu-id="ab769-177">Recovery of Related  Databases That Contain Marked Transaction</span></span>](recovery-of-related-databases-that-contain-marked-transaction.md)  
  
-   [<span data-ttu-id="ab769-178">恢复到日志序列号 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ab769-178">Recover to a Log Sequence Number &#40;SQL Server&#41;</span></span>](recover-to-a-log-sequence-number-sql-server.md)  
  
 <span data-ttu-id="ab769-179">**使用 WITH NORECOVERY 在还原备份后恢复数据库**</span><span class="sxs-lookup"><span data-stu-id="ab769-179">**To recover a database after restoring backups using WITH NORECOVERY**</span></span>  
  
-   [<span data-ttu-id="ab769-180">恢复数据库但不还原数据 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ab769-180">Recover a Database Without Restoring Data &#40;Transact-SQL&#41;</span></span>](recover-a-database-without-restoring-data-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="ab769-181">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ab769-181">See Also</span></span>  
 [<span data-ttu-id="ab769-182">事务日志 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ab769-182">The Transaction Log &#40;SQL Server&#41;</span></span>](../logs/the-transaction-log-sql-server.md)  
  
  
