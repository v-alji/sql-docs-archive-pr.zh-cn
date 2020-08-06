---
title: 面积图（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 245b236d-1d55-4744-b752-80bd133502aa
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f401efa0abd5eac8ab39e511bc6b16a4f381ebdf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690395"
---
# <a name="area-charts-report-builder-and-ssrs"></a><span data-ttu-id="85c7e-102">面积图（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="85c7e-102">Area Charts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="85c7e-103">面积图将序列显示为一组由线连接的点，并填充线下方的所有区域。</span><span class="sxs-lookup"><span data-stu-id="85c7e-103">An area chart displays a series as a set of points connected by a line, with all the area filled in below the line.</span></span> <span data-ttu-id="85c7e-104">有关如何向分区图添加数据的详细信息，请参阅 [图表（报表生成器和 SSRS）](charts-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="85c7e-104">For more information on how to add data to an area chart, see [Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="85c7e-105">下图显示了一个堆积面积图的例子。</span><span class="sxs-lookup"><span data-stu-id="85c7e-105">The following illustration shows an example of a stacked area chart.</span></span> <span data-ttu-id="85c7e-106">这里的数据非常适合用堆积面积图显示，因为这种图表可以显示所有序列的总计以及每个序列在总计中所占的比例。</span><span class="sxs-lookup"><span data-stu-id="85c7e-106">The data is well suited for display on a stacked area chart because the chart can display totals for all series as well as the proportion that each series contributes to the total.</span></span>  
  
 <span data-ttu-id="85c7e-107">![面积图](../media/areachart.gif "面积图")</span><span class="sxs-lookup"><span data-stu-id="85c7e-107">![Area chart](../media/areachart.gif "Area chart")</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations"></a><span data-ttu-id="85c7e-108">变体</span><span class="sxs-lookup"><span data-stu-id="85c7e-108">Variations</span></span>  
  
-   <span data-ttu-id="85c7e-109">**堆积面积图**。</span><span class="sxs-lookup"><span data-stu-id="85c7e-109">**Stacked area**.</span></span> <span data-ttu-id="85c7e-110">一种多个序列垂直堆积的面积图。</span><span class="sxs-lookup"><span data-stu-id="85c7e-110">An area chart where multiple series are stacked vertically.</span></span> <span data-ttu-id="85c7e-111">如果图表中只有一个序列，则这种堆积面积图将与一般面积图的显示相同。</span><span class="sxs-lookup"><span data-stu-id="85c7e-111">If there is only one series in your chart, the stacked area chart will display the same as an area chart.</span></span>  
  
-   <span data-ttu-id="85c7e-112">**百分比堆积面积图**。</span><span class="sxs-lookup"><span data-stu-id="85c7e-112">**Percent stacked area**.</span></span> <span data-ttu-id="85c7e-113">一种多个序列垂直堆积以占满整个图表区的面积图。</span><span class="sxs-lookup"><span data-stu-id="85c7e-113">An area chart where multiple series are stacked vertically to fit the entire chart area.</span></span> <span data-ttu-id="85c7e-114">如果图表中只有一个序列，则这种堆积面积图将与一般面积图的显示相同。</span><span class="sxs-lookup"><span data-stu-id="85c7e-114">If there is only one series in your chart, the stacked area chart will display the same as an area chart.</span></span>  
  
-   <span data-ttu-id="85c7e-115">**平滑面积图**。</span><span class="sxs-lookup"><span data-stu-id="85c7e-115">**Smooth area**.</span></span> <span data-ttu-id="85c7e-116">一种由平滑线而非规则线连接数据点的面积图。</span><span class="sxs-lookup"><span data-stu-id="85c7e-116">An area chart where the data points are connected by a smooth line instead of a regular line.</span></span> <span data-ttu-id="85c7e-117">如果您更加关注显示走向而非显示各个数据点的值，则应使用平滑面积图而非一般的面积图。</span><span class="sxs-lookup"><span data-stu-id="85c7e-117">Use a smooth area chart instead of an area chart when you are more concerned with displaying trends than with displaying the values of individual data points.</span></span>  
  
## <a name="data-considerations-for-area-charts"></a><span data-ttu-id="85c7e-118">面积图的数据注意事项</span><span class="sxs-lookup"><span data-stu-id="85c7e-118">Data Considerations for Area Charts</span></span>  
  
-   <span data-ttu-id="85c7e-119">除折线图之外，面积图是唯一一种连续显示数据的图表类型。</span><span class="sxs-lookup"><span data-stu-id="85c7e-119">Along with the line chart, the area chart is the only chart type that displays data contiguously.</span></span> <span data-ttu-id="85c7e-120">因此，面积图常用来表示在一个连续时间段内出现的数据。</span><span class="sxs-lookup"><span data-stu-id="85c7e-120">For this reason, an area chart is commonly used to represent data that occurs over a continuous period of time.</span></span>  
  
-   <span data-ttu-id="85c7e-121">百分比堆积面积图对显示在一段时间内出现的成比例数据很有用。</span><span class="sxs-lookup"><span data-stu-id="85c7e-121">A percent stacked area chart is useful for showing proportional data that occurs over time.</span></span>  
  
-   <span data-ttu-id="85c7e-122">如果只有一个序列，则会将堆积面积图绘制成一般的面积图。</span><span class="sxs-lookup"><span data-stu-id="85c7e-122">If there is only one series, a stacked area chart will be drawn as an area chart.</span></span>  
  
-   <span data-ttu-id="85c7e-123">在一般的面积图中，如果多个序列中的值相似，则面积可能会发生重叠，从而遮挡了重要的数据点值。</span><span class="sxs-lookup"><span data-stu-id="85c7e-123">In a plain area chart, if the values in multiple series are similar, the areas may overlap, obscuring important data point values.</span></span> <span data-ttu-id="85c7e-124">可以通过将图表类型更改为堆积面积图来解决此问题，堆积面积图的设计目的就是为了在面积图上显示多个序列。</span><span class="sxs-lookup"><span data-stu-id="85c7e-124">You can resolve this issue by changing the chart type to a stacked area chart, which is designed to show multiple series on an area chart.</span></span>  
  
-   <span data-ttu-id="85c7e-125">如果堆积面积图中含有间隙，可能是因为数据集包含空值，空值在堆积面积图上将显示为空白区域。</span><span class="sxs-lookup"><span data-stu-id="85c7e-125">If your stacked area chart contains gaps, it is possible that your dataset includes empty values, which will be shown as a vacant section on a stacked area chart.</span></span> <span data-ttu-id="85c7e-126">如果数据集包含空值，请考虑在图表中插入空点。</span><span class="sxs-lookup"><span data-stu-id="85c7e-126">If your dataset includes empty values, consider inserting empty points on the chart.</span></span> <span data-ttu-id="85c7e-127">如果添加空点，则会用一种不同的颜色填充图表上的空白区域以指示 Null 或零值。</span><span class="sxs-lookup"><span data-stu-id="85c7e-127">Adding empty points will fill in the empty areas on the chart with a different color to indicate null or zero values.</span></span> <span data-ttu-id="85c7e-128">有关详细信息，请参阅[向图表添加空点 &#40;报表生成器和 SSRS&#41;](add-empty-points-to-a-chart-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="85c7e-128">For more information, see [Add Empty Points to the Chart &#40;Report Builder and SSRS&#41;](add-empty-points-to-a-chart-report-builder-and-ssrs.md).</span></span>  
  
-   <span data-ttu-id="85c7e-129">面积图类型在行为上与柱形图和折线图非常相似。</span><span class="sxs-lookup"><span data-stu-id="85c7e-129">Area chart types are very similar to column and line charts in behavior.</span></span> <span data-ttu-id="85c7e-130">如果要在多个序列之间进行比较，请考虑改用柱形图。</span><span class="sxs-lookup"><span data-stu-id="85c7e-130">If you are making a comparison between multiple series, consider using a column chart instead.</span></span> <span data-ttu-id="85c7e-131">如果要分析在一段时间内的走向，请考虑使用折线图。</span><span class="sxs-lookup"><span data-stu-id="85c7e-131">If you are analyzing trends over a period of time, consider using a line chart.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85c7e-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="85c7e-132">See Also</span></span>  
 <span data-ttu-id="85c7e-133">[图表（报表生成器和 SSRS）](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="85c7e-133">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="85c7e-134">[图表类型（报表生成器和 SSRS）](chart-types-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="85c7e-134">[Chart Types &#40;Report Builder and SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="85c7e-135">[折线图（报表生成器和 SSRS）](line-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="85c7e-135">[Line Charts &#40;Report Builder and SSRS&#41;](line-charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="85c7e-136">[更改图表类型（报表生成器和 SSRS）](change-a-chart-type-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="85c7e-136">[Change a Chart Type &#40;Report Builder and SSRS&#41;](change-a-chart-type-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="85c7e-137">图表中的空白和 Null 数据点（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="85c7e-137">Empty and Null Data Points in Charts &#40;Report Builder and SSRS&#41;</span></span>](empty-and-null-data-points-in-charts-report-builder-and-ssrs.md)  
  
  
