---
title: 使用 Microsoft 关联规则查看器浏览模型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- itemsets [Analysis Services]
- mining models [Analysis Services], associations
- mining model content, viewing
- rules [Data Mining]
- Association Rules Viewer [Analysis Services]
- market basket analysis [Analysis Services]
- associations [Analysis Services]
- Microsoft Association Rules Viewer
- dependencies [Analysis Services]
ms.assetid: 538fc01b-8eb1-467a-9b66-3cd57cf7489f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 75bcefde30cb81cc00d8ad971756c68dedf670ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591025"
---
# <a name="browse-a-model-using-the-microsoft-association-rules-viewer"></a><span data-ttu-id="ceb94-102">使用 Microsoft 关联规则查看器浏览模型</span><span class="sxs-lookup"><span data-stu-id="ceb94-102">Browse a Model Using the Microsoft Association Rules Viewer</span></span>
  <span data-ttu-id="ceb94-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)]中的关联规则查看器 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 显示用关联算法生成的挖掘模型 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ceb94-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules Viewer in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] displays mining models that are built with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association algorithm.</span></span> <span data-ttu-id="ceb94-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 关联算法是用于创建可用于市场篮分析的数据挖掘模型的关联算法。</span><span class="sxs-lookup"><span data-stu-id="ceb94-104">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association algorithm is an association algorithm for use in creating data mining models that you can use for market basket analysis.</span></span> <span data-ttu-id="ceb94-105">有关此算法的详细信息，请参阅 [Microsoft Association Algorithm](microsoft-association-algorithm.md)。</span><span class="sxs-lookup"><span data-stu-id="ceb94-105">For more information about this algorithm, see [Microsoft Association Algorithm](microsoft-association-algorithm.md).</span></span>  
  
 <span data-ttu-id="ceb94-106">以下是使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 关联算法的主要原因：</span><span class="sxs-lookup"><span data-stu-id="ceb94-106">Following are the primary reasons for using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association algorithm:</span></span>  
  
-   <span data-ttu-id="ceb94-107">查找对通常能在一个事务中找到的项进行说明的项集。</span><span class="sxs-lookup"><span data-stu-id="ceb94-107">To find itemsets that describe items that are typically found together in a transaction.</span></span>  
  
-   <span data-ttu-id="ceb94-108">发现根据现有项预测事务中存在其他项的规则。</span><span class="sxs-lookup"><span data-stu-id="ceb94-108">To discover rules that predict the presence of other items in a transaction based on existing items.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ceb94-109">若要查看有关模型中使用的公式以及所发现的模式的详细信息，请使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 一般内容树查看器。</span><span class="sxs-lookup"><span data-stu-id="ceb94-109">To view detailed information about the equations used in the model and the patterns that were discovered, use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Generic Content Tree viewer.</span></span> <span data-ttu-id="ceb94-110">有关详细信息，请参阅[使用 Microsoft 一般内容树查看器浏览模型](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)或 [Microsoft 一般内容树查看器（数据挖掘）](../microsoft-generic-content-tree-viewer-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="ceb94-110">For more information, see [Browse a Model Using the Microsoft Generic Content Tree Viewer](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md) or [Microsoft Generic Content Tree Viewer &#40;Data Mining&#41;](../microsoft-generic-content-tree-viewer-data-mining.md).</span></span>  
  
 <span data-ttu-id="ceb94-111">有关如何创建、浏览和使用关联挖掘模型的详细信息，请参阅[第 3 课：生成市场篮方案（数据挖掘中级教程）](../../tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="ceb94-111">For a walkthrough of how to create, explore, and use an association mining model, see [Lesson 3: Building a Market Basket Scenario &#40;Intermediate Data Mining Tutorial&#41;](../../tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md).</span></span>  
  
##  <a name="viewer-tabs"></a><a name="BKMK_ViewerTabs"></a><span data-ttu-id="ceb94-112">查看器选项卡</span><span class="sxs-lookup"><span data-stu-id="ceb94-112">Viewer Tabs</span></span>  
 <span data-ttu-id="ceb94-113">在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]中浏览挖掘模型时，该模型会显示在其相应查看器的数据挖掘设计器的 **“挖掘模型查看器”** 选项卡上。</span><span class="sxs-lookup"><span data-stu-id="ceb94-113">When you browse a mining model in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the model is displayed on the **Mining Model Viewer** tab of Data Mining Designer in the appropriate viewer for the model.</span></span> <span data-ttu-id="ceb94-114">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 关联规则查看器包括以下选项卡：</span><span class="sxs-lookup"><span data-stu-id="ceb94-114">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules Viewer includes the following tabs:</span></span>  
  
-   [<span data-ttu-id="ceb94-115">项集</span><span class="sxs-lookup"><span data-stu-id="ceb94-115">Itemsets</span></span>](#BKMK_Itemsets)  
  
-   [<span data-ttu-id="ceb94-116">规则</span><span class="sxs-lookup"><span data-stu-id="ceb94-116">Rules</span></span>](#BKMK_Rules)  
  
-   [<span data-ttu-id="ceb94-117">依赖关系网络</span><span class="sxs-lookup"><span data-stu-id="ceb94-117">Dependency Net</span></span>](#BKMK_Dependency)  
  
 <span data-ttu-id="ceb94-118">每个选项卡都包含 **“显示长名称”** 复选框，可以使用此复选框来显示或隐藏在规则或项集中所以生成项集的表。</span><span class="sxs-lookup"><span data-stu-id="ceb94-118">Each tab contains the **Show long name** check box, which you can use to show or hide the table from which the itemset originates in the rule or itemset.</span></span>  
  
###  <a name="itemsets"></a><a name="BKMK_Itemsets"></a><span data-ttu-id="ceb94-119">项集</span><span class="sxs-lookup"><span data-stu-id="ceb94-119">Itemsets</span></span>  
 <span data-ttu-id="ceb94-120">**“项集”** 选项卡显示被模型识别为经常发现一起出现的项集的列表。</span><span class="sxs-lookup"><span data-stu-id="ceb94-120">The **Itemsets** tab displays the list of itemsets that the model identified as frequently found together.</span></span> <span data-ttu-id="ceb94-121">该选项卡显示的网格有以下列： **“支持”**、 **“大小”** 和 **“项集”**。</span><span class="sxs-lookup"><span data-stu-id="ceb94-121">The tab displays a grid with the following columns: **Support**, **Size**, and **Itemset**.</span></span> <span data-ttu-id="ceb94-122">有关支持的详细信息，请参阅 [Microsoft Association Algorithm](microsoft-association-algorithm.md)。</span><span class="sxs-lookup"><span data-stu-id="ceb94-122">For more information about support, see [Microsoft Association Algorithm](microsoft-association-algorithm.md).</span></span> <span data-ttu-id="ceb94-123">**“大小”** 列显示项集中的项的数量。</span><span class="sxs-lookup"><span data-stu-id="ceb94-123">The **Size** column displays the number of items in the itemset.</span></span> <span data-ttu-id="ceb94-124">**“项集”** 列显示模型发现的实际项集。</span><span class="sxs-lookup"><span data-stu-id="ceb94-124">The **Itemset** column displays the actual itemset that the model discovered.</span></span> <span data-ttu-id="ceb94-125">可以使用 **“显示”** 列表控制项集的格式，可将格式设置为以下选项：</span><span class="sxs-lookup"><span data-stu-id="ceb94-125">You can control the format of the itemset by using the **Show** list, which you can set to the following options:</span></span>  
  
-   <span data-ttu-id="ceb94-126">**显示属性名称和值**</span><span class="sxs-lookup"><span data-stu-id="ceb94-126">**Show attribute name and value**</span></span>  
  
-   <span data-ttu-id="ceb94-127">**仅显示属性值**</span><span class="sxs-lookup"><span data-stu-id="ceb94-127">**Show attribute value only**</span></span>  
  
-   <span data-ttu-id="ceb94-128">**仅显示属性名称**</span><span class="sxs-lookup"><span data-stu-id="ceb94-128">**Show attribute name only**</span></span>  
  
 <span data-ttu-id="ceb94-129">可以使用 **“最低支持”** 和 **“最小项集大小”** 来筛选选项卡中显示的项集数量。</span><span class="sxs-lookup"><span data-stu-id="ceb94-129">You can filter the number of itemsets that are displayed in the tab by using **Minimum support** and **Minimum itemset size**.</span></span> <span data-ttu-id="ceb94-130">还可使用 **“筛选项集”** 并输入必须存在的项集特征，来进一步限制项集的显示数量。</span><span class="sxs-lookup"><span data-stu-id="ceb94-130">You can limit the number of displayed itemsets even more by using **Filter Itemset** and entering an itemset characteristic that must exist.</span></span> <span data-ttu-id="ceb94-131">例如，如果键入 Water Bottle = existing，则可将项集限制为仅包含 water bottle 的那些项集。</span><span class="sxs-lookup"><span data-stu-id="ceb94-131">For example, if you type "Water Bottle = existing", you can limit the itemsets to only those that contain a water bottle.</span></span> <span data-ttu-id="ceb94-132">**“筛选项集”** 选项还会显示您以前使用过的筛选器列表。</span><span class="sxs-lookup"><span data-stu-id="ceb94-132">The **Filter Itemset** option also displays a list of the filters that you have used previously.</span></span>  
  
 <span data-ttu-id="ceb94-133">通过单击列标题，可以对网格中的行进行排序。</span><span class="sxs-lookup"><span data-stu-id="ceb94-133">You can sort the rows in the grid by clicking a column heading.</span></span>  
  
 [<span data-ttu-id="ceb94-134">返回页首</span><span class="sxs-lookup"><span data-stu-id="ceb94-134">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
###  <a name="rules"></a><a name="BKMK_Rules"></a><span data-ttu-id="ceb94-135">原则</span><span class="sxs-lookup"><span data-stu-id="ceb94-135">Rules</span></span>  
 <span data-ttu-id="ceb94-136">**“规则”** 选项卡显示关联算法发现的规则。</span><span class="sxs-lookup"><span data-stu-id="ceb94-136">The **Rules** tab displays the rules that the association algorithm discovered.</span></span> <span data-ttu-id="ceb94-137">**“规则”** 选项卡包括的网格包含以下列： **“概率”**、 **“重要性”** 和 **“规则”**。</span><span class="sxs-lookup"><span data-stu-id="ceb94-137">The **Rules** tab includes a grid that contains the following columns: **Probability**, **Importance**, and **Rule**.</span></span> <span data-ttu-id="ceb94-138">概率说明出现规则结果的可能性。</span><span class="sxs-lookup"><span data-stu-id="ceb94-138">The probability describes how likely the result of a rule is to occur.</span></span> <span data-ttu-id="ceb94-139">重要性用于度量规则的用途。</span><span class="sxs-lookup"><span data-stu-id="ceb94-139">The importance is designed to measure the usefulness of a rule.</span></span> <span data-ttu-id="ceb94-140">尽管规则出现的概率可能很高，但规则自身的用途可能并不重要。</span><span class="sxs-lookup"><span data-stu-id="ceb94-140">Although the probability that a rule will occur may be high, the usefulness of the rule may in itself be unimportant.</span></span> <span data-ttu-id="ceb94-141">重要性列就是说明这一情况的。</span><span class="sxs-lookup"><span data-stu-id="ceb94-141">The importance column addresses this.</span></span> <span data-ttu-id="ceb94-142">例如，如果每个项集都包含属性的某个特定状态，那么，即使概率非常高，预测状态的规则也并不重要。</span><span class="sxs-lookup"><span data-stu-id="ceb94-142">For example, if every itemset contains a specific state of an attribute, a rule that predicts state is trivial, even though the probability is very high.</span></span> <span data-ttu-id="ceb94-143">重要性越高，规则越重要。</span><span class="sxs-lookup"><span data-stu-id="ceb94-143">The greater the importance, the more important the rule is.</span></span>  
  
 <span data-ttu-id="ceb94-144">你可以使用 "**最小概率**" 和 "**最低重要性**" 来筛选规则，类似于你可以在 "**项集**" 选项卡上执行的筛选。你还可以使用**筛选规则**基于其包含的属性的状态筛选规则。</span><span class="sxs-lookup"><span data-stu-id="ceb94-144">You can use **Minimum probability** and **Minimum importance** to filter the rules, similar to the filtering you can do on the **Itemsets** tab. You can also use **Filter Rule** to filter a rule based on the states of the attributes that it contains.</span></span>  
  
 <span data-ttu-id="ceb94-145">通过单击列标题，可以对网格中的行进行排序。</span><span class="sxs-lookup"><span data-stu-id="ceb94-145">You can sort the rows in the grid by clicking a column heading.</span></span>  
  
 [<span data-ttu-id="ceb94-146">返回页首</span><span class="sxs-lookup"><span data-stu-id="ceb94-146">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
###  <a name="dependency-net"></a><a name="BKMK_Dependency"></a><span data-ttu-id="ceb94-147">依赖关系网络</span><span class="sxs-lookup"><span data-stu-id="ceb94-147">Dependency Net</span></span>  
 <span data-ttu-id="ceb94-148">**“依赖关系网络”** 选项卡包括一个依赖关系网络查看器。</span><span class="sxs-lookup"><span data-stu-id="ceb94-148">The **Dependency Net** tab includes a dependency network viewer.</span></span> <span data-ttu-id="ceb94-149">查看器中的每个节点代表一个项，如 state = WA。</span><span class="sxs-lookup"><span data-stu-id="ceb94-149">Each node in the viewer represents an item, such as "state = WA".</span></span> <span data-ttu-id="ceb94-150">节点间的箭头代表项之间有关联。</span><span class="sxs-lookup"><span data-stu-id="ceb94-150">The arrow between nodes represents the association between items.</span></span> <span data-ttu-id="ceb94-151">箭头的方向表示按照算法发现的规则确定的项之间的关联。</span><span class="sxs-lookup"><span data-stu-id="ceb94-151">The direction of the arrow dictates the association between the items according to the rules that the algorithm discovered.</span></span> <span data-ttu-id="ceb94-152">例如，如果查看器包含三个项 A、B 和 C，并且 C 是由 A 和 B 预测的，则如果选择节点 C，则两个箭头指向节点 C-A 到 C，B 到 C。</span><span class="sxs-lookup"><span data-stu-id="ceb94-152">For example, if the viewer contains three items, A, B, and C, and C is predicted by A and B, if you select node C, two arrows point toward node C - A to C and B to C.</span></span>  
  
 <span data-ttu-id="ceb94-153">查看器左边的滑块可当作与规则的概率关联的筛选器使用。</span><span class="sxs-lookup"><span data-stu-id="ceb94-153">The slider at the left of the viewer acts as a filter that is tied to the probability of the rules.</span></span> <span data-ttu-id="ceb94-154">降低滑块将只显示最强链接。</span><span class="sxs-lookup"><span data-stu-id="ceb94-154">Lowering the slider shows only the strongest links.</span></span>  
  
 [<span data-ttu-id="ceb94-155">返回页首</span><span class="sxs-lookup"><span data-stu-id="ceb94-155">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
## <a name="see-also"></a><span data-ttu-id="ceb94-156">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ceb94-156">See Also</span></span>  
 <span data-ttu-id="ceb94-157">[Microsoft 关联算法](microsoft-association-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="ceb94-157">[Microsoft Association Algorithm](microsoft-association-algorithm.md) </span></span>  
 <span data-ttu-id="ceb94-158">[挖掘模型查看器任务和操作指南](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="ceb94-158">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="ceb94-159">[挖掘模型查看器任务和操作指南](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="ceb94-159">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="ceb94-160">[数据挖掘工具](data-mining-tools.md) </span><span class="sxs-lookup"><span data-stu-id="ceb94-160">[Data Mining Tools](data-mining-tools.md) </span></span>  
 [<span data-ttu-id="ceb94-161">数据挖掘模型查看器</span><span class="sxs-lookup"><span data-stu-id="ceb94-161">Data Mining Model Viewers</span></span>](data-mining-model-viewers.md)  
  
  
