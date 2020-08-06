---
title: 创建“生成表”查询 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- queries [SQL Server], types
- table creation [SQL Server], Make Table query
- inserting tables
- Make Table query
- adding tables
ms.assetid: 4493cffa-7b2d-4c24-8ef0-d49329198972
author: stevestein
ms.author: sstein
ms.openlocfilehash: 91c4a3bf45935053789d6e884b1af5b338b4c7c9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689216"
---
# <a name="create-make-table-queries-visual-database-tools"></a><span data-ttu-id="2a471-102">创建“生成表”查询 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="2a471-102">Create Make Table Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="2a471-103">可以使用“生成表”查询将行复制到一个新表中，“生成表”查询对创建要使用的数据子集或在数据库之间复制表的内容非常有用。</span><span class="sxs-lookup"><span data-stu-id="2a471-103">You can copy rows into a new table using a Make Table query, which is useful for creating subsets of data to work with or copying the contents of a table from one database to another.</span></span> <span data-ttu-id="2a471-104">“生成表”查询与“插入结果”查询类似，但它会创建要向其中复制行的新表。</span><span class="sxs-lookup"><span data-stu-id="2a471-104">A Make Table query is similar to an Insert Results query but creates a new table to copy rows into.</span></span>  
  
 <span data-ttu-id="2a471-105">在创建“生成表”查询时，需要指定：</span><span class="sxs-lookup"><span data-stu-id="2a471-105">When you create a Make Table query, you specify:</span></span>  
  
-   <span data-ttu-id="2a471-106">新数据库表的名称（目标表）。</span><span class="sxs-lookup"><span data-stu-id="2a471-106">The name of the new database table (the destination table).</span></span>  
  
-   <span data-ttu-id="2a471-107">从中复制行的一个或多个表（源表）。</span><span class="sxs-lookup"><span data-stu-id="2a471-107">The table or tables to copy rows from (the source table).</span></span> <span data-ttu-id="2a471-108">您可以从单个表或联接的表中复制行。</span><span class="sxs-lookup"><span data-stu-id="2a471-108">You can copy from a single table or from joined tables.</span></span>  
  
-   <span data-ttu-id="2a471-109">源表中要复制其内容的列。</span><span class="sxs-lookup"><span data-stu-id="2a471-109">The columns in the source table whose contents you want to copy.</span></span>  
  
-   <span data-ttu-id="2a471-110">排序顺序（如果您希望按特定顺序复制行）。</span><span class="sxs-lookup"><span data-stu-id="2a471-110">Sort order, if you want to copy the rows in a particular order.</span></span>  
  
-   <span data-ttu-id="2a471-111">定义要复制的行的搜索条件。</span><span class="sxs-lookup"><span data-stu-id="2a471-111">Search conditions to define the rows you want to copy.</span></span>  
  
-   <span data-ttu-id="2a471-112">“分组依据”选项（如果您希望仅复制摘要信息）。</span><span class="sxs-lookup"><span data-stu-id="2a471-112">Group By options, if you want to copy only summary information.</span></span>  
  
 <span data-ttu-id="2a471-113">例如，下面的查询将创建一个名为 `uk`_`customers` 的新表，并将 `customers` 表中的信息复制到该表中：</span><span class="sxs-lookup"><span data-stu-id="2a471-113">For example, the following query creates a new table called `uk`_`customers` and copies information from the `customers` table to it:</span></span>  
  
```  
SELECT *   
INTO uk_customers  
FROM customers  
WHERE country = 'UK'  
```  
  
 <span data-ttu-id="2a471-114">为了成功使用“生成表”查询：</span><span class="sxs-lookup"><span data-stu-id="2a471-114">In order to use a Make Table query successfully:</span></span>  
  
-   <span data-ttu-id="2a471-115">数据库必须支持 SELECT...INTO 语法。</span><span class="sxs-lookup"><span data-stu-id="2a471-115">Your database must support the SELECT...INTO syntax.</span></span>  
  
-   <span data-ttu-id="2a471-116">必须具有在目标数据库中创建表的权限。</span><span class="sxs-lookup"><span data-stu-id="2a471-116">You must have permission to create a table in the target database.</span></span>  
  
### <a name="to-create-a-make-table-query"></a><span data-ttu-id="2a471-117">创建“生成表”查询</span><span class="sxs-lookup"><span data-stu-id="2a471-117">To create a Make Table query</span></span>  
  
1.  <span data-ttu-id="2a471-118">将一个或多个源表添加到“关系图”窗格中。</span><span class="sxs-lookup"><span data-stu-id="2a471-118">Add the source table or tables to the Diagram pane.</span></span>  
  
2.  <span data-ttu-id="2a471-119">在“查询设计器”  菜单中，指向“更改类型”  ，再单击“生成表”  。</span><span class="sxs-lookup"><span data-stu-id="2a471-119">From the **Query Designer** menu, point to **Change Type**, and then click **Make Table**.</span></span>  
  
3.  <span data-ttu-id="2a471-120">在“生成表”  对话框中，键入目标表的名称。</span><span class="sxs-lookup"><span data-stu-id="2a471-120">In the **Make Table** dialog box, type the name of the destination table.</span></span> <span data-ttu-id="2a471-121">查询和视图设计器不会检查该名称是否已使用，也不会检查您是否具有创建表的权限。</span><span class="sxs-lookup"><span data-stu-id="2a471-121">The Query and View Designer does not check whether the name is already in use or whether you have permission to create the table.</span></span>  
  
     <span data-ttu-id="2a471-122">若要在另一个数据库中创建目标表，请指定完全限定表名，包括目标数据库的名称、所有者（如果需要）以及表名。</span><span class="sxs-lookup"><span data-stu-id="2a471-122">To create a destination table in another database, specify a fully qualified table name including the name of the target database, the owner (if required), and the name of the table.</span></span>  
  
4.  <span data-ttu-id="2a471-123">通过将其添加到查询中来指定要复制的列。</span><span class="sxs-lookup"><span data-stu-id="2a471-123">Specify the columns to copy by adding them to the query.</span></span> <span data-ttu-id="2a471-124">有关详细信息，请参阅[向查询中添加列 (Visual Database Tools)](visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="2a471-124">For details, see [Add Columns to Queries &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span> <span data-ttu-id="2a471-125">列只有在添加到查询后才能复制。</span><span class="sxs-lookup"><span data-stu-id="2a471-125">Columns will be copied only if you add them to the query.</span></span> <span data-ttu-id="2a471-126">若要复制整行，请选择 " \*\* \*)  (所有列\*\*"。</span><span class="sxs-lookup"><span data-stu-id="2a471-126">To copy entire rows, choose **\* (All Columns)**.</span></span>  
  
     <span data-ttu-id="2a471-127">“查询和视图设计器”会将选择的列添加到“条件”窗格的“列”  列中。</span><span class="sxs-lookup"><span data-stu-id="2a471-127">The Query and View Designer adds the columns you choose to the **Column** column of the Criteria pane.</span></span>  
  
5.  <span data-ttu-id="2a471-128">如果希望按特定顺序复制行，请指定排序顺序。</span><span class="sxs-lookup"><span data-stu-id="2a471-128">If you want to copy rows in a particular order, specify a sort order.</span></span> <span data-ttu-id="2a471-129">有关详细信息，请参阅“对查询结果进行排序和分组”  。</span><span class="sxs-lookup"><span data-stu-id="2a471-129">For details, see **Sorting and Grouping Query Results**.</span></span>  
  
6.  <span data-ttu-id="2a471-130">通过输入搜索条件指定要复制的行。</span><span class="sxs-lookup"><span data-stu-id="2a471-130">Specify the rows to copy by entering search conditions.</span></span> <span data-ttu-id="2a471-131">有关详细信息，请参阅[指定搜索条件 (Visual Database Tools)](specify-search-criteria-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="2a471-131">For details, see [Specify Search Criteria &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md).</span></span>  
  
     <span data-ttu-id="2a471-132">如果未指定搜索条件，则源表中的所有行都会复制到目标表中。</span><span class="sxs-lookup"><span data-stu-id="2a471-132">If you do not specify a search condition, all rows from the source table will be copied to the destination table.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2a471-133">当向“条件”窗格添加要搜索的列时，查询和视图设计器也会将该列添加到要复制的列的列表中。</span><span class="sxs-lookup"><span data-stu-id="2a471-133">When you add a column to search to the Criteria pane, the Query and View Designer also adds it to the list of columns to copy.</span></span> <span data-ttu-id="2a471-134">若要在搜索中使用某列但不复制该列，请在表示表或表结构对象的矩形中，清除该列名旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="2a471-134">If you want to use a column for searching but not copy it, clear the check box next to the column name in the rectangle representing the table or table-structured object.</span></span>  
  
7.  <span data-ttu-id="2a471-135">如果希望复制摘要信息，请指定“分组依据”选项。</span><span class="sxs-lookup"><span data-stu-id="2a471-135">If you want to copy summary information, specify Group By options.</span></span> <span data-ttu-id="2a471-136">有关详细信息，请参阅[汇总查询结果 (Visual Database Tools)](summarize-query-results-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="2a471-136">For details, see [Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="2a471-137">在执行“生成表”查询时，不会在 [“结果窗格”](results-pane-visual-database-tools.md)中报告任何结果。</span><span class="sxs-lookup"><span data-stu-id="2a471-137">When you execute a Make Table query, no results are reported in the [Results Pane](results-pane-visual-database-tools.md).</span></span> <span data-ttu-id="2a471-138">但是，会显示一条消息，指出已复制的行数。</span><span class="sxs-lookup"><span data-stu-id="2a471-138">Instead, a message appears indicating how many rows were copied.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a471-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2a471-139">See Also</span></span>  
 <span data-ttu-id="2a471-140">[&#40;Visual Database Tools 的设计查询和视图操作指南主题&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="2a471-140">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="2a471-141">查询类型 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="2a471-141">Types of Queries &#40;Visual Database Tools&#41;</span></span>](types-of-queries-visual-database-tools.md)  
  
  
