---
title: Naive Bayes 模型查询示例 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- naive bayes model [Analysis Services]
- naive bayes algorithms [Analysis Services]
- content queries [DMX]
ms.assetid: e642bd7d-5afa-4dfb-8cca-4f84aadf61b0
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9694826bf2f74daef7b6d024e51e31d4ee448671
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687360"
---
# <a name="naive-bayes-model-query-examples"></a><span data-ttu-id="bbbb7-102">Naive Bayes 模型查询示例</span><span class="sxs-lookup"><span data-stu-id="bbbb7-102">Naive Bayes Model Query Examples</span></span>
  <span data-ttu-id="bbbb7-103">在创建针对数据挖掘模型的查询时，您既可以创建内容查询，也可创建预测查询；内容查询提供有关分析过程中发现的模式的详细信息，而预测查询则使用模型中的模式来对新数据进行预测。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-103">When you create a query against a data mining model, you can create either a content query, which provides details about the patterns discovered in analysis, or you can create a prediction query, which uses the patterns in the model to make predictions for new data.</span></span> <span data-ttu-id="bbbb7-104">您还可以通过使用针对数据挖掘架构行集的查询来检索元数据。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-104">You can also retrieve metadata about the model by using a query against the data mining schema rowset.</span></span> <span data-ttu-id="bbbb7-105">本节说明如何创建针对基于 Microsoft Naive Bayes 算法的模型的查询。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-105">This section explains how to create these queries for models that are based on the Microsoft Naive Bayes algorithm.</span></span>  
  
 <span data-ttu-id="bbbb7-106">**内容查询**</span><span class="sxs-lookup"><span data-stu-id="bbbb7-106">**Content Queries**</span></span>  
  
 [<span data-ttu-id="bbbb7-107">使用 DMX 获取模型元数据</span><span class="sxs-lookup"><span data-stu-id="bbbb7-107">Getting model metadata by using DMX</span></span>](#bkmk_Query1)  
  
 [<span data-ttu-id="bbbb7-108">检索定型数据的摘要</span><span class="sxs-lookup"><span data-stu-id="bbbb7-108">Retrieving a summary of training data</span></span>](#bkmk_Query2)  
  
 [<span data-ttu-id="bbbb7-109">查找有关属性的详细信息</span><span class="sxs-lookup"><span data-stu-id="bbbb7-109">Finding more information about attributes</span></span>](#bkmk_Query3)  
  
 [<span data-ttu-id="bbbb7-110">使用系统存储过程</span><span class="sxs-lookup"><span data-stu-id="bbbb7-110">Using system stored procedures</span></span>](#bkmk_Query4)  
  
 <span data-ttu-id="bbbb7-111">**预测查询**</span><span class="sxs-lookup"><span data-stu-id="bbbb7-111">**Prediction Queries**</span></span>  
  
 [<span data-ttu-id="bbbb7-112">使用单独查询预测结果</span><span class="sxs-lookup"><span data-stu-id="bbbb7-112">Predicting outcomes using a singleton query</span></span>](#bkmk_Query5)  
  
 [<span data-ttu-id="bbbb7-113">获取具有概率和支持值的预测</span><span class="sxs-lookup"><span data-stu-id="bbbb7-113">Getting predictions with probability and support values</span></span>](#bkmk_Query6)  
  
 [<span data-ttu-id="bbbb7-114">预测关联</span><span class="sxs-lookup"><span data-stu-id="bbbb7-114">Predicting associations</span></span>](#bkmk_Query7)  
  
## <a name="finding-information-about-a-naive-bayes-model"></a><span data-ttu-id="bbbb7-115">查找有关 Naive Bayes 模型的信息</span><span class="sxs-lookup"><span data-stu-id="bbbb7-115">Finding Information about a Naive Bayes Model</span></span>  
 <span data-ttu-id="bbbb7-116">Naive Bayes 模型的模型内容可提供有关定型数据中值分布的聚合信息。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-116">The model content of a Naive Bayes model provides aggregated information about the distribution of values in the training data.</span></span> <span data-ttu-id="bbbb7-117">您还可以通过创建针对数据挖掘架构行集的查询来检索有关模型的元数据的信息。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-117">You can also retrieve information about the metadata of the model by creating queries against the data mining schema rowsets.</span></span>  
  
###  <a name="sample-query-1-getting-model-metadata-by-using-dmx"></a><a name="bkmk_Query1"></a> <span data-ttu-id="bbbb7-118">示例查询 1：使用 DMX 获取模型元数据</span><span class="sxs-lookup"><span data-stu-id="bbbb7-118">Sample Query 1: Getting Model Metadata by Using DMX</span></span>  
 <span data-ttu-id="bbbb7-119">通过查询数据挖掘架构行集，您可找到模型的元数据。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-119">By querying the data mining schema rowset, you can find metadata for the model.</span></span> <span data-ttu-id="bbbb7-120">这包括模型创建时间、上次处理模型时间、模型所基于的挖掘结构的名称以及用作可预测属性的列的名称。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-120">This might include when the model was created, when the model was last processed, the name of the mining structure that the model is based on, and the name of the columns used as the predictable attribute.</span></span> <span data-ttu-id="bbbb7-121">您还可以返回创建模型时所使用的参数。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-121">You can also return the parameters that were used when the model was created.</span></span>  
  
```  
SELECT MODEL_CATALOG, MODEL_NAME, DATE_CREATED, LAST_PROCESSED,  
SERVICE_NAME, PREDICTION_ENTITY, FILTER  
FROM $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'TM_NaiveBayes_Filtered'  
```  
  
 <span data-ttu-id="bbbb7-122">示例结果：</span><span class="sxs-lookup"><span data-stu-id="bbbb7-122">Sample results:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bbbb7-123">MODEL_CATALOG</span><span class="sxs-lookup"><span data-stu-id="bbbb7-123">MODEL_CATALOG</span></span>|<span data-ttu-id="bbbb7-124">AdventureWorks</span><span class="sxs-lookup"><span data-stu-id="bbbb7-124">AdventureWorks</span></span>|  
|<span data-ttu-id="bbbb7-125">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="bbbb7-125">MODEL_NAME</span></span>|<span data-ttu-id="bbbb7-126">TM_NaiveBayes_Filtered</span><span class="sxs-lookup"><span data-stu-id="bbbb7-126">TM_NaiveBayes_Filtered</span></span>|  
|<span data-ttu-id="bbbb7-127">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="bbbb7-127">DATE_CREATED</span></span>|<span data-ttu-id="bbbb7-128">3/1/2008 19:15</span><span class="sxs-lookup"><span data-stu-id="bbbb7-128">3/1/2008 19:15</span></span>|  
|<span data-ttu-id="bbbb7-129">LAST_PROCESSED</span><span class="sxs-lookup"><span data-stu-id="bbbb7-129">LAST_PROCESSED</span></span>|<span data-ttu-id="bbbb7-130">3/2/2008 20:00</span><span class="sxs-lookup"><span data-stu-id="bbbb7-130">3/2/2008 20:00</span></span>|  
|<span data-ttu-id="bbbb7-131">SERVICE_NAME</span><span class="sxs-lookup"><span data-stu-id="bbbb7-131">SERVICE_NAME</span></span>|<span data-ttu-id="bbbb7-132">Microsoft_Naive_Bayes</span><span class="sxs-lookup"><span data-stu-id="bbbb7-132">Microsoft_Naive_Bayes</span></span>|  
|<span data-ttu-id="bbbb7-133">PREDICTION_ENTITY</span><span class="sxs-lookup"><span data-stu-id="bbbb7-133">PREDICTION_ENTITY</span></span>|<span data-ttu-id="bbbb7-134">Bike Buyer,Yearly Income</span><span class="sxs-lookup"><span data-stu-id="bbbb7-134">Bike Buyer,Yearly Income</span></span>|  
|<span data-ttu-id="bbbb7-135">FILTER</span><span class="sxs-lookup"><span data-stu-id="bbbb7-135">FILTER</span></span>|<span data-ttu-id="bbbb7-136">[Region] = 'Europe' OR [Region] = 'North America'</span><span class="sxs-lookup"><span data-stu-id="bbbb7-136">[Region] = 'Europe' OR [Region] = 'North America'</span></span>|  
  
 <span data-ttu-id="bbbb7-137">此示例所使用的模型基于您在 [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md)中创建的 Naive Bayes 模型，但进行了修改，添加了第二个可预测属性，并对定型数据应用了筛选器。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-137">The model used for this example is based on the Naive Bayes model you create in the [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md), but was modified by adding a second predictable attribute and applying a filter to the training data.</span></span>  
  
###  <a name="sample-query-2-retrieving-a-summary-of-training-data"></a><a name="bkmk_Query2"></a> <span data-ttu-id="bbbb7-138">示例查询 2：检索定型数据的摘要</span><span class="sxs-lookup"><span data-stu-id="bbbb7-138">Sample Query 2: Retrieving a Summary of Training Data</span></span>  
 <span data-ttu-id="bbbb7-139">在 Naive Bayes 模型中，有关定型数据中值分布的聚合信息存储在边际统计节点中。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-139">In a Naive Bayes model, the marginal statistics node stores aggregated information about the distribution of values in the training data.</span></span> <span data-ttu-id="bbbb7-140">该摘要获取方便，您不必创建针对定型数据的 SQL 查询，就可找到该摘要。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-140">This summary is convenient and saves you from having to create SQL queries against the training data to find the same information.</span></span>  
  
 <span data-ttu-id="bbbb7-141">下面的示例使用 DMX 内容查询，从节点 (NODE_TYPE = 24) 检索数据。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-141">The following example uses a DMX content query to retrieve the data from the node (NODE_TYPE = 24).</span></span> <span data-ttu-id="bbbb7-142">由于统计信息存储在嵌套表中，因此，使用 FLATTENED 关键字是为了使结果更易查看。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-142">Because the statistics are stored in a nested table, the FLATTENED keyword is used to make the results easier to view.</span></span>  
  
```  
SELECT FLATTENED MODEL_NAME,  
(SELECT ATTRIBUTE_NAME, ATTRIBUTE_VALUE, [SUPPORT], [PROBABILITY], VALUETYPE FROM NODE_DISTRIBUTION) AS t  
FROM TM_NaiveBayes.CONTENT  
WHERE NODE_TYPE = 26  
```  
  
> [!NOTE]  
>  <span data-ttu-id="bbbb7-143">您必须将列名 SUPPORT 和 PROBABILITY 括在括号中，以便将它们与同名的多维表达式 (MDX) 保留关键字区分开来。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-143">You must enclose the name of the columns, SUPPORT and PROBABILITY, in brackets to distinguish them from the Multidimensional Expressions (MDX) reserved keywords of the same names.</span></span>  
  
 <span data-ttu-id="bbbb7-144">部分结果：</span><span class="sxs-lookup"><span data-stu-id="bbbb7-144">Partial results:</span></span>  
  
|<span data-ttu-id="bbbb7-145">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="bbbb7-145">MODEL_NAME</span></span>|<span data-ttu-id="bbbb7-146">T.ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="bbbb7-146">t.ATTRIBUTE_NAME</span></span>|<span data-ttu-id="bbbb7-147">t.ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="bbbb7-147">t.ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="bbbb7-148">t.SUPPORT</span><span class="sxs-lookup"><span data-stu-id="bbbb7-148">t.SUPPORT</span></span>|<span data-ttu-id="bbbb7-149">t.PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="bbbb7-149">t.PROBABILITY</span></span>|<span data-ttu-id="bbbb7-150">t.VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="bbbb7-150">t.VALUETYPE</span></span>|  
|-----------------|-----------------------|------------------------|---------------|-------------------|-----------------|  
|<span data-ttu-id="bbbb7-151">TM_NaiveBayes</span><span class="sxs-lookup"><span data-stu-id="bbbb7-151">TM_NaiveBayes</span></span>|<span data-ttu-id="bbbb7-152">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="bbbb7-152">Bike Buyer</span></span>|<span data-ttu-id="bbbb7-153">Missing</span><span class="sxs-lookup"><span data-stu-id="bbbb7-153">Missing</span></span>|<span data-ttu-id="bbbb7-154">0</span><span class="sxs-lookup"><span data-stu-id="bbbb7-154">0</span></span>|<span data-ttu-id="bbbb7-155">0</span><span class="sxs-lookup"><span data-stu-id="bbbb7-155">0</span></span>|<span data-ttu-id="bbbb7-156">1</span><span class="sxs-lookup"><span data-stu-id="bbbb7-156">1</span></span>|  
|<span data-ttu-id="bbbb7-157">TM_NaiveBayes</span><span class="sxs-lookup"><span data-stu-id="bbbb7-157">TM_NaiveBayes</span></span>|<span data-ttu-id="bbbb7-158">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="bbbb7-158">Bike Buyer</span></span>|<span data-ttu-id="bbbb7-159">0</span><span class="sxs-lookup"><span data-stu-id="bbbb7-159">0</span></span>|<span data-ttu-id="bbbb7-160">8869</span><span class="sxs-lookup"><span data-stu-id="bbbb7-160">8869</span></span>|<span data-ttu-id="bbbb7-161">0.507263784</span><span class="sxs-lookup"><span data-stu-id="bbbb7-161">0.507263784</span></span>|<span data-ttu-id="bbbb7-162">4</span><span class="sxs-lookup"><span data-stu-id="bbbb7-162">4</span></span>|  
|<span data-ttu-id="bbbb7-163">TM_NaiveBayes</span><span class="sxs-lookup"><span data-stu-id="bbbb7-163">TM_NaiveBayes</span></span>|<span data-ttu-id="bbbb7-164">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="bbbb7-164">Bike Buyer</span></span>|<span data-ttu-id="bbbb7-165">1</span><span class="sxs-lookup"><span data-stu-id="bbbb7-165">1</span></span>|<span data-ttu-id="bbbb7-166">8615</span><span class="sxs-lookup"><span data-stu-id="bbbb7-166">8615</span></span>|<span data-ttu-id="bbbb7-167">0.492736216</span><span class="sxs-lookup"><span data-stu-id="bbbb7-167">0.492736216</span></span>|<span data-ttu-id="bbbb7-168">4</span><span class="sxs-lookup"><span data-stu-id="bbbb7-168">4</span></span>|  
|<span data-ttu-id="bbbb7-169">TM_NaiveBayes</span><span class="sxs-lookup"><span data-stu-id="bbbb7-169">TM_NaiveBayes</span></span>|<span data-ttu-id="bbbb7-170">性别</span><span class="sxs-lookup"><span data-stu-id="bbbb7-170">Gender</span></span>|<span data-ttu-id="bbbb7-171">Missing</span><span class="sxs-lookup"><span data-stu-id="bbbb7-171">Missing</span></span>|<span data-ttu-id="bbbb7-172">0</span><span class="sxs-lookup"><span data-stu-id="bbbb7-172">0</span></span>|<span data-ttu-id="bbbb7-173">0</span><span class="sxs-lookup"><span data-stu-id="bbbb7-173">0</span></span>|<span data-ttu-id="bbbb7-174">1</span><span class="sxs-lookup"><span data-stu-id="bbbb7-174">1</span></span>|  
|<span data-ttu-id="bbbb7-175">TM_NaiveBayes</span><span class="sxs-lookup"><span data-stu-id="bbbb7-175">TM_NaiveBayes</span></span>|<span data-ttu-id="bbbb7-176">性别</span><span class="sxs-lookup"><span data-stu-id="bbbb7-176">Gender</span></span>|<span data-ttu-id="bbbb7-177">F</span><span class="sxs-lookup"><span data-stu-id="bbbb7-177">F</span></span>|<span data-ttu-id="bbbb7-178">8656</span><span class="sxs-lookup"><span data-stu-id="bbbb7-178">8656</span></span>|<span data-ttu-id="bbbb7-179">0.495081217</span><span class="sxs-lookup"><span data-stu-id="bbbb7-179">0.495081217</span></span>|<span data-ttu-id="bbbb7-180">4</span><span class="sxs-lookup"><span data-stu-id="bbbb7-180">4</span></span>|  
|<span data-ttu-id="bbbb7-181">TM_NaiveBayes</span><span class="sxs-lookup"><span data-stu-id="bbbb7-181">TM_NaiveBayes</span></span>|<span data-ttu-id="bbbb7-182">性别</span><span class="sxs-lookup"><span data-stu-id="bbbb7-182">Gender</span></span>|<span data-ttu-id="bbbb7-183">M</span><span class="sxs-lookup"><span data-stu-id="bbbb7-183">M</span></span>|<span data-ttu-id="bbbb7-184">8828</span><span class="sxs-lookup"><span data-stu-id="bbbb7-184">8828</span></span>|<span data-ttu-id="bbbb7-185">0.504918783</span><span class="sxs-lookup"><span data-stu-id="bbbb7-185">0.504918783</span></span>|<span data-ttu-id="bbbb7-186">4</span><span class="sxs-lookup"><span data-stu-id="bbbb7-186">4</span></span>|  
  
 <span data-ttu-id="bbbb7-187">例如，这些结果告诉您每个离散值 (VALUETYPE = 4) 的定型事例的数量以及计算出的概率，其中进行了缺失值 (VALUETYPE = 1) 调整。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-187">For example, these results tell you the number of training cases for each discrete value (VALUETYPE = 4), together with the computed probability, adjusted for missing values (VALUETYPE = 1).</span></span>  
  
 <span data-ttu-id="bbbb7-188">有关 Naive Bayes 模型中的 NODE_DISTRIBUTION 表所提供的值的定义，请参阅 [Naive Bayes 模型的挖掘模型内容（Analysis Services - 数据挖掘）](mining-model-content-for-naive-bayes-models-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-188">For a definition of the values provided in the NODE_DISTRIBUTION table in a Naive Bayes model, see [Mining Model Content for Naive Bayes Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-naive-bayes-models-analysis-services-data-mining.md).</span></span> <span data-ttu-id="bbbb7-189">有关缺失的值如何影响支持和概率计算的详细信息，请参阅[缺失值（Analysis Services - 数据挖掘）](missing-values-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-189">For more information about how support and probability calculations are affected by missing values, see [Missing Values &#40;Analysis Services - Data Mining&#41;](missing-values-analysis-services-data-mining.md).</span></span>  
  
###  <a name="sample-query-3-finding-more-information-about-attributes"></a><a name="bkmk_Query3"></a> <span data-ttu-id="bbbb7-190">示例查询 3：查找有关属性的详细信息</span><span class="sxs-lookup"><span data-stu-id="bbbb7-190">Sample Query 3: Finding More Information about Attributes</span></span>  
 <span data-ttu-id="bbbb7-191">由于 Naive Bayes 模型经常包含有关不同属性之间关系的复杂信息，因此，查看这些关系的最简便的方法是使用 [Microsoft Naive Bayes 查看器](browse-a-model-using-the-microsoft-naive-bayes-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-191">Because a Naive Bayes model often contains complex information about the relationships among different attributes, the easiest way to view these relationships is to use the [Microsoft Naive Bayes Viewer](browse-a-model-using-the-microsoft-naive-bayes-viewer.md).</span></span> <span data-ttu-id="bbbb7-192">但您也可创建 DMX 查询来返回数据。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-192">However, you can create DMX queries to return the data.</span></span>  
  
 <span data-ttu-id="bbbb7-193">下面的示例演示如何从模型返回有关特定属性 `Region`的信息。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-193">The following example shows how to return information from the model about a particular attribute, `Region`.</span></span>  
  
```  
SELECT NODE_TYPE, NODE_CAPTION,   
NODE_PROBABILITY, NODE_SUPPORT, MSOLAP_NODE_SCORE  
FROM TM_NaiveBayes.CONTENT  
WHERE ATTRIBUTE_NAME = 'Region'  
```  
  
 <span data-ttu-id="bbbb7-194">此查询返回两种类型的节点：表示输入属性 (NODE_TYPE = 10) 的节点和属性 (NODE_TYPE = 11) 的每个值的节点。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-194">This query returns two types of nodes: the node that represents the input attribute (NODE_TYPE = 10), and nodes for each value of the attribute (NODE_TYPE = 11).</span></span> <span data-ttu-id="bbbb7-195">使用节点标题（而不是节点名称）来标识节点，是因为标题可同时显示属性名称和属性值。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-195">The node caption is used to identify the node, rather than the node name, because the caption shows both the attribute name and attribute value.</span></span>  
  
|<span data-ttu-id="bbbb7-196">NODE_TYPE</span><span class="sxs-lookup"><span data-stu-id="bbbb7-196">NODE_TYPE</span></span>|<span data-ttu-id="bbbb7-197">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="bbbb7-197">NODE_CAPTION</span></span>|<span data-ttu-id="bbbb7-198">NODE_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="bbbb7-198">NODE_PROBABILITY</span></span>|<span data-ttu-id="bbbb7-199">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="bbbb7-199">NODE_SUPPORT</span></span>|<span data-ttu-id="bbbb7-200">MSOLAP_NODE_SCORE</span><span class="sxs-lookup"><span data-stu-id="bbbb7-200">MSOLAP_NODE_SCORE</span></span>|<span data-ttu-id="bbbb7-201">NODE_TYPE</span><span class="sxs-lookup"><span data-stu-id="bbbb7-201">NODE_TYPE</span></span>|  
|----------------|-------------------|-----------------------|-------------------|-------------------------|----------------|  
|<span data-ttu-id="bbbb7-202">10</span><span class="sxs-lookup"><span data-stu-id="bbbb7-202">10</span></span>|<span data-ttu-id="bbbb7-203">Bike Buyer -> Region</span><span class="sxs-lookup"><span data-stu-id="bbbb7-203">Bike Buyer -> Region</span></span>|<span data-ttu-id="bbbb7-204">1</span><span class="sxs-lookup"><span data-stu-id="bbbb7-204">1</span></span>|<span data-ttu-id="bbbb7-205">17484</span><span class="sxs-lookup"><span data-stu-id="bbbb7-205">17484</span></span>|<span data-ttu-id="bbbb7-206">84.51555875</span><span class="sxs-lookup"><span data-stu-id="bbbb7-206">84.51555875</span></span>|<span data-ttu-id="bbbb7-207">10</span><span class="sxs-lookup"><span data-stu-id="bbbb7-207">10</span></span>|  
|<span data-ttu-id="bbbb7-208">11</span><span class="sxs-lookup"><span data-stu-id="bbbb7-208">11</span></span>|<span data-ttu-id="bbbb7-209">Bike Buyer -> Region = Missing</span><span class="sxs-lookup"><span data-stu-id="bbbb7-209">Bike Buyer -> Region = Missing</span></span>|<span data-ttu-id="bbbb7-210">0</span><span class="sxs-lookup"><span data-stu-id="bbbb7-210">0</span></span>|<span data-ttu-id="bbbb7-211">0</span><span class="sxs-lookup"><span data-stu-id="bbbb7-211">0</span></span>|<span data-ttu-id="bbbb7-212">0</span><span class="sxs-lookup"><span data-stu-id="bbbb7-212">0</span></span>|<span data-ttu-id="bbbb7-213">11</span><span class="sxs-lookup"><span data-stu-id="bbbb7-213">11</span></span>|  
|<span data-ttu-id="bbbb7-214">11</span><span class="sxs-lookup"><span data-stu-id="bbbb7-214">11</span></span>|<span data-ttu-id="bbbb7-215">Bike Buyer -> Region = North America</span><span class="sxs-lookup"><span data-stu-id="bbbb7-215">Bike Buyer -> Region = North America</span></span>|<span data-ttu-id="bbbb7-216">0.508236102</span><span class="sxs-lookup"><span data-stu-id="bbbb7-216">0.508236102</span></span>|<span data-ttu-id="bbbb7-217">8886</span><span class="sxs-lookup"><span data-stu-id="bbbb7-217">8886</span></span>|<span data-ttu-id="bbbb7-218">0</span><span class="sxs-lookup"><span data-stu-id="bbbb7-218">0</span></span>|<span data-ttu-id="bbbb7-219">11</span><span class="sxs-lookup"><span data-stu-id="bbbb7-219">11</span></span>|  
|<span data-ttu-id="bbbb7-220">11</span><span class="sxs-lookup"><span data-stu-id="bbbb7-220">11</span></span>|<span data-ttu-id="bbbb7-221">Bike Buyer -> Region = Pacific</span><span class="sxs-lookup"><span data-stu-id="bbbb7-221">Bike Buyer -> Region = Pacific</span></span>|<span data-ttu-id="bbbb7-222">0.193891558</span><span class="sxs-lookup"><span data-stu-id="bbbb7-222">0.193891558</span></span>|<span data-ttu-id="bbbb7-223">3390</span><span class="sxs-lookup"><span data-stu-id="bbbb7-223">3390</span></span>|<span data-ttu-id="bbbb7-224">0</span><span class="sxs-lookup"><span data-stu-id="bbbb7-224">0</span></span>|<span data-ttu-id="bbbb7-225">11</span><span class="sxs-lookup"><span data-stu-id="bbbb7-225">11</span></span>|  
|<span data-ttu-id="bbbb7-226">11</span><span class="sxs-lookup"><span data-stu-id="bbbb7-226">11</span></span>|<span data-ttu-id="bbbb7-227">Bike Buyer -> Region = Europe</span><span class="sxs-lookup"><span data-stu-id="bbbb7-227">Bike Buyer -> Region = Europe</span></span>|<span data-ttu-id="bbbb7-228">0.29787234</span><span class="sxs-lookup"><span data-stu-id="bbbb7-228">0.29787234</span></span>|<span data-ttu-id="bbbb7-229">5208</span><span class="sxs-lookup"><span data-stu-id="bbbb7-229">5208</span></span>|<span data-ttu-id="bbbb7-230">0</span><span class="sxs-lookup"><span data-stu-id="bbbb7-230">0</span></span>|<span data-ttu-id="bbbb7-231">11</span><span class="sxs-lookup"><span data-stu-id="bbbb7-231">11</span></span>|  
  
 <span data-ttu-id="bbbb7-232">节点中所存储的某些列与您可从边际统计信息获得的相同，如节点概率分数和节点支持值。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-232">Some of the columns stored in the nodes are the same that you can get from the marginal statistics nodes, such as the node probability score and the node support values.</span></span> <span data-ttu-id="bbbb7-233">但 MSOLAP_NODE_SCORE 是特殊值，只提供给输入属性节点，指示此节点在模型中的相对重要性。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-233">However, the MSOLAP_NODE_SCORE is a special value provided only for the input attribute nodes, and indicates the relative importance of this attribute in the model.</span></span> <span data-ttu-id="bbbb7-234">您可以在“依赖关系网络”窗格中查看更多同类信息，但不会提供分数。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-234">You can see much the same information in the Dependency Network pane of the viewer; however, the viewer does not provide scores.</span></span>  
  
 <span data-ttu-id="bbbb7-235">下面的查询返回模型中所有属性的重要性分数：</span><span class="sxs-lookup"><span data-stu-id="bbbb7-235">The following query returns the importance scores of all attributes in the model:</span></span>  
  
```  
SELECT NODE_CAPTION, MSOLAP_NODE_SCORE  
FROM TM_NaiveBayes.CONTENT  
WHERE NODE_TYPE = 10  
ORDER BY MSOLAP_NODE_SCORE DESC  
```  
  
 <span data-ttu-id="bbbb7-236">示例结果：</span><span class="sxs-lookup"><span data-stu-id="bbbb7-236">Sample results:</span></span>  
  
|<span data-ttu-id="bbbb7-237">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="bbbb7-237">NODE_CAPTION</span></span>|<span data-ttu-id="bbbb7-238">MSOLAP_NODE_SCORE</span><span class="sxs-lookup"><span data-stu-id="bbbb7-238">MSOLAP_NODE_SCORE</span></span>|  
|-------------------|-------------------------|  
|<span data-ttu-id="bbbb7-239">Bike Buyer -> Total Children</span><span class="sxs-lookup"><span data-stu-id="bbbb7-239">Bike Buyer -> Total Children</span></span>|<span data-ttu-id="bbbb7-240">181.3654836</span><span class="sxs-lookup"><span data-stu-id="bbbb7-240">181.3654836</span></span>|  
|<span data-ttu-id="bbbb7-241">Bike Buyer -> Commute Distance</span><span class="sxs-lookup"><span data-stu-id="bbbb7-241">Bike Buyer -> Commute Distance</span></span>|<span data-ttu-id="bbbb7-242">179.8419482</span><span class="sxs-lookup"><span data-stu-id="bbbb7-242">179.8419482</span></span>|  
|<span data-ttu-id="bbbb7-243">Bike Buyer -> English Education</span><span class="sxs-lookup"><span data-stu-id="bbbb7-243">Bike Buyer -> English Education</span></span>|<span data-ttu-id="bbbb7-244">156.9841928</span><span class="sxs-lookup"><span data-stu-id="bbbb7-244">156.9841928</span></span>|  
|<span data-ttu-id="bbbb7-245">Bike Buyer -> Number Children At Home</span><span class="sxs-lookup"><span data-stu-id="bbbb7-245">Bike Buyer -> Number Children At Home</span></span>|<span data-ttu-id="bbbb7-246">111.8122599</span><span class="sxs-lookup"><span data-stu-id="bbbb7-246">111.8122599</span></span>|  
|<span data-ttu-id="bbbb7-247">Bike Buyer -> Region</span><span class="sxs-lookup"><span data-stu-id="bbbb7-247">Bike Buyer -> Region</span></span>|<span data-ttu-id="bbbb7-248">84.51555875</span><span class="sxs-lookup"><span data-stu-id="bbbb7-248">84.51555875</span></span>|  
|<span data-ttu-id="bbbb7-249">Bike Buyer -> Marital Status</span><span class="sxs-lookup"><span data-stu-id="bbbb7-249">Bike Buyer -> Marital Status</span></span>|<span data-ttu-id="bbbb7-250">23.13297354</span><span class="sxs-lookup"><span data-stu-id="bbbb7-250">23.13297354</span></span>|  
|<span data-ttu-id="bbbb7-251">Bike Buyer -> English Occupation</span><span class="sxs-lookup"><span data-stu-id="bbbb7-251">Bike Buyer -> English Occupation</span></span>|<span data-ttu-id="bbbb7-252">2.832069191</span><span class="sxs-lookup"><span data-stu-id="bbbb7-252">2.832069191</span></span>|  
  
 <span data-ttu-id="bbbb7-253">通过在 [Microsoft 一般内容树查看器](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)中查看模型内容，您可以更好地了解统计信息所关注的内容。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-253">By browsing the model content in the [Microsoft Generic Content Tree Viewer](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md), you will get a better idea of what statistics might be interesting.</span></span> <span data-ttu-id="bbbb7-254">这里演示了一些简单示例；更多时候，您可能需要执行多个示例，或者在客户端存储并处理结果。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-254">Some simple examples were demonstrated here; more often you may need to execute multiple queries or store the results and process them on the client.</span></span>  
  
###  <a name="sample-query-4-using-system-stored-procedures"></a><a name="bkmk_Query4"></a> <span data-ttu-id="bbbb7-255">示例 4：使用系统存储过程</span><span class="sxs-lookup"><span data-stu-id="bbbb7-255">Sample Query 4: Using System Stored Procedures</span></span>  
 <span data-ttu-id="bbbb7-256">除了编写自己的内容查询外，您还可以使用 Analysis Services 系统存储过程浏览结果。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-256">In addition to writing your own content queries, you can use some Analysis Services system stored procedures to explore the results.</span></span> <span data-ttu-id="bbbb7-257">若要使用系统存储过程，请为存储过程的名称加上 CALL 关键字前缀：</span><span class="sxs-lookup"><span data-stu-id="bbbb7-257">To use a system stored procedure, prefix the stored procedure name with the CALL keyword:</span></span>  
  
```  
CALL GetPredictableAttributes ('TM_NaiveBayes')  
```  
  
 <span data-ttu-id="bbbb7-258">部分结果：</span><span class="sxs-lookup"><span data-stu-id="bbbb7-258">Partial results:</span></span>  
  
|<span data-ttu-id="bbbb7-259">ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="bbbb7-259">ATTRIBUTE_NAME</span></span>|<span data-ttu-id="bbbb7-260">NODE_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="bbbb7-260">NODE_UNIQUE_NAME</span></span>|  
|---------------------|------------------------|  
|<span data-ttu-id="bbbb7-261">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="bbbb7-261">Bike Buyer</span></span>|<span data-ttu-id="bbbb7-262">100000001</span><span class="sxs-lookup"><span data-stu-id="bbbb7-262">100000001</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="bbbb7-263">这些系统存储过程用于 Analysis Services 服务器与客户端之间的通信，请仅在开发和测试挖掘模型时使用它们，以为操作提供便利。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-263">These system stored procedures are for internal communication between the Analysis Services server and the client and should only be used for convenience when developing and testing mining models.</span></span> <span data-ttu-id="bbbb7-264">创建生产系统的查询时，请始终使用 DMX 编写您自己的查询。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-264">When you create queries for a production system, you should always write your own queries by using DMX.</span></span>  
  
 <span data-ttu-id="bbbb7-265">有关 Analysis Services 系统存储过程的详细信息，请参阅[数据挖掘存储过程（Analysis Services - 数据挖掘）](/sql/analysis-services/data-mining/data-mining-stored-procedures-analysis-services-data-mining)。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-265">For more information about Analysis Services system stored procedures, see [Data Mining Stored Procedures &#40;Analysis Services - Data Mining&#41;](/sql/analysis-services/data-mining/data-mining-stored-procedures-analysis-services-data-mining).</span></span>  
  
## <a name="using-a-naive-bayes-model-to-make-predictions"></a><span data-ttu-id="bbbb7-266">使用 Naive Bayes 模型进行预测</span><span class="sxs-lookup"><span data-stu-id="bbbb7-266">Using a Naive Bayes Model to Make Predictions</span></span>  
 <span data-ttu-id="bbbb7-267">和用于浏览输入属性与可预测属性之间的关系相比，Microsoft Naive Bayes 算法通常较少用于预测。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-267">The Microsoft Naive Bayes algorithm is typically used less for prediction than it is for exploration of relationships among the input and predictable attributes.</span></span> <span data-ttu-id="bbbb7-268">但模型支持使用预测函数进行预测和关联。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-268">However, the model supports the use of prediction functions for both prediction and association.</span></span>  
  
###  <a name="sample-query-5-predicting-outcomes-using-a-singleton-query"></a><a name="bkmk_Query5"></a> <span data-ttu-id="bbbb7-269">示例查询 5：使用单独查询预测结果</span><span class="sxs-lookup"><span data-stu-id="bbbb7-269">Sample Query 5: Predicting Outcomes using a Singleton Query</span></span>  
 <span data-ttu-id="bbbb7-270">下面的查询使用单独查询提供新值，并基于模型预测具有这些特征的客户是否会购买自行车。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-270">The following query uses a singleton query to provide a new value and predict, based on the model, whether a customer with these characteristics is likely to buy a bike.</span></span> <span data-ttu-id="bbbb7-271">创建针对回归模型的查询的最简便方法是使用 **“单独查询输入”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-271">The easiest way to create a singleton query on a regression model is by using the **Singleton Query Input** dialog box.</span></span> <span data-ttu-id="bbbb7-272">例如，创建下面的 DMX 查询可以使用以下方法：依次选择 `TM_NaiveBayes` 模型、 **“单独查询”**，然后从 `[Commute Distance]` 和 `Gender`的下拉列表中选择值。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-272">For example, you can build the following DMX query by selecting the `TM_NaiveBayes` model, choosing **Singleton Query**, and selecting values from the dropdown lists for `[Commute Distance]` and `Gender`.</span></span>  
  
```  
SELECT  
  Predict([TM_NaiveBayes].[Bike Buyer])  
FROM  
  [TM_NaiveBayes]  
NATURAL PREDICTION JOIN  
(SELECT '5-10 Miles' AS [Commute Distance],  
  'F' AS [Gender]) AS t  
```  
  
 <span data-ttu-id="bbbb7-273">示例结果：</span><span class="sxs-lookup"><span data-stu-id="bbbb7-273">Example results:</span></span>  
  
|<span data-ttu-id="bbbb7-274">Expression</span><span class="sxs-lookup"><span data-stu-id="bbbb7-274">Expression</span></span>|  
|----------------|  
|<span data-ttu-id="bbbb7-275">0</span><span class="sxs-lookup"><span data-stu-id="bbbb7-275">0</span></span>|  
  
 <span data-ttu-id="bbbb7-276">预测函数返回可能性最大的值，在本例中为 0，这意味着此种类型的客户不会购买自行车。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-276">The prediction function returns the most likely value, in this case, 0, which means this type of customer is unlikely to purchase a bike.</span></span>  
  
###  <a name="sample-query-6-getting-predictions-with-probability-and-support-values"></a><a name="bkmk_Query6"></a><span data-ttu-id="bbbb7-277">示例查询6：获取具有概率和支持值的预测</span><span class="sxs-lookup"><span data-stu-id="bbbb7-277">Sample Query 6: Getting Predictions with Probability and Support Values</span></span>  
 <span data-ttu-id="bbbb7-278">除了预测结果外，您可能经常想知道概率的可靠性。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-278">In addition to predicting an outcome, you often want to know how strong the prediction is.</span></span> <span data-ttu-id="bbbb7-279">下面的查询使用与上一示例相同的单个查询，但另外添加了预测函数 [PredictHistogram (DMX)](/sql/dmx/predicthistogram-dmx)，以返回包含有关预测支持的统计信息的嵌套表。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-279">The following query uses the same singleton query as the previous example, but adds the prediction function, [PredictHistogram &#40;DMX&#41;](/sql/dmx/predicthistogram-dmx), to return a nested table that contains statistics in support of the prediction.</span></span>  
  
```  
SELECT  
  Predict([TM_NaiveBayes].[Bike Buyer]),  
  PredictHistogram([TM_NaiveBayes].[Bike Buyer])  
FROM  
  [TM_NaiveBayes]  
NATURAL PREDICTION JOIN  
(SELECT '5-10 Miles' AS [Commute Distance],  
  'F' AS [Gender]) AS t  
```  
  
 <span data-ttu-id="bbbb7-280">示例结果：</span><span class="sxs-lookup"><span data-stu-id="bbbb7-280">Example results:</span></span>  
  
|<span data-ttu-id="bbbb7-281">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="bbbb7-281">Bike Buyer</span></span>|<span data-ttu-id="bbbb7-282">$SUPPORT</span><span class="sxs-lookup"><span data-stu-id="bbbb7-282">$SUPPORT</span></span>|<span data-ttu-id="bbbb7-283">$PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="bbbb7-283">$PROBABILITY</span></span>|<span data-ttu-id="bbbb7-284">$ADJUSTEDPROBABILITY</span><span class="sxs-lookup"><span data-stu-id="bbbb7-284">$ADJUSTEDPROBABILITY</span></span>|<span data-ttu-id="bbbb7-285">$VARIANCE</span><span class="sxs-lookup"><span data-stu-id="bbbb7-285">$VARIANCE</span></span>|<span data-ttu-id="bbbb7-286">$STDEV</span><span class="sxs-lookup"><span data-stu-id="bbbb7-286">$STDEV</span></span>|  
|----------------|--------------|------------------|--------------------------|---------------|------------|  
|<span data-ttu-id="bbbb7-287">0</span><span class="sxs-lookup"><span data-stu-id="bbbb7-287">0</span></span>|<span data-ttu-id="bbbb7-288">10161.5714</span><span class="sxs-lookup"><span data-stu-id="bbbb7-288">10161.5714</span></span>|<span data-ttu-id="bbbb7-289">0.581192599</span><span class="sxs-lookup"><span data-stu-id="bbbb7-289">0.581192599</span></span>|<span data-ttu-id="bbbb7-290">0.010530981</span><span class="sxs-lookup"><span data-stu-id="bbbb7-290">0.010530981</span></span>|<span data-ttu-id="bbbb7-291">0</span><span class="sxs-lookup"><span data-stu-id="bbbb7-291">0</span></span>|<span data-ttu-id="bbbb7-292">0</span><span class="sxs-lookup"><span data-stu-id="bbbb7-292">0</span></span>|  
|<span data-ttu-id="bbbb7-293">1</span><span class="sxs-lookup"><span data-stu-id="bbbb7-293">1</span></span>|<span data-ttu-id="bbbb7-294">7321.428768</span><span class="sxs-lookup"><span data-stu-id="bbbb7-294">7321.428768</span></span>|<span data-ttu-id="bbbb7-295">0.418750215</span><span class="sxs-lookup"><span data-stu-id="bbbb7-295">0.418750215</span></span>|<span data-ttu-id="bbbb7-296">0.008945684</span><span class="sxs-lookup"><span data-stu-id="bbbb7-296">0.008945684</span></span>|<span data-ttu-id="bbbb7-297">0</span><span class="sxs-lookup"><span data-stu-id="bbbb7-297">0</span></span>|<span data-ttu-id="bbbb7-298">0</span><span class="sxs-lookup"><span data-stu-id="bbbb7-298">0</span></span>|  
||<span data-ttu-id="bbbb7-299">0.999828444</span><span class="sxs-lookup"><span data-stu-id="bbbb7-299">0.999828444</span></span>|<span data-ttu-id="bbbb7-300">5.72E-05</span><span class="sxs-lookup"><span data-stu-id="bbbb7-300">5.72E-05</span></span>|<span data-ttu-id="bbbb7-301">5.72E-05</span><span class="sxs-lookup"><span data-stu-id="bbbb7-301">5.72E-05</span></span>|<span data-ttu-id="bbbb7-302">0</span><span class="sxs-lookup"><span data-stu-id="bbbb7-302">0</span></span>|<span data-ttu-id="bbbb7-303">0</span><span class="sxs-lookup"><span data-stu-id="bbbb7-303">0</span></span>|  
  
 <span data-ttu-id="bbbb7-304">表的最后一行显示对支持和概率的缺失值调整。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-304">The final row in the table shows the adjustments to support and probability for the missing value.</span></span> <span data-ttu-id="bbbb7-305">方差和标准偏差值始终为 0，因为 Naive Bayes 模型无法对连续值建立模型。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-305">Variance and standard deviation values are always 0, because Naive Bayes models cannot model continuous values.</span></span>  
  
###  <a name="sample-query-7-predicting-associations"></a><a name="bkmk_Query7"></a><span data-ttu-id="bbbb7-306">示例查询7：预测关联</span><span class="sxs-lookup"><span data-stu-id="bbbb7-306">Sample Query 7: Predicting Associations</span></span>  
 <span data-ttu-id="bbbb7-307">如果挖掘结构包含以可预测属性作为键的嵌套表，则不可将 Microsoft Naive Bayes 算法用于关联分析。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-307">The Microsoft Naive Bayes algorithm can be used for association analysis, if the mining structure contains a nested table with the predictable attribute as the key.</span></span> <span data-ttu-id="bbbb7-308">例如，可以通过使用在数据挖掘教程的[第 3 课：生成市场篮方案（数据挖掘中级教程）](../../tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)中创建的挖掘结构来生成 Naive Bayes 模型。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-308">For example, you could build a Naive Bayes model by using the mining structure created in [Lesson 3: Building a Market Basket Scenario &#40;Intermediate Data Mining Tutorial&#41;](../../tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md) of the data mining tutorial.</span></span> <span data-ttu-id="bbbb7-309">此示例中使用的模型经过修改，目的是向事例表中添加收入和客户区域。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-309">The model used in this example was modified to add information about income and customer region in the case table.</span></span>  
  
 <span data-ttu-id="bbbb7-310">下面的查询示例给出了一个单独查询，该查询预测购买产品 `'Road Tire Tube'`时还可能会购买产品。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-310">The following query example shows a singleton query that predicts products that are related to purchases of the product, `'Road Tire Tube'`.</span></span> <span data-ttu-id="bbbb7-311">您可使用这些信息，向特定类型的客户推荐产品。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-311">You might use this information to recommend products to a specific type of customer.</span></span>  
  
```  
SELECT   PredictAssociation([Association].[v Assoc Seq Line Items])  
FROM [Association_NB]  
NATURAL PREDICTION JOIN  
(SELECT 'High' AS [Income Group],  
  'Europe' AS [Region],  
  (SELECT 'Road Tire Tube' AS [Model])   
AS [v Assoc Seq Line Items])   
AS t  
```  
  
 <span data-ttu-id="bbbb7-312">部分结果：</span><span class="sxs-lookup"><span data-stu-id="bbbb7-312">Partial results:</span></span>  
  
|<span data-ttu-id="bbbb7-313">模型</span><span class="sxs-lookup"><span data-stu-id="bbbb7-313">Model</span></span>|  
|-----------|  
|<span data-ttu-id="bbbb7-314">Women's Mountain Shorts</span><span class="sxs-lookup"><span data-stu-id="bbbb7-314">Women's Mountain Shorts</span></span>|  
|<span data-ttu-id="bbbb7-315">Water Bottle</span><span class="sxs-lookup"><span data-stu-id="bbbb7-315">Water Bottle</span></span>|  
|<span data-ttu-id="bbbb7-316">Touring-3000</span><span class="sxs-lookup"><span data-stu-id="bbbb7-316">Touring-3000</span></span>|  
|<span data-ttu-id="bbbb7-317">Touring-2000</span><span class="sxs-lookup"><span data-stu-id="bbbb7-317">Touring-2000</span></span>|  
|<span data-ttu-id="bbbb7-318">Touring-1000</span><span class="sxs-lookup"><span data-stu-id="bbbb7-318">Touring-1000</span></span>|  
  
## <a name="function-list"></a><span data-ttu-id="bbbb7-319">函数列表</span><span class="sxs-lookup"><span data-stu-id="bbbb7-319">Function List</span></span>  
 <span data-ttu-id="bbbb7-320">所有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 算法均支持一组通用的函数。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-320">All [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms support a common set of functions.</span></span> <span data-ttu-id="bbbb7-321">此外， [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes 算法还额外支持下表中列出的函数。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-321">However, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm supports the additional functions that are listed in the following table.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bbbb7-322">预测函数</span><span class="sxs-lookup"><span data-stu-id="bbbb7-322">Prediction Function</span></span>|<span data-ttu-id="bbbb7-323">使用情况</span><span class="sxs-lookup"><span data-stu-id="bbbb7-323">Usage</span></span>|  
|[<span data-ttu-id="bbbb7-324">IsDescendant (DMX)</span><span class="sxs-lookup"><span data-stu-id="bbbb7-324">IsDescendant &#40;DMX&#41;</span></span>](/sql/dmx/isdescendant-dmx)|<span data-ttu-id="bbbb7-325">确定一个节点是否是模型中另一个节点的子节点。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-325">Determines whether one node is a child of another node in the model.</span></span>|  
|[<span data-ttu-id="bbbb7-326">Predict (DMX)</span><span class="sxs-lookup"><span data-stu-id="bbbb7-326">Predict &#40;DMX&#41;</span></span>](/sql/dmx/predict-dmx)|<span data-ttu-id="bbbb7-327">返回指定列的一个预测值或一组值。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-327">Returns a predicted value, or set of values, for a specified column.</span></span>|  
|[<span data-ttu-id="bbbb7-328">PredictAdjustedProbability (DMX)</span><span class="sxs-lookup"><span data-stu-id="bbbb7-328">PredictAdjustedProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictadjustedprobability-dmx)|<span data-ttu-id="bbbb7-329">返回加权的概率。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-329">Returns the weighted probability.</span></span>|  
|[<span data-ttu-id="bbbb7-330">PredictAssociation (DMX)</span><span class="sxs-lookup"><span data-stu-id="bbbb7-330">PredictAssociation &#40;DMX&#41;</span></span>](/sql/dmx/predictassociation-dmx)|<span data-ttu-id="bbbb7-331">预测关联数据集中的成员身份。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-331">Predicts membership in an associative dataset.</span></span>|  
|[<span data-ttu-id="bbbb7-332">PredictNodeId (DMX)</span><span class="sxs-lookup"><span data-stu-id="bbbb7-332">PredictNodeId &#40;DMX&#41;</span></span>](/sql/dmx/predictnodeid-dmx)|<span data-ttu-id="bbbb7-333">返回每个事例的 Node_ID。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-333">Returns the Node_ID for each case.</span></span>|  
|[<span data-ttu-id="bbbb7-334">PredictProbability (DMX)</span><span class="sxs-lookup"><span data-stu-id="bbbb7-334">PredictProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictprobability-dmx)|<span data-ttu-id="bbbb7-335">返回预测值的概率。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-335">Returns probability for the predicted value.</span></span>|  
|[<span data-ttu-id="bbbb7-336">PredictSupport (DMX)</span><span class="sxs-lookup"><span data-stu-id="bbbb7-336">PredictSupport &#40;DMX&#41;</span></span>](/sql/dmx/predictsupport-dmx)|<span data-ttu-id="bbbb7-337">返回指定状态的支持值。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-337">Returns the support value for a specified state.</span></span>|  
  
 <span data-ttu-id="bbbb7-338">若要查看特定函数的语法，请参阅[数据挖掘扩展插件 (DMX) 函数参考](/sql/dmx/data-mining-extensions-dmx-function-reference)。</span><span class="sxs-lookup"><span data-stu-id="bbbb7-338">To see  the syntax of specific functions, see [Data Mining Extensions &#40;DMX&#41; Function Reference](/sql/dmx/data-mining-extensions-dmx-function-reference).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbbb7-339">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bbbb7-339">See Also</span></span>  
 <span data-ttu-id="bbbb7-340">[Microsoft Naive Bayes 算法技术参考](microsoft-naive-bayes-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="bbbb7-340">[Microsoft Naive Bayes Algorithm Technical Reference](microsoft-naive-bayes-algorithm-technical-reference.md) </span></span>  
 <span data-ttu-id="bbbb7-341">[Microsoft Naive Bayes 算法](microsoft-naive-bayes-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="bbbb7-341">[Microsoft Naive Bayes Algorithm](microsoft-naive-bayes-algorithm.md) </span></span>  
 [<span data-ttu-id="bbbb7-342">Naive Bayes 模型的挖掘模型内容（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="bbbb7-342">Mining Model Content for Naive Bayes Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-naive-bayes-models-analysis-services-data-mining.md)  
  
  
