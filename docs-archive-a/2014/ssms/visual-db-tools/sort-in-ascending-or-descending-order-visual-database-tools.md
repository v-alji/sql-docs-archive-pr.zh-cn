---
title: 按升序或降序进行排序 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- descending sorts
- ascending sorts
ms.assetid: d61cc55b-9ee8-4ecf-a32f-6459ae43910b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 67b5e6b00f62cfc297cc5930bc8cf3a41314a2f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590480"
---
# <a name="sort-in-ascending-or-descending-order-visual-database-tools"></a><span data-ttu-id="b4146-102">按升序或降序进行排序 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="b4146-102">Sort in Ascending or Descending Order (Visual Database Tools)</span></span>
  <span data-ttu-id="b4146-103">通过在 `ASC` 子句中使用 `DESC` 或 `ORDER BY` 关键字，可以按结果集中的一列或多列以升序或降序对查询结果进行排序。</span><span class="sxs-lookup"><span data-stu-id="b4146-103">You can sort query results in ascending or descending order on one or more of the columns in the result set by using the `ASC` or `DESC` keywords with the `ORDER BY` clause.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b4146-104">排序顺序在一定程度上由列的排序规则顺序来决定。</span><span class="sxs-lookup"><span data-stu-id="b4146-104">The sort order is determined in part by the column's collation sequence.</span></span> <span data-ttu-id="b4146-105">可以在 [“排序规则”对话框](visual-database-tools.md)中更改排序规则顺序。</span><span class="sxs-lookup"><span data-stu-id="b4146-105">You can change the collation sequence in the [Collation Dialog Box](visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="b4146-106">下面的过程假设您已在查询和视图设计器中打开了一个查询，该查询使用 ORDER BY 子句对一列或多列进行排序。</span><span class="sxs-lookup"><span data-stu-id="b4146-106">The following procedure assumes that you have a query open in Query and View Designer that uses the ORDER BY clause to sort one or more columns.</span></span>  
  
### <a name="to-specify-or-change-the-order-in-which-results-are-sorted"></a><span data-ttu-id="b4146-107">指定或更改结果的排序顺序</span><span class="sxs-lookup"><span data-stu-id="b4146-107">To specify or change the order in which results are sorted</span></span>  
  
1.  <span data-ttu-id="b4146-108">在[“条件”窗格](criteria-pane-visual-database-tools.md)中，单击要重新排序的列的“排序类型”  字段。</span><span class="sxs-lookup"><span data-stu-id="b4146-108">In the [Criteria pane](criteria-pane-visual-database-tools.md), click the **Sort Type** field for the column that you want to reorder.</span></span>  
  
2.  <span data-ttu-id="b4146-109">选择“升序”  或“降序”  以指定该列的排序顺序。</span><span class="sxs-lookup"><span data-stu-id="b4146-109">Choose **Ascending** or **Descending** to specify the sort order for the column.</span></span>  
  
 <span data-ttu-id="b4146-110">请注意，在“条件”窗格中操作时，查询的 UNION 子句将随之更改以反映最近执行的操作。</span><span class="sxs-lookup"><span data-stu-id="b4146-110">Notice that as you work in the Criteria pane, your query's UNION clause changes to match your most recent actions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b4146-111">按多列对结果进行排序时，可使用“排序顺序”列指定要搜索的各列的相对顺序。</span><span class="sxs-lookup"><span data-stu-id="b4146-111">When sorting results by more than one column, specify the order in which columns are searched relative to each other by using the Sort Order column.</span></span> <span data-ttu-id="b4146-112">有关详细信息，请参阅[对查询中的多个列进行排序 (Visual Database Tools)](sort-multiple-columns-in-queries-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="b4146-112">For more information, see [Sort Multiple Columns in Queries &#40;Visual Database Tools&#41;](sort-multiple-columns-in-queries-visual-database-tools.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4146-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b4146-113">See Also</span></span>  
 <span data-ttu-id="b4146-114">[对查询结果进行排序和分组 &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="b4146-114">[Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span></span>  
 <span data-ttu-id="b4146-115">[&#40;Visual Database Tools&#41;汇总查询结果](summarize-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="b4146-115">[Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="b4146-116">设计查询和视图操作指南主题 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="b4146-116">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
