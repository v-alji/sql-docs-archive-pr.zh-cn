---
title: 在图表上显示具有多个数据区域的序列 (报表生成器和 SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 45da3d39-278e-4760-a4b3-9932c9547cf2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: dfe378f3fb5aa50ddf02f95b2b4be04dd1ae6ac5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578635"
---
# <a name="displaying-a-series-with-multiple-data-ranges-on-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="ab7c1-102">在图表中显示包含多个数据区域的序列（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="ab7c1-102">Displaying a Series with Multiple Data Ranges on a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="ab7c1-103">图表将使用序列中的最小值和最大值计算轴刻度。</span><span class="sxs-lookup"><span data-stu-id="ab7c1-103">Chart will use the minimum and maximum values of a series to calculate the axis scale.</span></span> <span data-ttu-id="ab7c1-104">图表中的序列包含多个数据区域时，数据点将会变得模糊，在图表中只能轻松地看到少量数据点。</span><span class="sxs-lookup"><span data-stu-id="ab7c1-104">When a series on your chart contains more than one range of data, the data points can become obscured, and only a few data points to be seen easily on the chart.</span></span> <span data-ttu-id="ab7c1-105">例如，假设报表显示 30 天内的每日销售总额。</span><span class="sxs-lookup"><span data-stu-id="ab7c1-105">For example, suppose a report displays daily sales totals over a period of 30 days.</span></span>  
  
 <span data-ttu-id="ab7c1-106">![具有多个数据区域的图表](../media/rs-multipledatarangeschart.gif "具有多个数据区域的图表")</span><span class="sxs-lookup"><span data-stu-id="ab7c1-106">![Chart with multiple data ranges](../media/rs-multipledatarangeschart.gif "Chart with multiple data ranges")</span></span>  
  
 <span data-ttu-id="ab7c1-107">对于大多数月份而言，销售量通常介于 10 到 40 之间。</span><span class="sxs-lookup"><span data-stu-id="ab7c1-107">For most of the month, the sales are between 10 and 40.</span></span> <span data-ttu-id="ab7c1-108">然而，为期一周的市场营销活动促使 4 月初的销售量突然增加。</span><span class="sxs-lookup"><span data-stu-id="ab7c1-108">However, a one-week sales marketing campaign has caused a sudden sales increase at the beginning of April.</span></span> <span data-ttu-id="ab7c1-109">这次销售数据的变化导致数据点的分布不均匀，从而降低了图表的整体可读性。</span><span class="sxs-lookup"><span data-stu-id="ab7c1-109">This change in sales data produces an uneven distribution of data points that reduces the overall readability of the chart.</span></span>  
  
 <span data-ttu-id="ab7c1-110">有几种不同的方法可以改善可读性：</span><span class="sxs-lookup"><span data-stu-id="ab7c1-110">There are different ways to improve readability:</span></span>  
  
-   <span data-ttu-id="ab7c1-111">**启用刻度分隔线**。</span><span class="sxs-lookup"><span data-stu-id="ab7c1-111">**Enable scale breaks**.</span></span> <span data-ttu-id="ab7c1-112">如果数据分成了两个或更多数据区域组，则可以使用刻度分隔线来删除各数据区域之间的空白。</span><span class="sxs-lookup"><span data-stu-id="ab7c1-112">If your data forms two or more sets of data ranges, use a scale break to remove the gap between the ranges.</span></span> <span data-ttu-id="ab7c1-113">刻度分隔线是在绘图区绘制的一个条带，表示序列中高值和低值之间的中断。</span><span class="sxs-lookup"><span data-stu-id="ab7c1-113">A scale break is a stripe drawn across the plotting area to denote a break between the high and low values of a series.</span></span>  
  
-   <span data-ttu-id="ab7c1-114">**筛选出不需要的值**。</span><span class="sxs-lookup"><span data-stu-id="ab7c1-114">**Filter out unnecessary values**.</span></span> <span data-ttu-id="ab7c1-115">如果您具有的数据点使重要数据区域在图表中显示时变得模糊，则可以使用报表筛选器删除不需要的数据点。</span><span class="sxs-lookup"><span data-stu-id="ab7c1-115">If you have data points that are obscuring the important data range to be displayed on the chart, remove the unwanted points using a report filter.</span></span> <span data-ttu-id="ab7c1-116">有关如何在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中向图表添加筛选器的详细信息，请参阅[添加数据集筛选器、数据区域筛选器和组筛选器（报表生成器和 SSRS）](add-dataset-filters-data-region-filters-and-group-filters.md)。</span><span class="sxs-lookup"><span data-stu-id="ab7c1-116">For information on how to add a filter to the chart in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], see [Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md).</span></span>  
  
-   <span data-ttu-id="ab7c1-117">**将每个数据区域绘制为不同的序列，以便进行多序列比较**。</span><span class="sxs-lookup"><span data-stu-id="ab7c1-117">**Plot each data range as a separate series for multiple series comparison**.</span></span> <span data-ttu-id="ab7c1-118">如果具有两个以上数据区域，可以考虑将数据区域分隔为不同的序列。</span><span class="sxs-lookup"><span data-stu-id="ab7c1-118">If you have more than two data ranges, consider separating the data ranges into separate series.</span></span> <span data-ttu-id="ab7c1-119">有关详细信息，请参阅 [图表中的多个序列（报表生成器和 SSRS）](multiple-series-on-a-chart-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="ab7c1-119">For more information, see [Multiple Series on a Chart &#40;Report Builder and SSRS&#41;](multiple-series-on-a-chart-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="displaying-multiple-data-ranges-using-scale-breaks"></a><span data-ttu-id="ab7c1-120">使用刻度分隔线显示多个数据区域</span><span class="sxs-lookup"><span data-stu-id="ab7c1-120">Displaying Multiple Data Ranges Using Scale Breaks</span></span>  
 <span data-ttu-id="ab7c1-121">启用刻度分隔线后，图表将计算在整个图表中绘制线条的位置。</span><span class="sxs-lookup"><span data-stu-id="ab7c1-121">When you enable a scale break, the chart calculates where to draw a line across the chart.</span></span> <span data-ttu-id="ab7c1-122">在各数据区域之间必须有足够的分隔空间，才能绘制刻度分隔线。</span><span class="sxs-lookup"><span data-stu-id="ab7c1-122">You must have sufficient separation between ranges to draw a scale break.</span></span> <span data-ttu-id="ab7c1-123">默认情况下，数据区域之间的分隔空间至少占图表总空间的 25% 时，才能添加刻度分隔线。</span><span class="sxs-lookup"><span data-stu-id="ab7c1-123">By default, a scale break can be added only if there is a separation between the data ranges of at least 25% of the chart.</span></span>  
  
 <span data-ttu-id="ab7c1-124">![具有刻度分割线的图表](../media/rs-multipledatarangeschart-scalebreak.gif "具有刻度分割线的图表")</span><span class="sxs-lookup"><span data-stu-id="ab7c1-124">![Chart with scale break](../media/rs-multipledatarangeschart-scalebreak.gif "Chart with scale break")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ab7c1-125">您不能指定在图表中放置刻度分隔线的位置。</span><span class="sxs-lookup"><span data-stu-id="ab7c1-125">You cannot specify where to place a scale break on a chart.</span></span> <span data-ttu-id="ab7c1-126">但是，可以修改刻度分隔线的计算方式，这将在本主题的后面部分进行介绍。</span><span class="sxs-lookup"><span data-stu-id="ab7c1-126">You can, however, modify how the scale break is calculated, described later in this topic.</span></span>  
  
 <span data-ttu-id="ab7c1-127">如果启用了刻度分隔线，但是它并未显示（即使数据区域之间有足够的分隔空间），则可以将 CollapsibleSpaceThreshold 属性设置为小于 25 的值。</span><span class="sxs-lookup"><span data-stu-id="ab7c1-127">If you enable a scale break but it does not appear, even though there is sufficient distance between the data ranges, you can set the CollapsibleSpaceThreshold property to a value less than 25.</span></span> <span data-ttu-id="ab7c1-128">CollapsibleSpaceThreshold 可指定数据区域间所需的可折叠空间的百分比。</span><span class="sxs-lookup"><span data-stu-id="ab7c1-128">The CollapsibleSpaceThreshold specifies the percent of collapsible space required between the data ranges.</span></span> <span data-ttu-id="ab7c1-129">有关详细信息，请参阅[向图表添加刻度分隔线（报表生成器和 SSRS）](add-scale-breaks-to-a-chart-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="ab7c1-129">For more information, see [Add Scale Breaks to a Chart &#40;Report Builder and SSRS&#41;](add-scale-breaks-to-a-chart-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="ab7c1-130">图表支持每个图表中最多包含 5 条刻度分隔线；但是，显示多条刻度分隔线会使报表不可读。</span><span class="sxs-lookup"><span data-stu-id="ab7c1-130">Charts support up to five scale breaks per chart; however, displaying more than one scale break can cause the chart to become unreadable.</span></span> <span data-ttu-id="ab7c1-131">如果有两个以上数据区域，可以考虑使用不同方法显示此数据。</span><span class="sxs-lookup"><span data-stu-id="ab7c1-131">If you have more than two data ranges, consider using a different method for displaying this data.</span></span> <span data-ttu-id="ab7c1-132">有关详细信息，请参阅 [图表中的多个序列（报表生成器和 SSRS）](multiple-series-on-a-chart-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="ab7c1-132">For more information, see [Multiple Series on a Chart &#40;Report Builder and SSRS&#41;](multiple-series-on-a-chart-report-builder-and-ssrs.md).</span></span>  
  
## <a name="unsupported-scale-break-scenarios"></a><span data-ttu-id="ab7c1-133">不受支持的刻度分隔线应用场景</span><span class="sxs-lookup"><span data-stu-id="ab7c1-133">Unsupported Scale Break Scenarios</span></span>  
 <span data-ttu-id="ab7c1-134">在下列图表应用场景中不支持刻度分隔线：</span><span class="sxs-lookup"><span data-stu-id="ab7c1-134">Scale breaks are not supported in the following chart scenarios:</span></span>  
  
-   <span data-ttu-id="ab7c1-135">启用了三维效果的图表。</span><span class="sxs-lookup"><span data-stu-id="ab7c1-135">The chart is 3-D enabled.</span></span>  
  
-   <span data-ttu-id="ab7c1-136">已指定对数值轴。</span><span class="sxs-lookup"><span data-stu-id="ab7c1-136">A logarithmic value axis has been specified.</span></span>  
  
-   <span data-ttu-id="ab7c1-137">已显式设置值轴的最小值或最大值。</span><span class="sxs-lookup"><span data-stu-id="ab7c1-137">The value axis minimum or maximum has been explicitly set.</span></span>  
  
-   <span data-ttu-id="ab7c1-138">图表类型为极坐标图、雷达图、饼图、圆环图、漏斗图、棱锥图或堆积图。</span><span class="sxs-lookup"><span data-stu-id="ab7c1-138">The chart type is polar, radar, pie, doughnut, funnel, pyramid, or any stacked chart.</span></span>  
  
 <span data-ttu-id="ab7c1-139">具有刻度分隔线的图表的示例可用于示例报表。</span><span class="sxs-lookup"><span data-stu-id="ab7c1-139">An example of chart with scale breaks is available as a sample report.</span></span> <span data-ttu-id="ab7c1-140">有关下载此示例报表和其他内容的详细信息，请参阅 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [报表生成器和报表设计器示例报表](https://go.microsoft.com/fwlink/?LinkId=198283)。</span><span class="sxs-lookup"><span data-stu-id="ab7c1-140">For more information about downloading this sample report and others, see [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][Report Builder and Report Designer sample reports](https://go.microsoft.com/fwlink/?LinkId=198283).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab7c1-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ab7c1-141">See Also</span></span>  
 <span data-ttu-id="ab7c1-142">[图表上的多个序列 &#40;报表生成器和 SSRS&#41;](multiple-series-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ab7c1-142">[Multiple Series on a Chart &#40;Report Builder and SSRS&#41;](multiple-series-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ab7c1-143">[设置图表格式 &#40;报表生成器和 SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ab7c1-143">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ab7c1-144">[图表中的三维效果、凹凸效果和其他效果 &#40;报表生成器和 SSRS&#41;](chart-effects-3d-bevel-and-other-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="ab7c1-144">[3D, Bevel, and Other Effects in a Chart &#40;Report Builder and SSRS&#41;](chart-effects-3d-bevel-and-other-report-builder.md) </span></span>  
 <span data-ttu-id="ab7c1-145">[图表 &#40;报表生成器和 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ab7c1-145">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ab7c1-146">["轴属性" 对话框-"轴选项" &#40;报表生成器和 SSRS&#41;](../axis-properties-dialog-box-axis-options-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ab7c1-146">[Axis Properties Dialog Box, Axis Options &#40;Report Builder and SSRS&#41;](../axis-properties-dialog-box-axis-options-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="ab7c1-147">收集饼图上的小切片（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="ab7c1-147">Collect Small Slices on a Pie Chart &#40;Report Builder and SSRS&#41;</span></span>](collect-small-slices-on-a-pie-chart-report-builder-and-ssrs.md)  
  
  
