---
title: 用于 Excel) 的预测 (表分析工具 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- forecasting
- mining model, time series
- time series [data mining]
ms.assetid: 22bb0b5e-78f5-484e-883d-2b5985a12749
author: minewiskan
ms.author: owend
ms.openlocfilehash: abca22dbcb9ae6426e839f92e391a658f5029e31
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579170"
---
# <a name="forecast-table-analysis-tools-for-excel"></a><span data-ttu-id="e711d-102">预测（Excel 表分析工具）</span><span class="sxs-lookup"><span data-stu-id="e711d-102">Forecast (Table Analysis Tools for Excel)</span></span>
  <span data-ttu-id="e711d-103">![“表分析工具”功能区中的“预测”按钮](media/tat-forecast.gif "“表分析工具”功能区中的“预测”按钮")</span><span class="sxs-lookup"><span data-stu-id="e711d-103">![Forecast button in Table Analysis tools ribbon](media/tat-forecast.gif "Forecast button in Table Analysis tools ribbon")</span></span>  
  
 <span data-ttu-id="e711d-104">**预测**工具可帮助您基于 Excel 数据表或其他数据源中的数据进行预测，并可选择查看与每个预测值相关联的概率。</span><span class="sxs-lookup"><span data-stu-id="e711d-104">The **Forecast** tool helps you make predictions based on data in an Excel data table or other data source, and optionally view the probabilities associated with each predicted value.</span></span> <span data-ttu-id="e711d-105">例如，如果数据包含一个日期列，另外还包含一个显示该月每天总销售额的列，则您可以预测将来某些天的销售额。</span><span class="sxs-lookup"><span data-stu-id="e711d-105">For example, if your data contains a date column and a column that shows total sales for each day of the month, you could predict the sales for future days.</span></span> <span data-ttu-id="e711d-106">还可以指定要进行的预测数。</span><span class="sxs-lookup"><span data-stu-id="e711d-106">You can also specify the number of predictions to make.</span></span> <span data-ttu-id="e711d-107">例如，可以预测 5 天或 30 天。</span><span class="sxs-lookup"><span data-stu-id="e711d-107">For example, you can predict five days, or thirty.</span></span>  
  
 <span data-ttu-id="e711d-108">该工具完成后，它将新预测追加到源数据表的末尾，并突出显示新值。</span><span class="sxs-lookup"><span data-stu-id="e711d-108">When the tool completes, it appends the new predictions to the end of the source data table, and highlights the new values.</span></span> <span data-ttu-id="e711d-109">新的时序值不追加，这使您可以首先查看预测。</span><span class="sxs-lookup"><span data-stu-id="e711d-109">New time series values are not appended; this allows you to review the predictions first.</span></span>  
  
 <span data-ttu-id="e711d-110">该工具还会创建一个名为 "**预测报表**" 的新工作表。</span><span class="sxs-lookup"><span data-stu-id="e711d-110">The tool also creates a new worksheet named **Forecasting Report**.</span></span> <span data-ttu-id="e711d-111">此工作表报告向导是否已成功创建预测。</span><span class="sxs-lookup"><span data-stu-id="e711d-111">This worksheet reports whether the wizard successfully created a prediction.</span></span> <span data-ttu-id="e711d-112">新工作表还包含一个显示历史趋势的折线图。</span><span class="sxs-lookup"><span data-stu-id="e711d-112">The new worksheet also contains a line graph that shows the historical trends.</span></span>  
  
 <span data-ttu-id="e711d-113">当您将时序扩展为包含新的预测时，预测值将添加到折线图中。</span><span class="sxs-lookup"><span data-stu-id="e711d-113">When you extend the time series to include the new predictions, the predicted values are added to the line graph.</span></span> <span data-ttu-id="e711d-114">历史值以实线显示，预测以点线显示。</span><span class="sxs-lookup"><span data-stu-id="e711d-114">The historical values are shown as a solid line and the predictions are shown as a dotted line.</span></span>  
  
## <a name="using-the-forecast-tool"></a><span data-ttu-id="e711d-115">使用预测工具</span><span class="sxs-lookup"><span data-stu-id="e711d-115">Using the Forecast Tool</span></span>  
  
1.  <span data-ttu-id="e711d-116">打开包含可预测数值数据的 Excel 表。</span><span class="sxs-lookup"><span data-stu-id="e711d-116">Open an Excel table that contains predictable numeric data.</span></span>  
  
2.  <span data-ttu-id="e711d-117">单击 "**分析**" 选项卡上的 "**预测**"。</span><span class="sxs-lookup"><span data-stu-id="e711d-117">Click **Forecast** on the **Analyze** tab.</span></span>  
  
3.  <span data-ttu-id="e711d-118">指定要预测的列。</span><span class="sxs-lookup"><span data-stu-id="e711d-118">Specify the columns to forecast.</span></span> <span data-ttu-id="e711d-119">该工具会自动选择数据中具有可预测数据类型的列，即连续数值数据。</span><span class="sxs-lookup"><span data-stu-id="e711d-119">The tool automatically selects columns in the data that have a predictable data type-that is, continuous numeric data.</span></span> <span data-ttu-id="e711d-120">如果某些具有连续数值数据的列包含许多 null 值或零值，由于缺少数据可能影响结果，该工具可能不会选择这些列。</span><span class="sxs-lookup"><span data-stu-id="e711d-120">The tool might not select some columns that have continuous numeric data if the columns contain many null or zero values, because the missing data might affect the results.</span></span> <span data-ttu-id="e711d-121">如果发生这种情况，可以使用 "重新[标记 &#40;SQL Server 数据挖掘外接程序"&#41;](relabel-sql-server-data-mining-add-ins.md)工具来修复数据。</span><span class="sxs-lookup"><span data-stu-id="e711d-121">If this happens, you can fix the data by using the [Relabel &#40;SQL Server Data Mining Add-ins&#41;](relabel-sql-server-data-mining-add-ins.md) tool.</span></span>  
  
4.  <span data-ttu-id="e711d-122">指定包含日期、时间或其他序列标识符的列。</span><span class="sxs-lookup"><span data-stu-id="e711d-122">Specify the column that contains the date, time, or other series identifier.</span></span> <span data-ttu-id="e711d-123">如果选择该选项 **\<no time stamp>** ，该工具将基于源数据中的行序列创建一个序列。</span><span class="sxs-lookup"><span data-stu-id="e711d-123">If you select the option **\<no time stamp>** the tool will create a series based on the sequence of rows in the source data.</span></span>  
  
5.  <span data-ttu-id="e711d-124">指定要进行的预测数。</span><span class="sxs-lookup"><span data-stu-id="e711d-124">Specify the number of predictions to make.</span></span>  
  
6.  <span data-ttu-id="e711d-125">或者，为算法提供关于您希望数据每周、每月还是按其他时间间隔重复的提示。</span><span class="sxs-lookup"><span data-stu-id="e711d-125">Optionally, provide a hint to the algorithm about whether you expect your data to repeat weekly, monthly, or in other periods.</span></span> <span data-ttu-id="e711d-126">如果数据不符合任何给定模式，或者不知道任何模式，请选择 **\<detect automatically>** 使该工具查找重复的时间段。</span><span class="sxs-lookup"><span data-stu-id="e711d-126">If your data does not fit any of the given patterns, or if you are unaware of any patterns, select **\<detect automatically>** to have the tool find the repeating time periods.</span></span>  
  
7.  <span data-ttu-id="e711d-127">向导将预测添加到源表中，并在新的工作表中创建预测报表。</span><span class="sxs-lookup"><span data-stu-id="e711d-127">The wizard adds the predictions to the source table, and creates a forecasting report in a new worksheet.</span></span>  
  
8.  <span data-ttu-id="e711d-128">若要将这些新值添加到预测图形中，请将时序扩展为包含预测值。</span><span class="sxs-lookup"><span data-stu-id="e711d-128">To add the new values to the prediction graph, extend the time series to include the forecasted values.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="e711d-129">要求</span><span class="sxs-lookup"><span data-stu-id="e711d-129">Requirements</span></span>  
 <span data-ttu-id="e711d-130">您预测的列必须包含连续的数值数据，如货币或其他数字。</span><span class="sxs-lookup"><span data-stu-id="e711d-130">The columns that you predict must contain continuous numeric data, such as currency or other numbers.</span></span>  
  
 <span data-ttu-id="e711d-131">如果可能，您的数据还应包含一列，该列的内容是时间或日期序列。</span><span class="sxs-lookup"><span data-stu-id="e711d-131">If possible, your data should also include a column that contains a series of times or dates.</span></span> <span data-ttu-id="e711d-132">可以使用数字序列 (1，2，3 ... ) ，而不是日期和时间数据。</span><span class="sxs-lookup"><span data-stu-id="e711d-132">You can use a numeric series (1,2,3....) instead of date and time data.</span></span> <span data-ttu-id="e711d-133">不过，序列列中的值必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="e711d-133">However, values in the series column must be unique.</span></span> <span data-ttu-id="e711d-134">如果**预测**工具在序列列中发现重复值，则会发生错误。</span><span class="sxs-lookup"><span data-stu-id="e711d-134">An error occurs if the **Forecast** tool finds duplicate values in the series column.</span></span>  
  
 <span data-ttu-id="e711d-135">不能使用**预测**工具预测日期。</span><span class="sxs-lookup"><span data-stu-id="e711d-135">You cannot predict a date by using the **Forecast** tool.</span></span> <span data-ttu-id="e711d-136">虽然不会出现错误，但此算法没有设计为将日期用作可预测值。</span><span class="sxs-lookup"><span data-stu-id="e711d-136">Although an error might not occur, this algorithm is not designed to use dates as predictable values.</span></span>  
  
### <a name="understanding-time-stamps"></a><span data-ttu-id="e711d-137">了解时间戳</span><span class="sxs-lookup"><span data-stu-id="e711d-137">Understanding Time Stamps</span></span>  
 <span data-ttu-id="e711d-138">必须标识要用作*时间戳*的列。</span><span class="sxs-lookup"><span data-stu-id="e711d-138">You must identify a column to use as a *time stamp*.</span></span> <span data-ttu-id="e711d-139">该时间戳具有两个用途。</span><span class="sxs-lookup"><span data-stu-id="e711d-139">The time stamp serves two purposes.</span></span> <span data-ttu-id="e711d-140">第一，它唯一标识时序中的值。</span><span class="sxs-lookup"><span data-stu-id="e711d-140">First, it uniquely identifies a value in a time series.</span></span> <span data-ttu-id="e711d-141">例如，如果要跟踪每天的销售情况，则每天应只有一个销售值。</span><span class="sxs-lookup"><span data-stu-id="e711d-141">For example, if you are tracking sales on a daily basis, you should have only one sales value for each day.</span></span> <span data-ttu-id="e711d-142">日历日期可以用作时间戳。</span><span class="sxs-lookup"><span data-stu-id="e711d-142">The calendar date can be used as the time stamp.</span></span> <span data-ttu-id="e711d-143">第二，时间戳列指示进行预测的单位。</span><span class="sxs-lookup"><span data-stu-id="e711d-143">Second, the time stamp column indicates the unit for making predictions.</span></span> <span data-ttu-id="e711d-144">如果要跟踪每天的销售情况，则预测也将以天为单位。</span><span class="sxs-lookup"><span data-stu-id="e711d-144">If you are tracking daily sales, your predictions will also be in units of days.</span></span>  
  
 <span data-ttu-id="e711d-145">如果数据不包括日期或时间列，则工具将自动创建一个名为 _RowIndex 的临时序列键。</span><span class="sxs-lookup"><span data-stu-id="e711d-145">If your data does not include a date or time column, the tool will automatically create a temporary series key, named _RowIndex.</span></span> <span data-ttu-id="e711d-146">该序列键将基于数据集中行的顺序。</span><span class="sxs-lookup"><span data-stu-id="e711d-146">The key will be based on the order of the rows in the data set.</span></span>  
  
 <span data-ttu-id="e711d-147">在指定预测数时，请输入一个整数来表示步骤数。</span><span class="sxs-lookup"><span data-stu-id="e711d-147">When you specify the number of predictions, you enter a whole number that indicates the number of steps.</span></span> <span data-ttu-id="e711d-148">这些步骤的单位取决于数据中的时间和日期序列所使用的单位。</span><span class="sxs-lookup"><span data-stu-id="e711d-148">The units for these steps depend on the units used in the time and date series in your data.</span></span> <span data-ttu-id="e711d-149">如果数据是按月列出销售结果，则预测将按照月份进行预测。</span><span class="sxs-lookup"><span data-stu-id="e711d-149">If your data lists sales results by the month, the prediction will be for a series of months.</span></span> <span data-ttu-id="e711d-150">除非更改源数据，否则无法更改时间单位。</span><span class="sxs-lookup"><span data-stu-id="e711d-150">You cannot change the units of time unless you change the source data.</span></span>  
  
### <a name="understanding-periodicity"></a><span data-ttu-id="e711d-151">了解周期</span><span class="sxs-lookup"><span data-stu-id="e711d-151">Understanding Periodicity</span></span>  
 <span data-ttu-id="e711d-152">预测以各时间段内的重复模式为基础。</span><span class="sxs-lookup"><span data-stu-id="e711d-152">A forecast is based on repeating patterns over a period of time.</span></span> <span data-ttu-id="e711d-153">因此，Microsoft 时序算法通过计算来确定具有最强模式的时间段。</span><span class="sxs-lookup"><span data-stu-id="e711d-153">Therefore, the Microsoft Time Series algorithm performs calculations to determine the time periods that have the strongest patterns.</span></span> <span data-ttu-id="e711d-154">*周期*指的是这些时间段。</span><span class="sxs-lookup"><span data-stu-id="e711d-154">*Periodicity* refers to these time periods.</span></span>  
  
 <span data-ttu-id="e711d-155">一个时序可以包含很多潜在模式。</span><span class="sxs-lookup"><span data-stu-id="e711d-155">A time series can contain many potential patterns.</span></span> <span data-ttu-id="e711d-156">如果您确信数据中包含某种模式，则通过提供算法提示可能可以改善预测的质量。</span><span class="sxs-lookup"><span data-stu-id="e711d-156">If you are certain that your data contains a certain pattern, you may be able to improve the quality of prediction by providing a hint to the algorithm.</span></span>  
  
 <span data-ttu-id="e711d-157">例如，如果您希望数据每周重复，则可以选择“每周”来指示算法应查找每周模式。</span><span class="sxs-lookup"><span data-stu-id="e711d-157">For example, if you expect that your data repeats on a weekly basis, you can select Weekly to indicate that the algorithm should look for weekly patterns.</span></span> <span data-ttu-id="e711d-158">不过，如果找不到较强的每周模式，算法将忽略该提示。</span><span class="sxs-lookup"><span data-stu-id="e711d-158">However, if no strong weekly patterns are found, the algorithm will ignore the hint.</span></span>  
  
## <a name="understanding-the-forecasting-report"></a><span data-ttu-id="e711d-159">理解预测报表</span><span class="sxs-lookup"><span data-stu-id="e711d-159">Understanding the Forecasting Report</span></span>  
 <span data-ttu-id="e711d-160">在此图形中，数据表中的历史值以黑线显示。</span><span class="sxs-lookup"><span data-stu-id="e711d-160">In this graph, the historical values from your data table appear as a dark line.</span></span> <span data-ttu-id="e711d-161">预测值以点线显示。</span><span class="sxs-lookup"><span data-stu-id="e711d-161">The predicted values appear as dotted lines.</span></span> <span data-ttu-id="e711d-162">可以单击线中的某个点来查看预测值。</span><span class="sxs-lookup"><span data-stu-id="e711d-162">You can click a point on the line to see the forecasted value.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e711d-163">如果看不到关系图中预测值的时间轴上的标签，请打开包含预测值的工作表，并使用 Excel 中的 "**填充"、"序列**" 功能将时间戳列扩展为包含预测值。</span><span class="sxs-lookup"><span data-stu-id="e711d-163">If you do not see labels on the time axis for the predicted values in the graph, open the worksheet that contains the predicted values, and use the **Fill, Series** function in Excel to extend the time stamp column to include the predicted values.</span></span>  
  
 <span data-ttu-id="e711d-164">在某些情况下，预测包含的时间段少于所请求的数量。</span><span class="sxs-lookup"><span data-stu-id="e711d-164">In some cases, the forecast may not have as many time slices as requested.</span></span> <span data-ttu-id="e711d-165">这通常意味着数据太少，不允许该算法对遥远的将来进行预测。</span><span class="sxs-lookup"><span data-stu-id="e711d-165">This usually means that data was insufficient to allow the algorithm to forecast that far into the future.</span></span> <span data-ttu-id="e711d-166">**预测**工具只会进行符合最小概率阈值的预测。</span><span class="sxs-lookup"><span data-stu-id="e711d-166">The **Forecast** tool will only make predictions that meet a minimum probability threshold.</span></span>  
  
## <a name="related-tools"></a><span data-ttu-id="e711d-167">相关工具</span><span class="sxs-lookup"><span data-stu-id="e711d-167">Related Tools</span></span>  
 <span data-ttu-id="e711d-168">Excel 数据挖掘客户端是一个独立的外接程序，它提供了更高级的数据挖掘功能，而且还包含一个用来进行预测的向导。</span><span class="sxs-lookup"><span data-stu-id="e711d-168">The Data Mining Client for Excel, which is a separate add-in that provides more advanced data mining functionality, also contains a wizard for forecasting.</span></span>  
  
 <span data-ttu-id="e711d-169">在 Excel 的 "数据挖掘客户端" 中，**预测**工具 (在 Excel 的表分析工具) 和**预测**向导 (，) 使用时序 [!INCLUDE[msCoName](../includes/msconame-md.md)] 算法。</span><span class="sxs-lookup"><span data-stu-id="e711d-169">Both the **Forecast** tool (in the Table Analysis Tools for Excel) and the **Forecast** wizard (in the Data Mining Client for Excel) use the [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series algorithm.</span></span>  
  
-   <span data-ttu-id="e711d-170">**预测**工具更易于使用，因为它会自动将算法配置为使用最适合您的数据的设置。</span><span class="sxs-lookup"><span data-stu-id="e711d-170">The **Forecast** tool is easier to use because it automatically configures the algorithm to use the settings that are best for your data.</span></span>  
  
-   <span data-ttu-id="e711d-171">Excel 数据挖掘客户端中的**预测**向导提供了自定义参数的功能。</span><span class="sxs-lookup"><span data-stu-id="e711d-171">The **Forecast** wizard in the Data Mining Client for Excel provides you with the ability to customize the parameters.</span></span>  
  
 <span data-ttu-id="e711d-172">有关**预测**向导的详细信息，请参阅用于[Excel 的数据挖掘外接程序的预测向导 &#40;&#41;](forecast-wizard-data-mining-add-ins-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="e711d-172">For more information about the **Forecast** wizard, see [Forecast Wizard &#40;Data Mining Add-ins for Excel&#41;](forecast-wizard-data-mining-add-ins-for-excel.md).</span></span> <span data-ttu-id="e711d-173">有关用来进行预测的算法的详细信息，请参阅 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 联机丛书中的主题“Microsoft 时序算法”。</span><span class="sxs-lookup"><span data-stu-id="e711d-173">For more information about the algorithm used for forecasting, see the topic "Microsoft Time Series Algorithm" in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e711d-174">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e711d-174">See Also</span></span>  
 [<span data-ttu-id="e711d-175">Excel 表分析工具</span><span class="sxs-lookup"><span data-stu-id="e711d-175">Table Analysis Tools for Excel</span></span>](table-analysis-tools-for-excel.md)  
  
  
