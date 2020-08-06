---
title: 聚类分析模型查询示例 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- clustering [Data Mining]
- content queries [DMX]
- clustering algorithms [Analysis Services]
ms.assetid: bf2ba332-9bc6-411a-a3af-b919c52432c8
author: minewiskan
ms.author: owend
ms.openlocfilehash: fe12b82ce2d237acd060b1e387e7a6dfbf958851
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591673"
---
# <a name="clustering-model-query-examples"></a><span data-ttu-id="e75c5-102">聚类分析模型查询示例</span><span class="sxs-lookup"><span data-stu-id="e75c5-102">Clustering Model Query Examples</span></span>
  <span data-ttu-id="e75c5-103">依据数据挖掘模型创建查询时，可以检索有关模型的元数据，或者创建内容查询以提供有关分析时发现的模式的详细信息。</span><span class="sxs-lookup"><span data-stu-id="e75c5-103">When you create a query against a data mining model, you can retrieve metadata about the model, or create a content query that provides details about the patterns discovered in analysis.</span></span> <span data-ttu-id="e75c5-104">或者，可以创建预测查询，以使用模型中的模式来对新数据进行预测。</span><span class="sxs-lookup"><span data-stu-id="e75c5-104">Alternatively, you can create a prediction query, which uses the patterns in the model to make predictions for new data.</span></span> <span data-ttu-id="e75c5-105">每一类查询都提供不同的信息。</span><span class="sxs-lookup"><span data-stu-id="e75c5-105">Each type of query will provide different information.</span></span> <span data-ttu-id="e75c5-106">例如，内容查询可能提供有关发现的分类的更多详细信息，而预测查询可能指出新数据点最有可能属于哪个分类。</span><span class="sxs-lookup"><span data-stu-id="e75c5-106">For example, a content query might provide additional details about the clusters that were found, whereas a prediction query might tell you in which cluster a new data point is most likely to belong.</span></span>  
  
 <span data-ttu-id="e75c5-107">本节说明如何为基于 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 聚类分析算法的模型创建查询。</span><span class="sxs-lookup"><span data-stu-id="e75c5-107">This section explains how to create queries for models that are based on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Clustering algorithm.</span></span>  
  
 <span data-ttu-id="e75c5-108">**内容查询**</span><span class="sxs-lookup"><span data-stu-id="e75c5-108">**Content Queries**</span></span>  
  
 [<span data-ttu-id="e75c5-109">使用 DMX 获取模型元数据</span><span class="sxs-lookup"><span data-stu-id="e75c5-109">Getting Model Metadata by Using DMX</span></span>](#bkmk_Query1)  
  
 [<span data-ttu-id="e75c5-110">从架构行集中检索模型元数据</span><span class="sxs-lookup"><span data-stu-id="e75c5-110">Retrieving Model Metadata from the Schema Rowset</span></span>](#bkmk_Query2)  
  
 [<span data-ttu-id="e75c5-111">返回分类或分类列表</span><span class="sxs-lookup"><span data-stu-id="e75c5-111">Returning a Cluster or a List of Clusters</span></span>](#bkmk_Query3)  
  
 [<span data-ttu-id="e75c5-112">返回分类的属性</span><span class="sxs-lookup"><span data-stu-id="e75c5-112">Returning Attributes for a Cluster</span></span>](#bkmk_Query4)  
  
 [<span data-ttu-id="e75c5-113">使用系统存储过程返回分类配置文件</span><span class="sxs-lookup"><span data-stu-id="e75c5-113">Returning a Cluster Profile Using System Stored Procedures</span></span>](#bkmk_Query5)  
  
 [<span data-ttu-id="e75c5-114">查找分类的对比因子</span><span class="sxs-lookup"><span data-stu-id="e75c5-114">Finding Discriminating Factors for a Cluster</span></span>](#bkmk_Query6)  
  
 [<span data-ttu-id="e75c5-115">返回属于分类的事例</span><span class="sxs-lookup"><span data-stu-id="e75c5-115">Returning Cases that Belong to a Cluster</span></span>](#bkmk_Query7)  
  
 <span data-ttu-id="e75c5-116">**预测查询**</span><span class="sxs-lookup"><span data-stu-id="e75c5-116">**Prediction Queries**</span></span>  
  
 [<span data-ttu-id="e75c5-117">从聚类分析模型中预测结果</span><span class="sxs-lookup"><span data-stu-id="e75c5-117">Predicting Outcomes from a Clustering Model</span></span>](#bkmk_Query8)  
  
 [<span data-ttu-id="e75c5-118">确定分类成员身份</span><span class="sxs-lookup"><span data-stu-id="e75c5-118">Determining Cluster Membership</span></span>](#bkmk_Query9)  
  
 [<span data-ttu-id="e75c5-119">返回具有概率和距离的所有可能分类</span><span class="sxs-lookup"><span data-stu-id="e75c5-119">Returning All Possible Clusters with Probability and Distance</span></span>](#bkmk_Query10)  
  
##  <a name="finding-information-about-the-model"></a><a name="bkmk_top2"></a> <span data-ttu-id="e75c5-120">查找有关模型的信息</span><span class="sxs-lookup"><span data-stu-id="e75c5-120">Finding Information about the Model</span></span>  
 <span data-ttu-id="e75c5-121">所有挖掘模型都公开算法根据标准化架构（即挖掘模型架构行集）学习的内容。</span><span class="sxs-lookup"><span data-stu-id="e75c5-121">All mining models expose the content learned by the algorithm according to a standardized schema, the mining model schema rowset.</span></span> <span data-ttu-id="e75c5-122">可以使用数据挖掘扩展插件 (DMX) 语句来针对挖掘模型架构行集创建查询。</span><span class="sxs-lookup"><span data-stu-id="e75c5-122">You can create queries against the mining model schema rowset by using Data Mining Extension (DMX) statements.</span></span> <span data-ttu-id="e75c5-123">在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中，还可以直接将架构行集作为系统表来查询。</span><span class="sxs-lookup"><span data-stu-id="e75c5-123">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you can also query the schema rowsets directly as system tables.</span></span>  
  
 [<span data-ttu-id="e75c5-124">返回页首</span><span class="sxs-lookup"><span data-stu-id="e75c5-124">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-1-getting-model-metadata-by-using-dmx"></a><a name="bkmk_Query1"></a> <span data-ttu-id="e75c5-125">示例查询 1：使用 DMX 获取模型元数据</span><span class="sxs-lookup"><span data-stu-id="e75c5-125">Sample Query 1: Getting Model Metadata by Using DMX</span></span>  
 <span data-ttu-id="e75c5-126">下面的查询返回您在基本数据挖掘教程中创建的聚类分析模型 `TM_Clustering`的基本元数据。</span><span class="sxs-lookup"><span data-stu-id="e75c5-126">The following query returns basic metadata about the clustering model, `TM_Clustering`, that you created in the Basic Data Mining Tutorial.</span></span> <span data-ttu-id="e75c5-127">聚类分析模型的父节点中可用的元数据包括模型的名称、存储模型的数据库以及模型中的子节点数目。</span><span class="sxs-lookup"><span data-stu-id="e75c5-127">The metadata available in the parent node of a clustering model includes the name of the model, the database where the model is stored, and the number of child nodes in the model.</span></span> <span data-ttu-id="e75c5-128">此查询使用 DMX 内容查询从模型的父节点中检索元数据：</span><span class="sxs-lookup"><span data-stu-id="e75c5-128">This query uses a DMX content query to retrieve the metadata from the parent node of the model:</span></span>  
  
```  
SELECT MODEL_CATALOG, MODEL_NAME, NODE_CAPTION,   
NODE_SUPPORT, [CHILDREN_CARDINALITY], NODE_DESCRIPTION  
FROM TM_Clustering.CONTENT  
WHERE NODE_TYPE = 1  
```  
  
> [!NOTE]  
>  <span data-ttu-id="e75c5-129">必须将列名 CHILDREN_CARDINALITY 括在括号中，以便将它与同名的多维表达式 (MDX) 保留关键字区分开来。</span><span class="sxs-lookup"><span data-stu-id="e75c5-129">You must enclose the name of the column, CHILDREN_CARDINALITY, in brackets to distinguish it from the Multidimensional Expressions (MDX) reserved keyword of the same name.</span></span>  
  
 <span data-ttu-id="e75c5-130">示例结果：</span><span class="sxs-lookup"><span data-stu-id="e75c5-130">Example results:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e75c5-131">MODEL_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e75c5-131">MODEL_CATALOG</span></span>|<span data-ttu-id="e75c5-132">TM_Clustering</span><span class="sxs-lookup"><span data-stu-id="e75c5-132">TM_Clustering</span></span>|  
|<span data-ttu-id="e75c5-133">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="e75c5-133">MODEL_NAME</span></span>|<span data-ttu-id="e75c5-134">Adventure Works DW</span><span class="sxs-lookup"><span data-stu-id="e75c5-134">Adventure Works DW</span></span>|  
|<span data-ttu-id="e75c5-135">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="e75c5-135">NODE_CAPTION</span></span>|<span data-ttu-id="e75c5-136">群集模型</span><span class="sxs-lookup"><span data-stu-id="e75c5-136">Cluster Model</span></span>|  
|<span data-ttu-id="e75c5-137">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="e75c5-137">NODE_SUPPORT</span></span>|<span data-ttu-id="e75c5-138">12939</span><span class="sxs-lookup"><span data-stu-id="e75c5-138">12939</span></span>|  
|<span data-ttu-id="e75c5-139">CHILDREN_CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="e75c5-139">CHILDREN_CARDINALITY</span></span>|<span data-ttu-id="e75c5-140">10</span><span class="sxs-lookup"><span data-stu-id="e75c5-140">10</span></span>|  
|<span data-ttu-id="e75c5-141">NODE_DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e75c5-141">NODE_DESCRIPTION</span></span>|<span data-ttu-id="e75c5-142">全部</span><span class="sxs-lookup"><span data-stu-id="e75c5-142">All</span></span>|  
  
 <span data-ttu-id="e75c5-143">有关这些列在聚类分析模型中的含义的定义，请参阅[聚类分析模型的挖掘模型内容（Analysis Services - 数据挖掘）](mining-model-content-for-clustering-models-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="e75c5-143">For a definition of what these columns mean in a clustering model, see [Mining Model Content for Clustering Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-clustering-models-analysis-services-data-mining.md).</span></span>  
  
 [<span data-ttu-id="e75c5-144">返回页首</span><span class="sxs-lookup"><span data-stu-id="e75c5-144">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-2-retrieving-model-metadata-from-the-schema-rowset"></a><a name="bkmk_Query2"></a> <span data-ttu-id="e75c5-145">示例查询 2：从架构行集中检索模型元数据</span><span class="sxs-lookup"><span data-stu-id="e75c5-145">Sample Query 2: Retrieving Model Metadata from the Schema Rowset</span></span>  
 <span data-ttu-id="e75c5-146">通过查询数据挖掘架构行集，可以找到在 DMX 内容查询中返回的相同信息。</span><span class="sxs-lookup"><span data-stu-id="e75c5-146">By querying the data mining schema rowset, you can find the same information that is returned in a DMX content query.</span></span> <span data-ttu-id="e75c5-147">但是，架构行集还提供一些额外的列。</span><span class="sxs-lookup"><span data-stu-id="e75c5-147">However, the schema rowset provides some additional columns.</span></span> <span data-ttu-id="e75c5-148">这包括创建模型时使用的参数、上次处理模型的日期和时间以及模型的所有者。</span><span class="sxs-lookup"><span data-stu-id="e75c5-148">These include the parameters that were used when the model was created, the date and time that the model was last processed, and the owner of the model.</span></span>  
  
 <span data-ttu-id="e75c5-149">下面的示例返回创建、修改和上次处理模型的日期，以及用于生成模型的聚类分析参数和定型集的大小。</span><span class="sxs-lookup"><span data-stu-id="e75c5-149">The following example returns the date the model was created, modified, and last processed, together with the clustering parameters that were used to build the model, and the size of the training set.</span></span> <span data-ttu-id="e75c5-150">这些信息对于模型的归档或者确定使用了哪些聚类分析选项来创建现有模型很有用。</span><span class="sxs-lookup"><span data-stu-id="e75c5-150">This information can be useful for documenting the model, or for determining which of the clustering options were used to create an existing model.</span></span>  
  
```  
SELECT MODEL_NAME, DATE_CREATED, LAST_PROCESSED, PREDICTION_ENTITY, MINING_PARAMETERS   
from $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'TM_Clustering'  
```  
  
 <span data-ttu-id="e75c5-151">示例结果：</span><span class="sxs-lookup"><span data-stu-id="e75c5-151">Example results:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e75c5-152">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="e75c5-152">MODEL_NAME</span></span>|<span data-ttu-id="e75c5-153">TM_Clustering</span><span class="sxs-lookup"><span data-stu-id="e75c5-153">TM_Clustering</span></span>|  
|<span data-ttu-id="e75c5-154">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="e75c5-154">DATE_CREATED</span></span>|<span data-ttu-id="e75c5-155">10/12/2007 7:42:51 PM</span><span class="sxs-lookup"><span data-stu-id="e75c5-155">10/12/2007 7:42:51 PM</span></span>|  
|<span data-ttu-id="e75c5-156">LAST_PROCESSED</span><span class="sxs-lookup"><span data-stu-id="e75c5-156">LAST_PROCESSED</span></span>|<span data-ttu-id="e75c5-157">10/12/2007 8:09:54 PM</span><span class="sxs-lookup"><span data-stu-id="e75c5-157">10/12/2007 8:09:54 PM</span></span>|  
|<span data-ttu-id="e75c5-158">PREDICTION_ENTITY</span><span class="sxs-lookup"><span data-stu-id="e75c5-158">PREDICTION_ENTITY</span></span>|<span data-ttu-id="e75c5-159">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="e75c5-159">Bike Buyer</span></span>|  
|<span data-ttu-id="e75c5-160">MINING_PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e75c5-160">MINING_PARAMETERS</span></span>|<span data-ttu-id="e75c5-161">CLUSTER_COUNT=10,</span><span class="sxs-lookup"><span data-stu-id="e75c5-161">CLUSTER_COUNT=10,</span></span><br /><br /> <span data-ttu-id="e75c5-162">CLUSTER_SEED=0,</span><span class="sxs-lookup"><span data-stu-id="e75c5-162">CLUSTER_SEED=0,</span></span><br /><br /> <span data-ttu-id="e75c5-163">CLUSTERING_METHOD=1,</span><span class="sxs-lookup"><span data-stu-id="e75c5-163">CLUSTERING_METHOD=1,</span></span><br /><br /> <span data-ttu-id="e75c5-164">MAXIMUM_INPUT_ATTRIBUTES=255,</span><span class="sxs-lookup"><span data-stu-id="e75c5-164">MAXIMUM_INPUT_ATTRIBUTES=255,</span></span><br /><br /> <span data-ttu-id="e75c5-165">MAXIMUM_STATES=100,</span><span class="sxs-lookup"><span data-stu-id="e75c5-165">MAXIMUM_STATES=100,</span></span><br /><br /> <span data-ttu-id="e75c5-166">MINIMUM_SUPPORT=1,</span><span class="sxs-lookup"><span data-stu-id="e75c5-166">MINIMUM_SUPPORT=1,</span></span><br /><br /> <span data-ttu-id="e75c5-167">MODELLING_CARDINALITY=10,</span><span class="sxs-lookup"><span data-stu-id="e75c5-167">MODELLING_CARDINALITY=10,</span></span><br /><br /> <span data-ttu-id="e75c5-168">SAMPLE_SIZE=50000,</span><span class="sxs-lookup"><span data-stu-id="e75c5-168">SAMPLE_SIZE=50000,</span></span><br /><br /> <span data-ttu-id="e75c5-169">STOPPING_TOLERANCE=10</span><span class="sxs-lookup"><span data-stu-id="e75c5-169">STOPPING_TOLERANCE=10</span></span>|  
  
 [<span data-ttu-id="e75c5-170">返回页首</span><span class="sxs-lookup"><span data-stu-id="e75c5-170">Return to Top</span></span>](#bkmk_top2)  
  
## <a name="finding-information-about-clusters"></a><span data-ttu-id="e75c5-171">查找有关分类的信息</span><span class="sxs-lookup"><span data-stu-id="e75c5-171">Finding Information about Clusters</span></span>  
 <span data-ttu-id="e75c5-172">聚类分析模型中最有用的内容查询通常返回与使用 **“分类查看器”** 可浏览的信息同类的信息。</span><span class="sxs-lookup"><span data-stu-id="e75c5-172">The most useful content queries on clustering models generally return the same type of information that you can browse by using the **Cluster Viewer**.</span></span> <span data-ttu-id="e75c5-173">这包括分类配置文件、分类特征以及分类对比。</span><span class="sxs-lookup"><span data-stu-id="e75c5-173">This includes cluster profiles, cluster characteristics, and cluster discrimination.</span></span> <span data-ttu-id="e75c5-174">本节提供检索这些信息的查询示例。</span><span class="sxs-lookup"><span data-stu-id="e75c5-174">This section provides examples of queries that retrieve this information.</span></span>  
  
###  <a name="sample-query-3-returning-a-cluster-or-list-of-clusters"></a><a name="bkmk_Query3"></a> <span data-ttu-id="e75c5-175">示例查询 3：返回分类或分类列表</span><span class="sxs-lookup"><span data-stu-id="e75c5-175">Sample Query 3: Returning a Cluster or List of Clusters</span></span>  
 <span data-ttu-id="e75c5-176">因为所有分类的节点类型都为 5，所以通过仅仅查询该类型的节点的模型内容可轻松地检索分类的列表。</span><span class="sxs-lookup"><span data-stu-id="e75c5-176">Because all clusters have a node type of 5, you can easily retrieve a list of the clusters by querying the model content for only the nodes of that type.</span></span> <span data-ttu-id="e75c5-177">您还可以筛选按概率或支持所返回的节点，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="e75c5-177">You can also filter the nodes that are returned by probability or by support, as shown in this example.</span></span>  
  
```  
SELECT NODE_NAME, NODE_CAPTION ,NODE_SUPPORT, NODE_DESCRIPTION  
FROM TM_Clustering.CONTENT  
WHERE NODE_TYPE = 5 AND NODE_SUPPORT > 1000  
```  
  
 <span data-ttu-id="e75c5-178">示例结果：</span><span class="sxs-lookup"><span data-stu-id="e75c5-178">Example results:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e75c5-179">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="e75c5-179">NODE_NAME</span></span>|<span data-ttu-id="e75c5-180">002</span><span class="sxs-lookup"><span data-stu-id="e75c5-180">002</span></span>|  
|<span data-ttu-id="e75c5-181">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="e75c5-181">NODE_CAPTION</span></span>|<span data-ttu-id="e75c5-182">Cluster 2</span><span class="sxs-lookup"><span data-stu-id="e75c5-182">Cluster 2</span></span>|  
|<span data-ttu-id="e75c5-183">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="e75c5-183">NODE_SUPPORT</span></span>|<span data-ttu-id="e75c5-184">1649</span><span class="sxs-lookup"><span data-stu-id="e75c5-184">1649</span></span>|  
|<span data-ttu-id="e75c5-185">NODE_DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e75c5-185">NODE_DESCRIPTION</span></span>|<span data-ttu-id="e75c5-186">English Education=Graduate Degree , 32 <=Age <=48 , Number Cars Owned=0 , 35964.0771121808 <=Yearly Income <=97407.7163393957 , English Occupation=Professional , Commute Distance=2-5 Miles , Region=North America , Bike Buyer=1 , Number Children At Home=0 , Number Cars Owned=1 , Commute Distance=0-1 Miles , English Education=Bachelors , Total Children=1 , Number Children At Home=2 , English Occupation=Skilled Manual , Marital Status=S , Total Children=0 , House Owner Flag=0 , Gender=F , Total Children=2 , Region=Pacific</span><span class="sxs-lookup"><span data-stu-id="e75c5-186">English Education=Graduate Degree , 32 <=Age <=48 , Number Cars Owned=0 , 35964.0771121808 <=Yearly Income <=97407.7163393957 , English Occupation=Professional , Commute Distance=2-5 Miles , Region=North America , Bike Buyer=1 , Number Children At Home=0 , Number Cars Owned=1 , Commute Distance=0-1 Miles , English Education=Bachelors , Total Children=1 , Number Children At Home=2 , English Occupation=Skilled Manual , Marital Status=S , Total Children=0 , House Owner Flag=0 , Gender=F , Total Children=2 , Region=Pacific</span></span>|  
  
 <span data-ttu-id="e75c5-187">定义分类的属性可以在数据挖掘架构行集中的两列找到。</span><span class="sxs-lookup"><span data-stu-id="e75c5-187">The attributes that define the cluster can be found in two columns in the data mining schema rowset.</span></span>  
  
-   <span data-ttu-id="e75c5-188">NODE_DESCRIPTION 列包含逗号分隔的属性列表。</span><span class="sxs-lookup"><span data-stu-id="e75c5-188">The NODE_DESCRIPTION column contains a comma-separated list of attributes.</span></span> <span data-ttu-id="e75c5-189">请注意，为便于显示，可能对属性列表进行了缩略。</span><span class="sxs-lookup"><span data-stu-id="e75c5-189">Note that the list of attributes might be abbreviated for display purposes.</span></span>  
  
-   <span data-ttu-id="e75c5-190">NODE_DISTRIBUTION 列中的嵌套表包含分类的属性的完整列表。</span><span class="sxs-lookup"><span data-stu-id="e75c5-190">The nested table in the NODE_DISTRIBUTION column contains the full list of attributes for the cluster.</span></span> <span data-ttu-id="e75c5-191">如果您的客户端不支持分层行集，可以通过在 SELECT 列列表前添加 FLATTENED 关键字来返回嵌套表。</span><span class="sxs-lookup"><span data-stu-id="e75c5-191">If your client does not support hierarchical rowsets, you can return the nested table by adding the FLATTENED keyword before the SELECT column list.</span></span> <span data-ttu-id="e75c5-192">有关 FLATTENED 关键字的使用的详细信息，请参阅 [SELECT FROM <model>.CONTENT (DMX)](/sql/dmx/select-from-model-dimension-content-dmx)。</span><span class="sxs-lookup"><span data-stu-id="e75c5-192">For more information about the use of the FLATTENED keyword, see [SELECT FROM &#60;model&#62;.CONTENT &#40;DMX&#41;](/sql/dmx/select-from-model-dimension-content-dmx).</span></span>  
  
 [<span data-ttu-id="e75c5-193">返回页首</span><span class="sxs-lookup"><span data-stu-id="e75c5-193">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-4-returning-attributes-for-a-cluster"></a><a name="bkmk_Query4"></a> <span data-ttu-id="e75c5-194">示例查询 4：返回分类的属性</span><span class="sxs-lookup"><span data-stu-id="e75c5-194">Sample Query 4: Returning Attributes for a Cluster</span></span>  
 <span data-ttu-id="e75c5-195">对于每个分类， **“分类查看器”** 都显示列出属性及其值的配置文件。</span><span class="sxs-lookup"><span data-stu-id="e75c5-195">For every cluster, the **Cluster Viewer** displays a profile that lists the attributes and their values.</span></span> <span data-ttu-id="e75c5-196">此查看器还显示一个直方图，以显示当模型中完全填充了事例时值的分布。</span><span class="sxs-lookup"><span data-stu-id="e75c5-196">The viewer also displays a histogram that shows the distribution of values for the whole population of cases in the model.</span></span> <span data-ttu-id="e75c5-197">如果您是在查看器中浏览模型，则可以轻松地将直方图从挖掘图例复制并粘贴到 Excel 或 Word 文档。</span><span class="sxs-lookup"><span data-stu-id="e75c5-197">If you are browsing the model in the viewer, you can easily copy the histogram from the Mining Legend and then paste it to Excel or a Word document.</span></span> <span data-ttu-id="e75c5-198">您还可以使用查看器的“分类特征”窗格以图形方式比较不同分类的属性。</span><span class="sxs-lookup"><span data-stu-id="e75c5-198">You can also use the Cluster Characteristics pane of the viewer to graphically compare the attributes of different clusters.</span></span>  
  
 <span data-ttu-id="e75c5-199">但是，如果您必须一次获取多个分类的值，则查询模型更容易。</span><span class="sxs-lookup"><span data-stu-id="e75c5-199">However, if you must obtain values for more than one cluster at a time, it is easier to query the model.</span></span> <span data-ttu-id="e75c5-200">例如，浏览模型时，您可能注意到最上面的两个分类在属性 `Number Cars Owned`上存在不同。</span><span class="sxs-lookup"><span data-stu-id="e75c5-200">For example, when you browse the model, you might notice that the top two clusters differ with regard to one attribute, `Number Cars Owned`.</span></span> <span data-ttu-id="e75c5-201">因此，您需要提取每个分类的值。</span><span class="sxs-lookup"><span data-stu-id="e75c5-201">Therefore, you want to extract the values for each cluster.</span></span>  
  
```  
SELECT TOP 2 NODE_NAME,   
(SELECT ATTRIBUTE_VALUE, [PROBABILITY] FROM NODE_DISTRIBUTION WHERE ATTRIBUTE_NAME = 'Number Cars Owned')  
AS t  
FROM [TM_Clustering].CONTENT  
WHERE NODE_TYPE = 5  
```  
  
 <span data-ttu-id="e75c5-202">代码的第一行指定您只需要最上面的两个分类。</span><span class="sxs-lookup"><span data-stu-id="e75c5-202">The first line of the code specifies that you want only the top two clusters.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e75c5-203">默认情况下，分类按支持排序。</span><span class="sxs-lookup"><span data-stu-id="e75c5-203">By default, the clusters are ordered by support.</span></span> <span data-ttu-id="e75c5-204">因此，NODE_SUPPORT 列可以忽略。</span><span class="sxs-lookup"><span data-stu-id="e75c5-204">Therefore, the NODE_SUPPORT column can be omitted.</span></span>  
  
 <span data-ttu-id="e75c5-205">代码的第二行添加仅仅从嵌套表列返回某些列的嵌套 Select 语句。</span><span class="sxs-lookup"><span data-stu-id="e75c5-205">The second line of the code adds a sub-select statement that returns only certain columns from the nested table column.</span></span> <span data-ttu-id="e75c5-206">此外，它将嵌套表中的行限定为与目标属性 `Number Cars Owned`有关的那些行。</span><span class="sxs-lookup"><span data-stu-id="e75c5-206">Furthermore, it restricts the rows from the nested table to those related to the target attribute, `Number Cars Owned`.</span></span> <span data-ttu-id="e75c5-207">为了简化显示，使用嵌套表的别名。</span><span class="sxs-lookup"><span data-stu-id="e75c5-207">To simplify the display, the nested table is aliased.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e75c5-208">嵌套表列 `PROBABILITY`必须括在括号中，因为它也是保留的 MDX 关键字的名称。</span><span class="sxs-lookup"><span data-stu-id="e75c5-208">The nested table column, `PROBABILITY`, must be enclosed in brackets because it is also the name of a reserved MDX keyword.</span></span>  
>   
>  <span data-ttu-id="e75c5-209">示例结果：</span><span class="sxs-lookup"><span data-stu-id="e75c5-209">Example results:</span></span>  
  
|<span data-ttu-id="e75c5-210">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="e75c5-210">NODE_NAME</span></span>|<span data-ttu-id="e75c5-211">T.ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="e75c5-211">T.ATTRIBUTE_VALUE</span></span>|<span data-ttu-id="e75c5-212">T.PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="e75c5-212">T.PROBABILITY</span></span>|  
|----------------|------------------------|-------------------|  
|<span data-ttu-id="e75c5-213">001</span><span class="sxs-lookup"><span data-stu-id="e75c5-213">001</span></span>|<span data-ttu-id="e75c5-214">2</span><span class="sxs-lookup"><span data-stu-id="e75c5-214">2</span></span>|<span data-ttu-id="e75c5-215">0.829207754</span><span class="sxs-lookup"><span data-stu-id="e75c5-215">0.829207754</span></span>|  
|<span data-ttu-id="e75c5-216">001</span><span class="sxs-lookup"><span data-stu-id="e75c5-216">001</span></span>|<span data-ttu-id="e75c5-217">1</span><span class="sxs-lookup"><span data-stu-id="e75c5-217">1</span></span>|<span data-ttu-id="e75c5-218">0.109354156</span><span class="sxs-lookup"><span data-stu-id="e75c5-218">0.109354156</span></span>|  
|<span data-ttu-id="e75c5-219">001</span><span class="sxs-lookup"><span data-stu-id="e75c5-219">001</span></span>|<span data-ttu-id="e75c5-220">3</span><span class="sxs-lookup"><span data-stu-id="e75c5-220">3</span></span>|<span data-ttu-id="e75c5-221">0.034481552</span><span class="sxs-lookup"><span data-stu-id="e75c5-221">0.034481552</span></span>|  
|<span data-ttu-id="e75c5-222">001</span><span class="sxs-lookup"><span data-stu-id="e75c5-222">001</span></span>|<span data-ttu-id="e75c5-223">4</span><span class="sxs-lookup"><span data-stu-id="e75c5-223">4</span></span>|<span data-ttu-id="e75c5-224">0.013503302</span><span class="sxs-lookup"><span data-stu-id="e75c5-224">0.013503302</span></span>|  
|<span data-ttu-id="e75c5-225">001</span><span class="sxs-lookup"><span data-stu-id="e75c5-225">001</span></span>|<span data-ttu-id="e75c5-226">0</span><span class="sxs-lookup"><span data-stu-id="e75c5-226">0</span></span>|<span data-ttu-id="e75c5-227">0.013453236</span><span class="sxs-lookup"><span data-stu-id="e75c5-227">0.013453236</span></span>|  
|<span data-ttu-id="e75c5-228">001</span><span class="sxs-lookup"><span data-stu-id="e75c5-228">001</span></span>|<span data-ttu-id="e75c5-229">Missing</span><span class="sxs-lookup"><span data-stu-id="e75c5-229">Missing</span></span>|<span data-ttu-id="e75c5-230">0</span><span class="sxs-lookup"><span data-stu-id="e75c5-230">0</span></span>|  
|<span data-ttu-id="e75c5-231">002</span><span class="sxs-lookup"><span data-stu-id="e75c5-231">002</span></span>|<span data-ttu-id="e75c5-232">0</span><span class="sxs-lookup"><span data-stu-id="e75c5-232">0</span></span>|<span data-ttu-id="e75c5-233">0.576980023</span><span class="sxs-lookup"><span data-stu-id="e75c5-233">0.576980023</span></span>|  
|<span data-ttu-id="e75c5-234">002</span><span class="sxs-lookup"><span data-stu-id="e75c5-234">002</span></span>|<span data-ttu-id="e75c5-235">1</span><span class="sxs-lookup"><span data-stu-id="e75c5-235">1</span></span>|<span data-ttu-id="e75c5-236">0.406623939</span><span class="sxs-lookup"><span data-stu-id="e75c5-236">0.406623939</span></span>|  
|<span data-ttu-id="e75c5-237">002</span><span class="sxs-lookup"><span data-stu-id="e75c5-237">002</span></span>|<span data-ttu-id="e75c5-238">2</span><span class="sxs-lookup"><span data-stu-id="e75c5-238">2</span></span>|<span data-ttu-id="e75c5-239">0.016380082</span><span class="sxs-lookup"><span data-stu-id="e75c5-239">0.016380082</span></span>|  
|<span data-ttu-id="e75c5-240">002</span><span class="sxs-lookup"><span data-stu-id="e75c5-240">002</span></span>|<span data-ttu-id="e75c5-241">3</span><span class="sxs-lookup"><span data-stu-id="e75c5-241">3</span></span>|<span data-ttu-id="e75c5-242">1.60E-05</span><span class="sxs-lookup"><span data-stu-id="e75c5-242">1.60E-05</span></span>|  
|<span data-ttu-id="e75c5-243">002</span><span class="sxs-lookup"><span data-stu-id="e75c5-243">002</span></span>|<span data-ttu-id="e75c5-244">4</span><span class="sxs-lookup"><span data-stu-id="e75c5-244">4</span></span>|<span data-ttu-id="e75c5-245">0</span><span class="sxs-lookup"><span data-stu-id="e75c5-245">0</span></span>|  
|<span data-ttu-id="e75c5-246">002</span><span class="sxs-lookup"><span data-stu-id="e75c5-246">002</span></span>|<span data-ttu-id="e75c5-247">Missing</span><span class="sxs-lookup"><span data-stu-id="e75c5-247">Missing</span></span>|<span data-ttu-id="e75c5-248">0</span><span class="sxs-lookup"><span data-stu-id="e75c5-248">0</span></span>|  
  
 [<span data-ttu-id="e75c5-249">返回页首</span><span class="sxs-lookup"><span data-stu-id="e75c5-249">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-5-return-a-cluster-profile-using-system-stored-procedures"></a><a name="bkmk_Query5"></a> <span data-ttu-id="e75c5-250">示例查询 5：使用系统存储过程返回分类配置文件</span><span class="sxs-lookup"><span data-stu-id="e75c5-250">Sample Query 5: Return a Cluster Profile Using System Stored Procedures</span></span>  
 <span data-ttu-id="e75c5-251">作为一种快捷方式，您还可以调用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 用来处理分类的系统存储过程，而不是使用 DMX 编写自己的查询。</span><span class="sxs-lookup"><span data-stu-id="e75c5-251">As a shortcut, rather than writing your own queries by using DMX, you can also call the system stored procedures that [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] uses to work with clusters.</span></span> <span data-ttu-id="e75c5-252">下面的示例说明如何使用内部存储过程来返回 ID 为 002 的分类的配置文件。</span><span class="sxs-lookup"><span data-stu-id="e75c5-252">The following example illustrates how to use the internal stored procedures to return the profile for a cluster with the ID of 002.</span></span>  
  
```  
CALL System.Microsoft.AnalysisServices.System.DataMining.Clustering.GetClusterProfiles('TM_Clustering", '002',0.0005  
```  
  
 <span data-ttu-id="e75c5-253">同样，可以使用系统存储过程来返回特定分类的特征，如下面的示例所示：</span><span class="sxs-lookup"><span data-stu-id="e75c5-253">Similarly, you can use a system stored procedure to return the characteristics of a specific cluster, as shown in the following example:</span></span>  
  
```  
CALL System.Microsoft.AnalysisServices.System.DataMining.Clustering.GetClusterCharacteristics('TM_Clustering", '009',0.0005  
```  
  
 <span data-ttu-id="e75c5-254">示例结果：</span><span class="sxs-lookup"><span data-stu-id="e75c5-254">Example results:</span></span>  
  
|<span data-ttu-id="e75c5-255">属性</span><span class="sxs-lookup"><span data-stu-id="e75c5-255">Attributes</span></span>|<span data-ttu-id="e75c5-256">值</span><span class="sxs-lookup"><span data-stu-id="e75c5-256">Values</span></span>|<span data-ttu-id="e75c5-257">频率</span><span class="sxs-lookup"><span data-stu-id="e75c5-257">Frequency</span></span>|<span data-ttu-id="e75c5-258">支持</span><span class="sxs-lookup"><span data-stu-id="e75c5-258">Support</span></span>|  
|----------------|------------|---------------|-------------|  
|<span data-ttu-id="e75c5-259">Number Children at Home</span><span class="sxs-lookup"><span data-stu-id="e75c5-259">Number Children at Home</span></span>|<span data-ttu-id="e75c5-260">0</span><span class="sxs-lookup"><span data-stu-id="e75c5-260">0</span></span>|<span data-ttu-id="e75c5-261">0.999999829076798</span><span class="sxs-lookup"><span data-stu-id="e75c5-261">0.999999829076798</span></span>|<span data-ttu-id="e75c5-262">899</span><span class="sxs-lookup"><span data-stu-id="e75c5-262">899</span></span>|  
|<span data-ttu-id="e75c5-263">区域</span><span class="sxs-lookup"><span data-stu-id="e75c5-263">Region</span></span>|<span data-ttu-id="e75c5-264">北美</span><span class="sxs-lookup"><span data-stu-id="e75c5-264">North America</span></span>|<span data-ttu-id="e75c5-265">0.999852875241508</span><span class="sxs-lookup"><span data-stu-id="e75c5-265">0.999852875241508</span></span>|<span data-ttu-id="e75c5-266">899</span><span class="sxs-lookup"><span data-stu-id="e75c5-266">899</span></span>|  
|<span data-ttu-id="e75c5-267">Total Children</span><span class="sxs-lookup"><span data-stu-id="e75c5-267">Total Children</span></span>|<span data-ttu-id="e75c5-268">0</span><span class="sxs-lookup"><span data-stu-id="e75c5-268">0</span></span>|<span data-ttu-id="e75c5-269">0.993860958572323</span><span class="sxs-lookup"><span data-stu-id="e75c5-269">0.993860958572323</span></span>|<span data-ttu-id="e75c5-270">893</span><span class="sxs-lookup"><span data-stu-id="e75c5-270">893</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="e75c5-271">数据挖掘系统存储过程仅供内部使用， [!INCLUDE[msCoName](../../includes/msconame-md.md)] 保留根据需要更改它们的权利。</span><span class="sxs-lookup"><span data-stu-id="e75c5-271">The data mining system stored procedures are for internal use and [!INCLUDE[msCoName](../../includes/msconame-md.md)] reserves the right to change them as needed.</span></span> <span data-ttu-id="e75c5-272">如果用于生产，建议您使用 DMX、AMO 或 XMLA 来创建查询。</span><span class="sxs-lookup"><span data-stu-id="e75c5-272">For production use, we recommend that you create queries by using DMX, AMO, or XMLA.</span></span>  
  
 [<span data-ttu-id="e75c5-273">返回页首</span><span class="sxs-lookup"><span data-stu-id="e75c5-273">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-6-find-discriminating-factors-for-a-cluster"></a><a name="bkmk_Query6"></a> <span data-ttu-id="e75c5-274">示例查询 6：查找分类的对比因子</span><span class="sxs-lookup"><span data-stu-id="e75c5-274">Sample Query 6: Find Discriminating Factors for a Cluster</span></span>  
 <span data-ttu-id="e75c5-275">使用**分类查看器**的“分类对比”\*\*\*\* 选项卡，可以轻松地将一个分类与另一个分类进行比较，或者将一个分类与其余所有事例（分类的补充）进行比较。</span><span class="sxs-lookup"><span data-stu-id="e75c5-275">The **Cluster Discrimination** tab of the **Cluster Viewer** enables you to easily compare a cluster with another cluster, or compare a cluster with all remaining cases (the complement of the cluster).</span></span>  
  
 <span data-ttu-id="e75c5-276">但是，创建查询来返回这些信息很复杂，您可能需要在客户端上进行一些额外的处理来存储临时结果并比较两个或更多查询的结果。</span><span class="sxs-lookup"><span data-stu-id="e75c5-276">However, creating queries to return this information can be complex, and you might need some additional processing on the client to store the temporary results and compare the results of two or more queries.</span></span> <span data-ttu-id="e75c5-277">作为一种快捷方式，可以使用系统存储过程。</span><span class="sxs-lookup"><span data-stu-id="e75c5-277">As a shortcut, you can use the system stored procedures.</span></span>  
  
 <span data-ttu-id="e75c5-278">下面的查询返回一个表，该表指示节点 ID 分别为 009 和 007 的两个分类之间的主对比因子。</span><span class="sxs-lookup"><span data-stu-id="e75c5-278">The following query returns a single table that indicates the primary discriminating factors between the two clusters that have the node IDs of 009 and 007.</span></span> <span data-ttu-id="e75c5-279">具有正值的属性有利于分类 009，而具有负值的属性则有利于分类 007。</span><span class="sxs-lookup"><span data-stu-id="e75c5-279">Attributes with positive values favor cluster 009, whereas attributes with negative values favor cluster 007.</span></span>  
  
```  
CALL System.Microsoft.AnalysisServices.System.DataMining.Clustering.GetClusterDiscrimination('TM_Clustering','009','007',0.0005,true)  
```  
  
 <span data-ttu-id="e75c5-280">示例结果：</span><span class="sxs-lookup"><span data-stu-id="e75c5-280">Example results:</span></span>  
  
|<span data-ttu-id="e75c5-281">属性</span><span class="sxs-lookup"><span data-stu-id="e75c5-281">Attributes</span></span>|<span data-ttu-id="e75c5-282">值</span><span class="sxs-lookup"><span data-stu-id="e75c5-282">Values</span></span>|<span data-ttu-id="e75c5-283">分数</span><span class="sxs-lookup"><span data-stu-id="e75c5-283">Score</span></span>|  
|----------------|------------|-----------|  
|<span data-ttu-id="e75c5-284">区域</span><span class="sxs-lookup"><span data-stu-id="e75c5-284">Region</span></span>|<span data-ttu-id="e75c5-285">北美</span><span class="sxs-lookup"><span data-stu-id="e75c5-285">North America</span></span>|<span data-ttu-id="e75c5-286">100</span><span class="sxs-lookup"><span data-stu-id="e75c5-286">100</span></span>|  
|<span data-ttu-id="e75c5-287">English Occupation</span><span class="sxs-lookup"><span data-stu-id="e75c5-287">English Occupation</span></span>|<span data-ttu-id="e75c5-288">技术工人</span><span class="sxs-lookup"><span data-stu-id="e75c5-288">Skilled Manual</span></span>|<span data-ttu-id="e75c5-289">94.9003803898654</span><span class="sxs-lookup"><span data-stu-id="e75c5-289">94.9003803898654</span></span>|  
|<span data-ttu-id="e75c5-290">区域</span><span class="sxs-lookup"><span data-stu-id="e75c5-290">Region</span></span>|<span data-ttu-id="e75c5-291">欧洲</span><span class="sxs-lookup"><span data-stu-id="e75c5-291">Europe</span></span>|<span data-ttu-id="e75c5-292">-72.5041051379789</span><span class="sxs-lookup"><span data-stu-id="e75c5-292">-72.5041051379789</span></span>|  
|<span data-ttu-id="e75c5-293">English Occupation</span><span class="sxs-lookup"><span data-stu-id="e75c5-293">English Occupation</span></span>|<span data-ttu-id="e75c5-294">手动</span><span class="sxs-lookup"><span data-stu-id="e75c5-294">Manual</span></span>|<span data-ttu-id="e75c5-295">-69.6503163202722</span><span class="sxs-lookup"><span data-stu-id="e75c5-295">-69.6503163202722</span></span>|  
  
 <span data-ttu-id="e75c5-296">这与当你从第一个下拉列表中选择分类 9，从第二个下拉列表中选择分类 7 时， **分类对比** 查看器的图中所显示的信息相同。</span><span class="sxs-lookup"><span data-stu-id="e75c5-296">This is the same information that is presented in the chart of the **Cluster Discrimination** viewer if you select Cluster 9 from the first drop-down list and Cluster 7 from the second drop-down list.</span></span> <span data-ttu-id="e75c5-297">若要将分类 9 与其补数进行比较，应在第二个参数中使用空字符串，如下面的示例所示：</span><span class="sxs-lookup"><span data-stu-id="e75c5-297">To compare cluster 9 with its complement, you use the empty string in the second parameter, as shown in the following example:</span></span>  
  
```  
CALL System.Microsoft.AnalysisServices.System.DataMining.Clustering.GetClusterDiscrimination('TM_Clustering','009','',0.0005,true)  
```  
  
> [!NOTE]  
>  <span data-ttu-id="e75c5-298">数据挖掘系统存储过程仅供内部使用， [!INCLUDE[msCoName](../../includes/msconame-md.md)] 保留根据需要更改它们的权利。</span><span class="sxs-lookup"><span data-stu-id="e75c5-298">The data mining system stored procedures are for internal use and [!INCLUDE[msCoName](../../includes/msconame-md.md)] reserves the right to change them as needed.</span></span> <span data-ttu-id="e75c5-299">如果用于生产，建议您使用 DMX、AMO 或 XMLA 来创建查询。</span><span class="sxs-lookup"><span data-stu-id="e75c5-299">For production use, we recommend that you create queries by using DMX, AMO, or XMLA.</span></span>  
  
 [<span data-ttu-id="e75c5-300">返回页首</span><span class="sxs-lookup"><span data-stu-id="e75c5-300">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-7-returning-cases-that-belong-to-a-cluster"></a><a name="bkmk_Query7"></a> <span data-ttu-id="e75c5-301">示例查询 7：返回属于分类的事例</span><span class="sxs-lookup"><span data-stu-id="e75c5-301">Sample Query 7: Returning Cases that Belong to a Cluster</span></span>  
 <span data-ttu-id="e75c5-302">如果对挖掘模型启用了钻取，则可以创建查询来返回有关在模型中使用的事例的详细信息。</span><span class="sxs-lookup"><span data-stu-id="e75c5-302">If drillthrough has been enabled on the mining model, you can create queries that return detailed information about the cases used in the model.</span></span> <span data-ttu-id="e75c5-303">此外，如果对挖掘结构启用了钻取，则可以通过使用 [StructureColumn （DMX）](/sql/dmx/structurecolumn-dmx) 函数来包括基础结构中的列。</span><span class="sxs-lookup"><span data-stu-id="e75c5-303">Moreover, if drillthrough has been enabled on the mining structure, you can include columns from the underlying structure by using the [StructureColumn &#40;DMX&#41;](/sql/dmx/structurecolumn-dmx) function.</span></span>  
  
 <span data-ttu-id="e75c5-304">下面的示例返回模型中使用的两列 Age 和 Region，以及模型中未使用的一列 First Name。</span><span class="sxs-lookup"><span data-stu-id="e75c5-304">The following example returns two columns that were used in the model, Age and Region, and one more column, First Name, that was not used in the model.</span></span> <span data-ttu-id="e75c5-305">此查询仅仅返回归为分类 1 的事例。</span><span class="sxs-lookup"><span data-stu-id="e75c5-305">The query returns only cases that were classified into Cluster 1.</span></span>  
  
```  
SELECT [Age], [Region], StructureColumn('First Name')  
FROM [TM_Clustering].CASES  
WHERE IsInNode('001')  
```  
  
 <span data-ttu-id="e75c5-306">若要返回属于某个分类的事例，必须知道该分类的 ID。</span><span class="sxs-lookup"><span data-stu-id="e75c5-306">To return the cases that belong to a cluster, you must know the ID of the cluster.</span></span> <span data-ttu-id="e75c5-307">可以通过在某个查看器中浏览模型来获取分类的 ID。</span><span class="sxs-lookup"><span data-stu-id="e75c5-307">You can obtain the ID of the cluster by browsing the model in one of the viewers.</span></span> <span data-ttu-id="e75c5-308">或者，为便于引用，可以重命名分类，之后，即可使用名称来代替 ID 号。</span><span class="sxs-lookup"><span data-stu-id="e75c5-308">Or, you can rename a cluster for easier reference, after which you could use the name in place of an ID number.</span></span> <span data-ttu-id="e75c5-309">但要注意的是，在重新处理模型后，您分配给分类的名称将会丢失。</span><span class="sxs-lookup"><span data-stu-id="e75c5-309">However, know that the names that you assign to a cluster will be lost if the model is reprocessed.</span></span>  
  
 [<span data-ttu-id="e75c5-310">返回页首</span><span class="sxs-lookup"><span data-stu-id="e75c5-310">Return to Top</span></span>](#bkmk_top2)  
  
## <a name="making-predictions-using-the-model"></a><span data-ttu-id="e75c5-311">使用模型进行预测</span><span class="sxs-lookup"><span data-stu-id="e75c5-311">Making Predictions using the Model</span></span>  
 <span data-ttu-id="e75c5-312">尽管聚类分析通常用于描述和了解数据，但是 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 实现使您还可以对分类成员身份进行预测，并返回与预测关联的概率。</span><span class="sxs-lookup"><span data-stu-id="e75c5-312">Although clustering is typically used for describing and understanding data, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] implementation also lets you make prediction about cluster membership, and return probabilities associated with the prediction.</span></span> <span data-ttu-id="e75c5-313">本节提供关于如何在聚类分析模型上创建预测查询的示例。</span><span class="sxs-lookup"><span data-stu-id="e75c5-313">This section provides examples of how to create prediction queries on clustering models.</span></span> <span data-ttu-id="e75c5-314">您可以通过指定表格格式数据源来针对多个事例进行预测，或者可以通过创建单独查询来一次提供一个新的值。</span><span class="sxs-lookup"><span data-stu-id="e75c5-314">You can make predictions for multiple cases, by specifying a tabular data source, or you can provide new values on at a time by creating a singleton query.</span></span> <span data-ttu-id="e75c5-315">为清楚起见，本节中的示例均为单独查询。</span><span class="sxs-lookup"><span data-stu-id="e75c5-315">For clarity the examples in this section are all singleton queries.</span></span>  
  
 <span data-ttu-id="e75c5-316">有关如何使用 DMX 创建预测查询的详细信息，请参阅[数据挖掘查询接口](data-mining-query-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="e75c5-316">For more information about how to create prediction queries using DMX, see [Data Mining Query Interfaces](data-mining-query-tools.md).</span></span>  
  
 [<span data-ttu-id="e75c5-317">返回页首</span><span class="sxs-lookup"><span data-stu-id="e75c5-317">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-8-predicting-outcomes-from-a-clustering-model"></a><a name="bkmk_Query8"></a> <span data-ttu-id="e75c5-318">示例查询 8：从聚类分析模型中预测结果</span><span class="sxs-lookup"><span data-stu-id="e75c5-318">Sample Query 8: Predicting Outcomes from a Clustering Model</span></span>  
 <span data-ttu-id="e75c5-319">如果您创建的聚类分析模型包含可预测的属性，则可以使用该模型来对结果进行预测。</span><span class="sxs-lookup"><span data-stu-id="e75c5-319">If the clustering model you create contains a predictable attribute, you can use the model to make predictions about outcomes.</span></span> <span data-ttu-id="e75c5-320">但是，根据您将可预测列设置为 `Predict` 还是 `PredictOnly`，模型处理该可预测属性的方式也不同。</span><span class="sxs-lookup"><span data-stu-id="e75c5-320">However, the model handles the predictable attribute differently depending on whether you set the predictable column to `Predict` or `PredictOnly`.</span></span> <span data-ttu-id="e75c5-321">如果您将列的用法设置为 `Predict`，则该属性的值会添加到聚类分析模型，并在完成的模型中显示为属性。</span><span class="sxs-lookup"><span data-stu-id="e75c5-321">If you set the usage of the column to `Predict`, the values for that attribute are added to the clustering model and appear as attributes in the finished model.</span></span> <span data-ttu-id="e75c5-322">但是，如果将列的用法设置为 `PredictOnly`，则值不会用于创建分类。</span><span class="sxs-lookup"><span data-stu-id="e75c5-322">However, if you set the usage of the column to `PredictOnly`, the values are not used to create clusters.</span></span> <span data-ttu-id="e75c5-323">模型完成后，聚类分析算法会基于每个事例所属的分类为 `PredictOnly` 属性创建新的值。</span><span class="sxs-lookup"><span data-stu-id="e75c5-323">Instead, after the mode is completed, the clustering algorithm creates new values for the `PredictOnly` attribute based on the clusters to which each case belongs.</span></span>  
  
 <span data-ttu-id="e75c5-324">下面的查询向模型提供一个新事例，在该模型中，有关该事例的唯一信息是年龄和性别。</span><span class="sxs-lookup"><span data-stu-id="e75c5-324">The following query provides a single new case to the model, where the only information about the case is the age and gender.</span></span> <span data-ttu-id="e75c5-325">SELECT 语句指定你关注的可预测属性/值对，而 [PredictProbability (DMX)](/sql/dmx/predictprobability-dmx) 函数则指出具有这些属性的事例具有目标结果的概率。</span><span class="sxs-lookup"><span data-stu-id="e75c5-325">The SELECT statement specifies the predictable attribute/value pair that you are interested in, and the [PredictProbability &#40;DMX&#41;](/sql/dmx/predictprobability-dmx) function tells you the probability that a case with those attributes will have the targeted outcome.</span></span>  
  
```  
SELECT  
  [TM_Clustering].[Bike Buyer], PredictProbability([Bike Buyer],1)  
FROM  
  [TM_Clustering]  
NATURAL PREDICTION JOIN  
(SELECT 40 AS [Age],  
  'F' AS [Gender]) AS t  
```  
  
 <span data-ttu-id="e75c5-326">用法设置为 `Predict` 时的结果示例：</span><span class="sxs-lookup"><span data-stu-id="e75c5-326">Example of results when usage is set to `Predict`:</span></span>  
  
|<span data-ttu-id="e75c5-327">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="e75c5-327">Bike Buyer</span></span>|<span data-ttu-id="e75c5-328">Expression</span><span class="sxs-lookup"><span data-stu-id="e75c5-328">Expression</span></span>|  
|----------------|----------------|  
|<span data-ttu-id="e75c5-329">1</span><span class="sxs-lookup"><span data-stu-id="e75c5-329">1</span></span>|<span data-ttu-id="e75c5-330">0.592924735740338</span><span class="sxs-lookup"><span data-stu-id="e75c5-330">0.592924735740338</span></span>|  
  
 <span data-ttu-id="e75c5-331">用法设置为 `PredictOnly` 且模型重新处理时的结果示例：</span><span class="sxs-lookup"><span data-stu-id="e75c5-331">Example of results when the usage is set to `PredictOnly` and the model is reprocessed:</span></span>  
  
|<span data-ttu-id="e75c5-332">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="e75c5-332">Bike Buyer</span></span>|<span data-ttu-id="e75c5-333">Expression</span><span class="sxs-lookup"><span data-stu-id="e75c5-333">Expression</span></span>|  
|----------------|----------------|  
|<span data-ttu-id="e75c5-334">1</span><span class="sxs-lookup"><span data-stu-id="e75c5-334">1</span></span>|<span data-ttu-id="e75c5-335">0.55843544003102</span><span class="sxs-lookup"><span data-stu-id="e75c5-335">0.55843544003102</span></span>|  
  
 <span data-ttu-id="e75c5-336">在本示例中，模型中的区别不是很明显。</span><span class="sxs-lookup"><span data-stu-id="e75c5-336">In this example, the difference in the model is not significant.</span></span> <span data-ttu-id="e75c5-337">但是，有时可能必须检测出值的实际分布与模型所预测的情况之间的区别。</span><span class="sxs-lookup"><span data-stu-id="e75c5-337">However, sometimes it can be important to detect differences between the actual distribution of values and what the model predicts.</span></span> <span data-ttu-id="e75c5-338">在这种情况下 [PredictCaseLikelihood (DMX)](/sql/dmx/predictcaselikelihood-dmx) 函数很有用，因为它可指出事例适用于模型的可能性。</span><span class="sxs-lookup"><span data-stu-id="e75c5-338">The [PredictCaseLikelihood &#40;DMX&#41;](/sql/dmx/predictcaselikelihood-dmx) function is useful in this scenario, because it tells you how likely a case is, given the model.</span></span>  
  
 <span data-ttu-id="e75c5-339">PredictCaseLikelihood 函数返回的数是概率，因此总是在 0 和 1 之间，值 .5 表示随机结果。</span><span class="sxs-lookup"><span data-stu-id="e75c5-339">The number that is returned by the PredictCaseLikelihood function is a probability, and therefore is always between 0 and 1, with a value of .5 representing random outcome.</span></span> <span data-ttu-id="e75c5-340">因此，小于 .5 的分数意味着预测的事例不太可能适用于此模型，而大于 .5 的分数则意味着预测的事例适用于模型的可能性比不适用于模型的可能性大。</span><span class="sxs-lookup"><span data-stu-id="e75c5-340">Therefore, a score less than .5 means that the predicted case is unlikely, given the model, and a score over.5 indicates that the predicted case is more likely than not to fit the model.</span></span>  
  
 <span data-ttu-id="e75c5-341">例如，下面的查询返回两个值，这两个值指出新示例事例的可能性。</span><span class="sxs-lookup"><span data-stu-id="e75c5-341">For example, the following query returns two values that characterize the likelihood of a new sample case.</span></span> <span data-ttu-id="e75c5-342">非规范化值表示适用于当前模型的概率。</span><span class="sxs-lookup"><span data-stu-id="e75c5-342">The non-normalized value represents the probability given the current model.</span></span> <span data-ttu-id="e75c5-343">使用 NORMALIZED 关键字时，此函数返回的可能性分数是用“有模型的概率”除以“没有模型的概率”来得到的。</span><span class="sxs-lookup"><span data-stu-id="e75c5-343">When you use the NORMALIZED keyword, the likelihood score that is returned by the function is adjusted by dividing "probability with the model" by "probability without the model".</span></span>  
  
```  
SELECT  
PredictCaseLikelihood(NORMALIZED) AS [NormalizedValue], PredictCaseLikelihood(NONNORMALIZED) AS [NonNormalizedValue]  
FROM  
  [TM_Clustering_PredictOnly]  
NATURAL PREDICTION JOIN  
(SELECT 40 AS [Age],  
  'F' AS [Gender]) AS t  
```  
  
 <span data-ttu-id="e75c5-344">示例结果：</span><span class="sxs-lookup"><span data-stu-id="e75c5-344">Example results:</span></span>  
  
|<span data-ttu-id="e75c5-345">NormalizedValue</span><span class="sxs-lookup"><span data-stu-id="e75c5-345">NormalizedValue</span></span>|<span data-ttu-id="e75c5-346">NonNormalizedValue</span><span class="sxs-lookup"><span data-stu-id="e75c5-346">NonNormalizedValue</span></span>|  
|---------------------|------------------------|  
|<span data-ttu-id="e75c5-347">5.56438372679893E-11</span><span class="sxs-lookup"><span data-stu-id="e75c5-347">5.56438372679893E-11</span></span>|<span data-ttu-id="e75c5-348">8.65459953145182E-68</span><span class="sxs-lookup"><span data-stu-id="e75c5-348">8.65459953145182E-68</span></span>|  
  
 <span data-ttu-id="e75c5-349">请注意这些结果中的数是用科学记数法来表示的。</span><span class="sxs-lookup"><span data-stu-id="e75c5-349">Note that the numbers in these results are expressed in scientific notation.</span></span>  
  
 [<span data-ttu-id="e75c5-350">返回页首</span><span class="sxs-lookup"><span data-stu-id="e75c5-350">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-9-determining-cluster-membership"></a><a name="bkmk_Query9"></a> <span data-ttu-id="e75c5-351">示例查询 9：确定分类成员身份</span><span class="sxs-lookup"><span data-stu-id="e75c5-351">Sample Query 9: Determining Cluster Membership</span></span>  
 <span data-ttu-id="e75c5-352">本示例使用 [分类 (DMX)](/sql/dmx/cluster-dmx) 函数来返回新事例最有可能属于的分类，并使用 [ClusterProbability (DMX)](/sql/dmx/clusterprobability-dmx) 函数来返回该分类中的成员身份的概率。</span><span class="sxs-lookup"><span data-stu-id="e75c5-352">This example uses the [Cluster &#40;DMX&#41;](/sql/dmx/cluster-dmx) function to return the cluster to which the new case is most likely to belong, and uses the [ClusterProbability &#40;DMX&#41;](/sql/dmx/clusterprobability-dmx) function to return the probability for membership in that cluster.</span></span>  
  
```  
SELECT Cluster(), ClusterProbability()  
FROM  
  [TM_Clustering]  
NATURAL PREDICTION JOIN  
(SELECT 40 AS [Age],  
  'F' AS [Gender],  
  'S' AS [Marital Status]) AS t  
```  
  
 <span data-ttu-id="e75c5-353">示例结果：</span><span class="sxs-lookup"><span data-stu-id="e75c5-353">Example results:</span></span>  
  
|<span data-ttu-id="e75c5-354">$CLUSTER</span><span class="sxs-lookup"><span data-stu-id="e75c5-354">$CLUSTER</span></span>|<span data-ttu-id="e75c5-355">Expression</span><span class="sxs-lookup"><span data-stu-id="e75c5-355">Expression</span></span>|  
|--------------|----------------|  
|<span data-ttu-id="e75c5-356">Cluster 2</span><span class="sxs-lookup"><span data-stu-id="e75c5-356">Cluster 2</span></span>|<span data-ttu-id="e75c5-357">0.397918596951617</span><span class="sxs-lookup"><span data-stu-id="e75c5-357">0.397918596951617</span></span>|  
  
 <span data-ttu-id="e75c5-358">**注意**默认情况下， `ClusterProbability` 函数返回最可能分类的概率。</span><span class="sxs-lookup"><span data-stu-id="e75c5-358">**Note** By default, the `ClusterProbability` function returns the probability of the most likely cluster.</span></span> <span data-ttu-id="e75c5-359">但是，您可以通过使用语法 `ClusterProbability('cluster name')`来指定另一分类。</span><span class="sxs-lookup"><span data-stu-id="e75c5-359">However, you can specify a different cluster by using the syntax `ClusterProbability('cluster name')`.</span></span> <span data-ttu-id="e75c5-360">如果这样做，请注意每个预测函数的结果都独立于其他结果。</span><span class="sxs-lookup"><span data-stu-id="e75c5-360">If you do this, be aware that the results from each prediction function are independent of the other results.</span></span> <span data-ttu-id="e75c5-361">因此，第二列中的概率分数可能引用另一个分类，而不是第一列中所指定的分类。</span><span class="sxs-lookup"><span data-stu-id="e75c5-361">Therefore, the probability score in the second column could refer to a different cluster than the cluster named in the first column.</span></span>  
  
 [<span data-ttu-id="e75c5-362">返回页首</span><span class="sxs-lookup"><span data-stu-id="e75c5-362">Return to Top</span></span>](#bkmk_top2)  
  
###  <a name="sample-query-10-returning-all-possible-clusters-with-probability-and-distance"></a><a name="bkmk_Query10"></a> <span data-ttu-id="e75c5-363">示例查询 10：返回具有概率和距离的所有可能分类</span><span class="sxs-lookup"><span data-stu-id="e75c5-363">Sample Query 10: Returning All Possible Clusters with Probability and Distance</span></span>  
 <span data-ttu-id="e75c5-364">在上一个示例中，概率分数不是非常高。</span><span class="sxs-lookup"><span data-stu-id="e75c5-364">In the previous example, the probability score was not very high.</span></span> <span data-ttu-id="e75c5-365">若要确定是否存在更好的分类，可以将 [PredictHistogram (DMX)](/sql/dmx/predicthistogram-dmx) 函数与 [分类 (DMX)](/sql/dmx/cluster-dmx) 函数一起使用，以返回包括所有可能的分类以及新事例属于每个分类的概率的嵌套表。</span><span class="sxs-lookup"><span data-stu-id="e75c5-365">To determine if there is a better cluster, you can use the [PredictHistogram &#40;DMX&#41;](/sql/dmx/predicthistogram-dmx) function together with the [Cluster &#40;DMX&#41;](/sql/dmx/cluster-dmx) function to return a nested table that includes all possible clusters, together with the probability that the new case that belongs to each cluster.</span></span> <span data-ttu-id="e75c5-366">FLATTENED 关键字用于将分层行集改为平面表，以便于查看。</span><span class="sxs-lookup"><span data-stu-id="e75c5-366">The FLATTENED keyword is used to change the hierarchical rowset into a flat table for easier viewing.</span></span>  
  
```  
SELECT FLATTENED PredictHistogram(Cluster())  
From  
  [TM_Clustering]  
NATURAL PREDICTION JOIN  
(SELECT 40 AS [Age],  
  'F' AS [Gender],  
  'S' AS [Marital Status])  
```  
  
|<span data-ttu-id="e75c5-367">Expression.$CLUSTER</span><span class="sxs-lookup"><span data-stu-id="e75c5-367">Expression.$CLUSTER</span></span>|<span data-ttu-id="e75c5-368">Expression.$DISTANCE</span><span class="sxs-lookup"><span data-stu-id="e75c5-368">Expression.$DISTANCE</span></span>|<span data-ttu-id="e75c5-369">Expression.$PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="e75c5-369">Expression.$PROBABILITY</span></span>|  
|-------------------------|--------------------------|-----------------------------|  
|<span data-ttu-id="e75c5-370">Cluster 2</span><span class="sxs-lookup"><span data-stu-id="e75c5-370">Cluster 2</span></span>|<span data-ttu-id="e75c5-371">0.602081403048383</span><span class="sxs-lookup"><span data-stu-id="e75c5-371">0.602081403048383</span></span>|<span data-ttu-id="e75c5-372">0.397918596951617</span><span class="sxs-lookup"><span data-stu-id="e75c5-372">0.397918596951617</span></span>|  
|<span data-ttu-id="e75c5-373">分类 10</span><span class="sxs-lookup"><span data-stu-id="e75c5-373">Cluster 10</span></span>|<span data-ttu-id="e75c5-374">0.719691686785675</span><span class="sxs-lookup"><span data-stu-id="e75c5-374">0.719691686785675</span></span>|<span data-ttu-id="e75c5-375">0.280308313214325</span><span class="sxs-lookup"><span data-stu-id="e75c5-375">0.280308313214325</span></span>|  
|<span data-ttu-id="e75c5-376">分类 4</span><span class="sxs-lookup"><span data-stu-id="e75c5-376">Cluster 4</span></span>|<span data-ttu-id="e75c5-377">0.867772590378791</span><span class="sxs-lookup"><span data-stu-id="e75c5-377">0.867772590378791</span></span>|<span data-ttu-id="e75c5-378">0.132227409621209</span><span class="sxs-lookup"><span data-stu-id="e75c5-378">0.132227409621209</span></span>|  
|<span data-ttu-id="e75c5-379">分类 5</span><span class="sxs-lookup"><span data-stu-id="e75c5-379">Cluster 5</span></span>|<span data-ttu-id="e75c5-380">0.931039872200985</span><span class="sxs-lookup"><span data-stu-id="e75c5-380">0.931039872200985</span></span>|<span data-ttu-id="e75c5-381">0.0689601277990149</span><span class="sxs-lookup"><span data-stu-id="e75c5-381">0.0689601277990149</span></span>|  
|<span data-ttu-id="e75c5-382">分类 3</span><span class="sxs-lookup"><span data-stu-id="e75c5-382">Cluster 3</span></span>|<span data-ttu-id="e75c5-383">0.942359230072167</span><span class="sxs-lookup"><span data-stu-id="e75c5-383">0.942359230072167</span></span>|<span data-ttu-id="e75c5-384">0.0576407699278328</span><span class="sxs-lookup"><span data-stu-id="e75c5-384">0.0576407699278328</span></span>|  
|<span data-ttu-id="e75c5-385">分类 6</span><span class="sxs-lookup"><span data-stu-id="e75c5-385">Cluster 6</span></span>|<span data-ttu-id="e75c5-386">0.958973668972756</span><span class="sxs-lookup"><span data-stu-id="e75c5-386">0.958973668972756</span></span>|<span data-ttu-id="e75c5-387">0.0410263310272437</span><span class="sxs-lookup"><span data-stu-id="e75c5-387">0.0410263310272437</span></span>|  
|<span data-ttu-id="e75c5-388">分类 7</span><span class="sxs-lookup"><span data-stu-id="e75c5-388">Cluster 7</span></span>|<span data-ttu-id="e75c5-389">0.979081275926724</span><span class="sxs-lookup"><span data-stu-id="e75c5-389">0.979081275926724</span></span>|<span data-ttu-id="e75c5-390">0.0209187240732763</span><span class="sxs-lookup"><span data-stu-id="e75c5-390">0.0209187240732763</span></span>|  
|<span data-ttu-id="e75c5-391">分类 1</span><span class="sxs-lookup"><span data-stu-id="e75c5-391">Cluster 1</span></span>|<span data-ttu-id="e75c5-392">0.999169044818624</span><span class="sxs-lookup"><span data-stu-id="e75c5-392">0.999169044818624</span></span>|<span data-ttu-id="e75c5-393">0.000830955181376364</span><span class="sxs-lookup"><span data-stu-id="e75c5-393">0.000830955181376364</span></span>|  
|<span data-ttu-id="e75c5-394">分类 9</span><span class="sxs-lookup"><span data-stu-id="e75c5-394">Cluster 9</span></span>|<span data-ttu-id="e75c5-395">0.999831227795894</span><span class="sxs-lookup"><span data-stu-id="e75c5-395">0.999831227795894</span></span>|<span data-ttu-id="e75c5-396">0.000168772204105754</span><span class="sxs-lookup"><span data-stu-id="e75c5-396">0.000168772204105754</span></span>|  
|<span data-ttu-id="e75c5-397">群集 8</span><span class="sxs-lookup"><span data-stu-id="e75c5-397">Cluster 8</span></span>|<span data-ttu-id="e75c5-398">1</span><span class="sxs-lookup"><span data-stu-id="e75c5-398">1</span></span>|<span data-ttu-id="e75c5-399">0</span><span class="sxs-lookup"><span data-stu-id="e75c5-399">0</span></span>|  
  
 <span data-ttu-id="e75c5-400">默认情况下，结果按概率进行排序。</span><span class="sxs-lookup"><span data-stu-id="e75c5-400">By default, the results are ranked by probability.</span></span> <span data-ttu-id="e75c5-401">结果指出，尽管分类 2 的概率非常低，分类 2 仍然最适合于新数据点。</span><span class="sxs-lookup"><span data-stu-id="e75c5-401">The results tell you that, even though the probability for Cluster 2 is fairly low, Cluster 2 is still the best fit for the new data point.</span></span>  
  
 <span data-ttu-id="e75c5-402">**注意** 额外的一列 `$DISTANCE`表示从数据点到分类的距离。</span><span class="sxs-lookup"><span data-stu-id="e75c5-402">**Note** The additional column, `$DISTANCE`, represents the distance from the data point to the cluster.</span></span> <span data-ttu-id="e75c5-403">默认情况下， [!INCLUDE[msCoName](../../includes/msconame-md.md)] 聚类分析算法使用可缩放的 EM 聚类分析，此类分析为每个数据点分配多个分类，并对可能的分类进行排序。</span><span class="sxs-lookup"><span data-stu-id="e75c5-403">By default, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Clustering Algorithm uses scalable EM clustering, which assigns multiple clusters to each data point and ranks the possible clusters.</span></span>  <span data-ttu-id="e75c5-404">但是，如果您使用 K-means 算法来创建聚类分析模型，则只能为每个数据点分配一个分类，并且此查询仅仅返回一行。</span><span class="sxs-lookup"><span data-stu-id="e75c5-404">However, if you create your clustering model using the K-means algorithm, only one cluster can be assigned to each data point, and this query would return only one row.</span></span> <span data-ttu-id="e75c5-405">了解这些区别对于解释 [PredictCaseLikelihood (DMX)](/sql/dmx/predictcaselikelihood-dmx) 函数来包括基础结构中的列。</span><span class="sxs-lookup"><span data-stu-id="e75c5-405">Understanding these differences is necessary to interpret the results of the [PredictCaseLikelihood &#40;DMX&#41;](/sql/dmx/predictcaselikelihood-dmx) function.</span></span> <span data-ttu-id="e75c5-406">有关 EM 与 K-means 聚类分析之间的区别的详细信息，请参阅 [Microsoft 聚类分析算法技术参考](microsoft-clustering-algorithm-technical-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="e75c5-406">For more information about the differences between EM and K-means clustering, see [Microsoft Clustering Algorithm Technical Reference](microsoft-clustering-algorithm-technical-reference.md).</span></span>  
  
 [<span data-ttu-id="e75c5-407">返回页首</span><span class="sxs-lookup"><span data-stu-id="e75c5-407">Return to Top</span></span>](#bkmk_top2)  
  
## <a name="function-list"></a><span data-ttu-id="e75c5-408">函数列表</span><span class="sxs-lookup"><span data-stu-id="e75c5-408">Function List</span></span>  
 <span data-ttu-id="e75c5-409">所有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 算法均支持一组通用的函数。</span><span class="sxs-lookup"><span data-stu-id="e75c5-409">All [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms support a common set of functions.</span></span> <span data-ttu-id="e75c5-410">不过，使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 聚类分析算法生成的模型还支持下表中列出的其他函数。</span><span class="sxs-lookup"><span data-stu-id="e75c5-410">However, models that are built by using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Clustering algorithm support the additional functions that are listed in the following table.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e75c5-411">预测函数</span><span class="sxs-lookup"><span data-stu-id="e75c5-411">Prediction Function</span></span>|<span data-ttu-id="e75c5-412">使用情况</span><span class="sxs-lookup"><span data-stu-id="e75c5-412">Usage</span></span>|  
|[<span data-ttu-id="e75c5-413">分类 (DMX)</span><span class="sxs-lookup"><span data-stu-id="e75c5-413">Cluster &#40;DMX&#41;</span></span>](/sql/dmx/cluster-dmx)|<span data-ttu-id="e75c5-414">返回最可能包含输入事例的分类。</span><span class="sxs-lookup"><span data-stu-id="e75c5-414">Returns the cluster that is most likely to contain the input case.</span></span>|  
|[<span data-ttu-id="e75c5-415">ClusterDistance (DMX)</span><span class="sxs-lookup"><span data-stu-id="e75c5-415">ClusterDistance &#40;DMX&#41;</span></span>](/sql/dmx/clusterdistance-dmx)|<span data-ttu-id="e75c5-416">返回输入事例与指定分类之间的距离；如果未指定分类，则返回输入事例与可能性最大的分类之间的距离。</span><span class="sxs-lookup"><span data-stu-id="e75c5-416">Returns the distance of the input case from the specified cluster, or if no cluster is specified, the distance of the input case from the most likely cluster.</span></span><br /><br /> <span data-ttu-id="e75c5-417">返回输入事例属于指定分类的概率。</span><span class="sxs-lookup"><span data-stu-id="e75c5-417">Returns the probability that the input case belongs to the specified cluster.</span></span>|  
|[<span data-ttu-id="e75c5-418">ClusterProbability (DMX)</span><span class="sxs-lookup"><span data-stu-id="e75c5-418">ClusterProbability &#40;DMX&#41;</span></span>](/sql/dmx/clusterprobability-dmx)|<span data-ttu-id="e75c5-419">返回输入事例属于指定分类的概率。</span><span class="sxs-lookup"><span data-stu-id="e75c5-419">Returns the probability that the input case belongs to the specified cluster.</span></span>|  
|[<span data-ttu-id="e75c5-420">IsDescendant (DMX)</span><span class="sxs-lookup"><span data-stu-id="e75c5-420">IsDescendant &#40;DMX&#41;</span></span>](/sql/dmx/isdescendant-dmx)|<span data-ttu-id="e75c5-421">确定一个节点是否是模型中另一个节点的子节点。</span><span class="sxs-lookup"><span data-stu-id="e75c5-421">Determines whether one node is a child of another node in the model.</span></span>|  
|[<span data-ttu-id="e75c5-422">IsInNode (DMX)</span><span class="sxs-lookup"><span data-stu-id="e75c5-422">IsInNode &#40;DMX&#41;</span></span>](/sql/dmx/isinnode-dmx)|<span data-ttu-id="e75c5-423">指示指定的节点是否包含当前事例。</span><span class="sxs-lookup"><span data-stu-id="e75c5-423">Indicates whether the specified node contains the current case.</span></span>|  
|[<span data-ttu-id="e75c5-424">PredictAdjustedProbability (DMX)</span><span class="sxs-lookup"><span data-stu-id="e75c5-424">PredictAdjustedProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictadjustedprobability-dmx)|<span data-ttu-id="e75c5-425">返回加权的概率。</span><span class="sxs-lookup"><span data-stu-id="e75c5-425">Returns the weighted probability.</span></span>|  
|[<span data-ttu-id="e75c5-426">PredictAssociation (DMX)</span><span class="sxs-lookup"><span data-stu-id="e75c5-426">PredictAssociation &#40;DMX&#41;</span></span>](/sql/dmx/predictassociation-dmx)|<span data-ttu-id="e75c5-427">预测关联数据集中的成员身份。</span><span class="sxs-lookup"><span data-stu-id="e75c5-427">Predicts membership in an associative dataset.</span></span>|  
|[<span data-ttu-id="e75c5-428">PredictCaseLikelihood (DMX)</span><span class="sxs-lookup"><span data-stu-id="e75c5-428">PredictCaseLikelihood &#40;DMX&#41;</span></span>](/sql/dmx/predictcaselikelihood-dmx)|<span data-ttu-id="e75c5-429">返回输入事例适合现有模型的可能性。</span><span class="sxs-lookup"><span data-stu-id="e75c5-429">Returns the likelihood that an input case will fit in the existing model.</span></span>|  
|[<span data-ttu-id="e75c5-430">PredictHistogram (DMX)</span><span class="sxs-lookup"><span data-stu-id="e75c5-430">PredictHistogram &#40;DMX&#41;</span></span>](/sql/dmx/predicthistogram-dmx)|<span data-ttu-id="e75c5-431">返回与当前预测值相关的值的表。</span><span class="sxs-lookup"><span data-stu-id="e75c5-431">Returns a table of values related to the current predicted value.</span></span>|  
|[<span data-ttu-id="e75c5-432">PredictNodeId (DMX)</span><span class="sxs-lookup"><span data-stu-id="e75c5-432">PredictNodeId &#40;DMX&#41;</span></span>](/sql/dmx/predictnodeid-dmx)|<span data-ttu-id="e75c5-433">返回每个事例的 Node_ID。</span><span class="sxs-lookup"><span data-stu-id="e75c5-433">Returns the Node_ID for each case.</span></span>|  
|[<span data-ttu-id="e75c5-434">PredictProbability (DMX)</span><span class="sxs-lookup"><span data-stu-id="e75c5-434">PredictProbability &#40;DMX&#41;</span></span>](/sql/dmx/predictprobability-dmx)|<span data-ttu-id="e75c5-435">返回预测值的概率。</span><span class="sxs-lookup"><span data-stu-id="e75c5-435">Returns probability for the predicted value.</span></span>|  
|[<span data-ttu-id="e75c5-436">PredictStdev (DMX)</span><span class="sxs-lookup"><span data-stu-id="e75c5-436">PredictStdev &#40;DMX&#41;</span></span>](/sql/dmx/predictstdev-dmx)|<span data-ttu-id="e75c5-437">返回指定列的预测标准偏差。</span><span class="sxs-lookup"><span data-stu-id="e75c5-437">Returns the predicted standard deviation for the specified column.</span></span>|  
|[<span data-ttu-id="e75c5-438">PredictSupport (DMX)</span><span class="sxs-lookup"><span data-stu-id="e75c5-438">PredictSupport &#40;DMX&#41;</span></span>](/sql/dmx/predictsupport-dmx)|<span data-ttu-id="e75c5-439">返回指定状态的支持值。</span><span class="sxs-lookup"><span data-stu-id="e75c5-439">Returns the support value for a specified state.</span></span>|  
|[<span data-ttu-id="e75c5-440">PredictVariance (DMX)</span><span class="sxs-lookup"><span data-stu-id="e75c5-440">PredictVariance &#40;DMX&#41;</span></span>](/sql/dmx/predictvariance-dmx)|<span data-ttu-id="e75c5-441">返回指定列的方差。</span><span class="sxs-lookup"><span data-stu-id="e75c5-441">Returns the variance of a specified column.</span></span>|  
  
 <span data-ttu-id="e75c5-442">有关特定函数的语法，请参阅[数据挖掘扩展插件 (DMX) 函数引用](/sql/dmx/data-mining-extensions-dmx-function-reference)。</span><span class="sxs-lookup"><span data-stu-id="e75c5-442">For the syntax of specific functions, see [Data Mining Extensions &#40;DMX&#41; Function Reference](/sql/dmx/data-mining-extensions-dmx-function-reference).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e75c5-443">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e75c5-443">See Also</span></span>  
 <span data-ttu-id="e75c5-444">[数据挖掘查询](data-mining-queries.md) </span><span class="sxs-lookup"><span data-stu-id="e75c5-444">[Data Mining Queries](data-mining-queries.md) </span></span>  
 <span data-ttu-id="e75c5-445">[Microsoft 聚类分析算法技术参考](microsoft-clustering-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="e75c5-445">[Microsoft Clustering Algorithm Technical Reference](microsoft-clustering-algorithm-technical-reference.md) </span></span>  
 [<span data-ttu-id="e75c5-446">Microsoft Clustering Algorithm</span><span class="sxs-lookup"><span data-stu-id="e75c5-446">Microsoft Clustering Algorithm</span></span>](microsoft-clustering-algorithm.md)  
  
  
