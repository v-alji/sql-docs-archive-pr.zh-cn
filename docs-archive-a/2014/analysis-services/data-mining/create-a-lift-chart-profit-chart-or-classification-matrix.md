---
title: 创建提升图、利润图或分类矩阵 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Mining Accuracy Chart [Analysis Services], mining structures
ms.assetid: aa3d052f-58a9-4417-8e7a-5e6feb562af0
author: minewiskan
ms.author: owend
ms.openlocfilehash: 932138b37b36269bed86df42786bd5d684f75ee9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687375"
---
# <a name="create-a-lift-chart-profit-chart-or-classification-matrix"></a><span data-ttu-id="bbcd0-102">创建提升图、利润图或分类矩阵</span><span class="sxs-lookup"><span data-stu-id="bbcd0-102">Create a Lift Chart, Profit Chart, or Classification Matrix</span></span>
  <span data-ttu-id="bbcd0-103">可以使用五个基本步骤为 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据挖掘模型创建准确性图表：</span><span class="sxs-lookup"><span data-stu-id="bbcd0-103">You can create an accuracy chart for an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] data mining model in five basic steps:</span></span>  
  
-   <span data-ttu-id="bbcd0-104">选择包含要比较的挖掘模型的挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-104">Select the mining structure that contains the mining models that you want to compare.</span></span>  
  
-   <span data-ttu-id="bbcd0-105">选择要添加到图表中的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-105">Select the mining models to add to the chart.</span></span>  
  
-   <span data-ttu-id="bbcd0-106">指定要在生成图表的过程中使用的测试数据的源。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-106">Specify a source of testing data to use in generating the chart.</span></span>  
  
-   <span data-ttu-id="bbcd0-107">选择图表类型。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-107">Choose the chart type.</span></span>  
  
-   <span data-ttu-id="bbcd0-108">配置图表选项。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-108">Configure the chart options.</span></span>  
  
 <span data-ttu-id="bbcd0-109">对于提升图、利润图和分类矩阵而言，这些基本步骤是相同的。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-109">These basic steps are the same for the lift chart, profit chart, and classification matrix.</span></span> <span data-ttu-id="bbcd0-110">下面的过程概述了为这些图表类型配置基本图表选项的步骤。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-110">The following procedures outline the steps to configure the basic chart options for these chart types.</span></span> <span data-ttu-id="bbcd0-111">有关如何创建交叉验证报表的信息，请参阅 [交叉验证报表中的度量值](measures-in-the-cross-validation-report.md)。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-111">For information about how to create a cross-validation report, see [Measures in the Cross-Validation Report](measures-in-the-cross-validation-report.md).</span></span>  
  
### <a name="open-the-mining-structure-in-the-accuracy-chart-designer"></a><span data-ttu-id="bbcd0-112">在准确性图表设计器中打开挖掘结构</span><span class="sxs-lookup"><span data-stu-id="bbcd0-112">Open the mining structure in the Accuracy Chart Designer</span></span>  
  
1.  <span data-ttu-id="bbcd0-113">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中打开数据挖掘设计器。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-113">Open the Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="bbcd0-114">在解决方案资源管理器中，双击包含挖掘模型的结构。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-114">In Solution Explorer, double-click the structure that contains the mining model or models.</span></span>  
  
3.  <span data-ttu-id="bbcd0-115">单击 **“挖掘准确性图表”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-115">Click the **Mining Accuracy Chart** tab.</span></span>  
  
### <a name="select-mining-models-for-inclusion-in-the-chart"></a><span data-ttu-id="bbcd0-116">选择要包括在图表中的挖掘模型</span><span class="sxs-lookup"><span data-stu-id="bbcd0-116">Select mining models for inclusion in the chart</span></span>  
  
1.  <span data-ttu-id="bbcd0-117">在 **中的数据挖掘设计器的** “挖掘准确性图表” [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]选项卡上，单击 **“输入选择”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-117">On the **Mining Accuracy Chart** tab of Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click the **Input Selection** tab.</span></span>  
  
     <span data-ttu-id="bbcd0-118">其中的列表显示了当前结构中具有相同可预测属性的所有模型。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-118">The list displays all models in the current structure that have the same predictable attribute.</span></span>  
  
2.  <span data-ttu-id="bbcd0-119">对要包括在图表中的每个模型选中 **“显示”** 框。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-119">Select the **Show box** for each model that you want to include in the chart.</span></span>  
  
3.  <span data-ttu-id="bbcd0-120">单击 **“可预测列名称”** 文本框，从列表中选择可预测列的名称。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-120">Click the **Predictable Column Name** text box, and select the name of a predictable column from the list.</span></span> <span data-ttu-id="bbcd0-121">放入一个图表中的所有模型都必须具有相同的可预测列。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-121">All models that you put in one chart must have the same predictable column.</span></span>  
  
4.  <span data-ttu-id="bbcd0-122">如果您比较两个模型，但其可预测列具有不同的值或不同的数据类型，则应清除 **“同步预测列和值”** 框以强制进行比较。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-122">If you compare two models and the predictable columns have different values or different data types, clear the **Synchonize prediction columns and values** box to force a comparison.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="bbcd0-123">如果选中了 **“同步预测列和值”** 框，则 Analysis Services 会分析模型的可预测列中的数据和测试数据，并尝试找到最佳匹配项。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-123">If the **Synchonize prediction columns and values** box is selected, Analysis Services analyzes the data in the predictable columns of the model and the test data, and attempts to find the best match.</span></span> <span data-ttu-id="bbcd0-124">因此，除非绝对需要强制进行列的比较，否则不要清除此框。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-124">Therefore, do not clear the box unless absolutely necessary to force a comparison of the columns.</span></span>  
  
5.  <span data-ttu-id="bbcd0-125">单击 **“预测值”** 文本框，并从列表中选择一个值。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-125">Click the **Predict Value** text box, and select a value from the list.</span></span> <span data-ttu-id="bbcd0-126">如果可预测列是连续数据类型，则必须在此文本框中键入一个值。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-126">If the predictable column is a continuous data type, you must type a value in the text box.</span></span>  
  
     <span data-ttu-id="bbcd0-127">有关详细信息，请参阅 [选择用于测试挖掘模型的列](choose-the-column-to-use-for-testing-a-mining-model.md)。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-127">For more information, see [Choose the Column to Use for Testing a Mining Model](choose-the-column-to-use-for-testing-a-mining-model.md).</span></span>  
  
### <a name="select-testing-data"></a><span data-ttu-id="bbcd0-128">选择测试数据</span><span class="sxs-lookup"><span data-stu-id="bbcd0-128">Select testing data</span></span>  
  
1.  <span data-ttu-id="bbcd0-129">在 **“挖掘准确性图表”** 选项卡的 **“输入选择”** 选项卡上，通过选择 **“选择要用于准确性图表的数据集”** 组中的一个选项来指定将用来生成图表的数据源。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-129">On the **Input Selection** tab of the **Mining Accuracy Chart** tab, specify the source of the data that you will use to generate the chart by selecting one of the options in the group, **Select data set to be used for accuracy chart**.</span></span>  
  
    -   <span data-ttu-id="bbcd0-130">如果您想要使用挖掘结构测试事例和在模型创建期间可能已应用的任何筛选器的交集定义的事例的子级，则选择选项 **“使用挖掘模型测试事例”**。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-130">Select the option, **Use Mining Model test cases**, if you want to use the subset of cases that is defined by the intersection of the mining structure test cases and any filters that may have been applied during model creation.</span></span>  
  
    -   <span data-ttu-id="bbcd0-131">选择 **“使用挖掘结构测试事例”** 选项可以使用已作为挖掘结构维持数据集的一部分定义的测试事例的完整集合。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-131">Select the option, **Use mining structure test cases**, to use the full set of testing cases that were defined as part of the mining structures holdout data set.</span></span>  
  
    -   <span data-ttu-id="bbcd0-132">若要使用外部数据，请选择“指定其他数据集”选项。 \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="bbcd0-132">Select the option, **Specify a different data set**, if you want to use external data.</span></span>  <span data-ttu-id="bbcd0-133">数据集必须可用作数据源视图。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-133">The data set must be available as a data source view.</span></span>   <span data-ttu-id="bbcd0-134">单击 "浏览 (**...** ") 按钮，选择要用于准确性图表的数据表。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-134">Click the browse (**...**) button to choose the data tables to use for the accuracy chart.</span></span> <span data-ttu-id="bbcd0-135">有关详细信息，请参阅 [Choose and Map Model Testing Data](choose-and-map-model-testing-data.md)。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-135">For more information, see [Choose and Map Model Testing Data](choose-and-map-model-testing-data.md).</span></span>  
  
         <span data-ttu-id="bbcd0-136">如果您使用的是外部数据集，则可以选择筛选输入数据集。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-136">If you are using an external data set, you can optionally filter the input data set.</span></span> <span data-ttu-id="bbcd0-137">有关详细信息，请参阅 [将筛选器应用于模型测试数据](apply-filters-to-model-testing-data.md)。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-137">For more information, see [Apply Filters to Model Testing Data](apply-filters-to-model-testing-data.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bbcd0-138">不能在 "**输入选择**" 选项卡上的模型测试事例或挖掘结构测试事例上创建筛选器。若要在挖掘模型上创建筛选器，请修改该模型的 "筛选器" 属性。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-138">You cannot create a filter on the model test cases or the mining structure test cases on the **Input Selection** tab. To create a filter on the mining model, modify the Filter property of the model.</span></span> <span data-ttu-id="bbcd0-139">有关详细信息，请参阅 [对挖掘模型应用筛选器](apply-a-filter-to-a-mining-model.md)。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-139">For more information, see [Apply a Filter to a Mining Model](apply-a-filter-to-a-mining-model.md).</span></span>  
  
### <a name="configure-chart-settings-and-generate-the-chart"></a><span data-ttu-id="bbcd0-140">配置图表设置并生成图表</span><span class="sxs-lookup"><span data-stu-id="bbcd0-140">Configure chart settings and generate the chart</span></span>  
  
1.  <span data-ttu-id="bbcd0-141">在 **“挖掘准确性图表”** 选项卡中，单击要创建的图表的对应选项卡。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-141">In the **Mining Accuracy Chart** tab, click the tab for the chart you want to create.</span></span>  
  
2.  <span data-ttu-id="bbcd0-142">对于**提升图**，请单击 "**提升图**" 选项卡。图表是根据模型、可预测属性以及您刚选择的输入数据自动生成的。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-142">For a **lift chart**, click the **Lift Chart** tab. The chart is automatically generated based on the model, predictable attributes, and input data that you just selected.</span></span>  
  
3.  <span data-ttu-id="bbcd0-143">对于**分类矩阵**，请单击 "**分类矩阵**" 选项卡。无需进一步的设置;将根据您选择的输入数据和模型自动生成图表。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-143">For a **classification matrix**, click the **Classification Matrix** tab. No further settings are needed; the chart is automatically generated based on the input data and model that you selected.</span></span>  
  
4.  <span data-ttu-id="bbcd0-144">对于**利润图**，请首先单击 "**提升图**" 选项卡。然后，从 "**图表类型**" 下拉列表中选择 "**利润图**"。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-144">For a **profit chart**, first click the **Lift Chart** tab. Then, from the **Chart type** drop-down list, select **Profit chart**.</span></span>  
  
     <span data-ttu-id="bbcd0-145">在 **“利润图设置”** 对话框中输入以下设置。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-145">Enter the following settings in the **Profit Chart Settings** dialog box.</span></span>  
  
     <span data-ttu-id="bbcd0-146">**总数**</span><span class="sxs-lookup"><span data-stu-id="bbcd0-146">**Population**</span></span>  
     <span data-ttu-id="bbcd0-147">创建提升图时要使用的数据集中的事例数。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-147">The number of cases from the data set that you want to use when creating the lift chart.</span></span>  
  
     <span data-ttu-id="bbcd0-148">该模型总是按概率降低的顺序选择事例，也就是说，如果正在评估潜在客户并且选择的数字仅表示客户数据库中记录数的一半，则该模型将在最适合于您的模型的事例子集上度量准确性。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-148">The model always chooses the cases in order of decreasing probability; that is, if you are assessing potential customers and you choose a number that represents only half the records in your customer database, the model will measure accuracy on the subset of cases that best fit your model.</span></span>  
  
     <span data-ttu-id="bbcd0-149">这是因为当使用该模型生成邮件或者创建活动时，将使用与每个事例关联的预测概率，以仅针对做出积极响应的概率最大的那些客户。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-149">This is because when you use the model to generate a mailing or create a campaign, you will use the prediction probability associated with each case to target only the customers who have the highest probability of making a positive response.</span></span>  
  
     <span data-ttu-id="bbcd0-150">**固定成本**</span><span class="sxs-lookup"><span data-stu-id="bbcd0-150">**Fixed Cost**</span></span>  
     <span data-ttu-id="bbcd0-151">与业务问题关联的固定成本。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-151">The fixed cost that is associated with the business problem.</span></span>  
  
     <span data-ttu-id="bbcd0-152">如果针对的是目标邮递解决方案，则固定成本可能表示打印机设置费用，其中包含准备促销邮件的初始成本。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-152">If this were for a targeted mailing solution, the fixed cost might represent a printer setup fee that covers the initial cost of preparing the promotional mailing.</span></span>  
  
     <span data-ttu-id="bbcd0-153">此成本一次性应用于整个目标总体。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-153">This cost applies one time to the entire target population.</span></span>  
  
     <span data-ttu-id="bbcd0-154">**单项成本**</span><span class="sxs-lookup"><span data-stu-id="bbcd0-154">**Individual Cost**</span></span>  
     <span data-ttu-id="bbcd0-155">除固定成本之外的成本，可以与每个客户联系相关联。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-155">Costs that are in addition to the fixed cost, that can be associated with each customer contact.</span></span> <span data-ttu-id="bbcd0-156">例如，可以输入促销邮件的邮费或者打电话的成本。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-156">For example, you might enter the postage cost for a promotional mailing or the cost of making telephone calls.</span></span>  
  
     <span data-ttu-id="bbcd0-157">此成本必须与整体目标总体相同。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-157">This cost must be the same for the entire target population.</span></span> <span data-ttu-id="bbcd0-158">每个值与目标事例数相乘。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-158">Each value is multiplied by the number of cases that are targeted.</span></span>  
  
     <span data-ttu-id="bbcd0-159">**每个人收入**</span><span class="sxs-lookup"><span data-stu-id="bbcd0-159">**Revenue Per Individual**</span></span>  
     <span data-ttu-id="bbcd0-160">与每个成功销售相关联的收入金额。</span><span class="sxs-lookup"><span data-stu-id="bbcd0-160">The amount of revenue that is associated with each successful sale.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbcd0-161">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bbcd0-161">See Also</span></span>  
 <span data-ttu-id="bbcd0-162">[Analysis Services &#40;提升图表&#41;](lift-chart-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="bbcd0-162">[Lift Chart &#40;Analysis Services - Data Mining&#41;](lift-chart-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="bbcd0-163">分类矩阵（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="bbcd0-163">Classification Matrix &#40;Analysis Services - Data Mining&#41;</span></span>](classification-matrix-analysis-services-data-mining.md)  
  
  
