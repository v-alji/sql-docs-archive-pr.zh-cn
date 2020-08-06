---
title: 将筛选器应用于模型测试数据 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- input row filtering [SQL Server]
- filtering input rows [Analysis Services]
- Mining Accuracy Chart [Analysis Services], filtering input rows
ms.assetid: 9ccc9a23-5597-4b35-a05f-2fc8eb885147
author: minewiskan
ms.author: owend
ms.openlocfilehash: d1fd2b643ae4f7d831cab980ca45b7d43d8b58f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577925"
---
# <a name="apply-filters-to-model-testing-data"></a><span data-ttu-id="f2468-102">将筛选器应用于模型测试数据</span><span class="sxs-lookup"><span data-stu-id="f2468-102">Apply Filters to Model Testing Data</span></span>
  <span data-ttu-id="f2468-103">在指定测试模型时使用的外部数据源时，可以选择应用筛选器以限制输入数据。</span><span class="sxs-lookup"><span data-stu-id="f2468-103">When you specify an external data source to use in testing a model, you can optionally apply a filter to restrict the input data.</span></span> <span data-ttu-id="f2468-104">例如，您可能想要专门针对有关某一收入范围的客户的预测来测试模型。</span><span class="sxs-lookup"><span data-stu-id="f2468-104">For example, you might want to test the model specifically for predictions on customers in a certain income range.</span></span>  
  
 <span data-ttu-id="f2468-105">例如，在 AdventureWorks 目标邮件方案中，你可以在 ProspectiveBuyer （即包含测试数据的表）上创建如下筛选器表达式，并按收入范围限制测试事例：</span><span class="sxs-lookup"><span data-stu-id="f2468-105">For example, in the AdventureWorks targeted mailing scenario, you can create a filter expression like the following one on ProspectiveBuyer, which is the table that contains the testing data, and restrict testing cases by income range:</span></span>  
  
 `[YearlyIncome] = '50000'`  
  
 <span data-ttu-id="f2468-106">根据您是在筛选定型数据还是测试数据集，筛选器的行为稍有不同：</span><span class="sxs-lookup"><span data-stu-id="f2468-106">The behavior of filters is slightly different, depending on whether you are filtering model training data or a testing data set:</span></span>  
  
-   <span data-ttu-id="f2468-107">在对测试数据集定义筛选器时，将对传入数据创建一个 WHERE 子句。</span><span class="sxs-lookup"><span data-stu-id="f2468-107">When you define a filter on a testing data set, you create a WHERE clause on the incoming data.</span></span> <span data-ttu-id="f2468-108">如果要筛选用于评估模型的输入数据集，则在创建图表时筛选表达式将转换为 Transact-SQL 语句并应用于输入表。</span><span class="sxs-lookup"><span data-stu-id="f2468-108">If you are filtering an input data set used for evaluating a model, the filter expression is translated to a Transact-SQL statement and applied to the input table when the chart is created.</span></span> <span data-ttu-id="f2468-109">结果，测试事例数会大大减少。</span><span class="sxs-lookup"><span data-stu-id="f2468-109">As a result, the number of test cases can be greatly reduced.</span></span>  
  
-   <span data-ttu-id="f2468-110">在对挖掘模型应用筛选器时，所创建的筛选表达式将转换为数据挖掘扩展插件 (DMX) 语句并应用于单个模型。</span><span class="sxs-lookup"><span data-stu-id="f2468-110">When you apply a filter to a mining model, the filter expression that you create is translated to a Data Mining Extensions (DMX) statement, and applied to the individual model.</span></span> <span data-ttu-id="f2468-111">因此，在对模型应用筛选器时，只有原始数据的子集用于定型该模型。</span><span class="sxs-lookup"><span data-stu-id="f2468-111">Therefore, when you apply a filter to a model, only a subset of the original data is used to train the model.</span></span> <span data-ttu-id="f2468-112">如果您使用一组条件筛选定型模型，以便模型优化为某一组数据，然后使用另一组条件对模型进行测试，这可能会导致问题。</span><span class="sxs-lookup"><span data-stu-id="f2468-112">This can cause problems if you filter the training model with one set of criteria, so that the model is tuned to a certain set of data, and then test the model with another set of criteria.</span></span>  
  
-   <span data-ttu-id="f2468-113">\*\*\*\* 如果创建结构时定义了测试数据集，则用于定型的模型事例将仅包括挖掘结构定型集中满足筛选条件的那些事例。</span><span class="sxs-lookup"><span data-stu-id="f2468-113">If you defined a testing data set when you created the structure, the model cases used for training include only those cases that are in the mining structure training set **and** which meet the conditions of the filter.</span></span> <span data-ttu-id="f2468-114">因此，在您测试模型并且选择 **“使用挖掘模型测试事例”** 选项时，测试事例将仅包括挖掘结构测试集中满足筛选条件的事例。</span><span class="sxs-lookup"><span data-stu-id="f2468-114">Thus, when you are testing a model and select the option **Use mining model test cases**, the testing cases will include only the cases that are in the mining structure test set and which meet the conditions of the filter.</span></span> <span data-ttu-id="f2468-115">但是，如果未定义维持数据集，用于测试的模型事例将包括该数据集中满足筛选条件的所有事例。</span><span class="sxs-lookup"><span data-stu-id="f2468-115">However, if you did not define a holdout data set, the model cases used for testing include all the cases in the data set that meet the filter conditions</span></span>  
  
-   <span data-ttu-id="f2468-116">您对模型应用的筛选条件也会影响对模型事例的钻取查询。</span><span class="sxs-lookup"><span data-stu-id="f2468-116">Filter conditions that you apply on a model also affect drillthrough queries on the model cases.</span></span>  
  
 <span data-ttu-id="f2468-117">总之，在您测试多个模型时，即使所有模型都基于相同的挖掘结构，您也必须了解这些模型可能会使用不同的数据子集来进行定型和测试。</span><span class="sxs-lookup"><span data-stu-id="f2468-117">In summary, when you test multiple models, even if all the models are based on the same mining structure, you must be aware that the models potentially use different subsets of data for training and testing.</span></span> <span data-ttu-id="f2468-118">这可能对准确性图表具有以下影响：</span><span class="sxs-lookup"><span data-stu-id="f2468-118">This can have the following effects on accuracy charts:</span></span>  
  
-   <span data-ttu-id="f2468-119">测试集中事例的总数在要测试的各模型中可能会不同。</span><span class="sxs-lookup"><span data-stu-id="f2468-119">The total number of cases in the testing sets can vary among the models being tested.</span></span>  
  
-   <span data-ttu-id="f2468-120">如果模型使用不同的定型数据或测试数据的子集，则每个模型的百分比在图表中可能不会对齐。</span><span class="sxs-lookup"><span data-stu-id="f2468-120">The percentages for each model may not align in the chart, if the models use different subsets of training data or testing data.</span></span>  
  
 <span data-ttu-id="f2468-121">为了确定某一模型是否包含可能会影响结果的预定义筛选器，您可以在 **“属性”** 窗格中查找 **Filter** 属性，或者可以通过使用数据挖掘架构行集对模型进行查询。</span><span class="sxs-lookup"><span data-stu-id="f2468-121">To determine whether a model contains a predefined filter that might affect results, you can look for the **Filter** property in the **Property** pane, or you can query the model by using the data mining schema rowsets.</span></span> <span data-ttu-id="f2468-122">例如，下面的查询将返回指定模型的筛选器文本：</span><span class="sxs-lookup"><span data-stu-id="f2468-122">For example, the following query returns the filter text for the specified model:</span></span>  
  
 `SELECT [FILTER] FROM $system.DMSCHEMA_MINING_MODELS WHERE MODEL_NAME = 'name of model'`  
  
> [!WARNING]  
>  <span data-ttu-id="f2468-123">如果您想要从现有挖掘模型中删除筛选器或更改筛选条件，则必须重新处理该挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="f2468-123">If you want to remove the filter from an existing mining model, or change the filter conditions, you must reprocess the mining model.</span></span>  
  
 <span data-ttu-id="f2468-124">有关可以应用的筛选器类型以及如何计算筛选表达式的详细信息，请参阅[模型筛选器语法和示例（Analysis Services – 数据挖掘）](model-filter-syntax-and-examples-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="f2468-124">For more information about the kinds of filters you can apply, and how filter expressions are evaluated, see [Model Filter Syntax and Examples &#40;Analysis Services - Data Mining&#41;](model-filter-syntax-and-examples-analysis-services-data-mining.md).</span></span>  
  
### <a name="create-a-filter-on-external-testing-data"></a><span data-ttu-id="f2468-125">创建针对外部测试数据的筛选器</span><span class="sxs-lookup"><span data-stu-id="f2468-125">Create a filter on external testing data</span></span>  
  
1.  <span data-ttu-id="f2468-126">双击包含您要测试的模型的挖掘结构，以便打开数据挖掘设计器。</span><span class="sxs-lookup"><span data-stu-id="f2468-126">Double-click the mining structure that contains the model you want to test, to open Data Mining Designer.</span></span>  
  
2.  <span data-ttu-id="f2468-127">选择“挖掘准确性图表” \*\*\*\* 选项卡，然后选择“输入选择” \*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="f2468-127">Select the **Mining Accuracy Chart** tab, and then select the **Input Selection** tab.</span></span>  
  
3.  <span data-ttu-id="f2468-128">在“输入选择” \*\*\*\* 选项卡的“选择要用于准确性图表的数据集” \*\*\*\* 下，选择“指定其他数据集” \*\*\*\* 选项。</span><span class="sxs-lookup"><span data-stu-id="f2468-128">On the **Input Selection** tab, under **Select data set to be used for Accuracy Chart**, select the option **Specify a different data set**.</span></span>  
  
4.  <span data-ttu-id="f2468-129">单击 "浏览" 按钮\*\* ( ... ") \*\*打开对话框并选择外部数据集。</span><span class="sxs-lookup"><span data-stu-id="f2468-129">Click the browse button **(...)** to open a dialog box and choose the external data set.</span></span>  
  
5.  <span data-ttu-id="f2468-130">选择事例表，并根据需要添加嵌套表。</span><span class="sxs-lookup"><span data-stu-id="f2468-130">Choose the case table, and add a nested table if necessary.</span></span> <span data-ttu-id="f2468-131">根据需要将模型中的列映射到外部数据集中的列。</span><span class="sxs-lookup"><span data-stu-id="f2468-131">Map columns in the model to columns in the external data set as necessary.</span></span> <span data-ttu-id="f2468-132">关闭 **“指定列映射”** 对话框以便保存源表定义。</span><span class="sxs-lookup"><span data-stu-id="f2468-132">Close the **Specify Column Mapping** dialog box to save the source table definition.</span></span>  
  
6.  <span data-ttu-id="f2468-133">单击 **“打开筛选器编辑器”** 为数据集定义筛选器。</span><span class="sxs-lookup"><span data-stu-id="f2468-133">Click **Open Filter Editor** to define a filter for the data set.</span></span>  
  
     <span data-ttu-id="f2468-134">此时将打开 **“数据集筛选器”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="f2468-134">The **Data Set Filter** dialog box opens.</span></span> <span data-ttu-id="f2468-135">如果结构包含嵌套表，则可以分两部分创建筛选器。</span><span class="sxs-lookup"><span data-stu-id="f2468-135">If the structure contains a nested table, you can create a filter in two parts.</span></span> <span data-ttu-id="f2468-136">首先，使用 **“数据集筛选器”** 对话框对事例表设置条件，然后使用 **“筛选器”** 对话框对嵌套行设置条件。</span><span class="sxs-lookup"><span data-stu-id="f2468-136">First, set conditions on the case table by using the **Data Set Filter** dialog box, and then set conditions on the nested rows by using the **Filter** dialog box.</span></span>  
  
7.  <span data-ttu-id="f2468-137">在 **“数据集筛选器”** 对话框中，单击网格顶部的行，并在 **“挖掘结构列”** 下的列表中选择表或列。</span><span class="sxs-lookup"><span data-stu-id="f2468-137">In the **Data Set Filter** dialog box, click the top row in the grid, under **Mining Structure Column**, and select a table or column from the list.</span></span>  
  
     <span data-ttu-id="f2468-138">如果数据源视图包含多个表或一个嵌套表，则必须先选择表名。</span><span class="sxs-lookup"><span data-stu-id="f2468-138">If the data source view contains multiple tables, or a nested table, you must first select the table name.</span></span> <span data-ttu-id="f2468-139">如果不先选择表名，则还可以直接从事例表中选择列。</span><span class="sxs-lookup"><span data-stu-id="f2468-139">Otherwise, you can select columns from the case table directly.</span></span>  
  
     <span data-ttu-id="f2468-140">为需要进行筛选的每个列都添加一个新行。</span><span class="sxs-lookup"><span data-stu-id="f2468-140">Add a new row for each column that you want to filter.</span></span>  
  
8.  <span data-ttu-id="f2468-141">使用 **“运算符”** 和 **“值”** 列来定义列的筛选方式。</span><span class="sxs-lookup"><span data-stu-id="f2468-141">Use **Operator**, and **Value** columns to define how the column is filtered.</span></span>  
  
     <span data-ttu-id="f2468-142">**注意** ：键入值时不必使用引号。</span><span class="sxs-lookup"><span data-stu-id="f2468-142">**Note** Type values without using quotation marks.</span></span>  
  
9. <span data-ttu-id="f2468-143">单击“和/或”\*\*\*\* 文本框并选择逻辑运算符来定义多个条件的组合方式。</span><span class="sxs-lookup"><span data-stu-id="f2468-143">Click the **And/Or** text box and select a logical operator to define how multiple conditions are combine.</span></span>  
  
10. <span data-ttu-id="f2468-144">（可选）单击 "**值**" 文本框右侧的 "浏览" 按钮\*\* ( ") \*\* " 打开 "**筛选器**" 对话框，并对嵌套表或单个事例表列设置条件。</span><span class="sxs-lookup"><span data-stu-id="f2468-144">Optionally, click the browse button **(...)** at the right of the **Value** text box to open the **Filter** dialog box and set conditions on the nested table or on the individual case table columns.</span></span>  
  
11. <span data-ttu-id="f2468-145">查看 **“表达式”** 窗格中的文本以验证整个筛选器条件是否正确。</span><span class="sxs-lookup"><span data-stu-id="f2468-145">Verify that the completed filter conditions are correct by viewing the text in the **Expression** pane.</span></span>  
  
12. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="f2468-146">筛选器条件将在创建准确性图表时应用到数据源。</span><span class="sxs-lookup"><span data-stu-id="f2468-146">The filter condition is applied to the data source when you create the accuracy chart.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2468-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f2468-147">See Also</span></span>  
 <span data-ttu-id="f2468-148">[选择和映射模型测试数据](choose-and-map-model-testing-data.md) </span><span class="sxs-lookup"><span data-stu-id="f2468-148">[Choose and Map Model Testing Data](choose-and-map-model-testing-data.md) </span></span>  
 <span data-ttu-id="f2468-149">[使用嵌套表数据作为准确性图表的输入](using-nested-table-data-as-an-input-for-an-accuracy-chart.md) </span><span class="sxs-lookup"><span data-stu-id="f2468-149">[Using Nested Table Data as an Input for an Accuracy Chart](using-nested-table-data-as-an-input-for-an-accuracy-chart.md) </span></span>  
 [<span data-ttu-id="f2468-150">选择准确性图表类型和设置图表选项</span><span class="sxs-lookup"><span data-stu-id="f2468-150">Choose an Accuracy Chart Type and Set Chart Options</span></span>](choose-an-accuracy-chart-type-and-set-chart-options.md)  
  
  
