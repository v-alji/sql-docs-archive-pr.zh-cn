---
title: 监视和优化性能 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- instances of SQL Server, monitoring performance
- monitoring server performance [SQL Server]
- Database Engine [SQL Server], performance
- monitoring performance [SQL Server], about performance
- server performance [SQL Server]
- monitoring performance [SQL Server]
- database performance [SQL Server], about performance
- tuning databases [SQL Server], about performance
- status information [SQL Server], performance monitoring
- database monitoring [SQL Server], about performance
- monitoring [SQL Server], queries performance
- server performance [SQL Server], about performance
- tuning databases [SQL Server]
- database performance [SQL Server]
- monitoring [SQL Server], server performance
- database monitoring [SQL Server]
- monitoring server performance [SQL Server], about monitoring server performance
ms.assetid: 87f23f03-0f19-4b2e-bfae-efa378f7a0d4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fe07bdf01df6c4b61a64c6ee78de313a21d62f90
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580214"
---
# <a name="monitor-and-tune-for-performance"></a><span data-ttu-id="fa9d5-102">监视和优化性能</span><span class="sxs-lookup"><span data-stu-id="fa9d5-102">Monitor and Tune for Performance</span></span>
  <span data-ttu-id="fa9d5-103">监视数据库的目的是评估服务器的性能。</span><span class="sxs-lookup"><span data-stu-id="fa9d5-103">The goal of monitoring databases is to assess how a server is performing.</span></span> <span data-ttu-id="fa9d5-104">有效监视包括定期拍摄当前性能的快照来隔离导致问题的进程，以及连续收集数据来跟踪性能趋势。</span><span class="sxs-lookup"><span data-stu-id="fa9d5-104">Effective monitoring involves taking periodic snapshots of current performance to isolate processes that are causing problems, and gathering data continuously over time to track performance trends.</span></span>  
  
 <span data-ttu-id="fa9d5-105">日常数据库性能评估有助于使响应时间最小化并使吞吐量最大化，从而实现最佳性能。</span><span class="sxs-lookup"><span data-stu-id="fa9d5-105">Ongoing evaluation of the database performance helps you minimize response times and maximize throughput, yielding optimal performance.</span></span> <span data-ttu-id="fa9d5-106">有效网络流量、磁盘 I/O 和 CPU 使用率是实现最佳性能的关键。</span><span class="sxs-lookup"><span data-stu-id="fa9d5-106">Efficient network traffic, disk I/O, and CPU usage are key to peak performance.</span></span> <span data-ttu-id="fa9d5-107">您需要透彻地分析应用程序要求，了解数据的逻辑结构和物理结构，评估数据库使用情况，并协商使用 [如联机事务处理 (OLTP) 与决策支持] 冲突之间的平衡措施。</span><span class="sxs-lookup"><span data-stu-id="fa9d5-107">You need to thoroughly analyze the application requirements, understand the logical and physical structure of the data, assess database usage, and negotiate tradeoffs between conflicting uses such as online transaction processing (OLTP) versus decision support.</span></span>  
  
## <a name="benefits-of-monitoring-and-tuning-databases-for-performance"></a><span data-ttu-id="fa9d5-108">监视和优化数据库性能的好处</span><span class="sxs-lookup"><span data-stu-id="fa9d5-108">Benefits of Monitoring and Tuning Databases for Performance</span></span>  
 <span data-ttu-id="fa9d5-109">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 Microsoft Windows 操作系统提供实用工具，允许您查看数据库的当前状态并跟踪条件变化时的性能。</span><span class="sxs-lookup"><span data-stu-id="fa9d5-109">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the Microsoft Windows operating system provide utilities that allow you to view the current condition of the database and to track performance as conditions change.</span></span> <span data-ttu-id="fa9d5-110">可以使用多种工具和技术来监视 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="fa9d5-110">There are a variety of tools and techniques that can be used to monitor [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="fa9d5-111">了解如何监视 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 有助于：</span><span class="sxs-lookup"><span data-stu-id="fa9d5-111">Understanding how to monitor [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can help you:</span></span>  
  
-   <span data-ttu-id="fa9d5-112">确定是否可以提高性能。</span><span class="sxs-lookup"><span data-stu-id="fa9d5-112">Determine whether you can improve performance.</span></span> <span data-ttu-id="fa9d5-113">例如，通过监视常用查询的响应时间，可以确定是否需要更改表的查询或索引。</span><span class="sxs-lookup"><span data-stu-id="fa9d5-113">For example, by monitoring the response times for frequently used queries, you can determine whether changes to the query or indexes on the tables are required.</span></span>  
  
-   <span data-ttu-id="fa9d5-114">评估用户活动。</span><span class="sxs-lookup"><span data-stu-id="fa9d5-114">Evaluate user activity.</span></span> <span data-ttu-id="fa9d5-115">例如，通过监视尝试连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例的用户，可以确定安全设置是否充分以及是否需要测试应用程序或开发系统。</span><span class="sxs-lookup"><span data-stu-id="fa9d5-115">For example, by monitoring users trying to connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you can determine whether security is set up adequately and test applications or development systems.</span></span> <span data-ttu-id="fa9d5-116">例如，通过在执行 SQL 查询时对其进行监视，可以确定这些查询是否编写正确并生成预期的结果。</span><span class="sxs-lookup"><span data-stu-id="fa9d5-116">For example, by monitoring SQL queries as they are executed, you can determine whether they are written correctly and producing the expected results.</span></span>  
  
-   <span data-ttu-id="fa9d5-117">解决任何问题或调试应用程序组件（如存储过程）。</span><span class="sxs-lookup"><span data-stu-id="fa9d5-117">Troubleshoot any problems or debug application components, such as stored procedures.</span></span>  
  
### <a name="monitoring-in-a-dynamic-environment"></a><span data-ttu-id="fa9d5-118">动态环境中的监视</span><span class="sxs-lookup"><span data-stu-id="fa9d5-118">Monitoring in a Dynamic Environment</span></span>  
 <span data-ttu-id="fa9d5-119">监视操作非常重要，因为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在动态环境中提供服务。</span><span class="sxs-lookup"><span data-stu-id="fa9d5-119">Monitoring is important because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides a service in a dynamic environment.</span></span> <span data-ttu-id="fa9d5-120">更改条件会导致性能发生变化。</span><span class="sxs-lookup"><span data-stu-id="fa9d5-120">Changing conditions result in changing performance.</span></span> <span data-ttu-id="fa9d5-121">在评估中，您可以看到性能会随着用户数量增加、用户访问和连接方法改变、数据库内容增加、客户端应用程序改变、应用程序中的数据变化、查询变得更加复杂以及网络流量上升而变化。</span><span class="sxs-lookup"><span data-stu-id="fa9d5-121">In your evaluations, you can see performance changes as the number of users increases, user access and connection methods change, database contents grow, client applications change, data in the applications changes, queries become more complex, and network traffic rises.</span></span> <span data-ttu-id="fa9d5-122">通过使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 工具来监视性能，可以将性能的某些变化与条件和复杂查询的变化相关联。</span><span class="sxs-lookup"><span data-stu-id="fa9d5-122">By using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tools to monitor performance, you can associate some changes in performance with changing conditions and complex queries.</span></span> <span data-ttu-id="fa9d5-123">下列方案提供了此方面的示例：</span><span class="sxs-lookup"><span data-stu-id="fa9d5-123">The following scenarios provide examples:</span></span>  
  
-   <span data-ttu-id="fa9d5-124">通过监视常用查询的响应时间，可以确定是否需要更改查询或执行查询的表上的索引。</span><span class="sxs-lookup"><span data-stu-id="fa9d5-124">By monitoring the response times for frequently used queries, you can determine whether changes to the query or indexes on the tables where the queries execute are required.</span></span>  
  
-   <span data-ttu-id="fa9d5-125">通过在执行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查询时对其进行监视，可以确定这些查询是否编写正确并生成预期的结果。</span><span class="sxs-lookup"><span data-stu-id="fa9d5-125">By monitoring [!INCLUDE[tsql](../../includes/tsql-md.md)] queries as they are executed, you can determine whether the queries are written correctly and producing the expected results.</span></span>  
  
-   <span data-ttu-id="fa9d5-126">通过监视试图连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例的用户，可以确定安全设置是否得当并测试应用程序或开发系统。</span><span class="sxs-lookup"><span data-stu-id="fa9d5-126">By monitoring users that try to connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you can determine whether security is set up adequately and test applications or development systems.</span></span>  
  
 <span data-ttu-id="fa9d5-127">响应时间是指以可视确认信息（指出正在处理查询）的形式将结果集的首行返回给用户所需的时间。</span><span class="sxs-lookup"><span data-stu-id="fa9d5-127">Response time is the length of time required for the first row of the result set to be returned to the user in the form of visual confirmation that a query is being processed.</span></span> <span data-ttu-id="fa9d5-128">吞吐量是指在一段给定时间内，服务器处理的查询总数。</span><span class="sxs-lookup"><span data-stu-id="fa9d5-128">Throughput is the total number of queries handled by the server during a specified period of time.</span></span>  
  
 <span data-ttu-id="fa9d5-129">随着用户数量的增加，对服务器资源的竞争也会更激烈，进而导致响应时间增加和总体吞吐量减少。</span><span class="sxs-lookup"><span data-stu-id="fa9d5-129">As the number of users increases, so does the competition for a server's resources, which in turn increases response time and decreases overall throughput.</span></span>  
  
## <a name="monitoring-and-tuning-performance-tasks"></a><span data-ttu-id="fa9d5-130">监视和优化性能任务</span><span class="sxs-lookup"><span data-stu-id="fa9d5-130">Monitoring and Tuning Performance Tasks</span></span>  
  
|<span data-ttu-id="fa9d5-131">任务说明</span><span class="sxs-lookup"><span data-stu-id="fa9d5-131">Task Description</span></span>|<span data-ttu-id="fa9d5-132">主题</span><span class="sxs-lookup"><span data-stu-id="fa9d5-132">Topic</span></span>|  
|----------------------|-----------|  
|[<span data-ttu-id="fa9d5-133">监视 SQL Server 组件</span><span class="sxs-lookup"><span data-stu-id="fa9d5-133">Monitor SQL Server Components</span></span>](monitor-sql-server-components.md)|<span data-ttu-id="fa9d5-134">提供有效地监视 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的任何组件所需的必要步骤。</span><span class="sxs-lookup"><span data-stu-id="fa9d5-134">Provides the necessary steps required to effectively monitor any component of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="fa9d5-135">性能监视和优化工具</span><span class="sxs-lookup"><span data-stu-id="fa9d5-135">Performance Monitoring and Tuning Tools</span></span>](performance-monitoring-and-tuning-tools.md)|<span data-ttu-id="fa9d5-136">列出 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 监视和优化工具。</span><span class="sxs-lookup"><span data-stu-id="fa9d5-136">Lists the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] monitoring and tuning tools.</span></span>|  
|[<span data-ttu-id="fa9d5-137">建立性能基线</span><span class="sxs-lookup"><span data-stu-id="fa9d5-137">Establish a Performance Baseline</span></span>](establish-a-performance-baseline.md)|<span data-ttu-id="fa9d5-138">提供有关如何建立性能基准的信息。</span><span class="sxs-lookup"><span data-stu-id="fa9d5-138">Provides information about how to establish a performance baseline.</span></span>|  
|[<span data-ttu-id="fa9d5-139">隔离性能问题</span><span class="sxs-lookup"><span data-stu-id="fa9d5-139">Isolate Performance Problems</span></span>](isolate-performance-problems.md)|<span data-ttu-id="fa9d5-140">介绍如何隔离数据库性能问题。</span><span class="sxs-lookup"><span data-stu-id="fa9d5-140">Describes how to isolate database performance problems.</span></span>|  
|[<span data-ttu-id="fa9d5-141">识别瓶颈</span><span class="sxs-lookup"><span data-stu-id="fa9d5-141">Identify Bottlenecks</span></span>](identify-bottlenecks.md)|<span data-ttu-id="fa9d5-142">介绍如何监视和跟踪服务器性能，以发现瓶颈。</span><span class="sxs-lookup"><span data-stu-id="fa9d5-142">Describes how to monitor and track server performance to identify bottlenecks.</span></span>|  
|[<span data-ttu-id="fa9d5-143">服务器性能和活动监视</span><span class="sxs-lookup"><span data-stu-id="fa9d5-143">Server Performance and Activity Monitoring</span></span>](server-performance-and-activity-monitoring.md)|<span data-ttu-id="fa9d5-144">介绍如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 Windows 性能和活动监视工具。</span><span class="sxs-lookup"><span data-stu-id="fa9d5-144">Describes how to use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows performance and activity monitoring tools.</span></span>|  
|[<span data-ttu-id="fa9d5-145">显示和保存执行计划</span><span class="sxs-lookup"><span data-stu-id="fa9d5-145">Display and Save Execution Plans</span></span>](display-and-save-execution-plans.md)|<span data-ttu-id="fa9d5-146">介绍如何显示执行计划并将其保存到 XML 格式的文件中。</span><span class="sxs-lookup"><span data-stu-id="fa9d5-146">Describes how to display and save execution plans to a file in XML format.</span></span>|  
|[<span data-ttu-id="fa9d5-147">使用查询存储来监视性能</span><span class="sxs-lookup"><span data-stu-id="fa9d5-147">Monitoring Performance By Using the Query Store</span></span>](monitoring-performance-by-using-the-query-store.md)|<span data-ttu-id="fa9d5-148">查询存储将自动捕获查询、计划和运行时统计信息的历史记录，并保留它们以供查阅。</span><span class="sxs-lookup"><span data-stu-id="fa9d5-148">The Query Store automatically captures a history of queries, plans, and runtime statistics, and retains these for your review.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fa9d5-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fa9d5-149">See Also</span></span>  
 <span data-ttu-id="fa9d5-150">[企业范围的自动化管理](../../ssms/agent/automated-administration-across-an-enterprise.md) </span><span class="sxs-lookup"><span data-stu-id="fa9d5-150">[Automated Administration Across an Enterprise](../../ssms/agent/automated-administration-across-an-enterprise.md) </span></span>  
 <span data-ttu-id="fa9d5-151">[数据库引擎优化顾问](database-engine-tuning-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="fa9d5-151">[Database Engine Tuning Advisor](database-engine-tuning-advisor.md) </span></span>  
 <span data-ttu-id="fa9d5-152">[监视资源使用情况（系统监视器）](../performance-monitor/monitor-resource-usage-system-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="fa9d5-152">[Monitor Resource Usage &#40;System Monitor&#41;](../performance-monitor/monitor-resource-usage-system-monitor.md) </span></span>  
 [<span data-ttu-id="fa9d5-153">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="fa9d5-153">SQL Server Profiler</span></span>](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
