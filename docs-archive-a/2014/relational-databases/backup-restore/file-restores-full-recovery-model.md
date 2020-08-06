---
title: 文件还原（完整恢复模式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- file restores [SQL Server]
- full recovery model [SQL Server], performing restores
- restoring files [SQL Server], Transact-SQL restore sequence
- restoring files [SQL Server]
- file restores [SQL Server], full recovery model
- restoring files [SQL Server], full recovery model
- Transact-SQL restore sequence
- file restores [SQL Server], Transact-SQL restore sequence
ms.assetid: d2236a2a-4cf1-4c3f-b542-f73f6096e15c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 488515ec900867f13d33580402e36a3f98747bb2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689455"
---
# <a name="file-restores-full-recovery-model"></a><span data-ttu-id="d3afb-102">文件还原（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="d3afb-102">File Restores (Full Recovery Model)</span></span>
  <span data-ttu-id="d3afb-103">本主题仅与在完整恢复模式或大容量加载恢复模式下包含多个文件或文件组的数据库相关。</span><span class="sxs-lookup"><span data-stu-id="d3afb-103">This topic is relevant only for databases that contain multiple files or filegroups under the full or bulk-load recovery model.</span></span>  
  
 <span data-ttu-id="d3afb-104">文件还原的目标是还原一个或多个损坏的文件，而不是还原整个数据库。</span><span class="sxs-lookup"><span data-stu-id="d3afb-104">In a file restore, the goal is to restore one or more damaged files without restoring the whole database.</span></span> <span data-ttu-id="d3afb-105">文件还原方案由复制、前滚和恢复相应数据的单一还原顺序组成。</span><span class="sxs-lookup"><span data-stu-id="d3afb-105">A file restore scenario consists of a single restore sequence that copies, rolls forward, and recovers the appropriate data</span></span>  
  
 <span data-ttu-id="d3afb-106">如果正在还原的文件组为读/写文件组，则在还原上一次数据备份或差异备份以后必须应用连续的日志备份链。</span><span class="sxs-lookup"><span data-stu-id="d3afb-106">If the filegroup that is being restored is read/write, an unbroken chain of log backups must be applied after the last data or differential backup is restored.</span></span> <span data-ttu-id="d3afb-107">这样才会使文件组记录到日志文件的当前活动日志记录中。</span><span class="sxs-lookup"><span data-stu-id="d3afb-107">This brings the filegroup forward to the log records in the current active log records in the log file.</span></span> <span data-ttu-id="d3afb-108">恢复点通常靠近日志的末端，但并非总是如此。</span><span class="sxs-lookup"><span data-stu-id="d3afb-108">The recovery point is typically near the end of log, but not necessarily.</span></span>  
  
 <span data-ttu-id="d3afb-109">如果正在还原的文件组为只读文件组，则通常不需要应用日志备份，并且会跳过该操作。</span><span class="sxs-lookup"><span data-stu-id="d3afb-109">If the filegroup that is being restored is read-only, usually applying log backups is unnecessary and is skipped.</span></span> <span data-ttu-id="d3afb-110">如果在文件变成只读后进行了备份，则该备份为要还原的最后备份。</span><span class="sxs-lookup"><span data-stu-id="d3afb-110">If the backup was taken after the file became read-only, that is the last backup to restore.</span></span> <span data-ttu-id="d3afb-111">前滚在目标点停止。</span><span class="sxs-lookup"><span data-stu-id="d3afb-111">Roll forward stops at the target point.</span></span>  
  
 <span data-ttu-id="d3afb-112">这些文件还原方案如下：</span><span class="sxs-lookup"><span data-stu-id="d3afb-112">The file-restore scenarios are as follows:</span></span>  
  
-   <span data-ttu-id="d3afb-113">脱机文件还原</span><span class="sxs-lookup"><span data-stu-id="d3afb-113">Offline file restore</span></span>  
  
     <span data-ttu-id="d3afb-114">在“脱机文件还原”  中，还原已损坏的文件或文件组时，数据库处于脱机状态。</span><span class="sxs-lookup"><span data-stu-id="d3afb-114">In an *offline file restore*, the database is offline while damaged files or filegroups are restored.</span></span> <span data-ttu-id="d3afb-115">还原顺序结束时，数据库将联机。</span><span class="sxs-lookup"><span data-stu-id="d3afb-115">At the end of the restore sequence, the database comes online.</span></span>  
  
     <span data-ttu-id="d3afb-116">所有版本的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 都支持脱机文件还原。</span><span class="sxs-lookup"><span data-stu-id="d3afb-116">All editions of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] support offline file restore.</span></span>  
  
-   <span data-ttu-id="d3afb-117">联机文件还原</span><span class="sxs-lookup"><span data-stu-id="d3afb-117">Online file restore</span></span>  
  
     <span data-ttu-id="d3afb-118">在“联机文件还原”  中，如果数据库在还原时处于联机状态，则该数据库在文件还原过程中将保持联机状态。</span><span class="sxs-lookup"><span data-stu-id="d3afb-118">In an *online file restore*, if database is online at restore time, it remains online during the file restore.</span></span> <span data-ttu-id="d3afb-119">不过，各文件组中如果有文件正在被还原，则该文件组在还原操作过程中将处于脱机状态。</span><span class="sxs-lookup"><span data-stu-id="d3afb-119">However, each filegroup in which a file is being restored is offline during the restore operation.</span></span> <span data-ttu-id="d3afb-120">恢复脱机文件组中的所有文件之后，该文件组将自动变为联机状态。</span><span class="sxs-lookup"><span data-stu-id="d3afb-120">After all the files in an offline filegroup are recovered, the filegroup is automatically brought online.</span></span>  
  
     <span data-ttu-id="d3afb-121">有关联机页和文件还原支持的信息，请参阅 [SQL Server 2014 各个版本支持的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="d3afb-121">For information about support for online page and file restore, see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span> <span data-ttu-id="d3afb-122">有关联机还原的详细信息，请参阅[联机还原 (SQL Server)](online-restore-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="d3afb-122">For more information about online restores, see [Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md).</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="d3afb-123">如果希望数据库脱机以进行文件还原，请在开始还原顺序之前执行下列 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options) 语句以使数据库脱机：ALTER DATABASE database_name SET OFFLINE  。</span><span class="sxs-lookup"><span data-stu-id="d3afb-123">If you want the database to be offline for a file restore, take the database offline before you start the restore sequence by executing the following [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options) statement: ALTER DATABASE *database_name* SET OFFLINE.</span></span>  
  
  
  
##  <a name="restoring-damaged-files-from-file-backups"></a><a name="Overview"></a> <span data-ttu-id="d3afb-124">从文件备份还原损坏的文件</span><span class="sxs-lookup"><span data-stu-id="d3afb-124">Restoring Damaged Files from File Backups</span></span>  
  
1.  <span data-ttu-id="d3afb-125">在还原一个或多个损坏的文件前，请尝试创建 [结尾日志备份](tail-log-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="d3afb-125">Before restoring one or more damaged files, attempt to create a [tail-log backup](tail-log-backups-sql-server.md).</span></span>  
  
     <span data-ttu-id="d3afb-126">如果该日志已损坏，则不能创建结尾日志备份，您必须还原整个数据库。</span><span class="sxs-lookup"><span data-stu-id="d3afb-126">If the log has been damaged, a tail-log backup cannot be created, and you must restore the whole database.</span></span>  
  
     <span data-ttu-id="d3afb-127">有关如何备份事务日志的信息，请参阅[事务日志备份 (SQL Server)](transaction-log-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="d3afb-127">For information about how to back up a transaction log, see [Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="d3afb-128">对于脱机文件还原，在文件还原之前必须始终先进行一次结尾日志备份。</span><span class="sxs-lookup"><span data-stu-id="d3afb-128">For an offline file restore, you must always take a tail-log backup before the file restore.</span></span> <span data-ttu-id="d3afb-129">对于联机文件还原，在文件还原之后必须始终先进行一次日志备份。</span><span class="sxs-lookup"><span data-stu-id="d3afb-129">For an online file restore, you must always take the log backup after the file restore.</span></span> <span data-ttu-id="d3afb-130">此日志备份对于将文件恢复到与数据库的其余部分一致的状态至关重要。</span><span class="sxs-lookup"><span data-stu-id="d3afb-130">This log backup is necessary to allow for the file to be recovered to a state consistent with the rest of the database.</span></span>  
  
2.  <span data-ttu-id="d3afb-131">从每个损坏的文件的最新文件备份还原相应文件。</span><span class="sxs-lookup"><span data-stu-id="d3afb-131">Restore each damaged file from the most recent file backup of that file.</span></span>  
  
3.  <span data-ttu-id="d3afb-132">针对每个还原的文件，还原最近的差异文件备份（如果有）。</span><span class="sxs-lookup"><span data-stu-id="d3afb-132">Restore the most recent differential file backup, if any, for each restored file.</span></span>  
  
4.  <span data-ttu-id="d3afb-133">按顺序还原事务日志备份，从覆盖最早还原文件的备份开始，到在步骤 1 中创建的结尾日志备份结束。</span><span class="sxs-lookup"><span data-stu-id="d3afb-133">Restore transaction log backups in sequence, starting with the backup that covers the oldest of the restored files and ending with the tail-log backup created in step 1.</span></span>  
  
     <span data-ttu-id="d3afb-134">必须还原在文件备份后创建的事务日志备份才能使数据库处于一致状态。</span><span class="sxs-lookup"><span data-stu-id="d3afb-134">You must restore the transaction log backups that were created after the file backups to bring the database to a consistent state.</span></span> <span data-ttu-id="d3afb-135">事务日志备份可以快速前滚，因为仅应用了对还原文件所做的更改。</span><span class="sxs-lookup"><span data-stu-id="d3afb-135">The transaction log backups can be rolled forward quickly, because only the changes that apply to the restored files are applied.</span></span> <span data-ttu-id="d3afb-136">与还原整个数据库相比，更好的方式是还原单个文件，因为并不会复制并随后前滚未损坏的文件。</span><span class="sxs-lookup"><span data-stu-id="d3afb-136">Restoring individual files can be better than restoring the whole database, because undamaged files are not copied and then rolled forward.</span></span> <span data-ttu-id="d3afb-137">但是，仍需要读取整个日志备份链。</span><span class="sxs-lookup"><span data-stu-id="d3afb-137">However, the whole chain of log backups still has to be read.</span></span>  
  
5.  <span data-ttu-id="d3afb-138">恢复数据库。</span><span class="sxs-lookup"><span data-stu-id="d3afb-138">Recover the database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d3afb-139">文件备份可用于将数据库还原到早期时间点。</span><span class="sxs-lookup"><span data-stu-id="d3afb-139">File backups can be used to restore the database to an earlier point in time.</span></span> <span data-ttu-id="d3afb-140">必须还原一组完整的文件备份，然后依次将事务日志备份还原到目标点（目标点是结束最近还原的文件备份后的时间点），才能执行此操作。</span><span class="sxs-lookup"><span data-stu-id="d3afb-140">To do this, you must restore a complete set of file backups, and then restore transaction log backups in sequence to reach a target point that is after the end of the most recent restored file backup.</span></span> <span data-ttu-id="d3afb-141">有关时点恢复的详细信息，请参阅[将 SQL Server 数据库还原到某个时间点（完整恢复模式）](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)。</span><span class="sxs-lookup"><span data-stu-id="d3afb-141">For more information about point-in-time recovery, see [Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md).</span></span>  
  
## <a name="transact-sql-restore-sequence-for-an-offline-file-restore-full-recovery-model"></a><span data-ttu-id="d3afb-142">脱机文件还原的 Transact-SQL 还原顺序（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="d3afb-142">Transact-SQL Restore Sequence for an Offline File Restore (Full Recovery Model)</span></span>  
 <span data-ttu-id="d3afb-143">文件还原方案由复制、前滚和恢复相应数据的单一还原顺序组成。</span><span class="sxs-lookup"><span data-stu-id="d3afb-143">A file restore scenario consists of a single restore sequence that copies, rolls forward, and recovers the appropriate data.</span></span>  
  
 <span data-ttu-id="d3afb-144">本节说明用于文件还原序列的基本 [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 选项。</span><span class="sxs-lookup"><span data-stu-id="d3afb-144">This section shows the essential [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) options for a file-restore sequence.</span></span> <span data-ttu-id="d3afb-145">将省略与此目的不相关的语法和详细信息。</span><span class="sxs-lookup"><span data-stu-id="d3afb-145">Syntax and details that are not relevant to this purpose are omitted.</span></span>  
  
 <span data-ttu-id="d3afb-146">以下示例说明了如何使用 WITH NORECOVERY 脱机还原两个辅助文件 `A` 和 `B`。</span><span class="sxs-lookup"><span data-stu-id="d3afb-146">The following sample restore sequence shows an offline restore of two secondary files, `A` and `B`, using WITH NORECOVERY.</span></span> <span data-ttu-id="d3afb-147">随后，对两个日志备份应用 NORECOVERY，然后是结尾日志备份（用 WITH RECOVERY 还原）。</span><span class="sxs-lookup"><span data-stu-id="d3afb-147">Next, two log backups are applied with NORECOVERY, followed with the tail-log backup, and this is restored using WITH RECOVERY.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d3afb-148">下面的示例还原序列通过使文件脱机开始，然后创建结尾日志备份，</span><span class="sxs-lookup"><span data-stu-id="d3afb-148">The following sample restore sequence starts by taking the file offline and then creates a tail-log backup.</span></span>  
  
```  
--Take the file offline.  
ALTER DATABASE database_name MODIFY FILE SET OFFLINE;  
-- Back up the currently active transaction log.  
BACKUP LOG database_name  
   TO <tail_log_backup>  
   WITH NORECOVERY;  
GO   
-- Restore the files.  
RESTORE DATABASE database_name FILE=name   
   FROM <file_backup_of_file_A>   
   WITH NORECOVERY;  
RESTORE DATABASE database_name FILE=<name> ......  
   FROM <file_backup_of_file_B>   
   WITH NORECOVERY;  
-- Restore the log backups.  
RESTORE LOG database_name FROM <log_backup>   
   WITH NORECOVERY;  
RESTORE LOG database_name FROM <log_backup>   
   WITH NORECOVERY;  
RESTORE LOG database_name FROM <tail_log_backup>   
   WITH RECOVERY;  
```  
  
## <a name="examples"></a><span data-ttu-id="d3afb-149">示例</span><span class="sxs-lookup"><span data-stu-id="d3afb-149">Examples</span></span>  
  
-   [<span data-ttu-id="d3afb-150">示例：读/写文件的联机还原（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="d3afb-150">Example: Online Restore of a Read-Write File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
-   [<span data-ttu-id="d3afb-151">示例：只读文件的联机还原（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="d3afb-151">Example: Online Restore of a Read-Only File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
-   [<span data-ttu-id="d3afb-152">示例：主文件组和一个其他文件组的脱机还原（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="d3afb-152">Example: Offline Restore of Primary and One Other Filegroup &#40;Full Recovery Model&#41;</span></span>](example-offline-restore-of-primary-and-one-other-filegroup-full-recovery-model.md)  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="d3afb-153">相关任务</span><span class="sxs-lookup"><span data-stu-id="d3afb-153">Related Tasks</span></span>  
 <span data-ttu-id="d3afb-154">**还原文件和文件组**</span><span class="sxs-lookup"><span data-stu-id="d3afb-154">**To restore files and filegroups**</span></span>  
  
-   [<span data-ttu-id="d3afb-155">将文件还原到新位置 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="d3afb-155">Restore Files to a New Location &#40;SQL Server&#41;</span></span>](restore-files-to-a-new-location-sql-server.md)  
  
-   [<span data-ttu-id="d3afb-156">还原文件和文件组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="d3afb-156">Restore Files and Filegroups &#40;SQL Server&#41;</span></span>](restore-files-and-filegroups-sql-server.md)  
  
-   <span data-ttu-id="d3afb-157"><xref:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="d3afb-157"><xref:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore%2A> (SMO)</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="d3afb-158">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d3afb-158">See Also</span></span>  
 <span data-ttu-id="d3afb-159">[备份和还原：互操作性和共存 &#40;SQL Server&#41;](backup-and-restore-interoperability-and-coexistence-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d3afb-159">[Backup and Restore: Interoperability and Coexistence &#40;SQL Server&#41;](backup-and-restore-interoperability-and-coexistence-sql-server.md) </span></span>  
 <span data-ttu-id="d3afb-160">[差异备份 (SQL Server)](differential-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d3afb-160">[Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md) </span></span>  
 <span data-ttu-id="d3afb-161">[完整文件备份 (SQL Server)](full-file-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d3afb-161">[Full File Backups &#40;SQL Server&#41;](full-file-backups-sql-server.md) </span></span>  
 <span data-ttu-id="d3afb-162">[备份概述 (SQL Server)](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d3afb-162">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 <span data-ttu-id="d3afb-163">[还原和恢复概述 (SQL Server)](restore-and-recovery-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d3afb-163">[Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span></span>  
 <span data-ttu-id="d3afb-164">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d3afb-164">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="d3afb-165">[完整数据库还原（简单恢复模式）](complete-database-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="d3afb-165">[Complete Database Restores &#40;Simple Recovery Model&#41;](complete-database-restores-simple-recovery-model.md) </span></span>  
 [<span data-ttu-id="d3afb-166">段落还原 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="d3afb-166">Piecemeal Restores &#40;SQL Server&#41;</span></span>](piecemeal-restores-sql-server.md)  
  
  
