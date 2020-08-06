---
title: 探索呼叫中心模型 (中级数据挖掘教程) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 9095212c-9068-4dd8-85ce-17a467adeabb
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2aceec298ba78e29988571293f8422ab9e55aa97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690936"
---
# <a name="exploring-the-call-center-model-intermediate-data-mining-tutorial"></a><span data-ttu-id="34b9a-102">探索呼叫中心模型（数据挖掘中级教程）</span><span class="sxs-lookup"><span data-stu-id="34b9a-102">Exploring the Call Center Model (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="34b9a-103">您已生成了探索模型，现在可以使用 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 提供的以下工具来了解有关数据的更多信息。</span><span class="sxs-lookup"><span data-stu-id="34b9a-103">Now that you have built the exploratory model, you can use it to learn more about your data by using the following tools provided in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
-   <span data-ttu-id="34b9a-104">[Microsoft 神经网络查看](#bkmk_NNviewer)器 **：** 该查看器位于数据挖掘设计器的 "**挖掘模型查看器**" 选项卡中，旨在帮助您试验数据中的交互。</span><span class="sxs-lookup"><span data-stu-id="34b9a-104">[Microsoft Neural Network Viewer](#bkmk_NNviewer) **:** This viewer is available in the **Mining Model Viewer** tab of Data Mining Designer, and is designed to help you experiment with interactions in the data.</span></span>  
  
-   <span data-ttu-id="34b9a-105">[Microsoft 一般内容树查看器](#bkmk_genviewer) **：** 此标准查看器提供有关算法在生成模型时所发现的模式和统计信息的详细信息。</span><span class="sxs-lookup"><span data-stu-id="34b9a-105">[Microsoft Generic Content Tree Viewer](#bkmk_genviewer) **:** This standard viewer provides in-depth detail about the patterns and statistics discovered by the algorithm when it generated the model.</span></span>  
  
##  <a name="microsoft-neural-network-viewer"></a><a name="bkmk_NNviewer"></a><span data-ttu-id="34b9a-106">Microsoft 神经网络查看器</span><span class="sxs-lookup"><span data-stu-id="34b9a-106">Microsoft Neural Network Viewer</span></span>  
 <span data-ttu-id="34b9a-107">查看器有三个窗格-**输入**、**输出**和**变量**。</span><span class="sxs-lookup"><span data-stu-id="34b9a-107">The viewer has three panes - **Input**, **Output**, and **Variables**.</span></span>  
  
 <span data-ttu-id="34b9a-108">通过使用 "**输出**" 窗格，可以为可预测属性或依赖变量选择不同的值。</span><span class="sxs-lookup"><span data-stu-id="34b9a-108">By using the **Output** pane, you can select different values for the predictable attribute, or dependent variable.</span></span> <span data-ttu-id="34b9a-109">如果模型包含多个可预测属性，则可以从 "**输出属性**" 列表中选择属性。</span><span class="sxs-lookup"><span data-stu-id="34b9a-109">If your model contains multiple predictable attributes, you can select the attribute from the **Output Attribute** list.</span></span>  
  
 <span data-ttu-id="34b9a-110">"**变量**" 窗格比较您在参与特性或变量方面所选的两个结果。</span><span class="sxs-lookup"><span data-stu-id="34b9a-110">The **Variables** pane compares the two outcomes that you chose in terms of contributing attributes, or variables.</span></span> <span data-ttu-id="34b9a-111">彩色条直观的表示变量对目标结果的影响程度。</span><span class="sxs-lookup"><span data-stu-id="34b9a-111">The colored bars visually represent how strongly the variable affects the target outcomes.</span></span> <span data-ttu-id="34b9a-112">您还可以查看变量的提升分数。</span><span class="sxs-lookup"><span data-stu-id="34b9a-112">You can also view lift scores for the variables.</span></span> <span data-ttu-id="34b9a-113">提升分数的计算方法不同，具体取决于使用的挖掘模型类型，但通常会告诉您使用此属性进行预测时在模型中的提高程度。</span><span class="sxs-lookup"><span data-stu-id="34b9a-113">A lift score is calculated differently depending on which mining model type you are using, but generally tells you the improvement in the model when using this attribute for prediction.</span></span>  
  
 <span data-ttu-id="34b9a-114">通过 "**输入**" 窗格，您可以向模型添加影响方，以尝试各种假设方案。</span><span class="sxs-lookup"><span data-stu-id="34b9a-114">The **Input** pane lets you add influencers to the model to try out various what-if scenarios.</span></span>  
  
### <a name="using-the-output-pane"></a><span data-ttu-id="34b9a-115">使用“输出”窗格</span><span class="sxs-lookup"><span data-stu-id="34b9a-115">Using the Output Pane</span></span>  
 <span data-ttu-id="34b9a-116">在此初始模型中，您会希望看到各种因素是如何影响服务等级的。</span><span class="sxs-lookup"><span data-stu-id="34b9a-116">In this initial model, you are interested in seeing how various factors affect the grade of service.</span></span> <span data-ttu-id="34b9a-117">为此，您可以从输出属性列表中选择 "服务级别"，然后通过从 "**值 1** " 和 "**值 2**" 下拉列表中选择范围来比较不同级别的服务。</span><span class="sxs-lookup"><span data-stu-id="34b9a-117">To do this, you can select Service Grade from the list of output attributes, and then compare different levels of service by selecting ranges from the dropdown lists for **Value 1** and **Value 2**.</span></span>  
  
##### <a name="to-compare-lowest-and-highest-service-grades"></a><span data-ttu-id="34b9a-118">比较最低服务等级和最高服务等级</span><span class="sxs-lookup"><span data-stu-id="34b9a-118">To compare lowest and highest service grades</span></span>  
  
1.  <span data-ttu-id="34b9a-119">对于 "**值 1**"，请选择具有最小值的范围。</span><span class="sxs-lookup"><span data-stu-id="34b9a-119">For **Value 1**, select the range with the lowest values.</span></span> <span data-ttu-id="34b9a-120">例如，范围 0-0-0.7 表示最低的挂断率，因此为最佳服务级别。</span><span class="sxs-lookup"><span data-stu-id="34b9a-120">For example, the range 0-0-0.7 represents the lowest abandon rates, and therefore the best level of service.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="34b9a-121">根据模型的配置方式，此范围内的确切值可能会有所不同。</span><span class="sxs-lookup"><span data-stu-id="34b9a-121">The exact values in this range may vary depending on how you configured the model.</span></span>  
  
2.  <span data-ttu-id="34b9a-122">对于 "**值 2**"，请选择具有最高值的范围。</span><span class="sxs-lookup"><span data-stu-id="34b9a-122">For **Value 2**, select the range with the highest values.</span></span> <span data-ttu-id="34b9a-123">例如，值为 >= 0.12 的范围表示最高的放弃率，因此是最差的服务等级。</span><span class="sxs-lookup"><span data-stu-id="34b9a-123">For example, the range with the value >=0.12 represents the highest abandon rates, and therefore the worst service grade.</span></span> <span data-ttu-id="34b9a-124">换句话说，在此班次期间，打电话的客户有 12% 在与代表通话之前就挂断了电话。</span><span class="sxs-lookup"><span data-stu-id="34b9a-124">In other words, 12% of the customers who phoned during this shift hung up before speaking to a representative.</span></span>  
  
     <span data-ttu-id="34b9a-125">"**变量**" 窗格的内容会进行更新，以比较影响结果值的属性。</span><span class="sxs-lookup"><span data-stu-id="34b9a-125">The contents of the **Variables** pane are updated to compare attributes that contribute to the outcome values.</span></span> <span data-ttu-id="34b9a-126">因此，左列显示与最佳服务等级关联的属性，右列显示与最差服务等级关联的属性。</span><span class="sxs-lookup"><span data-stu-id="34b9a-126">Therefore, the left column shows you the attributes that are associated with the best grade of service, and the right column shows you the attributes associated with the worst grade of service.</span></span>  
  
### <a name="using-the-variables-pane"></a><span data-ttu-id="34b9a-127">使用“变量”窗格</span><span class="sxs-lookup"><span data-stu-id="34b9a-127">Using the Variables Pane</span></span>  
 <span data-ttu-id="34b9a-128">在此模型中，它显示 `Average Time Per Issue` 为一个重要的因素。</span><span class="sxs-lookup"><span data-stu-id="34b9a-128">In this model, it appears that `Average Time Per Issue` is an important factor.</span></span> <span data-ttu-id="34b9a-129">此变量指示在不考虑呼叫类型的情况下应答一个呼叫所花费的平均时间。</span><span class="sxs-lookup"><span data-stu-id="34b9a-129">This variable indicates the average time that it takes for a call to be answered, regardless of call type.</span></span>  
  
##### <a name="to-view-and-copy-probability-and-lift-scores-for-an-attribute"></a><span data-ttu-id="34b9a-130">查看和复制属性的概率和提升分数</span><span class="sxs-lookup"><span data-stu-id="34b9a-130">To view and copy probability and lift scores for an attribute</span></span>  
  
1.  <span data-ttu-id="34b9a-131">在 "**变量**" 窗格中，将鼠标悬停在第一行中的彩色条上。</span><span class="sxs-lookup"><span data-stu-id="34b9a-131">In the **Variables** pane, pause the mouse over the colored bar in the first row.</span></span>  
  
     <span data-ttu-id="34b9a-132">此彩色条显示了 `Average Time Per Issue` 对服务级别的贡献程度。</span><span class="sxs-lookup"><span data-stu-id="34b9a-132">This colored bar shows you how strongly `Average Time Per Issue` contributes toward the service grade.</span></span> <span data-ttu-id="34b9a-133">工具提示显示每个变量和目标结果的组合的总分数、概率和提升分数。</span><span class="sxs-lookup"><span data-stu-id="34b9a-133">The tooltip shows an overall score, probabilities, and lift scores for each combination of a variable and a target outcome.</span></span>  
  
2.  <span data-ttu-id="34b9a-134">在 "**变量**" 窗格中，右键单击任何彩色条，然后选择 "**复制**"。</span><span class="sxs-lookup"><span data-stu-id="34b9a-134">In the **Variables** pane, right-click any colored bar and select **Copy**.</span></span>  
  
3.  <span data-ttu-id="34b9a-135">在 Excel 工作表中，右键单击任意单元格并选择 "**粘贴**"。</span><span class="sxs-lookup"><span data-stu-id="34b9a-135">In an Excel worksheet, right-click any cell and select **Paste**.</span></span>  
  
     <span data-ttu-id="34b9a-136">报表以 HTML 表格式粘贴，仅显示每个条的分数。</span><span class="sxs-lookup"><span data-stu-id="34b9a-136">The report is pasted as an HTML table, and shows only the scores for each bar.</span></span>  
  
4.  <span data-ttu-id="34b9a-137">在其他 Excel 工作表中，右键单击任意单元格并选择 "**选择性粘贴**"。</span><span class="sxs-lookup"><span data-stu-id="34b9a-137">In a different Excel worksheet, right-click any cell and select **Paste Special**.</span></span>  
  
     <span data-ttu-id="34b9a-138">报表以文本格式粘贴，并包括相关统计信息（如下节所述）。</span><span class="sxs-lookup"><span data-stu-id="34b9a-138">The report is pasted as text format, and includes the related statistics described in the next section.</span></span>  
  
### <a name="using-the-input-pane"></a><span data-ttu-id="34b9a-139">使用“输入”窗格</span><span class="sxs-lookup"><span data-stu-id="34b9a-139">Using the Input Pane</span></span>  
 <span data-ttu-id="34b9a-140">假设您希望看到特定因素所产生的影响，例如班次或操作员数。</span><span class="sxs-lookup"><span data-stu-id="34b9a-140">Suppose that you are interested in looking at the effect of a particular factor, such as the shift, or number of operators.</span></span> <span data-ttu-id="34b9a-141">您可以使用 "**输入**" 窗格选择特定变量，并且 "**变量**" 窗格会自动更新，以比较指定了指定变量的两个以前选择的组。</span><span class="sxs-lookup"><span data-stu-id="34b9a-141">You can select a particular variable by using the **Input** pane, and the **Variables** pane is automatically updated to compare the two previously selected groups given the specified variable.</span></span>  
  
##### <a name="to-review-the-effect-on-service-grade-by-changing-input-attributes"></a><span data-ttu-id="34b9a-142">通过更改输入属性查看对服务等级产生的影响</span><span class="sxs-lookup"><span data-stu-id="34b9a-142">To review the effect on service grade by changing input attributes</span></span>  
  
1.  <span data-ttu-id="34b9a-143">在 "**输入**" 窗格中，为 "**属性**" 选择 Shift。</span><span class="sxs-lookup"><span data-stu-id="34b9a-143">In the **Input** pane, for **attribute**, select Shift.</span></span>  
  
2.  <span data-ttu-id="34b9a-144">对于 "**值**"，选择 " **AM**"。</span><span class="sxs-lookup"><span data-stu-id="34b9a-144">For **Value**, select **AM**.</span></span>  
  
     <span data-ttu-id="34b9a-145">"**变量**" 窗格将更新以显示班次为**AM**时对模型的影响。</span><span class="sxs-lookup"><span data-stu-id="34b9a-145">The **Variables** pane updates to show the impact on the model when the shift is **AM**.</span></span> <span data-ttu-id="34b9a-146">所有其他选择保持不变-仍在比较最低和最高服务等级。</span><span class="sxs-lookup"><span data-stu-id="34b9a-146">All other selections remain the same - you are still comparing the lowest and highest service grades.</span></span>  
  
3.  <span data-ttu-id="34b9a-147">对于 "**值**"，请选择**PM1**。</span><span class="sxs-lookup"><span data-stu-id="34b9a-147">For **Value**, select **PM1**.</span></span>  
  
     <span data-ttu-id="34b9a-148">"**变量**" 窗格将更新以显示班次更改时对模型的影响。</span><span class="sxs-lookup"><span data-stu-id="34b9a-148">The **Variables** pane updates to show the impact on the model when the shift changes.</span></span>  
  
4.  <span data-ttu-id="34b9a-149">在 "**输入**" 窗格中，单击 "**属性**" 下的下一个空白行，然后选择 "调用"。</span><span class="sxs-lookup"><span data-stu-id="34b9a-149">In the **Input** pane, click the next blank row under **Attribute**, and select Calls.</span></span> <span data-ttu-id="34b9a-150">对于 "**值**"，请选择指示最大调用数的范围。</span><span class="sxs-lookup"><span data-stu-id="34b9a-150">For **Value**, select the range that indicates the greatest number of calls.</span></span>  
  
     <span data-ttu-id="34b9a-151">一个新的输入条件会添加到列表中。</span><span class="sxs-lookup"><span data-stu-id="34b9a-151">A new input condition is added to the list.</span></span> <span data-ttu-id="34b9a-152">"**变量**" 窗格会进行更新，以显示调用量最大时，特定班次对模型的影响。</span><span class="sxs-lookup"><span data-stu-id="34b9a-152">The **Variables** pane updates to show the impact on the model for a particular shift when the call volume is highest.</span></span>  
  
5.  <span data-ttu-id="34b9a-153">继续更改 Shift 和 Calls 的值可以发现班次、呼叫数量和服务等级之间所有值得注意的相关性。</span><span class="sxs-lookup"><span data-stu-id="34b9a-153">Continue to change the values for Shift and Calls to find any interesting correlations between shift, call volume, and service grade.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="34b9a-154">若要清除**输入**窗格以便使用不同的属性，请单击 "**刷新查看器内容**"。</span><span class="sxs-lookup"><span data-stu-id="34b9a-154">To clear the **Input** pane so that you can use different attributes, click **Refresh viewer content**.</span></span>  
  
### <a name="interpreting-the-statistics-provided-in-the-viewer"></a><span data-ttu-id="34b9a-155">解释查看器中提供的统计信息</span><span class="sxs-lookup"><span data-stu-id="34b9a-155">Interpreting the Statistics Provided in the Viewer</span></span>  
 <span data-ttu-id="34b9a-156">较长的等待时间是高挂断率的强预测因子，这意味着较差的服务等级。</span><span class="sxs-lookup"><span data-stu-id="34b9a-156">Longer waiting times are a strong predictor of a high abandon rate, meaning a poor service grade.</span></span> <span data-ttu-id="34b9a-157">这似乎是一个明显的结论；但挖掘模型为您提供了一些其他统计数据，以帮助您解释这些趋势。</span><span class="sxs-lookup"><span data-stu-id="34b9a-157">This may seem an obvious conclusion; however, the mining model provides you with some additional statistical data to help you interpret these trends.</span></span>  
  
-   <span data-ttu-id="34b9a-158">**评分**：值，该值指示此变量在结果之间的对比的整体重要性。</span><span class="sxs-lookup"><span data-stu-id="34b9a-158">**Score**: Value that indicates the overall importance of this variable for discriminating between outcomes.</span></span> <span data-ttu-id="34b9a-159">分数越高，变量对结果产生的影响就越大。</span><span class="sxs-lookup"><span data-stu-id="34b9a-159">The higher the score, the stronger the effect the variable has on the outcome.</span></span>  
  
-   <span data-ttu-id="34b9a-160">**值1的概率**：表示此结果的此值概率的百分比。</span><span class="sxs-lookup"><span data-stu-id="34b9a-160">**Probability of value 1**: Percentage that represents the probability of this value for this outcome.</span></span>  
  
-   <span data-ttu-id="34b9a-161">**值2的概率**：表示此结果的此值概率的百分比。</span><span class="sxs-lookup"><span data-stu-id="34b9a-161">**Probability of value 2**: Percentage that represents the probability of this value for this outcome.</span></span>  
  
-   <span data-ttu-id="34b9a-162">**提升值 1**并**提升值 2**：表示使用此特定变量预测值1和值2结果的影响的分数。</span><span class="sxs-lookup"><span data-stu-id="34b9a-162">**Lift for Value 1** and **Lift for Value 2**: Scores that represents the impact of using this particular variable for predicting the Value 1 and Value 2 outcomes.</span></span> <span data-ttu-id="34b9a-163">分数越高，使用该变量预测结果时就越准确。</span><span class="sxs-lookup"><span data-stu-id="34b9a-163">The higher the score, the better the variable is at predicting the outcomes.</span></span>  
  
 <span data-ttu-id="34b9a-164">下表包含首要影响因素的一些示例值。</span><span class="sxs-lookup"><span data-stu-id="34b9a-164">The following table contains some example values for the top influencers.</span></span> <span data-ttu-id="34b9a-165">例如，**值1的概率**为60.6%，值为**2 的概率**是8.30%，这意味着，每个问题的平均时间都在44-70 分钟的范围内，而最高服务等级为的倒班中的 60.6% (值 1) ，8.30 而 (值 2) ，% 的事例处于倒班中。</span><span class="sxs-lookup"><span data-stu-id="34b9a-165">For example, the **Probability of value 1** is 60.6% and **Probability of value 2** is 8.30%, meaning that when the Average Time Per Issue was in the range of 44-70 minutes, 60.6% of cases were in the shift with the highest service grades (Value 1), and 8.30% of cases were in the shift with the worse service grades (Value 2).</span></span>  
  
 <span data-ttu-id="34b9a-166">通过此信息，可以得出一些结论。</span><span class="sxs-lookup"><span data-stu-id="34b9a-166">From this information, you can draw some conclusions.</span></span> <span data-ttu-id="34b9a-167">较短的呼叫响应时间（范围为 44-70）会严重影响较好的服务等级（范围为 0.00-0.07）。</span><span class="sxs-lookup"><span data-stu-id="34b9a-167">Shorter call response time (the range of 44-70) strongly influences better service grade (the range 0.00-0.07).</span></span> <span data-ttu-id="34b9a-168">分数 (92.35) 告诉您此变量非常重要。</span><span class="sxs-lookup"><span data-stu-id="34b9a-168">The score (92.35) tells you that this variable is very important.</span></span>  
  
 <span data-ttu-id="34b9a-169">但是，当您向下查看相关因素的列表时，会发现一些其他因素产生的影响更微妙、更难于解释。</span><span class="sxs-lookup"><span data-stu-id="34b9a-169">However, as you look down the list of contributing factors, you see some other factors with effects that are more subtle and more difficult to interpret.</span></span> <span data-ttu-id="34b9a-170">例如，班次似乎影响服务，但提升分数和相关概率指示班次不是主要因素。</span><span class="sxs-lookup"><span data-stu-id="34b9a-170">For example, shift appears to influence service, but the lift scores and the relative probabilities indicate that shift is not a major factor.</span></span>  
  
|<span data-ttu-id="34b9a-171">Attribute</span><span class="sxs-lookup"><span data-stu-id="34b9a-171">Attribute</span></span>|<span data-ttu-id="34b9a-172">值</span><span class="sxs-lookup"><span data-stu-id="34b9a-172">Value</span></span>|<span data-ttu-id="34b9a-173">优先 \< 0.07</span><span class="sxs-lookup"><span data-stu-id="34b9a-173">Favors \< 0.07</span></span>|<span data-ttu-id="34b9a-174">优先 >= 0.12</span><span class="sxs-lookup"><span data-stu-id="34b9a-174">Favors >= 0.12</span></span>|  
|---------------|-----------|--------------------|----------------------|  
|<span data-ttu-id="34b9a-175">Average Time Per Issue</span><span class="sxs-lookup"><span data-stu-id="34b9a-175">Average Time Per Issue</span></span>|<span data-ttu-id="34b9a-176">89.087-120.000</span><span class="sxs-lookup"><span data-stu-id="34b9a-176">89.087 - 120.000</span></span>||<span data-ttu-id="34b9a-177">分数：100</span><span class="sxs-lookup"><span data-stu-id="34b9a-177">Score:  100</span></span><br /><br /> <span data-ttu-id="34b9a-178">Value1 的概率：4.45%</span><span class="sxs-lookup"><span data-stu-id="34b9a-178">Probability of Value1: 4.45 %</span></span><br /><br /> <span data-ttu-id="34b9a-179">Value2 的概率：51.94%</span><span class="sxs-lookup"><span data-stu-id="34b9a-179">Probability of Value2: 51.94 %</span></span><br /><br /> <span data-ttu-id="34b9a-180">用于 Value1：0.19 的提升</span><span class="sxs-lookup"><span data-stu-id="34b9a-180">Lift for Value1: 0.19</span></span><br /><br /> <span data-ttu-id="34b9a-181">Value2 的提升：1.94</span><span class="sxs-lookup"><span data-stu-id="34b9a-181">Lift for Value2: 1.94</span></span>|  
|<span data-ttu-id="34b9a-182">Average Time Per Issue</span><span class="sxs-lookup"><span data-stu-id="34b9a-182">Average Time Per Issue</span></span>|<span data-ttu-id="34b9a-183">44.000-70.597</span><span class="sxs-lookup"><span data-stu-id="34b9a-183">44.000 - 70.597</span></span>|<span data-ttu-id="34b9a-184">分数：92.35</span><span class="sxs-lookup"><span data-stu-id="34b9a-184">Score: 92.35</span></span><br /><br /> <span data-ttu-id="34b9a-185">Value1 的概率：60.06%</span><span class="sxs-lookup"><span data-stu-id="34b9a-185">Probability of Value1: 60.06 %</span></span><br /><br /> <span data-ttu-id="34b9a-186">Value2 的概率：8.30%</span><span class="sxs-lookup"><span data-stu-id="34b9a-186">Probability of Value2: 8.30 %</span></span><br /><br /> <span data-ttu-id="34b9a-187">Value1 的提升：2.61</span><span class="sxs-lookup"><span data-stu-id="34b9a-187">Lift for Value1: 2.61</span></span><br /><br /> <span data-ttu-id="34b9a-188">Value2 的提升：0.31</span><span class="sxs-lookup"><span data-stu-id="34b9a-188">Lift for Value2: 0.31</span></span>||  
  
 [<span data-ttu-id="34b9a-189">返回页首</span><span class="sxs-lookup"><span data-stu-id="34b9a-189">Back to Top</span></span>](#bkmk_NNviewer)  
  
##  <a name="microsoft-generic-content-tree-viewer"></a><a name="bkmk_genviewer"></a><span data-ttu-id="34b9a-190">Microsoft 一般内容树查看器</span><span class="sxs-lookup"><span data-stu-id="34b9a-190">Microsoft Generic Content Tree Viewer</span></span>  
 <span data-ttu-id="34b9a-191">通过使用该查看器，您可以查看在处理模型时算法创建的更多详细信息。</span><span class="sxs-lookup"><span data-stu-id="34b9a-191">This viewer can be used to view even more detailed information created by the algorithm when the model is processed.</span></span> <span data-ttu-id="34b9a-192">**MicrosoftGeneric 内容树查看器**将挖掘模型表示为一系列节点，其中每个节点表示有关定型数据的已知知识。</span><span class="sxs-lookup"><span data-stu-id="34b9a-192">The **MicrosoftGeneric Content Tree Viewer** represents the mining model as a series of nodes, wherein each node represents learned knowledge about the training data.</span></span> <span data-ttu-id="34b9a-193">该查看器可用于所有模型，但节点内容根据模型类型而不同。</span><span class="sxs-lookup"><span data-stu-id="34b9a-193">This viewer can be used with all models, but the contents of the nodes are different depending in the model type.</span></span>  
  
 <span data-ttu-id="34b9a-194">对于神经网络模型或逻辑回归模型，您会发现 `marginal statistics node` 特别有用。</span><span class="sxs-lookup"><span data-stu-id="34b9a-194">For neural network models or logistic regression models, you might find the `marginal statistics node` particularly useful.</span></span> <span data-ttu-id="34b9a-195">该节点包含有关数据中值分布的派生统计信息。</span><span class="sxs-lookup"><span data-stu-id="34b9a-195">This node contains derived statistics about the distribution of values in your data.</span></span> <span data-ttu-id="34b9a-196">如果希望获取数据摘要而无需编写许多 T-SQL 查询，该信息会很有用。</span><span class="sxs-lookup"><span data-stu-id="34b9a-196">This information can be useful if you want to get a summary of the data without having to write many T-SQL queries.</span></span> <span data-ttu-id="34b9a-197">前一主题中装箱值的图表派生自边际统计信息节点。</span><span class="sxs-lookup"><span data-stu-id="34b9a-197">The chart of binning values in the previous topic was derived from the marginal statistics node.</span></span>  
  
#### <a name="to-obtain-a-summary-of-data-values-from-the-mining-model"></a><span data-ttu-id="34b9a-198">从挖掘模型中获取数据摘要</span><span class="sxs-lookup"><span data-stu-id="34b9a-198">To obtain a summary of data values from the mining model</span></span>  
  
1.  <span data-ttu-id="34b9a-199">在数据挖掘设计器的 "**挖掘模型查看**器" 选项卡中，选择 \<mining model name> 。</span><span class="sxs-lookup"><span data-stu-id="34b9a-199">In Data Mining Designer, in the **Mining Model Viewer** tab, select \<mining model name>.</span></span>  
  
2.  <span data-ttu-id="34b9a-200">从 "**查看器**" 列表中，选择 " **Microsoft 一般内容树查看器**"。</span><span class="sxs-lookup"><span data-stu-id="34b9a-200">From the **Viewer** list, select **Microsoft Generic Content Tree Viewer**.</span></span>  
  
     <span data-ttu-id="34b9a-201">刷新挖掘模型的视图会在左侧窗格中显示节点层次结构，并在右侧窗格中显示 HTML 表。</span><span class="sxs-lookup"><span data-stu-id="34b9a-201">The view of the mining model refreshes to show a node hierarchy in the left-hand pane and an HTML table in the right-hand pane.</span></span>  
  
3.  <span data-ttu-id="34b9a-202">在 "**节点标题**" 窗格中，单击名称为10000000000000000的节点。</span><span class="sxs-lookup"><span data-stu-id="34b9a-202">In the **Node Caption** pane, click the node that has the name 10000000000000000.</span></span>  
  
     <span data-ttu-id="34b9a-203">任何模型中的最顶部节点都始终是模型根节点。</span><span class="sxs-lookup"><span data-stu-id="34b9a-203">The topmost node in any model is always the model root node.</span></span> <span data-ttu-id="34b9a-204">在神经网络模型或逻辑回归模型中，紧位于该节点下方的节点是边际统计信息节点。</span><span class="sxs-lookup"><span data-stu-id="34b9a-204">In a neural network or logistic regression model, the node immediately under that is the marginal statistics node.</span></span>  
  
4.  <span data-ttu-id="34b9a-205">在 "**节点详细信息**" 窗格中，向下滚动，直到找到行 NODE_DISTRIBUTION。</span><span class="sxs-lookup"><span data-stu-id="34b9a-205">In the **Node Details** pane, scroll down until you find the row, NODE_DISTRIBUTION.</span></span>  
  
5.  <span data-ttu-id="34b9a-206">向下滚动 NODE_DISTRIBUTION 表可以查看按照神经网络算法计算的值的分布。</span><span class="sxs-lookup"><span data-stu-id="34b9a-206">Scroll down through the NODE_DISTRIBUTION table to view the distribution of values as calculated by the neural network algorithm.</span></span>  
  
 <span data-ttu-id="34b9a-207">若要在报表中使用该数据，可以选择并复制特定行的信息，也可以使用下列数据挖掘扩展插件 (DMX) 查询来提取节点的完整内容。</span><span class="sxs-lookup"><span data-stu-id="34b9a-207">To use this data in a report, you could select and then copy the information for specific rows, or you can use the following Data Mining Extensions (DMX) query to extract the complete contents of the node.</span></span>  
  
```  
SELECT *   
FROM [Call Center EQ4].CONTENT  
WHERE NODE_NAME = '10000000000000000'  
```  
  
 <span data-ttu-id="34b9a-208">还可以使用节点层次结构和 NODE_DISTRIBUTION 表中的详细信息来遍历神经网络中的各个路径，并查看来自隐藏层的统计信息。</span><span class="sxs-lookup"><span data-stu-id="34b9a-208">You can also use the node hierarchy and the details in the NODE_DISTRIBUTION table to traverse individual paths in the neural network and view statistics from the hidden layer.</span></span> <span data-ttu-id="34b9a-209">有关详细信息，请参阅[神经网络模型查询示例](../../2014/analysis-services/data-mining/neural-network-model-query-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="34b9a-209">For more information, see [Neural Network Model Query Examples](../../2014/analysis-services/data-mining/neural-network-model-query-examples.md).</span></span>  
  
 [<span data-ttu-id="34b9a-210">返回页首</span><span class="sxs-lookup"><span data-stu-id="34b9a-210">Back to Top</span></span>](#bkmk_NNviewer)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="34b9a-211">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="34b9a-211">Next Task in Lesson</span></span>  
 [<span data-ttu-id="34b9a-212">向呼叫中心结构中添加逻辑回归模型 &#40;中级数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="34b9a-212">Adding a Logistic Regression Model to the Call Center Structure &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/add-logistic-regression-model-to-call-center-intermediate-data-mining.md)  
  
## <a name="see-also"></a><span data-ttu-id="34b9a-213">另请参阅</span><span class="sxs-lookup"><span data-stu-id="34b9a-213">See Also</span></span>  
 <span data-ttu-id="34b9a-214">[&#40;Analysis Services 数据挖掘的神经网络模型的挖掘模型内容&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-neural-network-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="34b9a-214">[Mining Model Content for Neural Network Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-neural-network-models-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="34b9a-215">[神经网络模型查询示例](../../2014/analysis-services/data-mining/neural-network-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="34b9a-215">[Neural Network Model Query Examples](../../2014/analysis-services/data-mining/neural-network-model-query-examples.md) </span></span>  
 <span data-ttu-id="34b9a-216">[Microsoft 神经网络算法技术参考](../../2014/analysis-services/data-mining/microsoft-neural-network-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="34b9a-216">[Microsoft Neural Network Algorithm Technical Reference](../../2014/analysis-services/data-mining/microsoft-neural-network-algorithm-technical-reference.md) </span></span>  
 [<span data-ttu-id="34b9a-217">更改挖掘模型中列的离散化</span><span class="sxs-lookup"><span data-stu-id="34b9a-217">Change the Discretization of a Column in a Mining Model</span></span>](../../2014/analysis-services/data-mining/change-the-discretization-of-a-column-in-a-mining-model.md)  
  
  
