---
title: 使用数据源视图设计器中的关系图 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dsvdesigner.diagramorganizerpane.f1
- sql12.asvs.dsvdesigner.findtable.f1
- sql12.asvs.dsvdesigner.diagrampane.f1
helpviewer_keywords:
- data source views [Analysis Services], diagrams
- diagrams [Analysis Services]
ms.assetid: 491fdd22-2326-4f27-a0dd-0a02faae3fd8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 40a58ed33ff6cfaebf2a6e7c084500dd3ae072da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587045"
---
# <a name="work-with-diagrams-in-data-source-view-designer-analysis-services"></a><span data-ttu-id="84180-102">使用数据源视图设计器中的关系图 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="84180-102">Work with Diagrams in Data Source View Designer (Analysis Services)</span></span>
  <span data-ttu-id="84180-103">数据源视图 (DSV) 关系图是 DSV 中对象的直观表示形式。</span><span class="sxs-lookup"><span data-stu-id="84180-103">A data source view (DSV) diagram is a visual representation of the objects in a DSV.</span></span> <span data-ttu-id="84180-104">您可以交互使用该关系图以添加、隐藏、删除或修改特定对象。</span><span class="sxs-lookup"><span data-stu-id="84180-104">You can work with the diagram interactively to add, hide, delete or modify specific objects.</span></span> <span data-ttu-id="84180-105">还可以对同一 DSV 创建多个关系图以特别关注对象的某个子集。</span><span class="sxs-lookup"><span data-stu-id="84180-105">You can also create multiple diagrams on the same DSV to focus attention on a subset of the objects.</span></span>  
  
 <span data-ttu-id="84180-106">若要更改关系图窗格中显示的关系图区域，请单击该窗格右下角的四向箭头，然后在关系图的缩略图上拖动选择框，直到选定要在关系图窗格中显示的区域为止。</span><span class="sxs-lookup"><span data-stu-id="84180-106">To change the area of the diagram that appears in the diagram pane, click the four-headed arrow in the lower right corner of the pane, and then drag the selection box over the thumbnail diagram until you select the area that is to appear in the diagram pane.</span></span>  
  
 <span data-ttu-id="84180-107">本主题包含下列部分：</span><span class="sxs-lookup"><span data-stu-id="84180-107">This topic includes the following sections:</span></span>  
  
 [<span data-ttu-id="84180-108">添加关系图</span><span class="sxs-lookup"><span data-stu-id="84180-108">Add a Diagram</span></span>](#bkmk_add)  
  
 [<span data-ttu-id="84180-109">编辑或删除关系图</span><span class="sxs-lookup"><span data-stu-id="84180-109">Edit or Delete a Diagram</span></span>](#bkmk_edit)  
  
 [<span data-ttu-id="84180-110">在关系图中查找表</span><span class="sxs-lookup"><span data-stu-id="84180-110">Find Tables in a Diagram</span></span>](#bkmk_findtables)  
  
 [<span data-ttu-id="84180-111">排列关系图中的对象</span><span class="sxs-lookup"><span data-stu-id="84180-111">Arrange Objects in a Diagram</span></span>](#bkmk_arrangeobjects)  
  
 [<span data-ttu-id="84180-112">保留对象排列</span><span class="sxs-lookup"><span data-stu-id="84180-112">Preserve object arrangement</span></span>](#bkmk_preserve)  
  
##  <a name="add-a-diagram"></a><a name="bkmk_add"></a> <span data-ttu-id="84180-113">添加关系图</span><span class="sxs-lookup"><span data-stu-id="84180-113">Add a Diagram</span></span>  
 <span data-ttu-id="84180-114">创建 DSV 时自动创建 DSV 关系图。</span><span class="sxs-lookup"><span data-stu-id="84180-114">DSV diagrams are created automatically when you create the DSV.</span></span> <span data-ttu-id="84180-115">在 DSV 存在后，您可以创建其他关系图、删除它们或隐藏特定对象以创建更便于管理的 DSV 表示形式。</span><span class="sxs-lookup"><span data-stu-id="84180-115">After the DSV exists, you can create additional diagrams, remove them, or hide specific objects to create a more manageable representation of the DSV.</span></span>  
  
 <span data-ttu-id="84180-116">若要创建新关系图，请右键单击“关系图组织程序”\*\*\*\* 窗格中的任意地方，再单击“新建关系图”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="84180-116">To create a new diagram, right-click anywhere in the **Diagram Organizer** pane, click **New Diagram**.</span></span>  
  
 <span data-ttu-id="84180-117">当您在 Analysis Services 项目中最初定义数据源视图 (DSV) 时，添加到数据源视图的所有表和视图都将添加到 \<All Tables> 关系图中。</span><span class="sxs-lookup"><span data-stu-id="84180-117">When you initially define a data source view (DSV) in an Analysis Services project, all tables and views added to the data source view are added to the \<All Tables> diagram.</span></span> <span data-ttu-id="84180-118">在数据源视图设计器的“关系图组织程序”窗格中将显示此关系图，在“表”窗格中将列出此关系图中的表及其列和关系，并在架构窗格中将以图形方式显示此关系图中的表及其列和关系。</span><span class="sxs-lookup"><span data-stu-id="84180-118">This diagram appears in the Diagram Organizer pane in Data Source View Designer, the tables in this diagram (and their columns and relationships) are listed in the Tables pane, and the tables in this diagram (and their columns and relationships) are displayed graphically in the schema pane.</span></span> <span data-ttu-id="84180-119">但是，当您向关系图中添加表、视图和命名查询时 \<All Tables> ，此关系图中的对象数量非常困难，尤其是将多个事实数据表添加到关系图中，维度表与多个事实数据表相关。</span><span class="sxs-lookup"><span data-stu-id="84180-119">However, as you add tables, views and named queries to the \<All Tables> diagram, the sheer number of objects in this diagram makes it difficult to visualize relationships-particularly as multiple fact tables are added to the diagram, and dimension tables relate to multiple fact tables.</span></span>  
  
 <span data-ttu-id="84180-120">当您只需要在数据源视图中查看表的子集时，若要减少视觉混乱，可以定义由数据源视图中所选表、视图和命名查询的子集组成的子关系图（简称为关系图）。</span><span class="sxs-lookup"><span data-stu-id="84180-120">To reduce the visual clutter when you only want to view a subset of the tables in the data source view, you can define sub-diagrams (simply called diagrams) consisting of selected subsets of the tables, views, and named queries in the data source view.</span></span> <span data-ttu-id="84180-121">根据业务或解决方案的需要，可以使用关系图对数据源视图中的项进行分组。</span><span class="sxs-lookup"><span data-stu-id="84180-121">You can use diagrams to group items in the data source view according to business or solution needs.</span></span>  
  
 <span data-ttu-id="84180-122">您可以将相关表和命名查询分组到单独的关系图中以便用于业务，这样可以使包含许多表、视图和命名查询的数据源视图更易于理解。</span><span class="sxs-lookup"><span data-stu-id="84180-122">You can group related tables and named queries in separate diagrams for business purposes, and to make it easier to understand a data source view that contains many tables, views, and named queries.</span></span> <span data-ttu-id="84180-123">同一个表或命名查询可以包含在多个关系图中， \<All Tables> 关系图除外。</span><span class="sxs-lookup"><span data-stu-id="84180-123">The same table or named query can be included in multiple diagrams except for the \<All Tables> diagram.</span></span> <span data-ttu-id="84180-124">在 \<All Tables> 关系图中，数据源视图中包含的所有对象都只显示一次。</span><span class="sxs-lookup"><span data-stu-id="84180-124">In the \<All Tables> diagram, all objects that are contained in the data source view are shown exactly once.</span></span>  
  
##  <a name="edit-or-delete-a-diagram"></a><a name="bkmk_edit"></a><span data-ttu-id="84180-125">编辑或删除关系图</span><span class="sxs-lookup"><span data-stu-id="84180-125">Edit or Delete a Diagram</span></span>  
 <span data-ttu-id="84180-126">使用关系图时，要特别注意用于添加和删除对象的命令。</span><span class="sxs-lookup"><span data-stu-id="84180-126">When working with a diagram, pay close attention to the commands used for adding and removing objects.</span></span> <span data-ttu-id="84180-127">例如，从关系图中删除对象时会将它从 DSV 中删除。</span><span class="sxs-lookup"><span data-stu-id="84180-127">For example, deleting an object from a diagram will delete it from the DSV.</span></span> <span data-ttu-id="84180-128">如果您只想将其从关系图中删除，请改用 **“隐藏表”** 。</span><span class="sxs-lookup"><span data-stu-id="84180-128">If you only want to delete it from the diagram, use **Hide Table** instead.</span></span>  
  
 <span data-ttu-id="84180-129">![“关系图”工作区的右键单击菜单的屏幕快照](../media/ssas-olapdsv-diagram.gif "“关系图”工作区的右键单击菜单的屏幕快照")</span><span class="sxs-lookup"><span data-stu-id="84180-129">![Screenshot of diagram workspace, right-click menu](../media/ssas-olapdsv-diagram.gif "Screenshot of diagram workspace, right-click menu")</span></span>  
  
 <span data-ttu-id="84180-130">尽管您可以逐个隐藏对象，但是使用“显示相关表”命令可将所有相关对象重新显示在关系图中。</span><span class="sxs-lookup"><span data-stu-id="84180-130">Although you can hide objects individually, bringing them back using the Show Related Tables command returns all related objects to the diagram.</span></span> <span data-ttu-id="84180-131">若要控制将哪些对象返回到工作区，请从“表”窗格中拖动它们。</span><span class="sxs-lookup"><span data-stu-id="84180-131">To control which objects are returned to the workspace, drag them from the Tables pane instead.</span></span>  
  
##  <a name="find-tables-in-a-diagram"></a><a name="bkmk_findtables"></a><span data-ttu-id="84180-132">在关系图中查找表</span><span class="sxs-lookup"><span data-stu-id="84180-132">Find Tables in a Diagram</span></span>  
 <span data-ttu-id="84180-133">如果架构很大，则在 **“关系图”** 窗格中滚动到特定表可能很困难。</span><span class="sxs-lookup"><span data-stu-id="84180-133">If your schema is large, scrolling to a particular table in the **Diagram** pane may be difficult.</span></span> <span data-ttu-id="84180-134">但是，下列工具将使在关系图中查找表变得容易。</span><span class="sxs-lookup"><span data-stu-id="84180-134">However, the following tools make it easy to find a table in a diagram.</span></span>  
  
-   <span data-ttu-id="84180-135">在 **“表”** 窗格中滚动表列表。</span><span class="sxs-lookup"><span data-stu-id="84180-135">Scroll the list of tables in the **Tables** pane.</span></span>  
  
     <span data-ttu-id="84180-136">若要在当前显示的关系图中包括某个表，请将该表从 **“表”** 窗格拖到关系图窗格中。</span><span class="sxs-lookup"><span data-stu-id="84180-136">To include a table in the currently displayed diagram, drag the table from the **Tables** pane to the diagram pane.</span></span>  
  
     <span data-ttu-id="84180-137">若要将显示焦点置于已包含在关系图中的某个表上，请在 **“表”** 窗格中选择相应的表。</span><span class="sxs-lookup"><span data-stu-id="84180-137">To center the display on a table that is already included in the diagram, select the table in the **Tables** pane.</span></span>  
  
-   <span data-ttu-id="84180-138">**关系图**窗格中的表定位器—表定位器是一个4向箭头图标，位于 "**关系图**" 窗格右下角的垂直和水平滚动条的交点处。</span><span class="sxs-lookup"><span data-stu-id="84180-138">Table locator in **Diagram** pane-The table locator is a 4-way arrow icon located at the intersection of the vertical and horizontal scroll bars in the lower right corner of the **Diagram** pane.</span></span> <span data-ttu-id="84180-139">它可打开“关系图”窗格中当前关系图的缩略图表示。</span><span class="sxs-lookup"><span data-stu-id="84180-139">It opens a thumbnail representation of the current diagram in the Diagram pane.</span></span> <span data-ttu-id="84180-140">您可以使用此缩略图将“关系图”窗格中的视图更改到关系图的任何位置。</span><span class="sxs-lookup"><span data-stu-id="84180-140">You can use this thumbnail to change the view in the Diagram pane to any location on the diagram.</span></span>  
  
-   <span data-ttu-id="84180-141">使用 "**查找表**" 对话框-右键单击 "关系图" 窗格中的 "打开区域"，然后单击 "**查找表**"。</span><span class="sxs-lookup"><span data-stu-id="84180-141">Use the **Find Table** dialog box- Right-click on open area in the Diagram pane and click **Find Table**.</span></span> <span data-ttu-id="84180-142">或者，单击工具栏或 **“数据源视图”** 菜单上的 **“查找表”** 命令。</span><span class="sxs-lookup"><span data-stu-id="84180-142">Or, click the **Find Table** command on the toolbar or the **Data Source View** menu.</span></span>  
  
     <span data-ttu-id="84180-143">您可以在“筛选器”框中键入字符串和通配符以查看关系图中的表的子集。</span><span class="sxs-lookup"><span data-stu-id="84180-143">You can type strings and wildcard characters in the Filter box to view subsets of the tables in the diagram.</span></span>  
  
##  <a name="arrange-objects-in-a-diagram"></a><a name="bkmk_arrangeobjects"></a> <span data-ttu-id="84180-144">在关系图中排列对象</span><span class="sxs-lookup"><span data-stu-id="84180-144">Arrange Objects in a Diagram</span></span>  
 <span data-ttu-id="84180-145">虽然数据源视图设计器可以定义多个关系图，从而使得 DSV 更易于理解，但是，包含大量表的关系图可能难以读取，并且手动重新排列表的布局也是一个乏味的过程。</span><span class="sxs-lookup"><span data-stu-id="84180-145">Although Data Source View Designer can define multiple diagrams to make a DSV more understandable, diagrams that contain dozens of tables can be hard to read and manually rearranging table layouts is a tedious process.</span></span> <span data-ttu-id="84180-146">根据当前关系图中表与表之间的关系，数据源视图设计器可以使用矩形布局或对角线布局，自动重新排列当前关系图中的表。</span><span class="sxs-lookup"><span data-stu-id="84180-146">The Data Source View Designer can automatically rearrange tables in the current diagram using either a rectangular or diagonal layout based on the relationships between tables in the current diagram.</span></span>  
  
-   <span data-ttu-id="84180-147">在矩形布局中，将在表与表之间（而不是列与列之间）绘制关系线。</span><span class="sxs-lookup"><span data-stu-id="84180-147">In a rectangular layout, the relationship lines are drawn between tables instead of between columns.</span></span> <span data-ttu-id="84180-148">表与表之间绘制有水平和垂直的关系线。</span><span class="sxs-lookup"><span data-stu-id="84180-148">Relationship lines are drawn horizontally and vertically between tables.</span></span>  
  
-   <span data-ttu-id="84180-149">在对角线布局中，将在表中相关列之间尽可能直接地绘制关系线。</span><span class="sxs-lookup"><span data-stu-id="84180-149">In a diagonal layout, relationship lines are drawn as directly as possible between related columns in tables.</span></span> <span data-ttu-id="84180-150">多列之间的关系将附加到表中的第一个相关列。</span><span class="sxs-lookup"><span data-stu-id="84180-150">A relationship to multiple columns attaches to the first related column in the table.</span></span> <span data-ttu-id="84180-151">如果表中的列不可见，则会在表的顶部绘制关系线。</span><span class="sxs-lookup"><span data-stu-id="84180-151">If the columns in a table are not visible, the lines are drawn to the top of the table.</span></span>  
  
##  <a name="preserve-object-arrangement"></a><a name="bkmk_preserve"></a><span data-ttu-id="84180-152">保留对象排列</span><span class="sxs-lookup"><span data-stu-id="84180-152">Preserve object arrangement</span></span>  
 <span data-ttu-id="84180-153">在按所需方式手动排列表后，在关系图中添加更多表可能导致关系图刷新，从而删除最近对对象布局所做的所有修改。</span><span class="sxs-lookup"><span data-stu-id="84180-153">After manually arranging tables the way you want, adding more tables to the diagram can result in a diagram refresh that removes any recent modifications you made to the object layout.</span></span>  
  
 <span data-ttu-id="84180-154">在添加表（此操作会使关系图组织程序移动其他表以便容纳新表）时，更有可能出现此行为。</span><span class="sxs-lookup"><span data-stu-id="84180-154">This behavior is more likely to occur when you add a table, causing the Diagram Organizer to move other tables in order to accommodate the new one.</span></span> <span data-ttu-id="84180-155">它随后重新绘制关系图以确保正确表示所有表和连接线。</span><span class="sxs-lookup"><span data-stu-id="84180-155">It then redraws the diagram to ensure all tables and connection lines represented correctly.</span></span> <span data-ttu-id="84180-156">此时，对特定对象的位置进行的所有手动调整都可能丢失。</span><span class="sxs-lookup"><span data-stu-id="84180-156">At this point, any manual adjustments to the placement of specific objects might be lost.</span></span>  
  
 <span data-ttu-id="84180-157">为避免此问题，请首先添加所有表，然后再进行任何最终调整。</span><span class="sxs-lookup"><span data-stu-id="84180-157">To avoid this problem, add all the tables first, before making any final adjustments.</span></span> <span data-ttu-id="84180-158">以后重新打开关系图时，对象应该保留它们在关系图中的位置。</span><span class="sxs-lookup"><span data-stu-id="84180-158">Objects should now retain their position in the diagram when you open it again later.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84180-159">另请参阅</span><span class="sxs-lookup"><span data-stu-id="84180-159">See Also</span></span>  
 <span data-ttu-id="84180-160">[多维模型中的数据源视图](data-source-views-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="84180-160">[Data Source Views in Multidimensional Models](data-source-views-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="84180-161">数据源视图设计器（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="84180-161">Data Source View Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../data-source-view-designer-analysis-services-multidimensional-data.md)  
  
  
