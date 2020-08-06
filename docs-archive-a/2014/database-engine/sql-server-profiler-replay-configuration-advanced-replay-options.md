---
title: SQL Server Profiler-重播配置 (高级重播选项) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.replay.generaloptions.advanced.f1
helpviewer_keywords:
- Replay Configuration dialog box
ms.assetid: b4eb34f7-3af6-4a44-ba7e-2b8430ec3cd7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 95070d8defb5b7778859ce470aaa8cfc85955ba6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691843"
---
# <a name="sql-server-profiler---replay-configuration-advanced-replay-options"></a><span data-ttu-id="2ca09-102">SQL Server Profiler - 重播配置（高级重播选项）</span><span class="sxs-lookup"><span data-stu-id="2ca09-102">SQL Server Profiler - Replay Configuration (Advanced Replay Options)</span></span>
  <span data-ttu-id="2ca09-103">在 **“重播配置”** 对话框中，使用 **“高级重播选项”** 选项卡可以指定如何重播跟踪文件。</span><span class="sxs-lookup"><span data-stu-id="2ca09-103">In the **Replay Configuration** dialog box, use the **Advanced Replay Options** tab to specify how to replay a trace file.</span></span>  
  
 <span data-ttu-id="2ca09-104">若要查看此窗口，请使用 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 打开包含相应重播事件的跟踪文件或表。</span><span class="sxs-lookup"><span data-stu-id="2ca09-104">To view this window, use [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] to open a trace file or table that contains the appropriate events for replay.</span></span> <span data-ttu-id="2ca09-105">有关详细信息，请参阅 [Replay Requirements](../tools/sql-server-profiler/replay-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2ca09-105">For more information, see [Replay Requirements](../tools/sql-server-profiler/replay-requirements.md).</span></span> <span data-ttu-id="2ca09-106">打开跟踪文件或表后，在 **“重播”** 菜单上，单击 **“启动”**，连接到要重播跟踪的 SQL Server 实例，再单击 **“高级重播选项”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="2ca09-106">While the trace file or table is open, on the **Replay** menu, click **Start**, connect to the instance of SQL Server where you want to replay the trace, and then click the **Advanced Replay Options** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="2ca09-107">选项</span><span class="sxs-lookup"><span data-stu-id="2ca09-107">Options</span></span>  
 <span data-ttu-id="2ca09-108">**重播系统 SPID**</span><span class="sxs-lookup"><span data-stu-id="2ca09-108">**Replay system SPIDs**</span></span>  
 <span data-ttu-id="2ca09-109">指定 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 是否重播系统进程标识符 (SPID)。</span><span class="sxs-lookup"><span data-stu-id="2ca09-109">Specifies whether [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] replays system process identifiers (SPIDs).</span></span>  
  
 <span data-ttu-id="2ca09-110">**仅重播一个 SPID**</span><span class="sxs-lookup"><span data-stu-id="2ca09-110">**Replay one SPID only**</span></span>  
 <span data-ttu-id="2ca09-111">仅重播与所选 SPID 相关的源跟踪文件中的活动。</span><span class="sxs-lookup"><span data-stu-id="2ca09-111">Replays only the activity in the source trace file that is related to the selected SPID.</span></span>  
  
 <span data-ttu-id="2ca09-112">**要重播的 SPID**</span><span class="sxs-lookup"><span data-stu-id="2ca09-112">**SPID to replay**</span></span>  
 <span data-ttu-id="2ca09-113">指定要重播的 SPID。</span><span class="sxs-lookup"><span data-stu-id="2ca09-113">Specify which SPID to replay.</span></span>  
  
 <span data-ttu-id="2ca09-114">**按日期和时间限制重播**</span><span class="sxs-lookup"><span data-stu-id="2ca09-114">**Limit replay by date and time**</span></span>  
 <span data-ttu-id="2ca09-115">选中此选项可以仅重播部分源跟踪文件。</span><span class="sxs-lookup"><span data-stu-id="2ca09-115">Check to replay only a portion of the source trace file.</span></span>  
  
 <span data-ttu-id="2ca09-116">**开始时间**</span><span class="sxs-lookup"><span data-stu-id="2ca09-116">**Start time**</span></span>  
 <span data-ttu-id="2ca09-117">源跟踪文件中重播开始的日期和时间。</span><span class="sxs-lookup"><span data-stu-id="2ca09-117">Date and time in the source trace file where the replay should start.</span></span>  
  
 <span data-ttu-id="2ca09-118">**结束时间**</span><span class="sxs-lookup"><span data-stu-id="2ca09-118">**End time**</span></span>  
 <span data-ttu-id="2ca09-119">源跟踪文件中重播结束的日期和时间。</span><span class="sxs-lookup"><span data-stu-id="2ca09-119">Date and time in the source trace file where the replay should stop.</span></span>  
  
 <span data-ttu-id="2ca09-120">**Health Monitor 等待间隔(秒)**</span><span class="sxs-lookup"><span data-stu-id="2ca09-120">**Health monitor wait interval (sec)**</span></span>  
 <span data-ttu-id="2ca09-121">指定重播的等待间隔（秒）。</span><span class="sxs-lookup"><span data-stu-id="2ca09-121">Specify the wait interval to replay in seconds.</span></span> <span data-ttu-id="2ca09-122">默认值为 3600 秒（1 小时）。</span><span class="sxs-lookup"><span data-stu-id="2ca09-122">Default is 3600 seconds (1 hour).</span></span> <span data-ttu-id="2ca09-123">此设置影响进程在被 health monitor 终止前所允许运行的时间。</span><span class="sxs-lookup"><span data-stu-id="2ca09-123">This setting affects the amount of time a process is allowed to run before being terminated by the health monitor.</span></span>  
  
 <span data-ttu-id="2ca09-124">**Health Monitor 轮询间隔(秒)**</span><span class="sxs-lookup"><span data-stu-id="2ca09-124">**Health monitor poll interval (sec)**</span></span>  
 <span data-ttu-id="2ca09-125">指定重播过程中的 Health Monitor 轮询间隔（秒）。</span><span class="sxs-lookup"><span data-stu-id="2ca09-125">Specify the health monitor poll interval during replay in seconds.</span></span> <span data-ttu-id="2ca09-126">默认值为 60 秒。</span><span class="sxs-lookup"><span data-stu-id="2ca09-126">Default is 60 seconds.</span></span> <span data-ttu-id="2ca09-127">使用此值，用户可以配置 Health Monitor 对终止候选项的轮询频率。</span><span class="sxs-lookup"><span data-stu-id="2ca09-127">This value allows the user to configure how often the health monitor polls for candidates for termination.</span></span>  
  
 <span data-ttu-id="2ca09-128">**启用 SQL Server 阻塞的进程监视器**</span><span class="sxs-lookup"><span data-stu-id="2ca09-128">**Enable SQL Server blocked processes monitor**</span></span>  
 <span data-ttu-id="2ca09-129">启用一个进程，搜索已阻塞或正在阻塞的进程。</span><span class="sxs-lookup"><span data-stu-id="2ca09-129">Enables a process that searches for blocked or blocking processes.</span></span>  
  
 <span data-ttu-id="2ca09-130">**阻塞的进程监视器等待间隔(秒)**</span><span class="sxs-lookup"><span data-stu-id="2ca09-130">**Blocked processes monitor wait interval (sec)**</span></span>  
 <span data-ttu-id="2ca09-131">配置阻塞的进程监视器搜索已阻塞的或正在阻塞的进程的频率。</span><span class="sxs-lookup"><span data-stu-id="2ca09-131">Configures how often the blocked processes monitor searches for blocked or blocking processes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ca09-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2ca09-132">See Also</span></span>  
 <span data-ttu-id="2ca09-133">[重播跟踪表 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="2ca09-133">[Replay a Trace Table &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="2ca09-134">[重播跟踪文件 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="2ca09-134">[Replay a Trace File &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="2ca09-135">重播跟踪</span><span class="sxs-lookup"><span data-stu-id="2ca09-135">Replay Traces</span></span>](../tools/sql-server-profiler/replay-traces.md)  
  
  
