---
title: 参数查询 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- parameter queries [SQL Server]
ms.assetid: 4897c41a-324a-47b8-a30b-cbc9e9e19a8b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7f6fd94ef180a34ae91d52c213092898612dc77d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588193"
---
# <a name="parameter-queries-visual-database-tools"></a><span data-ttu-id="9426b-102">参数查询 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="9426b-102">Parameter Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="9426b-103">在某些情况下，您需要创建可以使用多次但每次使用不同值的查询。</span><span class="sxs-lookup"><span data-stu-id="9426b-103">In some cases you want to create a query that you can use many times, but with a different value each time.</span></span> <span data-ttu-id="9426b-104">例如，可能经常运行一个查询以查找某位作者编写的所有 `title_ids` 。</span><span class="sxs-lookup"><span data-stu-id="9426b-104">For example, you might frequently run a query to find all the `title_ids` written by one author.</span></span> <span data-ttu-id="9426b-105">可以为每次请求运行相同的查询，只是每次使用的作者 ID 或姓名不同。</span><span class="sxs-lookup"><span data-stu-id="9426b-105">You could run the same query for each request, except that the author's ID or name would be different each time.</span></span>  
  
 <span data-ttu-id="9426b-106">若要创建每次使用不同值的查询，可以在查询中使用参数。</span><span class="sxs-lookup"><span data-stu-id="9426b-106">To create a query that can have different values at different times, you use parameters in the query.</span></span> <span data-ttu-id="9426b-107">参数是在运行查询时提供的值的占位符。</span><span class="sxs-lookup"><span data-stu-id="9426b-107">A parameter is a placeholder for a value that is supplied when the query runs.</span></span> <span data-ttu-id="9426b-108">带有参数的 SQL 语句可能类似于以下形式，其中“?”表示代表作者 ID 的参数：</span><span class="sxs-lookup"><span data-stu-id="9426b-108">An SQL statement with a parameter might look like the following, where "?" represents the parameter for the author's ID:</span></span>  
  
```  
SELECT title_id  
FROM titleauthor  
WHERE (au_id = ?)  
```  
  
## <a name="where-you-can-use-parameters"></a><span data-ttu-id="9426b-109">可以使用参数的位置</span><span class="sxs-lookup"><span data-stu-id="9426b-109">Where You Can Use Parameters</span></span>  
 <span data-ttu-id="9426b-110">可以将参数用作文本值（文本值或数值）的占位符。</span><span class="sxs-lookup"><span data-stu-id="9426b-110">You can use parameters as placeholders for literal values - for either text or numeric values.</span></span> <span data-ttu-id="9426b-111">最常见的情况是，在单个行或组的搜索条件中（即在 SQL 语句的 WHERE 或 HAVING 子句中）使用参数作为占位符。</span><span class="sxs-lookup"><span data-stu-id="9426b-111">Most commonly, parameters are used as placeholders in search conditions for individual rows or for groups (that is, in the WHERE or HAVING clauses of an SQL statement).</span></span>  
  
 <span data-ttu-id="9426b-112">您可以在表达式中使用参数作为占位符。</span><span class="sxs-lookup"><span data-stu-id="9426b-112">You can use parameters as placeholders in expressions.</span></span> <span data-ttu-id="9426b-113">例如，可能希望在每次运行查询时，通过提供不同的折扣值来计算打折价格。</span><span class="sxs-lookup"><span data-stu-id="9426b-113">For example, you might want to calculate discounted prices by supplying a different discount value each time you run a query.</span></span> <span data-ttu-id="9426b-114">为此，可以指定以下表达式：</span><span class="sxs-lookup"><span data-stu-id="9426b-114">To do so, you could specify the following expression:</span></span>  
  
```  
(price * ?)  
```  
  
## <a name="specifying-unnamed-and-named-parameters"></a><span data-ttu-id="9426b-115">指定未命名参数和命名参数</span><span class="sxs-lookup"><span data-stu-id="9426b-115">Specifying Unnamed and Named Parameters</span></span>  
 <span data-ttu-id="9426b-116">可以指定两种类型的参数：未命名参数和命名参数。</span><span class="sxs-lookup"><span data-stu-id="9426b-116">You can specify two types of parameters: unnamed and named.</span></span> <span data-ttu-id="9426b-117">未命名参数是可放在查询中的任意位置的问号 (?)，用于提示输入值或以文本值替代。</span><span class="sxs-lookup"><span data-stu-id="9426b-117">An unnamed parameter is a question mark (?) that you put anywhere in the query that you want to prompt for or substitute a literal value.</span></span> <span data-ttu-id="9426b-118">例如，如果在 `titleauthor` 表中使用未命名参数搜索某个作者的 ID，则在 [SQL 窗格](visual-database-tools.md) 中生成的语句可能类似于以下形式：</span><span class="sxs-lookup"><span data-stu-id="9426b-118">For example, if you use an unnamed parameter to search for an author's id in the `titleauthor` table, the resulting statement in the [SQL Pane](visual-database-tools.md) might look like this:</span></span>  
  
```  
SELECT title_id  
FROM titleauthor  
WHERE (au_id = ?)  
```  
  
 <span data-ttu-id="9426b-119">在 [查询和视图设计器](query-and-view-designer-tools-visual-database-tools.md)中运行查询时，将显示带有“?”（作为参数名称）的 [查询参数对话框](query-parameters-dialog-box-visual-database-tools.md) 。</span><span class="sxs-lookup"><span data-stu-id="9426b-119">When you run the query in the [Query and View Designer](query-and-view-designer-tools-visual-database-tools.md), the [Query Parameters Dialog Box](query-parameters-dialog-box-visual-database-tools.md) appears with "?" as the name of the parameter.</span></span>  
  
 <span data-ttu-id="9426b-120">此外，您也可以为参数分配一个名称。</span><span class="sxs-lookup"><span data-stu-id="9426b-120">Alternatively, you can assign a name to a parameter.</span></span> <span data-ttu-id="9426b-121">如果查询中存在多个参数，此时命名参数将非常有用。</span><span class="sxs-lookup"><span data-stu-id="9426b-121">Named parameters are particularly useful if you have multiple parameters in a query.</span></span> <span data-ttu-id="9426b-122">例如，如果在 `authors` 表中使用命名参数搜索某作者的姓氏和名称，则在 SQL 窗格中生成的语句可能类似于以下形式：</span><span class="sxs-lookup"><span data-stu-id="9426b-122">For example, if you use named parameters to search for an author's first and last names in the `authors` table, the resulting statement in the SQL pane might look like this:</span></span>  
  
```  
SELECT au_id  
FROM authors  
WHERE au_fname = %first name% AND  
      au_lname = %last name%  
```  
  
> [!TIP]  
>  <span data-ttu-id="9426b-123">在创建命名参数查询之前，必须定义前缀和后缀字符。</span><span class="sxs-lookup"><span data-stu-id="9426b-123">You must define prefix and suffix characters before creating a named parameter query.</span></span>  
  
 <span data-ttu-id="9426b-124">在查询和视图设计器中运行查询时，将显示 [查询参数对话框](query-parameters-dialog-box-visual-database-tools.md) 和命名参数列表。</span><span class="sxs-lookup"><span data-stu-id="9426b-124">When you run the query in the Query and View Designer, the [Query Parameters Dialog Box](query-parameters-dialog-box-visual-database-tools.md) appears with a list of named parameters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9426b-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9426b-125">See Also</span></span>  
 <span data-ttu-id="9426b-126">[用参数查询 &#40;Visual Database Tools&#41;](query-with-parameters-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="9426b-126">[Query with Parameters &#40;Visual Database Tools&#41;](query-with-parameters-visual-database-tools.md) </span></span>  
 <span data-ttu-id="9426b-127">[Visual Database Tools &#40;支持的查询类型&#41;](supported-query-types-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="9426b-127">[Supported Query Types &#40;Visual Database Tools&#41;](supported-query-types-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="9426b-128">设计查询和视图操作指南主题 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="9426b-128">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
