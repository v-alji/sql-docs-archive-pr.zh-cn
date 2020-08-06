---
title: 测试筛选的模型 (基本数据挖掘教程) |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f0d74f8c-600d-4df5-a742-695e6947a071
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a97b5ca3523d1fc73405baba52b179a9bef04767
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577122"
---
# <a name="testing-a-filtered-model-basic-data-mining-tutorial"></a><span data-ttu-id="887bb-102">测试筛选后的模型（数据挖掘基础教程）</span><span class="sxs-lookup"><span data-stu-id="887bb-102">Testing a Filtered Model (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="887bb-103">现在您已确定该 `TM_Decision_Tree` 模型是最准确的模型，您将自定义该模型以更好地满足 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 目标邮件市场活动的需要。</span><span class="sxs-lookup"><span data-stu-id="887bb-103">Now that you have determined that the `TM_Decision_Tree` model is the most accurate, you will customize the model to better suit the needs of the [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] targeted mailing campaign.</span></span> <span data-ttu-id="887bb-104">具体来说，市场部希望了解男客户和女客户是否存在特征差异。</span><span class="sxs-lookup"><span data-stu-id="887bb-104">Specifically, the Marketing department would like to know if there are any differences between male and female customers.</span></span> <span data-ttu-id="887bb-105">这些信息可帮助他们决定使用哪些杂志进行广告宣传，以及在邮件中推广哪些产品。</span><span class="sxs-lookup"><span data-stu-id="887bb-105">The information could help them decide which magazines to use for advertising and which products to feature in their mailings.</span></span>  
  
## <a name="using-filters"></a><span data-ttu-id="887bb-106">使用筛选器</span><span class="sxs-lookup"><span data-stu-id="887bb-106">Using Filters</span></span>  
 <span data-ttu-id="887bb-107">通过筛选，您可以轻松地创建基于数据子集生成的模型。</span><span class="sxs-lookup"><span data-stu-id="887bb-107">Filtering enables you to easily create models built on subsets of your data.</span></span> <span data-ttu-id="887bb-108">筛选器只应用于该模型，而且不会更改基础数据源。</span><span class="sxs-lookup"><span data-stu-id="887bb-108">The filter is applied only to the model and does not change the underlying data source.</span></span>  
  
 <span data-ttu-id="887bb-109">在本课中，您将创建一个针对性别进行了筛选的模型，以预测男性和女性中对自行车购买行为影响最大的特征。</span><span class="sxs-lookup"><span data-stu-id="887bb-109">In this lesson, you will create a model that is filtered on gender, to predict the characteristics that most influence buying behavior in males and female.</span></span>  
  
 <span data-ttu-id="887bb-110">首先，您将创建模型的副本 `TM_Decision_Tree` 。</span><span class="sxs-lookup"><span data-stu-id="887bb-110">First you will make a copy of the `TM_Decision_Tree` model.</span></span>  
  
#### <a name="to-copy-the-decision-tree-model"></a><span data-ttu-id="887bb-111">复制决策树模型</span><span class="sxs-lookup"><span data-stu-id="887bb-111">To copy the Decision Tree Model</span></span>  
  
1.  <span data-ttu-id="887bb-112">在的 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 解决方案资源管理器中，选择 " **BasicDataMining**"。</span><span class="sxs-lookup"><span data-stu-id="887bb-112">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], in Solution Explorer, select **BasicDataMining**.</span></span>  
  
2.  <span data-ttu-id="887bb-113">单击 **“挖掘模型”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="887bb-113">Click the **Mining Models** tab.</span></span>  
  
3.  <span data-ttu-id="887bb-114">右键单击该 `TM_Decision_Tree` 模型，然后选择 "**新建挖掘模型"。**</span><span class="sxs-lookup"><span data-stu-id="887bb-114">Right click the `TM_Decision_Tree` model, and select **New Mining Model.**</span></span>  
  
4.  <span data-ttu-id="887bb-115">在 "**模型名称**" 字段中，键入 `TM_Decision_Tree_Male` 。</span><span class="sxs-lookup"><span data-stu-id="887bb-115">In the **Model name** field, type `TM_Decision_Tree_Male`.</span></span>  
  
5.  <span data-ttu-id="887bb-116">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="887bb-116">Click **OK**.</span></span>  
  
 <span data-ttu-id="887bb-117">然后为模型创建一个筛选器，用于根据客户的性别选择客户。</span><span class="sxs-lookup"><span data-stu-id="887bb-117">Next, create a filter to select customers for the model based on their gender.</span></span>  
  
#### <a name="to-create-a-case-filter-on-a-mining-model"></a><span data-ttu-id="887bb-118">创建挖掘模型的事例筛选器</span><span class="sxs-lookup"><span data-stu-id="887bb-118">To create a case filter on a mining model</span></span>  
  
1.  <span data-ttu-id="887bb-119">右键单击 `TM_Decision_Tree_Male` 挖掘模型以打开快捷菜单。</span><span class="sxs-lookup"><span data-stu-id="887bb-119">Right-click the `TM_Decision_Tree_Male` mining model to open the shortcut menu.</span></span>  
  
     <span data-ttu-id="887bb-120">- 或 -</span><span class="sxs-lookup"><span data-stu-id="887bb-120">-- or --</span></span>  
  
     <span data-ttu-id="887bb-121">选择该模型。</span><span class="sxs-lookup"><span data-stu-id="887bb-121">Select the model.</span></span> <span data-ttu-id="887bb-122">在 **“挖掘模型”** 菜单上，选择 **“设置模型筛选器”**。</span><span class="sxs-lookup"><span data-stu-id="887bb-122">On the **Mining Model** menu, select **Set Model Filter**.</span></span>  
  
2.  <span data-ttu-id="887bb-123">在 **“模型筛选器”** 对话框的 **“挖掘结构列”** 文本框中，单击网格中的第一行。</span><span class="sxs-lookup"><span data-stu-id="887bb-123">In the **Model Filter** dialog box, click the top row in the grid, in the **Mining Structure Column** text box.</span></span>  
  
     <span data-ttu-id="887bb-124">下拉列表只显示该表中列的名称。</span><span class="sxs-lookup"><span data-stu-id="887bb-124">The drop-down list displays only the names of the columns in that table.</span></span>  
  
3.  <span data-ttu-id="887bb-125">在 "挖掘结构列" 文本框中，选择 "**性别**"。</span><span class="sxs-lookup"><span data-stu-id="887bb-125">In the Mining Structure Column text box, select **Gender**.</span></span>  
  
     <span data-ttu-id="887bb-126">文本框左侧的图标会发生改变，以指示所选项是表还是列。</span><span class="sxs-lookup"><span data-stu-id="887bb-126">The icon at the left side of the text box changes to indicate that the selected item is a table or a column.</span></span>  
  
4.  <span data-ttu-id="887bb-127">单击 "**运算符**" 文本框，然后从列表中选择等于 (=) 运算符。</span><span class="sxs-lookup"><span data-stu-id="887bb-127">Click the **Operator** text box and select the equal (=) operator from the list.</span></span>  
  
5.  <span data-ttu-id="887bb-128">单击 "**值**" 文本框，然后键入**M**。</span><span class="sxs-lookup"><span data-stu-id="887bb-128">Click the **Value** text box, and type **M**.</span></span>  
  
6.  <span data-ttu-id="887bb-129">单击网格中的下一行。</span><span class="sxs-lookup"><span data-stu-id="887bb-129">Click the next row in the grid.</span></span>  
  
7.  <span data-ttu-id="887bb-130">单击 **"确定"** 以关闭 "**模型筛选器**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="887bb-130">Click **OK** to close the **Model Filter** dialog box.</span></span>  
  
     <span data-ttu-id="887bb-131">筛选器显示在 "**属性**" 窗口中。</span><span class="sxs-lookup"><span data-stu-id="887bb-131">The filter displays in the **Properties** window.</span></span> <span data-ttu-id="887bb-132">或者，您可以从 "**属性**" 窗口启动 "**模型筛选器**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="887bb-132">Alternately, you can launch the **Model Filter** dialog from the **Properties** window.</span></span>  
  
8.  <span data-ttu-id="887bb-133">重复上述步骤，但这次在 `TM_Decision_Tree_Female` "**值**" 文本框中命名模型和类型 " **F** "。</span><span class="sxs-lookup"><span data-stu-id="887bb-133">Repeat the above steps, but this time name the model `TM_Decision_Tree_Female` and type **F** in the **Value** text box.</span></span>  
  
## <a name="process-the-filtered-models"></a><span data-ttu-id="887bb-134">处理筛选的模型</span><span class="sxs-lookup"><span data-stu-id="887bb-134">Process the Filtered Models</span></span>  
 <span data-ttu-id="887bb-135">模型经过部署和处理后才能使用。</span><span class="sxs-lookup"><span data-stu-id="887bb-135">Models cannot be used until they have been deployed and processed.</span></span> <span data-ttu-id="887bb-136">有关处理模型的详细信息，请参阅[&#40;基本数据挖掘教程&#41;中的处理目标邮件结构中的模型](../../2014/tutorials/processing-models-in-the-targeted-mailing-structure-basic-data-mining-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="887bb-136">For more information on processing models, see [Processing Models in the Targeted Mailing Structure &#40;Basic Data Mining Tutorial&#41;](../../2014/tutorials/processing-models-in-the-targeted-mailing-structure-basic-data-mining-tutorial.md).</span></span>  
  
#### <a name="to-process-the-filtered-model"></a><span data-ttu-id="887bb-137">处理筛选后的模型</span><span class="sxs-lookup"><span data-stu-id="887bb-137">To process the filtered model</span></span>  
  
1.  <span data-ttu-id="887bb-138">右键单击该 `TM_Decision_Tree_Male` 模型，然后选择 "**处理挖掘结构和所有模型**"</span><span class="sxs-lookup"><span data-stu-id="887bb-138">Right-click the `TM_Decision_Tree_Male` model and select **Process Mining Structure and all Model**s</span></span>  
  
2.  <span data-ttu-id="887bb-139">单击 "**运行**" 以处理新模型。</span><span class="sxs-lookup"><span data-stu-id="887bb-139">Click **Run** to process the new models.</span></span>  
  
3.  <span data-ttu-id="887bb-140">处理完成后，单击 "处理" 窗口中的 "**关闭**"。</span><span class="sxs-lookup"><span data-stu-id="887bb-140">After processing is complete, click **Close** on both processing windows.</span></span>  
  
     <span data-ttu-id="887bb-141">你现在可以在 "**挖掘模型**" 选项卡中显示两个新模型。</span><span class="sxs-lookup"><span data-stu-id="887bb-141">You now have two new models displayed in the **Mining Models** tab.</span></span>  
  
## <a name="evaluate-the-results"></a><span data-ttu-id="887bb-142">评估结果</span><span class="sxs-lookup"><span data-stu-id="887bb-142">Evaluate the Results</span></span>  
 <span data-ttu-id="887bb-143">查看结果并评估筛选后的模型的准确性，与您对前三个模型的操作非常相似。</span><span class="sxs-lookup"><span data-stu-id="887bb-143">View the results and assess the accuracy of the filtered models in much the same way as you did for the previous three models.</span></span> <span data-ttu-id="887bb-144">有关详细信息，请参见:</span><span class="sxs-lookup"><span data-stu-id="887bb-144">For more information, see:</span></span>  
  
 [<span data-ttu-id="887bb-145">浏览决策树模型 &#40;基本数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="887bb-145">Exploring the Decision Tree Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
 [<span data-ttu-id="887bb-146">测试提升图的准确性（数据挖掘基础教程）</span><span class="sxs-lookup"><span data-stu-id="887bb-146">Testing Accuracy with Lift Charts &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)  
  
#### <a name="to-explore-the-filtered-models"></a><span data-ttu-id="887bb-147">浏览筛选后的模型</span><span class="sxs-lookup"><span data-stu-id="887bb-147">To explore the filtered models</span></span>  
  
1.  <span data-ttu-id="887bb-148">在**数据挖掘设计器**中选择 "**挖掘模型查看器**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="887bb-148">Select the **Mining Model Viewer** tab in **Data Mining Designer**.</span></span>  
  
2.  <span data-ttu-id="887bb-149">在 "挖掘模型" 框中，选择 `TM_Decision_Tree_Male` 。</span><span class="sxs-lookup"><span data-stu-id="887bb-149">In the Mining Model box, select `TM_Decision_Tree_Male`.</span></span>  
  
3.  <span data-ttu-id="887bb-150">将**显示级别**幻灯片 `3` 。</span><span class="sxs-lookup"><span data-stu-id="887bb-150">Slide **Show Level** to `3`.</span></span>  
  
4.  <span data-ttu-id="887bb-151">将 "**背景**" 值更改为 `1` 。</span><span class="sxs-lookup"><span data-stu-id="887bb-151">Change the **Background** value to `1`.</span></span>  
  
5.  <span data-ttu-id="887bb-152">将光标置于标记为 "**全部**" 的节点上，以查看自行车购买者和非自行车购买者的数量。</span><span class="sxs-lookup"><span data-stu-id="887bb-152">Place your cursor over the node labeled **All** to see the number of bike buyers versus non-bike buyers.</span></span>  
  
6.  <span data-ttu-id="887bb-153">对执行步骤 1-5 `TM_Decision_Tree_Female` 。</span><span class="sxs-lookup"><span data-stu-id="887bb-153">Repeat steps 1 - 5 for `TM_Decision_Tree_Female`.</span></span>  
  
7.  <span data-ttu-id="887bb-154">浏览的结果和为 `TM_Decision_Tree` 性别筛选的模型。</span><span class="sxs-lookup"><span data-stu-id="887bb-154">Explore the results for the `TM_Decision_Tree` and the models filtered for gender.</span></span> <span data-ttu-id="887bb-155">与所有自行车购买者相比，男性和女性自行车购买者与未经筛选自行车购买者具有一些相同特征，但所有这三个群体也存在一些重要差异。</span><span class="sxs-lookup"><span data-stu-id="887bb-155">Compared to all bike buyers, male and female bike buyers share some of the same characteristics as the unfiltered bike buyers but all three have interesting differences as well.</span></span> <span data-ttu-id="887bb-156">这是 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 可用于开发市场营销活动的有用信息。</span><span class="sxs-lookup"><span data-stu-id="887bb-156">This is useful information that [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] can use to develop their marketing campaign.</span></span>  
  
#### <a name="to-test-the-lift-of-the-filtered-models"></a><span data-ttu-id="887bb-157">测试筛选后的模型的提升</span><span class="sxs-lookup"><span data-stu-id="887bb-157">To test the lift of the filtered models</span></span>  
  
1.  <span data-ttu-id="887bb-158">切换到数据挖掘设计器中的 "**挖掘准确性图表**" 选项卡 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ，然后选择 "**输入选择**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="887bb-158">Switch to the **Mining Accuracy Chart** tab in Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] and select the **Input Selection** tab.</span></span>  
  
2.  <span data-ttu-id="887bb-159">在 "**选择要用于准确性图表的数据集**" 组框中，选择 "**使用挖掘结构测试事例**"。</span><span class="sxs-lookup"><span data-stu-id="887bb-159">In the **Select data set to be used for Accuracy Chart** group box, select **Use mining structure test cases**.</span></span>  
  
3.  <span data-ttu-id="887bb-160">在数据挖掘设计器的 "**输入选择**" 选项卡上，在 "**选择要在提升图中显示的可预测的挖掘模型列**" 下，选中 "**同步预测列和值**" 复选框。</span><span class="sxs-lookup"><span data-stu-id="887bb-160">On the **Input Selection** tab of Data Mining Designer, under **Select predictable mining model columns to show in the lift chart**, select the checkbox for **Synchronize Prediction Columns and Values**.</span></span>  
  
4.  <span data-ttu-id="887bb-161">在 "**可预测列名称**" 列中，验证是否为每个模型选择了 "**自行车购买**者"。</span><span class="sxs-lookup"><span data-stu-id="887bb-161">In the **Predictable Column Name** column, verify that **Bike Buyer** is selected for each model.</span></span>  
  
5.  <span data-ttu-id="887bb-162">在 "**显示**" 列中，选择每个模型。</span><span class="sxs-lookup"><span data-stu-id="887bb-162">In the **Show** column, select each of the models.</span></span>  
  
6.  <span data-ttu-id="887bb-163">在 "**预测值**" 列中，选择 `1` 。</span><span class="sxs-lookup"><span data-stu-id="887bb-163">In the **Predict Value** column, select `1`.</span></span>  
  
7.  <span data-ttu-id="887bb-164">选择 "**提升图**" 选项卡以显示提升图。</span><span class="sxs-lookup"><span data-stu-id="887bb-164">Select the **Lift Chart** tab to display the lift chart.</span></span>  
  
     <span data-ttu-id="887bb-165">您现在会注意到，所有三个决策树模型与随机推测模型相比都有了显著提升，而且表现还超过了聚类分析和 Naive-Bayes 模型。</span><span class="sxs-lookup"><span data-stu-id="887bb-165">You will now notice that all three Decision Tree models provide significant lift compared to the random guess model, and also outperform the Clustering and Naive-Bayes models.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="887bb-166">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="887bb-166">Related Tasks</span></span>  
 <span data-ttu-id="887bb-167">有关筛选器的详细信息，请参阅[&#40;Analysis Services 挖掘模型的筛选器-数据挖掘&#41;](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="887bb-167">For more information on filters, see [Filters for Mining Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="887bb-168">有关如何将筛选器应用于嵌套表的示例，请参阅[数据挖掘的中间教程 &#40;Analysis Services 数据挖掘&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="887bb-168">For an example of how to apply filters to nested tables, see [Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md).</span></span>  
  
## <a name="previous-task-in-lesson"></a><span data-ttu-id="887bb-169">课程中的前一个任务</span><span class="sxs-lookup"><span data-stu-id="887bb-169">Previous Task in Lesson</span></span>  
 [<span data-ttu-id="887bb-170">测试提升图的准确性（数据挖掘基础教程）</span><span class="sxs-lookup"><span data-stu-id="887bb-170">Testing Accuracy with Lift Charts &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a><span data-ttu-id="887bb-171">下一课</span><span class="sxs-lookup"><span data-stu-id="887bb-171">Next Lesson</span></span>  
 [<span data-ttu-id="887bb-172">第 6 课：创建和使用预测（数据挖掘基础教程）</span><span class="sxs-lookup"><span data-stu-id="887bb-172">Lesson 6: Creating and Working with Predictions &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-6-creating-and-working-with-predictions-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="887bb-173">另请参阅</span><span class="sxs-lookup"><span data-stu-id="887bb-173">See Also</span></span>  
 <span data-ttu-id="887bb-174">[中级数据挖掘教程 &#40;Analysis Services 数据挖掘&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="887bb-174">[Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="887bb-175">[挖掘模型任务和操作指南](../../2014/analysis-services/data-mining/mining-model-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="887bb-175">[Mining Model Tasks and How-tos](../../2014/analysis-services/data-mining/mining-model-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="887bb-176">[从挖掘模型中删除筛选器](../../2014/analysis-services/data-mining/delete-a-filter-from-a-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="887bb-176">[Delete a Filter from a Mining Model](../../2014/analysis-services/data-mining/delete-a-filter-from-a-mining-model.md) </span></span>  
 [<span data-ttu-id="887bb-177">挖掘模型的筛选器（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="887bb-177">Filters for Mining Models &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)  
  
  
