---
title: 在图表中添加或删除边距（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 91c43f58-5771-4d33-a54d-0e802d2f5cba
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9d8bad99591964540bcd14fc5609560a3d324515
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691093"
---
# <a name="add-or-remove-margins-from-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="feb36-102">在图表中添加或删除边距（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="feb36-102">Add or Remove Margins from a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="feb36-103">在柱形图和散点图中，图表会自动在 x 轴结尾处添加侧边距。</span><span class="sxs-lookup"><span data-stu-id="feb36-103">In Column and Scatter chart types, the chart automatically adds side margins on the ends of the x-axis.</span></span> <span data-ttu-id="feb36-104">在条形图中，图表会自动在 y 轴结尾处添加侧边距。</span><span class="sxs-lookup"><span data-stu-id="feb36-104">In Bar chart types, the chart automatically adds side margins on the ends of the y-axis.</span></span> <span data-ttu-id="feb36-105">在所有其他图表类型中，图表都不会添加侧边距。</span><span class="sxs-lookup"><span data-stu-id="feb36-105">In all other chart types, the chart does not add side margins.</span></span> <span data-ttu-id="feb36-106">您无法更改该边距的大小。</span><span class="sxs-lookup"><span data-stu-id="feb36-106">You cannot change the size of the margin.</span></span>  
  
 <span data-ttu-id="feb36-107">本主题不适用于饼图、圆环图、漏斗图或棱锥图类型。</span><span class="sxs-lookup"><span data-stu-id="feb36-107">This topic does not apply to pie, doughnut, funnel, or pyramid chart types.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-enable-or-disable-side-margins"></a><span data-ttu-id="feb36-108">启用或禁用侧边距</span><span class="sxs-lookup"><span data-stu-id="feb36-108">To enable or disable side margins</span></span>  
  
1.  <span data-ttu-id="feb36-109">右键单击轴，然后选择“轴属性”  。</span><span class="sxs-lookup"><span data-stu-id="feb36-109">Right-click the axis and select **Axis Properties**.</span></span> <span data-ttu-id="feb36-110">将显示“垂直轴属性”  或“水平轴属性”  对话框。</span><span class="sxs-lookup"><span data-stu-id="feb36-110">The **Vertical** or **HorizontalAxis Properties** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="feb36-111">在 **“轴选项”** 页中，设置 **“侧边距”** 属性：</span><span class="sxs-lookup"><span data-stu-id="feb36-111">On the **Axis Options** page, set the **Side margins** property:</span></span>  
  
    -   <span data-ttu-id="feb36-112">**自动** 图表将基于图表类型确定是否添加侧边距。</span><span class="sxs-lookup"><span data-stu-id="feb36-112">**Auto** The chart will determine whether to add a side margin based on the chart type.</span></span>  
  
    -   <span data-ttu-id="feb36-113">**已禁用** 条形图、柱形图和散点图将不具有侧边距。</span><span class="sxs-lookup"><span data-stu-id="feb36-113">**Disabled** Bar, column, and scatter charts will have no side margins.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="feb36-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="feb36-114">See Also</span></span>  
 <span data-ttu-id="feb36-115">[设置图表上轴标签的格式（报表生成器和 SSRS）](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="feb36-115">[Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="feb36-116">[“轴属性”对话框 ->“轴选项”（报表生成器和 SSRS）](../axis-properties-dialog-box-axis-options-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="feb36-116">[Axis Properties Dialog Box, Axis Options &#40;Report Builder and SSRS&#41;](../axis-properties-dialog-box-axis-options-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="feb36-117">[指定轴间隔（报表生成器和 SSRS）](specify-an-axis-interval-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="feb36-117">[Specify an Axis Interval &#40;Report Builder and SSRS&#41;](specify-an-axis-interval-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="feb36-118">[将轴标签的格式设置为日期或货币（报表生成器和 SSRS）](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="feb36-118">[Format Axis Labels as Dates or Currencies &#40;Report Builder and SSRS&#41;](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="feb36-119">图表&#40;报表生成器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="feb36-119">Charts &#40;Report Builder and SSRS&#41;</span></span>](charts-report-builder-and-ssrs.md)  
  
  
