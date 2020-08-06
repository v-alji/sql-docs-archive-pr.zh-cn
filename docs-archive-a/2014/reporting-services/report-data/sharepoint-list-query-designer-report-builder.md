---
title: SharePoint 列表查询设计器（报表生成器）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10016"
ms.assetid: b8a3122c-8008-4950-b515-937636d7967f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a35efb926b8f729874cff42afc53fb5820c920f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694267"
---
# <a name="sharepoint-list-query-designer-report-builder"></a><span data-ttu-id="44858-102">SharePoint 列表查询设计器（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="44858-102">SharePoint List Query Designer (Report Builder)</span></span>
  <span data-ttu-id="44858-103">报表生成器提供了图形查询设计器和基于文本的查询设计器，可帮助您创建一个查询，该查询指定要从 SharePoint 站点中为报表数据集检索的数据。</span><span class="sxs-lookup"><span data-stu-id="44858-103">Report Builder provides both a graphical query designer and a text-based query designer to help you create a query that specifies the data to retrieve from a SharePoint site for a report dataset.</span></span> <span data-ttu-id="44858-104">使用图形查询设计器可以浏览 SharePoint 列表元数据、以交互方式生成查询，还可以查看查询结果。</span><span class="sxs-lookup"><span data-stu-id="44858-104">Use the graphical query designer to explore the SharePoint list metadata, interactively build a query, and view the results of your query.</span></span> <span data-ttu-id="44858-105">使用基于文本的查询设计器可以查看图形查询设计器生成的查询、修改查询或键入查询命令。</span><span class="sxs-lookup"><span data-stu-id="44858-105">Use the text-based query designer to view the query that was built by the graphical query designer, modify a query, or type the query commands.</span></span> <span data-ttu-id="44858-106">您还可以从文件或报表中导入现有的查询。</span><span class="sxs-lookup"><span data-stu-id="44858-106">You can also import an existing query from a file or report.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="44858-107">用户创建和运行查询时访问数据源。</span><span class="sxs-lookup"><span data-stu-id="44858-107">Users access data sources when they create and run queries.</span></span> <span data-ttu-id="44858-108">您应授予对数据源的最小权限（如只读权限）。</span><span class="sxs-lookup"><span data-stu-id="44858-108">You should grant minimal permissions on the data sources, such as read-only permissions.</span></span>  
  
## <a name="graphical-query-designer"></a><span data-ttu-id="44858-109">图形查询设计器</span><span class="sxs-lookup"><span data-stu-id="44858-109">Graphical Query Designer</span></span>  
 <span data-ttu-id="44858-110">在图形查询设计器中，您可以浏览 SharePoint 站点，也可以交互方式生成用于为数据集检索 SharePoint 列表数据的命令。</span><span class="sxs-lookup"><span data-stu-id="44858-110">In the graphical query designer you can explorer the SharePoint site, interactively build the command that retrieve SharePoint list data for a dataset.</span></span> <span data-ttu-id="44858-111">您可以选择要包括在数据集中的字段，或者指定限制数据集中数据的筛选器。</span><span class="sxs-lookup"><span data-stu-id="44858-111">You choose the fields to include in the dataset and optionally, specify filters that limit the data in the dataset.</span></span> <span data-ttu-id="44858-112">可以指定将筛选器作为参数并在运行时提供筛选器的值。</span><span class="sxs-lookup"><span data-stu-id="44858-112">You can specify that filters are used as parameters and provide the value of the filter at run-time.</span></span>  
  
 <span data-ttu-id="44858-113">SharePoint 列表包含大量 SharePoint 特定的字段，而将这些字段包括在报表中可能并不起什么作用。</span><span class="sxs-lookup"><span data-stu-id="44858-113">SharePoint lists include a large number of SharePoint specific fields that might not be useful to include in reports.</span></span> <span data-ttu-id="44858-114">查询设计器提供了一个用于隐藏这些字段的选项，从而能够更加轻松、更加快速地确定要使用的字段。</span><span class="sxs-lookup"><span data-stu-id="44858-114">The query designer provides an option to hide these fields to make it easier and quicker to determine the fields to use.</span></span>  
  
 <span data-ttu-id="44858-115">图形查询设计器分为三个区域</span><span class="sxs-lookup"><span data-stu-id="44858-115">The graphical query designer is divided into three areas</span></span>  
  
-   <span data-ttu-id="44858-116">“浏览”窗格，在其中您可以选择要使用的列表项及其字段。</span><span class="sxs-lookup"><span data-stu-id="44858-116">Explore pane in which you select the list items and their fields to use.</span></span>  
  
-   <span data-ttu-id="44858-117">“设计”区域，在其中您可以生成查询。</span><span class="sxs-lookup"><span data-stu-id="44858-117">Design area in which you build the query.</span></span>  
  
-   <span data-ttu-id="44858-118">“结果”窗格，在其中您可以查看查询结果。</span><span class="sxs-lookup"><span data-stu-id="44858-118">Results pane in which you view the query results.</span></span>  
  
 <span data-ttu-id="44858-119">下图显示了用于 SharePoint 列表的图形查询设计器。</span><span class="sxs-lookup"><span data-stu-id="44858-119">The following figure shows the graphical query designer when it is used with SharePoint lists.</span></span>  
  
 <span data-ttu-id="44858-120">![rsQD_Relational_Graphical_SharePoint](../media/rsqd-relational-graphical-sharepoint.gif "rsQD_Relational_Graphical_SharePoint")</span><span class="sxs-lookup"><span data-stu-id="44858-120">![rsQD_Relational_Graphical_SharePoint](../media/rsqd-relational-graphical-sharepoint.gif "rsQD_Relational_Graphical_SharePoint")</span></span>  
  
 <span data-ttu-id="44858-121">下表介绍了每个窗格的功能。</span><span class="sxs-lookup"><span data-stu-id="44858-121">The following table describes the function of each pane.</span></span>  
  
 [<span data-ttu-id="44858-122">SharePoint 列表</span><span class="sxs-lookup"><span data-stu-id="44858-122">SharePoint Lists</span></span>](#DatabaseView)  
 <span data-ttu-id="44858-123">在列表中显示 SharePoint 列表和每一项内的字段。</span><span class="sxs-lookup"><span data-stu-id="44858-123">Displays SharePoint lists and the fields within each item in the list.</span></span>  
  
 [<span data-ttu-id="44858-124">所选字段</span><span class="sxs-lookup"><span data-stu-id="44858-124">Selected fields</span></span>](#SelectedFields)  
 <span data-ttu-id="44858-125">在“SharePoint 列表”窗格中显示选定项中的 SharePoint 列表字段名称的列表。</span><span class="sxs-lookup"><span data-stu-id="44858-125">Displays the list of SharePoint list field names from the selected items in the SharePoint Lists pane.</span></span> <span data-ttu-id="44858-126">这些字段将成为报表数据集的字段集合。</span><span class="sxs-lookup"><span data-stu-id="44858-126">These fields become the field collection for the report dataset.</span></span>  
  
 [<span data-ttu-id="44858-127">应用的筛选器</span><span class="sxs-lookup"><span data-stu-id="44858-127">Applied filters</span></span>](#AppliedFilters)  
 <span data-ttu-id="44858-128">在“数据库视图”中显示表或视图的字段列表和筛选条件。</span><span class="sxs-lookup"><span data-stu-id="44858-128">Displays a list of fields and filter criteria for tables or views in the Database view.</span></span>  
  
 [<span data-ttu-id="44858-129">查询结果</span><span class="sxs-lookup"><span data-stu-id="44858-129">Query results</span></span>](#QueryResults)  
 <span data-ttu-id="44858-130">显示自动生成的查询的结果集示例数据。</span><span class="sxs-lookup"><span data-stu-id="44858-130">Displays sample data for the result set for the automatically generated query.</span></span>  
  
###  <a name="sharepoint-lists-pane"></a><a name="DatabaseView"></a> <span data-ttu-id="44858-131">“SharePoint 列表”窗格</span><span class="sxs-lookup"><span data-stu-id="44858-131">SharePoint Lists Pane</span></span>  
 <span data-ttu-id="44858-132">“SharePoint 列表”窗格显示您有权查看的数据库对象的元数据，该元数据取决于数据源连接和凭据。</span><span class="sxs-lookup"><span data-stu-id="44858-132">The SharePoint Lists pane displays the metadata for database objects that you have the permissions to view, which is determined by the data source connection and credentials.</span></span> <span data-ttu-id="44858-133">层次结构视图显示按数据库架构组织的数据库对象。</span><span class="sxs-lookup"><span data-stu-id="44858-133">The hierarchical view displays database objects organized by database schema.</span></span> <span data-ttu-id="44858-134">展开每个架构的节点可查看表、视图、存储过程及表值函数。</span><span class="sxs-lookup"><span data-stu-id="44858-134">Expand the node for each schema to view tables, views, stored procedures, and table-valued functions.</span></span> <span data-ttu-id="44858-135">展开表或视图可显示列。</span><span class="sxs-lookup"><span data-stu-id="44858-135">Expand a table or view to display the columns.</span></span>  
  
###  <a name="selected-fields-pane"></a><a name="SelectedFields"></a> <span data-ttu-id="44858-136">“所选字段”窗格</span><span class="sxs-lookup"><span data-stu-id="44858-136">Selected Fields Pane</span></span>  
 <span data-ttu-id="44858-137">“所选字段”窗格显示您为 SharePoint 列表项选择的列表项字段。</span><span class="sxs-lookup"><span data-stu-id="44858-137">The Selected Fields pane displays the list item fields that you select for SharePoint list items.</span></span> <span data-ttu-id="44858-138">此窗格中显示的字段将成为报表数据集的字段集合。</span><span class="sxs-lookup"><span data-stu-id="44858-138">The fields that are displayed in this pane become the field collection for the report dataset.</span></span> <span data-ttu-id="44858-139">创建数据集和查询后，使用“报表数据”窗格可查看报表数据集的字段集合。</span><span class="sxs-lookup"><span data-stu-id="44858-139">After you create a dataset and a query, use the Report Data pane to view the field collection for a report dataset.</span></span> <span data-ttu-id="44858-140">这些字段表示当您查看报表时可在表、图表及其他报表项中显示的数据。</span><span class="sxs-lookup"><span data-stu-id="44858-140">These fields represent the data you can display in tables, charts, and other report items when you view a report.</span></span>  
  
 <span data-ttu-id="44858-141">若要在此窗格中添加或删除字段，请在“SharePoint 列表”窗格中选中或清除针对表或视图字段的复选框。</span><span class="sxs-lookup"><span data-stu-id="44858-141">To add or remove fields to this pane, select or clear check boxes for the table or view fields in the SharePoint Lists pane.</span></span>  
  
###  <a name="applied-filters-pane"></a><a name="AppliedFilters"></a> <span data-ttu-id="44858-142">“应用的筛选器”窗格</span><span class="sxs-lookup"><span data-stu-id="44858-142">Applied Filters Pane</span></span>  
 <span data-ttu-id="44858-143">“应用的筛选器”窗格显示用于限制在运行时检索的数据行数的条件。</span><span class="sxs-lookup"><span data-stu-id="44858-143">The Applied Filters pane displays the criteria that are used to limit the number of rows of data that are retrieved at run-time.</span></span> <span data-ttu-id="44858-144">此窗格中指定的条件用于生成 [!INCLUDE[tsql](../../includes/tsql-md.md)] WHERE 子句。</span><span class="sxs-lookup"><span data-stu-id="44858-144">Criteria specified in this pane are used to generate a [!INCLUDE[tsql](../../includes/tsql-md.md)] WHERE clause.</span></span> <span data-ttu-id="44858-145">如果选择了参数选项，则会自动创建报表参数。</span><span class="sxs-lookup"><span data-stu-id="44858-145">When you select the parameter option, a report parameter is automatically created.</span></span> <span data-ttu-id="44858-146">通过基于查询参数的报表参数，用户可为查询指定值，以便控制报表中的数据。</span><span class="sxs-lookup"><span data-stu-id="44858-146">Report parameters that are based on query parameters enable a user to specify values for the query to control the data in the report.</span></span>  
  
 <span data-ttu-id="44858-147">显示以下列：</span><span class="sxs-lookup"><span data-stu-id="44858-147">The following columns are displayed:</span></span>  
  
-   <span data-ttu-id="44858-148">**字段名称** ：显示应用该条件的字段的名称。</span><span class="sxs-lookup"><span data-stu-id="44858-148">**Field Name** Displays the name of the field to apply the criteria to.</span></span>  
  
-   <span data-ttu-id="44858-149">**运算符** ：显示要在筛选表达式中使用的运算。</span><span class="sxs-lookup"><span data-stu-id="44858-149">**Operator** Displays the operation to use in the filter expression.</span></span>  
  
-   <span data-ttu-id="44858-150">**值** ：显示要在筛选表达式中使用的值。</span><span class="sxs-lookup"><span data-stu-id="44858-150">**Value** Displays the value to use in the filter expression.</span></span>  
  
-   <span data-ttu-id="44858-151">**参数** ：显示用于为查询添加查询参数的选项。</span><span class="sxs-lookup"><span data-stu-id="44858-151">**Parameter** Displays the option to add a query parameter to the query.</span></span> <span data-ttu-id="44858-152">使用“数据集属性”可查看查询参数与报表参数之间的关系。</span><span class="sxs-lookup"><span data-stu-id="44858-152">Use the Dataset properties to view the relationship between query parameter and report parameter.</span></span>  
  
###  <a name="query-results-pane"></a><a name="QueryResults"></a> <span data-ttu-id="44858-153">“查询结果”窗格</span><span class="sxs-lookup"><span data-stu-id="44858-153">Query Results Pane</span></span>  
 <span data-ttu-id="44858-154">“查询结果”窗格显示由其他窗格中的选项指定并且自动生成的查询的结果。</span><span class="sxs-lookup"><span data-stu-id="44858-154">The Query results pane displays the results for the automatically generated query that is specified by selections in the other panes.</span></span> <span data-ttu-id="44858-155">结果集中的列是您在“所选字段”窗格中指定的字段，行数据受限于您在“应用的筛选器”窗格中指定的筛选器。</span><span class="sxs-lookup"><span data-stu-id="44858-155">The columns in the result set are the fields that you specify in the Selected Fields pane and the row data is limited by the filters that you specify in the Applied Filters pane.</span></span>  
  
 <span data-ttu-id="44858-156">此数据表示在运行查询时数据源中的值。</span><span class="sxs-lookup"><span data-stu-id="44858-156">This data represents values from the data source at the time that you run the query.</span></span> <span data-ttu-id="44858-157">此数据未保存在报表定义中。报表中的实际数据是在处理报表时进行检索的。</span><span class="sxs-lookup"><span data-stu-id="44858-157">The data is not saved in the report definition .The actual data in the report is retrieved when the report is processed.</span></span>  
  
 <span data-ttu-id="44858-158">结果集中的排序顺序取决于从数据源检索数据的顺序。</span><span class="sxs-lookup"><span data-stu-id="44858-158">Sort order in the result set is determined by the order the data is retrieved from the data source.</span></span> <span data-ttu-id="44858-159">可以通过修改查询来更改排序顺序，也可以在为报表检索数据后更改。</span><span class="sxs-lookup"><span data-stu-id="44858-159">Sort order can be changed by modifying the query or after the data is retrieved for the report.</span></span>  
  
### <a name="graphical-query-designer-toolbar"></a><span data-ttu-id="44858-160">图形查询设计器工具栏</span><span class="sxs-lookup"><span data-stu-id="44858-160">Graphical Query Designer Toolbar</span></span>  
 <span data-ttu-id="44858-161">关系查询设计器工作栏提供了以下按钮，帮助您指定或查看查询结果。</span><span class="sxs-lookup"><span data-stu-id="44858-161">The relational query designer toolbar provides the following buttons to help you specify or view the results of a query.</span></span>  
  
|<span data-ttu-id="44858-162">按钮</span><span class="sxs-lookup"><span data-stu-id="44858-162">Button</span></span>|<span data-ttu-id="44858-163">说明</span><span class="sxs-lookup"><span data-stu-id="44858-163">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="44858-164">**编辑为文本**</span><span class="sxs-lookup"><span data-stu-id="44858-164">**Edit As Text**</span></span>|<span data-ttu-id="44858-165">切换到基于文本的查询设计器，可查看自动生成的查询，也可以修改查询。</span><span class="sxs-lookup"><span data-stu-id="44858-165">Toggle to the text-based query designer to view the automatically generated query or to modify the query.</span></span>|  
|<span data-ttu-id="44858-166">**导入**</span><span class="sxs-lookup"><span data-stu-id="44858-166">**Import**</span></span>|<span data-ttu-id="44858-167">从文件或报表中导入现有的查询。</span><span class="sxs-lookup"><span data-stu-id="44858-167">Import an existing query from a file or report.</span></span> <span data-ttu-id="44858-168">支持 .sql 和 .rdl 文件类型。</span><span class="sxs-lookup"><span data-stu-id="44858-168">File types .sql and .rdl are supported.</span></span>|  
|<span data-ttu-id="44858-169">**运行查询**</span><span class="sxs-lookup"><span data-stu-id="44858-169">**Run Query**</span></span>|<span data-ttu-id="44858-170">运行查询。</span><span class="sxs-lookup"><span data-stu-id="44858-170">Run the query.</span></span> <span data-ttu-id="44858-171">“查询结果”窗格显示结果集。</span><span class="sxs-lookup"><span data-stu-id="44858-171">The Query results pane displays the result set.</span></span>|  
|<span data-ttu-id="44858-172">**显示隐藏字段**</span><span class="sxs-lookup"><span data-stu-id="44858-172">**Show Hidden Fields**</span></span>|<span data-ttu-id="44858-173">在显示字段还是隐藏字段之间切换，这些字段是由 SharePoint 自动生成的（如用于 SharePoint 链接项的 ProgId 和 Level），但通常不在报表中使用。</span><span class="sxs-lookup"><span data-stu-id="44858-173">Toggle to show or hide the fields that were automatically generated by SharePoint such as the ProgId and Level for SharePoint link items, but are typically not used in reports..</span></span> <span data-ttu-id="44858-174">隐藏这些字段可使字段列表更短且易于使用。</span><span class="sxs-lookup"><span data-stu-id="44858-174">Hiding these fields makes the field list shorter and easier to use.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="44858-175">另请参阅</span><span class="sxs-lookup"><span data-stu-id="44858-175">See Also</span></span>  
 [<span data-ttu-id="44858-176">查询设计器（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="44858-176">Query Designers &#40;Report Builder&#41;</span></span>](../query-designers-report-builder.md)  
  
  
