---
title: " (挖掘模型查看器) 的顺序分析群集 \"转换\" 选项卡 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.sequenceclustering.transition.f1
ms.assetid: 40aef457-d69f-4905-a2d3-924c37bd3d97
author: minewiskan
ms.author: owend
ms.openlocfilehash: f777e48c2f69911e61420fd3b7a0a137a04e7c2f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694596"
---
# <a name="sequence-clustering-cluster-transition-tab-mining-model-viewer"></a><span data-ttu-id="662c4-102">顺序分析和聚类分析的“分类转换”选项卡（挖掘模型查看器）</span><span class="sxs-lookup"><span data-stu-id="662c4-102">Sequence Clustering Cluster Transition Tab (Mining Model Viewer)</span></span>
  <span data-ttu-id="662c4-103">可以使用“Microsoft 顺序分析和聚类分析查看器”\*\*\*\* 中的“状态转换”\*\*\*\* 选项卡，更仔细地查看选定分类中的各个属性-值对或状态之间的转换。</span><span class="sxs-lookup"><span data-stu-id="662c4-103">The **State Transitions** tab in the **Microsoft Sequence Clustering Viewer** provides a closer look at the transitions between attribute-value pairs, or states, in the selected cluster.</span></span>  
  
 <span data-ttu-id="662c4-104">使用此顺序分析和聚类分析模型视图可查看模式。</span><span class="sxs-lookup"><span data-stu-id="662c4-104">Use this view of a sequence clustering model to view patterns.</span></span> <span data-ttu-id="662c4-105">在关系图中，链接表示转换的概率，节点则表示序列状态。</span><span class="sxs-lookup"><span data-stu-id="662c4-105">In the diagram, a link represents the probability of a transition, and a node represents a sequence state.</span></span>  
  
 <span data-ttu-id="662c4-106">\*\*有关详细信息，请参阅 \*\* [Microsoft 顺序分析和聚类分析算法](data-mining/microsoft-sequence-clustering-algorithm.md)和[使用 Microsoft 序列分类查看器浏览模型](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="662c4-106">**For More Information:** [Microsoft Sequence Clustering Algorithm](data-mining/microsoft-sequence-clustering-algorithm.md), [Browse a Model Using the Microsoft Sequence Cluster Viewer](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="662c4-107">选项</span><span class="sxs-lookup"><span data-stu-id="662c4-107">Options</span></span>  
 <span data-ttu-id="662c4-108">**刷新查看器内容**</span><span class="sxs-lookup"><span data-stu-id="662c4-108">**Refresh viewer content**</span></span>  
 <span data-ttu-id="662c4-109">在查看器中重新加载挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="662c4-109">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="662c4-110">**挖掘模型**</span><span class="sxs-lookup"><span data-stu-id="662c4-110">**Mining Model**</span></span>  
 <span data-ttu-id="662c4-111">选择一个包含在当前挖掘结构中的挖掘模型以进行查看。</span><span class="sxs-lookup"><span data-stu-id="662c4-111">Choose a mining model to view that is contained in the current mining structure.</span></span> <span data-ttu-id="662c4-112">挖掘模型将在其关联的查看器中打开。</span><span class="sxs-lookup"><span data-stu-id="662c4-112">The mining model will open in its associated viewer.</span></span>  
  
 <span data-ttu-id="662c4-113">**查看器**</span><span class="sxs-lookup"><span data-stu-id="662c4-113">**Viewer**</span></span>  
 <span data-ttu-id="662c4-114">选择用于浏览选定挖掘模型的查看器。</span><span class="sxs-lookup"><span data-stu-id="662c4-114">Choose a viewer to use in exploring the selected mining model.</span></span> <span data-ttu-id="662c4-115">您可以使用自定义查看器或 **“Microsoft 一般内容树查看器”**。</span><span class="sxs-lookup"><span data-stu-id="662c4-115">You can use the custom viewer, or the **Microsoft Generic Content Tree Viewer**.</span></span> <span data-ttu-id="662c4-116">还可以使用插件查看器（如果有）。</span><span class="sxs-lookup"><span data-stu-id="662c4-116">You can also use plug-in viewers if available.</span></span>  
  
 <span data-ttu-id="662c4-117">**放大**</span><span class="sxs-lookup"><span data-stu-id="662c4-117">**Zoom In**</span></span>  
 <span data-ttu-id="662c4-118">放大关系图以更好地查看状态。</span><span class="sxs-lookup"><span data-stu-id="662c4-118">Zoom in to the diagram, to see the states better.</span></span>  
  
 <span data-ttu-id="662c4-119">**缩小**</span><span class="sxs-lookup"><span data-stu-id="662c4-119">**Zoom Out**</span></span>  
 <span data-ttu-id="662c4-120">缩小关系图以获取分类中的状态的整体视图。</span><span class="sxs-lookup"><span data-stu-id="662c4-120">Zoom out from the diagram, to get an overall view of the states in the cluster.</span></span>  
  
 <span data-ttu-id="662c4-121">**复制图形视图**</span><span class="sxs-lookup"><span data-stu-id="662c4-121">**Copy Graph View**</span></span>  
 <span data-ttu-id="662c4-122">将关系图的可见部分复制到剪贴板。</span><span class="sxs-lookup"><span data-stu-id="662c4-122">Copy the visible section of the diagram to the clipboard.</span></span>  
  
 <span data-ttu-id="662c4-123">**复制整个图形**</span><span class="sxs-lookup"><span data-stu-id="662c4-123">**Copy Entire Graph**</span></span>  
 <span data-ttu-id="662c4-124">将完整的关系图复制到剪贴板。</span><span class="sxs-lookup"><span data-stu-id="662c4-124">Copy the complete diagram to the clipboard.</span></span>  
  
 <span data-ttu-id="662c4-125">**Cluster**</span><span class="sxs-lookup"><span data-stu-id="662c4-125">**Cluster**</span></span>  
 <span data-ttu-id="662c4-126">选择要在查看器中显示的分类。</span><span class="sxs-lookup"><span data-stu-id="662c4-126">Choose a cluster to display in the viewer.</span></span> <span data-ttu-id="662c4-127">默认情况下，“总体(全部)”\*\*\*\* 处于选中状态，这意味着整个模型中的状态和转换都包含在图形中。</span><span class="sxs-lookup"><span data-stu-id="662c4-127">By default, **Population (All)** is selected, which means that states and transitions from the entire model are included in the graph.</span></span> <span data-ttu-id="662c4-128">在选择某个特定分类时，仅显示该分类中的状态和转换。</span><span class="sxs-lookup"><span data-stu-id="662c4-128">When you choose a particular cluster, only the states and transitions that are in that cluster are displayed.</span></span>  
  
 <span data-ttu-id="662c4-129">**提示：** 可以使用 "**分类关系图**" 选项卡重命名群集。只需选择一个分类，右键单击，然后选择 "**重命名**"。</span><span class="sxs-lookup"><span data-stu-id="662c4-129">**Tip:** You can rename clusters by using the **Cluster Diagram** tab. Just select a cluster, right-click, and select **Rename**.</span></span> <span data-ttu-id="662c4-130">通过使用更具说明性的标签来对分类进行重命名，可使得在 **“状态转换”** 选项卡中比较分类变得更容易。</span><span class="sxs-lookup"><span data-stu-id="662c4-130">Renaming clusters with a more descriptive label makes it easier to compare clusters in the **State Transitions** tab.</span></span>  
  
 <span data-ttu-id="662c4-131">**显示边缘标签**</span><span class="sxs-lookup"><span data-stu-id="662c4-131">**Show Edge Labels**</span></span>  
 <span data-ttu-id="662c4-132">选择此选项可在图形的每个边缘上显示一些数字来指示转换概率。</span><span class="sxs-lookup"><span data-stu-id="662c4-132">Select this option to display numbers on each edge in the graph that denote the probability of the transition.</span></span>  
  
 <span data-ttu-id="662c4-133">**链接**</span><span class="sxs-lookup"><span data-stu-id="662c4-133">**Links**</span></span>  
 <span data-ttu-id="662c4-134">使用滑块可控制图表中显示的状态数和转换数。</span><span class="sxs-lookup"><span data-stu-id="662c4-134">Use the slider to control the number of states and transitions that are displayed in the chart.</span></span> <span data-ttu-id="662c4-135">降低滑块将只显示具有最高概率的状态和转换。</span><span class="sxs-lookup"><span data-stu-id="662c4-135">Lowering the slider shows only the states and transitions with the highest probability.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="662c4-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="662c4-136">See Also</span></span>  
 <span data-ttu-id="662c4-137">[数据挖掘算法 &#40;Analysis Services 数据挖掘&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="662c4-137">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="662c4-138">[挖掘模型查看器 &#40;数据挖掘模型设计器&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="662c4-138">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="662c4-139">数据挖掘模型查看器</span><span class="sxs-lookup"><span data-stu-id="662c4-139">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
