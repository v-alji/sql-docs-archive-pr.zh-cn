---
title: 线性回归模型查询示例 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- linear regression algorithms [Analysis Services]
- linear regression [Analysis Services]
- content queries [DMX]
ms.assetid: fd3cf312-57a1-44b6-b772-fce6fc1c26d7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 02d4b7309d7b5ea3d6295089f0fb2e778b1c9b4b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591007"
---
# <a name="linear-regression-model-query-examples"></a><span data-ttu-id="d3c6e-102">线性回归模型查询示例</span><span class="sxs-lookup"><span data-stu-id="d3c6e-102">Linear Regression Model Query Examples</span></span>
  <span data-ttu-id="d3c6e-103">在创建针对数据挖掘模型的查询时，您既可以创建内容查询，也可以创建预测查询。内容查询提供有关分析过程中发现的模式的详细信息，而预测查询则使用模型中的模式对新数据进行预测。</span><span class="sxs-lookup"><span data-stu-id="d3c6e-103">When you create a query against a data mining model, you can create a content query, which provides details about the patterns discovered in analysis, or you can create a prediction query, which uses the patterns in the model to make predictions for new data.</span></span> <span data-ttu-id="d3c6e-104">例如，内容查询可能会提供有关回归公式的更多详细信息，而预测查询则可能会告诉您新数据点是否适合模型。</span><span class="sxs-lookup"><span data-stu-id="d3c6e-104">For example, a content query might provide additional details about the regression formula, while a prediction query might tell you if a new data point fits the model.</span></span> <span data-ttu-id="d3c6e-105">您还可以使用查询来检索有关模型的元数据。</span><span class="sxs-lookup"><span data-stu-id="d3c6e-105">You can also retrieve metadata about the model by using a query.</span></span>  
  
 <span data-ttu-id="d3c6e-106">本节介绍如何针对基于 Microsoft 线性回归算法的模型创建查询。</span><span class="sxs-lookup"><span data-stu-id="d3c6e-106">This section explains how to create queries for models that are based on the Microsoft Linear Regression algorithm.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d3c6e-107">由于线性回归基于 Microsoft 决策树算法的特殊情况，因而会存在诸多相似性，且某些使用连续可预测属性的决策树模型可包含回归公式。</span><span class="sxs-lookup"><span data-stu-id="d3c6e-107">Because linear regression is based on a special case of the Microsoft Decision Trees algorithm, there are many similarities, and some decision tree models that use continuous predictable attributes can contain regression formulas.</span></span> <span data-ttu-id="d3c6e-108">有关详细信息，请参阅 [Microsoft 决策树算法技术参考](microsoft-decision-trees-algorithm-technical-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="d3c6e-108">For more information, see [Microsoft Decision Trees Algorithm Technical Reference](microsoft-decision-trees-algorithm-technical-reference.md).</span></span>  
  
 <span data-ttu-id="d3c6e-109">**内容查询**</span><span class="sxs-lookup"><span data-stu-id="d3c6e-109">**Content queries**</span></span>  
  
 [<span data-ttu-id="d3c6e-110">使用数据挖掘架构行集确定用于模型的参数</span><span class="sxs-lookup"><span data-stu-id="d3c6e-110">Using the Data Mining Schema Rowset to determine parameters used for a model</span></span>](#bkmk_Query1)  
  
 [<span data-ttu-id="d3c6e-111">使用 DMX 返回模型的回归公式</span><span class="sxs-lookup"><span data-stu-id="d3c6e-111">Using DMX to return the regression formula for the model</span></span>](#bkmk_Query2)  
  
 [<span data-ttu-id="d3c6e-112">仅返回模型的系数</span><span class="sxs-lookup"><span data-stu-id="d3c6e-112">Returning only the coefficient for the model</span></span>](#bkmk_Query3)  
  
 <span data-ttu-id="d3c6e-113">**预测查询**</span><span class="sxs-lookup"><span data-stu-id="d3c6e-113">**Prediction queries**</span></span>  
  
 [<span data-ttu-id="d3c6e-114">使用单独查询预测收入</span><span class="sxs-lookup"><span data-stu-id="d3c6e-114">Predicting income using a singleton query</span></span>](#bkmk_Query4)  
  
 [<span data-ttu-id="d3c6e-115">对回归模型使用预测函数</span><span class="sxs-lookup"><span data-stu-id="d3c6e-115">Using prediction functions with a regression model</span></span>](#bkmk_Query5)  
  
##  <a name="finding-information-about-the-linear-regression-model"></a><a name="bkmk_top"></a> <span data-ttu-id="d3c6e-116">查找有关线性回归模型的信息</span><span class="sxs-lookup"><span data-stu-id="d3c6e-116">Finding Information about the Linear Regression Model</span></span>  
 <span data-ttu-id="d3c6e-117">线性回归模型的结构极其简单：挖掘模型将数据表示为定义回归公式的单个节点。</span><span class="sxs-lookup"><span data-stu-id="d3c6e-117">The structure of a linear regression model is extremely simple: the mining model represents the data as a single node, which defines the regression formula.</span></span> <span data-ttu-id="d3c6e-118">有关详细信息，请参阅 [逻辑回归模型的挖掘模型内容（Analysis Services - 数据挖掘）](mining-model-content-for-logistic-regression-models.md)。</span><span class="sxs-lookup"><span data-stu-id="d3c6e-118">For more information, see [Mining Model Content for Logistic Regression Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-logistic-regression-models.md).</span></span>  
  
 [<span data-ttu-id="d3c6e-119">返回页首</span><span class="sxs-lookup"><span data-stu-id="d3c6e-119">Return to Top</span></span>](#bkmk_top)  
  
###  <a name="sample-query-1-using-the-data-mining-schema-rowset-to-determine-parameters-used-for-a-model"></a><a name="bkmk_Query1"></a> <span data-ttu-id="d3c6e-120">示例查询 1：使用数据挖掘架构行集确定用于模型的参数</span><span class="sxs-lookup"><span data-stu-id="d3c6e-120">Sample Query 1: Using the Data Mining Schema Rowset to Determine Parameters Used for a Model</span></span>  
 <span data-ttu-id="d3c6e-121">通过查询数据挖掘架构行集，您可找到模型的元数据。</span><span class="sxs-lookup"><span data-stu-id="d3c6e-121">By querying the data mining schema rowset, you can find metadata about the model.</span></span> <span data-ttu-id="d3c6e-122">这包括模型创建时间、上次处理模型时间、模型所基于的挖掘结构的名称以及指定为可预测属性的列的名称。</span><span class="sxs-lookup"><span data-stu-id="d3c6e-122">This might include when the model was created, when the model was last processed, the name of the mining structure that the model is based on, and the name of the column designated as the predictable attribute.</span></span> <span data-ttu-id="d3c6e-123">您还可以返回首次创建模型时所使用的参数。</span><span class="sxs-lookup"><span data-stu-id="d3c6e-123">You can also return the parameters that were used when the model was first created.</span></span>  
  
```  
SELECT MINING_PARAMETERS   
FROM $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'TM_PredictIncome'  
```  
  
 <span data-ttu-id="d3c6e-124">示例结果：</span><span class="sxs-lookup"><span data-stu-id="d3c6e-124">Sample results:</span></span>  
  
|<span data-ttu-id="d3c6e-125">MINING_PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d3c6e-125">MINING_PARAMETERS</span></span>|  
|------------------------|  
|<span data-ttu-id="d3c6e-126">COMPLEXITY_PENALTY=0.9,</span><span class="sxs-lookup"><span data-stu-id="d3c6e-126">COMPLEXITY_PENALTY=0.9,</span></span><br /><br /> <span data-ttu-id="d3c6e-127">MAXIMUM_INPUT_ATTRIBUTES=255,</span><span class="sxs-lookup"><span data-stu-id="d3c6e-127">MAXIMUM_INPUT_ATTRIBUTES=255,</span></span><br /><br /> <span data-ttu-id="d3c6e-128">MAXIMUM_OUTPUT_ATTRIBUTES=255,</span><span class="sxs-lookup"><span data-stu-id="d3c6e-128">MAXIMUM_OUTPUT_ATTRIBUTES=255,</span></span><br /><br /> <span data-ttu-id="d3c6e-129">MINIMUM_SUPPORT=10,</span><span class="sxs-lookup"><span data-stu-id="d3c6e-129">MINIMUM_SUPPORT=10,</span></span><br /><br /> <span data-ttu-id="d3c6e-130">SCORE_METHOD=4,</span><span class="sxs-lookup"><span data-stu-id="d3c6e-130">SCORE_METHOD=4,</span></span><br /><br /> <span data-ttu-id="d3c6e-131">SPLIT_METHOD=3,</span><span class="sxs-lookup"><span data-stu-id="d3c6e-131">SPLIT_METHOD=3,</span></span><br /><br /> <span data-ttu-id="d3c6e-132">FORCE_REGRESSOR=</span><span class="sxs-lookup"><span data-stu-id="d3c6e-132">FORCE_REGRESSOR=</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="d3c6e-133">参数设置“`FORCE_REGRESSOR =` ”指示参数 FORCE_REGRESSOR 的当前值为 Null。</span><span class="sxs-lookup"><span data-stu-id="d3c6e-133">The parameter setting, "`FORCE_REGRESSOR =` ", indicates that the current value for the FORCE_REGRESSOR parameter is null.</span></span>  
  
 [<span data-ttu-id="d3c6e-134">返回页首</span><span class="sxs-lookup"><span data-stu-id="d3c6e-134">Return to Top</span></span>](#bkmk_top)  
  
###  <a name="sample-query-2-retrieving-the-regression-formula-for-the-model"></a><a name="bkmk_Query2"></a> <span data-ttu-id="d3c6e-135">示例查询 2：检索模型的回归公式</span><span class="sxs-lookup"><span data-stu-id="d3c6e-135">Sample Query 2: Retrieving the Regression Formula for the Model</span></span>  
 <span data-ttu-id="d3c6e-136">下面的查询返回一个线性回归模型的挖掘模型内容，该回归模型是通过使用 [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md)中使用的目标邮件数据源创建的。</span><span class="sxs-lookup"><span data-stu-id="d3c6e-136">The following query returns the mining model content for a linear regression model that was built by using the same Targeted Mailing data source that was used in the [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md).</span></span> <span data-ttu-id="d3c6e-137">此模型基于年龄预测客户收入。</span><span class="sxs-lookup"><span data-stu-id="d3c6e-137">This model predicts customer income based on age.</span></span>  
  
 <span data-ttu-id="d3c6e-138">查询返回包含回归公式的节点的内容。</span><span class="sxs-lookup"><span data-stu-id="d3c6e-138">The query returns the contents of the node that contains the regression formula.</span></span> <span data-ttu-id="d3c6e-139">所有变量和系数均存储在嵌套表 NODE_DISTRIBUTION 的单独行中。</span><span class="sxs-lookup"><span data-stu-id="d3c6e-139">Each variable and coefficient is stored in a separate row of the nested NODE_DISTRIBUTION table.</span></span> <span data-ttu-id="d3c6e-140">如果要查看完整的回归公式，请使用 [Microsoft 树查看器](browse-a-model-using-the-microsoft-tree-viewer.md)，单击“(全部)”节点，然后打开“挖掘图例”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="d3c6e-140">If you want to view the complete regression formula, use the [Microsoft Tree Viewer](browse-a-model-using-the-microsoft-tree-viewer.md), click the **(All)** node, and open the **Mining Legend**.</span></span>  
  
```  
SELECT FLATTENED NODE_DISTRIBUTION as t  
FROM LR_PredictIncome.CONTENT  
```  
  
> [!NOTE]  
>  <span data-ttu-id="d3c6e-141"> 如果通过使用查询（如 `SELECT <column name> from NODE_DISTRIBUTION`）来引用嵌套表的单个列，则必须将某些列（如 **SUPPORT** 或 **PROBABILITY**）用括号括起来，以将它们与同名的保留字区分开。</span><span class="sxs-lookup"><span data-stu-id="d3c6e-141">If you reference individual columns of the nested table by using a query such as `SELECT <column name> from NODE_DISTRIBUTION`, some columns, such as **SUPPORT** or **PROBABILITY**, must be enclosed in brackets to distinguish them from reserved keywords of the same name.</span></span>  
  
 <span data-ttu-id="d3c6e-142">预期的结果：</span><span class="sxs-lookup"><span data-stu-id="d3c6e-142">Expected results:</span></span>  
  
|<span data-ttu-id="d3c6e-143">T.ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="d3c6e-143">t.ATTRIBUTE_NAME</span></span>|<span data-ttu-id="d3c6e-144">t.ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="d3c6e-144">t.ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="d3c6e-145">t.SUPPORT</span><span class="sxs-lookup"><span data-stu-id="d3c6e-145">t.SUPPORT</span></span>|<span data-ttu-id="d3c6e-146">t.PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="d3c6e-146">t.PROBABILITY</span></span>|<span data-ttu-id="d3c6e-147">t.VARIANCE</span><span class="sxs-lookup"><span data-stu-id="d3c6e-147">t.VARIANCE</span></span>|<span data-ttu-id="d3c6e-148">t.VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="d3c6e-148">t.VALUETYPE</span></span>|  
|-----------------------|------------------------|---------------|-------------------|----------------|-----------------|  
|<span data-ttu-id="d3c6e-149">Yearly Income</span><span class="sxs-lookup"><span data-stu-id="d3c6e-149">Yearly Income</span></span>|<span data-ttu-id="d3c6e-150">Missing</span><span class="sxs-lookup"><span data-stu-id="d3c6e-150">Missing</span></span>|<span data-ttu-id="d3c6e-151">0</span><span class="sxs-lookup"><span data-stu-id="d3c6e-151">0</span></span>|<span data-ttu-id="d3c6e-152">0.000457142857142857</span><span class="sxs-lookup"><span data-stu-id="d3c6e-152">0.000457142857142857</span></span>|<span data-ttu-id="d3c6e-153">0</span><span class="sxs-lookup"><span data-stu-id="d3c6e-153">0</span></span>|<span data-ttu-id="d3c6e-154">1</span><span class="sxs-lookup"><span data-stu-id="d3c6e-154">1</span></span>|  
|<span data-ttu-id="d3c6e-155">Yearly Income</span><span class="sxs-lookup"><span data-stu-id="d3c6e-155">Yearly Income</span></span>|<span data-ttu-id="d3c6e-156">57220.8876687257</span><span class="sxs-lookup"><span data-stu-id="d3c6e-156">57220.8876687257</span></span>|<span data-ttu-id="d3c6e-157">17484</span><span class="sxs-lookup"><span data-stu-id="d3c6e-157">17484</span></span>|<span data-ttu-id="d3c6e-158">0.999542857142857</span><span class="sxs-lookup"><span data-stu-id="d3c6e-158">0.999542857142857</span></span>|<span data-ttu-id="d3c6e-159">1041275619.52776</span><span class="sxs-lookup"><span data-stu-id="d3c6e-159">1041275619.52776</span></span>|<span data-ttu-id="d3c6e-160">3</span><span class="sxs-lookup"><span data-stu-id="d3c6e-160">3</span></span>|  
|<span data-ttu-id="d3c6e-161">年限</span><span class="sxs-lookup"><span data-stu-id="d3c6e-161">Age</span></span>|<span data-ttu-id="d3c6e-162">471.687717702463</span><span class="sxs-lookup"><span data-stu-id="d3c6e-162">471.687717702463</span></span>|<span data-ttu-id="d3c6e-163">0</span><span class="sxs-lookup"><span data-stu-id="d3c6e-163">0</span></span>|<span data-ttu-id="d3c6e-164">0</span><span class="sxs-lookup"><span data-stu-id="d3c6e-164">0</span></span>|<span data-ttu-id="d3c6e-165">126.969442359327</span><span class="sxs-lookup"><span data-stu-id="d3c6e-165">126.969442359327</span></span>|<span data-ttu-id="d3c6e-166">7</span><span class="sxs-lookup"><span data-stu-id="d3c6e-166">7</span></span>|  
|<span data-ttu-id="d3c6e-167">年限</span><span class="sxs-lookup"><span data-stu-id="d3c6e-167">Age</span></span>|<span data-ttu-id="d3c6e-168">234.680904692439</span><span class="sxs-lookup"><span data-stu-id="d3c6e-168">234.680904692439</span></span>|<span data-ttu-id="d3c6e-169">0</span><span class="sxs-lookup"><span data-stu-id="d3c6e-169">0</span></span>|<span data-ttu-id="d3c6e-170">0</span><span class="sxs-lookup"><span data-stu-id="d3c6e-170">0</span></span>|<span data-ttu-id="d3c6e-171">0</span><span class="sxs-lookup"><span data-stu-id="d3c6e-171">0</span></span>|<span data-ttu-id="d3c6e-172">8</span><span class="sxs-lookup"><span data-stu-id="d3c6e-172">8</span></span>|  
|<span data-ttu-id="d3c6e-173">年限</span><span class="sxs-lookup"><span data-stu-id="d3c6e-173">Age</span></span>|<span data-ttu-id="d3c6e-174">45.4269617936399</span><span class="sxs-lookup"><span data-stu-id="d3c6e-174">45.4269617936399</span></span>|<span data-ttu-id="d3c6e-175">0</span><span class="sxs-lookup"><span data-stu-id="d3c6e-175">0</span></span>|<span data-ttu-id="d3c6e-176">0</span><span class="sxs-lookup"><span data-stu-id="d3c6e-176">0</span></span>|<span data-ttu-id="d3c6e-177">126.969442359327</span><span class="sxs-lookup"><span data-stu-id="d3c6e-177">126.969442359327</span></span>|<span data-ttu-id="d3c6e-178">9</span><span class="sxs-lookup"><span data-stu-id="d3c6e-178">9</span></span>|  
||<span data-ttu-id="d3c6e-179">35793.5477381267</span><span class="sxs-lookup"><span data-stu-id="d3c6e-179">35793.5477381267</span></span>|<span data-ttu-id="d3c6e-180">0</span><span class="sxs-lookup"><span data-stu-id="d3c6e-180">0</span></span>|<span data-ttu-id="d3c6e-181">0</span><span class="sxs-lookup"><span data-stu-id="d3c6e-181">0</span></span>|<span data-ttu-id="d3c6e-182">1012968919.28372</span><span class="sxs-lookup"><span data-stu-id="d3c6e-182">1012968919.28372</span></span>|<span data-ttu-id="d3c6e-183">11</span><span class="sxs-lookup"><span data-stu-id="d3c6e-183">11</span></span>|  
  
 <span data-ttu-id="d3c6e-184">我们来做个比较，在 **“挖掘图例”** 中，该回归公式显示如下：</span><span class="sxs-lookup"><span data-stu-id="d3c6e-184">In comparison, in the **Mining Legend**, the regression formula appears as follows:</span></span>  
  
 <span data-ttu-id="d3c6e-185">Yearly Income = 57,220.919 + 471.688 \* (Age - 45.427)</span><span class="sxs-lookup"><span data-stu-id="d3c6e-185">Yearly Income = 57,220.919 + 471.688 \* (Age - 45.427)</span></span>  
  
 <span data-ttu-id="d3c6e-186">可看出在“挖掘图例”中，对某些数值进行了舍入；但 NODE_DISTRIBUTION 表与“挖掘图例”实际上包含的是相同的值。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="d3c6e-186">You can see that in the **Mining Legend**, some numbers are rounded; however, the NODE_DISTRIBUTION table and the **Mining Legend** essentially contain the same values.</span></span>  
  
 <span data-ttu-id="d3c6e-187">VALUETYPE 列中的值可告诉您每一行所包含的信息的类型，这在以编程方式处理结果时很有用。</span><span class="sxs-lookup"><span data-stu-id="d3c6e-187">The values in the VALUETYPE column tell you what kind of information is contained in each row, which is useful if you are processing the results programmatically.</span></span> <span data-ttu-id="d3c6e-188">下表给出了一个线性回归公式的输出值的类型。</span><span class="sxs-lookup"><span data-stu-id="d3c6e-188">The following table shows the value types that are output for a linear regression formula.</span></span>  
  
|<span data-ttu-id="d3c6e-189">VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="d3c6e-189">VALUETYPE</span></span>|  
|---------------|  
|<span data-ttu-id="d3c6e-190">1（缺失）</span><span class="sxs-lookup"><span data-stu-id="d3c6e-190">1 (Missing)</span></span>|  
|<span data-ttu-id="d3c6e-191">3（连续）</span><span class="sxs-lookup"><span data-stu-id="d3c6e-191">3 (Continuous)</span></span>|  
|<span data-ttu-id="d3c6e-192">7（系数）</span><span class="sxs-lookup"><span data-stu-id="d3c6e-192">7 (Coefficient)</span></span>|  
|<span data-ttu-id="d3c6e-193">8（得分）</span><span class="sxs-lookup"><span data-stu-id="d3c6e-193">8 (Score Gain)</span></span>|  
|<span data-ttu-id="d3c6e-194">9（统计信息）</span><span class="sxs-lookup"><span data-stu-id="d3c6e-194">9 (Statistics)</span></span>|  
|<span data-ttu-id="d3c6e-195">7（系数）</span><span class="sxs-lookup"><span data-stu-id="d3c6e-195">7 (Coefficient)</span></span>|  
|<span data-ttu-id="d3c6e-196">8（得分）</span><span class="sxs-lookup"><span data-stu-id="d3c6e-196">8 (Score Gain)</span></span>|  
|<span data-ttu-id="d3c6e-197">9（统计信息）</span><span class="sxs-lookup"><span data-stu-id="d3c6e-197">9 (Statistics)</span></span>|  
|<span data-ttu-id="d3c6e-198">11（截距）</span><span class="sxs-lookup"><span data-stu-id="d3c6e-198">11 (Intercept)</span></span>|  
  
 <span data-ttu-id="d3c6e-199">有关回归模型每个值类型含义的详细信息，请参阅 [线性回归模型的挖掘模型内容（Analysis Services - 数据挖掘）](mining-model-content-for-linear-regression-models-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="d3c6e-199">For more information about the meaning of each value type for regression models, see [Mining Model Content for Linear Regression Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-linear-regression-models-analysis-services-data-mining.md).</span></span>  
  
 [<span data-ttu-id="d3c6e-200">返回页首</span><span class="sxs-lookup"><span data-stu-id="d3c6e-200">Return to Top</span></span>](#bkmk_top)  
  
###  <a name="sample-query-3-returning-only-the-coefficient-for-the-model"></a><a name="bkmk_Query3"></a> <span data-ttu-id="d3c6e-201">示例查询 3：仅返回模型的系数</span><span class="sxs-lookup"><span data-stu-id="d3c6e-201">Sample Query 3: Returning Only the Coefficient for the Model</span></span>  
 <span data-ttu-id="d3c6e-202">通过使用 VALUETYPE 枚举，您可以仅返回回归公式的系数，如下面的查询所示：</span><span class="sxs-lookup"><span data-stu-id="d3c6e-202">By using the VALUETYPE enumeration, you can return only the coefficient for the regression equation, as shown in the following query:</span></span>  
  
```  
SELECT FLATTENED MODEL_NAME,  
    (SELECT ATTRIBUTE_VALUE, VALUETYPE  
     FROM NODE_DISTRIBUTION  
     WHERE VALUETYPE = 11)   
AS t  
FROM LR_PredictIncome.CONTENT  
```  
  
 <span data-ttu-id="d3c6e-203">此查询返回两行：一行来自挖掘模型内容，另一行来自包含系数的嵌套表。</span><span class="sxs-lookup"><span data-stu-id="d3c6e-203">This query returns two rows, one from the mining model content, and the row from the nested table that contains the coefficient.</span></span> <span data-ttu-id="d3c6e-204">此处未包括 ATTRIBUTE_NAME 列，因为对于系数，该列始终为空。</span><span class="sxs-lookup"><span data-stu-id="d3c6e-204">The ATTRIBUTE_NAME column is not included here because it is always blank for the coefficient.</span></span>  
  
|<span data-ttu-id="d3c6e-205">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="d3c6e-205">MODEL_NAME</span></span>|<span data-ttu-id="d3c6e-206">t.ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="d3c6e-206">t.ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="d3c6e-207">t.VALUETYPE</span><span class="sxs-lookup"><span data-stu-id="d3c6e-207">t.VALUETYPE</span></span>|  
|-----------------|------------------------|-----------------|  
|<span data-ttu-id="d3c6e-208">LR_PredictIncome</span><span class="sxs-lookup"><span data-stu-id="d3c6e-208">LR_PredictIncome</span></span>|||  
|<span data-ttu-id="d3c6e-209">LR_PredictIncome</span><span class="sxs-lookup"><span data-stu-id="d3c6e-209">LR_PredictIncome</span></span>|<span data-ttu-id="d3c6e-210">35793.5477381267</span><span class="sxs-lookup"><span data-stu-id="d3c6e-210">35793.5477381267</span></span>|<span data-ttu-id="d3c6e-211">11</span><span class="sxs-lookup"><span data-stu-id="d3c6e-211">11</span></span>|  
  
 [<span data-ttu-id="d3c6e-212">返回页首</span><span class="sxs-lookup"><span data-stu-id="d3c6e-212">Return to Top</span></span>](#bkmk_top)  
  
## <a name="making-predictions-from-a-linear-regression-model"></a><span data-ttu-id="d3c6e-213">根据线性回归模型进行预测</span><span class="sxs-lookup"><span data-stu-id="d3c6e-213">Making Predictions from a Linear Regression Model</span></span>  
 <span data-ttu-id="d3c6e-214">您可以使用数据挖掘设计器中的“挖掘模型预测”选项卡来生成针对线性回归模型的预测查询。</span><span class="sxs-lookup"><span data-stu-id="d3c6e-214">You can build prediction queries on linear regression models by using the Mining Model Prediction tab in Data Mining Designer.</span></span> <span data-ttu-id="d3c6e-215">您可从 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 和 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]使用预测查询生成器。</span><span class="sxs-lookup"><span data-stu-id="d3c6e-215">The prediction query builder is available in both [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d3c6e-216">此外，还可以通过使用 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Excel 数据挖掘外接插件或 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Excel 数据挖掘外接插件来创建针对回归模型的查询。</span><span class="sxs-lookup"><span data-stu-id="d3c6e-216">You can also create queries on regression models by using the [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Data Mining Add-ins for Excel or the [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Data Mining Add-ins for Excel.</span></span> <span data-ttu-id="d3c6e-217">即使 Excel 数据挖掘外接插件无法创建回归模型，您也可以浏览并查询 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]实例中所存储的所有模型。</span><span class="sxs-lookup"><span data-stu-id="d3c6e-217">Even though the Data Mining Add-ins for Excel do not create regression models, you can browse and query any mining model that is stored on an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="d3c6e-218">返回页首</span><span class="sxs-lookup"><span data-stu-id="d3c6e-218">Return to Top</span></span>](#bkmk_top)  
  
###  <a name="sample-query-4-predicting-income-using-a-singleton-query"></a><a name="bkmk_Query4"></a> <span data-ttu-id="d3c6e-219">示例查询 4：使用单独查询预测收入</span><span class="sxs-lookup"><span data-stu-id="d3c6e-219">Sample Query 4: Predicting Income using a Singleton Query</span></span>  
 <span data-ttu-id="d3c6e-220">创建针对回归模型的单个查询的最简便方法是使用 **“单独查询输入”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="d3c6e-220">The easiest way to create a single query on a regression model is by using the **Singleton Query Input** dialog box.</span></span> <span data-ttu-id="d3c6e-221">例如，您可以通过选择相应的回归模型，选择 "**单独查询**"，然后键入 `20` 作为**Age**值，来生成以下 DMX 查询。</span><span class="sxs-lookup"><span data-stu-id="d3c6e-221">For example, you can build the following DMX query by selecting the appropriate regression model, choosing **Singleton Query**, and then typing `20` as the value for **Age**.</span></span>  
  
```  
SELECT [LR_PredictIncome].[Yearly Income]  
From   [LR_PredictIncome]  
NATURAL PREDICTION JOIN  
(SELECT 20 AS [Age]) AS t  
```  
  
 <span data-ttu-id="d3c6e-222">示例结果：</span><span class="sxs-lookup"><span data-stu-id="d3c6e-222">Sample results:</span></span>  
  
|<span data-ttu-id="d3c6e-223">Yearly Income</span><span class="sxs-lookup"><span data-stu-id="d3c6e-223">Yearly Income</span></span>|  
|-------------------|  
|<span data-ttu-id="d3c6e-224">45227.302092176</span><span class="sxs-lookup"><span data-stu-id="d3c6e-224">45227.302092176</span></span>|  
  
 [<span data-ttu-id="d3c6e-225">返回页首</span><span class="sxs-lookup"><span data-stu-id="d3c6e-225">Return to Top</span></span>](#bkmk_top)  
  
###  <a name="sample-query-5-using-prediction-functions-with-a-regression-model"></a><a name="bkmk_Query5"></a> <span data-ttu-id="d3c6e-226">示例查询 5：对回归模型使用预测函数</span><span class="sxs-lookup"><span data-stu-id="d3c6e-226">Sample Query 5: Using Prediction Functions with a Regression Model</span></span>  
 <span data-ttu-id="d3c6e-227">您可以对线性回归模型使用许多标准预测函数。</span><span class="sxs-lookup"><span data-stu-id="d3c6e-227">You can use many of the standard prediction functions with linear regression models.</span></span> <span data-ttu-id="d3c6e-228">下面的示例演示如何向预测查询结果中添加说明性统计信息。</span><span class="sxs-lookup"><span data-stu-id="d3c6e-228">The following example illustrates how to add some descriptive statistics to the prediction query results.</span></span> <span data-ttu-id="d3c6e-229">您可以从这些结果发现此模型的均值的偏差非常大。</span><span class="sxs-lookup"><span data-stu-id="d3c6e-229">From these results, you can see that there is considerable deviation from the mean for this model.</span></span>  
  
```  
SELECT  
  ([LR_PredictIncome].[Yearly Income]) as [PredIncome],  
  (PredictStdev([LR_PredictIncome].[Yearly Income])) as [StDev1]  
From  
  [LR_PredictIncome]  
NATURAL PREDICTION JOIN  
(SELECT 20 AS [Age]) AS t  
```  
  
 <span data-ttu-id="d3c6e-230">示例结果：</span><span class="sxs-lookup"><span data-stu-id="d3c6e-230">Sample results:</span></span>  
  
|<span data-ttu-id="d3c6e-231">Yearly Income</span><span class="sxs-lookup"><span data-stu-id="d3c6e-231">Yearly Income</span></span>|<span data-ttu-id="d3c6e-232">StDev1</span><span class="sxs-lookup"><span data-stu-id="d3c6e-232">StDev1</span></span>|  
|-------------------|------------|  
|<span data-ttu-id="d3c6e-233">45227.302092176</span><span class="sxs-lookup"><span data-stu-id="d3c6e-233">45227.302092176</span></span>|<span data-ttu-id="d3c6e-234">31827.1726561396</span><span class="sxs-lookup"><span data-stu-id="d3c6e-234">31827.1726561396</span></span>|  
  
 [<span data-ttu-id="d3c6e-235">返回页首</span><span class="sxs-lookup"><span data-stu-id="d3c6e-235">Return to Top</span></span>](#bkmk_top)  
  
## <a name="list-of-prediction-functions"></a><span data-ttu-id="d3c6e-236">预测函数的列表</span><span class="sxs-lookup"><span data-stu-id="d3c6e-236">List of Prediction Functions</span></span>  
 <span data-ttu-id="d3c6e-237">所有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 算法均支持一组通用的函数。</span><span class="sxs-lookup"><span data-stu-id="d3c6e-237">All [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms support a common set of functions.</span></span> <span data-ttu-id="d3c6e-238">此外， [!INCLUDE[msCoName](../../includes/msconame-md.md)] 线性回归算法还额外支持下表中列出的函数。</span><span class="sxs-lookup"><span data-stu-id="d3c6e-238">However, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Linear Regression algorithm supports the additional functions listed in the following table.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d3c6e-239">预测函数</span><span class="sxs-lookup"><span data-stu-id="d3c6e-239">Prediction Function</span></span>|<span data-ttu-id="d3c6e-240">使用情况</span><span class="sxs-lookup"><span data-stu-id="d3c6e-240">Usage</span></span>|  
|[<span data-ttu-id="d3c6e-241">IsDescendant (DMX)</span><span class="sxs-lookup"><span data-stu-id="d3c6e-241">IsDescendant &#40;DMX&#41;</span></span>](/sql/dmx/isdescendant-dmx)|<span data-ttu-id="d3c6e-242">确定一个节点是否是模型中另一个节点的子节点。</span><span class="sxs-lookup"><span data-stu-id="d3c6e-242">Determines whether one node is a child of another node in the model.</span></span>|  
|[<span data-ttu-id="d3c6e-243">IsInNode (DMX)</span><span class="sxs-lookup"><span data-stu-id="d3c6e-243">IsInNode &#40;DMX&#41;</span></span>](/sql/dmx/isinnode-dmx)|<span data-ttu-id="d3c6e-244">指示指定的节点是否包含当前事例。</span><span class="sxs-lookup"><span data-stu-id="d3c6e-244">Indicates whether the specified node contains the current case.</span></span>|  
|[<span data-ttu-id="d3c6e-245">PredictHistogram (DMX)</span><span class="sxs-lookup"><span data-stu-id="d3c6e-245">PredictHistogram &#40;DMX&#41;</span></span>](/sql/dmx/predicthistogram-dmx)|<span data-ttu-id="d3c6e-246">返回指定列的一个预测值或一组值。</span><span class="sxs-lookup"><span data-stu-id="d3c6e-246">Returns a predicted value, or set of values, for a specified column.</span></span>|  
|[<span data-ttu-id="d3c6e-247">PredictNodeId (DMX)</span><span class="sxs-lookup"><span data-stu-id="d3c6e-247">PredictNodeId &#40;DMX&#41;</span></span>](/sql/dmx/predictnodeid-dmx)|<span data-ttu-id="d3c6e-248">返回每个事例的 Node_ID。</span><span class="sxs-lookup"><span data-stu-id="d3c6e-248">Returns the Node_ID for each case.</span></span>|  
|[<span data-ttu-id="d3c6e-249">PredictStdev (DMX)</span><span class="sxs-lookup"><span data-stu-id="d3c6e-249">PredictStdev &#40;DMX&#41;</span></span>](/sql/dmx/predictstdev-dmx)|<span data-ttu-id="d3c6e-250">返回预测值的标准偏差。</span><span class="sxs-lookup"><span data-stu-id="d3c6e-250">Returns standard deviation for the predicted value.</span></span>|  
|[<span data-ttu-id="d3c6e-251">PredictSupport (DMX)</span><span class="sxs-lookup"><span data-stu-id="d3c6e-251">PredictSupport &#40;DMX&#41;</span></span>](/sql/dmx/predictsupport-dmx)|<span data-ttu-id="d3c6e-252">返回指定状态的支持值。</span><span class="sxs-lookup"><span data-stu-id="d3c6e-252">Returns the support value for a specified state.</span></span>|  
|[<span data-ttu-id="d3c6e-253">PredictVariance (DMX)</span><span class="sxs-lookup"><span data-stu-id="d3c6e-253">PredictVariance &#40;DMX&#41;</span></span>](/sql/dmx/predictvariance-dmx)|<span data-ttu-id="d3c6e-254">返回指定列的方差。</span><span class="sxs-lookup"><span data-stu-id="d3c6e-254">Returns the variance of a specified column.</span></span>|  
  
 <span data-ttu-id="d3c6e-255">有关对所有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 算法都通用的函数列表，请参阅[数据挖掘算法（Analysis Services - 数据挖掘）](data-mining-algorithms-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="d3c6e-255">For a list of the functions that are common to all [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms, see [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md).</span></span> <span data-ttu-id="d3c6e-256">有关如何使用这些函数的详细信息，请参阅[数据挖掘扩展插件 (DMX) 函数引用](/sql/dmx/data-mining-extensions-dmx-function-reference)。</span><span class="sxs-lookup"><span data-stu-id="d3c6e-256">For more information about how to use these functions, see [Data Mining Extensions &#40;DMX&#41; Function Reference](/sql/dmx/data-mining-extensions-dmx-function-reference).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3c6e-257">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d3c6e-257">See Also</span></span>  
 <span data-ttu-id="d3c6e-258">[Microsoft 线性回归算法](microsoft-linear-regression-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="d3c6e-258">[Microsoft Linear Regression Algorithm](microsoft-linear-regression-algorithm.md) </span></span>  
 <span data-ttu-id="d3c6e-259">[数据挖掘查询](data-mining-queries.md) </span><span class="sxs-lookup"><span data-stu-id="d3c6e-259">[Data Mining Queries](data-mining-queries.md) </span></span>  
 <span data-ttu-id="d3c6e-260">[Microsoft 线性回归算法技术参考](microsoft-linear-regression-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="d3c6e-260">[Microsoft Linear Regression Algorithm Technical Reference](microsoft-linear-regression-algorithm-technical-reference.md) </span></span>  
 [<span data-ttu-id="d3c6e-261">线性回归模型的挖掘模型内容（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="d3c6e-261">Mining Model Content for Linear Regression Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-linear-regression-models-analysis-services-data-mining.md)  
  
  
