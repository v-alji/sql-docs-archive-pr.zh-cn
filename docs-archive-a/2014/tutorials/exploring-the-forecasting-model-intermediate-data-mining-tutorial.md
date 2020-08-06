---
title: 了解 (中级数据挖掘教程) 的预测模型 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0a00f409-050f-4b92-9763-ba31a6aa3052
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 86bd6371a8d32c53c68351aaff36a317f7433ef0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691395"
---
# <a name="exploring-the-forecasting-model-intermediate-data-mining-tutorial"></a><span data-ttu-id="87b63-102">浏览预测模型（数据挖掘中级教程）</span><span class="sxs-lookup"><span data-stu-id="87b63-102">Exploring the Forecasting Model (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="87b63-103">既然您已经生成了预测挖掘模型，则可以使用数据挖掘设计器的 "**挖掘模型查看器**" 选项卡来浏览结果。</span><span class="sxs-lookup"><span data-stu-id="87b63-103">Now that you have built the forecasting mining model, you can explore the results by using the **Mining Model Viewer** tab of Data Mining Designer.</span></span> <span data-ttu-id="87b63-104">[!INCLUDE[msCoName](../includes/msconame-md.md)]时序查看器包含两个选项卡：**图表**和**模型**。</span><span class="sxs-lookup"><span data-stu-id="87b63-104">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series Viewer contains two tabs: **Charts** and **Model**.</span></span>  
  
 <span data-ttu-id="87b63-105">此外，您可以对所有模型使用 Microsoft 一般内容树查看器。</span><span class="sxs-lookup"><span data-stu-id="87b63-105">Additionally, you can use the Microsoft Generic Tree Viewer with all models.</span></span> <span data-ttu-id="87b63-106">每个视图都显示时序模型中稍有不同的信息概览。</span><span class="sxs-lookup"><span data-stu-id="87b63-106">Each view presents a slightly different picture of the information in the time series model.</span></span>  
  
-   [<span data-ttu-id="87b63-107">“图表”选项卡</span><span class="sxs-lookup"><span data-stu-id="87b63-107">Charts Tab</span></span>](#bkmk_Charts)  
  
-   [<span data-ttu-id="87b63-108">“模型”选项卡</span><span class="sxs-lookup"><span data-stu-id="87b63-108">Model Tab</span></span>](#bkmk_Model)  
  
-   [<span data-ttu-id="87b63-109">Microsoft 一般内容查看器</span><span class="sxs-lookup"><span data-stu-id="87b63-109">Microsoft Generic Content Viewer</span></span>](#bkmk_Content)  
  
##  <a name="charts-tab"></a><a name="bkmk_Charts"></a><span data-ttu-id="87b63-110">图表选项卡</span><span class="sxs-lookup"><span data-stu-id="87b63-110">Charts Tab</span></span>  
 <span data-ttu-id="87b63-111">时序查看器的 "**图表**" 选项卡 [!INCLUDE[msCoName](../includes/msconame-md.md)] 以图形方式显示每个序列，包括历史数据和预测。</span><span class="sxs-lookup"><span data-stu-id="87b63-111">The **Charts** tab of the [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series Viewer graphically shows you each of the series, including historical data and predictions.</span></span> <span data-ttu-id="87b63-112">时序图中的每条线都代表产品、区域和可预测属性的一种唯一组合。</span><span class="sxs-lookup"><span data-stu-id="87b63-112">Each line in the time series graph represents a unique combination of product, region, and predictable attribute.</span></span>  
  
 <span data-ttu-id="87b63-113">该查看器右侧的图例列出根据下拉列表中的所选内容提供的时序。</span><span class="sxs-lookup"><span data-stu-id="87b63-113">The legend on the right side of the viewer lists the time series that available, based on the selections in the drop-down list.</span></span> <span data-ttu-id="87b63-114">您可以选中和清除图例中的复选框，以便控制图形中显示的时序。</span><span class="sxs-lookup"><span data-stu-id="87b63-114">You can select and clear the check boxes in the legend to control which time series displays in the graph.</span></span>  
  
 <span data-ttu-id="87b63-115">还可以更改显示选项，例如用于每个时序的颜色或是否在图表中的点显示值。</span><span class="sxs-lookup"><span data-stu-id="87b63-115">You can also change the display options, such as the colors used for each time series, or whether values are displayed at points in the chart.</span></span>  
  
#### <a name="to-select-a-time-series"></a><span data-ttu-id="87b63-116">选择时序</span><span class="sxs-lookup"><span data-stu-id="87b63-116">To select a time series</span></span>  
  
1.  <span data-ttu-id="87b63-117">单击 "**挖掘模型查看器**" 选项卡的 "**图表**" 选项卡（如果它不可见）。</span><span class="sxs-lookup"><span data-stu-id="87b63-117">Click the **Charts** tab of the **Mining Model Viewer** tab, if it is not visible.</span></span>  
  
2.  <span data-ttu-id="87b63-118">单击图表视图右侧的下拉列表，选中所有复选框。</span><span class="sxs-lookup"><span data-stu-id="87b63-118">Click the drop-down list to the right of the chart view, and select all the check boxes.</span></span> [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="87b63-119">图表现在应包含 24 条不同的序列线。</span><span class="sxs-lookup"><span data-stu-id="87b63-119">The chart should now contain 24 different series lines.</span></span>  
  
3.  <span data-ttu-id="87b63-120">在图表右侧的复选框中取消选中响应的框，以临时隐藏基于 Amount 的所有序列线。</span><span class="sxs-lookup"><span data-stu-id="87b63-120">In the check boxes to the right of the chart, clear the boxes to temporarily hide the lines for all series that are based on Amount.</span></span>  
  
     <span data-ttu-id="87b63-121">然后，取消选中与 R750 和 R250 自行车有关的复选框。</span><span class="sxs-lookup"><span data-stu-id="87b63-121">Now, clear the check boxes related to the R750 and R250 bicycles.</span></span>  
  
     <span data-ttu-id="87b63-122">现在，图表仅包含以下 6 条序列线，因此您可以更方便地比较 M200 和 T1000 自行车的趋势。</span><span class="sxs-lookup"><span data-stu-id="87b63-122">The chart now contains just the following six series lines, so that can you more easily compare trends for the M200 and T1000 bicycles.</span></span>  
  
    -   <span data-ttu-id="87b63-123">**M200 欧洲：数量**</span><span class="sxs-lookup"><span data-stu-id="87b63-123">**M200 Europe: Quantity**</span></span>  
  
    -   <span data-ttu-id="87b63-124">**M200 North America:Quantity**</span><span class="sxs-lookup"><span data-stu-id="87b63-124">**M200 North America: Quantity**</span></span>  
  
    -   <span data-ttu-id="87b63-125">**M200 Pacific: Quantity**</span><span class="sxs-lookup"><span data-stu-id="87b63-125">**M200 Pacific: Quantity**</span></span>  
  
    -   <span data-ttu-id="87b63-126">**T1000 Europe: Quantity**</span><span class="sxs-lookup"><span data-stu-id="87b63-126">**T1000 Europe: Quantity**</span></span>  
  
    -   <span data-ttu-id="87b63-127">**T1000 North America: Quantity**</span><span class="sxs-lookup"><span data-stu-id="87b63-127">**T1000 North America: Quantity**</span></span>  
  
    -   <span data-ttu-id="87b63-128">**T1000 Pacific: Quantity**</span><span class="sxs-lookup"><span data-stu-id="87b63-128">**T1000 Pacific: Quantity**</span></span>  
  
 <span data-ttu-id="87b63-129">![预测 M200 和 T1000 数量的序列](../../2014/tutorials/media/6series-defaultforecasting.gif "预测 M200 和 T1000 数量的序列")</span><span class="sxs-lookup"><span data-stu-id="87b63-129">![Series predicting M200 and T1000 quantity](../../2014/tutorials/media/6series-defaultforecasting.gif "Series predicting M200 and T1000 quantity")</span></span>  
  
 <span data-ttu-id="87b63-130">在此查看器中显示的图表包括历史数据和预测数据。</span><span class="sxs-lookup"><span data-stu-id="87b63-130">The chart that is displayed in this viewer includes both historical and predicted data.</span></span> <span data-ttu-id="87b63-131">预测数据带有底纹，以便与历史数据区分开。</span><span class="sxs-lookup"><span data-stu-id="87b63-131">Predicted data is shaded to differentiate it from historical data.</span></span> <span data-ttu-id="87b63-132">为了方便比较不同的序列，您还可以更改与图形中每条线关联的颜色。</span><span class="sxs-lookup"><span data-stu-id="87b63-132">To make it easier to compare different series, you can also change the colors associated with each line in the graph.</span></span> <span data-ttu-id="87b63-133">有关详细信息，请参阅 [更改数据挖掘查看器中使用的颜色](../../2014/analysis-services/data-mining/change-the-colors-used-in-the-data-mining-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="87b63-133">For more information, see [Change the Colors Used in the Data Mining Viewer](../../2014/analysis-services/data-mining/change-the-colors-used-in-the-data-mining-viewer.md).</span></span>  
  
 <span data-ttu-id="87b63-134">从趋势线可以看出：所有区域的总销售额在普遍增长，并且每 12 个月（在 12 月）出现一次峰值。</span><span class="sxs-lookup"><span data-stu-id="87b63-134">From the trend lines, you can see that total sales for all regions are generally increasing, with a peak every 12 months in December.</span></span> <span data-ttu-id="87b63-135">通过图表，您还可以发现 T1000 自行车数据的开始时间比其他产品序列数据的开始时间晚得多。</span><span class="sxs-lookup"><span data-stu-id="87b63-135">From the chart, you can also see that the data for the T1000 bicycle starts much later than the data for the other product series.</span></span> <span data-ttu-id="87b63-136">这是因为这是一个较新的产品，但由于此序列基于的数据要少得多，预测的准确性可能相对较低。</span><span class="sxs-lookup"><span data-stu-id="87b63-136">That is because it is a newer product, but because this series is based on much less data, the predictions might not be as accurate.</span></span>  
  
 <span data-ttu-id="87b63-137">默认情况下，将为每个时序显示以虚线表示的五个预测步骤。</span><span class="sxs-lookup"><span data-stu-id="87b63-137">By default, five prediction steps are shown for each time series, displayed as dotted lines.</span></span> <span data-ttu-id="87b63-138">您可以更改此值以查看更多或更少的预测。</span><span class="sxs-lookup"><span data-stu-id="87b63-138">You can change this value to view more or fewer predictions.</span></span> <span data-ttu-id="87b63-139">您还可以通过向图表中添加误差线以图形方式查看预测的标准偏差。</span><span class="sxs-lookup"><span data-stu-id="87b63-139">You can also graphically view the standard deviation for the predictions by adding error bars to the chart.</span></span>  
  
#### <a name="to-change-prediction-and-display-options-in-the-chart-view"></a><span data-ttu-id="87b63-140">更改“图表”视图中的预测和显示选项</span><span class="sxs-lookup"><span data-stu-id="87b63-140">To change prediction and display options in the Chart view</span></span>  
  
1.  <span data-ttu-id="87b63-141">尝试逐步更改**预测步骤**的值，将其从**5**增加到**10**，然后再返回到**6**。</span><span class="sxs-lookup"><span data-stu-id="87b63-141">Try changing the value for **Prediction Steps** gradually, increasing it from **5** to **10**, and then back to **6**.</span></span>  
  
     <span data-ttu-id="87b63-142">如果历史数据具有较大波动，则随着您增大预测次数，波动会重复出现甚至被放大。</span><span class="sxs-lookup"><span data-stu-id="87b63-142">When the historical data has large fluctuations, the fluctuations tend to be repeated or even amplified as you increase the number of predictions.</span></span> <span data-ttu-id="87b63-143">此时您可能需要进行一些研究，了解历史数据出现较大增长的原因，然后决定是否接受这些结果，尝试在源数据中进行某种更正，或是对模型应用某种平滑处理。</span><span class="sxs-lookup"><span data-stu-id="87b63-143">You probably need to do some research at this point, to understand the cause of the big increase in the historical data and then decide whether to accept these results, seek some kind of correction in the source data, or apply some kind of smoothing in the model.</span></span>  
  
2.  <span data-ttu-id="87b63-144">选中 "**显示偏差**" 复选框。</span><span class="sxs-lookup"><span data-stu-id="87b63-144">Select the **Show Deviations** check box.</span></span>  
  
     <span data-ttu-id="87b63-145">此选项显示每个预测值的预估误差。</span><span class="sxs-lookup"><span data-stu-id="87b63-145">This option displays the estimated error for each predicted value.</span></span>  
  
3.  <span data-ttu-id="87b63-146">请注意 X 轴的刻度。</span><span class="sxs-lookup"><span data-stu-id="87b63-146">Note the scale of the X-axis.</span></span> <span data-ttu-id="87b63-147">历史和预测数据的更改始终表示为百分比，但实际值将被自动调整，以便所有值都能显示在图形中。</span><span class="sxs-lookup"><span data-stu-id="87b63-147">The changes over both historical and predicted data are always expressed as a percentage, but the actual values are adjusted automatically to fit all values onto the graph.</span></span> <span data-ttu-id="87b63-148">因此，在比较模型时务须小心，不要仅依赖于可见值。</span><span class="sxs-lookup"><span data-stu-id="87b63-148">Therefore you need to be careful when comparing models to not rely on visuals alone.</span></span> <span data-ttu-id="87b63-149">若要获取准确值，或者要获取百分比增加和预测值，请将鼠标悬停在虚线或实线上，或单击线条以查看 "**挖掘图例**" 中的值。</span><span class="sxs-lookup"><span data-stu-id="87b63-149">To get the exact value, or the percentage increase and value for predictions, pause the mouse over the dotted line or solid lines, or click the lines to view the values in the **Mining Legend**.</span></span>  
  
     <span data-ttu-id="87b63-150">**提示**：如果未显示 "**挖掘图例**"，请切换到 "**模型**" 视图，右键单击任意节点，然后选择 "**显示图例**"。</span><span class="sxs-lookup"><span data-stu-id="87b63-150">**Tip**: If the **Mining Legend** is not visible, switch to **Model** view, right-click any node, and select **Show Legend**.</span></span>  
  
 <span data-ttu-id="87b63-151">通过观察这些趋势，您会担心某些序列缺少数据，并想知道是否可以通过按模型（或者可能按地区）计算销售额的平均值来获取更可靠的预测。</span><span class="sxs-lookup"><span data-stu-id="87b63-151">From looking at these trends, you are concerned about the lack of data for some of the series, and wonder if you might get more reliable predictions by averaging sales by model, or perhaps averaging sales by region.</span></span> <span data-ttu-id="87b63-152">本教程后面的课程中将探讨这种方法。</span><span class="sxs-lookup"><span data-stu-id="87b63-152">You will explore this approach in a later lesson in this tutorial.</span></span>  
  
 [<span data-ttu-id="87b63-153">返回页首</span><span class="sxs-lookup"><span data-stu-id="87b63-153">Back to Top</span></span>](#bkmk_Charts)  
  
##  <a name="model-tab"></a><a name="bkmk_Model"></a><span data-ttu-id="87b63-154">模型选项卡</span><span class="sxs-lookup"><span data-stu-id="87b63-154">Model Tab</span></span>  
 <span data-ttu-id="87b63-155">在数据挖掘设计器中的时序查看器的 "**模型**" 选项卡上， [!INCLUDE[msCoName](../includes/msconame-md.md)] 您可以使用树形图形式查看预测模型。</span><span class="sxs-lookup"><span data-stu-id="87b63-155">The **Model** tab of the [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series Viewer in Data Mining Designer lets you view the forecasting model in the form of a tree graph.</span></span>  
  
 <span data-ttu-id="87b63-156">首先请注意，由于您的数据描述三个不同地区（欧洲、北美和太平洋地区）多个产品系列销售情况的两个不同的度量值（“金额”和“数量”），您所构建的模型实际包含 24 个不同的树，每个树表示由不同的地区、产品和可预测属性组合而成的销售模式的一个模型。</span><span class="sxs-lookup"><span data-stu-id="87b63-156">First, notice that because your data describes two different measures (Amount and Quantity) for sales of multiple product lines (T1000, etc.) in three different regions (Europe, North America, and Pacific), the model that you built actually contains 24 different trees, each tree representing a model of the sales patterns for a different combination of region, product, and predictable attribute.</span></span>  
  
 <span data-ttu-id="87b63-157">您可以通过从 "**模型**" 选项卡上的 "**树**" 下拉列表中选择一个序列，来选择要查看的 "产品线"、"区域" 和 "销售" 度量值的组合。</span><span class="sxs-lookup"><span data-stu-id="87b63-157">You can choose which combination of product line, region, and sales metric you want to view by selecting a series from the **Tree** dropdown list on the **Model** tab.</span></span>  
  
 <span data-ttu-id="87b63-158">那么，您可以从查看树形模型中学习到什么？</span><span class="sxs-lookup"><span data-stu-id="87b63-158">So what can you learn from viewing the model as a tree?</span></span> <span data-ttu-id="87b63-159">例如，我们比较两个模型，一个模型在树中有多个级别，另一个模型包含一个节点。</span><span class="sxs-lookup"><span data-stu-id="87b63-159">As an example, let's compare two models, one that has several levels in the tree, and one that has a single node.</span></span>  
  
-   <span data-ttu-id="87b63-160">当树形图包含单个节点时，这表示在模型中发现的趋势基本上随时间发生同质变化。</span><span class="sxs-lookup"><span data-stu-id="87b63-160">When a tree graph contains a single node, it means the trend found in the model is mostly homogenous over time.</span></span> <span data-ttu-id="87b63-161">您可以使用此单节点（标记为**全部**）来查看描述输入变量和结果之间的关系的公式。</span><span class="sxs-lookup"><span data-stu-id="87b63-161">You can use this single node, labeled **All**, to view the formula that describes the relationship between the input variables and the outcome.</span></span>  
  
-   <span data-ttu-id="87b63-162">如果某一时序的树形图包含多个分支，这表示检测到的时序太过复杂，无法表示为单个公式。</span><span class="sxs-lookup"><span data-stu-id="87b63-162">When a tree graph for a time series has multiple branches, it means the time series that was detected is too complex to be represented as a single equation.</span></span> <span data-ttu-id="87b63-163">相反，树关系图可能包含多个分支，每个分支标有导致树*拆分*的条件。</span><span class="sxs-lookup"><span data-stu-id="87b63-163">Instead, the tree graph might contain multiple branches, each branch labeled with the conditions that caused the tree to *split*.</span></span> <span data-ttu-id="87b63-164">当树拆分时，每个分支表示不同的时间段，这些时间段内的趋势可描述为单个公式。</span><span class="sxs-lookup"><span data-stu-id="87b63-164">When the tree splits, each branch represents a different segment of time, inside which the trend can be described as a single equation.</span></span>  
  
     <span data-ttu-id="87b63-165">例如，如果您查看图表图，并看到销售量在九月开始发生的突然跳转，并经历年末假期，则可以切换到 "**模型**" 视图，以查看趋势变化的准确日期。</span><span class="sxs-lookup"><span data-stu-id="87b63-165">For example, if you look at the chart graph and see a sudden jump in sales volume starting sometime in September and continuing through a year-end holiday, you can switch to the **Model** view to see the exact date where the trend changed.</span></span> <span data-ttu-id="87b63-166">表示 "九月前" 和 "九月之后" 的树中的分支将包含不同的公式：一个公式以数学方式描述了拆分的销售趋势，另一个公式描述了九月到年末假期的销售趋势。</span><span class="sxs-lookup"><span data-stu-id="87b63-166">The branches in the tree that represent "before September" and "after September" would contain different formulas: one formula that mathematically describes the sales trends up to the split, and another formula that describes sales trends for September through the year-end holiday.</span></span>  
  
#### <a name="to-explore-the-decision-tree-for-a-time-series-model"></a><span data-ttu-id="87b63-167">浏览时序模型的决策树</span><span class="sxs-lookup"><span data-stu-id="87b63-167">To explore the decision tree for a time series model</span></span>  
  
1.  <span data-ttu-id="87b63-168">在查看器的 "**模型**" 选项卡上的 "**树**" 列表中，选择 " **T1000 欧洲：金额**" 系列。</span><span class="sxs-lookup"><span data-stu-id="87b63-168">In the **Tree** list on the **Model** tab of the viewer, select the **T1000 Europe: Amount** series.</span></span>  
  
     <span data-ttu-id="87b63-169">单击标记为 "**全部**" 的节点。</span><span class="sxs-lookup"><span data-stu-id="87b63-169">Click the node labeled **All**.</span></span>  
  
     <span data-ttu-id="87b63-170">对于 "**全部**" 节点，显示的工具提示包括诸如整个系列中的事例数，以及从数据分析派生的时序公式等信息。</span><span class="sxs-lookup"><span data-stu-id="87b63-170">For an **All** node, the ToolTip that appears includes information such as, the number of cases in the entire series, and time series equations derived from analysis of the data.</span></span>  
  
2.  <span data-ttu-id="87b63-171">如果未显示 "**挖掘图例**"，请右键单击该节点，然后选择 "**显示图例**"。</span><span class="sxs-lookup"><span data-stu-id="87b63-171">If the **Mining Legend** is not visible, right-click the node and select **Show Legend**.</span></span>  
  
     <span data-ttu-id="87b63-172">**挖掘图例**提供的信息与工具提示中的信息几乎相同。</span><span class="sxs-lookup"><span data-stu-id="87b63-172">The **Mining Legend** provides much the same information that is in the Tooltip.</span></span> <span data-ttu-id="87b63-173">如有任何自变量为离散变量，您还会看到一个直方图，其中显示变量在节点中的分布。</span><span class="sxs-lookup"><span data-stu-id="87b63-173">If any of your independent variables are discrete, you will also see a histogram that shows the distribution of variables in the node.</span></span>  
  
3.  <span data-ttu-id="87b63-174">现在选择其他要查看的时序。</span><span class="sxs-lookup"><span data-stu-id="87b63-174">Now select a different time series to view.</span></span> <span data-ttu-id="87b63-175">使用查看器的 "**模型**" 选项卡上的 "**树**" 列表，选择**M200 北美：金额**系列。</span><span class="sxs-lookup"><span data-stu-id="87b63-175">Using the **Tree** list on the **Model** tab of the viewer, select the **M200 North America: Amount** series.</span></span>  
  
     <span data-ttu-id="87b63-176">树形图形现在包含一个 "**全部**" 节点和两个子节点。</span><span class="sxs-lookup"><span data-stu-id="87b63-176">The tree graph now contains an **All** node and two child nodes.</span></span> <span data-ttu-id="87b63-177">通过观察子节点上的标签，您可以发现趋势线在哪一点上发生了变化。</span><span class="sxs-lookup"><span data-stu-id="87b63-177">By looking at the labels on the child nodes, you can understand at what point the trend line changed.</span></span>  
  
     <span data-ttu-id="87b63-178">对于每个子节点，"**挖掘图例**" 中的说明还包括树的每个分支中的事例计数。</span><span class="sxs-lookup"><span data-stu-id="87b63-178">For each child node, the description in the **Mining Legend** also includes the count of cases in each branch of the tree.</span></span>  
  
 <span data-ttu-id="87b63-179">下面的列表描述了树查看器中的其他一些功能：</span><span class="sxs-lookup"><span data-stu-id="87b63-179">The following list describes some additional features in the tree viewer:</span></span>  
  
-   <span data-ttu-id="87b63-180">您可以使用 "**背景**" 控件更改图表中表示的变量。</span><span class="sxs-lookup"><span data-stu-id="87b63-180">You can change the variable that is represented in the chart by using the **Background** control.</span></span> <span data-ttu-id="87b63-181">默认情况下，较暗的节点包含更多的事例，因为 "**背景**" 的值设置为 "**填充**"。</span><span class="sxs-lookup"><span data-stu-id="87b63-181">By default, nodes that are darker contain more cases, because the value of **Background** is set to **Population**.</span></span> <span data-ttu-id="87b63-182">若要查看某个节点中有多少个事例，请将鼠标悬停在某个节点上，并查看显示的工具提示，或单击该节点，然后在 "**节点图例**" 窗口中查看数字。</span><span class="sxs-lookup"><span data-stu-id="87b63-182">To see just how many cases there are in a node, pause the mouse over a node and view the ToolTip that appears, or click the node and view the numbers in the **Node Legend** window.</span></span>  
  
-   <span data-ttu-id="87b63-183">还可以在工具提示中（或通过单击该节点）查看该节点的回归公式。</span><span class="sxs-lookup"><span data-stu-id="87b63-183">The regression formula for the node can also be viewed in the ToolTip, or by clicking the node.</span></span> <span data-ttu-id="87b63-184">如果创建了混合模型，则会看到两个公式：一个用于 ARTXP（在叶节点中），一个用于 ARIMA（在树的根节点中）。</span><span class="sxs-lookup"><span data-stu-id="87b63-184">If you have created a mixed model, you can see two formulas, one for ARTXP (in the leaf nodes) and one for ARIMA (in the root node of the tree).</span></span>  
  
-   <span data-ttu-id="87b63-185">节点中使用多个小菱形来表示连续数值。</span><span class="sxs-lookup"><span data-stu-id="87b63-185">The little diamonds are used in nodes that represent continuous numbers.</span></span> <span data-ttu-id="87b63-186">菱形所在的条形中会显示属性的范围。</span><span class="sxs-lookup"><span data-stu-id="87b63-186">The range of the attributes is shown in the bar on which the diamond rests.</span></span> <span data-ttu-id="87b63-187">菱形在节点均值处居中显示，其宽度表示该节点处属性的方差。</span><span class="sxs-lookup"><span data-stu-id="87b63-187">The diamond is centered on the mean for the node, and the width of the diamond represents the variance of the attribute at that node.</span></span>  
  
 [<span data-ttu-id="87b63-188">返回页首</span><span class="sxs-lookup"><span data-stu-id="87b63-188">Back to Top</span></span>](#bkmk_Charts)  
  
##  <a name="optional-generic-content-tree-viewer"></a><a name="bkmk_Content"></a> <span data-ttu-id="87b63-189">(可选) 一般内容树查看器</span><span class="sxs-lookup"><span data-stu-id="87b63-189">(Optional) Generic Content Tree Viewer</span></span>  
 <span data-ttu-id="87b63-190">除了时序的自定义查看器外， [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 还提供了**MicrosoftGeneric 内容树查看器**，以用于所有数据挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="87b63-190">In addition to the custom viewer for time series, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] provides the **MicrosoftGeneric Content Tree Viewer** for use with all data mining models.</span></span> <span data-ttu-id="87b63-191">此查看器具有以下优点：</span><span class="sxs-lookup"><span data-stu-id="87b63-191">This viewer provides some advantages:</span></span>  
  
-   <span data-ttu-id="87b63-192">**Microsoft 时序查看器**：此视图合并两个算法的结果。</span><span class="sxs-lookup"><span data-stu-id="87b63-192">**Microsoft Time Series Viewer**: This view merges the results of the two algorithms.</span></span> <span data-ttu-id="87b63-193">尽管您可以分别查看每个序列，但您无法确定每种算法的结果是如何合并的。</span><span class="sxs-lookup"><span data-stu-id="87b63-193">Although you can view each series separately, you cannot determine how the results of each algorithm were combined.</span></span> <span data-ttu-id="87b63-194">此外，在此视图中，工具提示和挖掘图例只显示最重要的统计数据。</span><span class="sxs-lookup"><span data-stu-id="87b63-194">Also, in this view, the Tooltips and Mining Legend show only the most important statistics.</span></span>  
  
-   <span data-ttu-id="87b63-195">**一般内容树查看器**：使你能够在一次浏览和查看模型中使用的所有数据序列，如果你创建了混合模型，则 ARIMA 和 ARTXP 树都将显示在同一图表中。</span><span class="sxs-lookup"><span data-stu-id="87b63-195">**Generic Content Tree Viewer**: Lets you browse and view all of the data series that were used in the model at one time, and if you have created a mixed model, both the ARIMA and ARTXP trees are displayed in the same graph.</span></span>  
  
     <span data-ttu-id="87b63-196">您可以使用此查看器获取两种算法的所有统计数据以及这些值的分布。</span><span class="sxs-lookup"><span data-stu-id="87b63-196">You can use this viewer to get all the statistics from both algorithms, as well as distributions of the values.</span></span>  
  
     <span data-ttu-id="87b63-197">对于要深入了解 ARIMA 和 ARTXP 分析结果的数据挖掘专家级用户，推荐使用此查看器。</span><span class="sxs-lookup"><span data-stu-id="87b63-197">Recommended for expert users of data mining who want to know more about the ARIMA and ARTXP analyses.</span></span>  
  
#### <a name="to-view-details-for-a-particular-data-series-in-the-generic-content-viewer"></a><span data-ttu-id="87b63-198">在一般内容查看器中查看特定数据序列的详细信息</span><span class="sxs-lookup"><span data-stu-id="87b63-198">To view details for a particular data series in the generic content viewer</span></span>  
  
1.  <span data-ttu-id="87b63-199">在 "**挖掘模型查看器**" 选项卡中，从 "**查看器**" 下拉列表中选择 " **Microsoft 一般内容树查看器**"。</span><span class="sxs-lookup"><span data-stu-id="87b63-199">In the **Mining Model Viewer** tab, select **Microsoft Generic Content Tree Viewer** from the **Viewer** drop-down list.</span></span>  
  
2.  <span data-ttu-id="87b63-200">在 "**节点标题**" 窗格中，单击 "最顶层 (所有) " 节点。</span><span class="sxs-lookup"><span data-stu-id="87b63-200">In the **Node Caption** pane, click the topmost (All) node.</span></span>  
  
3.  <span data-ttu-id="87b63-201">在 "**节点详细信息**" 窗格中，查看 ATTRIBUTE_NAME 的值。</span><span class="sxs-lookup"><span data-stu-id="87b63-201">In the **Node Details** pane, view the value for ATTRIBUTE_NAME.</span></span>  
  
     <span data-ttu-id="87b63-202">此值会显示该节点中包含哪个序列或产品和区域的哪个组合。</span><span class="sxs-lookup"><span data-stu-id="87b63-202">This value shows you which series, or combination of product and region, is contained in this node.</span></span> <span data-ttu-id="87b63-203">在 AdventureWorks 示例中，最顶部的节点是 M200 Europe 序列的节点。</span><span class="sxs-lookup"><span data-stu-id="87b63-203">In the AdventureWorks example, the topmost node is for the M200 Europe series.</span></span>  
  
4.  <span data-ttu-id="87b63-204">在 "**节点标题**" 窗格中，找到具有子节点的第一个节点。</span><span class="sxs-lookup"><span data-stu-id="87b63-204">In the **Node Caption** pane, locate the first node that has child nodes.</span></span>  
  
     <span data-ttu-id="87b63-205">如果某个序列节点有子级，则在 Microsoft 时序查看器的 "**模型**" 选项卡上显示的树视图也将有一个分支结构。</span><span class="sxs-lookup"><span data-stu-id="87b63-205">If a series node has children, the tree view that appears on the **Model** tab of the Microsoft Time Series Viewer will also have a branching structure.</span></span>  
  
5.  <span data-ttu-id="87b63-206">展开该节点，然后单击某个子节点。</span><span class="sxs-lookup"><span data-stu-id="87b63-206">Expand the node and click one of the child nodes.</span></span>  
  
     <span data-ttu-id="87b63-207">架构的 NODE_DESCRIPTION 列包含导致树拆分的条件。</span><span class="sxs-lookup"><span data-stu-id="87b63-207">The NODE_DESCRIPTION column of the schema contains the condition that caused the tree to split.</span></span>  
  
6.  <span data-ttu-id="87b63-208">在 "**节点标题**" 窗格中，单击最顶层的 ARIMA 节点，然后展开该节点，直到所有子节点都可见。</span><span class="sxs-lookup"><span data-stu-id="87b63-208">In the **Node Caption** pane, click the topmost ARIMA node, and expand the node until all child nodes are visible.</span></span>  
  
7.  <span data-ttu-id="87b63-209">在 "**节点详细信息**" 窗格中，查看 ATTRIBUTE_NAME 的值。</span><span class="sxs-lookup"><span data-stu-id="87b63-209">In the **Node Details** pane, view the value for ATTRIBUTE_NAME.</span></span>  
  
     <span data-ttu-id="87b63-210">此值会指出该节点中包含哪个时序。</span><span class="sxs-lookup"><span data-stu-id="87b63-210">This value tells you which time series is contained in this node.</span></span> <span data-ttu-id="87b63-211">ARIMA 部分中最顶部的节点应该与（“全部”）部分中最顶部的节点相匹配。</span><span class="sxs-lookup"><span data-stu-id="87b63-211">The topmost node in the ARIMA section should match the topmost node in the (All) section.</span></span> <span data-ttu-id="87b63-212">在 AdventureWorks 示例中，该节点包含序列 M200 Europe 的 ARIMA 分析。</span><span class="sxs-lookup"><span data-stu-id="87b63-212">In the AdventureWorks example, this node contains the ARIMA analysis for the series, M200 Europe.</span></span>  
  
 <span data-ttu-id="87b63-213">有关详细信息，请参阅[时序模型的挖掘模型内容](../../2014/analysis-services/data-mining/mining-model-content-for-time-series-models-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="87b63-213">For more information, see [Mining Model Content for Time Series Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-time-series-models-analysis-services-data-mining.md).</span></span>  
  
 [<span data-ttu-id="87b63-214">返回页首</span><span class="sxs-lookup"><span data-stu-id="87b63-214">Back to Top</span></span>](#bkmk_Charts)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="87b63-215">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="87b63-215">Next Task in Lesson</span></span>  
 [<span data-ttu-id="87b63-216">&#40;中级数据挖掘教程创建时序预测&#41;</span><span class="sxs-lookup"><span data-stu-id="87b63-216">Creating Time Series Predictions &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-time-series-predictions-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="87b63-217">另请参阅</span><span class="sxs-lookup"><span data-stu-id="87b63-217">See Also</span></span>  
 <span data-ttu-id="87b63-218">[时序模型查询示例](../../2014/analysis-services/data-mining/time-series-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="87b63-218">[Time Series Model Query Examples](../../2014/analysis-services/data-mining/time-series-model-query-examples.md) </span></span>  
 [<span data-ttu-id="87b63-219">Microsoft Time Series Algorithm Technical Reference</span><span class="sxs-lookup"><span data-stu-id="87b63-219">Microsoft Time Series Algorithm Technical Reference</span></span>](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)  
  
  
