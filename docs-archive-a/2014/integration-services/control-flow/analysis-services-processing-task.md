---
title: Analysis Services 处理任务 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.asprocessingtask.f1
helpviewer_keywords:
- Analysis Services Processing task
- processing objects [Integration Services]
ms.assetid: e5748836-b4ce-4e17-ab6b-617a336f02f4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 19ef8046c06c9131b3ea2eb8ffe267c026808dfd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688119"
---
# <a name="analysis-services-processing-task"></a><span data-ttu-id="db006-102">Analysis Services 处理任务</span><span class="sxs-lookup"><span data-stu-id="db006-102">Analysis Services Processing Task</span></span>
  <span data-ttu-id="db006-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 处理任务可负责处理 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 对象，如表格模型、多维数据集、维度和挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="db006-103">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Processing task processes [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects such as tabular models, cubes, dimensions, and mining models.</span></span>  
  
 <span data-ttu-id="db006-104">处理表格模型时，请记住以下事项：</span><span class="sxs-lookup"><span data-stu-id="db006-104">When processing tabular models, keep the following in mind:</span></span>  
  
-   <span data-ttu-id="db006-105">不能对表格模型执行影响分析。</span><span class="sxs-lookup"><span data-stu-id="db006-105">You cannot perform impact analysis on tabular models.</span></span>  
  
-   <span data-ttu-id="db006-106">不公开表格模型的一些处理选项，如“处理碎片整理”和“处理重新计算”。</span><span class="sxs-lookup"><span data-stu-id="db006-106">Some processing options for tabular mode are not exposed, such as Process Defrag and Process Recalc.</span></span> <span data-ttu-id="db006-107">您可以使用执行 DDL 任务来执行这些功能。</span><span class="sxs-lookup"><span data-stu-id="db006-107">You can perform these functions by using the Execute DDL task.</span></span>  
  
-   <span data-ttu-id="db006-108">选项“处理索引”和“处理更新”不适用于表格模型，不应使用它们。</span><span class="sxs-lookup"><span data-stu-id="db006-108">The options Process Index and Process Update are not appropriate for tabular models and should not be used.</span></span>  
  
-   <span data-ttu-id="db006-109">对表格模型忽略批处理设置。</span><span class="sxs-lookup"><span data-stu-id="db006-109">Batch settings are ignored for tabular models.</span></span>  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="db006-110">提供了一些可执行商业智能操作的任务，如运行数据定义语言 (DDL) 语句和数据挖掘预测查询。</span><span class="sxs-lookup"><span data-stu-id="db006-110">includes a number of tasks that perform business intelligence operations, such as running Data Definition Language (DDL) statements and data mining prediction queries.</span></span> <span data-ttu-id="db006-111">有关相关商业智能任务的详细信息，请单击以下主题之一：</span><span class="sxs-lookup"><span data-stu-id="db006-111">For more information about related business intelligence tasks, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="db006-112">Analysis Services 执行 DDL 任务</span><span class="sxs-lookup"><span data-stu-id="db006-112">Analysis Services Execute DDL Task</span></span>](analysis-services-execute-ddl-task.md)  
  
-   [<span data-ttu-id="db006-113">数据挖掘查询任务</span><span class="sxs-lookup"><span data-stu-id="db006-113">Data Mining Query Task</span></span>](data-mining-query-task.md)  
  
## <a name="object-processing"></a><span data-ttu-id="db006-114">对象处理</span><span class="sxs-lookup"><span data-stu-id="db006-114">Object Processing</span></span>  
 <span data-ttu-id="db006-115">可以同时处理多个对象。</span><span class="sxs-lookup"><span data-stu-id="db006-115">Multiple objects can be processed at the same time.</span></span> <span data-ttu-id="db006-116">处理多个对象时，您需要定义处理批中所有对象时要应用的设置。</span><span class="sxs-lookup"><span data-stu-id="db006-116">When processing multiple objects, you define settings that apply to the processing of all the objects in the batch.</span></span>  
  
 <span data-ttu-id="db006-117">批中的对象可以按顺序处理或并行处理。</span><span class="sxs-lookup"><span data-stu-id="db006-117">Objects in a batch can be processed in sequence or in parallel.</span></span> <span data-ttu-id="db006-118">如果批中不包含必须按顺序处理的对象，则并行处理可加快处理的速度。</span><span class="sxs-lookup"><span data-stu-id="db006-118">If the batch does not contain objects for which processing sequence is important, parallel processing can speed up processing.</span></span> <span data-ttu-id="db006-119">如果并行处理批中的对象，则可配置任务使其确定并行处理的对象数，也可以手动指定同时处理的对象数。</span><span class="sxs-lookup"><span data-stu-id="db006-119">If objects in the batch are processed in parallel, you can configure the task to let it determine how many objects to process in parallel, or you can manually specify the number of objects to process at the same time.</span></span> <span data-ttu-id="db006-120">如果按顺序处理对象，则可通过将所有对象登记在一个事务中或对批中的每个对象使用单独的事务来设置批的事务属性。</span><span class="sxs-lookup"><span data-stu-id="db006-120">If objects are processed sequentially, you can set a transaction attribute on the batch either by enlisting all objects in one transaction or by using a separate transaction for each object in the batch.</span></span>  
  
 <span data-ttu-id="db006-121">在处理分析对象时，可能还要处理依赖于这些对象的对象。</span><span class="sxs-lookup"><span data-stu-id="db006-121">When you process analytic objects, you might also want to process the objects that depend on them.</span></span> <span data-ttu-id="db006-122">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 处理任务还包含一个选项，可以在处理选定对象的同时，处理任意的相关对象。</span><span class="sxs-lookup"><span data-stu-id="db006-122">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Processing task includes an option to process any dependent objects in addition to the selected objects.</span></span>  
  
 <span data-ttu-id="db006-123">通常，您应该在处理事实表之前处理维度表。</span><span class="sxs-lookup"><span data-stu-id="db006-123">Typically, you process dimension tables before processing fact tables.</span></span> <span data-ttu-id="db006-124">如果您试图在处理维度表之前处理事实表，则可能会遇到错误。</span><span class="sxs-lookup"><span data-stu-id="db006-124">You may encounter errors if you try to process fact tables before processing the dimension tables.</span></span>  
  
 <span data-ttu-id="db006-125">此任务还允许配置如何处理维度键中的错误。</span><span class="sxs-lookup"><span data-stu-id="db006-125">This task also lets you configure the handling of errors in dimension keys.</span></span> <span data-ttu-id="db006-126">例如，任务可忽略错误或在发生指定数量的错误后停止。</span><span class="sxs-lookup"><span data-stu-id="db006-126">For example, the task can ignore errors or stop after a specified number of errors occur.</span></span> <span data-ttu-id="db006-127">任务可使用默认错误配置，或者您可以构造自定义错误配置。</span><span class="sxs-lookup"><span data-stu-id="db006-127">The task can use the default error configuration, or you can construct a custom error configuration.</span></span> <span data-ttu-id="db006-128">在自定义错误配置中，可以指定任务处理错误的方式和错误条件。</span><span class="sxs-lookup"><span data-stu-id="db006-128">In the custom error configuration, you specify how the task handles errors and the error conditions.</span></span> <span data-ttu-id="db006-129">例如，可以指定发生第四个错误时停止运行任务，或指定任务处理 **Null** 键值的方式。</span><span class="sxs-lookup"><span data-stu-id="db006-129">For example, you can specify that the task should stop running when the fourth error occurs, or specify how the task should handle **Null** key values.</span></span> <span data-ttu-id="db006-130">自定义错误配置还可以包含错误日志的路径。</span><span class="sxs-lookup"><span data-stu-id="db006-130">The custom error configuration can also include the path of an error log.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="db006-131">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 处理任务只能处理使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 工具创建的分析对象。</span><span class="sxs-lookup"><span data-stu-id="db006-131">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Processing task can process only analytic objects created by using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tools.</span></span>  
  
 <span data-ttu-id="db006-132">此任务常与大容量插入任务或数据流任务结合使用，前者将数据加载到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表，后者实现将数据加载到表中的数据流。</span><span class="sxs-lookup"><span data-stu-id="db006-132">This task is frequently used in combination with a Bulk Insert task that loads data into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table, or a Data Flow task that implements a data flow that loads data into a table.</span></span> <span data-ttu-id="db006-133">例如，数据流任务可能具有数据流，该数据流从联机事务性数据库 (OLTP) 数据库中提取数据，并将数据加载到数据仓库中的事实数据表，然后调用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 处理任务来处理根据数据仓库构建的多维数据集。</span><span class="sxs-lookup"><span data-stu-id="db006-133">For example, the Data Flow task might have a data flow that extracts data from an online transactional database (OLTP) database and loads it into a fact table in a data warehouse, after which the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Processing task is called to process the cube built on the data warehouse.</span></span>  
  
 <span data-ttu-id="db006-134">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 处理任务使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 连接管理器连接到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的实例。</span><span class="sxs-lookup"><span data-stu-id="db006-134">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Processing task uses an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] connection manager to connect to an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="db006-135">有关详细信息，请参阅 [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="db006-135">For more information, see [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md).</span></span>  
  
## <a name="error-handling"></a><span data-ttu-id="db006-136">错误处理</span><span class="sxs-lookup"><span data-stu-id="db006-136">Error Handling</span></span>  
  
## <a name="configuration-of-the-analysis-services-processing-task"></a><span data-ttu-id="db006-137">配置 Analysis Services 处理任务</span><span class="sxs-lookup"><span data-stu-id="db006-137">Configuration of the Analysis Services Processing Task</span></span>  
 <span data-ttu-id="db006-138">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="db006-138">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="db006-139">有关可以在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置的属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="db006-139">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="db006-140">Analysis Services 处理任务编辑器（“常规”页）</span><span class="sxs-lookup"><span data-stu-id="db006-140">Analysis Services Processing Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="db006-141">Analysis Services 处理任务编辑器（Analysis Services 页）</span><span class="sxs-lookup"><span data-stu-id="db006-141">Analysis Services Processing Task Editor &#40;Analysis Services Page&#41;</span></span>](../analysis-services-processing-task-editor-analysis-services-page.md)  
  
-   [<span data-ttu-id="db006-142">“表达式”页</span><span class="sxs-lookup"><span data-stu-id="db006-142">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="db006-143">有关在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置这些属性的详细信息，请单击以下主题：</span><span class="sxs-lookup"><span data-stu-id="db006-143">For more information about setting these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="db006-144">设置任务或容器的属性</span><span class="sxs-lookup"><span data-stu-id="db006-144">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="programmatic-configuration-of-the-analysis-services-processing-task"></a><span data-ttu-id="db006-145">以编程方式配置 Analysis Services 处理任务</span><span class="sxs-lookup"><span data-stu-id="db006-145">Programmatic Configuration of the Analysis Services Processing Task</span></span>  
 <span data-ttu-id="db006-146">有关以编程方式设置这些属性的详细信息，请单击下列主题之一：</span><span class="sxs-lookup"><span data-stu-id="db006-146">For more information about programmatically setting these properties, click one of the following topics:</span></span>  
  
-   <xref:Microsoft.DataTransformationServices.Tasks.DTSProcessingTask.DTSProcessingTask>  
  
  
