---
title: 数据定义查询 (数据挖掘) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 49e02de1-4ffa-401c-8eee-471a9c25b86a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 153369979737dded52609843cd30cf914315e9cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580468"
---
# <a name="data-definition-queries-data-mining"></a><span data-ttu-id="97890-102">数据定义查询（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="97890-102">Data Definition Queries (Data Mining)</span></span>
  <span data-ttu-id="97890-103">对于数据挖掘，“数据定义查询” \*\* 类别是指执行以下操作的 DMX 语句或 XMLA 命令：</span><span class="sxs-lookup"><span data-stu-id="97890-103">For data mining, the category *data definition query* means DMX statements or XMLA commands that do the following:</span></span>  
  
-   <span data-ttu-id="97890-104">创建、更改或操作数据挖掘对象（如模型）。</span><span class="sxs-lookup"><span data-stu-id="97890-104">Create, alter, or manipulate data mining objects, such as a model.</span></span>  
  
-   <span data-ttu-id="97890-105">定义要用于定型或预测的数据的源。</span><span class="sxs-lookup"><span data-stu-id="97890-105">Define the source of data to be used in training or for prediction.</span></span>  
  
-   <span data-ttu-id="97890-106">导出或导入挖掘模型和挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="97890-106">Export or import mining models and mining structures.</span></span>  
  
 [<span data-ttu-id="97890-107">创建数据定义查询</span><span class="sxs-lookup"><span data-stu-id="97890-107">Creating Data Definition Queries</span></span>](#bkmk_Create)  
  
-   [<span data-ttu-id="97890-108">SQL Server Data Tools 中的数据定义查询</span><span class="sxs-lookup"><span data-stu-id="97890-108">Data Definition Queries in SQL Server Data Tools</span></span>](#bkmk_ssdt)  
  
-   [<span data-ttu-id="97890-109">SQL Server Management Studio 中的数据定义查询</span><span class="sxs-lookup"><span data-stu-id="97890-109">Data Definition Queries in SQL Server Management Studio</span></span>](#bkmk_SSMS)  
  
 [<span data-ttu-id="97890-110">脚本数据定义语句</span><span class="sxs-lookup"><span data-stu-id="97890-110">Scripting Data Definition Statements</span></span>](#bkmk_Scripts)  
  
 [<span data-ttu-id="97890-111">脚本数据定义语句</span><span class="sxs-lookup"><span data-stu-id="97890-111">Scripting Data Definition Statements</span></span>](#bkmk_Export)  
  
##  <a name="creating-data-definition-queries"></a><a name="bkmk_Create"></a><span data-ttu-id="97890-112">创建数据定义查询</span><span class="sxs-lookup"><span data-stu-id="97890-112">Creating Data Definition Queries</span></span>  
 <span data-ttu-id="97890-113">可以使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 和 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的预测查询生成器或使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的 DMX 查询窗口来创建数据定义查询（语句）。</span><span class="sxs-lookup"><span data-stu-id="97890-113">You can create data definition queries (statements) by using the Prediction Query Builder in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], or by using the DMX Query window in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="97890-114">DMX 中的数据定义语句属于 Analysis Services 数据定义语言 (DDL)。</span><span class="sxs-lookup"><span data-stu-id="97890-114">Data definition statements in DMX are part of the Analysis Services data definition language (DDL).</span></span>  
  
 <span data-ttu-id="97890-115">有关特定数据定义语句的语法的信息，请参阅[数据挖掘扩展插件 (DMX) 引用](/sql/dmx/data-mining-extensions-dmx-reference)。</span><span class="sxs-lookup"><span data-stu-id="97890-115">For information about the syntax of specific data definition statements, see [Data Mining Extensions &#40;DMX&#41; Reference](/sql/dmx/data-mining-extensions-dmx-reference).</span></span>  
  
###  <a name="data-definition-queries-in-sql-server-data-tools"></a><a name="bkmk_ssdt"></a><span data-ttu-id="97890-116">SQL Server Data Tools 中的数据定义查询</span><span class="sxs-lookup"><span data-stu-id="97890-116">Data Definition Queries in SQL Server Data Tools</span></span>  
 <span data-ttu-id="97890-117">数据挖掘向导是 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中用来执行以下操作的首选工具：创建和修改挖掘模型和挖掘结构，以及定义用于预测查询和定型的数据源。</span><span class="sxs-lookup"><span data-stu-id="97890-117">The Data Mining Wizard is the preferred tool in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] for creating and modifying mining models and mining structures, and for defining the data sources that are used in prediction queries and for training.</span></span>  
  
 <span data-ttu-id="97890-118">但是，如果您想知道该向导向服务器发送了哪些语句来创建数据结构或挖掘模型，则可使用 SQL Server Profiler 来捕获数据定义语句。</span><span class="sxs-lookup"><span data-stu-id="97890-118">However, if you want to know what statements are being sent to the server by the wizard to create data structures or mining models, you can use SQL Server Profiler to capture the data definition statements.</span></span> <span data-ttu-id="97890-119">有关详细信息，请参阅 [Use SQL Server Profiler to Monitor Analysis Services](../instances/use-sql-server-profiler-to-monitor-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="97890-119">For more information, see [Use SQL Server Profiler to Monitor Analysis Services](../instances/use-sql-server-profiler-to-monitor-analysis-services.md).</span></span>  
  
 <span data-ttu-id="97890-120">若要查看在定义用于定型或预测的数据源时使用的语句，可以使用预测查询生成器中的 **“SQL 视图”** 。</span><span class="sxs-lookup"><span data-stu-id="97890-120">To view the statements used for defining data sources used for training or prediction, you can use the **SQL View** in the Prediction Query Builder.</span></span> <span data-ttu-id="97890-121">有时，使用预测查询生成器来生成用于定型和测试模型的基本查询对于建立正确的语法会很有用。</span><span class="sxs-lookup"><span data-stu-id="97890-121">Sometimes it can be helpful to build basic queries for training and testing models by using Prediction Query Builder, to establish the correct syntax.</span></span> <span data-ttu-id="97890-122">您可以切换到 **“SQL 视图”** 并手动编辑查询。</span><span class="sxs-lookup"><span data-stu-id="97890-122">You can then switch to **SQL View** and manually edit the query.</span></span> <span data-ttu-id="97890-123">有关详细信息，请参阅 [Manually Edit a Prediction Query](manually-edit-a-prediction-query.md)。</span><span class="sxs-lookup"><span data-stu-id="97890-123">For more information, see [Manually Edit a Prediction Query](manually-edit-a-prediction-query.md).</span></span>  
  
###  <a name="data-definition-queries-in-sql-server-management-studio"></a><a name="bkmk_SSMS"></a><span data-ttu-id="97890-124">SQL Server Management Studio 中的数据定义查询</span><span class="sxs-lookup"><span data-stu-id="97890-124">Data Definition Queries in SQL Server Management Studio</span></span>  
 <span data-ttu-id="97890-125">对于数据挖掘对象，可以使用数据定义查询来执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="97890-125">For data mining objects, you can use data definition queries to perform the following actions:</span></span>  
  
-   <span data-ttu-id="97890-126">使用 [CREATE MINING MODEL (DMX)](/sql/dmx/create-mining-model-dmx) 创建特定类型的模型，如聚类分析模型或决策树模型。</span><span class="sxs-lookup"><span data-stu-id="97890-126">Create specific types of models, such as a clustering model or decision tree model, by using [CREATE MINING MODEL &#40;DMX&#41;](/sql/dmx/create-mining-model-dmx).</span></span>  
  
-   <span data-ttu-id="97890-127">通过添加模型或使用 [ALTER MINING STRUCTURE (DMX)](/sql/dmx/alter-mining-structure-dmx) 更改列来更改现有挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="97890-127">Alter an existing mining structure by adding a model or by changing the columns, by using [ALTER MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/alter-mining-structure-dmx).</span></span> <span data-ttu-id="97890-128">请注意，无法使用 DMX 更改挖掘模型；只能向现有结构中添加新模型。</span><span class="sxs-lookup"><span data-stu-id="97890-128">Note that you cannot alter a mining model by using DMX; you only add new models to an existing structure.</span></span>  
  
-   <span data-ttu-id="97890-129">创建挖掘模型的副本，然后使用 [SELECT INTO (DMX)](/sql/dmx/select-into-dmx) 更改该副本。</span><span class="sxs-lookup"><span data-stu-id="97890-129">Make a copy of a mining model and then alter it, by using [SELECT INTO &#40;DMX&#41;](/sql/dmx/select-into-dmx).</span></span>  
  
-   <span data-ttu-id="97890-130">通过将 [INSERT INTO (DMX)](/sql/dmx/insert-into-dmx) 与数据源查询（如 OPENROWSET）结合使用来定义用于定型的数据集。</span><span class="sxs-lookup"><span data-stu-id="97890-130">Define the data set used for training a model, by using [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx) together with a data source query such as OPENROWSET.</span></span>  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="97890-131">提供了可帮助您创建数据定义查询的查询模板。</span><span class="sxs-lookup"><span data-stu-id="97890-131">provides query templates that can help you create data definition queries.</span></span> <span data-ttu-id="97890-132">有关详细信息，请参阅 [Use Analysis Services Templates in SQL Server Management Studio](../instances/use-analysis-services-templates-in-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="97890-132">For more information, see [Use Analysis Services Templates in SQL Server Management Studio](../instances/use-analysis-services-templates-in-sql-server-management-studio.md).</span></span>  
  
 <span data-ttu-id="97890-133">通常， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中为 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 提供的模板只包含常规语法定义，您必须使用 **“查询”** 窗口或用于输入参数的对话框来自定义该模板。</span><span class="sxs-lookup"><span data-stu-id="97890-133">In general, the templates that are provided for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] contain only the general syntax definition, which you must customize, either by typing in the **Query** window, or by using the dialog box provided for entering parameters.</span></span>  
  
 <span data-ttu-id="97890-134">有关如何使用接口输入参数的示例，请参阅 [通过模板创建单独预测查询](create-a-singleton-prediction-query-from-a-template.md)。</span><span class="sxs-lookup"><span data-stu-id="97890-134">For an example of how to enter parameters using the interface, see [Create a Singleton Prediction Query from a Template](create-a-singleton-prediction-query-from-a-template.md).</span></span>  
  
###  <a name="scripting-data-definition-statements"></a><a name="bkmk_Scripts"></a><span data-ttu-id="97890-135">脚本数据定义语句</span><span class="sxs-lookup"><span data-stu-id="97890-135">Scripting Data Definition Statements</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="97890-136">提供了多种脚本语言和编程语言，可以用来创建或更改数据挖掘对象，也可以用来定义数据源。</span><span class="sxs-lookup"><span data-stu-id="97890-136">provides multiple scripting and programming languages that you can use to create or alter data mining objects, or to define data sources.</span></span>  <span data-ttu-id="97890-137">虽然 DMX 旨在加快执行数据挖掘任务，但您也可以同时使用 XMLA 和 AMO 来操作脚本或自定义代码中的对象。</span><span class="sxs-lookup"><span data-stu-id="97890-137">Although DMX is designed for expediting data mining tasks, you can also use both XMLA and AMO to manipulate objects in scripts or in custom code.</span></span>  
  
 <span data-ttu-id="97890-138">用于 Excel 的数据挖掘外接程序还包含了多个查询模板，并提供了“高级查询编辑器”\*\*\*\*，有助于编写复杂的 DMX 语句。</span><span class="sxs-lookup"><span data-stu-id="97890-138">The Data Mining Add-in for Excel also includes many query templates, and provides the **Advanced Query Editor**, which helps you compose complex DMX statements.</span></span> <span data-ttu-id="97890-139">可以通过交互方式生成查询，然后切换到 SQL 视图以捕获 DMX 语句。</span><span class="sxs-lookup"><span data-stu-id="97890-139">You can build a query interactively and then switch to SQL View to capture the DMX statement.</span></span>  
  
##  <a name="exporting-and-importing-models"></a><a name="bkmk_Export"></a><span data-ttu-id="97890-140">导出和导入模型</span><span class="sxs-lookup"><span data-stu-id="97890-140">Exporting and Importing Models</span></span>  
 <span data-ttu-id="97890-141">可以使用 DMX 中的数据定义语句来导出模型的定义及其所需的结构和数据源，然后再将该定义导入其他服务器。</span><span class="sxs-lookup"><span data-stu-id="97890-141">You can use data definition statements in DMX to export the definition of a model and its required structure and data sources, and then import that definition into a different server.</span></span> <span data-ttu-id="97890-142">使用导出和导入是在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]实例之间移动数据挖掘模型和挖掘结构的最快且最便捷的方法。</span><span class="sxs-lookup"><span data-stu-id="97890-142">Using export and import is the fastest and easiest way to move data mining models and mining structures between instances of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="97890-143">有关详细信息，请参阅 [管理数据挖掘解决方案和对象](management-of-data-mining-solutions-and-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="97890-143">For more information, see [Management of Data Mining Solutions and Objects](management-of-data-mining-solutions-and-objects.md).</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="97890-144">如果模型基于多维数据集数据源中的数据，则您无法使用 DMX 导出模型，而应改用备份和还原功能。</span><span class="sxs-lookup"><span data-stu-id="97890-144">If your model is based on data from a cube data srouce, you cannot use DMX to export the model, and should use backup and restore instead.</span></span>  
  
##  <a name="related-tasks"></a><a name="bkmk_Tasks"></a> <span data-ttu-id="97890-145">相关任务</span><span class="sxs-lookup"><span data-stu-id="97890-145">Related Tasks</span></span>  
 <span data-ttu-id="97890-146">下表提供了一些链接，这些链接指向与数据定义查询相关的任务。</span><span class="sxs-lookup"><span data-stu-id="97890-146">The following table provides links to tasks that are related to data definition queries.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="97890-147">使用 DMX 查询模板。</span><span class="sxs-lookup"><span data-stu-id="97890-147">Work with templates for DMX queries.</span></span>|[<span data-ttu-id="97890-148">Use Analysis Services Templates in SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="97890-148">Use Analysis Services Templates in SQL Server Management Studio</span></span>](../instances/use-analysis-services-templates-in-sql-server-management-studio.md)|  
|<span data-ttu-id="97890-149">使用预测查询生成器来设计所有类型的查询。</span><span class="sxs-lookup"><span data-stu-id="97890-149">Design queries of all kinds, using Prediction Query Builder.</span></span>|[<span data-ttu-id="97890-150">使用预测查询生成器创建预测查询</span><span class="sxs-lookup"><span data-stu-id="97890-150">Create a Prediction Query Using the Prediction Query Builder</span></span>](create-a-prediction-query-using-the-prediction-query-builder.md)|  
|<span data-ttu-id="97890-151">使用 SQL Server Profiler 捕获查询定义，并使用跟踪来监视 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="97890-151">Capture query definitions by using SQL Server Profiler, and use traces to monitor [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>|[<span data-ttu-id="97890-152">Use SQL Server Profiler to Monitor Analysis Services</span><span class="sxs-lookup"><span data-stu-id="97890-152">Use SQL Server Profiler to Monitor Analysis Services</span></span>](../instances/use-sql-server-profiler-to-monitor-analysis-services.md)|  
|<span data-ttu-id="97890-153">了解有关为 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]提供的脚本语言和编程语言的详细信息。</span><span class="sxs-lookup"><span data-stu-id="97890-153">Learn more about the scripting languages and programming languages provided for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>|[<span data-ttu-id="97890-154">XML for Analysis (XMLA) 参考</span><span class="sxs-lookup"><span data-stu-id="97890-154">XML for Analysis  &#40;XMLA&#41; Reference</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-xmla-reference)<br /><br /> [<span data-ttu-id="97890-155">使用分析管理对象 (AMO) 进行开发</span><span class="sxs-lookup"><span data-stu-id="97890-155">Developing with Analysis Management Objects &#40;AMO&#41;</span></span>](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo)|  
|<span data-ttu-id="97890-156">了解如何管理 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 和 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中的模型。</span><span class="sxs-lookup"><span data-stu-id="97890-156">Learn how to manage models in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>|[<span data-ttu-id="97890-157">导出和导入数据挖掘对象</span><span class="sxs-lookup"><span data-stu-id="97890-157">Export and Import Data Mining Objects</span></span>](export-and-import-data-mining-objects.md)<br /><br /> [<span data-ttu-id="97890-158">EXPORT (DMX)</span><span class="sxs-lookup"><span data-stu-id="97890-158">EXPORT &#40;DMX&#41;</span></span>](/sql/dmx/export-dmx)<br /><br /> [<span data-ttu-id="97890-159">IMPORT (DMX)</span><span class="sxs-lookup"><span data-stu-id="97890-159">IMPORT &#40;DMX&#41;</span></span>](/sql/dmx/import-dmx)|  
|<span data-ttu-id="97890-160">了解有关 OPENROWSET 和用于查询外部数据的其他方法的详细信息。</span><span class="sxs-lookup"><span data-stu-id="97890-160">Learn more about OPENROWSET and other ways to query external data.</span></span>|<span data-ttu-id="97890-161">[<源数据查询>](/sql/dmx/source-data-query)。</span><span class="sxs-lookup"><span data-stu-id="97890-161">[&#60;source data query&#62;](/sql/dmx/source-data-query).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="97890-162">另请参阅</span><span class="sxs-lookup"><span data-stu-id="97890-162">See Also</span></span>  
 [<span data-ttu-id="97890-163">数据挖掘向导（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="97890-163">Data Mining Wizard &#40;Analysis Services - Data Mining&#41;</span></span>](data-mining-wizard-analysis-services-data-mining.md)  
  
  
