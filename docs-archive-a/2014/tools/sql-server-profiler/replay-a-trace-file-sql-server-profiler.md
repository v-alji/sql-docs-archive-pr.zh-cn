---
title: 重播跟踪文件 (SQL Server Profiler) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], replaying
- replaying traces
ms.assetid: 9e361275-c8fd-4499-8389-242cf8e27415
author: stevestein
ms.author: sstein
ms.openlocfilehash: d3a9f007b9b6d2b46be43abdb10db286a75c33fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692027"
---
# <a name="replay-a-trace-file-sql-server-profiler"></a><span data-ttu-id="607e2-102">重播跟踪文件 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="607e2-102">Replay a Trace File (SQL Server Profiler)</span></span>
  <span data-ttu-id="607e2-103">重播是指打开已保存的跟踪并对其重播的功能。</span><span class="sxs-lookup"><span data-stu-id="607e2-103">Replay is the ability to open a saved trace and replay it again.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="607e2-104">具有多线程播放引擎，能模拟用户连接和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证。</span><span class="sxs-lookup"><span data-stu-id="607e2-104">features a multithreaded playback engine that can simulate user connections and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="607e2-105">重播对于解决应用程序或进程问题是很有用的。</span><span class="sxs-lookup"><span data-stu-id="607e2-105">Replay is useful to troubleshoot an application or process problem.</span></span> <span data-ttu-id="607e2-106">在您确定问题并进行更正后，请对更正后的应用程序或进程运行发现该潜在问题的跟踪。</span><span class="sxs-lookup"><span data-stu-id="607e2-106">When you identify the problem and implement corrections, run the trace that found the potential problem against the corrected application or process.</span></span> <span data-ttu-id="607e2-107">然后，重播原始跟踪并比较结果。</span><span class="sxs-lookup"><span data-stu-id="607e2-107">Then, replay the original trace and compare results.</span></span>  
  
 <span data-ttu-id="607e2-108">除了要监视的任何其他事件类之外，还必须捕获特定的事件类才能启用重播。</span><span class="sxs-lookup"><span data-stu-id="607e2-108">In addition to any other event classes you want to monitor, specific event classes must be captured to enable replay.</span></span> <span data-ttu-id="607e2-109">如果使用 **TSQL_Replay** 跟踪模板，则在默认情况下将捕获这些事件。</span><span class="sxs-lookup"><span data-stu-id="607e2-109">These events are captured by default if you use the **TSQL_Replay** trace template.</span></span> <span data-ttu-id="607e2-110">有关详细信息，请参阅 [Replay Requirements](replay-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="607e2-110">For more information, see [Replay Requirements](replay-requirements.md).</span></span>  
  
### <a name="to-replay-a-trace-file"></a><span data-ttu-id="607e2-111">重播跟踪文件</span><span class="sxs-lookup"><span data-stu-id="607e2-111">To replay a trace file</span></span>  
  
1.  <span data-ttu-id="607e2-112">在 **“文件”** 菜单上，指向 **“打开”** ，然后单击 **“跟踪文件”** 。</span><span class="sxs-lookup"><span data-stu-id="607e2-112">On the **File** menu, point to **Open**, and then click **Trace File**.</span></span> <span data-ttu-id="607e2-113">选择包含需要重播的事件类的跟踪文件。</span><span class="sxs-lookup"><span data-stu-id="607e2-113">Select a trace file that contains the event classes necessary for replay.</span></span>  
  
2.  <span data-ttu-id="607e2-114">在 **“重播”** 菜单上，单击 **“开始”** ，然后连接到要重播跟踪的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="607e2-114">On the **Replay** menu, click **Start**, and connect to the server instance where you want to replay the trace.</span></span>  
  
3.  <span data-ttu-id="607e2-115">在 **“重播配置”** 对话框的 **“基本重播选项”** 选项卡上，指定 **“重播服务器”** 。</span><span class="sxs-lookup"><span data-stu-id="607e2-115">In the **Replay Configuration** dialog box, on the **Basic Replay Options** tab, specify the **Replay server**.</span></span> <span data-ttu-id="607e2-116">单击 **“更改”** 以更改 **“重播服务器”** 框中显示的服务器。</span><span class="sxs-lookup"><span data-stu-id="607e2-116">Click **Change** to change the server displayed in the **Replay server** box.</span></span>  
  
4.  <span data-ttu-id="607e2-117">根据需要，选择下列目标位置之一以在其中保存重播：</span><span class="sxs-lookup"><span data-stu-id="607e2-117">Optionally, select one of the following destinations in which to save the replay:</span></span>  
  
    -   <span data-ttu-id="607e2-118">**保存到文件**，指定用于保存重播的文件。</span><span class="sxs-lookup"><span data-stu-id="607e2-118">**Save to file**, which specifies a file in which to save the replay.</span></span>  
  
    -   <span data-ttu-id="607e2-119">**保存到表**，该选项指定保存重播的数据库表。</span><span class="sxs-lookup"><span data-stu-id="607e2-119">**Save to table**, which specifies a database table in which to save the replay.</span></span>  
  
5.  <span data-ttu-id="607e2-120">选择“按跟踪的顺序重播事件”  或“使用多个线程重播事件”  。</span><span class="sxs-lookup"><span data-stu-id="607e2-120">Choose either **Replay the events in the order they were traced**or **Replay events using multiple threads**.</span></span> <span data-ttu-id="607e2-121">下表列出了这些设置之间的差异。</span><span class="sxs-lookup"><span data-stu-id="607e2-121">The following table explains the difference between these settings.</span></span>  
  
    |<span data-ttu-id="607e2-122">选项</span><span class="sxs-lookup"><span data-stu-id="607e2-122">Option</span></span>|<span data-ttu-id="607e2-123">说明</span><span class="sxs-lookup"><span data-stu-id="607e2-123">Description</span></span>|  
    |------------|-----------------|  
    |<span data-ttu-id="607e2-124">**按跟踪事件的顺序重播事件**</span><span class="sxs-lookup"><span data-stu-id="607e2-124">**Replay events in the order they were traced**</span></span>|<span data-ttu-id="607e2-125">按记录事件的顺序重播事件。</span><span class="sxs-lookup"><span data-stu-id="607e2-125">Replays events in the order they were recorded.</span></span> <span data-ttu-id="607e2-126">此选项启用调试。</span><span class="sxs-lookup"><span data-stu-id="607e2-126">This option enables debugging.</span></span>|  
    |<span data-ttu-id="607e2-127">**使用多个线程重播事件**</span><span class="sxs-lookup"><span data-stu-id="607e2-127">**Replay events using multiple threads**</span></span>|<span data-ttu-id="607e2-128">此选项使用多个线程重播各个事件，而不考虑其顺序。</span><span class="sxs-lookup"><span data-stu-id="607e2-128">This option uses multiple threads to replay each event regardless of the sequence.</span></span> <span data-ttu-id="607e2-129">此选项用于优化性能。</span><span class="sxs-lookup"><span data-stu-id="607e2-129">This option optimizes performance.</span></span>|  
  
6.  <span data-ttu-id="607e2-130">选择 **“显示重播结果”** 以在重播时查看结果。</span><span class="sxs-lookup"><span data-stu-id="607e2-130">Select **Display replay results** to view the replay as it occurs.</span></span>  
  
7.  <span data-ttu-id="607e2-131">还可以单击“高级重播选项”  选项卡以配置以下选项：</span><span class="sxs-lookup"><span data-stu-id="607e2-131">Optionally click the **Advanced Replay Options**tab to configure the following options:</span></span>  
  
    -   <span data-ttu-id="607e2-132">若要重播所有服务器进程 ID (SPID)，请选择“重播系统 SPID”  。</span><span class="sxs-lookup"><span data-stu-id="607e2-132">To replay all server process IDs (SPIDs), select **Replay system SPIDs**.</span></span>  
  
    -   <span data-ttu-id="607e2-133">若要仅重播属于特定 SPID 的进程，请选择 **“仅重播一个 SPID”** 。</span><span class="sxs-lookup"><span data-stu-id="607e2-133">To limit the replay to processes belonging to a specific SPID, select **Replay one SPID only**.</span></span> <span data-ttu-id="607e2-134">在 **“要重播的 SPID”** 框中，键入 SPID。</span><span class="sxs-lookup"><span data-stu-id="607e2-134">In the **SPID to replay** box, type the SPID.</span></span>  
  
    -   <span data-ttu-id="607e2-135">若要重播特定时间段内发生的事件，请选择 **“按日期和时间限制重播”** 。</span><span class="sxs-lookup"><span data-stu-id="607e2-135">To replay events that occurred during a specific time period, select **Limit the replay by date and time**.</span></span> <span data-ttu-id="607e2-136">为“开始时间”  和“结束时间”  选择日期和时间，以指定要在重播中包括的时间段。</span><span class="sxs-lookup"><span data-stu-id="607e2-136">Select a date and time for the **Start time**and **End time**to specify the time period to include in the replay.</span></span>  
  
    -   <span data-ttu-id="607e2-137">若要控制重播期间 SQL Server 管理进程的方法，请配置 **“Health Monitor 选项”** 。</span><span class="sxs-lookup"><span data-stu-id="607e2-137">To control how SQL Server manages processes during replay, configure **Health Monitor Options**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="607e2-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="607e2-138">See Also</span></span>  
 <span data-ttu-id="607e2-139">[运行 SQL Server Profiler 所需的权限](sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="607e2-139">[Permissions Required to Run SQL Server Profiler](sql-server-profiler.md) </span></span>  
 <span data-ttu-id="607e2-140">[重播跟踪](replay-traces.md) </span><span class="sxs-lookup"><span data-stu-id="607e2-140">[Replay Traces](replay-traces.md) </span></span>  
 <span data-ttu-id="607e2-141">[打开跟踪文件 (SQL Server Profiler)](open-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="607e2-141">[Open a Trace File &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="607e2-142">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="607e2-142">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
