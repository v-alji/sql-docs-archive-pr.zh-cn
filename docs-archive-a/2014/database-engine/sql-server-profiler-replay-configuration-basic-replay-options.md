---
title: SQL Server Profiler 重播配置 (基本重播选项) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.replay.generaloptions.f1
helpviewer_keywords:
- Replay Configuration dialog box
ms.assetid: 85a1dec6-9bbc-477a-86c5-b463db9ebb31
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: cbf433c3108294909d91f7860136c0755b39b46f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691841"
---
# <a name="sql-server-profiler---replay-configuration-basic-replay-options"></a><span data-ttu-id="6c9af-102">SQL Server Profiler - 重播配置（基本重播选项）</span><span class="sxs-lookup"><span data-stu-id="6c9af-102">SQL Server Profiler - Replay Configuration (Basic Replay Options)</span></span>
  <span data-ttu-id="6c9af-103">在 **“重播配置”** 对话框中，使用 **“基本重播配置”** 页可以指定如何重播跟踪文件或表。</span><span class="sxs-lookup"><span data-stu-id="6c9af-103">In the **Replay Configuration** dialog box, use the **Basic Replay Options** page to specify how to replay a trace file or table.</span></span>  
  
 <span data-ttu-id="6c9af-104">若要查看此窗口，请使用 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 打开包含相应重播事件的跟踪文件或表。</span><span class="sxs-lookup"><span data-stu-id="6c9af-104">To view this window, use [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] to open a trace file or table that contains the appropriate events for replay.</span></span> <span data-ttu-id="6c9af-105">有关详细信息，请参阅 [Replay Requirements](../tools/sql-server-profiler/replay-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6c9af-105">For more information, see [Replay Requirements](../tools/sql-server-profiler/replay-requirements.md).</span></span> <span data-ttu-id="6c9af-106">打开跟踪文件或表后，在 **“重播”** 菜单上，单击 **“启动”**，然后连接到要重播跟踪的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="6c9af-106">While the trace file or table is open, on the **Replay** menu, click **Start**, and then connect to the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] where you want to replay the trace.</span></span>  
  
## <a name="options"></a><span data-ttu-id="6c9af-107">选项</span><span class="sxs-lookup"><span data-stu-id="6c9af-107">Options</span></span>  
 <span data-ttu-id="6c9af-108">**重播服务器**</span><span class="sxs-lookup"><span data-stu-id="6c9af-108">**Replay server**</span></span>  
 <span data-ttu-id="6c9af-109">显示要连接用来重播的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="6c9af-109">Displays the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to connect to for the replay.</span></span>  
  
 <span data-ttu-id="6c9af-110">**更改 .。。**</span><span class="sxs-lookup"><span data-stu-id="6c9af-110">**Change...**</span></span>  
 <span data-ttu-id="6c9af-111">启动“连接到服务器”\*\*\*\* 对话框以连接到另一台服务器。</span><span class="sxs-lookup"><span data-stu-id="6c9af-111">Launches the **Connect to Server** dialog box to connect to another server.</span></span>  
  
 <span data-ttu-id="6c9af-112">**保存到文件**</span><span class="sxs-lookup"><span data-stu-id="6c9af-112">**Save to file**</span></span>  
 <span data-ttu-id="6c9af-113">将重播结果保存到文件。</span><span class="sxs-lookup"><span data-stu-id="6c9af-113">Save the replay results to a file.</span></span> [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] <span data-ttu-id="6c9af-114">将显示标准文件对话框，您可以在该对话框中指定文件的保存位置。</span><span class="sxs-lookup"><span data-stu-id="6c9af-114">displays the standard file dialog, where you can specify the location to save the file.</span></span>  
  
 <span data-ttu-id="6c9af-115">**保存到表**</span><span class="sxs-lookup"><span data-stu-id="6c9af-115">**Save to table**</span></span>  
 <span data-ttu-id="6c9af-116">将重播结果保存到表。</span><span class="sxs-lookup"><span data-stu-id="6c9af-116">Save the replay results to a table.</span></span> [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] <span data-ttu-id="6c9af-117">将显示表选择对话框，您可以在该对话框中指定表的保存位置。</span><span class="sxs-lookup"><span data-stu-id="6c9af-117">displays the table selection dialog, where you can specify the location to save the table.</span></span>  
  
 <span data-ttu-id="6c9af-118">**重播线程数**</span><span class="sxs-lookup"><span data-stu-id="6c9af-118">**Number of replay threads**</span></span>  
 <span data-ttu-id="6c9af-119">指定要并发使用的重播线程数。</span><span class="sxs-lookup"><span data-stu-id="6c9af-119">Specify the number of replay threads to use concurrently.</span></span> <span data-ttu-id="6c9af-120">数目越大，重播期间消耗的资源越多，但是重播速度更快，允许的并发事件更多。</span><span class="sxs-lookup"><span data-stu-id="6c9af-120">A higher number consumes more resources during replay, but replay is faster and more concurrent.</span></span>  
  
 <span data-ttu-id="6c9af-121">**按跟踪事件的顺序重播事件**</span><span class="sxs-lookup"><span data-stu-id="6c9af-121">**Replay events in the order they were traced**</span></span>  
 <span data-ttu-id="6c9af-122">按顺序重播事件。</span><span class="sxs-lookup"><span data-stu-id="6c9af-122">Replay events sequentially.</span></span> <span data-ttu-id="6c9af-123">如果重播跟踪进行调试，请使用此选项。</span><span class="sxs-lookup"><span data-stu-id="6c9af-123">Use this option if you are replaying a trace for debugging.</span></span>  
  
 <span data-ttu-id="6c9af-124">**使用多个线程重播事件**</span><span class="sxs-lookup"><span data-stu-id="6c9af-124">**Replay events using multiple threads**</span></span>  
 <span data-ttu-id="6c9af-125">并发重播事件。</span><span class="sxs-lookup"><span data-stu-id="6c9af-125">Replay events concurrently.</span></span> <span data-ttu-id="6c9af-126">此选项比按顺序重播事件速度快，但将禁用调试。</span><span class="sxs-lookup"><span data-stu-id="6c9af-126">This option is faster than replaying events sequentially, but disables debugging.</span></span> <span data-ttu-id="6c9af-127">事件按其系统进程标识符 (SPID) 进行排序。</span><span class="sxs-lookup"><span data-stu-id="6c9af-127">The events are ordered within their system process identifiers (SPID).</span></span>  
  
 <span data-ttu-id="6c9af-128">**显示重播结果**</span><span class="sxs-lookup"><span data-stu-id="6c9af-128">**Display replay results**</span></span>  
 <span data-ttu-id="6c9af-129">在 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]中显示重播结果。</span><span class="sxs-lookup"><span data-stu-id="6c9af-129">Display replay results in [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c9af-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6c9af-130">See Also</span></span>  
 <span data-ttu-id="6c9af-131">[重播跟踪表 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="6c9af-131">[Replay a Trace Table &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="6c9af-132">[重播跟踪文件 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="6c9af-132">[Replay a Trace File &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="6c9af-133">重播跟踪</span><span class="sxs-lookup"><span data-stu-id="6c9af-133">Replay Traces</span></span>](../tools/sql-server-profiler/replay-traces.md)  
  
  
