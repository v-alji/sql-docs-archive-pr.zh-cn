---
title: " (挖掘模型查看器) 的顺序分析群集对比选项卡 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.sequenceclustering.discrimination.f1
ms.assetid: 7dd16479-2633-4f4b-83bf-cf55972a2241
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9839a6185933fd87929331558ed63c1d81c6a748
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694600"
---
# <a name="sequence-clustering-cluster-discrimination-tab-mining-model-viewer"></a><span data-ttu-id="3daf6-102">顺序分析和聚类分析的“分类对比”选项卡（挖掘模型查看器）</span><span class="sxs-lookup"><span data-stu-id="3daf6-102">Sequence Clustering Cluster Discrimination Tab (Mining Model Viewer)</span></span>
  <span data-ttu-id="3daf6-103">**“Microsoft 顺序分析和聚类分析查看器”** 中的 **“分类对比”** 选项卡将比较顺序分析和聚类分析模型中的所选分类。</span><span class="sxs-lookup"><span data-stu-id="3daf6-103">The  **Cluster Discrimination** tab in the **Microsoft Sequence Clustering Viewer** compares selected clusters from a sequence clustering model.</span></span>  
  
 <span data-ttu-id="3daf6-104">可以使用此顺序分析和聚类分析模型视图，比较两个分类并查看哪些状态和转换是不同的。</span><span class="sxs-lookup"><span data-stu-id="3daf6-104">Use this view of a sequence clustering model to compare two clusters and see which states and transitions are different.</span></span>  
  
 <span data-ttu-id="3daf6-105">\*\*有关详细信息，请参阅 \*\* [Microsoft 顺序分析和聚类分析算法](data-mining/microsoft-sequence-clustering-algorithm.md)和[使用 Microsoft 序列分类查看器浏览模型](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="3daf6-105">**For More Information:** [Microsoft Sequence Clustering Algorithm](data-mining/microsoft-sequence-clustering-algorithm.md), [Browse a Model Using the Microsoft Sequence Cluster Viewer](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="3daf6-106">选项</span><span class="sxs-lookup"><span data-stu-id="3daf6-106">Options</span></span>  
 <span data-ttu-id="3daf6-107">**刷新查看器内容**</span><span class="sxs-lookup"><span data-stu-id="3daf6-107">**Refresh viewer content**</span></span>  
 <span data-ttu-id="3daf6-108">在查看器中重新加载挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="3daf6-108">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="3daf6-109">**挖掘模型**</span><span class="sxs-lookup"><span data-stu-id="3daf6-109">**Mining Model**</span></span>  
 <span data-ttu-id="3daf6-110">选择一个包含在当前挖掘结构中的挖掘模型以进行查看。</span><span class="sxs-lookup"><span data-stu-id="3daf6-110">Choose a mining model to view that is contained in the current mining structure.</span></span> <span data-ttu-id="3daf6-111">挖掘模型将在其关联的查看器中打开。</span><span class="sxs-lookup"><span data-stu-id="3daf6-111">The mining model will open in its associated viewer.</span></span>  
  
 <span data-ttu-id="3daf6-112">**查看器**</span><span class="sxs-lookup"><span data-stu-id="3daf6-112">**Viewer**</span></span>  
 <span data-ttu-id="3daf6-113">选择用于浏览选定挖掘模型的查看器。</span><span class="sxs-lookup"><span data-stu-id="3daf6-113">Choose a viewer to use in exploring the selected mining model.</span></span> <span data-ttu-id="3daf6-114">您可以使用自定义查看器或 **“Microsoft 一般内容树查看器”**。</span><span class="sxs-lookup"><span data-stu-id="3daf6-114">You can use the custom viewer, or the **Microsoft Generic Content Tree Viewer**.</span></span> <span data-ttu-id="3daf6-115">还可以使用插件查看器（如果有）。</span><span class="sxs-lookup"><span data-stu-id="3daf6-115">You can also use plug-in viewers if available.</span></span>  
  
 <span data-ttu-id="3daf6-116">**分类 1**</span><span class="sxs-lookup"><span data-stu-id="3daf6-116">**Cluster 1**</span></span>  
 <span data-ttu-id="3daf6-117">从模型的分类中选择一个分类。</span><span class="sxs-lookup"><span data-stu-id="3daf6-117">Select a cluster from those in the model.</span></span>  
  
 <span data-ttu-id="3daf6-118">**Cluster 2**</span><span class="sxs-lookup"><span data-stu-id="3daf6-118">**Cluster 2**</span></span>  
 <span data-ttu-id="3daf6-119">从挖掘模型的分类中选择第二个分类，与 **“分类 1”** 进行比较。</span><span class="sxs-lookup"><span data-stu-id="3daf6-119">Select a second cluster in the mining model, to compare to **Cluster 1**.</span></span>  
  
 <span data-ttu-id="3daf6-120">如果您不选择其他分类，则默认情况下，所选分类将会与其补数进行比较，这表示模型中不属于分类 1 的所有事例。</span><span class="sxs-lookup"><span data-stu-id="3daf6-120">If you do not select another cluster, by default the selected cluster is compared to its complement, meaning all cases in the model that are not in Cluster 1.</span></span>  
  
 <span data-ttu-id="3daf6-121">**和的歧视分数 \<cluster 1>\<cluster 2>**</span><span class="sxs-lookup"><span data-stu-id="3daf6-121">**Discrimination scores for \<cluster 1> and \<cluster 2>**</span></span>  
 <span data-ttu-id="3daf6-122">此图表提供所选分类的详细比较。</span><span class="sxs-lookup"><span data-stu-id="3daf6-122">This chart provides the detailed comparison of the clusters that you selected.</span></span> <span data-ttu-id="3daf6-123">一般情况下，聚类分析模型很少以独占方式为单个分类分配状态或值。</span><span class="sxs-lookup"><span data-stu-id="3daf6-123">In general, a clustering model rarely assigns states or values exclusively to a single cluster.</span></span> <span data-ttu-id="3daf6-124">因此，查看器仅指示特定属性或状态 *倾向于* 某个特定分类。</span><span class="sxs-lookup"><span data-stu-id="3daf6-124">Therefore, the viewer indicates only that a particular attribute or state *favors* a particular cluster.</span></span>  
  
 <span data-ttu-id="3daf6-125">总体上而言，某个特定分类可能包含多个状态：例如，常见状态可能为依次购买 Water Bottle 和 Water Bottle Cage。</span><span class="sxs-lookup"><span data-stu-id="3daf6-125">Overall, a certain cluster might contain more of one state: for example, a common state might be the purchase of a Water Bottle and Water Bottle Cage in sequence.</span></span> <span data-ttu-id="3daf6-126">但是，相应的顺序可能存在于包含更重要的定义特征的其他分类中。</span><span class="sxs-lookup"><span data-stu-id="3daf6-126">However, the sequence might be present in other clusters that have more important defining characteristics.</span></span> <span data-ttu-id="3daf6-127">例如，另一个分类最主要的特点可能是事务时间非常短，并且分析表明，Water Bottle 和 Water Bottle Cage 项可能通常分组到此分类中，但并不总是这样。</span><span class="sxs-lookup"><span data-stu-id="3daf6-127">For example, another cluster might be characterized most strongly by very short transaction times, and an analysis would reveal that [Water Bottle and Waterthe items are positioned to might usually be grouped in this cluster, but not always.</span></span>  
  
|<span data-ttu-id="3daf6-128">值</span><span class="sxs-lookup"><span data-stu-id="3daf6-128">Value</span></span>|<span data-ttu-id="3daf6-129">说明</span><span class="sxs-lookup"><span data-stu-id="3daf6-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3daf6-130">**变量**</span><span class="sxs-lookup"><span data-stu-id="3daf6-130">**Variables**</span></span>|<span data-ttu-id="3daf6-131">挖掘模型中的属性。</span><span class="sxs-lookup"><span data-stu-id="3daf6-131">An attribute in the mining model.</span></span>|  
|<span data-ttu-id="3daf6-132">**值**</span><span class="sxs-lookup"><span data-stu-id="3daf6-132">**Values**</span></span>|<span data-ttu-id="3daf6-133">**“变量”** 中列出的属性的状态。</span><span class="sxs-lookup"><span data-stu-id="3daf6-133">A state of the attribute that is listed in **Variables**.</span></span>|  
|<span data-ttu-id="3daf6-134">**有利\<cluster 1>**</span><span class="sxs-lookup"><span data-stu-id="3daf6-134">**Favors \<cluster 1>**</span></span>|<span data-ttu-id="3daf6-135">包含一个阴影条，指示 **“变量”** 和 **“值”** 中列出的属性和状态倾向于 **“分类 1”** 中的所选分类的程度。</span><span class="sxs-lookup"><span data-stu-id="3daf6-135">Contains a shaded bar that indicates how strongly the attribute and the state that are listed in **Variables** and **Value** favor the cluster that is selected in **Cluster 1**.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3daf6-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3daf6-136">See Also</span></span>  
 <span data-ttu-id="3daf6-137">[数据挖掘算法 &#40;Analysis Services 数据挖掘&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="3daf6-137">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="3daf6-138">[挖掘模型查看器 &#40;数据挖掘模型设计器&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="3daf6-138">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="3daf6-139">数据挖掘模型查看器</span><span class="sxs-lookup"><span data-stu-id="3daf6-139">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
