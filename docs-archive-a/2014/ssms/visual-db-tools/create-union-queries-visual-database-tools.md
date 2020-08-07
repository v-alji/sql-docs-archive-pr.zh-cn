---
title: 创建 UNION 查询 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- queries [SQL Server], types
- UNION queries
- Select query
- combining query results
- merged SELECT query [SQL Server]
ms.assetid: b5aafb1d-e4ed-4922-b790-56abc5ec551a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3c10f39c3e44844c4ec8a6a2328c41ea2de350d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587689"
---
# <a name="create-union-queries-visual-database-tools"></a><span data-ttu-id="82ad9-102">创建 UNION 查询 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="82ad9-102">Create UNION Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="82ad9-103">使用 UNION 关键字，可以在一个结果表中包含两个 SELECT 语句的结果。</span><span class="sxs-lookup"><span data-stu-id="82ad9-103">The UNION keyword enables you to include the results of two SELECT statements in one resulting table.</span></span> <span data-ttu-id="82ad9-104">任一 SELECT 语句返回的所有行都可合并到 UNION 表达式的结果中。</span><span class="sxs-lookup"><span data-stu-id="82ad9-104">All rows returned from either SELECT statement are combined into the result of the UNION expression.</span></span> <span data-ttu-id="82ad9-105">有关示例，请参阅[SELECT 示例 &#40;transact-sql&#41;](/sql/t-sql/queries/select-examples-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="82ad9-105">For examples, see [SELECT Examples &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-examples-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="82ad9-106">“关系图”窗格只能显示一个 SELECT 子句。</span><span class="sxs-lookup"><span data-stu-id="82ad9-106">The Diagram pane can only display one SELECT clause.</span></span> <span data-ttu-id="82ad9-107">因此，当使用 UNION 查询时，查询设计器将隐藏“表操作”窗格。</span><span class="sxs-lookup"><span data-stu-id="82ad9-107">Therefore, when you are working with a UNION query, Query Designer hides the Table Operations pane.</span></span>  
  
### <a name="to-create-a-merged-select-query"></a><span data-ttu-id="82ad9-108">创建合并的 SELECT 查询</span><span class="sxs-lookup"><span data-stu-id="82ad9-108">To create a Merged SELECT query</span></span>  
  
1.  <span data-ttu-id="82ad9-109">打开一个查询或创建一个新查询。</span><span class="sxs-lookup"><span data-stu-id="82ad9-109">Open a query or create a new one.</span></span>  
  
2.  <span data-ttu-id="82ad9-110">在 SQL 窗格中，键入有效的 UNION 表达式。</span><span class="sxs-lookup"><span data-stu-id="82ad9-110">In the SQL pane, type a valid UNION expression.</span></span>  
  
     <span data-ttu-id="82ad9-111">下面的示例是有效的 UNION 表达式。</span><span class="sxs-lookup"><span data-stu-id="82ad9-111">The following example is a valid UNION expression.</span></span>  
  
    ```  
    SELECT ProductModelID, Name  
    FROM Production.ProductModel  
    UNION  
    SELECT ProductModelID, Name   
    FROM dbo.Gloves;  
    ```  
  
3.  <span data-ttu-id="82ad9-112">在“查询设计器”  菜单中，单击“执行 SQL”  以运行该查询。</span><span class="sxs-lookup"><span data-stu-id="82ad9-112">On the **Query Designer** menu, click **Execute SQL** to run the query.</span></span>  
  
     <span data-ttu-id="82ad9-113">UNION 查询现在由查询设计器进行格式设置。</span><span class="sxs-lookup"><span data-stu-id="82ad9-113">Your UNION query is now formatted by Query Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82ad9-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="82ad9-114">See Also</span></span>  
 <span data-ttu-id="82ad9-115">[Visual Database Tools &#40;支持的查询类型&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="82ad9-115">[Supported Query Types &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="82ad9-116">[&#40;Visual Database Tools 的设计查询和视图操作指南主题&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="82ad9-116">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span></span>  
 <span data-ttu-id="82ad9-117">[在 Visual Database Tools &#40;执行基本的查询操作&#41;](perform-basic-operations-with-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="82ad9-117">[Perform Basic Operations with Queries &#40;Visual Database Tools&#41;](perform-basic-operations-with-queries-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="82ad9-118">UNION (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="82ad9-118">UNION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/set-operators-union-transact-sql)  
  
  
