---
title: " (挖掘模型预测视图) 的设计窗格 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.prediction.design.f1
ms.assetid: 17f24c8d-43cd-4f4d-83b3-a41ee8fbe8e8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 32ac73a2d6fde38d15d1f45a8439293695749ea4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690212"
---
# <a name="design-pane-mining-model-prediction-view"></a><span data-ttu-id="17877-102">“设计”窗格（“挖掘模型预测”视图）</span><span class="sxs-lookup"><span data-stu-id="17877-102">Design Pane (Mining Model Prediction View)</span></span>
  <span data-ttu-id="17877-103">**“设计”** 窗格包含可用于生成数据挖掘预测的预测查询生成器。</span><span class="sxs-lookup"><span data-stu-id="17877-103">The **Design** pane contains the Prediction Query Builder, which you can use to build data mining predictions.</span></span> <span data-ttu-id="17877-104">您可以设计使用数据源视图中的输入数据表的预测查询来生成大量预测，也可以创建允许您提供各个值的单独预测查询。</span><span class="sxs-lookup"><span data-stu-id="17877-104">You can design prediction queries that use tables of input data from a data source view, to generate bulk predictions, or you can create singleton prediction queries, which let you provide individual values.</span></span>  
  
 <span data-ttu-id="17877-105">若要运行查询并查看结果，请切换到查询结果视图。</span><span class="sxs-lookup"><span data-stu-id="17877-105">To run the query and view the results, switch to query result view.</span></span>  
  
 <span data-ttu-id="17877-106">“查询”\*\*\*\* 视图可以显示预测查询生成器创建的数据挖掘扩展插件 (DMX) 查询。</span><span class="sxs-lookup"><span data-stu-id="17877-106">The **Query** view displays the Data Mining Extensions (DMX) query that Prediction Query Builder creates.</span></span> <span data-ttu-id="17877-107">如果您熟悉 DMX，则可以自定义此查询。</span><span class="sxs-lookup"><span data-stu-id="17877-107">If you are familiar with DMX, you can customize this query.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="17877-108">如果对查询进行任何手动更改，则当您切换回“设计”视图时会丢失您所做的更改。</span><span class="sxs-lookup"><span data-stu-id="17877-108">If you make any manual changes to the query, your changes will be lost when you switch back to Design view.</span></span> <span data-ttu-id="17877-109">如果要保存 DMX 查询，则可以将该查询复制到 Windows 剪贴板，然后将其粘贴到文本文件。</span><span class="sxs-lookup"><span data-stu-id="17877-109">If you want to save the DMX query, you can copy the query to the Windows Clipboard and then paste it to a text file.</span></span>  
  
 <span data-ttu-id="17877-110">**有关详细信息，请参阅** [数据挖掘查询](data-mining/data-mining-queries.md)</span><span class="sxs-lookup"><span data-stu-id="17877-110">**For More Information:** [Data Mining Queries](data-mining/data-mining-queries.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="17877-111">选项</span><span class="sxs-lookup"><span data-stu-id="17877-111">Options</span></span>  
 <span data-ttu-id="17877-112">**切换到查询结果视图**</span><span class="sxs-lookup"><span data-stu-id="17877-112">**Switch to query result view**</span></span>  
 <span data-ttu-id="17877-113">单击此项可以在“设计”\*\*\*\*、“查询”\*\*\*\* 和“结果”\*\*\*\* 窗格之间切换。</span><span class="sxs-lookup"><span data-stu-id="17877-113">Click to switch between the **Design**, **Query**, and **Result** panes.</span></span> <span data-ttu-id="17877-114">切换到 **“结果”** 窗格可以运行查询。</span><span class="sxs-lookup"><span data-stu-id="17877-114">Switching to the **Result** pane runs the query.</span></span>  
  
 <span data-ttu-id="17877-115">**保存查询结果**</span><span class="sxs-lookup"><span data-stu-id="17877-115">**Save the query result**</span></span>  
 <span data-ttu-id="17877-116">打开“保存数据挖掘查询结果”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="17877-116">Opens the **Save Data Mining Query Result** dialog box.</span></span>  
  
 <span data-ttu-id="17877-117">**单独查询**</span><span class="sxs-lookup"><span data-stu-id="17877-117">**Singleton query**</span></span>  
 <span data-ttu-id="17877-118">允许创建单独查询，您可以在单独查询中直接为查询提供值，而不是提供作为已知数据源的表。</span><span class="sxs-lookup"><span data-stu-id="17877-118">Enables creating a singleton query, in which you can provide values directly for the query instead of providing a table as the source of the known data.</span></span> <span data-ttu-id="17877-119">“选择输入表”\*\*\*\* 表由“单独查询输入”\*\*\*\* 表替换。</span><span class="sxs-lookup"><span data-stu-id="17877-119">The **Select Input Table(s)** table is replaced by a **Singleton Query Input** table.</span></span>  
  
 <span data-ttu-id="17877-120">**刷新查询结果**</span><span class="sxs-lookup"><span data-stu-id="17877-120">**Refresh query results**</span></span>  
 <span data-ttu-id="17877-121">重新处理预测查询。</span><span class="sxs-lookup"><span data-stu-id="17877-121">Reprocesses the prediction query.</span></span> <span data-ttu-id="17877-122">此选项仅在 **“结果”** 窗格中启用。</span><span class="sxs-lookup"><span data-stu-id="17877-122">This is enabled only in the **Result** pane.</span></span>  
  
 <span data-ttu-id="17877-123">**挖掘模型**</span><span class="sxs-lookup"><span data-stu-id="17877-123">**Mining Model**</span></span>  
 <span data-ttu-id="17877-124">显示所选的挖掘模型，您希望利用该模型来进行预测。</span><span class="sxs-lookup"><span data-stu-id="17877-124">Displays the selected mining model on which you want to base predictions.</span></span>  
  
 <span data-ttu-id="17877-125">**选择模型**</span><span class="sxs-lookup"><span data-stu-id="17877-125">**Select Model**</span></span>  
 <span data-ttu-id="17877-126">打开“选择挖掘模型”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="17877-126">Opens the **Select Mining Model** dialog box.</span></span>  
  
 <span data-ttu-id="17877-127">**选择输入表**</span><span class="sxs-lookup"><span data-stu-id="17877-127">**Select Input Table(s)**</span></span>  
 <span data-ttu-id="17877-128">显示包含预测所基于的已知数据的所选输入表。</span><span class="sxs-lookup"><span data-stu-id="17877-128">Displays the selected input tables that contain known data on which to base the predictions.</span></span>  
  
 <span data-ttu-id="17877-129">**删除表**</span><span class="sxs-lookup"><span data-stu-id="17877-129">**Delete Table**</span></span>  
 <span data-ttu-id="17877-130">删除所选择的表。</span><span class="sxs-lookup"><span data-stu-id="17877-130">Deletes the selected table.</span></span> <span data-ttu-id="17877-131">如果未选择表或者不存在表，则此按钮处于禁用状态。</span><span class="sxs-lookup"><span data-stu-id="17877-131">This button is disabled if a table has not been selected or does not exist.</span></span>  
  
 <span data-ttu-id="17877-132">**选择事例表**</span><span class="sxs-lookup"><span data-stu-id="17877-132">**Select Case Table**</span></span>  
 <span data-ttu-id="17877-133">打开“选择表”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="17877-133">Opens the **Select Table** dialog box.</span></span> <span data-ttu-id="17877-134">只有在未选择事例表时，才会显示此按钮。</span><span class="sxs-lookup"><span data-stu-id="17877-134">This button appears only if a case table has not been selected.</span></span>  
  
 <span data-ttu-id="17877-135">**选择嵌套表**</span><span class="sxs-lookup"><span data-stu-id="17877-135">**Select Nested Table**</span></span>  
 <span data-ttu-id="17877-136">打开“选择表”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="17877-136">Opens the **Select Table** dialog box.</span></span> <span data-ttu-id="17877-137">只有在已选择事例表的情况下，才会显示此按钮。</span><span class="sxs-lookup"><span data-stu-id="17877-137">This button appears only if a case table has been selected.</span></span> <span data-ttu-id="17877-138">如果关联的挖掘结构不包含嵌套表，则禁用此按钮。</span><span class="sxs-lookup"><span data-stu-id="17877-138">If the associated mining structure does not contain a nested table, this button is disabled.</span></span>  
  
 <span data-ttu-id="17877-139">**修改联接**</span><span class="sxs-lookup"><span data-stu-id="17877-139">**Modify Join**</span></span>  
 <span data-ttu-id="17877-140">打开“指定嵌套联接”\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="17877-140">Opens the **Specify Nested Join** dialog box.</span></span> <span data-ttu-id="17877-141">只有在已选择嵌套表的情况下，此按钮才处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="17877-141">This button is active only if the nested table is selected.</span></span>  
  
 <span data-ttu-id="17877-142">**单独查询输入**</span><span class="sxs-lookup"><span data-stu-id="17877-142">**Singleton Query input**</span></span>  
 <span data-ttu-id="17877-143">选择“单独查询”\*\*\*\* 按钮时，会启用此选项。</span><span class="sxs-lookup"><span data-stu-id="17877-143">Enabled when you select the **Singleton query** button.</span></span> <span data-ttu-id="17877-144">包含以下列：</span><span class="sxs-lookup"><span data-stu-id="17877-144">Contains the following columns:</span></span>  
  
|<span data-ttu-id="17877-145">值</span><span class="sxs-lookup"><span data-stu-id="17877-145">Value</span></span>|<span data-ttu-id="17877-146">说明</span><span class="sxs-lookup"><span data-stu-id="17877-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="17877-147">**挖掘模型列**</span><span class="sxs-lookup"><span data-stu-id="17877-147">**Mining Model Column**</span></span>|<span data-ttu-id="17877-148">列出在 **“挖掘模型”** 表中选择的挖掘模型中包含的挖掘模型列。</span><span class="sxs-lookup"><span data-stu-id="17877-148">Lists the mining model columns contained within the mining model that is selected in the **Mining Model** table.</span></span>|  
|<span data-ttu-id="17877-149">**值**</span><span class="sxs-lookup"><span data-stu-id="17877-149">**Value**</span></span>|<span data-ttu-id="17877-150">从包含所选挖掘模型列的各个可能状态的列表中选择一个值。</span><span class="sxs-lookup"><span data-stu-id="17877-150">Select a value from the list that contains each possible state of the selected mining model column.</span></span><br /><br /> <span data-ttu-id="17877-151">如果该列为嵌套表列，单击值单元可以打开 **“嵌套表输入”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="17877-151">If the column is a nested table column, clicking the value cell opens the **Nested Table Input** dialog box.</span></span>|  
  
 <span data-ttu-id="17877-152">**数据源**</span><span class="sxs-lookup"><span data-stu-id="17877-152">**Source**</span></span>  
 <span data-ttu-id="17877-153">选择包含要为该列使用的字段的源。</span><span class="sxs-lookup"><span data-stu-id="17877-153">Select the source that contains the field that you will use for the column.</span></span> <span data-ttu-id="17877-154">你可以使用在“挖掘模型”\*\*\*\* 表中选择的挖掘模型、在“选择输入表”\*\*\*\* 表中选择的输入表、预测函数或自定义表达式。</span><span class="sxs-lookup"><span data-stu-id="17877-154">You can either use the mining model that is selected in the **Mining Model** table, the input table or tables that are selected in the **Select Input Table(s)** table, a prediction function, or a custom expression.</span></span>  
  
 <span data-ttu-id="17877-155">可以将列从包含挖掘模型的表和输入表中拖动到单元。</span><span class="sxs-lookup"><span data-stu-id="17877-155">Columns can be dragged from the tables containing the mining model and input tables onto the cell.</span></span>  
  
 <span data-ttu-id="17877-156">**字段**</span><span class="sxs-lookup"><span data-stu-id="17877-156">**Field**</span></span>  
 <span data-ttu-id="17877-157">从派生自源表的列的列表中选择列。</span><span class="sxs-lookup"><span data-stu-id="17877-157">Select a column from the list of columns derived from the source table.</span></span> <span data-ttu-id="17877-158">如果在 **“源”** 中选择了 **“预测函数”**，则此字段将包含所选挖掘模型中可用的预测函数。</span><span class="sxs-lookup"><span data-stu-id="17877-158">If you selected **Prediction Function** in **Source**, this contains the prediction function available for the selected mining model.</span></span>  
  
 <span data-ttu-id="17877-159">**组**</span><span class="sxs-lookup"><span data-stu-id="17877-159">**Group**</span></span>  
 <span data-ttu-id="17877-160">与“和/或”\*\*\*\* 列一起使用，将表达式组合到一起。</span><span class="sxs-lookup"><span data-stu-id="17877-160">Use with the **And/Or** column to group expressions together.</span></span> <span data-ttu-id="17877-161">例如，`(expr1 Or expr2) And expr3`。</span><span class="sxs-lookup"><span data-stu-id="17877-161">For example, `(expr1 Or expr2) And expr3`.</span></span>  
  
 <span data-ttu-id="17877-162">**And/Or**</span><span class="sxs-lookup"><span data-stu-id="17877-162">**And/Or**</span></span>  
 <span data-ttu-id="17877-163">用于创建逻辑查询。</span><span class="sxs-lookup"><span data-stu-id="17877-163">Use to create a logical query.</span></span> <span data-ttu-id="17877-164">例如，`(expr1 Or expr2) And expr3`。</span><span class="sxs-lookup"><span data-stu-id="17877-164">For example, `(expr1 Or expr2) And expr3`.</span></span>  
  
 <span data-ttu-id="17877-165">**条件/参数**</span><span class="sxs-lookup"><span data-stu-id="17877-165">**Criteria/Argument**</span></span>  
 <span data-ttu-id="17877-166">指定应用于该列的条件表达式或用户表达式。</span><span class="sxs-lookup"><span data-stu-id="17877-166">Specify a condition or user expression that applies to the column.</span></span> <span data-ttu-id="17877-167">可以将列从包含挖掘模型的表和输入表中拖动到单元。</span><span class="sxs-lookup"><span data-stu-id="17877-167">Columns can be dragged from the tables containing the mining model and input tables onto the cell.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17877-168">另请参阅</span><span class="sxs-lookup"><span data-stu-id="17877-168">See Also</span></span>  
 <span data-ttu-id="17877-169">[数据挖掘扩展插件 &#40;DMX&#41; 语句参考](/sql/dmx/data-mining-extensions-dmx-statements) </span><span class="sxs-lookup"><span data-stu-id="17877-169">[Data Mining Extensions &#40;DMX&#41; Statement Reference](/sql/dmx/data-mining-extensions-dmx-statements) </span></span>  
 <span data-ttu-id="17877-170">[数据挖掘查询接口](data-mining/data-mining-query-tools.md) </span><span class="sxs-lookup"><span data-stu-id="17877-170">[Data Mining Query Interfaces](data-mining/data-mining-query-tools.md) </span></span>  
 [<span data-ttu-id="17877-171">预测查询生成器（数据挖掘）</span><span class="sxs-lookup"><span data-stu-id="17877-171">Prediction Query Builder &#40;Data Mining&#41;</span></span>](prediction-query-builder-data-mining.md)  
  
  
