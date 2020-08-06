---
title: 规划地图报表（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: dc0c27a4-7e31-4a15-a0bc-3a02479d5b02
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9403af12887b1850713a212e90ac70305b390d52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682688"
---
# <a name="plan-a-map-report-report-builder-and-ssrs"></a><span data-ttu-id="6159c-102">规划地图报表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="6159c-102">Plan a Map Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="6159c-103">好的报表提供的信息可指导您采取措施或让您洞察实际情况。</span><span class="sxs-lookup"><span data-stu-id="6159c-103">Good reports present information that leads to actions or insights.</span></span> <span data-ttu-id="6159c-104">若要展示分析数据，如某一地理背景下的总销售额或人口统计，您可以将地图添加到报表。</span><span class="sxs-lookup"><span data-stu-id="6159c-104">To present analytical data such as sales totals or demographics against a geographic background, you can add a map to your report.</span></span> <span data-ttu-id="6159c-105">一个地图可以包含多个图层，每个图层都显示由特定类型的空间数据定义的地图元素：代表地点的点、代表路线的线条以及代表区域的多边形。</span><span class="sxs-lookup"><span data-stu-id="6159c-105">A map can contain multiple layers, where each layer displays map elements that are defined by a specific type of spatial data: points that represent locations, lines that represent routes, or polygons that represent areas.</span></span> <span data-ttu-id="6159c-106">您可以将分析数据与每个图层上的地图元素相关联。</span><span class="sxs-lookup"><span data-stu-id="6159c-106">You can associate your analytical data with map elements on each layer.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="specify-the-purpose-of-the-map"></a><a name="MapPurpose"></a> <span data-ttu-id="6159c-107">指定地图的作用</span><span class="sxs-lookup"><span data-stu-id="6159c-107">Specify the Purpose of the Map</span></span>  
 <span data-ttu-id="6159c-108">良好的报表设计可以提供相关的信息以帮助用户采取措施来解决问题。</span><span class="sxs-lookup"><span data-stu-id="6159c-108">Good report design provides information that help users take actions to address issues.</span></span> <span data-ttu-id="6159c-109">若要创建有用的、易于理解的地图显示，请确定您希望地图帮助您回答的问题。</span><span class="sxs-lookup"><span data-stu-id="6159c-109">To create a useful, easily understood map display, decide what questions you want the map to help answer.</span></span> <span data-ttu-id="6159c-110">例如，在某个地图上，您可以实现以下数据类型的可视化，以确定市场商机：</span><span class="sxs-lookup"><span data-stu-id="6159c-110">For example, on a map you can visualize the following types of data to identify market opportunities:</span></span>  
  
-   <span data-ttu-id="6159c-111">每个商店的相关销售额。</span><span class="sxs-lookup"><span data-stu-id="6159c-111">Relative sales for each store.</span></span>  
  
-   <span data-ttu-id="6159c-112">根据相对于商店位置的客户位置，按客户人口统计学分类的销售额。</span><span class="sxs-lookup"><span data-stu-id="6159c-112">Sales categorized by customer demographics, based on customer location relative to store locations.</span></span>  
  
-   <span data-ttu-id="6159c-113">按销售区域划分的比较销售额或其他财务数据。</span><span class="sxs-lookup"><span data-stu-id="6159c-113">Comparative sales or other financial data by sales territory.</span></span>  
  
-   <span data-ttu-id="6159c-114">多个商店不同折扣策略的比较销售额。</span><span class="sxs-lookup"><span data-stu-id="6159c-114">Comparative sales for different discount strategies across multiple stores.</span></span>  
  
 <span data-ttu-id="6159c-115">在确定地图显示的作用之后，必须分析您需要的数据。</span><span class="sxs-lookup"><span data-stu-id="6159c-115">After you identify the purpose of the map display, you must analyze what data you need.</span></span> <span data-ttu-id="6159c-116">分析数据来自报表数据集。</span><span class="sxs-lookup"><span data-stu-id="6159c-116">Analytical data comes from report datasets.</span></span> <span data-ttu-id="6159c-117">位置数据来自您必须指定的空间数据源。</span><span class="sxs-lookup"><span data-stu-id="6159c-117">Location data comes from spatial data sources that you must specify.</span></span>  
  
 
  
##  <a name="specify-the-spatial-and-analytical-data"></a><a name="Data"></a> <span data-ttu-id="6159c-118">指定空间数据和分析数据</span><span class="sxs-lookup"><span data-stu-id="6159c-118">Specify the Spatial and Analytical Data</span></span>  
 <span data-ttu-id="6159c-119">您必须指定您需要哪些空间数据和分析数据。</span><span class="sxs-lookup"><span data-stu-id="6159c-119">You must specify which spatial and analytical data that you need.</span></span>  
  
 <span data-ttu-id="6159c-120">分析数据可来自报表数据集，来自与地图库中的地图一起包括的示例数据，或者来自与 ESRI 形状文件中的空间数据一起包括的分析数据。</span><span class="sxs-lookup"><span data-stu-id="6159c-120">Analytical data comes from a report dataset, from sample data included with a map from the map gallery, or from analytical data included with spatial data in an ESRI Shapefile.</span></span>  
  
 <span data-ttu-id="6159c-121">空间数据采用三种形式：点、线条和多边形。</span><span class="sxs-lookup"><span data-stu-id="6159c-121">Spatial data comes in three forms: points, lines, and polygons.</span></span>  
  
-   <span data-ttu-id="6159c-122">**点：**</span><span class="sxs-lookup"><span data-stu-id="6159c-122">**Points.**</span></span> <span data-ttu-id="6159c-123">点指定位置，例如，市县或商店、饭馆或会议中心的地址。</span><span class="sxs-lookup"><span data-stu-id="6159c-123">Points specify locations, for example, a city or an address for a store, restaurant, or convention center.</span></span> <span data-ttu-id="6159c-124">对于您要在地图上显示的每个位置，您必须提供该位置的空间数据。</span><span class="sxs-lookup"><span data-stu-id="6159c-124">For every location that you want to display on a map, you must provide the spatial data for that location.</span></span> <span data-ttu-id="6159c-125">在向地图添加点之后，您可以在点位置显示标记，并改变标记类型、大小和颜色。</span><span class="sxs-lookup"><span data-stu-id="6159c-125">After you add points to a map, you can display a marker at the point location and vary the marker type, size, and color.</span></span>  
  
-   <span data-ttu-id="6159c-126">**线条：**</span><span class="sxs-lookup"><span data-stu-id="6159c-126">**Lines.**</span></span> <span data-ttu-id="6159c-127">线条指定路径或路线，例如，交货路线或飞行路径。</span><span class="sxs-lookup"><span data-stu-id="6159c-127">Lines specify paths or routes, for example, delivery routes or flight paths.</span></span> <span data-ttu-id="6159c-128">在向地图添加线条之后，可以改变线条颜色和线条宽度。</span><span class="sxs-lookup"><span data-stu-id="6159c-128">After you add a line to a map, you can vary the line color and line width.</span></span>  
  
-   <span data-ttu-id="6159c-129">**多边形：**</span><span class="sxs-lookup"><span data-stu-id="6159c-129">**Polygons.**</span></span> <span data-ttu-id="6159c-130">多边形指定区域，例如，地区、领土、国家/地区、省/自治区/直辖市、省、县、市或城市涵盖的地区、邮政编码、电话交换机或人口普查地区。</span><span class="sxs-lookup"><span data-stu-id="6159c-130">Polygons specify areas, for example, regions, territories, countries, states, provinces, counties, cities, or areas covered by cities, postal codes, telephone exchanges, or census districts.</span></span> <span data-ttu-id="6159c-131">在向地图添加多边形后，除显示轮廓之外，还可以在多边形区域的中心点显示一个标记。</span><span class="sxs-lookup"><span data-stu-id="6159c-131">After you add polygons to a map, in addition to displaying the outline, you can display a marker at the center point of the area of the polygon.</span></span>  
  
 <span data-ttu-id="6159c-132">在确定需要的空间数据之后，您必须为此数据找到源。</span><span class="sxs-lookup"><span data-stu-id="6159c-132">After you identify which spatial data that you need, you must find a source for it.</span></span>  
  
### <a name="find-a-source-for-spatial-data"></a><span data-ttu-id="6159c-133">查找空间数据的源</span><span class="sxs-lookup"><span data-stu-id="6159c-133">Find a Source for Spatial Data</span></span>  
 <span data-ttu-id="6159c-134">若要找到要在地图中使用的空间数据，可以使用以下源：</span><span class="sxs-lookup"><span data-stu-id="6159c-134">To find spatial data to use in your map, you can use the following sources:</span></span>  
  
-   <span data-ttu-id="6159c-135">ESRI 形状文件，包括您可以在 Internet 上搜索的、向公众提供的形状文件。</span><span class="sxs-lookup"><span data-stu-id="6159c-135">ESRI Shapefiles, including publicly available Shapefiles that you can search for on the Internet.</span></span>  
  
-   <span data-ttu-id="6159c-136">来自 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 空间数据源的空间数据。</span><span class="sxs-lookup"><span data-stu-id="6159c-136">Spatial data from [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] spatial data sources.</span></span>  
  
-   <span data-ttu-id="6159c-137">地图库中报表内的地图。</span><span class="sxs-lookup"><span data-stu-id="6159c-137">Maps from reports in the Map Gallery.</span></span>  
  
-   <span data-ttu-id="6159c-138">提供空间数据作为 ESRI 形状文件或 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 空间数据的第三方站点。</span><span class="sxs-lookup"><span data-stu-id="6159c-138">Third-party sites that offer spatial data as ESRI Shapefiles or [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] spatial data.</span></span>  
  
-   <span data-ttu-id="6159c-139">Bing 地图图块，为地图视图提供背景。</span><span class="sxs-lookup"><span data-stu-id="6159c-139">Bing map tiles, which provide a background for the map view.</span></span> <span data-ttu-id="6159c-140">若要在地图中显示图块，必须将报表服务器配置为支持 Bing 地图 Web 服务。</span><span class="sxs-lookup"><span data-stu-id="6159c-140">To display tiles in a map, the report server must be configured to support Bing Maps Web Services.</span></span>  
  
 <span data-ttu-id="6159c-141">有关详细信息，请参阅</span><span class="sxs-lookup"><span data-stu-id="6159c-141">For more information, see "Where can I get ESRI shapefiles?"</span></span> <span data-ttu-id="6159c-142">[地图向导和地图层向导（报表生成器和 SSRS）](map-wizard-and-map-layer-wizard-report-builder-and-ssrs.md)中的“在何处可以获取 ESRI 形状文件？”。</span><span class="sxs-lookup"><span data-stu-id="6159c-142">in [Map Wizard and Map Layer Wizard &#40;Report Builder and SSRS&#41;](map-wizard-and-map-layer-wizard-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="6159c-143">空间数据可能具有政治敏感性，并且可能具有版权。</span><span class="sxs-lookup"><span data-stu-id="6159c-143">Spatial data can be politically sensitive and possibly copyrighted.</span></span> <span data-ttu-id="6159c-144">请检查空间数据源的使用条款和隐私声明，以了解如何在报表中使用空间数据。</span><span class="sxs-lookup"><span data-stu-id="6159c-144">Check the terms of use and privacy statements for spatial data sources to understand how you can use spatial data in your report.</span></span>  
  
 <span data-ttu-id="6159c-145">在找到所需的数据后，可以将数据嵌入到报表定义中，或者在处理报表时自动检索此数据。</span><span class="sxs-lookup"><span data-stu-id="6159c-145">After you find the data that you want, you can embed the data in the report definition or retrieve the data dynamically when the report is processed.</span></span> <span data-ttu-id="6159c-146">有关详细信息，请参阅本主题后面的 [在报表定义大小与报表处理时间之间达到平衡](#Embedding) 。</span><span class="sxs-lookup"><span data-stu-id="6159c-146">For more information, see [Balance Report Definition Size and Report Processing Time](#Embedding) later in this topic.</span></span>  
  
### <a name="determine-the-spatial-data-and-the-spatial-data-match-fields"></a><span data-ttu-id="6159c-147">确定空间数据和空间数据匹配字段</span><span class="sxs-lookup"><span data-stu-id="6159c-147">Determine the Spatial Data and the Spatial Data Match Fields</span></span>  
 <span data-ttu-id="6159c-148">若要在地图上显示分析数据并改变大小、颜色或标记类型，必须指定使空间数据与分析数据相关的字段。</span><span class="sxs-lookup"><span data-stu-id="6159c-148">To display analytical data on a map and to vary the size, color, or marker type, you must specify fields that relate the spatial data and analytical data.</span></span>  
  
 <span data-ttu-id="6159c-149">空间数据必须包含以下字段：</span><span class="sxs-lookup"><span data-stu-id="6159c-149">Spatial data must contain the following fields:</span></span>  
  
-   <span data-ttu-id="6159c-150">**Spatial data.**</span><span class="sxs-lookup"><span data-stu-id="6159c-150">**Spatial data.**</span></span> <span data-ttu-id="6159c-151">一个空间数据字段，它具有一系列坐标来定义每个点、线条或多边形。</span><span class="sxs-lookup"><span data-stu-id="6159c-151">A spatial data field that has the sets of coordinates that define each point, line, or polygon.</span></span>  
  
-   <span data-ttu-id="6159c-152">**匹配字段。**</span><span class="sxs-lookup"><span data-stu-id="6159c-152">**Match fields.**</span></span> <span data-ttu-id="6159c-153">一个或多个唯一标识每个空间数据字段的字段。</span><span class="sxs-lookup"><span data-stu-id="6159c-153">One or more fields that uniquely identify each spatial data field.</span></span> <span data-ttu-id="6159c-154">例如，对于表示商店位置的点，可以使用商店的名称。</span><span class="sxs-lookup"><span data-stu-id="6159c-154">For example, for a store location point, you might use the name of the store.</span></span> <span data-ttu-id="6159c-155">如果商店名称在空间数据中不唯一，则可以包含市县的名称以及商店名称。</span><span class="sxs-lookup"><span data-stu-id="6159c-155">If the store name is not unique in the spatial data, you might include the name of the city as well as the store.</span></span>  
  
 <span data-ttu-id="6159c-156">匹配字段用于使空间数据与分析数据相关。</span><span class="sxs-lookup"><span data-stu-id="6159c-156">The match fields are used to relate the spatial data with the analytical data.</span></span>  
  
### <a name="determine-the-analytical-data-and-the-analytical-data-match-fields"></a><span data-ttu-id="6159c-157">确定分析数据和分析数据匹配字段</span><span class="sxs-lookup"><span data-stu-id="6159c-157">Determine the Analytical Data and the Analytical Data Match Fields</span></span>  
 <span data-ttu-id="6159c-158">在确定空间数据之后，必须确定分析数据。</span><span class="sxs-lookup"><span data-stu-id="6159c-158">After you identify the spatial data, you must identify the analytical data.</span></span> <span data-ttu-id="6159c-159">分析数据可以来自以下源：</span><span class="sxs-lookup"><span data-stu-id="6159c-159">Analytical data can come from the following sources:</span></span>  
  
-   <span data-ttu-id="6159c-160">现有报表数据集。</span><span class="sxs-lookup"><span data-stu-id="6159c-160">An existing report dataset.</span></span> <span data-ttu-id="6159c-161">可以将字段指定为简单字段表达式，例如 [Sales] 或 =Fields!Sales.Value。</span><span class="sxs-lookup"><span data-stu-id="6159c-161">Fields are specified as simple field expressions, for example, [Sales] or =Fields!Sales.Value.</span></span>  
  
-   <span data-ttu-id="6159c-162">由空间数据源提供的数据字段。</span><span class="sxs-lookup"><span data-stu-id="6159c-162">Data fields provided by the spatial data source.</span></span> <span data-ttu-id="6159c-163">将字段指定为关键字，它们以 # 开头且后跟来自空间数据源的字段名称。</span><span class="sxs-lookup"><span data-stu-id="6159c-163">Fields are specified as keywords that begin with # followed the field name from the source of spatial data.</span></span>  
  
 <span data-ttu-id="6159c-164">然后，必须确定匹配字段的名称：</span><span class="sxs-lookup"><span data-stu-id="6159c-164">You must then determine the names of the match fields:</span></span>  
  
-   <span data-ttu-id="6159c-165">匹配字段。</span><span class="sxs-lookup"><span data-stu-id="6159c-165">Match fields.</span></span> <span data-ttu-id="6159c-166">与空间数据匹配字段指定相同信息的一个或多个字段，用于在空间数据与分析数据之间建立关系。</span><span class="sxs-lookup"><span data-stu-id="6159c-166">One or more fields that specify the same information as the spatial data match fields to build a relationship between the spatial data and the analytical data.</span></span> <span data-ttu-id="6159c-167">匹配字段应匹配数据类型以及格式。</span><span class="sxs-lookup"><span data-stu-id="6159c-167">Match fields should match data type as well as formatting.</span></span>  
  
 <span data-ttu-id="6159c-168">当您已确定空间数据源、空间数据、分析数据源、分析数据和匹配字段时，您就已准备就绪，可以确定要向报表添加哪种类型的地图。</span><span class="sxs-lookup"><span data-stu-id="6159c-168">When you have identified the spatial data source, the spatial data, the analytical data source, the analytical data, and the match fields, you are ready to decide which type of map to add to your report.</span></span>  
  

  
##  <a name="choose-a-map-type"></a><a name="MapType"></a> <span data-ttu-id="6159c-169">选择地图类型</span><span class="sxs-lookup"><span data-stu-id="6159c-169">Choose a Map Type</span></span>  
 <span data-ttu-id="6159c-170">当您运行“地图”向导时，可以向报表添加地图并添加第一个地图层。</span><span class="sxs-lookup"><span data-stu-id="6159c-170">When you run the Map wizard, you add a map and the first map layer to your report.</span></span> <span data-ttu-id="6159c-171">通过向导，可以向报表添加以下地图类型之一：</span><span class="sxs-lookup"><span data-stu-id="6159c-171">The wizard enables you to add one of the following types of maps to your report:</span></span>  
  
-   <span data-ttu-id="6159c-172">基本图，显示位置而没有关联的分析数据。</span><span class="sxs-lookup"><span data-stu-id="6159c-172">A basic map that displays locations without associated analytical data.</span></span>  
  
-   <span data-ttu-id="6159c-173">对于每个地图元素具有一个关联的分析值的地图，例如，每个商店位置的总销售额。</span><span class="sxs-lookup"><span data-stu-id="6159c-173">A map that has one analytical value associated with each map element, for example, sales total for each store location.</span></span>  
  
-   <span data-ttu-id="6159c-174">对于一个地图元素具有多个关联的分析值的地图，例如，每个商店位置的客户数和总销售额。</span><span class="sxs-lookup"><span data-stu-id="6159c-174">A map that has more than one analytical value associated with a map element, for example, number of customers and sales total for each store location.</span></span>  
  
 <span data-ttu-id="6159c-175">下表对各地图类型进行了说明。</span><span class="sxs-lookup"><span data-stu-id="6159c-175">The following table describes each map type.</span></span> <span data-ttu-id="6159c-176">所有地图类型都允许您选择一个控制调色板、边框样式和字体的主题以及显示标签。</span><span class="sxs-lookup"><span data-stu-id="6159c-176">All map types allow you to select a theme that controls palette, border style, and font, and to display labels.</span></span>  
  
|<span data-ttu-id="6159c-177">向导图标</span><span class="sxs-lookup"><span data-stu-id="6159c-177">Wizard Icon</span></span>|<span data-ttu-id="6159c-178">层样式</span><span class="sxs-lookup"><span data-stu-id="6159c-178">Layer style</span></span>|<span data-ttu-id="6159c-179">层类型</span><span class="sxs-lookup"><span data-stu-id="6159c-179">Layer Type</span></span>|<span data-ttu-id="6159c-180">说明和选项</span><span class="sxs-lookup"><span data-stu-id="6159c-180">Description and options</span></span>|  
|-----------------|-----------------|----------------|-----------------------------|  
|<span data-ttu-id="6159c-181">![rs_MapType_Polygon_Basic](../media/rs-maptype-polygon-basic.gif "rs_MapType_Polygon_Basic")</span><span class="sxs-lookup"><span data-stu-id="6159c-181">![rs_MapType_Polygon_Basic](../media/rs-maptype-polygon-basic.gif "rs_MapType_Polygon_Basic")</span></span>|<span data-ttu-id="6159c-182">基本图</span><span class="sxs-lookup"><span data-stu-id="6159c-182">Basic Map</span></span>|<span data-ttu-id="6159c-183">Polygon</span><span class="sxs-lookup"><span data-stu-id="6159c-183">Polygon</span></span>|<span data-ttu-id="6159c-184">只显示区域的地图，例如，销售区域。</span><span class="sxs-lookup"><span data-stu-id="6159c-184">A map that displays areas only, for example, sales territories.</span></span><br /><br /> <span data-ttu-id="6159c-185">选项：通过调色板改变颜色或使用一种颜色。</span><span class="sxs-lookup"><span data-stu-id="6159c-185">Options: Vary color by palette or use a single color.</span></span> <span data-ttu-id="6159c-186">调色板是一组预定义的颜色。</span><span class="sxs-lookup"><span data-stu-id="6159c-186">A palette is a predefined set of colors.</span></span> <span data-ttu-id="6159c-187">当分配完调色板中的所有颜色后，将分配颜色的阴影。</span><span class="sxs-lookup"><span data-stu-id="6159c-187">When all colors in a palette have been assigned, shades of colors are assigned.</span></span>|  
|<span data-ttu-id="6159c-188">![rs_MapType_Polygon_ColorAnalytical](../media/rs-maptype-polygon-coloranalytical.gif "rs_MapType_Polygon_ColorAnalytical")</span><span class="sxs-lookup"><span data-stu-id="6159c-188">![rs_MapType_Polygon_ColorAnalytical](../media/rs-maptype-polygon-coloranalytical.gif "rs_MapType_Polygon_ColorAnalytical")</span></span>|<span data-ttu-id="6159c-189">颜色分析图</span><span class="sxs-lookup"><span data-stu-id="6159c-189">Color Analytical Map</span></span>|<span data-ttu-id="6159c-190">Polygon</span><span class="sxs-lookup"><span data-stu-id="6159c-190">Polygon</span></span>|<span data-ttu-id="6159c-191">一个按变化的颜色显示分析数据的地图，例如，按区域列出的销售数据。</span><span class="sxs-lookup"><span data-stu-id="6159c-191">A map that displays analytical data by varying color, for example, sales data by area.</span></span>|  
|<span data-ttu-id="6159c-192">![rs_MapType_Polygon_Bubble](../media/rs-maptype-polygon-bubble.gif "rs_MapType_Polygon_Bubble")</span><span class="sxs-lookup"><span data-stu-id="6159c-192">![rs_MapType_Polygon_Bubble](../media/rs-maptype-polygon-bubble.gif "rs_MapType_Polygon_Bubble")</span></span>|<span data-ttu-id="6159c-193">气泡图</span><span class="sxs-lookup"><span data-stu-id="6159c-193">Bubble Map</span></span>|<span data-ttu-id="6159c-194">Polygon</span><span class="sxs-lookup"><span data-stu-id="6159c-194">Polygon</span></span>|<span data-ttu-id="6159c-195">一个在各区域中心以不同气泡大小显示分析数据的地图，例如，按区域列出的销售数据。</span><span class="sxs-lookup"><span data-stu-id="6159c-195">A map that displays analytical data by varying bubble size centered on areas, for example, sales data by area.</span></span><br /><br /> <span data-ttu-id="6159c-196">选项：根据第二个分析字段改变区域颜色以及指定颜色规则。</span><span class="sxs-lookup"><span data-stu-id="6159c-196">Options: Vary area colors based on a second analytical field and specify color rules.</span></span>|  
|<span data-ttu-id="6159c-197">![rs_MapType_Line_Basic](../media/rs-maptype-line-basic.gif "rs_MapType_Line_Basic")</span><span class="sxs-lookup"><span data-stu-id="6159c-197">![rs_MapType_Line_Basic](../media/rs-maptype-line-basic.gif "rs_MapType_Line_Basic")</span></span>|<span data-ttu-id="6159c-198">基本线条图</span><span class="sxs-lookup"><span data-stu-id="6159c-198">Basic Line Map</span></span>|<span data-ttu-id="6159c-199">行</span><span class="sxs-lookup"><span data-stu-id="6159c-199">Line</span></span>|<span data-ttu-id="6159c-200">只显示线条的地图，例如，交货路线。</span><span class="sxs-lookup"><span data-stu-id="6159c-200">A map that displays lines only, for example, delivery routes.</span></span><br /><br /> <span data-ttu-id="6159c-201">选项：通过调色板改变颜色或使用一种颜色。</span><span class="sxs-lookup"><span data-stu-id="6159c-201">Options: Vary color by palette or use a single color.</span></span>|  
|<span data-ttu-id="6159c-202">![rs_MapType_Line_Analytical](../media/rs-maptype-line-analytical.gif "rs_MapType_Line_Analytical")</span><span class="sxs-lookup"><span data-stu-id="6159c-202">![rs_MapType_Line_Analytical](../media/rs-maptype-line-analytical.gif "rs_MapType_Line_Analytical")</span></span>|<span data-ttu-id="6159c-203">分析线条图</span><span class="sxs-lookup"><span data-stu-id="6159c-203">Analytical Line Map</span></span>|<span data-ttu-id="6159c-204">行</span><span class="sxs-lookup"><span data-stu-id="6159c-204">Line</span></span>|<span data-ttu-id="6159c-205">线条颜色和宽度发生变化的地图，例如，交货的包装数和按路线的实时度量。</span><span class="sxs-lookup"><span data-stu-id="6159c-205">A map that varies line color and width, for example, number of packages delivered and on-time metrics by route.</span></span><br /><br /> <span data-ttu-id="6159c-206">选项：通过一个分析字段改变线条宽度，通过第二个分析字段改变线条颜色，以及指定颜色规则。</span><span class="sxs-lookup"><span data-stu-id="6159c-206">Options: Vary line width by one analytical field, vary line color by a second analytical field, and specify color rules.</span></span>|  
|<span data-ttu-id="6159c-207">![rs_MapType_Marker_Basic](../media/rs-maptype-marker-basic.gif "rs_MapType_Marker_Basic")</span><span class="sxs-lookup"><span data-stu-id="6159c-207">![rs_MapType_Marker_Basic](../media/rs-maptype-marker-basic.gif "rs_MapType_Marker_Basic")</span></span>|<span data-ttu-id="6159c-208">基本标记地图</span><span class="sxs-lookup"><span data-stu-id="6159c-208">Basic Marker Map</span></span>|<span data-ttu-id="6159c-209">Point</span><span class="sxs-lookup"><span data-stu-id="6159c-209">Point</span></span>|<span data-ttu-id="6159c-210">在每个位置显示一个标记的地图，例如，市县。</span><span class="sxs-lookup"><span data-stu-id="6159c-210">A map that displays a marker at each location, for example, cities.</span></span><br /><br /> <span data-ttu-id="6159c-211">选项：通过调色板改变颜色或使用一种颜色，以及更改标记样式。</span><span class="sxs-lookup"><span data-stu-id="6159c-211">Options: Vary color by palette or use a single color, and change marker style.</span></span>|  
|<span data-ttu-id="6159c-212">![rs_MapType_Marker_Bubble](../media/rs-maptype-marker-bubble.gif "rs_MapType_Marker_Bubble")</span><span class="sxs-lookup"><span data-stu-id="6159c-212">![rs_MapType_Marker_Bubble](../media/rs-maptype-marker-bubble.gif "rs_MapType_Marker_Bubble")</span></span>|<span data-ttu-id="6159c-213">气泡标记地图</span><span class="sxs-lookup"><span data-stu-id="6159c-213">Bubble Marker Map</span></span>|<span data-ttu-id="6159c-214">Point</span><span class="sxs-lookup"><span data-stu-id="6159c-214">Point</span></span>|<span data-ttu-id="6159c-215">对每个位置显示一个气泡且气泡大小按一个分析数据字段变化的地图，例如，按市县列出的销售数据。</span><span class="sxs-lookup"><span data-stu-id="6159c-215">A map that displays a bubble for each location and varies bubble size by one analytical data field, for example, sales data by city.</span></span><br /><br /> <span data-ttu-id="6159c-216">选项：根据第二个分析字段改变气泡颜色以及指定颜色规则。</span><span class="sxs-lookup"><span data-stu-id="6159c-216">Options: Vary bubble color by a second analytical field, and specify color rules.</span></span>|  
|<span data-ttu-id="6159c-217">![rs_MapType_Marker_Analytical](../media/rs-maptype-marker-analytical.gif "rs_MapType_Marker_Analytical")</span><span class="sxs-lookup"><span data-stu-id="6159c-217">![rs_MapType_Marker_Analytical](../media/rs-maptype-marker-analytical.gif "rs_MapType_Marker_Analytical")</span></span>|<span data-ttu-id="6159c-218">分析标记地图</span><span class="sxs-lookup"><span data-stu-id="6159c-218">Analytical Marker Map</span></span>|<span data-ttu-id="6159c-219">Point</span><span class="sxs-lookup"><span data-stu-id="6159c-219">Point</span></span>|<span data-ttu-id="6159c-220">在每个位置显示一个标记且标记颜色、大小和类型随分析数据发生变化的地图，例如，最畅销的产品、利润范围和折扣策略。</span><span class="sxs-lookup"><span data-stu-id="6159c-220">A map that displays a marker at each location and varies marker color, size, and type based on analytical data, for example, top selling products, profit range, and discount strategy.</span></span><br /><br /> <span data-ttu-id="6159c-221">选项：通过一个分析字段改变标记类型，通过第二个分析字段改变标记大小，通过第三个分析字段改变标记颜色，以及指定颜色规则。</span><span class="sxs-lookup"><span data-stu-id="6159c-221">Options: Vary marker type by one analytical field, vary marker size by a second analytical field, vary marker color by a third analytical field, and specify color rules.</span></span>|  
  
 <span data-ttu-id="6159c-222">在使用“地图”向导添加地图之后，您可以使用“层”向导创建其他层或更改用于层的选项。</span><span class="sxs-lookup"><span data-stu-id="6159c-222">After you add a map with the Map wizard, you can create additional layers or change options for a layer by using the Layer wizard.</span></span> <span data-ttu-id="6159c-223">有关向导的详细信息，请参阅[地图向导和地图层向导（报表生成器和 SSRS）](map-wizard-and-map-layer-wizard-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="6159c-223">For more information about the wizards, see [Map Wizard and Map Layer Wizard &#40;Report Builder and SSRS&#41;](map-wizard-and-map-layer-wizard-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="6159c-224">可以单独为每个层自定义显示或数据选项。</span><span class="sxs-lookup"><span data-stu-id="6159c-224">You can customize the display or data options for each layer independently.</span></span> <span data-ttu-id="6159c-225">有关运行向导后自定义地图的详细信息，请参阅 [自定义地图或地图层的数据和显示（报表生成器和 SSRS）](customize-the-data-and-display-of-a-map-or-map-layer-report-builder-and-ssrs.md)中的“在何处可以获取 ESRI 形状文件？”。</span><span class="sxs-lookup"><span data-stu-id="6159c-225">For more information about customizing a map after you run a wizard, see [Customize the Data and Display of a Map or Map Layer &#40;Report Builder and SSRS&#41;](customize-the-data-and-display-of-a-map-or-map-layer-report-builder-and-ssrs.md).</span></span>  
  
 
  
##  <a name="plan-for-legends"></a><a name="Legend"></a> <span data-ttu-id="6159c-226">规划图例</span><span class="sxs-lookup"><span data-stu-id="6159c-226">Plan for Legends</span></span>  
 <span data-ttu-id="6159c-227">为了帮助用户解释地图，可以添加多个地图图例、一个色阶和一个距离刻度。</span><span class="sxs-lookup"><span data-stu-id="6159c-227">To help your users interpret a map, you can add multiple map legends, a color scale, and a distance scale.</span></span> <span data-ttu-id="6159c-228">当您设计地图时，请规划要在何处显示图例。</span><span class="sxs-lookup"><span data-stu-id="6159c-228">When you design a map, plan where you want the legends to display.</span></span> <span data-ttu-id="6159c-229">可以指定有关每个图例的以下信息：</span><span class="sxs-lookup"><span data-stu-id="6159c-229">You can specify the following information about each legend:</span></span>  
  
-   <span data-ttu-id="6159c-230">**图例位置。**</span><span class="sxs-lookup"><span data-stu-id="6159c-230">**Legend location.**</span></span> <span data-ttu-id="6159c-231">例如，图例可以显示在视区内部或外部，并相对于视区显示在 12 个分离的位置。</span><span class="sxs-lookup"><span data-stu-id="6159c-231">For example, legends can display inside or outside the viewport, and in 12 discrete locations relative to the viewport.</span></span>  
  
-   <span data-ttu-id="6159c-232">**图例样式**。</span><span class="sxs-lookup"><span data-stu-id="6159c-232">**Legend styles**.</span></span> <span data-ttu-id="6159c-233">例如，可以指定字形、边框样式、分隔线和填充属性。</span><span class="sxs-lookup"><span data-stu-id="6159c-233">For example, you can specify the font style, border style, separator line, and fill properties.</span></span>  
  
-   <span data-ttu-id="6159c-234">**图例标题。**</span><span class="sxs-lookup"><span data-stu-id="6159c-234">**Legend title.**</span></span> <span data-ttu-id="6159c-235">例如，您可以指定标题文本，并独立控制是否为图例显示标题以及是否显示色阶。</span><span class="sxs-lookup"><span data-stu-id="6159c-235">For example, you can specify title text, and independently control whether to display the title for a map legend or the color scale.</span></span>  
  
-   <span data-ttu-id="6159c-236">**地图图例布局。**</span><span class="sxs-lookup"><span data-stu-id="6159c-236">**Map legend layout.**</span></span> <span data-ttu-id="6159c-237">例如，地图图例可以显示为高表或宽表。</span><span class="sxs-lookup"><span data-stu-id="6159c-237">For example, map legends can display as tall tables or wide tables.</span></span>  
  
 <span data-ttu-id="6159c-238">在报表处理过程中，将根据您为每个层设置的规则选项，自动创建图例的内容。</span><span class="sxs-lookup"><span data-stu-id="6159c-238">The contents of the legend are created automatically during report processing based on rule options that you set for each layer.</span></span>  
  
 <span data-ttu-id="6159c-239">默认情况下，所有层都在第一个地图图例中显示规则的结果。</span><span class="sxs-lookup"><span data-stu-id="6159c-239">By default, all layers display the results of rules in the first map legend.</span></span> <span data-ttu-id="6159c-240">您可以创建多个图例，然后对于每个规则，指定使用哪个图例来显示结果。</span><span class="sxs-lookup"><span data-stu-id="6159c-240">You can create multiple legends and then, for each rule, assign which legend to use to display the results.</span></span>  
  
 <span data-ttu-id="6159c-241">有关详细信息，请参阅[按规则和分析数据更改多边形、线条和点的显示方式（报表生成器和 SSRS）](vary-polygon-line-and-point-display-by-rules-and-analytical-data.md)和[更改地图图例、色阶和关联的规则（报表生成器和 SSRS）](change-map-legends-color-scale-and-associated-rules-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="6159c-241">For more information, see [Vary Polygon, Line, and Point Display by Rules and Analytical Data &#40;Report Builder and SSRS&#41;](vary-polygon-line-and-point-display-by-rules-and-analytical-data.md) and [Change Map Legends, Color Scale, and Associated Rules &#40;Report Builder and SSRS&#41;](change-map-legends-color-scale-and-associated-rules-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="balance-report-definition-size-and-report-processing-time"></a><a name="Embedding"></a> <span data-ttu-id="6159c-242">在报表定义大小与报表处理时间之间达到平衡</span><span class="sxs-lookup"><span data-stu-id="6159c-242">Balance Report Definition Size and Report Processing Time</span></span>  
 <span data-ttu-id="6159c-243">针对地图的良好报表设计要求您在控制报表性能和报表定义大小的选项之间达到平衡。</span><span class="sxs-lookup"><span data-stu-id="6159c-243">Good report design for maps require that you balance the options that control report performance and report definition size.</span></span> <span data-ttu-id="6159c-244">基于空间数据或 Bing 地图图块的地图元素可以是静态的且可嵌入到报表定义中；它们也可以是动态的，而在每次处理报表时创建。</span><span class="sxs-lookup"><span data-stu-id="6159c-244">Map elements that are based on spatial data, or Bing map tiles, can be static and embedded in the report definition or dynamic and created every time the report is processed.</span></span> <span data-ttu-id="6159c-245">必须在静态或动态地图数据之间进行折衷，并找出适合您所在环境的平衡点。</span><span class="sxs-lookup"><span data-stu-id="6159c-245">You must assess the trade-offs for static or dynamic map data and find the balance that works for your circumstances.</span></span> <span data-ttu-id="6159c-246">在制定这一决策时，请考虑以下信息：</span><span class="sxs-lookup"><span data-stu-id="6159c-246">Consider the following information to make this decision:</span></span>  
  
-   <span data-ttu-id="6159c-247">嵌入的地图元素可能显著增加报表定义的大小，但会减少在报表中查看地图所需的时间。</span><span class="sxs-lookup"><span data-stu-id="6159c-247">Embedded map elements can significantly increase the size of the report definition, but reduce the time that is required to view the map in the report.</span></span> <span data-ttu-id="6159c-248">报表服务器可能具有大小限制，您需要注意这一点。</span><span class="sxs-lookup"><span data-stu-id="6159c-248">Your report server might have size limits that you need to work with.</span></span>  
  
-   <span data-ttu-id="6159c-249">报表定义为可以处理的空间数据点数指定限制；同时指定一个单独的值，该值指定可以在报表定义中包含的地图元素的数量。</span><span class="sxs-lookup"><span data-stu-id="6159c-249">The report definition specifies limits to the number of spatial data points that can be processed and a separate value that specifies the number of map elements that can be included in the report definition.</span></span>  
  
-   <span data-ttu-id="6159c-250">动态地图元素减少报表定义大小，但会增加处理和呈现地图所需的时间。</span><span class="sxs-lookup"><span data-stu-id="6159c-250">Dynamic map elements reduce the report definition size but increase the time that is required to process and render the map.</span></span>  
  
-   <span data-ttu-id="6159c-251">如果空间数据源位于您的计算机上，则地图元素始终嵌入到报表定义中。</span><span class="sxs-lookup"><span data-stu-id="6159c-251">When the source of spatial data is located on the your computer, map elements are always embedded in the report definition.</span></span> <span data-ttu-id="6159c-252">这包括来自已在本地安装的地图库或 ESRI 形状文件的空间数据。</span><span class="sxs-lookup"><span data-stu-id="6159c-252">This includes spatial data from the Map Gallery or ESRI Shapefiles that have been installed locally.</span></span>  
  
 <span data-ttu-id="6159c-253">若要使用动态空间数据，空间数据源必须位于报表服务器上。</span><span class="sxs-lookup"><span data-stu-id="6159c-253">To use dynamic spatial data, the spatial data source must be on the report server.</span></span> <span data-ttu-id="6159c-254">当在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中设计报表时，可以将空间数据源添加到项目，并将其以及报表定义一起发布到报表服务器。</span><span class="sxs-lookup"><span data-stu-id="6159c-254">When reports are designed in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], spatial data sources can be added to a project and published to the report server together with the report definition.</span></span> <span data-ttu-id="6159c-255">如果您使用报表生成器来设计报表，必须首先将空间数据上载到报表服务器，然后在向导或层属性中，为该地图层指定此空间数据源。</span><span class="sxs-lookup"><span data-stu-id="6159c-255">If you are using Report Builder to design reports, you must upload the spatial data to the report server first, and then, in the wizard or in the layer properties, specify that source of spatial data for the map layer.</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="6159c-256">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6159c-256">See Also</span></span>  
 <span data-ttu-id="6159c-257">[自定义地图或地图层的数据和显示（报表生成器和 SSRS）](customize-the-data-and-display-of-a-map-or-map-layer-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6159c-257">[Customize the Data and Display of a Map or Map Layer &#40;Report Builder and SSRS&#41;](customize-the-data-and-display-of-a-map-or-map-layer-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="6159c-258">[教程：地图报表（报表生成器）](../tutorial-map-report-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="6159c-258">[Tutorial: Map Report &#40;Report Builder&#41;](../tutorial-map-report-report-builder.md) </span></span>  
 <span data-ttu-id="6159c-259">[地图（报表生成器和 SSRS）](maps-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6159c-259">[Maps &#40;Report Builder and SSRS&#41;](maps-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="6159c-260">报表故障排除：地图报表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="6159c-260">Troubleshoot Reports: Map Reports &#40;Report Builder and SSRS&#41;</span></span>](troubleshoot-reports-map-reports-report-builder-and-ssrs.md)  
  
  