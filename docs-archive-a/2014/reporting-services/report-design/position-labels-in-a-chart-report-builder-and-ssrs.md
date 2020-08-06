---
title: 图表中的位置标签（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5db74e0b-8be8-4b47-b386-faab56dffa9b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e90cbf04e0282454658e6324f0ba6600a99cb718
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682674"
---
# <a name="position-labels-in-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="bca92-102">图表中的位置标签（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="bca92-102">Position Labels in a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="bca92-103">由于每种图表类型都具有不同的形状，因此应将数据点标签放在最佳位置上以免对图表产生干扰。</span><span class="sxs-lookup"><span data-stu-id="bca92-103">Because each chart type has a different shape, data point labels are placed in an optimal location so as not to interfere on the chart.</span></span> <span data-ttu-id="bca92-104">标签的默认位置因图表类型而异：</span><span class="sxs-lookup"><span data-stu-id="bca92-104">The default position of the labels depends varies with the chart type:</span></span>  
  
-   <span data-ttu-id="bca92-105">在堆积图中，标签只能位于序列内部。</span><span class="sxs-lookup"><span data-stu-id="bca92-105">On stacked charts, labels can only be positioned inside the series.</span></span>  
  
-   <span data-ttu-id="bca92-106">在漏斗图或棱锥图中，标签位于列的外部。</span><span class="sxs-lookup"><span data-stu-id="bca92-106">On funnel or pyramid charts, labels are placed on the outside in a column.</span></span>  
  
-   <span data-ttu-id="bca92-107">在饼图中，标签位于饼图的各切片内部。</span><span class="sxs-lookup"><span data-stu-id="bca92-107">On pie charts, labels are placed inside the individual slices on a pie chart.</span></span>  
  
-   <span data-ttu-id="bca92-108">在条形图中，标签位于表示数据点的图条的外部。</span><span class="sxs-lookup"><span data-stu-id="bca92-108">On bar charts, labels are placed outside of the bars that represent data points.</span></span>  
  
-   <span data-ttu-id="bca92-109">在极坐标图中，标签位于表示数据点的圆形区域的外部。</span><span class="sxs-lookup"><span data-stu-id="bca92-109">On polar charts, labels are placed outside of the circular area that represents data points.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-the-position-of-point-labels-in-a-pie-chart"></a><span data-ttu-id="bca92-110">更改点标签在饼图中的位置</span><span class="sxs-lookup"><span data-stu-id="bca92-110">To change the position of point labels in a Pie chart</span></span>  
  
1.  <span data-ttu-id="bca92-111">创建一个饼图。</span><span class="sxs-lookup"><span data-stu-id="bca92-111">Create a pie chart.</span></span>  
  
2.  <span data-ttu-id="bca92-112">在设计图面上，右键单击该图表并选择“显示数据标签”  。</span><span class="sxs-lookup"><span data-stu-id="bca92-112">On the design surface, right-click the chart and select **Show Data Labels**.</span></span>  
  
3.  <span data-ttu-id="bca92-113">打开“属性”窗格。</span><span class="sxs-lookup"><span data-stu-id="bca92-113">Open the Properties pane.</span></span> <span data-ttu-id="bca92-114">在 **“视图”** 选项卡上，单击 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="bca92-114">On the **View** tab, click **Properties**.</span></span>  
  
4.  <span data-ttu-id="bca92-115">在设计图面上，单击该图表。</span><span class="sxs-lookup"><span data-stu-id="bca92-115">On the design surface, click the chart.</span></span> <span data-ttu-id="bca92-116">该图表的属性将显示在“属性”窗格中。</span><span class="sxs-lookup"><span data-stu-id="bca92-116">The properties for the chart are displayed in the Properties pane.</span></span>  
  
5.  <span data-ttu-id="bca92-117">在 **“常规”** 部分，展开 **CustomAttributes** 节点。</span><span class="sxs-lookup"><span data-stu-id="bca92-117">In the **General** section, expand the **CustomAttributes** node.</span></span> <span data-ttu-id="bca92-118">此时将显示该饼图的属性列表。</span><span class="sxs-lookup"><span data-stu-id="bca92-118">A list of attributes for the pie chart is displayed.</span></span>  
  
6.  <span data-ttu-id="bca92-119">为 PieLabelStyle 属性选择一个值。</span><span class="sxs-lookup"><span data-stu-id="bca92-119">Select a value for the PieLabelStyle property.</span></span>  
  
### <a name="to-change-the-position-of-point-labels-in-a-funnel-or-pyramid-chart"></a><span data-ttu-id="bca92-120">更改点标签在漏斗图或棱锥图中的位置</span><span class="sxs-lookup"><span data-stu-id="bca92-120">To change the position of point labels in a Funnel or Pyramid chart</span></span>  
  
1.  <span data-ttu-id="bca92-121">创建一个漏斗图或棱锥图。</span><span class="sxs-lookup"><span data-stu-id="bca92-121">Create a funnel or pyramid chart.</span></span>  
  
2.  <span data-ttu-id="bca92-122">在设计图面上，右键单击该图表并选择“显示数据标签”  。</span><span class="sxs-lookup"><span data-stu-id="bca92-122">On the design surface, right-click the chart and select **Show Data Labels**.</span></span>  
  
3.  <span data-ttu-id="bca92-123">打开“属性”窗格。</span><span class="sxs-lookup"><span data-stu-id="bca92-123">Open the Properties pane.</span></span> <span data-ttu-id="bca92-124">在 **“视图”** 选项卡上，单击 **“属性”**</span><span class="sxs-lookup"><span data-stu-id="bca92-124">On the **View** tab, click **Properties**</span></span>  
  
4.  <span data-ttu-id="bca92-125">在设计图面上，单击该图表。</span><span class="sxs-lookup"><span data-stu-id="bca92-125">On the design surface, click the chart.</span></span> <span data-ttu-id="bca92-126">该图表的属性将显示在“属性”窗格中。</span><span class="sxs-lookup"><span data-stu-id="bca92-126">The properties for the chart are displayed in the Properties pane.</span></span>  
  
5.  <span data-ttu-id="bca92-127">在 **“常规”** 部分，展开 **CustomAttributes** 节点。</span><span class="sxs-lookup"><span data-stu-id="bca92-127">In the **General** section, expand the **CustomAttributes** node.</span></span> <span data-ttu-id="bca92-128">此时将显示该漏斗图的属性列表。</span><span class="sxs-lookup"><span data-stu-id="bca92-128">A list of attributes for the funnel chart is displayed.</span></span>  
  
6.  <span data-ttu-id="bca92-129">对于漏斗图，请为 FunnelLabelStyle 属性选择一个值。</span><span class="sxs-lookup"><span data-stu-id="bca92-129">For a funnel chart, select a value for the FunnelLabelStyle property.</span></span> <span data-ttu-id="bca92-130">对于凌锥图，请为 PyramidLabelStyle 属性选择一个值。</span><span class="sxs-lookup"><span data-stu-id="bca92-130">For a pyramid chart, select a value for the PyramidLabelStyle property.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="bca92-131">当此属性设置为 `OutsideInColumn` 值时，标签会绘制在垂直图柱中。</span><span class="sxs-lookup"><span data-stu-id="bca92-131">When this property is set to a value `OutsideInColumn`, the labels are drawn in a vertical column.</span></span> <span data-ttu-id="bca92-132">列的位置无法更改。</span><span class="sxs-lookup"><span data-stu-id="bca92-132">There is no way to change the position of the column.</span></span>  
  
### <a name="to-change-the-position-of-point-labels-in-a-bar-chart"></a><span data-ttu-id="bca92-133">更改点标签在条形图中的位置</span><span class="sxs-lookup"><span data-stu-id="bca92-133">To change the position of point labels in a Bar chart</span></span>  
  
1.  <span data-ttu-id="bca92-134">创建一个条形图。</span><span class="sxs-lookup"><span data-stu-id="bca92-134">Create a bar chart.</span></span>  
  
2.  <span data-ttu-id="bca92-135">在设计图面上，右键单击该图表并选择“显示数据标签”  。</span><span class="sxs-lookup"><span data-stu-id="bca92-135">On the design surface, right-click the chart and select **Show Data Labels**.</span></span>  
  
3.  <span data-ttu-id="bca92-136">打开“属性”窗格。</span><span class="sxs-lookup"><span data-stu-id="bca92-136">Open the Properties pane.</span></span> <span data-ttu-id="bca92-137">在 **“视图”** 选项卡上，单击 **“属性”**</span><span class="sxs-lookup"><span data-stu-id="bca92-137">On the **View** tab, click **Properties**</span></span>  
  
4.  <span data-ttu-id="bca92-138">在设计图面上，单击该图表。</span><span class="sxs-lookup"><span data-stu-id="bca92-138">On the design surface, click the chart.</span></span> <span data-ttu-id="bca92-139">该图表的属性将显示在“属性”窗格中。</span><span class="sxs-lookup"><span data-stu-id="bca92-139">The properties for the chart are displayed in the Properties pane.</span></span>  
  
5.  <span data-ttu-id="bca92-140">在 **“常规”** 部分，展开 **CustomAttributes** 节点。</span><span class="sxs-lookup"><span data-stu-id="bca92-140">In the **General** section, expand the **CustomAttributes** node.</span></span> <span data-ttu-id="bca92-141">此时将显示该条形图的属性列表。</span><span class="sxs-lookup"><span data-stu-id="bca92-141">A list of attributes for the bar chart is displayed.</span></span>  
  
6.  <span data-ttu-id="bca92-142">为 BarLabelStyle 属性选择一个值。</span><span class="sxs-lookup"><span data-stu-id="bca92-142">Select a value for the BarLabelStyle property.</span></span>  
  
 <span data-ttu-id="bca92-143">当条形图标签样式设置为 `Outside` 时，只要图表区放得下，标签就将位于图条的外部。</span><span class="sxs-lookup"><span data-stu-id="bca92-143">When the bar label style is set to `Outside`, the labels will be placed outside of the bar, as long as it fits in the chart area.</span></span> <span data-ttu-id="bca92-144">如果标签在图表区内图条以外的区域放不下，则标签将位于最靠近图条末尾的图条内。</span><span class="sxs-lookup"><span data-stu-id="bca92-144">If the label cannot be placed outside of the bar but inside of the chart area, the label is placed inside the bar at the position closest to the end of the bar.</span></span>  
  
### <a name="to-change-the-position-of-point-labels-in-an-area-column-line-or-scatter-chart"></a><span data-ttu-id="bca92-145">更改点标签在面积图、柱形图、折线图或散点图中的位置</span><span class="sxs-lookup"><span data-stu-id="bca92-145">To change the position of point labels in an Area, Column, Line or Scatter chart</span></span>  
  
1.  <span data-ttu-id="bca92-146">创建一个面积图、柱形图、折线图或散点图。</span><span class="sxs-lookup"><span data-stu-id="bca92-146">Create an Area, Column, Line or Scatter chart.</span></span>  
  
2.  <span data-ttu-id="bca92-147">在设计图面上，右键单击该图表并选择“显示数据标签”  。</span><span class="sxs-lookup"><span data-stu-id="bca92-147">On the design surface, right-click the chart and select **Show Data Labels**.</span></span>  
  
3.  <span data-ttu-id="bca92-148">打开“属性”窗格。</span><span class="sxs-lookup"><span data-stu-id="bca92-148">Open the Properties pane.</span></span> <span data-ttu-id="bca92-149">在 **“视图”** 选项卡上，单击 **“属性”**</span><span class="sxs-lookup"><span data-stu-id="bca92-149">On the **View** tab, click **Properties**</span></span>  
  
4.  <span data-ttu-id="bca92-150">在设计图面上，单击序列。</span><span class="sxs-lookup"><span data-stu-id="bca92-150">On the design surface, click the series.</span></span> <span data-ttu-id="bca92-151">序列的属性将显示在“属性”窗格中。</span><span class="sxs-lookup"><span data-stu-id="bca92-151">The properties for the series are displayed in the Properties pane.</span></span>  
  
5.  <span data-ttu-id="bca92-152">在“数据”  部分中，展开 **DataPoint** 节点，然后展开 **Label**节点。</span><span class="sxs-lookup"><span data-stu-id="bca92-152">In the **Data** section, expand the **DataPoint** node, then expand the **Label**node.</span></span>  
  
6.  <span data-ttu-id="bca92-153">为 Position 属性选择一个值。</span><span class="sxs-lookup"><span data-stu-id="bca92-153">Select a value for the Position property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bca92-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bca92-154">See Also</span></span>  
 <span data-ttu-id="bca92-155">[饼图（报表生成器和 SSRS）](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="bca92-155">[Pie Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="bca92-156">[条形图（报表生成器和 SSRS）](bar-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="bca92-156">[Bar Charts &#40;Report Builder and SSRS&#41;](bar-charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="bca92-157">[设置图表上轴标签的格式（报表生成器和 SSRS）](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="bca92-157">[Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="bca92-158">[将轴标签的格式设置为日期或货币（报表生成器和 SSRS）](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="bca92-158">[Format Axis Labels as Dates or Currencies &#40;Report Builder and SSRS&#41;](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="bca92-159">[在饼图外显示数据点标签（报表生成器和 SSRS）](display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="bca92-159">[Display Data Point Labels Outside a Pie Chart &#40;Report Builder and SSRS&#41;](display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="bca92-160">设置图表上数据点的格式（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="bca92-160">Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;</span></span>](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)  
  
  
