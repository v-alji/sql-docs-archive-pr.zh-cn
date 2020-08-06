---
title: 监视资源使用情况（系统监视器）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- monitoring performance [SQL Server], resource usage
- System Monitor [SQL Server], about Windows System Monitor
- resource usage monitoring [SQL Server]
- System Monitor [SQL Server]
- counters [SQL Server], resource usage subjects
- performance counters [SQL Server], resource usage subjects
- Windows System Monitor [SQL Server], about Windows System Monitor
- monitoring [SQL Server], server resource usage
- monitoring resource usage [SQL Server]
- Windows System Monitor [SQL Server]
- database monitoring [SQL Server], resource usage
- database performance [SQL Server], resource usage
- tuning databases [SQL Server], resource usage
- server performance [SQL Server], resource usage
ms.assetid: f2993a28-0b81-46f2-aec0-6877fe990387
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d691091a41e3161c733902824bf439b6788cc4f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590742"
---
# <a name="monitor-resource-usage-system-monitor"></a><span data-ttu-id="c3c96-102">监视资源使用情况（系统监视器）</span><span class="sxs-lookup"><span data-stu-id="c3c96-102">Monitor Resource Usage (System Monitor)</span></span>
  <span data-ttu-id="c3c96-103">如果您运行的是 Microsoft Windows 服务器操作系统，则可以使用系统监视器图形工具来测量 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的性能。</span><span class="sxs-lookup"><span data-stu-id="c3c96-103">If you are running Microsoft Windows server operating system, use the System Monitor graphical tool to measure the performance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c3c96-104">可以查看 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 对象、性能计数器以及其他对象的行为，这些对象包括处理器、内存、缓存、线程和进程。</span><span class="sxs-lookup"><span data-stu-id="c3c96-104">You can view [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objects, performance counters, and the behavior of other objects, such as processors, memory, cache, threads, and processes.</span></span> <span data-ttu-id="c3c96-105">每个对象都有一个相关的计数器集，用于测量设备使用情况、队列长度、延时情况，另外还有吞吐量及内部拥塞指示器。</span><span class="sxs-lookup"><span data-stu-id="c3c96-105">Each of these objects has an associated set of counters that measure device usage, queue lengths, delays, and other indicators of throughput and internal congestion.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c3c96-106">在 Windows NT 4.0 以后的版本，系统监视器替换了性能监视器。</span><span class="sxs-lookup"><span data-stu-id="c3c96-106">System Monitor replaced Performance Monitor after Windows NT 4.0.</span></span>  
  
## <a name="benefits-of-system-monitor"></a><span data-ttu-id="c3c96-107">系统监视器的优点</span><span class="sxs-lookup"><span data-stu-id="c3c96-107">Benefits of System Monitor</span></span>  
 <span data-ttu-id="c3c96-108">系统监视器可用于同时监视 Windows 操作系统和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 计数器，以便确定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 性能与 Windows 性能之间可能存在的关联。</span><span class="sxs-lookup"><span data-stu-id="c3c96-108">System Monitor can be useful to monitor Windows operating system and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] counters at the same time to determine any correlation between the performance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows.</span></span> <span data-ttu-id="c3c96-109">例如，同时监视 Windows 磁盘输入/输出 (I/O) 计数器和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 缓冲区管理器计数器可以揭示整个系统的行为。</span><span class="sxs-lookup"><span data-stu-id="c3c96-109">For example, monitoring the Windows disk input/output (I/O) counters and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Buffer Manager counters at the same time can reveal the behavior of the entire system.</span></span>  
  
 <span data-ttu-id="c3c96-110">系统监视器使您可以获取有关当前 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 活动和性能的统计信息。</span><span class="sxs-lookup"><span data-stu-id="c3c96-110">System Monitor allows you to obtain statistics on current [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] activity and performance.</span></span> <span data-ttu-id="c3c96-111">利用系统监视器，可以：</span><span class="sxs-lookup"><span data-stu-id="c3c96-111">Using System Monitor, you can:</span></span>  
  
-   <span data-ttu-id="c3c96-112">同时查看任意多台计算机中的数据。</span><span class="sxs-lookup"><span data-stu-id="c3c96-112">View data simultaneously from any number of computers.</span></span>  
  
-   <span data-ttu-id="c3c96-113">查看和更改图表以反映当前的活动，以及显示按用户定义的频率进行更新的计数器值。</span><span class="sxs-lookup"><span data-stu-id="c3c96-113">View and change charts to reflect current activity, and show counter values that are updated at a frequency that the user defines.</span></span>  
  
-   <span data-ttu-id="c3c96-114">从图表、日志、警报日志和报告将数据导出到电子表格或数据库应用程序中，以进行进一步的操作和打印。</span><span class="sxs-lookup"><span data-stu-id="c3c96-114">Export data from charts, logs, alert logs, and reports to spreadsheet or database applications for further manipulation and printing.</span></span>  
  
-   <span data-ttu-id="c3c96-115">添加系统警报，这些警报可在警报日志中列出事件，并可以通过发出网络警报来通知您。</span><span class="sxs-lookup"><span data-stu-id="c3c96-115">Add system alerts that list an event in the alert log and can notify you by issuing a network alert.</span></span>  
  
-   <span data-ttu-id="c3c96-116">当计数器值首次或每次超过或低于用户定义的值时，运行预定义的应用程序。</span><span class="sxs-lookup"><span data-stu-id="c3c96-116">Run a predefined application the first time or every time a counter value goes over or under a user-defined value.</span></span>  
  
-   <span data-ttu-id="c3c96-117">创建日志文件，其中包含有关来自不同计算机的各种对象的数据。</span><span class="sxs-lookup"><span data-stu-id="c3c96-117">Create log files that contain data about various objects from different computers.</span></span>  
  
-   <span data-ttu-id="c3c96-118">将其他现有日志文件中的选定区域追加到一个文件上，以形成长期存档。</span><span class="sxs-lookup"><span data-stu-id="c3c96-118">Append to one file selected sections from other existing log files to form a long-term archive.</span></span>  
  
-   <span data-ttu-id="c3c96-119">查看当前活动报告，或从现有日志文件创建报告。</span><span class="sxs-lookup"><span data-stu-id="c3c96-119">View current-activity reports, or create reports from existing log files.</span></span>  
  
-   <span data-ttu-id="c3c96-120">保存各个图表、警报、日志或报告设置或整个工作空间设置，以备再次使用。</span><span class="sxs-lookup"><span data-stu-id="c3c96-120">Save individual chart, alert, log, or report settings, or the entire workspace setup for reuse.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c3c96-121">在 Windows NT 4.0 之后，系统监视器取代了性能监视器。</span><span class="sxs-lookup"><span data-stu-id="c3c96-121">System Monitor replaced the Performance Monitor after Windows NT 4.0.</span></span> <span data-ttu-id="c3c96-122">既可以使用系统监视器也可以使用性能监视器来执行这些任务。</span><span class="sxs-lookup"><span data-stu-id="c3c96-122">You can use either the System Monitor or Performance Monitor to do these tasks.</span></span>  
  
## <a name="system-monitor-performance"></a><span data-ttu-id="c3c96-123">系统监视器性能</span><span class="sxs-lookup"><span data-stu-id="c3c96-123">System Monitor Performance</span></span>  
 <span data-ttu-id="c3c96-124">当监视 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 Microsoft Windows 操作系统以调查与性能有关的问题时，请首先注意以下三个主要方面：</span><span class="sxs-lookup"><span data-stu-id="c3c96-124">When you monitor [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the Microsoft Windows operating system to investigate performance-related issues, concentrate your initial efforts in three main areas:</span></span>  
  
-   <span data-ttu-id="c3c96-125">磁盘活动</span><span class="sxs-lookup"><span data-stu-id="c3c96-125">Disk activity</span></span>  
  
-   <span data-ttu-id="c3c96-126">处理器利用率</span><span class="sxs-lookup"><span data-stu-id="c3c96-126">Processor utilization</span></span>  
  
-   <span data-ttu-id="c3c96-127">内存使用率</span><span class="sxs-lookup"><span data-stu-id="c3c96-127">Memory usage</span></span>  
  
 <span data-ttu-id="c3c96-128">监视运行系统监视器的系统会轻微地影响计算机性能。</span><span class="sxs-lookup"><span data-stu-id="c3c96-128">Monitoring a computer on which System Monitor is running can affect computer performance slightly.</span></span> <span data-ttu-id="c3c96-129">因此，要么将系统监视器数据记录到另一个磁盘或计算机上，以便减少对所监视计算机的影响，要么从远程计算机上运行系统监视器。</span><span class="sxs-lookup"><span data-stu-id="c3c96-129">Therefore, either log the System Monitor data to another disk (or computer) so that it reduces the effect on the computer being monitored, or run System Monitor from a remote computer.</span></span> <span data-ttu-id="c3c96-130">只监视您感兴趣的计数器。</span><span class="sxs-lookup"><span data-stu-id="c3c96-130">Monitor only the counters in which you are interested.</span></span> <span data-ttu-id="c3c96-131">如果监视的计数器过多，将会增加监视过程中使用的资源开销，并影响所监视计算机的性能。</span><span class="sxs-lookup"><span data-stu-id="c3c96-131">If you monitor too many counters, resource usage overhead is added to the monitoring process and affects the performance of the computer that is being monitored.</span></span>  
  
## <a name="system-monitor-tasks"></a><span data-ttu-id="c3c96-132">系统监视器任务</span><span class="sxs-lookup"><span data-stu-id="c3c96-132">System Monitor Tasks</span></span>  
  
|<span data-ttu-id="c3c96-133">任务说明</span><span class="sxs-lookup"><span data-stu-id="c3c96-133">Task Description</span></span>|<span data-ttu-id="c3c96-134">主题</span><span class="sxs-lookup"><span data-stu-id="c3c96-134">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="c3c96-135">描述何时使用系统监视器，并讨论使用系统监视器时的性能开销。</span><span class="sxs-lookup"><span data-stu-id="c3c96-135">Describes when to use System Monitor and discusses performance overhead when you use System Monitor.</span></span>|[<span data-ttu-id="c3c96-136">运行系统监视器</span><span class="sxs-lookup"><span data-stu-id="c3c96-136">Run System Monitor</span></span>](run-system-monitor.md)|  
|<span data-ttu-id="c3c96-137">描述如何监视磁盘计数器，以便确定其 SQL Server 组件生成的磁盘活动和 I/O 量。</span><span class="sxs-lookup"><span data-stu-id="c3c96-137">Describes how to monitor disk counters to determine disk activity and the amount of I/O generated by their SQL Server components.</span></span>|[<span data-ttu-id="c3c96-138">监视磁盘用量</span><span class="sxs-lookup"><span data-stu-id="c3c96-138">Monitor Disk Usage</span></span>](monitor-disk-usage.md)|  
|<span data-ttu-id="c3c96-139">描述如何监视 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例，以便确定 CPU 使用率是否在正常范围内。</span><span class="sxs-lookup"><span data-stu-id="c3c96-139">Describes how to monitor an instance of Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to determine whether CPU usage rates are within normal ranges.</span></span>|[<span data-ttu-id="c3c96-140">监视 CPU 用量</span><span class="sxs-lookup"><span data-stu-id="c3c96-140">Monitor CPU Usage</span></span>](monitor-cpu-usage.md)|  
|<span data-ttu-id="c3c96-141">描述如何监视 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例，以便确认内存使用量是否在正常范围内。</span><span class="sxs-lookup"><span data-stu-id="c3c96-141">Describes how to monitor an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to confirm that memory usage is within typical ranges.</span></span>|[<span data-ttu-id="c3c96-142">监视内存用量</span><span class="sxs-lookup"><span data-stu-id="c3c96-142">Monitor Memory Usage</span></span>](monitor-memory-usage.md)|  
|<span data-ttu-id="c3c96-143">描述如何创建一个在达到系统监视器计数器的阈值时发出的警报。</span><span class="sxs-lookup"><span data-stu-id="c3c96-143">Describes how to create an alert that is raised when a threshold value for a System Monitor counter has been reached.</span></span>|[<span data-ttu-id="c3c96-144">创建 SQL Server 数据库警报</span><span class="sxs-lookup"><span data-stu-id="c3c96-144">Create a SQL Server Database Alert</span></span>](create-a-sql-server-database-alert.md)|  
|<span data-ttu-id="c3c96-145">描述如何创建图表、警报、日志和报表，以便监视 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例。</span><span class="sxs-lookup"><span data-stu-id="c3c96-145">Describes how to you create charts, alerts, logs, and reports to monitor an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|[<span data-ttu-id="c3c96-146">创建图表、警报、日志和报告</span><span class="sxs-lookup"><span data-stu-id="c3c96-146">Create Charts, Alerts, Logs, and Reports</span></span>](create-charts-alerts-logs-and-reports.md)|  
|<span data-ttu-id="c3c96-147">列出系统监视器用来在运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例的计算机中监视活动的对象和计数器。</span><span class="sxs-lookup"><span data-stu-id="c3c96-147">Lists objects and counters that System Monitor uses to monitor activity in computers running an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|[<span data-ttu-id="c3c96-148">使用 SQL Server 对象</span><span class="sxs-lookup"><span data-stu-id="c3c96-148">Use SQL Server Objects</span></span>](use-sql-server-objects.md)|  
|<span data-ttu-id="c3c96-149">列出系统监视器用于监视内存中 OLTP 活动的对象和计数器。</span><span class="sxs-lookup"><span data-stu-id="c3c96-149">Lists objects and counters that System Monitor uses to monitor In-Memory OLTP activity.</span></span>|[<span data-ttu-id="c3c96-150">XTP &#40;内存中 OLTP&#41; 性能计数器</span><span class="sxs-lookup"><span data-stu-id="c3c96-150">XTP &#40;In-Memory OLTP&#41; Performance Counters</span></span>](../../integration-services/performance/performance-counters.md)|  
  
  
