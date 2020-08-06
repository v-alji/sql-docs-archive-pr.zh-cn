---
title: 在 AND 优先时组合条件 (Visual Database Tools) | Microsoft Docs
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
- combining search conditions
- AND, Criteria pane
ms.assetid: 450eb2eb-6ea3-405b-8dd2-1ff926c016e7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 917d5381bc83083ee1fa3c07375945c0908da521
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682614"
---
# <a name="combine-conditions-when-and-has-precedence-visual-database-tools"></a><span data-ttu-id="e9a98-102">在 AND 优先时组合条件 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="e9a98-102">Combine Conditions When AND Has Precedence (Visual Database Tools)</span></span>
  <span data-ttu-id="e9a98-103">若要使用 AND 组合条件，应向查询中添加两次列，一个条件一次。</span><span class="sxs-lookup"><span data-stu-id="e9a98-103">To combine conditions with AND, you add the column to the query twice--once for each condition.</span></span> <span data-ttu-id="e9a98-104">若要使用 OR 组合条件，可将第一个条件放在“筛选器”列中，并将其他条件放在“或...”  列中。</span><span class="sxs-lookup"><span data-stu-id="e9a98-104">To combine conditions with OR, you put the first one in the Filter column and additional conditions into an **Or...** column.</span></span>  
  
 <span data-ttu-id="e9a98-105">例如，假设要查找在公司的低级职位工作五年以上的雇员，或查找中级职位的雇员而不考虑其雇佣日期。</span><span class="sxs-lookup"><span data-stu-id="e9a98-105">For example, imagine that you want to find either employees who have been with the company for more than five years in lower-level jobs or employees with middle-level jobs regardless of their hire date.</span></span> <span data-ttu-id="e9a98-106">此查询需要三个条件，其中两个条件用 AND 链接：</span><span class="sxs-lookup"><span data-stu-id="e9a98-106">This query requires three conditions, two of them linked with AND:</span></span>  
  
-   <span data-ttu-id="e9a98-107">雇佣日期在五年之前并且职位等级为 100 的雇员。</span><span class="sxs-lookup"><span data-stu-id="e9a98-107">Employees with a hire date earlier than five years ago AND with a job level of 100.</span></span>  
  
     <span data-ttu-id="e9a98-108">-或-</span><span class="sxs-lookup"><span data-stu-id="e9a98-108">-or-</span></span>  
  
-   <span data-ttu-id="e9a98-109">职位等级为 200 的雇员。</span><span class="sxs-lookup"><span data-stu-id="e9a98-109">Employees with a job level of 200.</span></span>  
  
### <a name="to-combine-conditions-when-and-has-precedence"></a><span data-ttu-id="e9a98-110">在 AND 优先时组合条件</span><span class="sxs-lookup"><span data-stu-id="e9a98-110">To combine conditions when AND has precedence</span></span>  
  
1.  <span data-ttu-id="e9a98-111">在 [“条件”窗格](visual-database-tools.md)中，添加要搜索的数据列。</span><span class="sxs-lookup"><span data-stu-id="e9a98-111">In the [Criteria pane](visual-database-tools.md), add the data columns you want to search.</span></span> <span data-ttu-id="e9a98-112">如果希望使用通过 AND 链接的两个或多个条件搜索同一列，则对于每个要搜索的值都必须将该数据列名添加到网格中一次。</span><span class="sxs-lookup"><span data-stu-id="e9a98-112">If you want to search the same column using two or more conditions linked with AND, you must add the data column name to the grid once for each value you want to search.</span></span>  
  
2.  <span data-ttu-id="e9a98-113">在“筛选器”  列中，输入要用 AND 链接的所有条件。</span><span class="sxs-lookup"><span data-stu-id="e9a98-113">In the **Filter** column, enter all the conditions that you want to link with AND.</span></span> <span data-ttu-id="e9a98-114">例如，若要用 AND 链接搜索 `hire_date` 列和 `job_lvl` 列的条件，请在“筛选器”列中分别输入值 `< '1/1/91'` 和 `= 100`。</span><span class="sxs-lookup"><span data-stu-id="e9a98-114">For example, to link conditions with AND that search the `hire_date` and `job_lvl` columns, enter the values `< '1/1/91'` and `= 100`, respectively, in the Filter column.</span></span>  
  
     <span data-ttu-id="e9a98-115">这些网格项在 [SQL 窗格](sql-pane-visual-database-tools.md)内的语句中生成以下 WHERE 子句：</span><span class="sxs-lookup"><span data-stu-id="e9a98-115">These grid entries produce the following WHERE clause in the statement in the [SQL Pane](sql-pane-visual-database-tools.md):</span></span>  
  
    ```  
    WHERE (hire_date < '01/01/91') AND  
      (job_lvl = 100)  
    ```  
  
3.  <span data-ttu-id="e9a98-116">在“或...”  网格列中，输入要用 OR 链接的条件。</span><span class="sxs-lookup"><span data-stu-id="e9a98-116">In the **Or...** grid column, enter conditions that you want to link with OR.</span></span> <span data-ttu-id="e9a98-117">例如，若要添加在 `job_lvl` 列中搜索其他值的条件，请在“或...”  列中输入其他值，例如 `= 200`。</span><span class="sxs-lookup"><span data-stu-id="e9a98-117">For example, to add a condition that searches for another value in the `job_lvl` column, enter an additional value in the **Or...** column, such as `= 200`.</span></span>  
  
     <span data-ttu-id="e9a98-118">在“或...”  列中添加值时，将向 SQL 窗格内的语句中的 WHERE 子句中添加另一个条件：</span><span class="sxs-lookup"><span data-stu-id="e9a98-118">Adding a value in the **Or...** column adds another condition to the WHERE clause in the statement in the SQL pane:</span></span>  
  
    ```  
    WHERE (hire_date < '01/01/91' ) AND  
      (job_lvl = 100) OR   
      (job_lvl = 200)  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e9a98-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e9a98-119">See Also</span></span>  
 <span data-ttu-id="e9a98-120">[在或具有优先 &#40;Visual Database Tools&#41;时组合条件](combine-conditions-when-or-has-precedence-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="e9a98-120">[Combine Conditions When OR Has Precedence &#40;Visual Database Tools&#41;](combine-conditions-when-or-has-precedence-visual-database-tools.md) </span></span>  
 <span data-ttu-id="e9a98-121">[在 "条件" 窗格中组合搜索条件的约定 &#40;Visual Database Tools&#41;](conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md) </span><span class="sxs-lookup"><span data-stu-id="e9a98-121">[Conventions for Combining Search Conditions in the Criteria Pane &#40;Visual Database Tools&#41;](conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md) </span></span>  
 <span data-ttu-id="e9a98-122">[&#40;Visual Database Tools&#41;中输入搜索值的规则](rules-for-entering-search-values-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="e9a98-122">[Rules for Entering Search Values &#40;Visual Database Tools&#41;](rules-for-entering-search-values-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="e9a98-123">指定搜索条件 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="e9a98-123">Specify Search Criteria &#40;Visual Database Tools&#41;</span></span>](specify-search-criteria-visual-database-tools.md)  
  
  
