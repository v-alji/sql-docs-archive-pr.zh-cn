---
title: 移动系统数据库 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- moving system databases
- disaster recovery [SQL Server], moving database files
- database files [SQL Server], moving
- data files [SQL Server], moving
- tempdb database [SQL Server], moving
- system databases [SQL Server], moving
- scheduled disk maintenace [SQL Server]
- moving databases
- msdb database [SQL Server], moving
- moving database files
- relocating database files
- planned database relocations [SQL Server]
- master database [SQL Server], moving
- model database [SQL Server], moving
- Resource database [SQL Server]
- databases [SQL Server], moving
ms.assetid: 72bb62ee-9602-4f71-be51-c466c1670878
author: stevestein
ms.author: sstein
ms.openlocfilehash: 748d781d6bbefb0dc710427a34ebd71ec7037fdb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694502"
---
# <a name="move-system-databases"></a><span data-ttu-id="d514e-102">移动系统数据库</span><span class="sxs-lookup"><span data-stu-id="d514e-102">Move System Databases</span></span>
  <span data-ttu-id="d514e-103">本主题说明如何在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中移动系统数据库。</span><span class="sxs-lookup"><span data-stu-id="d514e-103">This topic describes how to move system databases in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d514e-104">移动系统数据库在下列情况下可能很有用：</span><span class="sxs-lookup"><span data-stu-id="d514e-104">Moving system databases may be useful in the following situations:</span></span>  
  
-   <span data-ttu-id="d514e-105">故障恢复。</span><span class="sxs-lookup"><span data-stu-id="d514e-105">Failure recovery.</span></span> <span data-ttu-id="d514e-106">例如，数据库处于可疑模式下或因硬件故障而关闭。</span><span class="sxs-lookup"><span data-stu-id="d514e-106">For example, the database is in suspect mode or has shut down because of a hardware failure.</span></span>  
  
-   <span data-ttu-id="d514e-107">预先安排的重定位。</span><span class="sxs-lookup"><span data-stu-id="d514e-107">Planned relocation.</span></span>  
  
-   <span data-ttu-id="d514e-108">为预定的磁盘维护操作而进行的重定位。</span><span class="sxs-lookup"><span data-stu-id="d514e-108">Relocation for scheduled disk maintenance.</span></span>  
  
 <span data-ttu-id="d514e-109">下列过程适用于在同一 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例内移动数据库文件。</span><span class="sxs-lookup"><span data-stu-id="d514e-109">The following procedures apply to moving database files within the same instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d514e-110">若要将数据库移动另一个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例中或另一台服务器上，请使用 [备份和还原](../backup-restore/back-up-and-restore-of-sql-server-databases.md) 或 [分离和附加](move-a-database-using-detach-and-attach-transact-sql.md) 操作。</span><span class="sxs-lookup"><span data-stu-id="d514e-110">To move a database to another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or to another server, use the [backup and restore](../backup-restore/back-up-and-restore-of-sql-server-databases.md) or [detach and attach](move-a-database-using-detach-and-attach-transact-sql.md) operations.</span></span>  
  
 <span data-ttu-id="d514e-111">本主题中的过程需要数据库文件的逻辑名称。</span><span class="sxs-lookup"><span data-stu-id="d514e-111">The procedures in this topic require the logical name of the database files.</span></span> <span data-ttu-id="d514e-112">若要获取该名称，请在 [sys.master_files](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql) 目录视图中查询名称列。</span><span class="sxs-lookup"><span data-stu-id="d514e-112">To obtain the name, query the name column in the [sys.master_files](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql) catalog view.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d514e-113">如果移动系统数据库并且随后重新生成 master 数据库，则必须再次移动系统数据库，因为重新生成操作会在默认位置安装所有系统数据库。</span><span class="sxs-lookup"><span data-stu-id="d514e-113">If you move a system database and later rebuild the master database, you must move the system database again because the rebuild operation installs all system databases to their default location.</span></span>  
  
##  <a name="in-this-topic"></a><a name="Intro"></a> <span data-ttu-id="d514e-114">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="d514e-114">**In This Topic**</span></span>  
  
-   [<span data-ttu-id="d514e-115">计划的重定位和计划的磁盘维护过程</span><span class="sxs-lookup"><span data-stu-id="d514e-115">Planned Relocation and Scheduled Disk Maintenance Procedure</span></span>](#Planned)  
  
-   [<span data-ttu-id="d514e-116">故障恢复过程</span><span class="sxs-lookup"><span data-stu-id="d514e-116">Failure Recovery Procedure</span></span>](#Failure)  
  
-   [<span data-ttu-id="d514e-117">移动 master 数据库</span><span class="sxs-lookup"><span data-stu-id="d514e-117">Moving the master Database</span></span>](#master)  
  
-   [<span data-ttu-id="d514e-118">移动资源数据库</span><span class="sxs-lookup"><span data-stu-id="d514e-118">Moving the Resource Database</span></span>](#Resource)  
  
-   [<span data-ttu-id="d514e-119">跟进：移动所有系统数据库后</span><span class="sxs-lookup"><span data-stu-id="d514e-119">Follow-up: After Moving All System Databases</span></span>](#Follow)  
  
-   [<span data-ttu-id="d514e-120">示例</span><span class="sxs-lookup"><span data-stu-id="d514e-120">Examples</span></span>](#Examples)  
  
##  <a name="planned-relocation-and-scheduled-disk-maintenance-procedure"></a><a name="Planned"></a> <span data-ttu-id="d514e-121">预先安排的重定位与预定的磁盘维护过程</span><span class="sxs-lookup"><span data-stu-id="d514e-121">Planned Relocation and Scheduled Disk Maintenance Procedure</span></span>  
 <span data-ttu-id="d514e-122">若要将移动系统数据库数据或日志文件的操作作为预先安排的重定位或预定的维护操作的一部分，请按照下列步骤操作。</span><span class="sxs-lookup"><span data-stu-id="d514e-122">To move a system database data or log file as part of a planned relocation or scheduled maintenance operation, follow these steps.</span></span> <span data-ttu-id="d514e-123">此过程适用于除 master 和 Resource 数据库以外的所有系统数据库。</span><span class="sxs-lookup"><span data-stu-id="d514e-123">This procedure applies to all system databases except the master and Resource databases.</span></span>  
  
1.  <span data-ttu-id="d514e-124">对于要移动的每个文件，请运行以下语句。</span><span class="sxs-lookup"><span data-stu-id="d514e-124">For each file to be moved, run the following statement.</span></span>  
  
    ```  
    ALTER DATABASE database_name MODIFY FILE ( NAME = logical_name , FILENAME = 'new_path\os_file_name' )  
    ```  
  
2.  <span data-ttu-id="d514e-125">停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例或关闭系统以执行维护。</span><span class="sxs-lookup"><span data-stu-id="d514e-125">Stop the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or shut down the system to perform maintenance.</span></span> <span data-ttu-id="d514e-126">有关详细信息，请参阅 [启动、停止、暂停、继续、重启 SQL Server 服务](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)。</span><span class="sxs-lookup"><span data-stu-id="d514e-126">For more information, see [Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md).</span></span>  
  
3.  <span data-ttu-id="d514e-127">将文件移动到新位置。</span><span class="sxs-lookup"><span data-stu-id="d514e-127">Move the file or files to the new location.</span></span>  
  
4.  <span data-ttu-id="d514e-128">重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例或服务器。</span><span class="sxs-lookup"><span data-stu-id="d514e-128">Restart the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or the server.</span></span> <span data-ttu-id="d514e-129">有关详细信息，请参阅 [启动、停止、暂停、继续、重启 SQL Server 服务](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)。</span><span class="sxs-lookup"><span data-stu-id="d514e-129">For more information, see [Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md).</span></span>  
  
5.  <span data-ttu-id="d514e-130">通过运行以下查询来验证文件更改。</span><span class="sxs-lookup"><span data-stu-id="d514e-130">Verify the file change by running the following query.</span></span>  
  
    ```  
    SELECT name, physical_name AS CurrentLocation, state_desc  
    FROM sys.master_files  
    WHERE database_id = DB_ID(N'<database_name>');  
    ```  
  
 <span data-ttu-id="d514e-131">如果移动了 msdb 数据库并为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库邮件 [配置了](../database-mail/database-mail.md)实例，则请完成下列附加步骤。</span><span class="sxs-lookup"><span data-stu-id="d514e-131">If the msdb database is moved and the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is configured for [Database Mail](../database-mail/database-mail.md), complete these additional steps.</span></span>  
  
1.  <span data-ttu-id="d514e-132">通过运行以下查询，验证是否已为 msdb 数据库启用 [!INCLUDE[ssSB](../../../includes/sssb-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d514e-132">Verify that [!INCLUDE[ssSB](../../../includes/sssb-md.md)] is enabled for the msdb database by running the following query.</span></span>  
  
    ```  
    SELECT is_broker_enabled   
    FROM sys.databases  
    WHERE name = N'msdb';  
    ```  
  
     <span data-ttu-id="d514e-133">有关启用 [!INCLUDE[ssSB](../../../includes/sssb-md.md)]的详细信息，请参阅 [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql)中移动系统数据库。</span><span class="sxs-lookup"><span data-stu-id="d514e-133">For more information about enabling [!INCLUDE[ssSB](../../../includes/sssb-md.md)], see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
2.  <span data-ttu-id="d514e-134">通过发送测试邮件来验证数据库邮件是否正常运行。</span><span class="sxs-lookup"><span data-stu-id="d514e-134">Verify that Database Mail is working by sending a test mail.</span></span>  
  
##  <a name="failure-recovery-procedure"></a><a name="Failure"></a> <span data-ttu-id="d514e-135">故障恢复过程</span><span class="sxs-lookup"><span data-stu-id="d514e-135">Failure Recovery Procedure</span></span>  
 <span data-ttu-id="d514e-136">如果由于硬件故障而必须移动文件，则请按照下列步骤将文件重新定位到一个新位置。</span><span class="sxs-lookup"><span data-stu-id="d514e-136">If a file must be moved because of a hardware failure, follow these steps to relocate the file to a new location.</span></span> <span data-ttu-id="d514e-137">此过程适用于除 master 和 Resource 数据库以外的所有系统数据库。</span><span class="sxs-lookup"><span data-stu-id="d514e-137">This procedure applies to all system databases except the master and Resource databases.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d514e-138">如果数据库无法启动，即处于可疑模式下或处于未恢复状态，则只有 sysadmin 固定角色的成员才可以移动该文件。</span><span class="sxs-lookup"><span data-stu-id="d514e-138">If the database cannot be started, that is it is in suspect mode or in an unrecovered state, only members of the sysadmin fixed role can move the file.</span></span>  
  
1.  <span data-ttu-id="d514e-139">如果启动了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例，则将其停止。</span><span class="sxs-lookup"><span data-stu-id="d514e-139">Stop the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] if it is started.</span></span>  
  
2.  <span data-ttu-id="d514e-140">通过在命令提示符下输入下列命令之一，在仅 master 恢复模式下启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="d514e-140">Start the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in master-only recovery mode by entering one of the following commands at the command prompt.</span></span> <span data-ttu-id="d514e-141">在这些命令中指定的参数区分大小写。</span><span class="sxs-lookup"><span data-stu-id="d514e-141">The parameters specified in these commands are case sensitive.</span></span> <span data-ttu-id="d514e-142">如果未按所示方式指定参数，则命令会失败。</span><span class="sxs-lookup"><span data-stu-id="d514e-142">The commands fail when the parameters are not specified as shown.</span></span>  
  
    -   <span data-ttu-id="d514e-143">对于默认的 (MSSQLSERVER) 实例，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="d514e-143">For the default (MSSQLSERVER) instance, run the following command:</span></span>  
  
        ```  
        NET START MSSQLSERVER /f /T3608  
        ```  
  
    -   <span data-ttu-id="d514e-144">对于命名实例，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="d514e-144">For a named instance, run the following command:</span></span>  
  
        ```  
        NET START MSSQL$instancename /f /T3608  
        ```  
  
     <span data-ttu-id="d514e-145">有关详细信息，请参阅 [启动、停止、暂停、继续、重启 SQL Server 服务](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)。</span><span class="sxs-lookup"><span data-stu-id="d514e-145">For more information, see [Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md).</span></span>  
  
3.  <span data-ttu-id="d514e-146">对于要移动的每个文件，请使用 **sqlcmd** 命令或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 运行以下语句。</span><span class="sxs-lookup"><span data-stu-id="d514e-146">For each file to be moved, use **sqlcmd** commands or [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] to run the following statement.</span></span>  
  
    ```  
    ALTER DATABASE database_name MODIFY FILE( NAME = logical_name , FILENAME = 'new_path\os_file_name' )  
    ```  
  
     <span data-ttu-id="d514e-147">有关使用 **sqlcmd** 实用工具的详细信息，请参阅 [使用 sqlcmd 实用工具](../scripting/sqlcmd-use-the-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="d514e-147">For more information about using the **sqlcmd** utility, see [Use the sqlcmd Utility](../scripting/sqlcmd-use-the-utility.md).</span></span>  
  
4.  <span data-ttu-id="d514e-148">退出 **sqlcmd** 实用工具或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d514e-148">Exit the **sqlcmd** utility or [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span>  
  
5.  <span data-ttu-id="d514e-149">停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例。</span><span class="sxs-lookup"><span data-stu-id="d514e-149">Stop the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d514e-150">例如，运行 `NET STOP MSSQLSERVER`。</span><span class="sxs-lookup"><span data-stu-id="d514e-150">For example, run `NET STOP MSSQLSERVER`.</span></span>  
  
6.  <span data-ttu-id="d514e-151">将文件移动到新位置。</span><span class="sxs-lookup"><span data-stu-id="d514e-151">Move the file or files to the new location.</span></span>  
  
7.  <span data-ttu-id="d514e-152">重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例。</span><span class="sxs-lookup"><span data-stu-id="d514e-152">Restart the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d514e-153">例如，运行 `NET START MSSQLSERVER`。</span><span class="sxs-lookup"><span data-stu-id="d514e-153">For example, run `NET START MSSQLSERVER`.</span></span>  
  
8.  <span data-ttu-id="d514e-154">通过运行以下查询来验证文件更改。</span><span class="sxs-lookup"><span data-stu-id="d514e-154">Verify the file change by running the following query.</span></span>  
  
    ```  
    SELECT name, physical_name AS CurrentLocation, state_desc  
    FROM sys.master_files  
    WHERE database_id = DB_ID(N'<database_name>');  
    ```  
  
##  <a name="moving-the-master-database"></a><a name="master"></a> <span data-ttu-id="d514e-155">移动 master 数据库</span><span class="sxs-lookup"><span data-stu-id="d514e-155">Moving the master Database</span></span>  
 <span data-ttu-id="d514e-156">若要移动 master 数据库，请按下列步骤进行操作。</span><span class="sxs-lookup"><span data-stu-id="d514e-156">To move the master database, follow these steps.</span></span>  
  
1.  <span data-ttu-id="d514e-157">在 **“开始”** 菜单中，依次指向 **“所有程序”** 、 **“Microsoft SQL Server”** 和 **“配置工具”** ，然后单击 **“SQL Server 配置管理器”** 。</span><span class="sxs-lookup"><span data-stu-id="d514e-157">From the **Start** menu, point to **All Programs**, point to **Microsoft SQL Server**, point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="d514e-158">在“SQL Server 服务”节点中，右键单击 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例（如 **SQL Server (MSSQLSERVER)** ），并选择“属性”。</span><span class="sxs-lookup"><span data-stu-id="d514e-158">In the **SQL Server Services** node, right-click the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (for example, **SQL Server (MSSQLSERVER)**) and choose **Properties**.</span></span>  
  
3.  <span data-ttu-id="d514e-159">在 " **SQL Server (***Instance_name***) 属性**" 对话框中，单击 "**启动参数**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="d514e-159">In the **SQL Server (***instance_name***) Properties** dialog box, click the **Startup Parameters** tab.</span></span>  
  
4.  <span data-ttu-id="d514e-160">在“现有参数”框中，选择 –d 参数以移动 master 数据文件。</span><span class="sxs-lookup"><span data-stu-id="d514e-160">In the **Existing parameters** box, select the -d parameter to move the master data file.</span></span> <span data-ttu-id="d514e-161">单击 **“更新”** 以保存更改。</span><span class="sxs-lookup"><span data-stu-id="d514e-161">Click **Update** to save the change.</span></span>  
  
     <span data-ttu-id="d514e-162">在“指定启动参数”框中，将该参数更改为 master 数据库的新路径。</span><span class="sxs-lookup"><span data-stu-id="d514e-162">In the **Specify a startup parameter** box, change the parameter to the new path of the master database.</span></span>  
  
5.  <span data-ttu-id="d514e-163">在“现有参数”框中，选择 –l 参数以移动 master 日志文件。</span><span class="sxs-lookup"><span data-stu-id="d514e-163">In the **Existing parameters** box, select the -l parameter to move the master log file.</span></span> <span data-ttu-id="d514e-164">单击 **“更新”** 以保存更改。</span><span class="sxs-lookup"><span data-stu-id="d514e-164">Click **Update** to save the change.</span></span>  
  
     <span data-ttu-id="d514e-165">在“指定启动参数”框中，将该参数更改为 master 数据库的新路径。</span><span class="sxs-lookup"><span data-stu-id="d514e-165">In the **Specify a startup parameter** box, change the parameter to the new path of the master database.</span></span>  
  
     <span data-ttu-id="d514e-166">数据文件的参数值必须跟在 `-d` 参数的后面，日志文件的参数值必须跟在 `-l` 参数的后面。</span><span class="sxs-lookup"><span data-stu-id="d514e-166">The parameter value for the data file must follow the `-d` parameter and the value for the log file must follow the `-l` parameter.</span></span> <span data-ttu-id="d514e-167">下面的示例显示用于 master 数据文件默认位置的参数值。</span><span class="sxs-lookup"><span data-stu-id="d514e-167">The following example shows the parameter values for the default location of the master data file.</span></span>  
  
     `-dC:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\master.mdf`  
  
     `-lC:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\mastlog.ldf`  
  
     <span data-ttu-id="d514e-168">如果 master 数据文件预先安排的重定位是 `E:\SQLData`，则参数值将做如下更改：</span><span class="sxs-lookup"><span data-stu-id="d514e-168">If the planned relocation for the master data file is `E:\SQLData`, the parameter values would be changed as follows:</span></span>  
  
     `-dE:\SQLData\master.mdf`  
  
     `-lE:\SQLData\mastlog.ldf`  
  
6.  <span data-ttu-id="d514e-169">通过右键单击实例名称并选择“停止”来停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="d514e-169">Stop the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by right-clicking the instance name and choosing **Stop**.</span></span>  
  
7.  <span data-ttu-id="d514e-170">将 master.mdf 和 mastlog.ldf 文件移动到新位置。</span><span class="sxs-lookup"><span data-stu-id="d514e-170">Move the master.mdf and mastlog.ldf files to the new location.</span></span>  
  
8.  <span data-ttu-id="d514e-171">重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例。</span><span class="sxs-lookup"><span data-stu-id="d514e-171">Restart the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
9. <span data-ttu-id="d514e-172">通过运行以下查询，验证 master 数据库的文件更改。</span><span class="sxs-lookup"><span data-stu-id="d514e-172">Verify the file change for the master database by running the following query.</span></span>  
  
    ```  
    SELECT name, physical_name AS CurrentLocation, state_desc  
    FROM sys.master_files  
    WHERE database_id = DB_ID('master');  
    GO  
    ```  
  
##  <a name="moving-the-resource-database"></a><a name="Resource"></a> <span data-ttu-id="d514e-173">移动 Resource 数据库</span><span class="sxs-lookup"><span data-stu-id="d514e-173">Moving the Resource Database</span></span>  
 <span data-ttu-id="d514e-174">Resource 数据库的位置是 \<*drive*>:\Program Files\Microsoft SQL Server\MSSQL\<version>.\<*instance_name*>\MSSQL\Binn\\。</span><span class="sxs-lookup"><span data-stu-id="d514e-174">The location of the Resource database is \<*drive*>:\Program Files\Microsoft SQL Server\MSSQL\<version>.\<*instance_name*>\MSSQL\Binn\\.</span></span> <span data-ttu-id="d514e-175">无法移动该数据库。</span><span class="sxs-lookup"><span data-stu-id="d514e-175">The database cannot be moved.</span></span>  
  
##  <a name="follow-up-after-moving-all-system-databases"></a><a name="Follow"></a> <span data-ttu-id="d514e-176">后续任务：移动所有系统数据库后</span><span class="sxs-lookup"><span data-stu-id="d514e-176">Follow-up: After Moving All System Databases</span></span>  
 <span data-ttu-id="d514e-177">如果已将所有系统数据库都移到新的驱动器/卷或移到使用不同驱动器盘符的另一个服务器，请进行下列更新。</span><span class="sxs-lookup"><span data-stu-id="d514e-177">If you have moved all of the system databases to a new drive or volume or to another server with a different drive letter, make the following updates.</span></span>  
  
-   <span data-ttu-id="d514e-178">更改 SQL Server 代理日志路径。</span><span class="sxs-lookup"><span data-stu-id="d514e-178">Change the SQL Server Agent log path.</span></span> <span data-ttu-id="d514e-179">如果不更新此路径，SQL Server 代理将无法启动。</span><span class="sxs-lookup"><span data-stu-id="d514e-179">If you do not update this path, SQL Server Agent will fail to start.</span></span>  
  
-   <span data-ttu-id="d514e-180">更改数据库默认位置。</span><span class="sxs-lookup"><span data-stu-id="d514e-180">Change the database default location.</span></span> <span data-ttu-id="d514e-181">如果指定为默认位置的驱动器盘符和路径不存在，则可能无法创建新的数据库。</span><span class="sxs-lookup"><span data-stu-id="d514e-181">Creating a new database may fail if the drive letter and path specified as the default location do not exist.</span></span>  
  
#### <a name="change-the-sql-server-agent-log-path"></a><span data-ttu-id="d514e-182">更改 SQL Server 代理日志路径</span><span class="sxs-lookup"><span data-stu-id="d514e-182">Change the SQL Server Agent Log Path</span></span>  
  
1.  <span data-ttu-id="d514e-183">从 SQL Server Management Studio 的对象资源管理器中，展开 **“SQL Server 代理”** 。</span><span class="sxs-lookup"><span data-stu-id="d514e-183">From SQL Server Management Studio, in Object Explorer, expand **SQL Server Agent**.</span></span>  
  
2.  <span data-ttu-id="d514e-184">右键单击 **“错误日志”** ，然后单击 **“配置”** 。</span><span class="sxs-lookup"><span data-stu-id="d514e-184">Right-click **Error Logs** and click **Configure**.</span></span>  
  
3.  <span data-ttu-id="d514e-185">在 **“配置 SQL Server 代理错误日志”** 对话框中，指定 SQLAGENT.OUT 文件的新位置。</span><span class="sxs-lookup"><span data-stu-id="d514e-185">In the **Configure SQL Server Agent Error Logs** dialog box, specify the new location of the SQLAGENT.OUT file.</span></span> <span data-ttu-id="d514e-186">默认位置为 C:\Program Files\Microsoft SQL Server\MSSQL12. <instance_name> \MSSQL\Log \\ 。</span><span class="sxs-lookup"><span data-stu-id="d514e-186">The default location is C:\Program Files\Microsoft SQL Server\MSSQL12.<instance_name>\MSSQL\Log\\.</span></span>  
  
#### <a name="change-the-database-default-location"></a><span data-ttu-id="d514e-187">更改数据库默认位置</span><span class="sxs-lookup"><span data-stu-id="d514e-187">Change the database default location</span></span>  
  
1.  <span data-ttu-id="d514e-188">从 SQL Server Management Studio 的对象资源管理器中，右键单击 SQL Server 所在服务器，然后单击 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="d514e-188">From SQL Server Management Studio, in Object Explorer, right-click the SQL Server server and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="d514e-189">在 **“服务器属性”** 对话框中，选择 **“数据库设置”** 。</span><span class="sxs-lookup"><span data-stu-id="d514e-189">In the **Server Properties** dialog box, select **Database Settings**.</span></span>  
  
3.  <span data-ttu-id="d514e-190">在 **“数据库默认位置”** 下，找到数据文件和日志文件的新位置。</span><span class="sxs-lookup"><span data-stu-id="d514e-190">Under **Database Default Locations**, browse to the new location for both the data and log files.</span></span>  
  
4.  <span data-ttu-id="d514e-191">先停止然后启动 SQL Server 服务以完成更改。</span><span class="sxs-lookup"><span data-stu-id="d514e-191">Stop and start the SQL Server service to complete the change.</span></span>  
  
##  <a name="examples"></a><a name="Examples"></a> <span data-ttu-id="d514e-192">示例</span><span class="sxs-lookup"><span data-stu-id="d514e-192">Examples</span></span>  
  
### <a name="a-moving-the-tempdb-database"></a><span data-ttu-id="d514e-193">A.</span><span class="sxs-lookup"><span data-stu-id="d514e-193">A.</span></span> <span data-ttu-id="d514e-194">移动 tempdb 数据库</span><span class="sxs-lookup"><span data-stu-id="d514e-194">Moving the tempdb database</span></span>  
 <span data-ttu-id="d514e-195">作为预先安排的重定位的一部分，下面的示例将 `tempdb` 数据和日志文件移动到一个新位置。</span><span class="sxs-lookup"><span data-stu-id="d514e-195">The following example moves the `tempdb` data and log files to a new location as part of a planned relocation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d514e-196">由于每次启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例时都将重新创建 tempdb，所以不必实际移动数据和日志文件。</span><span class="sxs-lookup"><span data-stu-id="d514e-196">Because tempdb is re-created each time the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is started, you do not have to physically move the data and log files.</span></span> <span data-ttu-id="d514e-197">在步骤 3 中重新启动服务时，将在新位置中创建这些文件。</span><span class="sxs-lookup"><span data-stu-id="d514e-197">The files are created in the new location when the service is restarted in step 3.</span></span> <span data-ttu-id="d514e-198">在重新启动服务之前，tempdb 将继续使用现有位置中的数据和日志文件。</span><span class="sxs-lookup"><span data-stu-id="d514e-198">Until the service is restarted, tempdb continues to use the data and log files in existing location.</span></span>  
  
1.  <span data-ttu-id="d514e-199">确定 `tempdb` 数据库的逻辑文件名称以及在磁盘上的当前位置。</span><span class="sxs-lookup"><span data-stu-id="d514e-199">Determine the logical file names of the `tempdb` database and their current location on the disk.</span></span>  
  
    ```  
    SELECT name, physical_name AS CurrentLocation  
    FROM sys.master_files  
    WHERE database_id = DB_ID(N'tempdb');  
    GO  
    ```  
  
2.  <span data-ttu-id="d514e-200">使用 `ALTER DATABASE`更改每个文件的位置。</span><span class="sxs-lookup"><span data-stu-id="d514e-200">Change the location of each file by using `ALTER DATABASE`.</span></span>  
  
    ```  
    USE master;  
    GO  
    ALTER DATABASE tempdb   
    MODIFY FILE (NAME = tempdev, FILENAME = 'E:\SQLData\tempdb.mdf');  
    GO  
    ALTER DATABASE tempdb   
    MODIFY FILE (NAME = templog, FILENAME = 'F:\SQLLog\templog.ldf');  
    GO  
    ```  
  
3.  <span data-ttu-id="d514e-201">停止再重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="d514e-201">Stop and restart the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
4.  <span data-ttu-id="d514e-202">验证文件更改。</span><span class="sxs-lookup"><span data-stu-id="d514e-202">Verify the file change.</span></span>  
  
    ```  
    SELECT name, physical_name AS CurrentLocation, state_desc  
    FROM sys.master_files  
    WHERE database_id = DB_ID(N'tempdb');  
    ```  
  
5.  <span data-ttu-id="d514e-203">将 `tempdb.mdf` 和 `templog.ldf` 文件从其原始位置删除。</span><span class="sxs-lookup"><span data-stu-id="d514e-203">Delete the `tempdb.mdf` and `templog.ldf` files from the original location.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d514e-204">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d514e-204">See Also</span></span>  
 <span data-ttu-id="d514e-205">[Resource 数据库](resource-database.md) </span><span class="sxs-lookup"><span data-stu-id="d514e-205">[Resource Database](resource-database.md) </span></span>  
 <span data-ttu-id="d514e-206">[tempdb 数据库](tempdb-database.md) </span><span class="sxs-lookup"><span data-stu-id="d514e-206">[tempdb Database](tempdb-database.md) </span></span>  
 <span data-ttu-id="d514e-207">[master 数据库](master-database.md) </span><span class="sxs-lookup"><span data-stu-id="d514e-207">[master Database](master-database.md) </span></span>  
 <span data-ttu-id="d514e-208">[msdb 数据库](msdb-database.md) </span><span class="sxs-lookup"><span data-stu-id="d514e-208">[msdb Database](msdb-database.md) </span></span>  
 <span data-ttu-id="d514e-209">[model 数据库](model-database.md) </span><span class="sxs-lookup"><span data-stu-id="d514e-209">[model Database](model-database.md) </span></span>  
 <span data-ttu-id="d514e-210">[移动用户数据库](move-user-databases.md) </span><span class="sxs-lookup"><span data-stu-id="d514e-210">[Move User Databases](move-user-databases.md) </span></span>  
 <span data-ttu-id="d514e-211">[移动数据库文件](move-database-files.md) </span><span class="sxs-lookup"><span data-stu-id="d514e-211">[Move Database Files](move-database-files.md) </span></span>  
 <span data-ttu-id="d514e-212">[启动、停止、暂停、继续、重新启动数据库引擎、SQL Server 代理或 SQL Server Browser 服务](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md) </span><span class="sxs-lookup"><span data-stu-id="d514e-212">[Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md) </span></span>  
 <span data-ttu-id="d514e-213">[ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d514e-213">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 [<span data-ttu-id="d514e-214">重新生成系统数据库</span><span class="sxs-lookup"><span data-stu-id="d514e-214">Rebuild System Databases</span></span>](system-databases.md)  
  
  
