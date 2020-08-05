---
title: 使用 SQL Server Profiler 查看和分析跟踪 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- Profiler [SQL Server Profiler], viewing traces
- SQL Server Profiler, viewing traces
- traces [SQL Server], viewing
- SQL Server Profiler, troubleshooting
- troubleshooting [SQL Server], traces
- events [SQL Server], finding inside trace
- Profiler [SQL Server Profiler], troubleshooting
- traces [SQL Server], events
ms.assetid: 17e821ca-a12e-4192-acc1-96765d9ae266
author: stevestein
ms.author: sstein
ms.openlocfilehash: b3e848fe9a07d838631eef1737c2a7679b67e649
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579919"
---
# <a name="view-and-analyze-traces-with-sql-server-profiler"></a><span data-ttu-id="6134d-102">使用 SQL Server Profiler 查看和分析跟踪</span><span class="sxs-lookup"><span data-stu-id="6134d-102">View and Analyze Traces with SQL Server Profiler</span></span>
  <span data-ttu-id="6134d-103">可以使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 查看跟踪中捕获的事件数据。</span><span class="sxs-lookup"><span data-stu-id="6134d-103">Use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to view captured event data in a trace.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="6134d-104">显示基于定义的跟踪属性的数据。</span><span class="sxs-lookup"><span data-stu-id="6134d-104">displays data based on defined trace properties.</span></span> <span data-ttu-id="6134d-105">分析 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据的一种方式是将数据复制到其他程序中，例如 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 优化顾问。</span><span class="sxs-lookup"><span data-stu-id="6134d-105">One way to analyze [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data is to copy the data to another program, such as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor.</span></span> [!INCLUDE[ssDE](../../includes/ssde-md.md)]<span data-ttu-id="6134d-106">如果跟踪中包括“文本”数据列，则优化顾问可以使用包含 SQL 批处理和远程过程调用 (RPC) 事件的跟踪文件  。</span><span class="sxs-lookup"><span data-stu-id="6134d-106">Tuning Advisor can use a trace file that contains SQL batch and remote procedure call (RPC) events if the **Text** data column is included in the trace.</span></span> <span data-ttu-id="6134d-107">为了确保捕获正确的事件和列以便与 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 优化顾问一起使用，请使用随 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]一起提供的预定义优化模板。</span><span class="sxs-lookup"><span data-stu-id="6134d-107">To make sure that the correct events and columns are captured for use with [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor, use the predefined Tuning template that is supplied with [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
 <span data-ttu-id="6134d-108">使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]打开跟踪时，如果跟踪文件是由 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 或 SQL 跟踪系统存储过程创建的，则该文件不需要带 .trc 文件扩展名。</span><span class="sxs-lookup"><span data-stu-id="6134d-108">When you open a trace by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], the trace file does not need to have the .trc file extension if the file was created by either [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] or SQL Trace system stored procedures.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="6134d-109">还可以读取 SQL 跟踪 .log 文件和通用 SQL 脚本文件。</span><span class="sxs-lookup"><span data-stu-id="6134d-109">can also read SQL Trace .log files and generic SQL script files.</span></span> <span data-ttu-id="6134d-110">打开不带 .log 文件扩展名的 SQL 跟踪 .log 文件（例如 trace.txt）时，应将文件格式指定为 **SQLTrace_Log** 。</span><span class="sxs-lookup"><span data-stu-id="6134d-110">When opening a SQL Trace .log file that does not have a .log file extension, such as trace.txt, specify **SQLTrace_Log** as the file format.</span></span>  
  
 <span data-ttu-id="6134d-111">您可以配置 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 日期和时间显示格式以便有助于跟踪分析。</span><span class="sxs-lookup"><span data-stu-id="6134d-111">You can configure the [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] date and time display format to assist in trace analysis.</span></span>  
  
## <a name="troubleshooting-data"></a><span data-ttu-id="6134d-112">排除数据故障</span><span class="sxs-lookup"><span data-stu-id="6134d-112">Troubleshooting Data</span></span>  
 <span data-ttu-id="6134d-113">使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]时，您可以按 **“持续时间”** 、 **CPU**、 **“读”** 或 **“写”** 数据列将跟踪或跟踪文件分组来排除数据故障。</span><span class="sxs-lookup"><span data-stu-id="6134d-113">Using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], you can troubleshoot data by grouping traces or trace files by the **Duration**, **CPU**, **Reads**, or **Writes** data columns.</span></span> <span data-ttu-id="6134d-114">例如，您可以对性能差的查询或逻辑读取操作数特别高的查询进行数据故障排除。</span><span class="sxs-lookup"><span data-stu-id="6134d-114">Examples of data you might troubleshoot are queries that perform poorly or that have exceptionally high numbers of logical read operations.</span></span>  
  
 <span data-ttu-id="6134d-115">通过将跟踪保存至表和使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查询事件数据，可以找到其他信息。</span><span class="sxs-lookup"><span data-stu-id="6134d-115">Additional information can be found by saving traces to tables and using [!INCLUDE[tsql](../../includes/tsql-md.md)] to query the event data.</span></span> <span data-ttu-id="6134d-116">例如，若要确定哪些 **SQL:BatchCompleted** 事件的等待时间过长，可执行：</span><span class="sxs-lookup"><span data-stu-id="6134d-116">For example, to determine which **SQL:BatchCompleted** events had excessive wait time, execute the following:</span></span>  
  
```  
SELECT  TextData, Duration, CPU  
FROM    trace_table_name  
WHERE   EventClass = 12 -- SQL:BatchCompleted events  
AND     CPU < (Duration * 1000)  
```  
  
> [!NOTE]  
>  <span data-ttu-id="6134d-117">服务器以微秒（百万分之一秒或 10<sup>-6</sup> 秒）为单位报告事件的持续时间，以毫秒（千分之一秒或 10<sup>-3</sup> 秒）为单位报告事件使用的 CPU 时间。</span><span class="sxs-lookup"><span data-stu-id="6134d-117">The server reports the duration of an event in microseconds (one millionth, or 10<sup>-6</sup>, of a second) and the amount of CPU time used by the event in milliseconds (one thousandth, or 10<sup>-3</sup>, of a second).</span></span> <span data-ttu-id="6134d-118">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 图形用户界面默认以毫秒为单位显示 **“持续时间”** 列，但是当跟踪保存到文件或数据库表中时，将以微秒为单位写入“持续时间”  列值。</span><span class="sxs-lookup"><span data-stu-id="6134d-118">The [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] graphical user interface displays the **Duration** column in milliseconds by default, but when a trace is saved to either a file or a database table, the **Duration** column value is written in microseconds.</span></span>  
  
## <a name="displaying-object-names-when-viewing-traces"></a><span data-ttu-id="6134d-119">查看跟踪时显示对象名称</span><span class="sxs-lookup"><span data-stu-id="6134d-119">Displaying Object Names When Viewing Traces</span></span>  
 <span data-ttu-id="6134d-120">如果你要显示对象名称而不是对象标识符（**对象 ID**），必须捕获“服务器名称”  和“数据库 ID”  数据列以及“对象名称”  数据列。</span><span class="sxs-lookup"><span data-stu-id="6134d-120">If you wish to display the name of an object rather than the object identifier (**Object ID**), you must capture the **Server Name** and **Database ID** data columns along with the **Object Name** data column.</span></span>  
  
 <span data-ttu-id="6134d-121">如果您选择按 **“对象 ID”** 数据列分组，请确保先按 **“服务器名称”** 和 **“数据库 ID”** 数据列分组，然后按 **“对象 ID”** 数据列分组。</span><span class="sxs-lookup"><span data-stu-id="6134d-121">If you choose to group by the **Object ID** data column, make sure you group by the **Server Name** and **Database ID** data columns first, and then by the **Object ID** data column.</span></span> <span data-ttu-id="6134d-122">同样，如果您选择按 **“索引 ID”** 数据列分组，请确保先按 **“服务器名称”** 、 **“数据库 ID”** 和 **“对象 ID”** 数据列分组，然后按 **“索引 ID”** 数据列分组。</span><span class="sxs-lookup"><span data-stu-id="6134d-122">Similarly, if you choose to group by the **Index ID** data column, make sure you group by the **Server Name**, **Database ID**, and **Object ID** data columns first, and then by the **Index ID** data columns.</span></span> <span data-ttu-id="6134d-123">您必须按照此顺序分组，因为对象 ID 和索引 ID 在服务器和数据库之间并不是唯一的，而索引 ID 甚至在各对象之间都不是唯一的。</span><span class="sxs-lookup"><span data-stu-id="6134d-123">You must group in this order because object and index IDs are not unique among servers and databases (and among objects for index IDs).</span></span>  
  
## <a name="finding-specific-events-within-a-trace"></a><span data-ttu-id="6134d-124">查找跟踪内的特定事件</span><span class="sxs-lookup"><span data-stu-id="6134d-124">Finding Specific Events Within a Trace</span></span>  
 <span data-ttu-id="6134d-125">若要查找跟踪中的事件并对事件进行分组，请按下列步骤执行操作：</span><span class="sxs-lookup"><span data-stu-id="6134d-125">To find and group events in a trace, follow these steps:</span></span>  
  
1.  <span data-ttu-id="6134d-126">创建跟踪。</span><span class="sxs-lookup"><span data-stu-id="6134d-126">Create your trace.</span></span>  
  
    -   <span data-ttu-id="6134d-127">定义跟踪时，除了要捕获的任何其他数据列外，还要捕获 **“事件类”** 、 **ClientProcessID**和 **“开始时间”** 数据列。</span><span class="sxs-lookup"><span data-stu-id="6134d-127">When defining the trace, capture the **Event Class**, **ClientProcessID**, and **Start Time** data columns in addition to any other data columns you want to capture.</span></span> <span data-ttu-id="6134d-128">有关详细信息，请参阅[创建跟踪 (SQL Server Profiler)](create-a-trace-sql-server-profiler.md)。</span><span class="sxs-lookup"><span data-stu-id="6134d-128">For more information, see [Create a Trace &#40;SQL Server Profiler&#41;](create-a-trace-sql-server-profiler.md).</span></span>  
  
    -   <span data-ttu-id="6134d-129">按“事件类” **“事件类”** 数据列对捕获的数据进行分组，并将跟踪内容捕获到文件或表中。</span><span class="sxs-lookup"><span data-stu-id="6134d-129">Group the captured data by the **Event Class**data column, and capture the trace to a file or table.</span></span> <span data-ttu-id="6134d-130">若要将捕获的数据分组，请单击“跟踪属性”对话框中 **“事件选择”** 选项卡中的 **“组织列”** 。</span><span class="sxs-lookup"><span data-stu-id="6134d-130">To group the captured data, click **Organize Columns** on the **Events Selection** tab of the Trace Properties dialog box.</span></span> <span data-ttu-id="6134d-131">有关详细信息，请参阅[组织跟踪中显示的列 (SQL Server Profiler)](organize-columns-displayed-in-a-trace-sql-server-profiler.md)。</span><span class="sxs-lookup"><span data-stu-id="6134d-131">For more information, see [Organize Columns Displayed in a Trace &#40;SQL Server Profiler&#41;](organize-columns-displayed-in-a-trace-sql-server-profiler.md).</span></span>  
  
    -   <span data-ttu-id="6134d-132">开始跟踪，并在经过适当时间或捕获了一定数量的事件后停止。</span><span class="sxs-lookup"><span data-stu-id="6134d-132">Start the trace and stop it after the appropriate time has passed or number of events have been captured.</span></span>  
  
2.  <span data-ttu-id="6134d-133">查找目标事件。</span><span class="sxs-lookup"><span data-stu-id="6134d-133">Find the target events.</span></span>  
  
    -   <span data-ttu-id="6134d-134">打开跟踪文件或表，并展开所需事件类的节点，例如， **Deadlock Chain**。</span><span class="sxs-lookup"><span data-stu-id="6134d-134">Open the trace file or table, and expand the node of the desired event class; for example, **Deadlock Chain**.</span></span> <span data-ttu-id="6134d-135">有关详细信息，请参阅 [打开跟踪文件 (SQL Server Profiler)](open-a-trace-file-sql-server-profiler.md) 或 [打开跟踪表 (SQL Server Profiler)](open-a-trace-table-sql-server-profiler.md)一起提供的预定义优化模板。</span><span class="sxs-lookup"><span data-stu-id="6134d-135">For more information, see [Open a Trace File &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) or [Open a Trace Table &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md).</span></span>  
  
    -   <span data-ttu-id="6134d-136">在跟踪数据中搜索直到找到所需的事件（使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 的“编辑”菜单上的“查找”命令帮助查找跟踪中的值）。</span><span class="sxs-lookup"><span data-stu-id="6134d-136">Search through the trace data until you find the events for which you are looking (use the **Find** command on the **Edit** menu of [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to help you find values in the trace).</span></span> <span data-ttu-id="6134d-137">记录所跟踪事件的“ClientProcessID”  和“开始时间”  数据列中的值。</span><span class="sxs-lookup"><span data-stu-id="6134d-137">Note the values in the **ClientProcessID** and **Start Time** data columns of the events you trace.</span></span>  
  
3.  <span data-ttu-id="6134d-138">在上下文中显示事件。</span><span class="sxs-lookup"><span data-stu-id="6134d-138">Display the events in context.</span></span>  
  
    -   <span data-ttu-id="6134d-139">显示跟踪属性，并按“ClientProcessID” **ClientProcessID**数据列（而不是“事件类” **“事件类”** 数据列。</span><span class="sxs-lookup"><span data-stu-id="6134d-139">Display the trace properties, and group by the **ClientProcessID**data column rather than by the **Event Class** data column.</span></span>  
  
    -   <span data-ttu-id="6134d-140">展开要查看的每个客户端进程 ID 的节点。</span><span class="sxs-lookup"><span data-stu-id="6134d-140">Expand the nodes of each client process ID you want to view.</span></span> <span data-ttu-id="6134d-141">手动搜索整个跟踪内容，或使用“查找” **的** 直到找到目标事件的“开始时间” **“开始时间”** 值（如上所述）。</span><span class="sxs-lookup"><span data-stu-id="6134d-141">Search through the trace manually, or use **Find** until you find the previously noted **Start Time**values of the target events.</span></span> <span data-ttu-id="6134d-142">这些事件与属于每个选定客户端进程 ID 的其他事件一起按时间顺序进行显示。</span><span class="sxs-lookup"><span data-stu-id="6134d-142">The events are displayed in chronological order with the other events that belong to each selected client process ID.</span></span> <span data-ttu-id="6134d-143">例如，跟踪内容中捕获的“死锁”  和“死锁链”  事件在展开的客户端进程 ID 内紧跟在“SQL:BatchStarting”  事件之后显示。</span><span class="sxs-lookup"><span data-stu-id="6134d-143">For example, the **Deadlock** and **Deadlock Chain**events, captured within the trace, appear immediately after the **SQL:BatchStarting**events within the expanded client process ID.</span></span>  
  
 <span data-ttu-id="6134d-144">可以使用相同的方法查找任何已分组的事件。</span><span class="sxs-lookup"><span data-stu-id="6134d-144">The same technique can be used to find any grouped events.</span></span> <span data-ttu-id="6134d-145">找到要查找的事件后，按 **ClientProcessID**、 **ApplicationName**或其他事件类分组，以便按时间顺序查看相关活动。</span><span class="sxs-lookup"><span data-stu-id="6134d-145">Once you have found the events you seek, group them by **ClientProcessID**, **ApplicationName**, or another event class to view related activity in chronological order.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6134d-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6134d-146">See Also</span></span>  
 <span data-ttu-id="6134d-147">[查看保存的跟踪 (Transact-SQL)](../../relational-databases/sql-trace/view-a-saved-trace-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="6134d-147">[View a Saved Trace &#40;Transact-SQL&#41;](../../relational-databases/sql-trace/view-a-saved-trace-transact-sql.md) </span></span>  
 <span data-ttu-id="6134d-148">[sys.fn_trace_getinfo (Transact-SQL)](/sql/relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6134d-148">[sys.fn_trace_getinfo &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql) </span></span>  
 <span data-ttu-id="6134d-149">[查看筛选器信息 (SQL Server Profiler)](view-filter-information-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="6134d-149">[View Filter Information &#40;SQL Server Profiler&#41;](view-filter-information-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="6134d-150">[查看筛选器信息 (Transact-SQL)](../../relational-databases/sql-trace/view-filter-information-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="6134d-150">[View Filter Information &#40;Transact-SQL&#41;](../../relational-databases/sql-trace/view-filter-information-transact-sql.md) </span></span>  
 <span data-ttu-id="6134d-151">[打开跟踪文件 (SQL Server Profiler)](open-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="6134d-151">[Open a Trace File &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="6134d-152">打开跟踪表 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="6134d-152">Open a Trace Table &#40;SQL Server Profiler&#41;</span></span>](open-a-trace-table-sql-server-profiler.md)  
  
  
