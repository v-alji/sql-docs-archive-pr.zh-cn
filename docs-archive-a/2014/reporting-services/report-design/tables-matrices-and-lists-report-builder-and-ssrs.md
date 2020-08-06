---
title: 表、矩阵和列表（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.tablix.visibility.f1
- sql12.rtp.rptdesigner.groupproperties.advanced.f1
- "10045"
- sql12.rtp.rptdesigner.groupproperties.filters.f1
- "10039"
- "10104"
- sql12.rtp.rptdesigner.tablixgroup.f1
- sql12.rtp.rptdesigner.tablix.general.f1
- "10047"
- "10044"
- "10046"
- sql12.rtp.rptdesigner.groupproperties.visibility.f1
- "10101"
- sql12.rtp.rptdesigner.groupproperties.sort.f1
- sql12.rtp.rptdesigner.groupproperties.variables.f1
- sql12.rtp.rptdesigner.groupproperties.general.f1
- "10042"
- sql12.rtp.rptdesigner.tablix.sort.f1
- "10041"
- sql12.rtp.rptdesigner.groupproperties.pagebreaks.f1
- "10102"
- "10103"
- "10043"
- sql12.rtp.rptdesigner.tablix.filter.f1
ms.assetid: 9dcf3fc8-bf9c-4a14-a03d-e78254aa4098
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 03384009b0e51c081f0906ef0a768dafa180be7e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586373"
---
# <a name="tables-matrices-and-lists-report-builder-and-ssrs"></a><span data-ttu-id="70fb7-102">表、矩阵和列表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="70fb7-102">Tables, Matrices, and Lists (Report Builder and SSRS)</span></span>
  <span data-ttu-id="70fb7-103">表、矩阵和列表是在以行和列形式组织的单元中显示报表数据的数据区域。</span><span class="sxs-lookup"><span data-stu-id="70fb7-103">Tables, matrices, and lists are data regions that display report data in cells that are organized into rows and columns.</span></span> <span data-ttu-id="70fb7-104">单元通常包含文本数据（如文本、日期和数字），但它们还可以包含仪表、图表或报表项（例如图像）。</span><span class="sxs-lookup"><span data-stu-id="70fb7-104">The cells typically contain text data such as text, dates, and numbers but they can also contain gauges, charts, or report items such as images.</span></span> <span data-ttu-id="70fb7-105">表、矩阵和列表常常统称为 Tablix 数据区域。</span><span class="sxs-lookup"><span data-stu-id="70fb7-105">Collectively, tables, matrices, and lists are frequently referred to as tablix data regions.</span></span>  
  
 <span data-ttu-id="70fb7-106">表、矩阵和列表模板是在 Tablix 数据区域的基础上建立的，Tablix 数据区域是可以在单元中显示数据的灵活的网格。</span><span class="sxs-lookup"><span data-stu-id="70fb7-106">The table, matrix, and list templates are built on the tablix data region, which is a flexible grid that can display data in cells.</span></span> <span data-ttu-id="70fb7-107">在表和矩阵模板中，单元将组织成行和列的形式。</span><span class="sxs-lookup"><span data-stu-id="70fb7-107">In the table and matrix templates, cells are organized into rows and columns.</span></span> <span data-ttu-id="70fb7-108">因为模板是一般性的基础 tablix 数据区域的变体，所以，您可以结合模板格式显示数据，并且在您开发报表时更改表、矩阵或列表以便包括其他数据区域的功能。</span><span class="sxs-lookup"><span data-stu-id="70fb7-108">Because templates are variations of the underlying generic tablix data region, you can display can display data in combination of template formats and change the table, matrix, or list on to include the features of another data region as you develop your report.</span></span> <span data-ttu-id="70fb7-109">例如，如果您添加一个表并发现它没有满足您的需要，则可以添加列组以使该表成为矩阵。</span><span class="sxs-lookup"><span data-stu-id="70fb7-109">For example, if you add a table and find it does not serve your needs, you can add column groups to make the table a matrix.</span></span>  
  
 <span data-ttu-id="70fb7-110">表和矩阵数据区域可以通过包括嵌套的表、矩阵、列表、图表和仪表，显示复杂的数据关系。</span><span class="sxs-lookup"><span data-stu-id="70fb7-110">The table and matrix data regions can display complex data relationships by including nested tables, matrices, lists, charts and gauges.</span></span> <span data-ttu-id="70fb7-111">表和矩阵具有表格形式的布局，并且其数据来自在单个数据源基础上建立的单个数据集。</span><span class="sxs-lookup"><span data-stu-id="70fb7-111">Tables and matrices have a tabular layout and their data comes from a single dataset, built on a single data source.</span></span> <span data-ttu-id="70fb7-112">表和矩阵之间的主要差异在于，表只能包含行组，而矩阵可具有行组和列组。</span><span class="sxs-lookup"><span data-stu-id="70fb7-112">The key difference between tables and matrices is that tables can include only row groups, where as matrices have row groups and column groups.</span></span>  
  
 <span data-ttu-id="70fb7-113">列表则稍有不同。</span><span class="sxs-lookup"><span data-stu-id="70fb7-113">Lists are a little different.</span></span> <span data-ttu-id="70fb7-114">它们支持可包括多个对等表或矩阵（每个对等表或矩阵都使用来自不同数据集的数据）的自由布局。</span><span class="sxs-lookup"><span data-stu-id="70fb7-114">They support a free-layout that and can include multiple peer tables or matrices, each using data from a different dataset.</span></span> <span data-ttu-id="70fb7-115">列表也可以用于发票之类的表单。</span><span class="sxs-lookup"><span data-stu-id="70fb7-115">Lists can also be used for forms, such as invoices.</span></span>  
  
 <span data-ttu-id="70fb7-116">下图显示具有表、矩阵或列表的简单报表。</span><span class="sxs-lookup"><span data-stu-id="70fb7-116">The following pictures show simple reports with a table, matrix, or list.</span></span>  
  
 <span data-ttu-id="70fb7-117">![RS_TableMatrixList](../media/rs-tablematrixlist.gif "RS_TableMatrixList")</span><span class="sxs-lookup"><span data-stu-id="70fb7-117">![RS_TableMatrixList](../media/rs-tablematrixlist.gif "RS_TableMatrixList")</span></span>  
  
 <span data-ttu-id="70fb7-118">若要快速开始使用表、矩阵和列表，请参阅[教程：创建基本表报表（报表生成器）](../tutorial-creating-a-basic-table-report-report-builder.md)、[教程：创建矩阵报表（报表生成器）](../tutorial-creating-a-matrix-report-report-builder.md)和[教程：创建自由格式的报表（报表生成器）](../tutorial-creating-a-free-form-report-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="70fb7-118">To quickly get started with tables, matrices, and lists, see [Tutorial: Creating a Basic Table Report &#40;Report Builder&#41;](../tutorial-creating-a-basic-table-report-report-builder.md), [Tutorial: Creating a Matrix Report &#40;Report Builder&#41;](../tutorial-creating-a-matrix-report-report-builder.md), and [Tutorial: Creating a Free Form Report &#40;Report Builder&#41;](../tutorial-creating-a-free-form-report-report-builder.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="70fb7-119">您可以将表、矩阵和列表作为报表部件与报表分开发布。</span><span class="sxs-lookup"><span data-stu-id="70fb7-119">You can publish tables, matrices, and lists separately from a report as report parts.</span></span> [!INCLUDE[ssRBrptparts](../../includes/ssrbrptparts-md.md)]  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="table"></a><a name="Table"></a><span data-ttu-id="70fb7-120">数据表</span><span class="sxs-lookup"><span data-stu-id="70fb7-120">Table</span></span>  
 <span data-ttu-id="70fb7-121">使用表显示详细信息数据、组织行组中的数据，或者同时用于两种目的。</span><span class="sxs-lookup"><span data-stu-id="70fb7-121">Use a table to display detail data, organize the data in row groups, or both.</span></span> <span data-ttu-id="70fb7-122">表模板包含三个列和一个表头行和一个数据详细信息行。</span><span class="sxs-lookup"><span data-stu-id="70fb7-122">The Table template contains three columns with a table header row and a details row for data.</span></span> <span data-ttu-id="70fb7-123">下图显示了在设计图面上选择的初始表模板：</span><span class="sxs-lookup"><span data-stu-id="70fb7-123">The following figure shows the initial table template, selected on the design surface:</span></span>  
  
 <span data-ttu-id="70fb7-124">![设计图面上的表模板，选中](../media/rs-tabletemplatenewselected.gif "设计图面上的表模板，选中")</span><span class="sxs-lookup"><span data-stu-id="70fb7-124">![Table template on design surface, selected](../media/rs-tabletemplatenewselected.gif "Table template on design surface, selected")</span></span>  
  
 <span data-ttu-id="70fb7-125">可以按单个字段、多个字段或通过编写自己的表达式来对数据进行分组。</span><span class="sxs-lookup"><span data-stu-id="70fb7-125">You can group data by a single field, by multiple fields, or by writing your own expression.</span></span> <span data-ttu-id="70fb7-126">可以创建嵌套的组或独立的相邻组和显示分组数据的聚合值，或将合计添加到组。</span><span class="sxs-lookup"><span data-stu-id="70fb7-126">You can create nested groups or independent, adjacent groups and display aggregated values for grouped data, or add totals to groups.</span></span> <span data-ttu-id="70fb7-127">例如，如果您的表中有一个称为 [类别] 的行组，则可以为每个组添加小计，以及为报表添加总计。</span><span class="sxs-lookup"><span data-stu-id="70fb7-127">For example, if your table has a row group called [Category], you can add a subtotal for each group as well as a grand total for the report.</span></span> <span data-ttu-id="70fb7-128">为了改进表的外观和突出显示要强调的数据，可以合并单元并将格式应用于数据和表标题。</span><span class="sxs-lookup"><span data-stu-id="70fb7-128">To improve the appearance of the table and highlight data you want to emphasize, you can merge cells and apply formatting to data and table headings.</span></span>  
  
 <span data-ttu-id="70fb7-129">可以在开始时隐藏详细信息数据或分组数据，并包括明细切换以使用户能够交互选择要显示的数据量。</span><span class="sxs-lookup"><span data-stu-id="70fb7-129">You can initially hide detail or grouped data, and include drilldown toggles to enable a user to interactively choose how much data to show.</span></span>  
  
 <span data-ttu-id="70fb7-130">有关详细信息，请参阅[表（报表生成器和 SSRS）](tables-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="70fb7-130">For more information, see [Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="matrix"></a><a name="Matrix"></a><span data-ttu-id="70fb7-131">矩阵</span><span class="sxs-lookup"><span data-stu-id="70fb7-131">Matrix</span></span>  
 <span data-ttu-id="70fb7-132">使用矩阵显示按行和列进行分组的聚合数据汇总，类似于数据透视表或交叉表。</span><span class="sxs-lookup"><span data-stu-id="70fb7-132">Use a matrix to display aggregated data summaries, grouped in rows and columns, similar to a PivotTable or crosstab.</span></span> <span data-ttu-id="70fb7-133">组的行数和列数由每个行组和列组中的唯一值的个数确定。</span><span class="sxs-lookup"><span data-stu-id="70fb7-133">The number of rows and columns for groups is determined by the number of unique values for each row and column groups.</span></span> <span data-ttu-id="70fb7-134">下图显示了在设计图面上选择的初始矩阵模板：</span><span class="sxs-lookup"><span data-stu-id="70fb7-134">The following figure shows the initial matrix template, selected on the design surface:</span></span>  
  
 <span data-ttu-id="70fb7-135">![从工具箱添加的新矩阵，选中](../media/rs-matrixtemplatenewselected.gif "从工具箱添加的新矩阵，选中")</span><span class="sxs-lookup"><span data-stu-id="70fb7-135">![New Matrix added from Toolbox, selected](../media/rs-matrixtemplatenewselected.gif "New Matrix added from Toolbox, selected")</span></span>  
  
 <span data-ttu-id="70fb7-136">您可以按行组和列组中的多个字段或表达式对数据进行分组。</span><span class="sxs-lookup"><span data-stu-id="70fb7-136">You can group data by multiple fields or expressions in row and column groups.</span></span> <span data-ttu-id="70fb7-137">在运行时，当组合报表数据和数据区域时，随着为列组添加列和为行组添加行，矩阵将在页面上水平和垂直增长。</span><span class="sxs-lookup"><span data-stu-id="70fb7-137">At run time, when the report data and data regions are combined, a matrix grows horizontally and vertically on the page as columns for column groups and rows for row groups are added.</span></span> <span data-ttu-id="70fb7-138">矩阵单元显示仅限于单元所属行组和列组的交集的聚合值。</span><span class="sxs-lookup"><span data-stu-id="70fb7-138">The matrix cells display aggregate values that are scoped to the intersection of the row and column groups to which the cell belongs.</span></span> <span data-ttu-id="70fb7-139">例如，如果您的矩阵具有一个行组（类别）和两个显示销售额之和的列组（区域和年份），则报表中将显示两个单元，其中对于“类别”组中的每个值都显示销售额之和。</span><span class="sxs-lookup"><span data-stu-id="70fb7-139">For example, if your matrix has a row group (Category) and two column groups (Territory and Year) that display the sum of sales, the report displays two cells with sums of sales for each value in the Category group.</span></span> <span data-ttu-id="70fb7-140">单元的作用域是两个交集：类别和区域的交集，以及类别和年份的交集。</span><span class="sxs-lookup"><span data-stu-id="70fb7-140">The scope of the cells are the two intersections are: Category and Territory and Category and Year.</span></span> <span data-ttu-id="70fb7-141">矩阵可以包含嵌套组和相邻组。</span><span class="sxs-lookup"><span data-stu-id="70fb7-141">The matrix can include nested and adjacent groups.</span></span> <span data-ttu-id="70fb7-142">嵌套组具有父-子关系，相邻组具有对等关系。</span><span class="sxs-lookup"><span data-stu-id="70fb7-142">Nested groups have a parent-child relationship and adjacent groups a peer relationship.</span></span> <span data-ttu-id="70fb7-143">您可以添加矩阵内嵌套行组和列组的任何级别和所有级别的小计。</span><span class="sxs-lookup"><span data-stu-id="70fb7-143">You can add subtotals for any and all levels of nested row and column groups within the matrix.</span></span>  
  
 <span data-ttu-id="70fb7-144">为使矩阵数据的外观更具可读性和突出显示要强调的数据，可以合并单元或者水平和垂直拆分，并将格式应用于数据和组标题。</span><span class="sxs-lookup"><span data-stu-id="70fb7-144">To make the matrix data more readable and highlight the data you want to emphasize, you can merge cells or split horizontally and vertically and apply formatting to data and group headings.</span></span>  
  
 <span data-ttu-id="70fb7-145">您也可以包括最初隐藏详细信息数据的明细切换，然后用户便可单击该切换以根据需要显示更多或更少的详细信息。</span><span class="sxs-lookup"><span data-stu-id="70fb7-145">You can also include drilldown toggles that initially hide detail data; the user can then click the toggles to display more or less detail as needed.</span></span>  
  
 <span data-ttu-id="70fb7-146">有关详细信息，请参阅[矩阵 &#40;报表生成器和 SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="70fb7-146">For more information, see [Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="list"></a><a name="List"></a><span data-ttu-id="70fb7-147">成员列表</span><span class="sxs-lookup"><span data-stu-id="70fb7-147">List</span></span>  
 <span data-ttu-id="70fb7-148">使用列表创建自由格式布局。</span><span class="sxs-lookup"><span data-stu-id="70fb7-148">Use a list to create a free-form layout.</span></span> <span data-ttu-id="70fb7-149">您不受网格布局的限制，而可以在列表内自由放置字段。</span><span class="sxs-lookup"><span data-stu-id="70fb7-149">You are not limited to a grid layout, but can place fields freely inside the list.</span></span> <span data-ttu-id="70fb7-150">可以使用列表设计用于显示多个数据集字段的表单，也可以将其用作容器以便并排显示分组数据的多个数据区域。</span><span class="sxs-lookup"><span data-stu-id="70fb7-150">You can use a list to design a form for displaying many dataset fields or as a container to display multiple data regions side by side for grouped data.</span></span> <span data-ttu-id="70fb7-151">例如，您可以为列表定义组；添加表、图表和图像；并显示每组值的表和图形表单中的各个值，正如对雇员或病人记录所执行的操作一样。</span><span class="sxs-lookup"><span data-stu-id="70fb7-151">For example, you can define a group for a list; add a table, chart, and image; and display values in table and graphic form for each group value, as you might for an employee or patient record.</span></span>  
  
 <span data-ttu-id="70fb7-152">![从工具箱添加的新列表，选中](../media/rs-listtemplatenewselected.gif "从工具箱添加的新列表，选中")</span><span class="sxs-lookup"><span data-stu-id="70fb7-152">![New List added from Toolbox, selected](../media/rs-listtemplatenewselected.gif "New List added from Toolbox, selected")</span></span>  
  
 <span data-ttu-id="70fb7-153">有关详细信息，请参阅[列出 &#40;报表生成器和 SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="70fb7-153">For more information, see [Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="preparing-data"></a><a name="PreparingData"></a><span data-ttu-id="70fb7-154">准备数据</span><span class="sxs-lookup"><span data-stu-id="70fb7-154">Preparing Data</span></span>  
 <span data-ttu-id="70fb7-155">表、矩阵和列表数据区域显示来自数据集的数据。</span><span class="sxs-lookup"><span data-stu-id="70fb7-155">A table, matrix, and list data regions display data from a dataset.</span></span> <span data-ttu-id="70fb7-156">您可以在检索数据集数据的查询中准备数据，也可以通过设置表、矩阵或列表中的属性来准备数据。</span><span class="sxs-lookup"><span data-stu-id="70fb7-156">You can prepare the data in the query that retrieves the data for the dataset or by setting properties in the table, matrix, or list.</span></span>  
  
 <span data-ttu-id="70fb7-157">您用于为报表数据集检索数据的查询语言（例如 [!INCLUDE[tsql](../../includes/tsql-md.md)]）可通过以下方式准备数据：应用筛选器以便只包括数据的子集，用使报表更具可读性的常量替换 Null 值或空值，以及对数据进行排序和分组。</span><span class="sxs-lookup"><span data-stu-id="70fb7-157">The query languages such as [!INCLUDE[tsql](../../includes/tsql-md.md)], that you use to retrieve the data for the report datasets can prepare the data by applying filters to include only a subset of the data, replacing null values or blanks with constants that make the report more readable, and sorting and grouping data.</span></span>  
  
 <span data-ttu-id="70fb7-158">如果您选择在报表的表、矩阵或列表数据区域中准备数据，则可以对数据区域或数据区域内的单元设置属性。</span><span class="sxs-lookup"><span data-stu-id="70fb7-158">If you choose to prepare the data in the table, matrix, or list data region of a report, you set properties on the data region or cells within the data region.</span></span> <span data-ttu-id="70fb7-159">如果要筛选数据或对数据进行排序，则对数据区域设置属性。</span><span class="sxs-lookup"><span data-stu-id="70fb7-159">If you want to filter or sort the data, set the properties on the data region.</span></span> <span data-ttu-id="70fb7-160">例如，若要对数据进行排序，则可以指定要依据其进行排序的列以及排序方向。</span><span class="sxs-lookup"><span data-stu-id="70fb7-160">For example, to sort the data you specify the columns to sort on and the sort direction.</span></span> <span data-ttu-id="70fb7-161">如果要为某一字段提供可选值，您可以设置显示该字段的单元文本的值。</span><span class="sxs-lookup"><span data-stu-id="70fb7-161">If you want to provide an alternative value for a field, you set the values of the cell text that displays the field.</span></span> <span data-ttu-id="70fb7-162">例如，若要在某一字段为空或 Null 时显示空白，您可以使用筛选器来设置值。</span><span class="sxs-lookup"><span data-stu-id="70fb7-162">For example, to display Blank when a field is empty or null, you use an expression to set the value.</span></span>  
  
 <span data-ttu-id="70fb7-163">有关详细信息，请参阅[准备要在 Tablix 数据区域中显示的数据（报表生成器和 SSRS）](preparing-data-for-display-in-a-tablix-data-region-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="70fb7-163">For more information, see [Preparing Data for Display in a Tablix Data Region &#40;Report Builder and SSRS&#41;](preparing-data-for-display-in-a-tablix-data-region-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="building-and-configuring-a-table-matrix-or-list"></a><a name="BuildingConfiguringTableMatrixList"></a> <span data-ttu-id="70fb7-164">生成和配置表、矩阵或列表</span><span class="sxs-lookup"><span data-stu-id="70fb7-164">Building and Configuring a Table, Matrix, or List</span></span>  
 <span data-ttu-id="70fb7-165">在您向报表中添加表或矩阵时，可以使用表和矩阵向导，也可以根据报表生成器和报表设计器提供的模板手动生成它们。</span><span class="sxs-lookup"><span data-stu-id="70fb7-165">When you add tables or matrices to your report, you can use the Table and Matrix Wizard or build them manually from the templates that Report Builder and Report Designer provide.</span></span> <span data-ttu-id="70fb7-166">而列表是根据列表模板手动生成的。</span><span class="sxs-lookup"><span data-stu-id="70fb7-166">Lists are built manually from the list template.</span></span>  
  
 <span data-ttu-id="70fb7-167">该向导将指导您一步步地快速生成并配置表或矩阵。</span><span class="sxs-lookup"><span data-stu-id="70fb7-167">The wizard guides you through the steps to quickly build and configure a table or matrix.</span></span> <span data-ttu-id="70fb7-168">在您完成该向导或从头开始生成 Tablix 数据区域后，可以进一步配置和优化它们。</span><span class="sxs-lookup"><span data-stu-id="70fb7-168">After you complete the wizard or if you build the tablix data regions from scratch, you can further configure and refine them.</span></span> <span data-ttu-id="70fb7-169">在数据区域的右键单击菜单上提供的对话框可便于您为分页符、页眉和页脚的可重复性和可见性、显示选项、筛选器和排序设置最常用的属性。</span><span class="sxs-lookup"><span data-stu-id="70fb7-169">The dialog boxes, available from the right-click menus on the data regions, make it easy to set the most commonly used properties for page breaks, repeatability and visibility of headers and footers, display options, filters, and sorting.</span></span> <span data-ttu-id="70fb7-170">但是，Tablix 数据区域提供大量的附加属性，这些属性只能在报表生成器的“属性”窗格中设置。</span><span class="sxs-lookup"><span data-stu-id="70fb7-170">But the tablix data region provides a wealth of additional properties, which you can set only in the Properties pane of Report Builder.</span></span> <span data-ttu-id="70fb7-171">例如，如果想要在表、矩阵或列表的数据集为空时显示一条消息，则在“属性”窗格的 NoRowsMessage Tablix 属性中指定消息文本。</span><span class="sxs-lookup"><span data-stu-id="70fb7-171">For example, if you want to display a message when the dataset for a table, matrix, or list is empty, you specify the message text in the NoRowsMessage tablix property in the Properties pane.</span></span>  
  

  
##  <a name="changing-between-tablix-templates"></a><a name="ChangingBetweenTablixTemplates"></a><span data-ttu-id="70fb7-172">Tablix 模板之间的更改</span><span class="sxs-lookup"><span data-stu-id="70fb7-172">Changing Between Tablix Templates</span></span>  
 <span data-ttu-id="70fb7-173">您不受初始 Tablix 模板选择的限制。</span><span class="sxs-lookup"><span data-stu-id="70fb7-173">You are not limited by your initial tablix template choice.</span></span> <span data-ttu-id="70fb7-174">添加组、总计和标签时，您可能希望修改 Tablix 设计。</span><span class="sxs-lookup"><span data-stu-id="70fb7-174">As you add groups, totals, and labels, you might want to modify your tablix design.</span></span> <span data-ttu-id="70fb7-175">例如，您可能会从表开始，然后删除详细信息行和添加列组。</span><span class="sxs-lookup"><span data-stu-id="70fb7-175">For example, you might start with a table and then delete the details row and add column groups.</span></span> <span data-ttu-id="70fb7-176">有关详细信息，请参阅[利用 Tablix 数据区域的灵活性（报表生成器和 SSRS）](exploring-the-flexibility-of-a-tablix-data-region-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="70fb7-176">For more information, see [Exploring the Flexibility of a Tablix Data Region &#40;Report Builder and SSRS&#41;](exploring-the-flexibility-of-a-tablix-data-region-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="70fb7-177">通过添加任何 Tablix 功能，可以继续开发表、矩阵或列表。</span><span class="sxs-lookup"><span data-stu-id="70fb7-177">You can continue to develop a table, matrix, or list by adding any tablix feature.</span></span> <span data-ttu-id="70fb7-178">Tablix 功能包括显示行和列中的分组数据的详细信息数据或聚合。</span><span class="sxs-lookup"><span data-stu-id="70fb7-178">Tablix features include displaying detail data or aggregates for grouped data on rows and columns.</span></span> <span data-ttu-id="70fb7-179">可以创建嵌套组、独立的相邻组或递归组。</span><span class="sxs-lookup"><span data-stu-id="70fb7-179">You can create nested groups, independent adjacent groups, or recursive groups.</span></span> <span data-ttu-id="70fb7-180">可以对分组数据进行筛选和排序，并通过在组定义中包括多个组表达式来方便地组合组。</span><span class="sxs-lookup"><span data-stu-id="70fb7-180">You can filter and sort grouped data, and easily combine groups by including multiple group expressions in a group definition</span></span>  
  
 <span data-ttu-id="70fb7-181">您还可以为组添加总计，或者为数据区域添加总计。</span><span class="sxs-lookup"><span data-stu-id="70fb7-181">You can also add totals for a group or grand totals for the data region.</span></span> <span data-ttu-id="70fb7-182">可以隐藏行或列以简化报表，并使用户能够切换显示隐藏数据，这与明细报表中相同。</span><span class="sxs-lookup"><span data-stu-id="70fb7-182">You can hide rows or columns to simplify a report and enable the user to toggle the display of the hidden data, as in a drilldown report.</span></span> <span data-ttu-id="70fb7-183">有关详细信息，请参阅 [控制 Tablix 数据区域在报表页上的显示（报表生成器和 SSRS）](controlling-the-tablix-data-region-display-on-a-report-page.md)。</span><span class="sxs-lookup"><span data-stu-id="70fb7-183">For more information, see [Controlling the Tablix Data Region Display on a Report Page &#40;Report Builder and SSRS&#41;](controlling-the-tablix-data-region-display-on-a-report-page.md).</span></span>  
  

  
##  <a name="how-to-topics"></a><a name="HowTo"></a><span data-ttu-id="70fb7-184">操作指南主题</span><span class="sxs-lookup"><span data-stu-id="70fb7-184">How-To Topics</span></span>  
 <span data-ttu-id="70fb7-185">本节中列出的过程分步向您说明如何在您的报表中使用表、矩阵和列表；如何显示行和列中的数据、添加和删除列、合并单元以及为行组和列组包括小计。</span><span class="sxs-lookup"><span data-stu-id="70fb7-185">This section lists procedures that show you, step by step, how to work with work with tables, matrices and lists in your reports; how to display data in rows and columns, add and delete columns, merge cells, and include subtotals for row and column groups.</span></span>  
  
-   [<span data-ttu-id="70fb7-186">添加详细信息组（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="70fb7-186">Add a Details Group &#40;Report Builder and SSRS&#41;</span></span>](add-a-details-group-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="70fb7-187">向组或 Tablix 数据区域添加总计（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="70fb7-187">Add a Total to a Group or Tablix Data Region &#40;Report Builder and SSRS&#41;</span></span>](add-a-total-to-a-group-or-tablix-data-region-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="70fb7-188">更改单元中的项（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="70fb7-188">Change an Item Within a Cell &#40;Report Builder and SSRS&#41;</span></span>](change-an-item-within-a-cell-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="70fb7-189">更改行高或列宽（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="70fb7-189">Change Row Height or Column Width &#40;Report Builder and SSRS&#41;</span></span>](change-row-height-or-column-width-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="70fb7-190">插入或删除列（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="70fb7-190">Insert or Delete a Column &#40;Report Builder and SSRS&#41;</span></span>](insert-or-delete-a-column-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="70fb7-191">插入或删除行（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="70fb7-191">Insert or Delete a Row &#40;Report Builder and SSRS&#41;</span></span>](insert-or-delete-a-row-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="70fb7-192">合并数据区域中的单元（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="70fb7-192">Merge Cells in a Data Region &#40;Report Builder and SSRS&#41;</span></span>](merge-cells-in-a-data-region-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="70fb7-193">创建一个递归层次结构组（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="70fb7-193">Create a Recursive Hierarchy Group &#40;Report Builder and SSRS&#41;</span></span>](create-a-recursive-hierarchy-group-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="70fb7-194">在数据区域中添加或删除组（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="70fb7-194">Add or Delete a Group in a Data Region &#40;Report Builder and SSRS&#41;</span></span>](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="70fb7-195">与组一起显示组头和组尾（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="70fb7-195">Display Headers and Footers with a Group &#40;Report Builder and SSRS&#41;</span></span>](display-headers-and-footers-with-a-group-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="70fb7-196">创建递阶报表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="70fb7-196">Create a Stepped Report &#40;Report Builder and SSRS&#41;</span></span>](create-a-stepped-report-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="70fb7-197">添加、移动或删除表、矩阵或列表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="70fb7-197">Add, Move, or Delete a Table, Matrix, or List &#40;Report Builder and SSRS&#41;</span></span>](add-move-or-delete-a-table-matrix-or-list-report-builder-and-ssrs.md)  
  

  
##  <a name="in-this-section"></a><a name="InThisSection"></a> <span data-ttu-id="70fb7-198">本节内容</span><span class="sxs-lookup"><span data-stu-id="70fb7-198">In This Section</span></span>  
 <span data-ttu-id="70fb7-199">下列主题提供有关使用 Tablix 数据区域的其他信息。</span><span class="sxs-lookup"><span data-stu-id="70fb7-199">The following topics provide additional information about working with the tablix data region.</span></span>  
  
 [<span data-ttu-id="70fb7-200">Tablix 数据区域（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="70fb7-200">Tablix Data Region &#40;Report Builder and SSRS&#41;</span></span>](../tablix-data-region-report-builder-and-ssrs.md)  
 <span data-ttu-id="70fb7-201">说明与 Tablix 数据区域（例如 Tablix 的区域、详细信息和分组数据、列组和行组以及静态和动态行和列）相关的关键概念。</span><span class="sxs-lookup"><span data-stu-id="70fb7-201">Explains key concepts related to the tablix data region such as areas of the tablix, detail and grouped data, column and row groups, and static and dynamic rows and columns.</span></span>  
  
 [<span data-ttu-id="70fb7-202">向 Tablix 数据区域添加数据（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="70fb7-202">Adding Data to a Tablix Data Region &#40;Report Builder and SSRS&#41;</span></span>](adding-data-to-a-tablix-data-region-report-builder-and-ssrs.md)  
 <span data-ttu-id="70fb7-203">提供与向 Tablix 数据区域添加详细信息和分组数据、小计和总计以及标签有关的详细信息。</span><span class="sxs-lookup"><span data-stu-id="70fb7-203">Provides detailed information about adding detail and grouped data, subtotals and totals, and labels to a tablix data region.</span></span>  
  
 [<span data-ttu-id="70fb7-204">控制 Tablix 数据区域在报表页上的显示（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="70fb7-204">Controlling the Tablix Data Region Display on a Report Page &#40;Report Builder and SSRS&#41;</span></span>](controlling-the-tablix-data-region-display-on-a-report-page.md)  
 <span data-ttu-id="70fb7-205">介绍 Tablix 数据区域的属性，您可以修改这些属性以便更改在报表中查看 Tablix 数据区域时该数据区域的显示方式。</span><span class="sxs-lookup"><span data-stu-id="70fb7-205">Describes properties for a tablix data region that you can modify to change the way a tablix data region appears when you view it in a report.</span></span>  
  
 [<span data-ttu-id="70fb7-206">控制行标题和列标题（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="70fb7-206">Controlling Row and Column Headings &#40;Report Builder and SSRS&#41;</span></span>](controlling-row-and-column-headings-report-builder-and-ssrs.md)  
 <span data-ttu-id="70fb7-207">介绍在表、矩阵或列表数据区域可以水平或垂直跨多页时如何控制行和列标题。</span><span class="sxs-lookup"><span data-stu-id="70fb7-207">Describes how to control row and column headings when a table, matrix, or list data region cans span multiple pages horizontally or vertically.</span></span>  
  
 [<span data-ttu-id="70fb7-208">创建递归层次结构组（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="70fb7-208">Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;</span></span>](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)  
 <span data-ttu-id="70fb7-209">介绍如何显示递归数据（其中，父级和子级之间的关系由数据集中的字段表示）。</span><span class="sxs-lookup"><span data-stu-id="70fb7-209">Describes how to display recursive data where the relationship between parent and child is represented by fields in the dataset.</span></span>  
  
 [<span data-ttu-id="70fb7-210">了解组（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="70fb7-210">Understanding Groups &#40;Report Builder and SSRS&#41;</span></span>](understanding-groups-report-builder-and-ssrs.md)  
 <span data-ttu-id="70fb7-211">说明什么是组以及何时使用它们，并介绍可用于不同 Tablix 数据区域的组。</span><span class="sxs-lookup"><span data-stu-id="70fb7-211">Explains what groups are and when you use them and describes the groups available for the different tablix data regions.</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="70fb7-212">另请参阅</span><span class="sxs-lookup"><span data-stu-id="70fb7-212">See Also</span></span>  
 <span data-ttu-id="70fb7-213">[添加数据集筛选器、数据区域筛选器和组筛选器 &#40;报表生成器和 SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span><span class="sxs-lookup"><span data-stu-id="70fb7-213">[Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span></span>  
 <span data-ttu-id="70fb7-214">[嵌套数据区域 &#40;报表生成器和 SSRS&#41;](nested-data-regions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="70fb7-214">[Nested Data Regions &#40;Report Builder and SSRS&#41;](nested-data-regions-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="70fb7-215">[将多个数据区域链接到同一数据集 &#40;报表生成器和 SSRS&#41;](linking-multiple-data-regions-to-the-same-dataset-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="70fb7-215">[Linking Multiple Data Regions to the Same Dataset &#40;Report Builder and SSRS&#41;](linking-multiple-data-regions-to-the-same-dataset-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="70fb7-216">[表达式（报表生成器和 SSRS）](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="70fb7-216">[Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="70fb7-217">[对数据进行筛选、分组和排序 &#40;报表生成器和 SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="70fb7-217">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="70fb7-218">[报表参数 &#40;报表生成器和报表设计器&#41;](report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="70fb7-218">[Report Parameters &#40;Report Builder and Report Designer&#41;](report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="70fb7-219">[图表 &#40;报表生成器和 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="70fb7-219">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="70fb7-220">仪表（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="70fb7-220">Gauges &#40;Report Builder and SSRS&#41;</span></span>](gauges-report-builder-and-ssrs.md)  
  
  
