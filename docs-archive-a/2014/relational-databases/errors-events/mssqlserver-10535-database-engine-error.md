---
title: MSSQLSERVER_10535 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10535 (Database Engine error)
ms.assetid: 478fd978-11d9-4155-8329-f599fdbec14b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 439d282f18490a4353d6528276eaf7e4231c503b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689421"
---
# <a name="mssqlserver_10535"></a><span data-ttu-id="5ad6d-102">MSSQLSERVER_10535</span><span class="sxs-lookup"><span data-stu-id="5ad6d-102">MSSQLSERVER_10535</span></span>
    
## <a name="details"></a><span data-ttu-id="5ad6d-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="5ad6d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5ad6d-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="5ad6d-104">Product Name</span></span>|<span data-ttu-id="5ad6d-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="5ad6d-105">SQL Server</span></span>|  
|<span data-ttu-id="5ad6d-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="5ad6d-106">Event ID</span></span>|<span data-ttu-id="5ad6d-107">10535</span><span class="sxs-lookup"><span data-stu-id="5ad6d-107">10535</span></span>|  
|<span data-ttu-id="5ad6d-108">事件源</span><span class="sxs-lookup"><span data-stu-id="5ad6d-108">Event Source</span></span>|<span data-ttu-id="5ad6d-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="5ad6d-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="5ad6d-110">组件</span><span class="sxs-lookup"><span data-stu-id="5ad6d-110">Component</span></span>|<span data-ttu-id="5ad6d-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="5ad6d-111">SQLEngine</span></span>|  
|<span data-ttu-id="5ad6d-112">符号名称</span><span class="sxs-lookup"><span data-stu-id="5ad6d-112">Symbolic Name</span></span>|<span data-ttu-id="5ad6d-113">PG_NO_PLAN</span><span class="sxs-lookup"><span data-stu-id="5ad6d-113">PG_NO_PLAN</span></span>|  
|<span data-ttu-id="5ad6d-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="5ad6d-114">Message Text</span></span>|<span data-ttu-id="5ad6d-115">由于在计划缓存中找不到与指定计划句柄对应的计划，因此无法创建计划指南 '%.\*ls'。</span><span class="sxs-lookup"><span data-stu-id="5ad6d-115">Cannot create plan guide '%.\*ls' because a plan was not found in the plan cache that corresponds to the specified plan handle.</span></span> <span data-ttu-id="5ad6d-116">请指定已缓存的计划句柄。</span><span class="sxs-lookup"><span data-stu-id="5ad6d-116">Specify a cached plan handle.</span></span> <span data-ttu-id="5ad6d-117">有关已缓存的计划句柄的列表，请查询 sys.dm_exec_query_stats 动态管理视图。</span><span class="sxs-lookup"><span data-stu-id="5ad6d-117">For a list of cached plan handles, query the sys.dm_exec_query_stats dynamic management view.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5ad6d-118">说明</span><span class="sxs-lookup"><span data-stu-id="5ad6d-118">Explanation</span></span>  
 <span data-ttu-id="5ad6d-119">未在与指定的计划句柄相对应的计划缓存中找到计划。</span><span class="sxs-lookup"><span data-stu-id="5ad6d-119">A plan was not found in the plan cache that corresponds to the specified plan handle.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5ad6d-120">用户操作</span><span class="sxs-lookup"><span data-stu-id="5ad6d-120">User Action</span></span>  
 <span data-ttu-id="5ad6d-121">请指定已缓存的计划句柄。</span><span class="sxs-lookup"><span data-stu-id="5ad6d-121">Specify a cached plan handle.</span></span> <span data-ttu-id="5ad6d-122">有关已缓存的计划句柄的列表，请查询 sys.dm_exec_query_stats 动态管理视图。</span><span class="sxs-lookup"><span data-stu-id="5ad6d-122">For a list of cached plan handles, query the sys.dm_exec_query_stats dynamic management view.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ad6d-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5ad6d-123">See Also</span></span>  
 <span data-ttu-id="5ad6d-124">[sp_create_plan_guide_from_handle (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5ad6d-124">[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql) </span></span>  
 [<span data-ttu-id="5ad6d-125">sys.dm_exec_query_stats (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5ad6d-125">sys.dm_exec_query_stats &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql)  
  
  
