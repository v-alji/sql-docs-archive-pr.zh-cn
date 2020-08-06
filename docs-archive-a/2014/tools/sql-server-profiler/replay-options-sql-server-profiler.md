---
title: 重播选项 (SQL Server Profiler) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], replaying
- replaying traces
- health monitor [SQL Server]
- Replay Configuration dialog box
ms.assetid: 58761a25-a84f-4a90-9c61-97700bc5ad9c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 695a1431145813f0a7829626a380e510d0e602e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692026"
---
# <a name="replay-options-sql-server-profiler"></a><span data-ttu-id="7adfe-102">重播选项 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="7adfe-102">Replay Options (SQL Server Profiler)</span></span>
  <span data-ttu-id="7adfe-103">使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]重播捕获的跟踪之前，请在 **“重播配置”** 对话框中指定重播选项。</span><span class="sxs-lookup"><span data-stu-id="7adfe-103">Before replaying a captured trace with [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], specify replay options in the **Replay Configuration** dialog box.</span></span> <span data-ttu-id="7adfe-104">若要启动此对话框，请在 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]中打开重播跟踪文件或表，然后在 **“重播”** 菜单上单击 **“开始”** 。</span><span class="sxs-lookup"><span data-stu-id="7adfe-104">To launch this dialog box, open the replay trace file or table in [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], and on the **Replay** menu, click **Start**.</span></span> <span data-ttu-id="7adfe-105">有关重播跟踪需要哪些权限的信息，请参阅 [Permissions Required to Run SQL Server Profiler](sql-server-profiler.md)。</span><span class="sxs-lookup"><span data-stu-id="7adfe-105">For information about what permissions are required to replay a trace, see [Permissions Required to Run SQL Server Profiler](sql-server-profiler.md).</span></span>  
  
 <span data-ttu-id="7adfe-106">本主题介绍使用 **“重播配置”** 对话框指定的选项。</span><span class="sxs-lookup"><span data-stu-id="7adfe-106">This topic describes the options specified with the **Replay Configuration** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7adfe-107">建议使用分布式重播实用工具重播密集型 OLTP 应用程序（具有大量活动并发连接或高吞吐量）。</span><span class="sxs-lookup"><span data-stu-id="7adfe-107">We recommend using the Distributed Replay Utility for replaying an intensive OLTP application (with many active concurrent connections or high throughput).</span></span> <span data-ttu-id="7adfe-108">分布式重播实用工具可以从多台计算机重播跟踪数据，并更好地模拟任务关键型工作负荷。</span><span class="sxs-lookup"><span data-stu-id="7adfe-108">The Distributed Replay Utility can replay trace data from multiple computers, better simulating a mission-critical workload.</span></span> <span data-ttu-id="7adfe-109">有关详细信息，请参阅 [SQL Server Distributed Replay](../distributed-replay/sql-server-distributed-replay.md)。</span><span class="sxs-lookup"><span data-stu-id="7adfe-109">For more information, see [SQL Server Distributed Replay](../distributed-replay/sql-server-distributed-replay.md).</span></span>  
  
## <a name="basic-replay-options"></a><span data-ttu-id="7adfe-110">基本重播选项</span><span class="sxs-lookup"><span data-stu-id="7adfe-110">Basic Replay Options</span></span>  
 <span data-ttu-id="7adfe-111">**重播服务器**</span><span class="sxs-lookup"><span data-stu-id="7adfe-111">**Replay server**</span></span>  
 <span data-ttu-id="7adfe-112">此服务器是要对其重播跟踪的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="7adfe-112">The server is the name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] against which you want to replay the trace.</span></span> <span data-ttu-id="7adfe-113">此服务器必须遵循 [Replay Requirements](replay-requirements.md)中说明的重播要求。</span><span class="sxs-lookup"><span data-stu-id="7adfe-113">The server must adhere to the replay requirements described in [Replay Requirements](replay-requirements.md)."</span></span>  
  
 <span data-ttu-id="7adfe-114">**保存到文件**</span><span class="sxs-lookup"><span data-stu-id="7adfe-114">**Save to file**</span></span>  
 <span data-ttu-id="7adfe-115">用于写入重播跟踪的结果以供将来查看的输出文件。</span><span class="sxs-lookup"><span data-stu-id="7adfe-115">The output file where the result of replaying the trace is written for later viewing.</span></span> <span data-ttu-id="7adfe-116">默认情况下， [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 只在屏幕上显示重播跟踪的结果。</span><span class="sxs-lookup"><span data-stu-id="7adfe-116">By default, [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] displays only the results of replaying the trace on the screen.</span></span>  
  
 <span data-ttu-id="7adfe-117">**保存到表**</span><span class="sxs-lookup"><span data-stu-id="7adfe-117">**Save to table**</span></span>  
 <span data-ttu-id="7adfe-118">用于写入重播跟踪的结果以供将来查看的数据库表。</span><span class="sxs-lookup"><span data-stu-id="7adfe-118">The database table where the result of replaying the trace is written for later viewing.</span></span>  
  
 <span data-ttu-id="7adfe-119">**重播线程数**</span><span class="sxs-lookup"><span data-stu-id="7adfe-119">**Number of replay threads**</span></span>  
 <span data-ttu-id="7adfe-120">指定要并发使用的重播线程数。</span><span class="sxs-lookup"><span data-stu-id="7adfe-120">Specify the number of replay threads to use concurrently.</span></span> <span data-ttu-id="7adfe-121">此数值越高，重播过程中占用的资源越多，但重播速度也越快。</span><span class="sxs-lookup"><span data-stu-id="7adfe-121">A higher number consumes more resources during replay, but replay is faster.</span></span> <span data-ttu-id="7adfe-122">使用多个线程时，不能完全保持事件的排序顺序。</span><span class="sxs-lookup"><span data-stu-id="7adfe-122">Event ordering is not fully maintained when multiple threads are used.</span></span>  
  
 <span data-ttu-id="7adfe-123">**按跟踪事件的顺序重播事件**</span><span class="sxs-lookup"><span data-stu-id="7adfe-123">**Replay events in the order they were traced**</span></span>  
 <span data-ttu-id="7adfe-124">使您可以使用调试方法，如逐步重播每个跟踪。</span><span class="sxs-lookup"><span data-stu-id="7adfe-124">Allows you to use debugging methods such as stepping through each trace.</span></span> <span data-ttu-id="7adfe-125">如果未选中此选项，重播将不能保证重播事件的顺序与原先捕获事件的顺序一致。</span><span class="sxs-lookup"><span data-stu-id="7adfe-125">If this option is not selected, replay does not guarantee that events are replayed in an order that is consistent with the order in which events were originally captured.</span></span>  
  
 <span data-ttu-id="7adfe-126">**使用多个线程重播事件**</span><span class="sxs-lookup"><span data-stu-id="7adfe-126">**Replay events using multiple threads**</span></span>  
 <span data-ttu-id="7adfe-127">优化性能并禁用调试。</span><span class="sxs-lookup"><span data-stu-id="7adfe-127">Optimizes performance and disables debugging.</span></span> <span data-ttu-id="7adfe-128">将按照对某一特定的服务器进程 ID (SPID) 记录事件的顺序来重播事件，但是不能保证 SPID 的排序顺序。</span><span class="sxs-lookup"><span data-stu-id="7adfe-128">Events are replayed in the order they were recorded for a particular server process ID (SPID), but ordering of SPIDs is not guaranteed.</span></span>  
  
 <span data-ttu-id="7adfe-129">**显示重播结果**</span><span class="sxs-lookup"><span data-stu-id="7adfe-129">**Display replay results**</span></span>  
 <span data-ttu-id="7adfe-130">显示重播的结果。</span><span class="sxs-lookup"><span data-stu-id="7adfe-130">Display the results of the replay.</span></span> <span data-ttu-id="7adfe-131">这是默认选项。</span><span class="sxs-lookup"><span data-stu-id="7adfe-131">This is the default option.</span></span> <span data-ttu-id="7adfe-132">如果正在重播的跟踪非常大，可能需要禁用此选项以节省磁盘空间。</span><span class="sxs-lookup"><span data-stu-id="7adfe-132">If the trace you are replaying is very large, you may want to disable this to save disk space.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7adfe-133">为了获得最佳的重播性能，建议选择使用多线程重播事件，不要选择显示重播结果。</span><span class="sxs-lookup"><span data-stu-id="7adfe-133">For best replay performance, we recommend that you select to replay events using multiple threads, and do not select to display the replay results.</span></span>  
  
## <a name="advanced-replay-options"></a><span data-ttu-id="7adfe-134">高级重播选项</span><span class="sxs-lookup"><span data-stu-id="7adfe-134">Advanced Replay Options</span></span>  
 <span data-ttu-id="7adfe-135">**重播系统 SPID**</span><span class="sxs-lookup"><span data-stu-id="7adfe-135">**Replay system SPIDs**</span></span>  
 <span data-ttu-id="7adfe-136">重播所有 SPID。</span><span class="sxs-lookup"><span data-stu-id="7adfe-136">Replay all SPIDs.</span></span> <span data-ttu-id="7adfe-137">这是默认选项。</span><span class="sxs-lookup"><span data-stu-id="7adfe-137">This is the default option.</span></span>  
  
 <span data-ttu-id="7adfe-138">**仅重播一个 SPID**</span><span class="sxs-lookup"><span data-stu-id="7adfe-138">**Replay one SPID only**</span></span>  
 <span data-ttu-id="7adfe-139">重播从列表中选择的 SPID 编号。</span><span class="sxs-lookup"><span data-stu-id="7adfe-139">Replays the SPID number you choose from the list.</span></span>  
  
 <span data-ttu-id="7adfe-140">**按日期和时间限制重播**</span><span class="sxs-lookup"><span data-stu-id="7adfe-140">**Limit replay by date and time**</span></span>  
 <span data-ttu-id="7adfe-141">重播指定的“开始时间”  和“结束时间”  内的跟踪。</span><span class="sxs-lookup"><span data-stu-id="7adfe-141">Replays the trace for the specified **Start time** and **End time**.</span></span>  
  
 <span data-ttu-id="7adfe-142">**Health Monitor 等待间隔**</span><span class="sxs-lookup"><span data-stu-id="7adfe-142">**Health monitor wait interval**</span></span>  
 <span data-ttu-id="7adfe-143">设置允许进程运行的时间，经过此时间段后 Health Monitor 将终止该进程。</span><span class="sxs-lookup"><span data-stu-id="7adfe-143">Sets the amount of time a process is allowed to run before the health monitor terminates it.</span></span>  
  
 <span data-ttu-id="7adfe-144">**Health Monitor 轮询间隔**</span><span class="sxs-lookup"><span data-stu-id="7adfe-144">**Health monitor poll interval**</span></span>  
 <span data-ttu-id="7adfe-145">设置 Health Monitor 轮询终止候选项的频率。</span><span class="sxs-lookup"><span data-stu-id="7adfe-145">Sets how often the health monitor polls candidates for termination.</span></span>  
  
 <span data-ttu-id="7adfe-146">**启用 SQL Server 阻塞的进程监视器**</span><span class="sxs-lookup"><span data-stu-id="7adfe-146">**Enable SQL Server blocked processes monitor**</span></span>  
 <span data-ttu-id="7adfe-147">设置阻塞进程监视器搜索已阻塞的进程或正在阻塞的进程的频率。</span><span class="sxs-lookup"><span data-stu-id="7adfe-147">Sets how often the blocked processes monitor searches for blocked or blocking processes.</span></span>  
  
## <a name="about-the-health-monitor"></a><span data-ttu-id="7adfe-148">关于 Health Monitor</span><span class="sxs-lookup"><span data-stu-id="7adfe-148">About the Health Monitor</span></span>  
 <span data-ttu-id="7adfe-149">Health Monitor 是一个应用程序线程，用于监视重播跟踪过程中涉及的模拟进程，并结束在重播过程中阻塞的那些进程。</span><span class="sxs-lookup"><span data-stu-id="7adfe-149">The health monitor is an application thread that monitors the simulated processes involved in replaying a trace, and ends those processes that are blocked within the replay.</span></span> <span data-ttu-id="7adfe-150">在“重播配置”对话框的“高级重播选项”选项卡中，可以指定 Health Monitor 在结束阻塞进程之前应等待的秒数（**Health Monitor 等待间隔**）。</span><span class="sxs-lookup"><span data-stu-id="7adfe-150">In the **Advanced Replay Options** tab of the **Replay Configuration** dialog box, you can specify how long the health monitor should wait in seconds before ending a blocked process (**Health monitor wait interval**).</span></span> <span data-ttu-id="7adfe-151">如果将此间隔设置为 0，则在重播跟踪过程中，Health Monitor 永远不会结束模拟阻塞进程。</span><span class="sxs-lookup"><span data-stu-id="7adfe-151">If you set this interval to 0, the health monitor never ends simulated blocking processes in the replaying trace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7adfe-152">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7adfe-152">See Also</span></span>  
 <span data-ttu-id="7adfe-153">[重播跟踪](replay-traces.md) </span><span class="sxs-lookup"><span data-stu-id="7adfe-153">[Replay Traces](replay-traces.md) </span></span>  
 <span data-ttu-id="7adfe-154">[重播要求](replay-requirements.md) </span><span class="sxs-lookup"><span data-stu-id="7adfe-154">[Replay Requirements](replay-requirements.md) </span></span>  
 [<span data-ttu-id="7adfe-155">重播跟踪的注意事项 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="7adfe-155">Considerations for Replaying Traces &#40;SQL Server Profiler&#41;</span></span>](considerations-for-replaying-traces-sql-server-profiler.md)  
  
  
