---
title: " (Excel) 的表分析工具示例Microsoft Docs"
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- fill from example
ms.assetid: dac57d8f-1c65-4878-8ea0-9c680df5e4fb
author: minewiskan
ms.author: owend
ms.openlocfilehash: 69ff9f554c51240eb6f9151718d30677bfb57996
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689671"
---
# <a name="fill-from-example-table-analysis-tools-for-excel"></a><span data-ttu-id="b8daf-102">从示例填充（Excel 表分析工具）</span><span class="sxs-lookup"><span data-stu-id="b8daf-102">Fill From Example (Table Analysis Tools for Excel)</span></span>
  <span data-ttu-id="b8daf-103">![表分析工具中的“从示例填充”按钮](media/tat-fillex.gif "表分析工具中的“从示例填充”按钮")</span><span class="sxs-lookup"><span data-stu-id="b8daf-103">![Fill From Example button in Table Analysis Tools](media/tat-fillex.gif "Fill From Example button in Table Analysis Tools")</span></span>  
  
 <span data-ttu-id="b8daf-104">"**从示例填充**" 工具可帮助您基于现有值生成新列的数据。</span><span class="sxs-lookup"><span data-stu-id="b8daf-104">The **Fill From Example** tool helps you build new columns of data based on existing values.</span></span>  
  
 <span data-ttu-id="b8daf-105">例如，假设您的数据包含一个 "**采购金额**" 列、"**订单数量**" 列和一个基于使用其他列的公式的 "**高级客户**" 列。</span><span class="sxs-lookup"><span data-stu-id="b8daf-105">For example, suppose your data contains a **Purchase Amount** column, an **Orders Quantity** column, and a **Premier Customer** column that is based on some formula using the other columns.</span></span> <span data-ttu-id="b8daf-106">如果 " **Premier Customer** " 列包含许多空白行，则可以使用 "**采购金额**" 和 "**订单数量**" 列作为输入来推断缺失的值。</span><span class="sxs-lookup"><span data-stu-id="b8daf-106">If the  **Premier Customer** column contains many blank rows, you could use the **Purchase Amount** and **Orders Quantity** columns as the inputs, to infer the missing values.</span></span> <span data-ttu-id="b8daf-107">该工具分析数据中的现有模式和所输入的示例，预测分配给每个客户的类别。</span><span class="sxs-lookup"><span data-stu-id="b8daf-107">The tool analyzes existing patterns in the data together with the examples you entered, and predicts which category to assign to each customer.</span></span>  
  
 <span data-ttu-id="b8daf-108">如果您对结果不满意，可以通过提供更多的示例来改进结果。</span><span class="sxs-lookup"><span data-stu-id="b8daf-108">If you are not satisfied with the results, you can refine the results by providing more examples.</span></span>  
  
## <a name="using-the-fill-from-example-tool"></a><span data-ttu-id="b8daf-109">使用从示例填充工具</span><span class="sxs-lookup"><span data-stu-id="b8daf-109">Using the Fill From Example Tool</span></span>  
  
1.  <span data-ttu-id="b8daf-110">在 "**分析**" 功能区中，单击 "**从示例填充**"。</span><span class="sxs-lookup"><span data-stu-id="b8daf-110">In the **Analyze** ribbon, click **Fill From Example**.</span></span>  
  
2.  <span data-ttu-id="b8daf-111">该工具将基于对数据的分析，自动挑选一列进行填充，您可接受也可覆盖建议的值。</span><span class="sxs-lookup"><span data-stu-id="b8daf-111">The tool will automatically pick a column to fill based on analysis of the data, and you can either accept or override this suggestion.</span></span>  
  
3.  <span data-ttu-id="b8daf-112">为新数据创建一列，并键入要预测的数据的示例。</span><span class="sxs-lookup"><span data-stu-id="b8daf-112">Create a column for the new data, and type in examples of the data that you want to predict.</span></span> <span data-ttu-id="b8daf-113">请确保要预测的每个值都至少有一个示例。</span><span class="sxs-lookup"><span data-stu-id="b8daf-113">Make sure that there is at least one example for every value that you want to predict.</span></span> <span data-ttu-id="b8daf-114">如果要在现有列中填充数据，请选择那个包含缺失值的列。</span><span class="sxs-lookup"><span data-stu-id="b8daf-114">If you are filling in data in an existing column, select the column that has missing values.</span></span>  
  
4.  <span data-ttu-id="b8daf-115">（可选）单击 "**选择要在分析中使用的列**"。</span><span class="sxs-lookup"><span data-stu-id="b8daf-115">Optionally, click **Choose columns to be used in analysis**.</span></span> <span data-ttu-id="b8daf-116">在 "**高级列选择**" 对话框中，指定在填入缺少的数据时最可能有用的列。</span><span class="sxs-lookup"><span data-stu-id="b8daf-116">In the **Advanced Columns Selection** dialog box, specify the columns that are most likely to be useful when filling in the missing data.</span></span>  
  
     <span data-ttu-id="b8daf-117">例如，如果根据经验，您知道一列和包含缺失值的列之间存在因果关系，您可以取消选择其他列，以获得更佳结果。</span><span class="sxs-lookup"><span data-stu-id="b8daf-117">For example, if you know from experience that there is a causal effect between one column and the column that has missing values, you can deselect other columns to get better results.</span></span>  
  
     <span data-ttu-id="b8daf-118">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="b8daf-118">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="b8daf-119">单击 **“运行”** 。</span><span class="sxs-lookup"><span data-stu-id="b8daf-119">Click **Run**.</span></span>  
  
     <span data-ttu-id="b8daf-120">分析完成后，该工具会创建一个包含分析结果的新**模式**工作表。</span><span class="sxs-lookup"><span data-stu-id="b8daf-120">When analysis is complete, the tool creates a new **Patterns** worksheet that contains the results of analysis.</span></span> <span data-ttu-id="b8daf-121">报表列出找到的规则或关键影响因素，并显示每个规则的概率。</span><span class="sxs-lookup"><span data-stu-id="b8daf-121">The report lists the rules, or key influencers, that were found, and shows the probability for each rule.</span></span>  
  
     <span data-ttu-id="b8daf-122">此工具还自动向原始数据表添加包含新值的列。</span><span class="sxs-lookup"><span data-stu-id="b8daf-122">The tool also automatically adds a column that contains the new values to the original data table.</span></span> <span data-ttu-id="b8daf-123">您可查看这些值，并将它们与原始值进行比较。</span><span class="sxs-lookup"><span data-stu-id="b8daf-123">You can review the values and compare them against the original.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="b8daf-124">要求</span><span class="sxs-lookup"><span data-stu-id="b8daf-124">Requirements</span></span>  
 <span data-ttu-id="b8daf-125">您只能处理列中的数据。</span><span class="sxs-lookup"><span data-stu-id="b8daf-125">You can only work with data in columns.</span></span> <span data-ttu-id="b8daf-126">如果要填充的序列存储在行中，可使用 Excel 中的粘贴、转置功能，将这些数据更改为列格式。</span><span class="sxs-lookup"><span data-stu-id="b8daf-126">If the series that you want to fill is stored in a row, you can use the Paste, Transpose function in Excel to change the data to a columnar format.</span></span>  
  
## <a name="understanding-the-pattern-report"></a><span data-ttu-id="b8daf-127">理解模式报表</span><span class="sxs-lookup"><span data-stu-id="b8daf-127">Understanding the Pattern Report</span></span>  
 <span data-ttu-id="b8daf-128">运行 "**从示例填充**" 工具时，将创建一个报表，该报表提供有关检测到的模式的详细信息。</span><span class="sxs-lookup"><span data-stu-id="b8daf-128">When you run the **Fill From Example** tool, a report is created that provides more information about the patterns that were detected.</span></span> <span data-ttu-id="b8daf-129">这些模式用于推断新数据值。</span><span class="sxs-lookup"><span data-stu-id="b8daf-129">These patterns are used for extrapolating new data values.</span></span>  
  
 <span data-ttu-id="b8daf-130">该模式报表显示每个预测值的关键影响因素。</span><span class="sxs-lookup"><span data-stu-id="b8daf-130">The Pattern Report shows the key influencers for each value that was predicted.</span></span> <span data-ttu-id="b8daf-131">每个影响因素或规则都被描述为列、列中的值以及规则对预测的相对影响的组合。</span><span class="sxs-lookup"><span data-stu-id="b8daf-131">Each influencer or rule is described as a combination of a column, the value in that column, and the relative impact of the rule on the prediction.</span></span>  
  
 <span data-ttu-id="b8daf-132">例如，如果您尝试填写一张显示订单发货距离的工作表，您可能会很自然地想到目的地对发货距离有重要影响。</span><span class="sxs-lookup"><span data-stu-id="b8daf-132">For example, if you were trying to fill in a worksheet that shows the shipping distance for orders, you might logically expect the destination to have a strong impact on the value for shipping distance.</span></span> <span data-ttu-id="b8daf-133">在这种情况下，报表可能包含以下行：</span><span class="sxs-lookup"><span data-stu-id="b8daf-133">In this case, the report might contain the following row:</span></span>  
  
|<span data-ttu-id="b8daf-134">列</span><span class="sxs-lookup"><span data-stu-id="b8daf-134">Column</span></span>|<span data-ttu-id="b8daf-135">Value</span><span class="sxs-lookup"><span data-stu-id="b8daf-135">Value</span></span>|<span data-ttu-id="b8daf-136">倾向于</span><span class="sxs-lookup"><span data-stu-id="b8daf-136">Favors</span></span>|<span data-ttu-id="b8daf-137">相对影响</span><span class="sxs-lookup"><span data-stu-id="b8daf-137">Relative Impact</span></span>|  
|------------|-----------|------------|---------------------|  
|<span data-ttu-id="b8daf-138">StateProvinceCode</span><span class="sxs-lookup"><span data-stu-id="b8daf-138">StateProvinceCode</span></span>|<span data-ttu-id="b8daf-139">AB</span><span class="sxs-lookup"><span data-stu-id="b8daf-139">AB</span></span>|<span data-ttu-id="b8daf-140">>500 千米</span><span class="sxs-lookup"><span data-stu-id="b8daf-140">>500 kilometers</span></span>|<span data-ttu-id="b8daf-141">80%</span><span class="sxs-lookup"><span data-stu-id="b8daf-141">80%</span></span>|  
  
 <span data-ttu-id="b8daf-142">这意味着， **StateProvinceCode**列中的值 AB 强烈预测 >500 千米的发货距离。</span><span class="sxs-lookup"><span data-stu-id="b8daf-142">This means that the value AB in the **StateProvinceCode** column strongly predicts a shipping distance of >500 kilometers.</span></span>  
  
 <span data-ttu-id="b8daf-143">通常预测所基于的模式远比此示例复杂，对于每个预测，该报表可能会包含许多行规则。</span><span class="sxs-lookup"><span data-stu-id="b8daf-143">Typically, predictions are based on patterns that are far more complex than this example, and the report may contain many rows of rules for each prediction.</span></span> <span data-ttu-id="b8daf-144">预测值是所有规则综合作用的结果。</span><span class="sxs-lookup"><span data-stu-id="b8daf-144">The effect of all the rules are combined to derive the predicted value.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b8daf-145">**相对影响**显示为灰色条。</span><span class="sxs-lookup"><span data-stu-id="b8daf-145">**Relative Impact** is shown as a shaded bar.</span></span> <span data-ttu-id="b8daf-146">该条越长，此规则对所填充的值的预测概率就越大。</span><span class="sxs-lookup"><span data-stu-id="b8daf-146">The longer the bar, the greater the probability that this rule is predictive of the filled-in value.</span></span>  
  
 <span data-ttu-id="b8daf-147">该工具还会将一个新列添加到名为 Extended 的原始数据表中 \<column name> 。</span><span class="sxs-lookup"><span data-stu-id="b8daf-147">The tool also adds a new column to the original data table, named \<column name> Extended.</span></span>  
  
 <span data-ttu-id="b8daf-148">如果原始数据列中包含值，则该值将被复制到新列中。</span><span class="sxs-lookup"><span data-stu-id="b8daf-148">If the original data column contained a value, that value is copied into the new column.</span></span> <span data-ttu-id="b8daf-149">但是，如果原始列包含空白单元，则在新列的相应位置将包含该向导预测的值。</span><span class="sxs-lookup"><span data-stu-id="b8daf-149">However, if the original column contained a blank cell, the new column contains the value that was predicted by the wizard.</span></span>  
  
## <a name="related-tools-and-information"></a><span data-ttu-id="b8daf-150">相关工具和信息</span><span class="sxs-lookup"><span data-stu-id="b8daf-150">Related Tools and Information</span></span>  
 <span data-ttu-id="b8daf-151">您还可以使用 Excel 数据挖掘客户端中提供的[浏览数据](explore-data-sql-server-data-mining-add-ins.md)向导来检查 excel 列中值的分布情况。</span><span class="sxs-lookup"><span data-stu-id="b8daf-151">You can also use the [Explore Data](explore-data-sql-server-data-mining-add-ins.md) wizard, available in the Data Mining Client for Excel, to examine the distribution of values in an Excel column.</span></span> <span data-ttu-id="b8daf-152">有关详细信息，请参阅[浏览和清理数据](exploring-and-cleaning-data.md)。</span><span class="sxs-lookup"><span data-stu-id="b8daf-152">For more information, see [Exploring and Cleaning Data](exploring-and-cleaning-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8daf-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b8daf-153">See Also</span></span>  
 [<span data-ttu-id="b8daf-154">Excel 表分析工具</span><span class="sxs-lookup"><span data-stu-id="b8daf-154">Table Analysis Tools for Excel</span></span>](table-analysis-tools-for-excel.md)  
  
  
