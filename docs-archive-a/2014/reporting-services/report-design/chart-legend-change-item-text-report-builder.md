---
title: 更改图例项的文本（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 9e82fa34-17ed-494f-b25d-03dcc353a21f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0d0bb721aa0ff03a5211065111c98605cd86e971
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590064"
---
# <a name="change-the-text-of-a-legend-item-report-builder-and-ssrs"></a><span data-ttu-id="688db-102">更改图例项的文本（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="688db-102">Change the Text of a Legend Item (Report Builder and SSRS)</span></span>
  <span data-ttu-id="688db-103">在图表的“值”区域中放入一个字段时，会自动生成一个包含此字段名称的图例项。</span><span class="sxs-lookup"><span data-stu-id="688db-103">When a field is placed in the Values area of the chart, a legend item is automatically generated that contains the name of this field.</span></span> <span data-ttu-id="688db-104">对于除形状图以外的其他图表，每个图例项会连接到图表上的单个序列，而对于形状图，图例会连接到单个数据点而不是单个序列。</span><span class="sxs-lookup"><span data-stu-id="688db-104">Every legend item is connected to an individual series on the chart, with the exception of shape charts, where the legend is connected to individual data points instead of individual series.</span></span>  
  
 <span data-ttu-id="688db-105">在形状图上，可以更改图例项的文本，以便显示有关单个数据点的详细信息。</span><span class="sxs-lookup"><span data-stu-id="688db-105">On shape charts, you can change the text of a legend item to show more information about the individual data points.</span></span> <span data-ttu-id="688db-106">例如，如果要在图例中按百分比显示数据点的值，则可以使用 `#PERCENT` 等关键字。</span><span class="sxs-lookup"><span data-stu-id="688db-106">For example, if you want to show the values of the data points as percentages in the legend, you can use a keyword such as `#PERCENT`.</span></span> <span data-ttu-id="688db-107">可以一起追加 .NET Framework 格式代码和关键字，以便应用数字和日期格式。</span><span class="sxs-lookup"><span data-stu-id="688db-107">You can append .NET Framework format codes in conjunction with keywords to apply numeric and date formats.</span></span> <span data-ttu-id="688db-108">有关关键字的详细信息，请参阅[设置图表上数据点的格式（报表生成器和 SSRS）](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="688db-108">For more information about keywords, see [Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="688db-109">![清晰图表](../media/sharpchart.png "清晰图表")</span><span class="sxs-lookup"><span data-stu-id="688db-109">![Sharp Chart](../media/sharpchart.png "Sharp Chart")</span></span>  
  
 <span data-ttu-id="688db-110">在非形状图上，可以更改图例项的文本。</span><span class="sxs-lookup"><span data-stu-id="688db-110">On non-shape charts, you can change the text of a legend item.</span></span> <span data-ttu-id="688db-111">例如，如果序列名称是“Series1”，您可能希望将该文本更改为更具说明性的名称，例如“Sales for 2008”。</span><span class="sxs-lookup"><span data-stu-id="688db-111">For example, if your series name is "Series1", you may want to change the text to something more descriptive like "Sales for 2008".</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-modify-the-text-that-appears-in-the-legend-on-a-shape-chart"></a><span data-ttu-id="688db-112">修改在形状图的图例中显示的文本</span><span class="sxs-lookup"><span data-stu-id="688db-112">To modify the text that appears in the legend on a Shape chart</span></span>  
  
1.  <span data-ttu-id="688db-113">右键单击某一序列，或右键单击“值”  区域中的字段，并选择“序列属性”  。</span><span class="sxs-lookup"><span data-stu-id="688db-113">Right-click on a series, or right-click on a field in the **Values** area, and select **Series Properties**.</span></span>  
  
2.  <span data-ttu-id="688db-114">单击 **“图例”** ，并在 **“自定义图例文本”** 框中键入关键字。</span><span class="sxs-lookup"><span data-stu-id="688db-114">Click **Legend** and in the **Custom legend text** box, type a keyword.</span></span>  
  
 <span data-ttu-id="688db-115">下表提供了用于“自定义图例文本”  属性的特定于图表的关键字示例。</span><span class="sxs-lookup"><span data-stu-id="688db-115">The following table provides examples of chart-specific keywords to use for the **Custom Legend Text** property.</span></span> <span data-ttu-id="688db-116">有关关键字的详细信息，请参阅[设置图表上数据点的格式（报表生成器和 SSRS）](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="688db-116">For more information about keywords, see [Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md).</span></span>  
  
|<span data-ttu-id="688db-117">关键字</span><span class="sxs-lookup"><span data-stu-id="688db-117">Keyword</span></span>|<span data-ttu-id="688db-118">说明</span><span class="sxs-lookup"><span data-stu-id="688db-118">Description</span></span>|<span data-ttu-id="688db-119">图例中的显示文本示例</span><span class="sxs-lookup"><span data-stu-id="688db-119">Example of what appears as text in the legend</span></span>|  
|-------------|-----------------|---------------------------------------------------|  
|`#PERCENT{P1}`|<span data-ttu-id="688db-120">显示包含一个小数位的总计值百分比。</span><span class="sxs-lookup"><span data-stu-id="688db-120">Displays the percentage of the total value to one decimal place.</span></span>|<span data-ttu-id="688db-121">85.0%</span><span class="sxs-lookup"><span data-stu-id="688db-121">85.0%</span></span>|  
|`#VALY`|<span data-ttu-id="688db-122">显示数据字段的实际数值。</span><span class="sxs-lookup"><span data-stu-id="688db-122">Displays the actual numeric value of the data field.</span></span>|<span data-ttu-id="688db-123">17000</span><span class="sxs-lookup"><span data-stu-id="688db-123">17000</span></span>|  
|`#VALY{C2}`|<span data-ttu-id="688db-124">将数据字段的实际数值显示为包含两个小数位的货币。</span><span class="sxs-lookup"><span data-stu-id="688db-124">Displays the actual numeric value of the data field as a currency to two decimal places.</span></span>|<span data-ttu-id="688db-125">$17000.00</span><span class="sxs-lookup"><span data-stu-id="688db-125">$17000.00</span></span>|  
|`#AXISLABEL (#PERCENT{P0})`|<span data-ttu-id="688db-126">显示类别字段的文本表示形式，后跟每个类别在图表上显示的百分比。</span><span class="sxs-lookup"><span data-stu-id="688db-126">Displays the text representation of the category field, followed by the percentage that each category displays on the chart.</span></span>|<span data-ttu-id="688db-127">Michael Blythe (85%)</span><span class="sxs-lookup"><span data-stu-id="688db-127">Michael Blythe (85%)</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="688db-128">仅当“序列组”  区域中没有指定的字段时，才能在运行时计算 #AXISLABEL 关键字。</span><span class="sxs-lookup"><span data-stu-id="688db-128">The #AXISLABEL keyword can only be evaluated at run time when there is not a field specified in the **Series Groups** area.</span></span>  
  
### <a name="to-modify-the-text-that-appears-in-the-legend-on-a-non-shape-chart"></a><span data-ttu-id="688db-129">修改在非形状图的图例中显示的文本</span><span class="sxs-lookup"><span data-stu-id="688db-129">To modify the text that appears in the legend on a non-Shape chart</span></span>  
  
1.  <span data-ttu-id="688db-130">右键单击某一序列，或右键单击“值”  区域中的字段，并选择“序列属性”  。</span><span class="sxs-lookup"><span data-stu-id="688db-130">Right-click on a series, or right-click on a field in the **Values** area, and select **Series Properties**.</span></span>  
  
2.  <span data-ttu-id="688db-131">单击 **“图例”** ，并在 **“自定义图例文本”** 框中键入图例标签。</span><span class="sxs-lookup"><span data-stu-id="688db-131">Click **Legend** and in the **Custom legend text** box, type a legend label.</span></span> <span data-ttu-id="688db-132">随即用该文本更新序列。</span><span class="sxs-lookup"><span data-stu-id="688db-132">The series is updated with your text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="688db-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="688db-133">See Also</span></span>  
 <span data-ttu-id="688db-134">[设置图表上图例的格式（报表生成器和 SSRS）](chart-legend-formatting-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="688db-134">[Formatting the Legend on a Chart &#40;Report Builder and SSRS&#41;](chart-legend-formatting-report-builder.md) </span></span>  
 <span data-ttu-id="688db-135">[设置图表上序列颜色的格式（报表生成器和 SSRS）](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="688db-135">[Formatting Series Colors on a Chart &#40;Report Builder and SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="688db-136">隐藏图表上的图例项（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="688db-136">Hide Legend Items on the Chart &#40;Report Builder and SSRS&#41;</span></span>](chart-legend-hide-items-report-builder.md)  
  
  
