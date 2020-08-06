---
title: 关联模型查询示例 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- itemsets [Analysis Services]
- association algorithms [Analysis Services]
- rules [Data Mining]
- association rules
- content queries [DMX]
ms.assetid: 68b39f5c-c439-44ac-8046-6f2d36649059
author: minewiskan
ms.author: owend
ms.openlocfilehash: a19eb2302639c7f13d48a8778969bbeca4fee18d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590447"
---
# <a name="association-model-query-examples"></a><span data-ttu-id="8f349-102">关联模型查询示例</span><span class="sxs-lookup"><span data-stu-id="8f349-102">Association Model Query Examples</span></span>
  <span data-ttu-id="8f349-103">在对数据挖掘模型创建查询时，可以创建内容查询，也可创建预测查询。内容查询提供有关在分析过程中发现的规则和项集的详细信息，预测查询使用在数据中发现的关联来做出预测。</span><span class="sxs-lookup"><span data-stu-id="8f349-103">When you create a query against a data mining model, you can create either a content query, which provides details about the rules and itemsets discovered during analysis, or you can create a prediction query, which uses the associations discovered in the data to make predictions.</span></span> <span data-ttu-id="8f349-104">对于关联模型来说，预测通常基于规则且可用来给出建议，而内容查询通常用于浏览项集之间的关系。</span><span class="sxs-lookup"><span data-stu-id="8f349-104">For an association model, predictions typically are based on rules, and can be used to make recommendations, whereas queries on content typically explore the relationship among itemsets.</span></span> <span data-ttu-id="8f349-105">此外，还可检索有关模型的元数据。</span><span class="sxs-lookup"><span data-stu-id="8f349-105">You can also retrieve metadata about the model.</span></span>  
  
 <span data-ttu-id="8f349-106">本节讲述如何为基于 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 关联规则的算法的模型创建这些类型的查询。</span><span class="sxs-lookup"><span data-stu-id="8f349-106">This section explains how to create these kinds of queries for models that are based on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules algorithm.</span></span>  
  
 <span data-ttu-id="8f349-107">**内容查询**</span><span class="sxs-lookup"><span data-stu-id="8f349-107">**Content Queries**</span></span>  
  
 [<span data-ttu-id="8f349-108">使用 DMX 获取模型元数据</span><span class="sxs-lookup"><span data-stu-id="8f349-108">Getting model metadata data by using DMX</span></span>](#bkmk_Query1)  
  
 [<span data-ttu-id="8f349-109">从架构行集中获取元数据</span><span class="sxs-lookup"><span data-stu-id="8f349-109">Getting metadata from the schema rowset</span></span>](#bkmk_Query2)  
  
 [<span data-ttu-id="8f349-110">检索模型的原始参数</span><span class="sxs-lookup"><span data-stu-id="8f349-110">Retrieving the original parameters for the model</span></span>](#bkmk_Query3)  
  
 [<span data-ttu-id="8f349-111">检索项集和产品列表</span><span class="sxs-lookup"><span data-stu-id="8f349-111">Retrieving a list of itemsets and products</span></span>](#bkmk_Query4)  
  
 [<span data-ttu-id="8f349-112">返回排在前 10 位的项集</span><span class="sxs-lookup"><span data-stu-id="8f349-112">Returning the top 10 itemsets</span></span>](#bkmk_Query5)  
  
 <span data-ttu-id="8f349-113">**预测查询**</span><span class="sxs-lookup"><span data-stu-id="8f349-113">**Prediction Queries**</span></span>  
  
 [<span data-ttu-id="8f349-114">预测关联项</span><span class="sxs-lookup"><span data-stu-id="8f349-114">Predicting associated items</span></span>](#bkmk_Query6)  
  
 [<span data-ttu-id="8f349-115">确定相关项集的置信度</span><span class="sxs-lookup"><span data-stu-id="8f349-115">Determining confidence for related itemsets</span></span>](#bkmk_Query7)  
  
##  <a name="finding-information-about-the-model"></a><a name="bkmk_top2"></a> <span data-ttu-id="8f349-116">查找有关模型的信息</span><span class="sxs-lookup"><span data-stu-id="8f349-116">Finding Information about the Model</span></span>  
 <span data-ttu-id="8f349-117">所有挖掘模型都公开算法根据标准化架构（即挖掘模型架构行集）所了解的内容。</span><span class="sxs-lookup"><span data-stu-id="8f349-117">All mining models expose the content learned by the algorithm according to a standardized schema, which is named the mining model schema rowset.</span></span> <span data-ttu-id="8f349-118">可以使用建数据挖掘扩展插件 (DMX) 语句或 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 存储过程来对挖掘模型架构行集创建查询。</span><span class="sxs-lookup"><span data-stu-id="8f349-118">You can create queries against the mining model schema rowset either by using Data Mining Extensions (DMX) statements, or by using [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] stored procedures.</span></span> <span data-ttu-id="8f349-119">在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中，还可使用类似 SQL 的语法，直接将架构行集作为系统表来查询。</span><span class="sxs-lookup"><span data-stu-id="8f349-119">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you can also query the schema rowsets directly as system tables, by using a SQL-like syntax.</span></span>  
  
###  <a name="sample-query-1-getting-model-metadata-by-using-dmx"></a><a name="bkmk_Query1"></a> <span data-ttu-id="8f349-120">示例查询 1：使用 DMX 获取模型元数据</span><span class="sxs-lookup"><span data-stu-id="8f349-120">Sample Query 1: Getting Model Metadata by Using DMX</span></span>  
 <span data-ttu-id="8f349-121">以下查询返回有关关联模型 `Association`的基本元数据，例如模型名称、存储模型的数据库以及模型中子节点的数目。</span><span class="sxs-lookup"><span data-stu-id="8f349-121">The following query returns basic metadata about the association model, `Association`, such as the name of the model, the database where the model is stored, and the number of child nodes in the model.</span></span> <span data-ttu-id="8f349-122">此查询使用 DMX 内容查询从模型的父节点中检索元数据：</span><span class="sxs-lookup"><span data-stu-id="8f349-122">This query uses a DMX content query to retrieve the metadata from the parent node of the model:</span></span>  
  
```  
SELECT MODEL_CATALOG, MODEL_NAME, NODE_CAPTION,   
NODE_SUPPORT, [CHILDREN_CARDINALITY], NODE_DESCRIPTION  
FROM Association.CONTENT  
WHERE NODE_TYPE = 1  
```  
  
> [!NOTE]  
>  <span data-ttu-id="8f349-123">必须将列名 CHILDREN_CARDINALITY 括在括号中，以便将它与同名的 MDX 保留关键字区分开来。</span><span class="sxs-lookup"><span data-stu-id="8f349-123">You must enclose the name of the column, CHILDREN_CARDINALITY, in brackets to distinguish it from the MDX reserved keyword of the same name.</span></span>  
  
 <span data-ttu-id="8f349-124">示例结果：</span><span class="sxs-lookup"><span data-stu-id="8f349-124">Example results:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8f349-125">MODEL_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8f349-125">MODEL_CATALOG</span></span>|<span data-ttu-id="8f349-126">Association Test</span><span class="sxs-lookup"><span data-stu-id="8f349-126">Association Test</span></span>|  
|<span data-ttu-id="8f349-127">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="8f349-127">MODEL_NAME</span></span>|<span data-ttu-id="8f349-128">关联</span><span class="sxs-lookup"><span data-stu-id="8f349-128">Association</span></span>|  
|<span data-ttu-id="8f349-129">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="8f349-129">NODE_CAPTION</span></span>|<span data-ttu-id="8f349-130">Association Rules Model</span><span class="sxs-lookup"><span data-stu-id="8f349-130">Association Rules Model</span></span>|  
|<span data-ttu-id="8f349-131">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="8f349-131">NODE_SUPPORT</span></span>|<span data-ttu-id="8f349-132">14879</span><span class="sxs-lookup"><span data-stu-id="8f349-132">14879</span></span>|  
|<span data-ttu-id="8f349-133">CHILDREN_CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="8f349-133">CHILDREN_CARDINALITY</span></span>|<span data-ttu-id="8f349-134">942</span><span class="sxs-lookup"><span data-stu-id="8f349-134">942</span></span>|  
|<span data-ttu-id="8f349-135">NODE_DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8f349-135">NODE_DESCRIPTION</span></span>|<span data-ttu-id="8f349-136">Association Rules Model; ITEMSET_COUNT=679; RULE_COUNT=263; MIN_SUPPORT=14; MAX_SUPPORT=4334; MIN_ITEMSET_SIZE=0; MAX_ITEMSET_SIZE=3; MIN_PROBABILITY=0.400390625; MAX_PROBABILITY=1; MIN_LIFT=0.14309369632511; MAX_LIFT=1.95758227647523</span><span class="sxs-lookup"><span data-stu-id="8f349-136">Association Rules Model; ITEMSET_COUNT=679; RULE_COUNT=263; MIN_SUPPORT=14; MAX_SUPPORT=4334; MIN_ITEMSET_SIZE=0; MAX_ITEMSET_SIZE=3; MIN_PROBABILITY=0.400390625; MAX_PROBABILITY=1; MIN_LIFT=0.14309369632511; MAX_LIFT=1.95758227647523</span></span>|  
  
 <span data-ttu-id="8f349-137">有关这些列在关联模型中含义的定义，请参阅 [关联模型的挖掘模型内容（Analysis Services - 数据挖掘）](mining-model-content-for-association-models-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="8f349-137">For a definition of what these columns mean in an association model, see [Mining Model Content for Association Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-association-models-analysis-services-data-mining.md).</span></span>  
  
 [<span data-ttu-id="8f349-138">返回页首</span><span class="sxs-lookup"><span data-stu-id="8f349-138">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-2-getting-additional-metadata-from-the-schema-rowset"></a><a name="bkmk_Query2"></a> <span data-ttu-id="8f349-139">示例查询 2：从架构行集中获取其他元数据</span><span class="sxs-lookup"><span data-stu-id="8f349-139">Sample Query 2: Getting Additional Metadata from the Schema Rowset</span></span>  
 <span data-ttu-id="8f349-140">通过查询数据挖掘架构行集，可以找到在 DMX 内容查询中返回的相同信息。</span><span class="sxs-lookup"><span data-stu-id="8f349-140">By querying the data mining schema rowset, you can find the same information that is returned in a DMX content query.</span></span> <span data-ttu-id="8f349-141">不过，架构行集还提供其他一些列，例如上次处理模型的日期、挖掘结构和用作可预测属性的列的名称。</span><span class="sxs-lookup"><span data-stu-id="8f349-141">However, the schema rowset provides some additional columns, such as the date the model was last processed, the mining structure, and the name of the column used as the predictable attribute.</span></span>  
  
```  
SELECT MODEL_CATALOG, MODEL_NAME, SERVICE_NAME, PREDICTION_ENTITY,   
MINING_STRUCTURE, LAST_PROCESSED  
FROM $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'Association'  
```  
  
 <span data-ttu-id="8f349-142">示例结果：</span><span class="sxs-lookup"><span data-stu-id="8f349-142">Example results:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8f349-143">MODEL_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8f349-143">MODEL_CATALOG</span></span>|<span data-ttu-id="8f349-144">Adventure Works DW Multidimensional 2012</span><span class="sxs-lookup"><span data-stu-id="8f349-144">Adventure Works DW Multidimensional 2012</span></span>|  
|<span data-ttu-id="8f349-145">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="8f349-145">MODEL_NAME</span></span>|<span data-ttu-id="8f349-146">关联</span><span class="sxs-lookup"><span data-stu-id="8f349-146">Association</span></span>|  
|<span data-ttu-id="8f349-147">SERVICE_NAME</span><span class="sxs-lookup"><span data-stu-id="8f349-147">SERVICE_NAME</span></span>|<span data-ttu-id="8f349-148">Association Rules Model</span><span class="sxs-lookup"><span data-stu-id="8f349-148">Association Rules Model</span></span>|  
|<span data-ttu-id="8f349-149">PREDICTION_ENTITY</span><span class="sxs-lookup"><span data-stu-id="8f349-149">PREDICTION_ENTITY</span></span>|<span data-ttu-id="8f349-150">v Assoc Seq Line Items</span><span class="sxs-lookup"><span data-stu-id="8f349-150">v Assoc Seq Line Items</span></span>|  
|<span data-ttu-id="8f349-151">MINING_STRUCTURE</span><span class="sxs-lookup"><span data-stu-id="8f349-151">MINING_STRUCTURE</span></span>|<span data-ttu-id="8f349-152">关联</span><span class="sxs-lookup"><span data-stu-id="8f349-152">Association</span></span>|  
|<span data-ttu-id="8f349-153">LAST_PROCESSED</span><span class="sxs-lookup"><span data-stu-id="8f349-153">LAST_PROCESSED</span></span>|<span data-ttu-id="8f349-154">9/29/2007 10:21:24 PM</span><span class="sxs-lookup"><span data-stu-id="8f349-154">9/29/2007 10:21:24 PM</span></span>|  
  
 [<span data-ttu-id="8f349-155">返回页首</span><span class="sxs-lookup"><span data-stu-id="8f349-155">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-3-retrieving-original-parameters-for-model"></a><a name="bkmk_Query3"></a> <span data-ttu-id="8f349-156">示例查询 3：检索模型的原始参数</span><span class="sxs-lookup"><span data-stu-id="8f349-156">Sample Query 3: Retrieving Original Parameters for Model</span></span>  
 <span data-ttu-id="8f349-157">以下查询返回一个列，该列包含有关创建模型时使用的参数设置的详细信息。</span><span class="sxs-lookup"><span data-stu-id="8f349-157">The following query returns a single column that contains details about the parameter settings that were used when the model was created.</span></span>  
  
```  
SELECT MINING_PARAMETERS   
from $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'Association'  
```  
  
 <span data-ttu-id="8f349-158">示例结果：</span><span class="sxs-lookup"><span data-stu-id="8f349-158">Example results:</span></span>  
  
 <span data-ttu-id="8f349-159">MAXIMUM_ITEMSET_COUNT=200000,MAXIMUM_ITEMSET_SIZE=3,MAXIMUM_SUPPORT=1,MINIMUM_SUPPORT=9.40923449156529E-04,MINIMUM_IMPORTANCE=-999999999,MINIMUM_ITEMSET_SIZE=0,MINIMUM_PROBABILITY=0.4</span><span class="sxs-lookup"><span data-stu-id="8f349-159">MAXIMUM_ITEMSET_COUNT=200000,MAXIMUM_ITEMSET_SIZE=3,MAXIMUM_SUPPORT=1,MINIMUM_SUPPORT=9.40923449156529E-04,MINIMUM_IMPORTANCE=-999999999,MINIMUM_ITEMSET_SIZE=0,MINIMUM_PROBABILITY=0.4</span></span>  
  
 [<span data-ttu-id="8f349-160">返回页首</span><span class="sxs-lookup"><span data-stu-id="8f349-160">Return to Top</span></span>](#bkmk_top2)  
  
## <a name="finding-information-about-rules-and-itemsets"></a><span data-ttu-id="8f349-161">查找有关规则和项集的信息</span><span class="sxs-lookup"><span data-stu-id="8f349-161">Finding Information about Rules and Itemsets</span></span>  
 <span data-ttu-id="8f349-162">关联模型有两个常见用途：查找有关常见项集的信息以及提取有关特定规则和项集的详细信息。</span><span class="sxs-lookup"><span data-stu-id="8f349-162">There are two common uses of an association model: to discover information about frequent itemsets, and to extract details about particular rules and itemsets.</span></span> <span data-ttu-id="8f349-163">例如，您可能希望提取评为当前特别受关注的规则的列表，或创建最常见项集的列表。</span><span class="sxs-lookup"><span data-stu-id="8f349-163">For example, you might want to extract a list of rules that were scored as being especially interesting, or create a list of the most common itemsets.</span></span> <span data-ttu-id="8f349-164">您可以使用 DMX 内容查询来检索此类信息，</span><span class="sxs-lookup"><span data-stu-id="8f349-164">You retrieve such information by using a DMX content query.</span></span> <span data-ttu-id="8f349-165">也可使用 **“Microsoft 关联查看器”** 浏览该信息。</span><span class="sxs-lookup"><span data-stu-id="8f349-165">You can also browse this information by using the **Microsoft Association Viewer**.</span></span>  
  
###  <a name="sample-query-4-retrieving-list-of-itemsets-and-products"></a><a name="bkmk_Query4"></a> <span data-ttu-id="8f349-166">示例查询 4：检索项集和产品列表</span><span class="sxs-lookup"><span data-stu-id="8f349-166">Sample Query 4: Retrieving List of Itemsets and Products</span></span>  
 <span data-ttu-id="8f349-167">以下查询检索全部项集，同时还将检索列出每个项集中包含的产品的嵌套表。</span><span class="sxs-lookup"><span data-stu-id="8f349-167">The following query retrieves all of the itemsets, together with a nested table that lists the products included in each itemset.</span></span> <span data-ttu-id="8f349-168">NODE_NAME 列包含模型内项集的唯一 ID，而 NODE_CAPTION 给出项目的文本说明。</span><span class="sxs-lookup"><span data-stu-id="8f349-168">The NODE_NAME column contains the unique ID of the itemset within the model, whereas the NODE_CAPTION provides a text description of the items.</span></span> <span data-ttu-id="8f349-169">本例中对嵌套表进行了平展处理，这样，包含两个产品的项集在结果中生成了两行。</span><span class="sxs-lookup"><span data-stu-id="8f349-169">In this example, the nested table is flattened, so that an itemset that contains two products generates two rows in the results.</span></span> <span data-ttu-id="8f349-170">如果客户端支持分层数据，则可以忽略 FLATTENED 关键字。</span><span class="sxs-lookup"><span data-stu-id="8f349-170">You can omit the FLATTENED keyword if your client supports hierarchical data.</span></span>  
  
```  
SELECT FLATTENED NODE_NAME, NODE_CAPTION,  
NODE_PROBABILITY, NODE_SUPPORT,  
(SELECT ATTRIBUTE_NAME FROM NODE_DISTRIBUTION) as PurchasedProducts  
FROM Association.CONTENT  
WHERE NODE_TYPE = 7  
```  
  
 <span data-ttu-id="8f349-171">示例结果：</span><span class="sxs-lookup"><span data-stu-id="8f349-171">Example results:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8f349-172">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="8f349-172">NODE_NAME</span></span>|<span data-ttu-id="8f349-173">37</span><span class="sxs-lookup"><span data-stu-id="8f349-173">37</span></span>|  
|<span data-ttu-id="8f349-174">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="8f349-174">NODE_CAPTION</span></span>|<span data-ttu-id="8f349-175">Sport-100 = Existing</span><span class="sxs-lookup"><span data-stu-id="8f349-175">Sport-100 = Existing</span></span>|  
|<span data-ttu-id="8f349-176">NODE_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="8f349-176">NODE_PROBABILITY</span></span>|<span data-ttu-id="8f349-177">0.291283016331743</span><span class="sxs-lookup"><span data-stu-id="8f349-177">0.291283016331743</span></span>|  
|<span data-ttu-id="8f349-178">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="8f349-178">NODE_SUPPORT</span></span>|<span data-ttu-id="8f349-179">4334</span><span class="sxs-lookup"><span data-stu-id="8f349-179">4334</span></span>|  
|<span data-ttu-id="8f349-180">PURCHASEDPRODUCTS.ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="8f349-180">PURCHASEDPRODUCTS.ATTRIBUTE_NAME</span></span>|<span data-ttu-id="8f349-181">v Assoc Seq Line Items(Sport-100)</span><span class="sxs-lookup"><span data-stu-id="8f349-181">v Assoc Seq Line Items(Sport-100)</span></span>|  
  
 [<span data-ttu-id="8f349-182">返回页首</span><span class="sxs-lookup"><span data-stu-id="8f349-182">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-5-returning-top-10-itemsets"></a><a name="bkmk_Query5"></a> <span data-ttu-id="8f349-183">示例查询 5：返回排在前 10 位的项集</span><span class="sxs-lookup"><span data-stu-id="8f349-183">Sample Query 5: Returning Top 10 Itemsets</span></span>  
 <span data-ttu-id="8f349-184">本例演示如何使用 DMX 在默认情况下提供的某些分组和排序函数。</span><span class="sxs-lookup"><span data-stu-id="8f349-184">This example demonstrates how to use some of the grouping and ordering functions that DMX provides by default.</span></span> <span data-ttu-id="8f349-185">当按照每个节点的支持对项集排序时，该查询返回排在前 10 位的项集。</span><span class="sxs-lookup"><span data-stu-id="8f349-185">The query returns the top 10 itemsets when ordered by the support for each node.</span></span> <span data-ttu-id="8f349-186">请注意，无需对结果进行显式分组，这与 Transact-SQL 中不同。不过，只能在每个查询中使用一个聚合函数。</span><span class="sxs-lookup"><span data-stu-id="8f349-186">Note that you do not need to explicitly group the results, as you would in Transact-SQL; however, you can use only one aggregate function in each query.</span></span>  
  
```  
SELECT TOP 10 (NODE_SUPPORT),NODE_NAME, NODE_CAPTION  
FROM Association.CONTENT  
WHERE NODE_TYPE = 7  
```  
  
 <span data-ttu-id="8f349-187">示例结果：</span><span class="sxs-lookup"><span data-stu-id="8f349-187">Example results:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8f349-188">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="8f349-188">NODE_SUPPORT</span></span>|<span data-ttu-id="8f349-189">4334</span><span class="sxs-lookup"><span data-stu-id="8f349-189">4334</span></span>|  
|<span data-ttu-id="8f349-190">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="8f349-190">NODE_NAME</span></span>|<span data-ttu-id="8f349-191">37</span><span class="sxs-lookup"><span data-stu-id="8f349-191">37</span></span>|  
|<span data-ttu-id="8f349-192">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="8f349-192">NODE_CAPTION</span></span>|<span data-ttu-id="8f349-193">Sport-100 = Existing</span><span class="sxs-lookup"><span data-stu-id="8f349-193">Sport-100 = Existing</span></span>|  
  
 [<span data-ttu-id="8f349-194">返回页首</span><span class="sxs-lookup"><span data-stu-id="8f349-194">Return to Top</span></span>](#bkmk_top2)  
  
## <a name="making-predictions-using-the-model"></a><span data-ttu-id="8f349-195">使用模型进行预测</span><span class="sxs-lookup"><span data-stu-id="8f349-195">Making Predictions using the Model</span></span>  
 <span data-ttu-id="8f349-196">关联规则模型通常用于生成建议，这些建议基于在项集中发现的相关性。</span><span class="sxs-lookup"><span data-stu-id="8f349-196">An association rules model is often used to generate recommendations, which are based on correlations discovered in the itemsets.</span></span> <span data-ttu-id="8f349-197">因此，基于关联规则模型创建预测查询时，您通常使用模型中的规则基于新数据进行猜测。</span><span class="sxs-lookup"><span data-stu-id="8f349-197">Therefore, when you create a prediction query based on an association rules model, you are typically using the rules in the model to make guesses based on new data.</span></span>  <span data-ttu-id="8f349-198">[PredictAssociation (DMX)](/sql/dmx/predictassociation-dmx) 是返回建议的函数，它包含几个可用于自定义查询结果的参数。</span><span class="sxs-lookup"><span data-stu-id="8f349-198">[PredictAssociation &#40;DMX&#41;](/sql/dmx/predictassociation-dmx) is the function that returns recommendations, and has several arguments that you can use to customize the query results.</span></span>  
  
 <span data-ttu-id="8f349-199">另一个说明对关联模型的查询非常有用的示例是返回各种规则和项集的置信度，以便可以比较不同跨区销售策略的有效性。</span><span class="sxs-lookup"><span data-stu-id="8f349-199">Another example of where queries on an association model might be useful is to return the confidence for various rules and itemsets so that you can compare the effectiveness of different cross-sell strategies.</span></span> <span data-ttu-id="8f349-200">以下示例说明如何创建这些查询。</span><span class="sxs-lookup"><span data-stu-id="8f349-200">The following examples illustrate how to create such queries.</span></span>  
  
###  <a name="sample-query-6-predicting-associated-items"></a><a name="bkmk_Query6"></a> <span data-ttu-id="8f349-201">示例查询 6：预测关联项目</span><span class="sxs-lookup"><span data-stu-id="8f349-201">Sample Query 6: Predicting Associated Items</span></span>  
 <span data-ttu-id="8f349-202">此示例使用在[数据挖掘中级教程（Analysis Services - 数据挖掘）](../../tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)中创建的关联模型。</span><span class="sxs-lookup"><span data-stu-id="8f349-202">This example uses the Association model created in the [Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;](../../tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md).</span></span> <span data-ttu-id="8f349-203">它演示如何创建一个预测查询，该查询告诉您应向已购买某种特定产品的客户推荐哪些产品。</span><span class="sxs-lookup"><span data-stu-id="8f349-203">It demonstrates how to create a prediction query that tells you what products to recommend to a customer who has purchased a particular product.</span></span> <span data-ttu-id="8f349-204">此种类型的查询称为单独查询，在该查询中，使用 `SELECT...UNION` 语句向模型提供所需的值。</span><span class="sxs-lookup"><span data-stu-id="8f349-204">This type of query, where you provide values to the model in a `SELECT...UNION` statement, is called a singleton query.</span></span> <span data-ttu-id="8f349-205">由于对应于新值的可预测模型列为嵌套表，因此必须使用一个 `SELECT` 子句将新值映射到嵌套表列 `[Model]`，再使用一个 `SELECT` 子句将嵌套表列映射到事例级别列 `[v Assoc Seq Line Items]`。</span><span class="sxs-lookup"><span data-stu-id="8f349-205">Because the predictable model column that corresponds to the new values is a nested table, you must use one `SELECT` clause to map the new value to the nested table column, `[Model]`, and another `SELECT` clause to map the nested table column to the case-level column, `[v Assoc Seq Line Items]`.</span></span> <span data-ttu-id="8f349-206">如果在该查询中添加 INCLUDE-STATISTICS 关键字，则可看到推荐的概率和支持。</span><span class="sxs-lookup"><span data-stu-id="8f349-206">Adding the keyword INCLUDE-STATISTICS to the query lets you see the probability and support for the recommendations.</span></span>  
  
```  
SELECT PredictAssociation([Association].[vAssocSeqLineItems],INCLUDE_STATISTICS, 3)  
FROM [Association]  
NATURAL PREDICTION JOIN   
(SELECT  
(SELECT 'Classic Vest' as [Model])  
AS [v Assoc Seq Line Items])  
AS t  
```  
  
 <span data-ttu-id="8f349-207">示例结果：</span><span class="sxs-lookup"><span data-stu-id="8f349-207">Example results:</span></span>  
  
|<span data-ttu-id="8f349-208">模型</span><span class="sxs-lookup"><span data-stu-id="8f349-208">Model</span></span>|<span data-ttu-id="8f349-209">$SUPPORT</span><span class="sxs-lookup"><span data-stu-id="8f349-209">$SUPPORT</span></span>|<span data-ttu-id="8f349-210">$PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="8f349-210">$PROBABILITY</span></span>|<span data-ttu-id="8f349-211">$ADJUSTEDPROBABILITY</span><span class="sxs-lookup"><span data-stu-id="8f349-211">$ADJUSTEDPROBABILITY</span></span>|  
|-----------|--------------|------------------|--------------------------|  
|<span data-ttu-id="8f349-212">Sport-100</span><span class="sxs-lookup"><span data-stu-id="8f349-212">Sport-100</span></span>|<span data-ttu-id="8f349-213">4334</span><span class="sxs-lookup"><span data-stu-id="8f349-213">4334</span></span>|<span data-ttu-id="8f349-214">0.291283</span><span class="sxs-lookup"><span data-stu-id="8f349-214">0.291283</span></span>|<span data-ttu-id="8f349-215">0.252696</span><span class="sxs-lookup"><span data-stu-id="8f349-215">0.252696</span></span>|  
|<span data-ttu-id="8f349-216">Water Bottle</span><span class="sxs-lookup"><span data-stu-id="8f349-216">Water Bottle</span></span>|<span data-ttu-id="8f349-217">2866</span><span class="sxs-lookup"><span data-stu-id="8f349-217">2866</span></span>|<span data-ttu-id="8f349-218">0.19262</span><span class="sxs-lookup"><span data-stu-id="8f349-218">0.19262</span></span>|<span data-ttu-id="8f349-219">0.175205</span><span class="sxs-lookup"><span data-stu-id="8f349-219">0.175205</span></span>|  
|<span data-ttu-id="8f349-220">Patch kit</span><span class="sxs-lookup"><span data-stu-id="8f349-220">Patch kit</span></span>|<span data-ttu-id="8f349-221">2113</span><span class="sxs-lookup"><span data-stu-id="8f349-221">2113</span></span>|<span data-ttu-id="8f349-222">0.142012</span><span class="sxs-lookup"><span data-stu-id="8f349-222">0.142012</span></span>|<span data-ttu-id="8f349-223">0.132389</span><span class="sxs-lookup"><span data-stu-id="8f349-223">0.132389</span></span>|  
  
 [<span data-ttu-id="8f349-224">返回页首</span><span class="sxs-lookup"><span data-stu-id="8f349-224">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-7-determining-confidence-for-related-itemsets"></a><a name="bkmk_Query7"></a> <span data-ttu-id="8f349-225">示例查询 7：确定相关项集的置信度</span><span class="sxs-lookup"><span data-stu-id="8f349-225">Sample Query 7: Determining Confidence for Related Itemsets</span></span>  
 <span data-ttu-id="8f349-226">尽管规则可用于生成建议，但在对数据集内的模式的更深入分析中，项集作用更大。</span><span class="sxs-lookup"><span data-stu-id="8f349-226">Whereas rules are useful for generating recommendations, itemsets are more interesting for deeper analysis of the patterns in the data set.</span></span> <span data-ttu-id="8f349-227">例如，如果对前面示例查询返回的建议不满意，则可以检查包含产品 A 的其他项集，以更好地了解是否产品 A 是人们在购买各种产品时倾向于购买的附件，或者是否产品 A 与购买特定产品有很强的关联性。</span><span class="sxs-lookup"><span data-stu-id="8f349-227">For example, if you were not satisfied with the recommendation that are returned by the previous sample query, you could examine other itemsets that contain Product A, to can get a better idea of whether Product A is an accessory that people tend to buy with all kinds of products, or whether A is strongly correlated with purchases of particular products.</span></span> <span data-ttu-id="8f349-228">浏览这些关系的最简单方法是在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 关联查看器中筛选项集，但也可使用查询检索这些信息。</span><span class="sxs-lookup"><span data-stu-id="8f349-228">The easiest way to explore these relationships is by filtering the itemsets in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Viewer; however, you can retrieve the same information with a query.</span></span>  
  
 <span data-ttu-id="8f349-229">以下示例查询返回包含 Water Bottle 项目（包括单项 Water bottle）的所有项集。</span><span class="sxs-lookup"><span data-stu-id="8f349-229">The following sample query returns all itemsets that include the Water Bottle item, including the single item Water bottle.</span></span>  
  
```  
SELECT TOP 100 FROM   
(  
SELECT FLATTENED NODE_CAPTION, NODE_SUPPORT,   
(SELECT ATTRIBUTE_NAME from NODE_DISTRIBUTION  
WHERE ATTRIBUTE_NAME = 'v Assoc Seq Line Items(Water Bottle)') as D  
FROM Association.CONTENT  
WHERE NODE_TYPE = 7  
) AS Items  
WHERE [D.ATTRIBUTE_NAME] <> NULL  
ORDER BY NODE_SUPPORT DESC  
```  
  
 <span data-ttu-id="8f349-230">示例结果：</span><span class="sxs-lookup"><span data-stu-id="8f349-230">Example results:</span></span>  
  
|<span data-ttu-id="8f349-231">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="8f349-231">NODE_CAPTION</span></span>|<span data-ttu-id="8f349-232">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="8f349-232">NODE_SUPPORT</span></span>|<span data-ttu-id="8f349-233">D.ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="8f349-233">D.ATTRIBUTE_NAME</span></span>|  
|-------------------|-------------------|-----------------------|  
|<span data-ttu-id="8f349-234">Water Bottle = Existing</span><span class="sxs-lookup"><span data-stu-id="8f349-234">Water Bottle = Existing</span></span>|<span data-ttu-id="8f349-235">2866</span><span class="sxs-lookup"><span data-stu-id="8f349-235">2866</span></span>|<span data-ttu-id="8f349-236">v Assoc Seq Line Items(Water Bottle)</span><span class="sxs-lookup"><span data-stu-id="8f349-236">v Assoc Seq Line Items(Water Bottle)</span></span>|  
|<span data-ttu-id="8f349-237">Mountain Bottle Cage = Existing, Water Bottle = Existing</span><span class="sxs-lookup"><span data-stu-id="8f349-237">Mountain Bottle Cage = Existing, Water Bottle = Existing</span></span>|<span data-ttu-id="8f349-238">1136</span><span class="sxs-lookup"><span data-stu-id="8f349-238">1136</span></span>|<span data-ttu-id="8f349-239">v Assoc Seq Line Items(Water Bottle)</span><span class="sxs-lookup"><span data-stu-id="8f349-239">v Assoc Seq Line Items(Water Bottle)</span></span>|  
|<span data-ttu-id="8f349-240">Road Bottle Cage = Existing, Water Bottle = Existing</span><span class="sxs-lookup"><span data-stu-id="8f349-240">Road Bottle Cage = Existing, Water Bottle = Existing</span></span>|<span data-ttu-id="8f349-241">1068</span><span class="sxs-lookup"><span data-stu-id="8f349-241">1068</span></span>|<span data-ttu-id="8f349-242">v Assoc Seq Line Items(Water Bottle)</span><span class="sxs-lookup"><span data-stu-id="8f349-242">v Assoc Seq Line Items(Water Bottle)</span></span>|  
|<span data-ttu-id="8f349-243">Water Bottle = Existing, Sport-100 = Existing</span><span class="sxs-lookup"><span data-stu-id="8f349-243">Water Bottle = Existing, Sport-100 = Existing</span></span>|<span data-ttu-id="8f349-244">734</span><span class="sxs-lookup"><span data-stu-id="8f349-244">734</span></span>|<span data-ttu-id="8f349-245">v Assoc Seq Line Items(Water Bottle)</span><span class="sxs-lookup"><span data-stu-id="8f349-245">v Assoc Seq Line Items(Water Bottle)</span></span>|  
  
 <span data-ttu-id="8f349-246">该查询不仅返回嵌套表中符合此条件的行，还返回嵌套表外部或事例表中的所有行。</span><span class="sxs-lookup"><span data-stu-id="8f349-246">This query returns both the rows from the nested table that match the criteria, and all the rows from the outside or case table.</span></span> <span data-ttu-id="8f349-247">因此，必须添加一个条件来消除对目标属性名称具有 Null 值的事例表行。</span><span class="sxs-lookup"><span data-stu-id="8f349-247">Therefore, you must add a condition that eliminates the case table rows that have a null value for the target attribute name.</span></span>  
  
 [<span data-ttu-id="8f349-248">返回页首</span><span class="sxs-lookup"><span data-stu-id="8f349-248">Return to Top</span></span>](#bkmk_top2)  
  
## <a name="function-list"></a><span data-ttu-id="8f349-249">函数列表</span><span class="sxs-lookup"><span data-stu-id="8f349-249">Function List</span></span>  
 <span data-ttu-id="8f349-250">所有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 算法均支持一组通用的函数。</span><span class="sxs-lookup"><span data-stu-id="8f349-250">All [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms support a common set of functions.</span></span> <span data-ttu-id="8f349-251">但 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 关联算法还支持下表中列出的函数。</span><span class="sxs-lookup"><span data-stu-id="8f349-251">However, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association algorithm supports the additional functions listed in the following table.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8f349-252">预测函数</span><span class="sxs-lookup"><span data-stu-id="8f349-252">Prediction Function</span></span>|<span data-ttu-id="8f349-253">使用情况</span><span class="sxs-lookup"><span data-stu-id="8f349-253">Usage</span></span>|  
|[<span data-ttu-id="8f349-254">IsDescendant (DMX)</span><span class="sxs-lookup"><span data-stu-id="8f349-254">IsDescendant &#40;DMX&#41;</span></span>](/sql/dmx/isdescendant-dmx)|<span data-ttu-id="8f349-255">确定一个节点是否是神经网络图中另一个节点的子节点。</span><span class="sxs-lookup"><span data-stu-id="8f349-255">Determines whether one node is a child of another node in the neural network graph.</span></span>|  
|[<span data-ttu-id="8f349-256">IsInNode (DMX)</span><span class="sxs-lookup"><span data-stu-id="8f349-256">IsInNode &#40;DMX&#41;</span></span>](/sql/dmx/isinnode-dmx)|<span data-ttu-id="8f349-257">指示指定的节点是否包含当前事例。</span><span class="sxs-lookup"><span data-stu-id="8f349-257">Indicates whether the specified node contains the current case.</span></span>|  
|[<span data-ttu-id="8f349-258">PredictAdjustedProbability (DMX)</span><span class="sxs-lookup"><span data-stu-id="8f349-258">PredictAdjustedProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictadjustedprobability-dmx)|<span data-ttu-id="8f349-259">返回加权的概率。</span><span class="sxs-lookup"><span data-stu-id="8f349-259">Returns the weighted probability.</span></span>|  
|[<span data-ttu-id="8f349-260">PredictAssociation (DMX)</span><span class="sxs-lookup"><span data-stu-id="8f349-260">PredictAssociation &#40;DMX&#41;</span></span>](/sql/dmx/predictassociation-dmx)|<span data-ttu-id="8f349-261">预测关联数据集中的成员身份。</span><span class="sxs-lookup"><span data-stu-id="8f349-261">Predicts membership in an associative dataset.</span></span>|  
|[<span data-ttu-id="8f349-262">PredictHistogram (DMX)</span><span class="sxs-lookup"><span data-stu-id="8f349-262">PredictHistogram &#40;DMX&#41;</span></span>](/sql/dmx/predicthistogram-dmx)|<span data-ttu-id="8f349-263">返回与当前预测值相关的值的表。</span><span class="sxs-lookup"><span data-stu-id="8f349-263">Returns a table of values related to the current predicted value.</span></span>|  
|[<span data-ttu-id="8f349-264">PredictNodeId (DMX)</span><span class="sxs-lookup"><span data-stu-id="8f349-264">PredictNodeId &#40;DMX&#41;</span></span>](/sql/dmx/predictnodeid-dmx)|<span data-ttu-id="8f349-265">返回每个事例的 Node_ID。</span><span class="sxs-lookup"><span data-stu-id="8f349-265">Returns the Node_ID for each case.</span></span>|  
|[<span data-ttu-id="8f349-266">PredictProbability (DMX)</span><span class="sxs-lookup"><span data-stu-id="8f349-266">PredictProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictprobability-dmx)|<span data-ttu-id="8f349-267">返回预测值的概率。</span><span class="sxs-lookup"><span data-stu-id="8f349-267">Returns probability for the predicted value.</span></span>|  
|[<span data-ttu-id="8f349-268">PredictSupport (DMX)</span><span class="sxs-lookup"><span data-stu-id="8f349-268">PredictSupport &#40;DMX&#41;</span></span>](/sql/dmx/predictsupport-dmx)|<span data-ttu-id="8f349-269">返回指定状态的支持值。</span><span class="sxs-lookup"><span data-stu-id="8f349-269">Returns the support value for a specified state.</span></span>|  
|[<span data-ttu-id="8f349-270">PredictVariance (DMX)</span><span class="sxs-lookup"><span data-stu-id="8f349-270">PredictVariance &#40;DMX&#41;</span></span>](/sql/dmx/predictvariance-dmx)|<span data-ttu-id="8f349-271">返回预测值的方差。</span><span class="sxs-lookup"><span data-stu-id="8f349-271">Returns variance for the predicted value.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8f349-272">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8f349-272">See Also</span></span>  
 <span data-ttu-id="8f349-273">[Microsoft 关联算法](microsoft-association-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="8f349-273">[Microsoft Association Algorithm](microsoft-association-algorithm.md) </span></span>  
 <span data-ttu-id="8f349-274">[Microsoft 关联算法技术参考](microsoft-association-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="8f349-274">[Microsoft Association Algorithm Technical Reference](microsoft-association-algorithm-technical-reference.md) </span></span>  
 [<span data-ttu-id="8f349-275">关联模型的挖掘模型内容（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="8f349-275">Mining Model Content for Association Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-association-models-analysis-services-data-mining.md)  
  
  
