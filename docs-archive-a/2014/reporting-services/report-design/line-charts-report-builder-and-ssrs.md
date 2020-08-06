---
title: 折线图（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 194e6679-890d-4a3e-a756-130d32ef7e29
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 44e7a011186e66e6b8bdc8b5dd31939c883e320b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692702"
---
# <a name="line-charts-report-builder-and-ssrs"></a><span data-ttu-id="57cfd-102">折线图（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="57cfd-102">Line Charts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="57cfd-103">折线图将序列显示为一组由单个线条连接的点。</span><span class="sxs-lookup"><span data-stu-id="57cfd-103">A line chart displays a series as a set of points connected by a single line.</span></span> <span data-ttu-id="57cfd-104">折线图用于表示在一段连续时间内发生的大量数据。</span><span class="sxs-lookup"><span data-stu-id="57cfd-104">Line charts are used to representing large amounts of data that occur over a continuous period of time.</span></span> <span data-ttu-id="57cfd-105">有关如何向折线图添加数据的详细信息，请参阅 [图表（报表生成器和 SSRS）](charts-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="57cfd-105">For more information about how to add data to a line chart, see [Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="57cfd-106">下图显示了一个包含三个序列的折线图。</span><span class="sxs-lookup"><span data-stu-id="57cfd-106">The following illustration shows a line chart that contains three series.</span></span>  
  
 <span data-ttu-id="57cfd-107">![折线图](../media/rs-linechart.gif "折线图")</span><span class="sxs-lookup"><span data-stu-id="57cfd-107">![Line chart](../media/rs-linechart.gif "Line chart")</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations"></a><span data-ttu-id="57cfd-108">变体</span><span class="sxs-lookup"><span data-stu-id="57cfd-108">Variations</span></span>  
  
-   <span data-ttu-id="57cfd-109">**平滑线图**。</span><span class="sxs-lookup"><span data-stu-id="57cfd-109">**Smooth line**.</span></span> <span data-ttu-id="57cfd-110">一种使用曲线而不是规则线条的折线图。</span><span class="sxs-lookup"><span data-stu-id="57cfd-110">A line chart that uses a curved line instead of a regular line.</span></span>  
  
-   <span data-ttu-id="57cfd-111">**渐变线图**。</span><span class="sxs-lookup"><span data-stu-id="57cfd-111">**Stepped line**.</span></span> <span data-ttu-id="57cfd-112">一种使用渐变线而不是规则线条的折线图。</span><span class="sxs-lookup"><span data-stu-id="57cfd-112">A line chart that uses a stepped line instead of a regular line.</span></span> <span data-ttu-id="57cfd-113">渐变线图通过使用一种线条来连接各点，这种线条使渐变线图看起来像阶梯或楼梯的梯级一样。</span><span class="sxs-lookup"><span data-stu-id="57cfd-113">The stepped line connects points by using a line that makes it look like steps on a ladder or staircase.</span></span>  
  
-   <span data-ttu-id="57cfd-114">**迷你图**。</span><span class="sxs-lookup"><span data-stu-id="57cfd-114">**Sparkline charts**.</span></span> <span data-ttu-id="57cfd-115">迷你图是折线图的变体，它仅在 Tablix 或矩阵的单元中显示线条序列。</span><span class="sxs-lookup"><span data-stu-id="57cfd-115">Variations of the line chart that show only the line series in the cell of a table or matrix.</span></span> <span data-ttu-id="57cfd-116">有关详细信息，请参阅 [迷你图和数据条（报表生成器和 SSRS）](sparklines-and-data-bars-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="57cfd-116">For more information, see [Sparklines and Data Bars &#40;Report Builder and SSRS&#41;](sparklines-and-data-bars-report-builder-and-ssrs.md).</span></span>  
  
## <a name="data-considerations-for-line-charts"></a><span data-ttu-id="57cfd-117">折线图的数据注意事项</span><span class="sxs-lookup"><span data-stu-id="57cfd-117">Data Considerations for Line Charts</span></span>  
  
-   <span data-ttu-id="57cfd-118">为了改善默认折线图的视觉效果，请考虑将序列边框的宽度更改为 3，然后增加阴影偏移量 1。</span><span class="sxs-lookup"><span data-stu-id="57cfd-118">To improve the visual impact of the default line chart, consider changing the width of the series border to 3, and adding a shadow offset of 1.</span></span> <span data-ttu-id="57cfd-119">这样，所生成折线图的线条会粗得多。</span><span class="sxs-lookup"><span data-stu-id="57cfd-119">This will create a much bolder line chart.</span></span> <span data-ttu-id="57cfd-120">如果将图表类型从“折线图”更改为其他类型，则需要将这些属性恢复为其原始值。</span><span class="sxs-lookup"><span data-stu-id="57cfd-120">You will need to revert these properties to their original values if you change the chart type from Line to another type.</span></span>  
  
-   <span data-ttu-id="57cfd-121">如果数据集包含空值，则折线图将以占位符线的形式添加空点，以便保持图表上的连续性。</span><span class="sxs-lookup"><span data-stu-id="57cfd-121">If your dataset includes empty values, the line chart will add empty points, in the form of placeholder lines, in order to maintain continuity on the chart.</span></span> <span data-ttu-id="57cfd-122">如果不希望看到这些占位符线，请考虑使用非连续图表类型（如条形图或柱形图）来显示数据集。</span><span class="sxs-lookup"><span data-stu-id="57cfd-122">If you would rather not see these lines, consider displaying your dataset using a non-contiguous chart type such as a bar or column chart.</span></span>  
  
-   <span data-ttu-id="57cfd-123">折线图需要至少两个点才能绘制线条。</span><span class="sxs-lookup"><span data-stu-id="57cfd-123">A line chart requires at least two points to draw a line.</span></span>  <span data-ttu-id="57cfd-124">如果数据集只有一个数据点，则折线图将显示为一个数据点标记。</span><span class="sxs-lookup"><span data-stu-id="57cfd-124">If your dataset has only one data point, the line chart will display as a single data point marker.</span></span>  
  
-   <span data-ttu-id="57cfd-125">绘制成线条的序列并不会在图表区占太大空间。</span><span class="sxs-lookup"><span data-stu-id="57cfd-125">A series that is drawn as a line will not take up much space within a chart area.</span></span>  <span data-ttu-id="57cfd-126">因此，折线图经常与其他图表类型（如柱形图）结合使用。</span><span class="sxs-lookup"><span data-stu-id="57cfd-126">For this reason, line charts are frequently combined with other chart types such as column charts.</span></span> <span data-ttu-id="57cfd-127">但是，折线图不能与条形图、极坐标图、饼图或形状图等图表类型结合使用。</span><span class="sxs-lookup"><span data-stu-id="57cfd-127">However, you cannot combine a line chart with bar, polar, pie or shape chart types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57cfd-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="57cfd-128">See Also</span></span>  
 <span data-ttu-id="57cfd-129">[条形图（报表生成器和 SSRS）](bar-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="57cfd-129">[Bar Charts &#40;Report Builder and SSRS&#41;](bar-charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="57cfd-130">[柱形图（报表生成器和 SSRS）](column-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="57cfd-130">[Column Charts &#40;Report Builder and SSRS&#41;](column-charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="57cfd-131">[图表（报表生成器和 SSRS）](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="57cfd-131">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="57cfd-132">[图表类型（报表生成器和 SSRS）](chart-types-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="57cfd-132">[Chart Types &#40;Report Builder and SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="57cfd-133">[分区图（报表生成器和 SSRS）](area-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="57cfd-133">[Area Charts &#40;Report Builder and SSRS&#41;](area-charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="57cfd-134">[图表中的空点和 Null 数据点（报表生成器和 SSRS）](empty-and-null-data-points-in-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="57cfd-134">[Empty and Null Data Points in Charts &#40;Report Builder and SSRS&#41;](empty-and-null-data-points-in-charts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="57cfd-135">图表&#40;报表生成器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="57cfd-135">Charts &#40;Report Builder and SSRS&#41;</span></span>](charts-report-builder-and-ssrs.md)  
  
  
