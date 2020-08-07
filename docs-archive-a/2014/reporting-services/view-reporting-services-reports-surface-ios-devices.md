---
title: 查看 Microsoft Surface 设备和 Apple iOS 设备上的 Reporting Services 报告 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- iPad
- Safari
- SSRS
- Report Viewer [Reporting Services]
- iOS
ms.assetid: 2124bcf5-d60a-475f-a4ae-de6df44d2860
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: db52ed500559969ae52eb9477caa6b410889c1d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588903"
---
# <a name="view-reporting-services-reports-on-microsoft-surface-devices-and--apple-ios-devices"></a><span data-ttu-id="95825-102">在 Microsoft Surface 设备和 Apple iOS 设备上查看 Reporting Services 报表</span><span class="sxs-lookup"><span data-stu-id="95825-102">View Reporting Services Reports on Microsoft Surface Devices and  Apple iOS Devices</span></span>
  <span data-ttu-id="95825-103">本文介绍 Microsoft Surface 设备和装有 Apple iOS 6 和 Apple Safari 的设备（如 iPad）支持的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 功能和工作流。</span><span class="sxs-lookup"><span data-stu-id="95825-103">This article describes the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features and workflows supported for Microsoft Surface devices, and devices with Apple iOS 6 and Apple Safari such as the iPad.</span></span>

## <a name="view-and-interact-with-reports"></a><span data-ttu-id="95825-104">查看报表以及与报表交互</span><span class="sxs-lookup"><span data-stu-id="95825-104">View and Interact With Reports</span></span>
 <span data-ttu-id="95825-105">从 [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)]开始， [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 支持在 Microsoft Surface 设备和装有 Apple iOS 6 和 Apple Safari 浏览器的设备（如 iPad）上查看报表以及与这些报表执行基本的交互操作。</span><span class="sxs-lookup"><span data-stu-id="95825-105">Starting with [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)], [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] supports viewing and basic interactivity with reports on Microsoft Surface devices, and devices with Apple iOS 6 and Apple Safari browser such as the iPad.</span></span> <span data-ttu-id="95825-106">您还可以使用 Microsoft Surface 设备发布报表。</span><span class="sxs-lookup"><span data-stu-id="95825-106">You can also publish reports using Microsoft Surface devices.</span></span>

 <span data-ttu-id="95825-107">![IPad 桌面](media/videothumbnail.jpg "IPad 桌面")观看有关在 iPad 上查看报表的演示。</span><span class="sxs-lookup"><span data-stu-id="95825-107">![IPad Desktop](media/videothumbnail.jpg "IPad Desktop") Watch a demonstration of viewing reports on an iPad.</span></span>

 <span data-ttu-id="95825-108">您还可以在 Windows Phone 8 设备上查看 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 报表。</span><span class="sxs-lookup"><span data-stu-id="95825-108">You can also view [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] reports on a Windows Phone 8 device.</span></span>

 <span data-ttu-id="95825-109">为了利用在本主题中介绍的功能，请安装以下产品之一：</span><span class="sxs-lookup"><span data-stu-id="95825-109">To utilize the features described in this topic, install one of the following:</span></span>

-   <span data-ttu-id="95825-110">对于本机模式报表服务器，安装 [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)] 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="95825-110">For a native mode report server, install [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)] or later.</span></span>

     [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)]<span data-ttu-id="95825-111">可从[Microsoft 下载中心](https://www.microsoft.com/download/details.aspx?id=35575)下载。</span><span class="sxs-lookup"><span data-stu-id="95825-111">is available for download from the [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=35575).</span></span>

-   <span data-ttu-id="95825-112">对于 SharePoint 模式报表服务器，请安装适用于 SharePoint 产品的 [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)] 外接程序的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="95825-112">For a SharePoint mode report server, install [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)] or later of the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] add-in for SharePoint products.</span></span>

 <span data-ttu-id="95825-113">**若要在 iPad 设备或 Microsoft Surface 设备上查看报表并与之交互**</span><span class="sxs-lookup"><span data-stu-id="95825-113">**To view and interact with a report on an iPad device or Microsoft Surface device**</span></span>

1.  <span data-ttu-id="95825-114">确保您可以连接到报表所在的报表服务器或 SharePoint 站点。</span><span class="sxs-lookup"><span data-stu-id="95825-114">Make sure that you can connect to the report server or SharePoint site where the report resides.</span></span>

2.  <span data-ttu-id="95825-115">通过执行下列操作之一，打开报表。</span><span class="sxs-lookup"><span data-stu-id="95825-115">Open the report by doing one of the following.</span></span>

    -   <span data-ttu-id="95825-116">**从电子邮件启动：** 从 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 订阅所创建的电子邮件中，轻按报表的 URL。</span><span class="sxs-lookup"><span data-stu-id="95825-116">**Start from e-mail:** From an e-mail that is created by a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] subscription, tap the URL of the report.</span></span> <span data-ttu-id="95825-117">该报表将在浏览器中打开。</span><span class="sxs-lookup"><span data-stu-id="95825-117">The report will open in the browser.</span></span>

    -   <span data-ttu-id="95825-118">**从报表服务器启动：** 浏览 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 报表服务器上的目录，然后点击报表名称以打开报表。</span><span class="sxs-lookup"><span data-stu-id="95825-118">**Start from Report Server:** Browse the directory on the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] report server, and then tap the report name to open the report.</span></span>

    -   <span data-ttu-id="95825-119">**从 SharePoint 文档库启动：** 浏览到包含 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 报表的 SharePoint 文档库，然后点击报表名称。</span><span class="sxs-lookup"><span data-stu-id="95825-119">**Start from a SharePoint document library:** Browse to a SharePoint document library that contains [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] reports, and then tap the report name.</span></span> <span data-ttu-id="95825-120">您可以查看报表和与报表交互。</span><span class="sxs-lookup"><span data-stu-id="95825-120">You can view and interact with the report.</span></span>

        > [!IMPORTANT]
        >  <span data-ttu-id="95825-121"> 对于 iPad，请确保针对 Safari 的 **“专用浏览”** 属性已禁用。</span><span class="sxs-lookup"><span data-stu-id="95825-121">For the iPad, ensure that the **Private Browsing** property for Safari is turned off.</span></span>

    -   <span data-ttu-id="95825-122">**SharePoint Web 部件：** 如果 Web 部件已添加到 SharePoint 页面，你可以查看 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 报表。</span><span class="sxs-lookup"><span data-stu-id="95825-122">**SharePoint web part:** If the web part has been added to a SharePoint page, you can view [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] reports.</span></span>

3.  <span data-ttu-id="95825-123">在 Microsoft Surface 设备上，还可以使用报表管理器打开报表。</span><span class="sxs-lookup"><span data-stu-id="95825-123">On your Microsoft Surface device, you can also open the report by using Report Manager.</span></span> <span data-ttu-id="95825-124">浏览 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 报表服务器中的目录，然后轻按报表名称以打开该报表。</span><span class="sxs-lookup"><span data-stu-id="95825-124">Browse the directory in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Report Manager, and then tap the report name to open the report.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="95825-125">iPad 不支持在报表管理器中查看报表。</span><span class="sxs-lookup"><span data-stu-id="95825-125">Viewing reports in Report Manager is not supported on an iPad.</span></span>

4.  <span data-ttu-id="95825-126">通过执行以下操作进行滚动和缩放。</span><span class="sxs-lookup"><span data-stu-id="95825-126">Scroll and zoom by doing the following.</span></span>

    -   <span data-ttu-id="95825-127">若要滚动显示报表，请用手指在屏幕上向上、下、左、右拖动。</span><span class="sxs-lookup"><span data-stu-id="95825-127">To scroll the report, drag your finger across the screen (up, down, left or right).</span></span> <span data-ttu-id="95825-128">这是滑动手势。</span><span class="sxs-lookup"><span data-stu-id="95825-128">This is the swipe gesture.</span></span>

    -   <span data-ttu-id="95825-129">若要放大，请将两指置于屏幕上并分开两指。</span><span class="sxs-lookup"><span data-stu-id="95825-129">To zoom in, place two fingers on the screen and separate the fingers.</span></span> <span data-ttu-id="95825-130">若要缩小，请将两指置于屏幕上并合拢两指。</span><span class="sxs-lookup"><span data-stu-id="95825-130">To zoom out, place two fingers on the screen and move the fingers together.</span></span> <span data-ttu-id="95825-131">这是捏合手势。</span><span class="sxs-lookup"><span data-stu-id="95825-131">This is the pinch gesture.</span></span>

5.  <span data-ttu-id="95825-132">通过执行以下操作进行报表导航和交互。</span><span class="sxs-lookup"><span data-stu-id="95825-132">Navigate and interact with the report by doing the following.</span></span>

    -   <span data-ttu-id="95825-133">通过轻按加号 (+) 执行折叠操作以及轻按减号 (-) 执行展开操作，折叠和展开报表项以及与组关联的行和列。</span><span class="sxs-lookup"><span data-stu-id="95825-133">Collapse and expand report items, and rows and columns that are associated with groups, by taping the plus (+) sign to collapse and the minus (-) sign to expand.</span></span>

    -   <span data-ttu-id="95825-134">通过轻按排序按钮，切换表中行或矩阵中的行列的升序和降序顺序。</span><span class="sxs-lookup"><span data-stu-id="95825-134">Toggle between ascending and descending order for rows in a table or for rows and columns in a matrix, by tapping the sort button.</span></span> <span data-ttu-id="95825-135">排序按钮通常位于列标题中。</span><span class="sxs-lookup"><span data-stu-id="95825-135">The sort button is usually located in the column header.</span></span>

    -   <span data-ttu-id="95825-136">通过轻按报表顶端附近的箭头按钮，展开和折叠参数窗格。</span><span class="sxs-lookup"><span data-stu-id="95825-136">Expand and collapse the parameter pane, by tapping the arrow button near the top of the report.</span></span>

    -   <span data-ttu-id="95825-137">通过轻按参数旁边的框或控件，选择参数值。</span><span class="sxs-lookup"><span data-stu-id="95825-137">Select a parameter value by tapping the box or control next to the parameter.</span></span> <span data-ttu-id="95825-138">轻按 **“查看报表”** 将参数值应用到报表中。</span><span class="sxs-lookup"><span data-stu-id="95825-138">Tap **View Report** to apply the parameter value to the report.</span></span>

    -   <span data-ttu-id="95825-139">通过轻按 **“查找”** 旁边的框，键入搜索项，然后轻按 **“查找”**，可以搜索报表内容。</span><span class="sxs-lookup"><span data-stu-id="95825-139">Search the report content by taping the box next to **Find**, typing a search term, and then taping **Find**.</span></span>

    -   <span data-ttu-id="95825-140">通过轻按导航按钮或轻按这些按钮旁边的文本框并键入页码，可在报表页之间导航。</span><span class="sxs-lookup"><span data-stu-id="95825-140">Navigate the report pages by tapping the navigation buttons, or tapping the text box next to the buttons and typing the page number.</span></span>

    -   <span data-ttu-id="95825-141">通过轻按添加到报表项（如文本框、图像、图表和仪表）的超链接导航到相应的 URL。</span><span class="sxs-lookup"><span data-stu-id="95825-141">Navigate to URLs by taping hyperlinks that have been added to report items such as text boxes, images, charts, and gauges.</span></span>

    -   <span data-ttu-id="95825-142">通过轻按 **“导出”** 下拉菜单图标，然后轻按文件格式来导出报表。</span><span class="sxs-lookup"><span data-stu-id="95825-142">Export the report by tapping the icon for the **Export drop down menu** and then tapping a file format.</span></span>

        -   <span data-ttu-id="95825-143">如果要在 Microsoft Surface 设备上查看报表，可以将报表导出为以下格式之一。</span><span class="sxs-lookup"><span data-stu-id="95825-143">If you're viewing the report on a Microsoft Surface device, you can export the report to one of the following formats.</span></span>

            -   <span data-ttu-id="95825-144">具有报表数据的 XML 文件</span><span class="sxs-lookup"><span data-stu-id="95825-144">XML file with report data</span></span>

            -   <span data-ttu-id="95825-145">CSV（逗号分隔）</span><span class="sxs-lookup"><span data-stu-id="95825-145">CSV (comma delimited)</span></span>

            -   <span data-ttu-id="95825-146">PDF</span><span class="sxs-lookup"><span data-stu-id="95825-146">PDF</span></span>

            -   <span data-ttu-id="95825-147">MHTML（Web 存档）</span><span class="sxs-lookup"><span data-stu-id="95825-147">MHTML (web archive)</span></span>

            -   <span data-ttu-id="95825-148">Excel</span><span class="sxs-lookup"><span data-stu-id="95825-148">Excel</span></span>

            -   <span data-ttu-id="95825-149">TIFF</span><span class="sxs-lookup"><span data-stu-id="95825-149">TIFF</span></span>

            -   <span data-ttu-id="95825-150">Word</span><span class="sxs-lookup"><span data-stu-id="95825-150">Word</span></span>

        -   <span data-ttu-id="95825-151">如果要在 iPad 上查看报表，可以将报表导出为 TIFF 或 PDF 文件。</span><span class="sxs-lookup"><span data-stu-id="95825-151">If you're viewing the report on an iPad, you can export the report as a TIFF or PDF file.</span></span>

## <a name="authentication"></a><span data-ttu-id="95825-152">身份验证</span><span class="sxs-lookup"><span data-stu-id="95825-152">Authentication</span></span>
 <span data-ttu-id="95825-153">RSWindowsNTLM 身份验证和 RSWindowsBasic 身份验证可用于本机模式下的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 或 iPad。</span><span class="sxs-lookup"><span data-stu-id="95825-153">RSWindowsNTLM authentication and RSWindowsBasic authentication work with [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in native mode and the iPad.</span></span>

 <span data-ttu-id="95825-154">通常，建议不要在非 Https 环境中使用 RSWindowsBasic，因为这种类型的身份验证不为传输的凭证提供任何保密性。</span><span class="sxs-lookup"><span data-stu-id="95825-154">In general, it is recommended that RSWindowsBasic is not used in non-https environments because this type of authentication provides no confidentiality for the transmitted credentials.</span></span>

 <span data-ttu-id="95825-155">有关 RSWindowsNTLM 和 RSWindowsBasic 身份验证的详细信息，请参阅 [Authentication with the Report Server](security/authentication-with-the-report-server.md)。</span><span class="sxs-lookup"><span data-stu-id="95825-155">For more information about RSWindowsNTLM and RSWindowsBasic authentication, see [Authentication with the Report Server](security/authentication-with-the-report-server.md).</span></span>

## <a name="uploading-reports"></a><span data-ttu-id="95825-156">上载报表</span><span class="sxs-lookup"><span data-stu-id="95825-156">Uploading Reports</span></span>
 <span data-ttu-id="95825-157">如果您具有适当的权限，可以使用以下方法之一从 Microsoft Surface 设备发布报表。</span><span class="sxs-lookup"><span data-stu-id="95825-157">You can publish reports from a Microsoft Surface device using one of the following methods, if you have the appropriate permissions.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="95825-158">在 iPad 上不支持这些方法。</span><span class="sxs-lookup"><span data-stu-id="95825-158">These methods are not supported on the iPad.</span></span>

-   <span data-ttu-id="95825-159">通过打开一个 SharePoint 文档库，然后轻按 **“上载文档”**，将报表定义文件 (.rdl) 上载到该文档库。</span><span class="sxs-lookup"><span data-stu-id="95825-159">Upload a report definition file (.rdl) to a SharePoint document library by opening the library and tapping **Upload Document**.</span></span>

-   <span data-ttu-id="95825-160">通过打开报表管理器，然后轻按 **“上载文件”**，将报表定义文件上载到报表服务器数据库。</span><span class="sxs-lookup"><span data-stu-id="95825-160">Upload a report definition file to the report server database by opening Report Manager and tapping **Upload File**.</span></span>

## <a name="additional-information"></a><span data-ttu-id="95825-161">其他信息</span><span class="sxs-lookup"><span data-stu-id="95825-161">Additional Information</span></span>
 <span data-ttu-id="95825-162">有关 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 和支持的浏览器的详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="95825-162">For more information on [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] and supported browsers, see:</span></span>

-   [<span data-ttu-id="95825-163">规划 Reporting Services 和 Power View 浏览器支持 &#40;Reporting Services 2014&#41;</span><span class="sxs-lookup"><span data-stu-id="95825-163">Planning for Reporting Services and Power View Browser Support &#40;Reporting Services 2014&#41;</span></span>](../../2014/reporting-services/browser-support-for-reporting-services-and-power-view.md)

 <span data-ttu-id="95825-164">有关 Microsoft 商业智能和移动设备的详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="95825-164">For more information on Microsoft Business Intelligence and Mobile devices, see the following:</span></span>

-   <span data-ttu-id="95825-165">[移动设备和 SharePoint 2013 (的概述](https://technet.microsoft.com/library/fp161351\(v=office.15\).aspx) https://technet.microsoft.com/library/fp161351(v=office.15).aspx) 。</span><span class="sxs-lookup"><span data-stu-id="95825-165">[Overview of mobile devices and SharePoint 2013](https://technet.microsoft.com/library/fp161351\(v=office.15\).aspx) (https://technet.microsoft.com/library/fp161351(v=office.15).aspx).</span></span>

-   <span data-ttu-id="95825-166">[SharePoint 2013 (中支持的移动设备浏览器](https://technet.microsoft.com/library/fp161353\(v=office.15\).aspx) https://technet.microsoft.com/library/fp161353(v=office.15).aspx) 。</span><span class="sxs-lookup"><span data-stu-id="95825-166">[Supported mobile device browsers in SharePoint 2013](https://technet.microsoft.com/library/fp161353\(v=office.15\).aspx) (https://technet.microsoft.com/library/fp161353(v=office.15).aspx).</span></span>

-   <span data-ttu-id="95825-167">[在 Apple iPad 设备上查看报表和记分卡 (SharePoint Server 2010) ](https://technet.microsoft.com/library/hh697482.aspx) (https://technet.microsoft.com/library/hh697482.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="95825-167">[Viewing reports and scorecards on Apple iPad devices (SharePoint Server 2010)](https://technet.microsoft.com/library/hh697482.aspx) (https://technet.microsoft.com/library/hh697482.aspx).</span></span>

-   <span data-ttu-id="95825-168">[查看 iPad (视频)  (Reporting Services 报表](https://technet.microsoft.com/sqlserver/jj873792.aspx) https://technet.microsoft.com/sqlserver/jj873792.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="95825-168">[Viewing Reporting Services Reports on an iPad (video)](https://technet.microsoft.com/sqlserver/jj873792.aspx) (https://technet.microsoft.com/sqlserver/jj873792.aspx).</span></span>

-   [<span data-ttu-id="95825-169">在 Microsoft Surface RT 设备上查看 Reporting Services 报表（视频）</span><span class="sxs-lookup"><span data-stu-id="95825-169">Viewing Reporting Services Reports on a Microsoft Surface RT Device (video)</span></span>](https://technet.microsoft.com/sqlserver/dn146017)


