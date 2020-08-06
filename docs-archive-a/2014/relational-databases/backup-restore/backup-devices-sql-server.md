---
title: 备份设备 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- tape backup devices, about tape backup devices
- backup devices [SQL Server]
- disk backup devices [SQL Server]
- database backups [SQL Server], backup devices
- logical devices [SQL Server]
- backup devices [SQL Server], about backup devices
- backing up [SQL Server], backup devices
- removable media [SQL Server]
- network shares [SQL Server]
- backups [SQL Server], backup devices
- tape backup devices
- physical devices [SQL Server]
- backing up databases [SQL Server], backup devices
- devices [SQL Server]
ms.assetid: 35a8e100-3ff2-4844-a5da-dd088c43cba4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a8abbba087679d263c00484764ecf445d6e5a006
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694501"
---
# <a name="backup-devices-sql-server"></a><span data-ttu-id="6c0e8-102">备份设备 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6c0e8-102">Backup Devices (SQL Server)</span></span>
  <span data-ttu-id="6c0e8-103">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库上执行备份操作期间，将备份的数据（“备份”  ）写入物理备份设备。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-103">During a backup operation on a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, the backed up data (the *backup*) is written to a physical backup device.</span></span> <span data-ttu-id="6c0e8-104">将介质集中的第一个备份写入物理备份设备时，便会初始化此备份设备。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-104">This physical backup device is initialized when the first backup in a media set is written to it.</span></span> <span data-ttu-id="6c0e8-105">包含一个或多个备份设备的集合的备份构成一个介质集。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-105">The backups on a set of one or more backup devices compose a single media set.</span></span>  
  
 <span data-ttu-id="6c0e8-106">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="6c0e8-106">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="6c0e8-107">术语和定义</span><span class="sxs-lookup"><span data-stu-id="6c0e8-107">Terms and Definitions</span></span>](#TermsAndDefinitions)  
  
-   [<span data-ttu-id="6c0e8-108">使用磁盘备份设备</span><span class="sxs-lookup"><span data-stu-id="6c0e8-108">Using Disk Backup Devices</span></span>](#DiskBackups)  
  
-   [<span data-ttu-id="6c0e8-109">使用磁带设备</span><span class="sxs-lookup"><span data-stu-id="6c0e8-109">Using Tape Devices</span></span>](#TapeDevices)  
  
-   [<span data-ttu-id="6c0e8-110">使用逻辑备份设备</span><span class="sxs-lookup"><span data-stu-id="6c0e8-110">Using a Logical Backup Device</span></span>](#LogicalBackupDevice)  
  
-   [<span data-ttu-id="6c0e8-111">镜像备份介质集</span><span class="sxs-lookup"><span data-stu-id="6c0e8-111">Mirrored Backup Media Sets</span></span>](#MirroredMediaSets)  
  
-   [<span data-ttu-id="6c0e8-112">SQL Server 备份数据存档</span><span class="sxs-lookup"><span data-stu-id="6c0e8-112">Archiving SQL Server Backups</span></span>](#Archiving)  
  
-   [<span data-ttu-id="6c0e8-113">相关任务</span><span class="sxs-lookup"><span data-stu-id="6c0e8-113">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="terms-and-definitions"></a><a name="TermsAndDefinitions"></a> <span data-ttu-id="6c0e8-114">术语和定义</span><span class="sxs-lookup"><span data-stu-id="6c0e8-114">Terms and Definitions</span></span>  
 <span data-ttu-id="6c0e8-115">备份磁盘 (backup disk)</span><span class="sxs-lookup"><span data-stu-id="6c0e8-115">backup disk</span></span>  
 <span data-ttu-id="6c0e8-116">包含一个或多个备份文件的硬盘或其他磁盘存储介质。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-116">A hard disk or other disk storage media that contains one or more backup files.</span></span> <span data-ttu-id="6c0e8-117">备份文件是常规操作系统文件。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-117">A backup file is a regular operating system file.</span></span>  
  
 <span data-ttu-id="6c0e8-118">介质集 (media set)</span><span class="sxs-lookup"><span data-stu-id="6c0e8-118">media set</span></span>  
 <span data-ttu-id="6c0e8-119">备份介质（磁带或磁盘文件）的有序集合，它使用固定类型和数量的备份设备。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-119">An ordered collection of backup media, tapes or disk files, that uses a fixed type and number of backup devices.</span></span> <span data-ttu-id="6c0e8-120">有关媒体集的信息，请参阅 [媒体集、媒体簇和备份集 (SQL Server)](media-sets-media-families-and-backup-sets-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-120">For more information about media sets, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
 <span data-ttu-id="6c0e8-121">物理备份设备 (physical backup device)</span><span class="sxs-lookup"><span data-stu-id="6c0e8-121">physical backup device</span></span>  
 <span data-ttu-id="6c0e8-122">磁带机或操作系统提供的磁盘文件。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-122">Either a tape drive or a disk file that is provided by the operating system.</span></span> <span data-ttu-id="6c0e8-123">可以将备份数据写入 1 到 64 个备份设备。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-123">A backup can be written to from 1 to 64 backup devices.</span></span> <span data-ttu-id="6c0e8-124">如果备份数据需要多个备份设备，则所有设备必须对应于一种设备类型（磁盘或磁带）。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-124">If a backup requires multiple backup devices, the devices all must correspond to a single type of device (disk or tape).</span></span>  
  
 <span data-ttu-id="6c0e8-125">除了磁盘或磁带外，还可以将 SQL Server 备份写入 Azure Blob 存储服务。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-125">SQL Server Backups can also be written to Azure Blob storage service in addition to disk or tape.</span></span>  
  
##  <a name="using-disk-backup-devices"></a><a name="DiskBackups"></a><span data-ttu-id="6c0e8-126">使用磁盘备份设备</span><span class="sxs-lookup"><span data-stu-id="6c0e8-126">Using Disk Backup Devices</span></span>  
 <span data-ttu-id="6c0e8-127">**本节内容：**</span><span class="sxs-lookup"><span data-stu-id="6c0e8-127">**In This Section:**</span></span>  
  
-   [<span data-ttu-id="6c0e8-128">使用物理名称指定备份文件 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6c0e8-128">Specifying a Backup File by Using Its Physical Name (Transact-SQL)</span></span>](#BackupFileUsingPhysicalName)  
  
-   [<span data-ttu-id="6c0e8-129">指定磁盘备份文件的路径</span><span class="sxs-lookup"><span data-stu-id="6c0e8-129">Specifying the Path of a Disk Backup File</span></span>](#BackupFileDiskPath)  
  
-   [<span data-ttu-id="6c0e8-130">备份到网络共享文件</span><span class="sxs-lookup"><span data-stu-id="6c0e8-130">Backing Up to a File on a Network Share</span></span>](#NetworkShare)  
  
 <span data-ttu-id="6c0e8-131">如果在备份操作将备份数据追加到介质集时磁盘文件已满，则备份操作会失败。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-131">If a disk file fills while a backup operation is appending a backup to the media set, the backup operation fails.</span></span> <span data-ttu-id="6c0e8-132">备份文件的最大大小由磁盘设备上的可用磁盘空间决定，因此，备份磁盘设备的适当大小取决于备份数据的大小。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-132">The maximum size of a backup file is determined by the free disk space available on the disk device; therefore, the appropriate size for a backup disk device depends on the size of your backups.</span></span>  
  
 <span data-ttu-id="6c0e8-133">磁盘备份设备可以是简单的磁盘设备，如 ATA 驱动器。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-133">A disk backup device could be a simple disk device, such as an ATA drive.</span></span> <span data-ttu-id="6c0e8-134">或者，您可以使用热交换磁盘驱动器，它允许您将驱动器上的已满磁盘透明地替换为空磁盘。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-134">Alternatively, you could use a hot-swappable disk drive that would let you transparently replace a full disk on the drive with an empty disk.</span></span> <span data-ttu-id="6c0e8-135">备份磁盘可以是服务器上的本地磁盘，也可以是作为共享网络资源的远程磁盘。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-135">A backup disk can be a local disk on the server or a remote disk that is a shared network resource.</span></span> <span data-ttu-id="6c0e8-136">有关如何使用远程磁盘的信息，请参阅本主题后面的 [备份到网络共享文件](#NetworkShare)。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-136">For information about how to use a remote disk, see [Backing Up to a File on a Network Share](#NetworkShare), later in this topic.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="6c0e8-137">管理工具在处理磁盘备份设备时非常灵活，因为它们会自动生成标有时间戳的磁盘文件名称。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-137">management tools are very flexible at handling disk backup devices because they automatically generate a time-stamped name on the disk file.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6c0e8-138">我们建议备份磁盘应不同于数据库数据和日志的磁盘。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-138">We recommend that a backup disk be a different disk than the database data and log disks.</span></span> <span data-ttu-id="6c0e8-139">这是数据或日志磁盘出现故障时访问备份数据必不可少的。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-139">This is necessary to make sure that you can access the backups if the data or log disk fails.</span></span>  
  
###  <a name="specifying-a-backup-file-by-using-its-physical-name-transact-sql"></a><a name="BackupFileUsingPhysicalName"></a><span data-ttu-id="6c0e8-140">通过使用 (Transact-sql) 的物理名称指定备份文件</span><span class="sxs-lookup"><span data-stu-id="6c0e8-140">Specifying a Backup File by Using Its Physical Name (Transact-SQL)</span></span>  
 <span data-ttu-id="6c0e8-141">使用物理设备名称指定备份文件的基本 [BACKUP](/sql/t-sql/statements/backup-transact-sql) 语法为：</span><span class="sxs-lookup"><span data-stu-id="6c0e8-141">The basic [BACKUP](/sql/t-sql/statements/backup-transact-sql) syntax for specifying a backup file by using its physical device name is:</span></span>  
  
 <span data-ttu-id="6c0e8-142">BACKUP DATABASE *database_name*</span><span class="sxs-lookup"><span data-stu-id="6c0e8-142">BACKUP DATABASE *database_name*</span></span>  
  
 <span data-ttu-id="6c0e8-143">TO DISK **=** { **'** _physical_backup_device_name_ **'**  |  **@** _physical_backup_device_name_var_ }</span><span class="sxs-lookup"><span data-stu-id="6c0e8-143">TO DISK **=** { **'**_physical_backup_device_name_**'** | **@**_physical_backup_device_name_var_ }</span></span>  
  
 <span data-ttu-id="6c0e8-144">例如：</span><span class="sxs-lookup"><span data-stu-id="6c0e8-144">For example:</span></span>  
  
```  
BACKUP DATABASE AdventureWorks2012   
   TO DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak';  
GO  
```  
  
 <span data-ttu-id="6c0e8-145">若要在 [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 语句中指定物理磁盘设备，基本语法为：</span><span class="sxs-lookup"><span data-stu-id="6c0e8-145">To specify a physical disk device in a [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) statement, the basic syntax is:</span></span>  
  
 <span data-ttu-id="6c0e8-146">RESTORE { DATABASE | LOG } *database_name*</span><span class="sxs-lookup"><span data-stu-id="6c0e8-146">RESTORE { DATABASE | LOG } *database_name*</span></span>  
  
 <span data-ttu-id="6c0e8-147">FROM DISK **=** { **'** _physical_backup_device_name_ **'**  |  **@** _physical_backup_device_name_var_ }</span><span class="sxs-lookup"><span data-stu-id="6c0e8-147">FROM DISK **=** { **'**_physical_backup_device_name_**'** | **@**_physical_backup_device_name_var_ }</span></span>  
  
 <span data-ttu-id="6c0e8-148">例如，</span><span class="sxs-lookup"><span data-stu-id="6c0e8-148">For example,</span></span>  
  
```  
RESTORE DATABASE AdventureWorks2012   
   FROM DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak';   
```  
  
###  <a name="specifying-the-path-of-a-disk-backup-file"></a><a name="BackupFileDiskPath"></a><span data-ttu-id="6c0e8-149">指定磁盘备份文件的路径</span><span class="sxs-lookup"><span data-stu-id="6c0e8-149">Specifying the Path of a Disk Backup File</span></span>  
 <span data-ttu-id="6c0e8-150">指定备份文件时，应输入其完整路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-150">When you are specifying a backup file, you should enter its full path and file name.</span></span> <span data-ttu-id="6c0e8-151">如果您在备份到文件时仅指定文件名或相对路径，则备份文件将存储到默认备份目录中。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-151">If you specify only the file name or a relative path when you are backing up to a file, the backup file is put in the default backup directory.</span></span> <span data-ttu-id="6c0e8-152">默认备份目录为 C:\Program Files\Microsoft SQL Server\MSSQL.*n*\MSSQL\Backup，其中 *n* 是服务器实例号。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-152">The default backup directory is C:\Program Files\Microsoft SQL Server\MSSQL.*n*\MSSQL\Backup, where *n* is the number of the server instance.</span></span> <span data-ttu-id="6c0e8-153">因此，对于默认服务器实例，默认备份目录为：C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Backup。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-153">Therefore, for the default server instance, the default backup directory is: C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Backup.</span></span>  
  
 <span data-ttu-id="6c0e8-154">为防止产生歧义，尤其是在脚本中，我们建议您在每个 DISK 子句中显式指定备份目录的路径。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-154">To avoid ambiguity, especially in scripts, we recommend that you explicitly specify the path of the backup directory in every DISK clause.</span></span> <span data-ttu-id="6c0e8-155">但是，当您使用查询编辑器时这一点不再那么重要。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-155">However, this is less important when you are using Query Editor.</span></span> <span data-ttu-id="6c0e8-156">此时，如果您确定备份文件位于默认备份目录中，则可以省略 DISK 子句中的路径。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-156">In that case, if you are sure that the backup file resides in the default backup directory, you can omit the path from a DISK clause.</span></span> <span data-ttu-id="6c0e8-157">例如，下面的 `BACKUP` 语句将 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库备份到默认的备份目录中。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-157">For example, the following `BACKUP` statement backs up the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database to the default backup directory.</span></span>  
  
```  
BACKUP DATABASE AdventureWorks2012   
   TO DISK = 'AdventureWorks2012.bak';  
GO  
```  
  
> [!NOTE]  
>  <span data-ttu-id="6c0e8-158">默认位置存储在 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\MSSQL.n\MSSQLServer** 下的 **BackupDirectory**注册表项中。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-158">The default location is stored in the **BackupDirectory** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\MSSQL.n\MSSQLServer**.</span></span>  
  
###  <a name="backing-up-to-a-file-on-a-network-share"></a><a name="NetworkShare"></a><span data-ttu-id="6c0e8-159">备份到网络共享上的文件</span><span class="sxs-lookup"><span data-stu-id="6c0e8-159">Backing Up to a File on a Network Share</span></span>  
 <span data-ttu-id="6c0e8-160">要让 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 访问远程磁盘文件， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务帐户必须有权访问网络共享。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-160">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to access a remote disk file, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account must have access to the network share.</span></span> <span data-ttu-id="6c0e8-161">这包括备份操作向网络共享中写入所需的权限以及还原操作从网络共享中读取所需的权限。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-161">This includes having the permissions needed for backup operations to write to the network share and for restore operations to read from it.</span></span> <span data-ttu-id="6c0e8-162">网络驱动器和权限的可用性取决于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务运行的环境：</span><span class="sxs-lookup"><span data-stu-id="6c0e8-162">The availability of network drives and permissions depends on the context is which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service is running:</span></span>  
  
-   <span data-ttu-id="6c0e8-163">若要在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用域用户帐户运行时备份到网络驱动器，共享驱动器必须在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 运行的会话中作为网络驱动器进行映射。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-163">To back up to a network drive when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running in a domain user account, the shared drive must be mapped as a network drive in the session where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running.</span></span> <span data-ttu-id="6c0e8-164">如果是通过命令行启动 Sqlservr.exe 的，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可以看到在登录会话中映射的所有网络驱动器。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-164">If you start Sqlservr.exe from command line, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sees any network drives you have mapped in your login session.</span></span>  
  
-   <span data-ttu-id="6c0e8-165">作为服务运行 Sqlservr.exe 时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将在单独的会话中运行，该会话与登录会话无关。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-165">When you run Sqlservr.exe as a service, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] runs in a separate session that has no relation to your login session.</span></span> <span data-ttu-id="6c0e8-166">运行服务的会话可以具有自己的映射驱动器（虽然它一般没有映射驱动器）。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-166">The session in which a service runs can have its own mapped drives, although it usually does not.</span></span>  
  
-   <span data-ttu-id="6c0e8-167">可以使用计算机帐户（而不是域用户）连接网络服务帐户。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-167">You can connect with the network service account by using the computer account instead of a domain user.</span></span> <span data-ttu-id="6c0e8-168">若要允许从特定计算机备份到共享驱动器，请向计算机帐户授予访问权限。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-168">To enable backups from specific computers to a shared drive, grant access to the computer accounts.</span></span> <span data-ttu-id="6c0e8-169">只要写入备份的 Sqlservr.exe 进程具有访问权限，那么发送 BACKUP 命令的用户是否具有访问权限便会无关紧要。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-169">As long as the Sqlservr.exe process that is writing the backup has access, it is irrelevant whether the user sending the BACKUP command has access.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="6c0e8-170">在网络上备份数据可能受网络错误的影响；因此，建议在使用远程磁盘时，完成备份后验证备份操作。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-170">Backing up data over a network can be subject to network errors; therefore, we recommend that when you are using a remote disk you verify the backup operation after it finishes.</span></span> <span data-ttu-id="6c0e8-171">有关详细信息，请参阅 [RESTORE VERIFYONLY (Transact-SQL)](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-171">For more information, see [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql).</span></span>  
  
#### <a name="specifying-a-universal-naming-convention-unc-name"></a><span data-ttu-id="6c0e8-172">指定通用命名约定 (UNC) 名称</span><span class="sxs-lookup"><span data-stu-id="6c0e8-172">Specifying a Universal Naming Convention (UNC) Name</span></span>  
 <span data-ttu-id="6c0e8-173">若要在备份或还原命令中指定网络共享，应针对备份设备使用文件的完全限定通用命名约定 (UNC) 名称。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-173">To specify a network share in a backup or restore command, you should use the fully qualified universal naming convention (UNC) name of the file for the backup device.</span></span> <span data-ttu-id="6c0e8-174">UNC 名称采用以下格式： **\\\\** _系统名称_ **\\** _共享名称_ **\\** _路径_ **\\** _文件名_。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-174">A UNC name has the form **\\\\**_Systemname_**\\**_ShareName_**\\**_Path_**\\**_FileName_.</span></span>  
  
 <span data-ttu-id="6c0e8-175">例如：</span><span class="sxs-lookup"><span data-stu-id="6c0e8-175">For example:</span></span>  
  
```  
BACKUP DATABASE AdventureWorks2012   
   TO DISK = '\\BackupSystem\BackupDisk1\AW_backups\AdventureWorksData.Bak';  
GO  
```  
  
##  <a name="using-tape-devices"></a><a name="TapeDevices"></a><span data-ttu-id="6c0e8-176">使用磁带设备</span><span class="sxs-lookup"><span data-stu-id="6c0e8-176">Using Tape Devices</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6c0e8-177">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的未来版本中将不再支持磁带备份设备。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-177">Support for tape backup devices will be removed in a future version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="6c0e8-178">请避免在新的开发工作中使用该功能，并着手修改当前还在使用该功能的应用程序。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-178">Avoid using this feature in new development work, and plan to modify applications that currently use this feature.</span></span>  
  
 <span data-ttu-id="6c0e8-179">**本节内容：**</span><span class="sxs-lookup"><span data-stu-id="6c0e8-179">**In This Section:**</span></span>  
  
-   [<span data-ttu-id="6c0e8-180">使用物理名称指定备份磁带 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6c0e8-180">Specifying a Backup Tape by Using Its Physical Name (Transact-SQL)</span></span>](#BackupTapeUsingPhysicalName)  
  
-   [<span data-ttu-id="6c0e8-181">特定于磁带的备份和还原选项 (Transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6c0e8-181">Tape-Specific BACKUP and RESTORE Options (Transact-SQL)</span></span>](#TapeOptions)  
  
-   [<span data-ttu-id="6c0e8-182">管理打开的磁带</span><span class="sxs-lookup"><span data-stu-id="6c0e8-182">Managing Open Tapes</span></span>](#OpenTapes)  
  
 <span data-ttu-id="6c0e8-183">将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据备份到磁带时要求 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 操作系统支持一个或多个磁带机。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-183">Backing up [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data to tape requires that the tape drive or drives be supported by the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows operating system.</span></span> <span data-ttu-id="6c0e8-184">另外，对于给定的磁带机，我们建议您仅使用磁带机制造商推荐的磁带。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-184">Additionally, for the given tape drive, we recommend that you use only tapes recommended by the drive manufacturer.</span></span> <span data-ttu-id="6c0e8-185">有关如何安装磁带机的详细信息，请参阅 Windows 操作系统的文档。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-185">For more information about how to install a tape drive, see the documentation for the Windows operating system.</span></span>  
  
 <span data-ttu-id="6c0e8-186">在使用磁带机时，备份操作可能会写满一个磁带，并继续在另一个磁带上进行。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-186">When a tape drive is used, a backup operation may fill one tape and continue onto another tape.</span></span> <span data-ttu-id="6c0e8-187">每个磁带包含一个介质标头。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-187">Each tape contains a media header.</span></span> <span data-ttu-id="6c0e8-188">使用的第一个介质称为“起始磁带  ”。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-188">The first media used is called the *initial tape*.</span></span> <span data-ttu-id="6c0e8-189">每个后续磁带称为“延续磁带”  ，其介质序列号比前一磁带的介质序列号大一。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-189">Each successive tape is known as a *continuation tape* and has a media sequence number that is one higher than the previous tape.</span></span> <span data-ttu-id="6c0e8-190">例如，与四个磁带设备相关联的介质集至少含有四个起始磁带（如果该数据库过大，还会有四个系列的延续磁带）。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-190">For example, a media set associated with four tape devices contains at least four initial tapes (and, if the database does not fit, four series of continuation tapes).</span></span> <span data-ttu-id="6c0e8-191">在追加备份集时，必须在序列中装入最后一个磁带。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-191">When appending a backup set, you must mount the last tape in the series.</span></span> <span data-ttu-id="6c0e8-192">如果没有装入最后一个磁带， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 将向前扫描到已装入磁带的末尾，然后要求更换磁带。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-192">If the last tape is not mounted, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] scans forward to the end of the mounted tape and then requires that you change the tape.</span></span> <span data-ttu-id="6c0e8-193">此时，请装入最后一个磁带。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-193">At that point, mount the last tape.</span></span>  
  
 <span data-ttu-id="6c0e8-194">磁带备份设备的用法类似于磁盘设备，但下述情况例外：</span><span class="sxs-lookup"><span data-stu-id="6c0e8-194">Tape backup devices are used like disk devices, with the following exceptions:</span></span>  
  
-   <span data-ttu-id="6c0e8-195">磁带设备必须物理连接到运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例的计算机上。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-195">The tape device must be connected physically to the computer that is running an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="6c0e8-196">不支持备份到远程磁带设备上。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-196">Backing up to remote tape devices is not supported.</span></span>  
  
-   <span data-ttu-id="6c0e8-197">如果磁带备份设备在备份操作过程中已满，但还必须写入一些数据，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将提示更换新磁带并在加载新磁带后继续备份操作。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-197">If a tape backup device is filled during the backup operation, but more data still must be written, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prompts for a new tape and continues the backup operation after a new tape is loaded.</span></span>  
  
###  <a name="specifying-a-backup-tape-by-using-its-physical-name-transact-sql"></a><a name="BackupTapeUsingPhysicalName"></a><span data-ttu-id="6c0e8-198">使用其物理名称指定备份磁带 (Transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6c0e8-198">Specifying a Backup Tape by Using Its Physical Name (Transact-SQL)</span></span>  
 <span data-ttu-id="6c0e8-199">使用磁带机物理设备名称指定备份磁带的基本 [BACKUP](/sql/t-sql/statements/backup-transact-sql) 语法为：</span><span class="sxs-lookup"><span data-stu-id="6c0e8-199">The basic [BACKUP](/sql/t-sql/statements/backup-transact-sql) syntax for specifying a backup tape using the physical device name of the tape drive is:</span></span>  
  
 <span data-ttu-id="6c0e8-200">BACKUP { DATABASE | LOG } *database_name*</span><span class="sxs-lookup"><span data-stu-id="6c0e8-200">BACKUP { DATABASE | LOG } *database_name*</span></span>  
  
 <span data-ttu-id="6c0e8-201">TO TAPE **=** { **'** _physical_backup_device_name_ **'**  |  **@** _physical_backup_device_name_var_ }</span><span class="sxs-lookup"><span data-stu-id="6c0e8-201">TO TAPE **=** { **'**_physical_backup_device_name_**'** | **@**_physical_backup_device_name_var_ }</span></span>  
  
 <span data-ttu-id="6c0e8-202">例如：</span><span class="sxs-lookup"><span data-stu-id="6c0e8-202">For example:</span></span>  
  
```  
BACKUP LOG AdventureWorks2012   
   TO TAPE = '\\.\tape0';  
GO  
```  
  
 <span data-ttu-id="6c0e8-203">若要在 [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 语句中指定物理磁带设备，基本语法为：</span><span class="sxs-lookup"><span data-stu-id="6c0e8-203">To specify a physical tape device in a [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) statement, the basic syntax is:</span></span>  
  
 <span data-ttu-id="6c0e8-204">RESTORE { DATABASE | LOG } *database_name*</span><span class="sxs-lookup"><span data-stu-id="6c0e8-204">RESTORE { DATABASE | LOG } *database_name*</span></span>  
  
 <span data-ttu-id="6c0e8-205">FROM TAPE **=** { **'** _physical_backup_device_name_ **'**  |  **@** _physical_backup_device_name_var_ }</span><span class="sxs-lookup"><span data-stu-id="6c0e8-205">FROM TAPE **=** { **'**_physical_backup_device_name_**'** | **@**_physical_backup_device_name_var_ }</span></span>  
  
###  <a name="tape-specific-backup-and-restore-options-transact-sql"></a><a name="TapeOptions"></a><span data-ttu-id="6c0e8-206">特定于磁带的备份和还原选项 (Transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6c0e8-206">Tape-Specific BACKUP and RESTORE Options (Transact-SQL)</span></span>  
 <span data-ttu-id="6c0e8-207">为了便于磁带管理，BACKUP 语句提供了下列磁带专用的选项：</span><span class="sxs-lookup"><span data-stu-id="6c0e8-207">To facilitate tape management, the BACKUP statement provides the following tape-specific options:</span></span>  
  
-   <span data-ttu-id="6c0e8-208">{ NOUNLOAD | **UNLOAD** }</span><span class="sxs-lookup"><span data-stu-id="6c0e8-208">{ NOUNLOAD | **UNLOAD** }</span></span>  
  
     <span data-ttu-id="6c0e8-209">您可以控制在备份或还原操作后备份磁带是否自动从磁带机卸载。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-209">You can control whether a backup tape is unloaded automatically from the tape drive after a backup or restore operation.</span></span> <span data-ttu-id="6c0e8-210">UNLOAD/NOUNLOAD 这一会话设置可在整个会话期间存在，或者在通过指定其他设置而进行重置之前一直存在。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-210">UNLOAD/NOUNLOAD is a session setting that persists for the life of the session or until it is reset by specifying the alternative.</span></span>  
  
-   <span data-ttu-id="6c0e8-211">{ **REWIND** | NOREWIND }</span><span class="sxs-lookup"><span data-stu-id="6c0e8-211">{ **REWIND** | NOREWIND }</span></span>  
  
     <span data-ttu-id="6c0e8-212">您可以控制在备份或还原操作后 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 是保持磁带处于打开状态，还是在磁带满后释放磁带并倒带。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-212">You can control whether [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] keeps the tape remains open after the backup or restore operation or releases and rewinds the tape after it fills.</span></span> <span data-ttu-id="6c0e8-213">默认行为是倒带 (REWIND)。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-213">The default behavior is to rewind the tape (REWIND).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6c0e8-214">有关 BACKUP 语法和参数的详细信息，请参阅 [BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-214">For more information about the BACKUP syntax and arguments, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span> <span data-ttu-id="6c0e8-215">有关 RESTORE 语法和参数的详细信息，请分别参阅 [RESTORE (Transact-SQL)](/sql/t-sql/statements/restore-statements-transact-sql) 和 [RESTORE 参数 (Transact-SQL)](/sql/t-sql/statements/restore-statements-arguments-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-215">For more information about the RESTORE syntax and arguments, see [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) and [RESTORE Arguments &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql), respectively.</span></span>  
  
###  <a name="managing-open-tapes"></a><a name="OpenTapes"></a><span data-ttu-id="6c0e8-216">管理打开的磁带</span><span class="sxs-lookup"><span data-stu-id="6c0e8-216">Managing Open Tapes</span></span>  
 <span data-ttu-id="6c0e8-217">若要查看打开的磁带设备列表以及装入请求状态，请查询 [sys.dm_io_backup_tapes](/sql/relational-databases/system-dynamic-management-views/sys-dm-io-backup-tapes-transact-sql) 动态管理视图。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-217">To view a list of open tape devices and the status of mount requests, query the [sys.dm_io_backup_tapes](/sql/relational-databases/system-dynamic-management-views/sys-dm-io-backup-tapes-transact-sql) dynamic management view.</span></span> <span data-ttu-id="6c0e8-218">此视图显示了所有打开的磁带。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-218">This view shows all the open tapes.</span></span> <span data-ttu-id="6c0e8-219">其中包括正在使用的磁带，它们等待下一个 BACKUP 或 RESTORE 操作时暂时处于空闲状态。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-219">These include in-use tapes that are temporarily idle while they wait for the next BACKUP or RESTORE operation.</span></span>  
  
 <span data-ttu-id="6c0e8-220">如果意外使磁带处于打开状态，则释放磁带的最快方式是使用以下命令：RESTORE REWINDONLY FROM TAPE **=** _backup_device_name_。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-220">If a tape has been accidentally left open, the fastest way to release the tape is by using the following command: RESTORE REWINDONLY FROM TAPE **=**_backup_device_name_.</span></span> <span data-ttu-id="6c0e8-221">有关详细信息，请参阅 [RESTORE REWINDONLY (Transact-SQL)](/sql/t-sql/statements/restore-statements-rewindonly-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-221">For more information, see [RESTORE REWINDONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-rewindonly-transact-sql).</span></span>  
  
## <a name="using-the-azure-blob-storage-service"></a><span data-ttu-id="6c0e8-222">使用 Azure Blob 存储服务</span><span class="sxs-lookup"><span data-stu-id="6c0e8-222">Using the Azure Blob Storage Service</span></span>  
 <span data-ttu-id="6c0e8-223">可以将 SQL Server 备份写入 Azure Blob 存储服务。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-223">SQL Server Backups can be written to the Azure Blob Storage Service.</span></span>  <span data-ttu-id="6c0e8-224">有关如何使用 Azure Blob 存储服务进行备份的详细信息，请参阅[使用 Azure Blob 存储服务进行备份和还原 SQL Server](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-224">For more information on how to use the Azure Blob storage service for your backups, see [SQL Server Backup and Restore with Azure Blob Storage Service](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).</span></span>  
  
##  <a name="using-a-logical-backup-device"></a><a name="LogicalBackupDevice"></a><span data-ttu-id="6c0e8-225">使用逻辑备份设备</span><span class="sxs-lookup"><span data-stu-id="6c0e8-225">Using a Logical Backup Device</span></span>  
 <span data-ttu-id="6c0e8-226">“逻辑备份设备  ”是指向特定物理备份设备（磁盘文件或磁带机）的可选用户定义名称。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-226">A *logical backup device* is an optional, user-defined name that points to a specific physical backup device (a disk file or tape drive).</span></span> <span data-ttu-id="6c0e8-227">通过逻辑备份设备，您可以在引用相应的物理备份设备时使用间接寻址。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-227">A logical backup device lets you use indirection when referencing the corresponding physical backup device.</span></span>  
  
 <span data-ttu-id="6c0e8-228">定义逻辑备份设备涉及为物理设备分配逻辑名称。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-228">Defining a logical backup device involves assigning a logical name to a physical device.</span></span> <span data-ttu-id="6c0e8-229">例如，逻辑设备 AdventureWorksBackups 可能被定义为指向 Z:\SQLServerBackups\AdventureWorks2012.bak 文件或 \\\\.\tape0 磁带驱动器。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-229">For example, a logical device, AdventureWorksBackups, could be defined to point to the Z:\SQLServerBackups\AdventureWorks2012.bak file or the \\\\.\tape0 tape drive.</span></span> <span data-ttu-id="6c0e8-230">备份和还原命令随后可以将 AdventureWorksBackups 指定为备份设备，而不是指定 DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak' 或 TAPE = '\\\\.\tape0'。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-230">Backup and restore commands can then specify AdventureWorksBackups as the backup device, instead of DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak' or TAPE = '\\\\.\tape0'.</span></span>  
  
 <span data-ttu-id="6c0e8-231">逻辑设备名称在服务器实例上的所有逻辑备份设备中必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-231">The logical device name must be unique among all the logical backup devices on the server instance.</span></span> <span data-ttu-id="6c0e8-232">若要查看现有逻辑设备名称，请查询 [sys.backup_devices](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) 目录视图。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-232">To view the existing logical device names, query the [sys.backup_devices](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) catalog view.</span></span> <span data-ttu-id="6c0e8-233">此视图显示每个逻辑备份设备的名称，并说明了相应物理备份设备的类型、物理文件名或路径。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-233">This view displays the name of each logical backup device and describes the type and physical file name or path of the corresponding physical backup device.</span></span>  
  
 <span data-ttu-id="6c0e8-234">定义逻辑备份设备后，您可以在 BACKUP 或 RESTORE 命令中指定此逻辑备份设备而不是设备的物理名称。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-234">After a logical backup device is defined, in a BACKUP or RESTORE command, you can specify the logical backup device instead of the physical name of the device.</span></span> <span data-ttu-id="6c0e8-235">例如，下面的语句将 `AdventureWorks2012` 数据库备份到 `AdventureWorksBackups` 逻辑备份设备。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-235">For example, the following statement backs up the `AdventureWorks2012` database to the `AdventureWorksBackups` logical backup device.</span></span>  
  
```  
BACKUP DATABASE AdventureWorks2012   
   TO AdventureWorksBackups;  
GO  
```  
  
> [!NOTE]  
>  <span data-ttu-id="6c0e8-236">在给定的 BACKUP 或 RESTORE 语句中，逻辑备份设备名称和相应的物理备份设备名称可以互换。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-236">In a given BACKUP or RESTORE statement, the logical backup device name and the corresponding physical backup device name are interchangeable.</span></span>  
  
 <span data-ttu-id="6c0e8-237">使用逻辑备份设备的一个优点是比使用长路径简单。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-237">One advantage of using a logical backup device is that it is simpler to use than a long path.</span></span> <span data-ttu-id="6c0e8-238">如果准备将一系列备份数据写入相同的路径或磁带设备，则使用逻辑备份设备非常有用。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-238">Using a logical backup device can help if you plan to write a series of backups to the same path or to a tape device.</span></span> <span data-ttu-id="6c0e8-239">逻辑备份设备对于标识磁带备份设备尤为有用。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-239">Logical backup devices are especially useful for identifying tape backup devices.</span></span>  
  
 <span data-ttu-id="6c0e8-240">可以编写一个备份脚本以使用特定逻辑备份设备。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-240">A backup script can be written to use a particular logical backup device.</span></span> <span data-ttu-id="6c0e8-241">这样，您无需更新脚本即可切换到新的物理备份设备。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-241">This lets you switch to a new physical backup devices without updating the script.</span></span> <span data-ttu-id="6c0e8-242">切换涉及以下过程：</span><span class="sxs-lookup"><span data-stu-id="6c0e8-242">Switching involves the following process:</span></span>  
  
1.  <span data-ttu-id="6c0e8-243">删除原来的逻辑备份设备。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-243">Dropping the original logical backup device.</span></span>  
  
2.  <span data-ttu-id="6c0e8-244">定义新的逻辑备份设备，新设备使用原来的逻辑设备名称，但映射到不同的物理备份设备。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-244">Defining a new logical backup device that uses the original logical device name but maps to a different physical backup device.</span></span> <span data-ttu-id="6c0e8-245">逻辑备份设备对于标识磁带备份设备尤为有用。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-245">Logical backup devices are especially useful for identifying tape backup devices.</span></span>  
  
##  <a name="mirrored-backup-media-sets"></a><a name="MirroredMediaSets"></a><span data-ttu-id="6c0e8-246">镜像备份介质集</span><span class="sxs-lookup"><span data-stu-id="6c0e8-246">Mirrored Backup Media Sets</span></span>  
 <span data-ttu-id="6c0e8-247">镜像备份介质集可减小备份设备故障的影响。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-247">Mirroring of backup media sets reduces the effect of backup-device malfunctions.</span></span> <span data-ttu-id="6c0e8-248">由于备份是防止数据丢失的最后防线，因此备份设备出现故障的后果是非常严重的。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-248">These malfunctions are especially serious because backups are the last line of defense against data loss.</span></span> <span data-ttu-id="6c0e8-249">随着数据库不断增大，备份设备或介质发生故障致使备份不可还原的可能性也相应增加。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-249">As the sizes of databases grow, the probability increases that a failure of a backup device or media will make a backup nonrestorable.</span></span> <span data-ttu-id="6c0e8-250">镜像备份介质通过提供物理备份设备冗余来提高备份的可靠性。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-250">Mirroring backup media increases the reliability of backups by providing redundancy for the physical backup device.</span></span> <span data-ttu-id="6c0e8-251">有关详细信息，请参阅本主题后面的 [镜像备份媒体集 (SQL Server)](mirrored-backup-media-sets-sql-server.md)不熟悉的读者。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-251">For more information, see [Mirrored Backup Media Sets &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6c0e8-252">只有 [!INCLUDE[ssEnterpriseEd2005](../../includes/ssenterpriseed2005-md.md)] 和更高版本支持镜像备份介质集。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-252">Mirrored backup media sets are supported only in [!INCLUDE[ssEnterpriseEd2005](../../includes/ssenterpriseed2005-md.md)] and later versions.</span></span>  
  
##  <a name="archiving-sql-server-backups"></a><a name="Archiving"></a><span data-ttu-id="6c0e8-253">存档 SQL Server 备份</span><span class="sxs-lookup"><span data-stu-id="6c0e8-253">Archiving SQL Server Backups</span></span>  
 <span data-ttu-id="6c0e8-254">建议您使用文件系统备份实用工具对磁盘备份数据进行存档，并将存档存储在另一个位置。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-254">We recommend that you use a file system backup utility to archive the disk backups and that you store the archives off-site.</span></span> <span data-ttu-id="6c0e8-255">使用磁盘的优点是您可以使用网络将已存档的备份数据写入另一个位置的磁盘。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-255">Using disk has the advantage that you use the network to write the archived backups onto an off-site disk.</span></span> <span data-ttu-id="6c0e8-256">Azure Blob 存储服务可作为站外存档选项。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-256">The Azure Blob storage service can be used as off-site archival option.</span></span>  <span data-ttu-id="6c0e8-257">可以上载磁盘备份，或直接将备份写入 Azure Blob 存储服务。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-257">You can either upload your disk backups, or directly write the backups to the Azure Blob storage service.</span></span>  
  
 <span data-ttu-id="6c0e8-258">另一个常用的存档方法是将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 备份写入本地备份磁盘，将备份存档到磁带，然后在将磁带存储在站外位置。</span><span class="sxs-lookup"><span data-stu-id="6c0e8-258">Another common archiving approach is to write [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backups onto a local backup disk, archive them to tape, and then store the tapes off-site.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="6c0e8-259">相关任务</span><span class="sxs-lookup"><span data-stu-id="6c0e8-259">Related Tasks</span></span>  
 <span data-ttu-id="6c0e8-260">**指定磁盘设备 (SQL Server Management Studio)**</span><span class="sxs-lookup"><span data-stu-id="6c0e8-260">**To specify a disk device (SQL Server Management Studio)**</span></span>  
  
-   [<span data-ttu-id="6c0e8-261">将磁盘或磁带指定为备份目标 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6c0e8-261">Specify a Disk or Tape As a Backup Destination &#40;SQL Server&#41;</span></span>](specify-a-disk-or-tape-as-a-backup-destination-sql-server.md)  
  
 <span data-ttu-id="6c0e8-262">**指定磁带设备 (SQL Server Management Studio)**</span><span class="sxs-lookup"><span data-stu-id="6c0e8-262">**To specify a tape device (SQL Server Management Studio)**</span></span>  
  
-   [<span data-ttu-id="6c0e8-263">将磁盘或磁带指定为备份目标 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6c0e8-263">Specify a Disk or Tape As a Backup Destination &#40;SQL Server&#41;</span></span>](specify-a-disk-or-tape-as-a-backup-destination-sql-server.md)  
  
 <span data-ttu-id="6c0e8-264">**定义逻辑备份设备**</span><span class="sxs-lookup"><span data-stu-id="6c0e8-264">**To define a logical backup device**</span></span>  
  
-   [<span data-ttu-id="6c0e8-265">sp_addumpdevice (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6c0e8-265">sp_addumpdevice &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)  
  
-   [<span data-ttu-id="6c0e8-266">为磁盘文件定义逻辑备份设备 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6c0e8-266">Define a Logical Backup Device for a Disk File &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-disk-file-sql-server.md)  
  
-   [<span data-ttu-id="6c0e8-267">为磁带驱动器定义逻辑备份设备 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6c0e8-267">Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
-   <span data-ttu-id="6c0e8-268"><xref:Microsoft.SqlServer.Management.Smo.BackupDevice> (SMO)</span><span class="sxs-lookup"><span data-stu-id="6c0e8-268"><xref:Microsoft.SqlServer.Management.Smo.BackupDevice> (SMO)</span></span>  
  
 <span data-ttu-id="6c0e8-269">**使用逻辑备份设备**</span><span class="sxs-lookup"><span data-stu-id="6c0e8-269">**To use a logical backup device**</span></span>  
  
-   [<span data-ttu-id="6c0e8-270">将磁盘或磁带指定为备份目标 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6c0e8-270">Specify a Disk or Tape As a Backup Destination &#40;SQL Server&#41;</span></span>](specify-a-disk-or-tape-as-a-backup-destination-sql-server.md)  
  
-   [<span data-ttu-id="6c0e8-271">从设备还原备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6c0e8-271">Restore a Backup from a Device &#40;SQL Server&#41;</span></span>](restore-a-backup-from-a-device-sql-server.md)  
  
-   [<span data-ttu-id="6c0e8-272">BACKUP (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6c0e8-272">BACKUP &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/backup-transact-sql)  
  
-   [<span data-ttu-id="6c0e8-273">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6c0e8-273">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
 <span data-ttu-id="6c0e8-274">**查看有关备份设备的信息**</span><span class="sxs-lookup"><span data-stu-id="6c0e8-274">**To View Information About Backup Devices**</span></span>  
  
-   [<span data-ttu-id="6c0e8-275">备份历史记录和标头信息 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6c0e8-275">Backup History and Header Information &#40;SQL Server&#41;</span></span>](backup-history-and-header-information-sql-server.md)  
  
-   [<span data-ttu-id="6c0e8-276">查看逻辑备份设备的属性和内容 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6c0e8-276">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
-   [<span data-ttu-id="6c0e8-277">查看备份磁带或文件的内容 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6c0e8-277">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
 <span data-ttu-id="6c0e8-278">**删除逻辑备份设备**</span><span class="sxs-lookup"><span data-stu-id="6c0e8-278">**To delete a logical backup device**</span></span>  
  
-   [<span data-ttu-id="6c0e8-279">sp_dropdevice (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6c0e8-279">sp_dropdevice &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dropdevice-transact-sql)  
  
-   [<span data-ttu-id="6c0e8-280">删除备份设备 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6c0e8-280">Delete a Backup Device &#40;SQL Server&#41;</span></span>](delete-a-backup-device-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="6c0e8-281">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6c0e8-281">See Also</span></span>  
 <span data-ttu-id="6c0e8-282">[SQL Server Backup Device 对象](../performance-monitor/sql-server-backup-device-object.md) </span><span class="sxs-lookup"><span data-stu-id="6c0e8-282">[SQL Server, Backup Device Object](../performance-monitor/sql-server-backup-device-object.md) </span></span>  
 <span data-ttu-id="6c0e8-283">[BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6c0e8-283">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="6c0e8-284">[维护计划](../maintenance-plans/maintenance-plans.md) </span><span class="sxs-lookup"><span data-stu-id="6c0e8-284">[Maintenance Plans](../maintenance-plans/maintenance-plans.md) </span></span>  
 <span data-ttu-id="6c0e8-285">[媒体集、媒体簇和备份集 (SQL Server)](media-sets-media-families-and-backup-sets-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6c0e8-285">[Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md) </span></span>  
 <span data-ttu-id="6c0e8-286">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6c0e8-286">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="6c0e8-287">[RESTORE LABELONLY (Transact-SQL)](/sql/t-sql/statements/restore-statements-labelonly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6c0e8-287">[RESTORE LABELONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-labelonly-transact-sql) </span></span>  
 <span data-ttu-id="6c0e8-288">[sys.backup_devices (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6c0e8-288">[sys.backup_devices &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) </span></span>  
 <span data-ttu-id="6c0e8-289">[sys.dm_io_backup_tapes (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-io-backup-tapes-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6c0e8-289">[sys.dm_io_backup_tapes &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-io-backup-tapes-transact-sql) </span></span>  
 [<span data-ttu-id="6c0e8-290">镜像备份媒体集 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6c0e8-290">Mirrored Backup Media Sets &#40;SQL Server&#41;</span></span>](mirrored-backup-media-sets-sql-server.md)  
  
  
