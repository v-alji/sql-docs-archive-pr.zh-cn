---
title: " (数据挖掘) 的内容查询 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: c4f4a5a8-a230-4222-bece-9d563501f65f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 44b162c34f5f505462a713205d8434484473afa4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591662"
---
# <a name="content-queries-data-mining"></a><span data-ttu-id="36096-102">内容查询（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="36096-102">Content Queries (Data Mining)</span></span>
  <span data-ttu-id="36096-103">内容查询是一种提取有关内部统计信息以及挖掘模型结构信息的一种方式。</span><span class="sxs-lookup"><span data-stu-id="36096-103">A content query is a way of extracting information about the internal statistics and structure of the mining model.</span></span> <span data-ttu-id="36096-104">有时，内容查询可提供在查看器中不易查看的详细信息。</span><span class="sxs-lookup"><span data-stu-id="36096-104">Sometimes a content query can provide details that are not readily available in the viewer.</span></span> <span data-ttu-id="36096-105">您还可以使用内容查询的结果以编程方式提取信息以供他用。</span><span class="sxs-lookup"><span data-stu-id="36096-105">You can also use the results of a content query to extract information programmatically for other uses.</span></span>  
  
 <span data-ttu-id="36096-106">本节提供有关可以使用内容查询检索的信息类型的常规信息，以及用于内容查询的一般 DMX 语法。</span><span class="sxs-lookup"><span data-stu-id="36096-106">This section provides general information about the types of information that you can retrieve by using a content query, and the general DMX syntax for content queries.</span></span>  
  
 [<span data-ttu-id="36096-107">基本内容查询</span><span class="sxs-lookup"><span data-stu-id="36096-107">Basic Content Queries</span></span>](#bkmk_ContentQuery)  
  
-   [<span data-ttu-id="36096-108">针对结构和事例数据的查询</span><span class="sxs-lookup"><span data-stu-id="36096-108">Queries on Structure and Case Data</span></span>](#bkmk_Structure)  
  
-   [<span data-ttu-id="36096-109">针对模型模式的查询</span><span class="sxs-lookup"><span data-stu-id="36096-109">Queries on Model Patterns</span></span>](#bkmk_Patterns)  
  
 [<span data-ttu-id="36096-110">示例</span><span class="sxs-lookup"><span data-stu-id="36096-110">Examples</span></span>](#bkmk_Examples)  
  
-   [<span data-ttu-id="36096-111">针对关联模型的内容查询</span><span class="sxs-lookup"><span data-stu-id="36096-111">Content Query on an Association Model</span></span>](#bkmk_Assoc)  
  
-   [<span data-ttu-id="36096-112">针对决策树模型的内容查询</span><span class="sxs-lookup"><span data-stu-id="36096-112">Content Query on a Decision Trees Model</span></span>](#bkmk_DecTree)  
  
 [<span data-ttu-id="36096-113">使用查询结果</span><span class="sxs-lookup"><span data-stu-id="36096-113">Working with the Query Results</span></span>](#bkmk_Results)  
  
##  <a name="basic-content-queries"></a><a name="bkmk_ContentQuery"></a> <span data-ttu-id="36096-114">基本内容查询</span><span class="sxs-lookup"><span data-stu-id="36096-114">Basic Content Queries</span></span>  
 <span data-ttu-id="36096-115">您可以通过使用预测查询生成器来创建内容查询，使用在 SQL Server Management Studio 中提供的 DMX 内容查询模板，或者直接在 DMX 中撰写查询。</span><span class="sxs-lookup"><span data-stu-id="36096-115">You can create content queries by using the Prediction Query Builder, use the DMX content query templates that are provided in SQL Server Management Studio, or write queries directly in DMX.</span></span> <span data-ttu-id="36096-116">与预测查询不同，您无需联接外部数据，因此内容查询易于撰写。</span><span class="sxs-lookup"><span data-stu-id="36096-116">Unlike prediction queries you do not need to join external data, so content queries are easy to write.</span></span>  
  
 <span data-ttu-id="36096-117">本节概述了您可以创建的内容查询类型。</span><span class="sxs-lookup"><span data-stu-id="36096-117">This section provides an overview of the types of content queries you can create.</span></span>  
  
-   <span data-ttu-id="36096-118">通过针对挖掘结构或事例数据的查询，您可以查看用于定型的详细数据。</span><span class="sxs-lookup"><span data-stu-id="36096-118">Queries on the mining structure or case data let you view the detailed data that was used for training.</span></span>  
  
-   <span data-ttu-id="36096-119">针对模型的查询可以返回模式、属性列表、公式等等。</span><span class="sxs-lookup"><span data-stu-id="36096-119">Queries on the model can return patterns, lists of attributes, formulas, and so forth.</span></span>  
  
###  <a name="queries-on-structure-and-case-data"></a><a name="bkmk_Structure"></a> <span data-ttu-id="36096-120">针对结构和事例数据的查询</span><span class="sxs-lookup"><span data-stu-id="36096-120">Queries on Structure and Case Data</span></span>  
 <span data-ttu-id="36096-121">DMX 支持对用于生成挖掘结构和模型的缓存数据进行查询。</span><span class="sxs-lookup"><span data-stu-id="36096-121">DMX supports queries on the cached data that is used to build mining structures and models.</span></span> <span data-ttu-id="36096-122">默认情况下，在您定义挖掘结构时将创建此缓存，并且在您处理该结构或模型时填充此缓存。</span><span class="sxs-lookup"><span data-stu-id="36096-122">By default, this cache is created when you define the mining structure, and is populated when you process the structure or model.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="36096-123">如果您需要将数据拆分为定型集和测试集，则不能清除或删除此缓存。</span><span class="sxs-lookup"><span data-stu-id="36096-123">This cache cannot be cleared or deleted if you need to separate data into training and testing sets.</span></span> <span data-ttu-id="36096-124">如果清除了缓存，则您无法查询事例数据。</span><span class="sxs-lookup"><span data-stu-id="36096-124">If the cache is cleared, you cannot query the case data.</span></span>  
  
 <span data-ttu-id="36096-125">以下示例演示了用于创建针对事例数据或挖掘结构中数据的查询的常用模式：</span><span class="sxs-lookup"><span data-stu-id="36096-125">The following examples show the common patterns for creating queries on the case data, or queries on the data in the mining structure:</span></span>  
  
 <span data-ttu-id="36096-126">**获取模型的所有事例**</span><span class="sxs-lookup"><span data-stu-id="36096-126">**Get all the cases for a model**</span></span>  
 `SELECT FROM <model>.CASES`  
  
 <span data-ttu-id="36096-127">使用此语句可以从用于生成模型的事例数据中检索指定列。</span><span class="sxs-lookup"><span data-stu-id="36096-127">Use this statement to retrieve specified columns from the case data used to build a model.</span></span> <span data-ttu-id="36096-128">为运行此查询，您必须对模型具有钻取权限。</span><span class="sxs-lookup"><span data-stu-id="36096-128">You must have drillthrough permissions on the model to run this query.</span></span>  
  
 <span data-ttu-id="36096-129">**查看在结构中包含的所有数据**</span><span class="sxs-lookup"><span data-stu-id="36096-129">**View all the data that is included in the structure**</span></span>  
 `SELECT FROM <structure>.CASES`  
  
 <span data-ttu-id="36096-130">使用此语句可以查看结构中包含的所有数据，包括特定挖掘模型中不包括的列。</span><span class="sxs-lookup"><span data-stu-id="36096-130">Use this statement to view all the data that is included in the structure, including columns that are not included in a particular mining model.</span></span> <span data-ttu-id="36096-131">您必须对模型以及结构具有钻取权限，才能从挖掘结构中检索数据。</span><span class="sxs-lookup"><span data-stu-id="36096-131">You must have drillthrough permissions on the model, as well as on the structure, to retrieve data from the mining structure.</span></span>  
  
 <span data-ttu-id="36096-132">**获取值范围**</span><span class="sxs-lookup"><span data-stu-id="36096-132">**Get range of values**</span></span>  
 `SELECT DISTINCT RangeMin(<column>), RangeMax(<column>) FROM <model>`  
  
 <span data-ttu-id="36096-133">使用此语句可以查找连续列或 DISCRETIZED 列的存储桶的最小值、最大值和平均值。</span><span class="sxs-lookup"><span data-stu-id="36096-133">Use this statement to find the minimum value, maximum value, and mean of a continuous column, or of the buckets of a DISCRETIZED column.</span></span>  
  
 <span data-ttu-id="36096-134">**获取非重复值**</span><span class="sxs-lookup"><span data-stu-id="36096-134">**Get distinct values**</span></span>  
 `SELECT DISTINCT <column>FROM <model>`  
  
 <span data-ttu-id="36096-135">使用此语句可以检索 DISCRETE 列的所有值。</span><span class="sxs-lookup"><span data-stu-id="36096-135">Use this statement to retrieve all the values of a DISCRETE column.</span></span>  <span data-ttu-id="36096-136">请勿针对 DISCRETIZED 列使用此语句；请改用 `RangeMin` 和 `RangeMax` 函数。</span><span class="sxs-lookup"><span data-stu-id="36096-136">Do not use this statement for DISCRETIZED columns; use the `RangeMin` and `RangeMax` functions instead.</span></span>  
  
 <span data-ttu-id="36096-137">**查找用于对模型或结构定型的事例**</span><span class="sxs-lookup"><span data-stu-id="36096-137">**Find the cases that were used to train a model or structure**</span></span>  
 `SELECT  FROM <mining structure.CASES WHERE IsTrainingCase()`  
  
 <span data-ttu-id="36096-138">使用此语句可获取用于对模型定型的完整数据集。</span><span class="sxs-lookup"><span data-stu-id="36096-138">Use this statement to get the complete set of data that was used in a training a model.</span></span>  
  
 <span data-ttu-id="36096-139">**查找用于测试模型或结构的事例**</span><span class="sxs-lookup"><span data-stu-id="36096-139">**Find the cases that are used for testing a model or structure**</span></span>  
 `SELECT  FROM <mining structure.CASES WHERE IsTestingCase()`  
  
 <span data-ttu-id="36096-140">使用此语句可获取为测试与特定结构相关的挖掘模型而保留的数据。</span><span class="sxs-lookup"><span data-stu-id="36096-140">Use this statement to get the data that has been set aside for testing mining models related to a specific structure.</span></span>  
  
 <span data-ttu-id="36096-141">**从特定的模型模式钻取到基础事例数据**</span><span class="sxs-lookup"><span data-stu-id="36096-141">**Drillthrough from a specific model pattern to underlying case data**</span></span>  
 `SELECT FROM <model>.CASESWHERE IsTrainingCase() AND IsInNode(<node>)`  
  
 <span data-ttu-id="36096-142">使用此语句可从定型模型中检索详细事例数据。</span><span class="sxs-lookup"><span data-stu-id="36096-142">Use this statement to retrieve detailed case data from a trained model.</span></span> <span data-ttu-id="36096-143">您必须指定特定节点：例如，必须知道群集的节点 ID、决策树的特定分支，等等。此外，您还必须拥有对模型的钻取权限才能运行此查询。</span><span class="sxs-lookup"><span data-stu-id="36096-143">You must specify a specific node: for example, you must know the node ID of the cluster, the specific branch of the decision tree, etc. Moreover, you must have drillthrough permissions on the model to run this query.</span></span>  
  
###  <a name="queries-on-model-patterns-statistics-and-attributes"></a><a name="bkmk_Patterns"></a> <span data-ttu-id="36096-144">针对模型模式、统计信息和属性的查询</span><span class="sxs-lookup"><span data-stu-id="36096-144">Queries on Model Patterns, Statistics, and Attributes</span></span>  
 <span data-ttu-id="36096-145">数据挖掘模型的内容有多种用途。</span><span class="sxs-lookup"><span data-stu-id="36096-145">The content of a data mining model is useful for many purposes.</span></span> <span data-ttu-id="36096-146">利用模型内容查询，您可以：</span><span class="sxs-lookup"><span data-stu-id="36096-146">With a model content query, you can:</span></span>  
  
-   <span data-ttu-id="36096-147">提取公式或概率以便您自己来进行计算。</span><span class="sxs-lookup"><span data-stu-id="36096-147">Extract formulas or probabilities for making your own calculations.</span></span>  
  
-   <span data-ttu-id="36096-148">对于关联模型，可检索用于生成预测的规则。</span><span class="sxs-lookup"><span data-stu-id="36096-148">For an association model, retrieve the rules that are used to generate a prediction.</span></span>  
  
-   <span data-ttu-id="36096-149">检索特定规则的说明，以便您可以在自定义应用程序中使用这些规则。</span><span class="sxs-lookup"><span data-stu-id="36096-149">Retrieve the descriptions of specific rules so that you can use the rules in a custom application.</span></span>  
  
-   <span data-ttu-id="36096-150">查看时序模型检测到的移动平均值。</span><span class="sxs-lookup"><span data-stu-id="36096-150">View the moving averages detected by a time series model.</span></span>  
  
-   <span data-ttu-id="36096-151">获取某段趋势线的回归公式。</span><span class="sxs-lookup"><span data-stu-id="36096-151">Obtain the regression formula for some segment of the trend line.</span></span>  
  
-   <span data-ttu-id="36096-152">检索与标识为特定群集的一部分的客户有关的可行信息。</span><span class="sxs-lookup"><span data-stu-id="36096-152">Retrieve actionable information about customers identified as being part of a specific cluster.</span></span>  
  
 <span data-ttu-id="36096-153">以下示例演示了一些用于创建针对模型内容的查询的常用模式：</span><span class="sxs-lookup"><span data-stu-id="36096-153">The following examples show some of the common patterns for creating queries on the model content:</span></span>  
  
 <span data-ttu-id="36096-154">**从模型中获取模式**</span><span class="sxs-lookup"><span data-stu-id="36096-154">**Get patterns from the model**</span></span>  
 `SELECT FROM <model>.CONTENT`  
  
 <span data-ttu-id="36096-155">使用此语句可以检索有关模型中特定节点的详细信息。</span><span class="sxs-lookup"><span data-stu-id="36096-155">Use this statement to retrieve detailed information about specific nodes in the model.</span></span> <span data-ttu-id="36096-156">根据算法类型，该节点可包含规则和公式、支持和方差统计信息等。</span><span class="sxs-lookup"><span data-stu-id="36096-156">Depending on the algorithm type, the node can contain rules and formulas, support and variance statistics, and so forth.</span></span>  
  
 <span data-ttu-id="36096-157">**检索在定型模型中使用的属性**</span><span class="sxs-lookup"><span data-stu-id="36096-157">**Retrieve attributes used in a trained model**</span></span>  
 `CALL System.GetModelAttributes(<model>)`  
  
 <span data-ttu-id="36096-158">使用此存储过程可以检索已由某一模型使用的属性的列表。</span><span class="sxs-lookup"><span data-stu-id="36096-158">Use this stored procedure to retrieve the list of attributes that were used by a model.</span></span> <span data-ttu-id="36096-159">例如，此信息可用于确定由于功能选择而清除的属性。</span><span class="sxs-lookup"><span data-stu-id="36096-159">This information is useful for determining attributes that were eliminated as a result of feature selection, for example.</span></span>  
  
 <span data-ttu-id="36096-160">**检索在数据挖掘维度中存储的内容**</span><span class="sxs-lookup"><span data-stu-id="36096-160">**Retrieve content stored in a data mining dimension**</span></span>  
 `SELECT FROM <model>.DIMENSIONCONTENT`  
  
 <span data-ttu-id="36096-161">使用此语句可以从数据挖掘维度中检索数据。</span><span class="sxs-lookup"><span data-stu-id="36096-161">Use this statement to retrieve the data from a data mining dimension.</span></span>  
  
 <span data-ttu-id="36096-162">此查询类型主要供内部使用。</span><span class="sxs-lookup"><span data-stu-id="36096-162">This query type is principally for internal use.</span></span> <span data-ttu-id="36096-163">但是，并非所有算法都支持此功能。</span><span class="sxs-lookup"><span data-stu-id="36096-163">However, not all algorithms support this functionality.</span></span> <span data-ttu-id="36096-164">是否支持将通过 MINING_SERVICES 架构行集中的一个标志来指示。</span><span class="sxs-lookup"><span data-stu-id="36096-164">Support is indicated by a flag in the MINING_SERVICES schema rowset.</span></span>  
  
 <span data-ttu-id="36096-165">如果您开发自己的插件算法，则可使用此语句验证您的模型的内容以便进行测试。</span><span class="sxs-lookup"><span data-stu-id="36096-165">If you develop your own plug-in algorithm, you might use this statement to verify the content of your model for testing.</span></span>  
  
 <span data-ttu-id="36096-166">**获取模型的 PMML 表示形式**</span><span class="sxs-lookup"><span data-stu-id="36096-166">**Get the PMML representation of a model**</span></span>  
 `SELECT * FROM <model>.PMML`  
  
 <span data-ttu-id="36096-167">获取以 PMML 格式表示模型的 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="36096-167">Gets an XML document that represents the model in PMML format.</span></span> <span data-ttu-id="36096-168">并非支持所有模型类型。</span><span class="sxs-lookup"><span data-stu-id="36096-168">Not all model types are supported.</span></span>  
  
##  <a name="examples"></a><a name="bkmk_Examples"></a> <span data-ttu-id="36096-169">示例</span><span class="sxs-lookup"><span data-stu-id="36096-169">Examples</span></span>  
 <span data-ttu-id="36096-170">尽管某些模型内容在各算法中是标准的，但根据您用于生成模型的算法不同，内容的某些部分会大不相同。</span><span class="sxs-lookup"><span data-stu-id="36096-170">Although some model content is standard across algorithms, some parts of the content vary greatly depending on the algorithm that you used to build the model.</span></span> <span data-ttu-id="36096-171">因此，在创建内容查询时，必须了解模型中哪些信息对您的特定模型最有用。</span><span class="sxs-lookup"><span data-stu-id="36096-171">Therefore, when you create a content query, you must understand what information in the model is most useful to your specific model.</span></span>  
  
 <span data-ttu-id="36096-172">本节提供了几个示例，用来演示选择的算法如何影响存储在模型中的信息类型。</span><span class="sxs-lookup"><span data-stu-id="36096-172">A few examples are provided in this section to illustrate how the choice of algorithm affects the kind of information that is stored in the model.</span></span> <span data-ttu-id="36096-173">有关挖掘模型内容以及每种模型类型特定的内容的详细信息，请参阅[挖掘模型内容（Analysis Services - 数据挖掘）](mining-model-content-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="36096-173">For more information about mining model content, and the content that is specific to each model type, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
###  <a name="example-1-content-query-on-an-association-model"></a><a name="bkmk_Assoc"></a> <span data-ttu-id="36096-174">示例 1：针对关联模型的内容查询</span><span class="sxs-lookup"><span data-stu-id="36096-174">Example 1: Content Query on an Association Model</span></span>  
 <span data-ttu-id="36096-175">`SELECT FROM <model>.CONTENT`语句返回不同种类的信息，具体取决于您正在查询的模型类型。</span><span class="sxs-lookup"><span data-stu-id="36096-175">The statement, `SELECT FROM <model>.CONTENT`, returns different kinds of information, depending on the type of model you are querying.</span></span> <span data-ttu-id="36096-176">对于关联模型，“节点类型” \*\* 为一段关键信息。</span><span class="sxs-lookup"><span data-stu-id="36096-176">For an association model, a key piece of information is the *node type*.</span></span> <span data-ttu-id="36096-177">节点类似于模型内容中的信息的容器。</span><span class="sxs-lookup"><span data-stu-id="36096-177">Nodes are like containers for information in the model content.</span></span> <span data-ttu-id="36096-178">在关联模型中，表示规则的节点的 NODE_TYPE 值为 8，而表示项集的节点的 NODE_TYPE 值为 7。</span><span class="sxs-lookup"><span data-stu-id="36096-178">In an association model, nodes that represent rules have a NODE_TYPE value of 8, whereas nodes that represent itemsets have a NODE_TYPE value of 7.</span></span>  
  
 <span data-ttu-id="36096-179">因此，以下查询将返回前 10 个项集，按照 SUPPORT 排序（默认排序）。</span><span class="sxs-lookup"><span data-stu-id="36096-179">Thus, the following query returns the top 10 itemsets, ranked by support (the default ordering).</span></span>  
  
```  
SELECT TOP 10 NODE_DESCRIPTION, NODE_PROBABILITY, SUPPORT  
FROM <model>.CONTENT WHERE NODE_TYPE = 7  
```  
  
 <span data-ttu-id="36096-180">下面的查询构建于这些信息之上。</span><span class="sxs-lookup"><span data-stu-id="36096-180">The following query builds on this information.</span></span> <span data-ttu-id="36096-181">该查询返回三列：节点的 ID、完整规则以及项集右侧的产品（即，预测将作为项集的一部分与其他某些产品关联的产品）。</span><span class="sxs-lookup"><span data-stu-id="36096-181">The query returns three columns: the ID of the node, the complete rule, and the product on the right-hand side of the itemset-that is, the product that is predicted to be associated with some other products as part of an itemset.</span></span>  
  
```  
SELECT FLATTENED NODE_UNIQUE_NAME, NODE_DESCRIPTION,  
     (SELECT RIGHT(ATTRIBUTE_NAME, (LEN(ATTRIBUTE_NAME)-LEN('Association model name')))   
FROM NODE_DISTRIBUTION  
WHERE LEN(ATTRIBUTE_NAME)>2  
)   
AS RightSideProduct  
FROM [<Association model name>].CONTENT  
WHERE NODE_TYPE = 8   
ORDER BY NODE_SUPPORT DESC  
```  
  
 <span data-ttu-id="36096-182">FLATTENED 关键字表示嵌套行集应转换为平展表。</span><span class="sxs-lookup"><span data-stu-id="36096-182">The FLATTENED keyword indicates that the nested rowset should be converted into a flattened table.</span></span> <span data-ttu-id="36096-183">在规则右侧表示产品的属性包含在 NODE_DISTRIBUTION 表中；因此，我们通过添加长度大于 2 的要求来仅检索包含属性名的行。</span><span class="sxs-lookup"><span data-stu-id="36096-183">The attribute that represents the product on the right-hand side of the rule is contained in the NODE_DISTRIBUTION table; therefore, we retrieve only the row that contains an attribute name, by adding a requirement that the length be greater than 2.</span></span>  
  
 <span data-ttu-id="36096-184">使用一个简单的字符串函数从第三列中删除模型的名称。</span><span class="sxs-lookup"><span data-stu-id="36096-184">A simple string function is used to remove the name of the model from the third column.</span></span> <span data-ttu-id="36096-185">（通常，模型名称作为嵌套列的值的前缀。）</span><span class="sxs-lookup"><span data-stu-id="36096-185">(Usually the model name is prefixed to the values of nested columns.)</span></span>  
  
 <span data-ttu-id="36096-186">WHERE 子句指定 NODE_TYPE 的值应当为 8，这表示仅仅检索规则。</span><span class="sxs-lookup"><span data-stu-id="36096-186">The WHERE clause specifies that the value of NODE_TYPE should be 8, to retrieve only rules.</span></span>  
  
 <span data-ttu-id="36096-187">有关更多示例，请参阅 [关联模型查询示例](association-model-query-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="36096-187">For more examples, see [Association Model Query Examples](association-model-query-examples.md).</span></span>  
  
###  <a name="example-2-content-query-on-a-decision-trees-model"></a><a name="bkmk_DecTree"></a> <span data-ttu-id="36096-188">示例 2：针对决策树模型的内容查询</span><span class="sxs-lookup"><span data-stu-id="36096-188">Example 2: Content Query on a Decision Trees Model</span></span>  
 <span data-ttu-id="36096-189">决策树模型可用于预测以及分类。</span><span class="sxs-lookup"><span data-stu-id="36096-189">A decision tree model can be used for prediction as well as for classification.</span></span>  <span data-ttu-id="36096-190">此示例假定您使用模型是为了预测结果，但同时也希望找出可以使用哪些因子或规则来对结果进行分类。</span><span class="sxs-lookup"><span data-stu-id="36096-190">This example assumes that you are using the model to predict an outcome, but you also want to find out which factors or rules can be used to classify the outcome.</span></span>  
  
 <span data-ttu-id="36096-191">在决策树模型中，使用节点表示树和叶节点。</span><span class="sxs-lookup"><span data-stu-id="36096-191">In a decision tree model, nodes are used to represent both trees and leaf nodes.</span></span> <span data-ttu-id="36096-192">每个节点的标题包含指向结果的路径的说明。</span><span class="sxs-lookup"><span data-stu-id="36096-192">The caption for each node contains the description of the path to the outcome.</span></span> <span data-ttu-id="36096-193">因此，若要跟踪任一特定结果的路径，您需要确定包含该结果的节点，然后获取该节点的详细信息。</span><span class="sxs-lookup"><span data-stu-id="36096-193">Therefore, to trace the path for any particular outcome, you need to identify the node that contains it, and get the details for that node.</span></span>  
  
 <span data-ttu-id="36096-194">在预测查询中，可以添加预测函数 [PredictNodeId (DMX)](/sql/dmx/predictnodeid-dmx) 来获取相关节点的 ID，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="36096-194">In your prediction query, you add the prediction function [PredictNodeId &#40;DMX&#41;](/sql/dmx/predictnodeid-dmx), to get the ID of the related node, as shown in the following example:</span></span>  
  
```  
SELECT  Predict([Bike Buyer]), PredictNodeID([Bike Buyer])   
FROM [<decision tree model name>]  
PREDICTION JOIN   
<input rowset>   
```  
  
 <span data-ttu-id="36096-195">一旦您有了包含结果的节点的 ID，就可以通过创建包含 NODE_CAPTION 的内容查询，来检索说明预测的规则或路径，如下所示：</span><span class="sxs-lookup"><span data-stu-id="36096-195">Once you have the ID of the node that contains the outcome, you can retrieve the rule or path that explains the prediction by creating a content query that includes the NODE_CAPTION, as follows:</span></span>  
  
```  
SELECT NODE_CAPTION  
FROM [<decision tree model name>]   
WHERE NODE_UNIQUE_NAME= '<node id>'  
```  
  
 <span data-ttu-id="36096-196">有关更多示例，请参阅 [决策树模型查询示例](decision-trees-model-query-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="36096-196">For more examples, see [Decision Trees Model Query Examples](decision-trees-model-query-examples.md).</span></span>  
  
##  <a name="working-with-the-query-results"></a><a name="bkmk_Results"></a> <span data-ttu-id="36096-197">使用查询结果</span><span class="sxs-lookup"><span data-stu-id="36096-197">Working with the Query Results</span></span>  
 <span data-ttu-id="36096-198">如示例中所示，内容查询主要返回表格行集，但还可以包含来自嵌套列的信息。</span><span class="sxs-lookup"><span data-stu-id="36096-198">As the examples demonstrate, content queries mostly return tabular rowsets, but can also include information from nested columns.</span></span> <span data-ttu-id="36096-199">您可以平展返回的行集，但这样做可能会导致对结果的使用更复杂。</span><span class="sxs-lookup"><span data-stu-id="36096-199">You can flatten the rowset that is returned, but this can make working with results more complex.</span></span> <span data-ttu-id="36096-200">特别是 NODE_DISTRIBUTION 节点的内容是嵌套的，但包含了大量有关模型的有用信息。</span><span class="sxs-lookup"><span data-stu-id="36096-200">The content of the NODE_DISTRIBUTION node in particular is nested, but contains much interesting information about the model.</span></span>  
  
 <span data-ttu-id="36096-201">有关如何使用分层行集的详细信息，请参阅 MSDN 上的 OLEDB 规范。</span><span class="sxs-lookup"><span data-stu-id="36096-201">For more information about how to work with hierarchical rowsets, see the OLEDB specification on MSDN.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36096-202">另请参阅</span><span class="sxs-lookup"><span data-stu-id="36096-202">See Also</span></span>  
 <span data-ttu-id="36096-203">[了解 DMX Select 语句](/sql/dmx/understanding-the-dmx-select-statement) </span><span class="sxs-lookup"><span data-stu-id="36096-203">[Understanding the DMX Select Statement](/sql/dmx/understanding-the-dmx-select-statement) </span></span>  
 [<span data-ttu-id="36096-204">数据挖掘查询</span><span class="sxs-lookup"><span data-stu-id="36096-204">Data Mining Queries</span></span>](data-mining-queries.md)  
  
  
