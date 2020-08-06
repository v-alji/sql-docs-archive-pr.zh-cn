---
title: 在图表中添加刻度分隔线（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 84d66436-ed62-4967-bbbd-b457593ee787
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1c081debd1e0a84158615edebdb6b84705c10e5b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691086"
---
# <a name="add-scale-breaks-to-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="f3a80-102">在图表中添加刻度分隔线（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="f3a80-102">Add Scale Breaks to a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="f3a80-103">刻度分隔线是在图表的绘图区绘制的一个条带，表示值轴（通常为垂直轴或 Y 轴）上高值和低值之间的一个中断。</span><span class="sxs-lookup"><span data-stu-id="f3a80-103">A scale break is a stripe drawn across the plotting area of a chart to denote a break in continuity between the high and low values on a value axis (usually the vertical, or y-axis).</span></span> <span data-ttu-id="f3a80-104">使用刻度分隔线可以在同一图表区中显示两个不同范围。</span><span class="sxs-lookup"><span data-stu-id="f3a80-104">Use a scale break to display two distinct ranges in the same chart area.</span></span>  
  
 <span data-ttu-id="f3a80-105">![具有刻度分割线的图表](../media/rs-multipledatarangeschart-scalebreak.gif "具有刻度分割线的图表")</span><span class="sxs-lookup"><span data-stu-id="f3a80-105">![Chart with scale break](../media/rs-multipledatarangeschart-scalebreak.gif "Chart with scale break")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f3a80-106">您不能指定在图表中放置刻度分隔线的位置。</span><span class="sxs-lookup"><span data-stu-id="f3a80-106">You cannot specify where to place a scale break on your chart.</span></span> <span data-ttu-id="f3a80-107">图表根据数据集中的值使用自有的计算方法确定数据范围之间是否有足够的分离空间，以便在运行时的值轴（Y 轴）上绘制刻度分隔线。</span><span class="sxs-lookup"><span data-stu-id="f3a80-107">The chart uses its own calculations based on the values in your dataset to determine whether there is sufficient separation between data ranges to draw a scale break on the value axis (y-axis) at run time.</span></span>  
  
 <span data-ttu-id="f3a80-108">具有刻度分隔线的图表的示例可用于示例报表。</span><span class="sxs-lookup"><span data-stu-id="f3a80-108">An example of a chart with scale breaks is available as a sample report.</span></span> <span data-ttu-id="f3a80-109">有关下载此示例报表和其他内容的详细信息，请参阅 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [报表生成器和报表设计器示例报表](https://go.microsoft.com/fwlink/?LinkId=198283)。</span><span class="sxs-lookup"><span data-stu-id="f3a80-109">For more information about downloading this sample report and others, see [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][Report Builder and Report Designer sample reports](https://go.microsoft.com/fwlink/?LinkId=198283).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-enable-scale-breaks-on-the-chart"></a><span data-ttu-id="f3a80-110">启用图表中的刻度分隔线</span><span class="sxs-lookup"><span data-stu-id="f3a80-110">To enable scale breaks on the chart</span></span>  
  
1.  <span data-ttu-id="f3a80-111">右键单击垂直轴，然后单击“轴属性”  。</span><span class="sxs-lookup"><span data-stu-id="f3a80-111">Right-click the vertical axis and then click **Axis Properties**.</span></span> <span data-ttu-id="f3a80-112">随即将打开“垂直轴属性”  对话框。</span><span class="sxs-lookup"><span data-stu-id="f3a80-112">The **VerticalAxis Properties** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="f3a80-113">选中 **“启用刻度分隔线”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="f3a80-113">Select the **Enable scale breaks** check box.</span></span>  
  
### <a name="to-change-the-style-of-the-scale-break"></a><span data-ttu-id="f3a80-114">更改刻度分隔线的样式</span><span class="sxs-lookup"><span data-stu-id="f3a80-114">To change the style of the scale break</span></span>  
  
1.  <span data-ttu-id="f3a80-115">打开“属性”窗格。</span><span class="sxs-lookup"><span data-stu-id="f3a80-115">Open the Properties pane.</span></span>  
  
2.  <span data-ttu-id="f3a80-116">在设计图面上，右键单击图表中的 Y 轴。</span><span class="sxs-lookup"><span data-stu-id="f3a80-116">On the design surface, right-click on the y-axis of the chart.</span></span> <span data-ttu-id="f3a80-117">Y 轴对象（默认情况下名为“图表轴”）的属性显示在“属性”窗格中。</span><span class="sxs-lookup"><span data-stu-id="f3a80-117">The properties for the y-axis object (named Chart Axis by default) are displayed in the Properties pane.</span></span>  
  
3.  <span data-ttu-id="f3a80-118">在“刻度线”  部分，展开 ScaleBreakStyle 属性。</span><span class="sxs-lookup"><span data-stu-id="f3a80-118">In the **Scale** section, expand the ScaleBreakStyle property.</span></span>  
  
4.  <span data-ttu-id="f3a80-119">更改 ScaleBreakStyle 属性（如 BreakLineType 和 Spacing）的值。</span><span class="sxs-lookup"><span data-stu-id="f3a80-119">Change the values for ScaleBreakStyle properties, such as BreakLineType and Spacing.</span></span> <span data-ttu-id="f3a80-120">有关设置刻度分隔线属性的详细信息，请参阅[在图表中显示包含多个数据区域的序列（报表生成器和 SSRS）](displaying-a-series-with-multiple-data-ranges-on-a-chart.md)。</span><span class="sxs-lookup"><span data-stu-id="f3a80-120">For more information about scale break properties, see [Displaying a Series with Multiple Data Ranges on a Chart &#40;Report Builder and SSRS&#41;](displaying-a-series-with-multiple-data-ranges-on-a-chart.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3a80-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f3a80-121">See Also</span></span>  
 <span data-ttu-id="f3a80-122">[图表 &#40;报表生成器和 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f3a80-122">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f3a80-123">[设置图表格式 &#40;报表生成器和 SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f3a80-123">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="f3a80-124">“轴属性”对话框 -&gt;“轴选项”（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="f3a80-124">Axis Properties Dialog Box, Axis Options &#40;Report Builder and SSRS&#41;</span></span>](../axis-properties-dialog-box-axis-options-report-builder-and-ssrs.md)  
  
  
