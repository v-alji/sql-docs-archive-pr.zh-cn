---
title: Reporting Services sharepoint 模式安装 (SharePoint 2010 和 SharePoint 2013) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- default configuration [Reporting Services]
- installing Reporting Services, SharePoint integrated mode
- installation options [Reporting Services]
ms.assetid: ac6cba68-2665-4a39-8fa3-cb7d7e6723c0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c27b6f9fbeebcc896b1a6097cb51e8d2e15924bf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578029"
---
# <a name="reporting-services-sharepoint-mode-installation-sharepoint-2010-and-sharepoint-2013"></a><span data-ttu-id="63b4e-102">Reporting Services SharePoint 模式安装（SharePoint 2010 和 SharePoint 2013）</span><span class="sxs-lookup"><span data-stu-id="63b4e-102">Reporting Services SharePoint Mode Installation (SharePoint 2010 and SharePoint 2013)</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]<span data-ttu-id="63b4e-103">在 SharePoint 模式下，提供基于 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 SharePoint 产品的报表生成和传递的服务器组件集合 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="63b4e-103">in SharePoint mode is a collection of server components that provide report generation and delivery, based on [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and [!INCLUDE[msCoName](../../includes/msconame-md.md)] SharePoint products.</span></span>  
  
 <span data-ttu-id="63b4e-104">在 SharePoint 模式下运行 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 提供 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] 和数据警报功能。</span><span class="sxs-lookup"><span data-stu-id="63b4e-104">Running [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint mode provides the [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] and data alerting features.</span></span> <span data-ttu-id="63b4e-105">有关 SharePoint 模式下的功能的详细信息，请参阅[Reporting Services 报表服务器](../reporting-services-report-server.md)中的 "按服务器模式的功能支持和行为差异" 部分</span><span class="sxs-lookup"><span data-stu-id="63b4e-105">For more information regarding features in SharePoint mode, see the section "Feature Support and Behavior Differences by Server Mode" in [Reporting Services Report Server](../reporting-services-report-server.md)</span></span>  
  
 <span data-ttu-id="63b4e-106">对于 SharePoint 模式下的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]，需要两个基本安装：</span><span class="sxs-lookup"><span data-stu-id="63b4e-106">There are two fundamental installations needed for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint mode:</span></span>  
  
|<span data-ttu-id="63b4e-107">安装</span><span class="sxs-lookup"><span data-stu-id="63b4e-107">Installation</span></span>|<span data-ttu-id="63b4e-108">说明</span><span class="sxs-lookup"><span data-stu-id="63b4e-108">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="63b4e-109">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 用于 SharePoint 产品的外接程序。</span><span class="sxs-lookup"><span data-stu-id="63b4e-109">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in for SharePoint products.</span></span>|<span data-ttu-id="63b4e-110">该外接程序在 SharePoint Web 前端服务器上安装 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 用户界面 (UI) 页和功能。</span><span class="sxs-lookup"><span data-stu-id="63b4e-110">The add-in installs the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] user interface (UI) pages and features on a SharePoint web front-end server.</span></span> <span data-ttu-id="63b4e-111">UI 功能包括 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]、SharePoint 管理中心中的管理页、在 SharePoint 文档库内使用的功能页以及 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 数据警报页。</span><span class="sxs-lookup"><span data-stu-id="63b4e-111">The UI features include [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], administration pages in SharePoint Central Administration, feature pages used within SharePoint document libraries, and [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Data Alerting pages.</span></span>|  
|<span data-ttu-id="63b4e-112">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 在 SharePoint 模式下安装的 Report Server</span><span class="sxs-lookup"><span data-stu-id="63b4e-112">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server installed in SharePoint Mode</span></span>|<span data-ttu-id="63b4e-113">该报表服务器处理数据和报表处理和呈现以及订阅和数据警报处理。</span><span class="sxs-lookup"><span data-stu-id="63b4e-113">The report server handles the data and report processing and rendering as well subscription and Data Alert processing.</span></span> <span data-ttu-id="63b4e-114">SharePoint 模式报表服务器构建并安装为 SharePoint 共享服务。</span><span class="sxs-lookup"><span data-stu-id="63b4e-114">The SharePoint mode report server is architected and installed as a SharePoint Shared Service.</span></span>|  
  
 <span data-ttu-id="63b4e-115">若要安装 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]，请使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 安装介质。</span><span class="sxs-lookup"><span data-stu-id="63b4e-115">To install [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], use the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] installation media.</span></span>  
  
 <span data-ttu-id="63b4e-116">有关高级部署方案的说明，请参阅[部署清单： Reporting Services、Power View 和 PowerPivot for SharePoint](../../sql-server/install/deployment-checklist-reporting-services-power-view-power-pivot-for-sharepoint.md)和[部署清单：将 Reporting Services 安装到现有的 SharePoint 场](../../sql-server/install/deployment-checklist-install-reporting-services-existing-sharepoint-farm.md)中。</span><span class="sxs-lookup"><span data-stu-id="63b4e-116">For instructions on advanced deployment scenarios, see [Deployment Checklist: Reporting Services, Power View, and PowerPivot for SharePoint](../../sql-server/install/deployment-checklist-reporting-services-power-view-power-pivot-for-sharepoint.md) and [Deployment Checklist: Install Reporting Services into an Existing SharePoint Farm](../../sql-server/install/deployment-checklist-install-reporting-services-existing-sharepoint-farm.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="63b4e-117">本节内容</span><span class="sxs-lookup"><span data-stu-id="63b4e-117">In This Section</span></span>  
 [<span data-ttu-id="63b4e-118">支持的 SharePoint 和 Reporting Services Server 和外接程序的组合 &#40;SQL Server 2014&#41;</span><span class="sxs-lookup"><span data-stu-id="63b4e-118">Supported Combinations of SharePoint and Reporting Services Server and Add-in &#40;SQL Server 2014&#41;</span></span>](supported-combinations-of-sharepoint-and-reporting-services-server.md)  
  
 [<span data-ttu-id="63b4e-119">安装用于 SharePoint 2013 的 Reporting Services SharePoint 模式</span><span class="sxs-lookup"><span data-stu-id="63b4e-119">Install Reporting Services SharePoint Mode for SharePoint 2013</span></span>](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md)  
  
 [<span data-ttu-id="63b4e-120">安装 SharePoint 2010 Reporting Services SharePoint 模式</span><span class="sxs-lookup"><span data-stu-id="63b4e-120">Install Reporting Services SharePoint Mode for SharePoint 2010</span></span>](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)  
  
 [<span data-ttu-id="63b4e-121">安装或卸载用于 SharePoint 的 Reporting Services 外接程序 &#40;SharePoint 2010 和 SharePoint 2013&#41;</span><span class="sxs-lookup"><span data-stu-id="63b4e-121">Install or Uninstall the Reporting Services Add-in for SharePoint &#40;SharePoint 2010 and SharePoint 2013&#41;</span></span>](install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
 [<span data-ttu-id="63b4e-122">在何处查找用于 SharePoint 产品的 Reporting Services 外接程序</span><span class="sxs-lookup"><span data-stu-id="63b4e-122">Where to find the Reporting Services add-in for SharePoint Products</span></span>](where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)  
  
 [<span data-ttu-id="63b4e-123">向场中添加另一个报表服务器（SSRS 扩展）</span><span class="sxs-lookup"><span data-stu-id="63b4e-123">Add an Additional Report Server to a Farm &#40;SSRS Scale-out&#41;</span></span>](add-an-additional-report-server-to-a-farm-ssrs-scale-out.md)  
  
 [<span data-ttu-id="63b4e-124">向场中添加另一个 Reporting Services Web 前端</span><span class="sxs-lookup"><span data-stu-id="63b4e-124">Add an Additional Reporting Services Web Front-end to a Farm</span></span>](add-an-additional-reporting-services-web-front-end-to-a-farm.md)  
  
 [<span data-ttu-id="63b4e-125">为 Reporting Services 服务应用程序配置电子邮件（SharePoint 2010 和 SharePoint 2013）</span><span class="sxs-lookup"><span data-stu-id="63b4e-125">Configure E-mail for a Reporting Services Service Application &#40;SharePoint 2010 and SharePoint 2013&#41;</span></span>](configure-e-mail-for-a-reporting-services-service-application.md)  
  
 [<span data-ttu-id="63b4e-126">用于 SSRS 服务应用程序的设置订阅和警报</span><span class="sxs-lookup"><span data-stu-id="63b4e-126">Provision Subscriptions and Alerts for SSRS Service Applications</span></span>](provision-subscriptions-and-alerts-for-ssrs-service-applications.md)  
  
 [<span data-ttu-id="63b4e-127">声明到 Windows 令牌服务 &#40;C2WTS&#41; 和 Reporting Services</span><span class="sxs-lookup"><span data-stu-id="63b4e-127">Claims to Windows Token Service &#40;C2WTS&#41; and Reporting Services</span></span>](../../sql-server/install/claims-to-windows-token-service-c2wts-and-reporting-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="63b4e-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="63b4e-128">See Also</span></span>  
 <span data-ttu-id="63b4e-129">[数据警报体系结构和工作流](../reporting-services-data-alerts.md#AlertingWF) </span><span class="sxs-lookup"><span data-stu-id="63b4e-129">[Data Alerts Architecture and Workflow](../reporting-services-data-alerts.md#AlertingWF) </span></span>  
 [<span data-ttu-id="63b4e-130">向管理员提出警报的数据警报管理器</span><span class="sxs-lookup"><span data-stu-id="63b4e-130">Data Alert Manager for Alerting Administrators</span></span>](../data-alert-manager-for-alerting-administrators.md)  
  
  
