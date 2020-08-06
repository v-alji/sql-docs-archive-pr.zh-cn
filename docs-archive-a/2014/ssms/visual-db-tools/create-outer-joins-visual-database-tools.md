---
title: 创建外部联接 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- outer joins
- joins [SQL Server], outer
ms.assetid: 18de47b1-f936-427d-b852-fe6d20334f71
author: stevestein
ms.author: sstein
ms.openlocfilehash: f02c0be049e2e75e1a657bb3c027d20430d562cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693602"
---
# <a name="create-outer-joins-visual-database-tools"></a><span data-ttu-id="b98a6-102">创建外部联接 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="b98a6-102">Create Outer Joins (Visual Database Tools)</span></span>
  <span data-ttu-id="b98a6-103">默认情况下， [查询和视图设计器](visual-database-tools.md) 在表之间创建内部联接。</span><span class="sxs-lookup"><span data-stu-id="b98a6-103">By default, the [Query and View Designer](visual-database-tools.md) creates an inner join between tables.</span></span> <span data-ttu-id="b98a6-104">内部联接消除了与其他表中的行不匹配的行。</span><span class="sxs-lookup"><span data-stu-id="b98a6-104">Inner joins eliminate the rows that do not match with a row from the other table.</span></span> <span data-ttu-id="b98a6-105">但是，外部联接可以从 FROM 子句中提到的至少一个表或视图中返回所有行，只要这些行符合任何 WHERE 或 HAVING 搜索条件。</span><span class="sxs-lookup"><span data-stu-id="b98a6-105">Outer joins, however, return all rows from at least one of the tables or views mentioned in the FROM clause, as long as those rows meet any WHERE or HAVING search conditions.</span></span> <span data-ttu-id="b98a6-106">若要在结果集中包含在联接表无匹配项的数据行，可以创建外部联接。</span><span class="sxs-lookup"><span data-stu-id="b98a6-106">If you want to include data rows in the result set that do not have a match in the joined table, you can create an outer join.</span></span>  
  
 <span data-ttu-id="b98a6-107">在创建外部联接时，表在 SQL 语句中出现的顺序（反映在 SQL 窗格中）非常重要。</span><span class="sxs-lookup"><span data-stu-id="b98a6-107">When you create an outer join, the order in which tables appear in the SQL statement (as reflected in the SQL pane) is significant.</span></span> <span data-ttu-id="b98a6-108">添加的第一个表成为“左”表，而第二个表成为“右”表。</span><span class="sxs-lookup"><span data-stu-id="b98a6-108">The first table you add becomes the "left" table and the second table becomes the "right" table.</span></span> <span data-ttu-id="b98a6-109">（表在 [“关系图”窗格](diagram-pane-visual-database-tools.md) 中实际出现的顺序并不重要。）当指定左外部联接或右外部联接时，引用的顺序是将这些表添加到查询中的顺序，以及它们在 [SQL 窗格](sql-pane-visual-database-tools.md)中的 SQL 语句中出现的顺序。</span><span class="sxs-lookup"><span data-stu-id="b98a6-109">(The actual order in which the tables appear in the [Diagram pane](diagram-pane-visual-database-tools.md) is not significant.) When you specify a left or right outer join, you are referring to the order in which the tables were added to the query and to the order in which they appear in the SQL statement in the [SQL pane](sql-pane-visual-database-tools.md).</span></span>  
  
### <a name="to-create-an-outer-join"></a><span data-ttu-id="b98a6-110">创建外部联接</span><span class="sxs-lookup"><span data-stu-id="b98a6-110">To create an outer join</span></span>  
  
1.  <span data-ttu-id="b98a6-111">自动或手动创建外部联接。</span><span class="sxs-lookup"><span data-stu-id="b98a6-111">Create the join, either automatically or manually.</span></span> <span data-ttu-id="b98a6-112">有关详细信息，请参阅[自动联接表 (Visual Database Tools)](join-tables-automatically-visual-database-tools.md) 或[手动联接表 (Visual Database Tools)](join-tables-manually-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="b98a6-112">For details, see [Join Tables Automatically &#40;Visual Database Tools&#41;](join-tables-automatically-visual-database-tools.md) or [Join Tables Manually &#40;Visual Database Tools&#41;](join-tables-manually-visual-database-tools.md).</span></span>  
  
2.  <span data-ttu-id="b98a6-113">在“关系图”窗格中选择联接线，然后在“查询设计器”菜单中选择“选择 \<tablename> 中的全部行”，选择包含要包含其中更多行的表的命令。</span><span class="sxs-lookup"><span data-stu-id="b98a6-113">Select the join line in the Diagram pane, and then from the **Query Designer** menu, choose **Select All Rows from \<tablename>**, selecting the command that includes the table whose extra rows you want to include.</span></span>  
  
    -   <span data-ttu-id="b98a6-114">选择第一个表可以创建左外部联接。</span><span class="sxs-lookup"><span data-stu-id="b98a6-114">Choose the first table to create a left outer join.</span></span>  
  
    -   <span data-ttu-id="b98a6-115">选择第二个表可以创建右外部联接。</span><span class="sxs-lookup"><span data-stu-id="b98a6-115">Choose the second table to create a right outer join.</span></span>  
  
    -   <span data-ttu-id="b98a6-116">选择两个表可以创建完全外部联接。</span><span class="sxs-lookup"><span data-stu-id="b98a6-116">Choose both tables to create a full outer join.</span></span>  
  
 <span data-ttu-id="b98a6-117">在指定外部联接时，查询和视图设计器将修改联接线以指示外部联接。</span><span class="sxs-lookup"><span data-stu-id="b98a6-117">When you specify an outer join, the Query and View Designer modifies the join line to indicate an outer join.</span></span>  
  
 <span data-ttu-id="b98a6-118">此外，查询和视图设计器将修改 SQL 窗格中的 SQL 语句，以反映联接类型的变化，如以下语句所示：</span><span class="sxs-lookup"><span data-stu-id="b98a6-118">In addition, the Query and View Designer modifies the SQL statement in the SQL pane to reflect the change in join type, as shown in the following statement:</span></span>  
  
```  
SELECT employee.job_id, employee.emp_id,  
   employee.fname, employee.minit, jobs.job_desc  
FROM employee LEFT OUTER JOIN jobs ON   
    employee.job_id = jobs.job_id  
```  
  
 <span data-ttu-id="b98a6-119">因为外部联接包含不匹配的行，所以可使用它查找与外键约束冲突的行。</span><span class="sxs-lookup"><span data-stu-id="b98a6-119">Because an outer join includes unmatched rows, you can use it to find rows that violate foreign key constraints.</span></span> <span data-ttu-id="b98a6-120">为此，可以创建一个外部联接，然后添加搜索条件以查找最右侧表的主键列为空的行。</span><span class="sxs-lookup"><span data-stu-id="b98a6-120">To do so, you create an outer join and then add a search condition to find rows in which the primary key column of the rightmost table is null.</span></span> <span data-ttu-id="b98a6-121">例如，下面的外部联接可以查找在 `employee` 表中无相应行的 `jobs` 表中的行：</span><span class="sxs-lookup"><span data-stu-id="b98a6-121">For example, the following outer join finds rows in the `employee` table that do not have corresponding rows in the `jobs` table:</span></span>  
  
```  
SELECT employee.emp_id, employee.job_id  
FROM employee LEFT OUTER JOIN jobs   
   ON employee.job_id = jobs.job_id  
WHERE (jobs.job_id IS NULL)  
```  
  
## <a name="see-also"></a><span data-ttu-id="b98a6-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b98a6-122">See Also</span></span>  
 <span data-ttu-id="b98a6-123">[利用联接查询 &#40;Visual Database Tools&#41;](query-with-joins-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="b98a6-123">[Query with Joins &#40;Visual Database Tools&#41;](query-with-joins-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="b98a6-124">“联接”对话框 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="b98a6-124">Join Dialog Box &#40;Visual Database Tools&#41;</span></span>](join-dialog-box-visual-database-tools.md)  
  
  
