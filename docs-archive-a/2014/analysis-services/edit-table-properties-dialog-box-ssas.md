---
title: " (SSAS) 上的 \"编辑表属性\" 对话框 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.edittablepropdb.f1
ms.assetid: 8d913e83-7246-44cc-8fc7-31729023c0d8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6664d244f5f653610b37bd628abdb2263e015c0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589938"
---
# <a name="edit-table-properties-dialog-box-ssas"></a><span data-ttu-id="ac2be-102">“编辑表属性”对话框 (SSAS)</span><span class="sxs-lookup"><span data-stu-id="ac2be-102">Edit Table Properties Dialog Box (SSAS)</span></span>
  <span data-ttu-id="ac2be-103">**“编辑表属性”** 对话框可用于查看和修改通过使用“表导入向导”导入到模型设计器中的表的属性。</span><span class="sxs-lookup"><span data-stu-id="ac2be-103">The **Edit Table Properties** dialog box enables you to view and modify the properties of tables that are imported into the model designer by using the Table Import Wizard.</span></span> <span data-ttu-id="ac2be-104">若要访问此对话框，请在模型设计器中选择表，然后在 **“表”** 菜单中单击 **“表属性”**。</span><span class="sxs-lookup"><span data-stu-id="ac2be-104">To access this dialog box, in the model designer, select a table, then click the **Table** menu, and then click **Table Properties**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="ac2be-105">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="ac2be-105">UI element list</span></span>  
 <span data-ttu-id="ac2be-106">根据您最初是通过从列表中选择表还是通过使用 SQL 查询导入数据的，此对话框的选项将有所不同。</span><span class="sxs-lookup"><span data-stu-id="ac2be-106">The options for this dialog box are different depending on whether you originally imported data by selecting tables from a list or by using a SQL query.</span></span>  
  
## <a name="table-preview-mode"></a><span data-ttu-id="ac2be-107">表预览模式</span><span class="sxs-lookup"><span data-stu-id="ac2be-107">Table Preview Mode</span></span>  
 <span data-ttu-id="ac2be-108">**表名称**</span><span class="sxs-lookup"><span data-stu-id="ac2be-108">**Table name**</span></span>  
 <span data-ttu-id="ac2be-109">显示模型中数据表的名称。</span><span class="sxs-lookup"><span data-stu-id="ac2be-109">Displays the name of the data table in the model.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ac2be-110">无法在此处编辑该名称。</span><span class="sxs-lookup"><span data-stu-id="ac2be-110">You cannot edit the name here.</span></span> <span data-ttu-id="ac2be-111">但是，可以通过右键单击模型设计器底部的表选项卡来更改表的名称。</span><span class="sxs-lookup"><span data-stu-id="ac2be-111">However, you can change the name of the table by right-clicking the table tab at the bottom of the model designer.</span></span>  
  
 <span data-ttu-id="ac2be-112">**连接名称**</span><span class="sxs-lookup"><span data-stu-id="ac2be-112">**Connection name**</span></span>  
 <span data-ttu-id="ac2be-113">显示当前正在使用的连接的名称。</span><span class="sxs-lookup"><span data-stu-id="ac2be-113">Displays the name of the connection that is currently in use.</span></span>  
  
 <span data-ttu-id="ac2be-114">**源名称**</span><span class="sxs-lookup"><span data-stu-id="ac2be-114">**Source name**</span></span>  
 <span data-ttu-id="ac2be-115">显示或更改从中获取数据的表。</span><span class="sxs-lookup"><span data-stu-id="ac2be-115">Display or change the table from which the data is obtained.</span></span>  
  
 <span data-ttu-id="ac2be-116">如果您将源更改为与当前表具有不同列的表，将显示一条消息以警告您列不相同。</span><span class="sxs-lookup"><span data-stu-id="ac2be-116">If you change the source to a table that has different columns than the current table, a message is displayed warning that the columns are different.</span></span> <span data-ttu-id="ac2be-117">然后，您必须选择要放在当前表中的列，并单击 **“保存”**。</span><span class="sxs-lookup"><span data-stu-id="ac2be-117">You must then select the columns that you want to put in the current table and click **Save**.</span></span> <span data-ttu-id="ac2be-118">您可以通过选中表左侧的复选框来替换整个表。</span><span class="sxs-lookup"><span data-stu-id="ac2be-118">You can replace the entire table by selecting the check box at the left of the table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ac2be-119">当您更改表的数据源时，您实质上是用新源表的内容替换当前表的内容。</span><span class="sxs-lookup"><span data-stu-id="ac2be-119">When you change the data source of a table, you essentially replace the contents of the current table with the contents of the new source table.</span></span>  
  
 <span data-ttu-id="ac2be-120">**列名来自**</span><span class="sxs-lookup"><span data-stu-id="ac2be-120">**Column names from**</span></span>  
 |||  
|-|-|  
|<span data-ttu-id="ac2be-121">**数据源**</span><span class="sxs-lookup"><span data-stu-id="ac2be-121">**Source**</span></span>|<span data-ttu-id="ac2be-122">选择此选项可用来自所选源表的列名替换当前列名。</span><span class="sxs-lookup"><span data-stu-id="ac2be-122">Select this option to replace the current column names with the column names from the selected source table.</span></span>|  
|<span data-ttu-id="ac2be-123">**Model**</span><span class="sxs-lookup"><span data-stu-id="ac2be-123">**Model**</span></span>|<span data-ttu-id="ac2be-124">选择此选项可使用当前列名，因为它们在模型中存在。</span><span class="sxs-lookup"><span data-stu-id="ac2be-124">Select this option to use the current column names as they exist in the model.</span></span>|  
  
 <span data-ttu-id="ac2be-125">**刷新预览**</span><span class="sxs-lookup"><span data-stu-id="ac2be-125">**Refresh preview**</span></span>  
 <span data-ttu-id="ac2be-126">单击以查看当前所选源表中的数据列。</span><span class="sxs-lookup"><span data-stu-id="ac2be-126">Click to view the columns of data in the currently selected source table.</span></span>  
  
 <span data-ttu-id="ac2be-127">**切换到**</span><span class="sxs-lookup"><span data-stu-id="ac2be-127">**Switch to**</span></span>  
 |||  
|-|-|  
|<span data-ttu-id="ac2be-128">**表预览**</span><span class="sxs-lookup"><span data-stu-id="ac2be-128">**Table preview**</span></span>|<span data-ttu-id="ac2be-129">选择此选项可以预览所选表和有限行数据。</span><span class="sxs-lookup"><span data-stu-id="ac2be-129">Select this option to preview the selected table and a limited number of rows of data.</span></span>|  
|<span data-ttu-id="ac2be-130">**查询编辑器**</span><span class="sxs-lookup"><span data-stu-id="ac2be-130">**Query editor**</span></span>|<span data-ttu-id="ac2be-131">选择此选项可以查看对所选数据源的查询。</span><span class="sxs-lookup"><span data-stu-id="ac2be-131">Select this option to view the query against the selected data source.</span></span> <span data-ttu-id="ac2be-132">此选项不适用于所有数据源。</span><span class="sxs-lookup"><span data-stu-id="ac2be-132">This option is not available for all data sources.</span></span>|  
  
 <span data-ttu-id="ac2be-133">**列标题中的复选框**</span><span class="sxs-lookup"><span data-stu-id="ac2be-133">**Checkbox in the column header**</span></span>  
 <span data-ttu-id="ac2be-134">选中该复选框可在数据导入中包括列。</span><span class="sxs-lookup"><span data-stu-id="ac2be-134">Select the checkbox to include the column in the data import.</span></span> <span data-ttu-id="ac2be-135">取消选中该复选框则从数据导入中删除列。</span><span class="sxs-lookup"><span data-stu-id="ac2be-135">Clear the checkbox to remove the column from the data import.</span></span>  
  
 <span data-ttu-id="ac2be-136">**列标题中的下箭头按钮**</span><span class="sxs-lookup"><span data-stu-id="ac2be-136">**Down-arrow button in the column header**</span></span>  
 <span data-ttu-id="ac2be-137">筛选列中的数据。</span><span class="sxs-lookup"><span data-stu-id="ac2be-137">Filter data in the column.</span></span>  
  
 <span data-ttu-id="ac2be-138">**清除行筛选器**</span><span class="sxs-lookup"><span data-stu-id="ac2be-138">**Clear row filters**</span></span>  
 <span data-ttu-id="ac2be-139">单击以删除任何已应用的筛选器。</span><span class="sxs-lookup"><span data-stu-id="ac2be-139">Click to remove any filters that have been applied.</span></span>  
  
 <span data-ttu-id="ac2be-140">**确定**</span><span class="sxs-lookup"><span data-stu-id="ac2be-140">**OK**</span></span>  
 <span data-ttu-id="ac2be-141">单击以应用您所做的所有更改，包括替换列。</span><span class="sxs-lookup"><span data-stu-id="ac2be-141">Click to apply all changes that you made, including replacing columns.</span></span>  
  
## <a name="query-design-mode"></a><span data-ttu-id="ac2be-142">查询设计模式</span><span class="sxs-lookup"><span data-stu-id="ac2be-142">Query Design Mode</span></span>  
 <span data-ttu-id="ac2be-143">**表名称**</span><span class="sxs-lookup"><span data-stu-id="ac2be-143">**Table name**</span></span>  
 <span data-ttu-id="ac2be-144">显示模型中数据表的名称。</span><span class="sxs-lookup"><span data-stu-id="ac2be-144">Displays the name of the data table in the model.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ac2be-145">您不能在此编辑该名称；但是，可以通过右键单击设计器底部的表选项卡来更改表的名称。</span><span class="sxs-lookup"><span data-stu-id="ac2be-145">You cannot edit the name here; however, you can change the name of the table by right-clicking the table tab at the bottom of the designer.</span></span>  
  
 <span data-ttu-id="ac2be-146">**连接名称**</span><span class="sxs-lookup"><span data-stu-id="ac2be-146">**Connection name**</span></span>  
 <span data-ttu-id="ac2be-147">显示当前正在使用的连接的名称。</span><span class="sxs-lookup"><span data-stu-id="ac2be-147">Displays the name of the connection that is currently in use.</span></span>  
  
 <span data-ttu-id="ac2be-148">**切换到**</span><span class="sxs-lookup"><span data-stu-id="ac2be-148">**Switch to**</span></span>  
 |||  
|-|-|  
|<span data-ttu-id="ac2be-149">**表预览**</span><span class="sxs-lookup"><span data-stu-id="ac2be-149">**Table preview**</span></span>|<span data-ttu-id="ac2be-150">选择此选项可以预览所选表和若干行数据。</span><span class="sxs-lookup"><span data-stu-id="ac2be-150">Select this option to preview the selected table and a few rows of data.</span></span>|  
|<span data-ttu-id="ac2be-151">**查询编辑器**</span><span class="sxs-lookup"><span data-stu-id="ac2be-151">**Query editor**</span></span>|<span data-ttu-id="ac2be-152">选择此选项可以查看对所选数据源发出的查询。</span><span class="sxs-lookup"><span data-stu-id="ac2be-152">Select this option to view the query that will be issued against the selected data source.</span></span>|  
  
 <span data-ttu-id="ac2be-153">**Sql 语句**</span><span class="sxs-lookup"><span data-stu-id="ac2be-153">**Sql statement**</span></span>  
 <span data-ttu-id="ac2be-154">显示对当前数据源发出的用于检索行的 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="ac2be-154">Displays the SQL statement that is issued against the current data source to retrieve rows.</span></span> <span data-ttu-id="ac2be-155">默认情况下将检索所有行，但您可以通过设计筛选器或手动编辑 SQL 语句来检索行的子集。</span><span class="sxs-lookup"><span data-stu-id="ac2be-155">By default, all rows are retrieved, but you can retrieve a subset of rows, either by designing a filter, or by manually editing the SQL statement.</span></span>  
  
 <span data-ttu-id="ac2be-156">**验证**</span><span class="sxs-lookup"><span data-stu-id="ac2be-156">**Validate**</span></span>  
 <span data-ttu-id="ac2be-157">单击以验证该语句对于所选数据源和提供程序在语法方面是否正确。</span><span class="sxs-lookup"><span data-stu-id="ac2be-157">Click to verify that the statement is syntactically correct for the selected data source and provider.</span></span>  
  
 <span data-ttu-id="ac2be-158">**设计**</span><span class="sxs-lookup"><span data-stu-id="ac2be-158">**Design**</span></span>  
 <span data-ttu-id="ac2be-159">单击以打开可视化查询设计器并生成查询语句。</span><span class="sxs-lookup"><span data-stu-id="ac2be-159">Click to open a visual query designer and build a query statement.</span></span> <span data-ttu-id="ac2be-160">有关如何使用设计器的信息，请从设计器中按 F1。</span><span class="sxs-lookup"><span data-stu-id="ac2be-160">For information about how to use the designer, press F1 from the designer.</span></span>  
  
 <span data-ttu-id="ac2be-161">**确定**</span><span class="sxs-lookup"><span data-stu-id="ac2be-161">**OK**</span></span>  
 <span data-ttu-id="ac2be-162">单击以应用您所做的所有更改，包括替换列。</span><span class="sxs-lookup"><span data-stu-id="ac2be-162">Click to apply all changes that you made, including replacing columns.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac2be-163">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ac2be-163">See Also</span></span>  
 [<span data-ttu-id="ac2be-164">表和列（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="ac2be-164">Tables and Columns &#40;SSAS Tabular&#41;</span></span>](tabular-models/tables-and-columns-ssas-tabular.md)  
  
  
