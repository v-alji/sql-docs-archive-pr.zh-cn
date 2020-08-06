---
title: 为数据区域设置“无数据”消息（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4b194714-46f7-4f0e-9632-7f89d9600762
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9ed38ef14eb8f89753b4b3d7af3324ef0e88fa52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688591"
---
# <a name="set-a-no-data-message-for-a-data-region-report-builder-and-ssrs"></a><span data-ttu-id="a1238-102">为数据区域设置“无数据”消息（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="a1238-102">Set a No Data Message for a Data Region (Report Builder and SSRS)</span></span>
  <span data-ttu-id="a1238-103">如果希望指定在呈现的报表中所显示的文本来代替没有数据的数据区域，请为表、矩阵或列表数据区域设置 NoRowsMessage 属性，为图表数据区域设置 NoDataMessage 属性，以及为地图的色阶设置 NoDataText 属性。</span><span class="sxs-lookup"><span data-stu-id="a1238-103">When you want to specify text to show in the rendered report in place of a data region that has no data, set the NoRowsMessage property for a table, matrix, or list data region, the NoDataMessage for a chart data region, and the NoDataText for the color scale for a map.</span></span> <span data-ttu-id="a1238-104">运行时，报表处理器会针对报表中每个数据集运行查询，并且该数据集查询可能不生成结果集。</span><span class="sxs-lookup"><span data-stu-id="a1238-104">At run time, the report processor runs the query for each dataset in a report and the dataset query may produce no result set.</span></span> <span data-ttu-id="a1238-105">对于绑定到空数据集的数据区域，可以指定显示文本，而不是显示空数据区域。</span><span class="sxs-lookup"><span data-stu-id="a1238-105">For a data region bound to an empty dataset, you can specify text to display instead of displaying an empty data region.</span></span> <span data-ttu-id="a1238-106">如果在运行时子报表的数据集中没有数据，则还可以设置子报表的 NoRowsMessage 属性。</span><span class="sxs-lookup"><span data-stu-id="a1238-106">You can also set the NoRowsMessage property for a subreport when no datasets in the subreport have data at run time.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-set-the-norowsmessage-property-for-a-table-matrix-or-list"></a><span data-ttu-id="a1238-107">设置表、矩阵或列表的 NoRowsMessage 属性</span><span class="sxs-lookup"><span data-stu-id="a1238-107">To set the NoRowsMessage property for a table, matrix, or list</span></span>  
  
1.  <span data-ttu-id="a1238-108">在“设计”视图中，单击设计图面上的表、矩阵或列表数据区域或子报表以将其选中。</span><span class="sxs-lookup"><span data-stu-id="a1238-108">In Design view, click the table, matrix, or list data region or subreport on the design surface to select it.</span></span> <span data-ttu-id="a1238-109">“属性”窗格将显示选定项的属性。</span><span class="sxs-lookup"><span data-stu-id="a1238-109">The Properties pane displays the properties for the selected item.</span></span>  
  
2.  <span data-ttu-id="a1238-110">在 "属性" 窗格中，在 "属性" 字段中键入要显示为消息的文本 `NoRowsMessage` 。</span><span class="sxs-lookup"><span data-stu-id="a1238-110">In the Properties pane, type the text that you want to display as a message in `NoRowsMessage` property field.</span></span>  
  
     <span data-ttu-id="a1238-111">此外，也可以在下拉列表中单击“表达式”以打开“表达式”对话框并创建表达式   。</span><span class="sxs-lookup"><span data-stu-id="a1238-111">Alternatively, from the drop-down list, click **Expression** to open the **Expression** dialog box and create an expression.</span></span>  
  
### <a name="to-set-the-nodatamessage-property-for-a-chart"></a><span data-ttu-id="a1238-112">设置图表的 NoDataMessage 属性</span><span class="sxs-lookup"><span data-stu-id="a1238-112">To set the NoDataMessage property for a chart</span></span>  
  
1.  <span data-ttu-id="a1238-113">在“设计”视图中，单击并选中设计图面上的图表。</span><span class="sxs-lookup"><span data-stu-id="a1238-113">In Design view, click the chart on the design surface to select it.</span></span> <span data-ttu-id="a1238-114">“属性”窗格将显示选定项的属性。</span><span class="sxs-lookup"><span data-stu-id="a1238-114">The Properties pane displays the properties for the selected item.</span></span>  
  
2.  <span data-ttu-id="a1238-115">在 "属性" 窗格中，展开的节点 `NoDataMessage` 。</span><span class="sxs-lookup"><span data-stu-id="a1238-115">In the Properties pane, expand the node for `NoDataMessage`.</span></span>  
  
3.  <span data-ttu-id="a1238-116">在 "**标题**" 中，在 "属性" 字段中键入要显示为消息的文本 `NoDataMessage` 。</span><span class="sxs-lookup"><span data-stu-id="a1238-116">In **Caption**, type the text that you want to display as a message in `NoDataMessage` property field.</span></span>  
  
     <span data-ttu-id="a1238-117">此外，也可以在下拉列表中单击“表达式”以打开“表达式”对话框并创建表达式   。</span><span class="sxs-lookup"><span data-stu-id="a1238-117">Alternatively, from the drop-down list, click **Expression** to open the **Expression** dialog box and create an expression.</span></span>  
  
### <a name="to-set-the-norowsmessage-for-a-subreport"></a><span data-ttu-id="a1238-118">设置子报表的 NoRowsMessage</span><span class="sxs-lookup"><span data-stu-id="a1238-118">To set the NoRowsMessage for a subreport</span></span>  
  
1.  <span data-ttu-id="a1238-119">在“设计”视图中，单击并选中设计图面上的子报表。</span><span class="sxs-lookup"><span data-stu-id="a1238-119">In Design view, click the subreport on the design surface to select it.</span></span> <span data-ttu-id="a1238-120">“属性”窗格将显示选定项的属性。</span><span class="sxs-lookup"><span data-stu-id="a1238-120">The Properties pane displays the properties for the selected item.</span></span>  
  
2.  <span data-ttu-id="a1238-121">在 "属性" 窗格中，在 "属性" 字段中键入要显示为消息的文本 `NoRowsMessage` 。</span><span class="sxs-lookup"><span data-stu-id="a1238-121">In the Properties pane, type the text that you want to display as a message in `NoRowsMessage` property field.</span></span>  
  
     <span data-ttu-id="a1238-122">此外，也可以在下拉列表中单击“表达式”以打开“表达式”对话框并创建表达式   。</span><span class="sxs-lookup"><span data-stu-id="a1238-122">Alternatively, from the drop-down list, click **Expression** to open the **Expression** dialog box and create an expression.</span></span>  
  
### <a name="to-set-the-nodatatext-property-for-a-color-scale-for-a-map"></a><span data-ttu-id="a1238-123">设置地图色阶的 NoDataText 属性</span><span class="sxs-lookup"><span data-stu-id="a1238-123">To set the NoDataText property for a color scale for a map</span></span>  
  
1.  <span data-ttu-id="a1238-124">在“设计”视图中，单击地图上的色阶以将其选中。</span><span class="sxs-lookup"><span data-stu-id="a1238-124">In Design view, click the color scale on the map to select it.</span></span> <span data-ttu-id="a1238-125">“属性”窗格将显示选定项的属性。</span><span class="sxs-lookup"><span data-stu-id="a1238-125">The Properties pane displays the properties for the selected item.</span></span>  
  
2.  <span data-ttu-id="a1238-126">在的 "属性" 窗格中， `NoDataText` 键入要显示为没有数据值的颜色的标签的文本。</span><span class="sxs-lookup"><span data-stu-id="a1238-126">In the Properties pane, in `NoDataText`, type the text that you want to display as a label for colors with no data value.</span></span>  
  
     <span data-ttu-id="a1238-127">此外，也可以在下拉列表中单击“表达式”以打开“表达式”对话框并创建表达式   。</span><span class="sxs-lookup"><span data-stu-id="a1238-127">Alternatively, from the drop-down list, click **Expression** to open the **Expression** dialog box and create an expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1238-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a1238-128">See Also</span></span>  
 <span data-ttu-id="a1238-129">[子报表（报表生成器和 SSRS）](../report-design/subreports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a1238-129">[Subreports &#40;Report Builder and SSRS&#41;](../report-design/subreports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a1238-130">[表、矩阵和列表（报表生成器和 SSRS）](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a1238-130">[Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a1238-131">[图表（报表生成器和 SSRS）](../report-design/charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a1238-131">[Charts &#40;Report Builder and SSRS&#41;](../report-design/charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a1238-132">[地图（报表生成器和 SSRS）](../report-design/maps-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a1238-132">[Maps &#40;Report Builder and SSRS&#41;](../report-design/maps-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="a1238-133">子报表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="a1238-133">Subreports &#40;Report Builder and SSRS&#41;</span></span>](../report-design/subreports-report-builder-and-ssrs.md)  
  
  
