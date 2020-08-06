---
title: 将共享数据源发布到 SharePoint 库 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- data sources [Reporting Services], publishing to a SharePoint library
- SharePoint integration [Reporting Services], publishing to a library
- publishing reports [Reporting Services], to a SharePoint library
ms.assetid: 966ed425-3ce2-4e76-8237-3c1c977954ae
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 77ee25535ccb98638ae02ca64e3bcbfc88291c12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687444"
---
# <a name="publish-a-shared-data-source-to-a-sharepoint-library"></a><span data-ttu-id="9ee14-102">将共享数据源发布到 SharePoint 库</span><span class="sxs-lookup"><span data-stu-id="9ee14-102">Publish a Shared Data Source to a SharePoint Library</span></span>
  <span data-ttu-id="9ee14-103">若要将共享数据源发布到在 SharePoint 集成模式下运行的报表服务器，必须在报表设计器中设置报表的项目属性。</span><span class="sxs-lookup"><span data-stu-id="9ee14-103">To publish a shared data source to a report server that is running in SharePoint integrated mode, you must set the report project properties in Report Designer.</span></span> <span data-ttu-id="9ee14-104">在项目属性中，对服务器、报表和共享数据源的所有引用都必须为完全限定的 URL。</span><span class="sxs-lookup"><span data-stu-id="9ee14-104">In the project properties, all references to servers, reports, and shared data sources must be fully qualified URLs.</span></span>  
  
 <span data-ttu-id="9ee14-105">必须对 SharePoint 站点拥有 **“成员”** 或 **“所有者”** 权限。</span><span class="sxs-lookup"><span data-stu-id="9ee14-105">You must have **Member** or **Owner** permission on the SharePoint site.</span></span> <span data-ttu-id="9ee14-106">有关详细信息，请参阅 [用于 SharePoint 模式下在报表服务器上已发布的报表项的 URL 示例 (SSRS)](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="9ee14-106">For more information, see [URL Examples for Published Report Items on a Report Server in SharePoint Mode &#40;SSRS&#41;](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md).</span></span>  
  
### <a name="to-publish-a-shared-data-source-to-a-sharepoint-site"></a><span data-ttu-id="9ee14-107">将共享数据源发布到 SharePoint 站点。</span><span class="sxs-lookup"><span data-stu-id="9ee14-107">To publish a shared data source to a SharePoint site</span></span>  
  
1.  <span data-ttu-id="9ee14-108">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开现有的或新的报表服务器项目。</span><span class="sxs-lookup"><span data-stu-id="9ee14-108">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open your existing or new Report Server project.</span></span>  
  
2.  <span data-ttu-id="9ee14-109">在“项目”菜单上，单击“属性” 。</span><span class="sxs-lookup"><span data-stu-id="9ee14-109">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="9ee14-110">此时将打开 " _\<project>_ **属性页**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="9ee14-110">The _\<project>_**Property Pages** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="9ee14-111">选择发布到 SharePoint 站点所用的 **“配置”** 。</span><span class="sxs-lookup"><span data-stu-id="9ee14-111">Choose the **Configuration** you use to publish to a SharePoint site.</span></span>  
  
4.  <span data-ttu-id="9ee14-112">如果想在项目中发布共享数据源，并覆盖以前发布的共享数据源，请将 **OverwriteDataSources** 设置为 **True**。</span><span class="sxs-lookup"><span data-stu-id="9ee14-112">If you want to publish the shared data sources in your project and overwrite previously published shared data sources, set **OverwriteDataSources** to **True**.</span></span>  
  
5.  <span data-ttu-id="9ee14-113">（可选）对于 **TargetDataSourceFolder**，键入指向 SharePoint 库或库文件夹的 URL。</span><span class="sxs-lookup"><span data-stu-id="9ee14-113">(Optional) For **TargetDataSourceFolder**, type a URL to a SharePoint library or library folder.</span></span> <span data-ttu-id="9ee14-114">例如， http://TestServer/TestSite/Documents/DataSources 。</span><span class="sxs-lookup"><span data-stu-id="9ee14-114">For example, *http://TestServer/TestSite/Documents/DataSources*.</span></span>  
  
     <span data-ttu-id="9ee14-115">如果不指定值，将使用 **TargetReportFolder** 值。</span><span class="sxs-lookup"><span data-stu-id="9ee14-115">If you do not specify a value, the **TargetReportFolder** value is used.</span></span>  
  
6.  <span data-ttu-id="9ee14-116">对于 **TargetReportFolder**，键入指向库或库文件夹的 URL。</span><span class="sxs-lookup"><span data-stu-id="9ee14-116">For **TargetReportFolder**, type a URL to a library or library folder.</span></span> <span data-ttu-id="9ee14-117">例如，http://TestServer/TestSite/Documents/Reports\*\*。</span><span class="sxs-lookup"><span data-stu-id="9ee14-117">For example, http:*//TestServer/TestSite/Documents/Reports*.</span></span>  
  
7.  <span data-ttu-id="9ee14-118">对于 **TargetServerURL**，键入指向 SharePoint 顶级站点或子站点的 URL。</span><span class="sxs-lookup"><span data-stu-id="9ee14-118">For **TargetServerURL**, type a URL to a SharePoint top-level site or subsite.</span></span> <span data-ttu-id="9ee14-119">如果不指定站点，将使用默认顶级站点。</span><span class="sxs-lookup"><span data-stu-id="9ee14-119">If you do not specify a site, the default top-level site is used.</span></span> <span data-ttu-id="9ee14-120">例如，http://服务器名**、http://服务器名**/站点\*\* 或 http://服务器名**/站点**/子站点\*\*。</span><span class="sxs-lookup"><span data-stu-id="9ee14-120">For example, http://*servername*, http://*servername*/*site*, or http://*servername*/*site*/*subsite*.</span></span>  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
9. <span data-ttu-id="9ee14-121">在解决方案资源管理器中，右键单击要发布的共享数据源，然后单击“部署”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9ee14-121">In Solution Explorer, right-click the shared data source you want to publish, and click **Deploy**.</span></span> <span data-ttu-id="9ee14-122">数据源将发布到 **TargetDataSourceFolder**中指定的位置。</span><span class="sxs-lookup"><span data-stu-id="9ee14-122">The data source is published to the location specified in **TargetDataSourceFolder**.</span></span> <span data-ttu-id="9ee14-123">部署错误将显示在输出窗口中。</span><span class="sxs-lookup"><span data-stu-id="9ee14-123">Deployment errors appear in the Output window.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9ee14-124">将共享数据源发布到 SharePoint 站点后，该数据源文件的扩展名会更改为 .rsds。</span><span class="sxs-lookup"><span data-stu-id="9ee14-124">After you publish a shared data source to a SharePoint site, the file name extension is changed to .rsds.</span></span> <span data-ttu-id="9ee14-125">可以直接在 SharePoint 站点上编辑和管理共享数据源。</span><span class="sxs-lookup"><span data-stu-id="9ee14-125">You can edit and manage a shared data source directly on the SharePoint site.</span></span> <span data-ttu-id="9ee14-126">有关详细信息，请参阅[创建和管理共享数据源（SharePoint 集成模式下的 Reporting Services）](../create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="9ee14-126">For more information, see [Create and Manage Shared Data Sources &#40;Reporting Services in SharePoint Integrated Mode&#41;](../create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ee14-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9ee14-127">See Also</span></span>  
 <span data-ttu-id="9ee14-128">[将报表发布到 SharePoint 库](publish-a-report-to-a-sharepoint-library.md) </span><span class="sxs-lookup"><span data-stu-id="9ee14-128">[Publish a Report to a SharePoint Library](publish-a-report-to-a-sharepoint-library.md) </span></span>  
 <span data-ttu-id="9ee14-129">[SharePoint 模式下的报表服务器上已发布报表项的 URL 示例 &#40;SSRS&#41;](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md) </span><span class="sxs-lookup"><span data-stu-id="9ee14-129">[URL Examples for Published Report Items on a Report Server in SharePoint Mode &#40;SSRS&#41;](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md) </span></span>  
 <span data-ttu-id="9ee14-130">["项目属性页" 对话框](../tools/project-property-pages-dialog-box.md) </span><span class="sxs-lookup"><span data-stu-id="9ee14-130">[Project Property Pages Dialog Box](../tools/project-property-pages-dialog-box.md) </span></span>  
 <span data-ttu-id="9ee14-131">[设置部署属性 &#40;Reporting Services&#41;](../tools/set-deployment-properties-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="9ee14-131">[Set Deployment Properties &#40;Reporting Services&#41;](../tools/set-deployment-properties-reporting-services.md) </span></span>  
 <span data-ttu-id="9ee14-132">[将报表发布到报表服务器](publishing-reports-to-a-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="9ee14-132">[Publishing Reports to a Report Server](publishing-reports-to-a-report-server.md) </span></span>  
 [<span data-ttu-id="9ee14-133">将 Office 数据连接 (.odc) 用于报表（SharePoint 集成模式下的 Reporting Services）</span><span class="sxs-lookup"><span data-stu-id="9ee14-133">Use an Office Data Connection &#40;.odc&#41; with Reports &#40;Reporting Services in SharePoint Integrated Mode&#41;</span></span>](../report-data/use-an-office-data-connection-odc-with-reports.md)  
  
  
