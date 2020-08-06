---
title: 极坐标图（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c9402d8f-202a-4cdf-949e-50f5b1d2b885
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b8c4dd9394fab3e076c4a714375954a616e081f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682677"
---
# <a name="polar-charts-report-builder-and-ssrs"></a><span data-ttu-id="4b320-102">极坐标图（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="4b320-102">Polar Charts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="4b320-103">极坐标图将序列显示为一组位于 360 度圆上、按类别分组的点。</span><span class="sxs-lookup"><span data-stu-id="4b320-103">A polar chart displays a series as a set of points that are grouped by category on a 360-degree circle.</span></span> <span data-ttu-id="4b320-104">值通过由自圆心测量的点的长度来表示。</span><span class="sxs-lookup"><span data-stu-id="4b320-104">Values are represented by the length of the point as measured from the center of the circle.</span></span> <span data-ttu-id="4b320-105">点离圆心的距离越远，其值越大。</span><span class="sxs-lookup"><span data-stu-id="4b320-105">The farther the point is from the center, the greater its value.</span></span> <span data-ttu-id="4b320-106">类别标签显示在图表的周边上。</span><span class="sxs-lookup"><span data-stu-id="4b320-106">Category labels are displayed on the perimeter of the chart.</span></span> <span data-ttu-id="4b320-107">有关如何将数据添加到坐标图的详细信息，请参阅 [图表（报表生成器和 SSRS）](charts-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="4b320-107">For more information on how to add data to a polar chart, see [Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations"></a><span data-ttu-id="4b320-108">变体</span><span class="sxs-lookup"><span data-stu-id="4b320-108">Variations</span></span>  
  
-   <span data-ttu-id="4b320-109">**雷达图**。</span><span class="sxs-lookup"><span data-stu-id="4b320-109">**Radar chart**.</span></span> <span data-ttu-id="4b320-110">雷达图将序列显示为环形线条或区域。</span><span class="sxs-lookup"><span data-stu-id="4b320-110">A radar chart displays a series as a circular line or area.</span></span> <span data-ttu-id="4b320-111">与极坐标图不同的是，雷达图不是以极坐标的形式显示数据。</span><span class="sxs-lookup"><span data-stu-id="4b320-111">Unlike the polar chart, the radar chart does not display data in terms of polar coordinates.</span></span>  
  
## <a name="data-considerations-for-polar-charts"></a><span data-ttu-id="4b320-112">极坐标图的数据注意事项</span><span class="sxs-lookup"><span data-stu-id="4b320-112">Data Considerations for Polar Charts</span></span>  
  
-   <span data-ttu-id="4b320-113">雷达图在比较多个类别数据序列方面很有用。</span><span class="sxs-lookup"><span data-stu-id="4b320-113">The radar chart is useful for comparisons between multiple series of category data.</span></span>  
  
-   <span data-ttu-id="4b320-114">极坐标图最常用于以图形表示极坐标数据，其中的每个数据点都是由一个角度和一个距离共同决定的。</span><span class="sxs-lookup"><span data-stu-id="4b320-114">Polar charts are most commonly used to graph polar data, where each data point is determined by an angle and a distance.</span></span>  
  
-   <span data-ttu-id="4b320-115">在同一图表区中，极坐标图不能与任何其他图表类型结合使用。</span><span class="sxs-lookup"><span data-stu-id="4b320-115">Polar charts cannot be combined with any other chart type in the same chart area.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b320-116">示例</span><span class="sxs-lookup"><span data-stu-id="4b320-116">Example</span></span>  
 <span data-ttu-id="4b320-117">下例说明了如何使用雷达图。</span><span class="sxs-lookup"><span data-stu-id="4b320-117">The following example shows how a radar chart can be used.</span></span> <span data-ttu-id="4b320-118">下表提供了雷达图的示例数据。</span><span class="sxs-lookup"><span data-stu-id="4b320-118">The table below provides sample data for the chart.</span></span>  
  
|<span data-ttu-id="4b320-119">名称</span><span class="sxs-lookup"><span data-stu-id="4b320-119">Name</span></span>|<span data-ttu-id="4b320-120">Sales</span><span class="sxs-lookup"><span data-stu-id="4b320-120">Sales</span></span>|  
|----------|-----------|  
|<span data-ttu-id="4b320-121">Shrubs</span><span class="sxs-lookup"><span data-stu-id="4b320-121">Shrubs</span></span>|<span data-ttu-id="4b320-122">61</span><span class="sxs-lookup"><span data-stu-id="4b320-122">61</span></span>|  
|<span data-ttu-id="4b320-123">Seeds</span><span class="sxs-lookup"><span data-stu-id="4b320-123">Seeds</span></span>|<span data-ttu-id="4b320-124">78</span><span class="sxs-lookup"><span data-stu-id="4b320-124">78</span></span>|  
|<span data-ttu-id="4b320-125">Bulbs</span><span class="sxs-lookup"><span data-stu-id="4b320-125">Bulbs</span></span>|<span data-ttu-id="4b320-126">60</span><span class="sxs-lookup"><span data-stu-id="4b320-126">60</span></span>|  
|<span data-ttu-id="4b320-127">Trees</span><span class="sxs-lookup"><span data-stu-id="4b320-127">Trees</span></span>|<span data-ttu-id="4b320-128">38</span><span class="sxs-lookup"><span data-stu-id="4b320-128">38</span></span>|  
|<span data-ttu-id="4b320-129">Flowers</span><span class="sxs-lookup"><span data-stu-id="4b320-129">Flowers</span></span>|<span data-ttu-id="4b320-130">81</span><span class="sxs-lookup"><span data-stu-id="4b320-130">81</span></span>|  
  
 <span data-ttu-id="4b320-131">在本例中，“名称”字段放置在“类别组”区域中。</span><span class="sxs-lookup"><span data-stu-id="4b320-131">In this example, the Name field is placed in the Category Groups area.</span></span> <span data-ttu-id="4b320-132">“销售量”字段放置在“值”区域中。</span><span class="sxs-lookup"><span data-stu-id="4b320-132">The Sales field is placed in the Values area.</span></span> <span data-ttu-id="4b320-133">放置“销售量”字段时，图表的该字段将自动合计。</span><span class="sxs-lookup"><span data-stu-id="4b320-133">The Sales field is automatically aggregated for the chart when you drop it.</span></span> <span data-ttu-id="4b320-134">雷达图根据“销售量”字段中值的个数计算标签的放置位置，该字段包含五个值，因此将标签放在圆上的五个等分点处。</span><span class="sxs-lookup"><span data-stu-id="4b320-134">The radar chart calculates where to place the labels based on the number of values in the Sales field, which contains five values and places labels at five equidistant points on a circle.</span></span> <span data-ttu-id="4b320-135">如果“销售量”字段包含三个值，则会将标签放在圆上的三个等分点处。</span><span class="sxs-lookup"><span data-stu-id="4b320-135">If the Sales field contained three values, the labels would be placed at three equidistant points on a circle.</span></span>  
  
 <span data-ttu-id="4b320-136">下图显示了一个基于前面所提供数据的雷达图示例。</span><span class="sxs-lookup"><span data-stu-id="4b320-136">The following illustration shows an example of a radar chart based on the data presented.</span></span>  
  
 <span data-ttu-id="4b320-137">![雷达图](../media/rs-radarchart.gif "雷达图")</span><span class="sxs-lookup"><span data-stu-id="4b320-137">![Radar chart](../media/rs-radarchart.gif "Radar chart")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b320-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4b320-138">See Also</span></span>  
 <span data-ttu-id="4b320-139">[图表（报表生成器和 SSRS）](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4b320-139">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4b320-140">[设置图表格式（报表生成器和 SSRS）](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4b320-140">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4b320-141">[图表类型（报表生成器和 SSRS）](chart-types-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4b320-141">[Chart Types &#40;Report Builder and SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4b320-142">[折线图（报表生成器和 SSRS）](line-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4b320-142">[Line Charts &#40;Report Builder and SSRS&#41;](line-charts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="4b320-143">图表中的空白和 Null 数据点（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="4b320-143">Empty and Null Data Points in Charts &#40;Report Builder and SSRS&#41;</span></span>](empty-and-null-data-points-in-charts-report-builder-and-ssrs.md)  
  
  
