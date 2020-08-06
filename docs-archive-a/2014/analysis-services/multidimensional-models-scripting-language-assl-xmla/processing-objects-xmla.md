---
title: ) XMLA (处理对象 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- errors [XML for Analysis]
- objects [XML for Analysis]
- XML for Analysis, objects
- XMLA, partitions
- partitions [Analysis Services], XML for Analysis
- XML for Analysis, partitions
- writeback [Analysis Services], XML for Analysis
- out-of-line bindings
- processing objects [XML for Analysis]
- XMLA, objects
ms.assetid: a65b3249-303d-49c6-98af-6ac6eed11a03
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2e59c7953ae8fc7d3cfceafa7b0e9d8c7186daf8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692591"
---
# <a name="processing-objects-xmla"></a><span data-ttu-id="b1605-102">处理对象 (XMLA)</span><span class="sxs-lookup"><span data-stu-id="b1605-102">Processing Objects (XMLA)</span></span>
  <span data-ttu-id="b1605-103">在中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，处理是将数据转换为业务分析信息的步骤或一系列步骤。</span><span class="sxs-lookup"><span data-stu-id="b1605-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], processing is the step or series of steps that turn data into information for business analysis.</span></span> <span data-ttu-id="b1605-104">处理因对象类型而异，但处理始终是将数据转换为信息的一个环节。</span><span class="sxs-lookup"><span data-stu-id="b1605-104">Processing is different depending on the type of object, but processing is always part of turning data into information.</span></span>  
  
 <span data-ttu-id="b1605-105">若要处理 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 对象，可以使用 "[处理](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla)" 命令。</span><span class="sxs-lookup"><span data-stu-id="b1605-105">To process an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] object, you can use the [Process](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla) command.</span></span> <span data-ttu-id="b1605-106">`Process` 命令可以对 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例处理以下对象：</span><span class="sxs-lookup"><span data-stu-id="b1605-106">The `Process` command can process the following objects on an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance:</span></span>  
  
-   <span data-ttu-id="b1605-107">多维数据集</span><span class="sxs-lookup"><span data-stu-id="b1605-107">Cubes</span></span>  
  
-   <span data-ttu-id="b1605-108">数据库</span><span class="sxs-lookup"><span data-stu-id="b1605-108">Databases</span></span>  
  
-   <span data-ttu-id="b1605-109">维度</span><span class="sxs-lookup"><span data-stu-id="b1605-109">Dimensions</span></span>  
  
-   <span data-ttu-id="b1605-110">度量值组</span><span class="sxs-lookup"><span data-stu-id="b1605-110">Measure groups</span></span>  
  
-   <span data-ttu-id="b1605-111">挖掘模型</span><span class="sxs-lookup"><span data-stu-id="b1605-111">Mining models</span></span>  
  
-   <span data-ttu-id="b1605-112">挖掘结构</span><span class="sxs-lookup"><span data-stu-id="b1605-112">Mining structures</span></span>  
  
-   <span data-ttu-id="b1605-113">分区</span><span class="sxs-lookup"><span data-stu-id="b1605-113">Partitions</span></span>  
  
 <span data-ttu-id="b1605-114">为了控制对象的处理，`Process` 命令有多个可设置的属性。</span><span class="sxs-lookup"><span data-stu-id="b1605-114">To control the processing of objects, the `Process` command has various properties that can be set.</span></span> <span data-ttu-id="b1605-115">`Process` 命令的属性可以控制以下方面：处理的程度、处理的对象、是否使用外部绑定、如何处理错误以及如何管理写回表。</span><span class="sxs-lookup"><span data-stu-id="b1605-115">The `Process` command has properties that control: how much processing will be done, which objects will be processed, whether to use out-of-line bindings, how to handle errors, and how to manage writeback tables.</span></span>  
  
## <a name="specifying-processing-options"></a><span data-ttu-id="b1605-116">指定处理选项</span><span class="sxs-lookup"><span data-stu-id="b1605-116">Specifying Processing Options</span></span>  
 <span data-ttu-id="b1605-117">命令的[Type](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/type-element-xmla)属性 `Process` 指定处理对象时要使用的处理选项。</span><span class="sxs-lookup"><span data-stu-id="b1605-117">The [Type](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/type-element-xmla) property of the `Process` command specifies the processing option to use when processing the object.</span></span> <span data-ttu-id="b1605-118">有关处理选项的详细信息，请参阅[处理选项和设置 (Analysis Services)](../multidimensional-models/processing-options-and-settings-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="b1605-118">For more information about processing options, see [Processing Options and Settings &#40;Analysis Services&#41;](../multidimensional-models/processing-options-and-settings-analysis-services.md).</span></span>  
  
 <span data-ttu-id="b1605-119">下表列出了 `Type` 属性的各个常量以及使用每一常量时可处理的不同对象。</span><span class="sxs-lookup"><span data-stu-id="b1605-119">The following table lists the constants for the `Type` property and the various objects that can be processed using each constant.</span></span>  
  
|<span data-ttu-id="b1605-120">`Type` 值</span><span class="sxs-lookup"><span data-stu-id="b1605-120">`Type` value</span></span>|<span data-ttu-id="b1605-121">适用对象</span><span class="sxs-lookup"><span data-stu-id="b1605-121">Applicable objects</span></span>|  
|--------------------|------------------------|  
|<span data-ttu-id="b1605-122">*ProcessFull*</span><span class="sxs-lookup"><span data-stu-id="b1605-122">*ProcessFull*</span></span>|<span data-ttu-id="b1605-123">多维数据集、数据库、维度、度量值组、挖掘模型、挖掘结构和分区</span><span class="sxs-lookup"><span data-stu-id="b1605-123">Cube, database, dimension, measure group, mining model, mining structure, partition</span></span>|  
|<span data-ttu-id="b1605-124">*ProcessAdd*</span><span class="sxs-lookup"><span data-stu-id="b1605-124">*ProcessAdd*</span></span>|<span data-ttu-id="b1605-125">维度和分区</span><span class="sxs-lookup"><span data-stu-id="b1605-125">Dimension, partition</span></span>|  
|<span data-ttu-id="b1605-126">*ProcessUpdate*</span><span class="sxs-lookup"><span data-stu-id="b1605-126">*ProcessUpdate*</span></span>|<span data-ttu-id="b1605-127">维度</span><span class="sxs-lookup"><span data-stu-id="b1605-127">Dimension</span></span>|  
|<span data-ttu-id="b1605-128">*ProcessIndexes*</span><span class="sxs-lookup"><span data-stu-id="b1605-128">*ProcessIndexes*</span></span>|<span data-ttu-id="b1605-129">维度、多维数据集、度量值组和分区</span><span class="sxs-lookup"><span data-stu-id="b1605-129">Dimension, cube, measure group, partition</span></span>|  
|<span data-ttu-id="b1605-130">*ProcessData*</span><span class="sxs-lookup"><span data-stu-id="b1605-130">*ProcessData*</span></span>|<span data-ttu-id="b1605-131">维度、多维数据集、度量值组和分区</span><span class="sxs-lookup"><span data-stu-id="b1605-131">Dimension, cube, measure group, partition</span></span>|  
|<span data-ttu-id="b1605-132">*ProcessDefault*</span><span class="sxs-lookup"><span data-stu-id="b1605-132">*ProcessDefault*</span></span>|<span data-ttu-id="b1605-133">多维数据集、数据库、维度、度量值组、挖掘模型、挖掘结构和分区</span><span class="sxs-lookup"><span data-stu-id="b1605-133">Cube, database, dimension, measure group, mining model, mining structure, partition</span></span>|  
|<span data-ttu-id="b1605-134">*ProcessClear*</span><span class="sxs-lookup"><span data-stu-id="b1605-134">*ProcessClear*</span></span>|<span data-ttu-id="b1605-135">多维数据集、数据库、维度、度量值组、挖掘模型、挖掘结构和分区</span><span class="sxs-lookup"><span data-stu-id="b1605-135">Cube, database, dimension, measure group, mining model, mining structure, partition</span></span>|  
|<span data-ttu-id="b1605-136">*ProcessStructure*</span><span class="sxs-lookup"><span data-stu-id="b1605-136">*ProcessStructure*</span></span>|<span data-ttu-id="b1605-137">多维数据集和挖掘结构</span><span class="sxs-lookup"><span data-stu-id="b1605-137">Cube, mining structure</span></span>|  
|<span data-ttu-id="b1605-138">*ProcessClearStructureOnly*</span><span class="sxs-lookup"><span data-stu-id="b1605-138">*ProcessClearStructureOnly*</span></span>|<span data-ttu-id="b1605-139">挖掘结构</span><span class="sxs-lookup"><span data-stu-id="b1605-139">Mining structure</span></span>|  
|<span data-ttu-id="b1605-140">*ProcessScriptCache*</span><span class="sxs-lookup"><span data-stu-id="b1605-140">*ProcessScriptCache*</span></span>|<span data-ttu-id="b1605-141">多维数据集</span><span class="sxs-lookup"><span data-stu-id="b1605-141">Cube</span></span>|  
  
 <span data-ttu-id="b1605-142">有关处理对象的详细信息 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，请参阅[多维模型对象处理](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="b1605-142">For more information about processing [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects, see [Multidimensional Model Object Processing](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md).</span></span>  
  
## <a name="specifying-objects-to-be-processed"></a><span data-ttu-id="b1605-143">指定要处理的对象</span><span class="sxs-lookup"><span data-stu-id="b1605-143">Specifying Objects to be Processed</span></span>  
 <span data-ttu-id="b1605-144">命令的[对象](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)属性 `Process` 包含要处理的对象的对象标识符。</span><span class="sxs-lookup"><span data-stu-id="b1605-144">The [Object](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) property of the `Process` command contains the object identifier of the object to be processed.</span></span> <span data-ttu-id="b1605-145">在 `Process` 命令中仅可指定一个对象，但是在处理一个对象的同时会处理其所有子对象。</span><span class="sxs-lookup"><span data-stu-id="b1605-145">Only one object can be specified in a `Process` command, but processing an object also processes any child objects.</span></span> <span data-ttu-id="b1605-146">例如，在处理多维数据集中的一个度量值组时会处理该度量值组的所有分区；在处理一个数据库时会处理该数据库所包含的所有对象，包括多维数据集、维度和挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="b1605-146">For example, processing a measure group in a cube processes all the partitions for that measure group, while processing a database processes all the objects, including cubes, dimensions, and mining structures, that are contained by the database.</span></span>  
  
 <span data-ttu-id="b1605-147">如果将 `ProcessAffectedObjects` 命令的 `Process` 属性设置为 true，则处理指定对象时所影响的所有相关对象都会得到处理。</span><span class="sxs-lookup"><span data-stu-id="b1605-147">If you set the `ProcessAffectedObjects` attribute of the `Process` command to true, any related object affected by processing the specified object is also processed.</span></span> <span data-ttu-id="b1605-148">例如，如果通过使用命令中的*ProcessUpdate*处理选项增量更新维度 `Process` ，则如果将 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] `ProcessAffectedObjects` 设置为 true，则也会处理其聚合因添加或删除成员而失效的任何分区。</span><span class="sxs-lookup"><span data-stu-id="b1605-148">For example, if a dimension is incrementally updated by using the *ProcessUpdate* processing option in the `Process` command, any partition whose aggregations are invalidated because of members being added or deleted is also processed by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] if `ProcessAffectedObjects` is set to true.</span></span> <span data-ttu-id="b1605-149">在这种情况下，单个 `Process` 命令可以处理 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例上的多个对象，但是 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 会确定除 `Process` 命令中指定的单个对象外，哪些对象也必须加以处理。</span><span class="sxs-lookup"><span data-stu-id="b1605-149">In this case, a single `Process` command can process multiple objects on an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance, but [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] determines which objects besides the single object specified in the `Process` command must also be processed.</span></span>  
  
 <span data-ttu-id="b1605-150">不过，在 `Process` 命令中使用多个 `Batch` 命令可以同时处理多个对象，如多个维度。</span><span class="sxs-lookup"><span data-stu-id="b1605-150">However, you can process multiple objects, such as dimensions, at the same time by using multiple `Process` commands within a `Batch` command.</span></span> <span data-ttu-id="b1605-151">与使用 `ProcessAffectedObjects` 属性相比，批处理操作可为 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例上对象的串行或并行处理提供更为精确的控制，从而为较大的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库提供更好的处理方法。</span><span class="sxs-lookup"><span data-stu-id="b1605-151">Batch operations provide a finer level of control for serial or parallel processing of objects on an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance than using the `ProcessAffectedObjects` attribute, and let you to tune your processing approach for larger [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] databases.</span></span> <span data-ttu-id="b1605-152">有关执行批处理操作的详细信息，请参阅[&#40;XMLA&#41;执行批处理操作](performing-batch-operations-xmla.md)。</span><span class="sxs-lookup"><span data-stu-id="b1605-152">For more information about performing batch operations, see [Performing Batch Operations &#40;XMLA&#41;](performing-batch-operations-xmla.md).</span></span>  
  
## <a name="specifying-out-of-line-bindings"></a><span data-ttu-id="b1605-153">指定外部绑定</span><span class="sxs-lookup"><span data-stu-id="b1605-153">Specifying Out-of-Line Bindings</span></span>  
 <span data-ttu-id="b1605-154">如果命令 `Process` 未包含在命令中 `Batch` ，则可以选择在命令的[bindings](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/bindings-element-xmla)、 [DataSource](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla)和[DataSourceView](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/datasourceview-element-xmla)属性中 `Process` 为要处理的对象指定外绑定。</span><span class="sxs-lookup"><span data-stu-id="b1605-154">If the `Process` command is not contained by a `Batch` command, you can optionally specify out-of-line bindings in the [Bindings](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/bindings-element-xmla), [DataSource](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla), and [DataSourceView](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/datasourceview-element-xmla) properties of the `Process` command for the objects to be processed.</span></span> <span data-ttu-id="b1605-155">外部绑定是对数据源、数据源视图和其他对象的引用（在这些数据源、数据源视图和对象中，该绑定仅在执行 `Process` 命令时存在），并会覆盖与所处理对象关联的所有现有绑定。</span><span class="sxs-lookup"><span data-stu-id="b1605-155">Out-of-line bindings are references to data sources, data source views, and other objects in which the binding exists only during the execution of the `Process` command, and which override any existing bindings associated with the objects being processed.</span></span> <span data-ttu-id="b1605-156">如果未指定外部绑定，则使用当前与要处理的对象关联的绑定。</span><span class="sxs-lookup"><span data-stu-id="b1605-156">If out-of-line bindings are not specified, the bindings currently associated with the objects to be processed are used.</span></span>  
  
 <span data-ttu-id="b1605-157">外部绑定用在以下情况下：</span><span class="sxs-lookup"><span data-stu-id="b1605-157">Out-of-line bindings are used in the following circumstances:</span></span>  
  
-   <span data-ttu-id="b1605-158">增量处理一个分区，其中必须指定另一个事实数据表或现有事实数据表上的一个筛选器以确保不会对行进行两次计数。</span><span class="sxs-lookup"><span data-stu-id="b1605-158">Incrementally processing a partition, in which an alternative fact table or a filter on the existing fact table must be specified to make sure that rows are not counted twice.</span></span>  
  
-   <span data-ttu-id="b1605-159">使用中的数据流任务在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 处理维度、挖掘模型或分区时提供数据。</span><span class="sxs-lookup"><span data-stu-id="b1605-159">Using a data flow task in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] to provide data while processing a dimension, mining model, or partition.</span></span>  
  
 <span data-ttu-id="b1605-160">外部绑定属于 Analysis Services 脚本语言 (ASSL) 的一部分。</span><span class="sxs-lookup"><span data-stu-id="b1605-160">Out-of-line bindings are described as part of the Analysis Services Scripting Language (ASSL).</span></span> <span data-ttu-id="b1605-161">有关 ASSL 中的传出绑定的详细信息，请参阅[SSAS 多维&#41;的数据源和绑定 &#40;](../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)。</span><span class="sxs-lookup"><span data-stu-id="b1605-161">For more information about out-of-line bindings in ASSL, see [Data Sources and Bindings &#40;SSAS Multidimensional&#41;](../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).</span></span>  
  
### <a name="incrementally-updating-partitions"></a><span data-ttu-id="b1605-162">增量更新分区</span><span class="sxs-lookup"><span data-stu-id="b1605-162">Incrementally Updating Partitions</span></span>  
 <span data-ttu-id="b1605-163">增量更新已处理的分区时通常需要外部绑定，原因在于为该分区指定的绑定会引用已在该分区中聚合的事实数据表数据。</span><span class="sxs-lookup"><span data-stu-id="b1605-163">Incrementally updating an already processed partition typically requires an out-of-line binding because the binding specified for the partition references fact table data already aggregated within the partition.</span></span> <span data-ttu-id="b1605-164">使用 `Process` 命令增量更新已处理的分区时，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 会执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="b1605-164">When incrementally updating an already processed partition by using the `Process` command, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] performs the following actions:</span></span>  
  
-   <span data-ttu-id="b1605-165">创建一个与要增量更新的分区具有相同结构的临时分区。</span><span class="sxs-lookup"><span data-stu-id="b1605-165">Creates a temporary partition with a structure identical to that of the partition to be incrementally updated.</span></span>  
  
-   <span data-ttu-id="b1605-166">使用 `Process` 命令中指定的外部绑定处理该临时分区。</span><span class="sxs-lookup"><span data-stu-id="b1605-166">Processes the temporary partition, using the out-of-line binding specified in the `Process` command.</span></span>  
  
-   <span data-ttu-id="b1605-167">将该临时分区与所选现有分区合并。</span><span class="sxs-lookup"><span data-stu-id="b1605-167">Merges the temporary partition with the existing selected partition.</span></span>  
  
 <span data-ttu-id="b1605-168">有关使用 XML for Analysis (XMLA) 合并分区的详细信息，请参阅将[分区合并 &#40;xmla&#41;](merging-partitions-xmla.md)。</span><span class="sxs-lookup"><span data-stu-id="b1605-168">For more information about merging partitions using XML for Analysis (XMLA), see [Merging Partitions &#40;XMLA&#41;](merging-partitions-xmla.md).</span></span>  
  
## <a name="handling-processing-errors"></a><span data-ttu-id="b1605-169">对处理错误进行处理</span><span class="sxs-lookup"><span data-stu-id="b1605-169">Handling Processing Errors</span></span>  
 <span data-ttu-id="b1605-170">使用该命令的[ErrorConfiguration](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/errorconfiguration-element-xmla)属性 `Process` 可以指定如何处理处理对象时遇到的错误。</span><span class="sxs-lookup"><span data-stu-id="b1605-170">The [ErrorConfiguration](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/errorconfiguration-element-xmla) property of the `Process` command lets you specify how to handle errors encountered while processing an object.</span></span> <span data-ttu-id="b1605-171">例如，在处理维度时，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 在键属性的键列中遇到重复的值。</span><span class="sxs-lookup"><span data-stu-id="b1605-171">For example, while processing a dimension, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] encounters a duplicate value in the key column of the key attribute.</span></span> <span data-ttu-id="b1605-172">因为属性键必须是唯一的，因此 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 丢弃重复的记录。</span><span class="sxs-lookup"><span data-stu-id="b1605-172">Because attribute keys must be unique, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] discards the duplicate records.</span></span> <span data-ttu-id="b1605-173">基于的[KeyDuplicate](https://docs.microsoft.com/bi-reference/assl/properties/keyduplicate-element-assl)属性 `ErrorConfiguration` ， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 可以：</span><span class="sxs-lookup"><span data-stu-id="b1605-173">Based on the [KeyDuplicate](https://docs.microsoft.com/bi-reference/assl/properties/keyduplicate-element-assl) property of `ErrorConfiguration`, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] could:</span></span>  
  
-   <span data-ttu-id="b1605-174">忽略错误并继续处理该维度。</span><span class="sxs-lookup"><span data-stu-id="b1605-174">Ignore the error and continue processing the dimension.</span></span>  
  
-   <span data-ttu-id="b1605-175">返回说明 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 遇到了重复键的消息并继续处理。</span><span class="sxs-lookup"><span data-stu-id="b1605-175">Return a message that states [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] encountered a duplicate key and continue processing.</span></span>  
  
 <span data-ttu-id="b1605-176">`ErrorConfiguration` 可为执行 `Process` 命令过程中遇到的许多类似情况提供各种选项。</span><span class="sxs-lookup"><span data-stu-id="b1605-176">There are many similar conditions for which `ErrorConfiguration` provides options during a `Process` command.</span></span>  
  
## <a name="managing-writeback-tables"></a><span data-ttu-id="b1605-177">管理写回表</span><span class="sxs-lookup"><span data-stu-id="b1605-177">Managing Writeback Tables</span></span>  
 <span data-ttu-id="b1605-178">如果 `Process` 命令遇到一个可写入的分区或者此类分区的多维数据集或度量值组，而且是未完整处理的，则该分区的写回表可能不存在。</span><span class="sxs-lookup"><span data-stu-id="b1605-178">If the `Process` command encounters a write-enabled partition, or a cube or measure group for such a partition, that is not already fully processed, a writeback table may not already exist for that partition.</span></span> <span data-ttu-id="b1605-179">命令的[WritebackTableCreation](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/writebacktablecreation-element-xmla)属性 `Process` 确定是否 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 应创建写回表。</span><span class="sxs-lookup"><span data-stu-id="b1605-179">The [WritebackTableCreation](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/writebacktablecreation-element-xmla) property of the `Process` command determines whether [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] should create a writeback table.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="b1605-180">示例</span><span class="sxs-lookup"><span data-stu-id="b1605-180">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="b1605-181">说明</span><span class="sxs-lookup"><span data-stu-id="b1605-181">Description</span></span>  
 <span data-ttu-id="b1605-182">下面的示例对 [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] 示例 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库进行完整处理。</span><span class="sxs-lookup"><span data-stu-id="b1605-182">The following example fully processes the [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] sample [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span>  
  
### <a name="code"></a><span data-ttu-id="b1605-183">代码</span><span class="sxs-lookup"><span data-stu-id="b1605-183">Code</span></span>  
  
```  
<Process xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
  <Object>  
    <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
  </Object>  
  <Type>ProcessFull</Type>  
  <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
</Process>  
```  
  
### <a name="description"></a><span data-ttu-id="b1605-184">说明</span><span class="sxs-lookup"><span data-stu-id="b1605-184">Description</span></span>  
 <span data-ttu-id="b1605-185">下面的示例在示例数据库中以增量**方式处理艾德 DW**多维数据集的 " **Internet Sales** " 度量值组中的**Internet_Sales_2004**分区 [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="b1605-185">The following example incrementally processes the **Internet_Sales_2004** partition in the **Internet Sales** measure group of the **Adventure Works DW** cube in the [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] sample [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="b1605-186">`Process`命令通过在命令的属性中使用传出查询绑定来 `Bindings` `Process` 检索要从中生成要添加到分区中的聚合的事实数据表行，从而向分区添加顺序为2006年12月31日的聚合。</span><span class="sxs-lookup"><span data-stu-id="b1605-186">The `Process` command is adding aggregations for order dates later than December 31, 2006 to the partition by using an out-of-line query binding in the `Bindings` property of the `Process` command to retrieve the fact table rows from which to generate aggregations to add to the partition.</span></span>  
  
### <a name="code"></a><span data-ttu-id="b1605-187">代码</span><span class="sxs-lookup"><span data-stu-id="b1605-187">Code</span></span>  
  
```  
<Process ProcessAffectedObjects="true" xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
  <Object>  
    <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
    <CubeID>Adventure Works DW</CubeID>  
    <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
    <PartitionID>Internet_Sales_2006</PartitionID>  
  </Object>  
  <Bindings>  
    <Binding>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2006</PartitionID>  
      <Source xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="QueryBinding">  
        <DataSourceID>Adventure Works DW</DataSourceID>  
        <QueryDefinition>  
          SELECT  
            [dbo].[FactInternetSales].[ProductKey],  
            [dbo].[FactInternetSales].[OrderDateKey],  
            [dbo].[FactInternetSales].[DueDateKey],  
            [dbo].[FactInternetSales].[ShipDateKey],   
            [dbo].[FactInternetSales].[CustomerKey],   
            [dbo].[FactInternetSales].[PromotionKey],  
            [dbo].[FactInternetSales].[CurrencyKey],  
            [dbo].[FactInternetSales].[SalesTerritoryKey],  
            [dbo].[FactInternetSales].[SalesOrderNumber],  
            [dbo].[FactInternetSales].[SalesOrderLineNumber],  
            [dbo].[FactInternetSales].[RevisionNumber],  
            [dbo].[FactInternetSales].[OrderQuantity],  
            [dbo].[FactInternetSales].[UnitPrice],  
            [dbo].[FactInternetSales].[ExtendedAmount],  
            [dbo].[FactInternetSales].[UnitPriceDiscountPct],  
            [dbo].[FactInternetSales].[DiscountAmount],  
            [dbo].[FactInternetSales].[ProductStandardCost],  
            [dbo].[FactInternetSales].[TotalProductCost],  
            [dbo].[FactInternetSales].[SalesAmount],  
            [dbo].[FactInternetSales].[TaxAmt],  
            [dbo].[FactInternetSales].[Freight],  
            [dbo].[FactInternetSales].[CarrierTrackingNumber],  
            [dbo].[FactInternetSales].[CustomerPONumber]  
          FROM [dbo].[FactInternetSales]  
          WHERE OrderDateKey > '1280'  
        </QueryDefinition>  
      </Source>  
    </Binding>  
  </Bindings>  
  <Type>ProcessAdd</Type>  
  <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
</Process>  
```  
  
  
