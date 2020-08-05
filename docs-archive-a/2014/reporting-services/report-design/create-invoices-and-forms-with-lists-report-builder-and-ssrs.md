---
title: 列出 (报表生成器和 SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c33231a5-b3a8-42e4-95bc-d05bdf2222f5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c9afb0dfabe5ccc3962d43eef30031a728514135
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580611"
---
# <a name="lists-report-builder-and-ssrs"></a><span data-ttu-id="82e23-102">列表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="82e23-102">Lists (Report Builder and SSRS)</span></span>
  <span data-ttu-id="82e23-103">列表数据区域重复报表数据集中的每一个组或行。</span><span class="sxs-lookup"><span data-stu-id="82e23-103">A list data region repeats with each group or row in the report dataset.</span></span> <span data-ttu-id="82e23-104">可以使用列表创建自由格式的报表或表单（如发票），或与其他数据区域结合使用。</span><span class="sxs-lookup"><span data-stu-id="82e23-104">A list can be used to create free-form reports or forms, such as invoices, or in conjunction with other data regions.</span></span> <span data-ttu-id="82e23-105">可以定义包含任意数量的报表项的列表。</span><span class="sxs-lookup"><span data-stu-id="82e23-105">You can define lists that contain any number of report items.</span></span> <span data-ttu-id="82e23-106">列表可以嵌套在其他列表中，以提供多组数据。</span><span class="sxs-lookup"><span data-stu-id="82e23-106">A list can be nested within another list to provide multiple groups of data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="82e23-107">您可以将列表作为报表部件与报表分开发布。</span><span class="sxs-lookup"><span data-stu-id="82e23-107">You can publish lists separately from a report as report parts.</span></span> [!INCLUDE[ssRBrptparts](../../includes/ssrbrptparts-md.md)]  
  
 <span data-ttu-id="82e23-108">若要快速开始使用列表，请参阅[教程：创建自由格式的报表（报表生成器）](../tutorial-creating-a-free-form-report-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="82e23-108">To quickly get started with lists, see [Tutorial: Creating a Free Form Report &#40;Report Builder&#41;](../tutorial-creating-a-free-form-report-report-builder.md).</span></span>  
  
 <span data-ttu-id="82e23-109">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 示例报表包括使用列表的报表。</span><span class="sxs-lookup"><span data-stu-id="82e23-109">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sample reports include a report that uses a list.</span></span> <span data-ttu-id="82e23-110">您可以通过在报表生成器或报表设计器中浏览示例报表的报表定义，或者通过在报表生成器或报表设计器中预览呈现的报表，了解列表的有关情况。</span><span class="sxs-lookup"><span data-stu-id="82e23-110">You can learn about lists by exploring the report definition of the sample report in Report Builder or Report Designer or by previewing the rendered report in Report Builder or Report Designer.</span></span> <span data-ttu-id="82e23-111">有关下载示例报表的详细信息，请参阅 [(SSRS) Reporting Services 示例](https://go.microsoft.com/fwlink/?LinkID=198283)。</span><span class="sxs-lookup"><span data-stu-id="82e23-111">For more information about downloading the sample reports, see [(SSRS) Reporting Services Samples](https://go.microsoft.com/fwlink/?LinkID=198283).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="adding-a-list-to-your-report"></a><a name="AddingList"></a><span data-ttu-id="82e23-112">向报表添加列表</span><span class="sxs-lookup"><span data-stu-id="82e23-112">Adding a List to Your Report</span></span>  
 <span data-ttu-id="82e23-113">从功能区上的“插入”选项卡向设计图面添加一个列表。</span><span class="sxs-lookup"><span data-stu-id="82e23-113">Add a list to the design surface from the Insert tab on ribbon.</span></span> <span data-ttu-id="82e23-114">默认情况下，该列表最初在一行中有一个单元与详细信息组关联。</span><span class="sxs-lookup"><span data-stu-id="82e23-114">By default, the list initially has a single cell in a row associated with the detail group.</span></span>  
  
 <span data-ttu-id="82e23-115">![设计图面上的新列表报表项](../media/rs-listtemplatenew.gif "设计图面上的新列表报表项")</span><span class="sxs-lookup"><span data-stu-id="82e23-115">![New List report item on the design surface](../media/rs-listtemplatenew.gif "New List report item on the design surface")</span></span>  
  
 <span data-ttu-id="82e23-116">在设计图面上选择列表时，将显示行控点和列控点，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="82e23-116">When you select a list on the design surface, row and column handles appear, as shown in the following figure.</span></span>  
  
 <span data-ttu-id="82e23-117">![从工具箱添加的新列表，选中](../media/rs-listtemplatenewselected.gif "从工具箱添加的新列表，选中")</span><span class="sxs-lookup"><span data-stu-id="82e23-117">![New List added from Toolbox, selected](../media/rs-listtemplatenewselected.gif "New List added from Toolbox, selected")</span></span>  
  
 <span data-ttu-id="82e23-118">最开始使用的列表是一个基于 Tablix 数据区域的模板。</span><span class="sxs-lookup"><span data-stu-id="82e23-118">The list you start with is a template based on the tablix data region.</span></span> <span data-ttu-id="82e23-119">添加一个列表后，可以继续增强设计，具体的方法是通过指定筛选器、排序或组表达式来更改此列表的内容或外观，或者更改此列表跨多个报表页显示的方式。</span><span class="sxs-lookup"><span data-stu-id="82e23-119">After you add a list, you can continue to enhance the design by changing the content or appearance of the list by specifying filter, sort, or group expressions, or changing the way the list displays across report pages.</span></span> <span data-ttu-id="82e23-120">有关详细信息，请参阅 [控制 Tablix 数据区域在报表页上的显示（报表生成器和 SSRS）](controlling-the-tablix-data-region-display-on-a-report-page.md)。</span><span class="sxs-lookup"><span data-stu-id="82e23-120">For more information, see [Controlling the Tablix Data Region Display on a Report Page &#40;Report Builder and SSRS&#41;](controlling-the-tablix-data-region-display-on-a-report-page.md).</span></span> <span data-ttu-id="82e23-121">尽管列表起初只具有一行、一列，但您可以通过添加嵌套或相邻的行组或列组或者添加额外的详细信息行，来进一步改进列表的设计。</span><span class="sxs-lookup"><span data-stu-id="82e23-121">Although the list starts with a single column and row, you can further continue to develop your list design by adding nested or adjacent row groups or column groups, or adding additional detail rows.</span></span> <span data-ttu-id="82e23-122">有关详细信息，请参阅[利用 Tablix 数据区域的灵活性（报表生成器和 SSRS）](exploring-the-flexibility-of-a-tablix-data-region-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="82e23-122">For more information, see [Exploring the Flexibility of a Tablix Data Region &#40;Report Builder and SSRS&#41;](exploring-the-flexibility-of-a-tablix-data-region-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="displaying-data-in-a-free-form-layout"></a><a name="DisplayingLayout"></a><span data-ttu-id="82e23-123">以自由格式布局显示数据</span><span class="sxs-lookup"><span data-stu-id="82e23-123">Displaying Data in a Free-form Layout</span></span>  
 <span data-ttu-id="82e23-124">若要以自由格式布局而非网格形式组织报表数据，可以向设计图面添加一个列表。</span><span class="sxs-lookup"><span data-stu-id="82e23-124">To organize report data in a free-form layout instead of a grid, you can add a list to the design surface.</span></span> <span data-ttu-id="82e23-125">从“报表数据”窗格向单元拖动字段。</span><span class="sxs-lookup"><span data-stu-id="82e23-125">Drag fields from the Report Data pane to the cell.</span></span> <span data-ttu-id="82e23-126">默认情况下，单元包含一个用作容器的矩形。</span><span class="sxs-lookup"><span data-stu-id="82e23-126">By default, the cell contains a rectangle that acts as a container.</span></span> <span data-ttu-id="82e23-127">移动此容器内的各个字段，直到产生所需的设计效果为止。</span><span class="sxs-lookup"><span data-stu-id="82e23-127">Move each field in the container until you have the design you want.</span></span> <span data-ttu-id="82e23-128">使用在此矩形容器内拖动文本框时显示的对齐线来帮助垂直和水平对齐边缘。</span><span class="sxs-lookup"><span data-stu-id="82e23-128">Use the snaplines that appear when you drag text boxes in the rectangle container to help you align edges vertically and horizontally.</span></span> <span data-ttu-id="82e23-129">通过调整单元的大小，删除不需要的空白区域。</span><span class="sxs-lookup"><span data-stu-id="82e23-129">Remove unwanted white space by adjusting the size of the cell.</span></span> <span data-ttu-id="82e23-130">有关详细信息，请参阅[更改行高或列宽（报表生成器和 SSRS）](change-row-height-or-column-width-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="82e23-130">For more information, see [Change Row Height or Column Width &#40;Report Builder and SSRS&#41;](change-row-height-or-column-width-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="82e23-131">下图显示了一个列表，该列表显示有关一个订单的信息，其中包括这些字段：Date、Order、Qty、Product、LineTotal 和一张图像。</span><span class="sxs-lookup"><span data-stu-id="82e23-131">The following figure shows a list that displays information about an order, including these fields: Date, Order, Qty, Product, LineTotal, and an image.</span></span>  
  
 <span data-ttu-id="82e23-132">![设计视图中的列表，有 4 个字段和一个图像](../media/rs-basiclistformdesign.gif "设计视图中的列表，有 4 个字段和一个图像")</span><span class="sxs-lookup"><span data-stu-id="82e23-132">![List in design view, 4 fields and an image](../media/rs-basiclistformdesign.gif "List in design view, 4 fields and an image")</span></span>  
  
 <span data-ttu-id="82e23-133">预览时，该列表重复以自由格式显示字段数据，如下图中所示：</span><span class="sxs-lookup"><span data-stu-id="82e23-133">In Preview, the list repeats to display the field data in the free-form format, as shown in the following figure:</span></span>  
  
 <span data-ttu-id="82e23-134">![具有 4 个字段和一个图像的列表的预览](../media/rs-basiclistformpreview.gif "具有 4 个字段和一个图像的列表的预览")</span><span class="sxs-lookup"><span data-stu-id="82e23-134">![Preview for List with 4 fields and one image](../media/rs-basiclistformpreview.gif "Preview for List with 4 fields and one image")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="82e23-135">这两张图中显示的点线用来说明每个字段值的自由格式布局。</span><span class="sxs-lookup"><span data-stu-id="82e23-135">The dotted lines displays in these figures are included to show the free-form layout for each field value.</span></span> <span data-ttu-id="82e23-136">通常情况下，在生产报表中不会使用点线。</span><span class="sxs-lookup"><span data-stu-id="82e23-136">Typically, you would not use dotted lines in a production report.</span></span>  
  

  
##  <a name="displaying-data-with-one-level-of-grouping"></a><a name="DisplayingGrouping"></a><span data-ttu-id="82e23-137">显示具有一级分组的数据</span><span class="sxs-lookup"><span data-stu-id="82e23-137">Displaying Data with One Level of Grouping</span></span>  
 <span data-ttu-id="82e23-138">由于列表自动提供容器，因此可以使用列表来显示具有多个视图的分组数据。</span><span class="sxs-lookup"><span data-stu-id="82e23-138">Because a list automatically provides a container, you can use a list to display grouped data with multiple views.</span></span> <span data-ttu-id="82e23-139">若要更改默认列表以便指定组，请编辑“详细信息”组，指定一个新名称，然后指定一个组表达式。</span><span class="sxs-lookup"><span data-stu-id="82e23-139">To change the default list to specify a group, edit the Details group, specify a new name, and specify a group expression.</span></span>  
  
 <span data-ttu-id="82e23-140">例如，可以嵌入一个表和一张图表，分别显示同一数据集的不同视图。</span><span class="sxs-lookup"><span data-stu-id="82e23-140">For example, you can embed a table and a chart that show different views of the same dataset.</span></span> <span data-ttu-id="82e23-141">可以向列表添加组，以使嵌套的报表项将对每个组值重复一次。</span><span class="sxs-lookup"><span data-stu-id="82e23-141">You can add a group to the list so that the nested report items will repeat once for every group value.</span></span> <span data-ttu-id="82e23-142">下图显示一个按产品类别分组的列表。</span><span class="sxs-lookup"><span data-stu-id="82e23-142">The following figure shows a list grouped by product category.</span></span> <span data-ttu-id="82e23-143">请注意，没有详细信息行。</span><span class="sxs-lookup"><span data-stu-id="82e23-143">Notice that there is no detail row.</span></span> <span data-ttu-id="82e23-144">两个表并列嵌套在此列表中。</span><span class="sxs-lookup"><span data-stu-id="82e23-144">Two tables are nested side by side in the list.</span></span> <span data-ttu-id="82e23-145">第一个表显示包含总销售额的子类别。</span><span class="sxs-lookup"><span data-stu-id="82e23-145">The first table displays the subcategories with total sales.</span></span> <span data-ttu-id="82e23-146">第二个表显示按地域分组的类别，并包含一张显示子类别分布情况的图表。</span><span class="sxs-lookup"><span data-stu-id="82e23-146">The second table displays the category grouped by geographical area, with a chart that shows the distribution of subcategories.</span></span>  
  
 <span data-ttu-id="82e23-147">![具有两个表（其中一个表带有嵌套图表）的列表](../media/rs-basiclistgroupdesign.gif "具有两个表（其中一个表带有嵌套图表）的列表")</span><span class="sxs-lookup"><span data-stu-id="82e23-147">![A list with 2 tables, one with nested chart](../media/rs-basiclistgroupdesign.gif "A list with 2 tables, one with nested chart")</span></span>  
  
 <span data-ttu-id="82e23-148">预览时，该表显示自行车的所有子类别的总销售额，它旁边的表显示每个地域的销售额细目。</span><span class="sxs-lookup"><span data-stu-id="82e23-148">In Preview, the table displays total sales for all subcategories of bicycles, and the table beside it displays the breakdown of sales per geographical area.</span></span> <span data-ttu-id="82e23-149">通过使用表达式为表指定背景色和为图表指定自定义调色板，第一个表还提供了图表颜色的图例。</span><span class="sxs-lookup"><span data-stu-id="82e23-149">By using an expression to specify the background color for the table and a custom palette for the chart, the first table also provides the legend for the chart colors.</span></span>  
  
 <span data-ttu-id="82e23-150">![两个表（其中一个表带有嵌套图表）的预览](../media/rs-basiclistgrouppreview.gif "两个表（其中一个表带有嵌套图表）的预览")</span><span class="sxs-lookup"><span data-stu-id="82e23-150">![Preview, 2 tables, one with nested chart](../media/rs-basiclistgrouppreview.gif "Preview, 2 tables, one with nested chart")</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="82e23-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="82e23-151">See Also</span></span>  
 <span data-ttu-id="82e23-152">[聚合函数引用（报表生成器和 SSRS）](report-builder-functions-aggregate-functions-reference.md) </span><span class="sxs-lookup"><span data-stu-id="82e23-152">[Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) </span></span>  
 [<span data-ttu-id="82e23-153">表达式示例（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="82e23-153">Expression Examples &#40;Report Builder and SSRS&#41;</span></span>](expression-examples-report-builder-and-ssrs.md)  
  
  
