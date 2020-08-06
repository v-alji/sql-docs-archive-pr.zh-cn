---
title: 为内存优化对象定义持续性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 0fe85fbf-8e8d-4983-96fd-d04b3c7d6d65
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 325f50a74ea75270dd62fc3564200c59255dc6cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579571"
---
# <a name="defining-durability-for-memory-optimized-objects"></a><span data-ttu-id="6b508-102">为内存优化对象定义持续性</span><span class="sxs-lookup"><span data-stu-id="6b508-102">Defining Durability for Memory-Optimized Objects</span></span>
  <span data-ttu-id="6b508-103">内存中 OLTP 可保证完整原子性、一致性、隔离和完整持久性 (ACID) 属性。</span><span class="sxs-lookup"><span data-stu-id="6b508-103">In-Memory OLTP guarantees full atomicity, consistency, isolation, and full durability (ACID) properties.</span></span> <span data-ttu-id="6b508-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和内存优化表上下文中的持续性提供了以下保证：</span><span class="sxs-lookup"><span data-stu-id="6b508-104">Durability in the context of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and memory-optimized tables provides following guarantees:</span></span>  
  
 <span data-ttu-id="6b508-105">事务持续性</span><span class="sxs-lookup"><span data-stu-id="6b508-105">Transactional Durability</span></span>  
 <span data-ttu-id="6b508-106">提交对内存优化表作出（DDL 或 DML）更改的完全持久事务时，对持久内存优化表作出的更改为永久更改。</span><span class="sxs-lookup"><span data-stu-id="6b508-106">When you commit a fully durable transaction that made (DDL or DML) changes to a memory-optimized table, the changes made to a durable memory-optimized table are permanent.</span></span>  
  
 <span data-ttu-id="6b508-107">向内存优化表提交延迟的持久事务时，仅在将内存中事务日志保存到磁盘后，该事务才成为持久事务。</span><span class="sxs-lookup"><span data-stu-id="6b508-107">When you commit a delayed durable transaction to a memory-optimized table, the transaction becomes durable only after the in-memory transaction log is saved to disk.</span></span>  
  
 <span data-ttu-id="6b508-108">重新启动持续性</span><span class="sxs-lookup"><span data-stu-id="6b508-108">Restart Durability</span></span>  
 <span data-ttu-id="6b508-109">当 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在崩溃或计划关闭后重新启动时，将对内存优化的持久表重新实例化，使其恢复为关闭或崩溃之前的状态。</span><span class="sxs-lookup"><span data-stu-id="6b508-109">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restarts after a crash or planned shutdown, the memory-optimized durable tables are reinstantiated to restore them to the state before the shutdown or crash.</span></span>  
  
 <span data-ttu-id="6b508-110">介质故障持续性</span><span class="sxs-lookup"><span data-stu-id="6b508-110">Media Failure Durability</span></span>  
 <span data-ttu-id="6b508-111">如果发生故障或损坏的磁盘包含持久内存优化的对象的一个或多个持久化副本，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 备份和还原功能将内存优化表还原到新介质上。</span><span class="sxs-lookup"><span data-stu-id="6b508-111">If a failed or corrupt disk contains one or more persisted copies of durable memory-optimized objects, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup and restore feature restores memory-optimized tables on the new media.</span></span>  
  
 <span data-ttu-id="6b508-112">有两个用于内存优化表的持续性选项：</span><span class="sxs-lookup"><span data-stu-id="6b508-112">There are two durability options for memory-optimized tables:</span></span>  
  
 <span data-ttu-id="6b508-113">SCHEMA_ONLY（非持久表）</span><span class="sxs-lookup"><span data-stu-id="6b508-113">SCHEMA_ONLY (non-durable table)</span></span>  
 <span data-ttu-id="6b508-114">此选项可确保表架构（包括索引）的持续性。</span><span class="sxs-lookup"><span data-stu-id="6b508-114">This option ensures durability of the table schema, including indexes.</span></span> <span data-ttu-id="6b508-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 重新启动时，将会重新创建非持久表，但是该表启动时不包含数据。</span><span class="sxs-lookup"><span data-stu-id="6b508-115">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is restarted, the non-durable table is recreated, but starts with no data.</span></span> <span data-ttu-id="6b508-116">（这与 tempdb 中的表不同；对于 tempdb 中的表，表及其数据都会在重新启动时丢失。）创建非持久表的典型情况是用于存储瞬时数据（如用于 ETL 进程的临时表）。</span><span class="sxs-lookup"><span data-stu-id="6b508-116">(This is unlike a table in tempdb, where both the table and its data are lost upon restart.) A typical scenario for creating a non-durable table is to store transient data, such as a staging table for an ETL process.</span></span> <span data-ttu-id="6b508-117">SCHEMA_ONLY 持续性可避免事务日志记录和检查点，这样可大幅减少 I/O 操作数。</span><span class="sxs-lookup"><span data-stu-id="6b508-117">A SCHEMA_ONLY durability avoids both transaction logging and checkpoint, which can significantly reduce I/O operations.</span></span>  
  
 <span data-ttu-id="6b508-118">SCHEMA_AND_DATA（持久表）</span><span class="sxs-lookup"><span data-stu-id="6b508-118">SCHEMA_AND_DATA (durable table)</span></span>  
 <span data-ttu-id="6b508-119">此选项提供架构和数据的持续性。</span><span class="sxs-lookup"><span data-stu-id="6b508-119">This option provides durability of both schema and data.</span></span> <span data-ttu-id="6b508-120">数据持续性的级别取决于提交事务时其作为完全持久还是延迟持续性。</span><span class="sxs-lookup"><span data-stu-id="6b508-120">The level of data durability depends on whether you commit a transaction as fully durable or with delayed durability.</span></span> <span data-ttu-id="6b508-121">完全持久事务对数据和架构提供相同的持续性保证，与基于磁盘的表类似。</span><span class="sxs-lookup"><span data-stu-id="6b508-121">Fully durable transactions provide the same durability guarantee for data and schema, similar to a disk-based table.</span></span> <span data-ttu-id="6b508-122">延迟持续性将提高性能，但如果服务器崩溃或进行故障转移，则可能会丢失数据。</span><span class="sxs-lookup"><span data-stu-id="6b508-122">Delayed durability will improve performance but can potentially result in data loss in case of a server crash or fail over.</span></span> <span data-ttu-id="6b508-123">（有关延迟持续性的详细信息，请参阅 [控制事务持续性](../logs/control-transaction-durability.md)。）</span><span class="sxs-lookup"><span data-stu-id="6b508-123">(For more information about delayed durability, see [Control Transaction Durability](../logs/control-transaction-durability.md).)</span></span>  
  
 <span data-ttu-id="6b508-124">与基于磁盘的表类似，内存优化表的架构在数据库的主文件组中持久化。</span><span class="sxs-lookup"><span data-stu-id="6b508-124">The schema of the memory-optimized table is persisted, similar to disk-based tables, in the primary file group of a database.</span></span>  
  
 <span data-ttu-id="6b508-125">持久内存优化表中的数据保存在数据和差异文件对中。</span><span class="sxs-lookup"><span data-stu-id="6b508-125">Data in durable memory-optimized tables is saved in data and delta file pairs.</span></span>  
  
 <span data-ttu-id="6b508-126">内存优化表中定义的索引仅在元数据中持久化，而在存储中不持久化。</span><span class="sxs-lookup"><span data-stu-id="6b508-126">The indexes defined in memory-optimized tables persist only in metadata, not in storage.</span></span> <span data-ttu-id="6b508-127">索引结构是在加载内存优化表期间生成的。</span><span class="sxs-lookup"><span data-stu-id="6b508-127">Index structures are generated as part of loading memory-optimized tables.</span></span>  
  
 <span data-ttu-id="6b508-128">行由 DELETE 语句显式删除，或由 UPDATE 语句间接删除。</span><span class="sxs-lookup"><span data-stu-id="6b508-128">Rows are deleted either explicitly by a DELETE statement or indirectly by an UPDATE statement.</span></span> <span data-ttu-id="6b508-129">UPDATE 操作是先执行删除，然后执行插入。</span><span class="sxs-lookup"><span data-stu-id="6b508-129">An UPDATE operation is executed as a delete followed by an insert.</span></span> <span data-ttu-id="6b508-130">删除行时，不会对数据文件进行任何更改，但是将用于标识已删除行的新行追加到对应的差异文件。</span><span class="sxs-lookup"><span data-stu-id="6b508-130">When a row is deleted, no change is made to a data file but a new row, identifying the deleted row, is appended to the corresponding delta file.</span></span>  
  
 <span data-ttu-id="6b508-131">在恢复或还原操作过程中，内存中 OLTP 引擎读取数据和差异文件以将其载入物理内存。</span><span class="sxs-lookup"><span data-stu-id="6b508-131">During recovery or restore operations, the In-Memory OLTP engine reads data and delta files for loading into physical memory.</span></span> <span data-ttu-id="6b508-132">加载时间由以下因素决定：</span><span class="sxs-lookup"><span data-stu-id="6b508-132">The load time is determined by:</span></span>  
  
-   <span data-ttu-id="6b508-133">要加载的数据量。</span><span class="sxs-lookup"><span data-stu-id="6b508-133">The amount of data to load.</span></span>  
  
-   <span data-ttu-id="6b508-134">顺序 I/O 带宽。</span><span class="sxs-lookup"><span data-stu-id="6b508-134">Sequential I/O bandwidth.</span></span>  
  
-   <span data-ttu-id="6b508-135">并行度，由文件容器数和处理器核心数决定。</span><span class="sxs-lookup"><span data-stu-id="6b508-135">Degree of parallelism, determined by number of file containers and processor cores.</span></span>  
  
-   <span data-ttu-id="6b508-136">日志的活动部分中需重做的日志记录量。</span><span class="sxs-lookup"><span data-stu-id="6b508-136">The amount of log records in the active portion of the log that need to be redone.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b508-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6b508-137">See Also</span></span>  
 [<span data-ttu-id="6b508-138">创建和管理用于内存优化对象的存储</span><span class="sxs-lookup"><span data-stu-id="6b508-138">Creating and Managing Storage for Memory-Optimized Objects</span></span>](creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  
