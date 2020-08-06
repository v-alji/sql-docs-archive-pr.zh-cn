---
title: 全距图（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 48e351d3-ac5b-4eda-a4bd-32a0de206a30
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 76a9723bc55030da59d22c945a40ce4418b84ab3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690383"
---
# <a name="range-charts-report-builder-and-ssrs"></a><span data-ttu-id="2d1f8-102">范围图（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="2d1f8-102">Range Charts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="2d1f8-103">范围图类型用于显示一组数据点，其中每个数据点都由同一类别的多个值定义。</span><span class="sxs-lookup"><span data-stu-id="2d1f8-103">A range chart type displays a set of data points that are each defined by multiple values for the same category.</span></span> <span data-ttu-id="2d1f8-104">这些值通过由值轴度量的标记高度来表示。</span><span class="sxs-lookup"><span data-stu-id="2d1f8-104">Values are represented by the height of the marker as measured by the value axis.</span></span> <span data-ttu-id="2d1f8-105">类别标签显示在类别轴上。</span><span class="sxs-lookup"><span data-stu-id="2d1f8-105">Category labels are displayed on the category axis.</span></span> <span data-ttu-id="2d1f8-106">平面范围图用于填充每个数据点的探顶值和探底值之间的区域。</span><span class="sxs-lookup"><span data-stu-id="2d1f8-106">The plain range chart fills in the area between the top and bottom value for each data point.</span></span>  
  
 <span data-ttu-id="2d1f8-107">下图显示了具有三个序列的平面范围图。</span><span class="sxs-lookup"><span data-stu-id="2d1f8-107">The following illustration shows a plain range chart with three series.</span></span>  
  
 <span data-ttu-id="2d1f8-108">![范围图](../media/rs-rangechart.gif "范围图")</span><span class="sxs-lookup"><span data-stu-id="2d1f8-108">![Range chart](../media/rs-rangechart.gif "Range chart")</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations"></a><span data-ttu-id="2d1f8-109">变体</span><span class="sxs-lookup"><span data-stu-id="2d1f8-109">Variations</span></span>  
  
-   <span data-ttu-id="2d1f8-110">**平滑范围图**。</span><span class="sxs-lookup"><span data-stu-id="2d1f8-110">**Smooth range**.</span></span> <span data-ttu-id="2d1f8-111">平滑范围图显示的是曲线而不是直线。</span><span class="sxs-lookup"><span data-stu-id="2d1f8-111">A smooth range chart displays curved lines rather than straight.</span></span>  
  
-   <span data-ttu-id="2d1f8-112">**柱形范围图**。</span><span class="sxs-lookup"><span data-stu-id="2d1f8-112">**Column range**.</span></span> <span data-ttu-id="2d1f8-113">柱形范围图使用柱形图而不是面积图来显示范围。</span><span class="sxs-lookup"><span data-stu-id="2d1f8-113">A column range chart uses columns instead of areas to display the ranges.</span></span>  
  
-   <span data-ttu-id="2d1f8-114">**条形范围图**。</span><span class="sxs-lookup"><span data-stu-id="2d1f8-114">**Bar range**.</span></span> <span data-ttu-id="2d1f8-115">条形范围图使用条形图而不是面积图来显示范围。</span><span class="sxs-lookup"><span data-stu-id="2d1f8-115">A bar range chart uses bars instead of areas to display the ranges.</span></span>  
  
## <a name="data-considerations-for-range-charts"></a><span data-ttu-id="2d1f8-116">范围图的数据注意事项</span><span class="sxs-lookup"><span data-stu-id="2d1f8-116">Data Considerations for Range Charts</span></span>  
  
-   <span data-ttu-id="2d1f8-117">每个数据点的范围图类型都需要两个值。</span><span class="sxs-lookup"><span data-stu-id="2d1f8-117">Range chart types require two values per data point.</span></span> <span data-ttu-id="2d1f8-118">这些值与定义每个数据点范围的高值和低值相对应。</span><span class="sxs-lookup"><span data-stu-id="2d1f8-118">These values correspond with a high value and a low value that defines the range for each data point.</span></span>  
  
-   <span data-ttu-id="2d1f8-119">仅当探顶值始终高于探底值时，才可将范围图用于分析。</span><span class="sxs-lookup"><span data-stu-id="2d1f8-119">Range charts are useful for analysis only if the top values are always higher than the bottom values.</span></span> <span data-ttu-id="2d1f8-120">如果探顶值不高于探底值，请考虑使用折线图。</span><span class="sxs-lookup"><span data-stu-id="2d1f8-120">If this is not the case, consider using a line chart.</span></span> <span data-ttu-id="2d1f8-121">如果高值低于低值，则范围图将显示这两个值之差的绝对值。</span><span class="sxs-lookup"><span data-stu-id="2d1f8-121">If the high value is lower the low value, the range chart will display the absolute value of the difference between these values.</span></span>  
  
-   <span data-ttu-id="2d1f8-122">如果仅指定了一个值，则范围图的显示方式将与常规面积图的显示方式相同，每个数据点用一个值表示。</span><span class="sxs-lookup"><span data-stu-id="2d1f8-122">If only one value is specified, the range chart will display as if it were a regular area chart, with one value per data point.</span></span>  
  
-   <span data-ttu-id="2d1f8-123">范围图通常用于以图形方式表示包含数据集中每一类别组的最小值和最大值的数据。</span><span class="sxs-lookup"><span data-stu-id="2d1f8-123">Range charts are often used to graph data that contains minimum and maximum values for each category group in the dataset.</span></span>  
  
-   <span data-ttu-id="2d1f8-124">范围图不支持在每个数据点上显示标记。</span><span class="sxs-lookup"><span data-stu-id="2d1f8-124">Displaying markers on each data point is not supported on the range chart.</span></span>  
  
-   <span data-ttu-id="2d1f8-125">与面积图一样，在平面范围图中，如果多个序列中的值相似，这些序列将相互重叠。</span><span class="sxs-lookup"><span data-stu-id="2d1f8-125">Like the area chart, in a plain range chart, if the values in multiple series are similar, the series will overlap.</span></span> <span data-ttu-id="2d1f8-126">在这种情况下，最好使用柱形范围图或者条形范围图，而非平面范围图。</span><span class="sxs-lookup"><span data-stu-id="2d1f8-126">In this scenario, you may want to use a column range or bar range chart instead of a plain range chart.</span></span>  
  
-   <span data-ttu-id="2d1f8-127">可以使用范围条形图创建甘特图。</span><span class="sxs-lookup"><span data-stu-id="2d1f8-127">Gantt charts can be created using a range bar chart.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d1f8-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2d1f8-128">See Also</span></span>  
 <span data-ttu-id="2d1f8-129">[图表（报表生成器和 SSRS）](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2d1f8-129">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="2d1f8-130">[图表类型（报表生成器和 SSRS）](chart-types-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2d1f8-130">[Chart Types &#40;Report Builder and SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="2d1f8-131">设置图表格式&#40;报表生成器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="2d1f8-131">Formatting a Chart &#40;Report Builder and SSRS&#41;</span></span>](formatting-a-chart-report-builder-and-ssrs.md)  
  
  
