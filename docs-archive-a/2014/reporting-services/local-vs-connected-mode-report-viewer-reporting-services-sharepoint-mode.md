---
title: 报表查看器中的本地模式和连接模式报表在 SharePoint 模式下 (Reporting Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a230a9bb-6046-401f-b5e5-53ff6edf2264
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 805be8722a38252a9a44797b5e59d2136bc83d6b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691638"
---
# <a name="local-mode-vs-connected-mode-reports-in-the-report-viewer-reporting-services-in-sharepoint-mode"></a><span data-ttu-id="0e14f-102">报表查看器中的本地模式和连接模式报表对比（SharePoint 模式下的 Reporting Services）</span><span class="sxs-lookup"><span data-stu-id="0e14f-102">Local Mode vs. Connected Mode Reports in the Report Viewer (Reporting Services in SharePoint Mode)</span></span>
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]<span data-ttu-id="0e14f-103">可以将报表配置为在 "*本地模式*" 或 "*连接模式" 下*运行，这种模式利用 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Report Server。</span><span class="sxs-lookup"><span data-stu-id="0e14f-103">reports can be configure to run in either *local mode* or *connected mode*, which leverages a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] report server.</span></span> <span data-ttu-id="0e14f-104">您而是可以在数据扩展插件支持本地模式报表时，使用报表查看器直接从 SharePoint 呈现报表。</span><span class="sxs-lookup"><span data-stu-id="0e14f-104">Instead, you can use the Report Viewer to directly render reports from SharePoint when the data extension supports local mode reporting.</span></span> <span data-ttu-id="0e14f-105">这种方法称为“本地模式” \*\*。</span><span class="sxs-lookup"><span data-stu-id="0e14f-105">This approach is called *local mode*.</span></span> <span data-ttu-id="0e14f-106">在之前的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]版本中，SharePoint 场需连接到在 SharePoint 模式下配置的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 报表服务器，以便报表查看器控件可以呈现报表。</span><span class="sxs-lookup"><span data-stu-id="0e14f-106">In previous versions of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], the SharePoint farm was required to be connected to a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] report server configured in SharePoint mode so the Report Viewer control could render reports.</span></span> <span data-ttu-id="0e14f-107">这种方法称为“远程模式” \*\* 或“连接模式” \*\*。</span><span class="sxs-lookup"><span data-stu-id="0e14f-107">This approach is called *remote mode* or *connected mode*.</span></span>  
  
 <span data-ttu-id="0e14f-108">“本地模式”中没有 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 报表服务器\*\*。</span><span class="sxs-lookup"><span data-stu-id="0e14f-108">In *local mode* there is no [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] report server.</span></span> <span data-ttu-id="0e14f-109">必须安装 SharePoint 产品的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 外接程序，但无需 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 报表服务器。</span><span class="sxs-lookup"><span data-stu-id="0e14f-109">You must install the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] add-in for SharePoint products, but no [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] report server is required.</span></span> <span data-ttu-id="0e14f-110">在本地模式中，用户可以查看报表，但无法使用订阅和数据警报之类的服务器端功能。</span><span class="sxs-lookup"><span data-stu-id="0e14f-110">With Local mode, users can view reports but will not have access to server side features such as subscriptions and data alerts.</span></span>  
  
||  
|-|  
|<span data-ttu-id="0e14f-111">**[!INCLUDE[applies](../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]SharePoint 模式</span><span class="sxs-lookup"><span data-stu-id="0e14f-111">**[!INCLUDE[applies](../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint mode</span></span>|  
  
 <span data-ttu-id="0e14f-112">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="0e14f-112">**In this topic:**</span></span>  
  
-   [<span data-ttu-id="0e14f-113">本地模式与连接模式和支持的扩展</span><span class="sxs-lookup"><span data-stu-id="0e14f-113">Local mode vs connected mode and supported extensions</span></span>](#bkmk_local_vs_connected)  
  
-   [<span data-ttu-id="0e14f-114">使用 SharePoint 2013 配置本地模式和访问服务</span><span class="sxs-lookup"><span data-stu-id="0e14f-114">Configure Local Mode and Access Services with SharePoint 2013</span></span>](#bkmk_local_mode_sharepoint2013)  
  
-   [<span data-ttu-id="0e14f-115">用 SharePoint 2010 配置本地模式报告</span><span class="sxs-lookup"><span data-stu-id="0e14f-115">Configure Local Mode Reporting with SharePoint 2010</span></span>](#bkmk_local_mode_sharepoint2010)  
  
##  <a name="local-mode-vs-connected-mode-and-supported-extensions"></a><a name="bkmk_local_vs_connected"></a> <span data-ttu-id="0e14f-116">本地模式与连接模式对比以及支持的扩展插件</span><span class="sxs-lookup"><span data-stu-id="0e14f-116">Local mode vs connected mode and supported extensions</span></span>  
 <span data-ttu-id="0e14f-117">**本地模式：** 当你具有支持本地模式的数据扩展插件时，报表查看器会直接从 SharePoint 呈现报表。</span><span class="sxs-lookup"><span data-stu-id="0e14f-117">**Local mode:** When you have a data extension that supports local mode, the Report Viewer directly renders reports from SharePoint.</span></span> <span data-ttu-id="0e14f-118">“本地模式”中没有 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 报表服务器\*\*。</span><span class="sxs-lookup"><span data-stu-id="0e14f-118">In *local mode* there is no [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] report server.</span></span> <span data-ttu-id="0e14f-119">必须安装 SharePoint 产品的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 外接程序，但无需 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 报表服务器。</span><span class="sxs-lookup"><span data-stu-id="0e14f-119">You must install the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] add-in for SharePoint products, but no [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] report server is required.</span></span> <span data-ttu-id="0e14f-120">在本地模式下，用户可以查看报表，但**不**能访问服务器端功能，如订阅和数据警报。</span><span class="sxs-lookup"><span data-stu-id="0e14f-120">With Local mode, users can view reports but will **not** have access to server side features such as subscriptions and data alerts.</span></span>  
  
 <span data-ttu-id="0e14f-121">**连接模式**也称为 *远程模式* ，在 SharePoint 模式下需使用连接至 SharePoint 场的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 报表服务器，以便报表服务器控件可以呈现报表。</span><span class="sxs-lookup"><span data-stu-id="0e14f-121">**Connected mode**, also called *remote mode* requires a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] report server in SharePoint mode, connected to the SharePoint farm so the Report Viewer control could render reports..</span></span>  
  
 <span data-ttu-id="0e14f-122">下表列出了支持本地模式报表的数据处理扩展插件：</span><span class="sxs-lookup"><span data-stu-id="0e14f-122">The following is a list of the data processing extensions that support local mode reporting:</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="0e14f-123">Access 2010 报表扩展插件。</span><span class="sxs-lookup"><span data-stu-id="0e14f-123">Access 2010 reporting extension.</span></span> <span data-ttu-id="0e14f-124">有关 Access Services 的详细信息，请参阅 [将 Access Services 与 SQL Reporting Services 配合使用：安装 SQL Server 2008 R2 Reporting Services 外接程序 (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?LinkId=192686)。</span><span class="sxs-lookup"><span data-stu-id="0e14f-124">For more information on Access Services, see [Use Access Services with SQL Reporting Services: Installing SQL Server 2008 R2 Reporting Services Add-In (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?LinkId=192686).</span></span>  
  
-   <span data-ttu-id="0e14f-125">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint 列表数据扩展插件。</span><span class="sxs-lookup"><span data-stu-id="0e14f-125">The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint list data extension.</span></span> <span data-ttu-id="0e14f-126">有关 SharePoint 列表数据扩展插件的详细信息，请参阅 [Reporting Services 支持的数据源 (SSRS)](create-deploy-and-manage-mobile-and-paginated-reports.md)</span><span class="sxs-lookup"><span data-stu-id="0e14f-126">For more information on the SharePoint List Data Extension, see [Data Sources Supported by Reporting Services &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md)</span></span>  
  
 <span data-ttu-id="0e14f-127">还可以开发自定义数据处理扩展插件，以支持本地模式。</span><span class="sxs-lookup"><span data-stu-id="0e14f-127">Custom data processing extensions can also be developed to support local mode.</span></span> <span data-ttu-id="0e14f-128">有关详细信息，请参阅 [Implementing a Data Processing Extension](extensions/data-processing/implementing-a-data-processing-extension.md)。</span><span class="sxs-lookup"><span data-stu-id="0e14f-128">For more information, see [Implementing a Data Processing Extension](extensions/data-processing/implementing-a-data-processing-extension.md).</span></span>  
  
 <span data-ttu-id="0e14f-129">本地模式支持呈现具有嵌入数据源或来自 .rsds 文件的共享数据源的报表。</span><span class="sxs-lookup"><span data-stu-id="0e14f-129">Local mode supports rendering reports that have an embedded data source or a shared data source from an .rsds file.</span></span> <span data-ttu-id="0e14f-130">但是，您不能管理报表或其关联的数据源。</span><span class="sxs-lookup"><span data-stu-id="0e14f-130">However, you cannot manage the report or its associated data source.</span></span> <span data-ttu-id="0e14f-131">如果您尝试进行管理，系统将会显示错误消息，因为在本地模式下不支持这样做。</span><span class="sxs-lookup"><span data-stu-id="0e14f-131">If you try to do this, you will receive an error that this is not supported in local mode.</span></span> <span data-ttu-id="0e14f-132">仅在连接模式下支持在 SharePoint 站点中管理数据源。</span><span class="sxs-lookup"><span data-stu-id="0e14f-132">Managing data sources in the SharePoint site is supported in only connected mode.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0e14f-133">与以前的版本一样，您不能在 .rsds 文件中嵌入用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="0e14f-133">As with previous versions, you cannot embed user names and passwords in the .rsds file.</span></span>  
  
##  <a name="configure-local-mode-and-access-services-with-sharepoint-2013"></a><a name="bkmk_local_mode_sharepoint2013"></a><span data-ttu-id="0e14f-134">使用 SharePoint 2013 配置本地模式和访问服务</span><span class="sxs-lookup"><span data-stu-id="0e14f-134">Configure Local Mode and Access Services with SharePoint 2013</span></span>  
 <span data-ttu-id="0e14f-135">您可以配置 SharePoint 2013 场支持现有的 Access 2010 Web 数据库和 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 本地模式。</span><span class="sxs-lookup"><span data-stu-id="0e14f-135">You can configure your SharePoint 2013 farm to support existing Access 2010 web databases and [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] local mode.</span></span> <span data-ttu-id="0e14f-136">有关详细信息，请参阅 [为 SharePoint Server 2013 中的 Web 数据库安装和配置 Access Services 2010](https://technet.microsoft.com/library/ee748653\(office.15\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="0e14f-136">For more information, see [Set up and configure Access Services 2010 for web databases in SharePoint Server 2013](https://technet.microsoft.com/library/ee748653\(office.15\).aspx).</span></span>  
  
 <span data-ttu-id="0e14f-137">不可能为 SharePoint 2013 创建新的 Access Web 数据库。</span><span class="sxs-lookup"><span data-stu-id="0e14f-137">It is not possible to create new Access web databases for SharePoint 2013.</span></span> <span data-ttu-id="0e14f-138">Access 2013 使用在 Access 中内置的新型数据库“Access Web 应用程序” \*\* ，然后将其用作 Web 浏览器中的 SharePoint 应用程序并与他人共享。</span><span class="sxs-lookup"><span data-stu-id="0e14f-138">Access 2013 uses a new type of database, *Access web app* that you build in Access, then use and share with others as a SharePoint app in a web browser.</span></span>  
  
 <span data-ttu-id="0e14f-139">有关详细信息，请参阅以下内容。</span><span class="sxs-lookup"><span data-stu-id="0e14f-139">For more information, see the following.</span></span>  
  
-   <span data-ttu-id="0e14f-140">[Access 2013 (的新增功能](https://office.microsoft.com/access-help/what-s-new-in-access-2013-HA102809500.aspx) https://office.microsoft.com/access-help/what-s-new-in-access-2013-HA102809500.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="0e14f-140">[What's new in Access 2013](https://office.microsoft.com/access-help/what-s-new-in-access-2013-HA102809500.aspx) (https://office.microsoft.com/access-help/what-s-new-in-access-2013-HA102809500.aspx).</span></span>  
  
-   <span data-ttu-id="0e14f-141"> ([访问应用程序的基本任务](https://office.microsoft.com/access-help/basic-tasks-for-an-access-app-HA102840210.aspx?CTT=5&origin=HA102809500) https://office.microsoft.com/access-help/basic-tasks-for-an-access-app-HA102840210.aspx?CTT=5&origin=HA102809500) 。</span><span class="sxs-lookup"><span data-stu-id="0e14f-141">[Basic tasks for an Access app](https://office.microsoft.com/access-help/basic-tasks-for-an-access-app-HA102840210.aspx?CTT=5&origin=HA102809500) (https://office.microsoft.com/access-help/basic-tasks-for-an-access-app-HA102840210.aspx?CTT=5&origin=HA102809500).</span></span>  
  
##  <a name="configure-local-mode-reporting-with-sharepoint-2010"></a><a name="bkmk_local_mode_sharepoint2010"></a><span data-ttu-id="0e14f-142">用 SharePoint 2010 配置本地模式报告</span><span class="sxs-lookup"><span data-stu-id="0e14f-142">Configure Local Mode Reporting with SharePoint 2010</span></span>  
 <span data-ttu-id="0e14f-143">本地模式要求 ASP.NET 会话状态。</span><span class="sxs-lookup"><span data-stu-id="0e14f-143">Local mode requires ASP.NET session state.</span></span> <span data-ttu-id="0e14f-144">安装 Access 服务将启用 ASP.Net 会话状态。</span><span class="sxs-lookup"><span data-stu-id="0e14f-144">The installation of Access services will enable ASP.Net sessions state.</span></span> <span data-ttu-id="0e14f-145">您也可以使用 PowerShell 来启用。</span><span class="sxs-lookup"><span data-stu-id="0e14f-145">You can also enable using PowerShell.</span></span>  
  
1.  <span data-ttu-id="0e14f-146">打开 SharePoint 2010 Management Shell。</span><span class="sxs-lookup"><span data-stu-id="0e14f-146">Open the SharePoint 2010 Management Shell.</span></span>  
  
2.  <span data-ttu-id="0e14f-147">键入以下命令：</span><span class="sxs-lookup"><span data-stu-id="0e14f-147">Type the following command:</span></span>  
  
    ```  
    - Enable-SPSessionStateService  
    ```  
  
3.  <span data-ttu-id="0e14f-148">在系统提示后，键入数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="0e14f-148">When prompted, type the name of your database.</span></span>  
  
4.  <span data-ttu-id="0e14f-149">执行 IIS 重置。</span><span class="sxs-lookup"><span data-stu-id="0e14f-149">Perform an IIS reset.</span></span>  
  
 <span data-ttu-id="0e14f-150">有关详细信息，请参阅将 [Access Services 与 SQL Reporting Services 配合使用：安装 SQL Server 2008 R2 Reporting Services 外接程序 (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?LinkId=192686) 和 [Enable-SPSessionStateService](https://technet.microsoft.com/library/ff607857\(v=office.15\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="0e14f-150">For more information, see [Use Access Services with SQL Reporting Services: Installing SQL Server 2008 R2 Reporting Services Add-In (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?LinkId=192686) and [Enable-SPSessionStateService](https://technet.microsoft.com/library/ff607857\(v=office.15\).aspx).</span></span>  
  
## <a name="connected-mode"></a><span data-ttu-id="0e14f-151">“连接模式”</span><span class="sxs-lookup"><span data-stu-id="0e14f-151">Connected mode</span></span>  
 <span data-ttu-id="0e14f-152">有关在连接模式下使用 ADS 扩展的最新信息 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ，请参阅[SharePoint 站点中的 Access Services 报表显示数据扩展插件 "ADS" 中的错误](https://social.technet.microsoft.com/wiki/contents/articles/25298.access-services-report-in-sharepoint-site-shows-error-in-data-extension-ads.aspx)。</span><span class="sxs-lookup"><span data-stu-id="0e14f-152">For the latest information on using ADS extension with [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] connected mode, see [Access Services Report in SharePoint Site shows error in data extension 'ADS'](https://social.technet.microsoft.com/wiki/contents/articles/25298.access-services-report-in-sharepoint-site-shows-error-in-data-extension-ads.aspx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e14f-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0e14f-153">See Also</span></span>  
 [<span data-ttu-id="0e14f-154">Reporting Services 支持的数据源 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="0e14f-154">Data Sources Supported by Reporting Services &#40;SSRS&#41;</span></span>](create-deploy-and-manage-mobile-and-paginated-reports.md)  
  
