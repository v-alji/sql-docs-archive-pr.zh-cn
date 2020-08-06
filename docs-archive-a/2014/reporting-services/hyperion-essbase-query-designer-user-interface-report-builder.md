---
title: Hyperion Essbase 查询设计器用户界面 (报表生成器) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10013"
helpviewer_keywords:
- Hyperion Essbase query designer
- query designers, Hyperion
ms.assetid: d89a6773-dbe5-48e5-bda9-db0e67100696
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 38da75955608d95eb9fe673c7cdef5896bbe2787
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694338"
---
# <a name="hyperion-essbase-query-designer-user-interface-report-builder"></a><span data-ttu-id="07bd5-102">Hyperion Essbase 查询设计器用户界面（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="07bd5-102">Hyperion Essbase Query Designer User Interface (Report Builder)</span></span>
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="07bd5-103">提供了一个图形查询设计器，用于为 [!INCLUDE[extEssbase](../includes/extessbase-md.md)] 数据源生成多维表达式 (MDX) 查询。</span><span class="sxs-lookup"><span data-stu-id="07bd5-103">provides a graphical query designer for building Multidimensional Expression (MDX) queries for a [!INCLUDE[extEssbase](../includes/extessbase-md.md)] data source.</span></span> <span data-ttu-id="07bd5-104">MDX 图形查询设计器有两种模式：设计模式和查询模式。</span><span class="sxs-lookup"><span data-stu-id="07bd5-104">The MDX graphical query designer has two modes: Design mode and Query mode.</span></span> <span data-ttu-id="07bd5-105">每种模式都提供一个“元数据”窗格，从该窗格中可以拖动在数据源中定义的多维数据集的成员，以生成可在处理报表时检索数据的 MDX 查询。</span><span class="sxs-lookup"><span data-stu-id="07bd5-105">Each mode provides a Metadata pane from which you can drag members from a cube defined on the data source to build an MDX query that retrieves data when the report is processed.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="07bd5-106">用户创建和运行查询时访问数据源。</span><span class="sxs-lookup"><span data-stu-id="07bd5-106">Users access data sources when they create and run queries.</span></span> <span data-ttu-id="07bd5-107">您应授予对数据源的最小权限（如只读权限）。</span><span class="sxs-lookup"><span data-stu-id="07bd5-107">You should grant minimal permissions on the data sources, such as read-only permissions.</span></span>

 <span data-ttu-id="07bd5-108">本节介绍每种模式的图形查询设计器中的工具栏按钮和查询设计器窗格。</span><span class="sxs-lookup"><span data-stu-id="07bd5-108">This section describes the toolbar buttons and query designer panes for each mode of the graphical query designer.</span></span>

## <a name="graphical-query-designer-in-design-mode"></a><span data-ttu-id="07bd5-109">设计模式下的图形查询设计器</span><span class="sxs-lookup"><span data-stu-id="07bd5-109">Graphical Query Designer in Design Mode</span></span>
 <span data-ttu-id="07bd5-110">为使用 [!INCLUDE[extEssbase](../includes/extessbase-md.md)] 数据源的数据集编辑 MDX 查询时，图形查询设计器将在设计模式下打开。</span><span class="sxs-lookup"><span data-stu-id="07bd5-110">When you edit an MDX query for a dataset that uses a [!INCLUDE[extEssbase](../includes/extessbase-md.md)] data source, the graphical query designer opens in Design mode.</span></span> <span data-ttu-id="07bd5-111">下图列出了设计模式的窗格。</span><span class="sxs-lookup"><span data-stu-id="07bd5-111">The following figure labels the panes for Design mode.</span></span>

 <span data-ttu-id="07bd5-112">![用于 Hyperion Essbase 数据源的查询设计器](media/rsqd-dshyperionessbase-mdx-designmode.gif "用于 Hyperion Essbase 数据源的查询设计器")</span><span class="sxs-lookup"><span data-stu-id="07bd5-112">![Query Designer for Hyperion Essbase data source](media/rsqd-dshyperionessbase-mdx-designmode.gif "Query Designer for Hyperion Essbase data source")</span></span>

 <span data-ttu-id="07bd5-113">下表列出了设计模式下的窗格。</span><span class="sxs-lookup"><span data-stu-id="07bd5-113">The following table lists the panes in this mode.</span></span>

|<span data-ttu-id="07bd5-114">窗格</span><span class="sxs-lookup"><span data-stu-id="07bd5-114">Pane</span></span>|<span data-ttu-id="07bd5-115">函数</span><span class="sxs-lookup"><span data-stu-id="07bd5-115">Function</span></span>|
|----------|--------------|
|<span data-ttu-id="07bd5-116">“选择多维数据集”按钮</span><span class="sxs-lookup"><span data-stu-id="07bd5-116">Select Cube button</span></span>|<span data-ttu-id="07bd5-117">显示当前选定的多维数据集。</span><span class="sxs-lookup"><span data-stu-id="07bd5-117">Displays the currently selected cube.</span></span>|
|<span data-ttu-id="07bd5-118">“元数据”窗格</span><span class="sxs-lookup"><span data-stu-id="07bd5-118">Metadata pane</span></span>|<span data-ttu-id="07bd5-119">显示多维数据集的层次结构列表。</span><span class="sxs-lookup"><span data-stu-id="07bd5-119">Displays a hierarchical list of cubes.</span></span>|
|<span data-ttu-id="07bd5-120">“计算成员”窗格</span><span class="sxs-lookup"><span data-stu-id="07bd5-120">Calculated Members pane</span></span>|<span data-ttu-id="07bd5-121">显示当前定义的可在查询中使用的计算成员。</span><span class="sxs-lookup"><span data-stu-id="07bd5-121">Displays the currently defined calculated members available for use in the query.</span></span>|
|<span data-ttu-id="07bd5-122">“筛选器”窗格</span><span class="sxs-lookup"><span data-stu-id="07bd5-122">Filter pane</span></span>|<span data-ttu-id="07bd5-123">显示要在查询中应用的筛选器。</span><span class="sxs-lookup"><span data-stu-id="07bd5-123">Displays the filters to apply in the query.</span></span>|
|<span data-ttu-id="07bd5-124">“数据”窗格</span><span class="sxs-lookup"><span data-stu-id="07bd5-124">Data pane</span></span>|<span data-ttu-id="07bd5-125">显示运行查询的结果。</span><span class="sxs-lookup"><span data-stu-id="07bd5-125">Displays the results of running the query.</span></span>|

 <span data-ttu-id="07bd5-126">可以将“元数据”窗格中的维度和度量值以及“计算成员”窗格中的计算成员拖到“数据”窗格中。</span><span class="sxs-lookup"><span data-stu-id="07bd5-126">You can drag dimensions and measures from the Metadata pane, and calculated members from the Calculated Member pane onto the Data pane.</span></span> <span data-ttu-id="07bd5-127">如果工具栏中的 **“自动执行”** 切换按钮为“开”，则每次将对象拖到“数据”窗格时，查询设计器都将运行查询。</span><span class="sxs-lookup"><span data-stu-id="07bd5-127">If the **AutoExecute** toggle button on the toolbar is on, the query designer runs the query every time you drop an object onto the Data pane.</span></span> <span data-ttu-id="07bd5-128">如果 **“自动执行”** 为“关”，则对“数据”窗格进行更改时，查询设计器将不运行查询。</span><span class="sxs-lookup"><span data-stu-id="07bd5-128">If **AutoExecute** is off, the query designer does not run the query as you make changes to the Data pane.</span></span> <span data-ttu-id="07bd5-129">使用工具栏上的 **“运行”** 按钮可以手动运行查询。</span><span class="sxs-lookup"><span data-stu-id="07bd5-129">You can manually run the query using the **Run** button on the toolbar.</span></span>

 <span data-ttu-id="07bd5-130">在“筛选器”窗格中，可以选择维度值来限制从数据源检索的数据。</span><span class="sxs-lookup"><span data-stu-id="07bd5-130">In the Filter pane, you can select dimension values to limit the data retrieved from the data source.</span></span> <span data-ttu-id="07bd5-131">在设计模式下的筛选器中定义的值显示在查询模式下的 MDX Where 子句中。</span><span class="sxs-lookup"><span data-stu-id="07bd5-131">Values you define in the filter in Design mode appear in the MDX Where clause in Query mode.</span></span>

### <a name="toolbar-for-the-graphical-query-designer-in-design-mode-toolbar"></a><span data-ttu-id="07bd5-132">设计模式下的图形查询设计器工具栏</span><span class="sxs-lookup"><span data-stu-id="07bd5-132">Toolbar for the Graphical Query Designer in Design Mode Toolbar</span></span>
 <span data-ttu-id="07bd5-133">查询设计器工具栏提供了可以帮助您使用图形界面来设计 MDX 查询的按钮。</span><span class="sxs-lookup"><span data-stu-id="07bd5-133">The query designer toolbar provides buttons to help you design MDX queries using the graphical interface.</span></span> <span data-ttu-id="07bd5-134">下表显示这些按钮并介绍了它们的功能。</span><span class="sxs-lookup"><span data-stu-id="07bd5-134">The following table shows the buttons and describes their functions.</span></span>

|<span data-ttu-id="07bd5-135">Button</span><span class="sxs-lookup"><span data-stu-id="07bd5-135">Button</span></span>|<span data-ttu-id="07bd5-136">描述</span><span class="sxs-lookup"><span data-stu-id="07bd5-136">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="07bd5-137">**编辑为文本**</span><span class="sxs-lookup"><span data-stu-id="07bd5-137">**Edit As Text**</span></span>|<span data-ttu-id="07bd5-138">在基于文本的查询设计器和图形查询设计器之间切换。</span><span class="sxs-lookup"><span data-stu-id="07bd5-138">Toggle between the text-based query designer and the graphical query designer.</span></span> <span data-ttu-id="07bd5-139">不可用于此数据源类型。</span><span class="sxs-lookup"><span data-stu-id="07bd5-139">Not available for this data source type.</span></span>|
|<span data-ttu-id="07bd5-140">**导入**</span><span class="sxs-lookup"><span data-stu-id="07bd5-140">**Import**</span></span>|<span data-ttu-id="07bd5-141">从文件系统中的报表定义 (.rdl) 文件导入现有查询。</span><span class="sxs-lookup"><span data-stu-id="07bd5-141">Import an existing query from a report definition (.rdl) file on the file system.</span></span>|
|<span data-ttu-id="07bd5-142">![刷新数据集字段](media/rsqdicon-refreshfields.gif "刷新数据集字段")</span><span class="sxs-lookup"><span data-stu-id="07bd5-142">![Refresh dataset fields](media/rsqdicon-refreshfields.gif "Refresh dataset fields")</span></span>|<span data-ttu-id="07bd5-143">刷新数据源的元数据。</span><span class="sxs-lookup"><span data-stu-id="07bd5-143">Refresh metadata from the data source.</span></span>|
|<span data-ttu-id="07bd5-144">![添加计算成员](../analysis-services/media/rsqdicon-addcalculatedmember.gif "添加计算成员")</span><span class="sxs-lookup"><span data-stu-id="07bd5-144">![Add calculated member](../analysis-services/media/rsqdicon-addcalculatedmember.gif "Add calculated member")</span></span>|<span data-ttu-id="07bd5-145">显示 **“计算成员生成器”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="07bd5-145">Display the **Calculated Member Builder** dialog box.</span></span> <span data-ttu-id="07bd5-146">使用此按钮可以创建或编辑计算成员表达式，其中包括设置 **“求解次序”** 属性。</span><span class="sxs-lookup"><span data-stu-id="07bd5-146">Use this to create or edit expressions for a calculated member, including setting the **Solve Order** property.</span></span>|
|<span data-ttu-id="07bd5-147">![切换显示空单元](../analysis-services/media/rsqdicon-showemptycells.gif "切换为显示空单元格")</span><span class="sxs-lookup"><span data-stu-id="07bd5-147">![Toggle for show empty cells](../analysis-services/media/rsqdicon-showemptycells.gif "Toggle for show empty cells")</span></span>|<span data-ttu-id="07bd5-148">在“数据”窗格中的显示或不显示空单元格之间切换。</span><span class="sxs-lookup"><span data-stu-id="07bd5-148">Switch between showing and not showing empty cells in the Data pane.</span></span> <span data-ttu-id="07bd5-149">（这等同于在 MDX 中使用 NON EMPTY 子句）。</span><span class="sxs-lookup"><span data-stu-id="07bd5-149">(This is the equivalent to using the NON EMPTY clause in MDX).</span></span>|
|<span data-ttu-id="07bd5-150">![自动执行查询](../analysis-services/media/rsqdicon-autoexecute.gif "自动执行查询")</span><span class="sxs-lookup"><span data-stu-id="07bd5-150">![AutoExecute the query](../analysis-services/media/rsqdicon-autoexecute.gif "AutoExecute the query")</span></span>|<span data-ttu-id="07bd5-151">自动运行查询并在每次更改（如在“数据”窗格中删除一列）之后显示结果。</span><span class="sxs-lookup"><span data-stu-id="07bd5-151">Automatically run the query and show the result every time a change is made, for example, deleting a column in the Data pane.</span></span> <span data-ttu-id="07bd5-152">结果将显示在“数据”窗格中。</span><span class="sxs-lookup"><span data-stu-id="07bd5-152">Results are shown in the Data pane.</span></span>|
|<span data-ttu-id="07bd5-153">![删除](../analysis-services/media/rsqdicon-delete.gif "删除")</span><span class="sxs-lookup"><span data-stu-id="07bd5-153">![Delete](../analysis-services/media/rsqdicon-delete.gif "Delete")</span></span>|<span data-ttu-id="07bd5-154">从查询中删除选定项。</span><span class="sxs-lookup"><span data-stu-id="07bd5-154">Delete the selected item from the query.</span></span> <span data-ttu-id="07bd5-155">使用此按钮可以删除“筛选器”窗格中的选定行。</span><span class="sxs-lookup"><span data-stu-id="07bd5-155">Use this button to delete selected rows in the Filter pane.</span></span>|
|<span data-ttu-id="07bd5-156">![运行查询](../analysis-services/media/rsqdicon-run.gif "运行查询")</span><span class="sxs-lookup"><span data-stu-id="07bd5-156">![Run the query](../analysis-services/media/rsqdicon-run.gif "Run the query")</span></span>|<span data-ttu-id="07bd5-157">运行查询并在“数据”窗格中显示结果。</span><span class="sxs-lookup"><span data-stu-id="07bd5-157">Run the query and display the results in the Data pane.</span></span>|
|<span data-ttu-id="07bd5-158">![取消查询](../analysis-services/media/rsqdicon-cancel.gif "取消查询")</span><span class="sxs-lookup"><span data-stu-id="07bd5-158">![Cancel the query](../analysis-services/media/rsqdicon-cancel.gif "Cancel the query")</span></span>|<span data-ttu-id="07bd5-159">取消查询。</span><span class="sxs-lookup"><span data-stu-id="07bd5-159">Cancel the query.</span></span>|
|<span data-ttu-id="07bd5-160">![切换到设计模式](../analysis-services/media/rsqdicon-designmode.gif "切换到设计模式")</span><span class="sxs-lookup"><span data-stu-id="07bd5-160">![Switch to Design mode](../analysis-services/media/rsqdicon-designmode.gif "Switch to Design mode")</span></span>|<span data-ttu-id="07bd5-161">在设计模式和查询模式之间切换。</span><span class="sxs-lookup"><span data-stu-id="07bd5-161">Switch between Design mode and Query mode.</span></span>|

## <a name="graphical-query-designer-in-query-mode"></a><span data-ttu-id="07bd5-162">查询模式下的图形查询设计器</span><span class="sxs-lookup"><span data-stu-id="07bd5-162">Graphical Query Designer in Query Mode</span></span>
 <span data-ttu-id="07bd5-163">若要将图形查询设计器更改为查询模式，请单击工具栏上的 **“设计模式”** 切换按钮。</span><span class="sxs-lookup"><span data-stu-id="07bd5-163">To change the graphical query designer to Query mode, click the **Design Mode** toggle button on the toolbar.</span></span>

 <span data-ttu-id="07bd5-164">![用于 Hyperion 的查询模式的查询设计器](media/rsqd-hyperionessbase-mdx-querymode.gif "用于 Hyperion 的查询模式的查询设计器")</span><span class="sxs-lookup"><span data-stu-id="07bd5-164">![Query Designer in Query Mode for Hyperion](media/rsqd-hyperionessbase-mdx-querymode.gif "Query Designer in Query Mode for Hyperion")</span></span>

 <span data-ttu-id="07bd5-165">下表介绍了每个窗格的功能。</span><span class="sxs-lookup"><span data-stu-id="07bd5-165">The following table describes the function of each pane.</span></span>

|<span data-ttu-id="07bd5-166">窗格</span><span class="sxs-lookup"><span data-stu-id="07bd5-166">Pane</span></span>|<span data-ttu-id="07bd5-167">函数</span><span class="sxs-lookup"><span data-stu-id="07bd5-167">Function</span></span>|
|----------|--------------|
|<span data-ttu-id="07bd5-168">“选择多维数据集”按钮</span><span class="sxs-lookup"><span data-stu-id="07bd5-168">Select Cube button</span></span>|<span data-ttu-id="07bd5-169">显示当前选定的多维数据集。</span><span class="sxs-lookup"><span data-stu-id="07bd5-169">Displays the currently selected cube.</span></span>|
|<span data-ttu-id="07bd5-170">“元数据/函数”窗格</span><span class="sxs-lookup"><span data-stu-id="07bd5-170">Metadata/Functions pane</span></span>|<span data-ttu-id="07bd5-171">显示一个选项卡式窗口，其中列出了可用于创建查询文本的元数据或函数列表。</span><span class="sxs-lookup"><span data-stu-id="07bd5-171">Displays a tabbed window that shows a list of available metadata or functions that can be used to build the query text.</span></span>|
|<span data-ttu-id="07bd5-172">“查询”窗格</span><span class="sxs-lookup"><span data-stu-id="07bd5-172">Query pane</span></span>|<span data-ttu-id="07bd5-173">显示当前的查询文本。</span><span class="sxs-lookup"><span data-stu-id="07bd5-173">Displays the current query text.</span></span>|
|<span data-ttu-id="07bd5-174">“结果”窗格</span><span class="sxs-lookup"><span data-stu-id="07bd5-174">Result pane</span></span>|<span data-ttu-id="07bd5-175">显示查询的结果。</span><span class="sxs-lookup"><span data-stu-id="07bd5-175">Displays the results of the query.</span></span>|

 <span data-ttu-id="07bd5-176">通过“元数据”窗格，可以将度量值和维度从 **“元数据”** 选项卡拖到“MDX 查询”窗格。</span><span class="sxs-lookup"><span data-stu-id="07bd5-176">From the Metadata pane, you can drag measures and dimensions from the **Metadata** tab onto the MDX Query pane.</span></span> <span data-ttu-id="07bd5-177">还可以将函数从 **“函数”** 选项卡拖到“MDX 查询”窗格。</span><span class="sxs-lookup"><span data-stu-id="07bd5-177">You can drag functions from the **Functions** tab onto the MDX Query pane.</span></span> <span data-ttu-id="07bd5-178">当执行查询时，“结果”窗格将显示当前 MDX 查询的结果。</span><span class="sxs-lookup"><span data-stu-id="07bd5-178">When you execute the query, the Result pane displays the results for the current MDX query.</span></span>

### <a name="toolbar-for-the-graphical-query-designer-in-query-mode"></a><span data-ttu-id="07bd5-179">查询模式下的图形查询设计器工具栏</span><span class="sxs-lookup"><span data-stu-id="07bd5-179">Toolbar for the Graphical Query Designer in Query Mode</span></span>
 <span data-ttu-id="07bd5-180">查询设计器工具栏提供了可以帮助您使用图形界面来设计 MDX 查询的按钮。</span><span class="sxs-lookup"><span data-stu-id="07bd5-180">The query designer toolbar provides buttons to help you design MDX queries using the graphical interface.</span></span> <span data-ttu-id="07bd5-181">工具栏按钮在设计模式和查询模式下是相同的，但是下列按钮在查询模式下不可用：</span><span class="sxs-lookup"><span data-stu-id="07bd5-181">The toolbar buttons are identical between Design mode and Query mode, but the following buttons are not enabled for Query mode:</span></span>

-   <span data-ttu-id="07bd5-182">**编辑为文本**</span><span class="sxs-lookup"><span data-stu-id="07bd5-182">**Edit As Text**</span></span>

-   <span data-ttu-id="07bd5-183">**添加计算成员**（![添加计算成员](../analysis-services/media/rsqdicon-addcalculatedmember.gif "添加计算成员")）</span><span class="sxs-lookup"><span data-stu-id="07bd5-183">**Add Calculated Member** (![Add calculated member](../analysis-services/media/rsqdicon-addcalculatedmember.gif "Add calculated member"))</span></span>

-   <span data-ttu-id="07bd5-184">**显示空单元格**（![切换为显示空单元格](../analysis-services/media/rsqdicon-showemptycells.gif "切换为显示空单元格")）</span><span class="sxs-lookup"><span data-stu-id="07bd5-184">**Show Empty Cells** (![Toggle for show empty cells](../analysis-services/media/rsqdicon-showemptycells.gif "Toggle for show empty cells"))</span></span>

-   <span data-ttu-id="07bd5-185">**自动执行**（![自动执行查询](../analysis-services/media/rsqdicon-autoexecute.gif "自动执行查询")）</span><span class="sxs-lookup"><span data-stu-id="07bd5-185">**AutoExecute** (![AutoExecute the query](../analysis-services/media/rsqdicon-autoexecute.gif "AutoExecute the query"))</span></span>

## <a name="see-also"></a><span data-ttu-id="07bd5-186">另请参阅</span><span class="sxs-lookup"><span data-stu-id="07bd5-186">See Also</span></span>
 [<span data-ttu-id="07bd5-187">查询设计器（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="07bd5-187">Query Designers &#40;Report Builder&#41;</span></span>](../../2014/reporting-services/query-designers-report-builder.md)


