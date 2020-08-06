---
title: 安装 SharePoint 2013 Reporting Services SharePoint 模式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: b29d0f45-0068-4c84-bd7e-5b8a9cd1b538
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 9190f990503a66a088351323effa6c17695f9757
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591738"
---
# <a name="install-reporting-services-sharepoint-mode-for-sharepoint-2013"></a><span data-ttu-id="f1dc1-102">安装用于 SharePoint 2013 的 Reporting Services SharePoint 模式</span><span class="sxs-lookup"><span data-stu-id="f1dc1-102">Install Reporting Services SharePoint Mode for SharePoint 2013</span></span>
  <span data-ttu-id="f1dc1-103">本主题中的过程将指导您完成以 SharePoint 模式在单台服务器上安装 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-103">The procedures in this topic guide you through a single server installation of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint mode.</span></span> <span data-ttu-id="f1dc1-104">涉及的步骤包括运行 SQL Server 安装向导以及使用 SharePoint 管理中心的配置任务。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-104">The steps include running the SQL Server installation wizard as well as configuration tasks that use SharePoint Central Administration.</span></span> <span data-ttu-id="f1dc1-105">本主题还可用于更新现有安装的单独过程，例如创建 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务应用程序。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-105">The topic can also be used for individual procedures for updating an existing installation, for example to create a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application.</span></span>  
  
||  
|-|  
|<span data-ttu-id="f1dc1-106">**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013 &#124;**注意：** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sharepoint 模式不**not**支持 sharepoint Server 多租户。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 &#124; **Note:** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode does **not** support SharePoint Server multi-tenancy.</span></span>|  
  
 <span data-ttu-id="f1dc1-107">有关在现有场中添加更多 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务器的信息，请参阅以下内容：</span><span class="sxs-lookup"><span data-stu-id="f1dc1-107">For information on adding more [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] servers to an existing farm, see the following:</span></span>  
  
-   [<span data-ttu-id="f1dc1-108">向场中添加另一个报表服务器（SSRS 扩展）</span><span class="sxs-lookup"><span data-stu-id="f1dc1-108">Add an Additional Report Server to a Farm &#40;SSRS Scale-out&#41;</span></span>](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md)  
  
-   [<span data-ttu-id="f1dc1-109">向场中添加另一个 Reporting Services Web 前端</span><span class="sxs-lookup"><span data-stu-id="f1dc1-109">Add an Additional Reporting Services Web Front-end to a Farm</span></span>](../../reporting-services/install-windows/add-an-additional-reporting-services-web-front-end-to-a-farm.md)  
  
 <span data-ttu-id="f1dc1-110">单服务器安装对于开发和测试方案很有用，但不建议用于生产环境。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-110">A single server installation is useful for development and testing scenarios but it is not recommended for production environments.</span></span>  
  
 <span data-ttu-id="f1dc1-111">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="f1dc1-111">**In this topic:**</span></span>  
  
-   [<span data-ttu-id="f1dc1-112">单服务器部署示例</span><span class="sxs-lookup"><span data-stu-id="f1dc1-112">Example Single-Server Deployment</span></span>](#bkmk_singleserver)  
  
-   [<span data-ttu-id="f1dc1-113">设置帐户</span><span class="sxs-lookup"><span data-stu-id="f1dc1-113">Setup accounts</span></span>](#bkmk_setupaccounts)  
  
-   [<span data-ttu-id="f1dc1-114">步骤 1：在 SharePoint 模式下安装 Reporting Services 报表服务器</span><span class="sxs-lookup"><span data-stu-id="f1dc1-114">Step 1: Install Reporting Services Report Server in SharePoint mode</span></span>](#bkmk_install_SSRS)  
  
-   [<span data-ttu-id="f1dc1-115">步骤2：注册并启动 Reporting Services SharePoint 服务</span><span class="sxs-lookup"><span data-stu-id="f1dc1-115">Step 2: Register and Start the Reporting Services SharePoint Service</span></span>](#bkmk_install_SSRS_sharedservice)  
  
-   [<span data-ttu-id="f1dc1-116">步骤3：创建 Reporting Services 服务应用程序</span><span class="sxs-lookup"><span data-stu-id="f1dc1-116">Step 3: Create a Reporting Services Service Application</span></span>](#bkmk_create_serrviceapplication)  
  
-   [<span data-ttu-id="f1dc1-117">步骤4：激活 "Power View 网站集" 功能。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-117">Step 4: Activate the Power View Site Collection Feature.</span></span>](#bkmk_powerview)  
  
-   [<span data-ttu-id="f1dc1-118">用于步骤1-4 的 Windows PowerShell 脚本</span><span class="sxs-lookup"><span data-stu-id="f1dc1-118">Windows PowerShell script for Steps 1-4</span></span>](#bkmk_full_script)  
  
-   <span data-ttu-id="f1dc1-119">[Additional Configuration](#bkmk_additional_config) 包括订阅和警报、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 内容类型的配置，以及配置 Excel Services 以使用 Analysis Services 服务器。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-119">[Additional Configuration](#bkmk_additional_config) including provisioning for subscriptions and alerts, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] content types, and configuring Excel Services to Use an Analysis Services Server.</span></span>  
  
-   [<span data-ttu-id="f1dc1-120">验证安装</span><span class="sxs-lookup"><span data-stu-id="f1dc1-120">Verify the installation</span></span>](#bkmk_verify_installation)  
  
##  <a name="example-single-server-deployment"></a><a name="bkmk_singleserver"></a><span data-ttu-id="f1dc1-121">单服务器部署示例</span><span class="sxs-lookup"><span data-stu-id="f1dc1-121">Example Single-Server Deployment</span></span>  
 <span data-ttu-id="f1dc1-122">单服务器安装对于开发和测试方案很有用，但不建议将单服务器用于生产环境。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-122">A single-server installation is useful for development and testing scenarios but a single-server is not recommended for a production environment.</span></span> <span data-ttu-id="f1dc1-123">单服务器环境是指 SharePoint 和 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 组件安装在同一台计算机上的一台计算机。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-123">The single-server environment refers to a single computer that has SharePoint and [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] components installed on the same computer.</span></span> <span data-ttu-id="f1dc1-124">本主题不涉及具有多个 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务器的扩展环境。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-124">The topic does not cover scale-out with multiple [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] servers.</span></span>  
  
 <span data-ttu-id="f1dc1-125">以下关系图阐明了属于单服务器 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 部署的一部分的组件。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-125">The following diagram illustrates the components that are part of a single server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] deployment.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f1dc1-126">**(1)**</span><span class="sxs-lookup"><span data-stu-id="f1dc1-126">**(1)**</span></span>|<span data-ttu-id="f1dc1-127">从 SQL Server 安装安装的 SharePoint 服务。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-127">SharePoint service installed from SQL Server installation.</span></span> <span data-ttu-id="f1dc1-128">您可以创建一个或多个 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务应用程序。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-128">You can create one or more [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service applications.</span></span>|  
|<span data-ttu-id="f1dc1-129">\*\* (2) \*\*</span><span class="sxs-lookup"><span data-stu-id="f1dc1-129">**(2)**</span></span>|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="f1dc1-130">用于 SharePoint 产品的外接程序在 SharePoint 服务器上提供用户界面组件。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-130">add-in for SharePoint products provides the user interface components on the SharePoint Servers.</span></span>|  
|<span data-ttu-id="f1dc1-131">\*\* (3) \*\*</span><span class="sxs-lookup"><span data-stu-id="f1dc1-131">**(3)**</span></span>|<span data-ttu-id="f1dc1-132">供 Power View 和 PowerPivot 使用的 Excel Service 应用程序。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-132">The Excel Service Application used by Power View and PowerPivot.</span></span>|  
|<span data-ttu-id="f1dc1-133">\*\* (4) \*\*</span><span class="sxs-lookup"><span data-stu-id="f1dc1-133">**(4)**</span></span>|<span data-ttu-id="f1dc1-134">PowerPivot 服务应用程序。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-134">PowerPivot service application.</span></span>|  
  
 <span data-ttu-id="f1dc1-135">![SSRS SharePoint 模式单服务器部署](../../../2014/sql-server/install/media/rs-sharepoint-1server-deployment.gif "SSRS SharePoint 模式单服务器部署")</span><span class="sxs-lookup"><span data-stu-id="f1dc1-135">![SSRS SharePoint Mode Single Server Deployment](../../../2014/sql-server/install/media/rs-sharepoint-1server-deployment.gif "SSRS SharePoint Mode Single Server Deployment")</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="f1dc1-136"> 有关更复杂的部署示例，请参阅 [Deployment Topologies for SQL Server BI Features in SharePoint](deployment-topologies-for-sql-server-bi-features-in-sharepoint.md)。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-136">For more complex deployment examples, see [Deployment Topologies for SQL Server BI Features in SharePoint](deployment-topologies-for-sql-server-bi-features-in-sharepoint.md).</span></span>  
  
##  <a name="setup-accounts"></a><a name="bkmk_setupaccounts"></a><span data-ttu-id="f1dc1-137">设置帐户</span><span class="sxs-lookup"><span data-stu-id="f1dc1-137">Setup accounts</span></span>  
 <span data-ttu-id="f1dc1-138">本部分介绍在 SharePoint 模式下用于主要 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 部署步骤的帐户和权限。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-138">This section describes the accounts and permissions used for the primary deployment steps of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint mode.</span></span>  
  
 <span data-ttu-id="f1dc1-139">**安装并注册 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务：**</span><span class="sxs-lookup"><span data-stu-id="f1dc1-139">**Installation and registering the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Service:**</span></span>  
  
-   <span data-ttu-id="f1dc1-140">在 SharePoint 模式下，当前帐户 (称为 "安装" 帐户) [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 在 SharePoint 模式下，需要具有本地计算机的管理权限。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-140">The current account during the installation (referred to as the 'setup' account) of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint mode needs to have administrative rights in the local computer.</span></span> <span data-ttu-id="f1dc1-141">如果在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安装 sharepoint 后安装并且 "安装" 帐户也是 sharepoint 场管理员组的成员，则 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安装将 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 为您注册服务。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-141">If you are installing [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] after SharePoint is installed and the 'setup' account is also a member of the SharePoint farm administrators group, the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation will register the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service for you.</span></span> <span data-ttu-id="f1dc1-142">如果在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安装 SharePoint 之前安装或者 "安装" 帐户不是 "服务器场管理员" 组的成员，则手动注册该服务。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-142">If you install [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] before SharePoint is installed or the 'setup' account is not a member of the farm administrators group, you register the service manually.</span></span> <span data-ttu-id="f1dc1-143">请参见 [步骤 2：注册并启动 Reporting Services SharePoint 服务](#bkmk_install_SSRS_sharedservice)。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-143">See the section [Step 2: Register and Start the Reporting Services SharePoint Service](#bkmk_install_SSRS_sharedservice).</span></span>  
  
 <span data-ttu-id="f1dc1-144">**创建 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务应用程序**</span><span class="sxs-lookup"><span data-stu-id="f1dc1-144">**Creating [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Service Applications**</span></span>  
  
-   <span data-ttu-id="f1dc1-145">在安装并注册 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务后，创建一个或多个 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务应用程序。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-145">Following installation and registering the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service, create one or more [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service applications.</span></span> <span data-ttu-id="f1dc1-146">“SharePoint 场服务帐户”需要暂时成为本地管理员组的成员才能创建 Reporting Services 服务应用程序。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-146">The "SharePoint farm service account " needs to temporarily be a member of the local administrators group so the Reporting Services service application can be created.</span></span> <span data-ttu-id="f1dc1-147">有关 SharePoint 2013 帐户权限的详细信息，请参阅[sharepoint 2013 (中的帐户权限和安全设置](https://technet.microsoft.com/library/cc678863.aspx) https://technet.microsoft.com/library/cc678863.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-147">For more information on SharePoint 2013 account permissions, see [Account permissions and security settings in SharePoint 2013](https://technet.microsoft.com/library/cc678863.aspx) (https://technet.microsoft.com/library/cc678863.aspx).</span></span>  
  
     <span data-ttu-id="f1dc1-148">根据最佳安全做法，SharePoint 场管理员帐户不应同时作为本地操作系统管理员帐户。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-148">It is security best practice that SharePoint farm administrator accounts are not also local operating system administrator accounts.</span></span> <span data-ttu-id="f1dc1-149">如果您在安装过程中向本地管理员组中添加场管理员帐户，建议您在安装完成后从本地管理员组中删除该帐户。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-149">If you add a farm admin account to the local administrators group as part of your installation process, it is recommended you remove the account from the local administrators group after installation is complete.</span></span>  
  
##  <a name="step-1-install-reporting-services-report-server-in-sharepoint-mode"></a><a name="bkmk_install_SSRS"></a><span data-ttu-id="f1dc1-150">步骤1：在 SharePoint 模式下安装 Reporting Services 报表服务器</span><span class="sxs-lookup"><span data-stu-id="f1dc1-150">Step 1: Install Reporting Services Report Server in SharePoint mode</span></span>  
 <span data-ttu-id="f1dc1-151">此步骤在 SharePoint 模式下安装 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 报表服务器以及用于 SharePoint 产品的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 外接程序。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-151">This step installs a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server in SharePoint mode and the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in for SharePoint products.</span></span> <span data-ttu-id="f1dc1-152">根据已在您的计算机上安装的项，您可能不会看到在下面的步骤中介绍的某些安装页。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-152">Depending on what is already installed on your computer, you may not see some of the installation pages described in the following steps.</span></span>  
  
1.  <span data-ttu-id="f1dc1-153">运行 SQL Server 安装向导 (Setup.exe)。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-153">Run the SQL Server Installation Wizard (Setup.exe).</span></span>  
  
2.  <span data-ttu-id="f1dc1-154">在向导的左侧单击 **“安装”** ，然后单击 **“全新 SQL Server 独立安装或向现有安装添加功能”**。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-154">Click **Installation** in the left side of the wizard and then click **New SQL Server stand-alone installation or add features to an existing installation**.</span></span>  
  
3.  <span data-ttu-id="f1dc1-155">在 **“安装程序支持规则”** 页上单击 **“确定”** ，假定所有规则均已通过验证。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-155">Click **OK** on the **Setup Support Rules** page, assuming all rules passed.</span></span>  
  
4.  <span data-ttu-id="f1dc1-156">在 **“安装程序支持文件”** 页中，单击 **“安装”** 。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-156">Click **Install** on the **Setup Support Files** page.</span></span> <span data-ttu-id="f1dc1-157">根据已在您的计算机上安装的项，您可能会看到以下消息：</span><span class="sxs-lookup"><span data-stu-id="f1dc1-157">Depending on what is already installed on your computer, you might see the following message:</span></span>  
  
    -   <span data-ttu-id="f1dc1-158">“一个或多个受影响的文件具有挂起的操作。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-158">"One or more affected files have operations pending.</span></span> <span data-ttu-id="f1dc1-159">安装过程完成后，必须重新启动计算机。”</span><span class="sxs-lookup"><span data-stu-id="f1dc1-159">You must restart your computer after the setup process is completed."</span></span>  
  
    -   <span data-ttu-id="f1dc1-160">单击“确定” 。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-160">Click **Ok**.</span></span>  
  
5.  <span data-ttu-id="f1dc1-161">在支持文件已完成安装并且 **“支持规则”** 页显示 **“已通过”** 状态后，单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-161">Click **Next** after the support files have completed installing and the **Support Rules** pages show a status of **Passed**.</span></span> <span data-ttu-id="f1dc1-162">查看任何警告或妨碍安装的问题。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-162">Review any warnings or blocking issues.</span></span>  
  
6.  <span data-ttu-id="f1dc1-163">在“安装类型” \*\*\*\* 页上，单击“向 SQL Server 2014 的现有实例中添加功能” \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-163">On the **Installation Type** page, click **Add features to an existing instance of SQL Server 2014**.</span></span> <span data-ttu-id="f1dc1-164">在下拉列表中选择正确实例，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-164">Select the correct instance in the drop-down list and click **Next**.</span></span>  
  
7.  <span data-ttu-id="f1dc1-165">如果看到 "**产品密钥**" 页，请键入密钥或接受默认的 "企业评估版"。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-165">If you see the **Product Key** page, type your key or accept the default of the 'Enterprise Evaluation' edition.</span></span>  
  
     <span data-ttu-id="f1dc1-166">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-166">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="f1dc1-167">如果您看到许可条款页，则查看并接受许可条款。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-167">If you see the License terms page, review and accept the license terms.</span></span> <span data-ttu-id="f1dc1-168">对于您单击以同意发送功能使用情况数据来帮助改进产品功能和支持，Microsoft 深表感谢。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-168">Microsoft appreciates you clicking to agree to send feature usage data to help improve product features and support.</span></span>  
  
     <span data-ttu-id="f1dc1-169">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-169">Click **Next**.</span></span>  
  
9. <span data-ttu-id="f1dc1-170">如果您看到 **“安装角色”** 页，则选择 **“SQL Server 功能安装”**。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-170">If you see the **Setup Role** page, select **SQL Server Feature Installation**</span></span>  
  
     <span data-ttu-id="f1dc1-171">点击“下一步”</span><span class="sxs-lookup"><span data-stu-id="f1dc1-171">Click **Next**</span></span>  
  
     <span data-ttu-id="f1dc1-172">![安装角色的 SQL Server 功能安装](../../../2014/sql-server/install/media/rs-setuprole.gif "安装角色的 SQL Server 功能安装")</span><span class="sxs-lookup"><span data-stu-id="f1dc1-172">![SQL Server Feature Installation for setup role](../../../2014/sql-server/install/media/rs-setuprole.gif "SQL Server Feature Installation for setup role")</span></span>  
  
10. <span data-ttu-id="f1dc1-173">在 **“功能选择”** 页中，选择以下选项：</span><span class="sxs-lookup"><span data-stu-id="f1dc1-173">Select the following on the **Feature Selection** page:</span></span>  
  
    -   <span data-ttu-id="f1dc1-174">**Reporting Services-SharePoint**</span><span class="sxs-lookup"><span data-stu-id="f1dc1-174">**Reporting Services - SharePoint**</span></span>  
  
    -   <span data-ttu-id="f1dc1-175">**Reporting Services 用于 SharePoint 产品的外接程序**。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-175">**Reporting Services add-in for SharePoint Products**.</span></span>  
  
         <span data-ttu-id="f1dc1-176">![注意](../../../2014/reporting-services/media/rs-fyinote.png "注意")用于安装外接程序的安装向导选项是版本的新 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 版本。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-176">![note](../../../2014/reporting-services/media/rs-fyinote.png "note") The installation wizard option for installing the add-in is new with the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] release.</span></span>  
  
    -   <span data-ttu-id="f1dc1-177">如果您尚未安装 SQL Server [!INCLUDE[ssDE](../../includes/ssde-md.md)]实例，则还可以选择 **“数据库引擎服务”** 和 **“管理工具 - 完整”** 以提供一个完整环境。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-177">If you do not already have an instance of SQL Server [!INCLUDE[ssDE](../../includes/ssde-md.md)], you could also select **Database Engine Services** and **Management Tools Complete** for a complete environment.</span></span>  
  
     <span data-ttu-id="f1dc1-178">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-178">Click **Next**.</span></span>  
  
     <span data-ttu-id="f1dc1-179">![SharePoint 模式的 SSRS 功能选择](../../../2014/sql-server/install/media/rs-setupfeatureselection-sharepoint-with-circles.gif "SharePoint 模式的 SSRS 功能选择")</span><span class="sxs-lookup"><span data-stu-id="f1dc1-179">![SSRS Feature Selection for SharePoint mode](../../../2014/sql-server/install/media/rs-setupfeatureselection-sharepoint-with-circles.gif "SSRS Feature Selection for SharePoint mode")</span></span>  
  
11. <span data-ttu-id="f1dc1-180">如果您看到 **“安装规则”** 页。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-180">If you see the **Installation Rules** page.</span></span> <span data-ttu-id="f1dc1-181">查看任何警告或妨碍安装的问题。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-181">Review any warnings or blocking issues.</span></span> <span data-ttu-id="f1dc1-182">然后单击“下一步” </span><span class="sxs-lookup"><span data-stu-id="f1dc1-182">Then click **Next**</span></span>  
  
12. <span data-ttu-id="f1dc1-183">如果您已选择“数据库引擎服务”，请在 **“实例配置”** 页上接受 **MSSQLSERVER** 的默认实例，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-183">If you selected the Database Engine services, accept the default instance of **MSSQLSERVER** on the **Instance Configuration** page and click **Next**.</span></span>  
  
     <span data-ttu-id="f1dc1-184">![请注意](../../../2014/reporting-services/media/rs-fyinote.png "注意")与以前的 Reporting Services 体系结构一样，Reporting Services SharePoint 服务体系结构不基于 SQL Server“实例”。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-184">![note](../../../2014/reporting-services/media/rs-fyinote.png "note")The Reporting Services SharePoint service architecture is not based on a SQL Server "instance" as was the previous Reporting Services architecture.</span></span>  
  
13. <span data-ttu-id="f1dc1-185">阅读 **“磁盘空间要求”** 页，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-185">Review the **Disk Space Requirements** page and click **Next**.</span></span>  
  
14. <span data-ttu-id="f1dc1-186">如果您看到 **“服务器配置”** 页，则键入相应的凭据。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-186">If you see the **Server Configuration** page type appropriate credentials.</span></span> <span data-ttu-id="f1dc1-187">如果您要使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 数据警报或订阅功能，则需要将 SQL Server 代理的 **“启动类型”** 更改为 **“自动”**。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-187">If you want to use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] data alerting or subscription features, you need to change the **Startup Type** for SQL Server Agent to **Automatic**.</span></span> <span data-ttu-id="f1dc1-188">根据已在计算机上安装的项，您可能不会看到 **“服务器配置”** 页。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-188">You may not see the **Server Configuration** page, depending on what is already installed on the computer.</span></span>  
  
     <span data-ttu-id="f1dc1-189">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-189">Click **Next**.</span></span>  
  
15. <span data-ttu-id="f1dc1-190">如果您选择了“数据库引擎服务”，您将看到 **“数据库引擎配置”** 页。请将相应的帐户添加到 SQL 管理员列表，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-190">If you selected the Database Engine services, you will see the **Database Engine Configuration** page, add appropriate accounts to the list of SQL Administrators and click **Next**.</span></span>  
  
16. <span data-ttu-id="f1dc1-191">在 **“Reporting Services 配置”** 页上，您应该看到 **“仅安装”** 选项处于选中状态。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-191">On the **Reporting Services Configuration** page you should see the **Install only** option is selected.</span></span> <span data-ttu-id="f1dc1-192">此选项将安装报表服务器文件，但不会为 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]配置 SharePoint 环境。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-192">This option installs the report server files, and does not configure the SharePoint environment for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f1dc1-193">SQL Server 安装完成后，您需要按照本主题的其他章节的内容配置 SharePoint 环境。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-193">When the SQL Server installation is complete, follow the other sections of this topic to configure the SharePoint environment.</span></span> <span data-ttu-id="f1dc1-194">这包括安装 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 共享服务和创建 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务应用程序。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-194">This Includes installing the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] shared service and creating [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service applications.</span></span>  
  
     <span data-ttu-id="f1dc1-195">![SQL Server 安装向导 -“SSRS 配置”页](../../../2014/sql-server/install/media/rs-2012sp1-setup-ssrs-configpage-with-circles.gif "SQL Server 安装向导 -“SSRS 配置”页")</span><span class="sxs-lookup"><span data-stu-id="f1dc1-195">![SQL Server Setup Wizard - SSRS Configuration Page](../../../2014/sql-server/install/media/rs-2012sp1-setup-ssrs-configpage-with-circles.gif "SQL Server Setup Wizard - SSRS Configuration Page")</span></span>  
  
17. <span data-ttu-id="f1dc1-196">请通过在 **“错误报告”** 页上单击用于发送错误报告的复选框，来帮助 Microsoft 改进 SQL Server 功能和服务。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-196">Help Microsoft improve SQL Server features and services by clicking the check box to send error reports on the **Error Reporting** page.</span></span>  
  
     <span data-ttu-id="f1dc1-197">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-197">Click **Next**.</span></span>  
  
18. <span data-ttu-id="f1dc1-198">查看任何警告，然后在 **“安装配置规则”** 页上单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-198">Review any warnings and then click **Next** on the **Installation Configuration Rules** page.</span></span>  
  
19. <span data-ttu-id="f1dc1-199">在 **“准备安装”** 页上，查看安装摘要，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-199">On the **Ready to Install** page, review the installation summary and then click **Next**.</span></span> <span data-ttu-id="f1dc1-200">该摘要将包含一个 **“Reporting Services SharePoint 模式”** 子节点，该节点将显示 **SharePointFilesOnlyMode**的值。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-200">The summary will include a **Reporting Services SharePoint Mode** child node that will show a value of **SharePointFilesOnlyMode**.</span></span> <span data-ttu-id="f1dc1-201">单击“安装”  。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-201">Click **Install**.</span></span>  
  
20. <span data-ttu-id="f1dc1-202">安装将需要几分钟时间。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-202">The installation will take several minutes.</span></span> <span data-ttu-id="f1dc1-203">您将看到 **“完成”** 页，其中列出了功能以及各功能的状态。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-203">You will see the **Complete** page with the features listed and the status of each feature.</span></span> <span data-ttu-id="f1dc1-204">您可能会看到一个信息对话框，指示计算机需要重新启动。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-204">You may see an information dialog indicating the computer needs to be restarted.</span></span>  
  
##  <a name="step-2-register-and-start-the-reporting-services-sharepoint-service"></a><a name="bkmk_install_SSRS_sharedservice"></a><span data-ttu-id="f1dc1-205">步骤2：注册并启动 Reporting Services SharePoint 服务</span><span class="sxs-lookup"><span data-stu-id="f1dc1-205">Step 2: Register and Start the Reporting Services SharePoint Service</span></span>  
 <span data-ttu-id="f1dc1-206">![PowerShell 相关内容](../../../2014/reporting-services/media/rs-powershellicon.jpg "PowerShell 相关内容")</span><span class="sxs-lookup"><span data-stu-id="f1dc1-206">![PowerShell related content](../../../2014/reporting-services/media/rs-powershellicon.jpg "PowerShell related content")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f1dc1-207">如果您要安装到现有 SharePoint 场，则不需要完成本节中的步骤。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-207">If you are installing into an existing SharePoint farm, you do not need to complete the steps in this section.</span></span> <span data-ttu-id="f1dc1-208">当您在本文档的上一节中运行 SQL Server 安装向导时，就已经安装并启动了 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 服务。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-208">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint service is installed and started when you ran the SQL Server installation wizard as part of the previous section of this document.</span></span>  
  
 <span data-ttu-id="f1dc1-209">下面是您需要手动注册 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务的常见原因。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-209">The following are the common reasons why you need to manually register the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service.</span></span>  
  
-   <span data-ttu-id="f1dc1-210">在安装 SharePoint 之前已安装 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-210">You installed [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode before SharePoint was installed.</span></span>  
  
-   <span data-ttu-id="f1dc1-211">用于安装 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式的帐户不是 SharePoint 场管理员组的成员。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-211">The account used to install [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode, was not a member of the SharePoint farm administrators group.</span></span> <span data-ttu-id="f1dc1-212">有关详细信息，请参阅[安装帐户](#bkmk_setupaccounts)部分。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-212">For more information, see the section [Setup accounts](#bkmk_setupaccounts).</span></span>  
  
 <span data-ttu-id="f1dc1-213">在执行 SQL Server 安装向导的过程中已安装了必需的文件，但需要将服务注册到 SharePoint 场中。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-213">The necessary files were installed as part of the SQL Server installation wizard, but the services need to be registered into the SharePoint farm.</span></span> <span data-ttu-id="f1dc1-214">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 版本引入了对 SharePoint 模式下的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的 PowerShell 支持。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-214">The [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] release introduces PowerShell support for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint mode.</span></span>  
  
 <span data-ttu-id="f1dc1-215">以下步骤将指导您完成打开 SharePoint Management Shell 并运行 cmdlet 的过程：</span><span class="sxs-lookup"><span data-stu-id="f1dc1-215">The following steps guide you through opening the SharePoint Management Shell and running cmdlets:</span></span>  
  
1.  <span data-ttu-id="f1dc1-216">单击 **“开始”** 按钮</span><span class="sxs-lookup"><span data-stu-id="f1dc1-216">Click the **Start** button</span></span>  
  
2.  <span data-ttu-id="f1dc1-217">单击 **“Microsoft SharePoint 2013 产品”** 组。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-217">Click the **Microsoft SharePoint 2013 Products** group.</span></span>  
  
3.  <span data-ttu-id="f1dc1-218">右键单击 **SharePoint 2013 Management Shell** ，然后单击 **“以管理员身份运行”**。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-218">Right-click **SharePoint 2013 Management Shell** click **Run as administrator**.</span></span> <span data-ttu-id="f1dc1-219">注意：在标准 Windows PowerShell 窗口中无法识别 SharePoint 命令。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-219">NOTE: the SharePoint commands are not recognized in the standard Windows PowerShell window.</span></span> <span data-ttu-id="f1dc1-220">请使用 **SharePoint 2013 Management Shell**。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-220">Use the **SharePoint 2013 Management Shell**.</span></span>  
  
4.  <span data-ttu-id="f1dc1-221">运行以下 PowerShell 命令以安装 SharePoint 服务。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-221">Run the following PowerShell command to install the SharePoint service.</span></span> <span data-ttu-id="f1dc1-222">命令成功完成后会在 Management Shell 中显示一个新行。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-222">A successful completion of the command displays a new line in the management shell.</span></span> <span data-ttu-id="f1dc1-223">命令成功完成时，**不会将消息返回**到命令行管理程序：</span><span class="sxs-lookup"><span data-stu-id="f1dc1-223">**No message is returned** to the management shell when the command completes successfully:</span></span>  
  
    ```powershell
    Install-SPRSService  
    ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="f1dc1-224">如果您看到与以下内容类似的错误消息：</span><span class="sxs-lookup"><span data-stu-id="f1dc1-224">If you see an error message similar to the following:</span></span>  
    >   
    >  <span data-ttu-id="f1dc1-225">Install-sprsserviceinstall-sprsservice：术语 "Install-Install-sprsserviceinstall-sprsservice"**未被识别**为</span><span class="sxs-lookup"><span data-stu-id="f1dc1-225">Install-SPRSService : The term 'Install-SPRSService' **is not recognized** as the</span></span>  
    > <span data-ttu-id="f1dc1-226">cmdlet、函数、脚本文件或可运行程序的名称。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-226">name of a cmdlet, function, script file, or operable program.</span></span> <span data-ttu-id="f1dc1-227">检查</span><span class="sxs-lookup"><span data-stu-id="f1dc1-227">Check the</span></span>  
    > <span data-ttu-id="f1dc1-228">名称的拼写，如果包括路径，请确保路径正确，</span><span class="sxs-lookup"><span data-stu-id="f1dc1-228">spelling of the name, or if a path was included, verify that the path is</span></span>  
    > <span data-ttu-id="f1dc1-229">然后重试。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-229">correct and try again.</span></span>  
  
5.  <span data-ttu-id="f1dc1-230">运行以下 PowerShell 命令以安装服务代理。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-230">Run the following PowerShell command to install the service proxy.</span></span> <span data-ttu-id="f1dc1-231">命令成功完成后会在 Management Shell 中显示一个新行。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-231">A successful completion of the command displays a new line in the management shell.</span></span> <span data-ttu-id="f1dc1-232">命令成功完成时，**不会将消息返回**到命令行管理程序：</span><span class="sxs-lookup"><span data-stu-id="f1dc1-232">**No message is returned** to the management shell when the command completes successfully:</span></span>  
  
    ```powershell
    Install-SPRSServiceProxy  
    ```  
  
6.  <span data-ttu-id="f1dc1-233">运行以下 PowerShell 命令以启动服务，或者查看下面的注释以了解有关从 SharePoint 管理中心启动服务的说明：</span><span class="sxs-lookup"><span data-stu-id="f1dc1-233">Run the following PowerShell command to start the service or see the following notes for instructions on how to start the service from SharePoint Central administration:</span></span>  
  
    ```powershell
    Get-SPServiceInstance -all |where {$_.TypeName -like "SQL Server Reporting*"} | Start-SPServiceInstance  
    ```  
  
 <span data-ttu-id="f1dc1-234">您在 Windows Powershell 中而不是 SharePoint Management Shell 中，或尚未安装 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-234">Either you are in the Windows Powershell instead of the SharePoint Management Shell  or [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode is not installed.</span></span> <span data-ttu-id="f1dc1-235">有关 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 和PowerShell 的详细信息，请参阅 [用于 Reporting Services SharePoint 模式的 PowerShell cmdlet](../../../2014/reporting-services/powershell-cmdlets-for-reporting-services-sharepoint-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-235">For more information on [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] and PowerShell, see [PowerShell cmdlets for Reporting Services SharePoint Mode](../../../2014/reporting-services/powershell-cmdlets-for-reporting-services-sharepoint-mode.md).</span></span>  
  
 <span data-ttu-id="f1dc1-236">您也可以通过 SharePoint 管理中心（而不是通过运行第三个 PowerShell 命令）来启动服务。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-236">You can also start the service from SharePoint central Administration rather than running the third PowerShell command.</span></span> <span data-ttu-id="f1dc1-237">以下步骤还用于验证服务是否正在运行。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-237">The following steps are also useful to verify that the service is running.</span></span>  
  
1.  <span data-ttu-id="f1dc1-238">在 SharePoint 管理中心的 **“系统设置”** 组中，单击 **“管理服务器上的服务”** 。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-238">In SharePoint Central Administration, click **Manage Services on Server** in the **System Settings** group.</span></span>  
  
2.  <span data-ttu-id="f1dc1-239">找到 **“SQL Server Reporting Services 服务”** ，然后在“操作”列中单击 **“启动”** 。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-239">Find **SQL Server Reporting Services Service** and click **Start** in the Action column.</span></span>  
  
3.  <span data-ttu-id="f1dc1-240">Reporting Services 服务的状态将从 **“已停止”** 更改为 **“已启动”**。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-240">The status of the Reporting Services service will change from **Stopped** to **Started**.</span></span> <span data-ttu-id="f1dc1-241">如果 Reporting Services 服务不在列表中，则使用 PowerShell 安装该服务。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-241">If the Reporting Services service is not in the list, use PowerShell to install the service.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f1dc1-242">如果 Reporting Services 服务仍处于 "**正在启动**" 状态，并且未更改为 "**已启动**"，请验证 Windows 服务器管理器中的 "SharePoint 2013 管理" 服务是否已启动。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-242">If the Reporting Services service stays in the **Starting** status and does not change to **Started**, verify the 'SharePoint 2013 Administration' service is started in Windows Server Manager.</span></span>  
  
##  <a name="step-3-create-a-reporting-services-service-application"></a><a name="bkmk_create_serrviceapplication"></a><span data-ttu-id="f1dc1-243">步骤3：创建 Reporting Services 服务应用程序</span><span class="sxs-lookup"><span data-stu-id="f1dc1-243">Step 3: Create a Reporting Services Service Application</span></span>  
 <span data-ttu-id="f1dc1-244">本节提供您在查看现有服务应用程序的情况下，用于创建服务应用程序的步骤和属性说明。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-244">This section provides the steps to create a service application and a description of the properties, if you are reviewing an existing service application.</span></span>  
  
1.  <span data-ttu-id="f1dc1-245">在 SharePoint 管理中心的 "**应用程序管理**" 组中，单击 "**管理服务应用程序**"。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-245">In SharePoint Central Administration, in the **Application Management** group, click **Manage Service Applications**.</span></span>  
  
2.  <span data-ttu-id="f1dc1-246">在 SharePoint 功能区中，单击 **“新建”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-246">In the SharePoint ribbon, click the **New** button.</span></span>  
  
3.  <span data-ttu-id="f1dc1-247">在“新建”菜单中，单击 **“SQL Server Reporting Services 服务应用程序”**。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-247">In the New menu, click **SQL Server Reporting Services Service Application.**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="f1dc1-248">如果该 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 选项未显示在列表中，则**表明 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 共享服务未安装**。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-248">If the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] option does not appear in the list, it is an **indication that the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] shared service is not installed**.</span></span> <span data-ttu-id="f1dc1-249">查看上一节，了解如何使用 PowerShell cmdlt 安装 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-249">Review the previous section on how to use PowerShell cmdlts to install the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service.</span></span>  
  
4.  <span data-ttu-id="f1dc1-250">在 **“创建 SQL Server Reporting Services 服务应用程序”** 页中，输入应用程序的名称。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-250">In the **Create SQL Server Reporting Services Service Application** page, enter a name for the application.</span></span> <span data-ttu-id="f1dc1-251">如果您要创建多个 Reporting Services 服务应用程序，则一个描述性名称或命名约定将帮助您组织管理操作。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-251">If you are creating multiple Reporting Services service applications, a descriptive name or naming convention will help you organize your administration and management operations.</span></span>  
  
5.  <span data-ttu-id="f1dc1-252">在 **“应用程序池”** 部分中，为该应用程序创建一个新应用程序池（推荐）。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-252">In **Application Pool** section, create a new application pool for the application (recommended).</span></span> <span data-ttu-id="f1dc1-253">如果您将相同的名称用于应用程序池和服务应用程序，则可能会使您正在进行的管理更加容易。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-253">If you use the same name for both the application pool and the services application, it can make ongoing administration easier.</span></span> <span data-ttu-id="f1dc1-254">这可能还会受到您将创建的服务应用程序的数目以及是否需要在单个应用程序池中使用若干应用程序的影响。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-254">This can also be affected by how many service applications you will create and if you need to use several in a single application pool.</span></span> <span data-ttu-id="f1dc1-255">请参阅 SharePoint Server 文档，了解有关应用程序池管理的建议和最佳做法。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-255">See the SharePoint Server documentation on recommendations and best practices for application pool management.</span></span>  
  
     <span data-ttu-id="f1dc1-256">为该应用程序池选择或创建一个安全帐户。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-256">Select or create a security account for the application pool.</span></span> <span data-ttu-id="f1dc1-257">请确保指定一个域用户帐户。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-257">Be sure to specify a domain user account.</span></span> <span data-ttu-id="f1dc1-258">通过域用户帐户，可以使用 SharePoint 的托管帐户功能，从而使您可以在一个位置中更新密码和帐户信息。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-258">A domain user account enables the use of the SharePoint managed account feature, which lets you update passwords and account information in one place.</span></span> <span data-ttu-id="f1dc1-259">如果您计划扩展部署以便包括将在同一标识下运行的附加服务实例，则域帐户也是必需的。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-259">Domain accounts are also required if you plan to scale out the deployment to include additional service instances that run under the same identity.</span></span>  
  
6.  <span data-ttu-id="f1dc1-260">在 **“数据库服务器”** 中，您可以使用当前服务器或选择其他 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-260">In the **Database Server**, you can use the current server or choose a different SQL Server.</span></span>  
  
7.  <span data-ttu-id="f1dc1-261">在 **“数据库名称”** 中，默认值是 `ReportingService_<guid>`，这是唯一的数据库名称。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-261">In **Database Name** the default value is `ReportingService_<guid>`, which is a unique database name.</span></span> <span data-ttu-id="f1dc1-262">如果您键入一个新值，请键入唯一值。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-262">If you type a new value, type a unique value.</span></span> <span data-ttu-id="f1dc1-263">这是您要专为服务应用程序创建的新数据库。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-263">This is the new database to be created specifically for the services application.</span></span>  
  
8.  <span data-ttu-id="f1dc1-264">在 **“数据库身份验证”** 中，默认值是 “Windows 身份验证”。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-264">In **Database Authentication**, the default is Windows Authentication.</span></span> <span data-ttu-id="f1dc1-265">如果您选择 **“SQL 身份验证”**，请参阅 SharePoint 文档以便了解有关如何在 SharePoint 部署中使用此身份验证类型的最佳做法。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-265">If you choose **SQL Authentication**, refer to SharePoint documentation for best practices on how to use this authentication type in a SharePoint deployment.</span></span>  
  
9. <span data-ttu-id="f1dc1-266">在 **“Web 应用程序关联”** 部分中，选择要设置为供当前 Reporting Services 服务应用程序访问的 Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-266">In the **Web Application Association** section, select the Web Application to be provisioned for access by the current Reporting Services Service Application.</span></span> <span data-ttu-id="f1dc1-267">可以将一个 Reporting Services 服务应用程序与一个 Web 应用程序相关联。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-267">You can associate one Reporting Services service application to one web application.</span></span> <span data-ttu-id="f1dc1-268">如果所有当前 Web 应用程序均已与一个 Reporting Services 服务应用程序相关联，将显示警告消息。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-268">If all of the current web applications are already associated with a Reporting Services service application, you see a warning message.</span></span>  
  
10. <span data-ttu-id="f1dc1-269">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-269">Click **OK**.</span></span>  
  
11. <span data-ttu-id="f1dc1-270">用于创建服务应用程序的过程可能会需要几分钟才能完成。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-270">The process to create a service application could take several minutes to complete.</span></span> <span data-ttu-id="f1dc1-271">当它完成时，将显示确认消息和一个指向 **“设置订阅和警报”** 页的链接。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-271">When it is complete, you will see a confirmation message and a link to a **Provision Subscriptions and Alerts** page.</span></span> <span data-ttu-id="f1dc1-272">如果您要使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 订阅功能或数据警报功能，则完成该设置步骤。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-272">Complete the provision step if you want to use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] subscriptions feature or the data alerts feature.</span></span> <span data-ttu-id="f1dc1-273">有关详细信息，请参阅[用于 SSRS 服务应用程序的设置订阅和警报](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-273">For more information, see [Provision Subscriptions and Alerts for SSRS Service Applications](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md).</span></span>  
  
 <span data-ttu-id="f1dc1-274">![与 PowerShell 相关的内容](../../../2014/reporting-services/media/rs-powershellicon.jpg "PowerShell 相关内容")有关使用 PowerShell 创建 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务应用程序的信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="f1dc1-274">![PowerShell related content](../../../2014/reporting-services/media/rs-powershellicon.jpg "PowerShell related content") For information on using PowerShell to create a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application, see:</span></span>  
  
-   <span data-ttu-id="f1dc1-275">有关步骤1-4，请参阅以下部分： [Windows PowerShell 脚本](#bkmk_full_script)。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-275">See the following section [Windows PowerShell script for Steps 1-4](#bkmk_full_script).</span></span>  
  
-   <span data-ttu-id="f1dc1-276">主题 [使用 PowerShell 创建 Reporting Services 服务应用程序](../../../2014/reporting-services/reporting-services-sharepoint-service-and-service-applications.md#bkmk_powershell_create_ssrs_serviceapp)。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-276">Topic [To create a Reporting Services Service Application using PowerShell](../../../2014/reporting-services/reporting-services-sharepoint-service-and-service-applications.md#bkmk_powershell_create_ssrs_serviceapp).</span></span>  
  
##  <a name="step-4-activate-the-power-view-site-collection-feature"></a><a name="bkmk_powerview"></a><span data-ttu-id="f1dc1-277">步骤4：激活 "Power View 网站集" 功能。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-277">Step 4: Activate the Power View Site Collection Feature.</span></span>  
 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]<span data-ttu-id="f1dc1-278">（用于 [!INCLUDE[msCoName](../../includes/msconame-md.md)] SharePoint 产品的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 外接程序的一个功能）是一个网站集功能。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-278">, a feature of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in for [!INCLUDE[msCoName](../../includes/msconame-md.md)] SharePoint Products, is a site collection feature.</span></span> <span data-ttu-id="f1dc1-279">自动为根网站集和安装 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 外接程序后创建的网站集激活该功能。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-279">The feature is activated automatically for root site collections and site collections created after the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in is installed.</span></span> <span data-ttu-id="f1dc1-280">如果您计划使用 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]，请验证已激活该功能。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-280">If you plan to use [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], verify that the feature is activated.</span></span>  
  
 <span data-ttu-id="f1dc1-281">如果在安装 SharePoint Server 后安装了用于 SharePoint 产品的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 外接程序，则仅对根网站集激活报表服务器集成功能和 Power View 集成功能。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-281">If you install the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in for SharePoint Products after the installation of the SharePoint Server, then the Report Server integration feature and the Power View integration feature will only be activated for root site collections.</span></span> <span data-ttu-id="f1dc1-282">对于其他网站集，请手动激活这些功能。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-282">For other site collections, manually activate the features.</span></span>  
  
#### <a name="to-activate-or-verify-the-power-view-site-collection-feature"></a><span data-ttu-id="f1dc1-283">激活或验证 Power View 网站集功能</span><span class="sxs-lookup"><span data-stu-id="f1dc1-283">To Activate or Verify the Power View Site Collection Feature</span></span>  
  
1.  <span data-ttu-id="f1dc1-284">下面的步骤假定您为 2013 **“体验版本”** 配置了您的 SharePoint 站点。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-284">The following steps assume your SharePoint site is configured for the 2013 **experience version**.</span></span>  
  
     <span data-ttu-id="f1dc1-285">打开浏览器找到所需的 SharePoint 网站。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-285">Open your browser to the desired SharePoint site.</span></span> <span data-ttu-id="f1dc1-286">例如 http:// \<servername> /sites/bi</span><span class="sxs-lookup"><span data-stu-id="f1dc1-286">For example http://\<servername>/sites/bi</span></span>  
  
2.  <span data-ttu-id="f1dc1-287">单击 "**设置**" "![SharePoint 设置](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint 设置")"。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-287">Click **Settings**![SharePoint Settings](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint Settings").</span></span>  
  
3.  <span data-ttu-id="f1dc1-288">单击 "**站点设置**"。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-288">Click **Site settings**.</span></span>  
  
4.  <span data-ttu-id="f1dc1-289">在 **“网站集管理”** 组中，单击 **“网站集功能”**。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-289">In the **Site Collection Administration** group Click **Site collection features**.</span></span>  
  
5.  <span data-ttu-id="f1dc1-290">在列表中找到 **“Power View 集成功能”** 。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-290">Find **Power View Integration Feature** in the list.</span></span>  
  
6.  <span data-ttu-id="f1dc1-291">单击“激活”  。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-291">Click **Activate**.</span></span> <span data-ttu-id="f1dc1-292">功能状态将更改为 **“活动”**。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-292">The feature status will change to **Active**.</span></span>  
  
 <span data-ttu-id="f1dc1-293">将对每个网站集完成此过程。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-293">This procedure is completed per site collection.</span></span> <span data-ttu-id="f1dc1-294">有关详细信息，请参阅 [在 SharePoint 中激活报表服务器和 Power View 集成功能](../../../2014/reporting-services/activate-the-report-server-and-power-view-integration-features-in-sharepoint.md)。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-294">For more information, see [Activate the Report Server and Power View Integration Features in SharePoint](../../../2014/reporting-services/activate-the-report-server-and-power-view-integration-features-in-sharepoint.md).</span></span>  
  
##  <a name="windows-powershell-script-for-steps-1-4"></a><a name="bkmk_full_script"></a><span data-ttu-id="f1dc1-295">用于步骤1-4 的 Windows PowerShell 脚本</span><span class="sxs-lookup"><span data-stu-id="f1dc1-295">Windows PowerShell script for Steps 1-4</span></span>  
 <span data-ttu-id="f1dc1-296">本节中的 PowerShells 脚本等同于完成前面几节中的步骤 1 - 4。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-296">The PowerShells script in this section are the equivalent of completing steps 1 to 4 in the previous sections.</span></span> <span data-ttu-id="f1dc1-297">此脚本将完成以下操作：</span><span class="sxs-lookup"><span data-stu-id="f1dc1-297">The script completes the following:</span></span>  
  
-   <span data-ttu-id="f1dc1-298">安装 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务和服务代理，然后启动该服务。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-298">Installs [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service and service proxy, and starts the service.</span></span>  
  
-   <span data-ttu-id="f1dc1-299">创建名为“Reporting Services”的服务代理。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-299">Creates a service proxy named "Reporting Services".</span></span>  
  
-   <span data-ttu-id="f1dc1-300">创建 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 名为 "Reporting Services 应用程序" 的服务应用程序。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-300">Creates a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application named "Reporting Services Application".</span></span>  
  
-   <span data-ttu-id="f1dc1-301">启用网站集的 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] 功能。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-301">Enables the [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] feature for a site collection.</span></span>  
  
 <span data-ttu-id="f1dc1-302">参数</span><span class="sxs-lookup"><span data-stu-id="f1dc1-302">Parameters</span></span>  
  
-   <span data-ttu-id="f1dc1-303">更新服务代理的 **-Account** 。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-303">Update the **-Account** for the service proxy.</span></span> <span data-ttu-id="f1dc1-304">该帐户在 SharePoint 场中必须是一个托管服务帐户。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-304">The account needs to be a managed service account in the SharePoint farm.</span></span> <span data-ttu-id="f1dc1-305">有关详细信息，请参阅 SharePoint 主题 [规划 SharePoint 2013 中的管理和服务帐户](https://technet.microsoft.com/library/cc263445.aspx)。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-305">For more information, see the SharePoint topic [Plan for administrative and service accounts in SharePoint 2013](https://technet.microsoft.com/library/cc263445.aspx).</span></span>  
  
-   <span data-ttu-id="f1dc1-306">更新服务应用程序的 **-DatabaseServer**参数。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-306">Update the **-DatabaseServer** parameter for the service application.</span></span> <span data-ttu-id="f1dc1-307">此参数是数据库引擎实例</span><span class="sxs-lookup"><span data-stu-id="f1dc1-307">This parameter is the database engine instance</span></span>  
  
-   <span data-ttu-id="f1dc1-308">更新希望 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] 功能启用的站点的 -url 参数\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-308">Update the **-url** parameter of the site that you want the [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] feature enabled.</span></span>  
  
 <span data-ttu-id="f1dc1-309">**使用脚本：**</span><span class="sxs-lookup"><span data-stu-id="f1dc1-309">**To use the script:**</span></span>  
  
1.  <span data-ttu-id="f1dc1-310">使用管理权限打开 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-310">Open Windows PowerShell with administrative privileges.</span></span>  
  
2.  <span data-ttu-id="f1dc1-311">将以下代码复制到脚本窗口。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-311">Copy the following code into the script window.</span></span>  
  
3.  <span data-ttu-id="f1dc1-312">更新以上部分中描述的三个参数，然后运行该脚本。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-312">Update the three parameters described in the previous section, and then run the script.</span></span>  
  
```powershell
#This script Configures SQL Server Reporting Services SharePoint mode  
  
$starttime = Get-Date  
Write-Host -foregroundcolor DarkGray StartTime>> $starttime   
  
Write-Host -ForegroundColor Green "Import the SharePoint PowerShell snappin"  
Add-PSSnapin Microsoft.Sharepoint.Powershell -EA 0  
  
Write-Host -ForegroundColor Green "Install SSRS Service and Service Proxy, and start the service"  
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"  
  
    Write-Host -ForegroundColor Green "Install the Reporting Services Shared Service"  
    Install-SPRSService  
  
    Write-Host -ForegroundColor Green " Install the Reporting Services Service Proxy"  
    Install-SPRSServiceProxy  
  
    # Get the ID of the RS Service Instance and start the service   
    Write-Host -ForegroundColor Green "Start the Reporting Services Service"  
    $RS = Get-SPServiceInstance | Where {$_.TypeName -eq "SQL Server Reporting Services Service"}  
    Start-SPServiceInstance -Identity $RS.Id.ToString()  
  
    # Wait for the Reporting Services Service to start...  
    $Status = Get-SPServiceInstance $RS.Id.ToString()  
    While ($Status.Status -ne "Online")  
    {  
        Write-Host -ForegroundColor Green "SSRS Service Not Online...Current Status = " $Status.Status  
        Start-Sleep -Seconds 2  
        $Status = Get-SPServiceInstance $RS.Id.ToString()  
    }  
  
$time = Get-Date  
Write-Host -foregroundcolor DarkGray StartTime>> $starttime   
Write-Host -foregroundcolor DarkGray $time  
  
Write-Host -ForegroundColor Green "Create a new application pool and Reporting Services service application"  
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"  
Write-Host -ForegroundColor Green "Create a new application pool"  
#!!!! update "-Account" with an existing Managed Service Account  
New-SPServiceApplicationPool -Name "Reporting Services" -Account "<domain>\User name>"  
$appPool = Get-SPServiceApplicationPool "Reporting Services"  
  
Write-Host -ForegroundColor Green " Create the Reporting Services Service Application"  
#!!!! Update "-DatabaseServer", an instance of the SQL Server database engine   
$rsService = New-SPRSServiceApplication -Name "Reporting Services Application" -ApplicationPool $appPool -DatabaseName "Reporting_Services_Application" -DatabaseServer "<server name>"  
  
Write-Host -ForegroundColor Green "Create the Reporting Services Service Application Proxy"  
$rsServiceProxy = New-SPRSServiceApplicationProxy -Name "Reporting Services Application Proxy" -ServiceApplication $rsService  
  
Write-Host -ForegroundColor Green "Associate service application proxy to default web site and grant web applications rights to SSRS application pool"  
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"     
# Associate the Reporting Services Service Applicatoin Proxy to the default web site...  
Get-SPServiceApplicationProxyGroup -default | Add-SPServiceApplicationProxyGroupMember -Member $rsServiceProxy  
  
$time=Get-Date  
Write-Host -foregroundcolor DarkGray StartTime>> $starttime   
Write-Host -foregroundcolor DarkGray $time  
  
Write-Host -ForegroundColor Green "Enable the PowerView and reportserver site features"  
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"  
#!!!! update "-url"  of the site where you want the features enabled  
Enable-SPfeature -identity "powerview" -Url http://server/sites/bi  
Enable-SPfeature -identity "reportserver" -Url http://server/sites/bi  
  
####To Verify, you can run the following:  
#Get-SPRSServiceApplication  
#Get-SPServiceApplicationPool | where {$_.name -like "reporting*"}  
#Get-SPRSServiceApplicationProxy
```  
  
##  <a name="additional-configuration"></a><a name="bkmk_additional_config"></a><span data-ttu-id="f1dc1-313">其他配置</span><span class="sxs-lookup"><span data-stu-id="f1dc1-313">Additional Configuration</span></span>  
 <span data-ttu-id="f1dc1-314">本部分介绍在大多数 SharePoint 部署中很重要的其他配置步骤。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-314">This section describes additional configuration steps that are important in most SharePoint deployments.</span></span>  
  
###  <a name="configure-excel-services-and-powerpivot"></a><a name="bkmk_configure_ECS"></a><span data-ttu-id="f1dc1-315">配置 Excel Services 和 PowerPivot</span><span class="sxs-lookup"><span data-stu-id="f1dc1-315">Configure Excel Services and PowerPivot</span></span>  
 <span data-ttu-id="f1dc1-316">如果您想要在 SharePoint 的 Excel 2013 工作簿中查看 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] Power View 报表，则需要将场中的 Excel Services 应用程序配置为使用 SharePoint 模式下的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 服务器。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-316">If you want to view [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] Power View reports in an Excel 2013 workbook in SharePoint, an Excel Services Application on the farm needs to be configured to use an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Server in SharePoint mode.</span></span> <span data-ttu-id="f1dc1-317">此外， [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务应用程序使用的应用程序池安全帐户必须是 Analysis Services 服务器上的管理员。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-317">Also, the application pool security account used by the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application, must be an administrator on the Analysis Services Server.</span></span> <span data-ttu-id="f1dc1-318">有关详细信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="f1dc1-318">For more information, see the following:</span></span>  
  
-   <span data-ttu-id="f1dc1-319">[PowerPivot for SharePoint 2013 安装](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode)中的 "为 Analysis Services 集成配置 Excel Services" 一节。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-319">The section "Configure Excel Services for Analysis Services integration" in [PowerPivot for SharePoint 2013 Installation](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode).</span></span>  
  
-   <span data-ttu-id="f1dc1-320">[管理 Excel Services 数据模型设置 (SharePoint Server 2013)](https://technet.microsoft.com/library/jj219780.aspx)。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-320">[Manage Excel Services data model settings (SharePoint Server 2013)](https://technet.microsoft.com/library/jj219780.aspx).</span></span>  
  
###  <a name="provision-subscriptions-and-alerts"></a><a name="bkmk_provision_agent"></a><span data-ttu-id="f1dc1-321">设置订阅和警报</span><span class="sxs-lookup"><span data-stu-id="f1dc1-321">Provision Subscriptions and Alerts</span></span>  
 <span data-ttu-id="f1dc1-322">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 订阅和数据警报功能可能要求配置 SQL Server 代理权限。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-322">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] subscription and data alert features may require the configuration of SQL Server Agent permissions.</span></span> <span data-ttu-id="f1dc1-323">如果您看到指示“需要 SQL Server 代理”的错误消息，而您已验证 SQL Server 代理正在运行，则应更新权限。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-323">If you see an error message that indicates SQL Server Agent is required and you have verified SQL Server Agent is running, update the permissions.</span></span> <span data-ttu-id="f1dc1-324">您可以在“创建服务应用程序成功”页上单击链接 **“设置订阅和警报”** ，以便转到其他页来设置 SQL Server 代理。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-324">You can click the link **Provision Subscriptions and Alerts** on the create service application success page to go to another page for provisioning SQL Server Agent.</span></span> <span data-ttu-id="f1dc1-325">如果您的部署是跨计算机边界的部署（例如，当 SQL Server 数据库实例位于其他计算机上时），会需要此设置步骤。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-325">The provision step is needed if your deployment crosses machine boundaries, for example when the SQL Server database instance is on a different machine.</span></span> <span data-ttu-id="f1dc1-326">有关详细信息，请参阅[为 SSRS 服务应用程序设置订阅和警报](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md)</span><span class="sxs-lookup"><span data-stu-id="f1dc1-326">For more information, see [Provision Subscriptions and Alerts for SSRS Service Applications](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md)</span></span>  
  
### <a name="configure-e-mail-for-ssrs-service-applications"></a><span data-ttu-id="f1dc1-327">为 SSRS 服务应用程序配置电子邮件</span><span class="sxs-lookup"><span data-stu-id="f1dc1-327">Configure E-mail for SSRS Service Applications</span></span>  
 <span data-ttu-id="f1dc1-328">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 数据警报功能会在电子邮件中发送警报。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-328">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] data alerts feature sends alerts in e-mail messages.</span></span> <span data-ttu-id="f1dc1-329">若要发送电子邮件，您可能需要配置 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务应用程序，并可能需要修改该服务应用程序的电子邮件传递扩展插件。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-329">To send e-mail you may need to configure your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application and you may need to modify the e-mail delivery extension for the service application.</span></span> <span data-ttu-id="f1dc1-330">如果您计划将电子邮件传递扩展插件用于 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 订阅功能，则需要进行电子邮件设置。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-330">If you plan to use the e-mail delivery extension for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] subscription feature, the e-mail settings are required.</span></span> <span data-ttu-id="f1dc1-331">有关详细信息，请参阅[为 Reporting Services 服务应用程序配置电子邮件（SharePoint 2010 和 SharePoint 2013）](../../reporting-services/install-windows/configure-e-mail-for-a-reporting-services-service-application.md)</span><span class="sxs-lookup"><span data-stu-id="f1dc1-331">For more information, see [Configure E-mail for a Reporting Services Service Application &#40;SharePoint 2010 and SharePoint 2013&#41;](../../reporting-services/install-windows/configure-e-mail-for-a-reporting-services-service-application.md)</span></span>  
  
### <a name="add-reporting-services-content-types-to-content-libraries"></a><span data-ttu-id="f1dc1-332">将 Reporting Services 内容类型添加到内容库</span><span class="sxs-lookup"><span data-stu-id="f1dc1-332">Add Reporting Services Content Types to Content Libraries</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="f1dc1-333">提供预定义的内容类型，用于管理共享数据源 (.rsds) 文件、报表模型 (.smdl) 和报表生成器报表定义 (.rdl) 文件。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-333">provides predefined content types that are used to manage shared data source (.rsds) files, report models (.smdl), and Report Builder report definition (.rdl) files.</span></span> <span data-ttu-id="f1dc1-334">将 **“报表生成器报表”**、 **“报表模型”** 和 **“报表数据源”** 内容类型添加到库中将启用 **“新建”** 命令，以便创建对应类型的新文档。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-334">Adding a **Report Builder Report**, **Report Model**, and **Report Data Source** content type to a library enables the **New** command so that you can create new documents of that type.</span></span> <span data-ttu-id="f1dc1-335">有关详细信息，请参阅[将报表服务器内容类型添加到库 &#40;Reporting Services 在 SharePoint 集成模式下&#41;" ](../../../2014/reporting-services/add-reporting-services-content-types-to-a-sharepoint-library.md)。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-335">For more information, see [Add Report Server Content Types to a Library &#40;Reporting Services in SharePoint Integrated Mode&#41;](../../../2014/reporting-services/add-reporting-services-content-types-to-a-sharepoint-library.md).</span></span>  
  
### <a name="activate-the-report-server-file-sync-feature"></a><span data-ttu-id="f1dc1-336">激活报表服务器文件同步功能</span><span class="sxs-lookup"><span data-stu-id="f1dc1-336">Activate the Report Server File sync Feature</span></span>  
 <span data-ttu-id="f1dc1-337">如果用户经常直接将已发布的报表项上载到 SharePoint 文档库，则 **“报表服务器文件同步”** 站点级别功能将很有用。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-337">If users will frequently upload published report items directly to SharePoint document libraries, the **Report Server File Sync** site level feature will be beneficial.</span></span> <span data-ttu-id="f1dc1-338">文件同步功能将更频繁地将报表服务器目录与文档库中的项进行同步。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-338">The file sync feature will synchronize the report server catalog with items in document libraries on a more frequent basis.</span></span> <span data-ttu-id="f1dc1-339">有关详细信息，请参阅[在 SharePoint 管理中心中激活报表服务器文件同步功能](../../../2014/reporting-services/activate-report-server-file-sync-feature-sharepoint-central-administration.md)。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-339">For more information, see [Activate the Report Server File Sync Feature in SharePoint Central Administration](../../../2014/reporting-services/activate-report-server-file-sync-feature-sharepoint-central-administration.md).</span></span>  
  
##  <a name="verify-the-installation"></a><a name="bkmk_verify_installation"></a><span data-ttu-id="f1dc1-340">验证安装</span><span class="sxs-lookup"><span data-stu-id="f1dc1-340">Verify the installation</span></span>  
 <span data-ttu-id="f1dc1-341">以下是验证 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式部署的建议步骤和过程。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-341">The following are suggested steps and procedures to verify the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode deployment.</span></span>  
  
-   <span data-ttu-id="f1dc1-342">请参阅验证主题 [Verify a Reporting Services Installation](../../reporting-services/install-windows/verify-a-reporting-services-installation.md)中的 SharePoint 部分。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-342">See the SharePoint section in the verification topic [Verify a Reporting Services Installation](../../reporting-services/install-windows/verify-a-reporting-services-installation.md).</span></span>  
  
-   <span data-ttu-id="f1dc1-343">在 SharePoint 文档库中，创建一个仅包含文本框的基本 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 报表，例如标题。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-343">In a SharePoint document library, create a basic [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report that only contains a text box, for example a title.</span></span> <span data-ttu-id="f1dc1-344">该报表不包含任何数据源或数据集。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-344">The report does not contain any data sources or datasets.</span></span> <span data-ttu-id="f1dc1-345">目标是确认您能打开报表生成器，生成基本报表，以及预览该报表。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-345">The goal is to verify you can open Report Builder, build a basic report, and preview the report.</span></span>  
  
     <span data-ttu-id="f1dc1-346">将报表保存到文档库并从库中运行该报表。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-346">Save the report to the document library and the run the report from the library.</span></span> <span data-ttu-id="f1dc1-347">有关使用报表生成器创建报表的详细信息，请参阅 [启动报表生成器（报表生成器）](https://technet.microsoft.com/library/ms159221.aspx)。</span><span class="sxs-lookup"><span data-stu-id="f1dc1-347">For more information on creating reports with Report Builder, see [Start Report Builder (Report Builder)](https://technet.microsoft.com/library/ms159221.aspx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1dc1-348">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f1dc1-348">See Also</span></span>  
 <span data-ttu-id="f1dc1-349">[Reporting Services SharePoint 模式的 PowerShell cmdlet](../../../2014/reporting-services/powershell-cmdlets-for-reporting-services-sharepoint-mode.md) </span><span class="sxs-lookup"><span data-stu-id="f1dc1-349">[PowerShell cmdlets for Reporting Services SharePoint Mode](../../../2014/reporting-services/powershell-cmdlets-for-reporting-services-sharepoint-mode.md) </span></span>  
 <span data-ttu-id="f1dc1-350">[升级和迁移 Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="f1dc1-350">[Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md) </span></span>  
 <span data-ttu-id="f1dc1-351">[内容路线图：设置和配置 SharePoint Server 和 SQL Server BI](https://technet.microsoft.com/library/dn205112.aspx) </span><span class="sxs-lookup"><span data-stu-id="f1dc1-351">[Content Roadmap: Set up and configure SharePoint Server and SQL Server BI](https://technet.microsoft.com/library/dn205112.aspx) </span></span>  
 <span data-ttu-id="f1dc1-352">[SQL Server 2012 的各个版本支持的功能](https://go.microsoft.com/fwlink/?linkid=232473) </span><span class="sxs-lookup"><span data-stu-id="f1dc1-352">[Features Supported by the Editions of SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473) </span></span>  
 [<span data-ttu-id="f1dc1-353">Reporting Services SharePoint 服务和服务应用程序</span><span class="sxs-lookup"><span data-stu-id="f1dc1-353">Reporting Services SharePoint Service and Service Applications</span></span>](../../../2014/reporting-services/reporting-services-sharepoint-service-and-service-applications.md)
