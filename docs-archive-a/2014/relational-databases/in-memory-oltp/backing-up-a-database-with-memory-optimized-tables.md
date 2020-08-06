---
title: 使用内存优化表备份数据库 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 83d47694-e56d-4dae-b54e-14945bf8ba31
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 176448aa9d4bab4101ab2db12ffc9a8a7fd1a5b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578198"
---
# <a name="backing-up-a-database-with-memory-optimized-tables"></a><span data-ttu-id="813a7-102">使用内存优化表备份数据库</span><span class="sxs-lookup"><span data-stu-id="813a7-102">Backing Up a Database with Memory-Optimized Tables</span></span>
  <span data-ttu-id="813a7-103">内存优化表在定期数据库备份过程中进行备份。</span><span class="sxs-lookup"><span data-stu-id="813a7-103">Memory-optimized tables are backed up as part of regular database backups.</span></span> <span data-ttu-id="813a7-104">对于基于磁盘的表，数据和差异文件对的 CHECKSUM 在数据库备份过程中进行验证，以检测存储损坏。</span><span class="sxs-lookup"><span data-stu-id="813a7-104">As for disk-based tables, the CHECKSUM of data and delta file pairs is validated as part of the database backup to detect storage corruption.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="813a7-105">在备份期间，如果检测到内存优化文件组中的一个或多个文件存在校验和错误，您将无法还原并重新启动数据库。</span><span class="sxs-lookup"><span data-stu-id="813a7-105">During a backup, if you detect a CHECKSUM error in one or more files in a memory-optimized filegroup, you will not be able to restore and restart the database.</span></span> <span data-ttu-id="813a7-106">在这种情况下，您必须使用最新的已知优良备份还原数据库。</span><span class="sxs-lookup"><span data-stu-id="813a7-106">In that situation, you must, restore your database with the last known good backup.</span></span> <span data-ttu-id="813a7-107">如果没有备份，可从内存优化表和基于磁盘的表导出数据，然后在删除并重新创建数据库之后重新加载数据。</span><span class="sxs-lookup"><span data-stu-id="813a7-107">If you don't have a backup, you can export the data from memory-optimized tables and disk-based tables and reload after you drop and recreate the database.</span></span>  
  
 <span data-ttu-id="813a7-108">具有一个或多个内存优化表的数据库的完整备份包括基于磁盘的表（如果有）的已分配存储、活动事务日志以及内存优化表的数据和差异文件对（也称为检查点文件对）。</span><span class="sxs-lookup"><span data-stu-id="813a7-108">A full backup of a database with one or more memory-optimized tables consists of the allocated storage for disk-based tables (if any), the active transaction log, and the data and delta file pairs (also known as checkpoint file pairs) for memory-optimized tables.</span></span> <span data-ttu-id="813a7-109">但是，如 [内存优化表的持久性](memory-optimized-tables.md)中所述，内存优化表使用的存储可以比其在内存中的大小大得多，会影响数据库备份的大小。</span><span class="sxs-lookup"><span data-stu-id="813a7-109">However, as described in [Durability for Memory-Optimized Tables](memory-optimized-tables.md), the storage used by memory-optimized tables can be much larger than its size in memory, and it affects the size of the database backup.</span></span>  
  
## <a name="full-database-backup"></a><span data-ttu-id="813a7-110">完整数据库备份</span><span class="sxs-lookup"><span data-stu-id="813a7-110">Full Database Backup</span></span>  
 <span data-ttu-id="813a7-111">此讨论侧重于只有持久内存优化表的数据库的数据库备份，因为基于磁盘的表的备份过程相同。</span><span class="sxs-lookup"><span data-stu-id="813a7-111">This discussion will focus on database backups for databases with just durable memory-optimized tables, because the backup for disk-based tables is the same.</span></span> <span data-ttu-id="813a7-112">内存优化文件组中的检查点文件对可能处于各种状态。</span><span class="sxs-lookup"><span data-stu-id="813a7-112">The checkpoint file pairs in the memory-optimized filegroup could be in various states.</span></span> <span data-ttu-id="813a7-113">下表介绍备份的文件部分。</span><span class="sxs-lookup"><span data-stu-id="813a7-113">The table below describes what part of the files is backed.</span></span>  
  
|<span data-ttu-id="813a7-114">检查点文件对状态</span><span class="sxs-lookup"><span data-stu-id="813a7-114">Checkpoint File Pair State</span></span>|<span data-ttu-id="813a7-115">备份</span><span class="sxs-lookup"><span data-stu-id="813a7-115">Backup</span></span>|  
|--------------------------------|------------|  
|<span data-ttu-id="813a7-116">PRECREATED</span><span class="sxs-lookup"><span data-stu-id="813a7-116">PRECREATED</span></span>|<span data-ttu-id="813a7-117">仅文件元数据</span><span class="sxs-lookup"><span data-stu-id="813a7-117">File metadata only</span></span>|  
|<span data-ttu-id="813a7-118">UNDER CONSTRUCTION</span><span class="sxs-lookup"><span data-stu-id="813a7-118">UNDER CONSTRUCTION</span></span>|<span data-ttu-id="813a7-119">仅文件元数据</span><span class="sxs-lookup"><span data-stu-id="813a7-119">File metadata only</span></span>|  
|<span data-ttu-id="813a7-120">活动</span><span class="sxs-lookup"><span data-stu-id="813a7-120">Active</span></span>|<span data-ttu-id="813a7-121">文件元数据加上使用的字节</span><span class="sxs-lookup"><span data-stu-id="813a7-121">File metadata plus used bytes</span></span>|  
|<span data-ttu-id="813a7-122">合并源</span><span class="sxs-lookup"><span data-stu-id="813a7-122">Merge source</span></span>|<span data-ttu-id="813a7-123">文件元数据加上使用的字节</span><span class="sxs-lookup"><span data-stu-id="813a7-123">File metadata plus used bytes</span></span>|  
|<span data-ttu-id="813a7-124">合并目标</span><span class="sxs-lookup"><span data-stu-id="813a7-124">Merge target</span></span>|<span data-ttu-id="813a7-125">仅文件元数据</span><span class="sxs-lookup"><span data-stu-id="813a7-125">File metadata only</span></span>|  
|<span data-ttu-id="813a7-126">REQUIRED FOR BACKUP/HA</span><span class="sxs-lookup"><span data-stu-id="813a7-126">REQUIRED FOR BACKUP/HA</span></span>|<span data-ttu-id="813a7-127">文件元数据加上使用的字节</span><span class="sxs-lookup"><span data-stu-id="813a7-127">File metadata plus used bytes</span></span>|  
|<span data-ttu-id="813a7-128">IN TRANSITION TO TOMBSTONE</span><span class="sxs-lookup"><span data-stu-id="813a7-128">IN TRANSITION TO TOMBSTONE</span></span>|<span data-ttu-id="813a7-129">仅文件元数据</span><span class="sxs-lookup"><span data-stu-id="813a7-129">File metadata only</span></span>|  
|<span data-ttu-id="813a7-130">TOMBSTONE</span><span class="sxs-lookup"><span data-stu-id="813a7-130">TOMBSTONE</span></span>|<span data-ttu-id="813a7-131">仅文件元数据</span><span class="sxs-lookup"><span data-stu-id="813a7-131">File metadata only</span></span>|  
  
 <span data-ttu-id="813a7-132">具有一个或多个内存优化表的数据库备份的大小通常大于其在内存中的大小，但小于磁盘上存储。</span><span class="sxs-lookup"><span data-stu-id="813a7-132">The size of database backups with one or more memory-optimized tables is typically larger than its size in memory but smaller than the on-disk storage.</span></span> <span data-ttu-id="813a7-133">额外大小取决于删除的行数以及处于状态“合并源”和 REQUIRED FOR BACKUP/HA 下的检查点文件对数，从而间接取决于工作负荷。</span><span class="sxs-lookup"><span data-stu-id="813a7-133">The extra size will depend upon the number of deleted rows and the number of checkpoint file pairs in the states Merge source and REQUIRED FOR BACKUP/HA which indirectly depends upon the workload.</span></span> <span data-ttu-id="813a7-134">有关检查点文件对状态的说明，请参阅[transact-sql&#41;&#40;dm_db_xtp_checkpoint_files ](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-files-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="813a7-134">For descriptions of the states for checkpoint file pairs, see [sys.dm_db_xtp_checkpoint_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-files-transact-sql).</span></span>  
  
### <a name="estimating-size-of-full-database-backup"></a><span data-ttu-id="813a7-135">估计完整数据库备份的大小</span><span class="sxs-lookup"><span data-stu-id="813a7-135">Estimating Size of Full Database Backup</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="813a7-136">不建议使用 BackupSizeInBytes 值来估计内存中 OLTP 的备份大小。</span><span class="sxs-lookup"><span data-stu-id="813a7-136">It's recommended that you not use the BackupSizeInBytes value to estimate the backup size for In-Memory OLTP.</span></span>  
  
 <span data-ttu-id="813a7-137">第一个工作负荷方案适用于（主要）插入。</span><span class="sxs-lookup"><span data-stu-id="813a7-137">The first workload scenario is for (mostly) insert.</span></span> <span data-ttu-id="813a7-138">在此方案中，大多数数据文件处于“活动”状态、完全加载，删除的行非常少。</span><span class="sxs-lookup"><span data-stu-id="813a7-138">In this scenario, most data files will be in the Active state, fully loaded, and with very few deleted rows.</span></span> <span data-ttu-id="813a7-139">数据库备份的大小接近于内存中的数据大小。</span><span class="sxs-lookup"><span data-stu-id="813a7-139">The size of database backup up will be close to the size of data in memory.</span></span>  
  
 <span data-ttu-id="813a7-140">第二个工作负荷方案适用于频繁的插入、删除和更新操作：在更糟糕的情况下，每个检查点文件对在考虑删除的行之后，加载 50%。</span><span class="sxs-lookup"><span data-stu-id="813a7-140">The second workload scenario is for frequent insert, delete, and update operations: In the worst case, each of the checkpoint file pairs are 50% loaded, after accounting for the deleted rows.</span></span> <span data-ttu-id="813a7-141">因此数据库备份的大小至少是内存中的数据大小的 2 倍。</span><span class="sxs-lookup"><span data-stu-id="813a7-141">So the size of the database backup will at least be 2 times the size of data in memory.</span></span> <span data-ttu-id="813a7-142">此外，将添加到数据库备份大小的、处于状态“合并源”和“需要备份/高可用性”下的检查点文件对很少。</span><span class="sxs-lookup"><span data-stu-id="813a7-142">Additionally, there will few checkpoint file pairs in states Merge source and Required for backup/high availability that will add to the size of database backup.</span></span>  
  
## <a name="differential-backups-of-databases-with-memory-optimized-tables"></a><span data-ttu-id="813a7-143">具有内存优化表的数据库的差异备份</span><span class="sxs-lookup"><span data-stu-id="813a7-143">Differential Backups of Databases with Memory-Optimized Tables</span></span>  
 <span data-ttu-id="813a7-144">如 [内存优化表的持久性](memory-optimized-tables.md)中所述，针对内存优化表的存储由数据和差异文件构成。</span><span class="sxs-lookup"><span data-stu-id="813a7-144">The storage for memory-optimized tables consists of data and delta files as described in [Durability for Memory-Optimized Tables](memory-optimized-tables.md).</span></span> <span data-ttu-id="813a7-145">具有内存优化表的数据库的差异备份包含下列数据：</span><span class="sxs-lookup"><span data-stu-id="813a7-145">The differential backup of a database with memory-optimized tables contains the following data:</span></span>  
  
-   <span data-ttu-id="813a7-146">用于存储基于磁盘的表的文件组的差异备份不会受到内存优化表是否存在的影响。</span><span class="sxs-lookup"><span data-stu-id="813a7-146">Differential backup for filegroups storing disk-based tables is not affected by the presence of memory-optimized tables.</span></span>  
  
-   <span data-ttu-id="813a7-147">活动事务日志与在完整数据库备份中相同。</span><span class="sxs-lookup"><span data-stu-id="813a7-147">The active transaction log is the same as in a full database backup.</span></span>  
  
-   <span data-ttu-id="813a7-148">对于内存优化数据文件组，差异备份使用与完整数据库备份相同的算法标识用于备份的数据和差异文件，但它之后会筛选出文件的子集，如下所示：</span><span class="sxs-lookup"><span data-stu-id="813a7-148">For a memory-optimized data filegroup, the differential backup uses the same algorithm as full database backup to identify the data and delta files for backup but it then filters out the subset of files as follows:</span></span>  
  
    -   <span data-ttu-id="813a7-149">数据文件包含新插入的行，并且在该文件已满时，它会关闭并且标记为只读。</span><span class="sxs-lookup"><span data-stu-id="813a7-149">A data file contains newly inserted rows and when it is full, it is closed and marked read-only.</span></span> <span data-ttu-id="813a7-150">只有在上次完整数据库备份后关闭了数据文件的情况下，才备份该数据文件。</span><span class="sxs-lookup"><span data-stu-id="813a7-150">A data file is backed up only if it was closed after the last full database backup.</span></span> <span data-ttu-id="813a7-151">差异备份仅备份包含自上次完整数据库备份后插入的行的数据文件，但更新和删除情形除外，在此情形中，某些插入的行可能已标记进行垃圾回收或已进行垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="813a7-151">The differential backup only backups up data files containing the inserted rows since the last full database backup with the exception of an update and delete scenario where it is possible that some of the inserted rows may have already been either marked for garbage collection or already garbage collected.</span></span>  
  
    -   <span data-ttu-id="813a7-152">差异文件存储对已删除数据行的引用。</span><span class="sxs-lookup"><span data-stu-id="813a7-152">A delta file stores references to the deleted data rows.</span></span> <span data-ttu-id="813a7-153">因为任何将来的事务都可能会删除行，所以，可在其生命周期中随时修改差异文件，该差异文件永远不会关闭。</span><span class="sxs-lookup"><span data-stu-id="813a7-153">Since any future transaction can delete a row, a delta file can be modified anytime in its life time, it is never closed.</span></span> <span data-ttu-id="813a7-154">差异文件始终备份。</span><span class="sxs-lookup"><span data-stu-id="813a7-154">A delta file is always backed up.</span></span> <span data-ttu-id="813a7-155">差异文件通常使用不到 10% 的存储空间，因此，差异文件对差异备份大小的影响很小。</span><span class="sxs-lookup"><span data-stu-id="813a7-155">Delta files typically use less than 10% of the storage, so delta files have a minimal impact on the size of differential backup.</span></span>  
  
 <span data-ttu-id="813a7-156">如果内存优化表在您的数据库大小中占据很大比例，则差异备份可显著减小数据库备份大小。</span><span class="sxs-lookup"><span data-stu-id="813a7-156">If memory-optimized tables are a significant portion of your database size, the differential backup can significantly reduce the size of your database backup.</span></span>  
  
 <span data-ttu-id="813a7-157">对于典型 OLTP 工作负荷，差异备份显著小于完整数据库备份。</span><span class="sxs-lookup"><span data-stu-id="813a7-157">For typical OLTP workloads, the differential backups will be considerably smaller than the full database backups.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="813a7-158">另请参阅</span><span class="sxs-lookup"><span data-stu-id="813a7-158">See Also</span></span>  
 [<span data-ttu-id="813a7-159">内存优化表的备份、还原和恢复</span><span class="sxs-lookup"><span data-stu-id="813a7-159">Backup, Restore, and Recovery of Memory-Optimized Tables</span></span>](restore-and-recovery-of-memory-optimized-tables.md)  
  
  
