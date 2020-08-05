---
title: Microsoft 关联算法技术参考 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- MINIMUM_ITEMSET_SIZE parameter
- MAXIMUM_SUPPORT parameter
- association algorithms [Analysis Services]
- MINIMUM_SUPPORT parameter
- OPTIMIZED_PREDICTION_COUNT parameter
- associations [Analysis Services]
- MAXIMUM_ITEMSET_COUNT parameter
- MAXIMUM_ITEMSET_SIZE parameter
- MINIMUM_PROBABILITY parameter
ms.assetid: 50a22202-e936-4995-ae1d-4ff974002e88
author: minewiskan
ms.author: owend
ms.openlocfilehash: eac813711aafc714edef6acc98cda612dd879549
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579860"
---
# <a name="microsoft-association-algorithm-technical-reference"></a><span data-ttu-id="d601b-102">Microsoft 关联算法技术参考</span><span class="sxs-lookup"><span data-stu-id="d601b-102">Microsoft Association Algorithm Technical Reference</span></span>
  <span data-ttu-id="d601b-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 关联规则算法是熟知的 Apriori 算法的简单实现。</span><span class="sxs-lookup"><span data-stu-id="d601b-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules algorithm is a straightforward implementation of the well-known Apriori algorithm.</span></span>  
  
 <span data-ttu-id="d601b-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 决策树算法和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 关联规则算法均可用于分析关联，但每种算法找到的规则可能不同。</span><span class="sxs-lookup"><span data-stu-id="d601b-104">Both the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules algorithm can be used to analyze associations, but the rules that are found by each algorithm can differ.</span></span> <span data-ttu-id="d601b-105">在决策树模型中，导致特定规则的拆分基于信息获取，而在关联模型中，规则完全基于置信度。</span><span class="sxs-lookup"><span data-stu-id="d601b-105">In a decision trees model, the splits that lead to specific rules are based on information gain, whereas in an association model, rules are based completely on confidence.</span></span> <span data-ttu-id="d601b-106">因此，在关联模型中，强规则或具有高置信度的规则由于不提供新信息，可能不一定会受到关注。</span><span class="sxs-lookup"><span data-stu-id="d601b-106">Therefore, in an association model, a strong rule, or one that has high confidence, might not necessarily be interesting because it does not provide new information.</span></span>  
  
## <a name="implementation-of-the-microsoft-association-algorithm"></a><span data-ttu-id="d601b-107">Microsoft 关联算法的实现</span><span class="sxs-lookup"><span data-stu-id="d601b-107">Implementation of the Microsoft Association Algorithm</span></span>  
 <span data-ttu-id="d601b-108">Apriori 算法不分析模式，而是生成“候选项集 \*\*”，然后计算该项集的数目。</span><span class="sxs-lookup"><span data-stu-id="d601b-108">The Apriori algorithm does not analyze patterns, but rather generates and then counts *candidate itemsets*.</span></span> <span data-ttu-id="d601b-109">根据要分析的数据类型，项目可表示事件、产品或属性值。</span><span class="sxs-lookup"><span data-stu-id="d601b-109">An item can represent an event, a product, or the value of an attribute, depending on the type of data that is being analyzed.</span></span>  
  
 <span data-ttu-id="d601b-110">在最常见的关联模型类型布尔变量下，表示将 Yes/No 或 Missing/Existing 值分配给每个属性，如产品名称或事件名称。</span><span class="sxs-lookup"><span data-stu-id="d601b-110">In the most common type of association model Boolean variables, representing a Yes/No or Missing/Existing value, are assigned to each attribute, such as a product or event name.</span></span> <span data-ttu-id="d601b-111">例如，市场篮分析就是关联规则模型的一个示例，它使用布尔变量表示特定产品在客户的购物篮是存在还是不存在。</span><span class="sxs-lookup"><span data-stu-id="d601b-111">A market basket analysis is an example of an association rules model that uses Boolean variables to represent the presence or absence of particular products in a customer's shopping basket.</span></span>  
  
 <span data-ttu-id="d601b-112">然后该算法为每个项集创建表示支持和置信度的分数。</span><span class="sxs-lookup"><span data-stu-id="d601b-112">For each itemset, the algorithm then creates scores that represent support and confidence.</span></span> <span data-ttu-id="d601b-113">这些分数可用于排名以及从项集中获取感兴趣的规则。</span><span class="sxs-lookup"><span data-stu-id="d601b-113">These scores can be used to rank and derive interesting rules from the itemsets.</span></span>  
  
 <span data-ttu-id="d601b-114">也可以为数值属性创建关联模型。</span><span class="sxs-lookup"><span data-stu-id="d601b-114">Association models can also be created for numerical attributes.</span></span> <span data-ttu-id="d601b-115">如果属性是连续的，则可以将数值“ \*\* 离散化”或使用存储桶对其进行分组。</span><span class="sxs-lookup"><span data-stu-id="d601b-115">If the attributes are continuous, the numbers can be *discretized, or* grouped in buckets.</span></span> <span data-ttu-id="d601b-116">然后，即可将离散化值作为布尔值或属性值对来处理。</span><span class="sxs-lookup"><span data-stu-id="d601b-116">The discretized values can then be handled either as Booleans or as attribute-value pairs.</span></span>  
  
### <a name="support-probability-and-importance"></a><span data-ttu-id="d601b-117">支持、概率和重要性</span><span class="sxs-lookup"><span data-stu-id="d601b-117">Support, Probability, and Importance</span></span>  
 <span data-ttu-id="d601b-118">“支持”（有时候将其称为“频率”）表示包含目标项目或项目组合的事例的数目\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d601b-118">*Support*, which issometimes referred to as *frequency*, means the number of cases that contain the targeted item or combination of items.</span></span> <span data-ttu-id="d601b-119">只有至少具有指定支持量的项目才可包含在模型中。</span><span class="sxs-lookup"><span data-stu-id="d601b-119">Only items that have at least the specified amount of support can be included in the model.</span></span>  
  
 <span data-ttu-id="d601b-120">“常用项集”\*\* 指满足以下条件的项目集合：该项目集合所具有的支持超过由 MINIMUM_SUPPORT 参数定义的阈值。</span><span class="sxs-lookup"><span data-stu-id="d601b-120">A *frequent itemset* refers to a collection of items where the combination of items also has support above the threshold defined by the MINIMUM_SUPPORT parameter.</span></span> <span data-ttu-id="d601b-121">例如，如果项集为 {A,B,C} 且 MINIMUM_SUPPORT 值为 10，则每个单个项目 A、B 和 C 必须均可在要包括在模型中的至少 10 个事例中找到，而且项目 {A,B,C} 的组合也必须可在至少 10 个事例中找到。</span><span class="sxs-lookup"><span data-stu-id="d601b-121">For example, if the itemset is {A,B,C} and the MINIMUM_SUPPORT value is 10, each individual item A, B, and C must be found in at least 10 cases to be included in the model, and the combination of items {A,B,C} must also be found in at least 10 cases.</span></span>  
  
 <span data-ttu-id="d601b-122">**注意** 通过指定项集的最大长度（这里长度指项目数目），还可控制挖掘模型中项集的数目。</span><span class="sxs-lookup"><span data-stu-id="d601b-122">**Note** You can also control the number of itemsets in a mining model by specifying the maximum length of an itemset, where length means the number of items.</span></span>  
  
 <span data-ttu-id="d601b-123">默认情况下，对任何特定项目或项集的支持均表示包含该项目或项集的事例的计数。</span><span class="sxs-lookup"><span data-stu-id="d601b-123">By default, the support for any particular item or itemset represents a count of the cases that contain that item or items.</span></span> <span data-ttu-id="d601b-124">不过，还可以将 MINIMUM_SUPPORT 表示为占数据集的总事例的百分比，方法是键入数字作为小于 1 的小数值。</span><span class="sxs-lookup"><span data-stu-id="d601b-124">However, you can also express MINIMUM_SUPPORT as a percentage of the total cases in the data set, by typing the number as a decimal value less than 1.</span></span> <span data-ttu-id="d601b-125">例如，如果指定 MINIMUM_SUPPORT 值为 0.03，就意味着至少有 3% 的数据集总事例必须包含该项目或项集以包含在模型中。</span><span class="sxs-lookup"><span data-stu-id="d601b-125">For example, if you specify a MINIMUM_SUPPORT value of 0.03, it means that at least 3% of the total cases in the data set must contain this item or itemset for inclusion in the model.</span></span> <span data-ttu-id="d601b-126">应当试用模型，以确定是使用计数还是百分比更有意义。</span><span class="sxs-lookup"><span data-stu-id="d601b-126">You should experiment with your model to determine whether using a count or percentage makes more sense.</span></span>  
  
 <span data-ttu-id="d601b-127">恰恰相反，规则的阈值不用计数或百分比表示，而用概率（有时称为“置信度 \*\*”）表示。</span><span class="sxs-lookup"><span data-stu-id="d601b-127">In contrast, the threshold for rules is expressed not as a count or percentage, but as a probability, sometimes referred to as *confidence*.</span></span> <span data-ttu-id="d601b-128">例如，如果项集 {A,B,C} 和项集 {A,B,D} 均出现在 50 个事例中，而项集 {A,B} 出现在另外 50 个事例中，则很明显，{A,B} 不是 {C} 的强预测因子。</span><span class="sxs-lookup"><span data-stu-id="d601b-128">For example, if the itemset {A,B,C} occurs in 50 cases, but the itemset {A,B,D} also occurs in 50 cases, and the itemset {A,B} in another 50 cases, it is obvious that {A,B} is not a strong predictor of {C}.</span></span> <span data-ttu-id="d601b-129">因此，为了将某个特定结果对所有已知结果加权， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 通过将项集 {A,B,C} 支持除以所有相关项集支持来计算单个规则的概率（例如 If {A,B} Then {C}）。</span><span class="sxs-lookup"><span data-stu-id="d601b-129">Therefore, to weight a particular outcomes against all known outcomes, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] calculates the probability of the individual rule (such as If {A,B} Then {C}) by dividing the support for the itemset {A,B,C} by the support for all related itemsets.</span></span>  
  
 <span data-ttu-id="d601b-130">可以通过设置 MINIMUM_PROBABILITY 的值来限制模型生成的规则的数目。</span><span class="sxs-lookup"><span data-stu-id="d601b-130">You can restrict the number of rules that a model produces by setting a value for MINIMUM_PROBABILITY.</span></span>  
  
 <span data-ttu-id="d601b-131">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 为创建的每个规则输出一个指示其“重要性”（也称为“提升”）的分数\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d601b-131">For each rule that is created, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] outputs a score that indicates its *importance*, which is alsoreferred to as *lift*.</span></span> <span data-ttu-id="d601b-132">项集和规则的提升重要性的计算方法不同。</span><span class="sxs-lookup"><span data-stu-id="d601b-132">Lift Importance is calculated differently for itemsets and rules.</span></span>  
  
 <span data-ttu-id="d601b-133">项集重要性的计算方法为项集概率除以项集中各个项的合成概率。</span><span class="sxs-lookup"><span data-stu-id="d601b-133">The importance of an itemset is calculated as the probability of the itemset divided by the compound probability of the individual items in the itemset.</span></span> <span data-ttu-id="d601b-134">例如，如果项集包含 {A,B}， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 首先计算包含此 A 和 B 组合的所有事例的数目，并用此事例数除以事例总数，然后将得到的概率规范化。</span><span class="sxs-lookup"><span data-stu-id="d601b-134">For example, if an itemset contains {A,B}, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] first counts all the cases that contain this combination A and B, and divides that by the total number of cases, and then normalizes the probability.</span></span>  
  
 <span data-ttu-id="d601b-135">规则重要性的计算方法为：在已知规则左侧的情况下，求规则右侧的对数可能性值。</span><span class="sxs-lookup"><span data-stu-id="d601b-135">The importance of a rule is calculated by the log likelihood of the right-hand side of the rule, given the left-hand side of the rule.</span></span> <span data-ttu-id="d601b-136">例如，如果规则为 `If {A} Then {B}`，则 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 计算具有 A 和 B 的事例与具有 B 但不具有 A 的事例之比，然后使用对数刻度将该比率规范化。</span><span class="sxs-lookup"><span data-stu-id="d601b-136">For example, in the rule `If {A} Then {B}`, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] calculates the ratio of cases with A and B over cases with B but without A, and then normalizes that ratio by using a logarithmic scale.</span></span>  
  
### <a name="feature-selection"></a><span data-ttu-id="d601b-137">特征选择</span><span class="sxs-lookup"><span data-stu-id="d601b-137">Feature Selection</span></span>  
 <span data-ttu-id="d601b-138">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 关联规则算法不执行任何一种自动功能选择，</span><span class="sxs-lookup"><span data-stu-id="d601b-138">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules algorithm does not perform any kind of automatic feature selection.</span></span> <span data-ttu-id="d601b-139">而是提供参数来控制其自身使用的数据。</span><span class="sxs-lookup"><span data-stu-id="d601b-139">Instead, the algorithm provides parameters that control the data that is used by the algorithm.</span></span> <span data-ttu-id="d601b-140">上述情况可能包括对每个项集大小的限制，或对将项集添加到模型中所需的最大和最小支持的设置。</span><span class="sxs-lookup"><span data-stu-id="d601b-140">This might include limits on the size of each itemset, or setting the maximum and minimum support required to add an itemset to the model.</span></span>  
  
-   <span data-ttu-id="d601b-141">若要筛选出太常见因而不受关注的项目和事件，请减小 MAXIMUM_SUPPORT 的值以将常见项集从模型中删除。</span><span class="sxs-lookup"><span data-stu-id="d601b-141">To filter out items and events that are too common and therefore uninteresting, decrease the value of MAXIMUM_SUPPORT to remove very frequent itemsets from the model.</span></span>  
  
-   <span data-ttu-id="d601b-142">若要筛选出罕见的项目和项集，请增大 MINIMUM_SUPPORT 的值。</span><span class="sxs-lookup"><span data-stu-id="d601b-142">To filter out items and itemsets that are rare, increase the value of MINIMUM_SUPPORT.</span></span>  
  
-   <span data-ttu-id="d601b-143">若要筛选出规则，请增大 MINIMUM_PROBABILITY 的值。</span><span class="sxs-lookup"><span data-stu-id="d601b-143">To filter out rules, increase the value of MINIMUM_PROBABILITY.</span></span>  
  
## <a name="customizing-the-microsoft-association-rules-algorithm"></a><span data-ttu-id="d601b-144">自定义 Microsoft 关联规则算法</span><span class="sxs-lookup"><span data-stu-id="d601b-144">Customizing the Microsoft Association Rules Algorithm</span></span>  
 <span data-ttu-id="d601b-145">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 关联规则算法支持多个参数，这些参数可以影响生成的挖掘模型的行为、性能和准确性。</span><span class="sxs-lookup"><span data-stu-id="d601b-145">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules algorithm supports several parameters that affect the behavior, performance, and accuracy of the resulting mining model.</span></span>  
  
### <a name="setting-algorithm-parameters"></a><span data-ttu-id="d601b-146">设置算法参数</span><span class="sxs-lookup"><span data-stu-id="d601b-146">Setting Algorithm Parameters</span></span>  
 <span data-ttu-id="d601b-147">在任何时候均可使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中的数据挖掘设计器来更改挖掘模型的参数。</span><span class="sxs-lookup"><span data-stu-id="d601b-147">You can change the parameters for a mining model at any time by using the Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="d601b-148">还可以通过使用 <xref:Microsoft.AnalysisServices.MiningModel.AlgorithmParameters%2A> AMO 中的集合或使用 XMLA 中的[MiningModels 元素 &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/collections/miningmodels-element-assl)以编程方式更改参数。</span><span class="sxs-lookup"><span data-stu-id="d601b-148">You can also change parameters programmatically by using the <xref:Microsoft.AnalysisServices.MiningModel.AlgorithmParameters%2A> collection in AMO, or by using the [MiningModels Element &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/collections/miningmodels-element-assl) in XMLA.</span></span> <span data-ttu-id="d601b-149">下表对各参数进行了说明：</span><span class="sxs-lookup"><span data-stu-id="d601b-149">The following table describes each parameter.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d601b-150">不能使用 DMX 语句更改现有模型中的参数;您必须指定 DMX CREATE MODEL 或 ALTER STRUCTURE .。。创建模型时添加模型。</span><span class="sxs-lookup"><span data-stu-id="d601b-150">You cannot change the parameters in an existing model by using a DMX statement; you must specify the parameters in the DMX CREATE MODEL or ALTER STRUCTURE... ADD MODEL when you create the model.</span></span>  
  
 <span data-ttu-id="d601b-151">*MAXIMUM_ITEMSET_COUNT*</span><span class="sxs-lookup"><span data-stu-id="d601b-151">*MAXIMUM_ITEMSET_COUNT*</span></span>  
 <span data-ttu-id="d601b-152">指定要生成的最大项集数。</span><span class="sxs-lookup"><span data-stu-id="d601b-152">Specifies the maximum number of itemsets to produce.</span></span> <span data-ttu-id="d601b-153">如果不指定任何数目，则使用默认值。</span><span class="sxs-lookup"><span data-stu-id="d601b-153">If no number is specified, the default value is used.</span></span>  
  
 <span data-ttu-id="d601b-154">默认值为 200000。</span><span class="sxs-lookup"><span data-stu-id="d601b-154">The default is 200000.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d601b-155">项集按支持排名。</span><span class="sxs-lookup"><span data-stu-id="d601b-155">Itemsets are ranked by support.</span></span> <span data-ttu-id="d601b-156">对具有相同支持的项集进行的排序是任意的。</span><span class="sxs-lookup"><span data-stu-id="d601b-156">Among itemsets that have the same support, ordering is arbitrary.</span></span>  
  
 <span data-ttu-id="d601b-157">*MAXIMUM_ITEMSET_SIZE*</span><span class="sxs-lookup"><span data-stu-id="d601b-157">*MAXIMUM_ITEMSET_SIZE*</span></span>  
 <span data-ttu-id="d601b-158">指定一个项集中允许的最大项数。</span><span class="sxs-lookup"><span data-stu-id="d601b-158">Specifies the maximum number of items that are allowed in an itemset.</span></span> <span data-ttu-id="d601b-159">将该值设置为 0 将指定对项集的大小没有限制。</span><span class="sxs-lookup"><span data-stu-id="d601b-159">Setting this value to 0 specifies that there is no limit to the size of the itemset.</span></span>  
  
 <span data-ttu-id="d601b-160">默认值为 3。</span><span class="sxs-lookup"><span data-stu-id="d601b-160">The default is 3.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d601b-161">由于该参数达到限制时对模型的处理将停止，因此减小该值可能会减少创建该模型所需的时间。</span><span class="sxs-lookup"><span data-stu-id="d601b-161">Decreasing this value can potentially reduce the time that is required for creating the model, because processing of the model stops when the limit is reached.</span></span>  
  
 <span data-ttu-id="d601b-162">*MAXIMUM_SUPPORT*</span><span class="sxs-lookup"><span data-stu-id="d601b-162">*MAXIMUM_SUPPORT*</span></span>  
 <span data-ttu-id="d601b-163">指定一个项集中包含的支持事例的最大数目。</span><span class="sxs-lookup"><span data-stu-id="d601b-163">Specifies the maximum number of cases that an itemset has for support.</span></span> <span data-ttu-id="d601b-164">该参数可用于消除频繁出现从而可能没有多少意义的项目。</span><span class="sxs-lookup"><span data-stu-id="d601b-164">This parameter can be used to eliminate items that appear frequently and therefore potentially have little meaning.</span></span>  
  
 <span data-ttu-id="d601b-165">如果该值小于 1，则表示事例总计的百分比。</span><span class="sxs-lookup"><span data-stu-id="d601b-165">If this value is less than 1, the value represents a percentage of the total cases.</span></span> <span data-ttu-id="d601b-166">如果该值大于 1，则表示可以包含项集的事例的绝对数。</span><span class="sxs-lookup"><span data-stu-id="d601b-166">Values greater than 1 represent the absolute number of cases that can contain the itemset.</span></span>  
  
 <span data-ttu-id="d601b-167">默认值为 1。</span><span class="sxs-lookup"><span data-stu-id="d601b-167">The default is 1.</span></span>  
  
 <span data-ttu-id="d601b-168">*MINIMUM_ITEMSET_SIZE*</span><span class="sxs-lookup"><span data-stu-id="d601b-168">*MINIMUM_ITEMSET_SIZE*</span></span>  
 <span data-ttu-id="d601b-169">指定一个项集中允许的最小项数。</span><span class="sxs-lookup"><span data-stu-id="d601b-169">Specifies the minimum number of items that are allowed in an itemset.</span></span> <span data-ttu-id="d601b-170">若增大该数值，模型包含的项集可能会减少。</span><span class="sxs-lookup"><span data-stu-id="d601b-170">If you increase this number, the model might contain fewer itemsets.</span></span> <span data-ttu-id="d601b-171">例如，在希望忽略单项目项集时，这会很有帮助。</span><span class="sxs-lookup"><span data-stu-id="d601b-171">This can be useful if you want to ignore single-item itemsets, for example.</span></span>  
  
 <span data-ttu-id="d601b-172">默认值为 1。</span><span class="sxs-lookup"><span data-stu-id="d601b-172">The default is 1.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d601b-173">由于无论如何 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 都必须在处理模型过程中为单个项目计算概率，因而不能通过增大该最小值来减少模型处理时间。</span><span class="sxs-lookup"><span data-stu-id="d601b-173">You cannot reduce model processing time by increasing the minimum value, because [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] must calculate probabilities for single items anyway as part of processing.</span></span> <span data-ttu-id="d601b-174">但通过增大该值，可筛选出较小的项集。</span><span class="sxs-lookup"><span data-stu-id="d601b-174">However, by setting this value higher you can filter out smaller itemsets.</span></span>  
  
 <span data-ttu-id="d601b-175">*MINIMUM_PROBABILITY*</span><span class="sxs-lookup"><span data-stu-id="d601b-175">*MINIMUM_PROBABILITY*</span></span>  
 <span data-ttu-id="d601b-176">指定规则为 True 的最小概率。</span><span class="sxs-lookup"><span data-stu-id="d601b-176">Specifies the minimum probability that a rule is true.</span></span>  
  
 <span data-ttu-id="d601b-177">例如，如果将该值设置为 0.5，这将意味着不生成概率小于百分之五十的规则。</span><span class="sxs-lookup"><span data-stu-id="d601b-177">For example, if you set this value to 0.5, it means that no rule with less than fifty percent probability can be generated.</span></span>  
  
 <span data-ttu-id="d601b-178">默认值为 0.4。</span><span class="sxs-lookup"><span data-stu-id="d601b-178">The default is 0.4.</span></span>  
  
 <span data-ttu-id="d601b-179">*MINIMUM_SUPPORT*</span><span class="sxs-lookup"><span data-stu-id="d601b-179">*MINIMUM_SUPPORT*</span></span>  
 <span data-ttu-id="d601b-180">指定在该算法生成规则之前必须包含项集的事例的最小数目。</span><span class="sxs-lookup"><span data-stu-id="d601b-180">Specifies the minimum number of cases that must contain the itemset before the algorithm generates a rule.</span></span>  
  
 <span data-ttu-id="d601b-181">如果将该值设置为小于 1，则最小事例数的计算方式为占总事例的百分比。</span><span class="sxs-lookup"><span data-stu-id="d601b-181">If you set this value to less than 1, the minimum number of cases is calculated as a percentage of the total cases.</span></span>  
  
 <span data-ttu-id="d601b-182">如果将该值设置为大于 1 的整数，则指定最小事例数的计算方式为必须包含该项集的事例计数。</span><span class="sxs-lookup"><span data-stu-id="d601b-182">If you set this value to a whole number greater than 1, specifies the minimum number of cases is calculated as a count of cases that must contain the itemset.</span></span> <span data-ttu-id="d601b-183">如果内存有限，则该算法可能会自动增大此参数的值。</span><span class="sxs-lookup"><span data-stu-id="d601b-183">The algorithm might automatically increase the value of this parameter if memory is limited.</span></span>  
  
 <span data-ttu-id="d601b-184">默认值为 0.03。</span><span class="sxs-lookup"><span data-stu-id="d601b-184">The default is 0.03.</span></span> <span data-ttu-id="d601b-185">这就意味着若要使某个项集包含在模型中，必须在至少 3% 的事例中可以找到该项集。</span><span class="sxs-lookup"><span data-stu-id="d601b-185">This means that to be included in the model, an itemset must be found in at least 3% of cases.</span></span>  
  
 <span data-ttu-id="d601b-186">*OPTIMIZED_PREDICTION_COUNT*</span><span class="sxs-lookup"><span data-stu-id="d601b-186">*OPTIMIZED_PREDICTION_COUNT*</span></span>  
 <span data-ttu-id="d601b-187">定义为优化预测而需要缓存的项目的数目。</span><span class="sxs-lookup"><span data-stu-id="d601b-187">Defines the number of items to be cached for optimizing prediction.</span></span>  
  
 <span data-ttu-id="d601b-188">默认值为 0。</span><span class="sxs-lookup"><span data-stu-id="d601b-188">The default value is 0.</span></span> <span data-ttu-id="d601b-189">使用默认值时，算法生成的预测与在查询中请求的预测数量相同。</span><span class="sxs-lookup"><span data-stu-id="d601b-189">When the default is used, the algorithm will produce as many predictions as requested in the query.</span></span>  
  
 <span data-ttu-id="d601b-190">如果为 OPTIMIZED_PREDICTION_COUNT 指定非零值，即使你请求了其他预测，预测查询也将最多返回指定项目数\*\*。</span><span class="sxs-lookup"><span data-stu-id="d601b-190">If you specify a nonzero value for *OPTIMIZED_PREDICTION_COUNT,* prediction queries can return at most the specified number of items, even if you request additional predictions.</span></span> <span data-ttu-id="d601b-191">不过，设置值可提高预测性能。</span><span class="sxs-lookup"><span data-stu-id="d601b-191">However, setting a value can improve prediction performance.</span></span>  
  
 <span data-ttu-id="d601b-192">例如，如果将该值设置为 3，算法将仅缓存 3 个项目进行预测。</span><span class="sxs-lookup"><span data-stu-id="d601b-192">For example, if the value is set to 3, the algorithm caches only 3 items for prediction.</span></span> <span data-ttu-id="d601b-193">无法看到与返回的这 3 个项目具有同等可能的其他预测。</span><span class="sxs-lookup"><span data-stu-id="d601b-193">You cannot see additional predictions that might be equally probable to the 3 items that are returned.</span></span>  
  
### <a name="modeling-flags"></a><span data-ttu-id="d601b-194">建模标志</span><span class="sxs-lookup"><span data-stu-id="d601b-194">Modeling Flags</span></span>  
 <span data-ttu-id="d601b-195">支持以下建模标志与 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 关联规则算法配合使用。</span><span class="sxs-lookup"><span data-stu-id="d601b-195">The following modeling flags are supported for use with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules algorithm.</span></span>  
  
 <span data-ttu-id="d601b-196">NOT NULL</span><span class="sxs-lookup"><span data-stu-id="d601b-196">NOT NULL</span></span>  
 <span data-ttu-id="d601b-197">指示该列不能包含 Null。</span><span class="sxs-lookup"><span data-stu-id="d601b-197">Indicates that the column cannot contain a null.</span></span> <span data-ttu-id="d601b-198">在模型定型过程中，如果 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 遇到 Null，将导致错误。</span><span class="sxs-lookup"><span data-stu-id="d601b-198">An error will result if [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] encounters a null during model training.</span></span>  
  
 <span data-ttu-id="d601b-199">适用于挖掘结构列。</span><span class="sxs-lookup"><span data-stu-id="d601b-199">Applies to the mining structure column.</span></span>  
  
 <span data-ttu-id="d601b-200">MODEL_EXISTENCE_ONLY</span><span class="sxs-lookup"><span data-stu-id="d601b-200">MODEL_EXISTENCE_ONLY</span></span>  
 <span data-ttu-id="d601b-201">表示列将被视为具有两个可能状态：`Missing` 和 `Existing`。</span><span class="sxs-lookup"><span data-stu-id="d601b-201">Means that the column will be treated as having two possible states: `Missing` and `Existing`.</span></span> <span data-ttu-id="d601b-202">Null 表示缺失值。</span><span class="sxs-lookup"><span data-stu-id="d601b-202">A null is a missing value.</span></span>  
  
 <span data-ttu-id="d601b-203">适用于挖掘模型列。</span><span class="sxs-lookup"><span data-stu-id="d601b-203">Applies to the mining model column.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d601b-204">要求</span><span class="sxs-lookup"><span data-stu-id="d601b-204">Requirements</span></span>  
 <span data-ttu-id="d601b-205">关联模型必须包含一个键列、多个输入列和单个可预测列。</span><span class="sxs-lookup"><span data-stu-id="d601b-205">An association model must contain a key column, input columns, and a single predictable column.</span></span>  
  
### <a name="input-and-predictable-columns"></a><span data-ttu-id="d601b-206">输入列和可预测列</span><span class="sxs-lookup"><span data-stu-id="d601b-206">Input and Predictable Columns</span></span>  
 <span data-ttu-id="d601b-207">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 关联规则算法支持特定的输入列和可预测列，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="d601b-207">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules algorithm supports the specific input columns and predictable columns that are listed in the following table.</span></span> <span data-ttu-id="d601b-208">有关挖掘模型中内容类型含义的详细信息，请参阅[内容类型（数据挖掘）](content-types-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="d601b-208">For more information about the meaning of content types in a mining model, see [Content Types &#40;Data Mining&#41;](content-types-data-mining.md).</span></span>  
  
|<span data-ttu-id="d601b-209">列</span><span class="sxs-lookup"><span data-stu-id="d601b-209">Column</span></span>|<span data-ttu-id="d601b-210">内容类型</span><span class="sxs-lookup"><span data-stu-id="d601b-210">Content types</span></span>|  
|------------|-------------------|  
|<span data-ttu-id="d601b-211">输入属性</span><span class="sxs-lookup"><span data-stu-id="d601b-211">Input attribute</span></span>|<span data-ttu-id="d601b-212">循环、离散、离散化、键、表和已排序</span><span class="sxs-lookup"><span data-stu-id="d601b-212">Cyclical, Discrete, Discretized, Key, Table, Ordered</span></span>|  
|<span data-ttu-id="d601b-213">可预测属性</span><span class="sxs-lookup"><span data-stu-id="d601b-213">Predictable attribute</span></span>|<span data-ttu-id="d601b-214">Cyclical、Discrete、Discretized、Table 和 Ordered</span><span class="sxs-lookup"><span data-stu-id="d601b-214">Cyclical, Discrete, Discretized, Table, Ordered</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="d601b-215">支持 Cyclical 和 Ordered 内容类型，但算法会将它们视为离散值，不会进行特殊处理。</span><span class="sxs-lookup"><span data-stu-id="d601b-215">Cyclical and Ordered content types are supported, but the algorithm treats them as discrete values and does not perform special processing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d601b-216">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d601b-216">See Also</span></span>  
 <span data-ttu-id="d601b-217">[Microsoft 关联算法](microsoft-association-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="d601b-217">[Microsoft Association Algorithm](microsoft-association-algorithm.md) </span></span>  
 <span data-ttu-id="d601b-218">[关联模型查询示例](association-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="d601b-218">[Association Model Query Examples](association-model-query-examples.md) </span></span>  
 [<span data-ttu-id="d601b-219">关联模型的挖掘模型内容（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="d601b-219">Mining Model Content for Association Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-association-models-analysis-services-data-mining.md)  
  
  
