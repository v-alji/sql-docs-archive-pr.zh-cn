---
title: 联机还原 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- online restores [SQL Server]
- online restores [SQL Server], about online restores
ms.assetid: 7982a687-980a-4eb8-8e9f-6894148e7d8c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4db4d5b5ce08c50646857099d82964bb944bc8af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589180"
---
# <a name="online-restore-sql-server"></a><span data-ttu-id="4b109-102">联机还原 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4b109-102">Online Restore (SQL Server)</span></span>
  <span data-ttu-id="4b109-103">只有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise Edition 支持联机还原。</span><span class="sxs-lookup"><span data-stu-id="4b109-103">Online restore is supported only on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise edition.</span></span> <span data-ttu-id="4b109-104">在此版本中，文件还原、页面还原或段落还原默认处于联机状态。</span><span class="sxs-lookup"><span data-stu-id="4b109-104">In this edition, a file, page, or piecemeal restore is online by default.</span></span> <span data-ttu-id="4b109-105">本主题与包含多个文件或文件组的数据库相关；在简单恢复模式下，仅与包含只读文件组的数据库相关。</span><span class="sxs-lookup"><span data-stu-id="4b109-105">This topic is relevant for databases that contain multiple files or filegroups (and, under the simple recovery model, only for read-only filegroups).</span></span>  
  
 <span data-ttu-id="4b109-106">数据库联机时还原数据的过程称为“联机还原”  。</span><span class="sxs-lookup"><span data-stu-id="4b109-106">Restoring data while the database is online is called an *online restore*.</span></span> <span data-ttu-id="4b109-107">只要主文件组处于联机状态，就将数据库视为联机，即使有一个或多个辅助文件组处于脱机状态。</span><span class="sxs-lookup"><span data-stu-id="4b109-107">A database is considered to be online whenever the primary filegroup is online, even if one or more of its secondary filegroups are offline.</span></span> <span data-ttu-id="4b109-108">在任何恢复模式下，您都可以在数据库联机时还原处于脱机状态的文件。</span><span class="sxs-lookup"><span data-stu-id="4b109-108">Under any recovery model, you can restore a file that is offline while the database is online.</span></span> <span data-ttu-id="4b109-109">在完整恢复模式下，您还可以在数据库联机时还原页。</span><span class="sxs-lookup"><span data-stu-id="4b109-109">Under the full recovery model, you can also restore pages while the database is online.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4b109-110">联机还原自动在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise 上执行，不需要用户执行任何操作。</span><span class="sxs-lookup"><span data-stu-id="4b109-110">Online restore occurs automatically on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise and requires no user action.</span></span> <span data-ttu-id="4b109-111">如果不想使用联机还原，则可以在开始还原之前使数据库脱机。</span><span class="sxs-lookup"><span data-stu-id="4b109-111">If you do not want to use online restore, you can take a database offline before you start a restore.</span></span> <span data-ttu-id="4b109-112">有关详细信息，请参阅本主题后面的 [使数据库或文件脱机](#taking_db_or_file_offline)。</span><span class="sxs-lookup"><span data-stu-id="4b109-112">For more information, see [Taking a Database or File Offline](#taking_db_or_file_offline), later in this topic.</span></span>  
  
 <span data-ttu-id="4b109-113">联机文件还原期间，正在还原的任何文件及其文件组均处于脱机状态。</span><span class="sxs-lookup"><span data-stu-id="4b109-113">During an online file restore, any file being restored and its filegroup are offline.</span></span> <span data-ttu-id="4b109-114">如果联机还原开始时这些文件中有任何一个处于联机状态的话，则第一个还原语句将使该文件的文件组脱机。</span><span class="sxs-lookup"><span data-stu-id="4b109-114">If any of these files is online when an online restore starts, the first restore statement takes the filegroup of the file offline.</span></span> <span data-ttu-id="4b109-115">相反，联机页还原期间，只有页处于脱机状态。</span><span class="sxs-lookup"><span data-stu-id="4b109-115">In contrast, during an online page restore, only the page is offline.</span></span>  
  
 <span data-ttu-id="4b109-116">所有联机还原方案均涉及以下几个基本步骤：</span><span class="sxs-lookup"><span data-stu-id="4b109-116">Every online restore scenario involves the following basic steps:</span></span>  
  
1.  <span data-ttu-id="4b109-117">还原数据。</span><span class="sxs-lookup"><span data-stu-id="4b109-117">Restore the data.</span></span>  
  
2.  <span data-ttu-id="4b109-118">使用 WITH RECOVERY 还原最近的日志。</span><span class="sxs-lookup"><span data-stu-id="4b109-118">Restore the log by using WITH RECOVERY for the last log restore.</span></span> <span data-ttu-id="4b109-119">此操作将使还原的数据联机。</span><span class="sxs-lookup"><span data-stu-id="4b109-119">This brings the restored data online.</span></span>  
  
 <span data-ttu-id="4b109-120">有时，未提交的事务无法回滚，因为回滚所需的数据在启动时处于脱机状态。</span><span class="sxs-lookup"><span data-stu-id="4b109-120">Occasionally, an uncommitted transaction cannot be rolled back because the data that is required by rollback is offline during startup.</span></span> <span data-ttu-id="4b109-121">在这种情况下，将延迟该事务。</span><span class="sxs-lookup"><span data-stu-id="4b109-121">In this case, the transaction is deferred.</span></span> <span data-ttu-id="4b109-122">有关详细信息，请参阅 [延迟的事务 (SQL Server)](deferred-transactions-sql-server.md)中删除失效的文件组。</span><span class="sxs-lookup"><span data-stu-id="4b109-122">For more information, see [Deferred Transactions &#40;SQL Server&#41;](deferred-transactions-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4b109-123">如果数据库正在使用大容量日志恢复模式，建议您在开始执行联机还原之前切换到完整恢复模式。</span><span class="sxs-lookup"><span data-stu-id="4b109-123">If the database is currently using the bulk-logged recovery model, we recommend that you switch to the full recovery model before you start an online restore.</span></span> <span data-ttu-id="4b109-124">有关详细信息，请参阅[查看或更改数据库的恢复模式 (SQL Server)](view-or-change-the-recovery-model-of-a-database-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="4b109-124">For more information, see [View or Change the Recovery Model of a Database &#40;SQL Server&#41;](view-or-change-the-recovery-model-of-a-database-sql-server.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="4b109-125">如果创建备份时有多个设备连接到服务器，则联机还原期间，可用设备数必须相同。</span><span class="sxs-lookup"><span data-stu-id="4b109-125">If the backups were taken with multiple devices that were attached to the server, the same number of devices must be available during an online restore.</span></span>  
  
## <a name="log-backups-for-online-restore"></a><span data-ttu-id="4b109-126">联机还原所需的日志备份</span><span class="sxs-lookup"><span data-stu-id="4b109-126">Log Backups for Online Restore</span></span>  
 <span data-ttu-id="4b109-127">对于联机还原，恢复点就是要恢复的数据最后一次变为脱机或只读时的点。</span><span class="sxs-lookup"><span data-stu-id="4b109-127">In an online restore, the recovery point is the point when the data being restored was taken offline or made read-only for the last time.</span></span> <span data-ttu-id="4b109-128">截止到该恢复点（包括该恢复点）的事务日志备份都必须是可用的。</span><span class="sxs-lookup"><span data-stu-id="4b109-128">The transaction log backups leading up to and including this recovery point must all be available.</span></span> <span data-ttu-id="4b109-129">通常在该点后都需要日志备份，以覆盖文件的恢复点。</span><span class="sxs-lookup"><span data-stu-id="4b109-129">Generally, a log backup is required after that point to cover the recovery point for the file.</span></span> <span data-ttu-id="4b109-130">唯一的例外情况是在使用当数据变为只读后执行的数据备份对只读数据进行联机还原的时候。</span><span class="sxs-lookup"><span data-stu-id="4b109-130">The only exception is during an online restore of read-only data from a data backup that was taken after the data became read-only.</span></span> <span data-ttu-id="4b109-131">在这种情况下，不必准备日志备份。</span><span class="sxs-lookup"><span data-stu-id="4b109-131">In this case, you do not have to have a log backup.</span></span>  
  
 <span data-ttu-id="4b109-132">通常，即使在启动还原顺序之后，您也可以在数据库联机时执行事务日志备份。</span><span class="sxs-lookup"><span data-stu-id="4b109-132">Generally, you may take transaction log backups while the database is online, even after the start of the restore sequence.</span></span> <span data-ttu-id="4b109-133">上次日志备份的时间取决于要还原的文件的属性：</span><span class="sxs-lookup"><span data-stu-id="4b109-133">The timing of the last log backup depends on the properties of the file being restored:</span></span>  
  
-   <span data-ttu-id="4b109-134">对于联机只读文件，可以在第一次还原顺序之前或期间执行恢复所需的上次日志备份。</span><span class="sxs-lookup"><span data-stu-id="4b109-134">For an online read-only file, you can take the last log backup that is required for recovery before or during the first restore sequence.</span></span> <span data-ttu-id="4b109-135">如果在文件组变为只读以后执行数据备份或差异备份，则只读文件组可能不需要日志备份。</span><span class="sxs-lookup"><span data-stu-id="4b109-135">A read-only filegroup may not require log backups if a data or differential backup was taken after the filegroup became read-only.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4b109-136">以上信息也适用于所有脱机文件。</span><span class="sxs-lookup"><span data-stu-id="4b109-136">The preceding information also applies to every offline file.</span></span>  
  
-   <span data-ttu-id="4b109-137">值得注意的特殊情况是这样一种读写文件：在执行第一个还原语句时处于联机状态，然后被该还原语句自动变为脱机的读写文件。</span><span class="sxs-lookup"><span data-stu-id="4b109-137">A special case exists for a read/write file that was online when the first restore statement was issued and that was then automatically taken offline by that restore statement.</span></span> <span data-ttu-id="4b109-138">在这种情况下，必须在第一个 *还原顺序* （用于还原、前滚和恢复数据的一个或多个 RESTORE 语句的顺序）期间执行日志备份。</span><span class="sxs-lookup"><span data-stu-id="4b109-138">In this case, you must take a log backup during the first *restore sequence* (the sequence of one or more RESTORE statements that restore, roll forward, and recover data).</span></span> <span data-ttu-id="4b109-139">通常，必须在还原所有完整备份之后并在恢复数据之前执行日志备份。</span><span class="sxs-lookup"><span data-stu-id="4b109-139">Generally, this log backup must occur after you restore all the full backups and before you recover the data.</span></span> <span data-ttu-id="4b109-140">但是，如果特定的文件组有多个文件备份，则最小的日志备份点为文件组脱机的时候。</span><span class="sxs-lookup"><span data-stu-id="4b109-140">However, if there are multiple file backups for a specific filegroup, the minimal point of log backup is the time after the filegroup is offline.</span></span> <span data-ttu-id="4b109-141">这个数据还原后的日志备份将捕获文件变为脱机时的点。</span><span class="sxs-lookup"><span data-stu-id="4b109-141">This post-data-restore log backup captures the point at which the file was taken offline.</span></span> <span data-ttu-id="4b109-142">数据还原后的日志备份是必要的，因为 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 无法将联机日志用于联机还原。</span><span class="sxs-lookup"><span data-stu-id="4b109-142">The post-data-restore log backup is necessary because the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] cannot use online log for an online restore.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4b109-143">或者，也可以在开始还原顺序前手动使文件脱机。</span><span class="sxs-lookup"><span data-stu-id="4b109-143">Alternatively, you can manually take the file offline before the restore sequence.</span></span> <span data-ttu-id="4b109-144">有关详细信息，请参阅本主题后面的“使数据库或文件脱机”。</span><span class="sxs-lookup"><span data-stu-id="4b109-144">For more information, see "Taking a Database or File Offline" later in this topic.</span></span>  
  
##  <a name="taking-a-database-or-file-offline"></a><a name="taking_db_or_file_offline"></a> <span data-ttu-id="4b109-145">使数据库或文件脱机</span><span class="sxs-lookup"><span data-stu-id="4b109-145">Taking a Database or File Offline</span></span>  
 <span data-ttu-id="4b109-146">如果不想使用联机还原，则可以使用以下方法之一，在启动还原顺序之前使数据库脱机：</span><span class="sxs-lookup"><span data-stu-id="4b109-146">If you do not want to use online restore, you can take the database offline before you start the restore sequence by using one of the following methods:</span></span>  
  
-   <span data-ttu-id="4b109-147">在任何恢复模式下，您都可以使用以下 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) 语句使数据库脱机：</span><span class="sxs-lookup"><span data-stu-id="4b109-147">Under any recovery model, you can take the database offline by using the following [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) statement:</span></span>  
  
     <span data-ttu-id="4b109-148">ALTER DATABASE *database_name* SET OFFLINE</span><span class="sxs-lookup"><span data-stu-id="4b109-148">ALTER DATABASE *database_name* SET OFFLINE</span></span>  
  
-   <span data-ttu-id="4b109-149">或者，在完整恢复模式下，可以通过使用以下 [BACKUP LOG](/sql/t-sql/statements/backup-transact-sql) 语句将数据库置于还原状态，强制文件还原或页还原脱机：</span><span class="sxs-lookup"><span data-stu-id="4b109-149">Alternatively, under the full recovery model, you can force a file or page restore to be offline, by using the following [BACKUP LOG](/sql/t-sql/statements/backup-transact-sql) statement put the database in to the restoring state:</span></span>  
  
     <span data-ttu-id="4b109-150">BACKUP LOG *database_name* WITH NORECOVERY。</span><span class="sxs-lookup"><span data-stu-id="4b109-150">BACKUP LOG *database_name* WITH NORECOVERY.</span></span>  
  
 <span data-ttu-id="4b109-151">只要数据库保持脱机状态，所有还原就都是脱机还原。</span><span class="sxs-lookup"><span data-stu-id="4b109-151">As long as a database remains offline, all restores are offline restores.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="4b109-152">示例</span><span class="sxs-lookup"><span data-stu-id="4b109-152">Examples</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4b109-153">联机还原顺序的语法与脱机还原顺序的语法完全相同。</span><span class="sxs-lookup"><span data-stu-id="4b109-153">The syntax for an online restore sequence is the same as for an offline restore sequence.</span></span>  
  
-   [<span data-ttu-id="4b109-154">示例：数据库的段落还原（简单恢复模式）</span><span class="sxs-lookup"><span data-stu-id="4b109-154">Example: Piecemeal Restore of Database &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [<span data-ttu-id="4b109-155">示例：仅对某些文件组进行段落还原（简单恢复模式）</span><span class="sxs-lookup"><span data-stu-id="4b109-155">Example: Piecemeal Restore of Only Some Filegroups &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [<span data-ttu-id="4b109-156">示例：只读文件的联机还原（简单恢复模式）</span><span class="sxs-lookup"><span data-stu-id="4b109-156">Example: Online Restore of a Read-Only File &#40;Simple Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [<span data-ttu-id="4b109-157">示例：数据库的段落还原（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="4b109-157">Example: Piecemeal Restore of Database &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [<span data-ttu-id="4b109-158">示例：仅对某些文件组进行段落还原（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="4b109-158">Example: Piecemeal Restore of Only Some Filegroups &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [<span data-ttu-id="4b109-159">示例：读/写文件的联机还原（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="4b109-159">Example: Online Restore of a Read-Write File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
-   [<span data-ttu-id="4b109-160">示例：只读文件的联机还原（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="4b109-160">Example: Online Restore of a Read-Only File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="4b109-161">相关任务</span><span class="sxs-lookup"><span data-stu-id="4b109-161">Related Tasks</span></span>  
  
-   [<span data-ttu-id="4b109-162">还原文件和文件组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4b109-162">Restore Files and Filegroups &#40;SQL Server&#41;</span></span>](restore-files-and-filegroups-sql-server.md)  
  
-   [<span data-ttu-id="4b109-163">还原页 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4b109-163">Restore Pages &#40;SQL Server&#41;</span></span>](restore-pages-sql-server.md)  
  
-   [<span data-ttu-id="4b109-164">管理 suspect_pages 表 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4b109-164">Manage the suspect_pages Table &#40;SQL Server&#41;</span></span>](manage-the-suspect-pages-table-sql-server.md)  
  
-   [<span data-ttu-id="4b109-165">恢复数据库但不还原数据 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4b109-165">Recover a Database Without Restoring Data &#40;Transact-SQL&#41;</span></span>](recover-a-database-without-restoring-data-transact-sql.md)  
  
-   [<span data-ttu-id="4b109-166">删除失效文件组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4b109-166">Remove Defunct Filegroups &#40;SQL Server&#41;</span></span>](remove-defunct-filegroups-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="4b109-167">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4b109-167">See Also</span></span>  
 <span data-ttu-id="4b109-168">[文件还原（完整恢复模式）](file-restores-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="4b109-168">[File Restores &#40;Full Recovery Model&#41;](file-restores-full-recovery-model.md) </span></span>  
 <span data-ttu-id="4b109-169">[文件还原（简单恢复模式）](file-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="4b109-169">[File Restores &#40;Simple Recovery Model&#41;](file-restores-simple-recovery-model.md) </span></span>  
 <span data-ttu-id="4b109-170">[还原页 (SQL Server)](restore-pages-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4b109-170">[Restore Pages &#40;SQL Server&#41;](restore-pages-sql-server.md) </span></span>  
 <span data-ttu-id="4b109-171">[段落还原 (SQL Server)](piecemeal-restores-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4b109-171">[Piecemeal Restores &#40;SQL Server&#41;](piecemeal-restores-sql-server.md) </span></span>  
 [<span data-ttu-id="4b109-172">还原和恢复概述 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4b109-172">Restore and Recovery Overview &#40;SQL Server&#41;</span></span>](restore-and-recovery-overview-sql-server.md)  
  
  
