---
title: 对顺序分析和聚类分析模型创建预测 (中间数据挖掘教程) |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 94a8d4f9-a76a-49c5-9785-917010359511
author: minewiskan
ms.author: owend
manager: kfilee
ms.openlocfilehash: 2402c28a564502df9ce12c5e3f97b9d19590cfea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576461"
---
# <a name="creating-predictions-on-a-sequence-clustering-model-intermediate-data-mining-tutorial"></a><span data-ttu-id="7207b-102">针对顺序分析和聚类分析模型创建预测（数据挖掘中级教程）</span><span class="sxs-lookup"><span data-stu-id="7207b-102">Creating Predictions on a Sequence Clustering Model (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="7207b-103">通过在查看器中浏览顺序来更好地了解顺序分析和聚类分析模型之后，可以使用数据挖掘设计器中 "**挖掘模型预测**" 选项卡上的预测查询生成器来创建预测查询。</span><span class="sxs-lookup"><span data-stu-id="7207b-103">After you understand the sequence clustering model better by browsing it in the viewer, you can create prediction queries by using Prediction Query Builder on the **Mining Model Prediction** tab in Data Mining Designer.</span></span> <span data-ttu-id="7207b-104">若要创建预测，首先要选择顺序分析和聚类分析模型，然后选择输入数据。</span><span class="sxs-lookup"><span data-stu-id="7207b-104">To create a prediction, you first select the sequence clustering model, and then select the input data.</span></span> <span data-ttu-id="7207b-105">对于输入，可以使用外部数据源，也可以生成单独查询并在对话框中提供值。</span><span class="sxs-lookup"><span data-stu-id="7207b-105">For inputs, you can use either an external data source, or you can build a singleton query and provide values in a dialog box.</span></span>  
  
 <span data-ttu-id="7207b-106">本课程假定您已经熟悉如何使用预测查询生成器，同时希望了解如何针对顺序分析和聚类分析模型生成查询。</span><span class="sxs-lookup"><span data-stu-id="7207b-106">This lesson assumes that you are already familiar with how to use the prediction query builder and want to learn how to build queries that are specific to a sequence clustering model.</span></span> <span data-ttu-id="7207b-107">有关如何使用预测查询生成器的常规信息，请参阅[数据挖掘查询接口](../../2014/analysis-services/data-mining/data-mining-query-tools.md)或基本数据挖掘教程的部分，[创建 &#40;基本数据挖掘教程&#41;的预测](../../2014/tutorials/creating-predictions-basic-data-mining-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="7207b-107">For general information about how to use Prediction Query Builder, see [Data Mining Query Interfaces](../../2014/analysis-services/data-mining/data-mining-query-tools.md) or the section of the Basic Data Mining tutorial, [Creating Predictions &#40;Basic Data Mining Tutorial&#41;](../../2014/tutorials/creating-predictions-basic-data-mining-tutorial.md).</span></span>  
  
## <a name="creating-predictions-on-the-regional-model"></a><span data-ttu-id="7207b-108">针对 Regional 模型创建预测</span><span class="sxs-lookup"><span data-stu-id="7207b-108">Creating Predictions on the Regional Model</span></span>  
 <span data-ttu-id="7207b-109">对此方案，您首先需要创建一些单独预测查询，以了解预测结果如何因区域不同而不同。</span><span class="sxs-lookup"><span data-stu-id="7207b-109">For this scenario, you will first create some singleton prediction queries, to get an idea of how predictions might be different by region.</span></span>  
  
#### <a name="to-create-a-singleton-query-on-a-sequence-clustering-model"></a><span data-ttu-id="7207b-110">针对顺序分析和聚类分析模型创建单独查询</span><span class="sxs-lookup"><span data-stu-id="7207b-110">To create a singleton query on a sequence clustering model</span></span>  
  
1.  <span data-ttu-id="7207b-111">单击数据挖掘设计器的 "**挖掘模型预测**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="7207b-111">Click the **Mining Model Prediction** tab of Data Mining Designer.</span></span>  
  
2.  <span data-ttu-id="7207b-112">在 "**挖掘模型**列" 菜单中，选择 "**单独查询**"。</span><span class="sxs-lookup"><span data-stu-id="7207b-112">In the **Mining Model** column menu, select **Singleton Query**.</span></span>  
  
     <span data-ttu-id="7207b-113">随即出现 "**挖掘模型**" 窗格和 "**单独查询输入**" 窗格。</span><span class="sxs-lookup"><span data-stu-id="7207b-113">The **Mining Model** pane and **Singleton Query Input** pane appear.</span></span>  
  
3.  <span data-ttu-id="7207b-114">在 "**挖掘模型**" 窗格中单击 "**选择模型**"。</span><span class="sxs-lookup"><span data-stu-id="7207b-114">In the **Mining Model** pane, click **Select Model**.</span></span> <span data-ttu-id="7207b-115">（如果已选择顺序分析和聚类分析模型，则可跳过此步骤。）</span><span class="sxs-lookup"><span data-stu-id="7207b-115">(You can skip this step if the sequence clustering mode is already selected.)</span></span>  
  
     <span data-ttu-id="7207b-116">此时将打开 "**选择挖掘模型**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="7207b-116">The **Select Mining Model** dialog box opens.</span></span>  
  
4.  <span data-ttu-id="7207b-117">展开表示挖掘结构**顺序群集**的节点，并选择 "**包含区域**的模型序列"。</span><span class="sxs-lookup"><span data-stu-id="7207b-117">Expand the node that represents the mining structure **Sequence Clustering with Region**, and select the model **Sequence Clustering with Region**.</span></span> <span data-ttu-id="7207b-118">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="7207b-118">Click **OK**.</span></span> <span data-ttu-id="7207b-119">现在，请忽略“输入”窗格；您将在设置预测函数之后指定输入。</span><span class="sxs-lookup"><span data-stu-id="7207b-119">For now, ignore the input pane; you will specify the inputs after you have set up the prediction functions.</span></span>  
  
5.  <span data-ttu-id="7207b-120">在网格中，单击 "**源**" 下的空单元格，然后选择 "**预测函数"。**</span><span class="sxs-lookup"><span data-stu-id="7207b-120">In the grid, click the empty cell under **Source** and select **Prediction Function.**</span></span> <span data-ttu-id="7207b-121">在 "**字段**" 下的单元中，选择 " **PredictSequence**"。</span><span class="sxs-lookup"><span data-stu-id="7207b-121">In the cell under **Field**, select **PredictSequence**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7207b-122">您也可以使用**Predict**函数。</span><span class="sxs-lookup"><span data-stu-id="7207b-122">You can also use the **Predict** function.</span></span> <span data-ttu-id="7207b-123">如果执行此操作，请确保选择采用表列作为参数的**Predict**函数的版本。</span><span class="sxs-lookup"><span data-stu-id="7207b-123">If you do, be sure to choose the version of the **Predict** function that takes a table column as argument..</span></span>  
  
6.  <span data-ttu-id="7207b-124">在 "**挖掘模型**" 窗格中，选择嵌套表 `v Assoc Seq Line Items` ，并将其拖到网格中的**PredictSequence**函数的 "**条件/参数**" 框。</span><span class="sxs-lookup"><span data-stu-id="7207b-124">In the **Mining Model** pane, select the nested table `v Assoc Seq Line Items`, and drag it into the grid, to the **Criteria/Argument** box for the **PredictSequence** function.</span></span>  
  
     <span data-ttu-id="7207b-125">拖放表名称和列名称使您能够生成复杂语句，而不会出现语法错误。</span><span class="sxs-lookup"><span data-stu-id="7207b-125">Dragging and dropping table and column names enables you to build complex statements without syntax errors.</span></span> <span data-ttu-id="7207b-126">但是，它将替换单元的当前内容，其中包括**PredictSequence**函数的其他可选参数。</span><span class="sxs-lookup"><span data-stu-id="7207b-126">However, it replaces the current contents of the cell, which include other optional arguments for the **PredictSequence** function.</span></span> <span data-ttu-id="7207b-127">为了查看其他参数，可以将函数的另一个实例临时添加到网格供参考。</span><span class="sxs-lookup"><span data-stu-id="7207b-127">To view the other arguments, you can temporarily add a second instance of the function to the grid for reference.</span></span>  
  
7.  <span data-ttu-id="7207b-128">单击预测查询生成器上角的 "**结果**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="7207b-128">Click the **Result** button in the upper corner of the Prediction Query Builder.</span></span>  
  
 <span data-ttu-id="7207b-129">预期结果包含带有标题**表达式**的单个列。</span><span class="sxs-lookup"><span data-stu-id="7207b-129">The expected results contain a single column with the heading **Expression**.</span></span> <span data-ttu-id="7207b-130">**Expression**列包含一个嵌套表，其中包含三列，如下所示：</span><span class="sxs-lookup"><span data-stu-id="7207b-130">The **Expression** column contains a nested table with three columns as follows:</span></span>  
  
|<span data-ttu-id="7207b-131">$SEQUENCE</span><span class="sxs-lookup"><span data-stu-id="7207b-131">$SEQUENCE</span></span>|<span data-ttu-id="7207b-132">Line Number</span><span class="sxs-lookup"><span data-stu-id="7207b-132">Line Number</span></span>|<span data-ttu-id="7207b-133">模型</span><span class="sxs-lookup"><span data-stu-id="7207b-133">Model</span></span>|  
|---------------|-----------------|-----------|  
|<span data-ttu-id="7207b-134">1</span><span class="sxs-lookup"><span data-stu-id="7207b-134">1</span></span>||<span data-ttu-id="7207b-135">Mountain-200</span><span class="sxs-lookup"><span data-stu-id="7207b-135">Mountain-200</span></span>|  
  
 <span data-ttu-id="7207b-136">这些结果是什么意思？</span><span class="sxs-lookup"><span data-stu-id="7207b-136">What do these results mean?</span></span> <span data-ttu-id="7207b-137">请记住，您没有指定任何输入。</span><span class="sxs-lookup"><span data-stu-id="7207b-137">Remember that you did not specify any inputs.</span></span> <span data-ttu-id="7207b-138">因此，该预测针对整个事例，Analysis Services 会返回最可能的总预测。</span><span class="sxs-lookup"><span data-stu-id="7207b-138">Therefore, the prediction is made against the entire population of cases, and Analysis Services returns the most likely prediction overall.</span></span>  
  
### <a name="adding-inputs-to-a-singleton-prediction-query"></a><span data-ttu-id="7207b-139">向单独预测查询添加输入</span><span class="sxs-lookup"><span data-stu-id="7207b-139">Adding Inputs to a Singleton Prediction Query</span></span>  
 <span data-ttu-id="7207b-140">到现在为止，您还没有指定任何输入。</span><span class="sxs-lookup"><span data-stu-id="7207b-140">Until now, you have not specified any inputs.</span></span> <span data-ttu-id="7207b-141">在下一任务中，您将使用 "**单独查询输入**" 窗格来指定查询的某些输入。</span><span class="sxs-lookup"><span data-stu-id="7207b-141">In the next task, you will use the **Singleton Query Input** pane to specify some inputs to the query.</span></span> <span data-ttu-id="7207b-142">首先，使用 [Region] 作为区域顺序分析和聚类分析模型的输入，以确定所有区域的预测序列是否都相同。</span><span class="sxs-lookup"><span data-stu-id="7207b-142">First, you will use [Region] as an input to the regional sequence clustering model, to determine whether the predicted sequences are the same for all regions.</span></span> <span data-ttu-id="7207b-143">然后将了解如何修改查询以添加每项查询的概率，并简化结果以便易于查看。</span><span class="sxs-lookup"><span data-stu-id="7207b-143">You will then learn how to modify the query to add the probability for each prediction, and flatten the results to make them easier to view.</span></span>  
  
##### <a name="to-generate-predictions-for-a-specific-customer-group"></a><span data-ttu-id="7207b-144">针对特定客户组生成预测</span><span class="sxs-lookup"><span data-stu-id="7207b-144">To generate predictions for a specific customer group</span></span>  
  
1.  <span data-ttu-id="7207b-145">单击预测查询生成器左上角的 "**设计**" 按钮，切换回查询生成网格。</span><span class="sxs-lookup"><span data-stu-id="7207b-145">Click the **Design** button in the upper left-hand corner of the Prediction Query Builder to switch back to the query building grid.</span></span>  
  
2.  <span data-ttu-id="7207b-146">在 "**单独查询输入**" 对话框中，单击 "**值**" 框 `Region` ，然后选择 "**欧洲**"。</span><span class="sxs-lookup"><span data-stu-id="7207b-146">In the **Singleton Query Input** dialog box, click the **Value** box for `Region`, and select **Europe**.</span></span>  
  
3.  <span data-ttu-id="7207b-147">单击 "**结果**" 按钮，查看欧洲客户的预测。</span><span class="sxs-lookup"><span data-stu-id="7207b-147">Click the **Result** button to view predictions for customers in Europe.</span></span>  
  
4.  <span data-ttu-id="7207b-148">单击预测查询生成器左上角的 "**设计**" 按钮，切换回查询生成网格。</span><span class="sxs-lookup"><span data-stu-id="7207b-148">Click the **Design** button in the upper left-hand corner of the Prediction Query Builder to switch back to the query building grid.</span></span>  
  
5.  <span data-ttu-id="7207b-149">在 "**单独查询输入**" 对话框中，单击 "**值**" 框 `Region` ，然后选择 "**北美**"。</span><span class="sxs-lookup"><span data-stu-id="7207b-149">In the **Singleton Query Input** dialog box, click the **Value** box for `Region`, and select **North America**.</span></span>  
  
6.  <span data-ttu-id="7207b-150">单击 "**结果**" 按钮可以查看北美中客户的预测。</span><span class="sxs-lookup"><span data-stu-id="7207b-150">Click the **Result** button to view predictions for customers in North America.</span></span>  
  
### <a name="adding-probabilities-by-using-a-custom-expression"></a><span data-ttu-id="7207b-151">使用自定义表达式添加概率</span><span class="sxs-lookup"><span data-stu-id="7207b-151">Adding Probabilities by Using a Custom Expression</span></span>  
 <span data-ttu-id="7207b-152">由于概率是预测的特性并且是作为嵌套表输出，所以输出每个预测的概率要稍微复杂一些。</span><span class="sxs-lookup"><span data-stu-id="7207b-152">To output the probability for each prediction is slightly more complicated, because the probability is an attribute of the prediction and is output as a nested table.</span></span> <span data-ttu-id="7207b-153">如果您熟悉数据挖掘扩展插件 (DMX)，就可以轻松地更改查询，在嵌套表上添加嵌套 select 语句。</span><span class="sxs-lookup"><span data-stu-id="7207b-153">If you are familiar with Data Mining Extensions (DMX), you can easily alter the query to add a sub-select statement on the nested table.</span></span> <span data-ttu-id="7207b-154">也可以通过添加自定义表达式的方法在预测查询生成器中创建嵌套 select 语句。</span><span class="sxs-lookup"><span data-stu-id="7207b-154">However, you can also create a sub-select statement in the Prediction Query Builder by adding a custom expression.</span></span>  
  
##### <a name="to-output-probabilities-for-a-predicted-sequence-by-using-a-custom-expression"></a><span data-ttu-id="7207b-155">使用自定义表达式输出预测序列的概率</span><span class="sxs-lookup"><span data-stu-id="7207b-155">To output probabilities for a predicted sequence by using a custom expression</span></span>  
  
1.  <span data-ttu-id="7207b-156">单击预测查询生成器左上角的 "**设计**" 按钮，切换回查询生成网格。</span><span class="sxs-lookup"><span data-stu-id="7207b-156">Click the **Design** button in the upper left-hand corner of the Prediction Query Builder to switch back to the query building grid.</span></span>  
  
2.  <span data-ttu-id="7207b-157">在网格中的 "**源**" 下，单击新行，然后选择 "**自定义表达式**"。</span><span class="sxs-lookup"><span data-stu-id="7207b-157">In the grid, under **Source**, click a new row, and select **Custom Expression**.</span></span>  
  
3.  <span data-ttu-id="7207b-158">将 "**字段**" 下的框留空。</span><span class="sxs-lookup"><span data-stu-id="7207b-158">Leave the box under **Field** blank.</span></span>  
  
4.  <span data-ttu-id="7207b-159">对于 "**别名**"，键入 `t` 。</span><span class="sxs-lookup"><span data-stu-id="7207b-159">For **Alias**, type `t`.</span></span>  
  
5.  <span data-ttu-id="7207b-160">在 "**条件/参数**" 框中，键入完整的子 select 语句，如下面的代码示例中所示。</span><span class="sxs-lookup"><span data-stu-id="7207b-160">In the **Criteria/Argument** box, type the complete sub-select statement as shown in the following code sample.</span></span> <span data-ttu-id="7207b-161">请确保包括开始括号和结束括号。</span><span class="sxs-lookup"><span data-stu-id="7207b-161">Be sure to include the starting and ending parentheses.</span></span>  
  
    ```  
    (SELECT PredictProbability([Model]) FROM PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]))  
    ```  
  
6.  <span data-ttu-id="7207b-162">单击 "**结果**" 按钮，查看欧洲客户的预测。</span><span class="sxs-lookup"><span data-stu-id="7207b-162">Click the **Result** button to view predictions for customers in Europe.</span></span>  
  
 <span data-ttu-id="7207b-163">现在结果包含两个嵌套表，一个包含预测，另一个包含预测的概率。</span><span class="sxs-lookup"><span data-stu-id="7207b-163">The results now contain two nested tables, one with the prediction, and one with the probability for the prediction.</span></span> <span data-ttu-id="7207b-164">如果查询不能运行，可以切换到查询设计视图查看完整的查询语句，应该如下所示：</span><span class="sxs-lookup"><span data-stu-id="7207b-164">If the query does not work, you can switch to query design view and review the complete query statement, which should be as follows:</span></span>  
  
```  
SELECT  
  PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]),  
  ( (SELECT PredictProbability([Model]) FROM PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]))) as [t]  
FROM  
  [Sequence Clustering with Region]  
NATURAL PREDICTION JOIN  
(SELECT 'Europe' AS [Region]) AS t  
```  
  
### <a name="working-with-results"></a><span data-ttu-id="7207b-165">使用结果</span><span class="sxs-lookup"><span data-stu-id="7207b-165">Working with Results</span></span>  
 <span data-ttu-id="7207b-166">如果结果中有很多嵌套表，您可能希望简化结果以便查看。</span><span class="sxs-lookup"><span data-stu-id="7207b-166">When there are many nested tables in the results, you might want to flatten the results for easier viewing.</span></span> <span data-ttu-id="7207b-167">为此，您可以手动修改查询并添加 `FLATTENED` 关键字。</span><span class="sxs-lookup"><span data-stu-id="7207b-167">To do this, you can manually modify the query and add the `FLATTENED` keyword.</span></span>  
  
##### <a name="to-flatten-nested-rowsets-in-a-prediction-query"></a><span data-ttu-id="7207b-168">平展预测查询中的嵌套行集</span><span class="sxs-lookup"><span data-stu-id="7207b-168">To flatten nested rowsets in a prediction query</span></span>  
  
1.  <span data-ttu-id="7207b-169">单击预测查询生成器角的 "**查询**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="7207b-169">Click the **Query** button in the corner of the Prediction Query Builder.</span></span>  
  
     <span data-ttu-id="7207b-170">网格更改为一个打开的窗格，在此您可以查看和修改由预测查询生成器创建的 DMX 语句。</span><span class="sxs-lookup"><span data-stu-id="7207b-170">The grid changes to an open pane where you can view and modify the DMX statement that was created by the Prediction Query Builder.</span></span>  
  
2.  <span data-ttu-id="7207b-171">在 `SELECT` 关键字后键入 `FLATTENED`。</span><span class="sxs-lookup"><span data-stu-id="7207b-171">After the `SELECT` keyword, type `FLATTENED`.</span></span>  
  
     <span data-ttu-id="7207b-172">完整的查询文本应与以下内容相似：</span><span class="sxs-lookup"><span data-stu-id="7207b-172">The complete text of the query should be similar to the following:</span></span>  
  
    ```  
    SELECT FLATTENED  
      PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]),  
      ( (SELECT PredictProbability([Model]) FROM PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]))) as [t]  
    FROM  
      [Sequence Clustering with Region]  
    NATURAL PREDICTION JOIN  
    (SELECT 'Europe' AS [Region]) AS t  
    ```  
  
3.  <span data-ttu-id="7207b-173">单击预测查询生成器上角的 "**结果**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="7207b-173">Click the **Results** button in the upper corner of the Prediction Query Builder.</span></span>  
  
 <span data-ttu-id="7207b-174">手动编辑查询之后，将无法切换回设计视图而不丢失更改。</span><span class="sxs-lookup"><span data-stu-id="7207b-174">After you have manually edited a query, you will not be able to switch back to Design view without losing the changes.</span></span> <span data-ttu-id="7207b-175">不过，您可以将创建的 DMX 语句手动保存到文本文件，然后更改回设计视图。</span><span class="sxs-lookup"><span data-stu-id="7207b-175">You can, however, save the DMX statement that you created manually to a text file, and then change back to Design view.</span></span> <span data-ttu-id="7207b-176">这时，查询会恢复到在设计视图中有效的上一版本。</span><span class="sxs-lookup"><span data-stu-id="7207b-176">When you do so, the query is reverted to the last version that was valid in Design view.</span></span>  
  
## <a name="creating-predictions-on-the-related-model"></a><span data-ttu-id="7207b-177">根据相关模型创建预测</span><span class="sxs-lookup"><span data-stu-id="7207b-177">Creating Predictions on the Related Model</span></span>  
 <span data-ttu-id="7207b-178">由于您希望了解模型在区域之间是否发现任何差别，所以前面的示例使用了一个事例表列 Region 作为单独预测查询的输入。</span><span class="sxs-lookup"><span data-stu-id="7207b-178">The previous examples used a case table column, Region, as the input to the singleton prediction query, because you were interested in knowing whether the model had found any differences between regions.</span></span> <span data-ttu-id="7207b-179">但是，浏览了模型之后，您发现差别不足以证明按区域可以生成自定义产品的建议。</span><span class="sxs-lookup"><span data-stu-id="7207b-179">However, after exploring the model, you decided that the differences are not strong enough to justify customizing product recommendations by region.</span></span> <span data-ttu-id="7207b-180">您真正感兴趣的是预测客户选择的产品。</span><span class="sxs-lookup"><span data-stu-id="7207b-180">What you are really interested in predicting is the items that customers select.</span></span> <span data-ttu-id="7207b-181">因此，在下面的查询中，您将使用不包括 Region 的顺序分析和聚类分析模型来生成对所有客户的建议。</span><span class="sxs-lookup"><span data-stu-id="7207b-181">Therefore, in the queries that follow, you will use the sequence clustering model that does not include Region, to generate recommendations for all customers.</span></span>  
  
### <a name="using-nested-table-columns-as-input"></a><span data-ttu-id="7207b-182">使用嵌套表列作为输入</span><span class="sxs-lookup"><span data-stu-id="7207b-182">Using Nested Table Columns as Input</span></span>  
 <span data-ttu-id="7207b-183">首先要创建一个单独预测查询，采用单个产品作为输入并返回下一个最可能的产品。</span><span class="sxs-lookup"><span data-stu-id="7207b-183">First you will create a singleton prediction query that takes a single item as input and returns the next most likely item.</span></span> <span data-ttu-id="7207b-184">若要获取此类预测，您需要使用嵌套表列作为输入值。</span><span class="sxs-lookup"><span data-stu-id="7207b-184">To get a prediction of this kind, you have to use a nested table column as the input value.</span></span> <span data-ttu-id="7207b-185">这是因为正在预测的属性 Model 是嵌套表的一部分。</span><span class="sxs-lookup"><span data-stu-id="7207b-185">This is because the attribute that you are predicting, Model, is part of a nested table.</span></span> <span data-ttu-id="7207b-186">Analysis Services 提供了 "**嵌套表输入**" 对话框，通过使用预测查询生成器，可以帮助您轻松地创建对嵌套表属性的预测查询。</span><span class="sxs-lookup"><span data-stu-id="7207b-186">Analysis Services provides the **Nested Table Input** dialog box to help you easily create prediction queries on nested table attributes, by using the Prediction Query Builder.</span></span>  
  
##### <a name="to-use-a-nested-table-as-input-to-a-prediction"></a><span data-ttu-id="7207b-187">使用嵌套表作为预测输入</span><span class="sxs-lookup"><span data-stu-id="7207b-187">To use a nested table as input to a prediction</span></span>  
  
1.  <span data-ttu-id="7207b-188">单击预测查询生成器左上角的 "**设计**" 按钮，切换回查询生成网格。</span><span class="sxs-lookup"><span data-stu-id="7207b-188">Click the **Design** button in the upper left-hand corner of the Prediction Query Builder to switch back to the query building grid.</span></span>  
  
2.  <span data-ttu-id="7207b-189">在 "**单独查询输入**" 对话框中，单击 "**值**" 框 `Region` ，然后选择空行以清除此字段的输入。</span><span class="sxs-lookup"><span data-stu-id="7207b-189">In the **Singleton Query Input** dialog box, click the **Value** box for `Region`, and select the empty row to clear the input for this field.</span></span>  
  
3.  <span data-ttu-id="7207b-190">在 "**单独查询输入**" 对话框中，单击 "**值**" 框 `vAssocSeqLineItems` ，然后单击 " ( ... ) " 按钮。</span><span class="sxs-lookup"><span data-stu-id="7207b-190">In the **Singleton Query Input** dialog box, click the **Value** box for `vAssocSeqLineItems`, and then click the (...) button.</span></span>  
  
4.  <span data-ttu-id="7207b-191">在 "**嵌套表输入**" 对话框中，单击 "**添加**"。</span><span class="sxs-lookup"><span data-stu-id="7207b-191">In the **Nested Table Input** dialog box, click **Add**.</span></span>  
  
5.  <span data-ttu-id="7207b-192">在新行中，单击下的框 `Model` ，然后从列表中选择 "旅行轮胎"。</span><span class="sxs-lookup"><span data-stu-id="7207b-192">In the new row, click the box under `Model`, and select Touring Tire from the list.</span></span> <span data-ttu-id="7207b-193">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="7207b-193">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="7207b-194">单击 "**结果**" 按钮查看预测。</span><span class="sxs-lookup"><span data-stu-id="7207b-194">Click the **Result** button to view the predictions.</span></span>  
  
 <span data-ttu-id="7207b-195">该模型为选择 Touring Tire 作为第一件商品的所有客户推荐了其他商品。</span><span class="sxs-lookup"><span data-stu-id="7207b-195">The model recommends the following next items for all customers who choose the Touring Tire as the first item.</span></span> <span data-ttu-id="7207b-196">您已经通过浏览模型了解到，客户经常同时购买 Touring Tire 和 Touring Tire Tube，因此这些建议看来不错。</span><span class="sxs-lookup"><span data-stu-id="7207b-196">You already know from exploring the model that customers frequently purchase the products Touring Tire and Touring Tire Tube together, so these recommendations look good.</span></span>  
  
|<span data-ttu-id="7207b-197">$SEQUENCE</span><span class="sxs-lookup"><span data-stu-id="7207b-197">$SEQUENCE</span></span>|<span data-ttu-id="7207b-198">Line Number</span><span class="sxs-lookup"><span data-stu-id="7207b-198">Line Number</span></span>|<span data-ttu-id="7207b-199">模型</span><span class="sxs-lookup"><span data-stu-id="7207b-199">Model</span></span>|  
|---------------|-----------------|-----------|  
|<span data-ttu-id="7207b-200">1</span><span class="sxs-lookup"><span data-stu-id="7207b-200">1</span></span>||<span data-ttu-id="7207b-201">Touring Tire Tube</span><span class="sxs-lookup"><span data-stu-id="7207b-201">Touring Tire Tube</span></span>|  
|<span data-ttu-id="7207b-202">2</span><span class="sxs-lookup"><span data-stu-id="7207b-202">2</span></span>||<span data-ttu-id="7207b-203">Sport-100</span><span class="sxs-lookup"><span data-stu-id="7207b-203">Sport-100</span></span>|  
|<span data-ttu-id="7207b-204">3</span><span class="sxs-lookup"><span data-stu-id="7207b-204">3</span></span>||<span data-ttu-id="7207b-205">Long-Sleeve Logo Jersey</span><span class="sxs-lookup"><span data-stu-id="7207b-205">Long-Sleeve Logo Jersey</span></span>|  
  
### <a name="creating-a-bulk-prediction-query-using-nested-table-inputs"></a><span data-ttu-id="7207b-206">使用嵌套表输入创建大量预测查询</span><span class="sxs-lookup"><span data-stu-id="7207b-206">Creating a Bulk Prediction Query using Nested Table Inputs</span></span>  
 <span data-ttu-id="7207b-207">现在，对于模型创建的预测可用来进行营销建议您感到很满意，您将创建一个映射到外部数据源的预测查询。</span><span class="sxs-lookup"><span data-stu-id="7207b-207">Now that you are satisfied that the model creates the kind of predictions that you can use in making recommendations, you will create a prediction query that is mapped to an external data source.</span></span> <span data-ttu-id="7207b-208">该数据源将提供表示当前产品的值。</span><span class="sxs-lookup"><span data-stu-id="7207b-208">That data source will provide values representing current products.</span></span> <span data-ttu-id="7207b-209">您希望创建一个预测查询，以将客户 ID 和产品列表作为输入，因此需要将客户表添加为事例表，将采购表添加为嵌套表。</span><span class="sxs-lookup"><span data-stu-id="7207b-209">Because you are interested in creating a prediction query that provides Customer ID and a list of products as input, you will add the customer table as the case table, and the purchases table as the nested table.</span></span> <span data-ttu-id="7207b-210">然后像前面那样，您将添加预测函数创建建议。</span><span class="sxs-lookup"><span data-stu-id="7207b-210">Then you will add prediction functions as you did previously to create recommendations.</span></span>  
  
 <span data-ttu-id="7207b-211">这与您在第 3 课的市场篮方案中创建预测使用的是同一过程；不过，在顺序分析和聚类分析模型预测中还需要将顺序作为输入。</span><span class="sxs-lookup"><span data-stu-id="7207b-211">This is the same procedure that you use to create predictions for the market basket scenario in Lesson 3; however, in a sequence clustering model predictions also need the order as input.</span></span>  
  
##### <a name="to-create-a-prediction-query-using-nested-table-inputs"></a><span data-ttu-id="7207b-212">使用嵌套表输入创建预测查询</span><span class="sxs-lookup"><span data-stu-id="7207b-212">To create a prediction query using nested table inputs</span></span>  
  
1.  <span data-ttu-id="7207b-213">在 "**挖掘模型**" 窗格中，选择 "顺序分析和聚类分析模型" （如果尚未选择）。</span><span class="sxs-lookup"><span data-stu-id="7207b-213">In the **Mining Model** pane, select the Sequence Clustering model, if it is not already selected.</span></span>  
  
2.  <span data-ttu-id="7207b-214">在 "**选择输入表 (s) \*\* " 对话框中，单击 "**选择事例表\*\*"。</span><span class="sxs-lookup"><span data-stu-id="7207b-214">In the **Select Input Table(s)** dialog box, click **Select Case Table**.</span></span>  
  
3.  <span data-ttu-id="7207b-215">在 "**选择表**" 对话框中，为 "数据源" 选择 Orders。</span><span class="sxs-lookup"><span data-stu-id="7207b-215">In the **Select Table** dialog box, for Data Source, select Orders.</span></span> <span data-ttu-id="7207b-216">在 "**表/视图名称**" 列表中，选择 "vAssocSeqOrders"，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="7207b-216">In the **Table/View Name** list, select vAssocSeqOrders, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="7207b-217">在 "**选择输入表 (s) \*\* " 对话框中，单击 "**选择嵌套表\*\*"。</span><span class="sxs-lookup"><span data-stu-id="7207b-217">In the **Select Input Table(s)** dialog box, click **Select Nested Table**.</span></span>  
  
5.  <span data-ttu-id="7207b-218">在 "**选择表**" 对话框中，为 "**数据源**" 选择 Orders。</span><span class="sxs-lookup"><span data-stu-id="7207b-218">In the **Select Table** dialog box, for **Data Source**, select Orders.</span></span> <span data-ttu-id="7207b-219">在 "**表/视图名称**" 列表中，选择 "vAssocSeqLineItems"，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="7207b-219">In the **Table/View name** list, select vAssocSeqLineItems, and then click **OK**.</span></span>  
  
     <span data-ttu-id="7207b-220">Analysis Services 将尝试检测关系，如果数据类型匹配并且列名称相近，将自动创建关系。</span><span class="sxs-lookup"><span data-stu-id="7207b-220">Analysis Services will try to detect relationships and create them automatically if the data types match and the column names are similar.</span></span> <span data-ttu-id="7207b-221">如果它创建的关系是错误的，则可以右键单击联接线并选择 "**修改连接**" 来编辑列映射，或者右键单击联接线并选择 "**删除**" 以完全删除该关系。</span><span class="sxs-lookup"><span data-stu-id="7207b-221">If the relationships that it creates are wrong, you can right-click the join line and select **Modify Connections** to edit the column mapping, or you can right-click the join line and select **Delete** to remove the relationship completely.</span></span> <span data-ttu-id="7207b-222">在此方案中，由于表已经在数据源视图中联接，因此，将在“设计”窗格中自动添加这些关系。</span><span class="sxs-lookup"><span data-stu-id="7207b-222">In this case, because the tables were already joined in the data source view, those relationships are automatically added to the design pane.</span></span>  
  
6.  <span data-ttu-id="7207b-223">在网格中添加一个新行。</span><span class="sxs-lookup"><span data-stu-id="7207b-223">Add a new row to the grid.</span></span> <span data-ttu-id="7207b-224">对于 "**源**"，请选择 "vAssocSeqOrders"，对于 "**字段**"，请选择 CustomerKey。</span><span class="sxs-lookup"><span data-stu-id="7207b-224">For **Source**, select vAssocSeqOrders, and for **Field**, select CustomerKey.</span></span>  
  
7.  <span data-ttu-id="7207b-225">在网格中添加一个新行。</span><span class="sxs-lookup"><span data-stu-id="7207b-225">Add a new row to the grid.</span></span> <span data-ttu-id="7207b-226">对于 "**源**"，选择 "**预测函数**"，为 "**字段**" 选择**PredictSequence**。</span><span class="sxs-lookup"><span data-stu-id="7207b-226">For **Source**, select **Prediction Function**, and for **Field**, select **PredictSequence**.</span></span>  
  
8.  <span data-ttu-id="7207b-227">将 vAssocSeqLineItems 拖到 "**条件/参数**" 框中。</span><span class="sxs-lookup"><span data-stu-id="7207b-227">Drag vAssocSeqLineItems, into the **Criteria/Argument** box.</span></span> <span data-ttu-id="7207b-228">单击 "**条件/参数**" 框的末尾，然后键入以下参数： `2` 。</span><span class="sxs-lookup"><span data-stu-id="7207b-228">Click at the end of the **Criteria/Argument** box and then type the following arguments: `2`.</span></span>  
  
     <span data-ttu-id="7207b-229">"**条件/参数**" 框中的完整文本应为：`[Sequence Clustering].[v Assoc Seq Line Items],2`</span><span class="sxs-lookup"><span data-stu-id="7207b-229">The complete text in the **Criteria/Argument** box should be: `[Sequence Clustering].[v Assoc Seq Line Items],2`</span></span>  
  
9. <span data-ttu-id="7207b-230">单击 "**结果**" 按钮，查看每个客户的预测。</span><span class="sxs-lookup"><span data-stu-id="7207b-230">Click the **Result** button to view the predictions for each customer.</span></span>  
  
 <span data-ttu-id="7207b-231">您已经完成关于顺序分析和聚类分析模型的教程。</span><span class="sxs-lookup"><span data-stu-id="7207b-231">You have completed the tutorial on sequence clustering models.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="7207b-232">后续步骤</span><span class="sxs-lookup"><span data-stu-id="7207b-232">Next Steps</span></span>  
 <span data-ttu-id="7207b-233">如果您已经完成了数据挖掘中的所有部分[&#40;Analysis Services 数据挖掘&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)，下一步就是了解如何使用数据挖掘扩展插件 (DMX) 语句来生成模型和生成预测。</span><span class="sxs-lookup"><span data-stu-id="7207b-233">If you have finished all the sections in the [Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md), the next step might be to learn to use Data Mining Extensions (DMX) statements to build models and generate predictions.</span></span> <span data-ttu-id="7207b-234">有关详细信息，请参阅[利用 DMX 创建和查询数据挖掘模型：教程 &#40;Analysis Services 数据挖掘&#41;](../../2014/tutorials/create-query-data-mining-models-dmx-tutorials.md)。</span><span class="sxs-lookup"><span data-stu-id="7207b-234">For more information, see [Creating and Querying Data Mining Models with DMX: Tutorials &#40;Analysis Services - Data Mining&#41;](../../2014/tutorials/create-query-data-mining-models-dmx-tutorials.md).</span></span>  
  
 <span data-ttu-id="7207b-235">如果您熟悉编程概念，您还可以使用分析管理对象 (AMO) 以编程方式处理数据挖掘对象。</span><span class="sxs-lookup"><span data-stu-id="7207b-235">If you are familiar with programming concepts, you can also use Analysis Management Objects (AMO) to programmatically work with data mining objects.</span></span> <span data-ttu-id="7207b-236">有关详细信息，请参阅 [AMO 数据挖掘类](https://docs.microsoft.com/bi-reference/amo/amo-data-mining-classes)。</span><span class="sxs-lookup"><span data-stu-id="7207b-236">For more information, see [AMO Data Mining Classes](https://docs.microsoft.com/bi-reference/amo/amo-data-mining-classes).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7207b-237">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7207b-237">See Also</span></span>  
 <span data-ttu-id="7207b-238">[顺序分析和聚类分析模型查询示例](../../2014/analysis-services/data-mining/sequence-clustering-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="7207b-238">[Sequence Clustering Model Query Examples](../../2014/analysis-services/data-mining/sequence-clustering-model-query-examples.md) </span></span>  
 [<span data-ttu-id="7207b-239">顺序分析和聚类分析模型的挖掘模型内容（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="7207b-239">Mining Model Content for Sequence Clustering Models &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/mining-model-content-for-sequence-clustering-models.md)  
  
  
