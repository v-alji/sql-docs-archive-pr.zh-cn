---
title: 使用 ORDER BY 排序 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- ORDER BY clause [Visual Database Tools]
ms.assetid: 459f5640-8058-4c24-97e7-7bbd6168bc39
author: stevestein
ms.author: sstein
ms.openlocfilehash: 93bdb9ed01c7935c5b9dae543804fca758a9262d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692066"
---
# <a name="sort-with-order-by-visual-database-tools"></a><span data-ttu-id="7c3dd-102">使用 ORDER BY 排序 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="7c3dd-102">Sort with ORDER BY (Visual Database Tools)</span></span>
  <span data-ttu-id="7c3dd-103">可以使用 ORDER BY 子句按返回行中的一个或多个列对查询结果进行排序。</span><span class="sxs-lookup"><span data-stu-id="7c3dd-103">You can sort query results by one or more of the columns in the returned rows by using an ORDER BY clause.</span></span> <span data-ttu-id="7c3dd-104">通过选择“条件详细信息”窗格中的选项可以定义 ORDER BY 子句。</span><span class="sxs-lookup"><span data-stu-id="7c3dd-104">You can define an ORDER BY clause by choosing options in the Criteria Details pane.</span></span>  
  
### <a name="to-sort-a-query-using-an-order-by-clause"></a><span data-ttu-id="7c3dd-105">使用 ORDER BY 子句对查询进行排序</span><span class="sxs-lookup"><span data-stu-id="7c3dd-105">To sort a query using an ORDER BY clause</span></span>  
  
1.  <span data-ttu-id="7c3dd-106">打开一个查询或创建一个新查询。</span><span class="sxs-lookup"><span data-stu-id="7c3dd-106">Open a query or create a new one.</span></span>  
  
2.  <span data-ttu-id="7c3dd-107">在[“条件”窗格](visual-database-tools.md)中，单击与对查询结果进行排序所依据的列相对应的行的“排序类型”  列。</span><span class="sxs-lookup"><span data-stu-id="7c3dd-107">In the [Criteria Pane](visual-database-tools.md), click the **Sort Type** column for the row corresponding to the column that you want to use to sort your query results.</span></span>  
  
3.  <span data-ttu-id="7c3dd-108">从下拉列表中选择升序  或降序  。</span><span class="sxs-lookup"><span data-stu-id="7c3dd-108">Choose *Ascending* or *Descending* from the drop-down list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7c3dd-109">清除某列的“排序类型”  项将从 ORDER BY 子句中删除该列。</span><span class="sxs-lookup"><span data-stu-id="7c3dd-109">Clearing the **Sort Type** entry for a column removes that column from the ORDER BY clause.</span></span>  
  
 <span data-ttu-id="7c3dd-110">请注意，在“条件”窗格中操作时，查询的 UNION 子句将随之更改以反映最近执行的操作。</span><span class="sxs-lookup"><span data-stu-id="7c3dd-110">Notice that as you work in the Criteria pane, your query's UNION clause changes to match your most recent actions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7c3dd-111">按多列对结果进行排序时，可使用“排序顺序”  列指定要搜索的各列的相对顺序。</span><span class="sxs-lookup"><span data-stu-id="7c3dd-111">When sorting results by more than one column, specify the order in which columns are searched relative to each other by using the **Sort Order** column.</span></span> <span data-ttu-id="7c3dd-112">有关详细信息，请参阅**如何对查询中的多个列进行排序**。</span><span class="sxs-lookup"><span data-stu-id="7c3dd-112">For more information, see **How to: Sort Multiple Columns in Queries**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c3dd-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7c3dd-113">See Also</span></span>  
 <span data-ttu-id="7c3dd-114">[对查询结果进行排序和分组 &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="7c3dd-114">[Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span></span>  
 <span data-ttu-id="7c3dd-115">[&#40;Visual Database Tools&#41;汇总查询结果](summarize-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="7c3dd-115">[Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="7c3dd-116">设计查询和视图操作指南主题 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="7c3dd-116">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
