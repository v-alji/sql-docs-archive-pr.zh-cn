---
title: 安装 SharePoint 2010 Reporting Services SharePoint 模式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 47efa72e-1735-4387-8485-f8994fb08c8c
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 8be76ab37ce66f4ef93d29093202768aa85c4fb2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588869"
---
# <a name="install-reporting-services-sharepoint-mode-for-sharepoint-2010"></a><span data-ttu-id="2290c-102">安装用于 SharePoint 2010 的 Reporting Services SharePoint 模式</span><span class="sxs-lookup"><span data-stu-id="2290c-102">Install Reporting Services SharePoint Mode for SharePoint 2010</span></span>
  <span data-ttu-id="2290c-103">本主题中的过程将指导您完成以 SharePoint 模式在单台服务器上安装 Reporting Services 报表服务器。</span><span class="sxs-lookup"><span data-stu-id="2290c-103">The procedures in this topic guide you through a single server installation of a Reporting Services report server in SharePoint mode.</span></span> <span data-ttu-id="2290c-104">涉及的步骤包括运行 SQL Server 安装向导以及使用 SharePoint 2010 管理中心的其他配置任务。</span><span class="sxs-lookup"><span data-stu-id="2290c-104">The steps include running the SQL Server installation wizard as well as additional configuration tasks that use SharePoint 2010 central administration.</span></span> <span data-ttu-id="2290c-105">本主题还可用于针对现有安装的单独过程，例如创建 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务应用程序。</span><span class="sxs-lookup"><span data-stu-id="2290c-105">The topic can also be used for individual procedures for an existing installation, for example to create a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application.</span></span> <span data-ttu-id="2290c-106">有关将其他服务器添加 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 到现有场中的信息，请参阅[向场中添加其他报表服务器 &#40;SSRS 向外扩展&#41;](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md)并[向场中添加其他 Reporting Services Web 前端](../../reporting-services/install-windows/add-an-additional-reporting-services-web-front-end-to-a-farm.md)。</span><span class="sxs-lookup"><span data-stu-id="2290c-106">For information on adding additional [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] servers to an existing farm, see [Add an Additional Report Server to a Farm &#40;SSRS Scale-out&#41;](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md) and [Add an Additional Reporting Services Web Front-end to a Farm](../../reporting-services/install-windows/add-an-additional-reporting-services-web-front-end-to-a-farm.md).</span></span>  
  
||  
|-|  
|<span data-ttu-id="2290c-107">**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2010</span><span class="sxs-lookup"><span data-stu-id="2290c-107">**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2010</span></span>|  
  
 <span data-ttu-id="2290c-108">单台服务器安装对于开发和测试方案很有用，但不建议用于生产环境。</span><span class="sxs-lookup"><span data-stu-id="2290c-108">A single server installation is useful for development and testing scenarios but is not recommended for production environments.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2290c-109">有关 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 将现有 SharePoint 模式安装升级到的信息 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，请参阅[升级和迁移 Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="2290c-109">For information on upgrading and existing [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode installation to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], see [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md).</span></span>  
  

  
##  <a name="prerequisites"></a><a name="bkmk_prereq"></a><span data-ttu-id="2290c-110">先决条件</span><span class="sxs-lookup"><span data-stu-id="2290c-110">Prerequisites</span></span>  
  
-   > [!IMPORTANT]  
    >  <span data-ttu-id="2290c-111">配置和管理 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式不再需要或支持 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置管理器。</span><span class="sxs-lookup"><span data-stu-id="2290c-111">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager is no longer required or supported to configure and administer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span> <span data-ttu-id="2290c-112">使用 SharePoint 管理中心在 SharePoint 模式中配置报表服务器。</span><span class="sxs-lookup"><span data-stu-id="2290c-112">Use SharePoint Central Administration to configure a report server in SharePoint mode.</span></span> <span data-ttu-id="2290c-113">有关详细信息，请参阅[管理 Reporting Services SharePoint 服务应用程序](../../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md)。</span><span class="sxs-lookup"><span data-stu-id="2290c-113">For more information, see [Manage a Reporting Services SharePoint Service Application](../../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md).</span></span>  
  
-   <span data-ttu-id="2290c-114">查看以下要求主题，包括针对 SharePoint 2010 产品的要求：</span><span class="sxs-lookup"><span data-stu-id="2290c-114">Review the following topics for requirements, including SharePoint 2010 products:</span></span>  
  
    -   [<span data-ttu-id="2290c-115">在线发行说明</span><span class="sxs-lookup"><span data-stu-id="2290c-115">Online Release Notes</span></span>](https://msdn.microsoft.com/library/dn169381.aspx)
  
    -   [<span data-ttu-id="2290c-116">在 SharePoint 2010 场中使用 SQL Server BI 功能的指南</span><span class="sxs-lookup"><span data-stu-id="2290c-116">Guidance for Using SQL Server BI Features in a SharePoint 2010 Farm</span></span>](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md)  
  
-   <span data-ttu-id="2290c-117">本主题不涉及安装 SharePoint 2010 产品。</span><span class="sxs-lookup"><span data-stu-id="2290c-117">This topic does no cover the installation of SharePoint 2010 Products.</span></span> <span data-ttu-id="2290c-118">有关详细信息，请参阅[在 SharePoint 2010 场中使用 SQL SERVER BI 功能的指南](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md)。</span><span class="sxs-lookup"><span data-stu-id="2290c-118">For more information, see [Guidance for Using SQL Server BI Features in a SharePoint 2010 Farm](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md).</span></span>  
  
-   <span data-ttu-id="2290c-119">以下过程用于配置 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 报表服务器，但不适用于报表服务器的以前版本。</span><span class="sxs-lookup"><span data-stu-id="2290c-119">These procedures are intended for configuring a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] report server and do not work for previous versions of report server.</span></span> <span data-ttu-id="2290c-120">以前版本的报表服务器未使用 SharePoint Shared Service 体系结构。</span><span class="sxs-lookup"><span data-stu-id="2290c-120">Previous versions of report server did not use the SharePoint Shared Service architecture.</span></span> <span data-ttu-id="2290c-121">例如，SQL Server 2008 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 报表服务器和 SQL Server 2008 R2 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 报表服务器。</span><span class="sxs-lookup"><span data-stu-id="2290c-121">For example, SQL Server 2008 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report servers and SQL Server 2008 R2 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report servers.</span></span>  
  
-   <span data-ttu-id="2290c-122">验证是否已在 Windows 服务器管理器中启动**SharePoint 2010 管理**服务。</span><span class="sxs-lookup"><span data-stu-id="2290c-122">Verify the **SharePoint 2010 Administration** service is started in Windows Server Manager.</span></span>  
  
 <span data-ttu-id="2290c-123">![单服务器安装的 SSRS 组件](../../../2014/sql-server/install/media/rs-deployment-1-server.gif "单服务器安装的 SSRS 组件")</span><span class="sxs-lookup"><span data-stu-id="2290c-123">![SSRS components on a 1 server installation](../../../2014/sql-server/install/media/rs-deployment-1-server.gif "SSRS components on a 1 server installation")</span></span>  
  
### <a name="database-considerations-for-a-single-server-configuration"></a><span data-ttu-id="2290c-124">单服务器配置的数据库注意事项</span><span class="sxs-lookup"><span data-stu-id="2290c-124">Database Considerations for a Single Server Configuration</span></span>  
  
-   <span data-ttu-id="2290c-125">Reporting Services 和 SharePoint 产品及技术均使用 SQL Server 关系数据库来存储应用程序数据。</span><span class="sxs-lookup"><span data-stu-id="2290c-125">Both Reporting Services and SharePoint products and technologies use SQL Server relational databases to store application data.</span></span>  
  
-   [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] <span data-ttu-id="2290c-126">需要兼容的 SQL 引擎的 SQL Server 评估版实例。</span><span class="sxs-lookup"><span data-stu-id="2290c-126">requires a compatible SQL Server evaluation edition instance of the SQL Engine.</span></span>  
  
-   <span data-ttu-id="2290c-127">SharePoint 产品可以使用现有的数据库实例。</span><span class="sxs-lookup"><span data-stu-id="2290c-127">SharePoint products can use an existing database instance.</span></span> <span data-ttu-id="2290c-128">如果未安装数据库引擎实例，则 SharePoint 产品安装程序将安装 SQL Server Express Edition 以用于 SharePoint 应用程序数据库。</span><span class="sxs-lookup"><span data-stu-id="2290c-128">If an instance of Database Engine is not installed, the SharePoint Products Setup program installs SQL Server Express Edition for the SharePoint application databases.</span></span>  
  
-   <span data-ttu-id="2290c-129">报表服务器实例不能将 SQL Server Express Edition 用于其数据库。</span><span class="sxs-lookup"><span data-stu-id="2290c-129">The report server instance cannot use the SQL Server Express Edition for its database.</span></span> <span data-ttu-id="2290c-130">但是，由 SharePoint 产品安装的 SQL Server Express Edition 实例可与其他数据库引擎版本并存。</span><span class="sxs-lookup"><span data-stu-id="2290c-130">However, the SQL Server Express Edition instance that is installed by the SharePoint product can exist side-by-side with other Database Engine editions.</span></span>  
  

  
##  <a name="install-reporting-services-report-server-in-sharepoint-mode"></a><a name="bkmk_install_SSRS"></a><span data-ttu-id="2290c-131">在 SharePoint 模式下安装 Reporting Services 报表服务器</span><span class="sxs-lookup"><span data-stu-id="2290c-131">Install Reporting Services Report Server in SharePoint mode</span></span>  
  
1.  <span data-ttu-id="2290c-132">运行 SQL Server 安装向导。</span><span class="sxs-lookup"><span data-stu-id="2290c-132">Run the SQL Server Installation Wizard.</span></span>  
  
2.  <span data-ttu-id="2290c-133">在向导的左侧单击 **“安装”** ，然后单击 **“全新 SQL Server 独立安装或向现有安装添加功能”**。</span><span class="sxs-lookup"><span data-stu-id="2290c-133">Click **Installation** in the left side of the wizard and then click **New SQL Server stand-alone installation or add features to an existing installation**.</span></span>  
  
3.  <span data-ttu-id="2290c-134">在 **“安装程序支持规则”** 页上单击 **“确定”** ，假定所有规则均已通过验证。</span><span class="sxs-lookup"><span data-stu-id="2290c-134">Click **OK** on the **Setup Support Rules** page, assuming all rules passed.</span></span>  
  
4.  <span data-ttu-id="2290c-135">在 **“安装程序支持文件”** 页中，单击 **“安装”** 。</span><span class="sxs-lookup"><span data-stu-id="2290c-135">Click **Install** on the **Setup Support Files** page.</span></span>  
  
5.  <span data-ttu-id="2290c-136">支持文件安装完成后，单击 "**下一步**"，支持规则显示的状态为 "已**通过**"。</span><span class="sxs-lookup"><span data-stu-id="2290c-136">Click **Next** after the support files have completed installing and the support rules show a status of **passed**.</span></span> <span data-ttu-id="2290c-137">查看任何警告或妨碍安装的问题。</span><span class="sxs-lookup"><span data-stu-id="2290c-137">Review any warnings or blocking issues.</span></span>  
  
6.  <span data-ttu-id="2290c-138">在 "**产品密钥**" 页上，键入密钥或接受默认的 "企业评估版"。</span><span class="sxs-lookup"><span data-stu-id="2290c-138">On the **Product Key** page, type your key or accept the default of the 'Enterprise Evaluation' edition.</span></span>  
  
     <span data-ttu-id="2290c-139">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="2290c-139">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="2290c-140">查看并接受许可条款。</span><span class="sxs-lookup"><span data-stu-id="2290c-140">Review and accept the license terms.</span></span> <span data-ttu-id="2290c-141">对于您单击以同意发送功能使用情况数据来帮助改进产品功能和支持，Microsoft 深表感谢。</span><span class="sxs-lookup"><span data-stu-id="2290c-141">Microsoft appreciates you clicking to agree to send feature usage data to help improve product features and support.</span></span>  
  
     <span data-ttu-id="2290c-142">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="2290c-142">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="2290c-143">选择 "**安装角色**" 页上的 " **SQL Server 功能安装**"。</span><span class="sxs-lookup"><span data-stu-id="2290c-143">Select **SQL Server Feature Installation** on the **Setup Role** page.</span></span>  
  
     <span data-ttu-id="2290c-144">点击“下一步”</span><span class="sxs-lookup"><span data-stu-id="2290c-144">Click **Next**</span></span>  
  
     <span data-ttu-id="2290c-145">![安装角色的 SQL Server 功能安装](../../../2014/sql-server/install/media/rs-setuprole.gif "安装角色的 SQL Server 功能安装")</span><span class="sxs-lookup"><span data-stu-id="2290c-145">![SQL Server Feature Installation for setup role](../../../2014/sql-server/install/media/rs-setuprole.gif "SQL Server Feature Installation for setup role")</span></span>  
  
9. <span data-ttu-id="2290c-146">在 **“功能选择”** 页中，选择以下选项：</span><span class="sxs-lookup"><span data-stu-id="2290c-146">Select the following on the **Feature Selection** page:</span></span>  
  
    -   <span data-ttu-id="2290c-147">**Reporting Services-SharePoint**</span><span class="sxs-lookup"><span data-stu-id="2290c-147">**Reporting Services - SharePoint**</span></span>  
  
    -   <span data-ttu-id="2290c-148">**Reporting Services 用于 SharePoint 2010 产品的外接程序**。</span><span class="sxs-lookup"><span data-stu-id="2290c-148">**Reporting Services add-in for SharePoint 2010 products**.</span></span> <span data-ttu-id="2290c-149">![注意](../../../2014/reporting-services/media/rs-fyinote.png "注意")用于安装外接程序的安装向导选项是版本的新 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 版本。</span><span class="sxs-lookup"><span data-stu-id="2290c-149">![note](../../../2014/reporting-services/media/rs-fyinote.png "note")The installation wizard option for installing the add-in is new with the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] release.</span></span>  
  
    -   <span data-ttu-id="2290c-150">如果您尚未安装 SQL Server [!INCLUDE[ssDE](../../includes/ssde-md.md)]实例，则还可以选择 **“数据库引擎服务”** 和 **“管理工具 - 完整”** 以提供一个完整环境。</span><span class="sxs-lookup"><span data-stu-id="2290c-150">If you do not already have an instance of SQL Server [!INCLUDE[ssDE](../../includes/ssde-md.md)], you could also select **Database Engine Services** and **Management Tools Complete** for a complete environment.</span></span>  
  
     <span data-ttu-id="2290c-151">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="2290c-151">Click **Next**.</span></span>  
  
     <span data-ttu-id="2290c-152">![SharePoint 模式的 SSRS 功能选择](../../../2014/sql-server/install/media/rs-setupfeatureselection-sharepoint-with-circles.gif "SharePoint 模式的 SSRS 功能选择")</span><span class="sxs-lookup"><span data-stu-id="2290c-152">![SSRS Feature Selection for SharePoint mode](../../../2014/sql-server/install/media/rs-setupfeatureselection-sharepoint-with-circles.gif "SSRS Feature Selection for SharePoint mode")</span></span>  
  
10. <span data-ttu-id="2290c-153">在 "**安装规则**" 页上单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="2290c-153">Click **Next** on the **Installation Rules** page.</span></span> <span data-ttu-id="2290c-154">查看任何警告或妨碍安装的问题。</span><span class="sxs-lookup"><span data-stu-id="2290c-154">Review any warnings or blocking issues.</span></span>  
  
11. <span data-ttu-id="2290c-155">如果您已选择“数据库引擎服务”，请在 **“实例配置”** 页上接受 **MSSQLSERVER** 的默认实例，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="2290c-155">If you selected the Database Engine services, accept the default instance of **MSSQLSERVER** on the **Instance Configuration** page and click **Next**.</span></span> <span data-ttu-id="2290c-156">与以前的 Reporting Services 体系结构不同，Reporting Services 共享服务体系结构不基于 SQL Server“实例”。</span><span class="sxs-lookup"><span data-stu-id="2290c-156">The Reporting Services shared service architecture is not based on a SQL Server "instance" was the previous Reporting Services architecture.</span></span>  
  
12. <span data-ttu-id="2290c-157">阅读 **“磁盘空间要求”** 页，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="2290c-157">Review the **Disk Space Requirements** page and click **Next**.</span></span>  
  
13. <span data-ttu-id="2290c-158">在 "**服务器配置**" 页上，键入相应的凭据。</span><span class="sxs-lookup"><span data-stu-id="2290c-158">On the **Server Configuration** page type appropriate credentials.</span></span> <span data-ttu-id="2290c-159">如果您要使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 数据警报或订阅功能，则需要将 SQL Server 代理的 **“启动类型”** 更改为 **“自动”**。</span><span class="sxs-lookup"><span data-stu-id="2290c-159">If you want to use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] data alerting or subscription features, you need to change the **Startup Type** for SQL Server Agent to **Automatic**.</span></span>  
  
     <span data-ttu-id="2290c-160">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="2290c-160">Click **Next**.</span></span>  
  
14. <span data-ttu-id="2290c-161">如果您选择了“数据库引擎服务”，您将看到 **“数据库引擎配置”** 页。请将相应的帐户添加到 SQL 管理员列表，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="2290c-161">If you selected the Database Engine services, you will see the **Database Engine Configuration** page, add appropriate accounts to the list of SQL Administrators and click **Next**.</span></span>  
  
15. <span data-ttu-id="2290c-162">在 **“Reporting Services 配置”** 页上，您应该看到 **“仅安装”** 选项处于选中状态。</span><span class="sxs-lookup"><span data-stu-id="2290c-162">On the **Reporting Services Configuration** page you should see the **Install only** option is selected.</span></span> <span data-ttu-id="2290c-163">此选项将安装报表服务器文件，但不会为 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置 SharePoint 环境。SQL Server 安装完成后，您需要按照本主题的其他章节的内容配置 SharePoint 环境。</span><span class="sxs-lookup"><span data-stu-id="2290c-163">This option installs the report server files, and does not configure the SharePoint environment for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].When the SQL Server installation is complete, follow the other sections of this topic to configure the SharePoint environment.</span></span> <span data-ttu-id="2290c-164">这包括安装 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 共享服务和创建 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务应用程序。</span><span class="sxs-lookup"><span data-stu-id="2290c-164">This Includes installing the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] shared service and creating [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service applications.</span></span>  
  
     <span data-ttu-id="2290c-165">![rs_SQL11_SETUP_SSRS_configpage_withcircles](../../../2014/sql-server/install/media/rs-kj-setup-ssrs-configpage-withcircles.gif "rs_SQL11_SETUP_SSRS_configpage_withcircles")</span><span class="sxs-lookup"><span data-stu-id="2290c-165">![rs_SQL11_SETUP_SSRS_configpage_withcircles](../../../2014/sql-server/install/media/rs-kj-setup-ssrs-configpage-withcircles.gif "rs_SQL11_SETUP_SSRS_configpage_withcircles")</span></span>  
  
16. <span data-ttu-id="2290c-166">请通过在 **“错误报告”** 页上单击用于发送错误报告的复选框，来帮助 Microsoft 改进 SQL Server 功能和服务。</span><span class="sxs-lookup"><span data-stu-id="2290c-166">Help Microsoft improve SQL Server features and services by clicking the check box to send error reports on the **Error Reporting** page.</span></span>  
  
     <span data-ttu-id="2290c-167">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="2290c-167">Click **Next**.</span></span>  
  
17. <span data-ttu-id="2290c-168">查看任何警告，然后在 **“安装配置规则”** 页上单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="2290c-168">Review any warnings and then click **Next** on the **Installation Configuration Rules** page.</span></span>  
  
18. <span data-ttu-id="2290c-169">在 **“准备安装”** 页上，查看安装摘要，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="2290c-169">On the **Ready to Install** page, review the installation summary and then click **Next**.</span></span> <span data-ttu-id="2290c-170">摘要将包含一个**Reporting Services**节点，该节点将包含**SharePointFilesOnlyMode**的安装模式值以及帐户信息。</span><span class="sxs-lookup"><span data-stu-id="2290c-170">The summary will include a **Reporting Services** node that will include the installation mode value of **SharePointFilesOnlyMode** as well as the account information.</span></span>  
  

  
##  <a name="install-and-start-the-reporting-services-sharepoint-service"></a><a name="bkmk_install_SSRS_sharedservice"></a><span data-ttu-id="2290c-171">安装并启动 Reporting Services SharePoint 服务</span><span class="sxs-lookup"><span data-stu-id="2290c-171">Install and Start the Reporting Services SharePoint Service</span></span>  
 <span data-ttu-id="2290c-172">![PowerShell 相关内容](../../../2014/reporting-services/media/rs-powershellicon.jpg "PowerShell 相关内容")</span><span class="sxs-lookup"><span data-stu-id="2290c-172">![PowerShell related content](../../../2014/reporting-services/media/rs-powershellicon.jpg "PowerShell related content")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2290c-173">如果要安装到现有 SharePoint 场，**则无需**完成本部分中的步骤。</span><span class="sxs-lookup"><span data-stu-id="2290c-173">If you are installing into an existing SharePoint farm, **you do not need to** complete the steps in this section.</span></span> <span data-ttu-id="2290c-174">在上一节中运行 SQL Server 安装向导时，已安装并已启动 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 服务。</span><span class="sxs-lookup"><span data-stu-id="2290c-174">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint service was installed and started when you ran the SQL Server installation wizard in the previous section.</span></span>  
  
 <span data-ttu-id="2290c-175">在执行 SQL Server 安装向导的过程中已安装了必需的文件，但需要将服务注册到 SharePoint 场中。</span><span class="sxs-lookup"><span data-stu-id="2290c-175">The necessary files were installed as part of the SQL Server installation wizard, but the services need to be registered into the SharePoint farm.</span></span> <span data-ttu-id="2290c-176">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 版本引入了对 SharePoint 模式下的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的 PowerShell 支持。</span><span class="sxs-lookup"><span data-stu-id="2290c-176">The [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] release introduces PowerShell support for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint mode.</span></span> <span data-ttu-id="2290c-177">以下步骤将指导您完成打开 SharePoint Management Shell 并运行 cmdlet 的过程：</span><span class="sxs-lookup"><span data-stu-id="2290c-177">The following steps guide you through opening the SharePoint Management Shell and running cmdlets:</span></span>  
  
1.  <span data-ttu-id="2290c-178">单击 **“开始”** 按钮</span><span class="sxs-lookup"><span data-stu-id="2290c-178">Click the **Start** button</span></span>  
  
2.  <span data-ttu-id="2290c-179">单击 " **Microsoft SharePoint 2010 产品**" 组。</span><span class="sxs-lookup"><span data-stu-id="2290c-179">Click the **Microsoft SharePoint 2010 Products** group.</span></span>  
  
3.  <span data-ttu-id="2290c-180">右键单击 " **SharePoint 2010 命令行管理**程序"，然后单击 "以**管理员身份运行**"。</span><span class="sxs-lookup"><span data-stu-id="2290c-180">Right-click **SharePoint 2010 Management Shell** click **Run as administrator**.</span></span>  
  
4.  <span data-ttu-id="2290c-181">运行以下 PowerShell 命令以安装 SharePoint 服务。</span><span class="sxs-lookup"><span data-stu-id="2290c-181">Run the following PowerShell command to install the SharePoint service.</span></span> <span data-ttu-id="2290c-182">命令成功完成后会在 Management Shell 中显示一个新行。</span><span class="sxs-lookup"><span data-stu-id="2290c-182">A successful completion of the command displays a new line in the management shell.</span></span> <span data-ttu-id="2290c-183">当命令成功完成时，不会向 Management Shell 返回任何消息：</span><span class="sxs-lookup"><span data-stu-id="2290c-183">No message is returned to the management shell when the command completes successfully:</span></span>  
  
    ```powershell
    Install-SPRSService  
    ```  
  
5.  <span data-ttu-id="2290c-184">运行以下 PowerShell 命令以安装服务代理：</span><span class="sxs-lookup"><span data-stu-id="2290c-184">Run the following PowerShell command to install the service proxy:</span></span>  
  
    ```powershell
    Install-SPRSServiceProxy  
    ```  
  
6.  <span data-ttu-id="2290c-185">运行以下 PowerShell 命令以启动服务，或者查看下面的注释以了解有关从 SharePoint 管理中心启动服务的说明：</span><span class="sxs-lookup"><span data-stu-id="2290c-185">Run the following PowerShell command to start the service or see the following notes for instructions to start the service from SharePoint Central administration:</span></span>  
  
    ```powershell
    Get-SPServiceInstance -All | Where {$_.TypeName -like "SQL Server Reporting*"} | Start-SPServiceInstance  
    ```  
  
 <span data-ttu-id="2290c-186">您也可以通过 SharePoint 管理中心（而不是通过运行第三个 PowerShell 命令）来启动服务。</span><span class="sxs-lookup"><span data-stu-id="2290c-186">You can also start the service from SharePoint central Administration rather than running the third PowerShell command.</span></span> <span data-ttu-id="2290c-187">以下步骤还用于验证服务是否正在运行。</span><span class="sxs-lookup"><span data-stu-id="2290c-187">The following steps are also useful to verify that the service is running.</span></span>  
  
1.  <span data-ttu-id="2290c-188">在 SharePoint 管理中心的 **“系统设置”** 组中，单击 **“管理服务器上的服务”** 。</span><span class="sxs-lookup"><span data-stu-id="2290c-188">In SharePoint Central Administration, click **Manage Services on Server** in the **System Settings** group.</span></span>  
  
2.  <span data-ttu-id="2290c-189">找到 **“SQL Server Reporting Services 服务”** ，然后在“操作”列中单击 **“启动”** 。</span><span class="sxs-lookup"><span data-stu-id="2290c-189">Find **SQL Server Reporting Services Service** and click **Start** in the Action column.</span></span>  
  
3.  <span data-ttu-id="2290c-190">Reporting Services 服务的状态将从 **“已停止”** 更改为 **“已启动”**。</span><span class="sxs-lookup"><span data-stu-id="2290c-190">The status of the Reporting Services service will change from **Stopped** to **Started**.</span></span> <span data-ttu-id="2290c-191">如果 Reporting Services 服务不在列表中，则使用 PowerShell 安装该服务。</span><span class="sxs-lookup"><span data-stu-id="2290c-191">If the Reporting Services service is not in the list, use PowerShell to install the service.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2290c-192">如果 Reporting Services 服务仍处于 "**正在启动**" 状态，并且未更改为 "**已启动**"，请验证 Windows 服务器管理器中的 "SharePoint 2010 管理" 服务是否已启动。</span><span class="sxs-lookup"><span data-stu-id="2290c-192">If the Reporting Services service stays in the **Starting** status and does not change to **Started**, verify the 'SharePoint 2010 Administration' service is started in Windows Server Manager.</span></span>  

##  <a name="create-a-reporting-services-service-application"></a><a name="bkmk_create_serrviceapplication"></a><span data-ttu-id="2290c-193">创建 Reporting Services 服务应用程序</span><span class="sxs-lookup"><span data-stu-id="2290c-193">Create a Reporting Services Service Application</span></span>  
 <span data-ttu-id="2290c-194">本节提供您在查看现有服务应用程序的情况下，用于创建服务应用程序的步骤和属性说明。</span><span class="sxs-lookup"><span data-stu-id="2290c-194">This section provides the steps to create a service application and a description of the properties, if you are reviewing an existing service application.</span></span>  
  
1.  <span data-ttu-id="2290c-195">在 SharePoint 管理中心的 "**应用程序管理**" 组中，单击 "**管理服务应用程序**"。</span><span class="sxs-lookup"><span data-stu-id="2290c-195">In SharePoint Central Administration, in the **Application Management** group, click **Manage Service Applications**.</span></span>  
  
2.  <span data-ttu-id="2290c-196">在 SharePoint 功能区中，单击 **“新建”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="2290c-196">In the SharePoint ribbon, click the **New** button.</span></span>  
  
3.  <span data-ttu-id="2290c-197">在“新建”菜单中，单击 **“SQL Server Reporting Services 服务应用程序”**。</span><span class="sxs-lookup"><span data-stu-id="2290c-197">In the New menu, click **SQL Server Reporting Services Service Application.**.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="2290c-198">如果该 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 选项未显示在列表中，则**表明 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 共享服务未安装**。</span><span class="sxs-lookup"><span data-stu-id="2290c-198">If the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] option does not appear in the list, it is an **indication that the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] shared service is not installed**.</span></span> <span data-ttu-id="2290c-199">查看上一节，了解如何使用 PowerShell cmdlt 安装 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务。</span><span class="sxs-lookup"><span data-stu-id="2290c-199">Review the previous section on how to use PowerShell cmdlts to install the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service.</span></span>  
  
4.  <span data-ttu-id="2290c-200">在 **“创建 SQL Server Reporting Services 服务应用程序”** 页中，输入应用程序的名称。</span><span class="sxs-lookup"><span data-stu-id="2290c-200">In the **Create SQL Server Reporting Services Service Application** page, enter a name for the application.</span></span> <span data-ttu-id="2290c-201">如果您要创建多个 Reporting Services 服务应用程序，则描述性名称或命名约定可帮助您组织您的管理操作。</span><span class="sxs-lookup"><span data-stu-id="2290c-201">If you are creating multiple Reporting Services service applications, a descriptive name or naming convention helps you organize your administration and management operations.</span></span>  
  
5.  <span data-ttu-id="2290c-202">在 **“应用程序池”** 部分中，为该应用程序创建一个新应用程序池（推荐）。</span><span class="sxs-lookup"><span data-stu-id="2290c-202">In **Application Pool** section, create a new application pool for the application (recommended).</span></span> <span data-ttu-id="2290c-203">使用与服务应用程序相同的名称作为新应用程序池的名称，这可以使您正在进行的管理更加容易。</span><span class="sxs-lookup"><span data-stu-id="2290c-203">Using the same name for the new application pool as the service application, makes ongoing administration easier.</span></span>  
  
     <span data-ttu-id="2290c-204">为该应用程序池选择或创建一个托管帐户。</span><span class="sxs-lookup"><span data-stu-id="2290c-204">Select or create a managed account for the application pool.</span></span> <span data-ttu-id="2290c-205">请确保指定一个域用户帐户。</span><span class="sxs-lookup"><span data-stu-id="2290c-205">Be sure to specify a domain user account.</span></span> <span data-ttu-id="2290c-206">通过域用户帐户，可以使用 SharePoint 的托管帐户功能，从而使您可以在一个位置中更新密码和帐户信息。</span><span class="sxs-lookup"><span data-stu-id="2290c-206">A domain user account enables the use of the SharePoint managed account feature, which lets you update passwords and account information in one place.</span></span> <span data-ttu-id="2290c-207">如果您计划扩展部署以便包括将在同一标识下运行的附加服务实例，则域帐户也是必需的。</span><span class="sxs-lookup"><span data-stu-id="2290c-207">Domain accounts are also required if you plan to scale out the deployment to include additional service instances that run under the same identity.</span></span>  
  
6.  <span data-ttu-id="2290c-208">在 **“数据库服务器”** 中，您可以使用当前服务器或选择其他 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="2290c-208">In the **Database Server**, you can use the current server or choose a different SQL Server.</span></span>  
  
7.  <span data-ttu-id="2290c-209">在 **“数据库名称”** 中，默认值是 `ReportingService_<guid>`，这是唯一的数据库名称。</span><span class="sxs-lookup"><span data-stu-id="2290c-209">In **Database Name** the default value is `ReportingService_<guid>`, which is a unique database name.</span></span> <span data-ttu-id="2290c-210">如果您键入一个新值，请键入唯一值。</span><span class="sxs-lookup"><span data-stu-id="2290c-210">If you type a new value, type a unique value.</span></span>  
  
8.  <span data-ttu-id="2290c-211">在 **“数据库身份验证”** 中，默认值是 “Windows 身份验证”。</span><span class="sxs-lookup"><span data-stu-id="2290c-211">In **Database Authentication**, the default is Windows Authentication.</span></span> <span data-ttu-id="2290c-212">如果您选择 **“SQL 身份验证”**，请参考 SharePoint 管理员指南以便了解有关如何在 SharePoint 部署中使用此身份验证类型的最佳实践。</span><span class="sxs-lookup"><span data-stu-id="2290c-212">If you choose **SQL Authentication**, refer to the SharePoint administrator guide for best practices on how to use this authentication type in a SharePoint deployment.</span></span>  
  
9. <span data-ttu-id="2290c-213">在 **“Web 应用程序关联”** 部分中，选择要设置为供当前 Reporting Services 服务应用程序访问的 Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="2290c-213">In the **Web Application Association** section, select the Web Application to be provisioned for access by the current Reporting Services Service Application.</span></span> <span data-ttu-id="2290c-214">可以将一个 Reporting Services 服务应用程序与一个 Web 应用程序相关联。</span><span class="sxs-lookup"><span data-stu-id="2290c-214">You can associate one Reporting Services service application to one web application.</span></span> <span data-ttu-id="2290c-215">如果所有当前 Web 应用程序均已与一个 Reporting Services 服务应用程序相关联，将显示警告消息。</span><span class="sxs-lookup"><span data-stu-id="2290c-215">If all of the current web applications are already associated with a Reporting Services service application, you see a warning message.</span></span>  
  
10. <span data-ttu-id="2290c-216">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="2290c-216">Click **OK**.</span></span>  
  
11. <span data-ttu-id="2290c-217">用于创建服务应用程序的过程可能会需要几分钟才能完成。</span><span class="sxs-lookup"><span data-stu-id="2290c-217">The process to create a service application could take several minutes to complete.</span></span> <span data-ttu-id="2290c-218">当它完成时，将显示确认消息和一个指向 **“设置订阅和警报”** 页的链接。</span><span class="sxs-lookup"><span data-stu-id="2290c-218">When it is complete, you will see a confirmation message and a link to a **Provision Subscriptions and Alerts** page.</span></span> <span data-ttu-id="2290c-219">如果您要使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 订阅和警报功能，请完成该设置步骤。</span><span class="sxs-lookup"><span data-stu-id="2290c-219">Complete the provision step if you want to use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] subscriptions and alerts features.</span></span> <span data-ttu-id="2290c-220">有关详细信息，请参阅[用于 SSRS 服务应用程序的设置订阅和警报](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="2290c-220">For more information, see [Provision Subscriptions and Alerts for SSRS Service Applications](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md).</span></span>  
  
 <span data-ttu-id="2290c-221">![与 PowerShell 相关的内容](../../../2014/reporting-services/media/rs-powershellicon.jpg "PowerShell 相关内容")有关使用 PowerShell 创建 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务应用程序的信息，请参阅[使用 powershell 创建 Reporting Services 服务应用程序](../../../2014/reporting-services/reporting-services-sharepoint-service-and-service-applications.md#bkmk_powershell_create_ssrs_serviceapp)。</span><span class="sxs-lookup"><span data-stu-id="2290c-221">![PowerShell related content](../../../2014/reporting-services/media/rs-powershellicon.jpg "PowerShell related content") For information on using PowerShell to create a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application, see [To create a Reporting Services Service Application using PowerShell](../../../2014/reporting-services/reporting-services-sharepoint-service-and-service-applications.md#bkmk_powershell_create_ssrs_serviceapp).</span></span>  
  

  
##  <a name="activate-the-power-view-site-collection-feature"></a><a name="bkmk_powerview"></a><span data-ttu-id="2290c-222">激活 "Power View 网站集" 功能。</span><span class="sxs-lookup"><span data-stu-id="2290c-222">Activate the Power View Site Collection Feature.</span></span>  
 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]<span data-ttu-id="2290c-223">（ [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 适用于 Enterprise Edition 的外接程序的一项功能 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] ）是一个网站集功能。</span><span class="sxs-lookup"><span data-stu-id="2290c-223">, a feature of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in for [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[SPS2010](../../includes/sps2010-md.md)] Enterprise Edition, is a site collection feature.</span></span> <span data-ttu-id="2290c-224">自动为根网站集和安装 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 外接程序后创建的网站集激活该功能。</span><span class="sxs-lookup"><span data-stu-id="2290c-224">The feature is activated automatically for root site collections and site collections created after the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in is installed.</span></span> <span data-ttu-id="2290c-225">如果您计划使用 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]，请验证已激活该功能。</span><span class="sxs-lookup"><span data-stu-id="2290c-225">If you plan to use [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], verify that the feature is activated.</span></span>  
  
 <span data-ttu-id="2290c-226">如果在安装 SharePoint 2010 产品后安装了用于 SharePoint 2010 产品的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 外接程序，则仅对根网站集激活报表服务器集成功能和 Power View 集成功能。</span><span class="sxs-lookup"><span data-stu-id="2290c-226">If you install the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in for SharePoint 2010 Products after the installation of the SharePoint 2010 product, then the Report Server integration feature and the Power View integration feature will only be activated for root site collections.</span></span> <span data-ttu-id="2290c-227">对于其他网站集，请手动激活这些功能。</span><span class="sxs-lookup"><span data-stu-id="2290c-227">For other site collections, manually activate the features.</span></span>  
  
#### <a name="to-activate-the-power-view-feature"></a><span data-ttu-id="2290c-228">激活 Power View 功能</span><span class="sxs-lookup"><span data-stu-id="2290c-228">To Activate the Power View Feature</span></span>  
  
1.  <span data-ttu-id="2290c-229">打开浏览器找到所需的 SharePoint 网站。</span><span class="sxs-lookup"><span data-stu-id="2290c-229">Open your browser to the desired SharePoint site.</span></span>  
  
2.  <span data-ttu-id="2290c-230">单击 **“网站操作”** 。</span><span class="sxs-lookup"><span data-stu-id="2290c-230">Click **Site Actions**.</span></span>  
  
3.  <span data-ttu-id="2290c-231">单击 **“网站设置”** 。</span><span class="sxs-lookup"><span data-stu-id="2290c-231">Click **Site Settings**.</span></span>  
  
4.  <span data-ttu-id="2290c-232">在网站集管理组中单击 **“网站集功能”** 。</span><span class="sxs-lookup"><span data-stu-id="2290c-232">Click **Site Collection Features** in the Site Collection Administration Group.</span></span>  
  
5.  <span data-ttu-id="2290c-233">在列表中找到 **“Power View 集成功能”** 。</span><span class="sxs-lookup"><span data-stu-id="2290c-233">Find **Power View Integration Feature** in the list.</span></span>  
  
6.  <span data-ttu-id="2290c-234">单击“激活”  。</span><span class="sxs-lookup"><span data-stu-id="2290c-234">Click **Activate**.</span></span>  
  
 <span data-ttu-id="2290c-235">将对每个网站集完成此过程。</span><span class="sxs-lookup"><span data-stu-id="2290c-235">This procedure is completed per site collection.</span></span> <span data-ttu-id="2290c-236">有关详细信息，请参阅[在 SharePoint 中激活报表服务器和 Power View 集成功能](../../reporting-services/activate-the-report-server-and-power-view-integration-features-in-sharepoint.md)。</span><span class="sxs-lookup"><span data-stu-id="2290c-236">For more information, see [Activate the Report Server and Power View Integration Features in SharePoint](../../reporting-services/activate-the-report-server-and-power-view-integration-features-in-sharepoint.md)  .</span></span>  
  
##  <a name="additional-configuration"></a><a name="bkmk_additional_config"></a><span data-ttu-id="2290c-237">其他配置</span><span class="sxs-lookup"><span data-stu-id="2290c-237">Additional Configuration</span></span>  
 <span data-ttu-id="2290c-238">本部分介绍在大多数 SharePoint 部署中很重要的其他配置步骤。</span><span class="sxs-lookup"><span data-stu-id="2290c-238">This section describes additional configuration steps that are important in most SharePoint deployments.</span></span>  
  
###  <a name="provision-subscriptions-and-alerts"></a><a name="bkmk_provision_agent"></a><span data-ttu-id="2290c-239">设置订阅和警报</span><span class="sxs-lookup"><span data-stu-id="2290c-239">Provision Subscriptions and Alerts</span></span>  
 <span data-ttu-id="2290c-240">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 订阅和数据警报功能可能要求配置 SQL Server 代理权限。</span><span class="sxs-lookup"><span data-stu-id="2290c-240">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] subscription and data alert features may require the configuration of SQL Server Agent permissions.</span></span> <span data-ttu-id="2290c-241">如果您看到指示“需要 SQL Server 代理”的错误消息，而您已验证 SQL Server 代理正在运行，则应更新权限。</span><span class="sxs-lookup"><span data-stu-id="2290c-241">If you see an error message that indicates SQL Server Agent is required and you have verified SQL Server Agent is running, update the permissions.</span></span> <span data-ttu-id="2290c-242">您可以在“创建服务应用程序成功”页上单击链接 **“设置订阅和警报”** ，以便转到其他页来设置 SQL Server 代理。</span><span class="sxs-lookup"><span data-stu-id="2290c-242">You can click the link **Provision Subscriptions and Alerts** on the create service application success page to go to another page for provisioning SQL Server Agent.</span></span> <span data-ttu-id="2290c-243">如果您的部署是跨计算机边界的部署（例如，当 SQL Server 数据库实例位于其他计算机上时），会需要此设置步骤。</span><span class="sxs-lookup"><span data-stu-id="2290c-243">The provision step is needed if your deployment crosses machine boundaries, for example when the SQL Server database instance is on a different machine.</span></span> <span data-ttu-id="2290c-244">有关详细信息，请参阅[为 SSRS 服务应用程序设置订阅和警报](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md)</span><span class="sxs-lookup"><span data-stu-id="2290c-244">For more information, see [Provision Subscriptions and Alerts for SSRS Service Applications](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md)</span></span>  
  

  
### <a name="configure-e-mail-for-a-service-application"></a><span data-ttu-id="2290c-245">为服务应用程序配置电子邮件</span><span class="sxs-lookup"><span data-stu-id="2290c-245">Configure e-mail for a service application</span></span>  
 <span data-ttu-id="2290c-246">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 数据警报功能会在电子邮件中发送警报。</span><span class="sxs-lookup"><span data-stu-id="2290c-246">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] data alerts feature sends alerts in e-mail messages.</span></span> <span data-ttu-id="2290c-247">若要发送电子邮件，您可能需要配置 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务应用程序，并可能需要修改该服务应用程序的电子邮件传递扩展插件。</span><span class="sxs-lookup"><span data-stu-id="2290c-247">To send e-mail you may need to configure your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application and you may need to modify the e-mail delivery extension for the service application.</span></span> <span data-ttu-id="2290c-248">如果您计划将电子邮件传递扩展插件用于 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 订阅功能，则需要进行电子邮件设置。</span><span class="sxs-lookup"><span data-stu-id="2290c-248">If you plan to use the e-mail delivery extension for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] subscription feature, the e-mail settings are required.</span></span> <span data-ttu-id="2290c-249">有关详细信息，请参阅[为 Reporting Services 服务应用程序配置电子邮件（SharePoint 2010 和 SharePoint 2013）](../../reporting-services/install-windows/configure-e-mail-for-a-reporting-services-service-application.md)</span><span class="sxs-lookup"><span data-stu-id="2290c-249">For more information, see [Configure E-mail for a Reporting Services Service Application &#40;SharePoint 2010 and SharePoint 2013&#41;](../../reporting-services/install-windows/configure-e-mail-for-a-reporting-services-service-application.md)</span></span>  
  

  
### <a name="add-reporting-services-content-types"></a><span data-ttu-id="2290c-250">添加 Reporting Services 内容类型</span><span class="sxs-lookup"><span data-stu-id="2290c-250">Add Reporting Services Content Types</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="2290c-251">提供预定义的内容类型，用于管理共享数据源 (.rsds) 文件、报表模型 (.smdl) 和报表生成器报表定义 (.rdl) 文件。</span><span class="sxs-lookup"><span data-stu-id="2290c-251">provides predefined content types that are used to manage shared data source (.rsds) files, report models (.smdl), and Report Builder report definition (.rdl) files.</span></span> <span data-ttu-id="2290c-252">将 **“报表生成器报表”**、 **“报表模型”** 和 **“报表数据源”** 内容类型添加到库中将启用 **“新建”** 命令，以便创建对应类型的新文档。</span><span class="sxs-lookup"><span data-stu-id="2290c-252">Adding a **Report Builder Report**, **Report Model**, and **Report Data Source** content type to a library enables the **New** command so that you can create new documents of that type.</span></span> <span data-ttu-id="2290c-253">有关详细信息，请参阅[将报表服务器内容类型添加到库 &#40;Reporting Services 在 SharePoint 集成模式下&#41;" ](../../../2014/reporting-services/add-reporting-services-content-types-to-a-sharepoint-library.md)。</span><span class="sxs-lookup"><span data-stu-id="2290c-253">For more information, see [Add Report Server Content Types to a Library &#40;Reporting Services in SharePoint Integrated Mode&#41;](../../../2014/reporting-services/add-reporting-services-content-types-to-a-sharepoint-library.md).</span></span>  
  

  
### <a name="activate-the-file-sync-feature"></a><span data-ttu-id="2290c-254">激活文件同步功能</span><span class="sxs-lookup"><span data-stu-id="2290c-254">Activate the File sync feature</span></span>  
 <span data-ttu-id="2290c-255">如果用户经常直接将已发布的报表项上载到 SharePoint 文档库，则报表服务器文件同步功能将很有用。</span><span class="sxs-lookup"><span data-stu-id="2290c-255">If users will frequently upload published report items directly to SharePoint document libraries, the report server file sync feature will be beneficial.</span></span> <span data-ttu-id="2290c-256">文件同步功能将更频繁地将报表服务器目录与文档库中的项进行同步。</span><span class="sxs-lookup"><span data-stu-id="2290c-256">The file sync feature will synchronize the report server catalog with items in document libraries on a more frequent basis.</span></span> <span data-ttu-id="2290c-257">有关详细信息，请参阅[在 SharePoint 管理中心中激活报表服务器文件同步功能](../../../2014/reporting-services/activate-report-server-file-sync-feature-sharepoint-central-administration.md)。</span><span class="sxs-lookup"><span data-stu-id="2290c-257">For more information, see [Activate the Report Server File Sync Feature in SharePoint Central Administration](../../../2014/reporting-services/activate-report-server-file-sync-feature-sharepoint-central-administration.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2290c-258">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2290c-258">See Also</span></span>  
 <span data-ttu-id="2290c-259">[Reporting Services SharePoint 模式的 PowerShell cmdlet](../../../2014/reporting-services/powershell-cmdlets-for-reporting-services-sharepoint-mode.md) </span><span class="sxs-lookup"><span data-stu-id="2290c-259">[PowerShell cmdlets for Reporting Services SharePoint Mode](../../../2014/reporting-services/powershell-cmdlets-for-reporting-services-sharepoint-mode.md) </span></span>  
 <span data-ttu-id="2290c-260">[SQL Server 2012 的各个版本支持的功能](https://go.microsoft.com/fwlink/?linkid=232473) </span><span class="sxs-lookup"><span data-stu-id="2290c-260">[Features Supported by the Editions of SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473) </span></span>  
 [<span data-ttu-id="2290c-261">Reporting Services SharePoint 服务和服务应用程序</span><span class="sxs-lookup"><span data-stu-id="2290c-261">Reporting Services SharePoint Service and Service Applications</span></span>](../../../2014/reporting-services/reporting-services-sharepoint-service-and-service-applications.md)  
