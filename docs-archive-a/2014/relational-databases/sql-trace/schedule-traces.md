---
title: 计划跟踪 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server], events
- traces [SQL Server]
- traces [SQL Server], stopping
- events [SQL Server], filters
- scheduling traces [SQL Server]
- traces [SQL Server], scheduling
- stopping traces
ms.assetid: 620b79db-924b-4502-8af3-39efcfca245d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a698d88db35c84f7611293cf45807203c883865a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588458"
---
# <a name="schedule-traces"></a><span data-ttu-id="7811a-102">安排跟踪</span><span class="sxs-lookup"><span data-stu-id="7811a-102">Schedule Traces</span></span>
  <span data-ttu-id="7811a-103">在 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中有两种计划跟踪的方法。</span><span class="sxs-lookup"><span data-stu-id="7811a-103">There are two ways to schedule tracing in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="7811a-104">可以：</span><span class="sxs-lookup"><span data-stu-id="7811a-104">You can:</span></span>  
  
-   <span data-ttu-id="7811a-105">启用跟踪停止时间。</span><span class="sxs-lookup"><span data-stu-id="7811a-105">Enable a trace stop time.</span></span>  
  
-   <span data-ttu-id="7811a-106">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理来计划跟踪。</span><span class="sxs-lookup"><span data-stu-id="7811a-106">Use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to schedule a trace.</span></span>  
  
## <a name="specifying-a-stop-time"></a><span data-ttu-id="7811a-107">指定停止时间</span><span class="sxs-lookup"><span data-stu-id="7811a-107">Specifying a Stop Time</span></span>  
 <span data-ttu-id="7811a-108">如果您使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 存储过程或 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]，则可以指定跟踪停止时间。</span><span class="sxs-lookup"><span data-stu-id="7811a-108">You can specify a trace stop time if you use [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedures or if you use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="7811a-109">停止时间必须在最初配置跟踪时设置。</span><span class="sxs-lookup"><span data-stu-id="7811a-109">The stop time must be set when the trace is originally configured.</span></span>  
  
## <a name="scheduling-traces-by-using-sql-server-agent"></a><span data-ttu-id="7811a-110">使用 SQL Server 代理来计划跟踪</span><span class="sxs-lookup"><span data-stu-id="7811a-110">Scheduling Traces by Using SQL Server Agent</span></span>  
 <span data-ttu-id="7811a-111">计划跟踪的最佳方法是先使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理启动跟踪，再使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 存储过程 **sp_trace_setstatus**或 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]来指定跟踪停止时间。</span><span class="sxs-lookup"><span data-stu-id="7811a-111">The best way to schedule traces is to use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to start the trace and then specify a trace stop time by using the [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure **sp_trace_setstatus**, or [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
 <span data-ttu-id="7811a-112">**设置跟踪的结束时间筛选器**</span><span class="sxs-lookup"><span data-stu-id="7811a-112">**To set an end time filter for a trace**</span></span>  
  
 [<span data-ttu-id="7811a-113">基于事件结束时间筛选事件 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="7811a-113">Filter Events Based on the Event End Time &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/filter-events-based-on-the-event-end-time-sql-server-profiler.md)  
  
 [<span data-ttu-id="7811a-114">sp_trace_setstatus (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="7811a-114">sp_trace_setstatus &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="7811a-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7811a-115">See Also</span></span>  
 [<span data-ttu-id="7811a-116">自动执行管理任务（SQL Server 代理）</span><span class="sxs-lookup"><span data-stu-id="7811a-116">Automated Administration Tasks &#40;SQL Server Agent&#41;</span></span>](../../ssms/agent/sql-server-agent.md)  
  
  
