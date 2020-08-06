---
title: SQL Server 数据挖掘外接程序的准确性图表 () |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- accuracy chart
- mining models, validating
- mining models, charting
- lift chart
- mining models, testing
- lift [data mining]
ms.assetid: 303973b4-71c0-4cfc-b7bc-92218b52509d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 45ca5b4d3944948b257b5fa063ebce5583701157
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578545"
---
# <a name="accuracy-chart-sql-server-data-mining-add-ins"></a><span data-ttu-id="a996e-102">准确性图表（SQL Server 数据挖掘外接程序）</span><span class="sxs-lookup"><span data-stu-id="a996e-102">Accuracy Chart (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="a996e-103">![“数据挖掘”功能区中的“准确性图表”按钮](media/dmc-accchart.gif "“数据挖掘”功能区中的“准确性图表”按钮")</span><span class="sxs-lookup"><span data-stu-id="a996e-103">![Accuracy Chart button in Data Mining ribbon](media/dmc-accchart.gif "Accuracy Chart button in Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="a996e-104">通过准确性图表，可以将模型应用于新的数据集，然后评估该模型的性能。</span><span class="sxs-lookup"><span data-stu-id="a996e-104">An accuracy chart enables you to apply a model to a new set of data and then evaluate how well the model performs.</span></span> <span data-ttu-id="a996e-105">此向导创建的准确性图表是*提升图*，它是一种经常用于度量数据挖掘模型准确性的图表。</span><span class="sxs-lookup"><span data-stu-id="a996e-105">The accuracy chart created by this wizard is a *lift chart*, which is a type of chart that is frequently used to measure the accuracy of a data mining model.</span></span> <span data-ttu-id="a996e-106">这种类型的准确性图表以图形方式显示以下改善：即在使用指定数据挖掘模型时，准确性为 100％ 的理想预测与随机预测相比之间的改善。</span><span class="sxs-lookup"><span data-stu-id="a996e-106">This type of accuracy chart displays a graphical representation of the improvement that you obtain from using the specified data mining model, as compared to random predictions, and to the ideal case where 100 percent of predictions are accurate.</span></span> <span data-ttu-id="a996e-107">您可以在一个图表中比较多个模型。</span><span class="sxs-lookup"><span data-stu-id="a996e-107">You can compare multiple models within a single chart.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a996e-108">示例</span><span class="sxs-lookup"><span data-stu-id="a996e-108">Example</span></span>  
 <span data-ttu-id="a996e-109">假设 Adventure Works Cycles 的市场部要开展一次定向邮寄活动。</span><span class="sxs-lookup"><span data-stu-id="a996e-109">Consider the case in which the Marketing department at Adventure Works Cycles wants to create a targeted mailing campaign.</span></span> <span data-ttu-id="a996e-110">从以往的活动中，他们推算应有 10% 的答复率。</span><span class="sxs-lookup"><span data-stu-id="a996e-110">From past campaigns, they know that a 10 percent response rate is typical.</span></span> <span data-ttu-id="a996e-111">在数据库的一个表中，存储了一个包含 10,000 名潜在客户的列表。</span><span class="sxs-lookup"><span data-stu-id="a996e-111">They have a list of 10,000 potential customers stored in a table in the database.</span></span> <span data-ttu-id="a996e-112">按照正常答复率计算，预计将有 1,000 名客户答复。</span><span class="sxs-lookup"><span data-stu-id="a996e-112">Based on the typical response rate, they can expect 1,000 customers to respond.</span></span>  
  
 <span data-ttu-id="a996e-113">但是，由于他们只能承担向 5,000 名客户邮寄广告的费用，因此市场部使用挖掘模型来寻找最有可能答复的 5,000 名目标客户。</span><span class="sxs-lookup"><span data-stu-id="a996e-113">However, because they can afford to mail an advertisement to only 5,000 customers, the Marketing department uses a mining model to target the 5,000 customers who are most likely to respond.</span></span>  
  
 <span data-ttu-id="a996e-114">如果该公司随机选择 5,000 名客户，则估计只能收到 500 个积极答复，因为正常情况下只有 10% 的客户答复。</span><span class="sxs-lookup"><span data-stu-id="a996e-114">If the company randomly selects 5,000 customers, they can expect to receive only 500 positive responses, because only 10 percent of those who are targeted typically respond.</span></span> <span data-ttu-id="a996e-115">这正是提升图中的随机线所表示的情况。</span><span class="sxs-lookup"><span data-stu-id="a996e-115">This scenario is what the random line in the lift chart represents.</span></span>  
  
 <span data-ttu-id="a996e-116">但是，如果市场部使用挖掘模型确定邮寄对象，假设该模型完美无缺的话，则公司可以预期实现这样的结果：向模型建议的 1,000 名潜在客户邮寄广告，会收到所有客户的答复，共计 1,000 份答复。</span><span class="sxs-lookup"><span data-stu-id="a996e-116">However, if the Marketing department uses a mining model to target their mailing, and if the model were perfect, the company could expect to receive 1,000 responses by mailing an advertisement to the 1,000 potential customers recommended by the model.</span></span> <span data-ttu-id="a996e-117">这正是提升图中的理想线所表示的情况。</span><span class="sxs-lookup"><span data-stu-id="a996e-117">This scenario is represented by the ideal line in the lift chart.</span></span>  
  
## <a name="using-the-accuracy-chart-wizard"></a><span data-ttu-id="a996e-118">使用准确性图表向导</span><span class="sxs-lookup"><span data-stu-id="a996e-118">Using the Accuracy Chart Wizard</span></span>  
 <span data-ttu-id="a996e-119">若要创建准确性图表，必须参考现有数据挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="a996e-119">To create an accuracy chart, you must reference an existing data mining structure.</span></span> <span data-ttu-id="a996e-120">对于基于该数据挖掘结构的多个模型，只要它们的预测对象相同，就可以衡量它们的准确性。</span><span class="sxs-lookup"><span data-stu-id="a996e-120">You can measure the accuracy of multiple models that are based on that structure, as long as they predict the same thing.</span></span>  
  
 <span data-ttu-id="a996e-121">如果无法确定哪个结构可用，则可浏览服务器。</span><span class="sxs-lookup"><span data-stu-id="a996e-121">If you are not sure which structures are available, you can browse the server.</span></span> <span data-ttu-id="a996e-122">有关详细信息，请参阅[在 Excel 中浏览模型 &#40;SQL Server 数据挖掘外接程序&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)。</span><span class="sxs-lookup"><span data-stu-id="a996e-122">For more information, see [Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md).</span></span>  
  
#### <a name="to-create-an-accuracy-chart"></a><span data-ttu-id="a996e-123">创建准确性图表</span><span class="sxs-lookup"><span data-stu-id="a996e-123">To create an accuracy chart</span></span>  
  
1.  <span data-ttu-id="a996e-124">单击 "**数据挖掘客户端**" 功能区。</span><span class="sxs-lookup"><span data-stu-id="a996e-124">Click the **Data Mining Client** ribbon.</span></span>  
  
2.  <span data-ttu-id="a996e-125">在 "**准确性和验证**" 组中，单击 "**准确性图表**"。</span><span class="sxs-lookup"><span data-stu-id="a996e-125">In the **Accuracy and Validation** group, click **Accuracy Chart**.</span></span>  
  
3.  <span data-ttu-id="a996e-126">在 "**选择结构或模型**" 对话框中，选择要评估的模型。</span><span class="sxs-lookup"><span data-stu-id="a996e-126">In the **Select Structure or Model** dialog box, choose the model that you want to evaluate.</span></span> <span data-ttu-id="a996e-127">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="a996e-127">Click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a996e-128">必须选择与要测试的数据最相匹配的模型。</span><span class="sxs-lookup"><span data-stu-id="a996e-128">You must choose a model that closely matches the data you intend to test.</span></span>  
  
4.  <span data-ttu-id="a996e-129">在 "**指定要预测的列和要预测的值**" 对话框中，选择要预测的列和目标值（如果适用）。</span><span class="sxs-lookup"><span data-stu-id="a996e-129">In the **Specify Column to Predict and Value to Predict** dialog box, choose the column that you want to predict, and a target value, if appropriate.</span></span> <span data-ttu-id="a996e-130">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="a996e-130">Click **Next**.</span></span>  
  
     <span data-ttu-id="a996e-131">例如，在上面的示例中，您可以选择用来建立顾客答复模型的列，并将目标值指定为“可能购买”。</span><span class="sxs-lookup"><span data-stu-id="a996e-131">For example, in the example above, you might choose the column that models the customer response, and specify the target value as "Probably Will Buy".</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a996e-132">不能预测连续值。</span><span class="sxs-lookup"><span data-stu-id="a996e-132">You cannot predict a continuous value.</span></span> <span data-ttu-id="a996e-133">但是，可通过将值分割为不同的离散范围，来离散化该列。</span><span class="sxs-lookup"><span data-stu-id="a996e-133">However, you can discretize the column by separating the values into discrete ranges.</span></span> <span data-ttu-id="a996e-134">在创建数据挖掘模型之前，就必须完成此操作。</span><span class="sxs-lookup"><span data-stu-id="a996e-134">You must do this before creating the data mining model.</span></span>  
  
5.  <span data-ttu-id="a996e-135">在 "**选择源数据**" 对话框中，指定将通过模型传递的数据源以创建预测。</span><span class="sxs-lookup"><span data-stu-id="a996e-135">In the **Select Source Data** dialog box, specify the source of the data that you will pass through the model in order to create a prediction.</span></span>  
  
6.  <span data-ttu-id="a996e-136">如果您使用的是外部数据源，而不是与模型一起存储的测试数据，则在 "**指定关系**" 对话框中，将新源数据中的列映射到数据挖掘模型中使用的列。</span><span class="sxs-lookup"><span data-stu-id="a996e-136">If you are using an external source of data, and not the test data that is stored with the model, in the **Specify Relationships** dialog box, map the columns in the new source data to the columns used in the data mining model.</span></span>  
  
     <span data-ttu-id="a996e-137">如果列名称类似，向导将自动映射它们。</span><span class="sxs-lookup"><span data-stu-id="a996e-137">If the column names are similar, the wizard will automatically map them.</span></span> <span data-ttu-id="a996e-138">虽然输入数据中的某些列可能与分析无关，可以忽略，但某些列是数据挖掘模型处理输入所必需的。</span><span class="sxs-lookup"><span data-stu-id="a996e-138">Although some columns in your input data may be irrelevant to analysis and can be ignored, some columns are required for the data mining model to process the input.</span></span> <span data-ttu-id="a996e-139">这样的列可能包括事务 ID、目标值或用于预测的列。</span><span class="sxs-lookup"><span data-stu-id="a996e-139">Such columns might include a transaction ID, the target value, or columns used for prediction.</span></span> <span data-ttu-id="a996e-140">如果无法映射所需的列，向导将提供一则警告消息。</span><span class="sxs-lookup"><span data-stu-id="a996e-140">If you fail to map a column that is required, the wizard will provide a warning message.</span></span>  
  
7.  <span data-ttu-id="a996e-141">单击“完成”。</span><span class="sxs-lookup"><span data-stu-id="a996e-141">Click **Finish**.</span></span>  
  
     <span data-ttu-id="a996e-142">向导将创建一个包括提升图和基础数据的报表。</span><span class="sxs-lookup"><span data-stu-id="a996e-142">The wizard creates a report that includes the lift chart and underlying data.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="a996e-143">要求</span><span class="sxs-lookup"><span data-stu-id="a996e-143">Requirements</span></span>  
 <span data-ttu-id="a996e-144">如果预测的是离散值，则必须选择要预测的目标值。</span><span class="sxs-lookup"><span data-stu-id="a996e-144">If you are predicting a discrete value, you must select the target value that you want to predict.</span></span> <span data-ttu-id="a996e-145">例如，如果数据是按照答复“Yes: Buy”(1) 和答复“No: Do Not Buy”(2) 进行分类的，则必须将 1 或 2 指定为预测值。</span><span class="sxs-lookup"><span data-stu-id="a996e-145">For example, if your data is categorized with a response "Yes: Buy" as 1 and the response "No: Do Not Buy" as 2, you must specify either 1 or 2 as the prediction values.</span></span> <span data-ttu-id="a996e-146">不过，如果要预测某一范围的值，则可以一次只比较两个值。</span><span class="sxs-lookup"><span data-stu-id="a996e-146">However, if you want to predict a range of values, you can compare only two values at a time.</span></span> <span data-ttu-id="a996e-147">例如，如果要预测 5 以上的分数，则可能必须重新标记源数据，并创建一个将结果分为两组（一组大于 5、一组小于 5）的新模型。</span><span class="sxs-lookup"><span data-stu-id="a996e-147">For example, if you want to predict a score above 5, you might have to relabel your source data and create a new model that separates the results into two sets: those greater than 5 and those less than 5.</span></span> <span data-ttu-id="a996e-148">然后，可以比较这两组的准确性。</span><span class="sxs-lookup"><span data-stu-id="a996e-148">You can then compare the accuracy of those two groups.</span></span>  
  
## <a name="understanding-accuracy"></a><span data-ttu-id="a996e-149">了解准确性</span><span class="sxs-lookup"><span data-stu-id="a996e-149">Understanding Accuracy</span></span>  
 <span data-ttu-id="a996e-150">可以创建两种类型的图表，在一种图表中指定可预测列的状态，而在另一种中不指定该状态。</span><span class="sxs-lookup"><span data-stu-id="a996e-150">You can create two types of charts, one in which you specify a state of the predictable column, and one in which you do not specify the state.</span></span>  
  
 <span data-ttu-id="a996e-151">如果指定可预测列的状态，则该图表的 X 轴表示用于比较预测的测试数据集的百分比。</span><span class="sxs-lookup"><span data-stu-id="a996e-151">If you specify the state of the predictable column, the x-axis of the chart represents the percentage of the test dataset that is used to compare the predictions.</span></span> <span data-ttu-id="a996e-152">该图表的 Y 轴表示预测为指定状态的值的百分比。</span><span class="sxs-lookup"><span data-stu-id="a996e-152">The y-axis of the chart represents the percentage of values that are predicted to be the specified state.</span></span>  
  
 <span data-ttu-id="a996e-153">如果不指定可预测列的状态，则图表将显示模型针对所有可能预测的准确性。</span><span class="sxs-lookup"><span data-stu-id="a996e-153">If you do not specify the state of the predictable column, the chart shows the accuracy of the model for all possible predictions.</span></span>  
  
 <span data-ttu-id="a996e-154">有关提升图工作原理以及如何基于随机预测线和理想预测线计算准确性的详细信息，请参阅 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 联机丛书中的主题“提升图”。</span><span class="sxs-lookup"><span data-stu-id="a996e-154">For more information about how a lift chart works, and how accuracy is calculated based on the random and ideal prediction lines, see the topic "Lift Chart" in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a996e-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a996e-155">See Also</span></span>  
 [<span data-ttu-id="a996e-156">验证模型和使用模型进行预测 &#40;Excel 数据挖掘外接程序&#41;</span><span class="sxs-lookup"><span data-stu-id="a996e-156">Validating Models and Using Models for Prediction &#40;Data Mining Add-ins for Excel&#41;</span></span>](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md)  
  
  
