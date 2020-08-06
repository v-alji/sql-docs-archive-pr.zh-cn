---
title: SQL 窗格 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- Query Designer [SQL Server], SQL pane
- View Designer, SQL pane
- SQL pane [Visual Database Tools]
ms.assetid: dbabab18-0614-415b-a2ef-9bcd0d320d5c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3a87ec1d5517852fefb152e0ec7b3165fa32988b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682569"
---
# <a name="sql-pane-visual-database-tools"></a><span data-ttu-id="ded6b-102">SQL 窗格 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="ded6b-102">SQL Pane (Visual Database Tools)</span></span>
  <span data-ttu-id="ded6b-103">您可以使用 SQL 窗格创建自己的 SQL 语句，也可以使用“条件”窗格和“关系图”窗格创建语句，在后面这种情况下将在 SQL 窗格中相应地创建 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="ded6b-103">You can use the SQL pane to create your own SQL statement, or you can use the Criteria pane and Diagram pane to create the statement, in which case the SQL statements will be created in the SQL pane.</span></span> <span data-ttu-id="ded6b-104">生成查询时，SQL 窗格将自动更新并重新设置格式以便于阅读。</span><span class="sxs-lookup"><span data-stu-id="ded6b-104">As you build your query, the SQL pane automatically updates and reformats for easy readability.</span></span>  
  
 <span data-ttu-id="ded6b-105">若要打开 SQL 窗格，请首先打开查询和视图设计器（在服务器资源管理器中选择相应的数据库对象后，在“数据库”  菜单中单击“新建查询”  ）。</span><span class="sxs-lookup"><span data-stu-id="ded6b-105">To open the SQL pane, first open Query and View Designer (with a database object selected in Server Explorer, from the **Database** menu, click **New Query**).</span></span> <span data-ttu-id="ded6b-106">然后在“查询设计器”  菜单中指向“窗格”  ，再单击“SQL”  。</span><span class="sxs-lookup"><span data-stu-id="ded6b-106">Then from the **Query Designer** menu point to **Pane** and click **SQL**.</span></span>  
  
 <span data-ttu-id="ded6b-107">在 SQL 窗格中，可以进行以下操作：</span><span class="sxs-lookup"><span data-stu-id="ded6b-107">In the SQL pane you can:</span></span>  
  
-   <span data-ttu-id="ded6b-108">通过输入 SQL 语句创建新查询。</span><span class="sxs-lookup"><span data-stu-id="ded6b-108">Create new queries by entering SQL statements.</span></span>  
  
-   <span data-ttu-id="ded6b-109">根据在“关系图”窗格和“条件”窗格中进行的设置，对查询和视图设计器创建的 SQL 语句进行修改。</span><span class="sxs-lookup"><span data-stu-id="ded6b-109">Modify the SQL statement created by the Query and View Designer based on settings you make in the Diagram and Criteria panes.</span></span>  
  
-   <span data-ttu-id="ded6b-110">输入语句以利用所使用数据库的特有功能。</span><span class="sxs-lookup"><span data-stu-id="ded6b-110">Enter statements that take advantage of features specific to the database you are using.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ded6b-111">请务必了解所用数据库中数据库对象的标识规则。</span><span class="sxs-lookup"><span data-stu-id="ded6b-111">Be sure you know the rules for identifying database objects in the database you are using.</span></span> <span data-ttu-id="ded6b-112">有关详细信息，请参阅数据库管理系统文档。</span><span class="sxs-lookup"><span data-stu-id="ded6b-112">For details, see the documentation for your database management system.</span></span>  
  
## <a name="statements-in-the-sql-pane"></a><span data-ttu-id="ded6b-113">SQL 窗格中的语句</span><span class="sxs-lookup"><span data-stu-id="ded6b-113">Statements in the SQL Pane</span></span>  
 <span data-ttu-id="ded6b-114">您可以直接在 SQL 窗格中编辑当前查询。</span><span class="sxs-lookup"><span data-stu-id="ded6b-114">You can edit the current query directly in the SQL pane.</span></span> <span data-ttu-id="ded6b-115">当移动到另一窗格时，查询和视图设计器会自动设置语句格式，再更改“关系图”窗格和“条件”窗格以同语句匹配。</span><span class="sxs-lookup"><span data-stu-id="ded6b-115">When you move to another pane, the Query and View Designer automatically formats your statement, and then changes the Diagram and Criteria panes to match your statement.</span></span>  
  
 <span data-ttu-id="ded6b-116">如果语句不能在“关系图”窗格和“条件”窗格中表示出来，并且这两个窗格是可见的，则查询和视图设计器将显示一条错误信息，然后提供两种选择：</span><span class="sxs-lookup"><span data-stu-id="ded6b-116">If your statement cannot be represented in the Diagram and Criteria panes, and if those panes are visible, Query and View Designer displays an error and then offers you two choices:</span></span>  
  
-   <span data-ttu-id="ded6b-117">忽略无法在“关系图”窗格和“条件”窗格中表示的语句。</span><span class="sxs-lookup"><span data-stu-id="ded6b-117">Ignore that the statement can not be represented in the Diagram and Criteria panes.</span></span>  
  
-   <span data-ttu-id="ded6b-118">撤销无法表示的更改，并恢复到最近的 SQL 语句版本。</span><span class="sxs-lookup"><span data-stu-id="ded6b-118">Undo the change that can not be represented and revert to the most recent version of the SQL statement.</span></span>  
  
 <span data-ttu-id="ded6b-119">如果选择忽略无法在“关系图”窗格和“条件”窗格中表示的语句，查询和视图设计器将使其他窗格变成灰色，指示它们不再反映 SQL 窗格的内容。</span><span class="sxs-lookup"><span data-stu-id="ded6b-119">If you choose to ignore that the statement can not be represented in the Diagram and Criteria panes, the Query and View Designer dims the other panes to indicate that they no longer reflect the contents of the SQL pane.</span></span>  
  
 <span data-ttu-id="ded6b-120">您可以继续编辑语句，并像执行任何 SQL 语句一样执行该语句。</span><span class="sxs-lookup"><span data-stu-id="ded6b-120">You can continue to edit the statement and execute it as you would any SQL statement.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ded6b-121">如果输入 SQL 语句，但随后通过更改“关系图”窗格和“条件”窗格对查询做进一步更改，则查询和视图设计器将重新生成和显示 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="ded6b-121">If you enter an SQL statement, but then make further changes to the query by changing the Diagram and Criteria panes, the Query and View Designer rebuilds and redisplays the SQL statement.</span></span> <span data-ttu-id="ded6b-122">在某些情况下，此操作产生的 SQL 语句在构造上和原先输入的 SQL 语句将有所不同（尽管该语句始终会产生相同的结果）。</span><span class="sxs-lookup"><span data-stu-id="ded6b-122">In some cases, this action results in an SQL statement that is constructed differently from the one you originally entered (though it will always yield the same results).</span></span> <span data-ttu-id="ded6b-123">当使用的搜索条件涉及用 AND 和 OR 链接的多个子句时，尤其可能产生这种差异。</span><span class="sxs-lookup"><span data-stu-id="ded6b-123">This difference is particularly likely when you are working with search conditions that involve several clauses linked with AND and OR.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ded6b-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ded6b-124">See Also</span></span>  
 <span data-ttu-id="ded6b-125">[&#40;Visual Database Tools 创建查询&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="ded6b-125">[Create Queries &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="ded6b-126">[&#40;Visual Database Tools 运行查询&#41;](run-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="ded6b-126">[Run Queries &#40;Visual Database Tools&#41;](run-queries-visual-database-tools.md) </span></span>  
 <span data-ttu-id="ded6b-127">[&#40;Visual Database Tools 的设计查询和视图操作指南主题&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="ded6b-127">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span></span>  
 <span data-ttu-id="ded6b-128">[Visual Database Tools &#40;的 "关系图" 窗格&#41;](diagram-pane-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="ded6b-128">[Diagram Pane &#40;Visual Database Tools&#41;](diagram-pane-visual-database-tools.md) </span></span>  
 <span data-ttu-id="ded6b-129">[Visual Database Tools &#40;的 "条件" 窗格&#41;](criteria-pane-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="ded6b-129">[Criteria Pane &#40;Visual Database Tools&#41;](criteria-pane-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="ded6b-130">“结果”窗格 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="ded6b-130">Results Pane &#40;Visual Database Tools&#41;</span></span>](results-pane-visual-database-tools.md)  
  
  
