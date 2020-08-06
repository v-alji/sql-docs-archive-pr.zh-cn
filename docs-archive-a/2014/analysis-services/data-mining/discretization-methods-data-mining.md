---
title: 数据挖掘)  (离散化方法 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- content types [data mining]
- discretization [Analysis Services]
- columns [data mining], discretization
- THRESHOLDS method
- CLUSTERS method
- DiscretizationBuckets property
- AUTOMATIC method
- EQUAL_AREAS method
- coding [Data Mining]
ms.assetid: 02c0df7b-6ca5-4bd0-ba97-a5826c9da120
author: minewiskan
ms.author: owend
ms.openlocfilehash: feca59697c1c78a08e629b62856053f2d2ce6d6d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589962"
---
# <a name="discretization-methods-data-mining"></a><span data-ttu-id="8b607-102">离散化方法（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="8b607-102">Discretization Methods (Data Mining)</span></span>
  <span data-ttu-id="8b607-103">用于在中创建数据挖掘模型的某些算法 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 需要特定的内容类型才能正常工作。</span><span class="sxs-lookup"><span data-stu-id="8b607-103">Some algorithms that are used to create data mining models in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] require specific content types in order to function correctly.</span></span> <span data-ttu-id="8b607-104">例如， [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes 算法的输入不能为连续列，并且不能预测连续值。</span><span class="sxs-lookup"><span data-stu-id="8b607-104">For example, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm cannot use continuous columns as input and cannot predict continuous values.</span></span> <span data-ttu-id="8b607-105">另外，有些列可能会因包含的值太多而导致算法不易标识数据中据以创建模型的相关模式。</span><span class="sxs-lookup"><span data-stu-id="8b607-105">Additionally, some columns may contain so many values that the algorithm cannot easily identify interesting patterns in the data from which to create a model.</span></span>  
  
 <span data-ttu-id="8b607-106">在这些情况下，可以将列中的数据离散化，以便能够使用算法来生成挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="8b607-106">In these cases, you can discretize the data in the columns to enable the use of the algorithms to produce a mining model.</span></span> <span data-ttu-id="8b607-107">“离散化\*\* ”是将值放入存储桶中以便得到有限数目的可能状态的过程。</span><span class="sxs-lookup"><span data-stu-id="8b607-107">*Discretization* is the process of putting values into buckets so that there are a limited number of possible states.</span></span> <span data-ttu-id="8b607-108">存储桶本身是作为有序且离散的值处理的。</span><span class="sxs-lookup"><span data-stu-id="8b607-108">The buckets themselves are treated as ordered and discrete values.</span></span> <span data-ttu-id="8b607-109">数值列和字符串列都可以进行离散化。</span><span class="sxs-lookup"><span data-stu-id="8b607-109">You can discretize both numeric and string columns.</span></span>  
  
 <span data-ttu-id="8b607-110">离散化数据时，可以使用多种方法。</span><span class="sxs-lookup"><span data-stu-id="8b607-110">There are several methods that you can use to discretize data.</span></span> <span data-ttu-id="8b607-111">如果数据挖掘解决方案使用关系数据，则通过设置 <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> 属性的值可以控制对数据分组所使用的存储桶数。</span><span class="sxs-lookup"><span data-stu-id="8b607-111">If your data mining solution uses relational data, you can control the number of buckets to use for grouping data by setting the value of the <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> property.</span></span> <span data-ttu-id="8b607-112">默认存储桶数为 5。</span><span class="sxs-lookup"><span data-stu-id="8b607-112">The default number of buckets is 5.</span></span>  
  
 <span data-ttu-id="8b607-113">如果数据挖掘解决方案使用联机分析处理 (OLAP) 多维数据集中的数据，数据挖掘算法将使用以下公式自动计算要生成的存储桶数，其中 n 是列中数据非重复值的数目：</span><span class="sxs-lookup"><span data-stu-id="8b607-113">If your data mining solution uses data from an Online Analytical Processing (OLAP) cube, the data mining algorithm automatically computes the number of buckets to generate by using the following equation, where n is the number of distinct values of data in the column:</span></span>  
  
 `Number of Buckets = sqrt(n)`  
  
 <span data-ttu-id="8b607-114">如果不希望由 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 计算存储桶数目，则可使用 <xref:Microsoft.AnalysisServices.DimensionAttribute.DiscretizationBucketCount%2A> 属性来手动指定存储桶的数目。</span><span class="sxs-lookup"><span data-stu-id="8b607-114">If you do not want [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to calculate the number of buckets, you can use the <xref:Microsoft.AnalysisServices.DimensionAttribute.DiscretizationBucketCount%2A> property to manually specify the number of buckets.</span></span>  
  
 <span data-ttu-id="8b607-115">下表说明了可在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]中用于离散化数据的方法。</span><span class="sxs-lookup"><span data-stu-id="8b607-115">The following table describes the methods that you can use to discretize data in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
|<span data-ttu-id="8b607-116">离散化方法</span><span class="sxs-lookup"><span data-stu-id="8b607-116">Discretization method</span></span>|<span data-ttu-id="8b607-117">说明</span><span class="sxs-lookup"><span data-stu-id="8b607-117">Description</span></span>|  
|---------------------------|-----------------|  
|`AUTOMATIC`|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="8b607-118">确定要使用的离散化方法。</span><span class="sxs-lookup"><span data-stu-id="8b607-118">determines which discretization method to use.</span></span>|  
|`CLUSTERS`|<span data-ttu-id="8b607-119">该算法可以对定型数据采样，初始化为一些随机点，然后使用 Expectation Maximization (EM) 聚类分析方法运行几次 Microsoft 聚类分析算法迭代，以此将数据分组。</span><span class="sxs-lookup"><span data-stu-id="8b607-119">The algorithm divides the data into groups by sampling the training data, initializing to a number of random points, and then running several iterations of the Microsoft Clustering algorithm using the Expectation Maximization (EM) clustering method.</span></span> <span data-ttu-id="8b607-120">由于 `CLUSTERS` 方法可用于所有分布曲线，所以该方法很有用。</span><span class="sxs-lookup"><span data-stu-id="8b607-120">The `CLUSTERS` method is useful because it works on any distribution curve.</span></span> <span data-ttu-id="8b607-121">但是，该方法所需的处理时间比其他离散化方法的处理时间长。</span><span class="sxs-lookup"><span data-stu-id="8b607-121">However, it requires more processing time than the other discretization methods.</span></span><br /><br /> <span data-ttu-id="8b607-122">此方法只能用于数值列。</span><span class="sxs-lookup"><span data-stu-id="8b607-122">This method can only be used with numeric columns.</span></span>|  
|`EQUAL_AREAS`|<span data-ttu-id="8b607-123">该算法将数据分成值数目相同的若干个组。</span><span class="sxs-lookup"><span data-stu-id="8b607-123">The algorithm divides the data into groups that contain an equal number of values.</span></span> <span data-ttu-id="8b607-124">此方法最适用于正常分布曲线，但如果分布包含的值数量很大，并且这些值在连续数据的窄组中，则此方法的使用效果不是很好。</span><span class="sxs-lookup"><span data-stu-id="8b607-124">This method is best used for normal distribution curves, but does not work well if the distribution includes a large number of values that occur in a narrow group in the continuous data.</span></span> <span data-ttu-id="8b607-125">例如，如果项有一半的成本为 0，那么这一半数据将位于曲线上的某个点以下。</span><span class="sxs-lookup"><span data-stu-id="8b607-125">For example, if one-half of the items have a cost of 0, one-half the data will occur under a single point in the curve.</span></span> <span data-ttu-id="8b607-126">在这种分布中，此方法将对数据进行分解，以便在多个区域中建立相同的离散化。</span><span class="sxs-lookup"><span data-stu-id="8b607-126">In such a distribution, this method breaks the data up in an effort to establish equal discretization into multiple areas.</span></span> <span data-ttu-id="8b607-127">这样一来，生成的数据表示形式就会不准确。</span><span class="sxs-lookup"><span data-stu-id="8b607-127">This produces an inaccurate representation of the data.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b607-128">备注</span><span class="sxs-lookup"><span data-stu-id="8b607-128">Remarks</span></span>  
  
-   <span data-ttu-id="8b607-129">您可以使用 `EQUAL_AREAS` 方法来离散化字符串。</span><span class="sxs-lookup"><span data-stu-id="8b607-129">You can use the `EQUAL_AREAS` method to discretize strings.</span></span>  
  
-   <span data-ttu-id="8b607-130">`CLUSTERS` 方法使用 1000 个随机记录样本来离散化数据。</span><span class="sxs-lookup"><span data-stu-id="8b607-130">The `CLUSTERS` method uses a random sample of 1000 records to discretize data.</span></span> <span data-ttu-id="8b607-131">如果您不希望算法对数据采样，请使用 `EQUAL_AREAS` 方法。</span><span class="sxs-lookup"><span data-stu-id="8b607-131">Use the `EQUAL_AREAS` method if you do not want the algorithm to sample data.</span></span>  
  
-   <span data-ttu-id="8b607-132">神经网络挖掘模型教程提供了一个介绍如何自定义离散化的示例。</span><span class="sxs-lookup"><span data-stu-id="8b607-132">The neural network mining model tutorial provides an example of how discretization can be customized.</span></span> <span data-ttu-id="8b607-133">有关详细信息，请参阅[第5课：生成神经网络和逻辑回归模型 &#40;中级数据挖掘教程&#41;](../../tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="8b607-133">For more information, see [Lesson 5: Building Neural Network and Logistic Regression Models &#40;Intermediate Data Mining Tutorial&#41;](../../tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b607-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8b607-134">See Also</span></span>  
 <span data-ttu-id="8b607-135">[内容类型 &#40;数据挖掘&#41;](content-types-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="8b607-135">[Content Types &#40;Data Mining&#41;](content-types-data-mining.md) </span></span>  
 <span data-ttu-id="8b607-136">[内容类型 &#40;DMX&#41;](/sql/dmx/content-types-dmx) </span><span class="sxs-lookup"><span data-stu-id="8b607-136">[Content Types &#40;DMX&#41;](/sql/dmx/content-types-dmx) </span></span>  
 <span data-ttu-id="8b607-137">[数据挖掘算法 &#40;Analysis Services 数据挖掘&#41;](data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="8b607-137">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="8b607-138">[挖掘结构 &#40;Analysis Services 数据挖掘&#41;](mining-structures-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="8b607-138">[Mining Structures &#40;Analysis Services - Data Mining&#41;](mining-structures-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="8b607-139">[数据挖掘 &#40;的数据类型&#41;](data-types-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="8b607-139">[Data Types &#40;Data Mining&#41;](data-types-data-mining.md) </span></span>  
 <span data-ttu-id="8b607-140">[挖掘结构列](mining-structure-columns.md) </span><span class="sxs-lookup"><span data-stu-id="8b607-140">[Mining Structure Columns](mining-structure-columns.md) </span></span>  
 [<span data-ttu-id="8b607-141">列分布（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="8b607-141">Column Distributions &#40;Data Mining&#41;</span></span>](column-distributions-data-mining.md)  
  
  
