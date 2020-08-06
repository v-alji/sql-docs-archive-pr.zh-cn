---
title: 挖掘模型查看器 (的 "依赖关系网络" 选项卡) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.dependencynetwork.f1
ms.assetid: e58ce1b7-20d6-42cb-ade5-916da8471e09
author: minewiskan
ms.author: owend
ms.openlocfilehash: 94ce82524445ffb8999c671c736087362ef0adfb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687336"
---
# <a name="dependency-network-tab-mining-model-viewer"></a><span data-ttu-id="0ce8e-102">“依赖关系网络”选项卡（挖掘模型查看器）</span><span class="sxs-lookup"><span data-stu-id="0ce8e-102">Dependency Network Tab (Mining Model Viewer)</span></span>
  <span data-ttu-id="0ce8e-103">**“依赖关系网络”** 选项卡提供挖掘模型所包含的所有属性的图形视图，并显示这些属性之间的关系。</span><span class="sxs-lookup"><span data-stu-id="0ce8e-103">The **Dependency Net** tab provides a graphical view of all attributes that the mining model contains, and shows how the attributes are related.</span></span>  
  
 <span data-ttu-id="0ce8e-104">**“依赖关系网络”**  选项卡用于多种类型的挖掘模型，包括 Naïve Bayes 模型、决策树模型和关联模型。</span><span class="sxs-lookup"><span data-stu-id="0ce8e-104">The **Dependency Net**  tab is used for several types of mining models, including Naïve Bayes models, decision tree models, and association models.</span></span> <span data-ttu-id="0ce8e-105">有关如何在这些模型的上下文中解释 **“依赖关系网络”**  选项卡的内容的详细信息，请参阅以下链接：</span><span class="sxs-lookup"><span data-stu-id="0ce8e-105">For more information about how to interpret the contents of the **Dependency Net**  tab in the context of these models, see the following links:</span></span>  
  
 [<span data-ttu-id="0ce8e-106">使用 Microsoft 树查看器浏览模型</span><span class="sxs-lookup"><span data-stu-id="0ce8e-106">Browse a Model Using the Microsoft Tree Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-tree-viewer.md)  
  
 [<span data-ttu-id="0ce8e-107">使用 Microsoft Naive Bayes 查看器浏览模型</span><span class="sxs-lookup"><span data-stu-id="0ce8e-107">Browse a Model Using the Microsoft Naive Bayes Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)  
  
 [<span data-ttu-id="0ce8e-108">使用 Microsoft 关联规则查看器浏览模型</span><span class="sxs-lookup"><span data-stu-id="0ce8e-108">Browse a Model Using the Microsoft Association Rules Viewer</span></span>](data-mining/browse-a-model-using-the-microsoft-association-rules-viewer.md)  
  
## <a name="options"></a><span data-ttu-id="0ce8e-109">选项</span><span class="sxs-lookup"><span data-stu-id="0ce8e-109">Options</span></span>  
 <span data-ttu-id="0ce8e-110">**刷新查看器内容**</span><span class="sxs-lookup"><span data-stu-id="0ce8e-110">**Refresh viewer content**</span></span>  
 <span data-ttu-id="0ce8e-111">在查看器中重新加载挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="0ce8e-111">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="0ce8e-112">**挖掘模型**</span><span class="sxs-lookup"><span data-stu-id="0ce8e-112">**Mining Model**</span></span>  
 <span data-ttu-id="0ce8e-113">从当前挖掘结构的挖掘模型中选择一个挖掘模型以进行查看。</span><span class="sxs-lookup"><span data-stu-id="0ce8e-113">Choose a mining model to view, from those in the current mining structure.</span></span> <span data-ttu-id="0ce8e-114">挖掘模型将在自定义查看器中打开。</span><span class="sxs-lookup"><span data-stu-id="0ce8e-114">The mining model will open in a custom viewer.</span></span> <span data-ttu-id="0ce8e-115">用于每个模型的自定义查看器的类型由您用来创建该模型的算法决定。</span><span class="sxs-lookup"><span data-stu-id="0ce8e-115">The type of custom viewer that is used for each model is determined by the algorithm that you used to create the model.</span></span>  
  
 <span data-ttu-id="0ce8e-116">**查看器**</span><span class="sxs-lookup"><span data-stu-id="0ce8e-116">**Viewer**</span></span>  
 <span data-ttu-id="0ce8e-117">选择用于浏览所选挖掘模型的查看器。</span><span class="sxs-lookup"><span data-stu-id="0ce8e-117">Choose a viewer to use to explore the selected mining model.</span></span> <span data-ttu-id="0ce8e-118">对于每个挖掘模型，可以使用为其提供的自定义查看器，也可以使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] 挖掘内容查看器。</span><span class="sxs-lookup"><span data-stu-id="0ce8e-118">For each model, you can use either the custom viewer is provided for each mining model, or the [!INCLUDE[msCoName](../includes/msconame-md.md)] Mining Content Viewer.</span></span> <span data-ttu-id="0ce8e-119">还可以使用插件查看器（如果有）。</span><span class="sxs-lookup"><span data-stu-id="0ce8e-119">You can also use plug-in viewers if available.</span></span> <span data-ttu-id="0ce8e-120">Microsoft 内容树查看器可用于所有模型，并表示 HTML 表中的模型内容。</span><span class="sxs-lookup"><span data-stu-id="0ce8e-120">The Microsoft Content Tree Viewer can be used with all models, and represents the model content in an HTML table.</span></span>  
  
 <span data-ttu-id="0ce8e-121">**放大**</span><span class="sxs-lookup"><span data-stu-id="0ce8e-121">**Zoom In**</span></span>  
 <span data-ttu-id="0ce8e-122">放大关系图，以便能更详细地查看属性。</span><span class="sxs-lookup"><span data-stu-id="0ce8e-122">Zoom in to the diagram, so that you can see the attributes in more detail.</span></span>  
  
 <span data-ttu-id="0ce8e-123">**缩小**</span><span class="sxs-lookup"><span data-stu-id="0ce8e-123">**Zoom Out**</span></span>  
 <span data-ttu-id="0ce8e-124">缩小关系图，以便能查看更多属性以及这些属性之间的链接。</span><span class="sxs-lookup"><span data-stu-id="0ce8e-124">Zoom out from the diagram, so that you can see more attributes and the links between them.</span></span>  
  
 <span data-ttu-id="0ce8e-125">**复制图形视图**</span><span class="sxs-lookup"><span data-stu-id="0ce8e-125">**Copy Graph View**</span></span>  
 <span data-ttu-id="0ce8e-126">将关系图的可见部分复制到剪贴板。</span><span class="sxs-lookup"><span data-stu-id="0ce8e-126">Copy the visible section of the diagram to the clipboard.</span></span>  
  
 <span data-ttu-id="0ce8e-127">**复制整个图形**</span><span class="sxs-lookup"><span data-stu-id="0ce8e-127">**Copy Entire Graph**</span></span>  
 <span data-ttu-id="0ce8e-128">将完整的关系图复制到剪贴板。</span><span class="sxs-lookup"><span data-stu-id="0ce8e-128">Copy the complete diagram to the clipboard.</span></span>  
  
 <span data-ttu-id="0ce8e-129">**链接**</span><span class="sxs-lookup"><span data-stu-id="0ce8e-129">**Links**</span></span>  
 <span data-ttu-id="0ce8e-130">通过调整属性右侧的滑块，可以调整查看器显示的链接（边缘）数和节点数。</span><span class="sxs-lookup"><span data-stu-id="0ce8e-130">Adjust how many links (edges) and nodes the viewer shows by adjusting the slider to the right of the attributes.</span></span> <span data-ttu-id="0ce8e-131">向下拖动滑动条将增大阈值，以便只显示最强链接。</span><span class="sxs-lookup"><span data-stu-id="0ce8e-131">Dragging the slider bar down increases the threshold value, so that only the strongest links are shown.</span></span> <span data-ttu-id="0ce8e-132">对于每种模型类型，均使用一个略为不同的值来表示图形中的链接：</span><span class="sxs-lookup"><span data-stu-id="0ce8e-132">For each model type, a slightly different value is used to represent the links in the graph:</span></span>  
  
-   <span data-ttu-id="0ce8e-133">在 **决策树** 模型中，边缘表示连接的预测强度（部分地由拆分分数决定）。</span><span class="sxs-lookup"><span data-stu-id="0ce8e-133">In a **decision tree** model, the edges represent the predictive strength of the connection, determined partly by the split score.</span></span>  
  
-   <span data-ttu-id="0ce8e-134">在 **Naïve Bayes** 模型中，两个节点之间的链接可以在任一方向上进行：也就是说，节点 A 可预测节点 B，节点 B 也可预测节点 A。</span><span class="sxs-lookup"><span data-stu-id="0ce8e-134">In a **Naïve Bayes** model, the links between two nodes can go either way: that is, node A can predict the node B, and vice versa.</span></span> <span data-ttu-id="0ce8e-135">与边缘关联的分数表示连接的预测强度。</span><span class="sxs-lookup"><span data-stu-id="0ce8e-135">The score associated with the edge represents the predictive strength of the connection.</span></span>  
  
-   <span data-ttu-id="0ce8e-136">在 **关联模型**中，节点之间的边缘表示包含连接两个项集的规则的重要性分数。</span><span class="sxs-lookup"><span data-stu-id="0ce8e-136">In an **association model**, the edges between nodes represent the importance score of the rule that connects two itemsets.</span></span>  
  
 <span data-ttu-id="0ce8e-137">所有模型类型的一般规则是：链接越强，两个属性之间的预测关系就越强。</span><span class="sxs-lookup"><span data-stu-id="0ce8e-137">A general rule for all model types is that the stronger the link, the stronger the predictive relationship between the two attributes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ce8e-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0ce8e-138">See Also</span></span>  
 <span data-ttu-id="0ce8e-139">[数据挖掘算法 &#40;Analysis Services 数据挖掘&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="0ce8e-139">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="0ce8e-140">[挖掘模型查看器 &#40;数据挖掘模型设计器&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="0ce8e-140">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="0ce8e-141">数据挖掘模型查看器</span><span class="sxs-lookup"><span data-stu-id="0ce8e-141">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
