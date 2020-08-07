---
title: 创建数据挖掘模型 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining models, creating
- forecasting [data mining]
- mining models, creating
- clustering [data mining]
- association [data mining]
- data modeling [data mining]
- estimation
- classification [data mining]
ms.assetid: 804b7db3-1f6a-4f73-a81d-bbe02520d7c6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1e27739d3733c0b48dc6cff3e83e01f9cb12bce7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587643"
---
# <a name="creating-a-data-mining-model"></a><span data-ttu-id="533d3-102">创建数据挖掘模型</span><span class="sxs-lookup"><span data-stu-id="533d3-102">Creating a Data Mining Model</span></span>
  <span data-ttu-id="533d3-103">数据建模是数据挖掘的一个步骤，通过将*算法*应用于数据来构建模式和趋势。</span><span class="sxs-lookup"><span data-stu-id="533d3-103">Data modeling is the step of data mining where you build patterns and trends by applying *algorithms* to data.</span></span> <span data-ttu-id="533d3-104">之后，可以使用这些模式进行分析或预测。</span><span class="sxs-lookup"><span data-stu-id="533d3-104">Later you can use those patterns for analysis, or to make predictions.</span></span>  
  
 <span data-ttu-id="533d3-105">Office 数据挖掘外接程序通过向导（使用这些向导可轻松地创建模型）支持数据挖掘。</span><span class="sxs-lookup"><span data-stu-id="533d3-105">The Data Mining Add-ins for Office support data mining through wizards that make it easy to create models.</span></span> <span data-ttu-id="533d3-106">这些向导对数据进行分析、标识关联、计算所有变量的统计重要性，以及自动选择最佳模型。</span><span class="sxs-lookup"><span data-stu-id="533d3-106">The wizards analyze the data, identify correlations, compute statistical significance of all variables, and automatically select the best model.</span></span>  
  
 <span data-ttu-id="533d3-107">尽管此功能的功能与和提供的数据挖掘工具一样强大 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，但 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 向导和熟悉的 Excel 界面的组合使你可以轻松地创建、修改和使用数据挖掘。</span><span class="sxs-lookup"><span data-stu-id="533d3-107">Although this functionality is every bit as powerful as the data mining tools provided by [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] and [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], the combination of wizards and the familiar Excel interface makes it easy to create, modify, and use data mining.</span></span>  
  
## <a name="advanced-data-mining"></a><span data-ttu-id="533d3-108">高级（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="533d3-108">Advanced (Data Mining)</span></span>  
 <span data-ttu-id="533d3-109">使用高级向导，您可以通过使用中的数据挖掘算法之一，基于在 Excel 中存储的数据创建新的数据挖掘模型 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="533d3-109">The Advanced wizards let you create new data mining models, based on data stored in Excel, by using one of the data mining algorithms in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
### <a name="create-mining-structure"></a><span data-ttu-id="533d3-110">创建挖掘结构</span><span class="sxs-lookup"><span data-stu-id="533d3-110">Create Mining Structure</span></span>  
 <span data-ttu-id="533d3-111">创建挖掘结构向导可帮助您生成新的数据挖掘结构并将其用作多个挖掘模型的基础。</span><span class="sxs-lookup"><span data-stu-id="533d3-111">The Create Mining Structure wizard helps you build a new data mining structure, which you can use as the basis for multiple mining models.</span></span> <span data-ttu-id="533d3-112">通过该向导，可以选择保留要用作测试集的数据部分，因此，您可以按照一致的测试标准来对所有使用相同数据的模型进行评估。</span><span class="sxs-lookup"><span data-stu-id="533d3-112">The wizard gives you the option to set aside a portion of the data to use as a testing set, so that you can evaluate all models that use the same data according to a consistent testing standard.</span></span>  
  
 [<span data-ttu-id="533d3-113">SQL Server 数据挖掘外接程序创建挖掘结构 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="533d3-113">Create Mining Structure &#40;SQL Server Data Mining Add-ins&#41;</span></span>](create-mining-structure-sql-server-data-mining-add-ins.md)  
  
### <a name="add-model-to-structure"></a><span data-ttu-id="533d3-114">将模型添加到结构</span><span class="sxs-lookup"><span data-stu-id="533d3-114">Add Model to Structure</span></span>  
 <span data-ttu-id="533d3-115">通过将模型添加到结构向导，可以选择现有的数据挖掘结构，并为该结构创建新的数据挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="533d3-115">The Add Model to Structure wizard lets you choose an existing data mining structure and create a new data mining model for it.</span></span> <span data-ttu-id="533d3-116">可以向结构中添加多个挖掘模型、更改参数或选择不同的数据挖掘算法，并自定义输出。</span><span class="sxs-lookup"><span data-stu-id="533d3-116">You can add multiple mining models to a structure, changing the parameters or choosing different data mining algorithms, and customize the output.</span></span>  
  
 [<span data-ttu-id="533d3-117">将模型添加到用于 Excel 的数据挖掘外接 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="533d3-117">Add Model to Structure &#40;Data Mining Add-ins for Excel&#41;</span></span>](add-model-to-structure-data-mining-add-ins-for-excel.md)  
  
## <a name="analyze-key-influencers-analyze"></a><span data-ttu-id="533d3-118">分析关键影响因素（分析）</span><span class="sxs-lookup"><span data-stu-id="533d3-118">Analyze Key Influencers (Analyze)</span></span>  
 <span data-ttu-id="533d3-119">您选择感兴趣的列或输出值，然后算法将分析所有输入数据，以便标识对目标影响最大的因素。</span><span class="sxs-lookup"><span data-stu-id="533d3-119">You choose a column or output value of interest, and then the algorithm analyzes all the input data to identify the factors that have the most influence on the target.</span></span> <span data-ttu-id="533d3-120">或者，您可以创建比较任何两个值的报告，以便可以看到影响因素是如何变化的。</span><span class="sxs-lookup"><span data-stu-id="533d3-120">Optionally, you can create a report that compares any two values, so that you can see how the influencers change.</span></span>  
  
 <span data-ttu-id="533d3-121">"**分析关键影响因素**" 工具使用 Microsoft Bayes 算法。</span><span class="sxs-lookup"><span data-stu-id="533d3-121">The **Analyze Key Influencers** tool uses the Microsoft Naïve Bayes algorithm.</span></span>  
  
 [<span data-ttu-id="533d3-122">分析&#41;Excel &#40;表分析工具的关键影响因素</span><span class="sxs-lookup"><span data-stu-id="533d3-122">Analyze Key Influencers &#40;Table Analysis Tools for Excel&#41;</span></span>](analyze-key-influencers-table-analysis-tools-for-excel.md)  
  
## <a name="associate-data-mining"></a><span data-ttu-id="533d3-123">关联（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="533d3-123">Associate (Data Mining)</span></span>  
 <span data-ttu-id="533d3-124">**关联**向导生成一个关联模型，用于检测在多个事务中出现的项之间的关联：例如，在市场篮分析中。</span><span class="sxs-lookup"><span data-stu-id="533d3-124">The **Associate** wizard builds an association model that detects associations between items that appear in multiple transactions: for example, in market basket analysis.</span></span>  
  
 [<span data-ttu-id="533d3-125">用于 Excel 的数据挖掘客户端的关联向导 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="533d3-125">Associate Wizard &#40;Data Mining Client for Excel&#41;</span></span>](associate-wizard-data-mining-client-for-excel.md)  
  
## <a name="classify-data-mining"></a><span data-ttu-id="533d3-126">分类（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="533d3-126">Classify (Data Mining)</span></span>  
 <span data-ttu-id="533d3-127">**分类**向导生成一个分类模型，该模型分析提供给目标结果的因素。</span><span class="sxs-lookup"><span data-stu-id="533d3-127">The  **Classify** wizard builds a classification model that analyzes the factors that contributed to a target outcome.</span></span> <span data-ttu-id="533d3-128">您可以将多个算法用于此向导，包括决策树、Naïve Bayes 和神经网络。</span><span class="sxs-lookup"><span data-stu-id="533d3-128">You can use multiple algorithms with this wizard, including Decision Trees, Naïve Bayes, and Neural Networks.</span></span>  
  
 [<span data-ttu-id="533d3-129">用于 Excel 的数据挖掘外接程序 &#40;分类向导&#41;</span><span class="sxs-lookup"><span data-stu-id="533d3-129">Classify Wizard &#40;Data Mining Add-ins for Excel&#41;</span></span>](classify-wizard-data-mining-add-ins-for-excel.md)  
  
## <a name="cluster-data-mining"></a><span data-ttu-id="533d3-130">聚类分析（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="533d3-130">Cluster (Data Mining)</span></span>  
 <span data-ttu-id="533d3-131">**聚**类分析向导生成一个聚类分析模型，用于检测具有相似特征的行组。</span><span class="sxs-lookup"><span data-stu-id="533d3-131">The **Cluster** wizard builds a clustering model that detects groups of rows that share similar characteristics.</span></span> <span data-ttu-id="533d3-132">群集 (有时称为*分段*) 是一种无人监督的学习技术，在尝试理解新数据中的模式和分组时非常有用。</span><span class="sxs-lookup"><span data-stu-id="533d3-132">Clustering (sometimes called *segmentation*) is an unsupervised learning technique that is very useful when trying to understand patterns and groupings in new data.</span></span>  
  
 <span data-ttu-id="533d3-133">Microsoft 聚类分析算法支持 K-means 聚类分析和期望最大化 (EM) 聚类分析的若干变化形式。</span><span class="sxs-lookup"><span data-stu-id="533d3-133">The Microsoft Clustering algorithm supports several varieties of both K-means and Expectation maximization (EM) clustering</span></span>  
  
 <span data-ttu-id="533d3-134">[群集向导 &#40;Excel 的数据挖掘外接程序&#41;](cluster-wizard-data-mining-add-ins-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="533d3-134">[Cluster Wizard &#40;Data Mining Add-ins for Excel&#41;](cluster-wizard-data-mining-add-ins-for-excel.md).</span></span>  
  
## <a name="detect-categories-analyze"></a><span data-ttu-id="533d3-135">检测类别（分析）</span><span class="sxs-lookup"><span data-stu-id="533d3-135">Detect Categories (Analyze)</span></span>  
 <span data-ttu-id="533d3-136">使用 "**检测类别**" 工具，可以添加任何数据集，并可以应用群集来查找数据分组。</span><span class="sxs-lookup"><span data-stu-id="533d3-136">The **Detect Categories** tool lets you add any data set and apply clustering to find groupings of data.</span></span> <span data-ttu-id="533d3-137">这对于查找相似点以及创建组以进行进一步分析非常有用。</span><span class="sxs-lookup"><span data-stu-id="533d3-137">It's useful for finding similarities and for creating groups to further analyze.</span></span>  
  
 <span data-ttu-id="533d3-138">"**检测类别**" 工具使用 Microsoft 聚类分析算法。</span><span class="sxs-lookup"><span data-stu-id="533d3-138">The **Detect Categories** tool uses the Microsoft Clustering algorithm.</span></span>  
  
 [<span data-ttu-id="533d3-139">检测类别 &#40;Excel&#41;的表分析工具</span><span class="sxs-lookup"><span data-stu-id="533d3-139">Detect Categories &#40;Table Analysis Tools for Excel&#41;</span></span>](detect-categories-table-analysis-tools-for-excel.md)  
  
## <a name="estimate-data-mining"></a><span data-ttu-id="533d3-140">估计（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="533d3-140">Estimate (Data Mining)</span></span>  
 <span data-ttu-id="533d3-141">估计向导生成一个估计模型，它提取数据模式并使用这些模式来预测连续的数字、日期或时间值。</span><span class="sxs-lookup"><span data-stu-id="533d3-141">The Estimate wizard builds an estimation model that extracts data patterns and uses the patterns to predict continuous numeric, date, or time values.</span></span> <span data-ttu-id="533d3-142">它使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] 决策树算法。</span><span class="sxs-lookup"><span data-stu-id="533d3-142">It uses the [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees algorithm.</span></span>  
  
 [<span data-ttu-id="533d3-143">估计向导 &#40;Excel 数据挖掘外接程序&#41;</span><span class="sxs-lookup"><span data-stu-id="533d3-143">Estimate Wizard &#40;Data Mining Add-ins for Excel&#41;</span></span>](estimate-wizard-data-mining-add-ins-for-excel.md)  
  
## <a name="fill-from-example-analyze"></a><span data-ttu-id="533d3-144">从示例填充（分析）</span><span class="sxs-lookup"><span data-stu-id="533d3-144">Fill From Example (Analyze)</span></span>  
 <span data-ttu-id="533d3-145">"**从示例填充**" 工具可帮助您归结缺失值。</span><span class="sxs-lookup"><span data-stu-id="533d3-145">The **Fill From Example** tool helps you impute missing values.</span></span> <span data-ttu-id="533d3-146">您提供缺失值应该是什么的一些示例，该工具将基于表中的所有数据生成模式，然后基于数据中的模式建议新值。</span><span class="sxs-lookup"><span data-stu-id="533d3-146">You provide some examples of what the missing values should be, and the tool builds patterns based on all data in the table, and then recommends new values based on patterns in the data.</span></span>  
  
 <span data-ttu-id="533d3-147">"**从示例填充**" 工具使用 Microsoft 逻辑回归算法。</span><span class="sxs-lookup"><span data-stu-id="533d3-147">The **Fill From Example** tool uses the Microsoft Logistic Regression algorithm.</span></span>  
  
 [<span data-ttu-id="533d3-148">Excel&#41;&#40;的填充示例表分析工具</span><span class="sxs-lookup"><span data-stu-id="533d3-148">Fill From Example &#40;Table Analysis Tools for Excel&#41;</span></span>](fill-from-example-table-analysis-tools-for-excel.md)  
  
## <a name="forecast-analyze"></a><span data-ttu-id="533d3-149">预测（分析）</span><span class="sxs-lookup"><span data-stu-id="533d3-149">Forecast (Analyze)</span></span>  
 <span data-ttu-id="533d3-150">**预测**工具获取随时间变化的数据，并预测将来的值。</span><span class="sxs-lookup"><span data-stu-id="533d3-150">The **Forecast** tool takes data that changes over time, and predicts future values.</span></span>  
  
 <span data-ttu-id="533d3-151">**预测**工具使用 Microsoft 时序算法。</span><span class="sxs-lookup"><span data-stu-id="533d3-151">The **Forecast** tool uses the Microsoft Time Series algorithm.</span></span>  
  
 [<span data-ttu-id="533d3-152">用于 Excel&#41;的预测 &#40;表分析工具</span><span class="sxs-lookup"><span data-stu-id="533d3-152">Forecast &#40;Table Analysis Tools for Excel&#41;</span></span>](forecast-table-analysis-tools-for-excel.md)  
  
## <a name="forecast-data-mining"></a><span data-ttu-id="533d3-153">预测（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="533d3-153">Forecast (Data Mining)</span></span>  
 <span data-ttu-id="533d3-154">**预测**向导生成一个预测模型，该模型检测一系列单元中的模式，然后预测其他值。</span><span class="sxs-lookup"><span data-stu-id="533d3-154">The **Forecast** wizard builds a forecasting model that detects patterns in a series of cells, and then forecasts additional values.</span></span>  
  
 [<span data-ttu-id="533d3-155">预测向导 &#40;Excel 数据挖掘外接程序&#41;</span><span class="sxs-lookup"><span data-stu-id="533d3-155">Forecast Wizard &#40;Data Mining Add-ins for Excel&#41;</span></span>](forecast-wizard-data-mining-add-ins-for-excel.md)  
  
## <a name="highlight-exceptions-analyze"></a><span data-ttu-id="533d3-156">突出显示异常值（分析）</span><span class="sxs-lookup"><span data-stu-id="533d3-156">Highlight Exceptions (Analyze)</span></span>  
 <span data-ttu-id="533d3-157">**突出显示异常**值工具可分析数据表中的模式，并查找不适合该模式的行和值。</span><span class="sxs-lookup"><span data-stu-id="533d3-157">The **Highlight Exceptions** tool analyzes patterns in a table of data and finds rows and values that don't fit the pattern.</span></span> <span data-ttu-id="533d3-158">然后，您可以查看和更正它们并重新运行模型，或者对值进行标记以便以后执行操作。</span><span class="sxs-lookup"><span data-stu-id="533d3-158">You can then review and correct them and rerun the model, or flag values for later action.</span></span>  
  
 <span data-ttu-id="533d3-159">**突出显示异常**工具使用 Microsoft 聚类分析算法。</span><span class="sxs-lookup"><span data-stu-id="533d3-159">The **Highlight Exceptions** tool uses the Microsoft Clustering algorithm.</span></span>  
  
 [<span data-ttu-id="533d3-160">突出显示 Excel &#40;表分析工具的异常&#41;</span><span class="sxs-lookup"><span data-stu-id="533d3-160">Highlight Exceptions &#40;Table Analysis Tools for Excel&#41;</span></span>](highlight-exceptions-table-analysis-tools-for-excel.md)  
  
## <a name="prediction-calculator-analyze"></a><span data-ttu-id="533d3-161">预测计算器（分析）</span><span class="sxs-lookup"><span data-stu-id="533d3-161">Prediction Calculator (Analyze)</span></span>  
 <span data-ttu-id="533d3-162">该工具创建对导致目标结果的因素进行分析的模型，然后基于从这些模式导出的条件预测任何新输入的结果。它还生成一个交互式的决策工作表，使您可以轻松地对新输入评分。</span><span class="sxs-lookup"><span data-stu-id="533d3-162">This tool creates a model that analyzes the factors leading to target outcomes, and then predicts a result for any new input, based on criteria derived from these patterns It also generates an interactive decision making worksheet that lets you easily score new inputs.</span></span> <span data-ttu-id="533d3-163">您还可以创建评分工作表的打印版本，以供脱机使用。</span><span class="sxs-lookup"><span data-stu-id="533d3-163">You can also create a printed version of the scoring worksheet for offline use.</span></span>  
  
 <span data-ttu-id="533d3-164">**预测计算器**工具使用 Microsoft 逻辑回归算法。</span><span class="sxs-lookup"><span data-stu-id="533d3-164">The **Prediction Calculator** tool uses the Microsoft Logistic Regression algorithm.</span></span>  
  
 [<span data-ttu-id="533d3-165">用于 Excel&#41;的预测计算器 &#40;表分析工具</span><span class="sxs-lookup"><span data-stu-id="533d3-165">Prediction Calculator &#40;Table Analysis Tools for Excel&#41;</span></span>](prediction-calculator-table-analysis-tools-for-excel.md)  
  
## <a name="scenario-goal-seek-analyze"></a><span data-ttu-id="533d3-166">应用场景：目标查找（分析）</span><span class="sxs-lookup"><span data-stu-id="533d3-166">Scenario: Goal Seek (Analyze)</span></span>  
 <span data-ttu-id="533d3-167">在 "**目标查找**" 工具中，您可以指定一个目标值，该工具将标识为了满足目标而必须更改的基本因素。</span><span class="sxs-lookup"><span data-stu-id="533d3-167">In the **Goal Seek** tool, you specify a target value, and the tool identifies the underlying factors that must change to meet that target.</span></span> <span data-ttu-id="533d3-168">例如，如果您知道必须将电话满意度增加 20%，则可以要求模型预测应进行变化以便实现该目标的因素。</span><span class="sxs-lookup"><span data-stu-id="533d3-168">For example, if you know that you must increase call satisfaction by 20%, you can ask the model to predict the factors that should change to produce that goal.</span></span>  
  
 <span data-ttu-id="533d3-169">**目标查找**工具使用 Microsoft 逻辑回归算法。</span><span class="sxs-lookup"><span data-stu-id="533d3-169">The **Goal Seek** tool uses the Microsoft Logistic Regression algorithm.</span></span>  
  
 <span data-ttu-id="533d3-170">详细信息</span><span class="sxs-lookup"><span data-stu-id="533d3-170">details</span></span>  
  
 [<span data-ttu-id="533d3-171">用于 Excel&#41;&#40;表分析工具的目标查找方案</span><span class="sxs-lookup"><span data-stu-id="533d3-171">Goal Seek Scenario &#40;Table Analysis Tools for Excel&#41;</span></span>](goal-seek-scenario-table-analysis-tools-for-excel.md)  
  
## <a name="scenario-what-if-scenario-analyze"></a><span data-ttu-id="533d3-172">应用场景：“假设”应用场景（分析）</span><span class="sxs-lookup"><span data-stu-id="533d3-172">Scenario: What-If Scenario (Analyze)</span></span>  
 <span data-ttu-id="533d3-173">**假设分析工具是**对**目标查找**工具的补充。</span><span class="sxs-lookup"><span data-stu-id="533d3-173">The **What-If Analysis** tool complements the **Goal Seek** tool.</span></span> <span data-ttu-id="533d3-174">使用此工具，您输入要更改的值，并且模型将预测该更改是否足以实现预期结果。</span><span class="sxs-lookup"><span data-stu-id="533d3-174">With this tool, you entered the value you want to change, and the model predicts whether that change will be sufficient to achieve the desired outcome.</span></span> <span data-ttu-id="533d3-175">例如，您可以要求该模型推断再增加一名电话接线员是否可以将客户满意度增加一个百分点。</span><span class="sxs-lookup"><span data-stu-id="533d3-175">For example, you might ask the model to infer whether adding one extra call operator would increase customer satisfaction by one point.</span></span>  
  
 <span data-ttu-id="533d3-176">**假设**工具使用 Microsoft 逻辑回归算法。</span><span class="sxs-lookup"><span data-stu-id="533d3-176">The **What-If** tool uses the Microsoft Logistic Regression algorithm.</span></span>  
  
 [<span data-ttu-id="533d3-177">假设方案 &#40;Excel&#41;的表分析工具</span><span class="sxs-lookup"><span data-stu-id="533d3-177">What-If Scenario &#40;Table Analysis Tools for Excel&#41;</span></span>](what-if-scenario-table-analysis-tools-for-excel.md)  
  
## <a name="shopping-basket-analysis-analyze"></a><span data-ttu-id="533d3-178">购物篮分析（分析）</span><span class="sxs-lookup"><span data-stu-id="533d3-178">Shopping Basket Analysis (Analyze)</span></span>  
 <span data-ttu-id="533d3-179">**购物篮分析**工具可创建经常一起购买的产品组，以确定可用于交叉销售或向上销售的模式。</span><span class="sxs-lookup"><span data-stu-id="533d3-179">The **Shopping Basket Analysis** tool creates groups of products that are frequently purchased together, to identify patterns that can be used in cross-selling or up-selling.</span></span> <span data-ttu-id="533d3-180">它还基于相关产品捆绑的价格和成本生成报告，以便帮助进行决策。</span><span class="sxs-lookup"><span data-stu-id="533d3-180">It also generates reports based on the price and cost of related product bundles, to aid in decision-making.</span></span>  
  
 <span data-ttu-id="533d3-181">您还可以将该工具用于经常一起发生的事件、导致诊断的因素或者任何其他可能原因和结果组。</span><span class="sxs-lookup"><span data-stu-id="533d3-181">You can also use this tool for events that frequently occur together, factors leading to a diagnosis, or any other set of potential causes and outcomes.</span></span>  
  
 <span data-ttu-id="533d3-182">**购物篮分析**工具使用 Microsoft 关联算法。</span><span class="sxs-lookup"><span data-stu-id="533d3-182">The **Shopping Basket Analysis** tool uses the Microsoft Association algorithm.</span></span>  
  
 [<span data-ttu-id="533d3-183">用于 Excel&#41;&#40;表 AnalysisTools 的购物篮分析</span><span class="sxs-lookup"><span data-stu-id="533d3-183">Shopping Basket Analysis &#40;Table AnalysisTools for Excel&#41;</span></span>](shopping-basket-analysis-table-analysistools-for-excel.md)  
  
## <a name="see-also"></a><span data-ttu-id="533d3-184">另请参阅</span><span class="sxs-lookup"><span data-stu-id="533d3-184">See Also</span></span>  
 <span data-ttu-id="533d3-185">[浏览和清理数据](exploring-and-cleaning-data.md) </span><span class="sxs-lookup"><span data-stu-id="533d3-185">[Exploring and Cleaning Data](exploring-and-cleaning-data.md) </span></span>  
 <span data-ttu-id="533d3-186">[验证模型和使用模型进行预测 &#40;Excel 数据挖掘外接程序&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="533d3-186">[Validating Models and Using Models for Prediction &#40;Data Mining Add-ins for Excel&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md) </span></span>  
 [<span data-ttu-id="533d3-187">&#40;Excel 数据挖掘外接程序部署和缩放挖掘模型&#41;</span><span class="sxs-lookup"><span data-stu-id="533d3-187">Deploying and Scaling Mining Models &#40;Data Mining Add-ins for Excel&#41;</span></span>](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)  
  
  
