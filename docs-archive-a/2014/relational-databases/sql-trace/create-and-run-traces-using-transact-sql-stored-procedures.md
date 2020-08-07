---
title: 使用 Transact-SQL 存储过程创建和运行跟踪 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 80347417-338d-4bea-8885-91fae5181cfe
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2905ce2822598502ef6337d1a083fb6fde001c2d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587749"
---
# <a name="create-and-run-traces-using-transact-sql-stored-procedures"></a><span data-ttu-id="11bc4-102">使用 Transact-SQL 存储过程创建和运行跟踪</span><span class="sxs-lookup"><span data-stu-id="11bc4-102">Create and Run Traces Using Transact-SQL Stored Procedures</span></span>
  <span data-ttu-id="11bc4-103">根据使用的是 Microsoft [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 还是系统存储过程来创建和运行跟踪，用 SQL 跟踪进行跟踪的过程会有所不同。</span><span class="sxs-lookup"><span data-stu-id="11bc4-103">The process of tracing with SQL Trace varies depending on whether you create and run your trace by using Microsoft [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] or by using system stored procedures.</span></span>  
  
 <span data-ttu-id="11bc4-104">除了 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]，还可以使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 系统存储过程来创建和运行跟踪。</span><span class="sxs-lookup"><span data-stu-id="11bc4-104">As an alternative to [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], you can use [!INCLUDE[tsql](../../includes/tsql-md.md)] system stored procedures to create and run traces.</span></span> <span data-ttu-id="11bc4-105">通过系统存储过程进行跟踪的过程如下：</span><span class="sxs-lookup"><span data-stu-id="11bc4-105">The process of tracing by using system stored procedures is as follows:</span></span>  
  
1.  <span data-ttu-id="11bc4-106">使用 **sp_trace_create**创建跟踪。</span><span class="sxs-lookup"><span data-stu-id="11bc4-106">Create a trace by using **sp_trace_create**.</span></span>  
  
2.  <span data-ttu-id="11bc4-107">使用 **sp_trace_setevent**添加事件。</span><span class="sxs-lookup"><span data-stu-id="11bc4-107">Add events with **sp_trace_setevent**.</span></span>  
  
3.  <span data-ttu-id="11bc4-108">（可选）使用 **sp_trace_setfilter**设置筛选器。</span><span class="sxs-lookup"><span data-stu-id="11bc4-108">(Optional) Set a filter with **sp_trace_setfilter**.</span></span>  
  
4.  <span data-ttu-id="11bc4-109">使用 **sp_trace_setstatus**启动跟踪。</span><span class="sxs-lookup"><span data-stu-id="11bc4-109">Start the trace with **sp_trace_setstatus**.</span></span>  
  
5.  <span data-ttu-id="11bc4-110">使用 **sp_trace_setstatus**停止跟踪。</span><span class="sxs-lookup"><span data-stu-id="11bc4-110">Stop the trace with **sp_trace_setstatus**.</span></span>  
  
6.  <span data-ttu-id="11bc4-111">使用 **sp_trace_setstatus**关闭跟踪。</span><span class="sxs-lookup"><span data-stu-id="11bc4-111">Close the trace with **sp_trace_setstatus**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="11bc4-112">使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 系统存储过程创建服务器端跟踪，这可以保证只要磁盘上有空间且不出现写入错误，就不会丢失任何事件。</span><span class="sxs-lookup"><span data-stu-id="11bc4-112">Using [!INCLUDE[tsql](../../includes/tsql-md.md)] system stored procedures creates a server-side trace, which guarantees that no events will be lost as long as there is space on the disk and no write errors occur.</span></span> <span data-ttu-id="11bc4-113">如果磁盘已满或发生故障， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例会继续运行，但跟踪将停止。</span><span class="sxs-lookup"><span data-stu-id="11bc4-113">If the disk becomes full or the disk fails, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance continues to run, but tracing stops.</span></span> <span data-ttu-id="11bc4-114">如果设置了 **c2 audit mode** 且出现写入错误，跟踪将停止且 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例关闭。</span><span class="sxs-lookup"><span data-stu-id="11bc4-114">If the **c2 audit mode** is set, and there is a write failure, tracing stops and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance shuts down.</span></span> <span data-ttu-id="11bc4-115">有关 **c2 audit mode** 设置的详细信息，请参阅 [c2 audit mode 服务器配置选项](../../database-engine/configure-windows/c2-audit-mode-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="11bc4-115">For more information about the **c2 audit mode** setting, see [c2 audit mode Server Configuration Option](../../database-engine/configure-windows/c2-audit-mode-server-configuration-option.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="11bc4-116">本节内容</span><span class="sxs-lookup"><span data-stu-id="11bc4-116">In This Section</span></span>  
  
|<span data-ttu-id="11bc4-117">主题</span><span class="sxs-lookup"><span data-stu-id="11bc4-117">Topic</span></span>|<span data-ttu-id="11bc4-118">说明</span><span class="sxs-lookup"><span data-stu-id="11bc4-118">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="11bc4-119">优化 SQL 跟踪</span><span class="sxs-lookup"><span data-stu-id="11bc4-119">Optimize SQL Trace</span></span>](sql-trace.md)|<span data-ttu-id="11bc4-120">说明如何降低跟踪对系统性能的影响。</span><span class="sxs-lookup"><span data-stu-id="11bc4-120">Contains information about ways you can reduce the effects of tracing on system performance.</span></span>|  
|[<span data-ttu-id="11bc4-121">筛选跟踪</span><span class="sxs-lookup"><span data-stu-id="11bc4-121">Filter a Trace</span></span>](filter-a-trace.md)|<span data-ttu-id="11bc4-122">介绍使用筛选器进行跟踪。</span><span class="sxs-lookup"><span data-stu-id="11bc4-122">Contains information about using filters for tracing.</span></span>|  
|[<span data-ttu-id="11bc4-123">限制跟踪文件和表的大小</span><span class="sxs-lookup"><span data-stu-id="11bc4-123">Limit Trace File and Table Sizes</span></span>](limit-trace-file-and-table-sizes.md)|<span data-ttu-id="11bc4-124">说明如何限制写入跟踪数据的文件和表的大小。</span><span class="sxs-lookup"><span data-stu-id="11bc4-124">Contains information about how to limit the size of files and tables where trace data is written.</span></span> <span data-ttu-id="11bc4-125">请注意，只有 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 可以将跟踪信息写入表。</span><span class="sxs-lookup"><span data-stu-id="11bc4-125">Note that only [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] can write trace information to tables.</span></span>|  
|[<span data-ttu-id="11bc4-126">安排跟踪</span><span class="sxs-lookup"><span data-stu-id="11bc4-126">Schedule Traces</span></span>](schedule-traces.md)|<span data-ttu-id="11bc4-127">说明如何设置跟踪的开始时间和结束时间。</span><span class="sxs-lookup"><span data-stu-id="11bc4-127">Contains information about how to set the start time and the end time for tracing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="11bc4-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="11bc4-128">See Also</span></span>  
 <span data-ttu-id="11bc4-129">[sp_trace_create (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="11bc4-129">[sp_trace_create &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql) </span></span>  
 <span data-ttu-id="11bc4-130">[sp_trace_setevent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="11bc4-130">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span></span>  
 <span data-ttu-id="11bc4-131">[sp_trace_setfilter (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="11bc4-131">[sp_trace_setfilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql) </span></span>  
 [<span data-ttu-id="11bc4-132">sp_trace_setstatus (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="11bc4-132">sp_trace_setstatus &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql)  
  
  
