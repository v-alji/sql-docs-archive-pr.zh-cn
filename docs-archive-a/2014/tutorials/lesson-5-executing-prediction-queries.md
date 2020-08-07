---
title: 第5课：执行预测查询 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0037bd2f-aa2d-464b-bf86-b0210f0438b1
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a5f4d6dd79f62541e207df688349f694680e2421
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690920"
---
# <a name="lesson-5-executing-prediction-queries"></a><span data-ttu-id="ec57f-102">第 5 课：执行预测查询</span><span class="sxs-lookup"><span data-stu-id="ec57f-102">Lesson 5: Executing Prediction Queries</span></span>
  <span data-ttu-id="ec57f-103">在本课中，您将使用 SELECT 语句的[SELECT FROM \<model> 预测联接 (DMX) ](/sql/dmx/select-from-model-cases-dmx)窗体，根据您在[第2课：向关联挖掘结构中添加挖掘模型](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md)中创建的决策树模型创建两种不同类型的预测。</span><span class="sxs-lookup"><span data-stu-id="ec57f-103">In this lesson, you will use the [SELECT FROM \<model> PREDICTION JOIN (DMX)](/sql/dmx/select-from-model-cases-dmx) form of the SELECT statement to create two different types of predictions based on the decision tree model you created in [Lesson 2: Adding Mining Models to the Association Mining Structure](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md).</span></span> <span data-ttu-id="ec57f-104">这些预测类型定义如下。</span><span class="sxs-lookup"><span data-stu-id="ec57f-104">These prediction types are defined below.</span></span>  
  
 <span data-ttu-id="ec57f-105">单独查询</span><span class="sxs-lookup"><span data-stu-id="ec57f-105">Singleton Query</span></span>  
 <span data-ttu-id="ec57f-106">使用单独查询可以在进行预测时提供即席值。</span><span class="sxs-lookup"><span data-stu-id="ec57f-106">Use a singleton query to provide ad hoc values when making predictions.</span></span> <span data-ttu-id="ec57f-107">例如，您可以通过将输入（如客户的上下班路程、区号或子女数）传递给查询来确定一个客户是否会购买自行车。</span><span class="sxs-lookup"><span data-stu-id="ec57f-107">For example, you can determine whether a single customer is likely to be a bike buyer, by passing inputs to the query such as the commute distance, the area code, or the number of children of the customer.</span></span> <span data-ttu-id="ec57f-108">单独查询可基于这些输入，返回指示客户购买自行车的可能性大小的值。</span><span class="sxs-lookup"><span data-stu-id="ec57f-108">The singleton query returns a value that indicates how likely the person is to purchase a bicycle based on those inputs.</span></span>  
  
 <span data-ttu-id="ec57f-109">批查询</span><span class="sxs-lookup"><span data-stu-id="ec57f-109">Batch Query</span></span>  
 <span data-ttu-id="ec57f-110">使用批查询可确定潜在客户表中的哪个人可能购买自行车。</span><span class="sxs-lookup"><span data-stu-id="ec57f-110">Use a batch query to determine who in a table of potential customers is likely to purchase a bicycle.</span></span> <span data-ttu-id="ec57f-111">例如，如果市场部提供客户及客户属性的列表，那么您可以使用批预测确定该表中的哪个人可能购买自行车。</span><span class="sxs-lookup"><span data-stu-id="ec57f-111">For example, if your marketing department provides you with a list of customers and customer attributes, then you can use a batch prediction to determine who from the table is likely to purchase a bicycle.</span></span>  
  
 <span data-ttu-id="ec57f-112">Select 语句的[SELECT FROM \<model> 预测联接 (DMX) ](/sql/dmx/select-from-model-cases-dmx)形式包含三个部分：</span><span class="sxs-lookup"><span data-stu-id="ec57f-112">The [SELECT FROM \<model> PREDICTION JOIN (DMX)](/sql/dmx/select-from-model-cases-dmx) form of the SELECT statement contains three parts:</span></span>  
  
-   <span data-ttu-id="ec57f-113">结果中返回的挖掘模型列和预测函数列表。</span><span class="sxs-lookup"><span data-stu-id="ec57f-113">A list of the mining model columns and prediction functions that are returned in the results.</span></span> <span data-ttu-id="ec57f-114">结果还可以包含源数据中的输入列。</span><span class="sxs-lookup"><span data-stu-id="ec57f-114">The results can also contain input columns from the source data.</span></span>  
  
-   <span data-ttu-id="ec57f-115">定义要用于创建预测的数据的源查询。</span><span class="sxs-lookup"><span data-stu-id="ec57f-115">The source query defining the data that is being used to create a prediction.</span></span> <span data-ttu-id="ec57f-116">例如，在批查询中，此部分可能是客户列表。</span><span class="sxs-lookup"><span data-stu-id="ec57f-116">For example, in a batch query this could be a list of customers.</span></span>  
  
-   <span data-ttu-id="ec57f-117">挖掘模型列和源数据之间的映射。</span><span class="sxs-lookup"><span data-stu-id="ec57f-117">A mapping between the mining model columns and the source data.</span></span> <span data-ttu-id="ec57f-118">如果这些名称匹配，则可以使用 NATURAL 语法并且不考虑列映射。</span><span class="sxs-lookup"><span data-stu-id="ec57f-118">If these names match, then you can use NATURAL syntax and leave out the column mappings.</span></span>  
  
 <span data-ttu-id="ec57f-119">可以使用预测函数进一步增强查询功能。</span><span class="sxs-lookup"><span data-stu-id="ec57f-119">You can further enhance the query by using prediction functions.</span></span> <span data-ttu-id="ec57f-120">预测函数提供其他信息（例如预测出现的概率），并支持在定型数据集中进行预测。</span><span class="sxs-lookup"><span data-stu-id="ec57f-120">Prediction functions provide additional information, such as the probability of a prediction occurring, and provide support for the prediction in the training dataset.</span></span> <span data-ttu-id="ec57f-121">有关预测函数的详细信息，请参阅[函数 &#40;DMX&#41;](/sql/dmx/functions-dmx)。</span><span class="sxs-lookup"><span data-stu-id="ec57f-121">For more information about prediction functions, see [Functions &#40;DMX&#41;](/sql/dmx/functions-dmx).</span></span>  
  
 <span data-ttu-id="ec57f-122">本教程中的预测基于 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 示例数据库中的 ProspectiveBuyer 表。</span><span class="sxs-lookup"><span data-stu-id="ec57f-122">The predictions in this tutorial are based on the ProspectiveBuyer table in the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] sample database.</span></span> <span data-ttu-id="ec57f-123">ProspectiveBuyer 表包含潜在客户及其关联特征的列表。</span><span class="sxs-lookup"><span data-stu-id="ec57f-123">The ProspectiveBuyer table contains a list of potential customers and their associated characteristics.</span></span> <span data-ttu-id="ec57f-124">此表中的客户与用来创建决策树挖掘模型的客户无关。</span><span class="sxs-lookup"><span data-stu-id="ec57f-124">The customers in this table are independent of the customers that were used to create the decision tree mining model.</span></span>  
  
 <span data-ttu-id="ec57f-125">您还可以在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中使用预测查询生成器创建预测。</span><span class="sxs-lookup"><span data-stu-id="ec57f-125">You can also create predictions by using the prediction query builder in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="ec57f-126">课程任务</span><span class="sxs-lookup"><span data-stu-id="ec57f-126">Lesson Tasks</span></span>  
 <span data-ttu-id="ec57f-127">您将在本课中执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="ec57f-127">You will perform the following tasks in this lesson:</span></span>  
  
-   <span data-ttu-id="ec57f-128">创建一个单独查询，以确定特定客户是否可能购买自行车</span><span class="sxs-lookup"><span data-stu-id="ec57f-128">Create a singleton query to determine whether a specific customer is likely to purchase a bicycle.</span></span>  
  
-   <span data-ttu-id="ec57f-129">创建一个批查询，以确定客户表中列出客户中哪些可能会购买自行车。</span><span class="sxs-lookup"><span data-stu-id="ec57f-129">Create a batch query to determine which customers, listed in a table of customers, are likely to purchase a bicycle.</span></span>  
  
## <a name="singleton-query"></a><span data-ttu-id="ec57f-130">单独查询</span><span class="sxs-lookup"><span data-stu-id="ec57f-130">Singleton Query</span></span>  
 <span data-ttu-id="ec57f-131">第一步是在单独预测查询中使用[SELECT FROM &#60;模型&#62; 预测联接 &#40;DMX&#41;](/sql/dmx/select-from-model-cases-dmx) 。</span><span class="sxs-lookup"><span data-stu-id="ec57f-131">The first step is to use the [SELECT FROM &#60;model&#62; PREDICTION JOIN &#40;DMX&#41;](/sql/dmx/select-from-model-cases-dmx) in a singleton prediction query.</span></span> <span data-ttu-id="ec57f-132">下面是单独语句的一般示例：</span><span class="sxs-lookup"><span data-stu-id="ec57f-132">The following is a generic example of the singleton statement:</span></span>  
  
```  
SELECT <select list> FROM [<mining model name>]   
NATURAL PREDICTION JOIN  
(SELECT '<value>' AS [<column>], ...)  
AS [<input alias>]  
```  
  
 <span data-ttu-id="ec57f-133">代码的第一行定义查询应返回的挖掘模型中的列，并指定用于生成预测的挖掘模型的名称：</span><span class="sxs-lookup"><span data-stu-id="ec57f-133">The first line of the code defines the columns from the mining model that the query should return, and specifies the mining model that is used to generate the prediction:</span></span>  
  
```  
SELECT <select list> FROM [<mining model name>]   
```  
  
 <span data-ttu-id="ec57f-134">代码接下来的各行定义用于创建预测的客户的特征：</span><span class="sxs-lookup"><span data-stu-id="ec57f-134">The next lines of the code define the characteristics of the customer that you use to create a prediction:</span></span>  
  
```  
NATURAL PREDICTION JOIN  
(SELECT '<value>' AS [<column>], ...)  
AS [<input alias>]  
ORDER BY <expression>  
```  
  
 <span data-ttu-id="ec57f-135">如果指定 NATURAL PREDICTION JOIN，则服务器会基于列名，尝试将模型的每列与输入的列进行匹配。</span><span class="sxs-lookup"><span data-stu-id="ec57f-135">If you specify NATURAL PREDICTION JOIN, the server matches each column from the model to a column from the input, based on column names.</span></span> <span data-ttu-id="ec57f-136">如果列名不匹配，则忽略这些列。</span><span class="sxs-lookup"><span data-stu-id="ec57f-136">If column names do not match, the columns are ignored.</span></span>  
  
#### <a name="to-create-a-singleton-prediction-query"></a><span data-ttu-id="ec57f-137">创建单独预测查询</span><span class="sxs-lookup"><span data-stu-id="ec57f-137">To create a singleton prediction query</span></span>  
  
1.  <span data-ttu-id="ec57f-138">在**对象资源管理器**中，右键单击实例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，指向 "**新建查询**"，然后单击 " **DMX**"。</span><span class="sxs-lookup"><span data-stu-id="ec57f-138">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="ec57f-139">将打开查询编辑器，其中包含一个新的空白查询。</span><span class="sxs-lookup"><span data-stu-id="ec57f-139">Query Editor opens and contains a new, blank query.</span></span>  
  
2.  <span data-ttu-id="ec57f-140">将单独语句的一般示例复制到空白查询中。</span><span class="sxs-lookup"><span data-stu-id="ec57f-140">Copy the generic example of the singleton statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="ec57f-141">将</span><span class="sxs-lookup"><span data-stu-id="ec57f-141">Replace the following:</span></span>  
  
    ```  
    <select list>   
    ```  
  
     <span data-ttu-id="ec57f-142">替换为：</span><span class="sxs-lookup"><span data-stu-id="ec57f-142">with:</span></span>  
  
    ```  
    [Bike Buyer] AS Buyer, PredictHistogram([Bike Buyer]) AS Statistics  
    ```  
  
     <span data-ttu-id="ec57f-143">AS 语句用于查询返回的别名列。</span><span class="sxs-lookup"><span data-stu-id="ec57f-143">The AS statement is used to alias columns returned by the query.</span></span> <span data-ttu-id="ec57f-144">[PredictHistogram](/sql/dmx/predicthistogram-dmx)函数返回有关预测的统计信息，包括概率和支持。</span><span class="sxs-lookup"><span data-stu-id="ec57f-144">The [PredictHistogram](/sql/dmx/predicthistogram-dmx) function returns statistics about the prediction, including the probability and the support.</span></span> <span data-ttu-id="ec57f-145">有关可在预测语句中使用的函数的详细信息，请参阅[函数 &#40;DMX&#41;](/sql/dmx/functions-dmx)。</span><span class="sxs-lookup"><span data-stu-id="ec57f-145">For more information about the functions that can be used in a prediction statement, see [Functions &#40;DMX&#41;](/sql/dmx/functions-dmx).</span></span>  
  
4.  <span data-ttu-id="ec57f-146">将</span><span class="sxs-lookup"><span data-stu-id="ec57f-146">Replace the following:</span></span>  
  
    ```  
    [<mining model>]   
    ```  
  
     <span data-ttu-id="ec57f-147">替换为：</span><span class="sxs-lookup"><span data-stu-id="ec57f-147">with:</span></span>  
  
    ```  
    [Decision Tree]  
    ```  
  
5.  <span data-ttu-id="ec57f-148">将</span><span class="sxs-lookup"><span data-stu-id="ec57f-148">Replace the following:</span></span>  
  
    ```  
    (SELECT '<value>' AS [<column name>], ...)  AS t  
    ```  
  
     <span data-ttu-id="ec57f-149">替换为：</span><span class="sxs-lookup"><span data-stu-id="ec57f-149">with:</span></span>  
  
    ```  
    (SELECT 35 AS [Age],  
      '5-10 Miles' AS [Commute Distance],  
      '1' AS [House Owner Flag],  
      2 AS [Number Cars Owned],  
      2 AS [Total Children]) AS t  
    ```  
  
     <span data-ttu-id="ec57f-150">现在，完整的语句应该如下所示：</span><span class="sxs-lookup"><span data-stu-id="ec57f-150">The complete statement should now be as follows:</span></span>  
  
    ```  
    SELECT  
       [Bike Buyer] AS Buyer,  
       PredictHistogram([Bike Buyer]) AS Statistics  
    FROM  
       [Decision Tree]  
    NATURAL PREDICTION JOIN  
    (SELECT 35 AS [Age],  
       '5-10 Miles' AS [Commute Distance],  
       '1' AS [House Owner Flag],  
       2 AS [Number Cars Owned],  
       2 AS [Total Children]) AS t  
    ```  
  
6.  <span data-ttu-id="ec57f-151">在 "**文件**" 菜单上，单击 "**将 DMXQuery1 另存为**"。</span><span class="sxs-lookup"><span data-stu-id="ec57f-151">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
7.  <span data-ttu-id="ec57f-152">在 "**另存为**" 对话框中，浏览到相应的文件夹，并将该文件命名为 `Singleton_Query.dmx` 。</span><span class="sxs-lookup"><span data-stu-id="ec57f-152">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Singleton_Query.dmx`.</span></span>  
  
8.  <span data-ttu-id="ec57f-153">在工具栏上，单击 "**执行**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="ec57f-153">On the toolbar, click the **Execute** button.</span></span>  
  
     <span data-ttu-id="ec57f-154">查询将返回有关具有指定特征的客户是否会购买自行车的预测，以及有关此预测的统计信息。</span><span class="sxs-lookup"><span data-stu-id="ec57f-154">The query returns a prediction about whether a customer with the specified characteristics will purchase a bicycle, as well as statistics about that prediction.</span></span>  
  
## <a name="batch-query"></a><span data-ttu-id="ec57f-155">批查询</span><span class="sxs-lookup"><span data-stu-id="ec57f-155">Batch Query</span></span>  
 <span data-ttu-id="ec57f-156">下一步是使用批预测查询中[&#60;模型&#62; 预测联接 &#40;DMX&#41;](/sql/dmx/select-from-model-cases-dmx) 。</span><span class="sxs-lookup"><span data-stu-id="ec57f-156">The next step is to use the [SELECT FROM &#60;model&#62; PREDICTION JOIN &#40;DMX&#41;](/sql/dmx/select-from-model-cases-dmx) in a batch prediction query.</span></span> <span data-ttu-id="ec57f-157">下面是批语句的一般示例：</span><span class="sxs-lookup"><span data-stu-id="ec57f-157">The following is a generic example of a batch statement:</span></span>  
  
```  
SELECT TOP <number> <select list>   
FROM [<mining model name>]  
PREDICTION JOIN  
OPENQUERY([<datasource>],'<SELECT statement>')  
  AS [<input alias>]  
ON <on clause, mapping,>  
WHERE <where clause, boolean expression,>  
ORDER BY <expression>  
```  
  
 <span data-ttu-id="ec57f-158">与在单独查询中相同，代码的前两行定义查询返回的挖掘模型的列，以及用于生成预测的挖掘模型的名称。</span><span class="sxs-lookup"><span data-stu-id="ec57f-158">As in the singleton query, the first two lines of the code define the columns from mining model that the query returns, as well as the name of the mining model that is used to generate the prediction.</span></span> <span data-ttu-id="ec57f-159">TOP \<number> 语句指定查询将只返回指定的数字或结果 \<number> 。</span><span class="sxs-lookup"><span data-stu-id="ec57f-159">The TOP \<number> statement specifies that the query will only return the number or the results specified by \<number>.</span></span>  
  
 <span data-ttu-id="ec57f-160">代码的接下来各行定义预测所基于的源数据：</span><span class="sxs-lookup"><span data-stu-id="ec57f-160">The next lines of the code define the source data that the predictions are based on:</span></span>  
  
```  
OPENQUERY([<datasource>],'<SELECT statement>')  
  AS [<input alias>]  
```  
  
 <span data-ttu-id="ec57f-161">您可以使用多种方法检索源数据，但是在本教程中，您将使用 OPENQUERY。</span><span class="sxs-lookup"><span data-stu-id="ec57f-161">You have several options for the method of retrieving the source data, but in this tutorial, you will use OPENQUERY.</span></span> <span data-ttu-id="ec57f-162">有关可用选项的详细信息，请参阅[&#60;源数据查询&#62;](/sql/dmx/source-data-query)。</span><span class="sxs-lookup"><span data-stu-id="ec57f-162">For more information about the options available, see [&#60;source data query&#62;](/sql/dmx/source-data-query).</span></span>  
  
 <span data-ttu-id="ec57f-163">下一行定义挖掘模型中的源列和源数据中的列之间的映射：</span><span class="sxs-lookup"><span data-stu-id="ec57f-163">The next line defines the mapping between the source columns in the mining model and the columns in the source data:</span></span>  
  
```  
ON <column mappings>  
```  
  
 <span data-ttu-id="ec57f-164">WHERE 子句筛选预测查询返回的结果：</span><span class="sxs-lookup"><span data-stu-id="ec57f-164">The WHERE clause filters the results returned by the prediction query:</span></span>  
  
```  
WHERE <where clause, boolean expression,>  
```  
  
 <span data-ttu-id="ec57f-165">代码的最后一行和可选行指定排列结果所依据的列：</span><span class="sxs-lookup"><span data-stu-id="ec57f-165">The last and optional line of the code specifies the column that the results will be ordered by:</span></span>  
  
```  
ORDER BY <expression> [DESC|ASC]  
```  
  
 <span data-ttu-id="ec57f-166">使用 ORDER BY 结合 TOP \<number> 语句来筛选返回的结果。</span><span class="sxs-lookup"><span data-stu-id="ec57f-166">Use ORDER BY in combination with the TOP \<number> statement, to filter the results that are returned.</span></span> <span data-ttu-id="ec57f-167">例如，在此预测中，您将返回前十位自行车购买者，他们按照正确的预测概率排列。</span><span class="sxs-lookup"><span data-stu-id="ec57f-167">For example, in this prediction you will return the top ten bike buyers, ordered by the probability of the prediction being correct.</span></span> <span data-ttu-id="ec57f-168">您可以使用 [DESC|ASC] 语法控制结果的显示顺序。</span><span class="sxs-lookup"><span data-stu-id="ec57f-168">You can use [DESC|ASC] syntax to control the order in which the results are displayed.</span></span>  
  
#### <a name="to-create-a-batch-prediction-query"></a><span data-ttu-id="ec57f-169">创建批预测查询</span><span class="sxs-lookup"><span data-stu-id="ec57f-169">To create a batch prediction query</span></span>  
  
1.  <span data-ttu-id="ec57f-170">在**对象资源管理器**中，右键单击实例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，指向 "**新建查询**"，然后单击 " **DMX**"。</span><span class="sxs-lookup"><span data-stu-id="ec57f-170">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="ec57f-171">将打开查询编辑器，其中包含一个新的空白查询。</span><span class="sxs-lookup"><span data-stu-id="ec57f-171">Query Editor opens and contains a new, blank query.</span></span>  
  
2.  <span data-ttu-id="ec57f-172">将批语句的一般示例复制到空白查询中。</span><span class="sxs-lookup"><span data-stu-id="ec57f-172">Copy the generic example of the batch statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="ec57f-173">将</span><span class="sxs-lookup"><span data-stu-id="ec57f-173">Replace the following:</span></span>  
  
    ```  
    <select list>   
    ```  
  
     <span data-ttu-id="ec57f-174">替换为：</span><span class="sxs-lookup"><span data-stu-id="ec57f-174">with:</span></span>  
  
    ```  
    SELECT  
      TOP 10  
      t.[LastName],  
      t.[FirstName],  
      [Decision Tree].[Bike Buyer],  
      PredictProbability([Bike Buyer])  
    ```  
  
     <span data-ttu-id="ec57f-175">TOP 10 子句指定查询只返回前十个结果。</span><span class="sxs-lookup"><span data-stu-id="ec57f-175">The TOP 10 clause specifies that only the top ten results will be returned by the query.</span></span> <span data-ttu-id="ec57f-176">此查询中的 ORDER BY 语句按照正确的预测概率排列结果，因此只返回前十个最可能的结果。</span><span class="sxs-lookup"><span data-stu-id="ec57f-176">The ORDER BY statement in this query orders the results by the probability of the prediction being correct, so only the ten most likely results will be returned.</span></span>  
  
4.  <span data-ttu-id="ec57f-177">将以下占位符</span><span class="sxs-lookup"><span data-stu-id="ec57f-177">Replace the following placeholder:</span></span>  
  
    ```  
    [<mining model>]   
    ```  
  
     <span data-ttu-id="ec57f-178">替换为模型的名称：</span><span class="sxs-lookup"><span data-stu-id="ec57f-178">With the name of the model:</span></span>  
  
    ```  
    [Decision Tree]  
    ```  
  
5.  <span data-ttu-id="ec57f-179">将以下一般 OPENQUERY 语句</span><span class="sxs-lookup"><span data-stu-id="ec57f-179">Replace the following generic OPENQUERY statement:</span></span>  
  
    ```  
    OPENQUERY([<datasource>],'<SELECT statement>')  
    ```  
  
     <span data-ttu-id="ec57f-180">替换为引用当前 Adventureworks 数据仓库的语句，例如：</span><span class="sxs-lookup"><span data-stu-id="ec57f-180">With a statement that references the current Adventureworks data warehouse, such as:</span></span>  
  
    ```  
    OPENQUERY([Adventure Works DW 2014],  
      'SELECT  
        [LastName],  
        [FirstName],  
        [MaritalStatus],  
        [Gender],  
        [YearlyIncome],  
        [TotalChildren],  
        [NumberChildrenAtHome],  
        [Education],  
        [Occupation],  
        [HouseOwnerFlag],  
        [NumberCarsOwned]  
      FROM  
        [dbo].[ProspectiveBuyer]  
      ') AS t  
    ```  
  
6.  <span data-ttu-id="ec57f-181">将以下一般语法</span><span class="sxs-lookup"><span data-stu-id="ec57f-181">Replace the following generic syntax:</span></span>  
  
    ```  
    <ON clause, mapping,>   
    WHERE <where clause, boolean expression,>  
    ORDER BY <expression>  
    ```  
  
     <span data-ttu-id="ec57f-182">替换为此模型和输入数据集所需的列映射：</span><span class="sxs-lookup"><span data-stu-id="ec57f-182">With the column mappings needed for this model and input data set:</span></span>  
  
    ```  
    [Decision Tree].[Marital Status] = t.[MaritalStatus] AND  
      [Decision Tree].[Gender] = t.[Gender] AND  
      [Decision Tree].[Yearly Income] = t.[YearlyIncome] AND  
      [Decision Tree].[Total Children] = t.[TotalChildren] AND  
      [Decision Tree].[Number Children At Home] = t.[NumberChildrenAtHome] AND  
      [Decision Tree].[Education] = t.[Education] AND  
      [Decision Tree].[Occupation] = t.[Occupation] AND  
      [Decision Tree].[House Owner Flag] = t.[HouseOwnerFlag] AND  
      [Decision Tree].[Number Cars Owned] = t.[NumberCarsOwned]  
    WHERE [Decision Tree].[Bike Buyer] =1  
    ORDER BY PredictProbability([Bike Buyer]) DESC  
    ```  
  
     <span data-ttu-id="ec57f-183">指定 `DESC` 以便首先列出概率最大的结果。</span><span class="sxs-lookup"><span data-stu-id="ec57f-183">Specify `DESC` in order to list the results with the highest probability first.</span></span>  
  
     <span data-ttu-id="ec57f-184">现在，完整的语句应该如下所示：</span><span class="sxs-lookup"><span data-stu-id="ec57f-184">The complete statement should now be as follows:</span></span>  
  
    ```  
    SELECT  
      TOP 10  
      t.[LastName],  
      t.[FirstName],  
      [Decision Tree].[Bike Buyer],  
      PredictProbability([Bike Buyer])  
    FROM  
      [Decision Tree]  
    PREDICTION JOIN  
      OPENQUERY([Adventure Works DW 2014],  
        'SELECT  
          [LastName],  
          [FirstName],  
          [MaritalStatus],  
          [Gender],  
          [YearlyIncome],  
          [TotalChildren],  
          [NumberChildrenAtHome],  
          [Education],  
          [Occupation],  
          [HouseOwnerFlag],  
          [NumberCarsOwned]  
        FROM  
          [dbo].[ProspectiveBuyer]  
        ') AS t  
    ON  
      [Decision Tree].[Marital Status] = t.[MaritalStatus] AND  
      [Decision Tree].[Gender] = t.[Gender] AND  
      [Decision Tree].[Yearly Income] = t.[YearlyIncome] AND  
      [Decision Tree].[Total Children] = t.[TotalChildren] AND  
      [Decision Tree].[Number Children At Home] = t.[NumberChildrenAtHome] AND  
      [Decision Tree].[Education] = t.[Education] AND  
      [Decision Tree].[Occupation] = t.[Occupation] AND  
      [Decision Tree].[House Owner Flag] = t.[HouseOwnerFlag] AND  
      [Decision Tree].[Number Cars Owned] = t.[NumberCarsOwned]  
    WHERE [Decision Tree].[Bike Buyer] =1  
    ORDER BY PredictProbability([Bike Buyer]) DESC  
    ```  
  
7.  <span data-ttu-id="ec57f-185">在 "**文件**" 菜单上，单击 "**将 DMXQuery1 另存为**"。</span><span class="sxs-lookup"><span data-stu-id="ec57f-185">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
8.  <span data-ttu-id="ec57f-186">在 "**另存为**" 对话框中，浏览到相应的文件夹，并将该文件命名为 `Batch_Prediction.dmx` 。</span><span class="sxs-lookup"><span data-stu-id="ec57f-186">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Batch_Prediction.dmx`.</span></span>  
  
9. <span data-ttu-id="ec57f-187">在工具栏上，单击 "**执行**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="ec57f-187">On the toolbar, click the **Execute** button.</span></span>  
  
     <span data-ttu-id="ec57f-188">查询将返回一个表，其中包含客户名称、每位客户是否将购买自行车的预测，以及该预测的概率。</span><span class="sxs-lookup"><span data-stu-id="ec57f-188">The query returns a table containing customer names, a prediction of whether each customer will purchase a bicycle, and the probability of the prediction.</span></span>  
  
 <span data-ttu-id="ec57f-189">这是自行车购买者教程中的最后一个步骤。</span><span class="sxs-lookup"><span data-stu-id="ec57f-189">This is the last step in the Bike Buyer tutorial.</span></span> <span data-ttu-id="ec57f-190">现在，您拥有一个挖掘模型集，可以使用它们来浏览客户之间的相似之处并预测潜在客户是否将购买自行车。</span><span class="sxs-lookup"><span data-stu-id="ec57f-190">You now have a set of mining models that you can use to explore similarities between you customers and predict whether potential customers will purchase a bicycle.</span></span>  
  
 <span data-ttu-id="ec57f-191">若要了解如何在市场篮方案中使用 DMX，请参阅[市场篮 DMX 教程](../../2014/tutorials/market-basket-dmx-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="ec57f-191">To learn how to use DMX in a Market Basket scenario, see [Market Basket DMX Tutorial](../../2014/tutorials/market-basket-dmx-tutorial.md).</span></span>  
  
  
