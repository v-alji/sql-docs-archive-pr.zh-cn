---
title: 使用 DAC 部署数据库 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.dbdeployment.settings.f1
- sql12.swb.dbdeployment.progress.f1
- sql12.swb.dbdeployment.summary.f1
- sql12.swb.dbdeployment.results.f1
- sql12.swb.dbdeployment.welcome.f1
helpviewer_keywords:
- deploy database wizard
- database deploy [SQL Server]
ms.assetid: 08c506e8-4ba0-4a19-a066-6e6a5c420539
author: stevestein
ms.author: sstein
ms.openlocfilehash: f753cfaf44e51b5bd3ffb939e38e2a300acb9703
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692956"
---
# <a name="deploy-a-database-by-using-a-dac"></a><span data-ttu-id="cf0db-102">使用 DAC 部署数据库</span><span class="sxs-lookup"><span data-stu-id="cf0db-102">Deploy a Database By Using a DAC</span></span>
  <span data-ttu-id="cf0db-103">使用“将数据库部署到 SQL Azure”  向导在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例与 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] 服务器之间，或在两台 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]服务器之间部署数据库。</span><span class="sxs-lookup"><span data-stu-id="cf0db-103">Use the **Deploy a Database to SQL Azure** Wizard to deploy a database between an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and a [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] server, or between two [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]servers.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeBegin"></a> <span data-ttu-id="cf0db-104">开始之前</span><span class="sxs-lookup"><span data-stu-id="cf0db-104">Before You Begin</span></span>  
 <span data-ttu-id="cf0db-105">该向导使用数据层应用程序 (DAC) BACPAC 存档文件部署数据库对象的数据和定义。</span><span class="sxs-lookup"><span data-stu-id="cf0db-105">The wizard uses a Data-tier Application (DAC) BACPAC archive file to deploy both the data and the definitions of database objects.</span></span> <span data-ttu-id="cf0db-106">它从源数据库执行 DAC 导出操作，并对目标执行 DAC 导入。</span><span class="sxs-lookup"><span data-stu-id="cf0db-106">It performs a DAC export operation from the source database, and a DAC import to the destination.</span></span>  
  
###  <a name="database-options-and-settings"></a><a name="DBOptSettings"></a> <span data-ttu-id="cf0db-107">数据库选项和设置</span><span class="sxs-lookup"><span data-stu-id="cf0db-107">Database Options and Settings</span></span>  
 <span data-ttu-id="cf0db-108">默认情况下，在部署过程中创建的数据库将具有来自 CREATE DATABASE 语句的默认设置。</span><span class="sxs-lookup"><span data-stu-id="cf0db-108">By default, the database created during the deployment will have the default settings from the CREATE DATABASE statement.</span></span> <span data-ttu-id="cf0db-109">例外是数据库集合和兼容级别将设置为源数据库中的值。</span><span class="sxs-lookup"><span data-stu-id="cf0db-109">The exception is that the database collation and compatibility level are set to the values from the source database.</span></span>  
  
 <span data-ttu-id="cf0db-110">数据库选项（如 TRUSTWORTHY、DB_CHAINING 和 HONOR_BROKER_PRIORITY）不能作为部署过程的一部分进行调整。</span><span class="sxs-lookup"><span data-stu-id="cf0db-110">Database options, such as TRUSTWORTHY, DB_CHAINING and HONOR_BROKER_PRIORITY, cannot be adjusted as part of the deployment process.</span></span> <span data-ttu-id="cf0db-111">物理属性（例如文件组的数目或者文件的数目和大小）不能作为部署过程的一部分进行更改。</span><span class="sxs-lookup"><span data-stu-id="cf0db-111">Physical properties, such as the number of filegroups, or the numbers and sizes of files cannot be altered as part of the deployment process.</span></span> <span data-ttu-id="cf0db-112">在部署完成后，可以使用 ALTER DATABASE 语句、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell 对数据库进行定制。</span><span class="sxs-lookup"><span data-stu-id="cf0db-112">After the deployment completes, you can use the ALTER DATABASE statement, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell to tailor the database.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="cf0db-113">限制和局限</span><span class="sxs-lookup"><span data-stu-id="cf0db-113">Limitations and Restrictions</span></span>  
 <span data-ttu-id="cf0db-114">**“部署数据库”** 向导支持：</span><span class="sxs-lookup"><span data-stu-id="cf0db-114">The **Deploy Database** wizard supports deploying a database:</span></span>  
  
-   <span data-ttu-id="cf0db-115">将数据库从 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的实例部署到 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="cf0db-115">From an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].</span></span>  
  
-   <span data-ttu-id="cf0db-116">将数据库从 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] 部署到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="cf0db-116">From [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
-   <span data-ttu-id="cf0db-117">在两台 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] 服务器之间部署数据库。</span><span class="sxs-lookup"><span data-stu-id="cf0db-117">Between two [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] servers.</span></span>  
  
 <span data-ttu-id="cf0db-118">此向导不支持在 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的两个实例之间部署数据库。</span><span class="sxs-lookup"><span data-stu-id="cf0db-118">The wizard does not support deploying databases between two instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
 <span data-ttu-id="cf0db-119">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 的实例必须运行 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) 或更高版本才能使用此向导。</span><span class="sxs-lookup"><span data-stu-id="cf0db-119">An instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] must be running [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) or later to work with the wizard.</span></span> <span data-ttu-id="cf0db-120">如果 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的实例上的数据库包含 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]上不支持的对象，则无法使用该向导将数据库部署到 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="cf0db-120">If a database on an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] contains objects not supported on [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], you cannot use the wizard to deploy the database to [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].</span></span> <span data-ttu-id="cf0db-121">如果 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] 上的数据库包含 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]不支持的对象，则您无法使用该向导将数据库部署到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="cf0db-121">If a database on [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] contains objects not supported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you cannot use the wizard to deploy the database to instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="cf0db-122">Security</span><span class="sxs-lookup"><span data-stu-id="cf0db-122">Security</span></span>  
 <span data-ttu-id="cf0db-123">为了提高安全性，SQL Server 身份验证登录名存储在 DAC BACPAC 文件中且没有密码。</span><span class="sxs-lookup"><span data-stu-id="cf0db-123">To improve security, SQL Server Authentication logins are stored in a DAC BACPAC file without a password.</span></span> <span data-ttu-id="cf0db-124">在导入此 BACPAC 时，登录名将作为含有生成的密码的已禁用登录名创建。</span><span class="sxs-lookup"><span data-stu-id="cf0db-124">When the BACPAC is imported, the login is created as a disabled login with a generated password.</span></span> <span data-ttu-id="cf0db-125">若要启用这些登录名，请使用具有 ALTER ANY LOGIN 权限的登录名登录，并且使用 ALTER LOGIN 来启用该登录名并且分配可以传达给用户的新密码。</span><span class="sxs-lookup"><span data-stu-id="cf0db-125">To enable the logins, log in using a login that has ALTER ANY LOGIN permission and use ALTER LOGIN to enable the login and assign a new password that can be communicated to the user.</span></span> <span data-ttu-id="cf0db-126">对于 Windows 身份验证登录名则无需执行此操作，因为其密码不是由 SQL Server 管理的。</span><span class="sxs-lookup"><span data-stu-id="cf0db-126">This is not needed for Windows Authentication logins because their passwords are not managed by SQL Server.</span></span>  
  
#### <a name="permissions"></a><span data-ttu-id="cf0db-127">权限</span><span class="sxs-lookup"><span data-stu-id="cf0db-127">Permissions</span></span>  
 <span data-ttu-id="cf0db-128">此向导需要对源数据库具有 DAC 导出权限。</span><span class="sxs-lookup"><span data-stu-id="cf0db-128">The wizard requires DAC export permissions on the source database.</span></span> <span data-ttu-id="cf0db-129">登录名至少要求 ALTER ANY LOGIN 和数据库作用域 VIEW DEFINITION 权限，以及对 **sys.sql_expression_dependencies**具有 SELECT 权限。</span><span class="sxs-lookup"><span data-stu-id="cf0db-129">The login requires at least ALTER ANY LOGIN and database scope VIEW DEFINITION permissions, as well as SELECT permissions on **sys.sql_expression_dependencies**.</span></span> <span data-ttu-id="cf0db-130">导出 DAC 可由 securityadmin 固定服务器角色的成员（也是从其导出 DAC 的数据库中 database_owner 固定数据库角色的成员）完成。</span><span class="sxs-lookup"><span data-stu-id="cf0db-130">Exporting a DAC can be done by members of the securityadmin fixed server role who are also members of the database_owner fixed database role in the database from which the DAC is exported.</span></span> <span data-ttu-id="cf0db-131">sysadmin 固定服务器角色的成员或名为 **sa** 的内置 SQL Server 系统管理员帐户也可以导出 DAC。</span><span class="sxs-lookup"><span data-stu-id="cf0db-131">Members of the sysadmin fixed server role or the built-in SQL Server system administrator account named **sa** can also export a DAC.</span></span>  
  
 <span data-ttu-id="cf0db-132">此向导需要对目标实例或服务器的 DAC 导入权限。</span><span class="sxs-lookup"><span data-stu-id="cf0db-132">The wizard requires DAC import permissions on the destination instance or server.</span></span> <span data-ttu-id="cf0db-133">登录名必须是 **sysadmin** 或 **serveradmin** 固定服务器角色的成员，或者是 **dbcreator** 固定服务器角色的成员并且具有 ALTER ANY LOGIN 权限。</span><span class="sxs-lookup"><span data-stu-id="cf0db-133">The login must be a member of the **sysadmin** or **serveradmin** fixed server roles, or in the **dbcreator** fixed server role and have ALTER ANY LOGIN permissions.</span></span> <span data-ttu-id="cf0db-134">名为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sa **的内置** 系统管理员帐户也可以导入 DAC。</span><span class="sxs-lookup"><span data-stu-id="cf0db-134">The built-in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator account named **sa** can also import a DAC.</span></span> <span data-ttu-id="cf0db-135">将具有登录名的 DAC 导入到 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 要求 loginmanager 或 serveradmin 角色的成员身份。</span><span class="sxs-lookup"><span data-stu-id="cf0db-135">Importing a DAC with logins to [!INCLUDE[ssSDS](../../includes/sssds-md.md)] requires membership in the loginmanager or serveradmin roles.</span></span> <span data-ttu-id="cf0db-136">将不具有登录名的 DAC 导入到 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 要求 dbmanager 或 serveradmin 角色的成员身份。</span><span class="sxs-lookup"><span data-stu-id="cf0db-136">Importing a DAC without logins to [!INCLUDE[ssSDS](../../includes/sssds-md.md)] requires membership in the dbmanager or serveradmin roles.</span></span>  
  
##  <a name="using-the-deploy-database-wizard"></a><a name="UsingDeployDACWizard"></a> <span data-ttu-id="cf0db-137">使用部署数据库向导</span><span class="sxs-lookup"><span data-stu-id="cf0db-137">Using the Deploy Database Wizard</span></span>  
 <span data-ttu-id="cf0db-138">**使用部署数据库向导迁移数据库**</span><span class="sxs-lookup"><span data-stu-id="cf0db-138">**To migrate a database using the Deploy Database Wizard**</span></span>  
  
1.  <span data-ttu-id="cf0db-139">连接到您要部署的数据库的位置。</span><span class="sxs-lookup"><span data-stu-id="cf0db-139">Connect to the location of the database you want to deploy.</span></span> <span data-ttu-id="cf0db-140">只能指定 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的实例或 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] 服务器。</span><span class="sxs-lookup"><span data-stu-id="cf0db-140">You can specify either an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] or a [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] server.</span></span>  
  
2.  <span data-ttu-id="cf0db-141">在 **“对象资源管理器”** 中，展开包含数据库的实例的节点。</span><span class="sxs-lookup"><span data-stu-id="cf0db-141">In **Object Explorer**, expand the node for the instance that has the database.</span></span>  
  
3.  <span data-ttu-id="cf0db-142">展开 **“数据库”** 节点。</span><span class="sxs-lookup"><span data-stu-id="cf0db-142">Expand the **Databases** node.</span></span>  
  
4.  <span data-ttu-id="cf0db-143">右键单击要部署的数据库，选择 “任务”，然后选择“将数据库部署到 SQL Azure…”  </span><span class="sxs-lookup"><span data-stu-id="cf0db-143">Right click the database you want to deploy, select **Tasks**, and then select **Deploy Database to SQL Azure...**</span></span>  
  
5.  <span data-ttu-id="cf0db-144">完成向导对话框：</span><span class="sxs-lookup"><span data-stu-id="cf0db-144">Complete the Wizard dialogs:</span></span>  
  
    -   [<span data-ttu-id="cf0db-145">“简介”页</span><span class="sxs-lookup"><span data-stu-id="cf0db-145">Introduction Page</span></span>](#Introduction)  
  
    -   [<span data-ttu-id="cf0db-146">“部署设置”</span><span class="sxs-lookup"><span data-stu-id="cf0db-146">Deployment Settings</span></span>](#Deployment_settings)  
  
    -   [<span data-ttu-id="cf0db-147">摘要页</span><span class="sxs-lookup"><span data-stu-id="cf0db-147">Summary Page</span></span>](#Summary)  
  
    -   [<span data-ttu-id="cf0db-148">结果</span><span class="sxs-lookup"><span data-stu-id="cf0db-148">Results</span></span>](#Results)  
  
##  <a name="introduction-page"></a><a name="Introduction"></a> <span data-ttu-id="cf0db-149">“简介”页</span><span class="sxs-lookup"><span data-stu-id="cf0db-149">Introduction Page</span></span>  
 <span data-ttu-id="cf0db-150">此页说明 **“部署数据库”** 向导的步骤。</span><span class="sxs-lookup"><span data-stu-id="cf0db-150">This page describes the steps for the **Deploy Database** Wizard.</span></span>  
  
 <span data-ttu-id="cf0db-151">**选项**</span><span class="sxs-lookup"><span data-stu-id="cf0db-151">**Options**</span></span>  
  
-   <span data-ttu-id="cf0db-152">**不再显示此页。**</span><span class="sxs-lookup"><span data-stu-id="cf0db-152">**Do not show this page again.**</span></span> <span data-ttu-id="cf0db-153">- 选中此复选框可以停止在将来显示“简介”页。</span><span class="sxs-lookup"><span data-stu-id="cf0db-153">- Click the check box to stop the Introduction page from being displayed in the future.</span></span>  
  
-   <span data-ttu-id="cf0db-154">**下一步** - 进入 **“部署设置”** 页。</span><span class="sxs-lookup"><span data-stu-id="cf0db-154">**Next** - Proceeds to the **Deployment Settings** page.</span></span>  
  
-   <span data-ttu-id="cf0db-155">**取消**-取消操作并关闭向导。</span><span class="sxs-lookup"><span data-stu-id="cf0db-155">**Cancel** - Cancels the operation and closes the Wizard.</span></span>  
  
##  <a name="deployment-settings-page"></a><a name="Deployment_settings"></a><span data-ttu-id="cf0db-156">部署设置页</span><span class="sxs-lookup"><span data-stu-id="cf0db-156">Deployment Settings Page</span></span>  
 <span data-ttu-id="cf0db-157">使用此页可以指定目标服务器并提供有关新数据库的详细信息。</span><span class="sxs-lookup"><span data-stu-id="cf0db-157">Use this page to specify the destination server and to provide details about your new database.</span></span>  
  
 <span data-ttu-id="cf0db-158">**本地主机：**</span><span class="sxs-lookup"><span data-stu-id="cf0db-158">**Local host:**</span></span>  
  
-   <span data-ttu-id="cf0db-159">**服务器连接**-指定服务器连接详细信息，然后单击 "**连接**" 以验证连接。</span><span class="sxs-lookup"><span data-stu-id="cf0db-159">**Server connection** - Specify server connection details and then click **Connect** to verify the connection.</span></span>  
  
-   <span data-ttu-id="cf0db-160">**新数据库名称**-指定新数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="cf0db-160">**New database name** - Specify a name for the new database.</span></span>  
  
 <span data-ttu-id="cf0db-161">**[!INCLUDE[ssSDS](../../includes/sssds-md.md)]数据库设置：**</span><span class="sxs-lookup"><span data-stu-id="cf0db-161">**[!INCLUDE[ssSDS](../../includes/sssds-md.md)] database settings:**</span></span>  
  
-   <span data-ttu-id="cf0db-162">\*\* [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 版本\*\*- [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 从下拉菜单中选择的版本。</span><span class="sxs-lookup"><span data-stu-id="cf0db-162">**[!INCLUDE[ssSDS](../../includes/sssds-md.md)] edition** - Select the edition of [!INCLUDE[ssSDS](../../includes/sssds-md.md)] from the drop-down menu.</span></span>  
  
-   <span data-ttu-id="cf0db-163">**最大数据库大小** - 从下拉菜单中选择最大数据库大小。</span><span class="sxs-lookup"><span data-stu-id="cf0db-163">**Maximum database size** - Select the maximum database size from the drop-down menu.</span></span>  
  
 <span data-ttu-id="cf0db-164">**其他设置：**</span><span class="sxs-lookup"><span data-stu-id="cf0db-164">**Other settings:**</span></span>  
  
-   <span data-ttu-id="cf0db-165">指定临时文件的本地目录，该文件为 BACPAC 存档文件。</span><span class="sxs-lookup"><span data-stu-id="cf0db-165">Specify a local directory for the temporary file, which is the BACPAC archive file.</span></span> <span data-ttu-id="cf0db-166">请注意，将在指定位置创建此文件，并且在操作完成后，此文件将保留在该位置。</span><span class="sxs-lookup"><span data-stu-id="cf0db-166">Note that the file will be created at the specified location and will remain there after the operation completes.</span></span>  
  
##  <a name="summary-page"></a><a name="Summary"></a> <span data-ttu-id="cf0db-167">摘要页</span><span class="sxs-lookup"><span data-stu-id="cf0db-167">Summary Page</span></span>  
 <span data-ttu-id="cf0db-168">使用此页可查看操作的指定的源和目标设置。</span><span class="sxs-lookup"><span data-stu-id="cf0db-168">Use this page to review the specified source and target settings for the operation.</span></span> <span data-ttu-id="cf0db-169">若要使用指定设置完成部署操作，请单击 **“完成”**。</span><span class="sxs-lookup"><span data-stu-id="cf0db-169">To complete the deploy operation using the specified settings, click **Finish**.</span></span> <span data-ttu-id="cf0db-170">若要取消部署操作并退出向导，请单击 **“取消”**。</span><span class="sxs-lookup"><span data-stu-id="cf0db-170">To cancel the deploy operation and exit the Wizard, click **Cancel**.</span></span>  
  
##  <a name="progress-page"></a><a name="Progress"></a> <span data-ttu-id="cf0db-171">“进度”页</span><span class="sxs-lookup"><span data-stu-id="cf0db-171">Progress Page</span></span>  
 <span data-ttu-id="cf0db-172">此页将显示一个指示操作状态的进度栏。</span><span class="sxs-lookup"><span data-stu-id="cf0db-172">This page displays a progress bar that indicates the status of the operation.</span></span> <span data-ttu-id="cf0db-173">若要查看详细状态，请单击 **“查看详细信息”** 选项。</span><span class="sxs-lookup"><span data-stu-id="cf0db-173">To view detailed status, click the **View details** option.</span></span>  
  
##  <a name="results-page"></a><a name="Results"></a><span data-ttu-id="cf0db-174">结果页</span><span class="sxs-lookup"><span data-stu-id="cf0db-174">Results Page</span></span>  
 <span data-ttu-id="cf0db-175">此页将报告部署操作是成功还是失败，并显示每个操作的结果。</span><span class="sxs-lookup"><span data-stu-id="cf0db-175">This page reports the success or failure of the deploy operation, showing the results of each action.</span></span> <span data-ttu-id="cf0db-176">遇到了错误的任何操作都将在 **“结果”** 列中具有一个链接。</span><span class="sxs-lookup"><span data-stu-id="cf0db-176">Any action that encountered an error will have a link in the **Result** column.</span></span> <span data-ttu-id="cf0db-177">单击该链接可以查看针对该操作的错误报告。</span><span class="sxs-lookup"><span data-stu-id="cf0db-177">Click the link to view a report of the error for that action.</span></span>  
  
 <span data-ttu-id="cf0db-178">单击 "**完成**" 关闭向导。</span><span class="sxs-lookup"><span data-stu-id="cf0db-178">Click **Finish** to close the Wizard.</span></span>  
  
## <a name="using-a-net-framework-application"></a><span data-ttu-id="cf0db-179">使用 .Net Framework 应用程序</span><span class="sxs-lookup"><span data-stu-id="cf0db-179">Using a .Net Framework Application</span></span>  
 <span data-ttu-id="cf0db-180">**使用 .Net Framework 应用程序中的 DacStoreExport() 和 Import() 方法来部署数据库。**</span><span class="sxs-lookup"><span data-stu-id="cf0db-180">**To deploy a database using the DacStoreExport() and Import() methods in a .Net Framework application.**</span></span>  
  
 <span data-ttu-id="cf0db-181">若要查看代码示例，请下载有关 [Codeplex](https://go.microsoft.com/fwlink/?LinkId=219575)的 DAC 示例应用程序</span><span class="sxs-lookup"><span data-stu-id="cf0db-181">To view a code example, download the DAC sample application on [Codeplex](https://go.microsoft.com/fwlink/?LinkId=219575)</span></span>  
  
1.  <span data-ttu-id="cf0db-182">创建一个 SMO Server 对象，并将该对象设置为包含要部署的数据库的实例或服务器。</span><span class="sxs-lookup"><span data-stu-id="cf0db-182">Create a SMO Server object and set it to the instance or server that contains the database to be deployed.</span></span>  
  
2.  <span data-ttu-id="cf0db-183">打开 `ServerConnection` 对象，并连接到同一实例。</span><span class="sxs-lookup"><span data-stu-id="cf0db-183">Open a `ServerConnection` object and connect to the same instance.</span></span>  
  
3.  <span data-ttu-id="cf0db-184">使用 `Export` 类型的 `Microsoft.SqlServer.Management.Dac.DacStore` 方法将数据库导出到 BACPAC 文件。</span><span class="sxs-lookup"><span data-stu-id="cf0db-184">Use the `Export` method of the `Microsoft.SqlServer.Management.Dac.DacStore` type to export the database to a BACPAC file.</span></span> <span data-ttu-id="cf0db-185">指定要导出的数据库的名称以及指向将用于放置 BACPAC 文件的文件夹的路径。</span><span class="sxs-lookup"><span data-stu-id="cf0db-185">Specify the name of the database to be exported, and the path to the folder where the BACPAC file is to be placed.</span></span>  
  
4.  <span data-ttu-id="cf0db-186">创建一个 SMO Server 对象，并将该对象设置为目标实例或服务器。</span><span class="sxs-lookup"><span data-stu-id="cf0db-186">Create a SMO Server object and set it to the destination instance or server.</span></span>  
  
5.  <span data-ttu-id="cf0db-187">打开 `ServerConnection` 对象，并连接到同一实例。</span><span class="sxs-lookup"><span data-stu-id="cf0db-187">Open a `ServerConnection` object and connect to the same instance.</span></span>  
  
6.  <span data-ttu-id="cf0db-188">使用 `Import` 类型的 `Microsoft.SqlServer.Management.Dac.DacStore` 方法导入 BACPAC。</span><span class="sxs-lookup"><span data-stu-id="cf0db-188">Use the `Import` method of the `Microsoft.SqlServer.Management.Dac.DacStore` type to import the BACPAC.</span></span> <span data-ttu-id="cf0db-189">指定导出创建的 BACPAC 文件。</span><span class="sxs-lookup"><span data-stu-id="cf0db-189">Specify the BACPAC file created by the export.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf0db-190">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cf0db-190">See Also</span></span>  
 <span data-ttu-id="cf0db-191">[数据层应用程序](data-tier-applications.md) </span><span class="sxs-lookup"><span data-stu-id="cf0db-191">[Data-tier Applications](data-tier-applications.md) </span></span>  
 <span data-ttu-id="cf0db-192">[导出数据层应用程序](export-a-data-tier-application.md) </span><span class="sxs-lookup"><span data-stu-id="cf0db-192">[Export a Data-tier Application](export-a-data-tier-application.md) </span></span>  
 [<span data-ttu-id="cf0db-193">导入 BACPAC 文件以创建新的用户数据库</span><span class="sxs-lookup"><span data-stu-id="cf0db-193">Import a BACPAC File to Create a New User Database</span></span>](import-a-bacpac-file-to-create-a-new-user-database.md)  
  
  
