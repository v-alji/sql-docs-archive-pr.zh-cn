---
title: 导入 BACPAC 文件以创建新的用户数据库 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.importdac.progress.f1
- sql12.swb. importdac.settings.f1
- sql12.swb.importdac.storagebrowser.f1
- sql12.swb. importdac.summary.f1
- sql12.swb.importdac.results.f1
- sql12.swb. importdac.progress.f1
- sql12.swb.importdac.welcome.f1
- sql12.swb.importdac.settings.f1
- sql12.swb. importdac.results.f1
- sql12.swb.importdac.summary.f1
helpviewer_keywords:
- Data-tier application
- SQL Server DAC
- Migrate database
- DAC
ms.assetid: 736d8d9a-39f1-4bf8-b81f-2e56c134d12e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 66e71453f38fe15f295fceaf63b5edba5ab5ff43
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589141"
---
# <a name="import-a-bacpac-file-to-create-a-new-user-database"></a><span data-ttu-id="06483-102">导入 BACPAC 文件以创建新的用户数据库</span><span class="sxs-lookup"><span data-stu-id="06483-102">Import a BACPAC File to Create a New User Database</span></span>
  <span data-ttu-id="06483-103">导入数据层应用程序 (DAC) 文件 - .bacpac 文件 - 以在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的新实例上创建一个带数据的原始数据库的副本，或者对 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] 创建一个此数据库的副本。</span><span class="sxs-lookup"><span data-stu-id="06483-103">Import a data-tier application (DAC) file - a .bacpac file - to create a copy of the original database, with the data, on a new instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], or to [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].</span></span> <span data-ttu-id="06483-104">可以将导出-导入操作结合起来在各实例之间迁移 DAC 或数据库，或者创建一个逻辑备份，例如创建部署在 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]中的数据库的本地副本。</span><span class="sxs-lookup"><span data-stu-id="06483-104">Export-import operations can be combined to migrate a DAC or database between instances, or to create a logical backup, such as creating an on-premise copy of a database deployed in [!INCLUDE[ssSDS](../../includes/sssds-md.md)].</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="06483-105">开始之前</span><span class="sxs-lookup"><span data-stu-id="06483-105">Before You Begin</span></span>  
 <span data-ttu-id="06483-106">导入过程分两个阶段生成新的 DAC。</span><span class="sxs-lookup"><span data-stu-id="06483-106">The import process builds a new DAC in two stages.</span></span>  
  
1.  <span data-ttu-id="06483-107">导入过程使用存储在导出文件中的 DAC 定义创建新的 DAC 和关联的数据库，同样，DAC 部署使用 DAC 包文件中的定义创建新的 DAC。</span><span class="sxs-lookup"><span data-stu-id="06483-107">The import creates a new DAC and associated database using the DAC definition stored in the export file, the same way a DAC deploy creates a new DAC from the definition in a DAC package file.</span></span>  
  
2.  <span data-ttu-id="06483-108">导入过程将从导出文件中大容量复制数据。</span><span class="sxs-lookup"><span data-stu-id="06483-108">The import bulk copies in the data from the export file.</span></span>  
  
 
## <a name="sql-server-utility"></a><span data-ttu-id="06483-109">SQL Server 实用工具</span><span class="sxs-lookup"><span data-stu-id="06483-109">SQL Server Utility</span></span>  
 <span data-ttu-id="06483-110">如果您将 DAC 导入到数据库引擎的托管实例，则在下次将实用工具收集组从该实例发送到实用工具控制点时，导入的 DAC 将合并到 SQL Server 实用工具中。</span><span class="sxs-lookup"><span data-stu-id="06483-110">If you import a DAC to a managed instance of the Database Engine, the imported DAC is incorporated into the SQL Server Utility the next time the utility collection set is sent from the instance to the utility control point.</span></span> <span data-ttu-id="06483-111">然后，该 DAC 将出现在  **实用工具资源管理器的“已部署的数据层应用程序”节点中，并且将在“已部署的数据层应用程序”的详细信息页面中报告**[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]   。</span><span class="sxs-lookup"><span data-stu-id="06483-111">The DAC will then be present in the **Deployed Data-tier Applications** node of the [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] **Utility Explorer** and reported in the **Deployed Data-tier Applications** details page.</span></span>  
  
## <a name="database-options-and-settings"></a><span data-ttu-id="06483-112">数据库选项和设置</span><span class="sxs-lookup"><span data-stu-id="06483-112">Database Options and Settings</span></span>  
 <span data-ttu-id="06483-113">默认情况下，在导入过程中创建的数据库将具有来自 CREATE DATABASE 语句的几乎所有默认设置，而例外的是数据库排序规则和兼容级别设置为在 DAC 导出文件中定义的值。</span><span class="sxs-lookup"><span data-stu-id="06483-113">By default, the database created during the import will have all of the default settings from the CREATE DATABASE statement, except that the database collation and compatibility level are set to the values defined in the DAC export file.</span></span> <span data-ttu-id="06483-114">DAC 导出文件将使用来自原始数据库的值。</span><span class="sxs-lookup"><span data-stu-id="06483-114">A DAC export file uses the values from the original database.</span></span>  
  
 <span data-ttu-id="06483-115">某些数据库选项（例如 TRUSTWORTHY、DB_CHAINING 和 HONOR_BROKER_PRIORITY）不能作为导入过程的一部分进行调整。</span><span class="sxs-lookup"><span data-stu-id="06483-115">Some database options, such as TRUSTWORTHY, DB_CHAINING, and HONOR_BROKER_PRIORITY, cannot be adjusted as part of the import process.</span></span> <span data-ttu-id="06483-116">物理属性（如文件组的数目或文件的数目和大小）不能作为导入过程的一部分进行更改。</span><span class="sxs-lookup"><span data-stu-id="06483-116">Physical properties, such as the number of filegroups, or the numbers and sizes of files cannot be altered as part of the import process.</span></span> <span data-ttu-id="06483-117">在导入完成后，可以使用 ALTER DATABASE 语句、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell 对数据库进行定制。</span><span class="sxs-lookup"><span data-stu-id="06483-117">After the import completes, you can use the ALTER DATABASE statement, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell to tailor the database.</span></span> <span data-ttu-id="06483-118">有关详细信息，请参阅 [Databases](../databases/databases.md)。</span><span class="sxs-lookup"><span data-stu-id="06483-118">For more information, see [Databases](../databases/databases.md).</span></span>  
  
## <a name="limitations-and-restrictions"></a><span data-ttu-id="06483-119">限制和局限</span><span class="sxs-lookup"><span data-stu-id="06483-119">Limitations and Restrictions</span></span>  
 <span data-ttu-id="06483-120">可以将 DAC 导入到 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]或运行 [!INCLUDE[ssDE](../../includes/ssde-md.md)] Service Pack 4 (SP4) 或更高版本的 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="06483-120">A DAC can be imported to [!INCLUDE[ssSDS](../../includes/sssds-md.md)], or an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] running [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) or later.</span></span> <span data-ttu-id="06483-121">如果从更高版本中导出 DAC，则 DAC 可能包含 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]不支持的对象。</span><span class="sxs-lookup"><span data-stu-id="06483-121">If you export a DAC from a higher version, the DAC may contain objects not supported by [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="06483-122">您不能将这些 DAC 部署到 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]实例。</span><span class="sxs-lookup"><span data-stu-id="06483-122">You cannot deploy those DACs to instances of [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="06483-123">必备条件</span><span class="sxs-lookup"><span data-stu-id="06483-123">Prerequisites</span></span>  
 <span data-ttu-id="06483-124">建议您不要从未知或不可信的源导入 DAC 导出文件。</span><span class="sxs-lookup"><span data-stu-id="06483-124">We recommend that you do not import a DAC export file from unknown or untrusted sources.</span></span> <span data-ttu-id="06483-125">此类文件可能包含恶意代码，这些代码可能会执行非预期的 Transact-SQL 代码，或者通过修改架构导致错误。</span><span class="sxs-lookup"><span data-stu-id="06483-125">Such files could contain malicious code that might execute unintended Transact-SQL code or cause errors by modifying the schema.</span></span> <span data-ttu-id="06483-126">在使用来自未知或不可信源的导出文件之前，请解压缩该 DAC 并检查代码，例如存储过程或者其他用户定义的代码。</span><span class="sxs-lookup"><span data-stu-id="06483-126">Before you use an export file from an unknown or untrusted source, unpack the DAC and examine the code, like stored procedures and other user-defined code.</span></span> <span data-ttu-id="06483-127">有关如何执行这些检查的详细信息，请参阅 [Validate a DAC Package](validate-a-dac-package.md)。</span><span class="sxs-lookup"><span data-stu-id="06483-127">For more information about how to perform these checks, see [Validate a DAC Package](validate-a-dac-package.md).</span></span>  
  
## <a name="security"></a><span data-ttu-id="06483-128">安全性</span><span class="sxs-lookup"><span data-stu-id="06483-128">Security</span></span>  
 <span data-ttu-id="06483-129">为了提高安全性，SQL Server 身份验证登录名存储在 DAC 导出文件中且没有密码。</span><span class="sxs-lookup"><span data-stu-id="06483-129">To improve security, SQL Server Authentication logins are stored in a DAC export file without a password.</span></span> <span data-ttu-id="06483-130">在导入该文件时，登录名将作为含有生成的密码的已禁用登录名创建。</span><span class="sxs-lookup"><span data-stu-id="06483-130">When the file is imported, the login is created as a disabled login with a generated password.</span></span> <span data-ttu-id="06483-131">若要启用这些登录名，请使用具有 ALTER ANY LOGIN 权限的登录名登录，并且使用 ALTER LOGIN 来启用该登录名并且分配可以传达给用户的新密码。</span><span class="sxs-lookup"><span data-stu-id="06483-131">To enable the logins, log in using a login that has ALTER ANY LOGIN permission and use ALTER LOGIN to enable the login and assign a new password that can be communicated to the user.</span></span> <span data-ttu-id="06483-132">对于 Windows 身份验证登录名则无需执行此操作，因为其密码不是由 SQL Server 管理的。</span><span class="sxs-lookup"><span data-stu-id="06483-132">This is not needed for Windows Authentication logins because their passwords are not managed by SQL Server.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="06483-133">权限</span><span class="sxs-lookup"><span data-stu-id="06483-133">Permissions</span></span>  
 <span data-ttu-id="06483-134">DAC 只能由 **sysadmin** 或 **serveradmin** 固定服务器角色的成员导入，或者由具有 **dbcreator** 固定服务器角色且具有 ALTER ANY LOGIN 权限的登录名导入。</span><span class="sxs-lookup"><span data-stu-id="06483-134">A DAC can only be imported by members of the **sysadmin** or **serveradmin** fixed server roles, or by logins that are in the **dbcreator** fixed server role and have ALTER ANY LOGIN permissions.</span></span> <span data-ttu-id="06483-135">名为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sa **的内置** 系统管理员帐户也可以导入 DAC。</span><span class="sxs-lookup"><span data-stu-id="06483-135">The built-in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator account named **sa** can also import a DAC.</span></span> <span data-ttu-id="06483-136">将具有登录名的 DAC 导入到 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 要求 loginmanager 或 serveradmin 角色的成员身份。</span><span class="sxs-lookup"><span data-stu-id="06483-136">Importing a DAC with logins to [!INCLUDE[ssSDS](../../includes/sssds-md.md)] requires membership in the loginmanager or serveradmin roles.</span></span> <span data-ttu-id="06483-137">将不具有登录名的 DAC 导入到 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 要求 dbmanager 或 serveradmin 角色的成员身份。</span><span class="sxs-lookup"><span data-stu-id="06483-137">Importing a DAC without logins to [!INCLUDE[ssSDS](../../includes/sssds-md.md)] requires membership in the dbmanager or serveradmin roles.</span></span>  
  
## <a name="using-the-import-data-tier-application-wizard"></a><span data-ttu-id="06483-138">使用“导入数据层应用程序向导”</span><span class="sxs-lookup"><span data-stu-id="06483-138">Using the Import Data-tier Application Wizard</span></span>  
 <span data-ttu-id="06483-139">**若要启动向导，则使用以下步骤：**</span><span class="sxs-lookup"><span data-stu-id="06483-139">**To launch the wizard, use the following steps:**</span></span>  
  
1.  <span data-ttu-id="06483-140">连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的实例（无论是在内部部署中还是在 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]中）。</span><span class="sxs-lookup"><span data-stu-id="06483-140">Connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], whether on-premise or in [!INCLUDE[ssSDS](../../includes/sssds-md.md)].</span></span>  
  
2.  <span data-ttu-id="06483-141">在“对象资源管理器”  中，右键单击“数据库”  ，然后选择“导入数据层应用程序”  菜单项以启动向导。</span><span class="sxs-lookup"><span data-stu-id="06483-141">In **Object Explorer**, right-click on **Databases**, and then select the **Import Data-tier Application** menu item to launch the wizard.</span></span>  
  
3.  <span data-ttu-id="06483-142">完成向导对话框：</span><span class="sxs-lookup"><span data-stu-id="06483-142">Complete the wizard dialogs:</span></span>  
  
    -   [<span data-ttu-id="06483-143">“简介”页</span><span class="sxs-lookup"><span data-stu-id="06483-143">Introduction Page</span></span>](#Introduction)  
  
    -   [<span data-ttu-id="06483-144">“导入设置”页</span><span class="sxs-lookup"><span data-stu-id="06483-144">Import Settings Page</span></span>](#Import_settings)  
  
    -   [<span data-ttu-id="06483-145">“数据库设置”页</span><span class="sxs-lookup"><span data-stu-id="06483-145">Database Settings Page</span></span>](#Database_settings)  
  
    -   [<span data-ttu-id="06483-146">摘要页</span><span class="sxs-lookup"><span data-stu-id="06483-146">Summary Page</span></span>](#Summary)  
  
    -   [<span data-ttu-id="06483-147">“进度”页</span><span class="sxs-lookup"><span data-stu-id="06483-147">Progress Page</span></span>](#Progress)  
  
    -   [<span data-ttu-id="06483-148">“结果”页</span><span class="sxs-lookup"><span data-stu-id="06483-148">Results Page</span></span>](#Results)  
  
###  <a name="introduction-page"></a><a name="Introduction"></a> <span data-ttu-id="06483-149">“简介”页</span><span class="sxs-lookup"><span data-stu-id="06483-149">Introduction Page</span></span>  
 <span data-ttu-id="06483-150">此页介绍“数据层应用程序导入向导”的各个步骤。</span><span class="sxs-lookup"><span data-stu-id="06483-150">This page describes the steps for the Data-tier Application Import Wizard.</span></span>  
  
 <span data-ttu-id="06483-151">**选项**</span><span class="sxs-lookup"><span data-stu-id="06483-151">**Options**</span></span>  
  
-   <span data-ttu-id="06483-152">**不再显示此页。**</span><span class="sxs-lookup"><span data-stu-id="06483-152">**Do not show this page again.**</span></span> <span data-ttu-id="06483-153">- 选中此复选框可以停止在将来显示“简介”页。</span><span class="sxs-lookup"><span data-stu-id="06483-153">- Click the check box to stop the Introduction page from being displayed in the future.</span></span>  
  
-   <span data-ttu-id="06483-154">**下一步** - 进入“导入设置”页  。</span><span class="sxs-lookup"><span data-stu-id="06483-154">**Next** - Proceeds to the **Import Settings** page.</span></span>  
  
-   <span data-ttu-id="06483-155">**取消** - 取消操作并关闭向导。</span><span class="sxs-lookup"><span data-stu-id="06483-155">**Cancel** - Cancels the operation and closes the wizard.</span></span>  
  
###  <a name="import-settings-page"></a><a name="Import_settings"></a> <span data-ttu-id="06483-156">“导入设置”页</span><span class="sxs-lookup"><span data-stu-id="06483-156">Import Settings Page</span></span>  
 <span data-ttu-id="06483-157">使用此页可以指定要导入的 .bacpac 文件的位置。</span><span class="sxs-lookup"><span data-stu-id="06483-157">Use this page to specify the location of the .bacpac file to import.</span></span>  
  
-   <span data-ttu-id="06483-158">**从本地磁盘导入** - 单击“浏览…”以导航本地计算机，或在提供的空间中指定路径  。</span><span class="sxs-lookup"><span data-stu-id="06483-158">**Import from local disk** - Click **Browse...** to navigate the local computer, or specify the path in the space provided.</span></span> <span data-ttu-id="06483-159">路径名必须包含文件名和 .bacpac 扩展名。</span><span class="sxs-lookup"><span data-stu-id="06483-159">The path name must include a file name and the .bacpac extension.</span></span>  
  
-   <span data-ttu-id="06483-160">**从 Azure 导入**-从 azure 容器导入 BACPAC 文件。</span><span class="sxs-lookup"><span data-stu-id="06483-160">**Import from Azure** - Imports a BACPAC file from an Azure container.</span></span> <span data-ttu-id="06483-161">若要验证此选项，则必须连接到 Azure 容器。</span><span class="sxs-lookup"><span data-stu-id="06483-161">You must connect to an Azure container in order to validate this option.</span></span> <span data-ttu-id="06483-162">请注意，此选项还要求您为临时文件指定一个本地目录。</span><span class="sxs-lookup"><span data-stu-id="06483-162">Note that this option also requires that you specify a local directory for the temporary file.</span></span> <span data-ttu-id="06483-163">将在指定位置创建临时文件，并且在操作完成后，临时文件将保留在该位置。</span><span class="sxs-lookup"><span data-stu-id="06483-163">The temporary file will be created at the specified location and will remain there after the operation completes.</span></span>  
  
     <span data-ttu-id="06483-164">在浏览 Azure 时，你将能够在单一帐户内的不同容器之间进行切换。</span><span class="sxs-lookup"><span data-stu-id="06483-164">When browsing Azure, you will be able to switch between containers within a single account.</span></span> <span data-ttu-id="06483-165">您必须指定一个单独的 .bacpac 文件以继续导入操作。</span><span class="sxs-lookup"><span data-stu-id="06483-165">You must specify a single .bacpac file to continue the import operation.</span></span> <span data-ttu-id="06483-166">请注意，您可以按 **“名称”**、 **“大小”** 或 **“修改日期”** 对列进行排序。</span><span class="sxs-lookup"><span data-stu-id="06483-166">Note that you can sort columns by **Name**, **Size**, or **Date Modified**.</span></span>  
  
     <span data-ttu-id="06483-167">若要继续，请指定要导入的 .bacpac 文件，然后单击 **“打开”** 。</span><span class="sxs-lookup"><span data-stu-id="06483-167">To continue, specify the .bacpac file to import, and then click **Open**.</span></span>  
  
###  <a name="database-settings-page"></a><a name="Database_settings"></a> <span data-ttu-id="06483-168">“数据库设置”页</span><span class="sxs-lookup"><span data-stu-id="06483-168">Database Settings Page</span></span>  
 <span data-ttu-id="06483-169">使用此页面可以指定将要创建的数据库的详细信息。</span><span class="sxs-lookup"><span data-stu-id="06483-169">Use this page to specify details for the database that will be created.</span></span>  
  
 <span data-ttu-id="06483-170">**对于 SQL Server 的本地实例：**</span><span class="sxs-lookup"><span data-stu-id="06483-170">**For a local instance of SQL Server:**</span></span>  
  
-   <span data-ttu-id="06483-171">**新数据库名称** - 提供导入的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="06483-171">**New database name** - Provide a name for the imported database.</span></span>  
  
-   <span data-ttu-id="06483-172">**数据文件路径** - 提供数据文件的本地目录。</span><span class="sxs-lookup"><span data-stu-id="06483-172">**Data file path** - Provide a local directory for data files.</span></span> <span data-ttu-id="06483-173">单击“浏览…”以导航本地计算机，或在提供的空间中指定路径  。</span><span class="sxs-lookup"><span data-stu-id="06483-173">Click **Browse...** to navigate the local computer, or specify the path in the space provided.</span></span>  
  
-   <span data-ttu-id="06483-174">**日志文件路径** - 提供日志文件的本地目录。</span><span class="sxs-lookup"><span data-stu-id="06483-174">**Log file path** - Provide a local directory for log files.</span></span> <span data-ttu-id="06483-175">单击“浏览…”以导航本地计算机，或在提供的空间中指定路径  。</span><span class="sxs-lookup"><span data-stu-id="06483-175">Click **Browse...** to navigate the local computer, or specify the path in the space provided.</span></span>  
  
 <span data-ttu-id="06483-176">若要继续，请单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="06483-176">To continue, click **Next**.</span></span>  
  
 <span data-ttu-id="06483-177">**对于 SQL 数据库：**</span><span class="sxs-lookup"><span data-stu-id="06483-177">**For a SQL Database:**</span></span>  
  
-   <span data-ttu-id="06483-178">**新数据库名称**-提供导入的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="06483-178">**New database name** - Provide a name for the imported database.</span></span>  
  
-   <span data-ttu-id="06483-179">\*\*版本的 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] \*\*-指定 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Business 或 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Web。</span><span class="sxs-lookup"><span data-stu-id="06483-179">**Edition of [!INCLUDE[ssSDS](../../includes/sssds-md.md)]** - Specify [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Business or [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Web.</span></span> <span data-ttu-id="06483-180">有关 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]版本的详细信息，请参阅此 [SQL Database](https://www.windowsazure.com/home/tour/database/) 网站。</span><span class="sxs-lookup"><span data-stu-id="06483-180">For more information about editions of [!INCLUDE[ssSDS](../../includes/sssds-md.md)], see this [SQL Database](https://www.windowsazure.com/home/tour/database/) web site.</span></span>  
  
-   <span data-ttu-id="06483-181">\*\*最大数据库大小 (GB) \*\* -使用下拉菜单指定数据库的最大大小。</span><span class="sxs-lookup"><span data-stu-id="06483-181">**Maximum database size (GB)** - Use the drop-down menu to specify the maximum size for your database.</span></span>  
  
 <span data-ttu-id="06483-182">若要继续，请单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="06483-182">To continue, click **Next**.</span></span>  
  
### <a name="validation-page"></a><span data-ttu-id="06483-183">“验证”页</span><span class="sxs-lookup"><span data-stu-id="06483-183">Validation Page</span></span>  
 <span data-ttu-id="06483-184">使用此页可查看阻止操作的任何问题。</span><span class="sxs-lookup"><span data-stu-id="06483-184">Use this page to review any issues that block the operation.</span></span> <span data-ttu-id="06483-185">若要继续，请解决阻止问题，然后单击“重新运行验证”\*\*\*\* 确保验证成功。</span><span class="sxs-lookup"><span data-stu-id="06483-185">To continue, resolve blocking issues and then click **Re-run Validation** to ensure that validation is successful.</span></span>  
  
 <span data-ttu-id="06483-186">若要继续，请单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="06483-186">To continue, click **Next**.</span></span>  
  
###  <a name="summary-page"></a><a name="Summary"></a> <span data-ttu-id="06483-187">摘要页</span><span class="sxs-lookup"><span data-stu-id="06483-187">Summary Page</span></span>  
 <span data-ttu-id="06483-188">使用此页可查看操作的指定的源和目标设置。</span><span class="sxs-lookup"><span data-stu-id="06483-188">Use this page to review the specified source and target settings for the operation.</span></span> <span data-ttu-id="06483-189">若要使用指定设置完成导入操作，请单击 **“完成”**。</span><span class="sxs-lookup"><span data-stu-id="06483-189">To complete the import operation using the specified settings, click **Finish**.</span></span> <span data-ttu-id="06483-190">若要取消导入操作并退出向导，请单击“取消” \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="06483-190">To cancel the import operation and exit the wizard, click **Cancel**.</span></span>  
  
###  <a name="progress-page"></a><a name="Progress"></a> <span data-ttu-id="06483-191">“进度”页</span><span class="sxs-lookup"><span data-stu-id="06483-191">Progress Page</span></span>  
 <span data-ttu-id="06483-192">此页将显示一个指示操作状态的进度栏。</span><span class="sxs-lookup"><span data-stu-id="06483-192">This page displays a progress bar that indicates the status of the operation.</span></span> <span data-ttu-id="06483-193">若要查看详细状态，请单击 **“查看详细信息”** 选项。</span><span class="sxs-lookup"><span data-stu-id="06483-193">To view detailed status, click the **View details** option.</span></span>  
  
 <span data-ttu-id="06483-194">若要继续，请单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="06483-194">To continue, click **Next**.</span></span>  
  
###  <a name="results-page"></a><a name="Results"></a><span data-ttu-id="06483-195">结果页</span><span class="sxs-lookup"><span data-stu-id="06483-195">Results Page</span></span>  
 <span data-ttu-id="06483-196">此页将报告导入和创建数据库操作是成功还是失败，并显示各个操作的成功或失败。</span><span class="sxs-lookup"><span data-stu-id="06483-196">This page reports the success or failure of the import and create database operations, showing the success or failure of each action.</span></span> <span data-ttu-id="06483-197">遇到了错误的任何操作都将在 **“结果”** 列中具有一个链接。</span><span class="sxs-lookup"><span data-stu-id="06483-197">Any action that encountered an error will have a link in the **Result** column.</span></span> <span data-ttu-id="06483-198">单击该链接可以查看针对该操作的错误报告。</span><span class="sxs-lookup"><span data-stu-id="06483-198">Click the link to view a report of the error for that action.</span></span>  
  
 <span data-ttu-id="06483-199">单击“**关闭**”以关闭向导。</span><span class="sxs-lookup"><span data-stu-id="06483-199">Click **Close** to close the wizard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06483-200">另请参阅</span><span class="sxs-lookup"><span data-stu-id="06483-200">See Also</span></span>  
 <span data-ttu-id="06483-201">[数据层应用程序](data-tier-applications.md) </span><span class="sxs-lookup"><span data-stu-id="06483-201">[Data-tier Applications](data-tier-applications.md) </span></span>  
 [<span data-ttu-id="06483-202">导出数据层应用程序</span><span class="sxs-lookup"><span data-stu-id="06483-202">Export a Data-tier Application</span></span>](export-a-data-tier-application.md)  
  
