---
title: 浏览关联规则模型 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, browsing
- mining model, association
- mining models, viewing
- association [data mining]
ms.assetid: faffe208-7a64-4ec6-825f-ecbaa79caff7
author: minewiskan
ms.author: owend
ms.openlocfilehash: de5adbca264fff81b44424d865a2c8201a6fdfc3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579291"
---
# <a name="browsing-an-association-rules-model"></a><span data-ttu-id="6fd9d-102">浏览关联规则模型</span><span class="sxs-lookup"><span data-stu-id="6fd9d-102">Browsing an Association Rules Model</span></span>
  <span data-ttu-id="6fd9d-103">使用 "**浏览**" 打开关联模型时，该模型将显示在交互式查看器中，类似于中的关联规则查看器 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-103">When you open an association model using **Browse**, the model is displayed in an interactive viewer, similar to the Association Rules Viewer in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  <span data-ttu-id="6fd9d-104">此查看器让您能对彼此关联的项一目了然，并显示可用于预测或提出建议的规则。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-104">The viewer lets you see at a glance which items were correlated with each other, and displays rules that you can use for prediction or making recommendations.</span></span>  
  
##  <a name="explore-the-model"></a><a name="BKMK_ViewerTabs"></a><span data-ttu-id="6fd9d-105">浏览模型</span><span class="sxs-lookup"><span data-stu-id="6fd9d-105">Explore the Model</span></span>  
 <span data-ttu-id="6fd9d-106">当您打开使用关联规则算法创建的挖掘模型时 [!INCLUDE[msCoName](../includes/msconame-md.md)] ，"**浏览**" 窗口包括以下视图，每个视图都允许您浏览模型的不同方面：</span><span class="sxs-lookup"><span data-stu-id="6fd9d-106">When you open a mining model that was created using the [!INCLUDE[msCoName](../includes/msconame-md.md)] Association Rules algorithm, the **Browse** window includes the following views, each designed to let you explore a different aspect of the model:</span></span>  
  
-   [<span data-ttu-id="6fd9d-107">项集</span><span class="sxs-lookup"><span data-stu-id="6fd9d-107">Itemsets</span></span>](#BKMK_Itemsets)  
  
-   [<span data-ttu-id="6fd9d-108">规则</span><span class="sxs-lookup"><span data-stu-id="6fd9d-108">Rules</span></span>](#BKMK_Rules)  
  
-   [<span data-ttu-id="6fd9d-109">依赖关系网络</span><span class="sxs-lookup"><span data-stu-id="6fd9d-109">Dependency Net</span></span>](#BKMK_Dependency)  
  
 <span data-ttu-id="6fd9d-110">记下每个选项卡上的选项 "**显示长名称**"。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-110">Take note of the option on each tab, **Show long name** .</span></span> <span data-ttu-id="6fd9d-111">通过选择此选项，您可以显示或隐藏项集的来源表，并且可以缩短或延长规则或项集的名称。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-111">By selecting this option, you can show or hide the table from which the itemset originates, and shorten or lengthen the name of the rule or itemset.</span></span> <span data-ttu-id="6fd9d-112">在事例数据和属性数据来自不同的数据源时，此选项特别有用。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-112">This option is particularly useful when your case data and attribute data are from different data sources.</span></span>  
  
 <span data-ttu-id="6fd9d-113">若要试验关联模型，可使用示例数据工作簿的“关联”选项卡上的示例数据，然后使用所有默认值建立关联模型。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-113">To experiment with an association model, you can use the sample data on the Associate tab of the sample data workbook, and build an association model using all the defaults.</span></span> <span data-ttu-id="6fd9d-114">你还可以使用 "**浏览**" 来构建购物篮分析模型并打开它。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-114">You can also build a Shopping Basket Analysis model and open that using **Browse**.</span></span>  
  
###  <a name="itemsets"></a><a name="BKMK_Itemsets"></a><span data-ttu-id="6fd9d-115">项集</span><span class="sxs-lookup"><span data-stu-id="6fd9d-115">Itemsets</span></span>  
 <span data-ttu-id="6fd9d-116">"**项集**" 选项卡是开始浏览关联模型的好地方。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-116">The **Itemsets** tab is a good place to begin exploring an association model.</span></span> <span data-ttu-id="6fd9d-117">此选项卡列出模型经常发现一起出现的项。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-117">This tab shows a list of the items that the model frequently found together.</span></span>  
  
 <span data-ttu-id="6fd9d-118">![关联模型中项的列表](media/dm13-association-itemsets.gif "关联模型中项的列表")</span><span class="sxs-lookup"><span data-stu-id="6fd9d-118">![List of items in an association model](media/dm13-association-itemsets.gif "List of items in an association model")</span></span>  
  
 <span data-ttu-id="6fd9d-119">最常见的项集示例出现在购物篮模型中，在此模型中，项集表示大量顾客在一次购物中同时购买的产品对或产品集。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-119">The most common example of itemsets is in a shopping basket model, where an itemset represents pairs or sets of products that lots of customers purchase at the same time.</span></span> <span data-ttu-id="6fd9d-120">不过，根据您分组和排序项的方式，项集可能包含顾客在一段时间内订购的影片序列，或倾向在特定位置发生的事件。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-120">However, depending on how you group and order your items, the itemset might contain a sequence of movies that customers order over a period of time, or events that tend to occur in  a particular location.</span></span>  
  
 <span data-ttu-id="6fd9d-121">一个*项集只能包含*一项到两个、三个或多个项，也可以将多个项设置为该模型的最大项集大小。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-121">An *itemset* can contain as few as one item to two, three, or however, many is set as the maximum itemset size for the model.</span></span> <span data-ttu-id="6fd9d-122">对于每个项集，查看器将显示项集的*支持*、*概率*和*大小*。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-122">For each itemset, the viewer displays the itemset  *support*,  *probability*, and *size*.</span></span> <span data-ttu-id="6fd9d-123">支持和概率是用于对关联模型生成的项集和规则进行排名的主要统计信息。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-123">Support and probability are the principal statistics used to rank the itemsets and rules generated by an association model.</span></span> <span data-ttu-id="6fd9d-124">这些值还用于计算和描述项集的重要性。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-124">These values are also used to calculate and describe their importance.</span></span>  
  
 <span data-ttu-id="6fd9d-125">**支持**。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-125">**Support**.</span></span> <span data-ttu-id="6fd9d-126">支持表示包含此项的事例数或输入数据行数。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-126">Support means the number of cases or rows of input data that have this item.</span></span> <span data-ttu-id="6fd9d-127">例如，如果项集包含在购物车中找到的两个项，则 "**支持**" 列中的数字指示在源数据中发生项组合的次数。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-127">For example, if an itemset contains two items that are found in a shopping cart, the number in the **Support** column indicates how many times that combination of items occurred in the source data.</span></span>  
  
 <span data-ttu-id="6fd9d-128">**大小**。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-128">**Size**.</span></span> <span data-ttu-id="6fd9d-129">通过更改项集大小，您可以控制项集列表的长度。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-129">By changing itemset size, you can control the length of the lists of itemsets.</span></span> <span data-ttu-id="6fd9d-130">如果不想看到列表中的单个产品，请将选项 "**最小**项集大小" 更改为2或更大。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-130">If you don't want to see single products in the list, change the option, **Minimum itemset size**, to 2 or more.</span></span>  <span data-ttu-id="6fd9d-131">通过增加项集最小大小来限制列表，您可以查找更为具体的模式。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-131">Restricting the list by increasing the minimum size of itemsets lets you look for very specific patterns.</span></span> <span data-ttu-id="6fd9d-132">在处理大型数据集时，这种方法可能很有用。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-132">This might be useful if you are working with a very large set of data.</span></span>  
  
 <span data-ttu-id="6fd9d-133">可以通过更改 "**最低支持**" 和 "**最大行**数" 值来筛选选项卡中显示的项集的数目。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-133">You can filter the number of itemsets that are displayed in the tab by changing the **Minimum support** and **Maximum rows** values.</span></span> <span data-ttu-id="6fd9d-134">如果增加**最小支持**值，列表将显示较少的项集，但项集将是输入数据中更常见的值。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-134">If you increase the **Minimum Support** value, the list will show fewer itemsets, but the itemsets will be the more common ones in the input data.</span></span> <span data-ttu-id="6fd9d-135">与 "重要" 是否相同是 "重要" 是另一个问题，你可以使用 "**规则**" 选项卡浏览。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-135">Whether common is the same as important is another question, which you can explore using the **Rules** tab.</span></span>  
  
 <span data-ttu-id="6fd9d-136">请注意，更改 "**项集**" 选项卡上的支持值或其他控件仅更改显示的项，而不会影响基础模型。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-136">Note that changing the support value or other controls on the **Itemsets** tab only changes the items that are displayed, and does not affect the underlying model.</span></span> <span data-ttu-id="6fd9d-137">如果要生成更少或更多的项集或限制其大小，应使用 `MINIMUM_SUPPORT` `MAXIMUM_SUPPORT` "**算法参数**" 对话框中提供的参数和。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-137">If you want to generate fewer or more itemsets, or limit their size, you should use the parameters, `MINIMUM_SUPPORT` and `MAXIMUM_SUPPORT`, available in the **Algorithm Parameters** dialog box.</span></span>  
  
##### <a name="explore-the-itemsets-list"></a><span data-ttu-id="6fd9d-138">探索项集列表</span><span class="sxs-lookup"><span data-stu-id="6fd9d-138">Explore the itemsets list</span></span>  
  
1.  <span data-ttu-id="6fd9d-139">单击 "**支持**" 列以便按最高到最低的支持排序。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-139">Click the **Support** column to sort by highest to lowest support.</span></span> <span data-ttu-id="6fd9d-140">这样一来，您可以了解顾客最常购买的商品。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-140">This will give you an idea of what customers are buying most often.</span></span>  
  
2.  <span data-ttu-id="6fd9d-141">若要将重点放在可能的一个或多个组合中，请在 "**筛选**项集" 框中键入一些文本。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-141">To focus on a particular itemset of interest, out of the many thousand combinations possible, type some text in the **Filter Itemset** box.</span></span>  
  
     <span data-ttu-id="6fd9d-142">这里，我们键入了 `Gloves` 。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-142">Here we typed `Gloves`.</span></span> <span data-ttu-id="6fd9d-143">应用此筛选器时，列表将会刷新，仅显示包含手套的项集。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-143">When you apply the filter, the list is refreshed to show only itemsets containing gloves.</span></span> <span data-ttu-id="6fd9d-144">这样一来，您可以重点关注顾客购买手套及其他一些商品的交易。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-144">This lets you focus on the transactions where customers purchased gloves and some other item.</span></span>  
  
     <span data-ttu-id="6fd9d-145">**“筛选项集”** 选项还会显示您以前使用过的筛选器列表。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-145">The **Filter Itemset** option also displays a list of the filters that you have used previously.</span></span>  
  
3.  <span data-ttu-id="6fd9d-146">更改 "**最小**项集大小" 的值，以筛选出仅购买了手套而不是其他商品的客户。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-146">Change the value of **Minimum itemset size** to filter out the customers who bought only gloves and no other items.</span></span>  
  
4.  <span data-ttu-id="6fd9d-147">单击 "**显示**" 选项的下拉列表以控制属性的显示方式：</span><span class="sxs-lookup"><span data-stu-id="6fd9d-147">Click the dropdown list for the option **Show**, to control how the attributes are displayed:</span></span>  
  
    -   <span data-ttu-id="6fd9d-148">**显示属性名称和值**</span><span class="sxs-lookup"><span data-stu-id="6fd9d-148">**Show attribute name and value**</span></span>  
  
    -   <span data-ttu-id="6fd9d-149">**仅显示属性值**</span><span class="sxs-lookup"><span data-stu-id="6fd9d-149">**Show attribute value only**</span></span>  
  
    -   <span data-ttu-id="6fd9d-150">**仅显示属性名称**</span><span class="sxs-lookup"><span data-stu-id="6fd9d-150">**Show attribute name only**</span></span>  
  
     <span data-ttu-id="6fd9d-151">请注意名称发生了怎样的变化。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-151">Notice how the name changes.</span></span> <span data-ttu-id="6fd9d-152">就购物篮模型而言，它是基于多位顾客已购买产品的嵌套表构建的，属性名称通常是产品名称，产品在列表中的存在状态被标记为`Existing`，表示顾客已购买了此物品。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-152">In the case of a market basket model, which is built on nested tables of products that were purchased by multiple customers, the attribute name is typically the product name, and the presence of the product in the list is marked as `Existing`, meaning that the customer did buy the item.</span></span>  
  
     <span data-ttu-id="6fd9d-153">与`Existing`相反的是`Missing`，后者对于在数据挖掘中开展调查会非常有用。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-153">The opposite of `Existing` is `Missing`, which can be a very useful attribute to investigate in data mining.</span></span> <span data-ttu-id="6fd9d-154">例如，假设项集 A + B 非常受欢迎，希望查找购买项 A 但不是项 B 的客户。为此，您可以使用预测查询并检索其中一个事务，而不是另一个事务，并对这些事务进行进一步的分析。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-154">For example, suppose the itemset A +B is so very popular that you wanted to find customers who purchased Item A but not item B. You could do this by using a prediction query and retrieving the transactions with one but not the other, and do some further analysis on those.</span></span> <span data-ttu-id="6fd9d-155">有关如何创建针对关联模型的预测查询的信息，请参阅 SQL Server 联机丛书中的[关联模型查询示例](data-mining/association-model-query-examples.md)</span><span class="sxs-lookup"><span data-stu-id="6fd9d-155">For information about how to create prediction queries on association models, see [Association Model Query Examples](data-mining/association-model-query-examples.md) in SQL Server Books Online</span></span>  
  
5.  <span data-ttu-id="6fd9d-156">若要强制使用新筛选条件重新显示项集列表，可以选中或清除 "**显示长名称**" 复选框。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-156">To force the list of itemsets to redisplay using your new filter criteria, you can select or clear the **Show long name** check box.</span></span>  
  
 [<span data-ttu-id="6fd9d-157">返回页首</span><span class="sxs-lookup"><span data-stu-id="6fd9d-157">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
###  <a name="rules"></a><a name="BKMK_Rules"></a><span data-ttu-id="6fd9d-158">原则</span><span class="sxs-lookup"><span data-stu-id="6fd9d-158">Rules</span></span>  
 <span data-ttu-id="6fd9d-159">"**规则**" 选项卡将有关项集及其相对值的信息合并在一起。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-159">The **Rules** tab combines information about the itemsets and their relative value.</span></span>  
  
 <span data-ttu-id="6fd9d-160">![关联模型创建的规则列表](media/dm13-association-rules.gif "关联模型创建的规则列表")</span><span class="sxs-lookup"><span data-stu-id="6fd9d-160">![List of rules created by an association model](media/dm13-association-rules.gif "List of rules created by an association model")</span></span>  
  
 <span data-ttu-id="6fd9d-161">*概率*表示包含目标组合项的数据集中的事例部分。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-161">*Probability* represents the fraction of cases in the dataset that contain the targeted combination of items.</span></span> <span data-ttu-id="6fd9d-162">"概率" 类似于 "*置信度*" 的统计概念，并提供了有关如何发生规则结果的指示。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-162">Probability is similar to the statistical concept of *confidence*, and gives you an indication of how likely the result of a rule is to occur.</span></span> <span data-ttu-id="6fd9d-163">可以在此窗格中更改 "**最小概率**" 的值，以筛选所显示的规则。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-163">You can change the value of **Minimum probability** in this pane to filter the rules that are displayed.</span></span>  
  
 <span data-ttu-id="6fd9d-164">最初看到的**最小概率**值是在生成模型时算法使用的阈值。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-164">The value for **Minimum probability** that you initially see is the threshold value that was used by the algorithm when building the model.</span></span> <span data-ttu-id="6fd9d-165">模型完成后，你将无法减少此值，但你可以将其增大到仅显示更高概率项。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-165">After the model is complete, you can't decrease this value, but you can increase it to show only the higher probability items.</span></span>  
  
 <span data-ttu-id="6fd9d-166">*重要性*用于度量规则的有用性。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-166">*Importance* is designed to measure the usefulness of a rule.</span></span> <span data-ttu-id="6fd9d-167">非常常见的规则可能非常普遍，具有很少的信息价值。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-167">A rule that is very common might be so ubiquitous that is has little information value.</span></span> <span data-ttu-id="6fd9d-168">重要性越高，则该规则用于预测结果的价值就越高。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-168">The greater the importance, the more valuable the rule is for predicting the outcome.</span></span> <span data-ttu-id="6fd9d-169">在[购物篮分析 &#40;表 AnalysisTools For Excel&#41;](shopping-basket-analysis-table-analysistools-for-excel.md)工具中，重要性可以与商品价格结合，以确定在销售方面可能最有价值的捆绑包。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-169">In the [Shopping Basket Analysis &#40;Table AnalysisTools for Excel&#41;](shopping-basket-analysis-table-analysistools-for-excel.md) tool, importance can be combined with the price of items to determine the bundles that are potentially most valuable in terms of sales.</span></span>  
  
##### <a name="explore-the-rules-list"></a><span data-ttu-id="6fd9d-170">探索规则列表</span><span class="sxs-lookup"><span data-stu-id="6fd9d-170">Explore the rules list</span></span>  
  
1.  <span data-ttu-id="6fd9d-171">尝试单击列标题 "**概率**"、"**重要性**" 和 "**规则**" 以查看数据更改的方式。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-171">Try clicking the column headings - **Probability**, **Importance**, and **Rule** - to see how the data changes.</span></span>  
  
2.  <span data-ttu-id="6fd9d-172">使用 "**筛选规则**" 选项可以键入值并专注于目标规则。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-172">Use the **Filter Rule** option to type in values and focus on targeted rules.</span></span>  
  
     <span data-ttu-id="6fd9d-173">例如，如果想要查看预测哪些客户可能与手套一起购买的所有规则，请在文本框中键入 "手套" 并刷新窗格。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-173">For example, if you want to see all the rules that predict what customers are likely to purchase along with gloves, type "gloves" in the text box and refresh the pane.</span></span>  
  
     <span data-ttu-id="6fd9d-174">**“筛选项集”** 选项还会显示您以前使用过的筛选器列表。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-174">The **Filter Itemset** option also displays a list of the filters that you have used previously.</span></span>  
  
3.  <span data-ttu-id="6fd9d-175">若要强制使用筛选条件重新显示规则列表，可以选中或清除 "**显示长名称**" 复选框。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-175">To force the list of rules to redisplay using filter criteria, you can select or clear the **Show long name** check box.</span></span>  
  
4.  <span data-ttu-id="6fd9d-176">使用选项 "**显示**" 以控制规则名称的显示方式。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-176">Use the option, **Show** to control the way that rule names are displayed.</span></span>  
  
5.  <span data-ttu-id="6fd9d-177">将 "**最大行数**" 选项的值设置为100，然后单击 "**复制到 Excel**"。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-177">Set the value for the **Maximum rows** option to 100, and then click **Copy to Excel**.</span></span>  
  
     <span data-ttu-id="6fd9d-178">请注意，更改此值不会对模型中的数据量产生任何影响;它只控制显示列表中的行数。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-178">Note that changing this value doesn't have any effect on the amount of data in the model; it simply controls the number of rows in the display list.</span></span> <span data-ttu-id="6fd9d-179">在使用特大型模型时，此选项会很有用。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-179">This option can be useful when working with very large models.</span></span>  
  
 [<span data-ttu-id="6fd9d-180">返回页首</span><span class="sxs-lookup"><span data-stu-id="6fd9d-180">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
###  <a name="dependency-network"></a><a name="BKMK_Dependency"></a><span data-ttu-id="6fd9d-181">依赖关系网络</span><span class="sxs-lookup"><span data-stu-id="6fd9d-181">Dependency Network</span></span>  
 <span data-ttu-id="6fd9d-182">"**依赖关系网络**" 选项卡是项之间的关联的可视化地图。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-182">The **Dependency Network** tab is a visual map of the correlations among items.</span></span> <span data-ttu-id="6fd9d-183">关系图中的每个椭圆 (称为*节点*) 表示属性-值对，如 "背心 = 现有" 或 "Age = 1-30"。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-183">Each oval in the graph (referred to as a *node*) represents an attribute-value pair, such as "Vest = Existing" or "Age = 1-30".</span></span>  <span data-ttu-id="6fd9d-184">连接各个椭圆的每行 (称为*边缘*) 表示一种相关性。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-184">Each line connecting the ovals (referred to as an *edge*) represents a type of correlation.</span></span>  
  
 <span data-ttu-id="6fd9d-185">![关联模型的依赖关系网络图形](media/dm13-association-dependencynetwork.gif "关联模型的依赖关系网络图形")</span><span class="sxs-lookup"><span data-stu-id="6fd9d-185">![Dependency network graph for an association model](media/dm13-association-dependencynetwork.gif "Dependency network graph for an association model")</span></span>  
  
##### <a name="explore-the-dependency-network"></a><span data-ttu-id="6fd9d-186">探索依赖关系网络</span><span class="sxs-lookup"><span data-stu-id="6fd9d-186">Explore the dependency network</span></span>  
  
1.  <span data-ttu-id="6fd9d-187">单击 "**查找**" 按钮，然后使用 "**查找节点**" 对话框键入感兴趣的项。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-187">Click the **Find** button and use the **Find Node** dialog box to type an item of interest.</span></span>  
  
     <span data-ttu-id="6fd9d-188">例如，键入 "手套"，然后在窗口中最大化图形，以便您可以轻松地看到结果。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-188">For example, type "gloves" and then maximize the graph in the window so that you can easily see the results.</span></span>  
  
     <span data-ttu-id="6fd9d-189">包含此项的节点突出显示，指向节点的箭头表示连接项的规则。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-189">The node that contains the item is highlighted, while the arrows pointing to the node represent a rule that connects the items.</span></span>  
  
     <span data-ttu-id="6fd9d-190">箭头的方向指示规则的方向。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-190">The direction of the arrow tells you the direction of the rule.</span></span> <span data-ttu-id="6fd9d-191">例如，如果购买了手套的人员也可能购买背心，箭头将从 "手套" 节点开始，并在 "背心" 节点上终止。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-191">For example, if someone who buys gloves is also likely to buy a vest, the arrow will start from the "glove" node and terminate on the "vest" node.</span></span>  
  
     <span data-ttu-id="6fd9d-192">若要获取有关此规则的附加统计信息，可以单击 "**规则**" 选项卡，然后查找描述为 "手套"-> "背心" 的规则。) </span><span class="sxs-lookup"><span data-stu-id="6fd9d-192">To get additional statistics about this rule, you can click the **Rules** tab and look for a rule with the description, "Glove - Existing" -> "Vest - Existing.")</span></span>  
  
2.  <span data-ttu-id="6fd9d-193">单击并拖动查看器左侧的滑块。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-193">Click and drag the slider at the left of the viewer.</span></span>  
  
     <span data-ttu-id="6fd9d-194">滑块可作为规则概率的筛选器使用。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-194">The slider acts as a filter on the probability of the rules.</span></span> <span data-ttu-id="6fd9d-195">降低滑块将只显示最强规则。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-195">Lowering the slider shows only the strongest rules.</span></span>  
  
3.  <span data-ttu-id="6fd9d-196">单击 "**复制到 excel** "，将当前窗口的快照复制到 excel。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-196">Click **Copy to Excel** to copy a snapshot of the current window to Excel.</span></span>  
  
     <span data-ttu-id="6fd9d-197">无法使用复制到 Excel 中的图形。如果需要交互式网络图形，请使用在[Visio 中查看数据挖掘模型 &#40;数据挖掘外接程序&#41;](viewing-data-mining-models-in-visio-data-mining-add-ins.md)。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-197">You won't be able to work with the graph that you copy into Excel; if you need an interactive network graph, use the [Viewing Data Mining Models in Visio &#40;Data Mining Add-ins&#41;](viewing-data-mining-models-in-visio-data-mining-add-ins.md).</span></span>  
  
 [<span data-ttu-id="6fd9d-198">返回页首</span><span class="sxs-lookup"><span data-stu-id="6fd9d-198">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
## <a name="more-about-association-models"></a><span data-ttu-id="6fd9d-199">有关关联模型的详细信息</span><span class="sxs-lookup"><span data-stu-id="6fd9d-199">More about Association Models</span></span>  
 <span data-ttu-id="6fd9d-200">您可以使用 "**浏览**" 功能打开并浏览使用 Microsoft 关联规则算法创建的任何模型。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-200">You can use the **Browse** feature to open and explore any model that was created using the Microsoft Association Rules algorithm.</span></span> <span data-ttu-id="6fd9d-201">这包括使用[购物篮分析 &#40;Table AnalysisTools For Excel&#41;](shopping-basket-analysis-table-analysistools-for-excel.md)工具、**表分析工具**功能区中或中生成的模型 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-201">This includes models built using the [Shopping Basket Analysis &#40;Table AnalysisTools for Excel&#41;](shopping-basket-analysis-table-analysistools-for-excel.md) tool, in the **Table Analysis Tools** ribbon, or in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="6fd9d-202">如果使用购物篮分析工具创建关联规则模型，则会自动为您配置许多高级选项。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-202">If you create an association rules model using the Shopping Basket Analysis tool, many of the advanced options are configured automatically for you.</span></span>  
  
 <span data-ttu-id="6fd9d-203">如果要设置高级参数或更改最小概率和支持，请使用[关联向导 &#40;excel&#41;的数据挖掘客户端](associate-wizard-data-mining-client-for-excel.md)"向导，或使用"[将 &#40;用于 Excel 的数据挖掘外数据挖掘外接程序&#41;](add-model-to-structure-data-mining-add-ins-for-excel.md)建模 "选项构建你自己的模型。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-203">If you want to set advanced parameters or alter minimum probability and support, use the [Associate Wizard &#40;Data Mining Client for Excel&#41;](associate-wizard-data-mining-client-for-excel.md) wizard, or build your own model using the [Add Model to Structure &#40;Data Mining Add-ins for Excel&#41;](add-model-to-structure-data-mining-add-ins-for-excel.md) modeling option.</span></span>  
  
-   <span data-ttu-id="6fd9d-204">**项集：** 创建模型时，还可以通过向 MINIMUM_PROBABILITY 参数赋值来控制生成的项集的数目。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-204">**Itemsets:** When you create the model, you can also control the number of itemsets that are generated by assigning a value to the MINIMUM_PROBABILITY parameter.</span></span> <span data-ttu-id="6fd9d-205">此参数可从“算法参数”对话框中获得。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-205">This parameter is available in the Algorithm Parameters dialog box.</span></span>  
  
-   <span data-ttu-id="6fd9d-206">**规则：**[!INCLUDE[msCoName](../includes/msconame-md.md)]关联规则算法使用概率值来限制所生成的规则数。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-206">**Rules:** The [!INCLUDE[msCoName](../includes/msconame-md.md)] Association Rules algorithm uses probability values to restrict the number of rules that are generated.</span></span> <span data-ttu-id="6fd9d-207">可以通过设置 `MINIMUM_PROBABILITY` 或 `MINIMUM _IMPORTANCE` 参数来控制规则数。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-207">You can control the number of rules by setting the parameters, `MINIMUM_PROBABILITY` or `MINIMUM _IMPORTANCE`.</span></span>  
  
 <span data-ttu-id="6fd9d-208">有关配置高级参数的详细信息，请参阅[&#40;SQL Server 数据挖掘外接程序&#41;的数据挖掘算法](data-mining-algorithms-sql-server-data-mining-add-ins.md)。</span><span class="sxs-lookup"><span data-stu-id="6fd9d-208">For more information about configuring advanced parameters, see [Data Mining Algorithms &#40;SQL Server Data Mining Add-ins&#41;](data-mining-algorithms-sql-server-data-mining-add-ins.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fd9d-209">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6fd9d-209">See Also</span></span>  
 [<span data-ttu-id="6fd9d-210">在 Excel 中浏览模型 &#40;SQL Server 数据挖掘外接程序&#41;</span><span class="sxs-lookup"><span data-stu-id="6fd9d-210">Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
