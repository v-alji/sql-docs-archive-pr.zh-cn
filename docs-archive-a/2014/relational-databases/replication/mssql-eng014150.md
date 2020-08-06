---
title: MSSQL_ENG014150 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014150 error
ms.assetid: c3dd3109-abf3-4b38-a4e9-ef48d0235656
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4c926d05be9613ff559f119484fa5e238d71d861
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577556"
---
# <a name="mssql_eng014150"></a><span data-ttu-id="26b43-102">MSSQL_ENG014150</span><span class="sxs-lookup"><span data-stu-id="26b43-102">MSSQL_ENG014150</span></span>
    
## <a name="message-details"></a><span data-ttu-id="26b43-103">消息详细信息</span><span class="sxs-lookup"><span data-stu-id="26b43-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="26b43-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="26b43-104">Product Name</span></span>|<span data-ttu-id="26b43-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="26b43-105">SQL Server</span></span>|  
|<span data-ttu-id="26b43-106">事件 ID</span><span class="sxs-lookup"><span data-stu-id="26b43-106">Event ID</span></span>|<span data-ttu-id="26b43-107">14150</span><span class="sxs-lookup"><span data-stu-id="26b43-107">14150</span></span>|  
|<span data-ttu-id="26b43-108">事件源</span><span class="sxs-lookup"><span data-stu-id="26b43-108">Event Source</span></span>|<span data-ttu-id="26b43-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="26b43-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="26b43-110">组件</span><span class="sxs-lookup"><span data-stu-id="26b43-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="26b43-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="26b43-111">Symbolic Name</span></span>||  
|<span data-ttu-id="26b43-112">消息正文</span><span class="sxs-lookup"><span data-stu-id="26b43-112">Message Text</span></span>|<span data-ttu-id="26b43-113">复制 - %s：代理 %s 成功。</span><span class="sxs-lookup"><span data-stu-id="26b43-113">Replication-%s: agent %s succeeded.</span></span> <span data-ttu-id="26b43-114">%s</span><span class="sxs-lookup"><span data-stu-id="26b43-114">%s</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="26b43-115">说明</span><span class="sxs-lookup"><span data-stu-id="26b43-115">Explanation</span></span>  
 <span data-ttu-id="26b43-116">此消息指出复制代理已成功完成运行。</span><span class="sxs-lookup"><span data-stu-id="26b43-116">This message indicates that a replication agent has successfully finished running.</span></span> <span data-ttu-id="26b43-117">复制使用下列代理：</span><span class="sxs-lookup"><span data-stu-id="26b43-117">Replication uses the following agents:</span></span>  
  
-   <span data-ttu-id="26b43-118">快照代理。</span><span class="sxs-lookup"><span data-stu-id="26b43-118">The Snapshot Agent.</span></span> <span data-ttu-id="26b43-119">该代理由所有发布使用。</span><span class="sxs-lookup"><span data-stu-id="26b43-119">This agent is used by all publications.</span></span>  
  
-   <span data-ttu-id="26b43-120">日志读取器代理。</span><span class="sxs-lookup"><span data-stu-id="26b43-120">The Log Reader Agent.</span></span> <span data-ttu-id="26b43-121">该代理由所有事务发布使用。</span><span class="sxs-lookup"><span data-stu-id="26b43-121">This agent is used by all transactional publications.</span></span>  
  
-   <span data-ttu-id="26b43-122">队列读取器代理。</span><span class="sxs-lookup"><span data-stu-id="26b43-122">The Queue Reader Agent.</span></span> <span data-ttu-id="26b43-123">该代理由为排队更新订阅启用的事务发布使用。</span><span class="sxs-lookup"><span data-stu-id="26b43-123">This agent is used by transactional publications enabled for queued updating subscriptions.</span></span>  
  
-   <span data-ttu-id="26b43-124">分发代理。</span><span class="sxs-lookup"><span data-stu-id="26b43-124">The Distribution Agent.</span></span> <span data-ttu-id="26b43-125">该代理将订阅同步到事务发布和快照发布。</span><span class="sxs-lookup"><span data-stu-id="26b43-125">This agent synchronizes subscriptions to transactional and snapshot publications.</span></span>  
  
-   <span data-ttu-id="26b43-126">合并代理。</span><span class="sxs-lookup"><span data-stu-id="26b43-126">The Merge Agent.</span></span> <span data-ttu-id="26b43-127">该代理将订阅同步到合并发布。</span><span class="sxs-lookup"><span data-stu-id="26b43-127">This agent synchronizes subscriptions to merge publications.</span></span>  
  
-   <span data-ttu-id="26b43-128">复制维护作业。</span><span class="sxs-lookup"><span data-stu-id="26b43-128">Replication maintenance jobs.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="26b43-129">用户操作</span><span class="sxs-lookup"><span data-stu-id="26b43-129">User Action</span></span>  
 <span data-ttu-id="26b43-130">日志读取器代理、队列读取器代理和分发代理通常连续运行，而其他代理通常则按需要或按计划运行。</span><span class="sxs-lookup"><span data-stu-id="26b43-130">The Log Reader Agent, Queue Reader Agent, and Distribution Agent typically run continuously, whereas the other agents typically run on demand or on a schedule.</span></span> <span data-ttu-id="26b43-131">如果认为某个代理无法完成运行，请检查该代理的状态。</span><span class="sxs-lookup"><span data-stu-id="26b43-131">If you do not expect an agent to have completed a run, check the status of the agent.</span></span> <span data-ttu-id="26b43-132">有关详细信息，请参阅 [Monitor Replication Agents](agents/replication-agents-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="26b43-132">For more information, see [Monitor Replication Agents](agents/replication-agents-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26b43-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="26b43-133">See Also</span></span>  
 <span data-ttu-id="26b43-134">[复制代理管理](agents/replication-agent-administration.md) </span><span class="sxs-lookup"><span data-stu-id="26b43-134">[Replication Agent Administration](agents/replication-agent-administration.md) </span></span>  
 <span data-ttu-id="26b43-135">[错误和事件参考（复制）](errors-and-events-reference-replication.md) </span><span class="sxs-lookup"><span data-stu-id="26b43-135">[Errors and Events Reference &#40;Replication&#41;](errors-and-events-reference-replication.md) </span></span>  
 <span data-ttu-id="26b43-136">[Replication Distribution Agent](agents/replication-distribution-agent.md) </span><span class="sxs-lookup"><span data-stu-id="26b43-136">[Replication Distribution Agent](agents/replication-distribution-agent.md) </span></span>  
 <span data-ttu-id="26b43-137">[Replication Log Reader Agent](agents/replication-log-reader-agent.md) </span><span class="sxs-lookup"><span data-stu-id="26b43-137">[Replication Log Reader Agent](agents/replication-log-reader-agent.md) </span></span>  
 <span data-ttu-id="26b43-138">[Replication Merge Agent](agents/replication-merge-agent.md) </span><span class="sxs-lookup"><span data-stu-id="26b43-138">[Replication Merge Agent](agents/replication-merge-agent.md) </span></span>  
 <span data-ttu-id="26b43-139">[复制队列读取器代理](agents/replication-queue-reader-agent.md) </span><span class="sxs-lookup"><span data-stu-id="26b43-139">[Replication Queue Reader Agent](agents/replication-queue-reader-agent.md) </span></span>  
 [<span data-ttu-id="26b43-140">Replication Snapshot Agent</span><span class="sxs-lookup"><span data-stu-id="26b43-140">Replication Snapshot Agent</span></span>](agents/replication-snapshot-agent.md)  
  
  
