---
title: 监视本机编译存储过程的执行 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 55548cb2-77a8-4953-8b5a-f2778a4f13cf
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d14d27cdc20c0f090c7a030efe05cfce4842f437
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693872"
---
# <a name="monitoring-performance-of-natively-compiled-stored-procedures"></a><span data-ttu-id="c90f5-102">监视本机编译的存储过程的执行</span><span class="sxs-lookup"><span data-stu-id="c90f5-102">Monitoring Performance of Natively Compiled Stored Procedures</span></span>
  <span data-ttu-id="c90f5-103">本主题论述如何监视本机编译的存储过程的性能</span><span class="sxs-lookup"><span data-stu-id="c90f5-103">This topic discusses how you can monitor the performance of natively compiled stored procedures</span></span>  
  
## <a name="using-extended-events"></a><span data-ttu-id="c90f5-104">使用扩展事件</span><span class="sxs-lookup"><span data-stu-id="c90f5-104">Using Extended Events</span></span>  
 <span data-ttu-id="c90f5-105">使用 `sp_statement_completed` 扩展事件可以跟踪查询的执行情况。</span><span class="sxs-lookup"><span data-stu-id="c90f5-105">Use the `sp_statement_completed` extended event to trace execution of a query.</span></span> <span data-ttu-id="c90f5-106">使用此事件或者可以选择使用针对某一特定本机编译的存储过程的 object_id 的筛选器创建一个扩展事件会话。在执行各查询后引发该扩展事件。</span><span class="sxs-lookup"><span data-stu-id="c90f5-106">Create an extended event session with this event, optionally with a filter on object_id for a particular natively compiled stored procedure, The extended event is raised after the execution of each query.</span></span> <span data-ttu-id="c90f5-107">该扩展事件报告的 CPU 时间和持续时间指示该查询占用了多少 CPU 以及执行时间。</span><span class="sxs-lookup"><span data-stu-id="c90f5-107">The CPU time and duration reported by the extended event indicate how much CPU the query used and the execution time.</span></span> <span data-ttu-id="c90f5-108">占用大量 CPU 时间的本机编译的存储过程可能具有性能问题。</span><span class="sxs-lookup"><span data-stu-id="c90f5-108">A natively compiled stored procedure that uses a lot of CPU time may have performance problems.</span></span>  
  
 <span data-ttu-id="c90f5-109">`line_number` 连同扩展事件中的 `object_id` 可用于调查该查询。</span><span class="sxs-lookup"><span data-stu-id="c90f5-109">`line_number`, along with the `object_id` in the extended event can be used to investigate the query.</span></span> <span data-ttu-id="c90f5-110">可以使用以下查询检索过程定义。</span><span class="sxs-lookup"><span data-stu-id="c90f5-110">The following query can be used to retrieve the procedure definition.</span></span> <span data-ttu-id="c90f5-111">可以使用行号标识该定义内的查询：</span><span class="sxs-lookup"><span data-stu-id="c90f5-111">The line number can be used to identify the query within the definition:</span></span>  
  
```sql  
select [definition] from sys.sql_modules where object_id=object_id  
```  
  
 <span data-ttu-id="c90f5-112">有关扩展事件的详细信息 `sp_statement_completed` ，请参阅[如何检索导致了事件的语句](https://blogs.msdn.com/b/extended_events/archive/2010/05/07/making-a-statement-how-to-retrieve-the-t-sql-statement-that-caused-an-event.aspx)。</span><span class="sxs-lookup"><span data-stu-id="c90f5-112">For more information about the `sp_statement_completed` extended event, see [How to retrieve the statement that caused an event](https://blogs.msdn.com/b/extended_events/archive/2010/05/07/making-a-statement-how-to-retrieve-the-t-sql-statement-that-caused-an-event.aspx).</span></span>  
  
## <a name="using-data-management-views"></a><span data-ttu-id="c90f5-113">使用数据管理视图</span><span class="sxs-lookup"><span data-stu-id="c90f5-113">Using Data Management Views</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c90f5-114">支持在过程级别和查询级别收集本机编译的存储过程的执行统计信息。</span><span class="sxs-lookup"><span data-stu-id="c90f5-114">supports collecting execution statistics for natively compiled stored procedures, both on the procedure level and the query level.</span></span> <span data-ttu-id="c90f5-115">由于对性能的影响，默认不启用收集执行统计信息。</span><span class="sxs-lookup"><span data-stu-id="c90f5-115">Collecting execution statistics is not enabled by default due to performance impact.</span></span>  
  
 <span data-ttu-id="c90f5-116">可使用 [sys.sp_xtp_control_proc_exec_stats (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-control-proc-exec-stats-transact-sql) 对本机编译的存储过程启用和禁用统计信息收集。</span><span class="sxs-lookup"><span data-stu-id="c90f5-116">You can enable and disable statistics collection on natively compiled stored procedures using [sys.sp_xtp_control_proc_exec_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-control-proc-exec-stats-transact-sql).</span></span>  
  
 <span data-ttu-id="c90f5-117">通过 [sys.sp_xtp_control_proc_exec_stats (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-control-proc-exec-stats-transact-sql) 启用统计信息收集后，你可以使用 [sys.dm_exec_procedure_stats (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql) 监视本机编译存储过程的性能。</span><span class="sxs-lookup"><span data-stu-id="c90f5-117">When statistics collection is enabled with [sys.sp_xtp_control_proc_exec_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-control-proc-exec-stats-transact-sql), you can use [sys.dm_exec_procedure_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql) to monitor performance of a natively compiled stored procedure.</span></span>  
  
 <span data-ttu-id="c90f5-118">通过 [sys.sp_xtp_control_query_exec_stats (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-control-query-exec-stats-transact-sql) 启用统计信息收集后，你可以使用 [sys.dm_exec_query_stats (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql) 监视本机编译存储过程的性能。</span><span class="sxs-lookup"><span data-stu-id="c90f5-118">When statistics collection is enabled with [sys.sp_xtp_control_query_exec_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-control-query-exec-stats-transact-sql), you can use [sys.dm_exec_query_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql) to monitor performance of a natively compiled stored procedure.</span></span>  
  
 <span data-ttu-id="c90f5-119">在收集开始时，启用统计信息收集。</span><span class="sxs-lookup"><span data-stu-id="c90f5-119">At the start of collection, enable statistics collection.</span></span> <span data-ttu-id="c90f5-120">然后，执行本机编译的存储过程。</span><span class="sxs-lookup"><span data-stu-id="c90f5-120">Then, execute the natively compiled stored procedure.</span></span> <span data-ttu-id="c90f5-121">在收集结束时，禁用统计信息收集。</span><span class="sxs-lookup"><span data-stu-id="c90f5-121">At the end of collection, disable statistics collection.</span></span> <span data-ttu-id="c90f5-122">然后，对 DMV 返回的执行统计信息进行分析。</span><span class="sxs-lookup"><span data-stu-id="c90f5-122">Then, analyze the execution statistics returned by the DMVs.</span></span>  
  
 <span data-ttu-id="c90f5-123">在你收集统计信息后，可以使用 [sys.dm_exec_procedure_stats (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql) 针对某一过程查询本机编译的存储过程的执行统计信息，以及使用 [sys.dm_exec_query_stats (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql) 针对查询来查询本机编译的存储过程的执行统计信息。</span><span class="sxs-lookup"><span data-stu-id="c90f5-123">After you collect statistics, the execution statistics for natively compiled stored procedures can be queried for a procedure with [sys.dm_exec_procedure_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql), and for queries with [sys.dm_exec_query_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c90f5-124">对于启用统计信息收集时的本机编译的存储过程，以毫秒为单位收集工作线程时间。</span><span class="sxs-lookup"><span data-stu-id="c90f5-124">For natively compiled stored procedures when statistics collection is enabled, worker time is collected in milliseconds.</span></span> <span data-ttu-id="c90f5-125">如果查询执行不到 1 毫秒，则该值将为 0。</span><span class="sxs-lookup"><span data-stu-id="c90f5-125">If the query executes in less than a millisecond, the value will be 0.</span></span> <span data-ttu-id="c90f5-126">对于本机编译的存储过程，如果许多执行所用的时间都不到 1 毫秒，则 **total_worker_time** 可能不精确。</span><span class="sxs-lookup"><span data-stu-id="c90f5-126">For natively compiled stored procedures, **total_worker_time** may not be accurate if many executions take less than 1 millisecond.</span></span>  
  
 <span data-ttu-id="c90f5-127">下面的查询在统计信息收集后返回当前数据库中本机编译的存储过程的过程名称和执行统计信息：</span><span class="sxs-lookup"><span data-stu-id="c90f5-127">The following query returns the procedure names and execution statistics for natively compiled stored procedures in the current database, after statistics collection:</span></span>  
  
```sql  
select object_id,  
       object_name(object_id) as 'object name',  
       cached_time,  
       last_execution_time,  
       execution_count,  
       total_worker_time,  
       last_worker_time,  
       min_worker_time,  
       max_worker_time,  
       total_elapsed_time,  
       last_elapsed_time,  
       min_elapsed_time,  
       max_elapsed_time   
from sys.dm_exec_procedure_stats  
where database_id=db_id() and object_id in (select object_id   
from sys.sql_modules where uses_native_compilation=1)  
order by total_worker_time desc  
```  
  
 <span data-ttu-id="c90f5-128">下面的查询按总工作线程时间的降序返回当前数据库中已为其收集了统计信息的本机编译的存储过程中所有查询的查询文本以及执行统计信息：</span><span class="sxs-lookup"><span data-stu-id="c90f5-128">The following query returns the query text as well as execution statistics for all queries in natively compiled stored procedures in the current database for which statistics have been collected, ordered by total worker time, in descending order:</span></span>  
  
```sql  
select st.objectid,   
       object_name(st.objectid) as 'object name',   
       SUBSTRING(st.text, (qs.statement_start_offset/2) + 1, ((qs.statement_end_offset-qs.statement_start_offset)/2) + 1) as 'query text',   
       qs.creation_time,  
       qs.last_execution_time,  
       qs.execution_count,  
       qs.total_worker_time,  
       qs.last_worker_time,  
       qs.min_worker_time,  
       qs.max_worker_time,  
       qs.total_elapsed_time,  
       qs.last_elapsed_time,  
       qs.min_elapsed_time,  
       qs.max_elapsed_time  
from sys.dm_exec_query_stats qs cross apply sys.dm_exec_sql_text(sql_handle) st  
where  st.dbid=db_id() and st.objectid in (select object_id   
from sys.sql_modules where uses_native_compilation=1)  
order by qs.total_worker_time desc  
```  
  
 <span data-ttu-id="c90f5-129">本机编译的存储过程支持 SHOWPLAN_XML（估计的执行计划）。</span><span class="sxs-lookup"><span data-stu-id="c90f5-129">Natively compiled stored procedures support SHOWPLAN_XML (estimated execution plan).</span></span> <span data-ttu-id="c90f5-130">可以使用该估计的执行计划检查查询计划，以便找到任何错误计划问题。</span><span class="sxs-lookup"><span data-stu-id="c90f5-130">The estimated execution plan can be used to inspect the query plan, to find any bad plan issues.</span></span> <span data-ttu-id="c90f5-131">错误计划的常见原因是：</span><span class="sxs-lookup"><span data-stu-id="c90f5-131">Common reasons for bad plans are:</span></span>  
  
-   <span data-ttu-id="c90f5-132">在创建过程前未更新统计信息。</span><span class="sxs-lookup"><span data-stu-id="c90f5-132">Stats were not updated before the procedure was created.</span></span>  
  
-   <span data-ttu-id="c90f5-133">缺失索引</span><span class="sxs-lookup"><span data-stu-id="c90f5-133">Missing indexes</span></span>  
  
 <span data-ttu-id="c90f5-134">通过执行以下 [!INCLUDE[tsql](../../includes/tsql-md.md)]获取 Showplan XML：</span><span class="sxs-lookup"><span data-stu-id="c90f5-134">Showplan XML is obtained by executing the following [!INCLUDE[tsql](../../includes/tsql-md.md)]:</span></span>  
  
```sql  
SET SHOWPLAN_XML ON  
GO  
EXEC my_proc   
GO  
SET SHOWPLAN_XML OFF  
GO  
```  
  
 <span data-ttu-id="c90f5-135">或者，在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，选择过程名称并且单击 **“显示估计的执行计划”** 。</span><span class="sxs-lookup"><span data-stu-id="c90f5-135">Alternatively, in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], select the procedure name and click **Display Estimated Execution Plan**.</span></span>  
  
 <span data-ttu-id="c90f5-136">本机编译的存储过程的估计的执行计划显示过程中查询的查询运算符和表达式。</span><span class="sxs-lookup"><span data-stu-id="c90f5-136">The estimated execution plan for natively compiled stored procedures shows the query operators and expressions for the queries in the procedure.</span></span> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] <span data-ttu-id="c90f5-137">对于本机编译的存储过程，并不支持所有 SHOWPLAN_XML 属性。</span><span class="sxs-lookup"><span data-stu-id="c90f5-137">does not support all SHOWPLAN_XML attributes for natively compiled stored procedures.</span></span> <span data-ttu-id="c90f5-138">例如，与查询优化器开销相关的属性不是针对过程的 SHOWPLAN_XML 的一部分。</span><span class="sxs-lookup"><span data-stu-id="c90f5-138">For example, attributes related to query optimizer costing are not part of the SHOWPLAN_XML for the procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c90f5-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c90f5-139">See Also</span></span>  
 [<span data-ttu-id="c90f5-140">本机编译的存储过程</span><span class="sxs-lookup"><span data-stu-id="c90f5-140">Natively Compiled Stored Procedures</span></span>](natively-compiled-stored-procedures.md)  
  
  
