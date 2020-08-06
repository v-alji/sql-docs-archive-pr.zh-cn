---
title: 在聚合查询中使用列 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- HAVING clause, query summary results
- GROUP BY clause, query summary results
- aggregate queries [SQL Server]
- WHERE clause, query summary results
ms.assetid: 1b82681f-3d4f-4b9a-bb1d-2060e44f2577
author: stevestein
ms.author: sstein
ms.openlocfilehash: 880f7529cebd7f51951e62952e3b5f13190f99b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682567"
---
# <a name="work-with-columns-in-aggregate-queries-visual-database-tools"></a><span data-ttu-id="08548-102">在聚合查询中使用列 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="08548-102">Work with Columns in Aggregate Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="08548-103">创建聚合查询时， [查询和视图设计器](visual-database-tools.md) 将进行某些假设以便可以构造有效的查询。</span><span class="sxs-lookup"><span data-stu-id="08548-103">When you create aggregate queries the [Query and View Designer](visual-database-tools.md) makes certain assumptions so that it can construct a valid query.</span></span> <span data-ttu-id="08548-104">例如，如果创建聚合查询并将某个数据列标记为输出，则查询和视图设计器将自动将该列包含在 GROUP BY 子句中，以避免无意中试图在汇总中显示个别行的内容。</span><span class="sxs-lookup"><span data-stu-id="08548-104">For example, if you are creating an aggregate query and mark a data column for output, the Query and View Designer automatically makes the column part of the GROUP BY clause so that you do not inadvertently attempt to display the contents of an individual row in a summary.</span></span>  
  
## <a name="using-group-by"></a><span data-ttu-id="08548-105">使用“分组依据”</span><span class="sxs-lookup"><span data-stu-id="08548-105">Using Group By</span></span>  
 <span data-ttu-id="08548-106">查询和视图设计器在处理列时使用以下原则：</span><span class="sxs-lookup"><span data-stu-id="08548-106">The Query and View Designer uses the following guidelines for working with columns:</span></span>  
  
-   <span data-ttu-id="08548-107">在选择“分组依据”选项或向查询中添加聚合函数时，所有标记为输出或用于排序的列将自动添加到 GROUP BY 子句中。</span><span class="sxs-lookup"><span data-stu-id="08548-107">When you choose the Group By option or add an aggregate function to a query, all columns marked for output or used for sorting are automatically added to the GROUP BY clause.</span></span> <span data-ttu-id="08548-108">如果列已经是聚合函数的一部分，则不会自动添加到 GROUP BY 子句中。</span><span class="sxs-lookup"><span data-stu-id="08548-108">Columns are not automatically added to the GROUP BY clause if they are already part of an aggregate function.</span></span>  
  
     <span data-ttu-id="08548-109">如果不想使某个特定列成为 GROUP BY 子句的一部分，必须在“条件”窗格的“分组依据”列中选择不同的选项以手动更改该设置。</span><span class="sxs-lookup"><span data-stu-id="08548-109">If you do not want a particular column to be part of the GROUP BY clause, you must manually change it by selecting a different option in the Group By column of the Criteria pane.</span></span> <span data-ttu-id="08548-110">然而，查询和视图设计器不会禁止您选择可能产生无法运行的查询的选项。</span><span class="sxs-lookup"><span data-stu-id="08548-110">However, the Query and View Designer will not prevent you from choosing an option that can result in a query that will not run.</span></span>  
  
-   <span data-ttu-id="08548-111">如果在“条件”窗格或 SQL 窗格中手动向聚合函数添加查询输出列，则查询和视图设计器不能自动从查询中移除其他输出列。</span><span class="sxs-lookup"><span data-stu-id="08548-111">If you manually add a query output column to an aggregate function in either the Criteria or SQL pane, the Query and View Designer does not automatically remove other output columns from the query.</span></span> <span data-ttu-id="08548-112">因此，必须从查询输出中移除剩余的列，或使它们成为 GROUP BY 子句或聚合函数的一部分。</span><span class="sxs-lookup"><span data-stu-id="08548-112">Therefore, you must remove the remaining columns from the query output or make them part of the GROUP BY clause or of an aggregate function.</span></span>  
  
 <span data-ttu-id="08548-113">向“条件”窗格的“筛选器”列中输入搜索条件时，查询和视图设计器将遵循以下规则：</span><span class="sxs-lookup"><span data-stu-id="08548-113">When you enter a search condition into the Filter column of the Criteria pane, the Query and View Designer follows these rules:</span></span>  
  
-   <span data-ttu-id="08548-114">如果没有显示网格的“分组依据”  列（因为尚未指定聚合查询），则搜索条件将放入 WHERE 子句中。</span><span class="sxs-lookup"><span data-stu-id="08548-114">If the **Group By** column of the grid is not displayed (because you have not yet specified an aggregate query), the search condition is placed into the WHERE clause.</span></span>  
  
-   <span data-ttu-id="08548-115">如果已在聚合查询中，并在“分组依据”列中选择了 **Where** 选项，则搜索条件被放入 WHERE 子句中。</span><span class="sxs-lookup"><span data-stu-id="08548-115">If you are already in an aggregate query and have selected the option **Where** in the **Group By** column, the search condition is placed into the WHERE clause.</span></span>  
  
-   <span data-ttu-id="08548-116">如果“分组依据”  列包含 **Where** 以外的任何值，则搜索条件将放入 HAVING 子句中。</span><span class="sxs-lookup"><span data-stu-id="08548-116">If the **Group By** column contains any value other than **Where**, the search condition is placed in the HAVING clause.</span></span>  
  
## <a name="using-the-having-and-where-clauses"></a><span data-ttu-id="08548-117">使用 HAVING 和 WHERE 子句</span><span class="sxs-lookup"><span data-stu-id="08548-117">Using the HAVING and WHERE Clauses</span></span>  
 <span data-ttu-id="08548-118">以下原则描述如何在聚合查询的搜索条件中引用列。</span><span class="sxs-lookup"><span data-stu-id="08548-118">The following principles describe how you can reference columns in an aggregate query in search conditions.</span></span> <span data-ttu-id="08548-119">通常，可以在搜索条件中使用列来筛选要汇总的行（WHERE 子句）或确定要在最终输出中显示的分组结果（HAVING 子句）。</span><span class="sxs-lookup"><span data-stu-id="08548-119">In general, you can use a column in a search condition to filter the rows that should be summarized (a WHERE clause) or to determine which grouped results appear in the final output (a HAVING clause).</span></span>  
  
-   <span data-ttu-id="08548-120">各个数据列可以出现在 WHERE 子句也可以出现在 HAVING 子句中，这取决于在查询中的其他地方使用这些数据列的方式。</span><span class="sxs-lookup"><span data-stu-id="08548-120">Individual data columns can appear in either the WHERE or HAVING clause, depending on how they are used elsewhere in the query.</span></span>  
  
-   <span data-ttu-id="08548-121">WHERE 子句用于选择行的子集以进行汇总和分组，因此在分组前应用 WHERE 子句。</span><span class="sxs-lookup"><span data-stu-id="08548-121">WHERE clauses are used to select a subset of rows for summarizing and grouping and are thus applied before any grouping is done.</span></span> <span data-ttu-id="08548-122">所以，即使某个数据列不是 GROUP BY 子句的一部分或者不包含在聚合函数中，也可以在 WHERE 子句中使用该列。</span><span class="sxs-lookup"><span data-stu-id="08548-122">Therefore, you can use a data column in a WHERE clause even if it is not part of the GROUP BY clause or contained in an aggregate function.</span></span> <span data-ttu-id="08548-123">例如，下面的语句选择所有超过 10.00 美元的书籍并求其平均价格：</span><span class="sxs-lookup"><span data-stu-id="08548-123">For example, the following statement selects all titles that cost more than $10.00 and averages the price:</span></span>  
  
    ```  
    SELECT AVG(price)  
    FROM titles  
    WHERE price > 10  
    ```  
  
-   <span data-ttu-id="08548-124">如果创建的搜索条件所涉及的列同时也用于 GROUP BY 子句或聚合函数中，则该搜索条件既可以作为 WHERE 子句出现也可以作为 HAVING 子句出现，你可以在创建条件时决定以哪一种形式出现。</span><span class="sxs-lookup"><span data-stu-id="08548-124">If you create a search condition that involves a column also used in a GROUP BY clause or aggregate function, the search condition can appear as either a WHERE clause or a HAVING clause - you can decide which when you create the condition.</span></span> <span data-ttu-id="08548-125">例如，下面的语句创建每个出版商的书籍的平均价格，然后显示平均价格超过 10.00 美元的出版商的平均值：</span><span class="sxs-lookup"><span data-stu-id="08548-125">For example, the following statement creates an average price for the titles for each publisher, then displays the average for the publishers in which the average price is greater than $10.00:</span></span>  
  
    ```  
    SELECT pub_id, AVG(price)  
    FROM titles  
    GROUP BY pub_id  
    HAVING (AVG(price) > 10)  
    ```  
  
-   <span data-ttu-id="08548-126">如果在搜索条件中使用聚合函数，则条件将涉及汇总，因此必须是 HAVING 子句的一部分。</span><span class="sxs-lookup"><span data-stu-id="08548-126">If you use an aggregate function in a search condition, the condition involves a summary and must therefore be part of the HAVING clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08548-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="08548-127">See Also</span></span>  
 <span data-ttu-id="08548-128">[&#40;Visual Database Tools&#41;汇总查询结果](summarize-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="08548-128">[Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="08548-129">对查询结果进行排序和分组 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="08548-129">Sort and Group Query Results &#40;Visual Database Tools&#41;</span></span>](sort-and-group-query-results-visual-database-tools.md)  
  
  
