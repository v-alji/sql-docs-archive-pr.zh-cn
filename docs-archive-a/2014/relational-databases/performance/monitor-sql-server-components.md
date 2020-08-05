---
title: 监视 SQL Server 组件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: e8f1b16b-ea40-4e12-886c-967ebda4e6e4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: baefe9aa1848bc3347a9a5a87c2ab81c382a6717
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580213"
---
# <a name="monitor-sql-server-components"></a><span data-ttu-id="f07ba-102">监视 SQL Server 组件</span><span class="sxs-lookup"><span data-stu-id="f07ba-102">Monitor SQL Server Components</span></span>
  <span data-ttu-id="f07ba-103">监视操作非常重要，因为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在动态环境中提供服务。</span><span class="sxs-lookup"><span data-stu-id="f07ba-103">Monitoring is important because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides a service in a dynamic environment.</span></span> <span data-ttu-id="f07ba-104">应用程序中的数据在变化。</span><span class="sxs-lookup"><span data-stu-id="f07ba-104">The data in the application changes.</span></span> <span data-ttu-id="f07ba-105">用户需要的访问类型在变化。</span><span class="sxs-lookup"><span data-stu-id="f07ba-105">The type of access that users require changes.</span></span> <span data-ttu-id="f07ba-106">用户连接的方式在变化。</span><span class="sxs-lookup"><span data-stu-id="f07ba-106">The way that users connect changes.</span></span> <span data-ttu-id="f07ba-107">甚至，访问 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的应用程序的类型也可能在变化，而 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 自动管理系统级资源（如内存和磁盘空间），以便最小化对广泛系统级手动优化的需要。</span><span class="sxs-lookup"><span data-stu-id="f07ba-107">The types of applications accessing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] may even change, but [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] automatically manages system-level resources, such as memory and disk space, to minimize the need for extensive system-level manual tuning.</span></span> <span data-ttu-id="f07ba-108">管理员可以通过监视来标识性能趋势以确定是否有必要进行更改。</span><span class="sxs-lookup"><span data-stu-id="f07ba-108">Monitoring lets administrators identify performance trends to determine if changes are necessary.</span></span>  
  
 <span data-ttu-id="f07ba-109">有效地监视任何 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 组件：</span><span class="sxs-lookup"><span data-stu-id="f07ba-109">To monitor any component of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] effectively:</span></span>  
  
1.  <span data-ttu-id="f07ba-110">确定监视目标。</span><span class="sxs-lookup"><span data-stu-id="f07ba-110">Determine your monitoring goals.</span></span>  
  
2.  <span data-ttu-id="f07ba-111">选择相应工具。</span><span class="sxs-lookup"><span data-stu-id="f07ba-111">Select the appropriate tool.</span></span>  
  
3.  <span data-ttu-id="f07ba-112">标识要监视的组件。</span><span class="sxs-lookup"><span data-stu-id="f07ba-112">Identify components to monitor.</span></span>  
  
4.  <span data-ttu-id="f07ba-113">选择那些组件的度量。</span><span class="sxs-lookup"><span data-stu-id="f07ba-113">Select metrics for those components.</span></span>  
  
5.  <span data-ttu-id="f07ba-114">监视服务器。</span><span class="sxs-lookup"><span data-stu-id="f07ba-114">Monitor the server.</span></span>  
  
6.  <span data-ttu-id="f07ba-115">分析数据。</span><span class="sxs-lookup"><span data-stu-id="f07ba-115">Analyze the data.</span></span>  
  
 <span data-ttu-id="f07ba-116">下面将依次介绍这些步骤。</span><span class="sxs-lookup"><span data-stu-id="f07ba-116">These steps are discussed in turn below.</span></span>  
  
## <a name="determine-your-monitoring-goals"></a><span data-ttu-id="f07ba-117">确定监视目标</span><span class="sxs-lookup"><span data-stu-id="f07ba-117">Determine Your Monitoring Goals</span></span>  
 <span data-ttu-id="f07ba-118">若要有效监视 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，必须清楚地确定监视原因。</span><span class="sxs-lookup"><span data-stu-id="f07ba-118">To monitor [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] effectively you should clearly identify your reason for monitoring.</span></span> <span data-ttu-id="f07ba-119">下面列出了可能的原因：</span><span class="sxs-lookup"><span data-stu-id="f07ba-119">Reasons can include the following:</span></span>  
  
-   <span data-ttu-id="f07ba-120">建立性能基线。</span><span class="sxs-lookup"><span data-stu-id="f07ba-120">Establish a baseline for performance.</span></span>  
  
-   <span data-ttu-id="f07ba-121">标识一段时间内的性能变化。</span><span class="sxs-lookup"><span data-stu-id="f07ba-121">Identify performance changes over time.</span></span>  
  
-   <span data-ttu-id="f07ba-122">诊断特定性能问题。</span><span class="sxs-lookup"><span data-stu-id="f07ba-122">Diagnose specific performance problems.</span></span>  
  
-   <span data-ttu-id="f07ba-123">标识要优化的组件或进程。</span><span class="sxs-lookup"><span data-stu-id="f07ba-123">Identify components or processes to optimize.</span></span>  
  
-   <span data-ttu-id="f07ba-124">比较对不同客户端应用程序性能的影响。</span><span class="sxs-lookup"><span data-stu-id="f07ba-124">Compare the effect of different client applications on performance.</span></span>  
  
-   <span data-ttu-id="f07ba-125">审核用户活动。</span><span class="sxs-lookup"><span data-stu-id="f07ba-125">Audit user activity.</span></span>  
  
-   <span data-ttu-id="f07ba-126">在不同负荷下测试服务器。</span><span class="sxs-lookup"><span data-stu-id="f07ba-126">Test a server under different loads.</span></span>  
  
-   <span data-ttu-id="f07ba-127">测试数据库体系结构。</span><span class="sxs-lookup"><span data-stu-id="f07ba-127">Test database architecture.</span></span>  
  
-   <span data-ttu-id="f07ba-128">测试维护计划。</span><span class="sxs-lookup"><span data-stu-id="f07ba-128">Test maintenance schedules.</span></span>  
  
-   <span data-ttu-id="f07ba-129">测试备份和还原计划。</span><span class="sxs-lookup"><span data-stu-id="f07ba-129">Test backup and restore plans.</span></span>  
  
-   <span data-ttu-id="f07ba-130">确定何时修改硬件配置。</span><span class="sxs-lookup"><span data-stu-id="f07ba-130">Determining when to modify your hardware configuration.</span></span>  
  
## <a name="select-the-appropriate-tool"></a><span data-ttu-id="f07ba-131">选择相应工具</span><span class="sxs-lookup"><span data-stu-id="f07ba-131">Select the Appropriate Tool</span></span>  
 <span data-ttu-id="f07ba-132">确定监视原因后，应该为该监视类型选择相应的工具。</span><span class="sxs-lookup"><span data-stu-id="f07ba-132">After determining why you are monitoring, you should select the appropriate tools for that type of monitoring.</span></span> <span data-ttu-id="f07ba-133">Windows 操作系统和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 提供了一整套用于在大型事务环境中监视服务器的工具。</span><span class="sxs-lookup"><span data-stu-id="f07ba-133">The Windows operating system and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provide a complete set of tools to monitor servers in transaction-intensive environments.</span></span> <span data-ttu-id="f07ba-134">这些工具清楚地显示 SQL Server 数据库引擎实例或 SQL Server Analysis Services 实例的状态。</span><span class="sxs-lookup"><span data-stu-id="f07ba-134">These tools clearly reveal the condition of an instance of the SQL Server Database Engine or an instance of SQL Server Analysis Services.</span></span>  
  
 <span data-ttu-id="f07ba-135">Windows 提供下列工具来监视在服务器上运行的应用程序：</span><span class="sxs-lookup"><span data-stu-id="f07ba-135">Windows provides the following tools for monitoring applications that are running on a server:</span></span>  
  
-   <span data-ttu-id="f07ba-136">系统监视器，使您可以收集和查看有关活动（如内存、磁盘和处理器使用）的实时数据</span><span class="sxs-lookup"><span data-stu-id="f07ba-136">System Monitor, which lets you collect and view real-time data about activities such as memory, disk, and processor usage</span></span>  
  
-   <span data-ttu-id="f07ba-137">性能日志和警报</span><span class="sxs-lookup"><span data-stu-id="f07ba-137">Performance logs and alerts</span></span>  
  
-   <span data-ttu-id="f07ba-138">任务管理器</span><span class="sxs-lookup"><span data-stu-id="f07ba-138">Task Manager</span></span>  
  
 <span data-ttu-id="f07ba-139">有关 Windows Server 或 Windows 工具的详细信息，请参阅 Windows 文档。</span><span class="sxs-lookup"><span data-stu-id="f07ba-139">For more information about Windows Server or Windows tools, see the Windows documentation.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="f07ba-140">提供下列工具来监视 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的组件：</span><span class="sxs-lookup"><span data-stu-id="f07ba-140">provides the following tools for monitoring components of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="f07ba-141">SQL 跟踪</span><span class="sxs-lookup"><span data-stu-id="f07ba-141">SQL Trace</span></span>  
  
-   [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]  
  
-   <span data-ttu-id="f07ba-142">分布式重播实用工具</span><span class="sxs-lookup"><span data-stu-id="f07ba-142">Distributed Replay Utility</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="f07ba-143">活动监视器</span><span class="sxs-lookup"><span data-stu-id="f07ba-143">Activity Monitor</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="f07ba-144">图形显示计划</span><span class="sxs-lookup"><span data-stu-id="f07ba-144">Graphical Showplan</span></span>  
  
-   <span data-ttu-id="f07ba-145">存储过程</span><span class="sxs-lookup"><span data-stu-id="f07ba-145">Stored procedures</span></span>  
  
-   <span data-ttu-id="f07ba-146">数据库控制台命令 (DBCC)</span><span class="sxs-lookup"><span data-stu-id="f07ba-146">Database Console Commands (DBCC)</span></span>  
  
-   <span data-ttu-id="f07ba-147">内置函数</span><span class="sxs-lookup"><span data-stu-id="f07ba-147">Built-in functions</span></span>  
  
-   <span data-ttu-id="f07ba-148">跟踪标志</span><span class="sxs-lookup"><span data-stu-id="f07ba-148">Trace flags</span></span>  
  
 <span data-ttu-id="f07ba-149">有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 监视工具的信息，请参阅 [性能监视和优化工具](performance-monitoring-and-tuning-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="f07ba-149">For more information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] monitoring tools, see [Performance Monitoring and Tuning Tools](performance-monitoring-and-tuning-tools.md).</span></span>  
  
## <a name="identify-the-components-to-monitor"></a><span data-ttu-id="f07ba-150">标识要监视的组件</span><span class="sxs-lookup"><span data-stu-id="f07ba-150">Identify the Components to Monitor</span></span>  
 <span data-ttu-id="f07ba-151">监视 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的第三步是标识监视组件。</span><span class="sxs-lookup"><span data-stu-id="f07ba-151">The third step to monitoring an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is to identify the components that you monitor.</span></span> <span data-ttu-id="f07ba-152">例如，如果使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 跟踪服务器，则可以定义该跟踪来收集有关特定事件的数据。</span><span class="sxs-lookup"><span data-stu-id="f07ba-152">For example, if you are using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to trace a server you can define the trace to collect data about specific events.</span></span> <span data-ttu-id="f07ba-153">还可以排除不适合您的情况的事件。</span><span class="sxs-lookup"><span data-stu-id="f07ba-153">You can also exclude events that do not apply to your situation.</span></span>  
  
## <a name="select-metrics-for-monitored-components"></a><span data-ttu-id="f07ba-154">选择监视组件的度量指标</span><span class="sxs-lookup"><span data-stu-id="f07ba-154">Select Metrics for Monitored Components</span></span>  
 <span data-ttu-id="f07ba-155">确定监视组件后，就需要确定监视组件的度量。</span><span class="sxs-lookup"><span data-stu-id="f07ba-155">After identifying the components to monitor, determine the metrics for components you monitor.</span></span> <span data-ttu-id="f07ba-156">例如，选择跟踪中包括的事件后，可以选择只包括有关事件的特定数据。</span><span class="sxs-lookup"><span data-stu-id="f07ba-156">For example, after selecting the events to include in a trace, you can choose to include only specific data about the events.</span></span> <span data-ttu-id="f07ba-157">限制只跟踪与该跟踪有关的数据可最大限度减少执行跟踪所需的系统资源。</span><span class="sxs-lookup"><span data-stu-id="f07ba-157">Limiting the trace to data that is relevant to the trace minimizes the system resources required to perform the tracing.</span></span>  
  
## <a name="monitor-the-server"></a><span data-ttu-id="f07ba-158">监视服务器</span><span class="sxs-lookup"><span data-stu-id="f07ba-158">Monitor the Server</span></span>  
 <span data-ttu-id="f07ba-159">若要监视服务器，请运行已配置为收集数据的监视工具。</span><span class="sxs-lookup"><span data-stu-id="f07ba-159">To monitor the server, run the monitoring tool that you have configured to gather data.</span></span> <span data-ttu-id="f07ba-160">例如，定义跟踪后，可以运行该跟踪以收集有关服务器中生成的事件的数据。</span><span class="sxs-lookup"><span data-stu-id="f07ba-160">For example, after a trace is defined, you can run the trace to gather data about events raised in the server.</span></span>  
  
## <a name="analyze-the-data"></a><span data-ttu-id="f07ba-161">分析数据</span><span class="sxs-lookup"><span data-stu-id="f07ba-161">Analyze the Data</span></span>  
 <span data-ttu-id="f07ba-162">跟踪结束后，分析数据以查看是否实现了监视目标。</span><span class="sxs-lookup"><span data-stu-id="f07ba-162">After the trace has finished, analyze the data to see if you have achieved your monitoring goal.</span></span> <span data-ttu-id="f07ba-163">如果没有，请修改用于监视服务器的组件或度量。</span><span class="sxs-lookup"><span data-stu-id="f07ba-163">If you have not, modify the components or metrics that you used to monitor the server.</span></span>  
  
 <span data-ttu-id="f07ba-164">下面概述了捕获事件数据并使用这些数据的过程。</span><span class="sxs-lookup"><span data-stu-id="f07ba-164">The following outlines the process for capturing event data and putting it to use.</span></span>  
  
1.  <span data-ttu-id="f07ba-165">使用筛选器限制收集的事件数据。</span><span class="sxs-lookup"><span data-stu-id="f07ba-165">Apply filters to limit the event data collected.</span></span>  
  
     <span data-ttu-id="f07ba-166">限制事件数据使系统可以集中在与监视方案有关的事件上。</span><span class="sxs-lookup"><span data-stu-id="f07ba-166">Limiting the event data allows for the system to focus on the events pertinent to the monitoring scenario.</span></span> <span data-ttu-id="f07ba-167">例如，若要监视执行速度慢的查询，可使用筛选器只监视那些在特定数据库中运行 30 秒以上的应用程序发出的查询。</span><span class="sxs-lookup"><span data-stu-id="f07ba-167">For example, if you want to monitor slow queries, you can use a filter to monitor only those queries issued by the application that take more than 30 seconds to run against a particular database.</span></span> <span data-ttu-id="f07ba-168">有关详细信息，请参阅[设置跟踪筛选器 (Transact-SQL)](../../ssms/agent/set-sql-server-alias-for-sql-server-agent-service-ssms.md) 和 [在跟踪中筛选事件 (SQL Server Profiler)](../../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md)。</span><span class="sxs-lookup"><span data-stu-id="f07ba-168">For more information, see [Set a Trace Filter &#40;Transact-SQL&#41;](../../ssms/agent/set-sql-server-alias-for-sql-server-agent-service-ssms.md) and [Filter Events in a Trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md).</span></span>  
  
2.  <span data-ttu-id="f07ba-169">监视（捕获）事件。</span><span class="sxs-lookup"><span data-stu-id="f07ba-169">Monitor (capture) events.</span></span>  
  
     <span data-ttu-id="f07ba-170">一旦启用，活动监视就从指定的应用程序、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例或操作系统捕获数据。</span><span class="sxs-lookup"><span data-stu-id="f07ba-170">As soon as it is enabled, active monitoring captures data from the specified application, instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or operating system.</span></span> <span data-ttu-id="f07ba-171">例如，当使用系统监视器监视磁盘活动时，监视将捕获事件数据（如磁盘读取和写入）并在屏幕上显示该数据。</span><span class="sxs-lookup"><span data-stu-id="f07ba-171">For example, when disk activity is monitored using System Monitor, monitoring captures event data, such as disk reads and writes, and displays it on the screen.</span></span> <span data-ttu-id="f07ba-172">有关详细信息，请参阅[监视资源使用情况（系统监视器）](../performance-monitor/monitor-resource-usage-system-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="f07ba-172">For more information, see [Monitor Resource Usage &#40;System Monitor&#41;](../performance-monitor/monitor-resource-usage-system-monitor.md).</span></span>  
  
3.  <span data-ttu-id="f07ba-173">保存捕获的事件数据。</span><span class="sxs-lookup"><span data-stu-id="f07ba-173">Save captured event data.</span></span>  
  
     <span data-ttu-id="f07ba-174">保存捕获的事件数据使您可以在以后对其进行分析，甚至使用分布式重播实用工具或 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]重播该数据。</span><span class="sxs-lookup"><span data-stu-id="f07ba-174">Saving captured event data lets you analyze it later or even replay it using the Distributed Replay Utility or [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="f07ba-175">捕获的事件数据将保存到文件，该文件可以加载回最初创建它的工具中以进行分析。</span><span class="sxs-lookup"><span data-stu-id="f07ba-175">Captured event data is saved to a file that can be loaded back into the tool that originally created it for analysis.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="f07ba-176">允许将事件数据保存到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 表。</span><span class="sxs-lookup"><span data-stu-id="f07ba-176">permits event data to be saved to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="f07ba-177">保存捕获的事件数据对创建性能基线非常重要。</span><span class="sxs-lookup"><span data-stu-id="f07ba-177">Saving captured event data is important when you are creating a performance baseline.</span></span> <span data-ttu-id="f07ba-178">在比较最近捕获的事件数据来确定是否已获得最佳性能时，将保存并使用性能基线数据。</span><span class="sxs-lookup"><span data-stu-id="f07ba-178">The performance baseline data is saved and used, when comparing recently captured event data, to determine whether performance is optimal.</span></span> <span data-ttu-id="f07ba-179">有关详细信息，请参阅 [SQL Server Profiler 模板和权限](../../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)。</span><span class="sxs-lookup"><span data-stu-id="f07ba-179">For more information, see [SQL Server Profiler Templates and Permissions](../../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md).</span></span>  
  
4.  <span data-ttu-id="f07ba-180">创建包含为捕获事件所指定设置的跟踪模板。</span><span class="sxs-lookup"><span data-stu-id="f07ba-180">Create trace templates that contain the settings specified to capture the events.</span></span>  
  
     <span data-ttu-id="f07ba-181">跟踪模板包括有关事件本身、事件数据和用于捕获数据的筛选器的规范。</span><span class="sxs-lookup"><span data-stu-id="f07ba-181">Trace templates include specifications about the events themselves, event data, and filters that are used to capture data.</span></span> <span data-ttu-id="f07ba-182">这些模板可用于以后监视特定事件集，而无需重新定义事件、事件数据和筛选器。</span><span class="sxs-lookup"><span data-stu-id="f07ba-182">These templates can be used to monitor a specific set of events later without redefining the events, event data, and filters.</span></span> <span data-ttu-id="f07ba-183">例如，若要频繁监视死锁数以及那些死锁所涉及的用户，您可以创建一个模板来定义那些事件、事件数据和事件筛选器；保存此模板；并在下次监视死锁时重新应用此筛选器。</span><span class="sxs-lookup"><span data-stu-id="f07ba-183">For example, if you want to frequently monitor the number of deadlocks, and the users involved in those deadlocks, you can create a template defining those events, event data, and event filters; save the template; and reapply the filter the next time that you want to monitor deadlocks.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="f07ba-184">使用跟踪模板。</span><span class="sxs-lookup"><span data-stu-id="f07ba-184">uses trace templates for this purpose.</span></span> <span data-ttu-id="f07ba-185">有关详细信息，请参阅[设置跟踪定义默认值 (SQL Server Profiler)](../../tools/sql-server-profiler/set-trace-definition-defaults-sql-server-profiler.md) 和[创建跟踪模板 (SQL Server Profiler)](../../tools/sql-server-profiler/create-a-trace-template-sql-server-profiler.md)。</span><span class="sxs-lookup"><span data-stu-id="f07ba-185">For more information, see [Set Trace Definition Defaults &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/set-trace-definition-defaults-sql-server-profiler.md) and [Create a Trace Template &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/create-a-trace-template-sql-server-profiler.md).</span></span>  
  
5.  <span data-ttu-id="f07ba-186">分析捕获的事件数据。</span><span class="sxs-lookup"><span data-stu-id="f07ba-186">Analyze captured event data.</span></span>  
  
     <span data-ttu-id="f07ba-187">为了进行分析，将捕获的事件数据加载到捕获该数据的应用程序中。</span><span class="sxs-lookup"><span data-stu-id="f07ba-187">To be analyzed, the captured event data is loaded into the application that captured the data.</span></span> <span data-ttu-id="f07ba-188">例如，可以将通过 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 捕获的跟踪重新加载到 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 中进行查看和分析。</span><span class="sxs-lookup"><span data-stu-id="f07ba-188">For example, a captured trace from [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] can be reloaded into [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] for viewing and analysis.</span></span> <span data-ttu-id="f07ba-189">有关详细信息，请参阅 [使用 SQL Server Profiler 查看和分析跟踪](../../tools/sql-server-profiler/view-and-analyze-traces-with-sql-server-profiler.md)。</span><span class="sxs-lookup"><span data-stu-id="f07ba-189">For more information, see [View and Analyze Traces with SQL Server Profiler](../../tools/sql-server-profiler/view-and-analyze-traces-with-sql-server-profiler.md).</span></span>  
  
     <span data-ttu-id="f07ba-190">对事件数据的分析包括确定所发生的事件和发生原因。</span><span class="sxs-lookup"><span data-stu-id="f07ba-190">Analyzing event data involves determining what is occurring and why.</span></span> <span data-ttu-id="f07ba-191">利用这些信息可以做一些更改（如根据所执行的分析类型添加更多内存、更改索引、更正使用 Transact-SQL 语句或存储过程的编码问题等）来提高性能。</span><span class="sxs-lookup"><span data-stu-id="f07ba-191">This information lets you make changes that can improve performance, such as adding more memory, changing indexes, correcting coding problems with Transact-SQL statements or stored procedures, and so on, depending on the type of analysis performed.</span></span> <span data-ttu-id="f07ba-192">例如，可以使用 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 优化顾问分析通过 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 捕获的跟踪并根据结果生成索引建议。</span><span class="sxs-lookup"><span data-stu-id="f07ba-192">For example, you can use the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor to analyze a captured trace from [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] and make index recommendations based on the results.</span></span>  
  
6.  <span data-ttu-id="f07ba-193">重播捕获的事件数据。</span><span class="sxs-lookup"><span data-stu-id="f07ba-193">Replay captured event data.</span></span>  
  
     <span data-ttu-id="f07ba-194">事件重播使您可以建立捕获数据时的数据库环境的测试副本，然后可以重复捕获的事件，就像最初在真实系统上捕获事件一样。</span><span class="sxs-lookup"><span data-stu-id="f07ba-194">Event replay lets you establish a test copy of the database environment from which the data was captured, and then repeat the captured events as they occurred originally on the real system.</span></span> <span data-ttu-id="f07ba-195">此功能仅适用于分布式重播实用工具或 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f07ba-195">This capability is only available with the Distributed Replay Utility or [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="f07ba-196">可以按事件最初发生时的速度重播它们，尽可能快地重播（增加系统的压力），或者尽可能一次重播一步（每个事件发生后对系统进行分析）。</span><span class="sxs-lookup"><span data-stu-id="f07ba-196">You can replay the events at the same speed as they originally occurred, as fast as possible (to stress the system), or more likely, one step at a time (to analyze the system after each event has occurred).</span></span> <span data-ttu-id="f07ba-197">通过在测试环境中分析确切事件，可以防止对生产系统产生有害影响。</span><span class="sxs-lookup"><span data-stu-id="f07ba-197">By analyzing the exact events in a test environment, you can prevent harm to the production system.</span></span> <span data-ttu-id="f07ba-198">有关详细信息，请参阅 [重播跟踪](../../tools/sql-server-profiler/replay-traces.md)。</span><span class="sxs-lookup"><span data-stu-id="f07ba-198">For more information, see [Replay Traces](../../tools/sql-server-profiler/replay-traces.md).</span></span>  
  
  
