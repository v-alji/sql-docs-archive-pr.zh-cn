---
title: 隐藏图表上的图例项（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 92256240-0cd5-4be4-8904-d1e3b93cb6b3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 20444432f580ffaf1c5f4de1320b06319f973a01
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590057"
---
# <a name="hide-legend-items-on-the-chart-report-builder-and-ssrs"></a><span data-ttu-id="4bb64-102">隐藏图表上的图例项（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="4bb64-102">Hide Legend Items on the Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="4bb64-103">默认情况下，添加到非形状图的任何序列将在图例中添加为图例项。</span><span class="sxs-lookup"><span data-stu-id="4bb64-103">By default, any series added to a non-Shape chart will be added as an item in the legend.</span></span> <span data-ttu-id="4bb64-104">对于饼图、圆环图、漏斗图和棱锥图，添加到图表的任何序列将在图例中添加单个数据点。</span><span class="sxs-lookup"><span data-stu-id="4bb64-104">For pie, doughnut, funnel, and pyramid charts, any series added to the chart will add individual data points in the legend.</span></span>  
  
 <span data-ttu-id="4bb64-105">您可以隐藏图例中的任何项。</span><span class="sxs-lookup"><span data-stu-id="4bb64-105">You can hide any item on the legend.</span></span> <span data-ttu-id="4bb64-106">隐藏图例项时，该项仍将在图表中显示。</span><span class="sxs-lookup"><span data-stu-id="4bb64-106">When you hide a legend item, it will still appear in the chart.</span></span> <span data-ttu-id="4bb64-107">当您不希望显示添加到图表的序列的详细信息时，上述功能非常有用。</span><span class="sxs-lookup"><span data-stu-id="4bb64-107">This is useful in situations where you do not want to show more information for a series that is added to the chart.</span></span> <span data-ttu-id="4bb64-108">例如，如果已将计算序列（如移动平均值）添加到图表，可能需要在图例中隐藏该条目，以便仅显示原始序列的详细信息。</span><span class="sxs-lookup"><span data-stu-id="4bb64-108">For example, if you have added a calculated series like a moving average to the chart, you may want to hide this entry in the legend so that more information is only shown for the original series.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-hide-an-item-from-display-in-the-legend"></a><span data-ttu-id="4bb64-109">在图例中隐藏项</span><span class="sxs-lookup"><span data-stu-id="4bb64-109">To hide an item from display in the legend</span></span>  
  
1.  <span data-ttu-id="4bb64-110">右键单击要隐藏的序列，并选择“序列属性”  。</span><span class="sxs-lookup"><span data-stu-id="4bb64-110">Right-click on the series you want to hide and select **Series Properties**.</span></span>  
  
2.  <span data-ttu-id="4bb64-111">单击 **“图例”** 。</span><span class="sxs-lookup"><span data-stu-id="4bb64-111">Click **Legend**.</span></span> <span data-ttu-id="4bb64-112">选择 **“不在图例中显示此序列”** 选项。</span><span class="sxs-lookup"><span data-stu-id="4bb64-112">Select the **Do not show this series in a legend** option.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4bb64-113">不能仅针对一个组隐藏序列，而对其他组显示该序列。</span><span class="sxs-lookup"><span data-stu-id="4bb64-113">You cannot hide a series for one group and not for the others.</span></span> <span data-ttu-id="4bb64-114">如果将字段添加到 **“序列组”** 区域中，将隐藏该组所包含的所有序列。</span><span class="sxs-lookup"><span data-stu-id="4bb64-114">If you have added a field to the **Series Groups** area, all series belonging to this group will be hidden.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bb64-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4bb64-115">See Also</span></span>  
 <span data-ttu-id="4bb64-116">[设置图表上图例的格式（报表生成器和 SSRS）](chart-legend-formatting-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="4bb64-116">[Formatting the Legend on a Chart &#40;Report Builder and SSRS&#41;](chart-legend-formatting-report-builder.md) </span></span>  
 <span data-ttu-id="4bb64-117">[设置图表上数据点的格式（报表生成器和 SSRS）](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4bb64-117">[Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4bb64-118">[更改图例项的文本（报表生成器和 SSRS）](chart-legend-change-item-text-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="4bb64-118">[Change the Text of a Legend Item &#40;Report Builder and SSRS&#41;](chart-legend-change-item-text-report-builder.md) </span></span>  
 <span data-ttu-id="4bb64-119">[向图表添加移动平均线（报表生成器和 SSRS）](add-a-moving-average-to-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4bb64-119">[Add a Moving Average to a Chart &#40;Report Builder and SSRS&#41;](add-a-moving-average-to-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="4bb64-120">“图例属性”对话框 ->“常规”（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="4bb64-120">Legend Properties Dialog Box, General &#40;Report Builder and SSRS&#41;</span></span>](../legend-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  
