---
title: 使用存储过程创建手动跟踪 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: f6f47fa2-7c17-41d4-9f69-9be144d56832
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e2840dced22ccdba8fe71cc87c05d7fd6fb4be58
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587747"
---
# <a name="create-manual-traces-using-stored-procedures"></a><span data-ttu-id="ab990-102">使用存储过程创建手动跟踪</span><span class="sxs-lookup"><span data-stu-id="ab990-102">Create Manual Traces using Stored Procedures</span></span>
  <span data-ttu-id="ab990-103">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 提供 [!INCLUDE[tsql](../../includes/tsql-md.md)] 系统存储过程来创建对 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]实例的跟踪。</span><span class="sxs-lookup"><span data-stu-id="ab990-103">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides [!INCLUDE[tsql](../../includes/tsql-md.md)] system stored procedures to create traces on an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span> <span data-ttu-id="ab990-104">可以不使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]，而使用这些系统存储过程从您自己的应用程序中手动创建跟踪。</span><span class="sxs-lookup"><span data-stu-id="ab990-104">These system stored procedures can be used from within your own applications to create traces manually, instead of using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="ab990-105">这样，您就可以针对企业的特定需求编写自定义应用程序。</span><span class="sxs-lookup"><span data-stu-id="ab990-105">This allows you to write custom applications specific to the needs of your enterprise.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ab990-106">本节内容</span><span class="sxs-lookup"><span data-stu-id="ab990-106">In This Section</span></span>  
 <span data-ttu-id="ab990-107">下表列出了用于跟踪 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]实例的系统存储过程。</span><span class="sxs-lookup"><span data-stu-id="ab990-107">The following table lists the system stored procedures for tracing an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
|<span data-ttu-id="ab990-108">存储过程</span><span class="sxs-lookup"><span data-stu-id="ab990-108">Stored procedure</span></span>|<span data-ttu-id="ab990-109">执行的任务</span><span class="sxs-lookup"><span data-stu-id="ab990-109">Task performed</span></span>|  
|----------------------|--------------------|  
|[<span data-ttu-id="ab990-110">sys.fn_trace_geteventinfo (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ab990-110">sys.fn_trace_geteventinfo &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/sys-fn-trace-geteventinfo-transact-sql)|<span data-ttu-id="ab990-111">返回跟踪中包含的事件的相关信息。</span><span class="sxs-lookup"><span data-stu-id="ab990-111">Returns information about events included in a trace.</span></span>|  
|[<span data-ttu-id="ab990-112">sys.fn_trace_getinfo (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ab990-112">sys.fn_trace_getinfo &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql)|<span data-ttu-id="ab990-113">返回有关指定跟踪或所有现有跟踪的信息。</span><span class="sxs-lookup"><span data-stu-id="ab990-113">Returns information about a specified trace or all existing traces.</span></span>|  
|[<span data-ttu-id="ab990-114">sp_trace_create (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ab990-114">sp_trace_create &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql)|<span data-ttu-id="ab990-115">创建跟踪定义。</span><span class="sxs-lookup"><span data-stu-id="ab990-115">Creates a trace definition.</span></span> <span data-ttu-id="ab990-116">新的跟踪将处于停止状态。</span><span class="sxs-lookup"><span data-stu-id="ab990-116">The new trace will be in a stopped state.</span></span>|  
|[<span data-ttu-id="ab990-117">sp_trace_generateevent (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ab990-117">sp_trace_generateevent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql)|<span data-ttu-id="ab990-118">创建用户定义事件。</span><span class="sxs-lookup"><span data-stu-id="ab990-118">Creates a user-defined event.</span></span>|  
|[<span data-ttu-id="ab990-119">sp_trace_setevent (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ab990-119">sp_trace_setevent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)|<span data-ttu-id="ab990-120">将事件类或数据列添加到跟踪，或从跟踪中删除事件类或数据列。</span><span class="sxs-lookup"><span data-stu-id="ab990-120">Adds an event class or data column to a trace, or removes one from it.</span></span>|  
|[<span data-ttu-id="ab990-121">sp_trace_setstatus (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ab990-121">sp_trace_setstatus &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql)|<span data-ttu-id="ab990-122">启动、停止或关闭跟踪。</span><span class="sxs-lookup"><span data-stu-id="ab990-122">Starts, stops, or closes a trace.</span></span>|  
|[<span data-ttu-id="ab990-123">sys.fn_trace_getfilterinfo (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ab990-123">sys.fn_trace_getfilterinfo &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql)|<span data-ttu-id="ab990-124">返回有关应用于跟踪的筛选器的信息。</span><span class="sxs-lookup"><span data-stu-id="ab990-124">Returns information about filters applied to a trace.</span></span>|  
|[<span data-ttu-id="ab990-125">sp_trace_setfilter (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ab990-125">sp_trace_setfilter &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql)|<span data-ttu-id="ab990-126">将新的或已修改的筛选器应用于跟踪。</span><span class="sxs-lookup"><span data-stu-id="ab990-126">Applies a new or modified filter to a trace.</span></span>|  
  
 <span data-ttu-id="ab990-127">**使用存储过程定义自己的跟踪**</span><span class="sxs-lookup"><span data-stu-id="ab990-127">**To define your own trace using stored procedures**</span></span>  
  
1.  <span data-ttu-id="ab990-128">使用 **sp_trace_setevent**指定要捕获的事件。</span><span class="sxs-lookup"><span data-stu-id="ab990-128">Specify the events to capture using **sp_trace_setevent**.</span></span>  
  
2.  <span data-ttu-id="ab990-129">指定任何事件筛选器。</span><span class="sxs-lookup"><span data-stu-id="ab990-129">Specify any event filters.</span></span> <span data-ttu-id="ab990-130">有关详细信息，请参阅[设置跟踪筛选器 (Transact SQL)](../../ssms/agent/set-sql-server-alias-for-sql-server-agent-service-ssms.md)。</span><span class="sxs-lookup"><span data-stu-id="ab990-130">For more information, see [Set a Trace Filter &#40;Transact-SQL&#41;](../../ssms/agent/set-sql-server-alias-for-sql-server-agent-service-ssms.md).</span></span>  
  
3.  <span data-ttu-id="ab990-131">使用 **sp_trace_create** 为捕获的事件数据指定目的。</span><span class="sxs-lookup"><span data-stu-id="ab990-131">Specify the destination for the captured event data using **sp_trace_create**.</span></span>  
  
 <span data-ttu-id="ab990-132">有关使用跟踪存储过程的示例，请参阅[创建跟踪 (Transact-SQL)](../sql-trace/create-a-trace-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="ab990-132">For an example of using trace stored procedures, see [Create a Trace &#40;Transact-SQL&#41;](../sql-trace/create-a-trace-transact-sql.md).</span></span>  
  
 <span data-ttu-id="ab990-133">**设置跟踪定义默认值**</span><span class="sxs-lookup"><span data-stu-id="ab990-133">**To set trace definition defaults**</span></span>  
  
 [<span data-ttu-id="ab990-134">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="ab990-134">SQL Server Profiler</span></span>](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
 <span data-ttu-id="ab990-135">**设置跟踪显示默认值**</span><span class="sxs-lookup"><span data-stu-id="ab990-135">**To set trace display defaults**</span></span>  
  
 [<span data-ttu-id="ab990-136">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="ab990-136">SQL Server Profiler</span></span>](../../tools/sql-server-profiler/set-trace-display-defaults-sql-server-profiler.md)  
  
 <span data-ttu-id="ab990-137">**创建跟踪**</span><span class="sxs-lookup"><span data-stu-id="ab990-137">**To create a trace**</span></span>  
  
 [<span data-ttu-id="ab990-138">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="ab990-138">SQL Server Profiler</span></span>](../../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)  
  
 [<span data-ttu-id="ab990-139">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ab990-139">Transact-SQL</span></span>](../sql-trace/create-a-trace-transact-sql.md)  
  
 <span data-ttu-id="ab990-140">**向跟踪模板添加或从中删除事件**</span><span class="sxs-lookup"><span data-stu-id="ab990-140">**To add or remove events from a trace template**</span></span>  
  
 [<span data-ttu-id="ab990-141">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="ab990-141">SQL Server Profiler</span></span>](../../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)  
  
 [<span data-ttu-id="ab990-142">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ab990-142">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
