---
title: 完整数据库还原（完整恢复模式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- complete database restores
- database restores [SQL Server], complete database
- restoring databases [SQL Server], complete database
- restoring [SQL Server], database
- full recovery model [SQL Server], performing restores
- log backups [SQL Server[
ms.assetid: 5b4c471c-b972-498e-aba9-92cf7a0ea881
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ea6ec9f196acd0a64a0b785024bd6426cd6a5381
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591423"
---
# <a name="complete-database-restores-full-recovery-model"></a><span data-ttu-id="1e726-102">完整数据库还原（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="1e726-102">Complete Database Restores (Full Recovery Model)</span></span>
  <span data-ttu-id="1e726-103">数据库完整还原的目的是还原整个数据库。</span><span class="sxs-lookup"><span data-stu-id="1e726-103">In a complete database restore, the goal is to restore the whole database.</span></span> <span data-ttu-id="1e726-104">整个数据库在还原期间处于脱机状态。</span><span class="sxs-lookup"><span data-stu-id="1e726-104">The whole database is offline for the duration of the restore.</span></span> <span data-ttu-id="1e726-105">在数据库的任何部分变为联机之前，必须将所有数据恢复到同一点，即数据库的所有部分都处于同一时间点并且不存在未提交的事务。</span><span class="sxs-lookup"><span data-stu-id="1e726-105">Before any part of the database can come online, all data is recovered to a consistent point in which all parts of the database are at the same point in time and no uncommitted transactions exist.</span></span>  
  
 <span data-ttu-id="1e726-106">在完整恢复模式下，还原数据备份之后，必须还原所有后续的事务日志备份，然后再恢复数据库。</span><span class="sxs-lookup"><span data-stu-id="1e726-106">Under the full recovery model, after you restore your data backup or backups, you must restore all subsequent transaction log backups and then recover the database.</span></span> <span data-ttu-id="1e726-107">您可以将数据库还原到这些日志备份之一的特定 *恢复点* 。</span><span class="sxs-lookup"><span data-stu-id="1e726-107">You can restore a database to a specific *recovery point* within one of these log backups.</span></span> <span data-ttu-id="1e726-108">恢复点可以是特定的日期和时间、标记的事务或日志序列号 (LSN)。</span><span class="sxs-lookup"><span data-stu-id="1e726-108">The recovery point can be a specific date and time, a marked transaction, or a log sequence number (LSN).</span></span>  
  
 <span data-ttu-id="1e726-109">还原数据库时，特别是在完整恢复模式或大容量日志恢复模式下，您应使用一个还原顺序。</span><span class="sxs-lookup"><span data-stu-id="1e726-109">When restoring a database, particularly under the full recovery model or bulk-logged recovery model, you should use a single restore sequence.</span></span> <span data-ttu-id="1e726-110">*还原顺序* 由通过一个或多个还原阶段来移动数据的一个或多个还原操作组成。</span><span class="sxs-lookup"><span data-stu-id="1e726-110">A *restore sequence* consists of one or more restore operations that move data through one or more of the phases of restore.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1e726-111">建议您不要附加或还原来自未知或不可信源的数据库。</span><span class="sxs-lookup"><span data-stu-id="1e726-111">We recommend that you do not attach or restore databases from unknown or untrusted sources.</span></span> <span data-ttu-id="1e726-112">这些数据库可能包含执行非预期 [!INCLUDE[tsql](../../includes/tsql-md.md)] 代码的恶意代码，或通过修改架构或物理数据库结构导致错误。</span><span class="sxs-lookup"><span data-stu-id="1e726-112">These databases could contain malicious code that might execute unintended [!INCLUDE[tsql](../../includes/tsql-md.md)] code or cause errors by modifying the schema or the physical database structure.</span></span> <span data-ttu-id="1e726-113">使用来自未知源或不可信源的数据库前，请在非生产服务器上针对数据库运行 [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) ，然后检查数据库中的代码，例如存储过程或其他用户定义代码。</span><span class="sxs-lookup"><span data-stu-id="1e726-113">Before you use a database from an unknown or untrusted source, run [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) on the database on a nonproduction server and also examine the code, such as stored procedures or other user-defined code, in the database.</span></span>  
  
 <span data-ttu-id="1e726-114">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="1e726-114">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="1e726-115">将数据库还原到故障点</span><span class="sxs-lookup"><span data-stu-id="1e726-115">Restoring a Database to the Point of Failure</span></span>](#PointOfFailure)  
  
-   [<span data-ttu-id="1e726-116">将数据库还原到日志备份中的某个点</span><span class="sxs-lookup"><span data-stu-id="1e726-116">Restoring a Database to a Point Within a Log Backup</span></span>](#PointWithinBackup)  
  
-   [<span data-ttu-id="1e726-117">相关任务</span><span class="sxs-lookup"><span data-stu-id="1e726-117">Related Tasks</span></span>](#RelatedTasks)  
  
> [!NOTE]  
>  <span data-ttu-id="1e726-118">有关支持从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的早期版本进行备份的信息，请参阅 [RESTORE (Transact-SQL)](/sql/t-sql/statements/restore-statements-transact-sql)中的“兼容性支持”部分。</span><span class="sxs-lookup"><span data-stu-id="1e726-118">For information about support for backups from earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see the "Compatibility Support" section of [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>  
  
##  <a name="restoring-a-database-to-the-point-of-failure"></a><a name="PointOfFailure"></a> <span data-ttu-id="1e726-119">将数据库还原到故障点</span><span class="sxs-lookup"><span data-stu-id="1e726-119">Restoring a Database to the Point of Failure</span></span>  
 <span data-ttu-id="1e726-120">通常，将数据库恢复到故障点分为下列基本步骤：</span><span class="sxs-lookup"><span data-stu-id="1e726-120">Typically, recovering a database to the point of failure involves the following basic steps:</span></span>  
  
1.  <span data-ttu-id="1e726-121">备份活动事务日志（称为日志尾部）。</span><span class="sxs-lookup"><span data-stu-id="1e726-121">Back up the active transaction log (known as the tail of the log).</span></span> <span data-ttu-id="1e726-122">此操作将创建结尾日志备份。</span><span class="sxs-lookup"><span data-stu-id="1e726-122">This creates a tail-log backup.</span></span> <span data-ttu-id="1e726-123">如果活动事务日志不可用，则该日志部分的所有事务都将丢失。</span><span class="sxs-lookup"><span data-stu-id="1e726-123">If the active transaction log is unavailable, all transactions in that part of the log are lost.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="1e726-124">在大容量日志恢复模式下，备份任何包含大容量日志操作的日志都需要访问数据库中的所有数据文件。</span><span class="sxs-lookup"><span data-stu-id="1e726-124">Under the bulk-logged recovery model, backing up any log that contains bulk-logged operations requires access to all data files in the database.</span></span> <span data-ttu-id="1e726-125">如果无法访问该数据文件，则不能备份事务日志。</span><span class="sxs-lookup"><span data-stu-id="1e726-125">If the data files cannot be accessed, the transaction log cannot be backed up.</span></span> <span data-ttu-id="1e726-126">在这种情况下，您必须手动重做自最近备份日志以来所做的所有更改。</span><span class="sxs-lookup"><span data-stu-id="1e726-126">In that case, you have to manually redo all changes that were made since the most recent log backup.</span></span>  
  
     <span data-ttu-id="1e726-127">有关详细信息，请参阅[结尾日志备份 (SQL Server)](tail-log-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="1e726-127">For more information, see [Tail-Log Backups &#40;SQL Server&#41;](tail-log-backups-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="1e726-128">还原最新完整数据库备份而不恢复数据库 (RESTORE DATABASE *database_name* FROM *backup_device* WITH NORECOVERY)。</span><span class="sxs-lookup"><span data-stu-id="1e726-128">Restore the most recent full database backup without recovering the database (RESTORE DATABASE *database_name* FROM *backup_device* WITH NORECOVERY).</span></span>  
  
3.  <span data-ttu-id="1e726-129">如果存在差异备份，则还原最新的差异备份而不恢复数据库 (RESTORE DATABASE *database_name* FROM *differential_backup_device* WITH NORECOVERY)。</span><span class="sxs-lookup"><span data-stu-id="1e726-129">If differential backups exist, restore the most recent one without recovering the database (RESTORE DATABASE *database_name* FROM *differential_backup_device* WITH NORECOVERY).</span></span>  
  
     <span data-ttu-id="1e726-130">还原最新差异备份可减少必须还原的日志备份数。</span><span class="sxs-lookup"><span data-stu-id="1e726-130">Restoring the most recent differential backup reduces the number of log backups that must be restored.</span></span>  
  
4.  <span data-ttu-id="1e726-131">从还原备份后创建的第一个事务日志备份开始，使用 NORECOVERY 依次还原日志。</span><span class="sxs-lookup"><span data-stu-id="1e726-131">Starting with the first transaction log backup that was created after the backup you just restored, restore the logs in sequence with NORECOVERY.</span></span>  
  
5.  <span data-ttu-id="1e726-132">恢复数据库 (RESTORE DATABASE *database_name* WITH RECOVERY)。</span><span class="sxs-lookup"><span data-stu-id="1e726-132">Recover the database (RESTORE DATABASE *database_name* WITH RECOVERY).</span></span> <span data-ttu-id="1e726-133">此步骤也可以与还原上一次日志备份结合使用。</span><span class="sxs-lookup"><span data-stu-id="1e726-133">Alternatively, this step can be combined with restoring the last log backup.</span></span>  
  
 <span data-ttu-id="1e726-134">下图说明此还原顺序。</span><span class="sxs-lookup"><span data-stu-id="1e726-134">The following illustration shows this restore sequence.</span></span> <span data-ttu-id="1e726-135">故障发生后 (1)，将创建结尾日志备份 (2)。</span><span class="sxs-lookup"><span data-stu-id="1e726-135">After a failure occurs (1), a tail-log backup is created (2).</span></span> <span data-ttu-id="1e726-136">接着，将数据库还原到该故障点。</span><span class="sxs-lookup"><span data-stu-id="1e726-136">Next, the database is restored to the point of the failure.</span></span> <span data-ttu-id="1e726-137">这涉及到还原数据库备份、后续差异备份以及在差异备份后执行的每个日志备份，包括结尾日志备份。</span><span class="sxs-lookup"><span data-stu-id="1e726-137">This involves restoring a database backup, a subsequent differential backup, and every log backup taken after the differential backup, including the tail-log backup.</span></span>  
  
 <span data-ttu-id="1e726-138">![将数据库完全还原到故障的时间点](../../database-engine/media/bnrr-rmfull1-db-failure-pt.gif "将数据库完全还原到故障的时间点")</span><span class="sxs-lookup"><span data-stu-id="1e726-138">![Complete database restore to the time of a failure](../../database-engine/media/bnrr-rmfull1-db-failure-pt.gif "Complete database restore to the time of a failure")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1e726-139">计划将数据库备份还原到其它服务器实例时，请参阅 [通过备份和还原来复制数据库](../databases/copy-databases-with-backup-and-restore.md)。</span><span class="sxs-lookup"><span data-stu-id="1e726-139">When you restore a database backup onto a different server instance, see [Copy Databases with Backup and Restore](../databases/copy-databases-with-backup-and-restore.md).</span></span>  
  
###  <a name="basic-transact-sql-restore-syntax"></a><a name="TsqlSyntax"></a> <span data-ttu-id="1e726-140">基本 TRANSACT-SQL RESTORE 语法</span><span class="sxs-lookup"><span data-stu-id="1e726-140">Basic Transact-SQL RESTORE Syntax</span></span>  
 <span data-ttu-id="1e726-141">上图中还原顺序的基本 [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] 语法如下：</span><span class="sxs-lookup"><span data-stu-id="1e726-141">The basic [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] syntax for the restore sequence in the preceding illustration is as follows:</span></span>  
  
1.  <span data-ttu-id="1e726-142">RESTORE DATABASE *database* FROM *full database backup* WITH NORECOVERY;</span><span class="sxs-lookup"><span data-stu-id="1e726-142">RESTORE DATABASE *database* FROM *full database backup* WITH NORECOVERY;</span></span>  
  
2.  <span data-ttu-id="1e726-143">RESTORE DATABASE *database* FROM *full_differential_backup* WITH NORECOVERY;</span><span class="sxs-lookup"><span data-stu-id="1e726-143">RESTORE DATABASE *database* FROM *full_differential_backup* WITH NORECOVERY;</span></span>  
  
3.  <span data-ttu-id="1e726-144">RESTORE LOG *database* FROM *log_backup* WITH NORECOVERY;</span><span class="sxs-lookup"><span data-stu-id="1e726-144">RESTORE LOG *database* FROM *log_backup* WITH NORECOVERY;</span></span>  
  
     <span data-ttu-id="1e726-145">对于其他每个日志备份，重复此还原日志步骤。</span><span class="sxs-lookup"><span data-stu-id="1e726-145">Repeat this restore-log step for each additional log backup.</span></span>  
  
4.  <span data-ttu-id="1e726-146">RESTORE DATABASE *database* WITH RECOVERY;</span><span class="sxs-lookup"><span data-stu-id="1e726-146">RESTORE DATABASE *database* WITH RECOVERY;</span></span>  
  
###  <a name="example-recovering-to-the-point-of-failure-transact-sql"></a><a name="ExampleToPoFTsql"></a> <span data-ttu-id="1e726-147">示例：恢复到故障点 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="1e726-147">Example: Recovering to the Point of Failure (Transact-SQL)</span></span>  
 <span data-ttu-id="1e726-148">以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 示例显示了将数据库还原到故障点的还原顺序中的基本选项。</span><span class="sxs-lookup"><span data-stu-id="1e726-148">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] example shows the essential options in a restore sequence that restores the database to the point of failure.</span></span> <span data-ttu-id="1e726-149">此示例将创建数据库的结尾日志备份。</span><span class="sxs-lookup"><span data-stu-id="1e726-149">The example creates a tail-log backup of the database.</span></span> <span data-ttu-id="1e726-150">接下来，此示例将还原完整数据库备份和日志备份，然后还原结尾日志备份。</span><span class="sxs-lookup"><span data-stu-id="1e726-150">Next, the example restores a full database backup and log backup and then restores the tail-log backup.</span></span> <span data-ttu-id="1e726-151">此示例将在最后的单独步骤中恢复数据库。</span><span class="sxs-lookup"><span data-stu-id="1e726-151">The example recovers the database in a separate, final step.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1e726-152">此示例使用在 [完整数据库备份 (SQL Server)](full-database-backups-sql-server.md)中的“兼容性支持”部分。</span><span class="sxs-lookup"><span data-stu-id="1e726-152">This example uses a database backup and log backup that is created in the "Using Database Backups Under the Full Recovery Model" section in [Full Database Backups &#40;SQL Server&#41;](full-database-backups-sql-server.md).</span></span> <span data-ttu-id="1e726-153">在备份数据库之前， [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 示例数据库设置为使用完整恢复模式。</span><span class="sxs-lookup"><span data-stu-id="1e726-153">Before the database backup, the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database was set to use the full recovery model.</span></span>  
  
```  
USE master;  
--Create tail-log backup.  
BACKUP LOG AdventureWorks2012   
TO DISK = 'Z:\SQLServerBackups\AdventureWorksFullRM.bak'    
   WITH NORECOVERY;   
GO  
--Restore the full database backup (from backup set 1).  
RESTORE DATABASE AdventureWorks2012   
  FROM DISK = 'Z:\SQLServerBackups\AdventureWorksFullRM.bak'   
  WITH FILE=1,   
    NORECOVERY;  
  
--Restore the regular log backup (from backup set 2).  
RESTORE LOG AdventureWorks2012   
  FROM DISK = 'Z:\SQLServerBackups\AdventureWorksFullRM.bak'   
  WITH FILE=2,   
    NORECOVERY;  
  
--Restore the tail-log backup (from backup set 3).  
RESTORE LOG AdventureWorks2012   
  FROM DISK = 'Z:\SQLServerBackups\AdventureWorksFullRM.bak'  
  WITH FILE=3,   
    NORECOVERY;  
GO  
--recover the database:  
RESTORE DATABASE AdventureWorks2012 WITH RECOVERY;  
GO  
```  
  
##  <a name="restoring-a-database-to-a-point-within-a-log-backup"></a><a name="PointWithinBackup"></a> <span data-ttu-id="1e726-154">将数据库还原到日志备份中的某个时间点</span><span class="sxs-lookup"><span data-stu-id="1e726-154">Restoring a Database to a Point Within a Log Backup</span></span>  
 <span data-ttu-id="1e726-155">在完整恢复模式下，完整的数据库还原通常可恢复到日志备份中的某个时间点、标记的事务或 LSN。</span><span class="sxs-lookup"><span data-stu-id="1e726-155">Under the full recovery model, a complete database restore can usually be recovered to a point of time, a marked transaction, or an LSN within a log backup.</span></span> <span data-ttu-id="1e726-156">但是，在大容量日志恢复模式下，如果日志备份包含大容量更改，则不能进行时点恢复。</span><span class="sxs-lookup"><span data-stu-id="1e726-156">However, under the bulk-logged recovery model, if the log backup contains bulk-logged changes, point-in-time recovery is not possible.</span></span>  
  
### <a name="sample-point-in-time-restore-scenarios"></a><span data-ttu-id="1e726-157">时点还原方案示例</span><span class="sxs-lookup"><span data-stu-id="1e726-157">Sample Point-in-Time Restore Scenarios</span></span>  
 <span data-ttu-id="1e726-158">下例假定针对一个关键任务型数据库系统，每天午夜创建一个完整数据库备份；从星期一到星期六，每小时创建一个差异数据库备份；全天每 10 分钟创建一个事务日志备份。</span><span class="sxs-lookup"><span data-stu-id="1e726-158">The following example assumes a mission-critical database system for which a full database backup is created daily at midnight, a differential database backup is created on the hour, Monday through Saturday, and transaction log backups are created every 10 minutes throughout the day.</span></span> <span data-ttu-id="1e726-159">若要将数据库还原到星期三凌晨 5:19 的状态，</span><span class="sxs-lookup"><span data-stu-id="1e726-159">To restore the database to the state is was in at 5:19 A.M.</span></span> <span data-ttu-id="1e726-160">请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="1e726-160">Wednesday, do the following:</span></span>  
  
1.  <span data-ttu-id="1e726-161">还原星期二午夜创建的完整数据库备份。</span><span class="sxs-lookup"><span data-stu-id="1e726-161">Restore the full database backup that was created Tuesday at midnight.</span></span>  
  
2.  <span data-ttu-id="1e726-162">还原星期四凌晨 5:00 创建的差异数据库</span><span class="sxs-lookup"><span data-stu-id="1e726-162">Restore the differential database backup that was created at 5:00 A.M.</span></span> <span data-ttu-id="1e726-163">备份。</span><span class="sxs-lookup"><span data-stu-id="1e726-163">on Wednesday.</span></span>  
  
3.  <span data-ttu-id="1e726-164">应用星期四凌晨 5:10创建的事务日志</span><span class="sxs-lookup"><span data-stu-id="1e726-164">Apply the transaction log backup that was created at 5:10 A.M.</span></span> <span data-ttu-id="1e726-165">备份。</span><span class="sxs-lookup"><span data-stu-id="1e726-165">on Wednesday.</span></span>  
  
4.  <span data-ttu-id="1e726-166">应用星期三凌晨 5:20 创建的事务日志</span><span class="sxs-lookup"><span data-stu-id="1e726-166">Apply the transaction log backup that was created 5:20 A.M.</span></span> <span data-ttu-id="1e726-167">备份，指定恢复进程仅应用到凌晨 5:19 之前发生的事务。</span><span class="sxs-lookup"><span data-stu-id="1e726-167">on Wednesday, specifying that the recovery process applies only to transactions that occurred before 5:19 A.M.</span></span>  
  
 <span data-ttu-id="1e726-168">或者，如果需要将数据库还原到它在星期四凌晨 3:04 的状态，</span><span class="sxs-lookup"><span data-stu-id="1e726-168">Alternatively, if the database needs to be restored to its state at 3:04 A.M.</span></span> <span data-ttu-id="1e726-169">而在星期四凌晨 3:00 创建的差异数据库备份已不可用，</span><span class="sxs-lookup"><span data-stu-id="1e726-169">Thursday, but the differential database backup that was created at 3:00 A.M.</span></span> <span data-ttu-id="1e726-170">则执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="1e726-170">Thursday is unavailable, do the following:</span></span>  
  
1.  <span data-ttu-id="1e726-171">还原在星期三午夜创建的数据库备份。</span><span class="sxs-lookup"><span data-stu-id="1e726-171">Restore the database backup that was created Wednesday at midnight.</span></span>  
  
2.  <span data-ttu-id="1e726-172">还原星期四凌晨 2:00 创建的差异数据库</span><span class="sxs-lookup"><span data-stu-id="1e726-172">Restore the differential database backup that was created at 2:00 A.M.</span></span> <span data-ttu-id="1e726-173">备份。</span><span class="sxs-lookup"><span data-stu-id="1e726-173">on Thursday.</span></span>  
  
3.  <span data-ttu-id="1e726-174">应用从星期四凌晨 2:10 到 3:00 创建的所有事务</span><span class="sxs-lookup"><span data-stu-id="1e726-174">Apply all the transaction log backups created from 2:10 A.M.</span></span> <span data-ttu-id="1e726-175">日志</span><span class="sxs-lookup"><span data-stu-id="1e726-175">to 3:00 A.M.</span></span> <span data-ttu-id="1e726-176">备份。</span><span class="sxs-lookup"><span data-stu-id="1e726-176">on Thursday.</span></span>  
  
4.  <span data-ttu-id="1e726-177">应用星期四凌晨 3:10 创建的事务日志</span><span class="sxs-lookup"><span data-stu-id="1e726-177">Apply the transaction log backup that was created at 3:10 A.M.</span></span> <span data-ttu-id="1e726-178">备份，停止凌晨 3:04 的恢复进程。</span><span class="sxs-lookup"><span data-stu-id="1e726-178">on Thursday, stopping the recovery process at 3:04 A.M.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1e726-179">有关时间点存储的示例，请参阅 [将 SQL Server 数据库还原到某个时间点（完整恢复模式）](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)中的“兼容性支持”部分。</span><span class="sxs-lookup"><span data-stu-id="1e726-179">For an example of a point-in-time restore, see [Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="1e726-180">相关任务</span><span class="sxs-lookup"><span data-stu-id="1e726-180">Related Tasks</span></span>  
 <span data-ttu-id="1e726-181">**还原完整数据库备份**</span><span class="sxs-lookup"><span data-stu-id="1e726-181">**To restore a full database backup**</span></span>  
  
-   [<span data-ttu-id="1e726-182">还原数据库备份 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="1e726-182">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-backup-using-ssms.md)  
  
-   [<span data-ttu-id="1e726-183">将数据库还原到新位置 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="1e726-183">Restore a Database to a New Location &#40;SQL Server&#41;</span></span>](restore-a-database-to-a-new-location-sql-server.md)  
  
 <span data-ttu-id="1e726-184">**还原差异数据库备份**</span><span class="sxs-lookup"><span data-stu-id="1e726-184">**To restore a differential database backup**</span></span>  
  
-   [<span data-ttu-id="1e726-185">还原差异数据库备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="1e726-185">Restore a Differential Database Backup &#40;SQL Server&#41;</span></span>](restore-a-differential-database-backup-sql-server.md)  
  
 <span data-ttu-id="1e726-186">**还原事务日志备份**</span><span class="sxs-lookup"><span data-stu-id="1e726-186">**To restore a transaction log backup**</span></span>  
  
-   [<span data-ttu-id="1e726-187">还原事务日志备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="1e726-187">Restore a Transaction Log Backup &#40;SQL Server&#41;</span></span>](restore-a-transaction-log-backup-sql-server.md)  
  
 <span data-ttu-id="1e726-188">**使用 SQL Server 管理对象 (SMO) 还原备份**</span><span class="sxs-lookup"><span data-stu-id="1e726-188">**To restore a backup by using SQL Server Management Objects (SMO)**</span></span>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore%2A>  
  
 <span data-ttu-id="1e726-189">**将数据库还原到日志备份中的某个时间点**</span><span class="sxs-lookup"><span data-stu-id="1e726-189">**To restore a database to a point within a log backup**</span></span>  
  
-   [<span data-ttu-id="1e726-190">将 SQL Server 数据库还原到某个时间点（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="1e726-190">Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;</span></span>](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)  
  
-   [<span data-ttu-id="1e726-191">包含标记的事务的相关数据库的恢复</span><span class="sxs-lookup"><span data-stu-id="1e726-191">Recovery of Related  Databases That Contain Marked Transaction</span></span>](recovery-of-related-databases-that-contain-marked-transaction.md)  
  
-   [<span data-ttu-id="1e726-192">恢复到日志序列号 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="1e726-192">Recover to a Log Sequence Number &#40;SQL Server&#41;</span></span>](recover-to-a-log-sequence-number-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="1e726-193">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1e726-193">See Also</span></span>  
 <span data-ttu-id="1e726-194">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1e726-194">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="1e726-195">[BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1e726-195">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="1e726-196">[应用事务日志备份 (SQL Server)](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1e726-196">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 <span data-ttu-id="1e726-197">[sp_addumpdevice (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1e726-197">[sp_addumpdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span></span>  
 <span data-ttu-id="1e726-198">[完整数据库备份 (SQL Server)](full-database-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1e726-198">[Full Database Backups &#40;SQL Server&#41;](full-database-backups-sql-server.md) </span></span>  
 <span data-ttu-id="1e726-199">[差异备份 (SQL Server)](differential-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1e726-199">[Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md) </span></span>  
 <span data-ttu-id="1e726-200">[备份概述 (SQL Server)](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1e726-200">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 [<span data-ttu-id="1e726-201">还原和恢复概述 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="1e726-201">Restore and Recovery Overview &#40;SQL Server&#41;</span></span>](restore-and-recovery-overview-sql-server.md)  
  
  
