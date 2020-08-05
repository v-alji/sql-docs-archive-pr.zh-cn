---
title: "\"创建轮询查询\" 对话框 (Analysis Services 多维数据) |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.createpollingquerydialog.f1
ms.assetid: 0f2902b5-796a-4eb0-be03-01514dc01b9a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 186f5d8c1838ed8edaba446e954e39f513bc6fca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581058"
---
# <a name="create-polling-query-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="db77d-102">“创建轮询查询”对话框（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="db77d-102">Create Polling Query Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="db77d-103">可以使用 **中的** “创建轮询查询” [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 对话框，在 **“存储选项”** 对话框的 **“通知”** 选项卡中创建轮询查询。</span><span class="sxs-lookup"><span data-stu-id="db77d-103">Use the **Create Polling Query** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to create a polling query in the **Notifications** tab of the **Storage Options** dialog box.</span></span> <span data-ttu-id="db77d-104">轮询查询通常是返回某个值的单独查询， [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 可以使用该返回值确定是否已对表或其他关系对象进行了更改。</span><span class="sxs-lookup"><span data-stu-id="db77d-104">A polling query is typically a singleton query that returns a value [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] can use to determine if changes have been made to a table or other relational object.</span></span> <span data-ttu-id="db77d-105">在“存储选项”对话框的“通知”选项卡上的“按计划轮询”选项中，单击该网格的“轮询查询”列上的省略号按钮 (**...**)，可以显示“创建轮询查询”对话框。\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="db77d-105">You can display the **Create Polling Query** dialog box by clicking the ellipsis button (**...**) on the **Polling Query** column of the grid for the **Scheduled polling** option on the **Notifications** tab of the **Storage Options** dialog box.</span></span> <span data-ttu-id="db77d-106">有关“存储选项”\*\*\*\* 对话框的“通知”\*\*\*\* 选项卡的详细信息，请参阅[通知（“存储选项”对话框）（Analysis Services - 多维数据）](notifications-storage-options-dialog-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="db77d-106">For more information about the **Notifications** tab of the **Storage Options** dialog box, see [Notifications &#40;Storage Options Dialog Box&#41; &#40;Analysis Services - Multidimensional Data&#41;](notifications-storage-options-dialog-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="db77d-107">轮询查询应返回的值的类型取决于为特定对象（基于正在查询的表）的多维 OLAP (MOLAP) 缓存所计划的更新类型：</span><span class="sxs-lookup"><span data-stu-id="db77d-107">The type of value that should be returned by the polling query depends on the type of updates planned for the multidimensional OLAP (MOLAP) cache of the object based on the table being queried:</span></span>  
  
-   <span data-ttu-id="db77d-108">如果在 **“存储选项”** 对话框的 **“通知”** 选项卡上未选中 **“启用增量更新”** ，则在按计划轮询期间检测到更改时 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 将完全更新对象的 MOLAP 缓存。</span><span class="sxs-lookup"><span data-stu-id="db77d-108">If **Enable incremental update** is not selected on the **Notifications** tab of the **Storage Options** dialog box, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] fully updates the MOLAP cache for the object if a change is detected during scheduled polling.</span></span> <span data-ttu-id="db77d-109">所使用的轮询查询应确定自上次轮询期以来是否已将记录添加到表中。</span><span class="sxs-lookup"><span data-stu-id="db77d-109">The polling query used should determine if records have been added to the table since the last polling period.</span></span>  
  
-   <span data-ttu-id="db77d-110">如果在 **“存储选项”** 对话框的 **“通知”** 选项卡上选中了 **“启用增量更新”** ，则在按计划轮询期间检测到更改时 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 将增量更新对象的 MOLAP 缓存。</span><span class="sxs-lookup"><span data-stu-id="db77d-110">If **Enable incremental update** is selected on the **Notifications** tab of the **Storage Options** dialog box, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] incrementally updates the MOLAP cache for the object if a change is detected during scheduled polling.</span></span> <span data-ttu-id="db77d-111">所使用的轮询查询应确定表中的最后一条记录。</span><span class="sxs-lookup"><span data-stu-id="db77d-111">The polling query used should determine the last record in the table.</span></span>  
  
 <span data-ttu-id="db77d-112">例如，可以使用以下轮询查询为 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] 示例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库中的客户维度提供完全更新或增量更新：</span><span class="sxs-lookup"><span data-stu-id="db77d-112">For example, you can use the following polling queries to supply either full or incremental updates for the Customer dimension in the [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] sample [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database:</span></span>  
  
|<span data-ttu-id="db77d-113">更新类型</span><span class="sxs-lookup"><span data-stu-id="db77d-113">Update type</span></span>|<span data-ttu-id="db77d-114">轮询查询</span><span class="sxs-lookup"><span data-stu-id="db77d-114">Polling query</span></span>|  
|-----------------|-------------------|  
|<span data-ttu-id="db77d-115">完全更新</span><span class="sxs-lookup"><span data-stu-id="db77d-115">Full update</span></span>|`SELECT`<br /><br /> `COUNT(*) AS TotalCount`<br /><br /> `FROM`<br /><br /> `[dbo].[DimCustomer]`|  
|<span data-ttu-id="db77d-116">增量更新</span><span class="sxs-lookup"><span data-stu-id="db77d-116">Incremental update</span></span>|`SELECT`<br /><br /> `MAX([CustomerKey]) AS LastCustomerKey`<br /><br /> `FROM`<br /><br /> `[dbo].[DimCustomer]`|  
  
 <span data-ttu-id="db77d-117">有关按计划轮询通知的完全更新和增量更新的详细信息，请参阅[主动缓存（分区）](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md)。</span><span class="sxs-lookup"><span data-stu-id="db77d-117">For more information about full and incremental updates for scheduled polling notifications, see [Proactive Caching &#40;Partitions&#41;](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md).</span></span>  
  
 <span data-ttu-id="db77d-118">输入的查询必须是基本访问接口的有效查询命令。</span><span class="sxs-lookup"><span data-stu-id="db77d-118">The query entered must be a valid query command for the underlying provider.</span></span> <span data-ttu-id="db77d-119">查询将通过基本访问接口进行处理，以便进行验证，并用于标识返回的列。</span><span class="sxs-lookup"><span data-stu-id="db77d-119">The query is prepared with the underlying provider for validation, and to identify the columns returned.</span></span> <span data-ttu-id="db77d-120">该对话框可以显示两个视图：</span><span class="sxs-lookup"><span data-stu-id="db77d-120">The dialog box can present two views:</span></span>  
  
-   <span data-ttu-id="db77d-121">Visual Database Tools (VDT) 查询生成器</span><span class="sxs-lookup"><span data-stu-id="db77d-121">Visual Database Tools (VDT) Query Builder</span></span>  
  
     <span data-ttu-id="db77d-122">对于所有用户，VDT 查询生成器视图提供了一组用户界面工具，用于以可视方式构造和测试 SQL 查询。</span><span class="sxs-lookup"><span data-stu-id="db77d-122">For all users, the VDT Query Builder view provides a set of user interface tools for visually constructing and testing a SQL query.</span></span>  
  
-   <span data-ttu-id="db77d-123">一般查询生成器</span><span class="sxs-lookup"><span data-stu-id="db77d-123">Generic Query Builder</span></span>  
  
     <span data-ttu-id="db77d-124">对于高级用户，一般查询生成器视图提供了一个更为简单直接的用户界面，用于构造和测试 SQL 查询。</span><span class="sxs-lookup"><span data-stu-id="db77d-124">For advanced users, the Generic Query Builder view provides a simpler, more direct user interface for constructing and testing a SQL query.</span></span>  
  
## <a name="options"></a><span data-ttu-id="db77d-125">选项</span><span class="sxs-lookup"><span data-stu-id="db77d-125">Options</span></span>  
 <span data-ttu-id="db77d-126">**数据源**</span><span class="sxs-lookup"><span data-stu-id="db77d-126">**Data Source**</span></span>  
 <span data-ttu-id="db77d-127">为查询指定数据源。</span><span class="sxs-lookup"><span data-stu-id="db77d-127">Specifies the data source for the query.</span></span>  
  
 <span data-ttu-id="db77d-128">**查询定义**</span><span class="sxs-lookup"><span data-stu-id="db77d-128">**Query definition**</span></span>  
 <span data-ttu-id="db77d-129">查询定义根据选定的视图提供用于定义和测试查询的一个工具栏和多个窗格。</span><span class="sxs-lookup"><span data-stu-id="db77d-129">The query definition provides a toolbar and panes in which to define and test the query, depending on the selected view.</span></span>  
  
 <span data-ttu-id="db77d-130">**工具栏**</span><span class="sxs-lookup"><span data-stu-id="db77d-130">**Toolbar**</span></span>  
 <span data-ttu-id="db77d-131">使用工具栏可以管理数据集、选择要显示的窗格以及控制各种查询函数。</span><span class="sxs-lookup"><span data-stu-id="db77d-131">Use the toolbar to manage datasets, select panes to display, and control various query functions.</span></span>  
  
|<span data-ttu-id="db77d-132">值</span><span class="sxs-lookup"><span data-stu-id="db77d-132">Value</span></span>|<span data-ttu-id="db77d-133">说明</span><span class="sxs-lookup"><span data-stu-id="db77d-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="db77d-134">**切换到一般查询生成器**</span><span class="sxs-lookup"><span data-stu-id="db77d-134">**Switch to Generic Query Builder**</span></span>|<span data-ttu-id="db77d-135">选择此选项将只显示可用于一般查询生成器视图的选项。</span><span class="sxs-lookup"><span data-stu-id="db77d-135">Select to display only the options available to the Generic Query Builder view.</span></span> <span data-ttu-id="db77d-136">仅显示下列选项：</span><span class="sxs-lookup"><span data-stu-id="db77d-136">Only the following options are displayed:</span></span><br /><br /> <span data-ttu-id="db77d-137">**SQL 窗格**</span><span class="sxs-lookup"><span data-stu-id="db77d-137">**SQL pane**</span></span><br /><br /> <span data-ttu-id="db77d-138">**结果窗格**</span><span class="sxs-lookup"><span data-stu-id="db77d-138">**Result pane**</span></span><br /><br /> <span data-ttu-id="db77d-139">**“工具栏”**，只包含 **“切换到 VDT 查询生成器”** 和 **“运行”**</span><span class="sxs-lookup"><span data-stu-id="db77d-139">**Toolbar**, containing only **Switch to VDT Query Builder** and **Run**</span></span><br /><br /> <br /><br /> <span data-ttu-id="db77d-140">注意：只有在选择了“切换到 VDT 查询生成器”时，才会显示此选项。 \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="db77d-140">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="db77d-141">**“切换到 VDT 查询生成器”**</span><span class="sxs-lookup"><span data-stu-id="db77d-141">**Switch to VDT Query Builder**</span></span>|<span data-ttu-id="db77d-142">选择此选项将显示可用于 Visual Database Tools (VDT) 查询生成器视图的所有选项。</span><span class="sxs-lookup"><span data-stu-id="db77d-142">Select to display all of the options available to the Visual Database Tools (VDT) Query Builder view.</span></span><br /><br /> <span data-ttu-id="db77d-143">注意：只有选定了“切换到一般查询生成器” \*\*\*\* ，才会显示此选项。</span><span class="sxs-lookup"><span data-stu-id="db77d-143">Note: This option is displayed only if **Switch to Generic Query Builder** is selected.</span></span>|  
|<span data-ttu-id="db77d-144">**显示/隐藏关系图窗格**</span><span class="sxs-lookup"><span data-stu-id="db77d-144">**Show/Hide Diagram Pane**</span></span>|<span data-ttu-id="db77d-145">显示或隐藏 **关系图窗格**。</span><span class="sxs-lookup"><span data-stu-id="db77d-145">Shows or hides the **Diagram pane**.</span></span><br /><br /> <span data-ttu-id="db77d-146">注意：只有在选择了“切换到 VDT 查询生成器”时，才会显示此选项。 \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="db77d-146">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="db77d-147">**显示/隐藏网格窗格**</span><span class="sxs-lookup"><span data-stu-id="db77d-147">**Show/Hide Grid Pane**</span></span>|<span data-ttu-id="db77d-148">显示或隐藏 **网格窗格**。</span><span class="sxs-lookup"><span data-stu-id="db77d-148">Shows or hides the **Grid pane**.</span></span><br /><br /> <span data-ttu-id="db77d-149">注意：只有在选择了“切换到 VDT 查询生成器”时，才会显示此选项。 \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="db77d-149">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="db77d-150">**显示/隐藏 SQL 窗格**</span><span class="sxs-lookup"><span data-stu-id="db77d-150">**Show/Hide SQL Pane**</span></span>|<span data-ttu-id="db77d-151">显示或隐藏 **SQL 窗格**。</span><span class="sxs-lookup"><span data-stu-id="db77d-151">Shows or hides the **SQL pane**.</span></span><br /><br /> <span data-ttu-id="db77d-152">注意：只有在选择了“切换到 VDT 查询生成器”时，才会显示此选项。 \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="db77d-152">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="db77d-153">**显示/隐藏结果窗格**</span><span class="sxs-lookup"><span data-stu-id="db77d-153">**Show/Hide Result Pane**</span></span>|<span data-ttu-id="db77d-154">显示或隐藏 **结果窗格**。</span><span class="sxs-lookup"><span data-stu-id="db77d-154">Shows or hides the **Result pane**.</span></span><br /><br /> <span data-ttu-id="db77d-155">注意：只有在选择了“切换到 VDT 查询生成器”时，才会显示此选项。 \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="db77d-155">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="db77d-156">**Run**</span><span class="sxs-lookup"><span data-stu-id="db77d-156">**Run**</span></span>|<span data-ttu-id="db77d-157">运行查询。</span><span class="sxs-lookup"><span data-stu-id="db77d-157">Runs the query.</span></span> <span data-ttu-id="db77d-158">结果将显示在 "**结果" 窗格**中。</span><span class="sxs-lookup"><span data-stu-id="db77d-158">Results are displayed in the **Result pane**.</span></span>|  
|<span data-ttu-id="db77d-159">**验证 SQL**</span><span class="sxs-lookup"><span data-stu-id="db77d-159">**Verify SQL**</span></span>|<span data-ttu-id="db77d-160">验证查询中的 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="db77d-160">Verifies the SQL statement in the query.</span></span><br /><br /> <span data-ttu-id="db77d-161">注意：只有在选择了“切换到 VDT 查询生成器”时，才会显示此选项。 \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="db77d-161">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="db77d-162">**升序排序**</span><span class="sxs-lookup"><span data-stu-id="db77d-162">**Sort Ascending**</span></span>|<span data-ttu-id="db77d-163">依据 **网格窗格**中的所选列对输出行按升序排序。</span><span class="sxs-lookup"><span data-stu-id="db77d-163">Sorts output rows on the selected column in the **Grid pane**, in ascending order.</span></span><br /><br /> <span data-ttu-id="db77d-164">注意：只有在选择了“切换到 VDT 查询生成器”时，才会显示此选项。 \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="db77d-164">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="db77d-165">**降序排序**</span><span class="sxs-lookup"><span data-stu-id="db77d-165">**Sort Descending**</span></span>|<span data-ttu-id="db77d-166">依据 **网格窗格**中的所选列对输出行按降序排序。</span><span class="sxs-lookup"><span data-stu-id="db77d-166">Sorts output rows on the selected column in the **Grid pane**, in descending order.</span></span><br /><br /> <span data-ttu-id="db77d-167">注意：只有在选择了“切换到 VDT 查询生成器”时，才会显示此选项。 \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="db77d-167">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="db77d-168">**删除筛选器**</span><span class="sxs-lookup"><span data-stu-id="db77d-168">**Remove Filter**</span></span>|<span data-ttu-id="db77d-169">删除 **网格窗格**中所选行的排序条件（如果适用的话）。</span><span class="sxs-lookup"><span data-stu-id="db77d-169">Removes sort criteria, if applicable, for the selected row in the **Grid pane**.</span></span><br /><br /> <span data-ttu-id="db77d-170">注意：只有在选择了“切换到 VDT 查询生成器”时，才会显示此选项。 \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="db77d-170">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="db77d-171">**使用 Group By**</span><span class="sxs-lookup"><span data-stu-id="db77d-171">**Use Group By**</span></span>|<span data-ttu-id="db77d-172">向查询中添加分组功能。</span><span class="sxs-lookup"><span data-stu-id="db77d-172">Adds grouping functionality to the query.</span></span><br /><br /> <span data-ttu-id="db77d-173">注意：只有在选择了“切换到 VDT 查询生成器”时，才会显示此选项。 \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="db77d-173">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
|<span data-ttu-id="db77d-174">**添加表**</span><span class="sxs-lookup"><span data-stu-id="db77d-174">**Add Table**</span></span>|<span data-ttu-id="db77d-175">显示 **“添加表”** 对话框，以便向查询中添加新表或新视图。</span><span class="sxs-lookup"><span data-stu-id="db77d-175">Displays the **Add Table** dialog box to add a new table or view to the query.</span></span> <span data-ttu-id="db77d-176">有关“添加表”\*\*\*\* 对话框的详细信息，请参阅[“添加表”对话框（Analysis Services - 多维数据）](add-table-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="db77d-176">For more information about the **Add Table** dialog box, see [Add Table Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](add-table-dialog-box-analysis-services-multidimensional-data.md).</span></span><br /><br /> <span data-ttu-id="db77d-177">注意：只有在选择了“切换到 VDT 查询生成器”时，才会显示此选项。 \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="db77d-177">Note: This option is displayed only if **Switch to VDT Query Builder** is selected.</span></span>|  
  
 <span data-ttu-id="db77d-178">**关系图窗格**</span><span class="sxs-lookup"><span data-stu-id="db77d-178">**Diagram pane**</span></span>  
 <span data-ttu-id="db77d-179">以关系图的形式显示查询所引用的对象。</span><span class="sxs-lookup"><span data-stu-id="db77d-179">Displays the objects referenced by the query as a diagram.</span></span> <span data-ttu-id="db77d-180">关系图可显示查询中包含的表以及这些表的联接方式。</span><span class="sxs-lookup"><span data-stu-id="db77d-180">The diagram shows the tables included in the query, and how they are joined.</span></span> <span data-ttu-id="db77d-181">选中或清除表中某列旁边的复选框，即可在查询输出中添加或删除该列。</span><span class="sxs-lookup"><span data-stu-id="db77d-181">Select or clear the check box next to a column in a table to add or remove it from the query output.</span></span>  
  
 <span data-ttu-id="db77d-182">向查询中添加表时，该对话框将根据表中的键创建表之间的联接。</span><span class="sxs-lookup"><span data-stu-id="db77d-182">When you add tables to the query, the dialog box creates joins between tables based on the keys in the table.</span></span> <span data-ttu-id="db77d-183">若要添加联接，请将一个表中的字段拖到另一个表中的字段上。</span><span class="sxs-lookup"><span data-stu-id="db77d-183">To add a join, drag a field from one table onto a field in another table.</span></span> <span data-ttu-id="db77d-184">若要管理某个联接，请右键单击该联接。</span><span class="sxs-lookup"><span data-stu-id="db77d-184">To manage a join, right-click the join.</span></span>  
  
 <span data-ttu-id="db77d-185">右键单击“关系图窗格”，可以添加或删除表，选择所有表，以及显示或隐藏窗格。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="db77d-185">Right-click the **Diagram pane** to add or remove tables, select all the tables, and show or hide panes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="db77d-186">**关系图窗格**、 **网格窗格**和 **SQL 窗格** 中的内容是同步的，这样其中一个窗格的更改可以反映在其他两个窗格中。</span><span class="sxs-lookup"><span data-stu-id="db77d-186">The contents of the **Diagram pane**, **Grid pane**, and **SQL pane** are synchronized, so that changes in one pane are reflected in the other two panes.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="db77d-187">该对话框不支持更改查询类型。</span><span class="sxs-lookup"><span data-stu-id="db77d-187">Changing query types is not supported by the dialog box.</span></span>  
  
 <span data-ttu-id="db77d-188">**“网格”窗格**</span><span class="sxs-lookup"><span data-stu-id="db77d-188">**Grid pane**</span></span>  
 <span data-ttu-id="db77d-189">在网格中显示查询所引用的对象。</span><span class="sxs-lookup"><span data-stu-id="db77d-189">Displays the objects referenced by the query in a grid.</span></span> <span data-ttu-id="db77d-190">使用此窗格可以在查询中添加和删除列，以及更改每一列的设置。</span><span class="sxs-lookup"><span data-stu-id="db77d-190">You can use this pane to add and remove columns to the query and change the settings for each column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="db77d-191">**关系图窗格**、 **网格窗格**和 **SQL 窗格** 中的内容是同步的，这样其中一个窗格的更改可以反映在其他两个窗格中。</span><span class="sxs-lookup"><span data-stu-id="db77d-191">The contents of the **Diagram pane**, **Grid pane**, and **SQL pane** are synchronized, so that changes in one pane are reflected in the other two panes.</span></span>  
  
 <span data-ttu-id="db77d-192">**SQL 窗格**</span><span class="sxs-lookup"><span data-stu-id="db77d-192">**SQL pane**</span></span>  
 <span data-ttu-id="db77d-193">将查询显示为 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="db77d-193">Displays the query as a SQL statement.</span></span> <span data-ttu-id="db77d-194">键入内容即可更改查询的 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="db77d-194">Type to change the SQL statement for the query.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="db77d-195">**关系图窗格**、 **网格窗格**和 **SQL 窗格** 中的内容是同步的，这样其中一个窗格的更改可以反映在其他两个窗格中。</span><span class="sxs-lookup"><span data-stu-id="db77d-195">The contents of the **Diagram pane**, **Grid pane**, and **SQL pane** are synchronized, so that changes in one pane are reflected in the other two panes.</span></span>  
  
 <span data-ttu-id="db77d-196">**结果窗格**</span><span class="sxs-lookup"><span data-stu-id="db77d-196">**Result pane**</span></span>  
 <span data-ttu-id="db77d-197">单击“工具栏”窗格中的“运行”时会显示查询结果。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="db77d-197">Displays the results of the query when you click **Run** on the **Toolbar** pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db77d-198">另请参阅</span><span class="sxs-lookup"><span data-stu-id="db77d-198">See Also</span></span>  
 [<span data-ttu-id="db77d-199">&#40;多维数据的 Analysis Services 设计器和对话框&#41;</span><span class="sxs-lookup"><span data-stu-id="db77d-199">Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;</span></span>](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  