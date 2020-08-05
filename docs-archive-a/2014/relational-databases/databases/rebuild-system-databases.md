---
title: 重新生成系统数据库 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- master database [SQL Server], rebuilding
- REBUILDDATABASE parameter
- rebuilding databases, master
- system databases [SQL Server], rebuilding
ms.assetid: af457ecd-523e-4809-9652-bdf2e81bd876
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5f695589fa0fc1b86d4433d36afa1bc6357aabd6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581290"
---
# <a name="rebuild-system-databases"></a><span data-ttu-id="74752-102">重新生成系统数据库</span><span class="sxs-lookup"><span data-stu-id="74752-102">Rebuild System Databases</span></span>
  <span data-ttu-id="74752-103">必须重新生成系统数据库才能修复 [master](master-database.md)、 [mode](model-database.md)l、 [msdb](msdb-database.md)或 [resource](resource-database.md) 系统数据库中的损坏问题或者修改默认的服务器级排序规则。</span><span class="sxs-lookup"><span data-stu-id="74752-103">System databases must be rebuilt to fix corruption problems in the [master](master-database.md), [model](model-database.md), [msdb](msdb-database.md), or [resource](resource-database.md) system databases or to modify the default server-level collation.</span></span> <span data-ttu-id="74752-104">本主题提供如何在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中重新生成系统数据库的分步说明。</span><span class="sxs-lookup"><span data-stu-id="74752-104">This topic provides step-by-step instructions to rebuild system databases in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="74752-105">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="74752-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="74752-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="74752-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="74752-107">限制和局限</span><span class="sxs-lookup"><span data-stu-id="74752-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="74752-108">先决条件</span><span class="sxs-lookup"><span data-stu-id="74752-108">Prerequisites</span></span>](#Prerequisites)  
  
-   <span data-ttu-id="74752-109">**过程：**</span><span class="sxs-lookup"><span data-stu-id="74752-109">**Procedures:**</span></span>  
  
     [<span data-ttu-id="74752-110">重新生成系统数据库</span><span class="sxs-lookup"><span data-stu-id="74752-110">Rebuild System Databases</span></span>](#RebuildProcedure)  
  
     [<span data-ttu-id="74752-111">resource 数据库重新生成</span><span class="sxs-lookup"><span data-stu-id="74752-111">Rebuild the resource Database</span></span>](#Resource)  
  
     [<span data-ttu-id="74752-112">创建新的 msdb 数据库</span><span class="sxs-lookup"><span data-stu-id="74752-112">Create a New msdb Database</span></span>](#CreateMSDB)  
  
-   <span data-ttu-id="74752-113">**跟进：**</span><span class="sxs-lookup"><span data-stu-id="74752-113">**Follow Up:**</span></span>  
  
     [<span data-ttu-id="74752-114">解决重新生成错误</span><span class="sxs-lookup"><span data-stu-id="74752-114">Troubleshoot Rebuild Errors</span></span>](#Troubleshoot)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="74752-115">开始之前</span><span class="sxs-lookup"><span data-stu-id="74752-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="74752-116">限制和局限</span><span class="sxs-lookup"><span data-stu-id="74752-116">Limitations and Restrictions</span></span>  
 <span data-ttu-id="74752-117">重新生成 master、model、msdb 和 tempdb 系统数据库时，将删除这些数据库，然后在其原位置重新创建它们。</span><span class="sxs-lookup"><span data-stu-id="74752-117">When the master, model, msdb, and tempdb system databases are rebuilt, the databases are dropped and re-created in their original location.</span></span> <span data-ttu-id="74752-118">如果在重新生成语句中指定了新排序规则，则将使用该排序规则设置创建系统数据库。</span><span class="sxs-lookup"><span data-stu-id="74752-118">If a new collation is specified in the rebuild statement, the system databases are created using that collation setting.</span></span> <span data-ttu-id="74752-119">用户对这些数据库所做的所有修改都会丢失。</span><span class="sxs-lookup"><span data-stu-id="74752-119">Any user modifications to these databases are lost.</span></span> <span data-ttu-id="74752-120">例如，您在 master 数据库中的用户定义对象、msdb 中的预定作业或 model 数据库中对默认数据库设置的更改都会丢失。</span><span class="sxs-lookup"><span data-stu-id="74752-120">For example, you may have user-defined objects in the master database, scheduled jobs in msdb, or changes to the default database settings in the model database.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="74752-121">先决条件</span><span class="sxs-lookup"><span data-stu-id="74752-121">Prerequisites</span></span>  
 <span data-ttu-id="74752-122">在重新生成系统数据库之前执行下列任务，以确保可以将系统数据库还原至它们的当前设置。</span><span class="sxs-lookup"><span data-stu-id="74752-122">Perform the following tasks before you rebuild the system databases to ensure that you can restore the system databases to their current settings.</span></span>  
  
1.  <span data-ttu-id="74752-123">记录所有服务器范围的配置值。</span><span class="sxs-lookup"><span data-stu-id="74752-123">Record all server-wide configuration values.</span></span>  
  
    ```  
    SELECT * FROM sys.configurations;  
    ```  
  
2.  <span data-ttu-id="74752-124">记录所有应用到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例和当前排序规则的 Service Pack 和修补程序。</span><span class="sxs-lookup"><span data-stu-id="74752-124">Record all service packs and hotfixes applied to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the current collation.</span></span> <span data-ttu-id="74752-125">重新生成系统数据库后必须重新应用这些更新。</span><span class="sxs-lookup"><span data-stu-id="74752-125">You must reapply these updates after rebuilding the system databases.</span></span>  
  
    ```  
    SELECT  
    SERVERPROPERTY('ProductVersion ') AS ProductVersion,  
    SERVERPROPERTY('ProductLevel') AS ProductLevel,  
    SERVERPROPERTY('ResourceVersion') AS ResourceVersion,  
    SERVERPROPERTY('ResourceLastUpdateDateTime') AS ResourceLastUpdateDateTime,  
    SERVERPROPERTY('Collation') AS Collation;  
    ```  
  
3.  <span data-ttu-id="74752-126">记录系统数据库的所有数据文件和日志文件的当前位置。</span><span class="sxs-lookup"><span data-stu-id="74752-126">Record the current location of all data and log files for the system databases.</span></span> <span data-ttu-id="74752-127">重新生成系统数据库会将所有系统数据库安装到其原位置。</span><span class="sxs-lookup"><span data-stu-id="74752-127">Rebuilding the system databases installs all system databases to their original location.</span></span> <span data-ttu-id="74752-128">如果已将系统数据库数据文件或日志文件移动到其他位置，则必须再次移动这些文件。</span><span class="sxs-lookup"><span data-stu-id="74752-128">If you have moved system database data or log files to a different location, you must move the files again.</span></span>  
  
    ```  
    SELECT name, physical_name AS current_file_location  
    FROM sys.master_files  
    WHERE database_id IN (DB_ID('master'), DB_ID('model'), DB_ID('msdb'), DB_ID('tempdb'));  
    ```  
  
4.  <span data-ttu-id="74752-129">找到 master、model 和 msdb 数据库的当前备份。</span><span class="sxs-lookup"><span data-stu-id="74752-129">Locate the current backup of the master, model, and msdb databases.</span></span>  
  
5.  <span data-ttu-id="74752-130">如果将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例配置为复制分发服务器，请找到该分发数据库的当前备份。</span><span class="sxs-lookup"><span data-stu-id="74752-130">If the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is configured as a replication Distributor, locate the current backup of the distribution database.</span></span>  
  
6.  <span data-ttu-id="74752-131">确保您有重新生成系统数据库的相应权限。</span><span class="sxs-lookup"><span data-stu-id="74752-131">Ensure you have appropriate permissions to rebuild the system databases.</span></span> <span data-ttu-id="74752-132">必须是 `sysadmin` 固定服务器角色的成员才能执行此操作。</span><span class="sxs-lookup"><span data-stu-id="74752-132">To perform this operation, you must be a member of the `sysadmin` fixed server role.</span></span> <span data-ttu-id="74752-133">有关详细信息，请参阅 [服务器级别角色](../security/authentication-access/server-level-roles.md)。</span><span class="sxs-lookup"><span data-stu-id="74752-133">For more information, see [Server-Level Roles](../security/authentication-access/server-level-roles.md).</span></span>  
  
7.  <span data-ttu-id="74752-134">请验证本地服务器上是否有 master、model、msdb 数据模板文件和日志模板文件的副本。</span><span class="sxs-lookup"><span data-stu-id="74752-134">Verify that copies of the master, model, msdb data and log template files exist on the local server.</span></span> <span data-ttu-id="74752-135">模板文件的默认位置是 C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn\Templates。</span><span class="sxs-lookup"><span data-stu-id="74752-135">The default location for the template files is C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn\Templates.</span></span> <span data-ttu-id="74752-136">在重新生成过程中要用到这些文件，而且若想让安装成功这些文件必须存在。</span><span class="sxs-lookup"><span data-stu-id="74752-136">These files are used during the rebuild process and must be present for Setup to succeed.</span></span> <span data-ttu-id="74752-137">如果缺少这些文件，请运行安装程序的“修复”功能或者手动从安装介质中复制这些文件。</span><span class="sxs-lookup"><span data-stu-id="74752-137">If they are missing, run the Repair feature of Setup, or manually copy the files from your installation media.</span></span> <span data-ttu-id="74752-138">若要在安装介质上查找这些文件，请导航到相应的平台目录（x86 或 x64），然后导航到 setup\sql_engine_core_inst_msi\Pfiles\SqlServr\MSSQL.X\MSSQL\Binn\Templates。</span><span class="sxs-lookup"><span data-stu-id="74752-138">To locate the files on the installation media, navigate to the appropriate platform directory (x86 or x64) and then navigate to setup\sql_engine_core_inst_msi\Pfiles\SqlServr\MSSQL.X\MSSQL\Binn\Templates.</span></span>  
  
##  <a name="rebuild-system-databases"></a><a name="RebuildProcedure"></a> <span data-ttu-id="74752-139">重新生成系统数据库</span><span class="sxs-lookup"><span data-stu-id="74752-139">Rebuild System Databases</span></span>  
 <span data-ttu-id="74752-140">以下过程将重新生成 master、model、msdb 和 tempdb 系统数据库。</span><span class="sxs-lookup"><span data-stu-id="74752-140">The following procedure rebuilds the master, model, msdb, and tempdb system databases.</span></span> <span data-ttu-id="74752-141">无法指定要重新生成哪些系统数据库。</span><span class="sxs-lookup"><span data-stu-id="74752-141">You cannot specify the system databases to be rebuilt.</span></span> <span data-ttu-id="74752-142">对于群集实例，必须在主动节点上执行此过程，并且在执行此过程之前，必须先使相应群集应用程序组中的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 资源脱机。</span><span class="sxs-lookup"><span data-stu-id="74752-142">For clustered instances, this procedure must be performed on the active node and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resource in the corresponding cluster application group must be taken offline before performing the procedure.</span></span>  
  
 <span data-ttu-id="74752-143">此过程不重新生成 resource 数据库。</span><span class="sxs-lookup"><span data-stu-id="74752-143">This procedure does not rebuild the resource database.</span></span> <span data-ttu-id="74752-144">请参阅本主题后面的“resource 数据库重新生成过程”部分。</span><span class="sxs-lookup"><span data-stu-id="74752-144">See the section, "Rebuild the resource Database Procedure" later in this topic.</span></span>  
  
#### <a name="to-rebuild-system-databases-for-an-instance-of-sql-server"></a><span data-ttu-id="74752-145">重新生成 SQL Server 实例的系统数据库：</span><span class="sxs-lookup"><span data-stu-id="74752-145">To rebuild system databases for an instance of SQL Server:</span></span>  
  
1.  <span data-ttu-id="74752-146">将 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 安装介质插入到磁盘驱动器中，或者在本地服务器上，从命令提示符处将目录更改为 setup.exe 文件的位置。</span><span class="sxs-lookup"><span data-stu-id="74752-146">Insert the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] installation media into the disk drive, or, from a command prompt, change directories to the location of the setup.exe file on the local server.</span></span> <span data-ttu-id="74752-147">在服务器上的默认位置为 C:\Program Files\Microsoft SQL Server\120\Setup Bootstrap\Release。</span><span class="sxs-lookup"><span data-stu-id="74752-147">The default location on the server is C:\Program Files\Microsoft SQL Server\120\Setup Bootstrap\Release.</span></span>  
  
2.  <span data-ttu-id="74752-148">在命令提示符窗口中，输入以下命令。</span><span class="sxs-lookup"><span data-stu-id="74752-148">From a command prompt window, enter the following command.</span></span> <span data-ttu-id="74752-149">方括号用来指示可选参数。</span><span class="sxs-lookup"><span data-stu-id="74752-149">Square brackets are used to indicate optional parameters.</span></span> <span data-ttu-id="74752-150">不要输入括号。</span><span class="sxs-lookup"><span data-stu-id="74752-150">Do not enter the brackets.</span></span> <span data-ttu-id="74752-151">在使用 Windows 操作系统且启用了用户帐户控制 (UAC) 时，运行安装程序需要提升特权。</span><span class="sxs-lookup"><span data-stu-id="74752-151">When using a Windows operating system that has User Account Control (UAC) enabled, running Setup requires elevated privileges.</span></span> <span data-ttu-id="74752-152">必须以管理员身份运行命令提示符。</span><span class="sxs-lookup"><span data-stu-id="74752-152">The command prompt must be run as Administrator.</span></span>  
  
     `Setup /QUIET /ACTION=REBUILDDATABASE /INSTANCENAME=InstanceName /SQLSYSADMINACCOUNTS=accounts [ /SAPWD= StrongPassword ] [ /SQLCOLLATION=CollationName]`  
  
    |<span data-ttu-id="74752-153">参数名称</span><span class="sxs-lookup"><span data-stu-id="74752-153">Parameter name</span></span>|<span data-ttu-id="74752-154">说明</span><span class="sxs-lookup"><span data-stu-id="74752-154">Description</span></span>|  
    |--------------------|-----------------|  
    |<span data-ttu-id="74752-155">/QUIET 或 /Q</span><span class="sxs-lookup"><span data-stu-id="74752-155">/QUIET or /Q</span></span>|<span data-ttu-id="74752-156">指定在没有任何用户界面的情况下运行安装程序。</span><span class="sxs-lookup"><span data-stu-id="74752-156">Specifies that Setup run without any user interface.</span></span>|  
    |<span data-ttu-id="74752-157">/ACTION=REBUILDDATABASE</span><span class="sxs-lookup"><span data-stu-id="74752-157">/ACTION=REBUILDDATABASE</span></span>|<span data-ttu-id="74752-158">指定安装程序将重新创建系统数据库。</span><span class="sxs-lookup"><span data-stu-id="74752-158">Specifies that Setup re-create the system databases.</span></span>|  
    |<span data-ttu-id="74752-159">/INSTANCENAME=*InstanceName*</span><span class="sxs-lookup"><span data-stu-id="74752-159">/INSTANCENAME=*InstanceName*</span></span>|<span data-ttu-id="74752-160">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例的名称。</span><span class="sxs-lookup"><span data-stu-id="74752-160">Is the name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="74752-161">对于默认实例，请输入 MSSQLSERVER。</span><span class="sxs-lookup"><span data-stu-id="74752-161">For the default instance, enter MSSQLSERVER.</span></span>|  
    |<span data-ttu-id="74752-162">/SQLSYSADMINACCOUNTS=*accounts*</span><span class="sxs-lookup"><span data-stu-id="74752-162">/SQLSYSADMINACCOUNTS=*accounts*</span></span>|<span data-ttu-id="74752-163">指定要添加到 `sysadmin` 固定服务器角色中的 Windows 组或单个帐户。</span><span class="sxs-lookup"><span data-stu-id="74752-163">Specifies the Windows groups or individual accounts to add to the `sysadmin` fixed server role.</span></span> <span data-ttu-id="74752-164">指定多个帐户时，请用空格将帐户隔开。</span><span class="sxs-lookup"><span data-stu-id="74752-164">When specifying more than one account, separate the accounts with a blank space.</span></span> <span data-ttu-id="74752-165">例如，输入 **BUILTIN\Administrators MyDomain\MyUser**。</span><span class="sxs-lookup"><span data-stu-id="74752-165">For example, enter **BUILTIN\Administrators MyDomain\MyUser**.</span></span> <span data-ttu-id="74752-166">当您在帐户名称内指定包含空格的帐户时，用双引号将该帐户引起来。</span><span class="sxs-lookup"><span data-stu-id="74752-166">When you are specifying an account that contains a blank space within the account name, enclose the account in double quotation marks.</span></span> <span data-ttu-id="74752-167">例如，输入 `NT AUTHORITY\SYSTEM`。</span><span class="sxs-lookup"><span data-stu-id="74752-167">For example, enter `NT AUTHORITY\SYSTEM`.</span></span>|  
    |<span data-ttu-id="74752-168">[ /SAPWD=*StrongPassword* ]</span><span class="sxs-lookup"><span data-stu-id="74752-168">[ /SAPWD=*StrongPassword* ]</span></span>|<span data-ttu-id="74752-169">指定帐户的密码 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `sa` 。</span><span class="sxs-lookup"><span data-stu-id="74752-169">Specifies the password for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `sa` account.</span></span> <span data-ttu-id="74752-170">如果实例使用混合身份验证（[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 Windows 身份验证）模式，则此参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="74752-170">This parameter is required if the instance uses Mixed Authentication ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows Authentication) mode.</span></span><br /><br /> <span data-ttu-id="74752-171">\*\* \* \* 安全 \* 说明 \* \*\*该 `sa` 帐户是一个众所周知的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帐户，并经常以恶意用户为目标。</span><span class="sxs-lookup"><span data-stu-id="74752-171">**\*\* Security Note \*\*** The `sa` account is a well-known [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account and it is often targeted by malicious users.</span></span> <span data-ttu-id="74752-172">因此，为 `sa` 登录名使用强密码非常重要。</span><span class="sxs-lookup"><span data-stu-id="74752-172">It is very important that you use a strong password for the `sa` login.</span></span><br /><br /> <span data-ttu-id="74752-173">不要为 Windows 身份验证模式指定此参数。</span><span class="sxs-lookup"><span data-stu-id="74752-173">Do not specify this parameter for Windows Authentication mode.</span></span>|  
    |<span data-ttu-id="74752-174">[ /SQLCOLLATION=*CollationName* ]</span><span class="sxs-lookup"><span data-stu-id="74752-174">[ /SQLCOLLATION=*CollationName* ]</span></span>|<span data-ttu-id="74752-175">指定新的服务器级排序规则。</span><span class="sxs-lookup"><span data-stu-id="74752-175">Specifies a new server-level collation.</span></span> <span data-ttu-id="74752-176">此参数是可选的。</span><span class="sxs-lookup"><span data-stu-id="74752-176">This parameter is optional.</span></span> <span data-ttu-id="74752-177">如果没有指定，则使用服务器的当前排序规则。</span><span class="sxs-lookup"><span data-stu-id="74752-177">When not specified, the current collation of the server is used.</span></span><br /><br /> <span data-ttu-id="74752-178">**\*\* 重要事项 \*\*** 更改服务器级排序规则不会更改现有用户数据库的排序。</span><span class="sxs-lookup"><span data-stu-id="74752-178">**\*\* Important \*\*** Changing the server-level collation does not change the collation of existing user databases.</span></span> <span data-ttu-id="74752-179">默认情况下，所有新创建的用户数据库都将使用新排序规则。</span><span class="sxs-lookup"><span data-stu-id="74752-179">All newly created user databases will use the new collation by default.</span></span><br /><br /> <span data-ttu-id="74752-180">有关详细信息，请参阅 [设置或更改服务器排序规则](../collations/set-or-change-the-server-collation.md)。</span><span class="sxs-lookup"><span data-stu-id="74752-180">For more information, see [Set or Change the Server Collation](../collations/set-or-change-the-server-collation.md).</span></span>|  
  
3.  <span data-ttu-id="74752-181">在安装程序完成系统数据库重新生成后，它将返回到命令提示符，而且不显示任何消息。</span><span class="sxs-lookup"><span data-stu-id="74752-181">When Setup has completed rebuilding the system databases, it returns to the command prompt with no messages.</span></span> <span data-ttu-id="74752-182">请检查 Summary.txt 日志文件以验证重新生成过程是否成功完成。</span><span class="sxs-lookup"><span data-stu-id="74752-182">Examine the Summary.txt log file to verify that the process completed successfully.</span></span> <span data-ttu-id="74752-183">此文件位于 C:\Program Files\Microsoft SQL Server\120\Setup Bootstrap\Logs。</span><span class="sxs-lookup"><span data-stu-id="74752-183">This file is located at C:\Program Files\Microsoft SQL Server\120\Setup Bootstrap\Logs.</span></span>  
  
## <a name="post-rebuild-tasks"></a><span data-ttu-id="74752-184">重新生成后的任务</span><span class="sxs-lookup"><span data-stu-id="74752-184">Post-Rebuild Tasks</span></span>  
 <span data-ttu-id="74752-185">重新生成数据库后，您可能需要执行以下额外任务：</span><span class="sxs-lookup"><span data-stu-id="74752-185">After rebuilding the database you may need to perform the following additional tasks:</span></span>  
  
-   <span data-ttu-id="74752-186">还原 master、model 和 msdb 数据库的最新完整备份。</span><span class="sxs-lookup"><span data-stu-id="74752-186">Restore your most recent full backups of the master, model, and msdb databases.</span></span> <span data-ttu-id="74752-187">有关详细信息，请参阅[备份和还原系统数据库 (SQL Server)](../backup-restore/back-up-and-restore-of-system-databases-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="74752-187">For more information, see [Back Up and Restore of System Databases &#40;SQL Server&#41;](../backup-restore/back-up-and-restore-of-system-databases-sql-server.md).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="74752-188">如果更改了服务器排序规则，请不要还原系统数据库。</span><span class="sxs-lookup"><span data-stu-id="74752-188">If you have changed the server collation, do not restore the system databases.</span></span> <span data-ttu-id="74752-189">否则，将使新排序规则替换为以前的排序规则设置。</span><span class="sxs-lookup"><span data-stu-id="74752-189">Doing so will replace the new collation with the previous collation setting.</span></span>  
  
     <span data-ttu-id="74752-190">如果没有备份或者还原的备份不是最新的，请重新创建所有缺失的条目。</span><span class="sxs-lookup"><span data-stu-id="74752-190">If a backup is not available or if the restored backup is not current, re-create any missing entries.</span></span> <span data-ttu-id="74752-191">例如，重新创建用户数据库、备份设备、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名、端点等缺少的所有条目。</span><span class="sxs-lookup"><span data-stu-id="74752-191">For example, re-create all missing entries for your user databases, backup devices, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins, end points, and so on.</span></span> <span data-ttu-id="74752-192">重新创建这些条目的最佳方法是运行创建它们的原始脚本。</span><span class="sxs-lookup"><span data-stu-id="74752-192">The best way to re-create entries is to run the original scripts that created them.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="74752-193">建议您保护好脚本，以防未经授权的人员更改脚本。</span><span class="sxs-lookup"><span data-stu-id="74752-193">We recommend that you secure your scripts to prevent their being altered by unauthorized by individuals.</span></span>  
  
-   <span data-ttu-id="74752-194">如果将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例配置为复制分发服务器，则必须还原分发数据库。</span><span class="sxs-lookup"><span data-stu-id="74752-194">If the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is configured as a replication Distributor, you must restore the distribution database.</span></span> <span data-ttu-id="74752-195">有关详细信息，请参阅 [备份和还原复制的数据库](../replication/administration/back-up-and-restore-replicated-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="74752-195">For more information, see [Back Up and Restore Replicated Databases](../replication/administration/back-up-and-restore-replicated-databases.md).</span></span>  
  
-   <span data-ttu-id="74752-196">将系统数据库移到您以前记录的位置。</span><span class="sxs-lookup"><span data-stu-id="74752-196">Move the system databases to the locations you recorded previously.</span></span> <span data-ttu-id="74752-197">有关详细信息，请参阅 [移动系统数据库](system-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="74752-197">For more information, see [Move System Databases](system-databases.md).</span></span>  
  
-   <span data-ttu-id="74752-198">验证服务器范围的配置值是否与您以前记录的值相符。</span><span class="sxs-lookup"><span data-stu-id="74752-198">Verify the server-wide configuration values match the values you recorded previously.</span></span>  
  
##  <a name="rebuild-the-resource-database"></a><a name="Resource"></a> <span data-ttu-id="74752-199">resource 数据库重新生成</span><span class="sxs-lookup"><span data-stu-id="74752-199">Rebuild the resource Database</span></span>  
 <span data-ttu-id="74752-200">以下过程将重新生成 resource 系统数据库。</span><span class="sxs-lookup"><span data-stu-id="74752-200">The following procedure rebuilds the resource system database.</span></span> <span data-ttu-id="74752-201">重新生成 resource 数据库时，所有的 Service Pack 和修补程序都将丢失，因此必须重新应用。</span><span class="sxs-lookup"><span data-stu-id="74752-201">When you rebuild the resource database, all service packs and hot fixes are lost, and therefore must be reapplied.</span></span>  
  
#### <a name="to-rebuild-the-resource-system-database"></a><span data-ttu-id="74752-202">重新生成 resource 系统数据库：</span><span class="sxs-lookup"><span data-stu-id="74752-202">To rebuild the resource system database:</span></span>  
  
1.  <span data-ttu-id="74752-203">从分发介质中启动 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 安装程序 (setup.exe)。</span><span class="sxs-lookup"><span data-stu-id="74752-203">Launch the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Setup program (setup.exe) from the distribution media.</span></span>  
  
2.  <span data-ttu-id="74752-204">在左侧导航区域中单击 **“维护”** ，然后单击 **“修复”** 。</span><span class="sxs-lookup"><span data-stu-id="74752-204">In the left navigation area, click **Maintenance**, and then click **Repair**.</span></span>  
  
3.  <span data-ttu-id="74752-205">安装程序支持规则和文件例程将运行，以确保您的系统上安装了必备组件，并且计算机能够通过安装程序验证规则。</span><span class="sxs-lookup"><span data-stu-id="74752-205">Setup support rule and file routines run to ensure that your system has prerequisites installed and that the computer passes Setup validation rules.</span></span> <span data-ttu-id="74752-206">单击 **“确定”** 或 **“安装”** 以继续操作。</span><span class="sxs-lookup"><span data-stu-id="74752-206">Click **OK** or **Install** to continue.</span></span>  
  
4.  <span data-ttu-id="74752-207">在“选择实例”页上，选择要修复的实例，然后单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="74752-207">On the Select Instance page, select the instance to repair, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="74752-208">将运行修复规则以验证修复操作。</span><span class="sxs-lookup"><span data-stu-id="74752-208">The repair rules will run to validate the operation.</span></span> <span data-ttu-id="74752-209">若要继续，请单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="74752-209">To continue, click **Next**.</span></span>  
  
6.  <span data-ttu-id="74752-210">在 **“准备修复”** 页上，单击 **“修复”** 。</span><span class="sxs-lookup"><span data-stu-id="74752-210">From the **Ready to Repair** page, click **Repair**.</span></span> <span data-ttu-id="74752-211">“完成”页指示修复操作已完成。</span><span class="sxs-lookup"><span data-stu-id="74752-211">The Complete page indicates that the operation is finished.</span></span>  
  
##  <a name="create-a-new-msdb-database"></a><a name="CreateMSDB"></a> <span data-ttu-id="74752-212">创建新的 msdb 数据库</span><span class="sxs-lookup"><span data-stu-id="74752-212">Create a New msdb Database</span></span>  
 <span data-ttu-id="74752-213">如果 `msdb` 数据库已损坏，并且没有数据库的备份 `msdb` ，则可以 `msdb` 使用**instmsdb**脚本创建新的。</span><span class="sxs-lookup"><span data-stu-id="74752-213">If the `msdb` database is damaged and you do not have a backup of the `msdb` database, you can create a new `msdb` by using the **instmsdb** script.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="74752-214">`msdb`使用**instmsdb**脚本重新生成数据库将消除中存储的所有信息 `msdb` ，例如作业、警报、运算符、维护计划、备份历史记录、基于策略的管理设置、数据库邮件、性能数据仓库等。</span><span class="sxs-lookup"><span data-stu-id="74752-214">Rebuilding the `msdb` database using the **instmsdb** script will eliminate all the information stored in `msdb` such as jobs, alert, operators, maintenance plans, backup history, Policy-Based Management settings, Database Mail, Performance Data Warehouse, etc.</span></span>  
  
1.  <span data-ttu-id="74752-215">停止与 [!INCLUDE[ssDE](../../includes/ssde-md.md)]连接的所有服务，包括 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理、 [!INCLUDE[ssRS](../../includes/ssrs.md)]、 [!INCLUDE[ssIS](../../includes/ssis-md.md)]以及将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用作数据存储区的所有应用程序。</span><span class="sxs-lookup"><span data-stu-id="74752-215">Stop all services connecting to the [!INCLUDE[ssDE](../../includes/ssde-md.md)], including [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, [!INCLUDE[ssRS](../../includes/ssrs.md)], [!INCLUDE[ssIS](../../includes/ssis-md.md)], and all applications using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as data store.</span></span>  
  
2.  <span data-ttu-id="74752-216">使用以下命令从命令行启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ： `NET START MSSQLSERVER /T3608`</span><span class="sxs-lookup"><span data-stu-id="74752-216">Start [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from the command line using the command: `NET START MSSQLSERVER /T3608`</span></span>  
  
     <span data-ttu-id="74752-217">有关详细信息，请参阅 [启动、停止、暂停、继续、重启 SQL Server 服务](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)。</span><span class="sxs-lookup"><span data-stu-id="74752-217">For more information, see [Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md).</span></span>  
  
3.  <span data-ttu-id="74752-218">在另一个命令行窗口中， `msdb` 通过执行以下命令分离数据库， *\<servername>* 并将替换为的实例 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ：`SQLCMD -E -S<servername> -dmaster -Q"EXEC sp_detach_db msdb"`</span><span class="sxs-lookup"><span data-stu-id="74752-218">In another command line window, detach the `msdb` database by executing the following command, replacing *\<servername>* with the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: `SQLCMD -E -S<servername> -dmaster -Q"EXEC sp_detach_db msdb"`</span></span>  
  
4.  <span data-ttu-id="74752-219">使用 Windows 资源管理器，重命名 `msdb` 数据库文件。</span><span class="sxs-lookup"><span data-stu-id="74752-219">Using the Windows Explorer, rename the `msdb` database files.</span></span> <span data-ttu-id="74752-220">默认情况下，这些文件位于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的 DATA 子文件夹中。</span><span class="sxs-lookup"><span data-stu-id="74752-220">By default these are in the DATA sub-folder for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
5.  <span data-ttu-id="74752-221">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器，停止然后正常重新启动 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 服务。</span><span class="sxs-lookup"><span data-stu-id="74752-221">Using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, stop and restart the [!INCLUDE[ssDE](../../includes/ssde-md.md)] service normally.</span></span>  
  
6.  <span data-ttu-id="74752-222">在命令行窗口中，连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 并执行以下命令： `SQLCMD -E -S<servername> -i"C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Install\instmsdb.sql" -o" C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Install\instmsdb.out"`</span><span class="sxs-lookup"><span data-stu-id="74752-222">In a command line window, connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and execute the command: `SQLCMD -E -S<servername> -i"C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Install\instmsdb.sql" -o" C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Install\instmsdb.out"`</span></span>  
  
     <span data-ttu-id="74752-223">使用 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的实例替换 \<servername>。</span><span class="sxs-lookup"><span data-stu-id="74752-223">Replace *\<servername>* with the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="74752-224">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例的文件系统路径。</span><span class="sxs-lookup"><span data-stu-id="74752-224">Use the file system path of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
7.  <span data-ttu-id="74752-225">使用 Windows 记事本，打开 **instmsdb.out** 文件，然后检查输出中是否存在任何错误。</span><span class="sxs-lookup"><span data-stu-id="74752-225">Using the Windows Notepad, open the **instmsdb.out** file and check the output for any errors.</span></span>  
  
8.  <span data-ttu-id="74752-226">重新应用在该实例上安装的任何 service pack 或修补程序。</span><span class="sxs-lookup"><span data-stu-id="74752-226">Re-apply any service packs or hotfix installed on the instance.</span></span>  
  
9. <span data-ttu-id="74752-227">重新创建存储在数据库中的用户内容 `msdb` ，例如作业、警报等。</span><span class="sxs-lookup"><span data-stu-id="74752-227">Recreate the user content stored in the `msdb` database, such as jobs, alert, etc.</span></span>  
  
10. <span data-ttu-id="74752-228">备份 `msdb` 数据库。</span><span class="sxs-lookup"><span data-stu-id="74752-228">Backup the `msdb` database.</span></span>  
  
##  <a name="troubleshoot-rebuild-errors"></a><a name="Troubleshoot"></a> <span data-ttu-id="74752-229">解决重新生成错误</span><span class="sxs-lookup"><span data-stu-id="74752-229">Troubleshoot Rebuild Errors</span></span>  
 <span data-ttu-id="74752-230">语法和其他运行时错误会显示在命令提示符窗口中。</span><span class="sxs-lookup"><span data-stu-id="74752-230">Syntax and other run-time errors are displayed in the command prompt window.</span></span> <span data-ttu-id="74752-231">检查 Setup 语句中是否存在以下语法错误：</span><span class="sxs-lookup"><span data-stu-id="74752-231">Examine the Setup statement for the following syntax errors:</span></span>  
  
-   <span data-ttu-id="74752-232">每个参数名称前面缺少斜杠标记 (/)。</span><span class="sxs-lookup"><span data-stu-id="74752-232">Missing slash mark (/) in front of each parameter name.</span></span>  
  
-   <span data-ttu-id="74752-233">参数名称和参数值之间缺少等号 (=)。</span><span class="sxs-lookup"><span data-stu-id="74752-233">Missing equal sign (=) between the parameter name and the parameter value.</span></span>  
  
-   <span data-ttu-id="74752-234">参数名称和等号之间存在空格。</span><span class="sxs-lookup"><span data-stu-id="74752-234">Presence of blank spaces between the parameter name and the equal sign.</span></span>  
  
-   <span data-ttu-id="74752-235">存在逗号 (,) 或语法中未指定的其他字符。</span><span class="sxs-lookup"><span data-stu-id="74752-235">Presence of commas (,) or other characters that are not specified in the syntax.</span></span>  
  
 <span data-ttu-id="74752-236">重新生成操作完成后，请检查 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 日志中是否存在任何错误。</span><span class="sxs-lookup"><span data-stu-id="74752-236">After the rebuild operation is complete, examine the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logs for any errors.</span></span> <span data-ttu-id="74752-237">默认的日志位置是 C:\Program Files\Microsoft SQL Server\120\Setup Bootstrap\Logs。</span><span class="sxs-lookup"><span data-stu-id="74752-237">The default log location is C:\Program Files\Microsoft SQL Server\120\Setup Bootstrap\Logs.</span></span> <span data-ttu-id="74752-238">若要查找包含重新生成过程的结果的日志文件，请从命令提示符处将目录更改到“Logs”文件夹，然后运行 `findstr /s RebuildDatabase summary*.*`。</span><span class="sxs-lookup"><span data-stu-id="74752-238">To locate the log file that contains the results of the rebuild process, change directories to the Logs folder from a command prompt, and then run `findstr /s RebuildDatabase summary*.*`.</span></span> <span data-ttu-id="74752-239">此搜索将引导您找到包含系统数据库重新生成结果的所有日志文件。</span><span class="sxs-lookup"><span data-stu-id="74752-239">This search will point you to any log files that contain the results of rebuilding system databases.</span></span> <span data-ttu-id="74752-240">打开日志文件，检查其中有无相关错误消息。</span><span class="sxs-lookup"><span data-stu-id="74752-240">Open the log files and examine them for relevant error messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74752-241">另请参阅</span><span class="sxs-lookup"><span data-stu-id="74752-241">See Also</span></span>  
 [<span data-ttu-id="74752-242">系统数据库</span><span class="sxs-lookup"><span data-stu-id="74752-242">System Databases</span></span>](system-databases.md)  
  
  
