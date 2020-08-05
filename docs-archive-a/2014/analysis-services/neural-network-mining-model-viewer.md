---
title: " (挖掘模型查看器的神经网络) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.neuralnet.f1
ms.assetid: 18d87e7b-a821-40ea-9bd8-c6fecf189a1c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 39ca8d3cd9f2a327abd8558b13a018ceda27968d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580918"
---
# <a name="neural-network-mining-model-viewer"></a><span data-ttu-id="5c2ed-102">神经网络（挖掘模型查看器）</span><span class="sxs-lookup"><span data-stu-id="5c2ed-102">Neural Network (Mining Model Viewer)</span></span>
  <span data-ttu-id="5c2ed-103">可以使用 **“神经网络”** 查看器浏览基于 [!INCLUDE[msCoName](../includes/msconame-md.md)] 神经网络算法或 [!INCLUDE[msCoName](../includes/msconame-md.md)] 逻辑回归算法的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="5c2ed-103">Use the **Neural Net** viewer to explore mining models that are based on the [!INCLUDE[msCoName](../includes/msconame-md.md)] Neural Network algorithm or the [!INCLUDE[msCoName](../includes/msconame-md.md)] Logistic Regression algorithm.</span></span>  
  
 <span data-ttu-id="5c2ed-104">**有关详细信息：** [Microsoft 神经网络算法](data-mining/microsoft-neural-network-algorithm.md)、[Microsoft 逻辑回归算法](data-mining/microsoft-logistic-regression-algorithm.md)、[使用 Microsoft 神经网络查看器浏览模型](data-mining/browse-a-model-using-the-microsoft-neural-network-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="5c2ed-104">**For More Information:** [Microsoft Neural Network Algorithm](data-mining/microsoft-neural-network-algorithm.md), [Microsoft Logistic Regression Algorithm](data-mining/microsoft-logistic-regression-algorithm.md),[Browse a Model Using the Microsoft Neural Network Viewer](data-mining/browse-a-model-using-the-microsoft-neural-network-viewer.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="5c2ed-105">选项</span><span class="sxs-lookup"><span data-stu-id="5c2ed-105">Options</span></span>  
 <span data-ttu-id="5c2ed-106">**刷新查看器内容**</span><span class="sxs-lookup"><span data-stu-id="5c2ed-106">**Refresh viewer content**</span></span>  
 <span data-ttu-id="5c2ed-107">在查看器中重新加载挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="5c2ed-107">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="5c2ed-108">**挖掘模型**</span><span class="sxs-lookup"><span data-stu-id="5c2ed-108">**Mining Model**</span></span>  
 <span data-ttu-id="5c2ed-109">从当前挖掘结构的挖掘模型中选择一个挖掘模型以进行查看。</span><span class="sxs-lookup"><span data-stu-id="5c2ed-109">Choose a mining model to view, from those in the current mining structure.</span></span> <span data-ttu-id="5c2ed-110">挖掘模型将在其关联的查看器中打开。</span><span class="sxs-lookup"><span data-stu-id="5c2ed-110">The mining model will open in its associated viewer.</span></span>  
  
 <span data-ttu-id="5c2ed-111">**查看器**</span><span class="sxs-lookup"><span data-stu-id="5c2ed-111">**Viewer**</span></span>  
 <span data-ttu-id="5c2ed-112">选择用于浏览所选挖掘模型的查看器。</span><span class="sxs-lookup"><span data-stu-id="5c2ed-112">Choose a viewer to use to explore the selected mining model.</span></span> <span data-ttu-id="5c2ed-113">您可以使用自定义查看器或 **“Microsoft 一般内容树查看器”**。</span><span class="sxs-lookup"><span data-stu-id="5c2ed-113">You can use the custom viewer, or the **Microsoft Generic Content Tree Viewer**.</span></span> <span data-ttu-id="5c2ed-114">还可以使用插件查看器（如果有）。</span><span class="sxs-lookup"><span data-stu-id="5c2ed-114">You can also use plug-in viewers if available.</span></span>  
  
 <span data-ttu-id="5c2ed-115">**输入**</span><span class="sxs-lookup"><span data-stu-id="5c2ed-115">**Input**</span></span>  
 <span data-ttu-id="5c2ed-116">使用此区域可选择输入属性和值，以便您稍后能浏览它们影响结果的方式。</span><span class="sxs-lookup"><span data-stu-id="5c2ed-116">Use this area to choose input attributes and values, so that you can later explore how these affect the outcome.</span></span>  
  
|<span data-ttu-id="5c2ed-117">值</span><span class="sxs-lookup"><span data-stu-id="5c2ed-117">Value</span></span>|<span data-ttu-id="5c2ed-118">说明</span><span class="sxs-lookup"><span data-stu-id="5c2ed-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5c2ed-119">**特性**</span><span class="sxs-lookup"><span data-stu-id="5c2ed-119">**Attribute**</span></span>|<span data-ttu-id="5c2ed-120">从列表中选择输入属性。</span><span class="sxs-lookup"><span data-stu-id="5c2ed-120">Choose an input attribute from the list.</span></span> <span data-ttu-id="5c2ed-121">如果将选定内容保留为默认值， **\<All>** 则图表将显示所有输入属性的列表（按其对可预测属性的影响进行排名）。</span><span class="sxs-lookup"><span data-stu-id="5c2ed-121">If you leave the selection as the default, **\<All>**, the chart shows a list of all input attributes, ranked by their impact on the predictable attribute.</span></span>|  
|<span data-ttu-id="5c2ed-122">**值**</span><span class="sxs-lookup"><span data-stu-id="5c2ed-122">**Value**</span></span>|<span data-ttu-id="5c2ed-123">为输入属性选择值。</span><span class="sxs-lookup"><span data-stu-id="5c2ed-123">Choose a value for the input attribute.</span></span>|  
  
 <span data-ttu-id="5c2ed-124">**输出**</span><span class="sxs-lookup"><span data-stu-id="5c2ed-124">**Output**</span></span>  
 <span data-ttu-id="5c2ed-125">使用这些控件可选择一个可预测属性和值，以在条形图中进行分析和比较。</span><span class="sxs-lookup"><span data-stu-id="5c2ed-125">Use these controls to choose a predictable attribute and value to analyze and compare in the bar graph.</span></span> <span data-ttu-id="5c2ed-126">如果您不更改选定内容，则条形图将比较最上面的两个结果状态。</span><span class="sxs-lookup"><span data-stu-id="5c2ed-126">If you do not change the selections, the bar graph compares the top two outcome states.</span></span>  
  
|<span data-ttu-id="5c2ed-127">值</span><span class="sxs-lookup"><span data-stu-id="5c2ed-127">Value</span></span>|<span data-ttu-id="5c2ed-128">说明</span><span class="sxs-lookup"><span data-stu-id="5c2ed-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5c2ed-129">**输出属性**</span><span class="sxs-lookup"><span data-stu-id="5c2ed-129">**Output Attribute**</span></span>|<span data-ttu-id="5c2ed-130">选择一个可预测属性。</span><span class="sxs-lookup"><span data-stu-id="5c2ed-130">Choose a predictable attribute.</span></span> <span data-ttu-id="5c2ed-131">如果您在创建模型时未将列定义为可预测列，则无法在此处添加列。</span><span class="sxs-lookup"><span data-stu-id="5c2ed-131">If you did not define the column as a predictable one when you created the model, you cannot add it here.</span></span>|  
|<span data-ttu-id="5c2ed-132">**值 1**</span><span class="sxs-lookup"><span data-stu-id="5c2ed-132">**Value 1**</span></span>|<span data-ttu-id="5c2ed-133">选择可预测属性的状态以与 **“值 2”** 中所包含状态进行比较。</span><span class="sxs-lookup"><span data-stu-id="5c2ed-133">Choose a state of the predictable attribute to compare to the state that is contained in **Value 2**.</span></span><br /><br /> <span data-ttu-id="5c2ed-134">可以比较任意两个离散或离散化值；但您无法像在其他查看器中一样，将一个值与其补数进行比较。</span><span class="sxs-lookup"><span data-stu-id="5c2ed-134">You can compare any two discrete or discretized values; however, you cannot compare a value to its complement, as you can in other viewers.</span></span>|  
|<span data-ttu-id="5c2ed-135">**值 2**</span><span class="sxs-lookup"><span data-stu-id="5c2ed-135">**Value 2**</span></span>|<span data-ttu-id="5c2ed-136">选择可预测属性的状态以与 **“值 1”** 中所包含状态进行比较。</span><span class="sxs-lookup"><span data-stu-id="5c2ed-136">Select a state of the predictable attribute to compare to the state that is contained in **Value 1**.</span></span>|  
  
 <span data-ttu-id="5c2ed-137">**变量**</span><span class="sxs-lookup"><span data-stu-id="5c2ed-137">**Variables**</span></span>  
 <span data-ttu-id="5c2ed-138">“神经网络”\*\*\*\* 选项卡的此部分包含一个交互条形图，该图会对你选择的输入和结果属性进行响应。</span><span class="sxs-lookup"><span data-stu-id="5c2ed-138">This part of the **Neural Network** tab contains an interactive bar graph, which responds to the selections that you made for input and outcome attributes.</span></span> <span data-ttu-id="5c2ed-139">由于神经网络会计算某个特定值影响特定结果的可能性，因此，您可以选择任何输入组合，并且条形图将显示该组合影响要比较的结果对的方式。</span><span class="sxs-lookup"><span data-stu-id="5c2ed-139">Because a neural network calculates the likelihood that a particular value influences a particular outcome, you can choose any combination of inputs, and the bar chart will display how that combination affects the pair of outcomes that you are comparing.</span></span>  
  
|<span data-ttu-id="5c2ed-140">值</span><span class="sxs-lookup"><span data-stu-id="5c2ed-140">Value</span></span>|<span data-ttu-id="5c2ed-141">说明</span><span class="sxs-lookup"><span data-stu-id="5c2ed-141">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5c2ed-142">**特性**</span><span class="sxs-lookup"><span data-stu-id="5c2ed-142">**Attribute**</span></span>|<span data-ttu-id="5c2ed-143">显示您在 **“属性”** 中选择的输入属性的名称。</span><span class="sxs-lookup"><span data-stu-id="5c2ed-143">Shows the name of the input attribute you selected in **Attribute**.</span></span>|  
|<span data-ttu-id="5c2ed-144">**值**</span><span class="sxs-lookup"><span data-stu-id="5c2ed-144">**Value**</span></span>|<span data-ttu-id="5c2ed-145">显示选定输入属性的值。</span><span class="sxs-lookup"><span data-stu-id="5c2ed-145">Shows the value for the selected input attribute.</span></span>|  
|<span data-ttu-id="5c2ed-146">**有利\<Value 1>**</span><span class="sxs-lookup"><span data-stu-id="5c2ed-146">**Favors \<Value 1>**</span></span>|<span data-ttu-id="5c2ed-147">显示一个条形，该条形指示此特定属性-值组合影响“值 1”\*\*\*\* 中选择的目标结果的程度。</span><span class="sxs-lookup"><span data-stu-id="5c2ed-147">Displays a bar that indicates how much this particular attribute-value combination affects the target outcome chosen in **Value 1**.</span></span>|  
|<span data-ttu-id="5c2ed-148">**有利\<Value 2>**</span><span class="sxs-lookup"><span data-stu-id="5c2ed-148">**Favors \<Value 2>**</span></span>|<span data-ttu-id="5c2ed-149">显示一个条形，该条形指示此特定属性-值组合影响“值 2”\*\*\*\* 中选择的目标结果的程度。</span><span class="sxs-lookup"><span data-stu-id="5c2ed-149">Displays a bar that indicates how much this particular attribute-value combination affects the target outcome chosen in **Value 2**.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5c2ed-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5c2ed-150">See Also</span></span>  
 <span data-ttu-id="5c2ed-151">[数据挖掘算法 &#40;Analysis Services 数据挖掘&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="5c2ed-151">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="5c2ed-152">[挖掘模型查看器 &#40;数据挖掘模型设计器&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="5c2ed-152">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="5c2ed-153">数据挖掘模型查看器</span><span class="sxs-lookup"><span data-stu-id="5c2ed-153">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
