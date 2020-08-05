---
title: 指定轴间隔（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ae46712d-a5bf-44c0-9929-e30ccc1e7e33
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 70b64b824933753a8482360f193ca4ccf71e8d52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577262"
---
# <a name="specify-an-axis-interval-report-builder-and-ssrs"></a><span data-ttu-id="1bb5d-102">指定轴间隔（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="1bb5d-102">Specify an Axis Interval (Report Builder and SSRS)</span></span>
  <span data-ttu-id="1bb5d-103">轴间隔用于定义坐标轴上的标签和附带的刻度线的数目。</span><span class="sxs-lookup"><span data-stu-id="1bb5d-103">The axis interval defines the number of labels and accompanying tick marks on an axis.</span></span> <span data-ttu-id="1bb5d-104">在值轴上，轴间隔提供图表上数据点的一致度量。</span><span class="sxs-lookup"><span data-stu-id="1bb5d-104">On the value axis, axis intervals provide a consistent measure of the data points on the chart.</span></span> <span data-ttu-id="1bb5d-105">但是，在类别轴上，此功能会导致显示不带轴标签的类别。</span><span class="sxs-lookup"><span data-stu-id="1bb5d-105">However, on the category axis, this functionality can cause categories to appear without axis labels.</span></span> <span data-ttu-id="1bb5d-106">可以在轴 Interval 属性中指定所需间隔数。</span><span class="sxs-lookup"><span data-stu-id="1bb5d-106">You can specify the number of intervals you want in the axis Interval property.</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="1bb5d-107">根据结果集中的数据在运行时计算间隔数。</span><span class="sxs-lookup"><span data-stu-id="1bb5d-107">calculates the number of intervals at run time, based on the data in the result set.</span></span> <span data-ttu-id="1bb5d-108">有关轴间隔的计算方式的详细信息，请参阅[设置图表上轴标签的格式（报表生成器和 SSRS）](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="1bb5d-108">For more information about how axis intervals are calculated, see [Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="1bb5d-109">本主题不适用于类别轴上的日期或时间值。</span><span class="sxs-lookup"><span data-stu-id="1bb5d-109">This topic is not applicable for date or time values on the category axis.</span></span> <span data-ttu-id="1bb5d-110">默认情况下，`DateTime` 值显示为天数。</span><span class="sxs-lookup"><span data-stu-id="1bb5d-110">Be default, `DateTime` values appear as days.</span></span> <span data-ttu-id="1bb5d-111">若要指定不同的日期或时间间隔，如月份或时间间隔，必须设置轴标签的格式并将该轴设置为显示 `DateTime` 类型而不是 `String` 类型的实例。</span><span class="sxs-lookup"><span data-stu-id="1bb5d-111">To specify a different date or time interval, such as a month or time interval, you must format the axis labels and set the axis to display instances of `DateTime` types instead of `String` types.</span></span> <span data-ttu-id="1bb5d-112">此外，必须设置 Interval 属性。</span><span class="sxs-lookup"><span data-stu-id="1bb5d-112">In addition, you must set the Interval property.</span></span> <span data-ttu-id="1bb5d-113">有关详细信息，请参阅[将轴标签的格式设置为日期或货币（报表生成器和 SSRS）](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="1bb5d-113">For more information, see [Format Axis Labels as Dates or Currencies &#40;Report Builder and SSRS&#41;](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="1bb5d-114">本主题不适用于饼图、圆环图、漏斗图或棱锥图，因为这些图表没有轴。</span><span class="sxs-lookup"><span data-stu-id="1bb5d-114">This topic does not apply to pie, doughnut, funnel or pyramid charts, which do not have axes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1bb5d-115">类别轴通常是水平轴（或 x 轴）。</span><span class="sxs-lookup"><span data-stu-id="1bb5d-115">The category axis is usually the horizontal or x-axis.</span></span> <span data-ttu-id="1bb5d-116">但对于条形图来说，类别轴是指垂直轴（或 y 轴）。</span><span class="sxs-lookup"><span data-stu-id="1bb5d-116">However, for bar charts, the category axis is the vertical or y-axis.</span></span>  
  
 <span data-ttu-id="1bb5d-117">指定不同轴间隔的图表的示例可用于示例报表。</span><span class="sxs-lookup"><span data-stu-id="1bb5d-117">An example of a chart specifying different axis intervals is available as a sample report.</span></span> <span data-ttu-id="1bb5d-118">有关下载此示例报表和其他内容的详细信息，请参阅 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [报表生成器和报表设计器示例报表](https://go.microsoft.com/fwlink/?LinkId=198283)。</span><span class="sxs-lookup"><span data-stu-id="1bb5d-118">For more information about downloading this sample report and others, see [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][Report Builder and Report Designer sample reports](https://go.microsoft.com/fwlink/?LinkId=198283).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-show-all-category-labels-on-the-x-axis"></a><span data-ttu-id="1bb5d-119">在 X 轴上显示所有类别标签</span><span class="sxs-lookup"><span data-stu-id="1bb5d-119">To show all category labels on the x-axis</span></span>  
  
1.  <span data-ttu-id="1bb5d-120">右键单击类别轴，然后单击 **“轴属性”**。</span><span class="sxs-lookup"><span data-stu-id="1bb5d-120">Right-click the category axis and click **Axis Properties**.</span></span> <span data-ttu-id="1bb5d-121">随即会打开 **“轴属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="1bb5d-121">The **Axis Properties** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="1bb5d-122">在 "**轴选项**" 中，将设置 `Interval` 为**1**。</span><span class="sxs-lookup"><span data-stu-id="1bb5d-122">In **Axis Options**, set `Interval` to **1**.</span></span> <span data-ttu-id="1bb5d-123">随即显示每个类别组标签。</span><span class="sxs-lookup"><span data-stu-id="1bb5d-123">Every category group label is displayed.</span></span> <span data-ttu-id="1bb5d-124">如果希望在 X 轴上显示所有其他类别组标签，请键入 **2**。</span><span class="sxs-lookup"><span data-stu-id="1bb5d-124">If you want to show every other category group label on the x-axis, type **2**.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
    > [!NOTE]  
    >  <span data-ttu-id="1bb5d-125">设置轴间隔后，将禁用所有自动标签。</span><span class="sxs-lookup"><span data-stu-id="1bb5d-125">When an axis interval is set, all automatic labeling is disabled.</span></span> <span data-ttu-id="1bb5d-126">如果指定轴间隔的值，则可能会遇到不可知的标签行为，具体取决于类别轴上的类别数。</span><span class="sxs-lookup"><span data-stu-id="1bb5d-126">If you specify a value for the axis interval, you may experience unpredictable labeling behavior depending on how many categories are on the category axis.</span></span>  
  
### <a name="to-enable-a-variable-interval-calculation-on-an-axis"></a><span data-ttu-id="1bb5d-127">启用轴上的可变间隔计算</span><span class="sxs-lookup"><span data-stu-id="1bb5d-127">To enable a variable interval calculation on an axis</span></span>  
  
1.  <span data-ttu-id="1bb5d-128">右键单击要更改的图表轴，然后单击 **“轴属性”**。</span><span class="sxs-lookup"><span data-stu-id="1bb5d-128">Right-click the chart axis that you want to change, and then click **Axis Properties**.</span></span> <span data-ttu-id="1bb5d-129">随即会打开 **“轴属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="1bb5d-129">The **Axis Properties** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="1bb5d-130">在 "**轴选项**" 中，将设置 `Interval` 为 "**自动**"。该图表将显示可沿该轴容纳的最佳类别标签数。</span><span class="sxs-lookup"><span data-stu-id="1bb5d-130">In **Axis Options**, set `Interval` to **Auto**. The chart will display the optimal number of category labels that can fit along the axis.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1bb5d-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1bb5d-131">See Also</span></span>  
 <span data-ttu-id="1bb5d-132">[设置图表格式 &#40;报表生成器和 SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1bb5d-132">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="1bb5d-133">[设置图表上数据点的格式 &#40;报表生成器和 SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1bb5d-133">[Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="1bb5d-134">[对数据区域中的数据进行排序 &#40;报表生成器和 SSRS&#41;](sort-data-in-a-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1bb5d-134">[Sort Data in a Data Region &#40;Report Builder and SSRS&#41;](sort-data-in-a-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="1bb5d-135">["轴属性" 对话框-"轴选项" &#40;报表生成器和 SSRS&#41;](../axis-properties-dialog-box-axis-options-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1bb5d-135">[Axis Properties Dialog Box, Axis Options &#40;Report Builder and SSRS&#41;](../axis-properties-dialog-box-axis-options-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="1bb5d-136">[指定对数刻度 &#40;报表生成器和 SSRS&#41;](specify-a-logarithmic-scale-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1bb5d-136">[Specify a Logarithmic Scale &#40;Report Builder and SSRS&#41;](specify-a-logarithmic-scale-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="1bb5d-137">在辅助轴上绘制数据（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="1bb5d-137">Plot Data on a Secondary Axis &#40;Report Builder and SSRS&#41;</span></span>](plot-data-on-a-secondary-axis-report-builder-and-ssrs.md)  
  
  
