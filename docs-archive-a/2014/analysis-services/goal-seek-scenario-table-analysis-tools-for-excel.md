---
title: 用于 Excel)  (表分析工具的目标查找方案 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- scenario analysis
- goal seek scenario
ms.assetid: efe50306-cf7c-46b3-9cc4-e7f0b6968b0c
author: minewiskan
ms.author: owend
ms.openlocfilehash: b3b4df4f78a2d3652b1dac3c566e66507b523ea5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580454"
---
# <a name="goal-seek-scenario-table-analysis-tools-for-excel"></a><span data-ttu-id="cbf49-102">目标查找应用场景（Excel 表分析工具）</span><span class="sxs-lookup"><span data-stu-id="cbf49-102">Goal Seek Scenario (Table Analysis Tools for Excel)</span></span>
  <span data-ttu-id="cbf49-103">![表分析工具中的“目标查找”按钮](media/tat-goalseek.gif "表分析工具中的“目标查找”按钮")</span><span class="sxs-lookup"><span data-stu-id="cbf49-103">![Goal Seek button in Table Analysis tools](media/tat-goalseek.gif "Goal Seek button in Table Analysis tools")</span></span>  
  
 <span data-ttu-id="cbf49-104">**目标查找**应用场景工具是[What If](what-if-scenario-table-analysis-tools-for-excel.md)方案工具的补充。</span><span class="sxs-lookup"><span data-stu-id="cbf49-104">The **Goal Seek** scenario tool is complementary to the [What If](what-if-scenario-table-analysis-tools-for-excel.md) scenario tool.</span></span> <span data-ttu-id="cbf49-105">**假设**工具会告诉您做出更改的影响，而**目标查找**工具会告诉您必须更改的基本因素才能获得所需的结果。</span><span class="sxs-lookup"><span data-stu-id="cbf49-105">The **What-If** tool tells you the impact of making a change, whereas the **Goal Seek** tool tells you the underlying factors that must change to achieve a desired result.</span></span>  
  
 <span data-ttu-id="cbf49-106">例如，假设您的目标是提高客户满意度。</span><span class="sxs-lookup"><span data-stu-id="cbf49-106">For example, let's say your goal is to increase customer satisfaction.</span></span> <span data-ttu-id="cbf49-107">您可以使用**目标查找**分析来确定哪些因素最有可能提高客户满意度，并决定这些变化是否经济高效。</span><span class="sxs-lookup"><span data-stu-id="cbf49-107">You can use **Goal Seek** analysis to determine which factors would be most likely to increase customer satisfaction, and decide whether those changes are cost-effective.</span></span>  
  
 <span data-ttu-id="cbf49-108">该工具完成分析后，它会在源数据表中创建两个新列。</span><span class="sxs-lookup"><span data-stu-id="cbf49-108">When the tool finishes its analysis, it creates two new columns in the source data table.</span></span> <span data-ttu-id="cbf49-109">这些列显示了实现目标结果的*可能性*，以及建议的更改（如果有）。</span><span class="sxs-lookup"><span data-stu-id="cbf49-109">These columns show the *likelihood* that the targeted outcome can be achieved, and the recommended change, if any.</span></span>  
  
 <span data-ttu-id="cbf49-110">该工具可分析一组数据并对整个数据集进行预测，或者可以创建分析，再每次测试一个应用场景。</span><span class="sxs-lookup"><span data-stu-id="cbf49-110">The tool can analyze a set of data and make predictions for the entire set, or you can create the analysis and then test scenarios one at a time.</span></span>  
  
## <a name="using-the-goal-seek-scenario-tool"></a><span data-ttu-id="cbf49-111">使用目标查找应用场景工具</span><span class="sxs-lookup"><span data-stu-id="cbf49-111">Using the Goal Seek Scenario Tool</span></span>  
  
1.  <span data-ttu-id="cbf49-112">打开 Excel 表。</span><span class="sxs-lookup"><span data-stu-id="cbf49-112">Open an Excel table.</span></span>  
  
2.  <span data-ttu-id="cbf49-113">单击 "**方案**"，然后选择 "**目标查找**"。</span><span class="sxs-lookup"><span data-stu-id="cbf49-113">Click **Scenarios**, and select **Goal Seek**.</span></span>  
  
3.  <span data-ttu-id="cbf49-114">在 "**方案分析：目标查找**" 对话框中，从列表中选择包含目标值的列。</span><span class="sxs-lookup"><span data-stu-id="cbf49-114">In the **Scenario Analysis: Goal Seek** dialog box, select the column that contains the target value from the list.</span></span>  
  
4.  <span data-ttu-id="cbf49-115">指定要达到的值。</span><span class="sxs-lookup"><span data-stu-id="cbf49-115">Specify the value that you want to achieve.</span></span>  
  
     <span data-ttu-id="cbf49-116">如果列目标包含连续数值，则还可以指定希望采用的值的增减幅度。</span><span class="sxs-lookup"><span data-stu-id="cbf49-116">If the column goal contains continuous numeric values, you can also specify a desired increase or decrease in the value.</span></span> <span data-ttu-id="cbf49-117">例如，你可以选择 "**销售**" 作为列，并指定目标为增加120%。</span><span class="sxs-lookup"><span data-stu-id="cbf49-117">For example, you might choose **Sales** as the column and specify that the target is an increase of 120%.</span></span>  
  
     <span data-ttu-id="cbf49-118">或者，可以通过键入上限和下限将目标指定为某一范围的值。</span><span class="sxs-lookup"><span data-stu-id="cbf49-118">Or, you can specify the goal as a range of values, by typing a lower and upper limit.</span></span>  
  
5.  <span data-ttu-id="cbf49-119">指定包含将要更改的值的列。</span><span class="sxs-lookup"><span data-stu-id="cbf49-119">Specify the column that contains the values you will change.</span></span> <span data-ttu-id="cbf49-120">也就是说，选取将对其进行操作以产生所需结果的列。</span><span class="sxs-lookup"><span data-stu-id="cbf49-120">In other words, pick the column that will be manipulated to produce the desired result.</span></span>  
  
6.  <span data-ttu-id="cbf49-121">（可选）单击 "**选择要用于分析的列**"，然后选择包含有用信息的列。</span><span class="sxs-lookup"><span data-stu-id="cbf49-121">Optionally, click **Choose columns to be used for analysis**, and select columns that contain useful information.</span></span> <span data-ttu-id="cbf49-122">取消选择对分析无用的列。</span><span class="sxs-lookup"><span data-stu-id="cbf49-122">Deselect columns that will not contribute to the analysis.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cbf49-123">不要取消选择将用于目标或更改的列。</span><span class="sxs-lookup"><span data-stu-id="cbf49-123">Do not deselect columns that you will use for either the goal or the change.</span></span> <span data-ttu-id="cbf49-124">这些列是必需的。</span><span class="sxs-lookup"><span data-stu-id="cbf49-124">These columns are required.</span></span>  
  
7.  <span data-ttu-id="cbf49-125">指定是要针对整个表进行预测，还是仅针对所选行进行预测。</span><span class="sxs-lookup"><span data-stu-id="cbf49-125">Specify whether you want to make predictions for the entire table, or for only the selected row.</span></span>  
  
8.  <span data-ttu-id="cbf49-126">如果选择了 "**整个表**" 选项，则该工具会将预测添加到源表中的两个新列中。</span><span class="sxs-lookup"><span data-stu-id="cbf49-126">If you selected the **Entire table** option, the tool adds the predictions to the source table in two new columns.</span></span>  
  
9. <span data-ttu-id="cbf49-127">如果在**此行**中选择了选项，则会将分析结果输出到对话框以供查看。</span><span class="sxs-lookup"><span data-stu-id="cbf49-127">If you selected the option **On this row**, the results of analysis are output to the dialog box for review.</span></span> <span data-ttu-id="cbf49-128">该对话框保持打开状态，以便您可以继续尝试不同的值和目标。</span><span class="sxs-lookup"><span data-stu-id="cbf49-128">The dialog box stays open so that you can continue trying out different values and goals.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="cbf49-129">要求</span><span class="sxs-lookup"><span data-stu-id="cbf49-129">Requirements</span></span>  
 <span data-ttu-id="cbf49-130">此工具使用 Microsoft 逻辑回归算法，该算法可处理数值或离散值。</span><span class="sxs-lookup"><span data-stu-id="cbf49-130">This tool uses the Microsoft Logistic Regression algorithm, which can process either numeric or discrete values.</span></span>  
  
 <span data-ttu-id="cbf49-131">您可多次运行预测，并选择不同的列，但是每个目标和更改的组合都必须单独计算。</span><span class="sxs-lookup"><span data-stu-id="cbf49-131">You can run the prediction multiple times, and select different columns later, but each combination of a goal and a change must be calculated separately.</span></span>  
  
 <span data-ttu-id="cbf49-132">如果选择了包含有用信息的分析列，则可获得更好的结果。</span><span class="sxs-lookup"><span data-stu-id="cbf49-132">You can achieve better results if you select columns for analysis that contain useful information.</span></span> <span data-ttu-id="cbf49-133">但是，如果您选择的列太少，则可能很难获得结果。</span><span class="sxs-lookup"><span data-stu-id="cbf49-133">However, if you include too few columns, it might be difficult to obtain a result.</span></span>  
  
 <span data-ttu-id="cbf49-134">一次创建一个预测时，请确保不要选择已包含所需结果的行，否则可能出现错误。</span><span class="sxs-lookup"><span data-stu-id="cbf49-134">When you create predictions one at a time, be sure to select a row that does not already contain the desired result, or you may get an error.</span></span> <span data-ttu-id="cbf49-135">也就是说，当目标查找的目的为确定鼓励购买自行车的因素时，您应该仅包含没有购买自行车的客户。</span><span class="sxs-lookup"><span data-stu-id="cbf49-135">In other words, if the purpose of goal seeking is to determine factors that encourage bike purchases, you should only include customers who did not purchase a bike.</span></span>  
  
## <a name="understanding-the-results-of-goal-seek-analysis"></a><span data-ttu-id="cbf49-136">理解目标查找分析的结果</span><span class="sxs-lookup"><span data-stu-id="cbf49-136">Understanding the Results of Goal Seek Analysis</span></span>  
 <span data-ttu-id="cbf49-137">在创建目标查找应用场景时，该工具执行以下三个操作：</span><span class="sxs-lookup"><span data-stu-id="cbf49-137">When you create a goal seeking scenario, the tool does three things:</span></span>  
  
-   <span data-ttu-id="cbf49-138">创建存储有关表中数据关键事实的数据挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="cbf49-138">Creates a data mining structure that stores key facts about the data in your table.</span></span>  
  
-   <span data-ttu-id="cbf49-139">基于数据创建逻辑回归挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="cbf49-139">Creates a logistic regression mining model based on the data.</span></span>  
  
-   <span data-ttu-id="cbf49-140">创建所指定的每个值的预测。</span><span class="sxs-lookup"><span data-stu-id="cbf49-140">Creates a prediction for each value that you specify.</span></span>  
  
 <span data-ttu-id="cbf49-141">如果一次测试一个目标查找应用场景，则可以交互方式查看结果。</span><span class="sxs-lookup"><span data-stu-id="cbf49-141">If you test goal-seeking scenarios one at a time, you can view the results interactively.</span></span> <span data-ttu-id="cbf49-142">这与创建*单独预测查询*相同。</span><span class="sxs-lookup"><span data-stu-id="cbf49-142">This is the same as creating a *singleton prediction query*.</span></span>  
  
 <span data-ttu-id="cbf49-143">工具将在对话框的**结果**窗格中进行报告，无论是否成功找到实现所需目标的方案。</span><span class="sxs-lookup"><span data-stu-id="cbf49-143">The tool reports in the **Results** pane of the dialog box whether it was successful in finding a scenario that achieves the desired goal.</span></span> <span data-ttu-id="cbf49-144">如果找到了成功的解决方案，则该工具还会生成告知所需更改的建议。</span><span class="sxs-lookup"><span data-stu-id="cbf49-144">If a successful solution was found, the tool also generates a recommendation that tells you the required change.</span></span> <span data-ttu-id="cbf49-145">例如，**目标查找**工具可能会告诉您上下班途中距离应小于5英里。</span><span class="sxs-lookup"><span data-stu-id="cbf49-145">For example, the **Goal Seek** tool might tell you that the commuting distance should be less than 5 miles.</span></span>  
  
 <span data-ttu-id="cbf49-146">示例结果：</span><span class="sxs-lookup"><span data-stu-id="cbf49-146">Example results:</span></span>  
  
 <span data-ttu-id="cbf49-147">**有兴趣购买的目标查找找到了解决方案。**</span><span class="sxs-lookup"><span data-stu-id="cbf49-147">**Goal Seeking for Interest in Buying has found a solution.**</span></span>  
  
 <span data-ttu-id="cbf49-148">**通过将“Commute distance”更改为“2-5 miles”，获得最近似匹配。**</span><span class="sxs-lookup"><span data-stu-id="cbf49-148">**Closest match obtained by changing 'Commute distance' to '2-5 miles'.**</span></span>  
  
 <span data-ttu-id="cbf49-149">由于此结果基于数据表中的现有行，因此这意味着，对于特定的客户，如果保持所有其他条件不变，而将该客户的上下班路程减少到 2-5 英里，则该客户将在某种程度上更有可能购买自行车。</span><span class="sxs-lookup"><span data-stu-id="cbf49-149">Because this result is based on an existing row in the data table, it means that, for a particular customer, if all else about the customer stayed the same but the customer's commute was reduced to 2-5 miles, the customer would be somewhat more likely buy a bicycle.</span></span>  
  
 <span data-ttu-id="cbf49-150">如果通过指定**整个表**为 Excel 表中的所有行创建目标查找预测，则 thetool 会在原始数据表中创建两个新列。</span><span class="sxs-lookup"><span data-stu-id="cbf49-150">If you create goal-seeking predictions for all the rows in the Excel table by specifying **Entire table**, thetool creates two new columns in the original data table.</span></span> <span data-ttu-id="cbf49-151">添加到表中的第一列包含两种标记之一：一种是外带绿圈的复选标记，说明可实现目标，另一种是外带红圈的 X 标记，说明任何更改都不能实现目标。</span><span class="sxs-lookup"><span data-stu-id="cbf49-151">The first column that is added to the table contains either a check mark in a green circle, to indicate that the goal can be met, or an X mark in a red circle, to indicate that no changes can be made that will enable the goal.</span></span>  
  
 <span data-ttu-id="cbf49-152">第二列包含建议的更改。</span><span class="sxs-lookup"><span data-stu-id="cbf49-152">The second column contains the recommended change.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cbf49-153">建议更改及其成功可能性的置信度级别由算法预先确定，不能更改。</span><span class="sxs-lookup"><span data-stu-id="cbf49-153">The confidence level for the recommendation and its success are predetermined by the algorithm and cannot be changed.</span></span>  
  
## <a name="related-tools"></a><span data-ttu-id="cbf49-154">相关工具</span><span class="sxs-lookup"><span data-stu-id="cbf49-154">Related Tools</span></span>  
 <span data-ttu-id="cbf49-155">Excel 数据挖掘客户端是一个独立的外接程序，它提供更高级的数据挖掘功能，还包含用于创建可预测行为的数据挖掘模型的向导。</span><span class="sxs-lookup"><span data-stu-id="cbf49-155">The Data Mining Client for Excel, which is a separate add-in that provides more advanced data mining functionality, includes wizards for creating data mining models that predict behavior.</span></span> <span data-ttu-id="cbf49-156">有关详细信息，请参阅[创建数据挖掘模型](creating-a-data-mining-model.md)。</span><span class="sxs-lookup"><span data-stu-id="cbf49-156">For more information, see [Creating a Data Mining Model](creating-a-data-mining-model.md).</span></span>  
  
 <span data-ttu-id="cbf49-157">有关 "**目标查找**" 方案工具使用的算法的详细信息，请参阅联机丛书中的主题 "Microsoft 逻辑回归算法" [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="cbf49-157">For more information about the algorithm used by the **Goal Seek** scenario tool, see the topic "Microsoft Logistic Regression Algorithm" in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbf49-158">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cbf49-158">See Also</span></span>  
 [<span data-ttu-id="cbf49-159">Excel 表分析工具</span><span class="sxs-lookup"><span data-stu-id="cbf49-159">Table Analysis Tools for Excel</span></span>](table-analysis-tools-for-excel.md)  
  
  
