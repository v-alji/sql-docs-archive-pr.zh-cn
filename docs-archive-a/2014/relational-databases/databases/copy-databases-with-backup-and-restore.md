---
title: 通过备份和还原复制数据库 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server], back up and restore
- restoring databases [SQL Server], previous SQL Server versions
- database restores [SQL Server], copying databases
- restoring databases [SQL Server], onto another server instance
- restoring [SQL Server], onto another server instance
- backing up databases [SQL Server], copying databases
- database backups [SQL Server], copying databases
ms.assetid: b93e9701-72a0-408e-958c-dc196872c040
author: stevestein
ms.author: sstein
ms.openlocfilehash: a8ffed36767f961f7482aa0dccf755118c80c019
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689432"
---
# <a name="copy-databases-with-backup-and-restore"></a><span data-ttu-id="ab972-102">通过备份和还原来复制数据库</span><span class="sxs-lookup"><span data-stu-id="ab972-102">Copy Databases with Backup and Restore</span></span>
  <span data-ttu-id="ab972-103">在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中，可以通过还原使用 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 或更高版本创建的用户数据库备份来创建新数据库。</span><span class="sxs-lookup"><span data-stu-id="ab972-103">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you can create a new database by restoring a backup of a user database created by using [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or a later version.</span></span> <span data-ttu-id="ab972-104">但是， **无法还原使用**早期版本创建的 **master** 、 **model** 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]备份。</span><span class="sxs-lookup"><span data-stu-id="ab972-104">However, backups of **master**, **model** and **msdb** that were created by using an earlier version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot be restored by [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="ab972-105">此外，任何早期版本的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 都无法还原 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]备份。</span><span class="sxs-lookup"><span data-stu-id="ab972-105">Also, [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] backups cannot be restored by any earlier version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="ab972-106">使用与早期版本不同的默认路径。</span><span class="sxs-lookup"><span data-stu-id="ab972-106">uses a different default path than earlier versions.</span></span> <span data-ttu-id="ab972-107">因此，若要还原在早期版本的默认位置中创建的数据库备份，必须使用 MOVE 选项。</span><span class="sxs-lookup"><span data-stu-id="ab972-107">Therefore, to restore backups of a database created in the default location of earlier versions you must use the MOVE option.</span></span> <span data-ttu-id="ab972-108">有关新的默认路径的信息，请参阅 [SQL Server 的默认实例和命名实例的文件位置](../../sql-server/install/file-locations-for-default-and-named-instances-of-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ab972-108">For information about the new default path see [File Locations for Default and Named Instances of SQL Server](../../sql-server/install/file-locations-for-default-and-named-instances-of-sql-server.md).</span></span> <span data-ttu-id="ab972-109">有关移动数据库文件的详细信息，请参阅本主题中后面的“移动数据库文件”。</span><span class="sxs-lookup"><span data-stu-id="ab972-109">For more information about moving database files, see "Moving the Database Files," later in this topic.</span></span>  
  
## <a name="general-steps-for-using-backup-and-restore-to-copy-a-database"></a><span data-ttu-id="ab972-110">使用备份和还原复制数据库的一般步骤</span><span class="sxs-lookup"><span data-stu-id="ab972-110">General Steps for Using Backup and Restore to Copy a Database</span></span>  
 <span data-ttu-id="ab972-111">使用备份和还原将数据库复制到其他 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例时，源计算机和目标计算机可以是运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的任何平台。</span><span class="sxs-lookup"><span data-stu-id="ab972-111">When you use backup and restore to copy a database to another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the source and destination computers can be any platform on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] runs.</span></span>  
  
 <span data-ttu-id="ab972-112">一般步骤如下：</span><span class="sxs-lookup"><span data-stu-id="ab972-112">The general steps are:</span></span>  
  
1.  <span data-ttu-id="ab972-113">备份可能位于 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 或更高版本的实例上的源数据库。</span><span class="sxs-lookup"><span data-stu-id="ab972-113">Back up the source database, which can reside on an instance of [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or later.</span></span> <span data-ttu-id="ab972-114">运行此 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的计算机为“源计算机”  。</span><span class="sxs-lookup"><span data-stu-id="ab972-114">The computer on which this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running is the *source computer*.</span></span>  
  
2.  <span data-ttu-id="ab972-115">在要将数据库复制到 (*目标计算机*的计算机上) ，连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 您计划在其上还原数据库的实例。</span><span class="sxs-lookup"><span data-stu-id="ab972-115">On the computer to which you want to copy the database (the *destination computer*), connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on which you plan to restore the database.</span></span> <span data-ttu-id="ab972-116">如果需要，在目标服务器实例上创建与源数据库备份设备相同的设备。</span><span class="sxs-lookup"><span data-stu-id="ab972-116">If needed, on the destination server instance, create the same backup devices as used to the backup of the source databases.</span></span>  
  
3.  <span data-ttu-id="ab972-117">在目标计算机上还原源数据库的备份。</span><span class="sxs-lookup"><span data-stu-id="ab972-117">Restore the backup of the source database on the destination computer.</span></span> <span data-ttu-id="ab972-118">还原数据库操作将自动创建所有数据库文件。</span><span class="sxs-lookup"><span data-stu-id="ab972-118">Restoring the database automatically creates all of the database files.</span></span>  
  
 <span data-ttu-id="ab972-119">下列主题讨论可能影响此进程的其他注意事项。</span><span class="sxs-lookup"><span data-stu-id="ab972-119">The following topics address additional considerations that may affect this process.</span></span>  
  
## <a name="before-you-restore-database-files"></a><span data-ttu-id="ab972-120">还原数据库文件之前</span><span class="sxs-lookup"><span data-stu-id="ab972-120">Before You Restore Database Files</span></span>  
 <span data-ttu-id="ab972-121">还原数据库将自动创建还原数据库所需的数据库文件。</span><span class="sxs-lookup"><span data-stu-id="ab972-121">Restoring a database automatically creates the database files that are needed by the restoring database.</span></span> <span data-ttu-id="ab972-122">默认情况下，还原进程中 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 创建的文件的名称和路径与源计算机上原始数据库中备份文件的名称和路径相同。</span><span class="sxs-lookup"><span data-stu-id="ab972-122">By default, the files that are created by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] during the restoration process use the same names and paths as the backup files from the original database on the source computer.</span></span>  
  
 <span data-ttu-id="ab972-123">或者，在还原数据库时，可以指定用于还原数据库的设备映射、文件名或路径。</span><span class="sxs-lookup"><span data-stu-id="ab972-123">Optionally, when restoring the database, you can specify the device mapping, file names, or path for the restoring database.</span></span> <span data-ttu-id="ab972-124">这在下列情况下可能很有必要：</span><span class="sxs-lookup"><span data-stu-id="ab972-124">This might be necessary in the following situations:</span></span>  
  
-   <span data-ttu-id="ab972-125">在其他计算机上不存在原始计算机上的数据库使用的目录结构或驱动器映射。</span><span class="sxs-lookup"><span data-stu-id="ab972-125">The directory structure or drive mapping used by the database on the original computer not exist on the other computer.</span></span> <span data-ttu-id="ab972-126">例如，备份中可能包含一个默认要还原到驱动器 E 的文件，而目标计算机上没有驱动器 E。</span><span class="sxs-lookup"><span data-stu-id="ab972-126">For example, perhaps the backup contains a file that would be restored to drive E by default, but the destination computer lacks a drive E.</span></span>  
  
-   <span data-ttu-id="ab972-127">目标位置可能空间不足。</span><span class="sxs-lookup"><span data-stu-id="ab972-127">The target location might have insufficient space.</span></span>  
  
-   <span data-ttu-id="ab972-128">您在重复使用在还原目标上存在的数据库名称并且其任何文件的名称与备份集中的某个数据库文件同名，则会发生以下情况之一：</span><span class="sxs-lookup"><span data-stu-id="ab972-128">You are reusing a database name that exists on the restore destination and any of its files is named the same as a database file in the backup set, one of the following occurs:</span></span>  
  
    -   <span data-ttu-id="ab972-129">如果可以覆盖现有的数据库文件，将覆盖该文件（这不会影响属于不同数据库名称的文件）。</span><span class="sxs-lookup"><span data-stu-id="ab972-129">If the existing database file can be overwritten, it will be overwritten (this would not affect a file that belongs to a different database name).</span></span>  
  
    -   <span data-ttu-id="ab972-130">如果无法覆盖现有文件，则会出现还原错误。</span><span class="sxs-lookup"><span data-stu-id="ab972-130">If the existing file cannot be overwritten, a restore error would occur.</span></span>  
  
 <span data-ttu-id="ab972-131">若要避免错误和意外结果，则在还原操作前，您可以使用 [backupfile](/sql/relational-databases/system-tables/backupfile-transact-sql) 历史记录表确定备份中您计划还原的数据库文件和日志文件。</span><span class="sxs-lookup"><span data-stu-id="ab972-131">To avoid errors and unintended consequences, before the restore operation, you can use the [backupfile](/sql/relational-databases/system-tables/backupfile-transact-sql) history table to find out the database and log files in the backup you plan to restore.</span></span>  
  
## <a name="moving-the-database-files"></a><span data-ttu-id="ab972-132">移动数据库文件</span><span class="sxs-lookup"><span data-stu-id="ab972-132">Moving the Database Files</span></span>  
 <span data-ttu-id="ab972-133">如果由于前面提到的原因，无法将数据库备份中的文件还原到目标计算机上，则必须在还原这些文件时将它们移到新的位置。</span><span class="sxs-lookup"><span data-stu-id="ab972-133">If the files within the database backup cannot be restored onto the destination computer because of the reasons mentioned earlier, it is necessary to move the files to a new location while they are being restored.</span></span> <span data-ttu-id="ab972-134">例如：</span><span class="sxs-lookup"><span data-stu-id="ab972-134">For example:</span></span>  
  
-   <span data-ttu-id="ab972-135">您想要通过在早期版本的默认位置创建的备份还原数据库。</span><span class="sxs-lookup"><span data-stu-id="ab972-135">You want to restore a database from backups created in the default location of the earlier version.</span></span>  
  
-   <span data-ttu-id="ab972-136">由于容量方面的原因，可能必须将备份中的一些数据库文件还原到其他驱动器上。</span><span class="sxs-lookup"><span data-stu-id="ab972-136">It may be necessary to restore some of the database files in the backup to a different drive because of capacity considerations.</span></span> <span data-ttu-id="ab972-137">这种情况很可能经常发生，因为单位中大多数计算机的磁盘驱动器的数目和大小不同或软件配置不同。</span><span class="sxs-lookup"><span data-stu-id="ab972-137">This is likely to be a common occurrence because most computers within an organization do not have the same number and size of disk drives or identical software configurations.</span></span>  
  
-   <span data-ttu-id="ab972-138">为了便于进行测试，可能必须在同一台计算机上创建现有数据库的副本。</span><span class="sxs-lookup"><span data-stu-id="ab972-138">It may be necessary to create a copy of an existing database on the same computer for testing purposes.</span></span> <span data-ttu-id="ab972-139">在这种情况下，因为原始数据库的数据库文件已经存在，所以在还原操作过程中创建数据库副本时，需要指定其他文件名。</span><span class="sxs-lookup"><span data-stu-id="ab972-139">In this case, the database files for the original database already exist, so different file names need to be specified when the database copy is created during the restore operation.</span></span>  
  
 <span data-ttu-id="ab972-140">有关详细信息，请参阅本主题中后面的“将文件和文件组还原到新位置”。</span><span class="sxs-lookup"><span data-stu-id="ab972-140">For more information, see "To restore files and filegroups to a new location," later in this topic.</span></span>  
  
## <a name="changing-the-database-name"></a><span data-ttu-id="ab972-141">更改数据库名称</span><span class="sxs-lookup"><span data-stu-id="ab972-141">Changing the Database Name</span></span>  
 <span data-ttu-id="ab972-142">在将数据库还原到目标计算机时可以更改其名称，而不必先还原数据库再手动更改其名称。</span><span class="sxs-lookup"><span data-stu-id="ab972-142">The name of the database can be changed as it is restored to the destination computer, without having to restore the database first and then change the name manually.</span></span> <span data-ttu-id="ab972-143">例如，可能有必要将数据库名称由 **Sales** 改为 **SalesCopy** 来表示这是数据库的一个副本。</span><span class="sxs-lookup"><span data-stu-id="ab972-143">For example, it may be necessary to change the database name from **Sales** to **SalesCopy** to indicate that this is a copy of a database.</span></span>  
  
 <span data-ttu-id="ab972-144">还原数据库时，显式提供的数据库名称将自动用作新的数据库名称。</span><span class="sxs-lookup"><span data-stu-id="ab972-144">The database name that is explicitly supplied when you restore a database is used automatically as the new database name.</span></span> <span data-ttu-id="ab972-145">由于数据库名称尚不存在，因此需使用备份中的文件创建新的数据库名称。</span><span class="sxs-lookup"><span data-stu-id="ab972-145">Because the database name does not already exist, a new one is created by using the files in the backup.</span></span>  
  
## <a name="when-upgrading-a-database-by-using-restore"></a><span data-ttu-id="ab972-146">使用还原升级数据库时</span><span class="sxs-lookup"><span data-stu-id="ab972-146">When Upgrading a Database by Using Restore</span></span>  
 <span data-ttu-id="ab972-147">从早期版本中还原备份时，提前了解目标计算机上是否存在备份中每个全文目录的路径（驱动器和目录）将很有帮助。</span><span class="sxs-lookup"><span data-stu-id="ab972-147">When restoring backups from an earlier version, it is helpful to know in advance whether the path (drive and directory) of each of the full-text catalogs in a backup exists on the destination computer.</span></span> <span data-ttu-id="ab972-148">若要列出备份中每个文件（包括目录文件）的逻辑名称和物理名称、路径名和文件名，请使用 RESTORE FILELISTONLY FROM *<backup_device>* 语句。</span><span class="sxs-lookup"><span data-stu-id="ab972-148">To list the logical names and physical names, path and file name) of every file in a backup, including the catalog files, use a RESTORE FILELISTONLY FROM *<backup_device>* statement.</span></span> <span data-ttu-id="ab972-149">有关详细信息，请参阅 [RESTORE FILELISTONLY (Transact-SQL)](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ab972-149">For more information, see [RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql).</span></span>  
  
 <span data-ttu-id="ab972-150">如果目标计算机上不存在相同的路径，则您可以执行下列两种操作：</span><span class="sxs-lookup"><span data-stu-id="ab972-150">If the same path does not exist on the destination computer, you have two alternatives:</span></span>  
  
-   <span data-ttu-id="ab972-151">在目标计算机上创建相同的驱动器/目录映射。</span><span class="sxs-lookup"><span data-stu-id="ab972-151">Create the equivalent drive/directory mapping on the destination computer.</span></span>  
  
-   <span data-ttu-id="ab972-152">通过在 RESTORE DATABASE 语句中使用 WITH MOVE 子句，在还原操作过程中将目录文件移动到新位置。</span><span class="sxs-lookup"><span data-stu-id="ab972-152">Move the catalog files to a new location during the restore operation, by using the WITH MOVE clause in your RESTORE DATABASE statement.</span></span> <span data-ttu-id="ab972-153">有关详细信息，请参阅 [RESTORE (Transact-SQL)](/sql/t-sql/statements/restore-statements-transact-sql)备份。</span><span class="sxs-lookup"><span data-stu-id="ab972-153">For more information, see [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>  
  
 <span data-ttu-id="ab972-154">有关升级全文检索的替代选项的信息，请参阅 [升级全文搜索](../search/upgrade-full-text-search.md)。</span><span class="sxs-lookup"><span data-stu-id="ab972-154">For information about alternative options for upgrading full-text indexes, see [Upgrade Full-Text Search](../search/upgrade-full-text-search.md).</span></span>  
  
## <a name="database-ownership"></a><span data-ttu-id="ab972-155">数据库所有权</span><span class="sxs-lookup"><span data-stu-id="ab972-155">Database Ownership</span></span>  
 <span data-ttu-id="ab972-156">在其他计算机上还原数据库时，启动还原操作的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录用户或 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 用户将自动成为新数据库的所有者。</span><span class="sxs-lookup"><span data-stu-id="ab972-156">When a database is restored on another computer, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login or [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows user who initiates the restore operation becomes the owner of the new database automatically.</span></span> <span data-ttu-id="ab972-157">还原数据库时，系统管理员或新数据库所有者可以更改数据库所有权。</span><span class="sxs-lookup"><span data-stu-id="ab972-157">When the database is restored, the system administrator or the new database owner can change database ownership.</span></span> <span data-ttu-id="ab972-158">若要防止未经授权的数据库还原操作，请使用介质集或备份集密码。</span><span class="sxs-lookup"><span data-stu-id="ab972-158">To prevent unauthorized restoration of a database, use media or backup set passwords.</span></span>  
  
## <a name="managing-metadata-when-restoring-to-another-server-instance"></a><span data-ttu-id="ab972-159">还原到另一个服务器实例时管理元数据</span><span class="sxs-lookup"><span data-stu-id="ab972-159">Managing Metadata When Restoring to Another Server Instance</span></span>  
 <span data-ttu-id="ab972-160">将数据库还原到另一个服务器实例上时，为了给用户和应用程序提供一致的体验，您可能需要在另一个服务器实例上为数据库重新创建部分或全部元数据（例如登录和作业）。</span><span class="sxs-lookup"><span data-stu-id="ab972-160">When you restore a database onto another server instance, to provide a consistent experience to users and applications, you might have to re-create some or all of the metadata for the database, such as logins and jobs, on the other server instance.</span></span> <span data-ttu-id="ab972-161">有关详细信息，请参阅 [当数据库在其他服务器实例上可用时管理元数据 (SQL Server)](manage-metadata-when-making-a-database-available-on-another-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ab972-161">For more information, see [Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](manage-metadata-when-making-a-database-available-on-another-server.md).</span></span>  
  
 <span data-ttu-id="ab972-162">**查看备份集中的数据文件和日志文件**</span><span class="sxs-lookup"><span data-stu-id="ab972-162">**To view the data and log files in a backup set**</span></span>  
  
-   [<span data-ttu-id="ab972-163">RESTORE FILELISTONLY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ab972-163">RESTORE FILELISTONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql)  
  
 <span data-ttu-id="ab972-164">**将文件和文件组还原到新位置**</span><span class="sxs-lookup"><span data-stu-id="ab972-164">**To restore files and filegroups to a new location**</span></span>  
  
-   [<span data-ttu-id="ab972-165">将文件还原到新位置 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ab972-165">Restore Files to a New Location &#40;SQL Server&#41;</span></span>](../backup-restore/restore-files-to-a-new-location-sql-server.md)  
  
-   [<span data-ttu-id="ab972-166">还原数据库备份 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="ab972-166">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](../backup-restore/restore-a-database-backup-using-ssms.md)  
  
 <span data-ttu-id="ab972-167">**在现有文件上还原文件和文件组**</span><span class="sxs-lookup"><span data-stu-id="ab972-167">**To restore files and filegroups over existing files**</span></span>  
  
-   [<span data-ttu-id="ab972-168">在现有文件上还原文件和文件组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ab972-168">Restore Files and Filegroups over Existing Files &#40;SQL Server&#41;</span></span>](../backup-restore/restore-files-and-filegroups-over-existing-files-sql-server.md)  
  
 <span data-ttu-id="ab972-169">**用新名称还原数据库**</span><span class="sxs-lookup"><span data-stu-id="ab972-169">**To restore a database with a new name**</span></span>  
  
-   [<span data-ttu-id="ab972-170">还原数据库备份 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="ab972-170">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](../backup-restore/restore-a-database-backup-using-ssms.md)  
  
 <span data-ttu-id="ab972-171">**重新启动中断的还原操作**</span><span class="sxs-lookup"><span data-stu-id="ab972-171">**To restart an interrupted restore operation**</span></span>  
  
-   [<span data-ttu-id="ab972-172">重新启动中断的还原操作 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ab972-172">Restart an Interrupted Restore Operation &#40;Transact-SQL&#41;</span></span>](../backup-restore/restart-an-interrupted-restore-operation-transact-sql.md)  
  
 <span data-ttu-id="ab972-173">**更改数据库的所有者**</span><span class="sxs-lookup"><span data-stu-id="ab972-173">**To change the owner of a database**</span></span>  
  
-   [<span data-ttu-id="ab972-174">sp_changedbowner (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ab972-174">sp_changedbowner &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-changedbowner-transact-sql)  
  
 <span data-ttu-id="ab972-175">**使用 SQL Server 管理对象 (SMO) 复制数据库**</span><span class="sxs-lookup"><span data-stu-id="ab972-175">**To copy a database by using SQL Server Management Objects (SMO)**</span></span>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Restore.ReadFileList%2A>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Restore.RelocateFiles%2A>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Restore.ReplaceDatabase%2A>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Restore>  
  
## <a name="see-also"></a><span data-ttu-id="ab972-176">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ab972-176">See Also</span></span>  
 <span data-ttu-id="ab972-177">[将数据库复制到其他服务器](copy-databases-to-other-servers.md) </span><span class="sxs-lookup"><span data-stu-id="ab972-177">[Copy Databases to Other Servers](copy-databases-to-other-servers.md) </span></span>  
 <span data-ttu-id="ab972-178">[SQL Server 的默认实例和命名实例的文件位置](../../sql-server/install/file-locations-for-default-and-named-instances-of-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ab972-178">[File Locations for Default and Named Instances of SQL Server](../../sql-server/install/file-locations-for-default-and-named-instances-of-sql-server.md) </span></span>  
 <span data-ttu-id="ab972-179">[RESTORE FILELISTONLY (Transact-SQL)](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ab972-179">[RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql) </span></span>  
 [<span data-ttu-id="ab972-180">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ab972-180">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
