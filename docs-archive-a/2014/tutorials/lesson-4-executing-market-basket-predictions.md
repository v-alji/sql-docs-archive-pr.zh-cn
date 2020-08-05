---
title: 第4课：执行市场篮预测 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b3238f1b-ea04-4253-ade2-838a806b62fe
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 3b49fc242eb8b2242269c5af33cc094937bbe0de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581068"
---
# <a name="lesson-4-executing-market-basket-predictions"></a><span data-ttu-id="c9dcb-102">第 4 课：执行市场篮预测</span><span class="sxs-lookup"><span data-stu-id="c9dcb-102">Lesson 4: Executing Market Basket Predictions</span></span>
  <span data-ttu-id="c9dcb-103">在本课中，您将使用 DMX `SELECT` 语句根据您在[第2课：向市场篮挖掘结构中添加挖掘模型](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md)中创建的关联模型创建预测。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-103">In this lesson, you will use the DMX `SELECT` statement to create predictions based on the association models you created in [Lesson 2: Adding Mining Models to the Market Basket Mining Structure](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md).</span></span> <span data-ttu-id="c9dcb-104">使用 DMX `SELECT` 语句并添加一个 `PREDICTION JOIN` 子句可创建一个预测查询。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-104">A prediction query is created by using the DMX `SELECT` statement and adding a `PREDICTION JOIN` clause.</span></span> <span data-ttu-id="c9dcb-105">有关预测联接的语法的详细信息，请参阅[&#60;模型中选择&#62; 预测联接 &#40;DMX&#41;](/sql/dmx/select-from-model-cases-dmx)。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-105">For more information about the syntax of a prediction join, see [SELECT FROM &#60;model&#62; PREDICTION JOIN &#40;DMX&#41;](/sql/dmx/select-from-model-cases-dmx).</span></span>  
  
 <span data-ttu-id="c9dcb-106">语句的**SELECT FROM \<model> 预测联接**窗体 `SELECT` 包含三个部分：</span><span class="sxs-lookup"><span data-stu-id="c9dcb-106">The **SELECT FROM \<model> PREDICTION JOIN** form of the `SELECT` statement contains three parts:</span></span>  
  
-   <span data-ttu-id="c9dcb-107">结果集中返回的挖掘模型列和预测函数的列表。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-107">A list of the mining model columns and prediction functions that are returned in the result set.</span></span> <span data-ttu-id="c9dcb-108">此列表还可以包含源数据中的输入列。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-108">This list can also contain input columns from the source data.</span></span>  
  
-   <span data-ttu-id="c9dcb-109">定义用于创建预测的数据的源查询。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-109">A source query that defines the data that is being used to create a prediction.</span></span> <span data-ttu-id="c9dcb-110">例如，如果您正批量创建多个预测，则源查询可以检索客户列表。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-110">For example, if you are creating many predictions in a batch, the source query could retrieve a list of customers.</span></span>  
  
-   <span data-ttu-id="c9dcb-111">挖掘模型列和源数据之间的映射。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-111">A mapping between the mining model columns and the source data.</span></span> <span data-ttu-id="c9dcb-112">如果列名称匹配，则可以使用 `NATURAL PREDICTION JOIN` 语法并忽略列映射。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-112">If the columns names match, you can use the `NATURAL PREDICTION JOIN` syntax and omit the column mappings.</span></span>  
  
 <span data-ttu-id="c9dcb-113">使用预测函数可增强查询。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-113">You can enhance the query by using prediction functions.</span></span> <span data-ttu-id="c9dcb-114">预测功能提供其他信息，例如，预测出现的概率或对定性数据集中预测的支持。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-114">Prediction functions provide additional information, such as the probability of a prediction occurring, or the support for a prediction in the training dataset.</span></span> <span data-ttu-id="c9dcb-115">有关预测函数的详细信息，请参阅[函数 &#40;DMX&#41;](/sql/dmx/functions-dmx)。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-115">For more information about prediction functions, see [Functions &#40;DMX&#41;](/sql/dmx/functions-dmx).</span></span>  
  
 <span data-ttu-id="c9dcb-116">您还可以使用 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中的预测查询生成器创建预测查询。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-116">You can also use the prediction query builder in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to create prediction queries.</span></span>  
  
## <a name="singleton-prediction-join-statement"></a><span data-ttu-id="c9dcb-117">单独 PREDICTION JOIN 语句</span><span class="sxs-lookup"><span data-stu-id="c9dcb-117">Singleton PREDICTION JOIN Statement</span></span>  
 <span data-ttu-id="c9dcb-118">第一步是通过使用**SELECT FROM \<model> 预测联接**语法并提供一组值作为输入来创建单独查询。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-118">The first step is to create a singleton query, by using the **SELECT FROM \<model> PREDICTION JOIN** syntax and supplying a single set of values as input.</span></span> <span data-ttu-id="c9dcb-119">下面是单独语句的一般示例：</span><span class="sxs-lookup"><span data-stu-id="c9dcb-119">The following is a generic example of the singleton statement:</span></span>  
  
```  
SELECT <select list>  
    FROM [<mining model>]   
[NATURAL] PREDICTION JOIN  
(SELECT '<value>' AS [<column>],   
    (SELECT 'value' AS [<nested column>] UNION  
        SELECT 'value' AS [<nested column>] ...)   
    AS [<nested table>])  
AS [<input alias>]  
```  
  
 <span data-ttu-id="c9dcb-120">代码的第一行定义查询返回的挖掘模型中的列，并指定用于生成预测的挖掘模型的名称：</span><span class="sxs-lookup"><span data-stu-id="c9dcb-120">The first line of the code defines the columns from the mining model that the query returns, and specifies the name of the mining model used to generate the prediction:</span></span>  
  
```  
SELECT <select list> FROM [<mining model>]   
```  
  
 <span data-ttu-id="c9dcb-121">代码的下一行指示要执行的操作。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-121">The next line of the code indicates the operation to perform.</span></span> <span data-ttu-id="c9dcb-122">因为要指定每个列的值并准确键入列名称以便与模型匹配，所以可以使用 `NATURAL PREDICTION JOIN` 语法。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-122">Because you will specify values for each of the columns and type the column names exactly so as to match the model, you can use the `NATURAL PREDICTION JOIN` syntax.</span></span> <span data-ttu-id="c9dcb-123">但是，如果列名不同，您将必须通过添加 `ON` 子句来指定模型中的列与新数据中的列之间的映射。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-123">However, if the column names were different, you would have to specify mappings between the columns in the model and the columns in the new data by adding an `ON` clause.</span></span>  
  
```  
[NATURAL] PREDICTION JOIN  
```  
  
 <span data-ttu-id="c9dcb-124">代码的以下各行定义购物车中将用于预测客户将添加的其他产品的产品：</span><span class="sxs-lookup"><span data-stu-id="c9dcb-124">The next lines of the code define the products in the shopping cart that will be used to predict additional products that a customer will add:</span></span>  
  
```  
(SELECT '<value>' AS [<column>],   
    (SELECT 'value' AS [<nested column>] UNION  
        SELECT 'value' AS [<nested column>] ...)   
    AS [<nested table>])  
```  
  
## <a name="lesson-tasks"></a><span data-ttu-id="c9dcb-125">课程任务</span><span class="sxs-lookup"><span data-stu-id="c9dcb-125">Lesson Tasks</span></span>  
 <span data-ttu-id="c9dcb-126">您将在本课中执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="c9dcb-126">You will perform the following tasks in this lesson:</span></span>  
  
-   <span data-ttu-id="c9dcb-127">创建一个查询，根据客户购物车中现有的物品预测客户可能要购买的其他产品。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-127">Create a query that predicts what other items a customer will likely purchase, based on items already existing in their shopping cart.</span></span> <span data-ttu-id="c9dcb-128">您将使用具有默认*MINIMUM_PROBABILITY*的挖掘模型创建此查询。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-128">You will create this query by using the mining model with the default *MINIMUM_PROBABILITY*.</span></span>  
  
-   <span data-ttu-id="c9dcb-129">根据客户购物车中的已有项创建一个查询，预测客户可能购买的其他项。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-129">Create a query that predicts what other items a customer will likely purchase based on items already existing in their shopping cart.</span></span> <span data-ttu-id="c9dcb-130">此查询基于一个不同的模型，在该模型中， *MINIMUM_PROBABILITY*已设置为0.01。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-130">This query is based on a different model, in which *MINIMUM_PROBABILITY* has been set to 0.01.</span></span> <span data-ttu-id="c9dcb-131">由于关联模型中*MINIMUM_PROBABILITY*的默认值为0.3，因此，对此模型的查询应返回比默认模型上的查询更多的可能项。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-131">Because the default value for *MINIMUM_PROBABILITY* in association models is 0.3, the query on this model should return more possible items than the query on the default model.</span></span>  
  
## <a name="create-a-prediction-by-using-a-model-with-the-default-minimum_probability"></a><span data-ttu-id="c9dcb-132">使用带有默认 MINIMUM_PROBABILITY 的模型创建预测</span><span class="sxs-lookup"><span data-stu-id="c9dcb-132">Create a Prediction by Using a Model with the Default MINIMUM_PROBABILITY</span></span>  
  
#### <a name="to-create-an-association-query"></a><span data-ttu-id="c9dcb-133">创建关联查询</span><span class="sxs-lookup"><span data-stu-id="c9dcb-133">To create an association query</span></span>  
  
1.  <span data-ttu-id="c9dcb-134">在**对象资源管理器**中，右键单击实例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，指向 "**新建查询**"，然后单击 " **DMX** " 以打开查询编辑器。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-134">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX** to open the Query Editor.</span></span>  
  
2.  <span data-ttu-id="c9dcb-135">将 `PREDICTION JOIN` 语句的一般示例复制到空白查询中。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-135">Copy the generic example of the `PREDICTION JOIN` statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="c9dcb-136">将</span><span class="sxs-lookup"><span data-stu-id="c9dcb-136">Replace the following:</span></span>  
  
    ```  
    <select list>   
    ```  
  
     <span data-ttu-id="c9dcb-137">替换为：</span><span class="sxs-lookup"><span data-stu-id="c9dcb-137">with:</span></span>  
  
    ```  
    PREDICT([Default Association].[Products],INCLUDE_STATISTICS,3)  
    ```  
  
     <span data-ttu-id="c9dcb-138">您可以只包括列名 [Products]，但通过使用 "[预测 &#40;DMX&#41;](/sql/dmx/predict-dmx)函数，您可以将该算法返回的产品数量限制为三个。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-138">You could just include the column name [Products], but by using the [Predict &#40;DMX&#41;](/sql/dmx/predict-dmx) function, you can limit the number of products that are returned by the algorithm to three.</span></span> <span data-ttu-id="c9dcb-139">还可以使用 `INCLUDE_STATISTICS`，它将返回每种产品的支持、概率以及校正后的概率。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-139">You can also use `INCLUDE_STATISTICS`, which returns the support, probability, and adjusted probability for each product.</span></span> <span data-ttu-id="c9dcb-140">这些统计信息有助于您对预测的准确性进行分级。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-140">These statistics help you rate the accuracy of the prediction.</span></span>  
  
4.  <span data-ttu-id="c9dcb-141">将</span><span class="sxs-lookup"><span data-stu-id="c9dcb-141">Replace the following:</span></span>  
  
    ```  
    [<mining model>]   
    ```  
  
     <span data-ttu-id="c9dcb-142">替换为：</span><span class="sxs-lookup"><span data-stu-id="c9dcb-142">with:</span></span>  
  
    ```  
    [Default Association]  
    ```  
  
5.  <span data-ttu-id="c9dcb-143">将</span><span class="sxs-lookup"><span data-stu-id="c9dcb-143">Replace the following:</span></span>  
  
    ```  
    (SELECT '<value>' AS [<column>],   
        (SELECT 'value' AS [<nested column>] UNION  
            SELECT 'value' AS [<nested column>] ...)   
        AS [<nested table>])  
    ```  
  
     <span data-ttu-id="c9dcb-144">替换为：</span><span class="sxs-lookup"><span data-stu-id="c9dcb-144">with:</span></span>  
  
    ```  
    (SELECT (SELECT 'Mountain Bottle Cage' AS [Model]  
      UNION SELECT 'Mountain Tire Tube' AS [Model]  
      UNION SELECT 'Mountain-200' AS [Model]) AS [Products]) AS t  
    ```  
  
     <span data-ttu-id="c9dcb-145">此语句使用 `UNION` 语句来指定三种产品，这三种产品必须与预测的产品一起包含在购物车中。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-145">This statement uses the `UNION` statement to specify three products that must be included in the shopping cart together with the predicted products.</span></span> <span data-ttu-id="c9dcb-146">`SELECT` 语句中的 Model 列对应于嵌套产品表中所包含的模型列。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-146">The Model column in the `SELECT` statement corresponds to the model column that is contained in the nested products table.</span></span>  
  
     <span data-ttu-id="c9dcb-147">现在，完整的语句应该如下所示：</span><span class="sxs-lookup"><span data-stu-id="c9dcb-147">The complete statement should now be as follows:</span></span>  
  
    ```  
    SELECT  
      PREDICT([Default Association].[Products],INCLUDE_STATISTICS,3)  
    From  
      [Default Association]  
    NATURAL PREDICTION JOIN  
    (SELECT (SELECT 'Mountain Bottle Cage' AS [Model]  
      UNION SELECT 'Mountain Tire Tube' AS [Model]  
      UNION SELECT 'Mountain-200' AS [Model]) AS [Products]) AS t  
    ```  
  
6.  <span data-ttu-id="c9dcb-148">在 "**文件**" 菜单上，单击 "**将 DMXQuery1 另存为**"。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-148">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
7.  <span data-ttu-id="c9dcb-149">在 "**另存为**" 对话框中，浏览到相应的文件夹，并将该文件命名为 `Association Prediction.dmx` 。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-149">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Association Prediction.dmx`.</span></span>  
  
8.  <span data-ttu-id="c9dcb-150">在工具栏上，单击 "**执行**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-150">On the toolbar, click the **Execute** button.</span></span>  
  
     <span data-ttu-id="c9dcb-151">查询将返回包含以下三种产品的表：HL Mountain Tire、Fender Set – Mountain 和 ML Mountain Tire。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-151">The query returns a table that contains three products: HL Mountain Tire, Fender Set - Mountain, and ML Mountain Tire.</span></span> <span data-ttu-id="c9dcb-152">该表按概率顺序列出这些返回的产品。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-152">The table lists these returned products in order of probability.</span></span> <span data-ttu-id="c9dcb-153">最有可能包含在查询指定的三种产品所在购物车中的返回的产品将出现在表的顶部。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-153">The returned product that is most likely to be included in the same shopping cart as the three products specified in the query appears at the top of the table.</span></span> <span data-ttu-id="c9dcb-154">其次最有可能包含在购物车中的产品是下面的两种产品。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-154">The two products that follow are the next most likely to be included in the shopping cart.</span></span> <span data-ttu-id="c9dcb-155">该表还包含说明预测准确性的统计信息。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-155">The table also contains statistics describing the accuracy of the prediction.</span></span>  
  
## <a name="create-a-prediction-by-using-a-model-with-a-minimum_probability-of-001"></a><span data-ttu-id="c9dcb-156">使用 MINIMUM_PROBABILITY 为 0.01 的模型创建预测</span><span class="sxs-lookup"><span data-stu-id="c9dcb-156">Create a Prediction by Using a Model with a MINIMUM_PROBABILITY of 0.01</span></span>  
  
#### <a name="to-create-an-association-query"></a><span data-ttu-id="c9dcb-157">创建关联查询</span><span class="sxs-lookup"><span data-stu-id="c9dcb-157">To create an association query</span></span>  
  
1.  <span data-ttu-id="c9dcb-158">在**对象资源管理器**中，右键单击实例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，指向 "**新建查询**"，然后单击 " **DMX** " 以打开查询编辑器。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-158">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX** to open the Query Editor.</span></span>  
  
2.  <span data-ttu-id="c9dcb-159">将 `PREDICTION JOIN` 语句的一般示例复制到空白查询中。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-159">Copy the generic example of the `PREDICTION JOIN` statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="c9dcb-160">将</span><span class="sxs-lookup"><span data-stu-id="c9dcb-160">Replace the following:</span></span>  
  
    ```  
    <select list>   
    ```  
  
     <span data-ttu-id="c9dcb-161">替换为：</span><span class="sxs-lookup"><span data-stu-id="c9dcb-161">with:</span></span>  
  
    ```  
    PREDICT([Modified Association].[Products],INCLUDE_STATISTICS,3)  
    ```  
  
4.  <span data-ttu-id="c9dcb-162">将</span><span class="sxs-lookup"><span data-stu-id="c9dcb-162">Replace the following:</span></span>  
  
    ```  
    [<mining model>]   
    ```  
  
     <span data-ttu-id="c9dcb-163">替换为：</span><span class="sxs-lookup"><span data-stu-id="c9dcb-163">with:</span></span>  
  
    ```  
    [Modified Association]  
    ```  
  
5.  <span data-ttu-id="c9dcb-164">将</span><span class="sxs-lookup"><span data-stu-id="c9dcb-164">Replace the following:</span></span>  
  
    ```  
    (SELECT '<value>' AS [<column>],   
        (SELECT 'value' AS [<nested column>] UNION  
            SELECT 'value' AS [<nested column>] ...)   
        AS [<nested table>])  
    ```  
  
     <span data-ttu-id="c9dcb-165">替换为：</span><span class="sxs-lookup"><span data-stu-id="c9dcb-165">with:</span></span>  
  
    ```  
    (SELECT (SELECT 'Mountain Bottle Cage' AS [Model]  
      UNION SELECT 'Mountain Tire Tube' AS [Model]  
      UNION SELECT 'Mountain-200' AS [Model]) AS [Products]) AS t  
    ```  
  
     <span data-ttu-id="c9dcb-166">此语句使用 `UNION` 语句来指定三种产品，这三种产品必须与预测的产品一起包含在购物车中。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-166">This statement uses the `UNION` statement to specify three products that must be included in the shopping cart together with the predicted products.</span></span> <span data-ttu-id="c9dcb-167">`SELECT` 语句中的 `[Model]` 列对应于嵌套产品表中的列。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-167">The `[Model]` column in the `SELECT` statement corresponds to the column in the nested products table.</span></span>  
  
     <span data-ttu-id="c9dcb-168">现在，完整的语句应该如下所示：</span><span class="sxs-lookup"><span data-stu-id="c9dcb-168">The complete statement should now be as follows:</span></span>  
  
    ```  
    SELECT  
      PREDICT([Modified Association].[Products],INCLUDE_STATISTICS,3)  
    From  
      [Modified Association]  
    NATURAL PREDICTION JOIN  
    (SELECT (SELECT 'Mountain Bottle Cage' AS [Model]  
      UNION SELECT 'Mountain Tire Tube' AS [Model]  
      UNION SELECT 'Mountain-200' AS [Model]) AS [Products]) AS t  
    ```  
  
6.  <span data-ttu-id="c9dcb-169">在 "**文件**" 菜单上，单击 "**将 DMXQuery1 另存为**"。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-169">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
7.  <span data-ttu-id="c9dcb-170">在 "**另存为**" 对话框中，浏览到相应的文件夹，并将该文件命名为 `Modified Association Prediction.dmx` 。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-170">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Modified Association Prediction.dmx`.</span></span>  
  
8.  <span data-ttu-id="c9dcb-171">在工具栏上，单击 "**执行**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-171">On the toolbar, click the **Execute** button.</span></span>  
  
     <span data-ttu-id="c9dcb-172">查询将返回包含以下三种产品的表：HL Mountain Tire、Water Bottle 和 Fender Set - Mountain。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-172">The query returns a table that contains three products: HL Mountain Tire, Water Bottle, and Fender Set - Mountain.</span></span> <span data-ttu-id="c9dcb-173">该表按概率顺序列出这些产品。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-173">The table lists these products in order of probability.</span></span> <span data-ttu-id="c9dcb-174">出现在该表顶部的产品是最有可能包含在查询指定的三种产品所在购物车中的产品。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-174">The product that appears at the top of the table is the product that is most likely to be included in the same shopping cart as the three products specified in the query.</span></span> <span data-ttu-id="c9dcb-175">其余产品是其次最有可能包含在该购物车中的产品。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-175">The remaining products are the next most likely to be included in the shopping cart.</span></span> <span data-ttu-id="c9dcb-176">该表还包含描述预测准确性的统计信息。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-176">The table also contains statistics that describe the accuracy of the prediction.</span></span>  
  
     <span data-ttu-id="c9dcb-177">在此查询的结果中可以看到， *MINIMUM_PROBABILITY*参数的值会影响查询返回的结果。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-177">You can see from the results of this query that the value of the *MINIMUM_PROBABILITY* parameter affects the results returned by the query.</span></span>  
  
 <span data-ttu-id="c9dcb-178">这是市场篮教程中的最后一个步骤。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-178">This is the last step in the Market Basket tutorial.</span></span> <span data-ttu-id="c9dcb-179">您现在即可拥有一组模型，并可通过该组模型预测客户可能同时购买的产品。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-179">You now have a set of models that you can use to predict the products that customers might purchase at the same time.</span></span>  
  
 <span data-ttu-id="c9dcb-180">若要了解如何在另一个预测方案中使用 DMX，请参阅[自行车购买者 DMX 教程](../../2014/tutorials/bike-buyer-dmx-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="c9dcb-180">To learn how to use DMX in another predictive scenario, see [Bike Buyer DMX Tutorial](../../2014/tutorials/bike-buyer-dmx-tutorial.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9dcb-181">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c9dcb-181">See Also</span></span>  
 <span data-ttu-id="c9dcb-182">[关联模型查询示例](../../2014/analysis-services/data-mining/association-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="c9dcb-182">[Association Model Query Examples](../../2014/analysis-services/data-mining/association-model-query-examples.md) </span></span>  
 [<span data-ttu-id="c9dcb-183">数据挖掘查询接口</span><span class="sxs-lookup"><span data-stu-id="c9dcb-183">Data Mining Query Interfaces</span></span>](../../2014/analysis-services/data-mining/data-mining-query-tools.md)  
  
  
