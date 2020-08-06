---
title: 挖掘模型查看器 (的 "分类特征" 选项卡) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.clustering.characteristics.f1
ms.assetid: 8e33ed1d-1ce4-405d-895b-7e995b2c910d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 959d94767b6cb27d9ebb6e06c592034fca20ac89
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579259"
---
# <a name="cluster-characteristics-tab-mining-model-viewer"></a><span data-ttu-id="e709e-102">“分类特征”选项卡（挖掘模型查看器）</span><span class="sxs-lookup"><span data-stu-id="e709e-102">Cluster Characteristics Tab (Mining Model Viewer)</span></span>
  <span data-ttu-id="e709e-103">利用 **“分类特征”** 选项卡，可以浏览聚类分析模型中分类的特征或该模型中所有事例的集。</span><span class="sxs-lookup"><span data-stu-id="e709e-103">The **Cluster Characteristics** tab lets you explore the characteristics of a cluster in a clustering model, or the set of all cases in the model.</span></span> <span data-ttu-id="e709e-104">图形会将每个属性-值对的重要性显示为定义分类的特征（与其他分类相比）。</span><span class="sxs-lookup"><span data-stu-id="e709e-104">The graph shows the importance of each attribute-value pair as a characteristic that defines the cluster, in comparison with other clusters.</span></span>  
  
 <span data-ttu-id="e709e-105">\*\*有关详细信息，请参阅 \*\* [Microsoft 聚类分析算法](data-mining/microsoft-clustering-algorithm.md)和[使用 Microsoft 分类查看器浏览模型](data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="e709e-105">**For More Information:** [Microsoft Clustering Algorithm](data-mining/microsoft-clustering-algorithm.md), [Browse a Model Using the Microsoft Cluster Viewer](data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="e709e-106">选项</span><span class="sxs-lookup"><span data-stu-id="e709e-106">Options</span></span>  
 <span data-ttu-id="e709e-107">**刷新查看器内容**</span><span class="sxs-lookup"><span data-stu-id="e709e-107">**Refresh viewer content**</span></span>  
 <span data-ttu-id="e709e-108">在查看器中重新加载挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="e709e-108">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="e709e-109">**挖掘模型**</span><span class="sxs-lookup"><span data-stu-id="e709e-109">**Mining Model**</span></span>  
 <span data-ttu-id="e709e-110">从当前挖掘结构的挖掘模型中选择一个挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="e709e-110">Choose a mining model from those in the current mining structure.</span></span> <span data-ttu-id="e709e-111">挖掘模型将在自定义查看器中打开。</span><span class="sxs-lookup"><span data-stu-id="e709e-111">The mining model will open in the custom viewer.</span></span>  
  
 <span data-ttu-id="e709e-112">**查看器**</span><span class="sxs-lookup"><span data-stu-id="e709e-112">**Viewer**</span></span>  
 <span data-ttu-id="e709e-113">选择用于浏览所选挖掘模型的查看器。</span><span class="sxs-lookup"><span data-stu-id="e709e-113">Choose a viewer to use to explore the selected mining model.</span></span> <span data-ttu-id="e709e-114">可以使用与此模型类型关联的自定义查看器或 [!INCLUDE[msCoName](../includes/msconame-md.md)] 挖掘内容查看器。</span><span class="sxs-lookup"><span data-stu-id="e709e-114">You can use the custom viewer associated with this model type, or the [!INCLUDE[msCoName](../includes/msconame-md.md)] Mining Content Viewer.</span></span> <span data-ttu-id="e709e-115">还可以使用任何可用的插件查看器。</span><span class="sxs-lookup"><span data-stu-id="e709e-115">You can also use any plug-in viewers that are available.</span></span>  
  
 <span data-ttu-id="e709e-116">**Cluster**</span><span class="sxs-lookup"><span data-stu-id="e709e-116">**Cluster**</span></span>  
 <span data-ttu-id="e709e-117">选择要查看的分类，或选择“总体(全部)”以查看模型的属性的整体分布情况。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="e709e-117">Choose the cluster you want to view, or choose **Population (All)** to see the distribution of attributes for the model as a whole.</span></span>  
  
 <span data-ttu-id="e709e-118">**特性\<cluster>**</span><span class="sxs-lookup"><span data-stu-id="e709e-118">**Characteristics for \<cluster>**</span></span>  
 <span data-ttu-id="e709e-119">图形包含以下列，这些列对所选分类的特征进行了说明。</span><span class="sxs-lookup"><span data-stu-id="e709e-119">The graph contains the following columns, which describe the characteristics of the selected cluster.</span></span>  
  
|<span data-ttu-id="e709e-120">值</span><span class="sxs-lookup"><span data-stu-id="e709e-120">Value</span></span>|<span data-ttu-id="e709e-121">说明</span><span class="sxs-lookup"><span data-stu-id="e709e-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e709e-122">**变量**</span><span class="sxs-lookup"><span data-stu-id="e709e-122">**Variable**</span></span>|<span data-ttu-id="e709e-123">列出在所选分类中找到的挖掘模型中的属性。</span><span class="sxs-lookup"><span data-stu-id="e709e-123">Lists the attributes from the mining model that are found in the selected cluster.</span></span>|  
|<span data-ttu-id="e709e-124">**值**</span><span class="sxs-lookup"><span data-stu-id="e709e-124">**Values**</span></span>|<span data-ttu-id="e709e-125">列出在当前所选分类中找到的当前属性的值。</span><span class="sxs-lookup"><span data-stu-id="e709e-125">Lists the values of the current attributes that are found in the currently selected cluster.</span></span>|  
|<span data-ttu-id="e709e-126">**概率**</span><span class="sxs-lookup"><span data-stu-id="e709e-126">**Probability**</span></span>|<span data-ttu-id="e709e-127">条形指示属性-值对的强度作为此分类的显著特征。</span><span class="sxs-lookup"><span data-stu-id="e709e-127">The bar indicates the strength of the attribute-value pair as a distinguishing feature of this cluster.</span></span> <span data-ttu-id="e709e-128">如果您将鼠标指针悬停在条形上方，则可查看以百分比表示的概率值。</span><span class="sxs-lookup"><span data-stu-id="e709e-128">If you hover the mouse over the bar, you can see the probability value, represented as a percentage.</span></span> <span data-ttu-id="e709e-129">这表示，在任何特定事例中使用此属性和值组合时，该事例会归入此分类的概率。</span><span class="sxs-lookup"><span data-stu-id="e709e-129">What this indicates is, given this attribute and value combination in any particular case, what is the probability that the case would belong in this cluster.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e709e-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e709e-130">See Also</span></span>  
 <span data-ttu-id="e709e-131">[数据挖掘算法 &#40;Analysis Services 数据挖掘&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="e709e-131">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="e709e-132">[挖掘模型查看器 &#40;数据挖掘模型设计器&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="e709e-132">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="e709e-133">数据挖掘模型查看器</span><span class="sxs-lookup"><span data-stu-id="e709e-133">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
