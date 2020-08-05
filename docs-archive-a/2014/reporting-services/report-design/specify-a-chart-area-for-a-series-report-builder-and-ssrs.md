---
title: 指定序列的图表区域（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10157"
- sql12.rtp.rptdesigner.chartareaproperties.alignment.f1
ms.assetid: dc3c365b-c263-402a-bf6f-c2a7081db073
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 483bc6d2fa4aa079c95e9dbd03e18c71d7b13abf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577265"
---
# <a name="specify-a-chart-area-for-a-series-report-builder-and-ssrs"></a><span data-ttu-id="60858-102">指定序列的图表区（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="60858-102">Specify a Chart Area for a Series (Report Builder and SSRS)</span></span>
  <span data-ttu-id="60858-103">图表为包括外部边框、图表标题和图例的顶级容器。</span><span class="sxs-lookup"><span data-stu-id="60858-103">The chart is the top-level container that includes the outer border, the chart title, and the legend.</span></span> <span data-ttu-id="60858-104">默认情况下，图表包含一个默认图表区。</span><span class="sxs-lookup"><span data-stu-id="60858-104">By default, the chart contains one default chart area.</span></span> <span data-ttu-id="60858-105">图表区在图表表面上不可见，但您可将图表区当作只包含轴标签、轴标题和一个或多个序列的绘图区的容器。</span><span class="sxs-lookup"><span data-stu-id="60858-105">The chart area is not visible on the chart surface, but you can think of the chart area as a container that encompasses only the axis labels, the axis title and the plotting area of one or more series.</span></span> <span data-ttu-id="60858-106">下图说明了单个图表中的图表区的概念。</span><span class="sxs-lookup"><span data-stu-id="60858-106">The following illustration shows the concept of chart areas within a single chart.</span></span>  
  
 <span data-ttu-id="60858-107">![显示图表区域关系图](../media/chartareasdiagram.gif "显示图表区域关系图")</span><span class="sxs-lookup"><span data-stu-id="60858-107">![Shows a diagram of a chart area](../media/chartareasdiagram.gif "Shows a diagram of a chart area")</span></span>  
  
 <span data-ttu-id="60858-108">默认情况下，所有序列都将添加到默认图表区。</span><span class="sxs-lookup"><span data-stu-id="60858-108">By default, all series are added to the default chart area.</span></span> <span data-ttu-id="60858-109">使用面积图、柱形图、折线图和散点图时，这些序列的任何组合均可显示在同一图表区上。</span><span class="sxs-lookup"><span data-stu-id="60858-109">When using area, column, line, and scatter charts, any combination of these series can be displayed on the same chart area.</span></span> <span data-ttu-id="60858-110">如果您在同一图表区拥有多个序列，则图表的可读性将会下降。</span><span class="sxs-lookup"><span data-stu-id="60858-110">If you have several series in the same chart area, the readability of the chart is reduced.</span></span> <span data-ttu-id="60858-111">最好将图表类型分为多个图表区。</span><span class="sxs-lookup"><span data-stu-id="60858-111">You may want to separate the chart types into multiple chart areas.</span></span> <span data-ttu-id="60858-112">使用多个图表区将提高可读性以更易于进行比较。</span><span class="sxs-lookup"><span data-stu-id="60858-112">Using multiple chart areas will increase readability for easier comparisons.</span></span> <span data-ttu-id="60858-113">例如，价量股票图表通常具有不同范围的值，但可以在同一时期在价格和数量数据之间进行比较。</span><span class="sxs-lookup"><span data-stu-id="60858-113">For example, price-volume stock charts often have different ranges of values, but comparisons can be made between the price and volume data over the same period of time.</span></span>  
  
 <span data-ttu-id="60858-114">条形图序列、极坐标图序列或形状序列只能与同一图表区中相同图表类型的序列组合。</span><span class="sxs-lookup"><span data-stu-id="60858-114">The bar, polar, or shape series can only be combined with series of the same chart types in the same chart area.</span></span> <span data-ttu-id="60858-115">如果您使用极坐标图图表或形状图表，请考虑为希望显示的各个字段使用单独的图表数据区域。</span><span class="sxs-lookup"><span data-stu-id="60858-115">If you are using a Polar or Shape chart, consider using a separate chart data region for each field that you wish to show.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-associate-a-series-with-a-new-chart-area"></a><span data-ttu-id="60858-116">将序列与新的图表区相关联</span><span class="sxs-lookup"><span data-stu-id="60858-116">To associate a series with a new chart area</span></span>  
  
1.  <span data-ttu-id="60858-117">右键单击图表上的任意位置并选择“添加新图表区域”  。</span><span class="sxs-lookup"><span data-stu-id="60858-117">Right-click anywhere on the chart and select **Add New Chart Area**.</span></span> <span data-ttu-id="60858-118">图表上将出现一个新的空白图表区。</span><span class="sxs-lookup"><span data-stu-id="60858-118">A new, blank chart area appears on the chart.</span></span>  
  
2.  <span data-ttu-id="60858-119">右键单击图表上的序列或右键单击“图表数据”窗格中的相应区域中的序列或数据字段，然后单击“序列属性”  。</span><span class="sxs-lookup"><span data-stu-id="60858-119">Right-click the series on the chart or right-click a series or data field in the appropriate area in the Chart Data pane, and then click **Series Properties**.</span></span>  
  
3.  <span data-ttu-id="60858-120">在 **“轴和图表区”** 中，选择要在其中显示序列的图表区。</span><span class="sxs-lookup"><span data-stu-id="60858-120">In **Axes and Chart Areas**, select the chart area that you want the series to be shown in.</span></span>  
  
4.  <span data-ttu-id="60858-121">（可选）将图表区垂直对齐。</span><span class="sxs-lookup"><span data-stu-id="60858-121">(Optional) Align the chart areas vertically.</span></span> <span data-ttu-id="60858-122">若要执行此操作，请右键单击图表并选择“图表区域属性”  。</span><span class="sxs-lookup"><span data-stu-id="60858-122">To do this, right-click the chart and select **Chart Area Properties**.</span></span> <span data-ttu-id="60858-123">在 **“对齐”** 中，选择要将选中的图表区与其对齐的另一图表区。</span><span class="sxs-lookup"><span data-stu-id="60858-123">In **Alignment**, select another chart area that you want to align the selected chart area with.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60858-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="60858-124">See Also</span></span>  
 <span data-ttu-id="60858-125">[图表中的多个序列（报表生成器和 SSRS）](multiple-series-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="60858-125">[Multiple Series on a Chart &#40;Report Builder and SSRS&#41;](multiple-series-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="60858-126">[设置图表上数据点的格式（报表生成器和 SSRS）](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="60858-126">[Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="60858-127">[使用调色板定义图表上的颜色（报表生成器和 SSRS）](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="60858-127">[Define Colors on a Chart Using a Palette &#40;Report Builder and SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="60858-128">[极坐标图（报表生成器和 SSRS）](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="60858-128">[Polar Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="60858-129">[形状图（报表生成器和 SSRS）](shape-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="60858-129">[Shape Charts &#40;Report Builder and SSRS&#41;](shape-charts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="60858-130">饼图&#40;报表生成器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="60858-130">Pie Charts &#40;Report Builder and SSRS&#41;</span></span>](pie-charts-report-builder-and-ssrs.md)  
  
  
