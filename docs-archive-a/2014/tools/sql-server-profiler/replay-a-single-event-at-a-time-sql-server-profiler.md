---
title: 每次重播一个事件 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- events [SQL Server], replaying single event at a time
- traces [SQL Server], replaying
- replaying traces
ms.assetid: 220fb192-9636-41a2-b15c-62af6cab8fff
author: stevestein
ms.author: sstein
ms.openlocfilehash: 457bc94d9d8eae470fb60b450d30441c07e676df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692033"
---
# <a name="replay-a-single-event-at-a-time-sql-server-profiler"></a><span data-ttu-id="bc9e8-102">每次重播一个事件 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="bc9e8-102">Replay a Single Event at a Time (SQL Server Profiler)</span></span>
  <span data-ttu-id="bc9e8-103">本主题介绍如何使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]每次重播跟踪文件或表中的一个事件。</span><span class="sxs-lookup"><span data-stu-id="bc9e8-103">This topic describes how to replay one event at a time in a replay trace file or table by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-replay-a-single-event-at-a-time"></a><span data-ttu-id="bc9e8-104">每次重播一个事件</span><span class="sxs-lookup"><span data-stu-id="bc9e8-104">To replay a single event at a time</span></span>  
  
1.  <span data-ttu-id="bc9e8-105">打开要重播的跟踪文件或跟踪表。</span><span class="sxs-lookup"><span data-stu-id="bc9e8-105">Open the trace file or trace table you want to replay.</span></span> <span data-ttu-id="bc9e8-106">有关详细信息，请参阅 [打开跟踪文件 (SQL Server Profiler)](open-a-trace-file-sql-server-profiler.md) 或 [打开跟踪表 (SQL Server Profiler)](open-a-trace-table-sql-server-profiler.md)一起提供的预定义优化模板。</span><span class="sxs-lookup"><span data-stu-id="bc9e8-106">For more information, see [Open a Trace File &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) or [Open a Trace Table &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md).</span></span>  
  
     <span data-ttu-id="bc9e8-107">请确保打开的跟踪文件或跟踪表包含重播所需的事件类。</span><span class="sxs-lookup"><span data-stu-id="bc9e8-107">Make sure that the trace file or table you open contains the event classes necessary for replay.</span></span> <span data-ttu-id="bc9e8-108">有关详细信息，请参阅 [Replay Requirements](replay-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bc9e8-108">For more information, see [Replay Requirements](replay-requirements.md).</span></span>  
  
2.  <span data-ttu-id="bc9e8-109">在 **“重播”** 菜单上，单击 **“步骤”** ，然后连接到要在其上重播跟踪的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="bc9e8-109">On the **Replay** menu, click **Step**, and connect to the server instance where you want to replay the trace.</span></span>  
  
3.  <span data-ttu-id="bc9e8-110">在 **“重播配置”** 对话框中，验证设置，再单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="bc9e8-110">In the **Replay Configuration** dialog box, verify the settings, and then click **OK**.</span></span> <span data-ttu-id="bc9e8-111">有关指定“重播配置”  对话框中的设置的详细信息，请参阅 [重播跟踪文件 (SQL Server Profiler)](replay-a-trace-file-sql-server-profiler.md) 或 [重播跟踪表 (SQL Server Profiler)](replay-a-trace-table-sql-server-profiler.md)。</span><span class="sxs-lookup"><span data-stu-id="bc9e8-111">For more information about specifying settings on the **Replay Configuration** dialog box, see [Replay a Trace File &#40;SQL Server Profiler&#41;](replay-a-trace-file-sql-server-profiler.md) or [Replay a Trace Table &#40;SQL Server Profiler&#41;](replay-a-trace-table-sql-server-profiler.md).</span></span>  
  
4.  <span data-ttu-id="bc9e8-112">若要重播第一个事件，请单击 **“重播配置”** 对话框中的 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="bc9e8-112">To replay the first event, click **OK** in the **Replay Configuration** dialog box.</span></span>  
  
5.  <span data-ttu-id="bc9e8-113">若要重播后续事件，请在 **“重播”** 菜单上，单击 **“步骤”** ，或按 F10。</span><span class="sxs-lookup"><span data-stu-id="bc9e8-113">To replay subsequent events, on the **Replay** menu, click **Step**, or press F10.</span></span> <span data-ttu-id="bc9e8-114">对每个事件重复单击 **“步骤”** 或按 F10。</span><span class="sxs-lookup"><span data-stu-id="bc9e8-114">Repeat clicking **Step** or pressing F10 for each event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc9e8-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bc9e8-115">See Also</span></span>  
 <span data-ttu-id="bc9e8-116">[重播跟踪](replay-traces.md) </span><span class="sxs-lookup"><span data-stu-id="bc9e8-116">[Replay Traces](replay-traces.md) </span></span>  
 [<span data-ttu-id="bc9e8-117">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="bc9e8-117">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
