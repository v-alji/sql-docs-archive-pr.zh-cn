---
title: SQL Server Profiler 模板和权限 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- Profiler [SQL Server Profiler], about SQL Server Profiler
- SQL Server Profiler, about SQL Server Profiler
ms.assetid: 6d00378a-5d74-463b-9ed6-a2685306a9d2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8f3e3bc180db4e59def5af7eae39d8f177c93268
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578605"
---
# <a name="sql-server-profiler-templates-and-permissions"></a><span data-ttu-id="b155b-102">SQL Server Profiler 模板和权限</span><span class="sxs-lookup"><span data-stu-id="b155b-102">SQL Server Profiler Templates and Permissions</span></span>
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="b155b-103">可显示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 如何在内部解析查询。</span><span class="sxs-lookup"><span data-stu-id="b155b-103">shows how [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resolves queries internally.</span></span> <span data-ttu-id="b155b-104">这就使管理员能够准确查看提交到服务器的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句或多维表达式，以及服务器是如何访问数据库或多维数据集以返回结果集的。</span><span class="sxs-lookup"><span data-stu-id="b155b-104">This allows administrators to see exactly what [!INCLUDE[tsql](../../includes/tsql-md.md)] statements or Multi-Dimensional Expressions are submitted to the server and how the server accesses the database or cube to return result sets.</span></span>  
  
 <span data-ttu-id="b155b-105">使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]可以执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="b155b-105">Using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], you can do the following:</span></span>  
  
-   <span data-ttu-id="b155b-106">创建基于可重用模板的跟踪</span><span class="sxs-lookup"><span data-stu-id="b155b-106">Create a trace that is based on a reusable template</span></span>  
  
-   <span data-ttu-id="b155b-107">当跟踪运行时监视跟踪结果</span><span class="sxs-lookup"><span data-stu-id="b155b-107">Watch the trace results as the trace runs</span></span>  
  
-   <span data-ttu-id="b155b-108">将跟踪结果存储在表中</span><span class="sxs-lookup"><span data-stu-id="b155b-108">Store the trace results in a table</span></span>  
  
-   <span data-ttu-id="b155b-109">根据需要启动、停止、暂停和修改跟踪结果</span><span class="sxs-lookup"><span data-stu-id="b155b-109">Start, stop, pause, and modify the trace results as necessary</span></span>  
  
-   <span data-ttu-id="b155b-110">重播跟踪结果</span><span class="sxs-lookup"><span data-stu-id="b155b-110">Replay the trace results</span></span>  
  
 <span data-ttu-id="b155b-111">使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 只监视感兴趣的事件。</span><span class="sxs-lookup"><span data-stu-id="b155b-111">Use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to monitor only the events in which you are interested.</span></span> <span data-ttu-id="b155b-112">如果跟踪变得太大，可以基于所需的信息进行筛选，以便只收集部分事件数据。</span><span class="sxs-lookup"><span data-stu-id="b155b-112">If traces are becoming too large, you can filter them based on the information you want, so that only a subset of the event data is collected.</span></span> <span data-ttu-id="b155b-113">监视过多事件会增加服务器和监视进程的开销，并且可能导致跟踪文件或跟踪表变得很大，尤其是当监视进程持续很长时间时。</span><span class="sxs-lookup"><span data-stu-id="b155b-113">Monitoring too many events adds overhead to the server and the monitoring process, and can cause the trace file or trace table to grow very large, especially when the monitoring process takes place over a long period of time.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b155b-114">大于 1 GB 的跟踪列值将返回错误，并且会在跟踪输出中被截断。</span><span class="sxs-lookup"><span data-stu-id="b155b-114">Trace column values greater than 1 GB return an error and are truncated in the trace output.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b155b-115">本节内容</span><span class="sxs-lookup"><span data-stu-id="b155b-115">In This Section</span></span>  
  
|<span data-ttu-id="b155b-116">主题</span><span class="sxs-lookup"><span data-stu-id="b155b-116">Topic</span></span>|<span data-ttu-id="b155b-117">说明</span><span class="sxs-lookup"><span data-stu-id="b155b-117">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="b155b-118">SQL Server Profiler 模板</span><span class="sxs-lookup"><span data-stu-id="b155b-118">SQL Server Profiler Templates</span></span>](sql-server-profiler-templates.md)|<span data-ttu-id="b155b-119">介绍 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]附带的预定义跟踪模板。</span><span class="sxs-lookup"><span data-stu-id="b155b-119">Contains information about the predefined trace templates that ship with [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>|  
|[<span data-ttu-id="b155b-120">运行 SQL Server Profiler 所需的权限</span><span class="sxs-lookup"><span data-stu-id="b155b-120">Permissions Required to Run SQL Server Profiler</span></span>](permissions-required-to-run-sql-server-profiler.md)|<span data-ttu-id="b155b-121">介绍运行 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]时所需的权限。</span><span class="sxs-lookup"><span data-stu-id="b155b-121">Contains information about the permissions that are required to run [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>|  
|[<span data-ttu-id="b155b-122">保存跟踪和跟踪模板</span><span class="sxs-lookup"><span data-stu-id="b155b-122">Save Traces and Trace Templates</span></span>](save-traces-and-trace-templates.md)|<span data-ttu-id="b155b-123">介绍如何保存跟踪输出和将跟踪定义保存到模板中。</span><span class="sxs-lookup"><span data-stu-id="b155b-123">Contains information about saving trace output and about saving trace definitions into a template.</span></span>|  
|[<span data-ttu-id="b155b-124">修改跟踪模板</span><span class="sxs-lookup"><span data-stu-id="b155b-124">Modify Trace Templates</span></span>](modify-trace-templates.md)|<span data-ttu-id="b155b-125">介绍如何使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 或 [!INCLUDE[tsql](../../includes/tsql-md.md)]来修改跟踪模板。</span><span class="sxs-lookup"><span data-stu-id="b155b-125">Contains information about modifying trace templates by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] or by using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>|  
|[<span data-ttu-id="b155b-126">启动跟踪</span><span class="sxs-lookup"><span data-stu-id="b155b-126">Start a Trace</span></span>](start-a-trace.md)|<span data-ttu-id="b155b-127">介绍启动、暂停或停止跟踪时将发生的情况。</span><span class="sxs-lookup"><span data-stu-id="b155b-127">Contains information about what happens when you start, pause, or stop a trace.</span></span>|  
|[<span data-ttu-id="b155b-128">将跟踪与 Windows 性能日志数据关联</span><span class="sxs-lookup"><span data-stu-id="b155b-128">Correlate a Trace with Windows Performance Log Data</span></span>](correlate-a-trace-with-windows-performance-log-data.md)|<span data-ttu-id="b155b-129">介绍如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Profiler 将 Windows 性能日志数据与跟踪相关联。</span><span class="sxs-lookup"><span data-stu-id="b155b-129">Contains information about correlating Windows performance log data with a trace by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Profiler.</span></span>|  
|[<span data-ttu-id="b155b-130">使用 SQL Server Profiler 查看和分析跟踪</span><span class="sxs-lookup"><span data-stu-id="b155b-130">View and Analyze Traces with SQL Server Profiler</span></span>](view-and-analyze-traces-with-sql-server-profiler.md)|<span data-ttu-id="b155b-131">介绍如何使用跟踪对数据进行故障排除、在跟踪中显示对象名以及在跟踪中查找事件。</span><span class="sxs-lookup"><span data-stu-id="b155b-131">Contains information about using traces to troubleshoot data, displaying object names in a trace, and finding events in a trace.</span></span>|  
|[<span data-ttu-id="b155b-132">使用 SQL Server Profiler 分析死锁</span><span class="sxs-lookup"><span data-stu-id="b155b-132">Analyze Deadlocks with SQL Server Profiler</span></span>](analyze-deadlocks-with-sql-server-profiler.md)|<span data-ttu-id="b155b-133">介绍如何使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 识别造成死锁的原因。</span><span class="sxs-lookup"><span data-stu-id="b155b-133">Contains information about using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to identify the cause of a deadlock.</span></span>|  
|[<span data-ttu-id="b155b-134">在 SQL Server Profiler 中使用 SHOWPLAN 结果来分析查询</span><span class="sxs-lookup"><span data-stu-id="b155b-134">Analyze Queries with SHOWPLAN Results in SQL Server Profiler</span></span>](analyze-queries-with-showplan-results-in-sql-server-profiler.md)|<span data-ttu-id="b155b-135">介绍如何使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 收集和显示“显示计划”和“显示计划统计信息”的结果。</span><span class="sxs-lookup"><span data-stu-id="b155b-135">Contains information about using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to collect and display Showplan and Showplan Statistics results.</span></span>|  
|[<span data-ttu-id="b155b-136">使用 SQL Server Profiler 筛选跟踪</span><span class="sxs-lookup"><span data-stu-id="b155b-136">Filter Traces with SQL Server Profiler</span></span>](filter-traces-with-sql-server-profiler.md)|<span data-ttu-id="b155b-137">介绍如何使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]设置针对数据列的筛选器以筛选跟踪输出。</span><span class="sxs-lookup"><span data-stu-id="b155b-137">Contains information about setting filters on data columns to filter trace output by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>|  
|[<span data-ttu-id="b155b-138">重播跟踪</span><span class="sxs-lookup"><span data-stu-id="b155b-138">Replay Traces</span></span>](replay-traces.md)|<span data-ttu-id="b155b-139">解释重播跟踪的意义以及重播跟踪所需的条件。</span><span class="sxs-lookup"><span data-stu-id="b155b-139">Contains information that explains what replaying a trace means and what is required to replay a trace.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b155b-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b155b-140">See Also</span></span>  
 <span data-ttu-id="b155b-141">[SQL Server 事件探查器](sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="b155b-141">[SQL Server Profiler](sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="b155b-142">启动 SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="b155b-142">Start SQL Server Profiler</span></span>](start-sql-server-profiler.md)  
  
  
