---
title: “存储过程”事件类别 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Stored Procedures event category [SQL Server]
- SQL Server event classes, Stored Procedures event category
- event classes [SQL Server], Stored Procedures event category
ms.assetid: 71bebaa3-a05a-4695-b349-078cecd0949a
author: stevestein
ms.author: sstein
ms.openlocfilehash: df2e0d9a4c077ff16eba09bc5ebb6447d5d27595
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694481"
---
# <a name="stored-procedures-event-category"></a><span data-ttu-id="d50e2-102">Stored Procedures 事件类别</span><span class="sxs-lookup"><span data-stu-id="d50e2-102">Stored Procedures Event Category</span></span>
  <span data-ttu-id="d50e2-103">**Stored Procedures** 事件类别包含一般的存储过程事件。</span><span class="sxs-lookup"><span data-stu-id="d50e2-103">The **Stored Procedures** event category contains general stored procedure events.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d50e2-104">本节内容</span><span class="sxs-lookup"><span data-stu-id="d50e2-104">In This Section</span></span>  
  
|<span data-ttu-id="d50e2-105">主题</span><span class="sxs-lookup"><span data-stu-id="d50e2-105">Topic</span></span>|<span data-ttu-id="d50e2-106">说明</span><span class="sxs-lookup"><span data-stu-id="d50e2-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="d50e2-107">RPC:Completed 事件类</span><span class="sxs-lookup"><span data-stu-id="d50e2-107">RPC:Completed Event Class</span></span>](rpc-completed-event-class.md)|<span data-ttu-id="d50e2-108">指示已完成远程过程调用 (RPC)。</span><span class="sxs-lookup"><span data-stu-id="d50e2-108">Indicates that a remote procedure call (RPC) has been completed.</span></span>|  
|[<span data-ttu-id="d50e2-109">PreConnect:Completed 事件类</span><span class="sxs-lookup"><span data-stu-id="d50e2-109">PreConnect:Completed Event Class</span></span>](preconnect-completed-event-class.md)|<span data-ttu-id="d50e2-110">指示何时资源调控器分类器函数结束执行。</span><span class="sxs-lookup"><span data-stu-id="d50e2-110">Indicates when the Resource Governor classifier function finishes execution.</span></span>|  
|[<span data-ttu-id="d50e2-111">PreConnect:Starting 事件类</span><span class="sxs-lookup"><span data-stu-id="d50e2-111">PreConnect:Starting Event Class</span></span>](preconnect-starting-event-class.md)|<span data-ttu-id="d50e2-112">指示何时资源调控器分类器函数开始执行。</span><span class="sxs-lookup"><span data-stu-id="d50e2-112">Indicates when the Resource Governor classifier function starts execution.</span></span>|  
|[<span data-ttu-id="d50e2-113">RPC Output Parameter 事件类</span><span class="sxs-lookup"><span data-stu-id="d50e2-113">RPC Output Parameter Event Class</span></span>](rpc-output-parameter-event-class.md)|<span data-ttu-id="d50e2-114">跟踪远程过程执行后调用的输出参数值。</span><span class="sxs-lookup"><span data-stu-id="d50e2-114">Traces the output parameter values of remote procedure calls after execution.</span></span>|  
|[<span data-ttu-id="d50e2-115">RPC:Starting 事件类</span><span class="sxs-lookup"><span data-stu-id="d50e2-115">RPC:Starting Event Class</span></span>](rpc-starting-event-class.md)|<span data-ttu-id="d50e2-116">指示正在启动远程过程调用。</span><span class="sxs-lookup"><span data-stu-id="d50e2-116">Indicates that a remote procedure call is starting.</span></span>|  
|[<span data-ttu-id="d50e2-117">SP:CacheHit 事件类</span><span class="sxs-lookup"><span data-stu-id="d50e2-117">SP:CacheHit Event Class</span></span>](sp-cachehit-event-class.md)|<span data-ttu-id="d50e2-118">指示存储过程位于缓存中。</span><span class="sxs-lookup"><span data-stu-id="d50e2-118">Indicates that the stored procedure is in the cache.</span></span>|  
|[<span data-ttu-id="d50e2-119">SP:CacheInsert 事件类</span><span class="sxs-lookup"><span data-stu-id="d50e2-119">SP:CacheInsert Event Class</span></span>](sp-cacheinsert-event-class.md)|<span data-ttu-id="d50e2-120">指示存储过程已载入缓存中。</span><span class="sxs-lookup"><span data-stu-id="d50e2-120">Indicates that the stored procedure has been brought into the cache.</span></span>|  
|[<span data-ttu-id="d50e2-121">SP:CacheMiss 事件类</span><span class="sxs-lookup"><span data-stu-id="d50e2-121">SP:CacheMiss Event Class</span></span>](sp-cachemiss-event-class.md)|<span data-ttu-id="d50e2-122">指示在缓存中未找到存储过程。</span><span class="sxs-lookup"><span data-stu-id="d50e2-122">Indicates that the stored procedure was not found in the cache.</span></span>|  
|[<span data-ttu-id="d50e2-123">SP:CacheRemove 事件类</span><span class="sxs-lookup"><span data-stu-id="d50e2-123">SP:CacheRemove Event Class</span></span>](sp-cacheremove-event-class.md)|<span data-ttu-id="d50e2-124">指示已从缓存中删除存储过程。</span><span class="sxs-lookup"><span data-stu-id="d50e2-124">Indicates that the stored procedure has been removed from the cache.</span></span>|  
|[<span data-ttu-id="d50e2-125">SP:Completed 事件类</span><span class="sxs-lookup"><span data-stu-id="d50e2-125">SP:Completed Event Class</span></span>](sp-completed-event-class.md)|<span data-ttu-id="d50e2-126">指示已完成存储过程的执行。</span><span class="sxs-lookup"><span data-stu-id="d50e2-126">Indicates that execution of the stored procedure has completed.</span></span>|  
|[<span data-ttu-id="d50e2-127">SP:Recompile 事件类</span><span class="sxs-lookup"><span data-stu-id="d50e2-127">SP:Recompile Event Class</span></span>](sp-recompile-event-class.md)|<span data-ttu-id="d50e2-128">指示已重新编写存储过程。</span><span class="sxs-lookup"><span data-stu-id="d50e2-128">Indicates that the stored procedure has been recompiled.</span></span>|  
|[<span data-ttu-id="d50e2-129">SP:Starting 事件类</span><span class="sxs-lookup"><span data-stu-id="d50e2-129">SP:Starting Event Class</span></span>](sp-starting-event-class.md)|<span data-ttu-id="d50e2-130">指示正在启动存储过程的执行。</span><span class="sxs-lookup"><span data-stu-id="d50e2-130">Indicates that execution of the stored procedure is starting.</span></span>|  
|[<span data-ttu-id="d50e2-131">SP:StmtCompleted 事件类</span><span class="sxs-lookup"><span data-stu-id="d50e2-131">SP:StmtCompleted Event Class</span></span>](sp-stmtcompleted-event-class.md)|<span data-ttu-id="d50e2-132">指示已完成存储过程中的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="d50e2-132">Indicates that a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement within a stored procedure has completed.</span></span>|  
|[<span data-ttu-id="d50e2-133">SP:StmtStarting 事件类</span><span class="sxs-lookup"><span data-stu-id="d50e2-133">SP:StmtStarting Event Class</span></span>](sp-stmtstarting-event-class.md)|<span data-ttu-id="d50e2-134">指示已启动存储过程中的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="d50e2-134">Indicates that a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement within a stored procedure has started.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d50e2-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d50e2-135">See Also</span></span>  
 <span data-ttu-id="d50e2-136">[扩展事件](../extended-events/extended-events.md) </span><span class="sxs-lookup"><span data-stu-id="d50e2-136">[Extended Events](../extended-events/extended-events.md) </span></span>  
 [<span data-ttu-id="d50e2-137">sp_trace_setevent (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="d50e2-137">sp_trace_setevent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
