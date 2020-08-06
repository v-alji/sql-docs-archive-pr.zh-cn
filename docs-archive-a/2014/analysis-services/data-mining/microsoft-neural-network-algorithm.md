---
title: Microsoft 神经网络算法 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- training neural networks
- output neurons [Analysis Services]
- algorithms [data mining]
- neural network algorithms [Analysis Services]
- neurons [Analysis Services]
- classification algorithms [Analysis Services]
- neural networks
- multilayer perceptron network of neurons [Analysis Services]
- hidden neurons
- Back-Propagated Delta Rule network
- input neurons [Analysis Services]
- regression algorithms [Analysis Services]
ms.assetid: 61eb4861-8a6a-4214-a4b8-1dd278ad7a68
author: minewiskan
ms.author: owend
ms.openlocfilehash: 389df77299bbf357e1b8b0f0695f03a74420f786
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577090"
---
# <a name="microsoft-neural-network-algorithm"></a><span data-ttu-id="8baf4-102">Microsoft Neural Network Algorithm</span><span class="sxs-lookup"><span data-stu-id="8baf4-102">Microsoft Neural Network Algorithm</span></span>
  <span data-ttu-id="8baf4-103">在中 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ， [!INCLUDE[msCoName](../../includes/msconame-md.md)] 神经网络算法将输入属性的每个可能状态与可预测属性的每个可能状态相结合，并使用定型数据来计算概率。</span><span class="sxs-lookup"><span data-stu-id="8baf4-103">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm combines each possible state of the input attribute with each possible state of the predictable attribute, and uses the training data to calculate probabilities.</span></span> <span data-ttu-id="8baf4-104">之后，可以根据输入属性，将这些概率用于分类或回归，并预测被预测属性的结果。</span><span class="sxs-lookup"><span data-stu-id="8baf4-104">You can later use these probabilities for classification or regression, and to predict an outcome of the predicted attribute, based on the input attributes.</span></span>  
  
 <span data-ttu-id="8baf4-105">使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 神经元网络算法构造的挖掘模型可以包含多个网络，这取决于用于输入和预测的列的数量，或者取决于仅用于预测的列的数量。</span><span class="sxs-lookup"><span data-stu-id="8baf4-105">A mining model that is constructed with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm can contain multiple networks, depending on the number of columns that are used for both input and prediction, or that are used only for prediction.</span></span> <span data-ttu-id="8baf4-106">一个挖掘模型包含的网络数取决于挖掘模型使用的输入列和预测列包含的状态数。</span><span class="sxs-lookup"><span data-stu-id="8baf4-106">The number of networks that a single mining model contains depends on the number of states that are contained by the input columns and predictable columns that the mining model uses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8baf4-107">示例</span><span class="sxs-lookup"><span data-stu-id="8baf4-107">Example</span></span>  
 <span data-ttu-id="8baf4-108">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 神经网络算法对分析复杂输入数据（如来自制造或商业流程的数据）很有用；对于那些提供了大量定型数据，但使用其他算法很难为其派生规则的业务问题，这种算法也很有用。</span><span class="sxs-lookup"><span data-stu-id="8baf4-108">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm is useful for analyzing complex input data, such as from a manufacturing or commercial process, or business problems for which a significant quantity of training data is available but for which rules cannot be easily derived by using other algorithms.</span></span>  
  
 <span data-ttu-id="8baf4-109">在以下情况下，建议使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 神经网络算法：</span><span class="sxs-lookup"><span data-stu-id="8baf4-109">Suggested scenarios for using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm include the following:</span></span>  
  
-   <span data-ttu-id="8baf4-110">营销和促销分析，如评估直接邮件促销或一个电台广告活动的成功情况。</span><span class="sxs-lookup"><span data-stu-id="8baf4-110">Marketing and promotion analysis, such as measuring the success of a direct mail promotion or a radio advertising campaign.</span></span>  
  
-   <span data-ttu-id="8baf4-111">根据历史数据预测股票升降、汇率浮动或其他频繁变动的金融信息。</span><span class="sxs-lookup"><span data-stu-id="8baf4-111">Predicting stock movement, currency fluctuation, or other highly fluid financial information from historical data.</span></span>  
  
-   <span data-ttu-id="8baf4-112">分析制造和工业流程。</span><span class="sxs-lookup"><span data-stu-id="8baf4-112">Analyzing manufacturing and industrial processes.</span></span>  
  
-   <span data-ttu-id="8baf4-113">文本挖掘。</span><span class="sxs-lookup"><span data-stu-id="8baf4-113">Text mining.</span></span>  
  
-   <span data-ttu-id="8baf4-114">分析多个输入和相对较少的输出之间的复杂关系的任何预测模型。</span><span class="sxs-lookup"><span data-stu-id="8baf4-114">Any prediction model that analyzes complex relationships between many inputs and relatively fewer outputs.</span></span>  
  
## <a name="how-the-algorithm-works"></a><span data-ttu-id="8baf4-115">算法的原理</span><span class="sxs-lookup"><span data-stu-id="8baf4-115">How the Algorithm Works</span></span>  
 <span data-ttu-id="8baf4-116">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 神经网络算法创建由多至三层神经元组成的网络。</span><span class="sxs-lookup"><span data-stu-id="8baf4-116">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm creates a network that is composed of up to three layers of neurons.</span></span> <span data-ttu-id="8baf4-117">这些层分别是输入层、可选隐藏层和输出层。</span><span class="sxs-lookup"><span data-stu-id="8baf4-117">These layers are an input layer, an optional hidden layer, and an output layer.</span></span>  
  
 <span data-ttu-id="8baf4-118">**输入层：** 输入神经元定义了数据挖掘模型的所有输入属性值及其概率。</span><span class="sxs-lookup"><span data-stu-id="8baf4-118">**Input layer:** Input neurons define all the input attribute values for the data mining model, and their probabilities.</span></span>  
  
 <span data-ttu-id="8baf4-119">**隐藏层：** 隐藏神经元接收来自输入神经元的输入，并向输出神经元提供输出。</span><span class="sxs-lookup"><span data-stu-id="8baf4-119">**Hidden layer:** Hidden neurons receive inputs from input neurons and provide outputs to output neurons.</span></span> <span data-ttu-id="8baf4-120">隐藏层是向各种输入概率分配权重的位置。</span><span class="sxs-lookup"><span data-stu-id="8baf4-120">The hidden layer is where the various probabilities of the inputs are assigned weights.</span></span> <span data-ttu-id="8baf4-121">权重说明某一特定输入对于隐藏神经元的相关性或重要性。</span><span class="sxs-lookup"><span data-stu-id="8baf4-121">A weight describes the relevance or importance of a particular input to the hidden neuron.</span></span> <span data-ttu-id="8baf4-122">输入所分配的权重越大，则输入的值越重要。</span><span class="sxs-lookup"><span data-stu-id="8baf4-122">The greater the weight that is assigned to an input, the more important the value of that input is.</span></span> <span data-ttu-id="8baf4-123">权重可为负值，表示输入抑制而不是促进某一特定结果。</span><span class="sxs-lookup"><span data-stu-id="8baf4-123">Weights can be negative, which means that the input can inhibit, rather than favor, a specific result.</span></span>  
  
 <span data-ttu-id="8baf4-124">**输出层：** 输出神经元代表数据挖掘模型的可预测属性值。</span><span class="sxs-lookup"><span data-stu-id="8baf4-124">**Output layer:** Output neurons represent predictable attribute values for the data mining model.</span></span>  
  
 <span data-ttu-id="8baf4-125">有关如何构造和评价输入层、隐藏层和输出层的详细说明，请参阅 [Microsoft 神经网络算法技术参考](microsoft-neural-network-algorithm-technical-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="8baf4-125">For a detailed explanation of how the input, hidden, and output layers are constructed and scored, see [Microsoft Neural Network Algorithm Technical Reference](microsoft-neural-network-algorithm-technical-reference.md).</span></span>  
  
## <a name="data-required-for-neural-network-models"></a><span data-ttu-id="8baf4-126">神经网络模型所需的数据</span><span class="sxs-lookup"><span data-stu-id="8baf4-126">Data Required for Neural Network Models</span></span>  
 <span data-ttu-id="8baf4-127">神经网络模型必须包含一个键列、一个或多个输入列以及一个或多个可预测列。</span><span class="sxs-lookup"><span data-stu-id="8baf4-127">A neural network model must contain a key column, one or more input columns, and one or more predictable columns.</span></span>  
  
 <span data-ttu-id="8baf4-128">使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 神经网络算法的数据挖掘模型与为该算法的可用参数指定的值紧密相关。</span><span class="sxs-lookup"><span data-stu-id="8baf4-128">Data mining models that use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm are heavily influenced by the values that you specify for the parameters that are available to the algorithm.</span></span> <span data-ttu-id="8baf4-129">这些参数定义如何对数据进行采样、数据在每个列中的分布方式或预期分布方式以及何时调用功能选择以限制在最终模型中使用的值。</span><span class="sxs-lookup"><span data-stu-id="8baf4-129">The parameters define how data is sampled, how data is distributed or expected to be distributed in each column, and when feature selection is invoked to limit the values that are used in the final model.</span></span>  
  
 <span data-ttu-id="8baf4-130">有关设置参数以自定义模型行为的详细信息，请参阅 [Microsoft 神经网络算法技术参考](microsoft-neural-network-algorithm-technical-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="8baf4-130">For more information about setting parameters to customize model behavior, see [Microsoft Neural Network Algorithm Technical Reference](microsoft-neural-network-algorithm-technical-reference.md).</span></span>  
  
## <a name="viewing-a-neural-network-model"></a><span data-ttu-id="8baf4-131">查看神经网络模型</span><span class="sxs-lookup"><span data-stu-id="8baf4-131">Viewing a Neural Network Model</span></span>  
 <span data-ttu-id="8baf4-132">您可以使用 **Microsoft 神经网络查看器**处理数据，并查看模型如何将输入与输出关联。</span><span class="sxs-lookup"><span data-stu-id="8baf4-132">To work with the data and see how the model correlates inputs with outputs, you can use the **Microsoft Neural Network Viewer**.</span></span> <span data-ttu-id="8baf4-133">使用此自定义查看器，您可以筛选输入属性及其值，并查看显示它们如何影响输出的图形。</span><span class="sxs-lookup"><span data-stu-id="8baf4-133">With this custom viewer, you can filter on input attributes and their values, and see graphs that show how they affect the outputs.</span></span> <span data-ttu-id="8baf4-134">查看器中的工具提示显示与每对输入和输出值关联的概率和提升。</span><span class="sxs-lookup"><span data-stu-id="8baf4-134">The tooltips in the viewer show you the probability and lift associated with each pair of input and output values.</span></span> <span data-ttu-id="8baf4-135">有关详细信息，请参阅 [使用 Microsoft 神经网络查看器浏览模型](browse-a-model-using-the-microsoft-neural-network-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="8baf4-135">For more information, see [Browse a Model Using the Microsoft Neural Network Viewer](browse-a-model-using-the-microsoft-neural-network-viewer.md).</span></span>  
  
 <span data-ttu-id="8baf4-136">浏览模型结构的最简便方式是使用 **Microsoft 一般内容树查看器**。</span><span class="sxs-lookup"><span data-stu-id="8baf4-136">The easiest way to explore the structure of the model is to use the **Microsoft Generic Content Tree Viewer**.</span></span> <span data-ttu-id="8baf4-137">您可以查看输入、输出以及模型创建的网络，并单击展开任何节点，查看与输入、输出或隐藏层节点相关的统计信息。</span><span class="sxs-lookup"><span data-stu-id="8baf4-137">You can view the inputs, outputs, and networks created by the model, and click on any node to expand it and see statistics related to the input, output, or hidden layer nodes.</span></span> <span data-ttu-id="8baf4-138">有关详细信息，请参阅 [使用 Microsoft 一般内容树查看器浏览模型](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="8baf4-138">For more information, see [Browse a Model Using the Microsoft Generic Content Tree Viewer](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md).</span></span>  
  
## <a name="creating-predictions"></a><span data-ttu-id="8baf4-139">创建预测</span><span class="sxs-lookup"><span data-stu-id="8baf4-139">Creating Predictions</span></span>  
 <span data-ttu-id="8baf4-140">处理完模型后，可以使用每个节点中存储的网络和权重来做出预测。</span><span class="sxs-lookup"><span data-stu-id="8baf4-140">After the model has been processed, you can use the network and the weights stored within each node to make predictions.</span></span> <span data-ttu-id="8baf4-141">神经网络模型支持回归、关联和分类分析，因此，每个预测的含义可能各不相同。</span><span class="sxs-lookup"><span data-stu-id="8baf4-141">A neural network model supports regression, association, and classification analysis, Therefore, the meaning of each prediction might be different.</span></span> <span data-ttu-id="8baf4-142">此外，还可以查询模型自身，以查看找到的相关性并检索相关统计信息。</span><span class="sxs-lookup"><span data-stu-id="8baf4-142">You can also query the model itself, to review the correlations that were found and retrieve related statistics.</span></span> <span data-ttu-id="8baf4-143">有关如何创建针对神经网络模型的查询的示例，请参阅 [神经网络模型查询示例](neural-network-model-query-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="8baf4-143">For examples of how to create queries against a neural network model, see [Neural Network Model Query Examples](neural-network-model-query-examples.md).</span></span>  
  
 <span data-ttu-id="8baf4-144">有关如何创建针对数据挖掘模型的查询的信息，请参阅 [数据挖掘查询](data-mining-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="8baf4-144">For general information about how to create a query on a data mining model, see [Data Mining Queries](data-mining-queries.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8baf4-145">备注</span><span class="sxs-lookup"><span data-stu-id="8baf4-145">Remarks</span></span>  
  
-   <span data-ttu-id="8baf4-146">不支持钻取或数据挖掘维度，</span><span class="sxs-lookup"><span data-stu-id="8baf4-146">Does not support drillthrough or data mining dimensions.</span></span> <span data-ttu-id="8baf4-147">这是因为挖掘模型中节点的结构不一定直接与基础数据对应。</span><span class="sxs-lookup"><span data-stu-id="8baf4-147">This is because the structure of the nodes in the mining model does not necessarily correspond directly to the underlying data.</span></span>  
  
-   <span data-ttu-id="8baf4-148">不支持以预测模型标记语言 (PMML) 格式创建模型。</span><span class="sxs-lookup"><span data-stu-id="8baf4-148">Does not support the creation of models in Predictive Model Markup Language (PMML) format.</span></span>  
  
-   <span data-ttu-id="8baf4-149">支持使用 OLAP 挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="8baf4-149">Supports the use of OLAP mining models.</span></span>  
  
-   <span data-ttu-id="8baf4-150">不支持创建数据挖掘维度。</span><span class="sxs-lookup"><span data-stu-id="8baf4-150">Does not support the creation of data mining dimensions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8baf4-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8baf4-151">See Also</span></span>  
 <span data-ttu-id="8baf4-152">[Microsoft 神经网络算法技术参考](microsoft-neural-network-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="8baf4-152">[Microsoft Neural Network Algorithm Technical Reference](microsoft-neural-network-algorithm-technical-reference.md) </span></span>  
 <span data-ttu-id="8baf4-153">[&#40;Analysis Services 数据挖掘的神经网络模型的挖掘模型内容&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="8baf4-153">[Mining Model Content for Neural Network Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="8baf4-154">[神经网络模型查询示例](neural-network-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="8baf4-154">[Neural Network Model Query Examples](neural-network-model-query-examples.md) </span></span>  
 [<span data-ttu-id="8baf4-155">Microsoft 逻辑回归算法</span><span class="sxs-lookup"><span data-stu-id="8baf4-155">Microsoft Logistic Regression Algorithm</span></span>](microsoft-logistic-regression-algorithm.md)  
  
  
