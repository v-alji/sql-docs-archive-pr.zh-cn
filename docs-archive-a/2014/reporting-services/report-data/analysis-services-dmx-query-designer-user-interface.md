---
title: Analysis Services DMX 查询设计器用户界面 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10012"
- sql12.rtp.rptdesigner.dataview.asquerydesigner.f1
helpviewer_keywords:
- Analysis Services [DMX]
- DMX [Analysis Services], user interface
- query designers [DMX]
ms.assetid: 5fd726a4-aed7-4e6c-9404-ccb2db66cf26
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b641423ad9563f252ba89f51fcd8cafb0ed7bbe8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578664"
---
# <a name="analysis-services-dmx-query-designer-user-interface"></a><span data-ttu-id="f4ac9-102">Analysis Services DMX 查询设计器用户界面</span><span class="sxs-lookup"><span data-stu-id="f4ac9-102">Analysis Services DMX Query Designer User Interface</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="f4ac9-103">提供了图形查询设计器，可用于为 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 数据源生成数据挖掘表达式 (DMX) 查询和多维表达式 (MDX) 查询。</span><span class="sxs-lookup"><span data-stu-id="f4ac9-103">provides graphical query designers for building Data Mining Expressions (DMX) queries and Multidimensional Expression (MDX) queries for an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] data source.</span></span> <span data-ttu-id="f4ac9-104">该主题介绍了 DMX 查询设计器。</span><span class="sxs-lookup"><span data-stu-id="f4ac9-104">This topic describes the DMX query designer.</span></span> <span data-ttu-id="f4ac9-105">有关 MDX 查询设计器的详细信息，请参阅 [Analysis Services MDX Query Designer User Interface](analysis-services-mdx-query-designer-user-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="f4ac9-105">For more information about the MDX query designer, see [Analysis Services MDX Query Designer User Interface](analysis-services-mdx-query-designer-user-interface.md).</span></span>  
  
 <span data-ttu-id="f4ac9-106">DMX 图形查询设计器有三种模式：设计、查询和结果。</span><span class="sxs-lookup"><span data-stu-id="f4ac9-106">The DMX graphical query designer has three modes: Design, Query, and Result.</span></span> <span data-ttu-id="f4ac9-107">若要切换模式，用右键单击“查询设计”窗格，并选择模式。</span><span class="sxs-lookup"><span data-stu-id="f4ac9-107">To switch modes, right-click on the Query Design pane, and select the mode.</span></span> <span data-ttu-id="f4ac9-108">每种模式都提供一个“元数据”窗格，从该窗格中可以拖动选定的多维数据集的成员，以创建可在处理报表时为数据集检索数据的 DMX 查询。</span><span class="sxs-lookup"><span data-stu-id="f4ac9-108">Each mode provides a Metadata pane from which you can drag members from the selected cubes to build a DMX query that retrieves data for a dataset when the report is processed.</span></span>  
  
## <a name="graphical-dmx-query-designer-toolbar"></a><span data-ttu-id="f4ac9-109">图形 DMX 查询设计器工具栏</span><span class="sxs-lookup"><span data-stu-id="f4ac9-109">Graphical DMX Query Designer Toolbar</span></span>  
 <span data-ttu-id="f4ac9-110">查询设计器工具栏提供了可以帮助您使用图形界面来设计 DMX 查询的按钮。</span><span class="sxs-lookup"><span data-stu-id="f4ac9-110">The query designer toolbar provides buttons to help you design DMX queries using the graphical interface.</span></span> <span data-ttu-id="f4ac9-111">下表介绍了这些按钮及其功能。</span><span class="sxs-lookup"><span data-stu-id="f4ac9-111">The following table describes the buttons and their functions.</span></span>  
  
|<span data-ttu-id="f4ac9-112">按钮</span><span class="sxs-lookup"><span data-stu-id="f4ac9-112">Button</span></span>|<span data-ttu-id="f4ac9-113">说明</span><span class="sxs-lookup"><span data-stu-id="f4ac9-113">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="f4ac9-114">**编辑为文本**</span><span class="sxs-lookup"><span data-stu-id="f4ac9-114">**Edit As Text**</span></span>|<span data-ttu-id="f4ac9-115">对此数据源类型禁用。</span><span class="sxs-lookup"><span data-stu-id="f4ac9-115">Disabled for this data source type.</span></span>|  
|<span data-ttu-id="f4ac9-116">**导入**</span><span class="sxs-lookup"><span data-stu-id="f4ac9-116">**Import**</span></span>|<span data-ttu-id="f4ac9-117">从文件系统中的报表定义 (.rdl) 文件导入现有查询。</span><span class="sxs-lookup"><span data-stu-id="f4ac9-117">Import an existing query from a report definition (.rdl) file on the file system.</span></span> <span data-ttu-id="f4ac9-118">有关详细信息，请参阅 [报表的嵌入数据集和共享数据集（报表生成器和 SSRS）](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="f4ac9-118">For more information, see [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).</span></span>|  
|<span data-ttu-id="f4ac9-119">![更改为 MDX 查询视图](../media/rsqdicon-commandtypemdx.gif "更改为 MDX 查询视图")</span><span class="sxs-lookup"><span data-stu-id="f4ac9-119">![Change to MDX query view](../media/rsqdicon-commandtypemdx.gif "Change to MDX query view")</span></span>|<span data-ttu-id="f4ac9-120">切换到 MDX 查询设计器模式。</span><span class="sxs-lookup"><span data-stu-id="f4ac9-120">Switch to the MDX query designer mode.</span></span>|  
|<span data-ttu-id="f4ac9-121">![更改为 DMX 查询语言视图](../media/rsqdicon-commandtypedmx.gif "更改为 DMX 查询语言视图")</span><span class="sxs-lookup"><span data-stu-id="f4ac9-121">![Change to DMX query language view](../media/rsqdicon-commandtypedmx.gif "Change to DMX query language view")</span></span>|<span data-ttu-id="f4ac9-122">切换到 DMX 查询设计器模式。</span><span class="sxs-lookup"><span data-stu-id="f4ac9-122">Switch to the DMX query designer mode.</span></span>|  
|<span data-ttu-id="f4ac9-123">![刷新结果数据](../media/rsqdicon-refresh.gif "刷新结果数据")</span><span class="sxs-lookup"><span data-stu-id="f4ac9-123">![Refresh result data](../media/rsqdicon-refresh.gif "Refresh result data")</span></span>|<span data-ttu-id="f4ac9-124">刷新数据源的元数据。</span><span class="sxs-lookup"><span data-stu-id="f4ac9-124">Refresh metadata from the data source.</span></span>|  
|<span data-ttu-id="f4ac9-125">![删除](../media/rsqdicon-delete.gif "删除")</span><span class="sxs-lookup"><span data-stu-id="f4ac9-125">![Delete](../media/rsqdicon-delete.gif "Delete")</span></span>|<span data-ttu-id="f4ac9-126">通过查询在“数据”窗格中删除选定列。</span><span class="sxs-lookup"><span data-stu-id="f4ac9-126">Delete the selected column in the Data pane from the query.</span></span>|  
|<span data-ttu-id="f4ac9-127">![“查询参数”对话框图标](../media/iconqueryparameter.gif "“查询参数”对话框图标")</span><span class="sxs-lookup"><span data-stu-id="f4ac9-127">![Icon for the Query Parameters dialog box](../media/iconqueryparameter.gif "Icon for the Query Parameters dialog box")</span></span>|<span data-ttu-id="f4ac9-128">显示 **“查询参数”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="f4ac9-128">Display the **Query Parameters** dialog box.</span></span> <span data-ttu-id="f4ac9-129">如果向变量分配了默认值，则当在报表设计器中切换到“布局”视图时，将创建相应的报表参数。</span><span class="sxs-lookup"><span data-stu-id="f4ac9-129">When you assign a default value to a variable, a corresponding report parameter is created when you switch to the Layout view in Report Designer.</span></span>|  
|<span data-ttu-id="f4ac9-130">![运行查询](../media/rsqdicon-run.gif "运行查询")</span><span class="sxs-lookup"><span data-stu-id="f4ac9-130">![Run the query](../media/rsqdicon-run.gif "Run the query")</span></span>|<span data-ttu-id="f4ac9-131">准备查询。</span><span class="sxs-lookup"><span data-stu-id="f4ac9-131">Prepare the query.</span></span>|  
|<span data-ttu-id="f4ac9-132">![切换到设计模式](../media/rsqdicon-designmode.gif "切换到设计模式")</span><span class="sxs-lookup"><span data-stu-id="f4ac9-132">![Switch to Design mode](../media/rsqdicon-designmode.gif "Switch to Design mode")</span></span>|<span data-ttu-id="f4ac9-133">在设计模式和查询模式之间切换。</span><span class="sxs-lookup"><span data-stu-id="f4ac9-133">Toggle between Design mode and Query mode.</span></span> <span data-ttu-id="f4ac9-134">若要更改为结果视图，请右键单击“设计”窗格并选择“结果”  。</span><span class="sxs-lookup"><span data-stu-id="f4ac9-134">To change to result view, right-click on the Design pane and choose **Result**.</span></span>|  
  
## <a name="graphical-dmx-query-designer-in-design-mode"></a><span data-ttu-id="f4ac9-135">设计模式下的图形 DMX 查询设计器</span><span class="sxs-lookup"><span data-stu-id="f4ac9-135">Graphical DMX Query Designer in Design Mode</span></span>  
 <span data-ttu-id="f4ac9-136">编辑使用 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 数据源的数据集（该数据集没有有效的多维数据集，但是具有有效的挖掘模型）时，将在设计模式下打开图形查询设计器。</span><span class="sxs-lookup"><span data-stu-id="f4ac9-136">When you edit a dataset that uses an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] data source that has no valid cubes but that does have valid mining models, the graphical query designer opens in Design mode.</span></span> <span data-ttu-id="f4ac9-137">下图列出了设计模式的窗格。</span><span class="sxs-lookup"><span data-stu-id="f4ac9-137">The following figure labels the panes for Design mode.</span></span>  
  
 <span data-ttu-id="f4ac9-138">![Analysis Services DMX 查询设计器的设计视图](../media/rsqd-dsawas-dmx-designmode.gif "Analysis Services DMX 查询设计器的设计视图")</span><span class="sxs-lookup"><span data-stu-id="f4ac9-138">![Analysis Services DMX query designer, design view](../media/rsqd-dsawas-dmx-designmode.gif "Analysis Services DMX query designer, design view")</span></span>  
  
 <span data-ttu-id="f4ac9-139">下表介绍了每个窗格的功能。</span><span class="sxs-lookup"><span data-stu-id="f4ac9-139">The following table describes the function of each pane.</span></span>  
  
|<span data-ttu-id="f4ac9-140">窗格</span><span class="sxs-lookup"><span data-stu-id="f4ac9-140">Pane</span></span>|<span data-ttu-id="f4ac9-141">函数</span><span class="sxs-lookup"><span data-stu-id="f4ac9-141">Function</span></span>|  
|----------|--------------|  
|<span data-ttu-id="f4ac9-142">“查询设计器”窗格</span><span class="sxs-lookup"><span data-stu-id="f4ac9-142">Query Design pane</span></span>|<span data-ttu-id="f4ac9-143">使用 **“挖掘模型”** 和 **“选择输入表”** 对话框创建 DMX 查询。</span><span class="sxs-lookup"><span data-stu-id="f4ac9-143">Use the **Mining Model** and **Select Input Table** dialog boxes to build the DMX query.</span></span>|  
|<span data-ttu-id="f4ac9-144">“网格”窗格</span><span class="sxs-lookup"><span data-stu-id="f4ac9-144">Grid pane</span></span>|<span data-ttu-id="f4ac9-145">使用“源”下拉列表为网格中的每行选择一个函数或表达式，并选择要用于 DMX 查询的字段、组以及条件或参数  。</span><span class="sxs-lookup"><span data-stu-id="f4ac9-145">For each row in the grid, use the **Source** drop-down list to select a function or expression, and choose fields, groups, and criteria or arguments to use in your DMX query.</span></span> <span data-ttu-id="f4ac9-146">若要查看根据您的选择生成的 DMX 查询文本，请单击工具栏中的 **“设计模式”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="f4ac9-146">To see the DMX query text generated by your selections, click the **Design Mode** button on the toolbar.</span></span>|  
  
 <span data-ttu-id="f4ac9-147">若要运行 DMX 查询并在“结果”窗格中显示结果，请右键单击“查询设计”窗格并选择“结果”  。</span><span class="sxs-lookup"><span data-stu-id="f4ac9-147">To run the DMX query and show results in the Result pane, right-click on the Query Design pane and select **Result**.</span></span>  
  
## <a name="graphical-dmx-query-designer-in-query-mode"></a><span data-ttu-id="f4ac9-148">查询模式下的图形 DMX 查询设计器</span><span class="sxs-lookup"><span data-stu-id="f4ac9-148">Graphical DMX Query Designer in Query Mode</span></span>  
 <span data-ttu-id="f4ac9-149">若要将图形查询设计器更改为查询模式，请单击工具栏上的“设计模式”按钮，或右键单击查询设计界面，并从快捷菜单中选择“查询”   。</span><span class="sxs-lookup"><span data-stu-id="f4ac9-149">To change the graphical query designer to Query mode, click the **Design Mode** button on the toolbar or right-click on the query design surface, and choose **Query** from the shortcut menu.</span></span> <span data-ttu-id="f4ac9-150">使用该模式直接在“查询”窗格中输入 DMX 文本。</span><span class="sxs-lookup"><span data-stu-id="f4ac9-150">Use this mode to enter DMX text directly into the Query pane.</span></span>  
  
 <span data-ttu-id="f4ac9-151">下图列出了查询模式的窗格。</span><span class="sxs-lookup"><span data-stu-id="f4ac9-151">The following figure labels the panes for Query mode.</span></span>  
  
 <span data-ttu-id="f4ac9-152">![Analysis Services DMX 查询设计器的查询视图](../media/rsqd-dsawas-dmx-querymode.gif "Analysis Services DMX 查询设计器的查询视图")</span><span class="sxs-lookup"><span data-stu-id="f4ac9-152">![Analysis Services DMX query designer, query view](../media/rsqd-dsawas-dmx-querymode.gif "Analysis Services DMX query designer, query view")</span></span>  
  
 <span data-ttu-id="f4ac9-153">下表介绍了每个窗格的功能。</span><span class="sxs-lookup"><span data-stu-id="f4ac9-153">The following table describes the function of each pane.</span></span>  
  
|<span data-ttu-id="f4ac9-154">窗格</span><span class="sxs-lookup"><span data-stu-id="f4ac9-154">Pane</span></span>|<span data-ttu-id="f4ac9-155">函数</span><span class="sxs-lookup"><span data-stu-id="f4ac9-155">Function</span></span>|  
|----------|--------------|  
|<span data-ttu-id="f4ac9-156">“查询设计器”窗格</span><span class="sxs-lookup"><span data-stu-id="f4ac9-156">Query Design pane</span></span>|<span data-ttu-id="f4ac9-157">使用 **“挖掘模型”** 和 **“选择输入表”** 对话框创建 DMX 查询。</span><span class="sxs-lookup"><span data-stu-id="f4ac9-157">Use the **Mining Model** and **Select Input Table** dialog boxes to build the DMX query.</span></span>|  
|<span data-ttu-id="f4ac9-158">“查询”窗格</span><span class="sxs-lookup"><span data-stu-id="f4ac9-158">Query pane</span></span>|<span data-ttu-id="f4ac9-159">直接在窗格中查看或编辑 DMX 查询文本。</span><span class="sxs-lookup"><span data-stu-id="f4ac9-159">View or edit DMX query text directly in the pane.</span></span> <span data-ttu-id="f4ac9-160">如果重新回到 **“设计”** 模式，对 DMX 查询文本所做的更改将不再存在。</span><span class="sxs-lookup"><span data-stu-id="f4ac9-160">Changes to the DMX query text do not persist if you change back to **Design** mode.</span></span>|  
  
 <span data-ttu-id="f4ac9-161">若要运行 DMX 查询并在“结果”窗格中显示结果，请右键单击“查询设计”窗格并选择“结果”  。</span><span class="sxs-lookup"><span data-stu-id="f4ac9-161">To run the DMX query and show results in the Result pane, right-click on the Query Design pane and select **Result**.</span></span>  
  
## <a name="graphical-dmx-query-designer-in-result-mode"></a><span data-ttu-id="f4ac9-162">结果模式下的图形 DMX 查询设计器</span><span class="sxs-lookup"><span data-stu-id="f4ac9-162">Graphical DMX Query Designer in Result Mode</span></span>  
 <span data-ttu-id="f4ac9-163">若要显示结果模式，请右键单击查询设计图面并从快捷菜单中选择“结果”  。</span><span class="sxs-lookup"><span data-stu-id="f4ac9-163">To display the Result mode, right-click the query design surface and choose **Result** from the shortcut menu.</span></span> <span data-ttu-id="f4ac9-164">切换到结果模式时，将自动运行 DMX 查询。</span><span class="sxs-lookup"><span data-stu-id="f4ac9-164">When you switch to Result mode, the DMX query runs automatically.</span></span>  
  
 <span data-ttu-id="f4ac9-165">下图显示结果模式下的查询设计器。</span><span class="sxs-lookup"><span data-stu-id="f4ac9-165">The following figure shows the query designer in Result mode.</span></span>  
  
 <span data-ttu-id="f4ac9-166">![Analysis Services DMX 查询设计器的结果视图](../media/rsqd-dsawas-dmx-resultmode.gif "Analysis Services DMX 查询设计器的结果视图")</span><span class="sxs-lookup"><span data-stu-id="f4ac9-166">![Analysis Services DMX query designer, result view](../media/rsqd-dsawas-dmx-resultmode.gif "Analysis Services DMX query designer, result view")</span></span>  
  
 <span data-ttu-id="f4ac9-167">若要切换回设计模式或查询模式，请右键单击“结果”窗格并选择“设计”或“查询”。  </span><span class="sxs-lookup"><span data-stu-id="f4ac9-167">To switch back to Design mode or Query mode, right-click on the Result pane and select **Design** or **Query**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4ac9-168">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f4ac9-168">See Also</span></span>  
 <span data-ttu-id="f4ac9-169">[在 Analysis Services 的 MDX 查询设计器中定义参数（报表生成器和 SSRS）](define-parameters-in-the-mdx-query-designer-for-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="f4ac9-169">[Define Parameters in the MDX Query Designer for Analysis Services &#40;Report Builder and SSRS&#41;](define-parameters-in-the-mdx-query-designer-for-analysis-services.md) </span></span>  
 <span data-ttu-id="f4ac9-170">[创建共享数据集或嵌入数据集（报表生成器和 SSRS）](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f4ac9-170">[Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f4ac9-171">[针对 DMX 的 Analysis Services 连接类型 (SSRS)](analysis-services-connection-type-for-dmx-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f4ac9-171">[Analysis Services Connection Type for DMX &#40;SSRS&#41;](analysis-services-connection-type-for-dmx-ssrs.md) </span></span>  
 <span data-ttu-id="f4ac9-172">[从数据挖掘模型检索数据 (DMX) (SSRS)](retrieve-data-from-a-data-mining-model-dmx-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f4ac9-172">[Retrieve Data from a Data Mining Model &#40;DMX&#41; &#40;SSRS&#41;](retrieve-data-from-a-data-mining-model-dmx-ssrs.md) </span></span>  
 <span data-ttu-id="f4ac9-173">[RSReportDesigner 配置文件](../report-server/rsreportdesigner-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="f4ac9-173">[RSReportDesigner Configuration File](../report-server/rsreportdesigner-configuration-file.md) </span></span>  
 <span data-ttu-id="f4ac9-174">[针对 MDX 的 Analysis Services 连接类型 (SSRS)](analysis-services-connection-type-for-mdx-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f4ac9-174">[Analysis Services Connection Type for MDX &#40;SSRS&#41;](analysis-services-connection-type-for-mdx-ssrs.md) </span></span>  
 [<span data-ttu-id="f4ac9-175">针对 DMX 的 Analysis Services 连接类型 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="f4ac9-175">Analysis Services Connection Type for DMX &#40;SSRS&#41;</span></span>](analysis-services-connection-type-for-dmx-ssrs.md)  
  
  
