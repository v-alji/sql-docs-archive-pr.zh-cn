---
title: 暂停跟踪 (SQL Server Profiler) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- pausing traces
- temporarily stopping traces
- traces [SQL Server], pausing
- stopping traces
ms.assetid: 432b9b0c-b5e7-47f3-a71b-310fb3bf2445
author: stevestein
ms.author: sstein
ms.openlocfilehash: cdc9dbbd01099b1d33787a72b0bd59b65cea722e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682494"
---
# <a name="pause-a-trace-sql-server-profiler"></a><span data-ttu-id="e8d3e-102">暂停跟踪 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="e8d3e-102">Pause a Trace (SQL Server Profiler)</span></span>
  <span data-ttu-id="e8d3e-103">暂停跟踪可防止捕获更多的事件数据，直到重新启动该跟踪。</span><span class="sxs-lookup"><span data-stu-id="e8d3e-103">Pausing a trace prevents further event data from being captured until the trace is restarted.</span></span>  
  
 <span data-ttu-id="e8d3e-104">暂停跟踪可以防止捕获事件数据，直到重新启动跟踪。</span><span class="sxs-lookup"><span data-stu-id="e8d3e-104">When you pause a trace, you prevent event data from being captured until the trace is restarted.</span></span> <span data-ttu-id="e8d3e-105">重新启动跟踪将恢复跟踪操作。</span><span class="sxs-lookup"><span data-stu-id="e8d3e-105">Restarting a trace lets trace operations resume.</span></span> <span data-ttu-id="e8d3e-106">重新启动后以前捕获的数据不会丢失。</span><span class="sxs-lookup"><span data-stu-id="e8d3e-106">No previously captured data is lost after a restart.</span></span> <span data-ttu-id="e8d3e-107">重新启动跟踪时，将从启动的那一点恢复数据捕获。</span><span class="sxs-lookup"><span data-stu-id="e8d3e-107">When the trace is restarted, data capturing resumes from that point onward.</span></span> <span data-ttu-id="e8d3e-108">暂停跟踪时，可以更改名称、事件、列和筛选器。</span><span class="sxs-lookup"><span data-stu-id="e8d3e-108">While a trace is paused, you can change the name, events, columns, and filters.</span></span> <span data-ttu-id="e8d3e-109">但是不能更改要将跟踪数据发送到的目标和服务器连接。</span><span class="sxs-lookup"><span data-stu-id="e8d3e-109">However, you cannot change the destinations to which you are sending the trace data, nor change the server connection.</span></span>  
  
### <a name="to-pause-a-trace"></a><span data-ttu-id="e8d3e-110">暂停跟踪</span><span class="sxs-lookup"><span data-stu-id="e8d3e-110">To pause a trace</span></span>  
  
1.  <span data-ttu-id="e8d3e-111">选择一个包含正在运行的跟踪的窗口。</span><span class="sxs-lookup"><span data-stu-id="e8d3e-111">Select a window that contains a running trace.</span></span>  
  
2.  <span data-ttu-id="e8d3e-112">在 **“文件”** 菜单上，单击 **“暂停跟踪”** 。</span><span class="sxs-lookup"><span data-stu-id="e8d3e-112">On the **File** menu, click **Pause Trace**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8d3e-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e8d3e-113">See Also</span></span>  
 [<span data-ttu-id="e8d3e-114">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="e8d3e-114">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
