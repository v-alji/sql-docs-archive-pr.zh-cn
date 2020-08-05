---
title: 用于聚类分析模型的挖掘模型内容 (Analysis Services 数据挖掘) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- nearest neighbor [Data Mining]
- clustering [Data Mining]
- mining model content, clustering models
- clustering algorithms [Analysis Services]
ms.assetid: aed1b7d3-8f20-4eeb-b156-0229f942cefd
author: minewiskan
ms.author: owend
ms.openlocfilehash: 400575d5c6ce8094b67500d15a86137302282fa7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581030"
---
# <a name="mining-model-content-for-clustering-models-analysis-services---data-mining"></a><span data-ttu-id="e453d-102">聚类分析模型的挖掘模型内容（Analysis Services – 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="e453d-102">Mining Model Content for Clustering Models (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="e453d-103">本主题介绍使用 Microsoft 聚类分析算法的模型特有的挖掘模型内容。</span><span class="sxs-lookup"><span data-stu-id="e453d-103">This topic describes mining model content that is specific to models that use the Microsoft Clustering algorithm.</span></span> <span data-ttu-id="e453d-104">有关所有模型类型的挖掘模型内容的常规说明，请参阅 [挖掘模型内容（Analysis Services - 数据挖掘）](mining-model-content-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="e453d-104">For a general explanation of mining model content for all model types, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
## <a name="understanding-the-structure-of-a-clustering-model"></a><span data-ttu-id="e453d-105">了解聚类分析模型的结构</span><span class="sxs-lookup"><span data-stu-id="e453d-105">Understanding the Structure of a Clustering Model</span></span>  
 <span data-ttu-id="e453d-106">聚类分析模型的结构很简单。</span><span class="sxs-lookup"><span data-stu-id="e453d-106">A clustering model has a simple structure.</span></span> <span data-ttu-id="e453d-107">每个模型均具有表示该模型及其元数据的单一父节点，且每个父节点均具有分类的平面列表 (NODE_TYPE = 5)。</span><span class="sxs-lookup"><span data-stu-id="e453d-107">Each model has a single parent node that represents the model and its metadata, and each parent node has a flat list of clusters (NODE_TYPE = 5).</span></span> <span data-ttu-id="e453d-108">下图显示了此组织。</span><span class="sxs-lookup"><span data-stu-id="e453d-108">This organization is shown in the following image.</span></span>  
  
 <span data-ttu-id="e453d-109">![聚类分析的模型内容结构](../media/modelcontentstructure-clust.gif "聚类分析的模型内容结构")</span><span class="sxs-lookup"><span data-stu-id="e453d-109">![structure of model content for clustering](../media/modelcontentstructure-clust.gif "structure of model content for clustering")</span></span>  
  
 <span data-ttu-id="e453d-110">每个子节点均表示一个分类，并包含有关该分类中事例属性的详细统计信息。</span><span class="sxs-lookup"><span data-stu-id="e453d-110">Each child node represents a single cluster and contains detailed statistics about the attributes of the cases in that cluster.</span></span> <span data-ttu-id="e453d-111">这包含该分类中事例数的计数以及将该分类与其他分类区分开来的值的分布。</span><span class="sxs-lookup"><span data-stu-id="e453d-111">This includes a count of the number of cases in the cluster, and the distribution of values that distinguish the cluster from other clusters.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e453d-112">您无需遍历节点来获取分类的计数或说明，该模型父节点也会对分类进行计数并列出分类。</span><span class="sxs-lookup"><span data-stu-id="e453d-112">You do not need to iterate through the nodes to get a count or description of the clusters; the model parent node also counts and lists the clusters.</span></span>  
  
 <span data-ttu-id="e453d-113">父节点包含有用的统计信息，用于描述所有定型事例的实际分布。</span><span class="sxs-lookup"><span data-stu-id="e453d-113">The parent node contains useful statistics that describe the actual distribution of all the training cases.</span></span> <span data-ttu-id="e453d-114">可在嵌套表列 NODE_DISTRIBUTION 中找到这些统计信息。</span><span class="sxs-lookup"><span data-stu-id="e453d-114">These statistics are found in the nested table column, NODE_DISTRIBUTION.</span></span> <span data-ttu-id="e453d-115">例如，下表显示了 NODE_DISTRIBUTION 表中的若干行，这些行描述了你在 `TM_Clustering`数据挖掘基础教程 [中创建的聚类分析模型](../../tutorials/basic-data-mining-tutorial.md)的客户人口统计信息的分布：</span><span class="sxs-lookup"><span data-stu-id="e453d-115">For example, the following table shows several rows from the NODE_DISTRIBUTION table that describe the distribution of customer demographics for the clustering model, `TM_Clustering`, that you create in the [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md):</span></span>  
  
|<span data-ttu-id="e453d-116">ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="e453d-116">ATTRIBUTE_NAME</span></span>|<span data-ttu-id="e453d-117">ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="e453d-117">ATRIBUTE_VALUE</span></span>|<span data-ttu-id="e453d-118">Support</span><span class="sxs-lookup"><span data-stu-id="e453d-118">SUPPORT</span></span>|<span data-ttu-id="e453d-119">PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="e453d-119">PROBABILITY</span></span>|<span data-ttu-id="e453d-120">方差</span><span class="sxs-lookup"><span data-stu-id="e453d-120">VARIANCE</span></span>|<span data-ttu-id="e453d-121">VALUE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e453d-121">VALUE_TYPE</span></span>|  
|---------------------|---------------------|-------------|-----------------|--------------|-----------------|  
|<span data-ttu-id="e453d-122">年限</span><span class="sxs-lookup"><span data-stu-id="e453d-122">Age</span></span>|<span data-ttu-id="e453d-123">Missing</span><span class="sxs-lookup"><span data-stu-id="e453d-123">Missing</span></span>|<span data-ttu-id="e453d-124">0</span><span class="sxs-lookup"><span data-stu-id="e453d-124">0</span></span>|<span data-ttu-id="e453d-125">0</span><span class="sxs-lookup"><span data-stu-id="e453d-125">0</span></span>|<span data-ttu-id="e453d-126">0</span><span class="sxs-lookup"><span data-stu-id="e453d-126">0</span></span>|<span data-ttu-id="e453d-127">1（缺失）</span><span class="sxs-lookup"><span data-stu-id="e453d-127">1 (Missing)</span></span>|  
|<span data-ttu-id="e453d-128">年限</span><span class="sxs-lookup"><span data-stu-id="e453d-128">Age</span></span>|<span data-ttu-id="e453d-129">44.9016152716593</span><span class="sxs-lookup"><span data-stu-id="e453d-129">44.9016152716593</span></span>|<span data-ttu-id="e453d-130">12939</span><span class="sxs-lookup"><span data-stu-id="e453d-130">12939</span></span>|<span data-ttu-id="e453d-131">1</span><span class="sxs-lookup"><span data-stu-id="e453d-131">1</span></span>|<span data-ttu-id="e453d-132">125.663453102554</span><span class="sxs-lookup"><span data-stu-id="e453d-132">125.663453102554</span></span>|<span data-ttu-id="e453d-133">3（连续）</span><span class="sxs-lookup"><span data-stu-id="e453d-133">3 (Continuous)</span></span>|  
|<span data-ttu-id="e453d-134">性别</span><span class="sxs-lookup"><span data-stu-id="e453d-134">Gender</span></span>|<span data-ttu-id="e453d-135">Missing</span><span class="sxs-lookup"><span data-stu-id="e453d-135">Missing</span></span>|<span data-ttu-id="e453d-136">0</span><span class="sxs-lookup"><span data-stu-id="e453d-136">0</span></span>|<span data-ttu-id="e453d-137">0</span><span class="sxs-lookup"><span data-stu-id="e453d-137">0</span></span>|<span data-ttu-id="e453d-138">0</span><span class="sxs-lookup"><span data-stu-id="e453d-138">0</span></span>|<span data-ttu-id="e453d-139">1（缺失）</span><span class="sxs-lookup"><span data-stu-id="e453d-139">1 (Missing)</span></span>|  
|<span data-ttu-id="e453d-140">性别</span><span class="sxs-lookup"><span data-stu-id="e453d-140">Gender</span></span>|<span data-ttu-id="e453d-141">F</span><span class="sxs-lookup"><span data-stu-id="e453d-141">F</span></span>|<span data-ttu-id="e453d-142">6350</span><span class="sxs-lookup"><span data-stu-id="e453d-142">6350</span></span>|<span data-ttu-id="e453d-143">0.490764355823479</span><span class="sxs-lookup"><span data-stu-id="e453d-143">0.490764355823479</span></span>|<span data-ttu-id="e453d-144">0</span><span class="sxs-lookup"><span data-stu-id="e453d-144">0</span></span>|<span data-ttu-id="e453d-145">4（离散）</span><span class="sxs-lookup"><span data-stu-id="e453d-145">4 (Discrete)</span></span>|  
|<span data-ttu-id="e453d-146">性别</span><span class="sxs-lookup"><span data-stu-id="e453d-146">Gender</span></span>|<span data-ttu-id="e453d-147">M</span><span class="sxs-lookup"><span data-stu-id="e453d-147">M</span></span>|<span data-ttu-id="e453d-148">6589</span><span class="sxs-lookup"><span data-stu-id="e453d-148">6589</span></span>|<span data-ttu-id="e453d-149">0.509235644176521</span><span class="sxs-lookup"><span data-stu-id="e453d-149">0.509235644176521</span></span>|<span data-ttu-id="e453d-150">0</span><span class="sxs-lookup"><span data-stu-id="e453d-150">0</span></span>|<span data-ttu-id="e453d-151">4（离散）</span><span class="sxs-lookup"><span data-stu-id="e453d-151">4 (Discrete)</span></span>|  
  
 <span data-ttu-id="e453d-152">从这些结果可以看出，12939 个事例用于生成此模型，男女的比例约为 50-50，平均年龄为 44。</span><span class="sxs-lookup"><span data-stu-id="e453d-152">From these results, you can see that there were 12939 cases used to build the model, that the ratio of males to females was about 50-50, and that the mean age was 44.</span></span> <span data-ttu-id="e453d-153">根据所报告的属性为连续数值数据类型（如年龄），还是为离散值类型（如性别），描述性统计信息也有所差异。</span><span class="sxs-lookup"><span data-stu-id="e453d-153">The descriptive statistics vary depending on whether the attribute being reported is a continuous numeric data type, such as age, or a discrete value type, such as gender.</span></span> <span data-ttu-id="e453d-154">对于连续数据类型，计算统计度量值“均值 \*\* ”和“方差 \*\* ”，而对于离散数据类型，则计算“概率 \*\* ”和“支持 \*\* ”。</span><span class="sxs-lookup"><span data-stu-id="e453d-154">The statistical measures *mean* and *variance* are computed for continuous data types, whereas *probability* and *support* are computed for discrete data types.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e453d-155">该方差表示分类的总方差。</span><span class="sxs-lookup"><span data-stu-id="e453d-155">The variance represents the total variance for the cluster.</span></span> <span data-ttu-id="e453d-156">如果方差的值较小，则表示列中的大多数值与均值很接近。</span><span class="sxs-lookup"><span data-stu-id="e453d-156">When the value for variance is small, it indicates that most values in the column were fairly close to the mean.</span></span> <span data-ttu-id="e453d-157">若要获取标准偏差，请计算该方差的平方根。</span><span class="sxs-lookup"><span data-stu-id="e453d-157">To obtain the standard deviation, calculate the square root of the variance.</span></span>  
  
 <span data-ttu-id="e453d-158">请注意，对于每个属性，都有一个 `Missing` 值类型，可告诉您有多少个事例没有该属性的数据。</span><span class="sxs-lookup"><span data-stu-id="e453d-158">Note that for each of the attributes there is a `Missing` value type that tells you how many cases had no data for that attribute.</span></span> <span data-ttu-id="e453d-159">缺少的数据可能会很重要，影响计算的方式也会不同，具体取决于数据类型。</span><span class="sxs-lookup"><span data-stu-id="e453d-159">Missing data can be significant and affects calculations in different ways, depending on the data type.</span></span> <span data-ttu-id="e453d-160">有关详细信息，请参阅 [缺失值（Analysis Services - 数据挖掘）](missing-values-analysis-services-data-mining.md)预定义的这些标志以外，第三方插件还可能具有其他建模标志。</span><span class="sxs-lookup"><span data-stu-id="e453d-160">For more information, see [Missing Values &#40;Analysis Services - Data Mining&#41;](missing-values-analysis-services-data-mining.md).</span></span>  
  
## <a name="model-content-for-a-clustering-model"></a><span data-ttu-id="e453d-161">聚类分析模型的模型内容</span><span class="sxs-lookup"><span data-stu-id="e453d-161">Model Content for a Clustering Model</span></span>  
 <span data-ttu-id="e453d-162">本节仅针对与聚类分析模型有关的挖掘模型内容中的这些列给出详细信息和示例。</span><span class="sxs-lookup"><span data-stu-id="e453d-162">This section provides detail and examples only for those columns in the mining model content that are relevant for clustering models.</span></span>  
  
 <span data-ttu-id="e453d-163">有关架构行集中通用列（例如 MODEL_CATALOG 和 MODEL_NAME）的信息，请参阅 [挖掘模型内容（Analysis Services - 数据挖掘）](mining-model-content-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="e453d-163">For information about the general-purpose columns in the schema rowset, such as MODEL_CATALOG and MODEL_NAME, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="e453d-164">MODEL_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e453d-164">MODEL_CATALOG</span></span>  
 <span data-ttu-id="e453d-165">存储模型的数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="e453d-165">Name of the database where the model is stored.</span></span>  
  
 <span data-ttu-id="e453d-166">MODEL_NAME</span><span class="sxs-lookup"><span data-stu-id="e453d-166">MODEL_NAME</span></span>  
 <span data-ttu-id="e453d-167">模型的名称。</span><span class="sxs-lookup"><span data-stu-id="e453d-167">Name of the model.</span></span>  
  
 <span data-ttu-id="e453d-168">ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="e453d-168">ATTRIBUTE_NAME</span></span>  
 <span data-ttu-id="e453d-169">在聚类分析模型中始终空白，原因是在该模式下没有任何可预测属性。</span><span class="sxs-lookup"><span data-stu-id="e453d-169">Always blank in clustering models because there is no predictable attribute in the mode.</span></span>  
  
 <span data-ttu-id="e453d-170">NODE_NAME</span><span class="sxs-lookup"><span data-stu-id="e453d-170">NODE_NAME</span></span>  
 <span data-ttu-id="e453d-171">始终与 NODE_UNIQUE_NAME 相同。</span><span class="sxs-lookup"><span data-stu-id="e453d-171">Always same as NODE_UNIQUE_NAME.</span></span>  
  
 <span data-ttu-id="e453d-172">NODE_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="e453d-172">NODE_UNIQUE_NAME</span></span>  
 <span data-ttu-id="e453d-173">此模型中节点的唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="e453d-173">A unique identifier for the node within the model.</span></span> <span data-ttu-id="e453d-174">此值不能更改。</span><span class="sxs-lookup"><span data-stu-id="e453d-174">This value cannot be changed.</span></span>  
  
 <span data-ttu-id="e453d-175">NODE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e453d-175">NODE_TYPE</span></span>  
 <span data-ttu-id="e453d-176">聚类分析模型输出以下节点类型：</span><span class="sxs-lookup"><span data-stu-id="e453d-176">A clustering model outputs the following node types:</span></span>  
  
|<span data-ttu-id="e453d-177">节点 ID 和名称</span><span class="sxs-lookup"><span data-stu-id="e453d-177">Node ID and Name</span></span>|<span data-ttu-id="e453d-178">说明</span><span class="sxs-lookup"><span data-stu-id="e453d-178">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="e453d-179">1（模型）</span><span class="sxs-lookup"><span data-stu-id="e453d-179">1 (Model)</span></span>|<span data-ttu-id="e453d-180">模型的根节点。</span><span class="sxs-lookup"><span data-stu-id="e453d-180">Root node for model.</span></span>|  
|<span data-ttu-id="e453d-181">5（分类）</span><span class="sxs-lookup"><span data-stu-id="e453d-181">5 (Cluster)</span></span>|<span data-ttu-id="e453d-182">包含分类中的事例计数、分类中事例的特征以及描述分类中的值的统计信息。</span><span class="sxs-lookup"><span data-stu-id="e453d-182">Contains a count of cases in the cluster, the characteristics of cases in the cluster, and statistics that describe the values in the cluster.</span></span>|  
  
 <span data-ttu-id="e453d-183">NODE_CAPTION</span><span class="sxs-lookup"><span data-stu-id="e453d-183">NODE_CAPTION</span></span>  
 <span data-ttu-id="e453d-184">显示时使用的友好名称。</span><span class="sxs-lookup"><span data-stu-id="e453d-184">A friendly name for display purposes.</span></span> <span data-ttu-id="e453d-185">当创建某个模型时，会将 NODE_UNIQUE_NAME 值自动用作标题。</span><span class="sxs-lookup"><span data-stu-id="e453d-185">When you create a model, the value of NODE_UNIQUE_NAME is automatically used as the caption.</span></span> <span data-ttu-id="e453d-186">但是，您可以用编程方式或使用查看器更改 NODE_CAPTION 的值，以更新该分类的显示名称。</span><span class="sxs-lookup"><span data-stu-id="e453d-186">However, you can change the value for NODE_CAPTION to update the display name for the cluster, either programmatically or by using the viewer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e453d-187">重新处理该模型时，新的值将覆盖所有的名称更改。</span><span class="sxs-lookup"><span data-stu-id="e453d-187">When you reprocess the model, all name changes will be overwritten by the new values.</span></span> <span data-ttu-id="e453d-188">您不能在模型中保留名称，也不能跟踪不同模型版本之间的分类成员身份中的更改。</span><span class="sxs-lookup"><span data-stu-id="e453d-188">You cannot persist names in the model, or track changes in cluster membership between different versions of a model.</span></span>  
  
 <span data-ttu-id="e453d-189">CHILDREN_CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="e453d-189">CHILDREN_CARDINALITY</span></span>  
 <span data-ttu-id="e453d-190">对节点所具有的子节点数的估计。</span><span class="sxs-lookup"><span data-stu-id="e453d-190">An estimate of the number of children that the node has.</span></span>  
  
 <span data-ttu-id="e453d-191">**父节点** 指示模型中分类的数目。</span><span class="sxs-lookup"><span data-stu-id="e453d-191">**Parent node** Indicates the number of clusters in the model.</span></span>  
  
 <span data-ttu-id="e453d-192">**群集节点** 始终为 0。</span><span class="sxs-lookup"><span data-stu-id="e453d-192">**Cluster nodes** Always 0.</span></span>  
  
 <span data-ttu-id="e453d-193">PARENT_UNIQUE_NAME</span><span class="sxs-lookup"><span data-stu-id="e453d-193">PARENT_UNIQUE_NAME</span></span>  
 <span data-ttu-id="e453d-194">节点的父节点的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="e453d-194">The unique name of the node's parent.</span></span>  
  
 <span data-ttu-id="e453d-195">**父节点** 始终为 NULL</span><span class="sxs-lookup"><span data-stu-id="e453d-195">**Parent node** Always NULL</span></span>  
  
 <span data-ttu-id="e453d-196">**群集节点** 通常为 000。</span><span class="sxs-lookup"><span data-stu-id="e453d-196">**Cluster nodes** Usually 000.</span></span>  
  
 <span data-ttu-id="e453d-197">NODE_DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e453d-197">NODE_DESCRIPTION</span></span>  
 <span data-ttu-id="e453d-198">节点的说明。</span><span class="sxs-lookup"><span data-stu-id="e453d-198">A description of the node.</span></span>  
  
 <span data-ttu-id="e453d-199">**父节点**：始终为“(全部)”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e453d-199">**Parent node** Always **(All)**.</span></span>  
  
 <span data-ttu-id="e453d-200">**群集节点** ：一个以逗号分隔的列表，包含用于将该分类与其他分类区分开来的主要属性。</span><span class="sxs-lookup"><span data-stu-id="e453d-200">**Cluster nodes** A comma-separated list of the primary attributes that distinguish the cluster from other clusters.</span></span>  
  
 <span data-ttu-id="e453d-201">NODE_RULE</span><span class="sxs-lookup"><span data-stu-id="e453d-201">NODE_RULE</span></span>  
 <span data-ttu-id="e453d-202">不用于聚类分析模型。</span><span class="sxs-lookup"><span data-stu-id="e453d-202">Not used for clustering models.</span></span>  
  
 <span data-ttu-id="e453d-203">MARGINAL_RULE</span><span class="sxs-lookup"><span data-stu-id="e453d-203">MARGINAL_RULE</span></span>  
 <span data-ttu-id="e453d-204">不用于聚类分析模型。</span><span class="sxs-lookup"><span data-stu-id="e453d-204">Not used for clustering models.</span></span>  
  
 <span data-ttu-id="e453d-205">NODE_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="e453d-205">NODE_PROBABILITY</span></span>  
 <span data-ttu-id="e453d-206">与此节点相关联的概率。</span><span class="sxs-lookup"><span data-stu-id="e453d-206">The probability associated with this node.</span></span> <span data-ttu-id="e453d-207">**父节点** 始终为 1。</span><span class="sxs-lookup"><span data-stu-id="e453d-207">**Parent node** Always 1.</span></span>  
  
 <span data-ttu-id="e453d-208">**群集节点** 该概率表示属性的组合概率，其中根据用于创建聚类分析模型的算法，会有某些调整。</span><span class="sxs-lookup"><span data-stu-id="e453d-208">**Cluster nodes** The probability represents the compound probability of the attributes, with some adjustments depending on the algorithm used to create the clustering model.</span></span>  
  
 <span data-ttu-id="e453d-209">MARGINAL_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="e453d-209">MARGINAL_PROBABILITY</span></span>  
 <span data-ttu-id="e453d-210">从父节点到达该节点的概率。</span><span class="sxs-lookup"><span data-stu-id="e453d-210">The probability of reaching the node from the parent node.</span></span> <span data-ttu-id="e453d-211">在聚类分析模型中，边缘概率始终与此节点概率相同。</span><span class="sxs-lookup"><span data-stu-id="e453d-211">In a clustering model, the marginal probability is always the same as the node probability.</span></span>  
  
 <span data-ttu-id="e453d-212">NODE_DISTRIBUTION</span><span class="sxs-lookup"><span data-stu-id="e453d-212">NODE_DISTRIBUTION</span></span>  
 <span data-ttu-id="e453d-213">包含节点的概率直方图的表。</span><span class="sxs-lookup"><span data-stu-id="e453d-213">A table that contains the probability histogram of the node.</span></span>  
  
 <span data-ttu-id="e453d-214">**父节点** 请参阅对本主题的介绍。</span><span class="sxs-lookup"><span data-stu-id="e453d-214">**Parent node** See the Introduction to this topic.</span></span>  
  
 <span data-ttu-id="e453d-215">**群集节点** 表示包含在此分类中的事例的属性和值的分布。</span><span class="sxs-lookup"><span data-stu-id="e453d-215">**Cluster nodes** Represents the distribution of attributes and values for cases that are included in this cluster.</span></span>  
  
 <span data-ttu-id="e453d-216">NODE_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="e453d-216">NODE_SUPPORT</span></span>  
 <span data-ttu-id="e453d-217">支持此节点的事例的数目。</span><span class="sxs-lookup"><span data-stu-id="e453d-217">The number of cases that support this node.</span></span> <span data-ttu-id="e453d-218">**父节点** 指示整个模型的定型事例数。</span><span class="sxs-lookup"><span data-stu-id="e453d-218">**Parent node** Indicates the number of training cases for the entire model.</span></span>  
  
 <span data-ttu-id="e453d-219">**群集节点** 指示将分类的大小作为事例数。</span><span class="sxs-lookup"><span data-stu-id="e453d-219">**Cluster nodes** Indicates the size of the cluster as a number of cases.</span></span>  
  
 <span data-ttu-id="e453d-220">**注意** ：如果模型使用 K-Means 聚类分析，则每个事例只能属于一个群集。</span><span class="sxs-lookup"><span data-stu-id="e453d-220">**Note** If the model uses K-Means clustering, each case can belong to only one cluster.</span></span> <span data-ttu-id="e453d-221">但是，如果模型使用 EM 聚类分析，则每个事例可以属于不同的分类，而且对于事例所属的每个分类，该事例都将分配有一个加权距离。</span><span class="sxs-lookup"><span data-stu-id="e453d-221">However, if the model uses EM clustering, each case can belong to different cluster, and the case is assigned a weighted distance for each cluster to which it belongs.</span></span> <span data-ttu-id="e453d-222">因此，对于 EM 模型来说，对单个分类支持的和将大于对整个模型的支持。</span><span class="sxs-lookup"><span data-stu-id="e453d-222">Therefore, for EM models the sum of support for an individual cluster is greater than support for the overall model.</span></span>  
  
 <span data-ttu-id="e453d-223">MSOLAP_MODEL_COLUMN</span><span class="sxs-lookup"><span data-stu-id="e453d-223">MSOLAP_MODEL_COLUMN</span></span>  
 <span data-ttu-id="e453d-224">不用于聚类分析模型。</span><span class="sxs-lookup"><span data-stu-id="e453d-224">Not used for clustering models.</span></span>  
  
 <span data-ttu-id="e453d-225">MSOLAP_NODE_SCORE</span><span class="sxs-lookup"><span data-stu-id="e453d-225">MSOLAP_NODE_SCORE</span></span>  
 <span data-ttu-id="e453d-226">显示与此节点关联的分数。</span><span class="sxs-lookup"><span data-stu-id="e453d-226">Displays a score associated with the node.</span></span>  
  
 <span data-ttu-id="e453d-227">**父节点** ：聚类分析模型的 Bayesian 信息标准 ( BIC) 分数。</span><span class="sxs-lookup"><span data-stu-id="e453d-227">**Parent node** The Bayesian Information Criterion (BIC) score for the clustering model.</span></span>  
  
 <span data-ttu-id="e453d-228">**群集节点** 始终为 0。</span><span class="sxs-lookup"><span data-stu-id="e453d-228">**Cluster nodes** Always 0.</span></span>  
  
 <span data-ttu-id="e453d-229">MSOLAP_NODE_SHORT_CAPTION</span><span class="sxs-lookup"><span data-stu-id="e453d-229">MSOLAP_NODE_SHORT_CAPTION</span></span>  
 <span data-ttu-id="e453d-230">用于显示的标签。</span><span class="sxs-lookup"><span data-stu-id="e453d-230">A label used for display purposes.</span></span> <span data-ttu-id="e453d-231">此标题无法更改。</span><span class="sxs-lookup"><span data-stu-id="e453d-231">You cannot change this caption.</span></span>  
  
 <span data-ttu-id="e453d-232">**父节点** 模型的类型：聚类分析模型</span><span class="sxs-lookup"><span data-stu-id="e453d-232">**Parent node** The type of model: Cluster model</span></span>  
  
 <span data-ttu-id="e453d-233">**群集节点** 分类的名称。</span><span class="sxs-lookup"><span data-stu-id="e453d-233">**Cluster nodes** The name of the cluster.</span></span> <span data-ttu-id="e453d-234">示例：分类 1。</span><span class="sxs-lookup"><span data-stu-id="e453d-234">Example: Cluster 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e453d-235">备注</span><span class="sxs-lookup"><span data-stu-id="e453d-235">Remarks</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="e453d-236">提供了用于创建聚类分析模型的多种方法。</span><span class="sxs-lookup"><span data-stu-id="e453d-236">provides multiple methods for creating a clustering model.</span></span> <span data-ttu-id="e453d-237">如果不了解所使用的模型是使用哪种方法创建的，可以使用 ADOMD 客户端或 AMO，也可以通过查询该数据挖掘架构行集，以编程方式检索该模型的元数据。</span><span class="sxs-lookup"><span data-stu-id="e453d-237">If you do not know which method was used to create the model that you are working with, you can retrieve the model metadata programmatically, by using an ADOMD client or AMO, or by querying the data mining schema rowset.</span></span> <span data-ttu-id="e453d-238">有关详细信息，请参阅 [查询用于创建挖掘模型的参数](query-the-parameters-used-to-create-a-mining-model.md)。</span><span class="sxs-lookup"><span data-stu-id="e453d-238">For more information, see [Query the Parameters Used to Create a Mining Model](query-the-parameters-used-to-create-a-mining-model.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e453d-239">无论使用哪一个聚类分析方法或参数，模型的结构和内容都保持不变。</span><span class="sxs-lookup"><span data-stu-id="e453d-239">The structure and content of the model stay the same, regardless of which clustering method or parameters you use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e453d-240">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e453d-240">See Also</span></span>  
 <span data-ttu-id="e453d-241">[挖掘模型内容 &#40;Analysis Services 数据挖掘&#41;](mining-model-content-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="e453d-241">[Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="e453d-242">[数据挖掘模型查看器](data-mining-model-viewers.md) </span><span class="sxs-lookup"><span data-stu-id="e453d-242">[Data Mining Model Viewers](data-mining-model-viewers.md) </span></span>  
 <span data-ttu-id="e453d-243">[Microsoft 聚类分析算法](microsoft-clustering-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="e453d-243">[Microsoft Clustering Algorithm](microsoft-clustering-algorithm.md) </span></span>  
 [<span data-ttu-id="e453d-244">数据挖掘查询</span><span class="sxs-lookup"><span data-stu-id="e453d-244">Data Mining Queries</span></span>](data-mining-queries.md)  
  
  
