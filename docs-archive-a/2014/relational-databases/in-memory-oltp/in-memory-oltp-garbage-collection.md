---
title: 内存中 OLTP 垃圾回收 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 940140a7-4785-46fc-8bf4-151435dccd3c
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 23997d3664fb48902d2be08bbb22d2189c832298
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692939"
---
# <a name="in-memory-oltp-garbage-collection"></a><span data-ttu-id="a8120-102">内存中 OLTP 垃圾回收</span><span class="sxs-lookup"><span data-stu-id="a8120-102">In-Memory OLTP Garbage Collection</span></span>
  <span data-ttu-id="a8120-103">如果数据行已被一个不再活动的事务删除，则该数据行被视为是陈旧的。</span><span class="sxs-lookup"><span data-stu-id="a8120-103">A data row is considered stale if it was deleted by a transaction that is no longer active.</span></span> <span data-ttu-id="a8120-104">可对陈旧的行进行垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="a8120-104">A stale row is eligible for garbage collection.</span></span> <span data-ttu-id="a8120-105">下面是 [!INCLUDE[hek_2](../../includes/hek-2-md.md)]中垃圾收集的特征：</span><span class="sxs-lookup"><span data-stu-id="a8120-105">The following are characteristics of garbage collection in [!INCLUDE[hek_2](../../includes/hek-2-md.md)]:</span></span>  
  
-   <span data-ttu-id="a8120-106">不产生阻塞。</span><span class="sxs-lookup"><span data-stu-id="a8120-106">Non-blocking.</span></span> <span data-ttu-id="a8120-107">垃圾收集随着时间推移进行分布，对工作负荷的影响极小。</span><span class="sxs-lookup"><span data-stu-id="a8120-107">Garbage collection is distributed over time with minimal impact on the workload.</span></span>  
  
-   <span data-ttu-id="a8120-108">协作。</span><span class="sxs-lookup"><span data-stu-id="a8120-108">Cooperative.</span></span> <span data-ttu-id="a8120-109">用户事务通过主垃圾收集线程参与垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="a8120-109">User transactions participate in garbage collection with main garbage-collection thread.</span></span>  
  
-   <span data-ttu-id="a8120-110">高效。</span><span class="sxs-lookup"><span data-stu-id="a8120-110">Efficient.</span></span> <span data-ttu-id="a8120-111">用户事务将所使用的访问路径（索引）中的陈旧行解除链接。</span><span class="sxs-lookup"><span data-stu-id="a8120-111">User transactions delink stale rows in the access path (the index) being used.</span></span> <span data-ttu-id="a8120-112">这样会减少最终删除行时所需的工作。</span><span class="sxs-lookup"><span data-stu-id="a8120-112">This reduces the work required when the row is finally removed.</span></span>  
  
-   <span data-ttu-id="a8120-113">快速响应。</span><span class="sxs-lookup"><span data-stu-id="a8120-113">Responsive.</span></span> <span data-ttu-id="a8120-114">内存压力会导致频繁垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="a8120-114">Memory pressure leads to aggressive garbage collection.</span></span>  
  
-   <span data-ttu-id="a8120-115">可缩放。</span><span class="sxs-lookup"><span data-stu-id="a8120-115">Scalable.</span></span> <span data-ttu-id="a8120-116">提交后，用户事务执行部分垃圾收集工作。</span><span class="sxs-lookup"><span data-stu-id="a8120-116">After commit, user transactions do part of the work of garbage collection.</span></span> <span data-ttu-id="a8120-117">事务活动越多，解除链接的陈旧行就越多。</span><span class="sxs-lookup"><span data-stu-id="a8120-117">The more transaction activity, the more the transactions delink stale rows.</span></span>  
  
 <span data-ttu-id="a8120-118">垃圾收集由主垃圾收集线程控制。</span><span class="sxs-lookup"><span data-stu-id="a8120-118">Garbage collection is controlled by the main garbage collection thread.</span></span> <span data-ttu-id="a8120-119">主垃圾收集线程每分钟运行一次，或在提交的事务数目超过内部阈值时运行。</span><span class="sxs-lookup"><span data-stu-id="a8120-119">The main garbage collection thread runs every minute, or when the number of committed transactions exceeds an internal threshold.</span></span> <span data-ttu-id="a8120-120">垃圾收集器的任务是：</span><span class="sxs-lookup"><span data-stu-id="a8120-120">The task of the garbage collector is to:</span></span>  
  
-   <span data-ttu-id="a8120-121">标识已删除或更新一组行且在最旧的活动事务之前已提交的事务。</span><span class="sxs-lookup"><span data-stu-id="a8120-121">Identify transactions that have deleted or updated a set of rows and have committed before the oldest active transaction.</span></span>  
  
-   <span data-ttu-id="a8120-122">标识这些旧事务创建的行版本。</span><span class="sxs-lookup"><span data-stu-id="a8120-122">Identity row versions created by these old transactions.</span></span>  
  
-   <span data-ttu-id="a8120-123">将旧行分组到每个单元有 16 行的一个或多个单元中。</span><span class="sxs-lookup"><span data-stu-id="a8120-123">Group old rows into one or more units of 16 rows each.</span></span> <span data-ttu-id="a8120-124">执行此操作是为了将垃圾收集器的工作分配到若干较小的单元中。</span><span class="sxs-lookup"><span data-stu-id="a8120-124">This is done to distribute the work of the garbage collector into smaller units.</span></span>  
  
-   <span data-ttu-id="a8120-125">将这些工作单元移到垃圾收集队列中，每个计划程序一个。</span><span class="sxs-lookup"><span data-stu-id="a8120-125">Move these work units into the garbage collection queue, one for each scheduler.</span></span> <span data-ttu-id="a8120-126">有关详细信息，请参考以下垃圾回收器 DMV：[sys.dm_xtp_gc_stats (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-xtp-gc-stats-transact-sql)、[sys.dm_db_xtp_gc_cycle_stats (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-gc-cycle-stats-transact-sql) 和 [sys.dm_xtp_gc_queue_stats (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-xtp-gc-queue-stats-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a8120-126">Refer to the garbage collector DMVs for the details: [sys.dm_xtp_gc_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xtp-gc-stats-transact-sql), [sys.dm_db_xtp_gc_cycle_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-gc-cycle-stats-transact-sql), and [sys.dm_xtp_gc_queue_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xtp-gc-queue-stats-transact-sql).</span></span>  
  
 <span data-ttu-id="a8120-127">在用户事务提交后，它识别与它在其上运行的计划程序相关联的所有排队项，然后释放内存。</span><span class="sxs-lookup"><span data-stu-id="a8120-127">After a user transaction commits, it identifies all queued items associated with the scheduler it ran on and then releases the memory.</span></span> <span data-ttu-id="a8120-128">如果计划程序上的垃圾收集队列为空，则它会搜索当前 NUMA 节点中的任何非空队列。</span><span class="sxs-lookup"><span data-stu-id="a8120-128">If the garbage collection queue on the scheduler is empty, it searches for any non-empty queue in the current NUMA node.</span></span> <span data-ttu-id="a8120-129">如果存在较少事务活动或者有内存压力，则主垃圾收集线程可访问任何队列的垃圾收集行。</span><span class="sxs-lookup"><span data-stu-id="a8120-129">If there is low transactional activity and there is memory pressure, the main garbage-collection thread can access garbage collect rows from any queue.</span></span> <span data-ttu-id="a8120-130">如果在删除大量行后（举例）没有事务活动并且没有内存压力，则在事务活动恢复或有内存压力之前，不会对删除的行进行垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="a8120-130">If there is no transactional activity after (for example) deleting a large number of rows and there is no memory pressure, the deleted rows will not be garbage collected until the transactional activity resumes or there is memory pressure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8120-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a8120-131">See Also</span></span>  
 [<span data-ttu-id="a8120-132">管理内存中 OLTP 的内存</span><span class="sxs-lookup"><span data-stu-id="a8120-132">Managing Memory for In-Memory OLTP</span></span>](../../database-engine/managing-memory-for-in-memory-oltp.md)  
  
  
