---
title: 内存优化表的还原和恢复 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 294975b7-e7d1-491b-b66a-fdb1100d2acc
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5e702798ea68745a038407fb65af7726a5c5d50e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589072"
---
# <a name="restore-and-recovery-of-memory-optimized-tables"></a><span data-ttu-id="ffbc7-102">内存优化表的还原和恢复</span><span class="sxs-lookup"><span data-stu-id="ffbc7-102">Restore and Recovery of Memory-Optimized Tables</span></span>
  <span data-ttu-id="ffbc7-103">检索或还原具有内存优化表的数据库的基本机制类似于仅具有基于磁盘的表的数据库。</span><span class="sxs-lookup"><span data-stu-id="ffbc7-103">The basic mechanism to recover or restore a database with memory-optimized tables is similar to databases with only disk-based tables.</span></span> <span data-ttu-id="ffbc7-104">但与基于磁盘的表不同，必须首先将内存优化表加载到内存中，然后数据库才可用于用户访问。</span><span class="sxs-lookup"><span data-stu-id="ffbc7-104">But unlike disk-based tables, memory-optimized tables must be loaded into memory before database is available for user access.</span></span> <span data-ttu-id="ffbc7-105">这会在数据库恢复中添加一个新步骤。</span><span class="sxs-lookup"><span data-stu-id="ffbc7-105">This adds a new step in the database recovery.</span></span> <span data-ttu-id="ffbc7-106">按如下所示更改数据库恢复中修改的步骤：</span><span class="sxs-lookup"><span data-stu-id="ffbc7-106">The modified steps in database recovery are changed as follows:</span></span>

 <span data-ttu-id="ffbc7-107">当 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 重新启动时，每个数据库都会经历一个恢复阶段，该阶段由以下三个阶段构成：</span><span class="sxs-lookup"><span data-stu-id="ffbc7-107">When the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restarts, each database goes through a recovery phase that consists of the following three phases:</span></span>

1.  <span data-ttu-id="ffbc7-108">分析阶段。</span><span class="sxs-lookup"><span data-stu-id="ffbc7-108">The analysis phase.</span></span> <span data-ttu-id="ffbc7-109">在此阶段中，将对活动事务日志执行一遍，以便检测已提交和未提交事务。</span><span class="sxs-lookup"><span data-stu-id="ffbc7-109">During this phase, a pass is made on the active transaction logs to detect committed and uncommitted transactions.</span></span> <span data-ttu-id="ffbc7-110">内存中 OLTP 引擎标识检查点以便加载和预加载其系统表日志条目。</span><span class="sxs-lookup"><span data-stu-id="ffbc7-110">The In-Memory OLTP engine identifies the checkpoint to load and preloads its system table log entries.</span></span> <span data-ttu-id="ffbc7-111">它还将处理某些文件分配日志记录。</span><span class="sxs-lookup"><span data-stu-id="ffbc7-111">It will also process some file allocation log records.</span></span>

2.  <span data-ttu-id="ffbc7-112">重做阶段。</span><span class="sxs-lookup"><span data-stu-id="ffbc7-112">The redo phase.</span></span> <span data-ttu-id="ffbc7-113">此阶段在基于磁盘的表和内存优化表上同时运行。</span><span class="sxs-lookup"><span data-stu-id="ffbc7-113">This phase is run concurrently on both disk-based and memory-optimized tables.</span></span>

     <span data-ttu-id="ffbc7-114">对于基于磁盘的表，数据库将移到当前时间点并且获取未提交事务持有的锁。</span><span class="sxs-lookup"><span data-stu-id="ffbc7-114">For disk-based tables, the database is moved to the current point in time and acquires locks taken by uncommitted transactions.</span></span>

     <span data-ttu-id="ffbc7-115">对于内存优化表，来自数据和差异文件对的数据将加载到内存中，然后基于上一持久检查点通过活动事务日志更新数据。</span><span class="sxs-lookup"><span data-stu-id="ffbc7-115">For memory-optimized tables, data from the data and delta file pairs are loaded into memory and then update the data with the active transaction log based on the last durable checkpoint.</span></span>

     <span data-ttu-id="ffbc7-116">在基于磁盘的表和内存优化表上的上述操作完成后，数据库将可供访问。</span><span class="sxs-lookup"><span data-stu-id="ffbc7-116">When the above operations on disk-based and memory-optimized tables are complete, the database is available for access.</span></span>

3.  <span data-ttu-id="ffbc7-117">撤消阶段。</span><span class="sxs-lookup"><span data-stu-id="ffbc7-117">The undo phase.</span></span> <span data-ttu-id="ffbc7-118">在此阶段中，将回滚未提交的事务。</span><span class="sxs-lookup"><span data-stu-id="ffbc7-118">In this phase, the uncommitted transactions are rolled back.</span></span>

 <span data-ttu-id="ffbc7-119">将内存优化表加载到内存中可能会影响恢复时间目标 (RTO) 的性能。</span><span class="sxs-lookup"><span data-stu-id="ffbc7-119">Loading memory-optimized tables into memory can affect performance of the recovery time objective (RTO).</span></span> <span data-ttu-id="ffbc7-120">为缩短从数据和差异文件加载内存优化的数据的时间，内存中 OLTP 引擎按如下所示并行加载数据/差异文件：</span><span class="sxs-lookup"><span data-stu-id="ffbc7-120">To improve the load time of memory-optimized data from data and delta files, the In-Memory OLTP engine loads the data/delta files in parallel as follows:</span></span>

-   <span data-ttu-id="ffbc7-121">创建增量映射筛选器。</span><span class="sxs-lookup"><span data-stu-id="ffbc7-121">Creating a Delta Map Filter.</span></span> <span data-ttu-id="ffbc7-122">差异文件存储对已删除行的引用。</span><span class="sxs-lookup"><span data-stu-id="ffbc7-122">Delta files store references to the deleted rows.</span></span> <span data-ttu-id="ffbc7-123">每个容器的一个线程读取差异文件并且创建增量映射筛选器。</span><span class="sxs-lookup"><span data-stu-id="ffbc7-123">One thread per container reads the delta files and creates a delta map filter.</span></span> <span data-ttu-id="ffbc7-124">（内存优化数据文件组可以具有一个或多个容器。）</span><span class="sxs-lookup"><span data-stu-id="ffbc7-124">(A memory optimized data filegroup can have one or more containers.)</span></span>

-   <span data-ttu-id="ffbc7-125">对数据文件进行流式处理。</span><span class="sxs-lookup"><span data-stu-id="ffbc7-125">Streaming the data files.</span></span>  <span data-ttu-id="ffbc7-126">在创建了增量映射筛选器后，可使用与逻辑 CPU 数量一样多的线程读取数据文件。</span><span class="sxs-lookup"><span data-stu-id="ffbc7-126">Once the delta-map filter is created, data files are read using as many threads as there are logical CPUs.</span></span> <span data-ttu-id="ffbc7-127">读取数据文件的每个线程都读取数据行、检查关联的增量映射并且只将尚未标记为删除的行插入表中。</span><span class="sxs-lookup"><span data-stu-id="ffbc7-127">Each thread reading the data file reads the data rows, checks the associated delta map and only inserts the row into table if this row has not been marked deleted.</span></span> <span data-ttu-id="ffbc7-128">在某些情况下，此部分的恢复可能是受到 CPU 的约束的，如下所述。</span><span class="sxs-lookup"><span data-stu-id="ffbc7-128">This part of recovery can be CPU bound in some cases as noted below.</span></span>

 <span data-ttu-id="ffbc7-129">![内存优化表。](../../database-engine/media/memory-optimized-tables.gif "内存优化表。")</span><span class="sxs-lookup"><span data-stu-id="ffbc7-129">![Memory-optimized tables.](../../database-engine/media/memory-optimized-tables.gif "Memory-optimized tables.")</span></span>

 <span data-ttu-id="ffbc7-130">内存优化表通常可按 I/O 速度加载到内存中，但有些情况下，将数据行加载到内存中将会较慢。</span><span class="sxs-lookup"><span data-stu-id="ffbc7-130">Memory-optimized tables can generally be loaded into memory at the speed of I/O but there are cases when loading data rows into memory will be slower.</span></span> <span data-ttu-id="ffbc7-131">具体情况为：</span><span class="sxs-lookup"><span data-stu-id="ffbc7-131">Specific cases are:</span></span>

-   <span data-ttu-id="ffbc7-132">针对哈希索引的较低的存储桶计数可能会导致过多冲突，以致降低插入数据行的速度。</span><span class="sxs-lookup"><span data-stu-id="ffbc7-132">Low bucket count for hash index can lead to excessive collision causing data row inserts to be slower.</span></span> <span data-ttu-id="ffbc7-133">这通常导致非常高的 CPU 使用吞吐量，尤其是在恢复即将结束时。</span><span class="sxs-lookup"><span data-stu-id="ffbc7-133">This generally results in very high CPU utilization throughout, and especially towards the end of recovery.</span></span> <span data-ttu-id="ffbc7-134">如果您正确配置了哈希索引，则不应影响恢复时间。</span><span class="sxs-lookup"><span data-stu-id="ffbc7-134">If you configured the hash index correctly, it should not impact the recovery time.</span></span>

-   <span data-ttu-id="ffbc7-135">与在创建时调整其存储桶计数大小的哈希索引不同，具有一个或多个非聚集索引的大型内存优化表会动态增长，从而导致较高的 CPU 使用率。</span><span class="sxs-lookup"><span data-stu-id="ffbc7-135">Large memory-optimized tables with one or more nonclustered indexes, unlike a hash index whose bucket count is sized at create time, the nonclustered indexes grow dynamically, resulting in high CPU utilization.</span></span>

## <a name="restoring-a-database-with-memory-optimized-tables"></a><span data-ttu-id="ffbc7-136">还原带有内存优化表的数据库</span><span class="sxs-lookup"><span data-stu-id="ffbc7-136">Restoring a Database with Memory-optimized tables</span></span>
 <span data-ttu-id="ffbc7-137">你知道服务器具有足够内存，可以还原数据库，但是我们要求将数据库所需的内存视为现有资源池的一部分。</span><span class="sxs-lookup"><span data-stu-id="ffbc7-137">You know that you have sufficient memory on the server to restore a database, but there's a requirement  that the memory needed by the database is accounted for as part of an existing Resource Pool.</span></span>  <span data-ttu-id="ffbc7-138">你知道在数据库出现之前，你无法创建到资源池的绑定，因此执行 RESTORE WITH NORECOVERY。</span><span class="sxs-lookup"><span data-stu-id="ffbc7-138">You know that you cannot create the binding to the resource pool before the database exists, so you perform the restore WITH NORECOVERY.</span></span>  <span data-ttu-id="ffbc7-139">这将导致数据库磁盘映像的还原和数据库的创建，但因为数据库未处于联机状态，所以不会使用任何内存中 OLTP 内存。</span><span class="sxs-lookup"><span data-stu-id="ffbc7-139">This causes the disk image of the database to be restored and the database to be created, but no In-Memory OLTP memory is consumed because the database is not brought online.</span></span>

 <span data-ttu-id="ffbc7-140">此时，你可以创建资源池到数据库的绑定，然后使用 RESTORE WITH RECOVERY 使已还原的数据库处于联机状态。</span><span class="sxs-lookup"><span data-stu-id="ffbc7-140">At this point, you can create the Resource Pool to Database binding, and then use RESTORE WITH RECOVERY to bring the restored database online.</span></span>  <span data-ttu-id="ffbc7-141">由于在使数据库处于联机状态之前，绑定已就绪，其内存中 OLTP 内存消耗已正确算入。</span><span class="sxs-lookup"><span data-stu-id="ffbc7-141">Since the binding is in place before the database is brought online, its In-Memory OLTP memory consumption is properly accounted for.</span></span> <span data-ttu-id="ffbc7-142">这要求仅还原数据库一次。</span><span class="sxs-lookup"><span data-stu-id="ffbc7-142">This requires restoring the database only once.</span></span> <span data-ttu-id="ffbc7-143">第一条 RESTORE 命令是一条仅读取备份标头的信息性命令，而最后一条命令只触发恢复而实际不还原任何位。</span><span class="sxs-lookup"><span data-stu-id="ffbc7-143">The first RESTORE command is an informational command that only reads the backup header, and the last command simply triggers recovery without actually restoring any bits.</span></span>

## <a name="see-also"></a><span data-ttu-id="ffbc7-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ffbc7-144">See Also</span></span>
 [<span data-ttu-id="ffbc7-145">内存优化表的备份、还原和恢复</span><span class="sxs-lookup"><span data-stu-id="ffbc7-145">Backup, Restore, and Recovery of Memory-Optimized Tables</span></span>](memory-optimized-tables.md)


