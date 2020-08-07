---
title: 浏览决策树模型 (基本数据挖掘教程) |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 2e1472c2-3f3e-4dae-acb3-62fca374d397
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a2c7f063d7cb73cdc431fb1bc94188c9266c10c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690934"
---
# <a name="exploring-the-decision-tree-model-basic-data-mining-tutorial"></a><span data-ttu-id="a07a1-102">浏览决策树模型（数据挖掘基础教程）</span><span class="sxs-lookup"><span data-stu-id="a07a1-102">Exploring the Decision Tree Model (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="a07a1-103">[!INCLUDE[msCoName](../includes/msconame-md.md)] 决策树算法预测哪些列影响基于定型集中的其余列做出的自行车购买决策。</span><span class="sxs-lookup"><span data-stu-id="a07a1-103">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees algorithm predicts which columns influence the decision to purchase a bike based upon the remaining columns in the training set.</span></span>  
  

  
##  <a name="decision-tree-tab"></a><a name="Decision_Tree_Tab"></a><span data-ttu-id="a07a1-104">决策树选项卡</span><span class="sxs-lookup"><span data-stu-id="a07a1-104">Decision Tree Tab</span></span>  
 <span data-ttu-id="a07a1-105">在 "**决策树**" 选项卡上，可以查看数据集中每个可预测属性的决策树。</span><span class="sxs-lookup"><span data-stu-id="a07a1-105">On the **Decision Tree** tab, you can view decision trees for every predictable attribute in the dataset.</span></span>  
  
 <span data-ttu-id="a07a1-106">在这种情况下，模型只预测一列（自行车购买者），因此只有一个要查看的树。</span><span class="sxs-lookup"><span data-stu-id="a07a1-106">In this case, the model predicts only one column, Bike Buyer, so there is only one tree to view.</span></span> <span data-ttu-id="a07a1-107">如果有更多的树，可以使用**树**框选择另一个树。</span><span class="sxs-lookup"><span data-stu-id="a07a1-107">If there were more trees, you could use the **Tree** box to choose another tree.</span></span>  
  
 <span data-ttu-id="a07a1-108">`TM_Decision_Tree`在决策树查看器中查看模型时，可以在图表左侧看到最重要的属性。</span><span class="sxs-lookup"><span data-stu-id="a07a1-108">As you view the `TM_Decision_Tree` model in the Decision Tree viewer, you can see the most important attributes at the left side of the chart.</span></span> <span data-ttu-id="a07a1-109">"最重要" 意味着这些属性对结果的影响最大。</span><span class="sxs-lookup"><span data-stu-id="a07a1-109">"Most important" means that these attributes have the greatest influence on the outcome.</span></span> <span data-ttu-id="a07a1-110">沿着该树越向下走的属性（图表右侧）的影响越小。</span><span class="sxs-lookup"><span data-stu-id="a07a1-110">Attributes further down the tree (to the right of the chart) have less of an effect.</span></span>  
  
 <span data-ttu-id="a07a1-111">在此示例中，在预测自行车购买行为时，年龄是最重要的因素。</span><span class="sxs-lookup"><span data-stu-id="a07a1-111">In this example, age is the single most important factor in predicting bike buying.</span></span> <span data-ttu-id="a07a1-112">模型按年龄对客户进行分组，然后显示每个年龄组的下一个较重要的属性。</span><span class="sxs-lookup"><span data-stu-id="a07a1-112">The model groups customers by age, and then shows the next more important attribute for each age group.</span></span> <span data-ttu-id="a07a1-113">例如，在年龄为 34 到 40 的客户组中，拥有的汽车数是仅次于年龄的预测因子。</span><span class="sxs-lookup"><span data-stu-id="a07a1-113">For example, in the group of customers aged 34 to 40, the number of cars owned is the strongest predictor after age.</span></span>  
  
#### <a name="to-explore-the-model-in-the-decision-tree-tab"></a><span data-ttu-id="a07a1-114">在“决策树”选项卡中浏览模型</span><span class="sxs-lookup"><span data-stu-id="a07a1-114">To explore the model in the Decision Tree tab</span></span>  
  
1.  <span data-ttu-id="a07a1-115">在**数据挖掘设计器**中选择 "**挖掘模型查看器**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="a07a1-115">Select the **Mining Model Viewer** tab in **Data Mining Designer**.</span></span>  
  
     <span data-ttu-id="a07a1-116">默认情况下，设计器将打开添加到结构中的第一个模型，在本例中为 `TM_Decision_Tree` 。</span><span class="sxs-lookup"><span data-stu-id="a07a1-116">By default, the designer opens to the first model that was added to the structure -- in this case, `TM_Decision_Tree`.</span></span>  
  
2.  <span data-ttu-id="a07a1-117">使用放大镜按钮调整树的显示大小。</span><span class="sxs-lookup"><span data-stu-id="a07a1-117">Use the magnifying glass buttons to adjust the size of the tree display.</span></span>  
  
     <span data-ttu-id="a07a1-118">默认情况下，[!INCLUDE[msCoName](../includes/msconame-md.md)] 树查看器仅显示树的前三个级别。</span><span class="sxs-lookup"><span data-stu-id="a07a1-118">By default, the [!INCLUDE[msCoName](../includes/msconame-md.md)] Tree Viewer shows only the first three levels of the tree.</span></span> <span data-ttu-id="a07a1-119">如果树级别不到三个，则查看器仅显示现有级别。</span><span class="sxs-lookup"><span data-stu-id="a07a1-119">If the tree contains fewer than three levels, the viewer shows only the existing levels.</span></span> <span data-ttu-id="a07a1-120">您可以使用 "**显示级别**" 滑块或**默认扩展**列表查看更多级别。</span><span class="sxs-lookup"><span data-stu-id="a07a1-120">You can view more levels by using the **Show Level** slider or the **Default Expansion** list.</span></span>  
  
3.  <span data-ttu-id="a07a1-121">向第四栏滑动**显示级别**。</span><span class="sxs-lookup"><span data-stu-id="a07a1-121">Slide **Show Level** to the fourth bar.</span></span>  
  
4.  <span data-ttu-id="a07a1-122">将 "**背景**" 值更改为 `1` 。</span><span class="sxs-lookup"><span data-stu-id="a07a1-122">Change the **Background** value to `1`.</span></span>  
  
     <span data-ttu-id="a07a1-123">通过更改 "**背景**" 设置，可以快速查看每个节点中的事例数，其目标值 `1` 为 [自行车购买者]。</span><span class="sxs-lookup"><span data-stu-id="a07a1-123">By changing the **Background** setting, you can quickly see the number of cases in each node that have the target value of `1` for [Bike Buyer].</span></span> <span data-ttu-id="a07a1-124">请注意，在这种特定的情况下，每个事例均表示一个客户。</span><span class="sxs-lookup"><span data-stu-id="a07a1-124">Remember that in this particular scenario, each case represents a customer.</span></span> <span data-ttu-id="a07a1-125">该值 `1` 表示客户以前购买了自行车; 值**0**指示客户未购买自行车。</span><span class="sxs-lookup"><span data-stu-id="a07a1-125">The value `1` indicates that the customer previously purchased a bike; the value **0** indicates that the customer has not purchased a bike.</span></span> <span data-ttu-id="a07a1-126">节点的底纹颜色越深，节点中具有目标值的事例所占的百分比越大。</span><span class="sxs-lookup"><span data-stu-id="a07a1-126">The darker the shading of the node, the higher the percentage of cases in the node that have the target value.</span></span>  
  
5.  <span data-ttu-id="a07a1-127">将光标置于标记为 "**全部**" 的节点上。</span><span class="sxs-lookup"><span data-stu-id="a07a1-127">Place your cursor over the node labeled **All**.</span></span> <span data-ttu-id="a07a1-128">将出现显示以下信息的工具提示：</span><span class="sxs-lookup"><span data-stu-id="a07a1-128">An tooltip will display the following information:</span></span>  
  
    -   <span data-ttu-id="a07a1-129">事例总数</span><span class="sxs-lookup"><span data-stu-id="a07a1-129">Total number of cases</span></span>  
  
    -   <span data-ttu-id="a07a1-130">非自行车购买者事例的数量</span><span class="sxs-lookup"><span data-stu-id="a07a1-130">Number of non bike buyer cases</span></span>  
  
    -   <span data-ttu-id="a07a1-131">自行车购买者事例的数量</span><span class="sxs-lookup"><span data-stu-id="a07a1-131">Number of bike buyer cases</span></span>  
  
    -   <span data-ttu-id="a07a1-132">缺少 [Bike Buyer] 值的事例的数量</span><span class="sxs-lookup"><span data-stu-id="a07a1-132">Number of cases with missing values for [Bike Buyer]</span></span>  
  
     <span data-ttu-id="a07a1-133">或者，将光标放在树中的任何节点上，查看从上级节点到达该节点所需的条件。</span><span class="sxs-lookup"><span data-stu-id="a07a1-133">Alternately, place your cursor over any node in the tree to see the condition that is required to reach that node from the node that comes before it.</span></span> <span data-ttu-id="a07a1-134">您还可以在 "**挖掘图例**" 中查看相同的信息。</span><span class="sxs-lookup"><span data-stu-id="a07a1-134">You can also view this same information in the **Mining Legend**.</span></span>  
  
6.  <span data-ttu-id="a07a1-135">单击 " **Age >= 34" 节点，然后单击 "< 41**"。</span><span class="sxs-lookup"><span data-stu-id="a07a1-135">Click on the node for **Age >=34 and < 41**.</span></span> <span data-ttu-id="a07a1-136">直方图将显示为一个穿过该节点的窄水平条，并表示此年龄范围中以前买过自行车的客户（粉色）和没有买过自行车的客户（蓝色）的分布情况。</span><span class="sxs-lookup"><span data-stu-id="a07a1-136">The histogram is displayed as a thin horizontal bar across the node and represents the distribution of customers in this age range who previously did (pink) and did not (blue) purchase a bike.</span></span> <span data-ttu-id="a07a1-137">查看器显示：没有汽车或者有一辆汽车、年龄在 34 到 40 的客户有可能购买自行车。</span><span class="sxs-lookup"><span data-stu-id="a07a1-137">The Viewer shows us that customers between the ages of 34 and 40 with one or no cars are likely to purchase a bike.</span></span> <span data-ttu-id="a07a1-138">再进一步考察发现，实际年龄在 38 到 40 的客户购买自行车的可能性会增加。</span><span class="sxs-lookup"><span data-stu-id="a07a1-138">Taking it one step further, we find that the likelihood to purchase a bike increases if the customer is actually age 38 to 40.</span></span>  
  
 <span data-ttu-id="a07a1-139">由于您在创建结构和模型时启用了钻取，因此，可以从模型事例和挖掘结构中检索详细的信息，其中包括挖掘模型中所不包含的列（例如，emailAddress 和 FirstName）。</span><span class="sxs-lookup"><span data-stu-id="a07a1-139">Because you enabled drillthrough when you created the structure and model, you can retrieve detailed information from the model cases and mining structure, including those columns that were not included in the mining model (e.g., emailAddress, FirstName).</span></span>  
  
 <span data-ttu-id="a07a1-140">有关详细信息，请参阅 [钻取查询（数据挖掘）](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="a07a1-140">For more information, see [Drillthrough Queries &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md).</span></span>  
  
#### <a name="to-drill-through-to-case-data"></a><span data-ttu-id="a07a1-141">钻取到事例数据</span><span class="sxs-lookup"><span data-stu-id="a07a1-141">To drill through to case data</span></span>  
  
1.  <span data-ttu-id="a07a1-142">右键单击某个节点，然后选择 "**钻取**"，然后选择 "**仅限模型列**"。</span><span class="sxs-lookup"><span data-stu-id="a07a1-142">Right-click a node, and select **Drill Through** then **Model Columns Only**.</span></span>  
  
     <span data-ttu-id="a07a1-143">每个定型事例的详细信息将以电子表格方式显示。</span><span class="sxs-lookup"><span data-stu-id="a07a1-143">The details for each training case are displayed in spreadsheet format.</span></span> <span data-ttu-id="a07a1-144">这些详细信息来自您在生成挖掘结构时选作事例表的 vTargetMail 视图。</span><span class="sxs-lookup"><span data-stu-id="a07a1-144">These details come from the vTargetMail view that you selected as the case table when building the mining structure.</span></span>  
  
2.  <span data-ttu-id="a07a1-145">右键单击某个节点，然后选择 "**钻取**"，然后选择 "**模型和结构列**"。</span><span class="sxs-lookup"><span data-stu-id="a07a1-145">Right-click a node, and select **Drill Through** then **Model and Structure Columns**.</span></span>  
  
     <span data-ttu-id="a07a1-146">将显示同一个电子表格，并在末尾处附加结构列。</span><span class="sxs-lookup"><span data-stu-id="a07a1-146">The same spreadsheet displays with the structure columns appended to the end.</span></span>  
  
  
###  <a name="dependency-network-tab"></a><a name="Dependency_Network_Tab"></a><span data-ttu-id="a07a1-147">依赖关系网络选项卡</span><span class="sxs-lookup"><span data-stu-id="a07a1-147">Dependency Network Tab</span></span>  
 <span data-ttu-id="a07a1-148">"**依赖关系网络**" 选项卡显示构成挖掘模型预测能力的属性之间的关系。</span><span class="sxs-lookup"><span data-stu-id="a07a1-148">The **Dependency Network** tab displays the relationships between the attributes that contribute to the predictive ability of the mining model.</span></span> <span data-ttu-id="a07a1-149">依赖关系网络查看器进一步证实了我们的发现：年龄和地区是预测自行车购买行为的重要因素。</span><span class="sxs-lookup"><span data-stu-id="a07a1-149">The Dependency Network viewer reinforces our findings that Age and Region are important factors in predicting bike buying.</span></span>  
  
##### <a name="to-explore-the-model-in-the-dependency-network-tab"></a><span data-ttu-id="a07a1-150">在“依赖关系网络”选项卡中浏览模型</span><span class="sxs-lookup"><span data-stu-id="a07a1-150">To explore the model in the Dependency Network tab</span></span>  
  
1.  <span data-ttu-id="a07a1-151">单击 `Bike Buyer` 节点以标识其依赖项。</span><span class="sxs-lookup"><span data-stu-id="a07a1-151">Click the `Bike Buyer` node to identify its dependencies.</span></span>  
  
     <span data-ttu-id="a07a1-152">依赖关系网络的中心节点 `Bike Buyer` 表示挖掘模型中的可预测属性。</span><span class="sxs-lookup"><span data-stu-id="a07a1-152">The center node for the dependency network, `Bike Buyer`, represents the predictable attribute in the mining model.</span></span> <span data-ttu-id="a07a1-153">该图形突出显示了影响可预测的属性的任何已连接节点。</span><span class="sxs-lookup"><span data-stu-id="a07a1-153">The graph highlights any connected nodes that have an effect on the predictable attribute.</span></span>  
  
2.  <span data-ttu-id="a07a1-154">调整 "**所有链接**" 滑块以确定最具影响力的特性。</span><span class="sxs-lookup"><span data-stu-id="a07a1-154">Adjust the **All Links** slider to identify the most influential attribute.</span></span>  
  
     <span data-ttu-id="a07a1-155">向下拖动滑块时，将从关系图中删除只对 [自行车买家] 列产生弱影响的属性。</span><span class="sxs-lookup"><span data-stu-id="a07a1-155">As you drag down the slider, attributes that have only a weak effect on the [Bike Buyer] column are removed from the graph.</span></span> <span data-ttu-id="a07a1-156">通过调整滑块，可以发现“年龄”和“地区”是预测个人自行车购买行为的最主要因素。</span><span class="sxs-lookup"><span data-stu-id="a07a1-156">By adjusting the slider, you can discover that Age and Region are the greatest factors in predicting whether someone is a bike buyer.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="a07a1-157">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="a07a1-157">Related Tasks</span></span>  
 <span data-ttu-id="a07a1-158">请参阅以下主题，了解如何使用其他模型类型来探索数据。</span><span class="sxs-lookup"><span data-stu-id="a07a1-158">See these topics to explore the data using the other kinds of models.</span></span>  
  
-   [<span data-ttu-id="a07a1-159">浏览聚类分析模型 &#40;基本数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="a07a1-159">Exploring the Clustering Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-clustering-model-basic-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="a07a1-160">浏览 Naive Bayes 模型 &#40;基本数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="a07a1-160">Exploring the Naive Bayes Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-naive-bayes-model-basic-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="a07a1-161">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="a07a1-161">Next Task in Lesson</span></span>  
 [<span data-ttu-id="a07a1-162">浏览聚类分析模型 &#40;基本数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="a07a1-162">Exploring the Clustering Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-clustering-model-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="a07a1-163">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a07a1-163">See Also</span></span>  
 <span data-ttu-id="a07a1-164">[挖掘模型查看器任务和操作指南](../../2014/analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="a07a1-164">[Mining Model Viewer Tasks and How-tos](../../2014/analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="a07a1-165">[挖掘模型查看器 &#40;的决策树选项卡&#41;](../../2014/analysis-services/decision-tree-tab-mining-model-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="a07a1-165">[Decision Tree Tab &#40;Mining Model Viewer&#41;](../../2014/analysis-services/decision-tree-tab-mining-model-viewer.md) </span></span>  
 <span data-ttu-id="a07a1-166">[挖掘模型查看器 &#40;的 "依赖关系网络" 选项卡&#41;](../../2014/analysis-services/dependency-network-tab-mining-model-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="a07a1-166">[Dependency Network Tab &#40;Mining Model Viewer&#41;](../../2014/analysis-services/dependency-network-tab-mining-model-viewer.md) </span></span>  
 [<span data-ttu-id="a07a1-167">使用 Microsoft 树查看器浏览模型</span><span class="sxs-lookup"><span data-stu-id="a07a1-167">Browse a Model Using the Microsoft Tree Viewer</span></span>](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-tree-viewer.md)  
  
  
