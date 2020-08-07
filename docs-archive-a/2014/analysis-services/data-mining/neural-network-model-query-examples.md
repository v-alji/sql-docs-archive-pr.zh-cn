---
title: 神经网络模型查询示例 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- neural network algorithms [Analysis Services]
- content queries [DMX]
- neural network model [Analysis Services]
ms.assetid: 81b06183-620f-4e0c-bc10-532e6a1f0829
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7154ce0ad66346634225734fe829c36e7bf3ad58
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690891"
---
# <a name="neural-network-model-query-examples"></a><span data-ttu-id="56d94-102">神经网络模型查询示例</span><span class="sxs-lookup"><span data-stu-id="56d94-102">Neural Network Model Query Examples</span></span>
  <span data-ttu-id="56d94-103">在对数据挖掘模型创建查询时，可以创建内容查询，也可以创建预测查询。内容查询提供有关分析时发现的模式的详细信息，预测查询使用模型中的模式来对新数据进行预测。</span><span class="sxs-lookup"><span data-stu-id="56d94-103">When you create a query against a data mining model, you can create a content query, which provides details about the patterns discovered in analysis, or a prediction query, which uses the patterns in the model to make predictions for new data.</span></span> <span data-ttu-id="56d94-104">例如，神经网络模型的内容查询可能会检索模型元数据，如隐藏层数。</span><span class="sxs-lookup"><span data-stu-id="56d94-104">For example, a content query for a neural network model might retrieve model metadata such as the number of hidden layers.</span></span> <span data-ttu-id="56d94-105">而预测查询会基于输入提供分类建议，还可以选择是否提供每个分类的概率。</span><span class="sxs-lookup"><span data-stu-id="56d94-105">Alternatively, a prediction query might suggest classifications based on an input and optionally provide probabilities for each classification.</span></span>  
  
 <span data-ttu-id="56d94-106">本节说明如何为基于 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 神经网络算法的模型创建查询。</span><span class="sxs-lookup"><span data-stu-id="56d94-106">This section explains how to create queries for models that are based on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm.</span></span>  
  
 <span data-ttu-id="56d94-107">**内容查询**</span><span class="sxs-lookup"><span data-stu-id="56d94-107">**Content queries**</span></span>  
  
 [<span data-ttu-id="56d94-108">使用 DMX 获取模型元数据</span><span class="sxs-lookup"><span data-stu-id="56d94-108">Getting Model Metadata by Using DMX</span></span>](#bkmk_Query1)  
  
 [<span data-ttu-id="56d94-109">从架构行集中检索模型元数据</span><span class="sxs-lookup"><span data-stu-id="56d94-109">Retrieving Model Metadata from the Schema Rowset</span></span>](#bkmk_Query2)  
  
 [<span data-ttu-id="56d94-110">示例查询 3：检索模型的输入属性</span><span class="sxs-lookup"><span data-stu-id="56d94-110">Retrieving the Input Attributes for the Model</span></span>](#bkmk_Query3)  
  
 [<span data-ttu-id="56d94-111">示例查询 4：从隐藏层中检索权重</span><span class="sxs-lookup"><span data-stu-id="56d94-111">Retrieving Weights from the Hidden Layer</span></span>](#bkmk_Query4)  
  
 <span data-ttu-id="56d94-112">**预测查询**</span><span class="sxs-lookup"><span data-stu-id="56d94-112">**Prediction queries**</span></span>  
  
 [<span data-ttu-id="56d94-113">创建单独预测</span><span class="sxs-lookup"><span data-stu-id="56d94-113">Creating a Singleton Prediction</span></span>](#bkmk_Query5)  
  
## <a name="finding-information-about-a-neural-network-model"></a><span data-ttu-id="56d94-114">查找有关 Naive Bayes 模型的信息</span><span class="sxs-lookup"><span data-stu-id="56d94-114">Finding Information about a Neural Network Model</span></span>  
 <span data-ttu-id="56d94-115">所有挖掘模型都公开算法根据标准化架构（即挖掘模型架构行集）学习的内容。</span><span class="sxs-lookup"><span data-stu-id="56d94-115">All mining models expose the content learned by the algorithm according to a standardized schema, the mining model schema rowset.</span></span> <span data-ttu-id="56d94-116">此信息提供有关模型的详细信息并包含基本元数据、分析中发现的结构以及处理时所使用的参数。</span><span class="sxs-lookup"><span data-stu-id="56d94-116">This information provides details about the model and includes the basic metadata, structures discovered in analysis, and parameters that are used when processing.</span></span> <span data-ttu-id="56d94-117">可以使用数据挖掘扩展插件 (DMX) 语句来创建针对该模型内容的查询。</span><span class="sxs-lookup"><span data-stu-id="56d94-117">You can create queries against the model content by using Data Mining Extension (DMX) statements.</span></span>  
  
###  <a name="sample-query-1-getting-model-metadata-by-using-dmx"></a><a name="bkmk_Query1"></a> <span data-ttu-id="56d94-118">示例查询 1：使用 DMX 获取模型元数据</span><span class="sxs-lookup"><span data-stu-id="56d94-118">Sample Query 1: Getting Model Metadata by Using DMX</span></span>  
 <span data-ttu-id="56d94-119">下面的查询返回与使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 神经网络算法生成的模型有关的一些基本元数据。</span><span class="sxs-lookup"><span data-stu-id="56d94-119">The following query returns some basic metadata about a model that was built by using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm.</span></span> <span data-ttu-id="56d94-120">在神经网络模型中，模型的父节点仅包含模型的名称、存储模型的数据库的名称以及子节点的数目。</span><span class="sxs-lookup"><span data-stu-id="56d94-120">In a neural network model, the parent node of the model contains only the name of the model, the name of the database where the model is stored, and the number of child nodes.</span></span> <span data-ttu-id="56d94-121">但是，边际统计信息节点 (NODE_TYPE = 24) 会提供这些基本元数据以及与模型中使用的输入列有关的一些派生统计信息。</span><span class="sxs-lookup"><span data-stu-id="56d94-121">However, the marginal statistics node (NODE_TYPE = 24) provides both this basic metadata and some derived statistics about the input columns used in the model.</span></span>  
  
 <span data-ttu-id="56d94-122">以下示例查询基于您在 [数据挖掘中级教程](../../tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)中创建的、名为 `Call Center Default NN`的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="56d94-122">The following sample query is based on the mining model that you create in the [Intermediate Data Mining Tutorial](../../tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md), named `Call Center Default NN`.</span></span> <span data-ttu-id="56d94-123">该模型使用来自呼叫中心的数据来探查人员配备、呼叫次数、订单与问题数之间可能的相关性。</span><span class="sxs-lookup"><span data-stu-id="56d94-123">The model uses data from a call center to explore possible correlations between staffing and the number of calls, orders, and issues.</span></span> <span data-ttu-id="56d94-124">该 DMX 语句检索神经网络模型的边际统计信息节点的数据。</span><span class="sxs-lookup"><span data-stu-id="56d94-124">The DMX statement retrieves data from the marginal statistics node of the neural network model.</span></span> <span data-ttu-id="56d94-125">该查询包含 FLATTENED 关键字，因为相关的输入属性统计信息存储在嵌套表 NODE_DISTRIBUTION 中。</span><span class="sxs-lookup"><span data-stu-id="56d94-125">The query includes the FLATTENED keyword, because the input attribute statistics of interest are stored in a nested table, NODE_DISTRIBUTION.</span></span> <span data-ttu-id="56d94-126">但是，如果您的查询访问接口支持分层行集，则无需使用 FLATTENED 关键字。</span><span class="sxs-lookup"><span data-stu-id="56d94-126">However, if your query provider supports hierarchical rowsets you do not need to use the FLATTENED keyword.</span></span>  
  
```  
SELECT FLATTENED MODEL_CATALOG, MODEL_NAME,   
(    SELECT ATTRIBUTE_NAME, ATTRIBUTE_VALUE,  
     [SUPPORT], [PROBABILITY], VALUETYPE   
     FROM NODE_DISTRIBUTION  
) AS t  
FROM [Call Center Default NN].CONTENT  
WHERE NODE_TYPE = 24  
```  
  
> [!NOTE]  
>  <span data-ttu-id="56d94-127">必须将嵌套表列的名称括在方括号中，如 `[SUPPORT]` 和 `[PROBABILITY]`，以便将它们与同名的保留关键字区分开来。</span><span class="sxs-lookup"><span data-stu-id="56d94-127">You must enclose the name of the nested table columns `[SUPPORT]` and `[PROBABILITY]` in brackets to distinguish them from the reserved keywords of the same name.</span></span>  
  
 <span data-ttu-id="56d94-128">示例结果：</span><span class="sxs-lookup"><span data-stu-id="56d94-128">Example results:</span></span>  
  
|<span data-ttu-id="56d94-129">MODEL_CATALOG</span><span class="sxs-lookup"><span data-stu-id="56d94-129">MODEL_CATALOG</span></span>|<span data-ttu-id="56d94-130">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="56d94-130">MODEL_NAME</span></span>|<span data-ttu-id="56d94-131">T.ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="56d94-131">t.ATTRIBUTE_NAME</span></span>|<span data-ttu-id="56d94-132">t.ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="56d94-132">t.ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="56d94-133">t.SUPPORT</span><span class="sxs-lookup"><span data-stu-id="56d94-133">t.SUPPORT</span></span>|<span data-ttu-id="56d94-134">t.PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="56d94-134">t.PROBABILITY</span></span>|<span data-ttu-id="56d94-135">t.VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="56d94-135">t.VALUETYPE</span></span>|  
|--------------------|-----------------|-----------------------|------------------------|---------------|-------------------|-----------------|  
|<span data-ttu-id="56d94-136">Adventure Works DW Multidimensional 2012</span><span class="sxs-lookup"><span data-stu-id="56d94-136">Adventure Works DW Multidimensional 2012</span></span>|<span data-ttu-id="56d94-137">Call Center NN</span><span class="sxs-lookup"><span data-stu-id="56d94-137">Call Center NN</span></span>|<span data-ttu-id="56d94-138">Average Time Per Issue</span><span class="sxs-lookup"><span data-stu-id="56d94-138">Average Time Per Issue</span></span>|<span data-ttu-id="56d94-139">Missing</span><span class="sxs-lookup"><span data-stu-id="56d94-139">Missing</span></span>|<span data-ttu-id="56d94-140">0</span><span class="sxs-lookup"><span data-stu-id="56d94-140">0</span></span>|<span data-ttu-id="56d94-141">0</span><span class="sxs-lookup"><span data-stu-id="56d94-141">0</span></span>|<span data-ttu-id="56d94-142">1</span><span class="sxs-lookup"><span data-stu-id="56d94-142">1</span></span>|  
|<span data-ttu-id="56d94-143">Adventure Works DW Multidimensional 2012</span><span class="sxs-lookup"><span data-stu-id="56d94-143">Adventure Works DW Multidimensional 2012</span></span>|<span data-ttu-id="56d94-144">Call Center NN</span><span class="sxs-lookup"><span data-stu-id="56d94-144">Call Center NN</span></span>|<span data-ttu-id="56d94-145">Average Time Per Issue</span><span class="sxs-lookup"><span data-stu-id="56d94-145">Average Time Per Issue</span></span>|<span data-ttu-id="56d94-146">< 64.7094100096</span><span class="sxs-lookup"><span data-stu-id="56d94-146">< 64.7094100096</span></span>|<span data-ttu-id="56d94-147">11</span><span class="sxs-lookup"><span data-stu-id="56d94-147">11</span></span>|<span data-ttu-id="56d94-148">0.407407407</span><span class="sxs-lookup"><span data-stu-id="56d94-148">0.407407407</span></span>|<span data-ttu-id="56d94-149">5</span><span class="sxs-lookup"><span data-stu-id="56d94-149">5</span></span>|  
  
 <span data-ttu-id="56d94-150">有关架构行集中的列在神经网络模型的上下文中的含义的定义，请参阅 [神经网络模型的挖掘模型内容（Analysis Services - 数据挖掘）](mining-model-content-for-neural-network-models-analysis-services-data-mining.md)的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="56d94-150">For a definition of what the columns in the schema rowset mean in the context of a neural network model, see [Mining Model Content for Neural Network Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md).</span></span>  
  
###  <a name="sample-query-2-retrieving-model-metadata-from-the-schema-rowset"></a><a name="bkmk_Query2"></a> <span data-ttu-id="56d94-151">示例查询 2：从架构行集中检索模型元数据</span><span class="sxs-lookup"><span data-stu-id="56d94-151">Sample Query 2: Retrieving Model Metadata from the Schema Rowset</span></span>  
 <span data-ttu-id="56d94-152">通过查询数据挖掘架构行集，可以找到在 DMX 内容查询中返回的相同信息。</span><span class="sxs-lookup"><span data-stu-id="56d94-152">You can find the same information that is returned in a DMX content query by querying the data mining schema rowset.</span></span> <span data-ttu-id="56d94-153">但是，架构行集还提供一些额外的列。</span><span class="sxs-lookup"><span data-stu-id="56d94-153">However, the schema rowset provides some additional columns.</span></span> <span data-ttu-id="56d94-154">下面的示例查询返回模型的创建日期、修改日期以及上次处理模型日期。</span><span class="sxs-lookup"><span data-stu-id="56d94-154">The following sample query returns the date that the model was created, the date it was modified, and the date that the model was last processed.</span></span> <span data-ttu-id="56d94-155">该查询还返回可预测列（这从模型内容中并不能轻易获得）以及用于生成该模型的参数。</span><span class="sxs-lookup"><span data-stu-id="56d94-155">The query also returns the predictable columns, which are not easily available from the model content, and the parameters that were used to build the model.</span></span> <span data-ttu-id="56d94-156">此信息对于模型的归档很有用。</span><span class="sxs-lookup"><span data-stu-id="56d94-156">This information can be useful for documenting the model.</span></span>  
  
```  
SELECT MODEL_NAME, DATE_CREATED, LAST_PROCESSED, PREDICTION_ENTITY, MINING_PARAMETERS   
from $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'Call Center Default NN'  
```  
  
 <span data-ttu-id="56d94-157">示例结果：</span><span class="sxs-lookup"><span data-stu-id="56d94-157">Example results:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="56d94-158">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="56d94-158">MODEL_NAME</span></span>|<span data-ttu-id="56d94-159">Call Center Default NN</span><span class="sxs-lookup"><span data-stu-id="56d94-159">Call Center Default NN</span></span>|  
|<span data-ttu-id="56d94-160">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="56d94-160">DATE_CREATED</span></span>|<span data-ttu-id="56d94-161">1/10/2008 5:07:38 PM</span><span class="sxs-lookup"><span data-stu-id="56d94-161">1/10/2008 5:07:38 PM</span></span>|  
|<span data-ttu-id="56d94-162">LAST_PROCESSED</span><span class="sxs-lookup"><span data-stu-id="56d94-162">LAST_PROCESSED</span></span>|<span data-ttu-id="56d94-163">1/10/2008 5:24:02 PM</span><span class="sxs-lookup"><span data-stu-id="56d94-163">1/10/2008 5:24:02 PM</span></span>|  
|<span data-ttu-id="56d94-164">PREDICTION_ENTITY</span><span class="sxs-lookup"><span data-stu-id="56d94-164">PREDICTION_ENTITY</span></span>|<span data-ttu-id="56d94-165">Average Time Per Issue,</span><span class="sxs-lookup"><span data-stu-id="56d94-165">Average Time Per Issue,</span></span><br /><br /> <span data-ttu-id="56d94-166">Grade Of Service,</span><span class="sxs-lookup"><span data-stu-id="56d94-166">Grade Of Service,</span></span><br /><br /> <span data-ttu-id="56d94-167">Number Of Orders</span><span class="sxs-lookup"><span data-stu-id="56d94-167">Number Of Orders</span></span>|  
|<span data-ttu-id="56d94-168">MINING_PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="56d94-168">MINING_PARAMETERS</span></span>|<span data-ttu-id="56d94-169">HOLDOUT_PERCENTAGE=30, HOLDOUT_SEED=0,</span><span class="sxs-lookup"><span data-stu-id="56d94-169">HOLDOUT_PERCENTAGE=30, HOLDOUT_SEED=0,</span></span><br /><br /> <span data-ttu-id="56d94-170">MAXIMUM_INPUT_ATTRIBUTES=255, MAXIMUM_OUTPUT_ATTRIBUTES=255,</span><span class="sxs-lookup"><span data-stu-id="56d94-170">MAXIMUM_INPUT_ATTRIBUTES=255, MAXIMUM_OUTPUT_ATTRIBUTES=255,</span></span><br /><br /> <span data-ttu-id="56d94-171">MAXIMUM_STATES=100, SAMPLE_SIZE=10000, HIDDEN_NODE_RATIO=4</span><span class="sxs-lookup"><span data-stu-id="56d94-171">MAXIMUM_STATES=100, SAMPLE_SIZE=10000, HIDDEN_NODE_RATIO=4</span></span>|  
  
###  <a name="sample-query-3-retrieving-the-input-attributes-for-the-model"></a><a name="bkmk_Query3"></a> <span data-ttu-id="56d94-172">示例查询 3：检索模型的输入属性</span><span class="sxs-lookup"><span data-stu-id="56d94-172">Sample Query 3: Retrieving the Input Attributes for the Model</span></span>  
 <span data-ttu-id="56d94-173">通过查询输入层 (NODE_TYPE = 18) 的子节点 (NODE_TYPE = 20) 可以检索用于创建模型的输入属性值对。</span><span class="sxs-lookup"><span data-stu-id="56d94-173">You can retrieve the input attribute-value pairs that were used to create the model by querying the child nodes (NODE_TYPE = 20) of the input layer (NODE_TYPE = 18).</span></span> <span data-ttu-id="56d94-174">下面的查询从节点说明返回输入属性列表。</span><span class="sxs-lookup"><span data-stu-id="56d94-174">The following query returns a list of input attributes from the node descriptions.</span></span>  
  
```  
SELECT NODE_DESCRIPTION  
FROM [Call Center Default NN].CONTENT  
WHERE NODE_TYPE = 2  
```  
  
 <span data-ttu-id="56d94-175">示例结果：</span><span class="sxs-lookup"><span data-stu-id="56d94-175">Example results:</span></span>  
  
|<span data-ttu-id="56d94-176">NODE_DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="56d94-176">NODE_DESCRIPTION</span></span>|  
|-----------------------|  
|<span data-ttu-id="56d94-177">Average Time Per Issue=64.7094100096 - 77.4002099712</span><span class="sxs-lookup"><span data-stu-id="56d94-177">Average Time Per Issue=64.7094100096 - 77.4002099712</span></span>|  
|<span data-ttu-id="56d94-178">Day Of Week=Fri.</span><span class="sxs-lookup"><span data-stu-id="56d94-178">Day Of Week=Fri.</span></span>|  
|<span data-ttu-id="56d94-179">Level 1 Operators</span><span class="sxs-lookup"><span data-stu-id="56d94-179">Level 1 Operators</span></span>|  
  
 <span data-ttu-id="56d94-180">此处仅显示结果中一些具有代表性的行。</span><span class="sxs-lookup"><span data-stu-id="56d94-180">Only a few representative rows from the results are shown here.</span></span> <span data-ttu-id="56d94-181">但是，可以看到 NODE_DESCRIPTION 提供了因输入属性的数据类型不同而略有差异的信息。</span><span class="sxs-lookup"><span data-stu-id="56d94-181">However, you can see that the NODE_DESCRIPTION provides slightly different information depending on the data type of the input attribute.</span></span>  
  
-   <span data-ttu-id="56d94-182">如果输入属性为离散值或离散化的值，则会返回该属性及其值或其离散化范围。</span><span class="sxs-lookup"><span data-stu-id="56d94-182">If the attribute is a discrete or discretized value, the attribute and either its value or its discretized range are returned.</span></span>  
  
-   <span data-ttu-id="56d94-183">如果输入属性为连续数值数据类型，则 NODE_DESCRIPTION 仅包含属性名称。</span><span class="sxs-lookup"><span data-stu-id="56d94-183">If the attribute is a continuous numeric data type, the NODE_DESCRIPTION contains only the attribute name.</span></span> <span data-ttu-id="56d94-184">但是，可以检索嵌套的 NODE_DISTRIBUTION 表以获取平均值，或者返回 NODE_RULE 以获取数值范围的最小值和最大值。</span><span class="sxs-lookup"><span data-stu-id="56d94-184">However, you can retrieve the nested NODE_DISTRIBUTION table to obtain the mean, or return the NODE_RULE to obtain the minimum and maximum values of the numeric range.</span></span>  
  
 <span data-ttu-id="56d94-185">下面的查询显示如何查询嵌套的 NODE_DISTRIBUTION 表以在一列中返回属性，并在另一列中返回这些属性的值。</span><span class="sxs-lookup"><span data-stu-id="56d94-185">The following query shows how to query the nested NODE_DISTRIBUTION table to return the attributes in one column, and their values in another column.</span></span> <span data-ttu-id="56d94-186">对于连续属性，属性值由其平均值来代表。</span><span class="sxs-lookup"><span data-stu-id="56d94-186">For continuous attributes, the value of the attribute is represented by its mean.</span></span>  
  
```  
SELECT FLATTENED   
(SELECT ATTRIBUTE_NAME, ATTRIBUTE_VALUE  
FROM NODE_DISTRIBUTION) as t  
FROM [Call Center Default NN -- Predict Service and Orders].CONTENT  
WHERE NODE_TYPE = 21  
```  
  
 <span data-ttu-id="56d94-187">示例结果：</span><span class="sxs-lookup"><span data-stu-id="56d94-187">Example results:</span></span>  
  
|<span data-ttu-id="56d94-188">T.ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="56d94-188">t.ATTRIBUTE_NAME</span></span>|<span data-ttu-id="56d94-189">t.ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="56d94-189">t.ATTRIBUTE_VALUE</span></span>|  
|-----------------------|------------------------|  
|<span data-ttu-id="56d94-190">Average Time Per Issue</span><span class="sxs-lookup"><span data-stu-id="56d94-190">Average Time Per Issue</span></span>|<span data-ttu-id="56d94-191">64.7094100096 - 77.4002099712</span><span class="sxs-lookup"><span data-stu-id="56d94-191">64.7094100096 - 77.4002099712</span></span>|  
|<span data-ttu-id="56d94-192">Day Of Week</span><span class="sxs-lookup"><span data-stu-id="56d94-192">Day Of Week</span></span>|<span data-ttu-id="56d94-193">Fri.</span><span class="sxs-lookup"><span data-stu-id="56d94-193">Fri.</span></span>|  
|<span data-ttu-id="56d94-194">Level 1 Operators</span><span class="sxs-lookup"><span data-stu-id="56d94-194">Level 1 Operators</span></span>|<span data-ttu-id="56d94-195">3.2962962962963</span><span class="sxs-lookup"><span data-stu-id="56d94-195">3.2962962962963</span></span>|  
  
 <span data-ttu-id="56d94-196">最小和最大范围值存储在 NODE_RULE 列中，并表示为 XML 片段，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="56d94-196">The minimum and maximum range values are stored in the NODE_RULE column, and are represented as an XML fragment, as shown in the following example:</span></span>  
  
```  
<NormContinuous field="Level 1 Operators">    
  <LinearNorm orig="2.83967303681711" norm="-1" />    
  <LinearNorm orig="3.75291955577548" norm="1" />    
</NormContinuous>    
```  
  
###  <a name="sample-query-4-retrieving-weights-from-the-hidden-layer"></a><a name="bkmk_Query4"></a> <span data-ttu-id="56d94-197">示例查询 4：从隐藏层中检索权重</span><span class="sxs-lookup"><span data-stu-id="56d94-197">Sample Query 4: Retrieving Weights from the Hidden Layer</span></span>  
 <span data-ttu-id="56d94-198">神经网络模型的模型内容采用特定的结构，以便轻松检索网络中的任何节点的详细信息。</span><span class="sxs-lookup"><span data-stu-id="56d94-198">The model content of a neural network model is structured in a way that makes it easy to retrieve details about any node in the network.</span></span> <span data-ttu-id="56d94-199">此外，节点的 ID 号提供了有助于您标识节点类型之间关系的信息。</span><span class="sxs-lookup"><span data-stu-id="56d94-199">Moreover, the ID numbers of the nodes provide information that helps you identify relationships among the node types.</span></span>  
  
 <span data-ttu-id="56d94-200">下面的查询演示了如何检索隐藏层特定节点下存储的系数。</span><span class="sxs-lookup"><span data-stu-id="56d94-200">The following query demonstrates how to retrieve the coefficients that are stored under a particular node of the hidden layer.</span></span> <span data-ttu-id="56d94-201">该隐藏层包含一个组织程序节点 (NODE_TYPE = 19) 和多个子节点 (NODE_TYPE = 22)，组织程序节点仅包含元数据，子节点包含属性和值的各种组合的系数。</span><span class="sxs-lookup"><span data-stu-id="56d94-201">The hidden layer consists of an organizer node (NODE_TYPE = 19), which contains only metadata, and multiple child nodes (NODE_TYPE = 22), which contain the coefficients for the various combinations of attributes and values.</span></span> <span data-ttu-id="56d94-202">此查询仅返回系数节点。</span><span class="sxs-lookup"><span data-stu-id="56d94-202">This query returns only the coefficient nodes.</span></span>  
  
```  
SELECT FLATTENED TOP 1 NODE_UNIQUE_NAME,   
(SELECT ATTRIBUTE_NAME, ATTRIBUTE_VALUE, VALUETYPE  
FROM NODE_DISTRIBUTION) as t  
FROM  [Call Center Default NN -- Predict Service and Orders].CONTENT  
WHERE NODE_TYPE = 22  
AND [PARENT_UNIQUE_NAME] = '40000000200000000' FROM [Call Center Default NN].CONTENT  
```  
  
 <span data-ttu-id="56d94-203">示例结果：</span><span class="sxs-lookup"><span data-stu-id="56d94-203">Example results:</span></span>  
  
|<span data-ttu-id="56d94-204">NODE_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="56d94-204">NODE_UNIQUE_NAME</span></span>|<span data-ttu-id="56d94-205">T.ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="56d94-205">t.ATTRIBUTE_NAME</span></span>|<span data-ttu-id="56d94-206">t.ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="56d94-206">t.ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="56d94-207">t.VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="56d94-207">t.VALUETYPE</span></span>|  
|------------------------|-----------------------|------------------------|-----------------|  
|<span data-ttu-id="56d94-208">70000000200000000</span><span class="sxs-lookup"><span data-stu-id="56d94-208">70000000200000000</span></span>|<span data-ttu-id="56d94-209">6000000000000000a</span><span class="sxs-lookup"><span data-stu-id="56d94-209">6000000000000000a</span></span>|<span data-ttu-id="56d94-210">-0.178616518</span><span class="sxs-lookup"><span data-stu-id="56d94-210">-0.178616518</span></span>|<span data-ttu-id="56d94-211">7</span><span class="sxs-lookup"><span data-stu-id="56d94-211">7</span></span>|  
|<span data-ttu-id="56d94-212">70000000200000000</span><span class="sxs-lookup"><span data-stu-id="56d94-212">70000000200000000</span></span>|<span data-ttu-id="56d94-213">6000000000000000b</span><span class="sxs-lookup"><span data-stu-id="56d94-213">6000000000000000b</span></span>|<span data-ttu-id="56d94-214">-0.267561918</span><span class="sxs-lookup"><span data-stu-id="56d94-214">-0.267561918</span></span>|<span data-ttu-id="56d94-215">7</span><span class="sxs-lookup"><span data-stu-id="56d94-215">7</span></span>|  
|<span data-ttu-id="56d94-216">70000000200000000</span><span class="sxs-lookup"><span data-stu-id="56d94-216">70000000200000000</span></span>|<span data-ttu-id="56d94-217">6000000000000000c</span><span class="sxs-lookup"><span data-stu-id="56d94-217">6000000000000000c</span></span>|<span data-ttu-id="56d94-218">0.11069497</span><span class="sxs-lookup"><span data-stu-id="56d94-218">0.11069497</span></span>|<span data-ttu-id="56d94-219">7</span><span class="sxs-lookup"><span data-stu-id="56d94-219">7</span></span>|  
|<span data-ttu-id="56d94-220">70000000200000000</span><span class="sxs-lookup"><span data-stu-id="56d94-220">70000000200000000</span></span>|<span data-ttu-id="56d94-221">6000000000000000d</span><span class="sxs-lookup"><span data-stu-id="56d94-221">6000000000000000d</span></span>|<span data-ttu-id="56d94-222">0.123757712</span><span class="sxs-lookup"><span data-stu-id="56d94-222">0.123757712</span></span>|<span data-ttu-id="56d94-223">7</span><span class="sxs-lookup"><span data-stu-id="56d94-223">7</span></span>|  
|<span data-ttu-id="56d94-224">70000000200000000</span><span class="sxs-lookup"><span data-stu-id="56d94-224">70000000200000000</span></span>|<span data-ttu-id="56d94-225">6000000000000000e</span><span class="sxs-lookup"><span data-stu-id="56d94-225">6000000000000000e</span></span>|<span data-ttu-id="56d94-226">0.294565343</span><span class="sxs-lookup"><span data-stu-id="56d94-226">0.294565343</span></span>|<span data-ttu-id="56d94-227">7</span><span class="sxs-lookup"><span data-stu-id="56d94-227">7</span></span>|  
|<span data-ttu-id="56d94-228">70000000200000000</span><span class="sxs-lookup"><span data-stu-id="56d94-228">70000000200000000</span></span>|<span data-ttu-id="56d94-229">6000000000000000f</span><span class="sxs-lookup"><span data-stu-id="56d94-229">6000000000000000f</span></span>|<span data-ttu-id="56d94-230">0.22245318</span><span class="sxs-lookup"><span data-stu-id="56d94-230">0.22245318</span></span>|<span data-ttu-id="56d94-231">7</span><span class="sxs-lookup"><span data-stu-id="56d94-231">7</span></span>|  
|<span data-ttu-id="56d94-232">70000000200000000</span><span class="sxs-lookup"><span data-stu-id="56d94-232">70000000200000000</span></span>||<span data-ttu-id="56d94-233">0.188805045</span><span class="sxs-lookup"><span data-stu-id="56d94-233">0.188805045</span></span>|<span data-ttu-id="56d94-234">7</span><span class="sxs-lookup"><span data-stu-id="56d94-234">7</span></span>|  
  
 <span data-ttu-id="56d94-235">此处显示的部分结果说明了神经网络模型内容如何将隐藏节点与输入节点相关联。</span><span class="sxs-lookup"><span data-stu-id="56d94-235">The partial results shown here demonstrate how the neural network model content relates the hidden node to the input nodes.</span></span>  
  
-   <span data-ttu-id="56d94-236">隐藏层中节点的唯一名称始终以 70000000 开头。</span><span class="sxs-lookup"><span data-stu-id="56d94-236">The unique names of nodes in the hidden layer always begin with 70000000.</span></span>  
  
-   <span data-ttu-id="56d94-237">输入层中节点的唯一名称始终以 60000000 开头。</span><span class="sxs-lookup"><span data-stu-id="56d94-237">The unique names of nodes in the input layer always begin with 60000000.</span></span>  
  
 <span data-ttu-id="56d94-238">因此，这些结果显示由 ID 70000000200000000 表示的节点可使六个不同的系数 (VALUETYPE = 7) 传递给它。</span><span class="sxs-lookup"><span data-stu-id="56d94-238">Thus, these results tell you that the node denoted by the ID 70000000200000000 had six different coefficients (VALUETYPE = 7) passed to it.</span></span> <span data-ttu-id="56d94-239">系数的值在 ATTRIBUTE_VALUE 列中。</span><span class="sxs-lookup"><span data-stu-id="56d94-239">The values of the coefficients are in the ATTRIBUTE_VALUE column.</span></span> <span data-ttu-id="56d94-240">您可以使用 ATTRIBUTE_NAME 列中的节点 ID 来明确地确定系数对应哪一个输入属性。</span><span class="sxs-lookup"><span data-stu-id="56d94-240">You can determine exactly which input attribute the coefficient is for by using the node ID in the ATTRIBUTE_NAME column.</span></span> <span data-ttu-id="56d94-241">例如，节点 ID 6000000000000000a 对应输入属性和值 `Day of Week = 'Tue.'` 。您可以使用节点 ID 来创建一个查询，或者可以使用 [Microsoft 一般内容树查看器](../microsoft-generic-content-tree-viewer-data-mining.md)浏览到该节点。</span><span class="sxs-lookup"><span data-stu-id="56d94-241">For example, the node ID 6000000000000000a refers to input attribute and value, `Day of Week = 'Tue.'` You can use the node ID to create a query, or you can browse to the node by using the [Microsoft Generic Content Tree Viewer](../microsoft-generic-content-tree-viewer-data-mining.md).</span></span>  
  
 <span data-ttu-id="56d94-242">同样，如果您查询输出层 (NODE_TYPE = 23) 中各节点的 NODE_DISTRIBUTION 表，则会看到每个输出值的系数。</span><span class="sxs-lookup"><span data-stu-id="56d94-242">Similarly, if you query the NODE_DISTRIBUTION table of the nodes in the output layer (NODE_TYPE = 23), you can see the coefficients for each output value.</span></span> <span data-ttu-id="56d94-243">但是，在输出层中，指针将回指隐藏层的节点。</span><span class="sxs-lookup"><span data-stu-id="56d94-243">However, in the output layer, the pointers refer back to the nodes of the hidden layer.</span></span> <span data-ttu-id="56d94-244">有关详细信息，请参阅 [神经网络模型的挖掘模型内容（Analysis Services - 数据挖掘）](mining-model-content-for-neural-network-models-analysis-services-data-mining.md)的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="56d94-244">For more information, see [Mining Model Content for Neural Network Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md).</span></span>  
  
## <a name="using-a-neural-network-model-to-make-predictions"></a><span data-ttu-id="56d94-245">使用神经网络模型进行预测</span><span class="sxs-lookup"><span data-stu-id="56d94-245">Using a Neural Network Model to Make Predictions</span></span>  
 <span data-ttu-id="56d94-246">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 神经网络算法支持分类和回归。</span><span class="sxs-lookup"><span data-stu-id="56d94-246">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm supports both classification and regression.</span></span> <span data-ttu-id="56d94-247">您可以对这些模型使用预测函数来提供新数据并创建单独预测或批预测。</span><span class="sxs-lookup"><span data-stu-id="56d94-247">You can use prediction functions with these models to provide new data and create either singleton or batch predictions.</span></span>  
  
###  <a name="sample-query-5-creating-a-singleton-prediction"></a><a name="bkmk_Query5"></a> <span data-ttu-id="56d94-248">示例查询 5：创建单独预测</span><span class="sxs-lookup"><span data-stu-id="56d94-248">Sample Query 5: Creating a Singleton Prediction</span></span>  
 <span data-ttu-id="56d94-249">对神经网络模型生成预测查询的最简单方法是使用预测查询生成器，在 **和** 的数据挖掘设计器的 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] “挖掘预测” [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]选项卡中都提供了该生成器。</span><span class="sxs-lookup"><span data-stu-id="56d94-249">The easiest way to build a prediction query on a neural network model is to use the Prediction Query Builder, available on the **Mining Prediction** tab of Data Mining Designer in both [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="56d94-250">您可以在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 神经网络查看器中浏览模型来筛选感兴趣的属性并查看趋势，然后切换到 **“挖掘预测”** 选项卡来创建一个查询并预测那些趋势的新值。</span><span class="sxs-lookup"><span data-stu-id="56d94-250">You can browse the model in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network Viewer to filter attributes of interest and view trends, and then switch to the **Mining Prediction** tab to create a query and predict new values for those trends.</span></span>  
  
 <span data-ttu-id="56d94-251">例如，您可以浏览呼叫中心模型来查看订单量和其他属性之间的相关性。</span><span class="sxs-lookup"><span data-stu-id="56d94-251">For example, you can browse the call center model to view correlations between the order volumes and other attributes.</span></span> <span data-ttu-id="56d94-252">为此，请在查看器中打开模型，然后为 "**输入**" 选择 **\<All>** 。</span><span class="sxs-lookup"><span data-stu-id="56d94-252">To do this, open the model in the viewer, and for **Input**, select **\<All>**.</span></span>  <span data-ttu-id="56d94-253">接下来，为 **“输出”** 选择 **“订单数”**。</span><span class="sxs-lookup"><span data-stu-id="56d94-253">Next, for **Output**, select **Number of Orders**.</span></span> <span data-ttu-id="56d94-254">对于 **“值 1”**，请选择表示最多订单的范围，对于 **“值 2”**，请选择表示最少订单的范围。</span><span class="sxs-lookup"><span data-stu-id="56d94-254">For **Value 1**, select the range that represents the most orders, and for **Value 2**, select the range that represents the fewest orders.</span></span> <span data-ttu-id="56d94-255">然后您将对模型将其与订单量关联的所有属性一目了然。</span><span class="sxs-lookup"><span data-stu-id="56d94-255">You can then see at a glance all the attributes that the model correlates with order volume.</span></span>  
  
 <span data-ttu-id="56d94-256">通过浏览查看器中的结果，您将发现一周中的某些天订单量较少，而操作员数的增加似乎与较高的销售额相关联。</span><span class="sxs-lookup"><span data-stu-id="56d94-256">By browsing the results in the viewer, you find that certain days of the week have low order volumes, and that an increase in the number of operators seems to be correlated with higher sales.</span></span> <span data-ttu-id="56d94-257">然后您可以使用针对模型的预测查询来测试假设情况，询问在订单量少的日子增加级别 2 操作员的人数是否能增加订单量。</span><span class="sxs-lookup"><span data-stu-id="56d94-257">You could then use a prediction query on the model to test a "what if" hypothesis and ask if increasing the number of level 2 operators on a low-volume day would increase orders.</span></span> <span data-ttu-id="56d94-258">为此，请创建如下所示的查询：</span><span class="sxs-lookup"><span data-stu-id="56d94-258">To do this, create a query such as the following:</span></span>  
  
```  
SELECT Predict([Call Center Default NN].[Number of Orders]) AS [Predicted Orders],  
PredictProbability([Call Center Default NN].[Number of Orders]) AS [Probability]  
FROM [Call Center Default NN]  
NATURAL PREDICTION JOIN   
(SELECT 'Tue.' AS [Day of Week],  
13 AS [Level 2 Operators]) AS t  
```  
  
 <span data-ttu-id="56d94-259">示例结果：</span><span class="sxs-lookup"><span data-stu-id="56d94-259">Example results:</span></span>  
  
|<span data-ttu-id="56d94-260">Predicted Orders</span><span class="sxs-lookup"><span data-stu-id="56d94-260">Predicted Orders</span></span>|<span data-ttu-id="56d94-261">概率</span><span class="sxs-lookup"><span data-stu-id="56d94-261">Probability</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="56d94-262">364</span><span class="sxs-lookup"><span data-stu-id="56d94-262">364</span></span>|<span data-ttu-id="56d94-263">0.9532 .。。</span><span class="sxs-lookup"><span data-stu-id="56d94-263">0.9532...</span></span>|  
  
 <span data-ttu-id="56d94-264">预测的周二销售量高于当前销售范围，并且该预测的概率非常高。</span><span class="sxs-lookup"><span data-stu-id="56d94-264">The predicted sales volume is higher than the current range of sales for Tuesday, and the probability of the prediction is very high.</span></span> <span data-ttu-id="56d94-265">但是，您可能要使用批处理创建多个预测来测试对模型的各种假设。</span><span class="sxs-lookup"><span data-stu-id="56d94-265">However, you might want to create multiple predictions by using a batch process to test a variety of hypotheses on the model.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="56d94-266">Excel 2007 数据挖掘外接程序提供的逻辑回归向导很容易回答一些复杂问题，如针对一个特定班次，要将服务等级提高到目标级别，需要多少名二级操作员。</span><span class="sxs-lookup"><span data-stu-id="56d94-266">The Data Mining Add-Ins for Excel 2007 provide logistic regression wizards that make it easy to answer complex questions, such as how many Level Two Operators would be needed to improve service grade to a target level for a specific shift.</span></span> <span data-ttu-id="56d94-267">数据挖掘外接程序是免费下载的，并包含基于神经网络和/或逻辑回归算法的向导。</span><span class="sxs-lookup"><span data-stu-id="56d94-267">The data mining add-ins are a free download, and include wizards that are based on the neural network and/or logistic regression algorithms.</span></span> <span data-ttu-id="56d94-268">有关详细信息，请参阅 [Data Mining Add-ins for Office 2007](https://go.microsoft.com/fwlink/?LinkID=117790) （Office 2007 数据挖掘外接程序）网站。</span><span class="sxs-lookup"><span data-stu-id="56d94-268">For more information, see the [Data Mining Add-ins for Office 2007](https://go.microsoft.com/fwlink/?LinkID=117790) Web site.</span></span>  
  
## <a name="list-of-prediction-functions"></a><span data-ttu-id="56d94-269">预测函数的列表</span><span class="sxs-lookup"><span data-stu-id="56d94-269">List of Prediction Functions</span></span>  
 <span data-ttu-id="56d94-270">所有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 算法均支持一组通用的函数。</span><span class="sxs-lookup"><span data-stu-id="56d94-270">All [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms support a common set of functions.</span></span> <span data-ttu-id="56d94-271">没有特定于 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 神经网络算法的预测函数；但该算法支持下表中列出的函数。</span><span class="sxs-lookup"><span data-stu-id="56d94-271">There are no prediction functions that are specific to the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm; however, the algorithm supports the functions that are listed in the following table.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="56d94-272">预测函数</span><span class="sxs-lookup"><span data-stu-id="56d94-272">Prediction Function</span></span>|<span data-ttu-id="56d94-273">使用情况</span><span class="sxs-lookup"><span data-stu-id="56d94-273">Usage</span></span>|  
|[<span data-ttu-id="56d94-274">IsDescendant (DMX)</span><span class="sxs-lookup"><span data-stu-id="56d94-274">IsDescendant &#40;DMX&#41;</span></span>](/sql/dmx/isdescendant-dmx)|<span data-ttu-id="56d94-275">确定一个节点是否是神经网络图中另一个节点的子节点。</span><span class="sxs-lookup"><span data-stu-id="56d94-275">Determines whether one node is a child of another node in the neural network graph.</span></span>|  
|[<span data-ttu-id="56d94-276">PredictAdjustedProbability (DMX)</span><span class="sxs-lookup"><span data-stu-id="56d94-276">PredictAdjustedProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictadjustedprobability-dmx)|<span data-ttu-id="56d94-277">返回加权的概率。</span><span class="sxs-lookup"><span data-stu-id="56d94-277">Returns the weighted probability.</span></span>|  
|[<span data-ttu-id="56d94-278">PredictHistogram (DMX)</span><span class="sxs-lookup"><span data-stu-id="56d94-278">PredictHistogram &#40;DMX&#41;</span></span>](/sql/dmx/predicthistogram-dmx)|<span data-ttu-id="56d94-279">返回与当前预测值相关的值的表。</span><span class="sxs-lookup"><span data-stu-id="56d94-279">Returns a table of values related to the current predicted value.</span></span>|  
|[<span data-ttu-id="56d94-280">PredictVariance (DMX)</span><span class="sxs-lookup"><span data-stu-id="56d94-280">PredictVariance &#40;DMX&#41;</span></span>](/sql/dmx/predictvariance-dmx)|<span data-ttu-id="56d94-281">返回预测值的方差。</span><span class="sxs-lookup"><span data-stu-id="56d94-281">Returns variance for the predicted value.</span></span>|  
|[<span data-ttu-id="56d94-282">PredictProbability (DMX)</span><span class="sxs-lookup"><span data-stu-id="56d94-282">PredictProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictprobability-dmx)|<span data-ttu-id="56d94-283">返回预测值的概率。</span><span class="sxs-lookup"><span data-stu-id="56d94-283">Returns probability  for the predicted value.</span></span>|  
|[<span data-ttu-id="56d94-284">PredictStdev (DMX)</span><span class="sxs-lookup"><span data-stu-id="56d94-284">PredictStdev &#40;DMX&#41;</span></span>](/sql/dmx/predictstdev-dmx)|<span data-ttu-id="56d94-285">返回预测值的标准偏差。</span><span class="sxs-lookup"><span data-stu-id="56d94-285">Returns the standard deviance for the predicted value.</span></span>|  
|[<span data-ttu-id="56d94-286">PredictSupport (DMX)</span><span class="sxs-lookup"><span data-stu-id="56d94-286">PredictSupport &#40;DMX&#41;</span></span>](/sql/dmx/predictsupport-dmx)|<span data-ttu-id="56d94-287">对于神经网络模型和逻辑回归模型，该函数将返回表示整个模型的定型集大小的单个值。</span><span class="sxs-lookup"><span data-stu-id="56d94-287">For neural network and logistic regression models, returns a single value that represents the size of the training set for the entire model.</span></span>|  
  
 <span data-ttu-id="56d94-288">有关特定函数的语法，请参阅[数据挖掘扩展插件 (DMX) 函数引用](/sql/dmx/data-mining-extensions-dmx-function-reference)。</span><span class="sxs-lookup"><span data-stu-id="56d94-288">For the syntax of specific functions, see [Data Mining Extensions &#40;DMX&#41; Function Reference](/sql/dmx/data-mining-extensions-dmx-function-reference).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56d94-289">另请参阅</span><span class="sxs-lookup"><span data-stu-id="56d94-289">See Also</span></span>  
 <span data-ttu-id="56d94-290">[Microsoft 神经网络算法](microsoft-neural-network-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="56d94-290">[Microsoft Neural Network Algorithm](microsoft-neural-network-algorithm.md) </span></span>  
 <span data-ttu-id="56d94-291">[Microsoft 神经网络算法技术参考](microsoft-neural-network-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="56d94-291">[Microsoft Neural Network Algorithm Technical Reference](microsoft-neural-network-algorithm-technical-reference.md) </span></span>  
 <span data-ttu-id="56d94-292">[&#40;Analysis Services 数据挖掘的神经网络模型的挖掘模型内容&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="56d94-292">[Mining Model Content for Neural Network Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="56d94-293">第 5 课：生成神经网络模型和逻辑回归模型（数据挖掘中级教程）</span><span class="sxs-lookup"><span data-stu-id="56d94-293">Lesson 5: Building Neural Network and Logistic Regression Models &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
  
  
