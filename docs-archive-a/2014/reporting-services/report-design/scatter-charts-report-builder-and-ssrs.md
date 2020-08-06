---
title: 散点图（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 2520ae24-0609-4890-807d-3267018aba8e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 93f9b31089eb8399c7fdfd201d3c799608f2e91e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690384"
---
# <a name="scatter-charts-report-builder-and-ssrs"></a><span data-ttu-id="12f47-102">散点图（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="12f47-102">Scatter Charts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="12f47-103">散点图将序列显示为一组点。</span><span class="sxs-lookup"><span data-stu-id="12f47-103">A scatter chart displays a series as a set of points.</span></span> <span data-ttu-id="12f47-104">值由点在图表中的位置表示。</span><span class="sxs-lookup"><span data-stu-id="12f47-104">Values are represented by the position of the points on the chart.</span></span> <span data-ttu-id="12f47-105">类别由图表中的不同标记表示。</span><span class="sxs-lookup"><span data-stu-id="12f47-105">Categories are represented by different markers on the chart.</span></span> <span data-ttu-id="12f47-106">散点图通常用于比较跨类别的聚合数据。</span><span class="sxs-lookup"><span data-stu-id="12f47-106">Scatter charts are typically used to compare aggregated data across categories.</span></span> <span data-ttu-id="12f47-107">有关如何将数据添加到散点图的详细信息，请参阅 [图表（报表生成器和 SSRS）](charts-report-builder-and-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="12f47-107">For more information on how to add data to a scatter chart, see [Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md)</span></span>  
  
 <span data-ttu-id="12f47-108">下图显示的是散点图示例。</span><span class="sxs-lookup"><span data-stu-id="12f47-108">The following illustration shows an example of a scatter chart.</span></span>  
  
 <span data-ttu-id="12f47-109">![散点图](../media/rs-scatterchart.gif "散点图")</span><span class="sxs-lookup"><span data-stu-id="12f47-109">![Scatter chart](../media/rs-scatterchart.gif "Scatter chart")</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations"></a><span data-ttu-id="12f47-110">变体</span><span class="sxs-lookup"><span data-stu-id="12f47-110">Variations</span></span>  
  
-   <span data-ttu-id="12f47-111">**气泡图。**</span><span class="sxs-lookup"><span data-stu-id="12f47-111">**Bubble.**</span></span> <span data-ttu-id="12f47-112">气泡图根据气泡的大小来显示数据点的两个值之间的差。</span><span class="sxs-lookup"><span data-stu-id="12f47-112">Bubble charts display the difference between two values of a data point based on the size of the bubble.</span></span> <span data-ttu-id="12f47-113">气泡越大，两个值之间的差就越大。</span><span class="sxs-lookup"><span data-stu-id="12f47-113">The larger the bubble, the larger the difference between the two values.</span></span>  
  
-   <span data-ttu-id="12f47-114">**三维气泡图**。</span><span class="sxs-lookup"><span data-stu-id="12f47-114">**3-D Bubble**.</span></span> <span data-ttu-id="12f47-115">以三维形式显示的气泡图。</span><span class="sxs-lookup"><span data-stu-id="12f47-115">A bubble chart displayed in 3-D.</span></span>  
  
## <a name="data-considerations-for-a-scatter-chart"></a><span data-ttu-id="12f47-116">散点图的数据注意事项</span><span class="sxs-lookup"><span data-stu-id="12f47-116">Data Considerations for a Scatter Chart</span></span>  
  
-   <span data-ttu-id="12f47-117">散点图通常用于显示和比较数值，例如科学数据、统计数据和工程数据。</span><span class="sxs-lookup"><span data-stu-id="12f47-117">Scatter charts are commonly used for displaying and comparing numeric values, such as scientific, statistical, and engineering data.</span></span>  
  
-   <span data-ttu-id="12f47-118">当要在不考虑时间的情况下比较大量数据点时，请使用散点图。</span><span class="sxs-lookup"><span data-stu-id="12f47-118">Use the scatter chart when you want to compare large numbers of data points without regard to time.</span></span> <span data-ttu-id="12f47-119">散点图中包含的数据越多，比较的效果就越好。</span><span class="sxs-lookup"><span data-stu-id="12f47-119">The more data that you include in a scatter chart, the better the comparisons that you can make.</span></span>  
  
-   <span data-ttu-id="12f47-120">气泡图要求每个数据点具有两个值（探顶值和探底值）。</span><span class="sxs-lookup"><span data-stu-id="12f47-120">The bubble chart requires two values (top and bottom) per data point.</span></span>  
  
-   <span data-ttu-id="12f47-121">对于处理值的分布和数据点的分簇，散点图都很理想。</span><span class="sxs-lookup"><span data-stu-id="12f47-121">Scatter charts are ideal for handling the distribution of values and clusters of data points.</span></span> <span data-ttu-id="12f47-122">如果数据集中包含非常多的点（例如，几千个点），那么散点图便是最佳图表类型。</span><span class="sxs-lookup"><span data-stu-id="12f47-122">This is the best chart type if your dataset contains many points (for example, several thousand points).</span></span> <span data-ttu-id="12f47-123">在点状图中显示多个序列看上去非常混乱，这种情况下，应避免使用点状图，</span><span class="sxs-lookup"><span data-stu-id="12f47-123">Displaying multiple series on a point chart is visually distracting and should be avoided.</span></span> <span data-ttu-id="12f47-124">而应考虑使用折线图。</span><span class="sxs-lookup"><span data-stu-id="12f47-124">In this scenario, consider using a line chart.</span></span>  
  
-   <span data-ttu-id="12f47-125">默认情况下，散点图以圆圈显示数据点。</span><span class="sxs-lookup"><span data-stu-id="12f47-125">By default, scatter charts display data points as circles.</span></span> <span data-ttu-id="12f47-126">如果在散点图中有多个序列，请考虑将每个点的标记形状更改为方形、三角形、菱形或其他形状。</span><span class="sxs-lookup"><span data-stu-id="12f47-126">If you have multiple series on a scatter chart, consider changing the marker shape of each point to be square, triangle, diamond, or another shape.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12f47-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="12f47-127">See Also</span></span>  
 <span data-ttu-id="12f47-128">[图表（报表生成器和 SSRS）](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="12f47-128">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="12f47-129">[图表类型（报表生成器和 SSRS）](chart-types-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="12f47-129">[Chart Types &#40;Report Builder and SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="12f47-130">[设置图表格式（报表生成器和 SSRS）](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="12f47-130">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="12f47-131">折线图（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="12f47-131">Line Charts &#40;Report Builder and SSRS&#41;</span></span>](line-charts-report-builder-and-ssrs.md)  
  
  
