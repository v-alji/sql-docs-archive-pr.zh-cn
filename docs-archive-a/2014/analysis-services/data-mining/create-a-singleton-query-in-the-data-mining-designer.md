---
title: 在数据挖掘设计器中创建单独查询 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- singleton queries [Analysis Services]
- Mining Model Prediction [Analysis Services], singleton queries
ms.assetid: 6cdca8a0-cf16-46eb-a652-0bff820625ab
author: minewiskan
ms.author: owend
ms.openlocfilehash: 07491924dbcf0bd35d049e6a7c290d49becfb45d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578526"
---
# <a name="create-a-singleton-query-in-the-data-mining-designer"></a><span data-ttu-id="05c0d-102">在数据挖掘设计器中创建单独查询</span><span class="sxs-lookup"><span data-stu-id="05c0d-102">Create a Singleton Query in the Data Mining Designer</span></span>
  <span data-ttu-id="05c0d-103">如果需要为单个事例创建预测，单独查询是非常有用的。</span><span class="sxs-lookup"><span data-stu-id="05c0d-103">A singleton query is useful if you want to create a prediction for a single case.</span></span> <span data-ttu-id="05c0d-104">有关单独查询的详细信息，请参阅 [数据挖掘查询](data-mining-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="05c0d-104">For more information about singleton queries, see [Data Mining Queries](data-mining-queries.md).</span></span>  
  
 <span data-ttu-id="05c0d-105">在数据挖掘设计器的 **“挖掘模型预测”** 选项卡中，可以创建许多不同类型的查询。</span><span class="sxs-lookup"><span data-stu-id="05c0d-105">In the **Mining Model Prediction** tab of Data Mining Designer, you can create many different types of queries.</span></span> <span data-ttu-id="05c0d-106">可以通过使用设计器或者通过键入数据挖掘扩展插件 (DMX) 语句来创建查询。</span><span class="sxs-lookup"><span data-stu-id="05c0d-106">You can create a query by using the designer, or by typing Data Mining Extensions (DMX) statements.</span></span> <span data-ttu-id="05c0d-107">还可以从设计器开始工作，并通过更改 DMX 语句或者通过添加 WHERE 或 ORDER BY 子句来修改它所创建的查询。</span><span class="sxs-lookup"><span data-stu-id="05c0d-107">You can also start with the designer and modify the query that it creates by changing the DMX statements, or by adding a WHERE or ORDER BY clause.</span></span>  
  
 <span data-ttu-id="05c0d-108">若要在查询设计视图和查询文本视图之间切换，请单击工具栏上的第一个按钮。</span><span class="sxs-lookup"><span data-stu-id="05c0d-108">To switch between the query design view and the query text view, click the first button on the toolbar.</span></span> <span data-ttu-id="05c0d-109">在查询文本视图中，可以查看预测查询生成器创建的 DMX 代码。</span><span class="sxs-lookup"><span data-stu-id="05c0d-109">When you are in the query text view, you can view the DMX code that Prediction Query Builder creates.</span></span> <span data-ttu-id="05c0d-110">您还可以运行查询，修改查询，并运行修改后的查询。</span><span class="sxs-lookup"><span data-stu-id="05c0d-110">You can also run the query, modify the query, and run the modified query.</span></span> <span data-ttu-id="05c0d-111">但是，如果切换回查询设计视图，则修改后的查询将不再继续运行。</span><span class="sxs-lookup"><span data-stu-id="05c0d-111">However, the modified query is not persisted if you switch back to the query design view.</span></span>  
  
 <span data-ttu-id="05c0d-112">下面的代码演示一个对目标邮件模型 TM_Decision_Tree 的单独查询的示例。</span><span class="sxs-lookup"><span data-stu-id="05c0d-112">The following code shows an example of a singleton query against the targeted mailing model, TM_Decision_Tree.</span></span>  
  
```  
SELECT [Bike Buyer], PredictProbability([Bike Buyer]) as ProbableBuyer  
FROM [TM_Decision_Tree]  
NATURAL PREDICTION JOIN  
(SELECT '2' AS [Number Children At Home], '45' as [Age])  
AS [t]  
```  
  
 <span data-ttu-id="05c0d-113">下列步骤说明如何创建该预测查询。</span><span class="sxs-lookup"><span data-stu-id="05c0d-113">The following steps explain how to create this prediction query.</span></span>  
  
### <a name="to-create-a-singleton-query-by-using-the-data-mining-designer"></a><span data-ttu-id="05c0d-114">使用数据挖掘设计器创建单独查询</span><span class="sxs-lookup"><span data-stu-id="05c0d-114">To create a singleton query by using the Data Mining Designer</span></span>  
  
1.  <span data-ttu-id="05c0d-115">在数据挖掘设计器中，单击 **“挖掘模型预测”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="05c0d-115">Click the **Mining Model Prediction** tab in Data Mining Designer.</span></span>  
  
2.  <span data-ttu-id="05c0d-116">在 **“挖掘模型”** 表中，单击 **“选择模型”** 。</span><span class="sxs-lookup"><span data-stu-id="05c0d-116">Click **Select Model** on the **Mining Model** table.</span></span>  
  
     <span data-ttu-id="05c0d-117">此时将打开 **“选择挖掘模型”** 对话框，以显示当前项目中存在的所有挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="05c0d-117">The **Select Mining Model** dialog box opens to show all the mining structures that exist in the current project.</span></span>  
  
     <span data-ttu-id="05c0d-118">选择要用于创建预测的模型。</span><span class="sxs-lookup"><span data-stu-id="05c0d-118">Select the model that you want to use for creating a prediction.</span></span>  
  
     <span data-ttu-id="05c0d-119">例如，若要创建本主题开头所显示的示例代码，请选择 TM_Decision_Tree，再单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="05c0d-119">For example, to create the sample code shown at the start of this topic, select TM_Decision_Tree, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="05c0d-120">在 **“挖掘模型预测”** 选项卡中，单击工具栏上的 **“单独查询”** 。</span><span class="sxs-lookup"><span data-stu-id="05c0d-120">Click **Singleton query** on the toolbar of the **Mining Model Prediction** tab.</span></span>  
  
     <span data-ttu-id="05c0d-121">该选项卡中将出现 **“单独查询输入”** 表，该表中的各列自动映射到 **“挖掘模型”** 表中的各列。</span><span class="sxs-lookup"><span data-stu-id="05c0d-121">The **Singleton Query Input** table appears on the tab, with the columns automatically mapped to the columns in the **Mining Model** table.</span></span>  
  
4.  <span data-ttu-id="05c0d-122">在 **“单独查询输入”** 表中，选择 **“值”** 列中的值，用以说明要为其创建预测的事例。</span><span class="sxs-lookup"><span data-stu-id="05c0d-122">On the **Singleton Query Input** table, select values in the **Value** column to describe the case for which you want to create a prediction.</span></span>  
  
     <span data-ttu-id="05c0d-123">例如，选择 " **2** " 作为 "家庭中的**子女数**"，然后键入 " `45` **Age**"。</span><span class="sxs-lookup"><span data-stu-id="05c0d-123">For example, select **2** for **Number Children At Home**, and then type `45` for **Age**.</span></span>  
  
5.  <span data-ttu-id="05c0d-124">将一个可预测列从 "**挖掘模型**" 表拖到该选项卡底部的 "**源**" 列。或者，您也可以为列键入一个别名。</span><span class="sxs-lookup"><span data-stu-id="05c0d-124">Drag a predictable column from the **Mining Model** table to the **Source** column at the bottom of the tab. Optionally, you can type an alias for the column.</span></span>  
  
     <span data-ttu-id="05c0d-125">例如，将 **Bike Buyer** 拖到 **“源”** 列。</span><span class="sxs-lookup"><span data-stu-id="05c0d-125">For example, drag **Bike Buyer** to the **Source** column.</span></span>  
  
6.  <span data-ttu-id="05c0d-126">通过在“源”列的下拉列表中选择“预测函数”或“自定义表达式”，向查询中添加其他函数\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="05c0d-126">Add any additional functions to the query by selecting **Prediction Function** or **Custom Expression** from the drop-down list in the **Source** column.</span></span>  
  
     <span data-ttu-id="05c0d-127">例如，单击 **“预测函数”**，再选择 **PredictProbability**。</span><span class="sxs-lookup"><span data-stu-id="05c0d-127">For example, click **Prediction Function**, and select **PredictProbability**.</span></span>  
  
7.  <span data-ttu-id="05c0d-128">在 **PredictProbability** 行中单击“条件/参数”\*\*\*\*，键入要预测的列的名称，还可以选择键入要预测的特定值。</span><span class="sxs-lookup"><span data-stu-id="05c0d-128">Click **Criteria/Argument** in the **PredictProbability** row, and type the name of the column to predict, and optionally a specific value to predict.</span></span>  
  
     <span data-ttu-id="05c0d-129">例如，键入 `[Bike Buyer], 1`。</span><span class="sxs-lookup"><span data-stu-id="05c0d-129">For example, type `[Bike Buyer], 1`.</span></span>  
  
8.  <span data-ttu-id="05c0d-130">在 **PredictProbability** 行中单击 **“别名”** 框，再键入一个表示新列的名称。</span><span class="sxs-lookup"><span data-stu-id="05c0d-130">Click the **Alias** box in the **PredictProbability** row, and type a name to refer to the new column.</span></span>  
  
     <span data-ttu-id="05c0d-131">例如，键入 `ProbableBuyer`。</span><span class="sxs-lookup"><span data-stu-id="05c0d-131">For example, type `ProbableBuyer`.</span></span>  
  
9. <span data-ttu-id="05c0d-132">在 **“挖掘模型预测”** 选项卡的工具栏上，单击 **“切换到查询结果视图”** 。</span><span class="sxs-lookup"><span data-stu-id="05c0d-132">Click **Switch to query result view** on the toolbar of the **Mining Model Prediction** tab.</span></span>  
  
     <span data-ttu-id="05c0d-133">此时将出现一个新屏幕，显示查询的结果。</span><span class="sxs-lookup"><span data-stu-id="05c0d-133">A new screen opens to show the result of the query.</span></span> <span data-ttu-id="05c0d-134">若要查看刚创建的 DMX 语句，请单击 **SQL**。</span><span class="sxs-lookup"><span data-stu-id="05c0d-134">To view the DMX statement that you just created, click **SQL**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05c0d-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="05c0d-135">See Also</span></span>  
 [<span data-ttu-id="05c0d-136">预测查询（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="05c0d-136">Prediction Queries &#40;Data Mining&#41;</span></span>](prediction-queries-data-mining.md)  
  
  
