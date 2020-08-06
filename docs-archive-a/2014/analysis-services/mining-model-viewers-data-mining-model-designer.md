---
title: 挖掘模型查看器 (数据挖掘模型设计器) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.viewers.f1
ms.assetid: 4ba391d5-c97b-4848-ba7c-7d096fa4b7dd
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4cc1c9d72a08ef49ed2f4f466953d2ba61394178
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693134"
---
# <a name="mining-model-viewers-data-mining-model-designer"></a><span data-ttu-id="d4e1a-102">挖掘模型查看器（数据挖掘模型设计器）</span><span class="sxs-lookup"><span data-stu-id="d4e1a-102">Mining Model Viewers (Data Mining Model Designer)</span></span>
  <span data-ttu-id="d4e1a-103">可以使用 **“挖掘模型查看器”** 选项卡浏览挖掘结构包含的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="d4e1a-103">Use the **Mining Model Viewer** tab to explore the mining models that a mining structure contains.</span></span>

 <span data-ttu-id="d4e1a-104">首先选择挖掘模型，然后选择查看器。</span><span class="sxs-lookup"><span data-stu-id="d4e1a-104">First you select the mining model and then you select a viewer.</span></span> <span data-ttu-id="d4e1a-105">每个模型始终提供两个查看器：自定义查看器，此查看器可以包括多个选项卡，以及一般查看器。</span><span class="sxs-lookup"><span data-stu-id="d4e1a-105">Each model always has two viewers available: a custom viewer, which can include multiple tabs, and the generic viewer.</span></span>

 <span data-ttu-id="d4e1a-106">有关如何使用各查看器的演练，请参阅 [数据挖掘模型查看器](data-mining/data-mining-model-viewers.md)。</span><span class="sxs-lookup"><span data-stu-id="d4e1a-106">For a walkthrough of how to use each viewer, see [Data Mining Model Viewers](data-mining/data-mining-model-viewers.md).</span></span>

## <a name="common-options"></a><span data-ttu-id="d4e1a-107">常用选项</span><span class="sxs-lookup"><span data-stu-id="d4e1a-107">Common Options</span></span>
 <span data-ttu-id="d4e1a-108">**刷新查看器内容** 在查看器中重新加载挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="d4e1a-108">**Refresh viewer content** Reload the mining model in the viewer.</span></span>

 <span data-ttu-id="d4e1a-109">**挖掘模型** 选择一个包含在当前挖掘结构中的挖掘模型以进行查看。</span><span class="sxs-lookup"><span data-stu-id="d4e1a-109">**Mining Model** Choose a mining model to view that is contained in the current mining structure.</span></span> <span data-ttu-id="d4e1a-110">挖掘模型将首先在其关联的自定义查看器中打开。</span><span class="sxs-lookup"><span data-stu-id="d4e1a-110">The mining model will first open in its associated custom viewer.</span></span>

 <span data-ttu-id="d4e1a-111">**查看器** 选择用于浏览所选挖掘模型的查看器。</span><span class="sxs-lookup"><span data-stu-id="d4e1a-111">**Viewer** Choose a viewer to use to explore the selected mining model.</span></span> <span data-ttu-id="d4e1a-112">此列表包括 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 为每个挖掘模型提供的查看器、 [!INCLUDE[msCoName](../includes/msconame-md.md)] 挖掘内容查看器以及所有插件查看器。</span><span class="sxs-lookup"><span data-stu-id="d4e1a-112">This list includes the viewers that [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] provides for each mining model, the [!INCLUDE[msCoName](../includes/msconame-md.md)] Mining Content Viewer, and any plug-in viewers.</span></span>

 <span data-ttu-id="d4e1a-113">下列关系图显示相同模型的自定义查看器和一般查看器。</span><span class="sxs-lookup"><span data-stu-id="d4e1a-113">The following diagram shows a custom viewer and the generic viewer for the same model.</span></span>

-   <span data-ttu-id="d4e1a-114">此关系图的上半部分显示基于 Microsoft 时序算法的挖掘模型的查看器。</span><span class="sxs-lookup"><span data-stu-id="d4e1a-114">The upper diagram shows the viewer for a mining model based on the Microsoft Time Series algorithm.</span></span> <span data-ttu-id="d4e1a-115">此特定自定义查看器自动创建时序图形，并提供五个预测。</span><span class="sxs-lookup"><span data-stu-id="d4e1a-115">This particular custom viewer automatically creates a graph of the time series and provides five predictions.</span></span>

-   <span data-ttu-id="d4e1a-116">此关系图的下半部分显示使用 **“Microsoft 一般内容树查看器”** 显示的相同模型。</span><span class="sxs-lookup"><span data-stu-id="d4e1a-116">The lower diagram shows the same model displayed using the **Microsoft Generic Content Tree Viewer**.</span></span> <span data-ttu-id="d4e1a-117">此查看器根据标准化架构显示挖掘模型的内容。</span><span class="sxs-lookup"><span data-stu-id="d4e1a-117">This viewer presents the contents of the mining model according to a standardized schema.</span></span> <span data-ttu-id="d4e1a-118">有关详细信息，请参阅 [Microsoft 一般内容树查看器（数据挖掘）](microsoft-generic-content-tree-viewer-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="d4e1a-118">For more information, see [Microsoft Generic Content Tree Viewer &#40;Data Mining&#41;](microsoft-generic-content-tree-viewer-data-mining.md).</span></span>

 <span data-ttu-id="d4e1a-119">![挖掘模型设计器概述](media/generic-mining-model-tab1.gif "挖掘模型设计器概述")</span><span class="sxs-lookup"><span data-stu-id="d4e1a-119">![Overview of mining model designer](media/generic-mining-model-tab1.gif "Overview of mining model designer")</span></span>

## <a name="viewers-and-their-components"></a><span data-ttu-id="d4e1a-120">各种查看器及其组件</span><span class="sxs-lookup"><span data-stu-id="d4e1a-120">Viewers and Their Components</span></span>
 <span data-ttu-id="d4e1a-121">根据您选择的模型以及用于创建所选数据挖掘模型的算法，您将看到不同的自定义查看器。</span><span class="sxs-lookup"><span data-stu-id="d4e1a-121">Depending on the model that you select, you will see a different custom viewer, tailored to the algorithm that you used to create the selected data mining model.</span></span> <span data-ttu-id="d4e1a-122">每个自定义查看器包含多种工具和对话框，有助于您浏览统计信息和模型中的模式。</span><span class="sxs-lookup"><span data-stu-id="d4e1a-122">Each custom viewer has a variety of tools and dialog boxes for helping you explore the statistics and patterns in the model.</span></span>

 <span data-ttu-id="d4e1a-123">下面的列表介绍各自定义查看器中的选项。</span><span class="sxs-lookup"><span data-stu-id="d4e1a-123">The following list describes the options in each of the custom viewers.</span></span>

### <a name="microsoft-association-rules-algorithm"></a><span data-ttu-id="d4e1a-124">Microsoft 关联规则算法</span><span class="sxs-lookup"><span data-stu-id="d4e1a-124">Microsoft Association Rules Algorithm</span></span>

-   [<span data-ttu-id="d4e1a-125">使用 Microsoft 关联规则查看器浏览模型</span><span class="sxs-lookup"><span data-stu-id="d4e1a-125">Browse a Model Using the Microsoft Association Rules Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-association-rules-viewer.md)

    -   [<span data-ttu-id="d4e1a-126">挖掘模型查看器 &#40;项集选项卡&#41;</span><span class="sxs-lookup"><span data-stu-id="d4e1a-126">Itemsets Tab &#40;Mining Model Viewer&#41;</span></span>](itemsets-tab-mining-model-viewer.md)

    -   [<span data-ttu-id="d4e1a-127">挖掘模型查看器 &#40;的 "规则" 选项卡&#41;</span><span class="sxs-lookup"><span data-stu-id="d4e1a-127">Rules Tab &#40;Mining Model Viewer&#41;</span></span>](rules-tab-mining-model-viewer.md)

    -   [<span data-ttu-id="d4e1a-128">挖掘模型查看器 &#40;的 "依赖关系网络" 选项卡&#41;</span><span class="sxs-lookup"><span data-stu-id="d4e1a-128">Dependency Network Tab &#40;Mining Model Viewer&#41;</span></span>](dependency-network-tab-mining-model-viewer.md)

### <a name="microsoft-clustering-algorithm"></a><span data-ttu-id="d4e1a-129">Microsoft Clustering Algorithm</span><span class="sxs-lookup"><span data-stu-id="d4e1a-129">Microsoft Clustering Algorithm</span></span>

-   [<span data-ttu-id="d4e1a-130">使用 Microsoft 分类查看器浏览模型</span><span class="sxs-lookup"><span data-stu-id="d4e1a-130">Browse a Model Using the Microsoft Cluster Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)

    -   [<span data-ttu-id="d4e1a-131">&#40;挖掘模型查看器的 "分类关系图" 选项卡&#41;</span><span class="sxs-lookup"><span data-stu-id="d4e1a-131">Cluster Diagram Tab &#40;Mining Model Viewer&#41;</span></span>](cluster-diagram-tab-mining-model-viewer.md)

    -   [<span data-ttu-id="d4e1a-132">挖掘模型查看器 &#40;的 "分类配置文件" 选项卡&#41;</span><span class="sxs-lookup"><span data-stu-id="d4e1a-132">Cluster Profiles Tab &#40;Mining Model Viewer&#41;</span></span>](cluster-profiles-tab-mining-model-viewer.md)

    -   [<span data-ttu-id="d4e1a-133">&#40;挖掘模型查看器的 "分类特征" 选项卡&#41;</span><span class="sxs-lookup"><span data-stu-id="d4e1a-133">Cluster Characteristics Tab &#40;Mining Model Viewer&#41;</span></span>](cluster-characteristics-tab-mining-model-viewer.md)

    -   [<span data-ttu-id="d4e1a-134">&#40;挖掘模型查看器的 "分类对比" 选项卡&#41;</span><span class="sxs-lookup"><span data-stu-id="d4e1a-134">Cluster Discrimination Tab &#40;Mining Model Viewer&#41;</span></span>](cluster-discrimination-tab-mining-model-viewer.md)

    -   [<span data-ttu-id="d4e1a-135">&#40;挖掘模型查看器的 "挖掘图例" 对话框&#41;</span><span class="sxs-lookup"><span data-stu-id="d4e1a-135">Mining Legend Dialog Box &#40;Mining Model Viewer&#41;</span></span>](mining-legend-dialog-box-mining-model-viewer.md)

### <a name="microsoft-decision-tree-algorithm"></a><span data-ttu-id="d4e1a-136">Microsoft 决策树算法</span><span class="sxs-lookup"><span data-stu-id="d4e1a-136">Microsoft Decision Tree Algorithm</span></span>

-   [<span data-ttu-id="d4e1a-137">使用 Microsoft 树查看器浏览模型</span><span class="sxs-lookup"><span data-stu-id="d4e1a-137">Browse a Model Using the Microsoft Tree Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-tree-viewer.md)

    -   [<span data-ttu-id="d4e1a-138">挖掘模型查看器 &#40;的决策树选项卡&#41;</span><span class="sxs-lookup"><span data-stu-id="d4e1a-138">Decision Tree Tab &#40;Mining Model Viewer&#41;</span></span>](decision-tree-tab-mining-model-viewer.md)

    -   [<span data-ttu-id="d4e1a-139">挖掘模型查看器 &#40;的 "依赖关系网络" 选项卡&#41;</span><span class="sxs-lookup"><span data-stu-id="d4e1a-139">Dependency Network Tab &#40;Mining Model Viewer&#41;</span></span>](dependency-network-tab-mining-model-viewer.md)

    -   [<span data-ttu-id="d4e1a-140">&#40;挖掘模型查看器的 "挖掘图例" 对话框&#41;</span><span class="sxs-lookup"><span data-stu-id="d4e1a-140">Mining Legend Dialog Box &#40;Mining Model Viewer&#41;</span></span>](mining-legend-dialog-box-mining-model-viewer.md)

### <a name="microsoft-linear-regression-algorithm"></a><span data-ttu-id="d4e1a-141">Microsoft 线性回归算法</span><span class="sxs-lookup"><span data-stu-id="d4e1a-141">Microsoft Linear Regression Algorithm</span></span>

-   [<span data-ttu-id="d4e1a-142">使用 Microsoft 神经网络查看器浏览模型</span><span class="sxs-lookup"><span data-stu-id="d4e1a-142">Browse a Model Using the Microsoft Neural Network Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-neural-network-viewer.md)

    -   [<span data-ttu-id="d4e1a-143">挖掘模型查看器 &#40;的决策树选项卡&#41;</span><span class="sxs-lookup"><span data-stu-id="d4e1a-143">Decision Tree Tab &#40;Mining Model Viewer&#41;</span></span>](decision-tree-tab-mining-model-viewer.md)

    -   [<span data-ttu-id="d4e1a-144">挖掘模型查看器 &#40;的 "依赖关系网络" 选项卡&#41;</span><span class="sxs-lookup"><span data-stu-id="d4e1a-144">Dependency Network Tab &#40;Mining Model Viewer&#41;</span></span>](dependency-network-tab-mining-model-viewer.md)

    -   [<span data-ttu-id="d4e1a-145">&#40;挖掘模型查看器的 "挖掘图例" 对话框&#41;</span><span class="sxs-lookup"><span data-stu-id="d4e1a-145">Mining Legend Dialog Box &#40;Mining Model Viewer&#41;</span></span>](mining-legend-dialog-box-mining-model-viewer.md)

### <a name="microsoft-logistic-regression-algorithm"></a><span data-ttu-id="d4e1a-146">Microsoft 逻辑回归算法</span><span class="sxs-lookup"><span data-stu-id="d4e1a-146">Microsoft Logistic Regression Algorithm</span></span>

-   [<span data-ttu-id="d4e1a-147">使用 Microsoft 神经网络查看器浏览模型</span><span class="sxs-lookup"><span data-stu-id="d4e1a-147">Browse a Model Using the Microsoft Neural Network Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-neural-network-viewer.md)

### <a name="microsoft-nave-bayes-algorithm"></a><span data-ttu-id="d4e1a-148">Microsoft Naive Bayes 算法</span><span class="sxs-lookup"><span data-stu-id="d4e1a-148">Microsoft Naïve Bayes Algorithm</span></span>

-   [<span data-ttu-id="d4e1a-149">使用 Microsoft Naive Bayes 查看器浏览模型</span><span class="sxs-lookup"><span data-stu-id="d4e1a-149">Browse a Model Using the Microsoft Naive Bayes Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)

    -   [<span data-ttu-id="d4e1a-150">挖掘模型查看器 &#40;的 "依赖关系网络" 选项卡&#41;</span><span class="sxs-lookup"><span data-stu-id="d4e1a-150">Dependency Network Tab &#40;Mining Model Viewer&#41;</span></span>](dependency-network-tab-mining-model-viewer.md)

    -   [<span data-ttu-id="d4e1a-151">挖掘模型查看器 &#40;"属性配置文件" 选项卡&#41;</span><span class="sxs-lookup"><span data-stu-id="d4e1a-151">Attribute Profiles Tab &#40;Mining Model Viewer&#41;</span></span>](attribute-profiles-tab-mining-model-viewer.md)

    -   [<span data-ttu-id="d4e1a-152">挖掘模型查看器 &#40;"属性特征" 选项卡&#41;</span><span class="sxs-lookup"><span data-stu-id="d4e1a-152">Attribute Characteristics Tab &#40;Mining Model Viewer&#41;</span></span>](attribute-characteristics-tab-mining-model-viewer.md)

    -   [<span data-ttu-id="d4e1a-153">挖掘模型查看器 &#40;的属性对比选项卡&#41;</span><span class="sxs-lookup"><span data-stu-id="d4e1a-153">Attribute Discrimination Tab &#40;Mining Model Viewer&#41;</span></span>](attribute-discrimination-tab-mining-model-viewer.md)

### <a name="microsoft-neural-network-algorithm"></a><span data-ttu-id="d4e1a-154">Microsoft Neural Network Algorithm</span><span class="sxs-lookup"><span data-stu-id="d4e1a-154">Microsoft Neural Network Algorithm</span></span>

-   [<span data-ttu-id="d4e1a-155">使用 Microsoft 神经网络查看器浏览模型</span><span class="sxs-lookup"><span data-stu-id="d4e1a-155">Browse a Model Using the Microsoft Neural Network Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-neural-network-viewer.md)

    -   [<span data-ttu-id="d4e1a-156">挖掘模型查看器 &#40;的 "依赖关系网络" 选项卡&#41;</span><span class="sxs-lookup"><span data-stu-id="d4e1a-156">Dependency Network Tab &#40;Mining Model Viewer&#41;</span></span>](dependency-network-tab-mining-model-viewer.md)

    -   [<span data-ttu-id="d4e1a-157">&#40;挖掘模型查看器的神经网络&#41;</span><span class="sxs-lookup"><span data-stu-id="d4e1a-157">Neural Network &#40;Mining Model Viewer&#41;</span></span>](neural-network-mining-model-viewer.md)

    -   [<span data-ttu-id="d4e1a-158">&#40;挖掘模型查看器的 "查找节点" 对话框&#41;</span><span class="sxs-lookup"><span data-stu-id="d4e1a-158">Find Node Dialog Box &#40;Mining Model Viewer&#41;</span></span>](find-node-dialog-box-mining-model-viewer.md)

### <a name="microsoft-sequence-clustering-algorithm"></a><span data-ttu-id="d4e1a-159">Microsoft 顺序分析和聚类分析算法</span><span class="sxs-lookup"><span data-stu-id="d4e1a-159">Microsoft Sequence Clustering Algorithm</span></span>

-   [<span data-ttu-id="d4e1a-160">使用 Microsoft 序列分类查看器浏览模型</span><span class="sxs-lookup"><span data-stu-id="d4e1a-160">Browse a Model Using the Microsoft Sequence Cluster Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)

    -   [<span data-ttu-id="d4e1a-161">&#40;挖掘模型查看器的顺序分析和聚类分析</span><span class="sxs-lookup"><span data-stu-id="d4e1a-161">Sequence Clustering Cluster Diagram Tab &#40;Mining Model Viewer</span></span>](sequence-clustering-cluster-diagram-tab-mining-model-viewer.md)

    -   [<span data-ttu-id="d4e1a-162">挖掘模型查看器 &#40;顺序分析群集配置文件选项卡</span><span class="sxs-lookup"><span data-stu-id="d4e1a-162">Sequence Clustering Cluster Profiles Tab &#40;Mining Model Viewer</span></span>](sequence-clustering-cluster-profiles-tab-mining-model-viewer.md)

    -   [<span data-ttu-id="d4e1a-163">&#40;挖掘模型查看器的顺序分析群集 "特性" 选项卡&#41;</span><span class="sxs-lookup"><span data-stu-id="d4e1a-163">Sequence Clustering Cluster Characteristics Tab &#40;Mining Model Viewer&#41;</span></span>](sequence-clustering-cluster-characteristics-tab-mining-model-viewer.md)

    -   [<span data-ttu-id="d4e1a-164">&#40;挖掘模型查看器的顺序分析和聚类分析&#41;</span><span class="sxs-lookup"><span data-stu-id="d4e1a-164">Sequence Clustering Cluster Discrimination Tab &#40;Mining Model Viewer&#41;</span></span>](sequence-clustering-cluster-discrimination-tab-mining-model-viewer.md)

    -   [<span data-ttu-id="d4e1a-165">&#40;挖掘模型查看器的顺序分析群集 "转换" 选项卡&#41;</span><span class="sxs-lookup"><span data-stu-id="d4e1a-165">Sequence Clustering Cluster Transition Tab &#40;Mining Model Viewer&#41;</span></span>](sequence-clustering-cluster-transition-tab-mining-model-viewer.md)

### <a name="microsoft-time-series-algorithm"></a><span data-ttu-id="d4e1a-166">Microsoft 时序算法</span><span class="sxs-lookup"><span data-stu-id="d4e1a-166">Microsoft Time Series Algorithm</span></span>

-   [<span data-ttu-id="d4e1a-167">使用 Microsoft 时序查看器浏览模型</span><span class="sxs-lookup"><span data-stu-id="d4e1a-167">Browse a Model Using the Microsoft Time Series Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-time-series-viewer.md)

    -   [<span data-ttu-id="d4e1a-168">挖掘模型查看器 &#40;模型选项卡&#41;</span><span class="sxs-lookup"><span data-stu-id="d4e1a-168">Model Tab &#40;Mining Model Viewers&#41;</span></span>](model-tab-mining-model-viewers.md)

    -   [<span data-ttu-id="d4e1a-169">挖掘模型查看器 &#40;的图表选项卡&#41;</span><span class="sxs-lookup"><span data-stu-id="d4e1a-169">Chart Tab &#40;Mining Model Viewers&#41;</span></span>](chart-tab-mining-model-viewers.md)

    -   [<span data-ttu-id="d4e1a-170">&#40;挖掘模型查看器的 "挖掘图例" 对话框&#41;</span><span class="sxs-lookup"><span data-stu-id="d4e1a-170">Mining Legend Dialog Box &#40;Mining Model Viewer&#41;</span></span>](mining-legend-dialog-box-mining-model-viewer.md)

## <a name="see-also"></a><span data-ttu-id="d4e1a-171">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d4e1a-171">See Also</span></span>
 <span data-ttu-id="d4e1a-172">[挖掘模型视图 &#40;数据挖掘模型设计器&#41;](mining-models-view-data-mining-model-designer.md) [挖掘结构视图 &#40;数据挖掘模型设计器&#41;](mining-structure-view-data-mining-model-designer.md) [挖掘准确性图表设计器 &#40;数据挖掘&#41;](mining-accuracy-chart-designer-data-mining.md) [预测查询生成器 &#40;数据挖掘&#41;](prediction-query-builder-data-mining.md)</span><span class="sxs-lookup"><span data-stu-id="d4e1a-172">[Mining Models View &#40;Data Mining Model Designer&#41;](mining-models-view-data-mining-model-designer.md) [Mining Structure View &#40;Data Mining Model Designer&#41;](mining-structure-view-data-mining-model-designer.md) [Mining Accuracy Chart Designer &#40;Data Mining&#41;](mining-accuracy-chart-designer-data-mining.md) [Prediction Query Builder &#40;Data Mining&#41;](prediction-query-builder-data-mining.md)</span></span>


