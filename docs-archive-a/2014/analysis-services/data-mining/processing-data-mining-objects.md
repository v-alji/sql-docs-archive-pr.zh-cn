---
title: 处理数据挖掘对象 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- processing objects [Analysis Services]
- mining structures [Analysis Services]
- process [Analysis Services]
- mining structures [Analysis Services], creating
- mining structures [Analysis Services], how-to topics
- mining structures [Analysis Services], processing
ms.assetid: 0f6993c0-0917-4935-82f9-7b8a8a7cc627
author: minewiskan
ms.author: owend
ms.openlocfilehash: a4a6693a46679badc068111a311bb82219e752cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690877"
---
# <a name="processing-data-mining-objects"></a><span data-ttu-id="59f1a-102">处理数据挖掘对象</span><span class="sxs-lookup"><span data-stu-id="59f1a-102">Processing Data Mining Objects</span></span>
  <span data-ttu-id="59f1a-103">数据挖掘对象在处理之前只是一个空容器。</span><span class="sxs-lookup"><span data-stu-id="59f1a-103">A data mining object is only an empty container until it has been processed.</span></span> <span data-ttu-id="59f1a-104">“处理\*\* ”数据挖掘模型也称为“定型 \*\*”。</span><span class="sxs-lookup"><span data-stu-id="59f1a-104">*Processing* a data mining model is also called *training*.</span></span>  
  
 <span data-ttu-id="59f1a-105">**处理挖掘结构：** 挖掘结构从列绑定和使用情况元数据定义的外部数据源获取数据，并读取此数据。</span><span class="sxs-lookup"><span data-stu-id="59f1a-105">**Processing mining structures:** A mining structure gets data from an external data source, as defined by the column bindings and usage metadata, and reads the data.</span></span> <span data-ttu-id="59f1a-106">挖掘结构将完全读取此数据，然后对这些数据进行分析以提取各种统计信息。</span><span class="sxs-lookup"><span data-stu-id="59f1a-106">This data is read in full and then analyzed to extract various statistics.</span></span> <span data-ttu-id="59f1a-107">Analysis Services 在本地缓存中存储数据的简洁表示形式，此形式适合于由数据挖掘算法进行分析。</span><span class="sxs-lookup"><span data-stu-id="59f1a-107">Analysis Services stores a compact representation of the data, which is suitable for analysis by data mining algorithms, in a local cache.</span></span> <span data-ttu-id="59f1a-108">处理模型之后，您可以保留或删除此缓存。</span><span class="sxs-lookup"><span data-stu-id="59f1a-108">You can either keep this cache or delete it after your models have been processed.</span></span> <span data-ttu-id="59f1a-109">默认情况下，将存储此缓存。</span><span class="sxs-lookup"><span data-stu-id="59f1a-109">By default, the cache is stored.</span></span> <span data-ttu-id="59f1a-110">有关详细信息，请参阅 [Process a Mining Structure](process-a-mining-structure.md)。</span><span class="sxs-lookup"><span data-stu-id="59f1a-110">For more information, see [Process a Mining Structure](process-a-mining-structure.md).</span></span>  
  
 <span data-ttu-id="59f1a-111">**处理挖掘模型：** 挖掘模型在处理之前为空，仅包含定义。</span><span class="sxs-lookup"><span data-stu-id="59f1a-111">**Processing mining models:** A mining model is empty, containing definitions only, until it is processed.</span></span> <span data-ttu-id="59f1a-112">若要处理挖掘模型，必须已经处理了该模型所基于的挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="59f1a-112">To process a mining model, the mining structure that it is based on must have been processed.</span></span> <span data-ttu-id="59f1a-113">挖掘模型从挖掘结构缓存获取数据，应用该模型上已创建的任何筛选器，然后传递通过算法设置的数据以检测模式。</span><span class="sxs-lookup"><span data-stu-id="59f1a-113">The mining model gets the data from the mining structure cache, applies any filters that may have been created on the model, and then passes the data set through the algorithm to detect patterns.</span></span> <span data-ttu-id="59f1a-114">处理模型之后，该模型仅存储处理的结果，而不会存储数据自身。</span><span class="sxs-lookup"><span data-stu-id="59f1a-114">After the model is processed, the model stores only the results of processing, not the data itself.</span></span> <span data-ttu-id="59f1a-115">有关详细信息，请参阅 [处理挖掘模型](process-a-mining-model.md)。</span><span class="sxs-lookup"><span data-stu-id="59f1a-115">For more information, see [Process a Mining Model](process-a-mining-model.md).</span></span>  
  
 <span data-ttu-id="59f1a-116">下图说明了处理挖掘结构和挖掘模型时的数据流。</span><span class="sxs-lookup"><span data-stu-id="59f1a-116">The following diagram illustrates the flow of data when a mining structure is processed, and when a mining model is processed.</span></span>  
  
 <span data-ttu-id="59f1a-117">![处理数据：源到结构到模型](../media/dmcon-modelarch.gif "处理数据：源到结构到模型")</span><span class="sxs-lookup"><span data-stu-id="59f1a-117">![Processing of data: source to structure to model](../media/dmcon-modelarch.gif "Processing of data: source to structure to model")</span></span>  
  
## <a name="viewing-the-results-of-processing"></a><span data-ttu-id="59f1a-118">查看处理结果</span><span class="sxs-lookup"><span data-stu-id="59f1a-118">Viewing the Results of Processing</span></span>  
 <span data-ttu-id="59f1a-119">处理了挖掘结构后，此挖掘结构包含数据的简洁表示形式，以用于统计分析。</span><span class="sxs-lookup"><span data-stu-id="59f1a-119">After a mining structure has been processed, it contains a compact representation of the data for use in statistical analysis.</span></span> <span data-ttu-id="59f1a-120">如果尚未清除缓存，则可以用以下几种方式访问此缓存中的数据：</span><span class="sxs-lookup"><span data-stu-id="59f1a-120">If the cache has not been cleared, you can access the data in this cache in the following ways:</span></span>  
  
-   <span data-ttu-id="59f1a-121">针对模型创建数据挖掘扩展插件 (DMX) 查询，并钻取到结构中。</span><span class="sxs-lookup"><span data-stu-id="59f1a-121">Creating a Data Mining Extensions (DMX) query on the model and drilling through to the structure.</span></span> <span data-ttu-id="59f1a-122">有关详细信息，请参阅 [SELECT FROM <模型> SAMPLE_CASES (DMX)](/sql/dmx/select-from-model-content-dmx)。</span><span class="sxs-lookup"><span data-stu-id="59f1a-122">For more information, see [SELECT FROM &#60;model&#62;.CASES &#40;DMX&#41;](/sql/dmx/select-from-model-content-dmx).</span></span>  
  
-   <span data-ttu-id="59f1a-123">基于结构浏览模型，并使用用户界面中的其中一个选项钻取到结构事例。</span><span class="sxs-lookup"><span data-stu-id="59f1a-123">Browsing a model based on the structure, and using one of the options in the user interface to drill through to structure cases.</span></span> <span data-ttu-id="59f1a-124">有关详细信息，请参阅 [数据挖掘模型查看器](data-mining-model-viewers.md)或 [从挖掘模型钻取到事例数据](drill-through-to-case-data-from-a-mining-model.md)。</span><span class="sxs-lookup"><span data-stu-id="59f1a-124">For more information, see [Data Mining Model Viewers](data-mining-model-viewers.md), or [Drill Through to Case Data from a Mining Model](drill-through-to-case-data-from-a-mining-model.md).</span></span>  
  
-   <span data-ttu-id="59f1a-125">针对结构事例创建 DMX 查询。</span><span class="sxs-lookup"><span data-stu-id="59f1a-125">Creating a DMX query on the structure cases.</span></span> <span data-ttu-id="59f1a-126">有关详细信息，请参阅 [SELECT FROM <结构> CASES](/sql/dmx/select-from-structure-cases)。</span><span class="sxs-lookup"><span data-stu-id="59f1a-126">For more information, see [SELECT FROM &#60;structure&#62;.CASES](/sql/dmx/select-from-structure-cases).</span></span>  
  
 <span data-ttu-id="59f1a-127">在处理“挖掘模型”之后，该模型仅包含从分析得出的模式，以及缓存定型数据的模型结果的映射。</span><span class="sxs-lookup"><span data-stu-id="59f1a-127">After a mining model has been processed, it contains only the patterns that were derived from analysis, and mappings from the model results to the cached training data.</span></span> <span data-ttu-id="59f1a-128">您可以浏览或查询模型结果（称为“模型内容 \*\*”），也可以查询模型和结构事例（如果已缓存）。</span><span class="sxs-lookup"><span data-stu-id="59f1a-128">You can browse or query the model results, called *model content*, or you can query the model and structure cases, if they have been cached.</span></span>  
  
 <span data-ttu-id="59f1a-129">每个挖掘模型的模型内容取决于创建该模型时所使用的算法。</span><span class="sxs-lookup"><span data-stu-id="59f1a-129">The model content for each mining model depends on the algorithm that was used to create it.</span></span> <span data-ttu-id="59f1a-130">例如，如果一个模型是聚类分析模型，而另一个模型是决策树模型，即使这两个模型使用完全相同的数据，其模型内容也大不相同。</span><span class="sxs-lookup"><span data-stu-id="59f1a-130">For example, if one model is a clustering model and another is a decision trees model, the model content is very different even though the models use exactly the same data.</span></span> <span data-ttu-id="59f1a-131">有关详细信息，请参阅[挖掘模型内容（Analysis Services - 数据挖掘）](mining-model-content-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="59f1a-131">For more information, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
## <a name="processing-requirements"></a><span data-ttu-id="59f1a-132">处理要求</span><span class="sxs-lookup"><span data-stu-id="59f1a-132">Processing Requirements</span></span>  
 <span data-ttu-id="59f1a-133">根据您的挖掘模型是完全基于关系数据还是基于多维数据源，处理要求可能有所不同。</span><span class="sxs-lookup"><span data-stu-id="59f1a-133">Processing requirements may differ depending on whether your mining models are based solely on relational data, or on multidimensional data source.</span></span>  
  
 <span data-ttu-id="59f1a-134">对于关系数据源，处理仅要求创建定型数据并对该数据运行挖掘算法。</span><span class="sxs-lookup"><span data-stu-id="59f1a-134">For relational data source, processing requires only that you create training data and run mining algorithms on that data.</span></span> <span data-ttu-id="59f1a-135">但是，基于 OLAP 对象（如维度和度量值）的挖掘模型则要求基础数据处于已处理状态。</span><span class="sxs-lookup"><span data-stu-id="59f1a-135">However, mining models that are based on OLAP objects, such as dimensions and measures, require that the underlying data be in a processed state.</span></span> <span data-ttu-id="59f1a-136">这可能要求处理多维对象以填充挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="59f1a-136">This may requires that the multidimensional objects be processed to populate the mining model.</span></span>  
  
 <span data-ttu-id="59f1a-137">有关详细信息，请参阅[处理要求和注意事项（数据挖掘）](processing-requirements-and-considerations-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="59f1a-137">For more information, see [Processing Requirements and Considerations &#40;Data Mining&#41;](processing-requirements-and-considerations-data-mining.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59f1a-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="59f1a-138">See Also</span></span>  
 <span data-ttu-id="59f1a-139">[数据挖掘 &#40;钻取查询&#41;](drillthrough-queries-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="59f1a-139">[Drillthrough Queries &#40;Data Mining&#41;](drillthrough-queries-data-mining.md) </span></span>  
 <span data-ttu-id="59f1a-140">[挖掘结构 &#40;Analysis Services 数据挖掘&#41;](mining-structures-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="59f1a-140">[Mining Structures &#40;Analysis Services - Data Mining&#41;](mining-structures-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="59f1a-141">[挖掘模型 &#40;Analysis Services 数据挖掘&#41;](mining-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="59f1a-141">[Mining Models &#40;Analysis Services - Data Mining&#41;](mining-models-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="59f1a-142">逻辑体系结构（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="59f1a-142">Logical Architecture &#40;Analysis Services - Data Mining&#41;</span></span>](logical-architecture-analysis-services-data-mining.md)  
  
  
