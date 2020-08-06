---
title: 在饼图上显示百分比值（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: eb905fc1-5235-4773-a27e-b07be9318be5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2dee9017d34f2751b790b2e4928571160b597f1d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586433"
---
# <a name="display-percentage-values-on-a-pie-chart-report-builder-and-ssrs"></a><span data-ttu-id="f0b3d-102">在饼图上显示百分比值（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="f0b3d-102">Display Percentage Values on a Pie Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="f0b3d-103">默认情况下，图例中显示了类别来标识每个值。</span><span class="sxs-lookup"><span data-stu-id="f0b3d-103">By default, categories are shown in the legend to identify each value.</span></span> <span data-ttu-id="f0b3d-104">如果使用了类别标签标记饼图，则可能希望在图例中显示百分比。</span><span class="sxs-lookup"><span data-stu-id="f0b3d-104">If you have labeled the pie chart using category labels, you may want show percentages in the legend.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-display-percentage-values-as-labels-on-a-pie-chart"></a><span data-ttu-id="f0b3d-105">在饼图上显示百分比值</span><span class="sxs-lookup"><span data-stu-id="f0b3d-105">To display percentage values as labels on a pie chart</span></span>  
  
1.  <span data-ttu-id="f0b3d-106">向报表添加一个饼图。</span><span class="sxs-lookup"><span data-stu-id="f0b3d-106">Add a pie chart to your report.</span></span> <span data-ttu-id="f0b3d-107">有关详细信息，请参阅[向报表添加图表（报表生成器和 SSRS）](add-a-chart-to-a-report-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="f0b3d-107">For more information, see [Add a Chart to a Report &#40;Report Builder and SSRS&#41;](add-a-chart-to-a-report-report-builder-and-ssrs.md).</span></span>  
  
2.  <span data-ttu-id="f0b3d-108">在设计图面上，右键单击饼图并选择“ **显示数据标签**”。</span><span class="sxs-lookup"><span data-stu-id="f0b3d-108">On the design surface, right-click on the pie and select **Show Data Labels**.</span></span> <span data-ttu-id="f0b3d-109">数据标签应显示在饼图上的每个切片上。</span><span class="sxs-lookup"><span data-stu-id="f0b3d-109">The data labels should appear within each slice on the pie chart.</span></span>  
  
3.  <span data-ttu-id="f0b3d-110">在设计图面上，右键单击标签并选择“ **序列标签属性**”。</span><span class="sxs-lookup"><span data-stu-id="f0b3d-110">On the design surface, right-click on the labels and select **Series Label Properties**.</span></span> <span data-ttu-id="f0b3d-111">此时将显示 **“序列标签属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="f0b3d-111">The **Series Label Properties** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="f0b3d-112">`#PERCENT`"**标签数据**" 选项的类型。</span><span class="sxs-lookup"><span data-stu-id="f0b3d-112">Type `#PERCENT` for the **Label data** option.</span></span>  
  
5.  <span data-ttu-id="f0b3d-113">（可选）若要指定标签显示的小数位数，请键入“#PERCENT{P*n*}”，其中 *n* 为要显示的小数位数。</span><span class="sxs-lookup"><span data-stu-id="f0b3d-113">(Optional) To specify how many decimal places the label shows, type "#PERCENT{P*n*}" where *n* is the number of decimal places to display.</span></span> <span data-ttu-id="f0b3d-114">例如，若不显示小数位数，请键入“#PERCENT{P0}”。</span><span class="sxs-lookup"><span data-stu-id="f0b3d-114">For example, to display no decimal places, type "#PERCENT{P0}".</span></span>  
  
### <a name="to-display-percentage-values-in-the-legend-of-a-pie-chart"></a><span data-ttu-id="f0b3d-115">在饼图的图例中显示百分比值</span><span class="sxs-lookup"><span data-stu-id="f0b3d-115">To display percentage values in the legend of a pie chart</span></span>  
  
1.  <span data-ttu-id="f0b3d-116">在设计图面上，右键单击饼图并选择“ **序列属性**”。</span><span class="sxs-lookup"><span data-stu-id="f0b3d-116">On the design surface, right-click on the pie chart and select **Series Properties**.</span></span> <span data-ttu-id="f0b3d-117">此时将显示 **“序列属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="f0b3d-117">The **Series Properties** dialog box displays.</span></span>  
  
2.  <span data-ttu-id="f0b3d-118">在 "**图例**" 的 `#PERCENT` "**自定义图例文本**" 属性中键入。</span><span class="sxs-lookup"><span data-stu-id="f0b3d-118">In **Legend**, type `#PERCENT` for the **Custom legend text** property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0b3d-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f0b3d-119">See Also</span></span>  
 <span data-ttu-id="f0b3d-120">[饼图 &#40;报表生成器和 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f0b3d-120">[Pie Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f0b3d-121">[设置图表上图例的格式 &#40;报表生成器和 SSRS&#41;](chart-legend-formatting-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="f0b3d-121">[Formatting the Legend on a Chart &#40;Report Builder and SSRS&#41;](chart-legend-formatting-report-builder.md) </span></span>  
 <span data-ttu-id="f0b3d-122">[在饼图外显示数据点标签 &#40;报表生成器和 SSRS&#41;](display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f0b3d-122">[Display Data Point Labels Outside a Pie Chart &#40;Report Builder and SSRS&#41;](display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="f0b3d-123">收集饼图上的小切片（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="f0b3d-123">Collect Small Slices on a Pie Chart &#40;Report Builder and SSRS&#41;</span></span>](collect-small-slices-on-a-pie-chart-report-builder-and-ssrs.md)  
  
  
