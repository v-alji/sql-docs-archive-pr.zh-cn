---
title: " (中级数据挖掘教程) 浏览市场篮模型 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: da1c9cb7-6c32-4b9b-96ec-ecea772aeb77
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d6246aa9330042f0e8033b6f2633a3ed24331ba7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691393"
---
# <a name="exploring-the-market-basket-models-intermediate-data-mining-tutorial"></a><span data-ttu-id="c1a6f-102">浏览市场篮模型（数据挖掘中级教程）</span><span class="sxs-lookup"><span data-stu-id="c1a6f-102">Exploring the Market Basket Models (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="c1a6f-103">现在您已经生成了 `Association` 模型，可以使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] 数据挖掘设计器的 "**挖掘模型查看器**" 选项卡中的 "关联查看器" 来浏览该模型。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-103">Now that you have built the `Association` model, you can explore it by using the [!INCLUDE[msCoName](../includes/msconame-md.md)] Association Viewer in the **Mining Model Viewer** tab of Data Mining Designer.</span></span> <span data-ttu-id="c1a6f-104">本教程指导您使用查看器来浏览各项之间的关系。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-104">This tutorial walks you through using the viewer to explore relationships between items.</span></span> <span data-ttu-id="c1a6f-105">查看器可以帮助您快速查看哪些产品通常会一起出现，并且大致了解出现的模式。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-105">The viewer helps you see at a glance which products tend to appear together, and get a general idea of the emerging patterns.</span></span>  
  
 <span data-ttu-id="c1a6f-106">[!INCLUDE[msCoName](../includes/msconame-md.md)]关联查看器包含三个选项卡：**规则**、**项集**和**依赖关系网络**。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-106">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Association Viewer contains three tabs: **Rules**, **Itemsets**, and **Dependency Network**.</span></span> <span data-ttu-id="c1a6f-107">由于每个选项卡显示的数据视图略有差异，因此在浏览某个模型时，您通常会在不同窗格之间多次来回切换，以便深入了解数据。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-107">Because each tab reveals a slightly different view of the data, when you are exploring a model, you will typically switch back and forth between the different panes several times as you pursue insights.</span></span>  
  
-   [<span data-ttu-id="c1a6f-108">依赖关系网络选项卡</span><span class="sxs-lookup"><span data-stu-id="c1a6f-108">Dependency Network tab</span></span>](#bkmk_DepNet)  
  
-   [<span data-ttu-id="c1a6f-109">项集选项卡</span><span class="sxs-lookup"><span data-stu-id="c1a6f-109">Itemsets tab</span></span>](#bkmk_Itemsets)  
  
-   [<span data-ttu-id="c1a6f-110">规则选项卡</span><span class="sxs-lookup"><span data-stu-id="c1a6f-110">Rules tab</span></span>](#bkmk_Rules)  
  
-   [<span data-ttu-id="c1a6f-111">“一般内容”视图</span><span class="sxs-lookup"><span data-stu-id="c1a6f-111">Generic Content View</span></span>](#bkmk_ContentViewer)  
  
 <span data-ttu-id="c1a6f-112">对于本教程，你将从 "**依赖关系网络**" 选项卡开始，然后使用 "**规则**" 选项卡和 "**项集**" 选项卡来加深你对查看器中显示的关系的了解。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-112">For this tutorial, you will start on the **Dependency Network** tab, and then use the **Rules** tab and **Itemsets** tab to deepen your understanding of the relationships revealed in the viewer.</span></span> <span data-ttu-id="c1a6f-113">你还将使用**Microsoft 一般内容树查看器**来检索单个规则或项集的详细统计信息。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-113">You will also use the **Microsoft Generic Content Tree Viewer** to retrieve detailed statistics for individual rules or itemsets.</span></span>  
  
##  <a name="dependency-network-tab"></a><a name="bkmk_DepNet"></a><span data-ttu-id="c1a6f-114">依赖关系网络选项卡</span><span class="sxs-lookup"><span data-stu-id="c1a6f-114">Dependency Network Tab</span></span>  
 <span data-ttu-id="c1a6f-115">利用 "**依赖关系网络**" 选项卡，您可以调查模型中不同项的交互。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-115">With the **Dependency Network** tab, you can investigate the interaction of the different items in the model.</span></span> <span data-ttu-id="c1a6f-116">查看器中的每个节点代表一个项，而节点之间的线条则代表规则。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-116">Each node in the viewer represents an item, while the lines between them represent rules.</span></span> <span data-ttu-id="c1a6f-117">通过选择节点，可以查看哪些其他节点预测选定项，还可以查看当前项预测哪些项。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-117">By selecting a node, you can see which other nodes predict the selected item, or which items the current item predicts.</span></span> <span data-ttu-id="c1a6f-118">在某些情况下，项之间存在双向关联，这意味着它们可以出现在同一事务中。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-118">In some cases, there is a two-way association between items, meaning that they often appear in the same transaction.</span></span> <span data-ttu-id="c1a6f-119">您可以参考选项卡底部的颜色图例来确定关联的方向。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-119">You can refer to the color legend at the bottom of the tab to determine the direction of the association.</span></span>  
  
 <span data-ttu-id="c1a6f-120">连接两个项的线条意味着这些项很可能共同出现在同一事务中。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-120">A line connecting two items means that these items are likely to appear in a transaction together.</span></span> <span data-ttu-id="c1a6f-121">也就是说，客户很可能一起购买这些物品。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-121">In other words, customers are likely to buy these items together.</span></span> <span data-ttu-id="c1a6f-122">滑块与规则的概率关联。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-122">The slider is associated with the probability of the rule.</span></span> <span data-ttu-id="c1a6f-123">上下移动滑块可以筛选出弱关联，弱关联意味着这些规则的概率很低。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-123">Move the slider up or down to filter out weak associations, meaning rules with low probability.</span></span>  
  
 <span data-ttu-id="c1a6f-124">"依赖关系网络" 关系图显示成对规则，这些规则可以逻辑上表示为 >B，这意味着，如果购买了产品 A，则可能会出现产品 B。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-124">The dependency network graph shows pairwise rules, which can be represented logically as A->B, meaning if Product A is purchased, then Product B is likely.</span></span> <span data-ttu-id="c1a6f-125">关系图不能显示类型为 AB >C 的规则。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-125">The graph cannot show rules of the type AB->C.</span></span> <span data-ttu-id="c1a6f-126">如果您移动滑块来显示所有规则，但仍未在图中看到任何线条，则意味着没有成对规则满足算法参数的条件。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-126">If you move the slider to show all rules but still do not see any lines in the graph, it means that there were no pairwise rules that met the criteria of the algorithm parameters.</span></span>  
  
 <span data-ttu-id="c1a6f-127">还可以通过键入属性名称的前几个字母，按名称查找节点。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-127">You can also find nodes by name, by typing the first letters of the attribute name.</span></span> <span data-ttu-id="c1a6f-128">有关详细信息，请参阅[“查找节点”对话框（挖掘模型查看器）](../../2014/analysis-services/find-node-dialog-box-mining-model-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-128">For more information, see [Find Node Dialog Box &#40;Mining Model Viewer&#41;](../../2014/analysis-services/find-node-dialog-box-mining-model-viewer.md).</span></span>  
  
#### <a name="to-open-the-association-mode-in-the-microsoft-assocaition-rules-viewer"></a><span data-ttu-id="c1a6f-129">在 Microsoft 关联规则查看器中打开关联模式</span><span class="sxs-lookup"><span data-stu-id="c1a6f-129">To open the Association mode in the Microsoft Assocaition Rules Viewer</span></span>  
  
1.  <span data-ttu-id="c1a6f-130">在**解决方案资源管理器**中，双击关联结构。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-130">In **Solution Explorer**, double-click the Association structure.</span></span>  
  
2.  <span data-ttu-id="c1a6f-131">在数据挖掘设计器中，单击 **“挖掘模型查看器”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-131">In Data Mining Designer, click the **Mining Model Viewer** tab.</span></span>  
  
3.  <span data-ttu-id="c1a6f-132">从 "**挖掘模型**" 下拉列表中的挖掘模型列表中选择 "关联"。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-132">Select Association from the list of mining models in the **Mining Model** dropdown list.</span></span>  
  
#### <a name="to-navigate-the-dependency-graph-and-locate-specific-nodes"></a><span data-ttu-id="c1a6f-133">导航依赖关系图和查找特定节点</span><span class="sxs-lookup"><span data-stu-id="c1a6f-133">To navigate the dependency graph and locate specific nodes</span></span>  
  
1.  <span data-ttu-id="c1a6f-134">在 "**挖掘模型查看器**" 选项卡中，单击 "**依赖关系网络**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-134">In the **Mining Model Viewer** tab, click the **Dependency Network** tab.</span></span>  
  
2.  <span data-ttu-id="c1a6f-135">单击 "**放大**" 几次，直到你可以轻松地查看每个节点的标签。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-135">Click **Zoom In** several times, until you can easily view the labels for each node.</span></span>  
  
     <span data-ttu-id="c1a6f-136">默认情况下，该图会以所有节点都可见这种形式显示。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-136">By default, the graph displays with all nodes visible.</span></span> <span data-ttu-id="c1a6f-137">复杂模型中可能有很多节点，使得每个节点都显得很小。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-137">In a complex model, there may be many nodes, making each node quite small.</span></span>  
  
3.  <span data-ttu-id="c1a6f-138">单击 **+** 查看器右下角的 "登录"，并按住鼠标按钮，以在图形周围平移。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-138">Click the **+** sign in the lower right-hand corner of the viewer and hold down the mouse button to pan around the graph.</span></span>  
  
4.  <span data-ttu-id="c1a6f-139">在查看器的左侧，向下拖动滑块，将默认)  (的**所有链接**移动到滑块控件的底部。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-139">On the left side of the viewer, drag the slider down, moving it from **All Links** (the default) to the bottom of the slider control.</span></span>  
  
5.  <span data-ttu-id="c1a6f-140">查看器更新该图，只显示最强的关联，也就是 Touring Tire 和 Touring Tire Tube 项之间的关联。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-140">The viewer updates the graph to now show only the strongest association, between the Touring Tire and Touring Tire Tube items.</span></span>  
  
6.  <span data-ttu-id="c1a6f-141">单击标记为 "**旅行轮胎电子管 = 现有**" 的节点。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-141">Click the node labeled **Touring Tire Tube = Existing**.</span></span>  
  
     <span data-ttu-id="c1a6f-142">该图进行更新，只突出显示与此项紧密相关的项。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-142">The graph is updated to highlight only items that are strongly related to this item.</span></span> <span data-ttu-id="c1a6f-143">请注意两个项之间箭头的方向。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-143">Note the direction of the arrow between the two items.</span></span>  
  
7.  <span data-ttu-id="c1a6f-144">在查看器的左侧，重新向上拖动滑块，将其从底部移至大约中间位置。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-144">On the left side of the viewer, drag the slider up again, moving it from the bottom to around the middle.</span></span>  
  
     <span data-ttu-id="c1a6f-145">请注意连接两个项的箭头的变化。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-145">Note the changes in the arrow that connects the two items.</span></span>  
  
8.  <span data-ttu-id="c1a6f-146">从 "依赖关系网络" 窗格顶部的下拉列表中选择 "**仅显示属性名称**"。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-146">Select **Show attribute name only** from the dropdown list at the top of the Dependency Network pane.</span></span>  
  
     <span data-ttu-id="c1a6f-147">图中的文本标签会更新为仅显示模型名称。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-147">The text labels in the graph are updated to show only the model name.</span></span>  
  
 [<span data-ttu-id="c1a6f-148">返回页首</span><span class="sxs-lookup"><span data-stu-id="c1a6f-148">Back to Top</span></span>](#bkmk_DepNet)  
  
##  <a name="itemsets-tab"></a><a name="bkmk_Itemsets"></a><span data-ttu-id="c1a6f-149">项集选项卡</span><span class="sxs-lookup"><span data-stu-id="c1a6f-149">Itemsets Tab</span></span>  
 <span data-ttu-id="c1a6f-150">接下来，您将更加详细地了解 Touring Tire 和 Touring Tire Tube 产品的模型所生成的规则和项集。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-150">Next, you will learn more about the rules and itemsets generated by the model for the Touring Tire and Touring Tire Tube products.</span></span> <span data-ttu-id="c1a6f-151">"**项集**" 选项卡显示与关联算法发现的项集相关的三个重要信息片段 [!INCLUDE[msCoName](../includes/msconame-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="c1a6f-151">The **Itemsets** tab displays three important pieces of information that relate to the itemsets that the [!INCLUDE[msCoName](../includes/msconame-md.md)] Association algorithm discovers:</span></span>  
  
-   <span data-ttu-id="c1a6f-152">**支持：** 在其中发生项集的事务的数目。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-152">**Support:** The number of transactions in which the itemset occurs.</span></span>  
  
-   <span data-ttu-id="c1a6f-153">**大小：** 项集中的项数。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-153">**Size:** The number of items in the itemset.</span></span>  
  
-   <span data-ttu-id="c1a6f-154">**项：** 每个项集中包含的项的列表。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-154">**Items:** A list of the items included in each itemset.</span></span>  
  
 <span data-ttu-id="c1a6f-155">根据算法参数的设置方式，算法可能生成多个项集。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-155">Depending on how the algorithm parameters are set, the algorithm might generate many itemsets.</span></span> <span data-ttu-id="c1a6f-156">查看器中返回的每个项集都代表销售该项的事务。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-156">Each itemset that is returned in the viewer represents transactions in which the item was sold.</span></span> <span data-ttu-id="c1a6f-157">通过使用 "**项集**" 选项卡顶部的控件，可以筛选查看器，以便仅显示包含指定的最低支持和项集大小的项集。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-157">By using the controls at the top of the **Itemsets** tab, you can filter the viewer to show only the itemsets that contain a specified minimum support and itemset size.</span></span>  
  
 <span data-ttu-id="c1a6f-158">如果您使用不同的挖掘模型，并且没有列出项集，则原因在于没有项集满足算法参数的条件。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-158">If you are working with a different mining model and no itemsets are listed, it is because no itemsets met the criteria of the algorithm parameters.</span></span> <span data-ttu-id="c1a6f-159">在这种情况下，可以更改算法参数，以允许具有较低支持的项集。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-159">In such a scenario, you can change the algorithm parameters to allow itemsets that have lower support.</span></span>  
  
#### <a name="to-filter-the-itemsets-that-are-shown-in-the-viewer-by-name"></a><span data-ttu-id="c1a6f-160">按名称筛选在查看器中显示的项集</span><span class="sxs-lookup"><span data-stu-id="c1a6f-160">To filter the itemsets that are shown in the viewer by name</span></span>  
  
1.  <span data-ttu-id="c1a6f-161">单击查看器的**项集**选项卡。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-161">Click the **Itemsets** tab of the viewer.</span></span>  
  
2.  <span data-ttu-id="c1a6f-162">在 "**筛选**项集" 框中键入 `Touring Tire` ，然后在框外单击。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-162">In the **Filter Itemset** box, type `Touring Tire`, and then click outside the box.</span></span>  
  
     <span data-ttu-id="c1a6f-163">筛选器返回所有包含此字符串的项。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-163">The filter returns all items that contain this string.</span></span>  
  
3.  <span data-ttu-id="c1a6f-164">在 "**显示**" 列表中，选择 "**仅显示属性名称**"。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-164">In the **Show** list, select **Show attribute name only**.</span></span>  
  
4.  <span data-ttu-id="c1a6f-165">选中 "**显示长名称**" 复选框。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-165">Select the **Show long name** check box.</span></span>  
  
     <span data-ttu-id="c1a6f-166">项集列表会更新为仅显示包含字符串“Touring Tire”的项集。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-166">The list of itemsets is updated to show only the itemsets that contain the string Touring Tire.</span></span> <span data-ttu-id="c1a6f-167">项集的长名称包括了表的名称，表名称包含每个项的属性和值。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-167">The long name of the itemset includes the name of the table that contains the attribute and value for each item.</span></span>  
  
5.  <span data-ttu-id="c1a6f-168">清除 "**显示长名称**" 复选框。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-168">Clear the **Show long name** check box.</span></span>  
  
     <span data-ttu-id="c1a6f-169">项集的列表会更新为仅显示短名称。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-169">The list of itemsets is updated to show only the short name.</span></span>  
  
 <span data-ttu-id="c1a6f-170">**Support**列中的值指示每个项集的事务数。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-170">The values in the **Support** column indicate the number of transactions for each itemset.</span></span> <span data-ttu-id="c1a6f-171">项集的事务表示该购买包括项集中的所有项。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-171">A transaction for an itemset means a purchase that included all the items in the itemset.</span></span>  
  
 <span data-ttu-id="c1a6f-172">默认情况下，查看器按支持的降序列出项集。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-172">By default, the viewer lists the itemsets in descending order by support.</span></span> <span data-ttu-id="c1a6f-173">可以单击列标题，按不同列（例如项集大小或名称）进行排序。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-173">You can click on the column headers to sort by a different column, such as the itemset size or name.</span></span> <span data-ttu-id="c1a6f-174">如果您有兴趣了解关于包括在项集中的各个事务的更多信息，可以从项集钻取到各个事例。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-174">If you are interested in learning more about the individual transactions that are included in an itemset, you can drill through from the itemsets to the individual cases.</span></span> <span data-ttu-id="c1a6f-175">钻取结果中的结构列是客户的收入水平和客户 ID，这些信息未在模型中使用。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-175">The structure columns in the drillthrough results are the customer's income level and customer ID, which were not used in the model.</span></span>  
  
#### <a name="to-view-details-for-an-itemset"></a><span data-ttu-id="c1a6f-176">查看项集的详细信息</span><span class="sxs-lookup"><span data-stu-id="c1a6f-176">To view details for an itemset</span></span>  
  
1.  <span data-ttu-id="c1a6f-177">在项集列表中，单击 "项集" 列**标题，按**名称排序。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-177">In the list of itemsets, click the **Itemset** column heading to sort by name.</span></span>  
  
2.  <span data-ttu-id="c1a6f-178">找到项， `Touring Tire` (不包含第二项) 。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-178">Locate the item, `Touring Tire` (with no second item).</span></span>  
  
3.  <span data-ttu-id="c1a6f-179">右键单击该项，选择 " `Touring Tire` **钻取**"，然后选择 "**模型和结构列**"。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-179">Right-click the item, `Touring Tire`, select **Drill Through**, and then select **Model and Structure Columns**.</span></span>  
  
     <span data-ttu-id="c1a6f-180">"**钻取**" 对话框显示用作支持此项集的单个事务。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-180">The **Drill Through** dialog box displays the individual transactions used as support for this itemset.</span></span>  
  
4.  <span data-ttu-id="c1a6f-181">展开嵌套表 vAssocSeqLineItems 可以查看事务中的实际购买列表。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-181">Expand the nested table, vAssocSeqLineItems, to view the actual list of purchases in the transaction.</span></span>  
  
#### <a name="to-filter-itemsets-by-support-or-size"></a><span data-ttu-id="c1a6f-182">按支持或大小筛选项集</span><span class="sxs-lookup"><span data-stu-id="c1a6f-182">To filter itemsets by support or size</span></span>  
  
1.  <span data-ttu-id="c1a6f-183">清除 "**筛选**项集" 框中可能存在的任何文本。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-183">Clear any text that might be in the **Filter Itemset** box.</span></span> <span data-ttu-id="c1a6f-184">不能将文本筛选器和数值筛选器一起使用。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-184">You cannot use a text filter together with a numeric filter.</span></span>  
  
2.  <span data-ttu-id="c1a6f-185">在 "**最低支持**" 框中，键入 "100"，然后单击查看器的背景。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-185">In the **Minimum support** box, type 100, and then click the background of the viewer.</span></span>  
  
     <span data-ttu-id="c1a6f-186">项集的列表会更新为仅显示支持最低达到 100 的项集。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-186">The list of itemsets is updated to show only itemsets with support of at least 100.</span></span>  
  
 [<span data-ttu-id="c1a6f-187">返回页首</span><span class="sxs-lookup"><span data-stu-id="c1a6f-187">Back to Top</span></span>](#bkmk_DepNet)  
  
##  <a name="rules-tab"></a><a name="bkmk_Rules"></a><span data-ttu-id="c1a6f-188">规则选项卡</span><span class="sxs-lookup"><span data-stu-id="c1a6f-188">Rules Tab</span></span>  
 <span data-ttu-id="c1a6f-189">"**规则**" 选项卡显示与算法找到的规则相关的下列信息。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-189">The **Rules** tab displays the following information that is related to the rules that the algorithm finds.</span></span>  
  
-   <span data-ttu-id="c1a6f-190">**概率：** 规则的*可能性*，定义为给定左侧项的右侧项的概率。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-190">**Probability:** The *likelihood* of a rule, defined as the probability of the right-hand item given the left-hand side item.</span></span>  
  
-   <span data-ttu-id="c1a6f-191">**重要性：** 规则有用性的度量值。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-191">**Importance:** A measure of the usefulness of a rule.</span></span> <span data-ttu-id="c1a6f-192">值越大则意味着规则越有用。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-192">A greater value means a better rule.</span></span>  
  
     <span data-ttu-id="c1a6f-193">重要性用于度量规则的有用性，因为只使用概率可能会发生误导。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-193">Importance is provided to help you gauge the usefulness of a rule, because probability alone can be misleading.</span></span> <span data-ttu-id="c1a6f-194">例如，如果每个事务都包含一个水壶（也许水壶是作为促销活动的一部分自动添加到每位客户的购物车中），该模型会创建一条规则，预测水壶的概率为 1。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-194">For example, if every transaction contains a water bottle--perhaps the water bottle is added to each customer's cart automatically as part of a promotion--the model would create a rule predicting that water bottle has a probability of 1.</span></span> <span data-ttu-id="c1a6f-195">仅依据概率来看，此规则非常准确，但它并未提供有用的信息。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-195">Based on probability alone, this rule is very accurate, but it does not provide useful information.</span></span>  
  
-   <span data-ttu-id="c1a6f-196">**规则：** 规则的定义。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-196">**Rule:** The definition of the rule.</span></span> <span data-ttu-id="c1a6f-197">对于市场篮模型，规则描述特定的项组合。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-197">For a market basket model, a rule describes a specific combination of items.</span></span>  
  
 <span data-ttu-id="c1a6f-198">每条规则都可以根据事务中其他项的发生情况来预测某个项的发生情况。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-198">Each rule can be used to predict the presence of an item in a transaction based on the presence of other items.</span></span> <span data-ttu-id="c1a6f-199">与在 "**项集**" 选项卡中一样，可以筛选规则，以便仅显示最有趣的规则。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-199">Just like in the **Itemsets** tab, you can filter the rules so that only the most interesting rules are shown.</span></span> <span data-ttu-id="c1a6f-200">如果您使用的挖掘模型没有任何规则，您可能希望更改算法参数，以降低规则的概率阈值。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-200">If you are working with a mining model that does not have any rules, you might want to change the algorithm parameters to lower the probability threshold for rules.</span></span>  
  
#### <a name="to-see-only-rules-that-include-the-mountain-200-bicycle"></a><span data-ttu-id="c1a6f-201">仅查看包括 Mountain-200 自行车的规则</span><span class="sxs-lookup"><span data-stu-id="c1a6f-201">To see only rules that include the Mountain-200 bicycle</span></span>  
  
1.  <span data-ttu-id="c1a6f-202">在 "**挖掘模型查看器**" 选项卡中，单击 "**规则**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-202">In the **Mining Model Viewer** tab, click the **Rules** tab.</span></span>  
  
2.  <span data-ttu-id="c1a6f-203">在 "**筛选规则**" 框中，输入 `Mountain-200` 。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-203">In the **Filter Rule** box, enter `Mountain-200`.</span></span>  
  
     <span data-ttu-id="c1a6f-204">清除 "**显示长名称**" 复选框。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-204">Clear the **Show long name** check box.</span></span>  
  
3.  <span data-ttu-id="c1a6f-205">从 "**显示**" 列表中，选择 "**仅显示属性名称**"。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-205">From the **Show** list, select **Show attribute name only**.</span></span>  
  
     <span data-ttu-id="c1a6f-206">然后，查看器将只显示包含词 "" 的规则 `Mountain-200` 。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-206">The viewer will then display only the rules that contain the words "`Mountain-200`".</span></span> <span data-ttu-id="c1a6f-207">规则的概率告诉你当某人购买 `Mountain-200` 自行车时，该人还会购买所列的其他产品。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-207">The probability of the rule tells you how likely it is that when someone buys a `Mountain-200` bicycle, that person will also buy the other listed product.</span></span>  
  
 <span data-ttu-id="c1a6f-208">这些规则按照概率降序排序，但您可以单击栏标题来更改排序顺序。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-208">The rules are ordered by probability in descending order, but you can click the column headings to change the sort order.</span></span> <span data-ttu-id="c1a6f-209">如果您有兴趣查找关于某个特定规则的更多详细信息，可以使用钻取功能来查看支持事例。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-209">If you are interested in finding out more details about a particular rule, you can use drillthrough to view the supporting cases.</span></span>  
  
#### <a name="to-view-cases-that-support-a-particular-rule"></a><span data-ttu-id="c1a6f-210">查看支持特定规则的事例</span><span class="sxs-lookup"><span data-stu-id="c1a6f-210">To view cases that support a particular rule</span></span>  
  
1.  <span data-ttu-id="c1a6f-211">在 "**规则**" 选项卡中，右键单击要查看的规则。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-211">In the **Rules** tab, right-click the rule that you want to view.</span></span>  
  
2.  <span data-ttu-id="c1a6f-212">选择 "**钻取**"，然后选择 "**仅限模型列**" 或 "**模型和结构列**"。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-212">Select **Drill Through**, and then select **Model Columns Only**, or **Model and Structure Columns**.</span></span>  
  
     <span data-ttu-id="c1a6f-213">"**钻取**" 对话框提供了窗格顶部的规则的摘要，以及用作规则的支持数据的所有事例的列表。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-213">The **Drill Through** dialog box provides a summary of the rule at the top of the pane, and a list of all cases that were used as supporting data for the rule.</span></span>  
  
 [<span data-ttu-id="c1a6f-214">返回页首</span><span class="sxs-lookup"><span data-stu-id="c1a6f-214">Back to Top</span></span>](#bkmk_DepNet)  
  
##  <a name="generic-content-tree-viewer"></a><a name="bkmk_ContentViewer"></a><span data-ttu-id="c1a6f-215">一般内容树查看器</span><span class="sxs-lookup"><span data-stu-id="c1a6f-215">Generic Content Tree Viewer</span></span>  
 <span data-ttu-id="c1a6f-216">此查看器可用于所有模型，无论算法和模型类型为何均为如此。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-216">This viewer can be used for all models, regardless of the algorithm or model type.</span></span> <span data-ttu-id="c1a6f-217">" **Microsoft 一般内容树查看器**" 可从 "**查看器**" 下拉列表中找到。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-217">The **Microsoft Generic Content Tree Viewer** is available from the **Viewer** drop-down list.</span></span>  
  
 <span data-ttu-id="c1a6f-218">内容树是挖掘模型的表示形式，由一系列节点组成，其中每个节点都表示与数据的某一子集相关的已发现的知识。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-218">A content tree is a representation of a mining model as a series of nodes, where each node represents learned knowledge about some subset of the data.</span></span> <span data-ttu-id="c1a6f-219">节点可以包含一种模式、一组规则、一个群集或共享某些特性的日期范围的定义。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-219">The node can contain a pattern, a set of rules, a cluster, or the definition of a range of dates that share some characteristics.</span></span> <span data-ttu-id="c1a6f-220">根据算法和可预测属性的类型的不同，节点的具体内容也会不同，但内容的通用表示形式是相同的。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-220">The exact content of the node differs depending on the algorithm and the type of the predictable attribute, but the general representation of the content is the same.</span></span> <span data-ttu-id="c1a6f-221">您可以展开每个节点以查看详细信息的递增级别，并可以将任何节点的内容复制到剪贴板。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-221">You can expand each node to see increasing levels of detail, and copy the content of any node to the Clipboard.</span></span>  
  
#### <a name="to-view-details-about-the-rule-by-using-the-content-viewer"></a><span data-ttu-id="c1a6f-222">使用内容查看器查看关于规则的详细信息</span><span class="sxs-lookup"><span data-stu-id="c1a6f-222">To view details about the rule by using the content viewer</span></span>  
  
1.  <span data-ttu-id="c1a6f-223">在 "**挖掘模型查看器**" 选项卡中，从**查看器**列表中选择 " **Microsoft 一般内容树查看器**"。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-223">In the **Mining Model Viewer** tab, select **Microsoft Generic Content Tree Viewer** from the **Viewer** list.</span></span>  
  
2.  <span data-ttu-id="c1a6f-224">在“节点标题”窗格中，滚动到列表的底部，然后单击最后一个节点。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-224">In the Node Caption pane, scroll to the bottom of the list, and click the last node.</span></span>  
  
     <span data-ttu-id="c1a6f-225">查看器首先显示项集，接下来显示规则，但不对它们进行分组。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-225">The viewer shows itemsets first and rules next, but does not group them.</span></span> <span data-ttu-id="c1a6f-226">查找特定节点的最简单方法是创建内容查询。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-226">The easiest way to find a specific node is to create a content query.</span></span> <span data-ttu-id="c1a6f-227">有关详细信息，请参阅 [关联模型查询示例](../../2014/analysis-services/data-mining/association-model-query-examples.md)</span><span class="sxs-lookup"><span data-stu-id="c1a6f-227">For more information, see [Association Model Query Examples](../../2014/analysis-services/data-mining/association-model-query-examples.md).</span></span>  
  
3.  <span data-ttu-id="c1a6f-228">在“节点详细信息”窗格中，查看 NODE_TYPE 和 NODE_DESCRIPTION 的值。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-228">In the Node Details pane, review the value for NODE_TYPE and NODE_DESCRIPTION.</span></span>  
  
     <span data-ttu-id="c1a6f-229">节点类型 8 是规则，节点类型 7 是项集。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-229">A node type of 8 is a rule, and a node type of 7 is an itemset.</span></span> <span data-ttu-id="c1a6f-230">对于规则来说，NODE_DESCRIPTION 的值指示了构成规则的条件。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-230">For a rule, the value of NODE_DESCRIPTION tells you the conditions that make up the rule.</span></span> <span data-ttu-id="c1a6f-231">对于项集来说，NODE_DESCRIPTION 的值指示了包括在项集中的项。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-231">For an itemset, the value of NODE_DESCRIPTION tells you the items included in the itemset.</span></span>  
  
 <span data-ttu-id="c1a6f-232">您还可以创建内容查询，以获取关于规则的详细统计信息。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-232">You can also create a content query to obtain detailed statistics about the rules.</span></span> <span data-ttu-id="c1a6f-233">有关挖掘模型内容以及如何对其进行解释的详细信息，请参阅[关联模型的挖掘模型内容 &#40;Analysis Services 数据挖掘&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-association-models-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="c1a6f-233">For more information about mining model content and how to interpret it, see [Mining Model Content for Association Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-association-models-analysis-services-data-mining.md).</span></span>  
  
 [<span data-ttu-id="c1a6f-234">返回页首</span><span class="sxs-lookup"><span data-stu-id="c1a6f-234">Back to Top</span></span>](#bkmk_DepNet)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="c1a6f-235">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="c1a6f-235">Next Task in Lesson</span></span>  
 [<span data-ttu-id="c1a6f-236">在挖掘模型中筛选嵌套表 &#40;中级数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="c1a6f-236">Filtering a Nested Table in a Mining Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/filtering-a-nested-table-in-a-mining-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="c1a6f-237">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c1a6f-237">See Also</span></span>  
 <span data-ttu-id="c1a6f-238">[第3课：生成市场篮方案 &#40;中级数据挖掘教程&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="c1a6f-238">[Lesson 3: Building a Market Basket Scenario &#40;Intermediate Data Mining Tutorial&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md) </span></span>  
 <span data-ttu-id="c1a6f-239">[第4课：生成顺序分析和聚类分析方案 &#40;中级数据挖掘教程&#41;](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="c1a6f-239">[Lesson 4: Building a Sequence Clustering Scenario &#40;Intermediate Data Mining Tutorial&#41;](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md) </span></span>  
 <span data-ttu-id="c1a6f-240">[Microsoft 关联算法](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="c1a6f-240">[Microsoft Association Algorithm](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md) </span></span>  
 [<span data-ttu-id="c1a6f-241">Microsoft 关联算法技术参考</span><span class="sxs-lookup"><span data-stu-id="c1a6f-241">Microsoft Association Algorithm Technical Reference</span></span>](../../2014/analysis-services/data-mining/microsoft-association-algorithm-technical-reference.md)  
  
  
