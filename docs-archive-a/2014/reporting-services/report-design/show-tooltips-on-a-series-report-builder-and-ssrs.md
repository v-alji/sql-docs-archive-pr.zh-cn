---
title: 在序列上显示工具提示（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4c9606ff-e1c3-4cf7-a4e7-bb16f1a9e8ab
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9113ec843b3b9255f380b17ee1ab6b360fa1f60d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590044"
---
# <a name="show-tooltips-on-a-series-report-builder-and-ssrs"></a><span data-ttu-id="ff9b3-102">在序列上显示工具提示（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="ff9b3-102">Show ToolTips on a Series (Report Builder and SSRS)</span></span>
  <span data-ttu-id="ff9b3-103">可以向图表的序列上的每个数据点添加工具提示，以显示与数据点有关的信息，例如，用户将光标悬停在所呈现报表中的数据点上时，会显示组名、数据点的值，或数据点相对于序列总计的百分比。</span><span class="sxs-lookup"><span data-stu-id="ff9b3-103">You can add a ToolTip to each data point on the series of a chart to display information related to the data point, such as the group name, the value of the data point, or the percentage of the data point relative to the series total when users hover over the data point in a rendered report.</span></span>  
  
 <span data-ttu-id="ff9b3-104">无法向计算序列添加工具提示。</span><span class="sxs-lookup"><span data-stu-id="ff9b3-104">You cannot add a ToolTip to a calculated series.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-specify-a-tooltip-on-each-data-point"></a><span data-ttu-id="ff9b3-105">指定关于每个数据点的工具提示</span><span class="sxs-lookup"><span data-stu-id="ff9b3-105">To specify a ToolTip on each data point</span></span>  
  
1.  <span data-ttu-id="ff9b3-106">右键单击序列，或右键单击“值”区域中的字段，并单击“序列属性”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ff9b3-106">Right-click on the series or right-click on the field in the **Values** area, and click **Series Properties**.</span></span>  
  
2.  <span data-ttu-id="ff9b3-107">单击 **“序列数据”** ，并为 **“工具提示”** 属性键入字符串或表达式。</span><span class="sxs-lookup"><span data-stu-id="ff9b3-107">Click **Series Data** and, for the **ToolTip** property, type in a string or expression.</span></span> <span data-ttu-id="ff9b3-108">可以使用任何特定于图表的关键字来表示图表上的另一个元素。</span><span class="sxs-lookup"><span data-stu-id="ff9b3-108">You can use any chart-specific keyword to represent another element on the chart.</span></span> <span data-ttu-id="ff9b3-109">有关详细信息，请参阅 [设置图表上数据点的格式（报表生成器和 SSRS）](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="ff9b3-109">For more information, see [Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff9b3-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ff9b3-110">See Also</span></span>  
 <span data-ttu-id="ff9b3-111">[设置图表上数据点的格式 &#40;报表生成器和 SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ff9b3-111">[Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ff9b3-112">[更改图例项 &#40;报表生成器和 SSRS 的文本&#41;](chart-legend-change-item-text-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="ff9b3-112">[Change the Text of a Legend Item &#40;Report Builder and SSRS&#41;](chart-legend-change-item-text-report-builder.md) </span></span>  
 <span data-ttu-id="ff9b3-113">[设置图表上序列颜色的格式 &#40;报表生成器和 SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ff9b3-113">[Formatting Series Colors on a Chart &#40;Report Builder and SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="ff9b3-114">在报表中添加钻取操作（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="ff9b3-114">Add a Drillthrough Action on a Report &#40;Report Builder and SSRS&#41;</span></span>](add-a-drillthrough-action-on-a-report-report-builder-and-ssrs.md)  
  
  
