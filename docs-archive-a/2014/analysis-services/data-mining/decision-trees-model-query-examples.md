---
title: 决策树模型查询示例 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- decision tree algorithms [Analysis Services]
- content queries [DMX]
- decision trees [Analysis Services]
ms.assetid: ceaf1370-9dd1-4d1a-a143-7f89a723ef80
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7a6b158a42c9ca90bf2cfd2e9b981a1e2a735ccc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688368"
---
# <a name="decision-trees-model-query-examples"></a><span data-ttu-id="fca37-102">决策树模型查询示例</span><span class="sxs-lookup"><span data-stu-id="fca37-102">Decision Trees Model Query Examples</span></span>
  <span data-ttu-id="fca37-103">在创建针对数据挖掘模型的查询时，您既可以创建内容查询，也可以创建预测查询。内容查询提供有关分析过程中发现的模式的详细信息，而预测查询则使用模型中的模式对新数据进行预测。</span><span class="sxs-lookup"><span data-stu-id="fca37-103">When you create a query against a data mining model, you can create a content query, which provides details about the patterns discovered in analysis, or you can create a prediction query, which uses the patterns in the model to make predictions for new data.</span></span> <span data-ttu-id="fca37-104">例如，决策树模型的内容查询可能提供有关树在每个级别上的事例数的统计信息或者区分事例的规则。</span><span class="sxs-lookup"><span data-stu-id="fca37-104">For example, a content query for a decision trees model might provide statistics about the number of cases at each level of the tree, or the rules that differentiate between cases.</span></span> <span data-ttu-id="fca37-105">而预测查询则是将模型映射到新数据，以生成建议、分类等等。</span><span class="sxs-lookup"><span data-stu-id="fca37-105">Alternatively, a prediction query maps the model to new data in order to generate recommendations, classifications, and so forth.</span></span> <span data-ttu-id="fca37-106">您还可以使用查询来检索有关模型的元数据。</span><span class="sxs-lookup"><span data-stu-id="fca37-106">You can also retrieve metadata about the model by using a query.</span></span>  
  
 <span data-ttu-id="fca37-107">本节说明如何为基于 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 决策树算法的模型创建查询。</span><span class="sxs-lookup"><span data-stu-id="fca37-107">This section explains how to create queries for models that are based on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm.</span></span>  
  
 <span data-ttu-id="fca37-108">**内容查询**</span><span class="sxs-lookup"><span data-stu-id="fca37-108">**Content Queries**</span></span>  
  
 [<span data-ttu-id="fca37-109">通过数据挖掘架构行集检索模型参数</span><span class="sxs-lookup"><span data-stu-id="fca37-109">Retrieving Model Parameters from the Data Mining Schema Rowset</span></span>](#bkmk_Query1)  
  
 [<span data-ttu-id="fca37-110">使用 DMX 获取与模型中的树有关的详细信息</span><span class="sxs-lookup"><span data-stu-id="fca37-110">Getting Details about Trees in the Model by Using DMX</span></span>](#bkmk_Query2)  
  
 [<span data-ttu-id="fca37-111">从模型中检索子树</span><span class="sxs-lookup"><span data-stu-id="fca37-111">Retrieving Subtrees from the Model</span></span>](#bkmk_Query3)  
  
 <span data-ttu-id="fca37-112">**预测查询**</span><span class="sxs-lookup"><span data-stu-id="fca37-112">**Prediction Queries**</span></span>  
  
 [<span data-ttu-id="fca37-113">返回具有概率的预测</span><span class="sxs-lookup"><span data-stu-id="fca37-113">Returning Predictions with Probabilities</span></span>](#bkmk_Query4)  
  
 [<span data-ttu-id="fca37-114">根据决策树模型预测关联</span><span class="sxs-lookup"><span data-stu-id="fca37-114">Predicting Associations from a Decision Trees Model</span></span>](#bkmk_Query5)  
  
 [<span data-ttu-id="fca37-115">从决策树模型中检索回归公式</span><span class="sxs-lookup"><span data-stu-id="fca37-115">Retrieving a Regression Formula from a Decision Trees Model</span></span>](#bkmk_Query6)  
  
##  <a name="finding-information-about-a-decision-trees-model"></a><a name="bkmk_top2"></a><span data-ttu-id="fca37-116">查找有关决策树模型的信息</span><span class="sxs-lookup"><span data-stu-id="fca37-116">Finding Information about a Decision Trees Model</span></span>  
 <span data-ttu-id="fca37-117">若要针对决策树模型内容创建有意义的查询，您应该了解模型内容的结构以及哪些节点类型存储哪类信息。</span><span class="sxs-lookup"><span data-stu-id="fca37-117">To create meaningful queries on the content of a decision trees model, you should understand the structure of the model content, and which node types store what kind of information.</span></span> <span data-ttu-id="fca37-118">有关详细信息，请参阅 [决策树模型的挖掘模型内容（Analysis Services - 数据挖掘）](mining-model-content-for-decision-tree-models-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="fca37-118">For more information, see [Mining Model Content for Decision Tree Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-decision-tree-models-analysis-services-data-mining.md).</span></span>  
  
###  <a name="sample-query-1-retrieving-model-parameters-from-the-data-mining-schema-rowset"></a><a name="bkmk_Query1"></a><span data-ttu-id="fca37-119">示例查询1：从数据挖掘架构行集中检索模型参数</span><span class="sxs-lookup"><span data-stu-id="fca37-119">Sample Query 1: Retrieving Model Parameters from the Data Mining Schema Rowset</span></span>  
 <span data-ttu-id="fca37-120">通过查询数据挖掘架构行集，您可以找到有关模型的元数据，如模型创建时间、上次处理模型的时间、模型基于的挖掘结构的名称以及用作可预测属性的列的名称。</span><span class="sxs-lookup"><span data-stu-id="fca37-120">By querying the data mining schema rowset, you can find metadata about the model, such as when it was created, when the model was last processed, the name of the mining structure that the model is based on, and the name of the column used as the predictable attribute.</span></span> <span data-ttu-id="fca37-121">您还可以返回首次创建模型时所使用的参数。</span><span class="sxs-lookup"><span data-stu-id="fca37-121">You can also return the parameters that were used when the model was first created.</span></span>  
  
```  
select MINING_PARAMETERS   
from $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'TM_Decision Tree'  
```  
  
 <span data-ttu-id="fca37-122">示例结果：</span><span class="sxs-lookup"><span data-stu-id="fca37-122">Sample results:</span></span>  
  
 <span data-ttu-id="fca37-123">MINING_PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fca37-123">MINING_PARAMETERS</span></span>  
  
 <span data-ttu-id="fca37-124">COMPLEXITY_PENALTY=0.5, MAXIMUM_INPUT_ATTRIBUTES=255,MAXIMUM_OUTPUT_ATTRIBUTES=255,MINIMUM_SUPPORT=10,SCORE_METHOD=4,SPLIT_METHOD=3,FORCE_REGRESSOR=</span><span class="sxs-lookup"><span data-stu-id="fca37-124">COMPLEXITY_PENALTY=0.5, MAXIMUM_INPUT_ATTRIBUTES=255,MAXIMUM_OUTPUT_ATTRIBUTES=255,MINIMUM_SUPPORT=10,SCORE_METHOD=4,SPLIT_METHOD=3,FORCE_REGRESSOR=</span></span>  
  
###  <a name="sample-query-2-returning-details-about-the-model-content-by-using-dmx"></a><a name="bkmk_Query2"></a><span data-ttu-id="fca37-125">示例查询2：使用 DMX 返回有关模型内容的详细信息</span><span class="sxs-lookup"><span data-stu-id="fca37-125">Sample Query 2: Returning Details about the Model Content by Using DMX</span></span>  
 <span data-ttu-id="fca37-126">下面的查询返回有关在 [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md)中生成模型时创建的决策树的一些基本信息。</span><span class="sxs-lookup"><span data-stu-id="fca37-126">The following query returns some basic information about the decision trees that were created when you built the model in the [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md).</span></span> <span data-ttu-id="fca37-127">每个树状结构都存储在自己的节点中。</span><span class="sxs-lookup"><span data-stu-id="fca37-127">Each tree structure is stored in its own node.</span></span> <span data-ttu-id="fca37-128">由于此模型包含单个可预测属性，因此只有一个树节点。</span><span class="sxs-lookup"><span data-stu-id="fca37-128">Because this model contains a single predictable attribute, there is only one tree node.</span></span> <span data-ttu-id="fca37-129">但是，如果使用决策树算法创建关联模型，则可能有成百上千的树，每种产品对应一个树。</span><span class="sxs-lookup"><span data-stu-id="fca37-129">However, if you create an association model by using the Decision Trees algorithm, there might be hundreds of trees, one for each product.</span></span>  
  
 <span data-ttu-id="fca37-130">此查询返回类型 2 的所有节点，这些节点是表示特定可预测属性的树的顶级节点。</span><span class="sxs-lookup"><span data-stu-id="fca37-130">This query returns all the nodes of type 2, which are the top level nodes of a tree that represents a particular predictable attribute.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fca37-131">必须将 `CHILDREN_CARDINALITY` 列括在括号中，以便将它与同名的 MDX 保留关键字区分开来。</span><span class="sxs-lookup"><span data-stu-id="fca37-131">The column, `CHILDREN_CARDINALITY`, must be enclosed in brackets to distinguish it from the MDX reserved keyword of the same name.</span></span>  
  
```  
SELECT MODEL_NAME, NODE_NAME, NODE_CAPTION,   
NODE_SUPPORT, [CHILDREN_CARDINALITY]  
FROM TM_DecisionTrees.CONTENT  
WHERE NODE_TYPE = 2  
```  
  
 <span data-ttu-id="fca37-132">示例结果：</span><span class="sxs-lookup"><span data-stu-id="fca37-132">Example results:</span></span>  
  
|<span data-ttu-id="fca37-133">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="fca37-133">MODEL_NAME</span></span>|<span data-ttu-id="fca37-134">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="fca37-134">NODE_NAME</span></span>|<span data-ttu-id="fca37-135">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="fca37-135">NODE_CAPTION</span></span>|<span data-ttu-id="fca37-136">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="fca37-136">NODE_SUPPORT</span></span>|<span data-ttu-id="fca37-137">CHILDREN_CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="fca37-137">CHILDREN_CARDINALITY</span></span>|  
|-----------------|----------------|-------------------|-------------------|---------------------------|  
|<span data-ttu-id="fca37-138">TM_DecisionTree</span><span class="sxs-lookup"><span data-stu-id="fca37-138">TM_DecisionTree</span></span>|<span data-ttu-id="fca37-139">000000001</span><span class="sxs-lookup"><span data-stu-id="fca37-139">000000001</span></span>|<span data-ttu-id="fca37-140">全部</span><span class="sxs-lookup"><span data-stu-id="fca37-140">All</span></span>|<span data-ttu-id="fca37-141">12939</span><span class="sxs-lookup"><span data-stu-id="fca37-141">12939</span></span>|<span data-ttu-id="fca37-142">5</span><span class="sxs-lookup"><span data-stu-id="fca37-142">5</span></span>|  
  
 <span data-ttu-id="fca37-143">这些结果是什么意思？</span><span class="sxs-lookup"><span data-stu-id="fca37-143">What do these results tell you?</span></span> <span data-ttu-id="fca37-144">在决策树模型中，特定节点的基数指明该节点有多少个直属子级。</span><span class="sxs-lookup"><span data-stu-id="fca37-144">In a decision trees model, the cardinality of a particular node tells you how many immediate children that node has.</span></span> <span data-ttu-id="fca37-145">此节点的基数是 5，这意味着该模型将潜在的自行车购买者的目标总体分成了 5 个子组。</span><span class="sxs-lookup"><span data-stu-id="fca37-145">The cardinality for this node is 5, meaning that the model divided the target population of potential bike buyers into 5 subgroups.</span></span>  
  
 <span data-ttu-id="fca37-146">下面的相关查询返回这 5 个子组的子级以及子节点中属性和值的分布。</span><span class="sxs-lookup"><span data-stu-id="fca37-146">The following related query returns the children for these five subgroups, together with the distribution of attributes and values in the child nodes.</span></span> <span data-ttu-id="fca37-147">由于统计信息（如支持、概率和方差）存储在嵌套表 `NODE_DISTRIBUTION`中，因此本示例使用 `FLATTENED` 关键字输出嵌套表列。</span><span class="sxs-lookup"><span data-stu-id="fca37-147">Because statistics such as support, probability, and variance are stored in the nested table, `NODE_DISTRIBUTION`, this example uses the `FLATTENED` keyword to output the nested table columns.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fca37-148">必须将嵌套表列 `SUPPORT` 括在括号中，以便将它与同名保留关键字区分开来。</span><span class="sxs-lookup"><span data-stu-id="fca37-148">The nested table column, `SUPPORT`, must be enclosed in brackets to distinguish it from the reserved keyword of the same name.</span></span>  
  
```  
SELECT FLATTENED NODE_NAME, NODE_CAPTION,  
(SELECT ATTRIBUTE_NAME, ATTRIBUTE_VALUE, [SUPPORT]  
FROM NODE_DISTRIBUTION) AS t  
FROM TM_DecisionTree.CONTENT  
WHERE [PARENT_UNIQUE_NAME] = '000000001'  
```  
  
 <span data-ttu-id="fca37-149">示例结果：</span><span class="sxs-lookup"><span data-stu-id="fca37-149">Example results:</span></span>  
  
|<span data-ttu-id="fca37-150">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="fca37-150">NODE_NAME</span></span>|<span data-ttu-id="fca37-151">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="fca37-151">NODE_CAPTION</span></span>|<span data-ttu-id="fca37-152">T.ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="fca37-152">T.ATTRIBUTE_NAME</span></span>|<span data-ttu-id="fca37-153">T.ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="fca37-153">T.ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="fca37-154">Support</span><span class="sxs-lookup"><span data-stu-id="fca37-154">SUPPORT</span></span>|  
|----------------|-------------------|-----------------------|------------------------|-------------|  
|<span data-ttu-id="fca37-155">00000000100</span><span class="sxs-lookup"><span data-stu-id="fca37-155">00000000100</span></span>|<span data-ttu-id="fca37-156">Number Cars Owned = 0</span><span class="sxs-lookup"><span data-stu-id="fca37-156">Number Cars Owned = 0</span></span>|<span data-ttu-id="fca37-157">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="fca37-157">Bike Buyer</span></span>|<span data-ttu-id="fca37-158">Missing</span><span class="sxs-lookup"><span data-stu-id="fca37-158">Missing</span></span>|<span data-ttu-id="fca37-159">0</span><span class="sxs-lookup"><span data-stu-id="fca37-159">0</span></span>|  
|<span data-ttu-id="fca37-160">00000000100</span><span class="sxs-lookup"><span data-stu-id="fca37-160">00000000100</span></span>|<span data-ttu-id="fca37-161">Number Cars Owned = 0</span><span class="sxs-lookup"><span data-stu-id="fca37-161">Number Cars Owned = 0</span></span>|<span data-ttu-id="fca37-162">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="fca37-162">Bike Buyer</span></span>|<span data-ttu-id="fca37-163">0</span><span class="sxs-lookup"><span data-stu-id="fca37-163">0</span></span>|<span data-ttu-id="fca37-164">1067</span><span class="sxs-lookup"><span data-stu-id="fca37-164">1067</span></span>|  
|<span data-ttu-id="fca37-165">00000000100</span><span class="sxs-lookup"><span data-stu-id="fca37-165">00000000100</span></span>|<span data-ttu-id="fca37-166">Number Cars Owned = 0</span><span class="sxs-lookup"><span data-stu-id="fca37-166">Number Cars Owned = 0</span></span>|<span data-ttu-id="fca37-167">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="fca37-167">Bike Buyer</span></span>|<span data-ttu-id="fca37-168">1</span><span class="sxs-lookup"><span data-stu-id="fca37-168">1</span></span>|<span data-ttu-id="fca37-169">1875</span><span class="sxs-lookup"><span data-stu-id="fca37-169">1875</span></span>|  
|<span data-ttu-id="fca37-170">00000000101</span><span class="sxs-lookup"><span data-stu-id="fca37-170">00000000101</span></span>|<span data-ttu-id="fca37-171">Number Cars Owned = 3</span><span class="sxs-lookup"><span data-stu-id="fca37-171">Number Cars Owned = 3</span></span>|<span data-ttu-id="fca37-172">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="fca37-172">Bike Buyer</span></span>|<span data-ttu-id="fca37-173">Missing</span><span class="sxs-lookup"><span data-stu-id="fca37-173">Missing</span></span>|<span data-ttu-id="fca37-174">0</span><span class="sxs-lookup"><span data-stu-id="fca37-174">0</span></span>|  
|<span data-ttu-id="fca37-175">00000000101</span><span class="sxs-lookup"><span data-stu-id="fca37-175">00000000101</span></span>|<span data-ttu-id="fca37-176">Number Cars Owned = 3</span><span class="sxs-lookup"><span data-stu-id="fca37-176">Number Cars Owned = 3</span></span>|<span data-ttu-id="fca37-177">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="fca37-177">Bike Buyer</span></span>|<span data-ttu-id="fca37-178">0</span><span class="sxs-lookup"><span data-stu-id="fca37-178">0</span></span>|<span data-ttu-id="fca37-179">678</span><span class="sxs-lookup"><span data-stu-id="fca37-179">678</span></span>|  
|<span data-ttu-id="fca37-180">00000000101</span><span class="sxs-lookup"><span data-stu-id="fca37-180">00000000101</span></span>|<span data-ttu-id="fca37-181">Number Cars Owned = 3</span><span class="sxs-lookup"><span data-stu-id="fca37-181">Number Cars Owned = 3</span></span>|<span data-ttu-id="fca37-182">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="fca37-182">Bike Buyer</span></span>|<span data-ttu-id="fca37-183">1</span><span class="sxs-lookup"><span data-stu-id="fca37-183">1</span></span>|<span data-ttu-id="fca37-184">473</span><span class="sxs-lookup"><span data-stu-id="fca37-184">473</span></span>|  
  
 <span data-ttu-id="fca37-185">根据这些结果，你可以判断买了自行车的客户 (`[Bike Buyer]` = 1) ，1067的客户的汽车和473客户有3辆车。</span><span class="sxs-lookup"><span data-stu-id="fca37-185">From these results, you can tell that of the customers who bought a bike (`[Bike Buyer]` = 1), 1067 customers had 0 cars and 473 customers had 3 cars.</span></span>  
  
###  <a name="sample-query-3-retrieving-subtrees-from-the-model"></a><a name="bkmk_Query3"></a><span data-ttu-id="fca37-186">示例查询3：从模型中检索子树</span><span class="sxs-lookup"><span data-stu-id="fca37-186">Sample Query 3: Retrieving Subtrees from the Model</span></span>  
 <span data-ttu-id="fca37-187">假定您希望查找有关购买了自行车的客户的更多信息。</span><span class="sxs-lookup"><span data-stu-id="fca37-187">Suppose you wanted to discover more about the customers who did buy a bike.</span></span> <span data-ttu-id="fca37-188">你可以通过在查询中使用 [IsDescendant (DMX)](/sql/dmx/isdescendant-dmx) 函数来查看任何子树的其他详细信息，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="fca37-188">You can view additional detail for any of the sub-trees by using the [IsDescendant &#40;DMX&#41;](/sql/dmx/isdescendant-dmx) function in the query, as shown in the following example.</span></span> <span data-ttu-id="fca37-189">通过从包含 42 岁以上的客户的树中检索叶节点 (NODE_TYPE = 4)，查询将返回自行车购买者的计数。</span><span class="sxs-lookup"><span data-stu-id="fca37-189">The query returns the count of bike purchasers by retrieving leaf nodes (NODE_TYPE = 4) from the tree that contains customers who are over 42 years of age.</span></span> <span data-ttu-id="fca37-190">查询将嵌套表中的行限定为其中 Bike Buyer = 1 的行。</span><span class="sxs-lookup"><span data-stu-id="fca37-190">The query restricts rows from the nested table to those where Bike Buyer = 1.</span></span>  
  
```  
SELECT FLATTENED NODE_NAME, NODE_CAPTION,NODE_TYPE,  
(  
SELECT [SUPPORT] FROM NODE_DISTRIBUTION WHERE ATTRIBUTE_NAME = 'Bike Buyer' AND ATTRIBUTE_VALUE = '1'  
) AS t  
FROM TM_DecisionTree.CONTENT  
WHERE ISDESCENDANT('0000000010001')  
AND NODE_TYPE = 4  
```  
  
 <span data-ttu-id="fca37-191">示例结果：</span><span class="sxs-lookup"><span data-stu-id="fca37-191">Example results:</span></span>  
  
|<span data-ttu-id="fca37-192">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="fca37-192">NODE_NAME</span></span>|<span data-ttu-id="fca37-193">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="fca37-193">NODE_CAPTION</span></span>|<span data-ttu-id="fca37-194">t.SUPPORT</span><span class="sxs-lookup"><span data-stu-id="fca37-194">t.SUPPORT</span></span>|  
|----------------|-------------------|---------------|  
|<span data-ttu-id="fca37-195">000000001000100</span><span class="sxs-lookup"><span data-stu-id="fca37-195">000000001000100</span></span>|<span data-ttu-id="fca37-196">Yearly Income >= 26000 and < 42000</span><span class="sxs-lookup"><span data-stu-id="fca37-196">Yearly Income >= 26000 and < 42000</span></span>|<span data-ttu-id="fca37-197">266</span><span class="sxs-lookup"><span data-stu-id="fca37-197">266</span></span>|  
|<span data-ttu-id="fca37-198">00000000100010100</span><span class="sxs-lookup"><span data-stu-id="fca37-198">00000000100010100</span></span>|<span data-ttu-id="fca37-199">Total Children = 3</span><span class="sxs-lookup"><span data-stu-id="fca37-199">Total Children = 3</span></span>|<span data-ttu-id="fca37-200">75</span><span class="sxs-lookup"><span data-stu-id="fca37-200">75</span></span>|  
|<span data-ttu-id="fca37-201">0000000010001010100</span><span class="sxs-lookup"><span data-stu-id="fca37-201">0000000010001010100</span></span>|<span data-ttu-id="fca37-202">Number Children At Home = 1</span><span class="sxs-lookup"><span data-stu-id="fca37-202">Number Children At Home = 1</span></span>|<span data-ttu-id="fca37-203">75</span><span class="sxs-lookup"><span data-stu-id="fca37-203">75</span></span>|  
  
## <a name="making-predictions-using-a-decision-trees-model"></a><span data-ttu-id="fca37-204">使用决策树模型进行预测</span><span class="sxs-lookup"><span data-stu-id="fca37-204">Making Predictions using a Decision Trees Model</span></span>  
 <span data-ttu-id="fca37-205">由于决策树可用于各种任务（包括分类、回归以及关联），因此，在针对决策树模型创建预测查询时，您可以使用许多选项。</span><span class="sxs-lookup"><span data-stu-id="fca37-205">Because decision trees can be used for various tasks, including classification, regression, and even association, when you create a prediction query on a decision tree model you have many options available to you.</span></span> <span data-ttu-id="fca37-206">必须了解创建模型的目的才能明白预测的结果。</span><span class="sxs-lookup"><span data-stu-id="fca37-206">You must understand the purpose for which the model was created to understand the results of prediction.</span></span> <span data-ttu-id="fca37-207">以下查询示例说明了三种不同的情况：</span><span class="sxs-lookup"><span data-stu-id="fca37-207">The following query samples illustrate three different scenarios:</span></span>  
  
-   <span data-ttu-id="fca37-208">返回分类模型的预测以及正确预测的概率，然后根据该概率筛选结果；</span><span class="sxs-lookup"><span data-stu-id="fca37-208">Returning a prediction for a classification model, together with the probability of the prediction being correct, and then filtering the results by the probability;</span></span>  
  
-   <span data-ttu-id="fca37-209">创建一个单独查询来预测关联；</span><span class="sxs-lookup"><span data-stu-id="fca37-209">Creating a singleton query to predict associations;</span></span>  
  
-   <span data-ttu-id="fca37-210">检索部分决策树的回归公式，其中输入和输出之间的关系是线性的。</span><span class="sxs-lookup"><span data-stu-id="fca37-210">Retrieving the regression formula for a part of a decision tree where the relationship between the input and output is linear.</span></span>  
  
###  <a name="sample-query-4-returning-predictions-with-probabilities"></a><a name="bkmk_Query4"></a><span data-ttu-id="fca37-211">示例查询4：返回具有概率的预测</span><span class="sxs-lookup"><span data-stu-id="fca37-211">Sample Query 4: Returning Predictions with Probabilities</span></span>  
 <span data-ttu-id="fca37-212">下面的示例查询使用在 [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md)中创建的决策树模型。</span><span class="sxs-lookup"><span data-stu-id="fca37-212">The following sample query uses the decision tree model that was created in the [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md).</span></span> <span data-ttu-id="fca37-213">该查询在 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] DW 的表 dbo.ProspectiveBuyers 中遍历新的示例数据集，以便预测新数据集中的哪些客户将购买自行车。</span><span class="sxs-lookup"><span data-stu-id="fca37-213">The query passes in a new set of sample data, from the table dbo.ProspectiveBuyers in [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] DW, to predict which of the customers in the new data set will purchase a bike.</span></span>  
  
 <span data-ttu-id="fca37-214">查询使用预测函数 [PredictHistogram (DMX)](/sql/dmx/predicthistogram-dmx)，该函数返回一个嵌套表，其中包含有关该模型发现的概率的有用信息。</span><span class="sxs-lookup"><span data-stu-id="fca37-214">The query uses the prediction function [PredictHistogram &#40;DMX&#41;](/sql/dmx/predicthistogram-dmx), which returns a nested table that contains useful information about the probabilities discovered by the model.</span></span> <span data-ttu-id="fca37-215">该查询的最后的 WHERE 子句将筛选结果，以便仅返回预测购买自行车的概率大于 0% 的那些潜在客户。</span><span class="sxs-lookup"><span data-stu-id="fca37-215">The final WHERE clause of the query filters the results to return only those customers who are predicted as likely to buy a bike, with a probability greater than 0%.</span></span>  
  
```  
SELECT  
  [TM_DecisionTree].[Bike Buyer],  
  PredictHistogram([Bike Buyer]) as Results  
From  
  [TM_DecisionTree]  
PREDICTION JOIN  
  OPENQUERY([Adventure Works DW Multidimensional 2012],  
    'SELECT  
      [FirstName],  
      [LastName],  
      [MaritalStatus],  
      [Gender],  
      [YearlyIncome],  
      [TotalChildren],  
      [NumberChildrenAtHome],  
      [HouseOwnerFlag],  
      [NumberCarsOwned]  
    FROM  
      [dbo].[ProspectiveBuyer]  
    ') AS t  
ON  
  [TM_DecisionTree].[First Name] = t.[FirstName] AND  
  [TM_DecisionTree].[Last Name] = t.[LastName] AND  
  [TM_DecisionTree].[Marital Status] = t.[MaritalStatus] AND  
  [TM_DecisionTree].[Gender] = t.[Gender] AND  
  [TM_DecisionTree].[Yearly Income] = t.[YearlyIncome] AND  
  [TM_DecisionTree].[Total Children] = t.[TotalChildren] AND  
  [TM_DecisionTree].[Number Children At Home] = t.[NumberChildrenAtHome] AND  
  [TM_DecisionTree].[House Owner Flag] = t.[HouseOwnerFlag] AND  
  [TM_DecisionTree].[Number Cars Owned] = t.[NumberCarsOwned]  
WHERE [Bike Buyer] = 1  
AND PredictProbability([Bike Buyer]) >'.05'  
```  
  
 <span data-ttu-id="fca37-216">默认情况下， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 将返回具有列标签 **Expression**的嵌套表。</span><span class="sxs-lookup"><span data-stu-id="fca37-216">By default, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] returns nested tables with the column label, **Expression**.</span></span> <span data-ttu-id="fca37-217">可通过对返回的列使用别名来更改此标签。</span><span class="sxs-lookup"><span data-stu-id="fca37-217">You can change this label by aliasing the column that is returned.</span></span> <span data-ttu-id="fca37-218">如果使用别名，则该别名（本例中为 **Results**）将用作嵌套表中的列标题和值。</span><span class="sxs-lookup"><span data-stu-id="fca37-218">If you do this, the alias (in this case, **Results**) is used as both the column heading and as the value in the nested table.</span></span> <span data-ttu-id="fca37-219">必须展开嵌套表才能查看结果。</span><span class="sxs-lookup"><span data-stu-id="fca37-219">You must expand the nested table to see the results.</span></span>  
  
 <span data-ttu-id="fca37-220">自行车购买者 = 1 的示例结果：</span><span class="sxs-lookup"><span data-stu-id="fca37-220">Example results where Bike Buyer = 1:</span></span>  
  
|<span data-ttu-id="fca37-221">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="fca37-221">Bike Buyer</span></span>|<span data-ttu-id="fca37-222">$SUPPORT</span><span class="sxs-lookup"><span data-stu-id="fca37-222">$SUPPORT</span></span>|<span data-ttu-id="fca37-223">$PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="fca37-223">$PROBABILITY</span></span>|<span data-ttu-id="fca37-224">$ADJUSTEDPROBABILITY</span><span class="sxs-lookup"><span data-stu-id="fca37-224">$ADJUSTEDPROBABILITY</span></span>|<span data-ttu-id="fca37-225">$VARIANCE</span><span class="sxs-lookup"><span data-stu-id="fca37-225">$VARIANCE</span></span>|<span data-ttu-id="fca37-226">$STDEV</span><span class="sxs-lookup"><span data-stu-id="fca37-226">$STDEV</span></span>|  
|----------------|--------------|------------------|--------------------------|---------------|------------|  
|<span data-ttu-id="fca37-227">1</span><span class="sxs-lookup"><span data-stu-id="fca37-227">1</span></span>|<span data-ttu-id="fca37-228">2540</span><span class="sxs-lookup"><span data-stu-id="fca37-228">2540</span></span>|<span data-ttu-id="fca37-229">0.634849242045644</span><span class="sxs-lookup"><span data-stu-id="fca37-229">0.634849242045644</span></span>|<span data-ttu-id="fca37-230">0.013562168281562</span><span class="sxs-lookup"><span data-stu-id="fca37-230">0.013562168281562</span></span>|<span data-ttu-id="fca37-231">0</span><span class="sxs-lookup"><span data-stu-id="fca37-231">0</span></span>|<span data-ttu-id="fca37-232">0</span><span class="sxs-lookup"><span data-stu-id="fca37-232">0</span></span>|  
|<span data-ttu-id="fca37-233">0</span><span class="sxs-lookup"><span data-stu-id="fca37-233">0</span></span>|<span data-ttu-id="fca37-234">1460</span><span class="sxs-lookup"><span data-stu-id="fca37-234">1460</span></span>|<span data-ttu-id="fca37-235">0.364984174579377</span><span class="sxs-lookup"><span data-stu-id="fca37-235">0.364984174579377</span></span>|<span data-ttu-id="fca37-236">0.00661336932550915</span><span class="sxs-lookup"><span data-stu-id="fca37-236">0.00661336932550915</span></span>|<span data-ttu-id="fca37-237">0</span><span class="sxs-lookup"><span data-stu-id="fca37-237">0</span></span>|<span data-ttu-id="fca37-238">0</span><span class="sxs-lookup"><span data-stu-id="fca37-238">0</span></span>|  
||<span data-ttu-id="fca37-239">0</span><span class="sxs-lookup"><span data-stu-id="fca37-239">0</span></span>|<span data-ttu-id="fca37-240">0.000166583374979177</span><span class="sxs-lookup"><span data-stu-id="fca37-240">0.000166583374979177</span></span>|<span data-ttu-id="fca37-241">0.000166583374979177</span><span class="sxs-lookup"><span data-stu-id="fca37-241">0.000166583374979177</span></span>|<span data-ttu-id="fca37-242">0</span><span class="sxs-lookup"><span data-stu-id="fca37-242">0</span></span>|<span data-ttu-id="fca37-243">0</span><span class="sxs-lookup"><span data-stu-id="fca37-243">0</span></span>|  
  
 <span data-ttu-id="fca37-244">如果提供程序不支持分层行集（如此处显示的结果），则可以在查询中使用 FLATTENED 关键字将结果返回为包含 Null（替代重复的列值）的表。</span><span class="sxs-lookup"><span data-stu-id="fca37-244">If your provider does not support hierarchical rowsets, such as those shown here, you can use the FLATTENED keyword in the query to return the results as a table that contains nulls in place of the repeated column values.</span></span> <span data-ttu-id="fca37-245">有关详细信息，请参阅[嵌套表（Analysis Services - 数据挖掘）](nested-tables-analysis-services-data-mining.md)或[了解 DMX Select 语句](/sql/dmx/understanding-the-dmx-select-statement)。</span><span class="sxs-lookup"><span data-stu-id="fca37-245">For more information, see [Nested Tables &#40;Analysis Services - Data Mining&#41;](nested-tables-analysis-services-data-mining.md) or [Understanding the DMX Select Statement](/sql/dmx/understanding-the-dmx-select-statement).</span></span>  
  
###  <a name="sample-query-5-predicting-associations-from-a-decision-trees-model"></a><a name="bkmk_Query5"></a><span data-ttu-id="fca37-246">示例查询5：根据决策树模型预测关联</span><span class="sxs-lookup"><span data-stu-id="fca37-246">Sample Query 5: Predicting Associations from a Decision Trees Model</span></span>  
 <span data-ttu-id="fca37-247">下面的示例查询基于关联挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="fca37-247">The following sample query is based on the Association mining structure.</span></span> <span data-ttu-id="fca37-248">为了按照此示例内容进行操作，您可以在此挖掘结构中添加一个新模型，并且选择 Microsoft 决策树作为算法。</span><span class="sxs-lookup"><span data-stu-id="fca37-248">To follow along with this example, you can add a new model to this mining structure, and select Microsoft Decision Trees as the algorithm.</span></span> <span data-ttu-id="fca37-249">有关如何创建关联挖掘结构的详细信息，请参阅[第 3 课：生成市场篮方案（数据挖掘中级教程）](../../tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="fca37-249">For more information on how to create the Association mining structure, see [Lesson 3: Building a Market Basket Scenario &#40;Intermediate Data Mining Tutorial&#41;](../../tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md).</span></span>  
  
 <span data-ttu-id="fca37-250">以下示例查询是一个单独查询，您可以在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中轻松创建该查询，方法是选择字段，然后从下拉列表中选择这些字段的值。</span><span class="sxs-lookup"><span data-stu-id="fca37-250">The following sample query is a singleton query, which you can create easily in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] by choosing fields and then selecting values for those fields from a drop-down list.</span></span>  
  
```  
SELECT PredictAssociation([DT_Association].[v Assoc Seq Line Items],3)  
FROM  
  [DT_Association]  
NATURAL PREDICTION JOIN  
(SELECT (SELECT 'Patch kit' AS [Model]) AS [v Assoc Seq Line Items]) AS t  
```  
  
 <span data-ttu-id="fca37-251">预期的结果：</span><span class="sxs-lookup"><span data-stu-id="fca37-251">Expected results:</span></span>  
  
|<span data-ttu-id="fca37-252">模型</span><span class="sxs-lookup"><span data-stu-id="fca37-252">Model</span></span>|  
|-----------|  
|<span data-ttu-id="fca37-253">Mountain-200</span><span class="sxs-lookup"><span data-stu-id="fca37-253">Mountain-200</span></span>|  
|<span data-ttu-id="fca37-254">Mountain Tire Tube</span><span class="sxs-lookup"><span data-stu-id="fca37-254">Mountain Tire Tube</span></span>|  
|<span data-ttu-id="fca37-255">Touring Tire Tube</span><span class="sxs-lookup"><span data-stu-id="fca37-255">Touring Tire Tube</span></span>|  
  
 <span data-ttu-id="fca37-256">结果告诉您要向已购买 Patch Kit 产品的客户推荐的三款最佳产品。</span><span class="sxs-lookup"><span data-stu-id="fca37-256">The results tell you the three best products to recommend to customers who have purchased the Patch Kit product.</span></span> <span data-ttu-id="fca37-257">也可以在您进行推荐时提供多款产品作为输入，方法是键入值，或使用 **“单独查询输入”** 对话框，然后添加或删除值。</span><span class="sxs-lookup"><span data-stu-id="fca37-257">You can also provide multiple products as input when you make recommendations, either by typing in values, or by using the **Singleton Query Input** dialog box and adding or removing values.</span></span> <span data-ttu-id="fca37-258">以下示例查询演示如何提供用来进行预测的多个值。</span><span class="sxs-lookup"><span data-stu-id="fca37-258">The following sample query shows how the multiple values are provided, upon which to make a prediction.</span></span> <span data-ttu-id="fca37-259">这些值用定义输入值的 SELECT 语句中的 UNION 子句来连接。</span><span class="sxs-lookup"><span data-stu-id="fca37-259">Values are connected by a UNION clause in the SELECT statement that defines the input values.</span></span>  
  
```  
SELECT PredictAssociation([DT_Association].[v Assoc Seq Line Items],3)  
From  
  [DT_Association]  
NATURAL PREDICTION JOIN  
(SELECT (SELECT 'Racing Socks' AS [Model]  
  UNION SELECT 'Women''s Mountain Shorts' AS [Model]) AS [v Assoc Seq Line Items]) AS t  
```  
  
 <span data-ttu-id="fca37-260">预期的结果：</span><span class="sxs-lookup"><span data-stu-id="fca37-260">Expected results:</span></span>  
  
|<span data-ttu-id="fca37-261">模型</span><span class="sxs-lookup"><span data-stu-id="fca37-261">Model</span></span>|  
|-----------|  
|<span data-ttu-id="fca37-262">Long-Sleeve Logo Jersey</span><span class="sxs-lookup"><span data-stu-id="fca37-262">Long-Sleeve Logo Jersey</span></span>|  
|<span data-ttu-id="fca37-263">Mountain-400-W</span><span class="sxs-lookup"><span data-stu-id="fca37-263">Mountain-400-W</span></span>|  
|<span data-ttu-id="fca37-264">Classic Vest</span><span class="sxs-lookup"><span data-stu-id="fca37-264">Classic Vest</span></span>|  
  
###  <a name="sample-query-6-retrieving-a-regression-formula-from-a-decision-trees-model"></a><a name="bkmk_Query6"></a><span data-ttu-id="fca37-265">示例查询6：从决策树模型中检索回归公式</span><span class="sxs-lookup"><span data-stu-id="fca37-265">Sample Query 6: Retrieving a Regression Formula from a Decision Trees Model</span></span>  
 <span data-ttu-id="fca37-266">在创建包含连续属性的回归的决策树模型时，可以使用回归公式进行预测，也可以提取有关回归公式的信息。</span><span class="sxs-lookup"><span data-stu-id="fca37-266">When you create a decision tree model that contains a regression on a continuous attribute, you can use the regression formula to make predictions, or you can extract information about the regression formula.</span></span> <span data-ttu-id="fca37-267">有关回归模型的查询的详细信息，请参阅 [线性回归模型查询示例](linear-regression-model-query-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="fca37-267">For more information about queries on regression models, see [Linear Regression Model Query Examples](linear-regression-model-query-examples.md).</span></span>  
  
 <span data-ttu-id="fca37-268">如果决策树模型由回归节点和根据离散属性或范围进行拆分的节点混合组成，则可以创建仅返回回归节点的查询。</span><span class="sxs-lookup"><span data-stu-id="fca37-268">If a decision trees model contains a mixture of regression nodes and nodes that split on discrete attributes or ranges, you can create a query that returns only the regression node.</span></span> <span data-ttu-id="fca37-269">NODE_DISTRIBUTION 表包含回归公式的详细信息。</span><span class="sxs-lookup"><span data-stu-id="fca37-269">The NODE_DISTRIBUTION table contains the details of the regression formula.</span></span> <span data-ttu-id="fca37-270">在本示例中，对列进行了平展，对 NODE_DISTRIBUTION 表使用了别名，以便于查看。</span><span class="sxs-lookup"><span data-stu-id="fca37-270">In this example, the columns are flattened and the NODE_DISTRIBUTION table is aliased for easier viewing.</span></span> <span data-ttu-id="fca37-271">但在此模型中，找不到将 Income 与其他连续属性相关联的回归量。</span><span class="sxs-lookup"><span data-stu-id="fca37-271">However, in this model, no regressors were found to relate Income with other continuous attributes.</span></span> <span data-ttu-id="fca37-272">在这些情况下， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 将返回属性的平均值和模型中该属性的总体方差。</span><span class="sxs-lookup"><span data-stu-id="fca37-272">In such cases, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] returns the mean value of the attribute and the total variance in the model for that attribute.</span></span>  
  
```  
SELECT FLATTENED NODE_DISTRIBUTION AS t  
FROM DT_Predict. CONTENT  
WHERE NODE_TYPE = 25  
```  
  
 <span data-ttu-id="fca37-273">示例结果：</span><span class="sxs-lookup"><span data-stu-id="fca37-273">Example results:</span></span>  
  
|<span data-ttu-id="fca37-274">T.ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="fca37-274">t.ATTRIBUTE_NAME</span></span>|<span data-ttu-id="fca37-275">t.ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="fca37-275">t.ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="fca37-276">t.SUPPORT</span><span class="sxs-lookup"><span data-stu-id="fca37-276">t.SUPPORT</span></span>|<span data-ttu-id="fca37-277">t.PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="fca37-277">t.PROBABILITY</span></span>|<span data-ttu-id="fca37-278">t.VARIANCE</span><span class="sxs-lookup"><span data-stu-id="fca37-278">t.VARIANCE</span></span>|<span data-ttu-id="fca37-279">t.VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="fca37-279">t.VALUETYPE</span></span>|  
|-----------------------|------------------------|---------------|-------------------|----------------|-----------------|  
|<span data-ttu-id="fca37-280">Yearly Income</span><span class="sxs-lookup"><span data-stu-id="fca37-280">Yearly Income</span></span>|<span data-ttu-id="fca37-281">Missing</span><span class="sxs-lookup"><span data-stu-id="fca37-281">Missing</span></span>|<span data-ttu-id="fca37-282">0</span><span class="sxs-lookup"><span data-stu-id="fca37-282">0</span></span>|<span data-ttu-id="fca37-283">0.000457142857142857</span><span class="sxs-lookup"><span data-stu-id="fca37-283">0.000457142857142857</span></span>|<span data-ttu-id="fca37-284">0</span><span class="sxs-lookup"><span data-stu-id="fca37-284">0</span></span>|<span data-ttu-id="fca37-285">1</span><span class="sxs-lookup"><span data-stu-id="fca37-285">1</span></span>|  
|<span data-ttu-id="fca37-286">Yearly Income</span><span class="sxs-lookup"><span data-stu-id="fca37-286">Yearly Income</span></span>|<span data-ttu-id="fca37-287">57220.8876687257</span><span class="sxs-lookup"><span data-stu-id="fca37-287">57220.8876687257</span></span>|<span data-ttu-id="fca37-288">17484</span><span class="sxs-lookup"><span data-stu-id="fca37-288">17484</span></span>|<span data-ttu-id="fca37-289">0.999542857142857</span><span class="sxs-lookup"><span data-stu-id="fca37-289">0.999542857142857</span></span>|<span data-ttu-id="fca37-290">1041275619.52776</span><span class="sxs-lookup"><span data-stu-id="fca37-290">1041275619.52776</span></span>|<span data-ttu-id="fca37-291">3</span><span class="sxs-lookup"><span data-stu-id="fca37-291">3</span></span>|  
||<span data-ttu-id="fca37-292">57220.8876687257</span><span class="sxs-lookup"><span data-stu-id="fca37-292">57220.8876687257</span></span>|<span data-ttu-id="fca37-293">0</span><span class="sxs-lookup"><span data-stu-id="fca37-293">0</span></span>|<span data-ttu-id="fca37-294">0</span><span class="sxs-lookup"><span data-stu-id="fca37-294">0</span></span>|<span data-ttu-id="fca37-295">1041216662.54387</span><span class="sxs-lookup"><span data-stu-id="fca37-295">1041216662.54387</span></span>|<span data-ttu-id="fca37-296">11</span><span class="sxs-lookup"><span data-stu-id="fca37-296">11</span></span>|  
  
 <span data-ttu-id="fca37-297">有关回归模型中使用的值类型和统计信息的详细信息，请参阅[线性回归模型的挖掘模型内容（Analysis Services - 数据挖掘）](mining-model-content-for-linear-regression-models-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="fca37-297">For more information about the value types and the statistics used in regression models, see [Mining Model Content for Linear Regression Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-linear-regression-models-analysis-services-data-mining.md).</span></span>  
  
## <a name="list-of-prediction-functions"></a><span data-ttu-id="fca37-298">预测函数的列表</span><span class="sxs-lookup"><span data-stu-id="fca37-298">List of Prediction Functions</span></span>  
 <span data-ttu-id="fca37-299">所有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 算法均支持一组通用的函数。</span><span class="sxs-lookup"><span data-stu-id="fca37-299">All [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms support a common set of functions.</span></span> <span data-ttu-id="fca37-300">但 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 决策树算法还支持下表中列出的其他函数。</span><span class="sxs-lookup"><span data-stu-id="fca37-300">However, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm supports the additional functions listed in the following table.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fca37-301">预测函数</span><span class="sxs-lookup"><span data-stu-id="fca37-301">Prediction Function</span></span>|<span data-ttu-id="fca37-302">使用情况</span><span class="sxs-lookup"><span data-stu-id="fca37-302">Usage</span></span>|  
|[<span data-ttu-id="fca37-303">IsDescendant (DMX)</span><span class="sxs-lookup"><span data-stu-id="fca37-303">IsDescendant &#40;DMX&#41;</span></span>](/sql/dmx/isdescendant-dmx)|<span data-ttu-id="fca37-304">确定一个节点是否是模型中另一个节点的子节点。</span><span class="sxs-lookup"><span data-stu-id="fca37-304">Determines whether one node is a child of another node in the model.</span></span>|  
|[<span data-ttu-id="fca37-305">IsInNode (DMX)</span><span class="sxs-lookup"><span data-stu-id="fca37-305">IsInNode &#40;DMX&#41;</span></span>](/sql/dmx/isinnode-dmx)|<span data-ttu-id="fca37-306">指示指定的节点是否包含当前事例。</span><span class="sxs-lookup"><span data-stu-id="fca37-306">Indicates whether the specified node contains the current case.</span></span>|  
|[<span data-ttu-id="fca37-307">PredictAdjustedProbability (DMX)</span><span class="sxs-lookup"><span data-stu-id="fca37-307">PredictAdjustedProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictadjustedprobability-dmx)|<span data-ttu-id="fca37-308">返回加权的概率。</span><span class="sxs-lookup"><span data-stu-id="fca37-308">Returns the weighted probability.</span></span>|  
|[<span data-ttu-id="fca37-309">PredictAssociation (DMX)</span><span class="sxs-lookup"><span data-stu-id="fca37-309">PredictAssociation &#40;DMX&#41;</span></span>](/sql/dmx/predictassociation-dmx)|<span data-ttu-id="fca37-310">预测关联数据集中的成员身份。</span><span class="sxs-lookup"><span data-stu-id="fca37-310">Predicts membership in an associative dataset.</span></span>|  
|[<span data-ttu-id="fca37-311">PredictHistogram (DMX)</span><span class="sxs-lookup"><span data-stu-id="fca37-311">PredictHistogram &#40;DMX&#41;</span></span>](/sql/dmx/predicthistogram-dmx)|<span data-ttu-id="fca37-312">返回与当前预测值相关的值的表。</span><span class="sxs-lookup"><span data-stu-id="fca37-312">Returns a table of values related to the current predicted value.</span></span>|  
|[<span data-ttu-id="fca37-313">PredictNodeId (DMX)</span><span class="sxs-lookup"><span data-stu-id="fca37-313">PredictNodeId &#40;DMX&#41;</span></span>](/sql/dmx/predictnodeid-dmx)|<span data-ttu-id="fca37-314">返回每个事例的 Node_ID。</span><span class="sxs-lookup"><span data-stu-id="fca37-314">Returns the Node_ID for each case.</span></span>|  
|[<span data-ttu-id="fca37-315">PredictProbability (DMX)</span><span class="sxs-lookup"><span data-stu-id="fca37-315">PredictProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictprobability-dmx)|<span data-ttu-id="fca37-316">返回预测值的概率。</span><span class="sxs-lookup"><span data-stu-id="fca37-316">Returns probability for the predicted value.</span></span>|  
|[<span data-ttu-id="fca37-317">PredictStdev (DMX)</span><span class="sxs-lookup"><span data-stu-id="fca37-317">PredictStdev &#40;DMX&#41;</span></span>](/sql/dmx/predictstdev-dmx)|<span data-ttu-id="fca37-318">返回指定列的预测标准偏差。</span><span class="sxs-lookup"><span data-stu-id="fca37-318">Returns the predicted standard deviation for the specified column.</span></span>|  
|[<span data-ttu-id="fca37-319">PredictSupport (DMX)</span><span class="sxs-lookup"><span data-stu-id="fca37-319">PredictSupport &#40;DMX&#41;</span></span>](/sql/dmx/predictsupport-dmx)|<span data-ttu-id="fca37-320">返回指定状态的支持值。</span><span class="sxs-lookup"><span data-stu-id="fca37-320">Returns the support value for a specified state.</span></span>|  
|[<span data-ttu-id="fca37-321">PredictVariance (DMX)</span><span class="sxs-lookup"><span data-stu-id="fca37-321">PredictVariance &#40;DMX&#41;</span></span>](/sql/dmx/predictvariance-dmx)|<span data-ttu-id="fca37-322">返回指定列的方差。</span><span class="sxs-lookup"><span data-stu-id="fca37-322">Returns the variance of a specified column.</span></span>|  
  
 <span data-ttu-id="fca37-323">有关所有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 算法都支持的通用函数的列表，请参阅[通用预测函数 (DMX)](/sql/dmx/general-prediction-functions-dmx)。</span><span class="sxs-lookup"><span data-stu-id="fca37-323">For a list of the functions that are common to all [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms, see [General Prediction Functions &#40;DMX&#41;](/sql/dmx/general-prediction-functions-dmx).</span></span> <span data-ttu-id="fca37-324">有关特定函数的语法，请参阅[数据挖掘扩展插件 (DMX) 函数引用](/sql/dmx/data-mining-extensions-dmx-function-reference)。</span><span class="sxs-lookup"><span data-stu-id="fca37-324">For the syntax of specific functions, see [Data Mining Extensions &#40;DMX&#41; Function Reference](/sql/dmx/data-mining-extensions-dmx-function-reference).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fca37-325">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fca37-325">See Also</span></span>  
 <span data-ttu-id="fca37-326">[数据挖掘查询](data-mining-queries.md) </span><span class="sxs-lookup"><span data-stu-id="fca37-326">[Data Mining Queries](data-mining-queries.md) </span></span>  
 <span data-ttu-id="fca37-327">[Microsoft 决策树算法](microsoft-decision-trees-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="fca37-327">[Microsoft Decision Trees Algorithm](microsoft-decision-trees-algorithm.md) </span></span>  
 <span data-ttu-id="fca37-328">[Microsoft 决策树算法技术参考](microsoft-decision-trees-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="fca37-328">[Microsoft Decision Trees Algorithm Technical Reference](microsoft-decision-trees-algorithm-technical-reference.md) </span></span>  
 [<span data-ttu-id="fca37-329">决策树模型的挖掘模型内容（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="fca37-329">Mining Model Content for Decision Tree Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-decision-tree-models-analysis-services-data-mining.md)  
  
  
