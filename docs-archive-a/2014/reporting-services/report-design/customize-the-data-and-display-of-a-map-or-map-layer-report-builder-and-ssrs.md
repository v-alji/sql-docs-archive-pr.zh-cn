---
title: 自定义的数据和显示的地图或地图层 （报表生成器和 SSRS） |Microsoft 文档
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10521"
- sql12.rtp.rptdesigner.shared.shadowdv.f1
- "10515"
- "10512"
- "10520"
- "10523"
- sql12.rtp.rptdesigner.mapgroupproperties.variables.f1
- sql12.rtp.rptdesigner.mapgroupproperties.filter.f1
- sql12.rtp.rptdesigner.shared.number.f1
- sql12.rtp.rptdesigner.shared.font.f1
- sql12.rtp.rptdesigner.mapgroupproperties.general.f1
- "10507"
ms.assetid: fdd9b994-d138-4990-a291-279b0249eb72
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 05987cea7ebde9d3587ade3f567eeb8ccef5e8fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691630"
---
# <a name="customize-the-data-and-display-of-a-map-or-map-layer-report-builder-and-ssrs"></a><span data-ttu-id="c4981-102">自定义地图或地图层的数据和显示（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="c4981-102">Customize the Data and Display of a Map or Map Layer (Report Builder and SSRS)</span></span>
  <span data-ttu-id="c4981-103">在使用向导向报表中添加地图或地图层之后，您可能希望更改地图在报表中的显示方式。</span><span class="sxs-lookup"><span data-stu-id="c4981-103">After you add a map or map layer to a report by using a wizard, you might want to change the way the map looks in the report.</span></span> <span data-ttu-id="c4981-104">可以考虑以下构思来进行改进：</span><span class="sxs-lookup"><span data-stu-id="c4981-104">You can make improvements by considering the following ideas:</span></span>  
  
-   <span data-ttu-id="c4981-105">为了帮助用户了解如何解释地图上的数据显示，可以添加图例和色阶以及添加标签和工具提示。</span><span class="sxs-lookup"><span data-stu-id="c4981-105">To help your users understand how to interpret the data display on a map, you can add legends and a color scale, and add labels and tooltips.</span></span>  
  
-   <span data-ttu-id="c4981-106">若要使地图变得更易读，请更改中心和缩放级别、添加距离刻度以及显示背景网格。</span><span class="sxs-lookup"><span data-stu-id="c4981-106">To make the map easier to read, change the center and zoom level, add a distance scale, and display a background grid.</span></span>  
  
-   <span data-ttu-id="c4981-107">为了在运行报表时帮助控制地图的绘制时间，可以调整分辨率以简化地图元素。</span><span class="sxs-lookup"><span data-stu-id="c4981-107">To help control map drawing time when you run the report, you can adjust the resolution to simplify the map elements.</span></span>  
  
-   <span data-ttu-id="c4981-108">可以在报表定义中嵌入地图元素，然后更改各元素的显示方式。</span><span class="sxs-lookup"><span data-stu-id="c4981-108">You can embed map elements in the report definition, and then change how individual elements appear.</span></span> <span data-ttu-id="c4981-109">例如，可以使用图钉显示主办公地点，而使用圆圈来显示其他办公地点。</span><span class="sxs-lookup"><span data-stu-id="c4981-109">For example, you can display the primary office location with a pushpin and other office locations with circles.</span></span>  
  
-   <span data-ttu-id="c4981-110">您可以通过指定自己的数据组表达式，添加自定义区域。</span><span class="sxs-lookup"><span data-stu-id="c4981-110">You can add customized regions by specifying your own data group expressions.</span></span>  
  
-   <span data-ttu-id="c4981-111">可以在您在具有嵌入点的地图层上指定的某个点处添加自定义位置。</span><span class="sxs-lookup"><span data-stu-id="c4981-111">You can add a custom location at a  point that you specify on a map layer that has embedded points.</span></span> <span data-ttu-id="c4981-112">对于自定义点，可以独立于点层上的其他点为其设置值和显示属性。</span><span class="sxs-lookup"><span data-stu-id="c4981-112">You can set the value and display properties for custom points independently from other points on a point layer.</span></span>  
  
-   <span data-ttu-id="c4981-113">若要提供更多详细信息，可以添加指向每层上各地图元素的链接，用户单击此类链接即可打开相关的报表。</span><span class="sxs-lookup"><span data-stu-id="c4981-113">To provide more detail, you can add links to map elements on each layer that a user can click to open related reports.</span></span>  
  
 <span data-ttu-id="c4981-114">有关改进报表的更多想法，请参阅[规划报表（报表生成器）](planning-a-report-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="c4981-114">For more ideas about improving a report, see [Planning a Report &#40;Report Builder&#41;](planning-a-report-report-builder.md).</span></span>  
  
 <span data-ttu-id="c4981-115">显示选项会影响您查看报表时地图或地图部分显示的方式。</span><span class="sxs-lookup"><span data-stu-id="c4981-115">Display options affect the way a map or the parts of a map appear when you view the report.</span></span> <span data-ttu-id="c4981-116">某些选项控制地图的外观，例如，边框和字体或地图上表示的区域。</span><span class="sxs-lookup"><span data-stu-id="c4981-116">Some options control the appearance of the map, such as the borders and fonts or the area represented on the map.</span></span> <span data-ttu-id="c4981-117">其他选项可控制每一层的内容，例如气泡大小、标记类型、标签或工具提示。</span><span class="sxs-lookup"><span data-stu-id="c4981-117">Other options control the content of each layer, such as bubble sizes, marker types, labels, or tooltips.</span></span>  
  
 <span data-ttu-id="c4981-118">地图报表项包括以下部分：地图本身、地图视区、一组标题、一组图例（图例、色阶和距离刻度）、一组层以及每一层上的一组地图元素（多边形、线条或点）。</span><span class="sxs-lookup"><span data-stu-id="c4981-118">A map report item includes the following parts: the map itself, a map viewport, a set of titles, a set of legends (legend, color scale, and distance scale), a set of layers, a set of map elements on each layer (polygons or lines or points).</span></span> <span data-ttu-id="c4981-119">使用以下各部分中的信息可以了解哪一属性对话框控制地图的各不同部分的显示选项。</span><span class="sxs-lookup"><span data-stu-id="c4981-119">Use the information in the following sections to understand which property dialog box controls the display options for different parts of a map.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="change-options-for-the-map"></a><a name="Map"></a> <span data-ttu-id="c4981-120">更改地图的选项</span><span class="sxs-lookup"><span data-stu-id="c4981-120">Change Options for the Map</span></span>  
 <span data-ttu-id="c4981-121">在地图报表项上，可以控制以下内容：</span><span class="sxs-lookup"><span data-stu-id="c4981-121">On a map report item, you can control the following:</span></span>  
  
-   <span data-ttu-id="c4981-122">添加多个标题。</span><span class="sxs-lookup"><span data-stu-id="c4981-122">Add multiple titles.</span></span>  
  
-   <span data-ttu-id="c4981-123">添加多个图例。</span><span class="sxs-lookup"><span data-stu-id="c4981-123">Add multiple legends.</span></span> <span data-ttu-id="c4981-124">若要更改图例的内容，您需要创建其他图例，然后更改规则以指定要在哪个图例中输入由每个规则创建的图例项。</span><span class="sxs-lookup"><span data-stu-id="c4981-124">To change the contents of a legend, you need to create additional legends and then change the rules to specify in which legend to enter the legend items created by each rule.</span></span>  
  
-   <span data-ttu-id="c4981-125">添加更多层。</span><span class="sxs-lookup"><span data-stu-id="c4981-125">Add more layers.</span></span>  
  
-   <span data-ttu-id="c4981-126">显示或隐藏距离刻度或色阶。</span><span class="sxs-lookup"><span data-stu-id="c4981-126">Hide or show the distance scale or color scale.</span></span>  
  
-   <span data-ttu-id="c4981-127">通过指定阴影，提供具有深度的错觉。</span><span class="sxs-lookup"><span data-stu-id="c4981-127">Provide the illusion of depth by specifying a shadow.</span></span>  
  
 <span data-ttu-id="c4981-128">若要更改这些选项，请右键单击“地图”，然后更改选项。 </span><span class="sxs-lookup"><span data-stu-id="c4981-128">To change these options, right-click the map, click **Map**, and change the options.</span></span>  
  
 
  
##  <a name="change-options-for-the-viewport"></a><a name="Viewport"></a> <span data-ttu-id="c4981-129">更改视区的选项</span><span class="sxs-lookup"><span data-stu-id="c4981-129">Change Options for the Viewport</span></span>  
 <span data-ttu-id="c4981-130">使用视区选项可以更改报表中显示的地图的视图。</span><span class="sxs-lookup"><span data-stu-id="c4981-130">Use the viewport options to change the view of the map that appears in your report.</span></span>  
  
 <span data-ttu-id="c4981-131">空间数据源提供的区域可能大于报表中您需要显示的区域。</span><span class="sxs-lookup"><span data-stu-id="c4981-131">The source of spatial data might provide more area than you need to display in the report.</span></span> <span data-ttu-id="c4981-132">可以使用视区来设置中心、缩放级别以及裁剪地图的区域。</span><span class="sxs-lookup"><span data-stu-id="c4981-132">You can use the viewport to set the center, the zoom level, and to crop the area for the map.</span></span>  
  
 <span data-ttu-id="c4981-133">可以为视区设置以下选项：</span><span class="sxs-lookup"><span data-stu-id="c4981-133">The following options can be set for the viewport:</span></span>  
  
-   <span data-ttu-id="c4981-134">选择坐标系，并对于地理坐标系选择投影。</span><span class="sxs-lookup"><span data-stu-id="c4981-134">Choose the coordinate system and, for a geographic coordinate system, choose the projection.</span></span>  
  
-   <span data-ttu-id="c4981-135">选择地图的中心。</span><span class="sxs-lookup"><span data-stu-id="c4981-135">Choose the center for the map.</span></span>  
  
-   <span data-ttu-id="c4981-136">裁剪地图的视图。</span><span class="sxs-lookup"><span data-stu-id="c4981-136">Crop the view for the map.</span></span>  
  
-   <span data-ttu-id="c4981-137">设置缩放级别。</span><span class="sxs-lookup"><span data-stu-id="c4981-137">Set the zoom level.</span></span>  
  
-   <span data-ttu-id="c4981-138">分辨率和简化。</span><span class="sxs-lookup"><span data-stu-id="c4981-138">Resolution and simplification.</span></span> <span data-ttu-id="c4981-139">对于线条和多边形，在绘制时间与轮廓详细程度之间选择平衡。</span><span class="sxs-lookup"><span data-stu-id="c4981-139">Choose a balance between drawing time and detailed outlines for lines and polygons.</span></span>  
  
 <span data-ttu-id="c4981-140">若要更改这些选项，请右键单击地图视区，然后使用[地图视区属性”对话框 -&gt;“常规”](../map-viewport-properties-dialog-box-general.md)页和相关页。</span><span class="sxs-lookup"><span data-stu-id="c4981-140">To change these options, right-click the map viewport, use the [Map Viewport Properties Dialog Box, General](../map-viewport-properties-dialog-box-general.md) page and related pages.</span></span>  
  

  
##  <a name="change-options-for-the-legends"></a><a name="Legends"></a> <span data-ttu-id="c4981-141">更改图例的选项</span><span class="sxs-lookup"><span data-stu-id="c4981-141">Change Options for the Legends</span></span>  
 <span data-ttu-id="c4981-142">图例可帮助用户解释地图上的数据。</span><span class="sxs-lookup"><span data-stu-id="c4981-142">Legends help users interpret the data on a map.</span></span>  
  
 <span data-ttu-id="c4981-143">默认情况下，您为层指定的所有规则会向第一个图例添加项。</span><span class="sxs-lookup"><span data-stu-id="c4981-143">By default, all rules that you specify for a layer add items to the first legend.</span></span> <span data-ttu-id="c4981-144">此外，所有颜色规则都在色阶中显示值。</span><span class="sxs-lookup"><span data-stu-id="c4981-144">In addition, all color rules display values in the color scale.</span></span>  
  
-   <span data-ttu-id="c4981-145">若要更改图例外观的显示选项（包括它相对于视区的位置），请对图例本身设置选项。</span><span class="sxs-lookup"><span data-stu-id="c4981-145">To change the display options for the appearance of the legend, including its position relative to the viewport, set options on the legend itself.</span></span>  
  
-   <span data-ttu-id="c4981-146">若要更改图例的内容或内容格式，请对层更改对应规则的图例选项。</span><span class="sxs-lookup"><span data-stu-id="c4981-146">To change the contents or the format of contents for a legend, change the legend options for the corresponding rules for a layer.</span></span>  
  
 <span data-ttu-id="c4981-147">有关详细信息，请参阅 [更改地图图例、色阶和关联的规则（报表生成器和 SSRS）](change-map-legends-color-scale-and-associated-rules-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="c4981-147">For more information, see [Change Map Legends, Color Scale, and Associated Rules &#40;Report Builder and SSRS&#41;](change-map-legends-color-scale-and-associated-rules-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="change-options-for-the-layer"></a><a name="Layer"></a> <span data-ttu-id="c4981-148">更改层的选项</span><span class="sxs-lookup"><span data-stu-id="c4981-148">Change Options for the Layer</span></span>  
 <span data-ttu-id="c4981-149">若要显示地图的层，请单击地图以选择对应的层。</span><span class="sxs-lookup"><span data-stu-id="c4981-149">To display the layers for a map, click the map to select it.</span></span> <span data-ttu-id="c4981-150">“地图”窗格将出现。</span><span class="sxs-lookup"><span data-stu-id="c4981-150">The Map pane appears.</span></span> <span data-ttu-id="c4981-151">若要更改层的选项，请右键单击该层并使用快捷方式菜单。</span><span class="sxs-lookup"><span data-stu-id="c4981-151">To change options for a layer, right-click the layer and use the shortcut menu.</span></span>  
  
 <span data-ttu-id="c4981-152">层可以为三种类型之一，具体取决于由空间数据源返回的空间数据：多边形层、线条层或点层。</span><span class="sxs-lookup"><span data-stu-id="c4981-152">A layer can be one of three types based on the spatial data that is returned by the spatial data source: a polygon layer, a line layer, or a point layer.</span></span>  
  
 <span data-ttu-id="c4981-153">可以为层设置以下选项：</span><span class="sxs-lookup"><span data-stu-id="c4981-153">The following options can be set for the layer:</span></span>  
  
-   <span data-ttu-id="c4981-154">关联的分析数据和匹配字段。</span><span class="sxs-lookup"><span data-stu-id="c4981-154">The associated analytical data and match fields.</span></span> <span data-ttu-id="c4981-155">空间数据源在“地图”窗格中对应层的名称之下列出。</span><span class="sxs-lookup"><span data-stu-id="c4981-155">The source of the spatial data is listed on the Map pane under the name of the layer.</span></span> <span data-ttu-id="c4981-156">当嵌入源时，层的地图元素是报表定义的组成部分。</span><span class="sxs-lookup"><span data-stu-id="c4981-156">When the source is embedded, the map elements for the layer are part of the report definition.</span></span> <span data-ttu-id="c4981-157">如果未嵌入源，则将在运行时检索空间数据，并且报表处理器将在处理报表时为层创建地图元素。</span><span class="sxs-lookup"><span data-stu-id="c4981-157">If the source is not embedded, then the spatial data is retrieved at run time and the report processor creates the map elements for the layer when the report is processed.</span></span> <span data-ttu-id="c4981-158">若要更改层的数据选项，请使用“地图层”对话框中的“分析数据”页。</span><span class="sxs-lookup"><span data-stu-id="c4981-158">To change data options on the layer, use the Analytical Data page in the Map Layer dialog box.</span></span>  
  
-   <span data-ttu-id="c4981-159">层绘制顺序。</span><span class="sxs-lookup"><span data-stu-id="c4981-159">Layer drawing order.</span></span> <span data-ttu-id="c4981-160">您查看“地图”窗格中列出的各层的顺序就是层的反向绘制顺序。</span><span class="sxs-lookup"><span data-stu-id="c4981-160">The order that you see the layers listed in the Map pane is the reverse drawing order for the layers.</span></span> <span data-ttu-id="c4981-161">列表中的最后一层最先绘制。</span><span class="sxs-lookup"><span data-stu-id="c4981-161">The last layer in the list is drawn first.</span></span> <span data-ttu-id="c4981-162">例如，如果您希望某个点层上的点显示在多边形层中各多边形的顶部，则首先绘制点层，然后绘制多边形层。</span><span class="sxs-lookup"><span data-stu-id="c4981-162">For example, if you want the points on a point layer to appear on top of the polygons in the polygon layer, the point layer should be first and the polygon layer second.</span></span>  
  
-   <span data-ttu-id="c4981-163">层可见性，包括透明度。</span><span class="sxs-lookup"><span data-stu-id="c4981-163">Layer visibility, including transparency.</span></span> <span data-ttu-id="c4981-164">若要让一层透过另一层显示，请将透明度设置为大于 0 的值。</span><span class="sxs-lookup"><span data-stu-id="c4981-164">To have one layer show through another layer, set the transparency to a value higher than 0.</span></span> <span data-ttu-id="c4981-165">值为 100% 表示该层不可见。</span><span class="sxs-lookup"><span data-stu-id="c4981-165">A value of 100% means the layer is not visible.</span></span> <span data-ttu-id="c4981-166">若要处理单个层，可以使用“地图”窗格中的 **“可见性”** 图标，轻松地单独显示或隐藏每一层。</span><span class="sxs-lookup"><span data-stu-id="c4981-166">To work with an individual layer, you can easily show or hide each layer independently by using the **Visibility** icon in the Map pane.</span></span> <span data-ttu-id="c4981-167">还可以设置缩放级别选项，以根据缩放级别指定何时在层上显示或隐藏地图元素。</span><span class="sxs-lookup"><span data-stu-id="c4981-167">You can also set zoom level options to specify when to show or hide map elements on the layer based on the zoom level.</span></span>  
  
-   <span data-ttu-id="c4981-168">为当前视区中心和缩放级别添加 Bing 地图图块层。</span><span class="sxs-lookup"><span data-stu-id="c4981-168">Add a Bing map tile layer for the current viewport center and zoom level.</span></span> <span data-ttu-id="c4981-169">您不需要为图块层指定地理坐标。</span><span class="sxs-lookup"><span data-stu-id="c4981-169">You do not need to specify the geographic coordinates for a tile layer.</span></span> <span data-ttu-id="c4981-170">如果坐标系为“地理”、投影为“Mercator”、Bing 地图服务器可用且报表服务器已配置为支持自动图块加载功能，则将自动加载图块以与视区区域匹配。</span><span class="sxs-lookup"><span data-stu-id="c4981-170">Tiles are automatically loaded to match the viewport area when the coordinate system is Geographic, the projection is Mercator, the Bing Maps servers are available, and when the report server has been configured to support this feature.</span></span> <span data-ttu-id="c4981-171">对于每个报表，可以指定是否使用安全连接来检索图块。</span><span class="sxs-lookup"><span data-stu-id="c4981-171">For each report, you can specify whether to use a secure connection to retrieve tiles.</span></span>  
  
 <span data-ttu-id="c4981-172">有关层的详细信息，请参阅[添加、更改或删除地图或地图层（报表生成器和 SSRS）](add-change-or-delete-a-map-or-map-layer-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="c4981-172">For more information about layers, see [Add, Change, or Delete a Map or Map Layer &#40;Report Builder and SSRS&#41;](add-change-or-delete-a-map-or-map-layer-report-builder-and-ssrs.md).</span></span>  
  
##  <a name="change-data-grouping-for-the-layer"></a><a name="DataGrouping"></a> <span data-ttu-id="c4981-173">更改层的数据分组</span><span class="sxs-lookup"><span data-stu-id="c4981-173">Change Data Grouping for the Layer</span></span>  
 <span data-ttu-id="c4981-174">您可以自定义为您自己的形状聚合空间数据的方式。</span><span class="sxs-lookup"><span data-stu-id="c4981-174">You can customize the way to aggregate spatial data for your own shapes.</span></span> <span data-ttu-id="c4981-175">若要设置某一层的组属性，请在“地图”窗格中选择该层，并且在该层的“属性”窗格中，单击“组”，然后单击省略号 (…) 以便打开“组”属性  。</span><span class="sxs-lookup"><span data-stu-id="c4981-175">To set the group properties for a layer, select the layer in the Map pane, and in the Properties pane for the layer, click **Group**, and then click the ellipsis (...) to open the Group properties.</span></span> <span data-ttu-id="c4981-176">在该对话框中，您可以指定组表达式、创建组变量并且筛选用于分组的数据。</span><span class="sxs-lookup"><span data-stu-id="c4981-176">In this dialog box, you can specify group expressions, create group variables, and filter data that is used for grouping.</span></span>  
  
 <span data-ttu-id="c4981-177">组表达式指定如何为层上的每个地图元素聚合与空间数据具有一定关系的分析数据。</span><span class="sxs-lookup"><span data-stu-id="c4981-177">The group expression specifies how analytical data that has a relationship to spatial data is aggregated for each map element on the layer.</span></span> <span data-ttu-id="c4981-178">默认情况下，组表达式是为空间数据与分析数据之间的关系指定的一组匹配字段。</span><span class="sxs-lookup"><span data-stu-id="c4981-178">By default, the group expression is the set of match fields that was specified for the relationship between the spatial data and the analytical data.</span></span> <span data-ttu-id="c4981-179">例如，对于显示某个国家或地区的城市位置和人口规模的气泡地图，匹配字段必须包括城市名称 [City] 和区域名称 [Region]，因为可能有多个城市具有相同的名称。</span><span class="sxs-lookup"><span data-stu-id="c4981-179">For example, for a bubble map that displays city locations and population size for a country or region, the match fields include city name [City] and region name [Region] because there can be multiple cities with the same name.</span></span> <span data-ttu-id="c4981-180">相应的组表达式包括两个字段：[City] 和 [Region]。</span><span class="sxs-lookup"><span data-stu-id="c4981-180">The corresponding group expression includes two fields: [City] and [Region].</span></span>  
  
 <span data-ttu-id="c4981-181">有关详细信息，请参阅 [地图提示：如何将形状文件导入到 SQL Server 中并且聚合空间数据](https://go.microsoft.com/fwlink/?LinkID=214991)。</span><span class="sxs-lookup"><span data-stu-id="c4981-181">For more information, see [Map Tips: How To Import Shapefiles Into SQL Server and Aggregate Spatial Data](https://go.microsoft.com/fwlink/?LinkID=214991).</span></span>  
  
 
  
##  <a name="change-options-for-the-map-elements-on-the-layer"></a><a name="MapElements"></a> <span data-ttu-id="c4981-182">更改层上地图元素的选项</span><span class="sxs-lookup"><span data-stu-id="c4981-182">Change Options for the Map Elements on the Layer</span></span>  
 <span data-ttu-id="c4981-183">地图元素是层上的点、线条或多边形，它们基于空间数据。</span><span class="sxs-lookup"><span data-stu-id="c4981-183">Map elements are the points, lines, or polygons on a layer that are based on the spatial data.</span></span> <span data-ttu-id="c4981-184">对于地图元素，可以设置以下选项。</span><span class="sxs-lookup"><span data-stu-id="c4981-184">For map elements, the following options can be set.</span></span> <span data-ttu-id="c4981-185">这些选项适用于层上的所有地图元素，无论这些元素是否为嵌入的元素：</span><span class="sxs-lookup"><span data-stu-id="c4981-185">These options apply to all map elements on the layer, whether or not they are embedded:</span></span>  
  
-   <span data-ttu-id="c4981-186">标签、标签可见性、标签偏移量和格式。</span><span class="sxs-lookup"><span data-stu-id="c4981-186">Labels, label visibility, label offset, and formatting.</span></span>  
  
-   <span data-ttu-id="c4981-187">边框和填充。</span><span class="sxs-lookup"><span data-stu-id="c4981-187">Borders and fill.</span></span>  
  
-   <span data-ttu-id="c4981-188">钻取操作。</span><span class="sxs-lookup"><span data-stu-id="c4981-188">Drillthrough actions.</span></span>  
  
-   <span data-ttu-id="c4981-189">显示选项。</span><span class="sxs-lookup"><span data-stu-id="c4981-189">Display options.</span></span>  
  
 <span data-ttu-id="c4981-190">地图元素的显示选项遵循一个优先级顺序，此顺序基于层、地图元素、地图元素的规则以及嵌入地图元素的覆盖选项。</span><span class="sxs-lookup"><span data-stu-id="c4981-190">Display options for map elements follow a precedence order based on the layer, the map element, rules for the map element, and override options for embedded map elements.</span></span>  
  
 <span data-ttu-id="c4981-191">若要更改这些选项，请右键单击地图元素，然后使用嵌入的属性对话框。</span><span class="sxs-lookup"><span data-stu-id="c4981-191">To change these options, right-click the map element, use the embedded properties dialog box.</span></span> <span data-ttu-id="c4981-192">例如，对于嵌入的多边形，使用“地图嵌入多边形属性”对话框中的“常规”页以及相关页。</span><span class="sxs-lookup"><span data-stu-id="c4981-192">For example, for an embedded polygon, use the Map Embedded Polygon Properties Dialog Box, General page and related pages.</span></span>  
  

  
##  <a name="understanding-display-option-precedence"></a><a name="Precedence"></a> <span data-ttu-id="c4981-193">了解显示选项优先级</span><span class="sxs-lookup"><span data-stu-id="c4981-193">Understanding Display Option Precedence</span></span>  
 <span data-ttu-id="c4981-194">当您要控制地图层上点、线条或多边形的显示外观时，必须了解可以在何处设置显示选项，以及哪些选项的优先级较高。</span><span class="sxs-lookup"><span data-stu-id="c4981-194">When you want to control the display appearance of a point, line, or polygon on a map layer, you must understand where display options can be set and which options have a higher precedence.</span></span> <span data-ttu-id="c4981-195">下面的显示选项按从低到高的顺序列出。</span><span class="sxs-lookup"><span data-stu-id="c4981-195">The following display options are listed from lowest to highest.</span></span> <span data-ttu-id="c4981-196">在该列表中，较高的显示选项覆盖较低的显示选项：</span><span class="sxs-lookup"><span data-stu-id="c4981-196">Higher display options override lower display options in this list:</span></span>  
  
-   <span data-ttu-id="c4981-197">层选项。</span><span class="sxs-lookup"><span data-stu-id="c4981-197">Layer options.</span></span>  
  
-   <span data-ttu-id="c4981-198">每层上的点、线条或多边形选项。</span><span class="sxs-lookup"><span data-stu-id="c4981-198">Points, Lines, or Polygons options on each layer.</span></span> <span data-ttu-id="c4981-199">无论地图元素是在处理报表时动态检索的，还是地图元素嵌入在报表元素中，上述选项均适用。</span><span class="sxs-lookup"><span data-stu-id="c4981-199">This applies whether the map elements are dynamically retrieved when the report is processed or whether they the map elements are embedded in the report definition.</span></span> <span data-ttu-id="c4981-200">例如，您可以为地图上的所有元素指定一种填充颜色。</span><span class="sxs-lookup"><span data-stu-id="c4981-200">For example, you specify a fill color for all elements on a layer.</span></span>  
  
-   <span data-ttu-id="c4981-201">规则。</span><span class="sxs-lookup"><span data-stu-id="c4981-201">Rules.</span></span> <span data-ttu-id="c4981-202">可以设置规则来控制层上所有地图元素的颜色、大小、宽度或标记类型。</span><span class="sxs-lookup"><span data-stu-id="c4981-202">You can set rules to control color, size, width, or marker type for all map elements on a layer.</span></span> <span data-ttu-id="c4981-203">可以设置的规则取决于地图元素的类型。</span><span class="sxs-lookup"><span data-stu-id="c4981-203">The rules that you can set depend on the type of map element.</span></span>  
  
    -   <span data-ttu-id="c4981-204">颜色规则。</span><span class="sxs-lookup"><span data-stu-id="c4981-204">Color Rules.</span></span> <span data-ttu-id="c4981-205">应用于点、线条、多边形的标记以及多边形中心点的标记。</span><span class="sxs-lookup"><span data-stu-id="c4981-205">Apply to markers for points, lines, polygons, and markers for polygon center points.</span></span>  
  
    -   <span data-ttu-id="c4981-206">大小规则。</span><span class="sxs-lookup"><span data-stu-id="c4981-206">Size Rules.</span></span> <span data-ttu-id="c4981-207">应用于点的标记以及多边形中心点的标记。</span><span class="sxs-lookup"><span data-stu-id="c4981-207">Apply to markers for points and markers for polygon center points.</span></span>  
  
    -   <span data-ttu-id="c4981-208">宽度规则。</span><span class="sxs-lookup"><span data-stu-id="c4981-208">Width Rules.</span></span> <span data-ttu-id="c4981-209">应用于线条宽度。</span><span class="sxs-lookup"><span data-stu-id="c4981-209">Applies to line widths.</span></span>  
  
    -   <span data-ttu-id="c4981-210">标记类型规则。</span><span class="sxs-lookup"><span data-stu-id="c4981-210">Marker Type Rules.</span></span> <span data-ttu-id="c4981-211">应用于点的标记以及多边形中心点的标记。</span><span class="sxs-lookup"><span data-stu-id="c4981-211">Applies to markers for points and markers for polygon center points.</span></span>  
  
-   <span data-ttu-id="c4981-212">层上各个嵌入点、线条或多边形的覆盖选项。</span><span class="sxs-lookup"><span data-stu-id="c4981-212">Override options for individual embedded points, lines, or polygons on a layer.</span></span> <span data-ttu-id="c4981-213">您进行的更改将是永久性的。</span><span class="sxs-lookup"><span data-stu-id="c4981-213">Changes that you make are permanent.</span></span> <span data-ttu-id="c4981-214">若要取消这些更改，必须为该层重新加载数据。</span><span class="sxs-lookup"><span data-stu-id="c4981-214">To revert these changes, you must reload the data for the layer.</span></span>  
  
 <span data-ttu-id="c4981-215">有关详细信息，请参阅 [按规则和分析数据更改多边形、线条和点的显示方式（报表生成器和 SSRS）](vary-polygon-line-and-point-display-by-rules-and-analytical-data.md)。</span><span class="sxs-lookup"><span data-stu-id="c4981-215">For more information, see [Vary Polygon, Line, and Point Display by Rules and Analytical Data &#40;Report Builder and SSRS&#41;](vary-polygon-line-and-point-display-by-rules-and-analytical-data.md).</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="c4981-216">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c4981-216">See Also</span></span>  
 <span data-ttu-id="c4981-217">[地图向导和地图层向导（报表生成器和 SSRS）](map-wizard-and-map-layer-wizard-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c4981-217">[Map Wizard and Map Layer Wizard &#40;Report Builder and SSRS&#41;](map-wizard-and-map-layer-wizard-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="c4981-218">地图（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="c4981-218">Maps &#40;Report Builder and SSRS&#41;</span></span>](maps-report-builder-and-ssrs.md)  
  
  
