---
title: 对查询结果进行排序和分组 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- View Designer, Results pane
- result sets [SQL Server], queries
- queries [SQL Server], groups
- Query Designer [SQL Server], Results pane
- results [SQL Server], query
- grouping query results
- row sorting [SQL Server]
- queries [SQL Server], results
- ordering query results [SQL Server]
- Results pane
- sorting query results [SQL Server]
ms.assetid: b004e1c0-cacc-4241-9426-9fd426978918
author: stevestein
ms.author: sstein
ms.openlocfilehash: fdaede20960356404cd0319c213abb76a19b8a77
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682570"
---
# <a name="sort-and-group-query-results-visual-database-tools"></a><span data-ttu-id="c593e-102">对查询结果进行排序和分组 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="c593e-102">Sort and Group Query Results (Visual Database Tools)</span></span>
  <span data-ttu-id="c593e-103">您可以创建这样的一个查询结果，其中每个结果行都与来自原始数据的一整组行相对应。</span><span class="sxs-lookup"><span data-stu-id="c593e-103">You can create a query result in which each result row corresponds to an entire group of rows from the original data.</span></span>  
  
 <span data-ttu-id="c593e-104">若要了解有关创建这种查询的详细信息，请参阅下表中所列的主题：</span><span class="sxs-lookup"><span data-stu-id="c593e-104">To learn the details about creating such queries, see the topics listed in the following table.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c593e-105">本节内容</span><span class="sxs-lookup"><span data-stu-id="c593e-105">In This Section</span></span>  
 [<span data-ttu-id="c593e-106">对行进行排序 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="c593e-106">Sort Rows &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
 <span data-ttu-id="c593e-107">介绍各种对行进行排序的方法并解释为什么使用这些方法。</span><span class="sxs-lookup"><span data-stu-id="c593e-107">Describes the various ways in which you can sort rows and why you would use them.</span></span>  
  
 [<span data-ttu-id="c593e-108">折叠行组 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="c593e-108">Collapse Groups of Rows &#40;Visual Database Tools&#41;</span></span>](collapse-groups-of-rows-visual-database-tools.md)  
 <span data-ttu-id="c593e-109">介绍折叠行的各种方法，例如计算或消除重复项。</span><span class="sxs-lookup"><span data-stu-id="c593e-109">Describes the various ways to collapse rows, such as calculating or eliminating duplicates.</span></span>  
  
 [<span data-ttu-id="c593e-110">使用 ORDER BY 排序 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="c593e-110">Sort with ORDER BY &#40;Visual Database Tools&#41;</span></span>](sort-with-order-by-visual-database-tools.md)  
 <span data-ttu-id="c593e-111">介绍按指定顺序返回结果的步骤。</span><span class="sxs-lookup"><span data-stu-id="c593e-111">Provides steps for returning results in a specified order.</span></span>  
  
 [<span data-ttu-id="c593e-112">按升序或降序进行排序 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="c593e-112">Sort in Ascending or Descending Order &#40;Visual Database Tools&#41;</span></span>](sort-in-ascending-or-descending-order-visual-database-tools.md)  
 <span data-ttu-id="c593e-113">介绍更改或设置排序方向的步骤。</span><span class="sxs-lookup"><span data-stu-id="c593e-113">Provides steps for changing or setting sort direction.</span></span>  
  
 [<span data-ttu-id="c593e-114">对查询中的多个列进行排序 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="c593e-114">Sort Multiple Columns in Queries &#40;Visual Database Tools&#41;</span></span>](sort-multiple-columns-in-queries-visual-database-tools.md)  
 <span data-ttu-id="c593e-115">介绍设置多个列的结果集顺序的步骤。</span><span class="sxs-lookup"><span data-stu-id="c593e-115">Provides steps for setting the order of results sets for multiple columns.</span></span>  
  
 [<span data-ttu-id="c593e-116">对查询结果中的行进行分组 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="c593e-116">Group Rows in Query Results &#40;Visual Database Tools&#41;</span></span>](group-rows-in-query-results-visual-database-tools.md)  
 <span data-ttu-id="c593e-117">介绍通过将数据分组来创建摘要信息子集的步骤。</span><span class="sxs-lookup"><span data-stu-id="c593e-117">Provides steps for creating subsets of summary information by organizing data into groups.</span></span>  
  
 [<span data-ttu-id="c593e-118">为组指定条件 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="c593e-118">Specify Conditions for Groups &#40;Visual Database Tools&#41;</span></span>](specify-conditions-for-groups-visual-database-tools.md)  
 <span data-ttu-id="c593e-119">介绍创建适用于成组行的搜索条件的步骤。</span><span class="sxs-lookup"><span data-stu-id="c593e-119">Provides steps for creating search conditions that apply to groups of rows.</span></span>  
  
 [<span data-ttu-id="c593e-120">重新排列输出列 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="c593e-120">Reorder Output Columns &#40;Visual Database Tools&#41;</span></span>](reorder-output-columns-visual-database-tools.md)  
 <span data-ttu-id="c593e-121">介绍更改当前排序设置的步骤。</span><span class="sxs-lookup"><span data-stu-id="c593e-121">Provides steps for changing current sorting settings.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c593e-122">相关章节</span><span class="sxs-lookup"><span data-stu-id="c593e-122">Related Sections</span></span>  
 [<span data-ttu-id="c593e-123">汇总查询结果 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="c593e-123">Summarize Query Results &#40;Visual Database Tools&#41;</span></span>](summarize-query-results-visual-database-tools.md)  
 <span data-ttu-id="c593e-124">提供指向有关汇总查询结果的主题的链接。</span><span class="sxs-lookup"><span data-stu-id="c593e-124">Provides links to topics on summarizing query results.</span></span>  
  
 [<span data-ttu-id="c593e-125">执行基本的查询操作 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="c593e-125">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
 <span data-ttu-id="c593e-126">提供指向介绍最常见查询任务的主题的链接。</span><span class="sxs-lookup"><span data-stu-id="c593e-126">Provides links to topics covering the most common query tasks.</span></span>  
  
 [<span data-ttu-id="c593e-127">设计查询和视图操作指南主题 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="c593e-127">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
 <span data-ttu-id="c593e-128">提供指向介绍如何使用查询和视图设计器的主题的链接。</span><span class="sxs-lookup"><span data-stu-id="c593e-128">Provides links to topics covering how to use the Query and View Designer.</span></span>  
  
  
