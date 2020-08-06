---
title: 挖掘模型的筛选器 (Analysis Services 数据挖掘) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [data mining]
- filter syntax [data mining]
- models [Analysis Services], filtering
- filters [data mining]
- filtering data [Analysis Services]
ms.assetid: 0f29c19c-4be3-4bc7-ab60-f4130a10d59c
author: minewiskan
ms.author: owend
ms.openlocfilehash: a4e2c82c977f734948e107773e439ca154f6cfdd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578515"
---
# <a name="filters-for-mining-models-analysis-services---data-mining"></a><span data-ttu-id="0c7ff-102">挖掘模型的筛选器（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="0c7ff-102">Filters for Mining Models (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="0c7ff-103">基于数据的模型筛选有助于创建利用挖掘结构中的数据子集的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-103">Data-based model filtering helps you create mining models that use subsets of data in a mining structure.</span></span> <span data-ttu-id="0c7ff-104">使用筛选功能，可以基于全面的数据源视图来创建单个挖掘结构，因此可以灵活地设计挖掘结构和数据源。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-104">Filtering gives you flexibility when you design your mining structures and data sources, because you can create a single mining structure, based on a comprehensive data source view.</span></span> <span data-ttu-id="0c7ff-105">随后即可以创建筛选器，以便仅将该数据的一部分用于对各种模型进行定型和测试，而不是为数据的每个子集均生成不同的结构和相关模型。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-105">You can then create filters to use only a part of that data for training and testing a variety of models, instead of building a different structure and related model for each subset of data.</span></span>  
  
 <span data-ttu-id="0c7ff-106">例如，针对 Customers 表和相关表定义数据源视图。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-106">For example, you define the data source view on the Customers table and related tables.</span></span> <span data-ttu-id="0c7ff-107">随后，定义一个包括所需的全部字段的挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-107">Next, you define a single mining structure that includes all the fields you need.</span></span> <span data-ttu-id="0c7ff-108">最后，创建一个针对特定的客户属性（如 Region）进行筛选的模型。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-108">Finally, you create a model that is filtered on a particular customer attribute, such as Region.</span></span> <span data-ttu-id="0c7ff-109">随后，您即可以方便地创建该模型的副本，而且只需更改筛选条件即可基于不同的区域生成新模型。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-109">You can then easily make a copy of that model, and change just the filter condition to generate a new model based on a different region.</span></span>  
  
 <span data-ttu-id="0c7ff-110">下面是一些可能受益于此功能的现实情况：</span><span class="sxs-lookup"><span data-stu-id="0c7ff-110">Some real-life scenarios where you might benefit from this feature include the following:</span></span>  
  
-   <span data-ttu-id="0c7ff-111">为离散值（如性别、区域等）创建单独的模型。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-111">Creating separate models for discrete values such as gender, regions, and so forth.</span></span> <span data-ttu-id="0c7ff-112">例如，服装店可以使用客户统计数据来按性别生成不同的模型，即使所有客户的销售数据来自同一个数据源也是如此。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-112">For example, a clothing store might use customer demographics to build separate models by gender, even though the sales data comes from a single data source for all customers.</span></span>  
  
-   <span data-ttu-id="0c7ff-113">通过创建并测试相同数据的不同分组（如年龄段 20-30 、年龄段 20-40 和年龄段 20-25）来试验模型。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-113">Experimenting with models by creating and then testing multiple groupings of the same data, such as ages 20-30 vs. ages 20-40 vs. ages 20-25.</span></span>  
  
-   <span data-ttu-id="0c7ff-114">针对嵌套表内容指定复杂的筛选器，例如，要求只有当客户至少购买了两件特定商品时才在模型中包括一个事例。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-114">Specifying complex filters on nested table contents, such as requiring that a case be included in the model only if the customer has purchased at least two of a particular item.</span></span>  
  
 <span data-ttu-id="0c7ff-115">本节介绍如何针对挖掘模型生成、使用和管理筛选器。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-115">This section explains how to build, use, and manage filters on mining models.</span></span>  
  
## <a name="creating-model-filters"></a><span data-ttu-id="0c7ff-116">创建模型筛选器</span><span class="sxs-lookup"><span data-stu-id="0c7ff-116">Creating Model Filters</span></span>  
 <span data-ttu-id="0c7ff-117">可以按如下方式创建和应用筛选器：</span><span class="sxs-lookup"><span data-stu-id="0c7ff-117">You can create and apply filters in the following ways:</span></span>  
  
-   <span data-ttu-id="0c7ff-118">使用数据挖掘设计器中的 **“挖掘模型”** 选项卡，并借助筛选器编辑器对话框生成各个条件。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-118">Using the **Mining Models** tab in Data Mining Designer to build conditions with the help of filter editor dialog boxes.</span></span>  
  
-   <span data-ttu-id="0c7ff-119">在挖掘模型的属性中直接键入筛选表达式 `Filter` 。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-119">Typing a filter expression directly into the `Filter` property of the mining model.</span></span>  
  
-   <span data-ttu-id="0c7ff-120">使用 AMO 以编程方式对模型设置筛选条件。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-120">Setting filter conditions on a model programmatically, by using AMO.</span></span>  
  
### <a name="creating-model-filters-using-data-mining-designer"></a><span data-ttu-id="0c7ff-121">使用数据挖掘设计器创建模型筛选器</span><span class="sxs-lookup"><span data-stu-id="0c7ff-121">Creating Model Filters using Data Mining Designer</span></span>  
 <span data-ttu-id="0c7ff-122">可以通过更改挖掘模型的 `Filter` 属性在数据挖掘设计器中筛选模型。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-122">You filter a model in Data Mining Designer by changing the `Filter` property of the mining model.</span></span> <span data-ttu-id="0c7ff-123">可以在 **“属性”** 窗格中直接键入筛选表达式，也可以打开一个筛选器对话框来生成条件。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-123">You can either type a filter expression directly into the **Properties** pane, or you can open a filter dialog box to build conditions.</span></span>  
  
 <span data-ttu-id="0c7ff-124">共有两个筛选器对话框。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-124">There are two filter dialog boxes.</span></span> <span data-ttu-id="0c7ff-125">第一个对话框可用来创建应用于事例表的条件。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-125">The first lets you create conditions that are applied to the case table.</span></span> <span data-ttu-id="0c7ff-126">如果数据源中包含多个表，请首先选择一个表，然后选择一列并指定应用于该列的运算符和条件。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-126">If the data source contains multiple tables, first you select a table, and then you select a column and specify operators and conditions that apply to that column.</span></span> <span data-ttu-id="0c7ff-127">可以通过使用运算符来链接多个条件 `AND` / `OR` 。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-127">You can link multiple conditions by using `AND`/`OR` operators.</span></span> <span data-ttu-id="0c7ff-128">可用于定义值的运算符取决于该列是包含离散值还是连续值。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-128">The operators that are available for defining values depend on whether the column contains discrete or continuous values.</span></span> <span data-ttu-id="0c7ff-129">例如，对于连续值，可以使用 `greater than` 和 `less than` 运算符。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-129">For example, with continuous values, you can use `greater than` and `less than` operators.</span></span> <span data-ttu-id="0c7ff-130">但是，对于离散值，只能使用 `= (equal to)`、`!= (not equal to)` 和 `is null` 运算符。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-130">However, for discrete values, you can only use `= (equal to)`, `!= (not equal to)`, and `is null` operators.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0c7ff-131">不支持使用 `LIKE` 关键字。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-131">The `LIKE` keyword is not supported.</span></span> <span data-ttu-id="0c7ff-132">如果您希望包括多个离散属性，则必须创建不同条件并使用 `OR` 运算符来链接它们。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-132">If you want to include multiple discrete attributes, you must create separate conditions and link them by using the `OR` operator.</span></span>  
  
 <span data-ttu-id="0c7ff-133">如果条件非常复杂，则可以使用第二个筛选器对话框，一次处理一个表。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-133">If the conditions are complex, you can use the second filter dialog box to work with one table at a time.</span></span> <span data-ttu-id="0c7ff-134">当您关闭第二个筛选器对话框时，系统会对筛选表达式进行求值，并将值与对事例表中其他列设置的筛选条件合并。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-134">When you close the second filter dialog box, the expression is evaluated and then combined with filter conditions that have been set on other columns in the case table.</span></span>  
  
### <a name="creating-filters-on-nested-tables"></a><span data-ttu-id="0c7ff-135">针对嵌套表创建筛选器</span><span class="sxs-lookup"><span data-stu-id="0c7ff-135">Creating Filters on Nested Tables</span></span>  
 <span data-ttu-id="0c7ff-136">如果数据源视图中包含嵌套表，则可以使用第二个筛选器对话框来针对嵌套表中的行生成条件。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-136">If the data source view contains nested tables, you can use the second filter dialog box to build conditions on the rows in the nested tables.</span></span>  
  
 <span data-ttu-id="0c7ff-137">例如，如果您的事例表与客户相关，而且嵌套表中显示客户已经购买的产品，则可以通过在嵌套表的筛选器中使用下面的语法来为已经购买了特定商品的客户创建一个筛选器： `[ProductName]='Water Bottle' OR ProductName='Water Bottle Cage'`。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-137">For example, if your case table is related to customers, and the nested table shows the products that a customer has purchased, you can create a filter for customers who have purchased particular items by using the following syntax in the nested table filter: `[ProductName]='Water Bottle' OR ProductName='Water Bottle Cage'`.</span></span>  
  
 <span data-ttu-id="0c7ff-138">还可以使用 `EXISTS` 或 `NOT EXISTS` 关键字和子查询在嵌套表中筛选特定值，以查看其是否存在。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-138">You can also filter on the existence of a particular value in the nested table by using the `EXISTS` or `NOT EXISTS` keywords and a subquery.</span></span> <span data-ttu-id="0c7ff-139">这允许您创建诸如 `EXISTS (SELECT * FROM Products WHERE ProductName='Water Bottle')`之类的条件。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-139">This lets you create conditions such as `EXISTS (SELECT * FROM Products WHERE ProductName='Water Bottle')`.</span></span> <span data-ttu-id="0c7ff-140">如果嵌套表中至少有一行包括 `EXISTS SELECT(<subquery>)` 值，则 `Water Bottle` 将返回 `true`。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-140">The `EXISTS SELECT(<subquery>)` returns `true` if the nested table contains at least one row that includes the value, `Water Bottle`.</span></span>  
  
 <span data-ttu-id="0c7ff-141">可以将事例表中的条件与嵌套表中的条件组合起来。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-141">You can combine conditions on the case table with conditions on the nested table.</span></span> <span data-ttu-id="0c7ff-142">例如，下面的语法包括事例表中的一个条件 (`Age > 30` )、嵌套表中的一个子查询 (`EXISTS (SELECT * FROM Products)`) 以及嵌套表中的多个条件 (`WHERE ProductName='Milk'  AND Quantity>2`)。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-142">For example, the following syntax includes a condition on the case table (`Age > 30` ), a subquery on the nested table (`EXISTS (SELECT * FROM Products)`), and multiple conditions on the nested table (`WHERE ProductName='Milk'  AND Quantity>2`) ).</span></span>  
  
```  
(Age > 30 AND EXISTS (SELECT * FROM Products WHERE ProductName='Milk'  AND Quantity>2) )  
```  
  
 <span data-ttu-id="0c7ff-143">在完成筛选器的生成之后，筛选器文本将由 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]进行求值，转换为 DMX 表达式，之后将随模型一起保存。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-143">When you have finished building the filter, the filter text is evaluated by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], translated to a DMX expression, and then saved with the model.</span></span>  
  
 <span data-ttu-id="0c7ff-144">有关如何在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中使用筛选器对话框的说明，请参阅 [对挖掘模型应用筛选器](apply-a-filter-to-a-mining-model.md)。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-144">For instructions on how to use the filter dialog boxes in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], see [Apply a Filter to a Mining Model](apply-a-filter-to-a-mining-model.md).</span></span>  
  
## <a name="managing-mining-model-filters"></a><span data-ttu-id="0c7ff-145">管理挖掘模型筛选器</span><span class="sxs-lookup"><span data-stu-id="0c7ff-145">Managing Mining Model Filters</span></span>  
 <span data-ttu-id="0c7ff-146">基于数据的模型筛选大大简化了管理挖掘结构和挖掘模型的任务，因为您可以基于同一个结构方便地创建多个模型。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-146">Data-based model filtering greatly simplifies the task of managing mining structures and mining models, because you can easily create multiple models that are based on the same structure.</span></span> <span data-ttu-id="0c7ff-147">您还可以快速创建现有挖掘模型的多个副本，之后将只需更改筛选条件。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-147">You can also quickly make copies of existing mining models and then change only the filter condition.</span></span> <span data-ttu-id="0c7ff-148">但是，筛选器会导致某些混淆。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-148">However, filters can lead to some confusion.</span></span>  
  
 <span data-ttu-id="0c7ff-149">以下是有关如何管理和解释有关挖掘模型的筛选器的常见问题：</span><span class="sxs-lookup"><span data-stu-id="0c7ff-149">Here are some frequently asked questions about how to manage and interpret filters on mining models:</span></span>  
  
### <a name="how-can-i-tell-whether-a-filter-is-being-used"></a><span data-ttu-id="0c7ff-150">我如何分辨是否正在使用筛选器？</span><span class="sxs-lookup"><span data-stu-id="0c7ff-150">How can I tell whether a filter is being used?</span></span>  
 <span data-ttu-id="0c7ff-151">可以使用多种方法确定是否对模型应用了筛选器：</span><span class="sxs-lookup"><span data-stu-id="0c7ff-151">There are multiple ways to determine whether a filter is applied to a model:</span></span>  
  
-   <span data-ttu-id="0c7ff-152">在设计器中，单击 "**挖掘模型**" 选项卡，打开 "**属性**"，然后查看 `Filter` 挖掘模型的属性。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-152">In the designer, click the **Mining Models** tab, open **Properties**, and view the `Filter` property of the mining model.</span></span>  
  
-   <span data-ttu-id="0c7ff-153">DMV DMSCHEMA_MINING_MODELS 将输出一个包含筛选器文本的列。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-153">The DMV, DMSCHEMA_MINING_MODELS, outputs a column that contains the text of the filter.</span></span> <span data-ttu-id="0c7ff-154">您可以使用以下有关 DMV 的查询来返回模型的名称及其筛选器：</span><span class="sxs-lookup"><span data-stu-id="0c7ff-154">You can use the following query on a DMV to return the names of models and their filters:</span></span>  
  
    ```  
    SELECT MODEL_NAME, [FILTER]   
    FROM $SYSTEM.DMSCHEMA_MINING_MODELS  
  
    ```  
  
-   <span data-ttu-id="0c7ff-155">您可以在 AMO 中获取 MiningModel 对象的 Filter 属性的值，或在 XMLA 中检查 Filter 元素。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-155">You can get the value of the Filter property of the MiningModel object in AMO, or inspect the Filter element in XMLA.</span></span>  
  
 <span data-ttu-id="0c7ff-156">您还可以建立模型的命名约定以反映筛选器的内容。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-156">You might also establish a naming convention for models to reflect the contents of the filter.</span></span> <span data-ttu-id="0c7ff-157">这样可更易于分辨相关模型。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-157">This can make it easier to tell related models apart.</span></span>  
  
### <a name="how-can-i-save-a-filter"></a><span data-ttu-id="0c7ff-158">如何保存筛选器？</span><span class="sxs-lookup"><span data-stu-id="0c7ff-158">How can I save a filter?</span></span>  
 <span data-ttu-id="0c7ff-159">筛选表达式将保存为脚本，并随其关联挖掘模型或嵌套表一起存储。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-159">The filter expression is saved as a script that is stored with the associated mining model or nested table.</span></span> <span data-ttu-id="0c7ff-160">如果删除了筛选器文本，则只能通过手动重新创建筛选表达式的方式来将其还原。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-160">If you delete the filter text, it can only be restored by manually re-creating the filter expression.</span></span> <span data-ttu-id="0c7ff-161">因此，如果创建了复杂的筛选表达式，还应当创建筛选器文本的备份副本。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-161">Therefore, if you create complex filter expressions, you should create a backup copy of the filter text.</span></span>  
  
### <a name="why-cant-i-see-any-effects-from-the-filter"></a><span data-ttu-id="0c7ff-162">为什么看不到来自筛选器的任何效果？</span><span class="sxs-lookup"><span data-stu-id="0c7ff-162">Why can't I see any effects from the filter?</span></span>  
 <span data-ttu-id="0c7ff-163">无论何时更改或添加筛选表达式，都必须重新处理挖掘结构和挖掘模型，然后才能查看筛选器的效果。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-163">Whenever you change or add a filter expression, you must reprocess the structure and model before you can view the effects of the filter.</span></span>  
  
### <a name="why-do-i-see-filtered-attributes-in-prediction-query-results"></a><span data-ttu-id="0c7ff-164">为什么我在预测查询结果中会看到已筛选的属性？</span><span class="sxs-lookup"><span data-stu-id="0c7ff-164">Why do I see filtered attributes in prediction query results?</span></span>  
 <span data-ttu-id="0c7ff-165">对模型应用筛选器时，仅影响对用于培训模型的事例的选择。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-165">When you apply a filter to a model, it affects only the selection of cases used for training the model.</span></span> <span data-ttu-id="0c7ff-166">筛选器不会影响对模型已知的属性，或更改或取消显示数据源中显示的数据。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-166">The filter does not affect the attributes known to the model, or change or suppress data that is present in the data source.</span></span> <span data-ttu-id="0c7ff-167">因此，针对模型的查询可以返回对其他事例类型的预测，且模型使用的值的下拉列表可能会显示筛选器所排除的属性值。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-167">As a result, queries against the model can return predictions for other types of cases, and dropdown lists of values used by the model might show attribute values excluded by the filter.</span></span>  
  
 <span data-ttu-id="0c7ff-168">例如，假设您培训仅使用涉及 20-30 年龄段的女性的事例的 [自行车购买者] 模型。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-168">For example, suppose you train the [Bike Buyer] model using only cases involving women aged 20-30.</span></span> <span data-ttu-id="0c7ff-169">您仍可以运行预测某个男性购买自行车的可能性的预测查询，或者预测 30-40 年龄段的女性的购买结果。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-169">You can still run a prediction query that predicts the probability of a man buying a bike, or predict the outcome for a woman aged 30-40.</span></span> <span data-ttu-id="0c7ff-170">这是因为数据源中显示的属性和值定义理论上的可能性，而事例定义用于培训的实际发生情况。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-170">That is because the attributes and values present in the data source define what is theoretically possible, while the cases define the occurrences used for training.</span></span> <span data-ttu-id="0c7ff-171">但是，这些查询将返回非常小的可能性，因为培训数据不包含任何带有目标值的事例。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-171">However, these queries would return very small probabilities, because the training data does not contain any cases with the target values.</span></span>  
  
 <span data-ttu-id="0c7ff-172">如果您需要在模型中完全隐藏或匿名属性值，可采取几个不同的方法：</span><span class="sxs-lookup"><span data-stu-id="0c7ff-172">If you need to completely hide or anonymize attribute values in the model, there are various options:</span></span>  
  
-   <span data-ttu-id="0c7ff-173">筛选作为数据源视图定义的一部分或在关系数据源中的传入数据。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-173">Filter the incoming data as part of the definition of the data source view, or in the relational data source.</span></span>  
  
-   <span data-ttu-id="0c7ff-174">对属性值进行掩码或编码。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-174">Mask or encode the attribute value.</span></span>  
  
-   <span data-ttu-id="0c7ff-175">将已排除的值作为挖掘结构定义的一部分折叠到某个类别中。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-175">Collapse excluded values into a category as part of the mining structure definition.</span></span>  
  
## <a name="related-resources"></a><span data-ttu-id="0c7ff-176">相关资源</span><span class="sxs-lookup"><span data-stu-id="0c7ff-176">Related Resources</span></span>  
 <span data-ttu-id="0c7ff-177">有关筛选器语法和筛选器表达式示例的详细信息，请参阅 [模型筛选器语法和示例（Analysis Services – 数据挖掘）](model-filter-syntax-and-examples-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-177">For more information about filter syntax, and examples of filter expressions, see [Model Filter Syntax and Examples &#40;Analysis Services - Data Mining&#41;](model-filter-syntax-and-examples-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="0c7ff-178">有关在测试挖掘模型时如何使用模型筛选器的信息，请参阅 [选择准确性图表类型和设置图表选项](choose-an-accuracy-chart-type-and-set-chart-options.md)。</span><span class="sxs-lookup"><span data-stu-id="0c7ff-178">For information about how to use model filters when you are testing a mining model, see [Choose an Accuracy Chart Type and Set Chart Options](choose-an-accuracy-chart-type-and-set-chart-options.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c7ff-179">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0c7ff-179">See Also</span></span>  
 <span data-ttu-id="0c7ff-180">[模型筛选器语法和示例 &#40;Analysis Services 数据挖掘&#41;](model-filter-syntax-and-examples-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="0c7ff-180">[Model Filter Syntax and Examples &#40;Analysis Services - Data Mining&#41;](model-filter-syntax-and-examples-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="0c7ff-181">测试和验证（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="0c7ff-181">Testing and Validation &#40;Data Mining&#41;</span></span>](testing-and-validation-data-mining.md)  
  
  
