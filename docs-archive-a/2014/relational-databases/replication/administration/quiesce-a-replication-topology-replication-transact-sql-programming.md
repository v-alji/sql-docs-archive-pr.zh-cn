---
title: 停止复制拓扑（复制 Transact-SQL 编程）| Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- administering replication, quiescing
- quiesce [SQL Server replication]
- transactional replication, backup and restore
ms.assetid: 7626d575-9994-47be-b772-5b6f1b7ef7ca
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f12f0fb8ee3a6118e03799d17836573fb5c733df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691695"
---
# <a name="quiesce-a-replication-topology-replication-transact-sql-programming"></a><span data-ttu-id="18838-102">静止复制拓扑（复制 Transact-SQL 编程）</span><span class="sxs-lookup"><span data-stu-id="18838-102">Quiesce a Replication Topology (Replication Transact-SQL Programming)</span></span>
  <span data-ttu-id="18838-103">“停止”系统，需要停止所有节点上已发布表的操作，并确保每个节点都已收到来自所有其他节点的所有更改\*\*。</span><span class="sxs-lookup"><span data-stu-id="18838-103">*Quiescing* a system involves stopping activity on published tables at all nodes and ensuring that each node has received all changes from all other nodes.</span></span> <span data-ttu-id="18838-104">本主题说明了如何停止复制拓扑（这是许多管理任务所必需的操作），以及如何确保节点收到来自其他节点的全部更改。</span><span class="sxs-lookup"><span data-stu-id="18838-104">This topic explains how to quiesce a replication topology, which is required for a number of administrative tasks, and how to ensure that a node has received all changes from other nodes.</span></span>  
  
### <a name="to-quiesce-a-transactional-replication-topology-with-read-only-subscriptions"></a><span data-ttu-id="18838-105">停止包含只读订阅的事务复制拓扑</span><span class="sxs-lookup"><span data-stu-id="18838-105">To quiesce a transactional replication topology with read-only subscriptions</span></span>  
  
1.  <span data-ttu-id="18838-106">停止发布服务器上所有已发布表中的活动。</span><span class="sxs-lookup"><span data-stu-id="18838-106">Stop activity on all published tables at the Publisher.</span></span>  
  
2.  <span data-ttu-id="18838-107">在发布服务器的发布数据库中，执行 [sp_posttracertoken (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-posttracertoken-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="18838-107">At the Publisher on the publication database, execute [sp_posttracertoken &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-posttracertoken-transact-sql).</span></span>  
  
3.  <span data-ttu-id="18838-108">在发布服务器的发布数据库中，执行 [sp_helptracertokenhistory](/sql/relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="18838-108">At the Publisher on the publication database, execute [sp_helptracertokenhistory](/sql/relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql).</span></span>  
  
4.  <span data-ttu-id="18838-109">确保每个订阅服务器已收到跟踪令牌。</span><span class="sxs-lookup"><span data-stu-id="18838-109">Ensure that each Subscriber has received the tracer token.</span></span>  
  
### <a name="to-quiesce-a-transactional-replication-topology-with-updatable-subscriptions"></a><span data-ttu-id="18838-110">停止包含可更新订阅的事务复制拓扑</span><span class="sxs-lookup"><span data-stu-id="18838-110">To quiesce a transactional replication topology with updatable subscriptions</span></span>  
  
1.  <span data-ttu-id="18838-111">停止发布服务器和所有订阅服务器上所有已发布表中的活动。</span><span class="sxs-lookup"><span data-stu-id="18838-111">Stop activity on all published tables at the Publisher and all Subscribers.</span></span>  
  
2.  <span data-ttu-id="18838-112">如果任何订阅服务器使用排队更新订阅：</span><span class="sxs-lookup"><span data-stu-id="18838-112">If any Subscribers use queued updating subscriptions:</span></span>  
  
    1.  <span data-ttu-id="18838-113">如果队列读取器代理未以连续模式运行，请运行该代理。</span><span class="sxs-lookup"><span data-stu-id="18838-113">If the Queue Reader Agent is not running in continuous mode, run the agent.</span></span> <span data-ttu-id="18838-114">有关运行代理的详细信息，请参阅[复制代理可执行文件概念](../concepts/replication-agent-executables-concepts.md)或[启动和停止复制代理 (SQL Server Management Studio)](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="18838-114">For more information about running agents, see [Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md) or [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).</span></span>  
  
    2.  <span data-ttu-id="18838-115">若要验证队列是否为空，请在每个订阅服务器上执行 [sp_replqueuemonitor](/sql/relational-databases/system-stored-procedures/sp-replqueuemonitor-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="18838-115">To verify that the queue is empty, execute [sp_replqueuemonitor](/sql/relational-databases/system-stored-procedures/sp-replqueuemonitor-transact-sql) at each Subscriber.</span></span>  
  
3.  <span data-ttu-id="18838-116">在发布服务器的发布数据库中，执行 [sp_posttracertoken](/sql/relational-databases/system-stored-procedures/sp-posttracertoken-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="18838-116">At the Publisher on the publication database, execute [sp_posttracertoken](/sql/relational-databases/system-stored-procedures/sp-posttracertoken-transact-sql).</span></span>  
  
4.  <span data-ttu-id="18838-117">在发布服务器的发布数据库中，执行 [sp_helptracertokenhistory](/sql/relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="18838-117">At the Publisher on the publication database, execute [sp_helptracertokenhistory](/sql/relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql).</span></span>  
  
5.  <span data-ttu-id="18838-118">确保每个订阅服务器已收到跟踪令牌。</span><span class="sxs-lookup"><span data-stu-id="18838-118">Ensure that each Subscriber has received the tracer token.</span></span>  
  
### <a name="to-quiesce-a-peer-to-peer-transactional-replication-topology"></a><span data-ttu-id="18838-119">停止对等事务复制拓扑</span><span class="sxs-lookup"><span data-stu-id="18838-119">To quiesce a peer-to-peer transactional replication topology</span></span>  
  
1.  <span data-ttu-id="18838-120">停止所有节点上所有已发布表中的活动。</span><span class="sxs-lookup"><span data-stu-id="18838-120">Stop activity on all published tables at all nodes.</span></span>  
  
2.  <span data-ttu-id="18838-121">对拓扑中每个发布数据库执行 [sp_requestpeerresponse](/sql/relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="18838-121">Execute [sp_requestpeerresponse](/sql/relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql) on each publication database in the topology.</span></span>  
  
3.  <span data-ttu-id="18838-122">如果日志读取器代理或分发代理未以连续模式运行，请运行该代理。</span><span class="sxs-lookup"><span data-stu-id="18838-122">If the Log Reader Agent or Distribution Agent is not running in continuous mode, run the agent.</span></span> <span data-ttu-id="18838-123">必须在启动分发代理之前启动日志读取器代理。</span><span class="sxs-lookup"><span data-stu-id="18838-123">The Log Reader Agent must be started before the Distribution Agent.</span></span> <span data-ttu-id="18838-124">有关运行代理的详细信息，请参阅[复制代理可执行文件概念](../concepts/replication-agent-executables-concepts.md)或[启动和停止复制代理 (SQL Server Management Studio)](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="18838-124">For more information about running agents, see [Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md) or [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).</span></span>  
  
4.  <span data-ttu-id="18838-125">对拓扑中每个发布数据库执行 [sp_helppeerresponses](/sql/relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="18838-125">Execute [sp_helppeerresponses](/sql/relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql) on each publication database in the topology.</span></span> <span data-ttu-id="18838-126">确保结果集包含来自所有其他节点的响应。</span><span class="sxs-lookup"><span data-stu-id="18838-126">Ensure that the result set contains responses from each of the other nodes.</span></span>  
  
### <a name="to-ensure-a-peer-to-peer-node-has-received-all-prior-changes"></a><span data-ttu-id="18838-127">确保对等节点已收到所有以前的更改</span><span class="sxs-lookup"><span data-stu-id="18838-127">To ensure a peer-to-peer node has received all prior changes</span></span>  
  
1.  <span data-ttu-id="18838-128">对要检查的节点上的发布数据库执行 [sp_requestpeerresponse](/sql/relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="18838-128">Execute [sp_requestpeerresponse](/sql/relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql) on the publication database at the node you are checking.</span></span>  
  
2.  <span data-ttu-id="18838-129">如果日志读取器代理或分发代理未以连续模式运行，请运行该代理。</span><span class="sxs-lookup"><span data-stu-id="18838-129">If the Log Reader Agent or Distribution Agent is not running in continuous mode, run the agent.</span></span> <span data-ttu-id="18838-130">必须在启动分发代理之前启动日志读取器代理。</span><span class="sxs-lookup"><span data-stu-id="18838-130">The Log Reader Agent must be started before the Distribution Agent.</span></span> <span data-ttu-id="18838-131">有关运行代理的详细信息，请参阅[复制代理可执行文件概念](../concepts/replication-agent-executables-concepts.md)或[启动和停止复制代理 (SQL Server Management Studio)](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="18838-131">For more information about running agents, see [Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md) or [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).</span></span>  
  
3.  <span data-ttu-id="18838-132">对要检查的节点上的发布数据库执行 [sp_helppeerresponses](/sql/relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="18838-132">Execute [sp_helppeerresponses](/sql/relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql) on the publication database at the node you are checking.</span></span> <span data-ttu-id="18838-133">确保结果集包含来自所有其他节点的响应。</span><span class="sxs-lookup"><span data-stu-id="18838-133">Ensure that the result set contains responses from each of the other nodes.</span></span>  
  
### <a name="to-quiesce-a-merge-replication-topology"></a><span data-ttu-id="18838-134">停止合并复制拓扑</span><span class="sxs-lookup"><span data-stu-id="18838-134">To quiesce a merge replication topology</span></span>  
  
1.  <span data-ttu-id="18838-135">停止发布服务器和所有订阅服务器上所有已发布表中的活动。</span><span class="sxs-lookup"><span data-stu-id="18838-135">Stop activity on all published tables at the Publisher and at all Subscribers.</span></span>  
  
2.  <span data-ttu-id="18838-136">为每个订阅运行两次合并代理：首先同步所有订阅，然后再同步每个订阅一次。</span><span class="sxs-lookup"><span data-stu-id="18838-136">Run the Merge Agent for each subscription two times: synchronize all subscriptions once and then synchronize each subscription a second time.</span></span> <span data-ttu-id="18838-137">这样可确保所有更改都复制到所有节点。</span><span class="sxs-lookup"><span data-stu-id="18838-137">This ensures that all changes are replicated to all nodes.</span></span> <span data-ttu-id="18838-138">有关运行代理的详细信息，请参阅[复制代理可执行文件概念](../concepts/replication-agent-executables-concepts.md)或[启动和停止复制代理 (SQL Server Management Studio)](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="18838-138">For more information about running agents, see [Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md) or [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="18838-139">如果同步过程中出现冲突，则运行合并代理两次之后冲突解决所需的更改可能不会传播到所有节点。</span><span class="sxs-lookup"><span data-stu-id="18838-139">If conflicts occur during synchronization, it is possible that changes required by conflict resolution will not be propagated to all nodes after running the Merge Agent two times.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18838-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="18838-140">See Also</span></span>  
 <span data-ttu-id="18838-141">[管理对等拓扑（复制 Transact-SQL 编程）](administer-a-peer-to-peer-topology-replication-transact-sql-programming.md) </span><span class="sxs-lookup"><span data-stu-id="18838-141">[Administer a Peer-to-Peer Topology &#40;Replication Transact-SQL Programming&#41;](administer-a-peer-to-peer-topology-replication-transact-sql-programming.md) </span></span>  
 [<span data-ttu-id="18838-142">为事务复制测量滞后时间和验证连接</span><span class="sxs-lookup"><span data-stu-id="18838-142">Measure Latency and Validate Connections for Transactional Replication</span></span>](../monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  
  
