---
title: 浏览神经网络模型 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, browsing
- mining models, viewing
- mining model, neural network
- neural networks
- dependency network
ms.assetid: e4224cb7-115b-4889-ac07-03f096fb55fc
author: minewiskan
ms.author: owend
ms.openlocfilehash: ab2673d5b1881f74c2bc146b084d2efc7b06d69b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579299"
---
# <a name="browsing-a-neural-network-model"></a><span data-ttu-id="e6a28-102">浏览神经网络模型</span><span class="sxs-lookup"><span data-stu-id="e6a28-102">Browsing a Neural Network Model</span></span>
  <span data-ttu-id="e6a28-103">使用“浏览”\*\*\*\* 打开神经网络或逻辑回归模型时，该模型显示在交互式查看器（类似于 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 中的神经网络模型查看器）中。</span><span class="sxs-lookup"><span data-stu-id="e6a28-103">When you open a neural network or logistic regression model using **Browse**, the model is displayed in an interactive viewer, similar to the neural network model viewer in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="e6a28-104">该查看器有助于您探索相关性并获取有关该模型和基础数据中各种模式的信息。</span><span class="sxs-lookup"><span data-stu-id="e6a28-104">The viewer helps you explore correlations, and get information about the patterns in the model and the underlying data.</span></span>

##  <a name="explore-the-model"></a><a name="BKMK_Tabs"></a><span data-ttu-id="e6a28-105">浏览模型</span><span class="sxs-lookup"><span data-stu-id="e6a28-105">Explore the Model</span></span>
 <span data-ttu-id="e6a28-106">基于 [!INCLUDE[msCoName](../includes/msconame-md.md)] 神经网络或逻辑回归算法的模型是类似的，它们都是将数据作为已知输入和输出中的一组连接进行分析。</span><span class="sxs-lookup"><span data-stu-id="e6a28-106">Models that are based on [!INCLUDE[msCoName](../includes/msconame-md.md)] Neural Network or Logistic Regression algorithms are similar in that they analyze data as a set of connections among known inputs and outputs.</span></span> <span data-ttu-id="e6a28-107">“浏览”\*\*\*\* 查看器可帮助你使用以下控件浏览这些连接：</span><span class="sxs-lookup"><span data-stu-id="e6a28-107">The **Browse** viewer helps you to explore those connections, using the following controls:</span></span>

-   [<span data-ttu-id="e6a28-108">变量</span><span class="sxs-lookup"><span data-stu-id="e6a28-108">Variables</span></span>](#BKMK_Variables)

-   [<span data-ttu-id="e6a28-109">输入</span><span class="sxs-lookup"><span data-stu-id="e6a28-109">Inputs</span></span>](#BKMK_Inputs)

-   [<span data-ttu-id="e6a28-110">输出</span><span class="sxs-lookup"><span data-stu-id="e6a28-110">Outputs</span></span>](#BKMK_Outputs)

 <span data-ttu-id="e6a28-111">如果要使用此查看器，可以使用[分类向导（Excel 数据挖掘外接程序）](classify-wizard-data-mining-add-ins-for-excel.md)向导创建一个模型，并使用“算法参数”\*\*\*\* 对话框中的“高级”\*\*\*\* 选项将算法更改为 Microsoft 逻辑回归。</span><span class="sxs-lookup"><span data-stu-id="e6a28-111">If you want to experiment with this viewer, you can create a model using the [Classify Wizard &#40;Data Mining Add-ins for Excel&#41;](classify-wizard-data-mining-add-ins-for-excel.md) wizard, and use the **Advanced** option to change the algorithm to Microsoft Logistic Regression in the **Algorithm Parameters** dialog box.</span></span>

###  <a name="variables"></a><a name="BKMK_Variables"></a><span data-ttu-id="e6a28-112">变化</span><span class="sxs-lookup"><span data-stu-id="e6a28-112">Variables</span></span>
 <span data-ttu-id="e6a28-113">“变量”\*\*\*\* 窗格按输入变量对模型影响大小的顺序显示输入变量的列表。</span><span class="sxs-lookup"><span data-stu-id="e6a28-113">The **Variables** pane displays a list of input variables in order of their effect on the model.</span></span> <span data-ttu-id="e6a28-114">可以使用“输入”\*\*\*\* 和“输出”\*\*\*\* 控件来筛选模型，从而控制显示的变量及其顺序。</span><span class="sxs-lookup"><span data-stu-id="e6a28-114">You use the **Input** and **Output** controls to filter the model, affecting the variables that are displayed, as well as their order.</span></span>

 <span data-ttu-id="e6a28-115">使用此查看器，您可以探索在确定客户是更有可能属于自行车购买者类别还是更有可能属于非购买者类别时最为重要的因素。</span><span class="sxs-lookup"><span data-stu-id="e6a28-115">Using this viewer, you can explore the factors that are most important in determining whether a customer more likely belongs to the bike buyer category or the non-buyer category.</span></span>

 <span data-ttu-id="e6a28-116">![针对所选属性结果的测试效果](media/dm13-neuralnet-agebuyer1.gif "针对所选属性结果的测试效果")</span><span class="sxs-lookup"><span data-stu-id="e6a28-116">![Testing effect on outcome of selected attributes](media/dm13-neuralnet-agebuyer1.gif "Testing effect on outcome of selected attributes")</span></span>

##### <a name="explore-variables"></a><span data-ttu-id="e6a28-117">浏览变量</span><span class="sxs-lookup"><span data-stu-id="e6a28-117">Explore variables</span></span>

1.  <span data-ttu-id="e6a28-118">首先，设置当前筛选器，“变量”\*\*\*\* 窗格按最重要属性的顺序进行排序。</span><span class="sxs-lookup"><span data-stu-id="e6a28-118">Initially, the **Variables** pane is sorted in order of the most important attributes, given the current filters.</span></span> <span data-ttu-id="e6a28-119">条的长度指示因素的强度。</span><span class="sxs-lookup"><span data-stu-id="e6a28-119">The length of the bar indicates the strength of the factor.</span></span>

     <span data-ttu-id="e6a28-120">在本示例中，可以看到收入是最有影响的因素，其次是地区。</span><span class="sxs-lookup"><span data-stu-id="e6a28-120">In the example, you can see that income is the most influential factor, followed by region.</span></span> <span data-ttu-id="e6a28-121">另一方面，拥有多辆汽车和很多孩子的客户购买自行车的可能性最低。</span><span class="sxs-lookup"><span data-stu-id="e6a28-121">On the other hand, customers with many cars and many children are highly unlikely to buy a bike.</span></span>

2.  <span data-ttu-id="e6a28-122">在“变量”\*\*\*\* 窗格中，单击“属性”\*\*\*\* 的列标题。</span><span class="sxs-lookup"><span data-stu-id="e6a28-122">In the **Variables** pane, click the column heading for **Attribute**.</span></span>

     <span data-ttu-id="e6a28-123">通过按属性排序，可以看到为每个输入列创建的箱。</span><span class="sxs-lookup"><span data-stu-id="e6a28-123">By sorting on attribute, you can see the bins that were created for each of the input columns.</span></span> <span data-ttu-id="e6a28-124">具有离散值的列（如“occupation”）按文本值进行装箱\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6a28-124">Columns with discrete values, such as occupation, are *binned* by the literal values.</span></span>

3.  <span data-ttu-id="e6a28-125">请注意“Age”\*\*\*\* 和“Income”\*\*\*\* 的值范围。</span><span class="sxs-lookup"><span data-stu-id="e6a28-125">Notice the ranges of values that were found for **Age** and **Income**.</span></span>

     <span data-ttu-id="e6a28-126">如果任何一个输入列是数字（即，整个数据列是连续数字数据类型），则这些数字会存储或装箱到离散范围内。</span><span class="sxs-lookup"><span data-stu-id="e6a28-126">If any of your input columns are numbers (that is, the entire column of data is a continuous numeric data type), the numbers are bucketed, or binned, into discrete ranges.</span></span>

     <span data-ttu-id="e6a28-127">对于“Income”，该列已细分为多个分组，如 78.4-154.06（用于最高收入范围）。</span><span class="sxs-lookup"><span data-stu-id="e6a28-127">For Income, the column has been subdivided into groupings such as 78.4-154.06 (for the uppermost income range).</span></span>

     <span data-ttu-id="e6a28-128">![排序以查看变量的装箱方式](media/dm13-nn-bucketing-variables.gif "排序以查看变量的装箱方式")</span><span class="sxs-lookup"><span data-stu-id="e6a28-128">![sort to view how variables were binned](media/dm13-nn-bucketing-variables.gif "sort to view how variables were binned")</span></span>

     <span data-ttu-id="e6a28-129">如果需要不同的分组，应使用[重新标记（SQL Server 数据挖掘外接程序）](relabel-sql-server-data-mining-add-ins.md)工具或 Excel 函数，在生成模型前创建新收入类别。</span><span class="sxs-lookup"><span data-stu-id="e6a28-129">If you want different groupings, you should use the [Relabel &#40;SQL Server Data Mining Add-ins&#41;](relabel-sql-server-data-mining-add-ins.md) tool, or Excel functions, to create new income categories before building the model.</span></span>

4.  <span data-ttu-id="e6a28-130">单击“倾向于 - 是”\*\*\*\* 将图形恢复到默认视图。</span><span class="sxs-lookup"><span data-stu-id="e6a28-130">Click **Favors Yes** to restore the graph to the default view.</span></span>

     <span data-ttu-id="e6a28-131">默认情况下，按第一个结果值的“倾向于”\*\*\*\* 值对视图排序。</span><span class="sxs-lookup"><span data-stu-id="e6a28-131">By default, the view is sorted by the value of **Favors** for the first outcome value.</span></span> <span data-ttu-id="e6a28-132">通过在“输出”\*\*\*\* 中选择新的“Value 1”\*\*\*\* 和“Value 2”\*\*\*\* 值，可以更改分配给第一列和第二列的结果。</span><span class="sxs-lookup"><span data-stu-id="e6a28-132">You can change which outcomes are assigned to the first and second columns by choosing a new value for **Value 1** and **Value 2** in **Output**.</span></span>

5.  <span data-ttu-id="e6a28-133">将鼠标指针悬停在图表中最上面的彩色条上。</span><span class="sxs-lookup"><span data-stu-id="e6a28-133">Pause the mouse over the topmost colored bar in the chart.</span></span>

     <span data-ttu-id="e6a28-134">出现一个工具提示，其中包含一个“重要性”\*\* 分数、一对“概率”\*\* 分数和一对“提升”\*\* 值。</span><span class="sxs-lookup"><span data-stu-id="e6a28-134">A ToolTip appears that includes an *importance* score, a pair of *probability* scores, and a pair of *lift* values.</span></span>

    -   <span data-ttu-id="e6a28-135">“重要性”\*\*\*\* 是针对整个数据集计算的，用于标识所有输入中与目标结果最相关的属性。</span><span class="sxs-lookup"><span data-stu-id="e6a28-135">**Importance** is calculated across the entire dataset, and identifies the attribute that, given all inputs, is most correlated with the target outcome.</span></span> <span data-ttu-id="e6a28-136">查看器按重要性分数对图表中的值进行排序。</span><span class="sxs-lookup"><span data-stu-id="e6a28-136">The viewer sorts the values in the chart by the importance scores.</span></span>

    -   <span data-ttu-id="e6a28-137">“概率”\*\*\*\* 是面向整个数据集的目标结果，针对每个属性/值对计算的。</span><span class="sxs-lookup"><span data-stu-id="e6a28-137">**Probability** is calculated for each set of attribute-value pairs, for the target outcomes, across the entire data set.</span></span>

    -   <span data-ttu-id="e6a28-138">“提升”\*\*\*\* 可显示此特定属性/值对对于提升某个结果的贡献度。</span><span class="sxs-lookup"><span data-stu-id="e6a28-138">**Lift** tells you how useful this particular attribute-value pair is for promoting one outcome or another.</span></span>

     <span data-ttu-id="e6a28-139">注意：无论将鼠标指针悬停在哪一列上，工具提示都包含相同的信息。</span><span class="sxs-lookup"><span data-stu-id="e6a28-139">Note: The ToolTip contains the same information no matter whether you position the mouse over one column or the other.</span></span>

 [<span data-ttu-id="e6a28-140">返回页首</span><span class="sxs-lookup"><span data-stu-id="e6a28-140">Back To Top</span></span>](#BKMK_Tabs)

###  <a name="inputs"></a><a name="BKMK_Inputs"></a><span data-ttu-id="e6a28-141">输入</span><span class="sxs-lookup"><span data-stu-id="e6a28-141">Inputs</span></span>
 <span data-ttu-id="e6a28-142">通过“输入”\*\*\*\* 窗格，可以选择一组输入作为筛选器应用于模型，这样可以看到这些选项基于定型数据对结果产生的影响</span><span class="sxs-lookup"><span data-stu-id="e6a28-142">The **Inputs** pane lets you choose a set of inputs and apply that as a filter to the model, which lets you see the influence of those choices on the outcome, based on the training data</span></span>

##### <a name="explore-inputs"></a><span data-ttu-id="e6a28-143">浏览输入</span><span class="sxs-lookup"><span data-stu-id="e6a28-143">Explore inputs</span></span>

1.  <span data-ttu-id="e6a28-144">假设要以特定组为目标，查看组中最影响购买行为的因素。</span><span class="sxs-lookup"><span data-stu-id="e6a28-144">Suppose you want to target a particular group, and see the factors that most influence purchasing in that group.</span></span>

     <span data-ttu-id="e6a28-145">在 "**输入**" 窗格中，单击 " **\<All>** **属性**" 下的单元格，然后选择 "**年龄**"。</span><span class="sxs-lookup"><span data-stu-id="e6a28-145">In the **Input** pane, click the **\<All>** cell under **Attribute**, and select **Age**.</span></span>

     <span data-ttu-id="e6a28-146">对于“值”\*\*\*\*，请选择最年轻的年龄类别。</span><span class="sxs-lookup"><span data-stu-id="e6a28-146">For **Value**, select the youngest age category.</span></span>

2.  <span data-ttu-id="e6a28-147">请注意，即使对特定年龄组进行筛选，太平洋地区也靠近列表的顶部。</span><span class="sxs-lookup"><span data-stu-id="e6a28-147">Notice that even when you filter on a particular age group, the Pacific region comes to near the top of the list.</span></span> <span data-ttu-id="e6a28-148">这是因为，与其他地区的客户相比，太平洋地区的客户购买自行车的可能性高很多。</span><span class="sxs-lookup"><span data-stu-id="e6a28-148">This is because customers in the Pacific region are far more likely to buy a bike than customers in other regions.</span></span>

     <span data-ttu-id="e6a28-149">因为地区不是您能影响的因素，所以，若要不考虑此变量查看其他因素，可以再次更改输入。</span><span class="sxs-lookup"><span data-stu-id="e6a28-149">Since region is not something you can influence, to remove this variable from consideration and see other factors, you can change the inputs again.</span></span>

     <span data-ttu-id="e6a28-150">在“输入”\*\*\*\* 窗格中，单击“Age”\*\*\*\* 下面的空单元，选择“Region”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6a28-150">In the **Input** pane, click the empty cell under **Age**, and select **Region**.</span></span>

     <span data-ttu-id="e6a28-151">对于“值”\*\*\*\*，选择“Europe”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6a28-151">For **Value**, select **Europe**.</span></span>

3.  <span data-ttu-id="e6a28-152">继续添加输入筛选器，重点关注特别感兴趣的组。</span><span class="sxs-lookup"><span data-stu-id="e6a28-152">Continue adding input filters to focus on a group of particular interest.</span></span>

     <span data-ttu-id="e6a28-153">例如，对于输入属性，添加“Gender”\*\*\*\*，然后选择“Female”\*\*\*\* 作为值。</span><span class="sxs-lookup"><span data-stu-id="e6a28-153">For example, for the input attribute, add **Gender**, and select **Female** as the value.</span></span>

     <span data-ttu-id="e6a28-154">![针对所选属性结果的测试效果](media/dm13-neuralnet-agebuyer2.gif "针对所选属性结果的测试效果")</span><span class="sxs-lookup"><span data-stu-id="e6a28-154">![Testing effect on outcome of selected attributes](media/dm13-neuralnet-agebuyer2.gif "Testing effect on outcome of selected attributes")</span></span>

     <span data-ttu-id="e6a28-155">注意变量列表是如何变化的。</span><span class="sxs-lookup"><span data-stu-id="e6a28-155">Notice how the list of variables changes.</span></span> <span data-ttu-id="e6a28-156">此时，“Income”\*\*\*\* 是在预测目标结果时最重要的变量。</span><span class="sxs-lookup"><span data-stu-id="e6a28-156">Now **Income** is the variable that is most important in predicting the target outcome.</span></span>

     <span data-ttu-id="e6a28-157">应用输入筛选器的顺序不会影响结果。</span><span class="sxs-lookup"><span data-stu-id="e6a28-157">The order in which you apply the input filters does not affect the results.</span></span>

 [<span data-ttu-id="e6a28-158">返回页首</span><span class="sxs-lookup"><span data-stu-id="e6a28-158">Back To Top</span></span>](#BKMK_Tabs)

###  <a name="outputs"></a><a name="BKMK_Outputs"></a><span data-ttu-id="e6a28-159">输出</span><span class="sxs-lookup"><span data-stu-id="e6a28-159">Outputs</span></span>
 <span data-ttu-id="e6a28-160">在“输出”\*\*\*\* 窗格中，可以选择感兴趣的结果。</span><span class="sxs-lookup"><span data-stu-id="e6a28-160">In the **Outputs** pane, you can choose the outcome that you are interested in.</span></span> <span data-ttu-id="e6a28-161">通过神经网络，可以指定所需数目的结果列，不过，添加更多输出会增加模型的复杂性，可能需要更长的处理时间。</span><span class="sxs-lookup"><span data-stu-id="e6a28-161">Neural networks let you specify as many outcome columns as you like, although adding more outputs adds to the complexity of the model and may require a much longer time to process.</span></span>

 <span data-ttu-id="e6a28-162">若要比较两个输出，这两个输出必须已指定为“预测”\*\*\*\* 或“仅预测”\*\*\*\* 列。</span><span class="sxs-lookup"><span data-stu-id="e6a28-162">To compare two outputs, they must have been designated as **Predict** or **Predict Only** columns.</span></span>

##### <a name="explore-outputs"></a><span data-ttu-id="e6a28-163">浏览输出</span><span class="sxs-lookup"><span data-stu-id="e6a28-163">Explore outputs</span></span>

1.  <span data-ttu-id="e6a28-164">使用“输出属性”\*\*\*\* 列表选择一个属性。</span><span class="sxs-lookup"><span data-stu-id="e6a28-164">Use the **Output Attribute** list to select an attribute.</span></span>

2.  <span data-ttu-id="e6a28-165">从“值 1”和“值 2”列表中选择两个结果。</span><span class="sxs-lookup"><span data-stu-id="e6a28-165">Select two outcomes from the Value 1 and Value 2 lists.</span></span> <span data-ttu-id="e6a28-166">输出属性的这两个状态将在 **“变量”** 窗格中进行比较。</span><span class="sxs-lookup"><span data-stu-id="e6a28-166">These two states of the output attribute will be compared in the **Variables** pane.</span></span>

 [<span data-ttu-id="e6a28-167">返回页首</span><span class="sxs-lookup"><span data-stu-id="e6a28-167">Back To Top</span></span>](#BKMK_Tabs)

## <a name="more-about-neural-network-models"></a><span data-ttu-id="e6a28-168">有关神经网络模型的详细信息</span><span class="sxs-lookup"><span data-stu-id="e6a28-168">More About Neural Network Models</span></span>
 <span data-ttu-id="e6a28-169">查看器中的信息是使用特定于此模型类型的存储过程从服务器检索的：System.Microsoft.AnalysisServices.System.DataMining.NeuralNet.GetAttributeScores。</span><span class="sxs-lookup"><span data-stu-id="e6a28-169">The information in the viewer is retrieved from the server using a stored procedure specific to this model type: System.Microsoft.AnalysisServices.System.DataMining.NeuralNet.GetAttributeScores.</span></span>

 <span data-ttu-id="e6a28-170">如果要使用外接程序创建含有多个可预测属性的模型，请使用“高级”\*\*\*\* 建模选项。</span><span class="sxs-lookup"><span data-stu-id="e6a28-170">If you want to create a model with multiple predictable attributes using the add-ins, use the **Advanced** modeling options.</span></span>

 <span data-ttu-id="e6a28-171">有关详细信息，请参阅[创建挖掘结构（SQL Server 数据挖掘外接程序）](create-mining-structure-sql-server-data-mining-add-ins.md)和[将模型添加到结构（Excel 数据挖掘外接程序）](add-model-to-structure-data-mining-add-ins-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="e6a28-171">For more information, see [Create Mining Structure &#40;SQL Server Data Mining Add-ins&#41;](create-mining-structure-sql-server-data-mining-add-ins.md) and [Add Model to Structure &#40;Data Mining Add-ins for Excel&#41;](add-model-to-structure-data-mining-add-ins-for-excel.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e6a28-172">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e6a28-172">See Also</span></span>
 [<span data-ttu-id="e6a28-173">在 Excel 中浏览模型 &#40;SQL Server 数据挖掘外接程序&#41;</span><span class="sxs-lookup"><span data-stu-id="e6a28-173">Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](browsing-models-in-excel-sql-server-data-mining-add-ins.md)


