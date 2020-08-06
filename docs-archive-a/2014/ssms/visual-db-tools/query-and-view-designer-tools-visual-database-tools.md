---
title: 查询和视图设计器工具 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.querydesigner
- vdt.pane.diagram
- vdt.pane.grid
- vdt.dlgbox.querybuilder
- vdt.pane.sql
- vdt.pane.results
helpviewer_keywords:
- Query Designer [SQL Server], panes
- View Designer, panes
- Query Designer [SQL Server], components
- View Designer, components
ms.assetid: 12e4b5a5-b793-4b6c-a0e5-c450c49bf26f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 29bd3fa9e171551197927aae0d1bc00446df6e7f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691489"
---
# <a name="query-and-view-designer-tools-visual-database-tools"></a><span data-ttu-id="5f898-102">查询和视图设计器工具 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="5f898-102">Query and View Designer Tools (Visual Database Tools)</span></span>
  <span data-ttu-id="5f898-103">在设计查询、视图、内嵌函数或单语句存储过程时，所使用的设计器由四个窗格组成：“关系图”窗格、“条件”窗格、SQL 窗格和“结果”窗格。</span><span class="sxs-lookup"><span data-stu-id="5f898-103">When you design a query, view, in-line function, or single-statement stored procedure, the designer you use consists of four panes: the Diagram pane, the Criteria pane, the SQL pane, and the Results pane.</span></span>  
  
 <span data-ttu-id="5f898-104">![查询设计器](../../database-engine/media//vs-queryviewdsgpanes.gif "查询设计器")</span><span class="sxs-lookup"><span data-stu-id="5f898-104">![Query Designer](../../database-engine/media//vs-queryviewdsgpanes.gif "Query Designer")</span></span>  
  
-   <span data-ttu-id="5f898-105">“关系图”窗格显示正在查询的表和其他表值对象。</span><span class="sxs-lookup"><span data-stu-id="5f898-105">The Diagram pane displays the tables and other table-valued objects that you are querying.</span></span> <span data-ttu-id="5f898-106">每个矩形代表一个表或表值对象，并显示可用的数据列。</span><span class="sxs-lookup"><span data-stu-id="5f898-106">Each rectangle represents a table or table-valued object and shows the available data columns.</span></span> <span data-ttu-id="5f898-107">联接用矩形之间的连线来表示。</span><span class="sxs-lookup"><span data-stu-id="5f898-107">Joins are indicated by lines between the rectangles.</span></span> <span data-ttu-id="5f898-108">有关详细信息，请参阅[“关系图”窗格 (Visual Database Tools)](visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="5f898-108">For more information, see [Diagram Pane &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
-   <span data-ttu-id="5f898-109">“条件”窗格包含一个类似于电子表格的网格，在该网格中可以指定相应的选项，例如要显示的数据列、要选择的行、行的分组方式等。</span><span class="sxs-lookup"><span data-stu-id="5f898-109">The Criteria pane contains a spreadsheet-like grid in which you specify options, such as which data columns to display, what rows to select, how to group rows, and so on.</span></span> <span data-ttu-id="5f898-110">有关详细信息，请参阅[“条件”窗格 (Visual Database Tools)](criteria-pane-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="5f898-110">For more information, see [Criteria Pane &#40;Visual Database Tools&#41;](criteria-pane-visual-database-tools.md).</span></span>  
  
-   <span data-ttu-id="5f898-111">SQL 窗格显示查询或视图的 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="5f898-111">The SQL pane displays the SQL statement for the query or view.</span></span> <span data-ttu-id="5f898-112">您可以对由设计器创建的 SQL 语句进行编辑，也可以输入自己的 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="5f898-112">You can edit the SQL statement created by the Designer or you can enter your own SQL statement.</span></span> <span data-ttu-id="5f898-113">对于输入不能用“关系图”窗格和“条件”窗格创建的 SQL 语句（例如联合查询），此窗格尤其有用。</span><span class="sxs-lookup"><span data-stu-id="5f898-113">It is particularly useful for entering SQL statements that cannot be created using the Diagram and Criteria panes, such as union queries.</span></span> <span data-ttu-id="5f898-114">有关详细信息，请参阅 [ SQL 窗格 (Visual Database Tools)](sql-pane-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="5f898-114">For more information, see [SQL Pane &#40;Visual Database Tools&#41;](sql-pane-visual-database-tools.md).</span></span>  
  
-   <span data-ttu-id="5f898-115">“结果”窗格显示一个网格，用来包含查询或视图检索到的数据。</span><span class="sxs-lookup"><span data-stu-id="5f898-115">The Results pane shows a grid with data retrieved by the query or view.</span></span> <span data-ttu-id="5f898-116">在查询和视图设计器中，该窗格显示最近执行的 SELECT 查询的结果。</span><span class="sxs-lookup"><span data-stu-id="5f898-116">In the Query and View Designer, the pane shows the results of the most recently executed SELECT query.</span></span> <span data-ttu-id="5f898-117">可以通过编辑网格单元格中的值来修改数据库，并可以添加或删除行。</span><span class="sxs-lookup"><span data-stu-id="5f898-117">You can modify the database by editing values in the cells of the grid, and you can add or delete rows.</span></span> <span data-ttu-id="5f898-118">有关详细信息，请参阅 [“结果”窗格 (Visual Database Tools)](results-pane-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="5f898-118">For more information, see [Results Pane &#40;Visual Database Tools&#41;](results-pane-visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="5f898-119">可以通过在任意一个窗格中进行操作来创建查询或视图：通过以下方法可以指定要显示的列，在“关系图”窗格中选择该列，在“条件”窗格中输入该列，或者在 SQL 窗格中使其成为 SQL 语句的一部分。</span><span class="sxs-lookup"><span data-stu-id="5f898-119">You can create a query or view by working in any of the panes: you can specify a column to display by choosing it in the Diagram pane, entering it into the Criteria pane, or making it part of the SQL statement in the SQL pane.</span></span>  
  
## <a name="displaying-and-hiding-panes"></a><span data-ttu-id="5f898-120">显示和隐藏窗格</span><span class="sxs-lookup"><span data-stu-id="5f898-120">Displaying and Hiding Panes</span></span>  
 <span data-ttu-id="5f898-121">若要隐藏窗格或显示不可见的窗格，请右键单击设计图面，指向“窗格”  ，再单击窗格的名称。</span><span class="sxs-lookup"><span data-stu-id="5f898-121">To hide a pane or display a pane that is not visible, right-click the design surface, point to **Pane**, and then click the name of the pane.</span></span> <span data-ttu-id="5f898-122">如果在查询设计器模式下打开了查询和视图设计器，则不会显示“结果”  窗格。</span><span class="sxs-lookup"><span data-stu-id="5f898-122">If the Query and View Designer is opened in Query Designer mode, the **Results** pane is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f898-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5f898-123">See Also</span></span>  
 <span data-ttu-id="5f898-124">[&#40;Visual Database Tools 的设计查询和视图操作指南主题&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="5f898-124">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span></span>  
 <span data-ttu-id="5f898-125">[&#40;Visual Database Tools 打开查询和视图设计器&#41;](open-the-query-and-view-designer-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="5f898-125">[Open the Query and View Designer &#40;Visual Database Tools&#41;](open-the-query-and-view-designer-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="5f898-126">SQL 编辑器 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="5f898-126">SQL Editor &#40;Visual Database Tools&#41;</span></span>](sql-editor-visual-database-tools.md)  
  
  
