---
title: 数据挖掘模型查看器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- displaying data mining models
- mining models [Analysis Services], viewing
- data mining [Analysis Services], models
- viewing data mining models
- mining model content
- support [data mining]
- exploring data mining models [Analysis Services]
ms.assetid: 14c8e656-f63c-4e8a-a3af-1d580e823d28
author: minewiskan
ms.author: owend
ms.openlocfilehash: 70215231f8ed7c9c218a9c3bf15c06ce59949f69
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577920"
---
# <a name="data-mining-model-viewers"></a><span data-ttu-id="75d8e-102">数据挖掘模型查看器</span><span class="sxs-lookup"><span data-stu-id="75d8e-102">Data Mining Model Viewers</span></span>
  <span data-ttu-id="75d8e-103">在中对数据挖掘模型进行定型后 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，可以浏览该模型以查找有意义的趋势。</span><span class="sxs-lookup"><span data-stu-id="75d8e-103">After you train a data mining model in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you can explore the model to look for interesting trends.</span></span> <span data-ttu-id="75d8e-104">由于挖掘模型的结果比较复杂并且原始格式的结果难以理解，因此以可视化方式调查数据通常是了解算法在该数据内部发现的规则和关系的最简单方法。</span><span class="sxs-lookup"><span data-stu-id="75d8e-104">Because the results of mining models are complex and can be difficult to understand in a raw format, visually investigating the data is often the easiest way to understand the rules and relationships that algorithms discover within the data.</span></span>  
  
 <span data-ttu-id="75d8e-105">用于生成模型的每种算法将返回不同类型的结果。</span><span class="sxs-lookup"><span data-stu-id="75d8e-105">Each algorithm that you use to build a model returns a different type of results.</span></span> <span data-ttu-id="75d8e-106">因此， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 为每种算法提供单独的查看器。</span><span class="sxs-lookup"><span data-stu-id="75d8e-106">Therefore, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] provides a separate viewer for each algorithm.</span></span> <span data-ttu-id="75d8e-107">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中浏览挖掘模型时，该模型会使用模型的相应查看器，显示在数据挖掘设计器的 **“挖掘模型查看器”** 选项卡上。</span><span class="sxs-lookup"><span data-stu-id="75d8e-107">When you browse a mining model in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], the model is displayed on the **Mining Model Viewer** tab of Data Mining Designer, using the appropriate viewer for the model.</span></span>  
  
## <a name="how-to-use-the-model-viewers"></a><span data-ttu-id="75d8e-108">如何使用模型查看器</span><span class="sxs-lookup"><span data-stu-id="75d8e-108">How to Use the Model Viewers</span></span>  
 <span data-ttu-id="75d8e-109">首先选择挖掘模型，然后选择查看器。</span><span class="sxs-lookup"><span data-stu-id="75d8e-109">First you select the mining model and then you select a viewer.</span></span> <span data-ttu-id="75d8e-110">每个模型始终提供两个查看器：自定义查看器，此查看器可以包括多个选项卡，以及一般查看器。</span><span class="sxs-lookup"><span data-stu-id="75d8e-110">Each model always has two viewers available: a custom viewer, which can include multiple tabs, and the generic viewer.</span></span>  
  
 <span data-ttu-id="75d8e-111">您将看到多种不同的模型浏览选项，具体取决于您选择的模型类型。</span><span class="sxs-lookup"><span data-stu-id="75d8e-111">Depending on the type of the model that you selected, you will see very different options for exploring the model.</span></span> <span data-ttu-id="75d8e-112">根据用于创建所选数据挖掘模型的算法，定制与每个模型类型关联的自定义查看器。</span><span class="sxs-lookup"><span data-stu-id="75d8e-112">The custom viewers associated with each model type are tailored to the algorithm that you used to create the selected data mining model.</span></span> <span data-ttu-id="75d8e-113">每个自定义查看器包含多种工具和对话框，有助于您浏览统计信息和模型中的模式、查看图表，或者以交互方式使用概率阈值或根据名称筛选项。</span><span class="sxs-lookup"><span data-stu-id="75d8e-113">Each custom viewer has a variety of tools and dialog boxes for helping you explore the statistics and patterns in the model, view charts, or interactively work with probability thresholds or filter out items by name.</span></span>  
  
 <span data-ttu-id="75d8e-114">下列关系图说明了为相同模型选择自定义查看器和一般查看器的区别。</span><span class="sxs-lookup"><span data-stu-id="75d8e-114">The following diagram illustrates the difference when you choose a custom viewer and the generic viewer for the same model.</span></span>  
  
1.  <span data-ttu-id="75d8e-115">首先，当您选择一个基于 Microsoft 时序算法的挖掘模型后，将看到所显示的自定义查看器。</span><span class="sxs-lookup"><span data-stu-id="75d8e-115">First, you see the custom viewer that is displayed when you select a mining model based on the Microsoft Time Series algorithm.</span></span>  
  
     <span data-ttu-id="75d8e-116">此特定自定义查看器自动创建时序图形，并提供五个预测。</span><span class="sxs-lookup"><span data-stu-id="75d8e-116">This particular custom viewer automatically creates a graph of the time series and provides five predictions.</span></span>  
  
2.  <span data-ttu-id="75d8e-117">接下来，您可看到使用 **“Microsoft 一般内容树查看器”** 显示的相同模型。</span><span class="sxs-lookup"><span data-stu-id="75d8e-117">Next, you see the same model, displayed using the **Microsoft Generic Content Tree Viewer**.</span></span>  
  
     <span data-ttu-id="75d8e-118">在左图中，一般查看器显示模型中节点的列表。</span><span class="sxs-lookup"><span data-stu-id="75d8e-118">On the left, the generic viewer displays a list of the nodes in the model.</span></span> <span data-ttu-id="75d8e-119">您可以单击一个节点在右侧窗格中查看其内容。</span><span class="sxs-lookup"><span data-stu-id="75d8e-119">You can click a node to view its contents in the right-hand pane.</span></span>  
  
 <span data-ttu-id="75d8e-120">![挖掘模型设计器概述](../media/generic-mining-model-tab1.gif "挖掘模型设计器概述")</span><span class="sxs-lookup"><span data-stu-id="75d8e-120">![Overview of mining model designer](../media/generic-mining-model-tab1.gif "Overview of mining model designer")</span></span>  
  
## <a name="more-about-the-microsoft-generic-content-tree-viewer"></a><span data-ttu-id="75d8e-121">有关 Microsoft 一般内容树查看器的详细信息</span><span class="sxs-lookup"><span data-stu-id="75d8e-121">More about the Microsoft Generic Content Tree Viewer</span></span>  
 <span data-ttu-id="75d8e-122">也可使用 [Microsoft 一般内容树查看器（数据挖掘）](../microsoft-generic-content-tree-viewer-data-mining.md)查看每个模型。</span><span class="sxs-lookup"><span data-stu-id="75d8e-122">Each model can also be viewed using the [Microsoft Generic Content Tree Viewer &#40;Data Mining&#41;](../microsoft-generic-content-tree-viewer-data-mining.md).</span></span> <span data-ttu-id="75d8e-123">此查看器根据标准的 HTML 表格格式显示挖掘模式的内容。</span><span class="sxs-lookup"><span data-stu-id="75d8e-123">This viewer presents the contents of the mining model according to a standard HTML table format.</span></span> <span data-ttu-id="75d8e-124">但是，节点的排列和每个节点的内容将会因生成结果所使用的算法而差别很大。</span><span class="sxs-lookup"><span data-stu-id="75d8e-124">However, the arrangement of the nodes and the content of each node will differ greatly depending on the algorithm used to generate the results.</span></span>  
  
 <span data-ttu-id="75d8e-125">自定义查看器是专为浏览和了解模型而设计的，但是如果您已了解模型并希望从特定节点提取统计信息或规则，则一般查看器的作用更大。</span><span class="sxs-lookup"><span data-stu-id="75d8e-125">Whereas the custom viewers are designed for exploring and understanding the model, the generic viewer is more useful when you already understand the model and want to extract statistics or rules from a specific node.</span></span> <span data-ttu-id="75d8e-126">例如，当您想要查看有关在分析期间 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 捕获的模式和统计的详细信息（如节点的概率或回归公式）时，应使用一般查看器。</span><span class="sxs-lookup"><span data-stu-id="75d8e-126">For example, you would use the generic viewer when you want to view detailed information about the patterns and statistics that [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] captured during analysis, such as the probability of a node, or a regression formula.</span></span>  
  
 <span data-ttu-id="75d8e-127">还可以使用 DMX 编写“内容查询” \*\* ，以获取从查看器中显示的所有信息。</span><span class="sxs-lookup"><span data-stu-id="75d8e-127">You can also write *content queries* using DMX to get all of the information that is presented in this viewer.</span></span> <span data-ttu-id="75d8e-128">有关详细信息，请参阅 [内容查询（数据挖掘）](content-queries-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="75d8e-128">For more information, see [Content Queries &#40;Data Mining&#41;](content-queries-data-mining.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="75d8e-129">本节内容</span><span class="sxs-lookup"><span data-stu-id="75d8e-129">In This Section</span></span>  
 <span data-ttu-id="75d8e-130">下面的主题详细描述了各个查看器以及如何解释这些查看器中的信息。</span><span class="sxs-lookup"><span data-stu-id="75d8e-130">The following topics describe in more detail each of the viewers, and how to interpret the information in them.</span></span>  
  
 [<span data-ttu-id="75d8e-131">使用 Microsoft 树查看器浏览模型</span><span class="sxs-lookup"><span data-stu-id="75d8e-131">Browse a Model Using the Microsoft Tree Viewer</span></span>](browse-a-model-using-the-microsoft-tree-viewer.md)  
 <span data-ttu-id="75d8e-132">描述 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 树查看器。</span><span class="sxs-lookup"><span data-stu-id="75d8e-132">Describes the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Tree Viewer.</span></span> <span data-ttu-id="75d8e-133">此查看器显示用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 决策树算法和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 线性回归算法生成的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="75d8e-133">This viewer displays mining models that are built with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Linear Regression algorithm.</span></span>  
  
 [<span data-ttu-id="75d8e-134">使用 Microsoft 分类查看器浏览模型</span><span class="sxs-lookup"><span data-stu-id="75d8e-134">Browse a Model Using the Microsoft Cluster Viewer</span></span>](browse-a-model-using-the-microsoft-cluster-viewer.md)  
 <span data-ttu-id="75d8e-135">介绍 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 分类查看器。</span><span class="sxs-lookup"><span data-stu-id="75d8e-135">Describes the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Cluster Viewer.</span></span> <span data-ttu-id="75d8e-136">该查看器显示使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 聚类分析算法生成的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="75d8e-136">This viewer displays mining models that are built with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Clustering algorithm.</span></span>  
  
 [<span data-ttu-id="75d8e-137">使用 Microsoft 时序查看器浏览模型</span><span class="sxs-lookup"><span data-stu-id="75d8e-137">Browse a Model Using the Microsoft Time Series Viewer</span></span>](browse-a-model-using-the-microsoft-time-series-viewer.md)  
 <span data-ttu-id="75d8e-138">介绍 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 时序查看器。</span><span class="sxs-lookup"><span data-stu-id="75d8e-138">Describes the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Time Series Viewer.</span></span> <span data-ttu-id="75d8e-139">该查看器显示使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 时序算法生成的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="75d8e-139">This viewer displays mining models that are built with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Time Series algorithm.</span></span>  
  
 [<span data-ttu-id="75d8e-140">使用 Microsoft Naive Bayes 查看器浏览模型</span><span class="sxs-lookup"><span data-stu-id="75d8e-140">Browse a Model Using the Microsoft Naive Bayes Viewer</span></span>](browse-a-model-using-the-microsoft-naive-bayes-viewer.md)  
 <span data-ttu-id="75d8e-141">介绍 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes 查看器。</span><span class="sxs-lookup"><span data-stu-id="75d8e-141">Describes the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes viewer.</span></span> <span data-ttu-id="75d8e-142">该查看器显示使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes 算法生成的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="75d8e-142">This viewer displays mining models that are built with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm.</span></span>  
  
 [<span data-ttu-id="75d8e-143">使用 Microsoft 序列分类查看器浏览模型</span><span class="sxs-lookup"><span data-stu-id="75d8e-143">Browse a Model Using the Microsoft Sequence Cluster Viewer</span></span>](browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)  
 <span data-ttu-id="75d8e-144">介绍 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 序列分类查看器。</span><span class="sxs-lookup"><span data-stu-id="75d8e-144">Describes the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Cluster Viewer.</span></span> <span data-ttu-id="75d8e-145">该查看器显示使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 顺序分析和聚类分析算法生成的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="75d8e-145">This viewer displays mining models that are built with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering algorithm.</span></span>  
  
 [<span data-ttu-id="75d8e-146">使用 Microsoft 关联规则查看器浏览模型</span><span class="sxs-lookup"><span data-stu-id="75d8e-146">Browse a Model Using the Microsoft Association Rules Viewer</span></span>](browse-a-model-using-the-microsoft-association-rules-viewer.md)  
 <span data-ttu-id="75d8e-147">介绍 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 关联规则查看器。</span><span class="sxs-lookup"><span data-stu-id="75d8e-147">Describes the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules Viewer.</span></span> <span data-ttu-id="75d8e-148">该查看器显示使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 关联算法生成的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="75d8e-148">This viewer displays mining models that are built with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association algorithm.</span></span>  
  
 [<span data-ttu-id="75d8e-149">使用 Microsoft 神经网络查看器浏览模型</span><span class="sxs-lookup"><span data-stu-id="75d8e-149">Browse a Model Using the Microsoft Neural Network Viewer</span></span>](browse-a-model-using-the-microsoft-neural-network-viewer.md)  
 <span data-ttu-id="75d8e-150">描述 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 神经网络查看器。</span><span class="sxs-lookup"><span data-stu-id="75d8e-150">Describes the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network Viewer.</span></span> <span data-ttu-id="75d8e-151">此查看器显示用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 神经网络算法生成的挖掘模型，其中包括使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 逻辑回归算法的模型。</span><span class="sxs-lookup"><span data-stu-id="75d8e-151">This viewer displays mining models that are built with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm, including models that use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Logistic Regression algorithm.</span></span>  
  
 [<span data-ttu-id="75d8e-152">使用 Microsoft 一般内容树查看器浏览模型</span><span class="sxs-lookup"><span data-stu-id="75d8e-152">Browse a Model Using the Microsoft Generic Content Tree Viewer</span></span>](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)  
 <span data-ttu-id="75d8e-153">介绍所有数据挖掘模型的一般查看器中提供的详细信息，并举例说明如何解释每个算法的信息。</span><span class="sxs-lookup"><span data-stu-id="75d8e-153">Describes the detailed information that is available in the generic viewer for all data mining models and provides examples of how to interpret the information for each algorithm.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75d8e-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="75d8e-154">See Also</span></span>  
 <span data-ttu-id="75d8e-155">[数据挖掘算法 &#40;Analysis Services 数据挖掘&#41;](data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="75d8e-155">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="75d8e-156">Data Mining Designer</span><span class="sxs-lookup"><span data-stu-id="75d8e-156">Data Mining Designer</span></span>](data-mining-designer.md)  
  
  
