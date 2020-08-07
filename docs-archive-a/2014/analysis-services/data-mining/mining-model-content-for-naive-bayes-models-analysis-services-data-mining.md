---
title: Naive Bayes 模型的挖掘模型内容 (Analysis Services 数据挖掘) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- naive bayes model [Analysis Services]
- Bayesian classifiers
- naive bayes algorithms [Analysis Services]
- mining model content, naive bayes models
ms.assetid: 63fa15b0-e00c-4aa3-aa49-335f5572ff7e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 52e5da80e109828722d56fada19b019d1cfa51f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589363"
---
# <a name="mining-model-content-for-naive-bayes-models-analysis-services---data-mining"></a><span data-ttu-id="a40c0-102">Naive Bayes 模型的挖掘模型内容（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="a40c0-102">Mining Model Content for Naive Bayes Models (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="a40c0-103">本主题介绍使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes 算法的模型特有的挖掘模型内容。</span><span class="sxs-lookup"><span data-stu-id="a40c0-103">This topic describes mining model content that is specific to models that use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm.</span></span> <span data-ttu-id="a40c0-104">有关如何解释所有模型类型共享的统计信息和结构，以及与挖掘模型内容相关的常规术语定义的说明，请参阅 [挖掘模型内容（Analysis Services - 数据挖掘）](mining-model-content-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="a40c0-104">For an explanation of how to interpret statistics and structure shared by all model types, and general definitions of terms related to mining model content, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
## <a name="understanding-the-structure-of-a-naive-bayes-model"></a><span data-ttu-id="a40c0-105">了解 Naive Bayes 模型的结构</span><span class="sxs-lookup"><span data-stu-id="a40c0-105">Understanding the Structure of a Naive Bayes Model</span></span>  
 <span data-ttu-id="a40c0-106">Naive Bayes 模型具有表示该模型及其元数据的单一父节点，并且在该父节点下，还存在任意数目的表示所选可预测属性的独立树。</span><span class="sxs-lookup"><span data-stu-id="a40c0-106">A Naive Bayes model has a single parent node that represents the model and its metadata, and underneath that parent node, any number of independent trees that represent the predictable attributes that you selected.</span></span> <span data-ttu-id="a40c0-107">除表示属性的树以外，每个模型还包含一个提供有关定型事例集的说明性统计信息的边际统计信息节点 (NODE_TYPE = 26)。</span><span class="sxs-lookup"><span data-stu-id="a40c0-107">In addition to trees for the attributes, each model contains one marginal statistics node (NODE_TYPE = 26) that provides descriptive statistics about the set of training cases.</span></span> <span data-ttu-id="a40c0-108">有关详细信息，请参阅 [边际统计信息节点中的信息](#bkmk_margstats)。</span><span class="sxs-lookup"><span data-stu-id="a40c0-108">For more information, see [Information in the Marginal Statistics Node](#bkmk_margstats).</span></span>  
  
 <span data-ttu-id="a40c0-109">对于每个可预测属性和值，该模型输出包含相关信息的树，这些信息描述各种输入列如何影响该特定可预测属性的结果。</span><span class="sxs-lookup"><span data-stu-id="a40c0-109">For each predictable attribute and value, the model outputs a tree that contains information describing how the various input columns affected the outcome of that particular predictable.</span></span> <span data-ttu-id="a40c0-110">每个树包含可预测属性及其值 (NODE_TYPE = 9)，以及一系列表示输入属性 (NODE_TYPE = 10) 的节点。</span><span class="sxs-lookup"><span data-stu-id="a40c0-110">Each tree contains the predictable attribute and its value (NODE_TYPE = 9), and then a series of nodes that represent the input attributes (NODE_TYPE = 10).</span></span> <span data-ttu-id="a40c0-111">由于输入属性通常具有多个值，因此每个输入属性 (NODE_TYPE = 10) 可能具有多个子节点 (NODE_TYPE = 11)，每个子节点各对应于该属性的某一特定状态。</span><span class="sxs-lookup"><span data-stu-id="a40c0-111">Because the input attributes typically have multiple values, each input attribute (NODE_TYPE = 10) may have multiple child nodes (NODE_TYPE = 11), each for a specific state of the attribute.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a40c0-112">由于 Naive Bayes 模型不允许使用连续数据类型，因此，输入列的所有值均被视为离散或离散化值。</span><span class="sxs-lookup"><span data-stu-id="a40c0-112">Because a Naive Bayes model does not permit continuous data types, all the values of the input columns are treated as discrete or discretized.</span></span> <span data-ttu-id="a40c0-113">您可以指定值的离散化方式。</span><span class="sxs-lookup"><span data-stu-id="a40c0-113">You can specify how a value is discretized.</span></span> <span data-ttu-id="a40c0-114">有关详细信息，请参阅 [更改挖掘模型中列的离散化](change-the-discretization-of-a-column-in-a-mining-model.md)。</span><span class="sxs-lookup"><span data-stu-id="a40c0-114">For more information, [Change the Discretization of a Column in a Mining Model](change-the-discretization-of-a-column-in-a-mining-model.md).</span></span>  
  
 <span data-ttu-id="a40c0-115">![Naive Bayes 的模型内容结构](../media/modelcontentstructure-nb.gif "Naive Bayes 的模型内容结构")</span><span class="sxs-lookup"><span data-stu-id="a40c0-115">![structure of model content for naive bayes](../media/modelcontentstructure-nb.gif "structure of model content for naive bayes")</span></span>  
  
## <a name="model-content-for-a-naive-bayes-model"></a><span data-ttu-id="a40c0-116">Native Bayes 模型的模型内容</span><span class="sxs-lookup"><span data-stu-id="a40c0-116">Model Content for a Naive Bayes Model</span></span>  
 <span data-ttu-id="a40c0-117">本节提供的详细信息和示例仅针对挖掘模型内容中与 Naive Bayes 模型有特殊关系的列。</span><span class="sxs-lookup"><span data-stu-id="a40c0-117">This section provides detail and examples only for those columns in the mining model content that have particular relevance for Naive Bayes models.</span></span>  
  
 <span data-ttu-id="a40c0-118">有关此处未涵盖的架构行集中的通用列（如 MODEL_CATALOG 和 MODEL_NAME）的信息或有关挖掘模型术语的说明，请参阅 [挖掘模型内容（Analysis Services - 数据挖掘）](mining-model-content-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="a40c0-118">For information about general-purpose columns in the schema rowset, such as MODEL_CATALOG and MODEL_NAME, that are not described here, or for explanations of mining model terminology, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="a40c0-119">MODEL_CATALOG</span><span class="sxs-lookup"><span data-stu-id="a40c0-119">MODEL_CATALOG</span></span>  
 <span data-ttu-id="a40c0-120">存储模型的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="a40c0-120">Name of the database where the model is stored.</span></span>  
  
 <span data-ttu-id="a40c0-121">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="a40c0-121">MODEL_NAME</span></span>  
 <span data-ttu-id="a40c0-122">模型的名称。</span><span class="sxs-lookup"><span data-stu-id="a40c0-122">Name of the model.</span></span>  
  
 <span data-ttu-id="a40c0-123">ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="a40c0-123">ATTRIBUTE_NAME</span></span>  
 <span data-ttu-id="a40c0-124">与此节点对应的属性的名称。</span><span class="sxs-lookup"><span data-stu-id="a40c0-124">The names of the attributes that correspond to this node.</span></span>  
  
 <span data-ttu-id="a40c0-125">**模型根** 可预测属性的名称。</span><span class="sxs-lookup"><span data-stu-id="a40c0-125">**Model root** The name of the predictable attribute.</span></span>  
  
 <span data-ttu-id="a40c0-126">**边际统计信息** 不适用</span><span class="sxs-lookup"><span data-stu-id="a40c0-126">**Marginal statistics** Not applicable</span></span>  
  
 <span data-ttu-id="a40c0-127">**可预测属性** 可预测属性的名称。</span><span class="sxs-lookup"><span data-stu-id="a40c0-127">**Predictable attribute** The name of the predictable attribute.</span></span>  
  
 <span data-ttu-id="a40c0-128">**输入属性** 输入属性的名称。</span><span class="sxs-lookup"><span data-stu-id="a40c0-128">**Input attribute** The name of the input attribute.</span></span>  
  
 <span data-ttu-id="a40c0-129">**输入属性状态** 仅限输入属性的名称。</span><span class="sxs-lookup"><span data-stu-id="a40c0-129">**Input attribute state** The name of the input attribute only.</span></span> <span data-ttu-id="a40c0-130">若要获取状态，请使用 MSOLAP_NODE_SHORT_CAPTION。</span><span class="sxs-lookup"><span data-stu-id="a40c0-130">To get the state, use MSOLAP_NODE_SHORT_CAPTION.</span></span>  
  
 <span data-ttu-id="a40c0-131">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="a40c0-131">NODE_NAME</span></span>  
 <span data-ttu-id="a40c0-132">节点的名称。</span><span class="sxs-lookup"><span data-stu-id="a40c0-132">The name of the node.</span></span>  
  
 <span data-ttu-id="a40c0-133">该列包含的值与 NODE_UNIQUE_NAME 列相同。</span><span class="sxs-lookup"><span data-stu-id="a40c0-133">This column contains the same value as NODE_UNIQUE_NAME.</span></span>  
  
 <span data-ttu-id="a40c0-134">有关节点命名约定的详细信息，请参阅 [使用节点名称和 ID](#bkmk_nodenames)。</span><span class="sxs-lookup"><span data-stu-id="a40c0-134">For more information about node naming conventions, see [Using Node Names and IDs](#bkmk_nodenames).</span></span>  
  
 <span data-ttu-id="a40c0-135">NODE_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="a40c0-135">NODE_UNIQUE_NAME</span></span>  
 <span data-ttu-id="a40c0-136">节点的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="a40c0-136">The unique name of the node.</span></span> <span data-ttu-id="a40c0-137">这些唯一名称是根据一定的命名约定分配的，该命名约定提供了各节点之间关系的相关信息。</span><span class="sxs-lookup"><span data-stu-id="a40c0-137">The unique names are assigned according to a convention that provides information about the relationships among the nodes.</span></span> <span data-ttu-id="a40c0-138">有关节点命名约定的详细信息，请参阅 [使用节点名称和 ID](#bkmk_nodenames)。</span><span class="sxs-lookup"><span data-stu-id="a40c0-138">For more information about node naming conventions, see [Using Node Names and IDs](#bkmk_nodenames).</span></span>  
  
 <span data-ttu-id="a40c0-139">NODE_TYPE</span><span class="sxs-lookup"><span data-stu-id="a40c0-139">NODE_TYPE</span></span>  
 <span data-ttu-id="a40c0-140">Naive Bayes 模型输出以下节点类型：</span><span class="sxs-lookup"><span data-stu-id="a40c0-140">A Naive Bayes model outputs the following node types:</span></span>  
  
|<span data-ttu-id="a40c0-141">节点类型 ID</span><span class="sxs-lookup"><span data-stu-id="a40c0-141">Node Type ID</span></span>|<span data-ttu-id="a40c0-142">说明</span><span class="sxs-lookup"><span data-stu-id="a40c0-142">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="a40c0-143">26 (NaiveBayesMarginalStatNode)</span><span class="sxs-lookup"><span data-stu-id="a40c0-143">26 (NaiveBayesMarginalStatNode)</span></span>|<span data-ttu-id="a40c0-144">包含描述模型的整个定型事例集的统计信息。</span><span class="sxs-lookup"><span data-stu-id="a40c0-144">Contains statistics that describes the entire set of training cases for the model.</span></span>|  
|<span data-ttu-id="a40c0-145">9（可预测属性）</span><span class="sxs-lookup"><span data-stu-id="a40c0-145">9 (Predictable attribute)</span></span>|<span data-ttu-id="a40c0-146">包含可预测属性的名称。</span><span class="sxs-lookup"><span data-stu-id="a40c0-146">Contains the name of the predictable-attribute.</span></span>|  
|<span data-ttu-id="a40c0-147">10（输入属性）</span><span class="sxs-lookup"><span data-stu-id="a40c0-147">10 (Input attribute)</span></span>|<span data-ttu-id="a40c0-148">包含输入属性列的名称，以及包含该属性的值的子节点。</span><span class="sxs-lookup"><span data-stu-id="a40c0-148">Contains the name of an input attribute column, and child nodes that contains the values for the attribute.</span></span>|  
|<span data-ttu-id="a40c0-149">11（输入属性状态）</span><span class="sxs-lookup"><span data-stu-id="a40c0-149">11 (Input attribute state)</span></span>|<span data-ttu-id="a40c0-150">包含与特定输出属性成对的所有输入属性的值或离散化值。</span><span class="sxs-lookup"><span data-stu-id="a40c0-150">Contains the values or discretized values of all input attributes that were paired with a particular output attribute.</span></span>|  
  
 <span data-ttu-id="a40c0-151">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="a40c0-151">NODE_CAPTION</span></span>  
 <span data-ttu-id="a40c0-152">与节点关联的标签或标题。</span><span class="sxs-lookup"><span data-stu-id="a40c0-152">The label or a caption associated with the node.</span></span> <span data-ttu-id="a40c0-153">此属性主要用于显示目的。</span><span class="sxs-lookup"><span data-stu-id="a40c0-153">This property is primarily for display purposes.</span></span>  
  
 <span data-ttu-id="a40c0-154">**模型根** 空白</span><span class="sxs-lookup"><span data-stu-id="a40c0-154">**Model root** blank</span></span>  
  
 <span data-ttu-id="a40c0-155">**边际统计信息**空白</span><span class="sxs-lookup"><span data-stu-id="a40c0-155">**Marginal statistics** blank</span></span>  
  
 <span data-ttu-id="a40c0-156">**可预测属性** 可预测属性的名称。</span><span class="sxs-lookup"><span data-stu-id="a40c0-156">**Predictable attribute** The name of the predictable attribute.</span></span>  
  
 <span data-ttu-id="a40c0-157">**输入属性** 可预测属性和当前输入属性的名称。</span><span class="sxs-lookup"><span data-stu-id="a40c0-157">**Input attribute** The name of the predictable attribute and the current input attribute.</span></span> <span data-ttu-id="a40c0-158">例如：</span><span class="sxs-lookup"><span data-stu-id="a40c0-158">Ex:</span></span>  
  
 <span data-ttu-id="a40c0-159">Bike Buyer -> Age</span><span class="sxs-lookup"><span data-stu-id="a40c0-159">Bike Buyer -> Age</span></span>  
  
 <span data-ttu-id="a40c0-160">**输入属性状态** 可预测属性和当前输入属性的名称，以及输入的值。</span><span class="sxs-lookup"><span data-stu-id="a40c0-160">**Input attribute state** The name of the predictable attribute and the current input attribute, plus the value of the input.</span></span> <span data-ttu-id="a40c0-161">例如：</span><span class="sxs-lookup"><span data-stu-id="a40c0-161">Ex:</span></span>  
  
 <span data-ttu-id="a40c0-162">Bike Buyer -> Age = Missing</span><span class="sxs-lookup"><span data-stu-id="a40c0-162">Bike Buyer -> Age = Missing</span></span>  
  
 <span data-ttu-id="a40c0-163">CHILDREN_CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="a40c0-163">CHILDREN_CARDINALITY</span></span>  
 <span data-ttu-id="a40c0-164">节点所具有的子节点的数目。</span><span class="sxs-lookup"><span data-stu-id="a40c0-164">The number of children that the node has.</span></span>  
  
 <span data-ttu-id="a40c0-165">**模型根** 模型中可预测属性的计数加 1（表示边际统计信息节点）。</span><span class="sxs-lookup"><span data-stu-id="a40c0-165">**Model root** Count of predictable attributes in the model plus 1 for the marginal statistics node.</span></span>  
  
 <span data-ttu-id="a40c0-166">**边际统计信息** 根据定义，没有任何子级。</span><span class="sxs-lookup"><span data-stu-id="a40c0-166">**Marginal statistics** By definition has no children.</span></span>  
  
 <span data-ttu-id="a40c0-167">**可预测属性**  与当前可预测属性相关的输入属性的计数。</span><span class="sxs-lookup"><span data-stu-id="a40c0-167">**Predictable attribute**  Count of the input attributes that were related to the current predictable attribute.</span></span>  
  
 <span data-ttu-id="a40c0-168">**输入属性** 当前输入属性的离散或离散化值的计数。</span><span class="sxs-lookup"><span data-stu-id="a40c0-168">**Input attribute** Count of the discrete or discretized values for the current input attribute.</span></span>  
  
 <span data-ttu-id="a40c0-169">**输入属性状态** 始终为 0。</span><span class="sxs-lookup"><span data-stu-id="a40c0-169">**Input attribute state** Always 0.</span></span>  
  
 <span data-ttu-id="a40c0-170">PARENT_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="a40c0-170">PARENT_UNIQUE_NAME</span></span>  
 <span data-ttu-id="a40c0-171">父节点的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="a40c0-171">The unique name of the parent node.</span></span> <span data-ttu-id="a40c0-172">有关关联父节点和子节点的详细信息，请参阅 [使用节点名称和 ID](#bkmk_nodenames)。</span><span class="sxs-lookup"><span data-stu-id="a40c0-172">For more information about relating parent and child nodes, see [Using Node Names and IDs](#bkmk_nodenames).</span></span>  
  
 <span data-ttu-id="a40c0-173">NODE_DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="a40c0-173">NODE_DESCRIPTION</span></span>  
 <span data-ttu-id="a40c0-174">与节点标题相同。</span><span class="sxs-lookup"><span data-stu-id="a40c0-174">The same as the node caption.</span></span>  
  
 <span data-ttu-id="a40c0-175">NODE_RULE</span><span class="sxs-lookup"><span data-stu-id="a40c0-175">NODE_RULE</span></span>  
 <span data-ttu-id="a40c0-176">节点标题的 XML 表示形式。</span><span class="sxs-lookup"><span data-stu-id="a40c0-176">An XML representation of the node caption.</span></span>  
  
 <span data-ttu-id="a40c0-177">MARGINAL_RULE</span><span class="sxs-lookup"><span data-stu-id="a40c0-177">MARGINAL_RULE</span></span>  
 <span data-ttu-id="a40c0-178">与节点规则相同。</span><span class="sxs-lookup"><span data-stu-id="a40c0-178">The same as the node rule.</span></span>  
  
 <span data-ttu-id="a40c0-179">NODE_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="a40c0-179">NODE_PROBABILITY</span></span>  
 <span data-ttu-id="a40c0-180">与此节点相关联的概率。</span><span class="sxs-lookup"><span data-stu-id="a40c0-180">The probability associated with this node.</span></span>  
  
 <span data-ttu-id="a40c0-181">**模型根** 始终为 0。</span><span class="sxs-lookup"><span data-stu-id="a40c0-181">**Model root** Always 0.</span></span>  
  
 <span data-ttu-id="a40c0-182">**边际统计信息** 始终为 0。</span><span class="sxs-lookup"><span data-stu-id="a40c0-182">**Marginal statistics** Always 0.</span></span>  
  
 <span data-ttu-id="a40c0-183">**可预测属性**  始终为 1。</span><span class="sxs-lookup"><span data-stu-id="a40c0-183">**Predictable attribute**  Always 1.</span></span>  
  
 <span data-ttu-id="a40c0-184">**输入属性** 始终为 1。</span><span class="sxs-lookup"><span data-stu-id="a40c0-184">**Input attribute** Always 1.</span></span>  
  
 <span data-ttu-id="a40c0-185">**输入属性状态** 表示当前值的概率的小数。</span><span class="sxs-lookup"><span data-stu-id="a40c0-185">**Input attribute state** A decimal number that represents the probability of the current value.</span></span> <span data-ttu-id="a40c0-186">输入属性父节点下所有输入属性状态的值的总和为 1。</span><span class="sxs-lookup"><span data-stu-id="a40c0-186">Values for all input attribute states under the parent input attribute node sum to 1.</span></span>  
  
 <span data-ttu-id="a40c0-187">MARGINAL_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="a40c0-187">MARGINAL_PROBABILITY</span></span>  
 <span data-ttu-id="a40c0-188">与节点概率相同。</span><span class="sxs-lookup"><span data-stu-id="a40c0-188">The same as the node probability.</span></span>  
  
 <span data-ttu-id="a40c0-189">NODE_DISTRIBUTION</span><span class="sxs-lookup"><span data-stu-id="a40c0-189">NODE_DISTRIBUTION</span></span>  
 <span data-ttu-id="a40c0-190">包含节点的概率直方图的表。</span><span class="sxs-lookup"><span data-stu-id="a40c0-190">A table that contains the probability histogram for the node.</span></span> <span data-ttu-id="a40c0-191">有关详细信息，请参阅 [NODE_DISTRIBUTION 表](#bkmk_nodedist)。</span><span class="sxs-lookup"><span data-stu-id="a40c0-191">For more information, see [NODE_DISTRIBUTION Table](#bkmk_nodedist).</span></span>  
  
 <span data-ttu-id="a40c0-192">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="a40c0-192">NODE_SUPPORT</span></span>  
 <span data-ttu-id="a40c0-193">支持此节点的事例的数目。</span><span class="sxs-lookup"><span data-stu-id="a40c0-193">The number of cases that support this node.</span></span>  
  
 <span data-ttu-id="a40c0-194">**模型根** 定型数据中所有事例的计数。</span><span class="sxs-lookup"><span data-stu-id="a40c0-194">**Model root** Count of all cases in training data.</span></span>  
  
 <span data-ttu-id="a40c0-195">**边际统计信息** 始终为 0。</span><span class="sxs-lookup"><span data-stu-id="a40c0-195">**Marginal statistics** Always 0.</span></span>  
  
 <span data-ttu-id="a40c0-196">**可预测属性** 定型数据中所有事例的计数。</span><span class="sxs-lookup"><span data-stu-id="a40c0-196">**Predictable attribute** Count of all cases in training data.</span></span>  
  
 <span data-ttu-id="a40c0-197">**输入属性** 定型数据中所有事例的计数。</span><span class="sxs-lookup"><span data-stu-id="a40c0-197">**Input attribute** Count of all cases in training data.</span></span>  
  
 <span data-ttu-id="a40c0-198">**输入属性状态** 定型数据中仅包含此特定值的事例的计数。</span><span class="sxs-lookup"><span data-stu-id="a40c0-198">**Input attribute state** Count of cases in training data that contain only this particular value.</span></span>  
  
 <span data-ttu-id="a40c0-199">MSOLAP_MODEL_COLUMN</span><span class="sxs-lookup"><span data-stu-id="a40c0-199">MSOLAP_MODEL_COLUMN</span></span>  
 <span data-ttu-id="a40c0-200">用于显示的标签。</span><span class="sxs-lookup"><span data-stu-id="a40c0-200">A label used for display purposes.</span></span> <span data-ttu-id="a40c0-201">通常与 ATTRIBUTE_NAME 相同。</span><span class="sxs-lookup"><span data-stu-id="a40c0-201">Usually the same as ATTRIBUTE_NAME.</span></span>  
  
 <span data-ttu-id="a40c0-202">MSOLAP_NODE_SCORE</span><span class="sxs-lookup"><span data-stu-id="a40c0-202">MSOLAP_NODE_SCORE</span></span>  
 <span data-ttu-id="a40c0-203">表示属性或值在模型中的重要性。</span><span class="sxs-lookup"><span data-stu-id="a40c0-203">Represents the importance of the attribute or value within the model.</span></span>  
  
 <span data-ttu-id="a40c0-204">**模型根** 始终为 0。</span><span class="sxs-lookup"><span data-stu-id="a40c0-204">**Model root** Always 0.</span></span>  
  
 <span data-ttu-id="a40c0-205">**边际统计信息** 始终为 0。</span><span class="sxs-lookup"><span data-stu-id="a40c0-205">**Marginal statistics** Always 0.</span></span>  
  
 <span data-ttu-id="a40c0-206">**可预测属性**  始终为 0。</span><span class="sxs-lookup"><span data-stu-id="a40c0-206">**Predictable attribute**  Always 0.</span></span>  
  
 <span data-ttu-id="a40c0-207">**输入属性** 与当前可预测属性相关的当前输入属性的兴趣性分数。</span><span class="sxs-lookup"><span data-stu-id="a40c0-207">**Input attribute** Interestingness score for the current input attribute in relation to the current predictable attribute.</span></span>  
  
 <span data-ttu-id="a40c0-208">**输入属性状态** 始终为 0。</span><span class="sxs-lookup"><span data-stu-id="a40c0-208">**Input attribute state** Always 0.</span></span>  
  
 <span data-ttu-id="a40c0-209">MSOLAP_NODE_SHORT_CAPTION</span><span class="sxs-lookup"><span data-stu-id="a40c0-209">MSOLAP_NODE_SHORT_CAPTION</span></span>  
 <span data-ttu-id="a40c0-210">表示列的名称或值的文本字符串。</span><span class="sxs-lookup"><span data-stu-id="a40c0-210">A text string that represents the name or the value of a column.</span></span>  
  
 <span data-ttu-id="a40c0-211">**模型根**空字符</span><span class="sxs-lookup"><span data-stu-id="a40c0-211">**Model root** Blank</span></span>  
  
 <span data-ttu-id="a40c0-212">**边际统计信息** 空白</span><span class="sxs-lookup"><span data-stu-id="a40c0-212">**Marginal statistics** Blank</span></span>  
  
 <span data-ttu-id="a40c0-213">**可预测属性** 可预测属性的名称。</span><span class="sxs-lookup"><span data-stu-id="a40c0-213">**Predictable attribute**  The name of the predictable attribute.</span></span>  
  
 <span data-ttu-id="a40c0-214">**输入属性** 输入属性的名称。</span><span class="sxs-lookup"><span data-stu-id="a40c0-214">**Input attribute** The name of the input attribute.</span></span>  
  
 <span data-ttu-id="a40c0-215">**输入属性状态** 输入属性的值或离散化值。</span><span class="sxs-lookup"><span data-stu-id="a40c0-215">**Input attribute state** The value or discretized value of the input attribute.</span></span>  
  
##  <a name="using-node-names-and-ids"></a><a name="bkmk_nodenames"></a><span data-ttu-id="a40c0-216">使用节点名称和 Id</span><span class="sxs-lookup"><span data-stu-id="a40c0-216">Using Node Names and IDs</span></span>  
 <span data-ttu-id="a40c0-217">Naive Bayes 模型中各节点的命名方式提供有关节点的类型的其他信息，以便于了解该模型中信息之间的关系。</span><span class="sxs-lookup"><span data-stu-id="a40c0-217">The naming of the nodes in a Naive Bayes model provides additional information about the type of node, to make it easier to understand the relationships among the information in the model.</span></span> <span data-ttu-id="a40c0-218">下表给出了为不同节点类型分配 ID 的约定。</span><span class="sxs-lookup"><span data-stu-id="a40c0-218">The following table shows the convention for the IDs that are assigned to different node types.</span></span>  
  
|<span data-ttu-id="a40c0-219">节点类型</span><span class="sxs-lookup"><span data-stu-id="a40c0-219">Node Type</span></span>|<span data-ttu-id="a40c0-220">节点 ID 约定</span><span class="sxs-lookup"><span data-stu-id="a40c0-220">Convention for node ID</span></span>|  
|---------------|----------------------------|  
|<span data-ttu-id="a40c0-221">模型根 (1)</span><span class="sxs-lookup"><span data-stu-id="a40c0-221">Model root (1)</span></span>|<span data-ttu-id="a40c0-222">始终为 0。</span><span class="sxs-lookup"><span data-stu-id="a40c0-222">Always 0.</span></span>|  
|<span data-ttu-id="a40c0-223">边际统计信息节点 (26)</span><span class="sxs-lookup"><span data-stu-id="a40c0-223">Marginal statistics node (26)</span></span>|<span data-ttu-id="a40c0-224">任意 ID 值。</span><span class="sxs-lookup"><span data-stu-id="a40c0-224">An arbitrary ID value.</span></span>|  
|<span data-ttu-id="a40c0-225">可预测属性 (9)</span><span class="sxs-lookup"><span data-stu-id="a40c0-225">Predictable attribute (9)</span></span>|<span data-ttu-id="a40c0-226">以 10000000 开头的十六进制数</span><span class="sxs-lookup"><span data-stu-id="a40c0-226">Hexadecimal number beginning with 10000000</span></span><br /><br /> <span data-ttu-id="a40c0-227">例如：100000001、10000000b</span><span class="sxs-lookup"><span data-stu-id="a40c0-227">Example: 100000001, 10000000b</span></span>|  
|<span data-ttu-id="a40c0-228">输入属性 (10)</span><span class="sxs-lookup"><span data-stu-id="a40c0-228">Input attribute (10)</span></span>|<span data-ttu-id="a40c0-229">一个由两部分组成的十六进制数字，其中第一个部分始终为 20000000，第二个部分以相关可预测属性的十六进制标识符作为开头。</span><span class="sxs-lookup"><span data-stu-id="a40c0-229">A two-part hexadecimal number where the first part is always 20000000, and the second part starts with the hexadecimal identifier of the related predictable attribute.</span></span><br /><br /> <span data-ttu-id="a40c0-230">例如：20000000b00000000</span><span class="sxs-lookup"><span data-stu-id="a40c0-230">Example: 20000000b00000000</span></span><br /><br /> <span data-ttu-id="a40c0-231">在本示例中，相关可预测属性为 10000000b。</span><span class="sxs-lookup"><span data-stu-id="a40c0-231">In this case, the related predictable attribute is 10000000b.</span></span>|  
|<span data-ttu-id="a40c0-232">输入属性状态 (11)</span><span class="sxs-lookup"><span data-stu-id="a40c0-232">Input attribute state (11)</span></span>|<span data-ttu-id="a40c0-233">一个由三部分组成的十六进制数字，其中第一个部分始终为 30000000，第二个部分以相关可预测属性的十六进制标识符作为开头，第三个部分表示该值的标识符。</span><span class="sxs-lookup"><span data-stu-id="a40c0-233">A three-part hexadecimal number where the first part is always 30000000, the second part starts with the hexadecimal identifier of the related predictable attribute, and the third part represents the identifier of the value.</span></span><br /><br /> <span data-ttu-id="a40c0-234">例如：30000000b00000000200000000</span><span class="sxs-lookup"><span data-stu-id="a40c0-234">Example: 30000000b00000000200000000</span></span><br /><br /> <span data-ttu-id="a40c0-235">在本示例中，相关可预测属性为 10000000b。</span><span class="sxs-lookup"><span data-stu-id="a40c0-235">In this case, the related predictable attribute is 10000000b.</span></span>|  
  
 <span data-ttu-id="a40c0-236">您可以使用 ID 将输入属性和状态与可预测属性关联。</span><span class="sxs-lookup"><span data-stu-id="a40c0-236">You can use the IDs to relate input attributes and states to a predictable attribute.</span></span> <span data-ttu-id="a40c0-237">例如，以下查询返回表示 `TM_NaiveBayes`模型的输入属性和可预测属性的可能组合的节点名称和标题。</span><span class="sxs-lookup"><span data-stu-id="a40c0-237">For example, the following query returns the names and captions for nodes that represent the possible combinations of input and predictable attributes for the model, `TM_NaiveBayes`.</span></span>  
  
```  
SELECT NODE_NAME, NODE_CAPTION  
FROM TM_NaiveBayes.CONTENT  
WHERE NODE_TYPE = 10  
```  
  
 <span data-ttu-id="a40c0-238">预期的结果：</span><span class="sxs-lookup"><span data-stu-id="a40c0-238">Expected results:</span></span>  
  
|<span data-ttu-id="a40c0-239">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="a40c0-239">NODE_NAME</span></span>|<span data-ttu-id="a40c0-240">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="a40c0-240">NODE_CAPTION</span></span>|  
|----------------|-------------------|  
|<span data-ttu-id="a40c0-241">20000000000000001</span><span class="sxs-lookup"><span data-stu-id="a40c0-241">20000000000000001</span></span>|<span data-ttu-id="a40c0-242">Bike Buyer -> Commute Distance</span><span class="sxs-lookup"><span data-stu-id="a40c0-242">Bike Buyer -> Commute Distance</span></span>|  
|<span data-ttu-id="a40c0-243">20000000000000002</span><span class="sxs-lookup"><span data-stu-id="a40c0-243">20000000000000002</span></span>|<span data-ttu-id="a40c0-244">Bike Buyer -> English Education</span><span class="sxs-lookup"><span data-stu-id="a40c0-244">Bike Buyer -> English Education</span></span>|  
|<span data-ttu-id="a40c0-245">20000000000000003</span><span class="sxs-lookup"><span data-stu-id="a40c0-245">20000000000000003</span></span>|<span data-ttu-id="a40c0-246">Bike Buyer -> English Occupation</span><span class="sxs-lookup"><span data-stu-id="a40c0-246">Bike Buyer -> English Occupation</span></span>|  
|<span data-ttu-id="a40c0-247">20000000000000009</span><span class="sxs-lookup"><span data-stu-id="a40c0-247">20000000000000009</span></span>|<span data-ttu-id="a40c0-248">Bike Buyer -> Marital Status</span><span class="sxs-lookup"><span data-stu-id="a40c0-248">Bike Buyer -> Marital Status</span></span>|  
|<span data-ttu-id="a40c0-249">2000000000000000a</span><span class="sxs-lookup"><span data-stu-id="a40c0-249">2000000000000000a</span></span>|<span data-ttu-id="a40c0-250">Bike Buyer -> Number Children At Home</span><span class="sxs-lookup"><span data-stu-id="a40c0-250">Bike Buyer -> Number Children At Home</span></span>|  
|<span data-ttu-id="a40c0-251">2000000000000000b</span><span class="sxs-lookup"><span data-stu-id="a40c0-251">2000000000000000b</span></span>|<span data-ttu-id="a40c0-252">Bike Buyer -> Region</span><span class="sxs-lookup"><span data-stu-id="a40c0-252">Bike Buyer -> Region</span></span>|  
|<span data-ttu-id="a40c0-253">2000000000000000c</span><span class="sxs-lookup"><span data-stu-id="a40c0-253">2000000000000000c</span></span>|<span data-ttu-id="a40c0-254">Bike Buyer -> Total Children</span><span class="sxs-lookup"><span data-stu-id="a40c0-254">Bike Buyer -> Total Children</span></span>|  
  
 <span data-ttu-id="a40c0-255">接着，您可以使用父节点的 ID 来检索子节点。</span><span class="sxs-lookup"><span data-stu-id="a40c0-255">You can then use the IDs of the parent nodes to retrieve the child nodes.</span></span> <span data-ttu-id="a40c0-256">以下查询检索包含 `Marital Status` 属性的值的节点以及每个节点的概率。</span><span class="sxs-lookup"><span data-stu-id="a40c0-256">The following query retrieves the nodes that contain values for the `Marital Status` attribute, together with the probability of each node.</span></span>  
  
```  
SELECT NODE_NAME, NODE_CAPTION, NODE_PROBABILITY  
FROM TM_NaiveBayes.CONTENT  
WHERE NODE_TYPE = 11  
AND [PARENT_UNIQUE_NAME] = '20000000000000009'  
```  
  
> [!NOTE]  
>  <span data-ttu-id="a40c0-257">必须将列 PARENT_UNIQUE_NAME 的名称括在括号内，以便将它与同名保留关键字区分开来。</span><span class="sxs-lookup"><span data-stu-id="a40c0-257">The name of the column, PARENT_UNIQUE_NAME, must be enclosed in brackets to distinguish it from the reserved keyword of the same name.</span></span>  
  
 <span data-ttu-id="a40c0-258">预期的结果：</span><span class="sxs-lookup"><span data-stu-id="a40c0-258">Expected results:</span></span>  
  
|<span data-ttu-id="a40c0-259">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="a40c0-259">NODE_NAME</span></span>|<span data-ttu-id="a40c0-260">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="a40c0-260">NODE_CAPTION</span></span>|<span data-ttu-id="a40c0-261">NODE_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="a40c0-261">NODE_PROBABILITY</span></span>|  
|----------------|-------------------|-----------------------|  
|<span data-ttu-id="a40c0-262">3000000000000000900000000</span><span class="sxs-lookup"><span data-stu-id="a40c0-262">3000000000000000900000000</span></span>|<span data-ttu-id="a40c0-263">Bike Buyer -> Marital Status = Missing</span><span class="sxs-lookup"><span data-stu-id="a40c0-263">Bike Buyer -> Marital Status = Missing</span></span>|<span data-ttu-id="a40c0-264">0</span><span class="sxs-lookup"><span data-stu-id="a40c0-264">0</span></span>|  
|<span data-ttu-id="a40c0-265">3000000000000000900000001</span><span class="sxs-lookup"><span data-stu-id="a40c0-265">3000000000000000900000001</span></span>|<span data-ttu-id="a40c0-266">Bike Buyer -> Marital Status = S</span><span class="sxs-lookup"><span data-stu-id="a40c0-266">Bike Buyer -> Marital Status = S</span></span>|<span data-ttu-id="a40c0-267">0.457504004</span><span class="sxs-lookup"><span data-stu-id="a40c0-267">0.457504004</span></span>|  
|<span data-ttu-id="a40c0-268">3000000000000000900000002</span><span class="sxs-lookup"><span data-stu-id="a40c0-268">3000000000000000900000002</span></span>|<span data-ttu-id="a40c0-269">Bike Buyer -> Marital Status = M</span><span class="sxs-lookup"><span data-stu-id="a40c0-269">Bike Buyer -> Marital Status = M</span></span>|<span data-ttu-id="a40c0-270">0.542495996</span><span class="sxs-lookup"><span data-stu-id="a40c0-270">0.542495996</span></span>|  
  
##  <a name="node_distribution-table"></a><a name="bkmk_nodedist"></a> <span data-ttu-id="a40c0-271">NODE_DISTRIBUTION 表</span><span class="sxs-lookup"><span data-stu-id="a40c0-271">NODE_DISTRIBUTION Table</span></span>  
 <span data-ttu-id="a40c0-272">嵌套表的 NODE_DISTRIBUTION 列通常包含有关节点中的值的分布统计信息。</span><span class="sxs-lookup"><span data-stu-id="a40c0-272">The nested table column, NODE_DISTRIBUTION, typically contains statistics about the distribution of values in the node.</span></span> <span data-ttu-id="a40c0-273">在 Naive Bayes 模型中，将仅针对下列节点填充此表：</span><span class="sxs-lookup"><span data-stu-id="a40c0-273">In a Naive Bayes model, this table is populated only for the following nodes:</span></span>  
  
|<span data-ttu-id="a40c0-274">节点类型</span><span class="sxs-lookup"><span data-stu-id="a40c0-274">Node Type</span></span>|<span data-ttu-id="a40c0-275">嵌套表内容</span><span class="sxs-lookup"><span data-stu-id="a40c0-275">Content of nested table</span></span>|  
|---------------|-----------------------------|  
|<span data-ttu-id="a40c0-276">模型根 (1)</span><span class="sxs-lookup"><span data-stu-id="a40c0-276">Model root (1)</span></span>|<span data-ttu-id="a40c0-277">空白。</span><span class="sxs-lookup"><span data-stu-id="a40c0-277">Blank.</span></span>|  
|<span data-ttu-id="a40c0-278">边际统计信息节点 (24)</span><span class="sxs-lookup"><span data-stu-id="a40c0-278">Marginal statistics node (24)</span></span>|<span data-ttu-id="a40c0-279">包含整个定型数据集的所有可预测属性和输入属性的摘要信息。</span><span class="sxs-lookup"><span data-stu-id="a40c0-279">Contains summary information for all predictable attributes and input attributes, for entire set of training data.</span></span>|  
|<span data-ttu-id="a40c0-280">可预测属性 (9)</span><span class="sxs-lookup"><span data-stu-id="a40c0-280">Predictable attribute (9)</span></span>|<span data-ttu-id="a40c0-281">空白。</span><span class="sxs-lookup"><span data-stu-id="a40c0-281">Blank.</span></span>|  
|<span data-ttu-id="a40c0-282">输入属性 (10)</span><span class="sxs-lookup"><span data-stu-id="a40c0-282">Input attribute (10)</span></span>|<span data-ttu-id="a40c0-283">空白。</span><span class="sxs-lookup"><span data-stu-id="a40c0-283">Blank.</span></span>|  
|<span data-ttu-id="a40c0-284">输入属性状态 (11)</span><span class="sxs-lookup"><span data-stu-id="a40c0-284">Input attribute state (11)</span></span>|<span data-ttu-id="a40c0-285">包含说明定型数据中可预测值和输入属性值的该特定组合的值的分布统计信息。</span><span class="sxs-lookup"><span data-stu-id="a40c0-285">Contains statistics that describe the distribution of values in the training data for this particular combination of a predictable value and input attribute value.</span></span>|  
  
 <span data-ttu-id="a40c0-286">您可以使用节点 ID 或节点标题检索进一步的详细信息。</span><span class="sxs-lookup"><span data-stu-id="a40c0-286">You can use the node IDs or node captions to retrieve increasing levels of detail.</span></span> <span data-ttu-id="a40c0-287">例如，以下查询检索 NODE_DISTRIBUTION 表中的特定列，以便仅获取与 `'Marital Status = S'`值相关的输入属性节点。</span><span class="sxs-lookup"><span data-stu-id="a40c0-287">For example, the following query retrieves specific columns from the NODE_DISTRIBUTION table for only those input attribute nodes that are related to the value, `'Marital Status = S'`.</span></span>  
  
```  
SELECT FLATTENED NODE_CAPTION,  
(SELECT ATTRIBUTE_NAME, ATTRIBUTE_VALUE, [SUPPORT], [PROBABILITY], VALUETYPE  
FROM NODE_DISTRIBUTION) as t  
FROM TM_NaiveBayes.content  
WHERE NODE_TYPE = 11  
AND NODE_CAPTION = 'Bike Buyer -> Marital Status = S'  
```  
  
 <span data-ttu-id="a40c0-288">预期的结果：</span><span class="sxs-lookup"><span data-stu-id="a40c0-288">Expected results:</span></span>  
  
|<span data-ttu-id="a40c0-289">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="a40c0-289">NODE_CAPTION</span></span>|<span data-ttu-id="a40c0-290">T.ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="a40c0-290">t.ATTRIBUTE_NAME</span></span>|<span data-ttu-id="a40c0-291">t.ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="a40c0-291">t.ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="a40c0-292">t.SUPPORT</span><span class="sxs-lookup"><span data-stu-id="a40c0-292">t.SUPPORT</span></span>|<span data-ttu-id="a40c0-293">t.PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="a40c0-293">t.PROBABILITY</span></span>|<span data-ttu-id="a40c0-294">t.VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="a40c0-294">t.VALUETYPE</span></span>|  
|-------------------|-----------------------|------------------------|---------------|-------------------|-----------------|  
|<span data-ttu-id="a40c0-295">Bike Buyer -> Marital Status = S</span><span class="sxs-lookup"><span data-stu-id="a40c0-295">Bike Buyer -> Marital Status = S</span></span>|<span data-ttu-id="a40c0-296">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="a40c0-296">Bike Buyer</span></span>|<span data-ttu-id="a40c0-297">Missing</span><span class="sxs-lookup"><span data-stu-id="a40c0-297">Missing</span></span>|<span data-ttu-id="a40c0-298">0</span><span class="sxs-lookup"><span data-stu-id="a40c0-298">0</span></span>|<span data-ttu-id="a40c0-299">0</span><span class="sxs-lookup"><span data-stu-id="a40c0-299">0</span></span>|<span data-ttu-id="a40c0-300">1</span><span class="sxs-lookup"><span data-stu-id="a40c0-300">1</span></span>|  
|<span data-ttu-id="a40c0-301">Bike Buyer -> Marital Status = S</span><span class="sxs-lookup"><span data-stu-id="a40c0-301">Bike Buyer -> Marital Status = S</span></span>|<span data-ttu-id="a40c0-302">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="a40c0-302">Bike Buyer</span></span>|<span data-ttu-id="a40c0-303">0</span><span class="sxs-lookup"><span data-stu-id="a40c0-303">0</span></span>|<span data-ttu-id="a40c0-304">3783</span><span class="sxs-lookup"><span data-stu-id="a40c0-304">3783</span></span>|<span data-ttu-id="a40c0-305">0.472934117</span><span class="sxs-lookup"><span data-stu-id="a40c0-305">0.472934117</span></span>|<span data-ttu-id="a40c0-306">4</span><span class="sxs-lookup"><span data-stu-id="a40c0-306">4</span></span>|  
|<span data-ttu-id="a40c0-307">Bike Buyer -> Marital Status = S</span><span class="sxs-lookup"><span data-stu-id="a40c0-307">Bike Buyer -> Marital Status = S</span></span>|<span data-ttu-id="a40c0-308">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="a40c0-308">Bike Buyer</span></span>|<span data-ttu-id="a40c0-309">1</span><span class="sxs-lookup"><span data-stu-id="a40c0-309">1</span></span>|<span data-ttu-id="a40c0-310">4216</span><span class="sxs-lookup"><span data-stu-id="a40c0-310">4216</span></span>|<span data-ttu-id="a40c0-311">0.527065883</span><span class="sxs-lookup"><span data-stu-id="a40c0-311">0.527065883</span></span>|<span data-ttu-id="a40c0-312">4</span><span class="sxs-lookup"><span data-stu-id="a40c0-312">4</span></span>|  
  
 <span data-ttu-id="a40c0-313">在这些结果中，SUPPORT 列的值显示已购买自行车且具有指定婚姻状况的客户的计数。</span><span class="sxs-lookup"><span data-stu-id="a40c0-313">In these results, the value of the SUPPORT column tells you the count of customers with the specified marital status who purchased a bike.</span></span> <span data-ttu-id="a40c0-314">PROBABILITY 列包含每个属性值的概率（仅针对该节点计算）。</span><span class="sxs-lookup"><span data-stu-id="a40c0-314">The PROBABILITY column contains the probability of each attribute value, as calculated for this node only.</span></span> <span data-ttu-id="a40c0-315">有关 NODE_DISTRIBUTION 表中所使用术语的常规定义，请参阅 [挖掘模型内容（Analysis Services - 数据挖掘）](mining-model-content-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="a40c0-315">For general definitions of terms used in the NODE_DISTRIBUTION table, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
###  <a name="information-in-the-marginal-statistics-node"></a><a name="bkmk_margstats"></a> <span data-ttu-id="a40c0-316">边际统计信息节点中的信息</span><span class="sxs-lookup"><span data-stu-id="a40c0-316">Information in the Marginal Statistics Node</span></span>  
 <span data-ttu-id="a40c0-317">在 Naive Bayes 模型中，边际统计节点的嵌套表包含整个定型数据集中的值的分布。</span><span class="sxs-lookup"><span data-stu-id="a40c0-317">In a Naive Bayes model, the nested table for the marginal statistics node contains the distribution of values for the entire set of training data.</span></span> <span data-ttu-id="a40c0-318">例如，下表包含 `TM_NaiveBayes`模型的 NODE_DISTRIBUTION 嵌套表的部分统计信息列表：</span><span class="sxs-lookup"><span data-stu-id="a40c0-318">For example, the following table contains a partial list of the statistics in the nested NODE_DISTRIBUTION table for the model, `TM_NaiveBayes`:</span></span>  
  
|<span data-ttu-id="a40c0-319">ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="a40c0-319">ATTRIBUTE_NAME</span></span>|<span data-ttu-id="a40c0-320">ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="a40c0-320">ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="a40c0-321">Support</span><span class="sxs-lookup"><span data-stu-id="a40c0-321">SUPPORT</span></span>|<span data-ttu-id="a40c0-322">PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="a40c0-322">PROBABILITY</span></span>|<span data-ttu-id="a40c0-323">方差</span><span class="sxs-lookup"><span data-stu-id="a40c0-323">VARIANCE</span></span>|<span data-ttu-id="a40c0-324">VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="a40c0-324">VALUETYPE</span></span>|  
|---------------------|----------------------|-------------|-----------------|--------------|---------------|  
|<span data-ttu-id="a40c0-325">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="a40c0-325">Bike Buyer</span></span>|<span data-ttu-id="a40c0-326">Missing</span><span class="sxs-lookup"><span data-stu-id="a40c0-326">Missing</span></span>|<span data-ttu-id="a40c0-327">0</span><span class="sxs-lookup"><span data-stu-id="a40c0-327">0</span></span>|<span data-ttu-id="a40c0-328">0</span><span class="sxs-lookup"><span data-stu-id="a40c0-328">0</span></span>|<span data-ttu-id="a40c0-329">0</span><span class="sxs-lookup"><span data-stu-id="a40c0-329">0</span></span>|<span data-ttu-id="a40c0-330">1</span><span class="sxs-lookup"><span data-stu-id="a40c0-330">1</span></span>|  
|<span data-ttu-id="a40c0-331">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="a40c0-331">Bike Buyer</span></span>|<span data-ttu-id="a40c0-332">0</span><span class="sxs-lookup"><span data-stu-id="a40c0-332">0</span></span>|<span data-ttu-id="a40c0-333">8869</span><span class="sxs-lookup"><span data-stu-id="a40c0-333">8869</span></span>|<span data-ttu-id="a40c0-334">0.507263784</span><span class="sxs-lookup"><span data-stu-id="a40c0-334">0.507263784</span></span>|<span data-ttu-id="a40c0-335">0</span><span class="sxs-lookup"><span data-stu-id="a40c0-335">0</span></span>|<span data-ttu-id="a40c0-336">4</span><span class="sxs-lookup"><span data-stu-id="a40c0-336">4</span></span>|  
|<span data-ttu-id="a40c0-337">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="a40c0-337">Bike Buyer</span></span>|<span data-ttu-id="a40c0-338">1</span><span class="sxs-lookup"><span data-stu-id="a40c0-338">1</span></span>|<span data-ttu-id="a40c0-339">8615</span><span class="sxs-lookup"><span data-stu-id="a40c0-339">8615</span></span>|<span data-ttu-id="a40c0-340">0.492736216</span><span class="sxs-lookup"><span data-stu-id="a40c0-340">0.492736216</span></span>|<span data-ttu-id="a40c0-341">0</span><span class="sxs-lookup"><span data-stu-id="a40c0-341">0</span></span>|<span data-ttu-id="a40c0-342">4</span><span class="sxs-lookup"><span data-stu-id="a40c0-342">4</span></span>|  
|<span data-ttu-id="a40c0-343">婚姻状况</span><span class="sxs-lookup"><span data-stu-id="a40c0-343">Marital Status</span></span>|<span data-ttu-id="a40c0-344">Missing</span><span class="sxs-lookup"><span data-stu-id="a40c0-344">Missing</span></span>|<span data-ttu-id="a40c0-345">0</span><span class="sxs-lookup"><span data-stu-id="a40c0-345">0</span></span>|<span data-ttu-id="a40c0-346">0</span><span class="sxs-lookup"><span data-stu-id="a40c0-346">0</span></span>|<span data-ttu-id="a40c0-347">0</span><span class="sxs-lookup"><span data-stu-id="a40c0-347">0</span></span>|<span data-ttu-id="a40c0-348">1</span><span class="sxs-lookup"><span data-stu-id="a40c0-348">1</span></span>|  
|<span data-ttu-id="a40c0-349">婚姻状况</span><span class="sxs-lookup"><span data-stu-id="a40c0-349">Marital Status</span></span>|<span data-ttu-id="a40c0-350">S</span><span class="sxs-lookup"><span data-stu-id="a40c0-350">S</span></span>|<span data-ttu-id="a40c0-351">7999</span><span class="sxs-lookup"><span data-stu-id="a40c0-351">7999</span></span>|<span data-ttu-id="a40c0-352">0.457504004</span><span class="sxs-lookup"><span data-stu-id="a40c0-352">0.457504004</span></span>|<span data-ttu-id="a40c0-353">0</span><span class="sxs-lookup"><span data-stu-id="a40c0-353">0</span></span>|<span data-ttu-id="a40c0-354">4</span><span class="sxs-lookup"><span data-stu-id="a40c0-354">4</span></span>|  
|<span data-ttu-id="a40c0-355">婚姻状况</span><span class="sxs-lookup"><span data-stu-id="a40c0-355">Marital Status</span></span>|<span data-ttu-id="a40c0-356">M</span><span class="sxs-lookup"><span data-stu-id="a40c0-356">M</span></span>|<span data-ttu-id="a40c0-357">9485</span><span class="sxs-lookup"><span data-stu-id="a40c0-357">9485</span></span>|<span data-ttu-id="a40c0-358">0.542495996</span><span class="sxs-lookup"><span data-stu-id="a40c0-358">0.542495996</span></span>|<span data-ttu-id="a40c0-359">0</span><span class="sxs-lookup"><span data-stu-id="a40c0-359">0</span></span>|<span data-ttu-id="a40c0-360">4</span><span class="sxs-lookup"><span data-stu-id="a40c0-360">4</span></span>|  
|<span data-ttu-id="a40c0-361">Total Children</span><span class="sxs-lookup"><span data-stu-id="a40c0-361">Total Children</span></span>|<span data-ttu-id="a40c0-362">Missing</span><span class="sxs-lookup"><span data-stu-id="a40c0-362">Missing</span></span>|<span data-ttu-id="a40c0-363">0</span><span class="sxs-lookup"><span data-stu-id="a40c0-363">0</span></span>|<span data-ttu-id="a40c0-364">0</span><span class="sxs-lookup"><span data-stu-id="a40c0-364">0</span></span>|<span data-ttu-id="a40c0-365">0</span><span class="sxs-lookup"><span data-stu-id="a40c0-365">0</span></span>|<span data-ttu-id="a40c0-366">1</span><span class="sxs-lookup"><span data-stu-id="a40c0-366">1</span></span>|  
|<span data-ttu-id="a40c0-367">Total Children</span><span class="sxs-lookup"><span data-stu-id="a40c0-367">Total Children</span></span>|<span data-ttu-id="a40c0-368">0</span><span class="sxs-lookup"><span data-stu-id="a40c0-368">0</span></span>|<span data-ttu-id="a40c0-369">4865</span><span class="sxs-lookup"><span data-stu-id="a40c0-369">4865</span></span>|<span data-ttu-id="a40c0-370">0.278254404</span><span class="sxs-lookup"><span data-stu-id="a40c0-370">0.278254404</span></span>|<span data-ttu-id="a40c0-371">0</span><span class="sxs-lookup"><span data-stu-id="a40c0-371">0</span></span>|<span data-ttu-id="a40c0-372">4</span><span class="sxs-lookup"><span data-stu-id="a40c0-372">4</span></span>|  
|<span data-ttu-id="a40c0-373">Total Children</span><span class="sxs-lookup"><span data-stu-id="a40c0-373">Total Children</span></span>|<span data-ttu-id="a40c0-374">3</span><span class="sxs-lookup"><span data-stu-id="a40c0-374">3</span></span>|<span data-ttu-id="a40c0-375">2093</span><span class="sxs-lookup"><span data-stu-id="a40c0-375">2093</span></span>|<span data-ttu-id="a40c0-376">0.119709449</span><span class="sxs-lookup"><span data-stu-id="a40c0-376">0.119709449</span></span>|<span data-ttu-id="a40c0-377">0</span><span class="sxs-lookup"><span data-stu-id="a40c0-377">0</span></span>|<span data-ttu-id="a40c0-378">4</span><span class="sxs-lookup"><span data-stu-id="a40c0-378">4</span></span>|  
|<span data-ttu-id="a40c0-379">Total Children</span><span class="sxs-lookup"><span data-stu-id="a40c0-379">Total Children</span></span>|<span data-ttu-id="a40c0-380">1</span><span class="sxs-lookup"><span data-stu-id="a40c0-380">1</span></span>|<span data-ttu-id="a40c0-381">3406</span><span class="sxs-lookup"><span data-stu-id="a40c0-381">3406</span></span>|<span data-ttu-id="a40c0-382">0.19480668</span><span class="sxs-lookup"><span data-stu-id="a40c0-382">0.19480668</span></span>|<span data-ttu-id="a40c0-383">0</span><span class="sxs-lookup"><span data-stu-id="a40c0-383">0</span></span>|<span data-ttu-id="a40c0-384">4</span><span class="sxs-lookup"><span data-stu-id="a40c0-384">4</span></span>|  
  
 <span data-ttu-id="a40c0-385">包括 `Bike Buyer` 列的原因在于边际统计信息节点始终包含对可预测属性及其可能值的说明。</span><span class="sxs-lookup"><span data-stu-id="a40c0-385">The `Bike Buyer` column is included because the marginal statistics node always contains a description of the predictable attribute and its possible values.</span></span> <span data-ttu-id="a40c0-386">列出的所有其他列表示在该模型中使用的输入属性以及值。</span><span class="sxs-lookup"><span data-stu-id="a40c0-386">All other columns that are listed represent input attributes, together with the values that were used in the model.</span></span> <span data-ttu-id="a40c0-387">值只能为缺少、离散或离散化值。</span><span class="sxs-lookup"><span data-stu-id="a40c0-387">Values can only be missing, discrete or discretized.</span></span>  
  
 <span data-ttu-id="a40c0-388">在 Naive Bayes 模型中，没有连续属性；因此，所有数值数据均表示为离散 (VALUE_TYPE = 4) 或离散化 (VALUE_TYPE = 5) 的值。</span><span class="sxs-lookup"><span data-stu-id="a40c0-388">In a Naive Bayes model, there can be no continuous attributes; therefore, all numeric data is represented as either discrete (VALUE_TYPE = 4) or discretized (VALUE_TYPE = 5).</span></span>  
  
 <span data-ttu-id="a40c0-389">将 `Missing` 值 (VALUE_TYPE = 1) 添加到每个输入和输出属性，以表示定型数据中未提供的潜在值。</span><span class="sxs-lookup"><span data-stu-id="a40c0-389">A `Missing` value (VALUE_TYPE = 1) is added to every input and output attribute to represent potential values that were not present in the training data.</span></span> <span data-ttu-id="a40c0-390">您必须注意区分字符串“missing”和默认的 `Missing` 值。</span><span class="sxs-lookup"><span data-stu-id="a40c0-390">You must be careful to distinguish between "missing" as a string and the default `Missing` value.</span></span> <span data-ttu-id="a40c0-391">有关详细信息，请参阅 [缺失值（Analysis Services - 数据挖掘）](missing-values-analysis-services-data-mining.md)预定义的这些标志以外，第三方插件还可能具有其他建模标志。</span><span class="sxs-lookup"><span data-stu-id="a40c0-391">For more information, see [Missing Values &#40;Analysis Services - Data Mining&#41;](missing-values-analysis-services-data-mining.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a40c0-392">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a40c0-392">See Also</span></span>  
 <span data-ttu-id="a40c0-393">[挖掘模型内容 &#40;Analysis Services 数据挖掘&#41;](mining-model-content-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="a40c0-393">[Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="a40c0-394">[数据挖掘模型查看器](data-mining-model-viewers.md) </span><span class="sxs-lookup"><span data-stu-id="a40c0-394">[Data Mining Model Viewers](data-mining-model-viewers.md) </span></span>  
 <span data-ttu-id="a40c0-395">[数据挖掘查询](data-mining-queries.md) </span><span class="sxs-lookup"><span data-stu-id="a40c0-395">[Data Mining Queries](data-mining-queries.md) </span></span>  
 [<span data-ttu-id="a40c0-396">Microsoft Naive Bayes Algorithm</span><span class="sxs-lookup"><span data-stu-id="a40c0-396">Microsoft Naive Bayes Algorithm</span></span>](microsoft-naive-bayes-algorithm.md)  
  
  
