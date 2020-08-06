---
title: 图表中的空点和 Null 数据点（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: faddd29d-4cc1-4c2c-8e29-d3d9918fe22a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3f0826a202969b432e53b3c57ddfe80680ba99e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682729"
---
# <a name="empty-and-null-data-points-in-charts-report-builder-and-ssrs"></a><span data-ttu-id="68a1d-102">图表中的空和 Null 数据点（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="68a1d-102">Empty and Null Data Points in Charts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="68a1d-103">如果在图表中显示具有空值或 Null 值的字段，则图表外观可能与预期不符。</span><span class="sxs-lookup"><span data-stu-id="68a1d-103">If you are displaying fields with empty or null values in your chart, the chart may not look as you expect.</span></span> <span data-ttu-id="68a1d-104">图表处理空值的方式会根据指定图表类型而改变：</span><span class="sxs-lookup"><span data-stu-id="68a1d-104">Charts process empty values differently depending on the specified chart type:</span></span>  
  
-   <span data-ttu-id="68a1d-105">如果图表类型是线性图表类型（条形图、柱形图、散点图、折线图、面积图和范围图），则空值将在该图表中显示为空格或“空白”。</span><span class="sxs-lookup"><span data-stu-id="68a1d-105">If the chart type is a linear chart type (bar, column, scatter, line, area, range), empty values are displayed as empty spaces or "gaps" in the chart.</span></span> <span data-ttu-id="68a1d-106">若要指示空点，则必须添加空点占位符。</span><span class="sxs-lookup"><span data-stu-id="68a1d-106">If you want to indicate empty points, you must add empty point placeholders.</span></span> <span data-ttu-id="68a1d-107">有关详细信息，请参阅[向图表添加空点 &#40;报表生成器和 SSRS&#41;](add-empty-points-to-a-chart-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="68a1d-107">For more information, see [Add Empty Points to the Chart &#40;Report Builder and SSRS&#41;](add-empty-points-to-a-chart-report-builder-and-ssrs.md).</span></span>  
  
-   <span data-ttu-id="68a1d-108">如果图表类型是连续线性图表类型（面积图、条形图、柱形图、折线图和散点图），则空数据点将添加到该图表中以维护序列的连续性。</span><span class="sxs-lookup"><span data-stu-id="68a1d-108">If the chart type is a contiguous, linear chart type (area, bar, column, line, scatter), empty data points are added to the chart to maintain continuity in the series.</span></span>  
  
-   <span data-ttu-id="68a1d-109">如果图表类型是非线性图表类型（极坐标图、饼图、圆环图、漏斗图或棱锥图），则空值将不显示在该图表中。</span><span class="sxs-lookup"><span data-stu-id="68a1d-109">If the chart type is a nonlinear chart type (polar, pie, doughnut, funnel or pyramid), empty values are omitted from display on the chart.</span></span>  
  
-   <span data-ttu-id="68a1d-110">在形状图表类型中，会省略 Null 值。</span><span class="sxs-lookup"><span data-stu-id="68a1d-110">In shape chart types, null values are omitted.</span></span>  
  
 <span data-ttu-id="68a1d-111">具有空数据点的图表的示例可用于示例报表。</span><span class="sxs-lookup"><span data-stu-id="68a1d-111">An example of a chart with empty data points is available as a sample report.</span></span> <span data-ttu-id="68a1d-112">有关下载此示例报表和其他内容的详细信息，请参阅 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [报表生成器和报表设计器示例报表](https://go.microsoft.com/fwlink/?LinkId=198283)。</span><span class="sxs-lookup"><span data-stu-id="68a1d-112">For more information about downloading this sample report and others, see [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][Report Builder and Report Designer sample reports](https://go.microsoft.com/fwlink/?LinkId=198283).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="removing-empty-or-null-values"></a><span data-ttu-id="68a1d-113">删除空值或 Null 值</span><span class="sxs-lookup"><span data-stu-id="68a1d-113">Removing Empty or Null Values</span></span>  
 <span data-ttu-id="68a1d-114">若要避免重要数据变得模糊，请考虑从数据集中删除空值。</span><span class="sxs-lookup"><span data-stu-id="68a1d-114">To avoid obscuring important data, consider removing empty values from your dataset.</span></span> <span data-ttu-id="68a1d-115">若要筛选 Null 值，可以在查询中使用 NOT IS NULL 子句。</span><span class="sxs-lookup"><span data-stu-id="68a1d-115">To filter nulls, you can use the NOT IS NULL clause in your query.</span></span> <span data-ttu-id="68a1d-116">或者，也可以添加指定仅显示非 0 值的筛选表达式。</span><span class="sxs-lookup"><span data-stu-id="68a1d-116">Alternatively, you can add a filtering expression that specifies that you only want to display values not equal to zero.</span></span> <span data-ttu-id="68a1d-117">有关详细信息，请参阅 [添加数据集筛选器、数据区域筛选器和组筛选器（报表生成器和 SSRS）](add-dataset-filters-data-region-filters-and-group-filters.md)。</span><span class="sxs-lookup"><span data-stu-id="68a1d-117">For more information, see [Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md).</span></span>  
  
## <a name="fields-with-no-values-in-a-chart"></a><span data-ttu-id="68a1d-118">在图表中不含值的字段</span><span class="sxs-lookup"><span data-stu-id="68a1d-118">Fields with No Values in a Chart</span></span>  
 <span data-ttu-id="68a1d-119">如果在返回的结果集中某个字段不包含任何值，则图表会显示一个没有任何数据点的空图表，但是序列名称（通常是字段名称）会添加为图例项。</span><span class="sxs-lookup"><span data-stu-id="68a1d-119">If a field does not contain any values in the returned dataset, the chart displays an empty chart with no data points, but the series name (typically the field name) is added as a legend item.</span></span>  
  
 <span data-ttu-id="68a1d-120">此行为不同于当报表已参数化并且所选值返回空结果集时，返回的数据集可能包含 0 行数据的情况。</span><span class="sxs-lookup"><span data-stu-id="68a1d-120">This behavior differs from the case where there are zero rows of data in the returned dataset, which can occur when the report is parameterized and the selected value returns an empty result set.</span></span> <span data-ttu-id="68a1d-121">如果数据集查询返回 0 行数据，在运行时系统会显示一条消息，指示没有可显示的数据。</span><span class="sxs-lookup"><span data-stu-id="68a1d-121">If your dataset query returns zero rows of data, a message is displayed at run time to indicate that no data can be shown.</span></span> <span data-ttu-id="68a1d-122">通过在“属性”窗格中修改该报表的 NoDataMessage 标题可以自定义此消息  。</span><span class="sxs-lookup"><span data-stu-id="68a1d-122">You can customize this message by modifying the NoDataMessage caption for the report in the **Properties** pane.</span></span> <span data-ttu-id="68a1d-123">有关详细信息，请参阅 [报表的嵌入数据集和共享数据集（报表生成器和 SSRS）](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="68a1d-123">For more information, see [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68a1d-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="68a1d-124">See Also</span></span>  
 <span data-ttu-id="68a1d-125">[图表 &#40;报表生成器和 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="68a1d-125">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="68a1d-126">[设置图表格式 &#40;报表生成器和 SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="68a1d-126">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="68a1d-127">[向报表添加图表 &#40;报表生成器和 SSRS&#41;](add-a-chart-to-a-report-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="68a1d-127">[Add a Chart to a Report &#40;Report Builder and SSRS&#41;](add-a-chart-to-a-report-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="68a1d-128">图表故障排除（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="68a1d-128">Troubleshoot Charts &#40;Report Builder and SSRS&#41;</span></span>](troubleshoot-charts-report-builder-and-ssrs.md)  
  
  
