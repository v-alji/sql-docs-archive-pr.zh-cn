---
title: "\"轴属性\" 对话框-\"轴选项\" (报表生成器和 SSRS) |Microsoft Docs"
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.axisproperties.axisoptions.f1
- "10138"
ms.assetid: b276e210-7a12-48ae-971b-7dabae51df11
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a94c4de6487d111417ef7ad3cee53a4172b5d275
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586515"
---
# <a name="axis-properties-dialog-box-axis-options-report-builder-and-ssrs"></a><span data-ttu-id="ae114-102">“轴属性”对话框 ->“轴选项”（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="ae114-102">Axis Properties Dialog Box, Axis Options (Report Builder and SSRS)</span></span>
  <span data-ttu-id="ae114-103">在 "**水平**" 或 "**垂直轴属性**" 对话框中选择 "**轴选项**" 可定义图表指定轴的外观。</span><span class="sxs-lookup"><span data-stu-id="ae114-103">Select **Axis Options** on the **Horizontal** or **VerticalAxis Properties** dialog box to define the appearance of the specified axis of the chart.</span></span> <span data-ttu-id="ae114-104">在以前版本的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]中，默认情况下，图表会在 X 轴上显示所有标签。</span><span class="sxs-lookup"><span data-stu-id="ae114-104">In previous versions of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], the chart displayed all labels on the x-axis by default.</span></span> <span data-ttu-id="ae114-105">但在 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2008 中，图表会跳过一些标签，以使生成的图表更加整洁，并避免标签冲突。</span><span class="sxs-lookup"><span data-stu-id="ae114-105">However, in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 2008, the chart skips labels in order to produce a cleaner image on the chart and avoid labeling collisions.</span></span> <span data-ttu-id="ae114-106">有关详细信息，请参阅[设置图表上轴标签的格式（报表生成器和 SSRS）](report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="ae114-106">For more information, see [Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="ae114-107">选项</span><span class="sxs-lookup"><span data-stu-id="ae114-107">Options</span></span>  
 <span data-ttu-id="ae114-108">**启用小数位数分隔符**</span><span class="sxs-lookup"><span data-stu-id="ae114-108">**Enable scale breaks**</span></span>  
 <span data-ttu-id="ae114-109">选择此选项可在必要时启用图表以绘制小数位数分隔符。</span><span class="sxs-lookup"><span data-stu-id="ae114-109">Select this option to enable the chart to draw a scale breaks when it is deemed necessary.</span></span> <span data-ttu-id="ae114-110">启用此选项后，图表将自动计算数据集中高点与低点之间是否存在足够的差异以绘制小数位数分隔符。</span><span class="sxs-lookup"><span data-stu-id="ae114-110">When this option is enabled, the chart will automatically calculate whether there is sufficient difference between the high and low points in the dataset to draw a scale break.</span></span>  
  
 <span data-ttu-id="ae114-111">**反向**</span><span class="sxs-lookup"><span data-stu-id="ae114-111">**Reverse direction**</span></span>  
 <span data-ttu-id="ae114-112">选择此选项可以反转图表的方向。</span><span class="sxs-lookup"><span data-stu-id="ae114-112">Select this option to reverse the direction of the chart.</span></span> <span data-ttu-id="ae114-113">例如，默认情况下，柱形图在图表的左侧显示 Y 轴，并从左向右显示类别。</span><span class="sxs-lookup"><span data-stu-id="ae114-113">For example, by default, a column chart displays the y-axis on the left side of the chart and categories from left to right.</span></span> <span data-ttu-id="ae114-114">选择了此选项后，图表将在其右侧显示 Y 轴并从右向左显示类别。</span><span class="sxs-lookup"><span data-stu-id="ae114-114">When this option is selected, the chart displays the y-axis on the right side of the chart and categories from right to left.</span></span>  
  
 <span data-ttu-id="ae114-115">**使用交错颜色**</span><span class="sxs-lookup"><span data-stu-id="ae114-115">**Use interlacing color**</span></span>  
 <span data-ttu-id="ae114-116">选择此选项以将条带线添加到图表中，然后选择一种颜色或键入表达式。</span><span class="sxs-lookup"><span data-stu-id="ae114-116">Select this option to add strip lines to the chart, and then select a color or type an expression.</span></span> <span data-ttu-id="ae114-117">条带线是图表区域的阴影带，可在网格线之间形成明暗交错的区域。</span><span class="sxs-lookup"><span data-stu-id="ae114-117">Strip lines are shaded bands on the chart area that give the effect of alternating light and dark areas between gridlines.</span></span> <span data-ttu-id="ae114-118">这些条带线对于突出显示轴上的重复样式非常有用。</span><span class="sxs-lookup"><span data-stu-id="ae114-118">These strip lines are useful for highlighting repeating patterns on an axis.</span></span>  
  
 <span data-ttu-id="ae114-119">**始终包括零**</span><span class="sxs-lookup"><span data-stu-id="ae114-119">**Always include zero**</span></span>  
 <span data-ttu-id="ae114-120">选择此选项可以在轴刻度上始终包括零。</span><span class="sxs-lookup"><span data-stu-id="ae114-120">Select this option to always include zero on the axis scale.</span></span> <span data-ttu-id="ae114-121">如果此选项未启用，则图表不会在轴上标记零值。</span><span class="sxs-lookup"><span data-stu-id="ae114-121">If this option is not enabled, the chart will not label the zero value on the axis.</span></span> <span data-ttu-id="ae114-122">包括零值在数据集包含负值或零值时将非常有用。</span><span class="sxs-lookup"><span data-stu-id="ae114-122">Including zero values is useful when the dataset includes negative or zero values.</span></span>  
  
 <span data-ttu-id="ae114-123">**标量轴**</span><span class="sxs-lookup"><span data-stu-id="ae114-123">**Scalar axis**</span></span>  
 <span data-ttu-id="ae114-124">选择此选项可以在连续刻度上显示一组轴值。</span><span class="sxs-lookup"><span data-stu-id="ae114-124">Select this option to display a set of axis values on a continuous scale.</span></span> <span data-ttu-id="ae114-125">例如，如果数据集包含一月、三月和十一月的数据，则非标量轴仅显示这些月份，而标量轴将显示一年中的所有月份。</span><span class="sxs-lookup"><span data-stu-id="ae114-125">For example, if the dataset contains data for January, March, and November, a non-scalar axis displays only those months, whereas a scalar axis displays all of the months in the year.</span></span>  
  
 <span data-ttu-id="ae114-126">**使用对数刻度**</span><span class="sxs-lookup"><span data-stu-id="ae114-126">**Use logarithmic scale**</span></span>  
 <span data-ttu-id="ae114-127">选择此选项以指示轴刻度为对数刻度。</span><span class="sxs-lookup"><span data-stu-id="ae114-127">Select this option to indicate that the axis scale is logarithmic.</span></span> <span data-ttu-id="ae114-128">当轴包含正的数值时，此选项仅能用于 Y 轴。</span><span class="sxs-lookup"><span data-stu-id="ae114-128">This option is available only on the y-axis if the axis contains positive numeric values.</span></span>  
  
 <span data-ttu-id="ae114-129">当轴设置为使用对数刻度时，在框中键入要使用的对数底数。</span><span class="sxs-lookup"><span data-stu-id="ae114-129">In the box, type the logarithmic base to use when the axis is set to use a logarithmic scale.</span></span> <span data-ttu-id="ae114-130">默认情况下，图表对轴的对数刻度使用底数 10。</span><span class="sxs-lookup"><span data-stu-id="ae114-130">By default, the chart uses a base of 10 for the logarithmic scale of an axis.</span></span> <span data-ttu-id="ae114-131">当轴是数轴时，此选项仅能用于 Y 轴。</span><span class="sxs-lookup"><span data-stu-id="ae114-131">This option is available only on the y-axis if the axis is numeric.</span></span>  
  
 <span data-ttu-id="ae114-132">**最低**</span><span class="sxs-lookup"><span data-stu-id="ae114-132">**Minimum**</span></span>  
 <span data-ttu-id="ae114-133">键入一个表示 X 轴最小值的表达式或值。</span><span class="sxs-lookup"><span data-stu-id="ae114-133">Type an expression or a value for the minimum value for the x-axis.</span></span> <span data-ttu-id="ae114-134">如果省略此参数，最小值将由数据集返回的数据决定。</span><span class="sxs-lookup"><span data-stu-id="ae114-134">If omitted, the minimum value is determined by the data returned by the dataset.</span></span>  
  
 <span data-ttu-id="ae114-135">最大值</span><span class="sxs-lookup"><span data-stu-id="ae114-135">**Maximum**</span></span>  
 <span data-ttu-id="ae114-136">键入一个表示 X 轴最大值的表达式或值。</span><span class="sxs-lookup"><span data-stu-id="ae114-136">Type an expression or a value for the maximum value for the x-axis.</span></span> <span data-ttu-id="ae114-137">如果省略此参数，最大值将由数据集返回的数据决定。</span><span class="sxs-lookup"><span data-stu-id="ae114-137">If omitted, the maximum value is determined by the data returned by the dataset.</span></span>  
  
 <span data-ttu-id="ae114-138">**时间间隔**</span><span class="sxs-lookup"><span data-stu-id="ae114-138">**Interval**</span></span>  
 <span data-ttu-id="ae114-139">键入表示轴标签之间间隔的表达式或值。</span><span class="sxs-lookup"><span data-stu-id="ae114-139">Type an expression or value for the interval between axis labels.</span></span> <span data-ttu-id="ae114-140">例如，键入 1 将在轴上显示每个类别标签。</span><span class="sxs-lookup"><span data-stu-id="ae114-140">For example, type 1 to display each category label on the axis.</span></span> <span data-ttu-id="ae114-141">键入 2 将每隔一个类别标签显示一次。</span><span class="sxs-lookup"><span data-stu-id="ae114-141">Type 2 to display every other category label.</span></span> <span data-ttu-id="ae114-142">如果省略，则将基于数据集中的值自动计算标签。</span><span class="sxs-lookup"><span data-stu-id="ae114-142">If omitted, the labels are calculated automatically based on the values in the dataset.</span></span>  
  
 <span data-ttu-id="ae114-143">**间隔类型**</span><span class="sxs-lookup"><span data-stu-id="ae114-143">**Interval type**</span></span>  
 <span data-ttu-id="ae114-144">键入表示指定间隔的间隔类型的表达式或值。</span><span class="sxs-lookup"><span data-stu-id="ae114-144">Type an expression or a value for the interval type of the interval specified.</span></span> <span data-ttu-id="ae114-145">例如，如果希望间隔为两天，则需指定间隔为 **2** ，间隔类型为 **天** 。</span><span class="sxs-lookup"><span data-stu-id="ae114-145">For example, if you want the interval to be two days, you will specify **2** for interval and **Days** for interval type.</span></span>  
  
 <span data-ttu-id="ae114-146">**侧边距**</span><span class="sxs-lookup"><span data-stu-id="ae114-146">**Side margins**</span></span>  
 <span data-ttu-id="ae114-147">键入一个表达式或选择一个值，以添加或去除图表元素与图表边之间的边距。</span><span class="sxs-lookup"><span data-stu-id="ae114-147">Type an expression or select a value to add or remove a margin between the chart elements and the sides of the chart.</span></span> <span data-ttu-id="ae114-148">如果将此选项设置为 **“自动”**，则会添加侧边距。</span><span class="sxs-lookup"><span data-stu-id="ae114-148">If this option is set to **Auto**, a side margins are added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae114-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ae114-149">See Also</span></span>  
 <span data-ttu-id="ae114-150">[设置图表上轴标签的格式 &#40;报表生成器和 SSRS&#41;](report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ae114-150">[Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ae114-151">[图表 &#40;报表生成器和 SSRS&#41;](report-design/charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ae114-151">[Charts &#40;Report Builder and SSRS&#41;](report-design/charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ae114-152">[设置图表上序列颜色的格式 &#40;报表生成器和 SSRS&#41;](report-design/formatting-series-colors-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ae114-152">[Formatting Series Colors on a Chart &#40;Report Builder and SSRS&#41;](report-design/formatting-series-colors-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ae114-153">[指定轴间隔 &#40;报表生成器和 SSRS&#41;](report-design/specify-an-axis-interval-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ae114-153">[Specify an Axis Interval &#40;Report Builder and SSRS&#41;](report-design/specify-an-axis-interval-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ae114-154">[将轴标签的格式设置为日期或货币 &#40;报表生成器和 SSRS&#41;](report-design/format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ae114-154">[Format Axis Labels as Dates or Currencies &#40;Report Builder and SSRS&#41;](report-design/format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ae114-155">[&#40;报表生成器和 SSRS 在辅助轴上绘制数据&#41;](report-design/plot-data-on-a-secondary-axis-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ae114-155">[Plot Data on a Secondary Axis &#40;Report Builder and SSRS&#41;](report-design/plot-data-on-a-secondary-axis-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ae114-156">[迷你图和数据条 &#40;报表生成器和 SSRS&#41;](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ae114-156">[Sparklines and Data Bars &#40;Report Builder and SSRS&#41;](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="ae114-157">在图表中添加或删除边距（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="ae114-157">Add or Remove Margins from a Chart &#40;Report Builder and SSRS&#41;</span></span>](report-design/add-or-remove-margins-from-a-chart-report-builder-and-ssrs.md)  
  
  
