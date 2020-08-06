---
title: 备份概述 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- tables [SQL Server], backing up data
- backups [SQL Server]
- database backups [SQL Server]
- backup types [SQL Server]
- data backups [SQL Server]
- backing up tables [SQL Server]
- database restores [SQL Server], backups
- backing up [SQL Server], about backing up
- restoring [SQL Server], backup types
- backups [SQL Server], about
- backups [SQL Server], table-level backups unsupported
ms.assetid: 09a6e0c2-d8fd-453f-9aac-4ff24a97dc1f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 60fbd0341c4e29c6f98cc4d5fe5a2cfabc9b703f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591427"
---
# <a name="backup-overview-sql-server"></a><span data-ttu-id="52b9e-102">Backup Overview (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="52b9e-102">Backup Overview (SQL Server)</span></span>
  <span data-ttu-id="52b9e-103">本主题介绍 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 备份组件。</span><span class="sxs-lookup"><span data-stu-id="52b9e-103">This topic introduces the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup component.</span></span> <span data-ttu-id="52b9e-104">备份 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库对于保护您的数据至关重要。</span><span class="sxs-lookup"><span data-stu-id="52b9e-104">Backing up your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database is essential for protecting your data.</span></span> <span data-ttu-id="52b9e-105">本讨论涵盖了备份类型和备份限制。</span><span class="sxs-lookup"><span data-stu-id="52b9e-105">This discussion covers backup types, and backup restrictions.</span></span> <span data-ttu-id="52b9e-106">该主题还介绍了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 备份设备和备份介质。</span><span class="sxs-lookup"><span data-stu-id="52b9e-106">The topic also introduces [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup devices and backup media.</span></span>  
  
 <span data-ttu-id="52b9e-107">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="52b9e-107">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="52b9e-108">组件和概念</span><span class="sxs-lookup"><span data-stu-id="52b9e-108">Components and Concepts</span></span>](#TermsAndDefinitions)  
  
-   [<span data-ttu-id="52b9e-109">备份压缩</span><span class="sxs-lookup"><span data-stu-id="52b9e-109">Backup Compression</span></span>](#BackupCompression)  
  
-   [<span data-ttu-id="52b9e-110">SQL Server 中备份操作的限制</span><span class="sxs-lookup"><span data-stu-id="52b9e-110">Restrictions on Backup Operations in SQL Server</span></span>](#Restrictions)  
  
-   [<span data-ttu-id="52b9e-111">相关任务</span><span class="sxs-lookup"><span data-stu-id="52b9e-111">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="components-and-concepts"></a><a name="TermsAndDefinitions"></a> <span data-ttu-id="52b9e-112">组件和概念</span><span class="sxs-lookup"><span data-stu-id="52b9e-112">Components and Concepts</span></span>  
 <span data-ttu-id="52b9e-113">备份 [动词] (back up)</span><span class="sxs-lookup"><span data-stu-id="52b9e-113">back up [verb]</span></span>  
 <span data-ttu-id="52b9e-114">从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库或其事务日志中将数据或日志记录复制到备份设备（如磁盘），以创建数据备份或日志备份。</span><span class="sxs-lookup"><span data-stu-id="52b9e-114">Copies the data or log records from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database or its transaction log to a backup device, such as a disk, to create a data backup or log backup.</span></span>  
  
 <span data-ttu-id="52b9e-115">备份 [名词] (backup)</span><span class="sxs-lookup"><span data-stu-id="52b9e-115">backup [noun]</span></span>  
 <span data-ttu-id="52b9e-116">可用于在失败后还原或恢复数据的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据副本。</span><span class="sxs-lookup"><span data-stu-id="52b9e-116">A copy of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data that can be used to restore and recover the data after a failure.</span></span> <span data-ttu-id="52b9e-117">在数据库级别以及针对数据库的一个或多个文件或文件组创建 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据的备份。</span><span class="sxs-lookup"><span data-stu-id="52b9e-117">A backup of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data is created at the level of a database or one or more of its files or filegroups.</span></span> <span data-ttu-id="52b9e-118">不能创建表级备份。</span><span class="sxs-lookup"><span data-stu-id="52b9e-118">Table-level backups cannot be created.</span></span> <span data-ttu-id="52b9e-119">除了数据备份之外，完整恢复模式要求创建事务日志的备份。</span><span class="sxs-lookup"><span data-stu-id="52b9e-119">In addition to data backups, the full recovery model requires creating backups of the transaction log.</span></span>  
  
 [<span data-ttu-id="52b9e-120">恢复模式</span><span class="sxs-lookup"><span data-stu-id="52b9e-120">recovery model</span></span>](recovery-models-sql-server.md)  
 <span data-ttu-id="52b9e-121">用于控制数据库上的事务日志维护的数据库属性。</span><span class="sxs-lookup"><span data-stu-id="52b9e-121">A database property that controls transaction log maintenance on a database.</span></span> <span data-ttu-id="52b9e-122">有三种恢复模式：简单恢复模式、完整恢复模式和大容量日志恢复模式。</span><span class="sxs-lookup"><span data-stu-id="52b9e-122">Three recovery models exist: simple, full, and bulk-logged.</span></span> <span data-ttu-id="52b9e-123">数据库的恢复模式确定其备份和还原要求。</span><span class="sxs-lookup"><span data-stu-id="52b9e-123">The recovery model of database determines its backup and restore requirements.</span></span>  
  
 [<span data-ttu-id="52b9e-124">还原 (restore)</span><span class="sxs-lookup"><span data-stu-id="52b9e-124">restore</span></span>](restore-and-recovery-overview-sql-server.md)  
 <span data-ttu-id="52b9e-125">一种包括多个阶段的过程，用于将指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 备份中的所有数据和日志页复制到指定数据库，然后通过应用记录的更改使该数据在时间上向前移动，以前滚备份中记录的所有事务。</span><span class="sxs-lookup"><span data-stu-id="52b9e-125">A multi-phase process that copies all the data and log pages from a specified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup to a specified database, and then rolls forward all the transactions that are logged in the backup by applying logged changes to bring the data forward in time.</span></span>  
  
 <span data-ttu-id="52b9e-126">**备份类型**</span><span class="sxs-lookup"><span data-stu-id="52b9e-126">**Types of Backups**</span></span>  
  
 [<span data-ttu-id="52b9e-127">仅复制备份 (copy-only backup)</span><span class="sxs-lookup"><span data-stu-id="52b9e-127">copy-only backup</span></span>](copy-only-backups-sql-server.md)  
 <span data-ttu-id="52b9e-128">独立于正常 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 备份序列的特殊用途备份。</span><span class="sxs-lookup"><span data-stu-id="52b9e-128">A special-use backup that is independent of the regular sequence of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backups.</span></span>  
  
 <span data-ttu-id="52b9e-129">数据备份 (data backup)</span><span class="sxs-lookup"><span data-stu-id="52b9e-129">data backup</span></span>  
 <span data-ttu-id="52b9e-130">完整数据库的数据备份（数据库备份）、部分数据库的数据备份（部分备份）或一组数据文件或文件组的数据备份（文件备份）。</span><span class="sxs-lookup"><span data-stu-id="52b9e-130">A backup of data in a complete database (a database backup), a partial database (a partial backup), or a set of data files or filegroups (a file backup).</span></span>  
  
 [<span data-ttu-id="52b9e-131">数据库备份 (database backup)</span><span class="sxs-lookup"><span data-stu-id="52b9e-131">database backup</span></span>](full-database-backups-sql-server.md)  
 <span data-ttu-id="52b9e-132">数据库的备份。</span><span class="sxs-lookup"><span data-stu-id="52b9e-132">A backup of a database.</span></span> <span data-ttu-id="52b9e-133">完整数据库备份表示备份完成时的整个数据库。</span><span class="sxs-lookup"><span data-stu-id="52b9e-133">Full database backups represent the whole database at the time the backup finished.</span></span> <span data-ttu-id="52b9e-134">差异数据库备份只包含自最近完整备份以来对数据库所做的更改。</span><span class="sxs-lookup"><span data-stu-id="52b9e-134">Differential database backups contain only changes made to the database since its most recent full database backup.</span></span>  
  
 [<span data-ttu-id="52b9e-135">差异备份 (differential backup)</span><span class="sxs-lookup"><span data-stu-id="52b9e-135">differential backup</span></span>](full-database-backups-sql-server.md)  
 <span data-ttu-id="52b9e-136">基于完整数据库或部分数据库以及一组数据文件或文件组的最新完整备份的数据备份（差异基准），仅包含自差异基准以来发生了更改的数据区。</span><span class="sxs-lookup"><span data-stu-id="52b9e-136">A data backup that is based on the latest full backup of a complete or partial database or a set of data files or filegroups (the *differential base*) and that contains only the data extents that have changed since the differential base.</span></span>  
  
 <span data-ttu-id="52b9e-137">部分差异备份仅记录自上一次部分备份（称为“差异基准”）以来文件组中发生更改的数据区。</span><span class="sxs-lookup"><span data-stu-id="52b9e-137">A differential partial backup records only the data extents that have changed in the filegroups since the previous partial backup, known as the base for the differential.</span></span>  
  
 <span data-ttu-id="52b9e-138">完整备份 (full backup)</span><span class="sxs-lookup"><span data-stu-id="52b9e-138">full backup</span></span>  
 <span data-ttu-id="52b9e-139">一种数据备份，包含特定数据库或者一组特定的文件组或文件中的所有数据，以及可以恢复这些数据的足够的日志。</span><span class="sxs-lookup"><span data-stu-id="52b9e-139">A data backup that contains all the data in a specific database or set of filegroups or files, and also enough log to allow for recovering that data.</span></span>  
  
 [<span data-ttu-id="52b9e-140">日志备份 (log backup)</span><span class="sxs-lookup"><span data-stu-id="52b9e-140">log backup</span></span>](transaction-log-backups-sql-server.md)  
 <span data-ttu-id="52b9e-141">包括以前日志备份中未备份的所有日志记录的事务日志备份。</span><span class="sxs-lookup"><span data-stu-id="52b9e-141">A backup of transaction logs that includes all log records that were not backed up in a previous log backup.</span></span> <span data-ttu-id="52b9e-142">（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="52b9e-142">(full recovery model)</span></span>  
  
 [<span data-ttu-id="52b9e-143">文件备份 (file backup)</span><span class="sxs-lookup"><span data-stu-id="52b9e-143">file backup</span></span>](full-file-backups-sql-server.md)  
 <span data-ttu-id="52b9e-144">一个或多个数据库文件或文件组的备份。</span><span class="sxs-lookup"><span data-stu-id="52b9e-144">A backup of one or more database files or filegroups.</span></span>  
  
 [<span data-ttu-id="52b9e-145">部分备份 (partial backup)</span><span class="sxs-lookup"><span data-stu-id="52b9e-145">partial backup</span></span>](partial-backups-sql-server.md)  
 <span data-ttu-id="52b9e-146">仅包含数据库中部分文件组的数据（包含主要文件组、每个读/写文件组以及任何可选指定的只读文件中的数据）。</span><span class="sxs-lookup"><span data-stu-id="52b9e-146">Contains data from only some of the filegroups in a database, including the data in the primary filegroup, every read/write filegroup, and any optionally-specified read-only files.</span></span>  
  
 <span data-ttu-id="52b9e-147">**备份媒体术语和定义**</span><span class="sxs-lookup"><span data-stu-id="52b9e-147">**Backup Media Terms and Definitions**</span></span>  
  
 [<span data-ttu-id="52b9e-148">备份设备 (backup device)</span><span class="sxs-lookup"><span data-stu-id="52b9e-148">backup device</span></span>](backup-devices-sql-server.md)  
 <span data-ttu-id="52b9e-149">要将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 备份写入其中以及可从其中还原的磁盘或磁带设备。</span><span class="sxs-lookup"><span data-stu-id="52b9e-149">A disk or tape device to which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backups are written and from which they can be restored.</span></span> <span data-ttu-id="52b9e-150">SQL Server 备份也可以写入 Azure Blob 存储服务，并且使用 URL 格式来指定备份文件的目标和名称。</span><span class="sxs-lookup"><span data-stu-id="52b9e-150">SQL Server backups can also be written to an Azure Blob storage service, and **URL** format is used to specify the destination and the name of the backup file..</span></span> <span data-ttu-id="52b9e-151">有关详细信息，请参阅[使用 Azure Blob 存储服务执行 SQL Server 备份和还原](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)。</span><span class="sxs-lookup"><span data-stu-id="52b9e-151">For more information, see [SQL Server Backup and Restore with Azure Blob Storage Service](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).</span></span>  
  
 [<span data-ttu-id="52b9e-152">备份介质</span><span class="sxs-lookup"><span data-stu-id="52b9e-152">backup media</span></span>](media-sets-media-families-and-backup-sets-sql-server.md)  
 <span data-ttu-id="52b9e-153">已写入一个或多个备份的一个或多个磁带或磁盘文件。</span><span class="sxs-lookup"><span data-stu-id="52b9e-153">One or more tapes or disk files to which one or more backup have been written.</span></span>  
  
 [<span data-ttu-id="52b9e-154">备份集 (backup set)</span><span class="sxs-lookup"><span data-stu-id="52b9e-154">backup set</span></span>](media-sets-media-families-and-backup-sets-sql-server.md)  
 <span data-ttu-id="52b9e-155">通过成功的备份操作添加到介质组的备份内容。</span><span class="sxs-lookup"><span data-stu-id="52b9e-155">The backup content that is added to a media set by a successful backup operation.</span></span>  
  
 [<span data-ttu-id="52b9e-156">介质簇 (media family)</span><span class="sxs-lookup"><span data-stu-id="52b9e-156">media family</span></span>](media-sets-media-families-and-backup-sets-sql-server.md)  
 <span data-ttu-id="52b9e-157">在介质集中的单个非镜像设备或一组镜像设备上创建的备份。</span><span class="sxs-lookup"><span data-stu-id="52b9e-157">Backups created on a single nonmirrored device or a set of mirrored devices in a media set</span></span>  
  
 [<span data-ttu-id="52b9e-158">介质集 (media set)</span><span class="sxs-lookup"><span data-stu-id="52b9e-158">media set</span></span>](media-sets-media-families-and-backup-sets-sql-server.md)  
 <span data-ttu-id="52b9e-159">备份介质（磁带或磁盘文件）的有序集合，使用固定类型和数量的备份设备向其写入了一个或多个备份操作。</span><span class="sxs-lookup"><span data-stu-id="52b9e-159">An ordered collection of backup media, tapes or disk files, to which one or more backup operations have written using a fixed type and number of backup devices.</span></span>  
  
 [<span data-ttu-id="52b9e-160">镜像介质集 (mirrored media set)</span><span class="sxs-lookup"><span data-stu-id="52b9e-160">mirrored media set</span></span>](mirrored-backup-media-sets-sql-server.md)  
 <span data-ttu-id="52b9e-161">介质集的多个副本（镜像）。</span><span class="sxs-lookup"><span data-stu-id="52b9e-161">Multiple copies (mirrors) of a media set.</span></span>  
  
##  <a name="backup-compression"></a><a name="BackupCompression"></a><span data-ttu-id="52b9e-162">备份压缩</span><span class="sxs-lookup"><span data-stu-id="52b9e-162">Backup Compression</span></span>  
 [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] <span data-ttu-id="52b9e-163">及更高版本支持压缩备份，并且 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 及更高版本可以还原压缩后的备份。</span><span class="sxs-lookup"><span data-stu-id="52b9e-163">and later versions support compressing backups, and [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and later versions can restore a compressed backup.</span></span> <span data-ttu-id="52b9e-164">有关详细信息，请参阅[备份压缩 (SQL Server)](backup-compression-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="52b9e-164">For more information, see [Backup Compression &#40;SQL Server&#41;](backup-compression-sql-server.md).</span></span>  
  
##  <a name="restrictions-on-backup-operations-in-sql-server"></a><a name="Restrictions"></a><span data-ttu-id="52b9e-165">SQL Server 中的备份操作的限制</span><span class="sxs-lookup"><span data-stu-id="52b9e-165">Restrictions on Backup Operations in SQL Server</span></span>  
 <span data-ttu-id="52b9e-166">可以在数据库在线并且正在使用时进行备份。</span><span class="sxs-lookup"><span data-stu-id="52b9e-166">Backup can occur while the database is online and being used.</span></span> <span data-ttu-id="52b9e-167">但是，存在下列限制。</span><span class="sxs-lookup"><span data-stu-id="52b9e-167">However, the following restrictions exist.</span></span>  
  
### <a name="offline-data-cannot-be-backed-up"></a><span data-ttu-id="52b9e-168">无法备份脱机数据</span><span class="sxs-lookup"><span data-stu-id="52b9e-168">Offline Data Cannot Be Backed Up</span></span>  
 <span data-ttu-id="52b9e-169">隐式或显式引用脱机数据的任何备份操作都会失败。</span><span class="sxs-lookup"><span data-stu-id="52b9e-169">Any backup operation that implicitly or explicitly references data that is offline fails.</span></span> <span data-ttu-id="52b9e-170">一些典型示例包括：</span><span class="sxs-lookup"><span data-stu-id="52b9e-170">Some typical examples include the following:</span></span>  
  
-   <span data-ttu-id="52b9e-171">您请求完整数据库备份，但是数据库的一个文件组脱机。</span><span class="sxs-lookup"><span data-stu-id="52b9e-171">You request a full database backup, but one filegroup of the database is offline.</span></span> <span data-ttu-id="52b9e-172">由于所有文件组都隐式包含在完整数据库备份中，因此，此操作将会失败。</span><span class="sxs-lookup"><span data-stu-id="52b9e-172">Because all filegroups are implicitly included in a full database backup, this operation fails.</span></span>  
  
     <span data-ttu-id="52b9e-173">若要备份此数据库，可以使用文件备份并仅指定联机的文件组。</span><span class="sxs-lookup"><span data-stu-id="52b9e-173">To back up this database, you can use a file backup and specify only the filegroups that are online.</span></span>  
  
-   <span data-ttu-id="52b9e-174">请求部分备份，但是有一个读/写文件组处于脱机状态。</span><span class="sxs-lookup"><span data-stu-id="52b9e-174">You request a partial backup, but a read/write filegroup is offline.</span></span> <span data-ttu-id="52b9e-175">由于部分备份需要使用所有读/写文件组，因此该操作失败。</span><span class="sxs-lookup"><span data-stu-id="52b9e-175">Because all read/write filegroups are required for a partial backup, the operation fails.</span></span>  
  
-   <span data-ttu-id="52b9e-176">请求特定文件的文件备份，但是其中有一个文件处于脱机状态。</span><span class="sxs-lookup"><span data-stu-id="52b9e-176">You request a file backup of specific files, but one of the files is not online.</span></span> <span data-ttu-id="52b9e-177">该操作失败。</span><span class="sxs-lookup"><span data-stu-id="52b9e-177">The operation fails.</span></span> <span data-ttu-id="52b9e-178">若要备份联机文件，可以省略文件列表中的脱机文件并重复该操作。</span><span class="sxs-lookup"><span data-stu-id="52b9e-178">To back up the online files, you can omit the offline file from the file list and repeat the operation.</span></span>  
  
 <span data-ttu-id="52b9e-179">通常，即使一个或多个数据文件不可用，日志备份也会成功。</span><span class="sxs-lookup"><span data-stu-id="52b9e-179">Typically, a log backup succeeds even if one or more data files are unavailable.</span></span> <span data-ttu-id="52b9e-180">但如果某个文件包含大容量日志恢复模式下所做的大容量日志更改，则所有文件都必须都处于联机状态才能成功备份。</span><span class="sxs-lookup"><span data-stu-id="52b9e-180">However, if any file contains bulk-logged changes made under the bulk-logged recovery model, all the files must be online for the backup to succeed.</span></span>  
  
### <a name="concurrency-restrictions-during-backup"></a><span data-ttu-id="52b9e-181">备份过程中的并发限制</span><span class="sxs-lookup"><span data-stu-id="52b9e-181">Concurrency Restrictions During Backup</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="52b9e-182">可以使用联机备份过程来备份数据库。</span><span class="sxs-lookup"><span data-stu-id="52b9e-182">uses an online backup process to allow for a database backup while the database is still being used.</span></span> <span data-ttu-id="52b9e-183">在备份过程中，可以进行多个操作；例如：在执行备份操作期间允许使用 INSERT、UPDATE 或 DELETE 语句。</span><span class="sxs-lookup"><span data-stu-id="52b9e-183">During a backup, most operations are possible; for example, INSERT, UPDATE, or DELETE statements are allowed during a backup operation.</span></span> <span data-ttu-id="52b9e-184">但是，如果在正在创建或删除数据库文件时尝试启动备份操作，则备份操作将等待，直到创建或删除操作完成或者备份超时。</span><span class="sxs-lookup"><span data-stu-id="52b9e-184">However, if you try to start a backup operation while a database file is being created or deleted, the backup operation waits until the create or delete operation is finished or the backup times out.</span></span>  
  
 <span data-ttu-id="52b9e-185">在数据库备份或事务日志备份的过程中无法执行的操作包括：</span><span class="sxs-lookup"><span data-stu-id="52b9e-185">Operations that cannot run during a database backup or transaction log backup include the following:</span></span>  
  
-   <span data-ttu-id="52b9e-186">文件管理操作，如含有 ADD FILE 或 REMOVE FILE 选项的 ALTER DATABASE 语句。</span><span class="sxs-lookup"><span data-stu-id="52b9e-186">File-management operations such as the ALTER DATABASE statement with either the ADD FILE or REMOVE FILE options.</span></span>  
  
-   <span data-ttu-id="52b9e-187">收缩数据库或文件操作。</span><span class="sxs-lookup"><span data-stu-id="52b9e-187">Shrink database or shrink file operations.</span></span> <span data-ttu-id="52b9e-188">这包括自动收缩操作。</span><span class="sxs-lookup"><span data-stu-id="52b9e-188">This includes auto-shrink operations.</span></span>  
  
-   <span data-ttu-id="52b9e-189">如果在进行备份操作时尝试创建或删除数据库文件，则创建或删除操作将失败。</span><span class="sxs-lookup"><span data-stu-id="52b9e-189">If you try to create or delete a database file while a backup operation is in progress, the create or delete operation fails.</span></span>  
  
 <span data-ttu-id="52b9e-190">如果备份操作与文件管理操作或收缩操作重叠，则产生冲突。</span><span class="sxs-lookup"><span data-stu-id="52b9e-190">If a backup operation overlaps with a file-management operation or shrink operation, a conflict occurs.</span></span> <span data-ttu-id="52b9e-191">无论哪个冲突操作首先开始，第二个操作总会等待第一个操作设置的锁超时。（超时期限由会话超时设置控制。）如果在超时期限内释放锁，第二个操作将继续执行。</span><span class="sxs-lookup"><span data-stu-id="52b9e-191">Regardless of which of the conflicting operation began first, the second operation waits for the lock set by the first operation to time out. (The time-out period is controlled by a session time-out setting.) If the lock is released during the time-out period, the second operation continues.</span></span> <span data-ttu-id="52b9e-192">如果锁超时，则第二个操作失败。</span><span class="sxs-lookup"><span data-stu-id="52b9e-192">If the lock times out, the second operation fails.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="52b9e-193">相关任务</span><span class="sxs-lookup"><span data-stu-id="52b9e-193">Related Tasks</span></span>  
 <span data-ttu-id="52b9e-194">**使用备份设备和备份介质**</span><span class="sxs-lookup"><span data-stu-id="52b9e-194">**To work with backup devices and backup media**</span></span>  
  
-   [<span data-ttu-id="52b9e-195">为磁盘文件定义逻辑备份设备 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="52b9e-195">Define a Logical Backup Device for a Disk File &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-disk-file-sql-server.md)  
  
-   [<span data-ttu-id="52b9e-196">为磁带驱动器定义逻辑备份设备 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="52b9e-196">Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
-   [<span data-ttu-id="52b9e-197">将磁盘或磁带指定为备份目标 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="52b9e-197">Specify a Disk or Tape As a Backup Destination &#40;SQL Server&#41;</span></span>](specify-a-disk-or-tape-as-a-backup-destination-sql-server.md)  
  
-   [<span data-ttu-id="52b9e-198">删除备份设备 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="52b9e-198">Delete a Backup Device &#40;SQL Server&#41;</span></span>](delete-a-backup-device-sql-server.md)  
  
-   [<span data-ttu-id="52b9e-199">设置备份的过期日期 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="52b9e-199">Set the Expiration Date on a Backup &#40;SQL Server&#41;</span></span>](set-the-expiration-date-on-a-backup-sql-server.md)  
  
-   [<span data-ttu-id="52b9e-200">查看备份磁带或文件的内容 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="52b9e-200">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [<span data-ttu-id="52b9e-201">查看备份集中的数据文件和日志文件 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="52b9e-201">View the Data and Log Files in a Backup Set &#40;SQL Server&#41;</span></span>](view-the-data-and-log-files-in-a-backup-set-sql-server.md)  
  
-   [<span data-ttu-id="52b9e-202">查看逻辑备份设备的属性和内容 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="52b9e-202">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
-   [<span data-ttu-id="52b9e-203">从设备还原备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="52b9e-203">Restore a Backup from a Device &#40;SQL Server&#41;</span></span>](restore-a-backup-from-a-device-sql-server.md)  
  
-   [<span data-ttu-id="52b9e-204">教程：将 SQL Server 备份和还原到 Azure Blob 存储服务</span><span class="sxs-lookup"><span data-stu-id="52b9e-204">Tutorial: SQL Server Backup and Restore to Azure Blob Storage Service</span></span>](../tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md)  
  
 <span data-ttu-id="52b9e-205">**创建备份**</span><span class="sxs-lookup"><span data-stu-id="52b9e-205">**To create a backup**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="52b9e-206">对于部分备份或仅复制备份，必须分别使用带 PARTIAL 或 COPY_ONLY 选项的 [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](/sql/t-sql/statements/backup-transact-sql) 语句。</span><span class="sxs-lookup"><span data-stu-id="52b9e-206">For partial or copy-only backups, you must use the [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](/sql/t-sql/statements/backup-transact-sql) statement with the PARTIAL or COPY_ONLY option, respectively.</span></span>  
  
-   [<span data-ttu-id="52b9e-207">创建完整数据库备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="52b9e-207">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="52b9e-208">备份事务日志 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="52b9e-208">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](back-up-a-transaction-log-sql-server.md)  
  
-   [<span data-ttu-id="52b9e-209">备份文件和文件组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="52b9e-209">Back Up Files and Filegroups &#40;SQL Server&#41;</span></span>](back-up-files-and-filegroups-sql-server.md)  
  
-   [<span data-ttu-id="52b9e-210">创建差异数据库备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="52b9e-210">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](create-a-differential-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="52b9e-211">在数据库损坏时备份事务日志 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="52b9e-211">Back Up the Transaction Log When the Database Is Damaged &#40;SQL Server&#41;</span></span>](back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md)  
  
-   [<span data-ttu-id="52b9e-212">在备份或还原期间启用或禁用备份校验和 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="52b9e-212">Enable or Disable Backup Checksums During Backup or Restore &#40;SQL Server&#41;</span></span>](enable-or-disable-backup-checksums-during-backup-or-restore-sql-server.md)  
  
-   [<span data-ttu-id="52b9e-213">指定备份或还原操作在遇到错误后是继续还是停止 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="52b9e-213">Specify Whether a Backup or Restore Operation Continues or Stops After Encountering an Error &#40;SQL Server&#41;</span></span>](specify-if-backup-or-restore-continues-or-stops-after-error.md)  
  
-   [<span data-ttu-id="52b9e-214">使用资源调控器限制备份压缩的 CPU 使用量 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="52b9e-214">Use Resource Governor to Limit CPU Usage by Backup Compression &#40;Transact-SQL&#41;</span></span>](use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md)  
  
-   [<span data-ttu-id="52b9e-215">教程：将 SQL Server 备份和还原到 Azure Blob 存储服务</span><span class="sxs-lookup"><span data-stu-id="52b9e-215">Tutorial: SQL Server Backup and Restore to Azure Blob Storage Service</span></span>](../tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md)  
  
## <a name="see-also"></a><span data-ttu-id="52b9e-216">另请参阅</span><span class="sxs-lookup"><span data-stu-id="52b9e-216">See Also</span></span>  
 <span data-ttu-id="52b9e-217">[SQL Server 数据库的备份和还原](back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="52b9e-217">[Back Up and Restore of SQL Server Databases](back-up-and-restore-of-sql-server-databases.md) </span></span>  
 <span data-ttu-id="52b9e-218">[还原和恢复概述 (SQL Server)](restore-and-recovery-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="52b9e-218">[Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span></span>  
 <span data-ttu-id="52b9e-219">[维护计划](../maintenance-plans/maintenance-plans.md) </span><span class="sxs-lookup"><span data-stu-id="52b9e-219">[Maintenance Plans](../maintenance-plans/maintenance-plans.md) </span></span>  
 <span data-ttu-id="52b9e-220">[事务日志 (SQL Server)](../logs/the-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="52b9e-220">[The Transaction Log &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md) </span></span>  
 [<span data-ttu-id="52b9e-221">恢复模式 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="52b9e-221">Recovery Models &#40;SQL Server&#41;</span></span>](recovery-models-sql-server.md)  
  
  
