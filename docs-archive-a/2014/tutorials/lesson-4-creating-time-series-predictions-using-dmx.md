---
title: 第4课：使用 DMX 创建时序预测 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 6b883e43-209d-489a-8dc3-9349f88acae8
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 772e5f5f71ca82dd18fec48730522c80e907414f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682458"
---
# <a name="lesson-4-creating-time-series-predictions-using-dmx"></a><span data-ttu-id="d52cc-102">第 4 课：使用 DMX 创建时序预测</span><span class="sxs-lookup"><span data-stu-id="d52cc-102">Lesson 4: Creating Time Series Predictions Using DMX</span></span>
  <span data-ttu-id="d52cc-103">在本课和下一课中，您将使用数据挖掘扩展插件 (DMX) 基于您在第1课中创建的时序模型创建不同类型的预测[：创建时序挖掘模型和挖掘结构](../../2014/tutorials/lesson-1-creating-a-time-series-mining-model-and-mining-structure.md)和[第2课：向时序挖掘结构中添加挖掘模型](../../2014/tutorials/lesson-2-adding-mining-models-to-the-time-series-mining-structure.md)。</span><span class="sxs-lookup"><span data-stu-id="d52cc-103">In this lesson and the following lesson, you will use Data Mining Extensions (DMX) to create different types of predictions based on the time series models that you created in [Lesson 1: Creating a Time Series Mining Model and Mining Structure](../../2014/tutorials/lesson-1-creating-a-time-series-mining-model-and-mining-structure.md) and [Lesson 2: Adding Mining Models to the Time Series Mining Structure](../../2014/tutorials/lesson-2-adding-mining-models-to-the-time-series-mining-structure.md).</span></span>  
  
 <span data-ttu-id="d52cc-104">使用时序模型，可以通过许多选项来进行预测：</span><span class="sxs-lookup"><span data-stu-id="d52cc-104">With a time series model, you have many options for making predictions:</span></span>  
  
-   <span data-ttu-id="d52cc-105">使用挖掘模型中现有的模式和数据</span><span class="sxs-lookup"><span data-stu-id="d52cc-105">Use the existing patterns and data in the mining model</span></span>  
  
-   <span data-ttu-id="d52cc-106">使用挖掘模型中的现有模式但提供新数据</span><span class="sxs-lookup"><span data-stu-id="d52cc-106">Use the existing patterns in the mining model but supply new data</span></span>  
  
-   <span data-ttu-id="d52cc-107">在模型中添加新数据或者更新模型。</span><span class="sxs-lookup"><span data-stu-id="d52cc-107">Add new data to the model or update the model.</span></span>  
  
 <span data-ttu-id="d52cc-108">下面概述了进行这些类型的预测所需的语法：</span><span class="sxs-lookup"><span data-stu-id="d52cc-108">The syntax for making these prediction types is summarized below:</span></span>  
  
 <span data-ttu-id="d52cc-109">默认的序列预测</span><span class="sxs-lookup"><span data-stu-id="d52cc-109">Default time series prediction</span></span>  
 <span data-ttu-id="d52cc-110">使用[PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx)从定型挖掘模型返回指定数量的预测。</span><span class="sxs-lookup"><span data-stu-id="d52cc-110">Use [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx) to return the specified number of predictions from the trained mining model.</span></span>  
  
 <span data-ttu-id="d52cc-111">有关示例，请参阅[PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx)或[时序模型查询示例](../../2014/analysis-services/data-mining/time-series-model-query-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="d52cc-111">For example, see [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx) or [Time Series Model Query Examples](../../2014/analysis-services/data-mining/time-series-model-query-examples.md).</span></span>  
  
 <span data-ttu-id="d52cc-112">EXTEND_MODEL_CASES</span><span class="sxs-lookup"><span data-stu-id="d52cc-112">EXTEND_MODEL_CASES</span></span>  
 <span data-ttu-id="d52cc-113">使用带有 EXTEND_MODEL_CASES 参数的[PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx)来添加新数据、扩展序列，并基于更新后的挖掘模型创建预测。</span><span class="sxs-lookup"><span data-stu-id="d52cc-113">Use [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx) with the EXTEND_MODEL_CASES argument to add new data, extend the series, and create predictions based on the updated mining model.</span></span>  
  
 <span data-ttu-id="d52cc-114">本教程包含有关如何使用 EXTEND_MODEL_CASES 的示例。</span><span class="sxs-lookup"><span data-stu-id="d52cc-114">This tutorial contains an example of how to use EXTEND_MODEL_CASES.</span></span>  
  
 <span data-ttu-id="d52cc-115">REPLACE_MODEL_CASES</span><span class="sxs-lookup"><span data-stu-id="d52cc-115">REPLACE_MODEL_CASES</span></span>  
 <span data-ttu-id="d52cc-116">使用带有 REPLACE_MODEL_CASES 参数的[PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx)将原始数据替换为新的数据系列，然后基于将挖掘模型中的模式应用于新数据序列来创建预测。</span><span class="sxs-lookup"><span data-stu-id="d52cc-116">Use [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx) with the REPLACE_MODEL_CASES argument to replace the original data with a new data series, and then create predictions based on applying the patterns in the mining model to the new data series.</span></span>  
  
 <span data-ttu-id="d52cc-117">有关如何使用 REPLACE_MODEL_CASES 的示例，请参阅[第2课： &#40;中级数据挖掘教程&#41;生成预测方案](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="d52cc-117">For an example of how to use REPLACE_MODEL_CASES, see [Lesson 2: Building a Forecasting Scenario &#40;Intermediate Data Mining Tutorial&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md).</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="d52cc-118">课程任务</span><span class="sxs-lookup"><span data-stu-id="d52cc-118">Lesson Tasks</span></span>  
 <span data-ttu-id="d52cc-119">您将在本课中执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="d52cc-119">You will perform the following tasks in this lesson:</span></span>  
  
-   <span data-ttu-id="d52cc-120">创建一个查询，基于现有数据获得默认预测。</span><span class="sxs-lookup"><span data-stu-id="d52cc-120">Create a query to get the default predictions based on existing data.</span></span>  
  
 <span data-ttu-id="d52cc-121">在下一课中，您将执行下列相关任务：</span><span class="sxs-lookup"><span data-stu-id="d52cc-121">In the following lesson you will perform the following related tasks:</span></span>  
  
-   <span data-ttu-id="d52cc-122">创建一个查询，提供新数据并获得更新的预测。</span><span class="sxs-lookup"><span data-stu-id="d52cc-122">Create a query to supply new data and get updated predictions.</span></span>  
  
 <span data-ttu-id="d52cc-123">除了使用 DMX 手动创建查询以外，还可以使用 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中的预测查询生成器来创建预测。</span><span class="sxs-lookup"><span data-stu-id="d52cc-123">In addition to creating queries manually by using DMX, you can also create predictions by using the prediction query builder in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="simple-time-series-prediction-query"></a><span data-ttu-id="d52cc-124">简单的时序预测查询</span><span class="sxs-lookup"><span data-stu-id="d52cc-124">Simple Time Series Prediction Query</span></span>  
 <span data-ttu-id="d52cc-125">第一步是结合使用 `SELECT FROM` 语句和 `PredictTimeSeries` 函数来创建时序预测。</span><span class="sxs-lookup"><span data-stu-id="d52cc-125">The first step is to use the `SELECT FROM` statement together with the `PredictTimeSeries` function to create time series predictions.</span></span> <span data-ttu-id="d52cc-126">时序模型支持一种简化的预测创建语法：您不必提供任何输入，而只需指定要创建的预测数。</span><span class="sxs-lookup"><span data-stu-id="d52cc-126">Time series models support a simplified syntax for creating predictions: you do not need to supply any inputs, but only have to specify the number of predictions to create.</span></span> <span data-ttu-id="d52cc-127">下面是将您使用的语句的一般示例：</span><span class="sxs-lookup"><span data-stu-id="d52cc-127">The following is a generic example of the statement you will use:</span></span>  
  
```  
SELECT <select list>   
FROM [<mining model name>]   
WHERE [<criteria>]  
```  
  
 <span data-ttu-id="d52cc-128">选择列表可以包含模型中的列，例如要为其创建预测的产品系列的名称，或预测函数（如[Lag &#40;dmx&#41;](/sql/dmx/lag-dmx)或[PredictTimeSeries &#40;dmx&#41;](/sql/dmx/predicttimeseries-dmx)，它们专用于时序挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="d52cc-128">The select list can contain columns from the model, such as the name of the product line that you are creating the predictions for, or prediction functions, such as [Lag &#40;DMX&#41;](/sql/dmx/lag-dmx) or [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx), which are specifically for time series mining models.</span></span>  
  
#### <a name="to-create-a-simple-time-series-prediction-query"></a><span data-ttu-id="d52cc-129">创建简单的时序预测查询</span><span class="sxs-lookup"><span data-stu-id="d52cc-129">To create a simple time series prediction query</span></span>  
  
1.  <span data-ttu-id="d52cc-130">在**对象资源管理器**中，右键单击实例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，指向 "**新建查询**"，然后单击 " **DMX**"。</span><span class="sxs-lookup"><span data-stu-id="d52cc-130">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="d52cc-131">将打开查询编辑器，其中包含一个新的空白查询。</span><span class="sxs-lookup"><span data-stu-id="d52cc-131">Query Editor opens and contains a new, blank query.</span></span>  
  
2.  <span data-ttu-id="d52cc-132">将该语句的一般示例复制到空白查询中。</span><span class="sxs-lookup"><span data-stu-id="d52cc-132">Copy the generic example of the statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="d52cc-133">将</span><span class="sxs-lookup"><span data-stu-id="d52cc-133">Replace the following:</span></span>  
  
    ```  
    <select list>   
    ```  
  
     <span data-ttu-id="d52cc-134">替换为：</span><span class="sxs-lookup"><span data-stu-id="d52cc-134">with:</span></span>  
  
    ```  
    [Forecasting_MIXED].[ModelRegion],  
    PredictTimeSeries([Forecasting_MIXED].[Quantity],6) AS PredictQty,  
    PredictTimeSeries ([Forecasting_MIXED].[Amount],6) AS PredictAmt  
    ```  
  
     <span data-ttu-id="d52cc-135">第一行从挖掘模型中检索用来标识序列的值。</span><span class="sxs-lookup"><span data-stu-id="d52cc-135">The first line retrieves a value from the mining model that identifies the series.</span></span>  
  
     <span data-ttu-id="d52cc-136">第二行和第三行使用 `PredictTimeSeries` 函数。</span><span class="sxs-lookup"><span data-stu-id="d52cc-136">The second and third lines use the `PredictTimeSeries` function.</span></span> <span data-ttu-id="d52cc-137">每一行都预测一个不同的属性（`[Quantity]` 或 `[Amount]`）。</span><span class="sxs-lookup"><span data-stu-id="d52cc-137">Each line predicts a different attribute, `[Quantity]` or `[Amount]`.</span></span> <span data-ttu-id="d52cc-138">可预测属性名称后面的数字指定要预测的时间步长量。</span><span class="sxs-lookup"><span data-stu-id="d52cc-138">The numbers after the names of the predictable attributes specify the number of time steps to predict.</span></span>  
  
     <span data-ttu-id="d52cc-139">`AS` 子句用于为每个预测函数返回的列提供名称。</span><span class="sxs-lookup"><span data-stu-id="d52cc-139">The `AS` clause is used to provide a name for the column that is returned by each prediction function.</span></span> <span data-ttu-id="d52cc-140">如果您不提供别名，则默认情况下将返回这两列，标签为 `Expression`。</span><span class="sxs-lookup"><span data-stu-id="d52cc-140">If you do not supply an alias, by default both columns are returned with the label, `Expression`.</span></span>  
  
4.  <span data-ttu-id="d52cc-141">将</span><span class="sxs-lookup"><span data-stu-id="d52cc-141">Replace the following:</span></span>  
  
    ```  
    [<mining model>]   
    ```  
  
     <span data-ttu-id="d52cc-142">替换为：</span><span class="sxs-lookup"><span data-stu-id="d52cc-142">with:</span></span>  
  
    ```  
    [Forecasting_MIXED]  
    ```  
  
5.  <span data-ttu-id="d52cc-143">将</span><span class="sxs-lookup"><span data-stu-id="d52cc-143">Replace the following:</span></span>  
  
    ```  
    WHERE [criteria>]   
    ```  
  
     <span data-ttu-id="d52cc-144">替换为：</span><span class="sxs-lookup"><span data-stu-id="d52cc-144">with:</span></span>  
  
    ```  
    WHERE [ModelRegion] = 'M200 Europe' OR  
    [ModelRegion] = 'M200 Pacific'  
    ```  
  
     <span data-ttu-id="d52cc-145">现在，完整的语句应该如下所示：</span><span class="sxs-lookup"><span data-stu-id="d52cc-145">The complete statement should now be as follows:</span></span>  
  
    ```  
    SELECT  
    [Forecasting_MIXED].[ModelRegion],  
    PredictTimeSeries([Forecasting_MIXED].[Quantity],6) AS PredictQty,  
    PredictTimeSeries ([Forecasting_MIXED].[Amount],6) AS PredictAmt  
    FROM   
    [Forecasting_MIXED]  
    WHERE [ModelRegion] = 'M200 Europe' OR  
    [ModelRegion] = 'M200 Pacific'  
    ```  
  
6.  <span data-ttu-id="d52cc-146">在 "**文件**" 菜单上，单击 "**将 DMXQuery1 另存为**"。</span><span class="sxs-lookup"><span data-stu-id="d52cc-146">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
7.  <span data-ttu-id="d52cc-147">在 "**另存为**" 对话框中，浏览到相应的文件夹，并将该文件命名为 `SimpleTimeSeriesPrediction.dmx` 。</span><span class="sxs-lookup"><span data-stu-id="d52cc-147">In the **Save As** dialog box, browse to the appropriate folder, and name the file `SimpleTimeSeriesPrediction.dmx`.</span></span>  
  
8.  <span data-ttu-id="d52cc-148">在工具栏上，单击 "**执行**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="d52cc-148">On the toolbar, click the **Execute** button.</span></span>  
  
     <span data-ttu-id="d52cc-149">该查询将针对在 `WHERE` 子句中指定的产品和地区的每个组合（共两个组合）返回 6 个预测。</span><span class="sxs-lookup"><span data-stu-id="d52cc-149">The query returns 6 predictions for each of the two combinations of product and region that are specified in the `WHERE` clause.</span></span>  
  
 <span data-ttu-id="d52cc-150">在下一课中，您将创建一个为模型提供新数据的查询，并将该预测的结果与刚创建的预测进行比较。</span><span class="sxs-lookup"><span data-stu-id="d52cc-150">In the next lesson, you will create a query that supplies new data to the model, and compare the results of that prediction with the one you just created.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="d52cc-151">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="d52cc-151">Next Task in Lesson</span></span>  
 [<span data-ttu-id="d52cc-152">第 5 课：扩展时序模型</span><span class="sxs-lookup"><span data-stu-id="d52cc-152">Lesson 5: Extending the Time Series Model</span></span>](../../2014/tutorials/lesson-5-extending-the-time-series-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="d52cc-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d52cc-153">See Also</span></span>  
 <span data-ttu-id="d52cc-154">[PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx) </span><span class="sxs-lookup"><span data-stu-id="d52cc-154">[PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx) </span></span>  
 <span data-ttu-id="d52cc-155">[Lag &#40;DMX&#41;](/sql/dmx/lag-dmx) </span><span class="sxs-lookup"><span data-stu-id="d52cc-155">[Lag &#40;DMX&#41;](/sql/dmx/lag-dmx) </span></span>  
 <span data-ttu-id="d52cc-156">[时序模型查询示例](../../2014/analysis-services/data-mining/time-series-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="d52cc-156">[Time Series Model Query Examples](../../2014/analysis-services/data-mining/time-series-model-query-examples.md) </span></span>  
 [<span data-ttu-id="d52cc-157">第2课： &#40;中级数据挖掘教程构建预测方案&#41;</span><span class="sxs-lookup"><span data-stu-id="d52cc-157">Lesson 2: Building a Forecasting Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
  
