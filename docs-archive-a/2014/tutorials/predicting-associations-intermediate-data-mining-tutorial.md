---
title: 预测 (中级数据挖掘教程的关联) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 9140c5f2-b340-45a6-9c27-d870d15aafea
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: bee5ca4ded1b2fd5cbda0712cb766c825b9d0318
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577150"
---
# <a name="predicting-associations-intermediate-data-mining-tutorial"></a><span data-ttu-id="d0cbe-102">预测关联（数据挖掘中级教程）</span><span class="sxs-lookup"><span data-stu-id="d0cbe-102">Predicting Associations (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="d0cbe-103">在处理模型后，您可以使用模型中存储的关联的相关信息来创建预测。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-103">After the models have been processed, you can use the information about associations stored in the model to create predictions.</span></span> <span data-ttu-id="d0cbe-104">在本课程的最后一个任务中，您将了解如何针对所创建的关联模型生成预测查询。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-104">In the final task of this lesson, you learn how to build prediction queries against the association models that you created.</span></span> <span data-ttu-id="d0cbe-105">本课程假定您已经熟悉了如何使用预测查询生成器，同时希望了解如何生成针对关联模型的预测查询。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-105">This lesson assumes that you are familiar with how to use the Prediction Query Builder and want to learn how to build prediction queries against association models.</span></span> <span data-ttu-id="d0cbe-106">有关如何使用预测查询生成器的详细信息，请参阅[数据挖掘查询接口](../../2014/analysis-services/data-mining/data-mining-query-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-106">For more information how to use Prediction Query Builder, see [Data Mining Query Interfaces](../../2014/analysis-services/data-mining/data-mining-query-tools.md).</span></span>  
  
## <a name="creating-a-singleton-prediction-query"></a><span data-ttu-id="d0cbe-107">创建单独预测查询</span><span class="sxs-lookup"><span data-stu-id="d0cbe-107">Creating a Singleton Prediction Query</span></span>  
 <span data-ttu-id="d0cbe-108">针对关联模型的预测查询可能非常有用：</span><span class="sxs-lookup"><span data-stu-id="d0cbe-108">Prediction queries on an association model can be very useful:</span></span>  
  
-   <span data-ttu-id="d0cbe-109">基于以前或相关的采购，向客户提出物料方面的建议</span><span class="sxs-lookup"><span data-stu-id="d0cbe-109">Recommend items to a customer, based on prior or related purchases</span></span>  
  
-   <span data-ttu-id="d0cbe-110">查找相关事件。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-110">Find related events.</span></span>  
  
-   <span data-ttu-id="d0cbe-111">标识事务集中或事务集之间的关系。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-111">Identify relationships in or across sets of transactions.</span></span>  
  
 <span data-ttu-id="d0cbe-112">若要生成预测查询，请先选择要使用的关联模型，然后指定输入数据。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-112">To build a prediction query, you first select the association model you want to use, and then you specify the input data.</span></span> <span data-ttu-id="d0cbe-113">输入可以来自外部数据源（例如值列表），也可以生成单独查询并随时提供值。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-113">Inputs can come from an external data source, such as a list of values, or you can build a singleton query and provide values as you go.</span></span>  
  
 <span data-ttu-id="d0cbe-114">对此方案，您首先需要创建一些单独预测查询，以了解预测是如何运行的。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-114">For this scenario, you will first create some singleton prediction queries, to get an idea of how prediction works.</span></span> <span data-ttu-id="d0cbe-115">然后您将创建一个批预测的查询，以便根据客户当前的购买情况提出建议。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-115">Then you will create a query for batch predictions that you could use for making recommendations based on a customer's current purchases.</span></span>  
  
#### <a name="to-create-a-prediction-query-on-an-association-model"></a><span data-ttu-id="d0cbe-116">针对关联模型创建预测查询</span><span class="sxs-lookup"><span data-stu-id="d0cbe-116">To create a prediction query on an association model</span></span>  
  
1.  <span data-ttu-id="d0cbe-117">单击数据挖掘设计器的 "**挖掘模型预测**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-117">Click the **Mining Model Prediction** tab of Data Mining Designer.</span></span>  
  
2.  <span data-ttu-id="d0cbe-118">在 "**挖掘模型**" 窗格中单击 "**选择模型**"。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-118">In the **Mining Model** pane, click **Select Model**.</span></span> <span data-ttu-id="d0cbe-119">（如果已选择正确的模型，则可跳过此步骤和下一步骤。）</span><span class="sxs-lookup"><span data-stu-id="d0cbe-119">(You can skip this step and the next step if the correct model is already selected.)</span></span>  
  
3.  <span data-ttu-id="d0cbe-120">在 "**选择挖掘模型**" 对话框中，展开表示挖掘结构**关联**的节点，然后选择模型**关联**。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-120">In the **Select Mining Model** dialog box, expand the node that represents the mining structure **Association**, and select the model **Association**.</span></span> <span data-ttu-id="d0cbe-121">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-121">Click **OK**.</span></span>  
  
     <span data-ttu-id="d0cbe-122">现在，可以忽略“输入”窗格。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-122">For now, you can ignore the input pane.</span></span>  
  
4.  <span data-ttu-id="d0cbe-123">在网格中，单击 "**源**" 下的空单元格，然后选择 "**预测函数"。**</span><span class="sxs-lookup"><span data-stu-id="d0cbe-123">In the grid, click the empty cell under **Source** and select **Prediction Function.**</span></span> <span data-ttu-id="d0cbe-124">在 "**字段**" 下的单元中，选择 `PredictAssociation` 。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-124">In the cell under **Field**, select `PredictAssociation`.</span></span>  
  
     <span data-ttu-id="d0cbe-125">还可以使用**predict**函数预测关联。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-125">You can also use the **Predict** function to predict associations.</span></span> <span data-ttu-id="d0cbe-126">如果执行此操作，请确保选择采用表列作为参数的**Predict**函数的版本。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-126">If you do, be sure to choose the version of the **Predict** function that takes a table column as argument.</span></span>  
  
5.  <span data-ttu-id="d0cbe-127">在 "**挖掘模型**" 窗格中，选择嵌套表 `vAssocSeqLineItems` ，并将其拖到网格中的 "**条件/参数**" 框 `PredictAssociation` 。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-127">In the **Mining Model** pane, select the nested table `vAssocSeqLineItems`, and drag it into the grid, to the **Criteria/Argument** box for the `PredictAssociation` function.</span></span>  
  
     <span data-ttu-id="d0cbe-128">通过拖放表和列名称可以生成没有语法错误的复杂语句。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-128">Dragging and dropping table and column names lets you build complex statements without syntax errors.</span></span> <span data-ttu-id="d0cbe-129">但是，它将替换单元的当前内容，其中包括函数的其他可选参数 `PredictAssociation` 。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-129">However, it replaces the current contents of the cell, which include other optional arguments for the `PredictAssociation` function.</span></span> <span data-ttu-id="d0cbe-130">为了查看其他参数，可以将函数的另一个实例临时添加到网格供参考。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-130">To view the other arguments, you can temporarily add a second instance of the function to the grid for reference.</span></span>  
  
6.  <span data-ttu-id="d0cbe-131">单击 "**条件/参数**" 框，然后在表名称后面键入以下文本：`,3`</span><span class="sxs-lookup"><span data-stu-id="d0cbe-131">Click the **Criteria/Argument** box and type the following text after the table name: `,3`</span></span>  
  
     <span data-ttu-id="d0cbe-132">"**条件/参数**" 框中的完整文本应该如下所示：</span><span class="sxs-lookup"><span data-stu-id="d0cbe-132">The complete text in the **Criteria/Argument** box should be as follows:</span></span>  
  
     `[Association].[v Assoc Seq Line Items],3`  
  
7.  <span data-ttu-id="d0cbe-133">单击预测查询生成器上角的 "**结果**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-133">Click the **Results** button in the upper corner of the Prediction Query Builder.</span></span>  
  
 <span data-ttu-id="d0cbe-134">预期结果包含带有标题**表达式**的单个列。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-134">The expected results contain a single column with the heading **Expression**.</span></span> <span data-ttu-id="d0cbe-135">**Expression**列包含一个嵌套表，其中包含一个列和下面三行。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-135">The **Expression** column contains a nested table with a single column and the following three rows.</span></span> <span data-ttu-id="d0cbe-136">由于未指定输入值，因此这些预测表示整个模型最可能的产品关联。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-136">Because you did not specify an input value, these predictions represent the most likely product associations for the model as a whole.</span></span>  
  
|<span data-ttu-id="d0cbe-137">模型</span><span class="sxs-lookup"><span data-stu-id="d0cbe-137">Model</span></span>|  
|-----------|  
|<span data-ttu-id="d0cbe-138">Women's Mountain Shorts</span><span class="sxs-lookup"><span data-stu-id="d0cbe-138">Women's Mountain Shorts</span></span>|  
|<span data-ttu-id="d0cbe-139">Water Bottle</span><span class="sxs-lookup"><span data-stu-id="d0cbe-139">Water Bottle</span></span>|  
|<span data-ttu-id="d0cbe-140">Touring-3000</span><span class="sxs-lookup"><span data-stu-id="d0cbe-140">Touring-3000</span></span>|  
  
 <span data-ttu-id="d0cbe-141">接下来，您将使用 "**单独查询输入**" 窗格将产品指定为查询的输入，并查看最有可能与该项目关联的产品。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-141">Next, you will use the **Singleton Query Input** pane to specify a product as input to the query, and view the products that are most likely associated with that item.</span></span>  
  
#### <a name="to-create-a-singleton-prediction-query-with-nested-table-inputs"></a><span data-ttu-id="d0cbe-142">创建带有嵌套表输入的单独预测查询</span><span class="sxs-lookup"><span data-stu-id="d0cbe-142">To create a singleton prediction query with nested table inputs</span></span>  
  
1.  <span data-ttu-id="d0cbe-143">单击预测查询生成器角的 "**设计**" 按钮，切换回查询生成网格。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-143">Click the **Design** button in the corner of the Prediction Query Builder to switch back to the query building grid.</span></span>  
  
2.  <span data-ttu-id="d0cbe-144">在 "**挖掘模型**" 菜单上，选择 "**单独查询**"。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-144">On the **Mining Model** menu, select **Singleton Query**.</span></span>  
  
3.  <span data-ttu-id="d0cbe-145">在 "**挖掘模型**" 对话框中，选择 "**关联**模型"。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-145">In the **Mining Model** dialog box, select the **Association** model.</span></span>  
  
4.  <span data-ttu-id="d0cbe-146">在网格中，单击 "**源**" 下的空单元格，然后选择 "**预测函数"。**</span><span class="sxs-lookup"><span data-stu-id="d0cbe-146">In the grid, click the empty cell under **Source** and select **Prediction Function.**</span></span> <span data-ttu-id="d0cbe-147">在 "**字段**" 下的单元中，选择 `PredictAssociation` 。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-147">In the cell under **Field**, select `PredictAssociation`.</span></span>  
  
5.  <span data-ttu-id="d0cbe-148">在 "**挖掘模型**" 窗格中，选择嵌套表 `vAssocSeqLineItems` ，并将其拖到网格中的 "**条件/参数**" 框 `PredictAssociation` 。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-148">In the **Mining Model** pane, select the nested table `vAssocSeqLineItems`, and drag it into the grid, to the **Criteria/Argument** box for the `PredictAssociation` function.</span></span> <span data-ttu-id="d0cbe-149">在 `,3` 嵌套表名称后键入，就像在前面的过程中一样。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-149">Type `,3` after the nested table name just as in the previous procedure.</span></span>  
  
6.  <span data-ttu-id="d0cbe-150">在 "**单独查询输入**" 对话框中，单击 " **vAssoc Seq 项**" 旁边的 "**值**" 框，然后单击 " \*\* ( ... ) \*\* " 按钮。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-150">In the **Singleton Query Input** dialog box, click the **Value** box next to **vAssoc Seq Line Items**, and then click the **(...)** button.</span></span>  
  
7.  <span data-ttu-id="d0cbe-151">在 "**嵌套表输入**" 对话框中，在 `Touring Tire` "**键列**" 窗格中选择，然后单击 "**添加**"。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-151">In the **Nested Table Input** dialog box, select `Touring Tire` in the **Key column** pane, and then click **Add**.</span></span>  
  
8.  <span data-ttu-id="d0cbe-152">单击 "**结果**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-152">Click the **Results** button.</span></span>  
  
 <span data-ttu-id="d0cbe-153">现在结果显示最可能与 Touring Tire 关联的产品的预测。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-153">The results now show the predictions for products that are most likely associated with the Touring Tire.</span></span>  
  
|<span data-ttu-id="d0cbe-154">模型</span><span class="sxs-lookup"><span data-stu-id="d0cbe-154">Model</span></span>|  
|-----------|  
|<span data-ttu-id="d0cbe-155">Touring Tire Tube</span><span class="sxs-lookup"><span data-stu-id="d0cbe-155">Touring Tire Tube</span></span>|  
|<span data-ttu-id="d0cbe-156">Sport-100</span><span class="sxs-lookup"><span data-stu-id="d0cbe-156">Sport-100</span></span>|  
|<span data-ttu-id="d0cbe-157">Water Bottle</span><span class="sxs-lookup"><span data-stu-id="d0cbe-157">Water Bottle</span></span>|  
  
 <span data-ttu-id="d0cbe-158">但是，您已经通过浏览模型了解到，客户经常同时购买 Touring Tire 和 Touring Tire Tube；您更愿意了解您能够向同时购买这些商品的客户推荐哪些产品。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-158">However, you already know from exploring the model that the Touring Tire Tube is frequently purchased with the Touring Tire; you are more interested in knowing what products you can recommend to customers who purchase these items together.</span></span> <span data-ttu-id="d0cbe-159">您将更改查询以便根据市场篮中的两个项目预测相关产品。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-159">You will change the query so that it predicts related products based on two items in the basket.</span></span> <span data-ttu-id="d0cbe-160">您还将修改查询以添加所有预测产品的概率。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-160">You will also modify the query to add the probability for each predicted product.</span></span>  
  
#### <a name="to-add-inputs-and-probabilities-to-the-singleton-prediction-query"></a><span data-ttu-id="d0cbe-161">向单独预测查询添加输入和概率</span><span class="sxs-lookup"><span data-stu-id="d0cbe-161">To add inputs and probabilities to the singleton prediction query</span></span>  
  
1.  <span data-ttu-id="d0cbe-162">单击预测查询生成器角的 "**设计**" 按钮，切换回查询生成网格。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-162">Click the **Design** button in the corner of the Prediction Query Builder to switch back to the query building grid.</span></span>  
  
2.  <span data-ttu-id="d0cbe-163">在 "**单独查询输入**" 对话框中，单击 " **vAssoc Seq 项**" 旁边的 "**值**" 框，然后单击 " \*\* ( ... ) \*\* " 按钮。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-163">In the **Singleton Query Input** dialog box, click the **Value** box next to **vAssoc Seq Line Items**, and then click the **(...)** button.</span></span>  
  
3.  <span data-ttu-id="d0cbe-164">在 "**键列**" 窗格中，选择 `Touring Tire` ，然后单击 "**添加**"。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-164">In the **Key column** pane, select `Touring Tire`, and then click **Add**.</span></span>  
  
4.  <span data-ttu-id="d0cbe-165">在网格中，单击 "**源**" 下的空单元格，然后选择 "**预测函数"。**</span><span class="sxs-lookup"><span data-stu-id="d0cbe-165">In the grid, click the empty cell under **Source** and select **Prediction Function.**</span></span> <span data-ttu-id="d0cbe-166">在 "**字段**" 下的单元中，选择 `PredictAssociation` 。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-166">In the cell under **Field**, select `PredictAssociation`.</span></span>  
  
5.  <span data-ttu-id="d0cbe-167">在 "**挖掘模型**" 窗格中，选择嵌套表 `vAssocSeqLineItems` ，并将其拖到网格中的 "**条件/参数**" 框 `PredictAssociation` 。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-167">In the **Mining Model** pane, select the nested table `vAssocSeqLineItems`, and drag it into the grid, to the **Criteria/Argument** box for the `PredictAssociation` function.</span></span> <span data-ttu-id="d0cbe-168">在 `,3` 嵌套表名称后键入，就像在前面的过程中一样。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-168">Type `,3` after the nested table name just as in the previous procedure.</span></span>  
  
6.  <span data-ttu-id="d0cbe-169">在 "**嵌套表输入**" 对话框中，在 `Touring Tire Tube` "**键列**" 窗格中选择，然后单击 "**添加**"。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-169">In the **Nested Table Input** dialog box, select `Touring Tire Tube` in the **Key column** pane, and then click **Add**.</span></span>  
  
7.  <span data-ttu-id="d0cbe-170">在网格的函数行中 `PredictAssociation` ，单击 "**条件/参数**" 框，然后更改参数以添加参数，INCLUDE_STATISTICS。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-170">In the grid, in the row for the `PredictAssociation` function, click the **Criteria/Argument** box, and change the arguments to add the argument, INCLUDE_STATISTICS.</span></span>  
  
     <span data-ttu-id="d0cbe-171">"**条件/参数**" 框中的完整文本应该如下所示：</span><span class="sxs-lookup"><span data-stu-id="d0cbe-171">The complete text in the **Criteria/Argument** box should be as follows:</span></span>  
  
     `[Association].[v Assoc Seq Line Items], INCLUDE_STATISTICS, 3`  
  
8.  <span data-ttu-id="d0cbe-172">单击 "**结果**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-172">Click the **Results** button.</span></span>  
  
 <span data-ttu-id="d0cbe-173">嵌套表中的结果现在更改为同时显示支持率和概率的预测。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-173">The results in the nested table now change to show the predictions, together with support and probability.</span></span> <span data-ttu-id="d0cbe-174">有关如何解释这些值的详细信息，请参阅[&#40;Analysis Services 数据挖掘&#41;的关联模型的挖掘模型内容](../../2014/analysis-services/data-mining/mining-model-content-for-association-models-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-174">For more information about how to interpret these values, see [Mining Model Content for Association Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-association-models-analysis-services-data-mining.md).</span></span>  
  
|<span data-ttu-id="d0cbe-175">模型</span><span class="sxs-lookup"><span data-stu-id="d0cbe-175">Model</span></span>|<span data-ttu-id="d0cbe-176">$SUPPORT</span><span class="sxs-lookup"><span data-stu-id="d0cbe-176">$SUPPORT</span></span>|<span data-ttu-id="d0cbe-177">$PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="d0cbe-177">$PROBABILITY</span></span>|<span data-ttu-id="d0cbe-178">$ADJUSTEDPROBABILITY</span><span class="sxs-lookup"><span data-stu-id="d0cbe-178">$ADJUSTEDPROBABILITY</span></span>|  
|-----------|--------------|------------------|--------------------------|  
|<span data-ttu-id="d0cbe-179">Sport-100</span><span class="sxs-lookup"><span data-stu-id="d0cbe-179">Sport-100</span></span>|<span data-ttu-id="d0cbe-180">4334</span><span class="sxs-lookup"><span data-stu-id="d0cbe-180">4334</span></span>|<span data-ttu-id="d0cbe-181">0.291 .。。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-181">0.291...</span></span>|<span data-ttu-id="d0cbe-182">0.252 .。。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-182">0.252...</span></span>|  
|<span data-ttu-id="d0cbe-183">Water Bottle</span><span class="sxs-lookup"><span data-stu-id="d0cbe-183">Water Bottle</span></span>|<span data-ttu-id="d0cbe-184">2866</span><span class="sxs-lookup"><span data-stu-id="d0cbe-184">2866</span></span>|<span data-ttu-id="d0cbe-185">0.192 .。。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-185">0.192...</span></span>|<span data-ttu-id="d0cbe-186">0.175 .。。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-186">0.175...</span></span>|  
|<span data-ttu-id="d0cbe-187">Patch Kit</span><span class="sxs-lookup"><span data-stu-id="d0cbe-187">Patch Kit</span></span>|<span data-ttu-id="d0cbe-188">2113</span><span class="sxs-lookup"><span data-stu-id="d0cbe-188">2113</span></span>|<span data-ttu-id="d0cbe-189">0.142 .。。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-189">0.142...</span></span>|<span data-ttu-id="d0cbe-190">0.132</span><span class="sxs-lookup"><span data-stu-id="d0cbe-190">0.132</span></span>|  
  
## <a name="working-with-results"></a><span data-ttu-id="d0cbe-191">使用结果</span><span class="sxs-lookup"><span data-stu-id="d0cbe-191">Working with Results</span></span>  
 <span data-ttu-id="d0cbe-192">如果结果中有很多嵌套表，您可能希望简化结果以便查看。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-192">When there are many nested tables in the results, you might want to flatten the results for easier viewing.</span></span> <span data-ttu-id="d0cbe-193">为此，您可以手动修改查询并添加 `FLATTENED` 关键字。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-193">To do this, you can manually modify the query and add the `FLATTENED` keyword.</span></span>  
  
#### <a name="to-flatten-nested-rowsets-in-a-prediction-query"></a><span data-ttu-id="d0cbe-194">平展预测查询中的嵌套行集</span><span class="sxs-lookup"><span data-stu-id="d0cbe-194">To flatten nested rowsets in a prediction query</span></span>  
  
1.  <span data-ttu-id="d0cbe-195">单击预测查询生成器角的 " **SQL** " 按钮。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-195">Click the **SQL** button in the corner of the Prediction Query Builder.</span></span>  
  
     <span data-ttu-id="d0cbe-196">网格更改为一个打开的窗格，在此您可以查看和修改由预测查询生成器创建的 DMX 语句。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-196">The grid changes to an open pane where you can view and modify the DMX statement that was created by the Prediction Query Builder.</span></span>  
  
2.  <span data-ttu-id="d0cbe-197">在 `SELECT` 关键字后键入 `FLATTENED`。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-197">After the `SELECT` keyword, type `FLATTENED`.</span></span>  
  
     <span data-ttu-id="d0cbe-198">查询的完整文本应该如下所示：</span><span class="sxs-lookup"><span data-stu-id="d0cbe-198">The complete text of the query should be as follows:</span></span>  
  
    ```  
    SELECT FLATTENED  
      PredictAssociation([Association].[v Assoc Seq Line Items],INCLUDE_STATISTICS,3)  
    FROM  
      [Association]  
    NATURAL PREDICTION JOIN  
    (SELECT (SELECT 'Touring Tire' AS [Model]  
      UNION SELECT 'Touring Tire Tube' AS [Model]) AS [v Assoc Seq Line Items]) AS t  
    ```  
  
3.  <span data-ttu-id="d0cbe-199">单击预测查询生成器上角的 "**结果**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-199">Click the **Results** button in the upper corner of the Prediction Query Builder.</span></span>  
  
 <span data-ttu-id="d0cbe-200">请注意，手动编辑查询之后，将无法切换回设计视图而不丢失更改。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-200">Note that after you have manually edited a query, you will not be able to switch back to Design view without losing the changes.</span></span> <span data-ttu-id="d0cbe-201">如果希望保存查询，可以将创建的 DMX 语句手动复制到一个文本文件中。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-201">If you wish to save the query, you can copy the DMX statement that you created manually to a text file.</span></span> <span data-ttu-id="d0cbe-202">更改回设计视图后，查询会恢复到设计视图中有效的上一版本。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-202">When you change back to Design view, the query is reverted to the last version that was valid in Design view.</span></span>  
  
## <a name="creating-multiple-predictions"></a><span data-ttu-id="d0cbe-203">创建多个预测</span><span class="sxs-lookup"><span data-stu-id="d0cbe-203">Creating Multiple Predictions</span></span>  
 <span data-ttu-id="d0cbe-204">假设您希望根据以往的购买情况了解每个客户的最佳预测。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-204">Suppose you want to know the best predictions for individual customers, based on past purchases.</span></span> <span data-ttu-id="d0cbe-205">您可以使用外部数据作为预测查询的输入，例如包含客户 ID 和最近产品购买情况的表。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-205">You can use external data as input to the prediction query, such as tables containing the customer ID and the most recent product purchases.</span></span> <span data-ttu-id="d0cbe-206">要求是，这些数据表已经定义为 Analysis Services 数据源视图；而且输入数据必须包含事例和类似模型中使用的嵌套表。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-206">The requirements are that the data tables be already defined as an Analysis Services data source view; moreover, the input data must contain case and nested tables like those used in the model.</span></span> <span data-ttu-id="d0cbe-207">不需要相同的名称，但结构必须相似。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-207">They need not have the same names, but the structure must be similar.</span></span> <span data-ttu-id="d0cbe-208">为了实现本教程教学目的，您将使用对模型进行定型的原始表。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-208">For the purpose of this tutorial, you will use the original tables on which the model was trained.</span></span>  
  
#### <a name="to-change-the-input-method-for-the-prediction-query"></a><span data-ttu-id="d0cbe-209">更改预测查询的输入方法</span><span class="sxs-lookup"><span data-stu-id="d0cbe-209">To change the input method for the prediction query</span></span>  
  
1.  <span data-ttu-id="d0cbe-210">在 "**挖掘模型**" 菜单中，再次选择 "**单独查询**" 以清除复选标记。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-210">In the **Mining Model** menu, select **Singleton Query** again, to clear the check mark.</span></span>  
  
2.  <span data-ttu-id="d0cbe-211">出现一条错误消息警告您单独查询将丢失。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-211">An error message appears warning that your singleton query will be lost.</span></span> <span data-ttu-id="d0cbe-212">单击 **“是”** 。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-212">Click **Yes**.</span></span>  
  
     <span data-ttu-id="d0cbe-213">输入对话框的名称将更改为 "\*\*选择输入表 (s) \*\*。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-213">The name of the input dialog box changes to **Select Input Table(s)**.</span></span>  
  
 <span data-ttu-id="d0cbe-214">您希望创建一个预测查询，以将客户 ID 和产品列表作为输入，因此需要将客户表添加为事例表，将采购表添加为嵌套表。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-214">Because you are interested in creating a prediction query that provides Customer ID and a list of products as input, you will add the customer table as the case table, and the purchases table as the nested table.</span></span> <span data-ttu-id="d0cbe-215">然后您将添加预测函数来创建建议。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-215">Then you will add prediction functions to create recommendations.</span></span>  
  
#### <a name="to-create-a-prediction-query-using-nested-table-inputs"></a><span data-ttu-id="d0cbe-216">使用嵌套表输入创建预测查询</span><span class="sxs-lookup"><span data-stu-id="d0cbe-216">To create a prediction query using nested table inputs</span></span>  
  
1.  <span data-ttu-id="d0cbe-217">在“挖掘模型”窗格中选择 Association Filtered 模型。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-217">In the Mining Model pane, select the Association Filtered model.</span></span>  
  
2.  <span data-ttu-id="d0cbe-218">在 "**选择输入表 (s) \*\* " 对话框中，单击 "**选择事例表\*\*"。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-218">In the **Select Input Table(s)** dialog box, click **Select Case Table**.</span></span>  
  
3.  <span data-ttu-id="d0cbe-219">在 "**选择表**" 对话框中，选择 "AdventureWorksDW2008" 作为 "**数据源**"。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-219">In the **Select Table** dialog box, for **Data Source**, select AdventureWorksDW2008.</span></span> <span data-ttu-id="d0cbe-220">在 "**表/视图名称**" 列表中，选择 "vAssocSeqOrders"，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-220">In the **Table/View Name** list, select vAssocSeqOrders, and then click **OK**.</span></span>  
  
     <span data-ttu-id="d0cbe-221">将表 vAssocSeqOrders 添加到窗格中。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-221">The table vAssocSeqOrders is added to the pane.</span></span>  
  
4.  <span data-ttu-id="d0cbe-222">在 "**选择输入表 (s) \*\* " 对话框中，单击 "**选择嵌套表\*\*"。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-222">In the **Select Input Table(s)** dialog box, click **Select Nested Table**.</span></span>  
  
5.  <span data-ttu-id="d0cbe-223">在 "**选择表**" 对话框中，选择 "AdventureWorksDW2008" 作为 "**数据源**"。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-223">In the **Select Table** dialog box, for **Data Source**, select AdventureWorksDW2008.</span></span> <span data-ttu-id="d0cbe-224">在 "**表/视图名称**" 列表中，选择 "vAssocSeqLineItems"，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-224">In the **Table/View name** list, select vAssocSeqLineItems, and then click **OK**.</span></span>  
  
     <span data-ttu-id="d0cbe-225">将表 vAssocSeqLineItems 添加到窗格中。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-225">The table vAssocSeqLineItems is added to the pane.</span></span>  
  
6.  <span data-ttu-id="d0cbe-226">在 "**指定嵌套联接**" 对话框中，将 "OrderNumber" 字段从事例表拖放到嵌套表中的 "OrderNumber" 字段。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-226">In the **Specify Nested Join** dialog box, drag the OrderNumber field from the case table and drop it onto the OrderNumber field in the nested table.</span></span>  
  
     <span data-ttu-id="d0cbe-227">您还可以单击 "**添加关系**" 并通过从列表中选择列来创建关系。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-227">You can also click **Add Relationship** and create the relationship by selecting columns from a list.</span></span>  
  
7.  <span data-ttu-id="d0cbe-228">在 "**指定关系**" 对话框中，验证 OrderNumber 字段是否已正确映射，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-228">In the **Specify Relationship** dialog box, verify that the OrderNumber fields are mapped correctly, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="d0cbe-229">单击 **"确定"** 以关闭 "**指定嵌套联接**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-229">Click **OK** to close the **Specify Nested Join** dialog box.</span></span>  
  
     <span data-ttu-id="d0cbe-230">在“设计”窗格中将更新事例表和嵌套表，显示将外部数据列连接到模型中的列的联接。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-230">The case and nested tables are updated in the design pane to show the joins connecting the external data columns to the columns in the model.</span></span> <span data-ttu-id="d0cbe-231">如果关系错误，您可以右键单击联接线并选择 "**修改连接**" 来编辑列映射，或者右键单击联接线并选择 "**删除**" 以完全删除该关系。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-231">If the relationships are wrong, you can right-click the join line and select **Modify Connections** to edit the column mapping, or you can right-click the join line and select **Delete** to remove the relationship completely.</span></span>  
  
9. <span data-ttu-id="d0cbe-232">在网格中添加一个新行。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-232">Add a new row to the grid.</span></span> <span data-ttu-id="d0cbe-233">对于 "**源**"，选择 " **vAssocSeqOrders 表**"。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-233">For **Source**, select **vAssocSeqOrders table**.</span></span> <span data-ttu-id="d0cbe-234">对于 "**字段**"，请选择 CustomerKey。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-234">For **Field**, select CustomerKey.</span></span>  
  
10. <span data-ttu-id="d0cbe-235">在网格中添加一个新行。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-235">Add a new row to the grid.</span></span> <span data-ttu-id="d0cbe-236">对于 "**源**"，选择 " **vAssocSeqOrders 表**"。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-236">For **Source**, select **vAssocSeqOrders table**.</span></span> <span data-ttu-id="d0cbe-237">对于 "**字段**"，选择 "区域"。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-237">For **Field**, select Region.</span></span>  
  
11. <span data-ttu-id="d0cbe-238">在网格中添加一个新行。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-238">Add a new row to the grid.</span></span> <span data-ttu-id="d0cbe-239">对于 "**源**"，选择 "**预测函数**"，为 "**字段**" 选择 `PredictAssociation` 。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-239">For **Source**, select **Prediction Function**, and for **Field**, select `PredictAssociation`.</span></span>  
  
12. <span data-ttu-id="d0cbe-240">将 vAssocSeqLineItems 拖到行的 "**条件/参数**" 框中 `PredictAssociation` 。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-240">Drag vAssocSeqLineItems, into the **Criteria/Argument** box of the `PredictAssociation` row.</span></span> <span data-ttu-id="d0cbe-241">单击 "**条件/参数**" 框的末尾，然后键入以下文本：`INCLUDE_STATISTICS,3`</span><span class="sxs-lookup"><span data-stu-id="d0cbe-241">Click at the end of the **Criteria/Argument** box and then type the following text: `INCLUDE_STATISTICS,3`</span></span>  
  
     <span data-ttu-id="d0cbe-242">"**条件/参数**" 框中的完整文本应为：`[Association].[v Assoc Seq Line Items], INCLUDE_STATISTICS, 3`</span><span class="sxs-lookup"><span data-stu-id="d0cbe-242">The complete text in the **Criteria/Argument** box should be: `[Association].[v Assoc Seq Line Items], INCLUDE_STATISTICS, 3`</span></span>  
  
13. <span data-ttu-id="d0cbe-243">单击 "**结果**" 按钮，查看每个客户的预测。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-243">Click the **Result** button to view the predictions for each customer.</span></span>  
  
 <span data-ttu-id="d0cbe-244">您可以尝试针对多个模型创建一个相似的预测查询，来查看筛选是否会更改预测结果。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-244">You might try creating a similar prediction query on the multiple models, to see whether filtering changes the prediction results.</span></span> <span data-ttu-id="d0cbe-245">有关创建预测和其他类型查询的详细信息，请参阅[关联模型查询示例](../../2014/analysis-services/data-mining/association-model-query-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="d0cbe-245">For more information about creating predictions and other types of queries, see [Association Model Query Examples](../../2014/analysis-services/data-mining/association-model-query-examples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0cbe-246">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d0cbe-246">See Also</span></span>  
 <span data-ttu-id="d0cbe-247">[关联模型的挖掘模型内容 &#40;Analysis Services 数据挖掘&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-association-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="d0cbe-247">[Mining Model Content for Association Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-association-models-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="d0cbe-248">[PredictAssociation &#40;DMX&#41;](/sql/dmx/predictassociation-dmx) </span><span class="sxs-lookup"><span data-stu-id="d0cbe-248">[PredictAssociation &#40;DMX&#41;](/sql/dmx/predictassociation-dmx) </span></span>  
 [<span data-ttu-id="d0cbe-249">使用预测查询生成器创建预测查询</span><span class="sxs-lookup"><span data-stu-id="d0cbe-249">Create a Prediction Query Using the Prediction Query Builder</span></span>](../../2014/analysis-services/data-mining/create-a-prediction-query-using-the-prediction-query-builder.md)  
  
  
