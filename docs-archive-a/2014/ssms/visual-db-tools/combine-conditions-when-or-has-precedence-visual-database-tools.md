---
title: 在 OR 优先时组合条件 (Visual Database Tools) | Microsoft Docs
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
- OR operator
ms.assetid: b30f5ac9-25e7-4163-80ed-44e4bccb455d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8be0d2f783c28662eb01f6bf191dc24d339534f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682611"
---
# <a name="combine-conditions-when-or-has-precedence-visual-database-tools"></a><span data-ttu-id="dacaa-102">在 OR 优先时组合条件 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="dacaa-102">Combine Conditions When OR Has Precedence (Visual Database Tools)</span></span>
  <span data-ttu-id="dacaa-103">若要用 OR 链接条件，并使其优先级高于用 AND 链接的条件，则必须为每个 OR 条件重复 AND 条件。</span><span class="sxs-lookup"><span data-stu-id="dacaa-103">To link conditions with OR and give them precedence over conditions linked with AND, you must repeat the AND condition for each OR condition.</span></span>  
  
 <span data-ttu-id="dacaa-104">例如，假设要查找在公司工作五年以上的低级职位或已退休的所有雇员。</span><span class="sxs-lookup"><span data-stu-id="dacaa-104">For example, imagine that you want to find all employees who have been with the company more than five years and have lower-level jobs or are retired.</span></span> <span data-ttu-id="dacaa-105">此查询需要三个条件，其中一个条件使用 AND 链接到另外两个条件：</span><span class="sxs-lookup"><span data-stu-id="dacaa-105">This query requires three conditions, a single condition linked to two additional conditions with AND:</span></span>  
  
-   <span data-ttu-id="dacaa-106">雇佣日期是在五年前的雇员，AND</span><span class="sxs-lookup"><span data-stu-id="dacaa-106">Employees with a hire date earlier than five years ago, and</span></span>  
  
-   <span data-ttu-id="dacaa-107">职位等级为 100 或其状态为“R”（表示已退休）的雇员。</span><span class="sxs-lookup"><span data-stu-id="dacaa-107">Employees with a job level of 100 or whose status is "R" (for retired).</span></span>  
  
 <span data-ttu-id="dacaa-108">以下过程说明如何在“条件”窗格中创建此类查询。</span><span class="sxs-lookup"><span data-stu-id="dacaa-108">The following procedure illustrates how to create this type of query in the Criteria pane.</span></span>  
  
### <a name="to-combine-conditions-when-or-has-precedence"></a><span data-ttu-id="dacaa-109">在 OR 优先时组合条件</span><span class="sxs-lookup"><span data-stu-id="dacaa-109">To combine conditions when OR has precedence</span></span>  
  
1.  <span data-ttu-id="dacaa-110">在 [“条件”窗格](visual-database-tools.md)中，添加要搜索的数据列。</span><span class="sxs-lookup"><span data-stu-id="dacaa-110">In the [Criteria pane](visual-database-tools.md), add the data columns you want to search.</span></span> <span data-ttu-id="dacaa-111">如果希望使用通过 AND 链接的两个或多个条件搜索同一列，则对于每个要搜索的值都必须将该数据列名添加到网格中一次。</span><span class="sxs-lookup"><span data-stu-id="dacaa-111">If you want to search the same column using two or more conditions linked with AND, you must add the data column name to the grid once for each value you want to search.</span></span>  
  
2.  <span data-ttu-id="dacaa-112">创建将由 OR 链接的条件，方法是将第一个条件输入到“筛选器”  网格列中，然后将第二个（以及后续条件）输入单独的“或...”  列中。</span><span class="sxs-lookup"><span data-stu-id="dacaa-112">Create the conditions to be linked with OR by entering the first one into the **Filter** grid column and the second (and subsequent ones) into separate **Or...** columns.</span></span> <span data-ttu-id="dacaa-113">例如，若要用 OR 链接搜索 `job_lvl` 和 `status` 列的条件，请在“筛选器”列中为 `job_lvl` 输入 `= 100`，在“或...”列中为 `status` 输入 `= 'R'`。</span><span class="sxs-lookup"><span data-stu-id="dacaa-113">For example, to link conditions with OR that search the `job_lvl` and `status` columns, enter `= 100` in the **Filter** column for `job_lvl` and `= 'R'` in the **Or...** column for `status`.</span></span>  
  
     <span data-ttu-id="dacaa-114">在网格中输入这些值后，就会在 SQL 窗格内的语句中生成以下 WHERE 子句：</span><span class="sxs-lookup"><span data-stu-id="dacaa-114">Entering these values in the grid produces the following WHERE clause in the statement in the SQL pane:</span></span>  
  
    ```  
    WHERE (job_lvl = 100) OR (status = 'R')  
    ```  
  
3.  <span data-ttu-id="dacaa-115">通过为每个 OR 条件输入一次 AND 条件来创建 AND 条件。</span><span class="sxs-lookup"><span data-stu-id="dacaa-115">Create the AND condition by entering it once for each OR condition.</span></span> <span data-ttu-id="dacaa-116">将每个项放在其所对应的 OR 条件所在的同一网格列中。</span><span class="sxs-lookup"><span data-stu-id="dacaa-116">Place each entry in the same grid column as the OR condition it corresponds to.</span></span> <span data-ttu-id="dacaa-117">例如，若要添加搜索 `hire_date` 列并应用于两个 OR 条件的 AND 条件，请在“条件”列和“或...”列中均输入 `< '1/1/91'`。</span><span class="sxs-lookup"><span data-stu-id="dacaa-117">For example, to add an AND condition that searches the `hire_date` column and applies to both OR conditions, enter `< '1/1/91'` in both the Criteria column and the **Or...** column.</span></span>  
  
     <span data-ttu-id="dacaa-118">在网格中输入这些值后，就会在 SQL 窗格内的语句中生成以下 WHERE 子句：</span><span class="sxs-lookup"><span data-stu-id="dacaa-118">Entering these values in the grid produces the following WHERE clause in the statement in the SQL pane:</span></span>  
  
    ```  
    WHERE (job_lvl = 100) AND   
      (hire_date < '01/01/91' ) OR  
      (status = 'R') AND   
      (hire_date < '01/01/91' )  
    ```  
  
    > [!TIP]  
    >  <span data-ttu-id="dacaa-119">可通过添加一次 AND 条件，再使用“编辑”  菜单中的“剪切”  和“粘贴”  命令对其他 OR 条件重复此操作来重复 AND 条件。</span><span class="sxs-lookup"><span data-stu-id="dacaa-119">You can repeat an AND condition by adding it once, and then using the **Cut** and **Paste** commands from the **Edit** menu to repeat it for other OR conditions.</span></span>  
  
 <span data-ttu-id="dacaa-120">查询和视图设计器创建的 WHERE 子句等效于以下 WHERE 子句，后者使用括号指定 OR 优先于 AND：</span><span class="sxs-lookup"><span data-stu-id="dacaa-120">The WHERE clause created by the Query and View Designer is equivalent to the following WHERE clause, which uses parentheses to specify the precedence of OR over AND:</span></span>  
  
```  
WHERE (job_lvl = 100 OR status = 'R') AND  
   (hire_date < '01/01/91')  
```  
  
> [!NOTE]  
>  <span data-ttu-id="dacaa-121">如果以上面显示的格式在 [SQL 窗格](sql-pane-visual-database-tools.md)中输入搜索条件，然后在“关系图”或“条件”窗格中对该查询进行更改，则查询和视图设计器将重新创建 SQL 语句，以使其形式与显式分配到两个 OR 条件的 AND 条件相匹配。</span><span class="sxs-lookup"><span data-stu-id="dacaa-121">If you enter the search conditions in the format shown immediately above in the [SQL Pane](sql-pane-visual-database-tools.md), but then make a change to the query in the Diagram or Criteria panes, the Query and View Designer recreates the SQL statement to match the form with the AND condition explicitly distributed to both OR conditions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dacaa-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dacaa-122">See Also</span></span>  
 <span data-ttu-id="dacaa-123">[在 "条件" 窗格中组合搜索条件的约定 &#40;Visual Database Tools&#41;](conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md) </span><span class="sxs-lookup"><span data-stu-id="dacaa-123">[Conventions for Combining Search Conditions in the Criteria Pane &#40;Visual Database Tools&#41;](conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md) </span></span>  
 [<span data-ttu-id="dacaa-124">指定搜索条件 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="dacaa-124">Specify Search Criteria &#40;Visual Database Tools&#41;</span></span>](specify-search-criteria-visual-database-tools.md)  
  
  
