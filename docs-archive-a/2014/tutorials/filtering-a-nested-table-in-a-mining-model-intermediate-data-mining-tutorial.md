---
title: 在挖掘模型中筛选嵌套表 (中级数据挖掘教程) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0a3ae0e5-897b-4898-a60d-5455eec3d305
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a1e6ce2936a3c6763ea41999b2724c0fe8c79301
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692617"
---
# <a name="filtering-a-nested-table-in-a-mining-model-intermediate-data-mining-tutorial"></a><span data-ttu-id="fe442-102">筛选挖掘模型中的嵌套表（数据挖掘中级教程）</span><span class="sxs-lookup"><span data-stu-id="fe442-102">Filtering a Nested Table in a Mining Model (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="fe442-103">创建并浏览模型后，您决定将精力集中在客户数据的某个子集上。</span><span class="sxs-lookup"><span data-stu-id="fe442-103">After you have created and explored the model, you decide that you want to focus on a subset of the customer data.</span></span> <span data-ttu-id="fe442-104">例如，您可能希望仅分析包含特定项的购物篮，或者可能希望仅分析在某个时间段内没有购买任何物品的客户的人口统计信息。</span><span class="sxs-lookup"><span data-stu-id="fe442-104">For example, you might want to analyze only the baskets that contain a specific item, or to analyze the demographics of customers who have not purchased anything in a certain period.</span></span>  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] <span data-ttu-id="fe442-105">提供了筛选挖掘模型中所使用数据的功能。</span><span class="sxs-lookup"><span data-stu-id="fe442-105">provides the ability to filter the data that is used in a mining model.</span></span> <span data-ttu-id="fe442-106">此功能非常有用，因为您无需设置新的数据源视图即可使用不同的数据。</span><span class="sxs-lookup"><span data-stu-id="fe442-106">This feature is useful because you do not need to set up a new data source view to use different data.</span></span> <span data-ttu-id="fe442-107">在数据挖掘基础教程中，您学习了如何通过对事例表应用条件来筛选平面表中的数据。</span><span class="sxs-lookup"><span data-stu-id="fe442-107">In the Basic Data Mining Tutorial, you learned how to filter data from a flat table by applying conditions to the case table.</span></span> <span data-ttu-id="fe442-108">在此任务中，您将创建一个应用于嵌套表的筛选器。</span><span class="sxs-lookup"><span data-stu-id="fe442-108">In this task, you create a filter that applies to a nested table.</span></span>  
  
## <a name="filters-on-nested-vs-case-tables"></a><span data-ttu-id="fe442-109">针对嵌套表和针对事例表的筛选器</span><span class="sxs-lookup"><span data-stu-id="fe442-109">Filters on Nested vs. Case Tables</span></span>  
 <span data-ttu-id="fe442-110">如果您的数据源视图包含一个事例表和一个嵌套表，如 Association 模型中使用的数据源视图，则可以筛选事例表中的值、筛选嵌套表中是否存在某个值，或者这两者的组合。</span><span class="sxs-lookup"><span data-stu-id="fe442-110">If your data source view contains a case table and a nested table, like the data source view used in the Association model, you can filter on values from the case table, the presence or absence of a value in the nested table, or some combination of both.</span></span>  
  
 <span data-ttu-id="fe442-111">在本任务中，您将首选制作 Association 模型的副本，然后将 IncomeGroup 和 Region 属性添加到新的相关模型中，以便您能够筛选事例表中的这些属性。</span><span class="sxs-lookup"><span data-stu-id="fe442-111">In this task, you will first make a copy of the Association model and then add the IncomeGroup and Region attributes to the new related model, so that you can filter on those attributes in the case table.</span></span>  
  
#### <a name="to-create-and-modify-a-copy-of-the-association-model"></a><span data-ttu-id="fe442-112">创建和修改 Association 模型的副本</span><span class="sxs-lookup"><span data-stu-id="fe442-112">To create and modify a copy of the Association model</span></span>  
  
1.  <span data-ttu-id="fe442-113">在的 "**挖掘模型**" 选项卡中 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ，右键单击该 `Association` 模型，然后选择 "**新建挖掘模型**"。</span><span class="sxs-lookup"><span data-stu-id="fe442-113">In the **Mining Models** tab of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], right-click the `Association` model, and select **New Mining Model**.</span></span>  
  
2.  <span data-ttu-id="fe442-114">对于 "**型号名称**"，请键入 `Association Filtered` 。</span><span class="sxs-lookup"><span data-stu-id="fe442-114">For **Model Name**, type `Association Filtered`.</span></span> <span data-ttu-id="fe442-115">对于 "**算法名称**"，请选择 " **Microsoft 关联规则**"。</span><span class="sxs-lookup"><span data-stu-id="fe442-115">For **Algorithm Name**, select **Microsoft Association Rules**.</span></span> <span data-ttu-id="fe442-116">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="fe442-116">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="fe442-117">在关联筛选模型的列中，单击 "IncomeGroup" 行，并将值从 "**忽略**" 更改为 "**输入**"。</span><span class="sxs-lookup"><span data-stu-id="fe442-117">In the column for the Association Filtered model, click the IncomeGroup row and change the value from **Ignore** to **Input**.</span></span>  
  
 <span data-ttu-id="fe442-118">接下来，将在新的关联模型中创建一个针对事例表的筛选器。</span><span class="sxs-lookup"><span data-stu-id="fe442-118">Next, you will create a filter on the case table in the new association model.</span></span> <span data-ttu-id="fe442-119">仅当客户在目标区域中时或者仅当客户达到目标收入水平时，该筛选器才传递给模型。</span><span class="sxs-lookup"><span data-stu-id="fe442-119">The filter will pass to the model only the customers in the target region or with the target income level.</span></span> <span data-ttu-id="fe442-120">然后，将添加第二个筛选条件集，以指定模型仅使用其购物篮已至少包含一项的客户。</span><span class="sxs-lookup"><span data-stu-id="fe442-120">Then, you will add a second set of filter conditions to specify that the model uses only customers whose shopping baskets contained at least one item.</span></span>  
  
#### <a name="to-add-a-filter-to-a-mining-model"></a><span data-ttu-id="fe442-121">将筛选器添加到挖掘模型中</span><span class="sxs-lookup"><span data-stu-id="fe442-121">To add a filter to a mining model</span></span>  
  
1.  <span data-ttu-id="fe442-122">在 "**挖掘模型**" 选项卡中，右键单击筛选的模型关联，然后选择 "**设置模型筛选器**"。</span><span class="sxs-lookup"><span data-stu-id="fe442-122">In the **Mining Models** tab, right-click the model Association Filtered, and select **Set Model Filter**.</span></span>  
  
2.  <span data-ttu-id="fe442-123">在 **“模型筛选器”** 对话框的 **“挖掘结构列”** 文本框中，单击网格中的第一行。</span><span class="sxs-lookup"><span data-stu-id="fe442-123">In the **Model Filter** dialog box, click the top row in the grid, in the **Mining Structure Column** text box.</span></span>  
  
3.  <span data-ttu-id="fe442-124">在 "**挖掘结构列**" 文本框中，选择 "IncomeGroup"。</span><span class="sxs-lookup"><span data-stu-id="fe442-124">In the **Mining Structure Column** text box, select IncomeGroup.</span></span>  
  
     <span data-ttu-id="fe442-125">该文本框左侧的图标会发生改变，以指示所选项是列。</span><span class="sxs-lookup"><span data-stu-id="fe442-125">The icon at the left side of the text box changes to indicate that the selected item is a column.</span></span>  
  
4.  <span data-ttu-id="fe442-126">单击 "**运算符**" 文本框，然后 **=** 从列表中选择运算符。</span><span class="sxs-lookup"><span data-stu-id="fe442-126">Click the **Operator** text box and select the **=** operator from the list.</span></span>  
  
5.  <span data-ttu-id="fe442-127">单击 "**值**" 文本框，然后 `High` 在框中键入。</span><span class="sxs-lookup"><span data-stu-id="fe442-127">Click the **Value** text box, and type `High` in the box.</span></span>  
  
6.  <span data-ttu-id="fe442-128">单击网格中的下一行。</span><span class="sxs-lookup"><span data-stu-id="fe442-128">Click the next row in the grid.</span></span>  
  
7.  <span data-ttu-id="fe442-129">单击网格下一行中的 "**和/或**" 文本框，然后选择**或**。</span><span class="sxs-lookup"><span data-stu-id="fe442-129">Click the **AND/OR** text box in the next row of the grid and select **OR**.</span></span>  
  
8.  <span data-ttu-id="fe442-130">在 "**挖掘结构列**" 文本框中，选择 "IncomeGroup"。</span><span class="sxs-lookup"><span data-stu-id="fe442-130">In the **Mining Structure Column** text box, select IncomeGroup.</span></span> <span data-ttu-id="fe442-131">在 "**值**" 文本框中，键入 `Moderate` 。</span><span class="sxs-lookup"><span data-stu-id="fe442-131">In the **Value** text box, type `Moderate`.</span></span>  
  
     <span data-ttu-id="fe442-132">您创建的筛选条件将自动添加到 "**表达式**" 文本框中，并应如下所示：</span><span class="sxs-lookup"><span data-stu-id="fe442-132">The filter condition that you created is automatically added to the **Expression** text box, and should appears as follows:</span></span>  
  
     `[IncomeGroup] = 'High' OR [IncomeGroup] = 'Moderate'`  
  
9. <span data-ttu-id="fe442-133">单击网格中的下一行，将运算符保留为默认值**和**。</span><span class="sxs-lookup"><span data-stu-id="fe442-133">Click the next row in the grid, leaving the operator as the default, **AND**.</span></span>  
  
10. <span data-ttu-id="fe442-134">对于 "**运算符**"，保留默认值 "**包含**"。</span><span class="sxs-lookup"><span data-stu-id="fe442-134">For **Operator**, leave the default value, **Contains**.</span></span> <span data-ttu-id="fe442-135">单击 "**值**" 文本框。</span><span class="sxs-lookup"><span data-stu-id="fe442-135">Click the **Value** text box.</span></span>  
  
11. <span data-ttu-id="fe442-136">在 "**筛选器**" 对话框中，在 "**挖掘结构列**" 下的第一行中，选择 `Model` 。</span><span class="sxs-lookup"><span data-stu-id="fe442-136">In the **Filter** dialog box, in the first row under **Mining Structure Column**, select `Model`.</span></span>  
  
12. <span data-ttu-id="fe442-137">对于 "**运算符**"，选择 "**不为 NULL**"。</span><span class="sxs-lookup"><span data-stu-id="fe442-137">For **Operator**, select **IS NOT NULL**.</span></span> <span data-ttu-id="fe442-138">将 "**值**" 文本框留空。</span><span class="sxs-lookup"><span data-stu-id="fe442-138">Leave the **Value** text box blank.</span></span> <span data-ttu-id="fe442-139">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="fe442-139">Click **OK**.</span></span>  
  
     <span data-ttu-id="fe442-140">"**模型筛选器**" 对话框的 "**表达式**" 文本框中的筛选条件会自动更新，以在嵌套表中包含新的条件。</span><span class="sxs-lookup"><span data-stu-id="fe442-140">The filter condition in the **Expression** text box of the **Model Filter** dialog box is automatically updated to include the new condition on the nested table.</span></span> <span data-ttu-id="fe442-141">完成的表达式如下：</span><span class="sxs-lookup"><span data-stu-id="fe442-141">The completed expression is as follows:</span></span>  
  
     `[IncomeGroup] = 'High' OR [IncomeGroup] = 'Moderate' AND EXISTS SELECT * FROM [vAssocSeqLineItems] WHERE [Model] <> NULL).`  
  
13. [!INCLUDE[clickOK](../includes/clickok-md.md)] ``  
  
#### <a name="to-enable-drillthrough-and-to-process-the-filtered-model"></a><span data-ttu-id="fe442-142">启用钻取并处理筛选后的模型</span><span class="sxs-lookup"><span data-stu-id="fe442-142">To enable drillthrough and to process the filtered model</span></span>  
  
1.  <span data-ttu-id="fe442-143">在 "**挖掘模型**" 选项卡中，右键单击该 `Association Filtered` 模型，然后选择 "**属性**"。</span><span class="sxs-lookup"><span data-stu-id="fe442-143">In the **Mining Models** tab, right-click the `Association Filtered` model, and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="fe442-144">将**AllowDrillThrough**属性更改为**True**。</span><span class="sxs-lookup"><span data-stu-id="fe442-144">Change the **AllowDrillThrough** property to **True**.</span></span>  
  
3.  <span data-ttu-id="fe442-145">右键单击 `Association Filtered` 挖掘模型，然后选择 "**处理模型**"。</span><span class="sxs-lookup"><span data-stu-id="fe442-145">Right-click the `Association Filtered` mining model, and select **Process Model**.</span></span>  
  
4.  <span data-ttu-id="fe442-146">在错误消息中单击 **"是"** 以将新模型部署到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="fe442-146">Click **Yes** in the error message to deploy the new model to the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
5.  <span data-ttu-id="fe442-147">在 "**处理挖掘结构**" 对话框中，单击 "**运行**"。</span><span class="sxs-lookup"><span data-stu-id="fe442-147">In the **Process Mining Structure** dialog box, click **Run**.</span></span>  
  
6.  <span data-ttu-id="fe442-148">处理完成后，单击 "**关闭**" 退出 "**处理进度**" 对话框，然后再次单击 "**关闭**" 以退出 "**处理挖掘结构**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="fe442-148">When processing is complete click **Close** to exit the **Process Progress** dialog box, and click **Close** again to exit the **Process Mining Structure** dialog box.</span></span>  
  
 <span data-ttu-id="fe442-149">您可以通过下面的方法进行验证：使用 Microsoft 一般内容树查看器并查看 NODE_SUPPORT 的值，看筛选模型所包含事例的数目是否小于原始模型中事例的数目。</span><span class="sxs-lookup"><span data-stu-id="fe442-149">You can verify by using the Microsoft Generic Content Tree viewer and looking at the value for NODE_SUPPORT that the filtered model contains fewer cases than the original model.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe442-150">备注</span><span class="sxs-lookup"><span data-stu-id="fe442-150">Remarks</span></span>  
 <span data-ttu-id="fe442-151">您刚才创建的嵌套表筛选器仅检查嵌套表中是否至少存在一个行；然而，您还可以创建用来检查特定产品是否存在的筛选条件。</span><span class="sxs-lookup"><span data-stu-id="fe442-151">The nested table filter that you just created checks only for the presence of at least one row in the nested table; however, you can also create filter conditions that check for the presence of specific products.</span></span>  <span data-ttu-id="fe442-152">例如，可以创建下面的筛选器：</span><span class="sxs-lookup"><span data-stu-id="fe442-152">For example, you could create the following filter:</span></span>  
  
```  
[IncomeGroup] = 'High' AND  
 EXISTS (SELECT * FROM [<nested table name>] WHERE [Model] = 'Water Bottle' )   
```  
  
 <span data-ttu-id="fe442-153">此语句表示您正在将事例表中的客户限制为仅为那些已购买水壶的客户。</span><span class="sxs-lookup"><span data-stu-id="fe442-153">This statement means that you are restricting the customers from the case table to only those who have purchased a water bottle.</span></span> <span data-ttu-id="fe442-154">但是，由于嵌套表属性的数量不受限制，因此，[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 不提供可供选择的可能值的列表。</span><span class="sxs-lookup"><span data-stu-id="fe442-154">However, because the number of nested table attributes is potentially unlimited, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] does not supply a list of possible values from which to select.</span></span> <span data-ttu-id="fe442-155">从而，您必须键入确切的值。</span><span class="sxs-lookup"><span data-stu-id="fe442-155">Instead, you must type the exact value.</span></span>  
  
 <span data-ttu-id="fe442-156">您可以单击 "**编辑查询**" 以手动更改筛选表达式。</span><span class="sxs-lookup"><span data-stu-id="fe442-156">You can click **Edit Query** to manually change the filter expression.</span></span> <span data-ttu-id="fe442-157">但是，如果手动更改筛选表达式的任意部分，网格都将被禁用，并且此后只能在文本编辑模式下编辑筛选表达式。</span><span class="sxs-lookup"><span data-stu-id="fe442-157">However, if you change any part of a filter expression manually, the grid will be disabled and thereafter you must work with the filter expression in text edit mode only.</span></span> <span data-ttu-id="fe442-158">若要恢复网格编辑模式，必须清除筛选表达式并重新开始。</span><span class="sxs-lookup"><span data-stu-id="fe442-158">To restore grid editing mode, you must clear the filter expression and start over.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="fe442-159">不能在嵌套表筛选器中使用 LIKE 运算符。</span><span class="sxs-lookup"><span data-stu-id="fe442-159">You cannot use the LIKE operator in a nested table filter.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="fe442-160">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="fe442-160">Next Task in Lesson</span></span>  
 [<span data-ttu-id="fe442-161">预测 &#40;中级数据挖掘教程的关联&#41;</span><span class="sxs-lookup"><span data-stu-id="fe442-161">Predicting Associations &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/predicting-associations-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="fe442-162">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fe442-162">See Also</span></span>  
 <span data-ttu-id="fe442-163">[模型筛选器语法和示例 &#40;Analysis Services 数据挖掘&#41;](../../2014/analysis-services/data-mining/model-filter-syntax-and-examples-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="fe442-163">[Model Filter Syntax and Examples &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/model-filter-syntax-and-examples-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="fe442-164">挖掘模型的筛选器（Analysis Services - 数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="fe442-164">Filters for Mining Models &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)  
  
  
