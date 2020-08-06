---
title: 重播到 (SQL Server Profiler) 的断点 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- breakpoints [SQL Server]
- traces [SQL Server], replaying
ms.assetid: 3caf751e-df3b-40c7-b5e8-4490ae178e0c
author: stevestein
ms.author: sstein
ms.openlocfilehash: f33b6862847b042a2613d8c2aa035dd5805493ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692024"
---
# <a name="replay-to-a-breakpoint-sql-server-profiler"></a><span data-ttu-id="053f1-102">重播到断点 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="053f1-102">Replay to a Breakpoint (SQL Server Profiler)</span></span>
  <span data-ttu-id="053f1-103">本主题说明如何在您要通过使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]进行重播的跟踪文件或表中设置断点。</span><span class="sxs-lookup"><span data-stu-id="053f1-103">This topic describes how to set breakpoints in a trace file or table that you want to replay by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="053f1-104">在重播跟踪之前，在跟踪文件或表中设置断点可以使您在发生特定事件时暂停重播跟踪。</span><span class="sxs-lookup"><span data-stu-id="053f1-104">Setting breakpoints in a trace file or table before you start to replay the trace, enables you to pause replay of the trace at specific events.</span></span> <span data-ttu-id="053f1-105">在重播跟踪时使用断点能够支持调试，因为您可以将长跟踪脚本的重播分解为较短的段以便进行增量分析。</span><span class="sxs-lookup"><span data-stu-id="053f1-105">Using breakpoints while replaying a trace supports debugging because you can break the replay of long trace scripts into short segments that can be analyzed incrementally.</span></span>  
  
### <a name="to-replay-to-a-breakpoint"></a><span data-ttu-id="053f1-106">重播到断点</span><span class="sxs-lookup"><span data-stu-id="053f1-106">To replay to a breakpoint</span></span>  
  
1.  <span data-ttu-id="053f1-107">打开要重播的跟踪文件或跟踪表。</span><span class="sxs-lookup"><span data-stu-id="053f1-107">Open the trace file or trace table you want to replay.</span></span> <span data-ttu-id="053f1-108">有关详细信息，请参阅 [打开跟踪文件 (SQL Server Profiler)](open-a-trace-file-sql-server-profiler.md) 或 [打开跟踪表 (SQL Server Profiler)](open-a-trace-table-sql-server-profiler.md)一起提供的预定义优化模板。</span><span class="sxs-lookup"><span data-stu-id="053f1-108">For more information, see [Open a Trace File &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) or [Open a Trace Table &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md).</span></span>  
  
     <span data-ttu-id="053f1-109">请确保打开的跟踪文件或跟踪表包含重播所需的事件类。</span><span class="sxs-lookup"><span data-stu-id="053f1-109">Make sure that the trace file or table you open contains the event classes necessary for replay.</span></span> <span data-ttu-id="053f1-110">有关详细信息，请参阅 [Replay Requirements](replay-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="053f1-110">For more information, see [Replay Requirements](replay-requirements.md).</span></span>  
  
2.  <span data-ttu-id="053f1-111">在跟踪窗口中，单击要用作断点的事件。</span><span class="sxs-lookup"><span data-stu-id="053f1-111">In the trace window, click an event that you want to use as a breakpoint.</span></span> <span data-ttu-id="053f1-112">可以使用以下三种方法来设置断点：</span><span class="sxs-lookup"><span data-stu-id="053f1-112">Use one of the following three methods to set a breakpoint:</span></span>  
  
    -   <span data-ttu-id="053f1-113">按 F9。</span><span class="sxs-lookup"><span data-stu-id="053f1-113">Press F9.</span></span>  
  
    -   <span data-ttu-id="053f1-114">在 **“重播”** 菜单上，单击 **“切换断点”** 。</span><span class="sxs-lookup"><span data-stu-id="053f1-114">On the **Replay** menu, click **Toggle Breakpoint**.</span></span>  
  
    -   <span data-ttu-id="053f1-115">右键单击“事件”，再单击“切换断点”  。</span><span class="sxs-lookup"><span data-stu-id="053f1-115">Right-click the event, and then click **Toggle Breakpoint**.</span></span>  
  
     <span data-ttu-id="053f1-116">选定跟踪事件的旁边将显示一个红色项目符号，表示其为跟踪断点。</span><span class="sxs-lookup"><span data-stu-id="053f1-116">A red bullet appears next to the selected trace event, indicating that it is the trace breakpoint.</span></span>  
  
     <span data-ttu-id="053f1-117">重复此步骤可以设置多个断点。</span><span class="sxs-lookup"><span data-stu-id="053f1-117">Repeat this step to set several breakpoints.</span></span>  
  
3.  <span data-ttu-id="053f1-118">在 **“重播”** 菜单上，单击 **“启动”** ，然后连接到要重播跟踪的服务器。</span><span class="sxs-lookup"><span data-stu-id="053f1-118">On the **Replay** menu, click **Start**, and connect to the server where you want to replay the trace.</span></span>  
  
4.  <span data-ttu-id="053f1-119">在 **“重播配置”** 对话框中，验证设置，再单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="053f1-119">In the **Replay Configuration** dialog box, verify the settings, and then click **OK**.</span></span>  
  
     <span data-ttu-id="053f1-120">将启动重播，并在到达断点时暂停。</span><span class="sxs-lookup"><span data-stu-id="053f1-120">The replay starts, pausing when the breakpoint is reached.</span></span>  
  
5.  <span data-ttu-id="053f1-121">按 F5 可恢复重播并继续运行直到下一个断点。</span><span class="sxs-lookup"><span data-stu-id="053f1-121">Press F5 to resume the replay and proceed to the next breakpoint.</span></span>  
  
6.  <span data-ttu-id="053f1-122">重复步骤 5 到跟踪的末尾。</span><span class="sxs-lookup"><span data-stu-id="053f1-122">Repeat Step 5 through the end of the trace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="053f1-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="053f1-123">See Also</span></span>  
 <span data-ttu-id="053f1-124">[重播至光标处 (SQL Server Profiler)](replay-to-a-cursor-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="053f1-124">[Replay to a Cursor &#40;SQL Server Profiler&#41;](replay-to-a-cursor-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="053f1-125">[重播跟踪](replay-traces.md) </span><span class="sxs-lookup"><span data-stu-id="053f1-125">[Replay Traces](replay-traces.md) </span></span>  
 [<span data-ttu-id="053f1-126">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="053f1-126">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
