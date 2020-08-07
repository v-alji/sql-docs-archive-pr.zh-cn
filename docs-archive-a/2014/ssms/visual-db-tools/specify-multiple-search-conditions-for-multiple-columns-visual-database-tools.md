---
title: " (Visual Database Tools) 为多个列指定多个搜索条件 |Microsoft Docs"
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
ms.assetid: 06617729-0d0b-4da2-9890-b7e2f5cdbc7b
author: stevestein
ms.author: sstein
ms.openlocfilehash: ccf08a98d39d4ab808b7c2df794164b341be363a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579932"
---
# <a name="specify-multiple-search-conditions-for-multiple-columns-visual-database-tools"></a><span data-ttu-id="0c952-102">为多个列指定多个搜索条件 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="0c952-102">Specify Multiple Search Conditions for Multiple Columns (Visual Database Tools)</span></span>
  <span data-ttu-id="0c952-103">通过在搜索条件中包括多个数据列，可以扩大或缩小查询范围。</span><span class="sxs-lookup"><span data-stu-id="0c952-103">You can expand or narrow the scope of your query by including several data columns as part of your search condition.</span></span> <span data-ttu-id="0c952-104">例如，您可能希望：</span><span class="sxs-lookup"><span data-stu-id="0c952-104">For example, you might want to:</span></span>  
  
-   <span data-ttu-id="0c952-105">搜索在公司工作五年以上或出任某些职位的雇员。</span><span class="sxs-lookup"><span data-stu-id="0c952-105">Search for employees who either have worked more than five years at the company or who hold certain jobs.</span></span>  
  
-   <span data-ttu-id="0c952-106">搜索由特定出版商出版的有关烹饪方面的书籍。</span><span class="sxs-lookup"><span data-stu-id="0c952-106">Search for a book that is both published by a specific publisher and pertains to cooking.</span></span>  
  
 <span data-ttu-id="0c952-107">若要创建在两个（或更多）列中的任一列中搜索值的查询，请指定 OR 条件。</span><span class="sxs-lookup"><span data-stu-id="0c952-107">To create a query that searches for values in either of two (or more) columns, you specify an OR condition.</span></span> <span data-ttu-id="0c952-108">若要创建必须满足两个（或更多）列中所有条件的查询，请指定 AND 条件。</span><span class="sxs-lookup"><span data-stu-id="0c952-108">To create a query that must meet all conditions in two (or more) columns, you specify an AND condition.</span></span>  
  
## <a name="specifying-an-or-condition"></a><span data-ttu-id="0c952-109">指定 OR 条件</span><span class="sxs-lookup"><span data-stu-id="0c952-109">Specifying an OR Condition</span></span>  
 <span data-ttu-id="0c952-110">若要创建使用 OR 链接的多个条件，请将每个独立的条件放在“条件”窗格的不同列中。</span><span class="sxs-lookup"><span data-stu-id="0c952-110">To create multiple conditions linked with OR, you put each separate condition in a different column of the Criteria pane.</span></span>  
  
#### <a name="to-specify-an-or-condition-for-two-different-columns"></a><span data-ttu-id="0c952-111">为两个不同的列指定 OR 条件</span><span class="sxs-lookup"><span data-stu-id="0c952-111">To specify an OR condition for two different columns</span></span>  
  
1.  <span data-ttu-id="0c952-112">在 [“条件”窗格](visual-database-tools.md)中，添加要搜索的列。</span><span class="sxs-lookup"><span data-stu-id="0c952-112">In the [Criteria Pane](visual-database-tools.md), add the columns you want to search.</span></span>  
  
2.  <span data-ttu-id="0c952-113">在要搜索的第一个列的“筛选器”  列中，指定第一个条件。</span><span class="sxs-lookup"><span data-stu-id="0c952-113">In the **Filter** column for the first column to search, specify the first condition.</span></span>  
  
3.  <span data-ttu-id="0c952-114">在要搜索的第二个数据列的 **Or...** 列中，指定第二个条件，将“筛选器”  列保留为空白。</span><span class="sxs-lookup"><span data-stu-id="0c952-114">In the **Or...** column for the second data column to search, specify the second condition, leaving the **Filter** column blank.</span></span>  
  
     <span data-ttu-id="0c952-115">查询和视图设计器将创建包含 OR 条件的 WHERE 子句，如下所示：</span><span class="sxs-lookup"><span data-stu-id="0c952-115">The Query and View Designer creates a WHERE clause that contains an OR condition such as the following:</span></span>  
  
    ```  
    SELECT job_lvl, hire_date  
    FROM employee  
    WHERE (job_lvl >= 200) OR   
      (hire_date < '01/01/1998')  
    ```  
  
4.  <span data-ttu-id="0c952-116">对每个要添加的其他条件重复第 2 和第 3 步。</span><span class="sxs-lookup"><span data-stu-id="0c952-116">Repeat Steps 2 and 3 for each additional condition you want to add.</span></span> <span data-ttu-id="0c952-117">对每个新条件使用不同的 **Or...** 列。</span><span class="sxs-lookup"><span data-stu-id="0c952-117">Use a different **Or...** column for each new condition.</span></span>  
  
## <a name="specifying-an-and-condition"></a><span data-ttu-id="0c952-118">指定 AND 条件</span><span class="sxs-lookup"><span data-stu-id="0c952-118">Specifying an AND Condition</span></span>  
 <span data-ttu-id="0c952-119">若要使用由 AND 链接的条件搜索不同的数据列，请将所有条件都放在网格的“筛选器”  列中。</span><span class="sxs-lookup"><span data-stu-id="0c952-119">To search different data columns using conditions linked with AND, you put all the conditions in the **Filter** column of the grid.</span></span>  
  
#### <a name="to-specify-an-and-condition-for-two-different-columns"></a><span data-ttu-id="0c952-120">为两个不同的列指定 AND 条件</span><span class="sxs-lookup"><span data-stu-id="0c952-120">To specify an AND condition for two different columns</span></span>  
  
1.  <span data-ttu-id="0c952-121">在 [“条件”窗格](visual-database-tools.md)中，添加要搜索的列。</span><span class="sxs-lookup"><span data-stu-id="0c952-121">In the [Criteria Pane](visual-database-tools.md), add the columns you want to search.</span></span>  
  
2.  <span data-ttu-id="0c952-122">在要搜索的第一个数据列的“筛选器”  列中，指定第一个条件。</span><span class="sxs-lookup"><span data-stu-id="0c952-122">In the **Filter** column for the first data column to search, specify the first condition.</span></span>  
  
3.  <span data-ttu-id="0c952-123">在第二个数据列的“筛选器”  列中，指定第二个条件。</span><span class="sxs-lookup"><span data-stu-id="0c952-123">In the **Filter** column for the second data column, specify the second condition.</span></span>  
  
     <span data-ttu-id="0c952-124">查询和视图设计器将创建包含 AND 条件的 WHERE 子句，如下所示：</span><span class="sxs-lookup"><span data-stu-id="0c952-124">The Query and View Designer creates a WHERE clause that contains an AND condition such as the following:</span></span>  
  
    ```  
    SELECT pub_id, title  
    FROM titles  
    WHERE (pub_id = '0877') AND (title LIKE '%Cook%')  
    ```  
  
4.  <span data-ttu-id="0c952-125">对每个要添加的其他条件重复第 2 和第 3 步。</span><span class="sxs-lookup"><span data-stu-id="0c952-125">Repeat Steps 2 and 3 for each additional condition you want to add.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c952-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0c952-126">See Also</span></span>  
 <span data-ttu-id="0c952-127">[当和具有优先 &#40;Visual Database Tools&#41;时组合条件](combine-conditions-when-and-has-precedence-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="0c952-127">[Combine Conditions When AND Has Precedence &#40;Visual Database Tools&#41;](combine-conditions-when-and-has-precedence-visual-database-tools.md) </span></span>  
 <span data-ttu-id="0c952-128">[在或具有优先 &#40;Visual Database Tools&#41;时组合条件](combine-conditions-when-or-has-precedence-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="0c952-128">[Combine Conditions When OR Has Precedence &#40;Visual Database Tools&#41;](combine-conditions-when-or-has-precedence-visual-database-tools.md) </span></span>  
 <span data-ttu-id="0c952-129">[在 "条件" 窗格中组合搜索条件的约定 &#40;Visual Database Tools&#41;](conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md) </span><span class="sxs-lookup"><span data-stu-id="0c952-129">[Conventions for Combining Search Conditions in the Criteria Pane &#40;Visual Database Tools&#41;](conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md) </span></span>  
 [<span data-ttu-id="0c952-130">指定搜索条件 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="0c952-130">Specify Search Criteria &#40;Visual Database Tools&#41;</span></span>](specify-search-criteria-visual-database-tools.md)  
  
  
