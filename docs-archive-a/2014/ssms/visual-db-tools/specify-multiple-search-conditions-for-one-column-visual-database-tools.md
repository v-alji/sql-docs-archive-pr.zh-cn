---
title: 为一个列 (Visual Database Tools) 指定多个搜索条件 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search criteria [SQL Server], multiple conditions
- multiple search conditions
- search conditions [SQL Server], multiple
- OR operator
- AND, Criteria pane
ms.assetid: 2c006e36-56b1-4992-89b4-c6c0b19808f3
author: stevestein
ms.author: sstein
ms.openlocfilehash: a07322120bd3b3f543e6f54fa50cdf75aa32be59
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586052"
---
# <a name="specify-multiple-search-conditions-for-one-column-visual-database-tools"></a><span data-ttu-id="a1252-102">为同一列指定多个搜索条件 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="a1252-102">Specify Multiple Search Conditions for One Column (Visual Database Tools)</span></span>
  <span data-ttu-id="a1252-103">在某些情况下，可能希望对同一数据列应用多个搜索条件。</span><span class="sxs-lookup"><span data-stu-id="a1252-103">In some instances, you might want to apply a number of search conditions to the same data column.</span></span> <span data-ttu-id="a1252-104">例如，您可能希望：</span><span class="sxs-lookup"><span data-stu-id="a1252-104">For example, you might want to:</span></span>  
  
-   <span data-ttu-id="a1252-105">在 `employee` 表中搜索几个不同的名字或搜索位于不同薪金范围内的雇员。</span><span class="sxs-lookup"><span data-stu-id="a1252-105">Search for several different names in an `employee` table or for employees who are in different salary ranges.</span></span> <span data-ttu-id="a1252-106">这种类型的搜索需要使用 OR 条件。</span><span class="sxs-lookup"><span data-stu-id="a1252-106">This type of search requires an OR condition.</span></span>  
  
-   <span data-ttu-id="a1252-107">搜索以单词“The”开头并包含单词“Cook”的书名。</span><span class="sxs-lookup"><span data-stu-id="a1252-107">Search for a book title that both starts with the word "The" and contains the word "Cook."</span></span> <span data-ttu-id="a1252-108">这种类型的搜索需要使用 AND 条件。</span><span class="sxs-lookup"><span data-stu-id="a1252-108">This type of search requires an AND condition.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a1252-109">本主题中的信息对查询的 WHERE 和 HAVING 子句中的搜索条件都适用。</span><span class="sxs-lookup"><span data-stu-id="a1252-109">The information in this topic applies to search conditions in both the WHERE and HAVING clauses of a query.</span></span> <span data-ttu-id="a1252-110">这些示例主要讨论创建 WHERE 子句，但其原理适用于这两种类型的搜索条件。</span><span class="sxs-lookup"><span data-stu-id="a1252-110">The examples focus on creating WHERE clauses, but the principles apply to both types of search conditions.</span></span>  
  
 <span data-ttu-id="a1252-111">若要在同一数据列中搜索可选值，可指定 OR 条件。</span><span class="sxs-lookup"><span data-stu-id="a1252-111">To search for alternative values in the same data column, you specify an OR condition.</span></span> <span data-ttu-id="a1252-112">若要搜索同时满足几个条件的值，可指定 AND 条件。</span><span class="sxs-lookup"><span data-stu-id="a1252-112">To search for values that meet several conditions, you specify an AND condition.</span></span>  
  
## <a name="specifying-an-or-condition"></a><span data-ttu-id="a1252-113">指定 OR 条件</span><span class="sxs-lookup"><span data-stu-id="a1252-113">Specifying an OR Condition</span></span>  
 <span data-ttu-id="a1252-114">使用 OR 条件，您可以指定要在列中搜索的多个可选值。</span><span class="sxs-lookup"><span data-stu-id="a1252-114">Using an OR condition enables you to specify several alternative values to search for in a column.</span></span> <span data-ttu-id="a1252-115">此选项扩展了搜索范围，可以比搜索单一值返回更多的行。</span><span class="sxs-lookup"><span data-stu-id="a1252-115">This option expands the scope of the search and can return more rows than searching for a single value.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="a1252-116">通常可以改用 IN 运算符在同一数据列中搜索多个值。</span><span class="sxs-lookup"><span data-stu-id="a1252-116">You can often use the IN operator instead to search for multiple values in the same data column.</span></span>  
  
#### <a name="to-specify-an-or-condition"></a><span data-ttu-id="a1252-117">指定 OR 条件</span><span class="sxs-lookup"><span data-stu-id="a1252-117">To specify an OR condition</span></span>  
  
1.  <span data-ttu-id="a1252-118">在[“条件窗格”](visual-database-tools.md)中，添加要搜索的列。</span><span class="sxs-lookup"><span data-stu-id="a1252-118">In the [Criteria Pane](visual-database-tools.md), add the column to search.</span></span>  
  
2.  <span data-ttu-id="a1252-119">在刚刚添加的数据列的“筛选器”  列中，指定第一个条件。</span><span class="sxs-lookup"><span data-stu-id="a1252-119">In the **Filter** column for the data column you just added, specify the first condition.</span></span>  
  
3.  <span data-ttu-id="a1252-120">在同一数据列的“或...”  列中，指定第二个条件。</span><span class="sxs-lookup"><span data-stu-id="a1252-120">In the **Or...** column for the same data column, specify the second condition.</span></span>  
  
 <span data-ttu-id="a1252-121">查询和视图设计器将创建包含 OR 条件的 WHERE 子句，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a1252-121">The Query and View Designer creates a WHERE clause that contains an OR condition such as the following:</span></span>  
  
```  
SELECT fname, lname  
FROM employees  
WHERE (salary < 30000) OR (salary > 100000)  
```  
  
## <a name="specifying-an-and-condition"></a><span data-ttu-id="a1252-122">指定 AND 条件</span><span class="sxs-lookup"><span data-stu-id="a1252-122">Specifying an AND Condition</span></span>  
 <span data-ttu-id="a1252-123">使用 AND 条件，您可以指定某列中的值必须同时满足两个（或更多）条件，才能使该行包含在结果集中。</span><span class="sxs-lookup"><span data-stu-id="a1252-123">Using an AND condition enables you to specify that values in a column must meet two (or more) conditions for the row to be included in the result set.</span></span> <span data-ttu-id="a1252-124">此选项缩小了搜索范围，通常会比搜索单一值返回更少的行。</span><span class="sxs-lookup"><span data-stu-id="a1252-124">This option narrows the scope of the search and usually returns fewer rows than searching for a single value.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="a1252-125">若要搜索一定范围内的值，可使用 BETWEEN 运算符替代 AND 来链接两个条件。</span><span class="sxs-lookup"><span data-stu-id="a1252-125">If you are searching for a range of values, you can use the BETWEEN operator instead of linking two conditions with AND.</span></span>  
  
#### <a name="to-specify-an-and-condition"></a><span data-ttu-id="a1252-126">指定 AND 条件</span><span class="sxs-lookup"><span data-stu-id="a1252-126">To specify an AND condition</span></span>  
  
1.  <span data-ttu-id="a1252-127">在“条件”窗格中，添加要搜索的列。</span><span class="sxs-lookup"><span data-stu-id="a1252-127">In the Criteria pane, add the column to search.</span></span>  
  
2.  <span data-ttu-id="a1252-128">在刚刚添加的数据列的“筛选器”  列中，指定第一个条件。</span><span class="sxs-lookup"><span data-stu-id="a1252-128">In the **Filter** column for the data column you just added, specify the first condition.</span></span>  
  
3.  <span data-ttu-id="a1252-129">将同一数据列再次添加到“条件”窗格中，将其放在网格的空行中。</span><span class="sxs-lookup"><span data-stu-id="a1252-129">Add the same data column to the Criteria pane again, placing it in an empty row of the grid.</span></span>  
  
4.  <span data-ttu-id="a1252-130">在数据列的第二个实例的“筛选器”  列中，指定第二个条件。</span><span class="sxs-lookup"><span data-stu-id="a1252-130">In the **Filter** column for the second instance of the data column, specify the second condition.</span></span>  
  
 <span data-ttu-id="a1252-131">查询设计器将创建包含 AND 条件的 WHERE 子句，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a1252-131">The Query Designer creates a WHERE clause that contains an AND condition such as the following:</span></span>  
  
```  
SELECT title_id, title  
FROM titles  
WHERE (title LIKE '%Cook%') AND   
  (title LIKE '%Recipe%')  
```  
  
## <a name="see-also"></a><span data-ttu-id="a1252-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a1252-132">See Also</span></span>  
 <span data-ttu-id="a1252-133">[在 "条件" 窗格中组合搜索条件的约定 &#40;Visual Database Tools&#41;](conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md) </span><span class="sxs-lookup"><span data-stu-id="a1252-133">[Conventions for Combining Search Conditions in the Criteria Pane &#40;Visual Database Tools&#41;](conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md) </span></span>  
 [<span data-ttu-id="a1252-134">指定搜索条件 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="a1252-134">Specify Search Criteria &#40;Visual Database Tools&#41;</span></span>](specify-search-criteria-visual-database-tools.md)  
  
  
