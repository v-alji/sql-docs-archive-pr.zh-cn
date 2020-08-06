---
title: Reporting Services SharePoint 模式下 (配置和管理报表服务器) |Microsoft Docs
ms.custom: ''
ms.date: 11/25/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 846e86d0-fbbb-426c-97f9-f179cd42b390
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ce7c1f524eec4785ddbc25d95c641d070ecbf408
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692799"
---
# <a name="configuration-and-administration-of-a-report-server-reporting-services-sharepoint-mode"></a><span data-ttu-id="038b4-102">配置和管理报表服务器（Reporting Services SharePoint 模式）</span><span class="sxs-lookup"><span data-stu-id="038b4-102">Configuration and Administration of a Report Server (Reporting Services SharePoint Mode)</span></span>
  [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="038b4-103">[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 是一种基于服务器的报表平台，它提供了各种现成可用的工具和服务，可帮助您创建、部署和管理组织的报表，以及使您能够扩展和自定义报表功能的编程功能。</span><span class="sxs-lookup"><span data-stu-id="038b4-103">[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] is a server-based reporting platform that provides a full range of ready-to-use tools and services to help you create, deploy, and manage reports for your organization, as well as programming features that enable you to extend and customize your reporting functionality.</span></span> <span data-ttu-id="038b4-104">您可以将您的报表环境与 SharePoint 产品相集成，体验使用 SharePoint 站点提供的协作环境所带来的好处。</span><span class="sxs-lookup"><span data-stu-id="038b4-104">You can integrate your reporting environment with a SharePoint product to experience the benefits of using the collaborative environment provided by SharePoint sites.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="038b4-105">本节内容</span><span class="sxs-lookup"><span data-stu-id="038b4-105">In this section</span></span>  
 <span data-ttu-id="038b4-106">以下各节中的内容可以帮助您理解与将 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 环境与 SharePoint 产品或技术相集成有关的概念、部署方案、过程等等：</span><span class="sxs-lookup"><span data-stu-id="038b4-106">Use the following sections to help you understand concepts, deployment scenarios, procedures, and more for integrating your [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] environment with a SharePoint product or technology:</span></span>  
  
-   <span data-ttu-id="038b4-107">SharePoint 文档库中的菜单选项</span><span class="sxs-lookup"><span data-stu-id="038b4-107">Menu options in a SharePoint document library</span></span>  
  
    -   [<span data-ttu-id="038b4-108">SharePoint 用户的数据警报管理器</span><span class="sxs-lookup"><span data-stu-id="038b4-108">Data Alert Manager for SharePoint Users</span></span>](../../2014/reporting-services/data-alert-manager-for-sharepoint-users.md)  
  
    -   [<span data-ttu-id="038b4-109">创建和管理 SharePoint 模式报表服务器的订阅</span><span class="sxs-lookup"><span data-stu-id="038b4-109">Create and Manage Subscriptions for SharePoint Mode Report Servers</span></span>](subscriptions/create-and-manage-subscriptions-for-sharepoint-mode-report-servers.md)  
  
    -   [<span data-ttu-id="038b4-110">从 SharePoint 站点更新报表数据源的凭据</span><span class="sxs-lookup"><span data-stu-id="038b4-110">Update Credentials in Report Data Sources from a SharePoint Site</span></span>](report-data/update-credentials-in-report-data-sources-from-a-sharepoint-site.md)  
  
    -   [<span data-ttu-id="038b4-111">管理共享数据集</span><span class="sxs-lookup"><span data-stu-id="038b4-111">Manage Shared Datasets</span></span>](report-data/manage-shared-datasets.md)  
  
    -   [<span data-ttu-id="038b4-112">设置已发布报表的参数（SharePoint 集成模式下的 Reporting Services）</span><span class="sxs-lookup"><span data-stu-id="038b4-112">Set Parameters on a Published Report &#40;Reporting Services in SharePoint Integrated Mode&#41;</span></span>](report-design/set-parameters-on-a-published-report-sharepoint-integrated-mode.md)  
  
    -   [<span data-ttu-id="038b4-113">设置处理选项（SharePoint 集成模式下的 Reporting Services）</span><span class="sxs-lookup"><span data-stu-id="038b4-113">Set Processing Options &#40;Reporting Services in SharePoint Integrated Mode&#41;</span></span>](../../2014/reporting-services/set-processing-options-reporting-services-in-sharepoint-integrated-mode.md)  
  
    -   [<span data-ttu-id="038b4-114">缓存刷新选项（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="038b4-114">Cache Refresh Options &#40;Report Manager&#41;</span></span>](../../2014/reporting-services/cache-refresh-options-report-manager.md)  
  
-   [<span data-ttu-id="038b4-115">Reporting Services 网站集功能</span><span class="sxs-lookup"><span data-stu-id="038b4-115">Reporting Services Site Collection Features</span></span>](../../2014/reporting-services/reporting-services-site-collection-features.md)  
  
-   [<span data-ttu-id="038b4-116">在 SharePoint 中激活报表服务器和 Power View 集成功能</span><span class="sxs-lookup"><span data-stu-id="038b4-116">Activate the Report Server and Power View Integration Features in SharePoint</span></span>](activate-the-report-server-and-power-view-integration-features-in-sharepoint.md)  
  
-   [<span data-ttu-id="038b4-117">Reporting Services 网站设置和网站功能（SharePoint 模式）</span><span class="sxs-lookup"><span data-stu-id="038b4-117">Reporting Services Site Settings and Site Features&#40;SharePoint Mode&#41;</span></span>](../../2014/reporting-services/reporting-services-site-settings-and-site-features-sharepoint-mode.md)  
  
-   [<span data-ttu-id="038b4-118">在 SharePoint 管理中心中激活报表服务器文件同步功能</span><span class="sxs-lookup"><span data-stu-id="038b4-118">Activate the Report Server File Sync Feature in SharePoint Central Administration</span></span>](../../2014/reporting-services/activate-report-server-file-sync-feature-sharepoint-central-administration.md)  
  
-   [<span data-ttu-id="038b4-119">将报表服务器内容类型添加到 SharePoint 集成模式下的库 &#40;Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="038b4-119">Add Report Server Content Types to a Library &#40;Reporting Services in SharePoint Integrated Mode&#41;</span></span>](../../2014/reporting-services/add-reporting-services-content-types-to-a-sharepoint-library.md)  
  
-   [<span data-ttu-id="038b4-120">报表查看器中的本地模式和报表查看器中的连接模式报表（SharePoint 模式下的 Reporting Services）</span><span class="sxs-lookup"><span data-stu-id="038b4-120">Local Mode vs. Connected Mode Reports in the Report Viewer &#40;Reporting Services in SharePoint Mode&#41;</span></span>](../../2014/reporting-services/local-vs-connected-mode-report-viewer-reporting-services-sharepoint-mode.md)  
  
-   [<span data-ttu-id="038b4-121">将文档上传到 SharePoint 库（SharePoint 模式下的 Reporting Services）</span><span class="sxs-lookup"><span data-stu-id="038b4-121">Upload Documents to a SharePoint Library &#40;Reporting Services in SharePoint Mode&#41;</span></span>](../../2014/reporting-services/upload-documents-to-a-sharepoint-library-reporting-services-in-sharepoint-mode.md)  
  
-   [<span data-ttu-id="038b4-122">设置处理选项（SharePoint 集成模式下的 Reporting Services）</span><span class="sxs-lookup"><span data-stu-id="038b4-122">Set Processing Options &#40;Reporting Services in SharePoint Integrated Mode&#41;</span></span>](../../2014/reporting-services/set-processing-options-reporting-services-in-sharepoint-integrated-mode.md)  
  
 <span data-ttu-id="038b4-123">有关 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 的一般信息，请参阅 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 联机丛书中的 [ Reporting Services (SSRS) ](create-deploy-and-manage-mobile-and-paginated-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="038b4-123">For more general information about [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], see [Reporting Services &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md) in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Books Online.</span></span> <span data-ttu-id="038b4-124">有关其他 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 组件、工具和资源的信息，请参阅 [SQL Server 联机丛书](../index.yml)。</span><span class="sxs-lookup"><span data-stu-id="038b4-124">For information about other [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] components, tools, and resources, see [SQL Server Books Online](../index.yml).</span></span>  
  
  
