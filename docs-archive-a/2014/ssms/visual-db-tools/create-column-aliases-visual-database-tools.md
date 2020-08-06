---
title: 创建列别名 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- columns [SQL Server], aliases
- aliases [SQL Server], columns
ms.assetid: e2e1c166-8ea7-47a2-b6a7-e419bf0fa3bb
author: stevestein
ms.author: sstein
ms.openlocfilehash: febe7ed27ed10a283cab549bc65299577d69761c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579944"
---
# <a name="create-column-aliases-visual-database-tools"></a><span data-ttu-id="272e2-102">创建列别名 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="272e2-102">Create Column Aliases (Visual Database Tools)</span></span>
  <span data-ttu-id="272e2-103">您可为列名创建别名，以更方便地使用列名、计算和汇总值。</span><span class="sxs-lookup"><span data-stu-id="272e2-103">You can create aliases for column names to make it easier to work with column names, calculations, and summary values.</span></span> <span data-ttu-id="272e2-104">例如，您可以创建列别名以实现以下目的：</span><span class="sxs-lookup"><span data-stu-id="272e2-104">For example, you can create a column alias to:</span></span>  
  
-   <span data-ttu-id="272e2-105">为诸如 `(quantity * unit_price)` 之类的表达式或为聚合函数创建列名，如“Total Amount”。</span><span class="sxs-lookup"><span data-stu-id="272e2-105">Create a column name, such as "Total Amount," for an expression such as `(quantity * unit_price)` or for an aggregate function.</span></span>  
  
-   <span data-ttu-id="272e2-106">为列名创建简写形式，如用 `"d_id"` 代表 `"discounts.stor_id."`</span><span class="sxs-lookup"><span data-stu-id="272e2-106">Create a shortened form of a column name, such as `"d_id"` for `"discounts.stor_id."`</span></span>  
  
 <span data-ttu-id="272e2-107">定义列别名后，可在“选择”查询中使用该别名以指定查询输出。</span><span class="sxs-lookup"><span data-stu-id="272e2-107">After you have defined a column alias, you can use the alias in a Select query to specify query output.</span></span>  
  
### <a name="to-create-a-column-alias"></a><span data-ttu-id="272e2-108">创建列别名</span><span class="sxs-lookup"><span data-stu-id="272e2-108">To create a column alias</span></span>  
  
1.  <span data-ttu-id="272e2-109">在“条件”  窗格中，找到包含要为其创建别名的数据列的行，如果需要，还可将其标记为输出。</span><span class="sxs-lookup"><span data-stu-id="272e2-109">In the **Criteria Pane**, locate the row containing the data column for which you want to create an alias, and if necessary, mark it for output.</span></span> <span data-ttu-id="272e2-110">如果该数据列不在网格中，则将其添加到网格中。</span><span class="sxs-lookup"><span data-stu-id="272e2-110">If the data column is not already in the grid, add it.</span></span>  
  
2.  <span data-ttu-id="272e2-111">在该行的“别名”  列中，输入别名。</span><span class="sxs-lookup"><span data-stu-id="272e2-111">In the **Alias** column for that row, enter the alias.</span></span> <span data-ttu-id="272e2-112">别名必须遵循 SQL 的所有命名约定。</span><span class="sxs-lookup"><span data-stu-id="272e2-112">The alias must follow all naming conventions for SQL.</span></span> <span data-ttu-id="272e2-113">如果输入的别名包含空格，则查询和视图设计器将自动在其两旁放置分隔符。</span><span class="sxs-lookup"><span data-stu-id="272e2-113">If the alias name you enter contains spaces, the Query and View Designer automatically puts delimiters around it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="272e2-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="272e2-114">See Also</span></span>  
 <span data-ttu-id="272e2-115">[在 Visual Database Tools &#40;向查询中添加列&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="272e2-115">[Add Columns to Queries &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="272e2-116">[对查询结果进行排序和分组 &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="272e2-116">[Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span></span>  
 <span data-ttu-id="272e2-117">[&#40;Visual Database Tools&#41;汇总查询结果](summarize-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="272e2-117">[Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="272e2-118">执行基本的查询操作 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="272e2-118">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
