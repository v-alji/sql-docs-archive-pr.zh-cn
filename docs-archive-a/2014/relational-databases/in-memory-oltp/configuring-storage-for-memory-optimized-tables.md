---
title: 为内存优化表配置存储 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 6e005de0-3a77-4b91-b497-14cc0f9f6605
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4e6e5f5a931669e2fc07cb957e60fd9c77b9b735
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693342"
---
# <a name="configuring-storage-for-memory-optimized-tables"></a><span data-ttu-id="f299e-102">为内存优化表配置内存</span><span class="sxs-lookup"><span data-stu-id="f299e-102">Configuring Storage for Memory-Optimized Tables</span></span>
  <span data-ttu-id="f299e-103">您需要配置存储容量和每秒输入/输出操作数 (IOPS)。</span><span class="sxs-lookup"><span data-stu-id="f299e-103">You need to configure storage capacity and input/output operations per second (IOPS).</span></span>  
  
## <a name="storage-capacity"></a><span data-ttu-id="f299e-104">存储容量</span><span class="sxs-lookup"><span data-stu-id="f299e-104">Storage Capacity</span></span>  
 <span data-ttu-id="f299e-105">使用 [估算内存优化表的内存需求](memory-optimized-tables.md) 中的信息估计数据库的持久内存优化表的内存中大小。</span><span class="sxs-lookup"><span data-stu-id="f299e-105">Use the information in [Estimate Memory Requirements for Memory-Optimized Tables](memory-optimized-tables.md) to estimate the in-memory size of the database's durable memory-optimized tables.</span></span> <span data-ttu-id="f299e-106">由于未为内存优化表保留索引，因此不包括索引大小。</span><span class="sxs-lookup"><span data-stu-id="f299e-106">Because indexes are not persisted for memory-optimized tables, do not include the size of indexes.</span></span> <span data-ttu-id="f299e-107">确定此大小后，您需要提供大小为持久内存中表大小的四倍的磁盘空间。</span><span class="sxs-lookup"><span data-stu-id="f299e-107">Once you determine the size, you need to provide disk space that is four times the size of durable, in-memory tables.</span></span>  
  
## <a name="storage-performance"></a><span data-ttu-id="f299e-108">存储性能</span><span class="sxs-lookup"><span data-stu-id="f299e-108">Storage Performance</span></span>  
 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] <span data-ttu-id="f299e-109">会大大增加您的工作负荷吞吐量。</span><span class="sxs-lookup"><span data-stu-id="f299e-109">can significantly increase your workload throughput.</span></span> <span data-ttu-id="f299e-110">因此，确保 IO 不成为瓶颈非常重要。</span><span class="sxs-lookup"><span data-stu-id="f299e-110">Therefore, it is important to ensure that IO is not a bottleneck.</span></span>  
  
-   <span data-ttu-id="f299e-111">在将基于磁盘的表迁移到内存优化表时，请确保事务日志位于可支持增加事务日志活动的存储介质上。</span><span class="sxs-lookup"><span data-stu-id="f299e-111">When migrating disk-based tables to memory-optimized tables, make sure that the transaction log is on a storage media that can support increased transaction log activity.</span></span> <span data-ttu-id="f299e-112">例如，如果存储介质以 100 MB/秒的速度支持事务日志操作，并且内存优化表产生 5 倍以上的性能，则事务日志的存储介质必须还能支持 5 倍的性能改进，从而防止事务日志活动成为性能瓶颈。</span><span class="sxs-lookup"><span data-stu-id="f299e-112">For example, if your storage media supports transaction log operations at 100 MB/sec, and memory-optimized tables result in five times greater performance, the transaction log's storage media must be able to also support five times performance improvement, to prevent the transaction log activity from becoming a performance bottleneck.</span></span>  
  
-   <span data-ttu-id="f299e-113">内存优化表保留在跨一个或多个容器分布的文件中。</span><span class="sxs-lookup"><span data-stu-id="f299e-113">Memory-optimized tables are persisted in files distributed across one or more containers.</span></span> <span data-ttu-id="f299e-114">通常，每个容器均应映射到其自己的主轴，并用于增加的存储容量和改进的性能。</span><span class="sxs-lookup"><span data-stu-id="f299e-114">Each container should typically be mapped to its own spindle and is used both for increased storage capacity and improved performance.</span></span> <span data-ttu-id="f299e-115">你需要确保存储介质的顺序 IOPS 可支持事务日志吞吐量的3倍增长。</span><span class="sxs-lookup"><span data-stu-id="f299e-115">You need to ensure that sequential IOPS of the storage media can support a 3 times increase in transaction log throughput.</span></span>  
  
     <span data-ttu-id="f299e-116">例如，如果内存优化表在事务日志中生成 500MB/sec 的活动，则内存优化表的存储必须支持 1.5 GB/秒。如果需要支持事务日志吞吐量的3倍增长，就会观察到，数据和差异文件对首先用初始数据写入，然后需要作为合并操作的一部分读取/重新写入。</span><span class="sxs-lookup"><span data-stu-id="f299e-116">For example, if memory-optimized tables generate 500MB/sec of activity in the transaction log, the storage for memory-optimized tables must support 1.5GB/sec. The need to support a 3 times increase in transaction log throughput comes from the observation that the data and delta file pairs are first written with the initial data and then need to be read/re-written as part of a merge operation.</span></span>  
  
     <span data-ttu-id="f299e-117">估计存储的吞吐量时要考虑的另一个因素是内存优化表的恢复时间。</span><span class="sxs-lookup"><span data-stu-id="f299e-117">Another factor in estimating throughput for storage is the recovery time for memory-optimized tables.</span></span> <span data-ttu-id="f299e-118">在使数据库对应用程序可用前，必须将持久表中的数据读取到内存中。</span><span class="sxs-lookup"><span data-stu-id="f299e-118">Data from durable tables must be read into memory before a database is made available to applications.</span></span> <span data-ttu-id="f299e-119">通常，可按 IOPS 速度将数据加载到内存优化表中。</span><span class="sxs-lookup"><span data-stu-id="f299e-119">Commonly, loading data into memory-optimized tables can be done at the speed of IOPS.</span></span> <span data-ttu-id="f299e-120">如果持久内存优化表的总存储为 60 GB，并且您希望能够在 1 分钟内加载此数据，则存储的 IOPS 必须设置为 1 GB/秒。</span><span class="sxs-lookup"><span data-stu-id="f299e-120">So if the total storage for durable, memory-optimized tables is 60 GB and you want to be able to load this data in 1 minute, the IOPS for the storage must be set at 1 GB/sec.</span></span>  
  
-   <span data-ttu-id="f299e-121">如果您具有偶数个主轴，则应创建两倍数目的容器，并且每对映射到相同的主轴。</span><span class="sxs-lookup"><span data-stu-id="f299e-121">If you have even number of spindles, you should create two times the number of containers, each pair mapped to the same spindle.</span></span> <span data-ttu-id="f299e-122">这是扩展 IOPS 和存储所需的。</span><span class="sxs-lookup"><span data-stu-id="f299e-122">This is needed to spread the IOPS and the storage.</span></span> <span data-ttu-id="f299e-123">有关详细信息，请参阅[内存优化文件组](the-memory-optimized-filegroup.md)。</span><span class="sxs-lookup"><span data-stu-id="f299e-123">For more information, see [The Memory Optimized Filegroup](the-memory-optimized-filegroup.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f299e-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f299e-124">See Also</span></span>  
 [<span data-ttu-id="f299e-125">创建和管理用于内存优化对象的存储</span><span class="sxs-lookup"><span data-stu-id="f299e-125">Creating and Managing Storage for Memory-Optimized Objects</span></span>](creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  
