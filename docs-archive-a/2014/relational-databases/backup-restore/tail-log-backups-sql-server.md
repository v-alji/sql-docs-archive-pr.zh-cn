---
title: 结尾日志备份 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backing up [SQL Server], tail of log
- transaction log backups [SQL Server], tail-log backups
- NO_TRUNCATE clause
- backups [SQL Server], log backups
- tail-log backups
- backups [SQL Server], tail-log backups
ms.assetid: 313ddaf6-ec54-4a81-a104-7ffa9533ca58
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: cd7c505701a4edb1f66ca516d06179b2eb1a222d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578263"
---
# <a name="tail-log-backups-sql-server"></a><span data-ttu-id="e8d70-102">结尾日志备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e8d70-102">Tail-Log Backups (SQL Server)</span></span>
  <span data-ttu-id="e8d70-103">本主题仅与备份和还原使用完整恢复模式或大容量日志恢复模式的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库相关。</span><span class="sxs-lookup"><span data-stu-id="e8d70-103">This topic is relevant only for backup and restore of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases that are using the full or bulk-logged recovery models.</span></span>  
  
 <span data-ttu-id="e8d70-104">“结尾日志备份”  捕获尚未备份的任何日志记录（“结尾日志”  ），以防丢失所做的工作并确保日志链完好无损。</span><span class="sxs-lookup"><span data-stu-id="e8d70-104">A *tail-log backup* captures any log records that have not yet been backed up (the *tail of the log*) to prevent work loss and to keep the log chain intact.</span></span> <span data-ttu-id="e8d70-105">在将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库恢复到其最近一个时间点之前，必须先备份数据库的事务日志。</span><span class="sxs-lookup"><span data-stu-id="e8d70-105">Before you can recover a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database to its latest point in time, you must back up the tail of its transaction log.</span></span> <span data-ttu-id="e8d70-106">结尾日志备份将是数据库还原计划中相关的最后一个备份。</span><span class="sxs-lookup"><span data-stu-id="e8d70-106">The tail-log backup will be the last backup of interest in the recovery plan for the database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e8d70-107">并非所有还原方案都要求执行结尾日志备份。</span><span class="sxs-lookup"><span data-stu-id="e8d70-107">Not all restore scenarios require a tail-log backup.</span></span> <span data-ttu-id="e8d70-108">如果恢复点包含在较早的日志备份中，则无需结尾日志备份。</span><span class="sxs-lookup"><span data-stu-id="e8d70-108">You do not need a tail-log backup if the recovery point is contained in an earlier log backup.</span></span> <span data-ttu-id="e8d70-109">此外，如果您准备移动或替换（覆盖）数据库，并且在最新备份后不需要将该数据库还原到某一时间点，则不需要结尾日志备份。</span><span class="sxs-lookup"><span data-stu-id="e8d70-109">Also, a tail-log backup is unnecessary if you are moving or replacing (overwriting) a database and do not need to restore it to a point of time after its most recent backup.</span></span>  
  
 
  
##  <a name="scenarios-that-require-a-tail-log-backup"></a><a name="TailLogScenarios"></a> <span data-ttu-id="e8d70-110">需要结尾日志备份的方案</span><span class="sxs-lookup"><span data-stu-id="e8d70-110">Scenarios That Require a Tail-Log Backup</span></span>  
 <span data-ttu-id="e8d70-111">建议您在以下方案中执行结尾日志备份：</span><span class="sxs-lookup"><span data-stu-id="e8d70-111">We recommend that you take a tail-log backup in the following scenarios:</span></span>  
  
-   <span data-ttu-id="e8d70-112">如果数据库处于联机状态并且您计划对数据库执行还原操作，则从备份日志结尾开始。</span><span class="sxs-lookup"><span data-stu-id="e8d70-112">If the database is online and you plan to perform a restore operation on the database, begin by backing up the tail of the log.</span></span> <span data-ttu-id="e8d70-113">若要避免联机数据库错误，必须使用 .。。[BACKUP](/sql/t-sql/statements/backup-transact-sql)语句的 WITH NORECOVERY 选项 [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e8d70-113">To avoid an error for an online database, you must use the ... WITH NORECOVERY option of the [BACKUP](/sql/t-sql/statements/backup-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
-   <span data-ttu-id="e8d70-114">如果数据库处于脱机状态而无法启动，则需要还原数据库，从备份日志结尾开始。</span><span class="sxs-lookup"><span data-stu-id="e8d70-114">If a database is offline and fails to start and you need to restore the database, first back up the tail of the log.</span></span> <span data-ttu-id="e8d70-115">由于此时不会发生任何事务，因此 WITH NORECOVERY 是可选的。</span><span class="sxs-lookup"><span data-stu-id="e8d70-115">Because no transactions can occur at this time, using the WITH NORECOVERY is optional.</span></span>  
  
-   <span data-ttu-id="e8d70-116">如果数据库损坏，则尝试使用 BACKUP 语句的 WITH CONTINUE_AFTER_ERROR 选项执行结尾日志备份。</span><span class="sxs-lookup"><span data-stu-id="e8d70-116">If a database is damaged, try to take a tail-log backup by using the WITH CONTINUE_AFTER_ERROR option of the BACKUP statement.</span></span>  
  
     <span data-ttu-id="e8d70-117">在损坏的数据库上，仅当日志文件未受损、数据库处于支持结尾日志备份的状态并且数据库不包含任何大容量日志更改时，日志结尾备份才会成功。</span><span class="sxs-lookup"><span data-stu-id="e8d70-117">On a damaged database backing up the tail of the log can succeed only if the log files are undamaged, the database is in a state that supports tail-log backups, and the database does not contain any bulk-logged changes.</span></span> <span data-ttu-id="e8d70-118">如果无法创建结尾日志备份，则最新日志备份后提交的任何事务都将丢失。</span><span class="sxs-lookup"><span data-stu-id="e8d70-118">If a tail-log backup cannot be created, any transactions committed after the latest log backup are lost.</span></span>  
  
 <span data-ttu-id="e8d70-119">下表总结了 BACKUP NORECOVERY 和 CONTINUE_AFTER_ERROR 选项。</span><span class="sxs-lookup"><span data-stu-id="e8d70-119">The following table summarizes the BACKUP NORECOVERY and CONTINUE_AFTER_ERROR options.</span></span>  
  
|<span data-ttu-id="e8d70-120">BACKUP LOG 选项</span><span class="sxs-lookup"><span data-stu-id="e8d70-120">BACKUP LOG option</span></span>|<span data-ttu-id="e8d70-121">注释</span><span class="sxs-lookup"><span data-stu-id="e8d70-121">Comments</span></span>|  
|-----------------------|--------------|  
|<span data-ttu-id="e8d70-122">NORECOVERY</span><span class="sxs-lookup"><span data-stu-id="e8d70-122">NORECOVERY</span></span>|<span data-ttu-id="e8d70-123">每当您准备对数据库继续执行还原操作时，请使用 NORECOVERY。</span><span class="sxs-lookup"><span data-stu-id="e8d70-123">Use NORECOVERY whenever you intend to continue with a restore operation on the database.</span></span> <span data-ttu-id="e8d70-124">NORECOVERY 使数据库进入还原状态。</span><span class="sxs-lookup"><span data-stu-id="e8d70-124">NORECOVERY takes the database into the restoring state.</span></span> <span data-ttu-id="e8d70-125">这确保了数据库在结尾日志备份后不会更改。</span><span class="sxs-lookup"><span data-stu-id="e8d70-125">This guarantees that the database does not change after the tail-log backup.</span></span>  <span data-ttu-id="e8d70-126">除非还指定了 NO_TRUNCATE 选项或 COPY_ONLY 选项，否则日志将被截断。</span><span class="sxs-lookup"><span data-stu-id="e8d70-126">The log is truncated unless the NO_TRUNCATE option or COPY_ONLY option is also specified.</span></span><br /><br /> <span data-ttu-id="e8d70-127">\*\* \* \* 重要 \* 提示 \* \*\* ：建议避免使用 NO_TRUNCATE，除非数据库已损坏。</span><span class="sxs-lookup"><span data-stu-id="e8d70-127">**\*\* Important \*\*** We recommend that you avoid using NO_TRUNCATE, except when the database is damaged.</span></span>|  
|<span data-ttu-id="e8d70-128">CONTINUE_AFTER_ERROR</span><span class="sxs-lookup"><span data-stu-id="e8d70-128">CONTINUE_AFTER_ERROR</span></span>|<span data-ttu-id="e8d70-129">仅当您要备份受损数据库的尾部时，才使用 CONTINUE_AFTER_ERROR。</span><span class="sxs-lookup"><span data-stu-id="e8d70-129">Use CONTINUE_AFTER_ERROR only if you are backing up the tail of a damaged database.</span></span><br /><br /> <span data-ttu-id="e8d70-130">注意：当你对损坏的数据库使用备份日志尾部时，某些通常在日志备份中捕获的元数据可能不可用。</span><span class="sxs-lookup"><span data-stu-id="e8d70-130">Note: When you use back up the tail of the log on a damaged database, some of the metadata ordinarily captured in log backups might be unavailable.</span></span> <span data-ttu-id="e8d70-131">有关详细信息，请参阅本主题后面的[包含不完整备份元数据的结尾日志备份](#IncompleteMetadata)。</span><span class="sxs-lookup"><span data-stu-id="e8d70-131">For more information, see [Tail-Log Backups That Have Incomplete Backup Metadata](#IncompleteMetadata), later in this topic.</span></span>|  
  
##  <a name="tail-log-backups-that-have-incomplete-backup-metadata"></a><a name="IncompleteMetadata"></a><span data-ttu-id="e8d70-132">包含不完整备份元数据的结尾日志备份</span><span class="sxs-lookup"><span data-stu-id="e8d70-132">Tail-Log Backups That Have Incomplete Backup Metadata</span></span>  
 <span data-ttu-id="e8d70-133">结尾日志备份可捕获日志尾部，即使数据库脱机、损坏或缺少数据文件。</span><span class="sxs-lookup"><span data-stu-id="e8d70-133">Tail log backups capture the tail of the log even if the database is offline, damaged, or missing data files.</span></span> <span data-ttu-id="e8d70-134">这可能导致还原信息命令和 **msdb**生成不完整的元数据。</span><span class="sxs-lookup"><span data-stu-id="e8d70-134">This might cause incomplete metadata from the restore information commands and **msdb**.</span></span> <span data-ttu-id="e8d70-135">但只有元数据是不完整的，而捕获的日志是完整且可用的。</span><span class="sxs-lookup"><span data-stu-id="e8d70-135">However, only the metadata is incomplete; the captured log is complete and usable.</span></span>  
  
 <span data-ttu-id="e8d70-136">如果结尾日志备份包含不完整的元数据，则 [backupset](/sql/relational-databases/system-tables/backupset-transact-sql) 表中的 **has_incomplete_metadata** 将设置为 **1**。</span><span class="sxs-lookup"><span data-stu-id="e8d70-136">If a tail-log backup has incomplete metadata, in the [backupset](/sql/relational-databases/system-tables/backupset-transact-sql) table, **has_incomplete_metadata** is set to **1**.</span></span> <span data-ttu-id="e8d70-137">此外，在 [RESTORE HEADERONLY](/sql/t-sql/statements/restore-statements-headeronly-transact-sql)的输出中， **HasIncompleteMetadata** 将设置为 **1**。</span><span class="sxs-lookup"><span data-stu-id="e8d70-137">Also, in the output of [RESTORE HEADERONLY](/sql/t-sql/statements/restore-statements-headeronly-transact-sql), **HasIncompleteMetadata** is set to **1**.</span></span>  
  
 <span data-ttu-id="e8d70-138">如果结尾日志备份中的元数据不完整，则 [backupfilegroup](/sql/relational-databases/system-tables/backupfilegroup-transact-sql) 表在结尾日志备份时将丢失文件组的大多数相关信息。</span><span class="sxs-lookup"><span data-stu-id="e8d70-138">If the metadata in a tail-log backup is incomplete, the [backupfilegroup](/sql/relational-databases/system-tables/backupfilegroup-transact-sql) table will be missing most of the information about filegroups at the time of the tail-log backup.</span></span> <span data-ttu-id="e8d70-139">大多数 **backupfilegroup** 表列为 NULL；只有以下几列有意义：</span><span class="sxs-lookup"><span data-stu-id="e8d70-139">Most of the **backupfilegroup** table columns are NULL; the only meaningful columns are as follows:</span></span>  
  
-   <span data-ttu-id="e8d70-140">**backup_set_id**</span><span class="sxs-lookup"><span data-stu-id="e8d70-140">**backup_set_id**</span></span>  
  
-   <span data-ttu-id="e8d70-141">**filegroup_id**</span><span class="sxs-lookup"><span data-stu-id="e8d70-141">**filegroup_id**</span></span>  
  
-   <span data-ttu-id="e8d70-142">type </span><span class="sxs-lookup"><span data-stu-id="e8d70-142">**type**</span></span>  
  
-   <span data-ttu-id="e8d70-143">**type_desc**</span><span class="sxs-lookup"><span data-stu-id="e8d70-143">**type_desc**</span></span>  
  
-   <span data-ttu-id="e8d70-144">**is_readonly**</span><span class="sxs-lookup"><span data-stu-id="e8d70-144">**is_readonly**</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="e8d70-145">相关任务</span><span class="sxs-lookup"><span data-stu-id="e8d70-145">Related Tasks</span></span>  
 <span data-ttu-id="e8d70-146">要创建结尾日志备份，请参阅[在数据库损坏时备份事务日志 (SQL Server)](back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="e8d70-146">To create a tail-log backup, see [Back Up the Transaction Log When the Database Is Damaged &#40;SQL Server&#41;](back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md).</span></span>  
  
 <span data-ttu-id="e8d70-147">若要还原事务日志备份，请参阅[还原事务日志备份 (SQL Server)](restore-a-transaction-log-backup-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="e8d70-147">To restore a transaction log backup, see [Restore a Transaction Log Backup &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8d70-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e8d70-148">See Also</span></span>  
 <span data-ttu-id="e8d70-149">[BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e8d70-149">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="e8d70-150">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e8d70-150">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="e8d70-151">[SQL Server 数据库的备份和还原](back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="e8d70-151">[Back Up and Restore of SQL Server Databases](back-up-and-restore-of-sql-server-databases.md) </span></span>  
 <span data-ttu-id="e8d70-152">[仅复制备份 (SQL Server)](copy-only-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e8d70-152">[Copy-Only Backups &#40;SQL Server&#41;](copy-only-backups-sql-server.md) </span></span>  
 <span data-ttu-id="e8d70-153">[事务日志备份 (SQL Server)](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e8d70-153">[Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 [<span data-ttu-id="e8d70-154">应用事务日志备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e8d70-154">Apply Transaction Log Backups &#40;SQL Server&#41;</span></span>](apply-transaction-log-backups-sql-server.md)  
  
  
