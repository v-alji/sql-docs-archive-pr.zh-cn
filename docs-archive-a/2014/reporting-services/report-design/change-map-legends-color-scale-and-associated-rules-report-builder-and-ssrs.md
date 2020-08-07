---
title: 更改地图图例、色阶和关联的规则 (报表生成器和 SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.shared.maprulesdistribution.f1
- "10512"
- "10539"
- "10533"
- sql12.rtp.rptdesigner.mappointlayerproperties.typerules.f1
- "10534"
- sql12.rtp.rptdesigner.maplegendproperties.general.f1
- sql12.rtp.rptdesigner.mapdistancescaleproperties.general.f1
- "10516"
- sql12.rtp.rptdesigner.mapcolorscaleproperties.labels.f1
- sql12.rtp.rptdesigner.maplegendtitleproperties.general.f1
- "10514"
- sql12.rtp.rptdesigner.shared.mapruleslegend.f1
- sql12.rtp.rptdesigner.mapcolorscaleproperties.general.f1
- sql12.rtp.rptdesigner.shared.embeddedlabels.f1
- "10513"
- sql12.rtp.rptdesigner.mappointlayerproperties.sizerules.f1
- sql12.rtp.rptdesigner.mapcolorscaletitleproperties.general.f1
- "10510"
- "10509"
- "10540"
- "10517"
ms.assetid: a1d691b2-c5ae-420f-af60-b7c54a7385a4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 17220c12e672ce49d3c5b1023f2a00db04e7613e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579997"
---
# <a name="change-map-legends-color-scale-and-associated-rules-report-builder-and-ssrs"></a><span data-ttu-id="c679a-102">更改地图图例、色阶和关联的规则（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="c679a-102">Change Map Legends, Color Scale, and Associated Rules (Report Builder and SSRS)</span></span>
  <span data-ttu-id="c679a-103">地图中可以包含地图图例、色阶和距离刻度。</span><span class="sxs-lookup"><span data-stu-id="c679a-103">A map can contain map legends, a color scale, and a distance scale.</span></span> <span data-ttu-id="c679a-104">地图的这些部分可帮助用户解释地图上的数据可视化。</span><span class="sxs-lookup"><span data-stu-id="c679a-104">These parts of a map help users interpret the data visualization on the map.</span></span>  
  
 <span data-ttu-id="c679a-105">图例包括地图的以下各部分：</span><span class="sxs-lookup"><span data-stu-id="c679a-105">Legends include the following parts of a map:</span></span>  
  
-   <span data-ttu-id="c679a-106">**地图图例** 显示的指导帮助解释可改变地图元素在地图层上的显示的分析数据。</span><span class="sxs-lookup"><span data-stu-id="c679a-106">**Map legend** Displays a guide to help interpret the analytical data that varies the display of a map elements on a map layer.</span></span> <span data-ttu-id="c679a-107">一个地图可以具有多个图例。</span><span class="sxs-lookup"><span data-stu-id="c679a-107">A map can have multiple legends.</span></span> <span data-ttu-id="c679a-108">对于每一地图层，您可以指定要使用的图例。</span><span class="sxs-lookup"><span data-stu-id="c679a-108">For each map layer, you A specify which legend to use.</span></span> <span data-ttu-id="c679a-109">一个图例可以为多个地图层提供指导。</span><span class="sxs-lookup"><span data-stu-id="c679a-109">A legend can provide a guide to more than one map layer.</span></span>  
  
-   <span data-ttu-id="c679a-110">**色阶** 显示的指导帮助解释地图上的颜色。</span><span class="sxs-lookup"><span data-stu-id="c679a-110">**Color scale** Displays a guide to help interpret colors on the map.</span></span> <span data-ttu-id="c679a-111">一个地图有一个色阶。</span><span class="sxs-lookup"><span data-stu-id="c679a-111">A map has one color scale.</span></span> <span data-ttu-id="c679a-112">多个层可以为色阶提供数据。</span><span class="sxs-lookup"><span data-stu-id="c679a-112">Multiple layers can provide the data for the color scale.</span></span>  
  
-   <span data-ttu-id="c679a-113">**距离刻度** 显示的指导帮助解释地图的刻度。</span><span class="sxs-lookup"><span data-stu-id="c679a-113">**Distance scale** Displays a guide to help interpret the scale of the map.</span></span> <span data-ttu-id="c679a-114">一个地图有一个距离刻度。</span><span class="sxs-lookup"><span data-stu-id="c679a-114">A map has one distance scale.</span></span> <span data-ttu-id="c679a-115">当前地图视区缩放值确定距离刻度。</span><span class="sxs-lookup"><span data-stu-id="c679a-115">The current map viewport zoom value determines the distance scale.</span></span>  
  
 <span data-ttu-id="c679a-116">![rs_MapElements](../media/rs-mapelements.gif "rs_MapElements")</span><span class="sxs-lookup"><span data-stu-id="c679a-116">![rs_MapElements](../media/rs-mapelements.gif "rs_MapElements")</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="to-change-the-position-of-a-legend-relative-to-the-viewport"></a><a name="Viewport"></a> <span data-ttu-id="c679a-117">更改图例相对于视区的位置</span><span class="sxs-lookup"><span data-stu-id="c679a-117">To change the position of a legend relative to the viewport</span></span>  
  
#### <a name="to-change-the-position-of-a-legend-relative-to-the-viewport"></a><span data-ttu-id="c679a-118">更改图例相对于视区的位置</span><span class="sxs-lookup"><span data-stu-id="c679a-118">To change the position of a legend relative to the viewport</span></span>  
  
1.  <span data-ttu-id="c679a-119">在设计视图中，右键单击图例，然后打开 " _\<report item->_ **属性**" 页。</span><span class="sxs-lookup"><span data-stu-id="c679a-119">In Design view, right-click the legend and open the _\<report item->_**Properties** page.</span></span>  
  
2.  <span data-ttu-id="c679a-120">在 **“位置”** 中，通过单击指定图例要在视区中显示的相对位置。</span><span class="sxs-lookup"><span data-stu-id="c679a-120">In **Position**, click the location that specifies where to display the legend relative to the viewport.</span></span>  
  
3.  <span data-ttu-id="c679a-121">若要在视区之外显示图例，请选择 "在\*\* \<report item> 视区外显示\*\*"。</span><span class="sxs-lookup"><span data-stu-id="c679a-121">To display the legend outside the viewport, select **Show \<report item> outside viewport**.</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
    > [!NOTE]  
    >  <span data-ttu-id="c679a-122">在预览中，仅当有来自与该图例相关的规则的结果时，才显示地图图例和色阶。</span><span class="sxs-lookup"><span data-stu-id="c679a-122">In preview, map legends and the color scale appear only when there are results from the rules related to that legend.</span></span> <span data-ttu-id="c679a-123">如果没有要显示的项，则图例不出现在呈现的报表中。</span><span class="sxs-lookup"><span data-stu-id="c679a-123">If there are no items to display, the legend does not appear in the rendered report.</span></span>  
  
  
  
##  <a name="to-change-the-layout-of-a-map-legend"></a><a name="MapLegend"></a> <span data-ttu-id="c679a-124">更改地图图例的布局</span><span class="sxs-lookup"><span data-stu-id="c679a-124">To change the layout of a map legend</span></span>  
  
#### <a name="to-change-the-layout-of-a-map-legend"></a><span data-ttu-id="c679a-125">更改地图图例的布局</span><span class="sxs-lookup"><span data-stu-id="c679a-125">To change the layout of a map legend</span></span>  
  
1.  <span data-ttu-id="c679a-126">在“设计”视图中，右键单击图例并打开“图例属性”  页。</span><span class="sxs-lookup"><span data-stu-id="c679a-126">In Design view, right-click the legend and open the **Legend Properties** page.</span></span>  
  
2.  <span data-ttu-id="c679a-127">在 **“图例布局”** 中，单击要用于图例的表布局。</span><span class="sxs-lookup"><span data-stu-id="c679a-127">In **Legend layout**, click the table layout that you want to use for the legend.</span></span> <span data-ttu-id="c679a-128">当您单击不同的选项时，设计图面上的布局将发生变化。</span><span class="sxs-lookup"><span data-stu-id="c679a-128">As you click different options, the layout on the design surface changes.</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
##  <a name="to-show-or-hide-a-map-legend-title"></a><a name="MapLegendTitle"></a> <span data-ttu-id="c679a-129">显示或隐藏地图图例标题</span><span class="sxs-lookup"><span data-stu-id="c679a-129">To show or hide a map legend title</span></span>  
  
#### <a name="to-show-or-hide-a-map-legend-title"></a><span data-ttu-id="c679a-130">显示或隐藏地图图例标题</span><span class="sxs-lookup"><span data-stu-id="c679a-130">To show or hide a map legend title</span></span>  
  
-   <span data-ttu-id="c679a-131">右键单击设计图面上的地图图例，然后单击“显示图例标题”  。</span><span class="sxs-lookup"><span data-stu-id="c679a-131">Right-click the map legend on the design surface, and then click **Show Legend Title**.</span></span>  
  
  
  
##  <a name="to-show-or-hide-a-color-scale-title"></a><a name="ColorScaleTitle"></a> <span data-ttu-id="c679a-132">显示或隐藏色阶标题</span><span class="sxs-lookup"><span data-stu-id="c679a-132">To show or hide a color scale title</span></span>  
  
#### <a name="to-show-or-hide-a-color-scale-title"></a><span data-ttu-id="c679a-133">显示或隐藏色阶标题</span><span class="sxs-lookup"><span data-stu-id="c679a-133">To show or hide a color scale title</span></span>  
  
-   <span data-ttu-id="c679a-134">右键单击设计图面上的色阶，然后单击“显示色阶标题”  。</span><span class="sxs-lookup"><span data-stu-id="c679a-134">Right-click the color scale on the design surface, and then click **Show Color Scale Title**.</span></span>  
  
  
  
##  <a name="to-move-items-out-of-the-first-legend"></a><a name="MoveItems"></a> <span data-ttu-id="c679a-135">将项目移出第一个图例</span><span class="sxs-lookup"><span data-stu-id="c679a-135">To move items out of the first legend</span></span>  
 <span data-ttu-id="c679a-136">根据需要创建任意数量的附加图例，然后更新每一地图层的规则，以指定要在其中显示规则结果的图例。</span><span class="sxs-lookup"><span data-stu-id="c679a-136">Create as many additional legends as you need and then update the rules for each map layer specify which legend to display the rule results in.</span></span>  
  
#### <a name="to-create-a-new-legend"></a><span data-ttu-id="c679a-137">创建新图例</span><span class="sxs-lookup"><span data-stu-id="c679a-137">To create a new legend</span></span>  
  
-   <span data-ttu-id="c679a-138">在“设计”视图中，在地图视区之外右键单击地图，然后单击“添加图例”  。</span><span class="sxs-lookup"><span data-stu-id="c679a-138">In Design view, right-click the map outside the map viewport, and then click **Add Legend**.</span></span>  
  
     <span data-ttu-id="c679a-139">一个新的图例将出现在地图上。</span><span class="sxs-lookup"><span data-stu-id="c679a-139">A new legend appears on the map.</span></span>  
  
#### <a name="to-display-rule-results-in-a-legend"></a><span data-ttu-id="c679a-140">在图例中显示规则结果</span><span class="sxs-lookup"><span data-stu-id="c679a-140">To display rule results in a legend</span></span>  
  
1.  <span data-ttu-id="c679a-141">在“设计”视图中，单击地图直到出现“地图”窗格。</span><span class="sxs-lookup"><span data-stu-id="c679a-141">In Design view, click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="c679a-142">右键单击具有所需数据的层，然后单击 " _\<map element type\>_ **颜色规则**"。</span><span class="sxs-lookup"><span data-stu-id="c679a-142">Right-click the layer that has the data that you want and then click _\<map element type\>_**Color Rule**.</span></span>  
  
3.  <span data-ttu-id="c679a-143">单击 **“图例”** 。</span><span class="sxs-lookup"><span data-stu-id="c679a-143">Click **Legend**.</span></span>  
  
4.  <span data-ttu-id="c679a-144">在“在此图例中显示”  下拉列表中，单击要将规则结果显示在其中的图例的名称。</span><span class="sxs-lookup"><span data-stu-id="c679a-144">In the **Show in this legend** drop-down list, click the name of the legend to display the rule results in.</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
##  <a name="to-vary-map-element-colors-based-on-a-template-style"></a><a name="TemplateStyle"></a> <span data-ttu-id="c679a-145">基于模板样式改变地图元素颜色</span><span class="sxs-lookup"><span data-stu-id="c679a-145">To vary map element colors based on a template style</span></span>  
  
#### <a name="to-vary-map-element-colors-based-on-a-template-style"></a><span data-ttu-id="c679a-146">基于模板样式改变地图元素颜色</span><span class="sxs-lookup"><span data-stu-id="c679a-146">To vary map element colors based on a template style</span></span>  
  
1.  <span data-ttu-id="c679a-147">在“设计”视图中，单击地图直到出现“地图”窗格。</span><span class="sxs-lookup"><span data-stu-id="c679a-147">In Design view, click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="c679a-148">右键单击具有所需数据的层，然后单击 " _\<map element type\>_ **颜色规则**"。</span><span class="sxs-lookup"><span data-stu-id="c679a-148">Right-click the layer that has the data that you want and then click _\<map element type\>_**Color Rule**.</span></span>  
  
3.  <span data-ttu-id="c679a-149">单击 **“应用模板样式”** 。</span><span class="sxs-lookup"><span data-stu-id="c679a-149">Click **Apply template style**.</span></span>  
  
     <span data-ttu-id="c679a-150">模板样式指定字体、边框样式和调色板。</span><span class="sxs-lookup"><span data-stu-id="c679a-150">A template style specifies font, border style, and color palette.</span></span> <span data-ttu-id="c679a-151">对于在“地图向导”或“地图层向导”中指定的主题，从调色板中为每个地图元素分配一种不同的颜色。</span><span class="sxs-lookup"><span data-stu-id="c679a-151">Each map element is assigned a different color from the color palette for the theme that was specified in the Map Wizard or Map Layer Wizard.</span></span> <span data-ttu-id="c679a-152">这是适用于不具备关联分析数据的层的唯一选项。</span><span class="sxs-lookup"><span data-stu-id="c679a-152">This is the only option that applies to layers that do not have associated analytical data.</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
##  <a name="to-vary-map-element-colors-based-on-color-palette"></a><a name="ColorPalette"></a> <span data-ttu-id="c679a-153">基于调色板改变地图元素颜色</span><span class="sxs-lookup"><span data-stu-id="c679a-153">To vary map element colors based on color palette</span></span>  
  
#### <a name="to-vary-map-element-colors-based-on-color-palette"></a><span data-ttu-id="c679a-154">基于调色板改变地图元素颜色</span><span class="sxs-lookup"><span data-stu-id="c679a-154">To vary map element colors based on color palette</span></span>  
  
1.  <span data-ttu-id="c679a-155">在“设计”视图中，单击地图直到出现“地图”窗格。</span><span class="sxs-lookup"><span data-stu-id="c679a-155">In Design view, click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="c679a-156">右键单击具有所需数据的层，然后单击 " _\<map element type\>_ **颜色规则**"。</span><span class="sxs-lookup"><span data-stu-id="c679a-156">Right-click the layer that has the data that you want, and then click _\<map element type\>_**Color Rule**.</span></span>  
  
3.  <span data-ttu-id="c679a-157">单击 **“使用调色板实现数据的可视化效果”** 。</span><span class="sxs-lookup"><span data-stu-id="c679a-157">Click **Visualize data by using color palette**.</span></span>  
  
     <span data-ttu-id="c679a-158">此选项使用内置调色板或您指定的自定义调色板。</span><span class="sxs-lookup"><span data-stu-id="c679a-158">This option uses a built-in or custom palette that you specify.</span></span> <span data-ttu-id="c679a-159">根据相关的分析数据，将从调色板中为每个地图元素分配不同的颜色或颜色阴影。</span><span class="sxs-lookup"><span data-stu-id="c679a-159">Based on related analytical data, each map element is assigned a different color or shade of color from the palette.</span></span>  
  
4.  <span data-ttu-id="c679a-160">在 **“数据字段”** 中，键入某个字段的名称，该字段包含要通过颜色实现可视化效果的分析数据。</span><span class="sxs-lookup"><span data-stu-id="c679a-160">In **Data field**, type the name of the field that contains the analytical data that you want to visualize by color.</span></span>  
  
5.  <span data-ttu-id="c679a-161">在“调色板”中  ，从下拉列表选择要使用的调色板的名称。</span><span class="sxs-lookup"><span data-stu-id="c679a-161">In **Palette**, from the drop-down list, select the name of the palette to use.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
##  <a name="to-vary-map-element-colors-based-on-color-ranges"></a><a name="ColorRanges"></a> <span data-ttu-id="c679a-162">基于颜色范围改变地图元素颜色</span><span class="sxs-lookup"><span data-stu-id="c679a-162">To vary map element colors based on color ranges</span></span>  
  
#### <a name="to-vary-map-element-colors-based-on-color-ranges"></a><span data-ttu-id="c679a-163">基于颜色范围改变地图元素颜色</span><span class="sxs-lookup"><span data-stu-id="c679a-163">To vary map element colors based on color ranges</span></span>  
  
1.  <span data-ttu-id="c679a-164">在“设计”视图中，单击地图直到出现“地图”窗格。</span><span class="sxs-lookup"><span data-stu-id="c679a-164">In Design view, click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="c679a-165">右键单击具有所需数据的层，然后单击 " _\<map element type\>_ **颜色规则**"。</span><span class="sxs-lookup"><span data-stu-id="c679a-165">Right-click the layer that has the data that you want, and then click _\<map element type\>_**Color Rule**.</span></span>  
  
3.  <span data-ttu-id="c679a-166">单击 **“使用颜色范围实现数据的可视化效果”** 。</span><span class="sxs-lookup"><span data-stu-id="c679a-166">Click **Visualize data by using color ranges**.</span></span>  
  
     <span data-ttu-id="c679a-167">此选项结合您在此页上指定的开始颜色、中间颜色和结束颜色以及您在 **“分布”** 页上指定的选项，将相关的分析数据划分到各个范围。</span><span class="sxs-lookup"><span data-stu-id="c679a-167">This option, combined with the start, middle, and end colors that you specify on this page and the options that you specify on the **Distribution** page, divide the related analytical data into ranges.</span></span> <span data-ttu-id="c679a-168">报表处理器将根据每个地图元素的关联数据及其归入的范围，向其分配适当的颜色。</span><span class="sxs-lookup"><span data-stu-id="c679a-168">The report processor assigns the appropriate color to each map element based on the its associated data and the range that it falls into.</span></span>  
  
4.  <span data-ttu-id="c679a-169">在 **“数据字段”** 中，键入某个字段的名称，该字段包含要通过颜色实现可视化效果的分析数据。</span><span class="sxs-lookup"><span data-stu-id="c679a-169">In **Data field**, type the name of the field that contains the analytical data that you want to visualize by color.</span></span>  
  
5.  <span data-ttu-id="c679a-170">在 **“开始颜色”** 中，指定要用于最低范围的颜色。</span><span class="sxs-lookup"><span data-stu-id="c679a-170">In **Start color**, specify the color to use for the lowest range.</span></span>  
  
6.  <span data-ttu-id="c679a-171">在 **“中间颜色”** 中，指定要用于中间范围的颜色。</span><span class="sxs-lookup"><span data-stu-id="c679a-171">In **Middle color**, specify the color to use for the middle range.</span></span>  
  
7.  <span data-ttu-id="c679a-172">在 **“结束颜色”** 中，指定要用于最高范围的颜色。</span><span class="sxs-lookup"><span data-stu-id="c679a-172">In **End color**, specify the color to use for the highest range.</span></span>  
  
8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
##  <a name="to-vary-map-element-colors-based-on-custom-colors"></a><a name="CustomColors"></a> <span data-ttu-id="c679a-173">基于自定义颜色改变地图元素颜色</span><span class="sxs-lookup"><span data-stu-id="c679a-173">To vary map element colors based on custom colors</span></span>  
  
#### <a name="to-vary-map-element-colors-based-on-custom-colors"></a><span data-ttu-id="c679a-174">基于自定义颜色改变地图元素颜色</span><span class="sxs-lookup"><span data-stu-id="c679a-174">To vary map element colors based on custom colors</span></span>  
  
1.  <span data-ttu-id="c679a-175">在“设计”视图中，单击地图直到出现“地图”窗格。</span><span class="sxs-lookup"><span data-stu-id="c679a-175">In Design view, click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="c679a-176">右键单击具有所需数据的层，然后单击 " _\<map element type\>_ **颜色规则**"。</span><span class="sxs-lookup"><span data-stu-id="c679a-176">Right-click the layer that has the data that you want, and then click _\<map element type\>_**Color Rule**.</span></span>  
  
3.  <span data-ttu-id="c679a-177">单击 **“使用自定义颜色实现数据的可视化效果”** 。</span><span class="sxs-lookup"><span data-stu-id="c679a-177">Click **Visualize data by using custom colors**.</span></span>  
  
     <span data-ttu-id="c679a-178">此选项使用您指定的颜色列表。</span><span class="sxs-lookup"><span data-stu-id="c679a-178">This option uses the list of colors that you specify.</span></span> <span data-ttu-id="c679a-179">根据相关的分析数据，将从该列表中为每个地图元素分配一种颜色。</span><span class="sxs-lookup"><span data-stu-id="c679a-179">Based on related analytical data, each map element is assigned a color from the list.</span></span> <span data-ttu-id="c679a-180">如果地图元素数多于颜色数，则不分配颜色。</span><span class="sxs-lookup"><span data-stu-id="c679a-180">If there are more map elements than colors, no color is assigned.</span></span>  
  
4.  <span data-ttu-id="c679a-181">在 **“数据字段”** 中，键入某个字段的名称，该字段包含要通过颜色实现可视化效果的分析数据。</span><span class="sxs-lookup"><span data-stu-id="c679a-181">In **Data field**, type the name of the field that contains the analytical data that you want to visualize by color.</span></span>  
  
5.  <span data-ttu-id="c679a-182">在 **“自定义颜色”** 中，单击 **“添加”** 以指定每种自定义颜色。</span><span class="sxs-lookup"><span data-stu-id="c679a-182">In **Custom colors**, click **Add** to specify each custom color.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
##  <a name="to-set-distribution-options-for-a-legend"></a><a name="DistributionOptions"></a> <span data-ttu-id="c679a-183">为图例设置分布选项</span><span class="sxs-lookup"><span data-stu-id="c679a-183">To set distribution options for a legend</span></span>  
  
#### <a name="to-set-distribution-options-for-a-legend"></a><span data-ttu-id="c679a-184">为图例设置分布选项</span><span class="sxs-lookup"><span data-stu-id="c679a-184">To set distribution options for a legend</span></span>  
  
1.  <span data-ttu-id="c679a-185">在“设计”视图中，单击地图直到出现“地图”窗格。</span><span class="sxs-lookup"><span data-stu-id="c679a-185">In Design view, click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="c679a-186">右键单击具有所需数据的层，然后单击 " _\<map element type\>_ **颜色规则**"。</span><span class="sxs-lookup"><span data-stu-id="c679a-186">Right-click the layer that has the data that you want, and then click _\<map element type\>_**Color Rule**.</span></span>  
  
3.  <span data-ttu-id="c679a-187">选择 "**使用数据实现数据的可视化效果**" \<rule type\> 选项。</span><span class="sxs-lookup"><span data-stu-id="c679a-187">Select the **Visualize data by using** \<rule type\> option.</span></span> <span data-ttu-id="c679a-188">若要使用分布选项，必须根据与层关联的分析数据，在 **“分布”** 页上创建范围。</span><span class="sxs-lookup"><span data-stu-id="c679a-188">To use distribution options, you must create ranges on the **Distribution** page based on analytical data that is associated with the layer.</span></span>  
  
4.  <span data-ttu-id="c679a-189">单击 **“分布”** 。</span><span class="sxs-lookup"><span data-stu-id="c679a-189">Click **Distribution**.</span></span>  
  
5.  <span data-ttu-id="c679a-190">请选择以下分布类型之一：</span><span class="sxs-lookup"><span data-stu-id="c679a-190">Select one of the following distribution types:</span></span>  
  
    -   <span data-ttu-id="c679a-191">**相等间隔**：</span><span class="sxs-lookup"><span data-stu-id="c679a-191">**EqualInterval**.</span></span> <span data-ttu-id="c679a-192">指定将数据划分为相等范围间隔的范围。</span><span class="sxs-lookup"><span data-stu-id="c679a-192">Specifies ranges that divide the data into equal range intervals.</span></span>  
  
    -   <span data-ttu-id="c679a-193">**相等分布**：</span><span class="sxs-lookup"><span data-stu-id="c679a-193">**EqualDistribution**.</span></span> <span data-ttu-id="c679a-194">指定用于划分数据以使每个范围具有相同项数的范围。</span><span class="sxs-lookup"><span data-stu-id="c679a-194">Specifies ranges that divide that data so that each range has an equal number of items.</span></span>  
  
    -   <span data-ttu-id="c679a-195">**最佳**：</span><span class="sxs-lookup"><span data-stu-id="c679a-195">**Optimal**.</span></span> <span data-ttu-id="c679a-196">指定自动调整分布以创建平衡子范围的范围。</span><span class="sxs-lookup"><span data-stu-id="c679a-196">Specifies ranges that automatically adjust distribution to create balanced subranges.</span></span>  
  
    -   <span data-ttu-id="c679a-197">**自定义**：</span><span class="sxs-lookup"><span data-stu-id="c679a-197">**Custom**.</span></span> <span data-ttu-id="c679a-198">指定您自己的范围数以控制值的分布。</span><span class="sxs-lookup"><span data-stu-id="c679a-198">Specify your own number of ranges to control the distribution of values.</span></span>  
  
     <span data-ttu-id="c679a-199">有关分布选项的详细信息，请参阅[按规则和分析数据更改多边形、线条和点的显示方式（报表生成器和 SSRS）](vary-polygon-line-and-point-display-by-rules-and-analytical-data.md)。</span><span class="sxs-lookup"><span data-stu-id="c679a-199">For more information about distribution options, see [Vary Polygon, Line, and Point Display by Rules and Analytical Data &#40;Report Builder and SSRS&#41;](vary-polygon-line-and-point-display-by-rules-and-analytical-data.md).</span></span>  
  
6.  <span data-ttu-id="c679a-200">在 **“子范围的数目”** 中，键入要使用的子范围数。</span><span class="sxs-lookup"><span data-stu-id="c679a-200">In **Number of subranges**, type the number of subranges to use.</span></span> <span data-ttu-id="c679a-201">当分布类型为 **“最佳”** 时，将自动计算子范围的数量。</span><span class="sxs-lookup"><span data-stu-id="c679a-201">When the distribution type is **Optimal**, the number of subranges is automatically calculated.</span></span>  
  
7.  <span data-ttu-id="c679a-202">在 **“范围开始”** 中，键入最小范围值。</span><span class="sxs-lookup"><span data-stu-id="c679a-202">In **Range start**, type a minimum range value.</span></span> <span data-ttu-id="c679a-203">所有小于此数字的值均与范围最小值相同。</span><span class="sxs-lookup"><span data-stu-id="c679a-203">All values less than this number are the same as the range minimum.</span></span>  
  
8.  <span data-ttu-id="c679a-204">在 **“范围结束”** 中，键入最大范围值。</span><span class="sxs-lookup"><span data-stu-id="c679a-204">In **Range end**, type a maximum range value.</span></span> <span data-ttu-id="c679a-205">所有大于此数字的值均与范围最大值相同。</span><span class="sxs-lookup"><span data-stu-id="c679a-205">All values larger than this number are the same as the range maximum.</span></span>  
  
9. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
##  <a name="to-change-the-contents-of-a-rule-legend"></a><a name="RuleLegend"></a> <span data-ttu-id="c679a-206">更改规则图例的内容</span><span class="sxs-lookup"><span data-stu-id="c679a-206">To change the contents of a rule legend</span></span>  
  
#### <a name="to-change-the-contents-of-a-color-size-width-or-marker-type-legend"></a><span data-ttu-id="c679a-207">更改颜色、大小、宽度或标记类型图例的内容</span><span class="sxs-lookup"><span data-stu-id="c679a-207">To change the contents of a color, size, width, or marker type legend</span></span>  
  
1.  <span data-ttu-id="c679a-208">在“设计”视图中，单击地图直到出现“地图”窗格。</span><span class="sxs-lookup"><span data-stu-id="c679a-208">In Design view, click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="c679a-209">右键单击具有所需数据的层，然后单击 " _\<map element type\>_ **规则**"。</span><span class="sxs-lookup"><span data-stu-id="c679a-209">Right-click the layer that has the data that you want, and then click _\<map element type\>_**Rule**.</span></span>  
  
3.  <span data-ttu-id="c679a-210">验证是否选择了 "**使用实现数据的可视化效果**" \<*rule type*> 。</span><span class="sxs-lookup"><span data-stu-id="c679a-210">Verify that **Visualize data by using** \<*rule type*> is selected.</span></span>  
  
4.  <span data-ttu-id="c679a-211">在 **“数据字段”** 中，验证选择了您要该层上实现可视化的分析数据。</span><span class="sxs-lookup"><span data-stu-id="c679a-211">In **Data field**, verify that the analytical data that you are visualizing on the layer is selected.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c679a-212">如果下拉列表中没有显示任何字段，则右键单击该层，然后单击“层数据”以打开“地图层数据属性”对话框的“分析数据”页，并验证你已为此层指定了分析数据  。</span><span class="sxs-lookup"><span data-stu-id="c679a-212">If no fields appear in the drop-down list, right-click the layer, and then click **Layer Data** to open the Map Layer Data Properties Dialog Box, Analytical Data page and verify that you have specified analytical data for this layer.</span></span>  
  
5.  <span data-ttu-id="c679a-213">单击 **“图例”** 。</span><span class="sxs-lookup"><span data-stu-id="c679a-213">Click **Legend**.</span></span>  
  
6.  <span data-ttu-id="c679a-214">在 **“在此图例中显示”** 中，选择要用于显示规则结果的地图图例。</span><span class="sxs-lookup"><span data-stu-id="c679a-214">In **Show in this legend**, select the map legend to use to display the rule results.</span></span>  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
##  <a name="to-change-the-contents-of-the-color-scale"></a><a name="ColorScale"></a> <span data-ttu-id="c679a-215">更改色阶的内容</span><span class="sxs-lookup"><span data-stu-id="c679a-215">To change the contents of the color scale</span></span>  
  
#### <a name="to-change-the-contents-of-the-color-scale-or-a-color-legend"></a><span data-ttu-id="c679a-216">更改色阶或颜色图例的内容</span><span class="sxs-lookup"><span data-stu-id="c679a-216">To change the contents of the color scale or a color legend</span></span>  
  
1.  <span data-ttu-id="c679a-217">在“设计”视图中，单击地图直到出现“地图”窗格。</span><span class="sxs-lookup"><span data-stu-id="c679a-217">In Design view, click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="c679a-218">右键单击具有所需数据的层，然后单击 " _\<map element type\>_ **颜色规则**"。</span><span class="sxs-lookup"><span data-stu-id="c679a-218">Right-click the layer that has the data that you want, and then click _\<map element type\>_**Color Rule**.</span></span>  
  
3.  <span data-ttu-id="c679a-219">选择要使用的颜色规则选项。</span><span class="sxs-lookup"><span data-stu-id="c679a-219">Select the color rule option to use.</span></span> <span data-ttu-id="c679a-220">若要在地图图例或色阶中显示项，您必须使用选项选择一个**可视化数据** \<rule type> 。</span><span class="sxs-lookup"><span data-stu-id="c679a-220">To display items in a map legend or color scale, you must select one of the **Visualize data by using** \<rule type> options.</span></span>  
  
4.  <span data-ttu-id="c679a-221">在 **“数据字段”** 中，验证选择了您要该层上实现可视化的分析数据。</span><span class="sxs-lookup"><span data-stu-id="c679a-221">In **Data field**, verify that the analytical data that you are visualizing on the layer is selected.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c679a-222">如果下拉列表中没有显示任何字段，则右键单击该层，然后单击“层数据”以打开“地图层数据属性”对话框的“分析数据”页，并验证你已为此层指定了分析数据  。</span><span class="sxs-lookup"><span data-stu-id="c679a-222">If no fields appear in the drop-down list, right-click the layer, and then click **Layer Data** to open the Map Layer Data Properties Dialog Box, Analytical Data page and verify that you have specified analytical data for this layer.</span></span>  
  
5.  <span data-ttu-id="c679a-223">单击 **“图例”** 。</span><span class="sxs-lookup"><span data-stu-id="c679a-223">Click **Legend**.</span></span>  
  
6.  <span data-ttu-id="c679a-224">在 **“色阶选项”** 中，选择 **“在色阶中显示”** 以便在色阶中显示规则结果。</span><span class="sxs-lookup"><span data-stu-id="c679a-224">In **Color scale options**, select **Show in color scale** to display the rule results in the color scale.</span></span> <span data-ttu-id="c679a-225">您可以为多个颜色规则指定此选项。</span><span class="sxs-lookup"><span data-stu-id="c679a-225">You can specify this option for more than one color rule.</span></span>  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
##  <a name="to-remove-all-items-from-a-legend"></a><a name="HideItems"></a> <span data-ttu-id="c679a-226">从图例中删除所有项目</span><span class="sxs-lookup"><span data-stu-id="c679a-226">To remove all items from a legend</span></span>  
  
#### <a name="to-hide-items-based-on-a-rule"></a><span data-ttu-id="c679a-227">基于规则隐藏项目</span><span class="sxs-lookup"><span data-stu-id="c679a-227">To hide items based on a rule</span></span>  
  
1.  <span data-ttu-id="c679a-228">在“设计”视图中，单击地图直到出现“地图”窗格。</span><span class="sxs-lookup"><span data-stu-id="c679a-228">In Design view, click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="c679a-229">右键单击具有所需数据的层，然后单击 " _\<map element type\>_ **规则**"。</span><span class="sxs-lookup"><span data-stu-id="c679a-229">Right-click the layer that has the data that you want, and then click _\<map element type\>_**Rule**.</span></span>  
  
3.  <span data-ttu-id="c679a-230">单击 **“图例”** 。</span><span class="sxs-lookup"><span data-stu-id="c679a-230">Click **Legend**.</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
##  <a name="to-change-the-format-of-content-in-a-legend"></a><a name="ChangeFormatItems"></a> <span data-ttu-id="c679a-231">更改图例中内容的格式</span><span class="sxs-lookup"><span data-stu-id="c679a-231">To change the format of content in a legend</span></span>  
 <span data-ttu-id="c679a-232">为与地图图例关联的规则设置图例选项。</span><span class="sxs-lookup"><span data-stu-id="c679a-232">Set legend options for the rule that is associated with the map legend.</span></span>  
  
#### <a name="to-change-the-format-of-content-in-a-legend"></a><span data-ttu-id="c679a-233">更改图例中内容的格式</span><span class="sxs-lookup"><span data-stu-id="c679a-233">To change the format of content in a legend</span></span>  
  
1.  <span data-ttu-id="c679a-234">在“设计”视图中，单击地图直到出现“地图”窗格。</span><span class="sxs-lookup"><span data-stu-id="c679a-234">In Design view, click the map until the Map pane appears.</span></span>  
  
2.  <span data-ttu-id="c679a-235">右键单击具有所需数据的层，然后单击 " _\<map element type\>_ **规则**"。</span><span class="sxs-lookup"><span data-stu-id="c679a-235">Right-click the layer that has the data that you want, and then click _\<map element type\>_**Rule**.</span></span>  
  
3.  <span data-ttu-id="c679a-236">单击 **“图例”** 。</span><span class="sxs-lookup"><span data-stu-id="c679a-236">Click **Legend**.</span></span>  
  
4.  <span data-ttu-id="c679a-237">**“图例文本”** 显示指定要在图例中显示的数据的关键字。</span><span class="sxs-lookup"><span data-stu-id="c679a-237">**Legend text** displays keywords that specify which data appears in the legend.</span></span> <span data-ttu-id="c679a-238">使用地图关键字和自定义格式可帮助控制图例文本的格式。</span><span class="sxs-lookup"><span data-stu-id="c679a-238">Use map keywords and custom formats to help control the format of legend text.</span></span> <span data-ttu-id="c679a-239">例如，#FROMVALUE {C2} 指定一个具有两个小数位的货币格式。</span><span class="sxs-lookup"><span data-stu-id="c679a-239">For example, #FROMVALUE {C2} specifies a currency format with two decimal places.</span></span> <span data-ttu-id="c679a-240">有关详细信息，请参阅 [按规则和分析数据更改多边形、线条和点的显示方式（报表生成器和 SSRS）](vary-polygon-line-and-point-display-by-rules-and-analytical-data.md)。</span><span class="sxs-lookup"><span data-stu-id="c679a-240">For more information, see [Vary Polygon, Line, and Point Display by Rules and Analytical Data &#40;Report Builder and SSRS&#41;](vary-polygon-line-and-point-display-by-rules-and-analytical-data.md).</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
  
## <a name="see-also"></a><span data-ttu-id="c679a-241">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c679a-241">See Also</span></span>  
 <span data-ttu-id="c679a-242">[地图（报表生成器和 SSRS）](maps-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c679a-242">[Maps &#40;Report Builder and SSRS&#41;](maps-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c679a-243">[添加、更改或删除地图或地图层（报表生成器和 SSRS）](add-change-or-delete-a-map-or-map-layer-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c679a-243">[Add, Change, or Delete a Map or Map Layer &#40;Report Builder and SSRS&#41;](add-change-or-delete-a-map-or-map-layer-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c679a-244">[自定义地图或地图层的数据和显示（报表生成器和 SSRS）](customize-the-data-and-display-of-a-map-or-map-layer-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c679a-244">[Customize the Data and Display of a Map or Map Layer &#40;Report Builder and SSRS&#41;](customize-the-data-and-display-of-a-map-or-map-layer-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c679a-245">[报表故障排除：地图报表（报表生成器和 SSRS）](troubleshoot-reports-map-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c679a-245">[Troubleshoot Reports: Map Reports &#40;Report Builder and SSRS&#41;](troubleshoot-reports-map-reports-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="c679a-246">地图向导和地图层向导（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="c679a-246">Map Wizard and Map Layer Wizard &#40;Report Builder and SSRS&#41;</span></span>](map-wizard-and-map-layer-wizard-report-builder-and-ssrs.md)  
  
  
