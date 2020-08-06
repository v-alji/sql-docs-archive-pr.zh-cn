---
title: 使用预测查询生成器创建预测查询 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- prediction queries [Analysis Services]
- Mining Model Prediction [Analysis Services], prediction queries
ms.assetid: e02836e5-dd8c-4c97-a078-840ae79d3660
author: minewiskan
ms.author: owend
ms.openlocfilehash: 13f39de4085cb74949e9540570d574c09e72ee27
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578528"
---
# <a name="create-a-prediction-query-using-the-prediction-query-builder"></a><span data-ttu-id="43071-102">使用预测查询生成器创建预测查询</span><span class="sxs-lookup"><span data-stu-id="43071-102">Create a Prediction Query Using the Prediction Query Builder</span></span>
  <span data-ttu-id="43071-103">可在 BI Development Studio 中生成数据挖掘解决方案时创建预测查询，或在 SQL Server Management Studio 中右键单击现有挖掘模型，然后选择“生成预测查询”\*\*\*\* 选项以创建预测查询。</span><span class="sxs-lookup"><span data-stu-id="43071-103">You can create prediction queries either while you are building a data mining solution in BI Development Studio, or by right-clicking an existing mining model in SQL Server Management Studio, and then choosing the option, **Build Prediction Query**.</span></span>  
  
 <span data-ttu-id="43071-104">“预测查询生成器”\*\*\*\* 包含以下三种设计模式，可单击左上角的图标在这三种模式之间切换。</span><span class="sxs-lookup"><span data-stu-id="43071-104">The **Prediction Query Builder** has the following three design modes, which you can switch among by clicking the icons in the upper-left corner.</span></span>  
  
-   <span data-ttu-id="43071-105">**设计**</span><span class="sxs-lookup"><span data-stu-id="43071-105">**Design**</span></span>  
  
-   <span data-ttu-id="43071-106">**查询**</span><span class="sxs-lookup"><span data-stu-id="43071-106">**Query**</span></span>  
  
-   <span data-ttu-id="43071-107">**结果**</span><span class="sxs-lookup"><span data-stu-id="43071-107">**Result**</span></span>  
  
 <span data-ttu-id="43071-108">利用 **“设计”** 模式，您可生成预测查询，方式为选择输入数据，将数据映射到模型中，然后将预测函数添加到使用网格生成的语句中。</span><span class="sxs-lookup"><span data-stu-id="43071-108">**Design** mode lets you build a prediction query by choosing input data, mapping the data to the model, and then adding prediction functions into statements you build by using the grid.</span></span> <span data-ttu-id="43071-109">设计网格包含以下生成块：</span><span class="sxs-lookup"><span data-stu-id="43071-109">The design grid contains these building blocks:</span></span>  
  
 <span data-ttu-id="43071-110">**数据源**</span><span class="sxs-lookup"><span data-stu-id="43071-110">**Source**</span></span>  
 <span data-ttu-id="43071-111">选择新列的源。</span><span class="sxs-lookup"><span data-stu-id="43071-111">Choose the source of the new column.</span></span> <span data-ttu-id="43071-112">您可使用挖掘模型中的列、数据源视图中包含的输入表、预测函数或自定义表达式。</span><span class="sxs-lookup"><span data-stu-id="43071-112">You can use columns from the mining model, input tables included in the data source view, a prediction function, or a customized expression.</span></span>  
  
 <span data-ttu-id="43071-113">**字段**</span><span class="sxs-lookup"><span data-stu-id="43071-113">**Field**</span></span>  
 <span data-ttu-id="43071-114">确定与“源”\*\*\*\* 列中的选择相关联的特定列或函数。</span><span class="sxs-lookup"><span data-stu-id="43071-114">Determines the specific column or function that is associated with the selection in the **Source** column.</span></span>  
  
 <span data-ttu-id="43071-115">**Alias**</span><span class="sxs-lookup"><span data-stu-id="43071-115">**Alias**</span></span>  
 <span data-ttu-id="43071-116">确定如何在结果集中命名列。</span><span class="sxs-lookup"><span data-stu-id="43071-116">Determines how the column is to be named in the result set.</span></span>  
  
 <span data-ttu-id="43071-117">**显示**</span><span class="sxs-lookup"><span data-stu-id="43071-117">**Show**</span></span>  
 <span data-ttu-id="43071-118">确定在“源”\*\*\*\* 列中选择的内容是否显示在结果中。</span><span class="sxs-lookup"><span data-stu-id="43071-118">Determines whether the selection in the **Source** column is displayed in the results.</span></span>  
  
 <span data-ttu-id="43071-119">**组**</span><span class="sxs-lookup"><span data-stu-id="43071-119">**Group**</span></span>  
 <span data-ttu-id="43071-120">通过使用括号来与“和/或”\*\*\*\* 列一起使用以便将表达式组合到一起。</span><span class="sxs-lookup"><span data-stu-id="43071-120">Works with the **And/Or** column to group expressions together by using parentheses.</span></span> <span data-ttu-id="43071-121">例如，(expr1 or expr2) and expr3。</span><span class="sxs-lookup"><span data-stu-id="43071-121">For example, (expr1 or expr2) and expr3.</span></span>  
  
 <span data-ttu-id="43071-122">**And/Or**</span><span class="sxs-lookup"><span data-stu-id="43071-122">**And/Or**</span></span>  
 <span data-ttu-id="43071-123">在查询中创建逻辑。</span><span class="sxs-lookup"><span data-stu-id="43071-123">Creates logic in the query.</span></span> <span data-ttu-id="43071-124">例如，(expr1 or expr2) and expr3。</span><span class="sxs-lookup"><span data-stu-id="43071-124">For example, (expr1 or expr2) and expr3.</span></span>  
  
 <span data-ttu-id="43071-125">**条件/参数**</span><span class="sxs-lookup"><span data-stu-id="43071-125">**Criteria/Argument**</span></span>  
 <span data-ttu-id="43071-126">指定应用于该列的条件或用户表达式。</span><span class="sxs-lookup"><span data-stu-id="43071-126">Specifies a condition or user expression that applies to the column.</span></span> <span data-ttu-id="43071-127">您可以将列从表拖至该单元格。</span><span class="sxs-lookup"><span data-stu-id="43071-127">You can drag columns from the tables to the cell.</span></span>  
  
 <span data-ttu-id="43071-128">“查询”\*\*\*\* 模式提供了一个可用于直接访问数据挖掘扩展插件 (DMX) 语言的文本编辑器，以及一个输入数据和模型列的视图。</span><span class="sxs-lookup"><span data-stu-id="43071-128">**Query** mode provides a text editor that gives you direct access to the Data Mining Extensions (DMX) language, along with a view of the input data and model columns.</span></span> <span data-ttu-id="43071-129">选择 **“查询”** 模式时，一个基本文本编辑器将替换用于定义查询的网格。</span><span class="sxs-lookup"><span data-stu-id="43071-129">When you select **Query** mode, the grid that you used to define the query is replaced by a basic text editor.</span></span> <span data-ttu-id="43071-130">您可使用此编辑器复制并保存编写的查询，或从剪贴板将其粘贴到现有 DMX 查询中，然后运行它们。</span><span class="sxs-lookup"><span data-stu-id="43071-130">You can use this editor to copy and save queries you have composed, or to paste in existing DMX queries and from the Clipboard and run them.</span></span>  
  
 <span data-ttu-id="43071-131">**“结果”** 视图运行当前查询，并将结果显示在网格中。</span><span class="sxs-lookup"><span data-stu-id="43071-131">**Result** view runs the current query and displays the results in a grid.</span></span> <span data-ttu-id="43071-132">如果基础数据已更改，并且要重新运行该查询，请单击状态栏的“开始”按钮。</span><span class="sxs-lookup"><span data-stu-id="43071-132">If the underlying data has changed and you want to rerun the query, click the Play button in the status bar</span></span>  
  
 <span data-ttu-id="43071-133">可结合使用可视工具和文本编辑器来设计数据挖掘查询。</span><span class="sxs-lookup"><span data-stu-id="43071-133">You can design a data mining query by using a combination of the visual tools and the text editor.</span></span> <span data-ttu-id="43071-134">如果在文本编辑器中键入对查询的更改，并切换回 **“设计”** 视图，则所有更改都将丢失，查询将恢复到预测查询生成器所创建的原始查询。本主题指导您使用图形查询生成器。</span><span class="sxs-lookup"><span data-stu-id="43071-134">If you type changes to the query in the text editor and switch back to the **Design** view, all the changes are lost, and the query reverts to the original query created by Prediction Query Builder This topic walks you through use of the graphical query builder.</span></span>  
  
### <a name="to-create-a-prediction-query"></a><span data-ttu-id="43071-135">创建预测查询</span><span class="sxs-lookup"><span data-stu-id="43071-135">To create a prediction query</span></span>  
  
1.  <span data-ttu-id="43071-136">在数据挖掘设计器中，单击 **“挖掘模型预测”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="43071-136">Click the **Mining Model Prediction** tab in Data Mining Designer.</span></span>  
  
2.  <span data-ttu-id="43071-137">在 **“挖掘模型”** 表中，单击 **“选择模型”** 。</span><span class="sxs-lookup"><span data-stu-id="43071-137">Click **Select Model** on the **Mining Model** table.</span></span>  
  
     <span data-ttu-id="43071-138">此时将打开 **“选择挖掘模型”** 对话框，以显示当前项目中存在的所有挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="43071-138">The **Select Mining Model** dialog box opens to show all the mining structures that exist in the current project.</span></span>  
  
3.  <span data-ttu-id="43071-139">选择要为其创建预测的模型，再单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="43071-139">Select the model on which you want to create a prediction, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="43071-140">在“选择输入表”\*\*\*\* 表上，单击“选择事例表”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="43071-140">On the **Select Input Table(s)** table, click **Select Case Table**.</span></span>  
  
     <span data-ttu-id="43071-141">将打开 **“选择表”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="43071-141">The **Select Table** dialog box opens.</span></span>  
  
5.  <span data-ttu-id="43071-142">在 **“数据源”** 列表中选择数据源，该数据源应当包含创建预测所基于的数据。</span><span class="sxs-lookup"><span data-stu-id="43071-142">In the **Data Source** list, select the data source that contains the data on which to create a prediction.</span></span>  
  
6.  <span data-ttu-id="43071-143">在“表/视图名称”\*\*\*\* 框中选择包含创建预测所基于的数据的表，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="43071-143">In the **Table/View Name** box, select the table that contains the data on which to create a prediction, and then click **OK**.</span></span>  
  
     <span data-ttu-id="43071-144">选择输入表之后，预测查询生成器便会根据各列的名称在挖掘模型和输入表之间创建默认映射。</span><span class="sxs-lookup"><span data-stu-id="43071-144">After you select the input table, Prediction Query Builder creates a default mapping between the mining model and the input table, based on the names of the columns.</span></span> <span data-ttu-id="43071-145">若要删除映射，请单击以选择相应的行（该行将“挖掘模型”\*\*\*\* 表中的列链接到“选择输入表”\*\*\*\* 表中的被映射列），再按 Delete 键。</span><span class="sxs-lookup"><span data-stu-id="43071-145">To delete a mapping, click to select the line that links the column in the **Mining Model** table to the mapped column in the **Select Input Table(s)** table, and then press DELETE.</span></span> <span data-ttu-id="43071-146">也可以手动创建映射，方法是单击“选择输入表”\*\*\*\* 表中的列，然后将其拖到“挖掘模型”\*\*\*\* 表中对应的列上。</span><span class="sxs-lookup"><span data-stu-id="43071-146">You can also manually create mappings by clicking a column in the **Select Input Table(s)** table and dragging it onto the corresponding column in the **Mining Model** table.</span></span>  
  
7.  <span data-ttu-id="43071-147">将以下三种类型的信息的任意组合添加到预测查询生成器网格中：</span><span class="sxs-lookup"><span data-stu-id="43071-147">Add any combination of the following three types of information to the Prediction Query Builder grid:</span></span>  
  
    -   <span data-ttu-id="43071-148">**“挖掘模型”** 框中的可预测列。</span><span class="sxs-lookup"><span data-stu-id="43071-148">Predictable columns from the **Mining Model** box.</span></span>  
  
    -   <span data-ttu-id="43071-149">“选择输入表”\*\*\*\* 框中的输入列的任意组合。</span><span class="sxs-lookup"><span data-stu-id="43071-149">Any combination of input columns from the **Select Input Table(s)** box.</span></span>  
  
    -   <span data-ttu-id="43071-150">预测函数</span><span class="sxs-lookup"><span data-stu-id="43071-150">Prediction functions</span></span>  
  
8.  <span data-ttu-id="43071-151">单击 **“挖掘模型预测”** 选项卡的工具栏上的第一个按钮，以运行查询，再选择 **“结果”**。</span><span class="sxs-lookup"><span data-stu-id="43071-151">Run the query by clicking the first button on the toolbar of the **Mining Model Prediction** tab, and then selecting **Result**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43071-152">另请参阅</span><span class="sxs-lookup"><span data-stu-id="43071-152">See Also</span></span>  
 <span data-ttu-id="43071-153">[在数据挖掘设计器中创建单独查询](create-a-singleton-query-in-the-data-mining-designer.md) </span><span class="sxs-lookup"><span data-stu-id="43071-153">[Create a Singleton Query in the Data Mining Designer](create-a-singleton-query-in-the-data-mining-designer.md) </span></span>  
 [<span data-ttu-id="43071-154">数据挖掘查询</span><span class="sxs-lookup"><span data-stu-id="43071-154">Data Mining Queries</span></span>](data-mining-queries.md)  
  
  
