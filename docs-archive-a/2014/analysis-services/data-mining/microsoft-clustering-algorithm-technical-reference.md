---
title: Microsoft 聚类分析算法技术参考 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- clustering [Data Mining]
- MAXIMUM_INPUT_ATTRIBUTES parameter
- CLUSTER_SEED parameter
- MODELLING_CARDINALITY parameter
- MINIMUM_SUPPORT parameter
- STOPPING_TOLERANCE parameter
- MAXIMUM_STATES parameter
- SAMPLE_SIZE parameter
- CLUSTERING_METHOD parameter
- soft clustering [Data Mining]
- clustering algorithms [Analysis Services]
- CLUSTER_COUNT parameter
ms.assetid: ec40868a-6dc7-4dfa-aadc-dedf69e555eb
author: minewiskan
ms.author: owend
ms.openlocfilehash: ee9019f821c5608527e0bdca5eddc8f1ead52f41
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588148"
---
# <a name="microsoft-clustering-algorithm-technical-reference"></a><span data-ttu-id="9a597-102">Microsoft 聚类分析算法技术参考</span><span class="sxs-lookup"><span data-stu-id="9a597-102">Microsoft Clustering Algorithm Technical Reference</span></span>
  <span data-ttu-id="9a597-103">本节说明 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 聚类分析算法的实现，包括可用来控制聚类分析模型的行为的参数。</span><span class="sxs-lookup"><span data-stu-id="9a597-103">This section explains the implementation of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Clustering algorithm, including the parameters that you can use to control the behavior of clustering models.</span></span> <span data-ttu-id="9a597-104">还提供关于在创建和处理聚类分析模型时如何提高性能的指南。</span><span class="sxs-lookup"><span data-stu-id="9a597-104">It also provides guidance about how to improve performance when you create and process clustering models.</span></span>  
  
 <span data-ttu-id="9a597-105">有关如何使用聚类分析模型的其他信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="9a597-105">For additional information about how to use clustering models, see the following topics:</span></span>  
  
-   [<span data-ttu-id="9a597-106">聚类分析模型的挖掘模型内容（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="9a597-106">Mining Model Content for Clustering Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-clustering-models-analysis-services-data-mining.md)  
  
-   [<span data-ttu-id="9a597-107">聚类分析模型查询示例</span><span class="sxs-lookup"><span data-stu-id="9a597-107">Clustering Model Query Examples</span></span>](clustering-model-query-examples.md)  
  
## <a name="implementation-of-the-microsoft-clustering-algorithm"></a><span data-ttu-id="9a597-108">Microsoft 聚类分析算法的实现</span><span class="sxs-lookup"><span data-stu-id="9a597-108">Implementation of the Microsoft Clustering Algorithm</span></span>  
 <span data-ttu-id="9a597-109">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 聚类分析算法提供两种创建分类并为分类分配数据点的方法。</span><span class="sxs-lookup"><span data-stu-id="9a597-109">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Clustering algorithm provides two methods for creating clusters and assigning data points to the clusters.</span></span> <span data-ttu-id="9a597-110">第一种方法是 *K-means* 算法，这是一种较难的聚类分析方法。</span><span class="sxs-lookup"><span data-stu-id="9a597-110">The first, the *K-means* algorithm, is a hard clustering method.</span></span> <span data-ttu-id="9a597-111">这意味着一个数据点只能属于一个分类，并会为该分类中的每个数据点的成员身份计算一个概率。</span><span class="sxs-lookup"><span data-stu-id="9a597-111">This means that a data point can belong to only one cluster, and that a single probability is calculated for the membership of each data point in that cluster.</span></span> <span data-ttu-id="9a597-112">第二种方法是期望值最大化 (EM) 方法，这是软聚类分析方法。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="9a597-112">The second method, the *Expectation Maximization* (EM) method, is a *soft clustering* method.</span></span> <span data-ttu-id="9a597-113">这意味着一个数据点总是属于多个分类，并会为每个数据点和分类的组合计算一个概率。</span><span class="sxs-lookup"><span data-stu-id="9a597-113">This means that a data point always belongs to multiple clusters, and that a probability is calculated for each combination of data point and cluster.</span></span>  
  
 <span data-ttu-id="9a597-114">可以通过设置 *CLUSTERING_METHOD* 参数来选择要使用的算法。</span><span class="sxs-lookup"><span data-stu-id="9a597-114">You can choose which algorithm to use by setting the *CLUSTERING_METHOD* parameter.</span></span> <span data-ttu-id="9a597-115">聚类分析的默认方法是可缩放的 EM。</span><span class="sxs-lookup"><span data-stu-id="9a597-115">The default method for clustering is scalable EM.</span></span>  
  
### <a name="em-clustering"></a><span data-ttu-id="9a597-116">EM 聚类分析</span><span class="sxs-lookup"><span data-stu-id="9a597-116">EM Clustering</span></span>  
 <span data-ttu-id="9a597-117">在 EM 聚类分析中，此算法反复优化初始分类模型以适合数据，并确定数据点存在于某个分类中的概率。</span><span class="sxs-lookup"><span data-stu-id="9a597-117">In EM clustering, the algorithm iteratively refines an initial cluster model to fit the data and determines the probability that a data point exists in a cluster.</span></span> <span data-ttu-id="9a597-118">当概率模型适合于数据时，此算法终止这一过程。</span><span class="sxs-lookup"><span data-stu-id="9a597-118">The algorithm ends the process when the probabilistic model fits the data.</span></span> <span data-ttu-id="9a597-119">用于确定是否适合的函数是数据适合模型的对数可能性。</span><span class="sxs-lookup"><span data-stu-id="9a597-119">The function used to determine the fit is the log-likelihood of the data given the model.</span></span>  
  
 <span data-ttu-id="9a597-120">如果在此过程中生成空分类，或者一个或多个分类的成员身份低于给定的阈值，则具有低填充率的分类会以新数据点重设种子，并且 EM 算法重新运行。</span><span class="sxs-lookup"><span data-stu-id="9a597-120">If empty clusters are generated during the process, or if the membership of one or more of the clusters falls below a given threshold, the clusters with low populations are reseeded at new points and the EM algorithm is rerun.</span></span>  
  
 <span data-ttu-id="9a597-121">EM 聚类分析方法的结果是概率性的。</span><span class="sxs-lookup"><span data-stu-id="9a597-121">The results of the EM clustering method are probabilistic.</span></span> <span data-ttu-id="9a597-122">这意味着每个数据点都属于所有分类，但数据点向分类的每次分配都有一个不同的概率。</span><span class="sxs-lookup"><span data-stu-id="9a597-122">This means that every data point belongs to all clusters, but each assignment of a data point to a cluster has a different probability.</span></span> <span data-ttu-id="9a597-123">因为此方法允许分类重叠，所以所有分类中的项的总数可能超过定型集中的总项数。</span><span class="sxs-lookup"><span data-stu-id="9a597-123">Because the method allows for clusters to overlap, the sum of items in all the clusters may exceed the total items in the training set.</span></span> <span data-ttu-id="9a597-124">在挖掘模型结果中，指示支持的分数会相应地调整以说明这一情况。</span><span class="sxs-lookup"><span data-stu-id="9a597-124">In the mining model results, scores that indicate support are adjusted to account for this.</span></span>  
  
 <span data-ttu-id="9a597-125">EM 算法是 Microsoft 聚类分析模型中使用的默认算法。</span><span class="sxs-lookup"><span data-stu-id="9a597-125">The EM algorithm is the default algorithm used in Microsoft clustering models.</span></span> <span data-ttu-id="9a597-126">此算法之所以用作默认算法，是因为与 k-means 聚类分析算法相比，它有多个优点：</span><span class="sxs-lookup"><span data-stu-id="9a597-126">This algorithm is used as the default because it offers multiple advantages in comparison to k-means clustering:</span></span>  
  
-   <span data-ttu-id="9a597-127">最多需要一次数据库扫描。</span><span class="sxs-lookup"><span data-stu-id="9a597-127">Requires one database scan, at most.</span></span>  
  
-   <span data-ttu-id="9a597-128">工作时不受内存 (RAM) 限制。</span><span class="sxs-lookup"><span data-stu-id="9a597-128">Will work despite limited memory (RAM).</span></span>  
  
-   <span data-ttu-id="9a597-129">能够使用只进游标。</span><span class="sxs-lookup"><span data-stu-id="9a597-129">Has the ability to use a forward-only cursor.</span></span>  
  
-   <span data-ttu-id="9a597-130">优于抽样方法。</span><span class="sxs-lookup"><span data-stu-id="9a597-130">Outperforms sampling approaches.</span></span>  
  
 <span data-ttu-id="9a597-131">Microsoft 实现提供两个选项：可缩放 EM 和不可缩放 EM。</span><span class="sxs-lookup"><span data-stu-id="9a597-131">The Microsoft implementation provides two options: scalable and non-scalable EM.</span></span> <span data-ttu-id="9a597-132">默认情况下，在可缩放 EM 中，前 50,000 个记录用于为初始扫描设种子。</span><span class="sxs-lookup"><span data-stu-id="9a597-132">By default, in scalable EM, the first 50,000 records are used to seed the initial scan.</span></span> <span data-ttu-id="9a597-133">如果成功，则模型将仅仅使用这些数据。</span><span class="sxs-lookup"><span data-stu-id="9a597-133">If this is successful, the model uses this data only.</span></span> <span data-ttu-id="9a597-134">如果使用 50,000 个记录时模型不适合，则会继续读取 50,000 个记录。</span><span class="sxs-lookup"><span data-stu-id="9a597-134">If the model cannot be fit using 50,000 records, an additional 50,000 records are read.</span></span> <span data-ttu-id="9a597-135">在不可缩放 EM 中，总是读取整个数据集，而不考虑数据集的大小。</span><span class="sxs-lookup"><span data-stu-id="9a597-135">In non-scalable EM, the entire dataset is read regardless of its size.</span></span> <span data-ttu-id="9a597-136">此方法可能会创建更准确的分类，但内存需求非常高。</span><span class="sxs-lookup"><span data-stu-id="9a597-136">This method might create more accurate clusters, but the memory requirements can be significant.</span></span> <span data-ttu-id="9a597-137">因为可缩放 EM 作用于本地缓冲区，所以循环访问数据要快得多，并且此算法对 CPU 内存缓存的利用率比不可缩放 EM 要高得多。</span><span class="sxs-lookup"><span data-stu-id="9a597-137">Because scalable EM operates on a local buffer, iterating through the data is much faster, and the algorithm makes much better use of the CPU memory cache than non-scalable EM.</span></span> <span data-ttu-id="9a597-138">此外，可缩放 EM 比不可缩放 EM 快三倍，即使所有数据都可容纳于主内存中也是如此。</span><span class="sxs-lookup"><span data-stu-id="9a597-138">Moreover, scalable EM is three times faster than non-scalable EM, even if all the data can fit in main memory.</span></span> <span data-ttu-id="9a597-139">在大多数情况下，性能改进不会导致完成的模型的质量下降。</span><span class="sxs-lookup"><span data-stu-id="9a597-139">In the majority of cases, the performance improvement does not lead to lower quality of the complete model.</span></span>  
  
 <span data-ttu-id="9a597-140">有关介绍 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 聚类分析算法中的 EM 的实现的技术报告，请参阅 [Scaling EM (Expectation Maximization) Clustering to Large Databases](https://go.microsoft.com/fwlink/?LinkId=45964)（针对大数据库对 EM (Expectation Maximization) 聚类分析进行扩展）。</span><span class="sxs-lookup"><span data-stu-id="9a597-140">For a technical report that describes the implementation of EM in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Clustering algorithm, see [Scaling EM (Expectation Maximization) Clustering to Large Databases](https://go.microsoft.com/fwlink/?LinkId=45964).</span></span>  
  
### <a name="k-means-clustering"></a><span data-ttu-id="9a597-141">K 平均值聚类</span><span class="sxs-lookup"><span data-stu-id="9a597-141">K-Means Clustering</span></span>  
 <span data-ttu-id="9a597-142">k-means 聚类分析是一种广为人知的方法，它通过尽量缩小一个分类中的项之间的差异，同时尽量拉大分类之间的距离，来分配分类成员身份。</span><span class="sxs-lookup"><span data-stu-id="9a597-142">K-means clustering is a well-known method of assigning cluster membership by minimizing the differences among items in a cluster while maximizing the distance between clusters.</span></span> <span data-ttu-id="9a597-143">k-means 中的 "means" 指的是分类的“中点”，它是任意选定的一个数据点，之后反复优化，直到真正代表该分类中的所有数据点的平均值。\*\*</span><span class="sxs-lookup"><span data-stu-id="9a597-143">The "means" in k-means refers to the *centroid* of the cluster, which is a data point that is chosen arbitrarily and then refined iteratively until it represents the true mean of all data points in the cluster.</span></span> <span data-ttu-id="9a597-144">"k" 指的是用于为聚类分析过程设种子的任意数目的点。</span><span class="sxs-lookup"><span data-stu-id="9a597-144">The "k" refers to an arbitrary number of points that are used to seed the clustering process.</span></span> <span data-ttu-id="9a597-145">k-means 算法计算一个分类中的数据记录之间的欧几里得距离的平方，以及表示分类平均值的矢量，并在和达到最小值时在最后一组 k 分类上收敛。</span><span class="sxs-lookup"><span data-stu-id="9a597-145">The k-means algorithm calculates the squared Euclidean distances between data records in a cluster and the vector that represents the cluster mean, and converges on a final set of k clusters when that sum reaches its minimum value.</span></span>  
  
 <span data-ttu-id="9a597-146">k-means 算法仅仅将每个数据点分配给一个分类，并且不允许成员身份存在不确定性。</span><span class="sxs-lookup"><span data-stu-id="9a597-146">The k-means algorithm assigns each data point to exactly one cluster, and does not allow for uncertainty in membership.</span></span> <span data-ttu-id="9a597-147">分类中的成员身份表示为与中点的距离。</span><span class="sxs-lookup"><span data-stu-id="9a597-147">Membership in a cluster is expressed as a distance from the centroid.</span></span>  
  
 <span data-ttu-id="9a597-148">通常，k-means 算法用于创建连续属性的分类，在这种情况下，计算与平均值的距离非常简单。</span><span class="sxs-lookup"><span data-stu-id="9a597-148">Typically, the k-means algorithm is used for creating clusters of continuous attributes, where calculating distance to a mean is straightforward.</span></span> <span data-ttu-id="9a597-149">但是， [!INCLUDE[msCoName](../../includes/msconame-md.md)] 实现通过使用概率针对分类离散属性对 k-means 方法进行改编。</span><span class="sxs-lookup"><span data-stu-id="9a597-149">However, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] implementation adapts the k-means method to cluster discrete attributes, by using probabilities.</span></span>  <span data-ttu-id="9a597-150">对于离散属性，数据点与特定分类的距离按如下公式计算：</span><span class="sxs-lookup"><span data-stu-id="9a597-150">For discrete attributes, the distance of a data point from a particular cluster is calculated as follows:</span></span>  
  
 <span data-ttu-id="9a597-151">1 - P(数据点, 分类)</span><span class="sxs-lookup"><span data-stu-id="9a597-151">1 - P(data point, cluster)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9a597-152">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 聚类分析算法不公开用于计算 k-means 的距离函数，并且在完成的模型中不能测量距离。</span><span class="sxs-lookup"><span data-stu-id="9a597-152">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Clustering algorithm does not expose the distance function used in computing k-means, and measures of distance are not available in the completed model.</span></span> <span data-ttu-id="9a597-153">但是，可以使用预测函数返回与距离对应的值，在这种情况下，距离计算为某个数据点属于此分类的概率。</span><span class="sxs-lookup"><span data-stu-id="9a597-153">However, you can use a prediction function to return a value that corresponds to distance, where distance is computed as the probability of a data point belonging to the cluster.</span></span> <span data-ttu-id="9a597-154">有关详细信息，请参阅 [ClusterProbability (DMX)](/sql/dmx/clusterprobability-dmx)。</span><span class="sxs-lookup"><span data-stu-id="9a597-154">For more information, see [ClusterProbability &#40;DMX&#41;](/sql/dmx/clusterprobability-dmx).</span></span>  
  
 <span data-ttu-id="9a597-155">k-means 算法提供两种对数据集进行抽样的方法：不可缩放的 K-means 和可缩放的 k-means，前者加载整个数据集并创建一个聚类分析阶段，后者使用前 50,000 个事例，并仅仅在需要更多数据才能使模型很好地适合数据时读取更多事例。</span><span class="sxs-lookup"><span data-stu-id="9a597-155">The k-means algorithm provides two methods of sampling the data set: non-scalable K-means, which loads the entire data set and makes one clustering pass, or scalable k-means, where the algorithm uses the first 50,000 cases and reads more cases only if it needs more data to achieve a good fit of model to data.</span></span>  
  
### <a name="updates-to-the-microsoft-clustering-algorithm-in-sql-server-2008"></a><span data-ttu-id="9a597-156">在 SQL Server 2008 中对 Microsoft 聚类分析算法的更新</span><span class="sxs-lookup"><span data-stu-id="9a597-156">Updates to the Microsoft Clustering Algorithm in SQL Server 2008</span></span>  
 <span data-ttu-id="9a597-157">在 SQL Server 2008 中， [!INCLUDE[msCoName](../../includes/msconame-md.md)] 聚类分析算法的默认配置已更改为使用内部参数 NORMALIZATION = 1。</span><span class="sxs-lookup"><span data-stu-id="9a597-157">In SQL Server 2008, the default configuration of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] clustering algorithm was changed to use the internal parameter, NORMALIZATION = 1.</span></span> <span data-ttu-id="9a597-158">使用 z-score 统计信息执行规范化，并且假定正态分布。</span><span class="sxs-lookup"><span data-stu-id="9a597-158">Normalization is performed using z-score statistics, and assumes normal distribution.</span></span> <span data-ttu-id="9a597-159">默认行为中的这一更改旨在尽量减小可能具有很大量度和许多离群值的属性的影响。</span><span class="sxs-lookup"><span data-stu-id="9a597-159">The intent of this change in the default behavior is to minimize the effect of attributes that might have large magnitudes and many outliers.</span></span> <span data-ttu-id="9a597-160">但是，z-score 规范化可能会更改针对并非正态的分布（例如均匀分布）的聚类分析结果。</span><span class="sxs-lookup"><span data-stu-id="9a597-160">However, z-score normalization may alter the clustering results on distributions that are not normal (such as uniform distributions).</span></span> <span data-ttu-id="9a597-161">为了避免规范化和获取与 SQL Server 2005 中的 K-means 聚类分析算法相同的行为，可以使用“参数设置”对话框添加自定义参数 NORMALIZATION 并将其值设置为 0。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="9a597-161">To prevent normalization and obtain the same behavior as the K-means clustering algorithm in SQL Server 2005, you can use the **Parameter Settings** dialog box to add the custom parameter, NORMALIZATION, and set its value to 0.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9a597-162">NORMALIZATION 参数是 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 聚类分析算法的内部属性并且不受支持。</span><span class="sxs-lookup"><span data-stu-id="9a597-162">The NORMALIZATION parameter is an internal property of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Clustering algorithm and is not supported.</span></span> <span data-ttu-id="9a597-163">通常，建议在聚类分析模型中使用规范化以便改进模型结果。</span><span class="sxs-lookup"><span data-stu-id="9a597-163">In general, the use of normalization is recommended in clustering models to improve model results.</span></span>  
  
## <a name="customizing-the-microsoft-clustering-algorithm"></a><span data-ttu-id="9a597-164">自定义 Microsoft 聚类分析算法</span><span class="sxs-lookup"><span data-stu-id="9a597-164">Customizing the Microsoft Clustering Algorithm</span></span>  
 <span data-ttu-id="9a597-165">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 聚类分析算法支持几个参数，这些参数会影响所生成的挖掘模型的行为、性能和准确性。</span><span class="sxs-lookup"><span data-stu-id="9a597-165">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Clustering algorithm supports several parameters that affect the behavior, performance, and accuracy of the resulting mining model.</span></span>  
  
### <a name="setting-algorithm-parameters"></a><span data-ttu-id="9a597-166">设置算法参数</span><span class="sxs-lookup"><span data-stu-id="9a597-166">Setting Algorithm Parameters</span></span>  
 <span data-ttu-id="9a597-167">下表介绍可与 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 聚类分析算法一起使用的参数。</span><span class="sxs-lookup"><span data-stu-id="9a597-167">The following table describes the parameters that can be used with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Clustering algorithm.</span></span> <span data-ttu-id="9a597-168">这些参数影响生成的挖掘模型的性能和准确性。</span><span class="sxs-lookup"><span data-stu-id="9a597-168">These parameters affect both the performance and accuracy of the resulting mining model.</span></span>  
  
 <span data-ttu-id="9a597-169">CLUSTERING_METHOD</span><span class="sxs-lookup"><span data-stu-id="9a597-169">CLUSTERING_METHOD</span></span>  
 <span data-ttu-id="9a597-170">指定算法要使用的聚类分析方法。</span><span class="sxs-lookup"><span data-stu-id="9a597-170">Specifies the clustering method for the algorithm to use.</span></span> <span data-ttu-id="9a597-171">有下列聚类分析方法可用：</span><span class="sxs-lookup"><span data-stu-id="9a597-171">The following clustering methods are available:</span></span>  
  
|<span data-ttu-id="9a597-172">ID</span><span class="sxs-lookup"><span data-stu-id="9a597-172">ID</span></span>|<span data-ttu-id="9a597-173">方法</span><span class="sxs-lookup"><span data-stu-id="9a597-173">Method</span></span>|  
|--------|------------|  
|<span data-ttu-id="9a597-174">1</span><span class="sxs-lookup"><span data-stu-id="9a597-174">1</span></span>|<span data-ttu-id="9a597-175">可缩放 EM</span><span class="sxs-lookup"><span data-stu-id="9a597-175">Scalable EM</span></span>|  
|<span data-ttu-id="9a597-176">2</span><span class="sxs-lookup"><span data-stu-id="9a597-176">2</span></span>|<span data-ttu-id="9a597-177">不可缩放 EM</span><span class="sxs-lookup"><span data-stu-id="9a597-177">Non-scalable EM</span></span>|  
|<span data-ttu-id="9a597-178">3</span><span class="sxs-lookup"><span data-stu-id="9a597-178">3</span></span>|<span data-ttu-id="9a597-179">可缩放 k-means</span><span class="sxs-lookup"><span data-stu-id="9a597-179">Scalable K-Means</span></span>|  
|<span data-ttu-id="9a597-180">4</span><span class="sxs-lookup"><span data-stu-id="9a597-180">4</span></span>|<span data-ttu-id="9a597-181">不可缩放 k-means。</span><span class="sxs-lookup"><span data-stu-id="9a597-181">Non-scalable K-Means.</span></span>|  
  
 <span data-ttu-id="9a597-182">默认值为 1（可缩放 EM）。</span><span class="sxs-lookup"><span data-stu-id="9a597-182">The default is 1 (scalable EM).</span></span>  
  
 <span data-ttu-id="9a597-183">CLUSTER_COUNT</span><span class="sxs-lookup"><span data-stu-id="9a597-183">CLUSTER_COUNT</span></span>  
 <span data-ttu-id="9a597-184">指定将由算法生成的大致分类数。</span><span class="sxs-lookup"><span data-stu-id="9a597-184">Specifies the approximate number of clusters to be built by the algorithm.</span></span> <span data-ttu-id="9a597-185">如果无法基于相应的数据生成该大致数目的分类，则算法将生成尽可能多的分类。</span><span class="sxs-lookup"><span data-stu-id="9a597-185">If the approximate number of clusters cannot be built from the data, the algorithm builds as many clusters as possible.</span></span> <span data-ttu-id="9a597-186">如果将 CLUSTER_COUNT 设置为 0，则算法将使用试探性方法最准确地确定要生成的分类数。</span><span class="sxs-lookup"><span data-stu-id="9a597-186">Setting the CLUSTER_COUNT to 0 causes the algorithm to use heuristics to best determine the number of clusters to build.</span></span>  
  
 <span data-ttu-id="9a597-187">默认值为 10。</span><span class="sxs-lookup"><span data-stu-id="9a597-187">The default is 10.</span></span>  
  
 <span data-ttu-id="9a597-188">CLUSTER_SEED</span><span class="sxs-lookup"><span data-stu-id="9a597-188">CLUSTER_SEED</span></span>  
 <span data-ttu-id="9a597-189">指定在为建模初始阶段随机生成分类时所要使用的种子数量。</span><span class="sxs-lookup"><span data-stu-id="9a597-189">Specifies the seed number that is used to randomly generate clusters for the initial stage of model building.</span></span>  
  
 <span data-ttu-id="9a597-190">通过更改此数字，可以更改生成初始分类的方法，然后使用不同的种子比较已生成的模型。</span><span class="sxs-lookup"><span data-stu-id="9a597-190">By changing this number, you can change the way that the initial clusters are built, and then compare models that have been built using different seeds.</span></span> <span data-ttu-id="9a597-191">如果种子已更改，但所发现的分类并没有太大的更改，则模型可被视为相对稳定。</span><span class="sxs-lookup"><span data-stu-id="9a597-191">If the seed is changed but the clusters that are found do not change greatly , the model can be considered relatively stable.</span></span>  
  
 <span data-ttu-id="9a597-192">默认值为 0。</span><span class="sxs-lookup"><span data-stu-id="9a597-192">The default is 0.</span></span>  
  
 <span data-ttu-id="9a597-193">MINIMUM_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="9a597-193">MINIMUM_SUPPORT</span></span>  
 <span data-ttu-id="9a597-194">指定生成某个分类至少需要的事例数。</span><span class="sxs-lookup"><span data-stu-id="9a597-194">Specifies the minimum number of cases that are required to build a cluster.</span></span> <span data-ttu-id="9a597-195">如果分类中的事例数小于此数目，则此分类将被视为空，并将被丢弃。</span><span class="sxs-lookup"><span data-stu-id="9a597-195">If the number of cases in the cluster is lower than this number, the cluster is treated as empty and discarded.</span></span>  
  
 <span data-ttu-id="9a597-196">如果将这个数目设置得过高，则可能遗漏有效分类。</span><span class="sxs-lookup"><span data-stu-id="9a597-196">If you set this number too high, you may miss valid clusters.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9a597-197">如果使用 EM，即默认聚类分析方法，则一些分类可能具有低于指定值的支持值。</span><span class="sxs-lookup"><span data-stu-id="9a597-197">If you use EM, which is the default clustering method, some clusters may have a support value that is lower than the specified value.</span></span> <span data-ttu-id="9a597-198">这是因为会计算每个事例在所有可能分类中的成员身份，对于某些分类，可能仅存在最小支持。</span><span class="sxs-lookup"><span data-stu-id="9a597-198">This is because each case is evaluated for its membership in all possible clusters, and for some clusters there may be only minimal support.</span></span>  
  
 <span data-ttu-id="9a597-199">默认值为 1。</span><span class="sxs-lookup"><span data-stu-id="9a597-199">The default is 1.</span></span>  
  
 <span data-ttu-id="9a597-200">MODELLING_CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="9a597-200">MODELLING_CARDINALITY</span></span>  
 <span data-ttu-id="9a597-201">指定在聚类分析过程中构建的示例模型数。</span><span class="sxs-lookup"><span data-stu-id="9a597-201">Specifies the number of sample models that are constructed during the clustering process.</span></span>  
  
 <span data-ttu-id="9a597-202">减少候选模型数会提高性能，但存在遗漏一些好的候选模型的风险。</span><span class="sxs-lookup"><span data-stu-id="9a597-202">Reducing the number of candidate models can improve performance at the risk of missing some good candidate models.</span></span>  
  
 <span data-ttu-id="9a597-203">默认值为 10。</span><span class="sxs-lookup"><span data-stu-id="9a597-203">The default is 10.</span></span>  
  
 <span data-ttu-id="9a597-204">STOPPING_TOLERANCE</span><span class="sxs-lookup"><span data-stu-id="9a597-204">STOPPING_TOLERANCE</span></span>  
 <span data-ttu-id="9a597-205">指定一个值，它可确定何时达到收敛而且算法完成建模。</span><span class="sxs-lookup"><span data-stu-id="9a597-205">Specifies the value that is used to determine when convergence is reached and the algorithm is finished building the model.</span></span> <span data-ttu-id="9a597-206">当分类概率中的整体变化小于 STOPPING_TOLERANCE 参数与模型大小之比时，即达到收敛。</span><span class="sxs-lookup"><span data-stu-id="9a597-206">Convergence is reached when the overall change in cluster probabilities is less than the ratio of the STOPPING_TOLERANCE parameter divided by the size of the model.</span></span>  
  
 <span data-ttu-id="9a597-207">默认值为 10。</span><span class="sxs-lookup"><span data-stu-id="9a597-207">The default is 10.</span></span>  
  
 <span data-ttu-id="9a597-208">SAMPLE_SIZE</span><span class="sxs-lookup"><span data-stu-id="9a597-208">SAMPLE_SIZE</span></span>  
 <span data-ttu-id="9a597-209">如果 CLUSTERING_METHOD 参数设置为其中一个可缩放聚类分析方法，请指定算法在每个传递中使用的事例数。</span><span class="sxs-lookup"><span data-stu-id="9a597-209">Specifies the number of cases that the algorithm uses on each pass if the CLUSTERING_METHOD parameter is set to one of the scalable clustering methods.</span></span> <span data-ttu-id="9a597-210">如果将 SAMPLE_SIZE 参数设置为 0，则会在单个传递中对整个数据集进行聚类分析操作，</span><span class="sxs-lookup"><span data-stu-id="9a597-210">Setting the SAMPLE_SIZE parameter to 0 will cause the whole dataset to be clustered in a single pass.</span></span> <span data-ttu-id="9a597-211">在单个传递中加载整个数据集会导致内存和性能问题。</span><span class="sxs-lookup"><span data-stu-id="9a597-211">Loading the entire dataset in a single pass can cause memory and performance issues.</span></span>  
  
 <span data-ttu-id="9a597-212">默认值为 50000。</span><span class="sxs-lookup"><span data-stu-id="9a597-212">The default is 50000.</span></span>  
  
 <span data-ttu-id="9a597-213">MAXIMUM_INPUT_ATTRIBUTES</span><span class="sxs-lookup"><span data-stu-id="9a597-213">MAXIMUM_INPUT_ATTRIBUTES</span></span>  
 <span data-ttu-id="9a597-214">指定算法在调用功能选择之前可以处理的最大输入属性数。</span><span class="sxs-lookup"><span data-stu-id="9a597-214">Specifies the maximum number of input attributes that the algorithm can handle before it invokes feature selection.</span></span> <span data-ttu-id="9a597-215">将该值设置为 0 表示不限制属性的最大数目。</span><span class="sxs-lookup"><span data-stu-id="9a597-215">Setting this value to 0 specifies that there is no maximum number of attributes.</span></span>  
  
 <span data-ttu-id="9a597-216">增大属性的数目会大大降低性能。</span><span class="sxs-lookup"><span data-stu-id="9a597-216">Increasing the number of attributes can significantly degrade performance.</span></span>  
  
 <span data-ttu-id="9a597-217">默认值为 255。</span><span class="sxs-lookup"><span data-stu-id="9a597-217">The default is 255.</span></span>  
  
 <span data-ttu-id="9a597-218">MAXIMUM_STATES</span><span class="sxs-lookup"><span data-stu-id="9a597-218">MAXIMUM_STATES</span></span>  
 <span data-ttu-id="9a597-219">指定算法支持的最大属性状态数。</span><span class="sxs-lookup"><span data-stu-id="9a597-219">Specifies the maximum number of attribute states that the algorithm supports.</span></span> <span data-ttu-id="9a597-220">如果属性的状态数超过此最大值，则算法将使用最常见状态，而忽略其余状态。</span><span class="sxs-lookup"><span data-stu-id="9a597-220">If an attribute has more states than the maximum, the algorithm uses the most popular states and ignores the remaining states.</span></span>  
  
 <span data-ttu-id="9a597-221">增大状态的数目会大大降低性能。</span><span class="sxs-lookup"><span data-stu-id="9a597-221">Increasing the number of states can significantly degrade performance.</span></span>  
  
 <span data-ttu-id="9a597-222">默认值为 100。</span><span class="sxs-lookup"><span data-stu-id="9a597-222">The default is 100.</span></span>  
  
### <a name="modeling-flags"></a><span data-ttu-id="9a597-223">建模标志</span><span class="sxs-lookup"><span data-stu-id="9a597-223">Modeling Flags</span></span>  
 <span data-ttu-id="9a597-224">此算法支持下列建模标志。</span><span class="sxs-lookup"><span data-stu-id="9a597-224">The algorithm supports the following modeling flags.</span></span> <span data-ttu-id="9a597-225">在创建挖掘结构或挖掘模型时会定义建模标志。</span><span class="sxs-lookup"><span data-stu-id="9a597-225">You define modeling flags when you create the mining structure or mining model.</span></span> <span data-ttu-id="9a597-226">建模标志指定在分析过程中如何处理每一列中的值。</span><span class="sxs-lookup"><span data-stu-id="9a597-226">The modeling flags specify how values in each column are handled during analysis.</span></span>  
  
|<span data-ttu-id="9a597-227">建模标志</span><span class="sxs-lookup"><span data-stu-id="9a597-227">Modeling Flag</span></span>|<span data-ttu-id="9a597-228">说明</span><span class="sxs-lookup"><span data-stu-id="9a597-228">Description</span></span>|  
|-------------------|-----------------|  
|<span data-ttu-id="9a597-229">MODEL_EXISTENCE_ONLY</span><span class="sxs-lookup"><span data-stu-id="9a597-229">MODEL_EXISTENCE_ONLY</span></span>|<span data-ttu-id="9a597-230">该列将被视为具有两个可能状态：“缺失”和“现有”。</span><span class="sxs-lookup"><span data-stu-id="9a597-230">The column will be treated as having two possible states: Missing and Existing.</span></span> <span data-ttu-id="9a597-231">Null 表示缺失值。</span><span class="sxs-lookup"><span data-stu-id="9a597-231">A null is a missing value.</span></span><br /><br /> <span data-ttu-id="9a597-232">适用于挖掘模型列。</span><span class="sxs-lookup"><span data-stu-id="9a597-232">Applies to mining model column.</span></span>|  
|<span data-ttu-id="9a597-233">NOT NULL</span><span class="sxs-lookup"><span data-stu-id="9a597-233">NOT NULL</span></span>|<span data-ttu-id="9a597-234">此列中不能包含 Null 值。</span><span class="sxs-lookup"><span data-stu-id="9a597-234">The column cannot contain a null.</span></span> <span data-ttu-id="9a597-235">如果 Analysis Services 在模型定型过程中遇到 Null 值，将会导致错误。</span><span class="sxs-lookup"><span data-stu-id="9a597-235">An error will result if Analysis Services encounters a null during model training.</span></span><br /><br /> <span data-ttu-id="9a597-236">适用于挖掘结构列。</span><span class="sxs-lookup"><span data-stu-id="9a597-236">Applies to mining structure column.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9a597-237">要求</span><span class="sxs-lookup"><span data-stu-id="9a597-237">Requirements</span></span>  
 <span data-ttu-id="9a597-238">聚类分析模型必须包含一个键列和若干输入列。</span><span class="sxs-lookup"><span data-stu-id="9a597-238">A clustering model must contain a key column and input columns.</span></span> <span data-ttu-id="9a597-239">还可以将输入列定义为可预测列。</span><span class="sxs-lookup"><span data-stu-id="9a597-239">You can also define input columns as being predictable.</span></span> <span data-ttu-id="9a597-240">设置为 `Predict Only` 的列不用来生成分类。</span><span class="sxs-lookup"><span data-stu-id="9a597-240">Columns set to `Predict Only` are not used to build clusters.</span></span> <span data-ttu-id="9a597-241">在生成分类后，将计算这些值在分类中的分布。</span><span class="sxs-lookup"><span data-stu-id="9a597-241">The distribution of these values in the clusters are calculated after the clusters are built.</span></span>  
  
### <a name="input-and-predictable-columns"></a><span data-ttu-id="9a597-242">输入列和可预测列</span><span class="sxs-lookup"><span data-stu-id="9a597-242">Input and Predictable Columns</span></span>  
 <span data-ttu-id="9a597-243">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 聚类分析算法支持下表中列出的特定输入列和可预测列。</span><span class="sxs-lookup"><span data-stu-id="9a597-243">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Clustering algorithm supports the specific input columns and predictable columns that are listed in the following table.</span></span> <span data-ttu-id="9a597-244">有关内容类型在用于挖掘模型中时的含义的详细信息，请参阅[内容类型（数据挖掘）](content-types-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="9a597-244">For more information about what the content types mean when used in a mining model, see [Content Types &#40;Data Mining&#41;](content-types-data-mining.md).</span></span>  
  
|<span data-ttu-id="9a597-245">列</span><span class="sxs-lookup"><span data-stu-id="9a597-245">Column</span></span>|<span data-ttu-id="9a597-246">内容类型</span><span class="sxs-lookup"><span data-stu-id="9a597-246">Content types</span></span>|  
|------------|-------------------|  
|<span data-ttu-id="9a597-247">输入属性</span><span class="sxs-lookup"><span data-stu-id="9a597-247">Input attribute</span></span>|<span data-ttu-id="9a597-248">连续、循环、离散、离散化、键、表和已排序</span><span class="sxs-lookup"><span data-stu-id="9a597-248">Continuous, Cyclical, Discrete, Discretized, Key, Table, Ordered</span></span>|  
|<span data-ttu-id="9a597-249">可预测属性</span><span class="sxs-lookup"><span data-stu-id="9a597-249">Predictable attribute</span></span>|<span data-ttu-id="9a597-250">连续、循环、离散、离散化、表和已排序</span><span class="sxs-lookup"><span data-stu-id="9a597-250">Continuous, Cyclical, Discrete, Discretized, Table, Ordered</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="9a597-251">支持 Cyclical 和 Ordered 内容类型，但算法会将它们视为离散值，不会进行特殊处理。</span><span class="sxs-lookup"><span data-stu-id="9a597-251">Cyclical and Ordered content types are supported, but the algorithm treats them as discrete values and does not perform special processing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a597-252">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9a597-252">See Also</span></span>  
 <span data-ttu-id="9a597-253">[Microsoft 聚类分析算法](microsoft-clustering-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="9a597-253">[Microsoft Clustering Algorithm](microsoft-clustering-algorithm.md) </span></span>  
 <span data-ttu-id="9a597-254">[聚类分析模型查询示例](clustering-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="9a597-254">[Clustering Model Query Examples](clustering-model-query-examples.md) </span></span>  
 [<span data-ttu-id="9a597-255">聚类分析模型的挖掘模型内容（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="9a597-255">Mining Model Content for Clustering Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-clustering-models-analysis-services-data-mining.md)  
  
  
