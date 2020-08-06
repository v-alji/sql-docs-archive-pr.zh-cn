---
title: 在 "条件" 窗格中组合搜索条件的约定 (Visual Database Tools) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search conditions [SQL Server], combining
- precedence [SQL Server], Criteria pane
- search criteria [SQL Server], combining conditions
- multiple OR clauses
- combining search conditions
- OR operator
- AND, Criteria pane
- multiple AND clauses
ms.assetid: d4859be5-ff5b-48b2-a101-ad40c6dbcc68
author: stevestein
ms.author: sstein
ms.openlocfilehash: 684521baa87d5325366a0e18296cd35342a0e947
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682613"
---
# <a name="conventions-for-combining-search-conditions-in-the-criteria-pane-visual-database-tools"></a><span data-ttu-id="e7614-102">在“条件”窗格中组合搜索条件的约定 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="e7614-102">Conventions for Combining Search Conditions in the Criteria Pane (Visual Database Tools)</span></span>
  <span data-ttu-id="e7614-103">您可以创建包含用任意多个 AND 和 OR 运算符链接的任意多个搜索条件的查询。</span><span class="sxs-lookup"><span data-stu-id="e7614-103">You can create queries that include any number of search conditions, linked with any number of AND and OR operators.</span></span> <span data-ttu-id="e7614-104">具有 AND 和 OR 子句组合的查询会变得非常复杂。因此，了解在执行此类查询时如何对其进行解释，以及在[“条件”窗格](visual-database-tools.md)和 [SQL 窗格](sql-pane-visual-database-tools.md)中如何表示此类查询，是非常有用的。</span><span class="sxs-lookup"><span data-stu-id="e7614-104">A query with a combination of AND and OR clauses can become complex, so it is helpful to understand how such a query is interpreted when you execute it, and how such a query is represented in the [Criteria Pane](visual-database-tools.md) and [SQL Pane](sql-pane-visual-database-tools.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e7614-105">有关仅包含一个 AND 或 OR 运算符的搜索条件的详细信息，请参阅[为同一列指定多个搜索条件 (Visual Database Tools)](specify-multiple-search-conditions-for-one-column-visual-database-tools.md) 和 [为多个列指定多个搜索条件 (Visual Database Tools)](specify-multiple-search-conditions-for-multiple-columns-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="e7614-105">For details about search conditions that contain only one AND or OR operator, see [Specify Multiple Search Conditions for One Column &#40;Visual Database Tools&#41;](specify-multiple-search-conditions-for-one-column-visual-database-tools.md) and [Specify Multiple Search Conditions for Multiple Columns &#40;Visual Database Tools&#41;](specify-multiple-search-conditions-for-multiple-columns-visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="e7614-106">在本文稍后部分中，您将了解以下相关信息：</span><span class="sxs-lookup"><span data-stu-id="e7614-106">Below you will find information about:</span></span>  
  
-   <span data-ttu-id="e7614-107">在包含 AND 和 OR 的查询中，AND 和 OR 的优先级。</span><span class="sxs-lookup"><span data-stu-id="e7614-107">The precedence of AND and OR in queries that contain both.</span></span>  
  
-   <span data-ttu-id="e7614-108">AND 和 OR 子句中的条件在逻辑上如何相关。</span><span class="sxs-lookup"><span data-stu-id="e7614-108">How the conditions in AND and OR clauses relate logically to one another.</span></span>  
  
-   <span data-ttu-id="e7614-109">查询和视图设计器在“条件”窗格中如何表示同时包含 AND 和 OR 的查询。</span><span class="sxs-lookup"><span data-stu-id="e7614-109">How the Query and View Designer represents in the Criteria Pane queries that contain both AND and OR.</span></span>  
  
 <span data-ttu-id="e7614-110">为帮助理解下面的讨论内容，本文假设您正使用包含 `employee` 、 `hire_date`和 `job_lvl`列的 `status`表。</span><span class="sxs-lookup"><span data-stu-id="e7614-110">To help you understand the discussion below, imagine that you are working with an `employee` table containing the columns `hire_date`, `job_lvl`, and `status`.</span></span> <span data-ttu-id="e7614-111">这些示例假设您需要知道如下信息：雇员在公司工作了多长时间（即雇员的雇佣日期），雇员承担何种工作（职位等级是什么），以及雇员的状况（例如，是否已退休）。</span><span class="sxs-lookup"><span data-stu-id="e7614-111">The examples assume that you need to know information such as how long an employee has worked with the company (that is, what the employee's hire date is), what type of job the employee performs (what the job level is), and the employee's status (for example, retired).</span></span>  
  
## <a name="precedence-of-and-and-or"></a><span data-ttu-id="e7614-112">AND 和 OR 的优先级</span><span class="sxs-lookup"><span data-stu-id="e7614-112">Precedence of AND and OR</span></span>  
 <span data-ttu-id="e7614-113">当执行查询时，它首先计算与 AND 链接的子句，然后计算与 OR 链接的子句。</span><span class="sxs-lookup"><span data-stu-id="e7614-113">When a query is executed, it evaluates first the clauses linked with AND, and then those linked with OR.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e7614-114">NOT 运算符的优先级高于 AND 和 OR 运算符。</span><span class="sxs-lookup"><span data-stu-id="e7614-114">The NOT operator takes precedence over both AND and OR.</span></span>  
  
 <span data-ttu-id="e7614-115">例如，若要查找在公司工作五年以上的低级职位雇员，或者查找中级职位的雇员而不考虑他们的雇佣日期，可构造如下的 WHERE 子句：</span><span class="sxs-lookup"><span data-stu-id="e7614-115">For example, to find either employees who have been with the company for more than five years in lower-level jobs or employees with middle-level jobs without regard for their hire date, you can construct a WHERE clause such as the following:</span></span>  
  
```  
WHERE   
   hire_date < '01/01/95' AND   
   job_lvl = 100 OR  
   job_lvl = 200  
  
```  
  
 <span data-ttu-id="e7614-116">若要改变 AND 高于 OR 的默认优先级，可在 SQL 窗格中将特定的条件用圆括号括起来。</span><span class="sxs-lookup"><span data-stu-id="e7614-116">To override the default precedence of AND over OR, you can put parentheses around specific conditions in the SQL pane.</span></span> <span data-ttu-id="e7614-117">括号里的条件始终先进行计算。</span><span class="sxs-lookup"><span data-stu-id="e7614-117">Conditions in parentheses are always evaluated first.</span></span> <span data-ttu-id="e7614-118">例如，若要查找在公司工作五年以上的低级职位或中级职位的所有雇员，可构造如下的 WHERE 子句：</span><span class="sxs-lookup"><span data-stu-id="e7614-118">For example, to find all employees who have been with the company more than five years in either lower or middle-level jobs, you can construct a WHERE clause such as the following:</span></span>  
  
```  
WHERE   
   hire_date < '01/01/95' AND   
   (job_lvl = 100 OR job_lvl = 200)  
```  
  
> [!TIP]  
>  <span data-ttu-id="e7614-119">为清楚起见，建议在组合 AND 和 OR 子句时始终使用圆括号，而不要依赖默认的优先级。</span><span class="sxs-lookup"><span data-stu-id="e7614-119">It is recommended that, for clarity, you always include parentheses when combining AND and OR clauses instead of relying on the default precedence.</span></span>  
  
## <a name="how-and-works-with-multiple-or-clauses"></a><span data-ttu-id="e7614-120">AND 如何与多个 OR 子句一起使用</span><span class="sxs-lookup"><span data-stu-id="e7614-120">How AND Works with Multiple OR Clauses</span></span>  
 <span data-ttu-id="e7614-121">了解组合 AND 和 OR 子句时它们的相关方式有助于构造和理解查询和视图设计器中的复杂查询。</span><span class="sxs-lookup"><span data-stu-id="e7614-121">Understanding how AND and OR clauses are related when combined can help you construct and understand complex queries in the Query and View Designer.</span></span>  
  
 <span data-ttu-id="e7614-122">如果使用 AND 链接多个条件，则与 AND 链接的第一组条件适用于第二组的所有条件。</span><span class="sxs-lookup"><span data-stu-id="e7614-122">If you link multiple conditions using AND, the first set of conditions linked with AND applies to all the conditions in the second set.</span></span> <span data-ttu-id="e7614-123">也就是说，用 AND 与另一个条件链接的条件将分布到第二组的所有条件。</span><span class="sxs-lookup"><span data-stu-id="e7614-123">In other words, a condition linked with AND to another condition is distributed to all the conditions in the second set.</span></span> <span data-ttu-id="e7614-124">例如，下面的表达式简单表示了与一组 OR 条件链接的 AND 条件：</span><span class="sxs-lookup"><span data-stu-id="e7614-124">For example, the following schematic representation shows an AND condition linked to a set of OR conditions:</span></span>  
  
```  
A AND (B OR C)  
```  
  
 <span data-ttu-id="e7614-125">上面的表达式与下面的简单表达式在逻辑上是等效的，后者表示 AND 条件如何分布到第二组条件中：</span><span class="sxs-lookup"><span data-stu-id="e7614-125">The representation above is logically equivalent to the following schematic representation, which shows how the AND condition is distributed to the second set of conditions:</span></span>  
  
```  
(A AND B) OR (A AND C)  
```  
  
 <span data-ttu-id="e7614-126">这种分布式原则将影响您对查询和视图设计器的使用方式。</span><span class="sxs-lookup"><span data-stu-id="e7614-126">This distributive principle affects how you use the Query and View Designer.</span></span> <span data-ttu-id="e7614-127">例如，假设您要查找在公司工作五年以上的低级或中级职位的所有雇员。</span><span class="sxs-lookup"><span data-stu-id="e7614-127">For example, imagine that you are looking for all employees who have been with the company more than five years in either lower or middle-level jobs.</span></span> <span data-ttu-id="e7614-128">您可在 SQL 窗格内的语句中输入以下 WHERE 子句：</span><span class="sxs-lookup"><span data-stu-id="e7614-128">You enter the following WHERE clause into the statement in the SQL pane:</span></span>  
  
```  
WHERE (hire_date < '01/01/95' ) AND   
   (job_lvl = 100 OR job_lvl = 200)  
```  
  
 <span data-ttu-id="e7614-129">用 AND 链接的子句适用于用 OR 链接的两个子句。</span><span class="sxs-lookup"><span data-stu-id="e7614-129">The clause linked with AND applies to both clauses linked with OR.</span></span> <span data-ttu-id="e7614-130">为清楚起见，可以为 OR 子句中的每个条件重复一次 AND 条件。</span><span class="sxs-lookup"><span data-stu-id="e7614-130">An explicit way to express this is to repeat the AND condition once for each condition in the OR clause.</span></span> <span data-ttu-id="e7614-131">下面的语句比前面的语句更清楚明了（也更长），但逻辑上是等效的：</span><span class="sxs-lookup"><span data-stu-id="e7614-131">The following statement is more explicit (and longer) than the previous statement, but is logically equivalent to it:</span></span>  
  
```  
WHERE    (hire_date < '01/01/95' ) AND  
  (job_lvl = 100) OR   
  (hire_date < '01/01/95' ) AND   
  (job_lvl = 200)  
```  
  
 <span data-ttu-id="e7614-132">将 AND 子句分布到链接的 OR 子句的原则也适用于涉及多个条件的情况。</span><span class="sxs-lookup"><span data-stu-id="e7614-132">The principle of distributing AND clauses to linked OR clauses applies no matter how many individual conditions are involved.</span></span> <span data-ttu-id="e7614-133">例如，假设您要查找在公司工作五年以上或已退休的中级或更高职位的雇员。</span><span class="sxs-lookup"><span data-stu-id="e7614-133">For example, imagine that you want to find higher or middle-level employees who have been with the company more than five years or are retired.</span></span> <span data-ttu-id="e7614-134">该 WHERE 子句可能类似以下形式：</span><span class="sxs-lookup"><span data-stu-id="e7614-134">The WHERE clause might look like this:</span></span>  
  
```  
WHERE   
   (job_lvl = 200 OR job_lvl = 300) AND  
   (hire_date < '01/01/95' ) OR (status = 'R')  
```  
  
 <span data-ttu-id="e7614-135">在分布用 AND 链接的条件后，WHERE 子句将类似以下形式：</span><span class="sxs-lookup"><span data-stu-id="e7614-135">After the conditions linked with AND have been distributed, the WHERE clause will look like this:</span></span>  
  
```  
WHERE   
   (job_lvl = 200 AND hire_date < '01/01/95' ) OR  
   (job_lvl = 200 AND status = 'R') OR  
   (job_lvl = 300 AND hire_date < '01/01/95' ) OR  
   (job_lvl = 300 AND status = 'R')   
```  
  
## <a name="how-multiple-and-and-or-clauses-are-represented-in-the-criteria-pane"></a><span data-ttu-id="e7614-136">在“条件”窗格中如何表示多个 AND 和 OR 子句</span><span class="sxs-lookup"><span data-stu-id="e7614-136">How Multiple AND and OR Clauses Are Represented in the Criteria Pane</span></span>  
 <span data-ttu-id="e7614-137">查询和视图设计器可以在 [“条件”窗格](visual-database-tools.md)中显示搜索条件。</span><span class="sxs-lookup"><span data-stu-id="e7614-137">The Query and View Designer represents your search conditions in the [Criteria Pane](visual-database-tools.md).</span></span> <span data-ttu-id="e7614-138">但是，在需要用 AND 和 OR 链接多个子句的某些情况下，“条件”窗格中的表示形式可能会与预期形式不一样。</span><span class="sxs-lookup"><span data-stu-id="e7614-138">However, in some cases that involve multiple clauses linked with AND and OR, the representation in the Criteria Pane might not be what you expect.</span></span> <span data-ttu-id="e7614-139">另外，如果在“条件”窗格或 [“关系图”](diagram-pane-visual-database-tools.md)窗格中修改查询，你可能会发现生成的 SQL 语句与输入的语句不同。</span><span class="sxs-lookup"><span data-stu-id="e7614-139">In addition, if you modify your query in the Criteria Pane or [Diagram Pane](diagram-pane-visual-database-tools.md), you might find that your SQL statement has been changed from what you entered.</span></span>  
  
 <span data-ttu-id="e7614-140">一般情况下，以下规则将决定 AND 和 OR 子句在“条件”窗格中的显示方式：</span><span class="sxs-lookup"><span data-stu-id="e7614-140">In general, these rules dictate how AND and OR clauses appear in the Criteria Pane:</span></span>  
  
-   <span data-ttu-id="e7614-141">所有用 AND 链接的条件都显示在“筛选器”  网格列中或同一个“或...”  列中。</span><span class="sxs-lookup"><span data-stu-id="e7614-141">All conditions linked with AND appear in the **Filter** grid column or in the same **Or...** column.</span></span>  
  
-   <span data-ttu-id="e7614-142">所有用 OR 链接的条件都显示在不同的“或...”  列中。</span><span class="sxs-lookup"><span data-stu-id="e7614-142">All conditions linked with OR appear in separate **Or...** columns.</span></span>  
  
-   <span data-ttu-id="e7614-143">如果 AND 和 OR 子句组合的逻辑结果是将 AND 分布到多个 OR 子句中，则“条件”窗格将根据需要重复 AND 子句以明确地表示结果。</span><span class="sxs-lookup"><span data-stu-id="e7614-143">If the logical result of a combination of AND and OR clauses is that the AND is distributed into several OR clauses, the Criteria Pane represents this explicitly by repeating the AND clause as many times as necessary.</span></span>  
  
 <span data-ttu-id="e7614-144">例如，在 SQL 窗格中可创建如下搜索条件，其中用 AND 链接的两个子句的优先级高于用 OR 链接的第三个子句：</span><span class="sxs-lookup"><span data-stu-id="e7614-144">For example, in the SQL pane you might create a search condition such as the following, in which two clauses linked with AND take precedence over a third one linked with OR:</span></span>  
  
```  
WHERE (hire_date < '01/01/95' ) AND   
  (job_lvl = 100) OR   
  (status = 'R')  
```  
  
 <span data-ttu-id="e7614-145">查询和视图设计器在“条件”窗格中按以下形式显示此 WHERE 子句：</span><span class="sxs-lookup"><span data-stu-id="e7614-145">The Query and View Designer represents this WHERE clause in the Criteria Pane as follows:</span></span>  
  
 <span data-ttu-id="e7614-146">![“条件”窗格中的 OR 子句优先级](../../database-engine/media//vs-criteriapane1.gif "“条件”窗格中的 OR 子句优先级")</span><span class="sxs-lookup"><span data-stu-id="e7614-146">![OR clause precedence in the Criteria Pane](../../database-engine/media//vs-criteriapane1.gif "OR clause precedence in the Criteria Pane")</span></span>  
  
 <span data-ttu-id="e7614-147">但是，如果链接的 OR 子句优先级高于 AND 子句，则每个 OR 子句都会重复 AND 子句。</span><span class="sxs-lookup"><span data-stu-id="e7614-147">However, if the linked OR clauses take precedence over an AND clause, the AND clause is repeated for each OR clause.</span></span> <span data-ttu-id="e7614-148">这将导致 AND 子句分布到每个 OR 子句中。</span><span class="sxs-lookup"><span data-stu-id="e7614-148">This causes the AND clause to be distributed to each OR clause.</span></span> <span data-ttu-id="e7614-149">例如，在 SQL 窗格中可以创建如下 WHERE 子句：</span><span class="sxs-lookup"><span data-stu-id="e7614-149">For example, in the SQL pane you might create a WHERE clause such as the following:</span></span>  
  
```  
WHERE (hire_date < '01/01/95' ) AND   
  ( (job_lvl = 100) OR   
  (status = 'R') )  
```  
  
 <span data-ttu-id="e7614-150">查询和视图设计器在“条件”窗格中按以下形式显示此 WHERE 子句：</span><span class="sxs-lookup"><span data-stu-id="e7614-150">The Query and View Designer represents this WHERE clause in the Criteria Pane as follows:</span></span>  
  
 <span data-ttu-id="e7614-151">![“条件”窗格中的多个 AND 子句和 OR 子句](../../database-engine/media//vs-criteriapane2.gif "“条件”窗格中的多个 AND 子句和 OR 子句")</span><span class="sxs-lookup"><span data-stu-id="e7614-151">![Multiple AND and OR clauses in the Criteria Pane](../../database-engine/media//vs-criteriapane2.gif "Multiple AND and OR clauses in the Criteria Pane")</span></span>  
  
 <span data-ttu-id="e7614-152">如果链接的 OR 子句仅涉及一个数据列，查询和视图设计器会将整个 OR 子句放置到单个的网格单元格中，以避免重复 AND 子句。</span><span class="sxs-lookup"><span data-stu-id="e7614-152">If the linked OR clauses involve only one data column, the Query and View Designer can place the entire OR clause into a single cell of the grid, avoiding the need to repeat the AND clause.</span></span> <span data-ttu-id="e7614-153">例如，在 SQL 窗格中可以创建如下 WHERE 子句：</span><span class="sxs-lookup"><span data-stu-id="e7614-153">For example, in the SQL pane you might create a WHERE clause such as the following:</span></span>  
  
```  
WHERE (hire_date < '01/01/95' ) AND   
  ((status = 'R') OR (status = 'A'))  
```  
  
 <span data-ttu-id="e7614-154">查询和视图设计器在“条件”窗格中按以下形式显示此 WHERE 子句：</span><span class="sxs-lookup"><span data-stu-id="e7614-154">The Query and View Designer represents this WHERE clause in the Criteria Pane as follows:</span></span>  
  
 <span data-ttu-id="e7614-155">![“条件”窗格中定义的链接 OR 子句](../../database-engine/media//vs-criteriapane3.gif "“条件”窗格中定义的链接 OR 子句")</span><span class="sxs-lookup"><span data-stu-id="e7614-155">![Linked OR clauses defined in the Criteria Pane](../../database-engine/media//vs-criteriapane3.gif "Linked OR clauses defined in the Criteria Pane")</span></span>  
  
 <span data-ttu-id="e7614-156">如果更改查询（如更改“条件”窗格中的某个值），查询和视图设计器将在 SQL 窗格中重新创建 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="e7614-156">If you make a change to the query (such as changing one of the values in the Criteria Pane), the Query and View Designer recreates the SQL statement in the SQL pane.</span></span> <span data-ttu-id="e7614-157">重新创建的 SQL 语句将与“条件”窗格的显示形式相似，而不是与原始语句相似。</span><span class="sxs-lookup"><span data-stu-id="e7614-157">The recreated SQL statement will resemble the Criteria Pane display rather than your original statement.</span></span> <span data-ttu-id="e7614-158">例如，如果“条件”窗格中包含分布式的 AND 子句，则会用清楚明了的分布式 AND 子句重新创建 SQL 窗格中的结果语句。</span><span class="sxs-lookup"><span data-stu-id="e7614-158">For example, if the Criteria Pane contains distributed AND clauses, the resulting statement in the SQL pane will be recreated with explicit distributed AND clauses.</span></span> <span data-ttu-id="e7614-159">有关详细信息，请参阅本主题前面部分中的“AND 如何与多个 OR 子句一起使用”。</span><span class="sxs-lookup"><span data-stu-id="e7614-159">For details, see "How AND Works with Multiple OR Clauses" earlier in this topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7614-160">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e7614-160">See Also</span></span>  
 [<span data-ttu-id="e7614-161">指定搜索条件 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="e7614-161">Specify Search Criteria &#40;Visual Database Tools&#41;</span></span>](specify-search-criteria-visual-database-tools.md)  
  
  
