---
title: " (挖掘模型查看器) 的顺序分析群集特性选项卡 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.sequenceclustering.characteristics.f1
ms.assetid: 3a9e8a0c-7d03-47cc-8625-e68d73a8c947
author: minewiskan
ms.author: owend
ms.openlocfilehash: c991005cb4daa436c86d09037ef523499add84e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693512"
---
# <a name="sequence-clustering-cluster-characteristics-tab-mining-model-viewer"></a><span data-ttu-id="3e97f-102">顺序分析和聚类分析的“分类特征”选项卡（挖掘模型查看器）</span><span class="sxs-lookup"><span data-stu-id="3e97f-102">Sequence Clustering Cluster Characteristics Tab (Mining Model Viewer)</span></span>
  <span data-ttu-id="3e97f-103">**“Microsoft 顺序分析和聚类分析查看器”** 中的 **“分类特征”** 选项卡提供了定义序列分类的特征的详细列表。</span><span class="sxs-lookup"><span data-stu-id="3e97f-103">The **Cluster Characteristics** tab in the **Microsoft Sequence Clustering Viewer** provides a detailed list of the characteristics that define a sequence cluster.</span></span> <span data-ttu-id="3e97f-104">这些特征可包括简单属性-值对以及状态间的转换。</span><span class="sxs-lookup"><span data-stu-id="3e97f-104">Those characteristics can include simple attribute-value pairs as well as transitions between states.</span></span>  
  
 <span data-ttu-id="3e97f-105">可以使用此顺序分析和聚类分析模型视图，来深化到分类内容并查看代表分类的序列。</span><span class="sxs-lookup"><span data-stu-id="3e97f-105">Use this view of a sequence clustering model to drill down into the cluster contents, and see the sequences that are representative of a cluster.</span></span>  
  
 <span data-ttu-id="3e97f-106">\*\*有关详细信息，请参阅 \*\* [Microsoft 顺序分析和聚类分析算法](data-mining/microsoft-sequence-clustering-algorithm.md)和[使用 Microsoft 序列分类查看器浏览模型](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="3e97f-106">**For More Information:** [Microsoft Sequence Clustering Algorithm](data-mining/microsoft-sequence-clustering-algorithm.md), [Browse a Model Using the Microsoft Sequence Cluster Viewer](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="3e97f-107">选项</span><span class="sxs-lookup"><span data-stu-id="3e97f-107">Options</span></span>  
 <span data-ttu-id="3e97f-108">**刷新查看器内容**</span><span class="sxs-lookup"><span data-stu-id="3e97f-108">**Refresh viewer content**</span></span>  
 <span data-ttu-id="3e97f-109">在查看器中重新加载挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="3e97f-109">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="3e97f-110">**挖掘模型**</span><span class="sxs-lookup"><span data-stu-id="3e97f-110">**Mining Model**</span></span>  
 <span data-ttu-id="3e97f-111">选择一个包含在当前挖掘结构中的挖掘模型以进行查看。</span><span class="sxs-lookup"><span data-stu-id="3e97f-111">Choose a mining model to view that is contained in the current mining structure.</span></span> <span data-ttu-id="3e97f-112">挖掘模型将在其关联的查看器中打开。</span><span class="sxs-lookup"><span data-stu-id="3e97f-112">The mining model will open in its associated viewer.</span></span>  
  
 <span data-ttu-id="3e97f-113">**查看器**</span><span class="sxs-lookup"><span data-stu-id="3e97f-113">**Viewer**</span></span>  
 <span data-ttu-id="3e97f-114">选择用于浏览选定挖掘模型的查看器。</span><span class="sxs-lookup"><span data-stu-id="3e97f-114">Choose a viewer to use in exploring the selected mining model.</span></span> <span data-ttu-id="3e97f-115">您可以使用自定义查看器或 **“Microsoft 一般内容树查看器”**。</span><span class="sxs-lookup"><span data-stu-id="3e97f-115">You can use the custom viewer, or the **Microsoft Generic Content Tree Viewer**.</span></span> <span data-ttu-id="3e97f-116">还可以使用插件查看器（如果有）。</span><span class="sxs-lookup"><span data-stu-id="3e97f-116">You can also use plug-in viewers if available.</span></span>  
  
 <span data-ttu-id="3e97f-117">**Cluster**</span><span class="sxs-lookup"><span data-stu-id="3e97f-117">**Cluster**</span></span>  
 <span data-ttu-id="3e97f-118">选择要查看的分类。</span><span class="sxs-lookup"><span data-stu-id="3e97f-118">Choose the cluster you want to view.</span></span>  
  
 <span data-ttu-id="3e97f-119">**特性\<Cluster>**</span><span class="sxs-lookup"><span data-stu-id="3e97f-119">**Characteristics for \<Cluster>**</span></span>  
 <span data-ttu-id="3e97f-120">此表提供已分配给当前分类的序列的列表（按概率排序）。</span><span class="sxs-lookup"><span data-stu-id="3e97f-120">This table provides a list of the sequences that were assigned to the current cluster, ordered by probability.</span></span> <span data-ttu-id="3e97f-121">请记住，序列基本上是一个属性-值对，后跟一个或多个其他的属性-值对。</span><span class="sxs-lookup"><span data-stu-id="3e97f-121">Remember that a sequence is basically one attribute-value pair, followed by one or more additional attribute-value pairs.</span></span> <span data-ttu-id="3e97f-122">序列及其概率的组合定义了每个分类的特征。</span><span class="sxs-lookup"><span data-stu-id="3e97f-122">The combination of sequences and their probabilities are the defining characteristics of each cluster.</span></span>  
  
 <span data-ttu-id="3e97f-123">例如，在基于市场篮分析的顺序分析和聚类分析模型中，一个分类可以让客户选择销售项，然后在不再购买其他项的情况下结束事务（这是此模型最主要的特点）。</span><span class="sxs-lookup"><span data-stu-id="3e97f-123">For example, in a sequence clustering model based on market basket analysis, one cluster might have as its top characteristic a customer choosing the sale item and then ending the transaction without purchasing anything more.</span></span> <span data-ttu-id="3e97f-124">在试图分析服务器失败的顺序分析和聚类分析模型中，分类的主要特征可能是一系列高频率错误事件。</span><span class="sxs-lookup"><span data-stu-id="3e97f-124">In a sequence clustering model that seeks to analyze server failures, the primary characteristics of a cluster might be a series of high frequency error events.</span></span>  
  
|<span data-ttu-id="3e97f-125">值</span><span class="sxs-lookup"><span data-stu-id="3e97f-125">Value</span></span>|<span data-ttu-id="3e97f-126">说明</span><span class="sxs-lookup"><span data-stu-id="3e97f-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3e97f-127">**变量**</span><span class="sxs-lookup"><span data-stu-id="3e97f-127">**Variable**</span></span>|<span data-ttu-id="3e97f-128">此列指示特征是一个值还是一个转换。</span><span class="sxs-lookup"><span data-stu-id="3e97f-128">This column indicates whether the characteristic is a value, or a transition.</span></span><br /><br /> <span data-ttu-id="3e97f-129">如果特征是一个值，则 "**变量**" 列包含属性名称。</span><span class="sxs-lookup"><span data-stu-id="3e97f-129">If the characteristic is a value, the **Variable** column contains the attribute name.</span></span><br /><br /> <span data-ttu-id="3e97f-130">如果特征表示状态转换，则 "**变量**" 列会包含文本 "转换"。</span><span class="sxs-lookup"><span data-stu-id="3e97f-130">If the characteristic represents a state transition, the **Variable** column contains the text "Transitions".</span></span>|  
|<span data-ttu-id="3e97f-131">**值**</span><span class="sxs-lookup"><span data-stu-id="3e97f-131">**Values**</span></span>|<span data-ttu-id="3e97f-132">此列的值取决于特征是一个简单属性-值对，还是一个表示项或事件的常见序列的状态转换。</span><span class="sxs-lookup"><span data-stu-id="3e97f-132">The value of this column depends on whether the characteristic is a simple attribute-value pair, or a state transition representing a common sequence of items or events.</span></span><br /><br /> <span data-ttu-id="3e97f-133">如果特征是一个值，则 "**值**" 列会包含状态。</span><span class="sxs-lookup"><span data-stu-id="3e97f-133">If the characteristic is a value, the **Value** column contains the state.</span></span><br /><br /> <span data-ttu-id="3e97f-134">如果特征表示状态转换，则 "**值**" 列包含状态转换的说明。</span><span class="sxs-lookup"><span data-stu-id="3e97f-134">If the characteristic represents a state transition, the **Value** column contains the description of the state transition.</span></span>|  
|<span data-ttu-id="3e97f-135">**概率**</span><span class="sxs-lookup"><span data-stu-id="3e97f-135">**Probability**</span></span>|<span data-ttu-id="3e97f-136">该列会显示一个栏，用于指示此特征（简单属性-值对或某些状态组合）是当前分类的成员的相对概率。</span><span class="sxs-lookup"><span data-stu-id="3e97f-136">This column displays a bar that indicates the relative probability that this characteristic (either a simple attribute-value pair, or some combination of states) are members of the current cluster.</span></span><br /><br /> <span data-ttu-id="3e97f-137">可以将鼠标悬停在该栏的上方，来显示特征的频率值。</span><span class="sxs-lookup"><span data-stu-id="3e97f-137">You can hover the mouse over the par to display the frequency value of the characteristic.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3e97f-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3e97f-138">See Also</span></span>  
 <span data-ttu-id="3e97f-139">[数据挖掘算法 &#40;Analysis Services 数据挖掘&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="3e97f-139">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="3e97f-140">[挖掘模型查看器 &#40;数据挖掘模型设计器&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="3e97f-140">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="3e97f-141">数据挖掘模型查看器</span><span class="sxs-lookup"><span data-stu-id="3e97f-141">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
