---
title: " (Visual Database Tools) 汇总或聚合表中所有行的值 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- summarizing query results
- aggregate functions [SQL Server], summarizing query results
ms.assetid: f5af876e-f937-4110-ba09-07999c35a699
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5c4d80c8ab2b811b8e796f0a37b2180a2866c332
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691471"
---
# <a name="summarize-or-aggregate-values-for-all-rows-in-a-table-visual-database-tools"></a><span data-ttu-id="18d99-102">汇总或聚合表中所有行的值 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="18d99-102">Summarize or Aggregate Values for All Rows in a Table (Visual Database Tools)</span></span>
  <span data-ttu-id="18d99-103">使用聚合函数，可为表中所有值创建汇总。</span><span class="sxs-lookup"><span data-stu-id="18d99-103">Using an aggregate function, you can create a summary for all the values in a table.</span></span> <span data-ttu-id="18d99-104">例如，可创建如下所示的查询，以显示 `titles` 表中所有书籍的总价：</span><span class="sxs-lookup"><span data-stu-id="18d99-104">For example, you can create a query such as the following to display the total price for all books in the `titles` table:</span></span>  
  
```  
SELECT SUM(price)  
FROM titles  
```  
  
 <span data-ttu-id="18d99-105">通过对多个列使用聚合函数，可在同一查询中创建多个聚合。</span><span class="sxs-lookup"><span data-stu-id="18d99-105">You can create multiple aggregations in the same query by using aggregate functions with more than one column.</span></span> <span data-ttu-id="18d99-106">例如，可创建计算 `price` 列的合计以及 `discount` 列的平均值的查询。</span><span class="sxs-lookup"><span data-stu-id="18d99-106">For example, you can create a query that calculates the total of the `price` column and the average of the `discount` column.</span></span>  
  
 <span data-ttu-id="18d99-107">您也可在同一查询中用不同方式聚合同一列（如合计、计数以及求平均值）。</span><span class="sxs-lookup"><span data-stu-id="18d99-107">You can also aggregate the same column in different ways (such as totaling, counting, and averaging) in the same query.</span></span> <span data-ttu-id="18d99-108">例如，下面的查询将对 `price` 表的 `titles` 列求平均值并进行汇总：</span><span class="sxs-lookup"><span data-stu-id="18d99-108">For example, the following query averages and summarizes the `price` column from the `titles` table:</span></span>  
  
```  
SELECT AVG(price), SUM(price)  
FROM titles  
```  
  
 <span data-ttu-id="18d99-109">如果添加搜索条件，则可聚合满足该条件的行子集。</span><span class="sxs-lookup"><span data-stu-id="18d99-109">If you add a search condition, you can aggregate the subset of rows that meet that condition.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="18d99-110">您还可以对表中的所有行或满足特定条件的行进行计数。</span><span class="sxs-lookup"><span data-stu-id="18d99-110">You can also count all the rows in the table or the ones that meet a specific condition.</span></span> <span data-ttu-id="18d99-111">有关详细信息，请参阅[如何计算表中的行数 (Visual Database Tools)](visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="18d99-111">For details, see [Count Rows in a Table &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="18d99-112">当为表中的所有行创建单个聚合值时，将仅显示聚合值本身。</span><span class="sxs-lookup"><span data-stu-id="18d99-112">When you create a single aggregation value for all rows in a table, you display only the aggregate values themselves.</span></span> <span data-ttu-id="18d99-113">例如，如果对 `price` 表的 `titles` 列的值进行合计，将无法同时显示单个书名、出版商名称等。</span><span class="sxs-lookup"><span data-stu-id="18d99-113">For example, if you are totaling the value of the `price` column of the `titles` table, you would not also display individual titles, publisher names, and so on.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="18d99-114">如果进行小计（即创建组），则可显示每个组的列值。</span><span class="sxs-lookup"><span data-stu-id="18d99-114">If you are subtotaling - that is, creating groups - you can display column values for each group.</span></span> <span data-ttu-id="18d99-115">有关详细信息，请参阅[对查询结果中的行进行分组 (Visual Database Tools)](group-rows-in-query-results-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="18d99-115">For details, see [Group Rows in Query Results &#40;Visual Database Tools&#41;](group-rows-in-query-results-visual-database-tools.md).</span></span>  
  
### <a name="to-aggregate-values-for-all-rows"></a><span data-ttu-id="18d99-116">对所有行的值进行聚合</span><span class="sxs-lookup"><span data-stu-id="18d99-116">To aggregate values for all rows</span></span>  
  
1.  <span data-ttu-id="18d99-117">请确保您要聚合的表已经包含在“关系图”窗格中。</span><span class="sxs-lookup"><span data-stu-id="18d99-117">Be sure the table you want to aggregate is already present in the Diagram pane.</span></span>  
  
2.  <span data-ttu-id="18d99-118">右键单击“关系图”窗格的背景，再从快捷菜单中选择“分组依据”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="18d99-118">Right-click the background of the Diagram pane, then choose **Group By** from the shortcut menu.</span></span> <span data-ttu-id="18d99-119">[查询和视图设计器](query-and-view-designer-tools-visual-database-tools.md)会在“条件”窗格的网格中添加一个“分组依据”\*\*\*\* 列。</span><span class="sxs-lookup"><span data-stu-id="18d99-119">The [Query and View Designer](query-and-view-designer-tools-visual-database-tools.md) adds a **Group By** column to the grid in the Criteria pane.</span></span>  
  
3.  <span data-ttu-id="18d99-120">将要聚合的列添加到“条件”窗格中。</span><span class="sxs-lookup"><span data-stu-id="18d99-120">Add the column you want to aggregate to the Criteria pane.</span></span> <span data-ttu-id="18d99-121">确保将该列标记为输出。</span><span class="sxs-lookup"><span data-stu-id="18d99-121">Be sure that the column is marked for output.</span></span>  
  
     <span data-ttu-id="18d99-122">查询及视图设计器将自动为要汇总的列分配列别名。</span><span class="sxs-lookup"><span data-stu-id="18d99-122">The Query and View Designer automatically assigns a column alias to the column you are summarizing.</span></span> <span data-ttu-id="18d99-123">您可以用更有意义的名称替换此别名。</span><span class="sxs-lookup"><span data-stu-id="18d99-123">You can replace this alias with a more meaningful one.</span></span> <span data-ttu-id="18d99-124">有关详细信息，请参阅[创建列别名 (Visual Database Tools)](create-column-aliases-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="18d99-124">For details, see [Create Column Aliases &#40;Visual Database Tools&#41;](create-column-aliases-visual-database-tools.md).</span></span>  
  
4.  <span data-ttu-id="18d99-125">在“分组依据”\*\*\*\* 网格列中，选择适当的聚合函数，例如：**Sum**、**Avg**、**Min**、**Max** 和 **Count**。</span><span class="sxs-lookup"><span data-stu-id="18d99-125">In the **Group By** grid column, select the appropriate aggregate function, such as: **Sum**, **Avg**, **Min**, **Max**, **Count**.</span></span> <span data-ttu-id="18d99-126">如果只希望聚合结果集中的唯一行，请选择带 DISTINCT 选项的聚合函数，如 **Min Distinct**。</span><span class="sxs-lookup"><span data-stu-id="18d99-126">If you want to aggregate only unique rows in the result set, choose an aggregate function with the DISTINCT options, such as **Min Distinct**.</span></span> <span data-ttu-id="18d99-127">不要选择 **Group By**、 **Expression**或 **Where**，因为这些选项不适用于聚合所有行。</span><span class="sxs-lookup"><span data-stu-id="18d99-127">Do not choose **Group By**, **Expression**, or **Where**, because those options do not apply when you are aggregating all rows.</span></span>  
  
     <span data-ttu-id="18d99-128">查询和视图设计器将用指定的聚合函数替换 [“SQL”窗格](sql-pane-visual-database-tools.md) 内语句中的列名。</span><span class="sxs-lookup"><span data-stu-id="18d99-128">The Query and View Designer replaces the column name in the statement in the [SQL pane](sql-pane-visual-database-tools.md) with the aggregate function that you specify.</span></span> <span data-ttu-id="18d99-129">例如，SQL 语句可能类似以下形式：</span><span class="sxs-lookup"><span data-stu-id="18d99-129">For example, the SQL statement might look like this:</span></span>  
  
    ```  
    SELECT SUM(price)  
    FROM titles  
    ```  
  
5.  <span data-ttu-id="18d99-130">如果希望在查询中创建多个聚合，请重复第 3 和第 4 步。</span><span class="sxs-lookup"><span data-stu-id="18d99-130">If you want to create more than one aggregation in the query, repeat steps 3 and 4.</span></span>  
  
     <span data-ttu-id="18d99-131">当向查询输出列表或排序依据列表中添加另一列时，查询和视图设计器会自动在网格的“分组依据”\*\*\*\* 列中填充 **Group By** 一词。</span><span class="sxs-lookup"><span data-stu-id="18d99-131">When you add another column to the query output list or order by list, the Query and View Designer automatically fills the term **Group By** into the **Group By** column of the grid.</span></span> <span data-ttu-id="18d99-132">请选择适当的聚合函数。</span><span class="sxs-lookup"><span data-stu-id="18d99-132">Select the appropriate aggregate function.</span></span>  
  
6.  <span data-ttu-id="18d99-133">添加搜索条件（如果有的话），以指定要汇总的行子集。</span><span class="sxs-lookup"><span data-stu-id="18d99-133">Add search conditions, if any, to specify the subset of rows you want to summarize.</span></span>  
  
 <span data-ttu-id="18d99-134">当您执行查询时，“结果”窗格将显示指定的聚合。</span><span class="sxs-lookup"><span data-stu-id="18d99-134">When you execute the query, the Results pane displays the aggregations that you specified.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="18d99-135">查询和视图设计器将聚合函数一直作为 SQL 窗格中 SQL 语句的一部分进行维护，直到您显式关闭“分组依据”模式为止。</span><span class="sxs-lookup"><span data-stu-id="18d99-135">The Query and View Designer maintains aggregate functions as part of the SQL statement in the SQL pane until you explicitly turn off Group By mode.</span></span> <span data-ttu-id="18d99-136">因此，如果您通过更改查询类型或更改“关系图”窗格中显示的表或表值对象来修改查询，那么所生成的查询可能包含无效的聚合函数。</span><span class="sxs-lookup"><span data-stu-id="18d99-136">Therefore, if you modify your query by changing its type or by changing which tables or table-valued objects are present in the Diagram pane, the resulting query might include invalid aggregate functions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18d99-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="18d99-137">See Also</span></span>  
 <span data-ttu-id="18d99-138">[对查询结果进行排序和分组 &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="18d99-138">[Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="18d99-139">汇总查询结果 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="18d99-139">Summarize Query Results &#40;Visual Database Tools&#41;</span></span>](summarize-query-results-visual-database-tools.md)  
  
  
