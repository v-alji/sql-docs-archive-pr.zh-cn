---
title: 优化 SQL 跟踪 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- time [SQL Server], traces
- SQL Trace, performance
- traces [SQL Server], performance
- performance [SQL Server], trace
ms.assetid: 50944218-925f-4576-aec8-4379846d7681
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 831875218423bdb9106d7d84995af1e788da44db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578032"
---
# <a name="optimize-sql-trace"></a><span data-ttu-id="a194a-102">优化 SQL 跟踪</span><span class="sxs-lookup"><span data-stu-id="a194a-102">Optimize SQL Trace</span></span>
  <span data-ttu-id="a194a-103">尽管运行 SQL 跟踪会导致性能损失（因为它使用系统资源收集数据），但是您可以通过多种方法将性能损失降到最低。</span><span class="sxs-lookup"><span data-stu-id="a194a-103">Although running SQL Trace incurs a performance cost because it uses system resources to gather data, you can do many things to minimize it.</span></span> <span data-ttu-id="a194a-104">若要将跟踪引起的性能损失降到最低，可以尝试下列解决方法：</span><span class="sxs-lookup"><span data-stu-id="a194a-104">To minimize the performance cost incurred by a trace, try the following:</span></span>  
  
-   <span data-ttu-id="a194a-105">请考虑使用命令提示运行跟踪。</span><span class="sxs-lookup"><span data-stu-id="a194a-105">Consider using the command prompt to run traces.</span></span> <span data-ttu-id="a194a-106">使用图形用户界面会影响性能。</span><span class="sxs-lookup"><span data-stu-id="a194a-106">Using a graphical user interface hinders performance.</span></span> <span data-ttu-id="a194a-107">有关详细信息，请参阅 [sp_trace_create (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a194a-107">For more information, see [sp_trace_create &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql).</span></span>  
  
-   <span data-ttu-id="a194a-108">避免包含频繁发生的事件。</span><span class="sxs-lookup"><span data-stu-id="a194a-108">Avoid including events that occur frequently.</span></span> <span data-ttu-id="a194a-109">如果可能，通过特定事件类和筛选器来缩小跟踪范围。</span><span class="sxs-lookup"><span data-stu-id="a194a-109">If possible, narrow your trace by means of specific event classes and filters.</span></span> <span data-ttu-id="a194a-110">收集的跟踪事件越少，支持跟踪所需的系统资源就越少。</span><span class="sxs-lookup"><span data-stu-id="a194a-110">If fewer trace events are gathered, fewer system resources are required to support tracing.</span></span>  
  
-   <span data-ttu-id="a194a-111">集中跟踪以仅收集提供相关数据的事件。</span><span class="sxs-lookup"><span data-stu-id="a194a-111">Focus the trace to collect only events that provide relevant data.</span></span> <span data-ttu-id="a194a-112">例如，如果您的跟踪用于标识死锁，则包括 **Lock:Deadlock** 事件类，而不包括 **Lock:Acquired** 事件类。</span><span class="sxs-lookup"><span data-stu-id="a194a-112">For example, if your trace is to identify deadlocks, include the **Lock:Deadlock** event class, but not the **Lock:Acquired** event class.</span></span> <span data-ttu-id="a194a-113">如果同时包括这两个事件类，则跟踪将必须响应获取的每个锁，执行成本将加倍。</span><span class="sxs-lookup"><span data-stu-id="a194a-113">If you include both event classes, the trace has to respond to every lock that is acquired, and your execution cost is doubled.</span></span>  
  
-   <span data-ttu-id="a194a-114">避免收集重复数据。</span><span class="sxs-lookup"><span data-stu-id="a194a-114">Avoid collecting duplicate data.</span></span> <span data-ttu-id="a194a-115">例如，如果收集 **SQL:BatchStarted** 和 **SQL:BatchCompleted**，则可以通过仅收集 **SQL:BatchStarted** 事件类的文本数据来最小化结果集的大小。</span><span class="sxs-lookup"><span data-stu-id="a194a-115">For example, if you collect **SQL:BatchStarted** and the **SQL:BatchCompleted**, you can minimize the size of the results set by collecting text data for the **SQL:BatchStarted** event class only.</span></span>  
  
-   <span data-ttu-id="a194a-116">在跟踪定义中使用筛选器。</span><span class="sxs-lookup"><span data-stu-id="a194a-116">Use filters in the trace definition.</span></span> <span data-ttu-id="a194a-117">例如，如果您知道某个用户在即席查询期间报告较慢性能，则对 **LoginName**创建筛选器。</span><span class="sxs-lookup"><span data-stu-id="a194a-117">For example, if you know that a certain user is reporting slow performance during ad hoc queries, create a filter on **LoginName**.</span></span> <span data-ttu-id="a194a-118">将筛选器设置为仅包含 **LoginName** 与该用户名匹配的事件。</span><span class="sxs-lookup"><span data-stu-id="a194a-118">Set the filter to include only events where the **LoginName** matches that user name.</span></span>  
  
 <span data-ttu-id="a194a-119">如果需要跟踪对性能产生极大影响的事件，请考虑使用下列一种方法来限制对服务器性能的影响：</span><span class="sxs-lookup"><span data-stu-id="a194a-119">If you need to run a trace for events that create a significant impact on performance, consider limiting the performance impact on the server by using one of the following methods:</span></span>  
  
-   <span data-ttu-id="a194a-120">短时间运行跟踪。</span><span class="sxs-lookup"><span data-stu-id="a194a-120">Run traces for shorter periods of time.</span></span> <span data-ttu-id="a194a-121">您可以通过启用停止时间来控制跟踪运行的时间长度。</span><span class="sxs-lookup"><span data-stu-id="a194a-121">You can control the length of time that a trace runs by enabling a stop time.</span></span> <span data-ttu-id="a194a-122">这在您无法限制事件类或筛选事件的情况下非常重要。</span><span class="sxs-lookup"><span data-stu-id="a194a-122">This is especially important if you cannot limit the event classes or filter an event.</span></span> <span data-ttu-id="a194a-123">启用停止时间可以确保性能不会无限期地受到影响。</span><span class="sxs-lookup"><span data-stu-id="a194a-123">Enabling a stop time ensures that the performance incurred does not last indefinitely.</span></span>  
  
-   <span data-ttu-id="a194a-124">限制跟踪结果的大小。</span><span class="sxs-lookup"><span data-stu-id="a194a-124">Limit the size of the trace results.</span></span> <span data-ttu-id="a194a-125">您可以将跟踪结果的大小限制为最大文件大小。</span><span class="sxs-lookup"><span data-stu-id="a194a-125">You can limit the size of the trace results to a maximum file size.</span></span> <span data-ttu-id="a194a-126">此策略可以确保在达到文件大小限制时停止性能损失（如果未启用文件滚动更新）。</span><span class="sxs-lookup"><span data-stu-id="a194a-126">This strategy ensures that the performance cost stops when the file-size limit is reached (if file rollover is not enabled).</span></span>  
  
-   <span data-ttu-id="a194a-127">限制返回的事件数。</span><span class="sxs-lookup"><span data-stu-id="a194a-127">Limit the number of events returned.</span></span> <span data-ttu-id="a194a-128">使用 [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] ，可以通过将跟踪保存到表并设置最大行数来限制返回的事件数。</span><span class="sxs-lookup"><span data-stu-id="a194a-128">With [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] you can limit the number of events returned by saving the trace to a table and setting the maximum number of rows.</span></span> <span data-ttu-id="a194a-129">达到最大行数后，跟踪结果仍会返回到 [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] 屏幕，但不再有将结果记录到表的开销。</span><span class="sxs-lookup"><span data-stu-id="a194a-129">Trace results are still returned to the [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] screen after the maximum number of rows has been reached, but the cost of recording the results to a table is eliminated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a194a-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a194a-130">See Also</span></span>  
 [<span data-ttu-id="a194a-131">筛选跟踪</span><span class="sxs-lookup"><span data-stu-id="a194a-131">Filter a Trace</span></span>](../sql-trace/filter-a-trace.md)  
  
  
