---
title: 数据挖掘属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- ClusterCount property
- AllowedProvidersInOpenRowset property
- MinimumSeriesValue property
- ScoreMethod property
- MinimumImportance property
- ModellingCardinality property
- BrentTolerance property
- ComplexityPenalty property
- MaximumItemsetCount property
- MinimumSupport property
- AllowSessionMiningModels property
- HoldoutPercentage property
- ClusterCountPrior property
- MaximumSequenceStates property
- OptimizedPredictionCount property
- data mining [Analysis Services], properties
- MaximumStates property
- MaximumContinuousInputAttributes property
- MaximumOutputAttributes property
- AllowAdHocOpenRowsetQueries property
- Enabled property
- HistoricModelGap property
- SampleSize property
- MaximumInputAttributes property
- PeriodicityHint property
- MissingValueSubstitution property
- SplitMethod property
- ForceRegressor property
- MaximumBucketsForContinuousSplit property
- MaxConcurrentPredictionQueries property
- MinimumItemsetSize property
- AcyclicGraph property
- HoldoutMethod property
- StoppingTolerance property
- properties [data mining]
- AutoDetectPeriodicity property
- HoldoutTolerance property
- MinimumLeafCases property
- HoldoutSeed property
- MinimumClusterCases property
- ClusterCountDeviation property
- MinimumDependencyProbability property
- ClusteringMethod property
- MaximumItemsetSize property
- HiddenNodeRatio property
- MaximumSeriesValue property
ms.assetid: 9bc9abed-180a-4bd8-b2eb-89c62fa88110
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5ed1c47faafeb0c680e6afb6f8e509c426760da2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694592"
---
# <a name="data-mining-properties"></a><span data-ttu-id="a801a-102">数据挖掘属性</span><span class="sxs-lookup"><span data-stu-id="a801a-102">Data Mining Properties</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="a801a-103">支持下表中列出的数据挖掘服务器属性。</span><span class="sxs-lookup"><span data-stu-id="a801a-103">supports the data mining server properties listed in the following tables.</span></span> <span data-ttu-id="a801a-104">有关更多服务器属性以及如何设置这些属性的详细信息，请参阅 [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="a801a-104">For more information about additional server properties and how to set them, see [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).</span></span>  
  
 <span data-ttu-id="a801a-105">**适用于：** 仅限多维服务器模式</span><span class="sxs-lookup"><span data-stu-id="a801a-105">**Applies to:** Multidimensional server mode only</span></span>  
  
## <a name="non-specific-category"></a><span data-ttu-id="a801a-106">非特定类别</span><span class="sxs-lookup"><span data-stu-id="a801a-106">Non-Specific Category</span></span>  
 `AllowSessionMiningModels`  
 <span data-ttu-id="a801a-107">一个布尔值属性，指示是否可以创建会话挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="a801a-107">A Boolean property that indicates whether session mining models can be created.</span></span>  
  
 <span data-ttu-id="a801a-108">此属性的默认值为 False，指示不能创建会话挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="a801a-108">The default value for this property is false, which indicates that session mining models cannot be created.</span></span>  
  
 `AllowAdHocOpenRowsetQueries`  
 <span data-ttu-id="a801a-109">布尔值属性，指示是否允许即席打开行集查询。</span><span class="sxs-lookup"><span data-stu-id="a801a-109">A Boolean property that indicates whether adhoc open rowset queries are allowed.</span></span>  
  
 <span data-ttu-id="a801a-110">此属性的默认值为 False，指示在会话期间不允许打开行集查询。</span><span class="sxs-lookup"><span data-stu-id="a801a-110">The default value for this property is false, which indicates that open rowset queries are not allowed during a session.</span></span>  
  
 `AllowedProvidersInOpenRowset`  
 <span data-ttu-id="a801a-111">字符串属性，标识在打开的行集中允许存在的提供程序，由以逗号/分号分隔的提供程序 ProgID 列表组成，或者为 [全部]。</span><span class="sxs-lookup"><span data-stu-id="a801a-111">A string property that identifies which providers are allowed in an open rowset, consisting of a comma/semi-colon separated list of provider ProgIDs, or else [All].</span></span>  
  
 `MaxConcurrentPredictionQueries`  
 <span data-ttu-id="a801a-112">有符号 32 位整数属性，用于定义并发预测查询的最大数目。</span><span class="sxs-lookup"><span data-stu-id="a801a-112">A signed 32-bit integer property that defines the maximum number of concurrent prediction queries.</span></span>  
  
## <a name="algorithms-category"></a><span data-ttu-id="a801a-113">算法类别</span><span class="sxs-lookup"><span data-stu-id="a801a-113">Algorithms Category</span></span>  
 `Microsoft_Association_Rules\ Enabled`  
 <span data-ttu-id="a801a-114">布尔值属性，指示是否启用 Microsoft_Association_Rules 算法。</span><span class="sxs-lookup"><span data-stu-id="a801a-114">A Boolean property that indicates whether the Microsoft_Association_Rules algorithm is enabled.</span></span>  
  
 `Microsoft_Clustering\ Enabled`  
 <span data-ttu-id="a801a-115">布尔值属性，指示是否启用 Microsoft_Clustering 算法。</span><span class="sxs-lookup"><span data-stu-id="a801a-115">A Boolean property that indicates whether the Microsoft_Clustering algorithm is enabled.</span></span>  
  
 `Microsoft_Decision_Trees\ Enabled`  
 <span data-ttu-id="a801a-116">布尔值属性，指示是否启用 Microsoft_DecisionTrees 算法。</span><span class="sxs-lookup"><span data-stu-id="a801a-116">A Boolean property that indicates whether the Microsoft_DecisionTrees algorithm is enabled.</span></span>  
  
 `Microsoft_Naive_Bayes\ Enabled`  
 <span data-ttu-id="a801a-117">布尔值属性，指示是否启用 Microsoft_ Naive_Bayes 算法。</span><span class="sxs-lookup"><span data-stu-id="a801a-117">A Boolean property that indicates whether the Microsoft_ Naive_Bayes algorithm is enabled.</span></span>  
  
 `Microsoft_Neural_Network\ Enabled`  
 <span data-ttu-id="a801a-118">布尔值属性，指示是否启用 Microsoft_Neural_Network 算法。</span><span class="sxs-lookup"><span data-stu-id="a801a-118">A Boolean property that indicates whether the Microsoft_Neural_Network algorithm is enabled.</span></span>  
  
 `Microsoft_Sequence_Clustering\ Enabled`  
 <span data-ttu-id="a801a-119">布尔值属性，指示是否启用 Microsoft_Sequence_Clustering 算法。</span><span class="sxs-lookup"><span data-stu-id="a801a-119">A Boolean property that indicates whether the Microsoft_Sequence_Clustering algorithm is enabled.</span></span>  
  
 `Microsoft_Time_Series\ Enabled`  
 <span data-ttu-id="a801a-120">布尔值属性，指示是否启用 Microsoft_Time_Series 算法。</span><span class="sxs-lookup"><span data-stu-id="a801a-120">A Boolean property that indicates whether the Microsoft_Time_Series algorithm is enabled.</span></span>  
  
 `Microsoft_Linear_Regression\ Enabled`  
 <span data-ttu-id="a801a-121">布尔值属性，指示是否启用 Microsoft_Linear_Regression 算法。</span><span class="sxs-lookup"><span data-stu-id="a801a-121">A Boolean property that indicates whether the Microsoft_Linear_Regression algorithm is enabled.</span></span>  
  
 `Microsoft_Logistic_Regression\ Enabled`  
 <span data-ttu-id="a801a-122">布尔值属性，指示是否启用 Microsoft_Logistic_Regression 算法。</span><span class="sxs-lookup"><span data-stu-id="a801a-122">A Boolean property that indicates whether the Microsoft_Logistic_Regression algorithm is enabled.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a801a-123">除了可定义服务器上可用的数据挖掘服务的属性外，还有定义特定算法的行为的数据挖掘属性。</span><span class="sxs-lookup"><span data-stu-id="a801a-123">In addition to properties that define the data mining services available on the server, there are data mining properties that define the behavior of specific algorithms.</span></span> <span data-ttu-id="a801a-124">您可在创建单个数据挖掘模型时，对这些属性进行配置（不在服务器级别）。</span><span class="sxs-lookup"><span data-stu-id="a801a-124">You configure these properties when you create an individual data mining model, not at the server level.</span></span> <span data-ttu-id="a801a-125">有关详细信息，请参阅[数据挖掘算法（Analysis Services - 数据挖掘）](../data-mining/data-mining-algorithms-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="a801a-125">For more information, see [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](../data-mining/data-mining-algorithms-analysis-services-data-mining.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a801a-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a801a-126">See Also</span></span>  
 <span data-ttu-id="a801a-127">[物理体系结构 &#40;Analysis Services 数据挖掘&#41;](../data-mining/physical-architecture-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="a801a-127">[Physical Architecture &#40;Analysis Services - Data Mining&#41;](../data-mining/physical-architecture-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="a801a-128">[在 Analysis Services 中配置服务器属性](server-properties-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="a801a-128">[Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="a801a-129">确定 Analysis Services 实例的服务器模式</span><span class="sxs-lookup"><span data-stu-id="a801a-129">Determine the Server Mode of an Analysis Services Instance</span></span>](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
