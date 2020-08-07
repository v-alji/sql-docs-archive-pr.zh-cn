---
title: 自定义和处理预测模型 (中级数据挖掘教程) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 4bd25e15-9d9e-4528-b7bc-ccb856643aec
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 03dc67907b22750eb1b8539feaddec58f61f702f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588784"
---
# <a name="customizing-and-processing-the-forecasting-model-intermediate-data-mining-tutorial"></a><span data-ttu-id="697ab-102">自定义和处理预测模型（数据挖掘中级教程）</span><span class="sxs-lookup"><span data-stu-id="697ab-102">Customizing and Processing the Forecasting Model (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="697ab-103">[!INCLUDE[msCoName](../includes/msconame-md.md)] 时序算法提供了多个参数，这些参数影响模型创建方式和时间数据分析方式。</span><span class="sxs-lookup"><span data-stu-id="697ab-103">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series algorithm provides parameters that affect how a model is created, and how time data is analyzed.</span></span> <span data-ttu-id="697ab-104">更改这些属性可以极大地影响挖掘模型进行预测的方式。</span><span class="sxs-lookup"><span data-stu-id="697ab-104">Changing these properties can significantly affect how the mining model makes predictions.</span></span>  
  
 <span data-ttu-id="697ab-105">对于教程中的此任务，您将执行以下任务来修改模型：</span><span class="sxs-lookup"><span data-stu-id="697ab-105">For this task in the tutorial, you will perform the following tasks to modify the model:</span></span>  
  
1.  <span data-ttu-id="697ab-106">您将通过为*PERIODICITY_HINT*参数添加新值来自定义模型处理时间段的方式。</span><span class="sxs-lookup"><span data-stu-id="697ab-106">You will customize the way your model handles time periods by adding a new value for the *PERIODICITY_HINT* parameter.</span></span>  
  
2.  <span data-ttu-id="697ab-107">您将了解 Microsoft 时序算法的两个其他重要参数：FORECAST_METHOD 和 PREDICTION_SMOOTHING，前者用于控制预测使用的方法，后者则用于自定义长期预测和短期预测的组合。</span><span class="sxs-lookup"><span data-stu-id="697ab-107">You will learn about two other important parameters for the Microsoft Time Series algorithm: FORECAST_METHOD, which lets you control the method used for forecasting, and PREDICTION_SMOOTHING, which lets you customize the blend of long-term and short-term predictions.</span></span>  
  
3.  <span data-ttu-id="697ab-108">您还可以告知算法要如何处理缺失值（可选）。</span><span class="sxs-lookup"><span data-stu-id="697ab-108">Optionally, you will tell the algorithm how you want missing values to be imputed.</span></span>  
  
4.  <span data-ttu-id="697ab-109">在进行所有更改后，您将部署和处理该模型。</span><span class="sxs-lookup"><span data-stu-id="697ab-109">After all the changes have been made, you will deploy and process the model.</span></span>  
  
## <a name="setting-time-series-parameters"></a><span data-ttu-id="697ab-110">设置时序参数</span><span class="sxs-lookup"><span data-stu-id="697ab-110">Setting Time Series Parameters</span></span>  
 <span data-ttu-id="697ab-111">**周期提示**</span><span class="sxs-lookup"><span data-stu-id="697ab-111">**Periodicity Hints**</span></span>  
  
 <span data-ttu-id="697ab-112">*PERIODICITY_HINT*参数提供算法，其中包含有关你预计会在数据中看到的其他时间段的信息。</span><span class="sxs-lookup"><span data-stu-id="697ab-112">The *PERIODICITY_HINT* parameter provides the algorithm with information about additional time periods that you expect to see in the data.</span></span> <span data-ttu-id="697ab-113">默认情况下，时序模型将尝试自动检测数据中的模式。</span><span class="sxs-lookup"><span data-stu-id="697ab-113">By default, time series models will try to automatically detect a pattern in the data.</span></span> <span data-ttu-id="697ab-114">但是，如果您已经知道预期的时间周期，提供周期提示可能提高模型的准确性。</span><span class="sxs-lookup"><span data-stu-id="697ab-114">However, if you already know the expected time cycle, providing a periodicity hint can potentially improve the accuracy of the model.</span></span> <span data-ttu-id="697ab-115">但是，如果您提供错误的周期提示，则会降低准确性；因此，如果不确定应该使用什么值，最好使用默认值。</span><span class="sxs-lookup"><span data-stu-id="697ab-115">However, if you provide the wrong periodicity hint, it can decrease accuracy; therefore, if you are not sure what value should be used, it is best to use the default.</span></span>  
  
 <span data-ttu-id="697ab-116">例如，用于此模型的视图每月聚合 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] 的销售数据。</span><span class="sxs-lookup"><span data-stu-id="697ab-116">For example, the view used for this model aggregates sales data from [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] on a monthly basis.</span></span> <span data-ttu-id="697ab-117">因此，模型使用的每个时间段表示一个月，所有预测将根据月份给出。</span><span class="sxs-lookup"><span data-stu-id="697ab-117">Therefore each time slice used by the model represents one month, and all predictions will also be in terms of months.</span></span> <span data-ttu-id="697ab-118">由于一年有12个月的时间，并且你预计销售模式每年都重复一次，因此，你需要将*PERIODICITY_HINT*参数设置为 `12` ，以指示12个时间段 (月) 构成一个完整的销售周期。</span><span class="sxs-lookup"><span data-stu-id="697ab-118">Since there are 12 months in a year and you expect that sales patterns more or less repeat on a yearly basis, you will set the *PERIODICITY_HINT* parameter to `12`, to indicate that 12 time slices (months) constitute one complete sales cycle.</span></span>  
  
 <span data-ttu-id="697ab-119">**预测方法**</span><span class="sxs-lookup"><span data-stu-id="697ab-119">**Forecasting Method**</span></span>  
  
 <span data-ttu-id="697ab-120">*FORECAST_METHOD*参数控制时序算法是否针对短期或长期预测进行了优化。</span><span class="sxs-lookup"><span data-stu-id="697ab-120">The *FORECAST_METHOD* parameter controls whether the time series algorithm is optimized for short-term or long-term predictions.</span></span> <span data-ttu-id="697ab-121">默认情况下， *FORECAST_METHOD*参数设置为 MIXED，这意味着将混合和平衡两个不同的算法，从而为短期预测和长期预测提供良好的结果。</span><span class="sxs-lookup"><span data-stu-id="697ab-121">By default, the *FORECAST_METHOD* parameter is set to MIXED, which means that two different algorithms are blended and balanced to provide good results for both short-term and long-term prediction.</span></span>  
  
 <span data-ttu-id="697ab-122">但是，如果您知道要使用特殊算法，可以将值更改为 ARIMA 或 ARTXP。</span><span class="sxs-lookup"><span data-stu-id="697ab-122">However, if you know that you want to use a particular algorithm, you can change the value to either ARIMA or ARTXP.</span></span>  
  
 <span data-ttu-id="697ab-123">**加权长期与短期预测**</span><span class="sxs-lookup"><span data-stu-id="697ab-123">**Weighting Long-Term vs. Short-Term Predictions**</span></span>  
  
 <span data-ttu-id="697ab-124">还可以使用 PREDICTION_SMOOTHING 参数自定义组合长期预测和短期预测的方式。</span><span class="sxs-lookup"><span data-stu-id="697ab-124">You can also customize the way that long-term and short-term predictions are combined by using the PREDICTION_SMOOTHING parameter.</span></span> <span data-ttu-id="697ab-125">默认情况下，此参数设置为 0.5，这通常会提供最佳平衡，从而实现总体准确性。</span><span class="sxs-lookup"><span data-stu-id="697ab-125">By default, this parameter is set to 0.5, which generally provides the best balance for overall accuracy.</span></span>  
  
#### <a name="to-change-the-algorithm-parameters"></a><span data-ttu-id="697ab-126">更改算法参数</span><span class="sxs-lookup"><span data-stu-id="697ab-126">To change the algorithm parameters</span></span>  
  
1.  <span data-ttu-id="697ab-127">在 "**挖掘模型**" 选项卡上，右键单击 "**预测**"，然后选择 "**设置算法参数**"。</span><span class="sxs-lookup"><span data-stu-id="697ab-127">On the **Mining Models** tab, right-click **Forecasting**, and select **Set Algorithm Parameters**.</span></span>  
  
2.  <span data-ttu-id="697ab-128">在 `PERIODICITY_HINT` "**算法参数**" 对话框的行中，单击 "**值**" 列，然后键入 `{12}` ，包括大括号。</span><span class="sxs-lookup"><span data-stu-id="697ab-128">In the `PERIODICITY_HINT` row of the **Algorithm Parameters** dialog box, click the **Value** column, then type `{12}`, including the braces.</span></span>  
  
     <span data-ttu-id="697ab-129">默认情况下，该算法还将添加值 {1}。</span><span class="sxs-lookup"><span data-stu-id="697ab-129">By default, the algorithm will also add the value {1}.</span></span>  
  
3.  <span data-ttu-id="697ab-130">在 `FORECAST_METHOD` 行中，验证 "**值**" 文本框是否为空或设置为 `MIXED` 。</span><span class="sxs-lookup"><span data-stu-id="697ab-130">In the `FORECAST_METHOD` row, verify that the **Value** text box is either blank or set to `MIXED`.</span></span> <span data-ttu-id="697ab-131">如果输入了不同的值，则键入 `MIXED` 以将参数更改回默认值。</span><span class="sxs-lookup"><span data-stu-id="697ab-131">If a different value has been entered, type `MIXED` to change the parameter back to the default value.</span></span>  
  
4.  <span data-ttu-id="697ab-132">在 " **PREDICTION_SMOOTHING** " 行中，验证 "**值**" 文本框是否为空或设置为0.5。</span><span class="sxs-lookup"><span data-stu-id="697ab-132">In the **PREDICTION_SMOOTHING** row, verify that the **Value** text box is either blank or set to 0.5.</span></span> <span data-ttu-id="697ab-133">如果输入了不同的值，请单击 "**值**" 并键入，将 `0.5` 参数更改回默认值。</span><span class="sxs-lookup"><span data-stu-id="697ab-133">If a different value has been entered, click **Value** and type `0.5` to change the parameter back to the default value.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="697ab-134">PREDICTION_SMOOTHING 参数仅在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Enterprise 中可用。</span><span class="sxs-lookup"><span data-stu-id="697ab-134">The PREDICTION_SMOOTHING parameter is available only in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Enterprise.</span></span> <span data-ttu-id="697ab-135">因此，在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Standard 中无法查看或更改 PREDICTION_SMOOTHING 参数的值。</span><span class="sxs-lookup"><span data-stu-id="697ab-135">Therefore, you cannot view or change the value of the PREDICTION_SMOOTHING parameter in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Standard.</span></span> <span data-ttu-id="697ab-136">但是，默认行为是使用两种算法并向它们分配相等的权重。</span><span class="sxs-lookup"><span data-stu-id="697ab-136">However, the default behavior is to use both algorithms and weight them equally.</span></span>  
  
5.  <span data-ttu-id="697ab-137">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="697ab-137">Click **OK**.</span></span>  
  
## <a name="handling-missing-data-optional"></a><span data-ttu-id="697ab-138">处理缺少的数据（可选）</span><span class="sxs-lookup"><span data-stu-id="697ab-138">Handling Missing Data (Optional)</span></span>  
 <span data-ttu-id="697ab-139">在许多情况下，您的销售数据可能具有用 null 填充的空白，或者某个商店在报告期限之前没有完成报表，在序列末尾留有空白单元。</span><span class="sxs-lookup"><span data-stu-id="697ab-139">In many cases, your sales data might have gaps that are filled with nulls, or a store might have failed to meet the reporting deadline, leaving an empty cell at the end of the series.</span></span> <span data-ttu-id="697ab-140">在这种情况下，[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 会引发以下错误，将不处理模型。</span><span class="sxs-lookup"><span data-stu-id="697ab-140">In such scenarios, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] raises the following error and will not process the model.</span></span>  
  
 <span data-ttu-id="697ab-141">"数据挖掘)  (错误：不会从挖掘模型的序列开始同步时间戳 \<series name> \<model name> 。</span><span class="sxs-lookup"><span data-stu-id="697ab-141">"Error (Data mining): Time stamps not synchronized starting with series \<series name>, of the mining model, \<model name>.</span></span> <span data-ttu-id="697ab-142">所有时序必须以相同的时间标记结束，并且不能有随意缺失的数据点。</span><span class="sxs-lookup"><span data-stu-id="697ab-142">All time series must end at the same time mark and cannot have arbitrarily missing data points.</span></span> <span data-ttu-id="697ab-143">如果将 MISSING_VALUE_SUBSTITUTION 参数设置为 Previous 或一个数值常量，那么，只要有可能，就将自动修补缺失的数据点。”</span><span class="sxs-lookup"><span data-stu-id="697ab-143">Setting the MISSING_VALUE_SUBSTITUTION parameter to Previous or to a numeric constant will automatically patch missing data points where possible."</span></span>  
  
 <span data-ttu-id="697ab-144">为了避免出现此错误，可以指定 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 通过使用以下方法之一自动提供新值以填充空白：</span><span class="sxs-lookup"><span data-stu-id="697ab-144">To avoid this error, you can specify that [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] automatically provide new values to fill in the gaps by using any one of the following methods:</span></span>  
  
-   <span data-ttu-id="697ab-145">使用平均值。</span><span class="sxs-lookup"><span data-stu-id="697ab-145">Using an average value.</span></span> <span data-ttu-id="697ab-146">平均值是使用同一数据序列中的所有有效值来计算的。</span><span class="sxs-lookup"><span data-stu-id="697ab-146">The mean is calculated by using all valid values in the same data series.</span></span>  
  
-   <span data-ttu-id="697ab-147">使用以前的值。</span><span class="sxs-lookup"><span data-stu-id="697ab-147">Using the previous value.</span></span> <span data-ttu-id="697ab-148">可以用以前的值替换多个缺少的单元格，但是不能填充起始值。</span><span class="sxs-lookup"><span data-stu-id="697ab-148">You can substitute previous values for multiple missing cells, but you cannot fill starting values.</span></span>  
  
-   <span data-ttu-id="697ab-149">使用您提供的常量值。</span><span class="sxs-lookup"><span data-stu-id="697ab-149">Using a constant value that you supply.</span></span>  
  
#### <a name="to-specify-that-gaps-be-filled-by-averaging-values"></a><span data-ttu-id="697ab-150">指定通过求平均值来填充空白</span><span class="sxs-lookup"><span data-stu-id="697ab-150">To specify that gaps be filled by averaging values</span></span>  
  
1.  <span data-ttu-id="697ab-151">在 "**挖掘模型**" 选项卡上，右键单击 "**预测**" 列，然后选择 "**设置算法参数**"。</span><span class="sxs-lookup"><span data-stu-id="697ab-151">On the **Mining Models** tab, right-click the **Forecasting** column, and select **Set Algorithm Parameters**.</span></span>  
  
2.  <span data-ttu-id="697ab-152">在 "**算法参数**" 对话框的 " **MISSING_VALUE_SUBSTITUTION** " 行中，单击 "**值**" 列，然后键入 `Mean` 。</span><span class="sxs-lookup"><span data-stu-id="697ab-152">In the **Algorithm Parameters** dialog box, in the **MISSING_VALUE_SUBSTITUTION** row, click the **Value** column, and type `Mean`.</span></span>  
  
## <a name="build-the-model"></a><span data-ttu-id="697ab-153">生成模型</span><span class="sxs-lookup"><span data-stu-id="697ab-153">Build the Model</span></span>  
 <span data-ttu-id="697ab-154">要使用模型，必须将它部署到服务器，然后通过算法运行定型数据以便处理模型。</span><span class="sxs-lookup"><span data-stu-id="697ab-154">To use the model, you must deploy it to a server, and process the model by running the training data through the algorithm.</span></span>  
  
#### <a name="to-process-the-forecasting-model"></a><span data-ttu-id="697ab-155">处理预测模型</span><span class="sxs-lookup"><span data-stu-id="697ab-155">To process the forecasting model</span></span>  
  
1.  <span data-ttu-id="697ab-156">在的 "**挖掘模型**" 菜单上 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] ，选择 "**处理挖掘结构和所有模型**"。</span><span class="sxs-lookup"><span data-stu-id="697ab-156">On the **Mining Model** menu of [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], select **Process Mining Structure and All Models**.</span></span>  
  
2.  <span data-ttu-id="697ab-157">如果出现警告，询问您是否要生成和部署项目，请单击 **"是"**。</span><span class="sxs-lookup"><span data-stu-id="697ab-157">At the warning asking whether you want to build and deploy the project, click **Yes**.</span></span>  
  
3.  <span data-ttu-id="697ab-158">在 "**处理挖掘结构-预测**" 对话框中，单击 "**运行**"。</span><span class="sxs-lookup"><span data-stu-id="697ab-158">In the **Process Mining Structure - Forecasting** dialog box, click **Run**.</span></span>  
  
     <span data-ttu-id="697ab-159">"**处理进度**" 对话框将打开以显示有关模型处理的信息。</span><span class="sxs-lookup"><span data-stu-id="697ab-159">The **Process Progress** dialog box opens to display information about model processing.</span></span> <span data-ttu-id="697ab-160">模型处理可能需要一些时间。</span><span class="sxs-lookup"><span data-stu-id="697ab-160">Model processing may take some time.</span></span>  
  
4.  <span data-ttu-id="697ab-161">处理完成后，单击 "**关闭**" 退出 "**处理进度**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="697ab-161">After processing is complete, click **Close** to exit the **Process Progress** dialog box.</span></span>  
  
5.  <span data-ttu-id="697ab-162">再次单击 "**关闭**" 以退出 "**处理挖掘结构-预测**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="697ab-162">Click **Close** again to exit the **Process Mining Structure - Forecasting** dialog box.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="697ab-163">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="697ab-163">Next Task in Lesson</span></span>  
 [<span data-ttu-id="697ab-164">了解 &#40;中级数据挖掘教程的预测模型&#41;</span><span class="sxs-lookup"><span data-stu-id="697ab-164">Exploring the Forecasting Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-forecasting-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="697ab-165">另请参阅</span><span class="sxs-lookup"><span data-stu-id="697ab-165">See Also</span></span>  
 <span data-ttu-id="697ab-166">[Microsoft 时序算法技术参考](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="697ab-166">[Microsoft Time Series Algorithm Technical Reference](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md) </span></span>  
 <span data-ttu-id="697ab-167">[Microsoft 时序算法](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="697ab-167">[Microsoft Time Series Algorithm](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md) </span></span>  
 [<span data-ttu-id="697ab-168">处理要求和注意事项（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="697ab-168">Processing Requirements and Considerations &#40;Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  
