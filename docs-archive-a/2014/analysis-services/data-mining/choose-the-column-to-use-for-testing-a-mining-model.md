---
title: 选择用于测试挖掘模型的列 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- columns [data mining], predictable mining columns
- Mining Accuracy Chart [Analysis Services], columns
- predictable mining columns [Analysis Services]
ms.assetid: c6a8f23a-da21-4f31-9521-99460d624649
author: minewiskan
ms.author: owend
ms.openlocfilehash: 326a7084600695d95d3a132f633041e9abad045b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588157"
---
# <a name="choose-the-column-to-use-for-testing-a-mining-model"></a><span data-ttu-id="04ad6-102">选择用于测试挖掘模型的列</span><span class="sxs-lookup"><span data-stu-id="04ad6-102">Choose the Column to Use for Testing a Mining Model</span></span>
  <span data-ttu-id="04ad6-103">您必须决定要访问哪个结果才能度量挖掘模型的准确性。</span><span class="sxs-lookup"><span data-stu-id="04ad6-103">Before you can measure the accuracy of a mining model, you must decide which outcome it is that you want to assess.</span></span> <span data-ttu-id="04ad6-104">大多数数据挖掘模型都要求您在创建模型时至少选择一列用作可预测属性。</span><span class="sxs-lookup"><span data-stu-id="04ad6-104">Most data mining models require that you choose at least one column to use as the predictable attribute when you create the model.</span></span> <span data-ttu-id="04ad6-105">因此，在测试模型准确性时，您一般必须选择要测试的属性。</span><span class="sxs-lookup"><span data-stu-id="04ad6-105">Therefore, when you test the accuracy of the model, you generally must select that attribute to test.</span></span>  
  
 <span data-ttu-id="04ad6-106">下表介绍了选择在测试中使用的可预测属性时应注意的一些其他事项：</span><span class="sxs-lookup"><span data-stu-id="04ad6-106">The following list describes some additional considerations for choosing the predictable attribute to use in testing:</span></span>  
  
-   <span data-ttu-id="04ad6-107">某些类型的数据挖掘模型可以预测多个属性（如神经网络），这些属性可以浏览多个属性之间的关系。</span><span class="sxs-lookup"><span data-stu-id="04ad6-107">Some types of data mining models can predict multiple attributes-such as neural networks, which can explore the relationships between many attributes.</span></span>  
  
-   <span data-ttu-id="04ad6-108">其他类型的挖掘模型（如聚类分析模型）不必具有可预测属性。</span><span class="sxs-lookup"><span data-stu-id="04ad6-108">Other types of mining models-such as clustering models-do not necessarily have a predictable attribute.</span></span> <span data-ttu-id="04ad6-109">除非聚类分析模型具有可预测属性，否则无法测试它们。</span><span class="sxs-lookup"><span data-stu-id="04ad6-109">Clustering models cannot be tested unless they have a predictable attribute.</span></span>  
  
-   <span data-ttu-id="04ad6-110">若要创建散点图或度量回归模型的准确性，则需选择连续可预测属性作为结果。</span><span class="sxs-lookup"><span data-stu-id="04ad6-110">To create a scatter plot or measure the accuracy of a regression model requires that you choose a continuous predictable attribute as the outcome.</span></span> <span data-ttu-id="04ad6-111">在这种情况下，您不能指定目标值。</span><span class="sxs-lookup"><span data-stu-id="04ad6-111">In that case, you cannot specify a target value.</span></span> <span data-ttu-id="04ad6-112">如果要创建散点图之外的任何内容，则基础挖掘结构列的内容类型还必须为 **“离散”** 或 **“离散化”**。</span><span class="sxs-lookup"><span data-stu-id="04ad6-112">If you are creating anything other than a scatter plot, the underlying mining structure column must also have a content type of **Discrete** or **Discretized**.</span></span>  
  
-   <span data-ttu-id="04ad6-113">如果选择离散属性作为可预测结果，则还可以指定一个目标值，或者可以将 **“预测值”** 字段留空。</span><span class="sxs-lookup"><span data-stu-id="04ad6-113">If you choose a discrete attribute as the predictable outcome, you can also specify a target value, or you can leave the **Predict Value** field blank.</span></span> <span data-ttu-id="04ad6-114">如果包含**预测值**，则图表将仅度量模型对预测目标值的有效性。</span><span class="sxs-lookup"><span data-stu-id="04ad6-114">If you include a **Predict Value**, the chart will measure only the model's effectiveness at predicting the target value.</span></span> <span data-ttu-id="04ad6-115">如果不指定目标结果，则会度量模型预测所有结果的准确性。</span><span class="sxs-lookup"><span data-stu-id="04ad6-115">If you do not specify a target outcome, the model is measured for its accuracy in predicting all outcomes.</span></span>  
  
-   <span data-ttu-id="04ad6-116">如果要在一个准确性图表中包含多个模型并对它们进行比较，则所有模型都必须使用相同的可预测列。</span><span class="sxs-lookup"><span data-stu-id="04ad6-116">If you want to include multiple models and compare them in a single accuracy chart, all models must use the same predictable column.</span></span>  
  
-   <span data-ttu-id="04ad6-117">在创建交叉验证报表时， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 将自动分析所有具有相同可预测属性的模型。</span><span class="sxs-lookup"><span data-stu-id="04ad6-117">When you create a cross-validation report, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] will automatically analyze all models that have the same predictable attribute.</span></span>  
  
-   <span data-ttu-id="04ad6-118">当选择了选项 **“同步预测列和值”** 时， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 会自动选择具有相同名称和匹配的数据类型的可预测列。</span><span class="sxs-lookup"><span data-stu-id="04ad6-118">When the option, **Synchronize Prediction columns and Values**, is selected, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] automatically chooses predictable columns that have the same names and matching data types.</span></span> <span data-ttu-id="04ad6-119">如果您的列不满足这些条件，则可以关闭此选项并手动选择一个可预测列。</span><span class="sxs-lookup"><span data-stu-id="04ad6-119">If your columns do not meet these criteria, you can turn off this option and manually choose a predictable column.</span></span> <span data-ttu-id="04ad6-120">如果要使用具有与该模型不同的列的外部数据集测试该模型，则可能需要执行此操作。</span><span class="sxs-lookup"><span data-stu-id="04ad6-120">You might need to do this if you are testing the model with an external data set that has different columns than the model.</span></span> <span data-ttu-id="04ad6-121">但是，如果您选择的列的数据类型有误，则您将收到错误或错误的结果。</span><span class="sxs-lookup"><span data-stu-id="04ad6-121">However, if you choose a column with the wrong the type of data you will either get an error or bad results.</span></span>  
  
### <a name="specify-the-outcome-to-predict"></a><span data-ttu-id="04ad6-122">指定要预测的结果</span><span class="sxs-lookup"><span data-stu-id="04ad6-122">Specify the outcome to predict</span></span>  
  
1.  <span data-ttu-id="04ad6-123">双击挖掘结构以在数据挖掘设计器中将其打开。</span><span class="sxs-lookup"><span data-stu-id="04ad6-123">Double-click the mining structure to open it in Data Mining Designer.</span></span>  
  
2.  <span data-ttu-id="04ad6-124">选择 **“挖掘准确性图表”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="04ad6-124">Select the **Mining Accuracy Chart** tab.</span></span>  
  
3.  <span data-ttu-id="04ad6-125">选择 **“输入选择”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="04ad6-125">Select the **Input Selection** tab.</span></span>  
  
4.  <span data-ttu-id="04ad6-126">在 **“输入选择”** 选项卡的 **“可预测列名称”** 下，为要包含在图表中的每个模型选择一个可预测列。</span><span class="sxs-lookup"><span data-stu-id="04ad6-126">On the **Input Selection** tab, under **Predictable Column Name**, select a predictable column for each model that you include in the chart.</span></span>  
  
     <span data-ttu-id="04ad6-127">**“可预测列名称”** 框中提供的挖掘模型列只有使用类型设置为 **“预测”** 或 **“仅预测”** 的列。</span><span class="sxs-lookup"><span data-stu-id="04ad6-127">The mining model columns that are available in the **Predictable Column Name** box are only those with the usage type set to **Predict** or **Predict Only**.</span></span>  
  
5.  <span data-ttu-id="04ad6-128">如果希望确定模型的提升情况，则必须从 **“预测值”** 列表为该模型选择要度量的特定结果值。</span><span class="sxs-lookup"><span data-stu-id="04ad6-128">If you want to determine the lift for a model, you must select a specific outcome value to measure, for by choosing from the **Predict Value** list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04ad6-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="04ad6-129">See Also</span></span>  
 <span data-ttu-id="04ad6-130">[选择和映射模型测试数据](choose-and-map-model-testing-data.md) </span><span class="sxs-lookup"><span data-stu-id="04ad6-130">[Choose and Map Model Testing Data](choose-and-map-model-testing-data.md) </span></span>  
 [<span data-ttu-id="04ad6-131">选择准确性图表类型和设置图表选项</span><span class="sxs-lookup"><span data-stu-id="04ad6-131">Choose an Accuracy Chart Type and Set Chart Options</span></span>](choose-an-accuracy-chart-type-and-set-chart-options.md)  
  
  
