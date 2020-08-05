---
title: 第5课：扩展时序模型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 7aad4946-c903-4e25-88b9-b087c20cb67d
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2716e985897f8115d189d9410b7cdb13fb1af291
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579912"
---
# <a name="lesson-5-extending-the-time-series-model"></a><span data-ttu-id="956c6-102">第 5 课：扩展时序模型</span><span class="sxs-lookup"><span data-stu-id="956c6-102">Lesson 5: Extending the Time Series Model</span></span>
  <span data-ttu-id="956c6-103">在 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Enterprise 中，可以向时序模型中添加新数据，并自动将新数据合并到模型中。</span><span class="sxs-lookup"><span data-stu-id="956c6-103">In [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Enterprise, you can add new data to a time series model and automatically incorporate the new data into the model.</span></span> <span data-ttu-id="956c6-104">您可以通过下列两种方式之一向时序挖掘模型添加新数据：</span><span class="sxs-lookup"><span data-stu-id="956c6-104">You add new data to a time series mining model in one of two ways:</span></span>  
  
-   <span data-ttu-id="956c6-105">使用 PREDICTION JOIN 将外部源中的数据联接到定型数据。</span><span class="sxs-lookup"><span data-stu-id="956c6-105">Use a PREDICTION JOIN to join data in an external source to the training data.</span></span>  
  
-   <span data-ttu-id="956c6-106">使用单独预测查询每次向数据提供一个切片。</span><span class="sxs-lookup"><span data-stu-id="956c6-106">Use a singleton prediction query to provide data one slice at a time.</span></span>  
  
 <span data-ttu-id="956c6-107">例如，假定您已经在几个月之前为现有销售数据的挖掘模型定型。</span><span class="sxs-lookup"><span data-stu-id="956c6-107">For example, assume that you trained the mining model on existing sales data some months ago.</span></span> <span data-ttu-id="956c6-108">当您获得新的销售数据时，您可能希望更新销售预测以合并新数据。</span><span class="sxs-lookup"><span data-stu-id="956c6-108">When you get new sales, you might want to update the sales predictions to incorporate the new data.</span></span> <span data-ttu-id="956c6-109">这可以通过一个步骤来完成，即提供新销售数字作为输入数据并基于复合数据集生成新预测。</span><span class="sxs-lookup"><span data-stu-id="956c6-109">You can do this in one step, by supplying the new sales figures as input data and generating new predictions based on the composite data set.</span></span>  
  
## <a name="making-predictions-with-extend_model_cases"></a><span data-ttu-id="956c6-110">使用 EXTEND_MODEL_CASES 进行预测</span><span class="sxs-lookup"><span data-stu-id="956c6-110">Making Predictions with EXTEND_MODEL_CASES</span></span>  
 <span data-ttu-id="956c6-111">下面是几个使用 EXTEND_MODEL_CASES 进行时序预测的一般示例。</span><span class="sxs-lookup"><span data-stu-id="956c6-111">The following are generic examples of a time series prediction using EXTEND_MODEL_CASES.</span></span> <span data-ttu-id="956c6-112">第一个示例使您能够从原始模型的最后一个时间步长开始指定预测数：</span><span class="sxs-lookup"><span data-stu-id="956c6-112">The first example enables you to specify the number of predictions starting from the last time step of the original model:</span></span>  
  
```  
SELECT [<model columns>,] PredictTimeSeries(<table column reference>, n, EXTEND_MODEL_CASES)   
FROM <mining model>  
PREDICTION JOIN <source query>  
[WHERE <criteria>]  
```  
  
 <span data-ttu-id="956c6-113">第二个示例使您能够指定预测的起始时间步长和结束时间步长。</span><span class="sxs-lookup"><span data-stu-id="956c6-113">The second example enables you to specify the time step where predictions should start, and where they should end.</span></span> <span data-ttu-id="956c6-114">当您扩展模型事例时，此选项非常重要，这是因为在默认情况下用于预测查询的时间步长始终从原始序列的末尾开始。</span><span class="sxs-lookup"><span data-stu-id="956c6-114">This option is important when you extend the model cases because, by default, the time steps used for prediction queries always start at the end of the original series.</span></span>  
  
```  
SELECT [<model columns>,] PredictTimeSeries(<table column reference>, n-start, n-end, EXTEND_MODEL_CASES)   
FROM <mining model>  
PREDICTION JOIN <source query>  
[WHERE <criteria>}  
```  
  
 <span data-ttu-id="956c6-115">在本教程中，您将创建两种查询。</span><span class="sxs-lookup"><span data-stu-id="956c6-115">In this tutorial, you will create both kinds of queries.</span></span>  
  
#### <a name="to-create-a-singleton-prediction-query-on-a-time-series-model"></a><span data-ttu-id="956c6-116">针对时序模型创建单独预测查询</span><span class="sxs-lookup"><span data-stu-id="956c6-116">To create a singleton prediction query on a time series model</span></span>  
  
1.  <span data-ttu-id="956c6-117">在**对象资源管理器**中，右键单击实例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，指向 "**新建查询**"，然后单击 " **DMX**"。</span><span class="sxs-lookup"><span data-stu-id="956c6-117">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="956c6-118">将打开查询编辑器，其中包含一个新的空白查询。</span><span class="sxs-lookup"><span data-stu-id="956c6-118">Query Editor opens and contains a new, blank query.</span></span>  
  
2.  <span data-ttu-id="956c6-119">将单独语句的一般示例复制到空白查询中。</span><span class="sxs-lookup"><span data-stu-id="956c6-119">Copy the generic example of the singleton statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="956c6-120">将</span><span class="sxs-lookup"><span data-stu-id="956c6-120">Replace the following:</span></span>  
  
    ```  
    SELECT [<model columns>,] PredictTimeSeries(<table column reference>, n, EXTEND_MODEL_CASES)   
    ```  
  
     <span data-ttu-id="956c6-121">替换为：</span><span class="sxs-lookup"><span data-stu-id="956c6-121">with:</span></span>  
  
    ```  
    SELECT [Model Region],  
    PredictTimeSeries([Quantity],6, EXTEND_MODEL_CASES) AS PredictQty  
    ```  
  
     <span data-ttu-id="956c6-122">第一行从模型中检索用来标识序列的值。</span><span class="sxs-lookup"><span data-stu-id="956c6-122">The first line retrieves a value from the model that identifies the series.</span></span>  
  
     <span data-ttu-id="956c6-123">第二行包含预测函数，该函数针对 Quantity 获得 6 个预测。</span><span class="sxs-lookup"><span data-stu-id="956c6-123">The second line contains the prediction function, which gets 6 predictions for Quantity.</span></span> <span data-ttu-id="956c6-124">系统会向预测结果列分配一个别名 (`PredictQty`)，使结果更易于理解。</span><span class="sxs-lookup"><span data-stu-id="956c6-124">An alias, `PredictQty`, is assigned to the prediction result column to make it easier to understand the results.</span></span>  
  
4.  <span data-ttu-id="956c6-125">将</span><span class="sxs-lookup"><span data-stu-id="956c6-125">Replace the following:</span></span>  
  
    ```  
    FROM <mining model>  
    ```  
  
     <span data-ttu-id="956c6-126">替换为：</span><span class="sxs-lookup"><span data-stu-id="956c6-126">with:</span></span>  
  
    ```  
    FROM [Forecasting_MIXED]  
    ```  
  
5.  <span data-ttu-id="956c6-127">将</span><span class="sxs-lookup"><span data-stu-id="956c6-127">Replace the following:</span></span>  
  
    ```  
    PREDICTION JOIN <source query>  
    ```  
  
     <span data-ttu-id="956c6-128">替换为：</span><span class="sxs-lookup"><span data-stu-id="956c6-128">with:</span></span>  
  
    ```  
    NATURAL PREDICTION JOIN   
    (  
       SELECT 1 AS [Reporting Date],  
       '10' AS [Quantity],  
       'M200 Europe' AS [Model Region]  
       UNION SELECT  
       2 AS [Reporting Date],  
       15 AS [Quantity]),  
       'M200 Europe' AS [Model Region]  
    ) AS t  
    ```  
  
6.  <span data-ttu-id="956c6-129">将</span><span class="sxs-lookup"><span data-stu-id="956c6-129">Replace the following:</span></span>  
  
    ```  
    [WHERE <criteria>]  
    ```  
  
     <span data-ttu-id="956c6-130">替换为：</span><span class="sxs-lookup"><span data-stu-id="956c6-130">with:</span></span>  
  
    ```  
    WHERE [ModelRegion] = 'M200 Europe' OR  
    [ModelRegion] = 'M200 Pacific'  
    ```  
  
     <span data-ttu-id="956c6-131">现在，完整的语句应该如下所示：</span><span class="sxs-lookup"><span data-stu-id="956c6-131">The complete statement should now be as follows:</span></span>  
  
    ```  
    SELECT [Model Region],  
    PredictTimeSeries([Quantity],6, EXTEND_MODEL_CASES) AS PredictQty  
    FROM  
       [Forecasting_MIXED]  
    NATURAL PREDICTION JOIN   
       SELECT 1 AS [ReportingDate],  
      '10' AS [Quantity],  
      'M200 Europe' AS [ModelRegion]  
    UNION SELECT  
      2 AS [ReportingDate],  
      15 AS [Quantity]),  
      'M200 Europe' AS [ModelRegion]  
    ) AS t  
    WHERE [ModelRegion] = 'M200 Europe' OR  
    [ModelRegion] = 'M200 Pacific'  
    ```  
  
7.  <span data-ttu-id="956c6-132">在 "**文件**" 菜单上，单击 "**将 DMXQuery1 另存为**"。</span><span class="sxs-lookup"><span data-stu-id="956c6-132">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
8.  <span data-ttu-id="956c6-133">在 "**另存为**" 对话框中，浏览到相应的文件夹，并将该文件命名为 `Singleton_TimeSeries_Query.dmx` 。</span><span class="sxs-lookup"><span data-stu-id="956c6-133">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Singleton_TimeSeries_Query.dmx`.</span></span>  
  
9. <span data-ttu-id="956c6-134">在工具栏上，单击 "**执行**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="956c6-134">On the toolbar, click the **Execute** button.</span></span>  
  
     <span data-ttu-id="956c6-135">该查询将返回 Europe 和 Pacific 地区 M200 自行车的销售量预测。</span><span class="sxs-lookup"><span data-stu-id="956c6-135">The query returns predictions of sales quantity for the M200 bicycle in the Europe and Pacific regions.</span></span>  
  
## <a name="understanding-prediction-start-with-extend_model_cases"></a><span data-ttu-id="956c6-136">了解以 EXTEND_MODEL_CASES 开始的预测</span><span class="sxs-lookup"><span data-stu-id="956c6-136">Understanding Prediction Start with EXTEND_MODEL_CASES</span></span>  
 <span data-ttu-id="956c6-137">现在，您已经基于原始模型用新数据创建了预测，现在可以对结果进行比较，以了解销售数据更新对预测的影响。</span><span class="sxs-lookup"><span data-stu-id="956c6-137">Now that you have created predictions based on the original model, and with new data, you can compare the results to see how updating the sales data affects the predictions.</span></span> <span data-ttu-id="956c6-138">在这样做之前，请检查刚创建的代码，并注意以下事项：</span><span class="sxs-lookup"><span data-stu-id="956c6-138">Before you do so, review the code that you just created, and notice the following:</span></span>  
  
-   <span data-ttu-id="956c6-139">您仅为 Europe 地区提供了新数据。</span><span class="sxs-lookup"><span data-stu-id="956c6-139">You supplied new data for only the Europe region.</span></span>  
  
-   <span data-ttu-id="956c6-140">您只提供了两个月的新数据。</span><span class="sxs-lookup"><span data-stu-id="956c6-140">You supplied only two months' worth of new data.</span></span>  
  
 <span data-ttu-id="956c6-141">下表显示了为 M200 Europe 提供的新值对预测的影响。</span><span class="sxs-lookup"><span data-stu-id="956c6-141">The following table shows how the new values supplied for M200 Europe affect predictions.</span></span> <span data-ttu-id="956c6-142">您没有为 Pacific 地区的 M200 产品提供任何新数据，只是为了进行比较而提供此序列：</span><span class="sxs-lookup"><span data-stu-id="956c6-142">You did not provide any new data for the M200 product in the Pacific region, but this series is presented for comparison:</span></span>  
  
 <span data-ttu-id="956c6-143">**产品和区域： M200 欧洲**</span><span class="sxs-lookup"><span data-stu-id="956c6-143">**Product and Region: M200 Europe**</span></span>  
  
|||||  
|-|-|-|-|  
|||<span data-ttu-id="956c6-144">现有模型 (`PredictTimeSeries`)</span><span class="sxs-lookup"><span data-stu-id="956c6-144">Existing model (`PredictTimeSeries`)</span></span>|<span data-ttu-id="956c6-145">具有更新销售数据的模型（具有 `PredictTimeSeries` 的 `EXTEND_MODEL_CASES`）</span><span class="sxs-lookup"><span data-stu-id="956c6-145">Model with updated sales data (`PredictTimeSeries` with `EXTEND_MODEL_CASES`)</span></span>|  
|<span data-ttu-id="956c6-146">M200 Europe</span><span class="sxs-lookup"><span data-stu-id="956c6-146">M200 Europe</span></span>|<span data-ttu-id="956c6-147">7/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="956c6-147">7/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="956c6-148">77</span><span class="sxs-lookup"><span data-stu-id="956c6-148">77</span></span>|<span data-ttu-id="956c6-149">10</span><span class="sxs-lookup"><span data-stu-id="956c6-149">10</span></span>|  
|<span data-ttu-id="956c6-150">M200 Europe</span><span class="sxs-lookup"><span data-stu-id="956c6-150">M200 Europe</span></span>|<span data-ttu-id="956c6-151">8/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="956c6-151">8/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="956c6-152">64</span><span class="sxs-lookup"><span data-stu-id="956c6-152">64</span></span>|<span data-ttu-id="956c6-153">15</span><span class="sxs-lookup"><span data-stu-id="956c6-153">15</span></span>|  
|<span data-ttu-id="956c6-154">M200 Europe</span><span class="sxs-lookup"><span data-stu-id="956c6-154">M200 Europe</span></span>|<span data-ttu-id="956c6-155">9/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="956c6-155">9/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="956c6-156">59</span><span class="sxs-lookup"><span data-stu-id="956c6-156">59</span></span>|<span data-ttu-id="956c6-157">72</span><span class="sxs-lookup"><span data-stu-id="956c6-157">72</span></span>|  
|<span data-ttu-id="956c6-158">M200 Europe</span><span class="sxs-lookup"><span data-stu-id="956c6-158">M200 Europe</span></span>|<span data-ttu-id="956c6-159">10/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="956c6-159">10/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="956c6-160">56</span><span class="sxs-lookup"><span data-stu-id="956c6-160">56</span></span>|<span data-ttu-id="956c6-161">69</span><span class="sxs-lookup"><span data-stu-id="956c6-161">69</span></span>|  
|<span data-ttu-id="956c6-162">M200 Europe</span><span class="sxs-lookup"><span data-stu-id="956c6-162">M200 Europe</span></span>|<span data-ttu-id="956c6-163">11/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="956c6-163">11/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="956c6-164">56</span><span class="sxs-lookup"><span data-stu-id="956c6-164">56</span></span>|<span data-ttu-id="956c6-165">68</span><span class="sxs-lookup"><span data-stu-id="956c6-165">68</span></span>|  
|<span data-ttu-id="956c6-166">M200 Europe</span><span class="sxs-lookup"><span data-stu-id="956c6-166">M200 Europe</span></span>|<span data-ttu-id="956c6-167">12/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="956c6-167">12/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="956c6-168">74</span><span class="sxs-lookup"><span data-stu-id="956c6-168">74</span></span>|<span data-ttu-id="956c6-169">89</span><span class="sxs-lookup"><span data-stu-id="956c6-169">89</span></span>|  
  
 <span data-ttu-id="956c6-170">**产品和区域： M200 太平洋**</span><span class="sxs-lookup"><span data-stu-id="956c6-170">**Product and Region: M200 Pacific**</span></span>  
  
|||||  
|-|-|-|-|  
|||<span data-ttu-id="956c6-171">现有模型 (`PredictTimeSeries`)</span><span class="sxs-lookup"><span data-stu-id="956c6-171">Existing model (`PredictTimeSeries`)</span></span>|<span data-ttu-id="956c6-172">具有更新销售数据的模型（具有 `PredictTimeSeries` 的 `EXTEND_MODEL_CASES`）</span><span class="sxs-lookup"><span data-stu-id="956c6-172">Model with updated sales data (`PredictTimeSeries` with `EXTEND_MODEL_CASES`)</span></span>|  
|<span data-ttu-id="956c6-173">M200 Pacific</span><span class="sxs-lookup"><span data-stu-id="956c6-173">M200 Pacific</span></span>|<span data-ttu-id="956c6-174">7/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="956c6-174">7/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="956c6-175">41</span><span class="sxs-lookup"><span data-stu-id="956c6-175">41</span></span>|<span data-ttu-id="956c6-176">41</span><span class="sxs-lookup"><span data-stu-id="956c6-176">41</span></span>|  
|<span data-ttu-id="956c6-177">M200 Pacific</span><span class="sxs-lookup"><span data-stu-id="956c6-177">M200 Pacific</span></span>|<span data-ttu-id="956c6-178">8/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="956c6-178">8/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="956c6-179">44</span><span class="sxs-lookup"><span data-stu-id="956c6-179">44</span></span>|<span data-ttu-id="956c6-180">44</span><span class="sxs-lookup"><span data-stu-id="956c6-180">44</span></span>|  
|<span data-ttu-id="956c6-181">M200 Pacific</span><span class="sxs-lookup"><span data-stu-id="956c6-181">M200 Pacific</span></span>|<span data-ttu-id="956c6-182">9/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="956c6-182">9/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="956c6-183">38</span><span class="sxs-lookup"><span data-stu-id="956c6-183">38</span></span>|<span data-ttu-id="956c6-184">38</span><span class="sxs-lookup"><span data-stu-id="956c6-184">38</span></span>|  
|<span data-ttu-id="956c6-185">M200 Pacific</span><span class="sxs-lookup"><span data-stu-id="956c6-185">M200 Pacific</span></span>|<span data-ttu-id="956c6-186">10/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="956c6-186">10/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="956c6-187">41</span><span class="sxs-lookup"><span data-stu-id="956c6-187">41</span></span>|<span data-ttu-id="956c6-188">41</span><span class="sxs-lookup"><span data-stu-id="956c6-188">41</span></span>|  
|<span data-ttu-id="956c6-189">M200 Pacific</span><span class="sxs-lookup"><span data-stu-id="956c6-189">M200 Pacific</span></span>|<span data-ttu-id="956c6-190">11/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="956c6-190">11/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="956c6-191">36</span><span class="sxs-lookup"><span data-stu-id="956c6-191">36</span></span>|<span data-ttu-id="956c6-192">36</span><span class="sxs-lookup"><span data-stu-id="956c6-192">36</span></span>|  
|<span data-ttu-id="956c6-193">M200 Pacific</span><span class="sxs-lookup"><span data-stu-id="956c6-193">M200 Pacific</span></span>|<span data-ttu-id="956c6-194">12/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="956c6-194">12/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="956c6-195">39</span><span class="sxs-lookup"><span data-stu-id="956c6-195">39</span></span>|<span data-ttu-id="956c6-196">39</span><span class="sxs-lookup"><span data-stu-id="956c6-196">39</span></span>|  
  
 <span data-ttu-id="956c6-197">从这些结果中，可以得出以下两个结论：</span><span class="sxs-lookup"><span data-stu-id="956c6-197">From these results, you can see two things:</span></span>  
  
-   <span data-ttu-id="956c6-198">M200 Europe 序列的前两个预测与您提供的新数据完全相同。</span><span class="sxs-lookup"><span data-stu-id="956c6-198">The first two predictions for the M200 Europe series are exactly the same as the new data you supplied.</span></span> <span data-ttu-id="956c6-199">在设计上，Analysis Services 返回实际的新数据点，而不进行预测。</span><span class="sxs-lookup"><span data-stu-id="956c6-199">By design, Analysis Services returns the actual new data points instead of making a prediction.</span></span> <span data-ttu-id="956c6-200">这是因为您扩展模型事例时，用于预测查询的时间步长始终从原始序列的末尾开始。</span><span class="sxs-lookup"><span data-stu-id="956c6-200">That is because when you extend the model cases, the time steps used for prediction queries always start at the end of the original series.</span></span> <span data-ttu-id="956c6-201">因此，如果添加两个新数据点，返回的前两个预测将会与新数据重叠。</span><span class="sxs-lookup"><span data-stu-id="956c6-201">Therefore, if you add two new data points, the first two predictions returned overlap with the new data.</span></span>  
  
-   <span data-ttu-id="956c6-202">用完所有新数据点之后，[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 将基于更新后的模型进行预测。</span><span class="sxs-lookup"><span data-stu-id="956c6-202">After all the new data points are used up, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] makes predictions based on the updated model.</span></span> <span data-ttu-id="956c6-203">因此，可以看出，从 2004 年 9 月份开始，基于原始模型的 M200 Europe 预测（位于左列）和基于使用 EXTEND_MODEL_CASES 的模型的 M200 Europe 预测（位于右侧）之间的区别。</span><span class="sxs-lookup"><span data-stu-id="956c6-203">Therefore, starting in September 2005, you can see the difference between predictions for M200 Europe from the original model, in the left-hand column, and the model that uses EXTEND_MODEL_CASES, in the right-hand column.</span></span> <span data-ttu-id="956c6-204">由于模型用新数据进行了更新，因此预测有所不同。</span><span class="sxs-lookup"><span data-stu-id="956c6-204">The predictions are different because the model has been updated with the new data.</span></span>  
  
## <a name="using-start-and-end-time-steps-to-control-predictions"></a><span data-ttu-id="956c6-205">使用开始时间步长和结束时间步长控制预测</span><span class="sxs-lookup"><span data-stu-id="956c6-205">Using Start and End Time Steps to Control Predictions</span></span>  
 <span data-ttu-id="956c6-206">扩展模型时，新数据始终附加到序列的末尾。</span><span class="sxs-lookup"><span data-stu-id="956c6-206">When you extend a model, the new data is always attached to the end of the series.</span></span> <span data-ttu-id="956c6-207">但是，为了进行预测，用于预测查询的时间段始终从原始序列的末尾开始。</span><span class="sxs-lookup"><span data-stu-id="956c6-207">However, for the purpose of prediction, the time slices used for prediction queries start at the end of the original series.</span></span> <span data-ttu-id="956c6-208">如果您只想在添加新数据时获得新预测，则必须将起始点指定为许多时间段。</span><span class="sxs-lookup"><span data-stu-id="956c6-208">If you want to obtain only the new predictions when you add the new data, you must specify the starting point as a number of time slices.</span></span> <span data-ttu-id="956c6-209">例如，如果要添加两个新数据点并希望进行四个新预测，您需要执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="956c6-209">For example, if you are adding two new data points and want to make four new predictions, you would do the following:</span></span>  
  
-   <span data-ttu-id="956c6-210">针对时序模型创建一个 PREDICTION JOIN，然后指定两个月的新数据。</span><span class="sxs-lookup"><span data-stu-id="956c6-210">Create a PREDICTION JOIN on a time series model, and specify two months of new data.</span></span>  
  
-   <span data-ttu-id="956c6-211">请求对四个时间段进行预测，其中起点是时间片 3，终点是时间片 6。</span><span class="sxs-lookup"><span data-stu-id="956c6-211">Request predictions for four time slices, where the starting point is 3, and the ending point is time slice 6.</span></span>  
  
 <span data-ttu-id="956c6-212">换言之，如果您的新数据包含 n 个时间段，并且您请求对时间步长1至 n 进行预测，则预测将与新数据的时间段一致。</span><span class="sxs-lookup"><span data-stu-id="956c6-212">In other words, if your new data contains n time slices, and you request predictions for time steps 1 through n, the predictions will coincide with the same period as the new data.</span></span> <span data-ttu-id="956c6-213">若要获取对数据未覆盖的时间段的新预测，您必须从新数据序列之后的时间段 n+1 处开始预测，或者确保您请求了其他的时间段。</span><span class="sxs-lookup"><span data-stu-id="956c6-213">To get new predictions for a time periods not covered by your data, you must either start predictions at the time slice n+1 after the new data series, or make sure that you request additional time slices.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="956c6-214">添加新数据时不能进行历史预测。</span><span class="sxs-lookup"><span data-stu-id="956c6-214">You cannot make historical predictions when you add new data.</span></span>  
  
 <span data-ttu-id="956c6-215">下面的示例显示了一条 DMX 语句，使用该语句可仅获得对上例中两个序列的新预测。</span><span class="sxs-lookup"><span data-stu-id="956c6-215">The following example shows the DMX statement that lets you get only the new predictions for the two series in the previous example.</span></span>  
  
```  
SELECT [Model Region],  
PredictTimeSeries([Quantity],3,6, EXTEND_MODEL_CASES) AS PredictQty  
FROM  
   [Forecasting_MIXED]  
NATURAL PREDICTION JOIN   
   SELECT 1 AS [ReportingDate],  
  '10' AS [Quantity],  
  'M200 Europe' AS [ModelRegion]  
UNION SELECT  
  2 AS [ReportingDate],  
  15 AS [Quantity]),  
  'M200 Europe' AS [ModelRegion]  
) AS t  
WHERE [ModelRegion] = 'M200 Europe'  
```  
  
 <span data-ttu-id="956c6-216">预测结果从时间段 3 开始，该时间段在您提供的 2 个月的新数据之后。</span><span class="sxs-lookup"><span data-stu-id="956c6-216">The prediction results start at time slice 3, which is after the 2 months of new data that you supplied.</span></span>  
  
 <span data-ttu-id="956c6-217">**产品和区域： M200 欧洲**</span><span class="sxs-lookup"><span data-stu-id="956c6-217">**Product and Region: M200 Europe**</span></span>  
  
 <span data-ttu-id="956c6-218">具有更新数据的模型（具有 EXTEND_MODEL_CASES 的 PredictTimeSeries）</span><span class="sxs-lookup"><span data-stu-id="956c6-218">Model with updated data (PredictTimeSeries with EXTEND_MODEL_CASES)</span></span>  
  
||||  
|-|-|-|  
|<span data-ttu-id="956c6-219">M200 Europe</span><span class="sxs-lookup"><span data-stu-id="956c6-219">M200 Europe</span></span>|<span data-ttu-id="956c6-220">9/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="956c6-220">9/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="956c6-221">72</span><span class="sxs-lookup"><span data-stu-id="956c6-221">72</span></span>|  
|<span data-ttu-id="956c6-222">M200 Europe</span><span class="sxs-lookup"><span data-stu-id="956c6-222">M200 Europe</span></span>|<span data-ttu-id="956c6-223">10/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="956c6-223">10/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="956c6-224">69</span><span class="sxs-lookup"><span data-stu-id="956c6-224">69</span></span>|  
|<span data-ttu-id="956c6-225">M200 Europe</span><span class="sxs-lookup"><span data-stu-id="956c6-225">M200 Europe</span></span>|<span data-ttu-id="956c6-226">11/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="956c6-226">11/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="956c6-227">68</span><span class="sxs-lookup"><span data-stu-id="956c6-227">68</span></span>|  
|<span data-ttu-id="956c6-228">M200 Europe</span><span class="sxs-lookup"><span data-stu-id="956c6-228">M200 Europe</span></span>|<span data-ttu-id="956c6-229">12/25/2008 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="956c6-229">12/25/2008 12:00:00 AM</span></span>|<span data-ttu-id="956c6-230">89</span><span class="sxs-lookup"><span data-stu-id="956c6-230">89</span></span>|  
  
## <a name="making-predictions-with-replace_model_cases"></a><span data-ttu-id="956c6-231">使用 REPLACE_MODEL_CASES 进行预测</span><span class="sxs-lookup"><span data-stu-id="956c6-231">Making Predictions with REPLACE_MODEL_CASES</span></span>  
 <span data-ttu-id="956c6-232">如果您想对一组事例的某个模型定型，然后将该模型应用到不同的数据序列，则替换模型事例非常有用。</span><span class="sxs-lookup"><span data-stu-id="956c6-232">Replacing the model cases is useful when you want to train a model on one set of cases and then apply that model to a different data series.</span></span> <span data-ttu-id="956c6-233">[第2课：生成预测方案 &#40;中级数据挖掘教程&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)中提供了此方案的详细演练。</span><span class="sxs-lookup"><span data-stu-id="956c6-233">A detailed walkthrough of this scenario is presented in [Lesson 2: Building a Forecasting Scenario &#40;Intermediate Data Mining Tutorial&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="956c6-234">另请参阅</span><span class="sxs-lookup"><span data-stu-id="956c6-234">See Also</span></span>  
 <span data-ttu-id="956c6-235">[时序模型查询示例](../../2014/analysis-services/data-mining/time-series-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="956c6-235">[Time Series Model Query Examples](../../2014/analysis-services/data-mining/time-series-model-query-examples.md) </span></span>  
 [<span data-ttu-id="956c6-236">PredictTimeSeries (DMX)</span><span class="sxs-lookup"><span data-stu-id="956c6-236">PredictTimeSeries &#40;DMX&#41;</span></span>](/sql/dmx/predicttimeseries-dmx)  
  
  
