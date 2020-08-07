---
title: MSSQLSERVER_8621 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8621 (Database Engine error)
ms.assetid: 67f59865-becd-4999-8bb0-90aedd7effbf
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 48c36cf936475e3deea37a172c7dc59f88d0a31a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588556"
---
# <a name="mssqlserver_8621"></a><span data-ttu-id="69003-102">MSSQLSERVER_8621</span><span class="sxs-lookup"><span data-stu-id="69003-102">MSSQLSERVER_8621</span></span>
    
## <a name="details"></a><span data-ttu-id="69003-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="69003-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="69003-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="69003-104">Product Name</span></span>|<span data-ttu-id="69003-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="69003-105">SQL Server</span></span>|  
|<span data-ttu-id="69003-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="69003-106">Event ID</span></span>|<span data-ttu-id="69003-107">8621</span><span class="sxs-lookup"><span data-stu-id="69003-107">8621</span></span>|  
|<span data-ttu-id="69003-108">事件源</span><span class="sxs-lookup"><span data-stu-id="69003-108">Event Source</span></span>|<span data-ttu-id="69003-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="69003-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="69003-110">组件</span><span class="sxs-lookup"><span data-stu-id="69003-110">Component</span></span>|<span data-ttu-id="69003-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="69003-111">SQLEngine</span></span>|  
|<span data-ttu-id="69003-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="69003-112">Symbolic Name</span></span>|<span data-ttu-id="69003-113">OPTIMIZER_STACK_OVERFLOW_ERR</span><span class="sxs-lookup"><span data-stu-id="69003-113">OPTIMIZER_STACK_OVERFLOW_ERR</span></span>|  
|<span data-ttu-id="69003-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="69003-114">Message Text</span></span>|<span data-ttu-id="69003-115">查询处理器在优化查询时堆栈空间不足。</span><span class="sxs-lookup"><span data-stu-id="69003-115">The query processor ran out of stack space during query optimization.</span></span> <span data-ttu-id="69003-116">请简化查询。</span><span class="sxs-lookup"><span data-stu-id="69003-116">Please simplify the query.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="69003-117">说明</span><span class="sxs-lookup"><span data-stu-id="69003-117">Explanation</span></span>  
 <span data-ttu-id="69003-118">出错的最可能原因是扩展查询的大小。</span><span class="sxs-lookup"><span data-stu-id="69003-118">The size of the expanded query is the most likely cause of the error.</span></span> <span data-ttu-id="69003-119">在每个视图的定义、计算列、[!INCLUDE[tsql](../../includes/tsql-md.md)] 函数和它引用的公用表表达式以及级联操作（如更新辅助索引、视图和触发器）方面，扩展查询将替换原始查询。</span><span class="sxs-lookup"><span data-stu-id="69003-119">The expanded query substitutes into the original query the definitions of each of the views, computed columns, [!INCLUDE[tsql](../../includes/tsql-md.md)] functions, and common table expressions it references, as well as cascading actions like updating secondary indexes, views, and triggers.</span></span>  
  
 <span data-ttu-id="69003-120">很可能查询在某个维度中很大；例如，视图定义所引用的表数，或者很大的标量表达式。</span><span class="sxs-lookup"><span data-stu-id="69003-120">Most likely the query is large in some dimension; for example, the number of tables referenced by view definitions, or a very large scalar expression.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="69003-121">用户操作</span><span class="sxs-lookup"><span data-stu-id="69003-121">User Action</span></span>  
 <span data-ttu-id="69003-122">通过沿最大维度将该查询分解为多个查询，对其进行简化。</span><span class="sxs-lookup"><span data-stu-id="69003-122">Simplify the query by breaking the query into multiple queries along the largest dimension.</span></span> <span data-ttu-id="69003-123">首先删除实际上不需要的任何查询元素，然后尝试添加临时表并将该查询拆分为两个查询。</span><span class="sxs-lookup"><span data-stu-id="69003-123">First remove any query elements that are not really necessary, then try adding a temp table and splitting the query in two.</span></span>  <span data-ttu-id="69003-124">仅将查询的一部分移动到子查询、函数或公用表表达式是不够的，因为 [!INCLUDE[tsql](../../includes/tsql-md.md)] 编译器会将它们重新组合在一起。</span><span class="sxs-lookup"><span data-stu-id="69003-124">Merely moving a part of the query to a subquery, function, or common table expression is insufficient because they get recombined by the [!INCLUDE[tsql](../../includes/tsql-md.md)] compiler.</span></span>  
  
  
