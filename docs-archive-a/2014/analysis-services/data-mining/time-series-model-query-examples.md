---
title: 时序模型查询示例 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- time series algorithms [Analysis Services]
- MISSING_VALUE_SUBSTITUTION
- time series [Analysis Services]
- predictions [Analysis Services], time series
- EXTEND_MODEL_CASES parameter
- REPLACE_MODEL_CASES parameter
- prediction queries [DMX]
- PREDICTION_SMOOTHING
- content queries [DMX]
ms.assetid: 9a1c527e-2997-493b-ad6a-aaa71260b018
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4f6b6ed2674d5f1d852b6281c6244af4f2f6ad3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590434"
---
# <a name="time-series-model-query-examples"></a><span data-ttu-id="a1b24-102">时序模型查询示例</span><span class="sxs-lookup"><span data-stu-id="a1b24-102">Time Series Model Query Examples</span></span>
  <span data-ttu-id="a1b24-103">在创建针对数据挖掘模型的查询时，您既可以创建内容查询，也可创建预测查询；内容查询提供有关分析过程中发现的模式的详细信息，而预测查询则使用模型中的模式来对新数据进行预测。</span><span class="sxs-lookup"><span data-stu-id="a1b24-103">When you create a query against a data mining model, you can create either a content query, which provides details about the patterns discovered in analysis, or you can create a prediction query, which uses the patterns in the model to make predictions for new data.</span></span> <span data-ttu-id="a1b24-104">例如，时序模型的内容查询可能提供有关检测到的周期性结构的其他详细信息，而预测查询可能给出接下来 5-10 个时间段的预测。</span><span class="sxs-lookup"><span data-stu-id="a1b24-104">For example, a content query for a time series model might provide additional details about the periodic structures that were detected, while a prediction query might give you predictions for the next 5-10 time slices.</span></span> <span data-ttu-id="a1b24-105">您还可以使用查询来检索有关模型的元数据。</span><span class="sxs-lookup"><span data-stu-id="a1b24-105">You can also retrieve metadata about the model by using a query.</span></span>  
  
 <span data-ttu-id="a1b24-106">本节介绍如何为基于 Microsoft 时序算法的模型创建这两种查询。</span><span class="sxs-lookup"><span data-stu-id="a1b24-106">This section explains how to create both kinds of queries for models that are based on the Microsoft Time Series algorithm.</span></span>  
  
 <span data-ttu-id="a1b24-107">**内容查询**</span><span class="sxs-lookup"><span data-stu-id="a1b24-107">**Content Queries**</span></span>  
  
 [<span data-ttu-id="a1b24-108">检索模型的周期提示</span><span class="sxs-lookup"><span data-stu-id="a1b24-108">Retrieving Periodicity Hints for the Model</span></span>](#bkmk_Query1)  
  
 [<span data-ttu-id="a1b24-109">检索 ARIMA 模型的公式</span><span class="sxs-lookup"><span data-stu-id="a1b24-109">Retrieving the Equation for an ARIMA Model</span></span>](#bkmk_Query2)  
  
 [<span data-ttu-id="a1b24-110">检索 ARTxp 模型的公式</span><span class="sxs-lookup"><span data-stu-id="a1b24-110">Retrieving the Equation for an ARTxp Model</span></span>](#bkmk_Query3)  
  
 <span data-ttu-id="a1b24-111">**预测查询**</span><span class="sxs-lookup"><span data-stu-id="a1b24-111">**Prediction Queries**</span></span>  
  
 [<span data-ttu-id="a1b24-112">了解何时替换和扩展时序数据</span><span class="sxs-lookup"><span data-stu-id="a1b24-112">Understanding When to Replace and When to Extend Time Series Data</span></span>](#bkmk_ReplaceExtend)  
  
 [<span data-ttu-id="a1b24-113">EXTEND_MODEL_CASES 进行预测</span><span class="sxs-lookup"><span data-stu-id="a1b24-113">Making Predictions with EXTEND_MODEL_CASES</span></span>](#bkmk_EXTEND)  
  
 [<span data-ttu-id="a1b24-114">REPLACE_MODEL_CASES 进行预测</span><span class="sxs-lookup"><span data-stu-id="a1b24-114">Making Predictions with REPLACE_MODEL_CASES</span></span>](#bkmk_REPLACE)  
  
 [<span data-ttu-id="a1b24-115">时序模型中的缺失值替代</span><span class="sxs-lookup"><span data-stu-id="a1b24-115">Missing Value Substitution in Time Series Models</span></span>](#bkmk_MissingValues)  
  
## <a name="getting-information-about-a-time-series-model"></a><span data-ttu-id="a1b24-116">获取有关时序模型的信息</span><span class="sxs-lookup"><span data-stu-id="a1b24-116">Getting Information about a Time Series Model</span></span>  
 <span data-ttu-id="a1b24-117">模型内容查询可以提供有关模型的基本信息，例如创建模型时使用的参数、上次处理模型的时间。</span><span class="sxs-lookup"><span data-stu-id="a1b24-117">A model content query can provide basic information about the model, such as the parameters that were used when the model was created, the time the model was last processed.</span></span> <span data-ttu-id="a1b24-118">以下示例说明了使用数据挖掘架构行集查询模型内容的基本语法。</span><span class="sxs-lookup"><span data-stu-id="a1b24-118">The following example illustrates the basic syntax for querying the model content by using the data mining schema rowsets.</span></span>  
  
###  <a name="sample-query-1-retrieving-periodicity-hints-for-the-model"></a><a name="bkmk_Query1"></a> <span data-ttu-id="a1b24-119">示例查询 1：检索模型的周期提示</span><span class="sxs-lookup"><span data-stu-id="a1b24-119">Sample Query 1: Retrieving Periodicity Hints for the Model</span></span>  
 <span data-ttu-id="a1b24-120">可通过查询 ARIMA 树或 ARTXP 树检索在时序内找到的周期。</span><span class="sxs-lookup"><span data-stu-id="a1b24-120">You can retrieve the periodicities that were found within the time series by querying the ARIMA tree or the ARTXP tree.</span></span> <span data-ttu-id="a1b24-121">但是，已完成的模型中的周期可能与创建模型时指定为提示的周期不同。</span><span class="sxs-lookup"><span data-stu-id="a1b24-121">However, the periodicities in the completed model might not be the same as the periods that you specified as hints when you created the model.</span></span> <span data-ttu-id="a1b24-122">若要检索创建模型时作为参数提供的提示，可以使用以下 DMX 语句来查询挖掘模型内容架构行集：</span><span class="sxs-lookup"><span data-stu-id="a1b24-122">To retrieve the hints that were supplied as parameters when you created the model, you can query the mining model content schema rowset by using the following DMX statement:</span></span>  
  
```  
SELECT MINING_PARAMETERS   
FROM $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = '<model name>'  
```  
  
 <span data-ttu-id="a1b24-123">部分结果：</span><span class="sxs-lookup"><span data-stu-id="a1b24-123">Partial results:</span></span>  
  
|<span data-ttu-id="a1b24-124">MINING_PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a1b24-124">MINING_PARAMETERS</span></span>|  
|------------------------|  
|<span data-ttu-id="a1b24-125">COMPLEXITY_PENALTY = 0.1，MINIMUM_SUPPORT = 10，PERIODICITY_HINT = {1,3} ,..。。</span><span class="sxs-lookup"><span data-stu-id="a1b24-125">COMPLEXITY_PENALTY=0.1,MINIMUM_SUPPORT=10,PERIODICITY_HINT={1,3},....</span></span>|  
  
 <span data-ttu-id="a1b24-126">默认周期提示为 {1}，将出现在所有模型中；此示例模型是使用可能不在最终模型中出现的附加提示创建的。</span><span class="sxs-lookup"><span data-stu-id="a1b24-126">The default periodicity hint is {1} and appears in all models; this sample model was created with an additional hint that might not be present in the final model.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a1b24-127">此处已将结果截断以提高可读性。</span><span class="sxs-lookup"><span data-stu-id="a1b24-127">The results have been truncated here for readability.</span></span>  
  
###  <a name="sample-query-2-retrieving-the-equation-for-an-arima-model"></a><a name="bkmk_Query2"></a> <span data-ttu-id="a1b24-128">示例查询 2：检索 ARIMA 模型的公式</span><span class="sxs-lookup"><span data-stu-id="a1b24-128">Sample Query 2: Retrieving the Equation for an ARIMA Model</span></span>  
 <span data-ttu-id="a1b24-129">通过查询单个树中的任何节点，可以检索 ARIMA 模型的公式。</span><span class="sxs-lookup"><span data-stu-id="a1b24-129">You can retrieve the equation for an ARIMA model by querying any node in an individual tree.</span></span> <span data-ttu-id="a1b24-130">请记住，ARIMA 模型中的每个树都表示不同的周期，如果有多个数据序列，则每个数据序列都将有自己的周期树集。</span><span class="sxs-lookup"><span data-stu-id="a1b24-130">Remember that each tree within an ARIMA model represents a different periodicity, and if there are multiple data series, each data series will have its own set of periodicity trees.</span></span> <span data-ttu-id="a1b24-131">因此，若要检索特定数据序列的公式，必须先标识树。</span><span class="sxs-lookup"><span data-stu-id="a1b24-131">Therefore, to retrieve the equation for a specific data series you must identify the tree first.</span></span>  
  
 <span data-ttu-id="a1b24-132">例如，TA 前缀表示该节点是 ARIMA 树的一部分，而 TS 前缀用于 ARTXP 树。</span><span class="sxs-lookup"><span data-stu-id="a1b24-132">For example, the TA prefix tells you that the node is part of an ARIMA tree, whereas the TS prefix is used for ARTXP trees.</span></span> <span data-ttu-id="a1b24-133">通过查询 NODE_TYPE 值为 27 的节点的模型内容可以找到所有的 ARIMA 根树。</span><span class="sxs-lookup"><span data-stu-id="a1b24-133">You can find all ARIMA root trees by querying the model content for nodes with a NODE_TYPE value of 27.</span></span> <span data-ttu-id="a1b24-134">也可以使用 ATTRIBUTE_NAME 值查找特定数据序列的 ARIMA 根节点。</span><span class="sxs-lookup"><span data-stu-id="a1b24-134">You can also use the value of ATTRIBUTE_NAME to find the ARIMA root node for a particular data series.</span></span> <span data-ttu-id="a1b24-135">该查询示例查找表示 R250 型号在 Europe 地区销售数量的 ARIMA 节点。</span><span class="sxs-lookup"><span data-stu-id="a1b24-135">This query example finds the ARIMA nodes that represent quantities sold of the R250 model in the Europe region.</span></span>  
  
```  
SELECT NODE_UNIQUE_NAME  
FROM Forecasting.CONTENT  
WHERE ATTRIBUTE_NAME = 'R250 Europe: Quantity"  
AND NODE_TYPE = 27  
```  
  
 <span data-ttu-id="a1b24-136">通过使用该节点 ID，可以检索有关该树的 ARIMA 公式的详细信息。</span><span class="sxs-lookup"><span data-stu-id="a1b24-136">By using this node ID, you can retrieve details about the ARIMA equation for this tree.</span></span> <span data-ttu-id="a1b24-137">下面的 DMX 语句检索该数据序列的 ARIMA 公式的缩写形式。</span><span class="sxs-lookup"><span data-stu-id="a1b24-137">The following DMX statement retrieves the short form of the ARIMA equation for the data series.</span></span> <span data-ttu-id="a1b24-138">该语句还从嵌套表 NODE_DISTRIBUTION 中检索截获。</span><span class="sxs-lookup"><span data-stu-id="a1b24-138">It also retrieves the intercept from the nested table, NODE_DISTRIBUTION.</span></span> <span data-ttu-id="a1b24-139">在此示例中，通过引用该节点的唯一 ID TA00000007 获取公式。</span><span class="sxs-lookup"><span data-stu-id="a1b24-139">In this example, the equation is obtained by referencing the node unique ID TA00000007.</span></span> <span data-ttu-id="a1b24-140">但是，您需要使用不同的节点 ID，这样您可能会从模型中获得稍有不同的结果。</span><span class="sxs-lookup"><span data-stu-id="a1b24-140">However, you may have to use a different node ID, and you may obtain slightly different results from your model.</span></span>  
  
```  
SELECT FLATTENED NODE_CAPTION as [Short equation],   
(SELECT ATTRIBUTE_NAME, ATTRIBUTE_VALUE   
FROM NODE_DISTRIBUTION) as t  
FROM Forecasting.CONTENT  
WHERE NODE_NAME = 'TA00000007'  
```  
  
 <span data-ttu-id="a1b24-141">示例结果：</span><span class="sxs-lookup"><span data-stu-id="a1b24-141">Example results:</span></span>  
  
|<span data-ttu-id="a1b24-142">短公式</span><span class="sxs-lookup"><span data-stu-id="a1b24-142">Short equation</span></span>|<span data-ttu-id="a1b24-143">T.ATTRIBUTE_NAME</span><span class="sxs-lookup"><span data-stu-id="a1b24-143">t.ATTRIBUTE_NAME</span></span>|<span data-ttu-id="a1b24-144">t.ATTRIBUTE_VALUE</span><span class="sxs-lookup"><span data-stu-id="a1b24-144">t.ATTRIBUTE_VALUE</span></span>|  
|--------------------|-----------------------|------------------------|  
|<span data-ttu-id="a1b24-145">ARIMA (2,0,7)x(1,0,2)(12)</span><span class="sxs-lookup"><span data-stu-id="a1b24-145">ARIMA (2,0,7)x(1,0,2)(12)</span></span>|<span data-ttu-id="a1b24-146">R250 Europe:Quantity(Intercept)</span><span class="sxs-lookup"><span data-stu-id="a1b24-146">R250 Europe:Quantity(Intercept)</span></span>|<span data-ttu-id="a1b24-147">15.24 ...。</span><span class="sxs-lookup"><span data-stu-id="a1b24-147">15.24....</span></span>|  
|<span data-ttu-id="a1b24-148">ARIMA (2,0,7)x(1,0,2)(12)</span><span class="sxs-lookup"><span data-stu-id="a1b24-148">ARIMA (2,0,7)x(1,0,2)(12)</span></span>|<span data-ttu-id="a1b24-149">R250 Europe:Quantity(Periodicity)</span><span class="sxs-lookup"><span data-stu-id="a1b24-149">R250 Europe:Quantity(Periodicity)</span></span>|<span data-ttu-id="a1b24-150">1</span><span class="sxs-lookup"><span data-stu-id="a1b24-150">1</span></span>|  
|<span data-ttu-id="a1b24-151">ARIMA (2,0,7)x(1,0,2)(12)</span><span class="sxs-lookup"><span data-stu-id="a1b24-151">ARIMA (2,0,7)x(1,0,2)(12)</span></span>|<span data-ttu-id="a1b24-152">R250 Europe:Quantity(Periodicity)</span><span class="sxs-lookup"><span data-stu-id="a1b24-152">R250 Europe:Quantity(Periodicity)</span></span>|<span data-ttu-id="a1b24-153">12</span><span class="sxs-lookup"><span data-stu-id="a1b24-153">12</span></span>|  
  
 <span data-ttu-id="a1b24-154">有关如何解释此信息的详细信息，请参阅 [时序模型的挖掘模型内容（Analysis Services - 数据挖掘）](mining-model-content-for-time-series-models-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="a1b24-154">For more information about how to interpret this information, see [Mining Model Content for Time Series Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-time-series-models-analysis-services-data-mining.md).</span></span>  
  
###  <a name="sample-query-3-retrieving-the-equation-for-an-artxp-model"></a><a name="bkmk_Query3"></a> <span data-ttu-id="a1b24-155">示例查询 3：检索 ARTXP 模型的公式</span><span class="sxs-lookup"><span data-stu-id="a1b24-155">Sample Query 3: Retrieving the Equation for an ARTXP Model</span></span>  
 <span data-ttu-id="a1b24-156">对于 ARTxp 模型，将在树的每个级别存储不同的信息。</span><span class="sxs-lookup"><span data-stu-id="a1b24-156">For an ARTxp model, different information is stored at each level of the tree.</span></span> <span data-ttu-id="a1b24-157">有关 ARTxp 模型的结构，以及如何解释公式中的信息的详细信息，请参阅 [时序模型的挖掘模型内容（Analysis Services - 数据挖掘）](mining-model-content-for-time-series-models-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="a1b24-157">For more information about the structure of an ARTxp model, and how to interpret the information in the equation, see [Mining Model Content for Time Series Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-time-series-models-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="a1b24-158">下面的 DMX 语句检索部分 ARTxp 树的信息，表示 R250 型号在 Europe 的销售数量。</span><span class="sxs-lookup"><span data-stu-id="a1b24-158">The following DMX statement retrieves information a part of the ARTxp tree that represents the quantity of sales for the R250 model in Europe.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a1b24-159">必须将嵌套表列的名称 VARIANCE 括在括号中，以便将它与同名的保留关键字区分开来。</span><span class="sxs-lookup"><span data-stu-id="a1b24-159">The name of the nested table column, VARIANCE, must be enclosed in brackets to distinguish it from the reserved keyword of the same name.</span></span> <span data-ttu-id="a1b24-160">由于嵌套表列 PROBABILITY 和 SUPPORT 在大多数情况下为空，因此这两列不包括在内。</span><span class="sxs-lookup"><span data-stu-id="a1b24-160">The nested table columns, PROBABILITY and SUPPORT, are not included because they are blank in most cases.</span></span>  
  
```  
SELECT NODE_CAPTION as [Split information],   
(SELECT ATTRIBUTE_NAME, ATTRIBUTE_VALUE,  
   [VARIANCE]  
   FROM NODE_DISTRIBUTION) AS t  
FROM Forecasting.CONTENT  
WHERE NODE_ATTRIBUTE_NAME = 'R250 Europe:Quantity'  
AND NODE_TYPE = 15  
```  
  
 <span data-ttu-id="a1b24-161">有关如何解释此信息的详细信息，请参阅 [时序模型的挖掘模型内容（Analysis Services - 数据挖掘）](mining-model-content-for-time-series-models-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="a1b24-161">For more information about how to interpret this information, see [Mining Model Content for Time Series Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-time-series-models-analysis-services-data-mining.md).</span></span>  
  
## <a name="creating-predictions-on-a-time-series-model"></a><span data-ttu-id="a1b24-162">创建针对时序模型的预测</span><span class="sxs-lookup"><span data-stu-id="a1b24-162">Creating Predictions on a Time Series Model</span></span>  
 <span data-ttu-id="a1b24-163">从 [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)]开始，可以在时序模型中添加新数据并自动将新数据合并到模型中。</span><span class="sxs-lookup"><span data-stu-id="a1b24-163">Beginning in [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)], you can add new data to a time series model and automatically incorporate the new data into the model.</span></span> <span data-ttu-id="a1b24-164">您可以通过下列两种方式之一向时序挖掘模型添加新数据：</span><span class="sxs-lookup"><span data-stu-id="a1b24-164">You add new data to a time series mining model in one of two ways:</span></span>  
  
-   <span data-ttu-id="a1b24-165">使用 `PREDICTION JOIN` 将外部源中的数据联接到定型数据。</span><span class="sxs-lookup"><span data-stu-id="a1b24-165">Use a `PREDICTION JOIN` to join data in an external source to the training data.</span></span>  
  
-   <span data-ttu-id="a1b24-166">使用单独预测查询每次向数据提供一个切片。</span><span class="sxs-lookup"><span data-stu-id="a1b24-166">Use a singleton prediction query to provide data one slice at a time.</span></span> <span data-ttu-id="a1b24-167">有关如何创建单独预测查询的信息，请参阅[数据挖掘查询接口](data-mining-query-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="a1b24-167">For information about how to create a singleton prediction query, see [Data Mining Query Interfaces](data-mining-query-tools.md).</span></span>  
  
###  <a name="understanding-the-behavior-of-replace-and-extend-operations"></a><a name="bkmk_ReplaceExtend"></a> <span data-ttu-id="a1b24-168">理解替换和扩展操作的行为</span><span class="sxs-lookup"><span data-stu-id="a1b24-168">Understanding the Behavior of Replace and Extend Operations</span></span>  
 <span data-ttu-id="a1b24-169">在时序模型中添加新数据时，可以指定是否扩展或替换定型数据：</span><span class="sxs-lookup"><span data-stu-id="a1b24-169">When you add new data to a time series model, you can specify whether to extend or replace the training data:</span></span>  
  
-   <span data-ttu-id="a1b24-170">**扩展：** 在您扩展某一数据序列时， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 将在现有定型数据的末尾添加新数据。</span><span class="sxs-lookup"><span data-stu-id="a1b24-170">**Extend:** When you extend a data series, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] adds the new data at the end of the existing training data.</span></span> <span data-ttu-id="a1b24-171">定型事例的数量也会增加。</span><span class="sxs-lookup"><span data-stu-id="a1b24-171">The number of training cases also increases.</span></span>  
  
     <span data-ttu-id="a1b24-172">扩展模型事例对于使用新数据持续更新模型很有用。</span><span class="sxs-lookup"><span data-stu-id="a1b24-172">Extending the model cases is useful for continuously updating the model with new data.</span></span> <span data-ttu-id="a1b24-173">例如，如果要使定型集随时间增长，则只需扩展该模型。</span><span class="sxs-lookup"><span data-stu-id="a1b24-173">For example, if you want to make the training set grow over time, you would simply extend the model.</span></span>  
  
     <span data-ttu-id="a1b24-174">若要扩展数据，请在时序模型上创建一个 `PREDICTION JOIN`，指定新数据源，然后使用 `EXTEND_MODEL_CASES` 参数。</span><span class="sxs-lookup"><span data-stu-id="a1b24-174">To extend the data, you create a `PREDICTION JOIN` on a time series model, specify the source of the new data, and use the `EXTEND_MODEL_CASES` argument.</span></span>  
  
-   <span data-ttu-id="a1b24-175">**替换：** 当您在数据系列中替换数据时， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 将保留定型模型，但使用新数据值替换全部或部分现有定型事例。</span><span class="sxs-lookup"><span data-stu-id="a1b24-175">**Replace:** When you replace the data in the data series, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] keeps the trained model, but uses the new data values to replace some or all of the existing training cases.</span></span> <span data-ttu-id="a1b24-176">因此，定型数据的大小永远不会发生变化，但事例本身却可以使用更新的数据不断进行替换。</span><span class="sxs-lookup"><span data-stu-id="a1b24-176">Therefore, the size of the training data never changes, but the cases themselves are continually being replaced with newer data.</span></span> <span data-ttu-id="a1b24-177">如果您提供了足够的新数据，则可以使用全新的序列替换定型数据。</span><span class="sxs-lookup"><span data-stu-id="a1b24-177">If you supply enough new data, you can replace the training data with a completely new series.</span></span>  
  
     <span data-ttu-id="a1b24-178">如果您想对一组事例的某个模型定型，然后将该模型应用到不同的数据序列，则替换模型事例非常有用。</span><span class="sxs-lookup"><span data-stu-id="a1b24-178">Replacing the model cases is useful when you want to train a model on one set of cases and then apply that model to a different data series.</span></span>  
  
     <span data-ttu-id="a1b24-179">若要替换数据，可以在时序模型上创建一个 `PREDICTION JOIN`，指定新数据源，然后使用 `REPLACE_MODEL_CASES` 参数。</span><span class="sxs-lookup"><span data-stu-id="a1b24-179">To replace the data, you create a `PREDICTION JOIN` on a time series model, specify the source of the new data, and use the `REPLACE_MODEL_CASES` argument.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a1b24-180">添加新数据时不能进行历史预测。</span><span class="sxs-lookup"><span data-stu-id="a1b24-180">You cannot make historical predictions when you add new data.</span></span>  
  
 <span data-ttu-id="a1b24-181">无论是扩展还是替换定型数据，始终在结束原始定型集的时间戳处开始预测。</span><span class="sxs-lookup"><span data-stu-id="a1b24-181">Regardless of whether you extend or replace the training data, predictions always begin at the time stamp that ends the original training set.</span></span> <span data-ttu-id="a1b24-182">换言之，如果新数据包含 n 个时间段，并且请求对时间步长 1 至 n 进行预测，则预测将与新数据的时间段一致，并且不会获取任何新的预测。</span><span class="sxs-lookup"><span data-stu-id="a1b24-182">In other words, if your new data contains n time slices, and you request predictions for time steps 1 through n, the predictions will coincide with the same period as the new data, and you will not get any new predictions.</span></span>  
  
 <span data-ttu-id="a1b24-183">若要获取对不与新数据重叠的时间段的新预测，必须从新数据序列之后的时间段 n+1 处开始预测，或者确保请求了其他的时间段。</span><span class="sxs-lookup"><span data-stu-id="a1b24-183">To get new predictions for time periods that do not overlap with the new data, you must either start predictions at the time slice n+1, or make sure that you request additional time slices.</span></span>  
  
 <span data-ttu-id="a1b24-184">例如，假定现有模型具有六个月积累的数据。</span><span class="sxs-lookup"><span data-stu-id="a1b24-184">For example, assume that the existing model has six months' worth of data.</span></span> <span data-ttu-id="a1b24-185">您想通过添加最近三个月的销售数字来扩展该模型。</span><span class="sxs-lookup"><span data-stu-id="a1b24-185">You want to extend this model by adding the sales figures from the last three months.</span></span> <span data-ttu-id="a1b24-186">同时，您还想对接下来三个月进行预测。</span><span class="sxs-lookup"><span data-stu-id="a1b24-186">At the same time, you want to make a prediction about the next three months.</span></span> <span data-ttu-id="a1b24-187">添加新数据时如果只想获得新的预测，则将起点指定为时间段 4，将终点指定为时间段 7。</span><span class="sxs-lookup"><span data-stu-id="a1b24-187">To obtain only the new predictions when you add the new data, specify the starting point as time slice 4, and the ending point as time slice 7.</span></span> <span data-ttu-id="a1b24-188">您可能还要请求全部六个预测，但是，前三个预测的时间段会与刚添加的新数据重叠。</span><span class="sxs-lookup"><span data-stu-id="a1b24-188">You could also request a total of six predictions, but the time slices for the first three would overlap with the new data just added.</span></span>  
  
 <span data-ttu-id="a1b24-189">有关使用和的语法的查询示例和详细信息 `REPLACE_MODEL_CASES` `EXTEND_MODEL_CASES` ，请参阅[PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx)。</span><span class="sxs-lookup"><span data-stu-id="a1b24-189">For query examples and more information about the syntax for using `REPLACE_MODEL_CASES` and `EXTEND_MODEL_CASES`, see [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx).</span></span>  
  
###  <a name="making-predictions-with-extend_model_cases"></a><a name="bkmk_EXTEND"></a> <span data-ttu-id="a1b24-190">使用 EXTEND_MODEL_CASES 进行预测</span><span class="sxs-lookup"><span data-stu-id="a1b24-190">Making Predictions with EXTEND_MODEL_CASES</span></span>  
 <span data-ttu-id="a1b24-191">根据您是要扩展还是替换模型事例，预测行为会有所不同。</span><span class="sxs-lookup"><span data-stu-id="a1b24-191">Prediction behavior differs depending on whether you extend or replace the model cases.</span></span> <span data-ttu-id="a1b24-192">如果要扩展模型，新数据会附加到序列的末尾，并且定型集的大小会增加。</span><span class="sxs-lookup"><span data-stu-id="a1b24-192">When you extend a model, the new data is attached to the end of the series and the size of the training set increases.</span></span> <span data-ttu-id="a1b24-193">但是，用于预测查询的时间段始终从原始序列的末尾开始。</span><span class="sxs-lookup"><span data-stu-id="a1b24-193">However, the time slices used for prediction queries always start at the end of the original series.</span></span> <span data-ttu-id="a1b24-194">因此，如果您要添加三个新数据点并请求六个预测，返回的前三个预测将会与新数据重叠。</span><span class="sxs-lookup"><span data-stu-id="a1b24-194">Therefore, if you add three new data points and request six predictions, the first three predictions returned overlap with the new data.</span></span> <span data-ttu-id="a1b24-195">在这种情况下， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 会返回实际的新数据点，而不是进行预测，直到所有新数据点用完为止。</span><span class="sxs-lookup"><span data-stu-id="a1b24-195">In this case, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] returns the actual new data points instead of making a prediction, until all the new data points are used up.</span></span> <span data-ttu-id="a1b24-196">然后， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 会根据组合序列进行预测。</span><span class="sxs-lookup"><span data-stu-id="a1b24-196">Then, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] makes predictions based on the composite series.</span></span>  
  
 <span data-ttu-id="a1b24-197">通过这种行为，您可以添加新数据，然后在预测图表中显示实际的销售数字，而不是查看预测。</span><span class="sxs-lookup"><span data-stu-id="a1b24-197">This behavior lets you add new data, and then show your actual sales figures in the prediction chart, instead of seeing projections.</span></span>  
  
 <span data-ttu-id="a1b24-198">例如，若要添加三个新数据点并进行三个新预测，您需要执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="a1b24-198">For example, to add three new data points and make three new predictions, you would do the following:</span></span>  
  
-   <span data-ttu-id="a1b24-199">在时序模型上创建一个 `PREDICTION JOIN`，然后指定三个月新数据的来源。</span><span class="sxs-lookup"><span data-stu-id="a1b24-199">Create a `PREDICTION JOIN` on a time series model, and specify the source of three months' of new data.</span></span>  
  
-   <span data-ttu-id="a1b24-200">请求六个时间段的预测。</span><span class="sxs-lookup"><span data-stu-id="a1b24-200">Request predictions for six time slices.</span></span> <span data-ttu-id="a1b24-201">为此，请指定 6 个时间段，其中，起点为时间段 1，终点为时间段 7。</span><span class="sxs-lookup"><span data-stu-id="a1b24-201">To do this, specify 6 time slices, where the starting point is time slice 1, and the ending point is time slice 7.</span></span> <span data-ttu-id="a1b24-202">这仅适用于 EXTEND_MODEL_CASES。</span><span class="sxs-lookup"><span data-stu-id="a1b24-202">This is true only for EXTEND_MODEL_CASES.</span></span>  
  
-   <span data-ttu-id="a1b24-203">若要仅获取新预测，请将起点指定为 4，终点指定为 7。</span><span class="sxs-lookup"><span data-stu-id="a1b24-203">To get only the new predictions, you specify the starting point as 4 and the ending point as 7.</span></span>  
  
-   <span data-ttu-id="a1b24-204">您必须使用参数 `EXTEND_MODEL_CASES`。</span><span class="sxs-lookup"><span data-stu-id="a1b24-204">You must use the argument `EXTEND_MODEL_CASES`.</span></span>  
  
     <span data-ttu-id="a1b24-205">将返回前三个时间段的实际销售数字，并返回接下来三个时间段的基于扩展模型的预测。</span><span class="sxs-lookup"><span data-stu-id="a1b24-205">The actual sales figures are returned for the first three time slices, and predictions based on the extended model are returned for the next three time slices.</span></span>  
  
###  <a name="making-predictions-with-replace_model_cases"></a><a name="bkmk_REPLACE"></a> <span data-ttu-id="a1b24-206">使用 REPLACE_MODEL_CASES 进行预测</span><span class="sxs-lookup"><span data-stu-id="a1b24-206">Making Predictions with REPLACE_MODEL_CASES</span></span>  
 <span data-ttu-id="a1b24-207">在替换模型中的事例时，模型的大小将保持不变，但是 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 将替换模型中的各个事例。</span><span class="sxs-lookup"><span data-stu-id="a1b24-207">When you replace the cases in a model, the size of the model stays the same but [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] replaces the individual cases in the model.</span></span> <span data-ttu-id="a1b24-208">这对于交叉预测以及需要让定型数据集的大小保持一致的情形很有用。</span><span class="sxs-lookup"><span data-stu-id="a1b24-208">This is useful for cross-prediction and scenarios in which maintaining the training data set at a consistent size is important.</span></span>  
  
 <span data-ttu-id="a1b24-209">例如，您的一个商店的销售数据不足。</span><span class="sxs-lookup"><span data-stu-id="a1b24-209">For example, one of your stores has insufficient sales data.</span></span> <span data-ttu-id="a1b24-210">您可以对位于特定地区的所有商店的销售量计算平均值，然后定型一个模型，以此来创建一个常规模型。</span><span class="sxs-lookup"><span data-stu-id="a1b24-210">You could create a general model by averaging sales for all stores in a particular region and then training a model.</span></span> <span data-ttu-id="a1b24-211">然后，为了对销售数据不足的商店进行预测，可以仅为该商店创建一个有关新销售数据的 `PREDICTION JOIN`。</span><span class="sxs-lookup"><span data-stu-id="a1b24-211">Then, to make predictions for the store without sufficient sales data, you create a `PREDICTION JOIN` on the new sales data for just that store.</span></span> <span data-ttu-id="a1b24-212">在进行此操作时， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 会保留从地区模型中派生的模式，而使用各个商店的数据替换现有的定型事例。</span><span class="sxs-lookup"><span data-stu-id="a1b24-212">When you do this, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] keeps the patterns derived from the regional model, but replaces the existing training cases with the data from the individual store.</span></span> <span data-ttu-id="a1b24-213">最后，您的预测值将更为接近各个商店的趋势线。</span><span class="sxs-lookup"><span data-stu-id="a1b24-213">As a result, your prediction values will be closer to the trend lines for the individual store.</span></span>  
  
 <span data-ttu-id="a1b24-214">使用 `REPLACE_MODEL_CASES` 参数时，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 会连续将新事例添加到事例集的末尾，并从事例集的开头删除相应数量的事例。</span><span class="sxs-lookup"><span data-stu-id="a1b24-214">When you use the `REPLACE_MODEL_CASES` argument, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] continually adds new cases to the end of the case set and deletes a corresponding number from the beginning of the case set.</span></span> <span data-ttu-id="a1b24-215">如果您要添加的新数据比原始定型集中的数据多， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 将丢弃最早的数据。</span><span class="sxs-lookup"><span data-stu-id="a1b24-215">If you add more new data than was in the original training set, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] discards the earliest data.</span></span> <span data-ttu-id="a1b24-216">如果您提供了足够的新值，则预测可以基于全新的数据。</span><span class="sxs-lookup"><span data-stu-id="a1b24-216">If you supply sufficient new values, the predictions can be based on completely new data.</span></span>  
  
 <span data-ttu-id="a1b24-217">例如，假如您已经对包含 1000 行的事例数据集定型了自己的模型。</span><span class="sxs-lookup"><span data-stu-id="a1b24-217">For example, you trained your model on a case data set that contained 1000 rows.</span></span> <span data-ttu-id="a1b24-218">然后您添加了 100 行新数据。</span><span class="sxs-lookup"><span data-stu-id="a1b24-218">You then add 100 rows of new data.</span></span> [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="a1b24-219">会从定型集中删除前 100 行，并向该定型集的末尾添加 100 行新数据，总和仍然是 1000 行。</span><span class="sxs-lookup"><span data-stu-id="a1b24-219">drops the first 100 rows from the training set and adds the 100 rows of new data to the end of the set for a total of 1000 rows.</span></span> <span data-ttu-id="a1b24-220">如果您添加了 1100 行新数据，则只使用最新的 1000 行。</span><span class="sxs-lookup"><span data-stu-id="a1b24-220">If you add 1100 rows of new data, only the most recent 1000 rows are used.</span></span>  
  
 <span data-ttu-id="a1b24-221">以下是另一个示例。</span><span class="sxs-lookup"><span data-stu-id="a1b24-221">Here is another example.</span></span> <span data-ttu-id="a1b24-222">若要添加新的三个月积累的数据并进行三个新预测，您需要执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="a1b24-222">To add three new month's worth of data and make three new predictions, you would do the following actions:</span></span>  
  
-   <span data-ttu-id="a1b24-223">在时序模型上创建 `PREDICTION JOIN`，并使用 `REPLACE_MODEL_CASE` 参数。</span><span class="sxs-lookup"><span data-stu-id="a1b24-223">Create a `PREDICTION JOIN` on a time series model and use the `REPLACE_MODEL_CASE` argument.</span></span>  
  
-   <span data-ttu-id="a1b24-224">指定三个月新数据的来源。</span><span class="sxs-lookup"><span data-stu-id="a1b24-224">Specify the source of three months' of new data.</span></span> <span data-ttu-id="a1b24-225">该数据可能来自与原始定型数据完全不同的来源。</span><span class="sxs-lookup"><span data-stu-id="a1b24-225">This data might be from a completely different source than the original training data.</span></span>  
  
-   <span data-ttu-id="a1b24-226">请求六个时间段的预测。</span><span class="sxs-lookup"><span data-stu-id="a1b24-226">Request predictions for six time slices.</span></span> <span data-ttu-id="a1b24-227">为此，请指定 6 个时间段，或者将起点指定为时间段 1，终点指定为时间段 7。</span><span class="sxs-lookup"><span data-stu-id="a1b24-227">To do this, specify 6 time slices, or specify the starting point as time slice 1, and the ending point as time slice 7.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a1b24-228">与 `EXTEND_MODEL_CASES` 不同，您不能返回作为输入数据添加的相同值。</span><span class="sxs-lookup"><span data-stu-id="a1b24-228">Unlike `EXTEND_MODEL_CASES`, you cannot return the same values that you added as input data.</span></span> <span data-ttu-id="a1b24-229">返回的全部六个值都是基于更新模型的预测，其中包括旧数据和新数据。</span><span class="sxs-lookup"><span data-stu-id="a1b24-229">All six values returned are predictions that are based on the updated model, which includes both old and new data.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a1b24-230">对于 REPLACE_MODEL_CASES，从时间戳 1 开始获取基于新数据的新预测，这会替换旧的定型数据。</span><span class="sxs-lookup"><span data-stu-id="a1b24-230">With REPLACE_MODEL_CASES, starting at timestamp 1 you get new predictions based on the new data, which replaces the old training data.</span></span>  
  
 <span data-ttu-id="a1b24-231">有关使用和的语法的查询示例和详细信息 `REPLACE_MODEL_CASES` `EXTEND_MODEL_CASES` ，请参阅[PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx)。</span><span class="sxs-lookup"><span data-stu-id="a1b24-231">For query examples and more information about the syntax for using `REPLACE_MODEL_CASES` and `EXTEND_MODEL_CASES`, see [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx).</span></span>  
  
###  <a name="missing-value-substitution-in-time-series-models"></a><a name="bkmk_MissingValues"></a><span data-ttu-id="a1b24-232">时序模型中缺少值替换</span><span class="sxs-lookup"><span data-stu-id="a1b24-232">Missing Value Substitution in Time Series Models</span></span>  
 <span data-ttu-id="a1b24-233">在通过 `PREDICTION JOIN` 语句在时序模型中添加新数据时，新数据集不能有任何缺失值。</span><span class="sxs-lookup"><span data-stu-id="a1b24-233">When you add new data to a time series model by using a `PREDICTION JOIN` statement, the new dataset cannot have any missing values.</span></span> <span data-ttu-id="a1b24-234">如果有任何序列不完整，则该模型必须使用 Null、数值平均值、特定数值平均值或预测值来替换缺失的值。</span><span class="sxs-lookup"><span data-stu-id="a1b24-234">If any series is incomplete, the model must supply the missing values by using either a null, a numeric means, a specific numeric mean, or a predicted value.</span></span> <span data-ttu-id="a1b24-235">如果指定了 `EXTEND_MODEL_CASES`，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 会将缺失值替换为基于原始模型的预测。</span><span class="sxs-lookup"><span data-stu-id="a1b24-235">If you specify `EXTEND_MODEL_CASES`, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] replaces the missing values with predictions based on the original model.</span></span> <span data-ttu-id="a1b24-236">如果你使用，则会将 `REPLACE_MODEL_CASES` [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 缺失值替换为你在*MISSING_VALUE_SUBSTITUTION*参数中指定的值。</span><span class="sxs-lookup"><span data-stu-id="a1b24-236">If you use `REPLACE_MODEL_CASES`, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] replaces the missing values with the value that you specify in the *MISSING_VALUE_SUBSTITUTION* parameter.</span></span>  
  
## <a name="list-of-prediction-functions"></a><span data-ttu-id="a1b24-237">预测函数的列表</span><span class="sxs-lookup"><span data-stu-id="a1b24-237">List of Prediction Functions</span></span>  
 <span data-ttu-id="a1b24-238">所有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 算法均支持一组通用的函数。</span><span class="sxs-lookup"><span data-stu-id="a1b24-238">All [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms support a common set of functions.</span></span> <span data-ttu-id="a1b24-239">但 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 时序算法支持下表中列出的其他函数。</span><span class="sxs-lookup"><span data-stu-id="a1b24-239">However, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Time Series algorithm supports the additional functions, listed in the following table.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a1b24-240">预测函数</span><span class="sxs-lookup"><span data-stu-id="a1b24-240">Prediction Function</span></span>|<span data-ttu-id="a1b24-241">使用情况</span><span class="sxs-lookup"><span data-stu-id="a1b24-241">Usage</span></span>|  
|[<span data-ttu-id="a1b24-242">Lag (DMX)</span><span class="sxs-lookup"><span data-stu-id="a1b24-242">Lag &#40;DMX&#41;</span></span>](/sql/dmx/lag-dmx)|<span data-ttu-id="a1b24-243">返回当前事例的日期与定型集的最近日期之间的若干时间段。</span><span class="sxs-lookup"><span data-stu-id="a1b24-243">Returns a number of time slices between the date of the current case and the last date of the training set.</span></span><br /><br /> <span data-ttu-id="a1b24-244">该函数的一个典型用途是标识最近的定型事例，以使您可以检索有关这些事例的详细数据。</span><span class="sxs-lookup"><span data-stu-id="a1b24-244">A typical use of this function is to identify recent training cases so that you can retrieve detailed data about the cases.</span></span>|  
|[<span data-ttu-id="a1b24-245">PredictNodeId (DMX)</span><span class="sxs-lookup"><span data-stu-id="a1b24-245">PredictNodeId &#40;DMX&#41;</span></span>](/sql/dmx/predictnodeid-dmx)|<span data-ttu-id="a1b24-246">返回指定的可预测列的节点 ID。</span><span class="sxs-lookup"><span data-stu-id="a1b24-246">Returns the node ID for the specified predictable column.</span></span><br /><br /> <span data-ttu-id="a1b24-247">该函数的一个典型用途是标识生成特定预测值的节点，以使您可以查看与该节点关联的事例，或者检索公式和其他详细信息。</span><span class="sxs-lookup"><span data-stu-id="a1b24-247">A typical use of this function is to identify the node that generated a particular predicted value so that you can review the cases associated with the node, or retrieve the equation and other details.</span></span>|  
|[<span data-ttu-id="a1b24-248">PredictStdev (DMX)</span><span class="sxs-lookup"><span data-stu-id="a1b24-248">PredictStdev &#40;DMX&#41;</span></span>](/sql/dmx/predictstdev-dmx)|<span data-ttu-id="a1b24-249">返回指定的可预测列中预测的标准偏差。</span><span class="sxs-lookup"><span data-stu-id="a1b24-249">Returns the standard deviation of the predictions in the specified predictable column.</span></span><br /><br /> <span data-ttu-id="a1b24-250">该函数取代时序模型不支持的 INCLUDE_STATISTICS 参数。</span><span class="sxs-lookup"><span data-stu-id="a1b24-250">This function replaces the INCLUDE_STATISTICS argument, which is not supported for time series models.</span></span>|  
|[<span data-ttu-id="a1b24-251">PredictVariance (DMX)</span><span class="sxs-lookup"><span data-stu-id="a1b24-251">PredictVariance &#40;DMX&#41;</span></span>](/sql/dmx/predictvariance-dmx)|<span data-ttu-id="a1b24-252">返回指定可预测列的预测方差。</span><span class="sxs-lookup"><span data-stu-id="a1b24-252">Returns the variance of the predictions for the specified predictable column.</span></span><br /><br /> <span data-ttu-id="a1b24-253">该函数取代时序模型不支持的 INCLUDE_STATISTICS 参数。</span><span class="sxs-lookup"><span data-stu-id="a1b24-253">This function replaces the INCLUDE_STATISTICS argument, which is not supported for time series models.</span></span>|  
|[<span data-ttu-id="a1b24-254">PredictTimeSeries (DMX)</span><span class="sxs-lookup"><span data-stu-id="a1b24-254">PredictTimeSeries &#40;DMX&#41;</span></span>](/sql/dmx/predicttimeseries-dmx)|<span data-ttu-id="a1b24-255">返回时序的历史预测值或未来预测值。</span><span class="sxs-lookup"><span data-stu-id="a1b24-255">Returns predicted historical values or future predicted values for a time series.</span></span><br /><br /> <span data-ttu-id="a1b24-256">还可以通过使用常规预测函数 [Predict (DMX)](/sql/dmx/predict-dmx) 来查询时序模型。</span><span class="sxs-lookup"><span data-stu-id="a1b24-256">You can also query time series models by using the general prediction function, [Predict &#40;DMX&#41;](/sql/dmx/predict-dmx).</span></span>|  
  
 <span data-ttu-id="a1b24-257">有关所有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 算法都支持的通用函数的列表，请参阅[通用预测函数 (DMX)](/sql/dmx/general-prediction-functions-dmx)。</span><span class="sxs-lookup"><span data-stu-id="a1b24-257">For a list of the functions that are common to all [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms, see [General Prediction Functions &#40;DMX&#41;](/sql/dmx/general-prediction-functions-dmx).</span></span> <span data-ttu-id="a1b24-258">有关特定函数的语法，请参阅[数据挖掘扩展插件 (DMX) 函数引用](/sql/dmx/data-mining-extensions-dmx-function-reference)。</span><span class="sxs-lookup"><span data-stu-id="a1b24-258">For the syntax of specific functions, see [Data Mining Extensions &#40;DMX&#41; Function Reference](/sql/dmx/data-mining-extensions-dmx-function-reference).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1b24-259">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a1b24-259">See Also</span></span>  
 <span data-ttu-id="a1b24-260">[数据挖掘查询](data-mining-queries.md) </span><span class="sxs-lookup"><span data-stu-id="a1b24-260">[Data Mining Queries](data-mining-queries.md) </span></span>  
 <span data-ttu-id="a1b24-261">[Microsoft 时序算法](microsoft-time-series-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="a1b24-261">[Microsoft Time Series Algorithm](microsoft-time-series-algorithm.md) </span></span>  
 <span data-ttu-id="a1b24-262">[Microsoft 时序算法技术参考](microsoft-time-series-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="a1b24-262">[Microsoft Time Series Algorithm Technical Reference](microsoft-time-series-algorithm-technical-reference.md) </span></span>  
 [<span data-ttu-id="a1b24-263">时序模型的挖掘模型内容（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="a1b24-263">Mining Model Content for Time Series Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-time-series-models-analysis-services-data-mining.md)  
  
  
