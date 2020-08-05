---
title: "\"分类对比\" 选项卡 (挖掘模型查看器) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.clustering.discrimination.f1
ms.assetid: ae7cfff7-ab1c-4cf5-9a91-97b21d15d85f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 35435736bcdf1b1962de6babace2def953bbfff0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579883"
---
# <a name="cluster-discrimination-tab-mining-model-viewer"></a><span data-ttu-id="6387e-102">“分类对比”选项卡（挖掘模型查看器）</span><span class="sxs-lookup"><span data-stu-id="6387e-102">Cluster Discrimination Tab (Mining Model Viewer)</span></span>
  <span data-ttu-id="6387e-103">可以使用 **“分类对比”** 选项卡，对聚类分析模型中的两个现有分类进行比较。</span><span class="sxs-lookup"><span data-stu-id="6387e-103">Use the **Cluster Discrimination** tab to compare two clusters that exist in a clustering model.</span></span> <span data-ttu-id="6387e-104">可以查看属性和值的各种组合在分类中的显示方式。</span><span class="sxs-lookup"><span data-stu-id="6387e-104">You can see how different combinations of attributes and values are represented within the clusters.</span></span>  
  
 <span data-ttu-id="6387e-105">\*\*有关详细信息，请参阅 \*\* [Microsoft 聚类分析算法](data-mining/microsoft-clustering-algorithm.md)和[使用 Microsoft 分类查看器浏览模型](data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="6387e-105">**For More Information:** [Microsoft Clustering Algorithm](data-mining/microsoft-clustering-algorithm.md), [Browse a Model Using the Microsoft Cluster Viewer](data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="6387e-106">选项</span><span class="sxs-lookup"><span data-stu-id="6387e-106">Options</span></span>  
 <span data-ttu-id="6387e-107">**刷新查看器内容**</span><span class="sxs-lookup"><span data-stu-id="6387e-107">**Refresh viewer content**</span></span>  
 <span data-ttu-id="6387e-108">在查看器中重新加载挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="6387e-108">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="6387e-109">**挖掘模型**</span><span class="sxs-lookup"><span data-stu-id="6387e-109">**Mining Model**</span></span>  
 <span data-ttu-id="6387e-110">从当前挖掘结构的挖掘模型中选择一个挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="6387e-110">Choose a mining model from those in the current mining structure.</span></span> <span data-ttu-id="6387e-111">挖掘模型将在其关联的查看器中打开。</span><span class="sxs-lookup"><span data-stu-id="6387e-111">The mining model will open in its associated viewer.</span></span>  
  
 <span data-ttu-id="6387e-112">**查看器**</span><span class="sxs-lookup"><span data-stu-id="6387e-112">**Viewer**</span></span>  
 <span data-ttu-id="6387e-113">选择用于浏览所选挖掘模型的查看器。</span><span class="sxs-lookup"><span data-stu-id="6387e-113">Choose a viewer to use to explore the selected mining model.</span></span> <span data-ttu-id="6387e-114">可以对分类模型使用自定义查看器，也可以使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] 挖掘内容查看器。</span><span class="sxs-lookup"><span data-stu-id="6387e-114">You can use the custom viewer for clustering models, or the [!INCLUDE[msCoName](../includes/msconame-md.md)] Mining Content Viewer.</span></span> <span data-ttu-id="6387e-115">还可以使用插件查看器（如果有）。</span><span class="sxs-lookup"><span data-stu-id="6387e-115">You can also use plug-in viewers if available.</span></span>  
  
 <span data-ttu-id="6387e-116">**分类 1**</span><span class="sxs-lookup"><span data-stu-id="6387e-116">**Cluster 1**</span></span>  
 <span data-ttu-id="6387e-117">选择一个分类，以便将其与其他分类进行比较。</span><span class="sxs-lookup"><span data-stu-id="6387e-117">Select a cluster, so that you can compare it to another cluster.</span></span>  
  
 <span data-ttu-id="6387e-118">**Cluster 2**</span><span class="sxs-lookup"><span data-stu-id="6387e-118">**Cluster 2**</span></span>  
 <span data-ttu-id="6387e-119">从挖掘模型的群集列表中选择第二个群集，与“群集 1”\*\*\*\* 进行比较。</span><span class="sxs-lookup"><span data-stu-id="6387e-119">Select a second cluster from the list of clusters in the mining model, to compare to **Cluster 1**.</span></span> <span data-ttu-id="6387e-120">还可以将分类与其补数进行比较，表示模型中的所有事例（选定分类中的事例除外）。</span><span class="sxs-lookup"><span data-stu-id="6387e-120">You can also compare a cluster to its complement, meaning all cases in the model except those in the selected cluster.</span></span>  
  
 <span data-ttu-id="6387e-121">**和的歧视分数 \<cluster 1>\<cluster 2>**</span><span class="sxs-lookup"><span data-stu-id="6387e-121">**Discrimination scores for \<cluster 1> and \<cluster 2>**</span></span>  
 <span data-ttu-id="6387e-122">图形中的列提供有关每个属性-值与两个选定分类之间的关系的信息。</span><span class="sxs-lookup"><span data-stu-id="6387e-122">The columns in the graph provide information about how each attribute-value pair is related to the two selected clusters.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6387e-123">**变量**</span><span class="sxs-lookup"><span data-stu-id="6387e-123">**Variables**</span></span>|<span data-ttu-id="6387e-124">挖掘模型中的属性。</span><span class="sxs-lookup"><span data-stu-id="6387e-124">An attribute in the mining model.</span></span>|  
|<span data-ttu-id="6387e-125">**值**</span><span class="sxs-lookup"><span data-stu-id="6387e-125">**Values**</span></span>|<span data-ttu-id="6387e-126">在 **“变量”** 中选择的属性的值。</span><span class="sxs-lookup"><span data-stu-id="6387e-126">A value of the attribute selected in **Variables**.</span></span>|  
|<span data-ttu-id="6387e-127">**有利\<cluster 1>**</span><span class="sxs-lookup"><span data-stu-id="6387e-127">**Favors \<cluster 1>**</span></span>|<span data-ttu-id="6387e-128">左侧的条形图表示所选属性-值对代表“群集 1”\*\*\*\* 中的所选群集的概率。</span><span class="sxs-lookup"><span data-stu-id="6387e-128">The bar graph on the left represents the probability that the selected attribute-value pair is representative of the cluster selected in **Cluster 1**.</span></span> <span data-ttu-id="6387e-129">可以将鼠标指针悬停在条形上方来查看以百分比表示的值。</span><span class="sxs-lookup"><span data-stu-id="6387e-129">You can pause the mouse over the bar to see the value, represented as a percentage.</span></span> <span data-ttu-id="6387e-130">请注意，即使值为零，它也不意味着群集中一定缺少属性值，只是分布在一个群集上具有更好的效果。</span><span class="sxs-lookup"><span data-stu-id="6387e-130">Note that even if the value is zero, it doesn't mean the attribute-value is necessarily missing from the cluster, just that the distribution strongly favors one cluster over the other.</span></span>|  
|<span data-ttu-id="6387e-131">**有利\<cluster 2>**</span><span class="sxs-lookup"><span data-stu-id="6387e-131">**Favors \<cluster 2>**</span></span>|<span data-ttu-id="6387e-132">右侧的条形图表示所选属性-值对代表“群集 2”\*\*\*\* 中的所选群集的概率。</span><span class="sxs-lookup"><span data-stu-id="6387e-132">The bar graph on the right represents the probability that the selected attribute-value pair is representative of the cluster selected in **Cluster 2**.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6387e-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6387e-133">See Also</span></span>  
 <span data-ttu-id="6387e-134">[数据挖掘算法 &#40;Analysis Services 数据挖掘&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="6387e-134">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="6387e-135">[挖掘模型查看器 &#40;数据挖掘模型设计器&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="6387e-135">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="6387e-136">数据挖掘模型查看器</span><span class="sxs-lookup"><span data-stu-id="6387e-136">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
