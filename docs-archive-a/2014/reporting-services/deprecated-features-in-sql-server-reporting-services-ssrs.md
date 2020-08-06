---
title: SQL Server 2014 的 SQL Server Reporting Services 中的不推荐使用的功能 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services, backward compatibility
- deprecated features [Reporting Services]
- HTML OWC rendering extension [Reporting Services]
- Report Server Web service, endpoints
ms.assetid: 3876c01e-f81d-4cce-9104-5106a8c369e6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: af858ae94bf5ea3d9f0cfe0b99759442dabd6629
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587237"
---
# <a name="deprecated-features-in-sql-server-reporting-services-in-sql-server-2014"></a><span data-ttu-id="c5da9-102">SQL Server 2014 的 SQL Server Reporting Services 中不推荐使用的功能</span><span class="sxs-lookup"><span data-stu-id="c5da9-102">Deprecated Features in SQL Server Reporting Services in SQL Server 2014</span></span>
  <span data-ttu-id="c5da9-103">本主题介绍不推荐使用的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 功能。</span><span class="sxs-lookup"><span data-stu-id="c5da9-103">This topic describes the deprecated [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features.</span></span> <span data-ttu-id="c5da9-104">在不推荐使用这些功能的版本中仍提供这些功能，但是计划在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的未来版本中删除它们。</span><span class="sxs-lookup"><span data-stu-id="c5da9-104">The features are still available in the release in which they are deprecated; however the features are scheduled to be removed in a future release of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c5da9-105">在新的应用程序中不应使用这些不推荐使用的功能。</span><span class="sxs-lookup"><span data-stu-id="c5da9-105">Deprecated features should not be used in new applications.</span></span>  
  
 <span data-ttu-id="c5da9-106">本主题内容：</span><span class="sxs-lookup"><span data-stu-id="c5da9-106">In this topic:</span></span>  
  
-   [<span data-ttu-id="c5da9-107">SQL Server 2014 Reporting Services 中弃用的功能</span><span class="sxs-lookup"><span data-stu-id="c5da9-107">SQL Server 2014 Reporting Services Deprecated Features</span></span>](#bkmk_2014)  
  
-   [<span data-ttu-id="c5da9-108">SQL Server 2012 SP1 Reporting Services 中不推荐使用的功能</span><span class="sxs-lookup"><span data-stu-id="c5da9-108">SQL Server 2012 SP1 Reporting Services Deprecated Features</span></span>](#bkmk_2012sp1)  
  
-   [<span data-ttu-id="c5da9-109">SQL Server 2012 Reporting Services 中弃用的功能</span><span class="sxs-lookup"><span data-stu-id="c5da9-109">SQL Server 2012 Reporting Services Deprecated Features</span></span>](#bkmk_2012)  
  
-   [<span data-ttu-id="c5da9-110">SQL Server 2008 R2 Reporting Services 中不推荐使用的功能</span><span class="sxs-lookup"><span data-stu-id="c5da9-110">SQL Server 2008 R2 Reporting Services Deprecated Features</span></span>](#bkmk_kj)  
  
##  <a name="sql-server-2014-reporting-services-deprecated-features"></a><a name="bkmk_2014"></a><span data-ttu-id="c5da9-111">SQL Server 2014 Reporting Services 弃用的功能</span><span class="sxs-lookup"><span data-stu-id="c5da9-111">SQL Server 2014 Reporting Services Deprecated Features</span></span>  
  
### <a name="features-not-supported-in-the-next-version-of-sql-server"></a><span data-ttu-id="c5da9-112">SQL Server 的下一版本中不支持的功能</span><span class="sxs-lookup"><span data-stu-id="c5da9-112">Features Not Supported in the Next Version of SQL Server</span></span>  
 <span data-ttu-id="c5da9-113">的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] **下一**版本将不支持以下功能 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c5da9-113">The following [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features will not be supported in the **next** version of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c5da9-114">请不要在新的开发工作中使用这些功能，并尽快修改当前还在使用这些功能的应用程序。</span><span class="sxs-lookup"><span data-stu-id="c5da9-114">Do not use these features in new development work, and modify applications that currently use these features as soon as possible.</span></span>  
  
#### <a name="html-rendering-extension-device-information-settings"></a><span data-ttu-id="c5da9-115">HTML 呈现扩展插件的设备信息设置</span><span class="sxs-lookup"><span data-stu-id="c5da9-115">HTML Rendering Extension Device Information Settings</span></span>  
 <span data-ttu-id="c5da9-116">不推荐使用 HTML 呈现扩展插件的以下设备信息设置。</span><span class="sxs-lookup"><span data-stu-id="c5da9-116">The following device information settings for the HTML rendering extension are deprecated.</span></span>  
  
-   <span data-ttu-id="c5da9-117">ActionScript</span><span class="sxs-lookup"><span data-stu-id="c5da9-117">ActionScript</span></span>  
  
-   <span data-ttu-id="c5da9-118">ActiveXControls</span><span class="sxs-lookup"><span data-stu-id="c5da9-118">ActiveXControls</span></span>  
  
-   <span data-ttu-id="c5da9-119">GetImage</span><span class="sxs-lookup"><span data-stu-id="c5da9-119">GetImage</span></span>  
  
-   <span data-ttu-id="c5da9-120">OnlyVisibleStyles</span><span class="sxs-lookup"><span data-stu-id="c5da9-120">OnlyVisibleStyles</span></span>  
  
-   <span data-ttu-id="c5da9-121">ReplacementRoot</span><span class="sxs-lookup"><span data-stu-id="c5da9-121">ReplacementRoot</span></span>  
  
-   <span data-ttu-id="c5da9-122">ResourceStreamRoot</span><span class="sxs-lookup"><span data-stu-id="c5da9-122">ResourceStreamRoot</span></span>  
  
-   <span data-ttu-id="c5da9-123">StreamRoot</span><span class="sxs-lookup"><span data-stu-id="c5da9-123">StreamRoot</span></span>  
  
-   <span data-ttu-id="c5da9-124">UsePx</span><span class="sxs-lookup"><span data-stu-id="c5da9-124">UsePx</span></span>  
  
-   <span data-ttu-id="c5da9-125">Zoom</span><span class="sxs-lookup"><span data-stu-id="c5da9-125">Zoom</span></span>  
  
 <span data-ttu-id="c5da9-126">有关 HTML 呈现扩展插件的详细信息，请参阅 [HTML Device Information Settings](html-device-information-settings.md)</span><span class="sxs-lookup"><span data-stu-id="c5da9-126">For more information on the HTML rendering extension, see [HTML Device Information Settings](html-device-information-settings.md)</span></span>  
  
#### <a name="microsoft-word-and-microsoft-excel-1997-2003-rendering"></a><span data-ttu-id="c5da9-127">Microsoft Word 和 Microsoft Excel 1997-2003 呈现</span><span class="sxs-lookup"><span data-stu-id="c5da9-127">Microsoft Word and Microsoft Excel 1997-2003 Rendering</span></span>  
 <span data-ttu-id="c5da9-128">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] BIFF8 呈现扩展插件将 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 报表呈现为 [!INCLUDE[msCoName](../includes/msconame-md.md)] Word 和 [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel 1997-2003 二进制交换文件格式。</span><span class="sxs-lookup"><span data-stu-id="c5da9-128">The[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] BIFF8 rendering extensions [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] reports to the [!INCLUDE[msCoName](../includes/msconame-md.md)] Word and [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel 1997-2003 binary interchange file format.</span></span> [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]<span data-ttu-id="c5da9-129">包含以 [!INCLUDE[msCoName](../includes/msconame-md.md)] Office 2007-2010 开放 XML 格式呈现的扩展。</span><span class="sxs-lookup"><span data-stu-id="c5da9-129">includes extensions that render in the [!INCLUDE[msCoName](../includes/msconame-md.md)] Office 2007-2010 Open XML format.</span></span>  
  
#### <a name="report-definition-language-rdl-2005-and-earlier"></a><span data-ttu-id="c5da9-130">报表定义语言 (RDL) 2005 和更早版本</span><span class="sxs-lookup"><span data-stu-id="c5da9-130">Report Definition Language (RDL) 2005 and Earlier</span></span>  
 <span data-ttu-id="c5da9-131">不推荐使用报表定义语言 (RDL) 2005 和更早版本。</span><span class="sxs-lookup"><span data-stu-id="c5da9-131">Report Definition Language (RDL) 2005 and earlier is deprecated.</span></span> <span data-ttu-id="c5da9-132">有关 RDL 的详细信息，请参阅[报表定义语言 &#40;SSRS&#41;](reports/report-definition-language-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="c5da9-132">For more information about RDL, see [Report Definition Language &#40;SSRS&#41;](reports/report-definition-language-ssrs.md).</span></span>  
  
 <span data-ttu-id="c5da9-133">有关升级报表的详细信息，请参阅 [Upgrade Reports](install-windows/upgrade-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="c5da9-133">For more information on upgrading reports, see [Upgrade Reports](install-windows/upgrade-reports.md).</span></span>  
  
#### <a name="sql-server-2005-and-earlier-custom-report-items"></a><span data-ttu-id="c5da9-134">SQL Server 2005 和更早版本的自定义报表项</span><span class="sxs-lookup"><span data-stu-id="c5da9-134">SQL Server 2005 and earlier Custom Report Items</span></span>  
 <span data-ttu-id="c5da9-135">为 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2005 及更早版本编译 (CRI) 的自定义报表项 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 已弃用。</span><span class="sxs-lookup"><span data-stu-id="c5da9-135">Custom Report Items (CRI) compiled for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 and earlier are deprecated.</span></span>  
  
#### <a name="reporting-services-snapshots-2005-and-earlier"></a><span data-ttu-id="c5da9-136">Reporting Services 快照 2005 和更早版本</span><span class="sxs-lookup"><span data-stu-id="c5da9-136">Reporting Services Snapshots 2005 and earlier</span></span>  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]<span data-ttu-id="c5da9-137">使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 和更早版本呈现的快照已弃用。</span><span class="sxs-lookup"><span data-stu-id="c5da9-137">snapshots rendered with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 and earlier are deprecated.</span></span>  
  
#### <a name="report-models"></a><span data-ttu-id="c5da9-138">报表模型</span><span class="sxs-lookup"><span data-stu-id="c5da9-138">Report Models</span></span>  
 <span data-ttu-id="c5da9-139">语义建模语言 (SMDL) 报表模型已不推荐使用。</span><span class="sxs-lookup"><span data-stu-id="c5da9-139">Semantic modeling language (SMDL) report models are deprecated.</span></span> <span data-ttu-id="c5da9-140">虽然您可以继续使用现有报表模型作为报表中的数据源，但 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 应考虑更新报表以删除其对报表模型的依赖关系。</span><span class="sxs-lookup"><span data-stu-id="c5da9-140">Although you can you continue to use existing report models as data sources in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] reports you should consider updating your reports to remove their dependency on report models.</span></span>  
  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]<span data-ttu-id="c5da9-141">不 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 包含用于创建或更新报表模型的工具。</span><span class="sxs-lookup"><span data-stu-id="c5da9-141">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] does not include tools for creating or updating report models.</span></span> <span data-ttu-id="c5da9-142">有关详细信息，请参阅[SQL Server 2014 的 SQL Server Reporting Services 中的重大更改](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md)。</span><span class="sxs-lookup"><span data-stu-id="c5da9-142">For more information, see [Breaking Changes in SQL Server Reporting Services in SQL Server 2014](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md).</span></span>  
  
#### <a name="deprecated-methods-in-the-web-service-endpoint"></a><span data-ttu-id="c5da9-143">Web 服务端点中不推荐使用的方法</span><span class="sxs-lookup"><span data-stu-id="c5da9-143">Deprecated Methods in the Web Service Endpoint</span></span>  
 <span data-ttu-id="c5da9-144">在 <xref:ReportService2010.ReportingService2010> Web 服务端点中不推荐使用以下操作：</span><span class="sxs-lookup"><span data-stu-id="c5da9-144">The following operations are deprecated in the <xref:ReportService2010.ReportingService2010> Web service endpoint:</span></span>  
  
-   <xref:ReportService2010.ReportingService2010.GetProperties%2A>  
  
-   <xref:ReportService2010.ReportingService2010.IsSSLRequired%2A>  
  
#### <a name="sharepoint-web-parts"></a><span data-ttu-id="c5da9-145">SharePoint Web 部件</span><span class="sxs-lookup"><span data-stu-id="c5da9-145">SharePoint Web Parts</span></span>  
 <span data-ttu-id="c5da9-146">不推荐使用安装 cab 文件 **RSWebParts.cab** 和可以从该 cab 文件解压缩的 SharePoint Web 部件。</span><span class="sxs-lookup"><span data-stu-id="c5da9-146">The installation cabinet file **RSWebParts.cab** and the SharePoint web parts that can be extracted from the cab file, are deprecated.</span></span> <span data-ttu-id="c5da9-147">不推荐使用的 Web 部件是报表资源管理器 (**SPExplorer.dwp**) 和报表查看器 (**SPViewer.dwp**)。</span><span class="sxs-lookup"><span data-stu-id="c5da9-147">The deprecated web parts are Report Explorer (**SPExplorer.dwp**) and Report Viewer (**SPViewer.dwp**).</span></span>  
  
 <span data-ttu-id="c5da9-148">有关不推荐使用的 Web 部件的详细信息，请参阅 [使用 SharePoint Web 部件查看和浏览本机模式下的报表 (SSRS)](https://msdn.microsoft.com/library/ms159772.aspx)</span><span class="sxs-lookup"><span data-stu-id="c5da9-148">For more information on the deprecated web parts, see [View and Explore Native Mode Reports Using SharePoint Web Parts (SSRS)](https://msdn.microsoft.com/library/ms159772.aspx)</span></span>  
  
### <a name="features-not-supported-in-a-future-version-of-sql-server"></a><span data-ttu-id="c5da9-149">SQL Server 未来版本中不支持的功能</span><span class="sxs-lookup"><span data-stu-id="c5da9-149">Features Not Supported in a Future Version of SQL Server</span></span>  
 <span data-ttu-id="c5da9-150">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 的下一版本仍支持以下 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]功能，但以后的版本将删除这些功能。</span><span class="sxs-lookup"><span data-stu-id="c5da9-150">The following [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features are supported in the next version of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], but will be removed in a later version.</span></span> <span data-ttu-id="c5da9-151">具体是哪一 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 版本现在还未确定。</span><span class="sxs-lookup"><span data-stu-id="c5da9-151">The specific version of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] has not been determined.</span></span>  
  
 <span data-ttu-id="c5da9-152">没有在 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 中不推荐使用的 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]功能。</span><span class="sxs-lookup"><span data-stu-id="c5da9-152">No [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features were deprecated in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span>  
  
##  <a name="sql-server-2012-sp1-reporting-services-deprecated-features"></a><a name="bkmk_2012sp1"></a><span data-ttu-id="c5da9-153">SQL Server 2012 SP1 Reporting Services 弃用的功能</span><span class="sxs-lookup"><span data-stu-id="c5da9-153">SQL Server 2012 SP1 Reporting Services Deprecated Features</span></span>  
 <span data-ttu-id="c5da9-154">本节介绍 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 中不推荐使用的 [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)]功能。</span><span class="sxs-lookup"><span data-stu-id="c5da9-154">This section describes [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features deprecated in [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)].</span></span> <span data-ttu-id="c5da9-155">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 的下一版本仍支持以下 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]功能，但以后的版本将删除这些功能。</span><span class="sxs-lookup"><span data-stu-id="c5da9-155">The following [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features are supported in the next version of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], but will be removed in a later version.</span></span> <span data-ttu-id="c5da9-156">具体是哪一 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 版本现在还未确定。</span><span class="sxs-lookup"><span data-stu-id="c5da9-156">The specific version of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] has not been determined.</span></span>  
  
### <a name="sharepoint-web-parts"></a><span data-ttu-id="c5da9-157">SharePoint Web 部件</span><span class="sxs-lookup"><span data-stu-id="c5da9-157">SharePoint Web Parts</span></span>  
 <span data-ttu-id="c5da9-158">不推荐使用安装 cab 文件 **RSWebParts.cab** 和可以从该 cab 文件解压缩的 SharePoint Web 部件。</span><span class="sxs-lookup"><span data-stu-id="c5da9-158">The installation cabinet file **RSWebParts.cab** and the SharePoint web parts that can be extracted from the cab file, are deprecated.</span></span> <span data-ttu-id="c5da9-159">不推荐使用的 Web 部件是报表资源管理器 (**SPExplorer.dwp**) 和报表查看器 (**SPViewer.dwp**)。</span><span class="sxs-lookup"><span data-stu-id="c5da9-159">The deprecated web parts are Report Explorer (**SPExplorer.dwp**) and Report Viewer (**SPViewer.dwp**).</span></span>  
  
 <span data-ttu-id="c5da9-160">有关不推荐使用的 Web 部件的详细信息，请参阅 [使用 SharePoint Web 部件查看和浏览本机模式下的报表 (SSRS)](https://msdn.microsoft.com/library/ms159772.aspx)</span><span class="sxs-lookup"><span data-stu-id="c5da9-160">For more information on the deprecated web parts, see [View and Explore Native Mode Reports Using SharePoint Web Parts (SSRS)](https://msdn.microsoft.com/library/ms159772.aspx)</span></span>  
  
##  <a name="sql-server-2012-reporting-services-deprecated-features"></a><a name="bkmk_2012"></a><span data-ttu-id="c5da9-161">SQL Server 2012 Reporting Services 弃用的功能</span><span class="sxs-lookup"><span data-stu-id="c5da9-161">SQL Server 2012 Reporting Services Deprecated Features</span></span>  
 <span data-ttu-id="c5da9-162">本节介绍 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 中不推荐使用的 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]功能。</span><span class="sxs-lookup"><span data-stu-id="c5da9-162">This section describes [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features deprecated in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].</span></span>  
  
### <a name="html-rendering-extension-device-information-settings"></a><span data-ttu-id="c5da9-163">HTML 呈现扩展插件的设备信息设置</span><span class="sxs-lookup"><span data-stu-id="c5da9-163">HTML Rendering Extension Device Information Settings</span></span>  
 <span data-ttu-id="c5da9-164">不推荐使用 HTML 呈现扩展插件的以下设备信息设置。</span><span class="sxs-lookup"><span data-stu-id="c5da9-164">The following device information settings for the HTML rendering extension are deprecated.</span></span>  
  
-   <span data-ttu-id="c5da9-165">ActionScript</span><span class="sxs-lookup"><span data-stu-id="c5da9-165">ActionScript</span></span>  
  
-   <span data-ttu-id="c5da9-166">ActiveXControls</span><span class="sxs-lookup"><span data-stu-id="c5da9-166">ActiveXControls</span></span>  
  
-   <span data-ttu-id="c5da9-167">GetImage</span><span class="sxs-lookup"><span data-stu-id="c5da9-167">GetImage</span></span>  
  
-   <span data-ttu-id="c5da9-168">OnlyVisibleStyles</span><span class="sxs-lookup"><span data-stu-id="c5da9-168">OnlyVisibleStyles</span></span>  
  
-   <span data-ttu-id="c5da9-169">ReplacementRoot</span><span class="sxs-lookup"><span data-stu-id="c5da9-169">ReplacementRoot</span></span>  
  
-   <span data-ttu-id="c5da9-170">ResourceStreamRoot</span><span class="sxs-lookup"><span data-stu-id="c5da9-170">ResourceStreamRoot</span></span>  
  
-   <span data-ttu-id="c5da9-171">StreamRoot</span><span class="sxs-lookup"><span data-stu-id="c5da9-171">StreamRoot</span></span>  
  
-   <span data-ttu-id="c5da9-172">UsePx</span><span class="sxs-lookup"><span data-stu-id="c5da9-172">UsePx</span></span>  
  
-   <span data-ttu-id="c5da9-173">Zoom</span><span class="sxs-lookup"><span data-stu-id="c5da9-173">Zoom</span></span>  
  
 <span data-ttu-id="c5da9-174">有关 HTML 呈现扩展插件的详细信息，请参阅 [HTML Device Information Settings](html-device-information-settings.md)</span><span class="sxs-lookup"><span data-stu-id="c5da9-174">For more information on the HTML rendering extension, see [HTML Device Information Settings](html-device-information-settings.md)</span></span>  
  
### <a name="microsoft-word-and-microsoft-excel-1997-2003-rendering"></a><span data-ttu-id="c5da9-175">Microsoft Word 和 Microsoft Excel 1997-2003 呈现</span><span class="sxs-lookup"><span data-stu-id="c5da9-175">Microsoft Word and Microsoft Excel 1997-2003 Rendering</span></span>  
 <span data-ttu-id="c5da9-176">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] BIFF8 呈现扩展插件将 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 报表呈现为 [!INCLUDE[msCoName](../includes/msconame-md.md)] Word 和 [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel 1997-2003 二进制交换文件格式。</span><span class="sxs-lookup"><span data-stu-id="c5da9-176">The[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] BIFF8 rendering extensions [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] reports to the [!INCLUDE[msCoName](../includes/msconame-md.md)] Word and [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel 1997-2003 binary interchange file format.</span></span> [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]<span data-ttu-id="c5da9-177">包含以 [!INCLUDE[msCoName](../includes/msconame-md.md)] Office 2007-2010 开放 XML 格式呈现的扩展。</span><span class="sxs-lookup"><span data-stu-id="c5da9-177">includes extensions that render in the [!INCLUDE[msCoName](../includes/msconame-md.md)] Office 2007-2010 Open XML format.</span></span>  
  
### <a name="report-definition-language-rdl-2005-and-earlier"></a><span data-ttu-id="c5da9-178">报表定义语言 (RDL) 2005 和更早版本</span><span class="sxs-lookup"><span data-stu-id="c5da9-178">Report Definition Language (RDL) 2005 and Earlier</span></span>  
 <span data-ttu-id="c5da9-179">不推荐使用报表定义语言 (RDL) 2005 和更早版本。</span><span class="sxs-lookup"><span data-stu-id="c5da9-179">Report Definition Language (RDL) 2005 and earlier is deprecated.</span></span> <span data-ttu-id="c5da9-180">有关 RDL 的详细信息，请参阅[报表定义语言 &#40;SSRS&#41;](reports/report-definition-language-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="c5da9-180">For more information about RDL, see [Report Definition Language &#40;SSRS&#41;](reports/report-definition-language-ssrs.md).</span></span>  
  
 <span data-ttu-id="c5da9-181">有关升级报表的详细信息，请参阅 [Upgrade Reports](install-windows/upgrade-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="c5da9-181">For more information on upgrading reports, see [Upgrade Reports](install-windows/upgrade-reports.md).</span></span>  
  
### <a name="sql-server-2005-and-earlier-custom-report-items"></a><span data-ttu-id="c5da9-182">SQL Server 2005 和更早版本的自定义报表项</span><span class="sxs-lookup"><span data-stu-id="c5da9-182">SQL Server 2005 and earlier Custom Report Items</span></span>  
 <span data-ttu-id="c5da9-183">为 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2005 及更早版本编译 (CRI) 的自定义报表项 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 已弃用。</span><span class="sxs-lookup"><span data-stu-id="c5da9-183">Custom Report Items (CRI) compiled for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 and earlier are deprecated.</span></span>  
  
### <a name="reporting-services-snapshots-2005-and-earlier"></a><span data-ttu-id="c5da9-184">Reporting Services 快照 2005 和更早版本</span><span class="sxs-lookup"><span data-stu-id="c5da9-184">Reporting Services Snapshots 2005 and earlier</span></span>  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]<span data-ttu-id="c5da9-185">使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 和更早版本呈现的快照已弃用。</span><span class="sxs-lookup"><span data-stu-id="c5da9-185">snapshots rendered with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2005 and earlier are deprecated.</span></span>  
  
### <a name="report-models"></a><span data-ttu-id="c5da9-186">报表模型</span><span class="sxs-lookup"><span data-stu-id="c5da9-186">Report Models</span></span>  
 <span data-ttu-id="c5da9-187">语义建模语言 (SMDL) 报表模型已不推荐使用。</span><span class="sxs-lookup"><span data-stu-id="c5da9-187">Semantic modeling language (SMDL) report models are deprecated.</span></span> <span data-ttu-id="c5da9-188">虽然您可以继续使用现有报表模型作为报表中的数据源，但 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 应考虑更新报表以删除其对报表模型的依赖关系。</span><span class="sxs-lookup"><span data-stu-id="c5da9-188">Although you can you continue to use existing report models as data sources in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] reports you should consider updating your reports to remove their dependency on report models.</span></span>  
  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]<span data-ttu-id="c5da9-189">不 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 包含用于创建或更新报表模型的工具。</span><span class="sxs-lookup"><span data-stu-id="c5da9-189">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] does not include tools for creating or updating report models.</span></span> <span data-ttu-id="c5da9-190">有关详细信息，请参阅[SQL Server 2014 的 SQL Server Reporting Services 中的重大更改](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md)。</span><span class="sxs-lookup"><span data-stu-id="c5da9-190">For more information, see [Breaking Changes in SQL Server Reporting Services in SQL Server 2014](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md).</span></span>  
  
### <a name="deprecated-methods-in-the-web-service-endpoint"></a><span data-ttu-id="c5da9-191">Web 服务端点中不推荐使用的方法</span><span class="sxs-lookup"><span data-stu-id="c5da9-191">Deprecated Methods in the Web Service Endpoint</span></span>  
 <span data-ttu-id="c5da9-192">在 <xref:ReportService2010.ReportingService2010> Web 服务端点中不推荐使用以下操作：</span><span class="sxs-lookup"><span data-stu-id="c5da9-192">The following operations are deprecated in the <xref:ReportService2010.ReportingService2010> Web service endpoint:</span></span>  
  
-   <xref:ReportService2010.ReportingService2010.GetProperties%2A>  
  
-   <xref:ReportService2010.ReportingService2010.IsSSLRequired%2A>  
  
##  <a name="sql-server-2008-r2-reporting-services-deprecated-features"></a><a name="bkmk_kj"></a><span data-ttu-id="c5da9-193">SQL Server 2008 R2 Reporting Services 弃用的功能</span><span class="sxs-lookup"><span data-stu-id="c5da9-193">SQL Server 2008 R2 Reporting Services Deprecated Features</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c5da9-194">因为 SQL Server 2008 R2 是 SQL Server 2008 的次版本升级，所以，我们建议您也查看 SQL Server 2008 部分的内容。</span><span class="sxs-lookup"><span data-stu-id="c5da9-194">Because SQL Server 2008 R2 is a minor version upgrade of SQL Server 2008, we recommend that you also review the content in the SQL Server 2008 section.</span></span>  
  
### <a name="report-server-web-service-endpoints"></a><span data-ttu-id="c5da9-195">报表服务器 Web 服务端点</span><span class="sxs-lookup"><span data-stu-id="c5da9-195">Report Server Web Service Endpoints</span></span>  
 <span data-ttu-id="c5da9-196">在此版本中，Web 服务 <xref:ReportService2005.ReportingService2005> 和 <xref:ReportService2006.ReportingService2006> 已不推荐使用。</span><span class="sxs-lookup"><span data-stu-id="c5da9-196">The Web services <xref:ReportService2005.ReportingService2005> and <xref:ReportService2006.ReportingService2006> have been deprecated in this release.</span></span> <span data-ttu-id="c5da9-197">这些端点已替换为一个新端点：<xref:ReportService2010.ReportingService2010>。</span><span class="sxs-lookup"><span data-stu-id="c5da9-197">These endpoints have been replaced by a new endpoint: <xref:ReportService2010.ReportingService2010>.</span></span>  
  
 <span data-ttu-id="c5da9-198">新端点包含不推荐使用的端点中可用的所有功能和 SQL Server 2008 R2 中引入的新功能。</span><span class="sxs-lookup"><span data-stu-id="c5da9-198">The new endpoint includes all the functionality available in the deprecated endpoints and the new features introduced in SQL Server 2008 R2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5da9-199">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c5da9-199">See Also</span></span>  
 <span data-ttu-id="c5da9-200">[新增功能 &#40;Reporting Services&#41;](what-s-new-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="c5da9-200">[What's New &#40;Reporting Services&#41;](what-s-new-reporting-services.md) </span></span>  
 <span data-ttu-id="c5da9-201">[向后兼容性](../getting-started/backward-compatibility.md) </span><span class="sxs-lookup"><span data-stu-id="c5da9-201">[Backward Compatibility](../getting-started/backward-compatibility.md) </span></span>  
 <span data-ttu-id="c5da9-202">[SQL Server 2014 中 SQL Server Reporting Services 的行为更改](behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md) </span><span class="sxs-lookup"><span data-stu-id="c5da9-202">[Behavior Changes to SQL Server Reporting Services  in SQL Server 2014](behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md) </span></span>  
 [<span data-ttu-id="c5da9-203">SQL Server 2014 的 SQL Server Reporting Services 中停止使用的功能</span><span class="sxs-lookup"><span data-stu-id="c5da9-203">Discontinued Functionality to SQL Server Reporting Services in SQL Server 2014</span></span>](discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md)  
  
  
