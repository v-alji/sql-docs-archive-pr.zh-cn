---
title: 复制系统存储过程概念 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
dev_langs:
- TSQL
helpviewer_keywords:
- stored procedures [SQL Server replication], programming
- programming [SQL Server replication], system stored procedures
- programming interfaces [SQL Server replication]
- system stored procedures [SQL Server replication]
- replication [SQL Server], how-to topics
ms.assetid: 816d2bda-ed72-43ec-aa4d-7ee3dc25fd8a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 50536e5b6816c84dff26c9c9f99c46d02272b7de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693764"
---
# <a name="replication-system-stored-procedures-concepts"></a><span data-ttu-id="afa40-102">Replication System Stored Procedures Concepts</span><span class="sxs-lookup"><span data-stu-id="afa40-102">Replication System Stored Procedures Concepts</span></span>
  <span data-ttu-id="afa40-103">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中，对复制拓扑中所有用户可配置的功能的编程访问是由系统存储过程提供的。</span><span class="sxs-lookup"><span data-stu-id="afa40-103">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], programmatic access to all of the user-configurable functionality in a replication topology is provided by system stored procedures.</span></span> <span data-ttu-id="afa40-104">虽然可使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 或 sqlcmd 命令行实用工具来单独执行存储过程，但编写可执行具有一定逻辑顺序的复制任务的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 脚本文件也有诸多好处。</span><span class="sxs-lookup"><span data-stu-id="afa40-104">While stored procedures may be executed individually using the [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or the sqlcmd command-line utility, it may be beneficial to write [!INCLUDE[tsql](../../../includes/tsql-md.md)] script files that can be executed to perform a logical sequence of replication tasks.</span></span>  
  
 <span data-ttu-id="afa40-105">编写复制任务脚本具备以下优点：</span><span class="sxs-lookup"><span data-stu-id="afa40-105">Scripting replication tasks provides the following benefits:</span></span>  
  
-   <span data-ttu-id="afa40-106">保存用于部署复制拓扑的步骤的永久副本。</span><span class="sxs-lookup"><span data-stu-id="afa40-106">Keeps a permanent copy of the steps used to deploy your replication topology.</span></span>  
  
-   <span data-ttu-id="afa40-107">使用单个脚本配置多个订阅服务器。</span><span class="sxs-lookup"><span data-stu-id="afa40-107">Uses a single script to configure multiple Subscribers.</span></span>  
  
-   <span data-ttu-id="afa40-108">通过让新数据库管理员评估、了解、更改代码以及解决代码相关问题来快速培训新数据库管理员。</span><span class="sxs-lookup"><span data-stu-id="afa40-108">Quickly educates new database administrators by enabling them to evaluate, understand, change, or troubleshoot the code.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="afa40-109">脚本可能会带来安全漏洞；它们可以在用户毫不知情或无用户干预的情况下调用系统函数，并且可能包含纯文本形式的安全凭据。</span><span class="sxs-lookup"><span data-stu-id="afa40-109">Scripts can be the source of security vulnerabilities; they can invoke system functions without user knowledge or intervention and may contain security credentials in plain text.</span></span> <span data-ttu-id="afa40-110">请在使用之前检查脚本是否存在安全问题。</span><span class="sxs-lookup"><span data-stu-id="afa40-110">Review scripts for security issues before you use them.</span></span>  
  
## <a name="creating-replication-scripts"></a><span data-ttu-id="afa40-111">创建复制脚本</span><span class="sxs-lookup"><span data-stu-id="afa40-111">Creating Replication Scripts</span></span>  
 <span data-ttu-id="afa40-112">从复制的角度来看，脚本是单个或一系列 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句，其中每个语句执行一个复制存储过程。</span><span class="sxs-lookup"><span data-stu-id="afa40-112">From the standpoint of replication, a script is a series of one or more [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements where each statement executes a replication stored procedure.</span></span> <span data-ttu-id="afa40-113">脚本为文本文件，文件扩展名通常为 .sql，可使用 sqlcmd 实用工具来运行。</span><span class="sxs-lookup"><span data-stu-id="afa40-113">Scripts are text files, often with a .sql file extension, that can be run using the sqlcmd utility.</span></span> <span data-ttu-id="afa40-114">运行脚本文件时，此实用工具将执行存储在该文件中的 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="afa40-114">When a script file is run, the utility executes the SQL statements stored in the file.</span></span> <span data-ttu-id="afa40-115">相似地，脚本可在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 项目中作为查询对象来存储。</span><span class="sxs-lookup"><span data-stu-id="afa40-115">Similarly, a script can be stored as a query object in a [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] project.</span></span>  
  
 <span data-ttu-id="afa40-116">可以通过下列方式创建复制脚本：</span><span class="sxs-lookup"><span data-stu-id="afa40-116">Replication scripts can be created in the following ways:</span></span>  
  
-   <span data-ttu-id="afa40-117">手动创建脚本。</span><span class="sxs-lookup"><span data-stu-id="afa40-117">Manually create the script.</span></span>  
  
-   <span data-ttu-id="afa40-118">使用复制向导或</span><span class="sxs-lookup"><span data-stu-id="afa40-118">Use the script generation features that are provided in the replication wizards or</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="afa40-119">列中的一个值匹配。</span><span class="sxs-lookup"><span data-stu-id="afa40-119">.</span></span> <span data-ttu-id="afa40-120">有关详细信息，请参阅 [Scripting Replication](../scripting-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="afa40-120">For more information, see [Scripting Replication](../scripting-replication.md).</span></span>  
  
-   <span data-ttu-id="afa40-121">使用复制管理对象 (RMO) 以编程方式生成脚本，从而创建 RMO 对象。</span><span class="sxs-lookup"><span data-stu-id="afa40-121">Use Replication Management Objects (RMOs) to programmatically generate the script to create an RMO object.</span></span>  
  
 <span data-ttu-id="afa40-122">手动创建复制脚本时，请注意以下事项：</span><span class="sxs-lookup"><span data-stu-id="afa40-122">When you manually create replication scripts, keep the following considerations in mind:</span></span>  
  
-   [!INCLUDE[tsql](../../../includes/tsql-md.md)] <span data-ttu-id="afa40-123">脚本包含一个或多个批处理。</span><span class="sxs-lookup"><span data-stu-id="afa40-123">scripts have one or more batches.</span></span> <span data-ttu-id="afa40-124">GO 命令表示一个批处理的结束。</span><span class="sxs-lookup"><span data-stu-id="afa40-124">The GO command signals the end of a batch.</span></span> <span data-ttu-id="afa40-125">如果 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 脚本中没有 GO 命令，则该脚本将作为单个批处理来执行。</span><span class="sxs-lookup"><span data-stu-id="afa40-125">If a [!INCLUDE[tsql](../../../includes/tsql-md.md)] script does not have any GO commands, it is executed as a single batch.</span></span>  
  
-   <span data-ttu-id="afa40-126">在单个批处理中执行多个复制存储过程时，批处理中第一个存储过程后的所有存储过程前面都要有 EXECUTE 关键字。</span><span class="sxs-lookup"><span data-stu-id="afa40-126">When executing multiple replication stored procedures in a single batch, after the first procedure, all subsequent procedures in the batch must be preceded by the EXECUTE keyword.</span></span>  
  
-   <span data-ttu-id="afa40-127">在批处理执行前，该批处理中的所有存储过程都必须先编译。</span><span class="sxs-lookup"><span data-stu-id="afa40-127">All stored procedures in a batch must compile before a batch will execute.</span></span> <span data-ttu-id="afa40-128">即便如此，编译完批处理并创建了执行计划后，仍有可能出现运行时错误。</span><span class="sxs-lookup"><span data-stu-id="afa40-128">However, once the batch has been compiled, and an execution plan has been created, a run-time error may or may not occur.</span></span>  
  
-   <span data-ttu-id="afa40-129">创建脚本以配置复制时，应使用 Windows 身份验证，以避免在脚本文件中存储安全凭据。</span><span class="sxs-lookup"><span data-stu-id="afa40-129">When creating scripts to configure replication, you should use Windows Authentication to avoid storing security credentials in the script file.</span></span> <span data-ttu-id="afa40-130">如果必须在脚本文件中存储凭据，则必须保护文件以防止未经授权的访问。</span><span class="sxs-lookup"><span data-stu-id="afa40-130">If you must store credentials in a script file, you must secure the file to prevent unauthorized access.</span></span>  
  
## <a name="sample-replication-script"></a><span data-ttu-id="afa40-131">复制脚本示例</span><span class="sxs-lookup"><span data-stu-id="afa40-131">Sample Replication Script</span></span>  
 <span data-ttu-id="afa40-132">执行下面的脚本可在服务器上设置发布和分发。</span><span class="sxs-lookup"><span data-stu-id="afa40-132">The following script can be executed to setup publishing and distribution on a server.</span></span>  
  
```  
-- This script uses sqlcmd scripting variables. They are in the form  
-- $(MyVariable). For information about how to use scripting variables    
-- on the command line and in SQL Server Management Studio, see the   
-- "Executing Replication Scripts" section in the topic  
-- "Programming Replication Using System Stored Procedures".  
  
-- Install the Distributor and the distribution database.  
DECLARE @distributor AS sysname;  
DECLARE @distributionDB AS sysname;  
DECLARE @publisher AS sysname;  
DECLARE @directory AS nvarchar(500);  
DECLARE @publicationDB AS sysname;  
-- Specify the Distributor name.  
SET @distributor = $(DistPubServer);  
-- Specify the distribution database.  
SET @distributionDB = N'distribution';  
-- Specify the Publisher name.  
SET @publisher = $(DistPubServer);  
-- Specify the replication working directory.  
SET @directory = N'\\' + $(DistPubServer) + '\repldata';  
-- Specify the publication database.  
SET @publicationDB = N'AdventureWorks2012';   
  
-- Install the server MYDISTPUB as a Distributor using the defaults,  
-- including autogenerating the distributor password.  
USE master  
EXEC sp_adddistributor @distributor = @distributor;  
  
-- Create a new distribution database using the defaults, including  
-- using Windows Authentication.  
USE master  
EXEC sp_adddistributiondb @database = @distributionDB,   
    @security_mode = 1;  
GO  
  
-- Create a Publisher and enable AdventureWorks2012 for replication.  
-- Add MYDISTPUB as a publisher with MYDISTPUB as a local distributor  
-- and use Windows Authentication.  
DECLARE @distributionDB AS sysname;  
DECLARE @publisher AS sysname;  
-- Specify the distribution database.  
SET @distributionDB = N'distribution';  
-- Specify the Publisher name.  
SET @publisher = $(DistPubServer);  
  
USE [distribution]  
EXEC sp_adddistpublisher @publisher=@publisher,   
    @distribution_db=@distributionDB,   
    @security_mode = 1;  
GO  
  
```  
  
 <span data-ttu-id="afa40-133">然后，可将此脚本在本地保存为 `instdistpub.sql`，以便在需要时可运行或再次运行此脚本。</span><span class="sxs-lookup"><span data-stu-id="afa40-133">This script can then be saved locally as `instdistpub.sql` so that it can be run or rerun when needed.</span></span>  
  
 <span data-ttu-id="afa40-134">上面的脚本包含 **sqlcmd** 脚本变量，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 联机丛书中的许多复制代码示例中也使用了这些变量。</span><span class="sxs-lookup"><span data-stu-id="afa40-134">The previous script includes **sqlcmd** scripting variables, which are used in many of the replication code samples in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Books Online.</span></span> <span data-ttu-id="afa40-135">脚本变量是使用 `$(MyVariable)` 语法定义的。</span><span class="sxs-lookup"><span data-stu-id="afa40-135">Scripting variables are defined by using `$(MyVariable)` syntax.</span></span> <span data-ttu-id="afa40-136">可在命令行或在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 中将脚本变量的值传递给脚本。</span><span class="sxs-lookup"><span data-stu-id="afa40-136">Values for variables can be passed to a script at the command line or in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="afa40-137">有关详细信息，请参阅本主题中的下一部分“执行复制脚本”。</span><span class="sxs-lookup"><span data-stu-id="afa40-137">For more information, see the next section in this topic, "Executing Replication Scripts."</span></span>  
  
## <a name="executing-replication-scripts"></a><span data-ttu-id="afa40-138">执行复制脚本</span><span class="sxs-lookup"><span data-stu-id="afa40-138">Executing Replication Scripts</span></span>  
 <span data-ttu-id="afa40-139">创建完复制脚本后，可以通过下列方式之一执行所创建的复制脚本：</span><span class="sxs-lookup"><span data-stu-id="afa40-139">Once created, a replication script can be executed in one of the following ways:</span></span>  
  
### <a name="creating-a-sql-query-file-in-sql-server-management-studio"></a><span data-ttu-id="afa40-140">在 SQL Server Management Studio 中创建一个 SQL 查询文件</span><span class="sxs-lookup"><span data-stu-id="afa40-140">Creating a SQL Query File in SQL Server Management Studio</span></span>  
 <span data-ttu-id="afa40-141">可以将复制 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 脚本文件创建为 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 项目中的 SQL 查询文件。</span><span class="sxs-lookup"><span data-stu-id="afa40-141">A replication [!INCLUDE[tsql](../../../includes/tsql-md.md)] script file can be created as a SQL Query file in a [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] project.</span></span> <span data-ttu-id="afa40-142">编写完脚本后，可以为此查询文件创建一个与数据库的连接，然后即可执行该脚本。</span><span class="sxs-lookup"><span data-stu-id="afa40-142">After the script is written, a connection can be made to the database for this query file and the script can be executed.</span></span> <span data-ttu-id="afa40-143">有关如何使用创建脚本的详细信息 [!INCLUDE[tsql](../../../includes/tsql-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ，请参阅[查询和文本编辑器 &#40;SQL Server Management Studio&#41;](../../scripting/query-and-text-editors-sql-server-management-studio.md)) 。</span><span class="sxs-lookup"><span data-stu-id="afa40-143">For more information about how to create [!INCLUDE[tsql](../../../includes/tsql-md.md)] scripts by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], see [Query and Text Editors &#40;SQL Server Management Studio&#41;](../../scripting/query-and-text-editors-sql-server-management-studio.md)).</span></span>  
  
 <span data-ttu-id="afa40-144">若要使用包含脚本变量的脚本，[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 必须在 **sqlcmd** 模式下运行。</span><span class="sxs-lookup"><span data-stu-id="afa40-144">To use a script that includes scripting variables, [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] must be running in **sqlcmd** mode.</span></span> <span data-ttu-id="afa40-145">在 **sqlcmd** 模式下，查询编辑器可接受特定于 **sqlcmd** 的附加语法，如可用于变量值的 `:setvar`。</span><span class="sxs-lookup"><span data-stu-id="afa40-145">In **sqlcmd** mode, the Query Editor accepts additional syntax specific to **sqlcmd**, such as `:setvar`, which is used to a value for a variable.</span></span> <span data-ttu-id="afa40-146">有关 **sqlcmd** 模式的详细信息，请参阅[使用查询编辑器编辑 SQLCMD 脚本](../../scripting/edit-sqlcmd-scripts-with-query-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="afa40-146">For more information about **sqlcmd** mode, see [Edit SQLCMD Scripts with Query Editor](../../scripting/edit-sqlcmd-scripts-with-query-editor.md).</span></span> <span data-ttu-id="afa40-147">在下面的脚本中，`:setvar` 用于为 `$(DistPubServer)` 变量提供值。</span><span class="sxs-lookup"><span data-stu-id="afa40-147">In the following script, `:setvar` is used to provide a value for the `$(DistPubServer)` variable.</span></span>  
  
```  
:setvar DistPubServer N'MyPublisherAndDistributor';  
  
-- Install the Distributor and the distribution database.  
DECLARE @distributor AS sysname;  
DECLARE @distributionDB AS sysname;  
DECLARE @publisher AS sysname;  
DECLARE @directory AS nvarchar(500);  
DECLARE @publicationDB AS sysname;  
-- Specify the Distributor name.  
SET @distributor = $(DistPubServer);  
-- Specify the distribution database.  
SET @distributionDB = N'distribution';  
-- Specify the Publisher name.  
SET @publisher = $(DistPubServer);  
  
--  
-- Additional code goes here  
--  
```  
  
### <a name="using-the-sqlcmd-utility-from-the-command-line"></a><span data-ttu-id="afa40-148">从命令行使用 sqlcmd 实用工具</span><span class="sxs-lookup"><span data-stu-id="afa40-148">Using the sqlcmd Utility from the Command Line</span></span>  
 <span data-ttu-id="afa40-149">下面的示例说明如何在命令行中使用 [sqlcmd 实用工具](../../../tools/sqlcmd-utility.md)来执行 `instdistpub.sql` 脚本文件：</span><span class="sxs-lookup"><span data-stu-id="afa40-149">The following example shows how the command line is used to execute the `instdistpub.sql` script file using the [sqlcmd utility](../../../tools/sqlcmd-utility.md):</span></span>  
  
```  
sqlcmd.exe -E -S sqlserverinstance -i C:\instdistpub.sql -o C:\output.log -v DistPubServer="N'MyDistributorAndPublisher'"  
```  
  
 <span data-ttu-id="afa40-150">在此示例中，`-E` 开关指示连接 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 时使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="afa40-150">In this example, the `-E` switch indicates that Windows Authentication is used when connecting to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="afa40-151">使用 Windows 身份验证时，不需要在脚本文件中存储用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="afa40-151">When using Windows Authentication, there is no need to store a username and password in the script file.</span></span> <span data-ttu-id="afa40-152">脚本文件的名称和路径是通过 `-i` 开关指定的，输出文件的名称是通过 `-o` 开关指定的（使用此开关时，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的输出将写入此文件，而不是控制台）。</span><span class="sxs-lookup"><span data-stu-id="afa40-152">The name and path of the script file is specified by the `-i` switch and the name of the output file is specified by the `-o` switch (output from [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is written to this file instead of the console when this switch is used).</span></span> <span data-ttu-id="afa40-153">在 `sqlcmd` 实用工具中使用 `-v` 开关，可以在运行时向 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 脚本传递脚本变量。</span><span class="sxs-lookup"><span data-stu-id="afa40-153">The `sqlcmd` utility enables you to pass scripting variables to a [!INCLUDE[tsql](../../../includes/tsql-md.md)] script at runtime using the `-v` switch.</span></span> <span data-ttu-id="afa40-154">在此示例中，`sqlcmd` 在执行前将脚本中的每个 `$(DistPubServer)` 实例替换为值 `N'MyDistributorAndPublisher'`。</span><span class="sxs-lookup"><span data-stu-id="afa40-154">In this example, `sqlcmd` replaces every instance of `$(DistPubServer)` in the script with the value `N'MyDistributorAndPublisher'` before execution.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="afa40-155">`-X` 开关可禁用脚本变量。</span><span class="sxs-lookup"><span data-stu-id="afa40-155">The `-X` switch disables scripting variables.</span></span>  
  
### <a name="automating-tasks-in-a-batch-file"></a><span data-ttu-id="afa40-156">自动执行批处理文件中的任务</span><span class="sxs-lookup"><span data-stu-id="afa40-156">Automating Tasks in a Batch File</span></span>  
 <span data-ttu-id="afa40-157">通过使用批处理文件，可在同一批处理文件中实现复制管理任务、复制同步任务以及其他任务的自动执行。</span><span class="sxs-lookup"><span data-stu-id="afa40-157">By using a batch file, replication administration tasks, replication synchronization tasks, and other tasks can be automated in the same batch file.</span></span> <span data-ttu-id="afa40-158">下面的批处理文件使用 **sqlcmd** 实用工具删除并重新创建订阅数据库，并添加一个合并请求订阅。</span><span class="sxs-lookup"><span data-stu-id="afa40-158">The following batch file uses the **sqlcmd** utility to drop and recreate the subscription database and add a merge pull subscription.</span></span> <span data-ttu-id="afa40-159">然后，该文件调用合并代理来同步新订阅：</span><span class="sxs-lookup"><span data-stu-id="afa40-159">Then the file invokes the merge agent to synchronize the new subscription:</span></span>  
  
```  
REM ----------------------Script to synchronize merge subscription ----------------------  
REM -- Creates subscription database and   
REM -- synchronizes the subscription to MergeSalesPerson.  
REM -- Current computer acts as both Publisher and Subscriber.  
REM -------------------------------------------------------------------------------------  
  
SET Publisher=%computername%  
SET Subscriber=%computername%  
SET PubDb=AdventureWorks  
SET SubDb=AdventureWorksReplica  
SET PubName=AdvWorksSalesOrdersMerge  
  
REM -- Drop and recreate the subscription database at the Subscriber  
sqlcmd /S%Subscriber% /E /Q"USE master IF EXISTS (SELECT * FROM sysdatabases WHERE name='%SubDb%' ) DROP DATABASE %SubDb%"  
sqlcmd /S%Subscriber% /E /Q"USE master CREATE DATABASE %SubDb%"  
  
REM -- Add a pull subscription at the Subscriber  
sqlcmd /S%Subscriber% /E /Q"USE %SubDb% EXEC sp_addmergepullsubscription @publisher = %Publisher%, @publication = %PubName%, @publisher_db = %PubDb%"  
sqlcmd /S%Subscriber% /E /Q"USE %SubDb%  EXEC sp_addmergepullsubscription_agent @publisher = %Publisher%, @publisher_db = %PubDb%, @publication = %PubName%, @subscriber = %Subscriber%, @subscriber_db = %SubDb%, @distributor = %Publisher%"  
  
REM -- This batch file starts the merge agent at the Subscriber to   
REM -- synchronize a pull subscription to a merge publication.  
REM -- The following must be supplied on one line.  
"\Program Files\Microsoft SQL Server\120\COM\REPLMERG.EXE"  -Publisher  %Publisher% -Subscriber  %Subscriber%  -Distributor %Publisher%  -PublisherDB  %PubDb% -SubscriberDB %SubDb% -Publication %PubName% -PublisherSecurityMode 1 -OutputVerboseLevel 1  -Output  -SubscriberSecurityMode 1  -SubscriptionType 1 -DistributorSecurityMode 1 -Validate 3  
  
```  
  
## <a name="scripting-common-replication-tasks"></a><span data-ttu-id="afa40-160">编写常见复制任务脚本</span><span class="sxs-lookup"><span data-stu-id="afa40-160">Scripting Common Replication Tasks</span></span>  
 <span data-ttu-id="afa40-161">下面是一些可使用系统存储过程来编写脚本的最常见复制任务：</span><span class="sxs-lookup"><span data-stu-id="afa40-161">The following are some of the most common replication tasks can be scripted using system stored procedures:</span></span>  
  
-   <span data-ttu-id="afa40-162">配置发布和分发</span><span class="sxs-lookup"><span data-stu-id="afa40-162">Configuring publishing and distribution</span></span>  
  
-   <span data-ttu-id="afa40-163">修改发布服务器和分发服务器属性</span><span class="sxs-lookup"><span data-stu-id="afa40-163">Modifying Publisher and Distributor properties</span></span>  
  
-   <span data-ttu-id="afa40-164">禁用发布和分发</span><span class="sxs-lookup"><span data-stu-id="afa40-164">Disabling publishing and distribution</span></span>  
  
-   <span data-ttu-id="afa40-165">创建发布及定义项目</span><span class="sxs-lookup"><span data-stu-id="afa40-165">Creating publications and defining articles</span></span>  
  
-   <span data-ttu-id="afa40-166">删除发布和项目</span><span class="sxs-lookup"><span data-stu-id="afa40-166">Deleting publications and articles</span></span>  
  
-   <span data-ttu-id="afa40-167">创建请求订阅</span><span class="sxs-lookup"><span data-stu-id="afa40-167">Creating a pull subscription</span></span>  
  
-   <span data-ttu-id="afa40-168">修改请求订阅</span><span class="sxs-lookup"><span data-stu-id="afa40-168">Modifying a pull subscription</span></span>  
  
-   <span data-ttu-id="afa40-169">删除请求订阅</span><span class="sxs-lookup"><span data-stu-id="afa40-169">Deleting a pull subscription</span></span>  
  
-   <span data-ttu-id="afa40-170">创建推送订阅</span><span class="sxs-lookup"><span data-stu-id="afa40-170">Creating a push subscription</span></span>  
  
-   <span data-ttu-id="afa40-171">修改推送订阅</span><span class="sxs-lookup"><span data-stu-id="afa40-171">Modifying a push subscription</span></span>  
  
-   <span data-ttu-id="afa40-172">删除推送订阅</span><span class="sxs-lookup"><span data-stu-id="afa40-172">Deleting a push subscription</span></span>  
  
-   <span data-ttu-id="afa40-173">同步请求订阅</span><span class="sxs-lookup"><span data-stu-id="afa40-173">Synchronizing a pull subscription</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afa40-174">另请参阅</span><span class="sxs-lookup"><span data-stu-id="afa40-174">See Also</span></span>  
 <span data-ttu-id="afa40-175">[复制编程概念](replication-programming-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="afa40-175">[Replication Programming Concepts](replication-programming-concepts.md) </span></span>  
 <span data-ttu-id="afa40-176">[复制存储过程 &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="afa40-176">[Replication Stored Procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql) </span></span>  
 [<span data-ttu-id="afa40-177">编写复制脚本</span><span class="sxs-lookup"><span data-stu-id="afa40-177">Scripting Replication</span></span>](../scripting-replication.md)  
  
  
