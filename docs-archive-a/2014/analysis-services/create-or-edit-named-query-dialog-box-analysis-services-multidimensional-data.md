---
title: "\"创建或编辑命名查询\" 对话框 (Analysis Services 多维数据) |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dsvdesigner.createnamedquery.f1
helpviewer_keywords:
- Create Named Query dialog box
ms.assetid: 8e192ad6-a0b1-4e21-bb3f-087c93e62941
author: minewiskan
ms.author: owend
ms.openlocfilehash: cb255a44d2dde18e8d5e20343c7c5396f2e867d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580472"
---
# <a name="create-or-edit-named-query-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="8e184-102">“创建或编辑命名查询”对话框（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="8e184-102">Create or Edit Named Query Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="8e184-103">可以使用 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中的“创建/编辑命名查询”对话框，在数据源视图设计器中创建或编辑命名查询。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="8e184-103">Use the **Create/Edit Named Query** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to create or edit a named query in **Data Source View Designer**.</span></span> <span data-ttu-id="8e184-104">可以将命名查询视为表，基于该表可以建立其他 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 对象。</span><span class="sxs-lookup"><span data-stu-id="8e184-104">A named query can be treated as a table, on which you can base other [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] objects.</span></span> <span data-ttu-id="8e184-105">可以通过执行以下操作之一显示“创建/编辑命名查询”对话框：\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="8e184-105">You can display the **Create/Edit Named Query** dialog box by:</span></span>  
  
-   <span data-ttu-id="8e184-106">在 **数据源视图设计器** 的 **“工具栏”** 窗格上，单击 **“新建命名查询”**。</span><span class="sxs-lookup"><span data-stu-id="8e184-106">Clicking **New Named Query** on the **Toolbar** pane of **Data Source View Designer**.</span></span>  
  
-   <span data-ttu-id="8e184-107">右键单击数据源视图设计器的“关系图”窗格，再选择“新建命名查询”。\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="8e184-107">Right-clicking the **Diagram** pane of **Data Source View Designer** and selecting **New Named Query**.</span></span>  
  
-   <span data-ttu-id="8e184-108">在数据源视图设计器的“关系图”窗格或“表”窗格中，右键单击某个命名查询的名称，再选择“编辑命名查询”。\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="8e184-108">Right-clicking the name of a named query in the **Diagram** or **Tables** pane of **Data Source View Designer** and selecting **Edit Named Query**.</span></span>  
  
 <span data-ttu-id="8e184-109">输入的查询必须是基本访问接口的有效查询命令。</span><span class="sxs-lookup"><span data-stu-id="8e184-109">The query entered must be a valid query command for the underlying provider.</span></span> <span data-ttu-id="8e184-110">查询将通过基本访问接口进行处理，以便进行验证，并用于标识返回的列。</span><span class="sxs-lookup"><span data-stu-id="8e184-110">The query is prepared with the underlying provider for validation, and to identify the columns returned.</span></span> <span data-ttu-id="8e184-111">该对话框可以显示两个视图：</span><span class="sxs-lookup"><span data-stu-id="8e184-111">The dialog box can present two views:</span></span>  
  
-   <span data-ttu-id="8e184-112">Visual Database Tools (VDT) 查询生成器</span><span class="sxs-lookup"><span data-stu-id="8e184-112">Visual Database Tools (VDT) Query Builder</span></span>  
  
     <span data-ttu-id="8e184-113">对于所有用户，VDT 查询生成器视图提供了一组用户界面工具，用于以可视方式构造和测试 SQL 查询。</span><span class="sxs-lookup"><span data-stu-id="8e184-113">For all users, the VDT Query Builder view provides a set of user interface tools for visually constructing and testing a SQL query.</span></span>  
  
-   <span data-ttu-id="8e184-114">一般查询生成器</span><span class="sxs-lookup"><span data-stu-id="8e184-114">Generic Query Builder</span></span>  
  
     <span data-ttu-id="8e184-115">对于高级用户，一般查询生成器视图提供了一个更为简单直接的用户界面，用于构造和测试 SQL 查询。</span><span class="sxs-lookup"><span data-stu-id="8e184-115">For advanced users, the Generic Query Builder view provides a simpler, more direct user interface for constructing and testing a SQL query.</span></span>  
  
## <a name="options"></a><span data-ttu-id="8e184-116">选项</span><span class="sxs-lookup"><span data-stu-id="8e184-116">Options</span></span>  
 <span data-ttu-id="8e184-117">**名称**</span><span class="sxs-lookup"><span data-stu-id="8e184-117">**Name**</span></span>  
 <span data-ttu-id="8e184-118">键入查询的名称。</span><span class="sxs-lookup"><span data-stu-id="8e184-118">Type the name of the query.</span></span>  
  
 <span data-ttu-id="8e184-119">**说明**</span><span class="sxs-lookup"><span data-stu-id="8e184-119">**Description**</span></span>  
 <span data-ttu-id="8e184-120">键入查询的说明（可选）。</span><span class="sxs-lookup"><span data-stu-id="8e184-120">Type the optional description of the query.</span></span>  
  
 <span data-ttu-id="8e184-121">**数据源**</span><span class="sxs-lookup"><span data-stu-id="8e184-121">**Data Source**</span></span>  
 <span data-ttu-id="8e184-122">为查询指定数据源。</span><span class="sxs-lookup"><span data-stu-id="8e184-122">Specifies the data source for the query.</span></span>  
  
 <span data-ttu-id="8e184-123">**查询定义**</span><span class="sxs-lookup"><span data-stu-id="8e184-123">**Query definition**</span></span>  
 <span data-ttu-id="8e184-124">查询定义根据选定的视图提供用于定义和测试查询的一个工具栏和多个窗格。</span><span class="sxs-lookup"><span data-stu-id="8e184-124">The query definition provides a toolbar and panes in which to define and test the query, depending on the selected view.</span></span>  
  
 <span data-ttu-id="8e184-125">**工具栏**</span><span class="sxs-lookup"><span data-stu-id="8e184-125">**Toolbar**</span></span>  
 <span data-ttu-id="8e184-126">使用工具栏可以管理数据集、选择要显示的窗格以及控制各种查询函数。</span><span class="sxs-lookup"><span data-stu-id="8e184-126">Use the toolbar to manage datasets, select panes to display, and control various query functions.</span></span>  
  
|<span data-ttu-id="8e184-127">值</span><span class="sxs-lookup"><span data-stu-id="8e184-127">Value</span></span>|<span data-ttu-id="8e184-128">说明</span><span class="sxs-lookup"><span data-stu-id="8e184-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8e184-129">**切换到一般查询生成器**</span><span class="sxs-lookup"><span data-stu-id="8e184-129">**Switch to Generic Query Builder**</span></span>|<span data-ttu-id="8e184-130">选择此选项将只显示可用于一般查询生成器视图的选项。</span><span class="sxs-lookup"><span data-stu-id="8e184-130">Select to display only the options available to the Generic Query Builder view.</span></span> <span data-ttu-id="8e184-131">仅显示下列选项：</span><span class="sxs-lookup"><span data-stu-id="8e184-131">Only the following options are displayed:</span></span><br /><span data-ttu-id="8e184-132">**SQL 窗格**</span><span class="sxs-lookup"><span data-stu-id="8e184-132">**SQL pane**</span></span><br /><span data-ttu-id="8e184-133">**结果窗格**</span><span class="sxs-lookup"><span data-stu-id="8e184-133">**Result pane**</span></span><br /><span data-ttu-id="8e184-134">**“工具栏”**，只包含 **“切换到 VDT 查询生成器”** 和 **“运行”**</span><span class="sxs-lookup"><span data-stu-id="8e184-134">**Toolbar**, containing only **Switch to VDT Query Builder** and **Run**</span></span><br /><br /> <br /><br /> <span data-ttu-id="8e184-135">注意：只有在选择了“切换到 VDT 查询生成器”时，才会显示此选项。 \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="8e184-135">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="8e184-136">**“切换到 VDT 查询生成器”**</span><span class="sxs-lookup"><span data-stu-id="8e184-136">**Switch to VDT Query Builder**</span></span>|<span data-ttu-id="8e184-137">选择此选项将显示可用于 Visual Database Tools (VDT) 查询生成器视图的所有选项。</span><span class="sxs-lookup"><span data-stu-id="8e184-137">Select to display all of the options available to the Visual Database Tools (VDT) Query Builder view.</span></span><br /><br /> <span data-ttu-id="8e184-138">注意：只有选定了“切换到一般查询生成器” \*\*\*\* ，才会显示此选项。</span><span class="sxs-lookup"><span data-stu-id="8e184-138">Note: This option is displayed only if **Switch to Generic Query Builder** is selected.</span></span>|  
|<span data-ttu-id="8e184-139">**显示/隐藏关系图窗格**</span><span class="sxs-lookup"><span data-stu-id="8e184-139">**Show/Hide Diagram Pane**</span></span>|<span data-ttu-id="8e184-140">显示或隐藏 **关系图窗格**。</span><span class="sxs-lookup"><span data-stu-id="8e184-140">Shows or hides the **Diagram pane**.</span></span><br /><br /> <span data-ttu-id="8e184-141">**注意**仅当选择了 "**切换到 VDT 查询生成器**" 时，才会显示此选项。</span><span class="sxs-lookup"><span data-stu-id="8e184-141">**Note** This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="8e184-142">**显示/隐藏网格窗格**</span><span class="sxs-lookup"><span data-stu-id="8e184-142">**Show/Hide Grid Pane**</span></span>|<span data-ttu-id="8e184-143">显示或隐藏 **网格窗格**。</span><span class="sxs-lookup"><span data-stu-id="8e184-143">Shows or hides the **Grid pane**.</span></span><br /><br /> <span data-ttu-id="8e184-144">注意：只有在选择了“切换到 VDT 查询生成器”时，才会显示此选项。 \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="8e184-144">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="8e184-145">**显示/隐藏 SQL 窗格**</span><span class="sxs-lookup"><span data-stu-id="8e184-145">**Show/Hide SQL Pane**</span></span>|<span data-ttu-id="8e184-146">显示或隐藏 **SQL 窗格**。</span><span class="sxs-lookup"><span data-stu-id="8e184-146">Shows or hides the **SQL pane**.</span></span><br /><br /> <span data-ttu-id="8e184-147">注意：只有在选择了“切换到 VDT 查询生成器”时，才会显示此选项。 \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="8e184-147">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="8e184-148">**显示/隐藏结果窗格**</span><span class="sxs-lookup"><span data-stu-id="8e184-148">**Show/Hide Result Pane**</span></span>|<span data-ttu-id="8e184-149">显示或隐藏 **结果窗格**。</span><span class="sxs-lookup"><span data-stu-id="8e184-149">Shows or hides the **Result pane**.</span></span><br /><br /> <span data-ttu-id="8e184-150">注意：只有在选择了“切换到 VDT 查询生成器”时，才会显示此选项。 \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="8e184-150">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="8e184-151">**Run**</span><span class="sxs-lookup"><span data-stu-id="8e184-151">**Run**</span></span>|<span data-ttu-id="8e184-152">运行查询。</span><span class="sxs-lookup"><span data-stu-id="8e184-152">Runs the query.</span></span> <span data-ttu-id="8e184-153">结果将显示在 "**结果" 窗格**中。</span><span class="sxs-lookup"><span data-stu-id="8e184-153">Results are displayed in the **Result pane**.</span></span>|  
|<span data-ttu-id="8e184-154">**验证 SQL**</span><span class="sxs-lookup"><span data-stu-id="8e184-154">**Verify SQL**</span></span>|<span data-ttu-id="8e184-155">验证查询中的 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="8e184-155">Verifies the SQL statement in the query.</span></span><br /><br /> <span data-ttu-id="8e184-156">注意：只有在选择了“切换到 VDT 查询生成器”时，才会显示此选项。 \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="8e184-156">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="8e184-157">**升序排序**</span><span class="sxs-lookup"><span data-stu-id="8e184-157">**Sort Ascending**</span></span>|<span data-ttu-id="8e184-158">依据 **网格窗格**中的所选列对输出行按升序排序。</span><span class="sxs-lookup"><span data-stu-id="8e184-158">Sorts output rows on the selected column in the **Grid pane**, in ascending order.</span></span><br /><br /> <span data-ttu-id="8e184-159">注意：只有在选择了“切换到 VDT 查询生成器”时，才会显示此选项。 \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="8e184-159">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="8e184-160">**降序排序**</span><span class="sxs-lookup"><span data-stu-id="8e184-160">**Sort Descending**</span></span>|<span data-ttu-id="8e184-161">依据 **网格窗格**中的所选列对输出行按降序排序。</span><span class="sxs-lookup"><span data-stu-id="8e184-161">Sorts output rows on the selected column in the **Grid pane**, in descending order.</span></span><br /><br /> <span data-ttu-id="8e184-162">注意：只有在选择了“切换到 VDT 查询生成器”时，才会显示此选项。 \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="8e184-162">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="8e184-163">**删除筛选器**</span><span class="sxs-lookup"><span data-stu-id="8e184-163">**Remove Filter**</span></span>|<span data-ttu-id="8e184-164">删除 **网格窗格**中所选行的排序条件（如果适用的话）。</span><span class="sxs-lookup"><span data-stu-id="8e184-164">Removes sort criteria, if applicable, for the selected row in the **Grid pane**.</span></span><br /><br /> <span data-ttu-id="8e184-165">注意：只有在选择了“切换到 VDT 查询生成器”时，才会显示此选项。 \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="8e184-165">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="8e184-166">**使用 Group By**</span><span class="sxs-lookup"><span data-stu-id="8e184-166">**Use Group By**</span></span>|<span data-ttu-id="8e184-167">向查询中添加分组功能。</span><span class="sxs-lookup"><span data-stu-id="8e184-167">Adds grouping functionality to the query.</span></span><br /><br /> <span data-ttu-id="8e184-168">注意：只有在选择了“切换到 VDT 查询生成器”时，才会显示此选项。 \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="8e184-168">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="8e184-169">**添加表**</span><span class="sxs-lookup"><span data-stu-id="8e184-169">**Add Table**</span></span>|<span data-ttu-id="8e184-170">显示 **“添加表”** 对话框，以便向查询中添加新表或新视图。</span><span class="sxs-lookup"><span data-stu-id="8e184-170">Displays the **Add Table** dialog box to add a new table or view to the query.</span></span> <span data-ttu-id="8e184-171">有关“添加表”\*\*\*\* 对话框的详细信息，请参阅[“添加表”对话框（Analysis Services - 多维数据）](add-table-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="8e184-171">For more information about the **Add Table** dialog box, see [Add Table Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](add-table-dialog-box-analysis-services-multidimensional-data.md).</span></span><br /><br /> <span data-ttu-id="8e184-172">注意：只有在选择了“切换到 VDT 查询生成器”时，才会显示此选项。 \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="8e184-172">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
  
 <span data-ttu-id="8e184-173">**关系图窗格**</span><span class="sxs-lookup"><span data-stu-id="8e184-173">**Diagram pane**</span></span>  
 <span data-ttu-id="8e184-174">以关系图的形式显示查询所引用的对象。</span><span class="sxs-lookup"><span data-stu-id="8e184-174">Displays the objects referenced by the query as a diagram.</span></span> <span data-ttu-id="8e184-175">关系图可显示查询中包含的表以及这些表的联接方式。</span><span class="sxs-lookup"><span data-stu-id="8e184-175">The diagram shows the tables included in the query, and how they are joined.</span></span> <span data-ttu-id="8e184-176">选中或清除表中某列旁边的复选框，即可在查询输出中添加或删除该列。</span><span class="sxs-lookup"><span data-stu-id="8e184-176">Select or clear the check box next to a column in a table to add or remove it from the query output.</span></span>  
  
 <span data-ttu-id="8e184-177">向查询中添加表时，该对话框将根据表中的键创建表之间的联接。</span><span class="sxs-lookup"><span data-stu-id="8e184-177">When you add tables to the query, the dialog box creates joins between tables based on the keys in the table.</span></span> <span data-ttu-id="8e184-178">若要添加联接，请将一个表中的字段拖到另一个表中的字段上。</span><span class="sxs-lookup"><span data-stu-id="8e184-178">To add a join, drag a field from one table onto a field in another table.</span></span> <span data-ttu-id="8e184-179">若要管理某个联接，请右键单击该联接。</span><span class="sxs-lookup"><span data-stu-id="8e184-179">To manage a join, right-click the join.</span></span>  
  
 <span data-ttu-id="8e184-180">右键单击“关系图窗格”，可以添加或删除表，选择所有表，以及显示或隐藏窗格。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="8e184-180">Right-click the **Diagram pane** to add or remove tables, select all the tables, and show or hide panes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8e184-181">**关系图窗格**、 **网格窗格**和 **SQL 窗格** 中的内容是同步的，这样其中一个窗格的更改可以反映在其他两个窗格中。</span><span class="sxs-lookup"><span data-stu-id="8e184-181">The contents of the **Diagram pane**, **Grid pane**, and **SQL pane** are synchronized, so that changes in one pane are reflected in the other two panes.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8e184-182">该对话框不支持更改查询类型。</span><span class="sxs-lookup"><span data-stu-id="8e184-182">Changing query types is not supported by the dialog box.</span></span>  
  
 <span data-ttu-id="8e184-183">**“网格”窗格**</span><span class="sxs-lookup"><span data-stu-id="8e184-183">**Grid pane**</span></span>  
 <span data-ttu-id="8e184-184">在网格中显示查询所引用的对象。</span><span class="sxs-lookup"><span data-stu-id="8e184-184">Displays the objects referenced by the query in a grid.</span></span> <span data-ttu-id="8e184-185">使用此窗格可以在查询中添加和删除列，以及更改每一列的设置。</span><span class="sxs-lookup"><span data-stu-id="8e184-185">You can use this pane to add and remove columns to the query and change the settings for each column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8e184-186">**关系图窗格**、 **网格窗格**和 **SQL 窗格** 中的内容是同步的，这样其中一个窗格的更改可以反映在其他两个窗格中。</span><span class="sxs-lookup"><span data-stu-id="8e184-186">The contents of the **Diagram pane**, **Grid pane**, and **SQL pane** are synchronized, so that changes in one pane are reflected in the other two panes.</span></span>  
  
 <span data-ttu-id="8e184-187">**SQL 窗格**</span><span class="sxs-lookup"><span data-stu-id="8e184-187">**SQL pane**</span></span>  
 <span data-ttu-id="8e184-188">将查询显示为 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="8e184-188">Displays the query as a SQL statement.</span></span> <span data-ttu-id="8e184-189">键入内容即可更改查询的 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="8e184-189">Type to change the SQL statement for the query.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8e184-190">**关系图窗格**、 **网格窗格**和 **SQL 窗格** 中的内容是同步的，这样其中一个窗格的更改可以反映在其他两个窗格中。</span><span class="sxs-lookup"><span data-stu-id="8e184-190">The contents of the **Diagram pane**, **Grid pane**, and **SQL pane** are synchronized, so that changes in one pane are reflected in the other two panes.</span></span>  
  
 <span data-ttu-id="8e184-191">**结果窗格**</span><span class="sxs-lookup"><span data-stu-id="8e184-191">**Result pane**</span></span>  
 <span data-ttu-id="8e184-192">单击“工具栏”窗格中的“运行”时会显示查询结果。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="8e184-192">Displays the results of the query when you click **Run** on the **Toolbar** pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e184-193">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8e184-193">See Also</span></span>  
 <span data-ttu-id="8e184-194">[&#40;多维数据的 Analysis Services 设计器和对话框&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="8e184-194">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="8e184-195">在数据源视图中定义命名查询 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="8e184-195">Define Named Queries in a Data Source View &#40;Analysis Services&#41;</span></span>](multidimensional-models/define-named-queries-in-a-data-source-view-analysis-services.md)  
  
  
