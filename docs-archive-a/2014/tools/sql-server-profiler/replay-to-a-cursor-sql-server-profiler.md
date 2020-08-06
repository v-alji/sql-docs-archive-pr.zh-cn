---
title: 重播到光标 (SQL Server Profiler) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- replaying cursors
- traces [SQL Server], replaying
- replaying traces
ms.assetid: 89eadc41-4424-4a1c-ba61-0b52c851cdb1
author: stevestein
ms.author: sstein
ms.openlocfilehash: bfc5ba06b60100bf8ecc8d04909371021a5b00e5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692023"
---
# <a name="replay-to-a-cursor-sql-server-profiler"></a><span data-ttu-id="efd57-102">重播至光标处 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="efd57-102">Replay to a Cursor (SQL Server Profiler)</span></span>
  <span data-ttu-id="efd57-103">本主题介绍了如何使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]重播到光标处即暂停的跟踪文件或表。</span><span class="sxs-lookup"><span data-stu-id="efd57-103">This topic describes how to replay trace files or tables that pause when a cursor is reached by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="efd57-104">在光标处暂停跟踪可支持调试，因为您可以将长跟踪脚本的重播分成较短的段，以便逐步进行分析。</span><span class="sxs-lookup"><span data-stu-id="efd57-104">Pausing traces at cursors supports debugging because you can break the replay of long trace scripts into short segments that can be analyzed incrementally.</span></span>  
  
### <a name="to-replay-to-the-cursor"></a><span data-ttu-id="efd57-105">重播至光标处</span><span class="sxs-lookup"><span data-stu-id="efd57-105">To replay to the cursor</span></span>  
  
1.  <span data-ttu-id="efd57-106">打开要重播的跟踪文件或跟踪表。</span><span class="sxs-lookup"><span data-stu-id="efd57-106">Open the trace file or trace table you want to replay.</span></span> <span data-ttu-id="efd57-107">有关详细信息，请参阅 [打开跟踪文件 (SQL Server Profiler)](open-a-trace-file-sql-server-profiler.md) 或 [打开跟踪表 (SQL Server Profiler)](open-a-trace-table-sql-server-profiler.md)一起提供的预定义优化模板。</span><span class="sxs-lookup"><span data-stu-id="efd57-107">For more information, see [Open a Trace File &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) or [Open a Trace Table &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md).</span></span>  
  
     <span data-ttu-id="efd57-108">请确保打开的跟踪文件或跟踪表包含重播所需的事件类。</span><span class="sxs-lookup"><span data-stu-id="efd57-108">Make sure that the trace file or table you open contains the event classes necessary for replay.</span></span> <span data-ttu-id="efd57-109">有关详细信息，请参阅 [Replay Requirements](replay-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="efd57-109">For more information, see [Replay Requirements](replay-requirements.md).</span></span>  
  
2.  <span data-ttu-id="efd57-110">在跟踪窗口中，单击一个事件。</span><span class="sxs-lookup"><span data-stu-id="efd57-110">In the trace window, click an event.</span></span>  
  
3.  <span data-ttu-id="efd57-111">在 **“重播”** 菜单上，单击 **“运行至光标处”** ，然后连接到要重播跟踪的服务器。</span><span class="sxs-lookup"><span data-stu-id="efd57-111">On the **Replay** menu, click **Run to Cursor**, and then connect to the server where you want to replay the trace.</span></span>  
  
4.  <span data-ttu-id="efd57-112">在 **“重播配置”** 对话框中，验证设置，再单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="efd57-112">In the **Replay Configuration** dialog box, verify the settings, and then click **OK**.</span></span>  
  
     <span data-ttu-id="efd57-113">重播将开始，并在第一次到达光标处时暂停。</span><span class="sxs-lookup"><span data-stu-id="efd57-113">The replay starts, pausing when the first cursor is reached.</span></span>  
  
5.  <span data-ttu-id="efd57-114">按 F5 恢复跟踪。</span><span class="sxs-lookup"><span data-stu-id="efd57-114">Press F5 to resume the trace.</span></span>  
  
6.  <span data-ttu-id="efd57-115">重复步骤 5 到跟踪的末尾。</span><span class="sxs-lookup"><span data-stu-id="efd57-115">Repeat Step 5 through the end of the trace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efd57-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="efd57-116">See Also</span></span>  
 <span data-ttu-id="efd57-117">[重播到断点 (SQL Server Profiler)](replay-to-a-breakpoint-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="efd57-117">[Replay to a Breakpoint &#40;SQL Server Profiler&#41;](replay-to-a-breakpoint-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="efd57-118">[重播跟踪](replay-traces.md) </span><span class="sxs-lookup"><span data-stu-id="efd57-118">[Replay Traces](replay-traces.md) </span></span>  
 [<span data-ttu-id="efd57-119">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="efd57-119">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
