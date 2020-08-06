---
title: Microsoft 顺序分析和聚类分析算法技术参考 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- MAXIMUM_SEQUENCE_STATES parameter
- MINIMUM_SUPPORT parameter
- MAXIMUM_STATES parameter
- sequence clustering algorithms [Analysis Services]
- CLUSTER_COUNT parameter
ms.assetid: 251c369d-6b02-4687-964e-39bf55c9b009
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3e09018fad9c291ec1f47bbb776797d634950381
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577091"
---
# <a name="microsoft-sequence-clustering-algorithm-technical-reference"></a><span data-ttu-id="af164-102">Microsoft 顺序分析和聚类分析算法技术参考</span><span class="sxs-lookup"><span data-stu-id="af164-102">Microsoft Sequence Clustering Algorithm Technical Reference</span></span>
  <span data-ttu-id="af164-103">Microsoft 顺序分析和聚类分析算法是一种综合算法，它使用 Markov 链分析来识别有序序列，并会综合利用此分析结果和聚类分析技术基于模型中的序列和其他属性生成分类。</span><span class="sxs-lookup"><span data-stu-id="af164-103">The Microsoft Sequence Clustering algorithm is a hybrid algorithm that uses Markov chain analysis to identify ordered sequences, and combines the results of this analysis with clustering techniques to generate clusters based on the sequences and other attributes in the model.</span></span> <span data-ttu-id="af164-104">本主题介绍该算法的实现以及如何自定义算法，最后还对顺序分析和聚类分析模型的特殊要求进行了说明。</span><span class="sxs-lookup"><span data-stu-id="af164-104">This topic describes the implementation of the algorithm, how to customize the algorithm, and special requirements for sequence clustering models.</span></span>  
  
 <span data-ttu-id="af164-105">有关该算法的详细常规信息，包括如何浏览和查询顺序分析和聚类分析模型，请参阅 [Microsoft Sequence Clustering Algorithm](microsoft-sequence-clustering-algorithm.md)。</span><span class="sxs-lookup"><span data-stu-id="af164-105">For more general information about the algorithm, including how to browse and query sequence clustering models, see [Microsoft Sequence Clustering Algorithm](microsoft-sequence-clustering-algorithm.md).</span></span>  
  
## <a name="implementation-of-the-microsoft-sequence-clustering-algorithm"></a><span data-ttu-id="af164-106">Microsoft 顺序分析和聚类分析算法的实现</span><span class="sxs-lookup"><span data-stu-id="af164-106">Implementation of the Microsoft Sequence Clustering Algorithm</span></span>  
 <span data-ttu-id="af164-107">Microsoft 顺序分析和聚类分析模型使用 Markov 模型来识别序列并确定序列的概率。</span><span class="sxs-lookup"><span data-stu-id="af164-107">The Microsoft Sequence Clustering model uses Markov models to identify sequences and determine the probability of sequences.</span></span> <span data-ttu-id="af164-108">Markov 模型是存储不同状态之间的转换的定向图形。</span><span class="sxs-lookup"><span data-stu-id="af164-108">A Markov model is a directed graph that stores the transitions between different states.</span></span> <span data-ttu-id="af164-109">Microsoft 顺序分析和聚类分析算法使用 N 阶 Markov 链，而不使用隐 Markov 模型。</span><span class="sxs-lookup"><span data-stu-id="af164-109">The Microsoft Sequence Clustering algorithm uses n-order Markov chains, not a Hidden Markov model.</span></span>  
  
 <span data-ttu-id="af164-110">您可由 Markov 链中的阶数知道有多少个状态用于确定当前状态的概率。</span><span class="sxs-lookup"><span data-stu-id="af164-110">The number of orders in a Markov chain tells you how many states are used to determine the probability of the current states.</span></span> <span data-ttu-id="af164-111">在一阶 Markov 模型中，当前状态的概率仅取决于前一个状态。</span><span class="sxs-lookup"><span data-stu-id="af164-111">In a first-order Markov model, the probability of the current state depends only on the previous state.</span></span> <span data-ttu-id="af164-112">在二阶 Markov 链中，当前状态的概率取决于前两个状态。其他情况下的概率可依此类推。</span><span class="sxs-lookup"><span data-stu-id="af164-112">In a second-order Markov chain, the probability of a state depends on the previous two states, and so forth.</span></span> <span data-ttu-id="af164-113">对于每个 Markov 链，转换矩阵都会存储每种状态组合的转换。</span><span class="sxs-lookup"><span data-stu-id="af164-113">For each Markov chain, a transition matrix stores the transitions for each combination of states.</span></span> <span data-ttu-id="af164-114">当 Markov 链的长度增加时，转换矩阵的规模也会呈指数增长，但同时会变得非常稀疏。</span><span class="sxs-lookup"><span data-stu-id="af164-114">As the length of the Markov chain increases, the size of the matrix also increases exponentially, and the matrix becomes extremely sparse.</span></span> <span data-ttu-id="af164-115">处理时间也会按比例增加。</span><span class="sxs-lookup"><span data-stu-id="af164-115">Processing time also increases proportionally.</span></span>  
  
 <span data-ttu-id="af164-116">点击流分析法是一种分析网站网页的访问情况的方法，它可帮助进行链的可视化处理。</span><span class="sxs-lookup"><span data-stu-id="af164-116">It might be helpful to visualize the chain by using the example of clickstream analysis, which analyzes visits to Web pages on a site.</span></span> <span data-ttu-id="af164-117">对于每个会话，用户都会创建一个很长的点击序列。</span><span class="sxs-lookup"><span data-stu-id="af164-117">Each user creates a long sequence of clicks for each session.</span></span> <span data-ttu-id="af164-118">通过创建模型来分析用户在网站中的行为时，用于定型的数据集就是一个 URL 序列；该序列可转换为一个图形，其中包含相同点击路径的所有实例的计数。</span><span class="sxs-lookup"><span data-stu-id="af164-118">When you create a model to analyze user behavior on a Web site, the data set used for training is a sequence of URLs, converted to a graph that includes the count of all instances of the same click path.</span></span> <span data-ttu-id="af164-119">例如，该图形可包含用户从第 1 页转到第 2 页的概率 (10%) 以及用户从第 1 页转到第 3 页的概率 (20%)，其余依此类推。</span><span class="sxs-lookup"><span data-stu-id="af164-119">For example, the graph contains the probability that the user moves from page 1 to page 2 (10%), the probability that the user moves from page 1 to page 3 (20%), and so forth.</span></span> <span data-ttu-id="af164-120">当将所有可能的路径以及路径片段整合到一起时，就可获得一张图，它比所观察到的任何单个路径都长，而且更复杂。</span><span class="sxs-lookup"><span data-stu-id="af164-120">When you put all the possible paths and pieces of the paths together, you obtain a graph that might be much longer and more complex than any single observed path.</span></span>  
  
 <span data-ttu-id="af164-121">默认情况下，Microsoft 顺序分析和聚类分析算法使用聚类分析的 Expectation Maximization (EM) 方法。</span><span class="sxs-lookup"><span data-stu-id="af164-121">By default, the Microsoft Sequence Clustering algorithm uses the Expectation Maximization (EM) method of clustering.</span></span> <span data-ttu-id="af164-122">有关详细信息，请参阅 [Microsoft 聚类分析算法技术参考](microsoft-clustering-algorithm-technical-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="af164-122">For more information, see [Microsoft Clustering Algorithm Technical Reference](microsoft-clustering-algorithm-technical-reference.md).</span></span>  
  
 <span data-ttu-id="af164-123">聚类分析的目标是序列属性和非序列属性。</span><span class="sxs-lookup"><span data-stu-id="af164-123">The targets of clustering are both the sequential and nonsequential attributes.</span></span> <span data-ttu-id="af164-124">每个分类都是利用概率分布随机选择的。</span><span class="sxs-lookup"><span data-stu-id="af164-124">Each cluster is randomly selected using a probability distribution.</span></span> <span data-ttu-id="af164-125">每个分类都具有表示完整路径集的 Markov 链以及包含序列状态转换和概率的矩阵。</span><span class="sxs-lookup"><span data-stu-id="af164-125">Each cluster has a Markov chain that represents the complete set of paths, and a matrix that contains the sequence state transitions and probabilities.</span></span> <span data-ttu-id="af164-126">算法会基于初始分布，使用 Bayes 定理来计算所有属性（包括序列）属于特定分类的概率。</span><span class="sxs-lookup"><span data-stu-id="af164-126">Based on the initial distribution, Bayes rule is used to calculate the probability of any attribute, including a sequence, in a specific cluster.</span></span>  
  
 <span data-ttu-id="af164-127">Microsoft 顺序分析和聚类分析算法支持在模型中使用其他非序列属性。</span><span class="sxs-lookup"><span data-stu-id="af164-127">The Microsoft Sequence Clustering algorithm supports the additional of nonsequential attributes to the model.</span></span> <span data-ttu-id="af164-128">这意味着将会将这些非序列属性与序列属性组合起来，创建具有相似属性的事例分类，就像典型的聚类分析模型中一样。</span><span class="sxs-lookup"><span data-stu-id="af164-128">This means that these additional attributes are combined with the sequence attributes to create clusters of cases with similar attributes, just like in a typical clustering model.</span></span>  
  
 <span data-ttu-id="af164-129">与典型的聚类分析模型相比，顺序分析和聚类分析模型通常会创建更多的分类。</span><span class="sxs-lookup"><span data-stu-id="af164-129">A sequence clustering model tends to create many more clusters than a typical clustering model.</span></span> <span data-ttu-id="af164-130">因此，Microsoft 顺序分析和聚类分析算法会执行“群集分解” \*\*，以基于序列属性和其他属性分离群集。</span><span class="sxs-lookup"><span data-stu-id="af164-130">Therefore, the Microsoft Sequence Clustering algorithm performs *cluster decomposition*to separate clusters based on sequences and other attributes.</span></span>  
  
### <a name="feature-selection-in-a-sequence-clustering-model"></a><span data-ttu-id="af164-131">顺序分析和聚类分析模型中的功能选择</span><span class="sxs-lookup"><span data-stu-id="af164-131">Feature Selection in a Sequence Clustering Model</span></span>  
 <span data-ttu-id="af164-132">生成序列时不会调用功能选择，但会在聚类分析阶段应用功能选择。</span><span class="sxs-lookup"><span data-stu-id="af164-132">Feature selection is not invoked when building sequences; however, feature selection applies at the clustering stage.</span></span>  
  
|<span data-ttu-id="af164-133">模型类型</span><span class="sxs-lookup"><span data-stu-id="af164-133">Model type</span></span>|<span data-ttu-id="af164-134">功能选择方法</span><span class="sxs-lookup"><span data-stu-id="af164-134">Feature Selection Method</span></span>|<span data-ttu-id="af164-135">注释</span><span class="sxs-lookup"><span data-stu-id="af164-135">Comments</span></span>|  
|----------------|------------------------------|--------------|  
|<span data-ttu-id="af164-136">顺序分析和聚类分析</span><span class="sxs-lookup"><span data-stu-id="af164-136">Sequence Clustering</span></span>|<span data-ttu-id="af164-137">未使用</span><span class="sxs-lookup"><span data-stu-id="af164-137">Not used</span></span>|<span data-ttu-id="af164-138">不调用功能选择；但可以通过设置参数 MINIMUM_SUPPORT 和 MINIMUM_PROBABILIITY 的值来控制算法的行为。</span><span class="sxs-lookup"><span data-stu-id="af164-138">Feature selection is not invoked; however, you can control the behavior of the algorithm by setting the value of the parameters MINIMUM_SUPPORT and MINIMUM_PROBABILIITY.</span></span>|  
|<span data-ttu-id="af164-139">群集</span><span class="sxs-lookup"><span data-stu-id="af164-139">Clustering</span></span>|<span data-ttu-id="af164-140">兴趣性分数</span><span class="sxs-lookup"><span data-stu-id="af164-140">Interestingness score</span></span>|<span data-ttu-id="af164-141">尽管聚类分析算法可能使用离散算法或离散化算法，但每个属性的分数仍将作为间距进行计算，并且是连续的，因此使用兴趣性分数。</span><span class="sxs-lookup"><span data-stu-id="af164-141">Although the clustering algorithm may use discrete or discretized algorithms, the score of each attribute is calculated as a distance and is continuous; therefore the interestingness score is used.</span></span>|  
  
 <span data-ttu-id="af164-142">有关详细信息，请参阅 [Feature Selection](../../sql-server/install/feature-selection.md)。</span><span class="sxs-lookup"><span data-stu-id="af164-142">For more information, see [Feature Selection](../../sql-server/install/feature-selection.md).</span></span>  
  
### <a name="optimizing-performance"></a><span data-ttu-id="af164-143">优化性能</span><span class="sxs-lookup"><span data-stu-id="af164-143">Optimizing Performance</span></span>  
 <span data-ttu-id="af164-144">Microsoft 顺序分析和聚类分析算法支持多种处理优化方法：</span><span class="sxs-lookup"><span data-stu-id="af164-144">The Microsoft Sequence Clustering algorithm supports various ways to optimize processing:</span></span>  
  
-   <span data-ttu-id="af164-145">通过设置 CLUSTER_COUNT 参数的值可以控制生成的分类数。</span><span class="sxs-lookup"><span data-stu-id="af164-145">Controlling the number of clusters generated, by setting a value for the CLUSTER_COUNT parameter.</span></span>  
  
-   <span data-ttu-id="af164-146">通过增大 MINIMUM_SUPPORT 参数的值可以减少包含为属性的序列的数量。</span><span class="sxs-lookup"><span data-stu-id="af164-146">Reducing the number of sequences included as attributes, by increasing the value of the MINIMUM_SUPPORT parameter.</span></span> <span data-ttu-id="af164-147">这会导致删除一些罕见的序列。</span><span class="sxs-lookup"><span data-stu-id="af164-147">As a result, rare sequences are eliminated.</span></span>  
  
-   <span data-ttu-id="af164-148">在处理模型之前，通过对相关属性进行分组可以降低复杂性。</span><span class="sxs-lookup"><span data-stu-id="af164-148">Reducing complexity before processing the model, by grouping related attributes.</span></span>  
  
 <span data-ttu-id="af164-149">通常，可以使用多种方法来优化 n 阶 Markov 链模式的性能：</span><span class="sxs-lookup"><span data-stu-id="af164-149">In general, you can optimize the performance of an n-order Markov chain mode in several ways:</span></span>  
  
-   <span data-ttu-id="af164-150">控制可能的序列的长度。</span><span class="sxs-lookup"><span data-stu-id="af164-150">Controlling the length of the possible sequences.</span></span>  
  
-   <span data-ttu-id="af164-151">以编程方式减小 n 值。</span><span class="sxs-lookup"><span data-stu-id="af164-151">Programmatically reducing the value of n.</span></span>  
  
-   <span data-ttu-id="af164-152">仅存储超出指定阈值的概率。</span><span class="sxs-lookup"><span data-stu-id="af164-152">Storing only probabilities that exceed a specified threshold.</span></span>  
  
 <span data-ttu-id="af164-153">有关这些方法的深入探讨不属于本主题的讨论范围。</span><span class="sxs-lookup"><span data-stu-id="af164-153">A complete discussion of these methods is beyond the scope of this topic.</span></span>  
  
## <a name="customizing-the-sequence-clustering-algorithm"></a><span data-ttu-id="af164-154">自定义顺序分析和聚类分析算法</span><span class="sxs-lookup"><span data-stu-id="af164-154">Customizing the Sequence Clustering Algorithm</span></span>  
 <span data-ttu-id="af164-155">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 顺序分析和聚类分析算法支持多个参数，这些参数可影响所生成的挖掘模型的行为、性能和准确性。</span><span class="sxs-lookup"><span data-stu-id="af164-155">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering algorithm supports parameters that affect the behavior, performance, and accuracy of the resulting mining model.</span></span> <span data-ttu-id="af164-156">您还可以通过设置用于控制算法的定型数据处理方式的建模标志来修改已完成模型的行为。</span><span class="sxs-lookup"><span data-stu-id="af164-156">You can also modify the behavior of the completed model by setting modeling flags that control the way the algorithm processes training data.</span></span>  
  
### <a name="setting-algorithm-parameters"></a><span data-ttu-id="af164-157">设置算法参数</span><span class="sxs-lookup"><span data-stu-id="af164-157">Setting Algorithm Parameters</span></span>  
 <span data-ttu-id="af164-158">下表介绍可用于 Microsoft 顺序分析和聚类分析算法的参数。</span><span class="sxs-lookup"><span data-stu-id="af164-158">The following table describes the parameters that can be used with the Microsoft Sequence Clustering algorithm.</span></span>  
  
 <span data-ttu-id="af164-159">CLUSTER_COUNT</span><span class="sxs-lookup"><span data-stu-id="af164-159">CLUSTER_COUNT</span></span>  
 <span data-ttu-id="af164-160">指定将由算法生成的大致分类数。</span><span class="sxs-lookup"><span data-stu-id="af164-160">Specifies the approximate number of clusters to be built by the algorithm.</span></span> <span data-ttu-id="af164-161">如果无法基于相应的数据生成该大致数目的分类，则算法将生成尽可能多的分类。</span><span class="sxs-lookup"><span data-stu-id="af164-161">If the approximate number of clusters cannot be built from the data, the algorithm builds as many clusters as possible.</span></span> <span data-ttu-id="af164-162">如果将 CLUSTER_COUNT 设置为 0，则算法将会使用试探性方法确定要生成的分类的最佳数量。</span><span class="sxs-lookup"><span data-stu-id="af164-162">Setting the CLUSTER_COUNT parameter to 0 causes the algorithm to use heuristics to best determine the number of clusters to build.</span></span>  
  
 <span data-ttu-id="af164-163">默认值为 10。</span><span class="sxs-lookup"><span data-stu-id="af164-163">The default is 10.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="af164-164">指定一个作为对算法的提示的非零数，算法将会查找该指定数，但最终的查找结果可能会大于或小于所指定的数。</span><span class="sxs-lookup"><span data-stu-id="af164-164">Specifying a non-zero number acts as a hint to the algorithm, which proceeds with the goal of finding the specified number, but may end up finding more or less.</span></span>  
  
 <span data-ttu-id="af164-165">MINIMUM_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="af164-165">MINIMUM_SUPPORT</span></span>  
 <span data-ttu-id="af164-166">指定支持属性创建分类所需的最小事例数。</span><span class="sxs-lookup"><span data-stu-id="af164-166">Specifies the minimum number of cases that is required in support of an attribute to create a cluster.</span></span>  
  
 <span data-ttu-id="af164-167">默认值为 10。</span><span class="sxs-lookup"><span data-stu-id="af164-167">The default is 10.</span></span>  
  
 <span data-ttu-id="af164-168">MAXIMUM_SEQUENCE_STATES</span><span class="sxs-lookup"><span data-stu-id="af164-168">MAXIMUM_SEQUENCE_STATES</span></span>  
 <span data-ttu-id="af164-169">指定一个顺序可以拥有的最大状态数。</span><span class="sxs-lookup"><span data-stu-id="af164-169">Specifies the maximum number of states that a sequence can have.</span></span>  
  
 <span data-ttu-id="af164-170">将该值设置为大于 100 的数将导致算法创建一个不提供有意义的信息的模型。</span><span class="sxs-lookup"><span data-stu-id="af164-170">Setting this value to a number greater than 100 may cause the algorithm to create a model that does not provide meaningful information.</span></span>  
  
 <span data-ttu-id="af164-171">默认值为 64。</span><span class="sxs-lookup"><span data-stu-id="af164-171">The default is 64.</span></span>  
  
 <span data-ttu-id="af164-172">MAXIMUM_STATES</span><span class="sxs-lookup"><span data-stu-id="af164-172">MAXIMUM_STATES</span></span>  
 <span data-ttu-id="af164-173">指定算法支持的非序列属性的最大状态数。</span><span class="sxs-lookup"><span data-stu-id="af164-173">Specifies the maximum number of states for a non-sequence attribute that the algorithm supports.</span></span> <span data-ttu-id="af164-174">如果非序列属性的状态数大于最大状态数，则算法将使用属性的最常用状态，并将剩余状态视为 `Missing` 。</span><span class="sxs-lookup"><span data-stu-id="af164-174">If the number of states for a non-sequence attribute is greater than the maximum number of states, the algorithm uses the attribute's most popular states and treats the remaining states as `Missing`.</span></span>  
  
 <span data-ttu-id="af164-175">默认值为 100。</span><span class="sxs-lookup"><span data-stu-id="af164-175">The default is 100.</span></span>  
  
### <a name="modeling-flags"></a><span data-ttu-id="af164-176">建模标志</span><span class="sxs-lookup"><span data-stu-id="af164-176">Modeling Flags</span></span>  
 <span data-ttu-id="af164-177">支持将以下建模标志与 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 顺序分析和聚类分析算法配合使用。</span><span class="sxs-lookup"><span data-stu-id="af164-177">The following modeling flags are supported for use with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering algorithm.</span></span>  
  
 <span data-ttu-id="af164-178">NOT NULL</span><span class="sxs-lookup"><span data-stu-id="af164-178">NOT NULL</span></span>  
 <span data-ttu-id="af164-179">指示该列不能包含 Null。</span><span class="sxs-lookup"><span data-stu-id="af164-179">Indicates that the column cannot contain a null.</span></span> <span data-ttu-id="af164-180">如果 Analysis Services 在模型定型过程中遇到 Null 值，将会导致错误。</span><span class="sxs-lookup"><span data-stu-id="af164-180">An error will result if Analysis Services encounters a null during model training.</span></span>  
  
 <span data-ttu-id="af164-181">适用于挖掘结构列。</span><span class="sxs-lookup"><span data-stu-id="af164-181">Applies to the mining structure column.</span></span>  
  
 <span data-ttu-id="af164-182">MODEL_EXISTENCE_ONLY</span><span class="sxs-lookup"><span data-stu-id="af164-182">MODEL_EXISTENCE_ONLY</span></span>  
 <span data-ttu-id="af164-183">表示列将被视为具有两个可能状态：`Missing` 和 `Existing`。</span><span class="sxs-lookup"><span data-stu-id="af164-183">Means that the column will be treated as having two possible states: `Missing` and `Existing`.</span></span> <span data-ttu-id="af164-184">Null 视为 `Missing` 值。</span><span class="sxs-lookup"><span data-stu-id="af164-184">A null is treated as a `Missing` value.</span></span>  
  
 <span data-ttu-id="af164-185">适用于挖掘模型列。</span><span class="sxs-lookup"><span data-stu-id="af164-185">Applies to the mining model column.</span></span>  
  
 <span data-ttu-id="af164-186">有关挖掘模型中 Missing 值的用法以及 Missing 值如何影响概率分数的详细信息，请参阅[缺失值（Analysis Services - 数据挖掘）](missing-values-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="af164-186">For more information about the use of Missing values in mining models, and how missing values affect probability scores, see [Missing Values &#40;Analysis Services - Data Mining&#41;](missing-values-analysis-services-data-mining.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af164-187">要求</span><span class="sxs-lookup"><span data-stu-id="af164-187">Requirements</span></span>  
 <span data-ttu-id="af164-188">事例表必须具有事例 ID 列。</span><span class="sxs-lookup"><span data-stu-id="af164-188">The case table must have a case ID column.</span></span> <span data-ttu-id="af164-189">此外，事例表还可以包含其他存储事例属性的列。</span><span class="sxs-lookup"><span data-stu-id="af164-189">Optionally the case table can contain other columns that store attributes about the case.</span></span>  
  
 <span data-ttu-id="af164-190">Microsoft 顺序分析和聚类分析算法要求序列信息以嵌套表的形式存储。</span><span class="sxs-lookup"><span data-stu-id="af164-190">The Microsoft Sequence Clustering algorithm requires sequence information, stored as a nested table.</span></span> <span data-ttu-id="af164-191">该嵌套表必须包含一个 Key Sequence 列。</span><span class="sxs-lookup"><span data-stu-id="af164-191">The nested table must have a single Key Sequence column.</span></span> <span data-ttu-id="af164-192">`Key Sequence` 列可包含可以存储的任何类型的数据（包括字符串数据类型），还必须包含每个事例的唯一值。</span><span class="sxs-lookup"><span data-stu-id="af164-192">A `Key Sequence` column can contain any type of data that can be sorted, including string data types, but the column must contain unique values for each case.</span></span> <span data-ttu-id="af164-193">而且，在处理模型之前，您必须确保事例表和嵌套表要按与其相关的键的升序存储。</span><span class="sxs-lookup"><span data-stu-id="af164-193">Moreover, before you process the model, you must ensure that both the case table and the nested table are sorted in ascending order on the key that relates the tables.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="af164-194">如果创建使用 Microsoft 顺序分析算法、但却不使用序列的模型，则生成的模型将不包含任何序列，而仅会基于模型中包含的其他属性对事例进行分类。</span><span class="sxs-lookup"><span data-stu-id="af164-194">If you create a model that uses the Microsoft Sequence algorithm but do not use a sequence column, the resulting model will not contain any sequences, but will simply cluster cases based on other attributes that are included in the model.</span></span>  
  
### <a name="input-and-predictable-columns"></a><span data-ttu-id="af164-195">输入列和可预测列</span><span class="sxs-lookup"><span data-stu-id="af164-195">Input and Predictable Columns</span></span>  
 <span data-ttu-id="af164-196">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 顺序分析和聚类分析算法支持下表中列出的特定输入列和可预测列。</span><span class="sxs-lookup"><span data-stu-id="af164-196">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering algorithm supports the specific input columns and predictable columns that are listed in the following table.</span></span> <span data-ttu-id="af164-197">有关内容类型在用于挖掘模型中时的含义的详细信息，请参阅[内容类型（数据挖掘）](content-types-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="af164-197">For more information about what the content types mean when used in a mining model, see [Content Types &#40;Data Mining&#41;](content-types-data-mining.md).</span></span>  
  
|<span data-ttu-id="af164-198">列</span><span class="sxs-lookup"><span data-stu-id="af164-198">Column</span></span>|<span data-ttu-id="af164-199">内容类型</span><span class="sxs-lookup"><span data-stu-id="af164-199">Content types</span></span>|  
|------------|-------------------|  
|<span data-ttu-id="af164-200">输入属性</span><span class="sxs-lookup"><span data-stu-id="af164-200">Input attribute</span></span>|<span data-ttu-id="af164-201">Continuous、Cyclical、Discrete、Discretized、Key、Key Sequence、Table 和 Ordered</span><span class="sxs-lookup"><span data-stu-id="af164-201">Continuous, Cyclical, Discrete, Discretized, Key, Key Sequence, Table, and Ordered</span></span>|  
|<span data-ttu-id="af164-202">可预测属性</span><span class="sxs-lookup"><span data-stu-id="af164-202">Predictable attribute</span></span>|<span data-ttu-id="af164-203">Continuous、Cyclical、Discrete、Discretized、Table 和 Ordered</span><span class="sxs-lookup"><span data-stu-id="af164-203">Continuous, Cyclical, Discrete, Discretized, Table, and Ordered</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af164-204">备注</span><span class="sxs-lookup"><span data-stu-id="af164-204">Remarks</span></span>  
  
-   <span data-ttu-id="af164-205">将 [PredictSequence (DMX)](/sql/dmx/predictsequence-dmx) 函数用于序列预测。</span><span class="sxs-lookup"><span data-stu-id="af164-205">Use the [PredictSequence &#40;DMX&#41;](/sql/dmx/predictsequence-dmx) function for Prediction of Sequences.</span></span> <span data-ttu-id="af164-206">有关支持序列预测的版本的详细信息 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，请参阅[SQL Server 2012 (各个版本支持的功能](https://go.microsoft.com/fwlink/?linkid=232473) https://go.microsoft.com/fwlink/?linkid=232473) 。</span><span class="sxs-lookup"><span data-stu-id="af164-206">For more information about the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that support Sequence Prediction, see [Features Supported by the Editions of SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473) (https://go.microsoft.com/fwlink/?linkid=232473).</span></span>  
  
-   <span data-ttu-id="af164-207">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 顺序分析和聚类分析算法不支持使用预测性模型标记语言 (PMML) 来创建挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="af164-207">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering algorithm does not support using the Predictive Model Markup Language (PMML) to create mining models.</span></span>  
  
-   <span data-ttu-id="af164-208">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 顺序分析和聚类分析算法支持钻取，支持使用 OLAP 挖掘模型和数据挖掘维度。</span><span class="sxs-lookup"><span data-stu-id="af164-208">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering algorithm supports drillthrough, the use of OLAP mining models, and the use of data mining dimensions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af164-209">另请参阅</span><span class="sxs-lookup"><span data-stu-id="af164-209">See Also</span></span>  
 <span data-ttu-id="af164-210">[Microsoft 顺序分析和聚类分析算法](microsoft-sequence-clustering-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="af164-210">[Microsoft Sequence Clustering Algorithm](microsoft-sequence-clustering-algorithm.md) </span></span>  
 <span data-ttu-id="af164-211">[顺序分析和聚类分析模型查询示例](clustering-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="af164-211">[Sequence Clustering Model Query Examples](clustering-model-query-examples.md) </span></span>  
 [<span data-ttu-id="af164-212">顺序分析和聚类分析模型的挖掘模型内容（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="af164-212">Mining Model Content for Sequence Clustering Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-sequence-clustering-models.md)  
  
  
