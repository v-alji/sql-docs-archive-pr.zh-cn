---
title: 在同一查询中使用 HAVING 和 WHERE 子句 (Visual Database Tools) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search criteria [SQL Server], excluding rows
- search criteria [SQL Server], WHERE clause
- search conditions [SQL Server], HAVING clause
- row excluded in search [SQL Server]
- search criteria [SQL Server], HAVING clause
- HAVING clause, search criteria
- search conditions [SQL Server], WHERE clause
- WHERE clause, search criteria
- excluding rows
ms.assetid: 1e07cf56-b4b7-4c49-8ddd-c276812a7148
author: stevestein
ms.author: sstein
ms.openlocfilehash: 20f6b471a60bf225ee61bdbbf0ecec30f21a92cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687408"
---
# <a name="use-having-and-where-clauses-in-the-same-query-visual-database-tools"></a><span data-ttu-id="0df92-102">在同一查询中使用 HAVING 和 WHERE 子句 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="0df92-102">Use HAVING and WHERE Clauses in the Same Query (Visual Database Tools)</span></span>
  <span data-ttu-id="0df92-103">在某些情况下，在对整个组应用条件（使用 HAVING 子句）之前，可能希望排除组中的单个行（使用 WHERE 子句）。</span><span class="sxs-lookup"><span data-stu-id="0df92-103">In some instances, you might want to exclude individual rows from groups (using a WHERE clause) before applying a condition to groups as a whole (using a HAVING clause).</span></span>  
  
 <span data-ttu-id="0df92-104">HAVING 子句与 WHERE 子句类似，但仅应用于整个组（即应用于表示组的结果集中的行），而 WHERE 子句应用于单个行。</span><span class="sxs-lookup"><span data-stu-id="0df92-104">A HAVING clause is like a WHERE clause, but applies only to groups as a whole (that is, to the rows in the result set representing groups), whereas the WHERE clause applies to individual rows.</span></span> <span data-ttu-id="0df92-105">查询可同时包含 WHERE 子句和 HAVING 子句。</span><span class="sxs-lookup"><span data-stu-id="0df92-105">A query can contain both a WHERE clause and a HAVING clause.</span></span> <span data-ttu-id="0df92-106">在这种情况下：</span><span class="sxs-lookup"><span data-stu-id="0df92-106">In that case:</span></span>  
  
-   <span data-ttu-id="0df92-107">首先在“关系图”窗格中将 WHERE 子句应用于表或表值对象中的单个行。</span><span class="sxs-lookup"><span data-stu-id="0df92-107">The WHERE clause is applied first to the individual rows in the tables or table-valued objects in the Diagram pane.</span></span> <span data-ttu-id="0df92-108">只对满足 WHERE 子句中的条件的行进行分组。</span><span class="sxs-lookup"><span data-stu-id="0df92-108">Only the rows that meet the conditions in the WHERE clause are grouped.</span></span>  
  
-   <span data-ttu-id="0df92-109">然后将 HAVING 子句应用于结果集中的行。</span><span class="sxs-lookup"><span data-stu-id="0df92-109">The HAVING clause is then applied to the rows in the result set.</span></span> <span data-ttu-id="0df92-110">只有满足 HAVING 条件的组才会显示在查询输出中。</span><span class="sxs-lookup"><span data-stu-id="0df92-110">Only the groups that meet the HAVING conditions appear in the query output.</span></span> <span data-ttu-id="0df92-111">可以将 HAVING 子句仅应用于也同时出现在 GROUP BY 子句或聚合函数中的列。</span><span class="sxs-lookup"><span data-stu-id="0df92-111">You can apply a HAVING clause only to columns that also appear in the GROUP BY clause or in an aggregate function.</span></span>  
  
 <span data-ttu-id="0df92-112">例如，假设您要联接 `titles` 和 `publishers` 表以创建一个查询，显示一组出版商的平均书籍价格。</span><span class="sxs-lookup"><span data-stu-id="0df92-112">For example, imagine that you are joining the `titles` and `publishers` tables to create a query showing the average book price for a set of publishers.</span></span> <span data-ttu-id="0df92-113">想要查看一组特定出版商（也许只是加利福尼亚州的出版商）的平均价格。</span><span class="sxs-lookup"><span data-stu-id="0df92-113">You want to see the average price for only a specific set of publishers - perhaps only the publishers in the state of California.</span></span> <span data-ttu-id="0df92-114">甚至仅希望看到高于 10.00 美元的平均价格。</span><span class="sxs-lookup"><span data-stu-id="0df92-114">And even then, you want to see the average price only if it is over $10.00.</span></span>  
  
 <span data-ttu-id="0df92-115">在计算平均价格前，可通过包含 WHERE 子句建立第一个条件，该条件放弃不属于加利福尼亚的所有出版商。</span><span class="sxs-lookup"><span data-stu-id="0df92-115">You can establish the first condition by including a WHERE clause, which discards any publishers that are not in California, before calculating average prices.</span></span> <span data-ttu-id="0df92-116">第二个条件要求使用 HAVING 子句，因为该条件基于对数据进行分组和汇总的结果。</span><span class="sxs-lookup"><span data-stu-id="0df92-116">The second condition requires a HAVING clause, because the condition is based on the results of grouping and summarizing the data.</span></span> <span data-ttu-id="0df92-117">最终得到的 SQL 语句可能与以下代码类似：</span><span class="sxs-lookup"><span data-stu-id="0df92-117">The resulting SQL statement might look like this:</span></span>  
  
```  
SELECT titles.pub_id, AVG(titles.price)  
FROM titles INNER JOIN publishers  
   ON titles.pub_id = publishers.pub_id  
WHERE publishers.state = 'CA'  
GROUP BY titles.pub_id  
HAVING AVG(price) > 10  
```  
  
 <span data-ttu-id="0df92-118">可以在“条件”窗格中同时创建 HAVING 子句和 WHERE 子句。</span><span class="sxs-lookup"><span data-stu-id="0df92-118">You can create both HAVING and WHERE clauses in the Criteria pane.</span></span> <span data-ttu-id="0df92-119">默认情况下，如果为某个列指定搜索条件，则该条件将成为 HAVING 子句的一部分。</span><span class="sxs-lookup"><span data-stu-id="0df92-119">By default, if you specify a search condition for a column, the condition becomes part of the HAVING clause.</span></span> <span data-ttu-id="0df92-120">但是，您可以将该条件更改为 WHERE 子句。</span><span class="sxs-lookup"><span data-stu-id="0df92-120">However, you can change the condition to be a WHERE clause.</span></span>  
  
 <span data-ttu-id="0df92-121">可以创建涉及同一列的 WHERE 子句和 HAVING 子句。</span><span class="sxs-lookup"><span data-stu-id="0df92-121">You can create a WHERE clause and HAVING clause involving the same column.</span></span> <span data-ttu-id="0df92-122">为此，必须向“条件”窗格添加该列两次，然后将一个实例指定为 HAVING 子句的一部分，并将另一个实例指定为 WHERE 子句的一部分。</span><span class="sxs-lookup"><span data-stu-id="0df92-122">To do so, you must add the column twice to the Criteria pane, then specify one instance as part of the HAVING clause and the other instance as part of the WHERE clause.</span></span>  
  
### <a name="to-specify-a-where-condition-in-an-aggregate-query"></a><span data-ttu-id="0df92-123">在聚合查询中指定 WHERE 条件</span><span class="sxs-lookup"><span data-stu-id="0df92-123">To specify a WHERE condition in an aggregate query</span></span>  
  
1.  <span data-ttu-id="0df92-124">为查询指定组。</span><span class="sxs-lookup"><span data-stu-id="0df92-124">Specify the groups for your query.</span></span> <span data-ttu-id="0df92-125">有关详细信息，请参阅[对查询结果中的行进行分组 (Visual Database Tools)](visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="0df92-125">For details, see [Group Rows in Query Results &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
2.  <span data-ttu-id="0df92-126">如果 WHERE 条件要基于的列不在“条件”窗格中，请添加该列。</span><span class="sxs-lookup"><span data-stu-id="0df92-126">If it is not already in the Criteria pane, add the column on which you want to base the WHERE condition.</span></span>  
  
3.  <span data-ttu-id="0df92-127">除非数据列是 GROUP BY 子句的一部分或包含在聚合函数中，否则请清除“输出”  列。</span><span class="sxs-lookup"><span data-stu-id="0df92-127">Clear the **Output** column unless the data column is part of the GROUP BY clause or included in an aggregate function.</span></span>  
  
4.  <span data-ttu-id="0df92-128">在“筛选器”  列中，指定 WHERE 条件。</span><span class="sxs-lookup"><span data-stu-id="0df92-128">In the **Filter** column, specify the WHERE condition.</span></span> <span data-ttu-id="0df92-129">查询和视图设计器会将该条件添加到 SQL 语句的 HAVING 子句中。</span><span class="sxs-lookup"><span data-stu-id="0df92-129">The Query and View Designer adds the condition to the HAVING clause of the SQL statement.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0df92-130">此过程的示例中显示的查询将联接 `titles` 和 `publishers`这两张表。</span><span class="sxs-lookup"><span data-stu-id="0df92-130">The query shown in the example for this procedure joins two tables, `titles` and `publishers`.</span></span>  
  
     <span data-ttu-id="0df92-131">此时在查询中，SQL 语句包含一个 HAVING 子句：</span><span class="sxs-lookup"><span data-stu-id="0df92-131">At this point in the query, the SQL statement contains a HAVING clause:</span></span>  
  
    ```  
    SELECT titles.pub_id, AVG(titles.price)  
    FROM titles INNER JOIN publishers   
       ON titles.pub_id = publishers.pub_id  
    GROUP BY titles.pub_id  
    HAVING publishers.state = 'CA'  
    ```  
  
5.  <span data-ttu-id="0df92-132">在“分组依据”  列中，从组和汇总选项的列表中选择 **Where**。</span><span class="sxs-lookup"><span data-stu-id="0df92-132">In the **Group By** column, select **Where** from the list of group and summary options.</span></span> <span data-ttu-id="0df92-133">查询和视图设计器将从 SQL 语句的 HAVING 子句中移除该条件，并将其添加到 WHERE 子句中。</span><span class="sxs-lookup"><span data-stu-id="0df92-133">The Query and View Designer removes the condition from the HAVING clause in the SQL statement and adds it to the WHERE clause.</span></span>  
  
     <span data-ttu-id="0df92-134">SQL 语句更改为包含 WHERE 子句：</span><span class="sxs-lookup"><span data-stu-id="0df92-134">The SQL statement changes to include a WHERE clause instead:</span></span>  
  
    ```  
    SELECT titles.pub_id, AVG(titles.price)  
    FROM titles INNER JOIN publishers   
       ON titles.pub_id = publishers.pub_id  
    WHERE publishers.state = 'CA'  
    GROUP BY titles.pub_id  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="0df92-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0df92-135">See Also</span></span>  
 <span data-ttu-id="0df92-136">[对查询结果进行排序和分组 &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="0df92-136">[Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="0df92-137">汇总查询结果 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="0df92-137">Summarize Query Results &#40;Visual Database Tools&#41;</span></span>](summarize-query-results-visual-database-tools.md)  
  
  
