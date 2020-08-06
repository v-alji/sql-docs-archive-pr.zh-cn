---
title: 浏览顺序分析和聚类分析模型 (中级数据挖掘教程) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f8a485d5-47ed-4dd5-bb66-ef4d6d463845
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: bac603d2480ec1f344d14351757027de749f8c86
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691392"
---
# <a name="exploring-the-sequence-clustering-model-intermediate-data-mining-tutorial"></a><span data-ttu-id="8fd63-102">浏览顺序分析和聚类分析模型（数据挖掘中级教程）</span><span class="sxs-lookup"><span data-stu-id="8fd63-102">Exploring the Sequence Clustering Model (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="8fd63-103">现在您已**使用区域**模型构建了序列群集，可以使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] 数据挖掘设计器的 "**挖掘模型查看**器" 选项卡中的 "序列聚类分析" 查看器对其进行浏览。</span><span class="sxs-lookup"><span data-stu-id="8fd63-103">Now that you have built the **Sequence Clustering with Region** model, you can explore it by using the [!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Clustering Viewer in the **Mining Model Viewer** tab of Data Mining Designer.</span></span> <span data-ttu-id="8fd63-104">[!INCLUDE[msCoName](../includes/msconame-md.md)]序列分类查看器包含五个选项卡：**群集图**、**群集配置文件**、**群集特征**、 **ClusterDiscrimination**和**状态转换**。</span><span class="sxs-lookup"><span data-stu-id="8fd63-104">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Cluster Viewer contains five tabs: **Cluster Diagram**, **Cluster Profiles**, **Cluster Characteristics**, **ClusterDiscrimination**, and **State Transitions**.</span></span> <span data-ttu-id="8fd63-105">有关如何使用此查看器的详细信息，请参阅[使用 Microsoft 序列分类查看器浏览模型](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="8fd63-105">For more information about how to use this viewer, see [Browse a Model Using the Microsoft Sequence Cluster Viewer](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md).</span></span>  
  
-   [<span data-ttu-id="8fd63-106">分类关系图选项卡</span><span class="sxs-lookup"><span data-stu-id="8fd63-106">Cluster Diagram tab</span></span>](#bkmk_CDiagram)  
  
-   [<span data-ttu-id="8fd63-107">群集配置文件选项卡</span><span class="sxs-lookup"><span data-stu-id="8fd63-107">Cluster Profiles tab</span></span>](#bkmk_CProfiles)  
  
-   [<span data-ttu-id="8fd63-108">分类特征选项卡</span><span class="sxs-lookup"><span data-stu-id="8fd63-108">Cluster Characteristics tab</span></span>](#bkmk_CChars)  
  
-   [<span data-ttu-id="8fd63-109">分类对比选项卡</span><span class="sxs-lookup"><span data-stu-id="8fd63-109">Cluster Discrimination tab</span></span>](#bkmk_CDiscrim2)  
  
-   [<span data-ttu-id="8fd63-110">“状态转换”选项卡</span><span class="sxs-lookup"><span data-stu-id="8fd63-110">State Transitions tab</span></span>](#bkmk_StateTran)  
  
-   [<span data-ttu-id="8fd63-111">“一般内容”视图</span><span class="sxs-lookup"><span data-stu-id="8fd63-111">Generic Content View</span></span>](#bkmk_Generic)  
  
##  <a name="cluster-diagram-tab"></a><a name="bkmk_CDiagram"></a><span data-ttu-id="8fd63-112">分类关系图选项卡</span><span class="sxs-lookup"><span data-stu-id="8fd63-112">Cluster Diagram Tab</span></span>  
 <span data-ttu-id="8fd63-113">"**分类关系图**" 选项卡以图形方式显示算法在数据库中发现的分类。</span><span class="sxs-lookup"><span data-stu-id="8fd63-113">The **Cluster Diagram** tab graphically displays the clusters that the algorithm discovered in the database.</span></span> <span data-ttu-id="8fd63-114">关系图中的布局表示分类之间的关系，其中相似的分类分组在一起。</span><span class="sxs-lookup"><span data-stu-id="8fd63-114">The layout in the diagram represents the relationships of the clusters, with similar clusters grouped close together.</span></span> <span data-ttu-id="8fd63-115">默认情况下，每个节点的明暗度表示分类中所有事例的密度，即节点越暗，它所包含的事例越多。</span><span class="sxs-lookup"><span data-stu-id="8fd63-115">By default, the shade of each node represents the density of all cases in the cluster: the darker the shade of the node, the more cases it contains.</span></span> <span data-ttu-id="8fd63-116">可以更改节点明暗度代表的含义，使其表示对每个分类内的属性或状态的支持。</span><span class="sxs-lookup"><span data-stu-id="8fd63-116">You can change the meaning of the shading of the nodes so that it represents support, within each cluster, for an attribute and a state.</span></span>  
  
 <span data-ttu-id="8fd63-117">也可以重命名分类，使其更加易于识别并与目标分类结合使用。</span><span class="sxs-lookup"><span data-stu-id="8fd63-117">You can also rename the clusters, to make it easier to identify and work with target clusters.</span></span> <span data-ttu-id="8fd63-118">在本教程中，您将重命名太平洋地区客户百分比最高的分类，以及事例总数量最多的分类。</span><span class="sxs-lookup"><span data-stu-id="8fd63-118">For this tutorial, you will rename the cluster that has the highest percentage of customers from the Pacific region, and the cluster that has the most cases overall.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8fd63-119">在重新处理模型时，分配给特定分类的事例可能会发生更改，具体取决于数据和模型参数。</span><span class="sxs-lookup"><span data-stu-id="8fd63-119">The cases that are assigned to specific clusters might change when you reprocess the model, depending on the data and the model parameters.</span></span> <span data-ttu-id="8fd63-120">此外，如果对分类进行了重命名，则在重新处理挖掘模型时，这些名称将会丢失。</span><span class="sxs-lookup"><span data-stu-id="8fd63-120">Also, if you rename clusters, the names will be lost when you reprocess the mining model.</span></span>  
  
#### <a name="to-change-the-attribute-used-for-highlighting-clusters"></a><span data-ttu-id="8fd63-121">更改用于突出显示分类的属性</span><span class="sxs-lookup"><span data-stu-id="8fd63-121">To change the attribute used for highlighting clusters</span></span>  
  
1.  <span data-ttu-id="8fd63-122">在 "**明暗度变量**" 列表中，选择 "**模型**"。</span><span class="sxs-lookup"><span data-stu-id="8fd63-122">In the **Shading Variable** list, select **Model**.</span></span>  
  
2.  <span data-ttu-id="8fd63-123">在 "**状态**" 列表中选择 "**循环 Cap** "。</span><span class="sxs-lookup"><span data-stu-id="8fd63-123">Select **Cycling Cap** in the **State** list.</span></span>  
  
     <span data-ttu-id="8fd63-124">该图会进行更新，以显示所选产品在每个分类中的集中度。</span><span class="sxs-lookup"><span data-stu-id="8fd63-124">The diagram updates to show the concentration of the selected product in each of the clusters.</span></span> <span data-ttu-id="8fd63-125">最暗的分类包含自行车帽的密度最大。</span><span class="sxs-lookup"><span data-stu-id="8fd63-125">The cluster that has the darkest shading contains the highest density of cycling caps.</span></span> <span data-ttu-id="8fd63-126">您可以将明暗度变量更改为使用任何输入列的任何状态。</span><span class="sxs-lookup"><span data-stu-id="8fd63-126">You can change the shading variable to use any state of any input column.</span></span>  
  
3.  <span data-ttu-id="8fd63-127">在 "**明暗度变量**" 列表中，选择 "**填充**"。</span><span class="sxs-lookup"><span data-stu-id="8fd63-127">In the **Shading Variable** list, select **Population**.</span></span>  
  
     <span data-ttu-id="8fd63-128">将明暗度变量更改为客户群体时，该图将进行更新，按大小比较分类。</span><span class="sxs-lookup"><span data-stu-id="8fd63-128">When you change the shading variable to population, the diagram updates to compare the clusters by size.</span></span> <span data-ttu-id="8fd63-129">最暗的分类所包含的事例多于其他分类。</span><span class="sxs-lookup"><span data-stu-id="8fd63-129">The cluster that has the darkest shading contains more cases than the other clusters.</span></span>  
  
#### <a name="to-rename-nodes-in-the-model"></a><span data-ttu-id="8fd63-130">重命名模型中的节点</span><span class="sxs-lookup"><span data-stu-id="8fd63-130">To rename nodes in the model</span></span>  
  
1.  <span data-ttu-id="8fd63-131">将**明暗度变量**更改为 `Region` ，并将**状态**设置为 "**太平洋**"。</span><span class="sxs-lookup"><span data-stu-id="8fd63-131">Change **Shading Variable** to `Region`, and set **State** to **Pacific**.</span></span>  
  
2.  <span data-ttu-id="8fd63-132">突出显示图形中最暗的节点。</span><span class="sxs-lookup"><span data-stu-id="8fd63-132">Highlight the darkest node in the graph.</span></span>  
  
3.  <span data-ttu-id="8fd63-133">右键单击此群集，然后选择 "**重命名群集"。**</span><span class="sxs-lookup"><span data-stu-id="8fd63-133">Right-click this cluster and select **Rename Cluster.**</span></span>  
  
4.  <span data-ttu-id="8fd63-134">键入 "**太平洋群集**名称"。</span><span class="sxs-lookup"><span data-stu-id="8fd63-134">Type the name**Pacific Cluster.**</span></span>  
  
5.  <span data-ttu-id="8fd63-135">将 "明暗度**变量**" 的值更改为 "**总体**"。</span><span class="sxs-lookup"><span data-stu-id="8fd63-135">Change the value of **Shading Variable** to **Population**.</span></span>  
  
6.  <span data-ttu-id="8fd63-136">在已更新的图形中，找到最暗的分类（应该是最大的分类）。</span><span class="sxs-lookup"><span data-stu-id="8fd63-136">In the updated graph, locate the darkest cluster, which should be the largest cluster.</span></span> <span data-ttu-id="8fd63-137">如果无法通过明暗度来判断哪个分类是最大的，请将鼠标悬停在每个分类上并查看工具提示，然后选择包含事例最多的分类。</span><span class="sxs-lookup"><span data-stu-id="8fd63-137">If you cannot tell by the shading which cluster is largest, pause the mouse over each cluster and view the ToolTip, and then choose the cluster that contains the most cases.</span></span>  
  
7.  <span data-ttu-id="8fd63-138">右键单击此群集，然后选择 "**重命名群集**"。</span><span class="sxs-lookup"><span data-stu-id="8fd63-138">Right-click this cluster and select **Rename Cluster**.</span></span> <span data-ttu-id="8fd63-139">键入新名称 `Largest Cluster` 。</span><span class="sxs-lookup"><span data-stu-id="8fd63-139">Type the new name, `Largest Cluster`.</span></span>  
  
 <span data-ttu-id="8fd63-140">可从表示该分类的节点进行钻取，以查看每个分类中事例的详细信息。</span><span class="sxs-lookup"><span data-stu-id="8fd63-140">You can drill through from the node that represents the cluster to view details of the cases that are in each cluster.</span></span> <span data-ttu-id="8fd63-141">如果要对分析结果进行操作（例如发送电子邮件给客户），则此功能非常有用。</span><span class="sxs-lookup"><span data-stu-id="8fd63-141">This can be useful if you want to take action on the results of your analysis, such as sending e-mail to a customer.</span></span> <span data-ttu-id="8fd63-142">还可以浏览包括在结构中但未在模型中使用的其他一些事例属性，例如 Region 和 IncomeGroup。</span><span class="sxs-lookup"><span data-stu-id="8fd63-142">You can also browse the other attributes of the cases that you included in the structure but did not use in the model, such as Region and IncomeGroup.</span></span> <span data-ttu-id="8fd63-143">有关从挖掘模型钻取到基础事例的详细信息，请参阅[钻取查询 &#40;数据挖掘&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="8fd63-143">For more information about drilling through from mining models to the underlying cases, see [Drillthrough Queries &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md).</span></span>  
  
#### <a name="to-drill-through-to-details-from-the-cluster-diagram"></a><span data-ttu-id="8fd63-144">从分类关系图钻取到详细信息</span><span class="sxs-lookup"><span data-stu-id="8fd63-144">To drill through to details from the Cluster diagram</span></span>  
  
1.  <span data-ttu-id="8fd63-145">右键单击 `Pacific Cluster` ，选择 "**钻取**"，然后选择 "**模型和结构列**"。</span><span class="sxs-lookup"><span data-stu-id="8fd63-145">Right-click `Pacific Cluster`, select **Drill Through**, and then select **Model and Structure columns**.</span></span>  
  
     <span data-ttu-id="8fd63-146">"**钻取**" 对话框将打开。</span><span class="sxs-lookup"><span data-stu-id="8fd63-146">The **Drill Through** dialog box opens.</span></span> <span data-ttu-id="8fd63-147">未在模型中使用但可用于查询的列的前缀为 "**结构**"。</span><span class="sxs-lookup"><span data-stu-id="8fd63-147">Columns that are not used in the model but that are available for querying are prefixed with **Structure**.</span></span>  
  
     <span data-ttu-id="8fd63-148">可以看到此分类包括的大多数客户都来自太平洋地区，只有少量客户来自其他地区。</span><span class="sxs-lookup"><span data-stu-id="8fd63-148">You can see that this cluster contains mostly customers from the Pacific region, with only a few customers from other regions.</span></span>  
  
2.  <span data-ttu-id="8fd63-149">单击嵌套列 v Assoc Seq Line Items 中的加号，可以查看特定客户订单中项的顺序。</span><span class="sxs-lookup"><span data-stu-id="8fd63-149">Click the plus sign in the nested column v Assoc Seq Line Items to view the sequence of items in a particular customer order.</span></span>  
  
3.  <span data-ttu-id="8fd63-150">关闭 "**钻取**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="8fd63-150">Close the **Drill Through** dialog box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8fd63-151">利用 "**播放**" 按钮，您可以重新查询数据;但是，如果模型已由其他进程在后台动态更新，则重新查询不会更改显示的数据。</span><span class="sxs-lookup"><span data-stu-id="8fd63-151">The **Play** button enables you to requery the data; however, requerying does not change the data that is displayed, unless the model has been dynamically updated in the background by some other process.</span></span>  
  
 [<span data-ttu-id="8fd63-152">返回页首</span><span class="sxs-lookup"><span data-stu-id="8fd63-152">Back to Top</span></span>](#bkmk_CDiagram)  
  
##  <a name="cluster-profiles-tab"></a><a name="bkmk_CProfiles"></a><span data-ttu-id="8fd63-153">群集配置文件选项卡</span><span class="sxs-lookup"><span data-stu-id="8fd63-153">Cluster Profiles Tab</span></span>  
 <span data-ttu-id="8fd63-154">"**分类配置文件**" 选项卡显示每个群集中的序列。</span><span class="sxs-lookup"><span data-stu-id="8fd63-154">The **Cluster Profiles** tab displays the sequences that are in each cluster.</span></span> <span data-ttu-id="8fd63-155">群集列在 "**状态**" 列右侧的各个列中。</span><span class="sxs-lookup"><span data-stu-id="8fd63-155">The clusters are listed in individual columns to the right of the **States** column.</span></span>  
  
 <span data-ttu-id="8fd63-156">在查看器中，"**模型**" 行描述了群集中各项的总体分布，而 "**模型**" 行包含各项的序列。</span><span class="sxs-lookup"><span data-stu-id="8fd63-156">In the viewer, the **Model** row describes the overall distribution of items in a cluster, and the **Model.samples** row contains sequences of the items.</span></span> <span data-ttu-id="8fd63-157">模型每个单元格中的颜色序列的每一行 **。 samples**行表示群集中随机选择的用户的行为。</span><span class="sxs-lookup"><span data-stu-id="8fd63-157">Each line of the color sequences in each cell of the **Model.samples** row represents the behavior of a randomly selected user in the cluster.</span></span>  
  
 <span data-ttu-id="8fd63-158">单个序列直方图中的每一种颜色都代表一个产品型号。</span><span class="sxs-lookup"><span data-stu-id="8fd63-158">Each color in an individual sequence histogram represents a product model.</span></span> <span data-ttu-id="8fd63-159">挖掘图例使用颜色编码和产品型号名称来显示产品序列。</span><span class="sxs-lookup"><span data-stu-id="8fd63-159">The Mining Legend shows you the sequences of products by using both color-coding and the product model names.</span></span> <span data-ttu-id="8fd63-160">如果您已经将其他列添加到聚类分析模型中，例如 Region 或 Income Group，则查看器将包含每个列的附加行，显示这些值在每个分类中的分布。</span><span class="sxs-lookup"><span data-stu-id="8fd63-160">If you have added other columns to the model for clustering, such as Region or Income Group, the viewer will contain an additional row for each column that shows the distribution of these values within each cluster.</span></span>  
  
#### <a name="to-view-the-sequences-that-are-most-common-in-a-cluster"></a><span data-ttu-id="8fd63-161">查看分类中最常见的顺序</span><span class="sxs-lookup"><span data-stu-id="8fd63-161">To view the sequences that are most common in a cluster</span></span>  
  
1.  <span data-ttu-id="8fd63-162">右键单击群集列中的 "**模型**" 行 `Largest Cluster` ，然后选择 "**显示图例**"。</span><span class="sxs-lookup"><span data-stu-id="8fd63-162">Right-click the **Model** row in the column for the cluster `Largest Cluster`, and select **Show Legend**.</span></span>  
  
     <span data-ttu-id="8fd63-163">**Color**列包含一个阴影条，用于指示在序列中找到的项的频率。</span><span class="sxs-lookup"><span data-stu-id="8fd63-163">The **Color** column contains a shaded bar that indicates the frequency of items found in sequences.</span></span> <span data-ttu-id="8fd63-164">每个项以一种不同颜色表示。</span><span class="sxs-lookup"><span data-stu-id="8fd63-164">Each item is represented by a different color.</span></span> <span data-ttu-id="8fd63-165">"**含义**" 列列出每种颜色的产品型号名称。</span><span class="sxs-lookup"><span data-stu-id="8fd63-165">The **Meaning** column lists the product model names for each color.</span></span> <span data-ttu-id="8fd63-166">"**分布**" 列告诉您序列中包含此项的事例的百分比。</span><span class="sxs-lookup"><span data-stu-id="8fd63-166">The **Distribution** column tells you the percentage of cases that contained this item in a sequence.</span></span>  
  
2.  <span data-ttu-id="8fd63-167">关闭 "**挖掘图例**"。</span><span class="sxs-lookup"><span data-stu-id="8fd63-167">Close the **Mining Legend**.</span></span>  
  
3.  <span data-ttu-id="8fd63-168">右键单击包含 "标题" 和 "**填充**" 的列中的 "**示例**" 行，然后选择 "**显示图例**"。</span><span class="sxs-lookup"><span data-stu-id="8fd63-168">Right-click the **Model.samples** row in the column with the heading, **Population,** and select **Show Legend**.</span></span>  
  
4.  <span data-ttu-id="8fd63-169">扫描整个模型中的序列列表`.`</span><span class="sxs-lookup"><span data-stu-id="8fd63-169">Scan the list of sequences in the overall model`.`</span></span>  
  
     <span data-ttu-id="8fd63-170">挖掘图例会首先列出最常见的序列，因此您可以看到 Mountain Tire Tube 是很多序列中的第一项。</span><span class="sxs-lookup"><span data-stu-id="8fd63-170">The Mining Legend lists the most common sequences first, so you can see that Mountain Tire Tube is the first item in many sequences.</span></span> <span data-ttu-id="8fd63-171">这意味着客户很有可能首先将 Mountain Tire Tube 放入购物篮中。</span><span class="sxs-lookup"><span data-stu-id="8fd63-171">This means that a customer is very likely to put the Mountain Tire Tube in the shopping basket first.</span></span>  
  
#### <a name="to-drill-through-to-cases-from-the-cluster-viewer"></a><span data-ttu-id="8fd63-172">从分类查看器钻取到事例</span><span class="sxs-lookup"><span data-stu-id="8fd63-172">To drill through to cases from the cluster viewer</span></span>  
  
1.  <span data-ttu-id="8fd63-173">在 "属性" 窗格中向下滚动，直到找到属性所在的行 `Region` 。</span><span class="sxs-lookup"><span data-stu-id="8fd63-173">Scroll down in the Attribute pane until you find the row for the `Region` attribute.</span></span>  
  
     <span data-ttu-id="8fd63-174">该行包含模型中每个分类的直方图，以及一个用于**填充**的附加柱状图，即模型中使用的整个事例集。</span><span class="sxs-lookup"><span data-stu-id="8fd63-174">The row contains a histogram for each cluster in the model, plus one additional histogram for **Population**, meaning the entire set of cases used in the model.</span></span> <span data-ttu-id="8fd63-175">直方图是一个带有不同颜色的条，每种颜色代表一个属性，该属性的彩色部分的大小代表了具有该属性的事例的百分比。</span><span class="sxs-lookup"><span data-stu-id="8fd63-175">A histogram is a bar with different colors in it, where each color represents an attribute, and the size of the colored section for that attribute represents the percentage of cases with that attribute.</span></span>  
  
2.  <span data-ttu-id="8fd63-176">比较您重命名的分类和的直方图 `Pacific Cluster` `Largest Cluster` 。</span><span class="sxs-lookup"><span data-stu-id="8fd63-176">Compare the histograms for the clusters that you renamed `Pacific Cluster` and `Largest Cluster`.</span></span> <span data-ttu-id="8fd63-177">每个分类显示在不同的列中。</span><span class="sxs-lookup"><span data-stu-id="8fd63-177">Each cluster appears in a different column.</span></span>  
  
     <span data-ttu-id="8fd63-178">这些颜色看起来都像是纯色，但却是不同的。</span><span class="sxs-lookup"><span data-stu-id="8fd63-178">Both look like solid colors, but the colors are different.</span></span>  
  
3.  <span data-ttu-id="8fd63-179">在行中，将鼠标悬停在的 `Region` 彩色直方图上 `Largest Cluster` 。</span><span class="sxs-lookup"><span data-stu-id="8fd63-179">In the `Region` row, pause the mouse over the colored histogram for `Largest Cluster`.</span></span>  
  
     <span data-ttu-id="8fd63-180">工具提示将显示一些值，这些值显示了来自每个区域的事例所占的实际百分比。</span><span class="sxs-lookup"><span data-stu-id="8fd63-180">The ToolTip displays values that show the actual percentages of cases from each region.</span></span>  
  
4.  <span data-ttu-id="8fd63-181">右键单击行中的彩色直方图 `Region` `Pacific Cluster` ，选择 "**钻取**"，然后选择 "**仅限模型列**"。</span><span class="sxs-lookup"><span data-stu-id="8fd63-181">Right-click the colored histogram in the `Region` row for `Pacific Cluster`, select **Drill Through**, and then select **Model Columns Only**.</span></span>  
  
5.  <span data-ttu-id="8fd63-182">移动滚动条可以查看此分类中的所有客户。</span><span class="sxs-lookup"><span data-stu-id="8fd63-182">Move the scroll bar to review all of the customers in this cluster.</span></span>  
  
     <span data-ttu-id="8fd63-183">通过再次钻取到详细信息，可以看到此分类包括的大多数订单都来自太平洋地区，但也有一些订单来自北美和欧洲地区。</span><span class="sxs-lookup"><span data-stu-id="8fd63-183">Again, from drilling through to the details you can see that the cluster contains mostly orders from the Pacific region but also a few from the North America and Europe regions.</span></span>  
  
6.  <span data-ttu-id="8fd63-184">关闭 "**钻取**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="8fd63-184">Close the **Drill Through** dialog box.</span></span>  
  
 [<span data-ttu-id="8fd63-185">返回页首</span><span class="sxs-lookup"><span data-stu-id="8fd63-185">Back to Top</span></span>](#bkmk_CDiagram)  
  
##  <a name="cluster-characteristics-tab"></a><a name="bkmk_CChars"></a><span data-ttu-id="8fd63-186">分类特征选项卡</span><span class="sxs-lookup"><span data-stu-id="8fd63-186">Cluster Characteristics Tab</span></span>  
 <span data-ttu-id="8fd63-187">"**分类特征**" 选项卡通过显示直观地表示所选分类的属性值重要性的栏来汇总群集中各状态之间的转换。</span><span class="sxs-lookup"><span data-stu-id="8fd63-187">The **Cluster Characteristics** tab summarizes the transitions between states in a cluster by displaying bars that visually represent the importance of the attribute value for the selected cluster.</span></span> <span data-ttu-id="8fd63-188">"**变量**" 列告诉您哪个模型对于所选的分类或总体非常重要：特定值或值之间的关系（称为*转换*）。</span><span class="sxs-lookup"><span data-stu-id="8fd63-188">The **Variables** column tells you what the model found to be important for the selected cluster or population: either a particular value or the relationship between values, known as *transition*.</span></span> <span data-ttu-id="8fd63-189">"**值**" 列提供关于值或转换的更多详细信息，"**概率**" 列直观地表示此属性或转换的权重。</span><span class="sxs-lookup"><span data-stu-id="8fd63-189">The **Values** column provides more detail about the value or transition, and the **Probability** column visually represents the weight of this attribute or transition.</span></span>  
  
#### <a name="to-view-the-important-attributes-for-a-cluster"></a><span data-ttu-id="8fd63-190">查看分类的重要属性</span><span class="sxs-lookup"><span data-stu-id="8fd63-190">To view the important attributes for a cluster</span></span>  
  
1.  <span data-ttu-id="8fd63-191">在 "**分类**" 下拉列表中，选择 `Pacific Cluster` 。</span><span class="sxs-lookup"><span data-stu-id="8fd63-191">In the **Cluster** dropdown list, select `Pacific Cluster`.</span></span>  
  
     <span data-ttu-id="8fd63-192">列表将更新以显示已重命名的分类的特征 `Pacific Cluster` 。</span><span class="sxs-lookup"><span data-stu-id="8fd63-192">The list updates to show the characteristics of the cluster that you renamed `Pacific Cluster`.</span></span> <span data-ttu-id="8fd63-193">在此群集中，最重要的特征是 `Region` 。</span><span class="sxs-lookup"><span data-stu-id="8fd63-193">In this cluster, the most important characteristic is `Region`.</span></span>  
  
2.  <span data-ttu-id="8fd63-194">将鼠标悬停在行中的阴影条上 `Region` 。</span><span class="sxs-lookup"><span data-stu-id="8fd63-194">Pause the mouse over the shaded bar in the row for `Region`.</span></span>  
  
     <span data-ttu-id="8fd63-195">该值为“Pacific”的概率非常高。</span><span class="sxs-lookup"><span data-stu-id="8fd63-195">The probability of the value being Pacific is very high.</span></span> <span data-ttu-id="8fd63-196">有关如何解释这些值的详细信息，请参阅[Microsoft 顺序分析和聚类分析算法技术参考](../../2014/analysis-services/data-mining/microsoft-sequence-clustering-algorithm-technical-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="8fd63-196">For more information about how to interpret these values, see [Microsoft Sequence Clustering Algorithm Technical Reference](../../2014/analysis-services/data-mining/microsoft-sequence-clustering-algorithm-technical-reference.md).</span></span>  
  
3.  <span data-ttu-id="8fd63-197">仔细查看分类的特征列表，直至找到第一个转换行。</span><span class="sxs-lookup"><span data-stu-id="8fd63-197">Look through the list of characteristics for the cluster until you find the first transition row.</span></span>  
  
4.  <span data-ttu-id="8fd63-198">转换行包含**Variables**列中的文本转换，以及**值**列中的顺序属性值的一些组合。</span><span class="sxs-lookup"><span data-stu-id="8fd63-198">A transition row contains the text Transition in the **Variables** column, and some combination of sequential attribute values in the **Value** column.</span></span> <span data-ttu-id="8fd63-199">该序列也可以包含起点和缺少值。</span><span class="sxs-lookup"><span data-stu-id="8fd63-199">The sequence can also contain starting points and missing values.</span></span>  
  
     <span data-ttu-id="8fd63-200">例如，假设过渡具有值 "[Start]-> 公路轮胎管"。</span><span class="sxs-lookup"><span data-stu-id="8fd63-200">For example, suppose the transition has the value, [Start] -> Road Tire Tube.</span></span> <span data-ttu-id="8fd63-201">这意味着此分类中的客户通常首先将 Road Tire Tube 放入购物篮中。</span><span class="sxs-lookup"><span data-stu-id="8fd63-201">This means that customers in this cluster frequently put the Road Tire Tube in their shopping basket first.</span></span> <span data-ttu-id="8fd63-202">这可能表示该产品是客户首先挑选出的受欢迎商品，或者只表示该产品在购物场所容易找到。</span><span class="sxs-lookup"><span data-stu-id="8fd63-202">This might signify that the product is a popular item that customers seek out first, or it might only indicate that the product is easy to find on the purchasing site.</span></span>  
  
5.  <span data-ttu-id="8fd63-203">滚动列表，直到找到其中没有 **[开始]** 或**缺少**的第一个转换。</span><span class="sxs-lookup"><span data-stu-id="8fd63-203">Scroll through the list until you find the first transition that does not have **[Start]** or **missing** in it.</span></span>  
  
     <span data-ttu-id="8fd63-204">例如，假设您找到了过渡、**旅行轮胎、旅行轮胎管**。</span><span class="sxs-lookup"><span data-stu-id="8fd63-204">For example, suppose you find the transition, **Touring Tire, Touring Tire Tube**.</span></span> <span data-ttu-id="8fd63-205">这意味着此分类中的客户通常将这些项一起放入购物篮中，而且是严格按照这个顺序放入。</span><span class="sxs-lookup"><span data-stu-id="8fd63-205">This means that customers in this cluster frequently purchased these items together, in exactly this order.</span></span>  
  
6.  <span data-ttu-id="8fd63-206">将鼠标悬停在此转换的阴影条上。</span><span class="sxs-lookup"><span data-stu-id="8fd63-206">Pause the mouse over the shaded bar for this transition.</span></span>  
  
     <span data-ttu-id="8fd63-207">此转换的概率以百分比显示。</span><span class="sxs-lookup"><span data-stu-id="8fd63-207">The probability of this transition is displayed as a percentage.</span></span>  
  
7.  <span data-ttu-id="8fd63-208">在 "**分类**" 下拉列表中，选择 "\*\*总体 (所有) \*\*"。</span><span class="sxs-lookup"><span data-stu-id="8fd63-208">In the **Cluster** dropdown list, select **Population (All)**.</span></span>  
  
     <span data-ttu-id="8fd63-209">该属性列表会更新为显示用于创建模型的所有订单的特征。</span><span class="sxs-lookup"><span data-stu-id="8fd63-209">The list of attributes updates to show the characteristics of all orders used to create the model.</span></span> <span data-ttu-id="8fd63-210">在此挖掘模型中，区分分类的最重要的特征是 `Region` ，值为**北美**。</span><span class="sxs-lookup"><span data-stu-id="8fd63-210">In this mining model, the most important characteristic for distinguishing between clusters is `Region`, with a value of **North America**.</span></span>  
  
 <span data-ttu-id="8fd63-211">在查看这些任务后，您认识到两点。</span><span class="sxs-lookup"><span data-stu-id="8fd63-211">After reviewing these tasks, you realize two things.</span></span> <span data-ttu-id="8fd63-212">第一点是您需要大量数据来获取有意义数量的组合。</span><span class="sxs-lookup"><span data-stu-id="8fd63-212">The first is that you need a lot of data to obtain a meaningful number of combinations.</span></span> <span data-ttu-id="8fd63-213">例如，概率最高的序列可能包含 **[Start]** 或**缺少**状态。</span><span class="sxs-lookup"><span data-stu-id="8fd63-213">For example, the sequences with the highest probabilities are likely to include a **[Start]** or **Missing** state.</span></span>  
  
 <span data-ttu-id="8fd63-214">第二种情况是，对的属性有一个强大的群集效果 `Region` ，这使得更难查看序列组。</span><span class="sxs-lookup"><span data-stu-id="8fd63-214">The second is that there is a strong clustering effect on attributes for `Region`, which makes it more difficult to see the groups of sequences.</span></span> <span data-ttu-id="8fd63-215">因此，您决定创建另一个模型，该模型只使用序列，而且不包括区域或收入的列。</span><span class="sxs-lookup"><span data-stu-id="8fd63-215">Therefore, you decide to create another model that uses sequences only, and does not include the columns for region or income.</span></span>  
  
 [<span data-ttu-id="8fd63-216">返回页首</span><span class="sxs-lookup"><span data-stu-id="8fd63-216">Back to Top</span></span>](#bkmk_CDiagram)  
  
##  <a name="cluster-discrimination-tab"></a><a name="bkmk_CDiscrim2"></a><span data-ttu-id="8fd63-217">分类对比选项卡</span><span class="sxs-lookup"><span data-stu-id="8fd63-217">Cluster Discrimination Tab</span></span>  
 <span data-ttu-id="8fd63-218">"**分类对比**" 选项卡可帮助你比较两个分类，以确定哪些属性区分不同的群集。</span><span class="sxs-lookup"><span data-stu-id="8fd63-218">The **Cluster Discrimination** tab helps you compare two clusters, to determine which attributes distinguish a particular cluster from another cluster.</span></span> <span data-ttu-id="8fd63-219">该选项卡包含四列：**变量**、**值**、**群集 1**和**分类 2**。</span><span class="sxs-lookup"><span data-stu-id="8fd63-219">The tab contains four columns: **Variables**, **Values**, **Cluster 1**, and **Cluster 2**.</span></span>  <span data-ttu-id="8fd63-220">你可以选择要用作**群集 1**和**分类 2**的任何群集。</span><span class="sxs-lookup"><span data-stu-id="8fd63-220">You can choose any cluster to use as **Cluster 1** and **Cluster 2**.</span></span>  
  
 <span data-ttu-id="8fd63-221">"**变量**" 列告诉您属性的名称，该名称可以是列名，也可以是列名称和 word**转换**的组合。</span><span class="sxs-lookup"><span data-stu-id="8fd63-221">The **Variables** column tells you the name of the attribute, which can either be a column name or combination of column name and the word **transition**.</span></span> <span data-ttu-id="8fd63-222">"**值**" 列显示属性或转换的确切值。</span><span class="sxs-lookup"><span data-stu-id="8fd63-222">The **Values** column shows the exact value of the attribute or the transition.</span></span> <span data-ttu-id="8fd63-223">"**分类 1** " 和 "**分类 2** " 列中的阴影条指示要比较的分类中的属性的强度。</span><span class="sxs-lookup"><span data-stu-id="8fd63-223">The shaded bars in the columns for **Cluster 1** and **Cluster 2** indicate the strength of the attribute in the clusters that you are comparing.</span></span> <span data-ttu-id="8fd63-224">阴影条越长，分类包括具有该属性的事例的可能性越大。</span><span class="sxs-lookup"><span data-stu-id="8fd63-224">The longer the bar, the more the cluster is likely to include cases with that attribute.</span></span>  
  
#### <a name="to-compare-two-clusters-by-using-the-cluster-discrimination-tab"></a><span data-ttu-id="8fd63-225">使用“分类对比”选项卡比较两个分类</span><span class="sxs-lookup"><span data-stu-id="8fd63-225">To compare two clusters by using the Cluster Discrimination tab</span></span>  
  
1.  <span data-ttu-id="8fd63-226">在 "**分类对比**" 选项卡中，为 "**分类 1**" 选择 `Pacific Cluster` 。</span><span class="sxs-lookup"><span data-stu-id="8fd63-226">In the **Cluster Discrimination** tab, for **Cluster 1**, select `Pacific Cluster`.</span></span>  
  
     <span data-ttu-id="8fd63-227">默认情况下，**群集 2**的选择将更改为**太平洋群集的补充**。</span><span class="sxs-lookup"><span data-stu-id="8fd63-227">By default, the selection for **Cluster 2** changes to **Complement of Pacific Cluster**.</span></span>  
  
     <span data-ttu-id="8fd63-228">与所有其他情况区分开来的顶级属性 `Pacific Cluster` 是区域。</span><span class="sxs-lookup"><span data-stu-id="8fd63-228">The top attribute that distinguishes `Pacific Cluster` from all other cases is the region.</span></span> <span data-ttu-id="8fd63-229">Region 是聚类分析的一个强属性，以至于它掩盖了其他属性。</span><span class="sxs-lookup"><span data-stu-id="8fd63-229">Region is such a strong attribute for clustering that it obscures other attributes.</span></span> <span data-ttu-id="8fd63-230">为了避免这种效果，请尝试相互比较几个较小的分类。</span><span class="sxs-lookup"><span data-stu-id="8fd63-230">To avoid this effect, try comparing several of the smaller clusters to each other.</span></span> <span data-ttu-id="8fd63-231">在进行比较时，属性列表会发生变化，可能包括模型之间的更多转换。</span><span class="sxs-lookup"><span data-stu-id="8fd63-231">When you do so, the list of attributes changes and might include more transitions between models.</span></span>  
  
2.  <span data-ttu-id="8fd63-232">找到转换行，将鼠标悬停在阴影条上。</span><span class="sxs-lookup"><span data-stu-id="8fd63-232">Locate a transition row, and pause the mouse over the shaded bar.</span></span>  
  
     <span data-ttu-id="8fd63-233">"**值**" 列中的项可以包括状态和转换。</span><span class="sxs-lookup"><span data-stu-id="8fd63-233">The items in the **Values** column can include both states and transitions.</span></span> <span data-ttu-id="8fd63-234">各项的明暗度指示对比分数。</span><span class="sxs-lookup"><span data-stu-id="8fd63-234">The shading for each item indicates the discrimination score.</span></span> <span data-ttu-id="8fd63-235">若要详细了解不同分数的含义，请参阅[顺序分析和聚类分析模型的挖掘模型内容 &#40;Analysis Services 数据挖掘&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-sequence-clustering-models.md)。</span><span class="sxs-lookup"><span data-stu-id="8fd63-235">To learn more about the meaning of different scores, see [Mining Model Content for Sequence Clustering Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-sequence-clustering-models.md).</span></span>  
  
 [<span data-ttu-id="8fd63-236">返回页首</span><span class="sxs-lookup"><span data-stu-id="8fd63-236">Back to Top</span></span>](#bkmk_CDiagram)  
  
##  <a name="state-transitions-tab"></a><a name="bkmk_StateTran"></a><span data-ttu-id="8fd63-237">"状态转换" 选项卡</span><span class="sxs-lookup"><span data-stu-id="8fd63-237">State Transitions Tab</span></span>  
 <span data-ttu-id="8fd63-238">在 "**状态转换**" 选项卡上，可以选择一个群集并浏览其状态转换。</span><span class="sxs-lookup"><span data-stu-id="8fd63-238">On the **State Transitions** tab, you can select a cluster and browse through its state transitions.</span></span> <span data-ttu-id="8fd63-239">如果从 "分类" 下拉列表中选择 "\*\*总体" (所有) \*\* ，则关系图将显示整个挖掘模型的状态分布。</span><span class="sxs-lookup"><span data-stu-id="8fd63-239">If you select **Population (All)** from the cluster drop-down list, the diagram shows the distribution of states for the whole mining model.</span></span>  
  
 <span data-ttu-id="8fd63-240">图中的每个节点都表示一个状态，或您试图分析的序列的可能值。</span><span class="sxs-lookup"><span data-stu-id="8fd63-240">Each node in the graph represents a state, or possible value, of the sequences that you are trying to analyze.</span></span> <span data-ttu-id="8fd63-241">节点的背景色表示该状态的频率。</span><span class="sxs-lookup"><span data-stu-id="8fd63-241">The background color of the nodes represents the frequency of that state.</span></span> <span data-ttu-id="8fd63-242">一些状态之间用线条连接，指示这些状态之间的转换。</span><span class="sxs-lookup"><span data-stu-id="8fd63-242">Lines connect some states, indicating a transition between states.</span></span> <span data-ttu-id="8fd63-243">可以上下移动滑块，以更改转换的概率阈值。</span><span class="sxs-lookup"><span data-stu-id="8fd63-243">You can move the slider up or down to change the probability threshold for the transitions.</span></span> <span data-ttu-id="8fd63-244">数字与某些节点相关联，指示该状态的概率。</span><span class="sxs-lookup"><span data-stu-id="8fd63-244">Numbers are associated with some nodes, indicating the probability of that state.</span></span>  
  
#### <a name="to-explore-the-relationships-in-the-state-transition-tab"></a><span data-ttu-id="8fd63-245">在“状态转换”选项卡中浏览关系</span><span class="sxs-lookup"><span data-stu-id="8fd63-245">To explore the relationships in the State Transition tab</span></span>  
  
1.  <span data-ttu-id="8fd63-246">在挖掘模型查看器的 "**状态转换**" 选项卡中， `Pacific Cluster` 从分类列表中选择。</span><span class="sxs-lookup"><span data-stu-id="8fd63-246">In the **State Transitions** tab of the Mining Model viewer, select `Pacific Cluster` from the list of clusters.</span></span> <span data-ttu-id="8fd63-247">确保选中 "**显示边缘标签**" 选项。</span><span class="sxs-lookup"><span data-stu-id="8fd63-247">Ensure that the **Show Edge Labels** option is selected.</span></span>  
  
     <span data-ttu-id="8fd63-248">该图会更新为显示此分类中最常见的转换。</span><span class="sxs-lookup"><span data-stu-id="8fd63-248">The graph updates to show the transitions that are most common in this cluster.</span></span>  
  
2.  <span data-ttu-id="8fd63-249">单击通过线条连接到另一个节点的任何节点。</span><span class="sxs-lookup"><span data-stu-id="8fd63-249">Click any node that is connected by a line to another node.</span></span>  
  
     <span data-ttu-id="8fd63-250">该图进行了更新，并且突出显示相关的节点。</span><span class="sxs-lookup"><span data-stu-id="8fd63-250">The graph is updated and highlights the related nodes.</span></span> <span data-ttu-id="8fd63-251">线条旁的数值指示转换的概率。</span><span class="sxs-lookup"><span data-stu-id="8fd63-251">The numeric value next to the line indicates the probability of the transition.</span></span>  
  
3.  <span data-ttu-id="8fd63-252">将滑块向上提升到**所有链接**，以增加图形中包含的转换数。</span><span class="sxs-lookup"><span data-stu-id="8fd63-252">Raise the slider up to **All Links**, to increase the number of transitions included in the graph.</span></span>  
  
4.  <span data-ttu-id="8fd63-253">选择 "填充" (**分类**中的\*\*所有) \*\* 。</span><span class="sxs-lookup"><span data-stu-id="8fd63-253">Select **Population (All)** from **Cluster**.</span></span>  
  
     <span data-ttu-id="8fd63-254">请注意，在加载另一个分类时，该图会重置为默认显示设置，因此滑块控件也会重置到中间位置。</span><span class="sxs-lookup"><span data-stu-id="8fd63-254">Note that when you load a different cluster, the graph resets to the default display settings, so the slider control is reset to the middle position.</span></span>  
  
5.  <span data-ttu-id="8fd63-255">单击关系图中最暗的节点，应为 "**运动-100**"。</span><span class="sxs-lookup"><span data-stu-id="8fd63-255">Click the darkest node in the graph, which should be **Sport-100**.</span></span>  
  
     <span data-ttu-id="8fd63-256">请注意，产品之间没有线条相互连接。</span><span class="sxs-lookup"><span data-stu-id="8fd63-256">Note that there are no lines connecting this product to other products.</span></span>  
  
6.  <span data-ttu-id="8fd63-257">将滑块向上提升一级，以增加图中包括的转换的数量。</span><span class="sxs-lookup"><span data-stu-id="8fd63-257">Raise the slider up one step, to increase the number of transitions included in the graph.</span></span> <span data-ttu-id="8fd63-258">目前尚无所有**链接**。</span><span class="sxs-lookup"><span data-stu-id="8fd63-258">Do not go all the way to **All Links** yet.</span></span>  
  
     <span data-ttu-id="8fd63-259">该图会添加更多的转换，从而进行更新，但这些转换都没有包括 Sport-100 型号。</span><span class="sxs-lookup"><span data-stu-id="8fd63-259">The graph is updated by adding several more transitions to the graph, but none that include the Sport-100 model.</span></span>  
  
7.  <span data-ttu-id="8fd63-260">将滑块控件一直移动到**所有链接**。</span><span class="sxs-lookup"><span data-stu-id="8fd63-260">Move the slider control all the way to **All Links**.</span></span> <span data-ttu-id="8fd63-261">如果尚未选择 Sport-100 节点，请单击该节点。</span><span class="sxs-lookup"><span data-stu-id="8fd63-261">Click the Sport-100 node if it is not already selected.</span></span>  
  
     <span data-ttu-id="8fd63-262">该图会更新为显示包括 Sport-100 产品的很多转换。</span><span class="sxs-lookup"><span data-stu-id="8fd63-262">The graph updates to show many transitions that include the Sport-100 product.</span></span> <span data-ttu-id="8fd63-263">连接线条的箭头的方向指示 Sport-100 项是作为配对中的第一项还是第二项选择的。</span><span class="sxs-lookup"><span data-stu-id="8fd63-263">The direction of the arrow on the connecting line tells you whether the Sport-100 item was selected as the first item or the second item in the pair.</span></span>  
  
8.  <span data-ttu-id="8fd63-264">单击 Touring Tire 的节点，将滑块控件向下移回至中间位置。</span><span class="sxs-lookup"><span data-stu-id="8fd63-264">Clicking the node for Touring Tire and move the slider control back down to the middle position.</span></span>  
  
     <span data-ttu-id="8fd63-265">首先，有许多将旅行轮胎连接到其他产品的转换线路，但当您提高概率阈值时，从图形中消除的转换可能性越小，只留下过渡，旅行轮胎 > 旅行轮胎管。</span><span class="sxs-lookup"><span data-stu-id="8fd63-265">At first, there are many transition lines connecting Touring Tire to other products, but when you raise the probability threshold, the less likely transitions are eliminated from the graph, leaving just the transition, Touring Tire > Touring Tire Tube.</span></span> <span data-ttu-id="8fd63-266">此转换的含义是如果客户将 Touring Tire 放入购物篮，则该客户接下来将 Touring Tire Tube 也放入购物篮的概率非常高。</span><span class="sxs-lookup"><span data-stu-id="8fd63-266">This transition means that if a customer puts a Touring Tire into the shopping basket, there is a strong probability that the customer will next put a Touring Tire Tube into the basket.</span></span>  
  
 [<span data-ttu-id="8fd63-267">返回页首</span><span class="sxs-lookup"><span data-stu-id="8fd63-267">Back to Top</span></span>](#bkmk_CDiagram)  
  
##  <a name="generic-content-tree-viewer"></a><a name="bkmk_Generic"></a><span data-ttu-id="8fd63-268">一般内容树查看器</span><span class="sxs-lookup"><span data-stu-id="8fd63-268">Generic Content Tree Viewer</span></span>  
 <span data-ttu-id="8fd63-269">此查看器可用于所有模型，无论算法和模型类型为何均为如此。</span><span class="sxs-lookup"><span data-stu-id="8fd63-269">This viewer can be used for all models, regardless of the algorithm or model type.</span></span> <span data-ttu-id="8fd63-270">"**查看器**" 下拉列表中提供了**MicrosoftGeneric 内容树查看器**。</span><span class="sxs-lookup"><span data-stu-id="8fd63-270">The **MicrosoftGeneric Content Tree Viewer** is available from the **Viewer** drop-down list.</span></span>  
  
 <span data-ttu-id="8fd63-271">内容树是任何挖掘模型的表示形式，由一系列节点组成，其中每个节点都表示关于定型数据的已了解的知识。</span><span class="sxs-lookup"><span data-stu-id="8fd63-271">A content tree is a representation of any mining model as a series of nodes, wherein each node represents learned knowledge about the training data.</span></span> <span data-ttu-id="8fd63-272">节点可以包含一种模式、一组规则、一个分类或共享某些属性的日期范围的定义。</span><span class="sxs-lookup"><span data-stu-id="8fd63-272">The node can contain a pattern, a set of rules, a cluster, or the definition of a range of dates that share some attributes.</span></span> <span data-ttu-id="8fd63-273">根据算法和可预测属性的不同，节点的具体内容会有所不同，但内容的通用表示形式是相同的。</span><span class="sxs-lookup"><span data-stu-id="8fd63-273">The exact content of the node differs depending on the algorithm and the predictable attribute, but the general representation of the content is the same.</span></span>  
  
 <span data-ttu-id="8fd63-274">您可以展开每个节点以查看详细信息的递增级别，并可以将任何节点的内容复制到剪贴板。</span><span class="sxs-lookup"><span data-stu-id="8fd63-274">You can expand each node to see increasing levels of detail, and copy the content of any node to the Clipboard.</span></span> <span data-ttu-id="8fd63-275">有关详细信息，请参阅 [使用 Microsoft 一般内容树查看器浏览模型](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="8fd63-275">For more information, see [Browse a Model Using the Microsoft Generic Content Tree Viewer](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-generic-content-tree-viewer.md).</span></span>  
  
#### <a name="to-view-details-for-a-sequence-clustering-model-by-using-the-generic-content-tree-viewer"></a><span data-ttu-id="8fd63-276">使用一般内容树查看器查看顺序分析和聚类分析模型的详细信息</span><span class="sxs-lookup"><span data-stu-id="8fd63-276">To view details for a sequence clustering model by using the Generic Content Tree Viewer</span></span>  
  
1.  <span data-ttu-id="8fd63-277">在 "**挖掘模型查看器**" 选项卡中，单击 "**查看器**" 列表，然后选择 " **Microsoft 一般内容树查看器**"。</span><span class="sxs-lookup"><span data-stu-id="8fd63-277">In the **Mining Model Viewer** tab, click the **Viewer** list, and select **Microsoft Generic Content Tree viewer**.</span></span>  
  
2.  <span data-ttu-id="8fd63-278">在 "**节点标题**" 窗格中，单击 "" `Pacific Cluster (1)` 。</span><span class="sxs-lookup"><span data-stu-id="8fd63-278">In the **Node Caption** pane, click `Pacific Cluster (1)`.</span></span>  
  
     <span data-ttu-id="8fd63-279">此节点的名称同时包含为分类指定的友好名称和基础节点 ID。</span><span class="sxs-lookup"><span data-stu-id="8fd63-279">The name for this node contains both the friendly name that you assigned to the cluster and the underlying node ID.</span></span> <span data-ttu-id="8fd63-280">可以使用节点 ID 来深化到模型中的其他详细信息。</span><span class="sxs-lookup"><span data-stu-id="8fd63-280">You can use the node IDs to drill down into additional detail in the model.</span></span>  
  
3.  <span data-ttu-id="8fd63-281">展开 "分类 1" 的第一个子节点，名为 "**序列级别**"。</span><span class="sxs-lookup"><span data-stu-id="8fd63-281">Expand the first child node, named **Sequence level for cluster 1**.</span></span>  
  
     <span data-ttu-id="8fd63-282">分类的序列级别节点包含了关于该分类中的状态和转换的详细信息。</span><span class="sxs-lookup"><span data-stu-id="8fd63-282">The sequence level node for a cluster contains details about the states and transitions that are included in that cluster.</span></span> <span data-ttu-id="8fd63-283">可以使用 NODE_DISTRIBUTION 列中的这些详细信息，浏览每个节点或模型的序列和状态。</span><span class="sxs-lookup"><span data-stu-id="8fd63-283">You can use these details, available in the NODE_DISTRIBUTION column, to explore the sequences and the states for each cluster or for the model as a while.</span></span>  
  
4.  <span data-ttu-id="8fd63-284">继续展开节点并在 HTML 查看器窗格中查看详细信息。</span><span class="sxs-lookup"><span data-stu-id="8fd63-284">Continue to expand nodes and view the details in the HTML viewer pane.</span></span>  
  
 <span data-ttu-id="8fd63-285">有关挖掘模型内容以及如何使用查看器中的详细信息的详细信息，请参阅[顺序分析和聚类分析模型的挖掘模型内容 &#40;Analysis Services 数据挖掘&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-sequence-clustering-models.md)。</span><span class="sxs-lookup"><span data-stu-id="8fd63-285">For more information about the mining model content, and how to use the details in the viewer, see [Mining Model Content for Sequence Clustering Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-sequence-clustering-models.md).</span></span>  
  
 [<span data-ttu-id="8fd63-286">返回页首</span><span class="sxs-lookup"><span data-stu-id="8fd63-286">Back to Top</span></span>](#bkmk_CDiagram)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="8fd63-287">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="8fd63-287">Next Task in Lesson</span></span>  
 [<span data-ttu-id="8fd63-288">&#40;中级数据挖掘教程创建相关的顺序分析和聚类分析模型&#41;</span><span class="sxs-lookup"><span data-stu-id="8fd63-288">Creating a Related Sequence Clustering Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-related-sequence-clustering-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="8fd63-289">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8fd63-289">See Also</span></span>  
 <span data-ttu-id="8fd63-290">[Microsoft 顺序分析和聚类分析算法](../../2014/analysis-services/data-mining/microsoft-sequence-clustering-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="8fd63-290">[Microsoft Sequence Clustering Algorithm](../../2014/analysis-services/data-mining/microsoft-sequence-clustering-algorithm.md) </span></span>  
 [<span data-ttu-id="8fd63-291">顺序分析和聚类分析模型查询示例</span><span class="sxs-lookup"><span data-stu-id="8fd63-291">Sequence Clustering Model Query Examples</span></span>](../../2014/analysis-services/data-mining/sequence-clustering-model-query-examples.md)  
  
  
