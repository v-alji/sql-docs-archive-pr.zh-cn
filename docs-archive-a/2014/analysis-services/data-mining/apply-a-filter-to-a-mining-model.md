---
title: 对挖掘模型应用筛选器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- model filter [data mining]
- filters [data mining]
- filtering input rows [Analysis Services]
- filtering data [Analysis Services]
ms.assetid: 4d0abeb5-e939-46d3-9097-6e0358244300
author: minewiskan
ms.author: owend
ms.openlocfilehash: d9f3147c36e69d9c2249d5bf6d1ba201799c6e27
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588759"
---
# <a name="apply-a-filter-to-a-mining-model"></a><span data-ttu-id="3c962-102">对挖掘模型应用筛选器</span><span class="sxs-lookup"><span data-stu-id="3c962-102">Apply a Filter to a Mining Model</span></span>
  <span data-ttu-id="3c962-103">如果挖掘结构包含嵌套表，则可以对事例表、嵌套表或两者同时应用筛选器。</span><span class="sxs-lookup"><span data-stu-id="3c962-103">If your mining structure contains a nested table, you can apply a filter to the case table, the nested table, or both.</span></span>  
  
 <span data-ttu-id="3c962-104">以下过程说明了如何创建两种筛选器：事例筛选器和嵌套表行筛选器。</span><span class="sxs-lookup"><span data-stu-id="3c962-104">The following procedure demonstrates how to create both kinds of filters: case filters, and filters on the nested table rows.</span></span>  
  
 <span data-ttu-id="3c962-105">事例表的条件将客户限制为收入在 30000 到 40000 之间的客户。</span><span class="sxs-lookup"><span data-stu-id="3c962-105">The condition on the case table restricts customers to those with income between 30000 and 40000.</span></span> <span data-ttu-id="3c962-106">嵌套表的条件将客户限制为未购买特定项目的客户。</span><span class="sxs-lookup"><span data-stu-id="3c962-106">The condition on the nested table restricts the customers to those who did not purchase a particular item.</span></span>  
  
 <span data-ttu-id="3c962-107">本示例中创建的完整筛选条件如下所示：</span><span class="sxs-lookup"><span data-stu-id="3c962-107">The complete filter condition created in this example is as follows:</span></span>  
  
```  
[Income] > '30000'   
AND  [Income] < '40000'   
AND EXISTS (SELECT * FROM [<nested table name>]   
WHERE [Model] <> 'Water Bottle' )   
```  
  
### <a name="to-create-a-case-filter-on-a-mining-model"></a><span data-ttu-id="3c962-108">创建挖掘模型的事例筛选器</span><span class="sxs-lookup"><span data-stu-id="3c962-108">To create a case filter on a mining model</span></span>  
  
1.  <span data-ttu-id="3c962-109">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]的解决方案资源管理器中，单击包含要筛选的挖掘模型的挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="3c962-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], in Solution Explorer, click the mining structure that contains the mining model you want to filter.</span></span>  
  
2.  <span data-ttu-id="3c962-110">单击 **“挖掘模型”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="3c962-110">Click the **Mining Models** tab.</span></span>  
  
3.  <span data-ttu-id="3c962-111">选择模型，然后右键单击打开快捷菜单。</span><span class="sxs-lookup"><span data-stu-id="3c962-111">Select the model, and right-click to open the shortcut menu.</span></span>  
  
     <span data-ttu-id="3c962-112">- 或 -</span><span class="sxs-lookup"><span data-stu-id="3c962-112">-or-</span></span>  
  
     <span data-ttu-id="3c962-113">选择该模型。</span><span class="sxs-lookup"><span data-stu-id="3c962-113">Select the model.</span></span> <span data-ttu-id="3c962-114">然后，在 **“挖掘模型”** 菜单上，选择 **“设置模型筛选器”**。</span><span class="sxs-lookup"><span data-stu-id="3c962-114">Then, on the **Mining Model** menu, select **Set Model Filter**.</span></span>  
  
4.  <span data-ttu-id="3c962-115">在 **“模型筛选器”** 对话框的 **“挖掘结构列”** 文本框中，单击网格中的第一行。</span><span class="sxs-lookup"><span data-stu-id="3c962-115">In the **Model Filter** dialog box, click the top row in the grid, in the **Mining Structure Column** text box.</span></span>  
  
5.  <span data-ttu-id="3c962-116">如果数据源包含一个平面表，则下拉列表只显示该表中列的名称。</span><span class="sxs-lookup"><span data-stu-id="3c962-116">If the data source contains a single flat table, the drop-down list displays only the names of the columns in that table.</span></span>  
  
     <span data-ttu-id="3c962-117">如果挖掘结构包含多个表，则下拉列表显示源表的名称。</span><span class="sxs-lookup"><span data-stu-id="3c962-117">If the mining structure contains multiple tables, the list shows the names of the source tables.</span></span> <span data-ttu-id="3c962-118">只有选中某个表后，才会显示列名。</span><span class="sxs-lookup"><span data-stu-id="3c962-118">The column names do not display until a table has been selected.</span></span>  
  
     <span data-ttu-id="3c962-119">如果挖掘结构包含一个事例表和一个嵌套表，则下拉列表显示事例表中的列和嵌套表的名称。</span><span class="sxs-lookup"><span data-stu-id="3c962-119">If the mining structure contains a case table and a nested table, the drop-down list shows columns from the case table, and the name of the nested table.</span></span>  
  
6.  <span data-ttu-id="3c962-120">从下拉列表中选择一列。</span><span class="sxs-lookup"><span data-stu-id="3c962-120">Select a column from the drop-down list.</span></span>  
  
     <span data-ttu-id="3c962-121">文本框左侧的图标会发生改变，以指示所选项是表还是列。</span><span class="sxs-lookup"><span data-stu-id="3c962-121">The icon at the left side of the text box changes to indicate that the selected item is a table or a column.</span></span>  
  
7.  <span data-ttu-id="3c962-122">单击 **“运算符”** 文本框并从列表中选择一个运算符。</span><span class="sxs-lookup"><span data-stu-id="3c962-122">Click the **Operator** text box and select an operator from the list.</span></span> <span data-ttu-id="3c962-123">有效的运算符会根据所选列的数据类型而不同。</span><span class="sxs-lookup"><span data-stu-id="3c962-123">The valid operators change depending on the data type of the column you selected.</span></span>  
  
8.  <span data-ttu-id="3c962-124">单击 **“值”** 文本框，然后在此框中键入一个值。</span><span class="sxs-lookup"><span data-stu-id="3c962-124">Click the **Value** text box, and type a value in the box.</span></span>  
  
     <span data-ttu-id="3c962-125">例如，选择 `Income` 作为列，选择大于运算符 ( # A0) ，然后键入 `30000` 。</span><span class="sxs-lookup"><span data-stu-id="3c962-125">For example, select `Income` as the column, select the greater than operator (>), and then type `30000`.</span></span>  
  
9. <span data-ttu-id="3c962-126">单击网格中的下一行。</span><span class="sxs-lookup"><span data-stu-id="3c962-126">Click the next row in the grid.</span></span>  
  
     <span data-ttu-id="3c962-127">您所创建的筛选条件自动添加到“表达式”文本框中。</span><span class="sxs-lookup"><span data-stu-id="3c962-127">The filter condition that you created is automatically added to the Expression text box.</span></span> <span data-ttu-id="3c962-128">例如： `[Income] > '30000'`</span><span class="sxs-lookup"><span data-stu-id="3c962-128">For example, `[Income] > '30000'`</span></span>  
  
10. <span data-ttu-id="3c962-129">单击网格下一行中的**和/或**文本框，以添加条件。</span><span class="sxs-lookup"><span data-stu-id="3c962-129">Click the **AND/OR** text box in the next row of the grid to add a condition.</span></span>  
  
     <span data-ttu-id="3c962-130">例如，若要创建 BETWEEN 条件，请 `AND` 从逻辑操作数下拉列表中选择。</span><span class="sxs-lookup"><span data-stu-id="3c962-130">For example, to create a BETWEEN condition, select `AND` from the drop-down list of logical operands.</span></span>  
  
11. <span data-ttu-id="3c962-131">按步骤 7 和 8 中所述选择一个运算符并键入一个值。</span><span class="sxs-lookup"><span data-stu-id="3c962-131">Select an operator and type a value as described in Steps 7 and 8.</span></span>  
  
     <span data-ttu-id="3c962-132">例如，再次选择 `Income` 作为列，选择小于运算符 ( # A0) ，然后键入 `40000` 。</span><span class="sxs-lookup"><span data-stu-id="3c962-132">For example, select `Income` as the column again, select the less than operator (<), and then type `40000`.</span></span>  
  
12. <span data-ttu-id="3c962-133">单击网格中的下一行。</span><span class="sxs-lookup"><span data-stu-id="3c962-133">Click the next row in the grid.</span></span>  
  
13. <span data-ttu-id="3c962-134">“表达式”文本框中的筛选条件自动更新以包含新的条件。</span><span class="sxs-lookup"><span data-stu-id="3c962-134">The filter condition in the Expression text box is automatically updated to include the new condition.</span></span> <span data-ttu-id="3c962-135">完成的表达式如下： `[Income] > '30000'AND [Income] < '40000'`</span><span class="sxs-lookup"><span data-stu-id="3c962-135">The completed expression is as follows: `[Income] > '30000'AND [Income] < '40000'`</span></span>  
  
### <a name="to-add-a-filter-on-the-nested-table-in-a-mining-model"></a><span data-ttu-id="3c962-136">向挖掘模型中的嵌套表添加筛选器</span><span class="sxs-lookup"><span data-stu-id="3c962-136">To add a filter on the nested table in a mining model</span></span>  
  
1.  <span data-ttu-id="3c962-137">在 " \*\* \<name> 模型筛选器**" 对话框中，单击 "**挖掘结构列\*\*" 下网格中的空行。</span><span class="sxs-lookup"><span data-stu-id="3c962-137">In the **\<name>Model Filter** Dialog box, click an empty row in the grid under **Mining Structure Column**.</span></span>  
  
2.  <span data-ttu-id="3c962-138">从下拉列表中选择嵌套表的名称。</span><span class="sxs-lookup"><span data-stu-id="3c962-138">Select the name of the nested table from the drop-down list.</span></span>  
  
     <span data-ttu-id="3c962-139">文本框左侧的图标会发生改变，以指示所选项是表名称。</span><span class="sxs-lookup"><span data-stu-id="3c962-139">The icon at the left side of the text box changes to indicate that the selected item is the name of a table.</span></span>  
  
3.  <span data-ttu-id="3c962-140">单击 **“运算符”** 文本框，然后选择 **“包含”** 或 **“不包含”**。</span><span class="sxs-lookup"><span data-stu-id="3c962-140">Click the **Operator** text box and select **Contains** or **Not Contain**.</span></span>  
  
     <span data-ttu-id="3c962-141">在 **“模型筛选器”** 对话框中，只有这些条件可用于嵌套表，因为您要将事例表限定为包含嵌套表中某一特定值的那些事例。</span><span class="sxs-lookup"><span data-stu-id="3c962-141">These are the only conditions available for the nested table in the **Model Filter** dialog box, because you are restricting the case table to only those cases that contain a certain value in the nested table.</span></span> <span data-ttu-id="3c962-142">在下一步中，您将设置嵌套表条件的值。</span><span class="sxs-lookup"><span data-stu-id="3c962-142">You will set the value for the condition on the nested table in the next step.</span></span>  
  
4.  <span data-ttu-id="3c962-143">单击 "**值**" 框，然后单击 " \*\* ( ..." ) \*\*按钮以生成表达式。</span><span class="sxs-lookup"><span data-stu-id="3c962-143">Click the **Value** box, and then click the **(...)** button to build an expression.</span></span>  
  
     <span data-ttu-id="3c962-144">此时将打开 " \*\* \<name> 筛选器\*\*" 对话框。</span><span class="sxs-lookup"><span data-stu-id="3c962-144">The **\<name>Filter** dialog box opens.</span></span> <span data-ttu-id="3c962-145">此对话框只能设置当前表的条件，本例中当前表是嵌套表。</span><span class="sxs-lookup"><span data-stu-id="3c962-145">This dialog box can set conditions only on the current table, which in this case is the nested table.</span></span>  
  
5.  <span data-ttu-id="3c962-146">单击 **“挖掘结构列”** 框并从嵌套表列下拉列表中选择一个列名。</span><span class="sxs-lookup"><span data-stu-id="3c962-146">Click the **Mining Structure Column** box and select a column name from the dropdown lists of nested table columns.</span></span>  
  
6.  <span data-ttu-id="3c962-147">单击 **“运算符”** 并从该列的有效运算符列表中选择一个运算符。</span><span class="sxs-lookup"><span data-stu-id="3c962-147">Click **Operator** and select an operator from the list of valid operators for the column.</span></span>  
  
7.  <span data-ttu-id="3c962-148">单击 **“值”** 并键入一个值。</span><span class="sxs-lookup"><span data-stu-id="3c962-148">Click **Value** and type a value.</span></span>  
  
     <span data-ttu-id="3c962-149">例如，对于 "**挖掘结构列"，** 选择 `Model` 。</span><span class="sxs-lookup"><span data-stu-id="3c962-149">For example, for **Mining Structure Column,** select `Model`.</span></span> <span data-ttu-id="3c962-150">对于 "**运算符**"，选择 `<>` ，然后键入值 `Water Bottle` 。</span><span class="sxs-lookup"><span data-stu-id="3c962-150">For **Operator**, select `<>`, and type the value `Water Bottle`.</span></span> <span data-ttu-id="3c962-151">此条件将创建如下的筛选表达式：</span><span class="sxs-lookup"><span data-stu-id="3c962-151">This condition creates the following filter expression:</span></span>  
  
```  
EXISTS (SELECT * FROM [<nested table name>] WHERE [Model] <> 'Water Bottle' )   
```  
  
> [!NOTE]  
>  <span data-ttu-id="3c962-152">由于嵌套表数属性的数量不受限制，因此， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 不提供可供选择的可能值的列表。</span><span class="sxs-lookup"><span data-stu-id="3c962-152">Because the number of nested table attributes is potentially unlimited, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] does not supply a list of possible values from which to select.</span></span> <span data-ttu-id="3c962-153">必须键入一个确切的值。</span><span class="sxs-lookup"><span data-stu-id="3c962-153">You must type the exact value.</span></span> <span data-ttu-id="3c962-154">此外，不能在嵌套表中使用 LIKE 运算符。</span><span class="sxs-lookup"><span data-stu-id="3c962-154">Also, you cannot use a LIKE operator in a nested table.</span></span>  
  
1.  <span data-ttu-id="3c962-155">根据需要添加更多条件， `AND` `OR` 并通过在 "**条件**" 网格左侧的 "**和/或**" 框中选择或来组合条件。</span><span class="sxs-lookup"><span data-stu-id="3c962-155">Add more conditions as necessary, combining the conditions by selecting `AND` or `OR` in the **AND/OR** box at the left side of the **Conditions** grid.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
2.  <span data-ttu-id="3c962-156">在 **“模型筛选器”** 对话框中，使用 **“筛选器”** 对话框检查创建的条件。</span><span class="sxs-lookup"><span data-stu-id="3c962-156">In the **Model Filter** dialog box, review the conditions that you created by using the **Filter** dialog box.</span></span> <span data-ttu-id="3c962-157">嵌套表的条件表将附加到事例表条件中，并在 **“表达式”** 文本框中显示一组完整的筛选条件。</span><span class="sxs-lookup"><span data-stu-id="3c962-157">The conditions for the nested table are appended to the conditions for the case table, and the complete set of filter conditions is displayed in the **Expression** text box.</span></span>  
  
3.  <span data-ttu-id="3c962-158">（可选）单击 **“编辑查询”** 以手动更改筛选表达式。</span><span class="sxs-lookup"><span data-stu-id="3c962-158">Optionally, click **Edit Query** to manually change the filter expression.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3c962-159">如果手动更改筛选表达式的任意部分，则会禁用该网格，以后只能在文本编辑模式下编辑筛选表达式。</span><span class="sxs-lookup"><span data-stu-id="3c962-159">If you change any part of a filter expression manually, the grid will be disabled and thereafter you must work with the filter expression in text edit mode only.</span></span> <span data-ttu-id="3c962-160">若要恢复网格编辑模式，必须清除筛选表达式并重新开始。</span><span class="sxs-lookup"><span data-stu-id="3c962-160">To restore grid editing mode, you must clear the filter expression and start over.</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="3c962-161">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3c962-161">See Also</span></span>  
 <span data-ttu-id="3c962-162">[挖掘模型的筛选器 &#40;Analysis Services 数据挖掘&#41;](mining-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="3c962-162">[Filters for Mining Models &#40;Analysis Services - Data Mining&#41;](mining-models-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="3c962-163">[挖掘模型任务和操作指南](mining-model-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="3c962-163">[Mining Model Tasks and How-tos](mining-model-tasks-and-how-tos.md) </span></span>  
 [<span data-ttu-id="3c962-164">从挖掘模型中删除筛选器</span><span class="sxs-lookup"><span data-stu-id="3c962-164">Delete a Filter from a Mining Model</span></span>](delete-a-filter-from-a-mining-model.md)  
  
  
