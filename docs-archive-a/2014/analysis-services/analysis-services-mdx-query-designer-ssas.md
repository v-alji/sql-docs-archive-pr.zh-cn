---
title: Analysis Services 的 MDX 查询设计器 (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.asmdxquerydes.f1
ms.assetid: a2fb0b79-802a-4dac-bd9a-32dfe2e8c4d4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 98c08da8e7caaba268346075a3bb3e9e8e5dc3c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579393"
---
# <a name="analysis-services-mdx-query-designer-ssas"></a><span data-ttu-id="33cdb-102">Analysis Services MDX 查询设计器 (SSAS)</span><span class="sxs-lookup"><span data-stu-id="33cdb-102">Analysis Services MDX Query Designer (SSAS)</span></span>
  <span data-ttu-id="33cdb-103">Analysis Services 多维表达式 (MDX) 查询设计器提供了图形用户界面，可帮助您为数据源创建 MDX 查询 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="33cdb-103">The Analysis Services Multidimensional Expression (MDX) query designer provides a graphical user interfaces to help you create MDX queries for a [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] data source.</span></span> <span data-ttu-id="33cdb-104">MDX 图形查询设计器有两种模式：设计模式和查询模式。</span><span class="sxs-lookup"><span data-stu-id="33cdb-104">The MDX graphical query designer has two modes: design mode and query mode.</span></span> <span data-ttu-id="33cdb-105">每种模式都提供一个“元数据”窗格，从该窗格中可以拖动所选多维数据集的成员，以生成可检索要使用的数据的 MDX 查询。</span><span class="sxs-lookup"><span data-stu-id="33cdb-105">Each mode provides a metadata pane from which you can drag members from the selected cubes to build an MDX query that retrieves the data you want to use.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="33cdb-106">用户创建和运行查询时访问数据源。</span><span class="sxs-lookup"><span data-stu-id="33cdb-106">Users access data sources when they create and run queries.</span></span> <span data-ttu-id="33cdb-107">您应授予对数据源的最小权限（如只读权限）。</span><span class="sxs-lookup"><span data-stu-id="33cdb-107">You should grant minimal permissions on the data sources, such as read-only permissions.</span></span>  
>   
>  <span data-ttu-id="33cdb-108">在执行查询时，当前用户的凭据（而非在“模拟信息”页中指定的凭据）用于连接到数据源并提取数据。</span><span class="sxs-lookup"><span data-stu-id="33cdb-108">The credentials of the current user, not the credentials specified in the Impersonation Information page, are used to connect to the data source when a query is executed.</span></span>  
  
 <span data-ttu-id="33cdb-109">以下几节介绍每种模式的图形查询设计器中的工具栏按钮和查询设计器窗格。</span><span class="sxs-lookup"><span data-stu-id="33cdb-109">The following sections describe the toolbar buttons and query designer panes for each mode of the graphical query designer.</span></span>  
  
## <a name="graphical-mdx-query-designer-in-design-mode"></a><span data-ttu-id="33cdb-110">设计模式下的图形 MDX 查询设计器</span><span class="sxs-lookup"><span data-stu-id="33cdb-110">Graphical MDX Query Designer in Design Mode</span></span>  
 <span data-ttu-id="33cdb-111">编辑 MDX 查询时，图形 MDX 查询设计器将以设计模式打开。</span><span class="sxs-lookup"><span data-stu-id="33cdb-111">When you edit an MDX query, the graphical MDX query designer opens in Design mode.</span></span>  
  
 <span data-ttu-id="33cdb-112">下图列出了设计模式的窗格。</span><span class="sxs-lookup"><span data-stu-id="33cdb-112">The following figure labels the panes for Design mode.</span></span>  
  
 <span data-ttu-id="33cdb-113">![Analysis Services MDX 查询设计器的设计视图](media/rsqd-dsawas-mdx-designmode.gif "Analysis Services MDX 查询设计器的设计视图")</span><span class="sxs-lookup"><span data-stu-id="33cdb-113">![Analysis Services MDX query designer, design view](media/rsqd-dsawas-mdx-designmode.gif "Analysis Services MDX query designer, design view")</span></span>  
  
 <span data-ttu-id="33cdb-114">下表列出了查询模式下的窗格：</span><span class="sxs-lookup"><span data-stu-id="33cdb-114">The following table lists the panes in this mode:</span></span>  
  
|<span data-ttu-id="33cdb-115">窗格</span><span class="sxs-lookup"><span data-stu-id="33cdb-115">Pane</span></span>|<span data-ttu-id="33cdb-116">函数</span><span class="sxs-lookup"><span data-stu-id="33cdb-116">Function</span></span>|  
|----------|--------------|  
|<span data-ttu-id="33cdb-117">选择“多维数据集”按钮 (**...**)</span><span class="sxs-lookup"><span data-stu-id="33cdb-117">Select Cube button (**...**)</span></span>|<span data-ttu-id="33cdb-118">显示当前选定的多维数据集。</span><span class="sxs-lookup"><span data-stu-id="33cdb-118">Displays the currently selected cube.</span></span>|  
|<span data-ttu-id="33cdb-119">“元数据”窗格</span><span class="sxs-lookup"><span data-stu-id="33cdb-119">Metadata pane</span></span>|<span data-ttu-id="33cdb-120">显示在选定多维数据集中定义的度量值、关键绩效指标 (KPI) 和维度的层次列表。</span><span class="sxs-lookup"><span data-stu-id="33cdb-120">Displays a hierarchical list of measures, Key Performance Indicators (KPIs), and dimensions defined on the selected cube.</span></span>|  
|<span data-ttu-id="33cdb-121">“计算成员”窗格</span><span class="sxs-lookup"><span data-stu-id="33cdb-121">Calculated Members pane</span></span>|<span data-ttu-id="33cdb-122">显示当前定义的可在查询中使用的计算成员。</span><span class="sxs-lookup"><span data-stu-id="33cdb-122">Displays the currently defined calculated members available for use in the query.</span></span>|  
|<span data-ttu-id="33cdb-123">“筛选器”窗格</span><span class="sxs-lookup"><span data-stu-id="33cdb-123">Filter pane</span></span>|<span data-ttu-id="33cdb-124">用于选择维度和相关的层次结构，以筛选源中的数据并限制返回的数据。</span><span class="sxs-lookup"><span data-stu-id="33cdb-124">Use to choose dimensions and related hierarchies to filter data at the source and limit data returned.</span></span>|  
|<span data-ttu-id="33cdb-125">“数据”窗格</span><span class="sxs-lookup"><span data-stu-id="33cdb-125">Data pane</span></span>|<span data-ttu-id="33cdb-126">在从“元数据”窗格向“计算成员”窗格拖动项目时，显示结果集的列标题。</span><span class="sxs-lookup"><span data-stu-id="33cdb-126">Displays the column headings for the result set as you drag items from the Metadata pane and the Calculated Members pane.</span></span> <span data-ttu-id="33cdb-127">如果选中 **“自动执行”** 按钮，则可自动更新结果集。</span><span class="sxs-lookup"><span data-stu-id="33cdb-127">Automatically updates the result set if the **AutoExecute** button is selected.</span></span>|  
  
 <span data-ttu-id="33cdb-128">可以将“元数据”窗格中的维度、度量值和 KPI 以及“计算成员”窗格中的计算成员拖至“数据”窗格。</span><span class="sxs-lookup"><span data-stu-id="33cdb-128">You can drag dimensions, measures, and KPIs from the Metadata pane, and calculated members from the Calculated Member pane, onto the Data pane.</span></span> <span data-ttu-id="33cdb-129">在“筛选器”窗格中，您可以选择维度和相关的层次结构，并设置筛选器表达式以限制可用于查询的数据。</span><span class="sxs-lookup"><span data-stu-id="33cdb-129">In the Filter pane, you can select dimensions and related hierarchies, and set filter expressions to limit the data available to query.</span></span> <span data-ttu-id="33cdb-130">如果工具栏上的“自动执行”\*\*\*\*（![自动执行查询](media/rsqdicon-autoexecute.gif "自动执行查询")）切换按钮处于选中状态，那么每当你将元数据对象拖到“数据”窗格时，查询设计器都会运行查询。</span><span class="sxs-lookup"><span data-stu-id="33cdb-130">If the **AutoExecute** (![AutoExecute the query](media/rsqdicon-autoexecute.gif "AutoExecute the query")) toggle button on the toolbar is selected, the query designer runs the query every time that you drop a metadata object onto the Data pane.</span></span> <span data-ttu-id="33cdb-131">可以使用工具栏上的“运行”\*\*\*\*（![运行查询](media/rsqdicon-run.gif "运行查询")）按钮来手动运行查询。</span><span class="sxs-lookup"><span data-stu-id="33cdb-131">You can manually run the query using the **Run** (![Run the query](media/rsqdicon-run.gif "Run the query")) button on the toolbar.</span></span>  
  
 <span data-ttu-id="33cdb-132">在此模式下创建 MDX 查询时，下面的附加属性将会自动包含到查询中：</span><span class="sxs-lookup"><span data-stu-id="33cdb-132">When you create an MDX query in this mode, the following additional properties are automatically included in the query:</span></span>  
  
 <span data-ttu-id="33cdb-133">**成员属性** MEMBER_CAPTION, MEMBER_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="33cdb-133">**Member Properties** MEMBER_CAPTION, MEMBER_UNIQUE_NAME</span></span>  
  
 <span data-ttu-id="33cdb-134">**单元属性** VALUE、BACK_COLOR、FORE_COLOR、FORMATTED_VALUE、FORMAT_STRING、FONT_NAME、FONT_SIZE、FONT_FLAGS</span><span class="sxs-lookup"><span data-stu-id="33cdb-134">**Cell Properties** VALUE, BACK_COLOR, FORE_COLOR, FORMATTED_VALUE, FORMAT_STRING, FONT_NAME, FONT_SIZE, FONT_FLAGS</span></span>  
  
 <span data-ttu-id="33cdb-135">若要指定您自己的附加属性，则必须在查询模式下，手动编辑 MDX 查询。</span><span class="sxs-lookup"><span data-stu-id="33cdb-135">To specify your own additional properties, you must manually edit the MDX query in Query mode.</span></span>  
  
 <span data-ttu-id="33cdb-136">不支持从文件导入 .mdx 查询。</span><span class="sxs-lookup"><span data-stu-id="33cdb-136">Importing an .mdx query from a file is not supported.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="33cdb-137">有关 MDX 的详细信息以及有关 MDX 查询设计器的常规信息，请参阅 [SQL Server 联机丛书](https://go.microsoft.com/fwlink/?linkid=98335)中的“MDX 查询编辑器（Analysis Services - 多维数据）”。</span><span class="sxs-lookup"><span data-stu-id="33cdb-137">For more information about MDX and general information about the MDX query designer, see "MDX Query Editor (Analysis Services - Multidimensional Data)" in [SQL Server Books Online](https://go.microsoft.com/fwlink/?linkid=98335).</span></span>  
  
### <a name="graphical-mdx-query-designer-toolbar-in-design-mode"></a><span data-ttu-id="33cdb-138">设计模式下的图形 MDX 查询设计器工具栏</span><span class="sxs-lookup"><span data-stu-id="33cdb-138">Graphical MDX Query Designer Toolbar in Design Mode</span></span>  
 <span data-ttu-id="33cdb-139">查询设计器工具栏提供了可以帮助您使用图形界面来设计 MDX 查询的按钮。</span><span class="sxs-lookup"><span data-stu-id="33cdb-139">The query designer toolbar provides buttons to help you design MDX queries using the graphical interface.</span></span> <span data-ttu-id="33cdb-140">下表列出了这些按钮及其功能。</span><span class="sxs-lookup"><span data-stu-id="33cdb-140">The following table lists the buttons and their functions.</span></span>  
  
|<span data-ttu-id="33cdb-141">Button</span><span class="sxs-lookup"><span data-stu-id="33cdb-141">Button</span></span>|<span data-ttu-id="33cdb-142">描述</span><span class="sxs-lookup"><span data-stu-id="33cdb-142">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="33cdb-143">**编辑为文本**</span><span class="sxs-lookup"><span data-stu-id="33cdb-143">**Edit As Text**</span></span>|<span data-ttu-id="33cdb-144">不可用于此数据源类型。</span><span class="sxs-lookup"><span data-stu-id="33cdb-144">Not enabled for this data source type.</span></span>|  
|<span data-ttu-id="33cdb-145">**导入**</span><span class="sxs-lookup"><span data-stu-id="33cdb-145">**Import**</span></span>|<span data-ttu-id="33cdb-146">从文件系统中的报表定义 (.rdl) 文件导入现有查询。</span><span class="sxs-lookup"><span data-stu-id="33cdb-146">Import an existing query from a report definition (.rdl) file on the file system.</span></span>|  
|<span data-ttu-id="33cdb-147">![更改为 MDX 查询视图](media/rsqdicon-commandtypemdx.gif "更改为 MDX 查询视图")</span><span class="sxs-lookup"><span data-stu-id="33cdb-147">![Change to MDX query view](media/rsqdicon-commandtypemdx.gif "Change to MDX query view")</span></span>|<span data-ttu-id="33cdb-148">切换到命令类型 MDX。</span><span class="sxs-lookup"><span data-stu-id="33cdb-148">Switch to Command Type MDX.</span></span>|  
|<span data-ttu-id="33cdb-149">![刷新结果数据](media/rsqdicon-refresh.gif "刷新结果数据")</span><span class="sxs-lookup"><span data-stu-id="33cdb-149">![Refresh result data](media/rsqdicon-refresh.gif "Refresh result data")</span></span>|<span data-ttu-id="33cdb-150">刷新数据源的元数据。</span><span class="sxs-lookup"><span data-stu-id="33cdb-150">Refresh metadata from the data source.</span></span>|  
|<span data-ttu-id="33cdb-151">![添加计算成员](media/rsqdicon-addcalculatedmember.gif "添加计算成员")</span><span class="sxs-lookup"><span data-stu-id="33cdb-151">![Add calculated member](media/rsqdicon-addcalculatedmember.gif "Add calculated member")</span></span>|<span data-ttu-id="33cdb-152">显示 **“计算成员生成器”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="33cdb-152">Display the **Calculated Member Builder** dialog box.</span></span>|  
|<span data-ttu-id="33cdb-153">![切换显示空单元](media/rsqdicon-showemptycells.gif "切换为显示空单元格")</span><span class="sxs-lookup"><span data-stu-id="33cdb-153">![Toggle for show empty cells](media/rsqdicon-showemptycells.gif "Toggle for show empty cells")</span></span>|<span data-ttu-id="33cdb-154">在“数据”窗格中的显示或不显示空单元格之间切换。</span><span class="sxs-lookup"><span data-stu-id="33cdb-154">Toggle between showing and not showing empty cells in the Data pane.</span></span> <span data-ttu-id="33cdb-155">（这等同于在 MDX 中使用 NON EMPTY 子句）。</span><span class="sxs-lookup"><span data-stu-id="33cdb-155">(This is the equivalent to using the NON EMPTY clause in MDX).</span></span>|  
|<span data-ttu-id="33cdb-156">![自动执行查询](media/rsqdicon-autoexecute.gif "自动执行查询")</span><span class="sxs-lookup"><span data-stu-id="33cdb-156">![AutoExecute the query](media/rsqdicon-autoexecute.gif "AutoExecute the query")</span></span>|<span data-ttu-id="33cdb-157">在每次进行更改时自动运行查询并显示结果。</span><span class="sxs-lookup"><span data-stu-id="33cdb-157">Automatically run the query and show the result every time a change is made.</span></span> <span data-ttu-id="33cdb-158">结果将显示在“数据”窗格中。</span><span class="sxs-lookup"><span data-stu-id="33cdb-158">Results are shown in the Data pane.</span></span>|  
|<span data-ttu-id="33cdb-159">![“显示聚合”按钮](media/rsqdicon-showaggregations.gif "“显示聚合”按钮")</span><span class="sxs-lookup"><span data-stu-id="33cdb-159">![Show Aggregations button](media/rsqdicon-showaggregations.gif "Show Aggregations button")</span></span>|<span data-ttu-id="33cdb-160">在“数据”窗格中显示聚合。</span><span class="sxs-lookup"><span data-stu-id="33cdb-160">Show aggregations in the Data pane.</span></span>|  
|<span data-ttu-id="33cdb-161">![删除](media/rsqdicon-delete.gif "删除")</span><span class="sxs-lookup"><span data-stu-id="33cdb-161">![Delete](media/rsqdicon-delete.gif "Delete")</span></span>|<span data-ttu-id="33cdb-162">通过查询在“数据”窗格中删除选定列。</span><span class="sxs-lookup"><span data-stu-id="33cdb-162">Delete the selected column in the Data pane from the query.</span></span>|  
|<span data-ttu-id="33cdb-163">![“查询参数”对话框图标](media/iconqueryparameter.gif "“查询参数”对话框图标")</span><span class="sxs-lookup"><span data-stu-id="33cdb-163">![Icon for the Query Parameters dialog box](media/iconqueryparameter.gif "Icon for the Query Parameters dialog box")</span></span>|<span data-ttu-id="33cdb-164">显示 **“查询参数”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="33cdb-164">Display the **Query Parameters** dialog box.</span></span> <span data-ttu-id="33cdb-165">指定查询参数的值时，会自动创建一个同名参数。</span><span class="sxs-lookup"><span data-stu-id="33cdb-165">When you specify values for a query parameter, a parameter with the same name is automatically created.</span></span>|  
|<span data-ttu-id="33cdb-166">![“准备查询”按钮](media/rsqdicon-preparequery.gif "“准备查询”按钮")</span><span class="sxs-lookup"><span data-stu-id="33cdb-166">![Prepare Query button](media/rsqdicon-preparequery.gif "Prepare Query button")</span></span>|<span data-ttu-id="33cdb-167">准备查询。</span><span class="sxs-lookup"><span data-stu-id="33cdb-167">Prepare the query.</span></span>|  
|<span data-ttu-id="33cdb-168">![运行查询](media/rsqdicon-run.gif "运行查询")</span><span class="sxs-lookup"><span data-stu-id="33cdb-168">![Run the query](media/rsqdicon-run.gif "Run the query")</span></span>|<span data-ttu-id="33cdb-169">运行查询并在“数据”窗格中显示结果。</span><span class="sxs-lookup"><span data-stu-id="33cdb-169">Run the query and display the results in the Data pane.</span></span>|  
|<span data-ttu-id="33cdb-170">![取消查询](media/rsqdicon-cancel.gif "取消查询")</span><span class="sxs-lookup"><span data-stu-id="33cdb-170">![Cancel the query](media/rsqdicon-cancel.gif "Cancel the query")</span></span>|<span data-ttu-id="33cdb-171">取消查询。</span><span class="sxs-lookup"><span data-stu-id="33cdb-171">Cancel the query.</span></span>|  
|<span data-ttu-id="33cdb-172">![切换到设计模式](media/rsqdicon-designmode.gif "切换到设计模式")</span><span class="sxs-lookup"><span data-stu-id="33cdb-172">![Switch to Design mode](media/rsqdicon-designmode.gif "Switch to Design mode")</span></span>|<span data-ttu-id="33cdb-173">在设计模式和查询模式之间切换。</span><span class="sxs-lookup"><span data-stu-id="33cdb-173">Toggle between Design mode and Query mode.</span></span>|  
  
## <a name="graphical-mdx-query-designer-in-query-mode"></a><span data-ttu-id="33cdb-174">查询模式下的图形 MDX 查询设计器</span><span class="sxs-lookup"><span data-stu-id="33cdb-174">Graphical MDX Query Designer in Query Mode</span></span>  
 <span data-ttu-id="33cdb-175">若要将图形查询设计器更改为 **“查询”** 模式，请单击工具栏上的 **“设计模式”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="33cdb-175">To change the graphical query designer to **Query** mode, click the **Design Mode** button on the toolbar.</span></span>  
  
 <span data-ttu-id="33cdb-176">下图列出了查询模式的窗格。</span><span class="sxs-lookup"><span data-stu-id="33cdb-176">The following figure labels the panes for Query mode.</span></span>  
  
 <span data-ttu-id="33cdb-177">![Analysis Services MDX 查询设计器的查询视图](media/rsqd-dsawas-mdx-querymode.gif "Analysis Services MDX 查询设计器的查询视图")</span><span class="sxs-lookup"><span data-stu-id="33cdb-177">![Analysis Services MDX query designer, query view](media/rsqd-dsawas-mdx-querymode.gif "Analysis Services MDX query designer, query view")</span></span>  
  
 <span data-ttu-id="33cdb-178">下表列出了查询模式下的窗格：</span><span class="sxs-lookup"><span data-stu-id="33cdb-178">The following table lists the panes in this mode:</span></span>  
  
|<span data-ttu-id="33cdb-179">窗格</span><span class="sxs-lookup"><span data-stu-id="33cdb-179">Pane</span></span>|<span data-ttu-id="33cdb-180">函数</span><span class="sxs-lookup"><span data-stu-id="33cdb-180">Function</span></span>|  
|----------|--------------|  
|<span data-ttu-id="33cdb-181">选择“多维数据集”按钮 (**...**)</span><span class="sxs-lookup"><span data-stu-id="33cdb-181">Select Cube button (**...**)</span></span>|<span data-ttu-id="33cdb-182">显示当前选定的多维数据集。</span><span class="sxs-lookup"><span data-stu-id="33cdb-182">Displays the currently selected cube.</span></span>|  
|<span data-ttu-id="33cdb-183">元数据/函数/模板窗格</span><span class="sxs-lookup"><span data-stu-id="33cdb-183">Metadata/Functions/Templates pane</span></span>|<span data-ttu-id="33cdb-184">显示在选定多维数据集中定义的度量值、KPI 和维度的层次列表。</span><span class="sxs-lookup"><span data-stu-id="33cdb-184">Displays a hierarchical list of measures, KPIs, and dimensions defined on the selected cube.</span></span>|  
|<span data-ttu-id="33cdb-185">“查询”窗格</span><span class="sxs-lookup"><span data-stu-id="33cdb-185">Query pane</span></span>|<span data-ttu-id="33cdb-186">显示查询文本。</span><span class="sxs-lookup"><span data-stu-id="33cdb-186">Displays the query text.</span></span>|  
|<span data-ttu-id="33cdb-187">“结果”窗格</span><span class="sxs-lookup"><span data-stu-id="33cdb-187">Result pane</span></span>|<span data-ttu-id="33cdb-188">显示运行查询的结果。</span><span class="sxs-lookup"><span data-stu-id="33cdb-188">Displays the results of running the query.</span></span>|  
  
 <span data-ttu-id="33cdb-189">“元数据”窗格会显示 **“元数据”** 选项卡、 **“函数”** 选项卡和 **“模板”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="33cdb-189">The Metadata pane displays tabs for **Metadata**, **Functions**, and **Templates**.</span></span> <span data-ttu-id="33cdb-190">通过 **“元数据”** 选项卡，可将维度、层次结构、KPI 和度量值拖到“MDX 查询”窗格中。</span><span class="sxs-lookup"><span data-stu-id="33cdb-190">From the **Metadata** tab, you can drag dimensions, hierarchies, KPIs, and measures onto the MDX Query pane.</span></span> <span data-ttu-id="33cdb-191">通过 **“函数”** 选项卡，可将函数拖到“MDX 查询”窗格中。</span><span class="sxs-lookup"><span data-stu-id="33cdb-191">From the **Functions** tab, you can drag functions onto the MDX Query pane.</span></span> <span data-ttu-id="33cdb-192">通过 **“模板”** 选项卡，可将 MDX 模板添加到“MDX 查询”窗格中。</span><span class="sxs-lookup"><span data-stu-id="33cdb-192">From the **Templates** tab, you can add MDX templates to the MDX Query pane.</span></span> <span data-ttu-id="33cdb-193">执行查询时，“结果”窗格将显示 MDX 查询的结果。</span><span class="sxs-lookup"><span data-stu-id="33cdb-193">When you execute the query, the Result pane displays the results for the MDX query.</span></span>  
  
 <span data-ttu-id="33cdb-194">您可以扩展设计模式下生成的默认 MDX 查询，以包含附加成员属性和单元属性。</span><span class="sxs-lookup"><span data-stu-id="33cdb-194">You can extend the default MDX query generated in Design mode to include additional member properties and cell properties.</span></span> <span data-ttu-id="33cdb-195">运行查询时，这些值不会显示在结果集中。</span><span class="sxs-lookup"><span data-stu-id="33cdb-195">When you run the query, these values do not appear in the result set.</span></span> <span data-ttu-id="33cdb-196">不过，这些值会随同数据集字段集合传递回来，并且您可以使用这些值。</span><span class="sxs-lookup"><span data-stu-id="33cdb-196">However, they are passed back with the dataset field collection and you can use these values.</span></span>  
  
### <a name="graphical-query-designer-toolbar-in-query-mode"></a><span data-ttu-id="33cdb-197">查询模式下的图形查询设计器工具栏</span><span class="sxs-lookup"><span data-stu-id="33cdb-197">Graphical Query Designer Toolbar in Query Mode</span></span>  
 <span data-ttu-id="33cdb-198">查询设计器工具栏提供了可以帮助您使用图形界面来设计 MDX 查询的按钮。</span><span class="sxs-lookup"><span data-stu-id="33cdb-198">The query designer toolbar provides buttons to help you design MDX queries using the graphical interface.</span></span>  
  
 <span data-ttu-id="33cdb-199">工具栏按钮在设计模式和查询模式下是相同的，但是下列按钮在查询模式下不可用：</span><span class="sxs-lookup"><span data-stu-id="33cdb-199">The toolbar buttons are identical between Design mode and Query mode, but the following buttons are not enabled for Query mode:</span></span>  
  
-   <span data-ttu-id="33cdb-200">**编辑为文本**</span><span class="sxs-lookup"><span data-stu-id="33cdb-200">**Edit As Text**</span></span>  
  
-   <span data-ttu-id="33cdb-201">**添加计算成员**（![添加计算成员](media/rsqdicon-addcalculatedmember.gif "添加计算成员")）</span><span class="sxs-lookup"><span data-stu-id="33cdb-201">**Add Calculated Member** (![Add calculated member](media/rsqdicon-addcalculatedmember.gif "Add calculated member"))</span></span>  
  
-   <span data-ttu-id="33cdb-202">**显示空单元格**（![切换为显示空单元格](media/rsqdicon-showemptycells.gif "切换为显示空单元格")）</span><span class="sxs-lookup"><span data-stu-id="33cdb-202">**Show Empty Cells** (![Toggle for show empty cells](media/rsqdicon-showemptycells.gif "Toggle for show empty cells"))</span></span>  
  
-   <span data-ttu-id="33cdb-203">**自动执行**（![自动执行查询](media/rsqdicon-autoexecute.gif "自动执行查询")）</span><span class="sxs-lookup"><span data-stu-id="33cdb-203">**AutoExecute** (![AutoExecute the query](media/rsqdicon-autoexecute.gif "AutoExecute the query"))</span></span>  
  
-   <span data-ttu-id="33cdb-204">**显示聚合**![“显示聚合”按钮](media/rsqdicon-showaggregations.gif "“显示聚合”按钮")</span><span class="sxs-lookup"><span data-stu-id="33cdb-204">**Show Aggregations** (![Show Aggregations button](media/rsqdicon-showaggregations.gif "Show Aggregations button"))</span></span>  
  
  
