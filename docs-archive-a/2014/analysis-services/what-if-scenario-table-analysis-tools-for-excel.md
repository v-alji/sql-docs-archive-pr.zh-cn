---
title: 假设方案 (Excel) 的表分析工具 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- what if scenario
- scenario analysis
ms.assetid: 4df5a5c5-1983-4009-a7c5-cd340649fd2f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4bb5c5e866c1320c297fb4f2760bca58623f6601
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694572"
---
# <a name="what-if-scenario-table-analysis-tools-for-excel"></a><span data-ttu-id="48689-102">“假设”应用场景（Excel 表分析工具）</span><span class="sxs-lookup"><span data-stu-id="48689-102">What-If Scenario (Table Analysis Tools for Excel)</span></span>
  <span data-ttu-id="48689-103">![表分析工具中的“假设”应用场景按钮](media/tat-whatif.gif "表分析工具中的“假设”应用场景按钮")</span><span class="sxs-lookup"><span data-stu-id="48689-103">![What If Scenario button in Table Analysis tools](media/tat-whatif.gif "What If Scenario button in Table Analysis tools")</span></span>

 <span data-ttu-id="48689-104">"**假设**" 应用场景工具分析现有数据中的模式，并使你能够评估一列中的更改对另一列的值的影响。</span><span class="sxs-lookup"><span data-stu-id="48689-104">The **What-If** scenario tool analyzes patterns in existing data, and then enables you to evaluate the effect that changes in one column would have on the value of a different column.</span></span>

 <span data-ttu-id="48689-105">例如，您可以检查某件商品在价格上涨时对其总销售额的影响。</span><span class="sxs-lookup"><span data-stu-id="48689-105">For example, you could explore the effect of raising the price of an item on its total sales.</span></span>

 <span data-ttu-id="48689-106">此工具在可以创建的预测数方面比较灵活。</span><span class="sxs-lookup"><span data-stu-id="48689-106">The tool is flexible about the number of predictions you can create.</span></span> <span data-ttu-id="48689-107">初始分析完成后，可以针对表中的所有数据预测更改，也可以一次输入一个测试值。</span><span class="sxs-lookup"><span data-stu-id="48689-107">After the initial analysis is complete, you can either predict changes for all the data in the table, or enter test values one at a time.</span></span>

## <a name="using-the-what-if-scenario-tool"></a><span data-ttu-id="48689-108">使用 "假设" 应用场景工具</span><span class="sxs-lookup"><span data-stu-id="48689-108">Using the What-If Scenario Tool</span></span>

1.  <span data-ttu-id="48689-109">打开 Excel 数据表。</span><span class="sxs-lookup"><span data-stu-id="48689-109">Open an Excel data table.</span></span>

2.  <span data-ttu-id="48689-110">单击 "**方案**"，然后选择 "**假设**"。</span><span class="sxs-lookup"><span data-stu-id="48689-110">Click **Scenarios**, and then select **What-If**.</span></span>

3.  <span data-ttu-id="48689-111">在 "**方案**" 框中，选择包含要更改的值的列，并将更改指定为特定值，或将更改指定为 (增加或减少) 当前值的更改的百分比。</span><span class="sxs-lookup"><span data-stu-id="48689-111">In the **Scenario** box, select the column that contains the value you will change, and specify the change either as a specific value or as a percentage of change (either increased or decreased) on the current values.</span></span>

4.  <span data-ttu-id="48689-112">在 "**要**执行的操作" 框中，指定要评估其效果的列。</span><span class="sxs-lookup"><span data-stu-id="48689-112">In the **What happens to** box, specify the column for which you want to assess the effect.</span></span>

5.  <span data-ttu-id="48689-113">（可选）单击 "**选择要用于分析的列**"，以选择在进行预测时可能有用的列。</span><span class="sxs-lookup"><span data-stu-id="48689-113">Optionally, click **Choose columns to be used for analysis** to select columns that are likely to be useful in making the prediction.</span></span> <span data-ttu-id="48689-114">也可取消选择对检测模式几乎没有什么用的列，如行 ID 或名称。</span><span class="sxs-lookup"><span data-stu-id="48689-114">You can also deselect columns that are likely to be of little use in detecting patterns, such as row IDs or names.</span></span>

6.  <span data-ttu-id="48689-115">在 "**指定行或表**" 框中，选择是希望仅对当前所选行评估影响，还是要对表中的完整数据集进行评估。</span><span class="sxs-lookup"><span data-stu-id="48689-115">In the **Specify row or table** box, choose whether you want the impact assessed for the currently selected row only, or for the complete set of data in the table.</span></span>

7.  <span data-ttu-id="48689-116">如果选择**此行**，则该工具将在对话框中显示结果。</span><span class="sxs-lookup"><span data-stu-id="48689-116">If you select **On this row**, the tool displays the result in the dialog box.</span></span> <span data-ttu-id="48689-117">在对话框保持打开的情况下，您可以修改选择以测试其他应用场景。</span><span class="sxs-lookup"><span data-stu-id="48689-117">While the dialog box remains open, you can modify your selections to test other scenarios.</span></span>

8.  <span data-ttu-id="48689-118">如果选择 "**整个表**"，则该工具将在对话框中显示一条状态消息，并将两个新列添加到原始数据表中。</span><span class="sxs-lookup"><span data-stu-id="48689-118">If you select **Entire table**, the tool displays a status message in the dialog box, and adds two new columns to the original data table.</span></span> <span data-ttu-id="48689-119">单击 "**关闭**" 以查看工作表中的完整结果。</span><span class="sxs-lookup"><span data-stu-id="48689-119">Click **Close** to view the complete results in the worksheet.</span></span>

### <a name="requirements"></a><span data-ttu-id="48689-120">要求</span><span class="sxs-lookup"><span data-stu-id="48689-120">Requirements</span></span>
 <span data-ttu-id="48689-121">此工具使用 Microsoft 逻辑回归算法，这一算法支持数值或离散值的预测。</span><span class="sxs-lookup"><span data-stu-id="48689-121">This tool uses the Microsoft Logistic Regression algorithm, which supports prediction of either numeric or discrete values.</span></span> <span data-ttu-id="48689-122">但是，为达到最佳结果，建议遵循以下最佳实践：</span><span class="sxs-lookup"><span data-stu-id="48689-122">However, to achieve the best results, we suggest the following best practices:</span></span>

-   <span data-ttu-id="48689-123">选择包含有用信息的列进行分析。</span><span class="sxs-lookup"><span data-stu-id="48689-123">Select columns for analysis that contain useful information.</span></span>

-   <span data-ttu-id="48689-124">如果包含的列太少，则可能很难获得结果。</span><span class="sxs-lookup"><span data-stu-id="48689-124">If you include too few columns it may be difficult to obtain a result.</span></span>

-   <span data-ttu-id="48689-125">如果使用 "**到值**" 选项，则必须在框中键入一个值，或从列表中选择一个值。</span><span class="sxs-lookup"><span data-stu-id="48689-125">If you use the **To value** option, you must type a value in the box or select a value from the list.</span></span>

-   <span data-ttu-id="48689-126">如果使用 "**百分比**" 选项，请将更改设置为增大或减小百分比。</span><span class="sxs-lookup"><span data-stu-id="48689-126">If you use the **Percentage** option, set the change as a percentage increase or decrease.</span></span> <span data-ttu-id="48689-127">默认值为 120%，表示在当前值的基础上增加 20%。</span><span class="sxs-lookup"><span data-stu-id="48689-127">The default is 120%, meaning a 20% increase over the current value.</span></span>

> [!NOTE]
>  <span data-ttu-id="48689-128">如果不设置值，则可能会出现错误。</span><span class="sxs-lookup"><span data-stu-id="48689-128">If you do not set a value, you might receive an error.</span></span>

## <a name="understanding-the-results-of-what-if-analysis"></a><span data-ttu-id="48689-129">了解假设分析的结果</span><span class="sxs-lookup"><span data-stu-id="48689-129">Understanding the Results of What-If Analysis</span></span>
 <span data-ttu-id="48689-130">创建**假设**方案时，该工具执行以下三项操作：</span><span class="sxs-lookup"><span data-stu-id="48689-130">When you create a **What-If** scenario, the tool does three things:</span></span>

-   <span data-ttu-id="48689-131">创建存储有关表中数据关键事实的数据挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="48689-131">Creates a data mining structure that stores key facts about the data in your table.</span></span>

-   <span data-ttu-id="48689-132">基于数据创建逻辑回归挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="48689-132">Creates a logistic regression mining model based on the data.</span></span>

-   <span data-ttu-id="48689-133">创建所指定的每个值的预测查询。</span><span class="sxs-lookup"><span data-stu-id="48689-133">Creates a prediction query for each of the values you specify.</span></span>

 <span data-ttu-id="48689-134">通过指定**整个表**，可以一次输出所有预测。</span><span class="sxs-lookup"><span data-stu-id="48689-134">You can output all the predictions at one time by specifying **Entire table**.</span></span> <span data-ttu-id="48689-135">此工具然后在原始数据表中创建两个新列。</span><span class="sxs-lookup"><span data-stu-id="48689-135">The tool then creates two new columns in the original data table.</span></span>

 <span data-ttu-id="48689-136">添加到表中的列包含两种类型的信息：给定更改幅度后得到的预测值以及预测值的置信度。</span><span class="sxs-lookup"><span data-stu-id="48689-136">The columns that are added to the table contain two types of information: the predicted value given the change, and its confidence.</span></span> <span data-ttu-id="48689-137">置信度表示预测准确的概率。</span><span class="sxs-lookup"><span data-stu-id="48689-137">Confidence means the probability that the prediction is correct.</span></span>

 <span data-ttu-id="48689-138">也可在对话框中逐个输入更改值，然后交互式查看预测。</span><span class="sxs-lookup"><span data-stu-id="48689-138">You can also enter change values one by one in the dialog box, and view the predictions interactively.</span></span> <span data-ttu-id="48689-139">这与创建*单独预测查询*相同。</span><span class="sxs-lookup"><span data-stu-id="48689-139">This is the same as creating a *singleton prediction query*.</span></span> <span data-ttu-id="48689-140">输出的预测查询结果中包括以下信息：预测是成功还是失败、预测值以及置信度。</span><span class="sxs-lookup"><span data-stu-id="48689-140">The results of the prediction query are output with the following information: the success or failure of prediction, the predicted value, and the confidence level.</span></span> <span data-ttu-id="48689-141">置信度显示为包含点线的条形图。</span><span class="sxs-lookup"><span data-stu-id="48689-141">The confidence level is shown as a bar that contains a dotted line.</span></span> <span data-ttu-id="48689-142">点线越长，结果的置信度就越高。</span><span class="sxs-lookup"><span data-stu-id="48689-142">The longer the dotted line, the higher the confidence in the result.</span></span>

 <span data-ttu-id="48689-143">例如，如果您正在尝试确定客户在购买客户的意愿上增加客户的年龄，并将客户的年龄增加到25，则**假设**工具会查询数据挖掘模型并返回以下结果：</span><span class="sxs-lookup"><span data-stu-id="48689-143">For example, if you are trying to determine the effect of increasing the customer's age on the customer's willingness to buy, and increase the customer's age to 25, the **What-If** tool queries the data mining model and returns the following result:</span></span>

 <span data-ttu-id="48689-144">**购买自行车的假设分析找到了解决方案。**</span><span class="sxs-lookup"><span data-stu-id="48689-144">**What-If Analysis for Purchases Bicycle has found a solution.**</span></span>

 <span data-ttu-id="48689-145">**“是否购买自行车”= 是**</span><span class="sxs-lookup"><span data-stu-id="48689-145">**'Purchases Bicycle' = yes**</span></span>

 <span data-ttu-id="48689-146">**置信度: 一般**</span><span class="sxs-lookup"><span data-stu-id="48689-146">**Confidence: Fair**</span></span>

 <span data-ttu-id="48689-147">由于此结果基于数据表中的现有行，因此这意味着，对于特定的客户，保持所有其他条件不变，而将该客户的年龄增加到 25 岁，那么该客户将有可能购买自行车。</span><span class="sxs-lookup"><span data-stu-id="48689-147">Because this result is based on an existing row in the data table, it means that, for a particular customer, if all else about the customer stayed the same but the customer's age was increased to 25, the customer would likely buy a bicycle.</span></span>

 <span data-ttu-id="48689-148">将预测输出到原始数据表中更便于确定预测是否有用。</span><span class="sxs-lookup"><span data-stu-id="48689-148">Outputting the predictions to the original data table might make it easier to determine whether the predictions are useful.</span></span>

## <a name="related-tools"></a><span data-ttu-id="48689-149">相关工具</span><span class="sxs-lookup"><span data-stu-id="48689-149">Related Tools</span></span>
 <span data-ttu-id="48689-150">Excel 数据挖掘客户端是一个独立的外接程序，它提供更高级的数据挖掘功能，还包含用于创建可预测行为的数据挖掘模型的向导。</span><span class="sxs-lookup"><span data-stu-id="48689-150">The Data Mining Client for Excel, which is a separate add-in that provides more advanced data mining functionality, includes wizards for creating data mining models that predict behavior.</span></span> <span data-ttu-id="48689-151">有关详细信息，请参阅[创建数据挖掘模型](creating-a-data-mining-model.md)。</span><span class="sxs-lookup"><span data-stu-id="48689-151">For more information, see [Creating a Data Mining Model](creating-a-data-mining-model.md).</span></span>

 <span data-ttu-id="48689-152">有关 "**假设**" 应用场景工具所用算法的详细信息，请参阅 SQL Server 联机丛书中的主题 "Microsoft 逻辑回归算法"。</span><span class="sxs-lookup"><span data-stu-id="48689-152">For more information about the algorithm used by the **What-If** scenario tool, see the topic "Microsoft Logistic Regression Algorithm" in SQL Server Books Online.</span></span>

## <a name="see-also"></a><span data-ttu-id="48689-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="48689-153">See Also</span></span>
 [<span data-ttu-id="48689-154">Excel 表分析工具</span><span class="sxs-lookup"><span data-stu-id="48689-154">Table Analysis Tools for Excel</span></span>](table-analysis-tools-for-excel.md)


