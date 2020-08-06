---
title: 汇总查询结果 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- summarizing query results
- queries [SQL Server], results
- aggregate queries [SQL Server]
ms.assetid: c9e15350-ed57-4d95-814d-815fbebfd86b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 08713be2d4439e520df07ec5efd6cb761a78a994
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691468"
---
# <a name="summarize-query-results-visual-database-tools"></a><span data-ttu-id="300d5-102">汇总查询结果 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="300d5-102">Summarize Query Results (Visual Database Tools)</span></span>
  <span data-ttu-id="300d5-103">当您创建聚合查询时，需要符合某些逻辑原则。</span><span class="sxs-lookup"><span data-stu-id="300d5-103">When you create aggregate queries, certain logical principles apply.</span></span> <span data-ttu-id="300d5-104">例如，在汇总查询中不能显示单个行的内容。</span><span class="sxs-lookup"><span data-stu-id="300d5-104">For example, you cannot display the contents of individual rows in a summary query.</span></span> <span data-ttu-id="300d5-105">查询和视图设计器可帮助你遵循 [“关系图”窗格](visual-database-tools.md) 和 [“条件”窗格](criteria-pane-visual-database-tools.md) 的行为原则。</span><span class="sxs-lookup"><span data-stu-id="300d5-105">The Query and View Designer helps you comply with these principles in the way the [Diagram pane](visual-database-tools.md) and [Criteria pane](criteria-pane-visual-database-tools.md) behave.</span></span>  
  
 <span data-ttu-id="300d5-106">通过理解聚合查询的原则以及查询和视图设计器的行为，可以创建逻辑关系正确的聚合查询。</span><span class="sxs-lookup"><span data-stu-id="300d5-106">By understanding the principles of aggregate queries and the Query and View Designer's behavior, you can create logically correct aggregate queries.</span></span> <span data-ttu-id="300d5-107">最重要的原则是聚合查询只能生成汇总信息。</span><span class="sxs-lookup"><span data-stu-id="300d5-107">The overriding principle is that aggregate queries can result only in summary information.</span></span> <span data-ttu-id="300d5-108">因此，以下大多数原则都介绍可以在聚合查询中引用单个数据列的方法。</span><span class="sxs-lookup"><span data-stu-id="300d5-108">Thus, most of the principles that follow describe the ways that you can reference individual data columns within an aggregate query.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="300d5-109">本节内容</span><span class="sxs-lookup"><span data-stu-id="300d5-109">In This Section</span></span>  
 [<span data-ttu-id="300d5-110">在聚合查询中使用列 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="300d5-110">Work with Columns in Aggregate Queries &#40;Visual Database Tools&#41;</span></span>](work-with-columns-in-aggregate-queries-visual-database-tools.md)  
 <span data-ttu-id="300d5-111">介绍有关使用 GROUP BY、WHERE 和 HAVING 子句对列进行分组和汇总的概念。</span><span class="sxs-lookup"><span data-stu-id="300d5-111">Describes concepts about grouping and summarizing columns with the GROUP BY, WHERE, and HAVING clauses.</span></span>  
  
 [<span data-ttu-id="300d5-112">计算表中的行数 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="300d5-112">Count Rows in a Table &#40;Visual Database Tools&#41;</span></span>](count-rows-in-a-table-visual-database-tools.md)  
 <span data-ttu-id="300d5-113">介绍计算表中行数或表中符合一组条件的行数的步骤。</span><span class="sxs-lookup"><span data-stu-id="300d5-113">Provides steps for counting the number of rows in a table or the number of rows in a table that meet a set of criteria.</span></span>  
  
 [<span data-ttu-id="300d5-114">汇总或聚合表中所有行的值 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="300d5-114">Summarize or Aggregate Values for All Rows in a Table &#40;Visual Database Tools&#41;</span></span>](summarize-or-aggregate-values-for-all-rows-in-a-table-visual-database-tools.md)  
 <span data-ttu-id="300d5-115">介绍汇总所有行而不是一些分组行的步骤。</span><span class="sxs-lookup"><span data-stu-id="300d5-115">Provides steps for summarizing all rows rather than for a set of grouped rows.</span></span>  
  
 [<span data-ttu-id="300d5-116">使用自定义表达式汇总或聚合值 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="300d5-116">Summarize or Aggregate Values Using Custom Expressions &#40;Visual Database Tools&#41;</span></span>](summarize-or-aggregate-values-using-custom-expressions-visual-database-tools.md)  
 <span data-ttu-id="300d5-117">介绍使用表达式而不是预定义子句进行汇总或聚合的步骤。</span><span class="sxs-lookup"><span data-stu-id="300d5-117">Provides steps for using expressions to summarize or aggregate rather than using the predefined clauses.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="300d5-118">相关章节</span><span class="sxs-lookup"><span data-stu-id="300d5-118">Related Sections</span></span>  
 [<span data-ttu-id="300d5-119">设计查询和视图操作指南主题 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="300d5-119">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
 <span data-ttu-id="300d5-120">提供指向介绍如何使用查询和视图设计器的主题的链接。</span><span class="sxs-lookup"><span data-stu-id="300d5-120">Provides links to topics covering how to use the Query and View Designer.</span></span>  
  
  
