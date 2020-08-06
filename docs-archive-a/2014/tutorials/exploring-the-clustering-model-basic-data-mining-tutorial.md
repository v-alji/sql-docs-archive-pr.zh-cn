---
title: 浏览聚类分析模型 (基本数据挖掘教程) |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: ce8aa034-161b-473f-baec-9c29e0a8e5f5
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: cca9d395fece59f607c8faf209128b9d32663a06
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694198"
---
# <a name="exploring-the-clustering-model-basic-data-mining-tutorial"></a><span data-ttu-id="30739-102">浏览聚类分析模型（数据挖掘基础教程）</span><span class="sxs-lookup"><span data-stu-id="30739-102">Exploring the Clustering Model (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="30739-103">[!INCLUDE[msCoName](../includes/msconame-md.md)]聚类分析算法将事例分组为包含类似特征的分类。</span><span class="sxs-lookup"><span data-stu-id="30739-103">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering algorithm groups cases into clusters that contain similar characteristics.</span></span> <span data-ttu-id="30739-104">在浏览数据、标识数据中的异常及创建预测时，这些分组十分有用。</span><span class="sxs-lookup"><span data-stu-id="30739-104">These groupings are useful for exploring data, identifying anomalies in the data, and creating predictions.</span></span>  
  
 <span data-ttu-id="30739-105">[!INCLUDE[msCoName](../includes/msconame-md.md)] 分类查看器提供了以下选项卡，用于浏览聚类分析挖掘模型：</span><span class="sxs-lookup"><span data-stu-id="30739-105">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Cluster Viewer provides the following tabs for use in exploring clustering mining models:</span></span>  
  

  
##  <a name="cluster-diagram-tab"></a><a name="ClusterDiagramTab"></a><span data-ttu-id="30739-106">分类关系图选项卡</span><span class="sxs-lookup"><span data-stu-id="30739-106">Cluster Diagram Tab</span></span>  
 <span data-ttu-id="30739-107">“分类关系图”选项卡显示挖掘模型中的所有分类。</span><span class="sxs-lookup"><span data-stu-id="30739-107">The Cluster Diagram tab displays all the clusters that are in a mining model.</span></span> <span data-ttu-id="30739-108">分类之间的线条表示“接近程度”，其明暗度取决于分类之间的相似程度。</span><span class="sxs-lookup"><span data-stu-id="30739-108">The lines between the clusters represent "closeness" and are shaded based on how similar the clusters are.</span></span> <span data-ttu-id="30739-109">每个分类的实际颜色表示分类中变量和状态的出现频率。</span><span class="sxs-lookup"><span data-stu-id="30739-109">The actual color of each cluster represents the frequency of the variable and the state in the cluster.</span></span>  
  
#### <a name="to-explore-the-model-in-the-cluster-diagram-tab"></a><span data-ttu-id="30739-110">在“分类关系图”选项卡中浏览模型</span><span class="sxs-lookup"><span data-stu-id="30739-110">To explore the model in the Cluster Diagram tab</span></span>  
  
1.  <span data-ttu-id="30739-111">可以使用 "**挖掘模型查看器**" 选项卡顶部的 "**挖掘模型**" 列表切换到 `TM_Clustering` 模型。</span><span class="sxs-lookup"><span data-stu-id="30739-111">Use the **Mining Model** list at the top of the **Mining Model Viewer** tab to switch to the `TM_Clustering` model.</span></span>  
  
2.  <span data-ttu-id="30739-112">在**查看器**列表中，选择 " **Microsoft 分类查看器**"。</span><span class="sxs-lookup"><span data-stu-id="30739-112">In the **Viewer** list, select **Microsoft Cluster Viewer**.</span></span>  
  
3.  <span data-ttu-id="30739-113">在 "**明暗度变量**" 框中，选择 "**自行车购买**者"。</span><span class="sxs-lookup"><span data-stu-id="30739-113">In the **Shading Variable** box, select **Bike Buyer**.</span></span>  
  
     <span data-ttu-id="30739-114">默认变量是**填充**，但您可以将其更改为模型中的任何属性，以发现哪些分类包含具有所需属性的成员。</span><span class="sxs-lookup"><span data-stu-id="30739-114">The default variable is **Population**, but you can change this to any attribute in the model, to discover which clusters contain members that have the attributes you want.</span></span>  
  
4.  <span data-ttu-id="30739-115">在 "**状态**" 框中选择**1**以浏览购买了自行车的情况。</span><span class="sxs-lookup"><span data-stu-id="30739-115">Select **1** in the **State** box to explore those cases where a bike was purchased.</span></span>  
  
     <span data-ttu-id="30739-116">**密度**图例描述了 "明暗度变量" 和 "状态" 中选定的属性状态对的密度。</span><span class="sxs-lookup"><span data-stu-id="30739-116">The **Density** legend describes the density of the attribute state pair selected in the Shading Variable and the State.</span></span> <span data-ttu-id="30739-117">在此示例中，它告诉我们，最暗的 clusterwith 是自行车购买者的最高百分比。</span><span class="sxs-lookup"><span data-stu-id="30739-117">In this example it tells us that the clusterwith the darkest shading has the highest percentage of bike buyers.</span></span>  
  
5.  <span data-ttu-id="30739-118">将鼠标悬停在明暗度最深的分类上。</span><span class="sxs-lookup"><span data-stu-id="30739-118">Pause your mouse over the cluster with the darkest shading.</span></span>  
  
     <span data-ttu-id="30739-119">工具提示将显示具有 `Bike Buyer = 1` 属性的事例所占的百分比。</span><span class="sxs-lookup"><span data-stu-id="30739-119">A tooltip displays the percentage of cases that have the attribute, `Bike Buyer = 1`.</span></span>  
  
6.  <span data-ttu-id="30739-120">选择密度最高的分类，右键单击该群集，选择 "**重命名群集**"，然后键入 "**自行车买家 High** "，以供以后标识。</span><span class="sxs-lookup"><span data-stu-id="30739-120">Select the cluster that has the highest density, right-click the cluster, select **Rename Cluster** and type **Bike Buyers High** for later identification.</span></span> [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="30739-121">查找明暗度最浅（也就是密度最低）的分类。</span><span class="sxs-lookup"><span data-stu-id="30739-121">Find the cluster that has the lightest shading (and the lowest density).</span></span> <span data-ttu-id="30739-122">右键单击该群集，选择 "**重命名群集**"，然后键入 "**自行车买家 Low**"。</span><span class="sxs-lookup"><span data-stu-id="30739-122">Right-click the cluster, select **Rename Cluster** and type **Bike Buyers Low**.</span></span> [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="30739-123">单击**自行车购买者高级**群集并将其拖到窗格中的某个区域，这会使你清楚地了解其与其他分类的连接。</span><span class="sxs-lookup"><span data-stu-id="30739-123">Click the **Bike Buyers High** cluster and drag it to an area of the pane that will give you a clear view of its connections to the other clusters.</span></span>  
  
     <span data-ttu-id="30739-124">选择某个分类时，将此分类连接到其他分类的线条将突出显示，以便您方便地查看此分类的所有关系。</span><span class="sxs-lookup"><span data-stu-id="30739-124">When you select a cluster, the lines that connect this cluster to other clusters are highlighted, so that you can easily see all the relationships for this cluster.</span></span> <span data-ttu-id="30739-125">如果该分类处于未选定状态，则可以通过线条的暗度来确定关系图中所有分类之间关系的紧密程度。</span><span class="sxs-lookup"><span data-stu-id="30739-125">When the cluster is not selected, you can tell by the darkness of the lines how strong the relationships are amongst all the clusters in the diagram.</span></span> <span data-ttu-id="30739-126">如果明暗度较浅或无明暗度，则表示分类的相似程度较低。</span><span class="sxs-lookup"><span data-stu-id="30739-126">If the shading is light or nonexistent, the clusters are not very similar.</span></span>  
  
9. <span data-ttu-id="30739-127">使用网络左侧的滑块，可筛选掉强度较低的链接，找出关系最接近的分类。</span><span class="sxs-lookup"><span data-stu-id="30739-127">Use the slider to the left of the network, to filter out the weaker links and find the clusters with the closest relationships.</span></span> <span data-ttu-id="30739-128">[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 市场部可能希望将相似的分类组合在一起，以便确定提供目标邮件的最佳方法。</span><span class="sxs-lookup"><span data-stu-id="30739-128">The [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] marketing department might want to combine similar clusters together when determining the best method for delivering the targeted mailing.</span></span>  
  

  
##  <a name="cluster-profiles-tab"></a><a name="ClusterProfilesTab"></a><span data-ttu-id="30739-129">群集配置文件选项卡</span><span class="sxs-lookup"><span data-stu-id="30739-129">Cluster Profiles Tab</span></span>  
 <span data-ttu-id="30739-130">"**分类配置文件**" 选项卡提供了模型的总体视图 `TM_Clustering` 。</span><span class="sxs-lookup"><span data-stu-id="30739-130">The **Cluster Profiles** tab provides an overall view of the `TM_Clustering` model.</span></span> <span data-ttu-id="30739-131">"**分类配置文件**" 选项卡包含模型中每个分类的列。</span><span class="sxs-lookup"><span data-stu-id="30739-131">The **Cluster Profiles** tab contains a column for each cluster in the model.</span></span> <span data-ttu-id="30739-132">第一列列出至少与一个分类关联的属性。</span><span class="sxs-lookup"><span data-stu-id="30739-132">The first column lists the attributes that are associated with at least one cluster.</span></span> <span data-ttu-id="30739-133">查看器的其余部分包含每个分类的某个属性的状态分布。</span><span class="sxs-lookup"><span data-stu-id="30739-133">The rest of the viewer contains the distribution of the states of an attribute for each cluster.</span></span> <span data-ttu-id="30739-134">离散变量的分布以彩色条显示，并显示在 "**直方图条**" 列表中显示的最大栏数。</span><span class="sxs-lookup"><span data-stu-id="30739-134">The distribution of a discrete variable is shown as a colored bar with the maximum number of bars displayed in the **Histogram bars** list.</span></span> <span data-ttu-id="30739-135">连续属性以菱形图显示，表示每个分类中的平均偏差和标准偏差。</span><span class="sxs-lookup"><span data-stu-id="30739-135">Continuous attributes are displayed with a diamond chart, which represents the mean and standard deviation in each cluster.</span></span>  
  
#### <a name="to-explore-the-model-in-the-cluster-profiles-tab"></a><span data-ttu-id="30739-136">在“分类剖面图”选项卡中浏览模型</span><span class="sxs-lookup"><span data-stu-id="30739-136">To explore the model in the Cluster Profiles tab</span></span>  
  
1.  <span data-ttu-id="30739-137">将**直方图**条设置为**5**。</span><span class="sxs-lookup"><span data-stu-id="30739-137">Set **Histogram** bars to **5**.</span></span>  
  
     <span data-ttu-id="30739-138">在我们的模型中，任意一个变量的最大状态数均为 5。</span><span class="sxs-lookup"><span data-stu-id="30739-138">In our model, 5 is the maximum number of states for any one variable.</span></span>  
  
2.  <span data-ttu-id="30739-139">如果 "**挖掘图例**" 阻止显示**属性配置文件**，请将其移开。</span><span class="sxs-lookup"><span data-stu-id="30739-139">If the **Mining Legend** blocks the display of the **Attribute profiles**, move it out of the way.</span></span>  
  
3.  <span data-ttu-id="30739-140">选择 "**自行车购买**者" 列并将其拖动到**填充**列的右侧。</span><span class="sxs-lookup"><span data-stu-id="30739-140">Select the **Bike Buyers High** column and drag it to the right of the **Population** column.</span></span>  
  
4.  <span data-ttu-id="30739-141">选择 "**自行车买家 Low** " 列并将其拖动到 "**自行车购买**者" 列的右侧。</span><span class="sxs-lookup"><span data-stu-id="30739-141">Select the **Bike Buyers Low** column and drag it to the right of the **Bike Buyers High** column.</span></span>  
  
5.  <span data-ttu-id="30739-142">单击 "**自行车购买**者" 列。</span><span class="sxs-lookup"><span data-stu-id="30739-142">Click the **Bike Buyers High** column.</span></span>  
  
     <span data-ttu-id="30739-143">**Variables**列按该分类的重要性顺序进行排序。</span><span class="sxs-lookup"><span data-stu-id="30739-143">The **Variables** column is sorted in order of importance for that cluster.</span></span> <span data-ttu-id="30739-144">滚动浏览该列，查看 Bike Buyer High 分类的特征。</span><span class="sxs-lookup"><span data-stu-id="30739-144">Scroll through the column and review characteristics of the Bike Buyer High cluster.</span></span> <span data-ttu-id="30739-145">例如，他们上下班路程较短的可能性较大。</span><span class="sxs-lookup"><span data-stu-id="30739-145">For example, they are more likely to have a short commute.</span></span>  
  
6.  <span data-ttu-id="30739-146">双击 "**自行车购买**者" 列中的**Age**单元格。</span><span class="sxs-lookup"><span data-stu-id="30739-146">Double-click the **Age** cell in the **Bike Buyers High** column.</span></span>  
  
     <span data-ttu-id="30739-147">"**挖掘图例**" 显示更详细的视图，可以查看这些客户的年龄范围以及平均年龄。</span><span class="sxs-lookup"><span data-stu-id="30739-147">The **Mining Legend** displays a more detailed view and you can see the age range of these customers as well as the mean age.</span></span>  
  
7.  <span data-ttu-id="30739-148">右键单击 "**自行车买家 Low** " 列并选择 "**隐藏列**"。</span><span class="sxs-lookup"><span data-stu-id="30739-148">Right-click the **Bike Buyers Low** column and select **Hide Column**.</span></span>  
  

  
##  <a name="cluster-characteristics-tab"></a><a name="ClusterCharacteristicsTab"></a><span data-ttu-id="30739-149">分类特征选项卡</span><span class="sxs-lookup"><span data-stu-id="30739-149">Cluster Characteristics Tab</span></span>  
 <span data-ttu-id="30739-150">使用 "**分类特征**" 选项卡，可以更详细地查看组成群集的特征。</span><span class="sxs-lookup"><span data-stu-id="30739-150">With the **Cluster Characteristics** tab, you can examine in more detail the characteristics that make up a cluster.</span></span> <span data-ttu-id="30739-151">您可以一次浏览一个分类，而不是比较所有分类的特征（就像在“分类剖面图”选项卡中那样）。</span><span class="sxs-lookup"><span data-stu-id="30739-151">Instead of comparing the characteristics of all of the clusters (as in the Cluster Profiles tab), you can explore one cluster at a time.</span></span> <span data-ttu-id="30739-152">例如，如果从**群集**列表中选择 "高" "**自行车购买**者"，则可以看到此群集中的客户的特征。</span><span class="sxs-lookup"><span data-stu-id="30739-152">For example, if you select **Bike Buyers High** from the **Cluster** list, you can see the characteristics of the customers in this cluster.</span></span> <span data-ttu-id="30739-153">尽管显示方式与分类剖面图查看器不同，但查找结果却是相同的。</span><span class="sxs-lookup"><span data-stu-id="30739-153">Though the display is different from the Cluster Profiles viewer, the findings are the same.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="30739-154">除非为**holdoutseed**设置初始值，否则每次处理该模型时，结果将有所不同。</span><span class="sxs-lookup"><span data-stu-id="30739-154">Unless you set an initial value for **holdoutseed**, results will vary each time you process the model.</span></span> <span data-ttu-id="30739-155">有关详细信息，请参阅[HoldoutSeed 元素](https://docs.microsoft.com/bi-reference/assl/properties/holdoutseed-element)</span><span class="sxs-lookup"><span data-stu-id="30739-155">For more information, see [HoldoutSeed Element](https://docs.microsoft.com/bi-reference/assl/properties/holdoutseed-element)</span></span>  
  

  
##  <a name="cluster-discrimination-tab"></a><a name="ClusterDiscriminationTab"></a><span data-ttu-id="30739-156">分类对比选项卡</span><span class="sxs-lookup"><span data-stu-id="30739-156">Cluster Discrimination Tab</span></span>  
 <span data-ttu-id="30739-157">利用 "**分类对比**" 选项卡，可以浏览区分不同分类的特征。</span><span class="sxs-lookup"><span data-stu-id="30739-157">With the **Cluster Discrimination** tab, you can explore the characteristics that distinguish one cluster from another.</span></span> <span data-ttu-id="30739-158">从 "**分类 1** " 列表中选择两个群集，然后从 "**分类 2** " 列表中选择两个群集后，查看器将计算这些分类之间的差异，并显示最大程度地区分分类的属性列表。</span><span class="sxs-lookup"><span data-stu-id="30739-158">After you select two clusters, one from the **Cluster 1** list, and one from the **Cluster 2** list, the viewer calculates the differences between the clusters and displays a list of the attributes that distinguish the clusters most.</span></span>  
  
#### <a name="to-explore-the-model-in-the-cluster-discrimination-tab"></a><span data-ttu-id="30739-159">在“分类对比”选项卡中浏览模型</span><span class="sxs-lookup"><span data-stu-id="30739-159">To explore the model in the Cluster Discrimination tab</span></span>  
  
1.  <span data-ttu-id="30739-160">在 "**分类 1** " 框中，选择 "**自行车买家 High**"。</span><span class="sxs-lookup"><span data-stu-id="30739-160">In the **Cluster 1** box, select **Bike Buyers High**.</span></span>  
  
2.  <span data-ttu-id="30739-161">在 "**分类 2** " 框中，选择 "**自行车买家 Low**"。</span><span class="sxs-lookup"><span data-stu-id="30739-161">In the **Cluster 2** box, select **Bike Buyers Low**.</span></span>  
  
3.  <span data-ttu-id="30739-162">单击 "**变量**" 以按字母顺序排序。</span><span class="sxs-lookup"><span data-stu-id="30739-162">Click **Variables** to sort alphabetically.</span></span>  
  
     <span data-ttu-id="30739-163">**自行车买家低端**和**自行车购买者高**群集的客户之间的一些显著差异包括年龄、汽车所有权、子女数量和地区。</span><span class="sxs-lookup"><span data-stu-id="30739-163">Some of the more substantial differences among the customers in the **Bike Buyers Low** and **Bike Buyers High** clusters include age, car ownership, number of children, and region.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="30739-164">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="30739-164">Related Tasks</span></span>  
 <span data-ttu-id="30739-165">请参阅以下主题以了解其他挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="30739-165">See the following topics to explore the other mining models.</span></span>  
  
-   [<span data-ttu-id="30739-166">浏览决策树模型 &#40;基本数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="30739-166">Exploring the Decision Tree Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="30739-167">浏览 Naive Bayes 模型 &#40;基本数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="30739-167">Exploring the Naive Bayes Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-naive-bayes-model-basic-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="30739-168">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="30739-168">Next Task in Lesson</span></span>  
 [<span data-ttu-id="30739-169">浏览 Naive Bayes 模型 &#40;基本数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="30739-169">Exploring the Naive Bayes Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-naive-bayes-model-basic-data-mining-tutorial.md)  
  
## <a name="previous-task-in-lesson"></a><span data-ttu-id="30739-170">课程中的前一个任务</span><span class="sxs-lookup"><span data-stu-id="30739-170">Previous Task in Lesson</span></span>  
 [<span data-ttu-id="30739-171">浏览决策树模型 &#40;基本数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="30739-171">Exploring the Decision Tree Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="30739-172">另请参阅</span><span class="sxs-lookup"><span data-stu-id="30739-172">See Also</span></span>  
 <span data-ttu-id="30739-173">[使用 Microsoft 分类查看器浏览模型](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="30739-173">[Browse a Model Using the Microsoft Cluster Viewer](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md) </span></span>  
 <span data-ttu-id="30739-174">[&#40;挖掘模型查看器的 "分类对比" 选项卡&#41;](../../2014/analysis-services/cluster-discrimination-tab-mining-model-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="30739-174">[Cluster Discrimination Tab &#40;Mining Model Viewer&#41;](../../2014/analysis-services/cluster-discrimination-tab-mining-model-viewer.md) </span></span>  
 <span data-ttu-id="30739-175">[挖掘模型查看器 &#40;的 "分类配置文件" 选项卡&#41;](../../2014/analysis-services/cluster-profiles-tab-mining-model-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="30739-175">[Cluster Profiles Tab &#40;Mining Model Viewer&#41;](../../2014/analysis-services/cluster-profiles-tab-mining-model-viewer.md) </span></span>  
 <span data-ttu-id="30739-176">[&#40;挖掘模型查看器的 "分类特征" 选项卡&#41;](../../2014/analysis-services/cluster-characteristics-tab-mining-model-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="30739-176">[Cluster Characteristics Tab &#40;Mining Model Viewer&#41;](../../2014/analysis-services/cluster-characteristics-tab-mining-model-viewer.md) </span></span>  
 [<span data-ttu-id="30739-177">&#40;挖掘模型查看器的 "分类关系图" 选项卡&#41;</span><span class="sxs-lookup"><span data-stu-id="30739-177">Cluster Diagram Tab &#40;Mining Model Viewer&#41;</span></span>](../../2014/analysis-services/cluster-diagram-tab-mining-model-viewer.md)  
  
  
