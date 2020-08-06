---
title: 数据挖掘)  (处理要求和注意事项 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], objects
- mining structures [Analysis Services], processing
- mining models [Analysis Services], processing
ms.assetid: f7331261-6f1c-4986-b2c7-740f4b92ca44
author: minewiskan
ms.author: owend
ms.openlocfilehash: f4b3f00692e58a55063a7d6bf4887dbee36df68c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690875"
---
# <a name="processing-requirements-and-considerations-data-mining"></a><span data-ttu-id="017da-102">处理要求和注意事项（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="017da-102">Processing Requirements and Considerations (Data Mining)</span></span>
  <span data-ttu-id="017da-103">本主题介绍了一些处理数据挖掘对象时要记住的技术注意事项。</span><span class="sxs-lookup"><span data-stu-id="017da-103">This topic describes some technical considerations to keep in mind when processing data mining objects.</span></span> <span data-ttu-id="017da-104">有关处理的涵义以及如何将处理应用于数据挖掘的一般说明，请参阅 [处理数据挖掘对象](processing-data-mining-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="017da-104">For a general explanation of what processing is, and how it applies to data mining, see [Processing Data Mining Objects](processing-data-mining-objects.md).</span></span>  
  
 [<span data-ttu-id="017da-105">针对关系存储区的查询</span><span class="sxs-lookup"><span data-stu-id="017da-105">Queries on Relational Store</span></span>](#bkmk_QueryReqs)  
  
 [<span data-ttu-id="017da-106">处理挖掘结构</span><span class="sxs-lookup"><span data-stu-id="017da-106">Processing Mining Structures</span></span>](#bkmk_ProcessStructures)  
  
 [<span data-ttu-id="017da-107">处理挖掘模型</span><span class="sxs-lookup"><span data-stu-id="017da-107">Processing Mining Models</span></span>](#bkmk_ProcessModels)  
  
##  <a name="queries-on-the-relational-store-during-processing"></a><a name="bkmk_QueryReqs"></a> <span data-ttu-id="017da-108">处理期间针对关系存储区的查询</span><span class="sxs-lookup"><span data-stu-id="017da-108">Queries on the Relational Store during Processing</span></span>  
 <span data-ttu-id="017da-109">对于数据挖掘，有以下三个处理阶段：查询源数据、确定原始统计信息和使用模型定义与算法对挖掘模型进行定型。</span><span class="sxs-lookup"><span data-stu-id="017da-109">For data mining, there are three phases to processing: querying the source data, determining raw statistics, and using the model definition and algorithm to train the mining model.</span></span>  
  
 <span data-ttu-id="017da-110">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 服务器向提供原始数据的数据库发出查询。</span><span class="sxs-lookup"><span data-stu-id="017da-110">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] server issues queries to the database that provides the raw data.</span></span> <span data-ttu-id="017da-111">此数据库可能是 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 SQL Server 数据库引擎早期版本的实例。</span><span class="sxs-lookup"><span data-stu-id="017da-111">This database might be an instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] or an earlier version of the SQL Server database engine.</span></span> <span data-ttu-id="017da-112">处理数据挖掘结构时，源中的数据传输到挖掘结构，并在磁盘上保存为一种新的压缩格式。</span><span class="sxs-lookup"><span data-stu-id="017da-112">When you process a data mining structure, the data in the source is transferred to the mining structure and persisted on disk in a new, compressed format.</span></span> <span data-ttu-id="017da-113">并不会处理数据源中的每个列，而仅会处理绑定所定义的挖掘结构中包含的列。</span><span class="sxs-lookup"><span data-stu-id="017da-113">Not every column in the data source is processed: only the columns that are included in the mining structure, as defined by the bindings.</span></span>  
  
 <span data-ttu-id="017da-114">使用此数据， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 生成所有数据和离散化列的索引，并对连续列创建单独索引。</span><span class="sxs-lookup"><span data-stu-id="017da-114">Using this data, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] builds an index of all data and discretized columns, and creates a separate index for continuous columns.</span></span> <span data-ttu-id="017da-115">针对每个嵌套表发出一个查询以创建索引，并根据每个嵌套表生成一个额外查询，以处理每对嵌套表和事例表之间的关系。</span><span class="sxs-lookup"><span data-stu-id="017da-115">One query is issued for each nested table to create the index, and an additional query per nested table is generated to process relationships between each pair of a nested table and case table.</span></span> <span data-ttu-id="017da-116">创建多个查询的原因在于处理特殊的内部多维数据存储区。</span><span class="sxs-lookup"><span data-stu-id="017da-116">The reason for creating multiple queries is to process a special internal multidimensional data store.</span></span> <span data-ttu-id="017da-117">您可以通过设置服务器属性 `DatabaseConnectionPoolMax` 来限制 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 发送到关系存储区的查询数。</span><span class="sxs-lookup"><span data-stu-id="017da-117">You can limit the number of queries that [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sends to the relational store by setting the server property, `DatabaseConnectionPoolMax`.</span></span> <span data-ttu-id="017da-118">有关详细信息，请参阅 [OLAP Properties](../server-properties/olap-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="017da-118">For more information, see [OLAP Properties](../server-properties/olap-properties.md).</span></span>  
  
 <span data-ttu-id="017da-119">处理模型时，模型不会从数据源中重新读取数据，而从挖掘结构获取数据摘要。</span><span class="sxs-lookup"><span data-stu-id="017da-119">When you process the model, the model does not reread the data from the data source, but instead gets the summary of the data from the mining structure.</span></span> <span data-ttu-id="017da-120">服务器将使用创建的多维数据集以及缓存的索引和事例数据来创建独立的线程，以便为模型定型。</span><span class="sxs-lookup"><span data-stu-id="017da-120">Using the cube that was created, together with the cached index and case data has been cached, the server creates independent threads to train the models.</span></span>  
  
 <span data-ttu-id="017da-121">有关支持并行模型处理的版本的详细信息 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，请参阅 SQL Server 2012 (的各个[版本支持的功能](https://go.microsoft.com/fwlink/?linkid=232473) https://go.microsoft.com/fwlink/?linkid=232473) 。</span><span class="sxs-lookup"><span data-stu-id="017da-121">For more information about the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that support Parallel Model Processing, see [Features Supported by the Editions of SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473) (https://go.microsoft.com/fwlink/?linkid=232473).</span></span>  
  
##  <a name="processing-mining-structures"></a><a name="bkmk_ProcessStructures"></a><span data-ttu-id="017da-122">处理挖掘结构</span><span class="sxs-lookup"><span data-stu-id="017da-122">Processing Mining Structures</span></span>  
 <span data-ttu-id="017da-123">可以一起处理所有相关模型的挖掘结构，也可以单独进行处理。</span><span class="sxs-lookup"><span data-stu-id="017da-123">A mining structure can be processed together with all dependent models, or separately.</span></span> <span data-ttu-id="017da-124">在预期某些模型要用较长时间进行处理并且您想要延迟该操作时，从各模型单独处理挖掘结构可能会很有用。</span><span class="sxs-lookup"><span data-stu-id="017da-124">Processing a mining structure separately from models can be useful when some models are expected to take a long time to process and you want to defer that operation.</span></span>  
  
 <span data-ttu-id="017da-125">有关详细信息，请参阅 [Process a Mining Structure](process-a-mining-structure.md)。</span><span class="sxs-lookup"><span data-stu-id="017da-125">For more information, see [Process a Mining Structure](process-a-mining-structure.md).</span></span>  
  
 <span data-ttu-id="017da-126">如果您十分关注对硬盘空间的节省，则请注意 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 将挖掘结构缓存保留在本地。</span><span class="sxs-lookup"><span data-stu-id="017da-126">If you are concerned about conserving hard disk space, note that [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] retains mining structure caches locally.</span></span> <span data-ttu-id="017da-127">也就是说，所有定型数据都将写在本地硬盘上。</span><span class="sxs-lookup"><span data-stu-id="017da-127">That is, it writes out all the training data to your local hard disk.</span></span> <span data-ttu-id="017da-128">如果您不希望缓存数据，则可以将挖掘结构的 <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> 属性设置为 `ClearAfterProcessing`，从而更改默认值。</span><span class="sxs-lookup"><span data-stu-id="017da-128">If you do not want the data cached, you can change the default by setting the <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> property on the mining structure to `ClearAfterProcessing`.</span></span> <span data-ttu-id="017da-129">这会在处理模型之后破坏缓存；但是，这还会在挖掘结构中禁用钻取功能。</span><span class="sxs-lookup"><span data-stu-id="017da-129">This will destroy the cache after models are processed; however, it will also disable drillthrough on the mining structure.</span></span> <span data-ttu-id="017da-130">有关详细信息，请参阅 [钻取查询（数据挖掘）](drillthrough-queries-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="017da-130">For more information, see [Drillthrough Queries &#40;Data Mining&#41;](drillthrough-queries-data-mining.md).</span></span>  
  
 <span data-ttu-id="017da-131">此外，如果您清理了缓存，则将无法使用维持测试集；如果已定义一个维持测试集，则此测试集分区的定义也将丢失。</span><span class="sxs-lookup"><span data-stu-id="017da-131">Also, if you clear the cache, you will not be able to use the holdout test set, if you defined one, and the definition of the test set partition will be lost.</span></span> <span data-ttu-id="017da-132">有关维持测试集的详细信息，请参阅 [定型和测试数据集](training-and-testing-data-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="017da-132">For more information about holdout test sets, see [Training and Testing Data Sets](training-and-testing-data-sets.md).</span></span>  
  
##  <a name="processing-mining-models"></a><a name="bkmk_ProcessModels"></a> <span data-ttu-id="017da-133">处理挖掘模型</span><span class="sxs-lookup"><span data-stu-id="017da-133">Processing Mining Models</span></span>  
 <span data-ttu-id="017da-134">您可以独立于其关联的挖掘结构来处理挖掘模型，也可以与该结构一起处理基于该结构的所有模型。</span><span class="sxs-lookup"><span data-stu-id="017da-134">You can process a mining model separately from its associated mining structure, or you can process all models that are based on the structure, together with the structure.</span></span>  
  
 <span data-ttu-id="017da-135">有关详细信息，请参阅 [处理挖掘模型](process-a-mining-model.md)。</span><span class="sxs-lookup"><span data-stu-id="017da-135">For more information, see [Process a Mining Model](process-a-mining-model.md).</span></span>  
  
 <span data-ttu-id="017da-136">但在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 和 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，不能选择多个要与结构一起处理的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="017da-136">However, in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you cannot multiselect mining models to process with the structure.</span></span> <span data-ttu-id="017da-137">如果您需要控制所处理的模型，则必须单独选择这些模型，或者使用 XMLA 或 DMX 连续处理多个模型。</span><span class="sxs-lookup"><span data-stu-id="017da-137">If you need to control which models are processed, you must select them individually, or use XMLA or DMX to process models serially.</span></span>  
  
## <a name="when-reprocessing-is-required"></a><span data-ttu-id="017da-138">在需要重新处理时</span><span class="sxs-lookup"><span data-stu-id="017da-138">When Reprocessing is Required</span></span>  
 <span data-ttu-id="017da-139">在开始用定义的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 模型进行工作之前，必须对其进行处理。</span><span class="sxs-lookup"><span data-stu-id="017da-139">You must process the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] models that you define before you can start to work with them.</span></span> <span data-ttu-id="017da-140">无论何时更改挖掘模型结构、更新定型数据、更改现有挖掘模型或在结构中添加挖掘模型，都必须重新处理挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="017da-140">You must also reprocess the mining models whenever you change the mining model structure, update the training data, change an existing mining model, or add a new mining model to the structure.</span></span>  
  
 <span data-ttu-id="017da-141">在以下方案中也处理挖掘模型：</span><span class="sxs-lookup"><span data-stu-id="017da-141">Mining models are also processed in these scenarios:</span></span>  
  
 <span data-ttu-id="017da-142">**部署项目**：部署项目时，项目中的挖掘模型通常依赖于项目设置和项目的当前状态进行完全处理。</span><span class="sxs-lookup"><span data-stu-id="017da-142">**Deployment of a project**: Depending on the project settings and the current state of the project, the mining models in the project are typically processed in full when the project is deployed.</span></span>  
  
 <span data-ttu-id="017da-143">启动部署时处理即自动开始，除非 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 服务器上有以前处理过的版本且没有发生结构更改。</span><span class="sxs-lookup"><span data-stu-id="017da-143">When you initiate deployment, processing starts automatically, unless there is a previously processed version on the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] server and there have been no structural changes.</span></span> <span data-ttu-id="017da-144">可以通过选中下拉列表中的“部署解决方案”\*\*\*\* 或按 F5 键来部署项目。</span><span class="sxs-lookup"><span data-stu-id="017da-144">You can deploy a project by selecting **Deploy solution** from the drop-down list or by pressing the F5 key.</span></span> <span data-ttu-id="017da-145">可以</span><span class="sxs-lookup"><span data-stu-id="017da-145">You can</span></span>  
  
 <span data-ttu-id="017da-146">有关如何设置控制挖掘模型部署方式的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 部署属性的详细信息，请参阅 [部署数据挖掘解决方案](deployment-of-data-mining-solutions.md)。</span><span class="sxs-lookup"><span data-stu-id="017da-146">For more information about how to set [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] deployment properties that control how mining models are deployed, see [Deployment of Data Mining Solutions](deployment-of-data-mining-solutions.md).</span></span>  
  
 <span data-ttu-id="017da-147">**移动挖掘模型**：在您通过使用 EXPORT 命令移动某一挖掘模型时，将只导出该模型的定义，这包括应该向该模型提供数据的挖掘结构的名称。</span><span class="sxs-lookup"><span data-stu-id="017da-147">**Moving a mining model**: When you move a mining model by using the EXPORT command, only the definition of the model is exported, which includes the name of the mining structure that is expected to provide data to the model.</span></span>  
  
 <span data-ttu-id="017da-148">针对以下方案使用 EXPORT 和 IMPORT 命令进行重新处理的要求：</span><span class="sxs-lookup"><span data-stu-id="017da-148">Reprocessing requirements for the following scenarios using the EXPORT and IMPORT commands:</span></span>  
  
-   <span data-ttu-id="017da-149">挖掘结构在目标实例上存在，并且挖掘结构处于未处理状态。</span><span class="sxs-lookup"><span data-stu-id="017da-149">The mining structure exists on the target instance and the mining structure is in an unprocessed state.</span></span>  
  
     <span data-ttu-id="017da-150">必须重新处理结构和模型。</span><span class="sxs-lookup"><span data-stu-id="017da-150">Both the structure and model must be reprocessed.</span></span>  
  
-   <span data-ttu-id="017da-151">挖掘结构在目标实例上存在，并且挖掘结构已处理。</span><span class="sxs-lookup"><span data-stu-id="017da-151">The mining structure exists on the target instance and the mining structure has been processed.</span></span> <span data-ttu-id="017da-152">仅导出了挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="017da-152">Only the mining model was exported.</span></span>  
  
     <span data-ttu-id="017da-153">可以不进行处理便使用模型。</span><span class="sxs-lookup"><span data-stu-id="017da-153">The model can be used without processing.</span></span>  
  
-   <span data-ttu-id="017da-154">还通过使用 WITH DEENDENCIES 关键字导出了挖掘模型定义。</span><span class="sxs-lookup"><span data-stu-id="017da-154">The mining structure definition was also exported by using the WITH DEENDENCIES keyword.</span></span>  
  
     <span data-ttu-id="017da-155">必须重新处理结构和模型。</span><span class="sxs-lookup"><span data-stu-id="017da-155">Both the structure and model must be reprocessed.</span></span>  
  
 <span data-ttu-id="017da-156">有关详细信息，请参阅 [导出和导入数据挖掘对象](export-and-import-data-mining-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="017da-156">For more information, see [Export and Import Data Mining Objects](export-and-import-data-mining-objects.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="017da-157">另请参阅</span><span class="sxs-lookup"><span data-stu-id="017da-157">See Also</span></span>  
 <span data-ttu-id="017da-158">[挖掘结构 &#40;Analysis Services 数据挖掘&#41;](mining-structures-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="017da-158">[Mining Structures &#40;Analysis Services - Data Mining&#41;](mining-structures-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="017da-159">[挖掘结构 &#40;Analysis Services 数据挖掘&#41;](mining-structures-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="017da-159">[Mining Structures &#40;Analysis Services - Data Mining&#41;](mining-structures-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="017da-160">多维模型对象处理</span><span class="sxs-lookup"><span data-stu-id="017da-160">Multidimensional Model Object Processing</span></span>](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md)  
  
  
