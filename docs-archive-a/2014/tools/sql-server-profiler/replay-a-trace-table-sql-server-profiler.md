---
title: 重播跟踪表 (SQL Server Profiler) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], replaying
- replaying traces
ms.assetid: 6a0ad817-3d8d-4495-889d-c66a7ef9e8bb
author: stevestein
ms.author: sstein
ms.openlocfilehash: f3c26858fa852686bc3d9ccf4a26d47e04852647
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690267"
---
# <a name="replay-a-trace-table-sql-server-profiler"></a><span data-ttu-id="9207c-102">重播跟踪表 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="9207c-102">Replay a Trace Table (SQL Server Profiler)</span></span>
  <span data-ttu-id="9207c-103">重播是指打开已保存的跟踪并对其重播的功能。</span><span class="sxs-lookup"><span data-stu-id="9207c-103">Replay is the ability to open a saved trace and replay it again.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="9207c-104">具有多线程播放引擎，能模拟用户连接和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证。</span><span class="sxs-lookup"><span data-stu-id="9207c-104">features a multithreaded playback engine that can simulate user connections and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="9207c-105">重播对于解决应用程序或进程问题是很有用的。</span><span class="sxs-lookup"><span data-stu-id="9207c-105">Replay is useful to troubleshoot an application or process problem.</span></span> <span data-ttu-id="9207c-106">在您确定问题并进行更正后，请对更正后的应用程序或进程运行发现该潜在问题的跟踪。</span><span class="sxs-lookup"><span data-stu-id="9207c-106">When you identify the problem and implement corrections, run the trace that found the potential problem against the corrected application or process.</span></span> <span data-ttu-id="9207c-107">然后，重播原始跟踪并比较结果。</span><span class="sxs-lookup"><span data-stu-id="9207c-107">Then, replay the original trace and compare results.</span></span>  
  
 <span data-ttu-id="9207c-108">除了要监视的任何其他事件类之外，还必须捕获特定的事件类才能启用重播。</span><span class="sxs-lookup"><span data-stu-id="9207c-108">In addition to any other event classes you want to monitor, specific event classes must be captured to enable replay.</span></span> <span data-ttu-id="9207c-109">如果使用 **TSQL_Replay** 跟踪模板，则在默认情况下将捕获这些事件。</span><span class="sxs-lookup"><span data-stu-id="9207c-109">These events are captured by default if you use the **TSQL_Replay** trace template.</span></span> <span data-ttu-id="9207c-110">有关详细信息，请参阅 [Replay Requirements](replay-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9207c-110">For more information, see [Replay Requirements](replay-requirements.md).</span></span>  
  
### <a name="to-replay-a-trace-table"></a><span data-ttu-id="9207c-111">重播跟踪表</span><span class="sxs-lookup"><span data-stu-id="9207c-111">To replay a trace table</span></span>  
  
1.  <span data-ttu-id="9207c-112">请打开需要重播的包含事件类的跟踪表。</span><span class="sxs-lookup"><span data-stu-id="9207c-112">Open a trace table that contains the event classes necessary for replay.</span></span>  
  
2.  <span data-ttu-id="9207c-113">在 **“重播”** 菜单上，单击 **“开始”** ，然后连接到要重播跟踪的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="9207c-113">On the **Replay** menu, click **Start**, and connect to the server instance where you want to replay the trace.</span></span>  
  
3.  <span data-ttu-id="9207c-114">在 **“重播配置”** 对话框的 **“基本重播选项”** 选项卡上，指定 **“重播服务器”** 。</span><span class="sxs-lookup"><span data-stu-id="9207c-114">In the **Replay Configuration** dialog box, on the **Basic Replay Options** tab, specify **Replay server**.</span></span> <span data-ttu-id="9207c-115">单击 **“更改”** 以更改 **“重播服务器”** 框中显示的服务器。</span><span class="sxs-lookup"><span data-stu-id="9207c-115">Click **Change** to change the server that is displayed in the **Replay server** box.</span></span>  
  
4.  <span data-ttu-id="9207c-116">根据需要，选择下列目标位置之一以在其中保存重播：</span><span class="sxs-lookup"><span data-stu-id="9207c-116">Optionally, select one of the following destinations in which to save the replay:</span></span>  
  
    -   <span data-ttu-id="9207c-117">**保存到文件** 指定用于保存重播的文件。</span><span class="sxs-lookup"><span data-stu-id="9207c-117">**Save to file,** which specifies a file in which to save the replay.</span></span>  
  
    -   <span data-ttu-id="9207c-118">**保存到表**，该选项指定保存重播的数据库表。</span><span class="sxs-lookup"><span data-stu-id="9207c-118">**Save to table**, which specifies a database table in which to save the replay.</span></span>  
  
5.  <span data-ttu-id="9207c-119">选择“按跟踪的顺序重播事件”  或“使用多个线程重播事件”  。</span><span class="sxs-lookup"><span data-stu-id="9207c-119">Choose either **Replay the events in the order they were traced**or **Replay events using multiple threads**.</span></span> <span data-ttu-id="9207c-120">下表列出了这些设置之间的差异。</span><span class="sxs-lookup"><span data-stu-id="9207c-120">The following table explains the difference between these settings.</span></span>  
  
    |<span data-ttu-id="9207c-121">选项</span><span class="sxs-lookup"><span data-stu-id="9207c-121">Option</span></span>|<span data-ttu-id="9207c-122">说明</span><span class="sxs-lookup"><span data-stu-id="9207c-122">Description</span></span>|  
    |------------|-----------------|  
    |<span data-ttu-id="9207c-123">**按跟踪事件的顺序重播事件**</span><span class="sxs-lookup"><span data-stu-id="9207c-123">**Replay events in the order they were traced**</span></span>|<span data-ttu-id="9207c-124">按记录事件的顺序重播事件。</span><span class="sxs-lookup"><span data-stu-id="9207c-124">Replays events in the order they were recorded.</span></span> <span data-ttu-id="9207c-125">此选项启用调试。</span><span class="sxs-lookup"><span data-stu-id="9207c-125">This option enables debugging.</span></span>|  
    |<span data-ttu-id="9207c-126">**使用多个线程重播事件**</span><span class="sxs-lookup"><span data-stu-id="9207c-126">**Replay events using multiple threads**</span></span>|<span data-ttu-id="9207c-127">此选项使用多个线程重播各个事件，而不考虑其顺序。</span><span class="sxs-lookup"><span data-stu-id="9207c-127">This option uses multiple threads to replay each event regardless of the sequence.</span></span> <span data-ttu-id="9207c-128">此选项用于优化性能。</span><span class="sxs-lookup"><span data-stu-id="9207c-128">This option optimizes performance.</span></span>|  
  
6.  <span data-ttu-id="9207c-129">选择 **“显示重播结果”** 以在重播时查看结果。</span><span class="sxs-lookup"><span data-stu-id="9207c-129">Select **Display replay results** to view the replay as it occurs.</span></span>  
  
7.  <span data-ttu-id="9207c-130">（可选）单击“高级重播选项”  选项卡来指定下列选项：</span><span class="sxs-lookup"><span data-stu-id="9207c-130">Optionally, click the **Advanced Replay Options**tab to specify the following options:</span></span>  
  
    -   <span data-ttu-id="9207c-131">若要重播所有服务器进程 ID (SPID)，请选择“重播系统 SPID”  。</span><span class="sxs-lookup"><span data-stu-id="9207c-131">To replay all server process IDs (SPIDs), select **Replay system SPIDs**.</span></span>  
  
    -   <span data-ttu-id="9207c-132">若要仅重播属于特定 SPID 的进程，请选择 **“仅重播一个 SPID”** 。</span><span class="sxs-lookup"><span data-stu-id="9207c-132">To limit the replay to processes belonging to a specific SPID, select **Replay one SPID only**.</span></span> <span data-ttu-id="9207c-133">在“要重播的 SPID”  框中，键入 SPID。</span><span class="sxs-lookup"><span data-stu-id="9207c-133">In the **SPID to replay**box, type the SPID.</span></span>  
  
    -   <span data-ttu-id="9207c-134">若要重播特定时间段内发生的事件，请选择 **“按日期和时间限制重播”** 。</span><span class="sxs-lookup"><span data-stu-id="9207c-134">To replay events that occurred during a specific time period, select **Limit replay by date and time**.</span></span> <span data-ttu-id="9207c-135">为“开始时间”  和“结束时间”  选择日期和时间，以指定要在重播中包括的时间段。</span><span class="sxs-lookup"><span data-stu-id="9207c-135">Select a date and time for the **Start time**and **End time**to specify the time period to include in the replay.</span></span>  
  
    -   <span data-ttu-id="9207c-136">若要控制 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在重播期间管理进程的方式，请配置 **“Health Monitor 选项”** 。</span><span class="sxs-lookup"><span data-stu-id="9207c-136">To control how [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] manages processes during replay, configure **Health Monitor Options**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9207c-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9207c-137">See Also</span></span>  
 <span data-ttu-id="9207c-138">[运行 SQL Server Profiler 所需的权限](sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="9207c-138">[Permissions Required to Run SQL Server Profiler](sql-server-profiler.md) </span></span>  
 <span data-ttu-id="9207c-139">[重播跟踪](replay-traces.md) </span><span class="sxs-lookup"><span data-stu-id="9207c-139">[Replay Traces](replay-traces.md) </span></span>  
 <span data-ttu-id="9207c-140">[打开跟踪表 (SQL Server Profiler)](open-a-trace-table-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="9207c-140">[Open a Trace Table &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="9207c-141">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="9207c-141">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
