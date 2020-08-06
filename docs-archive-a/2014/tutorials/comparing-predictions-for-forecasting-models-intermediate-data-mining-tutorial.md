---
title: 比较预测模型的预测 (中级数据挖掘教程) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: ead8a1fe-60d8-4017-8fb8-6fe32168e46d
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 63cf9c001298b0d2bfd2cf35ed42485a16817fd7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691396"
---
# <a name="comparing-predictions-for-forecasting-models-intermediate-data-mining-tutorial"></a><span data-ttu-id="8d2d5-102">比较预测模型的预测（数据挖掘中级教程）</span><span class="sxs-lookup"><span data-stu-id="8d2d5-102">Comparing Predictions for Forecasting Models (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="8d2d5-103">在本教程前面的步骤中，您已经创建了多个时序模型：</span><span class="sxs-lookup"><span data-stu-id="8d2d5-103">In the previous steps of this tutorial, you created multiple time series models:</span></span>  
  
-   <span data-ttu-id="8d2d5-104">区域和型号的每个组合的预测，只基于单个型号和区域的数据。</span><span class="sxs-lookup"><span data-stu-id="8d2d5-104">Predictions for each combination of region and model, based only on data for the individual model and region.</span></span>  
  
-   <span data-ttu-id="8d2d5-105">每个区域的预测，基于更新的数据。</span><span class="sxs-lookup"><span data-stu-id="8d2d5-105">Predictions for each region, based on updated data.</span></span>  
  
-   <span data-ttu-id="8d2d5-106">在全球范围对所有型号的预测，基于聚合数据。</span><span class="sxs-lookup"><span data-stu-id="8d2d5-106">Predictions for all models on a worldwide basis, based on aggregated data.</span></span>  
  
-   <span data-ttu-id="8d2d5-107">在北美区域对 M200 型号的预测，基于聚合模型。</span><span class="sxs-lookup"><span data-stu-id="8d2d5-107">Predictions for the M200 model in the North America region, based on the aggregated model.</span></span>  
  
 <span data-ttu-id="8d2d5-108">为了汇总时序预测的功能，您将查看变化以了解在使用用于扩展数据或替换数据的选项时是如何影响预测结果的。</span><span class="sxs-lookup"><span data-stu-id="8d2d5-108">To summarize the features for time series predictions, you will review the changes to see how the use of the options to extend or replace data affected forecasting results.</span></span>  
  
 [<span data-ttu-id="8d2d5-109">EXTEND_MODEL_CASES</span><span class="sxs-lookup"><span data-stu-id="8d2d5-109">EXTEND_MODEL_CASES</span></span>](#bkmk_EXTEND)  
  
 [<span data-ttu-id="8d2d5-110">REPLACE_MODEL_CASES</span><span class="sxs-lookup"><span data-stu-id="8d2d5-110">REPLACE_MODEL_CASES</span></span>](#bkmk_REPLACE)  
  
##  <a name="comparing-the-original-results-with-results-after-adding-data"></a><a name="bkmk_EXTEND"></a><span data-ttu-id="8d2d5-111">在添加数据后将原始结果与结果进行比较</span><span class="sxs-lookup"><span data-stu-id="8d2d5-111">Comparing the Original Results with Results after Adding Data</span></span>  
 <span data-ttu-id="8d2d5-112">让我们看看太平洋地区的 M200 产品系列的数据，以了解如何用新数据更新模型会影响结果。</span><span class="sxs-lookup"><span data-stu-id="8d2d5-112">Let's look at the data for just the M200 product line in the Pacific region, to see how updating the model with new data affects the results.</span></span> <span data-ttu-id="8d2d5-113">请记住原始数据序列在 2004 年 6 月结束，我们获取了 7 月、8 月和 9 月的新数据。</span><span class="sxs-lookup"><span data-stu-id="8d2d5-113">Remember that the original data series ended in June 2004, and we obtained new data for July, August, and September.</span></span>  
  
-   <span data-ttu-id="8d2d5-114">第一列显示添加的新数据。</span><span class="sxs-lookup"><span data-stu-id="8d2d5-114">The first column shows the new data that was added.</span></span>  
  
-   <span data-ttu-id="8d2d5-115">第二列显示基于原始数据序列 7 月和之后的预测。</span><span class="sxs-lookup"><span data-stu-id="8d2d5-115">The second column shows the forecast for July and later based on the original data series.</span></span>  
  
-   <span data-ttu-id="8d2d5-116">第三列显示基于扩展数据的预测。</span><span class="sxs-lookup"><span data-stu-id="8d2d5-116">The third column shows the forecast based on the extended data.</span></span>  
  
|<span data-ttu-id="8d2d5-117">**M200 Pacific**</span><span class="sxs-lookup"><span data-stu-id="8d2d5-117">**M200 Pacific**</span></span>|<span data-ttu-id="8d2d5-118">更新的实际销售额数据</span><span class="sxs-lookup"><span data-stu-id="8d2d5-118">Updated real sales data</span></span>|<span data-ttu-id="8d2d5-119">添加数据之前的预测</span><span class="sxs-lookup"><span data-stu-id="8d2d5-119">Forecast before data was added</span></span>|<span data-ttu-id="8d2d5-120">扩展的预测</span><span class="sxs-lookup"><span data-stu-id="8d2d5-120">Extended prediction</span></span>|  
|----------------------|-----------------------------|------------------------------------|-------------------------|  
|<span data-ttu-id="8d2d5-121">7-25-2008</span><span class="sxs-lookup"><span data-stu-id="8d2d5-121">7-25-2008</span></span>|<span data-ttu-id="8d2d5-122">**65**</span><span class="sxs-lookup"><span data-stu-id="8d2d5-122">**65**</span></span>|<span data-ttu-id="8d2d5-123">32</span><span class="sxs-lookup"><span data-stu-id="8d2d5-123">32</span></span>|<span data-ttu-id="8d2d5-124">**65**</span><span class="sxs-lookup"><span data-stu-id="8d2d5-124">**65**</span></span>|  
|<span data-ttu-id="8d2d5-125">8-25-2008</span><span class="sxs-lookup"><span data-stu-id="8d2d5-125">8-25-2008</span></span>|<span data-ttu-id="8d2d5-126">**54**</span><span class="sxs-lookup"><span data-stu-id="8d2d5-126">**54**</span></span>|<span data-ttu-id="8d2d5-127">37</span><span class="sxs-lookup"><span data-stu-id="8d2d5-127">37</span></span>|<span data-ttu-id="8d2d5-128">**54**</span><span class="sxs-lookup"><span data-stu-id="8d2d5-128">**54**</span></span>|  
|<span data-ttu-id="8d2d5-129">9-25-2008</span><span class="sxs-lookup"><span data-stu-id="8d2d5-129">9-25-2008</span></span>|<span data-ttu-id="8d2d5-130">**61**</span><span class="sxs-lookup"><span data-stu-id="8d2d5-130">**61**</span></span>|<span data-ttu-id="8d2d5-131">32</span><span class="sxs-lookup"><span data-stu-id="8d2d5-131">32</span></span>|<span data-ttu-id="8d2d5-132">**61**</span><span class="sxs-lookup"><span data-stu-id="8d2d5-132">**61**</span></span>|  
|<span data-ttu-id="8d2d5-133">10-25-2008</span><span class="sxs-lookup"><span data-stu-id="8d2d5-133">10-25-2008</span></span>|<span data-ttu-id="8d2d5-134">无数据</span><span class="sxs-lookup"><span data-stu-id="8d2d5-134">No data</span></span>|<span data-ttu-id="8d2d5-135">36</span><span class="sxs-lookup"><span data-stu-id="8d2d5-135">36</span></span>|<span data-ttu-id="8d2d5-136">32</span><span class="sxs-lookup"><span data-stu-id="8d2d5-136">32</span></span>|  
|<span data-ttu-id="8d2d5-137">11-25-2008</span><span class="sxs-lookup"><span data-stu-id="8d2d5-137">11-25-2008</span></span>|<span data-ttu-id="8d2d5-138">无数据</span><span class="sxs-lookup"><span data-stu-id="8d2d5-138">No data</span></span>|<span data-ttu-id="8d2d5-139">31</span><span class="sxs-lookup"><span data-stu-id="8d2d5-139">31</span></span>|<span data-ttu-id="8d2d5-140">41</span><span class="sxs-lookup"><span data-stu-id="8d2d5-140">41</span></span>|  
|<span data-ttu-id="8d2d5-141">12-25-2008</span><span class="sxs-lookup"><span data-stu-id="8d2d5-141">12-25-2008</span></span>|<span data-ttu-id="8d2d5-142">无数据</span><span class="sxs-lookup"><span data-stu-id="8d2d5-142">No data</span></span>|<span data-ttu-id="8d2d5-143">34</span><span class="sxs-lookup"><span data-stu-id="8d2d5-143">34</span></span>|<span data-ttu-id="8d2d5-144">32</span><span class="sxs-lookup"><span data-stu-id="8d2d5-144">32</span></span>|  
  
 <span data-ttu-id="8d2d5-145">您将注意到使用扩展数据（此处用粗体显示）的预测完全重复实际数据点。</span><span class="sxs-lookup"><span data-stu-id="8d2d5-145">You will note that the forecasts using the extended data (shown here in bold) repeat the real data points exactly.</span></span> <span data-ttu-id="8d2d5-146">重复是默认设置。</span><span class="sxs-lookup"><span data-stu-id="8d2d5-146">The repetition is by design.</span></span> <span data-ttu-id="8d2d5-147">只要有要使用的实际数据点，预测查询将返回实际值，仅在新的实际数据点用完后才输出新的预测值。</span><span class="sxs-lookup"><span data-stu-id="8d2d5-147">As long as there are real data points to use, the prediction query will return the actual values, and output new prediction values only after the new actual data points have been used up.</span></span>  
  
 <span data-ttu-id="8d2d5-148">通常，算法给予新数据中的更改的权重比模型开始就有的数据更改的权重大。</span><span class="sxs-lookup"><span data-stu-id="8d2d5-148">In general, the algorithm weights the changes in the new data more strongly than data from the beginning of the model data.</span></span> <span data-ttu-id="8d2d5-149">但是，在这种情况下，新销售额数字表示仅相对前一阶段增长了 20-30％，因此仅对预测的销售额稍有增加，在销售预测再次向下后，与新数据之前的月份的趋势更为一致。</span><span class="sxs-lookup"><span data-stu-id="8d2d5-149">However, in this case, the new sales figures represent an increase of only 20-30 percent over the previous period, so there only was a slight uptick in projected sales, after which the sales projections drop again, more in line with the trend in the months before the new data.</span></span>  
  
##  <a name="comparing-the-original-and-cross-prediction-results"></a><a name="bkmk_REPLACE"></a><span data-ttu-id="8d2d5-150">比较原始结果和交叉预测结果</span><span class="sxs-lookup"><span data-stu-id="8d2d5-150">Comparing the Original and Cross-Prediction Results</span></span>  
 <span data-ttu-id="8d2d5-151">请记住，原始挖掘模型揭示在区域之间以及产品系列之间存在较大的差异。</span><span class="sxs-lookup"><span data-stu-id="8d2d5-151">Remember that the original mining model revealed big differences between regions and between product lines.</span></span> <span data-ttu-id="8d2d5-152">例如，M200 型号的销售很强，而 T1000 型号的销售在所有区域中都比较弱。</span><span class="sxs-lookup"><span data-stu-id="8d2d5-152">For example, sales for the M200 model were very strong, while sales for the T1000 model were fairly low across all regions.</span></span> <span data-ttu-id="8d2d5-153">此外，某些系列的数据没有太多。</span><span class="sxs-lookup"><span data-stu-id="8d2d5-153">Moreover, some series didn't have much data.</span></span> <span data-ttu-id="8d2d5-154">序列不齐整，这意味着它们没有相同的起点。</span><span class="sxs-lookup"><span data-stu-id="8d2d5-154">Series were ragged, meaning they didn't have the same starting point.</span></span>  
  
 <span data-ttu-id="8d2d5-155">![预测 M200 和 T1000 数量的序列](../../2014/tutorials/media/6series-defaultforecasting.gif "预测 M200 和 T1000 数量的序列")</span><span class="sxs-lookup"><span data-stu-id="8d2d5-155">![Series predicting M200 and T1000 quantity](../../2014/tutorials/media/6series-defaultforecasting.gif "Series predicting M200 and T1000 quantity")</span></span>  
  
 <span data-ttu-id="8d2d5-156">因此，当您基于通用模型进行预测时预测如何变化，该模型基于全球范围内的销售额而非原始数据集？</span><span class="sxs-lookup"><span data-stu-id="8d2d5-156">So how did the predictions change when you made your projections based on the general model, which was based on world-wide sales, rather than the original data sets?</span></span> <span data-ttu-id="8d2d5-157">为了确保您没有丢失任何信息或进行错误预测，可以将结果存储到一个表中，将预测表与历史记录数据表联接，然后用图形表示两组历史记录数据和预测数据。</span><span class="sxs-lookup"><span data-stu-id="8d2d5-157">To assure yourself that you have not lost any information or skewed the predictions, you can save the results to a table, join the table of predictions to the table of historical data, and then graph the two sets of historical data and predictions.</span></span>  
  
 <span data-ttu-id="8d2d5-158">以下关系图仅基于一个产品系列（M200）。</span><span class="sxs-lookup"><span data-stu-id="8d2d5-158">The following diagram is based on just one product line, the M200.</span></span> <span data-ttu-id="8d2d5-159">该图比较了初始挖掘模型的预测值和使用聚合挖掘模型的预测值。</span><span class="sxs-lookup"><span data-stu-id="8d2d5-159">The graph compares the predictions from the initial mining model against the predictions using the aggregated mining model.</span></span>  
  
 <span data-ttu-id="8d2d5-160">![用于比较预测的 Excel 图表](../../2014/tutorials/media/m200-predictions-compared.gif "用于比较预测的 Excel 图表")</span><span class="sxs-lookup"><span data-stu-id="8d2d5-160">![Excel chart comparing predictions](../../2014/tutorials/media/m200-predictions-compared.gif "Excel chart comparing predictions")</span></span>  
  
 <span data-ttu-id="8d2d5-161">从此关系图中，您可以看到聚合挖掘模型在使得各个数据序列中的波动尽量最小的同时保持整体范围和值的趋势。</span><span class="sxs-lookup"><span data-stu-id="8d2d5-161">From this diagram, you can see that the aggregated mining model preserves the overall range and trends in values while minimizing the fluctuations in the individual data series.</span></span>  
  
## <a name="conclusion"></a><span data-ttu-id="8d2d5-162">结论</span><span class="sxs-lookup"><span data-stu-id="8d2d5-162">Conclusion</span></span>  
 <span data-ttu-id="8d2d5-163">您学习了如何创建和自定义可用于预测的时序模型。</span><span class="sxs-lookup"><span data-stu-id="8d2d5-163">You have learned how to create and to customize a time series model that can be used for forecasting.</span></span>  
  
 <span data-ttu-id="8d2d5-164">您学习了通过使用 EXTEND_MODEL_CASES 参数添加新数据和创建预测来更新时序模型，而不必重新处理它们。</span><span class="sxs-lookup"><span data-stu-id="8d2d5-164">You have learned to update your time series models without having to reprocess them, by adding new data and creating predictions using the parameter, EXTEND_MODEL_CASES.</span></span>  
  
 <span data-ttu-id="8d2d5-165">您学习了通过使用 REPLACE_MODEL_CASES 参数和将模型应用到不同数据序列，创建可用于交叉预测的模型。</span><span class="sxs-lookup"><span data-stu-id="8d2d5-165">You have learned to create models that can be used for cross-prediction, by using the REPLACE_MODEL_CASES parameter and applying the model to a different data series.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d2d5-166">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8d2d5-166">See Also</span></span>  
 <span data-ttu-id="8d2d5-167">[中级数据挖掘教程 &#40;Analysis Services 数据挖掘&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="8d2d5-167">[Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="8d2d5-168">时序模型查询示例</span><span class="sxs-lookup"><span data-stu-id="8d2d5-168">Time Series Model Query Examples</span></span>](../../2014/analysis-services/data-mining/time-series-model-query-examples.md)  
  
  
