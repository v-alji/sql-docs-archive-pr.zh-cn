---
title: 测试和验证 (数据挖掘) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- testing data mining models
- comparing mining models
- continuous attribute charts
- data mining [Analysis Services], models
- charts [Analysis Services]
- predictive modeling [Analysis Services]
- mining models [Analysis Services], validating
- validating data mining models
- viewing mining accuracy
- confidence scores [data mining]
- displaying mining accuracy
- predictions [Analysis Services], comparing mining models
- scoring [data mining]
- lift charts [Analysis Services]
- classification matrix [Analysis Services]
- CRISP-DM
- accuracy testing [data mining]
ms.assetid: 197144f5-21ed-4009-b448-fe412fb3916c
author: minewiskan
ms.author: owend
ms.openlocfilehash: c12f0215daed0c3308c63f36df0ba323152ec8d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577073"
---
# <a name="testing-and-validation-data-mining"></a><span data-ttu-id="da16e-102">测试和验证（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="da16e-102">Testing and Validation (Data Mining)</span></span>
  <span data-ttu-id="da16e-103">验证是评估挖掘模型对实际数据执行情况的过程。</span><span class="sxs-lookup"><span data-stu-id="da16e-103">Validation is the process of assessing how well your mining models perform against real data.</span></span> <span data-ttu-id="da16e-104">在将挖掘模型部署到生产环境之前，务必通过了解其质量和特征来对其进行验证。</span><span class="sxs-lookup"><span data-stu-id="da16e-104">It is important that you validate your mining models by understanding their quality and characteristics before you deploy them into a production environment.</span></span>  
  
 <span data-ttu-id="da16e-105">本部分介绍与模型质量有关的一些基本概念，并介绍中提供的模型验证的策略 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="da16e-105">This section introduces some basic concepts related to model quality, and describes the strategies for model validation that are provided in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="da16e-106">有关模型验证如何适合更大数据挖掘过程的概述，请参阅 [数据挖掘解决方案](data-mining-solutions.md)。</span><span class="sxs-lookup"><span data-stu-id="da16e-106">For an overview of how model validation fits into the larger data mining process, see [Data Mining Solutions](data-mining-solutions.md).</span></span>  
  
## <a name="methods-for-testing-and-validation-of-data-mining-models"></a><span data-ttu-id="da16e-107">测试和验证数据挖掘模型的方法</span><span class="sxs-lookup"><span data-stu-id="da16e-107">Methods for Testing and Validation of Data Mining Models</span></span>  
 <span data-ttu-id="da16e-108">可以使用多种方法评估数据挖掘模型的质量和特征。</span><span class="sxs-lookup"><span data-stu-id="da16e-108">There are many approaches for assessing the quality and characteristics of a data mining model.</span></span>  
  
-   <span data-ttu-id="da16e-109">使用统计信息有效性的各种度量值来确定数据或模型中是否存在问题。</span><span class="sxs-lookup"><span data-stu-id="da16e-109">Use various measures of statistical validity to determine whether there are problems in the data or in the model.</span></span>  
  
-   <span data-ttu-id="da16e-110">将数据划分为定型集和测试集，以测试预测的准确性。</span><span class="sxs-lookup"><span data-stu-id="da16e-110">Separate the data into training and testing sets to test the accuracy of predictions.</span></span>  
  
-   <span data-ttu-id="da16e-111">请求商业专家查看数据挖掘模型的结果，以确定发现的模式在目标商业方案中是否有意义。</span><span class="sxs-lookup"><span data-stu-id="da16e-111">Ask business experts to review the results of the data mining model to determine whether the discovered patterns have meaning in the targeted business scenario</span></span>  
  
 <span data-ttu-id="da16e-112">所有这些方法在数据挖掘方法中都非常有用，在创建、测试和优化模型来解决特定问题时可以反复使用这些方法。</span><span class="sxs-lookup"><span data-stu-id="da16e-112">All of these methods are useful in data mining methodology and are used iteratively as you create, test, and refine models to answer a specific problem.</span></span> <span data-ttu-id="da16e-113">没有一个全面的规则可以说明什么时候模型已足够好，或者什么时候具有足够的数据。</span><span class="sxs-lookup"><span data-stu-id="da16e-113">No single comprehensive rule can tell you when a model is good enough, or when you have enough data.</span></span>  
  
## <a name="definition-of-criteria-for-validating-data-mining-models"></a><span data-ttu-id="da16e-114">验证数据挖掘模型的条件的定义</span><span class="sxs-lookup"><span data-stu-id="da16e-114">Definition of Criteria for Validating Data Mining Models</span></span>  
 <span data-ttu-id="da16e-115">数据挖掘的度量通常分为以下三类：准确性、可靠性和有用性。</span><span class="sxs-lookup"><span data-stu-id="da16e-115">Measures of data mining generally fall into the categories of accuracy, reliability, and usefulness.</span></span>  
  
 <span data-ttu-id="da16e-116">\*\* “准确性”是模型与所提供数据中的属性的结果相关联程度的度量值。</span><span class="sxs-lookup"><span data-stu-id="da16e-116">*Accuracy* is a measure of how well the model correlates an outcome with the attributes in the data that has been provided.</span></span> <span data-ttu-id="da16e-117">准确性有各种度量值，但准确性的所有度量值都依赖于所使用的数据。</span><span class="sxs-lookup"><span data-stu-id="da16e-117">There are various measures of accuracy, but all measures of accuracy are dependent on the data that is used.</span></span> <span data-ttu-id="da16e-118">事实上，值可能缺少或近似，数据可能已被多个进程更改。</span><span class="sxs-lookup"><span data-stu-id="da16e-118">In reality, values might be missing or approximate, or the data might have been changed by multiple processes.</span></span> <span data-ttu-id="da16e-119">特别是在探索和开发阶段，您可能决定允许数据中存在一定数量的错误，尤其是在数据的特征非常统一时。</span><span class="sxs-lookup"><span data-stu-id="da16e-119">Particularly in the phase of exploration and development, you might decide to accept a certain amount of error in the data, especially if the data is fairly uniform in its characteristics.</span></span> <span data-ttu-id="da16e-120">例如，基于过去的销售额来预测特定商店的销售额的模型可能非常相关，并且非常准确，即使该商店一直使用错误的会计方法。</span><span class="sxs-lookup"><span data-stu-id="da16e-120">For example, a model that predicts sales for a particular store based on past sales can be strongly correlated and very accurate, even if that store consistently used the wrong accounting method.</span></span> <span data-ttu-id="da16e-121">所以，准确性的度量值必须通过评估可靠性来平衡。</span><span class="sxs-lookup"><span data-stu-id="da16e-121">Therefore, measurements of accuracy must be balanced by assessments of reliability.</span></span>  
  
 <span data-ttu-id="da16e-122">\*\* “可靠性”评估数据挖掘模型处理不同数据集的方法。</span><span class="sxs-lookup"><span data-stu-id="da16e-122">*Reliability* assesses the way that a data mining model performs on different data sets.</span></span> <span data-ttu-id="da16e-123">如果无论提供哪些测试数据，数据挖掘模型都生成相同类型的预测，或者发现相同常规类型的模式，则该数据挖掘模型是可靠的。</span><span class="sxs-lookup"><span data-stu-id="da16e-123">A data mining model is reliable if it generates the same type of predictions or finds the same general kinds of patterns regardless of the test data that is supplied.</span></span> <span data-ttu-id="da16e-124">例如，为使用错误会计方法的商店生成预测的模型将不适用于其他商店，因此该模型是不可靠的。</span><span class="sxs-lookup"><span data-stu-id="da16e-124">For example, the model that you generate for the store that used the wrong accounting method would not generalize well to other stores, and therefore would not be reliable.</span></span>  
  
 <span data-ttu-id="da16e-125">\*\* “有用性”包括说明模型是否提供了有用信息的各种指标。</span><span class="sxs-lookup"><span data-stu-id="da16e-125">*Usefulness* includes various metrics that tell you whether the model provides useful information.</span></span> <span data-ttu-id="da16e-126">例如，将商店位置与销售额相关联的数据挖掘模型可能既是准确的，也是可靠的，但可能是无用的，因为不能通过在同一位置增加更多商店来推广该结果。</span><span class="sxs-lookup"><span data-stu-id="da16e-126">For example, a data mining model that correlates store location with sales might be both accurate and reliable, but might not be useful, because you cannot generalize that result by adding more stores at the same location.</span></span> <span data-ttu-id="da16e-127">而且，它没有回答为什么某些位置销售额较高这一基本商业问题。</span><span class="sxs-lookup"><span data-stu-id="da16e-127">Moreover, it does not answer the fundamental business question of why certain locations have more sales.</span></span> <span data-ttu-id="da16e-128">您可能还会发现，如果模型基于数据中的交叉关联，它看起来是成功，但实际上没有意义。</span><span class="sxs-lookup"><span data-stu-id="da16e-128">You might also find that a model that appears successful in fact is meaningless, because it is based on cross-correlations in the data.</span></span>  
  
## <a name="tools-for-testing-and-validation-of-mining-models"></a><span data-ttu-id="da16e-129">用于测试和验证挖掘模型的的工具</span><span class="sxs-lookup"><span data-stu-id="da16e-129">Tools for Testing and Validation of Mining Models</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="da16e-130">支持多种验证方法。</span><span class="sxs-lookup"><span data-stu-id="da16e-130">supports multiple approaches to validation of data mining solutions, supporting all phases of the data mining test methodology.</span></span>  
  
-   <span data-ttu-id="da16e-131">将数据分区为测试集和定型集</span><span class="sxs-lookup"><span data-stu-id="da16e-131">Partitioning data into testing and training sets.</span></span>  
  
-   <span data-ttu-id="da16e-132">筛选模型以便定型和测试同一源数据的不同组合。</span><span class="sxs-lookup"><span data-stu-id="da16e-132">Filtering models to train and test different combinations of the same source data.</span></span>  
  
-   <span data-ttu-id="da16e-133">测量“提升” \*\* 和“增长” \*\*。</span><span class="sxs-lookup"><span data-stu-id="da16e-133">Measuring *lift* and *gain*.</span></span> <span data-ttu-id="da16e-134">“提升图” \*\* 是将使用数据挖掘模型获得的改进与随机推测进行对比时，可视化所获得改进的方法。</span><span class="sxs-lookup"><span data-stu-id="da16e-134">A *lift chart* is a method of visualizing the improvement that you get from using a data mining model, when you compare it to random guessing.</span></span>  
  
-   <span data-ttu-id="da16e-135">执行数据集的交叉验证\*\*</span><span class="sxs-lookup"><span data-stu-id="da16e-135">Performing *cross-validation* of data sets</span></span>  
  
-   <span data-ttu-id="da16e-136">生成“分类矩阵” \*\*。</span><span class="sxs-lookup"><span data-stu-id="da16e-136">Generating *classification matrices*.</span></span> <span data-ttu-id="da16e-137">这些图在表中对准确和不准确的推测进行排序，以便可以快速方便地衡量模型预测目标值的准确程度。</span><span class="sxs-lookup"><span data-stu-id="da16e-137">These charts sort good and bad guesses into a table so that you can quickly and easily gauge how accurately the model predicts the target value.</span></span>  
  
-   <span data-ttu-id="da16e-138">创建“散点图” \*\* 以评估回归公式的拟合度。</span><span class="sxs-lookup"><span data-stu-id="da16e-138">Creating *scatter plots* to assess the fit of a regression formula.</span></span>  
  
-   <span data-ttu-id="da16e-139">创建将财务收益或成本与使用挖掘模型相关联的“利润图” \*\* ，以便评估建议的值。</span><span class="sxs-lookup"><span data-stu-id="da16e-139">Creating *profit charts* that associate financial gain or costs with the use of a mining model, so that you can assess the value of the recommendations.</span></span>  
  
 <span data-ttu-id="da16e-140">这些度量不能准确回答数据挖掘模型是否能解决商业问题等之类的问题；但它们提供了可用于评估预测性分析的可靠性的目标度量值，并指导您是否在开发流程中使用特定遍历的决策。</span><span class="sxs-lookup"><span data-stu-id="da16e-140">These metrics do not aim to answer the question of whether the data mining model answers your business question; rather, these metrics provide objective measurements that you can use to assess the reliability of your data for predictive analytics, and to guide your decision of whether to use a particular iterate on the development process.</span></span>  
  
 <span data-ttu-id="da16e-141">本节中的主题提供了每个方法的概述，并引导您使用 SQL Server 数据挖掘完成度量您生成的模型准确性的过程。</span><span class="sxs-lookup"><span data-stu-id="da16e-141">The topics in this section provide an overview of each method and walk you through the process of measuring the accuracy of models that you build using SQL Server Data Mining.</span></span>  
  
### <a name="related-topics"></a><span data-ttu-id="da16e-142">相关主题</span><span class="sxs-lookup"><span data-stu-id="da16e-142">Related Topics</span></span>  
  
|<span data-ttu-id="da16e-143">主题</span><span class="sxs-lookup"><span data-stu-id="da16e-143">Topics</span></span>|<span data-ttu-id="da16e-144">链接</span><span class="sxs-lookup"><span data-stu-id="da16e-144">Links</span></span>|  
|------------|-----------|  
|<span data-ttu-id="da16e-145">了解如何使用向导或 DMX 命令设置测试数据集</span><span class="sxs-lookup"><span data-stu-id="da16e-145">Learn how to set up a testing data set using a wizard or DMX commands</span></span>|[<span data-ttu-id="da16e-146">定型数据集和测试数据集</span><span class="sxs-lookup"><span data-stu-id="da16e-146">Training and Testing Data Sets</span></span>](training-and-testing-data-sets.md)|  
|<span data-ttu-id="da16e-147">了解如何测试挖掘结构中的数据分布和代表性</span><span class="sxs-lookup"><span data-stu-id="da16e-147">Learn how to test the distribution and representativeness of the data in a mining structure</span></span>|[<span data-ttu-id="da16e-148">交叉验证（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="da16e-148">Cross-Validation &#40;Analysis Services - Data Mining&#41;</span></span>](cross-validation-analysis-services-data-mining.md)|  
|<span data-ttu-id="da16e-149">了解有关 [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)]中提供的图标类型的准确性。</span><span class="sxs-lookup"><span data-stu-id="da16e-149">Learn about the accuracy chart types provided in [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)].</span></span>|[<span data-ttu-id="da16e-150">提升图（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="da16e-150">Lift Chart &#40;Analysis Services - Data Mining&#41;</span></span>](lift-chart-analysis-services-data-mining.md)<br /><br /> [<span data-ttu-id="da16e-151">利润图（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="da16e-151">Profit Chart &#40;Analysis Services - Data Mining&#41;</span></span>](profit-chart-analysis-services-data-mining.md)<br /><br /> [<span data-ttu-id="da16e-152">散点图（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="da16e-152">Scatter Plot &#40;Analysis Services - Data Mining&#41;</span></span>](scatter-plot-analysis-services-data-mining.md)|  
|<span data-ttu-id="da16e-153">了解如何创建分类矩阵（有时也称为混淆矩阵），以评估真正、假正、真负和假负的次数。</span><span class="sxs-lookup"><span data-stu-id="da16e-153">Learn how to create a classification matrix, sometimes called a confusion matrix, for assessing the number of true and false positives and negatives.</span></span>|[<span data-ttu-id="da16e-154">分类矩阵（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="da16e-154">Classification Matrix &#40;Analysis Services - Data Mining&#41;</span></span>](classification-matrix-analysis-services-data-mining.md)|  
  
## <a name="see-also"></a><span data-ttu-id="da16e-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="da16e-155">See Also</span></span>  
 <span data-ttu-id="da16e-156">[数据挖掘工具](data-mining-tools.md) </span><span class="sxs-lookup"><span data-stu-id="da16e-156">[Data Mining Tools](data-mining-tools.md) </span></span>  
 <span data-ttu-id="da16e-157">[数据挖掘解决方案](data-mining-solutions.md) </span><span class="sxs-lookup"><span data-stu-id="da16e-157">[Data Mining Solutions](data-mining-solutions.md) </span></span>  
 [<span data-ttu-id="da16e-158">测试和验证任务和操作指南（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="da16e-158">Testing and Validation Tasks and How-tos &#40;Data Mining&#41;</span></span>](testing-and-validation-tasks-and-how-tos-data-mining.md)  
  
  
