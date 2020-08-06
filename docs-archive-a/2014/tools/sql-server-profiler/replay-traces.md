---
title: 重播跟踪 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Profiler, replaying traces
- Run to Cursor option
- Toggle Breakpoint option
- traces [SQL Server], replaying
- replaying traces
- playback engine [SQL Server Profiler]
- events [SQL Server], replaying traces
- Profiler [SQL Server Profiler], replaying traces
ms.assetid: da958d3c-7f3e-44c9-aecc-8a9493bea7c0
author: stevestein
ms.author: sstein
ms.openlocfilehash: c485317d1343958f9c430b73d858130097d44d75
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692022"
---
# <a name="replay-traces"></a><span data-ttu-id="c642f-102">重播跟踪</span><span class="sxs-lookup"><span data-stu-id="c642f-102">Replay Traces</span></span>
  <span data-ttu-id="c642f-103">重播是重现在跟踪内捕获的活动的功能。</span><span class="sxs-lookup"><span data-stu-id="c642f-103">Replay is the ability to reproduce activity that has been captured in a trace.</span></span> <span data-ttu-id="c642f-104">在创建或编辑跟踪时，可以将跟踪保存到文件中并在以后重播。</span><span class="sxs-lookup"><span data-stu-id="c642f-104">When you create or edit a trace, you can save the trace to a file and replay it later.</span></span> <span data-ttu-id="c642f-105">可以使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 从一台计算机重播跟踪活动。</span><span class="sxs-lookup"><span data-stu-id="c642f-105">You can use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to replay trace activity from a single computer.</span></span> <span data-ttu-id="c642f-106">对于大型工作负荷，可使用分布式重播实用工具从多台计算机重播跟踪数据。</span><span class="sxs-lookup"><span data-stu-id="c642f-106">For large workloads, use the Distributed Replay Utility to replay trace data from multiple computers.</span></span>  
  
 <span data-ttu-id="c642f-107">本节描述如何使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]的重播功能。</span><span class="sxs-lookup"><span data-stu-id="c642f-107">This section describes how to use the replay features of [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="c642f-108">有关分布式重播实用工具的详细信息，请参阅 [SQL Server Distributed Replay](../distributed-replay/sql-server-distributed-replay.md)。</span><span class="sxs-lookup"><span data-stu-id="c642f-108">For more information about the Distributed Replay Utility, see [SQL Server Distributed Replay](../distributed-replay/sql-server-distributed-replay.md).</span></span>  
  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="c642f-109">具有多线程播放引擎，能模拟用户连接和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证。</span><span class="sxs-lookup"><span data-stu-id="c642f-109">features a multithreaded playback engine that can simulate user connections and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="c642f-110">重播对于解决应用程序或进程问题是很有用的。</span><span class="sxs-lookup"><span data-stu-id="c642f-110">Replay is useful to troubleshoot an application or process problem.</span></span> <span data-ttu-id="c642f-111">当标识出问题并进行了纠正后，请对纠正后的应用程序或进程运行找出潜在问题的跟踪。</span><span class="sxs-lookup"><span data-stu-id="c642f-111">When you have identified the problem and implemented corrections, run the trace that found the potential problem against the corrected application or process.</span></span> <span data-ttu-id="c642f-112">然后，重播原始跟踪并比较结果。</span><span class="sxs-lookup"><span data-stu-id="c642f-112">Then, replay the original trace and compare results.</span></span>  
  
 <span data-ttu-id="c642f-113">跟踪重播支持通过使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]“重播”菜单上的“切换断点”和“运行至光标处”选项来进行调试。</span><span class="sxs-lookup"><span data-stu-id="c642f-113">Trace replay supports debugging by using the **Toggle Breakpoint** and the **Run to Cursor** options on the [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **Replay** menu.</span></span> <span data-ttu-id="c642f-114">由于这些选项可以将跟踪重播打断为较短的段以便进行增量分析，因此尤其改善了对长脚本的分析。</span><span class="sxs-lookup"><span data-stu-id="c642f-114">These options especially improve the analysis of long scripts because they can break the replay of the trace into short segments so they can be analyzed incrementally.</span></span>  
  
 <span data-ttu-id="c642f-115">有关重播跟踪所需权限的信息，请参阅 [运行 SQL Server Profiler 所需的权限](permissions-required-to-run-sql-server-profiler.md)。</span><span class="sxs-lookup"><span data-stu-id="c642f-115">For information about the permissions required to replay traces, see [Permissions Required to Run SQL Server Profiler](permissions-required-to-run-sql-server-profiler.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c642f-116">本节内容</span><span class="sxs-lookup"><span data-stu-id="c642f-116">In This Section</span></span>  
  
|<span data-ttu-id="c642f-117">主题</span><span class="sxs-lookup"><span data-stu-id="c642f-117">Topic</span></span>|<span data-ttu-id="c642f-118">说明</span><span class="sxs-lookup"><span data-stu-id="c642f-118">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="c642f-119">重播要求</span><span class="sxs-lookup"><span data-stu-id="c642f-119">Replay Requirements</span></span>](replay-requirements.md)|<span data-ttu-id="c642f-120">说明跟踪定义必须包含的事件，以便它能使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]进行重播。</span><span class="sxs-lookup"><span data-stu-id="c642f-120">Describes the events that must be included in a trace definition so that it can be replayed with [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>|  
|[<span data-ttu-id="c642f-121">重播选项 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="c642f-121">Replay Options &#40;SQL Server Profiler&#41;</span></span>](replay-options-sql-server-profiler.md)|<span data-ttu-id="c642f-122">说明在 **的** “重播配置” [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]对话框中可以设置的选项。</span><span class="sxs-lookup"><span data-stu-id="c642f-122">Describes the options you can set in the **Replay Configuration** dialog box of [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>|  
|[<span data-ttu-id="c642f-123">重播跟踪的注意事项 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="c642f-123">Considerations for Replaying Traces &#40;SQL Server Profiler&#41;</span></span>](considerations-for-replaying-traces-sql-server-profiler.md)|<span data-ttu-id="c642f-124">说明不能使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 重播的跟踪事件以及重播跟踪对服务器性能的影响。</span><span class="sxs-lookup"><span data-stu-id="c642f-124">Describes trace events that can not be replayed with [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] and the effects on server performance of replaying traces.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c642f-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c642f-125">See Also</span></span>  
 [<span data-ttu-id="c642f-126">SQL Server 分布式重播</span><span class="sxs-lookup"><span data-stu-id="c642f-126">SQL Server Distributed Replay</span></span>](../distributed-replay/sql-server-distributed-replay.md)  
  
  
