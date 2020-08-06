---
title: 挖掘模型查看器 (的属性对比选项卡) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.naivebayse.discrimination.f1
ms.assetid: 68323f23-121e-44fc-be85-6f9915d6d3c7
author: minewiskan
ms.author: owend
ms.openlocfilehash: a8b0d4bc99b1c8f1c5de0269312f02eeb09df022
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579365"
---
# <a name="attribute-discrimination-tab-mining-model-viewer"></a><span data-ttu-id="20207-102">“属性对比”选项卡（挖掘模型查看器）</span><span class="sxs-lookup"><span data-stu-id="20207-102">Attribute Discrimination Tab (Mining Model Viewer)</span></span>
  <span data-ttu-id="20207-103">可以使用 **“属性对比”** 选项卡，比较输入属性的状态并查看这些状态与结果属性相关的方式。</span><span class="sxs-lookup"><span data-stu-id="20207-103">Use the **Attribute Discrimination** tab to compare the states of the input attributes and see how they are related to the outcome attribute.</span></span> <span data-ttu-id="20207-104">两个所选的可预测属性状态之间差别最大的属性值会首先列出。</span><span class="sxs-lookup"><span data-stu-id="20207-104">The attribute values that make the most difference between the two selected predictable attribute states are listed first.</span></span>  
  
 <span data-ttu-id="20207-105">\*\*有关详细信息，请参阅 \*\* [Microsoft Naive Bayes 算法](data-mining/microsoft-naive-bayes-algorithm.md)、[使用 Microsoft Naive Bayes 查看器浏览模型](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="20207-105">**For More Information:** [Microsoft Naive Bayes Algorithm](data-mining/microsoft-naive-bayes-algorithm.md), [Browse a Model Using the Microsoft Naive Bayes Viewer](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="20207-106">选项</span><span class="sxs-lookup"><span data-stu-id="20207-106">Options</span></span>  
 <span data-ttu-id="20207-107">**刷新查看器内容**</span><span class="sxs-lookup"><span data-stu-id="20207-107">**Refresh viewer content**</span></span>  
 <span data-ttu-id="20207-108">在查看器中重新加载挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="20207-108">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="20207-109">**挖掘模型**</span><span class="sxs-lookup"><span data-stu-id="20207-109">**Mining Model**</span></span>  
 <span data-ttu-id="20207-110">从当前挖掘结构的挖掘模型中选择一个挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="20207-110">Choose a mining model from those in the current mining structure.</span></span> <span data-ttu-id="20207-111">该挖掘模型将自动在正确的自定义查看器中打开。</span><span class="sxs-lookup"><span data-stu-id="20207-111">The mining model automatically opens in the correct custom viewer.</span></span>  
  
 <span data-ttu-id="20207-112">**查看器**</span><span class="sxs-lookup"><span data-stu-id="20207-112">**Viewer**</span></span>  
 <span data-ttu-id="20207-113">选择用于浏览所选挖掘模型的查看器。</span><span class="sxs-lookup"><span data-stu-id="20207-113">Choose a viewer to use to explore the selected mining model.</span></span> <span data-ttu-id="20207-114">对于每个模型，您可以选择自定义查看器或 [!INCLUDE[msCoName](../includes/msconame-md.md)] 挖掘内容查看器。</span><span class="sxs-lookup"><span data-stu-id="20207-114">For each model, you can choose either the custom viewer, or the [!INCLUDE[msCoName](../includes/msconame-md.md)] Mining Content Viewer.</span></span> <span data-ttu-id="20207-115">还可以使用插件查看器（如果有）。</span><span class="sxs-lookup"><span data-stu-id="20207-115">You can also use plug-in viewers if available.</span></span>  
  
 <span data-ttu-id="20207-116">**特性**</span><span class="sxs-lookup"><span data-stu-id="20207-116">**Attribute**</span></span>  
 <span data-ttu-id="20207-117">选择一个可预测属性。</span><span class="sxs-lookup"><span data-stu-id="20207-117">Choose a predictable attribute.</span></span>  
  
 <span data-ttu-id="20207-118">**值 1**</span><span class="sxs-lookup"><span data-stu-id="20207-118">**Value 1**</span></span>  
 <span data-ttu-id="20207-119">选择可预测属性的状态以与 **“值 2”** 中所包含状态进行比较。</span><span class="sxs-lookup"><span data-stu-id="20207-119">Choose a state of the predictable attribute to compare to the state that is contained in **Value 2**.</span></span>  
  
 <span data-ttu-id="20207-120">**值 2**</span><span class="sxs-lookup"><span data-stu-id="20207-120">**Value 2**</span></span>  
 <span data-ttu-id="20207-121">选择可预测属性的状态以与 **“值 1”** 中所包含状态进行比较。</span><span class="sxs-lookup"><span data-stu-id="20207-121">Select a state of the predictable attribute to compare to the state that is contained in **Value 1**.</span></span> <span data-ttu-id="20207-122">你还可以选择 "**所有其他状态**"，以将**值 1**中的值与其补数（即除值1之外的所有其他值）进行比较。</span><span class="sxs-lookup"><span data-stu-id="20207-122">You can also select **All Other States** to compare the value in **Value 1** with its complement-that is, all other values except Value 1.</span></span>  
  
 <span data-ttu-id="20207-123">**和的歧视分数 \<Value 1>\<Value 2>**</span><span class="sxs-lookup"><span data-stu-id="20207-123">**Discrimination scores for \<Value 1> and \<Value 2>**</span></span>  
 <span data-ttu-id="20207-124">图形包含以下列，这些列说明了目标属性与输入属性的特定状态关联的方式。</span><span class="sxs-lookup"><span data-stu-id="20207-124">The graph contains the following columns, which describe how the target attribute is related to specific states of the input attribute.</span></span>  
  
|<span data-ttu-id="20207-125">值</span><span class="sxs-lookup"><span data-stu-id="20207-125">Value</span></span>|<span data-ttu-id="20207-126">说明</span><span class="sxs-lookup"><span data-stu-id="20207-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="20207-127">**属性**</span><span class="sxs-lookup"><span data-stu-id="20207-127">**Attributes**</span></span>|<span data-ttu-id="20207-128">挖掘模型中的输入属性。</span><span class="sxs-lookup"><span data-stu-id="20207-128">An input attribute in the mining model.</span></span>|  
|<span data-ttu-id="20207-129">**值**</span><span class="sxs-lookup"><span data-stu-id="20207-129">**Values**</span></span>|<span data-ttu-id="20207-130">**“属性”** 中列出的属性的状态。</span><span class="sxs-lookup"><span data-stu-id="20207-130">A state of the attribute that is listed in **Attributes**.</span></span>|  
|<span data-ttu-id="20207-131">**有利\<Value 1>**</span><span class="sxs-lookup"><span data-stu-id="20207-131">**Favors \<Value 1>**</span></span>|<span data-ttu-id="20207-132">条形指示当前属性和值是否倾向于“值 1” \*\*\*\* 中所选的目标结果。</span><span class="sxs-lookup"><span data-stu-id="20207-132">The bar indicates whether the current attribute and value favor the target outcome selected in **Value 1**.</span></span>|  
|<span data-ttu-id="20207-133">**有利\<Value 2>**</span><span class="sxs-lookup"><span data-stu-id="20207-133">**Favors \<Value 2>**</span></span>|<span data-ttu-id="20207-134">条形指示当前属性和值是否倾向于 **“值 2”** 中所选的目标结果。</span><span class="sxs-lookup"><span data-stu-id="20207-134">The bar indicates whether the current attribute and value favor the target outcome selected in **Value 2**.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="20207-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="20207-135">See Also</span></span>  
 <span data-ttu-id="20207-136">[数据挖掘算法 &#40;Analysis Services 数据挖掘&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="20207-136">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="20207-137">[挖掘模型查看器 &#40;数据挖掘模型设计器&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="20207-137">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="20207-138">数据挖掘模型查看器</span><span class="sxs-lookup"><span data-stu-id="20207-138">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
