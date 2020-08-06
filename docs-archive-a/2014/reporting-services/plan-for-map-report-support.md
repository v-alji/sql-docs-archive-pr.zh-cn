---
title: 规划地图报表支持 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5ddc97a7-7ee5-475d-bc49-3b814dce7e19
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f3d1e1774e44ae879b8c01e66289cefd4d42ee1c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692778"
---
# <a name="plan-for-map-report-support"></a><span data-ttu-id="38577-102">计划地图报表支持</span><span class="sxs-lookup"><span data-stu-id="38577-102">Plan for Map Report Support</span></span>
  [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]<span data-ttu-id="38577-103">支持使用空间数据源的地图报表。</span><span class="sxs-lookup"><span data-stu-id="38577-103">supports map reports that use spatial data sources.</span></span> <span data-ttu-id="38577-104">空间数据可来自 SQL Server 数据库或 ESRI 形状文件，或者来自随 Reporting Services 或报表生成器一起安装的地图库。</span><span class="sxs-lookup"><span data-stu-id="38577-104">Spatial data can come from SQL Server databases, from ESRI Shapefiles, or from the Map Gallery that is installed with either Reporting Services or Report Builder.</span></span> <span data-ttu-id="38577-105">地图还可以显示 Bing 地图图块的背景。</span><span class="sxs-lookup"><span data-stu-id="38577-105">A map can also display a background of Bing map tiles.</span></span> <span data-ttu-id="38577-106">报表作者可以创建一个报表，该报表可以将空间数据或 Bing 地图图块指定为动态的和在运行时检索的，也可以指定为静态的和嵌入在报表定义中的。</span><span class="sxs-lookup"><span data-stu-id="38577-106">A report author can create a report that specifies spatial data or Bing map tiles as dynamic and retrieved at run time or as static and embedded in the report definition.</span></span>  
  
## <a name="support-for-bing-maps"></a><span data-ttu-id="38577-107">支持 Bing 地图</span><span class="sxs-lookup"><span data-stu-id="38577-107">Support for Bing Maps</span></span>  
 <span data-ttu-id="38577-108">地图可以包括显示 Bing 地图图块的背景层。</span><span class="sxs-lookup"><span data-stu-id="38577-108">Maps can include a background layer that displays Bing map tiles.</span></span> <span data-ttu-id="38577-109">若要查看具有地图图块层的已发布报表，报表服务器必须配置为从 Bing 地图 Web 服务检索图块。</span><span class="sxs-lookup"><span data-stu-id="38577-109">To view a published report that has a map tile layer, the report server must be configured to retrieve tiles from Bing Maps Web Services.</span></span> <span data-ttu-id="38577-110">有关详细信息，请参阅 [RSReportServer Configuration File](report-server/rsreportserver-config-configuration-file.md)。</span><span class="sxs-lookup"><span data-stu-id="38577-110">For more information, see [RSReportServer Configuration File](report-server/rsreportserver-config-configuration-file.md).</span></span>  
  
 <span data-ttu-id="38577-111">在各报表中，报表作者可以指定是否使用安全套接字层 (SSL) 连接从图块服务器中检索图块。</span><span class="sxs-lookup"><span data-stu-id="38577-111">In each report, report authors can specify whether to use a Secure Sockets Layer (SSL) connection to retrieve tiles from the tile server.</span></span> <span data-ttu-id="38577-112">为此，必须在图块层的属性窗格中将布尔属性 UseSecureConnection 设置为 `true` 。</span><span class="sxs-lookup"><span data-stu-id="38577-112">To do this, in the Properties pane for the tile layer, they must set the Boolean property UseSecureConnection to `true`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="38577-113">有关在报表中使用 Bing 地图图块的详细信息，请参阅 [其他使用条款](https://go.microsoft.com/fwlink/?LinkId=151371) 和 [隐私声明](https://go.microsoft.com/fwlink/?LinkId=151372)。</span><span class="sxs-lookup"><span data-stu-id="38577-113">For more information about the use of Bing map tiles in your report, see [Additional Terms of Use](https://go.microsoft.com/fwlink/?LinkId=151371) and [Privacy Statement](https://go.microsoft.com/fwlink/?LinkId=151372).</span></span>  
  
## <a name="report-design-recommendations"></a><span data-ttu-id="38577-114">报表设计建议</span><span class="sxs-lookup"><span data-stu-id="38577-114">Report Design Recommendations</span></span>  
 <span data-ttu-id="38577-115">地图报表的优秀报表设计要求报表作者在静态和动态空间数据之间权衡利弊，找出满足报表用户需要的平衡点。</span><span class="sxs-lookup"><span data-stu-id="38577-115">Good report design for map reports requires that the report author assess the trade-offs between static and dynamic spatial data and find a balance that serves the report users.</span></span> <span data-ttu-id="38577-116">嵌入的地图元素可能会显著增加报表定义的大小，但会减少查看地图报表所需的时间。</span><span class="sxs-lookup"><span data-stu-id="38577-116">Embedded map elements can significantly increase the size of the report definition, but reduce the time that is required to view the map report.</span></span> <span data-ttu-id="38577-117">动态地图元素会减少报表定义大小，但会增加处理和查看地图所需的时间。</span><span class="sxs-lookup"><span data-stu-id="38577-117">Dynamic map elements reduce the report definition size but increase the time that is required to process and view the map.</span></span> <span data-ttu-id="38577-118">报表作者必须在这些对立的问题之间找到恰当的平衡点。</span><span class="sxs-lookup"><span data-stu-id="38577-118">The report author must find the right balance between these opposing issues.</span></span>  
  
 <span data-ttu-id="38577-119">在报表定义大小是问题所在时，作为报表服务器管理员，您可以鼓励报表设计者减少报表定义中的空间数据量。</span><span class="sxs-lookup"><span data-stu-id="38577-119">When report definition size is an issue, as report server administrator, you can encourage report designers to reduce the amount of spatial data in a report definition.</span></span>  
  
 <span data-ttu-id="38577-120">在以下情况下，地图元素嵌入在报表定义中：</span><span class="sxs-lookup"><span data-stu-id="38577-120">Under the following conditions, map elements are embedded in the report definition:</span></span>  
  
-   <span data-ttu-id="38577-121">在创建报表时，空间数据源位于本地文件系统上。</span><span class="sxs-lookup"><span data-stu-id="38577-121">When the report is created, the spatial data source is on the local file system.</span></span> <span data-ttu-id="38577-122">这包括来自已在本地安装的地图库或 ESRI 形状文件的空间数据。</span><span class="sxs-lookup"><span data-stu-id="38577-122">This includes spatial data from the Map Gallery or ESRI Shapefiles that have been installed locally.</span></span> <span data-ttu-id="38577-123">默认情况下，地图向导和地图层向导嵌入来自本地文件系统上的数据源的空间数据。</span><span class="sxs-lookup"><span data-stu-id="38577-123">By default, the map wizard and map layer wizard embed spatial data from data sources on the local file system.</span></span>  
  
-   <span data-ttu-id="38577-124">报表作者选择该选项可以手动在报表中嵌入空间数据。</span><span class="sxs-lookup"><span data-stu-id="38577-124">The report author chooses the option to embed spatial data manually in the report.</span></span>  
  
 <span data-ttu-id="38577-125">为了有助于减少具有地图的报表定义的大小，报表作者可以使用以下选项中的一个或多个：</span><span class="sxs-lookup"><span data-stu-id="38577-125">To help reduce the size of report definitions that have maps, report authors can use one or more of the following options:</span></span>  
  
-   <span data-ttu-id="38577-126">从报表设计器的中 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ，将 ESRI 形状文件的空间数据源添加到 Report Server 项目。</span><span class="sxs-lookup"><span data-stu-id="38577-126">From Report Designer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], add spatial data sources that are ESRI Shapefiles to the report server project.</span></span> <span data-ttu-id="38577-127">在您部署该项目时，这些 ESRI 形状文件将发布到报表服务器以及报表上。</span><span class="sxs-lookup"><span data-stu-id="38577-127">When you deploy the project, the ESRI Shapefiles are published to the report server in addition to the report.</span></span> <span data-ttu-id="38577-128">在报表作者运行地图向导时，他们可以从 Report Server 项目指定空间数据源，并且地图元素默认情况下不嵌入在报表定义中。</span><span class="sxs-lookup"><span data-stu-id="38577-128">When the report author runs the Map wizard, they can specify a spatial data source from the Report Server project, and the map elements are not embedded in the report definitions by default.</span></span>  
  
-   <span data-ttu-id="38577-129">从报表生成器中，通过从 Report Server 中选择 "形状文件" 来添加 ESRI 形状文件的空间数据源。</span><span class="sxs-lookup"><span data-stu-id="38577-129">From Report Builder, add spatial data sources that are ESRI Shapefiles by selecting Shapefiles from the report server.</span></span> <span data-ttu-id="38577-130">在报表作者运行地图向导时，他们可以从报表服务器中浏览并选择一个空间数据源，并且地图元素默认情况下不嵌入在报表定义中。</span><span class="sxs-lookup"><span data-stu-id="38577-130">When the report author runs the Map wizard, they can browse to and select a spatial data source from the report server, and the map elements are not embedded in the report definitions by default.</span></span>  
  
-   <span data-ttu-id="38577-131">在地图数据必须嵌入地图数据时，调整视区中心和缩放级别以便只包括报表所需的地图数据。</span><span class="sxs-lookup"><span data-stu-id="38577-131">When map data must be embedded map data, adjust the viewport center and zoom level to include just the map data that is needed for the report.</span></span>  
  
 <span data-ttu-id="38577-132">有关详细信息，请[&#40;报表生成器和 SSRS&#41;的映射](report-design/maps-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="38577-132">For more information, [Maps &#40;Report Builder and SSRS&#41;](report-design/maps-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38577-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="38577-133">See Also</span></span>  
 [<span data-ttu-id="38577-134">报表故障排除：地图报表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="38577-134">Troubleshoot Reports: Map Reports &#40;Report Builder and SSRS&#41;</span></span>](report-design/troubleshoot-reports-map-reports-report-builder-and-ssrs.md)  
  
  
