---
title: Integration Services 项目转换向导 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.migrationwizard.f1
ms.assetid: a192b094-4d0f-4c21-b911-460ec844a49f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c47dc8ed1d0485a62128be732cc34de1dca35740
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586871"
---
# <a name="integration-services-project-conversion-wizard"></a><span data-ttu-id="f0de1-102">Integration Services 项目转换向导</span><span class="sxs-lookup"><span data-stu-id="f0de1-102">Integration Services Project Conversion Wizard</span></span>
  <span data-ttu-id="f0de1-103">**“Integration Services 项目转换向导”** 可以将项目转换为项目部署模型。</span><span class="sxs-lookup"><span data-stu-id="f0de1-103">The **Integration Services Project Conversion Wizard** converts a project to the project deployment model.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f0de1-104">如果项目包含一个或多个数据源，则在项目转换完成时删除数据源。</span><span class="sxs-lookup"><span data-stu-id="f0de1-104">If the project contains one or more datasources, the datasources are removed when the project conversion is completed.</span></span> <span data-ttu-id="f0de1-105">若要创建到可由项目中的包共享的数据源的连接，请在项目级别添加连接管理器。</span><span class="sxs-lookup"><span data-stu-id="f0de1-105">To create a connection to a data source that can be shared by the packages in the project, add a connection manager at the project level.</span></span> <span data-ttu-id="f0de1-106">有关详细信息，请参阅 [在包中添加、删除或共享连接管理器](../../2014/integration-services/add-delete-or-share-a-connection-manager-in-a-package.md)。</span><span class="sxs-lookup"><span data-stu-id="f0de1-106">For more information, see [Add, Delete, or Share a Connection Manager in a Package](../../2014/integration-services/add-delete-or-share-a-connection-manager-in-a-package.md).</span></span>  
  
 <span data-ttu-id="f0de1-107">**您希望做什么？**</span><span class="sxs-lookup"><span data-stu-id="f0de1-107">**What do you want to do?**</span></span>  
  
-   [<span data-ttu-id="f0de1-108">打开“Integration Services 项目转换向导”</span><span class="sxs-lookup"><span data-stu-id="f0de1-108">Open the Integration Services Project Conversion Wizard</span></span>](#open_dialog)  
  
-   [<span data-ttu-id="f0de1-109">设置“查找包”页上的选项</span><span class="sxs-lookup"><span data-stu-id="f0de1-109">Set Options on the Locate Packages Page</span></span>](#locate)  
  
-   [<span data-ttu-id="f0de1-110">设置“选择包”页上的选项</span><span class="sxs-lookup"><span data-stu-id="f0de1-110">Set Options on the Select Packages Page</span></span>](#selectPackages)  
  
-   [<span data-ttu-id="f0de1-111">设置“选择目标”页上的选项</span><span class="sxs-lookup"><span data-stu-id="f0de1-111">Set Options on the Select Destination Page</span></span>](#destination)  
  
-   [<span data-ttu-id="f0de1-112">设置“指定项目属性”页上的选项</span><span class="sxs-lookup"><span data-stu-id="f0de1-112">Set Options on the Specify Project Properties Page</span></span>](#projectProperties)  
  
-   [<span data-ttu-id="f0de1-113">设置“更新执行包任务”页上的选项</span><span class="sxs-lookup"><span data-stu-id="f0de1-113">Set Options on the Update Execute Package Task Page</span></span>](#executePackage)  
  
-   [<span data-ttu-id="f0de1-114">设置“选择配置”页上的选项</span><span class="sxs-lookup"><span data-stu-id="f0de1-114">Set Options on the Select Configurations Page</span></span>](#configurations)  
  
-   [<span data-ttu-id="f0de1-115">设置“创建参数”页上的选项</span><span class="sxs-lookup"><span data-stu-id="f0de1-115">Set Options on the Create Parameters Page</span></span>](#createParameters)  
  
-   [<span data-ttu-id="f0de1-116">设置“配置参数”页上的选项</span><span class="sxs-lookup"><span data-stu-id="f0de1-116">Set Options on the Configure Parameters Page</span></span>](#configureParameters)  
  
-   [<span data-ttu-id="f0de1-117">设置“检查”页上的选项</span><span class="sxs-lookup"><span data-stu-id="f0de1-117">Set the Options on the Review page</span></span>](#review)  
  
-   [<span data-ttu-id="f0de1-118">设置执行转换的选项</span><span class="sxs-lookup"><span data-stu-id="f0de1-118">Set the Options on the Perform Conversion</span></span>](#conversion)  
  
##  <a name="open-the-integration-services-project-conversion-wizard"></a><a name="open_dialog"></a><span data-ttu-id="f0de1-119">打开 Integration Services 项目转换向导</span><span class="sxs-lookup"><span data-stu-id="f0de1-119">Open the Integration Services Project Conversion Wizard</span></span>  
 <span data-ttu-id="f0de1-120">执行下列操作之一以打开 **“Integration Services 项目转换”** 向导。</span><span class="sxs-lookup"><span data-stu-id="f0de1-120">Do one of the following to open the **Integration Services Project Conversion** Wizard.</span></span>  
  
-   <span data-ttu-id="f0de1-121">在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中打开该项目，然后在解决方案资源管理器中，右键单击该项目并单击“转换为项目部署模型”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f0de1-121">Open the project in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], and then in Solution Explorer, right-click the project and click **Convert to Project Deployment Model**.</span></span>  
  
-   <span data-ttu-id="f0de1-122">从 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 的对象资源管理器中，右键单击“项目”\*\*\*\* 节点并选择“导入包”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f0de1-122">From Object Explorer in [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], right-click the **Projects** node and select **Import Packages**.</span></span>  
  
 <span data-ttu-id="f0de1-123">根据您是从 **还是从** 运行 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] “Integration Services 项目转换向导” [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]，该向导将执行不同的转换任务。</span><span class="sxs-lookup"><span data-stu-id="f0de1-123">Depending on whether you run the **Integration Services Project Conversion Wizard** from [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] or from [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], the wizard performs different conversion tasks.</span></span> <span data-ttu-id="f0de1-124">有关详细信息，请参阅 [Deploy Projects to Integration Services Server](../../2014/integration-services/deploy-projects-to-integration-services-server.md)。</span><span class="sxs-lookup"><span data-stu-id="f0de1-124">For more information, see [Deploy Projects to Integration Services Server](../../2014/integration-services/deploy-projects-to-integration-services-server.md).</span></span>  
  
##  <a name="set-options-on-the-locate-packages-page"></a><a name="locate"></a><span data-ttu-id="f0de1-125">设置 "查找包" 页上的选项</span><span class="sxs-lookup"><span data-stu-id="f0de1-125">Set Options on the Locate Packages Page</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f0de1-126"> 只有在您从 **运行该向导时，** “查找包” [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]页才可用。</span><span class="sxs-lookup"><span data-stu-id="f0de1-126">The **Locate Packages** page is available only when you run the wizard from [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span>  
  
 <span data-ttu-id="f0de1-127">在“源”下拉列表中选择“文件系统”时，该页显示以下选项\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f0de1-127">The following option displays on the page when you select **File system** in the **Source** drop-down list.</span></span> <span data-ttu-id="f0de1-128">当包驻留在文件系统中时选择此选项。</span><span class="sxs-lookup"><span data-stu-id="f0de1-128">Select this option when the package is resides in the file system.</span></span>  
  
 <span data-ttu-id="f0de1-129">**文件夹**</span><span class="sxs-lookup"><span data-stu-id="f0de1-129">**Folder**</span></span>  
 <span data-ttu-id="f0de1-130">键入包路径，或通过单击“浏览”\*\*\*\* 导航到该包。</span><span class="sxs-lookup"><span data-stu-id="f0de1-130">Type the package path, or navigate to the package by clicking **Browse**.</span></span>  
  
 <span data-ttu-id="f0de1-131">在“源”下拉列表中选择“SSIS 包存储区”时，该页显示以下选项\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f0de1-131">The following options display on the page when you select **SSIS Package Store** in the **Source** drop-down list.</span></span> <span data-ttu-id="f0de1-132">有关包存储区的详细信息，请参阅[包管理（SSIS 服务）](service/package-management-ssis-service.md)。</span><span class="sxs-lookup"><span data-stu-id="f0de1-132">For more information about the package store, see [Package Management &#40;SSIS Service&#41;](service/package-management-ssis-service.md).</span></span>  
  
 <span data-ttu-id="f0de1-133">**Server**</span><span class="sxs-lookup"><span data-stu-id="f0de1-133">**Server**</span></span>  
 <span data-ttu-id="f0de1-134">键入服务器名称或选择该服务器。</span><span class="sxs-lookup"><span data-stu-id="f0de1-134">Type the server name or select the server.</span></span>  
  
 <span data-ttu-id="f0de1-135">**文件夹**</span><span class="sxs-lookup"><span data-stu-id="f0de1-135">**Folder**</span></span>  
 <span data-ttu-id="f0de1-136">键入包路径，或通过单击“浏览”\*\*\*\* 导航到该包。</span><span class="sxs-lookup"><span data-stu-id="f0de1-136">Type the package path, or navigate to the package by clicking **Browse**.</span></span>  
  
 <span data-ttu-id="f0de1-137">在“源”下拉列表中选择“Microsoft SQL Server”时，该页显示以下选项\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f0de1-137">The following options display on the page when you select **Microsoft SQL Server** in the **Source** drop-down list.</span></span> <span data-ttu-id="f0de1-138">当包驻留在 Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]中时选择此选项。</span><span class="sxs-lookup"><span data-stu-id="f0de1-138">Select this option when the package resides in Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="f0de1-139">**Server**</span><span class="sxs-lookup"><span data-stu-id="f0de1-139">**Server**</span></span>  
 <span data-ttu-id="f0de1-140">键入服务器名称或选择该服务器。</span><span class="sxs-lookup"><span data-stu-id="f0de1-140">Type the server name or select the server.</span></span>  
  
 <span data-ttu-id="f0de1-141">**使用 Windows 身份验证**</span><span class="sxs-lookup"><span data-stu-id="f0de1-141">**Use Windows authentication**</span></span>  
 <span data-ttu-id="f0de1-142">Microsoft Windows 身份验证模式允许用户通过 Windows 用户帐户进行连接。</span><span class="sxs-lookup"><span data-stu-id="f0de1-142">Microsoft Windows Authentication mode allows a user to connect through a Windows user account.</span></span> <span data-ttu-id="f0de1-143">如果使用 Windows 身份验证，则不需要提供用户名或密码。</span><span class="sxs-lookup"><span data-stu-id="f0de1-143">If you use Windows Authentication, you do not need to provide a user name or password.</span></span>  
  
 <span data-ttu-id="f0de1-144">**使用 SQL Server 身份验证**</span><span class="sxs-lookup"><span data-stu-id="f0de1-144">**Use SQL Server authentication**</span></span>  
 <span data-ttu-id="f0de1-145">当户使用指定的登录名和密码从不可信连接进行连接时， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 将通过检查是否已设置 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 登录帐户以及指定的密码是否与以前记录的密码匹配，对该连接进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="f0de1-145">When a user connects with a specified login name and password from a non-trusted connection, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] authenticates the connection by checking to see if a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] login account has been set up and if the specified password matches the one previously recorded.</span></span> <span data-ttu-id="f0de1-146">如果未设置 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 登录帐户，则身份验证失败，并且用户会收到一条错误消息。</span><span class="sxs-lookup"><span data-stu-id="f0de1-146">If [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] does not have a login account set, authentication fails, and the user receives an error message.</span></span>  
  
 <span data-ttu-id="f0de1-147">**用户名**</span><span class="sxs-lookup"><span data-stu-id="f0de1-147">**User name**</span></span>  
 <span data-ttu-id="f0de1-148">使用 SQL Server 身份验证时，指定用户名。</span><span class="sxs-lookup"><span data-stu-id="f0de1-148">Specify a user name when you are using SQL Server Authentication.</span></span>  
  
 <span data-ttu-id="f0de1-149">**密码**</span><span class="sxs-lookup"><span data-stu-id="f0de1-149">**Password**</span></span>  
 <span data-ttu-id="f0de1-150">使用 SQL Server 身份验证时，提供密码。</span><span class="sxs-lookup"><span data-stu-id="f0de1-150">Provide the password when you are using SQL Server Authentication.</span></span>  
  
 <span data-ttu-id="f0de1-151">**文件夹**</span><span class="sxs-lookup"><span data-stu-id="f0de1-151">**Folder**</span></span>  
 <span data-ttu-id="f0de1-152">键入包路径，或通过单击“浏览”\*\*\*\* 导航到该包。</span><span class="sxs-lookup"><span data-stu-id="f0de1-152">Type the package path, or navigate to the package by clicking **Browse**.</span></span>  
  
##  <a name="set-options-on-the-select-packages-page"></a><a name="selectPackages"></a><span data-ttu-id="f0de1-153">设置 "选择包" 页上的选项</span><span class="sxs-lookup"><span data-stu-id="f0de1-153">Set Options on the Select Packages Page</span></span>  
 <span data-ttu-id="f0de1-154">**包名称**</span><span class="sxs-lookup"><span data-stu-id="f0de1-154">**Package Name**</span></span>  
 <span data-ttu-id="f0de1-155">列出包文件。</span><span class="sxs-lookup"><span data-stu-id="f0de1-155">Lists the package file.</span></span>  
  
 <span data-ttu-id="f0de1-156">**Status**</span><span class="sxs-lookup"><span data-stu-id="f0de1-156">**Status**</span></span>  
 <span data-ttu-id="f0de1-157">指示包是否已准备好转换为项目部署模型。</span><span class="sxs-lookup"><span data-stu-id="f0de1-157">Indicates whether a package is ready to convert to the project deployment model.</span></span>  
  
 <span data-ttu-id="f0de1-158">**Message**</span><span class="sxs-lookup"><span data-stu-id="f0de1-158">**Message**</span></span>  
 <span data-ttu-id="f0de1-159">显示与包关联的消息。</span><span class="sxs-lookup"><span data-stu-id="f0de1-159">Displays a message associated with the package.</span></span>  
  
 <span data-ttu-id="f0de1-160">**密码**</span><span class="sxs-lookup"><span data-stu-id="f0de1-160">**Password**</span></span>  
 <span data-ttu-id="f0de1-161">显示与包关联的密码。</span><span class="sxs-lookup"><span data-stu-id="f0de1-161">Displays a password associated with the package.</span></span> <span data-ttu-id="f0de1-162">密码文本将被隐藏。</span><span class="sxs-lookup"><span data-stu-id="f0de1-162">The password text is hidden.</span></span>  
  
 <span data-ttu-id="f0de1-163">**应用于所选内容**</span><span class="sxs-lookup"><span data-stu-id="f0de1-163">**Apply to selection**</span></span>  
 <span data-ttu-id="f0de1-164">单击以将“密码”\*\*\*\* 文本框中的密码应用于一个或多个所选包。</span><span class="sxs-lookup"><span data-stu-id="f0de1-164">Click to apply the password in the **Password** text box, to the selected package or packages.</span></span>  
  
 <span data-ttu-id="f0de1-165">**“刷新”**</span><span class="sxs-lookup"><span data-stu-id="f0de1-165">**Refresh**</span></span>  
 <span data-ttu-id="f0de1-166">刷新包的列表。</span><span class="sxs-lookup"><span data-stu-id="f0de1-166">Refreshes the list of packages.</span></span>  
  
##  <a name="set-options-on-the-select-destination-page"></a><a name="destination"></a><span data-ttu-id="f0de1-167">设置 "选择目标" 页上的选项</span><span class="sxs-lookup"><span data-stu-id="f0de1-167">Set Options on the Select Destination Page</span></span>  
 <span data-ttu-id="f0de1-168">在此页上，指定新的项目部署文件 (.ispac) 的名称和路径或者选择一个现有文件。</span><span class="sxs-lookup"><span data-stu-id="f0de1-168">On this page, specify the name and path for a new project deployment file (.ispac) or select an existing file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f0de1-169"> 只有在您从 **运行该向导时，** “选择目标” [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]页才可用。</span><span class="sxs-lookup"><span data-stu-id="f0de1-169">The **Select Destination** page is available only when you run the wizard from [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span>  
  
 <span data-ttu-id="f0de1-170">“输出路径” </span><span class="sxs-lookup"><span data-stu-id="f0de1-170">**Output path**</span></span>  
 <span data-ttu-id="f0de1-171">键入部署文件的路径，或通过单击“浏览”\*\*\*\* 导航到该文件。</span><span class="sxs-lookup"><span data-stu-id="f0de1-171">Type the path for the deployment file or navigate to the file by clicking **Browse**.</span></span>  
  
 <span data-ttu-id="f0de1-172">**项目名称**</span><span class="sxs-lookup"><span data-stu-id="f0de1-172">**Project name**</span></span>  
 <span data-ttu-id="f0de1-173">键入项目名称。</span><span class="sxs-lookup"><span data-stu-id="f0de1-173">Type the project name.</span></span>  
  
 <span data-ttu-id="f0de1-174">**保护级别**</span><span class="sxs-lookup"><span data-stu-id="f0de1-174">**Protection level**</span></span>  
 <span data-ttu-id="f0de1-175">选择保护级别。</span><span class="sxs-lookup"><span data-stu-id="f0de1-175">Select the protection level.</span></span> <span data-ttu-id="f0de1-176">有关详细信息，请参阅 [Access Control for Sensitive Data in Packages](security/access-control-for-sensitive-data-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="f0de1-176">For more information, see [Access Control for Sensitive Data in Packages](security/access-control-for-sensitive-data-in-packages.md).</span></span>  
  
 <span data-ttu-id="f0de1-177">**项目说明**</span><span class="sxs-lookup"><span data-stu-id="f0de1-177">**Project description**</span></span>  
 <span data-ttu-id="f0de1-178">键入项目的可选说明。</span><span class="sxs-lookup"><span data-stu-id="f0de1-178">Type an optional description for the project.</span></span>  
  
##  <a name="set-options-on-the-specify-project-properties-page"></a><a name="projectProperties"></a><span data-ttu-id="f0de1-179">设置 "指定项目属性" 页上的选项</span><span class="sxs-lookup"><span data-stu-id="f0de1-179">Set Options on the Specify Project Properties Page</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f0de1-180"> 只有在您从 **运行该向导时，** “指定项目属性” [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]页才可用。</span><span class="sxs-lookup"><span data-stu-id="f0de1-180">The **Specify Project Properties** page is available only when you run the wizard from [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].</span></span>  
  
 <span data-ttu-id="f0de1-181">**项目名称**</span><span class="sxs-lookup"><span data-stu-id="f0de1-181">**Project name**</span></span>  
 <span data-ttu-id="f0de1-182">列出项目名称。</span><span class="sxs-lookup"><span data-stu-id="f0de1-182">Lists the project name.</span></span>  
  
 <span data-ttu-id="f0de1-183">**保护级别**</span><span class="sxs-lookup"><span data-stu-id="f0de1-183">**Protection level**</span></span>  
 <span data-ttu-id="f0de1-184">为项目中所含的包选择保护级别。</span><span class="sxs-lookup"><span data-stu-id="f0de1-184">Select a protection level for the packages contained in the project.</span></span> <span data-ttu-id="f0de1-185">有关保护级别的详细信息，请参阅 [Access Control for Sensitive Data in Packages](security/access-control-for-sensitive-data-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="f0de1-185">For more information about protection levels, see [Access Control for Sensitive Data in Packages](security/access-control-for-sensitive-data-in-packages.md).</span></span>  
  
 <span data-ttu-id="f0de1-186">**项目说明**</span><span class="sxs-lookup"><span data-stu-id="f0de1-186">**Project description**</span></span>  
 <span data-ttu-id="f0de1-187">键入可选的项目说明。</span><span class="sxs-lookup"><span data-stu-id="f0de1-187">Type an optional project description.</span></span>  
  
##  <a name="set-options-on-the-update-execute-package-task-page"></a><a name="executePackage"></a><span data-ttu-id="f0de1-188">设置 "更新执行包任务" 页上的选项</span><span class="sxs-lookup"><span data-stu-id="f0de1-188">Set Options on the Update Execute Package Task Page</span></span>  
 <span data-ttu-id="f0de1-189">更新包中所含的执行包任务，以使用基于项目的引用。</span><span class="sxs-lookup"><span data-stu-id="f0de1-189">Update Execute Package Tasks contain in the packages, to use a project-based reference.</span></span> <span data-ttu-id="f0de1-190">有关详细信息，请参阅 [Execute Package Task Editor](../../2014/integration-services/execute-package-task-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="f0de1-190">For more information, see [Execute Package Task Editor](../../2014/integration-services/execute-package-task-editor.md).</span></span>  
  
 <span data-ttu-id="f0de1-191">**父包**</span><span class="sxs-lookup"><span data-stu-id="f0de1-191">**Parent Package**</span></span>  
 <span data-ttu-id="f0de1-192">列出使用执行包任务执行子包的包名称。</span><span class="sxs-lookup"><span data-stu-id="f0de1-192">Lists the name of the package that executes the child package using the Execute Package task.</span></span>  
  
 <span data-ttu-id="f0de1-193">**任务名称**</span><span class="sxs-lookup"><span data-stu-id="f0de1-193">**Task name**</span></span>  
 <span data-ttu-id="f0de1-194">列出执行包任务的名称。</span><span class="sxs-lookup"><span data-stu-id="f0de1-194">Lists the name of the Execute Package task.</span></span>  
  
 <span data-ttu-id="f0de1-195">**原始引用**</span><span class="sxs-lookup"><span data-stu-id="f0de1-195">**Original reference**</span></span>  
 <span data-ttu-id="f0de1-196">列出子包的当前路径。</span><span class="sxs-lookup"><span data-stu-id="f0de1-196">Lists the current path of the child package.</span></span>  
  
 <span data-ttu-id="f0de1-197">**分配引用**</span><span class="sxs-lookup"><span data-stu-id="f0de1-197">**Assign reference**</span></span>  
 <span data-ttu-id="f0de1-198">选择存储在项目中的子包。</span><span class="sxs-lookup"><span data-stu-id="f0de1-198">Select a child package stored in the project.</span></span>  
  
##  <a name="set-options-on-the-select-configurations-page"></a><a name="configurations"></a><span data-ttu-id="f0de1-199">设置 "选择配置" 页上的选项</span><span class="sxs-lookup"><span data-stu-id="f0de1-199">Set Options on the Select Configurations Page</span></span>  
 <span data-ttu-id="f0de1-200">选择您要用参数替换的包配置。</span><span class="sxs-lookup"><span data-stu-id="f0de1-200">Select the package configurations that you want to replace with parameters.</span></span>  
  
 <span data-ttu-id="f0de1-201">**包**</span><span class="sxs-lookup"><span data-stu-id="f0de1-201">**Package**</span></span>  
 <span data-ttu-id="f0de1-202">列出包文件。</span><span class="sxs-lookup"><span data-stu-id="f0de1-202">Lists the package file.</span></span>  
  
 <span data-ttu-id="f0de1-203">**Type**</span><span class="sxs-lookup"><span data-stu-id="f0de1-203">**Type**</span></span>  
 <span data-ttu-id="f0de1-204">列出配置类型，如 XML 配置文件。</span><span class="sxs-lookup"><span data-stu-id="f0de1-204">Lists the type of configuration, such as an XML configuration file.</span></span>  
  
 <span data-ttu-id="f0de1-205">**配置字符串**</span><span class="sxs-lookup"><span data-stu-id="f0de1-205">**Configuration String**</span></span>  
 <span data-ttu-id="f0de1-206">列出配置文件的路径。</span><span class="sxs-lookup"><span data-stu-id="f0de1-206">Lists the path of the configuration file.</span></span>  
  
 <span data-ttu-id="f0de1-207">**Status**</span><span class="sxs-lookup"><span data-stu-id="f0de1-207">**Status**</span></span>  
 <span data-ttu-id="f0de1-208">显示配置的状态消息。</span><span class="sxs-lookup"><span data-stu-id="f0de1-208">Displays a status message for the configuration.</span></span> <span data-ttu-id="f0de1-209">单击该消息可以查看整个消息文本。</span><span class="sxs-lookup"><span data-stu-id="f0de1-209">Click the message to view the entire message text.</span></span>  
  
 <span data-ttu-id="f0de1-210">**添加配置**</span><span class="sxs-lookup"><span data-stu-id="f0de1-210">**Add Configurations**</span></span>  
 <span data-ttu-id="f0de1-211">将在其他项目中包含的包配置添加到要用参数替换的可用配置的列表中。</span><span class="sxs-lookup"><span data-stu-id="f0de1-211">Add package configurations contained in other projects to the list of available configurations that you want to replace with parameters.</span></span> <span data-ttu-id="f0de1-212">您可以选择存储在文件系统或 SQL Server 中的配置。</span><span class="sxs-lookup"><span data-stu-id="f0de1-212">You can select configurations stored in a file system or stored in SQL Server.</span></span>  
  
 <span data-ttu-id="f0de1-213">**“刷新”**</span><span class="sxs-lookup"><span data-stu-id="f0de1-213">**Refresh**</span></span>  
 <span data-ttu-id="f0de1-214">单击以刷新配置列表。</span><span class="sxs-lookup"><span data-stu-id="f0de1-214">Click to refresh the list of configurations.</span></span>  
  
 <span data-ttu-id="f0de1-215">**在转换后删除所有包的配置**</span><span class="sxs-lookup"><span data-stu-id="f0de1-215">**Remove configurations from all packages after conversion**</span></span>  
 <span data-ttu-id="f0de1-216">建议通过选择此选项从项目中删除所有配置。</span><span class="sxs-lookup"><span data-stu-id="f0de1-216">It is recommended that you remove all configurations from the project by selecting this option.</span></span>  
  
 <span data-ttu-id="f0de1-217">如果没有选择此选项，将只删除已选择用参数替换的配置。</span><span class="sxs-lookup"><span data-stu-id="f0de1-217">If you don't select this option, only the configurations that you selected to replace with parameters are removed.</span></span>  
  
##  <a name="set-options-on-the-create-parameters-page"></a><a name="createParameters"></a><span data-ttu-id="f0de1-218">设置 "创建参数" 页上的选项</span><span class="sxs-lookup"><span data-stu-id="f0de1-218">Set Options on the Create Parameters Page</span></span>  
 <span data-ttu-id="f0de1-219">选择每个配置属性的参数名称和作用域。</span><span class="sxs-lookup"><span data-stu-id="f0de1-219">Select the parameter name and scope for each configuration property.</span></span>  
  
 <span data-ttu-id="f0de1-220">**包**</span><span class="sxs-lookup"><span data-stu-id="f0de1-220">**Package**</span></span>  
 <span data-ttu-id="f0de1-221">列出包文件。</span><span class="sxs-lookup"><span data-stu-id="f0de1-221">Lists the package file.</span></span>  
  
 <span data-ttu-id="f0de1-222">**参数名称**</span><span class="sxs-lookup"><span data-stu-id="f0de1-222">**Parameter Name**</span></span>  
 <span data-ttu-id="f0de1-223">列出参数名称。</span><span class="sxs-lookup"><span data-stu-id="f0de1-223">Lists the parameter name.</span></span>  
  
 <span data-ttu-id="f0de1-224">**范围**</span><span class="sxs-lookup"><span data-stu-id="f0de1-224">**Scope**</span></span>  
 <span data-ttu-id="f0de1-225">选择参数的作用域（包或项目）。</span><span class="sxs-lookup"><span data-stu-id="f0de1-225">Select the scope of the parameter, either package or project.</span></span>  
  
##  <a name="set-options-on-the-configure-parameters-page"></a><a name="configureParameters"></a><span data-ttu-id="f0de1-226">设置 "配置参数" 页上的选项</span><span class="sxs-lookup"><span data-stu-id="f0de1-226">Set Options on the Configure Parameters Page</span></span>  
 <span data-ttu-id="f0de1-227">**名称**</span><span class="sxs-lookup"><span data-stu-id="f0de1-227">**Name**</span></span>  
 <span data-ttu-id="f0de1-228">列出参数名称。</span><span class="sxs-lookup"><span data-stu-id="f0de1-228">Lists the parameter name.</span></span>  
  
 <span data-ttu-id="f0de1-229">**范围**</span><span class="sxs-lookup"><span data-stu-id="f0de1-229">**Scope**</span></span>  
 <span data-ttu-id="f0de1-230">列出参数的作用域。</span><span class="sxs-lookup"><span data-stu-id="f0de1-230">Lists the scope of the parameter.</span></span>  
  
 <span data-ttu-id="f0de1-231">**值**</span><span class="sxs-lookup"><span data-stu-id="f0de1-231">**Value**</span></span>  
 <span data-ttu-id="f0de1-232">列出参数值。</span><span class="sxs-lookup"><span data-stu-id="f0de1-232">Lists the parameter value.</span></span>  
  
 <span data-ttu-id="f0de1-233">单击值字段旁边的省略号按钮以配置参数属性。</span><span class="sxs-lookup"><span data-stu-id="f0de1-233">Click the ellipsis button next to the value field to configure the parameter properties.</span></span>  
  
 <span data-ttu-id="f0de1-234">在 **“设置参数详细信息”** 对话框中，可以编辑参数值。</span><span class="sxs-lookup"><span data-stu-id="f0de1-234">In the **Set Parameter Details** dialog box, you can edit the parameter value.</span></span> <span data-ttu-id="f0de1-235">还可以指定在运行包时是否必须提供参数值。</span><span class="sxs-lookup"><span data-stu-id="f0de1-235">You can also specify whether the parameter value must be provided when you run the package.</span></span>  
  
 <span data-ttu-id="f0de1-236">您可以通过单击参数旁的“浏览”按钮，在 **的** “配置” **对话框的** “参数” [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]页中修改值。</span><span class="sxs-lookup"><span data-stu-id="f0de1-236">You can modify value in the **Parameters** page of the **Configure** dialog box in [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], by clicking the browse button next to the parameter.</span></span> <span data-ttu-id="f0de1-237">将显示 **“设置参数值”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="f0de1-237">The **Set Parameter Value** dialog box appears.</span></span>  
  
 <span data-ttu-id="f0de1-238">**“设置参数详细信息”** 对话框还列出参数值的数据类型和参数的来源。</span><span class="sxs-lookup"><span data-stu-id="f0de1-238">The **Set Parameter Details** dialog box also lists the data type of the parameter value and the origin of the parameter.</span></span>  
  
##  <a name="set-the-options-on-the-review-page"></a><a name="review"></a><span data-ttu-id="f0de1-239">设置 "检查" 页上的选项</span><span class="sxs-lookup"><span data-stu-id="f0de1-239">Set the Options on the Review page</span></span>  
 <span data-ttu-id="f0de1-240">使用“检查”页可以确认为项目转换选择的选项\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f0de1-240">Use the **Review** page to confirm the options that you've selected for the conversion of the project.</span></span>  
  
 <span data-ttu-id="f0de1-241">**上一页**</span><span class="sxs-lookup"><span data-stu-id="f0de1-241">**Previous**</span></span>  
 <span data-ttu-id="f0de1-242">单击以更改选项。</span><span class="sxs-lookup"><span data-stu-id="f0de1-242">Click to change an option.</span></span>  
  
 <span data-ttu-id="f0de1-243">**转换**</span><span class="sxs-lookup"><span data-stu-id="f0de1-243">**Convert**</span></span>  
 <span data-ttu-id="f0de1-244">单击以将项目转换为项目部署模型。</span><span class="sxs-lookup"><span data-stu-id="f0de1-244">Click to convert the project to the project deployment model.</span></span>  
  
##  <a name="set-the-options-on-the-perform-conversion"></a><a name="conversion"></a><span data-ttu-id="f0de1-245">设置执行转换的选项</span><span class="sxs-lookup"><span data-stu-id="f0de1-245">Set the Options on the Perform Conversion</span></span>  
 <span data-ttu-id="f0de1-246">“执行转换”页显示项目转换的状态。</span><span class="sxs-lookup"><span data-stu-id="f0de1-246">The Perform Conversion page shows status of the project conversion.</span></span>  
  
 <span data-ttu-id="f0de1-247">**Action**</span><span class="sxs-lookup"><span data-stu-id="f0de1-247">**Action**</span></span>  
 <span data-ttu-id="f0de1-248">列出特定的转换步骤。</span><span class="sxs-lookup"><span data-stu-id="f0de1-248">Lists a specific conversion step.</span></span>  
  
 <span data-ttu-id="f0de1-249">**结果**</span><span class="sxs-lookup"><span data-stu-id="f0de1-249">**Result**</span></span>  
 <span data-ttu-id="f0de1-250">列出每个转换步骤的状态。</span><span class="sxs-lookup"><span data-stu-id="f0de1-250">Lists the status of each conversion step.</span></span> <span data-ttu-id="f0de1-251">单击状态消息可获取详细信息。</span><span class="sxs-lookup"><span data-stu-id="f0de1-251">Click the status message for more information.</span></span>  
  
 <span data-ttu-id="f0de1-252">直到在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]中保存项目后，才保存项目转换。</span><span class="sxs-lookup"><span data-stu-id="f0de1-252">The project conversion is not saved until the project is saved in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].</span></span>  
  
 <span data-ttu-id="f0de1-253">**保存报表**</span><span class="sxs-lookup"><span data-stu-id="f0de1-253">**Save report**</span></span>  
 <span data-ttu-id="f0de1-254">单击以在 .xml 文件中保存项目转换的摘要。</span><span class="sxs-lookup"><span data-stu-id="f0de1-254">Click to save a summary of the project conversion in an .xml file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0de1-255">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f0de1-255">See Also</span></span>  
 [<span data-ttu-id="f0de1-256">Deploy Projects to Integration Services Server</span><span class="sxs-lookup"><span data-stu-id="f0de1-256">Deploy Projects to Integration Services Server</span></span>](../../2014/integration-services/deploy-projects-to-integration-services-server.md)  
  
  
