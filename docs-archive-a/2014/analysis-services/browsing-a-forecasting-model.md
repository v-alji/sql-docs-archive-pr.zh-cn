---
title: 浏览预测模型 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, browsing
- forecasting [data mining]
- mining models, viewing
- mining model, time series
- time series [data mining]
ms.assetid: ad35a528-1949-4048-8678-3b9760c1c88c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7d0b188c4ed6fba9bc5b1082725b17c99081c1b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579307"
---
# <a name="browsing-a-forecasting-model"></a><span data-ttu-id="8d5f6-102">浏览预测模型</span><span class="sxs-lookup"><span data-stu-id="8d5f6-102">Browsing a Forecasting Model</span></span>
  <span data-ttu-id="8d5f6-103">使用 "**浏览**" 打开预测模型时，该模型将显示在交互式查看器中，类似于中的时序模型查看器 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="8d5f6-103">When you open a forecasting model using **Browse**, the model is displayed in an interactive viewer, similar to the time series model viewer in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="8d5f6-104">查看器有助于您探索趋势、比较序列、创建预测以及获取有关模型和基础数据的信息。</span><span class="sxs-lookup"><span data-stu-id="8d5f6-104">The viewer helps you explore trends, compare series, create predictions, and get information about the model and the underlying data.</span></span>  
  
##  <a name="explore-the-model"></a><a name="bkmk_Top"></a><span data-ttu-id="8d5f6-105">浏览模型</span><span class="sxs-lookup"><span data-stu-id="8d5f6-105">Explore the Model</span></span>  
 <span data-ttu-id="8d5f6-106">用于预测模型的**浏览**查看器提供了一个图表视图，其中显示了一段时间内的趋势，并使您可以创建预测和模型视图，它将时间序列表示为决策树或回归树。</span><span class="sxs-lookup"><span data-stu-id="8d5f6-106">The **Browse** viewer for forecasting models provides a chart view, which shows the trends over time and lets you create predictions, and a model view, which represents the time series as a decision tree or a regression tree.</span></span>  
  
-   [<span data-ttu-id="8d5f6-107">图表视图</span><span class="sxs-lookup"><span data-stu-id="8d5f6-107">Chart view</span></span>](#bkmk_charts)  
  
-   [<span data-ttu-id="8d5f6-108">模型视图</span><span class="sxs-lookup"><span data-stu-id="8d5f6-108">Model view</span></span>](#bkmk_Model)  
  
 <span data-ttu-id="8d5f6-109">若要试验预测模型，可以使用示例数据工作簿的 "预测" 选项卡上的示例数据，并使用 &#40;"**数据挖掘**" 功能区中的 "[用于 Excel 的数据挖掘外接程序"&#41;](forecast-wizard-data-mining-add-ins-for-excel.md) &#40;或 "**分析**" 功能区中的 "excel 的数据挖掘外接程序" [&#41;](forecast-table-analysis-tools-for-excel.md)生成时序模型。</span><span class="sxs-lookup"><span data-stu-id="8d5f6-109">To experiment with a forecasting model, you can use the sample data on the Forecast tab of the sample data workbook, and build a time series model using the [Forecast Wizard &#40;Data Mining Add-ins for Excel&#41;](forecast-wizard-data-mining-add-ins-for-excel.md) in the **Data Mining** ribbon, or [Forecast &#40;Table Analysis Tools for Excel&#41;](forecast-table-analysis-tools-for-excel.md) in the **Analyze** ribbon.</span></span>  
  
###  <a name="chart"></a><a name="bkmk_charts"></a><span data-ttu-id="8d5f6-110">流程图</span><span class="sxs-lookup"><span data-stu-id="8d5f6-110">Chart</span></span>  
 <span data-ttu-id="8d5f6-111">"**图表**" 选项卡显示一段时间内数据系列的趋势以及预测值。</span><span class="sxs-lookup"><span data-stu-id="8d5f6-111">The **Chart** tab displays the trend in your data series over time, together with the predicted values.</span></span> <span data-ttu-id="8d5f6-112">图表的垂直轴表示序列的值，水平轴表示时间。</span><span class="sxs-lookup"><span data-stu-id="8d5f6-112">The vertical axis of the chart represents the values of the series, and the horizontal axis represents time.</span></span>  
  
##### <a name="explore-the-forecasting-chart"></a><span data-ttu-id="8d5f6-113">探索预测图</span><span class="sxs-lookup"><span data-stu-id="8d5f6-113">Explore the forecasting chart</span></span>  
  
1.  <span data-ttu-id="8d5f6-114">此模型包含多个时序，但是为了简化图表，可显示一个时序或少数几个相关时序。</span><span class="sxs-lookup"><span data-stu-id="8d5f6-114">This model contains multiple time series, but to simplify the chart, you can display a single series, or just a few related series.</span></span>  
  
     <span data-ttu-id="8d5f6-115">![预测模型中的历史预测](media/dm13-forecast-chart-historicpredictions.gif "预测模型中的历史预测")</span><span class="sxs-lookup"><span data-stu-id="8d5f6-115">![historical predictions in the forecasting model](media/dm13-forecast-chart-historicpredictions.gif "historical predictions in the forecasting model")</span></span>  
  
     <span data-ttu-id="8d5f6-116">使用复选框只选择北美的销售额预测。</span><span class="sxs-lookup"><span data-stu-id="8d5f6-116">Use the check boxes to select the forecast for just North America, and just for sales Amount.</span></span>  
  
2.  <span data-ttu-id="8d5f6-117">单击 "**预测步骤**" 并键入一个新值，以控制要在图表中看到的未来时间值数。</span><span class="sxs-lookup"><span data-stu-id="8d5f6-117">Click **Prediction Steps** and type a new value to control how many future time values you want to see in the chart.</span></span>  
  
     <span data-ttu-id="8d5f6-118">默认值为 5。</span><span class="sxs-lookup"><span data-stu-id="8d5f6-118">The default is 5.</span></span>  
  
3.  <span data-ttu-id="8d5f6-119">单击 "历史" 或 "未来" 行中的任意点，查看 "**挖掘图例**" 中显示的该时间点的确切值。</span><span class="sxs-lookup"><span data-stu-id="8d5f6-119">Click any point in the line, either historical or future, to see the exact values for that point in time, displayed in the **Mining Legend**.</span></span>  
  
4.  <span data-ttu-id="8d5f6-120">该图表同时显示历史数据和未来数据。</span><span class="sxs-lookup"><span data-stu-id="8d5f6-120">The chart displays both historical and future data.</span></span> <span data-ttu-id="8d5f6-121">注意带阴影背景的虚线。</span><span class="sxs-lookup"><span data-stu-id="8d5f6-121">Note the dotted line, with a shaded background.</span></span> <span data-ttu-id="8d5f6-122">这些值是基于模型得出的未来预测信息。</span><span class="sxs-lookup"><span data-stu-id="8d5f6-122">These values are the future predictions, based on the model.</span></span>  
  
     <span data-ttu-id="8d5f6-123">图表的左侧显示历史数据（您用于建立模型的数据）。</span><span class="sxs-lookup"><span data-stu-id="8d5f6-123">The historical data (which you used to build the model) is shown in the left side of the chart.</span></span>  
  
5.  <span data-ttu-id="8d5f6-124">选择 "**显示历史预测**" 选项，以了解时序的稳定性。</span><span class="sxs-lookup"><span data-stu-id="8d5f6-124">Select the **Show historic predictions** option to get a sense for the stability of the time series.</span></span>  
  
     <span data-ttu-id="8d5f6-125">![针对模型中单个序列的预测](media/dm13-forecast-chart-singleseries.gif "针对模型中单个序列的预测")</span><span class="sxs-lookup"><span data-stu-id="8d5f6-125">![forecasts for a single series in the model](media/dm13-forecast-chart-singleseries.gif "forecasts for a single series in the model")</span></span>  
  
     <span data-ttu-id="8d5f6-126">历史预测信息是根据序列为该点预测的值，不同于实际历史值。</span><span class="sxs-lookup"><span data-stu-id="8d5f6-126">Historical predictions are values predicted based on the series to that point, which are compared to actual historical values.</span></span> <span data-ttu-id="8d5f6-127">如果虚线（使用预测的值绘成）与实线（实际值）之间相距甚远，就表示序列的第一部分或许不能准确预测稍后的值。</span><span class="sxs-lookup"><span data-stu-id="8d5f6-127">If the dotted line (with the predicted values) is far apart from the solid line (the actual values), it means the first part of the series perhaps does not accurately predict the later values.</span></span> <span data-ttu-id="8d5f6-128">您可能需要更多数据，这也可能只是一种周期波动的表现。</span><span class="sxs-lookup"><span data-stu-id="8d5f6-128">You might need more data, or it might simply be an indicator of volatility in the cycle.</span></span>  
  
6.  <span data-ttu-id="8d5f6-129">选择 "**显示偏差**" 选项可在图表中显示误差线。</span><span class="sxs-lookup"><span data-stu-id="8d5f6-129">Select the **Show Deviations** option to display error bars in the chart.</span></span>  
  
     <span data-ttu-id="8d5f6-130">通过误差线，您可以直观地了解预测信息的变化范围。</span><span class="sxs-lookup"><span data-stu-id="8d5f6-130">The error bars let you visually assess the variability of the predictions.</span></span> <span data-ttu-id="8d5f6-131">预测信息的可靠性因源数据而异，不过，在您增加预测步骤数时，将会看到偏差稳定增长。</span><span class="sxs-lookup"><span data-stu-id="8d5f6-131">The quality of predictions varies depending on your source data, but as you increase the number of prediction steps, you should see the deviations steadily increase.</span></span>  
  
 <span data-ttu-id="8d5f6-132">**提示**</span><span class="sxs-lookup"><span data-stu-id="8d5f6-132">**Tips**</span></span>  
  
-   <span data-ttu-id="8d5f6-133">若要切换 "**挖掘图例**" 的显示，请右键单击图表中的任意点。</span><span class="sxs-lookup"><span data-stu-id="8d5f6-133">To toggle display of the **Mining Legend**, right-click any point in the chart.</span></span>  
  
     <span data-ttu-id="8d5f6-134">可以通过以下方法查看特定的时间范围：单击图表，将时间选定范围拖到图表上，然后再次单击图表以放大选定的范围。</span><span class="sxs-lookup"><span data-stu-id="8d5f6-134">You can view a specific time range by clicking the chart, dragging a time selection across the chart, and then clicking again to zoom in on the selected range.</span></span>  
  
-   <span data-ttu-id="8d5f6-135">若要获取当前图表的副本，请单击 "**复制到 excel**"，然后单击 Excel 中的工作表。</span><span class="sxs-lookup"><span data-stu-id="8d5f6-135">To get a copy of the current chart, click **Copy to Excel**, then click a worksheet in Excel.</span></span> <span data-ttu-id="8d5f6-136">即会使用您设置的所有选项在工作表中插入图形，包括图例。</span><span class="sxs-lookup"><span data-stu-id="8d5f6-136">A graphic is inserted in the sheet using all the options you had set, including a legend.</span></span>  
  
     <span data-ttu-id="8d5f6-137">但是，此图形是静态的，因此您不能编辑图例或查看基础数据;如果需要更交互式的图表视图，请使用[Visio](viewing-data-mining-models-in-visio-data-mining-add-ins.md)查看器。</span><span class="sxs-lookup"><span data-stu-id="8d5f6-137">However, this graphic is static so you cannot edit the legend or view the underlying data; if you need a more interactive chart view, use the [Visio viewers](viewing-data-mining-models-in-visio-data-mining-add-ins.md).</span></span>  
  
-   <span data-ttu-id="8d5f6-138">单击查看器菜单栏中的 " **Abs** "，在绝对曲线和相对曲线之间切换。</span><span class="sxs-lookup"><span data-stu-id="8d5f6-138">Click **Abs** in the viewer menu bar to toggle between absolute and relative curves.</span></span>  
  
     <span data-ttu-id="8d5f6-139">如果图表中包含多个模型，但每个模型的数据比例差异很大，则此选项将非常有用。</span><span class="sxs-lookup"><span data-stu-id="8d5f6-139">This option is useful if your chart contains multiple models, but the scale of the data for each model is very different.</span></span>  
  
     <span data-ttu-id="8d5f6-140">举例来说，如果太平洋地区商店新近开业，销售额很低，则在使用绝对值时，显示太平洋销售额的线可能显示为平的，难以看出实际变化，而其他模型将以更常规的比例显示。</span><span class="sxs-lookup"><span data-stu-id="8d5f6-140">For example, if the Pacific region stores were new and sales were low, and if absolute values are used, the line showing Pacific sales might appear flat, making it difficult to see actual changes, whereas the other models would be displayed at a more normal scale.</span></span>  
  
     <span data-ttu-id="8d5f6-141">通过切换视图以使用相对值，您可以规范化不同模型的比例，将差异显示为百分比更改。</span><span class="sxs-lookup"><span data-stu-id="8d5f6-141">By switching the view to use relative values, you can normalize the scale of different models, and display differences as a percent of change.</span></span> <span data-ttu-id="8d5f6-142">如果更改是相对于每个模型的，则可以在同一图形中显示这些模型，而不会出现明显的扭曲。</span><span class="sxs-lookup"><span data-stu-id="8d5f6-142">When change is relative to each model, they can be displayed in the same graph without significant distortion.</span></span>  
  
 [<span data-ttu-id="8d5f6-143">浏览模型</span><span class="sxs-lookup"><span data-stu-id="8d5f6-143">Explore the Model</span></span>](#bkmk_Top)  
  
###  <a name="model"></a><a name="bkmk_Model"></a><span data-ttu-id="8d5f6-144">模式</span><span class="sxs-lookup"><span data-stu-id="8d5f6-144">Model</span></span>  
 <span data-ttu-id="8d5f6-145">还可以将预测模型表示为决策树，或者，在序列基本呈线性时表示为回归模型。</span><span class="sxs-lookup"><span data-stu-id="8d5f6-145">A forecasting model can also be represented as a decision tree, or, if the series is mostly linear, a regression model.</span></span>  
  
 <span data-ttu-id="8d5f6-146">例如，在此模型中，基于某一特定条件的回归公式中存在差异，因此树拆分为两个分支，每个分支有一个不同的回归公式。</span><span class="sxs-lookup"><span data-stu-id="8d5f6-146">For example, in this model, there is a difference in the regression formula based on a certain condition, so the tree splits into two branches, each with a different regression formula.</span></span>  
  
 <span data-ttu-id="8d5f6-147">![筛选预测模型中单个序列](media/dm13-forecast-model-northamerica.gif "筛选预测模型中单个序列")</span><span class="sxs-lookup"><span data-stu-id="8d5f6-147">![Filter single series in the forecasting model](media/dm13-forecast-model-northamerica.gif "Filter single series in the forecasting model")</span></span>  
  
##### <a name="explore-the-forecasting-model-as-a-tree"></a><span data-ttu-id="8d5f6-148">按树的形式探索预测模型</span><span class="sxs-lookup"><span data-stu-id="8d5f6-148">Explore the forecasting model as a tree</span></span>  
  
1.  <span data-ttu-id="8d5f6-149">单击 "**树**" 下拉列表并选择要显示的模型。</span><span class="sxs-lookup"><span data-stu-id="8d5f6-149">Click the **Tree** dropdown list and choose a model to display.</span></span>  
  
     <span data-ttu-id="8d5f6-150">为每个可预测属性显示一个单独的树或回归节点。</span><span class="sxs-lookup"><span data-stu-id="8d5f6-150">A separate tree or regression node is displayed for each predictable attribute.</span></span> <span data-ttu-id="8d5f6-151">举例来说，如果您的数据包含欧洲、北美和太平洋的销售额，您将看到三个不同的模型，每个数据序列对应一个模型。</span><span class="sxs-lookup"><span data-stu-id="8d5f6-151">For example, if your data contains sales for Europe, North America, and the Pacific, there would three different models, one for each data series.</span></span>  
  
2.  <span data-ttu-id="8d5f6-152">拖动 "**显示级别**" 滑块以筛选出树的较低级别，并将重点放在最重要的拆分上。</span><span class="sxs-lookup"><span data-stu-id="8d5f6-152">Drag the **Show Level** slider to filter out lower levels of the tree, and focus on the most important splits.</span></span>  
  
3.  <span data-ttu-id="8d5f6-153">单击每个节点可以在 "**挖掘图例**" 中查看一些描述性统计信息。</span><span class="sxs-lookup"><span data-stu-id="8d5f6-153">Click each node to view some descriptive statistics in the **Mining Legend**.</span></span>  
  
     <span data-ttu-id="8d5f6-154">鼠标暂停在某个节点上后，工具提示也将显示相同的统计信息以及描述该节点的完整公式。</span><span class="sxs-lookup"><span data-stu-id="8d5f6-154">As you pause over a node with the mouse, a ToolTip also displays the same statistics, as well as the full formula describing that node.</span></span>  
  
4.  <span data-ttu-id="8d5f6-155">如果要复制 "**挖掘图例**" 中的信息，请右键单击 "**挖掘图例**"，选择 "**复制**"，然后在 Excel 工作表中单击。</span><span class="sxs-lookup"><span data-stu-id="8d5f6-155">If you want to copy the information in the **Mining Legend**, right-click the **Mining Legend**, select **Copy**, and click inside your Excel worksheet.</span></span> <span data-ttu-id="8d5f6-156">"**复制到 Excel** " 选项将复制图形，而不是统计信息。</span><span class="sxs-lookup"><span data-stu-id="8d5f6-156">The **Copy to Excel** option copies the graph, not the statistics.</span></span>  
  
 [<span data-ttu-id="8d5f6-157">浏览模型</span><span class="sxs-lookup"><span data-stu-id="8d5f6-157">Explore the Model</span></span>](#bkmk_Top)  
  
## <a name="see-also"></a><span data-ttu-id="8d5f6-158">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8d5f6-158">See Also</span></span>  
 [<span data-ttu-id="8d5f6-159">在 Excel 中浏览模型 &#40;SQL Server 数据挖掘外接程序&#41;</span><span class="sxs-lookup"><span data-stu-id="8d5f6-159">Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
