---
title: MSSQLSERVER_207 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 207 (Database Engine error)
ms.assetid: d1ab00c7-0331-437a-84fe-bae53b82feec
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bd6044c08ecd5a73f539bfbc1139d6257c2db9d3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688931"
---
# <a name="mssqlserver_207"></a><span data-ttu-id="c05dd-102">MSSQLSERVER_207</span><span class="sxs-lookup"><span data-stu-id="c05dd-102">MSSQLSERVER_207</span></span>
    
## <a name="details"></a><span data-ttu-id="c05dd-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="c05dd-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c05dd-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="c05dd-104">Product Name</span></span>|<span data-ttu-id="c05dd-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="c05dd-105">SQL Server</span></span>|  
|<span data-ttu-id="c05dd-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="c05dd-106">Event ID</span></span>|<span data-ttu-id="c05dd-107">207</span><span class="sxs-lookup"><span data-stu-id="c05dd-107">207</span></span>|  
|<span data-ttu-id="c05dd-108">事件源</span><span class="sxs-lookup"><span data-stu-id="c05dd-108">Event Source</span></span>|<span data-ttu-id="c05dd-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="c05dd-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="c05dd-110">组件</span><span class="sxs-lookup"><span data-stu-id="c05dd-110">Component</span></span>|<span data-ttu-id="c05dd-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="c05dd-111">SQLEngine</span></span>|  
|<span data-ttu-id="c05dd-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="c05dd-112">Symbolic Name</span></span>|<span data-ttu-id="c05dd-113">SQ_BADCOL</span><span class="sxs-lookup"><span data-stu-id="c05dd-113">SQ_BADCOL</span></span>|  
|<span data-ttu-id="c05dd-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="c05dd-114">Message Text</span></span>|<span data-ttu-id="c05dd-115">列名“%.\*ls”无效。</span><span class="sxs-lookup"><span data-stu-id="c05dd-115">Invalid column name '%.\*ls'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c05dd-116">说明</span><span class="sxs-lookup"><span data-stu-id="c05dd-116">Explanation</span></span>  
 <span data-ttu-id="c05dd-117">此查询错误可能是由以下问题之一导致的：</span><span class="sxs-lookup"><span data-stu-id="c05dd-117">This query error can be caused by one of the following problems.</span></span>  
  
-   <span data-ttu-id="c05dd-118">列名称拼写错误，或任一指定的表中不存在该列。</span><span class="sxs-lookup"><span data-stu-id="c05dd-118">The column name is misspelled or the column does not exist in any of the specified tables.</span></span>  
  
-   <span data-ttu-id="c05dd-119">数据库的排序规则区分大小写，在查询中指定的列名与表中所定义的列名的大小写不同。</span><span class="sxs-lookup"><span data-stu-id="c05dd-119">The collation of the database is case-sensitive and the case of the column name specified in the query does not match the case of the column defined in the table.</span></span> <span data-ttu-id="c05dd-120">例如，如果将某列在表中定义为 **LastName** 而且数据库使用区分大小写的排序规则，那么，以 **Lastname** 或 **lastname** 形式引用该列的查询将因列名不匹配而导致返回错误 207。</span><span class="sxs-lookup"><span data-stu-id="c05dd-120">For example, when a column is defined in a table as **LastName** and the database uses a case-sensitive collation, queries that refer to the column as **Lastname** or **lastname** will cause error 207 to return because the column name does not match.</span></span>  
  
-   <span data-ttu-id="c05dd-121">在 SELECT 子句中定义的列别名在另一个如 WHERE 或 GROUP BY 之类的子句中被引用。</span><span class="sxs-lookup"><span data-stu-id="c05dd-121">A column alias, defined in the SELECT clause, is referenced in another clause such as a WHERE or GROUP BY clause.</span></span> <span data-ttu-id="c05dd-122">例如，以下查询在 SELECT 子句中定义列别名 `Year`，并在 GROUP BY 子句中将其引用。</span><span class="sxs-lookup"><span data-stu-id="c05dd-122">For example, the following query defines the column alias `Year` in the SELECT clause and refers to it in the GROUP BY clause.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT DATEPART(yyyy,OrderDate) AS Year, SUM(TotalDue) AS Total  
    FROM Sales.SalesOrderHeader  
    GROUP BY Year;  
    ```  
  
     <span data-ttu-id="c05dd-123">由于查询子句逻辑上处理的顺序，该示例返回错误 207。</span><span class="sxs-lookup"><span data-stu-id="c05dd-123">Due to the order in which query clauses are logically processed, the example returns error 207.</span></span> <span data-ttu-id="c05dd-124">处理顺序如下所示：</span><span class="sxs-lookup"><span data-stu-id="c05dd-124">The processing order is as follows:</span></span>  
  
    1.  <span data-ttu-id="c05dd-125">FROM</span><span class="sxs-lookup"><span data-stu-id="c05dd-125">FROM</span></span>  
  
    2.  <span data-ttu-id="c05dd-126">ON</span><span class="sxs-lookup"><span data-stu-id="c05dd-126">ON</span></span>  
  
    3.  <span data-ttu-id="c05dd-127">JOIN</span><span class="sxs-lookup"><span data-stu-id="c05dd-127">JOIN</span></span>  
  
    4.  <span data-ttu-id="c05dd-128">WHERE</span><span class="sxs-lookup"><span data-stu-id="c05dd-128">WHERE</span></span>  
  
    5.  <span data-ttu-id="c05dd-129">GROUP BY</span><span class="sxs-lookup"><span data-stu-id="c05dd-129">GROUP BY</span></span>  
  
    6.  <span data-ttu-id="c05dd-130">WITH CUBE 或 WITH ROLLUP</span><span class="sxs-lookup"><span data-stu-id="c05dd-130">WITH CUBE or WITH ROLLUP</span></span>  
  
    7.  <span data-ttu-id="c05dd-131">HAVING</span><span class="sxs-lookup"><span data-stu-id="c05dd-131">HAVING</span></span>  
  
    8.  <span data-ttu-id="c05dd-132">SELECT</span><span class="sxs-lookup"><span data-stu-id="c05dd-132">SELECT</span></span>  
  
    9. <span data-ttu-id="c05dd-133">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="c05dd-133">DISTINCT</span></span>  
  
    10. <span data-ttu-id="c05dd-134">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="c05dd-134">ORDER BY</span></span>  
  
    11. <span data-ttu-id="c05dd-135">TOP</span><span class="sxs-lookup"><span data-stu-id="c05dd-135">TOP</span></span>  
  
     <span data-ttu-id="c05dd-136">因为列别名是在处理 SELECT 子句后定义的，所以当处理 GROUP BY 子句时列别名是未知的。</span><span class="sxs-lookup"><span data-stu-id="c05dd-136">Because a column alias is not defined until the SELECT clause is processed, the alias name is unknown when the GROUP BY clause is processed.</span></span>  
  
-   <span data-ttu-id="c05dd-137">当 *<merge_matched>* 子句引用源表中的列，但该源表在 WHEN NOT MATCHED BY SOURCE 子句中未返回任何行时，MERGE 语句将引发此错误。</span><span class="sxs-lookup"><span data-stu-id="c05dd-137">The MERGE statement raises this error when the *<merge_matched>* clause references columns in the source table but no rows are returned by the source table in the WHEN NOT MATCHED BY SOURCE clause.</span></span> <span data-ttu-id="c05dd-138">该错误的发生是因为当未返回任何行到查询中时源表中的列不能被访问。</span><span class="sxs-lookup"><span data-stu-id="c05dd-138">The error occurs because the columns in the source table cannot be accessed when no rows are returned to the query.</span></span> <span data-ttu-id="c05dd-139">例如，如果无法访问源表中的 `WHEN NOT MATCHED BY SOURCE THEN UPDATE SET TargetTable.Col1 = SourceTable.Col1`，`Col1` 子句可能导致该语句失败。</span><span class="sxs-lookup"><span data-stu-id="c05dd-139">For example, the clause `WHEN NOT MATCHED BY SOURCE THEN UPDATE SET TargetTable.Col1 = SourceTable.Col1` may cause the statement to fail if `Col1` in the source table is inaccessible.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c05dd-140">用户操作</span><span class="sxs-lookup"><span data-stu-id="c05dd-140">User Action</span></span>  
 <span data-ttu-id="c05dd-141">查看以下信息并根据需要更正该语句。</span><span class="sxs-lookup"><span data-stu-id="c05dd-141">Verify the following information and correct the statement as appropriate.</span></span>  
  
-   <span data-ttu-id="c05dd-142">表中存在此列名且该列名拼写正确。</span><span class="sxs-lookup"><span data-stu-id="c05dd-142">The column name exists in the table and is spelled correctly.</span></span> <span data-ttu-id="c05dd-143">下面的示例查询 **sys.columns** 目录视图以返回给定表的所有列名称。</span><span class="sxs-lookup"><span data-stu-id="c05dd-143">The following example queries the **sys.columns** catalog view to return all column names for a given table.</span></span>  
  
    ```  
    SELECT name FROM sys.columns WHERE object_id = OBJECT_ID('schema_name.table_name');  
    ```  
  
-   <span data-ttu-id="c05dd-144">数据库排序规则区分大小写。</span><span class="sxs-lookup"><span data-stu-id="c05dd-144">The case sensitivity of the database collation.</span></span> <span data-ttu-id="c05dd-145">以下语句返回指定数据库的排序规则。</span><span class="sxs-lookup"><span data-stu-id="c05dd-145">The following statement returns the collation of the specified database.</span></span>  
  
    ```  
    SELECT collation_name FROM sys.databases WHERE name = 'database_name';  
    ```  
  
     <span data-ttu-id="c05dd-146">排序规则名称中的缩写 CS 指示排序规则区分大小写。</span><span class="sxs-lookup"><span data-stu-id="c05dd-146">The abbreviation CS in the collation name indicates the collation is case-sensitive.</span></span> <span data-ttu-id="c05dd-147">例如，Latin1_General_CS_AS 是一个区分大小写和重音符号的排序规则。</span><span class="sxs-lookup"><span data-stu-id="c05dd-147">For example, Latin1_General_CS_AS is a case-sensitive and accent-sensitive collation.</span></span> <span data-ttu-id="c05dd-148">更改列名使之与表中定义的列名的大小写相同。</span><span class="sxs-lookup"><span data-stu-id="c05dd-148">Modify the column name to match the case of the column name as it is defined in the table.</span></span>  
  
-   <span data-ttu-id="c05dd-149">列别名引用不正确。</span><span class="sxs-lookup"><span data-stu-id="c05dd-149">A column alias is referenced incorrectly.</span></span> <span data-ttu-id="c05dd-150">通过重复在相应子句中定义别名的表达式或通过使用派生表，对语句进行更改。</span><span class="sxs-lookup"><span data-stu-id="c05dd-150">Modify the statement by repeating the expression that defines the alias in the appropriate clause or by using a derived table.</span></span> <span data-ttu-id="c05dd-151">下面的示例重复在 GROUP BY 子句中定义 `Year` 别名的表达式。</span><span class="sxs-lookup"><span data-stu-id="c05dd-151">The following example repeats the expressions that define the `Year` alias in the GROUP BY clause.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT DATEPART(yyyy,OrderDate) AS Year ,SUM(TotalDue) AS Total  
    FROM Sales.SalesOrderHeader  
    GROUP BY DATEPART(yyyy,OrderDate);  
    ```  
  
     <span data-ttu-id="c05dd-152">以下示例使用派生表使得别名可用于查询中的其他子句。</span><span class="sxs-lookup"><span data-stu-id="c05dd-152">The following example uses a derived table to make the alias name available to other clauses in the query.</span></span> <span data-ttu-id="c05dd-153">请注意，`Year` 别名是在首先处理的 FROM 子句中定义的，所以可以在查询中的其他子句中使用该别名。</span><span class="sxs-lookup"><span data-stu-id="c05dd-153">Notice that the alias `Year` is defined in the FROM clause, which is processed first, and so makes the alias available for use in other clauses in the query.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT d.Year, SUM(TotalDue) AS Total  
    FROM (SELECT DATEPART(yyyy,OrderDate) AS Year, TotalDue  
          FROM Sales.SalesOrderHeader)AS d  
    GROUP BY Year;  
    ```  
  
-   <span data-ttu-id="c05dd-154">MERGE 语句中的 WHEN NOT MATCHED BY SOURCE 子句引用的是可以访问的值。</span><span class="sxs-lookup"><span data-stu-id="c05dd-154">The WHEN NOT MATCHED BY SOURCE clause in the MERGE statement refers to a value that can be accessed.</span></span> <span data-ttu-id="c05dd-155">修改 MERGE 语句，使源表至少在 WHEN NOT MATCHED BY SOURCE 子句中返回一行。</span><span class="sxs-lookup"><span data-stu-id="c05dd-155">Modify the MERGE statement so that at least one row is returned by the source table in the WHEN NOT MATCHED BY SOURCE clause.</span></span> <span data-ttu-id="c05dd-156">例如，您可能需要添加或修订为子句指定的搜索条件。</span><span class="sxs-lookup"><span data-stu-id="c05dd-156">For example, you might need to add or revise the search condition specified for the clause.</span></span> <span data-ttu-id="c05dd-157">或者，也可以更改该子句以指定没有引用源表的值。</span><span class="sxs-lookup"><span data-stu-id="c05dd-157">Alternatively, you can modify the clause to specify a value that does not reference the source table.</span></span> <span data-ttu-id="c05dd-158">例如，`WHEN NOT MATCHED BY SOURCE THEN UPDATE SET TargetTable.Col1 = <expression, or other available value>`。</span><span class="sxs-lookup"><span data-stu-id="c05dd-158">For example, `WHEN NOT MATCHED BY SOURCE THEN UPDATE SET TargetTable.Col1 = <expression, or other available value>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c05dd-159">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c05dd-159">See Also</span></span>  
 <span data-ttu-id="c05dd-160">[MERGE (Transact-SQL)](/sql/t-sql/statements/merge-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c05dd-160">[MERGE &#40;Transact-SQL&#41;](/sql/t-sql/statements/merge-transact-sql) </span></span>  
 <span data-ttu-id="c05dd-161">[FROM (Transact-SQL)](/sql/t-sql/queries/from-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c05dd-161">[FROM &#40;Transact-SQL&#41;](/sql/t-sql/queries/from-transact-sql) </span></span>  
 <span data-ttu-id="c05dd-162">[SELECT (Transact-SQL)](/sql/t-sql/queries/select-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c05dd-162">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span></span>  
 [<span data-ttu-id="c05dd-163">UPDATE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="c05dd-163">UPDATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/update-transact-sql)  
  
  
