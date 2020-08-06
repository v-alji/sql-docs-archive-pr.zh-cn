---
title: 使用表 (Visual Database Tools) 创建查询 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- user-defined functions [SQL Server], queries
- queries [SQL Server], creating
ms.assetid: 8e4a1f0a-8a42-4733-be8d-e21d6dbddb33
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0444c20fe10080949930f23623d5699f7fd3712c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577194"
---
# <a name="create-queries-using-something-besides-a-table-visual-database-tools"></a><span data-ttu-id="1933d-102">使用表以外的对象创建查询 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="1933d-102">Create Queries using Something Besides a Table (Visual Database Tools)</span></span>
  <span data-ttu-id="1933d-103">每次编写检索查询时，必须明确说明所需的列和行以及查询处理器应从何处查找原始数据。</span><span class="sxs-lookup"><span data-stu-id="1933d-103">Whenever you write a retrieval query, you articulate what columns you want, what rows you want, and where the query processor should find the original data.</span></span> <span data-ttu-id="1933d-104">一般情况下，此类原始数据由一个表或几个联接在一起的表组成。</span><span class="sxs-lookup"><span data-stu-id="1933d-104">Typically, this original data consists of a table or several tables joined together.</span></span> <span data-ttu-id="1933d-105">不过，原始数据也可以来自表以外的源。</span><span class="sxs-lookup"><span data-stu-id="1933d-105">But the original data can come from sources other than tables.</span></span> <span data-ttu-id="1933d-106">事实上，它可以来自视图、查询、同义词或可返回表的用户定义函数。</span><span class="sxs-lookup"><span data-stu-id="1933d-106">In fact, it can come from views, queries, synonyms, or user-defined functions that return a table.</span></span>  
  
## <a name="using-a-view-in-place-of-a-table"></a><span data-ttu-id="1933d-107">使用视图代替表</span><span class="sxs-lookup"><span data-stu-id="1933d-107">Using a View in Place of a Table</span></span>  
 <span data-ttu-id="1933d-108">您可以从视图选择行。</span><span class="sxs-lookup"><span data-stu-id="1933d-108">You can select rows from a view.</span></span> <span data-ttu-id="1933d-109">例如，假设数据库包含一个名为“ExpensiveBooks”的视图，在该视图中，每行描述一个价格超过 19.99 美元的书名。</span><span class="sxs-lookup"><span data-stu-id="1933d-109">For example, suppose the database includes a view called "ExpensiveBooks," in which each row describes a title whose price exceeds 19.99.</span></span> <span data-ttu-id="1933d-110">视图定义可能类似以下形式：</span><span class="sxs-lookup"><span data-stu-id="1933d-110">The view definition might look like this:</span></span>  
  
```  
SELECT *  
FROM titles  
WHERE price > 19.99  
  
```  
  
 <span data-ttu-id="1933d-111">这样，只需从 ExpensiveBooks 视图中选择心理学书籍，就可以选择较贵的心理学书籍。</span><span class="sxs-lookup"><span data-stu-id="1933d-111">You can select the expensive psychology books merely by selecting the psychology books from the ExpensiveBooks view.</span></span> <span data-ttu-id="1933d-112">生成的 SQL 结果可能类似以下形式：</span><span class="sxs-lookup"><span data-stu-id="1933d-112">The resulting SQL might look like this:</span></span>  
  
```  
SELECT *  
FROM ExpensiveBooks  
WHERE type = 'psychology'  
  
```  
  
 <span data-ttu-id="1933d-113">同样，视图也可以参与 JOIN 操作。</span><span class="sxs-lookup"><span data-stu-id="1933d-113">Similarly, a view can participate in a JOIN operation.</span></span> <span data-ttu-id="1933d-114">例如，只需将 sales 表联接到 ExpensiveBooks 视图，就可以查找较贵的书籍的销售额。</span><span class="sxs-lookup"><span data-stu-id="1933d-114">For example, you can find the sales of expensive books merely by joining the sales table to the ExpensiveBooks view.</span></span> <span data-ttu-id="1933d-115">生成的 SQL 结果可能类似以下形式：</span><span class="sxs-lookup"><span data-stu-id="1933d-115">The resulting SQL might look like this:</span></span>  
  
```  
SELECT *  
FROM sales   
         INNER JOIN   
         ExpensiveBooks   
         ON sales.title_id   
         =  ExpensiveBooks.title_id  
  
```  
  
 <span data-ttu-id="1933d-116">有关向查询添加视图的详细信息，请参阅[向查询中添加表 (Visual Database Tools)](visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="1933d-116">For more information about adding a view to a query, see [Add Tables to Queries &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
## <a name="using-a-query-in-place-of-a-table"></a><span data-ttu-id="1933d-117">使用查询代替表</span><span class="sxs-lookup"><span data-stu-id="1933d-117">Using a Query in Place of a Table</span></span>  
 <span data-ttu-id="1933d-118">您可以从查询选择行。</span><span class="sxs-lookup"><span data-stu-id="1933d-118">You can select rows from a query.</span></span> <span data-ttu-id="1933d-119">例如，假设已编写了一个查询，用于检索合著书籍（有一个以上作者的书）的书名和标识符。</span><span class="sxs-lookup"><span data-stu-id="1933d-119">For example, suppose you have already written a query retrieving titles and identifiers of the coauthored books - the books with more than one author.</span></span> <span data-ttu-id="1933d-120">该 SQL 可能类似以下形式：</span><span class="sxs-lookup"><span data-stu-id="1933d-120">The SQL might look like this:</span></span>  
  
```  
SELECT   
     titles.title_id, title, type  
FROM   
     titleauthor   
         INNER JOIN  
         titles   
         ON titleauthor.title_id   
         =  titles.title_id   
GROUP BY   
     titles.title_id, title, type  
HAVING COUNT(*) > 1  
  
```  
  
 <span data-ttu-id="1933d-121">您随后可以编写另一个基于此结果的查询。</span><span class="sxs-lookup"><span data-stu-id="1933d-121">You can then write another query that builds on this result.</span></span> <span data-ttu-id="1933d-122">例如，您可以编写一个检索合著的心理学书籍的查询。</span><span class="sxs-lookup"><span data-stu-id="1933d-122">For example, you can write a query that retrieves the coauthored psychology books.</span></span> <span data-ttu-id="1933d-123">若要编写这个新查询，则可以将现有查询用作这个新查询的数据源。</span><span class="sxs-lookup"><span data-stu-id="1933d-123">To write this new query, you can use the existing query as the source of the new query's data.</span></span> <span data-ttu-id="1933d-124">生成的 SQL 结果可能类似以下形式：</span><span class="sxs-lookup"><span data-stu-id="1933d-124">The resulting SQL might look like this:</span></span>  
  
```  
SELECT   
    title  
FROM   
    (  
    SELECT   
        titles.title_id,   
        title,   
        type  
    FROM   
        titleauthor   
            INNER JOIN  
            titles   
            ON titleauthor.title_id   
            =  titles.title_id   
    GROUP BY   
        titles.title_id,   
        title,   
        type  
    HAVING COUNT(*) > 1  
    )   
    co_authored_books  
WHERE     type = 'psychology'  
  
```  
  
 <span data-ttu-id="1933d-125">加粗的文本表示用作新查询的数据源的现有查询。</span><span class="sxs-lookup"><span data-stu-id="1933d-125">The emphasized text shows the existing query used as the source of the new query's data.</span></span> <span data-ttu-id="1933d-126">请注意，新查询使用了现有查询的别名（“co_authored_books”）。</span><span class="sxs-lookup"><span data-stu-id="1933d-126">Note that the new query uses an alias ("co_authored_books") for the existing query.</span></span> <span data-ttu-id="1933d-127">有关别名的详细信息，请参阅[创建表别名 (Visual Database Tools)](create-table-aliases-visual-database-tools.md) 和[创建列别名 (Visual Database Tools)](create-column-aliases-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="1933d-127">For more information about aliases, see [Create Table Aliases &#40;Visual Database Tools&#41;](create-table-aliases-visual-database-tools.md) and [Create Column Aliases &#40;Visual Database Tools&#41;](create-column-aliases-visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="1933d-128">同样，查询也可以参与 JOIN 操作。</span><span class="sxs-lookup"><span data-stu-id="1933d-128">Similarly, a query can participate in a JOIN operation.</span></span> <span data-ttu-id="1933d-129">例如，只需将 ExpensiveBooks 视图联接到检索合著书籍的查询，就可以查找较贵的合著书籍的销售额。</span><span class="sxs-lookup"><span data-stu-id="1933d-129">For example, you can find the sales of expensive coauthored books merely by joining the ExpensiveBooks view to the query retrieving the coauthored books.</span></span> <span data-ttu-id="1933d-130">生成的 SQL 结果可能类似以下形式：</span><span class="sxs-lookup"><span data-stu-id="1933d-130">The resulting SQL might look like this:</span></span>  
  
```  
SELECT   
    ExpensiveBooks.title  
FROM   
    ExpensiveBooks   
        INNER JOIN  
        (  
        SELECT   
            titles.title_id,   
            title,   
            type  
        FROM   
            titleauthor   
                INNER JOIN  
                titles   
                ON titleauthor.title_id   
                =  titles.title_id   
        GROUP BY   
            titles.title_id,   
            title,   
            type  
        HAVING COUNT(*) > 1  
        )  
```  
  
 <span data-ttu-id="1933d-131">有关向查询添加查询的详细信息，请参阅[向查询中添加表 (Visual Database Tools)](visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="1933d-131">For more information about adding a query to a query, see [Add Tables to Queries &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
## <a name="using-a-user-defined-function-in-place-of-a-table"></a><span data-ttu-id="1933d-132">使用用户定义函数代替表</span><span class="sxs-lookup"><span data-stu-id="1933d-132">Using a User-Defined Function in Place of a Table</span></span>  
 <span data-ttu-id="1933d-133">在 SQL Server 2000 或更高版本中，可以创建返回表的用户定义函数。</span><span class="sxs-lookup"><span data-stu-id="1933d-133">In SQL Server 2000 or higher, you can create a user-defined function that returns a table.</span></span> <span data-ttu-id="1933d-134">此类函数对执行复杂逻辑操作或逐步逻辑操作很有用。</span><span class="sxs-lookup"><span data-stu-id="1933d-134">Such functions are useful for performing complex or procedural logic.</span></span>  
  
 <span data-ttu-id="1933d-135">例如，假设 employee 表包含一个附加列 employee.manager_emp_id，且存在从 manager_emp_id 到 employee.emp_id 的外键。</span><span class="sxs-lookup"><span data-stu-id="1933d-135">For example, suppose the employee table contains an additional column, employee.manager_emp_id, and that a foreign key exists from manager_emp_id to employee.emp_id.</span></span> <span data-ttu-id="1933d-136">在 employee 表的每个行中，在 manager_emp_id 列显示该雇员的老板。</span><span class="sxs-lookup"><span data-stu-id="1933d-136">Within each row of the employee table, the manager_emp_id column indicates the employee's boss.</span></span> <span data-ttu-id="1933d-137">更确切地说，它显示该雇员的老板的 emp_id。</span><span class="sxs-lookup"><span data-stu-id="1933d-137">More precisely, it indicates the employee's boss's emp_id.</span></span> <span data-ttu-id="1933d-138">您可以创建用户定义函数以返回这样的表：在某个特定高级经理的所辖部门层次结构中工作的每个雇员在该表中各占一行。</span><span class="sxs-lookup"><span data-stu-id="1933d-138">You can create a user-defined function that returns a table containing one row for each employee working within a particular high-level manager's organizational hierarchy.</span></span> <span data-ttu-id="1933d-139">可以调用函数 fn_GetWholeTeam，并对其进行设计以获得输入变量（待检索部门的经理的 emp_id）。</span><span class="sxs-lookup"><span data-stu-id="1933d-139">You might call the function fn_GetWholeTeam, and design it to take an input variable - the emp_id of the manager whose team you want to retrieve.</span></span>  
  
 <span data-ttu-id="1933d-140">随后可以编写将 fn_GetWholeTeam 函数用作数据源的查询。</span><span class="sxs-lookup"><span data-stu-id="1933d-140">You can write a query that uses the fn_GetWholeTeam function as a source of data.</span></span> <span data-ttu-id="1933d-141">生成的 SQL 结果可能类似以下形式：</span><span class="sxs-lookup"><span data-stu-id="1933d-141">The resulting SQL might look like this:</span></span>  
  
```  
SELECT *   
FROM   
     fn_GetWholeTeam ('VPA30890F')  
  
```  
  
 <span data-ttu-id="1933d-142">“VPA30890F”是待检索部门的经理的 emp_id。</span><span class="sxs-lookup"><span data-stu-id="1933d-142">"VPA30890F" is the emp_id of the manager whose organization you want to retrieve.</span></span> <span data-ttu-id="1933d-143">有关向查询添加用户定义函数的详细信息，请参阅[向查询中添加表 (Visual Database Tools)](visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="1933d-143">For more information about adding a user-defined function to a query, see [Add Tables to Queries &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span> <span data-ttu-id="1933d-144">有关用户定义函数的完整说明，请参阅 [用户定义函数](../../relational-databases/user-defined-functions/user-defined-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="1933d-144">For a complete description of user-defined functions, see [User-Defined Functions](../../relational-databases/user-defined-functions/user-defined-functions.md).</span></span>  
  
  
