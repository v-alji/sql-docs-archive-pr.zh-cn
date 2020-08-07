---
title: Microsoft 聚类分析算法 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- segmentation algorithms [Analysis Services]
- nearest neighbor [Data Mining]
- clustering [Data Mining]
- clusters [Analysis Services]
- relationships [Analysis Services], clusters
- algorithms [data mining]
- classification algorithms [Analysis Services]
- datasets [Analysis Services]
- clustering algorithms [Analysis Services]
ms.assetid: 92a1e67e-f46e-4960-99b2-4d20f6192fbd
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9cb14e1e2672cfaef883f0686fc29206b0c8e657
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588153"
---
# <a name="microsoft-clustering-algorithm"></a><span data-ttu-id="4bd2d-102">Microsoft Clustering Algorithm</span><span class="sxs-lookup"><span data-stu-id="4bd2d-102">Microsoft Clustering Algorithm</span></span>
  <span data-ttu-id="4bd2d-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 聚类分析算法是 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 提供的分段算法。</span><span class="sxs-lookup"><span data-stu-id="4bd2d-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Clustering algorithm is a segmentation algorithm provided by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="4bd2d-104">该算法使用迭代技术将数据集中的事例分组为包含类似特征的分类。</span><span class="sxs-lookup"><span data-stu-id="4bd2d-104">The algorithm uses iterative techniques to group cases in a dataset into clusters that contain similar characteristics.</span></span> <span data-ttu-id="4bd2d-105">在浏览数据、标识数据中的异常及创建预测时，这些分组十分有用。</span><span class="sxs-lookup"><span data-stu-id="4bd2d-105">These groupings are useful for exploring data, identifying anomalies in the data, and creating predictions.</span></span>

 <span data-ttu-id="4bd2d-106">聚类分析模型标识数据集中可能无法通过随意观察在逻辑上得出的关系。</span><span class="sxs-lookup"><span data-stu-id="4bd2d-106">Clustering models identify relationships in a dataset that you might not logically derive through casual observation.</span></span> <span data-ttu-id="4bd2d-107">例如，在逻辑上可以得知，骑自行车上下班的人的居住地点通常离其工作地点不远。</span><span class="sxs-lookup"><span data-stu-id="4bd2d-107">For example, you can logically discern that people who commute to their jobs by bicycle do not typically live a long distance from where they work.</span></span> <span data-ttu-id="4bd2d-108">但该算法可以找出有关骑自行车上下班人员的其他并不明显的特征。</span><span class="sxs-lookup"><span data-stu-id="4bd2d-108">The algorithm, however, can find other characteristics about bicycle commuters that are not as obvious.</span></span> <span data-ttu-id="4bd2d-109">在下面的关系图中，分类 A 表示有关通常开车上班人员的数据，而分类 B 表示通常骑自行车上班人员的数据。</span><span class="sxs-lookup"><span data-stu-id="4bd2d-109">In the following diagram, cluster A represents data about people who tend to drive to work, while cluster B represents data about people who tend to ride bicycles to work.</span></span>

 <span data-ttu-id="4bd2d-110">![往返式群集模式](../media/clustering-example.gif "往返式群集模式")</span><span class="sxs-lookup"><span data-stu-id="4bd2d-110">![Cluster pattern of commuter tendencies](../media/clustering-example.gif "Cluster pattern of commuter tendencies")</span></span>

 <span data-ttu-id="4bd2d-111">聚类分析算法不同于 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 决策树算法等其他数据挖掘算法，区别在于无需指定可预测列便能生成聚类分析模型。</span><span class="sxs-lookup"><span data-stu-id="4bd2d-111">The clustering algorithm differs from other data mining algorithms, such as the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm, in that you do not have to designate a predictable column to be able to build a clustering model.</span></span> <span data-ttu-id="4bd2d-112">聚类分析算法严格地根据数据以及该算法所标识的分类中存在的关系定型。</span><span class="sxs-lookup"><span data-stu-id="4bd2d-112">The clustering algorithm trains the model strictly from the relationships that exist in the data and from the clusters that the algorithm identifies.</span></span>

## <a name="example"></a><span data-ttu-id="4bd2d-113">示例</span><span class="sxs-lookup"><span data-stu-id="4bd2d-113">Example</span></span>
 <span data-ttu-id="4bd2d-114">考虑这样一组人员，他们共享类似的人口统计信息并从 [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] 公司购买类似的产品。</span><span class="sxs-lookup"><span data-stu-id="4bd2d-114">Consider a group of people who share similar demographic information and who buy similar products from the [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] company.</span></span> <span data-ttu-id="4bd2d-115">这组人员就表示一个数据分类。</span><span class="sxs-lookup"><span data-stu-id="4bd2d-115">This group of people represents a cluster of data.</span></span> <span data-ttu-id="4bd2d-116">数据库中可能存在多个这样的分类。</span><span class="sxs-lookup"><span data-stu-id="4bd2d-116">Several such clusters may exist in a database.</span></span> <span data-ttu-id="4bd2d-117">通过观察构成分类的各列，可以更清楚地了解数据集中的记录如何相互关联。</span><span class="sxs-lookup"><span data-stu-id="4bd2d-117">By observing the columns that make up a cluster, you can more clearly see how records in a dataset are related to one another.</span></span>

## <a name="how-the-algorithm-works"></a><span data-ttu-id="4bd2d-118">算法的原理</span><span class="sxs-lookup"><span data-stu-id="4bd2d-118">How the Algorithm Works</span></span>
 <span data-ttu-id="4bd2d-119">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 聚类分析算法首先标识数据集中的关系并根据这些关系生成一系列分类。</span><span class="sxs-lookup"><span data-stu-id="4bd2d-119">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Clustering algorithm first identifies relationships in a dataset and generates a series of clusters based on those relationships.</span></span> <span data-ttu-id="4bd2d-120">散点图是一种非常有用的方法，可以直观地表示算法如何对数据进行分组，如下面的关系图所示。</span><span class="sxs-lookup"><span data-stu-id="4bd2d-120">A scatter plot is a useful way to visually represent how the algorithm groups data, as shown in the following diagram.</span></span> <span data-ttu-id="4bd2d-121">散点图可以表示数据集中的所有事例，在该图中每个事例就是一个点。</span><span class="sxs-lookup"><span data-stu-id="4bd2d-121">The scatter plot represents all the cases in the dataset, and each case is a point on the graph.</span></span> <span data-ttu-id="4bd2d-122">分类对该图中的点进行分组并阐释该算法所标识的关系。</span><span class="sxs-lookup"><span data-stu-id="4bd2d-122">The clusters group points on the graph and illustrate the relationships that the algorithm identifies.</span></span>

 <span data-ttu-id="4bd2d-123">![数据集中事例的散点图](../media/clustering-plot.gif "数据集中事例的散点图")</span><span class="sxs-lookup"><span data-stu-id="4bd2d-123">![Scatter plot of cases in a dataset](../media/clustering-plot.gif "Scatter plot of cases in a dataset")</span></span>

 <span data-ttu-id="4bd2d-124">在最初定义分类后，算法将通过计算确定分类表示点分组情况的适合程度，然后尝试重新定义这些分组以创建可以更好地表示数据的分类。</span><span class="sxs-lookup"><span data-stu-id="4bd2d-124">After first defining the clusters, the algorithm calculates how well the clusters represent groupings of the points, and then tries to redefine the groupings to create clusters that better represent the data.</span></span> <span data-ttu-id="4bd2d-125">该算法将循环执行此过程，直到它不能再通过重新定义分类来改进结果为止。</span><span class="sxs-lookup"><span data-stu-id="4bd2d-125">The algorithm iterates through this process until it cannot improve the results more by redefining the clusters.</span></span>

 <span data-ttu-id="4bd2d-126">通过选择指定的聚类分析方法，可以自定义该算法的工作方式，从而限制分类的最大数量，或者更改创建一个分类所必需的支持量。</span><span class="sxs-lookup"><span data-stu-id="4bd2d-126">You can customize the way the algorithm works by selecting a specifying a clustering technique, limiting the maximum number of clusters, or changing the amount of support required to create a cluster.</span></span> <span data-ttu-id="4bd2d-127">有关详细信息，请参阅 [Microsoft 聚类分析算法技术参考](microsoft-clustering-algorithm-technical-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="4bd2d-127">For more information, see [Microsoft Clustering Algorithm Technical Reference](microsoft-clustering-algorithm-technical-reference.md).</span></span>

## <a name="data-required-for-clustering-models"></a><span data-ttu-id="4bd2d-128">聚类分析模型所必需的数据</span><span class="sxs-lookup"><span data-stu-id="4bd2d-128">Data Required for Clustering Models</span></span>
 <span data-ttu-id="4bd2d-129">准备用于定型聚类分析模型的数据时，应理解特定算法的要求，其中包括所需要的数据量以及使用数据的方式。</span><span class="sxs-lookup"><span data-stu-id="4bd2d-129">When you prepare data for use in training a clustering model, you should understand the requirements for the particular algorithm, including how much data is needed, and how the data is used.</span></span>

 <span data-ttu-id="4bd2d-130">聚类分析模型的要求如下：</span><span class="sxs-lookup"><span data-stu-id="4bd2d-130">The requirements for a clustering model are as follows:</span></span>

-   <span data-ttu-id="4bd2d-131">**单键列** 每个模型都必须包含一个用于唯一标识每条记录的数值列或文本列。</span><span class="sxs-lookup"><span data-stu-id="4bd2d-131">**A single key column** Each model must contain one numeric or text column that uniquely identifies each record.</span></span> <span data-ttu-id="4bd2d-132">不允许复合键。</span><span class="sxs-lookup"><span data-stu-id="4bd2d-132">Compound keys are not allowed.</span></span>

-   <span data-ttu-id="4bd2d-133">**输入列** 每个模型都必须至少包含一个输入列，该输入列包含用于生成此分类的值。</span><span class="sxs-lookup"><span data-stu-id="4bd2d-133">**Input columns** Each model must contain at least one input column that contains the values that are used to build the clusters.</span></span> <span data-ttu-id="4bd2d-134">可以根据需要拥有任意多的输入列，但是具体取决于每个列中值的数量，添加额外列会增加定型模型所需的时间。</span><span class="sxs-lookup"><span data-stu-id="4bd2d-134">You can have as many input columns as you want, but depending on the number of values in each column, the addition of extra columns can increase the time it takes to train the model.</span></span>

-   <span data-ttu-id="4bd2d-135">**可选可预测列** 该算法不需要可预测列来生成模型，但是可以添加几乎任意数据类型的可预测列。</span><span class="sxs-lookup"><span data-stu-id="4bd2d-135">**Optional predictable column** The algorithm does not need a predictable column to build the model, but you can add a predictable column of almost any data type.</span></span> <span data-ttu-id="4bd2d-136">可以将可预测列的值视为对聚类分析模型的输入，或者将其指定仅用于预测。</span><span class="sxs-lookup"><span data-stu-id="4bd2d-136">The values of the predictable column can be treated as input to the clustering model, or you can specify that it be used for prediction only.</span></span> <span data-ttu-id="4bd2d-137">例如，如果需要通过对人口统计信息（如地区或年龄）进行分类来预测客户的收入，则可将收入指定为 `PredictOnly`，然后将所有其他列（如地区和年龄）添加为输入。</span><span class="sxs-lookup"><span data-stu-id="4bd2d-137">For example, if you want to predict customer income by clustering on demographics such as region or age, you would specify income as `PredictOnly` and add all the other columns, such as region or age, as inputs.</span></span>

 <span data-ttu-id="4bd2d-138">有关聚类分析模型支持的内容类型和数据类型的更多详细信息，请参阅 [Microsoft 聚类分析算法技术参考](microsoft-clustering-algorithm-technical-reference.md)的“要求”部分。</span><span class="sxs-lookup"><span data-stu-id="4bd2d-138">For more detailed information about the content types and data types supported for clustering models, see the Requirements section of [Microsoft Clustering Algorithm Technical Reference](microsoft-clustering-algorithm-technical-reference.md).</span></span>

## <a name="viewing-a-clustering-model"></a><span data-ttu-id="4bd2d-139">查看聚类分析模型</span><span class="sxs-lookup"><span data-stu-id="4bd2d-139">Viewing a Clustering Model</span></span>
 <span data-ttu-id="4bd2d-140">若要浏览该模型，可以使用 **Microsoft 分类查看器**。</span><span class="sxs-lookup"><span data-stu-id="4bd2d-140">To explore the model, you can use the **Microsoft Cluster Viewer**.</span></span> <span data-ttu-id="4bd2d-141">查看聚类分析模型时， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 将在一个关系图中显示分类（该关系图描绘了分类之间的关系），还提供了每个分类的详细配置文件、将每个分类与其他分类区分开来的属性列表以及整个定型数据集的特征。</span><span class="sxs-lookup"><span data-stu-id="4bd2d-141">When you view a clustering model, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] shows you the clusters in a diagram that depicts the relationships among clusters, and also provides a detailed profile of each cluster, a list of the attributes that distinguish each cluster from the others, and the characteristics of the entire training data set.</span></span> <span data-ttu-id="4bd2d-142">有关详细信息，请参阅 [使用 Microsoft 分类查看器浏览模型](browse-a-model-using-the-microsoft-cluster-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="4bd2d-142">For more information, see [Browse a Model Using the Microsoft Cluster Viewer](browse-a-model-using-the-microsoft-cluster-viewer.md).</span></span>

 <span data-ttu-id="4bd2d-143">如果希望了解更多详细信息，可在 [Microsoft 一般内容树查看器](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)中浏览该模型。</span><span class="sxs-lookup"><span data-stu-id="4bd2d-143">If you want to know more detail, you can browse the model in the [Microsoft Generic Content Tree Viewer](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md).</span></span> <span data-ttu-id="4bd2d-144">为该模型存储的内容包括每个节点中所有值的分布、每个分类的概率以及其他信息。</span><span class="sxs-lookup"><span data-stu-id="4bd2d-144">The content stored for the model includes the distribution for all values in each node, the probability of each cluster, and other information.</span></span> <span data-ttu-id="4bd2d-145">有关详细信息，请参阅 [聚类分析模型的挖掘模型内容（Analysis Services - 数据挖掘）](mining-model-content-for-clustering-models-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="4bd2d-145">For more information, see [Mining Model Content for Clustering Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-clustering-models-analysis-services-data-mining.md).</span></span>

## <a name="creating-predictions"></a><span data-ttu-id="4bd2d-146">创建预测</span><span class="sxs-lookup"><span data-stu-id="4bd2d-146">Creating Predictions</span></span>
 <span data-ttu-id="4bd2d-147">为模型定型后，结果将存储为一组模式，您可以浏览该模型或利用它来作出预测。</span><span class="sxs-lookup"><span data-stu-id="4bd2d-147">After the model has been trained, the results are stored as a set of patterns, which you can explore or use to make predictions.</span></span>

 <span data-ttu-id="4bd2d-148">可以创建查询，用于返回关于新数据是否适合所发现分类的预测，或者用于获取有关该分类的描述性统计信息。</span><span class="sxs-lookup"><span data-stu-id="4bd2d-148">You can create queries to return predictions about whether new data fits into the clusters that were discovered, or to obtain descriptive statistics about the clusters.</span></span>

 <span data-ttu-id="4bd2d-149">有关如何创建针对数据挖掘模型的查询的信息，请参阅 [数据挖掘查询](data-mining-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="4bd2d-149">For information about how to create queries against a data mining model, see [Data Mining Queries](data-mining-queries.md).</span></span> <span data-ttu-id="4bd2d-150">有关如何使用针对聚类分析模型的查询的示例，请参阅 [聚类分析模型查询示例](clustering-model-query-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="4bd2d-150">For examples of how to use queries with a clustering model, see [Clustering Model Query Examples](clustering-model-query-examples.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="4bd2d-151">备注</span><span class="sxs-lookup"><span data-stu-id="4bd2d-151">Remarks</span></span>

-   <span data-ttu-id="4bd2d-152">支持使用预测模型标记语言 (PMML) 创建挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="4bd2d-152">Supports the use of Predictive Model Markup Language (PMML) to create mining models.</span></span>

-   <span data-ttu-id="4bd2d-153">支持钻取。</span><span class="sxs-lookup"><span data-stu-id="4bd2d-153">Supports drillthrough.</span></span>

-   <span data-ttu-id="4bd2d-154">支持使用 OLAP 挖掘模型和创建数据挖掘维度。</span><span class="sxs-lookup"><span data-stu-id="4bd2d-154">Supports the use of OLAP mining models and the creation of data mining dimensions.</span></span>

## <a name="see-also"></a><span data-ttu-id="4bd2d-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4bd2d-155">See Also</span></span>
 <span data-ttu-id="4bd2d-156">[数据挖掘算法 &#40;Analysis Services 数据挖掘&#41;](data-mining-algorithms-analysis-services-data-mining.md) [Microsoft 聚类分析算法技术参考](microsoft-clustering-algorithm-technical-reference.md)[群集模型的挖掘模型内容 &#40;Analysis Services 数据挖掘&#41;](mining-model-content-for-clustering-models-analysis-services-data-mining.md) [聚类分析模型查询示例](clustering-model-query-examples.md)</span><span class="sxs-lookup"><span data-stu-id="4bd2d-156">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md) [Microsoft Clustering Algorithm Technical Reference](microsoft-clustering-algorithm-technical-reference.md) [Mining Model Content for Clustering Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-clustering-models-analysis-services-data-mining.md) [Clustering Model Query Examples](clustering-model-query-examples.md)</span></span>


