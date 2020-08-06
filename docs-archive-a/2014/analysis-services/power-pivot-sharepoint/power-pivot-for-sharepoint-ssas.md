---
title: PowerPivot for SharePoint (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 11/25/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: c4c393d3-4856-47ac-ab5f-15da2f240d1d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 58ebcf004224d21ab5b47aaee1e2e7e3ef2047ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587025"
---
# <a name="powerpivot-for-sharepoint-ssas"></a><span data-ttu-id="15cbe-102">PowerPivot for SharePoint (SSAS)</span><span class="sxs-lookup"><span data-stu-id="15cbe-102">PowerPivot for SharePoint (SSAS)</span></span>
  <span data-ttu-id="15cbe-103">PowerPivot for SharePoint 是一个在 SharePoint 模式下运行的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 服务器。</span><span class="sxs-lookup"><span data-stu-id="15cbe-103">PowerPivot for SharePoint is a [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] server running in SharePoint mode.</span></span> <span data-ttu-id="15cbe-104">PowerPivot for SharePoint 对 SharePoint 场中的 PowerPivot 数据提供服务器托管。</span><span class="sxs-lookup"><span data-stu-id="15cbe-104">PowerPivot for SharePoint provides server hosting of PowerPivot data in a SharePoint farm.</span></span> <span data-ttu-id="15cbe-105">PowerPivot 数据是使用以下项之一生成的分析数据模型：</span><span class="sxs-lookup"><span data-stu-id="15cbe-105">PowerPivot data is an analytical data model that you build using one of the following:</span></span>  
  
-   <span data-ttu-id="15cbe-106">PowerPivot for Excel 2010 外接程序</span><span class="sxs-lookup"><span data-stu-id="15cbe-106">The PowerPivot for Excel 2010 add-in</span></span>  
  
-   <span data-ttu-id="15cbe-107">Excel 2013</span><span class="sxs-lookup"><span data-stu-id="15cbe-107">Excel 2013</span></span>  
  
 <span data-ttu-id="15cbe-108">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]2013 |[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]2010</span><span class="sxs-lookup"><span data-stu-id="15cbe-108">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 | [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2010</span></span>  
  
 <span data-ttu-id="15cbe-109">这些数据的服务器托管要求安装 SharePoint、Excel Services 和 PowerPivot for SharePoint。</span><span class="sxs-lookup"><span data-stu-id="15cbe-109">Server hosting of that data requires SharePoint, Excel Services, and an installation of PowerPivot for SharePoint.</span></span> <span data-ttu-id="15cbe-110">数据加载到 PowerPivot for SharePoint 实例上，从中，可以使用服务器为 Excel 2010 工作簿或 SharePoint 2013 Excel Services 为 Excel 2013 工具簿提供的 PowerPivot 数据刷新功能定期刷新数据。</span><span class="sxs-lookup"><span data-stu-id="15cbe-110">Data is loaded on PowerPivot for SharePoint instances where it can be refreshed at scheduled intervals using the PowerPivot data refresh capability that the server provides for Excel 2010 workbooks or that SharePoint 2013 Excel Services provides for Excel 2013 workbooks.</span></span>  
  
## <a name="powerpivot-for-sharepoint-2013"></a><span data-ttu-id="15cbe-111">PowerPivot for SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="15cbe-111">PowerPivot for SharePoint 2013</span></span>  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<span data-ttu-id="15cbe-112">[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]支持 [!INCLUDE[msCoName](../../includes/msconame-md.md)]SharePoint 2013 Excel Services 使用包含数据模型和 Power View 报表的 Excel 工作簿 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="15cbe-112">[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] supports [!INCLUDE[msCoName](../../includes/msconame-md.md)] SharePoint 2013 Excel Services usage of Excel workbooks containing data models and [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Power View reports.</span></span>  
  
 <span data-ttu-id="15cbe-113">SharePoint 2013 中的 Excel Services 包括数据模型功能，以便在浏览器中实现与 PowerPivot 工作簿的交互。</span><span class="sxs-lookup"><span data-stu-id="15cbe-113">Excel Services in SharePoint 2013 includes data model functionality to enable interaction with a PowerPivot workbook in the browser.</span></span> <span data-ttu-id="15cbe-114">您无需将 PowerPivot for SharePoint 2013 外接程序部署到场中。</span><span class="sxs-lookup"><span data-stu-id="15cbe-114">You do not need to deploy the PowerPivot for SharePoint 2013 add-in into the farm.</span></span> <span data-ttu-id="15cbe-115">您只需在 SharePoint 模式下安装 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 服务器，并且在 Excel Services 的 **“数据模型”** 设置中注册该服务器。</span><span class="sxs-lookup"><span data-stu-id="15cbe-115">You only need to install an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] server in SharePoint mode and register the server within the Excel Services **Data Model** settings.</span></span>  
  
 <span data-ttu-id="15cbe-116">通过部署 PowerPivot for SharePoint 2013 外接程序，您可以在 SharePoint 场中实现附加功能。</span><span class="sxs-lookup"><span data-stu-id="15cbe-116">Deploying the PowerPivot for SharePoint 2013 add-in enables additional functionality and features in your SharePoint farm.</span></span> <span data-ttu-id="15cbe-117">这些附加功能包括 PowerPivot 库、计划数据刷新和 PowerPivot 管理面板。</span><span class="sxs-lookup"><span data-stu-id="15cbe-117">The additional features include PowerPivot Gallery, Schedule Data Refresh, and the PowerPivot Management Dashboard.</span></span>  
  
 <span data-ttu-id="15cbe-118">![SSAS PowerPivot 模式 2 服务器部署](../media/as-powerpivot-mode-2server-deployment.gif "SSAS PowerPivot 模式 2 服务器部署")</span><span class="sxs-lookup"><span data-stu-id="15cbe-118">![SSAS PowerPivot Mode 2 Server Deployment](../media/as-powerpivot-mode-2server-deployment.gif "SSAS PowerPivot Mode 2 Server Deployment")</span></span>  
  
## <a name="powerpivot-for-sharepoint-2010"></a><span data-ttu-id="15cbe-119">PowerPivot for SharePoint 2010</span><span class="sxs-lookup"><span data-stu-id="15cbe-119">PowerPivot for SharePoint 2010</span></span>  
 <span data-ttu-id="15cbe-120">PowerPivot for SharePoint 2010 对 SharePoint 2010 场中的 PowerPivot 数据提供服务器托管。</span><span class="sxs-lookup"><span data-stu-id="15cbe-120">PowerPivot for SharePoint 2010 provides server hosting of PowerPivot data in a SharePoint 2010 farm.</span></span> <span data-ttu-id="15cbe-121">PowerPivot 数据是使用 PowerPivot for Excel 外接程序在 Excel 中生成的一种分析数据模型。</span><span class="sxs-lookup"><span data-stu-id="15cbe-121">PowerPivot data is an analytical data model that you build in Excel using the PowerPivot for Excel add-in.</span></span> <span data-ttu-id="15cbe-122">这些数据的服务器托管要求安装 SharePoint 2010、Excel Services 和 PowerPivot for SharePoint。</span><span class="sxs-lookup"><span data-stu-id="15cbe-122">Server hosting of that data requires SharePoint 2010, Excel Services, and an installation of PowerPivot for SharePoint.</span></span> <span data-ttu-id="15cbe-123">数据加载到场中的 PowerPivot for SharePoint 实例上，从中，可以使用服务器提供的 PowerPivot 数据刷新功能定期刷新数据。</span><span class="sxs-lookup"><span data-stu-id="15cbe-123">Data is loaded on PowerPivot for SharePoint instances in the farm, where it can be refreshed at scheduled intervals using the PowerPivot data refresh capability that the server provides.</span></span>  
  
### <a name="components-of-powerpivot-for-sharepoint-2010"></a><span data-ttu-id="15cbe-124">PowerPivot for SharePoint 2010 的组件</span><span class="sxs-lookup"><span data-stu-id="15cbe-124">Components of PowerPivot for SharePoint 2010</span></span>  
 <span data-ttu-id="15cbe-125">PowerPivot for SharePoint 作为共享服务实现，这意味着可以使用内置功能和基础结构来管理、保护和使用 PowerPivot 服务应用程序。</span><span class="sxs-lookup"><span data-stu-id="15cbe-125">PowerPivot for SharePoint is implemented as a shared service, which means that the built-in features and infrastructure can be used to administer, secure, and use a PowerPivot service application.</span></span> <span data-ttu-id="15cbe-126">服务器和数据库发现、重定向和连接管理全都在场级别管理。</span><span class="sxs-lookup"><span data-stu-id="15cbe-126">Server and database discovery, redirection, and connection management is all managed at the farm level.</span></span> <span data-ttu-id="15cbe-127">管理中心提供服务用来管理服务器标识、服务器状态和配置属性的管理界面。</span><span class="sxs-lookup"><span data-stu-id="15cbe-127">Central Administration provides the administrative interface to the services used to manage server identity, server state, and configuration properties.</span></span>  
  
 <span data-ttu-id="15cbe-128">完整部署 PowerPivot for SharePoint 包括将 Excel 和 Excel Services 在 SharePoint 场中进行集成的客户端和服务器组件。</span><span class="sxs-lookup"><span data-stu-id="15cbe-128">A complete deployment of PowerPivot for SharePoint includes client and server components that integrate with Excel and Excel Services in a SharePoint farm.</span></span> <span data-ttu-id="15cbe-129">Excel 工作簿内的 PowerPivot 数据是一种 Analysis Services 数据库，它要求 Analysis Services xVelocity 内存中分析引擎 (VertiPaq) 加载和查询数据。</span><span class="sxs-lookup"><span data-stu-id="15cbe-129">The PowerPivot data inside an Excel workbook is an Analysis Services database that requires an Analysis Services xVelocity in-memory analytics engine (VertiPaq) to load and query the data.</span></span> <span data-ttu-id="15cbe-130">在客户端工作站上，xVelocity 引擎在 Excel 内部在进程内运行。</span><span class="sxs-lookup"><span data-stu-id="15cbe-130">On a client workstation, the xVelocity engine runs in-process within Excel.</span></span> <span data-ttu-id="15cbe-131">在 SharePoint 场上，Analysis Services 在应用程序服务器上运行，它与相关服务配合使用以处理 PowerPivot 数据请求。</span><span class="sxs-lookup"><span data-stu-id="15cbe-131">On a SharePoint farm, Analysis Services runs on an application server where it is paired with related services that handle requests for PowerPivot data.</span></span> <span data-ttu-id="15cbe-132">下面的关系图说明了 PowerPivot 客户端和服务器组件：</span><span class="sxs-lookup"><span data-stu-id="15cbe-132">The following diagram illustrates PowerPivot client and server components:</span></span>  
  
 <span data-ttu-id="15cbe-133">![GMNI_GeminiArch2](../media/gmni-geminiarch2.gif "GMNI_GeminiArch2")</span><span class="sxs-lookup"><span data-stu-id="15cbe-133">![GMNI_GeminiArch2](../media/gmni-geminiarch2.gif "GMNI_GeminiArch2")</span></span>  
  
 <span data-ttu-id="15cbe-134">PowerPivot Web 服务在 Web 应用程序服务器上运行。</span><span class="sxs-lookup"><span data-stu-id="15cbe-134">PowerPivot Web service runs on a web application server.</span></span> <span data-ttu-id="15cbe-135">它将来自 Web 应用程序的请求重定向到场中的 PowerPivot 系统服务实例上。</span><span class="sxs-lookup"><span data-stu-id="15cbe-135">It redirects requests from the web application to a PowerPivot System Service instance in the farm.</span></span>  
  
 <span data-ttu-id="15cbe-136">PowerPivot 系统服务对 Analysis Services 服务器发出加载请求，管理已加载到内存中的数据的正在进行的连接，并且在数据不再使用或者出现系统资源争用时缓存或卸载数据。</span><span class="sxs-lookup"><span data-stu-id="15cbe-136">PowerPivot System Service issues load requests to the Analysis Services server and manages ongoing connections to data that is already loaded in memory, caching or unloading data if it is no longer used or when there is contention for system resources.</span></span> <span data-ttu-id="15cbe-137">它还跟踪用户活动。</span><span class="sxs-lookup"><span data-stu-id="15cbe-137">It also tracks user activity.</span></span> <span data-ttu-id="15cbe-138">收集服务器运行状况数据和其他使用情况数据并显示在报表中，以便指出系统的运行状况如何。</span><span class="sxs-lookup"><span data-stu-id="15cbe-138">Server health data and other usage data is gathered and presented in reports to indicate how well the system is performing.</span></span>  
  
 <span data-ttu-id="15cbe-139">SharePoint 集成模式下的 Analysis Service 服务器实例完成该部署。</span><span class="sxs-lookup"><span data-stu-id="15cbe-139">An Analysis Service server instance in SharePoint integrated mode completes the deployment.</span></span> <span data-ttu-id="15cbe-140">它加载、查询和卸载数据。</span><span class="sxs-lookup"><span data-stu-id="15cbe-140">It loads, queries, and unloads data.</span></span> <span data-ttu-id="15cbe-141">如果工作簿配置用于 PowerPivot 数据刷新，它还可以处理数据。</span><span class="sxs-lookup"><span data-stu-id="15cbe-141">It also processes data if the workbook is configured for PowerPivot data refresh.</span></span>  <span data-ttu-id="15cbe-142">每个实例都与属于同一安装的本地 PowerPivot 系统服务紧密结合。</span><span class="sxs-lookup"><span data-stu-id="15cbe-142">Each instance is tightly coupled with the local PowerPivot System Service that is part of the same installation.</span></span>  
  
##  <a name="in-this-section"></a><a name="bkmk_RelatedContent"></a> <span data-ttu-id="15cbe-143">本节内容</span><span class="sxs-lookup"><span data-stu-id="15cbe-143">In This Section</span></span>  
 [<span data-ttu-id="15cbe-144">在管理中心中管理和配置 PowerPivot 服务器</span><span class="sxs-lookup"><span data-stu-id="15cbe-144">PowerPivot Server Administration and Configuration in Central Administration</span></span>](power-pivot-server-administration-and-configuration-in-central-administration.md)  
  
 [<span data-ttu-id="15cbe-145">使用 Windows PowerShell 配置 PowerPivot</span><span class="sxs-lookup"><span data-stu-id="15cbe-145">PowerPivot Configuration using Windows PowerShell</span></span>](power-pivot-configuration-using-windows-powershell.md)  
  
 [<span data-ttu-id="15cbe-146">PowerPivot Configuration Tools</span><span class="sxs-lookup"><span data-stu-id="15cbe-146">PowerPivot Configuration Tools</span></span>](power-pivot-configuration-tools.md)  
  
 [<span data-ttu-id="15cbe-147">PowerPivot 身份验证和授权</span><span class="sxs-lookup"><span data-stu-id="15cbe-147">PowerPivot Authentication and Authorization</span></span>](power-pivot-authentication-and-authorization.md)  
  
 [<span data-ttu-id="15cbe-148">PowerPivot 运行状况规则 - 配置</span><span class="sxs-lookup"><span data-stu-id="15cbe-148">PowerPivot Health Rules - Configure</span></span>](configure-power-pivot-health-rules.md)  
  
 [<span data-ttu-id="15cbe-149">PowerPivot 管理面板和使用情况数据</span><span class="sxs-lookup"><span data-stu-id="15cbe-149">PowerPivot Management Dashboard and Usage Data</span></span>](power-pivot-management-dashboard-and-usage-data.md)  
  
 [<span data-ttu-id="15cbe-150">PowerPivot 库</span><span class="sxs-lookup"><span data-stu-id="15cbe-150">PowerPivot Gallery</span></span>](../../index.yml)  
  
 [<span data-ttu-id="15cbe-151">PowerPivot 数据访问</span><span class="sxs-lookup"><span data-stu-id="15cbe-151">PowerPivot Data Access</span></span>](power-pivot-data-access.md)  
  
 [<span data-ttu-id="15cbe-152">PowerPivot 数据刷新</span><span class="sxs-lookup"><span data-stu-id="15cbe-152">PowerPivot Data Refresh</span></span>](power-pivot-data-refresh.md)  
  
 [<span data-ttu-id="15cbe-153">PowerPivot 数据馈送</span><span class="sxs-lookup"><span data-stu-id="15cbe-153">PowerPivot Data Feeds</span></span>](power-pivot-data-feeds.md)  
  
 [<span data-ttu-id="15cbe-154">PowerPivot BI 语义模型连接 &#40; bism&#41;</span><span class="sxs-lookup"><span data-stu-id="15cbe-154">PowerPivot BI Semantic Model Connection &#40;.bism&#41;</span></span>](power-pivot-bi-semantic-model-connection-bism.md)  
  
 <span data-ttu-id="15cbe-155">**其他部分**</span><span class="sxs-lookup"><span data-stu-id="15cbe-155">**In other sections**</span></span>  
  
## <a name="additional-topics"></a><span data-ttu-id="15cbe-156">其他主题</span><span class="sxs-lookup"><span data-stu-id="15cbe-156">Additional topics</span></span>  
 [<span data-ttu-id="15cbe-157">升级 PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="15cbe-157">Upgrade PowerPivot for SharePoint</span></span>](../../database-engine/install-windows/upgrade-power-pivot-for-sharepoint.md)  
  
 [<span data-ttu-id="15cbe-158">PowerPivot for SharePoint 2013 安装</span><span class="sxs-lookup"><span data-stu-id="15cbe-158">PowerPivot for SharePoint 2013 Installation</span></span>](../instances/install-windows/install-analysis-services-in-power-pivot-mode.md)  
  
 [<span data-ttu-id="15cbe-159">针对 PowerPivot for SharePoint 的 PowerShell 参考</span><span class="sxs-lookup"><span data-stu-id="15cbe-159">PowerShell Reference for PowerPivot for SharePoint</span></span>](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint)  
  
 [<span data-ttu-id="15cbe-160">SQL Server 2014 自助商业智能的许可证拓扑和成本示例</span><span class="sxs-lookup"><span data-stu-id="15cbe-160">Example License Topologies and Costs  for SQL Server 2014 Self-Service Business Intelligence</span></span>](../../sql-server/install/example-license-topologies-costs-self-service-business-intelligence.md)  
  
## <a name="see-also"></a><span data-ttu-id="15cbe-161">另请参阅</span><span class="sxs-lookup"><span data-stu-id="15cbe-161">See Also</span></span>  
 <span data-ttu-id="15cbe-162">[PowerPivot 规划和部署](https://go.microsoft.com/fwlink/?linkID=220972) </span><span class="sxs-lookup"><span data-stu-id="15cbe-162">[PowerPivot Planning and Deployment](https://go.microsoft.com/fwlink/?linkID=220972) </span></span>  
 [<span data-ttu-id="15cbe-163">Disaster Recovery for PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="15cbe-163">Disaster Recovery for PowerPivot for SharePoint</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389570)  
  
  
