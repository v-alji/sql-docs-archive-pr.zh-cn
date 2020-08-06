---
title: "\"输入选择\" 选项卡 (挖掘准确性图表视图) |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.accuracychart.columnmapping.f1
ms.assetid: f8b1193c-5c86-4c7e-8e35-158d293184fa
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3c5e99e5be275dff6e218d172316c612b5ba0c41
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587103"
---
# <a name="input-selection-tab-mining-accuracy-chart-view"></a><span data-ttu-id="897f0-102">“输入选择”选项卡（“挖掘准确性图表”视图）</span><span class="sxs-lookup"><span data-stu-id="897f0-102">Input Selection Tab (Mining Accuracy Chart View)</span></span>
  <span data-ttu-id="897f0-103">可以使用 **“挖掘准确性图表”** 设计器的 **“输入选择”** 选项卡，指定用于测试模型和生成准确性图表的数据源。</span><span class="sxs-lookup"><span data-stu-id="897f0-103">Use the **Input Selection** tab of the **Mining Accuracy Chart** designer to specify the source of the data that is used to test the model and build the accuracy chart.</span></span>  
  
 <span data-ttu-id="897f0-104">**有关详细信息，请参阅** [测试和验证（数据挖掘）](data-mining/testing-and-validation-data-mining.md)</span><span class="sxs-lookup"><span data-stu-id="897f0-104">**For more information:** [Testing and Validation &#40;Data Mining&#41;](data-mining/testing-and-validation-data-mining.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="897f0-105">选项</span><span class="sxs-lookup"><span data-stu-id="897f0-105">Options</span></span>  
 <span data-ttu-id="897f0-106">**同步预测**  **列和值**</span><span class="sxs-lookup"><span data-stu-id="897f0-106">**Synchronize Prediction**  **Columns and Values**</span></span>  
 <span data-ttu-id="897f0-107">选中此项可以协调网格中的可预测属性，这样在模型定型期间，即使这些属性具有不同名称，也会从相同的可预测挖掘结构列中派生。</span><span class="sxs-lookup"><span data-stu-id="897f0-107">Select to coordinate the predictable attributes in the grid so that, even if they have a different name, they are derived from the same predictable mining structure column during model training.</span></span>  
  
 <span data-ttu-id="897f0-108">**注意** 默认情况下此选项处于选中状态。</span><span class="sxs-lookup"><span data-stu-id="897f0-108">**Note** This option is selected by default.</span></span> <span data-ttu-id="897f0-109">只有在您知道两个挖掘结构列派生自同一基础关系源或多维源并且这两列包含相同的状态或具有相同的离散程度时，才可清除此框。</span><span class="sxs-lookup"><span data-stu-id="897f0-109">You should only clear this box for cases in which you know that two mining structure columns derive from the same underlying relational or multi-dimensional source, and that the columns contain the same states or have been discretized in the same way.</span></span>  
  
 <span data-ttu-id="897f0-110">**选择要在提升图中显示的可预测的挖掘模型列**</span><span class="sxs-lookup"><span data-stu-id="897f0-110">**Select predictable mining model columns to show in the lift chart**</span></span>  
 <span data-ttu-id="897f0-111">包含的列用于控制提升图中包括的模型以及提升图使用这些模型的方式的网格。</span><span class="sxs-lookup"><span data-stu-id="897f0-111">A grid that contains columns to control which models are included in the lift chart and how they are used in the lift chart.</span></span>  
  
|<span data-ttu-id="897f0-112">值</span><span class="sxs-lookup"><span data-stu-id="897f0-112">Value</span></span>|<span data-ttu-id="897f0-113">说明</span><span class="sxs-lookup"><span data-stu-id="897f0-113">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="897f0-114">**显示**</span><span class="sxs-lookup"><span data-stu-id="897f0-114">**Show**</span></span>|<span data-ttu-id="897f0-115">选中要在图表中显示的挖掘模型中每个可预测列名称旁边的框。</span><span class="sxs-lookup"><span data-stu-id="897f0-115">Select the box next to the name of each predictable column in the mining model that you want to display in the chart.</span></span><br /><br /> <span data-ttu-id="897f0-116">如果图表因过于复杂而不便查看，请清除一列或多列旁边的框以简化该图表。</span><span class="sxs-lookup"><span data-stu-id="897f0-116">If the chart is too complex to view easily, clear the box next to one or more columns to simplify the chart.</span></span><br /><br /> <span data-ttu-id="897f0-117">注意：至少应选择一列，否则无法创建准确性图表。</span><span class="sxs-lookup"><span data-stu-id="897f0-117">Note: You cannot create an accuracy chart unless at least one column is selected.</span></span>|  
|<span data-ttu-id="897f0-118">**挖掘模型**</span><span class="sxs-lookup"><span data-stu-id="897f0-118">**Mining Model**</span></span>|<span data-ttu-id="897f0-119">列出挖掘结构中包含的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="897f0-119">Lists the mining models that are contained in the mining structure.</span></span>|  
|<span data-ttu-id="897f0-120">**可预测的列名**</span><span class="sxs-lookup"><span data-stu-id="897f0-120">**Predictable Column Name**</span></span>|<span data-ttu-id="897f0-121">选择用于创建提升图的挖掘模型中包含的可预测列。</span><span class="sxs-lookup"><span data-stu-id="897f0-121">Select a predictable column that is contained in the mining models that are used to create the lift chart.</span></span>|  
|<span data-ttu-id="897f0-122">**预测值**</span><span class="sxs-lookup"><span data-stu-id="897f0-122">**Predict Value**</span></span>|<span data-ttu-id="897f0-123">为可预测列选择值。</span><span class="sxs-lookup"><span data-stu-id="897f0-123">Select a value for the predictable column.</span></span> <span data-ttu-id="897f0-124">如果保留此项为空白，则提升图将预测模型对于可预测列的所有状态的执行性能。</span><span class="sxs-lookup"><span data-stu-id="897f0-124">If you leave this blank, the lift chart predicts how well the model performs for all states of the predictable column.</span></span>|  
  
 <span data-ttu-id="897f0-125">**选择要用于准确性图表的数据集**</span><span class="sxs-lookup"><span data-stu-id="897f0-125">**Select data set to be used for Accuracy Chart**</span></span>  
 <span data-ttu-id="897f0-126">其中包含用于指定准确性测试数据的三个选项的选项组。</span><span class="sxs-lookup"><span data-stu-id="897f0-126">An option group that contains three options for specifying accuracy test data.</span></span>  
  
|<span data-ttu-id="897f0-127">值</span><span class="sxs-lookup"><span data-stu-id="897f0-127">Value</span></span>|<span data-ttu-id="897f0-128">说明</span><span class="sxs-lookup"><span data-stu-id="897f0-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="897f0-129">**使用挖掘模型测试事例**</span><span class="sxs-lookup"><span data-stu-id="897f0-129">**Use mining model test cases**</span></span>|<span data-ttu-id="897f0-130">使用在对挖掘结构进行分区时创建的测试集，并应用为模型定义的筛选器。</span><span class="sxs-lookup"><span data-stu-id="897f0-130">Use the testing set that was created when you partitioned the mining structure, and apply the filter that is defined on the model.</span></span> <span data-ttu-id="897f0-131">有关模型筛选器的信息，请参阅 [Filters for Mining Models &#40;Analysis Services - Data Mining&#41;](data-mining/mining-models-analysis-services-data-mining.md)</span><span class="sxs-lookup"><span data-stu-id="897f0-131">For information about model filters, see [Filters for Mining Models &#40;Analysis Services - Data Mining&#41;](data-mining/mining-models-analysis-services-data-mining.md)</span></span>|  
|<span data-ttu-id="897f0-132">**使用挖掘结构测试事例**</span><span class="sxs-lookup"><span data-stu-id="897f0-132">**Use mining structure test cases**</span></span>|<span data-ttu-id="897f0-133">使用在对挖掘结构进行分区时创建的测试集。</span><span class="sxs-lookup"><span data-stu-id="897f0-133">Use the testing set that was created when you partitioned the mining structure.</span></span>|  
|<span data-ttu-id="897f0-134">**指定其他数据集**</span><span class="sxs-lookup"><span data-stu-id="897f0-134">**Specify a different data set**</span></span>|<span data-ttu-id="897f0-135">从现有数据源视图中指定要用作测试数据集的表。</span><span class="sxs-lookup"><span data-stu-id="897f0-135">Specify a table from an existing data source view to use as a test data set.</span></span>|  
  
## <a name="filtering-options"></a><span data-ttu-id="897f0-136">筛选选项</span><span class="sxs-lookup"><span data-stu-id="897f0-136">Filtering Options</span></span>  
 <span data-ttu-id="897f0-137">如果选择选项 **“指定其他数据集”**，则可以定义数据源视图并创建要应用于这些数据的筛选器。</span><span class="sxs-lookup"><span data-stu-id="897f0-137">If you select the option **Specify a different data set**, you can define a data source view and create filters to apply to that data.</span></span> <span data-ttu-id="897f0-138">创建筛选器时，您将在从数据源视图返回测试数据的查询中创建 WHERE 子句。</span><span class="sxs-lookup"><span data-stu-id="897f0-138">When you create a filter, you are creating a WHERE clause in the query that returns the test data from the data source view.</span></span>  
  
 <span data-ttu-id="897f0-139">**注意**不能通过使用 "**输入选择**" 选项卡为挖掘模型指定筛选器。若要创建模型筛选器，请单击 "**挖掘模型**" 选项卡，然后编辑模型属性。</span><span class="sxs-lookup"><span data-stu-id="897f0-139">**Note** You cannot specify a filter on the mining model by using the **Input Selection** tab. To create a model filter, click the **Mining Models** tab and edit the model properties.</span></span>  
  
 <span data-ttu-id="897f0-140">如果创建挖掘模型时未创建用于测试的维持集，则可以选择此选项并将原始数据源视图指定为测试集。</span><span class="sxs-lookup"><span data-stu-id="897f0-140">If you did not create a holdout set for testing when you created the mining structure, you can select this option and then specify the original data source view as a test set.</span></span> <span data-ttu-id="897f0-141">通过使用此解决方法，您还可以设置原始数据集的筛选器。</span><span class="sxs-lookup"><span data-stu-id="897f0-141">By using  this workaround, you can also set filters on the original data set.</span></span>  
  
 <span data-ttu-id="897f0-142">**指定列映射**</span><span class="sxs-lookup"><span data-stu-id="897f0-142">**Specify Column Mapping**</span></span>  
 <span data-ttu-id="897f0-143">打开“指定列映射”\*\*\*\* 对话框，在其中可以选择数据源、指定事例表和嵌套表以及将外部数据列映射到挖掘结构列。</span><span class="sxs-lookup"><span data-stu-id="897f0-143">Opens the **Specify Column Mapping** dialog box, where you select the data source, specify case and nested tables, and map external data columns to the mining structure columns.</span></span>  
  
 <span data-ttu-id="897f0-144">有关详细信息，请参阅[“指定列映射”对话框（挖掘准确性图表）](specify-column-mapping-dialog-box-mining-accuracy-chart.md)。</span><span class="sxs-lookup"><span data-stu-id="897f0-144">For more information, see [Specify Column Mapping Dialog Box &#40;Mining Accuracy Chart&#41;](specify-column-mapping-dialog-box-mining-accuracy-chart.md).</span></span>  
  
 <span data-ttu-id="897f0-145">**筛选表达式**</span><span class="sxs-lookup"><span data-stu-id="897f0-145">**Filter Expression**</span></span>  
 <span data-ttu-id="897f0-146">显示使用筛选器编辑器生成的筛选条件。</span><span class="sxs-lookup"><span data-stu-id="897f0-146">Displays the filter condition that you built by using the filter editors.</span></span>  
  
 <span data-ttu-id="897f0-147">**打开筛选器编辑器**</span><span class="sxs-lookup"><span data-stu-id="897f0-147">**Open Filter Editor**</span></span>  
 <span data-ttu-id="897f0-148">打开“数据集筛选器”\*\*\*\* 对话框（使用该对话框可以选择外部表并对事例表列设置条件）和“筛选器”\*\*\*\* 对话框（该对话框可帮助你生成应用于所选表中各个列或应用于嵌套表中的列的条件）。</span><span class="sxs-lookup"><span data-stu-id="897f0-148">Opens the **Data Set Filter** dialog box, which lets you select external tables, and set conditions on case table columns, and the **Filter** dialog box, which helps you build conditions that apply to individual columns in the selected table, or to columns in nested tables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="897f0-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="897f0-149">See Also</span></span>  
 <span data-ttu-id="897f0-150">[测试和验证任务以及操作方法 &#40;数据挖掘&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="897f0-150">[Testing and Validation Tasks and How-tos &#40;Data Mining&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span></span>  
 <span data-ttu-id="897f0-151">[挖掘准确性图表设计器 &#40;数据挖掘&#41;](mining-accuracy-chart-designer-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="897f0-151">[Mining Accuracy Chart Designer &#40;Data Mining&#41;](mining-accuracy-chart-designer-data-mining.md) </span></span>  
 <span data-ttu-id="897f0-152">[对挖掘模型应用筛选器](data-mining/apply-a-filter-to-a-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="897f0-152">[Apply a Filter to a Mining Model](data-mining/apply-a-filter-to-a-mining-model.md) </span></span>  
 [<span data-ttu-id="897f0-153">挖掘模型的筛选器（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="897f0-153">Filters for Mining Models &#40;Analysis Services - Data Mining&#41;</span></span>](data-mining/mining-models-analysis-services-data-mining.md)  
  
  
