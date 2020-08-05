---
title: " (挖掘模型查看器) 的 \"分类配置文件\" 选项卡 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.clustering.profiles.f1
ms.assetid: 1ebafa1f-74e9-4c05-b278-a690fa8543bd
author: minewiskan
ms.author: owend
ms.openlocfilehash: a7ec1ce5b5204ae81a9313ca7b7e5df58c98c5da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579879"
---
# <a name="cluster-profiles-tab-mining-model-viewer"></a><span data-ttu-id="102c9-102">“分类剖面图”选项卡（挖掘模型查看器）</span><span class="sxs-lookup"><span data-stu-id="102c9-102">Cluster Profiles Tab (Mining Model Viewer)</span></span>
  <span data-ttu-id="102c9-103">可以使用 **“分类剖面图”** 选项卡，提供算法在分类模型中发现的分类的总体视图。</span><span class="sxs-lookup"><span data-stu-id="102c9-103">Use the **Cluster Profiles** tab for an overall view of the clusters that the algorithm discovered within a clustering model.</span></span> <span data-ttu-id="102c9-104">该选项卡可显示每个属性及其在每个分类中的分布情况。</span><span class="sxs-lookup"><span data-stu-id="102c9-104">The tab displays each attribute, together with the distribution of the attribute in each cluster.</span></span>  
  
 <span data-ttu-id="102c9-105">\*\*有关详细信息，请参阅 \*\* [Microsoft 聚类分析算法](data-mining/microsoft-clustering-algorithm.md)和[使用 Microsoft 分类查看器浏览模型](data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="102c9-105">**For More Information:** [Microsoft Clustering Algorithm](data-mining/microsoft-clustering-algorithm.md), [Browse a Model Using the Microsoft Cluster Viewer](data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="102c9-106">选项</span><span class="sxs-lookup"><span data-stu-id="102c9-106">Options</span></span>  
 <span data-ttu-id="102c9-107">**刷新查看器内容**</span><span class="sxs-lookup"><span data-stu-id="102c9-107">**Refresh viewer content**</span></span>  
 <span data-ttu-id="102c9-108">在查看器中重新加载挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="102c9-108">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="102c9-109">**挖掘模型**</span><span class="sxs-lookup"><span data-stu-id="102c9-109">**Mining Model**</span></span>  
 <span data-ttu-id="102c9-110">从当前挖掘结构的挖掘模型中选择一个挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="102c9-110">Choose a mining model from those in the current mining structure.</span></span> <span data-ttu-id="102c9-111">挖掘模型将在其关联的查看器中打开。</span><span class="sxs-lookup"><span data-stu-id="102c9-111">The mining model will open in its associated viewer.</span></span>  
  
 <span data-ttu-id="102c9-112">**查看器**</span><span class="sxs-lookup"><span data-stu-id="102c9-112">**Viewer**</span></span>  
 <span data-ttu-id="102c9-113">选择用于查看所选挖掘模型的查看器。</span><span class="sxs-lookup"><span data-stu-id="102c9-113">Choose a viewer to use to view the selected mining model.</span></span> <span data-ttu-id="102c9-114">可以对挖掘模型使用自定义查看器，也可以使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] 挖掘内容查看器。</span><span class="sxs-lookup"><span data-stu-id="102c9-114">You can use the custom viewer for the mining model, or the [!INCLUDE[msCoName](../includes/msconame-md.md)] Mining Content Viewer.</span></span> <span data-ttu-id="102c9-115">还可以使用插件查看器（如果有）。</span><span class="sxs-lookup"><span data-stu-id="102c9-115">You can also use plug-in viewers if available.</span></span>  
  
 <span data-ttu-id="102c9-116">**显示图例**</span><span class="sxs-lookup"><span data-stu-id="102c9-116">**Show Legend**</span></span>  
 <span data-ttu-id="102c9-117">选择此选项可显示一个键，该键将显示查看器中的颜色与“状态”\*\*\*\* 列中的值之间的映射。</span><span class="sxs-lookup"><span data-stu-id="102c9-117">Select this option to display a key that shows the mapping of colors in the viewer to values in the **States** column.</span></span>  
  
 <span data-ttu-id="102c9-118">**直方图条**</span><span class="sxs-lookup"><span data-stu-id="102c9-118">**Histogram Bars**</span></span>  
 <span data-ttu-id="102c9-119">更改此值可控制每个直方图中包含的状态的数目。</span><span class="sxs-lookup"><span data-stu-id="102c9-119">Change this value to control how many states are included in each histogram.</span></span> <span data-ttu-id="102c9-120">如果存在的状态数多于您选择显示的状态数，则直方图中将显示概率最高的状态，其余状态则组合到 **“其他”** 中。</span><span class="sxs-lookup"><span data-stu-id="102c9-120">If there are more states than you choose to display, the states with the highest probability are shown in the histogram, and the remaining states are grouped together into **Other**.</span></span>  
  
 <span data-ttu-id="102c9-121">**属性**</span><span class="sxs-lookup"><span data-stu-id="102c9-121">**Attributes**</span></span>  
 <span data-ttu-id="102c9-122">列出分类模型中包含的列。</span><span class="sxs-lookup"><span data-stu-id="102c9-122">Lists the columns that are in the clustering model.</span></span> <span data-ttu-id="102c9-123">每个属性的直方图均演示该属性在算法所标识的分类中的分布方式。</span><span class="sxs-lookup"><span data-stu-id="102c9-123">The histograms for each attribute show how the attribute is distributed among the clusters identified by the algorithm.</span></span>  
  
 <span data-ttu-id="102c9-124">**状态**</span><span class="sxs-lookup"><span data-stu-id="102c9-124">**States**</span></span>  
 <span data-ttu-id="102c9-125">提供一个键，用于指示代表分类的对应行中的每个状态的颜色，或提供一个菱形滑块，用于指示连续数值的分布。</span><span class="sxs-lookup"><span data-stu-id="102c9-125">Provides a key that either denotes what color represents each state in the corresponding row of clusters, or a slider with diamond that indicates the distribution of continuous numeric values.</span></span> <span data-ttu-id="102c9-126">可以使用 **“显示图例”** 复选框来显示或隐藏此列。</span><span class="sxs-lookup"><span data-stu-id="102c9-126">You can show or hide this column by using the **Show Legend** check box.</span></span>  
  
 <span data-ttu-id="102c9-127">**分类剖面图**</span><span class="sxs-lookup"><span data-stu-id="102c9-127">**Cluster Profiles**</span></span>  
 <span data-ttu-id="102c9-128">本节对于模型中的每个分类都包含一个列。</span><span class="sxs-lookup"><span data-stu-id="102c9-128">This section contains a column for each cluster in the model.</span></span> <span data-ttu-id="102c9-129">对于每个属性，直方图显示该属性的值相对于相应分类的分布情况。</span><span class="sxs-lookup"><span data-stu-id="102c9-129">For each attribute, the histogram shows the distribution of the values in the attribute for just that cluster.</span></span> <span data-ttu-id="102c9-130">此图表还包含一个 **“总体”** 列，该列也会使用直方图来显示每个属性的值的分布情况（但针对的是模型中的事例）。</span><span class="sxs-lookup"><span data-stu-id="102c9-130">The chart also has a column for **Population**, which also uses histograms to display the distribution of values for each attribute, but for all cases in the model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="102c9-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="102c9-131">See Also</span></span>  
 <span data-ttu-id="102c9-132">[数据挖掘算法 &#40;Analysis Services 数据挖掘&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="102c9-132">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="102c9-133">[挖掘模型查看器 &#40;数据挖掘模型设计器&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="102c9-133">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="102c9-134">数据挖掘模型查看器</span><span class="sxs-lookup"><span data-stu-id="102c9-134">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
