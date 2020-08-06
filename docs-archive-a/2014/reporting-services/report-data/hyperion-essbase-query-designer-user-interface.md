---
title: Hyperion Essbase 查询设计器用户界面 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10013"
- sql12.rtp.rptdesigner.dataview.hyperionessbasequerydesigner.f1
helpviewer_keywords:
- Hyperion Essbase Query Designer
- data sources [Reporting Services], Hyperion Essbase
- multidimensional data [Reporting Services]
- query designers [Reporting Services]
- Hyperion Essbase [Reporting Services], query designer
ms.assetid: bc91b422-c6ab-4062-a300-8290fae6191b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1bc53c0f772027b9802bb83d5491aa13fd1492b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577322"
---
# <a name="hyperion-essbase-query-designer-user-interface"></a><span data-ttu-id="b45be-102">Hyperion Essbase 查询设计器用户界面</span><span class="sxs-lookup"><span data-stu-id="b45be-102">Hyperion Essbase Query Designer User Interface</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="b45be-103">提供了一个图形查询设计器，用于为 [!INCLUDE[extEssbase](../../../includes/extessbase-md.md)] 数据源生成多维表达式 (MDX) 查询。</span><span class="sxs-lookup"><span data-stu-id="b45be-103">provides a graphical query designer for building Multidimensional Expression (MDX) queries for a [!INCLUDE[extEssbase](../../../includes/extessbase-md.md)] data source.</span></span> <span data-ttu-id="b45be-104">MDX 图形查询设计器有两种模式：设计模式和查询模式。</span><span class="sxs-lookup"><span data-stu-id="b45be-104">The MDX graphical query designer has two modes: Design mode and Query mode.</span></span> <span data-ttu-id="b45be-105">每种模式都提供一个“元数据”窗格，从该窗格中可以拖动在数据源中定义的多维数据集的成员，以生成可在处理报表时检索数据的 MDX 查询。</span><span class="sxs-lookup"><span data-stu-id="b45be-105">Each mode provides a Metadata pane from which you can drag members from a cube defined on the data source to build an MDX query that retrieves data when the report is processed.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="b45be-106">用户创建和运行查询时访问数据源。</span><span class="sxs-lookup"><span data-stu-id="b45be-106">Users access data sources when they create and run queries.</span></span> <span data-ttu-id="b45be-107">您应授予对数据源的最小权限（如只读权限）。</span><span class="sxs-lookup"><span data-stu-id="b45be-107">You should grant minimal permissions on the data sources, such as read-only permissions.</span></span>

 <span data-ttu-id="b45be-108">有关使用 [!INCLUDE[extEssbase](../../../includes/extessbase-md.md)] 多维数据源的详细信息，请参阅 [Hyperion Essbase 连接类型 (SSRS)](hyperion-essbase-connection-type-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="b45be-108">For more information about working with a [!INCLUDE[extEssbase](../../../includes/extessbase-md.md)] multidimensional data source, see [Hyperion Essbase Connection Type &#40;SSRS&#41;](hyperion-essbase-connection-type-ssrs.md).</span></span>

 <span data-ttu-id="b45be-109">本节介绍每种模式的图形查询设计器中的工具栏按钮和查询设计器窗格。</span><span class="sxs-lookup"><span data-stu-id="b45be-109">This section describes the toolbar buttons and query designer panes for each mode of the graphical query designer.</span></span>

## <a name="graphical-query-designer-in-design-mode"></a><span data-ttu-id="b45be-110">设计模式下的图形查询设计器</span><span class="sxs-lookup"><span data-stu-id="b45be-110">Graphical Query Designer in Design Mode</span></span>
 <span data-ttu-id="b45be-111">为使用 [!INCLUDE[extEssbase](../../../includes/extessbase-md.md)] 数据源的数据集编辑 MDX 查询时，图形查询设计器将在设计模式下打开。</span><span class="sxs-lookup"><span data-stu-id="b45be-111">When you edit an MDX query for a dataset that uses a [!INCLUDE[extEssbase](../../../includes/extessbase-md.md)] data source, the graphical query designer opens in Design mode.</span></span>

 <span data-ttu-id="b45be-112">下图列出了设计模式的窗格。</span><span class="sxs-lookup"><span data-stu-id="b45be-112">The following figure labels the panes for Design mode.</span></span>

 <span data-ttu-id="b45be-113">![用于 Hyperion Essbase 数据源的查询设计器](../media/rsqd-dshyperionessbase-mdx-designmode.gif "用于 Hyperion Essbase 数据源的查询设计器")</span><span class="sxs-lookup"><span data-stu-id="b45be-113">![Query Designer for Hyperion Essbase data source](../media/rsqd-dshyperionessbase-mdx-designmode.gif "Query Designer for Hyperion Essbase data source")</span></span>

 <span data-ttu-id="b45be-114">下表列出了设计模式下的窗格。</span><span class="sxs-lookup"><span data-stu-id="b45be-114">The following table lists the panes in this mode.</span></span>

|<span data-ttu-id="b45be-115">窗格</span><span class="sxs-lookup"><span data-stu-id="b45be-115">Pane</span></span>|<span data-ttu-id="b45be-116">函数</span><span class="sxs-lookup"><span data-stu-id="b45be-116">Function</span></span>|
|----------|--------------|
|<span data-ttu-id="b45be-117">“选择多维数据集”按钮</span><span class="sxs-lookup"><span data-stu-id="b45be-117">Select Cube button</span></span>|<span data-ttu-id="b45be-118">显示当前选定的多维数据集。</span><span class="sxs-lookup"><span data-stu-id="b45be-118">Displays the currently selected cube.</span></span>|
|<span data-ttu-id="b45be-119">“元数据”窗格</span><span class="sxs-lookup"><span data-stu-id="b45be-119">Metadata pane</span></span>|<span data-ttu-id="b45be-120">显示多维数据集的层次结构列表。</span><span class="sxs-lookup"><span data-stu-id="b45be-120">Displays a hierarchical list of cubes.</span></span>|
|<span data-ttu-id="b45be-121">“计算成员”窗格</span><span class="sxs-lookup"><span data-stu-id="b45be-121">Calculated Members pane</span></span>|<span data-ttu-id="b45be-122">显示当前定义的可在查询中使用的计算成员。</span><span class="sxs-lookup"><span data-stu-id="b45be-122">Displays the currently defined calculated members available for use in the query.</span></span>|
|<span data-ttu-id="b45be-123">“筛选器”窗格</span><span class="sxs-lookup"><span data-stu-id="b45be-123">Filter pane</span></span>|<span data-ttu-id="b45be-124">显示要在查询中应用的筛选器。</span><span class="sxs-lookup"><span data-stu-id="b45be-124">Displays the filters to apply in the query.</span></span>|
|<span data-ttu-id="b45be-125">“数据”窗格</span><span class="sxs-lookup"><span data-stu-id="b45be-125">Data pane</span></span>|<span data-ttu-id="b45be-126">显示运行查询的结果。</span><span class="sxs-lookup"><span data-stu-id="b45be-126">Displays the results of running the query.</span></span>|

 <span data-ttu-id="b45be-127">可以将“元数据”窗格中的维度和度量值以及“计算成员”窗格中的计算成员拖到“数据”窗格中。</span><span class="sxs-lookup"><span data-stu-id="b45be-127">You can drag dimensions and measures from the Metadata pane, and calculated members from the Calculated Member pane onto the Data pane.</span></span> <span data-ttu-id="b45be-128">如果工具栏中的 **“自动执行”** 切换按钮为“开”，则每次将对象拖到“数据”窗格时，查询设计器都将运行查询。</span><span class="sxs-lookup"><span data-stu-id="b45be-128">If the **AutoExecute** toggle button on the toolbar is on, the query designer runs the query every time you drop an object onto the Data pane.</span></span> <span data-ttu-id="b45be-129">如果 **“自动执行”** 为“关”，则对“数据”窗格进行更改时，查询设计器将不运行查询。</span><span class="sxs-lookup"><span data-stu-id="b45be-129">If **AutoExecute** is off, the query designer does not run the query as you make changes to the Data pane.</span></span> <span data-ttu-id="b45be-130">使用工具栏上的 **“运行”** 按钮可以手动运行查询。</span><span class="sxs-lookup"><span data-stu-id="b45be-130">You can manually run the query using the **Run** button on the toolbar.</span></span>

 <span data-ttu-id="b45be-131">在“筛选器”窗格中，可以选择维度值来限制从数据源检索的数据。</span><span class="sxs-lookup"><span data-stu-id="b45be-131">In the Filter pane, you can select dimension values to limit the data retrieved from the data source.</span></span> <span data-ttu-id="b45be-132">在设计模式下的筛选器中定义的值显示在查询模式下的 MDX Where 子句中。</span><span class="sxs-lookup"><span data-stu-id="b45be-132">Values you define in the filter in Design mode appear in the MDX Where clause in Query mode.</span></span>

### <a name="toolbar-for-the-graphical-query-designer-in-design-mode-toolbar"></a><span data-ttu-id="b45be-133">设计模式下的图形查询设计器工具栏</span><span class="sxs-lookup"><span data-stu-id="b45be-133">Toolbar for the Graphical Query Designer in Design Mode Toolbar</span></span>
 <span data-ttu-id="b45be-134">查询设计器工具栏提供了可以帮助您使用图形界面来设计 MDX 查询的按钮。</span><span class="sxs-lookup"><span data-stu-id="b45be-134">The query designer toolbar provides buttons to help you design MDX queries using the graphical interface.</span></span> <span data-ttu-id="b45be-135">下表显示这些按钮并介绍了它们的功能。</span><span class="sxs-lookup"><span data-stu-id="b45be-135">The following table shows the buttons and describes their functions.</span></span>

|<span data-ttu-id="b45be-136">按钮</span><span class="sxs-lookup"><span data-stu-id="b45be-136">Button</span></span>|<span data-ttu-id="b45be-137">说明</span><span class="sxs-lookup"><span data-stu-id="b45be-137">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="b45be-138">**编辑为文本**</span><span class="sxs-lookup"><span data-stu-id="b45be-138">**Edit As Text**</span></span>|<span data-ttu-id="b45be-139">在基于文本的查询设计器和图形查询设计器之间切换。</span><span class="sxs-lookup"><span data-stu-id="b45be-139">Toggle between the text-based query designer and the graphical query designer.</span></span> <span data-ttu-id="b45be-140">不可用于此数据源类型。</span><span class="sxs-lookup"><span data-stu-id="b45be-140">Not available for this data source type.</span></span>|
|<span data-ttu-id="b45be-141">**导入**</span><span class="sxs-lookup"><span data-stu-id="b45be-141">**Import**</span></span>|<span data-ttu-id="b45be-142">从文件系统中的报表定义 (.rdl) 文件导入现有查询。</span><span class="sxs-lookup"><span data-stu-id="b45be-142">Import an existing query from a report definition (.rdl) file on the file system.</span></span> <span data-ttu-id="b45be-143">有关详细信息，请参阅 [报表的嵌入数据集和共享数据集（报表生成器和 SSRS）](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="b45be-143">For more information, see [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).</span></span>|
|<span data-ttu-id="b45be-144">![刷新数据集字段](../media/rsqdicon-refreshfields.gif "刷新数据集字段")</span><span class="sxs-lookup"><span data-stu-id="b45be-144">![Refresh dataset fields](../media/rsqdicon-refreshfields.gif "Refresh dataset fields")</span></span>|<span data-ttu-id="b45be-145">刷新数据源的元数据。</span><span class="sxs-lookup"><span data-stu-id="b45be-145">Refresh metadata from the data source.</span></span>|
|<span data-ttu-id="b45be-146">![添加计算成员](../../analysis-services/media/rsqdicon-addcalculatedmember.gif "添加计算成员")</span><span class="sxs-lookup"><span data-stu-id="b45be-146">![Add calculated member](../../analysis-services/media/rsqdicon-addcalculatedmember.gif "Add calculated member")</span></span>|<span data-ttu-id="b45be-147">显示 **“计算成员生成器”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="b45be-147">Display the **Calculated Member Builder** dialog box.</span></span> <span data-ttu-id="b45be-148">使用此按钮可以创建或编辑计算成员表达式，其中包括设置 **“求解次序”** 属性。</span><span class="sxs-lookup"><span data-stu-id="b45be-148">Use this to create or edit expressions for a calculated member, including setting the **Solve Order** property.</span></span>|
|<span data-ttu-id="b45be-149">![切换为显示空单元格](../../analysis-services/media/rsqdicon-showemptycells.gif "切换为显示空单元格")</span><span class="sxs-lookup"><span data-stu-id="b45be-149">![Toggle for show empty cells](../../analysis-services/media/rsqdicon-showemptycells.gif "Toggle for show empty cells")</span></span>|<span data-ttu-id="b45be-150">在“数据”窗格中的显示或不显示空单元格之间切换。</span><span class="sxs-lookup"><span data-stu-id="b45be-150">Switch between showing and not showing empty cells in the Data pane.</span></span> <span data-ttu-id="b45be-151">（这等同于在 MDX 中使用 NON EMPTY 子句）。</span><span class="sxs-lookup"><span data-stu-id="b45be-151">(This is the equivalent to using the NON EMPTY clause in MDX).</span></span>|
|<span data-ttu-id="b45be-152">![自动执行查询](../../analysis-services/media/rsqdicon-autoexecute.gif "自动执行查询")</span><span class="sxs-lookup"><span data-stu-id="b45be-152">![AutoExecute the query](../../analysis-services/media/rsqdicon-autoexecute.gif "AutoExecute the query")</span></span>|<span data-ttu-id="b45be-153">自动运行查询并在每次更改（如在“数据”窗格中删除一列）之后显示结果。</span><span class="sxs-lookup"><span data-stu-id="b45be-153">Automatically run the query and show the result every time a change is made, for example, deleting a column in the Data pane.</span></span> <span data-ttu-id="b45be-154">结果将显示在“数据”窗格中。</span><span class="sxs-lookup"><span data-stu-id="b45be-154">Results are shown in the Data pane.</span></span>|
|<span data-ttu-id="b45be-155">![删除](../../analysis-services/media/rsqdicon-delete.gif "删除")</span><span class="sxs-lookup"><span data-stu-id="b45be-155">![Delete](../../analysis-services/media/rsqdicon-delete.gif "Delete")</span></span>|<span data-ttu-id="b45be-156">从查询中删除选定项。</span><span class="sxs-lookup"><span data-stu-id="b45be-156">Delete the selected item from the query.</span></span> <span data-ttu-id="b45be-157">使用此按钮可以删除“筛选器”窗格中的选定行。</span><span class="sxs-lookup"><span data-stu-id="b45be-157">Use this button to delete selected rows in the Filter pane.</span></span>|
|<span data-ttu-id="b45be-158">![运行查询](../../analysis-services/media/rsqdicon-run.gif "运行查询")</span><span class="sxs-lookup"><span data-stu-id="b45be-158">![Run the query](../../analysis-services/media/rsqdicon-run.gif "Run the query")</span></span>|<span data-ttu-id="b45be-159">运行查询并在“数据”窗格中显示结果。</span><span class="sxs-lookup"><span data-stu-id="b45be-159">Run the query and display the results in the Data pane.</span></span>|
|<span data-ttu-id="b45be-160">![取消查询](../../analysis-services/media/rsqdicon-cancel.gif "取消查询")</span><span class="sxs-lookup"><span data-stu-id="b45be-160">![Cancel the query](../../analysis-services/media/rsqdicon-cancel.gif "Cancel the query")</span></span>|<span data-ttu-id="b45be-161">取消查询。</span><span class="sxs-lookup"><span data-stu-id="b45be-161">Cancel the query.</span></span>|
|<span data-ttu-id="b45be-162">![切换到设计模式](../../analysis-services/media/rsqdicon-designmode.gif "切换到设计模式")</span><span class="sxs-lookup"><span data-stu-id="b45be-162">![Switch to Design mode](../../analysis-services/media/rsqdicon-designmode.gif "Switch to Design mode")</span></span>|<span data-ttu-id="b45be-163">在设计模式和查询模式之间切换。</span><span class="sxs-lookup"><span data-stu-id="b45be-163">Switch between Design mode and Query mode.</span></span>|

## <a name="graphical-query-designer-in-query-mode"></a><span data-ttu-id="b45be-164">查询模式下的图形查询设计器</span><span class="sxs-lookup"><span data-stu-id="b45be-164">Graphical Query Designer in Query Mode</span></span>
 <span data-ttu-id="b45be-165">若要将图形查询设计器更改为查询模式，请单击工具栏上的 **“设计模式”** 切换按钮。</span><span class="sxs-lookup"><span data-stu-id="b45be-165">To change the graphical query designer to Query mode, click the **Design Mode** toggle button on the toolbar.</span></span> <span data-ttu-id="b45be-166">下图列出了查询模式下查询设计器的各个部分。</span><span class="sxs-lookup"><span data-stu-id="b45be-166">The following figure indicates the parts of the query designer in Query mode.</span></span>

 <span data-ttu-id="b45be-167">![用于 Hyperion 的查询模式的查询设计器](../media/rsqd-hyperionessbase-mdx-querymode.gif "用于 Hyperion 的查询模式的查询设计器")</span><span class="sxs-lookup"><span data-stu-id="b45be-167">![Query Designer in Query Mode for Hyperion](../media/rsqd-hyperionessbase-mdx-querymode.gif "Query Designer in Query Mode for Hyperion")</span></span>

 <span data-ttu-id="b45be-168">下表介绍了每个窗格的功能。</span><span class="sxs-lookup"><span data-stu-id="b45be-168">The following table describes the function of each pane.</span></span>

|<span data-ttu-id="b45be-169">窗格</span><span class="sxs-lookup"><span data-stu-id="b45be-169">Pane</span></span>|<span data-ttu-id="b45be-170">函数</span><span class="sxs-lookup"><span data-stu-id="b45be-170">Function</span></span>|
|----------|--------------|
|<span data-ttu-id="b45be-171">“选择多维数据集”按钮</span><span class="sxs-lookup"><span data-stu-id="b45be-171">Select Cube button</span></span>|<span data-ttu-id="b45be-172">显示当前选定的多维数据集。</span><span class="sxs-lookup"><span data-stu-id="b45be-172">Displays the currently selected cube.</span></span>|
|<span data-ttu-id="b45be-173">“元数据/函数”窗格</span><span class="sxs-lookup"><span data-stu-id="b45be-173">Metadata/Functions pane</span></span>|<span data-ttu-id="b45be-174">显示一个选项卡式窗口，其中列出了可用于创建查询文本的元数据或函数列表。</span><span class="sxs-lookup"><span data-stu-id="b45be-174">Displays a tabbed window that shows a list of available metadata or functions that can be used to build the query text.</span></span>|
|<span data-ttu-id="b45be-175">“查询”窗格</span><span class="sxs-lookup"><span data-stu-id="b45be-175">Query pane</span></span>|<span data-ttu-id="b45be-176">显示当前的查询文本。</span><span class="sxs-lookup"><span data-stu-id="b45be-176">Displays the current query text.</span></span>|
|<span data-ttu-id="b45be-177">“结果”窗格</span><span class="sxs-lookup"><span data-stu-id="b45be-177">Result pane</span></span>|<span data-ttu-id="b45be-178">显示查询的结果。</span><span class="sxs-lookup"><span data-stu-id="b45be-178">Displays the results of the query.</span></span>|

 <span data-ttu-id="b45be-179">通过“元数据”窗格，可以将度量值和维度从 **“元数据”** 选项卡拖到“MDX 查询”窗格。</span><span class="sxs-lookup"><span data-stu-id="b45be-179">From the Metadata pane, you can drag measures and dimensions from the **Metadata** tab onto the MDX Query pane.</span></span> <span data-ttu-id="b45be-180">还可以将函数从 **“函数”** 选项卡拖到“MDX 查询”窗格。</span><span class="sxs-lookup"><span data-stu-id="b45be-180">You can drag functions from the **Functions** tab onto the MDX Query pane.</span></span> <span data-ttu-id="b45be-181">当执行查询时，“结果”窗格将显示当前 MDX 查询的结果。</span><span class="sxs-lookup"><span data-stu-id="b45be-181">When you execute the query, the Result pane displays the results for the current MDX query.</span></span>

### <a name="toolbar-for-the-graphical-query-designer-in-query-mode"></a><span data-ttu-id="b45be-182">查询模式下的图形查询设计器工具栏</span><span class="sxs-lookup"><span data-stu-id="b45be-182">Toolbar for the Graphical Query Designer in Query Mode</span></span>
 <span data-ttu-id="b45be-183">查询设计器工具栏提供了可以帮助您使用图形界面来设计 MDX 查询的按钮。</span><span class="sxs-lookup"><span data-stu-id="b45be-183">The query designer toolbar provides buttons to help you design MDX queries using the graphical interface.</span></span> <span data-ttu-id="b45be-184">工具栏按钮在设计模式和查询模式下是相同的，但是下列按钮在查询模式下不可用：</span><span class="sxs-lookup"><span data-stu-id="b45be-184">The toolbar buttons are identical between Design mode and Query mode, but the following buttons are not enabled for Query mode:</span></span>

-   <span data-ttu-id="b45be-185">**编辑为文本**</span><span class="sxs-lookup"><span data-stu-id="b45be-185">**Edit As Text**</span></span>

-   <span data-ttu-id="b45be-186">**添加计算成员**（![添加计算成员](../../analysis-services/media/rsqdicon-addcalculatedmember.gif "添加计算成员")）</span><span class="sxs-lookup"><span data-stu-id="b45be-186">**Add Calculated Member** (![Add calculated member](../../analysis-services/media/rsqdicon-addcalculatedmember.gif "Add calculated member"))</span></span>

-   <span data-ttu-id="b45be-187">**显示空单元格**（![切换为显示空单元格](../../analysis-services/media/rsqdicon-showemptycells.gif "切换为显示空单元格")）</span><span class="sxs-lookup"><span data-stu-id="b45be-187">**Show Empty Cells** (![Toggle for show empty cells](../../analysis-services/media/rsqdicon-showemptycells.gif "Toggle for show empty cells"))</span></span>

-   <span data-ttu-id="b45be-188">**自动执行**（![自动执行查询](../../analysis-services/media/rsqdicon-autoexecute.gif "自动执行查询")）</span><span class="sxs-lookup"><span data-stu-id="b45be-188">**AutoExecute** (![AutoExecute the query](../../analysis-services/media/rsqdicon-autoexecute.gif "AutoExecute the query"))</span></span>

## <a name="see-also"></a><span data-ttu-id="b45be-189">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b45be-189">See Also</span></span>
 <span data-ttu-id="b45be-190">[创建共享数据集或嵌入数据集 &#40;报表生成器和 SSRS&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md) [rsreportdesigner.config 配置文件](../report-server/rsreportdesigner-configuration-file.md)</span><span class="sxs-lookup"><span data-stu-id="b45be-190">[Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md) [RSReportDesigner Configuration File](../report-server/rsreportdesigner-configuration-file.md)</span></span>


