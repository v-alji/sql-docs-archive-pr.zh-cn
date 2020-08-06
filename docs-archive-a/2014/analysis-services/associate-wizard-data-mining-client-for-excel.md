---
title: " (Excel) 的数据挖掘客户端的关联向导 |Microsoft Docs"
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- nested tables, in association models
- association [data mining]
ms.assetid: 4db6462f-93c7-443f-8ff7-39474dc7029e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 73ce4bbedb710de1ded149a12f6f9b83f0b92a11
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579371"
---
# <a name="associate-wizard-data-mining-client-for-excel"></a><span data-ttu-id="ac8a0-102">关联向导（Excel 数据挖掘客户端）</span><span class="sxs-lookup"><span data-stu-id="ac8a0-102">Associate Wizard (Data Mining Client for Excel)</span></span>
  <span data-ttu-id="ac8a0-103">![“数据挖掘”功能区中的关联向导](media/dmc-associate.gif "“数据挖掘”功能区中的关联向导")</span><span class="sxs-lookup"><span data-stu-id="ac8a0-103">![Associate wizard in Data Mining ribbon](media/dmc-associate.gif "Associate wizard in Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="ac8a0-104">关联向导可以帮助您使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] 关联规则算法来创建数据挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-104">The Associate wizard helps you create a data mining model using the [!INCLUDE[msCoName](../includes/msconame-md.md)] Association Rules algorithm.</span></span> <span data-ttu-id="ac8a0-105">此类挖掘模型对于创建*建议系统*特别有用。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-105">Such mining models are particularly useful for creating *recommendation systems*.</span></span>  
  
 <span data-ttu-id="ac8a0-106">其工作方式为 [!INCLUDE[msCoName](../includes/msconame-md.md)] 关联规则算法扫描由事务或事件组成的数据集，然后找到经常一起出现的组合。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-106">How it works is that the [!INCLUDE[msCoName](../includes/msconame-md.md)] Association Rules algorithm scans a dataset comprised of transactions or events, and finds the combinations that frequently appear together.</span></span> <span data-ttu-id="ac8a0-107">可能有数千个组合，但是，可自定义该算法以查找更多或更少以及仅保留最有可能的组合。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-107">There can be many thousand combinations, but the algorithm can be customized to find more or fewer, and to retain only the most probable combinations.</span></span>  
  
 <span data-ttu-id="ac8a0-108">可将关联分析应用于许多问题。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-108">You can apply association analysis to many problems.</span></span> <span data-ttu-id="ac8a0-109">此方法的最常见的应用是购物篮分析，该分析可找到经常一起购买的个别产品。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-109">The most popular application of this method is market basket analysis, which finds individual products that are often purchased together.</span></span> <span data-ttu-id="ac8a0-110">然后，您可以使用这些信息根据客户已经购买的物品向其推荐产品。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-110">You can then use that information to recommend products to customers based on items they have already bought.</span></span>  
  
## <a name="using-the-associate-wizard"></a><span data-ttu-id="ac8a0-111">使用关联向导</span><span class="sxs-lookup"><span data-stu-id="ac8a0-111">Using the Associate Wizard</span></span>  
  
1.  <span data-ttu-id="ac8a0-112">在 "**数据挖掘**" 功能区中，单击 "**关联**"。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-112">In the **Data Mining** ribbon, click **Associate**.</span></span>  
  
2.  <span data-ttu-id="ac8a0-113">在 "**选择源数据**" 页上，选择 Excel 表或数据区域，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-113">On the **Select Source Data** page, choose an Excel table or data range, and click **Next**.</span></span>  
  
     <span data-ttu-id="ac8a0-114">示例数据工作簿的“关联”选项卡中包含一个示例，说明每笔交易中有多个产品或每个客户有多个采购记录时，交易数据通常的排列方式。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-114">The sample data workbook contains an example, in the Associate tab, of how transaction data is typically arranged if, for example, you have multiple products in each transaction or multiple purchasing records per customer that you want to analyze.</span></span>  
  
     <span data-ttu-id="ac8a0-115">如果要使用外部数据来使用关联向导构建关联模型，则必须先将数据添加到 Excel 中，然后再*平展*数据。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-115">If you want to use external data to build an association model using the Associate wizard, you must add the data to Excel first, and *flatten* the data.</span></span> <span data-ttu-id="ac8a0-116">有关为关联建模准备数据的详细信息，请参阅 SQL Server 联机丛书中[&#40;Analysis Services 数据挖掘&#41;的嵌套表](data-mining/nested-tables-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-116">For more information about preparing data for association modeling, see [Nested Tables &#40;Analysis Services - Data Mining&#41;](data-mining/nested-tables-analysis-services-data-mining.md), in SQL Server Books Online.</span></span>  
  
3.  <span data-ttu-id="ac8a0-117">在 "**关联**" 页上，选择用于标识事务的列。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-117">On the **Association** page, choose the column that identifies the transaction.</span></span>  
  
     <span data-ttu-id="ac8a0-118">对于购物篮模型，此标识符表示要建模的单元。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-118">For market basket models, this identifier represents the unit you want to model.</span></span> <span data-ttu-id="ac8a0-119">您是要分析单个客户一段时间内购买的物品，还是要分析涉及多个客户的多宗交易？</span><span class="sxs-lookup"><span data-stu-id="ac8a0-119">Do you want to analyze items that individual customers have purchased over time, or do you want to analyze many transactions involving multiple customers?</span></span> <span data-ttu-id="ac8a0-120">在第一种情况下，您可以选择客户 ID；在后一种情况下，您可以选择采购订单或其他交易 ID。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-120">In the first case, you would choose the customer ID; in the latter you would choose the purchase order or other transaction ID.</span></span>  
  
4.  <span data-ttu-id="ac8a0-121">对于 "项"，请选择包含要在其中查找关联的**项**的列。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-121">For **Item**, select the column that contains the things among which you need to find associations.</span></span>  
  
     <span data-ttu-id="ac8a0-122">例如，在购物篮模型中，您可以选择一个产品字段以分析哪些产品通常会被一起购买。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-122">For example, in a market basket model, you would choose a products field, to analyze which products are often purchased together.</span></span> <span data-ttu-id="ac8a0-123">如果要有效关联在一起的单个产品数量过多，可以选择一个产品类别或子类别字段。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-123">If there are too many individual products to correlate them effectively, you might choose a product category or subcategory field.</span></span>  
  
5.  <span data-ttu-id="ac8a0-124">在 "**阈值**" 中，可以设置控制或影响模型输出的值：</span><span class="sxs-lookup"><span data-stu-id="ac8a0-124">In **Thresholds**, you can set values that control or affect the output of the model:</span></span>  
  
    -   <span data-ttu-id="ac8a0-125">**最低支持。**</span><span class="sxs-lookup"><span data-stu-id="ac8a0-125">**Minimum support.**</span></span> <span data-ttu-id="ac8a0-126">指定一组项目要被视为重要必须达到的出现次数。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-126">Specifies how many times a group of items must appear to be considered important.</span></span> <span data-ttu-id="ac8a0-127">此算法将忽略任何不满足此条件的项组合。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-127">The algorithm will ignore any item combinations that do not meet this criterion.</span></span> <span data-ttu-id="ac8a0-128">例如，您可能希望仅看到整体一起出现至少 10 次的项集。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-128">For example, you might want to see only itemsets where the items appeared together at least 10 times overall.</span></span>  
  
    -   <span data-ttu-id="ac8a0-129">**最小规则概率**。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-129">**Minimum rule probability**.</span></span> <span data-ttu-id="ac8a0-130">指定使规则得以保存所需的最小概率值。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-130">Specifies the minimum probability value required for a rule to be saved.</span></span> <span data-ttu-id="ac8a0-131">分析整个数据集以找出所有组合，然后计算出概率。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-131">The entire data set is analyzed to find all combinations, and then probability is calculated.</span></span> <span data-ttu-id="ac8a0-132">如果该阈值过低，则向导可能会将关联度较低的项关联在一起。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-132">If the threshold is low, the wizard may associate items that are only loosely correlated.</span></span> <span data-ttu-id="ac8a0-133">如果该阈值过高，则某些关联将可能会被忽略，因为它们没有足够的支持数据。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-133">If the threshold is too high, some associations may be omitted because they do not have enough supporting data.</span></span>  
  
     <span data-ttu-id="ac8a0-134">一般来说，更改这些值将产生以下影响：</span><span class="sxs-lookup"><span data-stu-id="ac8a0-134">In general, changing these values has the following effects:</span></span>  
  
    -   <span data-ttu-id="ac8a0-135">如果减小支持的值，则会增加找到的组合数。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-135">As you lower the value for support, you increase the number of combinations that are found.</span></span>  
  
    -   <span data-ttu-id="ac8a0-136">如果减小最大支持，则会筛选出因频繁出现而没有多少意义的项。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-136">As you decrease the maximum support, you filter out items that occur so often that they have little meaning.</span></span>  
  
    -   <span data-ttu-id="ac8a0-137">如果降低规则的概率，则会降低组合在整个数据集上下文中被视为重要组合所必须满足的要求。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-137">As you lower the probability of a rule, you lower the requirements that a combination must meet to be considered important in the context of the total data set.</span></span>  
  
     <span data-ttu-id="ac8a0-138">**提示：** 最好使用支持和概率的不同组合创建多个挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-138">**Tip:** It is a good idea to create multiple mining models using different combinations of support and probability.</span></span> <span data-ttu-id="ac8a0-139">若要跟踪您用于每个模型的设置，您可以使用**文档模型**向导（可在 Excel 数据挖掘客户端中使用），并使用**详细**报告选项。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-139">To track which settings you used for each model, you can use the **Document Model** wizard, available in the Data Mining Client for Excel, and use the **Detailed** report option.</span></span> <span data-ttu-id="ac8a0-140">有关详细信息，请参阅[记录挖掘模型 &#40;Excel 数据挖掘外接程序&#41;](documenting-mining-models-data-mining-add-ins-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-140">For more information, see [Documenting Mining Models &#40;Data Mining Add-ins for Excel&#41;](documenting-mining-models-data-mining-add-ins-for-excel.md).</span></span>  
  
6.  <span data-ttu-id="ac8a0-141">（可选）单击 "**参数**" 更改算法参数，并自定义挖掘模型的行为。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-141">Optionally, click **Parameters** to change the algorithm parameters and customize the behavior of the mining model.</span></span>  
  
     <span data-ttu-id="ac8a0-142">“算法参数”对话框包括您在此向导中设置的所有参数，以及一些不常用到的参数，例如 MAXIMUM_SUPPORT。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-142">The Algorithm Parameters dialog box includes all of the parameters you set in the wizard, plus a few that are less commonly used, such as MAXIMUM_SUPPORT.</span></span> <span data-ttu-id="ac8a0-143">有关如何使用这些参数的详细信息，请参阅[Microsoft 关联算法技术参考](data-mining/microsoft-association-algorithm-technical-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-143">For information about how to use these parameters, see [Microsoft Association Algorithm Technical Reference](data-mining/microsoft-association-algorithm-technical-reference.md).</span></span>  
  
7.  <span data-ttu-id="ac8a0-144">在 "**完成**" 页上，键入数据集和模型的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-144">On the **Finish** page, type a unique name for the data set and the model.</span></span>  
  
8.  <span data-ttu-id="ac8a0-145">在 "**选项**" 中，可以定义在模型完成后如何使用它：</span><span class="sxs-lookup"><span data-stu-id="ac8a0-145">In **Options**, you define how you want to work with the model after it is completed:</span></span>  
  
    -   <span data-ttu-id="ac8a0-146">**浏览**。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-146">**Browse**.</span></span>  <span data-ttu-id="ac8a0-147">在模型准备就绪后，向导将打开一个窗口，该窗口显示规则、项集以及描述关联的依赖关系网络图。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-147">When the model is ready, the wizard opens a window that displays the rules, the itemsets, and a dependency network graph that depicts associations.</span></span>  
  
         <span data-ttu-id="ac8a0-148">有关如何解释关联模型查看器中的数据的详细信息，请参阅[浏览关联规则模型](browsing-an-association-rules-model.md)。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-148">For more information about how to interpret the data in the association model viewer, see [Browsing an Association Rules Model](browsing-an-association-rules-model.md).</span></span>  
  
    -   <span data-ttu-id="ac8a0-149">**启用钻取**。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-149">**Enable drillthrough**.</span></span> <span data-ttu-id="ac8a0-150">选择此选项可以通过模型访问基础数据。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-150">Select this option to gain access to the underlying data, via the model.</span></span>  
  
         <span data-ttu-id="ac8a0-151">例如，在您希望单击特定的项集和查看源数据时，钻取很有用。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-151">Drillthrough is useful, for example, if you want to click on a particular itemset and see the source data.</span></span>  
  
    -   <span data-ttu-id="ac8a0-152">**使用临时模型**。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-152">**Use temporary model**.</span></span> <span data-ttu-id="ac8a0-153">如果您不希望在服务器上保存模型，请选择此选项。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-153">Select this option if you don't want the model saved on the server.</span></span> <span data-ttu-id="ac8a0-154">在您关闭 Excel 时，临时模型将被删除。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-154">Temporary models are deleted when you close Excel.</span></span>  
  
9. <span data-ttu-id="ac8a0-155">该向导分析所有可能存在的组合，然后创建一个报表，其中包含项集和规则。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-155">The wizard analyzes all possible combinations and creates a report that contains the itemsets and rules.</span></span>  
  
## <a name="more-about-association-models"></a><span data-ttu-id="ac8a0-156">有关关联模型的详细信息</span><span class="sxs-lookup"><span data-stu-id="ac8a0-156">More About Association Models</span></span>  
 <span data-ttu-id="ac8a0-157">[!INCLUDE[msCoName](../includes/msconame-md.md)] 关联规则算法可检查定型数据以查找同时出现在某个事务中的项。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-157">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Association Rules algorithm examines the training data to find items that appear together in a transaction.</span></span> <span data-ttu-id="ac8a0-158">每组项*构成一个项*集。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-158">Each group of items constitutes an *itemset*.</span></span> <span data-ttu-id="ac8a0-159">然后，该算法计算每个项集的出现次数，并计算每个项集在所有事务中的相对重要性。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-159">The algorithm then counts the number of times each itemset appears and calculates the relative importance of each itemset across all transactions.</span></span>  
  
 <span data-ttu-id="ac8a0-160">该算法将使用项集的此信息来生成可用于预测关联或提出建议的规则。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-160">The algorithm uses this information about itemsets to generate rules that can be used to predict associations or make recommendations.</span></span> <span data-ttu-id="ac8a0-161">例如，规则可能为“如果用户购买了作者 1 和作者 2 的书各一本，则该用户可能还将购买一本作者 3 的书”。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-161">For example, a rule could be "if the user purchased a book by Author 1 and a book by Author 2, then it is likely that the user will also purchase a book by Author 3".</span></span> <span data-ttu-id="ac8a0-162">会根据关联的程度为每个建议指定一个概率。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-162">Each recommendation is assigned a probability, based on the strength of the associations.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="ac8a0-163">要求</span><span class="sxs-lookup"><span data-stu-id="ac8a0-163">Requirements</span></span>  
 <span data-ttu-id="ac8a0-164">若要使用关联向导，必须连接到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-164">To use the Associate wizard, you must be connected to a [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="ac8a0-165">源数据必须组织为一个事务表。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-165">Your source data must be organized as a transaction table.</span></span> <span data-ttu-id="ac8a0-166">源数据必须包括含有事务标识符的一列。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-166">The source data must contain one column that contains the transaction identifier.</span></span> <span data-ttu-id="ac8a0-167">此列标识各组项。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-167">This column identifies each group of items.</span></span> <span data-ttu-id="ac8a0-168">该事务列与另一列（项 ID）必须为一对多关系，项 ID 列存储组中各项的名称或 ID 号。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-168">That transaction column must be in a one-to-many relationship with a second column, the item ID, which stores names or ID numbers for the individual items in the group.</span></span>  
  
 <span data-ttu-id="ac8a0-169">从概念上讲，试想购物车的例子可能最易于帮助理解。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-169">Conceptually, this might be easiest to understand by recalling the shopping cart example.</span></span> <span data-ttu-id="ac8a0-170">如果为购物车分配一个 ID，则购物车 ID 将作为交易（事务）的标识符。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-170">If the shopping cart is assigned an ID, the shopping cart ID serves as the identifier for the transaction.</span></span> <span data-ttu-id="ac8a0-171">购物车中的每件物品（如土豆或牛奶）都是该交易的组成部分。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-171">Each item in the shopping cart, such as potatoes or milk, is a member of that transaction.</span></span> <span data-ttu-id="ac8a0-172">关联算法可以跨事务跟踪项，例如，确定土豆和牛奶在任何单一交易中出现的次数。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-172">The Associate algorithm can track items across transactions: for example, to determine how many times potatoes and milk appear within any single transaction.</span></span>  
  
 <span data-ttu-id="ac8a0-173">源数据必须按事务标识符列排序。</span><span class="sxs-lookup"><span data-stu-id="ac8a0-173">Your source data must be sorted by the transaction identifier column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac8a0-174">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ac8a0-174">See Also</span></span>  
 <span data-ttu-id="ac8a0-175">[创建数据挖掘模型](creating-a-data-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="ac8a0-175">[Creating a Data Mining Model](creating-a-data-mining-model.md) </span></span>  
 <span data-ttu-id="ac8a0-176">[浏览关联规则模型](browsing-an-association-rules-model.md) </span><span class="sxs-lookup"><span data-stu-id="ac8a0-176">[Browsing an Association Rules Model](browsing-an-association-rules-model.md) </span></span>  
 <span data-ttu-id="ac8a0-177">[用于 Excel&#41;&#40;表 AnalysisTools 的购物篮分析](shopping-basket-analysis-table-analysistools-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="ac8a0-177">[Shopping Basket Analysis &#40;Table AnalysisTools for Excel&#41;](shopping-basket-analysis-table-analysistools-for-excel.md) </span></span>  
 [<span data-ttu-id="ac8a0-178">依赖关系网络关系图演练 &#40;数据挖掘外接程序&#41;</span><span class="sxs-lookup"><span data-stu-id="ac8a0-178">Dependency Network Diagram Walkthrough &#40;Data Mining Add-ins&#41;</span></span>](dependency-network-diagram-walkthrough-data-mining-add-ins.md)  
  
  
