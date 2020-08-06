---
title: 从查询结果中删除列 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- columns [SQL Server], deleting
- result sets [SQL Server], queries
- removing columns
- results [SQL Server], query
- deleting columns
- queries [SQL Server], results
ms.assetid: a7de7a87-4249-49bd-863d-dc0b40a49e78
author: stevestein
ms.author: sstein
ms.openlocfilehash: 90d502ad2cdb4c67d5d4f23f262b56cb17ea7519
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682574"
---
# <a name="remove-columns-from-query-results-visual-database-tools"></a><span data-ttu-id="15083-102">从查询结果中删除列 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="15083-102">Remove Columns from Query Results (Visual Database Tools)</span></span>
  <span data-ttu-id="15083-103">如果在“选择”查询中使用某列，但不希望在结果集中显示该列（即不希望它显示在查询的选择列表中），则可将其从输出中移除。</span><span class="sxs-lookup"><span data-stu-id="15083-103">If you are using a column in a Select query but do not want to display it in the result set (that is, you do not want it in the query's select list), you can remove it from output.</span></span> <span data-ttu-id="15083-104">从查询的输出中移除该列后，您仍可在搜索条件中使用它或将其用作排序字段。</span><span class="sxs-lookup"><span data-stu-id="15083-104">After you remove the column from the query's output, you can still use it in search conditions or as a sorting field.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="15083-105">如果希望从查询中完全删除某一列，请参阅 [从查询中删除列 (Visual Database Tools)](visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="15083-105">If you want to remove a column from the query altogether, see [Remove Columns from Queries &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
### <a name="to-remove-a-column-from-the-query-output"></a><span data-ttu-id="15083-106">从查询输出中移除列</span><span class="sxs-lookup"><span data-stu-id="15083-106">To remove a column from the query output</span></span>  
  
-   <span data-ttu-id="15083-107">在“条件”  窗格中，对于要删除的数据列，清除“输出”  列中的复选框。</span><span class="sxs-lookup"><span data-stu-id="15083-107">In the **Criteria Pane**, clear the check box in the **Output** column for the data column you want to remove.</span></span> <span data-ttu-id="15083-108">（如果希望将该列添加回查询输出中，可再次选中“输出”  列。）</span><span class="sxs-lookup"><span data-stu-id="15083-108">(If you want to add the column back to the query output, you can check the **Output** column again.)</span></span>  
  
     <span data-ttu-id="15083-109">-或-</span><span class="sxs-lookup"><span data-stu-id="15083-109">-or-</span></span>  
  
-   <span data-ttu-id="15083-110">将该列从 [SQL 窗格](sql-pane-visual-database-tools.md)的输出列表中删除。</span><span class="sxs-lookup"><span data-stu-id="15083-110">Remove the column from the output list in the [SQL pane](sql-pane-visual-database-tools.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15083-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="15083-111">See Also</span></span>  
 <span data-ttu-id="15083-112">[在 Visual Database Tools &#40;向查询中添加列&#41;](add-columns-to-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="15083-112">[Add Columns to Queries &#40;Visual Database Tools&#41;](add-columns-to-queries-visual-database-tools.md) </span></span>  
 <span data-ttu-id="15083-113">[&#40;Visual Database Tools&#41;从查询中删除列](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="15083-113">[Remove Columns from Queries &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="15083-114">[对查询结果进行排序和分组 &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="15083-114">[Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span></span>  
 <span data-ttu-id="15083-115">[&#40;Visual Database Tools&#41;汇总查询结果](summarize-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="15083-115">[Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="15083-116">执行基本的查询操作 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="15083-116">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
