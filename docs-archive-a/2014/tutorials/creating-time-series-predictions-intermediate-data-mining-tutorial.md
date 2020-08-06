---
title: " (中级数据挖掘教程) 创建时序预测 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: fb22cffa-ac99-4d34-ac4a-9c93068e33e8
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a1175cdffd1512e0cb876b9565dd0727a9f094c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579437"
---
# <a name="creating-time-series-predictions-intermediate-data-mining-tutorial"></a><span data-ttu-id="54af4-102">创建时序预测（数据挖掘中级教程）</span><span class="sxs-lookup"><span data-stu-id="54af4-102">Creating Time Series Predictions (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="54af4-103">在本课前面的任务中，您已经创建了时序模型并浏览了结果。</span><span class="sxs-lookup"><span data-stu-id="54af4-103">In the previous tasks in this lesson, you created a time series model and explored the results.</span></span> <span data-ttu-id="54af4-104">默认情况下，[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 将始终为一个时序模型创建一组五 (5) 个预测，并将预测值作为预测图的一部分显示。</span><span class="sxs-lookup"><span data-stu-id="54af4-104">By default, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] always creates a set of five (5) predictions for a time series model and displays the predicted values as part of the forecasting chart.</span></span> <span data-ttu-id="54af4-105">但是，也可以通过生成数据挖掘扩展插件 (DMX) 预测查询，来创建预测。</span><span class="sxs-lookup"><span data-stu-id="54af4-105">However, you can also create forecasts by building Data Mining Extensions (DMX) prediction queries.</span></span>  
  
 <span data-ttu-id="54af4-106">在本任务中，您将创建一个预测查询，该查询生成的预测就是您在查看器中看到的同一预测。</span><span class="sxs-lookup"><span data-stu-id="54af4-106">In this task, you will create a prediction query that generates the same predictions that you saw in the viewer.</span></span> <span data-ttu-id="54af4-107">该任务假定您已经学完了“数据挖掘基础教程”中的课程，并且熟悉如何使用预测查询生成器。</span><span class="sxs-lookup"><span data-stu-id="54af4-107">This task assumes that you have already completed the lessons in the Basic Data Mining Tutorial and are familiar with how to use Prediction Query Builder.</span></span> <span data-ttu-id="54af4-108">现在，您将学习如何创建特定于时序模型的查询。</span><span class="sxs-lookup"><span data-stu-id="54af4-108">You will now learn how to create queries specific to time series models.</span></span>  
  
## <a name="creating-time-series-predictions"></a><span data-ttu-id="54af4-109">创建时序预测</span><span class="sxs-lookup"><span data-stu-id="54af4-109">Creating Time Series Predictions</span></span>  
 <span data-ttu-id="54af4-110">一般来说，创建预测查询的第一步是选择挖掘模型和输入表。</span><span class="sxs-lookup"><span data-stu-id="54af4-110">Typically, the first step in creating a prediction query is to select a mining model and input table.</span></span> <span data-ttu-id="54af4-111">但是，时序模型不需要为常规预测进行额外输入。</span><span class="sxs-lookup"><span data-stu-id="54af4-111">However, a time series model does not require additional input for a regular prediction.</span></span> <span data-ttu-id="54af4-112">因此，您在进行预测时并不需要指定新数据源，除非您要将数据添加到模型或替换数据。</span><span class="sxs-lookup"><span data-stu-id="54af4-112">Therefore, you do not need to specify a new source of data when making predictions, unless you are adding data to the model or replacing the data.</span></span>  
  
 <span data-ttu-id="54af4-113">在本课程中，您必须指定预测步骤数。</span><span class="sxs-lookup"><span data-stu-id="54af4-113">For this lesson, you must specify the number of prediction steps.</span></span> <span data-ttu-id="54af4-114">可以指定序列名称来获取针对产品和区域的特定组合的预测。</span><span class="sxs-lookup"><span data-stu-id="54af4-114">You can specify the series name, to get a prediction for a particular combination of a product and a region.</span></span>  
  
#### <a name="to-select-a-model-and-input-table"></a><span data-ttu-id="54af4-115">选择模型和输入表</span><span class="sxs-lookup"><span data-stu-id="54af4-115">To select a model and input table</span></span>  
  
1.  <span data-ttu-id="54af4-116">在数据挖掘设计器的 "**挖掘模型预测**" 选项卡上的 "**挖掘模型**" 框中，单击 "**选择模型**"。</span><span class="sxs-lookup"><span data-stu-id="54af4-116">On the **Mining Model Prediction** tab of the Data Mining Designer, in the **Mining Model** box, click **Select Model**.</span></span>  
  
2.  <span data-ttu-id="54af4-117">在 "**选择挖掘模型**" 对话框中，展开 "预测" 结构，从列表中选择 "**预测**" 模型，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="54af4-117">In the **Select Mining Model** dialog box, expand the Forecasting structure, select the **Forecasting** model from the list, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="54af4-118">忽略 "\*\*选择输入表 (s) \*\* " 框。</span><span class="sxs-lookup"><span data-stu-id="54af4-118">Ignore the **Select Input Table(s)** box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="54af4-119">对于时序模型，并不需要指定单独的输入，除非您要进行交叉预测。</span><span class="sxs-lookup"><span data-stu-id="54af4-119">For a time series model, you do not need to specify a separate input unless you are doing cross-prediction.</span></span>  
  
4.  <span data-ttu-id="54af4-120">在 "**源**" 列中，在 "**挖掘模型预测**" 选项卡上的网格中，单击第一个空行中的单元，然后选择 "**预测挖掘模型**"。</span><span class="sxs-lookup"><span data-stu-id="54af4-120">In the **Source** column, in the grid on the **Mining Model Prediction** tab, click the cell in the first empty row, and then select **Forecasting mining model**.</span></span>  
  
5.  <span data-ttu-id="54af4-121">在 "**字段**" 列中，选择 "**模型区域**"。</span><span class="sxs-lookup"><span data-stu-id="54af4-121">In the **Field** column, select **Model Region**.</span></span>  
  
     <span data-ttu-id="54af4-122">此操作可将序列标识符添加到预测查询中，以指示预测适用于的型号和区域的组合。</span><span class="sxs-lookup"><span data-stu-id="54af4-122">This action adds the series identifier to the prediction query to indicate the combination of model and region to which the prediction applies.</span></span>  
  
6.  <span data-ttu-id="54af4-123">单击 "**源**" 列中的下一个空行，然后选择 "**预测函数**"。</span><span class="sxs-lookup"><span data-stu-id="54af4-123">Click the next empty row in the **Source** column, and then select **Prediction Function**.</span></span>  
  
7.  <span data-ttu-id="54af4-124">在 "**字段**" 列中，选择**PredictTimeSeries**。</span><span class="sxs-lookup"><span data-stu-id="54af4-124">In the **Field** column, select **PredictTimeSeries**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="54af4-125">还可以将函数用于 `Predict` 时序模型。</span><span class="sxs-lookup"><span data-stu-id="54af4-125">You can also use the `Predict` function with time series models.</span></span> <span data-ttu-id="54af4-126">但在默认情况下，预测函数只为每个时序创建一个预测。</span><span class="sxs-lookup"><span data-stu-id="54af4-126">However, by default, the Predict function creates only one prediction for each series.</span></span> <span data-ttu-id="54af4-127">因此，若要指定多个预测步骤，必须使用**PredictTimeSeries**函数。</span><span class="sxs-lookup"><span data-stu-id="54af4-127">Therefore, to specify multiple prediction steps, you must use the **PredictTimeSeries** function.</span></span>  
  
8.  <span data-ttu-id="54af4-128">在 "**挖掘模型**" 窗格中，选择 "挖掘模型" 列、"**金额"。**</span><span class="sxs-lookup"><span data-stu-id="54af4-128">In the **Mining Model** pane, select the mining model column, **Amount.**</span></span> <span data-ttu-id="54af4-129">将 "数量" 拖动到前面添加的**PredictTimeSeries**函数的 "**条件/参数**" 框中。</span><span class="sxs-lookup"><span data-stu-id="54af4-129">Drag Amount to the **Criteria/Arguments** box for the **PredictTimeSeries** function that you added earlier.</span></span>  
  
9. <span data-ttu-id="54af4-130">单击 "**条件/参数**" 框，在字段名称后键入一个逗号，后跟**5**。</span><span class="sxs-lookup"><span data-stu-id="54af4-130">Click the **Criteria/Arguments** box, and type a comma, followed by **5**, after the field name.</span></span>  
  
     <span data-ttu-id="54af4-131">"**条件/参数**" 框中的文本现在应显示以下内容：</span><span class="sxs-lookup"><span data-stu-id="54af4-131">The text in the **Criteria/Arguments** box should now display the following:</span></span>  
  
     `[Forecasting].[Amount],5`  
  
10. <span data-ttu-id="54af4-132">在 "**别名**" 列中，键入 `PredictAmount` 。</span><span class="sxs-lookup"><span data-stu-id="54af4-132">In the **Alias** column, type `PredictAmount`.</span></span>  
  
11. <span data-ttu-id="54af4-133">单击 "**源**" 列中的下一个空行，然后再次选择 "**预测函数**"。</span><span class="sxs-lookup"><span data-stu-id="54af4-133">Click the next empty row in the **Source** column, and then select **Prediction Function** again.</span></span>  
  
12. <span data-ttu-id="54af4-134">在 "**字段**" 列中，选择**PredictTimeSeries**。</span><span class="sxs-lookup"><span data-stu-id="54af4-134">In the **Field** column, select **PredictTimeSeries**.</span></span>  
  
13. <span data-ttu-id="54af4-135">在 "**挖掘模型**" 窗格中，选择列数量，然后将其拖到第二个**PredictTimeSeries**函数的 "**条件/参数**" 框中。</span><span class="sxs-lookup"><span data-stu-id="54af4-135">In the **Mining Model** pane, select the column Quantity, and then drag it into the **Criteria/Arguments** box for the second **PredictTimeSeries** function.</span></span>  
  
14. <span data-ttu-id="54af4-136">单击 "**条件/参数**" 框，在字段名称后键入一个逗号，后跟**5**。</span><span class="sxs-lookup"><span data-stu-id="54af4-136">Click the **Criteria/Arguments** box, and type a comma, followed by **5**, after the field name.</span></span>  
  
     <span data-ttu-id="54af4-137">"**条件/参数**" 框中的文本现在应显示以下内容：</span><span class="sxs-lookup"><span data-stu-id="54af4-137">The text in the **Criteria/Arguments** box should now display the following:</span></span>  
  
     `[Forecasting].[ Quantity],5`  
  
15. <span data-ttu-id="54af4-138">在 "**别名**" 列中，键入 `PredictQuantity` 。</span><span class="sxs-lookup"><span data-stu-id="54af4-138">In the **Alias** column, type `PredictQuantity`.</span></span>  
  
16. <span data-ttu-id="54af4-139">单击 "**切换到查询结果视图**"。</span><span class="sxs-lookup"><span data-stu-id="54af4-139">Click **Switch to query result view**.</span></span>  
  
     <span data-ttu-id="54af4-140">查询结果以表格形式显示。</span><span class="sxs-lookup"><span data-stu-id="54af4-140">The results of the query are displayed in tabular format.</span></span>  
  
 <span data-ttu-id="54af4-141">请记住，您在查询生成器中创建了三个不同类型的结果，一个结果使用列中的值，另两个结果从预测函数中获取预测值。</span><span class="sxs-lookup"><span data-stu-id="54af4-141">Remember that you created three different types of results in the query builder, one that uses values from a column, and two that get predicted values from a prediction function.</span></span> <span data-ttu-id="54af4-142">因此，查询结果包含三个单独的列。</span><span class="sxs-lookup"><span data-stu-id="54af4-142">Therefore, the results of the query contain three separate columns.</span></span> <span data-ttu-id="54af4-143">第一列包含产品和区域组合的列表。</span><span class="sxs-lookup"><span data-stu-id="54af4-143">The first column contains the list of product and region combinations.</span></span> <span data-ttu-id="54af4-144">第二列和第三列都包含预测结构的嵌套表。</span><span class="sxs-lookup"><span data-stu-id="54af4-144">The second and third columns each contain a nested table of prediction results.</span></span> <span data-ttu-id="54af4-145">每个嵌套表都包含时间步长和预测值，如下表所示：</span><span class="sxs-lookup"><span data-stu-id="54af4-145">Each nested table contains the time step and predicted values, such as the following table:</span></span>  
  
 <span data-ttu-id="54af4-146">示例结果（金额被截断为两位小数）：</span><span class="sxs-lookup"><span data-stu-id="54af4-146">Example results (amounts are truncated to two decimal places):</span></span>  
  
 <span data-ttu-id="54af4-147">**M200 欧洲 PredictAmount**</span><span class="sxs-lookup"><span data-stu-id="54af4-147">**M200 Europe PredictAmount**</span></span>  
  
|<span data-ttu-id="54af4-148">$TIME</span><span class="sxs-lookup"><span data-stu-id="54af4-148">$TIME</span></span>|<span data-ttu-id="54af4-149">金额</span><span class="sxs-lookup"><span data-stu-id="54af4-149">Amount</span></span>|  
|-----------|------------|  
|<span data-ttu-id="54af4-150">7/25/2008</span><span class="sxs-lookup"><span data-stu-id="54af4-150">7/25/2008</span></span>|<span data-ttu-id="54af4-151">99978.00</span><span class="sxs-lookup"><span data-stu-id="54af4-151">99978.00</span></span>|  
|<span data-ttu-id="54af4-152">2008 年 8 月 25 日</span><span class="sxs-lookup"><span data-stu-id="54af4-152">8/25/2008</span></span>|<span data-ttu-id="54af4-153">145575.07</span><span class="sxs-lookup"><span data-stu-id="54af4-153">145575.07</span></span>|  
|<span data-ttu-id="54af4-154">9/25/2008</span><span class="sxs-lookup"><span data-stu-id="54af4-154">9/25/2008</span></span>|<span data-ttu-id="54af4-155">116835.19</span><span class="sxs-lookup"><span data-stu-id="54af4-155">116835.19</span></span>|  
|<span data-ttu-id="54af4-156">10/25/2008</span><span class="sxs-lookup"><span data-stu-id="54af4-156">10/25/2008</span></span>|<span data-ttu-id="54af4-157">116537.38</span><span class="sxs-lookup"><span data-stu-id="54af4-157">116537.38</span></span>|  
|<span data-ttu-id="54af4-158">11/25/2008</span><span class="sxs-lookup"><span data-stu-id="54af4-158">11/25/2008</span></span>|<span data-ttu-id="54af4-159">107760.55</span><span class="sxs-lookup"><span data-stu-id="54af4-159">107760.55</span></span>|  
  
 <span data-ttu-id="54af4-160">**M200 欧洲 PredictQuantity**</span><span class="sxs-lookup"><span data-stu-id="54af4-160">**M200 Europe PredictQuantity**</span></span>  
  
|<span data-ttu-id="54af4-161">$TIME</span><span class="sxs-lookup"><span data-stu-id="54af4-161">$TIME</span></span>|<span data-ttu-id="54af4-162">数量</span><span class="sxs-lookup"><span data-stu-id="54af4-162">Quantity</span></span>|  
|-----------|--------------|  
|<span data-ttu-id="54af4-163">7/25/2008</span><span class="sxs-lookup"><span data-stu-id="54af4-163">7/25/2008</span></span>|<span data-ttu-id="54af4-164">52</span><span class="sxs-lookup"><span data-stu-id="54af4-164">52</span></span>|  
|<span data-ttu-id="54af4-165">2008 年 8 月 25 日</span><span class="sxs-lookup"><span data-stu-id="54af4-165">8/25/2008</span></span>|<span data-ttu-id="54af4-166">67</span><span class="sxs-lookup"><span data-stu-id="54af4-166">67</span></span>|  
|<span data-ttu-id="54af4-167">9/25/2008</span><span class="sxs-lookup"><span data-stu-id="54af4-167">9/25/2008</span></span>|<span data-ttu-id="54af4-168">58</span><span class="sxs-lookup"><span data-stu-id="54af4-168">58</span></span>|  
|<span data-ttu-id="54af4-169">10/25/2008</span><span class="sxs-lookup"><span data-stu-id="54af4-169">10/25/2008</span></span>|<span data-ttu-id="54af4-170">57</span><span class="sxs-lookup"><span data-stu-id="54af4-170">57</span></span>|  
|<span data-ttu-id="54af4-171">11/25/2008</span><span class="sxs-lookup"><span data-stu-id="54af4-171">11/25/2008</span></span>|<span data-ttu-id="54af4-172">54</span><span class="sxs-lookup"><span data-stu-id="54af4-172">54</span></span>|  
  
 <span data-ttu-id="54af4-173">**M200 北美-PredictAmount**</span><span class="sxs-lookup"><span data-stu-id="54af4-173">**M200 North America - PredictAmount**</span></span>  
  
|<span data-ttu-id="54af4-174">$TIME</span><span class="sxs-lookup"><span data-stu-id="54af4-174">$TIME</span></span>|<span data-ttu-id="54af4-175">金额</span><span class="sxs-lookup"><span data-stu-id="54af4-175">Amount</span></span>|  
|-----------|------------|  
|<span data-ttu-id="54af4-176">7/25/2008</span><span class="sxs-lookup"><span data-stu-id="54af4-176">7/25/2008</span></span>|<span data-ttu-id="54af4-177">348533.93</span><span class="sxs-lookup"><span data-stu-id="54af4-177">348533.93</span></span>|  
|<span data-ttu-id="54af4-178">2008 年 8 月 25 日</span><span class="sxs-lookup"><span data-stu-id="54af4-178">8/25/2008</span></span>|<span data-ttu-id="54af4-179">340097.98</span><span class="sxs-lookup"><span data-stu-id="54af4-179">340097.98</span></span>|  
|<span data-ttu-id="54af4-180">9/25/2008</span><span class="sxs-lookup"><span data-stu-id="54af4-180">9/25/2008</span></span>|<span data-ttu-id="54af4-181">257986.19</span><span class="sxs-lookup"><span data-stu-id="54af4-181">257986.19</span></span>|  
|<span data-ttu-id="54af4-182">10/25/2008</span><span class="sxs-lookup"><span data-stu-id="54af4-182">10/25/2008</span></span>|<span data-ttu-id="54af4-183">374658.24</span><span class="sxs-lookup"><span data-stu-id="54af4-183">374658.24</span></span>|  
|<span data-ttu-id="54af4-184">11/25/2008</span><span class="sxs-lookup"><span data-stu-id="54af4-184">11/25/2008</span></span>|<span data-ttu-id="54af4-185">379241.44</span><span class="sxs-lookup"><span data-stu-id="54af4-185">379241.44</span></span>|  
  
 <span data-ttu-id="54af4-186">**M200 北美-PredictQuantity**</span><span class="sxs-lookup"><span data-stu-id="54af4-186">**M200 North America - PredictQuantity**</span></span>  
  
|<span data-ttu-id="54af4-187">$TIME</span><span class="sxs-lookup"><span data-stu-id="54af4-187">$TIME</span></span>|<span data-ttu-id="54af4-188">数量</span><span class="sxs-lookup"><span data-stu-id="54af4-188">Quantity</span></span>|  
|-----------|--------------|  
|<span data-ttu-id="54af4-189">7/25/2008</span><span class="sxs-lookup"><span data-stu-id="54af4-189">7/25/2008</span></span>|<span data-ttu-id="54af4-190">272</span><span class="sxs-lookup"><span data-stu-id="54af4-190">272</span></span>|  
|<span data-ttu-id="54af4-191">2008 年 8 月 25 日</span><span class="sxs-lookup"><span data-stu-id="54af4-191">8/25/2008</span></span>|<span data-ttu-id="54af4-192">152</span><span class="sxs-lookup"><span data-stu-id="54af4-192">152</span></span>|  
|<span data-ttu-id="54af4-193">9/25/2008</span><span class="sxs-lookup"><span data-stu-id="54af4-193">9/25/2008</span></span>|<span data-ttu-id="54af4-194">250</span><span class="sxs-lookup"><span data-stu-id="54af4-194">250</span></span>|  
|<span data-ttu-id="54af4-195">10/25/2008</span><span class="sxs-lookup"><span data-stu-id="54af4-195">10/25/2008</span></span>|<span data-ttu-id="54af4-196">181</span><span class="sxs-lookup"><span data-stu-id="54af4-196">181</span></span>|  
|<span data-ttu-id="54af4-197">11/25/2008</span><span class="sxs-lookup"><span data-stu-id="54af4-197">11/25/2008</span></span>|<span data-ttu-id="54af4-198">290</span><span class="sxs-lookup"><span data-stu-id="54af4-198">290</span></span>|  
  
> [!WARNING]  
>  <span data-ttu-id="54af4-199">在示例数据库中使用的日期对于此版本已更改。</span><span class="sxs-lookup"><span data-stu-id="54af4-199">The dates that are used in the sample database have changed for this release.</span></span> <span data-ttu-id="54af4-200">如果您在使用较早版本的示例数据，则可能会看到不同的结果。</span><span class="sxs-lookup"><span data-stu-id="54af4-200">If you are using an earlier version of the sample data, you might see different results.</span></span>  
  
## <a name="saving-the-prediction-results"></a><span data-ttu-id="54af4-201">保存预测结果</span><span class="sxs-lookup"><span data-stu-id="54af4-201">Saving the Prediction Results</span></span>  
 <span data-ttu-id="54af4-202">对于使用预测结果，有几个不同的选项可供您选择。</span><span class="sxs-lookup"><span data-stu-id="54af4-202">You have several different options for using the prediction results.</span></span> <span data-ttu-id="54af4-203">您可以平展结果，从“结果”视图复制数据，然后将数据粘贴到 Excel 工作表或其他文件中。</span><span class="sxs-lookup"><span data-stu-id="54af4-203">You can flatten the results, copy the data from the Results view, and paste it into an Excel worksheet or other file.</span></span>  
  
 <span data-ttu-id="54af4-204">为了简化保存结果的过程，数据挖掘设计器还提供将数据保存到数据源视图的功能。</span><span class="sxs-lookup"><span data-stu-id="54af4-204">To simplify the process of saving results, Data Mining Designer also provides the ability to save the data to a data source view.</span></span> <span data-ttu-id="54af4-205">将结果保存到数据源视图的功能仅在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中提供。</span><span class="sxs-lookup"><span data-stu-id="54af4-205">The functionality for saving results to a data source view is available only in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="54af4-206">结果只能以平展格式存储。</span><span class="sxs-lookup"><span data-stu-id="54af4-206">The results can only be stored in a flattened format.</span></span>  
  
#### <a name="to-flatten-the-results-in-the-results-pane"></a><span data-ttu-id="54af4-207">在“结果”窗格中平展结果</span><span class="sxs-lookup"><span data-stu-id="54af4-207">To flatten the results in the Results pane</span></span>  
  
1.  <span data-ttu-id="54af4-208">在预测查询生成器中，单击 "**切换到查询设计视图**"。</span><span class="sxs-lookup"><span data-stu-id="54af4-208">In the Prediction Query Builder, click **Switch to query design view**.</span></span>  
  
     <span data-ttu-id="54af4-209">该视图发生变化，允许手动编辑 DMX 查询文本。</span><span class="sxs-lookup"><span data-stu-id="54af4-209">The view changes to allow manual editing of the DMX query text.</span></span>  
  
2.  <span data-ttu-id="54af4-210">在 `FLATTENED` 关键字后键入 `SELECT` 关键字。</span><span class="sxs-lookup"><span data-stu-id="54af4-210">Type the `FLATTENED` keyword after the `SELECT` keyword.</span></span> <span data-ttu-id="54af4-211">完整的查询文本应该如下所示：</span><span class="sxs-lookup"><span data-stu-id="54af4-211">The complete query text should be as follows:</span></span>  
  
    ```  
    SELECT FLATTENED  
      [Forecasting].[Model Region],  
      (PredictTimeSeries([Forecasting].[Amount],5)) as [PredictAmount],  
      (PredictTimeSeries([Forecasting].[Quantity],5)) as [PredictQuantity]  
    FROM  
      [Forecasting]  
    ```  
  
3.  <span data-ttu-id="54af4-212">或者，您可以键入一个子句来限制结果，如下面的示例所示：</span><span class="sxs-lookup"><span data-stu-id="54af4-212">Optionally, you can type a clause to restrict the results, such as the following example:</span></span>  
  
    ```  
    SELECT FLATTENED  
      [Forecasting].[Model Region],  
      (PredictTimeSeries([Forecasting].[Amount],5)) as [PredictAmount],  
      (PredictTimeSeries([Forecasting].[Quantity],5)) as [PredictQuantity]  
    FROM  
      [Forecasting]  
    WHERE [Forecasting].[Model Region] = 'M200 North America'   
    OR [Forecasting].[Model Region] = 'M200 Europe'  
  
    ```  
  
4.  <span data-ttu-id="54af4-213">单击 "**切换到查询结果视图**"。</span><span class="sxs-lookup"><span data-stu-id="54af4-213">Click **Switch to query result view**.</span></span>  
  
#### <a name="to-export-prediction-query-results"></a><span data-ttu-id="54af4-214">导出预测查询结果</span><span class="sxs-lookup"><span data-stu-id="54af4-214">To export prediction query results</span></span>  
  
1.  <span data-ttu-id="54af4-215">单击 "**保存查询结果**"。</span><span class="sxs-lookup"><span data-stu-id="54af4-215">Click **Save query results**.</span></span>  
  
2.  <span data-ttu-id="54af4-216">在 "**保存数据挖掘查询结果**" 对话框中，选择 "**数据源**" [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="54af4-216">In the **Save Data Mining Query Result** dialog box, for **Data Source**, select [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)].</span></span> <span data-ttu-id="54af4-217">如果您希望将数据保存到不同的关系数据库，也可以创建数据源。</span><span class="sxs-lookup"><span data-stu-id="54af4-217">You can also create a data source if you want to save the data to a different relational database.</span></span>  
  
3.  <span data-ttu-id="54af4-218">在 "**表名称**" 列中，键入新的临时表名称，例如**测试预测**。</span><span class="sxs-lookup"><span data-stu-id="54af4-218">In the **Table Name** column, type a new temporary table name, such as **Test Predictions**.</span></span>  
  
4.  <span data-ttu-id="54af4-219">单击“ **保存**”。</span><span class="sxs-lookup"><span data-stu-id="54af4-219">Click **Save**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="54af4-220">若要查看您创建的表，请创建与您保存数据的实例的数据库引擎的连接，然后创建查询。</span><span class="sxs-lookup"><span data-stu-id="54af4-220">To view the table that you created, create a connection to the database engine of the instance where you saved the data, and create a query.</span></span>  
  
## <a name="conclusion"></a><span data-ttu-id="54af4-221">结论</span><span class="sxs-lookup"><span data-stu-id="54af4-221">Conclusion</span></span>  
 <span data-ttu-id="54af4-222">您学习了如何生成基本时序模型、解释预测和创建预测。</span><span class="sxs-lookup"><span data-stu-id="54af4-222">You have learned how to build a basic time series model, interpret the forecasts, and create predictions.</span></span>  
  
 <span data-ttu-id="54af4-223">本教程中的其余任务是可选的，它们介绍高级时序预测。</span><span class="sxs-lookup"><span data-stu-id="54af4-223">The remaining tasks in this tutorial are optional, and describe advanced time series predictions.</span></span> <span data-ttu-id="54af4-224">如果您决定继续，将学习如何将新数据添加到模型并基于扩展的序列创建预测。</span><span class="sxs-lookup"><span data-stu-id="54af4-224">If you decide to go on, you will learn how to add new data to your model and create predictions on the extended series.</span></span> <span data-ttu-id="54af4-225">您还将学习如何通过使用模型中的趋势但是使用新数据序列替换模型中的数据来执行交叉预测。</span><span class="sxs-lookup"><span data-stu-id="54af4-225">You will also learn how to perform cross-prediction, by using the trend in the model but replacing the data with a new series of data.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="54af4-226">下一课</span><span class="sxs-lookup"><span data-stu-id="54af4-226">Next Lesson</span></span>  
 [<span data-ttu-id="54af4-227">&#40;中级数据挖掘教程的高级时序预测&#41;</span><span class="sxs-lookup"><span data-stu-id="54af4-227">Advanced Time Series Predictions &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/advanced-time-series-predictions-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="54af4-228">另请参阅</span><span class="sxs-lookup"><span data-stu-id="54af4-228">See Also</span></span>  
 [<span data-ttu-id="54af4-229">时序模型查询示例</span><span class="sxs-lookup"><span data-stu-id="54af4-229">Time Series Model Query Examples</span></span>](../../2014/analysis-services/data-mining/time-series-model-query-examples.md)  
  
  
