---
title: 创建全文搜索查询 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- CONTAINS predicate (Transact-SQL)
- queries [full-text search], creating
- full-text queries [SQL Server], creating
ms.assetid: 537fa556-390e-4c88-9b8e-679848d94abc
author: stevestein
ms.author: sstein
ms.openlocfilehash: f84ab465da0a1b7ac1da1211de1d5199fd28ee95
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689218"
---
# <a name="create-full-text-search-queries-visual-database-tools"></a><span data-ttu-id="d1737-102">创建全文搜索查询 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="d1737-102">Create Full-Text Search Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="d1737-103">全文搜索使用 CONTAINS 谓词来查找在给定列中包含指定文本的行。</span><span class="sxs-lookup"><span data-stu-id="d1737-103">Full-text searches use the CONTAINS predicate to locate rows that have specified text in a given column.</span></span> <span data-ttu-id="d1737-104">全文搜索仅适用于具有活动的全文索引的列。</span><span class="sxs-lookup"><span data-stu-id="d1737-104">Full-Text searches are only possible on columns that have active full-text indexes.</span></span> <span data-ttu-id="d1737-105">如果试图将 CONTAINS 子句用于不具有当前活动的全文索引的列，则将收到错误。</span><span class="sxs-lookup"><span data-stu-id="d1737-105">If you attempt to use the CONTAINS clause on a column that does not have a currently active full-text index, you will receive an error.</span></span> <span data-ttu-id="d1737-106">有关全文索引和 CONTAINS 子句的详细信息，请参阅[全文搜索](../../relational-databases/search/full-text-search.md)和[包含 &#40;transact-sql&#41;](/sql/t-sql/queries/contains-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="d1737-106">For more information on full-text indexes and the CONTAINS clause, see [Full-Text Search](../../relational-databases/search/full-text-search.md) and [CONTAINS &#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql).</span></span>  
  
### <a name="to-create-a-full-text-search-query"></a><span data-ttu-id="d1737-107">创建全文搜索查询</span><span class="sxs-lookup"><span data-stu-id="d1737-107">To create a full-text search query</span></span>  
  
1.  <span data-ttu-id="d1737-108">在解决方案资源管理器中打开一个查询或创建新的查询。</span><span class="sxs-lookup"><span data-stu-id="d1737-108">Open a query from Solution Explorer or create a new one.</span></span>  
  
2.  <span data-ttu-id="d1737-109">在该查询的 WHERE 子句中，用 CONTAINS 函数来搜索全文本列。</span><span class="sxs-lookup"><span data-stu-id="d1737-109">In the WHERE clause of your query, use the CONTAINS function to search a full-text column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1737-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d1737-110">See Also</span></span>  
 <span data-ttu-id="d1737-111">[Visual Database Tools &#40;支持的查询类型&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="d1737-111">[Supported Query Types &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="d1737-112">[&#40;Visual Database Tools 的设计查询和视图操作指南主题&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="d1737-112">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="d1737-113">执行基本的查询操作 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="d1737-113">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
