---
title: 启动跟踪 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Profiler, stopping traces
- pausing traces
- Profiler [SQL Server Profiler], stopping traces
- Profiler [SQL Server Profiler], starting traces
- traces [SQL Server], starting
- SQL Server Profiler, pausing traces
- traces [SQL Server], stopping
- Profiler [SQL Server Profiler], pausing traces
- traces [SQL Server], pausing
- SQL Server Profiler, starting traces
- stopping traces
- starting traces
ms.assetid: aeeb38eb-229a-4c8b-ad66-57e9ce45fb6a
author: stevestein
ms.author: sstein
ms.openlocfilehash: f2b75519631269a1213077a4e295ac73fca1b950
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690949"
---
# <a name="start-a-trace"></a><span data-ttu-id="e85d1-102">启动跟踪</span><span class="sxs-lookup"><span data-stu-id="e85d1-102">Start a Trace</span></span>
  <span data-ttu-id="e85d1-103">使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]定义新跟踪或创建模板之后，可以使用新的跟踪定义或模板来启动、暂停或停止捕获数据。</span><span class="sxs-lookup"><span data-stu-id="e85d1-103">After you have defined a new trace or created a template by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], you can start, pause, or stop capturing data by using the new trace definition or template.</span></span>  
  
## <a name="starting-a-trace"></a><span data-ttu-id="e85d1-104">启动跟踪</span><span class="sxs-lookup"><span data-stu-id="e85d1-104">Starting a Trace</span></span>  
 <span data-ttu-id="e85d1-105">当启动跟踪并且已定义的源为 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 或 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]的实例时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将创建一个队列，为捕获的服务器事件提供临时存放位置。</span><span class="sxs-lookup"><span data-stu-id="e85d1-105">When you start a trace and the defined source is an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] or [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] creates a queue that provides a temporary holding place for captured server events.</span></span>  
  
 <span data-ttu-id="e85d1-106">使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 访问 SQL 跟踪时，启动跟踪将打开一个新的跟踪窗口（如果没有窗口打开），并立即捕获数据。</span><span class="sxs-lookup"><span data-stu-id="e85d1-106">When you use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to access SQL Trace, a new trace window opens (if one is not already open) when a trace is started, and data is immediately captured.</span></span>  
  
 <span data-ttu-id="e85d1-107">使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 系统存储过程访问 SQL 跟踪时，每次启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例都必须启动跟踪，以便捕获数据。</span><span class="sxs-lookup"><span data-stu-id="e85d1-107">When you use [!INCLUDE[tsql](../../includes/tsql-md.md)] system stored procedures to access SQL Trace, you must start a trace every time an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] starts for data to be captured.</span></span> <span data-ttu-id="e85d1-108">启动跟踪后，只能修改跟踪的名称。</span><span class="sxs-lookup"><span data-stu-id="e85d1-108">When a trace has been started, you can modify only the name of the trace.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e85d1-109">在使用现有跟踪时，可以查看属性，但是不能修改属性。</span><span class="sxs-lookup"><span data-stu-id="e85d1-109">When working with existing traces, you can view the properties, but you cannot modify the properties.</span></span> <span data-ttu-id="e85d1-110">若要修改属性，请停止或暂停跟踪。</span><span class="sxs-lookup"><span data-stu-id="e85d1-110">To modify the properties, stop or pause the trace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e85d1-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e85d1-111">See Also</span></span>  
 <span data-ttu-id="e85d1-112">[连接到服务器后自动启动跟踪 &#40;SQL Server Profiler&#41;](start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="e85d1-112">[Start a Trace Automatically after Connecting to a Server &#40;SQL Server Profiler&#41;](start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="e85d1-113">[暂停跟踪 &#40;SQL Server Profiler&#41;](pause-a-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="e85d1-113">[Pause a Trace &#40;SQL Server Profiler&#41;](pause-a-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="e85d1-114">[停止跟踪 &#40;SQL Server Profiler&#41;](stop-a-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="e85d1-114">[Stop a Trace &#40;SQL Server Profiler&#41;](stop-a-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="e85d1-115">[清除跟踪窗口 &#40;SQL Server Profiler&#41;](clear-a-trace-window-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="e85d1-115">[Clear a Trace Window &#40;SQL Server Profiler&#41;](clear-a-trace-window-sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="e85d1-116">在跟踪暂停或停止之后运行跟踪 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="e85d1-116">Run a Trace After It Has Been Paused or Stopped &#40;SQL Server Profiler&#41;</span></span>](run-a-trace-after-it-has-been-paused-or-stopped-sql-server-profiler.md)  
  
  
