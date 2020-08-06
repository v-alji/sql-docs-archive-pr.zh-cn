---
title: 服务器性能和活动监视 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- activity monitoring [SQL Server]
- traces [SQL Server], how-to topics
- monitoring server performance [SQL Server], activity monitoring
- stored procedures [SQL Server], traces
- performance [SQL Server], servers
- servers [SQL Server], performance
- SQL Server Profiler, how-to topics
- SQL Server Management Studio [SQL Server], monitoring system
- Profiler [SQL Server Profiler], how-to topics
ms.assetid: f9abe48d-d6e9-4c38-a355-fc5eb5a95a25
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a0fa7902d68c587a7733f07ceb8daccd3a6a98fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591305"
---
# <a name="server-performance-and-activity-monitoring"></a><span data-ttu-id="606fb-102">服务器性能和活动监视</span><span class="sxs-lookup"><span data-stu-id="606fb-102">Server Performance and Activity Monitoring</span></span>
  <span data-ttu-id="606fb-103">监视数据库的目的是评估服务器的性能。</span><span class="sxs-lookup"><span data-stu-id="606fb-103">The goal of monitoring databases is to assess how a server is performing.</span></span> <span data-ttu-id="606fb-104">有效监视包括定期拍摄当前性能的快照来隔离导致问题的进程，以及连续收集数据来跟踪性能趋势。</span><span class="sxs-lookup"><span data-stu-id="606fb-104">Effective monitoring involves taking periodic snapshots of current performance to isolate processes that are causing problems, and gathering data continuously over time to track performance trends.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="606fb-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 操作系统提供可以查看数据库当前状态并跟踪性能状态变化的实用工具。</span><span class="sxs-lookup"><span data-stu-id="606fb-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows operating system provide utilities that let you view the current condition of the database and to track performance as conditions change.</span></span>  
  
 <span data-ttu-id="606fb-106">下一节包含的主题说明了如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 Windows 性能以及活动监视工具。</span><span class="sxs-lookup"><span data-stu-id="606fb-106">The following section contains topics that describe how to use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows performance and activity monitoring tools.</span></span> <span data-ttu-id="606fb-107">本节包含以下主题：</span><span class="sxs-lookup"><span data-stu-id="606fb-107">It contains the following topics:</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="606fb-108">本节内容</span><span class="sxs-lookup"><span data-stu-id="606fb-108">In This Section</span></span>  
 <span data-ttu-id="606fb-109">**使用 Windows 工具执行监视任务**</span><span class="sxs-lookup"><span data-stu-id="606fb-109">**To perform monitoring tasks with Windows tools**</span></span>  
  
-   [<span data-ttu-id="606fb-110">启动系统监视器 (Windows)</span><span class="sxs-lookup"><span data-stu-id="606fb-110">Start System Monitor &#40;Windows&#41;</span></span>](start-system-monitor-windows.md)  
  
-   [<span data-ttu-id="606fb-111">查看 Windows 应用程序日志 (Windows)</span><span class="sxs-lookup"><span data-stu-id="606fb-111">View the Windows Application Log &#40;Windows&#41;</span></span>](view-the-windows-application-log-windows-10.md)  
  
 <span data-ttu-id="606fb-112">**使用 Windows 工具创建 SQL Server 数据库警报**</span><span class="sxs-lookup"><span data-stu-id="606fb-112">**To create SQL Server database alerts with Windows tools**</span></span>  
  
-   [<span data-ttu-id="606fb-113">设置 SQL Server 数据库警报 (Windows)</span><span class="sxs-lookup"><span data-stu-id="606fb-113">Set Up a SQL Server Database Alert &#40;Windows&#41;</span></span>](set-up-a-sql-server-database-alert-windows.md)  
  
 <span data-ttu-id="606fb-114">**使用 SQL Server Management Studio 执行监视任务**</span><span class="sxs-lookup"><span data-stu-id="606fb-114">**To perform monitoring tasks with SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="606fb-115">查看 SQL Server 错误日志 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="606fb-115">View the SQL Server Error Log &#40;SQL Server Management Studio&#41;</span></span>](../../ssms/sql-server-management-studio-ssms.md)  
  
-   [<span data-ttu-id="606fb-116">打开活动监视器 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="606fb-116">Open Activity Monitor &#40;SQL Server Management Studio&#41;</span></span>](../performance-monitor/open-activity-monitor-sql-server-management-studio.md)  
  
 <span data-ttu-id="606fb-117">**使用 Transact-SQL 存储过程并通过 SQL 跟踪执行监视任务**</span><span class="sxs-lookup"><span data-stu-id="606fb-117">**To perform monitoring tasks with SQL Trace by using Transact-SQL stored procedures**</span></span>  
  
-   [<span data-ttu-id="606fb-118">创建跟踪 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="606fb-118">Create a Trace &#40;Transact-SQL&#41;</span></span>](../sql-trace/create-a-trace-transact-sql.md)  
  
-   [<span data-ttu-id="606fb-119">设置跟踪筛选器 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="606fb-119">Set a Trace Filter &#40;Transact-SQL&#41;</span></span>](../../ssms/agent/set-sql-server-alias-for-sql-server-agent-service-ssms.md)  
  
-   [<span data-ttu-id="606fb-120">修改现有跟踪 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="606fb-120">Modify an Existing Trace &#40;Transact-SQL&#41;</span></span>](../sql-trace/modify-an-existing-trace-transact-sql.md)  
  
-   [<span data-ttu-id="606fb-121">查看保存的跟踪 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="606fb-121">View a Saved Trace &#40;Transact-SQL&#41;</span></span>](../sql-trace/view-a-saved-trace-transact-sql.md)  
  
-   [<span data-ttu-id="606fb-122">查看筛选器信息 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="606fb-122">View Filter Information &#40;Transact-SQL&#41;</span></span>](../sql-trace/view-filter-information-transact-sql.md)  
  
-   [<span data-ttu-id="606fb-123">删除跟踪 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="606fb-123">Delete a Trace &#40;Transact-SQL&#41;</span></span>](../sql-trace/delete-a-trace-transact-sql.md)  
  
 <span data-ttu-id="606fb-124">**使用 SQL Server Profiler 创建和修改跟踪**</span><span class="sxs-lookup"><span data-stu-id="606fb-124">**To create and modify traces by using SQL Server Profiler**</span></span>  
  
-   [<span data-ttu-id="606fb-125">创建跟踪 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="606fb-125">Create a Trace &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)  
  
-   [<span data-ttu-id="606fb-126">设置全局跟踪选项 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="606fb-126">Set Global Trace Options &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/set-global-trace-options-sql-server-profiler.md)  
  
-   [<span data-ttu-id="606fb-127">指定跟踪文件的事件和数据列 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="606fb-127">Specify Events and Data Columns for a Trace File &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)  
  
-   [<span data-ttu-id="606fb-128">创建 Transact-SQL 脚本来运行跟踪 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="606fb-128">Create a Transact-SQL Script for Running a Trace &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/create-a-transact-sql-script-for-running-a-trace-sql-server-profiler.md)  
  
-   [<span data-ttu-id="606fb-129">将跟踪结果保存到文件 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="606fb-129">Save Trace Results to a File &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/save-trace-results-to-a-file-sql-server-profiler.md)  
  
-   [<span data-ttu-id="606fb-130">设置跟踪文件的最大文件大小 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="606fb-130">Set a Maximum File Size for a Trace File &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/set-a-maximum-file-size-for-a-trace-file-sql-server-profiler.md)  
  
-   [<span data-ttu-id="606fb-131">将跟踪结果保存到表 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="606fb-131">Save Trace Results to a Table &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/save-trace-results-to-a-table-sql-server-profiler.md)  
  
-   [<span data-ttu-id="606fb-132">设置跟踪表的最大表大小 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="606fb-132">Set a Maximum Table Size for a Trace Table &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/set-a-maximum-table-size-for-a-trace-table-sql-server-profiler.md)  
  
-   [<span data-ttu-id="606fb-133">在跟踪中筛选事件 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="606fb-133">Filter Events in a Trace &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md)  
  
-   [<span data-ttu-id="606fb-134">查看筛选器信息 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="606fb-134">View Filter Information &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/view-filter-information-sql-server-profiler.md)  
  
-   [<span data-ttu-id="606fb-135">修改筛选器 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="606fb-135">Modify a Filter &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md)  
  
-   [<span data-ttu-id="606fb-136">基于事件开始时间筛选事件 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="606fb-136">Filter Events Based on the Event Start Time &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/filter-events-based-on-the-event-start-time-sql-server-profiler.md)  
  
-   [<span data-ttu-id="606fb-137">基于事件结束时间筛选事件 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="606fb-137">Filter Events Based on the Event End Time &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/filter-events-based-on-the-event-end-time-sql-server-profiler.md)  
  
-   [<span data-ttu-id="606fb-138">在跟踪中筛选服务器进程 ID (SPID) (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="606fb-138">Filter Server Process IDs &#40;SPIDs&#41; in a Trace &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/filter-server-process-ids-spids-in-a-trace-sql-server-profiler.md)  
  
-   [<span data-ttu-id="606fb-139">组织跟踪中显示的列 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="606fb-139">Organize Columns Displayed in a Trace &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/organize-columns-displayed-in-a-trace-sql-server-profiler.md)  
  
 <span data-ttu-id="606fb-140">**使用 SQL Server Profiler 启动、暂停和停止跟踪**</span><span class="sxs-lookup"><span data-stu-id="606fb-140">**To start, pause, and stop traces by using SQL Server Profiler**</span></span>  
  
-   [<span data-ttu-id="606fb-141">连接到服务器后自动启动跟踪 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="606fb-141">Start a Trace Automatically after Connecting to a Server &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler.md)  
  
-   [<span data-ttu-id="606fb-142">暂停跟踪 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="606fb-142">Pause a Trace &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/pause-a-trace-sql-server-profiler.md)  
  
-   [<span data-ttu-id="606fb-143">停止跟踪 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="606fb-143">Stop a Trace &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/stop-a-trace-sql-server-profiler.md)  
  
-   [<span data-ttu-id="606fb-144">在跟踪暂停或停止之后运行跟踪 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="606fb-144">Run a Trace After It Has Been Paused or Stopped &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/run-a-trace-after-it-has-been-paused-or-stopped-sql-server-profiler.md)  
  
 <span data-ttu-id="606fb-145">**使用 SQL Server Profiler 打开跟踪并配置如何显示跟踪**</span><span class="sxs-lookup"><span data-stu-id="606fb-145">**To open traces and configure how traces are displayed by using SQL Server Profiler**</span></span>  
  
-   [<span data-ttu-id="606fb-146">打开跟踪文件 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="606fb-146">Open a Trace File &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md)  
  
-   [<span data-ttu-id="606fb-147">打开跟踪表 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="606fb-147">Open a Trace Table &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md)  
  
-   [<span data-ttu-id="606fb-148">清除跟踪窗口 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="606fb-148">Clear a Trace Window &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/clear-a-trace-window-sql-server-profiler.md)  
  
-   [<span data-ttu-id="606fb-149">关闭跟踪窗口 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="606fb-149">Close a Trace Window &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/close-a-trace-window-sql-server-profiler.md)  
  
-   [<span data-ttu-id="606fb-150">设置跟踪定义默认值 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="606fb-150">Set Trace Definition Defaults &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/set-trace-definition-defaults-sql-server-profiler.md)  
  
-   [<span data-ttu-id="606fb-151">设置跟踪显示默认值 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="606fb-151">Set Trace Display Defaults &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/set-trace-display-defaults-sql-server-profiler.md)  
  
 <span data-ttu-id="606fb-152">**使用 SQL Server Profiler 重播跟踪**</span><span class="sxs-lookup"><span data-stu-id="606fb-152">**To replay traces by using SQL Server Profiler**</span></span>  
  
-   [<span data-ttu-id="606fb-153">重播跟踪文件 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="606fb-153">Replay a Trace File &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md)  
  
-   [<span data-ttu-id="606fb-154">重播跟踪表 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="606fb-154">Replay a Trace Table &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md)  
  
-   [<span data-ttu-id="606fb-155">每次重播一个事件 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="606fb-155">Replay a Single Event at a Time &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/replay-a-single-event-at-a-time-sql-server-profiler.md)  
  
-   [<span data-ttu-id="606fb-156">重播到断点 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="606fb-156">Replay to a Breakpoint &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/replay-to-a-breakpoint-sql-server-profiler.md)  
  
-   [<span data-ttu-id="606fb-157">重播至光标处 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="606fb-157">Replay to a Cursor &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/replay-to-a-cursor-sql-server-profiler.md)  
  
-   [<span data-ttu-id="606fb-158">重播 Transact-SQL 脚本 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="606fb-158">Replay a Transact-SQL Script &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/replay-a-transact-sql-script-sql-server-profiler.md)  
  
 <span data-ttu-id="606fb-159">**使用 SQL Server Profiler 创建、修改和使用跟踪模板**</span><span class="sxs-lookup"><span data-stu-id="606fb-159">**To create, modify, and use trace templates by using SQL Server Profiler**</span></span>  
  
-   [<span data-ttu-id="606fb-160">创建跟踪模板 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="606fb-160">Create a Trace Template &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/create-a-trace-template-sql-server-profiler.md)  
  
-   [<span data-ttu-id="606fb-161">修改跟踪模板 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="606fb-161">Modify a Trace Template &#40;SQL Server Profiler&#41;</span></span>](../../database-engine/modify-a-trace-template-sql-server-profiler.md)  
  
-   [<span data-ttu-id="606fb-162">从正在运行的跟踪中派生模板 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="606fb-162">Derive a Template from a Running Trace &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/derive-a-template-from-a-running-trace-sql-server-profiler.md)  
  
-   [<span data-ttu-id="606fb-163">从跟踪文件或跟踪表派生模板 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="606fb-163">Derive a Template from a Trace File or Trace Table &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/derive-a-template-from-a-trace-file-or-trace-table-sql-server-profiler.md)  
  
-   [<span data-ttu-id="606fb-164">导出跟踪模板 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="606fb-164">Export a Trace Template &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/export-a-trace-template-sql-server-profiler.md)  
  
-   [<span data-ttu-id="606fb-165">导入跟踪模板 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="606fb-165">Import a Trace Template &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/import-a-trace-template-sql-server-profiler.md)  
  
 <span data-ttu-id="606fb-166">**使用 SQL Server Profiler 跟踪来收集和监视服务器性能**</span><span class="sxs-lookup"><span data-stu-id="606fb-166">**To use SQL Server Profiler traces to collect and monitor server performance**</span></span>  
  
-   [<span data-ttu-id="606fb-167">在跟踪时查找值或数据列 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="606fb-167">Find a Value or Data Column While Tracing &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/find-a-value-or-data-column-while-tracing-sql-server-profiler.md)  
  
-   [<span data-ttu-id="606fb-168">保存死锁图形 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="606fb-168">Save Deadlock Graphs &#40;SQL Server Profiler&#41;</span></span>](save-deadlock-graphs-sql-server-profiler.md)  
  
-   [<span data-ttu-id="606fb-169">分别保存 Showplan XML 事件 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="606fb-169">Save Showplan XML Events Separately &#40;SQL Server Profiler&#41;</span></span>](save-showplan-xml-events-separately-sql-server-profiler.md)  
  
-   [<span data-ttu-id="606fb-170">分别保存 Showplan XML Statistics Profile 事件 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="606fb-170">Save Showplan XML Statistics Profile Events Separately &#40;SQL Server Profiler&#41;</span></span>](save-showplan-xml-statistics-profile-events-separately-sql-server-profiler.md)  
  
-   [<span data-ttu-id="606fb-171">从跟踪提取脚本 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="606fb-171">Extract a Script from a Trace &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/extract-a-script-from-a-trace-sql-server-profiler.md)  
  
-   [<span data-ttu-id="606fb-172">将跟踪与 Windows 性能日志数据关联 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="606fb-172">Correlate a Trace with Windows Performance Log Data &#40;SQL Server Profiler&#41;</span></span>](../../database-engine/correlate-a-trace-with-windows-performance-log-data-sql-server-profiler.md)  
  
  
