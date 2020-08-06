---
title: " (基本数据挖掘教程) 创建预测 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a8410ed2-bb98-4d51-a9eb-b239be1201c2
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 456aec6c6b9d0d1a5d0ee1d9949507a37577130c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682472"
---
# <a name="creating-predictions-basic-data-mining-tutorial"></a><span data-ttu-id="b3607-102">创建预测（数据挖掘基础教程）</span><span class="sxs-lookup"><span data-stu-id="b3607-102">Creating Predictions (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="b3607-103">在您测试了挖掘模型的准确性并确定您对结果感到满意后，就可以使用数据挖掘设计器中 "**挖掘模型预测**" 选项卡上的预测查询生成器来生成预测。</span><span class="sxs-lookup"><span data-stu-id="b3607-103">After you have tested the accuracy of your mining models and decided that you are satisfied with the results, you can then generate predictions by using the Prediction Query Builder on the **Mining Model Prediction** tab in the Data Mining Designer.</span></span>  
  
 <span data-ttu-id="b3607-104">预测查询生成器有三个视图。</span><span class="sxs-lookup"><span data-stu-id="b3607-104">The Prediction Query Builder has three views.</span></span> <span data-ttu-id="b3607-105">利用 "**设计**" 和 "**查询**" 视图，您可以生成并检查查询。</span><span class="sxs-lookup"><span data-stu-id="b3607-105">With the **Design** and **Query** views, you can build and examine your query.</span></span> <span data-ttu-id="b3607-106">然后，您可以运行查询并在 "**结果**" 视图中查看结果。</span><span class="sxs-lookup"><span data-stu-id="b3607-106">You can then run the query and view the results in the **Result** view.</span></span>  
  
 <span data-ttu-id="b3607-107">所有预测查询均使用 DMX，DMX 是数据挖掘扩展 (DMX) 语言的简称。</span><span class="sxs-lookup"><span data-stu-id="b3607-107">All prediction queries use DMX, which is short for the Data Mining Extensions (DMX) language.</span></span> <span data-ttu-id="b3607-108">DMX 的语法与 T-SQL 的语法相似，但用于对数据挖掘对象的查询。</span><span class="sxs-lookup"><span data-stu-id="b3607-108">DMX has syntax like that of T-SQL but is used for queries against data mining objects.</span></span> <span data-ttu-id="b3607-109">尽管 DMX 语法不复杂，但使用与此类似的查询生成器，或者使用[SQL Server Office 数据挖掘外接程序](../../2014/analysis-services/data-mining/sql-server-data-mining-add-ins-for-office.md)中的查询生成器，因此，我们强烈建议你了解基础知识。</span><span class="sxs-lookup"><span data-stu-id="b3607-109">Although DMX syntax is not complicated, using a query builder like this one, or the one in the [SQL Server Data Mining Add-Ins for Office](../../2014/analysis-services/data-mining/sql-server-data-mining-add-ins-for-office.md), makes it much easier to select inputs and build expressions, so we highly recommend that you learn the basics.</span></span>  
  
## <a name="creating-the-query"></a><span data-ttu-id="b3607-110">创建查询</span><span class="sxs-lookup"><span data-stu-id="b3607-110">Creating the Query</span></span>  
 <span data-ttu-id="b3607-111">创建预测查询的第一步是选择挖掘模型和输入表。</span><span class="sxs-lookup"><span data-stu-id="b3607-111">The first step in creating a prediction query is to select a mining model and input table.</span></span>  
  
#### <a name="to-select-a-model-and-input-table"></a><span data-ttu-id="b3607-112">选择模型和输入表</span><span class="sxs-lookup"><span data-stu-id="b3607-112">To select a model and input table</span></span>  
  
1.  <span data-ttu-id="b3607-113">在数据挖掘设计器的 "**挖掘模型预测**" 选项卡上的 "**挖掘模型**" 框中，单击 "**选择模型**"。</span><span class="sxs-lookup"><span data-stu-id="b3607-113">On the **Mining Model Prediction** tab of Data Mining Designer, in the **Mining Model** box, click **Select Model**.</span></span>  
  
2.  <span data-ttu-id="b3607-114">在 "**选择挖掘模型**" 对话框中，在树中导航到**目标邮件**结构，展开结构，选择 `TM_Decision_Tree` ，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="b3607-114">In the **Select Mining Model** dialog box, navigate through the tree to the **Targeted Mailing** structure, expand the structure, select `TM_Decision_Tree`, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="b3607-115">在 "**选择输入表 (s) **中，单击"**选择事例表**"。</span><span class="sxs-lookup"><span data-stu-id="b3607-115">In the **Select Input Table(s)** box, click **Select Case Table**.</span></span>  
  
4.  <span data-ttu-id="b3607-116">在 "**选择表**" 对话框的 "**数据源**" 列表中，选择数据源视图 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="b3607-116">In the **Select Table** dialog box, in the **Data Source** list, select the data source view [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)].</span></span>  
  
5.  <span data-ttu-id="b3607-117">在 "**表/视图名称**" 中，选择\*\*ProspectiveBuyer (dbo) \*\*表，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="b3607-117">In **Table/View Name**, select the **ProspectiveBuyer (dbo)** table, and then click **OK**.</span></span>  
  
     <span data-ttu-id="b3607-118">`ProspectiveBuyer`该表最接近于**vTargetMail**事例表。</span><span class="sxs-lookup"><span data-stu-id="b3607-118">The `ProspectiveBuyer` table most closely resembles the **vTargetMail** case table.</span></span>  
  
## <a name="mapping-the-columns"></a><span data-ttu-id="b3607-119">映射列</span><span class="sxs-lookup"><span data-stu-id="b3607-119">Mapping the Columns</span></span>  
 <span data-ttu-id="b3607-120">选择输入表之后，预测查询生成器便会根据各列的名称在挖掘模型和输入表之间创建默认映射。</span><span class="sxs-lookup"><span data-stu-id="b3607-120">After you select the input table, Prediction Query Builder creates a default mapping between the mining model and the input table, based on the names of the columns.</span></span> <span data-ttu-id="b3607-121">结构中至少有一列必须与外部数据中的某列相匹配。</span><span class="sxs-lookup"><span data-stu-id="b3607-121">At least one column from the structure must match a column in the external data.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b3607-122">用于确定模型准确性的数据必须包含一个可以映射到可预测列的列。</span><span class="sxs-lookup"><span data-stu-id="b3607-122">The data that you use to determine the accuracy of the models must contain a column that can be mapped to the predictable column.</span></span> <span data-ttu-id="b3607-123">如果不存在这种列，您可以使用空值创建一列，但该列的数据类型必须与可预测列相同。</span><span class="sxs-lookup"><span data-stu-id="b3607-123">If such a column does not exist, you can create one with empty values, but it must have the same data type as the predictable column.</span></span>  
  
#### <a name="to-map-the-inputs-to-the-model"></a><span data-ttu-id="b3607-124">将输入内容映射到模型</span><span class="sxs-lookup"><span data-stu-id="b3607-124">To map the inputs to the model</span></span>  
  
1.  <span data-ttu-id="b3607-125">右键单击将 "**挖掘模型**" 窗口连接到 "**选择输入表**" 窗口的行，然后选择 "**修改连接**"。</span><span class="sxs-lookup"><span data-stu-id="b3607-125">Right-click the lines connecting the **Mining Model** window to the **Select Input Table** window, and select **Modify Connections**.</span></span>  
  
     <span data-ttu-id="b3607-126">请注意，并非每个列都映射。</span><span class="sxs-lookup"><span data-stu-id="b3607-126">Notice that not every column is mapped.</span></span> <span data-ttu-id="b3607-127">我们将为多个**表列**添加映射。</span><span class="sxs-lookup"><span data-stu-id="b3607-127">We will add mappings for several **Table Columns**.</span></span> <span data-ttu-id="b3607-128">我们还将基于当前的日期列生成新的出生日期列，以便更好地匹配列。</span><span class="sxs-lookup"><span data-stu-id="b3607-128">We will also generate a new birth date column based on the current date column, so that the columns match better.</span></span>  
  
2.  <span data-ttu-id="b3607-129">在 "**表列**" 下，单击 `Bike Buyer` 单元格，然后从下拉列表中选择 "ProspectiveBuyer"。</span><span class="sxs-lookup"><span data-stu-id="b3607-129">Under **Table Column**, click the `Bike Buyer` cell and select ProspectiveBuyer.Unknown from the dropdown.</span></span>  
  
     <span data-ttu-id="b3607-130">这样便将可预测列 [Bike Buyer] 映射到一个输入表列。</span><span class="sxs-lookup"><span data-stu-id="b3607-130">This maps the predictable column, [Bike Buyer], to an input table column.</span></span>  
  
3.  <span data-ttu-id="b3607-131">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="b3607-131">Click **OK**.</span></span>  
  
4.  <span data-ttu-id="b3607-132">在**解决方案资源管理器**中，右键单击**目标邮件**数据源视图，然后选择 "**视图设计器**"。</span><span class="sxs-lookup"><span data-stu-id="b3607-132">In **Solution Explorer**, right-click the **Targeted Mailing** data source view and select **View Designer**.</span></span>  
  
5.  <span data-ttu-id="b3607-133">右键单击表 ProspectiveBuyer，然后选择 "**新建命名计算**"。</span><span class="sxs-lookup"><span data-stu-id="b3607-133">Right-click the table, ProspectiveBuyer, and select **New Named Calculation**.</span></span>  
  
6.  <span data-ttu-id="b3607-134">在 "**创建命名计算**" 对话框中，键入 "**列名称**" `calcAge` 。</span><span class="sxs-lookup"><span data-stu-id="b3607-134">In the **Create Named Calculation** dialog box, for **Column name**, type `calcAge`.</span></span>  
  
7.  <span data-ttu-id="b3607-135">对于 "**说明**"，键入**基于生日计算年龄**。</span><span class="sxs-lookup"><span data-stu-id="b3607-135">For **Description**, type **Calculate age based on birthdate**.</span></span>  
  
8.  <span data-ttu-id="b3607-136">在 "**表达式**" 框中键入， `DATEDIFF(YYYY,[BirthDate],getdate())` 然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="b3607-136">In the **Expression** box, type `DATEDIFF(YYYY,[BirthDate],getdate())` and then click **OK**.</span></span>  
  
     <span data-ttu-id="b3607-137">由于输入表中没有**Age**列对应于模型中的列，因此您可以使用此表达式来计算输入表中 "出生日期" 列的客户年龄。</span><span class="sxs-lookup"><span data-stu-id="b3607-137">Because the input table has no **Age** column corresponding to the one in the model, you can use this expression to calculate customer age from the BirthDate column in the input table.</span></span> <span data-ttu-id="b3607-138">由于**Age**被标识为预测自行车购买的最具影响力的列，因此它必须同时存在于模型和输入表中。</span><span class="sxs-lookup"><span data-stu-id="b3607-138">Since **Age** was identified as the most influential column for predicting bike buying, it must exist in both the model and in the input table.</span></span>  
  
9. <span data-ttu-id="b3607-139">在数据挖掘设计器中，选择 "**挖掘模型预测**" 选项卡，然后重新打开 "**修改连接**" 窗口。</span><span class="sxs-lookup"><span data-stu-id="b3607-139">In Data Mining Designer, select the **Mining Model Prediction** tab and re-open the **Modify Connections** window.</span></span>  
  
10. <span data-ttu-id="b3607-140">在 "**表列**" 下，单击 " **Age** " 单元格，然后从下拉列表中选择 "ProspectiveBuyer"。</span><span class="sxs-lookup"><span data-stu-id="b3607-140">Under **Table Column**, click the **Age** cell and select ProspectiveBuyer.calcAge from the dropdown.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="b3607-141">如果看不到列表中的列，则可能必须刷新设计器中加载的数据源视图的定义。</span><span class="sxs-lookup"><span data-stu-id="b3607-141">If you do not see the column in the list, you might have to refresh the definition of the data source view that is loaded in the designer.</span></span> <span data-ttu-id="b3607-142">为此，请在 "**文件**" 菜单中选择 "**全部保存**"，然后关闭并重新打开设计器中的项目。</span><span class="sxs-lookup"><span data-stu-id="b3607-142">To do this, from the **File** menu, select **Save all**, and then close and re-open the project in the designer.</span></span>  
  
11. <span data-ttu-id="b3607-143">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="b3607-143">Click **OK**.</span></span>  
  
## <a name="designing-the-prediction-query"></a><span data-ttu-id="b3607-144">设计预测查询</span><span class="sxs-lookup"><span data-stu-id="b3607-144">Designing the Prediction Query</span></span>  
  
1.  <span data-ttu-id="b3607-145">"**挖掘模型预测**" 选项卡的工具栏上的第一个按钮是 "**设计视图"/"切换到结果视图"/"切换到查询视图**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="b3607-145">The first button on the toolbar of the **Mining Model Prediction** tab is the **Switch to design view / Switch to result view / Switch to query view** button.</span></span> <span data-ttu-id="b3607-146">单击此按钮上的向下箭头，然后选择 "**设计**"。</span><span class="sxs-lookup"><span data-stu-id="b3607-146">Click the down arrow on this button, and select **Design**.</span></span>  
  
2.  <span data-ttu-id="b3607-147">在 "**挖掘模型预测**" 选项卡上的网格中，单击 "**源**" 列中第一个空行中的单元，然后选择 "**预测函数**"。</span><span class="sxs-lookup"><span data-stu-id="b3607-147">In the grid on the **Mining Model Prediction** tab, click the cell in the first empty row in the **Source** column, and then select **Prediction Function**.</span></span>  
  
3.  <span data-ttu-id="b3607-148">在**预测函数**行的 "**字段**" 列中，选择 `PredictProbability` 。</span><span class="sxs-lookup"><span data-stu-id="b3607-148">In the **Prediction Function** row, in the **Field** column, select `PredictProbability`.</span></span>  
  
     <span data-ttu-id="b3607-149">在同一行的 "**别名**" 列中，键入**result 的概率**。</span><span class="sxs-lookup"><span data-stu-id="b3607-149">In the **Alias** column of the same row, type **Probability of result**.</span></span>  
  
4.  <span data-ttu-id="b3607-150">在上面的 "**挖掘模型**" 窗口中，选择 "[自行车购买者]" 并将其拖到 "**条件/参数**" 单元中。</span><span class="sxs-lookup"><span data-stu-id="b3607-150">From the **Mining Model** window above, select and drag [Bike Buyer] into the **Criteria/Argument** cell.</span></span>  
  
     <span data-ttu-id="b3607-151">当你开始时，[TM_Decision_Tree]。[自行车购买者] 出现在 "**条件/参数**" 单元中。</span><span class="sxs-lookup"><span data-stu-id="b3607-151">When you let go, [TM_Decision_Tree].[Bike Buyer] appears in the **Criteria/Argument** cell.</span></span>  
  
     <span data-ttu-id="b3607-152">这将指定 `PredictProbability` 函数的目标列。</span><span class="sxs-lookup"><span data-stu-id="b3607-152">This specifies the target column for the `PredictProbability` function.</span></span> <span data-ttu-id="b3607-153">有关函数的详细信息，请参阅[数据挖掘扩展插件 &#40;DMX&#41; 函数引用](/sql/dmx/data-mining-extensions-dmx-function-reference)。</span><span class="sxs-lookup"><span data-stu-id="b3607-153">For more information about functions, see [Data Mining Extensions &#40;DMX&#41; Function Reference](/sql/dmx/data-mining-extensions-dmx-function-reference).</span></span>  
  
5.  <span data-ttu-id="b3607-154">单击 "**源**" 列中的下一个空行，然后选择**TM_Decision_Tree**挖掘模型 "。</span><span class="sxs-lookup"><span data-stu-id="b3607-154">Click the next empty row in the **Source** column, and then select **TM_Decision_Tree** mining model.</span></span>  
  
6.  <span data-ttu-id="b3607-155">在行的 " `TM_Decision_Tree` **字段**" 列中，选择 `Bike Buyer` 。</span><span class="sxs-lookup"><span data-stu-id="b3607-155">In the `TM_Decision_Tree` row, in the **Field** column, select `Bike Buyer`.</span></span>  
  
7.  <span data-ttu-id="b3607-156">在 `TM_Decision_Tree` 行的 "**条件/参数**" 列中，键入 `=1` 。</span><span class="sxs-lookup"><span data-stu-id="b3607-156">In the `TM_Decision_Tree` row, in the **Criteria/Argument** column, type `=1`.</span></span>  
  
8.  <span data-ttu-id="b3607-157">单击 "**源**" 列中的下一个空行，然后选择 " **ProspectiveBuyer 表**"。</span><span class="sxs-lookup"><span data-stu-id="b3607-157">Click the next empty row in the **Source** column, and then select **ProspectiveBuyer table**.</span></span>  
  
9. <span data-ttu-id="b3607-158">在行的 " `ProspectiveBuyer` **字段**" 列中，选择 " **ProspectiveBuyerKey**"。</span><span class="sxs-lookup"><span data-stu-id="b3607-158">In the `ProspectiveBuyer` row, in the **Field** column, select **ProspectiveBuyerKey**.</span></span>  
  
     <span data-ttu-id="b3607-159">这会将唯一标识符添加到预测查询中，以便您可以标识谁可能购买自行车，以及谁不可能购买自行车。</span><span class="sxs-lookup"><span data-stu-id="b3607-159">This adds the unique identifier to the prediction query so that you can identify who is and who is not likely to buy a bicycle.</span></span>  
  
10. <span data-ttu-id="b3607-160">向网格中添加五个以上的行。</span><span class="sxs-lookup"><span data-stu-id="b3607-160">Add five more rows to the grid.</span></span> <span data-ttu-id="b3607-161">对于每一行，选择 " **ProspectiveBuyer 表**" 作为**源**，然后在 "**字段**" 单元格中添加以下列：</span><span class="sxs-lookup"><span data-stu-id="b3607-161">For each row, select **ProspectiveBuyer table** as the **Source** and then add the following columns in the **Field** cells:</span></span>  
  
    -   <span data-ttu-id="b3607-162">calcAge</span><span class="sxs-lookup"><span data-stu-id="b3607-162">calcAge</span></span>  
  
    -   <span data-ttu-id="b3607-163">LastName</span><span class="sxs-lookup"><span data-stu-id="b3607-163">LastName</span></span>  
  
    -   <span data-ttu-id="b3607-164">FirstName</span><span class="sxs-lookup"><span data-stu-id="b3607-164">FirstName</span></span>  
  
    -   <span data-ttu-id="b3607-165">AddressLine1</span><span class="sxs-lookup"><span data-stu-id="b3607-165">AddressLine1</span></span>  
  
    -   <span data-ttu-id="b3607-166">AddressLine2</span><span class="sxs-lookup"><span data-stu-id="b3607-166">AddressLine2</span></span>  
  
 <span data-ttu-id="b3607-167">最后，运行查询并浏览结果。</span><span class="sxs-lookup"><span data-stu-id="b3607-167">Finally, run the query and browse the results.</span></span>  
  
 <span data-ttu-id="b3607-168">**预测查询生成器**还包括以下控件：</span><span class="sxs-lookup"><span data-stu-id="b3607-168">The **Prediction Query Builder** also includes these controls:</span></span>  
  
-   <span data-ttu-id="b3607-169">**显示**复选框</span><span class="sxs-lookup"><span data-stu-id="b3607-169">**Show** check box</span></span>  
  
     <span data-ttu-id="b3607-170">可以允许您从查询中移除子句而不从设计器中删除它们。</span><span class="sxs-lookup"><span data-stu-id="b3607-170">Lets you remove clauses from the query without having to delete them from the designer.</span></span> <span data-ttu-id="b3607-171">当您使用复杂查询并想要保留语法而不必将 DMX 复制和粘贴到窗口时，这很有用。</span><span class="sxs-lookup"><span data-stu-id="b3607-171">This can be useful when you are working with complex queries and want to preserve syntax without having to copy and paste DMX into the window.</span></span>  
  
-   <span data-ttu-id="b3607-172">**组**</span><span class="sxs-lookup"><span data-stu-id="b3607-172">**Group**</span></span>  
  
     <span data-ttu-id="b3607-173">在所选行的开头插入一个左括号，或在当前行的结尾插入一个右括号。</span><span class="sxs-lookup"><span data-stu-id="b3607-173">Inserts an opening (left) parentheses at the beginning of the selected line, or inserts a closing (right) parenthesis at the end of the current line.</span></span>  
  
-   <span data-ttu-id="b3607-174">**AND/OR**</span><span class="sxs-lookup"><span data-stu-id="b3607-174">**AND/OR**</span></span>  
  
     <span data-ttu-id="b3607-175">在紧挨当前函数或列后面插入 `AND` 或 `OR` 运算符。</span><span class="sxs-lookup"><span data-stu-id="b3607-175">Inserts the  `AND` operator or the `OR` operator immediately after the current function or column.</span></span>  
  
#### <a name="to-run-the-query-and-view-results"></a><span data-ttu-id="b3607-176">运行查询并查看结果</span><span class="sxs-lookup"><span data-stu-id="b3607-176">To run the query and view results</span></span>  
  
1.  <span data-ttu-id="b3607-177">在 "**挖掘模型预测**" 选项卡中，选择 "**结果**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="b3607-177">In the **Mining Model Prediction** tab, select the **Result** button.</span></span>  
  
2.  <span data-ttu-id="b3607-178">运行查询并显示结果后，您可以查看结果。</span><span class="sxs-lookup"><span data-stu-id="b3607-178">After the query runs and the results are displayed, you can review the results.</span></span>  
  
     <span data-ttu-id="b3607-179">"**挖掘模型预测**" 选项卡显示可能为自行车购买者的潜在客户的联系信息。</span><span class="sxs-lookup"><span data-stu-id="b3607-179">The **Mining Model Prediction** tab displays contact information for potential customers who are likely to be bike buyers.</span></span> <span data-ttu-id="b3607-180">Result 列的**概率**表示预测正确的概率。</span><span class="sxs-lookup"><span data-stu-id="b3607-180">The **Probability of result** column indicates the probability of the prediction being correct.</span></span> <span data-ttu-id="b3607-181">您可以使用这些结果来确定向哪些潜在客户发送电子邮件。</span><span class="sxs-lookup"><span data-stu-id="b3607-181">You can use these results to determine which potential customers to target for the mailing.</span></span>  
  
3.  <span data-ttu-id="b3607-182">此时您可以保存结果。</span><span class="sxs-lookup"><span data-stu-id="b3607-182">At this point, you can save the results.</span></span> <span data-ttu-id="b3607-183">您有三种选择：</span><span class="sxs-lookup"><span data-stu-id="b3607-183">You have three options:</span></span>  
  
    -   <span data-ttu-id="b3607-184">右键单击结果中的行数据，然后选择 "**复制**"，只保存该值 (并且列标题) 到剪贴板。</span><span class="sxs-lookup"><span data-stu-id="b3607-184">Right-click a row of data in the results, and select **Copy** to save just that value (and the column heading) to the Clipboard.</span></span>  
  
    -   <span data-ttu-id="b3607-185">右键单击结果中的任何行，然后选择 "**全部复制**" 以将整个结果集（包括列标题）复制到剪贴板。</span><span class="sxs-lookup"><span data-stu-id="b3607-185">Right-click any row in the results, and select **Copy All** to copy the entire result set, including column headings, to the Clipboard.</span></span>  
  
    -   <span data-ttu-id="b3607-186">单击 "**保存查询结果**" 将结果直接保存到数据库，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b3607-186">Click **Save query result** to save the results directly to a database as follows:</span></span>  
  
        1.  <span data-ttu-id="b3607-187">在 "**保存数据挖掘查询结果**" 对话框中，选择数据源或定义新的数据源。</span><span class="sxs-lookup"><span data-stu-id="b3607-187">In the **Save Data Mining Query Result** dialog box, select a data source, or define a new data source.</span></span>  
  
        2.  <span data-ttu-id="b3607-188">键入将包含查询结果的表的名称。 </span><span class="sxs-lookup"><span data-stu-id="b3607-188">Type a name for the table that will contain the query results.</span></span>  
  
        3.  <span data-ttu-id="b3607-189">使用选项 "**添加到 DSV**" 创建表并将其添加到现有数据源视图。</span><span class="sxs-lookup"><span data-stu-id="b3607-189">Use the option, **Add to DSV**, to create the table and add it to an existing data source view.</span></span> <span data-ttu-id="b3607-190">如果要在同一数据源视图中保留模型的所有相关表（如定型数据、预测源数据和查询结果），此方法很有用。</span><span class="sxs-lookup"><span data-stu-id="b3607-190">This is useful if you want to keep all related tables for a model-such as training data, prediction source data, and query results-in the same data source view.</span></span>  
  
        4.  <span data-ttu-id="b3607-191">使用 "**如果存在，则覆盖**" 选项来更新具有最新结果的现有表。</span><span class="sxs-lookup"><span data-stu-id="b3607-191">Use the option, **Overwrite if exists**, to update an existing table with the latest results.</span></span>  
  
             <span data-ttu-id="b3607-192">如果您将任何列添加到了预测查询、更改了预测查询中任何列的名称或数据类型，或者对目标表运行了任何 ALTER 语句，必须使用此选项来覆盖表。</span><span class="sxs-lookup"><span data-stu-id="b3607-192">You must use the option to overwrite the table if you have added any columns to the prediction query, changed the names or data types of any columns in the prediction query, or if you have run any ALTER statements on the destination table.</span></span>  
  
             <span data-ttu-id="b3607-193">此外，如果多个列具有相同的名称 (例如，默认的列名**表达式**) 您必须为具有重复名称的列创建一个别名，否则当设计器尝试将结果保存到 SQL Server 时将引发错误。</span><span class="sxs-lookup"><span data-stu-id="b3607-193">Also, if multiple columns have the same name (for example, the default column name **Expression**) you must create an alias for the columns with duplicate names, or an error will be raised when the designer tries to save the results to SQL Server.</span></span> <span data-ttu-id="b3607-194">原因是 SQL Server 不允许多个列具有相同的名称。</span><span class="sxs-lookup"><span data-stu-id="b3607-194">The reason is that SQL Server does not allow multiple columns to have the same name.</span></span>  
  
             <span data-ttu-id="b3607-195">有关详细信息，请参阅 "[将数据挖掘查询结果保存到 &#40;挖掘模型预测" 视图&#41;](../../2014/analysis-services/save-data-mining-query-result-dialog-box-mining-model-prediction-view.md)。</span><span class="sxs-lookup"><span data-stu-id="b3607-195">For more information, see [Save Data Mining Query Result Dialog Box &#40;Mining Model Prediction View&#41;](../../2014/analysis-services/save-data-mining-query-result-dialog-box-mining-model-prediction-view.md).</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="b3607-196">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="b3607-196">Next Task in Lesson</span></span>  
 [<span data-ttu-id="b3607-197">对结构数据使用钻取 &#40;基本数据挖掘教程&#41;</span><span class="sxs-lookup"><span data-stu-id="b3607-197">Using Drillthrough on Structure Data &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/using-drillthrough-on-structure-data-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="b3607-198">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b3607-198">See Also</span></span>  
 [<span data-ttu-id="b3607-199">使用预测查询生成器创建预测查询</span><span class="sxs-lookup"><span data-stu-id="b3607-199">Create a Prediction Query Using the Prediction Query Builder</span></span>](../../2014/analysis-services/data-mining/create-a-prediction-query-using-the-prediction-query-builder.md)  
  
  
