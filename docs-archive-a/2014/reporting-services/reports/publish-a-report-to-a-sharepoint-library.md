---
title: 将报表发布到 SharePoint 库 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- deploying [Reporting Services], reports in SharePoint integrated mode
- SharePoint integration [Reporting Services], publishing to a library
- publishing reports [Reporting Services], to a SharePoint library
ms.assetid: 3f6dfc28-50d8-4231-bd25-871b5f77cce6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 23b74ffb04bf1e13523dcf6ec5d774089d80f73b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687448"
---
# <a name="publish-a-report-to-a-sharepoint-library"></a><span data-ttu-id="3bf22-102">将报表发布到 SharePoint 库</span><span class="sxs-lookup"><span data-stu-id="3bf22-102">Publish a Report to a SharePoint Library</span></span>
  <span data-ttu-id="3bf22-103">若要将报表发布到配置为 SharePoint 集成模式的 SharePoint 站点，必须在报表设计器中设置项目属性。</span><span class="sxs-lookup"><span data-stu-id="3bf22-103">To publish a report to a SharePoint site configured for SharePoint integration, you must set the project properties in Report Designer.</span></span> <span data-ttu-id="3bf22-104">在项目属性中，对服务器、报表和共享数据源的所有引用都必须为完全限定的 URL。</span><span class="sxs-lookup"><span data-stu-id="3bf22-104">In the project properties, all references to servers, reports, and shared data sources must be fully qualified URLs.</span></span> <span data-ttu-id="3bf22-105">在报表定义中，对子报表、钻取报表以及资源（如基于 Web 的图像）的所有引用都必须为完全限定的 URL。</span><span class="sxs-lookup"><span data-stu-id="3bf22-105">In the report definition, all references to subreports, drillthrough reports, and resources such as Web-based images, must be fully qualified URLS.</span></span>  
  
 <span data-ttu-id="3bf22-106">必须对 SharePoint 站点拥有 **“成员”** 或 **“所有者”** 权限，才能设置项目的属性。</span><span class="sxs-lookup"><span data-stu-id="3bf22-106">You must have **Member** or **Owner** permission on the SharePoint site to set the properties on the project.</span></span> <span data-ttu-id="3bf22-107">有关详细信息，请参阅 [用于 SharePoint 模式下在报表服务器上已发布的报表项的 URL 示例 (SSRS)](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="3bf22-107">For more information, see [URL Examples for Published Report Items on a Report Server in SharePoint Mode &#40;SSRS&#41;](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md).</span></span>  
  
### <a name="to-publish-a-report-to-a-sharepoint-site"></a><span data-ttu-id="3bf22-108">将报表发布到 SharePoint 站点</span><span class="sxs-lookup"><span data-stu-id="3bf22-108">To publish a report to a SharePoint site</span></span>  
  
1.  <span data-ttu-id="3bf22-109">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开现有的或新的报表服务器项目。</span><span class="sxs-lookup"><span data-stu-id="3bf22-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open an existing or new Report Server project.</span></span>  
  
2.  <span data-ttu-id="3bf22-110">在 **“项目”** 菜单中单击 **“属性”**。</span><span class="sxs-lookup"><span data-stu-id="3bf22-110">From the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="3bf22-111">此时将打开 " _\<project>_ **属性页**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="3bf22-111">The _\<project>_**Property Pages** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="3bf22-112">在 **“配置”** 列表中，选择要用于生成并发布报表的解决方案生成配置的名称。</span><span class="sxs-lookup"><span data-stu-id="3bf22-112">In the **Configuration** list, select the name of a solution build configuration to use to build and publish your report.</span></span> <span data-ttu-id="3bf22-113">当前配置作为**Active** (*\<configuration>*) 列出。</span><span class="sxs-lookup"><span data-stu-id="3bf22-113">The current configuration is listed as **Active**(*\<configuration>*).</span></span>  
  
4.  <span data-ttu-id="3bf22-114">如果想在项目中发布共享数据源，并覆盖以前发布的共享数据源，请将 **OverwriteDataSources** 设置为 **True**。</span><span class="sxs-lookup"><span data-stu-id="3bf22-114">If you want to publish the shared data sources in your project and overwrite previously published shared data sources, set **OverwriteDataSources** to **True**.</span></span>  
  
5.  <span data-ttu-id="3bf22-115"> (**TargetDataSourceFolder**的可选) 中，键入指向 SharePoint 库或库文件夹的 URL (例如， *http://TestServer/TestSite/Documents/DataSources)* 。</span><span class="sxs-lookup"><span data-stu-id="3bf22-115">(Optional) For **TargetDataSourceFolder**, type a URL to a SharePoint library or library folder (for example, *http://TestServer/TestSite/Documents/DataSources)*.</span></span>  
  
     <span data-ttu-id="3bf22-116">如果不指定值，将使用 **TargetReportFolder** 值。</span><span class="sxs-lookup"><span data-stu-id="3bf22-116">If you do not specify a value, the **TargetReportFolder** value is used.</span></span>  
  
6.  <span data-ttu-id="3bf22-117">对于**TargetReportFolder**，键入指向库或库文件夹的 URL (例如， *http://TestServer/TestSite/Documents/Reports)* 。</span><span class="sxs-lookup"><span data-stu-id="3bf22-117">For **TargetReportFolder**, type a URL to a library or library folder (for example, *http://TestServer/TestSite/Documents/Reports)*.</span></span>  
  
7.  <span data-ttu-id="3bf22-118">对于 **TargetServerURL**，键入指向 SharePoint 顶级站点或子站点的 URL。</span><span class="sxs-lookup"><span data-stu-id="3bf22-118">For **TargetServerURL**, type a URL to a SharePoint top-level site or subsite.</span></span> <span data-ttu-id="3bf22-119">如果不指定站点，将使用默认的顶层站点 (例如，、 *http://servername* *http://servername/site* 或 *http://servername/site/subsite*) 。</span><span class="sxs-lookup"><span data-stu-id="3bf22-119">If you do not specify a site, the default top-level site is used (for example, *http://servername*, *http://servername/site*, or *http://servername/site/subsite*).</span></span>  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
9. <span data-ttu-id="3bf22-120">在解决方案资源管理器中，右键单击要发布的报表，然后单击“部署”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3bf22-120">In Solution Explorer, right-click the report you want to publish, and click **Deploy**.</span></span> <span data-ttu-id="3bf22-121">报表将发布到 **TargetReportFolder**中指定的位置。</span><span class="sxs-lookup"><span data-stu-id="3bf22-121">The report is published to the location specified in **TargetReportFolder**.</span></span> <span data-ttu-id="3bf22-122">部署错误将显示在输出窗口中。</span><span class="sxs-lookup"><span data-stu-id="3bf22-122">Deployment errors appear in the Output window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bf22-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3bf22-123">See Also</span></span>  
 <span data-ttu-id="3bf22-124">["项目属性页" 对话框](../tools/project-property-pages-dialog-box.md) </span><span class="sxs-lookup"><span data-stu-id="3bf22-124">[Project Property Pages Dialog Box](../tools/project-property-pages-dialog-box.md) </span></span>  
 <span data-ttu-id="3bf22-125">[设置部署属性 &#40;Reporting Services&#41;](../tools/set-deployment-properties-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="3bf22-125">[Set Deployment Properties &#40;Reporting Services&#41;](../tools/set-deployment-properties-reporting-services.md) </span></span>  
 <span data-ttu-id="3bf22-126">[将报表发布到报表服务器](publishing-reports-to-a-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="3bf22-126">[Publishing Reports to a Report Server](publishing-reports-to-a-report-server.md) </span></span>  
 <span data-ttu-id="3bf22-127">[SharePoint 模式下的报表服务器上已发布报表项的 URL 示例 &#40;SSRS&#41;](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md) </span><span class="sxs-lookup"><span data-stu-id="3bf22-127">[URL Examples for Published Report Items on a Report Server in SharePoint Mode &#40;SSRS&#41;](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md) </span></span>  
 [<span data-ttu-id="3bf22-128">将 Office 数据连接 (.odc) 用于报表（SharePoint 集成模式下的 Reporting Services）</span><span class="sxs-lookup"><span data-stu-id="3bf22-128">Use an Office Data Connection &#40;.odc&#41; with Reports &#40;Reporting Services in SharePoint Integrated Mode&#41;</span></span>](../report-data/use-an-office-data-connection-odc-with-reports.md)  
  
  
