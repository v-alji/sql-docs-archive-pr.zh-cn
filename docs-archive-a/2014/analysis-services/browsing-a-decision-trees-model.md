---
title: 浏览决策树模型 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, browsing
- mining models, viewing
- tree viewer
- mining model, decision tree
- decision tree [data mining]
- dependency network
ms.assetid: 6b3dd1ae-caff-41c3-817b-802dc020ff88
author: minewiskan
ms.author: owend
ms.openlocfilehash: 809d2e494cfa7a6c4078acf95c2c70a0e68c188d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579310"
---
# <a name="browsing-a-decision-trees-model"></a><span data-ttu-id="45750-102">浏览决策树模型</span><span class="sxs-lookup"><span data-stu-id="45750-102">Browsing a Decision Trees Model</span></span>
  <span data-ttu-id="45750-103">使用 "**浏览**" 打开分类模型时，该模型将显示在交互式决策树查看器中，类似于 [!INCLUDE[msCoName](../includes/msconame-md.md)] 中的决策树查看器 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="45750-103">When you open a classification model using **Browse**, the model is displayed in an interactive decision tree viewer, similar to the [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees viewer in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="45750-104">该查看器将分类结果显示为一个图形，图形设计可以突出将一组数据与其他数据区分开来的条件。</span><span class="sxs-lookup"><span data-stu-id="45750-104">The viewer displays the results of classification as a graph that is designed to highlight the criteria that differentiate one group of data from another.</span></span> <span data-ttu-id="45750-105">您还可以深化到树的各个子集并检索基础数据。</span><span class="sxs-lookup"><span data-stu-id="45750-105">You can also drill down into individual subsets of the tree and retrieve the underlying data.</span></span>  
  
##  <a name="explore-the-model"></a><a name="bkmk_Top"></a><span data-ttu-id="45750-106">浏览模型</span><span class="sxs-lookup"><span data-stu-id="45750-106">Explore the Model</span></span>  
 <span data-ttu-id="45750-107">基于决策树算法的模型有很多有趣的信息值得探索。</span><span class="sxs-lookup"><span data-stu-id="45750-107">Models based on the Decision Trees algorithm have lots of interesting information to explore.</span></span> <span data-ttu-id="45750-108">"**浏览**" 窗口包括以下选项卡和窗格，可帮助您了解使用图形的模式并预测结果：</span><span class="sxs-lookup"><span data-stu-id="45750-108">The **Browse** window includes the following tabs and panes to help you learn the patterns and predict outcomes using the graph:</span></span>  
  
-   [<span data-ttu-id="45750-109">决策树</span><span class="sxs-lookup"><span data-stu-id="45750-109">Decision Tree</span></span>](#BKMK_DecisionTree)  
  
-   [<span data-ttu-id="45750-110">依赖关系网络</span><span class="sxs-lookup"><span data-stu-id="45750-110">Dependency Network</span></span>](#BKMK_DNetwork)  
  
 <span data-ttu-id="45750-111">要尝试使用决策树模型，可以使用示例数据工作簿中“定型数据”（或“源数据”）选项卡上的示例数据，并使用“Bike Buyer”作为可预测属性生成决策树模型。</span><span class="sxs-lookup"><span data-stu-id="45750-111">To experiment with a decision trees model, you can use the sample data on the Training Data (or Source Data) tab of the sample data workbook, and build a decision tree model using Bike Buyer as the predictable attribute.</span></span>  
  
###  <a name="decision-tree"></a><a name="BKMK_DecisionTree"></a><span data-ttu-id="45750-112">决策树</span><span class="sxs-lookup"><span data-stu-id="45750-112">Decision Tree</span></span>  
 <span data-ttu-id="45750-113">此视图旨在帮助您了解和探索导致某一结果的因素。</span><span class="sxs-lookup"><span data-stu-id="45750-113">This view is intended to help you understand and explore the factors that lead to an outcome.</span></span>  
  
 <span data-ttu-id="45750-114">决策树图形可像下面这样从左到右读取：</span><span class="sxs-lookup"><span data-stu-id="45750-114">The decision tree graph can be read from left to right as follows:</span></span>  
  
-   <span data-ttu-id="45750-115">矩形（称为*节点*）包含数据的子集。</span><span class="sxs-lookup"><span data-stu-id="45750-115">The rectangles, which are referred to as *nodes*, contain subsets of the data.</span></span> <span data-ttu-id="45750-116">节点标签指示相应子集的定义特征。</span><span class="sxs-lookup"><span data-stu-id="45750-116">The label on the node tells you the defining characteristics of that subset.</span></span>  
  
-   <span data-ttu-id="45750-117">最左侧的节点（标记为 "**全部**"）表示完整的数据集。</span><span class="sxs-lookup"><span data-stu-id="45750-117">The leftmost node, labeled **All**, represents the complete data set.</span></span> <span data-ttu-id="45750-118">所有后续节点表示数据子集。</span><span class="sxs-lookup"><span data-stu-id="45750-118">All subsequent nodes represent subsets of the data.</span></span>  
  
-   <span data-ttu-id="45750-119">决策树包含很多*分割*，或者数据与其分离为多个基于属性的集的位置。</span><span class="sxs-lookup"><span data-stu-id="45750-119">A decision tree contains many *splits*, or places where the data diverges into multiple sets based on attributes.</span></span>  
  
     <span data-ttu-id="45750-120">例如，示例模型中的第一个拆分将数据集按年龄分为三组。</span><span class="sxs-lookup"><span data-stu-id="45750-120">For example, the first split in the sample model divides the dataset into three groups by age.</span></span>  
  
-   <span data-ttu-id="45750-121">紧随 "**全部**" 节点之后的拆分最重要，因为它显示了分割此数据集的主要条件。</span><span class="sxs-lookup"><span data-stu-id="45750-121">The split immediately after the **All** node is most important because it shows the primary condition that divides this dataset.</span></span>  
  
     <span data-ttu-id="45750-122">其他拆分出现在右侧。</span><span class="sxs-lookup"><span data-stu-id="45750-122">Additional splits occur to the right.</span></span> <span data-ttu-id="45750-123">因此，通过分析树段可以了解哪些属性对购买行为影响最大。</span><span class="sxs-lookup"><span data-stu-id="45750-123">Thus, by analyzing different segments of the tree, you can learn which attributes had the most influence on purchasing behavior.</span></span>  
  
 <span data-ttu-id="45750-124">![关联模型的依赖关系网络图形](media/dm13-dec-tree-split-definition.gif "关联模型的依赖关系网络图形")</span><span class="sxs-lookup"><span data-stu-id="45750-124">![Dependency network graph for an association model](media/dm13-dec-tree-split-definition.gif "Dependency network graph for an association model")</span></span>  
  
 <span data-ttu-id="45750-125">您可以使用这些信息针对稍加鼓励就会购买的客户制定营销战略。</span><span class="sxs-lookup"><span data-stu-id="45750-125">Using this information, you might focus a marketing campaign on customers that might simply need encouragement to make a purchase.</span></span>  
  
##### <a name="explore-the-decision-tree"></a><span data-ttu-id="45750-126">浏览决策树</span><span class="sxs-lookup"><span data-stu-id="45750-126">Explore the decision tree</span></span>  
  
1.  <span data-ttu-id="45750-127">单击 "**全部**" 节点，查看 "**挖掘图例**"。</span><span class="sxs-lookup"><span data-stu-id="45750-127">Click the **All** node, and look at the **Mining Legend**.</span></span>  
  
     <span data-ttu-id="45750-128">它显示了定型数据集中事例的准确计数和结果细分。</span><span class="sxs-lookup"><span data-stu-id="45750-128">It displays the exact count of cases in the training data set, as well as a breakdown of the outcomes.</span></span>  
  
     <span data-ttu-id="45750-129">将鼠标悬停在节点上时出现的工具提示中也会有相同的信息。</span><span class="sxs-lookup"><span data-stu-id="45750-129">You can view the same information in a tooltip if you pause the mouse over a node.</span></span>  
  
2.  <span data-ttu-id="45750-130">单击每个节点旁的加号和减号可以展开或折叠决策树。</span><span class="sxs-lookup"><span data-stu-id="45750-130">Click the plus and minus signs next to each node to expand or collapse the tree.</span></span>  
  
     <span data-ttu-id="45750-131">还可以使用 "**显示级别**" 滑块展开或收缩树。</span><span class="sxs-lookup"><span data-stu-id="45750-131">You can also use the **Show Level** slider to expand or shrink the tree.</span></span>  
  
3.  <span data-ttu-id="45750-132">请注意，有些节点颜色更深一些。</span><span class="sxs-lookup"><span data-stu-id="45750-132">Notice that some nodes are darker than others?</span></span>  
  
     <span data-ttu-id="45750-133">默认情况下，**填充**用作明暗度变量，这意味着颜色强度显示最支持的节点。</span><span class="sxs-lookup"><span data-stu-id="45750-133">By default, **Population** is used as the shading variable, which means that the intensity of the color shows you which nodes have the most support.</span></span>  
  
     <span data-ttu-id="45750-134">所以最左侧的节点颜色最深，因为它包含整个数据集。</span><span class="sxs-lookup"><span data-stu-id="45750-134">Therefore the leftmost node is darkest, because it contains the entire dataset.</span></span>  
  
4.  <span data-ttu-id="45750-135">将 "**背景**" 的 "值"**更改为** **"是"**。</span><span class="sxs-lookup"><span data-stu-id="45750-135">Change the value for **Background** from **All Cases** to **Yes**.</span></span>  
  
     <span data-ttu-id="45750-136">![更改决策树图形以突出显示购买者](media/dm13-dectreeshadedbuyer.gif "更改决策树图形以突出显示购买者")</span><span class="sxs-lookup"><span data-stu-id="45750-136">![changing decision tree graph to highlight buyers](media/dm13-dectreeshadedbuyer.gif "changing decision tree graph to highlight buyers")</span></span>  
  
5.  <span data-ttu-id="45750-137">现在，颜色强度告诉您每个节点有多少客户购买了自行车，这正是您感兴趣的行为。</span><span class="sxs-lookup"><span data-stu-id="45750-137">Now the intensity of the color tells you how many customers in each node purchased a bike, which is the behavior you are interested in.</span></span>  
  
     <span data-ttu-id="45750-138">请注意每个节点中的彩色条。</span><span class="sxs-lookup"><span data-stu-id="45750-138">Notice the colored bars within each node.</span></span> <span data-ttu-id="45750-139">这是显示此数据子集中结果分布情况的直方图。</span><span class="sxs-lookup"><span data-stu-id="45750-139">This is a histogram that shows the distribution of outcomes within this subset of data.</span></span> <span data-ttu-id="45750-140">例如，在示例自行车买家决策树中，彩色条显示购买了自行车 (是值的客户的比例) 与未 (任何值) 的客户。</span><span class="sxs-lookup"><span data-stu-id="45750-140">For example, in the sample Bike Buyer decision tree, the colored bar shows the proportion of customers who bought bikes (Yes values) vs. those who did not (No values).</span></span> <span data-ttu-id="45750-141">若要获取准确值，可以单击该节点并查看 "**挖掘图例**"。</span><span class="sxs-lookup"><span data-stu-id="45750-141">To get the exact values, you can click the node and view the **Mining Legend**.</span></span>  
  
6.  <span data-ttu-id="45750-142">分析图形，可以看到每个数据子集如何进一步分解为更小的组，以及哪些属性对预测结果最有用。</span><span class="sxs-lookup"><span data-stu-id="45750-142">By following the graph, you can see how each subset of data is further decomposed into smaller groups, and which attributes are most useful in predicting an outcome.</span></span>  
  
     <span data-ttu-id="45750-143">只通过阴影强度您就可以锁定一些感兴趣的组，获取更详细的数据进行比较。</span><span class="sxs-lookup"><span data-stu-id="45750-143">Just by looking at the intensity of the shading, you can focus on a couple groups of interest, and get more detailed data on them for comparison.</span></span> <span data-ttu-id="45750-144">例如，这些组购买自行车的概率相当高：</span><span class="sxs-lookup"><span data-stu-id="45750-144">For example, these groups have a fairly high probability of buying bikes:</span></span>  
  
    -   <span data-ttu-id="45750-145">Age >= 32， \< 53 and Yearly Income > = 26000，子代 = 0</span><span class="sxs-lookup"><span data-stu-id="45750-145">Age >= 32 and \< 53 and Yearly Income >= 26000 and Children = 0</span></span>  
  
         <span data-ttu-id="45750-146">事例总大小：1150</span><span class="sxs-lookup"><span data-stu-id="45750-146">Total cases: 1150</span></span>  
  
         <span data-ttu-id="45750-147">自行车购买者概率：18%</span><span class="sxs-lookup"><span data-stu-id="45750-147">Bike buyer probability: 18%</span></span>  
  
    -   <span data-ttu-id="45750-148">Age >= 32， \< 53 and Yearly Income > = 26000，子元素不 = 0，婚姻状态 = ' 单个 '</span><span class="sxs-lookup"><span data-stu-id="45750-148">Age >= 32 and \< 53 and Yearly Income >= 26000 and Children not = 0 and Marital Status = 'Single'</span></span>  
  
         <span data-ttu-id="45750-149">Total cases: 402</span><span class="sxs-lookup"><span data-stu-id="45750-149">Total cases: 402</span></span>  
  
         <span data-ttu-id="45750-150">Bike buyer probability: 16%</span><span class="sxs-lookup"><span data-stu-id="45750-150">Bike buyer probability: 16%</span></span>  
  
7.  <span data-ttu-id="45750-151">将 "**背景**" 的值从 **"是"** 更改为 "**否**"，并查看图形如何变化。</span><span class="sxs-lookup"><span data-stu-id="45750-151">Change the value for **Background** from **Yes** to **No** and see how the graph changes.</span></span>  
  
     <span data-ttu-id="45750-152">![关联模型的依赖关系网络图形](media/dm13-dec-tree-background-no.gif "关联模型的依赖关系网络图形")</span><span class="sxs-lookup"><span data-stu-id="45750-152">![Dependency network graph for an association model](media/dm13-dec-tree-background-no.gif "Dependency network graph for an association model")</span></span>  
  
 <span data-ttu-id="45750-153">**提示**</span><span class="sxs-lookup"><span data-stu-id="45750-153">**Tips**</span></span>  
  
-   <span data-ttu-id="45750-154">如果您的数据可以分为多个序列，会为要建模的每组数据生成一个不同的模型。</span><span class="sxs-lookup"><span data-stu-id="45750-154">If your data can be divided into multiple series, a different model is built for each set of data that you want to model.</span></span>  
  
-   <span data-ttu-id="45750-155">在示例数据模型中，只有一个可预测的结果-自行车购买者-但假设您有关于客户是否购买了服务计划并想要预测的信息。</span><span class="sxs-lookup"><span data-stu-id="45750-155">In the sample data model, there is only one predictable outcome - Bike Buyer - but suppose you had information about whether the customer purchased a service plan and wanted to predict that as well.</span></span> <span data-ttu-id="45750-156">在这种情况下，应将这些数据放在单独的列中，并在模型中包含两个可预测属性。</span><span class="sxs-lookup"><span data-stu-id="45750-156">In that case you would have that data in a separate column, and include two predictable attributes in the model.</span></span>  
  
     <span data-ttu-id="45750-157">单击 "决策树" 窗格左上角的 "**直方图**" 选项，以更改可在树的直方图中显示的最大状态数。</span><span class="sxs-lookup"><span data-stu-id="45750-157">Click the **Histogram** option, in the upper left corner of the Decision Tree pane, to change the maximum number of states that can appear in the histograms in the tree.</span></span> <span data-ttu-id="45750-158">如果可预测属性有很多状态，这一功能将非常有用。</span><span class="sxs-lookup"><span data-stu-id="45750-158">This is useful if the predictable attribute has many states.</span></span> <span data-ttu-id="45750-159">各种状态将按使用频率高低自左到右显示在直方图中。</span><span class="sxs-lookup"><span data-stu-id="45750-159">The states appear in a histogram in order of popularity from left to right.</span></span>  
  
-   <span data-ttu-id="45750-160">您还可以使用 "**决策树**" 选项卡上的选项，通过放大或缩小来影响树的显示方式，或调整关系图的大小以适合窗口大小。</span><span class="sxs-lookup"><span data-stu-id="45750-160">You can also use the options on the **Decision Tree** tab to affect how the tree is displayed, by zooming in or out, or sizing the graph to fit the window.</span></span>  
  
-   <span data-ttu-id="45750-161">使用 **“默认扩展”** 可以设置模型中所有树的默认显示级别数。</span><span class="sxs-lookup"><span data-stu-id="45750-161">Use **Default Expansion** to set the default number of levels that are displayed for all trees in the model.</span></span>  
  
-   <span data-ttu-id="45750-162">选择 "**显示长名称**" 可显示属性的完整名称，包括数据源。</span><span class="sxs-lookup"><span data-stu-id="45750-162">Select **Show long name** to display the full name of the attribute, including the data source.</span></span> <span data-ttu-id="45750-163">短名称和长名称是相同的，除非各自的属性是从不同的数据源获取的。</span><span class="sxs-lookup"><span data-stu-id="45750-163">Short names and long names are the same unless your cases are obtained from a different data source than the attributes for each case.</span></span>  
  
 [<span data-ttu-id="45750-164">返回页首</span><span class="sxs-lookup"><span data-stu-id="45750-164">Back To Top</span></span>](#bkmk_Top)  
  
###  <a name="dependency-network"></a><a name="BKMK_DNetwork"></a><span data-ttu-id="45750-165">依赖关系网络</span><span class="sxs-lookup"><span data-stu-id="45750-165">Dependency Network</span></span>  
 <span data-ttu-id="45750-166">"**依赖关系网络**" 视图显示模型中的输入属性和可预测属性之间的连接。</span><span class="sxs-lookup"><span data-stu-id="45750-166">The **Dependency Network** view displays the connections between the input attributes and the predictable attributes in the model.</span></span>  
  
1.  <span data-ttu-id="45750-167">单击并拖动查看器左侧的滑块</span><span class="sxs-lookup"><span data-stu-id="45750-167">Click and drag the slider at the left of the viewer</span></span>  
  
     <span data-ttu-id="45750-168">顶部位置显示了所有连接。</span><span class="sxs-lookup"><span data-stu-id="45750-168">At the top position, all connections are shown.</span></span> <span data-ttu-id="45750-169">向下拖动滑块时，查看器中仅显示最强链接。</span><span class="sxs-lookup"><span data-stu-id="45750-169">When you drag the slider down, only the strongest links are shown in the viewer.</span></span>  
  
2.  <span data-ttu-id="45750-170">现在单击“Bike Buyer”节点。</span><span class="sxs-lookup"><span data-stu-id="45750-170">Now click the Bike Buyer node.</span></span>  
  
     <span data-ttu-id="45750-171">![决策树的依赖关系网络视图](media/dm13-dectree-depnet.gif "决策树的依赖关系网络视图")</span><span class="sxs-lookup"><span data-stu-id="45750-171">![Dependency network view for decision trees](media/dm13-dectree-depnet.gif "Dependency network view for decision trees")</span></span>  
  
     <span data-ttu-id="45750-172">选择一个节点后，查看器将突出显示该节点特定的依赖项。</span><span class="sxs-lookup"><span data-stu-id="45750-172">When you select a node, the viewer highlights the dependencies that are specific to the node.</span></span> <span data-ttu-id="45750-173">在这种情况下，查看器突出显示有助于预测结果的每个节点。</span><span class="sxs-lookup"><span data-stu-id="45750-173">In this case, the viewer highlights each node that helps predict the outcome.</span></span>  
  
3.  <span data-ttu-id="45750-174">如果查看器包含多个节点，则可以通过使用 "**查找节点**" 按钮来搜索特定节点。</span><span class="sxs-lookup"><span data-stu-id="45750-174">If the viewer contains many nodes, you can search for specific nodes by using the **Find Node** button.</span></span> <span data-ttu-id="45750-175">单击 **“查找节点”** 将打开 **“查找节点”** 对话框，可以在该对话框中使用筛选器来搜索和选择特定的节点。</span><span class="sxs-lookup"><span data-stu-id="45750-175">Clicking **Find Node** opens the **Find Node** dialog box, in which you can use a filter to search for and select specific nodes.</span></span>  
  
4.  <span data-ttu-id="45750-176">查看器底部的图例说明了图表中不同颜色代码所代表的依赖关系类型。</span><span class="sxs-lookup"><span data-stu-id="45750-176">The legend at the bottom of the viewer links color codes to the type of dependency in the graph.</span></span> <span data-ttu-id="45750-177">例如，如果选择一个可预测节点，该节点将呈青绿色，而预测所选节点的节点呈橙色。</span><span class="sxs-lookup"><span data-stu-id="45750-177">For example, when you select a predictable node, the predictable node is shaded turquoise, and the nodes that predict the selected node are shaded orange.</span></span>  
  
 [<span data-ttu-id="45750-178">返回页首</span><span class="sxs-lookup"><span data-stu-id="45750-178">Back To Top</span></span>](#bkmk_Top)  
  
### <a name="drill-through-to-underlying-data"></a><span data-ttu-id="45750-179">钻取到基础数据</span><span class="sxs-lookup"><span data-stu-id="45750-179">Drill through to Underlying Data</span></span>  
 <span data-ttu-id="45750-180">几种类型的模型支持从模型*钻取*到基础事例数据的功能。</span><span class="sxs-lookup"><span data-stu-id="45750-180">Several types of models support the ability to *drill through* from the model to the underlying case data.</span></span> <span data-ttu-id="45750-181">如果您要联系某一特定段中的客户或提取数据执行进一步分析，这会非常有用。</span><span class="sxs-lookup"><span data-stu-id="45750-181">This can be very useful if you want to contact customers in a particular segment or pull out the data to perform further analysis.</span></span>  
  
##### <a name="get-case-data"></a><span data-ttu-id="45750-182">获取事例数据</span><span class="sxs-lookup"><span data-stu-id="45750-182">Get case data</span></span>  
  
1.  <span data-ttu-id="45750-183">在树中右键单击包含所需数据的节点，然后选择下面选项中的一个：</span><span class="sxs-lookup"><span data-stu-id="45750-183">Right-click the node in the tree that contains the desired data and select one of these options:</span></span>  
  
    -   <span data-ttu-id="45750-184">**钻取模型**。</span><span class="sxs-lookup"><span data-stu-id="45750-184">**Drill Through Model**.</span></span> <span data-ttu-id="45750-185">此选项获取属于所选节点的事例并将它们保存到一个 Excel 表中。</span><span class="sxs-lookup"><span data-stu-id="45750-185">This option gets the cases that belong to the selected node, and saves them to a table in Excel.</span></span> <span data-ttu-id="45750-186">您获取的只是生成模型时实际使用的数据列。</span><span class="sxs-lookup"><span data-stu-id="45750-186">You get back only the columns of data that were actually used in building the model.</span></span>  
  
    -   <span data-ttu-id="45750-187">**钻取结构列**。</span><span class="sxs-lookup"><span data-stu-id="45750-187">**Drill Through Structure Columns**.</span></span> <span data-ttu-id="45750-188">此选项获取属于所选节点的事例并将它们保存到一个 Excel 表中。</span><span class="sxs-lookup"><span data-stu-id="45750-188">This option gets the cases that belong to the selected node, and saves them to a table in Excel.</span></span> <span data-ttu-id="45750-189">您可以获取在生成基础数据时提供的所有信息，甚至是在模型中未使用的列。</span><span class="sxs-lookup"><span data-stu-id="45750-189">You get all information that was available in the underlying data when you built it, even of a column wasn't used in the model.</span></span> <span data-ttu-id="45750-190">例如，您可能排除了客户地址和邮政编码，因为这些字段对分析没用，但将它们留在了结构中。</span><span class="sxs-lookup"><span data-stu-id="45750-190">For example, you might have excluded the customer address and zip code because those fields are not useful with analysis, but left them in the structure.</span></span>  
  
     <span data-ttu-id="45750-191">返回 Excel 查看数据。</span><span class="sxs-lookup"><span data-stu-id="45750-191">Return to Excel to view your data.</span></span> <span data-ttu-id="45750-192">“浏览”查看器运行一个查询，将数据保存到一个表的新工作表中，并标记结果。</span><span class="sxs-lookup"><span data-stu-id="45750-192">The Browse viewer runs a query, saves the data to a table in a new worksheet, and labels the results.</span></span>  
  
     <span data-ttu-id="45750-193">![钻取操作的结果保存到 Excel](media/dm13-dectree-drillthroughresults.gif "钻取操作的结果保存到 Excel")</span><span class="sxs-lookup"><span data-stu-id="45750-193">![results of drillthrough are saved to Excel](media/dm13-dectree-drillthroughresults.gif "results of drillthrough are saved to Excel")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45750-194">另请参阅</span><span class="sxs-lookup"><span data-stu-id="45750-194">See Also</span></span>  
 [<span data-ttu-id="45750-195">在 Excel 中浏览模型 &#40;SQL Server 数据挖掘外接程序&#41;</span><span class="sxs-lookup"><span data-stu-id="45750-195">Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
