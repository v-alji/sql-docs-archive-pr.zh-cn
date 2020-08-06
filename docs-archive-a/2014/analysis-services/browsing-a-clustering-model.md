---
title: 浏览聚类分析模型 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, browsing
- mining models, viewing
- clustering [data mining]
- mining model, clustering
ms.assetid: 7f3f0949-d791-403a-88e2-54cb1a803dae
author: minewiskan
ms.author: owend
ms.openlocfilehash: f1d508603acd29fde981bddc5642b54ca9413f5f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579325"
---
# <a name="browsing-a-clustering-model"></a><span data-ttu-id="3a071-102">浏览聚类分析模型</span><span class="sxs-lookup"><span data-stu-id="3a071-102">Browsing a Clustering Model</span></span>
  <span data-ttu-id="3a071-103">使用 "**浏览**" 打开聚类分析模型时，该模型将显示在交互式查看器中，类似于中的聚类分析查看器 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="3a071-103">When you open a clustering model using **Browse**, the model is displayed in an interactive viewer, similar to the clustering viewer in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="3a071-104">该查看器可帮助您浏览已创建的分类并了解分类特征。</span><span class="sxs-lookup"><span data-stu-id="3a071-104">The viewer helps you explore the clusters that were created, and understand cluster characteristics.</span></span> <span data-ttu-id="3a071-105">您还可以将各个段与其他段或填充进行比较和对比。</span><span class="sxs-lookup"><span data-stu-id="3a071-105">You can also compare and contrast individual segments with other segments or with the population.</span></span>  
  
##  <a name="explore-the-model"></a><a name="BKMK_Tabs"></a><span data-ttu-id="3a071-106">浏览模型</span><span class="sxs-lookup"><span data-stu-id="3a071-106">Explore the Model</span></span>  
 <span data-ttu-id="3a071-107">"**浏览**" 窗口包含以下工具，可帮助您了解聚类分析模型并探索底层数据组的属性：</span><span class="sxs-lookup"><span data-stu-id="3a071-107">The **Browse** window includes the following tools to help you understand your clustering model and explore the attributes of the underlying data groups:</span></span>  
  
-   [<span data-ttu-id="3a071-108">分类关系图</span><span class="sxs-lookup"><span data-stu-id="3a071-108">Cluster Diagram</span></span>](#BKMK_ClusterDiagram)  
  
-   [<span data-ttu-id="3a071-109">分类剖面图</span><span class="sxs-lookup"><span data-stu-id="3a071-109">Cluster Profiles</span></span>](#BKMK_ClusterProfiles)  
  
-   [<span data-ttu-id="3a071-110">分类特征</span><span class="sxs-lookup"><span data-stu-id="3a071-110">Cluster Characteristics</span></span>](#BKMK_ClusterCharacteristics)  
  
-   [<span data-ttu-id="3a071-111">分类对比</span><span class="sxs-lookup"><span data-stu-id="3a071-111">Cluster Discrimination</span></span>](#BKMK_ClusterDiscrimination)  
  
 <span data-ttu-id="3a071-112">若要对聚类分析模型进行试验，可以使用示例数据工作簿的 "培训" 选项卡上的示例数据，并使用 "群集" 向导生成聚类分析模型[&#40;用于 Excel 的数据挖掘外接程序&#41;](cluster-wizard-data-mining-add-ins-for-excel.md)和所有默认值。</span><span class="sxs-lookup"><span data-stu-id="3a071-112">To experiment with a clustering model, you can use the sample data on the Training tab of the sample data workbook, and build a clustering model using [Cluster Wizard &#40;Data Mining Add-ins for Excel&#41;](cluster-wizard-data-mining-add-ins-for-excel.md) and all the defaults.</span></span>  
  
###  <a name="cluster-diagram"></a><a name="BKMK_ClusterDiagram"></a><span data-ttu-id="3a071-113">分类关系图</span><span class="sxs-lookup"><span data-stu-id="3a071-113">Cluster Diagram</span></span>  
 <span data-ttu-id="3a071-114">"**分类关系图**" 选项卡显示挖掘模型中的所有分类。</span><span class="sxs-lookup"><span data-stu-id="3a071-114">The **Cluster Diagram** tab displays all the clusters that are in a mining model.</span></span> <span data-ttu-id="3a071-115">在这里，可以查看数据集中有多少个不同分组，以及这些分组之间的远近。</span><span class="sxs-lookup"><span data-stu-id="3a071-115">Here you can see how many different groupings were found in your data set, and how near or far they are from each other.</span></span>  
  
##### <a name="explore-the-cluster-diagram"></a><span data-ttu-id="3a071-116">探索分类关系图</span><span class="sxs-lookup"><span data-stu-id="3a071-116">Explore the cluster diagram</span></span>  
  
1.  <span data-ttu-id="3a071-117">单击关系图中的“分类 1”。</span><span class="sxs-lookup"><span data-stu-id="3a071-117">Click Cluster 1 in the diagram.</span></span>  
  
     <span data-ttu-id="3a071-118">注意连接所有分类的灰色线条如何变化以便以浅蓝色突出显示指向所选分类的线条。</span><span class="sxs-lookup"><span data-stu-id="3a071-118">Note how the gray lines connecting all clusters change so that lines leading to the selected cluster are highlighted in bright blue.</span></span>  
  
     <span data-ttu-id="3a071-119">![分类关系图介绍](media/dm13-cluster-diagram-intro.gif "分类关系图介绍")</span><span class="sxs-lookup"><span data-stu-id="3a071-119">![cluster diagram intro](media/dm13-cluster-diagram-intro.gif "cluster diagram intro")</span></span>  
  
     <span data-ttu-id="3a071-120">将一个分类连接到另一个分类的线条强度表示群集相似性的强度。</span><span class="sxs-lookup"><span data-stu-id="3a071-120">The intensity of the line that connects one cluster to another represents the strength of the similarity of the clusters.</span></span> <span data-ttu-id="3a071-121">如果明暗度较浅或无明暗度，则表示分类的相似程度较低。</span><span class="sxs-lookup"><span data-stu-id="3a071-121">If the shading is light or nonexistent, the clusters are not very similar.</span></span> <span data-ttu-id="3a071-122">连线颜色越深，表示两个分类之间的相似性越大。</span><span class="sxs-lookup"><span data-stu-id="3a071-122">As the line becomes darker, it indicates that the similarity between the two clusters is stronger.</span></span>  
  
2.  <span data-ttu-id="3a071-123">单击并拖动分类关系图左侧的滑块可调整查看器显示的线条数目。</span><span class="sxs-lookup"><span data-stu-id="3a071-123">Click and drag the slider to the left of the cluster diagram, to adjust how many lines the viewer shows.</span></span>  
  
     <span data-ttu-id="3a071-124">向下拖动滑块时，仅显示分类间的最强链接。</span><span class="sxs-lookup"><span data-stu-id="3a071-124">When you drag the slider down, only the strongest links between clusters are shown.</span></span> <span data-ttu-id="3a071-125">这有助于您重点关注相关的组。</span><span class="sxs-lookup"><span data-stu-id="3a071-125">This helps you focus on related groups.</span></span>  
  
3.  <span data-ttu-id="3a071-126">请注意 "**分类关系图**" 窗口右上角的 "**明暗度变量**" 控件。</span><span class="sxs-lookup"><span data-stu-id="3a071-126">Notice the **Shading Variable** control in the upper right corner of the **Cluster Diagram** window.</span></span>  
  
     <span data-ttu-id="3a071-127">默认情况下，它设置为 "**填充**"。</span><span class="sxs-lookup"><span data-stu-id="3a071-127">By default, it is set to **Population**.</span></span> <span data-ttu-id="3a071-128">这表示颜色较暗的分类具有更高程度的支持。</span><span class="sxs-lookup"><span data-stu-id="3a071-128">What this means is that the darker clusters have greater support.</span></span>  
  
4.  <span data-ttu-id="3a071-129">将鼠标指针停留在任一分类上。</span><span class="sxs-lookup"><span data-stu-id="3a071-129">Pause over any cluster with the cursor.</span></span>  
  
     <span data-ttu-id="3a071-130">将显示工具提示，其中包含该分类的总体。</span><span class="sxs-lookup"><span data-stu-id="3a071-130">A ToolTip is displayed that contains the population of that cluster.</span></span>  
  
5.  <span data-ttu-id="3a071-131">现在，单击 "**明暗度变量**" 下拉列表，然后选择 " **Age** " 变量。</span><span class="sxs-lookup"><span data-stu-id="3a071-131">Now, click the **Shading Variable** dropdown list and choose the **Age** variable.</span></span> <span data-ttu-id="3a071-132">这样做时，"**状态**" 文本框中将出现一个值列表。</span><span class="sxs-lookup"><span data-stu-id="3a071-132">As you do so, a list of values appears in the **State** text box.</span></span>  
  
     <span data-ttu-id="3a071-133">用作此模型的输入的“Age”列包含连续数值，但为了聚类分析，该算法始终将数字离散化。</span><span class="sxs-lookup"><span data-stu-id="3a071-133">The Age column used as input to this model contains continuous numeric values, but for the purpose of clustering, the algorithm always discretizes numbers.</span></span> <span data-ttu-id="3a071-134">可在此处查看该算法创建的箱或组，例如 "极低 (\<=27)" and "Very High (> = 63) "。</span><span class="sxs-lookup"><span data-stu-id="3a071-134">Here you can see the bins, or groups that the algorithm created, such as "Very Low (\<=27)" and "Very High (>=63)".</span></span>  
  
6.  <span data-ttu-id="3a071-135">从 "**状态**" 下拉列表中，选择 "**非常高**"，并查看关系图如何变化。</span><span class="sxs-lookup"><span data-stu-id="3a071-135">From the **State** dropdown lists, select **Very High** and see how the diagram changes.</span></span>  
  
     <span data-ttu-id="3a071-136">通过更改明暗度变量，可以一目了然地看到哪些分类包含此目标年龄组内的更多客户，哪些分类包含此年龄组内的很少客户。</span><span class="sxs-lookup"><span data-stu-id="3a071-136">By changing the shading variable, you can see at a glance which clusters contain more of this targeted age group, and which clusters contain very few customers in this age group.</span></span>  
  
     <span data-ttu-id="3a071-137">![修改分类关系图以便显示年龄](media/dm13-cluster-diagramshadebyage.gif "修改分类关系图以便显示年龄")</span><span class="sxs-lookup"><span data-stu-id="3a071-137">![Modify the cluster diagram to show age](media/dm13-cluster-diagramshadebyage.gif "Modify the cluster diagram to show age")</span></span>  
  
     <span data-ttu-id="3a071-138">明暗度越深，所聚类的目标属性和值分配比例就越高。</span><span class="sxs-lookup"><span data-stu-id="3a071-138">The darker the shading, the larger the proportion of the target attribute and value distribution that cluster.</span></span>  
  
7.  <span data-ttu-id="3a071-139">当**明暗度变量**设置为 Age >65 时，找到阴影最暗的分类。</span><span class="sxs-lookup"><span data-stu-id="3a071-139">Locate the cluster that is shaded darkest when the **Shading Variable** is set to Age >65.</span></span>  
  
     <span data-ttu-id="3a071-140">将鼠标指针悬停在该分类上。</span><span class="sxs-lookup"><span data-stu-id="3a071-140">Hover the mouse over the cluster.</span></span>  
  
     <span data-ttu-id="3a071-141">工具提示中的值此时显示年龄超过 65 的此分类中的客户人数。</span><span class="sxs-lookup"><span data-stu-id="3a071-141">The value displayed in the ToolTip now shows you the population of customers in this cluster who are over 65.</span></span>  
  
8.  <span data-ttu-id="3a071-142">右键单击该群集，然后选择 "**重命名群集**"。</span><span class="sxs-lookup"><span data-stu-id="3a071-142">Right-click the cluster and select **Rename Cluster**.</span></span> <span data-ttu-id="3a071-143">键入一个描述性的新名称，例如 "**超过 65**"。</span><span class="sxs-lookup"><span data-stu-id="3a071-143">Type a new name that is descriptive, such as **Over 65**.</span></span> <span data-ttu-id="3a071-144">新名称随模型保存到服务器，可用于标识其他聚类分析视图中的分类。</span><span class="sxs-lookup"><span data-stu-id="3a071-144">The new name is saved with the model to the server and can be used for identifying the cluster in the other clustering views.</span></span>  
  
 [<span data-ttu-id="3a071-145">返回页首</span><span class="sxs-lookup"><span data-stu-id="3a071-145">Back To Top</span></span>](#BKMK_Tabs)  
  
###  <a name="cluster-profiles"></a><a name="BKMK_ClusterProfiles"></a><span data-ttu-id="3a071-146">群集配置文件</span><span class="sxs-lookup"><span data-stu-id="3a071-146">Cluster Profiles</span></span>  
 <span data-ttu-id="3a071-147">通过 "**分类配置文件**" 选项卡，您可以一目了然地比较所有分类的构成。</span><span class="sxs-lookup"><span data-stu-id="3a071-147">The **Cluster Profiles** tab lets you compare the makeup of all clusters at a glance.</span></span> <span data-ttu-id="3a071-148">要熟悉模型，这里是很好的起点。</span><span class="sxs-lookup"><span data-stu-id="3a071-148">This is a good place to start when you are getting familiar with the model.</span></span> <span data-ttu-id="3a071-149">如果您在探索特定分类并且需要查找相关分类，稍后此视图也非常有用。</span><span class="sxs-lookup"><span data-stu-id="3a071-149">This view is also useful later on, if you have been exploring a particular cluster and decide you need to find related ones.</span></span>  
  
 <span data-ttu-id="3a071-150">**群集配置文件**还可让你更好地了解群集之间的不同之处。</span><span class="sxs-lookup"><span data-stu-id="3a071-150">**Cluster Profiles** also gives you a good overview of how the clusters are different from each other.</span></span> <span data-ttu-id="3a071-151">因此，您可能会发现使用此视图为每个分类提供说明性名称十分方便。</span><span class="sxs-lookup"><span data-stu-id="3a071-151">Therefore, you might find it convenient to use this view to give each cluster a descriptive name.</span></span>  
  
##### <a name="explore-the-cluster-profiles"></a><span data-ttu-id="3a071-152">探索分类剖面图</span><span class="sxs-lookup"><span data-stu-id="3a071-152">Explore the cluster profiles</span></span>  
  
1.  <span data-ttu-id="3a071-153">单击 "**状态**" 列中的 "职业" 单元格，查看职业的所有值的列表。</span><span class="sxs-lookup"><span data-stu-id="3a071-153">Click the cell for Occupations, in the **States** column, to see the list of all values for Occupation.</span></span>  
  
2.  <span data-ttu-id="3a071-154">现在，将鼠标指针移到分类剖面图中的“Occupation”上。</span><span class="sxs-lookup"><span data-stu-id="3a071-154">Now move the cursor over Occupation in the cluster profiles.</span></span>  
  
     <span data-ttu-id="3a071-155">工具提示显示该分类中的职业分布。</span><span class="sxs-lookup"><span data-stu-id="3a071-155">The ToolTip shows the distribution of occupations in that cluster.</span></span>  
  
     <span data-ttu-id="3a071-156">![在工具提示或图例中查看详细值](media/dm13-cluster-profile-age-tooltip.gif "在工具提示或图例中查看详细值")</span><span class="sxs-lookup"><span data-stu-id="3a071-156">![View detailed values in Tooltips or in Legend](media/dm13-cluster-profile-age-tooltip.gif "View detailed values in Tooltips or in Legend")</span></span>  
  
     <span data-ttu-id="3a071-157">请注意，在某些分类中 (例如，在图形) 中，职业的列表不完整，某些职业被替换为**标签。**</span><span class="sxs-lookup"><span data-stu-id="3a071-157">Notice that, in some clusters (such as the one in the graphic), the list of occupations is not complete, and some occupations are replaced with the label, **Other**.</span></span>  
  
     <span data-ttu-id="3a071-158">这是设计使然，因为可能很难判断直方图中许多小条之间的差别。</span><span class="sxs-lookup"><span data-stu-id="3a071-158">This is by design, because it can be hard to tell the difference between many small bars in a histogram.</span></span> <span data-ttu-id="3a071-159">默认情况下，仅保留最高重要性的条形，其余条形组合到一个灰色的**其他**存储桶中。</span><span class="sxs-lookup"><span data-stu-id="3a071-159">By default only the bars of highest importance are retained, and the remaining bars are grouped together into a gray **Other** bucket.</span></span>  
  
     <span data-ttu-id="3a071-160">若要更改在任何直方图中可见的条数，请使用 "选项"**直方图条**。</span><span class="sxs-lookup"><span data-stu-id="3a071-160">To change the number of bars that are visible in any histogram, use the option **Histogram bars**.</span></span>  
  
3.  <span data-ttu-id="3a071-161">请注意，"**年龄**" 列看起来与其他不同。</span><span class="sxs-lookup"><span data-stu-id="3a071-161">Note that the **Age** column looks different from the others.</span></span> <span data-ttu-id="3a071-162">单击图表中用于表示 Age 的菱形。</span><span class="sxs-lookup"><span data-stu-id="3a071-162">Click the diamond in the chart used to represent Age.</span></span>  
  
     <span data-ttu-id="3a071-163">Age 列最初仅包含连续值。</span><span class="sxs-lookup"><span data-stu-id="3a071-163">The column Age originally contained only continuous numbers.</span></span> <span data-ttu-id="3a071-164">聚类分析算法需要离散值，因此，它基于值的分布将 Age 列中的数值分组为有限数目的年龄组。</span><span class="sxs-lookup"><span data-stu-id="3a071-164">The clustering algorithm requires discrete values, so it grouped the numeric values in the Age column into a limited number of age groups, based on the distribution of values.</span></span>  
  
4.  <span data-ttu-id="3a071-165">单击分类剖面图中的一个菱形图表。</span><span class="sxs-lookup"><span data-stu-id="3a071-165">Click one of the diamond charts in a cluster profile.</span></span>  
  
     <span data-ttu-id="3a071-166">只有在源数据使用连续数值时，才会显示这些菱形图表。</span><span class="sxs-lookup"><span data-stu-id="3a071-166">These diamond charts are displayed only when the source data uses continuous numeric values.</span></span> <span data-ttu-id="3a071-167">菱形图表提供了一些有用的说明性统计信息，包括每个分类中该值的平均偏差和标准偏差：</span><span class="sxs-lookup"><span data-stu-id="3a071-167">The diamond charts provide some useful descriptive statistics, including the mean and standard deviation for that value in each cluster:</span></span>  
  
    -   <span data-ttu-id="3a071-168">菱形图表中的线条表示该属性的值范围。</span><span class="sxs-lookup"><span data-stu-id="3a071-168">The line in the diamond chart represents the range of values for the attribute.</span></span> <span data-ttu-id="3a071-169">值还会显示在**配置文件**图表左侧的 "**状态**" 列中。</span><span class="sxs-lookup"><span data-stu-id="3a071-169">The values are also shown in the **States** column at the left of the **Profiles** chart.</span></span>  
  
    -   <span data-ttu-id="3a071-170">菱形的中心位于该节点的平均值处。</span><span class="sxs-lookup"><span data-stu-id="3a071-170">The center of the diamond is positioned at the mean for the node.</span></span>  
  
    -   <span data-ttu-id="3a071-171">菱形的宽度表示该节点处属性的方差。</span><span class="sxs-lookup"><span data-stu-id="3a071-171">The width of the diamond represents the variance of the attribute at that node.</span></span> <span data-ttu-id="3a071-172">因此，较细的菱形表示该节点可以生成更精确的预测。</span><span class="sxs-lookup"><span data-stu-id="3a071-172">Therefore, a thinner diamond indicates that the node can create a more accurate prediction.</span></span>  
  
5.  <span data-ttu-id="3a071-173">若要在关系图中腾出更多空间，请右键单击不需要立即查看的分类，然后选择 "**隐藏列**"。</span><span class="sxs-lookup"><span data-stu-id="3a071-173">To make more room in the graph, right-click a cluster you don't need to view right away, and select **Hide Column**.</span></span> <span data-ttu-id="3a071-174">这并不会将其从模型中删除，只需暂时折叠列。</span><span class="sxs-lookup"><span data-stu-id="3a071-174">This doesn't delete it from the model, just collapses the column temporarily.</span></span>  
  
     <span data-ttu-id="3a071-175">若要查看已隐藏的群集，可以单击并拖动列边缘，或从列表中选择群集名称，**更多群集**。</span><span class="sxs-lookup"><span data-stu-id="3a071-175">To view clusters that you've hidden, you can click and drag the column edge, or select the cluster name from the list, **More clusters**.</span></span>  
  
6.  <span data-ttu-id="3a071-176">向下滚动属性列表，直至找到“Bike Buyer”，然后查找具有最高“Yes”值百分比的分类。</span><span class="sxs-lookup"><span data-stu-id="3a071-176">Scroll down the attribute list till you find Bike Buyer, and then find the cluster that has the highest percentage of Yes values.</span></span>  
  
     <span data-ttu-id="3a071-177">右键单击要重命名的群集的列标题，选择 "**重命名群集**"，然后键入 "**自行车购买**者"。</span><span class="sxs-lookup"><span data-stu-id="3a071-177">Right-click the column heading for the cluster that you want to rename, select **Rename cluster**, and type **Bike Buyers**.</span></span>  
  
     <span data-ttu-id="3a071-178">新的分类名称保留在所有视图中以及服务器上，直到您重新处理该模型。</span><span class="sxs-lookup"><span data-stu-id="3a071-178">The new cluster name is persisted in all views, and on the server, until you reprocess the model.</span></span>  
  
     <span data-ttu-id="3a071-179">![重命名分类以使图表更易于使用](media/dm13-cluster-rename.gif "重命名分类以使图表更易于使用")</span><span class="sxs-lookup"><span data-stu-id="3a071-179">![Rename clusters to make chart easier to use](media/dm13-cluster-rename.gif "Rename clusters to make chart easier to use")</span></span>  
  
 <span data-ttu-id="3a071-180">**提示**</span><span class="sxs-lookup"><span data-stu-id="3a071-180">**Tips**</span></span>  
  
-   <span data-ttu-id="3a071-181">单击列标题，可以将列中的属性按照其对分类的重要性来进行排序。</span><span class="sxs-lookup"><span data-stu-id="3a071-181">Click a column heading to sort the attributes in order of importance for that cluster.</span></span>  
  
-   <span data-ttu-id="3a071-182">在查看器中拖动各列以对它们重新排序。</span><span class="sxs-lookup"><span data-stu-id="3a071-182">Drag columns to reorder them in the viewer.</span></span>  
  
-   <span data-ttu-id="3a071-183">单击 "配置文件" 图表中的任意单元可在 "**挖掘图例**" 中查看详细统计信息。</span><span class="sxs-lookup"><span data-stu-id="3a071-183">Click any cell in the profiles chart to view detailed statistics in the **Mining Legend**.</span></span>  
  
-   <span data-ttu-id="3a071-184">右键单击任一单元格，然后选择 "**钻取模型列**"，将基础数据输出到 Excel 中的新工作表。</span><span class="sxs-lookup"><span data-stu-id="3a071-184">Right-click any cell and select **Drillthrough model columns** to output the underlying data to a new worksheet in Excel.</span></span>  
  
-   <span data-ttu-id="3a071-185">右键单击群集的列标题，然后选择 "**钻取到结构数据**"，以获取有关模型中未包含的群集成员的详细信息。</span><span class="sxs-lookup"><span data-stu-id="3a071-185">Right-click the cluster's column heading and select **Drillthrough to structure data** to get detailed information about the cluster members that wasn't included in the model.</span></span>  
  
     <span data-ttu-id="3a071-186">例如，如果您正在分析客户，则可以将基础数据中的联系信息 (挖掘) 结构中，但不将其包括在模型中，因为它对于分析并不有用。</span><span class="sxs-lookup"><span data-stu-id="3a071-186">For example, if you are profiling customers, you might leave the contact information in the underlying data (the mining structure) but not include it in the model, because it's not useful for analysis.</span></span> <span data-ttu-id="3a071-187">但是，在将客户分配给分类后，您可通过使用钻取来查看详细数据。</span><span class="sxs-lookup"><span data-stu-id="3a071-187">However, after customers have been assigned to clusters, you can view the detailed data by using drillthrough.</span></span>  
  
 [<span data-ttu-id="3a071-188">返回页首</span><span class="sxs-lookup"><span data-stu-id="3a071-188">Back To Top</span></span>](#BKMK_Tabs)  
  
###  <a name="cluster-characteristics"></a><a name="BKMK_ClusterCharacteristics"></a> <span data-ttu-id="3a071-189">分类特征</span><span class="sxs-lookup"><span data-stu-id="3a071-189">Cluster Characteristics</span></span>  
 <span data-ttu-id="3a071-190">通过“分类特征”视图，您实际上可以探索单个分类，以了解哪些属性最能概括此组数据的特征。</span><span class="sxs-lookup"><span data-stu-id="3a071-190">The Cluster Characteristics view lets you really explore a single cluster, to find which attributes most strongly characterize this group of data.</span></span>  
  
##### <a name="explore-the-cluster-characteristics"></a><span data-ttu-id="3a071-191">探索分类特征</span><span class="sxs-lookup"><span data-stu-id="3a071-191">Explore the cluster characteristics</span></span>  
  
1.  <span data-ttu-id="3a071-192">从**群集**列表中选择 "**超过 65** " 群集。</span><span class="sxs-lookup"><span data-stu-id="3a071-192">Select the **Over 65** cluster from the **Cluster** list.</span></span>  
  
     <span data-ttu-id="3a071-193">选择分类后，您可以详细查看构成特定分类的特征。</span><span class="sxs-lookup"><span data-stu-id="3a071-193">After you select a cluster, you can see in detail the characteristics that make up that specific cluster.</span></span>  
  
     <span data-ttu-id="3a071-194">分类包含的属性列在 **“变量”** 列中，所列属性的状态列在 **“值”** 列中。</span><span class="sxs-lookup"><span data-stu-id="3a071-194">The attributes that the cluster contains are listed in the **Variables** columns, and the state of the listed attribute is listed in the **Values** column.</span></span>  
  
     <span data-ttu-id="3a071-195">属性状态按重要性顺序列出，附带在此分类中的概率，以 "**概率**" 列中的彩色条表示。</span><span class="sxs-lookup"><span data-stu-id="3a071-195">Attribute states are listed in order of importance, accompanied by their probability in this cluster, represented as a colored bar in the **Probability** column.</span></span>  
  
     <span data-ttu-id="3a071-196">![聚类分析模型的特性](media/dm13-cluster-characteristics.gif "聚类分析模型的特性")</span><span class="sxs-lookup"><span data-stu-id="3a071-196">![Characteristics of a clustering model](media/dm13-cluster-characteristics.gif "Characteristics of a clustering model")</span></span>  
  
2.  <span data-ttu-id="3a071-197">单击 "**变量**" 列按属性排序。</span><span class="sxs-lookup"><span data-stu-id="3a071-197">Click the **Variables** column to sort by attribute.</span></span>  
  
     <span data-ttu-id="3a071-198">通过更改排序变量，您可以更方便地查看变量值（如收入或汽车拥有情况）是如何在该组中分布的。</span><span class="sxs-lookup"><span data-stu-id="3a071-198">By changing the sort variable, you can more easily see how values for variables such as income or car ownership are distributed in the group.</span></span>  
  
3.  <span data-ttu-id="3a071-199">单击 "**复制到 Excel**"。</span><span class="sxs-lookup"><span data-stu-id="3a071-199">Click **Copy to Excel**.</span></span>  
  
     <span data-ttu-id="3a071-200">一个新工作表将添加到包含所选分类的特征的工作簿中。</span><span class="sxs-lookup"><span data-stu-id="3a071-200">A new worksheet is added to your workbook that contains the characteristics of the selected cluster.</span></span>  
  
4.  <span data-ttu-id="3a071-201">现在，请从列表中选择一个不同的群集，**自行车购买**者。</span><span class="sxs-lookup"><span data-stu-id="3a071-201">Now choose a different cluster from the list, **Bike Buyers**.</span></span>  
  
5.  <span data-ttu-id="3a071-202">单击 "**复制到 Excel**"。</span><span class="sxs-lookup"><span data-stu-id="3a071-202">Click **Copy to Excel**.</span></span>  
  
     <span data-ttu-id="3a071-203">请注意，新的分类特征图表将会添加到其自己的工作表中。</span><span class="sxs-lookup"><span data-stu-id="3a071-203">Note that the new cluster characteristics chart is added on its own worksheet.</span></span> <span data-ttu-id="3a071-204">您可以将它移动到与其他配置文件相同的工作表中，以便更轻松地比较它们，您将在下一步中执行此操作。</span><span class="sxs-lookup"><span data-stu-id="3a071-204">You can move it onto the same worksheet as the other profile to make it easier to compare them, which you'll do in the next step.</span></span>  
  
 <span data-ttu-id="3a071-205">**提示**</span><span class="sxs-lookup"><span data-stu-id="3a071-205">**Tips**</span></span>  
  
-   <span data-ttu-id="3a071-206">请注意，超过65个群集中的客户的主要特性是他们不购买您的产品！</span><span class="sxs-lookup"><span data-stu-id="3a071-206">Note that the primary characteristic of the customer in the Over 65 cluster is that they don't buy your product!</span></span> <span data-ttu-id="3a071-207">如果需要了解原因，可以浏览各分类并比较各组，也可以使用适合探索原因与结果的算法来创建一个相关模型，如决策树模型或 Naïve Bayes 模型。</span><span class="sxs-lookup"><span data-stu-id="3a071-207">If you want to know why this is so, you can browse clusters and compare groups, or you might create a related model using an algorithm that is good at exploring causes and outcomes, such as a decision tree model or a Naïve Bayes model.</span></span>  
  
-   <span data-ttu-id="3a071-208">如果需要获得此分类（或所有分类）的属性与概率的完整列表，可以创建一个查询。</span><span class="sxs-lookup"><span data-stu-id="3a071-208">If you want to get a complete list of attributes and probabilities for this cluster (or all clusters) you can create a query.</span></span> <span data-ttu-id="3a071-209">有关聚类分析模型的查询的示例，请参阅[聚类分析模型查询示例](data-mining/clustering-model-query-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="3a071-209">For examples of queries on clustering models, see [Clustering Model Query Examples](data-mining/clustering-model-query-examples.md).</span></span>  
  
 [<span data-ttu-id="3a071-210">返回页首</span><span class="sxs-lookup"><span data-stu-id="3a071-210">Back To Top</span></span>](#BKMK_Tabs)  
  
###  <a name="cluster-discrimination"></a><a name="BKMK_ClusterDiscrimination"></a><span data-ttu-id="3a071-211">分类对比</span><span class="sxs-lookup"><span data-stu-id="3a071-211">Cluster Discrimination</span></span>  
 <span data-ttu-id="3a071-212">您可以使用 "**分类对比**" 选项卡来比较两个分类之间的属性，或在群集与数据集中的所有其他情况之间进行比较。</span><span class="sxs-lookup"><span data-stu-id="3a071-212">You use the **Cluster Discrimination** tab to compare attributes between two clusters, or between a cluster and all the other cases in the data set.</span></span>  
  
 <span data-ttu-id="3a071-213">为了突出显示此查看器的功能，我们会将其与基于 "**分类特征**" 视图创建的 Excel 中的并排表进行比较。</span><span class="sxs-lookup"><span data-stu-id="3a071-213">To highlight the features of this viewer, we'll compare it to the side-by-side tables in Excel that you created based on the **Cluster Characteristics** view.</span></span>  
  
##### <a name="explore-cluster-discrimination"></a><span data-ttu-id="3a071-214">探索分类对比</span><span class="sxs-lookup"><span data-stu-id="3a071-214">Explore cluster discrimination</span></span>  
  
1.  <span data-ttu-id="3a071-215">使用 **“分类 1”** 和 **“分类 2”** 列表选择要比较的分类。</span><span class="sxs-lookup"><span data-stu-id="3a071-215">Use the **Cluster 1** and **Cluster 2** lists to select the clusters to compare.</span></span>  
  
    -   <span data-ttu-id="3a071-216">对于“分类 1”请选择“Over 65”。</span><span class="sxs-lookup"><span data-stu-id="3a071-216">For Cluster 1, select Over 65.</span></span>  
  
    -   <span data-ttu-id="3a071-217">对于“分类 2”，请选择“Bike Buyers”。</span><span class="sxs-lookup"><span data-stu-id="3a071-217">For Cluster 2, select Bike Buyers.</span></span>  
  
     <span data-ttu-id="3a071-218">比较结果如下图所示。</span><span class="sxs-lookup"><span data-stu-id="3a071-218">The comparison should look similar to the following graphic.</span></span>  
  
     <span data-ttu-id="3a071-219">![比较模型中的分类](media/dm13-cluster-compareclusters.gif "比较模型中的分类")</span><span class="sxs-lookup"><span data-stu-id="3a071-219">![comparing clusters in a model](media/dm13-cluster-compareclusters.gif "comparing clusters in a model")</span></span>  
  
     <span data-ttu-id="3a071-220">请注意，在这两个方面，**分类对比**查看器将复杂查询发送到数据挖掘服务器，以提取在区分这两个组时最重要的属性，从而更容易比较两组客户。</span><span class="sxs-lookup"><span data-stu-id="3a071-220">Note that, under the covers, the **Cluster Discrimination** viewer sends complex queries to the data mining server, to extract the attributes that are most important in distinguishing between the two groups, making it easier to compare two sets of customers.</span></span>  
  
2.  <span data-ttu-id="3a071-221">单击 "**优先 ...** " 列之一。</span><span class="sxs-lookup"><span data-stu-id="3a071-221">Click either of the **Favors...** columns.</span></span>  
  
     <span data-ttu-id="3a071-222">属性和值表右侧的条显示了哪些功能或值最适合作为所选分类的特征。</span><span class="sxs-lookup"><span data-stu-id="3a071-222">The bar to the right of the attribute and value list shows which features or values are most important as a characteristic of the selected cluster.</span></span>  
  
3.  <span data-ttu-id="3a071-223">现在，在 Excel 中对各列表进行比较。</span><span class="sxs-lookup"><span data-stu-id="3a071-223">Now compare the lists in Excel.</span></span>  
  
     <span data-ttu-id="3a071-224">![关联模型的依赖关系网络图形](media/dm13-comparing-profiles-in-excel.gif "关联模型的依赖关系网络图形")</span><span class="sxs-lookup"><span data-stu-id="3a071-224">![Dependency network graph for an association model](media/dm13-comparing-profiles-in-excel.gif "Dependency network graph for an association model")</span></span>  
  
     <span data-ttu-id="3a071-225">因为用于在查看器中生成图像的基础统计信息以表的形式保存到 Excel，所以，您可以筛选、排序和查看实际概率值。</span><span class="sxs-lookup"><span data-stu-id="3a071-225">Because the underlying statistics that were used to build the image in the viewer are saved to Excel as tables, you can filter and sort, and view the actual probability values.</span></span>  
  
     <span data-ttu-id="3a071-226">除使用 Excel 外，建议您尝试将分类查看器用于 Visio，这样不仅可以查看数据点，还可以广泛修改和增强图形。</span><span class="sxs-lookup"><span data-stu-id="3a071-226">In addition to using Excel, we recommend that you try the cluster viewer for Visio, which also allows you to not just view data points but also extensively modify and enhance the graph.</span></span> <span data-ttu-id="3a071-227">有关详细信息，请参阅[分类关系图演练 &#40;数据挖掘外接程序&#41;](cluster-diagram-walkthrough-data-mining-add-ins.md)。</span><span class="sxs-lookup"><span data-stu-id="3a071-227">For more information, see [Cluster Diagram Walkthrough &#40;Data Mining Add-ins&#41;](cluster-diagram-walkthrough-data-mining-add-ins.md).</span></span>  
  
 <span data-ttu-id="3a071-228">**提示**</span><span class="sxs-lookup"><span data-stu-id="3a071-228">**Tips**</span></span>  
  
 <span data-ttu-id="3a071-229">深入了解客户组后，请尝试使用 "[假设方案 &#40;表分析工具" excel&#41;](what-if-scenario-table-analysis-tools-for-excel.md)或 "[目标查找" 方案 &#40;excel&#41;工具的表分析工具](goal-seek-scenario-table-analysis-tools-for-excel.md)，以浏览模型中可能会更改以影响结果的因素。</span><span class="sxs-lookup"><span data-stu-id="3a071-229">After getting some insights into groups of customers, try using the [What-If Scenario &#40;Table Analysis Tools for Excel&#41;](what-if-scenario-table-analysis-tools-for-excel.md) or [Goal Seek Scenario &#40;Table Analysis Tools for Excel&#41;](goal-seek-scenario-table-analysis-tools-for-excel.md) tools, to explore factors in the model that might be changed to affect the outcome.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a071-230">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3a071-230">See Also</span></span>  
 <span data-ttu-id="3a071-231">[在 Excel 中浏览模型 &#40;SQL Server 数据挖掘外接程序&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md) </span><span class="sxs-lookup"><span data-stu-id="3a071-231">[Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md) </span></span>  
 [<span data-ttu-id="3a071-232">群集向导 &#40;Excel 数据挖掘外接程序&#41;</span><span class="sxs-lookup"><span data-stu-id="3a071-232">Cluster Wizard &#40;Data Mining Add-ins for Excel&#41;</span></span>](cluster-wizard-data-mining-add-ins-for-excel.md)  
  
  
