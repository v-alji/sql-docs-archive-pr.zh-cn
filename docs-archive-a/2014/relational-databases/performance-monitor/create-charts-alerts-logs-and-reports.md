---
title: 创建图表、警报、日志和报表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- System Monitor [SQL Server], charts and reports
- charts [SQL Server]
- reports [SQL Server]
- reports [SQL Server], creating
- Windows System Monitor [SQL Server], charts and reports
- logs [SQL Server], System Monitor
- System Monitor [SQL Server], logs
- Windows System Monitor [SQL Server], logs
ms.assetid: c9162b37-e5dc-43d1-a3aa-1e9ebc69fecc
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3a0c95c3f483a8af3e3e68d9c5c7d3caf44350d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692863"
---
# <a name="create-charts-alerts-logs-and-reports"></a><span data-ttu-id="25563-102">创建图表、警报、日志和报表</span><span class="sxs-lookup"><span data-stu-id="25563-102">Create Charts, Alerts, Logs, and Reports</span></span>
  <span data-ttu-id="25563-103">使用系统监视器可以创建图表、警报、日志和报表，以监视 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例。</span><span class="sxs-lookup"><span data-stu-id="25563-103">System Monitor lets you create charts, alerts, logs, and reports to monitor an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="charts"></a><span data-ttu-id="25563-104">图表</span><span class="sxs-lookup"><span data-stu-id="25563-104">Charts</span></span>  
 <span data-ttu-id="25563-105">图表可以监视所选对象和计数器的当前性能，例如，CPU 使用率或磁盘 I/O。</span><span class="sxs-lookup"><span data-stu-id="25563-105">Charts can monitor the current performance of selected objects and counters; for example, the CPU usage or disk I/O.</span></span> <span data-ttu-id="25563-106">您可以向图表添加系统监视器对象和计数器的各种组合。</span><span class="sxs-lookup"><span data-stu-id="25563-106">You can add to a chart various combinations of System Monitor objects and counters.</span></span> <span data-ttu-id="25563-107">还可以向图表中添加 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 对象和计数器。</span><span class="sxs-lookup"><span data-stu-id="25563-107">You also can add [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows objects and counters to a chart.</span></span>  
  
 <span data-ttu-id="25563-108">每个图表表示要监视的信息的一个子集。</span><span class="sxs-lookup"><span data-stu-id="25563-108">Each chart represents a subset of information you want to monitor.</span></span> <span data-ttu-id="25563-109">例如，第一个图表可跟踪内存使用统计信息，第二个图表可跟踪磁盘 I/O 统计信息。</span><span class="sxs-lookup"><span data-stu-id="25563-109">For example, one chart can track memory usage statistics and a second chart can track disk I/O statistics.</span></span>  
  
 <span data-ttu-id="25563-110">对于以下任务使用图表将非常有用：</span><span class="sxs-lookup"><span data-stu-id="25563-110">Using a chart can be useful for the following tasks:</span></span>  
  
-   <span data-ttu-id="25563-111">分析计算机或应用程序运行缓慢或效率低下的原因。</span><span class="sxs-lookup"><span data-stu-id="25563-111">Investigating why a computer or application is slow or inefficient.</span></span>  
  
-   <span data-ttu-id="25563-112">连续监视系统，以找出间歇性性能问题。</span><span class="sxs-lookup"><span data-stu-id="25563-112">Continually monitoring systems to find intermittent performance problems.</span></span>  
  
-   <span data-ttu-id="25563-113">找出需提高性能的原因。</span><span class="sxs-lookup"><span data-stu-id="25563-113">Discovering why you need to increase capacity.</span></span>  
  
-   <span data-ttu-id="25563-114">用折线图显示一种趋势。</span><span class="sxs-lookup"><span data-stu-id="25563-114">Displaying a trend as a line chart.</span></span>  
  
-   <span data-ttu-id="25563-115">用柱状图显示比较结果。</span><span class="sxs-lookup"><span data-stu-id="25563-115">Displaying a comparison as a histogram chart.</span></span>  
  
 <span data-ttu-id="25563-116">图表对于短期、实时监视本地或远程计算机很有用，例如，希望在事件发生时对其进行监视。</span><span class="sxs-lookup"><span data-stu-id="25563-116">Charts are useful for short-term, real-time monitoring of a local or remote computer (for example, when you want to monitor an event as it occurs).</span></span>  
  
## <a name="alerts"></a><span data-ttu-id="25563-117">警报</span><span class="sxs-lookup"><span data-stu-id="25563-117">Alerts</span></span>  
 <span data-ttu-id="25563-118">利用警报，系统监视器可以跟踪特定的事件，并按要求向您通知这些事件。</span><span class="sxs-lookup"><span data-stu-id="25563-118">Using alerts, System Monitor tracks specific events and notifies you of these events as requested.</span></span> <span data-ttu-id="25563-119">警报日志可以监视所选计数器和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中对象的实例的性能。</span><span class="sxs-lookup"><span data-stu-id="25563-119">An alert log can monitor the current performance of selected counters and instances for objects in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="25563-120">当计数器超过给定值时，日志记录下这一事件的日期和时间。</span><span class="sxs-lookup"><span data-stu-id="25563-120">When a counter exceeds a given value, the log records the date and time of the event.</span></span> <span data-ttu-id="25563-121">事件也可产生网络警报。</span><span class="sxs-lookup"><span data-stu-id="25563-121">An event can also generate a network alert.</span></span> <span data-ttu-id="25563-122">可在一个事件第一次出现或每次出现时运行一个特定的程序。</span><span class="sxs-lookup"><span data-stu-id="25563-122">You can have a specified program run the first time or every time an event occurs.</span></span> <span data-ttu-id="25563-123">例如，一个警报可以向所有系统管理员发送一条网络消息，报告 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的磁盘空间不足。</span><span class="sxs-lookup"><span data-stu-id="25563-123">For example, an alert can send a network message to all system administrators that the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is getting low on disk space.</span></span>  
  
## <a name="logs"></a><span data-ttu-id="25563-124">日志</span><span class="sxs-lookup"><span data-stu-id="25563-124">Logs</span></span>  
 <span data-ttu-id="25563-125">日志可以记录选定对象和计算机的当前活动信息，以便日后查看和分析。</span><span class="sxs-lookup"><span data-stu-id="25563-125">Logs allow you to record information on the current activity of selected objects and computers for later viewing and analysis.</span></span> <span data-ttu-id="25563-126">可以将多个系统的数据收集到一个日志文件中。</span><span class="sxs-lookup"><span data-stu-id="25563-126">You can collect data from multiple systems into a single log file.</span></span> <span data-ttu-id="25563-127">例如，可以创建不同的日志，以积累不同计算机上所选对象的性能信息，供将来进行分析。</span><span class="sxs-lookup"><span data-stu-id="25563-127">For example, you can create different logs to accumulate information about the performance of selected objects on various computers for future analysis.</span></span> <span data-ttu-id="25563-128">可以在一个文件名下保存这些选择，当要创建另一用于比较的、具有相似信息的日志时再次使用它们。</span><span class="sxs-lookup"><span data-stu-id="25563-128">You can save these selections under a file name and reuse them when you want to create another log of similar information for comparison.</span></span>  
  
 <span data-ttu-id="25563-129">日志文件提供丰富的信息，用于故障处理和系统规划。</span><span class="sxs-lookup"><span data-stu-id="25563-129">Log files provide a wealth of information for troubleshooting or planning.</span></span> <span data-ttu-id="25563-130">当前活动的图表、警报和报告可提供当前的即时反馈，而使用日志文件则可以对计数器进行长时间跟踪。</span><span class="sxs-lookup"><span data-stu-id="25563-130">Whereas charts, alerts, and reports on current activity provide instant feedback, log files enable you to track counters over a long period of time.</span></span> <span data-ttu-id="25563-131">这样，便可以更彻底地检查信息和文档系统的性能。</span><span class="sxs-lookup"><span data-stu-id="25563-131">Thus, you can examine information more thoroughly and document system performance.</span></span>  
  
## <a name="reports"></a><span data-ttu-id="25563-132">报表</span><span class="sxs-lookup"><span data-stu-id="25563-132">Reports</span></span>  
 <span data-ttu-id="25563-133">报表可对选定对象显示不断变化的计数器和实例值。</span><span class="sxs-lookup"><span data-stu-id="25563-133">Reports allow you to display constantly changing counter and instance values for selected objects.</span></span> <span data-ttu-id="25563-134">每个实例的值记录在列中。</span><span class="sxs-lookup"><span data-stu-id="25563-134">Values appear in columns for each instance.</span></span> <span data-ttu-id="25563-135">可调整报表时间间隔、打印快照和导出数据。</span><span class="sxs-lookup"><span data-stu-id="25563-135">You can adjust report intervals, print snapshots, and export data.</span></span> <span data-ttu-id="25563-136">当需要显示原始数据时可使用报表。</span><span class="sxs-lookup"><span data-stu-id="25563-136">Use reports when you need to display the raw numbers.</span></span>  
  
 <span data-ttu-id="25563-137">有关创建图表、警报、日志和报表，或 Windows 对象和计数器的详细信息，请参阅 Windows 文档。</span><span class="sxs-lookup"><span data-stu-id="25563-137">For more information about creating charts, alerts, logs, and reports, or about Windows objects and counters, see the Windows documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25563-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="25563-138">See Also</span></span>  
 [<span data-ttu-id="25563-139">监视资源使用情况（系统监视器）</span><span class="sxs-lookup"><span data-stu-id="25563-139">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
