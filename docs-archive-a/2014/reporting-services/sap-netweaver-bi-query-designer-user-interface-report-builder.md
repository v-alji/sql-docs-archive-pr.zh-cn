---
title: SAP NetWeaver BI 查询设计器用户界面 (报表生成器) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10014"
helpviewer_keywords:
- query designers, SAP
ms.assetid: 8edda06d-1608-498b-bd50-10905e54f6ce
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 69a009322bd2d4dcd7211e6b21aa3ecd7c9466e5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579471"
---
# <a name="sap-netweaver-bi-query-designer-user-interface-report-builder"></a><span data-ttu-id="bf8f6-102">SAP NetWeaver BI 查询设计器用户界面（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="bf8f6-102">SAP NetWeaver BI Query Designer User Interface (Report Builder)</span></span>
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="bf8f6-103">提供了图形查询设计器，可用于为 SAP NetWeaver® Business Intelligence 数据源生成多维表达式 (MDX) 查询。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-103">provides a graphical query designer for building Multidimensional Expression (MDX) queries for a SAP NetWeaver® Business Intelligence data source.</span></span> <span data-ttu-id="bf8f6-104">MDX 图形查询设计器有两种模式：设计模式和查询模式。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-104">The MDX graphical query designer has two modes: Design mode and Query mode.</span></span> <span data-ttu-id="bf8f6-105">每种模式都提供一个元数据窗格，在该窗格中，您可以从 InfoCube、MultiProvider 或根据数据源定义的启用 Web 的查询中拖动成员，创建 MDX 查询以便在处理报表时检索数据。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-105">Each mode provides a Metadata pane from which you can drag members from an InfoCube, MultiProvider, or Web-enabled query defined on the data source to build an MDX query that retrieves data when the report is processed.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="bf8f6-106">用户创建和运行查询时访问数据源。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-106">Users access data sources when they create and run queries.</span></span> <span data-ttu-id="bf8f6-107">您应授予对数据源的最小权限（如只读权限）。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-107">You should grant minimal permissions on the data sources, such as read-only permissions.</span></span>

 <span data-ttu-id="bf8f6-108">本节介绍每种模式的图形查询设计器中的工具栏按钮和查询设计器窗格。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-108">This section describes the toolbar buttons and query designer panes for each mode of the graphical query designer.</span></span>

## <a name="graphical-query-designer-in-design-mode"></a><span data-ttu-id="bf8f6-109">设计模式下的图形查询设计器</span><span class="sxs-lookup"><span data-stu-id="bf8f6-109">Graphical Query Designer in Design Mode</span></span>
 <span data-ttu-id="bf8f6-110">编辑使用 [!INCLUDE[SAP_DPE_BW_1](../includes/sap-dpe-bw-1-md.md)] 数据源的数据集查询时，图形查询设计器将以设计模式打开。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-110">When you edit a dataset query that uses a [!INCLUDE[SAP_DPE_BW_1](../includes/sap-dpe-bw-1-md.md)] data source, the graphical query designer opens in the Design mode.</span></span>

 <span data-ttu-id="bf8f6-111">![在设计模式下使用 MDX 的查询设计器](media/rsqd-dssapbw-mdx-designmode.gif "在设计模式下使用 MDX 的查询设计器")</span><span class="sxs-lookup"><span data-stu-id="bf8f6-111">![Query Designer using MDX in Design Mode](media/rsqd-dssapbw-mdx-designmode.gif "Query Designer using MDX in Design Mode")</span></span>

 <span data-ttu-id="bf8f6-112">下表列出了设计模式下的窗格。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-112">The following table lists the panes in this mode.</span></span>

|<span data-ttu-id="bf8f6-113">窗格</span><span class="sxs-lookup"><span data-stu-id="bf8f6-113">Pane</span></span>|<span data-ttu-id="bf8f6-114">函数</span><span class="sxs-lookup"><span data-stu-id="bf8f6-114">Function</span></span>|
|----------|--------------|
|<span data-ttu-id="bf8f6-115">“选择多维数据集”按钮</span><span class="sxs-lookup"><span data-stu-id="bf8f6-115">Select Cube button</span></span>|<span data-ttu-id="bf8f6-116">显示当前选择的 InfoCube、MultiProvider 或启用 Web 的查询。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-116">Displays the currently selected InfoCube, MultiProvider, or Web-enabled query.</span></span>|
|<span data-ttu-id="bf8f6-117">“元数据”窗格</span><span class="sxs-lookup"><span data-stu-id="bf8f6-117">Metadata pane</span></span>|<span data-ttu-id="bf8f6-118">显示 InfoCube、MultiProvider 和查询的层次列表。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-118">Displays a hierarchical list of InfoCubes, MultiProviders, and queries.</span></span> <span data-ttu-id="bf8f6-119">在数据源中创建的查询可能显示在相应的多维数据集下。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-119">Queries created at the data source may appear under the corresponding cube.</span></span>|
|<span data-ttu-id="bf8f6-120">“计算成员”窗格</span><span class="sxs-lookup"><span data-stu-id="bf8f6-120">Calculated Members pane</span></span>|<span data-ttu-id="bf8f6-121">显示当前定义的可在查询中使用的计算成员。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-121">Displays the currently defined calculated members available for use in the query.</span></span>|
|<span data-ttu-id="bf8f6-122">“数据”窗格</span><span class="sxs-lookup"><span data-stu-id="bf8f6-122">Data pane</span></span>|<span data-ttu-id="bf8f6-123">显示运行查询的结果。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-123">Displays the results of running the query.</span></span>|

 <span data-ttu-id="bf8f6-124">可以将“元数据”窗格中的维度和关键数字以及“计算成员”窗格中的计算成员拖至“数据”窗格。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-124">You can drag dimensions and key figures from the Metadata pane, and calculated members from the Calculated Member pane onto the Data pane.</span></span> <span data-ttu-id="bf8f6-125">如果工具栏中的 **“自动执行”** 切换按钮为“开”，则每次将对象拖到“数据”窗格时，查询设计器都将运行查询。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-125">If the **AutoExecute** toggle button on the toolbar is on, the query designer runs the query every time you drop an object onto the Data pane.</span></span> <span data-ttu-id="bf8f6-126">如果 **“自动执行”** 为“关”，则对“数据”窗格进行更改时，查询设计器将不运行查询。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-126">If **AutoExecute** is off, the query designer does not run the query as you make changes to the Data pane.</span></span> <span data-ttu-id="bf8f6-127">使用工具栏上的 **“运行”** 按钮可以手动运行查询。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-127">You can manually run the query using the **Run** button on the toolbar.</span></span>

### <a name="toolbar-for-the-graphical-query-designer-in-design-mode-toolbar"></a><span data-ttu-id="bf8f6-128">设计模式下的图形查询设计器工具栏</span><span class="sxs-lookup"><span data-stu-id="bf8f6-128">Toolbar for the Graphical Query Designer in Design Mode Toolbar</span></span>
 <span data-ttu-id="bf8f6-129">查询设计器工具栏提供了可以帮助您使用图形界面来设计 MDX 查询的按钮。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-129">The query designer toolbar provides buttons to help you design MDX queries using the graphical interface.</span></span> <span data-ttu-id="bf8f6-130">下表介绍了这些按钮及其功能。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-130">The following table describes the buttons and their functions.</span></span>

|<span data-ttu-id="bf8f6-131">Button</span><span class="sxs-lookup"><span data-stu-id="bf8f6-131">Button</span></span>|<span data-ttu-id="bf8f6-132">描述</span><span class="sxs-lookup"><span data-stu-id="bf8f6-132">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="bf8f6-133">**编辑为文本**</span><span class="sxs-lookup"><span data-stu-id="bf8f6-133">**Edit As Text**</span></span>|<span data-ttu-id="bf8f6-134">在基于文本的查询设计器和图形查询设计器之间切换。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-134">Toggle between the text-based query designer and the graphical query designer.</span></span> <span data-ttu-id="bf8f6-135">不可用于此数据源类型。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-135">Not available for this data source type.</span></span>|
|<span data-ttu-id="bf8f6-136">**导入**</span><span class="sxs-lookup"><span data-stu-id="bf8f6-136">**Import**</span></span>|<span data-ttu-id="bf8f6-137">从文件系统中的报表定义 (.rdl) 文件导入现有查询。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-137">Import an existing query from a report definition (.rdl) file on the file system.</span></span>|
|<span data-ttu-id="bf8f6-138">![刷新数据集字段](media/rsqdicon-refreshfields.gif "刷新数据集字段")</span><span class="sxs-lookup"><span data-stu-id="bf8f6-138">![Refresh dataset fields](media/rsqdicon-refreshfields.gif "Refresh dataset fields")</span></span>|<span data-ttu-id="bf8f6-139">刷新数据源的元数据。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-139">Refresh metadata from the data source.</span></span>|
|<span data-ttu-id="bf8f6-140">![添加计算成员](../analysis-services/media/rsqdicon-addcalculatedmember.gif "添加计算成员")</span><span class="sxs-lookup"><span data-stu-id="bf8f6-140">![Add calculated member](../analysis-services/media/rsqdicon-addcalculatedmember.gif "Add calculated member")</span></span>|<span data-ttu-id="bf8f6-141">显示 **“计算成员生成器”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-141">Display the **Calculated Member Builder** dialog box.</span></span>|
|<span data-ttu-id="bf8f6-142">![切换显示空单元](../analysis-services/media/rsqdicon-showemptycells.gif "切换为显示空单元格")</span><span class="sxs-lookup"><span data-stu-id="bf8f6-142">![Toggle for show empty cells](../analysis-services/media/rsqdicon-showemptycells.gif "Toggle for show empty cells")</span></span>|<span data-ttu-id="bf8f6-143">在“数据”窗格中的显示或不显示空单元格之间切换。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-143">Switch between showing and not showing empty cells in the Data pane.</span></span> <span data-ttu-id="bf8f6-144">（这等同于在 MDX 中使用 NON EMPTY 子句）。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-144">(This is the equivalent to using the NON EMPTY clause in MDX).</span></span>|
|<span data-ttu-id="bf8f6-145">![自动执行查询](../analysis-services/media/rsqdicon-autoexecute.gif "自动执行查询")</span><span class="sxs-lookup"><span data-stu-id="bf8f6-145">![AutoExecute the query](../analysis-services/media/rsqdicon-autoexecute.gif "AutoExecute the query")</span></span>|<span data-ttu-id="bf8f6-146">自动运行查询并在每次更改（如在“数据”窗格中删除一列）之后显示结果。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-146">Automatically run the query and show the result every time a change is made, for example, deleting a column in the Data pane.</span></span> <span data-ttu-id="bf8f6-147">结果将显示在“数据”窗格中。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-147">Results are shown in the Data pane.</span></span>|
|<span data-ttu-id="bf8f6-148">![删除](../analysis-services/media/rsqdicon-delete.gif "删除")</span><span class="sxs-lookup"><span data-stu-id="bf8f6-148">![Delete](../analysis-services/media/rsqdicon-delete.gif "Delete")</span></span>|<span data-ttu-id="bf8f6-149">通过查询在“数据”窗格中删除选定列。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-149">Delete the selected column in the Data pane from the query.</span></span>|
|<span data-ttu-id="bf8f6-150">![“查询参数”对话框图标](../analysis-services/media/iconqueryparameter.gif "“查询参数”对话框图标")</span><span class="sxs-lookup"><span data-stu-id="bf8f6-150">![Icon for the Query Parameters dialog box](../analysis-services/media/iconqueryparameter.gif "Icon for the Query Parameters dialog box")</span></span>|<span data-ttu-id="bf8f6-151">显示 **“变量”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-151">Display the **Variables** dialog box.</span></span> <span data-ttu-id="bf8f6-152">仅当选定的多维数据集为“查询”多维数据集时此按钮才可用（因为只有“查询”多维数据集支持变量）。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-152">This button is enabled only when the selected cube is a Query cube (because only query cubes support variables).</span></span> <span data-ttu-id="bf8f6-153">当向变量分配默认值时，将创建一个相应的报表参数。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-153">When you assign a default value to a variable, a corresponding report parameter is created.</span></span>|
|<span data-ttu-id="bf8f6-154">![运行查询](../analysis-services/media/rsqdicon-run.gif "运行查询")</span><span class="sxs-lookup"><span data-stu-id="bf8f6-154">![Run the query](../analysis-services/media/rsqdicon-run.gif "Run the query")</span></span>|<span data-ttu-id="bf8f6-155">运行查询并在“数据”窗格中显示结果。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-155">Run the query and display the results in the Data pane.</span></span>|
|<span data-ttu-id="bf8f6-156">![取消查询](../analysis-services/media/rsqdicon-cancel.gif "取消查询")</span><span class="sxs-lookup"><span data-stu-id="bf8f6-156">![Cancel the query](../analysis-services/media/rsqdicon-cancel.gif "Cancel the query")</span></span>|<span data-ttu-id="bf8f6-157">取消查询。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-157">Cancel the query.</span></span>|
|<span data-ttu-id="bf8f6-158">![切换到设计模式](../analysis-services/media/rsqdicon-designmode.gif "切换到设计模式")</span><span class="sxs-lookup"><span data-stu-id="bf8f6-158">![Switch to Design mode](../analysis-services/media/rsqdicon-designmode.gif "Switch to Design mode")</span></span>|<span data-ttu-id="bf8f6-159">在设计模式和查询模式之间切换。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-159">Switch between Design mode and Query mode.</span></span>|

## <a name="graphical-query-designer-in-query-mode"></a><span data-ttu-id="bf8f6-160">查询模式下的图形查询设计器</span><span class="sxs-lookup"><span data-stu-id="bf8f6-160">Graphical Query Designer in Query Mode</span></span>
 <span data-ttu-id="bf8f6-161">若要将图形查询设计器更改为查询模式，请单击工具栏上的 **“设计模式”** 切换按钮。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-161">To change the graphical query designer to Query mode, click the **Design Mode** toggle button on the toolbar.</span></span>

 <span data-ttu-id="bf8f6-162">下图列出了查询模式下查询设计器的各个部分。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-162">The following figure indicates the parts of the query designer in Query mode.</span></span>

 <span data-ttu-id="bf8f6-163">![查询视图中的 SAP BW MDX 查询设计器](media/rsqd-dssapbw-mdx-querymode.gif "查询视图中的 SAP BW MDX 查询设计器")</span><span class="sxs-lookup"><span data-stu-id="bf8f6-163">![SAP BW MDX query designer in query view](media/rsqd-dssapbw-mdx-querymode.gif "SAP BW MDX query designer in query view")</span></span>

 <span data-ttu-id="bf8f6-164">下表介绍了每个窗格的功能。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-164">The following table describes the function of each pane.</span></span>

|<span data-ttu-id="bf8f6-165">窗格</span><span class="sxs-lookup"><span data-stu-id="bf8f6-165">Pane</span></span>|<span data-ttu-id="bf8f6-166">函数</span><span class="sxs-lookup"><span data-stu-id="bf8f6-166">Function</span></span>|
|----------|--------------|
|<span data-ttu-id="bf8f6-167">“选择多维数据集”按钮</span><span class="sxs-lookup"><span data-stu-id="bf8f6-167">Select Cube button</span></span>|<span data-ttu-id="bf8f6-168">显示当前选择的 InfoCube、MultiProvider 或其他多维数据集。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-168">Displays the currently selected InfoCube, MultiProvider, or other cube.</span></span>|
|<span data-ttu-id="bf8f6-169">“元数据/函数”窗格</span><span class="sxs-lookup"><span data-stu-id="bf8f6-169">Metadata/Functions pane</span></span>|<span data-ttu-id="bf8f6-170">显示一个选项卡式窗口，其中列出了可用于创建查询文本的元数据或函数列表。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-170">Displays a tabbed window that shows a list of available metadata or functions that can be used to build the query text.</span></span>|
|<span data-ttu-id="bf8f6-171">“变量”窗格</span><span class="sxs-lookup"><span data-stu-id="bf8f6-171">Variables pane</span></span>|<span data-ttu-id="bf8f6-172">显示当前定义的可在查询中使用的变量。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-172">Displays the currently defined variables available for use in the query.</span></span>|
|<span data-ttu-id="bf8f6-173">“查询”窗格</span><span class="sxs-lookup"><span data-stu-id="bf8f6-173">Query pane</span></span>|<span data-ttu-id="bf8f6-174">显示当前的查询文本。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-174">Displays the current query text.</span></span>|
|<span data-ttu-id="bf8f6-175">“结果”窗格</span><span class="sxs-lookup"><span data-stu-id="bf8f6-175">Result pane</span></span>|<span data-ttu-id="bf8f6-176">显示查询的结果。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-176">Displays the results of the query.</span></span>|

 <span data-ttu-id="bf8f6-177">在“元数据”窗格中，您可以将关键数字和维度从 **“元数据”** 选项卡拖到“MDX 查询”窗格，元数据的技术名称将在光标处插入。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-177">From the Metadata pane, you can drag key figures and dimensions from the **Metadata** tab onto the MDX Query pane; the technical name for the metadata is inserted at the cursor.</span></span> <span data-ttu-id="bf8f6-178">还可以将函数从 **“函数”** 选项卡拖到“MDX 查询”窗格。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-178">You can drag functions from the **Functions** tab onto the MDX Query pane.</span></span> <span data-ttu-id="bf8f6-179">当执行查询时，“结果”窗格将显示当前 MDX 查询的结果。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-179">When you execute the query, the Result pane displays the results for the current MDX query.</span></span>

 <span data-ttu-id="bf8f6-180">如果选中的多维数据集是启用 Web 的查询，系统将提示您为现有变量设置静态默认值。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-180">If your selected cube is a Web-enabled query, you will be prompted to set static default values for the existing variables.</span></span> <span data-ttu-id="bf8f6-181">然后可以将变量拖到“MDX 查询”窗格。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-181">You can then drag variables onto the MDX Query pane.</span></span>

 <span data-ttu-id="bf8f6-182">“元数据”和“变量”窗格会显示友好名称。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-182">The Metadata and Variable panes display friendly names.</span></span> <span data-ttu-id="bf8f6-183">将对象拖到“MDX 查询”窗格时，可以看到数据源所需要的技术名称会输入到 MDX 查询中。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-183">When you drop the objects onto the MDX Query pane, you see the technical names needed by the data source entered into the MDX query.</span></span>

### <a name="toolbar-for-the-graphical-query-designer-in-query-mode"></a><span data-ttu-id="bf8f6-184">查询模式下的图形查询设计器工具栏</span><span class="sxs-lookup"><span data-stu-id="bf8f6-184">Toolbar for the Graphical Query Designer in Query Mode</span></span>
 <span data-ttu-id="bf8f6-185">查询设计器工具栏提供了可以帮助您使用图形界面来设计 MDX 查询的按钮。</span><span class="sxs-lookup"><span data-stu-id="bf8f6-185">The query designer toolbar provides buttons to help you design MDX queries using the graphical interface.</span></span> <span data-ttu-id="bf8f6-186">工具栏按钮在设计模式和查询模式下是相同的，但是下列按钮在查询模式下不可用：</span><span class="sxs-lookup"><span data-stu-id="bf8f6-186">The toolbar buttons are identical between Design mode and Query mode, but the following buttons are not enabled for Query mode:</span></span>

-   <span data-ttu-id="bf8f6-187">**编辑为文本**</span><span class="sxs-lookup"><span data-stu-id="bf8f6-187">**Edit As Text**</span></span>

-   <span data-ttu-id="bf8f6-188">**添加计算成员**（![添加计算成员](../analysis-services/media/rsqdicon-addcalculatedmember.gif "添加计算成员")）</span><span class="sxs-lookup"><span data-stu-id="bf8f6-188">**Add Calculated Member** (![Add calculated member](../analysis-services/media/rsqdicon-addcalculatedmember.gif "Add calculated member"))</span></span>

-   <span data-ttu-id="bf8f6-189">**显示空单元格**（![切换为显示空单元格](../analysis-services/media/rsqdicon-showemptycells.gif "切换为显示空单元格")）</span><span class="sxs-lookup"><span data-stu-id="bf8f6-189">**Show Empty Cells** (![Toggle for show empty cells](../analysis-services/media/rsqdicon-showemptycells.gif "Toggle for show empty cells"))</span></span>

-   <span data-ttu-id="bf8f6-190">**自动执行**（![自动执行查询](../analysis-services/media/rsqdicon-autoexecute.gif "自动执行查询")）</span><span class="sxs-lookup"><span data-stu-id="bf8f6-190">**AutoExecute** (![AutoExecute the query](../analysis-services/media/rsqdicon-autoexecute.gif "AutoExecute the query"))</span></span>

-   <span data-ttu-id="bf8f6-191">**删除**（![删除](../analysis-services/media/rsqdicon-delete.gif "删除")）</span><span class="sxs-lookup"><span data-stu-id="bf8f6-191">**Delete** (![Delete](../analysis-services/media/rsqdicon-delete.gif "Delete"))</span></span>

## <a name="see-also"></a><span data-ttu-id="bf8f6-192">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bf8f6-192">See Also</span></span>
 [<span data-ttu-id="bf8f6-193">查询设计器（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="bf8f6-193">Query Designers &#40;Report Builder&#41;</span></span>](../../2014/reporting-services/query-designers-report-builder.md)


