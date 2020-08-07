---
title: 对查询结果中的行进行分组 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- summarizing table subsets
- grouping rows
- grouping query results
ms.assetid: b07082d5-4d55-4903-9af9-4c470554c6d3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 52de25c86425d95f5917d89c8a3f4fec8939fb16
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587680"
---
# <a name="group-rows-in-query-results-visual-database-tools"></a><span data-ttu-id="f5513-102">对查询结果中的行进行分组 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="f5513-102">Group Rows in Query Results (Visual Database Tools)</span></span>
  <span data-ttu-id="f5513-103">如果希望创建小计或显示表的子集的其他摘要信息，可使用聚合查询创建组。</span><span class="sxs-lookup"><span data-stu-id="f5513-103">If you want to create subtotals or show other summary information for subsets of a table, you create groups using an aggregate query.</span></span> <span data-ttu-id="f5513-104">各组可对表中具有相同值的所有行的数据进行汇总。</span><span class="sxs-lookup"><span data-stu-id="f5513-104">Each group summarizes the data for all the rows in the table that have the same value.</span></span>  
  
 <span data-ttu-id="f5513-105">例如，假设希望看到 `titles` 表中某书籍的平均价格，并将结果按出版商分组。</span><span class="sxs-lookup"><span data-stu-id="f5513-105">For example, you might want to see the average price of a book in the `titles` table, but break the results down by publisher.</span></span> <span data-ttu-id="f5513-106">为此，需要按出版商（例如 `pub_id`）对查询进行分组。</span><span class="sxs-lookup"><span data-stu-id="f5513-106">To do so, you group the query by publisher (for example, `pub_id`).</span></span> <span data-ttu-id="f5513-107">声称的查询输出结果可能类似以下形式：</span><span class="sxs-lookup"><span data-stu-id="f5513-107">The resulting query output might look like this:</span></span>  
  
 <span data-ttu-id="f5513-108">![查询结果：按出版商分组的平均价格](../../database-engine/media//dv3w9e1.gif "查询结果：按出版商分组的平均价格")</span><span class="sxs-lookup"><span data-stu-id="f5513-108">![Query results: average price grouped by publisher](../../database-engine/media//dv3w9e1.gif "Query results: average price grouped by publisher")</span></span>  
  
 <span data-ttu-id="f5513-109">当对数据进行分组时，只能显示汇总数据和分组数据，例如：</span><span class="sxs-lookup"><span data-stu-id="f5513-109">When you group data, you can display only summary or grouped data, such as:</span></span>  
  
-   <span data-ttu-id="f5513-110">分组列（GROUP BY 子句中显示的列）的值。</span><span class="sxs-lookup"><span data-stu-id="f5513-110">The values of the grouped columns (those that appear in the GROUP BY clause).</span></span> <span data-ttu-id="f5513-111">在上面的示例中， `pub_id` 就是分组列。</span><span class="sxs-lookup"><span data-stu-id="f5513-111">In the example above, `pub_id` is the grouped column.</span></span>  
  
-   <span data-ttu-id="f5513-112">由类似于 SUM(&#xA0;</ph>) 和 AVG(&#xA0;</ph>) 的聚合函数生成的值。</span><span class="sxs-lookup"><span data-stu-id="f5513-112">Values produced by aggregate functions such as SUM( ) and AVG( ).</span></span> <span data-ttu-id="f5513-113">在上面的示例中，第二列就是对 `price` 列应用 AVG( ) 函数而生成的。</span><span class="sxs-lookup"><span data-stu-id="f5513-113">In the example above, the second column is produced by using the AVG( ) function with the `price` column.</span></span>  
  
 <span data-ttu-id="f5513-114">您无法显示单个行的值。</span><span class="sxs-lookup"><span data-stu-id="f5513-114">You cannot display values from individual rows.</span></span> <span data-ttu-id="f5513-115">例如，如果仅按出版商分组，则无法同时在查询中显示单个书名。</span><span class="sxs-lookup"><span data-stu-id="f5513-115">For example, if you group only by publisher, you cannot also display individual titles in the query.</span></span> <span data-ttu-id="f5513-116">因此，如果向查询输出中添加列，则 [查询和视图设计器](visual-database-tools.md) 会自动将其添加到 [SQL 窗格](sql-pane-visual-database-tools.md)内语句的 GROUP BY 子句中。</span><span class="sxs-lookup"><span data-stu-id="f5513-116">Therefore, if you add columns to the query output, the [Query and View Designer](visual-database-tools.md) automatically adds them to the GROUP BY clause of the statement in the [SQL pane](sql-pane-visual-database-tools.md).</span></span> <span data-ttu-id="f5513-117">如果希望对某列进行聚合，则可为该列指定聚合函数。</span><span class="sxs-lookup"><span data-stu-id="f5513-117">If you want a column to be aggregated instead, you can specify an aggregate function for that column.</span></span>  
  
 <span data-ttu-id="f5513-118">如果按多个列进行分组，查询中的每一组都会显示所有分组列的聚合值。</span><span class="sxs-lookup"><span data-stu-id="f5513-118">If you group by more than one column, each group in the query shows the aggregate values for all grouping columns.</span></span>  
  
 <span data-ttu-id="f5513-119">例如，下面对 `titles` 表进行的查询按出版商 (`pub_id`) 和书籍类型 (`type`) 进行分组。</span><span class="sxs-lookup"><span data-stu-id="f5513-119">For example, the following query against the `titles` table groups by publisher (`pub_id`) and also by book type (`type`).</span></span> <span data-ttu-id="f5513-120">查询结果将按出版商进行排序，并会显示相应出版商出版的各种不同类型书籍的摘要信息：</span><span class="sxs-lookup"><span data-stu-id="f5513-120">The query results are ordered by publisher and show summary information for each different type of book that the publisher produces:</span></span>  
  
```  
SELECT pub_id, type, SUM(price) Total_price  
FROM titles  
GROUP BY pub_id, type  
```  
  
 <span data-ttu-id="f5513-121">生成的输出结果可能类似以下形式：</span><span class="sxs-lookup"><span data-stu-id="f5513-121">The resulting output might look like this:</span></span>  
  
 <span data-ttu-id="f5513-122">![查询结果：按出版商和类型分组的价格](../../database-engine/media//dv3w9e2.gif "查询结果：按出版商和类型分组的价格")</span><span class="sxs-lookup"><span data-stu-id="f5513-122">![Query results: price grouped by publisher and type](../../database-engine/media//dv3w9e2.gif "Query results: price grouped by publisher and type")</span></span>  
  
### <a name="to-group-rows"></a><span data-ttu-id="f5513-123">对行进行分组</span><span class="sxs-lookup"><span data-stu-id="f5513-123">To group rows</span></span>  
  
1.  <span data-ttu-id="f5513-124">通过将要汇总的表添加到“关系图”窗格中来启动查询。</span><span class="sxs-lookup"><span data-stu-id="f5513-124">Start the query by adding the tables you want to summarize to the Diagram pane.</span></span>  
  
2.  <span data-ttu-id="f5513-125">右键单击“关系图”窗格的背景，再从快捷菜单中选择“添加分组依据”  。</span><span class="sxs-lookup"><span data-stu-id="f5513-125">Right-click the background of the Diagram pane, then choose **Add Group By** from the shortcut menu.</span></span> <span data-ttu-id="f5513-126">查询和视图设计器会在“条件”窗格的网格中添加一个“分组依据”  列。</span><span class="sxs-lookup"><span data-stu-id="f5513-126">The Query and View Designer adds a **Group By** column to the grid in the Criteria pane.</span></span>  
  
3.  <span data-ttu-id="f5513-127">将要分组的一列或多列添加到“条件”窗格中。</span><span class="sxs-lookup"><span data-stu-id="f5513-127">Add the column or columns you want to group to the Criteria pane.</span></span> <span data-ttu-id="f5513-128">如果希望列显示在查询输出中，请确保为输出选中了“输出”  列。</span><span class="sxs-lookup"><span data-stu-id="f5513-128">If you want the column to appear in the query output, be sure that the **Output** column is selected for output.</span></span>  
  
     <span data-ttu-id="f5513-129">查询和视图设计器将在 SQL 窗格内的语句中添加 GROUP BY 子句。</span><span class="sxs-lookup"><span data-stu-id="f5513-129">The Query and View Designer adds a GROUP BY clause to the statement in the SQL pane.</span></span> <span data-ttu-id="f5513-130">例如，SQL 语句可能类似以下形式：</span><span class="sxs-lookup"><span data-stu-id="f5513-130">For example, the SQL statement might look like this:</span></span>  
  
    ```  
    SELECT pub_id  
    FROM titles  
    GROUP BY pub_id  
    ```  
  
4.  <span data-ttu-id="f5513-131">将要聚合的一列或多列添加到“条件”窗格中。</span><span class="sxs-lookup"><span data-stu-id="f5513-131">Add the column or columns you want to aggregate to the Criteria pane.</span></span> <span data-ttu-id="f5513-132">确保将该列标记为输出。</span><span class="sxs-lookup"><span data-stu-id="f5513-132">Be sure that the column is marked for output.</span></span>  
  
5.  <span data-ttu-id="f5513-133">在要进行聚合的列的“分组依据”  网格单元格中，选择适当的聚合函数。</span><span class="sxs-lookup"><span data-stu-id="f5513-133">In the **Group By** grid cell for the column that is going to be aggregated, select the appropriate aggregate function.</span></span>  
  
     <span data-ttu-id="f5513-134">查询及视图设计器将自动为要汇总的列分配列别名。</span><span class="sxs-lookup"><span data-stu-id="f5513-134">The Query and View Designer automatically assigns a column alias to the column you are summarizing.</span></span> <span data-ttu-id="f5513-135">您可以用更有意义的名称替换这一自动生成的别名。</span><span class="sxs-lookup"><span data-stu-id="f5513-135">You can replace this automatically generated alias with a more meaningful one.</span></span> <span data-ttu-id="f5513-136">有关详细信息，请参阅[创建列别名 (Visual Database Tools)](create-column-aliases-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="f5513-136">For more details, see [Create Column Aliases &#40;Visual Database Tools&#41;](create-column-aliases-visual-database-tools.md).</span></span>  
  
     <span data-ttu-id="f5513-137">![向查询结果集添加列别名](../../database-engine/media//dv3w9e3.gif "向查询结果集添加列别名")</span><span class="sxs-lookup"><span data-stu-id="f5513-137">![Adding a column alias to the query result set](../../database-engine/media//dv3w9e3.gif "Adding a column alias to the query result set")</span></span>  
  
     <span data-ttu-id="f5513-138">**SQL** 窗格中的相应语句可能类似以下形式：</span><span class="sxs-lookup"><span data-stu-id="f5513-138">The corresponding statement in the **SQL** pane might look like this:</span></span>  
  
    ```  
    SELECT   pub_id, SUM(price) AS Totalprice  
    FROM     titles  
    GROUP BY pub_id  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f5513-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f5513-139">See Also</span></span>  
 [<span data-ttu-id="f5513-140">对查询结果进行排序和分组 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="f5513-140">Sort and Group Query Results &#40;Visual Database Tools&#41;</span></span>](sort-and-group-query-results-visual-database-tools.md)  
  
  
