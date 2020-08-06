---
title: 创建跟踪 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], example
- traces [SQL Server], creating
ms.assetid: 79dd4254-e3c6-467a-bb6f-f99e51757e99
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 35644891b2dca8359d6dc68fbddb67288d241cb4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587748"
---
# <a name="create-a-trace-transact-sql"></a><span data-ttu-id="cd8fc-102">创建跟踪 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="cd8fc-102">Create a Trace (Transact-SQL)</span></span>
  <span data-ttu-id="cd8fc-103">本主题介绍了如何使用存储过程创建跟踪。</span><span class="sxs-lookup"><span data-stu-id="cd8fc-103">This topic describes how to use stored procedures to create a trace.</span></span>  
  
### <a name="to-create-a-trace"></a><span data-ttu-id="cd8fc-104">创建跟踪</span><span class="sxs-lookup"><span data-stu-id="cd8fc-104">To create a trace</span></span>  
  
1.  <span data-ttu-id="cd8fc-105">执行带所需参数的 **sp_trace_create** 以创建新的跟踪。</span><span class="sxs-lookup"><span data-stu-id="cd8fc-105">Execute **sp_trace_create** with the required parameters to create a new trace.</span></span> <span data-ttu-id="cd8fc-106">新的跟踪将处于停止状态（状态  为 **0**）。</span><span class="sxs-lookup"><span data-stu-id="cd8fc-106">The new trace will be in a stopped state (*status* is **0**).</span></span>  
  
2.  <span data-ttu-id="cd8fc-107">执行带所需参数的 **sp_trace_setevent** 以选择要跟踪的事件和列。</span><span class="sxs-lookup"><span data-stu-id="cd8fc-107">Execute **sp_trace_setevent** with the required parameters to select the events and columns to trace.</span></span>  
  
3.  <span data-ttu-id="cd8fc-108">也可以执行 **sp_trace_setfilter** 以设置任意筛选或筛选组合。</span><span class="sxs-lookup"><span data-stu-id="cd8fc-108">Optionally, execute **sp_trace_setfilter** to set any or a combination of filters.</span></span>  
  
     <span data-ttu-id="cd8fc-109">**sp_trace_setevent** 和 **sp_trace_setfilter** 只能在已停止的现有跟踪上执行。</span><span class="sxs-lookup"><span data-stu-id="cd8fc-109">**sp_trace_setevent** and **sp_trace_setfilter** can be executed only on existing traces that are stopped.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="cd8fc-110">与常规存储过程不同的是，必须严格键入所有 SQL Server Profiler 存储过程的参数 (<strong>sp_trace_xx</strong>)，而且这些参数不支持数据类型自动转换。</span><span class="sxs-lookup"><span data-stu-id="cd8fc-110">Unlike regular stored procedures, parameters of all SQL Server Profiler stored procedures (<strong>sp_trace_*xx*</strong>) are strictly typed and do not support automatic data type conversion.</span></span> <span data-ttu-id="cd8fc-111">如果这些参数不是使用正确的输入参数数据类型（正如参数说明中指定的一样）调用的，则存储过程会返回错误。</span><span class="sxs-lookup"><span data-stu-id="cd8fc-111">If these parameters are not called with the correct input parameter data types, as specified in the argument description, the stored procedure returns an error.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd8fc-112">示例</span><span class="sxs-lookup"><span data-stu-id="cd8fc-112">Example</span></span>  
 <span data-ttu-id="cd8fc-113">下面的代码演示如何使用 [!INCLUDE[tsql](../../includes/tsql-md.md)]创建跟踪。</span><span class="sxs-lookup"><span data-stu-id="cd8fc-113">The following code demonstrates creating a trace using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="cd8fc-114">代码分为三部分：创建跟踪、填充跟踪文件以及停止跟踪。</span><span class="sxs-lookup"><span data-stu-id="cd8fc-114">It is in three sections: creating the trace, populating the trace file, and stopping the trace.</span></span> <span data-ttu-id="cd8fc-115">通过添加要跟踪的事件来自定义跟踪。</span><span class="sxs-lookup"><span data-stu-id="cd8fc-115">Customize the trace by adding the events that you want to trace.</span></span> <span data-ttu-id="cd8fc-116">有关事件和列的列表，请参阅 [sp_trace_setevent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)创建跟踪。</span><span class="sxs-lookup"><span data-stu-id="cd8fc-116">For the list of events and columns, see [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql).</span></span>  
  
 <span data-ttu-id="cd8fc-117">下面的代码创建跟踪，向跟踪添加事件，随后启动跟踪：</span><span class="sxs-lookup"><span data-stu-id="cd8fc-117">The following code creates a trace, adds events to the trace, and then starts the trace:</span></span>  
  
```  
DECLARE @RC int, @TraceID int, @on BIT  
EXEC @rc = sp_trace_create @TraceID output, 0, N'C:\SampleTrace'  
  
-- Select the return code to see if the trace creation was successful.  
SELECT RC = @RC, TraceID = @TraceID  
  
-- Set the events and data columns you need to capture.  
SELECT @on = 1  
  
-- 10 is RPC:Completed event. 1 is TextData column.   
EXEC sp_trace_setevent @TraceID, 10, 1, @on   
-- 13 is SQL:BatchStarting, 11 is LoginName  
EXEC sp_trace_setevent @TraceID, 13, 11, @on   
-- 13 is SQL:BatchStarting, 14 is StartTime  
EXEC sp_trace_setevent @TraceID, 13, 14, @on   
-- 12 is SQL:BatchCompleted, 15 is EndTime  
EXEC sp_trace_setevent @TraceID, 12, 15, @on   
-- 13 is SQL:BatchStarting, 1 is TextData  
EXEC sp_trace_setevent @TraceID, 13, 1, @on   
  
-- Set any filter. Not provided in this example  
--EXEC sp_trace_setfilter 1, 10, 0, 6, N'%Profiler%'  
  
-- Start Trace (status 1 = start)  
EXEC @RC = sp_trace_setstatus @TraceID, 1  
GO  
  
```  
  
## <a name="example"></a><span data-ttu-id="cd8fc-118">示例</span><span class="sxs-lookup"><span data-stu-id="cd8fc-118">Example</span></span>  
 <span data-ttu-id="cd8fc-119">现在已创建并启动跟踪，接下来执行下面的代码以便用活动填充跟踪。</span><span class="sxs-lookup"><span data-stu-id="cd8fc-119">Now that the trace has been created and started, execute the following code to populate the trace with activity.</span></span>  
  
```  
SELECT * FROM master.sys.databases  
GO  
SELECT * FROM ::fn_trace_getinfo(default)  
GO  
  
```  
  
## <a name="example"></a><span data-ttu-id="cd8fc-120">示例</span><span class="sxs-lookup"><span data-stu-id="cd8fc-120">Example</span></span>  
 <span data-ttu-id="cd8fc-121">可以随时停止和重新启动跟踪。</span><span class="sxs-lookup"><span data-stu-id="cd8fc-121">The trace can be stopped and restarted at any time.</span></span> <span data-ttu-id="cd8fc-122">在本示例中，执行下面的代码以停止跟踪、关闭跟踪并删除跟踪定义。</span><span class="sxs-lookup"><span data-stu-id="cd8fc-122">In this example, execute the following code to stop the trace, close the trace, and delete the trace definition.</span></span>  
  
```  
DECLARE @TraceID int  
-- Populate a variable with the trace_id of the current trace  
SELECT  @TraceID = TraceID FROM ::fn_trace_getinfo(default) WHERE VALUE = N'C:\SampleTrace.trc'  
  
-- First stop the trace.   
EXEC sp_trace_setstatus @TraceID, 0  
  
-- Close and then delete its definition from SQL Server.   
EXEC sp_trace_setstatus @TraceID, 2  
  
```  
  
## <a name="example"></a><span data-ttu-id="cd8fc-123">示例</span><span class="sxs-lookup"><span data-stu-id="cd8fc-123">Example</span></span>  
 <span data-ttu-id="cd8fc-124">若要检查跟踪文件，请使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]打开 SampleTrace.trc 文件。</span><span class="sxs-lookup"><span data-stu-id="cd8fc-124">To examine the trace file, open the SampleTrace.trc file using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd8fc-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cd8fc-125">See Also</span></span>  
 <span data-ttu-id="cd8fc-126">[SQL Server Profiler 存储过程 (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cd8fc-126">[SQL Server Profiler Stored Procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql) </span></span>  
 <span data-ttu-id="cd8fc-127">[sp_trace_create (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cd8fc-127">[sp_trace_create &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql) </span></span>  
 <span data-ttu-id="cd8fc-128">[sp_trace_setevent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cd8fc-128">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span></span>  
 [<span data-ttu-id="cd8fc-129">sp_trace_setfilter (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="cd8fc-129">sp_trace_setfilter &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql)  
  
  
