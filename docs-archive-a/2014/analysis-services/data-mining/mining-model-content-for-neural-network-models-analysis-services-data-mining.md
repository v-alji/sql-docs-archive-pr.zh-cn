---
title: " (Analysis Services 数据挖掘) 的神经网络模型的挖掘模型内容 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- output neurons [Analysis Services]
- neural network algorithms [Analysis Services]
- output layer [Data Mining]
- hidden layer
- hidden neurons
- input layer [Data Mining]
- input neurons [Analysis Services]
- mining model content, neural network models
- neural network model [Analysis Services]
ms.assetid: ea21ff9d-857f-475c-bd3d-6d1405bad069
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4f3dc1ff7badfae6c3dfcee9919f5879782764e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589361"
---
# <a name="mining-model-content-for-neural-network-models-analysis-services---data-mining"></a><span data-ttu-id="56e8e-102">神经网络模型的挖掘模型内容（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="56e8e-102">Mining Model Content for Neural Network Models (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="56e8e-103">本主题介绍使用 Microsoft 神经网络算法的模型特有的挖掘模型内容。</span><span class="sxs-lookup"><span data-stu-id="56e8e-103">This topic describes mining model content that is specific to models that use the Microsoft Neural Network algorithm.</span></span> <span data-ttu-id="56e8e-104">有关如何解释所有模型类型共享的统计信息和结构，以及与挖掘模型内容相关的常规术语定义的说明，请参阅 [挖掘模型内容（Analysis Services - 数据挖掘）](mining-model-content-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="56e8e-104">For an explanation of how to interpret statistics and structure shared by all model types, and general definitions of terms related to mining model content, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
## <a name="understanding-the-structure-of-a-neural-network-model"></a><span data-ttu-id="56e8e-105">了解神经网络模型的结构</span><span class="sxs-lookup"><span data-stu-id="56e8e-105">Understanding the Structure of a Neural Network Model</span></span>  
 <span data-ttu-id="56e8e-106">每个神经网络模型都具有一个表示该模型及其元数据的单一父节点，以及一个提供有关输入属性的说明性统计信息的边际统计信息节点 (NODE_TYPE = 24)。</span><span class="sxs-lookup"><span data-stu-id="56e8e-106">Each neural network model has a single parent node that represents the model and its metadata, and a marginal statistics node (NODE_TYPE = 24) that provides descriptive statistics about the input attributes.</span></span> <span data-ttu-id="56e8e-107">边际统计信息节点非常有用，它汇总了输入相关信息，因此您无需从各个节点查询数据。</span><span class="sxs-lookup"><span data-stu-id="56e8e-107">The marginal statistics node is useful because it summarizes information about inputs, so that you do not need to query data from the individual nodes.</span></span>  
  
 <span data-ttu-id="56e8e-108">在这两个节点下面，至少还有两个另外的节点，也可能有更多节点，具体取决于该模型所具有的可预测属性的数目。</span><span class="sxs-lookup"><span data-stu-id="56e8e-108">Underneath these two nodes, there are at least two more nodes, and might be many more, depending on how many predictable attributes the model has.</span></span>  
  
-   <span data-ttu-id="56e8e-109">第一个节点 (NODE_TYPE = 18) 始终表示输入层的顶端节点。</span><span class="sxs-lookup"><span data-stu-id="56e8e-109">The first node (NODE_TYPE = 18) always represents the top node of the input layer.</span></span> <span data-ttu-id="56e8e-110">在该顶端节点下，您可以找到包含实际输入属性及其值的输入节点 (NODE_TYPE = 21)。</span><span class="sxs-lookup"><span data-stu-id="56e8e-110">Beneath this top node, you can find input nodes (NODE_TYPE = 21) that contain the actual input attributes and their values.</span></span>  
  
-   <span data-ttu-id="56e8e-111">每个后续节点各包含一个不同的“子网”\*\*(NODE_TYPE = 17)。</span><span class="sxs-lookup"><span data-stu-id="56e8e-111">Successive nodes each contain a different *subnetwork* (NODE_TYPE = 17).</span></span> <span data-ttu-id="56e8e-112">每个子网始终包含一个隐藏层 (NODE_TYPE = 19) 以及该子网的输出层 (NODE_TYPE = 20)。</span><span class="sxs-lookup"><span data-stu-id="56e8e-112">Each subnetwork always contains a hidden layer (NODE_TYPE = 19), and an output layer (NODE_TYPE = 20) for that subnetwork.</span></span>  
  
 <span data-ttu-id="56e8e-113">![神经网络的模型内容结构](../media/modelcontentstructure-nn.gif "神经网络的模型内容结构")</span><span class="sxs-lookup"><span data-stu-id="56e8e-113">![structure of model content for neural networks](../media/modelcontentstructure-nn.gif "structure of model content for neural networks")</span></span>  
  
 <span data-ttu-id="56e8e-114">输入层中的信息简单明了：每个输入层的顶端节点 (NODE_TYPE = 18) 充当输入节点 (NODE_TYPE = 21) 集合的组织程序。</span><span class="sxs-lookup"><span data-stu-id="56e8e-114">The information in the input layer is straightforward: the top node for each input layer (NODE_TYPE = 18) serves as an organizer for a collection of input nodes (NODE_TYPE = 21).</span></span> <span data-ttu-id="56e8e-115">下表说明了输入节点的内容。</span><span class="sxs-lookup"><span data-stu-id="56e8e-115">The content of the input nodes is described in the following table.</span></span>  
  
 <span data-ttu-id="56e8e-116">每个子网 (NODE_TYPE = 17) 表示输入层对特定可预测属性的影响的分析。</span><span class="sxs-lookup"><span data-stu-id="56e8e-116">Each subnetwork (NODE_TYPE = 17) represents the analysis of the influence of the input layer on a particular predictable attribute.</span></span> <span data-ttu-id="56e8e-117">如果有多个可预测输出，则有多个子网。</span><span class="sxs-lookup"><span data-stu-id="56e8e-117">If there are multiple predictable outputs, there are multiple subnetworks.</span></span> <span data-ttu-id="56e8e-118">每个子网的隐藏层都包含多个隐藏节点 (NODE_TYPE = 22)，这些节点包含有关在该特定隐藏节点结束的每个转换的权重的详细信息。</span><span class="sxs-lookup"><span data-stu-id="56e8e-118">The hidden layer for each subnetwork contains multiple hidden nodes (NODE_TYPE = 22) that contain details about the weights for each transition that ends in that particular hidden node.</span></span>  
  
 <span data-ttu-id="56e8e-119">输出层 (NODE_TYPE = 20) 包含多个输出节点 (NODE_TYPE = 23)，每个输出节点包含可预测属性的非重复值。</span><span class="sxs-lookup"><span data-stu-id="56e8e-119">The output layer (NODE_TYPE = 20) contains output nodes (NODE_TYPE = 23) that each contain distinct values of the predictable attribute.</span></span> <span data-ttu-id="56e8e-120">如果可预测属性为连续数值数据类型，则该属性只有一个输出节点。</span><span class="sxs-lookup"><span data-stu-id="56e8e-120">If the predictable attribute is a continuous numeric data type, there is only one output node for the attribute.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="56e8e-121">逻辑回归算法使用的是一种特殊的神经网络，这种神经网络仅有一个可预测结果并可能有多个输入。</span><span class="sxs-lookup"><span data-stu-id="56e8e-121">The logistic regression algorithm uses a special case of a neural network that has only one predictable outcome and potentially many inputs.</span></span> <span data-ttu-id="56e8e-122">逻辑回归不使用隐藏层。</span><span class="sxs-lookup"><span data-stu-id="56e8e-122">Logistic regression does not use a hidden layer.</span></span>  
  
 <span data-ttu-id="56e8e-123">浏览输入和子网结构的最简便方式是使用 **Microsoft 一般内容树查看器**。</span><span class="sxs-lookup"><span data-stu-id="56e8e-123">The easiest way to explore the structure of the inputs and subnetworks is to use the **Microsoft Generic Content Tree viewer**.</span></span> <span data-ttu-id="56e8e-124">您可以单击并展开任何节点，查看其子节点，或者查看该节点中包含的权重和其他统计信息。</span><span class="sxs-lookup"><span data-stu-id="56e8e-124">You can click any node to expand it and see the child nodes, or view the weights and other statistics that is contained in the node.</span></span>  
  
 <span data-ttu-id="56e8e-125">若要使用数据和查看模型如何将输入与输出关联，请使用 **Microsoft 神经网络查看器**。</span><span class="sxs-lookup"><span data-stu-id="56e8e-125">To work with the data and see how the model correlates inputs with outputs, use the **Microsoft Neural Network Viewer**.</span></span> <span data-ttu-id="56e8e-126">使用此自定义查看器，您可以筛选输入属性及其值，并以图形方式查看它们如何影响输出。</span><span class="sxs-lookup"><span data-stu-id="56e8e-126">By using this custom viewer, you can filter on input attributes and their values, and graphically see how they affect the outputs.</span></span> <span data-ttu-id="56e8e-127">查看器中的工具提示显示与每对输入和输出值关联的概率和提升。</span><span class="sxs-lookup"><span data-stu-id="56e8e-127">The tooltips in the viewer show you the probability and lift associated with each pair of inputs and output values.</span></span> <span data-ttu-id="56e8e-128">有关详细信息，请参阅 [使用 Microsoft 神经网络查看器浏览模型](browse-a-model-using-the-microsoft-neural-network-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="56e8e-128">For more information, see [Browse a Model Using the Microsoft Neural Network Viewer](browse-a-model-using-the-microsoft-neural-network-viewer.md).</span></span>  
  
## <a name="model-content-for-a-neural-network-model"></a><span data-ttu-id="56e8e-129">神经网络模型的模型内容</span><span class="sxs-lookup"><span data-stu-id="56e8e-129">Model Content for a Neural Network Model</span></span>  
 <span data-ttu-id="56e8e-130">本部分提供的详细信息和示例仅针对挖掘模型内容中与神经网络有特殊关系的列。</span><span class="sxs-lookup"><span data-stu-id="56e8e-130">This section provides detail and examples only for those columns in the mining model content that have particular relevance for neural networks.</span></span> <span data-ttu-id="56e8e-131">有关此处未涵盖的架构行集中的通用列（如 MODEL_CATALOG 和 MODEL_NAME）的信息或有关挖掘模型术语的说明，请参阅 [挖掘模型内容（Analysis Services - 数据挖掘）](mining-model-content-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="56e8e-131">For information about general-purpose columns in the schema rowset, such as MODEL_CATALOG and MODEL_NAME, that are not described here, or for explanations of mining model terminology, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="56e8e-132">MODEL_CATALOG</span><span class="sxs-lookup"><span data-stu-id="56e8e-132">MODEL_CATALOG</span></span>  
 <span data-ttu-id="56e8e-133">存储模型的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="56e8e-133">Name of the database where the model is stored.</span></span>  
  
 <span data-ttu-id="56e8e-134">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="56e8e-134">MODEL_NAME</span></span>  
 <span data-ttu-id="56e8e-135">模型的名称。</span><span class="sxs-lookup"><span data-stu-id="56e8e-135">Name of the model.</span></span>  
  
 <span data-ttu-id="56e8e-136">ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="56e8e-136">ATTRIBUTE_NAME</span></span>  
 <span data-ttu-id="56e8e-137">与此节点对应的属性的名称。</span><span class="sxs-lookup"><span data-stu-id="56e8e-137">The names of the attributes that correspond to this node.</span></span>  
  
|<span data-ttu-id="56e8e-138">节点</span><span class="sxs-lookup"><span data-stu-id="56e8e-138">Node</span></span>|<span data-ttu-id="56e8e-139">内容</span><span class="sxs-lookup"><span data-stu-id="56e8e-139">Content</span></span>|  
|----------|-------------|  
|<span data-ttu-id="56e8e-140">模型根</span><span class="sxs-lookup"><span data-stu-id="56e8e-140">Model root</span></span>|<span data-ttu-id="56e8e-141">空</span><span class="sxs-lookup"><span data-stu-id="56e8e-141">Blank</span></span>|  
|<span data-ttu-id="56e8e-142">边际统计信息</span><span class="sxs-lookup"><span data-stu-id="56e8e-142">Marginal statistics</span></span>|<span data-ttu-id="56e8e-143">空</span><span class="sxs-lookup"><span data-stu-id="56e8e-143">Blank</span></span>|  
|<span data-ttu-id="56e8e-144">输入层</span><span class="sxs-lookup"><span data-stu-id="56e8e-144">Input layer</span></span>|<span data-ttu-id="56e8e-145">空</span><span class="sxs-lookup"><span data-stu-id="56e8e-145">Blank</span></span>|  
|<span data-ttu-id="56e8e-146">输入节点</span><span class="sxs-lookup"><span data-stu-id="56e8e-146">Input node</span></span>|<span data-ttu-id="56e8e-147">输入属性名称</span><span class="sxs-lookup"><span data-stu-id="56e8e-147">Input attribute name</span></span>|  
|<span data-ttu-id="56e8e-148">隐藏层</span><span class="sxs-lookup"><span data-stu-id="56e8e-148">Hidden layer</span></span>|<span data-ttu-id="56e8e-149">空</span><span class="sxs-lookup"><span data-stu-id="56e8e-149">Blank</span></span>|  
|<span data-ttu-id="56e8e-150">隐藏节点</span><span class="sxs-lookup"><span data-stu-id="56e8e-150">Hidden node</span></span>|<span data-ttu-id="56e8e-151">空</span><span class="sxs-lookup"><span data-stu-id="56e8e-151">Blank</span></span>|  
|<span data-ttu-id="56e8e-152">输出层</span><span class="sxs-lookup"><span data-stu-id="56e8e-152">Output layer</span></span>|<span data-ttu-id="56e8e-153">空</span><span class="sxs-lookup"><span data-stu-id="56e8e-153">Blank</span></span>|  
|<span data-ttu-id="56e8e-154">输出节点</span><span class="sxs-lookup"><span data-stu-id="56e8e-154">Output node</span></span>|<span data-ttu-id="56e8e-155">输出属性名称</span><span class="sxs-lookup"><span data-stu-id="56e8e-155">Output attribute name</span></span>|  
  
 <span data-ttu-id="56e8e-156">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="56e8e-156">NODE_NAME</span></span>  
 <span data-ttu-id="56e8e-157">节点的名称。</span><span class="sxs-lookup"><span data-stu-id="56e8e-157">The name of the node.</span></span> <span data-ttu-id="56e8e-158">该列包含的值与 NODE_UNIQUE_NAME 列相同。</span><span class="sxs-lookup"><span data-stu-id="56e8e-158">This column contains the same value as NODE_UNIQUE_NAME.</span></span>  
  
 <span data-ttu-id="56e8e-159">NODE_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="56e8e-159">NODE_UNIQUE_NAME</span></span>  
 <span data-ttu-id="56e8e-160">节点的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="56e8e-160">The unique name of the node.</span></span>  
  
 <span data-ttu-id="56e8e-161">有关名称和 ID 如何提供有关模型的结构信息的详细信息，请参阅 [使用节点名称和 ID](#bkmk_NodeIDs)部分。</span><span class="sxs-lookup"><span data-stu-id="56e8e-161">For more information about how the names and IDs provide structural information about the model, see the section, [Using Node Names and IDs](#bkmk_NodeIDs).</span></span>  
  
 <span data-ttu-id="56e8e-162">NODE_TYPE</span><span class="sxs-lookup"><span data-stu-id="56e8e-162">NODE_TYPE</span></span>  
 <span data-ttu-id="56e8e-163">神经网络模型输出以下节点类型：</span><span class="sxs-lookup"><span data-stu-id="56e8e-163">A neural network model outputs the following node types:</span></span>  
  
|<span data-ttu-id="56e8e-164">节点类型 ID</span><span class="sxs-lookup"><span data-stu-id="56e8e-164">Node Type ID</span></span>|<span data-ttu-id="56e8e-165">说明</span><span class="sxs-lookup"><span data-stu-id="56e8e-165">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="56e8e-166">1</span><span class="sxs-lookup"><span data-stu-id="56e8e-166">1</span></span>|<span data-ttu-id="56e8e-167">模型。</span><span class="sxs-lookup"><span data-stu-id="56e8e-167">Model.</span></span>|  
|<span data-ttu-id="56e8e-168">17</span><span class="sxs-lookup"><span data-stu-id="56e8e-168">17</span></span>|<span data-ttu-id="56e8e-169">子网的组织程序节点。</span><span class="sxs-lookup"><span data-stu-id="56e8e-169">Organizer node for the subnetwork.</span></span>|  
|<span data-ttu-id="56e8e-170">18</span><span class="sxs-lookup"><span data-stu-id="56e8e-170">18</span></span>|<span data-ttu-id="56e8e-171">输入层的组织程序节点。</span><span class="sxs-lookup"><span data-stu-id="56e8e-171">Organizer node for the input layer.</span></span>|  
|<span data-ttu-id="56e8e-172">19</span><span class="sxs-lookup"><span data-stu-id="56e8e-172">19</span></span>|<span data-ttu-id="56e8e-173">隐藏层的组织程序节点。</span><span class="sxs-lookup"><span data-stu-id="56e8e-173">Organizer node for the hidden layer.</span></span>|  
|<span data-ttu-id="56e8e-174">20</span><span class="sxs-lookup"><span data-stu-id="56e8e-174">20</span></span>|<span data-ttu-id="56e8e-175">输出层的组织程序节点。</span><span class="sxs-lookup"><span data-stu-id="56e8e-175">Organizer node for the output layer.</span></span>|  
|<span data-ttu-id="56e8e-176">21</span><span class="sxs-lookup"><span data-stu-id="56e8e-176">21</span></span>|<span data-ttu-id="56e8e-177">输入属性节点。</span><span class="sxs-lookup"><span data-stu-id="56e8e-177">Input attribute node.</span></span>|  
|<span data-ttu-id="56e8e-178">22</span><span class="sxs-lookup"><span data-stu-id="56e8e-178">22</span></span>|<span data-ttu-id="56e8e-179">隐藏层节点</span><span class="sxs-lookup"><span data-stu-id="56e8e-179">Hidden layer node</span></span>|  
|<span data-ttu-id="56e8e-180">23</span><span class="sxs-lookup"><span data-stu-id="56e8e-180">23</span></span>|<span data-ttu-id="56e8e-181">输出属性节点。</span><span class="sxs-lookup"><span data-stu-id="56e8e-181">Output attribute node.</span></span>|  
|<span data-ttu-id="56e8e-182">24</span><span class="sxs-lookup"><span data-stu-id="56e8e-182">24</span></span>|<span data-ttu-id="56e8e-183">边际统计信息节点。</span><span class="sxs-lookup"><span data-stu-id="56e8e-183">Marginal statistics node.</span></span>|  
  
 <span data-ttu-id="56e8e-184">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="56e8e-184">NODE_CAPTION</span></span>  
 <span data-ttu-id="56e8e-185">与节点关联的标签或标题。</span><span class="sxs-lookup"><span data-stu-id="56e8e-185">A label or a caption associated with the node.</span></span> <span data-ttu-id="56e8e-186">在神经网络模型中，始终为空白。</span><span class="sxs-lookup"><span data-stu-id="56e8e-186">In neural network models, always blank.</span></span>  
  
 <span data-ttu-id="56e8e-187">CHILDREN_CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="56e8e-187">CHILDREN_CARDINALITY</span></span>  
 <span data-ttu-id="56e8e-188">对节点所具有的子节点数的估计。</span><span class="sxs-lookup"><span data-stu-id="56e8e-188">An estimate of the number of children that the node has.</span></span>  
  
|<span data-ttu-id="56e8e-189">节点</span><span class="sxs-lookup"><span data-stu-id="56e8e-189">Node</span></span>|<span data-ttu-id="56e8e-190">内容</span><span class="sxs-lookup"><span data-stu-id="56e8e-190">Content</span></span>|  
|----------|-------------|  
|<span data-ttu-id="56e8e-191">模型根</span><span class="sxs-lookup"><span data-stu-id="56e8e-191">Model root</span></span>|<span data-ttu-id="56e8e-192">指示子节点的计数，其中至少包括 1 个网络，1 个必需边际节点和 1 个必需输入层。</span><span class="sxs-lookup"><span data-stu-id="56e8e-192">Indicates the count of child nodes, which includes at least 1 network, 1 required marginal node, and 1 required input layer.</span></span> <span data-ttu-id="56e8e-193">例如，如果值为 5，则具有 3 个子网。</span><span class="sxs-lookup"><span data-stu-id="56e8e-193">For example, if the value is 5, there are 3 subnetworks.</span></span>|  
|<span data-ttu-id="56e8e-194">边际统计信息</span><span class="sxs-lookup"><span data-stu-id="56e8e-194">Marginal statistics</span></span>|<span data-ttu-id="56e8e-195">始终为 0。</span><span class="sxs-lookup"><span data-stu-id="56e8e-195">Always 0.</span></span>|  
|<span data-ttu-id="56e8e-196">输入层</span><span class="sxs-lookup"><span data-stu-id="56e8e-196">Input layer</span></span>|<span data-ttu-id="56e8e-197">指示模型使用的输入属性值对的数目。</span><span class="sxs-lookup"><span data-stu-id="56e8e-197">Indicates the number of input attribute-values pairs that were used by the model.</span></span>|  
|<span data-ttu-id="56e8e-198">输入节点</span><span class="sxs-lookup"><span data-stu-id="56e8e-198">Input node</span></span>|<span data-ttu-id="56e8e-199">始终为 0。</span><span class="sxs-lookup"><span data-stu-id="56e8e-199">Always 0.</span></span>|  
|<span data-ttu-id="56e8e-200">隐藏层</span><span class="sxs-lookup"><span data-stu-id="56e8e-200">Hidden layer</span></span>|<span data-ttu-id="56e8e-201">指示该模型创建的隐藏节点的数目。</span><span class="sxs-lookup"><span data-stu-id="56e8e-201">Indicates the number of hidden nodes that were created by the model.</span></span>|  
|<span data-ttu-id="56e8e-202">隐藏节点</span><span class="sxs-lookup"><span data-stu-id="56e8e-202">Hidden node</span></span>|<span data-ttu-id="56e8e-203">始终为 0。</span><span class="sxs-lookup"><span data-stu-id="56e8e-203">Always 0.</span></span>|  
|<span data-ttu-id="56e8e-204">输出层</span><span class="sxs-lookup"><span data-stu-id="56e8e-204">Output layer</span></span>|<span data-ttu-id="56e8e-205">指示输出值的数目。</span><span class="sxs-lookup"><span data-stu-id="56e8e-205">Indicates the number of output values.</span></span>|  
|<span data-ttu-id="56e8e-206">输出节点</span><span class="sxs-lookup"><span data-stu-id="56e8e-206">Output node</span></span>|<span data-ttu-id="56e8e-207">始终为 0。</span><span class="sxs-lookup"><span data-stu-id="56e8e-207">Always 0.</span></span>|  
  
 <span data-ttu-id="56e8e-208">PARENT_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="56e8e-208">PARENT_UNIQUE_NAME</span></span>  
 <span data-ttu-id="56e8e-209">节点的父节点的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="56e8e-209">The unique name of the node's parent.</span></span> <span data-ttu-id="56e8e-210">根级别上的任何节点均返回 NULL。</span><span class="sxs-lookup"><span data-stu-id="56e8e-210">NULL is returned for any nodes at the root level.</span></span>  
  
 <span data-ttu-id="56e8e-211">有关名称和 ID 如何提供有关模型的结构信息的详细信息，请参阅 [使用节点名称和 ID](#bkmk_NodeIDs)部分。</span><span class="sxs-lookup"><span data-stu-id="56e8e-211">For more information about how the names and IDs provide structural information about the model, see the section, [Using Node Names and IDs](#bkmk_NodeIDs).</span></span>  
  
 <span data-ttu-id="56e8e-212">NODE_DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="56e8e-212">NODE_DESCRIPTION</span></span>  
 <span data-ttu-id="56e8e-213">节点的用户友好说明。</span><span class="sxs-lookup"><span data-stu-id="56e8e-213">A user-friendly description of the node.</span></span>  
  
|<span data-ttu-id="56e8e-214">节点</span><span class="sxs-lookup"><span data-stu-id="56e8e-214">Node</span></span>|<span data-ttu-id="56e8e-215">内容</span><span class="sxs-lookup"><span data-stu-id="56e8e-215">Content</span></span>|  
|----------|-------------|  
|<span data-ttu-id="56e8e-216">模型根</span><span class="sxs-lookup"><span data-stu-id="56e8e-216">Model root</span></span>|<span data-ttu-id="56e8e-217">空</span><span class="sxs-lookup"><span data-stu-id="56e8e-217">Blank</span></span>|  
|<span data-ttu-id="56e8e-218">边际统计信息</span><span class="sxs-lookup"><span data-stu-id="56e8e-218">Marginal statistics</span></span>|<span data-ttu-id="56e8e-219">空</span><span class="sxs-lookup"><span data-stu-id="56e8e-219">Blank</span></span>|  
|<span data-ttu-id="56e8e-220">输入层</span><span class="sxs-lookup"><span data-stu-id="56e8e-220">Input layer</span></span>|<span data-ttu-id="56e8e-221">空</span><span class="sxs-lookup"><span data-stu-id="56e8e-221">Blank</span></span>|  
|<span data-ttu-id="56e8e-222">输入节点</span><span class="sxs-lookup"><span data-stu-id="56e8e-222">Input node</span></span>|<span data-ttu-id="56e8e-223">输入属性名称</span><span class="sxs-lookup"><span data-stu-id="56e8e-223">Input attribute name</span></span>|  
|<span data-ttu-id="56e8e-224">隐藏层</span><span class="sxs-lookup"><span data-stu-id="56e8e-224">Hidden layer</span></span>|<span data-ttu-id="56e8e-225">空</span><span class="sxs-lookup"><span data-stu-id="56e8e-225">Blank</span></span>|  
|<span data-ttu-id="56e8e-226">隐藏节点</span><span class="sxs-lookup"><span data-stu-id="56e8e-226">Hidden node</span></span>|<span data-ttu-id="56e8e-227">指示该隐藏节点在隐藏节点列表中的顺序的整数。</span><span class="sxs-lookup"><span data-stu-id="56e8e-227">Integer that indicates the sequence of the hidden node in the list of hidden nodes.</span></span>|  
|<span data-ttu-id="56e8e-228">输出层</span><span class="sxs-lookup"><span data-stu-id="56e8e-228">Output layer</span></span>|<span data-ttu-id="56e8e-229">空</span><span class="sxs-lookup"><span data-stu-id="56e8e-229">Blank</span></span>|  
|<span data-ttu-id="56e8e-230">输出节点</span><span class="sxs-lookup"><span data-stu-id="56e8e-230">Output node</span></span>|<span data-ttu-id="56e8e-231">如果输出属性是连续的，则包含输出属性的名称。</span><span class="sxs-lookup"><span data-stu-id="56e8e-231">If the output attribute is continuous, contains the name of the output attribute.</span></span><br /><br /> <span data-ttu-id="56e8e-232">如果输出属性是离散或离散化属性，则包含属性的名称和值。</span><span class="sxs-lookup"><span data-stu-id="56e8e-232">If the output attribute is discrete or discretized, contains the name of the attribute and the value.</span></span>|  
  
 <span data-ttu-id="56e8e-233">NODE_RULE</span><span class="sxs-lookup"><span data-stu-id="56e8e-233">NODE_RULE</span></span>  
 <span data-ttu-id="56e8e-234">嵌入节点的规则的 XML 说明。</span><span class="sxs-lookup"><span data-stu-id="56e8e-234">An XML description of the rule that is embedded in the node.</span></span>  
  
|<span data-ttu-id="56e8e-235">节点</span><span class="sxs-lookup"><span data-stu-id="56e8e-235">Node</span></span>|<span data-ttu-id="56e8e-236">内容</span><span class="sxs-lookup"><span data-stu-id="56e8e-236">Content</span></span>|  
|----------|-------------|  
|<span data-ttu-id="56e8e-237">模型根</span><span class="sxs-lookup"><span data-stu-id="56e8e-237">Model root</span></span>|<span data-ttu-id="56e8e-238">空</span><span class="sxs-lookup"><span data-stu-id="56e8e-238">Blank</span></span>|  
|<span data-ttu-id="56e8e-239">边际统计信息</span><span class="sxs-lookup"><span data-stu-id="56e8e-239">Marginal statistics</span></span>|<span data-ttu-id="56e8e-240">空</span><span class="sxs-lookup"><span data-stu-id="56e8e-240">Blank</span></span>|  
|<span data-ttu-id="56e8e-241">输入层</span><span class="sxs-lookup"><span data-stu-id="56e8e-241">Input layer</span></span>|<span data-ttu-id="56e8e-242">空</span><span class="sxs-lookup"><span data-stu-id="56e8e-242">Blank</span></span>|  
|<span data-ttu-id="56e8e-243">输入节点</span><span class="sxs-lookup"><span data-stu-id="56e8e-243">Input node</span></span>|<span data-ttu-id="56e8e-244">包含与 NODE_DESCRIPTION 列相同的信息的 XML 片段。</span><span class="sxs-lookup"><span data-stu-id="56e8e-244">An XML fragment that contains the same information as the NODE_DESCRIPTION column.</span></span>|  
|<span data-ttu-id="56e8e-245">隐藏层</span><span class="sxs-lookup"><span data-stu-id="56e8e-245">Hidden layer</span></span>|<span data-ttu-id="56e8e-246">空</span><span class="sxs-lookup"><span data-stu-id="56e8e-246">Blank</span></span>|  
|<span data-ttu-id="56e8e-247">隐藏节点</span><span class="sxs-lookup"><span data-stu-id="56e8e-247">Hidden node</span></span>|<span data-ttu-id="56e8e-248">指示该隐藏节点在隐藏节点列表中的顺序的整数。</span><span class="sxs-lookup"><span data-stu-id="56e8e-248">Integer that indicates the sequence of the hidden node in the list of hidden nodes.</span></span>|  
|<span data-ttu-id="56e8e-249">输出层</span><span class="sxs-lookup"><span data-stu-id="56e8e-249">Output layer</span></span>|<span data-ttu-id="56e8e-250">空</span><span class="sxs-lookup"><span data-stu-id="56e8e-250">Blank</span></span>|  
|<span data-ttu-id="56e8e-251">输出节点</span><span class="sxs-lookup"><span data-stu-id="56e8e-251">Output node</span></span>|<span data-ttu-id="56e8e-252">包含与 NODE_DESCRIPTION 列相同的信息的 XML 片段。</span><span class="sxs-lookup"><span data-stu-id="56e8e-252">An XML fragment that contains the same information as the NODE_DESCRIPTION column.</span></span>|  
  
 <span data-ttu-id="56e8e-253">MARGINAL_RULE</span><span class="sxs-lookup"><span data-stu-id="56e8e-253">MARGINAL_RULE</span></span>  
 <span data-ttu-id="56e8e-254">对于神经网络模型，始终为空白。</span><span class="sxs-lookup"><span data-stu-id="56e8e-254">For neural network models, always blank.</span></span>  
  
 <span data-ttu-id="56e8e-255">NODE_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="56e8e-255">NODE_PROBABILITY</span></span>  
 <span data-ttu-id="56e8e-256">与此节点相关联的概率。</span><span class="sxs-lookup"><span data-stu-id="56e8e-256">The probability associated with this node.</span></span> <span data-ttu-id="56e8e-257">对于神经网络模型，始终为 0。</span><span class="sxs-lookup"><span data-stu-id="56e8e-257">For neural network models, always 0.</span></span>  
  
 <span data-ttu-id="56e8e-258">MARGINAL_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="56e8e-258">MARGINAL_PROBABILITY</span></span>  
 <span data-ttu-id="56e8e-259">从父节点到达该节点的概率。</span><span class="sxs-lookup"><span data-stu-id="56e8e-259">The probability of reaching the node from the parent node.</span></span> <span data-ttu-id="56e8e-260">对于神经网络模型，始终为 0。</span><span class="sxs-lookup"><span data-stu-id="56e8e-260">For neural network models, always 0.</span></span>  
  
 <span data-ttu-id="56e8e-261">NODE_DISTRIBUTION</span><span class="sxs-lookup"><span data-stu-id="56e8e-261">NODE_DISTRIBUTION</span></span>  
 <span data-ttu-id="56e8e-262">包含节点的统计信息的嵌套表。</span><span class="sxs-lookup"><span data-stu-id="56e8e-262">A nested table that contains statistical information for the node.</span></span> <span data-ttu-id="56e8e-263">有关该表中每个节点类型的内容的详细信息，请参阅 [了解 NODE_DISTRIBUTION 表](#bkmk_NodeDistTable)部分。</span><span class="sxs-lookup"><span data-stu-id="56e8e-263">For detailed information about the contents of this table for each node type, see the section, [Understanding the NODE_DISTRIBUTION Table](#bkmk_NodeDistTable).</span></span>  
  
 <span data-ttu-id="56e8e-264">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="56e8e-264">NODE_SUPPORT</span></span>  
 <span data-ttu-id="56e8e-265">对于神经网络模型，始终为 0。</span><span class="sxs-lookup"><span data-stu-id="56e8e-265">For neural network models, always 0.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="56e8e-266">由于该模型类型的输出不是概率性的，因此支持概率始终为 0。</span><span class="sxs-lookup"><span data-stu-id="56e8e-266">Support probabilities are always 0 because the output of this model type is not probabilistic.</span></span> <span data-ttu-id="56e8e-267">只有权重才对该算法有意义；因此，该算法不会计算概率、支持或方差。</span><span class="sxs-lookup"><span data-stu-id="56e8e-267">Only the weights are meaningful for the algorithm; therefore, the algorithm does not compute probability, support, or variance.</span></span>  
  
 <span data-ttu-id="56e8e-268">若要获取定型事例中对特定值的支持信息，请参阅边际统计信息节点。</span><span class="sxs-lookup"><span data-stu-id="56e8e-268">To get information about the support in the training cases for specific values, see the marginal statistics node.</span></span>  
  
 <span data-ttu-id="56e8e-269">MSOLAP_MODEL_COLUMN</span><span class="sxs-lookup"><span data-stu-id="56e8e-269">MSOLAP_MODEL_COLUMN</span></span>  
 |<span data-ttu-id="56e8e-270">节点</span><span class="sxs-lookup"><span data-stu-id="56e8e-270">Node</span></span>|<span data-ttu-id="56e8e-271">内容</span><span class="sxs-lookup"><span data-stu-id="56e8e-271">Content</span></span>|  
|----------|-------------|  
|<span data-ttu-id="56e8e-272">模型根</span><span class="sxs-lookup"><span data-stu-id="56e8e-272">Model root</span></span>|<span data-ttu-id="56e8e-273">空</span><span class="sxs-lookup"><span data-stu-id="56e8e-273">Blank</span></span>|  
|<span data-ttu-id="56e8e-274">边际统计信息</span><span class="sxs-lookup"><span data-stu-id="56e8e-274">Marginal statistics</span></span>|<span data-ttu-id="56e8e-275">空</span><span class="sxs-lookup"><span data-stu-id="56e8e-275">Blank</span></span>|  
|<span data-ttu-id="56e8e-276">输入层</span><span class="sxs-lookup"><span data-stu-id="56e8e-276">Input layer</span></span>|<span data-ttu-id="56e8e-277">空</span><span class="sxs-lookup"><span data-stu-id="56e8e-277">Blank</span></span>|  
|<span data-ttu-id="56e8e-278">输入节点</span><span class="sxs-lookup"><span data-stu-id="56e8e-278">Input node</span></span>|<span data-ttu-id="56e8e-279">输入属性名称。</span><span class="sxs-lookup"><span data-stu-id="56e8e-279">Input attribute name.</span></span>|  
|<span data-ttu-id="56e8e-280">隐藏层</span><span class="sxs-lookup"><span data-stu-id="56e8e-280">Hidden layer</span></span>|<span data-ttu-id="56e8e-281">空</span><span class="sxs-lookup"><span data-stu-id="56e8e-281">Blank</span></span>|  
|<span data-ttu-id="56e8e-282">隐藏节点</span><span class="sxs-lookup"><span data-stu-id="56e8e-282">Hidden node</span></span>|<span data-ttu-id="56e8e-283">空</span><span class="sxs-lookup"><span data-stu-id="56e8e-283">Blank</span></span>|  
|<span data-ttu-id="56e8e-284">输出层</span><span class="sxs-lookup"><span data-stu-id="56e8e-284">Output layer</span></span>|<span data-ttu-id="56e8e-285">空</span><span class="sxs-lookup"><span data-stu-id="56e8e-285">Blank</span></span>|  
|<span data-ttu-id="56e8e-286">输出节点</span><span class="sxs-lookup"><span data-stu-id="56e8e-286">Output node</span></span>|<span data-ttu-id="56e8e-287">输入属性名称。</span><span class="sxs-lookup"><span data-stu-id="56e8e-287">Input attribute name.</span></span>|  
  
 <span data-ttu-id="56e8e-288">MSOLAP_NODE_SCORE</span><span class="sxs-lookup"><span data-stu-id="56e8e-288">MSOLAP_NODE_SCORE</span></span>  
 <span data-ttu-id="56e8e-289">对于神经网络模型，始终为 0。</span><span class="sxs-lookup"><span data-stu-id="56e8e-289">For a neural network model, always 0.</span></span>  
  
 <span data-ttu-id="56e8e-290">MSOLAP_NODE_SHORT_CAPTION</span><span class="sxs-lookup"><span data-stu-id="56e8e-290">MSOLAP_NODE_SHORT_CAPTION</span></span>  
 <span data-ttu-id="56e8e-291">对于神经网络模型，始终为空白。</span><span class="sxs-lookup"><span data-stu-id="56e8e-291">For neural network models, always blank.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56e8e-292">备注</span><span class="sxs-lookup"><span data-stu-id="56e8e-292">Remarks</span></span>  
 <span data-ttu-id="56e8e-293">定型神经网络模型的目的是确定与从输入到中点、再从中点到终结点的每个转换关联的权重。</span><span class="sxs-lookup"><span data-stu-id="56e8e-293">The purpose of training a neural network model is to determine the weights that are associated with each transition from an input to a midpoint, and from a midpoint to an endpoint.</span></span> <span data-ttu-id="56e8e-294">因此，该模型的输入层的主要存在目的是存储用于生成该模型的实际值。</span><span class="sxs-lookup"><span data-stu-id="56e8e-294">Therefore, the input layer of the model principally exists to store the actual values that were used to build the model.</span></span> <span data-ttu-id="56e8e-295">隐藏层存储计算的权重，并提供回指到输入属性的指针。</span><span class="sxs-lookup"><span data-stu-id="56e8e-295">The hidden layer stores the weights that were computed, and provides pointers back to the input attributes.</span></span> <span data-ttu-id="56e8e-296">输出层存储可预测值，并提供回指到隐藏层的中点的指针。</span><span class="sxs-lookup"><span data-stu-id="56e8e-296">The output layer stores the predictable values, and also provides pointers back to the midpoints in the hidden layer.</span></span>  
  
##  <a name="using-node-names-and-ids"></a><a name="bkmk_NodeIDs"></a><span data-ttu-id="56e8e-297">使用节点名称和 Id</span><span class="sxs-lookup"><span data-stu-id="56e8e-297">Using Node Names and IDs</span></span>  
 <span data-ttu-id="56e8e-298">神经网络模型中各节点的命名方式提供有关节点的类型的其他信息，以便于将隐藏层与输入层相关联，并将输出层与隐藏层相关联。</span><span class="sxs-lookup"><span data-stu-id="56e8e-298">The naming of the nodes in a neural network model provides additional information about the type of node, to make it easier to relate the hidden layer to the input layer, and the output layer to the hidden layer.</span></span> <span data-ttu-id="56e8e-299">下表给出了为每层中的节点分配 ID 的约定。</span><span class="sxs-lookup"><span data-stu-id="56e8e-299">The following table shows the convention for the IDs that are assigned to nodes in each layer.</span></span>  
  
|<span data-ttu-id="56e8e-300">节点类型</span><span class="sxs-lookup"><span data-stu-id="56e8e-300">Node Type</span></span>|<span data-ttu-id="56e8e-301">节点 ID 约定</span><span class="sxs-lookup"><span data-stu-id="56e8e-301">Convention for node ID</span></span>|  
|---------------|----------------------------|  
|<span data-ttu-id="56e8e-302">模型根 (1)</span><span class="sxs-lookup"><span data-stu-id="56e8e-302">Model root (1)</span></span>|<span data-ttu-id="56e8e-303">00000000000000000.</span><span class="sxs-lookup"><span data-stu-id="56e8e-303">00000000000000000.</span></span>|  
|<span data-ttu-id="56e8e-304">边际统计信息节点 (24)</span><span class="sxs-lookup"><span data-stu-id="56e8e-304">Marginal statistics node (24)</span></span>|<span data-ttu-id="56e8e-305">10000000000000000</span><span class="sxs-lookup"><span data-stu-id="56e8e-305">10000000000000000</span></span>|  
|<span data-ttu-id="56e8e-306">输入层 (18)</span><span class="sxs-lookup"><span data-stu-id="56e8e-306">Input layer (18)</span></span>|<span data-ttu-id="56e8e-307">30000000000000000</span><span class="sxs-lookup"><span data-stu-id="56e8e-307">30000000000000000</span></span>|  
|<span data-ttu-id="56e8e-308">输入节点 (21)</span><span class="sxs-lookup"><span data-stu-id="56e8e-308">Input node (21)</span></span>|<span data-ttu-id="56e8e-309">以 60000000000000000 作为开头</span><span class="sxs-lookup"><span data-stu-id="56e8e-309">Starts at 60000000000000000</span></span>|  
|<span data-ttu-id="56e8e-310">子网 (17)</span><span class="sxs-lookup"><span data-stu-id="56e8e-310">Subnetwork (17)</span></span>|<span data-ttu-id="56e8e-311">20000000000000000</span><span class="sxs-lookup"><span data-stu-id="56e8e-311">20000000000000000</span></span>|  
|<span data-ttu-id="56e8e-312">隐藏层 (19)</span><span class="sxs-lookup"><span data-stu-id="56e8e-312">Hidden layer (19)</span></span>|<span data-ttu-id="56e8e-313">40000000000000000</span><span class="sxs-lookup"><span data-stu-id="56e8e-313">40000000000000000</span></span>|  
|<span data-ttu-id="56e8e-314">隐藏节点 (22)</span><span class="sxs-lookup"><span data-stu-id="56e8e-314">Hidden node (22)</span></span>|<span data-ttu-id="56e8e-315">以 70000000000000000 作为开头</span><span class="sxs-lookup"><span data-stu-id="56e8e-315">Starts at 70000000000000000</span></span>|  
|<span data-ttu-id="56e8e-316">输出层 (20)</span><span class="sxs-lookup"><span data-stu-id="56e8e-316">Output layer (20)</span></span>|<span data-ttu-id="56e8e-317">50000000000000000</span><span class="sxs-lookup"><span data-stu-id="56e8e-317">50000000000000000</span></span>|  
|<span data-ttu-id="56e8e-318">输出节点 (23)</span><span class="sxs-lookup"><span data-stu-id="56e8e-318">Output node (23)</span></span>|<span data-ttu-id="56e8e-319">以 80000000000000000 作为开头</span><span class="sxs-lookup"><span data-stu-id="56e8e-319">Starts at 80000000000000000</span></span>|  
  
 <span data-ttu-id="56e8e-320">通过查看隐藏节点 (NODE_TYPE = 22) 中的 NODE_DISTRIBUTION 表，您可以确定哪些输入属性与特定隐藏层节点关联。</span><span class="sxs-lookup"><span data-stu-id="56e8e-320">You can determine which input attributes are related to a specific hidden layer node by viewing the NODE_DISTRIBUTION table in the hidden node (NODE_TYPE = 22).</span></span> <span data-ttu-id="56e8e-321">NODE_DISTRIBUTION 表的每个行包含输入属性节点的 ID。</span><span class="sxs-lookup"><span data-stu-id="56e8e-321">Each row of the NODE_DISTRIBUTION table contains the ID of an input attribute node.</span></span>  
  
 <span data-ttu-id="56e8e-322">类似地，通过查看输出节点 (NODE_TYPE = 23) 中的 NODE_DISTRIBUTION 表，您可以确定哪些隐藏层与输出属性关联。</span><span class="sxs-lookup"><span data-stu-id="56e8e-322">Similarly, you can determine which hidden layers are related to an output attribute by viewing the NODE_DISTRIBUTION table in the output node (NODE_TYPE = 23).</span></span> <span data-ttu-id="56e8e-323">NODE_DISTRIBUTION 表的每个行包含隐藏层节点的 ID 和相关系数。</span><span class="sxs-lookup"><span data-stu-id="56e8e-323">Each row of the NODE_DISTRIBUTION table contains the ID of a hidden layer node, together with the related coefficient.</span></span>  
  
##  <a name="interpreting-the-information-in-the-node_distribution-table"></a><a name="bkmk_NodeDistTable"></a> <span data-ttu-id="56e8e-324">解释 NODE_DISTRIBUTION 表中的信息</span><span class="sxs-lookup"><span data-stu-id="56e8e-324">Interpreting the Information in the NODE_DISTRIBUTION Table</span></span>  
 <span data-ttu-id="56e8e-325">NODE_DISTRIBUTION 表在某些节点中可以为空。</span><span class="sxs-lookup"><span data-stu-id="56e8e-325">The NODE_DISTRIBUTION table can be empty in some nodes.</span></span> <span data-ttu-id="56e8e-326">但是，对于输入节点、隐藏层节点和输出节点，NODE_DISTRIBUTION 表存储模型的重要相关信息。</span><span class="sxs-lookup"><span data-stu-id="56e8e-326">However, for input nodes, hidden layer nodes, and output nodes, the NODE_DISTRIBUTION table stores important and interesting information about the model.</span></span> <span data-ttu-id="56e8e-327">为帮助您解释该信息，NODE_DISTRIBUTION 表为每个行包含一个 VALUETYPE 列，指示 ATTRIBUTE_VALUE 列中的值是离散 (4)、离散化 (5) 还是连续 (3) 值。</span><span class="sxs-lookup"><span data-stu-id="56e8e-327">To help you interpret this information, the NODE_DISTRIBUTION table contains a VALUETYPE column for each row that tells you whether the value in the ATTRIBUTE_VALUE column is Discrete (4), Discretized (5), or Continuous (3).</span></span>  
  
### <a name="input-nodes"></a><span data-ttu-id="56e8e-328">输入节点</span><span class="sxs-lookup"><span data-stu-id="56e8e-328">Input Nodes</span></span>  
 <span data-ttu-id="56e8e-329">输入层为模型中使用的属性的每个值各包含一个节点。</span><span class="sxs-lookup"><span data-stu-id="56e8e-329">The input layer contains a node for each value of the attribute that was used in the model.</span></span>  
  
 <span data-ttu-id="56e8e-330">**离散属性：** 输入节点仅在 ATTRIBUTE_NAME 和 ATTRIBUTE_VALUE 列中存储属性的名称和值。</span><span class="sxs-lookup"><span data-stu-id="56e8e-330">**Discrete attribute:** The input node stores only the name of the attribute and its value in the ATTRIBUTE_NAME and ATTRIBUTE_VALUE columns.</span></span> <span data-ttu-id="56e8e-331">例如，如果列为 [Work Shift]，则为模型中使用的该列的每个值（例如 AM 和 PM）创建一个单独的节点。</span><span class="sxs-lookup"><span data-stu-id="56e8e-331">For example, if [Work Shift] is the column, a separate node is created for each value of that column that was used in the model, such as AM and PM.</span></span> <span data-ttu-id="56e8e-332">每个节点的 NODE_DISTRIBUTION 表仅列出属性的当前值。</span><span class="sxs-lookup"><span data-stu-id="56e8e-332">The NODE_DISTRIBUTION table for each node lists only the current value of the attribute.</span></span>  
  
 <span data-ttu-id="56e8e-333">**离散化数值属性：** 输入节点存储属性的名称和值，该值可以是一个范围或一个特定值。</span><span class="sxs-lookup"><span data-stu-id="56e8e-333">**Discretized numeric attribute:** The input node stores the name of the attribute, and the value, which can be a range or a specific value.</span></span> <span data-ttu-id="56e8e-334">所有值均通过表达式表示，例如将 [Time Per Issue] 的值表示为“77.4 - 87.4”或“< 64.0”。</span><span class="sxs-lookup"><span data-stu-id="56e8e-334">All values are represented by expressions, such as '77.4 - 87.4' or ' < 64.0' for the value of the [Time Per Issue].</span></span> <span data-ttu-id="56e8e-335">每个节点的 NODE_DISTRIBUTION 表仅列出属性的当前值。</span><span class="sxs-lookup"><span data-stu-id="56e8e-335">The NODE_DISTRIBUTION table for each node lists only the current value of the attribute.</span></span>  
  
 <span data-ttu-id="56e8e-336">**连续属性：** 输入节点存储属性的平均值。</span><span class="sxs-lookup"><span data-stu-id="56e8e-336">**Continuous attribute:** The input node stores the mean value of the attribute.</span></span> <span data-ttu-id="56e8e-337">每个节点的 NODE_DISTRIBUTION 表仅列出属性的当前值。</span><span class="sxs-lookup"><span data-stu-id="56e8e-337">The NODE_DISTRIBUTION table for each node lists only the current value of the attribute.</span></span>  
  
### <a name="hidden-layer-nodes"></a><span data-ttu-id="56e8e-338">隐藏层节点</span><span class="sxs-lookup"><span data-stu-id="56e8e-338">Hidden Layer Nodes</span></span>  
 <span data-ttu-id="56e8e-339">隐藏层包含可变数目的节点。</span><span class="sxs-lookup"><span data-stu-id="56e8e-339">The hidden layer contains a variable number of nodes.</span></span> <span data-ttu-id="56e8e-340">在每个节点中，NODE_DISTRIBUTION 表包含从隐藏层到输入层中的节点的映射。</span><span class="sxs-lookup"><span data-stu-id="56e8e-340">In each node, the NODE_DISTRIBUTION table contains mappings from the hidden layer to the nodes in the input layer.</span></span> <span data-ttu-id="56e8e-341">ATTRIBUTE_NAME 列包含与输入层中的节点对应的节点 ID。</span><span class="sxs-lookup"><span data-stu-id="56e8e-341">The ATTRIBUTE_NAME column contains a node ID that corresponds to a node in the input layer.</span></span> <span data-ttu-id="56e8e-342">ATTRIBUTE_VALUE 列包含与输入节点和隐藏层节点的该组合关联的权重。</span><span class="sxs-lookup"><span data-stu-id="56e8e-342">The ATTRIBUTE_VALUE column contains the weight associated with that combination of input node and hidden layer node.</span></span> <span data-ttu-id="56e8e-343">表中的最后一行包含表示隐藏层中的该隐藏节点的权重的系数。</span><span class="sxs-lookup"><span data-stu-id="56e8e-343">The last row in the table contains a coefficient that represents the weight of that hidden node in the hidden layer.</span></span>  
  
### <a name="output-nodes"></a><span data-ttu-id="56e8e-344">输出节点</span><span class="sxs-lookup"><span data-stu-id="56e8e-344">Output Nodes</span></span>  
 <span data-ttu-id="56e8e-345">输出层为模型中使用的每个输出值各包含一个输出节点。</span><span class="sxs-lookup"><span data-stu-id="56e8e-345">The output layer contains one output node for each output value that was used in the model.</span></span> <span data-ttu-id="56e8e-346">在每个节点中，NODE_DISTRIBUTION 表包含从输出层到隐藏层中的节点的映射。</span><span class="sxs-lookup"><span data-stu-id="56e8e-346">In each node, the NODE_DISTRIBUTION table contains mappings from the output layer to the nodes in the hidden layer.</span></span> <span data-ttu-id="56e8e-347">ATTRIBUTE_NAME 列包含与隐藏层中的节点对应的节点 ID。</span><span class="sxs-lookup"><span data-stu-id="56e8e-347">The ATTRIBUTE_NAME column contains a node ID that corresponds to a node in the hidden layer.</span></span> <span data-ttu-id="56e8e-348">ATTRIBUTE_VALUE 列包含与输出节点和隐藏层节点的该组合关联的权重。</span><span class="sxs-lookup"><span data-stu-id="56e8e-348">The ATTRIBUTE_VALUE column contains the weight associated with that combination of output node and hidden layer node.</span></span>  
  
 <span data-ttu-id="56e8e-349">NODE_DISTRIBUTION 表根据属性类型包含以下其他信息：</span><span class="sxs-lookup"><span data-stu-id="56e8e-349">The NODE_DISTRIBUTION table has the following additional information, depending on whether the type of the attribute:</span></span>  
  
 <span data-ttu-id="56e8e-350">**离散属性：** NODE_DISTRIBUTION 表的最后两行包含整个节点的系数和属性的当前值。</span><span class="sxs-lookup"><span data-stu-id="56e8e-350">**Discrete attribute:** The final two rows of the NODE_DISTRIBUTION table contain a coefficient for the node as a whole, and the current value of the attribute.</span></span>  
  
 <span data-ttu-id="56e8e-351">**离散化数值属性：** 除非该属性的值是一个值范围，否则该属性与离散属性相同。</span><span class="sxs-lookup"><span data-stu-id="56e8e-351">**Discretized numeric attribute:** Identical to discrete attributes, except that the value of the attribute is a range of values.</span></span>  
  
 <span data-ttu-id="56e8e-352">**连续属性：** NODE_DISTRIBUTION 表的最后两行包含该属性的平均值、整个节点的系数和系数的方差。</span><span class="sxs-lookup"><span data-stu-id="56e8e-352">**Continuous attribute:** The final two rows of the NODE_DISTRIBUTION table contain the mean of the attribute, the coefficient for the node as a whole, and the variance of the coefficient.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56e8e-353">另请参阅</span><span class="sxs-lookup"><span data-stu-id="56e8e-353">See Also</span></span>  
 <span data-ttu-id="56e8e-354">[Microsoft 神经网络算法](microsoft-neural-network-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="56e8e-354">[Microsoft Neural Network Algorithm](microsoft-neural-network-algorithm.md) </span></span>  
 <span data-ttu-id="56e8e-355">[Microsoft 神经网络算法技术参考](microsoft-neural-network-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="56e8e-355">[Microsoft Neural Network Algorithm Technical Reference](microsoft-neural-network-algorithm-technical-reference.md) </span></span>  
 [<span data-ttu-id="56e8e-356">神经网络模型查询示例</span><span class="sxs-lookup"><span data-stu-id="56e8e-356">Neural Network Model Query Examples</span></span>](neural-network-model-query-examples.md)  
  
  
