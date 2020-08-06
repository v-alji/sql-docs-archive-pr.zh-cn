---
title: 逻辑回归模型查询示例 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- logistic regression [Analysis Services]
- content queries [DMX]
ms.assetid: 7c8e13a3-5c67-46c2-abfa-4881e6ef9c62
author: minewiskan
ms.author: owend
ms.openlocfilehash: d432d38794e65e8b8bea69608479e330649ee395
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577097"
---
# <a name="logistic-regression-model-query-examples"></a><span data-ttu-id="f7d94-102">逻辑回归模型查询示例</span><span class="sxs-lookup"><span data-stu-id="f7d94-102">Logistic Regression Model Query Examples</span></span>
  <span data-ttu-id="f7d94-103">在对数据挖掘模型创建查询时，可以创建内容查询，也可以创建预测查询。内容查询提供有关分析时发现的模式的详细信息，预测查询使用模型中的模式来应用新数据进行预测。</span><span class="sxs-lookup"><span data-stu-id="f7d94-103">When you create a query against a data mining model, you can create a content query, which provides details about the patterns discovered in analysis, or you can create a prediction query, which uses the patterns in the model to make predictions using new data.</span></span>  
  
 <span data-ttu-id="f7d94-104">本节介绍如何为基于 Microsoft 逻辑回归算法的模型创建查询。</span><span class="sxs-lookup"><span data-stu-id="f7d94-104">This section explains how to create queries for models that are based on the Microsoft Logistic Regression algorithm.</span></span>  
  
 <span data-ttu-id="f7d94-105">**内容查询**</span><span class="sxs-lookup"><span data-stu-id="f7d94-105">**Content Queries**</span></span>  
  
 [<span data-ttu-id="f7d94-106">使用数据挖掘架构行集检索模型参数</span><span class="sxs-lookup"><span data-stu-id="f7d94-106">Retrieving Model Parameters by Using the Data Mining Schema Rowset</span></span>](#bkmk_Query1)  
  
 [<span data-ttu-id="f7d94-107">使用 DMX 查找有关模型的其他详细信息</span><span class="sxs-lookup"><span data-stu-id="f7d94-107">Finding Additional Detail about the Model by Using DMX</span></span>](#bkmk_Query2)  
  
 <span data-ttu-id="f7d94-108">**预测查询**</span><span class="sxs-lookup"><span data-stu-id="f7d94-108">**Prediction Queries**</span></span>  
  
 [<span data-ttu-id="f7d94-109">对连续值进行预测</span><span class="sxs-lookup"><span data-stu-id="f7d94-109">Making Predictions for a Continuous Value</span></span>](#bkmk_Query3)  
  
 [<span data-ttu-id="f7d94-110">对离散值进行预测</span><span class="sxs-lookup"><span data-stu-id="f7d94-110">Making Predictions for a Discrete Value</span></span>](#bkmk_Query4)  
  
##  <a name="getting-information-about-the-logistic-regression-model"></a><a name="bkmk_top"></a><span data-ttu-id="f7d94-111">获取有关逻辑回归模型的信息</span><span class="sxs-lookup"><span data-stu-id="f7d94-111">Getting Information about the Logistic Regression Model</span></span>  
 <span data-ttu-id="f7d94-112">逻辑回归模型是使用带有一组特殊参数的 Microsoft 神经网络算法创建的；因此，逻辑回归模型具有某些与神经网络模型相同的信息，但是会简单些。</span><span class="sxs-lookup"><span data-stu-id="f7d94-112">Logistic regression models are created by using the Microsoft Neural Network algorithm with a special set of parameters; therefore, a logistic regression model has some of the same information as a neural networks model, but is less complex.</span></span> <span data-ttu-id="f7d94-113">若要了解模型内容的结构以及哪些节点存储哪类信息，请参阅 [逻辑回归模型的挖掘模型内容（Analysis Services - 数据挖掘）](mining-model-content-for-logistic-regression-models.md)。</span><span class="sxs-lookup"><span data-stu-id="f7d94-113">To understand the structure of the model content, and which node types store what kind of information, see [Mining Model Content for Logistic Regression Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-logistic-regression-models.md).</span></span>  
  
 <span data-ttu-id="f7d94-114">若要继续探讨查询方案，可以按“数据挖掘中级教程”中的下一节所述，创建逻辑回归模型： [第 5 课：生成神经网络模型和逻辑回归模型（数据挖掘中级教程）](../../tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="f7d94-114">To follow along in the query scenarios, you can create a logistic regression model as described in the following section of the Intermediate Data Mining Tutorial: [Lesson 5: Building Neural Network and Logistic Regression Models &#40;Intermediate Data Mining Tutorial&#41;](../../tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md).</span></span>  
  
 <span data-ttu-id="f7d94-115">此外，还可以使用 [数据挖掘基础教程](../../tutorials/basic-data-mining-tutorial.md)中的挖掘结构 Targeted Mailing。</span><span class="sxs-lookup"><span data-stu-id="f7d94-115">You can also use the mining structure, Targeted Mailing, from the [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md).</span></span>  
  
```  
ALTER MINING STRUCTURE [Targeted Mailing]  
ADD MINING MODEL [TM_Logistic Regression]  
([Customer Key],  
[Age],  
[Bike Buyer] PREDICT,  
[Yearly Income] PREDICT,  
[Commute Distance],  
[English Education],  
Gender,  
[House Owner Flag],  
[Marital Status],  
[Number Cars Owned],  
[Number Children At Home],  
[Region],  
[Total Children]  
)  
USING Microsoft_Logistic_Regression  
```  
  
###  <a name="sample-query-1-retrieving-model-parameters-by-using-the-data-mining-schema-rowset"></a><a name="bkmk_Query1"></a><span data-ttu-id="f7d94-116">示例查询1：使用数据挖掘架构行集检索模型参数</span><span class="sxs-lookup"><span data-stu-id="f7d94-116">Sample Query 1: Retrieving Model Parameters by Using the Data Mining Schema Rowset</span></span>  
 <span data-ttu-id="f7d94-117">通过查询数据挖掘架构行集，您可以找到有关模型的元数据，如模型创建时间、上次处理模型的时间、模型基于的挖掘结构的名称以及用作可预测属性的列的名称。</span><span class="sxs-lookup"><span data-stu-id="f7d94-117">By querying the data mining schema rowset, you can find metadata about the model, such as when it was created, when the model was last processed, the name of the mining structure that the model is based on, and the name of the column used as the predictable attribute.</span></span> <span data-ttu-id="f7d94-118">下面的示例返回首次创建模型时所用的参数、模型的名称和类型以及模型的创建时间。</span><span class="sxs-lookup"><span data-stu-id="f7d94-118">The following example returns the parameters that were used when the model was first created, together with the name and type of the model, and the date that it was created.</span></span>  
  
```  
SELECT MODEL_NAME, SERVICE_NAME, DATE_CREATED, MINING_PARAMETERS   
FROM $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'Call Center_LR'  
```  
  
 <span data-ttu-id="f7d94-119">示例结果：</span><span class="sxs-lookup"><span data-stu-id="f7d94-119">Sample results:</span></span>  
  
|<span data-ttu-id="f7d94-120">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="f7d94-120">MODEL_NAME</span></span>|<span data-ttu-id="f7d94-121">SERVICE_NAME</span><span class="sxs-lookup"><span data-stu-id="f7d94-121">SERVICE_NAME</span></span>|<span data-ttu-id="f7d94-122">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="f7d94-122">DATE_CREATED</span></span>|<span data-ttu-id="f7d94-123">MINING_PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f7d94-123">MINING_PARAMETERS</span></span>|  
|-----------------|-------------------|-------------------|------------------------|  
|<span data-ttu-id="f7d94-124">Call Center_LR</span><span class="sxs-lookup"><span data-stu-id="f7d94-124">Call Center_LR</span></span>|<span data-ttu-id="f7d94-125">Microsoft_Logistic_Regression</span><span class="sxs-lookup"><span data-stu-id="f7d94-125">Microsoft_Logistic_Regression</span></span>|<span data-ttu-id="f7d94-126">04/07/2009 20:38:33</span><span class="sxs-lookup"><span data-stu-id="f7d94-126">04/07/2009 20:38:33</span></span>|<span data-ttu-id="f7d94-127">HOLDOUT_PERCENTAGE=30, HOLDOUT_SEED=1, MAXIMUM_INPUT_ATTRIBUTES=255, MAXIMUM_OUTPUT_ATTRIBUTES=255, MAXIMUM_STATES=100, SAMPLE_SIZE=10000</span><span class="sxs-lookup"><span data-stu-id="f7d94-127">HOLDOUT_PERCENTAGE=30, HOLDOUT_SEED=1, MAXIMUM_INPUT_ATTRIBUTES=255, MAXIMUM_OUTPUT_ATTRIBUTES=255, MAXIMUM_STATES=100, SAMPLE_SIZE=10000</span></span>|  
  
###  <a name="sample-query-2-finding-additional-detail-about-the-model-by-using-dmx"></a><a name="bkmk_Query2"></a><span data-ttu-id="f7d94-128">示例查询2：使用 DMX 查找有关模型的其他详细信息</span><span class="sxs-lookup"><span data-stu-id="f7d94-128">Sample Query 2: Finding Additional Detail about the Model by Using DMX</span></span>  
 <span data-ttu-id="f7d94-129">下面的查询返回有关逻辑回归模型的一些基本信息。</span><span class="sxs-lookup"><span data-stu-id="f7d94-129">The following query returns some basic information about the logistic regression model.</span></span> <span data-ttu-id="f7d94-130">逻辑回归模型在很多方面与神经网络模型类似，包括都存在描述用作输入的值的边际统计信息节点 (NODE_TYPE = 24)。</span><span class="sxs-lookup"><span data-stu-id="f7d94-130">A logistic regression model is similar to a neural network model in many ways, including the presence of a marginal statistic node (NODE_TYPE = 24) that describes the values used as inputs.</span></span> <span data-ttu-id="f7d94-131">此示例查询使用 Targeted Mailing 模型，并通过从嵌套表 NODE_DISTRIBUTION 中检索所有输入的值来获取这些值。</span><span class="sxs-lookup"><span data-stu-id="f7d94-131">This example query uses the Targeted Mailing model, and gets the values of all the inputs by retrieving them from the nested table, NODE_DISTRIBUTION.</span></span>  
  
```  
SELECT FLATTENED NODE_DISTRIBUTION AS t  
FROM [TM_Logistic Regression].CONTENT   
```  
  
 <span data-ttu-id="f7d94-132">部分结果：</span><span class="sxs-lookup"><span data-stu-id="f7d94-132">Partial results:</span></span>  
  
|<span data-ttu-id="f7d94-133">T.ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="f7d94-133">t.ATTRIBUTE_NAME</span></span>|<span data-ttu-id="f7d94-134">t.ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="f7d94-134">t.ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="f7d94-135">t.SUPPORT</span><span class="sxs-lookup"><span data-stu-id="f7d94-135">t.SUPPORT</span></span>|<span data-ttu-id="f7d94-136">t.PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="f7d94-136">t.PROBABILITY</span></span>|<span data-ttu-id="f7d94-137">t.VARIANCE</span><span class="sxs-lookup"><span data-stu-id="f7d94-137">t.VARIANCE</span></span>|<span data-ttu-id="f7d94-138">t.VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="f7d94-138">t.VALUETYPE</span></span>|  
|-----------------------|------------------------|---------------|-------------------|----------------|-----------------|  
|<span data-ttu-id="f7d94-139">年限</span><span class="sxs-lookup"><span data-stu-id="f7d94-139">Age</span></span>|<span data-ttu-id="f7d94-140">Missing</span><span class="sxs-lookup"><span data-stu-id="f7d94-140">Missing</span></span>|<span data-ttu-id="f7d94-141">0</span><span class="sxs-lookup"><span data-stu-id="f7d94-141">0</span></span>|<span data-ttu-id="f7d94-142">0</span><span class="sxs-lookup"><span data-stu-id="f7d94-142">0</span></span>|<span data-ttu-id="f7d94-143">0</span><span class="sxs-lookup"><span data-stu-id="f7d94-143">0</span></span>|<span data-ttu-id="f7d94-144">1</span><span class="sxs-lookup"><span data-stu-id="f7d94-144">1</span></span>|  
|<span data-ttu-id="f7d94-145">年限</span><span class="sxs-lookup"><span data-stu-id="f7d94-145">Age</span></span>|<span data-ttu-id="f7d94-146">45.43491192</span><span class="sxs-lookup"><span data-stu-id="f7d94-146">45.43491192</span></span>|<span data-ttu-id="f7d94-147">17484</span><span class="sxs-lookup"><span data-stu-id="f7d94-147">17484</span></span>|<span data-ttu-id="f7d94-148">1</span><span class="sxs-lookup"><span data-stu-id="f7d94-148">1</span></span>|<span data-ttu-id="f7d94-149">126.9544114</span><span class="sxs-lookup"><span data-stu-id="f7d94-149">126.9544114</span></span>|<span data-ttu-id="f7d94-150">3</span><span class="sxs-lookup"><span data-stu-id="f7d94-150">3</span></span>|  
|<span data-ttu-id="f7d94-151">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="f7d94-151">Bike Buyer</span></span>|<span data-ttu-id="f7d94-152">Missing</span><span class="sxs-lookup"><span data-stu-id="f7d94-152">Missing</span></span>|<span data-ttu-id="f7d94-153">0</span><span class="sxs-lookup"><span data-stu-id="f7d94-153">0</span></span>|<span data-ttu-id="f7d94-154">0</span><span class="sxs-lookup"><span data-stu-id="f7d94-154">0</span></span>|<span data-ttu-id="f7d94-155">0</span><span class="sxs-lookup"><span data-stu-id="f7d94-155">0</span></span>|<span data-ttu-id="f7d94-156">1</span><span class="sxs-lookup"><span data-stu-id="f7d94-156">1</span></span>|  
|<span data-ttu-id="f7d94-157">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="f7d94-157">Bike Buyer</span></span>|<span data-ttu-id="f7d94-158">0</span><span class="sxs-lookup"><span data-stu-id="f7d94-158">0</span></span>|<span data-ttu-id="f7d94-159">8869</span><span class="sxs-lookup"><span data-stu-id="f7d94-159">8869</span></span>|<span data-ttu-id="f7d94-160">0.507263784</span><span class="sxs-lookup"><span data-stu-id="f7d94-160">0.507263784</span></span>|<span data-ttu-id="f7d94-161">0</span><span class="sxs-lookup"><span data-stu-id="f7d94-161">0</span></span>|<span data-ttu-id="f7d94-162">4</span><span class="sxs-lookup"><span data-stu-id="f7d94-162">4</span></span>|  
|<span data-ttu-id="f7d94-163">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="f7d94-163">Bike Buyer</span></span>|<span data-ttu-id="f7d94-164">1</span><span class="sxs-lookup"><span data-stu-id="f7d94-164">1</span></span>|<span data-ttu-id="f7d94-165">8615</span><span class="sxs-lookup"><span data-stu-id="f7d94-165">8615</span></span>|<span data-ttu-id="f7d94-166">0.492736216</span><span class="sxs-lookup"><span data-stu-id="f7d94-166">0.492736216</span></span>|<span data-ttu-id="f7d94-167">0</span><span class="sxs-lookup"><span data-stu-id="f7d94-167">0</span></span>|<span data-ttu-id="f7d94-168">4</span><span class="sxs-lookup"><span data-stu-id="f7d94-168">4</span></span>|  
|<span data-ttu-id="f7d94-169">上下班路程</span><span class="sxs-lookup"><span data-stu-id="f7d94-169">Commute Distance</span></span>|<span data-ttu-id="f7d94-170">Missing</span><span class="sxs-lookup"><span data-stu-id="f7d94-170">Missing</span></span>|<span data-ttu-id="f7d94-171">0</span><span class="sxs-lookup"><span data-stu-id="f7d94-171">0</span></span>|<span data-ttu-id="f7d94-172">0</span><span class="sxs-lookup"><span data-stu-id="f7d94-172">0</span></span>|<span data-ttu-id="f7d94-173">0</span><span class="sxs-lookup"><span data-stu-id="f7d94-173">0</span></span>|<span data-ttu-id="f7d94-174">1</span><span class="sxs-lookup"><span data-stu-id="f7d94-174">1</span></span>|  
|<span data-ttu-id="f7d94-175">上下班路程</span><span class="sxs-lookup"><span data-stu-id="f7d94-175">Commute Distance</span></span>|<span data-ttu-id="f7d94-176">5-10 英里</span><span class="sxs-lookup"><span data-stu-id="f7d94-176">5-10 Miles</span></span>|<span data-ttu-id="f7d94-177">3033</span><span class="sxs-lookup"><span data-stu-id="f7d94-177">3033</span></span>|<span data-ttu-id="f7d94-178">0.173472889</span><span class="sxs-lookup"><span data-stu-id="f7d94-178">0.173472889</span></span>|<span data-ttu-id="f7d94-179">0</span><span class="sxs-lookup"><span data-stu-id="f7d94-179">0</span></span>|<span data-ttu-id="f7d94-180">4</span><span class="sxs-lookup"><span data-stu-id="f7d94-180">4</span></span>|  
  
 <span data-ttu-id="f7d94-181">实际查询会返回多得多的行；但是此示例演示了所提供的有关输入的信息类型。</span><span class="sxs-lookup"><span data-stu-id="f7d94-181">The actual query returns many more rows; however, this sample illustrates the type of information that is provided about the inputs.</span></span> <span data-ttu-id="f7d94-182">对于离散输入，每个可能值都列在表中。</span><span class="sxs-lookup"><span data-stu-id="f7d94-182">For discrete inputs, each possible value is listed in the table.</span></span> <span data-ttu-id="f7d94-183">对于“年龄”之类的连续值输入，全部列出是不可能的，所以输入被离散化为均值。</span><span class="sxs-lookup"><span data-stu-id="f7d94-183">For continuous-value inputs such as Age, a complete listing is impossible, so the input is discretized as a mean.</span></span> <span data-ttu-id="f7d94-184">有关如何使用边际统计信息节点中的信息的详细信息，请参阅 [逻辑回归模型的挖掘模型内容（Analysis Services - 数据挖掘）](mining-model-content-for-logistic-regression-models.md)。</span><span class="sxs-lookup"><span data-stu-id="f7d94-184">For more information about how to use the information in the marginal statistics node, see [Mining Model Content for Logistic Regression Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-logistic-regression-models.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f7d94-185">为便于查看，结果是平展的，但是，如果您的访问接口支持分层行集，则可在单个列中返回嵌套表。</span><span class="sxs-lookup"><span data-stu-id="f7d94-185">The results have been flattened for easier viewing, but you can return the nested table in a single column if your provider supports hierarchical rowsets.</span></span>  
  
## <a name="prediction-queries-on-a-logistic-regression-model"></a><span data-ttu-id="f7d94-186">针对逻辑回归模型的预测查询</span><span class="sxs-lookup"><span data-stu-id="f7d94-186">Prediction Queries on a Logistic Regression Model</span></span>  
 <span data-ttu-id="f7d94-187">对每种挖掘模型都可以使用 [Predict (DMX)](/sql/dmx/predict-dmx) 函数向模型提供新数据并基于新值进行预测。</span><span class="sxs-lookup"><span data-stu-id="f7d94-187">You can use the [Predict &#40;DMX&#41;](/sql/dmx/predict-dmx) function with every kind of mining model to provide new data to the model and make predictions based on the new values.</span></span> <span data-ttu-id="f7d94-188">还可以使用函数返回有关预测的其他信息，例如，预测正确性的概率。</span><span class="sxs-lookup"><span data-stu-id="f7d94-188">You can also use functions to return additional information about the prediction, such as the probability that a prediction is correct.</span></span> <span data-ttu-id="f7d94-189">本节提供针对逻辑回归模型的预测查询的一些示例。</span><span class="sxs-lookup"><span data-stu-id="f7d94-189">This section provides some examples of prediction queries on a logistic regression model.</span></span>  
  
###  <a name="sample-query-3-making-predictions-for-a-continuous-value"></a><a name="bkmk_Query3"></a><span data-ttu-id="f7d94-190">示例查询3：对连续值进行预测</span><span class="sxs-lookup"><span data-stu-id="f7d94-190">Sample Query 3: Making Predictions for a Continuous Value</span></span>  
 <span data-ttu-id="f7d94-191">由于逻辑回归支持在输入和预测中都使用连续属性，因此可以轻松地在您的数据中创建与各种因素相关的模型。</span><span class="sxs-lookup"><span data-stu-id="f7d94-191">Because logistic regression supports the use of continuous attributes for both input and prediction, it is easy to create models that correlate various factors in your data.</span></span> <span data-ttu-id="f7d94-192">您可以使用预测查询来探查这些因素之间的关系。</span><span class="sxs-lookup"><span data-stu-id="f7d94-192">You can use prediction queries to explore the relationship among these factors.</span></span>  
  
 <span data-ttu-id="f7d94-193">以下查询示例基于中级教程中的 Call Center（呼叫中心）模型，并创建了预测 Friday AM shift（周五早班）的服务等级的单独查询。</span><span class="sxs-lookup"><span data-stu-id="f7d94-193">The following query sample is based on the Call Center model, from the Intermediate Tutorial, and creates a singleton query that predicts service grade for the Friday AM shift.</span></span> <span data-ttu-id="f7d94-194">[PredictHistogram (DMX)](/sql/dmx/predicthistogram-dmx) 函数返回一个嵌套表，该表提供与用于了解预测值的有效性相关的统计信息。</span><span class="sxs-lookup"><span data-stu-id="f7d94-194">The [PredictHistogram (DMX)](/sql/dmx/predicthistogram-dmx) function returns a nested table that provides statistics relevant to understanding the validity of the predicted value.</span></span>  
  
```  
SELECT  
  Predict([Call Center_LR].[Service Grade]) as Predicted ServiceGrade,  
  PredictHistogram([Call Center_LR].[Service Grade]) as [Results],  
FROM  
  [Call Center_LR]  
NATURAL PREDICTION JOIN  
(SELECT 'Friday' AS [Day Of Week],  
  'AM' AS [Shift]) AS t  
```  
  
 <span data-ttu-id="f7d94-195">示例结果：</span><span class="sxs-lookup"><span data-stu-id="f7d94-195">Sample results:</span></span>  
  
 <span data-ttu-id="f7d94-196">**预测的服务等级**：0.102601830123659</span><span class="sxs-lookup"><span data-stu-id="f7d94-196">**Predicted Service Grade**: 0.102601830123659</span></span>  
  
 <span data-ttu-id="f7d94-197">**结果**</span><span class="sxs-lookup"><span data-stu-id="f7d94-197">**Results**</span></span>  
  
|<span data-ttu-id="f7d94-198">Service Grade</span><span class="sxs-lookup"><span data-stu-id="f7d94-198">Service Grade</span></span>|<span data-ttu-id="f7d94-199">$SUPPORT</span><span class="sxs-lookup"><span data-stu-id="f7d94-199">$SUPPORT</span></span>|<span data-ttu-id="f7d94-200">$PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="f7d94-200">$PROBABILITY</span></span>|<span data-ttu-id="f7d94-201">$ADJUSTEDPROBABILITY</span><span class="sxs-lookup"><span data-stu-id="f7d94-201">$ADJUSTEDPROBABILITY</span></span>|<span data-ttu-id="f7d94-202">$VARIANCE</span><span class="sxs-lookup"><span data-stu-id="f7d94-202">$VARIANCE</span></span>|<span data-ttu-id="f7d94-203">$STDEV</span><span class="sxs-lookup"><span data-stu-id="f7d94-203">$STDEV</span></span>|  
|-------------------|--------------|------------------|--------------------------|---------------|------------|  
|<span data-ttu-id="f7d94-204">0.102601830123659</span><span class="sxs-lookup"><span data-stu-id="f7d94-204">0.102601830123659</span></span>|<span data-ttu-id="f7d94-205">83.0232558139535</span><span class="sxs-lookup"><span data-stu-id="f7d94-205">83.0232558139535</span></span>|<span data-ttu-id="f7d94-206">0.988372093023256</span><span class="sxs-lookup"><span data-stu-id="f7d94-206">0.988372093023256</span></span>|<span data-ttu-id="f7d94-207">0</span><span class="sxs-lookup"><span data-stu-id="f7d94-207">0</span></span>|<span data-ttu-id="f7d94-208">0.00120552660600087</span><span class="sxs-lookup"><span data-stu-id="f7d94-208">0.00120552660600087</span></span>|<span data-ttu-id="f7d94-209">0.034720694203902</span><span class="sxs-lookup"><span data-stu-id="f7d94-209">0.034720694203902</span></span>|  
||<span data-ttu-id="f7d94-210">0.976744186046512</span><span class="sxs-lookup"><span data-stu-id="f7d94-210">0.976744186046512</span></span>|<span data-ttu-id="f7d94-211">0.0116279069767442</span><span class="sxs-lookup"><span data-stu-id="f7d94-211">0.0116279069767442</span></span>|<span data-ttu-id="f7d94-212">0.0116279069767442</span><span class="sxs-lookup"><span data-stu-id="f7d94-212">0.0116279069767442</span></span>|<span data-ttu-id="f7d94-213">0</span><span class="sxs-lookup"><span data-stu-id="f7d94-213">0</span></span>|<span data-ttu-id="f7d94-214">0</span><span class="sxs-lookup"><span data-stu-id="f7d94-214">0</span></span>|  
  
 <span data-ttu-id="f7d94-215">有关嵌套表 NODE_DISTRIBUTION 中的概率、支持和标准偏差值的详细信息，请参阅 [逻辑回归模型的挖掘模型内容（Analysis Services - 数据挖掘）](mining-model-content-for-logistic-regression-models.md)。</span><span class="sxs-lookup"><span data-stu-id="f7d94-215">For more information about the probability, support, and standard deviation values in the nested NODE_DISTRIBUTION table, see [Mining Model Content for Logistic Regression Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-logistic-regression-models.md).</span></span>  
  
###  <a name="sample-query-4-making-predictions-for-a-discrete-value"></a><a name="bkmk_Query4"></a><span data-ttu-id="f7d94-216">示例查询4：对离散值进行预测</span><span class="sxs-lookup"><span data-stu-id="f7d94-216">Sample Query 4: Making Predictions for a Discrete Value</span></span>  
 <span data-ttu-id="f7d94-217">要分析产生二进制结果的因素时通常使用逻辑回归。</span><span class="sxs-lookup"><span data-stu-id="f7d94-217">Logistic regression is typically used in scenarios where you want to analyze the factors that contribute to a binary outcome.</span></span> <span data-ttu-id="f7d94-218">尽管教程中使用的模型预测的是连续值 **ServiceGrade**，但实际生活中你可能还是希望设置该模型来预测服务等级是否符合特定的离散化目标值。</span><span class="sxs-lookup"><span data-stu-id="f7d94-218">Although the model used in the tutorial predicts a continuous value, **ServiceGrade**, in a real-life scenario you might want to set up the model to predict whether service grade met some discretized target value.</span></span> <span data-ttu-id="f7d94-219">或者，您可以使用连续值来输出预测，但之后将这些预测结果分组到 **较好**、 **一般**或 **较差**这几个等级中。</span><span class="sxs-lookup"><span data-stu-id="f7d94-219">Alternatively, you could output the predictions using a continuous value but later group the predicted outcomes into **Good**, **Fair**, or **Poor**.</span></span>  
  
 <span data-ttu-id="f7d94-220">下面的示例演示如何更改可预测属性的分组方式。</span><span class="sxs-lookup"><span data-stu-id="f7d94-220">The following sample illustrates how to change the way that the predictable attribute is grouped.</span></span> <span data-ttu-id="f7d94-221">若要执行此操作，您需要复制挖掘结构，然后更改目标列的离散化方法，以便值归入各分组而不是连续的。</span><span class="sxs-lookup"><span data-stu-id="f7d94-221">To do this, you create a copy of the mining structure and then change the discretization method of the target column so that the values are grouped rather than continuous.</span></span>  
  
 <span data-ttu-id="f7d94-222">以下过程介绍如何更改呼叫中心数据中的 Service Grade 值的分组。</span><span class="sxs-lookup"><span data-stu-id="f7d94-222">The following procedure describes how to change the grouping of Service Grade values in the Call Center data.</span></span>  
  
##### <a name="to-create-a-discretized-version-of-the-call-center-mining-structure-and-models"></a><span data-ttu-id="f7d94-223">创建 Call Center 挖掘结构和模型的离散化版本</span><span class="sxs-lookup"><span data-stu-id="f7d94-223">To create a discretized version of the Call Center mining structure and models</span></span>  
  
1.  <span data-ttu-id="f7d94-224">在的 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 解决方案资源管理器中，展开 "**挖掘结构**"。</span><span class="sxs-lookup"><span data-stu-id="f7d94-224">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], in Solution Explorer, expand **Mining Structures**.</span></span>  
  
2.  <span data-ttu-id="f7d94-225">右键单击 Call Center.dmm 并选择\*\*\*\*“复制”。</span><span class="sxs-lookup"><span data-stu-id="f7d94-225">Right-click Call Center.dmm and select **Copy**.</span></span>  
  
3.  <span data-ttu-id="f7d94-226">右键单击 **“挖掘结构”** ，然后选择 **“粘贴”**。</span><span class="sxs-lookup"><span data-stu-id="f7d94-226">Right click **Mining Structures** and select **Paste**.</span></span> <span data-ttu-id="f7d94-227">将添加名为 Call Center 1 的新挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="f7d94-227">A new mining structure iss added, named Call Center 1.</span></span>  
  
4.  <span data-ttu-id="f7d94-228">右键单击新的挖掘结构，然后选择“重命名”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="f7d94-228">Right-click the new mining structure and select **Rename**.</span></span> <span data-ttu-id="f7d94-229">键入新名称 **Call Center Discretized**。</span><span class="sxs-lookup"><span data-stu-id="f7d94-229">Type the new name, **Call Center Discretized**.</span></span>  
  
5.  <span data-ttu-id="f7d94-230">双击新的挖掘结构以在设计器中将其打开。</span><span class="sxs-lookup"><span data-stu-id="f7d94-230">Double-click the new mining structure to open it in the designer.</span></span> <span data-ttu-id="f7d94-231">请注意，随之复制了所有挖掘模型，并且都具有扩展名 1。</span><span class="sxs-lookup"><span data-stu-id="f7d94-231">Notice that the mining models have all been copied as well, and all have the extension 1.</span></span> <span data-ttu-id="f7d94-232">暂时将这些名称保留原样。</span><span class="sxs-lookup"><span data-stu-id="f7d94-232">Leave the names as is for now.</span></span>  
  
6.  <span data-ttu-id="f7d94-233">在“挖掘结构”选项卡中，右键单击 Service Grade 对应的列，然后选择“属性”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="f7d94-233">In the **Mining Structure** tab, right-click the column for Service Grade, and select **Properties**.</span></span>  
  
7.  <span data-ttu-id="f7d94-234">将 `Content` 属性从 "**连续**" 更改为 "**离散**化"。</span><span class="sxs-lookup"><span data-stu-id="f7d94-234">Change the `Content` property from **Continuous** to **Discretized**.</span></span> <span data-ttu-id="f7d94-235">将 `DiscretizationMethod` 属性更改为 "**分类**"。</span><span class="sxs-lookup"><span data-stu-id="f7d94-235">Change the `DiscretizationMethod` property to **Clusters**.</span></span> <span data-ttu-id="f7d94-236">对于 Discretization BucketCount，键入 **3**。</span><span class="sxs-lookup"><span data-stu-id="f7d94-236">For Discretization BucketCount, type **3**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f7d94-237">这些参数仅用于演示过程，不一定生成有效模型。</span><span class="sxs-lookup"><span data-stu-id="f7d94-237">These parameters are just used for illustrating the process, and do not necessarily produce a valid model,</span></span>  
  
8.  <span data-ttu-id="f7d94-238">从 **“挖掘模型”** 菜单上选择 **“处理挖掘结构和所有模型”**。</span><span class="sxs-lookup"><span data-stu-id="f7d94-238">From the **Mining Model** menu, select **Process structure and all models**.</span></span>  
  
 <span data-ttu-id="f7d94-239">以下示例查询基于此离散化模型，并预测了周中某指定日期的服务等级以及每个预测的结果的概率。</span><span class="sxs-lookup"><span data-stu-id="f7d94-239">The following sample query is based on this discretized model, and predicts the service grade for the specified day of the week, together with the probabilities for each predicted outcome.</span></span>  
  
```  
SELECT  
  (PredictHistogram([Call Center_LR 1].[Service Grade])) as [Predictions]  
FROM  
  [Call Center_LR 1]  
NATURAL PREDICTION JOIN  
(SELECT 'Saturday' AS [Day Of Week]) AS t    
```  
  
 <span data-ttu-id="f7d94-240">预期的结果：</span><span class="sxs-lookup"><span data-stu-id="f7d94-240">Expected results:</span></span>  
  
 <span data-ttu-id="f7d94-241">**预测**</span><span class="sxs-lookup"><span data-stu-id="f7d94-241">**Predictions**</span></span>  
  
|<span data-ttu-id="f7d94-242">Service Grade</span><span class="sxs-lookup"><span data-stu-id="f7d94-242">Service Grade</span></span>|<span data-ttu-id="f7d94-243">$SUPPORT</span><span class="sxs-lookup"><span data-stu-id="f7d94-243">$SUPPORT</span></span>|<span data-ttu-id="f7d94-244">$PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="f7d94-244">$PROBABILITY</span></span>|<span data-ttu-id="f7d94-245">$ADJUSTEDPROBABILITY</span><span class="sxs-lookup"><span data-stu-id="f7d94-245">$ADJUSTEDPROBABILITY</span></span>|<span data-ttu-id="f7d94-246">$VARIANCE</span><span class="sxs-lookup"><span data-stu-id="f7d94-246">$VARIANCE</span></span>|<span data-ttu-id="f7d94-247">$STDEV</span><span class="sxs-lookup"><span data-stu-id="f7d94-247">$STDEV</span></span>|  
|-------------------|--------------|------------------|--------------------------|---------------|------------|  
|<span data-ttu-id="f7d94-248">0.10872718383125</span><span class="sxs-lookup"><span data-stu-id="f7d94-248">0.10872718383125</span></span>|<span data-ttu-id="f7d94-249">35.7246504770641</span><span class="sxs-lookup"><span data-stu-id="f7d94-249">35.7246504770641</span></span>|<span data-ttu-id="f7d94-250">0.425293458060287</span><span class="sxs-lookup"><span data-stu-id="f7d94-250">0.425293458060287</span></span>|<span data-ttu-id="f7d94-251">0.0170168360030293</span><span class="sxs-lookup"><span data-stu-id="f7d94-251">0.0170168360030293</span></span>|<span data-ttu-id="f7d94-252">0</span><span class="sxs-lookup"><span data-stu-id="f7d94-252">0</span></span>|<span data-ttu-id="f7d94-253">0</span><span class="sxs-lookup"><span data-stu-id="f7d94-253">0</span></span>|  
|<span data-ttu-id="f7d94-254">0.05855769230625</span><span class="sxs-lookup"><span data-stu-id="f7d94-254">0.05855769230625</span></span>|<span data-ttu-id="f7d94-255">31.7098880800703</span><span class="sxs-lookup"><span data-stu-id="f7d94-255">31.7098880800703</span></span>|<span data-ttu-id="f7d94-256">0.377498667619885</span><span class="sxs-lookup"><span data-stu-id="f7d94-256">0.377498667619885</span></span>|<span data-ttu-id="f7d94-257">0.020882020060454</span><span class="sxs-lookup"><span data-stu-id="f7d94-257">0.020882020060454</span></span>|<span data-ttu-id="f7d94-258">0</span><span class="sxs-lookup"><span data-stu-id="f7d94-258">0</span></span>|<span data-ttu-id="f7d94-259">0</span><span class="sxs-lookup"><span data-stu-id="f7d94-259">0</span></span>|  
|<span data-ttu-id="f7d94-260">0.170169491525</span><span class="sxs-lookup"><span data-stu-id="f7d94-260">0.170169491525</span></span>|<span data-ttu-id="f7d94-261">15.6109159883202</span><span class="sxs-lookup"><span data-stu-id="f7d94-261">15.6109159883202</span></span>|<span data-ttu-id="f7d94-262">0.185844237956192</span><span class="sxs-lookup"><span data-stu-id="f7d94-262">0.185844237956192</span></span>|<span data-ttu-id="f7d94-263">0.0661386571386049</span><span class="sxs-lookup"><span data-stu-id="f7d94-263">0.0661386571386049</span></span>|<span data-ttu-id="f7d94-264">0</span><span class="sxs-lookup"><span data-stu-id="f7d94-264">0</span></span>|<span data-ttu-id="f7d94-265">0</span><span class="sxs-lookup"><span data-stu-id="f7d94-265">0</span></span>|  
||<span data-ttu-id="f7d94-266">0.954545454545455</span><span class="sxs-lookup"><span data-stu-id="f7d94-266">0.954545454545455</span></span>|<span data-ttu-id="f7d94-267">0.0113636363636364</span><span class="sxs-lookup"><span data-stu-id="f7d94-267">0.0113636363636364</span></span>|<span data-ttu-id="f7d94-268">0.0113636363636364</span><span class="sxs-lookup"><span data-stu-id="f7d94-268">0.0113636363636364</span></span>|<span data-ttu-id="f7d94-269">0</span><span class="sxs-lookup"><span data-stu-id="f7d94-269">0</span></span>|<span data-ttu-id="f7d94-270">0</span><span class="sxs-lookup"><span data-stu-id="f7d94-270">0</span></span>|  
  
 <span data-ttu-id="f7d94-271">请注意，预测结果已分组到指定的三个类别中；但是，这些分组基于数据中实际值的分类，而不是基于您可能设置为业务目标的任意值。</span><span class="sxs-lookup"><span data-stu-id="f7d94-271">Note that the predicted outcomes have been grouped into three categories as specified; however, these groupings are based on the clustering of actual values in the data, not arbitrary values that you might set as business goals.</span></span>  
  
## <a name="list-of-prediction-functions"></a><span data-ttu-id="f7d94-272">预测函数的列表</span><span class="sxs-lookup"><span data-stu-id="f7d94-272">List of Prediction Functions</span></span>  
 <span data-ttu-id="f7d94-273">所有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 算法均支持一组通用的函数。</span><span class="sxs-lookup"><span data-stu-id="f7d94-273">All [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms support a common set of functions.</span></span> <span data-ttu-id="f7d94-274">但 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 逻辑回归算法还额外支持下表中列出的函数。</span><span class="sxs-lookup"><span data-stu-id="f7d94-274">However, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Logistic Regression algorithm supports the additional functions listed in the following table.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f7d94-275">预测函数</span><span class="sxs-lookup"><span data-stu-id="f7d94-275">Prediction Function</span></span>|<span data-ttu-id="f7d94-276">使用情况</span><span class="sxs-lookup"><span data-stu-id="f7d94-276">Usage</span></span>|  
|[<span data-ttu-id="f7d94-277">IsDescendant (DMX)</span><span class="sxs-lookup"><span data-stu-id="f7d94-277">IsDescendant &#40;DMX&#41;</span></span>](/sql/dmx/isdescendant-dmx)|<span data-ttu-id="f7d94-278">确定一个节点是否是模型中另一个节点的子节点。</span><span class="sxs-lookup"><span data-stu-id="f7d94-278">Determines whether one node is a child of another node in the model.</span></span>|  
|[<span data-ttu-id="f7d94-279">PredictAdjustedProbability (DMX)</span><span class="sxs-lookup"><span data-stu-id="f7d94-279">PredictAdjustedProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictadjustedprobability-dmx)|<span data-ttu-id="f7d94-280">返回指定状态调整后的概率。</span><span class="sxs-lookup"><span data-stu-id="f7d94-280">Returns the adjusted probability of a specified state.</span></span>|  
|[<span data-ttu-id="f7d94-281">PredictHistogram (DMX)</span><span class="sxs-lookup"><span data-stu-id="f7d94-281">PredictHistogram &#40;DMX&#41;</span></span>](/sql/dmx/predicthistogram-dmx)|<span data-ttu-id="f7d94-282">返回指定列的一个预测值或一组值。</span><span class="sxs-lookup"><span data-stu-id="f7d94-282">Returns a predicted value, or set of values, for a specified column.</span></span>|  
|[<span data-ttu-id="f7d94-283">PredictProbability (DMX)</span><span class="sxs-lookup"><span data-stu-id="f7d94-283">PredictProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictprobability-dmx)|<span data-ttu-id="f7d94-284">返回指定状态的概率。</span><span class="sxs-lookup"><span data-stu-id="f7d94-284">Returns the probability for a specified state.</span></span>|  
|[<span data-ttu-id="f7d94-285">PredictStdev (DMX)</span><span class="sxs-lookup"><span data-stu-id="f7d94-285">PredictStdev &#40;DMX&#41;</span></span>](/sql/dmx/predictstdev-dmx)|<span data-ttu-id="f7d94-286">返回预测值的标准偏差。</span><span class="sxs-lookup"><span data-stu-id="f7d94-286">Returns standard deviation for the predicted value.</span></span>|  
|[<span data-ttu-id="f7d94-287">PredictSupport (DMX)</span><span class="sxs-lookup"><span data-stu-id="f7d94-287">PredictSupport &#40;DMX&#41;</span></span>](/sql/dmx/predictsupport-dmx)|<span data-ttu-id="f7d94-288">返回指定状态的支持值。</span><span class="sxs-lookup"><span data-stu-id="f7d94-288">Returns the support value for a specified state.</span></span>|  
|[<span data-ttu-id="f7d94-289">PredictVariance (DMX)</span><span class="sxs-lookup"><span data-stu-id="f7d94-289">PredictVariance &#40;DMX&#41;</span></span>](/sql/dmx/predictvariance-dmx)|<span data-ttu-id="f7d94-290">返回指定列的方差。</span><span class="sxs-lookup"><span data-stu-id="f7d94-290">Returns the variance of a specified column.</span></span>|  
  
 <span data-ttu-id="f7d94-291">有关所有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 算法都支持的通用函数的列表，请参阅[通用预测函数 (DMX)](/sql/dmx/general-prediction-functions-dmx)。</span><span class="sxs-lookup"><span data-stu-id="f7d94-291">For a list of the functions that are common to all [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms, see [General Prediction Functions &#40;DMX&#41;](/sql/dmx/general-prediction-functions-dmx).</span></span> <span data-ttu-id="f7d94-292">有关特定函数的语法，请参阅[数据挖掘扩展插件 (DMX) 函数引用](/sql/dmx/data-mining-extensions-dmx-function-reference)。</span><span class="sxs-lookup"><span data-stu-id="f7d94-292">For the syntax of specific functions, see [Data Mining Extensions &#40;DMX&#41; Function Reference](/sql/dmx/data-mining-extensions-dmx-function-reference).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f7d94-293">对于神经网络模型和逻辑回归模型， [PredictSupport (DMX)](/sql/dmx/predictsupport-dmx) 函数将返回表示整个模型的定型集大小的单个值。</span><span class="sxs-lookup"><span data-stu-id="f7d94-293">For neural network and logistic regression models, the [PredictSupport &#40;DMX&#41;](/sql/dmx/predictsupport-dmx) function returns a single value that represents the size of the training set for the entire model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7d94-294">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f7d94-294">See Also</span></span>  
 <span data-ttu-id="f7d94-295">[数据挖掘查询](data-mining-queries.md) </span><span class="sxs-lookup"><span data-stu-id="f7d94-295">[Data Mining Queries](data-mining-queries.md) </span></span>  
 <span data-ttu-id="f7d94-296">[Microsoft 逻辑回归算法](microsoft-logistic-regression-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="f7d94-296">[Microsoft Logistic Regression Algorithm](microsoft-logistic-regression-algorithm.md) </span></span>  
 <span data-ttu-id="f7d94-297">[Microsoft 逻辑回归算法技术参考](microsoft-logistic-regression-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="f7d94-297">[Microsoft Logistic Regression Algorithm Technical Reference](microsoft-logistic-regression-algorithm-technical-reference.md) </span></span>  
 <span data-ttu-id="f7d94-298">[&#40;Analysis Services 数据挖掘的逻辑回归模型的挖掘模型内容&#41;](mining-model-content-for-logistic-regression-models.md) </span><span class="sxs-lookup"><span data-stu-id="f7d94-298">[Mining Model Content for Logistic Regression Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-logistic-regression-models.md) </span></span>  
 [<span data-ttu-id="f7d94-299">第 5 课：生成神经网络模型和逻辑回归模型（数据挖掘中级教程）</span><span class="sxs-lookup"><span data-stu-id="f7d94-299">Lesson 5: Building Neural Network and Logistic Regression Models &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
  
  
