---
title: 分类矩阵 (SQL Server 数据挖掘外接程序) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, validating
- classification matrix
- confusion table
- mining models, testing
ms.assetid: d6f620f4-39af-4714-9628-28ce3c361fca
author: minewiskan
ms.author: owend
ms.openlocfilehash: a930f2628ac41fc5886cf41d7ec0ad274b42bf2f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579266"
---
# <a name="classification-matrix-sql-server-data-mining-add-ins"></a><span data-ttu-id="49baf-102">分类矩阵（SQL Server 数据挖掘外接程序）</span><span class="sxs-lookup"><span data-stu-id="49baf-102">Classification Matrix (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="49baf-103">![“数据挖掘”功能区中的“分类矩阵”按钮](media/dmc-cmatrix.gif "“数据挖掘”功能区中的“分类矩阵”按钮")</span><span class="sxs-lookup"><span data-stu-id="49baf-103">![Classification Matrix button, Data Mining ribbon](media/dmc-cmatrix.gif "Classification Matrix button, Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="49baf-104">可以使用分类矩阵评估模型进行预测的准确性。</span><span class="sxs-lookup"><span data-stu-id="49baf-104">You can use the classification matrix to assess the accuracy of a model for prediction.</span></span> <span data-ttu-id="49baf-105">若要生成分类矩阵，您可通过模型运行测试数据集，分类矩阵工具会将来自测试集的实际值与模型进行的预测进行比较。</span><span class="sxs-lookup"><span data-stu-id="49baf-105">To generate a classification matrix, you run a set of testing data through the model, and the classification matrix tool compares the actual values from the testing set against the predictions made by the model.</span></span> <span data-ttu-id="49baf-106">通过查看该矩阵，您可以一目了然地判断模型正确的频率以及预测错误的频率。</span><span class="sxs-lookup"><span data-stu-id="49baf-106">By looking at the matrix, you can tell at a glance how often the model is correct, and how often it predicts wrongly.</span></span>  
  
 <span data-ttu-id="49baf-107">在这些外接程序中，使用**分类矩阵**向导选择模型，指定测试数据，然后生成结果矩阵。</span><span class="sxs-lookup"><span data-stu-id="49baf-107">In these add-ins, use the **Classification Matrix** wizard to select a model, specify the testing data, and then generate a results matrix.</span></span>  
  
## <a name="how-to-read-a-classification-matrix"></a><span data-ttu-id="49baf-108">如何读取分类矩阵</span><span class="sxs-lookup"><span data-stu-id="49baf-108">How to Read a Classification Matrix</span></span>  
 <span data-ttu-id="49baf-109">假设您的目标是设计客户忠实度计划，然后将客户分配到适当的类别，以便您可以向他们提供适当的激励级别。</span><span class="sxs-lookup"><span data-stu-id="49baf-109">Let's assume your objective is to design a customer loyalty program and then assign customers to appropriate categories, so that you can provide them with the appropriate level of incentives.</span></span> <span data-ttu-id="49baf-110">您已经实现了三个级别的奖励计划--青铜、银和黄金，并在试用阶段向客户提供这些级别。</span><span class="sxs-lookup"><span data-stu-id="49baf-110">You have implemented three levels for the reward program -- bronze, silver, and gold - and given these out to customers in a trial phase.</span></span> <span data-ttu-id="49baf-111">您还设计了一个模型，该模型分析客户并预测正确的类别。</span><span class="sxs-lookup"><span data-stu-id="49baf-111">You have also designed a model that analyzes customers and predicts the correct categories.</span></span> <span data-ttu-id="49baf-112">现在，您将对试用数据使用分类矩阵以确定模型在为所有客户预测正确类别方面的表现。</span><span class="sxs-lookup"><span data-stu-id="49baf-112">Now you will use the classification matrix on the trial data to determine how good the model was at predicting the correct offer for all customers.</span></span>  
  
 <span data-ttu-id="49baf-113">来自分类矩阵的表可告知您基于模型分配给每种类别的客户数，并将该结果与实际针对每种奖励级别注册的客户数进行比较。</span><span class="sxs-lookup"><span data-stu-id="49baf-113">The table from the classification matrix tells you how many customers would be assigned to each category based on the model, and compares that result to the number of customers who actually signed up for each reward level.</span></span>  
  
||<span data-ttu-id="49baf-114">铜卡（实际数）</span><span class="sxs-lookup"><span data-stu-id="49baf-114">Bronze (Actual)</span></span>|<span data-ttu-id="49baf-115">金卡（实际数）</span><span class="sxs-lookup"><span data-stu-id="49baf-115">Gold (Actual)</span></span>|<span data-ttu-id="49baf-116">银卡（实际数）</span><span class="sxs-lookup"><span data-stu-id="49baf-116">Silver (Actual)</span></span>|  
|-|-----------------------|---------------------|-----------------------|  
|<span data-ttu-id="49baf-117">Bronze</span><span class="sxs-lookup"><span data-stu-id="49baf-117">Bronze</span></span>|<span data-ttu-id="49baf-118">**94.45%**</span><span class="sxs-lookup"><span data-stu-id="49baf-118">**94.45%**</span></span>|<span data-ttu-id="49baf-119">15.18%</span><span class="sxs-lookup"><span data-stu-id="49baf-119">15.18%</span></span>|<span data-ttu-id="49baf-120">1.70%</span><span class="sxs-lookup"><span data-stu-id="49baf-120">1.70%</span></span>|  
|<span data-ttu-id="49baf-121">Gold</span><span class="sxs-lookup"><span data-stu-id="49baf-121">Gold</span></span>|<span data-ttu-id="49baf-122">2.72%</span><span class="sxs-lookup"><span data-stu-id="49baf-122">2.72%</span></span>|<span data-ttu-id="49baf-123">**84.82%**</span><span class="sxs-lookup"><span data-stu-id="49baf-123">**84.82%**</span></span>|<span data-ttu-id="49baf-124">0.00%</span><span class="sxs-lookup"><span data-stu-id="49baf-124">0.00%</span></span>|  
|<span data-ttu-id="49baf-125">Silver</span><span class="sxs-lookup"><span data-stu-id="49baf-125">Silver</span></span>|<span data-ttu-id="49baf-126">1.84%</span><span class="sxs-lookup"><span data-stu-id="49baf-126">1.84%</span></span>|<span data-ttu-id="49baf-127">0.00%</span><span class="sxs-lookup"><span data-stu-id="49baf-127">0.00%</span></span>|<span data-ttu-id="49baf-128">**93.80%**</span><span class="sxs-lookup"><span data-stu-id="49baf-128">**93.80%**</span></span>|  
|<span data-ttu-id="49baf-129">*恰当*</span><span class="sxs-lookup"><span data-stu-id="49baf-129">*Correct*</span></span>|<span data-ttu-id="49baf-130">*95.45%*</span><span class="sxs-lookup"><span data-stu-id="49baf-130">*95.45%*</span></span>|<span data-ttu-id="49baf-131">*84.82%*</span><span class="sxs-lookup"><span data-stu-id="49baf-131">*84.82%*</span></span>|<span data-ttu-id="49baf-132">*98.30%*</span><span class="sxs-lookup"><span data-stu-id="49baf-132">*98.30%*</span></span>|  
|<span data-ttu-id="49baf-133">*分类错误*</span><span class="sxs-lookup"><span data-stu-id="49baf-133">*Misclassified*</span></span>|<span data-ttu-id="49baf-134">*4.55%*</span><span class="sxs-lookup"><span data-stu-id="49baf-134">*4.55%*</span></span>|<span data-ttu-id="49baf-135">*15.18%*</span><span class="sxs-lookup"><span data-stu-id="49baf-135">*15.18%*</span></span>|<span data-ttu-id="49baf-136">*1.70%*</span><span class="sxs-lookup"><span data-stu-id="49baf-136">*1.70%*</span></span>|  
  
-   <span data-ttu-id="49baf-137">每列显示测试数据集中的实际值。</span><span class="sxs-lookup"><span data-stu-id="49baf-137">Each column shows the actual values in the testing dataset.</span></span>  
  
-   <span data-ttu-id="49baf-138">每行显示预测值。</span><span class="sxs-lookup"><span data-stu-id="49baf-138">Each row shows the predicted values.</span></span>  
  
-   <span data-ttu-id="49baf-139">从矩阵的左上角到右下角沿对角线排列的粗体值显示了模型预测的正确情况。</span><span class="sxs-lookup"><span data-stu-id="49baf-139">The values in boldface, which run diagonally from the upper-left corner to the lower-right corner of the matrix, give you the picture of what the model got right.</span></span>  
  
-   <span data-ttu-id="49baf-140">对角线之外的所有其他值都表示错误。</span><span class="sxs-lookup"><span data-stu-id="49baf-140">All other values outside the diagonal represent errors.</span></span> <span data-ttu-id="49baf-141">一些错误是假正，表示模型预测客户会加入金牌计划，但事实并非如此。</span><span class="sxs-lookup"><span data-stu-id="49baf-141">Some errors are false positives, meaning the model predicted the customer would join the gold program but was wrong.</span></span>  <span data-ttu-id="49baf-142">根据您的具体业务领域，误报成本可能非常高昂。</span><span class="sxs-lookup"><span data-stu-id="49baf-142">Depending on your domain, false positives can be very costly.</span></span>  
  
     <span data-ttu-id="49baf-143">有些错误是假负，表示模型预测客户应无意加入某计划，但客户实际却加入了该计划。</span><span class="sxs-lookup"><span data-stu-id="49baf-143">Others are false negatives, meaning the model predicted the customer would not be interested though he or she did join the program.</span></span> <span data-ttu-id="49baf-144">根据具体工作领域，这种丧失机会的成本也可能十分高昂。</span><span class="sxs-lookup"><span data-stu-id="49baf-144">Again, depending on the problem domain, this lost opportunity cost might be significant.</span></span>  
  
## <a name="using-the-classification-matrix-wizard"></a><span data-ttu-id="49baf-145">使用分类矩阵向导</span><span class="sxs-lookup"><span data-stu-id="49baf-145">Using the Classification Matrix Wizard</span></span>  
  
1.  <span data-ttu-id="49baf-146">选择预测要基于的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="49baf-146">Select the mining model on which to base predictions.</span></span>  
  
2.  <span data-ttu-id="49baf-147">选择新测试数据的源，或使用随结构保存的测试数据。</span><span class="sxs-lookup"><span data-stu-id="49baf-147">Select a source of new test data, or use testing data that was saved with the structure.</span></span>  
  
3.  <span data-ttu-id="49baf-148">选择要评估其准确性的列。</span><span class="sxs-lookup"><span data-stu-id="49baf-148">Select the column for which you want to assess accuracy.</span></span> <span data-ttu-id="49baf-149">可以在创建矩阵时仅选择一列，但是该列可以具有多个值。</span><span class="sxs-lookup"><span data-stu-id="49baf-149">You can choose only one column when creating a matrix, but the column can have multiple values.</span></span>  
  
     <span data-ttu-id="49baf-150">提示：如果可预测列要与许多列比较，则分类矩阵可能难以解读。</span><span class="sxs-lookup"><span data-stu-id="49baf-150">Tip: It can be difficult to interpret a classification matrix if your predictable column has many columns to compare.</span></span>  
  
     <span data-ttu-id="49baf-151">在 "**选择要预测的列**" 页中，还可以指定是否要显示错误和不正确的值的计数，或显示百分比。</span><span class="sxs-lookup"><span data-stu-id="49baf-151">In the **Select Columns to Predict** page, you can also specify whether you want to display the count of incorrect and incorrect values, or display a percentage.</span></span>  
  
4.  <span data-ttu-id="49baf-152">在“选择源数据”页上，指示是使用外部测试数据还是随模型保存的测试数据。</span><span class="sxs-lookup"><span data-stu-id="49baf-152">On the Select Source Data page, indicate whether you are using external testing data, or the test data saved with the model.</span></span>  
  
5.  <span data-ttu-id="49baf-153">如果使用外部测试数据，则需要在向导的 "**指定关系**" 页上将模型映射到输入列。</span><span class="sxs-lookup"><span data-stu-id="49baf-153">If you use external testing data, you need to map the model to the input columns on the **Specify Relationship** page of the wizard.</span></span>  
  
     <span data-ttu-id="49baf-154">如果使用嵌入式测试数据集，则会为您自动执行映射</span><span class="sxs-lookup"><span data-stu-id="49baf-154">If you use the embedded test data set, the mapping is done for you</span></span>  
  
6.  <span data-ttu-id="49baf-155">单击 "**完成**" 可对模型运行预测并生成分类矩阵。</span><span class="sxs-lookup"><span data-stu-id="49baf-155">Click **Finish** to run predictions against the model and generate the classification matrix.</span></span>  
  
     <span data-ttu-id="49baf-156">该向导将创建一个报表，报表中包含分类矩阵和有关分析的其他详细信息。</span><span class="sxs-lookup"><span data-stu-id="49baf-156">The wizard creates a report that contains the classification matrix and other details about the analysis.</span></span> <span data-ttu-id="49baf-157">此报表保存为 Excel 中的表，报表上方有一个摘要，指示正确预测的事例数以及错误的预测数。</span><span class="sxs-lookup"><span data-stu-id="49baf-157">This report is saved as a table in Excel, with a summary above the report that indicates how many cases were correctly predicted and how many predictions were wrong.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="49baf-158">要求</span><span class="sxs-lookup"><span data-stu-id="49baf-158">Requirements</span></span>  
  
-   <span data-ttu-id="49baf-159">若要创建分类矩阵，您必须拥有支持准确性度量的现有挖掘模型的访问权限。</span><span class="sxs-lookup"><span data-stu-id="49baf-159">To create a classification matrix, you must have access to an existing mining model that supports accuracy measurement.</span></span> <span data-ttu-id="49baf-160">预测模型和关联模型无法使用此工具进行度量。</span><span class="sxs-lookup"><span data-stu-id="49baf-160">Forecasting models and association models cannot be measured using this tool.</span></span>  
  
-   <span data-ttu-id="49baf-161">所度量的模型需要预测作为离散值或已离散化的值。</span><span class="sxs-lookup"><span data-stu-id="49baf-161">The model that you are measuring needs to predict a value that is either discrete or that has already been discretized.</span></span>  
  
-   <span data-ttu-id="49baf-162">如果未使用选项来保存测试集以及结构或模型，则需要获取一个输入数据集，该数据集本质上具有与在模型中使用的列数相同的列。</span><span class="sxs-lookup"><span data-stu-id="49baf-162">If you didn't use the option to save a testing set along with your structure or model, you need to obtain an input data set that has essentially the same number of columns, with matching data types, as those used in the model.</span></span>  
  
-   <span data-ttu-id="49baf-163">数据挖掘模型和测试中要使用的新数据都必须包含至少一个可预测的列，而且这些列必须包含同类数据。</span><span class="sxs-lookup"><span data-stu-id="49baf-163">Both the data mining model and the new data that you are using for testing must contain at least one column that can be predicted, and the columns must contain the same kind of data.</span></span>  
  
### <a name="known-issues"></a><span data-ttu-id="49baf-164">已知问题</span><span class="sxs-lookup"><span data-stu-id="49baf-164">Known Issues</span></span>  
 <span data-ttu-id="49baf-165">在 SQL Server 2012 和 SQL Server 2014 中，将内部测试数据集映射到模型的功能在**分类矩阵**工具中不起作用。</span><span class="sxs-lookup"><span data-stu-id="49baf-165">In SQL Server 2012 and SQL Server 2014, the ability to map the internal test data set to the model is not working in the **Classification Matrix** tool.</span></span> <span data-ttu-id="49baf-166">但是，您可以指定外部数据集，然后选择定型集作为输入以确定原始数据集上的错误。</span><span class="sxs-lookup"><span data-stu-id="49baf-166">However, you can specify an external data set, and then select the training set as the input to determine error on the original data set.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49baf-167">另请参阅</span><span class="sxs-lookup"><span data-stu-id="49baf-167">See Also</span></span>  
 <span data-ttu-id="49baf-168">[验证模型和使用模型进行预测 &#40;Excel 数据挖掘外接程序&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="49baf-168">[Validating Models and Using Models for Prediction &#40;Data Mining Add-ins for Excel&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md) </span></span>  
 <span data-ttu-id="49baf-169">[浏览数据挖掘外接 &#40;SQL Server 数据&#41;](explore-data-sql-server-data-mining-add-ins.md) </span><span class="sxs-lookup"><span data-stu-id="49baf-169">[Explore Data &#40;SQL Server Data Mining Add-ins&#41;](explore-data-sql-server-data-mining-add-ins.md) </span></span>  
 [<span data-ttu-id="49baf-170">检测类别 &#40;Excel&#41;的表分析工具</span><span class="sxs-lookup"><span data-stu-id="49baf-170">Detect Categories &#40;Table Analysis Tools for Excel&#41;</span></span>](detect-categories-table-analysis-tools-for-excel.md)  
  
  
