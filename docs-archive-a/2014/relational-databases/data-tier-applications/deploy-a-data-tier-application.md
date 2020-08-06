---
title: 部署数据层应用程序 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.deploydacwizard.updateconfiguration.f1
- sql12.swb.deploydacwizard.selectdac.f1
- sql12.swb.deploydacwizard.deploydac.f1
- sql12.swb.deploydacwizard.introduction.f1
- sql12.swb.deploydacwizard.summary.f1
helpviewer_keywords:
- Deploy data-tier application
- deploy DAC
- data-tier application [SQL Server], deploy
- How to [DAC], deploy
- wizard [DAC], deploy
ms.assetid: c117af35-aa53-44a5-8034-fa8715dc735f
author: stevestein
ms.author: sstein
ms.openlocfilehash: fd4a09eed946863064728fd8c62230121ad3d403
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692958"
---
# <a name="deploy-a-data-tier-application"></a><span data-ttu-id="eb13d-102">部署数据层应用程序</span><span class="sxs-lookup"><span data-stu-id="eb13d-102">Deploy a Data-tier Application</span></span>
  <span data-ttu-id="eb13d-103">您可使用向导或 PowerShell 脚本将数据层应用程序 (DAC) 从 DAC 包部署到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 或 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 的现有实例。</span><span class="sxs-lookup"><span data-stu-id="eb13d-103">You can deploy a data-tier application (DAC) from a DAC package to an existing instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] or [!INCLUDE[ssSDS](../../includes/sssds-md.md)] by using a wizard or a PowerShell script.</span></span> <span data-ttu-id="eb13d-104">该部署过程通过在 **msdb** 系统数据库（在**中为** master [!INCLUDE[ssSDS](../../includes/sssds-md.md)]）中存储 DAC 定义来注册一个 DAC 实例，创建一个数据库，然后使用在该 DAC 中定义的所有数据库对象来填充该数据库。</span><span class="sxs-lookup"><span data-stu-id="eb13d-104">The deployment process registers a DAC instance by storing the DAC definition in the **msdb** system database (**master** in [!INCLUDE[ssSDS](../../includes/sssds-md.md)]), creates a database, and then populates the database with all the database objects defined in the DAC.</span></span>  
  
-   <span data-ttu-id="eb13d-105">**开始之前：**  [SQL Server 实用工具](#SQLUtility)、 [数据库选项和设置](#DBOptSettings)、 [限制和局限](#LimitationsRestrictions)、 [先决条件](#Prerequisites)、 [安全性](#Security)、 [权限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="eb13d-105">**Before you begin:**  [SQL Server Utility](#SQLUtility), [Database Options and Settings](#DBOptSettings), [Limitations and Restrictions](#LimitationsRestrictions), [Prerequisites](#Prerequisites), [Security](#Security), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="eb13d-106">**若要部署 DAC，请使用：**  [部署数据层应用程序向导](#UsingDeployDACWizard)、 [PowerShell](#DeployDACPowerShell)</span><span class="sxs-lookup"><span data-stu-id="eb13d-106">**To deploy a DAC, using:**  [The Deploy Data-tier Application Wizard](#UsingDeployDACWizard), [PowerShell](#DeployDACPowerShell)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeBegin"></a> <span data-ttu-id="eb13d-107">开始之前</span><span class="sxs-lookup"><span data-stu-id="eb13d-107">Before You Begin</span></span>  
 <span data-ttu-id="eb13d-108">同一 DAC 包可以多次部署到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的单个实例上，但必须一次一个执行这些部署。</span><span class="sxs-lookup"><span data-stu-id="eb13d-108">The same DAC package can be deployed to a single instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] multiple times, however the deployments must be run one at a time.</span></span> <span data-ttu-id="eb13d-109">为每个部署指定的 DAC 实例名称在 [!INCLUDE[ssDE](../../includes/ssde-md.md)]实例中必须唯一。</span><span class="sxs-lookup"><span data-stu-id="eb13d-109">The DAC instance name specified for each deployment must be unique within the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
###  <a name="sql-server-utility"></a><a name="SQLUtility"></a><span data-ttu-id="eb13d-110">SQL Server 实用工具</span><span class="sxs-lookup"><span data-stu-id="eb13d-110">SQL Server Utility</span></span>  
 <span data-ttu-id="eb13d-111">如果您将 DAC 部署到数据库引擎的托管实例，在下次将实用工具收集组从该实例发送到实用工具控制点时，部署的 DAC 将合并到 SQL Server 实用工具中。</span><span class="sxs-lookup"><span data-stu-id="eb13d-111">If you deploy a DAC to a managed instance of the Database Engine, the deployed DAC is incorporated into the SQL Server Utility the next time the utility collection set is sent from the instance to the utility control point.</span></span> <span data-ttu-id="eb13d-112">然后，该 DAC 将出现在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 实用工具资源管理器的“已部署的数据层应用程序”节点中，并且将在“已部署的数据层应用程序”的详细信息页面中报告  。</span><span class="sxs-lookup"><span data-stu-id="eb13d-112">The DAC will then be present in the **Deployed Data-tier Applications** node of the [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] **Utility Explorer** and reported in the **Deployed Data-tier Applications** details page.</span></span>  
  
###  <a name="database-options-and-settings"></a><a name="DBOptSettings"></a><span data-ttu-id="eb13d-113">数据库选项和设置</span><span class="sxs-lookup"><span data-stu-id="eb13d-113">Database Options and Settings</span></span>  
 <span data-ttu-id="eb13d-114">默认情况下，在部署过程中创建的数据库将具有来自 CREATE DATABASE 语句的几乎所有默认设置，只有以下方面除外：</span><span class="sxs-lookup"><span data-stu-id="eb13d-114">By default, the database created during the deployment will have all of the default settings from the CREATE DATABASE statement, except:</span></span>  
  
-   <span data-ttu-id="eb13d-115">数据库排序规则和兼容级别设置为在 DAC 包中定义的值。</span><span class="sxs-lookup"><span data-stu-id="eb13d-115">The database collation and compatibility level are set to the values defined in the DAC package.</span></span> <span data-ttu-id="eb13d-116">从 SQL Server 开发工具的数据库项目生成的 DAC 包使用在数据库项目中设置的值。</span><span class="sxs-lookup"><span data-stu-id="eb13d-116">A DAC package built from a database project in the SQL Server Developer Tools uses the values set in the database project.</span></span> <span data-ttu-id="eb13d-117">从现有数据库中提取的包将使用来自原始数据库的值。</span><span class="sxs-lookup"><span data-stu-id="eb13d-117">A package extracted from an existing database uses the values from the original database.</span></span>  
  
-   <span data-ttu-id="eb13d-118">您可以在 **“更新配置”** 页中调整某些数据库设置，例如数据库名称和文件路径。</span><span class="sxs-lookup"><span data-stu-id="eb13d-118">You can adjust some of the database settings, such as database name and file paths, in the **Update Configuration** page.</span></span> <span data-ttu-id="eb13d-119">在部署到 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]时，不能设置文件路径。</span><span class="sxs-lookup"><span data-stu-id="eb13d-119">You cannot set the file paths when deploying to [!INCLUDE[ssSDS](../../includes/sssds-md.md)].</span></span>  
  
 <span data-ttu-id="eb13d-120">某些数据库选项（例如 TRUSTWORTHY、DB_CHAINING 和 HONOR_BROKER_PRIORITY）不能作为部署过程的一部分进行调整。</span><span class="sxs-lookup"><span data-stu-id="eb13d-120">Some database options, such as TRUSTWORTHY, DB_CHAINING, and HONOR_BROKER_PRIORITY, cannot be adjusted as part of the deployment process.</span></span> <span data-ttu-id="eb13d-121">物理属性（例如文件组的数目或者文件的数目和大小）不能作为部署过程的一部分进行更改。</span><span class="sxs-lookup"><span data-stu-id="eb13d-121">Physical properties, such as the number of filegroups, or the numbers and sizes of files cannot be altered as part of the deployment process.</span></span> <span data-ttu-id="eb13d-122">在部署完成后，可以使用 ALTER DATABASE 语句、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell 对数据库进行定制。</span><span class="sxs-lookup"><span data-stu-id="eb13d-122">After the deployment completes, you can use the ALTER DATABASE statement, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell to tailor the database.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="eb13d-123">限制和局限</span><span class="sxs-lookup"><span data-stu-id="eb13d-123">Limitations and Restrictions</span></span>  
 <span data-ttu-id="eb13d-124">可以将 DAC 部署到 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]或运行 [!INCLUDE[ssDE](../../includes/ssde-md.md)] Service Pack 4 (SP4) 或更高版本的 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="eb13d-124">A DAC can be deployed to [!INCLUDE[ssSDS](../../includes/sssds-md.md)], or an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] running [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) or later.</span></span> <span data-ttu-id="eb13d-125">如果使用更高版本创建 DAC，则 DAC 可能包含 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]不支持的对象。</span><span class="sxs-lookup"><span data-stu-id="eb13d-125">If you create a DAC using a later version, the DAC may contain objects not supported by [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="eb13d-126">您不能将这些 DAC 部署到 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]实例。</span><span class="sxs-lookup"><span data-stu-id="eb13d-126">You cannot deploy those DACs to instances of [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="eb13d-127">先决条件</span><span class="sxs-lookup"><span data-stu-id="eb13d-127">Prerequisites</span></span>  
 <span data-ttu-id="eb13d-128">建议您不要从未知或不可信源部署 DAC 包。</span><span class="sxs-lookup"><span data-stu-id="eb13d-128">We recommend that you do not deploy a DAC package from unknown or untrusted sources.</span></span> <span data-ttu-id="eb13d-129">此类包可能包含恶意代码，这些代码可能会执行非预期的 Transact-SQL 代码，或者通过修改架构导致错误。</span><span class="sxs-lookup"><span data-stu-id="eb13d-129">Such packages could contain malicious code that might execute unintended Transact-SQL code or cause errors by modifying the schema.</span></span> <span data-ttu-id="eb13d-130">在使用来自未知或不可信源的包之前，请解压缩该 DAC 并检查代码，例如存储过程或者其他用户定义的代码。</span><span class="sxs-lookup"><span data-stu-id="eb13d-130">Before you use a package from an unknown or untrusted source, unpack the DAC and examine the code, such as stored procedures or other user-defined code.</span></span> <span data-ttu-id="eb13d-131">有关如何执行这些检查的详细信息，请参阅 [Validate a DAC Package](validate-a-dac-package.md)。</span><span class="sxs-lookup"><span data-stu-id="eb13d-131">For more information about how to perform these checks, see [Validate a DAC Package](validate-a-dac-package.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="eb13d-132">Security</span><span class="sxs-lookup"><span data-stu-id="eb13d-132">Security</span></span>  
 <span data-ttu-id="eb13d-133">为了提高安全性，SQL Server 身份验证登录名存储在 DAC 包中且没有密码。</span><span class="sxs-lookup"><span data-stu-id="eb13d-133">To improve security, SQL Server Authentication logins are stored in a DAC package without a password.</span></span> <span data-ttu-id="eb13d-134">在部署或升级该包时，登录名将作为含有生成的密码的已禁用登录名创建。</span><span class="sxs-lookup"><span data-stu-id="eb13d-134">When the package is deployed or upgraded, the login is created as a disabled login with a generated password.</span></span> <span data-ttu-id="eb13d-135">若要启用这些登录名，请使用具有 ALTER ANY LOGIN 权限的登录名登录，并且使用 ALTER LOGIN 来启用该登录名并且分配可以传达给用户的新密码。</span><span class="sxs-lookup"><span data-stu-id="eb13d-135">To enable the logins, log in using a login that has ALTER ANY LOGIN permission and use ALTER LOGIN to enable the login and assign a new password that can be communicated to the user.</span></span> <span data-ttu-id="eb13d-136">对于 Windows 身份验证登录名则无需执行此操作，因为其密码不是由 SQL Server 管理的。</span><span class="sxs-lookup"><span data-stu-id="eb13d-136">This is not needed for Windows Authentication logins because their passwords are not managed by SQL Server.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="eb13d-137">权限</span><span class="sxs-lookup"><span data-stu-id="eb13d-137">Permissions</span></span>  
 <span data-ttu-id="eb13d-138">DAC 只能由 **sysadmin** 或 **serveradmin** 固定服务器角色的成员部署，或者由属于 **dbcreator** 固定服务器角色并具有 ALTER ANY LOGIN 权限的登录名部署。</span><span class="sxs-lookup"><span data-stu-id="eb13d-138">A DAC can only be deployed by members of the **sysadmin** or **serveradmin** fixed server roles, or by logins that are in the **dbcreator** fixed server role and have ALTER ANY LOGIN permissions.</span></span> <span data-ttu-id="eb13d-139">名为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sa **的内置** 系统管理员帐户也可以部署 DAC。</span><span class="sxs-lookup"><span data-stu-id="eb13d-139">The built-in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator account named **sa** can also deploy a DAC.</span></span> <span data-ttu-id="eb13d-140">将具有登录名的 DAC 部署到 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 要求 loginmanager 或 serveradmin 角色的成员身份。</span><span class="sxs-lookup"><span data-stu-id="eb13d-140">Deploying a DAC with logins to [!INCLUDE[ssSDS](../../includes/sssds-md.md)] requires membership in the loginmanager or serveradmin roles.</span></span> <span data-ttu-id="eb13d-141">将不带登录名的 DAC 部署到 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 要求 dbmanager 或 serveradmin 角色的成员身份。</span><span class="sxs-lookup"><span data-stu-id="eb13d-141">Deploying a DAC without logins to [!INCLUDE[ssSDS](../../includes/sssds-md.md)] requires membership in the dbmanager or serveradmin roles.</span></span>  
  
##  <a name="using-the-deploy-data-tier-application-wizard"></a><a name="UsingDeployDACWizard"></a><span data-ttu-id="eb13d-142">使用 "部署数据层应用程序向导"</span><span class="sxs-lookup"><span data-stu-id="eb13d-142">Using the Deploy Data-tier Application Wizard</span></span>  
 <span data-ttu-id="eb13d-143">**使用向导部署 DAC**</span><span class="sxs-lookup"><span data-stu-id="eb13d-143">**To Deploy a DAC Using a Wizard**</span></span>  
  
1.  <span data-ttu-id="eb13d-144">在 **“对象资源管理器”** 中，展开要将 DAC 部署到的实例的节点。</span><span class="sxs-lookup"><span data-stu-id="eb13d-144">In **Object Explorer**, expand the node for the instance to which you want to deploy the DAC.</span></span>  
  
2.  <span data-ttu-id="eb13d-145">右键单击 "**数据库**" 节点，然后选择 "**部署数据层应用程序 ...** "</span><span class="sxs-lookup"><span data-stu-id="eb13d-145">Right-click the **Databases** node, then select **Deploy Data-tier Application...**</span></span>  
  
3.  <span data-ttu-id="eb13d-146">完成向导对话框：</span><span class="sxs-lookup"><span data-stu-id="eb13d-146">Complete the wizard dialogs:</span></span>  
  
    -   [<span data-ttu-id="eb13d-147">“简介”页</span><span class="sxs-lookup"><span data-stu-id="eb13d-147">Introduction Page</span></span>](#Introduction)  
  
    -   [<span data-ttu-id="eb13d-148">“选择 DAC 包”页</span><span class="sxs-lookup"><span data-stu-id="eb13d-148">Select DAC Package Page</span></span>](#Select_dac_package)  
  
    -   [<span data-ttu-id="eb13d-149">"查看策略" 页</span><span class="sxs-lookup"><span data-stu-id="eb13d-149">Review Policy Page</span></span>](#Review_policy)  
  
    -   [<span data-ttu-id="eb13d-150">“更新配置”页</span><span class="sxs-lookup"><span data-stu-id="eb13d-150">Update Configuration Page</span></span>](#Update_configuration)  
  
    -   [<span data-ttu-id="eb13d-151">摘要页</span><span class="sxs-lookup"><span data-stu-id="eb13d-151">Summary Page</span></span>](#Summary)  
  
    -   [<span data-ttu-id="eb13d-152">“部署”页</span><span class="sxs-lookup"><span data-stu-id="eb13d-152">Deploy Page</span></span>](#Deploy)  
  
##  <a name="introduction-page"></a><a name="Introduction"></a> <span data-ttu-id="eb13d-153">“简介”页</span><span class="sxs-lookup"><span data-stu-id="eb13d-153">Introduction Page</span></span>  
 <span data-ttu-id="eb13d-154">此页描述数据层应用程序的部署步骤。</span><span class="sxs-lookup"><span data-stu-id="eb13d-154">This page describes the steps for deploying a data-tier application.</span></span>  
  
 <span data-ttu-id="eb13d-155">**不再显示此页。**</span><span class="sxs-lookup"><span data-stu-id="eb13d-155">**Do not show this page again.**</span></span> <span data-ttu-id="eb13d-156">- 选中该复选框可以停止在将来显示此页。</span><span class="sxs-lookup"><span data-stu-id="eb13d-156">- Click the check box to stop the page from being displayed in the future.</span></span>  
  
 <span data-ttu-id="eb13d-157">“下一步 >”\*\*\*\* - 继续到“选择 DAC 包”\*\*\*\* 页。</span><span class="sxs-lookup"><span data-stu-id="eb13d-157">**Next >** - Proceeds to the **Select DAC Package** page.</span></span>  
  
 <span data-ttu-id="eb13d-158">“取消”\*\*\*\*- 终止向导且不部署 DAC。</span><span class="sxs-lookup"><span data-stu-id="eb13d-158">**Cancel** - Terminates the wizard without deploying a DAC.</span></span>  
  
##  <a name="select-dac-package-page"></a><a name="Select_dac_package"></a><span data-ttu-id="eb13d-159">"选择 DAC 包" 页</span><span class="sxs-lookup"><span data-stu-id="eb13d-159">Select DAC Package Page</span></span>  
 <span data-ttu-id="eb13d-160">使用此页可以指定包含要部署的数据层应用程序的 DAC 包。</span><span class="sxs-lookup"><span data-stu-id="eb13d-160">Use this page to specify the DAC package that contains the data-tier application to be deployed.</span></span> <span data-ttu-id="eb13d-161">该页可为三种状态。</span><span class="sxs-lookup"><span data-stu-id="eb13d-161">The page transitions through three states.</span></span>  
  
### <a name="select-the-dac-package"></a><span data-ttu-id="eb13d-162">选择 DAC 包</span><span class="sxs-lookup"><span data-stu-id="eb13d-162">Select the DAC Package</span></span>  
 <span data-ttu-id="eb13d-163">使用该页的初始状态可以选择要部署的 DAC 包。</span><span class="sxs-lookup"><span data-stu-id="eb13d-163">Use the initial state of the page to choose the DAC package to deploy.</span></span> <span data-ttu-id="eb13d-164">该 DAC 包必须是有效的 DAC 包文件，并且必须具有 .dacpac 扩展名。</span><span class="sxs-lookup"><span data-stu-id="eb13d-164">The DAC package must be a valid DAC package file and must have a .dacpac extension.</span></span>  
  
 <span data-ttu-id="eb13d-165">“DAC 包”\*\*\*\*- 指定包含要部署的数据层应用程序的 DAC 包的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="eb13d-165">**DAC Package** - Specify the path and file name of the DAC package that contains the data-tier application to be deployed.</span></span> <span data-ttu-id="eb13d-166">您可以选择框右侧的 **“浏览”** 按钮以便浏览到 DAC 包的位置。</span><span class="sxs-lookup"><span data-stu-id="eb13d-166">You can select the **Browse** button at the right of the box to browse to the location of the DAC package.</span></span>  
  
 <span data-ttu-id="eb13d-167">“应用程序名称”\*\*\*\* - 一个只读框，它显示创作 DAC 或者从某一数据库中提取 DAC 时分配的 DAC 名称。</span><span class="sxs-lookup"><span data-stu-id="eb13d-167">**Application Name** - A read-only box that displays the DAC name assigned when the DAC was authored or extracted from a database.</span></span>  
  
 <span data-ttu-id="eb13d-168">“版本”\*\*\*\*- 一个只读框，它显示创作 DAC 或者从某一数据库中提取 DAC 时分配的版本。</span><span class="sxs-lookup"><span data-stu-id="eb13d-168">**Version** - A read-only box that displays the version assigned when the DAC was authored or extracted from a database.</span></span>  
  
 <span data-ttu-id="eb13d-169">“说明”\*\*\*\*- 一个只读框，它显示创作 DAC 或者从某一数据库中提取 DAC 时编写的版本。</span><span class="sxs-lookup"><span data-stu-id="eb13d-169">**Description** - A read-only box that displays the description written when the DAC was authored or extracted from a database.</span></span>  
  
 <span data-ttu-id="eb13d-170">" \*\* \< 上一步**"-返回到 "**简介\*\*" 页。</span><span class="sxs-lookup"><span data-stu-id="eb13d-170">**\< Previous** - Returns to the **Introduction** page.</span></span>  
  
 <span data-ttu-id="eb13d-171">“下一步 >”\*\*\*\*- 显示进度栏，因为向导已确认所选文件为有效的 DAC 包。</span><span class="sxs-lookup"><span data-stu-id="eb13d-171">**Next >** - Displays a progress bar as the wizard confirms that the selected file is a valid DAC package.</span></span>  
  
 <span data-ttu-id="eb13d-172">“取消”\*\*\*\*- 终止向导且不部署 DAC。</span><span class="sxs-lookup"><span data-stu-id="eb13d-172">**Cancel** - Terminates the wizard without deploying the DAC.</span></span>  
  
### <a name="validating-the-dac-package"></a><span data-ttu-id="eb13d-173">验证 DAC 包</span><span class="sxs-lookup"><span data-stu-id="eb13d-173">Validating the DAC Package</span></span>  
 <span data-ttu-id="eb13d-174">在向导确认所选文件是有效的 DAC 包时显示一个进度栏。</span><span class="sxs-lookup"><span data-stu-id="eb13d-174">Displays a progress bar as the wizard confirms that the selected file is a valid DAC package.</span></span> <span data-ttu-id="eb13d-175">如果对该 DAC 包进行了验证，则向导将继续到 **“选择包”** 页的最终形式，从中可以查看验证的结果。</span><span class="sxs-lookup"><span data-stu-id="eb13d-175">If the DAC package is validated, the wizard proceeds to the final version of the **Select Package** page where you can review the results of the validation.</span></span> <span data-ttu-id="eb13d-176">如果该文件不是有效的 DAC 包，则向导会保持在 **“选择 DAC 包”** 页上。</span><span class="sxs-lookup"><span data-stu-id="eb13d-176">If the file is not a valid DAC package, the wizard remains on the **Select DAC Package**.</span></span> <span data-ttu-id="eb13d-177">或者选择另一个有效的 DAC 包，或者取消该向导并且生成一个新的 DAC 包。</span><span class="sxs-lookup"><span data-stu-id="eb13d-177">Either select another valid DAC package or cancel the wizard and generate a new DAC package.</span></span>  
  
 <span data-ttu-id="eb13d-178">“正在验证 DAC 的内容”\*\*\*\*- 报告验证过程的当前状态的进度栏。</span><span class="sxs-lookup"><span data-stu-id="eb13d-178">**Validating the contents of the DAC** - The progress bar that reports the current status of the validation process.</span></span>  
  
 <span data-ttu-id="eb13d-179">" \*\* \< 上一步**"-返回到 "**选择包\*\*" 页的初始状态。</span><span class="sxs-lookup"><span data-stu-id="eb13d-179">**\< Previous** - Returns to the initial state of the **Select Package** page.</span></span>  
  
 <span data-ttu-id="eb13d-180">“下一步 >”\*\*\*\*- 继续到“选择包”\*\*\*\* 页的最终版本。</span><span class="sxs-lookup"><span data-stu-id="eb13d-180">**Next >** - Proceeds to the final version of the **Select Package** page.</span></span>  
  
 <span data-ttu-id="eb13d-181">“取消”\*\*\*\*- 终止向导且不部署 DAC。</span><span class="sxs-lookup"><span data-stu-id="eb13d-181">**Cancel** - Terminates the wizard without deploying the DAC.</span></span>  
  
##  <a name="review-policy-page"></a><a name="Review_policy"></a> <span data-ttu-id="eb13d-182">“查看策略”页</span><span class="sxs-lookup"><span data-stu-id="eb13d-182">Review Policy Page</span></span>  
 <span data-ttu-id="eb13d-183">使用此页可查看评估 DAC 服务器选择策略的结果（如果该 DAC 具有策略）。</span><span class="sxs-lookup"><span data-stu-id="eb13d-183">Use this page to review the results of evaluating the DAC server selection policy, if the DAC has a policy.</span></span> <span data-ttu-id="eb13d-184">该 DAC 服务器选择策略是可选的，并在 Visual Studio 中创建它时分配给该 DAC。</span><span class="sxs-lookup"><span data-stu-id="eb13d-184">The DAC server selection policy is optional, and is assigned to the DAC when it is created in Visual Studio.</span></span> <span data-ttu-id="eb13d-185">该策略使用该服务器选择策略方面指定 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的实例为承载该 DAC 而必须满足的条件。</span><span class="sxs-lookup"><span data-stu-id="eb13d-185">The policy uses the server selection policy facets to specify conditions an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] should meet to host the DAC.</span></span>  
  
 <span data-ttu-id="eb13d-186">“策略条件的评估结果”\*\*\*\*- 一个只读报告，显示 DAC 部署策略的条件是否成功。</span><span class="sxs-lookup"><span data-stu-id="eb13d-186">**Evaluation results of policy conditions** - A read-only report showing whether the conditions of the DAC deployment policy succeeded.</span></span> <span data-ttu-id="eb13d-187">将在单独的行上报告对每个条件进行评估的结果。</span><span class="sxs-lookup"><span data-stu-id="eb13d-187">The results of evaluating each condition are reported on a separate line.</span></span>  
  
 <span data-ttu-id="eb13d-188">在将 DAC 部署到 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]时以下服务器选择策略的计算结果始终为 false：操作系统版本、语言、启用的命名管道、平台和启用的 tcp。</span><span class="sxs-lookup"><span data-stu-id="eb13d-188">The following server selection policies always evaluate to false when deploying a DAC to [!INCLUDE[ssSDS](../../includes/sssds-md.md)]: operating system version, language, named pipes enabled, platform, and tcp enabled.</span></span>  
  
 <span data-ttu-id="eb13d-189">“忽略违反策略情况”\*\*\*\*- 使用此复选框可以在未能满足一个或多个策略条件的情况下继续进行部署。</span><span class="sxs-lookup"><span data-stu-id="eb13d-189">**Ignore policy violations** - Use this check box to proceed with the deployment if one or more of the policy conditions failed.</span></span> <span data-ttu-id="eb13d-190">只有在您确保未满足的所有条件都不会阻碍 DAC 操作成功条件的情况下，才选择此选项。</span><span class="sxs-lookup"><span data-stu-id="eb13d-190">Only select this option if you are sure that all of the conditions which failed will not prevent the successful operation of the DAC.</span></span>  
  
 <span data-ttu-id="eb13d-191">" \*\* \< 上一步**"-返回到 "**选择包\*\*" 页。</span><span class="sxs-lookup"><span data-stu-id="eb13d-191">**\< Previous** - Returns to the **Select Package** page.</span></span>  
  
 <span data-ttu-id="eb13d-192">“下一步 >”\*\*\*\*- 继续到“更新配置”\*\*\*\* 页。</span><span class="sxs-lookup"><span data-stu-id="eb13d-192">**Next >** - Proceeds to the **Update Configureation** page.</span></span>  
  
 <span data-ttu-id="eb13d-193">“取消”\*\*\*\*- 终止向导且不部署 DAC。</span><span class="sxs-lookup"><span data-stu-id="eb13d-193">**Cancel** - Terminates the wizard without deploying the DAC.</span></span>  
  
##  <a name="update-configuration-page"></a><a name="Update_configuration"></a><span data-ttu-id="eb13d-194">"更新配置" 页</span><span class="sxs-lookup"><span data-stu-id="eb13d-194">Update Configuration Page</span></span>  
 <span data-ttu-id="eb13d-195">使用此页可指定已部署的 DAC 实例的名称以及部署创建的数据库的名称，并且可设置数据库选项。</span><span class="sxs-lookup"><span data-stu-id="eb13d-195">Use this page to specify the names of the deployed DAC instance and the database created by the deployment, and to set database options.</span></span>  
  
 <span data-ttu-id="eb13d-196">“数据库名称”\*\*\*\*：- 指定要由部署创建的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="eb13d-196">**Database Name:** - Specify the name of the database to be created by the deployment.</span></span> <span data-ttu-id="eb13d-197">默认值是从其提取该 DAC 的源数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="eb13d-197">The default is the name of the source database the DAC was extracted from.</span></span> <span data-ttu-id="eb13d-198">该名称在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的实例内必须唯一，并且必须符合 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 标识符的规则。</span><span class="sxs-lookup"><span data-stu-id="eb13d-198">The name must be unique within the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and comply with the rules for [!INCLUDE[ssDE](../../includes/ssde-md.md)] identifiers.</span></span>  
  
 <span data-ttu-id="eb13d-199">如果您更改数据库名称，则数据文件和日志文件的名称也将更改以匹配这个新值。</span><span class="sxs-lookup"><span data-stu-id="eb13d-199">If you change the database name, the names of the data file and log files will change to match the new value.</span></span>  
  
 <span data-ttu-id="eb13d-200">该数据库名称还用作 DAC 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="eb13d-200">The database name is also used as the name of the DAC instance.</span></span> <span data-ttu-id="eb13d-201">该实例名称显示在“对象资源管理器”\*\*\*\* 中“数据层应用程序”\*\*\*\* 节点下的 DAC 的节点上，或者显示在“实用工具资源管理器”\*\*\*\* 中“已部署的数据层应用程序”\*\*\*\* 节点下的 DAC 的节点上。</span><span class="sxs-lookup"><span data-stu-id="eb13d-201">The instance name is displayed on the node for the DAC under the **Data-tier Applications** node in **Object Explorer**, or the **Deployed Data-tier Applications** node in the **Utility Explorer**.</span></span>  
  
 <span data-ttu-id="eb13d-202">以下选项不应用于 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]，并且在部署到 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]时不显示。</span><span class="sxs-lookup"><span data-stu-id="eb13d-202">The following options do not apply to [!INCLUDE[ssSDS](../../includes/sssds-md.md)], and are not displayed when deploying to [!INCLUDE[ssSDS](../../includes/sssds-md.md)].</span></span>  
  
 <span data-ttu-id="eb13d-203">“使用默认数据库位置”\*\*\*\*- 选择此选项可在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例的默认位置中创建数据库数据和日志文件。</span><span class="sxs-lookup"><span data-stu-id="eb13d-203">**Use the default database location** - Select this option to create the database data and log files in the default location for the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="eb13d-204">将使用数据库名称生成文件名。</span><span class="sxs-lookup"><span data-stu-id="eb13d-204">The file names will be built using the database name.</span></span>  
  
 <span data-ttu-id="eb13d-205">“指定数据库文件”\*\*\*\*- 选择此选项可为数据文件和日志文件指定其他位置或名称。</span><span class="sxs-lookup"><span data-stu-id="eb13d-205">**Specify database files** - Select this option to specify a different location or name for the data and log files.</span></span>  
  
 <span data-ttu-id="eb13d-206">“数据文件路径和名称”\*\*\*\*：- 指定数据文件的完整路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="eb13d-206">**Data file path and name: -** Specify the full path and file name for the data file.</span></span> <span data-ttu-id="eb13d-207">该框将用默认路径和文件名填充。</span><span class="sxs-lookup"><span data-stu-id="eb13d-207">The box is populated with the default path and file name.</span></span> <span data-ttu-id="eb13d-208">编辑该框中的字符串可以更改默认值，或者使用“浏览”按钮可以导航到要用于放置数据文件的文件夹。</span><span class="sxs-lookup"><span data-stu-id="eb13d-208">Edit the string in the box to change the default, or use the Browse button to navigate to the folder where the data file is to be placed.</span></span>  
  
 <span data-ttu-id="eb13d-209">“日志文件路径和名称”\*\*\*\*：- 指定日志文件的完整路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="eb13d-209">**Log file path and name:** - Specify the full path and file name for the log file.</span></span> <span data-ttu-id="eb13d-210">该框将用默认路径和文件名填充。</span><span class="sxs-lookup"><span data-stu-id="eb13d-210">The box is populated with the default path and file name.</span></span> <span data-ttu-id="eb13d-211">编辑该框中的字符串可以更改默认值，或者使用 **“浏览”** 按钮可以导航到要用于放置日志文件的文件夹。</span><span class="sxs-lookup"><span data-stu-id="eb13d-211">Edit the string in the box to change the default, or use the **Browse** button to navigate to the folder where the log file is to be placed.</span></span>  
  
 <span data-ttu-id="eb13d-212">" \*\* \< 上一步**"-返回到 "**选择 DAC 包\*\*" 页。</span><span class="sxs-lookup"><span data-stu-id="eb13d-212">**\< Previous** - Returns to the **Select DAC Package** page.</span></span>  
  
 <span data-ttu-id="eb13d-213">“下一步 >”\*\*\*\*- 继续到“摘要”\*\*\*\* 页。</span><span class="sxs-lookup"><span data-stu-id="eb13d-213">**Next >** - Proceeds to the **Summary** page.</span></span>  
  
 <span data-ttu-id="eb13d-214">“取消”\*\*\*\*- 终止向导且不部署 DAC。</span><span class="sxs-lookup"><span data-stu-id="eb13d-214">**Cancel** - Terminates the wizard without deploying the DAC.</span></span>  
  
##  <a name="summary-page"></a><a name="Summary"></a> <span data-ttu-id="eb13d-215">摘要页</span><span class="sxs-lookup"><span data-stu-id="eb13d-215">Summary Page</span></span>  
 <span data-ttu-id="eb13d-216">使用此页可以查看在部署 DAC 时向导将执行的操作。</span><span class="sxs-lookup"><span data-stu-id="eb13d-216">Use this page to review the actions the wizard will take when deploying the DAC.</span></span>  
  
 <span data-ttu-id="eb13d-217">**将使用以下设置部署 DAC。**</span><span class="sxs-lookup"><span data-stu-id="eb13d-217">**The following settings will be used to deploy your DAC.**</span></span> <span data-ttu-id="eb13d-218">- 查看显示的信息以便确保将执行的操作正确。</span><span class="sxs-lookup"><span data-stu-id="eb13d-218">- Review the information displayed to ensure the actions taken will be correct.</span></span> <span data-ttu-id="eb13d-219">该窗口显示您选择的 DAC 包，以及您为部署的 DAC 实例选择的名称。</span><span class="sxs-lookup"><span data-stu-id="eb13d-219">The window displays the DAC package you selected, and the name you selected for the deployed DAC instance.</span></span> <span data-ttu-id="eb13d-220">该窗口还显示在创建与该 DAC 相关联的数据库时将使用的设置。</span><span class="sxs-lookup"><span data-stu-id="eb13d-220">The window also displays the settings that will be used when creating the database associated with the DAC.</span></span>  
  
 <span data-ttu-id="eb13d-221">" \*\* \< 上一步**"-返回到 "**更新配置\*\*" 页以更改你的选择。</span><span class="sxs-lookup"><span data-stu-id="eb13d-221">**\< Previous** - Returns you to the **Update Configuration** page to change your selections.</span></span>  
  
 <span data-ttu-id="eb13d-222">“下一步 >”\*\*\*\*- 部署 DAC，并在“部署 DAC”\*\*\*\* 页中显示结果。</span><span class="sxs-lookup"><span data-stu-id="eb13d-222">**Next >** - Deploys the DAC and displays the results in the **Deploy DAC** page.</span></span>  
  
 <span data-ttu-id="eb13d-223">“取消”\*\*\*\*- 终止向导且不部署 DAC。</span><span class="sxs-lookup"><span data-stu-id="eb13d-223">**Cancel** - Terminates the wizard without deploying the DAC.</span></span>  
  
##  <a name="deploy-page"></a><a name="Deploy"></a><span data-ttu-id="eb13d-224">部署页</span><span class="sxs-lookup"><span data-stu-id="eb13d-224">Deploy Page</span></span>  
 <span data-ttu-id="eb13d-225">此页报告部署操作是成功还是失败。</span><span class="sxs-lookup"><span data-stu-id="eb13d-225">This page reports the success or failure of the deploy operation.</span></span>  
  
 <span data-ttu-id="eb13d-226">“部署 DAC”\*\*\*\*- 报告为部署 DAC 而执行的每个操作是成功还是失败。</span><span class="sxs-lookup"><span data-stu-id="eb13d-226">**Deploying the DAC** - Reports the success or failure of each action taken to deploy the DAC.</span></span> <span data-ttu-id="eb13d-227">查看信息以便确定每个操作是成功还是失败。</span><span class="sxs-lookup"><span data-stu-id="eb13d-227">Review the information to determine the success or failure of each action.</span></span> <span data-ttu-id="eb13d-228">遇到了错误的任何操作都将在 **“结果”** 列中具有一个链接。</span><span class="sxs-lookup"><span data-stu-id="eb13d-228">Any action that encountered an error will have a link in the **Result** column.</span></span> <span data-ttu-id="eb13d-229">选择该链接可以查看针对该操作的错误报告。</span><span class="sxs-lookup"><span data-stu-id="eb13d-229">Select the link to view a report of the error for that action.</span></span>  
  
 <span data-ttu-id="eb13d-230">“保存报表”\*\*\*\*- 选择此按钮可以将部署报表保存到某一 HTML 文件。</span><span class="sxs-lookup"><span data-stu-id="eb13d-230">**Save Report** - Select this button to save the deployment report to an HTML file.</span></span> <span data-ttu-id="eb13d-231">该文件报告每个操作的状态，并且包括任何操作生成的所有错误。</span><span class="sxs-lookup"><span data-stu-id="eb13d-231">The file reports the status of each action, including all errors generated by any of the actions.</span></span> <span data-ttu-id="eb13d-232">默认文件夹是您的 Windows 帐户的 Documents 文件夹中的 SQL Server Management Studio\DAC Packages 文件夹。</span><span class="sxs-lookup"><span data-stu-id="eb13d-232">The default folder is the SQL Server Management Studio\DAC Packages folder in the Documents folder of your Windows account.</span></span>  
  
 <span data-ttu-id="eb13d-233">“完成” - 终止向导。</span><span class="sxs-lookup"><span data-stu-id="eb13d-233">**Finish** - Terminates the wizard.</span></span>  
  
##  <a name="using-powershell"></a><a name="DeployDACPowerShell"></a> <span data-ttu-id="eb13d-234">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="eb13d-234">Using PowerShell</span></span>  
 <span data-ttu-id="eb13d-235">**在 PowerShell 脚本中使用 Install() 方法部署 DAC**</span><span class="sxs-lookup"><span data-stu-id="eb13d-235">**To deploy a DAC using the Install() method in a PowerShell script**</span></span>  
  
1.  <span data-ttu-id="eb13d-236">创建一个 SMO Server 对象，并将该对象设置为要将 DAC 部署到的实例。</span><span class="sxs-lookup"><span data-stu-id="eb13d-236">Create a SMO Server object and set it to the instance to which you want to deploy the DAC.</span></span>  
  
2.  <span data-ttu-id="eb13d-237">打开 `ServerConnection` 对象，并连接到同一实例。</span><span class="sxs-lookup"><span data-stu-id="eb13d-237">Open a `ServerConnection` object and connect to the same instance.</span></span>  
  
3.  <span data-ttu-id="eb13d-238">使用 `System.IO.File` 加载 DAC 包文件。</span><span class="sxs-lookup"><span data-stu-id="eb13d-238">Use `System.IO.File` to load the DAC package file.</span></span>  
  
4.  <span data-ttu-id="eb13d-239">使用 `add_DacActionStarted` 和 `add_DacActionFinished` 订阅 DAC 部署事件。</span><span class="sxs-lookup"><span data-stu-id="eb13d-239">Use `add_DacActionStarted` and `add_DacActionFinished` to subscribe to the DAC deployment events.</span></span>  
  
5.  <span data-ttu-id="eb13d-240">设置 `DatabaseDeploymentProperties` 。</span><span class="sxs-lookup"><span data-stu-id="eb13d-240">Set the `DatabaseDeploymentProperties`.</span></span>  
  
6.  <span data-ttu-id="eb13d-241">使用 `DacStore.Install` 方法部署 DAC。</span><span class="sxs-lookup"><span data-stu-id="eb13d-241">Use the `DacStore.Install` method to deploy the DAC.</span></span>  
  
7.  <span data-ttu-id="eb13d-242">关闭用于读取 DAC 包文件的文件流。</span><span class="sxs-lookup"><span data-stu-id="eb13d-242">Close the file stream used to read the DAC package file.</span></span>  
  
### <a name="example-powershell"></a><span data-ttu-id="eb13d-243">示例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="eb13d-243">Example (PowerShell)</span></span>  
 <span data-ttu-id="eb13d-244">下面的示例使用来自 MyApplication.dacpac 包的 DAC 定义，将名为 MyApplication 的 DAC 部署到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的默认实例。</span><span class="sxs-lookup"><span data-stu-id="eb13d-244">The following example deploys a DAC named MyApplication on a default instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], using a DAC definition from a MyApplication.dacpac package.</span></span>  
  
```powershell
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = Get-Item .  
  
## Open a Common.ServerConnection to the same instance.  
$serverconnection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection($srv.ConnectionContext.SqlConnectionObject)  
$serverconnection.Connect()  
$dacstore = New-Object Microsoft.SqlServer.Management.Dac.DacStore($serverconnection)  
  
## Load the DAC package file.  
$dacpacPath = "C:\MyDACs\MyApplication.dacpac"  
$fileStream = [System.IO.File]::Open($dacpacPath,[System.IO.FileMode]::OpenOrCreate)  
$dacType = [Microsoft.SqlServer.Management.Dac.DacType]::Load($fileStream)  
  
## Subscribe to the DAC deployment events.  
$dacstore.add_DacActionStarted({Write-Host `n`nStarting at $(get-date) :: $_.Description})  
$dacstore.add_DacActionFinished({Write-Host Completed at $(get-date) :: $_.Description})  
  
## Deploy the DAC and create the database.  
$dacName  = "MyApplication"  
$evaluateTSPolicy = $true  
$deployProperties = New-Object Microsoft.SqlServer.Management.Dac.DatabaseDeploymentProperties($serverconnection,$dacName)  
$dacstore.Install($dacType, $deployProperties, $evaluateTSPolicy)  
$fileStream.Close()  
```  
  
## <a name="see-also"></a><span data-ttu-id="eb13d-245">另请参阅</span><span class="sxs-lookup"><span data-stu-id="eb13d-245">See Also</span></span>  
 <span data-ttu-id="eb13d-246">[数据层应用程序](data-tier-applications.md) </span><span class="sxs-lookup"><span data-stu-id="eb13d-246">[Data-tier Applications](data-tier-applications.md) </span></span>  
 <span data-ttu-id="eb13d-247">[从数据库中提取 DAC](extract-a-dac-from-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="eb13d-247">[Extract a DAC From a Database](extract-a-dac-from-a-database.md) </span></span>  
 [<span data-ttu-id="eb13d-248">数据库标识符</span><span class="sxs-lookup"><span data-stu-id="eb13d-248">Database Identifiers</span></span>](../databases/database-identifiers.md)  
