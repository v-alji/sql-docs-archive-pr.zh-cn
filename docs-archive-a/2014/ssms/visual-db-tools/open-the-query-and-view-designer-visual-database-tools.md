---
title: 打开查询和视图设计器 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- opening View Designer
- View Designer, opening
- Query Designer [SQL Server], opening
- opening Query Designer
ms.assetid: b473f258-d53c-41c0-9ad9-528a2ff141f4
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3a36a0a9f014759269517a5774167f84c19b0b18
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587119"
---
# <a name="open-the-query-and-view-designer-visual-database-tools"></a><span data-ttu-id="7fa50-102">打开查询和视图设计器 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="7fa50-102">Open the Query and View Designer (Visual Database Tools)</span></span>
  <span data-ttu-id="7fa50-103">当您打开视图的定义、显示查询或视图的结果或者创建或打开查询时，查询和视图设计器将会打开。</span><span class="sxs-lookup"><span data-stu-id="7fa50-103">The Query and View Designer opens when you open the definition of a view, show the results for a query or view, or create or open a query.</span></span> <span data-ttu-id="7fa50-104">它由四个不同的窗格组成：</span><span class="sxs-lookup"><span data-stu-id="7fa50-104">It consists of four separate panes:</span></span>  
  
-   <span data-ttu-id="7fa50-105">“关系图”窗格以图形形式显示了您通过数据连接选择的表或表值对象。</span><span class="sxs-lookup"><span data-stu-id="7fa50-105">The Diagram pane presents a graphic display of the tables or table-valued objects you have selected from the data connection.</span></span> <span data-ttu-id="7fa50-106">同时也会显示它们之间的联接关系。</span><span class="sxs-lookup"><span data-stu-id="7fa50-106">It also shows any join relationships among them.</span></span>  
  
-   <span data-ttu-id="7fa50-107">“条件”窗格用于指定查询选项（例如要显示哪些数据列、如何对结果进行排序以及选择哪些行等），可以通过将选择输入到一个类似电子表格的网格中来进行指定。</span><span class="sxs-lookup"><span data-stu-id="7fa50-107">The Criteria pane allows you to specify query options - such as which data columns to display, how to order the results, and what rows to select - by entering your choices into a spreadsheet-like grid.</span></span>  
  
-   <span data-ttu-id="7fa50-108">您可以使用 SQL 窗格创建自己的 SQL 语句，也可以使用“条件”窗格和“关系图”窗格创建语句，在后面这种情况下将在 SQL 窗格中相应地创建 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="7fa50-108">You can use the SQL pane to create your own SQL statement, or you can use the Criteria pane and Diagram pane to create the statement, in which case the SQL statements will be created in the SQL pane.</span></span> <span data-ttu-id="7fa50-109">生成查询时，SQL 窗格将自动更新并重新设置格式以便于阅读。</span><span class="sxs-lookup"><span data-stu-id="7fa50-109">As you build your query, the SQL pane automatically updates and reformats to be easily read.</span></span>  
  
-   <span data-ttu-id="7fa50-110">“结果”窗格显示最近执行的“选择”查询的结果。</span><span class="sxs-lookup"><span data-stu-id="7fa50-110">The Results pane shows the results of the most recently executed Select query.</span></span> <span data-ttu-id="7fa50-111">（其他类型查询的结果会在消息框中显示。）</span><span class="sxs-lookup"><span data-stu-id="7fa50-111">(The results of other query types are displayed in message boxes.)</span></span>  
  
-   <span data-ttu-id="7fa50-112">这些窗格对于处理查询和视图非常有用。</span><span class="sxs-lookup"><span data-stu-id="7fa50-112">These panes are useful for working with both queries and views.</span></span>  
  
-   <span data-ttu-id="7fa50-113">当您打开一个视图或查询时，以上部分或全部窗格将随之打开。</span><span class="sxs-lookup"><span data-stu-id="7fa50-113">When you open a view or query some or all of the panes open with it.</span></span> <span data-ttu-id="7fa50-114">所打开的窗格取决于“选项”  对话框中的设置以及你所连接的数据库管理系统。</span><span class="sxs-lookup"><span data-stu-id="7fa50-114">Which ones open depend on the settings in the **Options** dialog box and what database management system you're connected to.</span></span> <span data-ttu-id="7fa50-115">默认设置是四个窗格全都打开。</span><span class="sxs-lookup"><span data-stu-id="7fa50-115">The default is that all four open.</span></span>  
  
### <a name="to-open-the-query-and-view-designer-for-a-view"></a><span data-ttu-id="7fa50-116">为视图打开查询和视图设计器</span><span class="sxs-lookup"><span data-stu-id="7fa50-116">To open the Query and View Designer for a view</span></span>  
  
1.  <span data-ttu-id="7fa50-117">在对象资源管理器中，右键单击要打开的视图，然后单击“设计”  或“打开视图”  。</span><span class="sxs-lookup"><span data-stu-id="7fa50-117">In Object Explorer, right-click the view you want to open and click **Design** or **Open View**.</span></span>  
  
     <span data-ttu-id="7fa50-118">如果选择“设计”  ，查询和视图设计器窗格将按照在“选项”  对话框中选定的选项设置打开。</span><span class="sxs-lookup"><span data-stu-id="7fa50-118">If you chose **Design**, the Query and View Designer panes open as dictated by the options selected in the **Options** dialog box.</span></span> <span data-ttu-id="7fa50-119">如果选择“打开视图”  ，默认情况下仅打开“结果”窗格。</span><span class="sxs-lookup"><span data-stu-id="7fa50-119">If you chose **Open View**, only the Results pane opens by default.</span></span>  
  
### <a name="to-open-the-query-and-view-designer-for-an-existing-query"></a><span data-ttu-id="7fa50-120">为现有查询打开查询和视图设计器</span><span class="sxs-lookup"><span data-stu-id="7fa50-120">To open the Query and View Designer for an existing query</span></span>  
  
1.  <span data-ttu-id="7fa50-121">在解决方案资源管理器中，展开“查询”  文件夹。</span><span class="sxs-lookup"><span data-stu-id="7fa50-121">In Solution Explorer, expand the **Queries** folder.</span></span>  
  
2.  <span data-ttu-id="7fa50-122">双击要打开的查询。</span><span class="sxs-lookup"><span data-stu-id="7fa50-122">Double-click the query you want to open.</span></span>  
  
3.  <span data-ttu-id="7fa50-123">突出显示相应的查询语句，右键单击突出显示的区域，再单击“在编辑器中设计查询”  。</span><span class="sxs-lookup"><span data-stu-id="7fa50-123">Highlight the query statement(s), right-click the highlighted area and click **Design Query in Editor**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fa50-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7fa50-124">See Also</span></span>  
 <span data-ttu-id="7fa50-125">[&#40;Visual Database Tools 的设计查询和视图操作指南主题&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="7fa50-125">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 [<span data-ttu-id="7fa50-126">查询和视图设计器工具 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="7fa50-126">Query and View Designer Tools &#40;Visual Database Tools&#41;</span></span>](query-and-view-designer-tools-visual-database-tools.md)  
  
  
