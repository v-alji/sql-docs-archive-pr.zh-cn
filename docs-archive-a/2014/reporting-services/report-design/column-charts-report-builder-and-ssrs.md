---
title: 柱形图（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ae8c138b-e356-4ad8-862c-a4a8d0c04149
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b6ebada49e65d44a2294228a3840bf4951140812
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694255"
---
# <a name="column-charts-report-builder-and-ssrs"></a><span data-ttu-id="31e73-102">柱形图（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="31e73-102">Column Charts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="31e73-103">柱形图将序列显示为一组按类别分组的垂直图条。</span><span class="sxs-lookup"><span data-stu-id="31e73-103">A column chart displays a series as a set of vertical bars that are grouped by category.</span></span> <span data-ttu-id="31e73-104">柱形图对于显示一段时间的数据变化或说明各项之间的比较来说十分有用。</span><span class="sxs-lookup"><span data-stu-id="31e73-104">Column charts are useful for showing data changes over a period of time or for illustrating comparisons among items.</span></span> <span data-ttu-id="31e73-105">平面柱形图与条形图关系密切，条形图将序列显示为多组水平图条，而范围柱形图将序列显示为多组具有不同起点和终点的垂直图条。</span><span class="sxs-lookup"><span data-stu-id="31e73-105">The plain column chart is closely related to the bar chart, which displays series as sets of horizontal bars, and the range column chart, which displays series as sets of vertical bars with varying beginning and end points.</span></span> <span data-ttu-id="31e73-106">有关详细信息，请参阅 [条形图（报表生成器和 SSRS）](charts-report-builder-and-ssrs.md) 和 [范围图（报表生成器和 SSRS）](range-charts-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="31e73-106">For more information, see [Bar Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) and [Range Charts &#40;Report Builder and SSRS&#41;](range-charts-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="31e73-107">柱形图非常适用于此数据，因为所有这三个序列都共享一个公共时间段，允许进行有效比较。</span><span class="sxs-lookup"><span data-stu-id="31e73-107">The column chart is well suited for this data because all three series share a common time period, allowing for valid comparisons to be made.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations-of-a-column-chart"></a><span data-ttu-id="31e73-108">柱形图变体</span><span class="sxs-lookup"><span data-stu-id="31e73-108">Variations of a Column Chart</span></span>  
  
-   <span data-ttu-id="31e73-109">**堆积**。</span><span class="sxs-lookup"><span data-stu-id="31e73-109">**Stacked**.</span></span> <span data-ttu-id="31e73-110">一种多个序列垂直堆积的柱形图。</span><span class="sxs-lookup"><span data-stu-id="31e73-110">A column chart where multiple series are stacked vertically.</span></span> <span data-ttu-id="31e73-111">如果图表中只有一个序列，则堆积柱形图将与柱形图的显示相同。</span><span class="sxs-lookup"><span data-stu-id="31e73-111">If there is only one series in your chart, the stacked column chart will display the same as a column chart.</span></span>  
  
-   <span data-ttu-id="31e73-112">**百分比堆积**。</span><span class="sxs-lookup"><span data-stu-id="31e73-112">**Percent stacked**.</span></span> <span data-ttu-id="31e73-113">一种多个序列垂直堆积以占满图表区的柱形图。</span><span class="sxs-lookup"><span data-stu-id="31e73-113">A column chart where multiple series are stacked vertically to fit 100% of the chart area.</span></span> <span data-ttu-id="31e73-114">如果图表中只有一个序列，则所有柱形条将占满图表区。</span><span class="sxs-lookup"><span data-stu-id="31e73-114">If there is only one series in your chart, all the column bars will fit to 100% of the chart area.</span></span>  
  
-   <span data-ttu-id="31e73-115">**三维簇状**。</span><span class="sxs-lookup"><span data-stu-id="31e73-115">**3D clustered**.</span></span> <span data-ttu-id="31e73-116">一种将每个序列分别显示在三维图表的单独行中的柱形图。</span><span class="sxs-lookup"><span data-stu-id="31e73-116">A column chart that shows individual series in separate rows on a 3D chart.</span></span>  
  
-   <span data-ttu-id="31e73-117">**三维圆柱**。</span><span class="sxs-lookup"><span data-stu-id="31e73-117">**3D cylinder**.</span></span> <span data-ttu-id="31e73-118">一种图条在三维图表中的形状类似于圆柱的柱形图。</span><span class="sxs-lookup"><span data-stu-id="31e73-118">A column chart whose bars are shaped like cylinders on a 3D chart.</span></span>  
  
-   <span data-ttu-id="31e73-119">`Histogram`.</span><span class="sxs-lookup"><span data-stu-id="31e73-119">`Histogram`.</span></span> <span data-ttu-id="31e73-120">一种图表通过计算以使其图条按正态分布进行排列的柱形图。</span><span class="sxs-lookup"><span data-stu-id="31e73-120">A column chart which the chart calculates so that its bars are arranged in a normal distribution.</span></span>  
  
-   <span data-ttu-id="31e73-121">`Pareto`.</span><span class="sxs-lookup"><span data-stu-id="31e73-121">`Pareto`.</span></span> <span data-ttu-id="31e73-122">一种图条按从最高到最低排列的柱形图。</span><span class="sxs-lookup"><span data-stu-id="31e73-122">A column chart whose bars are arranged from highest to lowest.</span></span>  
  
## <a name="data-considerations-for-a-column-chart"></a><span data-ttu-id="31e73-123">柱形图在数据方面的注意事项</span><span class="sxs-lookup"><span data-stu-id="31e73-123">Data Considerations for a Column Chart</span></span>  
  
-   <span data-ttu-id="31e73-124">条形图和柱形图最常用于说明各组之间的比较情况。</span><span class="sxs-lookup"><span data-stu-id="31e73-124">Bar and column charts are most commonly used to show comparisons between groups.</span></span> <span data-ttu-id="31e73-125">如果图表中存在三个以上的序列，请考虑使用堆积条形图或柱形图。</span><span class="sxs-lookup"><span data-stu-id="31e73-125">If more than three series are present on the chart, consider using a stacked bar or column chart.</span></span> <span data-ttu-id="31e73-126">如果图表中有多个序列，则还可以将堆积条形图或柱形图收集到多个组中。</span><span class="sxs-lookup"><span data-stu-id="31e73-126">You can also collect stacked bar or column charts into multiple groups if you have several series on your chart.</span></span> <span data-ttu-id="31e73-127">有关详细信息，请参阅[条形图 &#40;报表生成器和 SSRS&#41;](charts-report-builder-and-ssrs.md)和*柱形图*。</span><span class="sxs-lookup"><span data-stu-id="31e73-127">For more information, see [Bar Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) and *Column Charts*.</span></span>  
  
-   <span data-ttu-id="31e73-128">在柱形图中，在以水平方式显示类别轴标签时空间会很局促。</span><span class="sxs-lookup"><span data-stu-id="31e73-128">In a column chart, you have less space for category axis labels to display horizontally.</span></span> <span data-ttu-id="31e73-129">如果类别标签较长，请考虑使用条形图或更改标签的旋转角度。</span><span class="sxs-lookup"><span data-stu-id="31e73-129">If you have longer category labels, consider using a bar chart or changing the rotation angle of the label.</span></span>  
  
-   <span data-ttu-id="31e73-130">您可以在柱形图中为单个图条添加特殊的绘制样式以增加其视觉效果。</span><span class="sxs-lookup"><span data-stu-id="31e73-130">You can add special drawing styles to the individual bars on a column chart to increase its visual impact.</span></span> <span data-ttu-id="31e73-131">绘制样式包括楔形、浮雕、圆柱形和由明到暗。</span><span class="sxs-lookup"><span data-stu-id="31e73-131">Drawing styles include wedge, emboss, cylinder and light-to-dark.</span></span> <span data-ttu-id="31e73-132">设计这些效果的目的是为了改进二维图表的外观。</span><span class="sxs-lookup"><span data-stu-id="31e73-132">These effects are designed to improve the appearance of your 2D chart.</span></span> <span data-ttu-id="31e73-133">即使使用的是三维图表，您仍可应用绘制样式，但效果可能不会相同。</span><span class="sxs-lookup"><span data-stu-id="31e73-133">If you are using a 3D chart, the drawing styles will still be applied, but may not have the same effect.</span></span> <span data-ttu-id="31e73-134">有关如何向条形图添加绘制样式的详细信息，请参阅 [向图表添加凹凸效果、阳文和纹理样式（报表生成器和 SSRS）](chart-effects-add-bevel-emboss-or-texture-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="31e73-134">For more information about how to add a drawing style to a bar chart, see [Add Bevel, Emboss, and Texture Styles to a Chart &#40;Report Builder and SSRS&#41;](chart-effects-add-bevel-emboss-or-texture-report-builder.md).</span></span>  
  
-   <span data-ttu-id="31e73-135">柱形图的独特功能是将图表显示为直方图或排列图。</span><span class="sxs-lookup"><span data-stu-id="31e73-135">Unique to column charts is the ability to show your chart as a histogram or Pareto chart.</span></span> <span data-ttu-id="31e73-136">为此，请 `Histogram` `Pareto` 在属性窗口中将 ShowColumnAs 属性设置为或 `true` 。</span><span class="sxs-lookup"><span data-stu-id="31e73-136">To do so, set the ShowColumnAs property to `Histogram` or `Pareto` in the Properties window to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31e73-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="31e73-137">See Also</span></span>  
 <span data-ttu-id="31e73-138">[图表（报表生成器和 SSRS）](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="31e73-138">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="31e73-139">[图表类型（报表生成器和 SSRS）](chart-types-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="31e73-139">[Chart Types &#40;Report Builder and SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="31e73-140">[条形图（报表生成器和 SSRS）](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="31e73-140">[Bar Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="31e73-141">[范围图（报表生成器和 SSRS）](range-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="31e73-141">[Range Charts &#40;Report Builder and SSRS&#41;](range-charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="31e73-142">[教程：向报表添加条形图（报表生成器）](../tutorial-add-a-bar-chart-to-your-report-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="31e73-142">[Tutorial: Add a Bar Chart to Your Report &#40;Report Builder&#41;](../tutorial-add-a-bar-chart-to-your-report-report-builder.md) </span></span>  
 [<span data-ttu-id="31e73-143">图表中的空白和 Null 数据点（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="31e73-143">Empty and Null Data Points in Charts &#40;Report Builder and SSRS&#41;</span></span>](empty-and-null-data-points-in-charts-report-builder-and-ssrs.md)  
  
  
