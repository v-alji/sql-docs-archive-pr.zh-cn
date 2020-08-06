---
title: 识别瓶颈 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- resource bottlenecks [SQL Server]
- database monitoring [SQL Server], bottlenecks
- performance [SQL Server], bottlenecks
- tuning databases [SQL Server], bottlenecks
- monitoring server performance [SQL Server], bottlenecks
- monitoring performance [SQL Server], bottlenecks
- database performance [SQL Server], bottlenecks
- server performance [SQL Server], bottlenecks
- bottlenecks [SQL Server]
- identifying bottlenecks [SQL Server]
ms.assetid: db079e65-ee80-4105-aec9-f8230d0d6635
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e941b3f4a1185177cef007eb6a02a71ae1adece7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687784"
---
# <a name="identify-bottlenecks"></a><span data-ttu-id="fcfd0-102">识别瓶颈</span><span class="sxs-lookup"><span data-stu-id="fcfd0-102">Identify Bottlenecks</span></span>
  <span data-ttu-id="fcfd0-103">对共享资源同时访问会导致瓶颈。</span><span class="sxs-lookup"><span data-stu-id="fcfd0-103">Simultaneous access to shared resources causes bottlenecks.</span></span> <span data-ttu-id="fcfd0-104">通常，每一软件系统都不可避免地存在瓶颈。</span><span class="sxs-lookup"><span data-stu-id="fcfd0-104">In general, bottlenecks are present in every software system and are inevitable.</span></span> <span data-ttu-id="fcfd0-105">然而，对共享资源的过多需求将导致响应时间过长，因此必须进行识别和优化。</span><span class="sxs-lookup"><span data-stu-id="fcfd0-105">However, excessive demands on shared resources cause poor response time and must be identified and tuned.</span></span>  
  
 <span data-ttu-id="fcfd0-106">导致瓶颈的原因包括：</span><span class="sxs-lookup"><span data-stu-id="fcfd0-106">Causes of bottlenecks include:</span></span>  
  
-   <span data-ttu-id="fcfd0-107">资源不足，需要添加或升级组件。</span><span class="sxs-lookup"><span data-stu-id="fcfd0-107">Insufficient resources, requiring additional or upgraded components.</span></span>  
  
-   <span data-ttu-id="fcfd0-108">工作负荷在同类资源之间分布不均（例如，一个磁盘被独占）。</span><span class="sxs-lookup"><span data-stu-id="fcfd0-108">Resources of the same type among which workloads are not distributed evenly; for example, one disk is being monopolized.</span></span>  
  
-   <span data-ttu-id="fcfd0-109">资源发生故障。</span><span class="sxs-lookup"><span data-stu-id="fcfd0-109">Malfunctioning resources.</span></span>  
  
-   <span data-ttu-id="fcfd0-110">资源配置不正确。</span><span class="sxs-lookup"><span data-stu-id="fcfd0-110">Incorrectly configured resources.</span></span>  
  
## <a name="analyzing-bottlenecks"></a><span data-ttu-id="fcfd0-111">分析瓶颈</span><span class="sxs-lookup"><span data-stu-id="fcfd0-111">Analyzing Bottlenecks</span></span>  
 <span data-ttu-id="fcfd0-112">如果有多个事件的持续时间都过长，则表明存在能被优化的瓶颈。</span><span class="sxs-lookup"><span data-stu-id="fcfd0-112">Excessive durations for various events are indicators of bottlenecks that can be tuned.</span></span>  
  
 <span data-ttu-id="fcfd0-113">例如：</span><span class="sxs-lookup"><span data-stu-id="fcfd0-113">For example:</span></span>  
  
-   <span data-ttu-id="fcfd0-114">当某项工作试图访问某个组件时，某些其他组件可能加以妨碍，从而延长完成该工作所需的时间。</span><span class="sxs-lookup"><span data-stu-id="fcfd0-114">Some other component may prevent the load from reaching this component thereby increasing the time to complete the load.</span></span>  
  
-   <span data-ttu-id="fcfd0-115">客户端请求可能因网络阻塞而花费更长时间。</span><span class="sxs-lookup"><span data-stu-id="fcfd0-115">Client requests may take longer due to network congestion.</span></span>  
  
 <span data-ttu-id="fcfd0-116">下面是跟踪服务器性能以识别瓶颈时应监视的五个主要方面。</span><span class="sxs-lookup"><span data-stu-id="fcfd0-116">Following are five key areas to monitor when tracking server performance to identify bottlenecks.</span></span>  
  
|<span data-ttu-id="fcfd0-117">可能的瓶颈方面</span><span class="sxs-lookup"><span data-stu-id="fcfd0-117">Possible bottleneck area</span></span>|<span data-ttu-id="fcfd0-118">对服务器的影响</span><span class="sxs-lookup"><span data-stu-id="fcfd0-118">Effects on the server</span></span>|  
|------------------------------|---------------------------|  
|<span data-ttu-id="fcfd0-119">内存使用率</span><span class="sxs-lookup"><span data-stu-id="fcfd0-119">Memory usage</span></span>|<span data-ttu-id="fcfd0-120">分配的内存不足或可由 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用的内存不足导致性能下降。</span><span class="sxs-lookup"><span data-stu-id="fcfd0-120">Insufficient memory allocated or available to Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] degrades performance.</span></span> <span data-ttu-id="fcfd0-121">数据必须从磁盘读取而非直接从数据缓存读取。</span><span class="sxs-lookup"><span data-stu-id="fcfd0-121">Data must be read from the disk rather than directly from the data cache.</span></span> <span data-ttu-id="fcfd0-122">当需要页时，Microsoft Windows 操作系统将通过与磁盘交换数据来执行大量分页操作。</span><span class="sxs-lookup"><span data-stu-id="fcfd0-122">Microsoft Windows operating systems perform excessive paging by swapping data to and from the disk as the pages are needed.</span></span>|  
|<span data-ttu-id="fcfd0-123">CPU 使用率</span><span class="sxs-lookup"><span data-stu-id="fcfd0-123">CPU utilization</span></span>|<span data-ttu-id="fcfd0-124">长期的高 CPU 使用率可能表明 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查询需要优化或 CPU 需要升级。</span><span class="sxs-lookup"><span data-stu-id="fcfd0-124">A chronically high CPU utilization rate may indicate that [!INCLUDE[tsql](../../includes/tsql-md.md)] queries need to be tuned or that a CPU upgrade is needed.</span></span>|  
|<span data-ttu-id="fcfd0-125">磁盘输入/输出 (I/O)</span><span class="sxs-lookup"><span data-stu-id="fcfd0-125">Disk input/output (I/O)</span></span>|[!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="fcfd0-126">可以优化查询以减少不必要的 I/O（例如，使用索引）。</span><span class="sxs-lookup"><span data-stu-id="fcfd0-126">queries can be tuned to reduce unnecessary I/O; for example, by employing indexes.</span></span>|  
|<span data-ttu-id="fcfd0-127">用户连接</span><span class="sxs-lookup"><span data-stu-id="fcfd0-127">User connections</span></span>|<span data-ttu-id="fcfd0-128">可能有太多用户同时访问服务器，从而导致性能下降。</span><span class="sxs-lookup"><span data-stu-id="fcfd0-128">Too many users may be accessing the server simultaneously causing performance degradation.</span></span>|  
|<span data-ttu-id="fcfd0-129">阻塞锁</span><span class="sxs-lookup"><span data-stu-id="fcfd0-129">Blocking locks</span></span>|<span data-ttu-id="fcfd0-130">应用程序设计不合理可能导致锁定或妨碍并发，因而导致更长的响应时间和更低的事务吞吐速度。</span><span class="sxs-lookup"><span data-stu-id="fcfd0-130">Incorrectly designed applications can cause locks and hamper concurrency, thus causing longer response times and lower transaction throughput rates.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fcfd0-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fcfd0-131">See Also</span></span>  
 <span data-ttu-id="fcfd0-132">[监视 CPU 使用率](../performance-monitor/monitor-cpu-usage.md) </span><span class="sxs-lookup"><span data-stu-id="fcfd0-132">[Monitor CPU Usage](../performance-monitor/monitor-cpu-usage.md) </span></span>  
 <span data-ttu-id="fcfd0-133">[监视磁盘使用情况](../performance-monitor/monitor-disk-usage.md) </span><span class="sxs-lookup"><span data-stu-id="fcfd0-133">[Monitor Disk Usage](../performance-monitor/monitor-disk-usage.md) </span></span>  
 <span data-ttu-id="fcfd0-134">[监视内存使用量](../performance-monitor/monitor-memory-usage.md) </span><span class="sxs-lookup"><span data-stu-id="fcfd0-134">[Monitor Memory Usage](../performance-monitor/monitor-memory-usage.md) </span></span>  
 <span data-ttu-id="fcfd0-135">[SQL Server General Statistics 对象](../performance-monitor/sql-server-general-statistics-object.md) </span><span class="sxs-lookup"><span data-stu-id="fcfd0-135">[SQL Server, General Statistics Object](../performance-monitor/sql-server-general-statistics-object.md) </span></span>  
 [<span data-ttu-id="fcfd0-136">SQL Server - Locks 对象</span><span class="sxs-lookup"><span data-stu-id="fcfd0-136">SQL Server, Locks Object</span></span>](../performance-monitor/sql-server-locks-object.md)  
  
  
