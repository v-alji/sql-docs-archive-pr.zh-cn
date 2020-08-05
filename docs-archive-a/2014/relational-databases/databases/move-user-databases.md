---
title: 移动用户数据库 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- disaster recovery [SQL Server], moving database files
- database files [SQL Server], moving
- data files [SQL Server], moving
- editions [SQL Server], moving databases between
- moving full-text catalogs
- scheduled disk maintenace [SQL Server]
- moving databases
- full-text catalogs [SQL Server], moving
- moving database files
- moving user databases
- relocating database files
- planned database relocations [SQL Server]
- databases [SQL Server], moving
ms.assetid: ad9a4e92-13fb-457d-996a-66ffc2d55b79
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6c2b82c3bec13c82aa30aebd175ef78f8136ee04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581293"
---
# <a name="move-user-databases"></a><span data-ttu-id="f1ae9-102">移动用户数据库</span><span class="sxs-lookup"><span data-stu-id="f1ae9-102">Move User Databases</span></span>
  <span data-ttu-id="f1ae9-103">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中，通过在 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) 语句的 FILENAME 子句中指定新的文件位置，可以将用户数据库中的数据、日志和全文目录文件移动到新位置。</span><span class="sxs-lookup"><span data-stu-id="f1ae9-103">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you can move the data, log, and full-text catalog files of a user database to a new location by specifying the new file location in the FILENAME clause of the [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) statement.</span></span> <span data-ttu-id="f1ae9-104">此方法适用于在同一 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例中移动数据库文件。</span><span class="sxs-lookup"><span data-stu-id="f1ae9-104">This method applies to moving database files within the same instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f1ae9-105">若要将数据库移动到另一个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例或另一台服务器上，请使用 [备份和还原](../backup-restore/back-up-and-restore-of-sql-server-databases.md) 或 [分离和附加操作](move-a-database-using-detach-and-attach-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="f1ae9-105">To move a database to another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or to another server, use [backup and restore](../backup-restore/back-up-and-restore-of-sql-server-databases.md) or [detach and attach operations](move-a-database-using-detach-and-attach-transact-sql.md).</span></span>  
  
## <a name="considerations"></a><span data-ttu-id="f1ae9-106">注意事项</span><span class="sxs-lookup"><span data-stu-id="f1ae9-106">Considerations</span></span>  
 <span data-ttu-id="f1ae9-107">将数据库移动到另一个服务器实例上时，若要为用户和应用程序提供一致的体验，您可能需要为数据库重新创建部分或全部元数据。</span><span class="sxs-lookup"><span data-stu-id="f1ae9-107">When you move a database onto another server instance, to provide a consistent experience to users and applications, you might have to re-create some or all the metadata for the database.</span></span> <span data-ttu-id="f1ae9-108">有关详细信息，请参阅 [当数据库在其他服务器实例上可用时管理元数据 (SQL Server)](manage-metadata-when-making-a-database-available-on-another-server.md)。</span><span class="sxs-lookup"><span data-stu-id="f1ae9-108">For more information, see [Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](manage-metadata-when-making-a-database-available-on-another-server.md).</span></span>  
  
 <span data-ttu-id="f1ae9-109">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的某些功能改变了[!INCLUDE[ssDE](../../includes/ssde-md.md)]在数据库文件中存储信息的方式。</span><span class="sxs-lookup"><span data-stu-id="f1ae9-109">Some features of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] change the way that the [!INCLUDE[ssDE](../../includes/ssde-md.md)] stores information in the database files.</span></span> <span data-ttu-id="f1ae9-110">这些功能仅限于特定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]版本。</span><span class="sxs-lookup"><span data-stu-id="f1ae9-110">These features are restricted to specific editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f1ae9-111">不能将包含这些功能的数据库移到不支持这些功能的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本。</span><span class="sxs-lookup"><span data-stu-id="f1ae9-111">A database that contains these features cannot be moved to an edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that does not support them.</span></span> <span data-ttu-id="f1ae9-112">使用 sys.dm_db_persisted_sku_features 动态管理视图可列出当前数据库中启用的所有特定于版本的功能。</span><span class="sxs-lookup"><span data-stu-id="f1ae9-112">Use the sys.dm_db_persisted_sku_features dynamic management view to list all edition-specific features that are enabled in the current database.</span></span>  
  
 <span data-ttu-id="f1ae9-113">本主题中的过程需要数据库文件的逻辑名称。</span><span class="sxs-lookup"><span data-stu-id="f1ae9-113">The procedures in this topic require the logical name of the database files.</span></span> <span data-ttu-id="f1ae9-114">若要获取该名称，请在 [sys.master_files](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql) 目录视图中查询名称列。</span><span class="sxs-lookup"><span data-stu-id="f1ae9-114">To obtain the name, query the name column in the [sys.master_files](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql) catalog view.</span></span>  
  
 <span data-ttu-id="f1ae9-115">从 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]开始，全文目录已集成到数据库中，而不是存储在文件系统中。</span><span class="sxs-lookup"><span data-stu-id="f1ae9-115">Starting with [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], full-text catalogs are integrated into the database rather than being stored in the file system.</span></span> <span data-ttu-id="f1ae9-116">现在移动数据库时将自动移动全文目录。</span><span class="sxs-lookup"><span data-stu-id="f1ae9-116">The full-text catalogs now move automatically when you move a database.</span></span>  
  
## <a name="planned-relocation-procedure"></a><span data-ttu-id="f1ae9-117">计划的重定位过程</span><span class="sxs-lookup"><span data-stu-id="f1ae9-117">Planned Relocation Procedure</span></span>  
 <span data-ttu-id="f1ae9-118">若要将移动数据或日志文件作为计划的重定位的一部分，请执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="f1ae9-118">To move a data or log file as part of a planned relocation, follow these steps:</span></span>  
  
1.  <span data-ttu-id="f1ae9-119">运行以下语句。</span><span class="sxs-lookup"><span data-stu-id="f1ae9-119">Run the following statement.</span></span>  
  
    ```  
    ALTER DATABASE database_name SET OFFLINE;  
    ```  
  
2.  <span data-ttu-id="f1ae9-120">将文件移动到新位置。</span><span class="sxs-lookup"><span data-stu-id="f1ae9-120">Move the file or files to the new location.</span></span>  
  
3.  <span data-ttu-id="f1ae9-121">对于已移动的每个文件，请运行以下语句。</span><span class="sxs-lookup"><span data-stu-id="f1ae9-121">For each file moved, run the following statement.</span></span>  
  
    ```  
    ALTER DATABASE database_name MODIFY FILE ( NAME = logical_name, FILENAME = 'new_path\os_file_name' );  
    ```  
  
4.  <span data-ttu-id="f1ae9-122">运行以下语句。</span><span class="sxs-lookup"><span data-stu-id="f1ae9-122">Run the following statement.</span></span>  
  
    ```  
    ALTER DATABASE database_name SET ONLINE;  
    ```  
  
5.  <span data-ttu-id="f1ae9-123">通过运行以下查询来验证文件更改。</span><span class="sxs-lookup"><span data-stu-id="f1ae9-123">Verify the file change by running the following query.</span></span>  
  
    ```  
    SELECT name, physical_name AS CurrentLocation, state_desc  
    FROM sys.master_files  
    WHERE database_id = DB_ID(N'<database_name>');  
    ```  
  
## <a name="relocation-for-scheduled-disk-maintenance"></a><span data-ttu-id="f1ae9-124">计划的磁盘维护的重定位</span><span class="sxs-lookup"><span data-stu-id="f1ae9-124">Relocation for Scheduled Disk Maintenance</span></span>  
 <span data-ttu-id="f1ae9-125">若要将重定位文件作为计划的磁盘维护过程的一部分，请执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="f1ae9-125">To relocate a file as part of a scheduled disk maintenance process, follow these steps:</span></span>  
  
1.  <span data-ttu-id="f1ae9-126">对于要移动的每个文件，请运行以下语句。</span><span class="sxs-lookup"><span data-stu-id="f1ae9-126">For each file to be moved, run the following statement.</span></span>  
  
    ```  
    ALTER DATABASE database_name MODIFY FILE ( NAME = logical_name , FILENAME = 'new_path\os_file_name' );  
    ```  
  
2.  <span data-ttu-id="f1ae9-127">停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例或关闭系统以执行维护。</span><span class="sxs-lookup"><span data-stu-id="f1ae9-127">Stop the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or shut down the system to perform maintenance.</span></span> <span data-ttu-id="f1ae9-128">有关详细信息，请参阅 [启动、停止、暂停、继续、重启 SQL Server 服务](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)。</span><span class="sxs-lookup"><span data-stu-id="f1ae9-128">For more information, see [Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md).</span></span>  
  
3.  <span data-ttu-id="f1ae9-129">将文件移动到新位置。</span><span class="sxs-lookup"><span data-stu-id="f1ae9-129">Move the file or files to the new location.</span></span>  
  
4.  <span data-ttu-id="f1ae9-130">重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例或服务器。</span><span class="sxs-lookup"><span data-stu-id="f1ae9-130">Restart the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or the server.</span></span> <span data-ttu-id="f1ae9-131">有关详细信息，请参阅 [启动、停止、暂停、继续、重新启动数据库引擎、SQL Server 代理或 SQL Server Browser 服务](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)</span><span class="sxs-lookup"><span data-stu-id="f1ae9-131">For more information, see [Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)</span></span>  
  
5.  <span data-ttu-id="f1ae9-132">通过运行以下查询来验证文件更改。</span><span class="sxs-lookup"><span data-stu-id="f1ae9-132">Verify the file change by running the following query.</span></span>  
  
    ```  
    SELECT name, physical_name AS CurrentLocation, state_desc  
    FROM sys.master_files  
    WHERE database_id = DB_ID(N'<database_name>');  
    ```  
  
## <a name="failure-recovery-procedure"></a><span data-ttu-id="f1ae9-133">故障恢复过程</span><span class="sxs-lookup"><span data-stu-id="f1ae9-133">Failure Recovery Procedure</span></span>  
 <span data-ttu-id="f1ae9-134">如果由于硬件故障而必须移动文件，则请执行下列步骤，将文件重新定位到一个新位置。</span><span class="sxs-lookup"><span data-stu-id="f1ae9-134">If a file must be moved because of a hardware failure, use the following steps to relocate the file to a new location.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f1ae9-135">如果数据库无法启动，即处于可疑模式下或处于未恢复状态，则只有 sysadmin 固定角色的成员才可以移动该文件。</span><span class="sxs-lookup"><span data-stu-id="f1ae9-135">If the database cannot be started, that is it is in suspect mode or in an unrecovered state, only members of the sysadmin fixed role can move the file.</span></span>  
  
1.  <span data-ttu-id="f1ae9-136">如果启动了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例，则将其停止。</span><span class="sxs-lookup"><span data-stu-id="f1ae9-136">Stop the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] if it is started.</span></span>  
  
2.  <span data-ttu-id="f1ae9-137">通过在命令提示符下输入下列命令之一，在仅 master 恢复模式下启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="f1ae9-137">Start the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in master-only recovery mode by entering one of the following commands at the command prompt.</span></span>  
  
    -   <span data-ttu-id="f1ae9-138">对于默认的 (MSSQLSERVER) 实例，请运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="f1ae9-138">For the default (MSSQLSERVER) instance, run the following command.</span></span>  
  
        ```  
        NET START MSSQLSERVER /f /T3608  
        ```  
  
    -   <span data-ttu-id="f1ae9-139">对于命名实例，请运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="f1ae9-139">For a named instance, run the following command.</span></span>  
  
        ```  
        NET START MSSQL$instancename /f /T3608  
        ```  
  
     <span data-ttu-id="f1ae9-140">有关详细信息，请参阅 [启动、停止、暂停、继续、重启 SQL Server 服务](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)。</span><span class="sxs-lookup"><span data-stu-id="f1ae9-140">For more information, see [Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md).</span></span>  
  
3.  <span data-ttu-id="f1ae9-141">对于要移动的每个文件，请使用 **sqlcmd** 命令或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 运行以下语句。</span><span class="sxs-lookup"><span data-stu-id="f1ae9-141">For each file to be moved, use **sqlcmd** commands or [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] to run the following statement.</span></span>  
  
    ```  
    ALTER DATABASE database_name MODIFY FILE( NAME = logical_name , FILENAME = 'new_path\os_file_name' );  
    ```  
  
     <span data-ttu-id="f1ae9-142">有关如何使用 **sqlcmd** 实用工具的详细信息，请参阅 [使用 sqlcmd 实用工具](../scripting/sqlcmd-use-the-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="f1ae9-142">For more information about how to use the **sqlcmd** utility, see [Use the sqlcmd Utility](../scripting/sqlcmd-use-the-utility.md).</span></span>  
  
4.  <span data-ttu-id="f1ae9-143">退出 **sqlcmd** 实用工具或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f1ae9-143">Exit the **sqlcmd** utility or [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span>  
  
5.  <span data-ttu-id="f1ae9-144">停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例。</span><span class="sxs-lookup"><span data-stu-id="f1ae9-144">Stop the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
6.  <span data-ttu-id="f1ae9-145">将文件移动到新位置。</span><span class="sxs-lookup"><span data-stu-id="f1ae9-145">Move the file or files to the new location.</span></span>  
  
7.  <span data-ttu-id="f1ae9-146">启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例。</span><span class="sxs-lookup"><span data-stu-id="f1ae9-146">Start the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f1ae9-147">例如，运行 `NET START MSSQLSERVER`。</span><span class="sxs-lookup"><span data-stu-id="f1ae9-147">For example, run: `NET START MSSQLSERVER`.</span></span>  
  
8.  <span data-ttu-id="f1ae9-148">通过运行以下查询来验证文件更改。</span><span class="sxs-lookup"><span data-stu-id="f1ae9-148">Verify the file change by running the following query.</span></span>  
  
    ```  
    SELECT name, physical_name AS CurrentLocation, state_desc  
    FROM sys.master_files  
    WHERE database_id = DB_ID(N'<database_name>');  
    ```  
  
## <a name="examples"></a><span data-ttu-id="f1ae9-149">示例</span><span class="sxs-lookup"><span data-stu-id="f1ae9-149">Examples</span></span>  
 <span data-ttu-id="f1ae9-150">下面的示例将 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 日志文件移动到一个新位置，作为计划的重定位的一部分。</span><span class="sxs-lookup"><span data-stu-id="f1ae9-150">The following example moves the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] log file to a new location as part of a planned relocation.</span></span>  
  
```  
USE master;  
GO  
-- Return the logical file name.  
SELECT name, physical_name AS CurrentLocation, state_desc  
FROM sys.master_files  
WHERE database_id = DB_ID(N'AdventureWorks2012')  
    AND type_desc = N'LOG';  
GO  
ALTER DATABASE AdventureWorks2012 SET OFFLINE;  
GO  
-- Physically move the file to a new location.  
-- In the following statement, modify the path specified in FILENAME to  
-- the new location of the file on your server.  
ALTER DATABASE AdventureWorks2012   
    MODIFY FILE ( NAME = AdventureWorks2012_Log,   
                  FILENAME = 'C:\NewLoc\AdventureWorks2012_Log.ldf');  
GO  
ALTER DATABASE AdventureWorks2012 SET ONLINE;  
GO  
--Verify the new location.  
SELECT name, physical_name AS CurrentLocation, state_desc  
FROM sys.master_files  
WHERE database_id = DB_ID(N'AdventureWorks2012')  
    AND type_desc = N'LOG';  
```  
  
## <a name="see-also"></a><span data-ttu-id="f1ae9-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f1ae9-151">See Also</span></span>  
 <span data-ttu-id="f1ae9-152">[ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f1ae9-152">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="f1ae9-153">[CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f1ae9-153">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 <span data-ttu-id="f1ae9-154">[数据库分离和附加 (SQL Server)](database-detach-and-attach-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f1ae9-154">[Database Detach and Attach &#40;SQL Server&#41;](database-detach-and-attach-sql-server.md) </span></span>  
 <span data-ttu-id="f1ae9-155">[移动系统数据库](system-databases.md) </span><span class="sxs-lookup"><span data-stu-id="f1ae9-155">[Move System Databases](system-databases.md) </span></span>  
 <span data-ttu-id="f1ae9-156">[移动数据库文件](move-database-files.md) </span><span class="sxs-lookup"><span data-stu-id="f1ae9-156">[Move Database Files](move-database-files.md) </span></span>  
 <span data-ttu-id="f1ae9-157">[BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f1ae9-157">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="f1ae9-158">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f1ae9-158">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="f1ae9-159">启动、停止、暂停、继续、重新启动数据库引擎、SQL Server 代理或 SQL Server Browser 服务</span><span class="sxs-lookup"><span data-stu-id="f1ae9-159">Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service</span></span>](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)  
  
  
