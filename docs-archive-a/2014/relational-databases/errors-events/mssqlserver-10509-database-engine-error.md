---
title: MSSQLSERVER_10509 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10509 (Database Engine error)
ms.assetid: e9dd5357-ee3d-420a-9a89-d12ab5404e73
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 73194c7da553bf27acb78d8c4e7d71bc93f457d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693368"
---
# <a name="mssqlserver_10509"></a><span data-ttu-id="82661-102">MSSQLSERVER_10509</span><span class="sxs-lookup"><span data-stu-id="82661-102">MSSQLSERVER_10509</span></span>
    
## <a name="details"></a><span data-ttu-id="82661-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="82661-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="82661-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="82661-104">Product Name</span></span>|<span data-ttu-id="82661-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="82661-105">SQL Server</span></span>|  
|<span data-ttu-id="82661-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="82661-106">Event ID</span></span>|<span data-ttu-id="82661-107">10509</span><span class="sxs-lookup"><span data-stu-id="82661-107">10509</span></span>|  
|<span data-ttu-id="82661-108">事件源</span><span class="sxs-lookup"><span data-stu-id="82661-108">Event Source</span></span>|<span data-ttu-id="82661-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="82661-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="82661-110">组件</span><span class="sxs-lookup"><span data-stu-id="82661-110">Component</span></span>|<span data-ttu-id="82661-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="82661-111">SQLEngine</span></span>|  
|<span data-ttu-id="82661-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="82661-112">Symbolic Name</span></span>|<span data-ttu-id="82661-113">PG_INVALID_STMT</span><span class="sxs-lookup"><span data-stu-id="82661-113">PG_INVALID_STMT</span></span>|  
|<span data-ttu-id="82661-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="82661-114">Message Text</span></span>|<span data-ttu-id="82661-115">无法创建计划指南 '%.\*ls'，因为 `@stmt` 或 `@statement_start_offset` 指定的语句包含语法错误或者无法在计划指南中使用。</span><span class="sxs-lookup"><span data-stu-id="82661-115">Cannot create plan guide '%.\*ls' because the statement specified by `@stmt` or `@statement_start_offset` either contains a syntax error or is ineligible for use in a plan guide.</span></span> <span data-ttu-id="82661-116">请提供一个有效的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句或者该语句在批中的有效起始位置。</span><span class="sxs-lookup"><span data-stu-id="82661-116">Provide a single valid [!INCLUDE[tsql](../../includes/tsql-md.md)] statement or a valid starting position of the statement within the batch.</span></span> <span data-ttu-id="82661-117">若要获取有效的起始位置，请在 sys.dm_exec_query_stats 动态管理函数中查询 statement_start_offset 列。</span><span class="sxs-lookup"><span data-stu-id="82661-117">To obtain a valid starting position, query the statement_start_offset column in the sys.dm_exec_query_stats dynamic management function.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="82661-118">说明</span><span class="sxs-lookup"><span data-stu-id="82661-118">Explanation</span></span>  
 <span data-ttu-id="82661-119">`@stmt` 或 `@statement_start_offset` 指定的语句包含语法错误或者无法在计划指南中使用。</span><span class="sxs-lookup"><span data-stu-id="82661-119">The statement specified by `@stmt` or `@statement_start_offset` either contains a syntax error or is ineligible for use in a plan guide.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="82661-120">用户操作</span><span class="sxs-lookup"><span data-stu-id="82661-120">User Action</span></span>  
 <span data-ttu-id="82661-121">请提供一个有效的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句或者该语句在批中的有效起始位置。</span><span class="sxs-lookup"><span data-stu-id="82661-121">Provide a single valid [!INCLUDE[tsql](../../includes/tsql-md.md)] statement or a valid starting position of the statement within the batch.</span></span> <span data-ttu-id="82661-122">若要获取有效的起始位置，请在 sys.dm_exec_query_stats 动态管理函数中查询 statement_start_offset 列。</span><span class="sxs-lookup"><span data-stu-id="82661-122">To obtain a valid starting position, query the statement_start_offset column in the sys.dm_exec_query_stats dynamic management function.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82661-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="82661-123">See Also</span></span>  
 <span data-ttu-id="82661-124">[sp_create_plan_guide (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="82661-124">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 <span data-ttu-id="82661-125">[计划指南](../performance/plan-guides.md) </span><span class="sxs-lookup"><span data-stu-id="82661-125">[Plan Guides](../performance/plan-guides.md) </span></span>  
 <span data-ttu-id="82661-126">[sys. dm_exec_query_stats &#40;Transact-sql&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="82661-126">[sys.dm_exec_query_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql) </span></span>  
 [<span data-ttu-id="82661-127">sp_create_plan_guide_from_handle (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="82661-127">sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
