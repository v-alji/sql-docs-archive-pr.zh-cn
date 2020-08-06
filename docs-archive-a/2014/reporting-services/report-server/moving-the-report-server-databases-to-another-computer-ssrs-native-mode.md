---
title: 将报表服务器数据库移动到其他计算机（SSRS 本机模式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 44a9854d-e333-44f6-bdc7-8837b9f34416
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 49fd35f57cf783b262b3c690e3047e5f479ab193
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682667"
---
# <a name="moving-the-report-server-databases-to-another-computer-ssrs-native-mode"></a><span data-ttu-id="3558c-102">将报表服务器数据库移至其他计算机（SSRS 本机模式）</span><span class="sxs-lookup"><span data-stu-id="3558c-102">Moving the Report Server Databases to Another Computer (SSRS Native Mode)</span></span>
  <span data-ttu-id="3558c-103">可以将安装中使用的 Report Server 数据库移动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 到其他计算机上的实例。</span><span class="sxs-lookup"><span data-stu-id="3558c-103">You can move the report server databases that are used in an installation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] to an instance that is on a different computer.</span></span> <span data-ttu-id="3558c-104">必须一同移动或复制数据库 reportserver 和数据库 reportservertempdb。</span><span class="sxs-lookup"><span data-stu-id="3558c-104">Both the reportserver and reportservertempdb databases must be moved or copied together.</span></span> <span data-ttu-id="3558c-105">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安装需要这两个数据库；reportservertempdb 数据库必须按名称与将要移动的 reportserver 主数据库相关。</span><span class="sxs-lookup"><span data-stu-id="3558c-105">A [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation requires both databases; the reportservertempdb database must be related by name to the primary reportserver database you are moving.</span></span>  
  
 <span data-ttu-id="3558c-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]本机模式。</span><span class="sxs-lookup"><span data-stu-id="3558c-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>  
  
 <span data-ttu-id="3558c-107">移动数据库不会影响当前为报表服务器项定义的计划操作。</span><span class="sxs-lookup"><span data-stu-id="3558c-107">Moving a database does not effect scheduled operations that are currently defined for report server items.</span></span>  
  
-   <span data-ttu-id="3558c-108">首次重新启动报表服务器服务时会重新创建计划。</span><span class="sxs-lookup"><span data-stu-id="3558c-108">Schedules will be recreated the first time that you restart the Report Server service.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="3558c-109">代理作业。</span><span class="sxs-lookup"><span data-stu-id="3558c-109">Agent jobs that are used to trigger a schedule will be recreated on the new database instance.</span></span> <span data-ttu-id="3558c-110">您不必将作业移到新计算机上，不过您可能需要删除计算机上不再使用的作业。</span><span class="sxs-lookup"><span data-stu-id="3558c-110">You do not have to move the jobs to the new computer, but you might want to delete jobs on the computer that will no longer be used.</span></span>  
  
-   <span data-ttu-id="3558c-111">订阅、缓存报表和快照将保留在移动的数据库中。</span><span class="sxs-lookup"><span data-stu-id="3558c-111">Subscriptions, cached reports, and snapshots are preserved in the moved database.</span></span> <span data-ttu-id="3558c-112">如果在数据库移动之后快照不选取刷新的数据，则在报表管理器中清除快照选项，单击“应用”保存更改，重新创建计划，然后再次单击“应用”保存所做的更改\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3558c-112">If a snapshot is not picking up refreshed data after the database is moved, clear the snapshot options in Report Manager, click **Apply** to save your changes, re-create the schedule, and click **Apply** again to save your changes.</span></span>  
  
-   <span data-ttu-id="3558c-113">移动数据库时，会保留 reportservertempdb 中存储的临时报表和用户会话数据。</span><span class="sxs-lookup"><span data-stu-id="3558c-113">Temporary report and user session data that is stored in reportservertempdb are persisted when you move that database.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="3558c-114">提供了多种移动数据库的方法，包括备份和还原、附加和分离以及复制。</span><span class="sxs-lookup"><span data-stu-id="3558c-114">provides several approaches for moving databases, including backup and restore, attach and detach, and copy.</span></span> <span data-ttu-id="3558c-115">并不是所有的方法都适用于将现有数据库重新定位到新的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="3558c-115">Not all approaches are appropriate for relocating an existing database to a new server instance.</span></span> <span data-ttu-id="3558c-116">根据您的系统可用性要求，移动报表服务器数据库的方法会有所不同。</span><span class="sxs-lookup"><span data-stu-id="3558c-116">The approach that you should use to move the report server database will vary depending on your system availability requirements.</span></span> <span data-ttu-id="3558c-117">移动报表服务器数据库的最简单方法是附加和分离数据库。</span><span class="sxs-lookup"><span data-stu-id="3558c-117">The easiest way to move the report server databases is to attach and detach them.</span></span> <span data-ttu-id="3558c-118">但是，此方法要求您在分离数据库的同时使报表服务器脱机。</span><span class="sxs-lookup"><span data-stu-id="3558c-118">However, this approach requires that you take the report server offline while you detach the database.</span></span> <span data-ttu-id="3558c-119">如果要最大程度地减少服务中断，则备份和还原是最佳选择，但是必须运行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 命令以执行操作。</span><span class="sxs-lookup"><span data-stu-id="3558c-119">Backup and restore is a better choice if you want to minimize service disruptions, but you must run [!INCLUDE[tsql](../../includes/tsql-md.md)] commands to perform the operations.</span></span> <span data-ttu-id="3558c-120">建议不要复制数据库（特别是不要使用复制数据库向导）；这样做将不保留数据库中的权限设置。</span><span class="sxs-lookup"><span data-stu-id="3558c-120">Copying the database is not recommended (specifically, by using the Copy Database Wizard); it does not preserve permission settings in the database.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3558c-121">当重新定位报表服务器数据库是对现有安装的唯一更改时，建议执行本主题中提供的步骤。</span><span class="sxs-lookup"><span data-stu-id="3558c-121">The steps provided in this topic are recommended when relocating the report server database is the only change you are making to the existing installation.</span></span> <span data-ttu-id="3558c-122">若要迁移整个 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安装（即，移动数据库并更改使用该数据库的报表服务器 Windows 服务的标识），需要重新配置连接并重置加密密钥。</span><span class="sxs-lookup"><span data-stu-id="3558c-122">Migrating an entire [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation (that is, moving the database and changing the identity of the Report Server Windows service that uses the database) requires connection reconfiguration and an encryption key reset.</span></span>  
  
## <a name="detaching-and-attaching-the-report-server-databases"></a><span data-ttu-id="3558c-123">分离和附加报表服务器数据库</span><span class="sxs-lookup"><span data-stu-id="3558c-123">Detaching and Attaching the Report Server Databases</span></span>  
 <span data-ttu-id="3558c-124">如果可使报表服务器脱机，则可分离数据库，以将其移至要使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="3558c-124">If you can take the report server offline, you can detach the databases to move them to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you want to use.</span></span> <span data-ttu-id="3558c-125">此方法将保留数据库中的权限。</span><span class="sxs-lookup"><span data-stu-id="3558c-125">This approach preserves permissions in the databases.</span></span> <span data-ttu-id="3558c-126">如果在使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 数据库，则必须将其移至另一个 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="3558c-126">If you are using a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] database, you must move it to another [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] instance.</span></span> <span data-ttu-id="3558c-127">移动数据库后，必须重新配置报表服务器与报表服务器数据库的连接。</span><span class="sxs-lookup"><span data-stu-id="3558c-127">After you move the databases, you must reconfigure the report server connection to the report server database.</span></span> <span data-ttu-id="3558c-128">如果您运行的是扩展部署，则必须为部署中的每个报表服务器重新配置报表服务器数据库连接。</span><span class="sxs-lookup"><span data-stu-id="3558c-128">If you are running a scale-out deployment, you must reconfigure the report server database connection for each report server in the deployment.</span></span>  
  
 <span data-ttu-id="3558c-129">请使用下列步骤来移动数据库：</span><span class="sxs-lookup"><span data-stu-id="3558c-129">Use the following steps to move the databases:</span></span>  
  
1.  <span data-ttu-id="3558c-130">为要移动的报表服务器数据库备份加密密钥。</span><span class="sxs-lookup"><span data-stu-id="3558c-130">Backup the encryption keys for the report server database you want to move.</span></span> <span data-ttu-id="3558c-131">可以使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置工具来备份密钥。</span><span class="sxs-lookup"><span data-stu-id="3558c-131">You can use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool backup the keys.</span></span>  
  
2.  <span data-ttu-id="3558c-132">停止报表服务器服务。</span><span class="sxs-lookup"><span data-stu-id="3558c-132">Stop the Report Server service.</span></span> <span data-ttu-id="3558c-133">可以使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置工具停止该服务。</span><span class="sxs-lookup"><span data-stu-id="3558c-133">You can use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool to stop the service.</span></span>  
  
3.  <span data-ttu-id="3558c-134">启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 并打开与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 承载 Report Server 数据库的实例的连接。</span><span class="sxs-lookup"><span data-stu-id="3558c-134">Start [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and open a connection to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that hosts the report server databases.</span></span>  
  
4.  <span data-ttu-id="3558c-135">右键单击该报表服务器数据库，指向“任务”，并单击“分离”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3558c-135">Right-click the report server database, point to Tasks, and click **Detach**.</span></span> <span data-ttu-id="3558c-136">对报表服务器临时数据库重复此步骤。</span><span class="sxs-lookup"><span data-stu-id="3558c-136">Repeat this step for the report server temporary database.</span></span>  
  
5.  <span data-ttu-id="3558c-137">将 .mdf 和 .ldf 文件复制或移至要使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的 Data 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="3558c-137">Copy or move the .mdf and .ldf files to the Data folder of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you want to use.</span></span> <span data-ttu-id="3558c-138">由于要移动两个数据库，因此请确保移动或复制所有四个文件。</span><span class="sxs-lookup"><span data-stu-id="3558c-138">Because you are moving two databases, make sure that you move or copy all four files.</span></span>  
  
6.  <span data-ttu-id="3558c-139">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中，打开与将承载报表服务器数据库的新 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的连接。</span><span class="sxs-lookup"><span data-stu-id="3558c-139">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], open a connection to the new [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that will host the report server databases.</span></span>  
  
7.  <span data-ttu-id="3558c-140">右键单击“数据库”节点，然后单击“附加”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3558c-140">Right-click the Databases node, and then click **Attach**.</span></span>  
  
8.  <span data-ttu-id="3558c-141">单击 **“添加”** 以选择要附加的报表服务器数据库 .mdf 和 .ldf 文件。</span><span class="sxs-lookup"><span data-stu-id="3558c-141">Click **Add** to select the report server database .mdf and .ldf files that you want to attach.</span></span> <span data-ttu-id="3558c-142">对报表服务器临时数据库重复此步骤。</span><span class="sxs-lookup"><span data-stu-id="3558c-142">Repeat this step for the report server temporary database.</span></span>  
  
9. <span data-ttu-id="3558c-143">附加数据库后，验证 `RSExecRole` 是否是 Report Server 数据库和临时数据库中的数据库角色。</span><span class="sxs-lookup"><span data-stu-id="3558c-143">After the databases are attached, verify that the `RSExecRole` is a database role in the report server database and temporary database.</span></span> <span data-ttu-id="3558c-144">`RSExecRole`必须对 Report Server 数据库表具有 select、insert、update、delete 和 reference 权限，以及对存储过程的 execute 权限。</span><span class="sxs-lookup"><span data-stu-id="3558c-144">`RSExecRole` must have select, insert, update, delete, and reference permissions on the report server database tables, and execute permissions on the stored procedures.</span></span> <span data-ttu-id="3558c-145">有关详细信息，请参阅 [创建 RSExecRole](../security/create-the-rsexecrole.md)。</span><span class="sxs-lookup"><span data-stu-id="3558c-145">For more information, see [Create the RSExecRole](../security/create-the-rsexecrole.md).</span></span>  
  
10. <span data-ttu-id="3558c-146">启动 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置工具并打开与报表服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="3558c-146">Start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool and open a connection to the report server.</span></span>  
  
11. <span data-ttu-id="3558c-147">在“数据库”页上，选择新的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例，然后单击 **“连接”**。</span><span class="sxs-lookup"><span data-stu-id="3558c-147">On the Database page, select the new [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance, and then click **Connect**.</span></span>  
  
12. <span data-ttu-id="3558c-148">选择刚才移动的报表服务器数据库，然后单击 **“应用”**。</span><span class="sxs-lookup"><span data-stu-id="3558c-148">Select the report server database that you just moved, and then click **Apply**.</span></span>  
  
13. <span data-ttu-id="3558c-149">在“加密密钥”页上，单击“还原”。</span><span class="sxs-lookup"><span data-stu-id="3558c-149">On the Encryption Keys page, click Restore.</span></span> <span data-ttu-id="3558c-150">指定包含密钥备份副本的文件以及该文件的解锁密码。</span><span class="sxs-lookup"><span data-stu-id="3558c-150">Specify the file that contains the backup copy of the keys and the password to unlock the file.</span></span>  
  
14. <span data-ttu-id="3558c-151">重新启动报表服务器服务。</span><span class="sxs-lookup"><span data-stu-id="3558c-151">Restart the Report Server service.</span></span>  
  
## <a name="backing-up-and-restoring-the-report-server-databases"></a><span data-ttu-id="3558c-152">备份和还原报表服务器数据库</span><span class="sxs-lookup"><span data-stu-id="3558c-152">Backing Up and Restoring the Report Server Databases</span></span>  
 <span data-ttu-id="3558c-153">如果不能使报表服务器脱机，则可使用备份和还原来重新定位报表服务器数据库。</span><span class="sxs-lookup"><span data-stu-id="3558c-153">If you cannot take the report server offline, you can use backup and restore to relocate the report server databases.</span></span> <span data-ttu-id="3558c-154">您必须使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句执行备份和还原。</span><span class="sxs-lookup"><span data-stu-id="3558c-154">You must use [!INCLUDE[tsql](../../includes/tsql-md.md)] statements to do the backup and restore.</span></span> <span data-ttu-id="3558c-155">还原数据库后，必须将报表服务器配置为使用新服务器实例上的数据库。</span><span class="sxs-lookup"><span data-stu-id="3558c-155">After you restore the databases, you must configure the report server to use the database on the new server instance.</span></span> <span data-ttu-id="3558c-156">有关详细信息，请参阅本主题结尾的说明。</span><span class="sxs-lookup"><span data-stu-id="3558c-156">For more information, see the instructions at the end of this topic.</span></span>  
  
### <a name="using-backup-and-copy_only-to-backup-the-report-server-databases"></a><span data-ttu-id="3558c-157">使用 BACKUP 和 COPY_ONLY 备份报表服务器数据库</span><span class="sxs-lookup"><span data-stu-id="3558c-157">Using BACKUP and COPY_ONLY to Backup the Report Server Databases</span></span>  
 <span data-ttu-id="3558c-158">备份数据库时，请设置 COPY_ONLY 参数。</span><span class="sxs-lookup"><span data-stu-id="3558c-158">When backing up the databases, set the COPY_ONLY argument.</span></span> <span data-ttu-id="3558c-159">请确保备份数据库和日志文件。</span><span class="sxs-lookup"><span data-stu-id="3558c-159">Be sure to back up both of the databases and log files.</span></span>  
  
```  
-- To permit log backups, before the full database backup, alter the database   
-- to use the full recovery model.  
USE master;  
GO  
ALTER DATABASE ReportServer  
   SET RECOVERY FULL  
  
-- If the ReportServerData device does not exist yet, create it.   
USE master  
GO  
EXEC sp_addumpdevice 'disk', 'ReportServerData',   
'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\BACKUP\ReportServerData.bak'  
  
-- Create a logical backup device, ReportServerLog.  
USE master  
GO  
EXEC sp_addumpdevice 'disk', 'ReportServerLog',   
'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\BACKUP\ReportServerLog.bak'  
  
-- Back up the full ReportServer database.  
BACKUP DATABASE ReportServer  
   TO ReportServerData  
   WITH COPY_ONLY  
  
-- Back up the ReportServer log.  
BACKUP LOG ReportServer  
   TO ReportServerLog  
   WITH COPY_ONLY  
  
-- To permit log backups, before the full database backup, alter the database   
-- to use the full recovery model.  
USE master;  
GO  
ALTER DATABASE ReportServerTempdb  
   SET RECOVERY FULL  
  
-- If the ReportServerTempDBData device does not exist yet, create it.   
USE master  
GO  
EXEC sp_addumpdevice 'disk', 'ReportServerTempDBData',   
'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\BACKUP\ReportServerTempDBData.bak'  
  
-- Create a logical backup device, ReportServerTempDBLog.  
USE master  
GO  
EXEC sp_addumpdevice 'disk', 'ReportServerTempDBLog',   
'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\BACKUP\ReportServerTempDBLog.bak'  
  
-- Back up the full ReportServerTempDB database.  
BACKUP DATABASE ReportServerTempDB  
   TO ReportServerTempDBData  
   WITH COPY_ONLY  
  
-- Back up the ReportServerTempDB log.  
BACKUP LOG ReportServerTempDB  
   TO ReportServerTempDBLog  
   WITH COPY_ONLY  
```  
  
### <a name="using-restore-and-move-to-relocate-the-report-server-databases"></a><span data-ttu-id="3558c-160">使用 RESTORE 和 MOVE 重新定位报表服务器数据库</span><span class="sxs-lookup"><span data-stu-id="3558c-160">Using RESTORE and MOVE to Relocate the Report Server Databases</span></span>  
 <span data-ttu-id="3558c-161">还原数据库时，请务必包括 MOVE 参数，以便指定路径。</span><span class="sxs-lookup"><span data-stu-id="3558c-161">When restoring the databases, be sure to include the MOVE argument so that you can specify a path.</span></span> <span data-ttu-id="3558c-162">使用 NORECOVERY 参数执行初始还原；此操作可使数据库保持 RESTORING 状态，给您留出时间来检查日志备份，以确定要还原的备份。</span><span class="sxs-lookup"><span data-stu-id="3558c-162">Use the NORECOVERY argument to perform the initial restore; this keeps the database in a RESTORING state, giving you time to review log backups to determine which one to restore.</span></span> <span data-ttu-id="3558c-163">最后一步是重复包含 RECOVERY 参数的 RESTORE 操作。</span><span class="sxs-lookup"><span data-stu-id="3558c-163">The final step repeats the RESTORE operation with the RECOVERY argument.</span></span>  
  
 <span data-ttu-id="3558c-164">MOVE 参数使用数据文件的逻辑名称。</span><span class="sxs-lookup"><span data-stu-id="3558c-164">The MOVE argument uses the logical name of the data file.</span></span> <span data-ttu-id="3558c-165">若要找到逻辑名称，请执行下列语句： `RESTORE FILELISTONLY FROM DISK='C:\ReportServerData.bak';`</span><span class="sxs-lookup"><span data-stu-id="3558c-165">To find the logical name, execute the following statement: `RESTORE FILELISTONLY FROM DISK='C:\ReportServerData.bak';`</span></span>  
  
 <span data-ttu-id="3558c-166">以下示例包括 FILE 参数，因此您可以指定要还原的日志文件的文件位置。</span><span class="sxs-lookup"><span data-stu-id="3558c-166">The following examples include the FILE argument so that you can specify the file position of the log file to restore.</span></span> <span data-ttu-id="3558c-167">若要找到文件位置，请执行下列语句： `RESTORE HEADERONLY FROM DISK='C:\ReportServerData.bak';`</span><span class="sxs-lookup"><span data-stu-id="3558c-167">To find the file position, execute the following statement: `RESTORE HEADERONLY FROM DISK='C:\ReportServerData.bak';`</span></span>  
  
 <span data-ttu-id="3558c-168">还原数据库和日志文件时，应单独运行每个 RESTORE 操作。</span><span class="sxs-lookup"><span data-stu-id="3558c-168">When restoring the database and log files, you should run each RESTORE operation separately.</span></span>  
  
```  
-- Restore the report server database and move to new instance folder   
RESTORE DATABASE ReportServer  
   FROM DISK='C:\ReportServerData.bak'  
   WITH NORECOVERY,   
      MOVE 'ReportServer' TO   
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\ReportServer.mdf',   
      MOVE 'ReportServer_log' TO  
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\ReportServer_Log.ldf';  
GO  
  
-- Restore the report server log file to new instance folder   
RESTORE LOG ReportServer  
   FROM DISK='C:\ReportServerData.bak'  
   WITH NORECOVERY, FILE=2  
      MOVE 'ReportServer' TO   
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\ReportServer.mdf',   
      MOVE 'ReportServer_log' TO  
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\ReportServer_Log.ldf';  
GO  
  
-- Restore and move the report server temporary database  
RESTORE DATABASE ReportServerTempdb  
   FROM DISK='C:\ReportServerTempDBData.bak'  
   WITH NORECOVERY,   
      MOVE 'ReportServerTempDB' TO   
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\ReportServerTempDB.mdf',   
      MOVE 'ReportServerTempDB_log' TO  
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\REportServerTempDB_Log.ldf';  
GO  
  
-- Restore the temporary database log file to new instance folder   
RESTORE LOG ReportServerTempdb  
   FROM DISK='C:\ReportServerTempDBData.bak'  
   WITH NORECOVERY, FILE=2  
      MOVE 'ReportServerTempDB' TO   
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\ReportServerTempDB.mdf',   
      MOVE 'ReportServerTempDB_log' TO  
         'C:\Program Files\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Data\REportServerTempDB_Log.ldf';  
GO  
  
-- Perform final restore  
RESTORE DATABASE ReportServer  
   WITH RECOVERY  
GO  
  
-- Perform final restore  
RESTORE DATABASE ReportServerTempDB  
   WITH RECOVERY  
GO  
```  
  
### <a name="how-to-configure-the-report-server-database-connection"></a><span data-ttu-id="3558c-169">如何配置报表服务器数据库连接</span><span class="sxs-lookup"><span data-stu-id="3558c-169">How to Configure the Report Server Database Connection</span></span>  
  
1.  <span data-ttu-id="3558c-170">启动 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置管理器并连接到报表服务器。</span><span class="sxs-lookup"><span data-stu-id="3558c-170">Start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager and open a connection to the report server.</span></span>  
  
2.  <span data-ttu-id="3558c-171">在“数据库”页上，单击 **“更改数据库”**。</span><span class="sxs-lookup"><span data-stu-id="3558c-171">On the Database page, click **Change Database**.</span></span> <span data-ttu-id="3558c-172">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="3558c-172">Click **Next**.</span></span>  
  
3.  <span data-ttu-id="3558c-173">单击 **“选择现有报表服务器数据库”**。</span><span class="sxs-lookup"><span data-stu-id="3558c-173">Click **Choose an existing report server database**.</span></span> <span data-ttu-id="3558c-174">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="3558c-174">Click **Next**.</span></span>  
  
4.  <span data-ttu-id="3558c-175">选择现在承载报表服务器数据库的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，并单击 **“测试连接”**。</span><span class="sxs-lookup"><span data-stu-id="3558c-175">Select the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that now hosts the report server database and click **Test Connection**.</span></span> <span data-ttu-id="3558c-176">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="3558c-176">Click **Next**.</span></span>  
  
5.  <span data-ttu-id="3558c-177">在“数据库名称”中，选择要使用的报表服务器数据库。</span><span class="sxs-lookup"><span data-stu-id="3558c-177">In Database Name, select the report server database that you want to use.</span></span> <span data-ttu-id="3558c-178">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="3558c-178">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="3558c-179">在“凭据”中，指定报表服务器用来连接到报表服务器数据库的凭据。</span><span class="sxs-lookup"><span data-stu-id="3558c-179">In Credentials, specify the credentials that the report server will use to connect to the report server database.</span></span> <span data-ttu-id="3558c-180">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="3558c-180">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="3558c-181">单击 **“下一步”** ，然后单击 **“完成”**。</span><span class="sxs-lookup"><span data-stu-id="3558c-181">Click **Next** and then **Finish**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3558c-182">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安装要求 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]实例包含 `RSExecRole` 角色。</span><span class="sxs-lookup"><span data-stu-id="3558c-182">A [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation requires that the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] instance include the `RSExecRole` role.</span></span> <span data-ttu-id="3558c-183">通过 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置工具设置报表服务器数据库连接时，将创建角色、注册登录信息并分配角色。</span><span class="sxs-lookup"><span data-stu-id="3558c-183">Role creation, login registration, and role assignments occur when you set the report server database connection through the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool.</span></span> <span data-ttu-id="3558c-184">如果使用备用方法（具体来说，如果使用 rsconfig.exe 命令提示实用工具）来配置连接，报表服务器不会处于工作状态。</span><span class="sxs-lookup"><span data-stu-id="3558c-184">If you use alternate approaches (specifically, if you use the rsconfig.exe command prompt utility) to configure the connection, the report server will not be in a working state.</span></span> <span data-ttu-id="3558c-185">您可能需要编写 WMI 代码以使报表服务器可用。</span><span class="sxs-lookup"><span data-stu-id="3558c-185">You might have to write WMI code to make the report server available.</span></span> <span data-ttu-id="3558c-186">有关详细信息，请参阅 [访问 Reporting Services WMI 提供程序](../tools/access-the-reporting-services-wmi-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="3558c-186">For more information, see [Access the Reporting Services WMI Provider](../tools/access-the-reporting-services-wmi-provider.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3558c-187">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3558c-187">See Also</span></span>  
 <span data-ttu-id="3558c-188">[创建 RSExecRole](../security/create-the-rsexecrole.md) </span><span class="sxs-lookup"><span data-stu-id="3558c-188">[Create the RSExecRole](../security/create-the-rsexecrole.md) </span></span>  
 <span data-ttu-id="3558c-189">[启动和停止报表服务器服务](start-and-stop-the-report-server-service.md) </span><span class="sxs-lookup"><span data-stu-id="3558c-189">[Start and Stop the Report Server Service](start-and-stop-the-report-server-service.md) </span></span>  
 <span data-ttu-id="3558c-190">[&#40;SSRS Configuration Manager 配置报表服务器数据库连接&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="3558c-190">[Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="3558c-191">[&#40;SSRS Configuration Manager 配置无人参与的执行帐户&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="3558c-191">[Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="3558c-192">[Reporting Services Configuration Manager（本机模式）](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="3558c-192">[Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md) </span></span>  
 <span data-ttu-id="3558c-193">[rsconfig 实用工具 &#40;SSRS&#41;](../tools/rsconfig-utility-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3558c-193">[rsconfig Utility &#40;SSRS&#41;](../tools/rsconfig-utility-ssrs.md) </span></span>  
 <span data-ttu-id="3558c-194">[&#40;SSRS Configuration Manager 中配置和管理加密密钥&#41;](../install-windows/ssrs-encryption-keys-manage-encryption-keys.md) </span><span class="sxs-lookup"><span data-stu-id="3558c-194">[Configure and Manage Encryption Keys &#40;SSRS Configuration Manager&#41;](../install-windows/ssrs-encryption-keys-manage-encryption-keys.md) </span></span>  
 [<span data-ttu-id="3558c-195">报表服务器数据库（SSRS 本机模式）</span><span class="sxs-lookup"><span data-stu-id="3558c-195">Report Server Database &#40;SSRS Native Mode&#41;</span></span>](report-server-database-ssrs-native-mode.md)  
  
  
