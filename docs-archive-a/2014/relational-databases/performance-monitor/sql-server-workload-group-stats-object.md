---
title: SQL Server - Workload Group Stats 对象 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Workload Group Stats object
- 'SQLServer: Workload Group Stats'
ms.assetid: ca20e4f6-50ec-4456-900d-87d280fde2b3
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fb363803c562b305687e78e1315f1c4255041b1f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580215"
---
# <a name="sql-server-workload-group-stats-object"></a><span data-ttu-id="d4837-102">SQLServer，Workload Group Stats 对象</span><span class="sxs-lookup"><span data-stu-id="d4837-102">SQL Server, Workload Group Stats Object</span></span>
  <span data-ttu-id="d4837-103">SQLServer:Workload Group Stats 对象包含报告资源调控器工作负荷组统计相关信息的性能计数器。</span><span class="sxs-lookup"><span data-stu-id="d4837-103">The SQLServer:Workload Group Stats object contains performance counters that report information about Resource Governor workload group statistics.</span></span>  
  
 <span data-ttu-id="d4837-104">每个活动工作负荷组都创建一个 SQLServer:Workload Group Stats 性能对象实例，实例的名称与资源调控器工作负荷组的名称相同。</span><span class="sxs-lookup"><span data-stu-id="d4837-104">Each active workload group creates an instance of the SQLServer:Workload Group Stats performance object that has the same instance name as the Resource Governor workload group name.</span></span> <span data-ttu-id="d4837-105">下表介绍了此实例支持的计数器。</span><span class="sxs-lookup"><span data-stu-id="d4837-105">The following table describes counters supported on this instance.</span></span>  
  
|<span data-ttu-id="d4837-106">计数器名称</span><span class="sxs-lookup"><span data-stu-id="d4837-106">Counter name</span></span>|<span data-ttu-id="d4837-107">说明</span><span class="sxs-lookup"><span data-stu-id="d4837-107">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="d4837-108">Queued requests</span><span class="sxs-lookup"><span data-stu-id="d4837-108">Queued requests</span></span>|<span data-ttu-id="d4837-109">当前正在等待拾取的排队请求数。</span><span class="sxs-lookup"><span data-stu-id="d4837-109">The current number of queued requests that is waiting to be picked up.</span></span> <span data-ttu-id="d4837-110">如果达到 GROUP_MAX_REQUESTS 限制后操作中止，则此计数可为非零值。</span><span class="sxs-lookup"><span data-stu-id="d4837-110">This count can be non-zero if throttling occurs after the GROUP_MAX_REQUESTS limit is reached.</span></span>|  
|<span data-ttu-id="d4837-111">Active requests</span><span class="sxs-lookup"><span data-stu-id="d4837-111">Active requests</span></span>|<span data-ttu-id="d4837-112">此工作负荷组中当前运行的请求数。</span><span class="sxs-lookup"><span data-stu-id="d4837-112">The number of requests that are currently running in this workload group.</span></span> <span data-ttu-id="d4837-113">此值应该等于按组 ID 筛选的 sys.dm_exec_requests 的行数。</span><span class="sxs-lookup"><span data-stu-id="d4837-113">This should be equivalent to the count of rows from sys.dm_exec_requests filtered by group ID.</span></span>|  
|<span data-ttu-id="d4837-114">Requests completed/sec</span><span class="sxs-lookup"><span data-stu-id="d4837-114">Requests completed/sec</span></span>|<span data-ttu-id="d4837-115">此工作负荷组中已完成的请求数。</span><span class="sxs-lookup"><span data-stu-id="d4837-115">The number of requests that have completed in this workload group.</span></span> <span data-ttu-id="d4837-116">此数值可累计。</span><span class="sxs-lookup"><span data-stu-id="d4837-116">This number is cumulative.</span></span>|  
|<span data-ttu-id="d4837-117">CPU usage %</span><span class="sxs-lookup"><span data-stu-id="d4837-117">CPU usage %</span></span>|<span data-ttu-id="d4837-118">此工作负荷组中所有请求的 CPU 带宽使用量，该值是相对于计算机度量的，并且针对系统中的所有 CPU 进行规范化。</span><span class="sxs-lookup"><span data-stu-id="d4837-118">The CPU bandwidth usage by all requests in this workload group measured relative to the computer and normalized to all the CPUs on the system.</span></span> <span data-ttu-id="d4837-119">此值将随着可用于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 进程的 CPU 量的变化而变化。</span><span class="sxs-lookup"><span data-stu-id="d4837-119">This value will change as the amount of CPU available to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process changes.</span></span> <span data-ttu-id="d4837-120">它不会针对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 进程接收的信息进行规范化。</span><span class="sxs-lookup"><span data-stu-id="d4837-120">It is not normalized to what the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process receives.</span></span>|  
|<span data-ttu-id="d4837-121">Max request CPU time (ms)</span><span class="sxs-lookup"><span data-stu-id="d4837-121">Max request CPU time (ms)</span></span>|<span data-ttu-id="d4837-122">此工作负荷组中当前运行的请求所用的最长 CPU 时间，以毫秒为单位。</span><span class="sxs-lookup"><span data-stu-id="d4837-122">The maximum CPU time, in milliseconds, used by a request currently running in the workload group.</span></span>|  
|<span data-ttu-id="d4837-123">Blocked requests</span><span class="sxs-lookup"><span data-stu-id="d4837-123">Blocked requests</span></span>|<span data-ttu-id="d4837-124">工作负荷组中当前被禁止的请求数。</span><span class="sxs-lookup"><span data-stu-id="d4837-124">The current number of blocked requests in the workload group.</span></span> <span data-ttu-id="d4837-125">此值可用于确定工作负荷特征。</span><span class="sxs-lookup"><span data-stu-id="d4837-125">This can be used to determine workload characteristics.</span></span>|  
|<span data-ttu-id="d4837-126">Reduced memory grants/sec</span><span class="sxs-lookup"><span data-stu-id="d4837-126">Reduced memory grants/sec</span></span>|<span data-ttu-id="d4837-127">每秒所获内存量小于理想内存授予量的查询数。</span><span class="sxs-lookup"><span data-stu-id="d4837-127">The number of queries that are getting less than ideal amount of memory grants per second.</span></span>|  
|<span data-ttu-id="d4837-128">Max request memory grant (KB)</span><span class="sxs-lookup"><span data-stu-id="d4837-128">Max request memory grant (KB)</span></span>|<span data-ttu-id="d4837-129">查询的最大内存授予值，以千字节 (KB) 为单位。</span><span class="sxs-lookup"><span data-stu-id="d4837-129">The maximum value of memory grant, in kilobytes (KB), for a query.</span></span>|  
|<span data-ttu-id="d4837-130">Query optimizations/sec</span><span class="sxs-lookup"><span data-stu-id="d4837-130">Query optimizations/sec</span></span>|<span data-ttu-id="d4837-131">每秒此工作负荷组中发生的查询优化次数。</span><span class="sxs-lookup"><span data-stu-id="d4837-131">The number of query optimizations that have happened in this workload group per second.</span></span> <span data-ttu-id="d4837-132">此值可用于确定工作负荷特征。</span><span class="sxs-lookup"><span data-stu-id="d4837-132">This can be used to determine workload characteristics.</span></span>|  
|<span data-ttu-id="d4837-133">Suboptimal plans/sec</span><span class="sxs-lookup"><span data-stu-id="d4837-133">Suboptimal plans/sec</span></span>|<span data-ttu-id="d4837-134">每秒此工作负荷组中生成的非最优计划数。</span><span class="sxs-lookup"><span data-stu-id="d4837-134">The number of suboptimal plans that are generated in this workload group per second.</span></span>|  
|<span data-ttu-id="d4837-135">Active parallel threads</span><span class="sxs-lookup"><span data-stu-id="d4837-135">Active parallel threads</span></span>|<span data-ttu-id="d4837-136">当前使用的并行线程数。</span><span class="sxs-lookup"><span data-stu-id="d4837-136">The current count of parallel threads usage.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d4837-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d4837-137">See Also</span></span>  
 <span data-ttu-id="d4837-138">[监视资源使用情况（系统监视器）](monitor-resource-usage-system-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="d4837-138">[Monitor Resource Usage &#40;System Monitor&#41;](monitor-resource-usage-system-monitor.md) </span></span>  
 <span data-ttu-id="d4837-139">[SQL Server，Resource Pool Stats 对象](sql-server-resource-pool-stats-object.md) </span><span class="sxs-lookup"><span data-stu-id="d4837-139">[SQL Server, Resource Pool Stats Object](sql-server-resource-pool-stats-object.md) </span></span>  
 [<span data-ttu-id="d4837-140">资源调控器</span><span class="sxs-lookup"><span data-stu-id="d4837-140">Resource Governor</span></span>](../resource-governor/resource-governor.md)  
  
  
