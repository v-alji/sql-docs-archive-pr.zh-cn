---
title: 验证模型和使用模型进行预测 (Excel 数据挖掘外接程序) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, validating
- mining models, charting
- validation [data mining]
- mining models, testing
ms.assetid: e245ac1f-1230-48e9-9091-e70b131aa2a8
author: minewiskan
ms.author: owend
ms.openlocfilehash: c1dd4f9bab977a90579076b824d2c0aa525c84af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580399"
---
# <a name="validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel"></a><span data-ttu-id="631cc-102">验证模型和使用模型进行预测（Excel 数据挖掘外接程序）</span><span class="sxs-lookup"><span data-stu-id="631cc-102">Validating Models and Using Models for Prediction (Data Mining Add-ins for Excel)</span></span>
  <span data-ttu-id="631cc-103">测试和验证模型是数据挖掘过程中很重要的一步。</span><span class="sxs-lookup"><span data-stu-id="631cc-103">Testing and validating your model is an important step in the data mining process.</span></span> <span data-ttu-id="631cc-104">将挖掘模型部署到生产环境中之前，必须了解挖掘模型对于实际数据的执行情况。</span><span class="sxs-lookup"><span data-stu-id="631cc-104">You must know how well your mining models perform against real data before you deploy the models into a production environment.</span></span>  
  
 <span data-ttu-id="631cc-105">数据挖掘外接程序包含的工具可帮助您对生成的模型进行测试，以及使用模型创建预测和建议。</span><span class="sxs-lookup"><span data-stu-id="631cc-105">The Data Mining Add-ins include tools that help you test the models you built, and create predictions and recommendations using the models.</span></span>  
  
## <a name="accuracy-chart"></a><span data-ttu-id="631cc-106">准确性图表</span><span class="sxs-lookup"><span data-stu-id="631cc-106">Accuracy Chart</span></span>  
 <span data-ttu-id="631cc-107">**准确性图表**向导可帮助您创建预测查询，并通过创建提升图或散点图来评估数据挖掘模型的性能。</span><span class="sxs-lookup"><span data-stu-id="631cc-107">The **Accuracy Chart** wizard helps you create a prediction query and assess the performance of a data mining model by creating a lift chart or scatter plot chart.</span></span> <span data-ttu-id="631cc-108">提升图有助于区分同一结构中几乎相同的两个模型，从而帮助您确定哪个模型能够提供最佳的预测。</span><span class="sxs-lookup"><span data-stu-id="631cc-108">The lift chart helps distinguish between models in a structure that are almost the same, to help you determine which model provides the best predictions.</span></span>  
  
 [<span data-ttu-id="631cc-109">SQL Server 数据挖掘外接程序的准确性图表 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="631cc-109">Accuracy Chart &#40;SQL Server Data Mining Add-ins&#41;</span></span>](accuracy-chart-sql-server-data-mining-add-ins.md)  
  
## <a name="classification-matrix"></a><span data-ttu-id="631cc-110">分类矩阵</span><span class="sxs-lookup"><span data-stu-id="631cc-110">Classification Matrix</span></span>  
 <span data-ttu-id="631cc-111">**分类矩阵**向导可帮助您创建预测查询，以评估分类模型的性能。</span><span class="sxs-lookup"><span data-stu-id="631cc-111">The **Classification Matrix** wizard helps you create a prediction query to assess the performance of a classification model.</span></span> <span data-ttu-id="631cc-112">其输出是一张图表，汇总了模型所做出的准确预测及不准确预测。</span><span class="sxs-lookup"><span data-stu-id="631cc-112">The output is a chart that summarizes both accurate and inaccurate predictions made by the model.</span></span> <span data-ttu-id="631cc-113">该矩阵是一个重要的工具，因为它不仅可显示模型正确预测某一值的频率，而且还显示模型最经常预测错的值。</span><span class="sxs-lookup"><span data-stu-id="631cc-113">The matrix is a valuable tool because it not only shows how frequently the model correctly predicted a value, but also shows which values the model most frequently predicted incorrectly.</span></span>  
  
 [<span data-ttu-id="631cc-114">SQL Server 数据挖掘外接程序的分类矩阵 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="631cc-114">Classification Matrix &#40;SQL Server Data Mining Add-ins&#41;</span></span>](classification-matrix-sql-server-data-mining-add-ins.md)  
  
## <a name="profit-chart"></a><span data-ttu-id="631cc-115">利润图</span><span class="sxs-lookup"><span data-stu-id="631cc-115">Profit Chart</span></span>  
 <span data-ttu-id="631cc-116">**利润图**向导可帮助您权衡使用数据挖掘模型的好处，并评估误报和漏报的成本</span><span class="sxs-lookup"><span data-stu-id="631cc-116">The **Profit Chart** wizard helps you weigh the benefits of using a data mining model and assess the costs of both false positives and false negatives</span></span>  
  
 <span data-ttu-id="631cc-117">此图表类型衡量模型的预测精确性并且纳入您指定的单位和整体成本。</span><span class="sxs-lookup"><span data-stu-id="631cc-117">This chart type measures the prediction accuracy of the model and incorporates unit and overall costs that you specify.</span></span>  
  
 <span data-ttu-id="631cc-118">[利润图 &#40;SQL Server 数据挖掘外接程序&#41;](profit-chart-sql-server-data-mining-add-ins.md)。</span><span class="sxs-lookup"><span data-stu-id="631cc-118">[Profit Chart &#40;SQL Server Data Mining Add-ins&#41;](profit-chart-sql-server-data-mining-add-ins.md).</span></span>  
  
## <a name="cross-validation"></a><span data-ttu-id="631cc-119">交叉验证</span><span class="sxs-lookup"><span data-stu-id="631cc-119">Cross-Validation</span></span>  
 <span data-ttu-id="631cc-120">交叉验证是数据挖掘社区中的一种既有技术，用于评估某一数据集的有效性以及该数据集上挖掘模型的精确性。</span><span class="sxs-lookup"><span data-stu-id="631cc-120">Cross-validation is an established technique in the data mining community for assessing the validity of a data set and the accuracy of a mining model on that data set.</span></span> <span data-ttu-id="631cc-121">它会将一个数据集划分为多个子集，然后在每个子集上反复创建、定型和测试模型。</span><span class="sxs-lookup"><span data-stu-id="631cc-121">It divides a set of data into subsets, and then iteratively creates, trains, and tests models on each subset.</span></span>  
  
 <span data-ttu-id="631cc-122">使用**交叉验证**向导可以指定要将数据划分成多少个折叠，然后提供一份交叉验证报表，该报表以统计方式描述这些交叉部分之间的差异。</span><span class="sxs-lookup"><span data-stu-id="631cc-122">The **Cross-Validation** wizard lets you specify the number of folds to divide your data by, and then provides a cross-validation report that statistically describes the differences among these cross-sections.</span></span> <span data-ttu-id="631cc-123">从该报表中，您可以确定模型是在所有定型数据上都正常运行，还是可能只对特定子集倾斜。</span><span class="sxs-lookup"><span data-stu-id="631cc-123">From this you can determine whether the model performs well on all training data, or might be skewed to a particular subset.</span></span>  
  
 [<span data-ttu-id="631cc-124">SQL Server 数据挖掘外接程序的交叉验证 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="631cc-124">Cross-Validation &#40;SQL Server Data Mining Add-ins&#41;</span></span>](cross-validation-sql-server-data-mining-add-ins.md)  
  
## <a name="query-wizard"></a><span data-ttu-id="631cc-125">查询向导</span><span class="sxs-lookup"><span data-stu-id="631cc-125">Query Wizard</span></span>  
 <span data-ttu-id="631cc-126">**查询**向导是一种可帮助您生成预测查询的交互式工具。</span><span class="sxs-lookup"><span data-stu-id="631cc-126">The **Query** wizard is an interactive tool that helps you build a prediction query.</span></span> <span data-ttu-id="631cc-127">查询是您生成建议、将来的预测等的方式。</span><span class="sxs-lookup"><span data-stu-id="631cc-127">Queries are how you generate recommendations, future forecasts, and so forth.</span></span>  
  
 <span data-ttu-id="631cc-128">在**查询**向导中，您可以选择一个模型，然后以单个值或从表或范围提供输入数据，向导将帮助您选择要输出的列。</span><span class="sxs-lookup"><span data-stu-id="631cc-128">In the **Query** wizard, you pick a model, and then provide input data, either as single values or from a table or range, and the wizard helps you select columns to output.</span></span> <span data-ttu-id="631cc-129">您还可以向查询中添加函数，以便生成概率分数和其他有用的统计信息。</span><span class="sxs-lookup"><span data-stu-id="631cc-129">You can also add functions to your query to generate probability scores and other useful statistics.</span></span>  
  
 [<span data-ttu-id="631cc-130">查询 &#40;SQL Server 数据挖掘外接程序&#41;</span><span class="sxs-lookup"><span data-stu-id="631cc-130">Query &#40;SQL Server Data Mining Add-ins&#41;</span></span>](query-sql-server-data-mining-add-ins.md)  
  
## <a name="advanced-query-editor"></a><span data-ttu-id="631cc-131">高级查询编辑器</span><span class="sxs-lookup"><span data-stu-id="631cc-131">Advanced Query Editor</span></span>  
 <span data-ttu-id="631cc-132">**高级查询编辑器**是一组交互式对话框，可帮助您生成所有类型的 DMX 语句、运行自定义查询来创建和定型新模型、删除模型或创建新数据集。</span><span class="sxs-lookup"><span data-stu-id="631cc-132">The **Advanced Query Editor** is an interactive set of dialog boxes that helps you build all kinds of DMX statements, anything from running custom queries to creating and training new models, deleting models, or creating new data sets.</span></span>  
  
 [<span data-ttu-id="631cc-133">高级数据挖掘查询编辑器</span><span class="sxs-lookup"><span data-stu-id="631cc-133">Advanced Data Mining Query Editor</span></span>](advanced-data-mining-query-editor.md)  
  
## <a name="see-also"></a><span data-ttu-id="631cc-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="631cc-134">See Also</span></span>  
 <span data-ttu-id="631cc-135">[浏览和清理数据](exploring-and-cleaning-data.md) </span><span class="sxs-lookup"><span data-stu-id="631cc-135">[Exploring and Cleaning Data](exploring-and-cleaning-data.md) </span></span>  
 <span data-ttu-id="631cc-136">[创建数据挖掘模型](creating-a-data-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="631cc-136">[Creating a Data Mining Model](creating-a-data-mining-model.md) </span></span>  
 [<span data-ttu-id="631cc-137">&#40;Excel 数据挖掘外接程序部署和缩放挖掘模型&#41;</span><span class="sxs-lookup"><span data-stu-id="631cc-137">Deploying and Scaling Mining Models &#40;Data Mining Add-ins for Excel&#41;</span></span>](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)  
  
  
