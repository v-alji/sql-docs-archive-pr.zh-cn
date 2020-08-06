---
title: 完整文件备份 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full backups [SQL Server]
- backing up [SQL Server], files or filegroups
- backups [SQL Server], files or filegroups
- full recovery model [SQL Server], full file backups
- file backups [SQL Server], full
- files [SQL Server], backing up
- filegroups [SQL Server], backing up
- file backups [SQL Server]
ms.assetid: a716bf8d-0c5a-490d-aadd-597b3b0fac0c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e2e45dc68afa4d464aa3931075a1c1b3be792e6f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589185"
---
# <a name="full-file-backups-sql-server"></a><span data-ttu-id="69053-102">完整文件备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="69053-102">Full File Backups (SQL Server)</span></span>
  <span data-ttu-id="69053-103">本主题适用于包含多个文件或文件组的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="69053-103">This topic is relevant for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] databases that contain multiple files or filegroups.</span></span>  
  
 <span data-ttu-id="69053-104">可以分别备份和还原 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据库中的文件。</span><span class="sxs-lookup"><span data-stu-id="69053-104">The files in a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database can be backed up and restored individually.</span></span> <span data-ttu-id="69053-105">此外，可以指定整个文件组，而不是逐个指定每个构成文件。</span><span class="sxs-lookup"><span data-stu-id="69053-105">Also, you can specify a whole filegroup instead of specifying each constituent file individually.</span></span> <span data-ttu-id="69053-106">请注意，如果文件组中的任何文件脱机（例如，由于正在还原该文件），则整个文件组均将脱机并且无法备份。</span><span class="sxs-lookup"><span data-stu-id="69053-106">Note that if any file in a filegroup is offline (for example, because the file is being restored), the whole filegroup is offline and cannot be backed up.</span></span>  
  
 <span data-ttu-id="69053-107">只读文件组的文件备份可以与部分备份一起使用。</span><span class="sxs-lookup"><span data-stu-id="69053-107">File backups of read-only filegroups can be combined with partial backups.</span></span> <span data-ttu-id="69053-108">部分备份包括所有读/写文件组以及可选的一个或多个只读文件组。</span><span class="sxs-lookup"><span data-stu-id="69053-108">Partial backups include all the read/write filegroups and, optionally, one or more read-only filegroups.</span></span> <span data-ttu-id="69053-109">有关详细信息，请参阅[部分备份 (SQL Server)](partial-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="69053-109">For more information, see [Partial Backups &#40;SQL Server&#41;](partial-backups-sql-server.md).</span></span>  
  
 <span data-ttu-id="69053-110">文件备份可以用作差异文件备份的“差异基准  ”。</span><span class="sxs-lookup"><span data-stu-id="69053-110">A file backup can serve as the *differential base* for differential file backups.</span></span> <span data-ttu-id="69053-111">有关详细信息，请参阅 [差异备份 (SQL Server)](differential-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="69053-111">For more information, see [Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="69053-112">除了在与“差异文件备份”  明确进行比较的时候，完整文件备份通常称为文件备份  。</span><span class="sxs-lookup"><span data-stu-id="69053-112">Full file backups are typically called *file backups*, except when they are being explicitly compared with *differential file backups*.</span></span>  
  
 <span data-ttu-id="69053-113">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="69053-113">**In This Topic:**</span></span>  
  
-   [<span data-ttu-id="69053-114">文件备份的优点</span><span class="sxs-lookup"><span data-stu-id="69053-114">Benefits of File Backups</span></span>](#Benefits)  
  
-   [<span data-ttu-id="69053-115">文件备份的缺点</span><span class="sxs-lookup"><span data-stu-id="69053-115">Disadvantages of File Backups</span></span>](#Disadvantages)  
  
-   [<span data-ttu-id="69053-116">文件备份概述</span><span class="sxs-lookup"><span data-stu-id="69053-116">Overview of File Backups</span></span>](#Overview)  
  
-   [<span data-ttu-id="69053-117">相关任务</span><span class="sxs-lookup"><span data-stu-id="69053-117">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="benefits-of-file-backups"></a><a name="Benefits"></a> <span data-ttu-id="69053-118">文件备份的优点</span><span class="sxs-lookup"><span data-stu-id="69053-118">Benefits of File Backups</span></span>  
 <span data-ttu-id="69053-119">相对于数据库备份，文件备份具有如下优点：</span><span class="sxs-lookup"><span data-stu-id="69053-119">File backups offer the following advantages over database backups:</span></span>  
  
-   <span data-ttu-id="69053-120">使用文件备份使您能够只还原损坏的文件，而不用还原数据库的其余部分，从而加快了恢复速度。</span><span class="sxs-lookup"><span data-stu-id="69053-120">Using file backups can increase the speed of recovery by letting you restore only damaged files, without restoring the rest of the database.</span></span>  
  
     <span data-ttu-id="69053-121">例如，如果数据库由位于不同磁盘上的若干个文件组成，在其中一个磁盘发生故障时，只需还原故障磁盘上的文件。</span><span class="sxs-lookup"><span data-stu-id="69053-121">For example, if a database consists of several files that are located on different disks and one disk fails, only the file on the failed disk has to be restored.</span></span> <span data-ttu-id="69053-122">可以快速还原已损坏的文件，并且恢复速度快于针对整个数据库的恢复速度。</span><span class="sxs-lookup"><span data-stu-id="69053-122">The damaged file can be quickly restored, and recovery is faster than it would be for an entire database.</span></span>  
  
-   <span data-ttu-id="69053-123">与完整数据库备份（对于超大型数据库而言，变得难以管理）相比，文件备份增加了计划和介质处理的灵活性。</span><span class="sxs-lookup"><span data-stu-id="69053-123">File backups increase flexibility in scheduling and media handling over full database backups, which for very large databases can become unmanageable.</span></span> <span data-ttu-id="69053-124">文件或文件组备份的更高灵活性对于包含具有不同更新特征的数据的大型数据库也很有用。</span><span class="sxs-lookup"><span data-stu-id="69053-124">The increased flexibility of file or filegroup backups is also useful for large databases that contain data that has varying update characteristics.</span></span>  
  
##  <a name="disadvantages-of-file-backups"></a><a name="Disadvantages"></a> <span data-ttu-id="69053-125">文件备份的缺点</span><span class="sxs-lookup"><span data-stu-id="69053-125">Disadvantages of File Backups</span></span>  
  
-   <span data-ttu-id="69053-126">与完整数据库备份相比，文件备份的主要缺点是管理较复杂。</span><span class="sxs-lookup"><span data-stu-id="69053-126">The primary disadvantage of file backups compared to full database backups is the additional administrative complexity.</span></span> <span data-ttu-id="69053-127">维护和跟踪这些完整备份是一种耗时的任务，所需空间可能会超过完整数据库备份的所需空间。</span><span class="sxs-lookup"><span data-stu-id="69053-127">Maintaining and keeping track of a complete set of these backups can be a time-consuming task that might outweigh the space requirements of full database backups.</span></span>  
  
-   <span data-ttu-id="69053-128">如果某个损坏的文件未备份，那么介质故障可能会导致无法恢复整个数据库。</span><span class="sxs-lookup"><span data-stu-id="69053-128">A media failure can make a complete database unrecoverable if a damaged file lacks a backup.</span></span> <span data-ttu-id="69053-129">因此，必须维护一组完整的文件备份，对于完整/大容量日志恢复模式，还必须维护一个或多个日志备份，这些日志备份至少涵盖第一个完整文件备份和最后一个完整备份之间的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="69053-129">You must therefore maintain a complete set of file backups, and, for the full/bulk-logged recovery model, one or more log backups covering minimally the interval between the first full file backup and last full file backup.</span></span>  
  
##  <a name="overview-of-file-backups"></a><a name="Overview"></a> <span data-ttu-id="69053-130">文件备份概述</span><span class="sxs-lookup"><span data-stu-id="69053-130">Overview of File Backups</span></span>  
 <span data-ttu-id="69053-131">完整文件备份指备份一个或多个文件或文件组中的所有数据。</span><span class="sxs-lookup"><span data-stu-id="69053-131">A full file backup backs up all the data in one or more files or filegroups.</span></span> <span data-ttu-id="69053-132">文件备份在默认情况下包含足够的日志记录，可以将文件前滚至备份操作的末尾。</span><span class="sxs-lookup"><span data-stu-id="69053-132">By default, file backups contain enough log records to roll forward the file to the end of the backup operation.</span></span>  
  
 <span data-ttu-id="69053-133">备份只读文件或文件组的方法对每种恢复模式均相同。</span><span class="sxs-lookup"><span data-stu-id="69053-133">Backing up a read-only file or filegroup is the same for every recovery model.</span></span> <span data-ttu-id="69053-134">在完整恢复模式下，一整套完整文件备份与跨所有文件备份的足够日志备份合起来等同于完整数据库备份。</span><span class="sxs-lookup"><span data-stu-id="69053-134">Under the full recovery model, a complete set of full file backups, together with enough log backups to span all the file backups, is the equivalent of a full database backup.</span></span>  
  
 <span data-ttu-id="69053-135">一次只能进行一个文件备份操作。</span><span class="sxs-lookup"><span data-stu-id="69053-135">Only one file backup operation can occur at a time.</span></span> <span data-ttu-id="69053-136">可以在一个操作中备份多个文件，但如果只需要还原一个文件，这样做可能会延长恢复时间。</span><span class="sxs-lookup"><span data-stu-id="69053-136">You can back up multiple files in one operation, but this might extend the recovery time if you only have to restore a single file.</span></span> <span data-ttu-id="69053-137">这是因为查找该文件时，将读取整个备份。</span><span class="sxs-lookup"><span data-stu-id="69053-137">This is because to locate that file, the whole backup is read.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="69053-138">单个文件可以从数据库备份中还原；但与从文件备份中还原相比，从数据库备份中找到和还原文件所需的时间更长。</span><span class="sxs-lookup"><span data-stu-id="69053-138">Individual files can be restored from a database backup; however, locating and restoring a file takes longer from a database backup than from a file backup.</span></span>  
  
### <a name="file-backups-and-the-simple-recovery-model"></a><span data-ttu-id="69053-139">文件备份和简单恢复模式</span><span class="sxs-lookup"><span data-stu-id="69053-139">File Backups and the Simple Recovery Model</span></span>  
 <span data-ttu-id="69053-140">在简单恢复模式下，必须一起备份所有读/写文件。</span><span class="sxs-lookup"><span data-stu-id="69053-140">Under the simple recovery model, read/write files must all be backed up together.</span></span> <span data-ttu-id="69053-141">这样可以确保将数据库还原到一致的时点。</span><span class="sxs-lookup"><span data-stu-id="69053-141">This makes sure that the database can be restored to a consistent point in time.</span></span> <span data-ttu-id="69053-142">请使用 READ_WRITE_FILEGROUPS 选项，而不是逐个指定每个读/写文件或文件组。</span><span class="sxs-lookup"><span data-stu-id="69053-142">Instead of individually specifying each read/write file or filegroup, use the READ_WRITE_FILEGROUPS option.</span></span> <span data-ttu-id="69053-143">此选项用于备份数据库中的所有读/写文件组。</span><span class="sxs-lookup"><span data-stu-id="69053-143">This option backs up all the read/write filegroups in the database.</span></span> <span data-ttu-id="69053-144">通过指定 READ_WRITE_FILEGROUPS 创建的备份称为部分备份。</span><span class="sxs-lookup"><span data-stu-id="69053-144">A backup that is created by specifying READ_WRITE_FILEGROUPS is known as a partial backup.</span></span> <span data-ttu-id="69053-145">有关详细信息，请参阅[部分备份 (SQL Server)](partial-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="69053-145">For more information, see [Partial Backups &#40;SQL Server&#41;](partial-backups-sql-server.md).</span></span>  
  
### <a name="file-backups-and-the-full-recovery-model"></a><span data-ttu-id="69053-146">文件备份和完全恢复模式</span><span class="sxs-lookup"><span data-stu-id="69053-146">File Backups and the Full Recovery Model</span></span>  
 <span data-ttu-id="69053-147">在完整恢复模式下，必须备份事务日志，不用考虑备份策略的其余部分。</span><span class="sxs-lookup"><span data-stu-id="69053-147">Under the full recovery model, you must back up the transaction log, regardless of the rest of your backup strategy.</span></span> <span data-ttu-id="69053-148">一整套完整文件备份与涵盖从第一个文件备份开始的所有文件备份的足够日志备份合起来等同于完整数据库备份。</span><span class="sxs-lookup"><span data-stu-id="69053-148">A complete set of full file backups, together with enough log backups to span all the file backups from the start of the first file backup, is the equivalent of a full database backup.</span></span>  
  
 <span data-ttu-id="69053-149">仅使用文件备份和日志备份还原数据库的操作可能比较复杂。</span><span class="sxs-lookup"><span data-stu-id="69053-149">Restoring a database using just file and log backups can be complex.</span></span> <span data-ttu-id="69053-150">因此，如果可能，最好执行完整数据库备份并在第一个文件备份开始之前开始日志备份。</span><span class="sxs-lookup"><span data-stu-id="69053-150">Therefore, if it is possible, it is a best practice to perform a full database backup and start the log backups before the first file backup.</span></span> <span data-ttu-id="69053-151">下图显示了在创建数据库（在 t0 时间）之后立即执行完整数据库备份（在 t1 时间）的策略。</span><span class="sxs-lookup"><span data-stu-id="69053-151">The following illustration shows a strategy in which a full database backup is taken (at time t1) soon after the database is created (at time t0).</span></span> <span data-ttu-id="69053-152">创建了第一个数据库备份之后，便可开始执行事务日志备份。</span><span class="sxs-lookup"><span data-stu-id="69053-152">This first database backup enables transaction log backups to start.</span></span> <span data-ttu-id="69053-153">事务日志备份计划按设置的间隔执行。</span><span class="sxs-lookup"><span data-stu-id="69053-153">Transaction log backups are scheduled to occur at set intervals.</span></span> <span data-ttu-id="69053-154">文件备份以最适合数据库业务要求的间隔执行。</span><span class="sxs-lookup"><span data-stu-id="69053-154">File backups occur at whatever interval best meets the business requirements for the database.</span></span> <span data-ttu-id="69053-155">此图显示了四个文件组，每次备份其中的一个文件组。</span><span class="sxs-lookup"><span data-stu-id="69053-155">This illustration shows each of the four filegroups being backed up one at a time.</span></span> <span data-ttu-id="69053-156">它们的备份顺序（A、C、B、A）反映了数据库的业务要求。</span><span class="sxs-lookup"><span data-stu-id="69053-156">The order in which they are backed up (A, C, B, A) reflects the business requirements of the database.</span></span>  
  
 <span data-ttu-id="69053-157">![合并数据库、文件和日志备份的策略](../../database-engine/media/bnr-rmfull-3-fulldb-filegrps-log-backups.gif "合并数据库、文件和日志备份的策略")</span><span class="sxs-lookup"><span data-stu-id="69053-157">![Strategy combining database, file, and log backups](../../database-engine/media/bnr-rmfull-3-fulldb-filegrps-log-backups.gif "Strategy combining database, file, and log backups")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="69053-158">在完整恢复模式下，必须在还原读/写文件备份时前滚事务日志，以确保该文件与数据库的其余部分保持一致。</span><span class="sxs-lookup"><span data-stu-id="69053-158">Under the full recovery model, you must roll forward the transaction log when restoring a read/write file backup to make sure that the file is consistent with the rest of the database.</span></span> <span data-ttu-id="69053-159">若要避免前滚大量事务日志备份，请考虑使用差异文件备份。</span><span class="sxs-lookup"><span data-stu-id="69053-159">To avoid rolling forward a lot of transaction log backups, consider using differential file backups.</span></span> <span data-ttu-id="69053-160">有关详细信息，请参阅 [差异备份 (SQL Server)](differential-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="69053-160">For more information, see [Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="69053-161">相关任务</span><span class="sxs-lookup"><span data-stu-id="69053-161">Related Tasks</span></span>  
 <span data-ttu-id="69053-162">**创建文件或文件组备份**</span><span class="sxs-lookup"><span data-stu-id="69053-162">**To create a file or filegroup backup**</span></span>  
  
-   [<span data-ttu-id="69053-163">备份文件和文件组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="69053-163">Back Up Files and Filegroups &#40;SQL Server&#41;</span></span>](back-up-files-and-filegroups-sql-server.md)  
  
-   <span data-ttu-id="69053-164"><xref:Microsoft.SqlServer.Management.Smo.Backup.SqlBackup%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="69053-164"><xref:Microsoft.SqlServer.Management.Smo.Backup.SqlBackup%2A> (SMO)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="69053-165">维护计划向导不支持文件备份。</span><span class="sxs-lookup"><span data-stu-id="69053-165">File backups are not supported by the Maintenance Plan Wizard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69053-166">另请参阅</span><span class="sxs-lookup"><span data-stu-id="69053-166">See Also</span></span>  
 <span data-ttu-id="69053-167">[BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="69053-167">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="69053-168">[备份概述 (SQL Server)](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="69053-168">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 <span data-ttu-id="69053-169">[备份和还原：互操作性和共存 &#40;SQL Server&#41;](backup-and-restore-interoperability-and-coexistence-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="69053-169">[Backup and Restore: Interoperability and Coexistence &#40;SQL Server&#41;](backup-and-restore-interoperability-and-coexistence-sql-server.md) </span></span>  
 <span data-ttu-id="69053-170">[差异备份 (SQL Server)](differential-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="69053-170">[Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md) </span></span>  
 <span data-ttu-id="69053-171">[文件还原（简单恢复模式）](file-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="69053-171">[File Restores &#40;Simple Recovery Model&#41;](file-restores-simple-recovery-model.md) </span></span>  
 <span data-ttu-id="69053-172">[文件还原（完整恢复模式）](file-restores-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="69053-172">[File Restores &#40;Full Recovery Model&#41;](file-restores-full-recovery-model.md) </span></span>  
 <span data-ttu-id="69053-173">[联机还原 (SQL Server)](online-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="69053-173">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span></span>  
 [<span data-ttu-id="69053-174">段落还原 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="69053-174">Piecemeal Restores &#40;SQL Server&#41;</span></span>](piecemeal-restores-sql-server.md)  
  
  
