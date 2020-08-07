---
title: 包含或排除行 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search criteria [SQL Server], excluding rows
- search criteria [SQL Server], WHERE clause
- included rows
- search conditions [SQL Server], HAVING clause
- search criteria [SQL Server], including rows
- row excluded in search [SQL Server]
- search criteria [SQL Server], HAVING clause
- search conditions [SQL Server], WHERE clause
- row included in search [SQL Server]
- excluding rows
ms.assetid: ba4e1202-31a2-444d-8365-c68a530ef223
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7b2d31c51296fa73a503e59a14adb60d79a61178
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587664"
---
# <a name="include-or-exclude-rows-visual-database-tools"></a><span data-ttu-id="82c9f-102">包含或排除行 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="82c9f-102">Include or Exclude Rows (Visual Database Tools)</span></span>
  <span data-ttu-id="82c9f-103">若要限制 SELECT 查询应返回的行数，请创建搜索条件或筛选条件。</span><span class="sxs-lookup"><span data-stu-id="82c9f-103">To restrict the number of rows a SELECT query should return, you create search conditions or filter criteria.</span></span> <span data-ttu-id="82c9f-104">在 SQL 中，搜索条件出现在语句的 WHERE 子句中，或者如果创建的是聚合查询，则搜索条件将出现在 HAVING 子句中。</span><span class="sxs-lookup"><span data-stu-id="82c9f-104">In SQL, search conditions appear in the WHERE clause of the statement, or if you are creating an aggregate query, in the HAVING clause.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="82c9f-105">您也可使用搜索条件指示受“更新”、“插入结果”、“插入值”、“删除”或“生成表”查询影响的行。</span><span class="sxs-lookup"><span data-stu-id="82c9f-105">You can also use search conditions to indicate which rows are affected by an Update, Insert Results, Insert Values, Delete, or Make Table query.</span></span>  
  
 <span data-ttu-id="82c9f-106">当查询运行时， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 将检查搜索条件并将其应用到要搜索的表的每一行。</span><span class="sxs-lookup"><span data-stu-id="82c9f-106">When the query runs, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] examines and applies the search condition to each row in the tables you are searching.</span></span> <span data-ttu-id="82c9f-107">如果行满足搜索条件，就会包括在查询中。</span><span class="sxs-lookup"><span data-stu-id="82c9f-107">If the row meets the condition, it is included in the query.</span></span> <span data-ttu-id="82c9f-108">例如，一个查找特定区域内所有雇员的搜索条件可以类似如下形式：</span><span class="sxs-lookup"><span data-stu-id="82c9f-108">For example, a search condition that would find all the employees in a particular region might be:</span></span>  
  
```  
region = 'UK'  
```  
  
 <span data-ttu-id="82c9f-109">若要建立在结果中包括行的准则，可以使用多个搜索条件。</span><span class="sxs-lookup"><span data-stu-id="82c9f-109">To establish the criteria for including a row in a result, you can use multiple search conditions.</span></span> <span data-ttu-id="82c9f-110">例如，下面的搜索准则由两个搜索条件组成。</span><span class="sxs-lookup"><span data-stu-id="82c9f-110">For example, the following search criterion consists of two search conditions.</span></span> <span data-ttu-id="82c9f-111">只有当行满足这两个条件时，查询才在结果集内包括该行。</span><span class="sxs-lookup"><span data-stu-id="82c9f-111">The query includes a row in the result set only if that row satisfies both of the conditions.</span></span>  
  
```  
region = 'UK' AND product_line = 'Housewares'  
```  
  
 <span data-ttu-id="82c9f-112">您可以用 AND 或 OR 组合这些条件。</span><span class="sxs-lookup"><span data-stu-id="82c9f-112">You can combine these conditions with AND or OR.</span></span> <span data-ttu-id="82c9f-113">上面的示例使用了 AND。</span><span class="sxs-lookup"><span data-stu-id="82c9f-113">The previous example uses AND.</span></span> <span data-ttu-id="82c9f-114">相反，下面的准则使用的是 OR。</span><span class="sxs-lookup"><span data-stu-id="82c9f-114">In contrast, the following criterion uses OR.</span></span> <span data-ttu-id="82c9f-115">结果集将包括满足其中任一个搜索条件或两个搜索条件都满足的所有行：</span><span class="sxs-lookup"><span data-stu-id="82c9f-115">The result set will include any row that satisfies either or both of the search conditions:</span></span>  
  
```  
region = 'UK' OR product_line = 'Housewares'  
```  
  
 <span data-ttu-id="82c9f-116">您甚至可以组合对单个列的搜索条件。</span><span class="sxs-lookup"><span data-stu-id="82c9f-116">You can even combine search conditions on a single column.</span></span> <span data-ttu-id="82c9f-117">例如，下面的准则组合了区域列的两个条件：</span><span class="sxs-lookup"><span data-stu-id="82c9f-117">For example, the following criterion combines two conditions on the region column:</span></span>  
  
```  
region = 'UK' OR region = 'US'  
```  
  
 <span data-ttu-id="82c9f-118">有关组合搜索条件的详细信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="82c9f-118">For details about combining search conditions, see the following topics:</span></span>  
  
-   [<span data-ttu-id="82c9f-119">在“条件”窗格中组合搜索条件的约定 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="82c9f-119">Conventions for Combining Search Conditions in the Criteria Pane &#40;Visual Database Tools&#41;</span></span>](conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md)  
  
-   [<span data-ttu-id="82c9f-120">为同一列指定多个搜索条件 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="82c9f-120">Specify Multiple Search Conditions for One Column &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
-   [<span data-ttu-id="82c9f-121">为多个列指定多个搜索条件 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="82c9f-121">Specify Multiple Search Conditions for Multiple Columns &#40;Visual Database Tools&#41;</span></span>](specify-multiple-search-conditions-for-multiple-columns-visual-database-tools.md)  
  
-   [<span data-ttu-id="82c9f-122">在 AND 优先时组合条件 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="82c9f-122">Combine Conditions When AND Has Precedence &#40;Visual Database Tools&#41;</span></span>](combine-conditions-when-and-has-precedence-visual-database-tools.md)  
  
-   [<span data-ttu-id="82c9f-123">在 OR 优先时组合条件 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="82c9f-123">Combine Conditions When OR Has Precedence &#40;Visual Database Tools&#41;</span></span>](combine-conditions-when-or-has-precedence-visual-database-tools.md)  
  
## <a name="examples"></a><span data-ttu-id="82c9f-124">示例</span><span class="sxs-lookup"><span data-stu-id="82c9f-124">Examples</span></span>  
 <span data-ttu-id="82c9f-125">下面是使用各种运算符和行条件的查询的一些示例：</span><span class="sxs-lookup"><span data-stu-id="82c9f-125">Here are some examples of queries using various operators and row criteria:</span></span>  
  
-   <span data-ttu-id="82c9f-126">**文本** 单个文本值、数值、日期值或逻辑值。</span><span class="sxs-lookup"><span data-stu-id="82c9f-126">**Literal** A single text, numeric, date, or logical value.</span></span> <span data-ttu-id="82c9f-127">下面的示例使用一个文本值在所有行中查找在英国的雇员：</span><span class="sxs-lookup"><span data-stu-id="82c9f-127">The following example uses a literal to find all rows for employees in the United Kingdom:</span></span>  
  
    ```  
    WHERE region = 'UK'  
    ```  
  
-   <span data-ttu-id="82c9f-128">**列引用** 比较一个列中的值和另一个列中的值。</span><span class="sxs-lookup"><span data-stu-id="82c9f-128">**Column reference** Compares the values in one column with the values in another.</span></span> <span data-ttu-id="82c9f-129">下面的示例在 `products` 表中搜索所有生产成本低于运输成本的行：</span><span class="sxs-lookup"><span data-stu-id="82c9f-129">The following example searches a `products` table for all rows in which the value of the production cost is lower than the shipping cost:</span></span>  
  
    ```  
    WHERE prod_cost < ship_cost  
    ```  
  
-   <span data-ttu-id="82c9f-130">**函数** 对函数的引用，数据库后端可以对其进行解析以计算搜索值。</span><span class="sxs-lookup"><span data-stu-id="82c9f-130">**Function** A reference to a function that the database back-end can resolve to calculate a value for the search.</span></span> <span data-ttu-id="82c9f-131">此类函数可以是由数据库服务器定义的函数或者是返回标量值的用户定义函数。</span><span class="sxs-lookup"><span data-stu-id="82c9f-131">The function can be a function defined by the database server or a user-defined function that returns a scalar value.</span></span> <span data-ttu-id="82c9f-132">下面的示例搜索今天所下的订单（GETDATE(&#xA0;</ph>) 函数返回当前日期）：</span><span class="sxs-lookup"><span data-stu-id="82c9f-132">The following example searches for orders placed today (the GETDATE( ) function returns the current date):</span></span>  
  
    ```  
    WHERE order_date = GETDATE()  
    ```  
  
-   <span data-ttu-id="82c9f-133">**NULL** 下面的示例在 `authors` 表中搜索所有名字已存档的作者：</span><span class="sxs-lookup"><span data-stu-id="82c9f-133">**NULL** The following example searches an `authors` table for all authors who have a first name on file:</span></span>  
  
    ```  
    WHERE au_fname IS NOT NULL  
    ```  
  
-   <span data-ttu-id="82c9f-134">**计算** 涉及文本、列引用或其他表达式的计算结果。</span><span class="sxs-lookup"><span data-stu-id="82c9f-134">**Calculation** The result of a calculation that can involve literals, column references, or other expressions.</span></span> <span data-ttu-id="82c9f-135">下面的示例在 `products` 表中搜索零售价格高于生产成本两倍的所有行：</span><span class="sxs-lookup"><span data-stu-id="82c9f-135">The following example searches a `products` table to find all rows in which the retail sales price is more than twice the production cost:</span></span>  
  
    ```  
    WHERE sales_price > (prod_cost * 2)  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="82c9f-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="82c9f-136">See Also</span></span>  
 <span data-ttu-id="82c9f-137">[&#40;Visual Database Tools 的设计查询和视图操作指南主题&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="82c9f-137">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span></span>  
 <span data-ttu-id="82c9f-138">[指定 Visual Database Tools &#40;搜索条件&#41;](specify-search-criteria-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="82c9f-138">[Specify Search Criteria &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="82c9f-139">使用参数进行查询 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="82c9f-139">Query with Parameters &#40;Visual Database Tools&#41;</span></span>](query-with-parameters-visual-database-tools.md)  
  
  
