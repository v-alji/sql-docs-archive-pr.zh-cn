---
title: Visual Database Tool 设计器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- data sources [SQL Server]
- View Designer
- Visual Database Tools [SQL Server]
- Database Diagram Designer
- Query Designer [SQL Server]
- design tools [Visual Database Tools]
- Table Designer
- Visual Database Tools [SQL Server], designers
- Properties window [Visual Database Tools]
ms.assetid: bd0ca68e-6f69-42dd-bcb5-ce511673769c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6a307a0a82aa02e7197189ca6cfc9ba70a3fea33
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578617"
---
# <a name="visual-database-tool-designers"></a><span data-ttu-id="e79e1-102">Visual Database Tool 设计器</span><span class="sxs-lookup"><span data-stu-id="e79e1-102">Visual Database Tool Designers</span></span>
  <span data-ttu-id="e79e1-103">Visual Database Tools 包含可用来处理数据源的多种设计工具。</span><span class="sxs-lookup"><span data-stu-id="e79e1-103">The Visual Database Tools are a combination of design tools you can use to work with a data source.</span></span> <span data-ttu-id="e79e1-104">您可以使用这些工具创建查询，设计或修改数据库结构，或者更新数据。</span><span class="sxs-lookup"><span data-stu-id="e79e1-104">You can use them to create queries, design or modify a database structure, or update data.</span></span> <span data-ttu-id="e79e1-105">这些工具包括数据库关系图设计器、表设计器以及查询和视图设计器。</span><span class="sxs-lookup"><span data-stu-id="e79e1-105">The tools are Database Diagram Designer, Table Designer, and Query and View Designer.</span></span>  
  
## <a name="properties-window"></a><span data-ttu-id="e79e1-106">“属性”窗口</span><span class="sxs-lookup"><span data-stu-id="e79e1-106">Properties Window</span></span>  
 <span data-ttu-id="e79e1-107">属性窗口并不是 Visual Database Tools 所特有的，但是在其属性窗口中可以进行许多修改。</span><span class="sxs-lookup"><span data-stu-id="e79e1-107">The properties window is not specific to Visual Database Tools, but it is where many modifications can be made.</span></span> <span data-ttu-id="e79e1-108">该窗口显示当前所选项（如表）的属性，并允许您编辑这些属性（从属性名称到列排序规则的所有属性）。</span><span class="sxs-lookup"><span data-stu-id="e79e1-108">It shows the properties for the item currently selected (like a table) and allows you to edit those properties (everything from the properties name to the collation of a column).</span></span> <span data-ttu-id="e79e1-109">某些属性可以在属性窗口中查看，但必须使用其他工具进行修改。</span><span class="sxs-lookup"><span data-stu-id="e79e1-109">Some properties can be seen in the properties window but must be modified in a different tool.</span></span>  
  
## <a name="database-diagram-designer"></a><span data-ttu-id="e79e1-110">数据库关系图设计器</span><span class="sxs-lookup"><span data-stu-id="e79e1-110">Database Diagram Designer</span></span>  
 <span data-ttu-id="e79e1-111">数据库关系图设计器提供了一个窗口，您可以在其中直观地创建、编辑和显示数据库中的表及关系。</span><span class="sxs-lookup"><span data-stu-id="e79e1-111">Database Diagram Designer provides a window where you can visually create, edit, and show the tables and relationships in a database.</span></span>  
  
 <span data-ttu-id="e79e1-112">若要显示数据库关系图设计器，请打开现有关系图，或右键单击对象资源管理器中的“数据库”节点并从下拉菜单上选择“新建数据库关系图”  。</span><span class="sxs-lookup"><span data-stu-id="e79e1-112">To display Database Diagram Designer, open an existing diagram or right-click the Database node in Object Explorer and choose **New Database Diagram** from the drop-down menu.</span></span>  
  
 <span data-ttu-id="e79e1-113">设计器打开后，就会在主菜单上显示“数据库关系图”  菜单。</span><span class="sxs-lookup"><span data-stu-id="e79e1-113">Once the designer is open, the **Database Diagram** menu appears in the main menu.</span></span> <span data-ttu-id="e79e1-114">可通过此菜单访问设计器的特殊功能。</span><span class="sxs-lookup"><span data-stu-id="e79e1-114">This menu is the access point to the designer's special features.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e79e1-115">此设计器可与 Microsoft SQL Server 数据库配合使用。</span><span class="sxs-lookup"><span data-stu-id="e79e1-115">This designer works with Microsoft SQL Server databases.</span></span>  
>   
>  <span data-ttu-id="e79e1-116">此版本的 Visual Database Tools 不支持 Microsoft SQL Server version 7 及更早版本。</span><span class="sxs-lookup"><span data-stu-id="e79e1-116">This version of Visual Database Tools does not support Microsoft SQL Server version 7 and earlier.</span></span>  
  
## <a name="table-designer"></a><span data-ttu-id="e79e1-117">表设计器</span><span class="sxs-lookup"><span data-stu-id="e79e1-117">Table Designer</span></span>  
 <span data-ttu-id="e79e1-118">表设计器是一种可视化工具，在其中可对所连接的 Microsoft SQL Server 数据库中的单个表进行设计和可视化处理。</span><span class="sxs-lookup"><span data-stu-id="e79e1-118">Table Designer is a visual tool allowing you to design and visualize a single table in a Microsoft SQL Server database to which you are connected.</span></span>  
  
 <span data-ttu-id="e79e1-119">表设计器有两个窗格。</span><span class="sxs-lookup"><span data-stu-id="e79e1-119">Table Designer has two panes.</span></span> <span data-ttu-id="e79e1-120">上部区域显示一个网格；网格的每一行描述一个数据库列。</span><span class="sxs-lookup"><span data-stu-id="e79e1-120">The upper area shows a grid; each row of the grid describes one database column.</span></span> <span data-ttu-id="e79e1-121">对于每个数据库列，该网格都会显示其基本属性：列名、数据类型和“允许空”设置。</span><span class="sxs-lookup"><span data-stu-id="e79e1-121">For each database column, the grid displays its fundamental attributes: column name, data type, and nulls-allowed setting.</span></span>  
  
 <span data-ttu-id="e79e1-122">表设计器的下部区域是“列属性”选项卡，它显示在上部区域中突出显示的任何列的其他属性。</span><span class="sxs-lookup"><span data-stu-id="e79e1-122">The lower area of Table Designer, the Column Properties tab, shows additional attributes for whichever column is highlighted in the upper area.</span></span>  
  
 <span data-ttu-id="e79e1-123">在表设计器中，还可以通过在网格区域中右键单击来访问对话框，通过这些对话框可以创建和修改表的关系、约束、索引以及键。</span><span class="sxs-lookup"><span data-stu-id="e79e1-123">From Table Designer, you can also right-click in the grid section to access dialog boxes through which you can create and modify relationships, constraints, indexes, and keys for the table.</span></span>  
  
 <span data-ttu-id="e79e1-124">若要显示表设计器，请打开一个现有表，或在对象资源管理器中右键单击“表”  节点，再从下拉菜单中选择“添加新表”  。</span><span class="sxs-lookup"><span data-stu-id="e79e1-124">To display Table Designer, open an existing table, or right-click the **Tables** node in Object Explorer, and choose **Add New Table** from the drop-down menu.</span></span>  
  
 <span data-ttu-id="e79e1-125">设计器一旦打开，就会在主菜单上显示“表设计器”菜单。</span><span class="sxs-lookup"><span data-stu-id="e79e1-125">Once the designer is open, the Table Designer menu appears in the main menu.</span></span> <span data-ttu-id="e79e1-126">可通过此菜单访问设计器的特殊功能。</span><span class="sxs-lookup"><span data-stu-id="e79e1-126">This menu is the access point to the designer's special features.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e79e1-127">此设计器可与 Microsoft SQL Server 数据库配合使用。</span><span class="sxs-lookup"><span data-stu-id="e79e1-127">This designer works with Microsoft SQL Server databases.</span></span>  
>   
>  <span data-ttu-id="e79e1-128">此版本的 Visual Database Tools 不支持 Microsoft SQL Server version 7 及更早版本。</span><span class="sxs-lookup"><span data-stu-id="e79e1-128">This version of Visual Database Tools does not support Microsoft SQL Server version 7 and earlier.</span></span>  
  
## <a name="query-and-view-designer"></a><span data-ttu-id="e79e1-129">查询和视图设计器</span><span class="sxs-lookup"><span data-stu-id="e79e1-129">Query and View Designer</span></span>  
 <span data-ttu-id="e79e1-130">查询和视图设计器实际上是两个工作方式极其类似的工具。</span><span class="sxs-lookup"><span data-stu-id="e79e1-130">Query and View designer is actually two tools that work in very similar ways.</span></span> <span data-ttu-id="e79e1-131">它们的主要区别包括：</span><span class="sxs-lookup"><span data-stu-id="e79e1-131">Some of the major differences are:</span></span>  
  
-   <span data-ttu-id="e79e1-132">视图随数据库保存，而查询则随 Visual Studio 数据库对象保存。</span><span class="sxs-lookup"><span data-stu-id="e79e1-132">Views are saved with the database while a query is saved with a Visual Studio database project.</span></span>  
  
-   <span data-ttu-id="e79e1-133">查询设计器几乎可以处理任何数据源，而视图设计器只能与 SQL Server 一起使用。</span><span class="sxs-lookup"><span data-stu-id="e79e1-133">Query Designer works with nearly any data source, where View Designer works only with SQL Server.</span></span>  
  
-   <span data-ttu-id="e79e1-134">查询设计器允许设计 SELECT、INSERT、UPDATE 和 DELETE DML 语句，而视图只能包含 SELECT 语句。</span><span class="sxs-lookup"><span data-stu-id="e79e1-134">Query Designer allows you to design SELECT, INSERT, UPDATE and DELETE DML statements, while views can only contain SELECT statements.</span></span>  
  
### <a name="view-designer"></a><span data-ttu-id="e79e1-135">视图设计器</span><span class="sxs-lookup"><span data-stu-id="e79e1-135">View Designer</span></span>  
 <span data-ttu-id="e79e1-136">使用视图设计器可以对现有视图进行设计和可视化处理，或者在所连接的 Microsoft SQL Server 数据库中创建新的视图。</span><span class="sxs-lookup"><span data-stu-id="e79e1-136">View Designer allows you to design and visualize an existing view or create a new one in a Microsoft SQL Server database to which you are connected.</span></span>  
  
 <span data-ttu-id="e79e1-137">视图设计器包含四个窗格：“关系图”窗格、“条件”窗格、“SQL”窗格和“结果”窗格。</span><span class="sxs-lookup"><span data-stu-id="e79e1-137">View Designer has four panes: the Diagram pane, the Criteria pane, the SQL pane, and the Results pane.</span></span> <span data-ttu-id="e79e1-138">有关上述各个窗格的详细信息，请参阅[查询和视图设计器工具 (Visual Database Tools)](visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="e79e1-138">For more detailed information on each of these panes, see [Query and View Designer Tools &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="e79e1-139">若要显示视图设计器，请打开一个现有视图，或在对象资源管理器中右键单击“视图”  节点，再从下拉菜单中选择“添加新视图”  。</span><span class="sxs-lookup"><span data-stu-id="e79e1-139">To display View Designer, open an existing view or right-click the **View** node in Object Explorer and choose **Add New View** from the drop-down menu.</span></span>  
  
 <span data-ttu-id="e79e1-140">打开该设计器后，就会在主菜单上显示“查询设计器”  菜单。</span><span class="sxs-lookup"><span data-stu-id="e79e1-140">Once the designer is open, the **Query Designer** menu appears in the main menu.</span></span> <span data-ttu-id="e79e1-141">可通过此菜单访问设计器的特殊功能。</span><span class="sxs-lookup"><span data-stu-id="e79e1-141">This menu is the access point to the designer's special features.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e79e1-142">此设计器可与 Microsoft SQL Server 数据库配合使用。</span><span class="sxs-lookup"><span data-stu-id="e79e1-142">This designer works with Microsoft SQL Server databases.</span></span>  
>   
>  <span data-ttu-id="e79e1-143">此版本的 Visual Database Tools 不支持 Microsoft SQL Server version 7 及更早版本。</span><span class="sxs-lookup"><span data-stu-id="e79e1-143">This version of Visual Database Tools does not support Microsoft SQL Server version 7 and earlier.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e79e1-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e79e1-144">See Also</span></span>  
 <span data-ttu-id="e79e1-145">[&#40;Visual Database Tools 设计数据库关系图&#41;](design-database-diagrams-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="e79e1-145">[Design Database Diagrams &#40;Visual Database Tools&#41;](design-database-diagrams-visual-database-tools.md) </span></span>  
 <span data-ttu-id="e79e1-146">[&#40;Visual Database Tools 设计表&#41;](design-tables-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="e79e1-146">[Design Tables &#40;Visual Database Tools&#41;](design-tables-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="e79e1-147">设计查询和视图操作指南主题 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="e79e1-147">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
