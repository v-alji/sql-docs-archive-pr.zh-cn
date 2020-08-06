---
title: 使用更新的数据 (中级数据挖掘教程) 的时序预测 |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: af73681d-ce1c-4b6e-b195-6df3d2fb5275
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2017defaba74071b1a12bee14a5d8907e4c71cda
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577118"
---
# <a name="time-series-predictions-using-updated-data-intermediate-data-mining-tutorial"></a><span data-ttu-id="93200-102">使用更新数据进行时序预测（数据挖掘中级教程）</span><span class="sxs-lookup"><span data-stu-id="93200-102">Time Series Predictions using Updated Data (Intermediate Data Mining Tutorial)</span></span>
    
## <a name="creating-predictions-using-the-extended-sales-data"></a><span data-ttu-id="93200-103">使用扩展的销售额数据创建预测</span><span class="sxs-lookup"><span data-stu-id="93200-103">Creating Predictions using the Extended Sales Data</span></span>  
 <span data-ttu-id="93200-104">在本课中，您将创建一个预测查询，该查询将新的销售额数据添加到模型。</span><span class="sxs-lookup"><span data-stu-id="93200-104">In this lesson, you will create a prediction query that adds the new sales data to the model.</span></span> <span data-ttu-id="93200-105">通过使用新数据扩展模型，您可以获得最新预测，其中包括最新的数据点。</span><span class="sxs-lookup"><span data-stu-id="93200-105">By extending the model with new data, you can get up-to-date predictions that include the newest data points.</span></span>  
  
 <span data-ttu-id="93200-106">创建使用新数据的时序预测非常简单：只需将参数 EXTEND_MODEL_CASES 添加到[PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx)函数，指定新数据的源，并指定要获取的预测数。</span><span class="sxs-lookup"><span data-stu-id="93200-106">Creating time series predictions that use new data is easy: you simply add the parameter EXTEND_MODEL_CASES to the [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx) function, specify the source of the new data, and specify how many predictions you want to get.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="93200-107">参数 EXTEND_MODEL_CASES 是可选的；默认情况下，通过联接新数据作为输入将该模型扩展您创建时序预测查询的任意时间。</span><span class="sxs-lookup"><span data-stu-id="93200-107">The parameter EXTEND_MODEL_CASES is optional; by default the model is extended any time that you create a time series prediction query by joining new data as inputs.</span></span>  
  
#### <a name="to-build-the-prediction-query-and-add-new-data"></a><span data-ttu-id="93200-108">生成预测查询和添加新数据</span><span class="sxs-lookup"><span data-stu-id="93200-108">To build the prediction query and add new data</span></span>  
  
1.  <span data-ttu-id="93200-109">如果模型尚未打开，请双击预测结构，并在数据挖掘设计器中单击 "**挖掘模型预测**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="93200-109">If the model is not already open, double-click the Forecasting structure, and in Data Mining Designer, click the **Mining Model Prediction** tab.</span></span>  
  
2.  <span data-ttu-id="93200-110">在 "**挖掘模型**" 窗格中，应该已选择模型预测。</span><span class="sxs-lookup"><span data-stu-id="93200-110">In the **Mining Model** pane, the model Forecasting should already be selected.</span></span> <span data-ttu-id="93200-111">如果未选择此选项，请单击 "**选择模型**"，然后选择模型 "预测"。</span><span class="sxs-lookup"><span data-stu-id="93200-111">If it is not selected, click **Select Model**, and then select the model, Forecasting.</span></span>  
  
3.  <span data-ttu-id="93200-112">在 "**选择输入表 (s) **窗格中，单击"**选择事例表**"。</span><span class="sxs-lookup"><span data-stu-id="93200-112">In the **Select Input Table(s)** pane, click **Select Case Table**.</span></span>  
  
4.  <span data-ttu-id="93200-113">在 "**选择表**" 对话框中，选择数据源 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="93200-113">In the **Select Table** dialog box, select the data source, [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)].</span></span>  
  
     <span data-ttu-id="93200-114">从数据源视图列表中，选择 "NewSalesData"，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="93200-114">From the list of data source views, select NewSalesData and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="93200-115">右键单击设计区域的图面，然后选择 "**修改连接**"。</span><span class="sxs-lookup"><span data-stu-id="93200-115">Right-click the surface of the design area and select **Modify Connections**.</span></span>  
  
6.  <span data-ttu-id="93200-116">使用 "**修改映射**" 对话框，将模型中的列映射到外部数据中的列，如下所示：</span><span class="sxs-lookup"><span data-stu-id="93200-116">Using the **Modify Mapping** dialog box, map the columns in the model to the columns in the external data as follows:</span></span>  
  
    -   <span data-ttu-id="93200-117">将挖掘模型中的 ReportingDate 列映射到输入数据中的 NewDate 列。</span><span class="sxs-lookup"><span data-stu-id="93200-117">Map the ReportingDate column in the mining model to the NewDate column in the input data.</span></span>  
  
    -   <span data-ttu-id="93200-118">将挖掘模型中的量列映射到输入数据中的 NewAmount 列。</span><span class="sxs-lookup"><span data-stu-id="93200-118">Map the Amount column in the mining model to the NewAmount column in the input data.</span></span>  
  
    -   <span data-ttu-id="93200-119">将挖掘模型中的 "数量" 列映射到输入数据中的 NewQty 列。</span><span class="sxs-lookup"><span data-stu-id="93200-119">Map the Quantity column in the mining model to the NewQty column in the input data.</span></span>  
  
    -   <span data-ttu-id="93200-120">将挖掘模型中的 ModelRegion 列映射到输入数据中的序列列。</span><span class="sxs-lookup"><span data-stu-id="93200-120">Map the ModelRegion column in the mining model to the Series column in the input data.</span></span>  
  
7.  <span data-ttu-id="93200-121">现在，您将生成预测查询。</span><span class="sxs-lookup"><span data-stu-id="93200-121">Now you will build the prediction query.</span></span>  
  
     <span data-ttu-id="93200-122">首先，将一个列添加到预测查询来输出预测应用到的序列。</span><span class="sxs-lookup"><span data-stu-id="93200-122">First, add a column to the prediction query to output the series the prediction applies to.</span></span>  
  
    1.  <span data-ttu-id="93200-123">在网格中，单击 "**源**" 下的第一个空行，然后选择 "预测"。</span><span class="sxs-lookup"><span data-stu-id="93200-123">In the grid, click the first empty row, under **Source**, and then select Forecasting.</span></span>  
  
    2.  <span data-ttu-id="93200-124">在 "**字段**" 列中，选择 "模型区域"，为 "**别名**" 键入 `Model Region` 。</span><span class="sxs-lookup"><span data-stu-id="93200-124">In the **Field** column, select Model Region and for **Alias**, type `Model Region`.</span></span>  
  
8.  <span data-ttu-id="93200-125">接下来，添加和编辑预测函数。</span><span class="sxs-lookup"><span data-stu-id="93200-125">Next, add and edit the prediction function.</span></span>  
  
    1.  <span data-ttu-id="93200-126">单击一个空行，然后在 "**源**" 下，选择 "**预测函数**"。</span><span class="sxs-lookup"><span data-stu-id="93200-126">Click an empty row, and under **Source**, select **Prediction Function**.</span></span>  
  
    2.  <span data-ttu-id="93200-127">对于 "**字段**"，请选择**PredictTimeSeries**。</span><span class="sxs-lookup"><span data-stu-id="93200-127">For **Field**, select **PredictTimeSeries**.</span></span>  
  
    3.  <span data-ttu-id="93200-128">对于 "**别名**"，键入**预测值**。</span><span class="sxs-lookup"><span data-stu-id="93200-128">For **Alias**, type **Predicted Values**.</span></span>  
  
    4.  <span data-ttu-id="93200-129">从 "**挖掘模型**" 窗格中将字段数量拖到 "**条件/参数**" 列中。</span><span class="sxs-lookup"><span data-stu-id="93200-129">Drag the field Quantity from the **Mining Model** pane into the **Criteria/Argument** column.</span></span>  
  
    5.  <span data-ttu-id="93200-130">在 "**条件/参数**" 列中的字段名称后，键入以下文本： **5，EXTEND_MODEL_CASES**</span><span class="sxs-lookup"><span data-stu-id="93200-130">In the **Criteria/Argument** column, after the field name, type the following text:  **5,EXTEND_MODEL_CASES**</span></span>  
  
         <span data-ttu-id="93200-131">"**条件/参数**" 文本框的完整文本应该如下所示：`[Forecasting].[Quantity],5,EXTEND_MODEL_CASES`</span><span class="sxs-lookup"><span data-stu-id="93200-131">The complete text of the **Criteria/Argument** text box should be as follows: `[Forecasting].[Quantity],5,EXTEND_MODEL_CASES`</span></span>  
  
9. <span data-ttu-id="93200-132">单击 "**结果**" 并查看结果。</span><span class="sxs-lookup"><span data-stu-id="93200-132">Click **Results** and review the results.</span></span>  
  
     <span data-ttu-id="93200-133">预测从 7 月（原始数据结束后的第一个时间段）开始，到 11 月结束（原始数据结束后的第 5 个时间段）。</span><span class="sxs-lookup"><span data-stu-id="93200-133">The predictions begin in July (the first time slice after the end of the original data) and end at November (the fifth time slice after the end of the original data).</span></span>  
  
 <span data-ttu-id="93200-134">您可以看到，要高效使用此预测查询类型，您需要知道旧数据何时结束以及新数据中有多少时间段。</span><span class="sxs-lookup"><span data-stu-id="93200-134">You can see that to use this type of prediction query effectively, you need to know when the old data ends, as well as how many time slices there are in the new data.</span></span>  
  
 <span data-ttu-id="93200-135">例如，在此模型中，原始数据序列 6 月结束，并且数据针对 7 月、 8 月和 9 月。</span><span class="sxs-lookup"><span data-stu-id="93200-135">For example, in this model, the original data series ended in June, and the data is for the months of July, August, and September.</span></span>  
  
 <span data-ttu-id="93200-136">使用 EXTEND_MODEL_CASES 的预测始终在原始数据序列结束时开始。</span><span class="sxs-lookup"><span data-stu-id="93200-136">Predictions that use EXTEND_MODEL_CASES always begin at the end of the original data series.</span></span> <span data-ttu-id="93200-137">因此，如果您只想获取未知月份的预测，则需要指定预测的起点和终点。</span><span class="sxs-lookup"><span data-stu-id="93200-137">Therefore, if you want to get only the predictions for the unknown months, you need to specify the starting point and the end point for prediction.</span></span> <span data-ttu-id="93200-138">这两个值被指定为从旧数据结束时开始的一些时间段。</span><span class="sxs-lookup"><span data-stu-id="93200-138">Both values are specified as a number of time slices starting at the end of the old data.</span></span>  
  
 <span data-ttu-id="93200-139">下面的过程演示如何做到这点。</span><span class="sxs-lookup"><span data-stu-id="93200-139">The following procedure demonstrates how to do this.</span></span>  
  
### <a name="change-the-start-and-end-points-of-the-predictions"></a><span data-ttu-id="93200-140">更改预测的起点和终点</span><span class="sxs-lookup"><span data-stu-id="93200-140">Change the start and end points of the predictions</span></span>  
  
1.  <span data-ttu-id="93200-141">在预测查询生成器中，单击 "**查询**" 以切换到 DMX 视图。</span><span class="sxs-lookup"><span data-stu-id="93200-141">In Prediction Query Builder, click **Query** to switch to DMX view.</span></span>  
  
2.  <span data-ttu-id="93200-142">找到包含 PredictTimeSeries 函数的 DMX 语句并按以下方式更改它：</span><span class="sxs-lookup"><span data-stu-id="93200-142">Locate the DMX statement that contains the PredictTimeSeries function and change it as follows:</span></span>  
  
     `PredictTimeSeries([Forecasting 12].[Quantity],4,6,EXTEND_MODEL_CASES)`  
  
3.  <span data-ttu-id="93200-143">单击 "**结果**" 并查看结果。</span><span class="sxs-lookup"><span data-stu-id="93200-143">Click **Results** and review the results.</span></span>  
  
     <span data-ttu-id="93200-144">现在预测从 10 月开始（原始数据结束后的第四个时间段），到 12 月结束（原始数据结束后的第六个时间段）。</span><span class="sxs-lookup"><span data-stu-id="93200-144">Now the predictions begin at October (the fourth time slice, counting from the end of the original data) and end at December (the sixth time slice, counting from the end of the original data).</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="93200-145">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="93200-145">Next Task in Lesson</span></span>  
 [<span data-ttu-id="93200-146">使用替换数据 &#40;中级数据挖掘教程的时序预测&#41;</span><span class="sxs-lookup"><span data-stu-id="93200-146">Time Series Predictions using Replacement Data &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/time-series-predictions-replacement-data-intermediate-data-mining.md)  
  
## <a name="see-also"></a><span data-ttu-id="93200-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="93200-147">See Also</span></span>  
 <span data-ttu-id="93200-148">[Microsoft 时序算法技术参考](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="93200-148">[Microsoft Time Series Algorithm Technical Reference](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md) </span></span>  
 [<span data-ttu-id="93200-149">时序模型的挖掘模型内容（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="93200-149">Mining Model Content for Time Series Models &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/mining-model-content-for-time-series-models-analysis-services-data-mining.md)  
  
  
