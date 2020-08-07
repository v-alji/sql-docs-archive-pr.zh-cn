---
title: " (Analysis Services 数据挖掘) 的逻辑回归模型的挖掘模型内容 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- logistic regression [Analysis Services]
- mining model content, logistic regression models
- regression algorithms [Analysis Services]
ms.assetid: 69cc0b86-e8bc-4d6c-903e-85724f5c0396
author: minewiskan
ms.author: owend
ms.openlocfilehash: 84964c59a63d41f0985001a2ae384fa298096927
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589368"
---
# <a name="mining-model-content-for-logistic-regression-models-analysis-services---data-mining"></a><span data-ttu-id="62b0d-102">逻辑回归模型的挖掘模型内容（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="62b0d-102">Mining Model Content for Logistic Regression Models (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="62b0d-103">本主题介绍使用 Microsoft 逻辑回归算法的模型特有的挖掘模型内容。</span><span class="sxs-lookup"><span data-stu-id="62b0d-103">This topic describes mining model content that is specific to models that use the Microsoft Logistic Regression algorithm.</span></span> <span data-ttu-id="62b0d-104">有关如何解释所有模型类型共享的统计信息和结构，以及与挖掘模型内容相关的常规术语定义的说明，请参阅 [挖掘模型内容（Analysis Services - 数据挖掘）](mining-model-content-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="62b0d-104">For an explanation of how to interpret statistics and structure shared by all model types, and general definitions of terms related to mining model content, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
## <a name="understanding-the-structure-of-a-logistic-regression-model"></a><span data-ttu-id="62b0d-105">了解逻辑回归模型的结构</span><span class="sxs-lookup"><span data-stu-id="62b0d-105">Understanding the Structure of a Logistic Regression Model</span></span>  
 <span data-ttu-id="62b0d-106">逻辑回归模型是使用带有约束模型以消除隐藏节点的参数的 Microsoft 神经网络算法创建的。</span><span class="sxs-lookup"><span data-stu-id="62b0d-106">A logistic regression model is created by using the Microsoft Neural Network algorithm with parameters that constrain the model to eliminate the hidden node.</span></span> <span data-ttu-id="62b0d-107">因此，逻辑回归模型的总体结构几乎与神经网络的总体结构相同：每个模型都具有一个表示该模型及其元数据的单一父节点，以及一个提供有关在该模型中使用的输入的说明性统计信息的特殊边际统计信息节点 (NODE_TYPE = 24)。</span><span class="sxs-lookup"><span data-stu-id="62b0d-107">Therefore, the overall structure of a logistic regression model is almost identical to that of a neural network: each model has a single parent node that represents the model and its metadata, and a special marginal statistics node (NODE_TYPE = 24) that provides descriptive statistics about the inputs used in the model.</span></span>  
  
 <span data-ttu-id="62b0d-108">此外，该模型还包含每个可预测属性的子网 (NODE_TYPE = 17)。</span><span class="sxs-lookup"><span data-stu-id="62b0d-108">Additionally, the model contains a subnetwork (NODE_TYPE = 17) for each predictable attribute.</span></span> <span data-ttu-id="62b0d-109">和在神经网络模型中一样，每个子网始终包含两个分支：其中一个分支用于输入层，而另一个分支则包含网络的隐藏层 (NODE_TYPE = 19) 和输出层 (NODE_TYPE = 20)。</span><span class="sxs-lookup"><span data-stu-id="62b0d-109">Just like in a neural network model, each subnetwork always contains two branches: one for the input layer, and another branch that contains the hidden layer (NODE_TYPE = 19) and the output layer (NODE_TYPE = 20) for the network.</span></span> <span data-ttu-id="62b0d-110">如果将多个属性指定为仅预测，则可以对这些属性使用相同的子网。</span><span class="sxs-lookup"><span data-stu-id="62b0d-110">The same subnetwork may be used for multiple attributes if they are specified as predict-only.</span></span> <span data-ttu-id="62b0d-111">同时作为输入的可预测属性可能不会显示在相同子网中。</span><span class="sxs-lookup"><span data-stu-id="62b0d-111">Predictable attributes that are also inputs may not appear in the same subnetwork.</span></span>  
  
 <span data-ttu-id="62b0d-112">但是，在逻辑回归模型中，表示隐藏层的节点为空，该节点没有任何子级。</span><span class="sxs-lookup"><span data-stu-id="62b0d-112">However, in a logistic regression model, the node that represents the hidden layer is empty, and has no children.</span></span> <span data-ttu-id="62b0d-113">因此，该模型包含表示单个输出 (NODE_TYPE = 23) 和单个输入 (NODE_TYPE = 21) 的节点，但不包含任何单个隐藏节点。</span><span class="sxs-lookup"><span data-stu-id="62b0d-113">Therefore the model contains nodes that represent individual outputs (NODE_TYPE = 23) and individual inputs (NODE_TYPE = 21) but no individual hidden nodes.</span></span>  
  
 <span data-ttu-id="62b0d-114">![Logisitc 回归模型的内容结构](../media/skt-modelcontentstructure-logregc.gif "Logisitc 回归模型的内容结构")</span><span class="sxs-lookup"><span data-stu-id="62b0d-114">![structure of content for logisitc regression model](../media/skt-modelcontentstructure-logregc.gif "structure of content for logisitc regression model")</span></span>  
  
 <span data-ttu-id="62b0d-115">默认情况下，逻辑回归模型在 **Microsoft 神经网络查看器**中显示。</span><span class="sxs-lookup"><span data-stu-id="62b0d-115">By default, a logistic regression model is displayed in the **Microsoft Neural Network Viewer**.</span></span> <span data-ttu-id="62b0d-116">使用此自定义查看器，您可以筛选输入属性及其值，并以图形方式查看它们如何影响输出。</span><span class="sxs-lookup"><span data-stu-id="62b0d-116">With this custom viewer, you can filter on input attributes and their values, and graphically see how they affect the outputs.</span></span> <span data-ttu-id="62b0d-117">查看器中的工具提示显示与每对输入和输出值关联的概率和提升。</span><span class="sxs-lookup"><span data-stu-id="62b0d-117">The tooltips in the viewer show you the probability and lift associated with each pair of inputs and output values.</span></span> <span data-ttu-id="62b0d-118">有关详细信息，请参阅 [使用 Microsoft 神经网络查看器浏览模型](browse-a-model-using-the-microsoft-neural-network-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="62b0d-118">For more information, see [Browse a Model Using the Microsoft Neural Network Viewer](browse-a-model-using-the-microsoft-neural-network-viewer.md).</span></span>  
  
 <span data-ttu-id="62b0d-119">若要浏览输入和子网的结构，并查看详细统计信息，您可以使用 Microsoft 一般内容树查看器。</span><span class="sxs-lookup"><span data-stu-id="62b0d-119">To explore the structure of the inputs and subnetworks, and to see detailed statistics, you can use the Microsoft Generic Content Tree viewer.</span></span> <span data-ttu-id="62b0d-120">您可以单击并展开任何节点，查看其子节点，或者查看该节点中包含的权重和其他统计信息。</span><span class="sxs-lookup"><span data-stu-id="62b0d-120">You can click on any node to expand it and see the child nodes, or view the weights and other statistics contained in the node.</span></span>  
  
## <a name="model-content-for-a-logistic-regression-model"></a><span data-ttu-id="62b0d-121">逻辑回归模型的模型内容</span><span class="sxs-lookup"><span data-stu-id="62b0d-121">Model Content for a Logistic Regression Model</span></span>  
 <span data-ttu-id="62b0d-122">本部分提供的详细信息和示例仅针对挖掘模型内容中与逻辑回归有特殊关系的列。</span><span class="sxs-lookup"><span data-stu-id="62b0d-122">This section provides detail and examples only for those columns in the mining model content that have particular relevance for logistic regression.</span></span> <span data-ttu-id="62b0d-123">模型内容与神经网络模型的内容几乎相同，但是为方便起见，此表可能将重复应用于神经网络模型的说明。</span><span class="sxs-lookup"><span data-stu-id="62b0d-123">The model content is almost identical to that of a neural network model, but descriptions that apply to neural network models may be repeated in this table for convenience.</span></span>  
  
 <span data-ttu-id="62b0d-124">有关此处未涵盖的架构行集中的通用列（如 MODEL_CATALOG 和 MODEL_NAME）的信息或有关挖掘模型术语的说明，请参阅 [挖掘模型内容（Analysis Services - 数据挖掘）](mining-model-content-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="62b0d-124">For information about general-purpose columns in the schema rowset, such as MODEL_CATALOG and MODEL_NAME, that are not described here, or for explanations of mining model terminology, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="62b0d-125">MODEL_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62b0d-125">MODEL_CATALOG</span></span>  
 <span data-ttu-id="62b0d-126">存储模型的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="62b0d-126">Name of the database where the model is stored.</span></span>  
  
 <span data-ttu-id="62b0d-127">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="62b0d-127">MODEL_NAME</span></span>  
 <span data-ttu-id="62b0d-128">模型的名称。</span><span class="sxs-lookup"><span data-stu-id="62b0d-128">Name of the model.</span></span>  
  
 <span data-ttu-id="62b0d-129">ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="62b0d-129">ATTRIBUTE_NAME</span></span>  
 <span data-ttu-id="62b0d-130">与此节点对应的属性的名称。</span><span class="sxs-lookup"><span data-stu-id="62b0d-130">The names of the attribute that corresponds to this node.</span></span>  
  
|<span data-ttu-id="62b0d-131">节点</span><span class="sxs-lookup"><span data-stu-id="62b0d-131">Node</span></span>|<span data-ttu-id="62b0d-132">内容</span><span class="sxs-lookup"><span data-stu-id="62b0d-132">Content</span></span>|  
|----------|-------------|  
|<span data-ttu-id="62b0d-133">模型根</span><span class="sxs-lookup"><span data-stu-id="62b0d-133">Model root</span></span>|<span data-ttu-id="62b0d-134">空</span><span class="sxs-lookup"><span data-stu-id="62b0d-134">Blank</span></span>|  
|<span data-ttu-id="62b0d-135">边际统计信息</span><span class="sxs-lookup"><span data-stu-id="62b0d-135">Marginal statistics</span></span>|<span data-ttu-id="62b0d-136">空</span><span class="sxs-lookup"><span data-stu-id="62b0d-136">Blank</span></span>|  
|<span data-ttu-id="62b0d-137">输入层</span><span class="sxs-lookup"><span data-stu-id="62b0d-137">Input layer</span></span>|<span data-ttu-id="62b0d-138">空</span><span class="sxs-lookup"><span data-stu-id="62b0d-138">Blank</span></span>|  
|<span data-ttu-id="62b0d-139">输入节点</span><span class="sxs-lookup"><span data-stu-id="62b0d-139">Input node</span></span>|<span data-ttu-id="62b0d-140">输入属性名称</span><span class="sxs-lookup"><span data-stu-id="62b0d-140">Input attribute name</span></span>|  
|<span data-ttu-id="62b0d-141">隐藏层</span><span class="sxs-lookup"><span data-stu-id="62b0d-141">Hidden layer</span></span>|<span data-ttu-id="62b0d-142">空</span><span class="sxs-lookup"><span data-stu-id="62b0d-142">Blank</span></span>|  
|<span data-ttu-id="62b0d-143">输出层</span><span class="sxs-lookup"><span data-stu-id="62b0d-143">Output layer</span></span>|<span data-ttu-id="62b0d-144">空</span><span class="sxs-lookup"><span data-stu-id="62b0d-144">Blank</span></span>|  
|<span data-ttu-id="62b0d-145">输出节点</span><span class="sxs-lookup"><span data-stu-id="62b0d-145">Output node</span></span>|<span data-ttu-id="62b0d-146">输出属性名称</span><span class="sxs-lookup"><span data-stu-id="62b0d-146">Output attribute name</span></span>|  
  
 <span data-ttu-id="62b0d-147">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="62b0d-147">NODE_NAME</span></span>  
 <span data-ttu-id="62b0d-148">节点的名称。</span><span class="sxs-lookup"><span data-stu-id="62b0d-148">The name of the node.</span></span> <span data-ttu-id="62b0d-149">当前，该列包含的值与 NODE_UNIQUE_NAME 的值相同，但是这一情况在以后的版本中可能会发生变化。</span><span class="sxs-lookup"><span data-stu-id="62b0d-149">Currently, this column contains the same value as NODE_UNIQUE_NAME, though this may change in future releases.</span></span>  
  
 <span data-ttu-id="62b0d-150">NODE_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="62b0d-150">NODE_UNIQUE_NAME</span></span>  
 <span data-ttu-id="62b0d-151">节点的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="62b0d-151">The unique name of the node.</span></span>  
  
 <span data-ttu-id="62b0d-152">有关名称和 ID 如何提供有关模型的结构信息的详细信息，请参阅 [使用节点名称和 ID](#bkmk_NodeIDs)部分。</span><span class="sxs-lookup"><span data-stu-id="62b0d-152">For more information about how the names and IDs provide structural information about the model, see the section, [Using Node Names and IDs](#bkmk_NodeIDs).</span></span>  
  
 <span data-ttu-id="62b0d-153">NODE_TYPE</span><span class="sxs-lookup"><span data-stu-id="62b0d-153">NODE_TYPE</span></span>  
 <span data-ttu-id="62b0d-154">逻辑回归模型输出以下节点类型：</span><span class="sxs-lookup"><span data-stu-id="62b0d-154">A logistic regression model outputs the following node types:</span></span>  
  
|<span data-ttu-id="62b0d-155">节点类型 ID</span><span class="sxs-lookup"><span data-stu-id="62b0d-155">Node Type ID</span></span>|<span data-ttu-id="62b0d-156">说明</span><span class="sxs-lookup"><span data-stu-id="62b0d-156">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="62b0d-157">1</span><span class="sxs-lookup"><span data-stu-id="62b0d-157">1</span></span>|<span data-ttu-id="62b0d-158">模型。</span><span class="sxs-lookup"><span data-stu-id="62b0d-158">Model.</span></span>|  
|<span data-ttu-id="62b0d-159">17</span><span class="sxs-lookup"><span data-stu-id="62b0d-159">17</span></span>|<span data-ttu-id="62b0d-160">子网的组织程序节点。</span><span class="sxs-lookup"><span data-stu-id="62b0d-160">Organizer node for the subnetwork.</span></span>|  
|<span data-ttu-id="62b0d-161">18</span><span class="sxs-lookup"><span data-stu-id="62b0d-161">18</span></span>|<span data-ttu-id="62b0d-162">输入层的组织程序节点。</span><span class="sxs-lookup"><span data-stu-id="62b0d-162">Organizer node for the input layer.</span></span>|  
|<span data-ttu-id="62b0d-163">19</span><span class="sxs-lookup"><span data-stu-id="62b0d-163">19</span></span>|<span data-ttu-id="62b0d-164">隐藏层的组织程序节点。</span><span class="sxs-lookup"><span data-stu-id="62b0d-164">Organizer node for the hidden layer.</span></span> <span data-ttu-id="62b0d-165">隐藏层为空。</span><span class="sxs-lookup"><span data-stu-id="62b0d-165">The hidden layer is empty.</span></span>|  
|<span data-ttu-id="62b0d-166">20</span><span class="sxs-lookup"><span data-stu-id="62b0d-166">20</span></span>|<span data-ttu-id="62b0d-167">输出层的组织程序节点。</span><span class="sxs-lookup"><span data-stu-id="62b0d-167">Organizer node for the output layer.</span></span>|  
|<span data-ttu-id="62b0d-168">21</span><span class="sxs-lookup"><span data-stu-id="62b0d-168">21</span></span>|<span data-ttu-id="62b0d-169">输入属性节点。</span><span class="sxs-lookup"><span data-stu-id="62b0d-169">Input attribute node.</span></span>|  
|<span data-ttu-id="62b0d-170">23</span><span class="sxs-lookup"><span data-stu-id="62b0d-170">23</span></span>|<span data-ttu-id="62b0d-171">输出属性节点。</span><span class="sxs-lookup"><span data-stu-id="62b0d-171">Output attribute node.</span></span>|  
|<span data-ttu-id="62b0d-172">24</span><span class="sxs-lookup"><span data-stu-id="62b0d-172">24</span></span>|<span data-ttu-id="62b0d-173">边际统计信息节点。</span><span class="sxs-lookup"><span data-stu-id="62b0d-173">Marginal statistics node.</span></span>|  
  
 <span data-ttu-id="62b0d-174">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="62b0d-174">NODE_CAPTION</span></span>  
 <span data-ttu-id="62b0d-175">与节点关联的标签或标题。</span><span class="sxs-lookup"><span data-stu-id="62b0d-175">A label or a caption associated with the node.</span></span> <span data-ttu-id="62b0d-176">在逻辑回归模型中，始终为空白。</span><span class="sxs-lookup"><span data-stu-id="62b0d-176">In logistic regression models, always blank.</span></span>  
  
 <span data-ttu-id="62b0d-177">CHILDREN_CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="62b0d-177">CHILDREN_CARDINALITY</span></span>  
 <span data-ttu-id="62b0d-178">对节点所具有的子节点数的估计。</span><span class="sxs-lookup"><span data-stu-id="62b0d-178">An estimate of the number of children that the node has.</span></span>  
  
|<span data-ttu-id="62b0d-179">节点</span><span class="sxs-lookup"><span data-stu-id="62b0d-179">Node</span></span>|<span data-ttu-id="62b0d-180">内容</span><span class="sxs-lookup"><span data-stu-id="62b0d-180">Content</span></span>|  
|----------|-------------|  
|<span data-ttu-id="62b0d-181">模型根</span><span class="sxs-lookup"><span data-stu-id="62b0d-181">Model root</span></span>|<span data-ttu-id="62b0d-182">指示子节点的计数，其中至少包括 1 个网络，1 个必需边际节点和 1 个必需输入层。</span><span class="sxs-lookup"><span data-stu-id="62b0d-182">Indicates the count of child nodes, which includes at least 1 network, 1 required marginal node, and 1 required input layer.</span></span> <span data-ttu-id="62b0d-183">例如，如果值为 5，则具有 3 个子网。</span><span class="sxs-lookup"><span data-stu-id="62b0d-183">For example, if the value is 5, there are 3 subnetworks.</span></span>|  
|<span data-ttu-id="62b0d-184">边际统计信息</span><span class="sxs-lookup"><span data-stu-id="62b0d-184">Marginal statistics</span></span>|<span data-ttu-id="62b0d-185">始终为 0。</span><span class="sxs-lookup"><span data-stu-id="62b0d-185">Always 0.</span></span>|  
|<span data-ttu-id="62b0d-186">输入层</span><span class="sxs-lookup"><span data-stu-id="62b0d-186">Input layer</span></span>|<span data-ttu-id="62b0d-187">指示模型使用的输入属性值对的数目。</span><span class="sxs-lookup"><span data-stu-id="62b0d-187">Indicates the number of input attribute-values pairs that were used by the model.</span></span>|  
|<span data-ttu-id="62b0d-188">输入节点</span><span class="sxs-lookup"><span data-stu-id="62b0d-188">Input node</span></span>|<span data-ttu-id="62b0d-189">始终为 0。</span><span class="sxs-lookup"><span data-stu-id="62b0d-189">Always 0.</span></span>|  
|<span data-ttu-id="62b0d-190">隐藏层</span><span class="sxs-lookup"><span data-stu-id="62b0d-190">Hidden layer</span></span>|<span data-ttu-id="62b0d-191">在逻辑回归模型中，始终为 0。</span><span class="sxs-lookup"><span data-stu-id="62b0d-191">In a logistic regression model, always 0.</span></span>|  
|<span data-ttu-id="62b0d-192">输出层</span><span class="sxs-lookup"><span data-stu-id="62b0d-192">Output layer</span></span>|<span data-ttu-id="62b0d-193">指示输出值的数目。</span><span class="sxs-lookup"><span data-stu-id="62b0d-193">Indicates the number of output values.</span></span>|  
|<span data-ttu-id="62b0d-194">输出节点</span><span class="sxs-lookup"><span data-stu-id="62b0d-194">Output node</span></span>|<span data-ttu-id="62b0d-195">始终为 0。</span><span class="sxs-lookup"><span data-stu-id="62b0d-195">Always 0.</span></span>|  
  
 <span data-ttu-id="62b0d-196">PARENT_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="62b0d-196">PARENT_UNIQUE_NAME</span></span>  
 <span data-ttu-id="62b0d-197">节点的父节点的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="62b0d-197">The unique name of the node's parent.</span></span> <span data-ttu-id="62b0d-198">根级别上的任何节点均返回 NULL。</span><span class="sxs-lookup"><span data-stu-id="62b0d-198">NULL is returned for any nodes at the root level.</span></span>  
  
 <span data-ttu-id="62b0d-199">有关名称和 ID 如何提供有关模型的结构信息的详细信息，请参阅 [使用节点名称和 ID](#bkmk_NodeIDs)部分。</span><span class="sxs-lookup"><span data-stu-id="62b0d-199">For more information about how the names and IDs provide structural information about the model, see the section, [Using Node Names and IDs](#bkmk_NodeIDs).</span></span>  
  
 <span data-ttu-id="62b0d-200">NODE_DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="62b0d-200">NODE_DESCRIPTION</span></span>  
 <span data-ttu-id="62b0d-201">节点的用户友好说明。</span><span class="sxs-lookup"><span data-stu-id="62b0d-201">A user-friendly description of the node.</span></span>  
  
|<span data-ttu-id="62b0d-202">节点</span><span class="sxs-lookup"><span data-stu-id="62b0d-202">Node</span></span>|<span data-ttu-id="62b0d-203">内容</span><span class="sxs-lookup"><span data-stu-id="62b0d-203">Content</span></span>|  
|----------|-------------|  
|<span data-ttu-id="62b0d-204">模型根</span><span class="sxs-lookup"><span data-stu-id="62b0d-204">Model root</span></span>|<span data-ttu-id="62b0d-205">空</span><span class="sxs-lookup"><span data-stu-id="62b0d-205">Blank</span></span>|  
|<span data-ttu-id="62b0d-206">边际统计信息</span><span class="sxs-lookup"><span data-stu-id="62b0d-206">Marginal statistics</span></span>|<span data-ttu-id="62b0d-207">空</span><span class="sxs-lookup"><span data-stu-id="62b0d-207">Blank</span></span>|  
|<span data-ttu-id="62b0d-208">输入层</span><span class="sxs-lookup"><span data-stu-id="62b0d-208">Input layer</span></span>|<span data-ttu-id="62b0d-209">空</span><span class="sxs-lookup"><span data-stu-id="62b0d-209">Blank</span></span>|  
|<span data-ttu-id="62b0d-210">输入节点</span><span class="sxs-lookup"><span data-stu-id="62b0d-210">Input node</span></span>|<span data-ttu-id="62b0d-211">输入属性名称</span><span class="sxs-lookup"><span data-stu-id="62b0d-211">Input attribute name</span></span>|  
|<span data-ttu-id="62b0d-212">隐藏层</span><span class="sxs-lookup"><span data-stu-id="62b0d-212">Hidden layer</span></span>|<span data-ttu-id="62b0d-213">空</span><span class="sxs-lookup"><span data-stu-id="62b0d-213">Blank</span></span>|  
|<span data-ttu-id="62b0d-214">输出层</span><span class="sxs-lookup"><span data-stu-id="62b0d-214">Output layer</span></span>|<span data-ttu-id="62b0d-215">空</span><span class="sxs-lookup"><span data-stu-id="62b0d-215">Blank</span></span>|  
|<span data-ttu-id="62b0d-216">输出节点</span><span class="sxs-lookup"><span data-stu-id="62b0d-216">Output node</span></span>|<span data-ttu-id="62b0d-217">如果输出属性是连续的，则包含输出属性的名称。</span><span class="sxs-lookup"><span data-stu-id="62b0d-217">If the output attribute is continuous, contains the name of the output attribute.</span></span><br /><br /> <span data-ttu-id="62b0d-218">如果输出属性是离散或离散化属性，则包含属性的名称和值。</span><span class="sxs-lookup"><span data-stu-id="62b0d-218">If the output attribute is discrete or discretized, contains the name of the attribute and the value.</span></span>|  
  
 <span data-ttu-id="62b0d-219">NODE_RULE</span><span class="sxs-lookup"><span data-stu-id="62b0d-219">NODE_RULE</span></span>  
 <span data-ttu-id="62b0d-220">嵌入节点的规则的 XML 说明。</span><span class="sxs-lookup"><span data-stu-id="62b0d-220">An XML description of the rule that is embedded in the node.</span></span>  
  
|<span data-ttu-id="62b0d-221">节点</span><span class="sxs-lookup"><span data-stu-id="62b0d-221">Node</span></span>|<span data-ttu-id="62b0d-222">内容</span><span class="sxs-lookup"><span data-stu-id="62b0d-222">Content</span></span>|  
|----------|-------------|  
|<span data-ttu-id="62b0d-223">模型根</span><span class="sxs-lookup"><span data-stu-id="62b0d-223">Model root</span></span>|<span data-ttu-id="62b0d-224">空</span><span class="sxs-lookup"><span data-stu-id="62b0d-224">Blank</span></span>|  
|<span data-ttu-id="62b0d-225">边际统计信息</span><span class="sxs-lookup"><span data-stu-id="62b0d-225">Marginal statistics</span></span>|<span data-ttu-id="62b0d-226">空</span><span class="sxs-lookup"><span data-stu-id="62b0d-226">Blank</span></span>|  
|<span data-ttu-id="62b0d-227">输入层</span><span class="sxs-lookup"><span data-stu-id="62b0d-227">Input layer</span></span>|<span data-ttu-id="62b0d-228">空</span><span class="sxs-lookup"><span data-stu-id="62b0d-228">Blank</span></span>|  
|<span data-ttu-id="62b0d-229">输入节点</span><span class="sxs-lookup"><span data-stu-id="62b0d-229">Input node</span></span>|<span data-ttu-id="62b0d-230">包含与 NODE_DESCRIPTION 列相同的信息的 XML 片段。</span><span class="sxs-lookup"><span data-stu-id="62b0d-230">An XML fragment containing the same information as the NODE_DESCRIPTION column.</span></span>|  
|<span data-ttu-id="62b0d-231">隐藏层</span><span class="sxs-lookup"><span data-stu-id="62b0d-231">Hidden layer</span></span>|<span data-ttu-id="62b0d-232">空</span><span class="sxs-lookup"><span data-stu-id="62b0d-232">Blank</span></span>|  
|<span data-ttu-id="62b0d-233">输出层</span><span class="sxs-lookup"><span data-stu-id="62b0d-233">Output layer</span></span>|<span data-ttu-id="62b0d-234">空</span><span class="sxs-lookup"><span data-stu-id="62b0d-234">Blank</span></span>|  
|<span data-ttu-id="62b0d-235">输出节点</span><span class="sxs-lookup"><span data-stu-id="62b0d-235">Output node</span></span>|<span data-ttu-id="62b0d-236">包含与 NODE_DESCRIPTION 列相同的信息的 XML 片段。</span><span class="sxs-lookup"><span data-stu-id="62b0d-236">An XML fragment containing the same information as the NODE_DESCRIPTION column.</span></span>|  
  
 <span data-ttu-id="62b0d-237">MARGINAL_RULE</span><span class="sxs-lookup"><span data-stu-id="62b0d-237">MARGINAL_RULE</span></span>  
 <span data-ttu-id="62b0d-238">对于逻辑回归模型，始终为空白。</span><span class="sxs-lookup"><span data-stu-id="62b0d-238">For logistic regression models, always blank.</span></span>  
  
 <span data-ttu-id="62b0d-239">NODE_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="62b0d-239">NODE_PROBABILITY</span></span>  
 <span data-ttu-id="62b0d-240">与此节点相关联的概率。</span><span class="sxs-lookup"><span data-stu-id="62b0d-240">The probability associated with this node.</span></span> <span data-ttu-id="62b0d-241">对于逻辑回归模型，始终为 0。</span><span class="sxs-lookup"><span data-stu-id="62b0d-241">For logistic regression models, always 0.</span></span>  
  
 <span data-ttu-id="62b0d-242">MARGINAL_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="62b0d-242">MARGINAL_PROBABILITY</span></span>  
 <span data-ttu-id="62b0d-243">从父节点到达该节点的概率。</span><span class="sxs-lookup"><span data-stu-id="62b0d-243">The probability of reaching the node from the parent node.</span></span> <span data-ttu-id="62b0d-244">对于逻辑回归模型，始终为 0。</span><span class="sxs-lookup"><span data-stu-id="62b0d-244">For logistic regression models, always 0.</span></span>  
  
 <span data-ttu-id="62b0d-245">NODE_DISTRIBUTION</span><span class="sxs-lookup"><span data-stu-id="62b0d-245">NODE_DISTRIBUTION</span></span>  
 <span data-ttu-id="62b0d-246">包含节点的统计信息的嵌套表。</span><span class="sxs-lookup"><span data-stu-id="62b0d-246">A nested table that contains statistical information for the node.</span></span> <span data-ttu-id="62b0d-247">有关该表中每个节点类型的内容的详细信息，请参阅 [神经网络模型的挖掘模型内容（Analysis Services - 数据挖掘）](mining-model-content-for-neural-network-models-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="62b0d-247">For detailed information about the contents of this table for each node type, see the section, Understanding the NODE_DISTRIBUTION Table, in [Mining Model Content for Neural Network Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="62b0d-248">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="62b0d-248">NODE_SUPPORT</span></span>  
 <span data-ttu-id="62b0d-249">对于逻辑回归模型，始终为 0。</span><span class="sxs-lookup"><span data-stu-id="62b0d-249">For logistic regression models, always 0.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="62b0d-250">由于该模型类型的输出不是概率性的，因此支持概率始终为 0。</span><span class="sxs-lookup"><span data-stu-id="62b0d-250">Support probabilities are always 0 because the output of this model type is not probabilistic.</span></span> <span data-ttu-id="62b0d-251">对算法有意义的唯一项是权重；因此，算法不会计算概率、支持或方差。</span><span class="sxs-lookup"><span data-stu-id="62b0d-251">The only thing that is meaningful for the algorithm is the weights; therefore, the algorithm does not compute probability, support, or variance.</span></span>  
  
 <span data-ttu-id="62b0d-252">若要获取定型事例中对特定值的支持信息，请参阅边际统计信息节点。</span><span class="sxs-lookup"><span data-stu-id="62b0d-252">To get information about the support in the training cases for specific values, see the marginal statistics node.</span></span>  
  
 <span data-ttu-id="62b0d-253">MSOLAP_MODEL_COLUMN</span><span class="sxs-lookup"><span data-stu-id="62b0d-253">MSOLAP_MODEL_COLUMN</span></span>  
 |<span data-ttu-id="62b0d-254">节点</span><span class="sxs-lookup"><span data-stu-id="62b0d-254">Node</span></span>|<span data-ttu-id="62b0d-255">内容</span><span class="sxs-lookup"><span data-stu-id="62b0d-255">Content</span></span>|  
|----------|-------------|  
|<span data-ttu-id="62b0d-256">模型根</span><span class="sxs-lookup"><span data-stu-id="62b0d-256">Model root</span></span>|<span data-ttu-id="62b0d-257">空</span><span class="sxs-lookup"><span data-stu-id="62b0d-257">Blank</span></span>|  
|<span data-ttu-id="62b0d-258">边际统计信息</span><span class="sxs-lookup"><span data-stu-id="62b0d-258">Marginal statistics</span></span>|<span data-ttu-id="62b0d-259">空</span><span class="sxs-lookup"><span data-stu-id="62b0d-259">Blank</span></span>|  
|<span data-ttu-id="62b0d-260">输入层</span><span class="sxs-lookup"><span data-stu-id="62b0d-260">Input layer</span></span>|<span data-ttu-id="62b0d-261">空</span><span class="sxs-lookup"><span data-stu-id="62b0d-261">Blank</span></span>|  
|<span data-ttu-id="62b0d-262">输入节点</span><span class="sxs-lookup"><span data-stu-id="62b0d-262">Input node</span></span>|<span data-ttu-id="62b0d-263">输入属性名称。</span><span class="sxs-lookup"><span data-stu-id="62b0d-263">Input attribute name.</span></span>|  
|<span data-ttu-id="62b0d-264">隐藏层</span><span class="sxs-lookup"><span data-stu-id="62b0d-264">Hidden layer</span></span>|<span data-ttu-id="62b0d-265">空</span><span class="sxs-lookup"><span data-stu-id="62b0d-265">Blank</span></span>|  
|<span data-ttu-id="62b0d-266">输出层</span><span class="sxs-lookup"><span data-stu-id="62b0d-266">Output layer</span></span>|<span data-ttu-id="62b0d-267">空</span><span class="sxs-lookup"><span data-stu-id="62b0d-267">Blank</span></span>|  
|<span data-ttu-id="62b0d-268">输出节点</span><span class="sxs-lookup"><span data-stu-id="62b0d-268">Output node</span></span>|<span data-ttu-id="62b0d-269">输入属性名称。</span><span class="sxs-lookup"><span data-stu-id="62b0d-269">Input attribute name.</span></span>|  
  
 <span data-ttu-id="62b0d-270">MSOLAP_NODE_SCORE</span><span class="sxs-lookup"><span data-stu-id="62b0d-270">MSOLAP_NODE_SCORE</span></span>  
 <span data-ttu-id="62b0d-271">在逻辑回归模型中，始终为 0。</span><span class="sxs-lookup"><span data-stu-id="62b0d-271">In logistic regression models, always 0.</span></span>  
  
 <span data-ttu-id="62b0d-272">MSOLAP_NODE_SHORT_CAPTION</span><span class="sxs-lookup"><span data-stu-id="62b0d-272">MSOLAP_NODE_SHORT_CAPTION</span></span>  
 <span data-ttu-id="62b0d-273">在逻辑回归模型中，始终为空白。</span><span class="sxs-lookup"><span data-stu-id="62b0d-273">In logistic regression models, always blank.</span></span>  
  
##  <a name="using-node-names-and-ids"></a><a name="bkmk_NodeIDs"></a><span data-ttu-id="62b0d-274">使用节点名称和 Id</span><span class="sxs-lookup"><span data-stu-id="62b0d-274">Using Node Names and IDs</span></span>  
 <span data-ttu-id="62b0d-275">逻辑回归模型中各节点的命名方式提供该模型中各节点之间的关系的其他相关信息。</span><span class="sxs-lookup"><span data-stu-id="62b0d-275">The naming of the nodes in a logistic regression model provides additional information about the relationships between nodes in the model.</span></span> <span data-ttu-id="62b0d-276">下表给出了为每层中的节点分配 ID 的约定。</span><span class="sxs-lookup"><span data-stu-id="62b0d-276">The following table shows the conventions for the IDs that are assigned to nodes in each layer.</span></span>  
  
|<span data-ttu-id="62b0d-277">节点类型</span><span class="sxs-lookup"><span data-stu-id="62b0d-277">Node Type</span></span>|<span data-ttu-id="62b0d-278">节点 ID 约定</span><span class="sxs-lookup"><span data-stu-id="62b0d-278">Convention for node ID</span></span>|  
|---------------|----------------------------|  
|<span data-ttu-id="62b0d-279">模型根 (1)</span><span class="sxs-lookup"><span data-stu-id="62b0d-279">Model root (1)</span></span>|<span data-ttu-id="62b0d-280">00000000000000000.</span><span class="sxs-lookup"><span data-stu-id="62b0d-280">00000000000000000.</span></span>|  
|<span data-ttu-id="62b0d-281">边际统计信息节点 (24)</span><span class="sxs-lookup"><span data-stu-id="62b0d-281">Marginal statistics node (24)</span></span>|<span data-ttu-id="62b0d-282">10000000000000000</span><span class="sxs-lookup"><span data-stu-id="62b0d-282">10000000000000000</span></span>|  
|<span data-ttu-id="62b0d-283">输入层 (18)</span><span class="sxs-lookup"><span data-stu-id="62b0d-283">Input layer (18)</span></span>|<span data-ttu-id="62b0d-284">30000000000000000</span><span class="sxs-lookup"><span data-stu-id="62b0d-284">30000000000000000</span></span>|  
|<span data-ttu-id="62b0d-285">输入节点 (21)</span><span class="sxs-lookup"><span data-stu-id="62b0d-285">Input node (21)</span></span>|<span data-ttu-id="62b0d-286">以 60000000000000000 作为开头</span><span class="sxs-lookup"><span data-stu-id="62b0d-286">Starts at 60000000000000000</span></span>|  
|<span data-ttu-id="62b0d-287">子网 (17)</span><span class="sxs-lookup"><span data-stu-id="62b0d-287">Subnetwork (17)</span></span>|<span data-ttu-id="62b0d-288">20000000000000000</span><span class="sxs-lookup"><span data-stu-id="62b0d-288">20000000000000000</span></span>|  
|<span data-ttu-id="62b0d-289">隐藏层 (19)</span><span class="sxs-lookup"><span data-stu-id="62b0d-289">Hidden layer (19)</span></span>|<span data-ttu-id="62b0d-290">40000000000000000</span><span class="sxs-lookup"><span data-stu-id="62b0d-290">40000000000000000</span></span>|  
|<span data-ttu-id="62b0d-291">输出层 (20)</span><span class="sxs-lookup"><span data-stu-id="62b0d-291">Output layer (20)</span></span>|<span data-ttu-id="62b0d-292">50000000000000000</span><span class="sxs-lookup"><span data-stu-id="62b0d-292">50000000000000000</span></span>|  
|<span data-ttu-id="62b0d-293">输出节点 (23)</span><span class="sxs-lookup"><span data-stu-id="62b0d-293">Output node (23)</span></span>|<span data-ttu-id="62b0d-294">以 80000000000000000 作为开头</span><span class="sxs-lookup"><span data-stu-id="62b0d-294">Starts at 80000000000000000</span></span>|  
  
 <span data-ttu-id="62b0d-295">通过查看输出节点的 NODE_DISTRIBUTION 表，您可以使用这些 ID 确定输出属性如何与特定输入层属性关联。</span><span class="sxs-lookup"><span data-stu-id="62b0d-295">You can use these IDs to determine how output attributes are related to specific input layer attributes, by viewing the NODE_DISTRIBUTION table of the output node.</span></span> <span data-ttu-id="62b0d-296">该表中的每一行都包含一个会指到特定输入属性节点的 ID。</span><span class="sxs-lookup"><span data-stu-id="62b0d-296">Each row in that table contains an ID that points back to a specific input attribute node.</span></span> <span data-ttu-id="62b0d-297">NODE_DISTRIBUTION 表还包含该输入-输出对的系数。</span><span class="sxs-lookup"><span data-stu-id="62b0d-297">The NODE_DISTRIBUTION table also contains the coefficient for that input-output pair.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62b0d-298">另请参阅</span><span class="sxs-lookup"><span data-stu-id="62b0d-298">See Also</span></span>  
 <span data-ttu-id="62b0d-299">[Microsoft 逻辑回归算法](microsoft-logistic-regression-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="62b0d-299">[Microsoft Logistic Regression Algorithm](microsoft-logistic-regression-algorithm.md) </span></span>  
 <span data-ttu-id="62b0d-300">[&#40;Analysis Services 数据挖掘的神经网络模型的挖掘模型内容&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="62b0d-300">[Mining Model Content for Neural Network Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="62b0d-301">[逻辑回归模型查询示例](logistic-regression-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="62b0d-301">[Logistic Regression Model Query Examples](logistic-regression-model-query-examples.md) </span></span>  
 [<span data-ttu-id="62b0d-302">Microsoft 逻辑回归算法技术参考</span><span class="sxs-lookup"><span data-stu-id="62b0d-302">Microsoft Logistic Regression Algorithm Technical Reference</span></span>](microsoft-logistic-regression-algorithm-technical-reference.md)  
  
  
