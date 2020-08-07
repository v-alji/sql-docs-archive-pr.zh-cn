---
title: 利用提升图测试准确性 (基本数据挖掘教程) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 822d414b-4a39-473f-80c3-53476e30655a
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 7a3dcdd1d1b78911f5ffd37a383532abdd4814c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690892"
---
# <a name="testing-accuracy-with-lift-charts-basic-data-mining-tutorial"></a><span data-ttu-id="163ee-102">测试提升图的准确性（数据挖掘基础教程）</span><span class="sxs-lookup"><span data-stu-id="163ee-102">Testing Accuracy with Lift Charts (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="163ee-103">在数据挖掘设计器的 "**挖掘准确性图表**" 选项卡上，您可以计算每个模型进行预测的程度，并将每个模型的结果与其他模型的结果进行比较。</span><span class="sxs-lookup"><span data-stu-id="163ee-103">On the **Mining Accuracy Chart** tab of Data Mining Designer, you can calculate how well each of your models makes predictions, and compare the results of each model directly against the results of the other models.</span></span> <span data-ttu-id="163ee-104">这种比较方法称为*提升图*。</span><span class="sxs-lookup"><span data-stu-id="163ee-104">This method of comparison is referred to as a *lift chart*.</span></span> <span data-ttu-id="163ee-105">通常，用提升图或分类准确性对挖掘模型的预测准确性进行度量。</span><span class="sxs-lookup"><span data-stu-id="163ee-105">Typically, the predictive accuracy of a mining model is measured by either lift or classification accuracy.</span></span> <span data-ttu-id="163ee-106">在本教程中，我们将只使用提升图。</span><span class="sxs-lookup"><span data-stu-id="163ee-106">For this tutorial we will use the lift chart only.</span></span>  
  
 <span data-ttu-id="163ee-107">在本主题中，您将完成下列任务：</span><span class="sxs-lookup"><span data-stu-id="163ee-107">In this topic, you will perform the following tasks:</span></span>  
  
-   [<span data-ttu-id="163ee-108">选择输入数据</span><span class="sxs-lookup"><span data-stu-id="163ee-108">Choose the Input Data</span></span>](#BKMK_InputData)  
  
-   [<span data-ttu-id="163ee-109">配置准确性图表参数</span><span class="sxs-lookup"><span data-stu-id="163ee-109">Configure Accuracy Chart Parameters</span></span>](#BKMK_Selecting)  
  
##  <a name="choosing-the-input-data"></a><a name="BKMK_InputData"></a><span data-ttu-id="163ee-110">选择输入数据</span><span class="sxs-lookup"><span data-stu-id="163ee-110">Choosing the Input Data</span></span>  
 <span data-ttu-id="163ee-111">测试挖掘模型准确性的第一步是选择将用于测试的数据源。</span><span class="sxs-lookup"><span data-stu-id="163ee-111">The first step in testing the accuracy of your mining models is to select the data source that you will use for testing.</span></span> <span data-ttu-id="163ee-112">您将根据测试数据测试模型的准确性，然后将它们与外部数据一起使用。</span><span class="sxs-lookup"><span data-stu-id="163ee-112">You will test how well the models perform against your testing data and then you will use them with external data.</span></span>  
  
#### <a name="to-select-the-data-set"></a><span data-ttu-id="163ee-113">选择数据集</span><span class="sxs-lookup"><span data-stu-id="163ee-113">To select the data set</span></span>  
  
1.  <span data-ttu-id="163ee-114">切换到数据挖掘设计器中的 "**挖掘准确性图表**" 选项卡 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ，然后选择 "**输入选择**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="163ee-114">Switch to the **Mining Accuracy Chart** tab in Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] and select the **Input Selection** tab.</span></span>  
  
2.  <span data-ttu-id="163ee-115">在 "**选择要用于准确性图表的数据集**" 组框中，选择 "**使用挖掘结构测试事例**"。</span><span class="sxs-lookup"><span data-stu-id="163ee-115">In the **Select data set to be used for Accuracy Chart** group box, select **Use mining structure test cases**.</span></span> <span data-ttu-id="163ee-116">这是当您创建挖掘结构时留出的测试数据。</span><span class="sxs-lookup"><span data-stu-id="163ee-116">This is the testing data that you set aside when you created the mining structure.</span></span>  
  
     <span data-ttu-id="163ee-117">有关其他选项的详细信息，请参阅[选择准确性图表类型和设置图表选项](../../2014/analysis-services/data-mining/choose-an-accuracy-chart-type-and-set-chart-options.md)。</span><span class="sxs-lookup"><span data-stu-id="163ee-117">For more information on the other options, see [Choose an Accuracy Chart Type and Set Chart Options](../../2014/analysis-services/data-mining/choose-an-accuracy-chart-type-and-set-chart-options.md).</span></span>  
  
##  <a name="setting-accuracy-chart-parameters"></a><a name="BKMK_Selecting"></a><span data-ttu-id="163ee-118">设置准确性图表参数</span><span class="sxs-lookup"><span data-stu-id="163ee-118">Setting Accuracy Chart Parameters</span></span>  
 <span data-ttu-id="163ee-119">若要创建准确性图表，必须定义三个内容：</span><span class="sxs-lookup"><span data-stu-id="163ee-119">To create an accuracy chart, you must define three things:</span></span>  
  
-   <span data-ttu-id="163ee-120">应在准确性图表中包含哪些模型？</span><span class="sxs-lookup"><span data-stu-id="163ee-120">Which models should you include in the accuracy chart?</span></span>  
  
-   <span data-ttu-id="163ee-121">您希望测量哪个可预测的属性？</span><span class="sxs-lookup"><span data-stu-id="163ee-121">Which predictable attribute do you want to measure?</span></span> <span data-ttu-id="163ee-122">一些模型可能有多个目标，但是每个图表一次只能测量一个结果。</span><span class="sxs-lookup"><span data-stu-id="163ee-122">Some models might have multiple targets, but each chart can measure only one outcome at a time.</span></span>  
  
     <span data-ttu-id="163ee-123">若要使用列作为准确性图表中的**可预测列名称**，则这些列的使用类型必须为 `Predict` 或 `Predict Only` 。</span><span class="sxs-lookup"><span data-stu-id="163ee-123">To use a column as the **Predictable Column Name** in an accuracy chart, the columns must have the usage type of `Predict` or `Predict Only`.</span></span> <span data-ttu-id="163ee-124">此外，目标列的内容类型必须为 `Discrete` 或 `Discretized`。</span><span class="sxs-lookup"><span data-stu-id="163ee-124">Also, the content type of the target column must be either `Discrete` or `Discretized`.</span></span> <span data-ttu-id="163ee-125">换言之，您无法使用提升图针对连续数值输出测量准确性。</span><span class="sxs-lookup"><span data-stu-id="163ee-125">In other words, you cannot measure accuracy against continuous numeric outputs using the lift chart.</span></span>  
  
-   <span data-ttu-id="163ee-126">您是要衡量模型的一般准确性，还是在预测特定值 (如 [自行车买家] = ' Yes ' ) </span><span class="sxs-lookup"><span data-stu-id="163ee-126">Do you want to measure the model's general accuracy, or its accuracy  in predicting a particular value (such as [Bike Buyer] = 'Yes')</span></span>  
  
#### <a name="to-generate-the-lift-chart"></a><span data-ttu-id="163ee-127">生成提升图</span><span class="sxs-lookup"><span data-stu-id="163ee-127">To generate the lift chart</span></span>  
  
1.  <span data-ttu-id="163ee-128">在数据挖掘设计器的 "**输入选择**" 选项卡上，在 "**选择要在提升图中显示的可预测的挖掘模型列**" 下，选中 "**同步预测列和值**" 复选框。</span><span class="sxs-lookup"><span data-stu-id="163ee-128">On the **Input Selection** tab of Data Mining Designer, under **Select predictable mining model columns to show in the lift chart**, select the checkbox for **Synchronize Prediction Columns and Values**.</span></span>  
  
2.  <span data-ttu-id="163ee-129">在 "**可预测列名称**" 列中，验证是否为每个模型选择了 "**自行车购买**者"。</span><span class="sxs-lookup"><span data-stu-id="163ee-129">In the **Predictable Column Name** column, verify that **Bike Buyer** is selected for each model.</span></span>  
  
3.  <span data-ttu-id="163ee-130">在 "**显示**" 列中，选择每个模型。</span><span class="sxs-lookup"><span data-stu-id="163ee-130">In the **Show** column, select each of the models.</span></span>  
  
     <span data-ttu-id="163ee-131">默认情况下，系统会选中挖掘结构中的所有模型。</span><span class="sxs-lookup"><span data-stu-id="163ee-131">By default, all the models in the mining structure are selected.</span></span> <span data-ttu-id="163ee-132">可以决定不包含某一模型，但对于本教程，请选中所有模型。</span><span class="sxs-lookup"><span data-stu-id="163ee-132">You can decide not to include a model, but for this tutorial leave all the models selected.</span></span>  
  
4.  <span data-ttu-id="163ee-133">在 "**预测值**" 列中，选择**1**。</span><span class="sxs-lookup"><span data-stu-id="163ee-133">In the **Predict Value** column, select **1**.</span></span> <span data-ttu-id="163ee-134">对于具有相同可预测列的每个模型，将自动填充相同的值。</span><span class="sxs-lookup"><span data-stu-id="163ee-134">The same value is automatically filled in for each model that has the same predictable column.</span></span>  
  
5.  <span data-ttu-id="163ee-135">选择 "**提升图**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="163ee-135">Select the **Lift Chart** tab.</span></span>  
  
     <span data-ttu-id="163ee-136">当您单击该选项卡时，将执行一个预测查询以获取测试数据的预测结果，并针对已知值比较这些结果。</span><span class="sxs-lookup"><span data-stu-id="163ee-136">When you click the tab, a prediction query is executed to get predictions for the test data, and the results are compared against the known values.</span></span> <span data-ttu-id="163ee-137">结果将绘制在图上。</span><span class="sxs-lookup"><span data-stu-id="163ee-137">The results are plotted on the graph.</span></span>  
  
     <span data-ttu-id="163ee-138">如果使用 "**预测值**" 选项指定了特定目标结果，则提升图会绘制随机推测的结果和理想模型的结果。</span><span class="sxs-lookup"><span data-stu-id="163ee-138">If you specified a particular target outcome using the **Predict Value** option, the lift chart plots the results of random guesses and the results of an ideal model.</span></span>  
  
    -   <span data-ttu-id="163ee-139">随机猜测线显示没有使用任何数据进行预测时模型的准确程度：即两个结果之间的 50-50 拆分。</span><span class="sxs-lookup"><span data-stu-id="163ee-139">The random guess line shows how accurate the model would be without using any data to inform its predictions: that is, a 50-50 split between two outcomes.</span></span> <span data-ttu-id="163ee-140">提升图帮助您可视化模型在与随机猜测进行比较时结果获得改进的程度。</span><span class="sxs-lookup"><span data-stu-id="163ee-140">The lift chart helps you visualize how much better your model performs in comparison to a random guess.</span></span>  
  
    -   <span data-ttu-id="163ee-141">理想模型线表示准确性的上限。</span><span class="sxs-lookup"><span data-stu-id="163ee-141">The ideal model line represents the upper bound of accuracy.</span></span> <span data-ttu-id="163ee-142">它显示如果您的模型始终预测准确可能获得的最大好处。</span><span class="sxs-lookup"><span data-stu-id="163ee-142">It shows you the maximum possible benefit you could achieve if your model always predicted accurately.</span></span>  
  
     <span data-ttu-id="163ee-143">您创建的挖掘模型通常将处于这两种极限情况之间。</span><span class="sxs-lookup"><span data-stu-id="163ee-143">The mining models you created will usually fall between these two extremes.</span></span> <span data-ttu-id="163ee-144">随机推测的任何改进都被视为*提升*。</span><span class="sxs-lookup"><span data-stu-id="163ee-144">Any improvement from the random guess is considered to be *lift*.</span></span>  
  
6.  <span data-ttu-id="163ee-145">使用图例可以查找表示理想模型和随机推测模型的彩色线。</span><span class="sxs-lookup"><span data-stu-id="163ee-145">Use the legend to locate the colored lines representing the Ideal Model and the Random Guess Model.</span></span>  
  
     <span data-ttu-id="163ee-146">你会注意到 `TM_Decision_Tree` ，模型提供了最大的提升，同时遥遥领先远远了聚类分析和 Naive Bayes 模型。</span><span class="sxs-lookup"><span data-stu-id="163ee-146">You'll notice that the `TM_Decision_Tree` model provides the greatest lift,  outperforming both the Clustering and Naive Bayes models.</span></span>  
  
 <span data-ttu-id="163ee-147">有关与在本课中创建的提升图类似的提升图的详细说明，请参阅[提升图 &#40;Analysis Services-数据挖掘&#41;](../../2014/analysis-services/data-mining/lift-chart-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="163ee-147">For an in-depth explanation of a lift chart similar to the one created in this lesson, see [Lift Chart &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/lift-chart-analysis-services-data-mining.md).</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="163ee-148">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="163ee-148">Next Task in Lesson</span></span>  
 [<span data-ttu-id="163ee-149">&#40;数据挖掘基础教程中测试筛选的模型&#41;</span><span class="sxs-lookup"><span data-stu-id="163ee-149">Testing a Filtered Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/testing-a-filtered-model-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="163ee-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="163ee-150">See Also</span></span>  
 <span data-ttu-id="163ee-151">[Analysis Services &#40;提升图表&#41;](../../2014/analysis-services/data-mining/lift-chart-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="163ee-151">[Lift Chart &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/lift-chart-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="163ee-152">"提升图" 选项卡 &#40;挖掘准确性图表视图&#41;</span><span class="sxs-lookup"><span data-stu-id="163ee-152">Lift Chart Tab &#40;Mining Accuracy Chart View&#41;</span></span>](../../2014/analysis-services/lift-chart-tab-mining-accuracy-chart-view.md)  
  
  
