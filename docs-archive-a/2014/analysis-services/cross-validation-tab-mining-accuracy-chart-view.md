---
title: "\"交叉验证\" 选项卡 (挖掘准确性图表视图) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.accuracychart.crossvalidation.f1
ms.assetid: bd215a68-1ad7-4046-9c44-ec8e2be13a64
author: minewiskan
ms.author: owend
ms.openlocfilehash: 867bd6d1abffb29ec3eb2a8a78e562e5cbcc5b29
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581052"
---
# <a name="cross-validation-tab-mining-accuracy-chart-view"></a><span data-ttu-id="4347f-102">“交叉验证”选项卡（“挖掘准确性图表”视图）</span><span class="sxs-lookup"><span data-stu-id="4347f-102">Cross-Validation Tab (Mining Accuracy Chart View)</span></span>
  <span data-ttu-id="4347f-103">通过使用交叉验证，可以将挖掘结构分区为交叉部分，并针对每个交叉部分循环定型和测试模型。</span><span class="sxs-lookup"><span data-stu-id="4347f-103">Cross-validation lets you partition a mining structure into cross-sections and iteratively train and test models against each cross-section.</span></span> <span data-ttu-id="4347f-104">您可以指定要将数据划分成多少个折叠，每个折叠反过来会用作测试数据，而其余的数据用于为新模型定型。</span><span class="sxs-lookup"><span data-stu-id="4347f-104">You specify a number of folds to divide the data into, and each fold is used in turn as the test data, whereas the remaining data is used to train a new model.</span></span> [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] <span data-ttu-id="4347f-105">然后为每个模型生成一组标准准确性指标。</span><span class="sxs-lookup"><span data-stu-id="4347f-105">then generates a set of standard accuracy metrics for each model.</span></span> <span data-ttu-id="4347f-106">通过比较为每个交叉部分生成的模型的指标，可以清楚地了解挖掘模型对于整个数据集的可靠程度。</span><span class="sxs-lookup"><span data-stu-id="4347f-106">By comparing the metrics for the models generated for each cross-section, you can get a good idea of how reliable the mining model is for the whole data set.</span></span>  
  
 <span data-ttu-id="4347f-107">有关详细信息，请参阅[交叉验证（Analysis Services - 数据挖掘）](data-mining/cross-validation-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="4347f-107">For more information, see [Cross-Validation &#40;Analysis Services - Data Mining&#41;](data-mining/cross-validation-analysis-services-data-mining.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4347f-108">交叉验证不能用于使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] 时序算法或 [!INCLUDE[msCoName](../includes/msconame-md.md)] 顺序分析和聚类分析算法生成的模型。</span><span class="sxs-lookup"><span data-stu-id="4347f-108">Cross-validation cannot be used with models that were built by using the [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series algorithm or the [!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Clustering algorithm.</span></span> <span data-ttu-id="4347f-109">如果对包含这些模型类型的挖掘结构运行报表，则这些模型将不会包括在报表中。</span><span class="sxs-lookup"><span data-stu-id="4347f-109">If you run the report on a mining structure that contains these types of models, the models will not be included in the report.</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="4347f-110">任务列表</span><span class="sxs-lookup"><span data-stu-id="4347f-110">Task List</span></span>  
  
-   <span data-ttu-id="4347f-111">指定折叠数。</span><span class="sxs-lookup"><span data-stu-id="4347f-111">Specify the number of folds.</span></span>  
  
-   <span data-ttu-id="4347f-112">指定将用于交叉验证的最大事例数。</span><span class="sxs-lookup"><span data-stu-id="4347f-112">Specify the maximum number of cases to use for cross-validation.</span></span>  
  
-   <span data-ttu-id="4347f-113">指定可预测列。</span><span class="sxs-lookup"><span data-stu-id="4347f-113">Specify the predictable column.</span></span>  
  
-   <span data-ttu-id="4347f-114">可以选择指定可预测状态。</span><span class="sxs-lookup"><span data-stu-id="4347f-114">Optionally, specify a predictable state.</span></span>  
  
-   <span data-ttu-id="4347f-115">可以选择设置控制如何评估预测准确性的参数。</span><span class="sxs-lookup"><span data-stu-id="4347f-115">Optionally, set parameters that control how the accuracy of prediction is assessed.</span></span>  
  
-   <span data-ttu-id="4347f-116">单击“获取结果”\*\*\*\* 可显示交叉验证的结果。</span><span class="sxs-lookup"><span data-stu-id="4347f-116">Click **Get Results** to display the results of cross-validation.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="4347f-117">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="4347f-117">UI element list</span></span>  
 <span data-ttu-id="4347f-118">**折叠计数**</span><span class="sxs-lookup"><span data-stu-id="4347f-118">**Fold Count**</span></span>  
 <span data-ttu-id="4347f-119">指定要创建的折叠数或分区数。</span><span class="sxs-lookup"><span data-stu-id="4347f-119">Specify the number of folds, or partitions, to create.</span></span> <span data-ttu-id="4347f-120">最小值是 2，这表示数据集的一半用于测试，另一半用于定型。</span><span class="sxs-lookup"><span data-stu-id="4347f-120">The minimum value is 2, meaning that half the data set is used for testing and half for training.</span></span>  
  
 <span data-ttu-id="4347f-121">对于会话挖掘结构，最大值是 10。</span><span class="sxs-lookup"><span data-stu-id="4347f-121">The maximum value is 10 for session mining structures.</span></span>  
  
 <span data-ttu-id="4347f-122">如果挖掘结构存储在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]的实例中，则最大值为 256。</span><span class="sxs-lookup"><span data-stu-id="4347f-122">The maximum value is 256 if the mining structure is stored in an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4347f-123">随着您增加折叠数，执行交叉验证所需的时间近似增加 n 倍。</span><span class="sxs-lookup"><span data-stu-id="4347f-123">As you increase the number of folds, the time that is required to perform cross-validation similarly increases by n.</span></span> <span data-ttu-id="4347f-124">如果事例数很大且“折叠计数”\*\*\*\* 的值也很大，可能遇到性能问题。</span><span class="sxs-lookup"><span data-stu-id="4347f-124">You might experience performance issues if the number of cases is large and the value of **Fold Count** is also large.</span></span>  
  
 <span data-ttu-id="4347f-125">**最大事例数**</span><span class="sxs-lookup"><span data-stu-id="4347f-125">**Max Cases**</span></span>  
 <span data-ttu-id="4347f-126">指定将用于交叉验证的最大事例数。</span><span class="sxs-lookup"><span data-stu-id="4347f-126">Specify the maximum number of cases to use for cross-validation.</span></span> <span data-ttu-id="4347f-127">任一特定折叠中的事例数等于 **“最大事例数”** 值除以 **“折叠计数”** 值。</span><span class="sxs-lookup"><span data-stu-id="4347f-127">The number of cases in any particular fold is equal to the **Max Cases** value divided by the **Fold Count** value.</span></span>  
  
 <span data-ttu-id="4347f-128">如果使用 **0**，则源数据中的所有事例都用于交叉验证。</span><span class="sxs-lookup"><span data-stu-id="4347f-128">If you use **0**, all cases in the source data are used for cross-validation.</span></span>  
  
 <span data-ttu-id="4347f-129">无默认值。</span><span class="sxs-lookup"><span data-stu-id="4347f-129">There is no default value.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4347f-130">如果增加事例数，处理时间也会增加。</span><span class="sxs-lookup"><span data-stu-id="4347f-130">As you increase the number of cases, processing time also increases.</span></span>  
  
 <span data-ttu-id="4347f-131">**目标属性**</span><span class="sxs-lookup"><span data-stu-id="4347f-131">**Target Attribute**</span></span>  
 <span data-ttu-id="4347f-132">从在所有模型中找到的可预测列的列表中选择列。</span><span class="sxs-lookup"><span data-stu-id="4347f-132">Select a column from the list of predictable columns found in all models.</span></span> <span data-ttu-id="4347f-133">每次执行交叉验证时，只能选择一个可预测列。</span><span class="sxs-lookup"><span data-stu-id="4347f-133">You can only select one predictable column every time that you perform cross-validation.</span></span>  
  
 <span data-ttu-id="4347f-134">若要只测试聚类分析模型，请选择 **“分类”**。</span><span class="sxs-lookup"><span data-stu-id="4347f-134">To test only clustering models, select **Cluster**.</span></span>  
  
 <span data-ttu-id="4347f-135">**目标状态**</span><span class="sxs-lookup"><span data-stu-id="4347f-135">**Target State**</span></span>  
 <span data-ttu-id="4347f-136">键入一个值，或者从值的下拉列表中选择一个目标值。</span><span class="sxs-lookup"><span data-stu-id="4347f-136">Type a value, or select a target value from a drop-down list of values.</span></span>  
  
 <span data-ttu-id="4347f-137">默认值为 `null`，表示将测试所有状态。</span><span class="sxs-lookup"><span data-stu-id="4347f-137">The default value is `null`, indicating that all states are to be tested.</span></span>  
  
 <span data-ttu-id="4347f-138">对聚类分析模型禁用。</span><span class="sxs-lookup"><span data-stu-id="4347f-138">Disabled for clustering models.</span></span>  
  
 <span data-ttu-id="4347f-139">**目标**  **阈值**</span><span class="sxs-lookup"><span data-stu-id="4347f-139">**Target**  **Threshold**</span></span>  
 <span data-ttu-id="4347f-140">指定一个 0 到 1 之间的值，该值指示预测概率，高于此概率的预测状态被计为正确。</span><span class="sxs-lookup"><span data-stu-id="4347f-140">Specify a value between 0 and 1 that indicates the prediction probability above which a predicted state is considered to be correct.</span></span> <span data-ttu-id="4347f-141">可以使用 0.1 为增量来设置该值。</span><span class="sxs-lookup"><span data-stu-id="4347f-141">The value can be set in 0.1 increments.</span></span>  
  
 <span data-ttu-id="4347f-142">默认值为 `null`，表明将可能性最大的预测计为正确。</span><span class="sxs-lookup"><span data-stu-id="4347f-142">The default is `null`, indicating that the most probable prediction is counted as correct.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4347f-143">虽然可以将值设置为 0.0，但这样做会增加处理时间，而且不会产生有意义的结果。</span><span class="sxs-lookup"><span data-stu-id="4347f-143">Although you can set the value to 0.0, using this value will increase processing time and not yield meaningful results.</span></span>  
  
 <span data-ttu-id="4347f-144">**获取结果**</span><span class="sxs-lookup"><span data-stu-id="4347f-144">**Get Results**</span></span>  
 <span data-ttu-id="4347f-145">单击此项将使用指定参数开始模型的交叉验证。</span><span class="sxs-lookup"><span data-stu-id="4347f-145">Click to begin cross-validation of the model using the specified parameters.</span></span>  
  
 <span data-ttu-id="4347f-146">模型被分区为指定数量的折叠，并为每个折叠测试单独的模型。</span><span class="sxs-lookup"><span data-stu-id="4347f-146">The model is partitioned into the specified number of folds and a separate model is tested for each fold.</span></span> <span data-ttu-id="4347f-147">因此，交叉验证可能需要一些时间才能返回结果。</span><span class="sxs-lookup"><span data-stu-id="4347f-147">Therefore, it might take some time for cross-validation to return the results.</span></span>  
  
 <span data-ttu-id="4347f-148">有关如何解释交叉验证报告的结果的详细信息，请参阅 [交叉验证报表中的度量值](data-mining/measures-in-the-cross-validation-report.md)。</span><span class="sxs-lookup"><span data-stu-id="4347f-148">For more information about how to interpret the results of the cross-validation report, see [Measures in the Cross-Validation Report](data-mining/measures-in-the-cross-validation-report.md).</span></span>  
  
## <a name="setting-the-accuracy-threshold"></a><span data-ttu-id="4347f-149">设置准确性阈值</span><span class="sxs-lookup"><span data-stu-id="4347f-149">Setting the Accuracy Threshold</span></span>  
 <span data-ttu-id="4347f-150">您可以通过设置 **“目标阈值”** \*\*\*\* 的值来控制度量预测准确性的标准。</span><span class="sxs-lookup"><span data-stu-id="4347f-150">You can control the standard for measuring prediction accuracy by setting a value for **Target** **Threshold**.</span></span> <span data-ttu-id="4347f-151">阈值表示一种准确性栏。</span><span class="sxs-lookup"><span data-stu-id="4347f-151">A threshold represents a kind of accuracy bar.</span></span> <span data-ttu-id="4347f-152">为每个预测分配一个预测值正确的概率。</span><span class="sxs-lookup"><span data-stu-id="4347f-152">Each prediction is assigned a probability that the predicted value is correct.</span></span> <span data-ttu-id="4347f-153">因此，如果将 **“目标阈值”** \*\*\*\* 的值设置为接近 1，则要求任一特定预测的概率很高才能计为准确的预测。</span><span class="sxs-lookup"><span data-stu-id="4347f-153">Therefore, if you set the **Target** **Threshold** value closer to 1, you are requiring that the probability for any particular prediction to be fairly high to be counted as a good prediction.</span></span> <span data-ttu-id="4347f-154">反之，如果将 **“目标阈值”** \*\*\*\* 设置为接近 0，则即使具有较低概率值的预测也会计为“准确的”预测。</span><span class="sxs-lookup"><span data-stu-id="4347f-154">Conversely, if you set **Target** **Threshold** closer to 0, even predictions with lower probability values are counted as "good" predictions.</span></span>  
  
 <span data-ttu-id="4347f-155">由于任何预测的概率都取决于数据量以及所进行预测的类型，因此没有建议的阈值。</span><span class="sxs-lookup"><span data-stu-id="4347f-155">There is no recommended threshold value because the probability of any prediction depends on the amount of data and the type of prediction you are making.</span></span> <span data-ttu-id="4347f-156">应查看不同概率级别的一些预测，以确定适用于您的数据的准确性栏。</span><span class="sxs-lookup"><span data-stu-id="4347f-156">You should review some predictions at different probability levels to determine an appropriate accuracy bar for your data.</span></span> <span data-ttu-id="4347f-157">进行此操作非常重要，因为对 **“目标阈值”** \*\*\*\* 设置的值会影响模型的度量准确性。</span><span class="sxs-lookup"><span data-stu-id="4347f-157">It is important that you do this, because the value that you set for **Target** **Threshold** affects the measured accuracy of the model.</span></span>  
  
 <span data-ttu-id="4347f-158">例如，假设对特定目标状态进行了三次预测，每次预测的概率分别是 0.05、0.15 和 0.8。</span><span class="sxs-lookup"><span data-stu-id="4347f-158">For example, suppose three predictions are made for a particular target state, and the probabilities of each prediction are 0.05, 0.15, and 0.8.</span></span> <span data-ttu-id="4347f-159">如果将阈值设置为 0.5，则仅有一个预测计为正确。</span><span class="sxs-lookup"><span data-stu-id="4347f-159">If you set the threshold to 0.5, only one prediction is counted as being correct.</span></span> <span data-ttu-id="4347f-160">如果将 **“目标阈值”** \*\*\*\* 设置为 0.10，则两个预测将计为正确。</span><span class="sxs-lookup"><span data-stu-id="4347f-160">If you set **Target** **Threshold** to 0.10, two predictions are counted as being correct.</span></span>  
  
 <span data-ttu-id="4347f-161">如果将 "**目标\*\*\*\*阈值**" 设置为 `null` （默认值），则每个事例的最可能预测将计为正确。</span><span class="sxs-lookup"><span data-stu-id="4347f-161">When **Target** **Threshold** is set to `null`, which is the default value, the most probable prediction for each case is counted as correct.</span></span> <span data-ttu-id="4347f-162">在上面的示例中，0.05、0.15 和 0.8 是三个不同事例中的预测概率。</span><span class="sxs-lookup"><span data-stu-id="4347f-162">In the example just cited, 0.05, 0.15, and 0.8 are the probabilities for predictions in three different cases.</span></span> <span data-ttu-id="4347f-163">虽然概率差别较大，但每个预测都记为正确，因为每个事例只生成一个预测，而这些预测是这些事例的最佳预测。</span><span class="sxs-lookup"><span data-stu-id="4347f-163">Although the probabilities are very different, each prediction would be counted as correct, because each case generates only one prediction and these are the best predictions for these cases.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4347f-164">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4347f-164">See Also</span></span>  
 <span data-ttu-id="4347f-165">[测试和验证 &#40;数据挖掘&#41;](data-mining/testing-and-validation-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="4347f-165">[Testing and Validation &#40;Data Mining&#41;](data-mining/testing-and-validation-data-mining.md) </span></span>  
 <span data-ttu-id="4347f-166">[交叉验证 &#40;Analysis Services 数据挖掘&#41;](data-mining/cross-validation-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="4347f-166">[Cross-Validation &#40;Analysis Services - Data Mining&#41;](data-mining/cross-validation-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="4347f-167">[交叉验证报表中的度量值](data-mining/measures-in-the-cross-validation-report.md) </span><span class="sxs-lookup"><span data-stu-id="4347f-167">[Measures in the Cross-Validation Report](data-mining/measures-in-the-cross-validation-report.md) </span></span>  
 [<span data-ttu-id="4347f-168">数据挖掘存储过程（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="4347f-168">Data Mining Stored Procedures &#40;Analysis Services - Data Mining&#41;</span></span>](/sql/analysis-services/data-mining/data-mining-stored-procedures-analysis-services-data-mining)  
  
  
