---
title: 关联模型的挖掘模型内容 (Analysis Services 数据挖掘) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- itemsets [Analysis Services]
- association algorithms [Analysis Services]
- mining model content, association models
- rules [Data Mining]
- associations [Analysis Services]
ms.assetid: d5849bcb-4b8f-4f71-9761-7dc5bb465224
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8904ce155526aee595db19094fd2bad48770e83e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581028"
---
# <a name="mining-model-content-for-association-models-analysis-services---data-mining"></a><span data-ttu-id="78e4e-102">关联模型的挖掘模型内容（Analysis Services – 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="78e4e-102">Mining Model Content for Association Models (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="78e4e-103">本主题讲述使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 关联规则算法的模型特有的挖掘模型内容。</span><span class="sxs-lookup"><span data-stu-id="78e4e-103">This topic describes mining model content that is specific to models that use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules algorithm.</span></span> <span data-ttu-id="78e4e-104">有关与适用于所有模型类型的挖掘模型内容相关的常规术语和统计术语的说明，请参阅 [挖掘模型内容（Analysis Services - 数据挖掘）](mining-model-content-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="78e4e-104">For an explanation of general and statistical terminology related to mining model content that applies to all model types, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
## <a name="understanding-the-structure-of-an-association-model"></a><span data-ttu-id="78e4e-105">了解关联模型的结构</span><span class="sxs-lookup"><span data-stu-id="78e4e-105">Understanding the Structure of an Association Model</span></span>  
 <span data-ttu-id="78e4e-106">关联模型结构非常简单。</span><span class="sxs-lookup"><span data-stu-id="78e4e-106">An association model has a simple structure.</span></span> <span data-ttu-id="78e4e-107">每个模型均具有表示该模型及其元数据的单一父节点，且每个父节点均具有项集和规则的平面列表。</span><span class="sxs-lookup"><span data-stu-id="78e4e-107">Each model has a single parent node that represents the model and its metadata, and each parent node has a flat list of itemsets and rules.</span></span> <span data-ttu-id="78e4e-108">项集和规则不是按树组织的，它们的顺序是项集在先、规则在后，如下面的关系图所示。</span><span class="sxs-lookup"><span data-stu-id="78e4e-108">The itemsets and rules are not organized in trees, they are ordered with itemsets first and rules next as shown in the following diagram.</span></span>  
  
 <span data-ttu-id="78e4e-109">![关联模型的模型内容结构](../media/modelcontentstructure-assoc.gif "关联模型的模型内容结构")</span><span class="sxs-lookup"><span data-stu-id="78e4e-109">![structure of model content for association models](../media/modelcontentstructure-assoc.gif "structure of model content for association models")</span></span>  
  
 <span data-ttu-id="78e4e-110">每个项集均包含在其自己的节点中 (NODE_TYPE = 7)。</span><span class="sxs-lookup"><span data-stu-id="78e4e-110">Each itemset is contained in its own node (NODE_TYPE = 7).</span></span> <span data-ttu-id="78e4e-111">“节点 \*\* ”包含项集定义、含有此项集的事例的数目以及其他信息。</span><span class="sxs-lookup"><span data-stu-id="78e4e-111">The *node* includes the definition of the itemset, the number of cases that contain this itemset, and other information.</span></span>  
  
 <span data-ttu-id="78e4e-112">每个规则也包含在其自己的节点中 (NODE_TYPE = 8)。</span><span class="sxs-lookup"><span data-stu-id="78e4e-112">Each rule is also contained in its own node (NODE_TYPE = 8).</span></span> <span data-ttu-id="78e4e-113">“规则 \*\* ”说明项目关联方式的一般模式。</span><span class="sxs-lookup"><span data-stu-id="78e4e-113">A *rule* describes a general pattern for how items are associated.</span></span> <span data-ttu-id="78e4e-114">规则类似于 IF-THEN 语句。</span><span class="sxs-lookup"><span data-stu-id="78e4e-114">A rule is like an IF-THEN statement.</span></span> <span data-ttu-id="78e4e-115">规则左侧显示的是一个现有条件或条件集。</span><span class="sxs-lookup"><span data-stu-id="78e4e-115">The left-hand side of the rule shows an existing condition or set of conditions.</span></span> <span data-ttu-id="78e4e-116">规则右侧显示的是数据集中的项，该项通常与左侧的条件相关联。</span><span class="sxs-lookup"><span data-stu-id="78e4e-116">The right-hand side of the rule shows the item in your data set that is usually associated with the conditions on the left side.</span></span>  
  
 <span data-ttu-id="78e4e-117">**注意** 如果要提取规则或项集，可使用查询仅返回需要的节点类型。</span><span class="sxs-lookup"><span data-stu-id="78e4e-117">**Note** If you want to extract either the rules or the itemsets, you can use a query to return only the node types that you want.</span></span> <span data-ttu-id="78e4e-118">有关详细信息，请参阅 [关联模型查询示例](association-model-query-examples.md)</span><span class="sxs-lookup"><span data-stu-id="78e4e-118">For more information, see [Association Model Query Examples](association-model-query-examples.md).</span></span>  
  
## <a name="model-content-for-an-association-model"></a><span data-ttu-id="78e4e-119">关联模型的模型内容</span><span class="sxs-lookup"><span data-stu-id="78e4e-119">Model Content for an Association Model</span></span>  
 <span data-ttu-id="78e4e-120">本节仅针对与关联模型相关的挖掘模型内容中的列给出详细信息和示例。</span><span class="sxs-lookup"><span data-stu-id="78e4e-120">This section provides detail and examples only for those columns in the mining model content that are relevant for association models.</span></span>  
  
 <span data-ttu-id="78e4e-121">有关架构行集中通用列（例如 MODEL_CATALOG 和 MODEL_NAME）的信息，请参阅 [挖掘模型内容（Analysis Services - 数据挖掘）](mining-model-content-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="78e4e-121">For information about the general-purpose columns in the schema rowset, such as MODEL_CATALOG and MODEL_NAME, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="78e4e-122">MODEL_CATALOG</span><span class="sxs-lookup"><span data-stu-id="78e4e-122">MODEL_CATALOG</span></span>  
 <span data-ttu-id="78e4e-123">存储模型的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="78e4e-123">Name of the database where the model is stored.</span></span>  
  
 <span data-ttu-id="78e4e-124">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="78e4e-124">MODEL_NAME</span></span>  
 <span data-ttu-id="78e4e-125">模型的名称。</span><span class="sxs-lookup"><span data-stu-id="78e4e-125">Name of the model.</span></span>  
  
 <span data-ttu-id="78e4e-126">ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="78e4e-126">ATTRIBUTE_NAME</span></span>  
 <span data-ttu-id="78e4e-127">与此节点对应的属性的名称。</span><span class="sxs-lookup"><span data-stu-id="78e4e-127">The names of the attributes that correspond to this node.</span></span>  
  
 <span data-ttu-id="78e4e-128">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="78e4e-128">NODE_NAME</span></span>  
 <span data-ttu-id="78e4e-129">节点的名称。</span><span class="sxs-lookup"><span data-stu-id="78e4e-129">The name of the node.</span></span> <span data-ttu-id="78e4e-130">对于关联模型，该列包含的值与 NODE_UNIQUE_NAME 列相同。</span><span class="sxs-lookup"><span data-stu-id="78e4e-130">For an association model, this column contains the same value as NODE_UNIQUE_NAME.</span></span>  
  
 <span data-ttu-id="78e4e-131">NODE_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="78e4e-131">NODE_UNIQUE_NAME</span></span>  
 <span data-ttu-id="78e4e-132">节点的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="78e4e-132">The unique name of the node.</span></span>  
  
 <span data-ttu-id="78e4e-133">NODE_TYPE</span><span class="sxs-lookup"><span data-stu-id="78e4e-133">NODE_TYPE</span></span>  
 <span data-ttu-id="78e4e-134">关联模型仅输出以下节点类型：</span><span class="sxs-lookup"><span data-stu-id="78e4e-134">A association model outputs only the following node types:</span></span>  
  
|<span data-ttu-id="78e4e-135">节点类型 ID</span><span class="sxs-lookup"><span data-stu-id="78e4e-135">Node Type ID</span></span>|<span data-ttu-id="78e4e-136">类型</span><span class="sxs-lookup"><span data-stu-id="78e4e-136">Type</span></span>|  
|------------------|----------|  
|<span data-ttu-id="78e4e-137">1（模型）</span><span class="sxs-lookup"><span data-stu-id="78e4e-137">1 (Model)</span></span>|<span data-ttu-id="78e4e-138">根节点或父节点。</span><span class="sxs-lookup"><span data-stu-id="78e4e-138">Root or parent node.</span></span>|  
|<span data-ttu-id="78e4e-139">7（项集）</span><span class="sxs-lookup"><span data-stu-id="78e4e-139">7 (Itemset)</span></span>|<span data-ttu-id="78e4e-140">项集，或属性-值对的集合。</span><span class="sxs-lookup"><span data-stu-id="78e4e-140">An itemset, or collection of attribute-value pairs.</span></span> <span data-ttu-id="78e4e-141">示例：</span><span class="sxs-lookup"><span data-stu-id="78e4e-141">Examples:</span></span><br /><br /> `Product 1 = Existing, Product 2 = Existing`<br /><br /> <span data-ttu-id="78e4e-142">或</span><span class="sxs-lookup"><span data-stu-id="78e4e-142">or</span></span><br /><br /> <span data-ttu-id="78e4e-143">`Gender = Male`.</span><span class="sxs-lookup"><span data-stu-id="78e4e-143">`Gender = Male`.</span></span>|  
|<span data-ttu-id="78e4e-144">8（规则）</span><span class="sxs-lookup"><span data-stu-id="78e4e-144">8 (Rule)</span></span>|<span data-ttu-id="78e4e-145">用于定义项相互关联的方式的规则。</span><span class="sxs-lookup"><span data-stu-id="78e4e-145">A rule defining how items relate to each other.</span></span><br /><br /> <span data-ttu-id="78e4e-146">示例：</span><span class="sxs-lookup"><span data-stu-id="78e4e-146">Example:</span></span><br /><br /> <span data-ttu-id="78e4e-147">`Product 1 = Existing, Product 2 = Existing -> Product 3 = Existing`.</span><span class="sxs-lookup"><span data-stu-id="78e4e-147">`Product 1 = Existing, Product 2 = Existing -> Product 3 = Existing`.</span></span>|  
  
 <span data-ttu-id="78e4e-148">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="78e4e-148">NODE_CAPTION</span></span>  
 <span data-ttu-id="78e4e-149">与节点关联的标签或标题。</span><span class="sxs-lookup"><span data-stu-id="78e4e-149">A label or a caption associated with the node.</span></span>  
  
 <span data-ttu-id="78e4e-150">**项集节点** 逗号分隔的项列表。</span><span class="sxs-lookup"><span data-stu-id="78e4e-150">**Itemset node** A comma-separated list of items.</span></span>  
  
 <span data-ttu-id="78e4e-151">**规则节点** 包含规则的左右两边。</span><span class="sxs-lookup"><span data-stu-id="78e4e-151">**Rule node** Contains the left and right-hand sides of the rule.</span></span>  
  
 <span data-ttu-id="78e4e-152">CHILDREN_CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="78e4e-152">CHILDREN_CARDINALITY</span></span>  
 <span data-ttu-id="78e4e-153">指示当前节点的子节点的数目。</span><span class="sxs-lookup"><span data-stu-id="78e4e-153">Indicates the number of children of the current node.</span></span>  
  
 <span data-ttu-id="78e4e-154">**父节点** 指示项集与规则数目的总和。</span><span class="sxs-lookup"><span data-stu-id="78e4e-154">**Parent node** Indicates the total number of itemsets plus rules.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="78e4e-155">若要获取对项集和规则计数的明细，请参阅该模型根节点的 NODE_DESCRIPTION。</span><span class="sxs-lookup"><span data-stu-id="78e4e-155">To get a breakdown of the count for itemsets and rules, see the NODE_DESCRIPTION for the root node of the model.</span></span>  
  
 <span data-ttu-id="78e4e-156">**项集或规则节点** 始终为 0。</span><span class="sxs-lookup"><span data-stu-id="78e4e-156">**Itemset or rule node** Always 0.</span></span>  
  
 <span data-ttu-id="78e4e-157">PARENT_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="78e4e-157">PARENT_UNIQUE_NAME</span></span>  
 <span data-ttu-id="78e4e-158">节点的父节点的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="78e4e-158">The unique name of the node's parent.</span></span>  
  
 <span data-ttu-id="78e4e-159">**父节点**始终为 NULL。</span><span class="sxs-lookup"><span data-stu-id="78e4e-159">**Parent node** Always NULL.</span></span>  
  
 <span data-ttu-id="78e4e-160">**项集或规则节点** 始终为 0。</span><span class="sxs-lookup"><span data-stu-id="78e4e-160">**Itemset or rule node** Always 0.</span></span>  
  
 <span data-ttu-id="78e4e-161">NODE_DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="78e4e-161">NODE_DESCRIPTION</span></span>  
 <span data-ttu-id="78e4e-162">节点内容的用户友好说明。</span><span class="sxs-lookup"><span data-stu-id="78e4e-162">A user-friendly description of the contents of the node.</span></span>  
  
 <span data-ttu-id="78e4e-163">**父节点** 包括一个逗号分隔列表，该列表包含有关该模型的以下信息：</span><span class="sxs-lookup"><span data-stu-id="78e4e-163">**Parent node** Includes a comma-separated list of the following information about the model:</span></span>  
  
|<span data-ttu-id="78e4e-164">项</span><span class="sxs-lookup"><span data-stu-id="78e4e-164">Item</span></span>|<span data-ttu-id="78e4e-165">说明</span><span class="sxs-lookup"><span data-stu-id="78e4e-165">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="78e4e-166">ITEMSET_COUNT</span><span class="sxs-lookup"><span data-stu-id="78e4e-166">ITEMSET_COUNT</span></span>|<span data-ttu-id="78e4e-167">模型中所有项集的计数。</span><span class="sxs-lookup"><span data-stu-id="78e4e-167">Count of all itemsets in model.</span></span>|  
|<span data-ttu-id="78e4e-168">RULE_COUNT</span><span class="sxs-lookup"><span data-stu-id="78e4e-168">RULE_COUNT</span></span>|<span data-ttu-id="78e4e-169">模型中所有规则的计数。</span><span class="sxs-lookup"><span data-stu-id="78e4e-169">Count of all rules in model.</span></span>|  
|<span data-ttu-id="78e4e-170">MIN_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="78e4e-170">MIN_SUPPORT</span></span>|<span data-ttu-id="78e4e-171">为任何单个项集找到的最小支持。</span><span class="sxs-lookup"><span data-stu-id="78e4e-171">The minimum support found for any single itemset.</span></span><br /><br /> <span data-ttu-id="78e4e-172">**注意** 值可能不同于为 *MINIMUM _SUPPORT* 参数设置的值。</span><span class="sxs-lookup"><span data-stu-id="78e4e-172">**Note** This value might differ from the value that you set for the *MINIMUM _SUPPORT* parameter.</span></span>|  
|<span data-ttu-id="78e4e-173">MAX_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="78e4e-173">MAX_SUPPORT</span></span>|<span data-ttu-id="78e4e-174">为任何单个项集找到的最大支持。</span><span class="sxs-lookup"><span data-stu-id="78e4e-174">The maximum support found for any single itemset.</span></span><br /><br /> <span data-ttu-id="78e4e-175">**注意** 值可能不同于为 *MAXIMUM_SUPPORT* 参数设置的值。</span><span class="sxs-lookup"><span data-stu-id="78e4e-175">**Note** This value might differ from the value that you set for the *MAXIMUM_SUPPORT* parameter.</span></span>|  
|<span data-ttu-id="78e4e-176">MIN_ITEMSET_SIZE</span><span class="sxs-lookup"><span data-stu-id="78e4e-176">MIN_ITEMSET_SIZE</span></span>|<span data-ttu-id="78e4e-177">最小项集的大小，由项目的计数表示。</span><span class="sxs-lookup"><span data-stu-id="78e4e-177">The size of the smallest itemset, represented as a count of items.</span></span><br /><br /> <span data-ttu-id="78e4e-178">值为 0 指示 `Missing` 状态被视为独立项目。</span><span class="sxs-lookup"><span data-stu-id="78e4e-178">A value of 0 indicates that the `Missing` state was treated as an independent item.</span></span><br /><br /> <span data-ttu-id="78e4e-179">\**注意\*\*\*MINIMUM_ITEMSET_SIZE* 参数的默认值为 1。</span><span class="sxs-lookup"><span data-stu-id="78e4e-179">**Note** The default value of the *MINIMUM_ITEMSET_SIZE* parameter is 1.</span></span>|  
|<span data-ttu-id="78e4e-180">MAX_ITEMSET_SIZE</span><span class="sxs-lookup"><span data-stu-id="78e4e-180">MAX_ITEMSET_SIZE</span></span>|<span data-ttu-id="78e4e-181">指示找到的最大项集的大小。</span><span class="sxs-lookup"><span data-stu-id="78e4e-181">Indicates the size of the largest itemset that was found.</span></span><br /><br /> <span data-ttu-id="78e4e-182">**注意** 此值受创建模型时为 *MAX_ITEMSET_SIZE* 参数设置的值的约束。</span><span class="sxs-lookup"><span data-stu-id="78e4e-182">**Note** This value is constrained by the value that you set for the *MAX_ITEMSET_SIZE* parameter when you created the model.</span></span> <span data-ttu-id="78e4e-183">该值永远不可大于、但可小于为该参数设置的值。</span><span class="sxs-lookup"><span data-stu-id="78e4e-183">This value can never exceed that value; however, it can be less.</span></span> <span data-ttu-id="78e4e-184">默认值为 3。</span><span class="sxs-lookup"><span data-stu-id="78e4e-184">The default value is 3.</span></span>|  
|<span data-ttu-id="78e4e-185">MIN_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="78e4e-185">MIN_PROBABILITY</span></span>|<span data-ttu-id="78e4e-186">为模型中的任何单个项集或规则检测到的最小概率。</span><span class="sxs-lookup"><span data-stu-id="78e4e-186">The minimum probability detected for any single itemset or rule in the model.</span></span><br /><br /> <span data-ttu-id="78e4e-187">示例：0.400390625</span><span class="sxs-lookup"><span data-stu-id="78e4e-187">Example: 0.400390625</span></span><br /><br /> <span data-ttu-id="78e4e-188">**注意** 对于项集，此值始终大于创建模型时为 *MINIMUM_PROBABILITY* 参数设置的值。</span><span class="sxs-lookup"><span data-stu-id="78e4e-188">**Note** For itemsets, this value is always greater than the value that you set for the *MINIMUM_PROBABILITY* parameter when you created the model.</span></span>|  
|<span data-ttu-id="78e4e-189">MAX_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="78e4e-189">MAX_PROBABILITY</span></span>|<span data-ttu-id="78e4e-190">为模型中的任何单个项集或规则检测到的最大概率。</span><span class="sxs-lookup"><span data-stu-id="78e4e-190">The maximum probability detected for any single itemset or rule in the model.</span></span><br /><br /> <span data-ttu-id="78e4e-191">示例：1</span><span class="sxs-lookup"><span data-stu-id="78e4e-191">Example: 1</span></span><br /><br /> <span data-ttu-id="78e4e-192">**注意** 没有参数来约束项集的最大概率。</span><span class="sxs-lookup"><span data-stu-id="78e4e-192">**Note** There is no parameter to constrain maximum probability of itemsets.</span></span> <span data-ttu-id="78e4e-193">若要消除出现过于频繁的项目，请改用 *MAXIMUM_SUPPORT* 参数。</span><span class="sxs-lookup"><span data-stu-id="78e4e-193">If you want to eliminate items that are too frequent, use the *MAXIMUM_SUPPORT* parameter instead.</span></span>|  
|<span data-ttu-id="78e4e-194">MIN_LIFT</span><span class="sxs-lookup"><span data-stu-id="78e4e-194">MIN_LIFT</span></span>|<span data-ttu-id="78e4e-195">该模型为任何项集提供的最小提升量。</span><span class="sxs-lookup"><span data-stu-id="78e4e-195">The minimum amount of lift that is provided by the model for any itemset.</span></span><br /><br /> <span data-ttu-id="78e4e-196">示例：0.14309369632511</span><span class="sxs-lookup"><span data-stu-id="78e4e-196">Example: 0.14309369632511</span></span><br /><br /> <span data-ttu-id="78e4e-197">注意：了解最小提升可帮助你确定对任何一个项集的提升是否有效。</span><span class="sxs-lookup"><span data-stu-id="78e4e-197">Note: Knowing the minimum lift can help you determine whether the lift for any one itemset is significant.</span></span>|  
|<span data-ttu-id="78e4e-198">MAX_LIFT</span><span class="sxs-lookup"><span data-stu-id="78e4e-198">MAX_LIFT</span></span>|<span data-ttu-id="78e4e-199">该模型为每个项集提供的最大提升量。</span><span class="sxs-lookup"><span data-stu-id="78e4e-199">The maximum amount of lift that is provided by the model for any itemset.</span></span><br /><br /> <span data-ttu-id="78e4e-200">示例：1.95758227647523 **注意** 了解最大提升可帮助您确定对任何一个项集的提升是否有效。</span><span class="sxs-lookup"><span data-stu-id="78e4e-200">Example: 1.95758227647523 **Note** Knowing the maximum lift can help you determine whether the lift for any one itemset is significant.</span></span>|  
  
 <span data-ttu-id="78e4e-201">**项集节点** 项集节点包含一个项目列表，该列表显示为一个以逗号分隔的文本字符串。</span><span class="sxs-lookup"><span data-stu-id="78e4e-201">**Itemset node** Itemset nodes contain a list of the items, displayed as a comma-separated text string.</span></span>  
  
 <span data-ttu-id="78e4e-202">示例：</span><span class="sxs-lookup"><span data-stu-id="78e4e-202">Example:</span></span>  
  
 `Touring Tire = Existing, Water Bottle = Existing`  
  
 <span data-ttu-id="78e4e-203">这表示同时购买了旅行车轮胎和水瓶。</span><span class="sxs-lookup"><span data-stu-id="78e4e-203">This means touring tires and water bottles were purchased together.</span></span>  
  
 <span data-ttu-id="78e4e-204">**规则节点** 规则节点包含由箭头分隔的规则的左右两边。</span><span class="sxs-lookup"><span data-stu-id="78e4e-204">**Rule node** Rule nodes contains a left-hand and right-hand side of the rule, separated by an arrow.</span></span>  
  
 <span data-ttu-id="78e4e-205">示例： `Touring Tire = Existing, Water Bottle = Existing -> Cycling cap = Existing`</span><span class="sxs-lookup"><span data-stu-id="78e4e-205">Example: `Touring Tire = Existing, Water Bottle = Existing -> Cycling cap = Existing`</span></span>  
  
 <span data-ttu-id="78e4e-206">这意味着如果某人买了旅行车轮胎和水瓶，他还可能买了自行车运动帽。</span><span class="sxs-lookup"><span data-stu-id="78e4e-206">This means that if someone bought a touring tire and a water bottle, they were also likely to buy a cycling cap.</span></span>  
  
 <span data-ttu-id="78e4e-207">NODE_RULE</span><span class="sxs-lookup"><span data-stu-id="78e4e-207">NODE_RULE</span></span>  
 <span data-ttu-id="78e4e-208">描述节点中嵌套的规则或项集的 XML 片段。</span><span class="sxs-lookup"><span data-stu-id="78e4e-208">An XML fragment that describes the rule or itemset that is embedded in the node.</span></span>  
  
 <span data-ttu-id="78e4e-209">**父节点** 空白。</span><span class="sxs-lookup"><span data-stu-id="78e4e-209">**Parent node** Blank.</span></span>  
  
 <span data-ttu-id="78e4e-210">**项集节点** 空白。</span><span class="sxs-lookup"><span data-stu-id="78e4e-210">**Itemset node** Blank.</span></span>  
  
 <span data-ttu-id="78e4e-211">**规则节点** 包含关于规则的其他有用信息的 XML 片段，这些信息包括支持、置信度、项目数量以及表示规则左侧的节点的 ID 等。</span><span class="sxs-lookup"><span data-stu-id="78e4e-211">**Rule node** The XML fragment includes additional useful information about the rule, such as support, confidence, and the number of items, and the ID of the node that represents the left-hand side of the rule.</span></span>  
  
 <span data-ttu-id="78e4e-212">MARGINAL_RULE</span><span class="sxs-lookup"><span data-stu-id="78e4e-212">MARGINAL_RULE</span></span>  
 <span data-ttu-id="78e4e-213">空白。</span><span class="sxs-lookup"><span data-stu-id="78e4e-213">Blank.</span></span>  
  
 <span data-ttu-id="78e4e-214">NODE_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="78e4e-214">NODE_PROBABILITY</span></span>  
 <span data-ttu-id="78e4e-215">与项集或规则关联的概率或置信度分数。</span><span class="sxs-lookup"><span data-stu-id="78e4e-215">A probability or confidence score associated with the itemset or rule.</span></span>  
  
 <span data-ttu-id="78e4e-216">**父节点** 始终为 0。</span><span class="sxs-lookup"><span data-stu-id="78e4e-216">**Parent node** Always 0.</span></span>  
  
 <span data-ttu-id="78e4e-217">**项集节点** 项集的概率。</span><span class="sxs-lookup"><span data-stu-id="78e4e-217">**Itemset node** Probability of the itemset.</span></span>  
  
 <span data-ttu-id="78e4e-218">**规则节点** 规则的置信度值。</span><span class="sxs-lookup"><span data-stu-id="78e4e-218">**Rule node** Confidence value for the rule.</span></span>  
  
 <span data-ttu-id="78e4e-219">MARGINAL_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="78e4e-219">MARGINAL_PROBABILITY</span></span>  
 <span data-ttu-id="78e4e-220">与 NODE_PROBABILITY 相同。</span><span class="sxs-lookup"><span data-stu-id="78e4e-220">Same as NODE_PROBABILITY.</span></span>  
  
 <span data-ttu-id="78e4e-221">NODE_DISTRIBUTION</span><span class="sxs-lookup"><span data-stu-id="78e4e-221">NODE_DISTRIBUTION</span></span>  
 <span data-ttu-id="78e4e-222">根据节点是项集还是规则，该表包含的信息可能会有很大不同。</span><span class="sxs-lookup"><span data-stu-id="78e4e-222">The table contains very different information, depending on whether the node is an itemset or a rule.</span></span>  
  
 <span data-ttu-id="78e4e-223">**父节点** 空白。</span><span class="sxs-lookup"><span data-stu-id="78e4e-223">**Parent node** Blank.</span></span>  
  
 <span data-ttu-id="78e4e-224">**项集节点** 列出了项集中的每个项目以及概率和支持值。</span><span class="sxs-lookup"><span data-stu-id="78e4e-224">**Itemset node** Lists each item in the itemset together with a probability and support value.</span></span> <span data-ttu-id="78e4e-225">例如，如果项集包含两个产品，则将列出每个产品的名称，同时还会列出包括每个产品的事例的计数。</span><span class="sxs-lookup"><span data-stu-id="78e4e-225">For example, if the itemset contains two products, the name of each product is listed, together with the count of cases that include each product.</span></span>  
  
 <span data-ttu-id="78e4e-226">**规则节点** 包含两行。</span><span class="sxs-lookup"><span data-stu-id="78e4e-226">**Rule node** Contains two rows.</span></span> <span data-ttu-id="78e4e-227">第一行显示规则右侧（预测项目）所具有的属性以及置信度分数。</span><span class="sxs-lookup"><span data-stu-id="78e4e-227">The first row shows the attribute from the right-hand side of the rule, which is the predicted item, together with a confidence score.</span></span>  
  
 <span data-ttu-id="78e4e-228">第二行为关联模型独有，包含一个指向位于规则右侧的项集的指针。</span><span class="sxs-lookup"><span data-stu-id="78e4e-228">The second row is unique to association models; it contains a pointer to the itemset on the right-hand side of the rule.</span></span> <span data-ttu-id="78e4e-229">在 ATTRIBUTE_VALUE 列中，将该指针表示为仅包含右侧项目的项集的 ID。</span><span class="sxs-lookup"><span data-stu-id="78e4e-229">The pointer is represented in the ATTRIBUTE_VALUE column as the ID of the itemset that contains only the right-hand item.</span></span>  
  
 <span data-ttu-id="78e4e-230">例如，如果规则为 `If {A,B} Then {C}`，则该表包含项目 `{C}`的名称，以及含有项目 C 所在项集的节点的 ID。</span><span class="sxs-lookup"><span data-stu-id="78e4e-230">For example, if the rule is `If {A,B} Then {C}`, the table contains the name of the item `{C}`, and the ID of the node that contains the itemset for item C.</span></span>  
  
 <span data-ttu-id="78e4e-231">在根据项集节点确定总共有多少个事例包含右侧产品时，该指针很有用处。</span><span class="sxs-lookup"><span data-stu-id="78e4e-231">This pointer is useful because you can determine from the itemset node how many cases in all include the right-hand side product.</span></span> <span data-ttu-id="78e4e-232">遵循 `If {A,B} Then {C}` 规则的事例是 `{C}`的项集中列出的事例的子集。</span><span class="sxs-lookup"><span data-stu-id="78e4e-232">The cases that are subject to the rule `If {A,B} Then {C}` are a subset of the cases listed in the itemset for `{C}`.</span></span>  
  
 <span data-ttu-id="78e4e-233">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="78e4e-233">NODE_SUPPORT</span></span>  
 <span data-ttu-id="78e4e-234">支持此节点的事例的数目。</span><span class="sxs-lookup"><span data-stu-id="78e4e-234">The number of cases that support this node.</span></span>  
  
 <span data-ttu-id="78e4e-235">**父节点** 模型中的事例数。</span><span class="sxs-lookup"><span data-stu-id="78e4e-235">**Parent node** Number of cases in the model.</span></span>  
  
 <span data-ttu-id="78e4e-236">**项集节点** 包含项集中所有项目的事例的数目。</span><span class="sxs-lookup"><span data-stu-id="78e4e-236">**Itemset node** Number of cases that contains all items in the itemset.</span></span>  
  
 <span data-ttu-id="78e4e-237">**规则节点** 含有规则中包含的所有项目的事例的数目。</span><span class="sxs-lookup"><span data-stu-id="78e4e-237">**Rule node** The number of cases that contain all items included in the rule.</span></span>  
  
 <span data-ttu-id="78e4e-238">MSOLAP_MODEL_COLUMN</span><span class="sxs-lookup"><span data-stu-id="78e4e-238">MSOLAP_MODEL_COLUMN</span></span>  
 <span data-ttu-id="78e4e-239">根据节点是项集还是规则，包含不同的信息。</span><span class="sxs-lookup"><span data-stu-id="78e4e-239">Contains different information depending on whether the node is an itemset or rule.</span></span>  
  
 <span data-ttu-id="78e4e-240">**父节点** 空白。</span><span class="sxs-lookup"><span data-stu-id="78e4e-240">**Parent node** Blank.</span></span>  
  
 <span data-ttu-id="78e4e-241">**项集节点** 空白。</span><span class="sxs-lookup"><span data-stu-id="78e4e-241">**Itemset node** Blank.</span></span>  
  
 <span data-ttu-id="78e4e-242">**规则节点** 包含规则左侧项目的项集的 ID。</span><span class="sxs-lookup"><span data-stu-id="78e4e-242">**Rule node** The ID of the itemset that contains the items in the left-hand side of the rule.</span></span> <span data-ttu-id="78e4e-243">例如，如果规则为 `If {A,B} Then {C}`，则该列包含仅含有 `{A,B}`的项集的 ID。</span><span class="sxs-lookup"><span data-stu-id="78e4e-243">For example, if the rule is `If {A,B} Then {C}`, this column contains the ID of the itemset that contains only `{A,B}`.</span></span>  
  
 <span data-ttu-id="78e4e-244">MSOLAP_NODE_SCORE</span><span class="sxs-lookup"><span data-stu-id="78e4e-244">MSOLAP_NODE_SCORE</span></span>  
 <span data-ttu-id="78e4e-245">**父节点** 空白。</span><span class="sxs-lookup"><span data-stu-id="78e4e-245">**Parent node** Blank.</span></span>  
  
 <span data-ttu-id="78e4e-246">**项集节点** 项集的重要性分数。</span><span class="sxs-lookup"><span data-stu-id="78e4e-246">**Itemset node** Importance score for the itemset.</span></span>  
  
 <span data-ttu-id="78e4e-247">**规则节点** 规则的重要性分数。</span><span class="sxs-lookup"><span data-stu-id="78e4e-247">**Rule node** Importance score for the rule.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="78e4e-248">项集和规则的重要性的计算方法不同。</span><span class="sxs-lookup"><span data-stu-id="78e4e-248">Importance is calculated differently for itemsets and rules.</span></span> <span data-ttu-id="78e4e-249">有关详细信息，请参阅 [Microsoft 关联算法技术参考](microsoft-association-algorithm-technical-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="78e4e-249">For more information, see [Microsoft Association Algorithm Technical Reference](microsoft-association-algorithm-technical-reference.md).</span></span>  
  
 <span data-ttu-id="78e4e-250">MSOLAP_NODE_SHORT_CAPTION</span><span class="sxs-lookup"><span data-stu-id="78e4e-250">MSOLAP_NODE_SHORT_CAPTION</span></span>  
 <span data-ttu-id="78e4e-251">空白。</span><span class="sxs-lookup"><span data-stu-id="78e4e-251">Blank.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78e4e-252">另请参阅</span><span class="sxs-lookup"><span data-stu-id="78e4e-252">See Also</span></span>  
 <span data-ttu-id="78e4e-253">[挖掘模型内容 &#40;Analysis Services 数据挖掘&#41;](mining-model-content-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="78e4e-253">[Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="78e4e-254">[Microsoft 关联算法](microsoft-association-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="78e4e-254">[Microsoft Association Algorithm](microsoft-association-algorithm.md) </span></span>  
 [<span data-ttu-id="78e4e-255">关联模型查询示例</span><span class="sxs-lookup"><span data-stu-id="78e4e-255">Association Model Query Examples</span></span>](association-model-query-examples.md)  
  
  
