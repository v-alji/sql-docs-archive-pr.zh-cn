---
title: 基于使用情况的优化向导的 F1 帮助 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.usagebasedoptimizationwizard.f1
helpviewer_keywords:
- Usage-Based Optimization Wizard
ms.assetid: e5f5a938-ae7c-4f4e-9416-a7f94ac82763
author: minewiskan
ms.author: owend
ms.openlocfilehash: 517c122f79421294e1dfa562665948c4dc7bf95f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691346"
---
# <a name="usage-based-optimization-wizard-f1-help"></a><span data-ttu-id="39d00-102">基于使用情况的优化向导的 F1 帮助</span><span class="sxs-lookup"><span data-stu-id="39d00-102">Usage-Based Optimization Wizard F1 Help</span></span>
  <span data-ttu-id="39d00-103">基于使用情况的优化向导用于为分区设计聚合，它在输出方面与聚合设计向导相似。</span><span class="sxs-lookup"><span data-stu-id="39d00-103">The Usage-Based Optimization Wizard is similar in output to the Aggregation Design Wizard, and is used to design aggregations for a partition.</span></span> <span data-ttu-id="39d00-104">但是，基于使用情况的优化向导设计聚合时所基于的是 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例查询日志中所记录的特定使用模式的查询。</span><span class="sxs-lookup"><span data-stu-id="39d00-104">However, the Usage-Based Optimization Wizard designs aggregations based on the specific usage patterns of queries recorded in the query log of an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="39d00-105">聚合通过允许 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 直接从多维数据集存储中检索预先计算的总计，而不必为每个查询重新计算基础数据源中的数据，从而提高了性能。</span><span class="sxs-lookup"><span data-stu-id="39d00-105">Aggregations provide performance improvements by allowing [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] to retrieve pre-calculated totals directly from cube storage instead of having to recalculate data from an underlying data source for each query.</span></span>  
  
 <span data-ttu-id="39d00-106">若要从内打开基于使用情况的优化向导 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ，请为项目打开多维数据集设计器， [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 然后单击 "**聚合**" 选项卡。单击工具栏中的 "**基于使用情况的优化**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="39d00-106">To open the Usage-Based Optimization Wizard from within [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the cube designer for an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, and then click the **Aggregations** tab. Click the **Usage Based Optimization** button in the toolbar.</span></span>  
  
 <span data-ttu-id="39d00-107">要从 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 内打开基于使用情况的优化向导，请连接到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库，然后打开“多维数据集”\*\*\*\* 文件夹。</span><span class="sxs-lookup"><span data-stu-id="39d00-107">To open the Usage-Based Optimization Wizard from within [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], connect to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database and then open the **Cubes** folder.</span></span> <span data-ttu-id="39d00-108">选择多维数据集，然后打开 **“度量组”** 文件夹，然后展开要修改的度量组。</span><span class="sxs-lookup"><span data-stu-id="39d00-108">Select a cube and then open the **Measure Groups** folder and expand the measure group that you want to modify.</span></span> <span data-ttu-id="39d00-109">右键单击“分区”\*\*\*\* 文件夹，然后选择“基于使用情况的优化”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="39d00-109">Right-click the **Partitions** folder and then select **Usage Based Optimization**.</span></span>  
  
 <span data-ttu-id="39d00-110">若要对这些聚合进行设计，可以使用聚合设计向导。</span><span class="sxs-lookup"><span data-stu-id="39d00-110">To design these aggregations, you can use the Aggregation Design Wizard.</span></span> <span data-ttu-id="39d00-111">此向导可引导您完成以下步骤：</span><span class="sxs-lookup"><span data-stu-id="39d00-111">This wizard guides you through the following steps:</span></span>  
  
-   <span data-ttu-id="39d00-112">为分区、度量值组或多维数据集的存储和缓存选项选择标准或自定义设置。</span><span class="sxs-lookup"><span data-stu-id="39d00-112">Selecting standard or custom settings for the storage and caching options of a partition, measure group, or cube.</span></span>  
  
-   <span data-ttu-id="39d00-113">为分区、度量值组或多维数据集所引用的对象提供估计计数或实际计数。</span><span class="sxs-lookup"><span data-stu-id="39d00-113">Providing estimated or actual counts for objects referenced by the partition, measure group, or cube.</span></span>  
  
-   <span data-ttu-id="39d00-114">指定聚合选项和限制，以优化所设计聚合的存储和查询性能。</span><span class="sxs-lookup"><span data-stu-id="39d00-114">Specifying aggregation options and limits to optimize the storage and query performance delivered by designed aggregations.</span></span>  
  
-   <span data-ttu-id="39d00-115">保存并根据需要处理分区、度量值组或多维数据集，以生成定义的聚合。</span><span class="sxs-lookup"><span data-stu-id="39d00-115">Saving and optionally processing the partition, measure group, or cube to generate the defined aggregations.</span></span>  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] <span data-ttu-id="39d00-116">提供的聚合设计向导基于对分区结构的统计分析设计聚合，可生成受存储大小或估计性能提升范围限制的聚合设计。</span><span class="sxs-lookup"><span data-stu-id="39d00-116">provides the Aggregation Design Wizard to design aggregations based on statistical analysis of the structure of the partition to deliver an aggregation design that can be limited by storage size or estimated performance gain.</span></span> <span data-ttu-id="39d00-117">您可以使用聚合设计向导改进分区的总体性能，但是并不能针对业务用户的特定需要设计聚合。</span><span class="sxs-lookup"><span data-stu-id="39d00-117">You can use the Aggregation Design Wizard to improve the overall performance of a partition, but the aggregation design is not targeted to the specific needs of your business users.</span></span> <span data-ttu-id="39d00-118">基于使用情况的优化向导可以针对这些特定需要设计聚合，但前提是 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例的查询日志包含了构造此类查询所需的足够信息。</span><span class="sxs-lookup"><span data-stu-id="39d00-118">The Usage-Based Optimization Wizard can provide an aggregation design targeted to these specific needs, but the wizard can do so only if the query log for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance contains enough information to construct such queries.</span></span>  
  
 <span data-ttu-id="39d00-119">通常，可以同时使用这两个向导来改进在部署时和一段时间后的性能。</span><span class="sxs-lookup"><span data-stu-id="39d00-119">Typically, both wizards are used together to improve performance both upon deployment and over time.</span></span> <span data-ttu-id="39d00-120">在完成分区（或包含分区的多维数据集或度量值组）的初期部署后，应当首先使用聚合设计向导，以改进整体性能。</span><span class="sxs-lookup"><span data-stu-id="39d00-120">The Aggregation Design Wizard should be used first, when the partition (or the cube or measure group containing the partition) is initially deployed, to provide an overall performance benefit.</span></span> <span data-ttu-id="39d00-121">经过一段时间（在此期间您已在查询日志中记录了业务用户对分区的所有查询）之后，则可以使用基于使用情况的优化向导来进一步完善聚合设计，以便更好地满足业务用户的性能和查询要求。</span><span class="sxs-lookup"><span data-stu-id="39d00-121">After a period of time during which you have recorded the queries of business users for the partition in the query log, you can then use the Usage-Based Optimization Wizard to further focus the aggregation design to better serve the performance and query requirements of your business users.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="39d00-122">有关配置查询日志的信息，请参阅 [配置 Analysis Services 查询日志](instances/log-operations-in-analysis-services.md?view=sql-server-2014#bkmk_querylog)。</span><span class="sxs-lookup"><span data-stu-id="39d00-122">For information about configuring the query log, see [Configuring the Analysis Services Query Log](instances/log-operations-in-analysis-services.md?view=sql-server-2014#bkmk_querylog).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="39d00-123">本节内容</span><span class="sxs-lookup"><span data-stu-id="39d00-123">In This Section</span></span>  
  
-   [<span data-ttu-id="39d00-124">选择要修改 &#40;基于使用情况的优化向导的分区&#41;</span><span class="sxs-lookup"><span data-stu-id="39d00-124">Select Partitions to Modify &#40;Usage-Based Optimization Wizard&#41;</span></span>](select-partitions-to-modify-usage-based-optimization-wizard.md)  
  
-   [<span data-ttu-id="39d00-125">指定基于使用情况的优化向导 &#40;查询条件&#41;</span><span class="sxs-lookup"><span data-stu-id="39d00-125">Specify Query Criteria &#40;Usage-Based Optimization Wizard&#41;</span></span>](specify-query-criteria-usage-based-optimization-wizard.md)  
  
-   [<span data-ttu-id="39d00-126">查看将优化 &#40;基于使用情况的优化向导的查询&#41;</span><span class="sxs-lookup"><span data-stu-id="39d00-126">Review the Queries that will be Optimized &#40;Usage-Based Optimization Wizard&#41;</span></span>](review-the-queries-that-will-be-optimized-usage-based-optimization-wizard.md)  
  
-   [<span data-ttu-id="39d00-127">查看聚合使用情况 &#40;基于使用情况的优化向导&#41;</span><span class="sxs-lookup"><span data-stu-id="39d00-127">Review Aggregation Usage &#40;Usage-Based Optimiation Wizard&#41;</span></span>](review-aggregation-usage-usage-based-optimiation-wizard.md)  
  
-   [<span data-ttu-id="39d00-128">指定基于使用情况的优化向导 &#40;对象计数&#41;</span><span class="sxs-lookup"><span data-stu-id="39d00-128">Specify Object Counts &#40;Usage-Based Optimization Wizard&#41;</span></span>](specify-object-counts-usage-based-optimization-wizard.md)  
  
-   [<span data-ttu-id="39d00-129">使用基于使用情况的优化向导 &#40;设置聚合选项&#41;</span><span class="sxs-lookup"><span data-stu-id="39d00-129">Set Aggregation Options &#40;Usage-Based Optimization Wizard&#41;</span></span>](set-aggregation-options-usage-based-optimization-wizard.md)  
  
-   [<span data-ttu-id="39d00-130">完成向导 &#40;基于使用情况的优化向导&#41;</span><span class="sxs-lookup"><span data-stu-id="39d00-130">Completing the Wizard &#40;Usage-Based Optimization Wizard&#41;</span></span>](completing-the-wizard-usage-based-optimization-wizard.md)  
  
## <a name="see-also"></a><span data-ttu-id="39d00-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="39d00-131">See Also</span></span>  
 <span data-ttu-id="39d00-132">[聚合和聚合设计](multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md) </span><span class="sxs-lookup"><span data-stu-id="39d00-132">[Aggregations and Aggregation Designs](multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md) </span></span>  
 <span data-ttu-id="39d00-133">[多维模型中的多维数据集](multidimensional-models/cubes-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="39d00-133">[Cubes in Multidimensional Models](multidimensional-models/cubes-in-multidimensional-models.md) </span></span>  
 <span data-ttu-id="39d00-134">[聚合设计向导的 F1 帮助](aggregation-design-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="39d00-134">[Aggregation Design Wizard F1 Help](aggregation-design-wizard-f1-help.md) </span></span>  
 [<span data-ttu-id="39d00-135">&#40;多维数据的 Analysis Services 向导&#41;</span><span class="sxs-lookup"><span data-stu-id="39d00-135">Analysis Services Wizards &#40;Multidimensional Data&#41;</span></span>](analysis-services-wizards-multidimensional-data.md)  
  
  
