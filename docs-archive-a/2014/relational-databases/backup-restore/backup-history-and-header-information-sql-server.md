---
title: 备份历史记录和标头信息 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backup headers [SQL Server]
- history tables [SQL Server]
- file restores [SQL Server], status information
- backup sets [SQL Server], status information
- listing backed up databases
- status information [SQL Server], backups
- backing up [SQL Server], viewing backup sets
- restoring [SQL Server], history tables
- restoring databases [SQL Server], status information
- backups [SQL Server], status information
- headers [SQL Server]
- media headers [SQL Server]
- backup history tables [SQL Server]
- viewing backup information
- restoring files [SQL Server], viewing backup information
- restoring databases [SQL Server], history tables
- displaying backup information
- restoring files [SQL Server], status information
- historical information [SQL Server], backups
- database restores [SQL Server], history tables
- restore history tables [SQL Server]
- listing backed up files
ms.assetid: 799b9934-0ec2-4f43-960b-5c9653f18374
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ff1e75cc88e51de75af32bcd9d48860be52d5861
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694499"
---
# <a name="backup-history-and-header-information-sql-server"></a><span data-ttu-id="20426-102">备份历史记录和标头信息 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="20426-102">Backup History and Header Information (SQL Server)</span></span>
  <span data-ttu-id="20426-103">服务器实例上所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 备份和还原操作的完整历史记录存储在 **msdb** 数据库中。</span><span class="sxs-lookup"><span data-stu-id="20426-103">A complete history of all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup and restore operations on a server instance is stored in the **msdb** database.</span></span> <span data-ttu-id="20426-104">本主题介绍备份和还原历史记录表以及用于访问备份历史记录的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="20426-104">This topic introduces the backup and restore history tables and also the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that are used to access backup history.</span></span> <span data-ttu-id="20426-105">本主题还讨论何时列出数据库和事务日志文件有用，以及何时使用介质标头信息与何时使用备份标头信息的比较。</span><span class="sxs-lookup"><span data-stu-id="20426-105">The topic also discusses when listing database and transaction log files is useful and when to use media-header information compared to when to use backup-header information.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="20426-106">为了规避丢失对备份和还原历史记录的最新更改的风险，请经常备份 **msdb** 。</span><span class="sxs-lookup"><span data-stu-id="20426-106">To manage the risk of losing recent changes to your backup and restore history, back up **msdb** frequently.</span></span> <span data-ttu-id="20426-107">有关必须备份哪些系统数据库的信息，请参阅[备份和还原系统数据库 (SQL Server)](back-up-and-restore-of-system-databases-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="20426-107">For information about which of the system databases you must back up, see [Back Up and Restore of System Databases &#40;SQL Server&#41;](back-up-and-restore-of-system-databases-sql-server.md).</span></span>  
  
 <span data-ttu-id="20426-108">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="20426-108">**In This Topic:**</span></span>  
  
-   [<span data-ttu-id="20426-109">备份和还原历史记录表</span><span class="sxs-lookup"><span data-stu-id="20426-109">Backup and Restore History Tables</span></span>](#BnRHistoryTables)  
  
-   [<span data-ttu-id="20426-110">用于访问备份历史记录的 Transact-SQL 语句</span><span class="sxs-lookup"><span data-stu-id="20426-110">Transact-SQL Statements for Accessing Backup History</span></span>](#TsqlStatementsForBackupHistory)  
  
-   [<span data-ttu-id="20426-111">数据库和事务日志文件</span><span class="sxs-lookup"><span data-stu-id="20426-111">Database and Transaction Log Files</span></span>](#ListDbTlogFiles)  
  
-   [<span data-ttu-id="20426-112">介质标头信息</span><span class="sxs-lookup"><span data-stu-id="20426-112">Media-Header Information</span></span>](#MediaHeader)  
  
-   [<span data-ttu-id="20426-113">备份标头信息</span><span class="sxs-lookup"><span data-stu-id="20426-113">Backup-Header Information</span></span>](#BackupHeader)  
  
-   [<span data-ttu-id="20426-114">介质标头信息和备份标头信息的比较</span><span class="sxs-lookup"><span data-stu-id="20426-114">Comparison of Media-Header and Backup-Header Information</span></span>](#CompareMediaHeaderBackupHeader)  
  
-   [<span data-ttu-id="20426-115">验证备份</span><span class="sxs-lookup"><span data-stu-id="20426-115">Backup Verification</span></span>](#Verification)  
  
-   [<span data-ttu-id="20426-116">相关任务</span><span class="sxs-lookup"><span data-stu-id="20426-116">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="backup-and-restore-history-tables"></a><a name="BnRHistoryTables"></a> <span data-ttu-id="20426-117">备份和还原历史记录表</span><span class="sxs-lookup"><span data-stu-id="20426-117">Backup and Restore History Tables</span></span>  
 <span data-ttu-id="20426-118">本部分介绍 **msdb** 系统数据库中存储备份和还原元数据的历史记录表。</span><span class="sxs-lookup"><span data-stu-id="20426-118">This section introduces the history tables that store backup and restore metadata in the **msdb** system database.</span></span>  
  
|<span data-ttu-id="20426-119">历史记录表</span><span class="sxs-lookup"><span data-stu-id="20426-119">History table</span></span>|<span data-ttu-id="20426-120">说明</span><span class="sxs-lookup"><span data-stu-id="20426-120">Description</span></span>|  
|-------------------|-----------------|  
|[<span data-ttu-id="20426-121">backupfile</span><span class="sxs-lookup"><span data-stu-id="20426-121">backupfile</span></span>](/sql/relational-databases/system-tables/backupfile-transact-sql)|<span data-ttu-id="20426-122">每个备份的数据或日志文件在表中占一行。</span><span class="sxs-lookup"><span data-stu-id="20426-122">Contains one row for each data or log file that is backed up.</span></span>|  
|[<span data-ttu-id="20426-123">backupfilegroup</span><span class="sxs-lookup"><span data-stu-id="20426-123">backupfilegroup</span></span>](/sql/relational-databases/system-tables/backupfilegroup-transact-sql)|<span data-ttu-id="20426-124">备份集中的每个文件组在表中占一行。</span><span class="sxs-lookup"><span data-stu-id="20426-124">Contains a row for each filegroup in a backup set.</span></span>|  
|[<span data-ttu-id="20426-125">backupmediafamily</span><span class="sxs-lookup"><span data-stu-id="20426-125">backupmediafamily</span></span>](/sql/relational-databases/system-tables/backupmediafamily-transact-sql)|<span data-ttu-id="20426-126">每个介质簇在表中占一行。</span><span class="sxs-lookup"><span data-stu-id="20426-126">Contains one row for each media family.</span></span> <span data-ttu-id="20426-127">如果介质簇驻留在镜像介质集中，则对于介质集中的每个镜像，该介质簇都具有一个单独的行。</span><span class="sxs-lookup"><span data-stu-id="20426-127">If a media family resides in a mirrored media set, the family has a separate row for each mirror in the media set.</span></span>|  
|[<span data-ttu-id="20426-128">backupmediaset</span><span class="sxs-lookup"><span data-stu-id="20426-128">backupmediaset</span></span>](/sql/relational-databases/system-tables/backupmediaset-transact-sql)|<span data-ttu-id="20426-129">每个备份介质集在表中占一行。</span><span class="sxs-lookup"><span data-stu-id="20426-129">Contains one row for each backup media set.</span></span>|  
|[<span data-ttu-id="20426-130">backupset</span><span class="sxs-lookup"><span data-stu-id="20426-130">backupset</span></span>](/sql/relational-databases/system-tables/backupset-transact-sql)|<span data-ttu-id="20426-131">每个备份集在表中占一行。</span><span class="sxs-lookup"><span data-stu-id="20426-131">Contains a row for each backup set.</span></span>|  
|[<span data-ttu-id="20426-132">restorefile</span><span class="sxs-lookup"><span data-stu-id="20426-132">restorefile</span></span>](/sql/relational-databases/system-tables/restorefile-transact-sql)|<span data-ttu-id="20426-133">每个已还原的文件在表中占一行。</span><span class="sxs-lookup"><span data-stu-id="20426-133">Contains one row for each restored file.</span></span> <span data-ttu-id="20426-134">这包括按文件组名称间接还原的文件。</span><span class="sxs-lookup"><span data-stu-id="20426-134">This includes files restored indirectly by filegroup name.</span></span>|  
|[<span data-ttu-id="20426-135">restorefilegroup</span><span class="sxs-lookup"><span data-stu-id="20426-135">restorefilegroup</span></span>](/sql/relational-databases/system-tables/restorefilegroup-transact-sql)|<span data-ttu-id="20426-136">每个已还原的文件组在表中占一行。</span><span class="sxs-lookup"><span data-stu-id="20426-136">Contains one row for each restored filegroup.</span></span>|  
|[<span data-ttu-id="20426-137">restorehistory</span><span class="sxs-lookup"><span data-stu-id="20426-137">restorehistory</span></span>](/sql/relational-databases/system-tables/restorehistory-transact-sql)|<span data-ttu-id="20426-138">每个还原操作在表中占一行。</span><span class="sxs-lookup"><span data-stu-id="20426-138">Contains one row for each restore operation.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="20426-139">执行还原时，会修改备份历史记录表和还原历史记录表。</span><span class="sxs-lookup"><span data-stu-id="20426-139">When a restore is performed, backup history tables and restore history tables are modified.</span></span>  
  
##  <a name="transact-sql-statements-for-accessing-backup-history"></a><a name="TsqlStatementsForBackupHistory"></a> <span data-ttu-id="20426-140">用于访问备份历史记录的 Transact-SQL 语句</span><span class="sxs-lookup"><span data-stu-id="20426-140">Transact-SQL Statements for Accessing Backup History</span></span>  
 <span data-ttu-id="20426-141">还原信息语句与特定备份历史记录表中存储的信息存在对应关系。</span><span class="sxs-lookup"><span data-stu-id="20426-141">The restore information statements correspond with information stored in certain backup history tables.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="20426-142">RESTORE FILELISTONLY、RESTORE HEADERONLY、RESTORE LABELONLY 和 RESTORE VERIFYONLY Transact-SQL 语句需要 CREATE DATABASE 权限。</span><span class="sxs-lookup"><span data-stu-id="20426-142">The RESTORE FILELISTONLY, RESTORE HEADERONLY, RESTORE LABELONLY, and RESTORE VERIFYONLY Transact-SQL statements require CREATE DATABASE permission.</span></span> <span data-ttu-id="20426-143">与以前的版本相比，这项新要求为您的备份文件提高了安全性，并更周全地保护了您的备份信息。</span><span class="sxs-lookup"><span data-stu-id="20426-143">This requirement secures your backup files and protects your backup information more fully than in previous versions.</span></span> <span data-ttu-id="20426-144">有关此权限的信息，请参阅 [GRANT 数据库权限 (Transact-SQL)](/sql/t-sql/statements/grant-database-permissions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="20426-144">For information about this permission, see [GRANT Database Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-permissions-transact-sql).</span></span>  
  
|<span data-ttu-id="20426-145">信息语句</span><span class="sxs-lookup"><span data-stu-id="20426-145">Information statement</span></span>|<span data-ttu-id="20426-146">备份历史记录表</span><span class="sxs-lookup"><span data-stu-id="20426-146">Backup history table</span></span>|<span data-ttu-id="20426-147">说明</span><span class="sxs-lookup"><span data-stu-id="20426-147">Description</span></span>|  
|---------------------------|--------------------------|-----------------|  
|[<span data-ttu-id="20426-148">RESTORE FILELISTONLY</span><span class="sxs-lookup"><span data-stu-id="20426-148">RESTORE FILELISTONLY</span></span>](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql)|[<span data-ttu-id="20426-149">backupfile</span><span class="sxs-lookup"><span data-stu-id="20426-149">backupfile</span></span>](/sql/relational-databases/system-tables/backupfile-transact-sql)|<span data-ttu-id="20426-150">返回一个结果集，其中包含一个列出了指定备份集中包含的数据库和日志文件的列表。</span><span class="sxs-lookup"><span data-stu-id="20426-150">Returns a result set that has a list of the database and log files that are contained in the specified backup set.</span></span><br /><br /> <span data-ttu-id="20426-151">有关详细信息，请参阅本主题后面的“列出数据库文件和事务日志文件”部分。</span><span class="sxs-lookup"><span data-stu-id="20426-151">For more information, see "Listing Database and Transaction Log Files," later in this topic.</span></span>|  
|[<span data-ttu-id="20426-152">RESTORE HEADERONLY</span><span class="sxs-lookup"><span data-stu-id="20426-152">RESTORE HEADERONLY</span></span>](/sql/t-sql/statements/restore-statements-headeronly-transact-sql)|[<span data-ttu-id="20426-153">backupset</span><span class="sxs-lookup"><span data-stu-id="20426-153">backupset</span></span>](/sql/relational-databases/system-tables/backupset-transact-sql)|<span data-ttu-id="20426-154">在特定的备份设备上检索所有备份集的所有备份标头信息。</span><span class="sxs-lookup"><span data-stu-id="20426-154">Retrieves all the backup header information for all backup sets on a particular backup device.</span></span> <span data-ttu-id="20426-155">执行 RESTORE HEADERONLY 的结果是一个结果集。</span><span class="sxs-lookup"><span data-stu-id="20426-155">The result from executing RESTORE HEADERONLY is a result set.</span></span><br /><br /> <span data-ttu-id="20426-156">有关详细信息，请参阅本主题后面的“查看备份标头信息”部分。</span><span class="sxs-lookup"><span data-stu-id="20426-156">For more information, see "Viewing the Backup-Header Information," later in this topic.</span></span>|  
|[<span data-ttu-id="20426-157">RESTORE LABELONLY</span><span class="sxs-lookup"><span data-stu-id="20426-157">RESTORE LABELONLY</span></span>](/sql/t-sql/statements/restore-statements-labelonly-transact-sql)|[<span data-ttu-id="20426-158">backupmediaset</span><span class="sxs-lookup"><span data-stu-id="20426-158">backupmediaset</span></span>](/sql/relational-databases/system-tables/backupmediaset-transact-sql)|<span data-ttu-id="20426-159">返回一个结果集，其中包含有关指定备份设备中的备份介质的信息。</span><span class="sxs-lookup"><span data-stu-id="20426-159">Returns a result set that contains information about the backup media on a specified backup device.</span></span><br /><br /> <span data-ttu-id="20426-160">有关详细信息，请参阅本主题后面的“查看介质标头信息”部分。</span><span class="sxs-lookup"><span data-stu-id="20426-160">For more information, see "Viewing the Media-Header Information," later in this topic.</span></span>|  
  
##  <a name="database-and-transaction-log-files"></a><a name="ListDbTlogFiles"></a> <span data-ttu-id="20426-161">数据库和事务日志文件</span><span class="sxs-lookup"><span data-stu-id="20426-161">Database and Transaction Log Files</span></span>  
 <span data-ttu-id="20426-162">列出备份中的数据库文件和事务日志文件时，显示的信息包括逻辑名称、物理名称、文件类型（数据库文件或日志文件）、文件组成员资格、文件大小（字节）、允许的文件最大大小和预定义的文件增长大小（字节）。</span><span class="sxs-lookup"><span data-stu-id="20426-162">Information that is displayed when the database and transaction log files are listed in a backup includes the logical name, physical name, file type (database or log), filegroup membership, file size (in bytes), the maximum allowed file size, and the predefined file growth size (in bytes).</span></span> <span data-ttu-id="20426-163">在下列情况下，这些信息对于在还原数据库备份之前确定数据库备份中文件的名称很有用：</span><span class="sxs-lookup"><span data-stu-id="20426-163">This information is useful, in the following situations, to determine the names of the files in a database backup before you restore the database backup:</span></span>  
  
-   <span data-ttu-id="20426-164">丢失了包含数据库中一个或多个文件的磁盘驱动器。</span><span class="sxs-lookup"><span data-stu-id="20426-164">You have lost a disk drive that contains one or more of the files for a database.</span></span>  
  
     <span data-ttu-id="20426-165">可以列出数据库备份中的文件以确定哪些文件受到影响，然后在还原整个数据库时将那些文件还原到另一个驱动器上，或者只还原那些文件并应用自进行数据库备份后创建的任何事务日志备份。</span><span class="sxs-lookup"><span data-stu-id="20426-165">You can list the files in the database backup to determine which files were affected, and then restore those files onto a different drive when you restore the whole database; or restore just those files and apply any transaction log backups created since the database was backed up.</span></span>  
  
-   <span data-ttu-id="20426-166">将数据库从一台服务器还原到另一台服务器上，但这台服务器上没有目录结构和驱动器映射。</span><span class="sxs-lookup"><span data-stu-id="20426-166">You are restoring a database from one server onto another server, but the directory structure and drive mapping does not exist on the server.</span></span>  
  
     <span data-ttu-id="20426-167">列出备份中的文件使您能够确定哪些文件受到影响。</span><span class="sxs-lookup"><span data-stu-id="20426-167">Listing the files in the backup let you determine which files are affected.</span></span> <span data-ttu-id="20426-168">例如，备份中包含必须还原到驱动器 E 的文件，而目标服务器没有驱动器 E。还原此文件时，必须将此文件重新定位至其他位置，例如驱动器 Z。</span><span class="sxs-lookup"><span data-stu-id="20426-168">For example, the backup contains a file that it has to restore to drive E, but the destination server does not have a drive E. The file must be relocated to another location, such as drive Z, when the file is restored.</span></span>  
  
##  <a name="media-header-information"></a><a name="MediaHeader"></a> <span data-ttu-id="20426-169">介质标头信息</span><span class="sxs-lookup"><span data-stu-id="20426-169">Media-Header Information</span></span>  
 <span data-ttu-id="20426-170">查看介质标头时显示有关介质本身的信息，而不显示有关介质上的备份的信息。</span><span class="sxs-lookup"><span data-stu-id="20426-170">Viewing the media header displays information about the media itself, instead of about the backups on the media.</span></span> <span data-ttu-id="20426-171">显示的介质标头信息包括介质名称、说明、创建介质标头的软件的名称以及介质标头的写入日期。</span><span class="sxs-lookup"><span data-stu-id="20426-171">Media header information that is displayed includes the media name, description, name of the software that created the media header, and the date the media header was written.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="20426-172">查看介质标头的速度很快。</span><span class="sxs-lookup"><span data-stu-id="20426-172">Viewing the media header is quick.</span></span>  
  
 <span data-ttu-id="20426-173">有关详细信息，请参阅本主题后面的 [介质标头信息和备份标头信息的比较](#CompareMediaHeaderBackupHeader)。</span><span class="sxs-lookup"><span data-stu-id="20426-173">For more information, see [Comparison of Media-Header and Backup-Header Information](#CompareMediaHeaderBackupHeader), later in this topic.</span></span>  
  
##  <a name="backup-header-information"></a><a name="BackupHeader"></a> <span data-ttu-id="20426-174">备份标头信息</span><span class="sxs-lookup"><span data-stu-id="20426-174">Backup-Header Information</span></span>  
 <span data-ttu-id="20426-175">查看备份标头时，将显示有关介质上的所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 备份集的信息。</span><span class="sxs-lookup"><span data-stu-id="20426-175">Viewing the backup header displays information about all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup sets on the media.</span></span> <span data-ttu-id="20426-176">显示的信息包括使用的备份设备类型、备份类型（数据库备份、事务备份、文件备份还是差异数据库备份）以及备份开始和停止的日期/时间。</span><span class="sxs-lookup"><span data-stu-id="20426-176">Information that is displayed includes the types of backup devices that are used, the types of backup (for example, database, transaction, file, or differential database), and backup start and stop date/time information.</span></span> <span data-ttu-id="20426-177">这些信息对确定还原磁带上的哪个备份集或确定介质上包含哪些备份很有用。</span><span class="sxs-lookup"><span data-stu-id="20426-177">This information is useful when you have to determine which backup set on the tape to restore, or the backups that are contained on the media.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="20426-178">查看备份标头信息时需要扫描整个介质以显示有关介质上每个备份的信息，因此对高容量磁带可能需要很长时间。</span><span class="sxs-lookup"><span data-stu-id="20426-178">Viewing backup header information can take a long time for high-capacity tapes, because the whole media must be scanned to display information about each backup on the media.</span></span>  
  
 <span data-ttu-id="20426-179">有关详细信息，请参阅本主题后面的 [介质标头信息和备份标头信息的比较](#CompareMediaHeaderBackupHeader)。</span><span class="sxs-lookup"><span data-stu-id="20426-179">For more information, see [Comparison of Media-Header and Backup-Header Information](#CompareMediaHeaderBackupHeader), later in this topic.</span></span>  
  
### <a name="which-backup-set-to-restore"></a><span data-ttu-id="20426-180">要还原的备份集</span><span class="sxs-lookup"><span data-stu-id="20426-180">Which Backup Set to Restore</span></span>  
 <span data-ttu-id="20426-181">可以使用备份标头中的信息来标识要还原的备份集。</span><span class="sxs-lookup"><span data-stu-id="20426-181">You can use information in the backup header to identify which backup set to restore.</span></span> <span data-ttu-id="20426-182">数据库引擎将对备份介质上的每个备份集进行编号。</span><span class="sxs-lookup"><span data-stu-id="20426-182">The Database Engine numbers each backup set on the backup media.</span></span> <span data-ttu-id="20426-183">这样，您就可以通过备份集在介质中的位置标识要还原的备份集。</span><span class="sxs-lookup"><span data-stu-id="20426-183">This lets you identify the backup set you want to restore by using its position on the media.</span></span> <span data-ttu-id="20426-184">例如，下面的介质包含三个备份集。</span><span class="sxs-lookup"><span data-stu-id="20426-184">For example, the following media contains three backup sets.</span></span>  
  
 <span data-ttu-id="20426-185">![包含 SQL Server 备份集的备份媒体](../../database-engine/media/bnr-media-backup-sets.gif "包含 SQL Server 备份集的备份媒体")</span><span class="sxs-lookup"><span data-stu-id="20426-185">![Backup media containing SQL Server backup sets](../../database-engine/media/bnr-media-backup-sets.gif "Backup media containing SQL Server backup sets")</span></span>  
  
 <span data-ttu-id="20426-186">若要还原特定的备份集，请指定要还原的备份集的位置编号。</span><span class="sxs-lookup"><span data-stu-id="20426-186">To restore a specific backup set, specify the position number of the backup set you want to restore.</span></span> <span data-ttu-id="20426-187">例如，若要还原第二个备份集，请指定 2 作为要还原的备份集。</span><span class="sxs-lookup"><span data-stu-id="20426-187">For example, to restore the second backup set, specify 2 as the backup set to restore.</span></span>  
  
##  <a name="comparison-of-media-header-and-backup-header-information"></a><a name="CompareMediaHeaderBackupHeader"></a> <span data-ttu-id="20426-188">介质标头信息和备份标头信息的比较</span><span class="sxs-lookup"><span data-stu-id="20426-188">Comparison of Media-Header and Backup-Header Information</span></span>  
 <span data-ttu-id="20426-189">可以下图为例了解备份标头和介质标头信息在查看方法上的区别。</span><span class="sxs-lookup"><span data-stu-id="20426-189">The following illustration provides an example of the differences between viewing backup-header and media-header information.</span></span> <span data-ttu-id="20426-190">获取介质标头信息只需要从磁带开头检索信息。</span><span class="sxs-lookup"><span data-stu-id="20426-190">Obtaining the media header requires retrieving information from only the start of the tape.</span></span> <span data-ttu-id="20426-191">获取备份标头信息则需要扫描整个磁带以查看每个备份集的标头。</span><span class="sxs-lookup"><span data-stu-id="20426-191">Obtaining the backup header requires scanning the whole tape to look at the header of every backup set.</span></span>  
  
 <span data-ttu-id="20426-192">![包含三个 SQL Server 备份集的媒体集](../../database-engine/media/bnr-media-label.gif "包含三个 SQL Server 备份集的媒体集")</span><span class="sxs-lookup"><span data-stu-id="20426-192">![Media set containing three SQL Server backup sets](../../database-engine/media/bnr-media-label.gif "Media set containing three SQL Server backup sets")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="20426-193">使用包含多个介质簇的介质集时，介质标头和备份集都写入所有介质簇中。</span><span class="sxs-lookup"><span data-stu-id="20426-193">When you use media sets that have multiple media families, the media header and backup set are written to all media families.</span></span> <span data-ttu-id="20426-194">因此，只需为这些报表操作提供单个介质簇即可。</span><span class="sxs-lookup"><span data-stu-id="20426-194">Therefore, you only have to provide a single media family for these reporting operations.</span></span>  
  
 <span data-ttu-id="20426-195">有关如何查看介质标头的信息，请参阅本主题前面的“查看介质标头信息”部分。</span><span class="sxs-lookup"><span data-stu-id="20426-195">For information about how to view the media-header, see "Viewing the Media-Header Information," earlier in this topic.</span></span>  
  
 <span data-ttu-id="20426-196">有关如何查看备份设备上所有备份集的备份标头信息的信息，请参阅本主题前面的“查看备份标头信息”。</span><span class="sxs-lookup"><span data-stu-id="20426-196">For information about how to view the backup header information for all backup sets on a backup device, see "Viewing the Backup-Header Information," earlier in this topic.</span></span>  
  
##  <a name="backup-verification"></a><a name="Verification"></a> <span data-ttu-id="20426-197">验证备份</span><span class="sxs-lookup"><span data-stu-id="20426-197">Backup Verification</span></span>  
 <span data-ttu-id="20426-198">尽管验证备份不是必需的，但却很有用。</span><span class="sxs-lookup"><span data-stu-id="20426-198">Although not required, verifying a backup is a useful practice.</span></span> <span data-ttu-id="20426-199">验证备份可以检查备份在物理上是否完好无损，以确保备份中的所有文件都是可读、可还原的，并且在您需要使用它时可以还原备份。</span><span class="sxs-lookup"><span data-stu-id="20426-199">Verifying a backup checks that the backup is intact physically, to ensure that all the files in the backup are readable and can be restored, and that you can restore your backup in the event you need to use it.</span></span> <span data-ttu-id="20426-200">了解验证备份时不会验证备份中数据的结构是非常重要的。</span><span class="sxs-lookup"><span data-stu-id="20426-200">It is important to understand that verifying a backup does not verify the structure of the data on the backup.</span></span> <span data-ttu-id="20426-201">但是，如果备份是使用 WITH CHECKSUMS 创建的，则使用 WITH CHECKSUMS 验证备份可以很好地表明备份中数据的可靠性。</span><span class="sxs-lookup"><span data-stu-id="20426-201">However, if the backup was created using WITH CHECKSUMS, verifying the backup using WITH CHECKSUMS can provide a good indication of the reliability of the data on the backup.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="20426-202">相关任务</span><span class="sxs-lookup"><span data-stu-id="20426-202">Related Tasks</span></span>  
 <span data-ttu-id="20426-203">**从备份中删除旧行并还原历史记录表**</span><span class="sxs-lookup"><span data-stu-id="20426-203">**To delete old rows from backup and restore history tables**</span></span>  
  
-   [<span data-ttu-id="20426-204">sp_delete_backuphistory (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="20426-204">sp_delete_backuphistory &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql)  
  
 <span data-ttu-id="20426-205">**从备份中删除特定数据库的所有行并还原历史记录表**</span><span class="sxs-lookup"><span data-stu-id="20426-205">**To delete all rows for a specific database from backup and restore history tables**</span></span>  
  
-   [<span data-ttu-id="20426-206">sp_delete_database_backuphistory (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="20426-206">sp_delete_database_backuphistory &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-delete-database-backuphistory-transact-sql)  
  
 <span data-ttu-id="20426-207">**查看备份集中的数据文件和日志文件**</span><span class="sxs-lookup"><span data-stu-id="20426-207">**To view the data and log files in a backup set**</span></span>  
  
-   [<span data-ttu-id="20426-208">RESTORE FILELISTONLY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="20426-208">RESTORE FILELISTONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql)  
  
-   <span data-ttu-id="20426-209"><xref:Microsoft.SqlServer.Management.Smo.Restore.ReadFileList%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="20426-209"><xref:Microsoft.SqlServer.Management.Smo.Restore.ReadFileList%2A> (SMO)</span></span>  
  
 <span data-ttu-id="20426-210">**查看介质标头信息**</span><span class="sxs-lookup"><span data-stu-id="20426-210">**To view media header information**</span></span>  
  
-   [<span data-ttu-id="20426-211">RESTORE LABELONLY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="20426-211">RESTORE LABELONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-labelonly-transact-sql)  
  
-   [<span data-ttu-id="20426-212">查看逻辑备份设备的属性和内容 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="20426-212">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
-   [<span data-ttu-id="20426-213">查看备份磁带或文件的内容 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="20426-213">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   <span data-ttu-id="20426-214"><xref:Microsoft.SqlServer.Management.Smo.Restore.ReadMediaHeader%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="20426-214"><xref:Microsoft.SqlServer.Management.Smo.Restore.ReadMediaHeader%2A> (SMO)</span></span>  
  
 <span data-ttu-id="20426-215">**查看备份标头信息**</span><span class="sxs-lookup"><span data-stu-id="20426-215">**To view backup header information**</span></span>  
  
-   [<span data-ttu-id="20426-216">RESTORE HEADERONLY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="20426-216">RESTORE HEADERONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-headeronly-transact-sql)  
  
-   [<span data-ttu-id="20426-217">查看备份磁带或文件的内容 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="20426-217">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [<span data-ttu-id="20426-218">查看逻辑备份设备的属性和内容 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="20426-218">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
-   <span data-ttu-id="20426-219"><xref:Microsoft.SqlServer.Management.Smo.Restore.ReadBackupHeader%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="20426-219"><xref:Microsoft.SqlServer.Management.Smo.Restore.ReadBackupHeader%2A> (SMO)</span></span>  
  
 <span data-ttu-id="20426-220">**从备份中删除旧行并还原历史记录表**</span><span class="sxs-lookup"><span data-stu-id="20426-220">**To delete old rows from backup and restore history tables**</span></span>  
  
-   [<span data-ttu-id="20426-221">sp_delete_backuphistory (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="20426-221">sp_delete_backuphistory &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql)  
  
 <span data-ttu-id="20426-222">**从备份中删除特定数据库的所有行并还原历史记录表**</span><span class="sxs-lookup"><span data-stu-id="20426-222">**To delete all rows for a specific database from backup and restore history tables**</span></span>  
  
-   [<span data-ttu-id="20426-223">sp_delete_database_backuphistory (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="20426-223">sp_delete_database_backuphistory &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-delete-database-backuphistory-transact-sql)  
  
 <span data-ttu-id="20426-224">**查看介质标头信息**</span><span class="sxs-lookup"><span data-stu-id="20426-224">**To view media header information**</span></span>  
  
-   [<span data-ttu-id="20426-225">RESTORE LABELONLY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="20426-225">RESTORE LABELONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-labelonly-transact-sql)  
  
-   [<span data-ttu-id="20426-226">查看逻辑备份设备的属性和内容 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="20426-226">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
-   [<span data-ttu-id="20426-227">查看备份磁带或文件的内容 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="20426-227">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   <span data-ttu-id="20426-228"><xref:Microsoft.SqlServer.Management.Smo.Restore.ReadMediaHeader%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="20426-228"><xref:Microsoft.SqlServer.Management.Smo.Restore.ReadMediaHeader%2A> (SMO)</span></span>  
  
 <span data-ttu-id="20426-229">**查看备份标头信息**</span><span class="sxs-lookup"><span data-stu-id="20426-229">**To view backup header information**</span></span>  
  
-   [<span data-ttu-id="20426-230">RESTORE HEADERONLY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="20426-230">RESTORE HEADERONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-headeronly-transact-sql)  
  
-   [<span data-ttu-id="20426-231">查看备份磁带或文件的内容 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="20426-231">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [<span data-ttu-id="20426-232">查看逻辑备份设备的属性和内容 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="20426-232">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
-   <span data-ttu-id="20426-233"><xref:Microsoft.SqlServer.Management.Smo.Restore.ReadBackupHeader%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="20426-233"><xref:Microsoft.SqlServer.Management.Smo.Restore.ReadBackupHeader%2A> (SMO)</span></span>  
  
 <span data-ttu-id="20426-234">**查看备份集中的文件**</span><span class="sxs-lookup"><span data-stu-id="20426-234">**To view the files in a backup set**</span></span>  
  
-   [<span data-ttu-id="20426-235">查看备份集中的数据文件和日志文件 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="20426-235">View the Data and Log Files in a Backup Set &#40;SQL Server&#41;</span></span>](view-the-data-and-log-files-in-a-backup-set-sql-server.md)  
  
-   [<span data-ttu-id="20426-236">RESTORE HEADERONLY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="20426-236">RESTORE HEADERONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-headeronly-transact-sql)  
  
 <span data-ttu-id="20426-237">**验证备份**</span><span class="sxs-lookup"><span data-stu-id="20426-237">**To verify a backup**</span></span>  
  
-   [<span data-ttu-id="20426-238">RESTORE VERIFYONLY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="20426-238">RESTORE VERIFYONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql)  
  
-   <span data-ttu-id="20426-239"><xref:Microsoft.SqlServer.Management.Smo.Restore.SqlVerify%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="20426-239"><xref:Microsoft.SqlServer.Management.Smo.Restore.SqlVerify%2A> (SMO)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20426-240">另请参阅</span><span class="sxs-lookup"><span data-stu-id="20426-240">See Also</span></span>  
 <span data-ttu-id="20426-241">[BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="20426-241">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="20426-242">[媒体集、媒体簇和备份集 (SQL Server)](media-sets-media-families-and-backup-sets-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="20426-242">[Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md) </span></span>  
 <span data-ttu-id="20426-243">[备份设备 (SQL Server)](backup-devices-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="20426-243">[Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md) </span></span>  
 <span data-ttu-id="20426-244">[镜像备份媒体集 (SQL Server)](mirrored-backup-media-sets-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="20426-244">[Mirrored Backup Media Sets &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md) </span></span>  
 [<span data-ttu-id="20426-245">备份和还原期间可能出现的媒体错误 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="20426-245">Possible Media Errors During Backup and Restore &#40;SQL Server&#41;</span></span>](possible-media-errors-during-backup-and-restore-sql-server.md)  
  
  
