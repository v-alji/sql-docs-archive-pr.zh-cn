---
title: SQL Server Profiler 分析死锁 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- process nodes [SQL Server Profiler]
- Profiler [SQL Server Profiler], deadlocks
- deadlocks [SQL Server], identifying cause
- resource nodes [SQL Server Profiler]
- graphs [SQL Server Profiler]
- SQL Server Profiler, deadlocks
- events [SQL Server], deadlocks
- edges [SQL Server Profiler]
ms.assetid: 72d6718f-501b-4ea6-b344-c0e653f19561
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3414cda74d75dbacf10ed98b6fc6d50da2feaa18
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682517"
---
# <a name="analyze-deadlocks-with-sql-server-profiler"></a><span data-ttu-id="9c1f4-102">使用 SQL Server Profiler 分析死锁</span><span class="sxs-lookup"><span data-stu-id="9c1f4-102">Analyze Deadlocks with SQL Server Profiler</span></span>
  <span data-ttu-id="9c1f4-103">使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 确定死锁的原因。</span><span class="sxs-lookup"><span data-stu-id="9c1f4-103">Use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to identify the cause of a deadlock.</span></span> <span data-ttu-id="9c1f4-104">当 SQL Server 中某组资源的两个或多个线程或进程之间存在循环的依赖关系时，将会发生死锁。</span><span class="sxs-lookup"><span data-stu-id="9c1f4-104">A deadlock occurs when there is a cyclic dependency between two or more threads, or processes, for some set of resources within SQL Server.</span></span> <span data-ttu-id="9c1f4-105">使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]，可以创建记录、重播和显示死锁事件的跟踪以进行分析。</span><span class="sxs-lookup"><span data-stu-id="9c1f4-105">Using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], you can create a trace that records, replays, and displays deadlock events for analysis.</span></span>  
  
 <span data-ttu-id="9c1f4-106">若要跟踪死锁事件，请将 **Deadlock graph** 事件类添加到跟踪。</span><span class="sxs-lookup"><span data-stu-id="9c1f4-106">To trace deadlock events, add the **Deadlock graph** event class to a trace.</span></span> <span data-ttu-id="9c1f4-107">此事件类会在跟踪中的 **TextData** 数据列中填充有关死锁中涉及的进程和对象的 XML 数据。</span><span class="sxs-lookup"><span data-stu-id="9c1f4-107">This event class populates the **TextData** data column in the trace with XML data about the process and objects that are involved in the deadlock.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="9c1f4-108">可将 XML 文档提取到死锁 XML (.xdl) 文件，你稍后可在 SQL Server Management Studio 中查看该文件。</span><span class="sxs-lookup"><span data-stu-id="9c1f4-108">can extract the XML document to a deadlock XML (.xdl) file which you can view later in SQL Server Management Studio.</span></span> <span data-ttu-id="9c1f4-109">您可以配置 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] ，将 **Deadlock graph** 事件提取到一个包含了所有 **Deadlock graph** 事件的文件中，或提取到多个单独的文件中。</span><span class="sxs-lookup"><span data-stu-id="9c1f4-109">You can configure [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to extract **Deadlock graph** events to a single file that contains all **Deadlock graph** events, or to separate files.</span></span> <span data-ttu-id="9c1f4-110">可以通过下列任一方法进行提取：</span><span class="sxs-lookup"><span data-stu-id="9c1f4-110">This extraction can be done in any of the following ways:</span></span>  
  
-   <span data-ttu-id="9c1f4-111">在配置跟踪时，使用 **“事件提取设置”** 选项卡。请注意，只有在 **“事件选择”** 选项卡上选择了 **Deadlock graph** 事件，才会出现此选项卡。</span><span class="sxs-lookup"><span data-stu-id="9c1f4-111">At trace configuration time, using the **Events Extraction Settings** tab. Note that this tab does not appear until you select the **Deadlock graph** event on the **Events Selection** tab.</span></span>  
  
-   <span data-ttu-id="9c1f4-112">使用 **“文件”** 菜单上的 **“提取 SQL Server 事件”** 选项。</span><span class="sxs-lookup"><span data-stu-id="9c1f4-112">Using the **Extract SQL Server Events** option on the **File** menu.</span></span>  
  
-   <span data-ttu-id="9c1f4-113">通过右键单击特定事件并选择“提取事件数据”  ，也可以提取并保存各个事件。</span><span class="sxs-lookup"><span data-stu-id="9c1f4-113">Individual events can also be extracted and saved by right-clicking a specific event and choosing **Extract Event Data**.</span></span>  
  
## <a name="deadlock-graphs"></a><span data-ttu-id="9c1f4-114">死锁图形</span><span class="sxs-lookup"><span data-stu-id="9c1f4-114">Deadlock Graphs</span></span>  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="9c1f4-115">和 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 使用死锁等待图形描述死锁。</span><span class="sxs-lookup"><span data-stu-id="9c1f4-115">and [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] use a deadlock wait-for graph to describe a deadlock.</span></span> <span data-ttu-id="9c1f4-116">此死锁等待图形中包含进程节点、资源节点以及表示进程和资源之间关系的边。</span><span class="sxs-lookup"><span data-stu-id="9c1f4-116">The deadlock wait-for graph contains process nodes, resource nodes, and edges representing the relationships between the processes and the resources.</span></span> <span data-ttu-id="9c1f4-117">等待图形的组件的定义如下表所示：</span><span class="sxs-lookup"><span data-stu-id="9c1f4-117">The components of wait-for graphs are defined in the following table:</span></span>  
  
 <span data-ttu-id="9c1f4-118">进程节点</span><span class="sxs-lookup"><span data-stu-id="9c1f4-118">Process node</span></span>  
 <span data-ttu-id="9c1f4-119">执行任务的线程。例如，INSERT、UPDATE 或 DELETE。</span><span class="sxs-lookup"><span data-stu-id="9c1f4-119">A thread that performs a task; for example, INSERT, UPDATE, or DELETE.</span></span>  
  
 <span data-ttu-id="9c1f4-120">资源节点</span><span class="sxs-lookup"><span data-stu-id="9c1f4-120">Resource node</span></span>  
 <span data-ttu-id="9c1f4-121">数据库对象。例如，表、索引或行。</span><span class="sxs-lookup"><span data-stu-id="9c1f4-121">A database object; for example, a table, index, or row.</span></span>  
  
 <span data-ttu-id="9c1f4-122">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="9c1f4-122">Edge</span></span>  
 <span data-ttu-id="9c1f4-123">进程和资源之间的关系。</span><span class="sxs-lookup"><span data-stu-id="9c1f4-123">A relationship between a process and a resource.</span></span> <span data-ttu-id="9c1f4-124">当进程等待资源时，将出现 `request` 边。</span><span class="sxs-lookup"><span data-stu-id="9c1f4-124">A `request` edge occurs when a process waits for a resource.</span></span> <span data-ttu-id="9c1f4-125">当资源等待进程时，将出现 `owner` 边。</span><span class="sxs-lookup"><span data-stu-id="9c1f4-125">An `owner` edge occurs when a resource waits for a process.</span></span> <span data-ttu-id="9c1f4-126">边说明中包括了锁模式。</span><span class="sxs-lookup"><span data-stu-id="9c1f4-126">The lock mode is included in the edge description.</span></span> <span data-ttu-id="9c1f4-127">例如，模式：  X。</span><span class="sxs-lookup"><span data-stu-id="9c1f4-127">For example, **Mode: X**.</span></span>  
  
## <a name="deadlock-process-node"></a><span data-ttu-id="9c1f4-128">死锁进程节点</span><span class="sxs-lookup"><span data-stu-id="9c1f4-128">Deadlock Process Node</span></span>  
 <span data-ttu-id="9c1f4-129">在等待图形中，进程节点包含有关进程的信息。</span><span class="sxs-lookup"><span data-stu-id="9c1f4-129">In a wait-for graph, the process node contains information about the process.</span></span> <span data-ttu-id="9c1f4-130">下表介绍了进程的组件。</span><span class="sxs-lookup"><span data-stu-id="9c1f4-130">The following table explains the components of a process.</span></span>  
  
|<span data-ttu-id="9c1f4-131">组件</span><span class="sxs-lookup"><span data-stu-id="9c1f4-131">Component</span></span>|<span data-ttu-id="9c1f4-132">定义</span><span class="sxs-lookup"><span data-stu-id="9c1f4-132">Definition</span></span>|  
|---------------|----------------|  
|<span data-ttu-id="9c1f4-133">服务器进程 ID</span><span class="sxs-lookup"><span data-stu-id="9c1f4-133">Server process Id</span></span>|<span data-ttu-id="9c1f4-134">服务器进程标识符 (SPID)，即服务器给拥有锁的进程分配的标识符。</span><span class="sxs-lookup"><span data-stu-id="9c1f4-134">Server process identifier (SPID), a server assigned identifier for the process owning the lock.</span></span>|  
|<span data-ttu-id="9c1f4-135">服务器批 ID</span><span class="sxs-lookup"><span data-stu-id="9c1f4-135">Server batch Id</span></span>|<span data-ttu-id="9c1f4-136">服务器批标识符 (SBID)。</span><span class="sxs-lookup"><span data-stu-id="9c1f4-136">Server batch identifier (SBID).</span></span>|  
|<span data-ttu-id="9c1f4-137">执行上下文 ID</span><span class="sxs-lookup"><span data-stu-id="9c1f4-137">Execution context Id</span></span>|<span data-ttu-id="9c1f4-138">执行上下文标识符 (ECID)。</span><span class="sxs-lookup"><span data-stu-id="9c1f4-138">Execution context identifier (ECID).</span></span> <span data-ttu-id="9c1f4-139">与指定 SPID 相关联的给定线程的执行上下文 ID。</span><span class="sxs-lookup"><span data-stu-id="9c1f4-139">The execution context ID of a given thread associated with a specific SPID.</span></span><br /><br /> <span data-ttu-id="9c1f4-140">ECID = {0, 1, 2, 3, *...n*}，其中 0 始终表示主或父线程，并且 {1, 2, 3, *...n*} 表示子线程。</span><span class="sxs-lookup"><span data-stu-id="9c1f4-140">ECID = {0,1,2,3, *...n*}, where 0 always represents the main or parent thread, and {1,2,3, *...n*} represent the subthreads.</span></span>|  
|<span data-ttu-id="9c1f4-141">死锁优先级</span><span class="sxs-lookup"><span data-stu-id="9c1f4-141">Deadlock priority</span></span>|<span data-ttu-id="9c1f4-142">进程的死锁优先级</span><span class="sxs-lookup"><span data-stu-id="9c1f4-142">Deadlock priority for the process.</span></span> <span data-ttu-id="9c1f4-143">有关可能值的详细信息，请参阅 [SET DEADLOCK_PRIORITY (Transact-SQL)](/sql/t-sql/statements/set-deadlock-priority-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="9c1f4-143">For more information about possible values, see [SET DEADLOCK_PRIORITY &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-deadlock-priority-transact-sql).</span></span>|  
|<span data-ttu-id="9c1f4-144">已用日志</span><span class="sxs-lookup"><span data-stu-id="9c1f4-144">Log Used</span></span>|<span data-ttu-id="9c1f4-145">进程所使用的日志空间量。</span><span class="sxs-lookup"><span data-stu-id="9c1f4-145">Amount of log space used by the process.</span></span>|  
|<span data-ttu-id="9c1f4-146">所有者 ID</span><span class="sxs-lookup"><span data-stu-id="9c1f4-146">Owner Id</span></span>|<span data-ttu-id="9c1f4-147">正在使用事务并且当前正在等待锁的进程的事务 ID。</span><span class="sxs-lookup"><span data-stu-id="9c1f4-147">Transaction ID for the processes which are using transactions and currently waiting on a lock.</span></span>|  
|<span data-ttu-id="9c1f4-148">事务描述符</span><span class="sxs-lookup"><span data-stu-id="9c1f4-148">Transaction descriptor</span></span>|<span data-ttu-id="9c1f4-149">指向描述事务状态的事务描述符的指针。</span><span class="sxs-lookup"><span data-stu-id="9c1f4-149">Pointer to the transaction descriptor that describes the state of the transaction.</span></span>|  
|<span data-ttu-id="9c1f4-150">输入缓冲区</span><span class="sxs-lookup"><span data-stu-id="9c1f4-150">Input buffer</span></span>|<span data-ttu-id="9c1f4-151">当前进程的输入缓冲区。定义了事件的类型和正在执行的语句。</span><span class="sxs-lookup"><span data-stu-id="9c1f4-151">Input buffer of the current process, defines the type of event and the statement being executed.</span></span> <span data-ttu-id="9c1f4-152">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="9c1f4-152">Possible values include:</span></span><br /><br /> <span data-ttu-id="9c1f4-153">**语言**</span><span class="sxs-lookup"><span data-stu-id="9c1f4-153">**Language**</span></span><br /><br /> <span data-ttu-id="9c1f4-154">**RPC**</span><span class="sxs-lookup"><span data-stu-id="9c1f4-154">**RPC**</span></span><br /><br /> <span data-ttu-id="9c1f4-155">无 </span><span class="sxs-lookup"><span data-stu-id="9c1f4-155">**None**</span></span>|  
|<span data-ttu-id="9c1f4-156">语句</span><span class="sxs-lookup"><span data-stu-id="9c1f4-156">Statement</span></span>|<span data-ttu-id="9c1f4-157">语句类型。</span><span class="sxs-lookup"><span data-stu-id="9c1f4-157">Type of statement.</span></span> <span data-ttu-id="9c1f4-158">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="9c1f4-158">Possible values are:</span></span><br /><br /> <span data-ttu-id="9c1f4-159">**NOP**</span><span class="sxs-lookup"><span data-stu-id="9c1f4-159">**NOP**</span></span><br /><br /> <span data-ttu-id="9c1f4-160">**SELECT**</span><span class="sxs-lookup"><span data-stu-id="9c1f4-160">**SELECT**</span></span><br /><br /> <span data-ttu-id="9c1f4-161">**UPDATE**</span><span class="sxs-lookup"><span data-stu-id="9c1f4-161">**UPDATE**</span></span><br /><br /> <span data-ttu-id="9c1f4-162">**INSERT**</span><span class="sxs-lookup"><span data-stu-id="9c1f4-162">**INSERT**</span></span><br /><br /> <span data-ttu-id="9c1f4-163">**DELETE**</span><span class="sxs-lookup"><span data-stu-id="9c1f4-163">**DELETE**</span></span><br /><br /> <span data-ttu-id="9c1f4-164">**Unknown**</span><span class="sxs-lookup"><span data-stu-id="9c1f4-164">**Unknown**</span></span>|  
  
## <a name="deadlock-resource-node"></a><span data-ttu-id="9c1f4-165">死锁资源节点</span><span class="sxs-lookup"><span data-stu-id="9c1f4-165">Deadlock Resource Node</span></span>  
 <span data-ttu-id="9c1f4-166">在死锁中，两个进程都在等待对方占用的资源。</span><span class="sxs-lookup"><span data-stu-id="9c1f4-166">In a deadlock, two processes are each waiting for a resource held by the other process.</span></span> <span data-ttu-id="9c1f4-167">在死锁图形中，资源显示为资源节点。</span><span class="sxs-lookup"><span data-stu-id="9c1f4-167">In a deadlock graph, the resources are displayed as resource nodes.</span></span>  
  
  
