---
title: 从查询中删除列 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- removing columns
- queries [SQL Server], columns
- deleting columns
- dropping columns
ms.assetid: 6d9819b8-ee2f-4838-9713-c5e3ad37ab46
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8532f5240729a2516a0c07ae943dd42dc01d9c1c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691009"
---
# <a name="remove-columns-from-queries-visual-database-tools"></a><span data-ttu-id="892a4-102">从查询中删除列 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="892a4-102">Remove Columns from Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="892a4-103">如果不希望再在查询中使用某列，则可以可移除该列。</span><span class="sxs-lookup"><span data-stu-id="892a4-103">If you no longer want to use a column in a query, you can remove it.</span></span> <span data-ttu-id="892a4-104">如果执行此操作，“查询和视图设计器”将从选择列表、排序规范、搜索条件、“SQL”窗格  以及所有分组规范中删除对该列的引用。</span><span class="sxs-lookup"><span data-stu-id="892a4-104">If you do, the Query and View Designer removes references to the column in the select list, the sort specification, the search criteria, **SQL Pane**, and any grouping specifications.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="892a4-105">如果只希望从“选择”查询的输出中移除某列，则可以直接从输出中移除该列，而不必同时从查询中移除该列。</span><span class="sxs-lookup"><span data-stu-id="892a4-105">If you want to remove a column from just the output of a Select query, you can do so without removing it from the query altogether.</span></span> <span data-ttu-id="892a4-106">有关详细信息，请参阅[从查询结果中删除列 (Visual Database Tools)](visual-database-tools.md)</span><span class="sxs-lookup"><span data-stu-id="892a4-106">For details, see [Remove Columns from Query Results &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
### <a name="to-remove-a-column-from-the-query"></a><span data-ttu-id="892a4-107">从查询中移除列</span><span class="sxs-lookup"><span data-stu-id="892a4-107">To remove a column from the query</span></span>  
  
-   <span data-ttu-id="892a4-108">在“条件”  窗格中，选择包含要移除的列的网格行，然后按 Delete。</span><span class="sxs-lookup"><span data-stu-id="892a4-108">In the **Criteria Pane**, select the grid row containing the column you want to remove and then press DELETE.</span></span>  
  
     <span data-ttu-id="892a4-109">-或-</span><span class="sxs-lookup"><span data-stu-id="892a4-109">-or-</span></span>  
  
-   <span data-ttu-id="892a4-110">在 [“SQL”窗格](sql-pane-visual-database-tools.md)中移除对该列的所有引用。</span><span class="sxs-lookup"><span data-stu-id="892a4-110">Remove all references to the column in the [SQL Pane](sql-pane-visual-database-tools.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="892a4-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="892a4-111">See Also</span></span>  
 <span data-ttu-id="892a4-112">[在 Visual Database Tools &#40;向查询中添加列&#41;](add-columns-to-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="892a4-112">[Add Columns to Queries &#40;Visual Database Tools&#41;](add-columns-to-queries-visual-database-tools.md) </span></span>  
 <span data-ttu-id="892a4-113">[对查询结果进行排序和分组 &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="892a4-113">[Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span></span>  
 <span data-ttu-id="892a4-114">[&#40;Visual Database Tools&#41;汇总查询结果](summarize-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="892a4-114">[Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="892a4-115">执行基本的查询操作 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="892a4-115">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
