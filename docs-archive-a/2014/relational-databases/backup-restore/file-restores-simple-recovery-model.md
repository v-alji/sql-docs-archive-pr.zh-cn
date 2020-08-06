---
title: 文件还原（简单恢复模式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- file restores [SQL Server]
- simple recovery model [SQL Server]
- restoring files [SQL Server], Transact-SQL restore sequence
- restoring files [SQL Server]
- Transact-SQL restore sequence
- restoring files [SQL Server], simple recovery model
- file restores [SQL Server], simple recovery model
- file restores [SQL Server], Transact-SQL restore sequence
ms.assetid: b6d07386-7c6f-4cc6-be32-93289adbd3d6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2ed48f48f531e727de5d6e1403ef47f5399f874d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689454"
---
# <a name="file-restores-simple-recovery-model"></a><span data-ttu-id="db82c-102">文件还原（简单恢复模式）</span><span class="sxs-lookup"><span data-stu-id="db82c-102">File Restores (Simple Recovery Model)</span></span>
  <span data-ttu-id="db82c-103">本主题仅适用于至少包含一个只读辅助文件组的简单模式数据库。</span><span class="sxs-lookup"><span data-stu-id="db82c-103">This topic is relevant only for simple-model databases that contain at least one read-only secondary filegroup.</span></span>  
  
 <span data-ttu-id="db82c-104">文件还原的目标是还原一个或多个损坏的文件，而不是还原整个数据库。</span><span class="sxs-lookup"><span data-stu-id="db82c-104">In a file restore, the goal is to restore one or more damaged files without restoring the whole database.</span></span> <span data-ttu-id="db82c-105">在简单恢复模式下，仅只读文件支持文件备份。</span><span class="sxs-lookup"><span data-stu-id="db82c-105">Under the simple recovery model, file backups are supported only for read-only files.</span></span> <span data-ttu-id="db82c-106">在还原数据库备份或部分备份时，将始终一同还原主文件组和读/写辅助文件组。</span><span class="sxs-lookup"><span data-stu-id="db82c-106">The primary filegroup and read/write secondary filegroups are always restored together, by restoring a database or partial backup.</span></span>  
  
 <span data-ttu-id="db82c-107">这些文件还原方案如下：</span><span class="sxs-lookup"><span data-stu-id="db82c-107">The file-restore scenarios are as follows:</span></span>  
  
-   <span data-ttu-id="db82c-108">脱机文件还原</span><span class="sxs-lookup"><span data-stu-id="db82c-108">Offline file restore</span></span>  
  
     <span data-ttu-id="db82c-109">在“脱机文件还原”  中，还原已损坏的文件或文件组时，数据库处于脱机状态。</span><span class="sxs-lookup"><span data-stu-id="db82c-109">In an *offline file restore*, the database is offline while damaged files or filegroups are restored.</span></span> <span data-ttu-id="db82c-110">还原顺序结束时，数据库将联机。</span><span class="sxs-lookup"><span data-stu-id="db82c-110">At the end of the restore sequence, the database comes online.</span></span>  
  
     <span data-ttu-id="db82c-111">所有版本的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 都支持脱机文件还原。</span><span class="sxs-lookup"><span data-stu-id="db82c-111">All editions of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] support offline file restore.</span></span>  
  
-   <span data-ttu-id="db82c-112">联机文件还原</span><span class="sxs-lookup"><span data-stu-id="db82c-112">Online file restore</span></span>  
  
     <span data-ttu-id="db82c-113">在“联机文件还原”  中，如果数据库在还原时处于联机状态，则该数据库在文件还原过程中将保持联机状态。</span><span class="sxs-lookup"><span data-stu-id="db82c-113">In an *online file restore*, if database is online at restore time, it remains online during the file restore.</span></span> <span data-ttu-id="db82c-114">不过，各文件组中如果有文件正在被还原，则该文件组在还原操作过程中将处于脱机状态。</span><span class="sxs-lookup"><span data-stu-id="db82c-114">However, each filegroup in which a file is being restored is offline during the restore operation.</span></span> <span data-ttu-id="db82c-115">恢复脱机文件组中的所有文件之后，该文件组将自动变为联机状态。</span><span class="sxs-lookup"><span data-stu-id="db82c-115">After all the files in an offline filegroup are recovered, the filegroup is automatically brought online.</span></span>  
  
     <span data-ttu-id="db82c-116">有关联机页和文件还原支持的信息，请参阅 [SQL Server 2014 各个版本支持的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="db82c-116">For information about support for online page and file restore, see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span> <span data-ttu-id="db82c-117">有关联机还原的详细信息，请参阅[联机还原 (SQL Server)](online-restore-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="db82c-117">For more information about online restores, see [Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md).</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="db82c-118">如果希望数据库脱机以进行文件还原，请在开始还原顺序之前执行下列 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options) 语句以使数据库脱机：ALTER DATABASE database_name SET OFFLINE  。</span><span class="sxs-lookup"><span data-stu-id="db82c-118">If you want the database to be offline for a file restore, take the database offline before you start the restore sequence by executing the following [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options) statement: ALTER DATABASE *database_name* SET OFFLINE.</span></span>  
  

  
##  <a name="overview-of-file-and-filegroup-restore-under-the-simple-recovery-model"></a><a name="Overview"></a> <span data-ttu-id="db82c-119">在简单恢复模式下还原文件和文件组的概述</span><span class="sxs-lookup"><span data-stu-id="db82c-119">Overview of File and Filegroup Restore Under the Simple Recovery Model</span></span>  
 <span data-ttu-id="db82c-120">文件还原方案由复制、前滚和恢复相应数据的单一还原顺序组成，如下所示：</span><span class="sxs-lookup"><span data-stu-id="db82c-120">A file restore scenario consists of a single restore sequence that copies, rolls forward, and recovers the appropriate data as follows:</span></span>  
  
1.  <span data-ttu-id="db82c-121">从各个损坏文件的最新文件备份还原每个文件。</span><span class="sxs-lookup"><span data-stu-id="db82c-121">Restore each damaged file from its most recent file backup.</span></span>  
  
2.  <span data-ttu-id="db82c-122">针对每个还原的文件，还原最新的差异文件备份并恢复数据库。</span><span class="sxs-lookup"><span data-stu-id="db82c-122">Restore the most recent differential file backup for each restored file and recover the database.</span></span>  
  
### <a name="transact-sql-steps-for-file-restore-sequence-simple-recovery-model"></a><span data-ttu-id="db82c-123">文件还原序列的 Transact-SQL 步骤（简单恢复模式）</span><span class="sxs-lookup"><span data-stu-id="db82c-123">Transact-SQL Steps for File Restore Sequence (Simple Recovery Model)</span></span>  
 <span data-ttu-id="db82c-124">本节说明用于简单文件还原序列的基本 [!INCLUDE[tsql](../../../includes/tsql-md.md)][RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 选项。</span><span class="sxs-lookup"><span data-stu-id="db82c-124">This section shows the essential [!INCLUDE[tsql](../../../includes/tsql-md.md)][RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) options for a simple file-restore sequence.</span></span> <span data-ttu-id="db82c-125">将省略与此目的不相关的语法和详细信息。</span><span class="sxs-lookup"><span data-stu-id="db82c-125">Syntax and details that are not relevant to this purpose are omitted.</span></span>  
  
 <span data-ttu-id="db82c-126">该还原序列仅包含两个 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="db82c-126">The restore sequence contains only two [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="db82c-127">第一个语句还原辅助文件（即文件 `A`），这是使用 WITH NORECOVERY 还原的。</span><span class="sxs-lookup"><span data-stu-id="db82c-127">The first statement restores a secondary file, file `A`, which is restored using WITH NORECOVERY.</span></span> <span data-ttu-id="db82c-128">第二项操作是还原其他两个文件（ `B` 和 `C` ），这两个文件是使用 WITH RECOVERY 从不同的备份设备还原的：</span><span class="sxs-lookup"><span data-stu-id="db82c-128">The second operation restores two other files, `B` and `C` which are restored using WITH RECOVERY from a different backup device:</span></span>  
  
1.  <span data-ttu-id="db82c-129">RESTORE DATABASE *database* FILE **=** _name_of_file_A_</span><span class="sxs-lookup"><span data-stu-id="db82c-129">RESTORE DATABASE *database* FILE **=**_name_of_file_A_</span></span>  
  
     <span data-ttu-id="db82c-130">FROM *file_backup_of_file_A*</span><span class="sxs-lookup"><span data-stu-id="db82c-130">FROM *file_backup_of_file_A*</span></span>  
  
     <span data-ttu-id="db82c-131">WITH NORECOVERY **;**</span><span class="sxs-lookup"><span data-stu-id="db82c-131">WITH NORECOVERY **;**</span></span>  
  
2.  <span data-ttu-id="db82c-132">RESTORE DATABASE *database* FILE **=** _name_of_file_B_ **,** _name_of_file_C_</span><span class="sxs-lookup"><span data-stu-id="db82c-132">RESTORE DATABASE *database* FILE **=**_name_of_file_B_**,**_name_of_file_C_</span></span>  
  
     <span data-ttu-id="db82c-133">FROM *file_backup_of_files_B_and_C*</span><span class="sxs-lookup"><span data-stu-id="db82c-133">FROM *file_backup_of_files_B_and_C*</span></span>  
  
     <span data-ttu-id="db82c-134">WITH RECOVERY **;**</span><span class="sxs-lookup"><span data-stu-id="db82c-134">WITH RECOVERY **;**</span></span>  
  
### <a name="examples"></a><span data-ttu-id="db82c-135">示例</span><span class="sxs-lookup"><span data-stu-id="db82c-135">Examples</span></span>  
  
-   [<span data-ttu-id="db82c-136">示例：只读文件的联机还原（简单恢复模式）</span><span class="sxs-lookup"><span data-stu-id="db82c-136">Example: Online Restore of a Read-Only File &#40;Simple Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [<span data-ttu-id="db82c-137">示例：主文件组和一个其他文件组的脱机还原（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="db82c-137">Example: Offline Restore of Primary and One Other Filegroup &#40;Full Recovery Model&#41;</span></span>](example-offline-restore-of-primary-and-one-other-filegroup-full-recovery-model.md)  
  
 
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="db82c-138">相关任务</span><span class="sxs-lookup"><span data-stu-id="db82c-138">Related Tasks</span></span>  
 <span data-ttu-id="db82c-139">**还原文件和文件组**</span><span class="sxs-lookup"><span data-stu-id="db82c-139">**To restore files and filegroups**</span></span>  
  
-   [<span data-ttu-id="db82c-140">在现有文件上还原文件和文件组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="db82c-140">Restore Files and Filegroups over Existing Files &#40;SQL Server&#41;</span></span>](restore-files-and-filegroups-over-existing-files-sql-server.md)  
  
-   [<span data-ttu-id="db82c-141">还原文件和文件组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="db82c-141">Restore Files and Filegroups &#40;SQL Server&#41;</span></span>](restore-files-and-filegroups-sql-server.md)  
  
-   [<span data-ttu-id="db82c-142">还原文件和文件组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="db82c-142">Restore Files and Filegroups &#40;SQL Server&#41;</span></span>](restore-files-and-filegroups-sql-server.md)  
  
-   <span data-ttu-id="db82c-143"><xref:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="db82c-143"><xref:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore%2A> (SMO)</span></span>  
  
  
  
## <a name="see-also"></a><span data-ttu-id="db82c-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="db82c-144">See Also</span></span>  
 <span data-ttu-id="db82c-145">[备份和还原：互操作性和共存 &#40;SQL Server&#41;](backup-and-restore-interoperability-and-coexistence-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="db82c-145">[Backup and Restore: Interoperability and Coexistence &#40;SQL Server&#41;](backup-and-restore-interoperability-and-coexistence-sql-server.md) </span></span>  
 <span data-ttu-id="db82c-146">[差异备份 (SQL Server)](differential-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="db82c-146">[Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md) </span></span>  
 <span data-ttu-id="db82c-147">[完整文件备份 (SQL Server)](full-file-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="db82c-147">[Full File Backups &#40;SQL Server&#41;](full-file-backups-sql-server.md) </span></span>  
 <span data-ttu-id="db82c-148">[备份概述 (SQL Server)](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="db82c-148">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 <span data-ttu-id="db82c-149">[还原和恢复概述 (SQL Server)](restore-and-recovery-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="db82c-149">[Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span></span>  
 <span data-ttu-id="db82c-150">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="db82c-150">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="db82c-151">[完整数据库还原（简单恢复模式）](complete-database-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="db82c-151">[Complete Database Restores &#40;Simple Recovery Model&#41;](complete-database-restores-simple-recovery-model.md) </span></span>  
 [<span data-ttu-id="db82c-152">段落还原 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="db82c-152">Piecemeal Restores &#40;SQL Server&#41;</span></span>](piecemeal-restores-sql-server.md)  
  
  
