---
title: 交叉验证 (SQL Server 数据挖掘外接程序) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- cross-validation
- partitioning data [data mining]
- mining models, testing
ms.assetid: bf9483b3-4099-41c4-bbc5-da7005e07bcd
author: minewiskan
ms.author: owend
ms.openlocfilehash: a615de9d20106041f2f01e9912928b64597bc895
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581054"
---
# <a name="cross-validation-sql-server-data-mining-add-ins"></a><span data-ttu-id="64c40-102">交叉验证（SQL Server 数据挖掘外接程序）</span><span class="sxs-lookup"><span data-stu-id="64c40-102">Cross-Validation (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="64c40-103">![“数据挖掘”功能区中的“交叉验证”按钮](media/dmc-xvalid.gif "“数据挖掘”功能区中的“交叉验证”按钮")</span><span class="sxs-lookup"><span data-stu-id="64c40-103">![Cross-Validation button, Data Mining ribbon](media/dmc-xvalid.gif "Cross-Validation button, Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="64c40-104">交叉验证是分析中的一个标准工具，同时也是一项重要的功能，可帮助您开发和优化数据挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="64c40-104">Cross-validation is a standard tool in analytics and is an important feature for helping you develop and fine-tune data mining models.</span></span> <span data-ttu-id="64c40-105">在创建了一个挖掘模型之后，可使用交叉验证来确定该模型的有效性，并将其结果与其他相关的挖掘模型进行比较。</span><span class="sxs-lookup"><span data-stu-id="64c40-105">You use cross-validation after you have created a mining model to ascertain the validity of the model and to compare its results with other, related mining models.</span></span>  
  
 <span data-ttu-id="64c40-106">交叉验证包括两个阶段：定型阶段和报表生成阶段。</span><span class="sxs-lookup"><span data-stu-id="64c40-106">Cross-validation consists of two phases: training and report generation.</span></span> <span data-ttu-id="64c40-107">您将完成下列步骤：</span><span class="sxs-lookup"><span data-stu-id="64c40-107">You will complete the following steps:</span></span>  
  
-   <span data-ttu-id="64c40-108">选择一个目标挖掘结构或挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="64c40-108">Select a target mining structure or mining model.</span></span>  
  
-   <span data-ttu-id="64c40-109">指定目标值（如果适用）。</span><span class="sxs-lookup"><span data-stu-id="64c40-109">Specify the target value if applicable.</span></span>  
  
-   <span data-ttu-id="64c40-110">指定用于对结构数据进行分区的交叉部分或*折叠*数。</span><span class="sxs-lookup"><span data-stu-id="64c40-110">Specify the number of cross-sections, or *folds*, into which to partition the structure data.</span></span>  
  
 <span data-ttu-id="64c40-111">然后，**交叉验证**向导将在每个折叠上创建一个新模型，并在另一个折叠上测试该模型，然后报告该模型的准确性。</span><span class="sxs-lookup"><span data-stu-id="64c40-111">The **Cross-Validation** wizard then creates a new model on each of the folds, tests the model on the other folds, and then reports the accuracy of the model.</span></span> <span data-ttu-id="64c40-112">完成后，**交叉验证**向导将创建一个报表，该报表显示每个折叠的指标，并提供聚合中模型的摘要。</span><span class="sxs-lookup"><span data-stu-id="64c40-112">Upon completion, the **Cross-Validation** wizard creates a report that shows you the metrics for each fold, and provides a summary of the model in aggregate.</span></span> <span data-ttu-id="64c40-113">此信息可用于确定基础数据对模型的有益程度，或对基于同一数据的不同模型进行比较。</span><span class="sxs-lookup"><span data-stu-id="64c40-113">This information can be used to determine how good the underlying data is for a model, or to compare different models that are built on the same data.</span></span>  
  
## <a name="using-the-cross-validation-wizard"></a><span data-ttu-id="64c40-114">使用交叉验证向导</span><span class="sxs-lookup"><span data-stu-id="64c40-114">Using the Cross-Validation Wizard</span></span>  
 <span data-ttu-id="64c40-115">对临时模型和存储在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例中的模型都可以使用交叉验证。</span><span class="sxs-lookup"><span data-stu-id="64c40-115">You can use cross-validation against both temporary models and models that are stored on an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
#### <a name="to-create-a-cross-validation-report"></a><span data-ttu-id="64c40-116">创建交叉验证报表</span><span class="sxs-lookup"><span data-stu-id="64c40-116">To create a cross-validation report</span></span>  
  
1.  <span data-ttu-id="64c40-117">在 "**数据挖掘**" 功能区的 "**准确性和验证**" 组中，单击 "**交叉验证**"。</span><span class="sxs-lookup"><span data-stu-id="64c40-117">In the **Accuracy and Validation** group of the **Data Mining** ribbon, click **Cross Validation**.</span></span>  
  
2.  <span data-ttu-id="64c40-118">在 "**选择结构或模型**" 对话框中，选择一个现有挖掘结构或挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="64c40-118">In the **Select Structure or Model** dialog box, select an existing mining structure or mining model.</span></span> <span data-ttu-id="64c40-119">如果选择结构，该向导将对所有基于该结构且具有相同可预测属性的模型都使用交叉验证。</span><span class="sxs-lookup"><span data-stu-id="64c40-119">If you select a structure, the wizard will use cross-validation against all models that are based on that structure that have the same predictable attribute.</span></span> <span data-ttu-id="64c40-120">如果选择模型，则该向导将只对该模型使用交叉验证。</span><span class="sxs-lookup"><span data-stu-id="64c40-120">If you select a model, the wizard will use cross-validation against only that model.</span></span>  
  
3.  <span data-ttu-id="64c40-121">在 "**指定交叉验证参数**" 对话框的 "**折叠计数**" 框中，选择要在其中划分数据集的折叠数。</span><span class="sxs-lookup"><span data-stu-id="64c40-121">In the **Specify Cross-Validation Parameters** dialog box, in the **Fold Count** box, choose the number of folds among which to divide the data set.</span></span> <span data-ttu-id="64c40-122">折叠是随机选择的数据交叉部分。</span><span class="sxs-lookup"><span data-stu-id="64c40-122">A fold is a randomly selected cross-section of the data.</span></span>  
  
4.  <span data-ttu-id="64c40-123">还可以通过在 "**最大行**数" 文本框中键入一个数字，设置要在交叉验证中使用的最大行数。</span><span class="sxs-lookup"><span data-stu-id="64c40-123">Optionally, set the maximum number of rows to use in cross-validation by typing a number in the **Maximum Rows** text box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="64c40-124">使用的行越多，得到的结果就越精确。</span><span class="sxs-lookup"><span data-stu-id="64c40-124">The more rows that you use, the more accurate the results will be.</span></span> <span data-ttu-id="64c40-125">但是，处理时间也会显著增加。</span><span class="sxs-lookup"><span data-stu-id="64c40-125">However, processing time might also increase significantly.</span></span> <span data-ttu-id="64c40-126">选择的行数取决于您的数据，但是通常情况下，应该在不牺牲性能的前提下选择最大的行数。</span><span class="sxs-lookup"><span data-stu-id="64c40-126">The number you choose depends on your data, but in general, you should choose the highest number you can without sacrificing performance.</span></span> <span data-ttu-id="64c40-127">为了提高性能，也可以指定较少的折叠。</span><span class="sxs-lookup"><span data-stu-id="64c40-127">To improve performance, you can also specify fewer folds.</span></span>  
  
5.  <span data-ttu-id="64c40-128">从 "**目标属性**" 下拉列表中选择一列。</span><span class="sxs-lookup"><span data-stu-id="64c40-128">Select a column from the **Target Attribute** dropdown list.</span></span> <span data-ttu-id="64c40-129">该列表只显示那些在最初创建该模型时配置为可预测属性的列。</span><span class="sxs-lookup"><span data-stu-id="64c40-129">The list displays only those columns that were configured as predictable attributes when you originally created the model.</span></span> <span data-ttu-id="64c40-130">该模型可能包含多个可预测属性，但是您只能选择其中的一个。</span><span class="sxs-lookup"><span data-stu-id="64c40-130">The model may contain multiple predictable attributes, but you can choose only one.</span></span>  
  
6.  <span data-ttu-id="64c40-131">从 "**目标状态**" 下拉列表中选择一个值。</span><span class="sxs-lookup"><span data-stu-id="64c40-131">Select a value from the **Target State** dropdown list.</span></span>  
  
     <span data-ttu-id="64c40-132">如果可预测列包含连续数值数据，则此选项不可用。</span><span class="sxs-lookup"><span data-stu-id="64c40-132">If the predictable column contains continuous numeric data, this option is not available.</span></span>  
  
7.  <span data-ttu-id="64c40-133">（可选）指定一个值，该值用作准确计算预测的**目标阈值**。</span><span class="sxs-lookup"><span data-stu-id="64c40-133">Optionally, specify a value to use as the **Target Threshold** in counting predictions as accurate.</span></span> <span data-ttu-id="64c40-134">该值表示为概率，它是一个 0 到 1 之间的数字，其中 1 表示保证该预测准确，0 表示该预测不可能正确，.5 相当于随机推测。</span><span class="sxs-lookup"><span data-stu-id="64c40-134">This value is expressed as a probability, which is a number between 0 and 1, where 1 means that the prediction is guaranteed to be accurate, 0 means there is no chance that the prediction is correct, and .5 is the same as a random guess.</span></span>  
  
     <span data-ttu-id="64c40-135">如果可预测列包含连续数值数据，则此选项不可用。</span><span class="sxs-lookup"><span data-stu-id="64c40-135">If the predictable column contains continuous numeric data, this option is not available.</span></span>  
  
8.  <span data-ttu-id="64c40-136">单击“完成”。</span><span class="sxs-lookup"><span data-stu-id="64c40-136">Click **Finish**.</span></span> <span data-ttu-id="64c40-137">将创建一个名为 "**交叉验证**" 的新工作表。</span><span class="sxs-lookup"><span data-stu-id="64c40-137">A new worksheet is created, named **Cross-Validation**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="64c40-138">在将模型分区到折叠中并对每个折叠进行测试时，Microsoft Excel 可能会暂时停止响应。</span><span class="sxs-lookup"><span data-stu-id="64c40-138">Microsoft Excel may temporarily become unresponsive while the model is being partitioned into folds and each fold is tested.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="64c40-139">要求</span><span class="sxs-lookup"><span data-stu-id="64c40-139">Requirements</span></span>  
 <span data-ttu-id="64c40-140">若要创建交叉验证报表，您必须已经创建了数据挖掘结构和相关的模型。</span><span class="sxs-lookup"><span data-stu-id="64c40-140">To create a cross-validation report, you must have already created a data mining structure and related models.</span></span> <span data-ttu-id="64c40-141">该向导提供一个对话框，可帮助您从现有结构和模型中进行选择。</span><span class="sxs-lookup"><span data-stu-id="64c40-141">The wizard provides a dialog box to help you choose from existing structure and models.</span></span>  
  
 <span data-ttu-id="64c40-142">如果您选择了一个支持多个挖掘模型的挖掘结构，并且这些模型使用不同的可预测属性，则交叉验证向导将只对那些共享同一可预测属性的模型进行测试。</span><span class="sxs-lookup"><span data-stu-id="64c40-142">If you choose a mining structure that supports multiple mining models, and the models use different predictable attributes, the Cross-Validation wizard will test only those models that share the same predictable attribute.</span></span>  
  
 <span data-ttu-id="64c40-143">如果您选择同时支持聚类分析模型和其他类型模型的结构，则不会对聚类分析模型进行测试。</span><span class="sxs-lookup"><span data-stu-id="64c40-143">If you choose a structure that supports both clustering models and other kinds of models, the clustering models will not be tested.</span></span>  
  
## <a name="understanding-cross-validation-results"></a><span data-ttu-id="64c40-144">了解交叉验证结果</span><span class="sxs-lookup"><span data-stu-id="64c40-144">Understanding Cross-Validation Results</span></span>  
 <span data-ttu-id="64c40-145">交叉验证的结果显示在一个新的工作表中，标题为**的 \<attribute name> 交叉验证报表**。</span><span class="sxs-lookup"><span data-stu-id="64c40-145">The results of cross-validation are displayed in a new worksheet, titled **Cross-Validation Report for \<attribute name>**.</span></span> <span data-ttu-id="64c40-146">新工作表包括多个部分：第一部分是一个摘要，提供有关已测试模型的重要元数据，以便您了解这些结果分别属于哪个模型或结构。</span><span class="sxs-lookup"><span data-stu-id="64c40-146">The new worksheet contains several sections: the first section is a summary that provides important metadata about the model that was tested, so that you can know which model or structure the results are for.</span></span>  
  
 <span data-ttu-id="64c40-147">报表中的第二部分提供一个统计信息摘要，指示原始模型的有效程度。</span><span class="sxs-lookup"><span data-stu-id="64c40-147">The second section in the report provides a statistical summary that indicates how good the original model is.</span></span> <span data-ttu-id="64c40-148">在此摘要中，将分析为每个折叠创建的模型之间的差异，其中包含三个关键度量值：*根本平均方形错误*、*平均绝对错误*和*日志分数*。</span><span class="sxs-lookup"><span data-stu-id="64c40-148">In this summary, the differences between the models created for each fold are analyzed for three key measures: *root mean square error*, *mean absolute error*, and *log score*.</span></span> <span data-ttu-id="64c40-149">这些是标准的统计度量值，不仅用于数据挖掘，还用在大多数类型的统计分析中。</span><span class="sxs-lookup"><span data-stu-id="64c40-149">These are standard statistical measures used not only in data mining but also in most kinds of statistical analysis.</span></span>  
  
 <span data-ttu-id="64c40-150">对于其中的每个度量值，交叉验证向导都会将模型作为一个整体来计算平均值和标准偏差。</span><span class="sxs-lookup"><span data-stu-id="64c40-150">For each of these measures, the Cross-Validation wizard calculates the mean and standard deviation across the model as a whole.</span></span> <span data-ttu-id="64c40-151">它指示在预测不同的数据子集时该模型的一致程度。</span><span class="sxs-lookup"><span data-stu-id="64c40-151">This tells you how consistent the model is when prediction on different subsets of the data.</span></span> <span data-ttu-id="64c40-152">例如，如果标准偏差非常大，则指示为每个折叠创建的模型具有完全不同的结果，因此该模型定型时可能与特定数据组的关联过于紧密，因而不适用于其他数据集。</span><span class="sxs-lookup"><span data-stu-id="64c40-152">For example, if the standard deviation is very large, it indicates that the models created for each fold have very different results, and therefore the model may have trained too closely on a particular group of data and not be applicable to other data sets.</span></span>  
  
 <span data-ttu-id="64c40-153">下面介绍用于评估模型的度量值。</span><span class="sxs-lookup"><span data-stu-id="64c40-153">The following section explains the measures that are used to assess the models.</span></span>  
  
### <a name="tests-and-measures"></a><span data-ttu-id="64c40-154">测试和度量值</span><span class="sxs-lookup"><span data-stu-id="64c40-154">Tests and Measures</span></span>  
 <span data-ttu-id="64c40-155">除了有关数据中的折叠数以及每个折叠中的数据量的一些基本信息之外，工作表还显示有关每个模型的按测试类型分类的一组指标。</span><span class="sxs-lookup"><span data-stu-id="64c40-155">In addition to some basic information about the number of folds in the data, and the amount of data in each fold, the worksheet displays a set of metrics about each model, categorized by test type.</span></span> <span data-ttu-id="64c40-156">例如，聚类分析模型的准确性是由与您将用于预测模型的测试不同的测试评估的。</span><span class="sxs-lookup"><span data-stu-id="64c40-156">For example, the accuracy of a clustering model is assessed by different tests than you would use for a forecasting model.</span></span>  
  
 <span data-ttu-id="64c40-157">下表列出了测试和指标，并附有指标含义的说明。</span><span class="sxs-lookup"><span data-stu-id="64c40-157">The following table lists the tests and metrics, with an explanation of what the metric means.</span></span>  
  
#### <a name="aggregates-and-general-statistical-measures"></a><span data-ttu-id="64c40-158">聚合和常规统计信息度量值</span><span class="sxs-lookup"><span data-stu-id="64c40-158">Aggregates and General Statistical Measures</span></span>  
 <span data-ttu-id="64c40-159">报表中提供的聚合度量值指示您在数据中创建的折叠之间的差异。</span><span class="sxs-lookup"><span data-stu-id="64c40-159">The aggregate measures provided in the report indicate how the folds that you created in the data differ from each other.</span></span>  
  
-   <span data-ttu-id="64c40-160">平均偏差和标准偏差。</span><span class="sxs-lookup"><span data-stu-id="64c40-160">Average and standard deviation.</span></span>  
  
-   <span data-ttu-id="64c40-161">一个模型的所有分区中相对于特定度量值平均值的偏差的平均值。</span><span class="sxs-lookup"><span data-stu-id="64c40-161">Average of the deviation from the mean for a specific measure, across all the partitions in a model.</span></span>  
  
#### <a name="classification-passfail"></a><span data-ttu-id="64c40-162">分类：通过/失败</span><span class="sxs-lookup"><span data-stu-id="64c40-162">Classification: Pass/Fail</span></span>  
 <span data-ttu-id="64c40-163">没有为可预测属性指定目标值时，此度量值用于分类模型中。</span><span class="sxs-lookup"><span data-stu-id="64c40-163">This measure is used in classification models when you do not specify a target value for the predictable attribute.</span></span> <span data-ttu-id="64c40-164">例如，如果您创建了一个可预测多种可能性的模型，此度量值将指示该模型在预测所有可能的值时的有效程度。</span><span class="sxs-lookup"><span data-stu-id="64c40-164">For example, if you create a model that predicts multiple possibilities, this measure tells you how well the model did at predicting all possible values.</span></span>  
  
 <span data-ttu-id="64c40-165">通过/失败是通过对满足以下条件的事例进行计数计算得出**的：如果**具有最高概率的预测状态与输入状态相同并且概率大于您为 "**状态阈值**" 指定的值，则通过：否则，将**失败**。</span><span class="sxs-lookup"><span data-stu-id="64c40-165">Pass/fail is calculated by counting of cases that meet the following conditions: **pass** if the predicted state with the highest probability is the same as the input state and probability is greater than the value that you specified for **State Threshold**; otherwise, **fail**.</span></span>  
  
#### <a name="classification-true-or-false-positives-and-negatives"></a><span data-ttu-id="64c40-166">分类：真正、假正、真负和假负</span><span class="sxs-lookup"><span data-stu-id="64c40-166">Classification: True or False Positives and Negatives</span></span>  
 <span data-ttu-id="64c40-167">此测试可用于具有指定目标的所有分类模型。</span><span class="sxs-lookup"><span data-stu-id="64c40-167">This test is used for all classification models that have a specified target.</span></span> <span data-ttu-id="64c40-168">该度量值指示根据对以下问题的回答，每个事例如何分类：模型预测什么内容和实际结果如何。</span><span class="sxs-lookup"><span data-stu-id="64c40-168">The measure indicates how each case is classified in response to these questions: what did the model predict, and what was the actual result.</span></span>  
  
|<span data-ttu-id="64c40-169">度量</span><span class="sxs-lookup"><span data-stu-id="64c40-169">Measure</span></span>|<span data-ttu-id="64c40-170">说明</span><span class="sxs-lookup"><span data-stu-id="64c40-170">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="64c40-171">真正</span><span class="sxs-lookup"><span data-stu-id="64c40-171">True positive</span></span>|<span data-ttu-id="64c40-172">满足以下条件的事例计数：</span><span class="sxs-lookup"><span data-stu-id="64c40-172">Count of cases that meet these conditions:</span></span><br /><br /> <span data-ttu-id="64c40-173">事例包含目标值。</span><span class="sxs-lookup"><span data-stu-id="64c40-173">Case contains the target value.</span></span><br /><br /> <span data-ttu-id="64c40-174">模型已预测事例包含目标值。</span><span class="sxs-lookup"><span data-stu-id="64c40-174">Model predicted that case contains the target value.</span></span>|  
|<span data-ttu-id="64c40-175">假正</span><span class="sxs-lookup"><span data-stu-id="64c40-175">False positive</span></span>|<span data-ttu-id="64c40-176">满足以下条件的事例计数：</span><span class="sxs-lookup"><span data-stu-id="64c40-176">Count of cases that meet these conditions:</span></span><br /><br /> <span data-ttu-id="64c40-177">实际值等于目标值。</span><span class="sxs-lookup"><span data-stu-id="64c40-177">Actual value is equal to target value.</span></span><br /><br /> <span data-ttu-id="64c40-178">模型已预测事例包含目标值。</span><span class="sxs-lookup"><span data-stu-id="64c40-178">Model predicted that case contains the target value.</span></span>|  
|<span data-ttu-id="64c40-179">真负</span><span class="sxs-lookup"><span data-stu-id="64c40-179">True negative</span></span>|<span data-ttu-id="64c40-180">满足以下条件的事例计数：</span><span class="sxs-lookup"><span data-stu-id="64c40-180">Count of cases that meet these conditions:</span></span><br /><br /> <span data-ttu-id="64c40-181">事例不包含目标值。</span><span class="sxs-lookup"><span data-stu-id="64c40-181">Case does not contain the target value.</span></span><br /><br /> <span data-ttu-id="64c40-182">模型已预测事例不包含目标值。</span><span class="sxs-lookup"><span data-stu-id="64c40-182">Model predicted that case does not contain the target value.</span></span>|  
|<span data-ttu-id="64c40-183">假负</span><span class="sxs-lookup"><span data-stu-id="64c40-183">False negative</span></span>|<span data-ttu-id="64c40-184">满足以下条件的事例计数：</span><span class="sxs-lookup"><span data-stu-id="64c40-184">Count of cases that meet these conditions:</span></span><br /><br /> <span data-ttu-id="64c40-185">实际值不等于目标值。</span><span class="sxs-lookup"><span data-stu-id="64c40-185">Actual value not equal to target value.</span></span><br /><br /> <span data-ttu-id="64c40-186">模型已预测事例不包含目标值。</span><span class="sxs-lookup"><span data-stu-id="64c40-186">Model predicted that case does not contain the target value.</span></span>|  
  
#### <a name="lift"></a><span data-ttu-id="64c40-187">提升</span><span class="sxs-lookup"><span data-stu-id="64c40-187">Lift</span></span>  
 <span data-ttu-id="64c40-188">*提升*是与可能性关联的度量值。</span><span class="sxs-lookup"><span data-stu-id="64c40-188">*Lift* is a measure that is associated with likelihood.</span></span> <span data-ttu-id="64c40-189">如果与随机推测相比，使用模型的结果更有可能，则会说模型提供*积极的提升*。</span><span class="sxs-lookup"><span data-stu-id="64c40-189">If an outcome is more likely when you use the model than when you make a random guess, the model is said to provide *positive lift*.</span></span> <span data-ttu-id="64c40-190">但是，如果该模型做出的预测可能不如随机机会，则提升分数为*负数*。</span><span class="sxs-lookup"><span data-stu-id="64c40-190">However, if the model makes predictions that are less likely than random chance, the lift score is *negative*.</span></span> <span data-ttu-id="64c40-191">因此，此指标指示通过使用模型可获得的改善程度，分数越高越好。</span><span class="sxs-lookup"><span data-stu-id="64c40-191">Therefore, this metric indicates the amount of improvement that can be achieved by using the model, where a higher score is better.</span></span>  
  
 <span data-ttu-id="64c40-192">提升的计算方法为：测试事例中实际预测概率与边缘概率的比率。</span><span class="sxs-lookup"><span data-stu-id="64c40-192">Lift is calculated as the ratio of the actual prediction probability to the marginal probability in the test cases.</span></span>  
  
#### <a name="log-score"></a><span data-ttu-id="64c40-193">对数评分</span><span class="sxs-lookup"><span data-stu-id="64c40-193">Log Score</span></span>  
 <span data-ttu-id="64c40-194">*日志分数*也称为预测的*对数概率分数*，表示两个概率之间的比值，转换为对数刻度。</span><span class="sxs-lookup"><span data-stu-id="64c40-194">The *log score*, also called the *log likelihood score* for the prediction, represents the ratio between two probabilities, converted to a logarithmic scale.</span></span> <span data-ttu-id="64c40-195">由于概率用小数表示，因此，对数评分始终是负数。</span><span class="sxs-lookup"><span data-stu-id="64c40-195">Because probabilities are represented as a decimal fraction, the log score is always a negative number.</span></span> <span data-ttu-id="64c40-196">接近 0 的分数是较好的分数。</span><span class="sxs-lookup"><span data-stu-id="64c40-196">A score that is closer to 0 is a better score.</span></span>  
  
 <span data-ttu-id="64c40-197">原始分数可以具有非常不规则或扭曲的分布，而对数评分与百分比相似。</span><span class="sxs-lookup"><span data-stu-id="64c40-197">Whereas raw scores can have very irregular or skewed distributions, a log score is similar to a percentage.</span></span>  
  
#### <a name="root-mean-square-error"></a><span data-ttu-id="64c40-198">均方根误差</span><span class="sxs-lookup"><span data-stu-id="64c40-198">Root Mean Square Error</span></span>  
 <span data-ttu-id="64c40-199">*平方根* (RMSE 错误) 是统计信息中的一种标准方法，用于查看不同数据集的比较方式，并对输入的小数位数引入的差异进行平滑处理。</span><span class="sxs-lookup"><span data-stu-id="64c40-199">*Root mean square error* (RMSE) is a standard method in statistics for looking at how different data sets compare, and smoothing out the differences that can be introduced by the scale of the inputs.</span></span>  
  
 <span data-ttu-id="64c40-200">RMSE 表示预测值与实际值进行比较时的平均误差。</span><span class="sxs-lookup"><span data-stu-id="64c40-200">RMSE represents the average error of the predicted value when compared to the actual value.</span></span> <span data-ttu-id="64c40-201">它的计算方式为：所有分区事例的平均误差的平方根除以分区中的事例数，不包括目标属性缺失值的行。</span><span class="sxs-lookup"><span data-stu-id="64c40-201">It is calculated as the square root of the mean error for all partition cases, divided by the number of cases in the partition, excluding rows that have missing values for the target attributes.</span></span>  
  
#### <a name="mean-absolute-error"></a><span data-ttu-id="64c40-202">平均绝对误差</span><span class="sxs-lookup"><span data-stu-id="64c40-202">Mean Absolute Error</span></span>  
 <span data-ttu-id="64c40-203">*平均绝对误差*是预测值与实际值的平均误差。</span><span class="sxs-lookup"><span data-stu-id="64c40-203">The *mean absolute error* is the average error of the predicted value to the actual value.</span></span> <span data-ttu-id="64c40-204">其计算方法为：获取误差的绝对值之和，然后找出这些误差的平均值。</span><span class="sxs-lookup"><span data-stu-id="64c40-204">It is calculated by obtaining the absolute sum of errors, and finding the mean of those errors.</span></span>  
  
 <span data-ttu-id="64c40-205">此值可帮助您了解分数与平均值之间的差异大小。</span><span class="sxs-lookup"><span data-stu-id="64c40-205">This value helps you understand how far scores vary from the mean.</span></span>  
  
#### <a name="case-likelihood"></a><span data-ttu-id="64c40-206">事例可能性</span><span class="sxs-lookup"><span data-stu-id="64c40-206">Case Likelihood</span></span>  
 <span data-ttu-id="64c40-207">此度量值只用于聚类分析模型，它指示一个新事例属于特定分类的可能性。</span><span class="sxs-lookup"><span data-stu-id="64c40-207">This measure is used only for clustering models, and indicates how probable it is that a new case belongs to a particular cluster.</span></span>  
  
 <span data-ttu-id="64c40-208">在聚类分析模型中存在两种分类成员身份，具体取决于创建模型所用的方法。</span><span class="sxs-lookup"><span data-stu-id="64c40-208">In clustering models, there are two kinds of cluster membership, depending on the method you used to create the model.</span></span> <span data-ttu-id="64c40-209">在某些模型中，根据 K-means 算法，新的事例应该只属于一个分类。</span><span class="sxs-lookup"><span data-stu-id="64c40-209">In some models, based on the K-means algorithm, a new case is expected to belong to only one cluster.</span></span> <span data-ttu-id="64c40-210">但是，默认情况下，Microsoft 聚类分析算法使用期望最大化方法，该方法假设新事例可能可以属于任何分类。</span><span class="sxs-lookup"><span data-stu-id="64c40-210">However, by default the Microsoft Clustering algorithm uses the Expectation Maximization method, which assumes that a new case potentially can belong to any cluster.</span></span> <span data-ttu-id="64c40-211">因此，在这些模型中，一个事例可以有多个 `CaseLikelihood` 值，但默认情况下报告的值是该事例属于某分类的可能性，该分类是最适合新事例的分类。</span><span class="sxs-lookup"><span data-stu-id="64c40-211">Therefore, in these models a case can have multiple `CaseLikelihood` values, but the one reported by default is the likelihood of the case belonging to the cluster that is the best match for the new case.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64c40-212">另请参阅</span><span class="sxs-lookup"><span data-stu-id="64c40-212">See Also</span></span>  
 [<span data-ttu-id="64c40-213">验证模型和使用模型进行预测 &#40;Excel 数据挖掘外接程序&#41;</span><span class="sxs-lookup"><span data-stu-id="64c40-213">Validating Models and Using Models for Prediction &#40;Data Mining Add-ins for Excel&#41;</span></span>](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md)  
  
  
