---
title: 添加、更改或删除地图或地图层（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10526"
- sql12.rtp.rptdesigner.maptilelayerproperties.general.f1
- "10529"
- "10525"
- "10535"
- sql12.rtp.rptdesigner.mappolygonlayerproperties.general.f1
- sql12.rtp.rptdesigner.shared.layervisibility.f1
- sql12.rtp.rptdesigner.mappointlayerproperties.general.f1
- sql12.rtp.rptdesigner.shared.layerfilters.f1
- "10524"
- sql12.rtp.rptdesigner.maplayerproperties.general.f1
- sql12.rtp.rptdesigner.maplinelayerproperties.general.f1
- "10532"
- "10528"
- "10527"
- sql12.rtp.rptdesigner.maplayerproperties.analyticaldata.f1
ms.assetid: 6e89815e-187e-45bf-bf63-3d5c4a246360
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4e9fd178d36ee3322c0bd94dd44d621439139b71
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586465"
---
# <a name="add-change-or-delete-a-map-or-map-layer-report-builder-and-ssrs"></a><span data-ttu-id="eab5f-102">添加、更改或删除地图或地图层（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="eab5f-102">Add, Change, or Delete a Map or Map Layer (Report Builder and SSRS)</span></span>
  <span data-ttu-id="eab5f-103">地图是层的集合。</span><span class="sxs-lookup"><span data-stu-id="eab5f-103">A map is a collection of layers.</span></span> <span data-ttu-id="eab5f-104">当您向报表添加一个地图时，就定义了第一个层。</span><span class="sxs-lookup"><span data-stu-id="eab5f-104">When you add a map to a report, you define the first layer.</span></span> <span data-ttu-id="eab5f-105">可以使用地图层向导创建其他层。</span><span class="sxs-lookup"><span data-stu-id="eab5f-105">You can create additional layers by using the map layer wizard.</span></span>  
  
 <span data-ttu-id="eab5f-106">若要添加、删除或更改层的选项，最简单的方法是使用地图层向导。</span><span class="sxs-lookup"><span data-stu-id="eab5f-106">The easiest way to add, remove, or change options for a layer is to use the map layer wizard.</span></span> <span data-ttu-id="eab5f-107">还可以从“地图”窗格中手动更改选项。</span><span class="sxs-lookup"><span data-stu-id="eab5f-107">You can also change options manually from the Map pane.</span></span> <span data-ttu-id="eab5f-108">若要显示 **“地图”** 窗格，请单击报表设计图面中的地图。</span><span class="sxs-lookup"><span data-stu-id="eab5f-108">To display the **Map** pane, click in the map on the report design surface.</span></span> <span data-ttu-id="eab5f-109">下图显示该窗格的各个部分：</span><span class="sxs-lookup"><span data-stu-id="eab5f-109">The following figure displays the parts of the pane:</span></span>  
  
 <span data-ttu-id="eab5f-110">![rsMapLayerZone](../media/rsmaplayerzone.gif "rsMapLayerZone")</span><span class="sxs-lookup"><span data-stu-id="eab5f-110">![rsMapLayerZone](../media/rsmaplayerzone.gif "rsMapLayerZone")</span></span>  
  
 <span data-ttu-id="eab5f-111">按照地图层在“地图”窗格中的显示顺序从下到上绘制地图层。</span><span class="sxs-lookup"><span data-stu-id="eab5f-111">Map layers are drawn from bottom to top in the order that they appear in the Map pane.</span></span> <span data-ttu-id="eab5f-112">在上图中，首先绘制图块层，最后绘制多边形层。</span><span class="sxs-lookup"><span data-stu-id="eab5f-112">In the previous figure, the tile layer is drawn first and the polygon layer is drawn last.</span></span> <span data-ttu-id="eab5f-113">后来绘制的层可能隐藏先前绘制的层上的地图元素。</span><span class="sxs-lookup"><span data-stu-id="eab5f-113">Layers that are drawn later might hide map elements on layers that are drawn earlier.</span></span> <span data-ttu-id="eab5f-114">可以使用“地图”窗格工具栏上的箭头键来更改层的顺序。</span><span class="sxs-lookup"><span data-stu-id="eab5f-114">You can change the order of layers by using the arrow keys on the Map pane toolbar.</span></span> <span data-ttu-id="eab5f-115">若要显示或隐藏层，请切换可见性图标。</span><span class="sxs-lookup"><span data-stu-id="eab5f-115">To show or hide layers, toggle the visibility icon.</span></span> <span data-ttu-id="eab5f-116">您可以在 `Visibility` "**层数据**属性" 对话框的页上更改层的透明度。</span><span class="sxs-lookup"><span data-stu-id="eab5f-116">You can change the transparency of a layer on the `Visibility` page of the **Layer Data** properties dialog box.</span></span>  
  
 <span data-ttu-id="eab5f-117">下表列出了 **“地图”** 窗格的工具栏图标：</span><span class="sxs-lookup"><span data-stu-id="eab5f-117">The following table displays the toolbar icons for the **Map** pane.</span></span>  
  
|<span data-ttu-id="eab5f-118">符号</span><span class="sxs-lookup"><span data-stu-id="eab5f-118">Symbol</span></span>|<span data-ttu-id="eab5f-119">说明</span><span class="sxs-lookup"><span data-stu-id="eab5f-119">Description</span></span>|<span data-ttu-id="eab5f-120">何时使用</span><span class="sxs-lookup"><span data-stu-id="eab5f-120">When to use</span></span>|  
|------------|-----------------|-----------------|  
|<span data-ttu-id="eab5f-121">![rs_IconMapLayerWizard](../../tutorials/media/rs-iconmaplayerwizard.gif "rs_IconMapLayerWizard")</span><span class="sxs-lookup"><span data-stu-id="eab5f-121">![rs_IconMapLayerWizard](../../tutorials/media/rs-iconmaplayerwizard.gif "rs_IconMapLayerWizard")</span></span>|<span data-ttu-id="eab5f-122">地图层向导</span><span class="sxs-lookup"><span data-stu-id="eab5f-122">Map Layer Wizard</span></span>|<span data-ttu-id="eab5f-123">若要使用向导添加层，请单击 **“新建层向导”** 。</span><span class="sxs-lookup"><span data-stu-id="eab5f-123">To add a layer by using a wizard, click **New layer wizard**.</span></span>|  
|<span data-ttu-id="eab5f-124">![rs_IconMapAddLayer](../../tutorials/media/rs-iconmapaddlayer.gif "rs_IconMapAddLayer")</span><span class="sxs-lookup"><span data-stu-id="eab5f-124">![rs_IconMapAddLayer](../../tutorials/media/rs-iconmapaddlayer.gif "rs_IconMapAddLayer")</span></span>|<span data-ttu-id="eab5f-125">添加层</span><span class="sxs-lookup"><span data-stu-id="eab5f-125">Add Layer</span></span>|<span data-ttu-id="eab5f-126">若要手动添加层，请单击 **“添加层”** ，然后单击要添加的地图层类型。</span><span class="sxs-lookup"><span data-stu-id="eab5f-126">To manually add a layer, click **Add Layer**, and then click the type of map layer to add.</span></span>|  
|<span data-ttu-id="eab5f-127">![rs_IconMapPolygonLayer](../media/rs-iconmappolygonlayer.gif "rs_IconMapPolygonLayer")</span><span class="sxs-lookup"><span data-stu-id="eab5f-127">![rs_IconMapPolygonLayer](../media/rs-iconmappolygonlayer.gif "rs_IconMapPolygonLayer")</span></span>|<span data-ttu-id="eab5f-128">多边形层</span><span class="sxs-lookup"><span data-stu-id="eab5f-128">Polygon Layer</span></span>|<span data-ttu-id="eab5f-129">添加显示基于一组多边形坐标的区域或形状的地图层。</span><span class="sxs-lookup"><span data-stu-id="eab5f-129">Add a map layer that displays areas or shapes that are based sets of polygon coordinates.</span></span>|  
|<span data-ttu-id="eab5f-130">![rs_IconMapLineLayer](../media/rs-iconmaplinelayer.gif "rs_IconMapLineLayer")</span><span class="sxs-lookup"><span data-stu-id="eab5f-130">![rs_IconMapLineLayer](../media/rs-iconmaplinelayer.gif "rs_IconMapLineLayer")</span></span>|<span data-ttu-id="eab5f-131">线条层</span><span class="sxs-lookup"><span data-stu-id="eab5f-131">Line Layer</span></span>|<span data-ttu-id="eab5f-132">添加显示基于一组线条坐标的路径或路线的地图层。</span><span class="sxs-lookup"><span data-stu-id="eab5f-132">Add a map layer that displays paths or routes that are based on sets of line coordinates.</span></span>|  
|<span data-ttu-id="eab5f-133">![rs_IconMapPointLayer](../media/rs-iconmappointlayer.gif "rs_IconMapPointLayer")</span><span class="sxs-lookup"><span data-stu-id="eab5f-133">![rs_IconMapPointLayer](../media/rs-iconmappointlayer.gif "rs_IconMapPointLayer")</span></span>|<span data-ttu-id="eab5f-134">点层</span><span class="sxs-lookup"><span data-stu-id="eab5f-134">Point Layer</span></span>|<span data-ttu-id="eab5f-135">添加显示基于一组点坐标的位置的地图层。</span><span class="sxs-lookup"><span data-stu-id="eab5f-135">Add a map layer that displays locations that are based on sets of point coordinates.</span></span>|  
|<span data-ttu-id="eab5f-136">![rs_IconMapTileLayer](../media/rs-iconmaptilelayer.gif "rs_IconMapTileLayer")</span><span class="sxs-lookup"><span data-stu-id="eab5f-136">![rs_IconMapTileLayer](../media/rs-iconmaptilelayer.gif "rs_IconMapTileLayer")</span></span>|<span data-ttu-id="eab5f-137">图块层</span><span class="sxs-lookup"><span data-stu-id="eab5f-137">Tile Layer</span></span>|<span data-ttu-id="eab5f-138">添加显示 Bing 地图图块的一个地图层，这些图块对应于由视区定义的当前地图视图区域。</span><span class="sxs-lookup"><span data-stu-id="eab5f-138">Add a map layer that displays Bing Map tiles that correspond to the current map view area that is defined by the viewport.</span></span>|  
  
 <span data-ttu-id="eab5f-139">“地图”窗格的底部是“地图”视图区域。</span><span class="sxs-lookup"><span data-stu-id="eab5f-139">At the bottom of the Map pane is the Map view area.</span></span> <span data-ttu-id="eab5f-140">若要更改地图的中心或缩放选项，请使用箭头键来调整视图中心和使用滑块来调整缩放级别。</span><span class="sxs-lookup"><span data-stu-id="eab5f-140">To change the center or zoom options for the map, use the arrow keys to adjust the view center and the slider to adjust the zoom level.</span></span>  
  
 <span data-ttu-id="eab5f-141">有关层的详细信息，请参阅 [地图（报表生成器和 SSRS）](maps-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="eab5f-141">For more information about layers, see [Maps &#40;Report Builder and SSRS&#41;](maps-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="to-add-a-layer-from-the-map-layer-wizard"></a><a name="AddLayer"></a> <span data-ttu-id="eab5f-142">从地图层向导添加层</span><span class="sxs-lookup"><span data-stu-id="eab5f-142">To add a layer from the map layer wizard</span></span>  
  
-   <span data-ttu-id="eab5f-143">从“功能区”的 **“插入”** 菜单上，单击 **“地图”** ，然后单击 **“地图” Wizard.**</span><span class="sxs-lookup"><span data-stu-id="eab5f-143">From the Ribbon, on the **Insert** menu, click **Map**, and then click **Map Wizard.**</span></span> <span data-ttu-id="eab5f-144">。通过该向导可以向现有地图添加层。</span><span class="sxs-lookup"><span data-stu-id="eab5f-144">The wizard enables you to add a layer to the existing map.</span></span> <span data-ttu-id="eab5f-145">地图向导和地图层向导的大多数向导页是相同的。</span><span class="sxs-lookup"><span data-stu-id="eab5f-145">Most wizard pages are identical between the map wizard and the map layer wizard.</span></span>  
  
     <span data-ttu-id="eab5f-146">有关详细信息，请参阅 [地图向导和地图层向导（报表生成器和 SSRS）](map-wizard-and-map-layer-wizard-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="eab5f-146">For more information, see [Map Wizard and Map Layer Wizard &#40;Report Builder and SSRS&#41;](map-wizard-and-map-layer-wizard-report-builder-and-ssrs.md).</span></span>  

##  <a name="to-change-options-for-a-layer-by-using-the-map-layer-wizard"></a><a name="ChangeLayer"></a> <span data-ttu-id="eab5f-147">使用地图层向导更改层的选项</span><span class="sxs-lookup"><span data-stu-id="eab5f-147">To change options for a layer by using the map layer wizard</span></span>  
  
-   <span data-ttu-id="eab5f-148">运行地图层向导。</span><span class="sxs-lookup"><span data-stu-id="eab5f-148">Run the map layer wizard.</span></span> <span data-ttu-id="eab5f-149">此向导允许您更改使用地图层向导创建的层的选项。</span><span class="sxs-lookup"><span data-stu-id="eab5f-149">This wizard enables you to change options for a layer that you created by using the map layer wizard.</span></span> <span data-ttu-id="eab5f-150">在“地图”窗格中，右键单击该层，然后在工具栏上单击层向导按钮 (![rs_IconMapLayerWizard](../../tutorials/media/rs-iconmaplayerwizard.gif "rs_IconMapLayerWizard"))。</span><span class="sxs-lookup"><span data-stu-id="eab5f-150">In the Map pane, right-click the layer, and on the toolbar, click the layer wizard button (![rs_IconMapLayerWizard](../../tutorials/media/rs-iconmaplayerwizard.gif "rs_IconMapLayerWizard")).</span></span>  
  
     <span data-ttu-id="eab5f-151">有关详细信息，请参阅 [地图向导和地图层向导（报表生成器和 SSRS）](map-wizard-and-map-layer-wizard-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="eab5f-151">For more information, see [Map Wizard and Map Layer Wizard &#40;Report Builder and SSRS&#41;](map-wizard-and-map-layer-wizard-report-builder-and-ssrs.md).</span></span>  

##  <a name="to-add-a-point-line-or-polygon-layer-from-the-map-pane-toolbar"></a><a name="AddVectorLayer"></a> <span data-ttu-id="eab5f-152">从“地图”窗格工具栏添加点、线条或多边形层</span><span class="sxs-lookup"><span data-stu-id="eab5f-152">To add a point, line, or polygon layer from the Map pane toolbar</span></span>  
  
1.  <span data-ttu-id="eab5f-153">单击地图直到显示“地图”窗格。</span><span class="sxs-lookup"><span data-stu-id="eab5f-153">Click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="eab5f-154">依次单击工具栏中的“添加层”  按钮，以及下拉列表中的要添加的层类型：“点”  、“线”  或“多边形”  。</span><span class="sxs-lookup"><span data-stu-id="eab5f-154">On the toolbar, click the **Add Layer** button, and from the drop-down list, click the type of layer that you want to add: **Point**, **Line**, or **Polygon**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="eab5f-155">尽管可以手动添加并配置地图层，我们仍建议您使用地图层向导来添加新层。</span><span class="sxs-lookup"><span data-stu-id="eab5f-155">Although you can add a map layer and configure it manually, we recommend that you use the map layer wizard to add new layers.</span></span> <span data-ttu-id="eab5f-156">若要在“地图”窗格工具栏中启动向导，请单击层向导按钮 (![rs_IconMapLayerWizard](../../tutorials/media/rs-iconmaplayerwizard.gif "rs_IconMapLayerWizard"))。</span><span class="sxs-lookup"><span data-stu-id="eab5f-156">To launch the wizard from the Map pane toolbar, click the layer wizard button (![rs_IconMapLayerWizard](../../tutorials/media/rs-iconmaplayerwizard.gif "rs_IconMapLayerWizard")).</span></span>  
  
3.  <span data-ttu-id="eab5f-157">右键单击该层，然后单击“层数据”  。</span><span class="sxs-lookup"><span data-stu-id="eab5f-157">Right-click the layer, and then click **Layer Data**.</span></span>  
  
4.  <span data-ttu-id="eab5f-158">在 **“使用的空间数据来自”** 中，选择空间数据的源。</span><span class="sxs-lookup"><span data-stu-id="eab5f-158">In **Use spatial data from**, select the source of spatial data.</span></span> <span data-ttu-id="eab5f-159">选项根据您的选择内容而有所不同。</span><span class="sxs-lookup"><span data-stu-id="eab5f-159">Options vary based on your selection.</span></span>  
  
     <span data-ttu-id="eab5f-160">如果要将此层上的报表的分析数据可视化，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="eab5f-160">If you want to visualize analytical from your report on this layer, do the following:</span></span>  
  
    1.  <span data-ttu-id="eab5f-161">单击 **“分析数据”** 。</span><span class="sxs-lookup"><span data-stu-id="eab5f-161">Click **Analytical data**.</span></span>  
  
    2.  <span data-ttu-id="eab5f-162">在 **“分析数据集”** 中，单击包含分析数据和匹配字段（用于建立分析数据和空间数据之间的关系）的数据集的名称。</span><span class="sxs-lookup"><span data-stu-id="eab5f-162">In **Analytical dataset**, click the name of the dataset that contains analytical data and the match fields to build a relationship between analytical and spatial data.</span></span>  
  
    3.  <span data-ttu-id="eab5f-163">单击“添加”  。</span><span class="sxs-lookup"><span data-stu-id="eab5f-163">Click **Add**.</span></span>  
  
    4.  <span data-ttu-id="eab5f-164">键入空间数据集中匹配字段的名称。</span><span class="sxs-lookup"><span data-stu-id="eab5f-164">Type the name of the match field from the spatial dataset.</span></span>  
  
    5.  <span data-ttu-id="eab5f-165">键入分析数据集中匹配字段的名称。</span><span class="sxs-lookup"><span data-stu-id="eab5f-165">Type the name of the match field from the analytical dataset.</span></span>  
  
     <span data-ttu-id="eab5f-166">有关链接空间数据和分析数据的详细信息，请参阅[自定义地图或地图层的数据和显示（报表生成器和 SSRS）](customize-the-data-and-display-of-a-map-or-map-layer-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="eab5f-166">For more information about linking spatial and analytical data, see [Customize the Data and Display of a Map or Map Layer &#40;Report Builder and SSRS&#41;](customize-the-data-and-display-of-a-map-or-map-layer-report-builder-and-ssrs.md).</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

##  <a name="to-filter-analytical-data-for-the-layer"></a><a name="FilterAnalyticalData"></a> <span data-ttu-id="eab5f-167">为层筛选分析数据</span><span class="sxs-lookup"><span data-stu-id="eab5f-167">To filter analytical data for the layer</span></span>  
  
1.  <span data-ttu-id="eab5f-168">单击地图直到显示“地图”窗格。</span><span class="sxs-lookup"><span data-stu-id="eab5f-168">Click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="eab5f-169">在“地图”窗格中右键单击层，然后单击“层数据”  。</span><span class="sxs-lookup"><span data-stu-id="eab5f-169">Right-click the layer in the Map pane, and then click  **Layer Data**.</span></span>  
  
3.  <span data-ttu-id="eab5f-170">单击 **“筛选器”** 。</span><span class="sxs-lookup"><span data-stu-id="eab5f-170">Click **Filters**.</span></span>  
  
4.  <span data-ttu-id="eab5f-171">定义筛选器公式以便限制用于地图显示的分析数据。</span><span class="sxs-lookup"><span data-stu-id="eab5f-171">Define a filter equation to limit the analytical data that is used in the map display.</span></span> <span data-ttu-id="eab5f-172">有关详细信息，请参阅[筛选器公式示例（报表生成器和 SSRS）](filter-equation-examples-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="eab5f-172">For more information, see [Filter Equation Examples &#40;Report Builder and SSRS&#41;](filter-equation-examples-report-builder-and-ssrs.md).</span></span>  

##  <a name="to-control-point-properties-for-a-point-layer-or-for-polygon-center-points"></a><a name="PointProperties"></a> <span data-ttu-id="eab5f-173">为点层或多边形中心点控制点属性</span><span class="sxs-lookup"><span data-stu-id="eab5f-173">To control point properties for a point layer or for polygon center points</span></span>  
  
1.  <span data-ttu-id="eab5f-174">选择 **“地图点属性”** 对话框中的 **“常规”** 可以更改以下地图元素的标签、工具提示和标记类型选项：</span><span class="sxs-lookup"><span data-stu-id="eab5f-174">Select **General** on the **Map Point Properties** dialog box to change label, tooltip, and marker type options for the following map elements:</span></span>  
  
    -   <span data-ttu-id="eab5f-175">点层上的所有动态或嵌入的点。</span><span class="sxs-lookup"><span data-stu-id="eab5f-175">All dynamic or embedded points on a point layer.</span></span> <span data-ttu-id="eab5f-176">点的颜色规则、大小规则和标记类型规则覆盖这些选项。</span><span class="sxs-lookup"><span data-stu-id="eab5f-176">Color rules, size rules, and marker type rules for points override these options.</span></span> <span data-ttu-id="eab5f-177">若要覆盖特定嵌入点的选项，请使用 [Map Embedded Point Properties Dialog Box, Marker](../map-embedded-point-properties-dialog-box-marker.md) 页。</span><span class="sxs-lookup"><span data-stu-id="eab5f-177">To override options for a specific embedded point, use the [Map Embedded Point Properties Dialog Box, Marker](../map-embedded-point-properties-dialog-box-marker.md) page.</span></span>  
  
    -   <span data-ttu-id="eab5f-178">多边形层上的所有动态或嵌入的多边形的中心点。</span><span class="sxs-lookup"><span data-stu-id="eab5f-178">The center point for all dynamic or embedded polygons on a polygon layer.</span></span> <span data-ttu-id="eab5f-179">中心点的颜色规则、大小规则和标记类型规则覆盖这些选项。</span><span class="sxs-lookup"><span data-stu-id="eab5f-179">Color rules, size rules, and marker type rules for center points override these options.</span></span> <span data-ttu-id="eab5f-180">若要覆盖特定中心点的选项，请使用 [“地图嵌入点属性”对话框，标记](../map-embedded-point-properties-dialog-box-marker.md) 页。</span><span class="sxs-lookup"><span data-stu-id="eab5f-180">To override options for a specific center point, use the [Map Embedded Point Properties Dialog Box, Marker](../map-embedded-point-properties-dialog-box-marker.md) page.</span></span>  

##  <a name="to-specify-embedded-data-as-a-source-of-spatial-data"></a><a name="Embedded"></a> <span data-ttu-id="eab5f-181">指定嵌入数据作为空间数据的源</span><span class="sxs-lookup"><span data-stu-id="eab5f-181">To specify embedded data as a source of spatial data</span></span>  
  
1.  <span data-ttu-id="eab5f-182">单击地图直到显示“地图”窗格。</span><span class="sxs-lookup"><span data-stu-id="eab5f-182">Click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="eab5f-183">右键单击该层，然后单击“层数据”  。</span><span class="sxs-lookup"><span data-stu-id="eab5f-183">Right-click the layer, and then click **Layer Data**.</span></span>  
  
3.  <span data-ttu-id="eab5f-184">在 **“使用的空间数据来自”** 中，选择 **“报表中嵌入的数据”** 。</span><span class="sxs-lookup"><span data-stu-id="eab5f-184">In **Use spatial data from**, select **Data embedded in report**.</span></span>  
  
4.  <span data-ttu-id="eab5f-185">若要从现有报表加载地图元素或基于 ESRI 文件创建地图元素，请单击 **“浏览”** ，指向该文件，然后单击 **“打开”** 。</span><span class="sxs-lookup"><span data-stu-id="eab5f-185">To load map elements from an existing report or to create map elements based on an ESRI file, click **Browse**, point to the file, and then click **Open**.</span></span> <span data-ttu-id="eab5f-186">这些地图元素嵌入在此报表定义中。</span><span class="sxs-lookup"><span data-stu-id="eab5f-186">The map elements are embedded in this report definition.</span></span> <span data-ttu-id="eab5f-187">您指向的空间数据必须与该层类型匹配。</span><span class="sxs-lookup"><span data-stu-id="eab5f-187">The spatial data that you point to must match the layer type.</span></span> <span data-ttu-id="eab5f-188">例如，对于点层，必须指向指定一组点坐标的空间数据。</span><span class="sxs-lookup"><span data-stu-id="eab5f-188">For example, for a point layer, you must point to spatial data that specifies sets of point coordinates.</span></span>  
  
5.  <span data-ttu-id="eab5f-189">在 **“空间字段”** 中，指定包含空间数据的字段的名称。</span><span class="sxs-lookup"><span data-stu-id="eab5f-189">In **Spatial field**, specify the name of the field that contains spatial data.</span></span> <span data-ttu-id="eab5f-190">您可能需要从空间数据的源确定此名称。</span><span class="sxs-lookup"><span data-stu-id="eab5f-190">You might need to determine this name from the source of spatial data.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="eab5f-191">如果不知道该字段的名称且已找到 ESRI 形状文件，请使用“链接到 ESRI 形状文件”  选项来替代此选项。</span><span class="sxs-lookup"><span data-stu-id="eab5f-191">If you do not know the name of the field and you browsed to an ESRI Shapefile, use the **Link to ESRI shape file option** instead of this option.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

##  <a name="to-specify-an-esri-shapefile-as-a-source-of-spatial-data"></a><a name="ESRI"></a> <span data-ttu-id="eab5f-192">指定 ESRI 形状文件作为空间数据的源</span><span class="sxs-lookup"><span data-stu-id="eab5f-192">To specify an ESRI Shapefile as a source of spatial data</span></span>  
  
1.  <span data-ttu-id="eab5f-193">单击地图直到显示“地图”窗格。</span><span class="sxs-lookup"><span data-stu-id="eab5f-193">Click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="eab5f-194">右键单击该层，然后单击“层数据”  。</span><span class="sxs-lookup"><span data-stu-id="eab5f-194">Right-click the layer, and then click **Layer Data**.</span></span>  
  
3.  <span data-ttu-id="eab5f-195">在 **“使用的空间数据来自”** 中，选择 **“链接到 ESRI 形状文件”** 。</span><span class="sxs-lookup"><span data-stu-id="eab5f-195">In **Use spatial data from**, select **Link to ESRI Shapefile**.</span></span>  
  
4.  <span data-ttu-id="eab5f-196">在 **“文件名”** 中，键入 ESRI 形状文件的位置，或单击 **“浏览”** 以选择 ESRI 形状文件。</span><span class="sxs-lookup"><span data-stu-id="eab5f-196">In **File name**, type the location of an ESRI Shapefile, or click **Browse** to select an ESRI Shapefile.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="eab5f-197">如果该形状文件位于本地计算机上，则将空间数据嵌入报表定义中。</span><span class="sxs-lookup"><span data-stu-id="eab5f-197">If the Shapefile is on your local computer, the spatial data is embedded in the report definition.</span></span> <span data-ttu-id="eab5f-198">若要在处理报表时动态检索数据，必须将 ESRI .shp 文件及其 .dbf 支持文件上载到报表服务器。</span><span class="sxs-lookup"><span data-stu-id="eab5f-198">To retrieve the data dynamically when the report is processed, you must upload the ESRI .shp file and its .dbf support file to the report server.</span></span> <span data-ttu-id="eab5f-199">有关详细信息，请参阅 SQL Server 联机丛书中 [Reporting Services 文档](https://go.microsoft.com/fwlink/?linkid=121312) 中的“如何上传文件或报表（报表管理器）”。</span><span class="sxs-lookup"><span data-stu-id="eab5f-199">For more information, see " How to: Upload a File or Report (Report Manager)" in the [Reporting Services documentation](https://go.microsoft.com/fwlink/?linkid=121312) in SQL Server Books Online.</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

##  <a name="to-specify-a-report-dataset-field-as-a-source-of-spatial-data"></a><a name="DatasetField"></a> <span data-ttu-id="eab5f-200">指定报表数据集字段作为空间数据的源</span><span class="sxs-lookup"><span data-stu-id="eab5f-200">To specify a report dataset field as a source of spatial data</span></span>  
  
1.  <span data-ttu-id="eab5f-201">单击地图直到显示“地图”窗格。</span><span class="sxs-lookup"><span data-stu-id="eab5f-201">Click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="eab5f-202">右键单击该层，然后单击“层数据”  。</span><span class="sxs-lookup"><span data-stu-id="eab5f-202">Right-click the layer, and then click **Layer Data**.</span></span>  
  
3.  <span data-ttu-id="eab5f-203">在 **“使用的空间数据来自”** 中，选择 **“数据集中的空间字段”** 。</span><span class="sxs-lookup"><span data-stu-id="eab5f-203">In **Use spatial data from**, select **Spatial field in a dataset**.</span></span>  
  
4.  <span data-ttu-id="eab5f-204">在 **“数据集名称”** 中，单击报表中包含您所需的空间数据的数据集的名称。</span><span class="sxs-lookup"><span data-stu-id="eab5f-204">In **Dataset name**, click the name of a dataset in the report that contains that spatial data that you want.</span></span>  
  
5.  <span data-ttu-id="eab5f-205">在 **“空间字段名称”** 中，单击数据集中包含空间数据的字段的名称。</span><span class="sxs-lookup"><span data-stu-id="eab5f-205">In **Spatial field name**, click the name of the field in the dataset that contains spatial data.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

##  <a name="to-add-a-tile-layer"></a><a name="TileLayer"></a> <span data-ttu-id="eab5f-206">添加图块层</span><span class="sxs-lookup"><span data-stu-id="eab5f-206">To add a tile layer</span></span>  
  
1.  <span data-ttu-id="eab5f-207">单击地图直到显示“地图”窗格。</span><span class="sxs-lookup"><span data-stu-id="eab5f-207">Click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="eab5f-208">在工具栏上单击“添加层”  按钮，然后从下拉列表中单击“图块层”  。</span><span class="sxs-lookup"><span data-stu-id="eab5f-208">On the toolbar, click the **Add Layer** button, and from the drop-down list, click **Tile Layer**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="eab5f-209">有关在报表中使用 Bing 地图图块的详细信息，请参阅 [其他使用条款](https://go.microsoft.com/fwlink/?LinkId=151371) 和 [隐私声明](https://go.microsoft.com/fwlink/?LinkId=151372)。</span><span class="sxs-lookup"><span data-stu-id="eab5f-209">For more information about the use of Bing map tiles in your report, see [Additional Terms of Use](https://go.microsoft.com/fwlink/?LinkId=151371) and [Privacy Statement](https://go.microsoft.com/fwlink/?LinkId=151372).</span></span>  
  
3.  <span data-ttu-id="eab5f-210">右键单击“地图”窗格中的该图块层，然后单击“图块属性”  。</span><span class="sxs-lookup"><span data-stu-id="eab5f-210">Right-click the tile layer in the Map pane, and then click **Tile Properties**.</span></span>  
  
4.  <span data-ttu-id="eab5f-211">在 **“图块选项”** 中，选择一种图块样式。</span><span class="sxs-lookup"><span data-stu-id="eab5f-211">In **Tile options**, select a tile style.</span></span> <span data-ttu-id="eab5f-212">如果 Bing 地图图块可用，则使用您选择的样式更新设计图面上的该层。</span><span class="sxs-lookup"><span data-stu-id="eab5f-212">If the Bing map tiles are available, the layer on the design surface updates with the style that you select.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="eab5f-213">当您在地图向导或地图层向导中添加多边形、线条或点层时，也可以添加图块层。</span><span class="sxs-lookup"><span data-stu-id="eab5f-213">A tile layer can also be added when you add a polygon, line, or point layer in the Map or Map Layer wizard.</span></span> <span data-ttu-id="eab5f-214">在 **“选择空间数据和地图视图选项”** 页上，选择选项 **“为该地图视图添加 Bing 地图背景”** 。</span><span class="sxs-lookup"><span data-stu-id="eab5f-214">On the **Choose spatial data and map view options** page, select the option **Add a Bing Maps background for this map view**.</span></span>  

##  <a name="to-change-the-drawing-order-of-a-layer"></a><a name="DrawingOrder"></a> <span data-ttu-id="eab5f-215">更改层的绘制顺序</span><span class="sxs-lookup"><span data-stu-id="eab5f-215">To change the drawing order of a layer</span></span>  
  
1.  <span data-ttu-id="eab5f-216">单击地图直到显示“地图”窗格。</span><span class="sxs-lookup"><span data-stu-id="eab5f-216">Click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="eab5f-217">单击“地图”窗格中的层以选中它。</span><span class="sxs-lookup"><span data-stu-id="eab5f-217">Click the layer in the Map pane to select it.</span></span>  
  
3.  <span data-ttu-id="eab5f-218">在“地图”窗格工具栏上，单击向上键或向下键来更改每个层的绘制顺序。</span><span class="sxs-lookup"><span data-stu-id="eab5f-218">On the Map pane toolbar, click the up or down arrow to change the drawing order of each layer.</span></span>  

##  <a name="to-change-the-transparency-of-a-polygon-line-or-point-layer"></a><a name="Transparency"></a> <span data-ttu-id="eab5f-219">更改多边形、线条或点层的透明度</span><span class="sxs-lookup"><span data-stu-id="eab5f-219">To change the transparency of a polygon, line, or point layer</span></span>  
  
1.  <span data-ttu-id="eab5f-220">单击地图直到显示“地图”窗格。</span><span class="sxs-lookup"><span data-stu-id="eab5f-220">Click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="eab5f-221">右键单击该层，然后单击“层数据”  。</span><span class="sxs-lookup"><span data-stu-id="eab5f-221">Right-click the layer, and then click **Layer Data**.</span></span>  
  
3.  <span data-ttu-id="eab5f-222">单击 `Visibility`。</span><span class="sxs-lookup"><span data-stu-id="eab5f-222">Click `Visibility`.</span></span>  
  
4.  <span data-ttu-id="eab5f-223">在 **“透明度选项”** 中，键入表示百分比透明度的值，例如 **40**。</span><span class="sxs-lookup"><span data-stu-id="eab5f-223">In **Transparency options**, type a value that represents the percentage transparency, for example, **40**.</span></span> <span data-ttu-id="eab5f-224">零 (0) % 透明度表示该层不透明。</span><span class="sxs-lookup"><span data-stu-id="eab5f-224">Zero (0) % transparency means that the layer is opaque.</span></span> <span data-ttu-id="eab5f-225">100% 透明度意味着您在报表中将看不到该层。</span><span class="sxs-lookup"><span data-stu-id="eab5f-225">100% transparency means that you will not see the layer in the report.</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

##  <a name="to-change-the-transparency-of-a-tile-layer"></a><a name="TileTransparency"></a> <span data-ttu-id="eab5f-226">更改图块层的透明度</span><span class="sxs-lookup"><span data-stu-id="eab5f-226">To change the transparency of a tile layer</span></span>  
  
1.  <span data-ttu-id="eab5f-227">单击地图直到显示“地图”窗格。</span><span class="sxs-lookup"><span data-stu-id="eab5f-227">Click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="eab5f-228">右键单击该层，然后单击“图块属性”  。</span><span class="sxs-lookup"><span data-stu-id="eab5f-228">Right-click the layer, and then click **Tile Properties**.</span></span>  
  
3.  <span data-ttu-id="eab5f-229">单击 `Visibility`。</span><span class="sxs-lookup"><span data-stu-id="eab5f-229">Click `Visibility`.</span></span>  
  
4.  <span data-ttu-id="eab5f-230">在 **“透明度选项”** 中，键入表示百分比透明度的值，例如 **40**。</span><span class="sxs-lookup"><span data-stu-id="eab5f-230">In **Transparency options**, type a value that represents the percentage transparency, for example, **40**.</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

##  <a name="to-specify-a-secure-connection-for-a-tile-layer"></a><a name="Secure"></a> <span data-ttu-id="eab5f-231">为图块层指定安全连接</span><span class="sxs-lookup"><span data-stu-id="eab5f-231">To specify a secure connection for a tile layer</span></span>  
  
1.  <span data-ttu-id="eab5f-232">单击地图直到显示“地图”窗格。</span><span class="sxs-lookup"><span data-stu-id="eab5f-232">Click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="eab5f-233">在“地图”窗格中，单击该图块层以选中它。</span><span class="sxs-lookup"><span data-stu-id="eab5f-233">In the Map pane, click the tile layer to select it.</span></span> <span data-ttu-id="eab5f-234">“属性”窗格显示该图块层的属性。</span><span class="sxs-lookup"><span data-stu-id="eab5f-234">The Properties pane displays the tile layer properties.</span></span>  
  
3.  <span data-ttu-id="eab5f-235">在“属性”窗格中，将 UseSecureConnection 设置为 **True**。</span><span class="sxs-lookup"><span data-stu-id="eab5f-235">In the Properties pane, set UseSecureConnection to **True**.</span></span>  
  
 <span data-ttu-id="eab5f-236">Bing 地图 Web 服务的连接将使用 HTTP SSL（安全套接字层）服务来检索此层的 Bing 地图图块。</span><span class="sxs-lookup"><span data-stu-id="eab5f-236">The connection for the Bing Maps Web service will use the HTTP SSL (Secure Sockets Layer) service to retrieve Bing map tiles for this layer.</span></span>  

##  <a name="to-specify-the-language-for-tile-labels"></a><a name="Language"></a> <span data-ttu-id="eab5f-237">为图块标签指定语言</span><span class="sxs-lookup"><span data-stu-id="eab5f-237">To specify the language for tile labels</span></span>  
  
1.  <span data-ttu-id="eab5f-238">默认情况下，对于显示标签的图块样式，从报表生成器的默认区域设置确定语言。</span><span class="sxs-lookup"><span data-stu-id="eab5f-238">By default, for tile styles that display labels, the language is determined from the default locale for Report Builder.</span></span> <span data-ttu-id="eab5f-239">您可以按如下方式自定义图块标签的语言设置：</span><span class="sxs-lookup"><span data-stu-id="eab5f-239">You can customize the language setting for tile labels in the following ways.</span></span>  
  
    -   <span data-ttu-id="eab5f-240">在视区外单击地图以选中它。</span><span class="sxs-lookup"><span data-stu-id="eab5f-240">Click the map outside the viewport to select the map.</span></span> <span data-ttu-id="eab5f-241">在“属性”窗格中，对于 TileLanguage 属性，从下拉列表中选择一个区域性值。</span><span class="sxs-lookup"><span data-stu-id="eab5f-241">In the Properties pane, for the TileLanguage property, select a culture value from the drop-down list.</span></span>  
  
    -   <span data-ttu-id="eab5f-242">单击报表背景以选择该报表。</span><span class="sxs-lookup"><span data-stu-id="eab5f-242">Click the report background to select the report.</span></span> <span data-ttu-id="eab5f-243">在“属性”窗格中，对于 Language 属性，从下拉列表中选择一个区域性值。</span><span class="sxs-lookup"><span data-stu-id="eab5f-243">In the Properties pane, from for the Language property, select a culture value from the drop-down list.</span></span>  
  
     <span data-ttu-id="eab5f-244">设置图块标签语言的优先次序为：报表属性 Language、“报表生成器”的默认区域设置、地图属性 TileLanguage。</span><span class="sxs-lookup"><span data-stu-id="eab5f-244">The order of precedence for setting the tile label language is: report property Language, default locale for Report Builder, and map property TileLanguage.</span></span>  

##  <a name="to-conditionally-hide-a-layer-based-on-viewport-zoom-level"></a><a name="ConditionalHide"></a> <span data-ttu-id="eab5f-245">基于视区缩放级别有条件地隐藏层</span><span class="sxs-lookup"><span data-stu-id="eab5f-245">To conditionally hide a layer based on viewport zoom level</span></span>  
  
1.  <span data-ttu-id="eab5f-246">设置 `Visibility` 选项以控制地图层的显示。</span><span class="sxs-lookup"><span data-stu-id="eab5f-246">Set `Visibility` options to control the display for a map layer.</span></span>  
  
    -   <span data-ttu-id="eab5f-247">在“地图层”窗格中，右键单击某个层以便选择该层，然后在“地图层”工具栏上单击“属性”，以便打开“地图层属性”  。</span><span class="sxs-lookup"><span data-stu-id="eab5f-247">In the Map Layers pane, right-click a layer to select it, and on the Map Layers toolbar, click Properties to open **Map Layer Properties**.</span></span>  
  
    -   <span data-ttu-id="eab5f-248">单击 `Visibility`。</span><span class="sxs-lookup"><span data-stu-id="eab5f-248">Click `Visibility`.</span></span>  
  
    -   <span data-ttu-id="eab5f-249">在层可见性中，选择 **“基于缩放值显示或隐藏”** 。</span><span class="sxs-lookup"><span data-stu-id="eab5f-249">In Layer visibility, select **Show or hide based on zoom value**.</span></span>  
  
    -   <span data-ttu-id="eab5f-250">输入显示层时的最小和最大缩放值。</span><span class="sxs-lookup"><span data-stu-id="eab5f-250">Enter minimum and maximum zoom values for when display the layer.</span></span>  
  
    -   <span data-ttu-id="eab5f-251">可选。</span><span class="sxs-lookup"><span data-stu-id="eab5f-251">Optional.</span></span> <span data-ttu-id="eab5f-252">输入透明度值。</span><span class="sxs-lookup"><span data-stu-id="eab5f-252">Enter a value for transparency.</span></span>  
  
     <span data-ttu-id="eab5f-253">还可以有条件隐藏层。</span><span class="sxs-lookup"><span data-stu-id="eab5f-253">You can also conditionally hide the layer.</span></span> <span data-ttu-id="eab5f-254">有关详细信息，请参阅[隐藏项（报表生成器和 SSRS）](../report-builder/hide-an-item-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="eab5f-254">For more information, see [Hide an Item &#40;Report Builder and SSRS&#41;](../report-builder/hide-an-item-report-builder-and-ssrs.md).</span></span>  

## <a name="see-also"></a><span data-ttu-id="eab5f-255">另请参阅</span><span class="sxs-lookup"><span data-stu-id="eab5f-255">See Also</span></span>  
 <span data-ttu-id="eab5f-256">[地图（报表生成器和 SSRS）](maps-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="eab5f-256">[Maps &#40;Report Builder and SSRS&#41;](maps-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="eab5f-257">报表故障排除：地图报表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="eab5f-257">Troubleshoot Reports: Map Reports &#40;Report Builder and SSRS&#41;</span></span>](troubleshoot-reports-map-reports-report-builder-and-ssrs.md)  
