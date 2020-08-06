---
title: 计算表中的行数 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- totals [SQL Server], row counts
- row counts [SQL Server]
- column values [SQL Server]
- number of rows
- number of values
- counting rows
ms.assetid: dda4296a-1d16-4e77-8d6f-e295f6dd4e87
author: stevestein
ms.author: sstein
ms.openlocfilehash: f6dca92fb955b776f56d9b51f28b1a486b89f18f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689682"
---
# <a name="count-rows-in-a-table-visual-database-tools"></a><span data-ttu-id="5bfe1-102">计算表中的行数 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="5bfe1-102">Count Rows in a Table (Visual Database Tools)</span></span>
  <span data-ttu-id="5bfe1-103">您可对表中的行进行计数以确定以下信息：</span><span class="sxs-lookup"><span data-stu-id="5bfe1-103">You can count rows in a table to determine:</span></span>  
  
-   <span data-ttu-id="5bfe1-104">表中的总行数，例如 `titles` 表中所有书籍的数量。</span><span class="sxs-lookup"><span data-stu-id="5bfe1-104">The total number of rows in a table, for example, a count of all the books in a `titles` table.</span></span>  
  
-   <span data-ttu-id="5bfe1-105">表中满足特定条件的行数，例如， `titles` 表中某出版商出版的书籍数量。</span><span class="sxs-lookup"><span data-stu-id="5bfe1-105">The number of rows in a table that meet a specific condition, for example, the number of books by one publisher in a `titles` table.</span></span>  
  
-   <span data-ttu-id="5bfe1-106">特定列中的值的数量。</span><span class="sxs-lookup"><span data-stu-id="5bfe1-106">The number of values in a particular column.</span></span>  
  
 <span data-ttu-id="5bfe1-107">当对列中的值进行计数时，空值将不包含在计数中。</span><span class="sxs-lookup"><span data-stu-id="5bfe1-107">When you count values in a column, nulls are not included in the count.</span></span> <span data-ttu-id="5bfe1-108">例如，假设要计算 `titles` 表中在 `advance` 列具有值的书籍的数量。</span><span class="sxs-lookup"><span data-stu-id="5bfe1-108">For example, you might count the number of books in a `titles` table that have values in the `advance` column.</span></span> <span data-ttu-id="5bfe1-109">默认情况下，该计数包含所有值，而不仅仅是唯一值。</span><span class="sxs-lookup"><span data-stu-id="5bfe1-109">By default, the count includes all values, not just unique values.</span></span>  
  
 <span data-ttu-id="5bfe1-110">以上所有三种类型的计数过程都是类似的。</span><span class="sxs-lookup"><span data-stu-id="5bfe1-110">The procedures for all three types of counts are similar.</span></span>  
  
### <a name="to-count-all-the-rows-in-a-table"></a><span data-ttu-id="5bfe1-111">对表中的所有行进行计数</span><span class="sxs-lookup"><span data-stu-id="5bfe1-111">To count all the rows in a table</span></span>  
  
1.  <span data-ttu-id="5bfe1-112">确保您要汇总的表已经包含在“关系图”窗格中。</span><span class="sxs-lookup"><span data-stu-id="5bfe1-112">Be sure the table you want to summarize is already present in the Diagram pane.</span></span>  
  
2.  <span data-ttu-id="5bfe1-113">右键单击“关系图”窗格的背景，再从快捷菜单中选择“添加分组依据”  。</span><span class="sxs-lookup"><span data-stu-id="5bfe1-113">Right-click the background of the Diagram pane, then choose **Add Group By** from the shortcut menu.</span></span> <span data-ttu-id="5bfe1-114">[查询和视图设计器](visual-database-tools.md)会在“条件”窗格的网格中添加一个“分组依据”  列。</span><span class="sxs-lookup"><span data-stu-id="5bfe1-114">The [Query and View Designer](visual-database-tools.md) adds a **Group By** column to the grid in the Criteria pane.</span></span>  
  
3.  <span data-ttu-id="5bfe1-115">选择表示表或表值对象的矩形中\*\* \*)  (所有列\*\*。</span><span class="sxs-lookup"><span data-stu-id="5bfe1-115">Select **\* (All Columns)** in the rectangle representing the table or table-valued object.</span></span>  
  
     <span data-ttu-id="5bfe1-116">查询和视图设计器会自动在“条件”窗格的“分组依据”列中填充 **Count** 一词，并为要汇总的列分配列别名。</span><span class="sxs-lookup"><span data-stu-id="5bfe1-116">The Query and View Designer automatically fills the term **Count** into the **Group By** column in the Criteria pane and assigns a column alias to the column you are summarizing.</span></span> <span data-ttu-id="5bfe1-117">您可以用更有意义的名称替换这一自动生成的别名。</span><span class="sxs-lookup"><span data-stu-id="5bfe1-117">You can replace this automatically generated alias with a more meaningful one.</span></span> <span data-ttu-id="5bfe1-118">有关详细信息，请参阅[创建列别名 (Visual Database Tools)](create-column-aliases-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="5bfe1-118">For more details, see [Create Column Aliases &#40;Visual Database Tools&#41;](create-column-aliases-visual-database-tools.md).</span></span>  
  
4.  <span data-ttu-id="5bfe1-119">运行查询。</span><span class="sxs-lookup"><span data-stu-id="5bfe1-119">Run the query.</span></span>  
  
### <a name="to-count-all-the-rows-that-meet-a-condition"></a><span data-ttu-id="5bfe1-120">对满足条件的所有行进行计数</span><span class="sxs-lookup"><span data-stu-id="5bfe1-120">To count all the rows that meet a condition</span></span>  
  
1.  <span data-ttu-id="5bfe1-121">确保您要汇总的表已经包含在“关系图”窗格中。</span><span class="sxs-lookup"><span data-stu-id="5bfe1-121">Be sure the table you want to summarize is already present in the Diagram pane.</span></span>  
  
2.  <span data-ttu-id="5bfe1-122">右键单击“关系图”窗格的背景，再从快捷菜单中选择“添加分组依据”  。</span><span class="sxs-lookup"><span data-stu-id="5bfe1-122">Right-click the background of the Diagram pane, then choose **Add Group By** from the shortcut menu.</span></span> <span data-ttu-id="5bfe1-123">查询和视图设计器会在“条件”窗格的网格中添加一个“分组依据”  列。</span><span class="sxs-lookup"><span data-stu-id="5bfe1-123">The Query and View Designer adds a **Group By** column to the grid in the Criteria pane.</span></span>  
  
3.  <span data-ttu-id="5bfe1-124">选择表示表或表结构对象的矩形中\*\* \*)  (所有列\*\*。</span><span class="sxs-lookup"><span data-stu-id="5bfe1-124">Select **\*(All Columns)** in the rectangle representing the table or table-structured object.</span></span>  
  
     <span data-ttu-id="5bfe1-125">查询和视图设计器会自动在“条件”窗格的“分组依据”列中填充 **Count** 一词，并为要汇总的列分配列别名。</span><span class="sxs-lookup"><span data-stu-id="5bfe1-125">The Query and View Designer automatically fills the term **Count** into the **Group By** column in the Criteria pane and assigns a column alias to the column you are summarizing.</span></span> <span data-ttu-id="5bfe1-126">若要在查询输出中创建更实用的列标题，请参阅[创建列别名 (Visual Database Tools)](create-column-aliases-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="5bfe1-126">To create a more useful column heading in query output, see [Create Column Aliases &#40;Visual Database Tools&#41;](create-column-aliases-visual-database-tools.md).</span></span>  
  
4.  <span data-ttu-id="5bfe1-127">添加要搜索的数据列，再清除“输出”  列中的复选框。</span><span class="sxs-lookup"><span data-stu-id="5bfe1-127">Add the data column that you want to search, and then clear the check box in the **Output** column.</span></span>  
  
     <span data-ttu-id="5bfe1-128">查询和视图设计器会自动在网格的“分组依据”列中填充 **Group By** 一词。</span><span class="sxs-lookup"><span data-stu-id="5bfe1-128">The Query and View Designer automatically fills the term **Group By** into the **Group By** column of the grid.</span></span>  
  
5.  <span data-ttu-id="5bfe1-129">将“分组依据”列中的 **Group By** 改为 **Where**。</span><span class="sxs-lookup"><span data-stu-id="5bfe1-129">Change **Group By** in the **Group By** column to **Where**.</span></span>  
  
6.  <span data-ttu-id="5bfe1-130">在要搜索的数据列的“筛选器”  列中，输入搜索条件。</span><span class="sxs-lookup"><span data-stu-id="5bfe1-130">In the **Filter** column for the data column to search, enter the search condition.</span></span>  
  
7.  <span data-ttu-id="5bfe1-131">运行查询。</span><span class="sxs-lookup"><span data-stu-id="5bfe1-131">Run the query.</span></span>  
  
### <a name="to-count-the-values-in-a-column"></a><span data-ttu-id="5bfe1-132">对列中的值进行计数</span><span class="sxs-lookup"><span data-stu-id="5bfe1-132">To count the values in a column</span></span>  
  
1.  <span data-ttu-id="5bfe1-133">确保您要汇总的表已经包含在“关系图”窗格中。</span><span class="sxs-lookup"><span data-stu-id="5bfe1-133">Be sure the table you want to summarize is already present in the Diagram pane.</span></span>  
  
2.  <span data-ttu-id="5bfe1-134">右键单击“关系图”窗格的背景，再从快捷菜单中选择“添加分组依据”  。</span><span class="sxs-lookup"><span data-stu-id="5bfe1-134">Right-click the background of the Diagram pane, then choose **Add Group By** from the shortcut menu.</span></span> <span data-ttu-id="5bfe1-135">查询和视图设计器会在“条件”窗格的网格中添加一个“分组依据”  列。</span><span class="sxs-lookup"><span data-stu-id="5bfe1-135">The Query and View Designer adds a **Group By** column to the grid in the Criteria pane.</span></span>  
  
3.  <span data-ttu-id="5bfe1-136">将要计数的列添加到“条件”窗格中。</span><span class="sxs-lookup"><span data-stu-id="5bfe1-136">Add the column that you want to count to the Criteria pane.</span></span>  
  
     <span data-ttu-id="5bfe1-137">查询和视图设计器会自动在网格的“分组依据”列中填充 **Group By** 一词。</span><span class="sxs-lookup"><span data-stu-id="5bfe1-137">The Query and View Designer automatically fills the term **Group By** into the **Group By** column of the grid.</span></span>  
  
4.  <span data-ttu-id="5bfe1-138">将“分组依据”列中的 **Group By** 改为 **Count**。</span><span class="sxs-lookup"><span data-stu-id="5bfe1-138">Change **Group By** in the **Group By** column to **Count**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5bfe1-139">若要只计算唯一值的数目，请选择 **Count Distinct**。</span><span class="sxs-lookup"><span data-stu-id="5bfe1-139">To count only unique values, choose **Count Distinct**.</span></span>  
  
5.  <span data-ttu-id="5bfe1-140">运行查询。</span><span class="sxs-lookup"><span data-stu-id="5bfe1-140">Run the query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bfe1-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5bfe1-141">See Also</span></span>  
 <span data-ttu-id="5bfe1-142">[对查询结果进行排序和分组 &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="5bfe1-142">[Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="5bfe1-143">汇总查询结果 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="5bfe1-143">Summarize Query Results &#40;Visual Database Tools&#41;</span></span>](summarize-query-results-visual-database-tools.md)  
  
  
