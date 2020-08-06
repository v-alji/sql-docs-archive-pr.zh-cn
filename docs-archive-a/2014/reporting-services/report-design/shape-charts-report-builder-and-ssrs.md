---
title: 形状图（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4b8404c1-aa89-4350-8bd6-203bc0446ee4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c8940f23c0c2b1fdabadec62de4c214c98d60b1c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587185"
---
# <a name="shape-charts-report-builder-and-ssrs"></a><span data-ttu-id="40871-102">形状图（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="40871-102">Shape Charts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="40871-103">形状图将值数据显示为整体的百分比。</span><span class="sxs-lookup"><span data-stu-id="40871-103">A shape chart displays value data as percentages of a whole.</span></span> <span data-ttu-id="40871-104">形状图通常用于显示数据集中不同值之间的比例比较结果。</span><span class="sxs-lookup"><span data-stu-id="40871-104">Shape charts are typically used to show proportional comparisons between different values in a set.</span></span> <span data-ttu-id="40871-105">类别由各个形状段来表示。</span><span class="sxs-lookup"><span data-stu-id="40871-105">Categories are represented by individual segments of the shape.</span></span> <span data-ttu-id="40871-106">形状段的大小由值来决定。</span><span class="sxs-lookup"><span data-stu-id="40871-106">The size of the segment is determined by the value.</span></span> <span data-ttu-id="40871-107">形状图与饼图的用法类似，但前者是按从最大到最小的顺序来排列类别。</span><span class="sxs-lookup"><span data-stu-id="40871-107">Shape charts are similar in use to pie charts, except that they order categories from largest to smallest.</span></span>  
  
 <span data-ttu-id="40871-108">漏斗图按逐渐递减的比例来显示值。</span><span class="sxs-lookup"><span data-stu-id="40871-108">A funnel chart displays values as progressively decreasing proportions.</span></span> <span data-ttu-id="40871-109">漏斗区的大小由序列值在所有值总计中所占的百分比来确定。</span><span class="sxs-lookup"><span data-stu-id="40871-109">The size of the area is determined by the series value as a percentage of the total of all values.</span></span> <span data-ttu-id="40871-110">例如，您可能使用漏斗图来显示网站访问者的趋势。</span><span class="sxs-lookup"><span data-stu-id="40871-110">For example, you might use a funnel chart to display Web site visitor trends.</span></span> <span data-ttu-id="40871-111">漏斗图可能会在顶部显示较宽的区域，表明访问者对主页的点击率；而其他区域将成比例缩小。</span><span class="sxs-lookup"><span data-stu-id="40871-111">It is likely that the funnel chart will display a wide area at the top, indicating visitor page hits to the homepage, and the other areas will be proportionally smaller.</span></span> <span data-ttu-id="40871-112">有关如何向漏斗图添加数据的详细信息，请参阅 [图表（报表生成器和 SSRS）](charts-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="40871-112">For more information about how to add data to a funnel chart, see [Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="40871-113">下图显示的是漏斗图示例。</span><span class="sxs-lookup"><span data-stu-id="40871-113">The following illustration shows an example of a funnel chart.</span></span>  
  
 <span data-ttu-id="40871-114">![漏斗图](../media/rs-funnelchart.gif "漏斗图")</span><span class="sxs-lookup"><span data-stu-id="40871-114">![Funnel chart](../media/rs-funnelchart.gif "Funnel chart")</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations"></a><span data-ttu-id="40871-115">变体</span><span class="sxs-lookup"><span data-stu-id="40871-115">Variations</span></span>  
  
-   <span data-ttu-id="40871-116">**棱锥图**。</span><span class="sxs-lookup"><span data-stu-id="40871-116">**Pyramid**.</span></span> <span data-ttu-id="40871-117">棱锥图显示的是成比例数据，以便图表看起来像一个棱锥。</span><span class="sxs-lookup"><span data-stu-id="40871-117">A pyramid chart displays proportional data so that the chart looks like a pyramid.</span></span>  
  
## <a name="data-considerations-for-shape-charts"></a><span data-ttu-id="40871-118">形状图的数据注意事项</span><span class="sxs-lookup"><span data-stu-id="40871-118">Data Considerations for Shape Charts</span></span>  
  
-   <span data-ttu-id="40871-119">形状图的视觉效果较好，因此常用于报表中。</span><span class="sxs-lookup"><span data-stu-id="40871-119">Shape charts are popular in reports because of their visual impact.</span></span> <span data-ttu-id="40871-120">但是，形状图是一种非常简单化的图表类型，可能无法最好地表示数据。</span><span class="sxs-lookup"><span data-stu-id="40871-120">However, shape charts are a very simplified chart type that may not best represent your data.</span></span> <span data-ttu-id="40871-121">仅当数据聚合成七个数据点或更少数据点时，才考虑使用形状图。</span><span class="sxs-lookup"><span data-stu-id="40871-121">Consider using a shape chart only once the data has been aggregated to seven data points or less.</span></span> <span data-ttu-id="40871-122">通常，在使用形状图时应当对每个数据区域仅显示一种类别。</span><span class="sxs-lookup"><span data-stu-id="40871-122">In general, use the shape chart to display only one category per data region.</span></span>  
  
-   <span data-ttu-id="40871-123">形状图将每个数据组显示为单独的图表段。</span><span class="sxs-lookup"><span data-stu-id="40871-123">Shape charts display each data group as a separate segment of the chart.</span></span> <span data-ttu-id="40871-124">您必须至少添加一个数据字段和一个类别字段。</span><span class="sxs-lookup"><span data-stu-id="40871-124">You must add at least one data field and one category field.</span></span> <span data-ttu-id="40871-125">如果向形状图中添加多个数据字段，则形状图会在同一个图表中显示这些数据字段。</span><span class="sxs-lookup"><span data-stu-id="40871-125">If more than one data field is added to a shape chart, the shape chart will display both data fields in the same chart.</span></span>  
  
-   <span data-ttu-id="40871-126">形状图最有效的是以排序顺序显示成比例的百分比。</span><span class="sxs-lookup"><span data-stu-id="40871-126">Shape charts are most effective for showing proportional percentages in sorted order.</span></span> <span data-ttu-id="40871-127">然而，为了保持一致性，图表默认情况下不会对数据集中的值进行排序。</span><span class="sxs-lookup"><span data-stu-id="40871-127">However, in order to maintain consistency, the chart does not sort the values in your dataset by default.</span></span> <span data-ttu-id="40871-128">请考虑从高到低对值排序，从而最准确地以漏斗图或棱锥图来表示数据。</span><span class="sxs-lookup"><span data-stu-id="40871-128">Consider ordering your values from highest to lowest to most accurately represent your data as a funnel or a pyramid.</span></span> <span data-ttu-id="40871-129">有关详细信息，请参阅 [对数据进行筛选、分组和排序（报表生成器和 SSRS）](filter-group-and-sort-data-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="40871-129">For more information, see [Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md).</span></span>  
  
-   <span data-ttu-id="40871-130">当计算比率时，Null 值、空值、负值和零值均无效。</span><span class="sxs-lookup"><span data-stu-id="40871-130">Null, empty, negative and zero values have no effect when calculating ratios.</span></span> <span data-ttu-id="40871-131">因此，这些值不会显示在形状图中。</span><span class="sxs-lookup"><span data-stu-id="40871-131">For this reason, these values are not shown on a shape chart.</span></span> <span data-ttu-id="40871-132">若要将这些值类型显示在图表中，需将图表类型更改为除形状图外的其他类型。</span><span class="sxs-lookup"><span data-stu-id="40871-132">If you want to visually indicate these types of values on your chart, change the chart type to be something other than a shape chart.</span></span> <span data-ttu-id="40871-133">有关如何向非形状图添加空点的详细信息，请参阅向[图表添加空点 &#40;报表生成器和 SSRS&#41;](add-empty-points-to-a-chart-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="40871-133">For more information about how to add empty points to a non-shape chart, see [Add Empty Points to the Chart &#40;Report Builder and SSRS&#41;](add-empty-points-to-a-chart-report-builder-and-ssrs.md).</span></span>  
  
-   <span data-ttu-id="40871-134">若要使用自定义调色板在形状图上定义自己的颜色，请确保调色板中有足够的颜色，从而均用唯一的颜色突出显示各个数据点。</span><span class="sxs-lookup"><span data-stu-id="40871-134">If you are defining your own colors on a shape chart using a custom palette, be sure that you have enough colors in your palette to highlight each data point with its own unique color.</span></span> <span data-ttu-id="40871-135">有关详细信息，请参阅 [设置图表上序列颜色的格式（报表生成器和 SSRS）](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="40871-135">For more information, see [Formatting Series Colors on a Chart &#40;Report Builder and SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md).</span></span>  
  
-   <span data-ttu-id="40871-136">与所有其他图表类型不同的是，形状图将在其图例中显示各个数据点，而不是单个序列。</span><span class="sxs-lookup"><span data-stu-id="40871-136">Unlike all other chart types, a shape chart will display individual data points, and not individual series, in its legend.</span></span>  
  
-   <span data-ttu-id="40871-137">漏斗图将忽略值和类别轴的设置。</span><span class="sxs-lookup"><span data-stu-id="40871-137">Settings for the value and category axis are ignored for funnel charts.</span></span> <span data-ttu-id="40871-138">如果有多个类别或序列组，则图表图例中将显示组标签。</span><span class="sxs-lookup"><span data-stu-id="40871-138">If you have multiple category or series groups, the group labels are displayed in the chart legend.</span></span>  
  
-   <span data-ttu-id="40871-139">在相同的图表区域中，形状图不能与任何其他图表类型结合使用。</span><span class="sxs-lookup"><span data-stu-id="40871-139">Shape chart types cannot be combined with any other chart type in the same chart area.</span></span> <span data-ttu-id="40871-140">如果必须显示形状图数据与其他类型图表数据之间的比较结果，则需要添加第二个图表区域。</span><span class="sxs-lookup"><span data-stu-id="40871-140">If you have to show comparisons between data displayed on a shape chart, and data displayed on another chart type, you will need to add a second chart area.</span></span>  
  
-   <span data-ttu-id="40871-141">添加三维效果将显著改善形状图表类型的总体外观。</span><span class="sxs-lookup"><span data-stu-id="40871-141">Adding 3-D effects significantly improves the overall appearance of a shape chart type.</span></span>  
  
-   <span data-ttu-id="40871-142">您可以在饼图和圆环图中应用其他绘制样式以增加视觉效果。</span><span class="sxs-lookup"><span data-stu-id="40871-142">You can apply additional drawing styles to pie and doughnut charts for increased visual impact.</span></span> <span data-ttu-id="40871-143">有关详细信息，请参阅[设置图表上序列颜色的格式（报表生成器和 SSRS）](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="40871-143">See [Formatting Series Colors on a Chart &#40;Report Builder and SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md) for more information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40871-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="40871-144">See Also</span></span>  
 <span data-ttu-id="40871-145">[图表 &#40;报表生成器和 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="40871-145">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="40871-146">[设置图表格式 &#40;报表生成器和 SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="40871-146">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="40871-147">[图表中的空和 Null 数据点 &#40;报表生成器和 SSRS&#41;](empty-and-null-data-points-in-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="40871-147">[Empty and Null Data Points in Charts &#40;Report Builder and SSRS&#41;](empty-and-null-data-points-in-charts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="40871-148">饼图&#40;报表生成器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="40871-148">Pie Charts &#40;Report Builder and SSRS&#41;</span></span>](pie-charts-report-builder-and-ssrs.md)  
  
  
