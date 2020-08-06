---
title: Reporting Services (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 11/25/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services]
- SSRS
- reports [Reporting Services], about reports
- Reporting Services
- SQL Server Reporting Services
ms.assetid: b8d18d3d-9db0-43e7-8286-7b46cc3a37ed
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0418acaab54032148f4bc6d42d06c97070b89e1e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682752"
---
# <a name="reporting-services-ssrs"></a><span data-ttu-id="7bde1-102">Reporting Services (SSRS)</span><span class="sxs-lookup"><span data-stu-id="7bde1-102">Reporting Services (SSRS)</span></span>
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]<span data-ttu-id="7bde1-103">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]提供各种现成可用的工具和服务，帮助您创建、部署和管理组织的报表。</span><span class="sxs-lookup"><span data-stu-id="7bde1-103">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] provides a full range of ready-to-use tools and services to help you create, deploy, and manage reports for your organization.</span></span> [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="7bde1-104">中包括了很多可用于扩展和自定义报告功能的编程特性。</span><span class="sxs-lookup"><span data-stu-id="7bde1-104">includes programming features that enable you to extend and customize your reporting functionality.</span></span>

 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]<span data-ttu-id="7bde1-105">是一个基于服务器的报表平台，它为各种数据源提供综合性报表功能。</span><span class="sxs-lookup"><span data-stu-id="7bde1-105">is a server-based reporting platform that provides comprehensive reporting functionality for a variety of data sources.</span></span> [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]<span data-ttu-id="7bde1-106">包括一组完整的工具，可用于创建、管理和传递报表，以及允许开发人员在自定义应用程序中集成或扩展数据和报表处理的 Api。</span><span class="sxs-lookup"><span data-stu-id="7bde1-106">includes a complete set of tools for you to create, manage, and deliver reports, and APIs that enable developers to integrate or extend data and report processing in custom applications.</span></span> [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]<span data-ttu-id="7bde1-107">工具在环境中工作 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ，并与 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 工具和组件完全集成。</span><span class="sxs-lookup"><span data-stu-id="7bde1-107">tools work within the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] environment and are fully integrated with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] tools and components.</span></span>

 <span data-ttu-id="7bde1-108">使用 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]，可以从关系数据源、多维数据源和基于 XML 的数据源创建交互式、表格式、图形式或自由格式的报表。</span><span class="sxs-lookup"><span data-stu-id="7bde1-108">With [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], you can create interactive, tabular, graphical, or free-form reports from relational, multidimensional, or XML-based data sources.</span></span> <span data-ttu-id="7bde1-109">报表可以包含丰富的数据可视化内容，包括图表、地图和迷你图。</span><span class="sxs-lookup"><span data-stu-id="7bde1-109">Reports can include rich data visualization, including charts, maps, and sparklines.</span></span> <span data-ttu-id="7bde1-110">您可以发布报表、计划报表处理或按需访问报表。</span><span class="sxs-lookup"><span data-stu-id="7bde1-110">You can publish reports, schedule report processing, or access reports on-demand.</span></span> <span data-ttu-id="7bde1-111">您可以选择多种查看格式、将报表导出到其他应用程序（如 [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)]）以及订阅已发布的报表。</span><span class="sxs-lookup"><span data-stu-id="7bde1-111">You can select from a variety of viewing formats, export reports to other applications such as [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)], and subscribe to published reports.</span></span> <span data-ttu-id="7bde1-112">您创建的报表既可以通过基于 Web 的连接来查看，也可以作为 [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows 应用程序或 SharePoint 站点的一部分来查看。</span><span class="sxs-lookup"><span data-stu-id="7bde1-112">The reports that you create can be viewed over a Web-based connection or as part of a [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows application or SharePoint site.</span></span> <span data-ttu-id="7bde1-113">您还可以在发布到 SharePoint 站点的报表上创建数据警报并在报表数据更改时接收电子邮件。</span><span class="sxs-lookup"><span data-stu-id="7bde1-113">You can also create data alerts on reports published to a SharePoint site and receive email messages when report data changes.</span></span>

 <span data-ttu-id="7bde1-114">有关中新增功能的详细信息 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ，请参阅[&#41;的新 &#40;Reporting Services ](../../2014/reporting-services/what-s-new-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="7bde1-114">For more information about features new in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], see [What's New &#40;Reporting Services&#41;](../../2014/reporting-services/what-s-new-reporting-services.md).</span></span>

 <span data-ttu-id="7bde1-115">有关其他 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 组件、工具和资源的信息，请参阅 [SQL Server 联机丛书](../index.yml)。</span><span class="sxs-lookup"><span data-stu-id="7bde1-115">For information about other [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] components, tools, and resources, see [SQL Server Books Online](../index.yml).</span></span>

 <span data-ttu-id="7bde1-116">[Reporting Services 报表服务器](../../2014/reporting-services/reporting-services-report-server.md)**按区域文件夹浏览内容**![图标](media/hlp-16folder.gif "文件夹图标")</span><span class="sxs-lookup"><span data-stu-id="7bde1-116">**Browse Content by Area** ![Folder icon](media/hlp-16folder.gif "Folder icon") [Reporting Services Report Server](../../2014/reporting-services/reporting-services-report-server.md)</span></span>

 <span data-ttu-id="7bde1-117">[&#40;SSRS Reporting Services 报表](reports/reporting-services-reports-ssrs.md)的![文件夹图标](media/hlp-16folder.gif "文件夹图标")&#41;</span><span class="sxs-lookup"><span data-stu-id="7bde1-117">![Folder icon](media/hlp-16folder.gif "Folder icon") [Reporting Services Reports &#40;SSRS&#41;](reports/reporting-services-reports-ssrs.md)</span></span>

 <span data-ttu-id="7bde1-118">![文件夹图标](media/hlp-16folder.gif "文件夹图标")[报表数据 &#40;SSRS&#41;](report-data/report-data-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="7bde1-118">![Folder icon](media/hlp-16folder.gif "Folder icon") [Report Data &#40;SSRS&#41;](report-data/report-data-ssrs.md)</span></span>

 <span data-ttu-id="7bde1-119">![文件夹图标](media/hlp-16folder.gif "文件夹图标")[报表参数 &#40;报表生成器和报表设计器&#41;](report-design/report-parameters-report-builder-and-report-designer.md)</span><span class="sxs-lookup"><span data-stu-id="7bde1-119">![Folder icon](media/hlp-16folder.gif "Folder icon") [Report Parameters &#40;Report Builder and Report Designer&#41;](report-design/report-parameters-report-builder-and-report-designer.md)</span></span>

 <span data-ttu-id="7bde1-120">![文件夹图标](media/hlp-16folder.gif "文件夹图标")[报表部分报表设计器 &#40;SSRS&#41;](report-design/report-parts-in-report-designer-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="7bde1-120">![Folder icon](media/hlp-16folder.gif "Folder icon") [Report Parts in Report Designer &#40;SSRS&#41;](report-design/report-parts-in-report-designer-ssrs.md)</span></span>

 <span data-ttu-id="7bde1-121">![文件夹图标](media/hlp-16folder.gif "文件夹图标")[计划](subscriptions/schedules.md)</span><span class="sxs-lookup"><span data-stu-id="7bde1-121">![Folder icon](media/hlp-16folder.gif "Folder icon") [Schedules](subscriptions/schedules.md)</span></span>

 <span data-ttu-id="7bde1-122">![文件夹图标](media/hlp-16folder.gif "文件夹图标")[订阅和传递 &#40;Reporting Services&#41;](subscriptions/subscriptions-and-delivery-reporting-services.md)</span><span class="sxs-lookup"><span data-stu-id="7bde1-122">![Folder icon](media/hlp-16folder.gif "Folder icon") [Subscriptions and Delivery &#40;Reporting Services&#41;](subscriptions/subscriptions-and-delivery-reporting-services.md)</span></span>

 <span data-ttu-id="7bde1-123">![文件夹图标](media/hlp-16folder.gif "文件夹图标") [Reporting Services 数据警报](../ssms/agent/alerts.md)</span><span class="sxs-lookup"><span data-stu-id="7bde1-123">![Folder icon](media/hlp-16folder.gif "Folder icon") [Reporting Services Data Alerts](../ssms/agent/alerts.md)</span></span>

 <span data-ttu-id="7bde1-124">![文件夹图标](media/hlp-16folder.gif "文件夹图标") [Power View](https://office.microsoft.com/excel-help/power-view-explore-visualize-and-present-your-data-HA102835634.aspx)</span><span class="sxs-lookup"><span data-stu-id="7bde1-124">![Folder icon](media/hlp-16folder.gif "Folder icon") [Power View](https://office.microsoft.com/excel-help/power-view-explore-visualize-and-present-your-data-HA102835634.aspx)</span></span>

 <span data-ttu-id="7bde1-125">![文件夹图标](media/hlp-16folder.gif "文件夹图标") [Reporting Services 安全和保护](security/reporting-services-security-and-protection.md)</span><span class="sxs-lookup"><span data-stu-id="7bde1-125">![Folder icon](media/hlp-16folder.gif "Folder icon") [Reporting Services Security and Protection](security/reporting-services-security-and-protection.md)</span></span>

 <span data-ttu-id="7bde1-126">![文件夹图标](media/hlp-16folder.gif "文件夹图标") [URL 访问 &#40;SSRS&#41;](url-access-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="7bde1-126">![Folder icon](media/hlp-16folder.gif "Folder icon") [URL Access &#40;SSRS&#41;](url-access-ssrs.md)</span></span>

 <span data-ttu-id="7bde1-127">[&#40;SSRS&#41;](extensions-ssrs.md) ![文件夹图标](media/hlp-16folder.gif "文件夹图标")扩展</span><span class="sxs-lookup"><span data-stu-id="7bde1-127">![Folder icon](media/hlp-16folder.gif "Folder icon") [Extensions &#40;SSRS&#41;](extensions-ssrs.md)</span></span>

 <span data-ttu-id="7bde1-128">![文件夹图标](media/hlp-16folder.gif "文件夹图标") [Reporting Services 工具](tools/reporting-services-tools.md)</span><span class="sxs-lookup"><span data-stu-id="7bde1-128">![Folder icon](media/hlp-16folder.gif "Folder icon") [Reporting Services Tools](tools/reporting-services-tools.md)</span></span>

 <span data-ttu-id="7bde1-129">![文件夹图标](media/hlp-16folder.gif "文件夹图标")[错误和事件参考 &#40;Reporting Services&#41;](troubleshooting/errors-and-events-reference-reporting-services.md)</span><span class="sxs-lookup"><span data-stu-id="7bde1-129">![Folder icon](media/hlp-16folder.gif "Folder icon") [Errors and Events Reference &#40;Reporting Services&#41;](troubleshooting/errors-and-events-reference-reporting-services.md)</span></span>

 <span data-ttu-id="7bde1-130">![文件夹图标](media/hlp-16folder.gif "文件夹图标")[功能参考 &#40;Reporting Services&#41;](feature-reference-reporting-services.md)</span><span class="sxs-lookup"><span data-stu-id="7bde1-130">![Folder icon](media/hlp-16folder.gif "Folder icon") [Feature Reference &#40;Reporting Services&#41;](feature-reference-reporting-services.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="7bde1-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7bde1-131">See Also</span></span>
 [<span data-ttu-id="7bde1-132">SQL Server 资源中心</span><span class="sxs-lookup"><span data-stu-id="7bde1-132">SQL Server Resource Center</span></span>](https://go.microsoft.com/fwlink/?linkID=219676)


