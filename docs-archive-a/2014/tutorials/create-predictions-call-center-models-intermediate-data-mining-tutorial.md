---
title: " (中级数据挖掘教程) 中为呼叫中心模型创建预测Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5be0cec7-f639-4eeb-835e-e3204ae619e9
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: c2d402fb9f6509292442f31f85478b0612a45d56
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579449"
---
# <a name="creating-predictions-for-the-call-center-models-intermediate-data-mining-tutorial"></a><span data-ttu-id="9d74e-102">为呼叫中心模型创建预测（数据挖掘中级教程）</span><span class="sxs-lookup"><span data-stu-id="9d74e-102">Creating Predictions for the Call Center Models (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="9d74e-103">现在您已经了解了关于班次、操作员人数、呼叫和服务等级之间的交互，您将准备创建一些可用于业务分析和规划的预测查询。</span><span class="sxs-lookup"><span data-stu-id="9d74e-103">Now that you have learned something about the interactions between shifts, the number of operators, calls, and service grade, you are ready to create some prediction queries that can be used in business analysis and planning.</span></span> <span data-ttu-id="9d74e-104">首先您将在探索模型上创建一些预测来测试某些假设。</span><span class="sxs-lookup"><span data-stu-id="9d74e-104">You will first create some predictions on the exploratory model to test some assumptions.</span></span> <span data-ttu-id="9d74e-105">接下来，您将通过使用逻辑回归模型创建大容量预测。</span><span class="sxs-lookup"><span data-stu-id="9d74e-105">Next, you will create bulk predictions by using the logistic regression model.</span></span>  
  
 <span data-ttu-id="9d74e-106">本课假定您已经熟悉预测查询的概念。</span><span class="sxs-lookup"><span data-stu-id="9d74e-106">This lesson assumes that you are already familiar with the concept of prediction queries.</span></span>  
  
## <a name="creating-predictions-using-the-neural-network-model"></a><span data-ttu-id="9d74e-107">使用神经网络模型创建预测</span><span class="sxs-lookup"><span data-stu-id="9d74e-107">Creating Predictions using the Neural Network Model</span></span>  
 <span data-ttu-id="9d74e-108">下面的示例演示如何使用为探索阶段创建的神经网络模型进行单独预测。</span><span class="sxs-lookup"><span data-stu-id="9d74e-108">The following example demonstrates how to make a singleton prediction using the neural network model that was created for exploration.</span></span> <span data-ttu-id="9d74e-109">单独预测是试用不同的值以在模型中查看效果的好办法。</span><span class="sxs-lookup"><span data-stu-id="9d74e-109">Singleton predictions are a good way to try out different values to see the effect in the model.</span></span> <span data-ttu-id="9d74e-110">在此方案中，如果六个经验丰富的操作员值夜班，您将预测该夜班的服务等级（未指定星期几）。</span><span class="sxs-lookup"><span data-stu-id="9d74e-110">In this scenario, you will predict the service grade for the midnight shift (no day of the week specified) if six experienced operators are on duty.</span></span>  
  
#### <a name="to-create-a-singleton-query-by-using-the-neural-network-model"></a><span data-ttu-id="9d74e-111">通过使用神经网络模型创建单独查询</span><span class="sxs-lookup"><span data-stu-id="9d74e-111">To create a singleton query by using the neural network model</span></span>  
  
1.  <span data-ttu-id="9d74e-112">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中，打开包含要使用的模型的解决方案。</span><span class="sxs-lookup"><span data-stu-id="9d74e-112">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the solution that contains the model that you want to use.</span></span>  
  
2.  <span data-ttu-id="9d74e-113">在数据挖掘设计器中，单击 "**挖掘模型预测**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="9d74e-113">In Data Mining Designer, click the **Mining Model Prediction** tab.</span></span>  
  
3.  <span data-ttu-id="9d74e-114">在 "**挖掘模型**" 窗格中单击 "**选择模型**"。</span><span class="sxs-lookup"><span data-stu-id="9d74e-114">In the **Mining Model** pane, click **Select Model**.</span></span>  
  
4.  <span data-ttu-id="9d74e-115">"**选择挖掘模型**" 对话框显示挖掘结构的列表。</span><span class="sxs-lookup"><span data-stu-id="9d74e-115">The **Select Mining Model** dialog box shows a list of mining structures.</span></span> <span data-ttu-id="9d74e-116">展开挖掘结构可查看与该结构相关联的挖掘模型列表。</span><span class="sxs-lookup"><span data-stu-id="9d74e-116">Expand the mining structure to view a list of mining models associated with that structure.</span></span>  
  
5.  <span data-ttu-id="9d74e-117">展开挖掘结构 Call Center Default，选中神经网络模型 Call Center - LR。</span><span class="sxs-lookup"><span data-stu-id="9d74e-117">Expand the mining structure Call Center Default, and select the neural network model, Call Center - LR.</span></span>  
  
6.  <span data-ttu-id="9d74e-118">从 **“挖掘模型”** 菜单中选择 **“单独查询”**。</span><span class="sxs-lookup"><span data-stu-id="9d74e-118">From the **Mining Model** menu, select **Singleton Query**.</span></span>  
  
     <span data-ttu-id="9d74e-119">出现 "**单独查询输入**" 对话框，其中的列映射到挖掘模型中的列。</span><span class="sxs-lookup"><span data-stu-id="9d74e-119">The **Singleton Query Input** dialog box appears, with columns mapped to the columns in the mining model.</span></span>  
  
7.  <span data-ttu-id="9d74e-120">在 "**单独查询输入**" 对话框中，单击要移动的行，然后选择 "*午夜*"。</span><span class="sxs-lookup"><span data-stu-id="9d74e-120">In the **Singleton Query Input** dialog box, click the row for Shift, and then select *midnight*.</span></span>  
  
8.  <span data-ttu-id="9d74e-121">单击 "Lvl 2" 运算符对应的行，然后键入 `6` 。</span><span class="sxs-lookup"><span data-stu-id="9d74e-121">Click the row for Lvl 2 Operators, and type `6`.</span></span>  
  
9. <span data-ttu-id="9d74e-122">在 "**挖掘模型预测**" 选项卡的下半部分，单击网格中的第一行。</span><span class="sxs-lookup"><span data-stu-id="9d74e-122">In the bottom half of the **Mining Model Prediction** tab, click the first row in the grid.</span></span>  
  
10. <span data-ttu-id="9d74e-123">在 "**源**" 列中，单击向下箭头，然后选择 "**预测函数**"。</span><span class="sxs-lookup"><span data-stu-id="9d74e-123">In the **Source** column, click the down arrow, and select **Prediction function**.</span></span> <span data-ttu-id="9d74e-124">在 "**字段**" 列中，选择**PredictHistogram**。</span><span class="sxs-lookup"><span data-stu-id="9d74e-124">In the **Field** column, select **PredictHistogram**.</span></span>  
  
     <span data-ttu-id="9d74e-125">可用于此预测函数的参数的列表会自动显示在 "**条件/参数**" 框中。</span><span class="sxs-lookup"><span data-stu-id="9d74e-125">A list of arguments that you can use with this prediction function automatically appears in the **Criteria/Arguments** box.</span></span>  
  
11. <span data-ttu-id="9d74e-126">将 ServiceGrade 列从 "**挖掘模型**" 窗格中的列列表拖到 "**条件/参数**" 框。</span><span class="sxs-lookup"><span data-stu-id="9d74e-126">Drag the ServiceGrade column from the list of columns in the **Mining Model** pane to the **Criteria/Arguments** box.</span></span>  
  
     <span data-ttu-id="9d74e-127">列的名称自动作为参数插入。</span><span class="sxs-lookup"><span data-stu-id="9d74e-127">The name of the column is automatically inserted as the argument.</span></span> <span data-ttu-id="9d74e-128">可以选择任何可预测属性列以便放入此文本框。</span><span class="sxs-lookup"><span data-stu-id="9d74e-128">You can choose any predictable attribute column to drag into this text box.</span></span>  
  
12. <span data-ttu-id="9d74e-129">单击 "**切换到查询结果视图**" 按钮，然后在预测查询生成器的上角。</span><span class="sxs-lookup"><span data-stu-id="9d74e-129">Click the button **Switch to query results view**, in the upper corner of the Prediction Query Builder.</span></span>  
  
 <span data-ttu-id="9d74e-130">预期结果包含对于给定这些输入的每个服务等级可能的预测值，以及对每个预测的支持值和概率值。</span><span class="sxs-lookup"><span data-stu-id="9d74e-130">The expected results contain the possible predicted values for each service grade given these inputs, together with support and probability values for each prediction.</span></span> <span data-ttu-id="9d74e-131">您可以随时返回设计视图，更改输入或添加更多输入。</span><span class="sxs-lookup"><span data-stu-id="9d74e-131">You can return to design view at any time and change the inputs, or add more inputs.</span></span>  
  
## <a name="creating-predictions-by-using-a-logistic-regression-model"></a><span data-ttu-id="9d74e-132">通过使用逻辑回归模型创建预测</span><span class="sxs-lookup"><span data-stu-id="9d74e-132">Creating Predictions by using a Logistic Regression Model</span></span>  
 <span data-ttu-id="9d74e-133">如果您已经知道与业务问题相关的属性，您就可以使用逻辑回归模型来预测在某些属性中进行更改的效果。</span><span class="sxs-lookup"><span data-stu-id="9d74e-133">If you already know the attributes that are relevant to the business problem, you can use a logistic regression model to predict the effect of making changes in some attributes.</span></span> <span data-ttu-id="9d74e-134">逻辑回归是一种统计方法，常用于基于独立变量中的更改进行预测：例如，它用于财务计分中，以便基于客户人口统计信息来预测客户行为。</span><span class="sxs-lookup"><span data-stu-id="9d74e-134">Logistic regression is a statistical method that is commonly used to make predictions based on changes in independent variables: for example, it is used in financial scoring, to predict customer behavior based on customer demographics.</span></span>  
  
 <span data-ttu-id="9d74e-135">在本任务中，您将学习如何创建将用于预测的数据源，然后进行预测来协助回答一些业务问题。</span><span class="sxs-lookup"><span data-stu-id="9d74e-135">In this task, you will learn how to create a data source that will be used for predictions, and then make predictions to help answer several business questions.</span></span>  
  
### <a name="generating-data-used-for-bulk-prediction"></a><span data-ttu-id="9d74e-136">生成用于大容量预测的数据</span><span class="sxs-lookup"><span data-stu-id="9d74e-136">Generating Data used for Bulk Prediction</span></span>  
 <span data-ttu-id="9d74e-137">有多种方式可提供输入数据：例如，您可以从电子表格中导入人员配备级别，并通过模型运行该数据以预测下个月的服务质量。</span><span class="sxs-lookup"><span data-stu-id="9d74e-137">There are many ways to provide input data: for example, you might import staffing levels from a spreadsheet, and run that data through the model to predict service quality for the next month.</span></span>  
  
 <span data-ttu-id="9d74e-138">在本课中，您将使用数据源视图设计器创建命名查询。</span><span class="sxs-lookup"><span data-stu-id="9d74e-138">In this lesson, you will use the Data Source View designer to create a named query.</span></span> <span data-ttu-id="9d74e-139">该命名查询是一个自定义 Transact-SQL 语句，为计划的每个班次计算配备的最多操作员数、接收的最少呼叫数和生成的平均问题数。</span><span class="sxs-lookup"><span data-stu-id="9d74e-139">This named query is a custom Transact-SQL statement that for each shift on the schedule calculates the maximum number of operators on staff, the minimum calls received, and the average number of issues that are generated.</span></span> <span data-ttu-id="9d74e-140">然后，您将该数据与一个挖掘模型联接以预测有关未来一系列日期的情况。</span><span class="sxs-lookup"><span data-stu-id="9d74e-140">You will then join that data to a mining model to make predictions about a series of upcoming dates.</span></span>  
  
##### <a name="to-generate-input-data-for-a-bulk-prediction-query"></a><span data-ttu-id="9d74e-141">生成大容量预测查询的输入数据</span><span class="sxs-lookup"><span data-stu-id="9d74e-141">To generate input data for a bulk prediction query</span></span>  
  
1.  <span data-ttu-id="9d74e-142">在解决方案资源管理器中，右键单击 "**数据源视图**"，然后选择 "**新建数据源视图**"。</span><span class="sxs-lookup"><span data-stu-id="9d74e-142">In Solution Explorer, right-click **Data Source Views**, and then select **New Data Source View**.</span></span>  
  
2.  <span data-ttu-id="9d74e-143">在数据源视图向导中，选择 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] 作为数据源，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="9d74e-143">In the Data Source View wizard, select [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] as the data source, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="9d74e-144">在 "**选择表和视图**" 页上，单击 "**下一步**"，不选择任何表。</span><span class="sxs-lookup"><span data-stu-id="9d74e-144">On the **Select Tables and Views** page, click **Next** without selecting any tables.</span></span>  
  
4.  <span data-ttu-id="9d74e-145">在 "**完成向导**" 页上，键入名称， `Shifts` 。</span><span class="sxs-lookup"><span data-stu-id="9d74e-145">On the **Completing the Wizard** page, type the name, `Shifts`.</span></span>  
  
     <span data-ttu-id="9d74e-146">该名称将作为数据源视图的名称显示在解决方案资源管理器中。</span><span class="sxs-lookup"><span data-stu-id="9d74e-146">This name will appear in Solution Explorer as the name of the data source view.</span></span>  
  
5.  <span data-ttu-id="9d74e-147">右键单击空设计窗格，然后选择 "**新建命名查询**"。</span><span class="sxs-lookup"><span data-stu-id="9d74e-147">Right-click the empty design pane, then select **New Named Query**.</span></span>  
  
6.  <span data-ttu-id="9d74e-148">在 "**创建命名查询**" 对话框中，为 "**名称**" 键入 `Shifts for Call Center` 。</span><span class="sxs-lookup"><span data-stu-id="9d74e-148">In the **Create Named Query** dialog box, for **Name**, type `Shifts for Call Center`.</span></span>  
  
     <span data-ttu-id="9d74e-149">该名称将仅作为命名查询的名称显示在数据源视图设计器中。</span><span class="sxs-lookup"><span data-stu-id="9d74e-149">This name will appear in Data Source View designer only as the name of the named query.</span></span>  
  
7.  <span data-ttu-id="9d74e-150">将以下查询语句粘贴到对话框下半部分的 SQL 文本窗格中。</span><span class="sxs-lookup"><span data-stu-id="9d74e-150">Paste the following query statement into the SQL text pane in the lower half of the dialog box.</span></span>  
  
    ```  
    SELECT DISTINCT WageType, Shift,   
    AVG(Orders) as AvgOrders, MIN(Orders) as MinOrders, MAX(Orders) as MaxOrders,  
    AVG(Calls) as AvgCalls, MIN(Calls) as MinCalls, MAX(Calls) as MaxCalls,  
    AVG(LevelTwoOperators) as AvgOperators, MIN(LevelTwoOperators) as MinOperators, MAX(LevelTwoOperators) as MaxOperators,  
    AVG(IssuesRaised) as AvgIssues, MIN(IssuesRaised) as MinIssues, MAX(IssuesRaised) as MaxIssues  
    FROM dbo.FactCallCenter  
    GROUP BY Shift, WageType  
    ```  
  
8.  <span data-ttu-id="9d74e-151">在 "设计" 窗格中，右键单击表，在 "调用中心" 的偏移，然后选择 "**浏览数据**" 以预览 t-sql 查询返回的数据。</span><span class="sxs-lookup"><span data-stu-id="9d74e-151">In the design pane, right-click the table, Shifts for Call Center, and select **Explore Data** to preview the data as returned by the T-SQL query.</span></span>  
  
9. <span data-ttu-id="9d74e-152">右键单击选项卡，将 "**移动" ("设计") ，** 然后单击 "**保存**" 以保存新的数据源视图定义。</span><span class="sxs-lookup"><span data-stu-id="9d74e-152">Right-click the tab, **Shifts.dsv (Design),** and then click **Save** to save the new data source view definition.</span></span>  
  
### <a name="predicting-service-metrics-for-each-shift"></a><span data-ttu-id="9d74e-153">预测每个班次的服务标准</span><span class="sxs-lookup"><span data-stu-id="9d74e-153">Predicting Service Metrics for Each Shift</span></span>  
 <span data-ttu-id="9d74e-154">现在您已经为每个班次生成了一些值，将使用那些值作为您生成的逻辑回归模型的输入，来生成可用于业务规划的一些预测。</span><span class="sxs-lookup"><span data-stu-id="9d74e-154">Now that you have generated some values for each shift, you will use those values as input to the logistic regression model that you built, to generate some predictions that can be used in business planning.</span></span>  
  
##### <a name="to-use-the-new-dsv-as-input-to-a-prediction-query"></a><span data-ttu-id="9d74e-155">使用新 DSV 作为预测查询输入</span><span class="sxs-lookup"><span data-stu-id="9d74e-155">To use the new DSV as input to a prediction query</span></span>  
  
1.  <span data-ttu-id="9d74e-156">在数据挖掘设计器中，单击 "**挖掘模型预测**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="9d74e-156">In Data Mining Designer, click the **Mining Model Prediction** tab.</span></span>  
  
2.  <span data-ttu-id="9d74e-157">在 "**挖掘模型**" 窗格中，单击 "**选择模型**"，然后从可用模型列表中选择 "呼叫中心-LR"。</span><span class="sxs-lookup"><span data-stu-id="9d74e-157">In the **Mining Model** pane, click **Select Model**, and choose Call Center - LR from the list of available models.</span></span>  
  
3.  <span data-ttu-id="9d74e-158">从 "**挖掘模型**" 菜单中，清除 "**单独查询**" 选项。</span><span class="sxs-lookup"><span data-stu-id="9d74e-158">From the **Mining Model** menu, clear the option, **Singleton Query**.</span></span> <span data-ttu-id="9d74e-159">将警告您单独查询输入将丢失。</span><span class="sxs-lookup"><span data-stu-id="9d74e-159">A warning tells you that the singleton query inputs will be lost.</span></span> <span data-ttu-id="9d74e-160">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="9d74e-160">Click **OK**.</span></span>  
  
     <span data-ttu-id="9d74e-161">"**单独查询输入**" 对话框被替换为 "\*\*选择输入表 (s) \*\* " 对话框。</span><span class="sxs-lookup"><span data-stu-id="9d74e-161">The **Singleton Query Input** dialog box is replaced with the **Select Input Table(s)** dialog box.</span></span>  
  
4.  <span data-ttu-id="9d74e-162">单击“选择事例表” \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9d74e-162">Click **Select Case Table**.</span></span>  
  
5.  <span data-ttu-id="9d74e-163">在 "**选择表**" 对话框中，从数据源列表中 selectShifts。</span><span class="sxs-lookup"><span data-stu-id="9d74e-163">In the **Select Table** dialog box, selectShifts from the list of data sources.</span></span> <span data-ttu-id="9d74e-164">在 "**表/视图名称**" 列表中，选择 "倒班 For Call Center" (它可能会自动选择) ，然后单击 **"确定"。**</span><span class="sxs-lookup"><span data-stu-id="9d74e-164">In the **Table/View name** list, select Shifts for Call Center (it might be automatically selected), and then click **OK.**</span></span>  
  
     <span data-ttu-id="9d74e-165">"**挖掘模型预测**" 设计图面将更新，以显示基于输入数据和模型中列的名称和数据类型创建的映射。</span><span class="sxs-lookup"><span data-stu-id="9d74e-165">The **Mining Model Prediction** design surface is updated to show mappings that are created based on the names and data types of columns in the input data and in the model.</span></span>  
  
6.  <span data-ttu-id="9d74e-166">右键单击其中一条联接线，然后选择 "**修改连接**"。</span><span class="sxs-lookup"><span data-stu-id="9d74e-166">Right-click one of the join lines, and then select **Modify Connections**.</span></span>  
  
     <span data-ttu-id="9d74e-167">在此对话框中，您可以确切看到映射了哪些列以及未映射哪些列。</span><span class="sxs-lookup"><span data-stu-id="9d74e-167">In this dialog box, you can see exactly which columns are mapped and which are not.</span></span> <span data-ttu-id="9d74e-168">该挖掘模型包含 Calls 列、Orders 列、IssuesRaised 列和 LvlTwoOperators 列，这些列可以映射到您基于源数据中上述列创建的任何聚合中。</span><span class="sxs-lookup"><span data-stu-id="9d74e-168">The mining model contains columns for Calls, Orders, IssuesRaised, and LvlTwoOperators, which you can map to any of the aggregates that you created based on these columns in the source data.</span></span> <span data-ttu-id="9d74e-169">在此情况下，您将映射到平均值。</span><span class="sxs-lookup"><span data-stu-id="9d74e-169">In this scenario, you will map to the averages.</span></span>  
  
7.  <span data-ttu-id="9d74e-170">单击 "LevelTwoOperators" 旁边的空单元格，然后选择 " **for call center.avgoperators**"。</span><span class="sxs-lookup"><span data-stu-id="9d74e-170">Click the empty cell next to LevelTwoOperators, and select **Shifts for Call Center.AvgOperators**.</span></span>  
  
8.  <span data-ttu-id="9d74e-171">单击 "调用" 旁边的空单元格，然后选择 " **for call center.avgcalls**"。</span><span class="sxs-lookup"><span data-stu-id="9d74e-171">Click the empty cell next to Calls, select **Shifts for Call Center.AvgCalls**.</span></span> <span data-ttu-id="9d74e-172">然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="9d74e-172">and then click **OK**.</span></span>  
  
##### <a name="to-create-the-predictions-for-each-shift"></a><span data-ttu-id="9d74e-173">创建每个班次的预测</span><span class="sxs-lookup"><span data-stu-id="9d74e-173">To create the predictions for each shift</span></span>  
  
1.  <span data-ttu-id="9d74e-174">在**预测查询生成器**下半部分的网格中，单击 "源" 下的空单元 **，** 然后选择 "针对呼叫中心的倒班"。</span><span class="sxs-lookup"><span data-stu-id="9d74e-174">In the grid at the bottom half of the **Prediction Query Builder**, click the empty cell under **Source,** and then select Shifts for Call Center.</span></span>  
  
2.  <span data-ttu-id="9d74e-175">在 "**字段**" 下的空单元中，选择 "Shift"。</span><span class="sxs-lookup"><span data-stu-id="9d74e-175">In the empty cell under **Field**, select Shift.</span></span>  
  
3.  <span data-ttu-id="9d74e-176">单击网格中的下一个空行并重复实数过程来为 WageType 添加另一行。</span><span class="sxs-lookup"><span data-stu-id="9d74e-176">Click the next empty line in the grid and repeat the procedure described above to add another row for WageType.</span></span>  
  
4.  <span data-ttu-id="9d74e-177">单击网格中的下一个空行。</span><span class="sxs-lookup"><span data-stu-id="9d74e-177">Click the next empty line in the grid.</span></span> <span data-ttu-id="9d74e-178">在 "**源**" 列中，选择 "**预测函数**"。</span><span class="sxs-lookup"><span data-stu-id="9d74e-178">In the **Source** column, select **Prediction Function**.</span></span> <span data-ttu-id="9d74e-179">在 "**字段**" 列中，选择 "**预测**"。</span><span class="sxs-lookup"><span data-stu-id="9d74e-179">In the **Field** column, select **Predict**.</span></span>  
  
5.  <span data-ttu-id="9d74e-180">将 ServiceGrade 列从 "**挖掘模型**" 窗格向下拖动到网格，并将其拖到 "**条件/参数**" 单元中。</span><span class="sxs-lookup"><span data-stu-id="9d74e-180">Drag the column ServiceGrade from the **Mining Model** pane down to the grid, and into the **Criteria/Argument** cell.</span></span> <span data-ttu-id="9d74e-181">在 "**别名**" 字段中，键入**预测的服务等级**。</span><span class="sxs-lookup"><span data-stu-id="9d74e-181">In the **Alias** field, type **Predicted Service Grade**.</span></span>  
  
6.  <span data-ttu-id="9d74e-182">单击网格中的下一个空行。</span><span class="sxs-lookup"><span data-stu-id="9d74e-182">Click the next empty line in the grid.</span></span> <span data-ttu-id="9d74e-183">在 "**源**" 列中，选择 "**预测函数**"。</span><span class="sxs-lookup"><span data-stu-id="9d74e-183">In the **Source** column, select **Prediction Function**.</span></span> <span data-ttu-id="9d74e-184">在 "**字段**" 列中，选择**PredictProbability**。</span><span class="sxs-lookup"><span data-stu-id="9d74e-184">In the **Field** column, select **PredictProbability**.</span></span>  
  
7.  <span data-ttu-id="9d74e-185">将 ServiceGrade 列从 "**挖掘模型**" 窗格向下拖动到网格，并将其拖到 "**条件/参数**" 单元中。</span><span class="sxs-lookup"><span data-stu-id="9d74e-185">Drag the column ServiceGrade from the **Mining Model** pane down to the grid, and into the **Criteria/Argument** cell.</span></span> <span data-ttu-id="9d74e-186">在 "**别名**" 字段中，键入**Probability**。</span><span class="sxs-lookup"><span data-stu-id="9d74e-186">In the **Alias** field, type **Probability**.</span></span>  
  
8.  <span data-ttu-id="9d74e-187">单击 "**切换到查询结果视图**" 查看预测。</span><span class="sxs-lookup"><span data-stu-id="9d74e-187">Click **Switch to query result view** to view the predictions.</span></span>  
  
 <span data-ttu-id="9d74e-188">下表显示了每个班次的示例结果。</span><span class="sxs-lookup"><span data-stu-id="9d74e-188">The following table shows sample results for each shift.</span></span>  
  
|<span data-ttu-id="9d74e-189">移位</span><span class="sxs-lookup"><span data-stu-id="9d74e-189">Shift</span></span>|<span data-ttu-id="9d74e-190">WageType</span><span class="sxs-lookup"><span data-stu-id="9d74e-190">WageType</span></span>|<span data-ttu-id="9d74e-191">预测服务等级</span><span class="sxs-lookup"><span data-stu-id="9d74e-191">Predicted Service Grade</span></span>|<span data-ttu-id="9d74e-192">概率</span><span class="sxs-lookup"><span data-stu-id="9d74e-192">Probability</span></span>|  
|-----------|--------------|-----------------------------|-----------------|  
|<span data-ttu-id="9d74e-193">AM</span><span class="sxs-lookup"><span data-stu-id="9d74e-193">AM</span></span>|<span data-ttu-id="9d74e-194">假日</span><span class="sxs-lookup"><span data-stu-id="9d74e-194">holiday</span></span>|<span data-ttu-id="9d74e-195">0.165</span><span class="sxs-lookup"><span data-stu-id="9d74e-195">0.165</span></span>|<span data-ttu-id="9d74e-196">0.377520666</span><span class="sxs-lookup"><span data-stu-id="9d74e-196">0.377520666</span></span>|  
|<span data-ttu-id="9d74e-197">午夜</span><span class="sxs-lookup"><span data-stu-id="9d74e-197">midnight</span></span>|<span data-ttu-id="9d74e-198">假日</span><span class="sxs-lookup"><span data-stu-id="9d74e-198">holiday</span></span>|<span data-ttu-id="9d74e-199">0.105</span><span class="sxs-lookup"><span data-stu-id="9d74e-199">0.105</span></span>|<span data-ttu-id="9d74e-200">0.364105573</span><span class="sxs-lookup"><span data-stu-id="9d74e-200">0.364105573</span></span>|  
|<span data-ttu-id="9d74e-201">PM1</span><span class="sxs-lookup"><span data-stu-id="9d74e-201">PM1</span></span>|<span data-ttu-id="9d74e-202">假日</span><span class="sxs-lookup"><span data-stu-id="9d74e-202">holiday</span></span>|<span data-ttu-id="9d74e-203">0.165</span><span class="sxs-lookup"><span data-stu-id="9d74e-203">0.165</span></span>|<span data-ttu-id="9d74e-204">0.40056055</span><span class="sxs-lookup"><span data-stu-id="9d74e-204">0.40056055</span></span>|  
|<span data-ttu-id="9d74e-205">PM2</span><span class="sxs-lookup"><span data-stu-id="9d74e-205">PM2</span></span>|<span data-ttu-id="9d74e-206">假日</span><span class="sxs-lookup"><span data-stu-id="9d74e-206">holiday</span></span>|<span data-ttu-id="9d74e-207">0.165</span><span class="sxs-lookup"><span data-stu-id="9d74e-207">0.165</span></span>|<span data-ttu-id="9d74e-208">0.338532973</span><span class="sxs-lookup"><span data-stu-id="9d74e-208">0.338532973</span></span>|  
|<span data-ttu-id="9d74e-209">AM</span><span class="sxs-lookup"><span data-stu-id="9d74e-209">AM</span></span>|<span data-ttu-id="9d74e-210">weekday</span><span class="sxs-lookup"><span data-stu-id="9d74e-210">weekday</span></span>|<span data-ttu-id="9d74e-211">0.165</span><span class="sxs-lookup"><span data-stu-id="9d74e-211">0.165</span></span>|<span data-ttu-id="9d74e-212">0.370847617</span><span class="sxs-lookup"><span data-stu-id="9d74e-212">0.370847617</span></span>|  
|<span data-ttu-id="9d74e-213">午夜</span><span class="sxs-lookup"><span data-stu-id="9d74e-213">midnight</span></span>|<span data-ttu-id="9d74e-214">weekday</span><span class="sxs-lookup"><span data-stu-id="9d74e-214">weekday</span></span>|<span data-ttu-id="9d74e-215">0.08</span><span class="sxs-lookup"><span data-stu-id="9d74e-215">0.08</span></span>|<span data-ttu-id="9d74e-216">0.352999173</span><span class="sxs-lookup"><span data-stu-id="9d74e-216">0.352999173</span></span>|  
|<span data-ttu-id="9d74e-217">PM1</span><span class="sxs-lookup"><span data-stu-id="9d74e-217">PM1</span></span>|<span data-ttu-id="9d74e-218">weekday</span><span class="sxs-lookup"><span data-stu-id="9d74e-218">weekday</span></span>|<span data-ttu-id="9d74e-219">0.165</span><span class="sxs-lookup"><span data-stu-id="9d74e-219">0.165</span></span>|<span data-ttu-id="9d74e-220">0.317419177</span><span class="sxs-lookup"><span data-stu-id="9d74e-220">0.317419177</span></span>|  
|<span data-ttu-id="9d74e-221">PM2</span><span class="sxs-lookup"><span data-stu-id="9d74e-221">PM2</span></span>|<span data-ttu-id="9d74e-222">weekday</span><span class="sxs-lookup"><span data-stu-id="9d74e-222">weekday</span></span>|<span data-ttu-id="9d74e-223">0.105</span><span class="sxs-lookup"><span data-stu-id="9d74e-223">0.105</span></span>|<span data-ttu-id="9d74e-224">0.311672027</span><span class="sxs-lookup"><span data-stu-id="9d74e-224">0.311672027</span></span>|  
  
### <a name="predicting-the-effect-of-reduced-response-time-on-service-grade"></a><span data-ttu-id="9d74e-225">预测缩短响应时间对服务等级的影响</span><span class="sxs-lookup"><span data-stu-id="9d74e-225">Predicting the Effect of Reduced Response Time on Service Grade</span></span>  
 <span data-ttu-id="9d74e-226">您为每个班次生成了一些平均值，并将那些值用作逻辑回归模型的输入。</span><span class="sxs-lookup"><span data-stu-id="9d74e-226">You generated some average values for each shift, and used those values as input to the logistic regression model.</span></span> <span data-ttu-id="9d74e-227">但是，假定业务目标是将挂断率保持在 0.00-0.05 的范围内，但结果并不令人满意。</span><span class="sxs-lookup"><span data-stu-id="9d74e-227">However, given that the business objective is to keep abandon rate within the range 0.00-0.05, the results are not encouraging.</span></span>  
  
 <span data-ttu-id="9d74e-228">因此，根据原始模型（该模型显示了响应时间对服务等级的巨大影响），业务团队决定运行一些预测，评估缩短响应呼叫的平均时间是否会提高服务质量。</span><span class="sxs-lookup"><span data-stu-id="9d74e-228">Therefore, based on the original model, which showed a strong influence of response time on service grade, the Operations team decides to run some predictions to assess whether reducing the average time for responding to calls might improve service quality.</span></span> <span data-ttu-id="9d74e-229">例如，如果您将呼叫响应时间缩短到当前响应时间的 90%，甚至 80%，服务等级值会发生什么变化？</span><span class="sxs-lookup"><span data-stu-id="9d74e-229">For example, if you cut the call response time to 90 percent or even to 80 percent of the current call response time, what would happen to service grade values?</span></span>  
  
 <span data-ttu-id="9d74e-230">创建计算每个班次平均响应时间的数据源视图 (DSV)，随后添加计算该平均响应时间的 80% 或 90% 的列，这操作起来很容易。</span><span class="sxs-lookup"><span data-stu-id="9d74e-230">It is easy to create a data source view (DSV) that calculates the average response times for each shift, and then add columns that calculate 80% or 90% of the average response time.</span></span> <span data-ttu-id="9d74e-231">然后可以将该 DSV 用作模型输入。</span><span class="sxs-lookup"><span data-stu-id="9d74e-231">You can then use the DSV as input to the model.</span></span>  
  
 <span data-ttu-id="9d74e-232">尽管此处未显示确切的步骤，但是下表比较了在您将响应时间缩短到当前响应时间的 80% 或 90% 时对服务等级的影响。</span><span class="sxs-lookup"><span data-stu-id="9d74e-232">Although the exact steps are not shown here, the following table compares the effects on service grade when you reduce response times to 80% or to 90% of current response times.</span></span>  
  
 <span data-ttu-id="9d74e-233">从这些结果中可以得出结论：对于针对的班次，应将响应时间缩短到当前响应时间的 90% 以提高服务质量。</span><span class="sxs-lookup"><span data-stu-id="9d74e-233">From these results, you might conclude that on targeted shifts you should reduce the response time to 90 percent of the current rate in order to improve service quality.</span></span>  
  
|<span data-ttu-id="9d74e-234">班次、工资和日</span><span class="sxs-lookup"><span data-stu-id="9d74e-234">Shift, wage, and day</span></span>|<span data-ttu-id="9d74e-235">预测的当前平均响应时间下的服务质量</span><span class="sxs-lookup"><span data-stu-id="9d74e-235">Predicted service quality with current average response time</span></span>|<span data-ttu-id="9d74e-236">预测的响应时间缩短为 90％ 时的服务质量</span><span class="sxs-lookup"><span data-stu-id="9d74e-236">Predicted service quality with 90 percent reduction in response time</span></span>|<span data-ttu-id="9d74e-237">响应时间缩短80% 的预测服务质量</span><span class="sxs-lookup"><span data-stu-id="9d74e-237">Predicted service quality with 80 percent reduction in response time</span></span>|  
|--------------------------|------------------------------------------------------------------|--------------------------------------------------------------------------|--------------------------------------------------------------------------|  
|<span data-ttu-id="9d74e-238">假日 AM</span><span class="sxs-lookup"><span data-stu-id="9d74e-238">Holiday AM</span></span>|<span data-ttu-id="9d74e-239">0.165</span><span class="sxs-lookup"><span data-stu-id="9d74e-239">0.165</span></span>|<span data-ttu-id="9d74e-240">0.05</span><span class="sxs-lookup"><span data-stu-id="9d74e-240">0.05</span></span>|<span data-ttu-id="9d74e-241">0.05</span><span class="sxs-lookup"><span data-stu-id="9d74e-241">0.05</span></span>|  
|<span data-ttu-id="9d74e-242">假日 PM1</span><span class="sxs-lookup"><span data-stu-id="9d74e-242">Holiday PM1</span></span>|<span data-ttu-id="9d74e-243">0.05</span><span class="sxs-lookup"><span data-stu-id="9d74e-243">0.05</span></span>|<span data-ttu-id="9d74e-244">0.05</span><span class="sxs-lookup"><span data-stu-id="9d74e-244">0.05</span></span>|<span data-ttu-id="9d74e-245">0.05</span><span class="sxs-lookup"><span data-stu-id="9d74e-245">0.05</span></span>|  
|<span data-ttu-id="9d74e-246">假日午夜</span><span class="sxs-lookup"><span data-stu-id="9d74e-246">Holiday Midnight</span></span>|<span data-ttu-id="9d74e-247">0.165</span><span class="sxs-lookup"><span data-stu-id="9d74e-247">0.165</span></span>|<span data-ttu-id="9d74e-248">0.05</span><span class="sxs-lookup"><span data-stu-id="9d74e-248">0.05</span></span>|<span data-ttu-id="9d74e-249">0.05</span><span class="sxs-lookup"><span data-stu-id="9d74e-249">0.05</span></span>|  
  
 <span data-ttu-id="9d74e-250">可以在此模型上创建多种其他预测查询。</span><span class="sxs-lookup"><span data-stu-id="9d74e-250">There are a variety of other prediction queries that you can create on this model.</span></span> <span data-ttu-id="9d74e-251">例如，您可以预测需要多少运算符来满足某个服务级别或响应特定数量的传入呼叫。</span><span class="sxs-lookup"><span data-stu-id="9d74e-251">For example, you could predict how many operators are required to meet a certain service level or to respond to a certain number of incoming calls.</span></span> <span data-ttu-id="9d74e-252">因为您可以在逻辑回归模型中包括多个输出，所以很容易试用不同的独立变量和结果，而无需创建许多单独的模型。</span><span class="sxs-lookup"><span data-stu-id="9d74e-252">Because you can include multiple outputs in a logistic regression model, it is easy to experiment with different independent variables and outcomes without having to create many separate models.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d74e-253">备注</span><span class="sxs-lookup"><span data-stu-id="9d74e-253">Remarks</span></span>  
 <span data-ttu-id="9d74e-254">2007 Excel 的数据挖掘外接程序提供了逻辑回归向导，可以方便地回答复杂的问题，例如，将服务等级提高到特定班次的目标级别需要多少个级别。</span><span class="sxs-lookup"><span data-stu-id="9d74e-254">The Data Mining Add-Ins for Excel 2007 provide logistic regression wizards that make it easy to answer complex questions, such as how many Level Two Operators would be required to improve service grade to a target level for a specific shift.</span></span> <span data-ttu-id="9d74e-255">数据挖掘外接程序是免费下载的，并包含基于神经网络或逻辑回归算法的向导。</span><span class="sxs-lookup"><span data-stu-id="9d74e-255">The data mining add-ins are a free download, and include wizards that are based on the neural network or logistic regression algorithms.</span></span> <span data-ttu-id="9d74e-256">有关详细信息，请参阅以下链接：</span><span class="sxs-lookup"><span data-stu-id="9d74e-256">For more information, see the following links:</span></span>  
  
-   <span data-ttu-id="9d74e-257">[SQL Server 2005 Office 2007 数据挖掘外接程序](https://www.microsoft.com/sql/technologies/dm/addins.mspx)：目标查找和 What If 方案分析</span><span class="sxs-lookup"><span data-stu-id="9d74e-257">[SQL Server 2005 Data Mining Add-Ins for Office 2007](https://www.microsoft.com/sql/technologies/dm/addins.mspx): Goal Seek and What If Scenario Analysis</span></span>  
  
-   <span data-ttu-id="9d74e-258">[SQL Server 2008 Office 2007 数据挖掘外接程序](https://go.microsoft.com/fwlink/?LinkID=117790)：目标查找方案分析、What If 方案分析和预测计算器</span><span class="sxs-lookup"><span data-stu-id="9d74e-258">[SQL Server 2008 Data Mining Add-Ins for Office 2007](https://go.microsoft.com/fwlink/?LinkID=117790): Goal Seek Scenario Analysis, What If Scenario Analysis, and Prediction Calculator</span></span>  
  
## <a name="conclusion"></a><span data-ttu-id="9d74e-259">结论</span><span class="sxs-lookup"><span data-stu-id="9d74e-259">Conclusion</span></span>  
 <span data-ttu-id="9d74e-260">您已经学习了创建、自定义和解释基于 Microsoft 神经网络算法和 Microsoft 逻辑回归算法的挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="9d74e-260">You have learned to create, customize, and interpret mining models that are based on the Microsoft Neural Network algorithm and the Microsoft Logistic Regression algorithm.</span></span> <span data-ttu-id="9d74e-261">这些模型类型很精细，允许在分析中使用几乎无限种变化，因此会很复杂并难于掌握。</span><span class="sxs-lookup"><span data-stu-id="9d74e-261">These model types are sophisticated and permit almost infinite variety in analysis, and therefore can be complex and difficult to master.</span></span>  
  
 <span data-ttu-id="9d74e-262">但是，如果提供模式的统计支持（很难使用 Transact-SQL 或甚至 PowerPivot 通过手动浏览数据来发现），这些算法可以通过因素的很多组合来迭代并自动标识最强的相关性。</span><span class="sxs-lookup"><span data-stu-id="9d74e-262">However, these algorithms can iterate through many combinations of factors and automatically identify the strongest correlations, providing statistical support for insights that would be very difficult to discover through manual exploration of data using Transact-SQL or even PowerPivot.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d74e-263">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9d74e-263">See Also</span></span>  
 <span data-ttu-id="9d74e-264">[逻辑回归模型查询示例](../../2014/analysis-services/data-mining/logistic-regression-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="9d74e-264">[Logistic Regression Model Query Examples](../../2014/analysis-services/data-mining/logistic-regression-model-query-examples.md) </span></span>  
 <span data-ttu-id="9d74e-265">[Microsoft 逻辑回归算法](../../2014/analysis-services/data-mining/microsoft-logistic-regression-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="9d74e-265">[Microsoft Logistic Regression Algorithm](../../2014/analysis-services/data-mining/microsoft-logistic-regression-algorithm.md) </span></span>  
 <span data-ttu-id="9d74e-266">[Microsoft 神经网络算法](../../2014/analysis-services/data-mining/microsoft-neural-network-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="9d74e-266">[Microsoft Neural Network Algorithm](../../2014/analysis-services/data-mining/microsoft-neural-network-algorithm.md) </span></span>  
 [<span data-ttu-id="9d74e-267">神经网络模型查询示例</span><span class="sxs-lookup"><span data-stu-id="9d74e-267">Neural Network Model Query Examples</span></span>](../../2014/analysis-services/data-mining/neural-network-model-query-examples.md)  
  
  
