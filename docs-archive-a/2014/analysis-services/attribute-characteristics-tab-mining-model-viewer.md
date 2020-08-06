---
title: 挖掘模型查看器 ("属性特征" 选项卡) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.naivebayse.characteristics.f1
ms.assetid: f0c3350d-84c0-4ab8-9fb8-1527c2647299
author: minewiskan
ms.author: owend
ms.openlocfilehash: b29ba482c21bb674a10bc4c9e6c6eccdf30905dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579370"
---
# <a name="attribute-characteristics-tab-mining-model-viewer"></a><span data-ttu-id="4ef76-102">“属性特征”选项卡（挖掘模型查看器）</span><span class="sxs-lookup"><span data-stu-id="4ef76-102">Attribute Characteristics Tab (Mining Model Viewer)</span></span>
  <span data-ttu-id="4ef76-103">可以使用 **“属性特征”** 窗格浏览 Naïve Bayes 模型中结果和输入属性之间的关系。</span><span class="sxs-lookup"><span data-stu-id="4ef76-103">Use the **Attribute Characteristics** pane to explore the relationships between outcomes and input attributes in a Naïve Bayes model.</span></span> <span data-ttu-id="4ef76-104">可以选择目标属性的值，然后查看对结果产生的影响最大的输入属性的列表。</span><span class="sxs-lookup"><span data-stu-id="4ef76-104">You can choose the value of the target attribute, and then see a list of the input attributes that have the strongest effect on the outcomes.</span></span>  
  
 <span data-ttu-id="4ef76-105">\*\*有关详细信息，请参阅 \*\* [Microsoft Naive Bayes 算法](data-mining/microsoft-naive-bayes-algorithm.md)、[使用 Microsoft Naive Bayes 查看器浏览模型](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="4ef76-105">**For More Information:** [Microsoft Naive Bayes Algorithm](data-mining/microsoft-naive-bayes-algorithm.md), [Browse a Model Using the Microsoft Naive Bayes Viewer](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="4ef76-106">选项</span><span class="sxs-lookup"><span data-stu-id="4ef76-106">Options</span></span>  
 <span data-ttu-id="4ef76-107">**刷新查看器内容**</span><span class="sxs-lookup"><span data-stu-id="4ef76-107">**Refresh viewer content**</span></span>  
 <span data-ttu-id="4ef76-108">在查看器中重新加载挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="4ef76-108">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="4ef76-109">**挖掘模型**</span><span class="sxs-lookup"><span data-stu-id="4ef76-109">**Mining Model**</span></span>  
 <span data-ttu-id="4ef76-110">从当前挖掘结构的模型中选择一个挖掘模型以进行查看。</span><span class="sxs-lookup"><span data-stu-id="4ef76-110">Choose a mining model to view, from the models in the current mining structure.</span></span> <span data-ttu-id="4ef76-111">挖掘模型将自动在最适用于所选特定类型的模型的自定义查看器中打开。</span><span class="sxs-lookup"><span data-stu-id="4ef76-111">The mining model will automatically open in a custom viewer that is best for the particular type of model you chose.</span></span>  
  
 <span data-ttu-id="4ef76-112">**查看器**</span><span class="sxs-lookup"><span data-stu-id="4ef76-112">**Viewer**</span></span>  
 <span data-ttu-id="4ef76-113">选择用于浏览所选挖掘模型的查看器。</span><span class="sxs-lookup"><span data-stu-id="4ef76-113">Choose a viewer to use to explore the selected mining model.</span></span> <span data-ttu-id="4ef76-114">对于每个模型，您可以选择自定义查看器或 [!INCLUDE[msCoName](../includes/msconame-md.md)] 挖掘内容查看器。</span><span class="sxs-lookup"><span data-stu-id="4ef76-114">For each model, you have the choice of a custom viewer, or the [!INCLUDE[msCoName](../includes/msconame-md.md)] Mining Content Viewer.</span></span> <span data-ttu-id="4ef76-115">插件查看器也将出现在此列表中（如果有）。</span><span class="sxs-lookup"><span data-stu-id="4ef76-115">Plug-in viewers also appear in this list if available.</span></span>  
  
 <span data-ttu-id="4ef76-116">**特性**</span><span class="sxs-lookup"><span data-stu-id="4ef76-116">**Attribute**</span></span>  
 <span data-ttu-id="4ef76-117">选择要分析的可预测属性。</span><span class="sxs-lookup"><span data-stu-id="4ef76-117">Choose the predictable attribute that you want to analyze.</span></span>  
  
 <span data-ttu-id="4ef76-118">**值**</span><span class="sxs-lookup"><span data-stu-id="4ef76-118">**Value**</span></span>  
 <span data-ttu-id="4ef76-119">选择在“属性”中设置的可预测属性的状态。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="4ef76-119">Choose a state for the predictable attribute that you set in **Attribute**.</span></span> <span data-ttu-id="4ef76-120">由于 Naïve Bayes 模型不支持连续变量，因此，所有目标属性都包含离散或离散化结果。</span><span class="sxs-lookup"><span data-stu-id="4ef76-120">Because Naïve Bayes models do not support continuous variables, all target attributes have discrete or discretized outcomes.</span></span> <span data-ttu-id="4ef76-121">始终会自动将 Missing 属性添加到列表。</span><span class="sxs-lookup"><span data-stu-id="4ef76-121">The Missing attribute is always automatically added to the list.</span></span>  
  
 <span data-ttu-id="4ef76-122">**特性\<predictable state>**</span><span class="sxs-lookup"><span data-stu-id="4ef76-122">**Characteristics for \<predictable state>**</span></span>  
 <span data-ttu-id="4ef76-123">图形包含以下列，这些列对输入属性状态与所选可预测属性状态之间的关系进行了说明：</span><span class="sxs-lookup"><span data-stu-id="4ef76-123">The graph contains the following columns, which describe how states of the input attributes are related to the selected predictable attribute state.</span></span>  
  
|<span data-ttu-id="4ef76-124">值</span><span class="sxs-lookup"><span data-stu-id="4ef76-124">Value</span></span>|<span data-ttu-id="4ef76-125">说明</span><span class="sxs-lookup"><span data-stu-id="4ef76-125">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4ef76-126">**变量**</span><span class="sxs-lookup"><span data-stu-id="4ef76-126">**Variable**</span></span>|<span data-ttu-id="4ef76-127">列出挖掘模型中的输入属性。</span><span class="sxs-lookup"><span data-stu-id="4ef76-127">Lists the input attributes in the mining model.</span></span>|  
|<span data-ttu-id="4ef76-128">**值**</span><span class="sxs-lookup"><span data-stu-id="4ef76-128">**Values**</span></span>|<span data-ttu-id="4ef76-129">列出 **“变量”** 中每个输入属性状态。</span><span class="sxs-lookup"><span data-stu-id="4ef76-129">Lists each state of the input attribute in **Variable**.</span></span>|  
|<span data-ttu-id="4ef76-130">**概率**</span><span class="sxs-lookup"><span data-stu-id="4ef76-130">**Probability**</span></span>|<span data-ttu-id="4ef76-131">条形表示该行中的属性和值与可预测属性的选定状态相关联的概率。</span><span class="sxs-lookup"><span data-stu-id="4ef76-131">The bar represents the probability that the attribute and value in that row are associated with the selected state of the predictable attribute.</span></span> <span data-ttu-id="4ef76-132">将鼠标指针悬停在条形上方可查看以百分比表示的概率。</span><span class="sxs-lookup"><span data-stu-id="4ef76-132">Hover the mouse over the bar to view the probability as a percentage.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4ef76-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4ef76-133">See Also</span></span>  
 <span data-ttu-id="4ef76-134">[数据挖掘算法 &#40;Analysis Services 数据挖掘&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="4ef76-134">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="4ef76-135">[挖掘模型查看器 &#40;数据挖掘模型设计器&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="4ef76-135">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="4ef76-136">数据挖掘模型查看器</span><span class="sxs-lookup"><span data-stu-id="4ef76-136">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
