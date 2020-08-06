---
title: 收集饼图上的小切片（报表生成器和 SSRS） | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 21c2b8cb-b9ca-4bc0-bf49-50ba432562f6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2302217843864115847aeb544d1c64727b8ad3a1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587199"
---
# <a name="collect-small-slices-on-a-pie-chart-report-builder-and-ssrs"></a><span data-ttu-id="11c69-102">收集饼图上的小切片（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="11c69-102">Collect Small Slices on a Pie Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="11c69-103">饼图显示太多数据点时，这些数据点会显得混乱。</span><span class="sxs-lookup"><span data-stu-id="11c69-103">When pie charts display too many points of data, they begin to look cluttered.</span></span> <span data-ttu-id="11c69-104">若要解决此问题，可以将低于特定值的所有数据显示为饼图的一个切片。</span><span class="sxs-lookup"><span data-stu-id="11c69-104">To resolve this issue, you can show all data that falls beneath a certain value as one slice on the pie chart.</span></span>  
  
 <span data-ttu-id="11c69-105">若要将若干小切片收集到一个切片中，请先确定用于收集小切片的阈值以饼图的百分比度量或为固定值。</span><span class="sxs-lookup"><span data-stu-id="11c69-105">To collect small slices into one slice, first decide whether your threshold for collecting small slices is measured as a percentage of the pie chart or as a fixed value.</span></span> <span data-ttu-id="11c69-106">然后设置 CollectedThreshold 和 CollectedThresholdUsePercent 属性。将 CollectedThreshold 属性设置为某个值必须低至可以进行收集的图表百分比，或者设置为用于收集的实际阈值数据值。</span><span class="sxs-lookup"><span data-stu-id="11c69-106">Then set the CollectedThreshold and CollectedThresholdUsePercent properties.Set the CollectedThreshold property to either the percentage of the chart that a value must fall below to be collected, or the actual threshold data value for collection.</span></span> <span data-ttu-id="11c69-107">将 CollectedThresholdUsePercent 属性设置为 `True` 以使用百分比或 `False` 使用实际值。</span><span class="sxs-lookup"><span data-stu-id="11c69-107">Set the CollectedThresholdUsePercent property to `True` to use a percentage or `False` to use an actual value.</span></span>  
  
 <span data-ttu-id="11c69-108">还可以将小切片收集到第一个饼图的收集切片标注的辅助饼图中。</span><span class="sxs-lookup"><span data-stu-id="11c69-108">You can also collect small slices into a second pie chart that is called out from a collected slice of the first pie chart.</span></span> <span data-ttu-id="11c69-109">该辅助饼图绘制在原始饼图的右侧。</span><span class="sxs-lookup"><span data-stu-id="11c69-109">The second pie chart is drawn to the right of the original pie chart.</span></span>  
  
 <span data-ttu-id="11c69-110">不能将漏斗图或棱锥图的切片组合到一个切片。</span><span class="sxs-lookup"><span data-stu-id="11c69-110">You cannot combine slices of funnel or pyramid charts into one slice.</span></span>  
  
 <span data-ttu-id="11c69-111">此图表的示例可用于示例报表。</span><span class="sxs-lookup"><span data-stu-id="11c69-111">An example of this chart is available as a sample report.</span></span> <span data-ttu-id="11c69-112">有关下载此示例报表和其他内容的详细信息，请参阅 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [报表生成器和报表设计器示例报表](https://go.microsoft.com/fwlink/?LinkId=198283)。</span><span class="sxs-lookup"><span data-stu-id="11c69-112">For more information about downloading this sample report and others, see [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][Report Builder and Report Designer sample reports](https://go.microsoft.com/fwlink/?LinkId=198283).</span></span>  
  
### <a name="to-collect-small-slices-into-a-single-slice-on-a-pie-chart"></a><span data-ttu-id="11c69-113">将小切片收集到饼图上的一个切片中</span><span class="sxs-lookup"><span data-stu-id="11c69-113">To collect small slices into a single slice on a pie chart</span></span>  
  
1.  <span data-ttu-id="11c69-114">打开“属性”窗格。</span><span class="sxs-lookup"><span data-stu-id="11c69-114">Open the Properties pane.</span></span>  
  
2.  <span data-ttu-id="11c69-115">在设计图面上，单击饼图的任一切片。</span><span class="sxs-lookup"><span data-stu-id="11c69-115">On the design surface, click on any slice of the pie chart.</span></span> <span data-ttu-id="11c69-116">序列的属性将显示在“属性”窗格中。</span><span class="sxs-lookup"><span data-stu-id="11c69-116">The properties for the series are displayed in the Properties pane.</span></span>  
  
3.  <span data-ttu-id="11c69-117">在 **“常规”** 部分，展开 **CustomAttributes** 节点。</span><span class="sxs-lookup"><span data-stu-id="11c69-117">In the **General** section, expand the **CustomAttributes** node.</span></span>  
  
4.  <span data-ttu-id="11c69-118">将“CollectedStyle”属性设置为“SingleSlice”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="11c69-118">Set the CollectedStyle property to **SingleSlice**.</span></span>  
  
5.  <span data-ttu-id="11c69-119">设置收集的阈值和阈值的类型。</span><span class="sxs-lookup"><span data-stu-id="11c69-119">Set the collected threshold value and type of threshold.</span></span> <span data-ttu-id="11c69-120">以下示例是收集阈值的常见设置方法。</span><span class="sxs-lookup"><span data-stu-id="11c69-120">The following examples are common ways of setting collected thresholds.</span></span>  
  
    -   <span data-ttu-id="11c69-121">**按百分比。**</span><span class="sxs-lookup"><span data-stu-id="11c69-121">**By percentage.**</span></span> <span data-ttu-id="11c69-122">例如，若要将饼图上少于 10% 的切片收集到一个切片：</span><span class="sxs-lookup"><span data-stu-id="11c69-122">For example, to collect any slice on your pie chart that is less than 10% into a single slice:</span></span>  
  
         <span data-ttu-id="11c69-123">将 CollectedThresholdUsePercent 属性设置为 `True` 。</span><span class="sxs-lookup"><span data-stu-id="11c69-123">Set the CollectedThresholdUsePercent property to `True`.</span></span>  
  
         <span data-ttu-id="11c69-124">将 CollectedThreshold 属性设置为 **10**。</span><span class="sxs-lookup"><span data-stu-id="11c69-124">Set the CollectedThreshold property to **10**.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="11c69-125">如果将 CollectedStyle 设置为**SingleSlice**，将 CollectedThreshold 设置为大于**100**的值，并且 CollectedThresholdUsePercent 为 `True` ，则图表将引发异常，因为它无法计算百分比。</span><span class="sxs-lookup"><span data-stu-id="11c69-125">If you set CollectedStyle to **SingleSlice**, CollectedThreshold to a value greater than **100**, and CollectedThresholdUsePercent is `True`, the chart will throw an exception because it cannot calculate a percentage.</span></span> <span data-ttu-id="11c69-126">若要解决此问题，请将 CollectedThreshold 设置为小于 **100** 的值。</span><span class="sxs-lookup"><span data-stu-id="11c69-126">To resolve this issue, set the CollectedThreshold to a value less than **100**.</span></span>  
  
    -   <span data-ttu-id="11c69-127">**按数据值。**</span><span class="sxs-lookup"><span data-stu-id="11c69-127">**By data value.**</span></span> <span data-ttu-id="11c69-128">例如，若要将饼图上少于 5000 的切片收集到一个切片：</span><span class="sxs-lookup"><span data-stu-id="11c69-128">For example, to collect any slice on your pie chart that is less than 5000 into a single slice:</span></span>  
  
         <span data-ttu-id="11c69-129">将 CollectedThresholdUsePercent 属性设置为 `False` 。</span><span class="sxs-lookup"><span data-stu-id="11c69-129">Set the CollectedThresholdUsePercent property to `False`.</span></span>  
  
         <span data-ttu-id="11c69-130">将 CollectedThreshold 属性设置为 **5000**。</span><span class="sxs-lookup"><span data-stu-id="11c69-130">Set the CollectedThreshold property to **5000**.</span></span>  
  
6.  <span data-ttu-id="11c69-131">将 CollectedLabel 属性设置为字符串，该字符串表示将在收集的切片上显示的文本标签。</span><span class="sxs-lookup"><span data-stu-id="11c69-131">Set the CollectedLabel property to a string that represents the text label that will be shown on the collected slice.</span></span>  
  
7.  <span data-ttu-id="11c69-132">（可选）设置 CollectedSliceExploded、CollectedColor、CollectedLegendText 和 CollectedToolTip 属性。</span><span class="sxs-lookup"><span data-stu-id="11c69-132">(Optional) Set the CollectedSliceExploded, CollectedColor, CollectedLegendText and CollectedToolTip properties.</span></span> <span data-ttu-id="11c69-133">这些属性可更改一个切片的外观、颜色、标签文本、图例文本和工具提示方面。</span><span class="sxs-lookup"><span data-stu-id="11c69-133">These properties change the appearance, color, label text, legend text and tooltip aspects of the single slice.</span></span>  
  
### <a name="to-collect-small-slices-into-a-secondary-callout-pie-chart"></a><span data-ttu-id="11c69-134">将小切片收集到辅助标注饼图中</span><span class="sxs-lookup"><span data-stu-id="11c69-134">To collect small slices into a secondary, callout pie chart</span></span>  
  
1.  <span data-ttu-id="11c69-135">请执行以上 1 - 3 步骤。</span><span class="sxs-lookup"><span data-stu-id="11c69-135">Follow Steps 1-3 from above.</span></span>  
  
2.  <span data-ttu-id="11c69-136">将 CollectedStyle 属性设置为 **CollectedPie**。</span><span class="sxs-lookup"><span data-stu-id="11c69-136">Set the CollectedStyle property to **CollectedPie**.</span></span>  
  
3.  <span data-ttu-id="11c69-137">将 CollectedThreshold 属性设置为一个值，该值表示将小切片收集成一个切片的阈值。</span><span class="sxs-lookup"><span data-stu-id="11c69-137">Set the CollectedThresholdproperty to a value that represents the threshold at which small slices will be collected into one slice.</span></span> <span data-ttu-id="11c69-138">如果将 CollectedStyle 属性设置为**CollectedPie**，则 CollectedThresholdUsePercentproperty 始终设置为 `True` ，并且收集的阈值始终按百分比度量。</span><span class="sxs-lookup"><span data-stu-id="11c69-138">When the CollectedStyle property is set to **CollectedPie**, the CollectedThresholdUsePercentproperty is always set to `True`, and the collected threshold is always measured in percent.</span></span>  
  
4.  <span data-ttu-id="11c69-139">（可选）设置 CollectedColor、CollectedLabel、CollectedLegendText 和 CollectedToolTip 属性。</span><span class="sxs-lookup"><span data-stu-id="11c69-139">(Optional) Set the CollectedColor, CollectedLabel, CollectedLegendText and CollectedToolTip properties.</span></span> <span data-ttu-id="11c69-140">所有名为“Collected”的其他属性都不适用于收集的切片。</span><span class="sxs-lookup"><span data-stu-id="11c69-140">All other properties named "Collected" do not apply to the collected pie.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="11c69-141">辅助饼图是根据您数据中的小切片计算的，因此将仅在“预览”中显示。</span><span class="sxs-lookup"><span data-stu-id="11c69-141">The secondary pie chart is calculated based on the small slices in your data so it will only appear in Preview.</span></span> <span data-ttu-id="11c69-142">它不显示在设计图面上。</span><span class="sxs-lookup"><span data-stu-id="11c69-142">It does not appear on the design surface.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="11c69-143">您不能设置辅助饼图的格式。</span><span class="sxs-lookup"><span data-stu-id="11c69-143">You cannot format the secondary pie chart.</span></span> <span data-ttu-id="11c69-144">因此，强烈建议使用第一种方法收集饼图切片。</span><span class="sxs-lookup"><span data-stu-id="11c69-144">For this reason, it is strongly recommended to use the first approach when collecting pie slices.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11c69-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="11c69-145">See Also</span></span>  
 <span data-ttu-id="11c69-146">[饼图 &#40;报表生成器和 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="11c69-146">[Pie Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="11c69-147">[设置图表上数据点的格式 &#40;报表生成器和 SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="11c69-147">[Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="11c69-148">[在饼图外显示数据点标签 &#40;报表生成器和 SSRS&#41;](display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="11c69-148">[Display Data Point Labels Outside a Pie Chart &#40;Report Builder and SSRS&#41;](display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="11c69-149">[在饼图上显示百分比值 &#40;报表生成器和 SSRS&#41;](display-percentage-values-on-a-pie-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="11c69-149">[Display Percentage Values on a Pie Chart &#40;Report Builder and SSRS&#41;](display-percentage-values-on-a-pie-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="11c69-150">向图表添加三维效果（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="11c69-150">Add 3D Effects to a Chart &#40;Report Builder and SSRS&#41;</span></span>](chart-effects-add-3d-effects-report-builder.md)  
  
  
