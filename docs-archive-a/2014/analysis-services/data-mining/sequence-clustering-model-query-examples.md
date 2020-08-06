---
title: 顺序分析和聚类分析模型查询示例 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- sequence clustering algorithms [Analysis Services]
- content queries [DMX]
- sequence [Analysis Services]
ms.assetid: 64bebcdc-70ab-43fb-8d40-57672a126602
author: minewiskan
ms.author: owend
ms.openlocfilehash: d56924f27f7986861895cf4fff21fa758cc47070
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577083"
---
# <a name="sequence-clustering-model-query-examples"></a><span data-ttu-id="da790-102">顺序分析和聚类分析模型查询示例</span><span class="sxs-lookup"><span data-stu-id="da790-102">Sequence Clustering Model Query Examples</span></span>
  <span data-ttu-id="da790-103">在对数据挖掘模型创建查询时，可以创建内容查询，也可以创建预测查询。内容查询提供有关模型中存储的信息的详细信息，预测查询使用模型中的模式并基于您提供的新数据进行预测。</span><span class="sxs-lookup"><span data-stu-id="da790-103">When you create a query against a data mining model, you can create either a content query, which provides details about the information stored in the model, or you can create a prediction query, which uses the patterns in the model to make predictions based on new data that you provide.</span></span> <span data-ttu-id="da790-104">对于顺序分析和聚类分析模型，内容查询通常会提供所发现的分类的更多详细信息，或这些分类中的转换。</span><span class="sxs-lookup"><span data-stu-id="da790-104">For a sequence clustering model, content queries typically provide additional details about the clusters that were found, or the transitions within those clusters.</span></span> <span data-ttu-id="da790-105">您还可以使用查询来检索有关模型的元数据。</span><span class="sxs-lookup"><span data-stu-id="da790-105">You can also retrieve metadata about the model by using a query.</span></span>  
  
 <span data-ttu-id="da790-106">针对顺序分析和聚类分析模型的预测查询通常是基于序列和转换、基于模型中包含的非序列属性或基于序列属性和非序列属性的组合来提出建议。</span><span class="sxs-lookup"><span data-stu-id="da790-106">Prediction queries on a sequence clustering model typically make recommendations based either on the sequences and transitions, on non-sequence attributes that were included in the model, or on a combination of sequence and non-sequence attributes.</span></span>  
  
 <span data-ttu-id="da790-107">本节说明如何为基于 Microsoft 顺序分析和聚类分析算法的模型创建查询。</span><span class="sxs-lookup"><span data-stu-id="da790-107">This section explains how to create queries for models that are based on the Microsoft Sequence Clustering algorithm.</span></span> <span data-ttu-id="da790-108">有关创建查询的常规信息，请参阅 [数据挖掘查询](data-mining-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="da790-108">For general information about creating queries, see [Data Mining Queries](data-mining-queries.md).</span></span>  
  
 <span data-ttu-id="da790-109">**内容查询**</span><span class="sxs-lookup"><span data-stu-id="da790-109">**Content Queries**</span></span>  
  
 [<span data-ttu-id="da790-110">使用数据挖掘架构行集返回模型参数</span><span class="sxs-lookup"><span data-stu-id="da790-110">Using the Data Mining Schema Rowset to return model parameters</span></span>](#bkmk_Query1)  
  
 [<span data-ttu-id="da790-111">获取某种状态的序列列表</span><span class="sxs-lookup"><span data-stu-id="da790-111">Getting a list of sequences for a state</span></span>](#bkmk_Query2)  
  
 [<span data-ttu-id="da790-112">使用系统存储过程</span><span class="sxs-lookup"><span data-stu-id="da790-112">Using system stored procedures</span></span>](#bkmk_Query3)  
  
 <span data-ttu-id="da790-113">**预测查询**</span><span class="sxs-lookup"><span data-stu-id="da790-113">**Prediction Queries**</span></span>  
  
 [<span data-ttu-id="da790-114">预测后面的一种或多种状态</span><span class="sxs-lookup"><span data-stu-id="da790-114">Predict next state or states</span></span>](#bkmk_Query4)  
  
##  <a name="finding-information-about-the-sequence-clustering-model"></a><a name="bkmk_ContentQueries"></a><span data-ttu-id="da790-115">查找有关顺序分析和聚类分析模型的信息</span><span class="sxs-lookup"><span data-stu-id="da790-115">Finding Information about the Sequence Clustering Model</span></span>  
 <span data-ttu-id="da790-116">若要对挖掘模型的内容创建有意义的查询，您必须了解模型内容的结构以及哪些节点类型存储哪类信息。</span><span class="sxs-lookup"><span data-stu-id="da790-116">To create meaningful queries on the content of a mining model, you must understand the structure of the model content, and which node types store what kind of information.</span></span> <span data-ttu-id="da790-117">有关详细信息，请参阅 [顺序分析和聚类分析模型的挖掘模型内容（Analysis Services - 数据挖掘）](mining-model-content-for-sequence-clustering-models.md)。</span><span class="sxs-lookup"><span data-stu-id="da790-117">For more information, see [Mining Model Content for Sequence Clustering Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-sequence-clustering-models.md).</span></span>  
  
###  <a name="sample-query-1-using-the-data-mining-schema-rowset-to-return-model-parameters"></a><a name="bkmk_Query1"></a><span data-ttu-id="da790-118">示例查询1：使用数据挖掘架构行集返回模型参数</span><span class="sxs-lookup"><span data-stu-id="da790-118">Sample Query 1: Using the Data Mining Schema Rowset to Return Model Parameters</span></span>  
 <span data-ttu-id="da790-119">通过查询数据挖掘架构行集，您可以找到关于模型的各类信息，包括基本元数据、模型的创建日期和时间、上次处理模型的日期和时间、模型所基于的挖掘结构的名称以及用作可预测属性的列。</span><span class="sxs-lookup"><span data-stu-id="da790-119">By querying the data mining schema rowset, you can find various kinds of information about the model, including basic metadata, the date and time that the model was created and last processed, the name of the mining structure that the model is based on, and the column used as the predictable attribute.</span></span>  
  
 <span data-ttu-id="da790-120">下面的查询返回用于生成模型 `[Sequence Clustering]`和为其定型的参数。</span><span class="sxs-lookup"><span data-stu-id="da790-120">The following query returns the parameters that were used to build and train the model, `[Sequence Clustering]`.</span></span> <span data-ttu-id="da790-121">您可以在 [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md)的第 5 课中创建此模型。</span><span class="sxs-lookup"><span data-stu-id="da790-121">You can create this model in Lesson 5 of the [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md).</span></span>  
  
```  
SELECT MINING_PARAMETERS   
from $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'Sequence Clustering'  
```  
  
 <span data-ttu-id="da790-122">示例结果：</span><span class="sxs-lookup"><span data-stu-id="da790-122">Example results:</span></span>  
  
|<span data-ttu-id="da790-123">MINING_PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="da790-123">MINING_PARAMETERS</span></span>|  
|------------------------|  
|<span data-ttu-id="da790-124">CLUSTER_COUNT=15,MINIMUM_SUPPORT=10,MAXIMUM_STATES=100,MAXIMUM_SEQUENCE_STATES=64</span><span class="sxs-lookup"><span data-stu-id="da790-124">CLUSTER_COUNT=15,MINIMUM_SUPPORT=10,MAXIMUM_STATES=100,MAXIMUM_SEQUENCE_STATES=64</span></span>|  
  
 <span data-ttu-id="da790-125">请注意，此模型是使用默认值为 10 的 CLUSTER_COUNT 创建的。</span><span class="sxs-lookup"><span data-stu-id="da790-125">Note that this model was built by using the default value of 10 for CLUSTER_COUNT.</span></span> <span data-ttu-id="da790-126">当您为 CLUSTER_COUNT 指定的分类数不为零时，算法会将此数视为要查找的大致分类数。</span><span class="sxs-lookup"><span data-stu-id="da790-126">When you specify a non-zero number of clusters for CLUSTER_COUNT, the algorithm treats this number as a hint for the approximate number of clusters to find.</span></span> <span data-ttu-id="da790-127">但是，在分析的过程中，算法可能会找到多于或少于指定数的分类。</span><span class="sxs-lookup"><span data-stu-id="da790-127">However, in the process of analysis, the algorithm may find more or fewer clusters.</span></span> <span data-ttu-id="da790-128">在本例中，算法发现 15 个分类与定型数据拟合最好。</span><span class="sxs-lookup"><span data-stu-id="da790-128">In this case, the algorithm found that 15 clusters best fit the training data.</span></span> <span data-ttu-id="da790-129">因此，已完成模型的参数值列表将报告由算法确定的分类数，而不是创建模型时传入的值。</span><span class="sxs-lookup"><span data-stu-id="da790-129">Therefore, the list of parameter values for the completed model reports the count of clusters as determined by the algorithm, not the value passed in when creating the model.</span></span>  
  
 <span data-ttu-id="da790-130">此行为与让算法确定最佳分类数有何不同呢？</span><span class="sxs-lookup"><span data-stu-id="da790-130">How does this behavior differ from letting the algorithm determine the best number of clusters?</span></span> <span data-ttu-id="da790-131">您可以试验一下，创建另一个使用相同数据的聚类分析模型，但将 CLUSTER_COUNT 设置为 0。</span><span class="sxs-lookup"><span data-stu-id="da790-131">As an experiment, you can create another clustering model that uses this same data, but set CLUSTER_COUNT to 0.</span></span> <span data-ttu-id="da790-132">这样做的结果是，算法将检测到 32 个分类。</span><span class="sxs-lookup"><span data-stu-id="da790-132">When you do this, the algorithm detects 32 clusters.</span></span> <span data-ttu-id="da790-133">因此，CLUSTER_COUNT 的默认值使用 10 可以限制结果的数目。</span><span class="sxs-lookup"><span data-stu-id="da790-133">Therefore, by using the default value of 10 for CLUSTER_COUNT, you constrain the number of results.</span></span>  
  
 <span data-ttu-id="da790-134">默认值使用 10 是因为减少分类数更便于大多数人浏览并了解数据中的分组。</span><span class="sxs-lookup"><span data-stu-id="da790-134">The value of 10 is used by default because reducing the number of clusters makes it easier for most people to browse and understand groupings in the data.</span></span> <span data-ttu-id="da790-135">但是，每个模型和数据集是不同的。</span><span class="sxs-lookup"><span data-stu-id="da790-135">However, each model and set of data is different.</span></span> <span data-ttu-id="da790-136">您可以试用不同的分类数，从而发现哪个参数值能产生最精确的模型。</span><span class="sxs-lookup"><span data-stu-id="da790-136">You may wish to experiment with different numbers of clusters to see which parameter value yields the most accurate model.</span></span>  
  
###  <a name="sample-query-2-getting-a-list-of-sequences-for-a-state"></a><a name="bkmk_Query2"></a><span data-ttu-id="da790-137">示例查询2：获取状态的序列列表</span><span class="sxs-lookup"><span data-stu-id="da790-137">Sample Query 2: Getting a List of Sequences for a State</span></span>  
 <span data-ttu-id="da790-138">挖掘模型内容存储在定型数据中找到的序列，序列由第一种状态与所有相关第二种状态的列表组成。</span><span class="sxs-lookup"><span data-stu-id="da790-138">The mining model content stores the sequences that are found in the training data as a first state coupled with a list of all related second states.</span></span> <span data-ttu-id="da790-139">第一种状态用作该序列的标签，相关的第二种状态称为转换。</span><span class="sxs-lookup"><span data-stu-id="da790-139">The first state is used as the label for the sequence, and the related second states are called transitions.</span></span>  
  
 <span data-ttu-id="da790-140">例如，在序列分组到各分类中之前，下面的查询返回模型中第一种状态的完整列表。</span><span class="sxs-lookup"><span data-stu-id="da790-140">For example, the following query returns the complete list of first states in the model, before the sequences are grouped into clusters.</span></span>  <span data-ttu-id="da790-141">获取此列表的方法是返回将模型根节点作为父节点 (PARENT_UNIQUE_NAME = 0) 的序列 (NODE_TYPE = 13) 的列表。</span><span class="sxs-lookup"><span data-stu-id="da790-141">You can get this list by returning the list of sequences (NODE_TYPE = 13) that have the model root node as parent (PARENT_UNIQUE_NAME = 0).</span></span> <span data-ttu-id="da790-142">FLATTENED 关键字可使结果更易读。</span><span class="sxs-lookup"><span data-stu-id="da790-142">The FLATTENED keyword makes the results easier to read.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="da790-143">列的名称、PARENT_UNIQUE_NAME、Support 和 Probability 必须括在方括号内，以便将它们与同名的保留关键字区分开来。</span><span class="sxs-lookup"><span data-stu-id="da790-143">The name of the columns, PARENT_UNIQUE_NAME, Support, and Probability must be enclosed in brackets to distinguish them from the reserved keywords of the same name.</span></span>  
  
```  
SELECT FLATTENED NODE_UNIQUE_NAME,  
(SELECT ATTRIBUTE_VALUE AS [Product 1],  
[Support] AS [Sequence Support],   
[Probability] AS [Sequence Probability]  
FROM NODE_DISTRIBUTION) AS t  
FROM [Sequence Clustering].CONTENT  
WHERE NODE_TYPE = 13  
AND [PARENT_UNIQUE_NAME] = 0  
```  
  
 <span data-ttu-id="da790-144">部分结果：</span><span class="sxs-lookup"><span data-stu-id="da790-144">Partial results:</span></span>  
  
|<span data-ttu-id="da790-145">NODE_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="da790-145">NODE_UNIQUE_NAME</span></span>|<span data-ttu-id="da790-146">Product 1</span><span class="sxs-lookup"><span data-stu-id="da790-146">Product 1</span></span>|<span data-ttu-id="da790-147">Sequence Support</span><span class="sxs-lookup"><span data-stu-id="da790-147">Sequence Support</span></span>|<span data-ttu-id="da790-148">Sequence Probability</span><span class="sxs-lookup"><span data-stu-id="da790-148">Sequence Probability</span></span>|  
|------------------------|---------------|----------------------|--------------------------|  
|<span data-ttu-id="da790-149">1081327</span><span class="sxs-lookup"><span data-stu-id="da790-149">1081327</span></span>|<span data-ttu-id="da790-150">Missing</span><span class="sxs-lookup"><span data-stu-id="da790-150">Missing</span></span>|<span data-ttu-id="da790-151">0</span><span class="sxs-lookup"><span data-stu-id="da790-151">0</span></span>|#######|  
|<span data-ttu-id="da790-152">1081327</span><span class="sxs-lookup"><span data-stu-id="da790-152">1081327</span></span>|<span data-ttu-id="da790-153">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="da790-153">All-Purpose Bike Stand</span></span>|<span data-ttu-id="da790-154">17</span><span class="sxs-lookup"><span data-stu-id="da790-154">17</span></span>|<span data-ttu-id="da790-155">0.00111</span><span class="sxs-lookup"><span data-stu-id="da790-155">0.00111</span></span>|  
|<span data-ttu-id="da790-156">1081327</span><span class="sxs-lookup"><span data-stu-id="da790-156">1081327</span></span>|<span data-ttu-id="da790-157">Bike Wash</span><span class="sxs-lookup"><span data-stu-id="da790-157">Bike Wash</span></span>|<span data-ttu-id="da790-158">64</span><span class="sxs-lookup"><span data-stu-id="da790-158">64</span></span>|<span data-ttu-id="da790-159">0.00418</span><span class="sxs-lookup"><span data-stu-id="da790-159">0.00418</span></span>|  
|<span data-ttu-id="da790-160">1081327</span><span class="sxs-lookup"><span data-stu-id="da790-160">1081327</span></span>|<span data-ttu-id="da790-161">（第 4-36 行省略）</span><span class="sxs-lookup"><span data-stu-id="da790-161">(rows 4-36 omitted)</span></span>|||  
|<span data-ttu-id="da790-162">1081327</span><span class="sxs-lookup"><span data-stu-id="da790-162">1081327</span></span>|<span data-ttu-id="da790-163">Women's Mountain Shorts</span><span class="sxs-lookup"><span data-stu-id="da790-163">Women's Mountain Shorts</span></span>|<span data-ttu-id="da790-164">506</span><span class="sxs-lookup"><span data-stu-id="da790-164">506</span></span>|<span data-ttu-id="da790-165">0.03307</span><span class="sxs-lookup"><span data-stu-id="da790-165">0.03307</span></span>|  
  
 <span data-ttu-id="da790-166">模型中的序列列表始终按字母升序排序。</span><span class="sxs-lookup"><span data-stu-id="da790-166">The list of sequences in the model is always sorted alphabetically in ascending order.</span></span> <span data-ttu-id="da790-167">序列的排序非常重要，因为您可以通过查看序列的序号来查找相关转换。</span><span class="sxs-lookup"><span data-stu-id="da790-167">The ordering of the sequences is important because you can find the related transitions by looking at the order number of the sequence.</span></span> <span data-ttu-id="da790-168">`Missing` 值始终为转换 0。</span><span class="sxs-lookup"><span data-stu-id="da790-168">The `Missing` value is always transition 0.</span></span>  
  
 <span data-ttu-id="da790-169">例如，在上面的结果中，产品“Women's Mountain Shorts”在模型中的序列号为 37。</span><span class="sxs-lookup"><span data-stu-id="da790-169">For example, in the previous results, the product "Women's Mountain Shorts" is the sequence number 37 in the model.</span></span> <span data-ttu-id="da790-170">您可以使用该信息来查看在购买“Women's Mountain Shorts”之后购买的所有产品。</span><span class="sxs-lookup"><span data-stu-id="da790-170">You can use that information to view all of the products that were ever purchased after "Women's Mountain Shorts."</span></span>  
  
 <span data-ttu-id="da790-171">为此，首先需要引用从上述查询中返回的 NODE_UNIQUE_NAME 值，以获取包含该模型所有序列的节点的 ID。</span><span class="sxs-lookup"><span data-stu-id="da790-171">To do this, first, you reference the value returned for NODE_UNIQUE_NAME in the previous query, to get the ID of the node that contains all sequences for the model.</span></span> <span data-ttu-id="da790-172">将此值作为父节点的 ID 传递给查询，这样将仅获取此节点中包含的转换，而此节点恰好包含该模型所有序列的列表。</span><span class="sxs-lookup"><span data-stu-id="da790-172">You pass this value to the query as the ID of the parent node, to get only the transitions included in this node, which happens to contain a list of al sequences for the model.</span></span> <span data-ttu-id="da790-173">但是，如果您希望查看特定分类的转换列表，则可传入群集节点的 ID，从而仅查看与该分类关联的序列。</span><span class="sxs-lookup"><span data-stu-id="da790-173">However, if you wanted to see the list of transitions for a specific cluster, you could pass in the ID of the cluster node, and see only the sequences associated with that cluster.</span></span>  
  
```  
SELECT NODE_UNIQUE_NAME  
FROM [Sequence Clustering].CONTENT  
WHERE NODE_DESCRIPTION = 'Transition row for sequence state 37'  
AND [PARENT_UNIQUE_NAME] = '1081327'  
```  
  
 <span data-ttu-id="da790-174">示例结果：</span><span class="sxs-lookup"><span data-stu-id="da790-174">Example results:</span></span>  
  
|<span data-ttu-id="da790-175">NODE_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="da790-175">NODE_UNIQUE_NAME</span></span>|  
|------------------------|  
|<span data-ttu-id="da790-176">1081365</span><span class="sxs-lookup"><span data-stu-id="da790-176">1081365</span></span>|  
  
 <span data-ttu-id="da790-177">此 ID 表示的节点包含购买“Women's Mountain Shorts”产品之后的序列列表以及支持和概率值。</span><span class="sxs-lookup"><span data-stu-id="da790-177">The node represented by this ID contains a list of the sequences that follow the "Women's Mountain Shorts" product, together with the support and probability values.</span></span>  
  
```  
SELECT FLATTENED  
(SELECT ATTRIBUTE_VALUE AS Product2,  
[Support] AS [P2 Support],  
[Probability] AS [P2 Probability]  
FROM NODE_DISTRIBUTION) AS t  
FROM [Sequence Clustering].CONTENT  
WHERE NODE_UNIQUE_NAME = '1081365'  
```  
  
 <span data-ttu-id="da790-178">示例结果：</span><span class="sxs-lookup"><span data-stu-id="da790-178">Example results:</span></span>  
  
|<span data-ttu-id="da790-179">t.Product2</span><span class="sxs-lookup"><span data-stu-id="da790-179">t.Product2</span></span>|<span data-ttu-id="da790-180">t.P2 Support</span><span class="sxs-lookup"><span data-stu-id="da790-180">t.P2 Support</span></span>|<span data-ttu-id="da790-181">t.P2 Probability</span><span class="sxs-lookup"><span data-stu-id="da790-181">t.P2 Probability</span></span>|  
|----------------|------------------|----------------------|  
|<span data-ttu-id="da790-182">Missing</span><span class="sxs-lookup"><span data-stu-id="da790-182">Missing</span></span>|<span data-ttu-id="da790-183">230.7419</span><span class="sxs-lookup"><span data-stu-id="da790-183">230.7419</span></span>|<span data-ttu-id="da790-184">0.456012</span><span class="sxs-lookup"><span data-stu-id="da790-184">0.456012</span></span>|  
|<span data-ttu-id="da790-185">Classic Vest</span><span class="sxs-lookup"><span data-stu-id="da790-185">Classic Vest</span></span>|<span data-ttu-id="da790-186">8.16129</span><span class="sxs-lookup"><span data-stu-id="da790-186">8.16129</span></span>|<span data-ttu-id="da790-187">0.016129</span><span class="sxs-lookup"><span data-stu-id="da790-187">0.016129</span></span>|  
|<span data-ttu-id="da790-188">Cycling Cap</span><span class="sxs-lookup"><span data-stu-id="da790-188">Cycling Cap</span></span>|<span data-ttu-id="da790-189">60.83871</span><span class="sxs-lookup"><span data-stu-id="da790-189">60.83871</span></span>|<span data-ttu-id="da790-190">0.120235</span><span class="sxs-lookup"><span data-stu-id="da790-190">0.120235</span></span>|  
|<span data-ttu-id="da790-191">Half-Finger Gloves</span><span class="sxs-lookup"><span data-stu-id="da790-191">Half-Finger Gloves</span></span>|<span data-ttu-id="da790-192">30.41935</span><span class="sxs-lookup"><span data-stu-id="da790-192">30.41935</span></span>|<span data-ttu-id="da790-193">0.060117</span><span class="sxs-lookup"><span data-stu-id="da790-193">0.060117</span></span>|  
|<span data-ttu-id="da790-194">Long-Sleeve Logo Jersey</span><span class="sxs-lookup"><span data-stu-id="da790-194">Long-Sleeve Logo Jersey</span></span>|<span data-ttu-id="da790-195">86.80645</span><span class="sxs-lookup"><span data-stu-id="da790-195">86.80645</span></span>|<span data-ttu-id="da790-196">0.171554</span><span class="sxs-lookup"><span data-stu-id="da790-196">0.171554</span></span>|  
|<span data-ttu-id="da790-197">Racing Socks</span><span class="sxs-lookup"><span data-stu-id="da790-197">Racing Socks</span></span>|<span data-ttu-id="da790-198">28.93548</span><span class="sxs-lookup"><span data-stu-id="da790-198">28.93548</span></span>|<span data-ttu-id="da790-199">0.057185</span><span class="sxs-lookup"><span data-stu-id="da790-199">0.057185</span></span>|  
|<span data-ttu-id="da790-200">Short-Sleeve Classic Jersey</span><span class="sxs-lookup"><span data-stu-id="da790-200">Short-Sleeve Classic Jersey</span></span>|<span data-ttu-id="da790-201">60.09677</span><span class="sxs-lookup"><span data-stu-id="da790-201">60.09677</span></span>|<span data-ttu-id="da790-202">0.118768</span><span class="sxs-lookup"><span data-stu-id="da790-202">0.118768</span></span>|  
  
 <span data-ttu-id="da790-203">请注意，与 Women's Mountain Shorts 相关的各序列的支持在模型中为 506。</span><span class="sxs-lookup"><span data-stu-id="da790-203">Note that support for the various sequences related to Women's Mountain Shorts is 506 in the model.</span></span> <span data-ttu-id="da790-204">转换的支持值总计也为 506。</span><span class="sxs-lookup"><span data-stu-id="da790-204">The support values for the transitions also add up to 506.</span></span> <span data-ttu-id="da790-205">但是，这些支持数不是整数，如果您认为支持仅表示包含每个转换的事例计数，这似乎有些奇怪。</span><span class="sxs-lookup"><span data-stu-id="da790-205">However, the numbers are not whole numbers, which seems a bit odd if you expect support to simply represent a count of cases that contain each transition.</span></span> <span data-ttu-id="da790-206">但是，由于用于创建分类的方法计算部分成员身份，因此某个分类中任一转换的概率必须由该转换属于该特定分类的概率来衡量。</span><span class="sxs-lookup"><span data-stu-id="da790-206">However, because the method for creating clusters calculates partial membership, the probability of any transition within a cluster must be weighted by its probability of belonging to that particular cluster.</span></span>  
  
 <span data-ttu-id="da790-207">例如，如果有 4 个分类，则特定序列可能有 40% 的几率属于分类 1、30% 的几率属于分类 2、20% 的几率属于分类 3 以及 10% 的几率属于分类 4。</span><span class="sxs-lookup"><span data-stu-id="da790-207">For example, if there are four clusters, a particular sequence might have a 40% chance of belonging to cluster 1, a 30% chance of belonging to cluster 2, a 20% chance of belonging to cluster 3, and a 10% chance of belonging to cluster 4.</span></span> <span data-ttu-id="da790-208">在算法确定转换最有可能属于的分类后，它使用分类先验概率来衡量转换在该分类中的概率。</span><span class="sxs-lookup"><span data-stu-id="da790-208">After the algorithm determines the cluster that the transition is mostly likely to belong to, it weights the probabilities within the cluster by the cluster prior probability.</span></span>  
  
###  <a name="sample-query-3-using-system-stored-procedures"></a><a name="bkmk_Query3"></a><span data-ttu-id="da790-209">示例查询3：使用系统存储过程</span><span class="sxs-lookup"><span data-stu-id="da790-209">Sample Query 3: Using System Stored Procedures</span></span>  
 <span data-ttu-id="da790-210">从这些查询示例中，可以看到模型中存储的信息很复杂，您可能需要创建多个查询才能获取所需的信息。</span><span class="sxs-lookup"><span data-stu-id="da790-210">You can see from these query samples that the information stored in the model is complex, and that you might need to create multiple queries to get the information that you need.</span></span> <span data-ttu-id="da790-211">不过，Microsoft 顺序分析和聚类分析查看器提供了一组功能强大的工具，可用于以图形方式浏览顺序分析和聚类分析模型中包含的信息，您还可以使用该查看器来查询和深化模型。</span><span class="sxs-lookup"><span data-stu-id="da790-211">However, the Microsoft Sequence Clustering viewer provides a powerful set of tools for graphically browsing the information contained in a sequence clustering model, and you can also use the viewer to query and drill down into the model.</span></span>  
  
 <span data-ttu-id="da790-212">在大多数情况下，Microsoft 顺序分析和聚类分析查看器中显示的信息是使用 Analysis Services 系统存储过程来查询模型而创建的。</span><span class="sxs-lookup"><span data-stu-id="da790-212">In most cases, the information that is presented in the Microsoft Sequence Clustering viewer is created by using Analysis Services system stored procedures to query the model.</span></span> <span data-ttu-id="da790-213">您也可以编写针对模型内容的数据挖掘扩展插件 (DMX) 查询来检索同一信息，但是对于浏览或测试模型，使用 Analysis Services 系统存储过程非常简便快捷。</span><span class="sxs-lookup"><span data-stu-id="da790-213">You can write Data Mining Extensions (DMX) queries against the model content to retrieve the same information, but the Analysis Services system stored procedures provide a convenient shortcut when for exploration or for testing models.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="da790-214">系统存储过程是 Microsoft 提供的与 Analysis Services 服务器进行交互的工具，可供服务器和客户端进行内部处理。</span><span class="sxs-lookup"><span data-stu-id="da790-214">System stored procedures are used for internal processing by the server and by the clients that Microsoft provides for interacting with the Analysis Services server.</span></span> <span data-ttu-id="da790-215">因此，Microsoft 保留随时更改它们的权利。</span><span class="sxs-lookup"><span data-stu-id="da790-215">Therefore, Microsoft reserves the right to change them at any time.</span></span> <span data-ttu-id="da790-216">虽然为方便起见在此处介绍了系统存储过程，但不建议在生产环境中使用它们。</span><span class="sxs-lookup"><span data-stu-id="da790-216">Although they are described here for your convenience, we do not support their use in a production environment.</span></span> <span data-ttu-id="da790-217">为了确保生产环境中的稳定性和兼容性，您应始终使用 DMX 编写您自己的查询。</span><span class="sxs-lookup"><span data-stu-id="da790-217">To ensure stability and compatibility in a production environment, you should always write your own queries by using DMX.</span></span>  
  
 <span data-ttu-id="da790-218">本节提供了如何使用系统存储过程来创建针对顺序分析和聚类分析模型的查询的一些示例：</span><span class="sxs-lookup"><span data-stu-id="da790-218">This section provides some samples of how to use the system stored procedures to create queries against a sequence clustering model:</span></span>  
  
#### <a name="cluster-profiles-and-sample-cases"></a><span data-ttu-id="da790-219">分类剖面图和样本事例</span><span class="sxs-lookup"><span data-stu-id="da790-219">Cluster Profiles and Sample Cases</span></span>  
 <span data-ttu-id="da790-220">“分类剖面图”选项卡显示了一个列表，列出模型中的分类、每个分类的大小以及指示该分类中包含的状态的直方图。</span><span class="sxs-lookup"><span data-stu-id="da790-220">The Cluster Profiles tab shows you a list of the clusters in the model, the size of each cluster, and a histogram that indicates the states included in the cluster.</span></span> <span data-ttu-id="da790-221">您可在查询中使用两个系统存储过程来检索类似信息：</span><span class="sxs-lookup"><span data-stu-id="da790-221">There are two system stored procedures that you can use in queries to retrieve similar information:</span></span>  
  
-   <span data-ttu-id="da790-222">`GetClusterProfile` 返回分类的特征以及在分类的 NODE_DISTRIBUTION 表中找到的所有信息。</span><span class="sxs-lookup"><span data-stu-id="da790-222">`GetClusterProfile` returns the characteristics of the cluster, with all the information that is found in the NODE_DISTRIBUTION table for the cluster.</span></span>  
  
-   <span data-ttu-id="da790-223">`GetNodeGraph` 返回可用于构造分类的数学图形表示形式的节点和边缘，这与您在“顺序分析和聚类分析”视图的第一个选项卡中所见的相对应。</span><span class="sxs-lookup"><span data-stu-id="da790-223">`GetNodeGraph` returns nodes and edges that can be used to construct a mathematical graph representation of the clusters, corresponding to what you see on the first tab of the Sequence Clustering view.</span></span> <span data-ttu-id="da790-224">节点代表分类，边缘代表权重或强度。</span><span class="sxs-lookup"><span data-stu-id="da790-224">The nodes are clusters, and the edges represent weights or strength.</span></span>  
  
 <span data-ttu-id="da790-225">下例演示了如何使用系统存储过程 `GetClusterProfiles`来返回模型中的所有分类及其各自的剖面图。</span><span class="sxs-lookup"><span data-stu-id="da790-225">The following example illustrates how to use the system stored procedure, `GetClusterProfiles`, to return all of the clusters in the model, with their respective profiles.</span></span> <span data-ttu-id="da790-226">此存储过程将执行一系列 DMX 语句，它们返回模型中完整的一组剖面图。</span><span class="sxs-lookup"><span data-stu-id="da790-226">This stored procedure executes a series of DMX statements that return the complete set of profiles in the model.</span></span> <span data-ttu-id="da790-227">但是，若要使用此存储过程，您必须知道模型的地址。</span><span class="sxs-lookup"><span data-stu-id="da790-227">However, to use this stored procedure you must know the address of the model.</span></span>  
  
 `CALL System.Microsoft.AnalysisServices.System.DataMining.Clustering.GetClusterProfiles('Sequence Clustering', 2147483647, 0)`  
  
 <span data-ttu-id="da790-228">下例演示了如何检索特定分类 Cluster 12 的剖面图，方法是使用系统存储过程 `GetNodeGraph`，然后指定分类 ID，该 ID 通常与分类名称中的数字相同。</span><span class="sxs-lookup"><span data-stu-id="da790-228">The following example illustrates how to retrieve the profile for a specific cluster, Cluster 12, by using the system stored procedure `GetNodeGraph`, and specifying the cluster ID, which is usually the same as the number in the cluster name.</span></span>  
  
```  
CALL System.Microsoft.AnalysisServices.System.DataMining.Clustering.GetNodeGraph('Sequence Clustering','12',0)  
```  
  
 <span data-ttu-id="da790-229">如果您如以下查询中所示省略分类 ID，则 `GetNodeGraph` 会返回所有分类剖面图的有序平展列表：</span><span class="sxs-lookup"><span data-stu-id="da790-229">If you omit the cluster ID, as shown in the following query, `GetNodeGraph` returns an ordered, flattened list of all cluster profiles:</span></span>  
  
```  
CALL System.Microsoft.AnalysisServices.System.DataMining.Clustering.GetNodeGraph('Sequence Clustering','',0)  
```  
  
 <span data-ttu-id="da790-230">**“分类剖面图”** 选项卡还显示了模型样本事例的直方图。</span><span class="sxs-lookup"><span data-stu-id="da790-230">The **Cluster Profile** tab also displays a histogram of model sample cases.</span></span> <span data-ttu-id="da790-231">这些样本事例代表模型的理想化事例。</span><span class="sxs-lookup"><span data-stu-id="da790-231">These sample cases represent the idealized cases for the model.</span></span> <span data-ttu-id="da790-232">这些事例在模型中的存储方式与定型数据不同；您必须使用特殊的语法来检索模型的样本事例。</span><span class="sxs-lookup"><span data-stu-id="da790-232">These cases are not stored in the model the same way that the training data is; you must use a special syntax to retrieve the sample cases for the model.</span></span>  
  
```  
SELECT * FROM [Sequence Clustering].SAMPLE_CASES WHERE IsInNode('12')  
```  
  
 <span data-ttu-id="da790-233">有关详细信息，请参阅 [SELECT FROM <模型>.SAMPLE_CASES (DMX)](/sql/dmx/select-from-model-dmx)。</span><span class="sxs-lookup"><span data-stu-id="da790-233">For more information, see [SELECT FROM &#60;model&#62;.SAMPLE_CASES &#40;DMX&#41;](/sql/dmx/select-from-model-dmx).</span></span>  
  
#### <a name="cluster-characteristics-and-cluster-discrimination"></a><span data-ttu-id="da790-234">分类特征和分类对比</span><span class="sxs-lookup"><span data-stu-id="da790-234">Cluster Characteristics and Cluster Discrimination</span></span>  
 <span data-ttu-id="da790-235">**“分类特征”** 选项卡汇总了每个分类的主属性，按概率进行排序。</span><span class="sxs-lookup"><span data-stu-id="da790-235">The **Cluster Characteristics** tab summarizes the main attributes of each cluster, ranked by probability.</span></span> <span data-ttu-id="da790-236">您可以查看属于一个分类的事例数，以及该分类中的事例分布情况：每个特征都有一定的支持。</span><span class="sxs-lookup"><span data-stu-id="da790-236">You can find out how many cases belong to a cluster, and what the distribution of cases is like in the cluster: Each characteristic has certain support.</span></span> <span data-ttu-id="da790-237">若要查看特定分类的特征，您必须知道该分类的 ID。</span><span class="sxs-lookup"><span data-stu-id="da790-237">To see the characteristics of a particular cluster, you must know the ID of the cluster.</span></span>  
  
 <span data-ttu-id="da790-238">以下示例使用系统存储过程 `GetClusterCharacteristics`返回概率值超过指定阈值 0.0005 的 Cluster 12 的所有特征。</span><span class="sxs-lookup"><span data-stu-id="da790-238">The following examples uses the system stored procedure, `GetClusterCharacteristics`, to return all the characteristics of Cluster 12 that have a probability score over the specified threshold of 0.0005.</span></span>  
  
```  
CALL System.Microsoft.AnalysisServices.System.DataMining.Clustering.GetClusterCharacteristics('Sequence Clustering','12',0.0005)  
```  
  
 <span data-ttu-id="da790-239">若要返回所有分类的特征，必须将分类 ID 保留为空。</span><span class="sxs-lookup"><span data-stu-id="da790-239">To return the characteristics of all clusters, you can leave the cluster ID empty.</span></span>  
  
```  
CALL System.Microsoft.AnalysisServices.System.DataMining.Clustering.GetClusterCharacteristics('Sequence Clustering','',0.0005)  
```  
  
 <span data-ttu-id="da790-240">下例调用系统存储过程 `GetClusterDiscrimination` 来比较 Cluster 1 和 Cluster 12 的特征。</span><span class="sxs-lookup"><span data-stu-id="da790-240">The following example calls the system stored procedure `GetClusterDiscrimination` to compare the characteristics of Cluster 1 and Cluster 12.</span></span>  
  
```  
CALL System.Microsoft.AnalysisServices.System.DataMining.Clustering.GetClusterDiscrimination('Sequence Clustering','1','12',0.0005,true)  
```  
  
 <span data-ttu-id="da790-241">如果您要使用 DMX 编写您自己的查询来比较两个分类，或将一个分类与其补进行比较，您必须首先检索一组特征，再检索您感兴趣的特定分类的特征，然后比较这两组特征。</span><span class="sxs-lookup"><span data-stu-id="da790-241">If you want to write your own query in DMX to compare two clusters, or compare a cluster with its complement, you must first retrieve one set of characteristics, and then retrieve the characteristics for the specific cluster that you are interested in, and compare the two sets.</span></span> <span data-ttu-id="da790-242">这种情况更为复杂，通常需要某些客户端处理。</span><span class="sxs-lookup"><span data-stu-id="da790-242">This scenario is more complicated and typically requires some client processing.</span></span>  
  
#### <a name="states-and-transitions"></a><span data-ttu-id="da790-243">状态和转换</span><span class="sxs-lookup"><span data-stu-id="da790-243">States and Transitions</span></span>  
 <span data-ttu-id="da790-244">Microsoft 顺序分析和聚类分析的 **“状态转换”** 选项卡会在后端执行复杂的查询以检索并比较不同分类的统计信息。</span><span class="sxs-lookup"><span data-stu-id="da790-244">The **State Transitions** tab of the Microsoft Sequence Clustering performs complicated queries on the back end to retrieve and compare the statistics for different clusters.</span></span> <span data-ttu-id="da790-245">重新生成这些结果需要更复杂的查询和一些客户端处理。</span><span class="sxs-lookup"><span data-stu-id="da790-245">To reproduce these results requires a more complex query and some client processing.</span></span>  
  
 <span data-ttu-id="da790-246">但是，可以使用 [内容查询](#bkmk_ContentQueries)部分的示例 2 中介绍的 DMX 查询来检索序列或各个转换的概率和状态。</span><span class="sxs-lookup"><span data-stu-id="da790-246">However, you can use the DMX queries described in Example 2 of the section, [Content Queries](#bkmk_ContentQueries), to retrieve probabilities and states for sequences or for individual transitions.</span></span>  
  
## <a name="using-the-model-to-make-predictions"></a><span data-ttu-id="da790-247">使用模型进行预测</span><span class="sxs-lookup"><span data-stu-id="da790-247">Using the Model to Make Predictions</span></span>  
 <span data-ttu-id="da790-248">针对顺序分析和聚类分析模型的预测查询可使用许多适用于其他聚类分析模型的预测函数。</span><span class="sxs-lookup"><span data-stu-id="da790-248">Prediction queries on a sequence clustering model can use many of the prediction functions that are used with other clustering models.</span></span> <span data-ttu-id="da790-249">此外，还可以使用特殊预测函数 [PredictSequence (DMX)](/sql/dmx/predictsequence-dmx)建议或推测下一状态。</span><span class="sxs-lookup"><span data-stu-id="da790-249">In addition, you can use the special prediction function, [PredictSequence &#40;DMX&#41;](/sql/dmx/predictsequence-dmx), to make recommendations or to predict next states.</span></span>  
  
###  <a name="sample-query-4-predict-next-state-or-states"></a><a name="bkmk_Query4"></a><span data-ttu-id="da790-250">示例查询4：预测下一状态或状态</span><span class="sxs-lookup"><span data-stu-id="da790-250">Sample Query 4: Predict Next State or States</span></span>  
 <span data-ttu-id="da790-251">在给定值的情况下，可以使用 [PredictSequence (DMX)](/sql/dmx/predictsequence-dmx) 函数来预测下一个最可能的状态。</span><span class="sxs-lookup"><span data-stu-id="da790-251">You can use the [PredictSequence &#40;DMX&#41;](/sql/dmx/predictsequence-dmx) function to predict the next most likely state, given a value.</span></span> <span data-ttu-id="da790-252">还可以预测多个下一状态：例如，可以返回客户可能购买的前三种产品，以提供一个建议列表。</span><span class="sxs-lookup"><span data-stu-id="da790-252">You can also predict multiple next states: for example, you can return a list of the top three products that a customer is likely to purchase, to present a list of recommendations.</span></span>  
  
 <span data-ttu-id="da790-253">下面的示例查询是一个单独预测查询，它将返回前 5 个预测及其概率。</span><span class="sxs-lookup"><span data-stu-id="da790-253">The following sample query is a singleton prediction query that returns the top five predictions, together with their probability.</span></span> <span data-ttu-id="da790-254">由于该模型包含一个嵌套表，因此进行预测时必须将嵌套表 `[v Assoc Seq Line Items]`用作列引用。</span><span class="sxs-lookup"><span data-stu-id="da790-254">Because the model includes a nested table, you must use the nested table, `[v Assoc Seq Line Items]`, as the column reference when making predictions.</span></span> <span data-ttu-id="da790-255">此外，提供输入值时，必须联接事例表和嵌套表列，如嵌套 SELECT 语句所示。</span><span class="sxs-lookup"><span data-stu-id="da790-255">Also, when you supply values as input, you must join both the case table and the nested table columns, as shown by the nested SELECT statements.</span></span>  
  
```  
SELECT FLATTENED PredictSequence([v Assoc Seq Line Items], 7)  
FROM [Sequence Clustering]  
NATURAL PREDICTION JOIN  
(SELECT  (SELECT 1 as [Line Number],  
   'All-Purpose Bike Stand' as [Model]) AS [v Assoc Seq Line Items])   
AS t  
```  
  
 <span data-ttu-id="da790-256">示例结果：</span><span class="sxs-lookup"><span data-stu-id="da790-256">Example results:</span></span>  
  
|<span data-ttu-id="da790-257">Expression.$Sequence</span><span class="sxs-lookup"><span data-stu-id="da790-257">Expression.$Sequence</span></span>|<span data-ttu-id="da790-258">Expression.Line Number</span><span class="sxs-lookup"><span data-stu-id="da790-258">Expression.Line Number</span></span>|<span data-ttu-id="da790-259">Expression.Model</span><span class="sxs-lookup"><span data-stu-id="da790-259">Expression.Model</span></span>|  
|--------------------------|----------------------------|----------------------|  
|<span data-ttu-id="da790-260">1</span><span class="sxs-lookup"><span data-stu-id="da790-260">1</span></span>||<span data-ttu-id="da790-261">Cycling Cap</span><span class="sxs-lookup"><span data-stu-id="da790-261">Cycling Cap</span></span>|  
|<span data-ttu-id="da790-262">2</span><span class="sxs-lookup"><span data-stu-id="da790-262">2</span></span>||<span data-ttu-id="da790-263">Cycling Cap</span><span class="sxs-lookup"><span data-stu-id="da790-263">Cycling Cap</span></span>|  
|<span data-ttu-id="da790-264">3</span><span class="sxs-lookup"><span data-stu-id="da790-264">3</span></span>||<span data-ttu-id="da790-265">Sport-100</span><span class="sxs-lookup"><span data-stu-id="da790-265">Sport-100</span></span>|  
|<span data-ttu-id="da790-266">4</span><span class="sxs-lookup"><span data-stu-id="da790-266">4</span></span>||<span data-ttu-id="da790-267">Long-Sleeve Logo Jersey</span><span class="sxs-lookup"><span data-stu-id="da790-267">Long-Sleeve logo Jersey</span></span>|  
|<span data-ttu-id="da790-268">5</span><span class="sxs-lookup"><span data-stu-id="da790-268">5</span></span>||<span data-ttu-id="da790-269">Half-Finger Gloves</span><span class="sxs-lookup"><span data-stu-id="da790-269">Half-Finger Gloves</span></span>|  
|<span data-ttu-id="da790-270">6</span><span class="sxs-lookup"><span data-stu-id="da790-270">6</span></span>||<span data-ttu-id="da790-271">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="da790-271">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="da790-272">7</span><span class="sxs-lookup"><span data-stu-id="da790-272">7</span></span>||<span data-ttu-id="da790-273">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="da790-273">All-Purpose Bike Stand</span></span>|  
  
 <span data-ttu-id="da790-274">尽管您可能仅需要一列，但结果中包含三列，因为查询会始终为事例表返回一列。</span><span class="sxs-lookup"><span data-stu-id="da790-274">There are three columns in the results, even though you might only expect one column, because the query always returns a column for the case table.</span></span> <span data-ttu-id="da790-275">此处的结果是平展的；否则，查询将返回包含两个嵌套表列的单个列。</span><span class="sxs-lookup"><span data-stu-id="da790-275">Here the results are flattened; otherwise, the query would return a single column that contains two nested table columns.</span></span>  
  
 <span data-ttu-id="da790-276">列 $sequence 是由 `PredictSequence` 函数默认返回的列，以对预测结果进行排序。</span><span class="sxs-lookup"><span data-stu-id="da790-276">The column $sequence is a column returned by default by the `PredictSequence` function to order the prediction results.</span></span> <span data-ttu-id="da790-277">对模型中的序列键进行匹配时需要 `[Line Number]`列，但不输出这些序列键。</span><span class="sxs-lookup"><span data-stu-id="da790-277">The column, `[Line Number]`, is required to match the sequence keys in the model, but the keys are not output.</span></span>  
  
 <span data-ttu-id="da790-278">有趣的是，购买 All-Purpose Bike Stand 之后的最前面两个预测序列是 Cycling Cap 和 Cycling Cap。</span><span class="sxs-lookup"><span data-stu-id="da790-278">Interestingly, the top predicted sequences after All-Purpose Bike Stand are Cycling Cap and Cycling Cap.</span></span> <span data-ttu-id="da790-279">这不是一个错误。</span><span class="sxs-lookup"><span data-stu-id="da790-279">This is not an error.</span></span> <span data-ttu-id="da790-280">这种序列很可能出现，具体取决于向客户显示数据的方式以及为模型定型时数据的分组方式。</span><span class="sxs-lookup"><span data-stu-id="da790-280">Depending on how the data is presented to the customer, and how it is grouped when training the model, it is very possible to have sequences of this kind.</span></span> <span data-ttu-id="da790-281">例如，客户可能购买一顶红色的自行车帽，再购买一顶蓝色的自行车帽，在无法指定数量的情况下，就会在一行中出现两次购买自行车帽。</span><span class="sxs-lookup"><span data-stu-id="da790-281">For example, a customer might purchase a cycling cap (red) and then another cycling cap (blue), or purchase two in a row if there were no way to specify quantity.</span></span>  
  
 <span data-ttu-id="da790-282">第 6 行和第 7 行中的值为占位符。</span><span class="sxs-lookup"><span data-stu-id="da790-282">The values in rows 6 and 7 are placeholders.</span></span> <span data-ttu-id="da790-283">当您到达可能的转换的链末尾，而不是终止预测结果时，作为输入传递的值将添加到结果中。</span><span class="sxs-lookup"><span data-stu-id="da790-283">When you reach the end of the chain of possible transitions, rather than terminating the prediction results, the value that was passed as an input is added to the results.</span></span> <span data-ttu-id="da790-284">例如，如果将预测数增加到 20，则第 6 行到第 20 行的值是一样的，全部为 All-Purpose Bike Stand。</span><span class="sxs-lookup"><span data-stu-id="da790-284">For example, if you increased the number of predictions to 20, the values for rows 6-20 would all be the same, All-Purpose Bike Stand.</span></span>  
  
## <a name="function-list"></a><span data-ttu-id="da790-285">函数列表</span><span class="sxs-lookup"><span data-stu-id="da790-285">Function List</span></span>  
 <span data-ttu-id="da790-286">所有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 算法均支持一组通用的函数。</span><span class="sxs-lookup"><span data-stu-id="da790-286">All [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms support a common set of functions.</span></span> <span data-ttu-id="da790-287">此外， [!INCLUDE[msCoName](../../includes/msconame-md.md)] 顺序分析和聚类分析算法还额外支持下表中列出的函数。</span><span class="sxs-lookup"><span data-stu-id="da790-287">However, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering algorithm supports the additional functions that are listed in the following table.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="da790-288">预测函数</span><span class="sxs-lookup"><span data-stu-id="da790-288">Prediction Function</span></span>|<span data-ttu-id="da790-289">使用情况</span><span class="sxs-lookup"><span data-stu-id="da790-289">Usage</span></span>|  
|[<span data-ttu-id="da790-290">分类 (DMX)</span><span class="sxs-lookup"><span data-stu-id="da790-290">Cluster &#40;DMX&#41;</span></span>](/sql/dmx/cluster-dmx)|<span data-ttu-id="da790-291">返回最可能包含输入事例的分类</span><span class="sxs-lookup"><span data-stu-id="da790-291">Returns the cluster that is most likely to contain the input case</span></span>|  
|[<span data-ttu-id="da790-292">ClusterDistance (DMX)</span><span class="sxs-lookup"><span data-stu-id="da790-292">ClusterDistance &#40;DMX&#41;</span></span>](/sql/dmx/clusterdistance-dmx)|<span data-ttu-id="da790-293">返回输入事例与指定分类之间的距离；如果未指定分类，则返回输入事例与可能性最大的分类之间的距离。</span><span class="sxs-lookup"><span data-stu-id="da790-293">Returns the distance of the input case from the specified cluster, or if no cluster is specified, the distance of the input case from the most likely cluster.</span></span><br /><br /> <span data-ttu-id="da790-294">此函数可用于任何类型的聚类分析模型（EM、K-Means 等），但结果会因算法而异。</span><span class="sxs-lookup"><span data-stu-id="da790-294">This function can be used with any kind of clustering model (EM, K-Means, etc.), but the results differ depending on the algorithm.</span></span>|  
|[<span data-ttu-id="da790-295">ClusterProbability (DMX)</span><span class="sxs-lookup"><span data-stu-id="da790-295">ClusterProbability &#40;DMX&#41;</span></span>](/sql/dmx/clusterprobability-dmx)|<span data-ttu-id="da790-296">返回输入事例属于指定分类的概率。</span><span class="sxs-lookup"><span data-stu-id="da790-296">Returns the probability that the input case belongs to the specified cluster.</span></span>|  
|[<span data-ttu-id="da790-297">IsInNode (DMX)</span><span class="sxs-lookup"><span data-stu-id="da790-297">IsInNode &#40;DMX&#41;</span></span>](/sql/dmx/isinnode-dmx)|<span data-ttu-id="da790-298">指示指定的节点是否包含当前事例。</span><span class="sxs-lookup"><span data-stu-id="da790-298">Indicates whether the specified node contains the current case.</span></span>|  
|[<span data-ttu-id="da790-299">PredictAdjustedProbability (DMX)</span><span class="sxs-lookup"><span data-stu-id="da790-299">PredictAdjustedProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictadjustedprobability-dmx)|<span data-ttu-id="da790-300">返回指定状态调整后的概率。</span><span class="sxs-lookup"><span data-stu-id="da790-300">Returns the adjusted probability of a specified state.</span></span>|  
|[<span data-ttu-id="da790-301">PredictAssociation (DMX)</span><span class="sxs-lookup"><span data-stu-id="da790-301">PredictAssociation &#40;DMX&#41;</span></span>](/sql/dmx/predictassociation-dmx)|<span data-ttu-id="da790-302">预测关联的成员身份。</span><span class="sxs-lookup"><span data-stu-id="da790-302">Predicts associative membership.</span></span>|  
|[<span data-ttu-id="da790-303">PredictCaseLikelihood (DMX)</span><span class="sxs-lookup"><span data-stu-id="da790-303">PredictCaseLikelihood &#40;DMX&#41;</span></span>](/sql/dmx/predictcaselikelihood-dmx)|<span data-ttu-id="da790-304">返回输入事例适合现有模型的可能性。</span><span class="sxs-lookup"><span data-stu-id="da790-304">Returns the likelihood that an input case will fit in the existing model.</span></span>|  
|[<span data-ttu-id="da790-305">PredictHistogram (DMX)</span><span class="sxs-lookup"><span data-stu-id="da790-305">PredictHistogram &#40;DMX&#41;</span></span>](/sql/dmx/predicthistogram-dmx)|<span data-ttu-id="da790-306">返回一个表示给定列预测的直方图的表。</span><span class="sxs-lookup"><span data-stu-id="da790-306">Returns a table that represents a histogram for the prediction of a given column.</span></span>|  
|[<span data-ttu-id="da790-307">PredictNodeId (DMX)</span><span class="sxs-lookup"><span data-stu-id="da790-307">PredictNodeId &#40;DMX&#41;</span></span>](/sql/dmx/predictnodeid-dmx)|<span data-ttu-id="da790-308">返回事例所属的节点的 Node_ID。</span><span class="sxs-lookup"><span data-stu-id="da790-308">Returns the Node_ID of the node to which the case is classified.</span></span>|  
|[<span data-ttu-id="da790-309">PredictProbability (DMX)</span><span class="sxs-lookup"><span data-stu-id="da790-309">PredictProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictprobability-dmx)|<span data-ttu-id="da790-310">返回指定状态的概率。</span><span class="sxs-lookup"><span data-stu-id="da790-310">Returns the probability for a specified state.</span></span>|  
|[<span data-ttu-id="da790-311">PredictSequence (DMX)</span><span class="sxs-lookup"><span data-stu-id="da790-311">PredictSequence &#40;DMX&#41;</span></span>](/sql/dmx/predictsequence-dmx)|<span data-ttu-id="da790-312">为一组指定的序列数据预测将来的序列值。</span><span class="sxs-lookup"><span data-stu-id="da790-312">Predicts future sequence values for a specified set of sequence data.</span></span>|  
|[<span data-ttu-id="da790-313">PredictStdev (DMX)</span><span class="sxs-lookup"><span data-stu-id="da790-313">PredictStdev &#40;DMX&#41;</span></span>](/sql/dmx/predictstdev-dmx)|<span data-ttu-id="da790-314">返回指定列的预测标准偏差。</span><span class="sxs-lookup"><span data-stu-id="da790-314">Returns the predicted standard deviation for the specified column.</span></span>|  
|[<span data-ttu-id="da790-315">PredictSupport (DMX)</span><span class="sxs-lookup"><span data-stu-id="da790-315">PredictSupport &#40;DMX&#41;</span></span>](/sql/dmx/predictsupport-dmx)|<span data-ttu-id="da790-316">返回指定状态的支持值。</span><span class="sxs-lookup"><span data-stu-id="da790-316">Returns the support value for a specified state.</span></span>|  
|[<span data-ttu-id="da790-317">PredictVariance (DMX)</span><span class="sxs-lookup"><span data-stu-id="da790-317">PredictVariance &#40;DMX&#41;</span></span>](/sql/dmx/predictvariance-dmx)|<span data-ttu-id="da790-318">返回指定列的方差。</span><span class="sxs-lookup"><span data-stu-id="da790-318">Returns the variance of a specified column.</span></span>|  
  
 <span data-ttu-id="da790-319">有关所有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 算法都支持的通用函数的列表，请参阅[通用预测函数 (DMX)](/sql/dmx/general-prediction-functions-dmx)。</span><span class="sxs-lookup"><span data-stu-id="da790-319">For a list of the functions that are common to all [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms, see [General Prediction Functions &#40;DMX&#41;](/sql/dmx/general-prediction-functions-dmx).</span></span> <span data-ttu-id="da790-320">有关特定函数的语法，请参阅[数据挖掘扩展插件 (DMX) 函数引用](/sql/dmx/data-mining-extensions-dmx-function-reference)。</span><span class="sxs-lookup"><span data-stu-id="da790-320">For the syntax of specific functions, see [Data Mining Extensions &#40;DMX&#41; Function Reference](/sql/dmx/data-mining-extensions-dmx-function-reference).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da790-321">另请参阅</span><span class="sxs-lookup"><span data-stu-id="da790-321">See Also</span></span>  
 <span data-ttu-id="da790-322">[数据挖掘查询](data-mining-queries.md) </span><span class="sxs-lookup"><span data-stu-id="da790-322">[Data Mining Queries](data-mining-queries.md) </span></span>  
 <span data-ttu-id="da790-323">[Microsoft 顺序分析和聚类分析算法技术参考](microsoft-sequence-clustering-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="da790-323">[Microsoft Sequence Clustering Algorithm Technical Reference](microsoft-sequence-clustering-algorithm-technical-reference.md) </span></span>  
 <span data-ttu-id="da790-324">[Microsoft 顺序分析和聚类分析算法](microsoft-sequence-clustering-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="da790-324">[Microsoft Sequence Clustering Algorithm](microsoft-sequence-clustering-algorithm.md) </span></span>  
 [<span data-ttu-id="da790-325">顺序分析和聚类分析模型的挖掘模型内容（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="da790-325">Mining Model Content for Sequence Clustering Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-sequence-clustering-models.md)  
  
  
