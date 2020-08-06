---
title: 重新组织和重新生成索引 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
f1_keywords:
- sql12.swb.indexproperties.fragmentation.f1
- sql12.swb.index.reorg.f1
- sql12.swb.index.rebuild.f1
helpviewer_keywords:
- large object defragmenting
- indexes [SQL Server], reorganizing
- index reorganization [SQL Server]
- reorganizing indexes
- defragmenting large object data types
- index fragmentation [SQL Server]
- index rebuilding [SQL Server]
- rebuilding indexes
- indexes [SQL Server], rebuilding
- defragmenting indexes
- nonclustered indexes [SQL Server], defragmenting
- fragmentation [SQL Server]
- index defragmenting [SQL Server]
- LOB data [SQL Server], defragmenting
- clustered indexes, defragmenting
ms.assetid: a28c684a-c4e9-4b24-a7ae-e248808b31e9
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7c00f2128bb4c54064511ffff9e8929c9faf4d59
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692934"
---
# <a name="reorganize-and-rebuild-indexes"></a><span data-ttu-id="30104-102">重新组织和重新生成索引</span><span class="sxs-lookup"><span data-stu-id="30104-102">Reorganize and Rebuild Indexes</span></span>
  <span data-ttu-id="30104-103">本主题介绍如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中重新组织或重新生成碎片索引。</span><span class="sxs-lookup"><span data-stu-id="30104-103">This topic describes how to reorganize or rebuild a fragmented index in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="30104-104">无论何时对基础数据执行插入、更新或删除操作， [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 都会自动维护索引。</span><span class="sxs-lookup"><span data-stu-id="30104-104">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] automatically maintains indexes whenever insert, update, or delete operations are made to the underlying data.</span></span> <span data-ttu-id="30104-105">随着时间的推移，这些修改可能会导致索引中的信息分散在数据库中（含有碎片）。</span><span class="sxs-lookup"><span data-stu-id="30104-105">Over time these modifications can cause the information in the index to become scattered in the database (fragmented).</span></span> <span data-ttu-id="30104-106">当索引包含的页中的逻辑排序（基于键值）与数据文件中的物理排序不匹配时，就存在碎片。</span><span class="sxs-lookup"><span data-stu-id="30104-106">Fragmentation exists when indexes have pages in which the logical ordering, based on the key value, does not match the physical ordering inside the data file.</span></span> <span data-ttu-id="30104-107">碎片非常多的索引可能会降低查询性能，导致应用程序响应缓慢。</span><span class="sxs-lookup"><span data-stu-id="30104-107">Heavily fragmented indexes can degrade query performance and cause your application to respond slowly.</span></span>  
  
 <span data-ttu-id="30104-108">您可以通过重新组织或重新生成索引来修复索引碎片。</span><span class="sxs-lookup"><span data-stu-id="30104-108">You can remedy index fragmentation by reorganizing or rebuilding an index.</span></span> <span data-ttu-id="30104-109">对于基于分区方案生成的已分区索引，可以在完整索引或索引的单个分区上使用下列方法之一。</span><span class="sxs-lookup"><span data-stu-id="30104-109">For partitioned indexes built on a partition scheme, you can use either of these methods on a complete index or a single partition of an index.</span></span> <span data-ttu-id="30104-110">重新生成索引将会删除并重新创建索引。</span><span class="sxs-lookup"><span data-stu-id="30104-110">Rebuilding an index drops and re-creates the index.</span></span> <span data-ttu-id="30104-111">这将根据指定的或现有的填充因子设置压缩页来删除碎片、回收磁盘空间，然后对连续页中的索引行重新排序。</span><span class="sxs-lookup"><span data-stu-id="30104-111">This removes fragmentation, reclaims disk space by compacting the pages based on the specified or existing fill factor setting, and reorders the index rows in contiguous pages.</span></span> <span data-ttu-id="30104-112">如果指定 ALL，将删除表中的所有索引，然后在单个事务中重新生成。</span><span class="sxs-lookup"><span data-stu-id="30104-112">When ALL is specified, all indexes on the table are dropped and rebuilt in a single transaction.</span></span> <span data-ttu-id="30104-113">使用最少系统资源重新组织索引。</span><span class="sxs-lookup"><span data-stu-id="30104-113">Reorganizing an index uses minimal system resources.</span></span> <span data-ttu-id="30104-114">通过对叶级页以物理方式重新排序，使之与叶节点的从左到右的逻辑顺序相匹配，进而对表和视图中的聚集索引和非聚集索引的叶级进行碎片整理。</span><span class="sxs-lookup"><span data-stu-id="30104-114">It defragments the leaf level of clustered and nonclustered indexes on tables and views by physically reordering the leaf-level pages to match the logical, left to right, order of the leaf nodes.</span></span> <span data-ttu-id="30104-115">重新组织还会压缩索引页。</span><span class="sxs-lookup"><span data-stu-id="30104-115">Reorganizing also compacts the index pages.</span></span> <span data-ttu-id="30104-116">压缩基于现有的填充因子值。</span><span class="sxs-lookup"><span data-stu-id="30104-116">Compaction is based on the existing fill factor value.</span></span>  
  
 <span data-ttu-id="30104-117">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="30104-117">**In This Topic**</span></span>  
  
-   <span data-ttu-id="30104-118">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="30104-118">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="30104-119">检测碎片</span><span class="sxs-lookup"><span data-stu-id="30104-119">Detecting Fragmentation</span></span>](#Fragmentation)  
  
     [<span data-ttu-id="30104-120">限制和局限</span><span class="sxs-lookup"><span data-stu-id="30104-120">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="30104-121">安全性</span><span class="sxs-lookup"><span data-stu-id="30104-121">Security</span></span>](#Security)  
  
-   <span data-ttu-id="30104-122">**若要检查索引的碎片，请使用：**</span><span class="sxs-lookup"><span data-stu-id="30104-122">**To check the fragmentation of an index, using:**</span></span>  
  
     [<span data-ttu-id="30104-123">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="30104-123">SQL Server Management Studio</span></span>](#SSMSProcedureFrag)  
  
     [<span data-ttu-id="30104-124">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="30104-124">Transact-SQL</span></span>](#TsqlProcedureFrag)  
  
-   <span data-ttu-id="30104-125">**若要重新组织或重新生成索引，请使用：**</span><span class="sxs-lookup"><span data-stu-id="30104-125">**To reorganize or rebuild an index, using:**</span></span>  
  
     [<span data-ttu-id="30104-126">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="30104-126">SQL Server Management Studio</span></span>](#SSMSProcedureReorg)  
  
     [<span data-ttu-id="30104-127">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="30104-127">Transact-SQL</span></span>](#TsqlProcedureReorg)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="30104-128">开始之前</span><span class="sxs-lookup"><span data-stu-id="30104-128">Before You Begin</span></span>  
  
###  <a name="detecting-fragmentation"></a><a name="Fragmentation"></a><span data-ttu-id="30104-129">检测碎片</span><span class="sxs-lookup"><span data-stu-id="30104-129">Detecting Fragmentation</span></span>  
 <span data-ttu-id="30104-130">决定使用哪种碎片整理方法的第一步是分析索引以确定碎片程度。</span><span class="sxs-lookup"><span data-stu-id="30104-130">The first step in deciding which defragmentation method to use is to analyze the index to determine the degree of fragmentation.</span></span> <span data-ttu-id="30104-131">通过使用系统函数 [sys.dm_db_index_physical_stats](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql)，你可以检测特定索引中的碎片、表或索引视图的所有索引、某个数据库中的所有索引或所有数据库中的所有索引。</span><span class="sxs-lookup"><span data-stu-id="30104-131">By using the system function [sys.dm_db_index_physical_stats](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql), you can detect fragmentation in a specific index, all indexes on a table or indexed view, all indexes in a database, or all indexes in all databases.</span></span> <span data-ttu-id="30104-132">对于已分区索引， **sys.dm_db_index_physical_stats** 还提供每个分区的碎片信息。</span><span class="sxs-lookup"><span data-stu-id="30104-132">For partitioned indexes, **sys.dm_db_index_physical_stats** also provides fragmentation information for each partition.</span></span>  
  
 <span data-ttu-id="30104-133">由 **sys.dm_db_index_physical_stats** 函数返回的结果集包含以下列。</span><span class="sxs-lookup"><span data-stu-id="30104-133">The result set returned by the **sys.dm_db_index_physical_stats** function includes the following columns.</span></span>  
  
|<span data-ttu-id="30104-134">列</span><span class="sxs-lookup"><span data-stu-id="30104-134">Column</span></span>|<span data-ttu-id="30104-135">说明</span><span class="sxs-lookup"><span data-stu-id="30104-135">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="30104-136">**avg_fragmentation_in_percent**</span><span class="sxs-lookup"><span data-stu-id="30104-136">**avg_fragmentation_in_percent**</span></span>|<span data-ttu-id="30104-137">逻辑碎片（索引中的无序页）的百分比。</span><span class="sxs-lookup"><span data-stu-id="30104-137">The percent of logical fragmentation (out-of-order pages in the index).</span></span>|  
|<span data-ttu-id="30104-138">**fragment_count**</span><span class="sxs-lookup"><span data-stu-id="30104-138">**fragment_count**</span></span>|<span data-ttu-id="30104-139">索引中的碎片（物理上连续的叶页）数量。</span><span class="sxs-lookup"><span data-stu-id="30104-139">The number of fragments (physically consecutive leaf pages) in the index.</span></span>|  
|<span data-ttu-id="30104-140">**avg_fragment_size_in_pages**</span><span class="sxs-lookup"><span data-stu-id="30104-140">**avg_fragment_size_in_pages**</span></span>|<span data-ttu-id="30104-141">索引中一个碎片的平均页数。</span><span class="sxs-lookup"><span data-stu-id="30104-141">Average number of pages in one fragment in an index.</span></span>|  
  
 <span data-ttu-id="30104-142">知道碎片程度后，可以使用下表确定修复碎片的最佳方法。</span><span class="sxs-lookup"><span data-stu-id="30104-142">After the degree of fragmentation is known, use the following table to determine the best method to correct the fragmentation.</span></span>  
  
|<span data-ttu-id="30104-143">**avg_fragmentation_in_percent** 值</span><span class="sxs-lookup"><span data-stu-id="30104-143">**avg_fragmentation_in_percent** value</span></span>|<span data-ttu-id="30104-144">修复语句</span><span class="sxs-lookup"><span data-stu-id="30104-144">Corrective statement</span></span>|  
|-----------------------------------------------|--------------------------|  
|<span data-ttu-id="30104-145">> 5%， \< = 30%</span><span class="sxs-lookup"><span data-stu-id="30104-145">> 5% and \< = 30%</span></span>|<span data-ttu-id="30104-146">ALTER INDEX REORGANIZE</span><span class="sxs-lookup"><span data-stu-id="30104-146">ALTER INDEX REORGANIZE</span></span>|  
|<span data-ttu-id="30104-147">> 30%</span><span class="sxs-lookup"><span data-stu-id="30104-147">> 30%</span></span>|<span data-ttu-id="30104-148">ALTER INDEX REBUILD WITH (ONLINE = ON) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="30104-148">ALTER INDEX REBUILD WITH (ONLINE = ON) <sup>1</sup></span></span>|

<span data-ttu-id="30104-149"><sup>1</sup> 重新生成索引可以联机执行，也可以脱机执行。</span><span class="sxs-lookup"><span data-stu-id="30104-149"><sup>1</sup> Rebuilding an index can be executed online or offline.</span></span> <span data-ttu-id="30104-150">重新组织索引始终联机执行。</span><span class="sxs-lookup"><span data-stu-id="30104-150">Reorganizing an index is always executed online.</span></span> <span data-ttu-id="30104-151">若要获得与重新组织选项相似的可用性，应联机重新生成索引。</span><span class="sxs-lookup"><span data-stu-id="30104-151">To achieve availability similar to the reorganize option, you should rebuild indexes online.</span></span>  
  
> [!TIP]
> <span data-ttu-id="30104-152">这些值提供了一个大致指导原则，用于确定应在 `ALTER INDEX REORGANIZE` 和 `ALTER INDEX REBUILD` 之间进行切换的点。</span><span class="sxs-lookup"><span data-stu-id="30104-152">These values provide a rough guideline for determining the point at which you should switch between `ALTER INDEX REORGANIZE` and `ALTER INDEX REBUILD`.</span></span> <span data-ttu-id="30104-153">不过，实际值可能会随情况而变化。</span><span class="sxs-lookup"><span data-stu-id="30104-153">However, the actual values may vary from case to case.</span></span> <span data-ttu-id="30104-154">必须要通过试验来确定最适合您环境的阈值。</span><span class="sxs-lookup"><span data-stu-id="30104-154">It is important that you experiment to determine the best threshold for your environment.</span></span> <span data-ttu-id="30104-155">例如，如果给定索引主要用于扫描操作，则删除碎片可以提高这些操作的性能。</span><span class="sxs-lookup"><span data-stu-id="30104-155">For example, if a given index is used mainly for scan operations, removing fragmentation can improve performance of these operations.</span></span> <span data-ttu-id="30104-156">对于主要用于查找操作的索引，性能优势不太明显。</span><span class="sxs-lookup"><span data-stu-id="30104-156">The performance benefit is less noticeable for indexes that are used primarily for seek operations.</span></span> <span data-ttu-id="30104-157">同样，删除堆中的碎片（不包含聚集索引的表）对于非聚集索引扫描操作特别有用，但在查找操作中不起作用。</span><span class="sxs-lookup"><span data-stu-id="30104-157">Similarly, removing fragmentation in a heap (a table with no clustered index) is especially useful for nonclustered index scan operations, but has little effect in lookup operations.</span></span>

<span data-ttu-id="30104-158">通常情况下，非常低的碎片级别（小于 5%）不应通过这些命令来解决，因为删除如此少量的碎片所获得的收益始终远低于重新组织或重新生成索引的开销。</span><span class="sxs-lookup"><span data-stu-id="30104-158">Very low levels of fragmentation (less than 5 percent) should typically not be addressed by either of these commands, because the benefit from removing such a small amount of fragmentation is almost always vastly outweighed by the cost of reorganizing or rebuilding the index.</span></span> 

> [!NOTE]
> <span data-ttu-id="30104-159">重新生成或重新组织小索引不会减少碎片。</span><span class="sxs-lookup"><span data-stu-id="30104-159">Rebuilding or reorganizing small indexes often does not reduce fragmentation.</span></span> <span data-ttu-id="30104-160">小索引的页面有关存储在混合盘区中。</span><span class="sxs-lookup"><span data-stu-id="30104-160">The pages of small indexes are sometimes stored on mixed extents.</span></span> <span data-ttu-id="30104-161">混合区最多可由八个对象共享，因此在重新组织或重新生成小索引之后可能不会减少小索引中的碎片。</span><span class="sxs-lookup"><span data-stu-id="30104-161">Mixed extents are shared by up to eight objects, so the fragmentation in a small index might not be reduced after reorganizing or rebuilding it.</span></span>

### <a name="index-defragmentation-considerations"></a><span data-ttu-id="30104-162">索引碎片整理注意事项</span><span class="sxs-lookup"><span data-stu-id="30104-162">Index defragmentation considerations</span></span>
<span data-ttu-id="30104-163">在某些情况下，如果非聚集索引记录中包含的物理或逻辑标识符需要更改，则重新生成聚集索引将自动重新生成引用聚集键的任何非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="30104-163">Under certain conditions, rebuilding a clustered index will automatically rebuild any nonclustered index that reference the clustering key, if the physical or logical identifiers contained in the nonclustered index records needs to change.</span></span>

<span data-ttu-id="30104-164">强制在表上自动重新生成所有非聚集索引的方案：</span><span class="sxs-lookup"><span data-stu-id="30104-164">Scenarios that force all nonclustered indexes to be automatically rebuilt on a table:</span></span>

-  <span data-ttu-id="30104-165">在表上创建聚集索引</span><span class="sxs-lookup"><span data-stu-id="30104-165">Creating a clustered index on a table</span></span>
-  <span data-ttu-id="30104-166">删除聚集索引，从而使表存储为堆</span><span class="sxs-lookup"><span data-stu-id="30104-166">Removing a clustered index, causing the table to be stored as a heap</span></span>
-  <span data-ttu-id="30104-167">更改聚集键以包括或排除列</span><span class="sxs-lookup"><span data-stu-id="30104-167">Changing the clustering key to include or exclude columns</span></span>

<span data-ttu-id="30104-168">不需要在表上自动重新生成所有非聚集索引的方案：</span><span class="sxs-lookup"><span data-stu-id="30104-168">Scenarios that do not require all nonclustered indexes to be automatically rebuilt on a table:</span></span>

-  <span data-ttu-id="30104-169">重新生成唯一聚集索引</span><span class="sxs-lookup"><span data-stu-id="30104-169">Rebuilding a unique clustered index</span></span>
-  <span data-ttu-id="30104-170">重新生成非唯一聚集索引</span><span class="sxs-lookup"><span data-stu-id="30104-170">Rebuilding a non-unique clustered index</span></span>
-  <span data-ttu-id="30104-171">更改索引架构，例如将分区方案应用于聚集索引或将聚集索引移到其他文件组</span><span class="sxs-lookup"><span data-stu-id="30104-171">Changing the index schema, such as applying a partitioning scheme to a clustered index or moving the clustered index to a different filegroup</span></span>
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="30104-172">限制和局限</span><span class="sxs-lookup"><span data-stu-id="30104-172">Limitations and Restrictions</span></span>  
  
<span data-ttu-id="30104-173">带有多于 128 个区的索引通过两个单独的阶段重新生成：逻辑阶段和物理阶段。</span><span class="sxs-lookup"><span data-stu-id="30104-173">Indexes with more than 128 extents are rebuilt in two separate phases: logical and physical.</span></span> <span data-ttu-id="30104-174">在逻辑阶段，将把由索引使用的现有分配单元标记为释放，对数据行进行复制并排序，然后将它们移到为存储重新生成的索引而创建的新分配单元。</span><span class="sxs-lookup"><span data-stu-id="30104-174">In the logical phase, the existing allocation units used by the index are marked for deallocation, the data rows are copied and sorted, then moved to new allocation units created to store the rebuilt index.</span></span> <span data-ttu-id="30104-175">在物理阶段，先前标记为取消分配的分配单元在发生在后台的短事务中被物理删除，而且不需要很多锁。</span><span class="sxs-lookup"><span data-stu-id="30104-175">In the physical phase, the allocation units previously marked for deallocation are physically dropped in short transactions that happen in the background, and do not require many locks.</span></span> <span data-ttu-id="30104-176">有关区的详细信息，请参考[页和区体系结构指南](https://docs.microsoft.com/sql/relational-databases/pages-and-extents-architecture-guide)。</span><span class="sxs-lookup"><span data-stu-id="30104-176">For more information about extents, refer to the [Pages and Extents Architecture Guide](https://docs.microsoft.com/sql/relational-databases/pages-and-extents-architecture-guide).</span></span>

<span data-ttu-id="30104-177">`ALTER INDEX REORGANIZE` 语句要求包含索引的数据文件具有可用的空间，因为该操作仅可在同一文件中分配临时工作，而不能在文件组内的另一个文件中进行分配。</span><span class="sxs-lookup"><span data-stu-id="30104-177">The `ALTER INDEX REORGANIZE` statement requires the data file containing the index to have space available, because the operation can only allocate temporary work pages on the same file, not another file within the filegroup.</span></span> <span data-ttu-id="30104-178">因此，尽管文件组可能有可用的空闲页，用户仍可能会遇到错误 1105：`Could not allocate space for object '###' in database '###' because the '###' filegroup is full. Create disk space by deleting unneeded files, dropping objects in the filegroup, adding additional files to the filegroup, or setting autogrowth on for existing files in the filegroup.`</span><span class="sxs-lookup"><span data-stu-id="30104-178">So although the filegroup might have free pages available, the user can still encounter error 1105: `Could not allocate space for object '###' in database '###' because the '###' filegroup is full. Create disk space by deleting unneeded files, dropping objects in the filegroup, adding additional files to the filegroup, or setting autogrowth on for existing files in the filegroup.`</span></span>

<span data-ttu-id="30104-179">对超过 1,000 个分区的表创建和重新生成非对齐索引是可能的，但不推荐。</span><span class="sxs-lookup"><span data-stu-id="30104-179">Creating and rebuilding non-aligned indexes on a table with more than 1,000 partitions is possible, but is not recommended.</span></span> <span data-ttu-id="30104-180">这样做可能会导致性能下降，或在执行这些操作的过程中占用过多内存。</span><span class="sxs-lookup"><span data-stu-id="30104-180">Doing so may cause degraded performance or excessive memory consumption during these operations.</span></span>

<span data-ttu-id="30104-181">如果索引所在的文件组脱机或设置为只读，则无法重新组织或重新生成索引。</span><span class="sxs-lookup"><span data-stu-id="30104-181">An index cannot be reorganized or rebuilt if the filegroup in which it is located is offline or set to read-only.</span></span> <span data-ttu-id="30104-182">如果指定了关键字 `ALL`，但有一个或多个索引位于脱机文件组或只读文件组中，该语句将失败。</span><span class="sxs-lookup"><span data-stu-id="30104-182">When the keyword `ALL` is specified and one or more indexes are in an offline or read-only filegroup, the statement fails.</span></span>
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="30104-183">Security</span><span class="sxs-lookup"><span data-stu-id="30104-183">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="30104-184">权限</span><span class="sxs-lookup"><span data-stu-id="30104-184">Permissions</span></span>  
 <span data-ttu-id="30104-185">要求具有对表或视图的 `ALTER` 权限。</span><span class="sxs-lookup"><span data-stu-id="30104-185">Requires `ALTER` permission on the table or view.</span></span> <span data-ttu-id="30104-186">用户必须是 **sysadmin** 固定服务器角色的成员，或者是 **db_ddladmin** 和 **db_owner** 固定数据库角色的成员。</span><span class="sxs-lookup"><span data-stu-id="30104-186">User must be a member of the **sysadmin** fixed server role or the **db_ddladmin** and **db_owner** fixed database roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedureFrag"></a> <span data-ttu-id="30104-187">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="30104-187">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-check-the-fragmentation-of-an-index"></a><span data-ttu-id="30104-188">检查索引的碎片</span><span class="sxs-lookup"><span data-stu-id="30104-188">To check the fragmentation of an index</span></span>  
  
1.  <span data-ttu-id="30104-189">在“对象资源管理器”中，展开其中包含要检查索引碎片的表的数据库。</span><span class="sxs-lookup"><span data-stu-id="30104-189">In Object Explorer, Expand the database that contains the table on which you want to check an index's fragmentation.</span></span>  
  
2.  <span data-ttu-id="30104-190">展开 **“表”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="30104-190">Expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="30104-191">展开要检查索引碎片的表。</span><span class="sxs-lookup"><span data-stu-id="30104-191">Expand the table on which you want to check an index's fragmentation.</span></span>  
  
4.  <span data-ttu-id="30104-192">展开 **“索引”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="30104-192">Expand the **Indexes** folder.</span></span>  
  
5.  <span data-ttu-id="30104-193">右键单击要检查碎片的索引，然后选择 **“属性”** 。</span><span class="sxs-lookup"><span data-stu-id="30104-193">Right-click the index of which you want to check the fragmentation and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="30104-194">在 **“选择页”** 下，选择 **“碎片”** 。</span><span class="sxs-lookup"><span data-stu-id="30104-194">Under **Select a page**, select **Fragmentation**.</span></span>  
  
     <span data-ttu-id="30104-195">**“碎片”** 页将提供以下信息：</span><span class="sxs-lookup"><span data-stu-id="30104-195">The following information is available on the **Fragmentation** page:</span></span>  
  
     <span data-ttu-id="30104-196">**页填充度**</span><span class="sxs-lookup"><span data-stu-id="30104-196">**Page fullness**</span></span>  
     <span data-ttu-id="30104-197">指示索引页的平均填充率（以百分比表示）。</span><span class="sxs-lookup"><span data-stu-id="30104-197">Indicates average fullness of the index pages, as a percentage.</span></span> <span data-ttu-id="30104-198">100% 表示索引页完全填充。</span><span class="sxs-lookup"><span data-stu-id="30104-198">100% means the index pages are completely full.</span></span> <span data-ttu-id="30104-199">50% 表示每个索引页平均填充一半。</span><span class="sxs-lookup"><span data-stu-id="30104-199">50% means that, on average, each index page is half full.</span></span>  
  
     <span data-ttu-id="30104-200">**碎片总计**</span><span class="sxs-lookup"><span data-stu-id="30104-200">**Total fragmentation**</span></span>  
     <span data-ttu-id="30104-201">逻辑碎片百分比。</span><span class="sxs-lookup"><span data-stu-id="30104-201">The logical fragmentation percentage.</span></span> <span data-ttu-id="30104-202">用于指示索引中未按顺序存储的页数。</span><span class="sxs-lookup"><span data-stu-id="30104-202">This indicates the number of pages in an index that are not stored in order.</span></span>  
  
     <span data-ttu-id="30104-203">**平均行大小**</span><span class="sxs-lookup"><span data-stu-id="30104-203">**Average row size**</span></span>  
     <span data-ttu-id="30104-204">叶级行的平均大小。</span><span class="sxs-lookup"><span data-stu-id="30104-204">The average size of a leaf level row.</span></span>  
  
     <span data-ttu-id="30104-205">**Depth**</span><span class="sxs-lookup"><span data-stu-id="30104-205">**Depth**</span></span>  
     <span data-ttu-id="30104-206">索引中的级别数（包括叶级别）。</span><span class="sxs-lookup"><span data-stu-id="30104-206">The number of levels in the index, including the leaf level.</span></span>  
  
     <span data-ttu-id="30104-207">**前推记录数**</span><span class="sxs-lookup"><span data-stu-id="30104-207">**Forwarded records**</span></span>  
     <span data-ttu-id="30104-208">堆中具有指向另一个数据位置的转向指针的记录数。</span><span class="sxs-lookup"><span data-stu-id="30104-208">The number of records in a heap that have forward pointers to another data location.</span></span> <span data-ttu-id="30104-209">（在更新过程中，如果在原始位置存储新行的空间不足，将会出现此状态。）</span><span class="sxs-lookup"><span data-stu-id="30104-209">(This state occurs during an update, when there is not enough room to store the new row in the original location.)</span></span>  
  
     <span data-ttu-id="30104-210">**虚影行数**</span><span class="sxs-lookup"><span data-stu-id="30104-210">**Ghost rows**</span></span>  
     <span data-ttu-id="30104-211">标记为已删除，但尚未移除的行数。</span><span class="sxs-lookup"><span data-stu-id="30104-211">The number of rows that are marked as deleted but not yet removed.</span></span> <span data-ttu-id="30104-212">当服务器不忙时，将通过清除线程移除这些行。</span><span class="sxs-lookup"><span data-stu-id="30104-212">These rows will be removed by a clean-up thread, when the server is not busy.</span></span> <span data-ttu-id="30104-213">此值不包括由于某个快照隔离事务未完成而保留的行。</span><span class="sxs-lookup"><span data-stu-id="30104-213">This value does not include rows that are being retained due to an outstanding snapshot isolation transaction.</span></span>  
  
     <span data-ttu-id="30104-214">**索引类型**</span><span class="sxs-lookup"><span data-stu-id="30104-214">**Index type**</span></span>  
     <span data-ttu-id="30104-215">索引的类型。</span><span class="sxs-lookup"><span data-stu-id="30104-215">The type of index.</span></span> <span data-ttu-id="30104-216">可能的值包括 **“聚集索引”** 、 **“非聚集索引”** 和 **“主 XML”** 。</span><span class="sxs-lookup"><span data-stu-id="30104-216">Possible values are **Clustered index**, **Nonclustered index**, and **Primary XML**.</span></span> <span data-ttu-id="30104-217">表也可以存储为堆（不带索引），但此后将无法打开此“索引属性”页。</span><span class="sxs-lookup"><span data-stu-id="30104-217">Tables can also be stored as a heap (without indexes), but then this Index Properties page cannot be opened.</span></span>  
  
     <span data-ttu-id="30104-218">**叶级行数**</span><span class="sxs-lookup"><span data-stu-id="30104-218">**Leaf-level rows**</span></span>  
     <span data-ttu-id="30104-219">叶级行的数目。</span><span class="sxs-lookup"><span data-stu-id="30104-219">The number of leaf level rows.</span></span>  
  
     <span data-ttu-id="30104-220">**最大行大小**</span><span class="sxs-lookup"><span data-stu-id="30104-220">**Maximum row size**</span></span>  
     <span data-ttu-id="30104-221">叶级行最大大小。</span><span class="sxs-lookup"><span data-stu-id="30104-221">The maximum leaf-level row size.</span></span>  
  
     <span data-ttu-id="30104-222">**最小行大小**</span><span class="sxs-lookup"><span data-stu-id="30104-222">**Minimum row size**</span></span>  
     <span data-ttu-id="30104-223">叶级行最小大小。</span><span class="sxs-lookup"><span data-stu-id="30104-223">The minimum leaf-level row size.</span></span>  
  
     <span data-ttu-id="30104-224">**页**</span><span class="sxs-lookup"><span data-stu-id="30104-224">**Pages**</span></span>  
     <span data-ttu-id="30104-225">数据页总数。</span><span class="sxs-lookup"><span data-stu-id="30104-225">The total number of data pages.</span></span>  
  
     <span data-ttu-id="30104-226">**分区 ID**</span><span class="sxs-lookup"><span data-stu-id="30104-226">**Partition ID**</span></span>  
     <span data-ttu-id="30104-227">包含该索引的 B 树的分区 ID。</span><span class="sxs-lookup"><span data-stu-id="30104-227">The partition ID of the b-tree containing the index.</span></span>  
  
     <span data-ttu-id="30104-228">**建立虚影行版本**</span><span class="sxs-lookup"><span data-stu-id="30104-228">**Version ghost rows**</span></span>  
     <span data-ttu-id="30104-229">由于某个快照隔离事务未完成而保留的虚影记录的数目。</span><span class="sxs-lookup"><span data-stu-id="30104-229">The number of ghost records that are being retained due to an outstanding snapshot isolation transaction.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedureFrag"></a> <span data-ttu-id="30104-230">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="30104-230">Using Transact-SQL</span></span>  
  
#### <a name="to-check-the-fragmentation-of-an-index"></a><span data-ttu-id="30104-231">检查索引的碎片</span><span class="sxs-lookup"><span data-stu-id="30104-231">To check the fragmentation of an index</span></span>  
  
1.  <span data-ttu-id="30104-232">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="30104-232">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="30104-233">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="30104-233">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="30104-234">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="30104-234">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Find the average fragmentation percentage of all indexes  
    -- in the HumanResources.Employee table.   
    SELECT a.index_id, name, avg_fragmentation_in_percent  
    FROM sys.dm_db_index_physical_stats (DB_ID(N'AdventureWorks2012'), OBJECT_ID(N'HumanResources.Employee'), NULL, NULL, NULL) AS a  
        JOIN sys.indexes AS b ON a.object_id = b.object_id AND a.index_id = b.index_id;   
    GO  
    ```  
  
     <span data-ttu-id="30104-235">上述语句可能会返回类似于以下内容的结果集。</span><span class="sxs-lookup"><span data-stu-id="30104-235">The statement above might return a result set similar to the following.</span></span>  
  
    ```  
    index_id    name                                                  avg_fragmentation_in_percent  
    ----------- ----------------------------------------------------- ----------------------------  
    1           PK_Employee_BusinessEntityID                          0  
    2           IX_Employee_OrganizationalNode                        0  
    3           IX_Employee_OrganizationalLevel_OrganizationalNode    0  
    5           AK_Employee_LoginID                                   66.6666666666667  
    6           AK_Employee_NationalIDNumber                          50  
    7           AK_Employee_rowguid                                   0  
  
    (6 row(s) affected)  
    ```  
  
 <span data-ttu-id="30104-236">有关详细信息，请参阅[sys.databases&#41;dm_db_index_physical_stats &#40;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="30104-236">For more information, see  [sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedureReorg"></a> <span data-ttu-id="30104-237">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="30104-237">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-reorganize-or-rebuild-an-index"></a><span data-ttu-id="30104-238">重新组织或重新生成索引</span><span class="sxs-lookup"><span data-stu-id="30104-238">To reorganize or rebuild an index</span></span>  
  
1.  <span data-ttu-id="30104-239">在“对象资源管理器”中，展开包含您要重新组织索引的表的数据库。</span><span class="sxs-lookup"><span data-stu-id="30104-239">In Object Explorer, Expand the database that contains the table on which you want to reorganize an index.</span></span>  
  
2.  <span data-ttu-id="30104-240">展开 **“表”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="30104-240">Expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="30104-241">展开要为其重新组织索引的表。</span><span class="sxs-lookup"><span data-stu-id="30104-241">Expand the table on which you want to reorganize an index.</span></span>  
  
4.  <span data-ttu-id="30104-242">展开 **“索引”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="30104-242">Expand the **Indexes** folder.</span></span>  
  
5.  <span data-ttu-id="30104-243">右键单击要重新组织的索引，然后选择 **“重新组织”** 。</span><span class="sxs-lookup"><span data-stu-id="30104-243">Right-click the index you want to reorganize and select **Reorganize**.</span></span>  
  
6.  <span data-ttu-id="30104-244">在 **“重新组织索引”** 对话框中，确认正确的索引位于 **“要重新组织的索引”** 网格中，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="30104-244">In the **Reorganize Indexes** dialog box, verify that the correct index is in the **Indexes to be reorganized** grid and click **OK**.</span></span>  
  
7.  <span data-ttu-id="30104-245">选中 **“压缩大型对象列数据”** 复选框，以指定也压缩所有包含大型对象 (LOB) 数据的页。</span><span class="sxs-lookup"><span data-stu-id="30104-245">Select the **Compact large object column data** check box to specify that all pages that contain large object (LOB) data are also compacted.</span></span>  
  
8.  <span data-ttu-id="30104-246">单击“确定” **。**</span><span class="sxs-lookup"><span data-stu-id="30104-246">Click **OK.**</span></span>  
  
#### <a name="to-reorganize-all-indexes-in-a-table"></a><span data-ttu-id="30104-247">重新组织表中的所有索引</span><span class="sxs-lookup"><span data-stu-id="30104-247">To reorganize all indexes in a table</span></span>  
  
1.  <span data-ttu-id="30104-248">在“对象资源管理器”中，展开包含您要重新组织索引的表的数据库。</span><span class="sxs-lookup"><span data-stu-id="30104-248">In Object Explorer, Expand the database that contains the table on which you want to reorganize the indexes.</span></span>  
  
2.  <span data-ttu-id="30104-249">展开 **“表”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="30104-249">Expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="30104-250">展开要为其重新组织索引的表。</span><span class="sxs-lookup"><span data-stu-id="30104-250">Expand the table on which you want to reorganize the indexes.</span></span>  
  
4.  <span data-ttu-id="30104-251">右键单击 **“索引”** 文件夹，然后选择 **“全部重新组织”** 。</span><span class="sxs-lookup"><span data-stu-id="30104-251">Right-click the **Indexes** folder and select **Reorganize All**.</span></span>  
  
5.  <span data-ttu-id="30104-252">在 **“重新组织索引”** 对话框中，确认正确的索引位于 **“要重新组织的索引”** 中。</span><span class="sxs-lookup"><span data-stu-id="30104-252">In the **Reorganize Indexes** dialog box, verify that the correct indexes are in the **Indexes to be reorganized**.</span></span> <span data-ttu-id="30104-253">若要从 **“要重新组织的索引”** 网格中删除索引，请选择该索引，再按 Delete 键。</span><span class="sxs-lookup"><span data-stu-id="30104-253">To remove an index from the **Indexes to be reorganized** grid, select the index and then press the Delete key.</span></span>  
  
6.  <span data-ttu-id="30104-254">选中 **“压缩大型对象列数据”** 复选框，以指定也压缩所有包含大型对象 (LOB) 数据的页。</span><span class="sxs-lookup"><span data-stu-id="30104-254">Select the **Compact large object column data** check box to specify that all pages that contain large object (LOB) data are also compacted.</span></span>  
  
7.  <span data-ttu-id="30104-255">单击“确定” **。**</span><span class="sxs-lookup"><span data-stu-id="30104-255">Click **OK.**</span></span>  
  
#### <a name="to-rebuild-an-index"></a><span data-ttu-id="30104-256">重新生成索引</span><span class="sxs-lookup"><span data-stu-id="30104-256">To rebuild an index</span></span>  
  
1.  <span data-ttu-id="30104-257">在“对象资源管理器”中，展开包含您要重新组织索引的表的数据库。</span><span class="sxs-lookup"><span data-stu-id="30104-257">In Object Explorer, Expand the database that contains the table on which you want to reorganize an index.</span></span>  
  
2.  <span data-ttu-id="30104-258">展开 **“表”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="30104-258">Expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="30104-259">展开要为其重新组织索引的表。</span><span class="sxs-lookup"><span data-stu-id="30104-259">Expand the table on which you want to reorganize an index.</span></span>  
  
4.  <span data-ttu-id="30104-260">展开 **“索引”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="30104-260">Expand the **Indexes** folder.</span></span>  
  
5.  <span data-ttu-id="30104-261">右键单击要重新组织的索引，然后选择 **“重新组织”** 。</span><span class="sxs-lookup"><span data-stu-id="30104-261">Right-click the index you want to reorganize and select **Reorganize**.</span></span>  
  
6.  <span data-ttu-id="30104-262">在 **“重新生成索引”** 对话框中，确认正确的索引位于 **“要重新生成的索引”** 网格中，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="30104-262">In the **Rebuild Indexes** dialog box, verify that the correct index is in the **Indexes to be rebuilt** grid and click **OK**.</span></span>  
  
7.  <span data-ttu-id="30104-263">选中 **“压缩大型对象列数据”** 复选框，以指定也压缩所有包含大型对象 (LOB) 数据的页。</span><span class="sxs-lookup"><span data-stu-id="30104-263">Select the **Compact large object column data** check box to specify that all pages that contain large object (LOB) data are also compacted.</span></span>  
  
8.  <span data-ttu-id="30104-264">单击“确定” **。**</span><span class="sxs-lookup"><span data-stu-id="30104-264">Click **OK.**</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedureReorg"></a> <span data-ttu-id="30104-265">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="30104-265">Using Transact-SQL</span></span>  
  
#### <a name="to-reorganize-a-defragmented-index"></a><span data-ttu-id="30104-266">重新组织碎片索引</span><span class="sxs-lookup"><span data-stu-id="30104-266">To reorganize a defragmented index</span></span>  
  
1.  <span data-ttu-id="30104-267">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="30104-267">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="30104-268">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="30104-268">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="30104-269">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="30104-269">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    -- Reorganize the IX_Employee_OrganizationalLevel_OrganizationalNode index on the HumanResources.Employee table.   
  
    ALTER INDEX IX_Employee_OrganizationalLevel_OrganizationalNode ON HumanResources.Employee  
    REORGANIZE ;   
    GO  
    ```  
  
#### <a name="to-reorganize-all-indexes-in-a-table"></a><span data-ttu-id="30104-270">重新组织表中的所有索引</span><span class="sxs-lookup"><span data-stu-id="30104-270">To reorganize all indexes in a table</span></span>  
  
1.  <span data-ttu-id="30104-271">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="30104-271">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="30104-272">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="30104-272">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="30104-273">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="30104-273">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    -- Reorganize all indexes on the HumanResources.Employee table.  
    ALTER INDEX ALL ON HumanResources.Employee  
    REORGANIZE ;   
    GO  
    ```  
  
#### <a name="to-rebuild-a-defragmented-index"></a><span data-ttu-id="30104-274">重新生成碎片索引</span><span class="sxs-lookup"><span data-stu-id="30104-274">To rebuild a defragmented index</span></span>  
  
1.  <span data-ttu-id="30104-275">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="30104-275">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="30104-276">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="30104-276">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="30104-277">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="30104-277">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="30104-278">该示例在 `Employee` 表中重新生成单个索引。</span><span class="sxs-lookup"><span data-stu-id="30104-278">The example rebuilds a single index on the `Employee` table.</span></span>  
  
     [!code-sql[IndexDDL#AlterIndex1](../../snippets/tsql/SQL14/tsql/indexddl/transact-sql/alterindex.sql#alterindex1)]  
  
#### <a name="to-rebuild-all-indexes-in-a-table"></a><span data-ttu-id="30104-279">重新生成表中的所有索引</span><span class="sxs-lookup"><span data-stu-id="30104-279">To rebuild all indexes in a table</span></span>  
  
1.  <span data-ttu-id="30104-280">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="30104-280">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="30104-281">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="30104-281">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="30104-282">复制以下示例并将其粘贴到查询中，该示例指定了 `ALL`关键字。</span><span class="sxs-lookup"><span data-stu-id="30104-282">Copy and paste the following example into the query The example specifies the keyword `ALL`.</span></span> <span data-ttu-id="30104-283">这将重新生成与表相关联的所有索引。</span><span class="sxs-lookup"><span data-stu-id="30104-283">This rebuilds all indexes associated with the table.</span></span> <span data-ttu-id="30104-284">其中指定了三个选项。</span><span class="sxs-lookup"><span data-stu-id="30104-284">Three options are specified.</span></span>  
  
     [!code-sql[IndexDDL#AlterIndex2](../../snippets/tsql/SQL14/tsql/indexddl/transact-sql/alterindex.sql#alterindex2)]  
  
 <span data-ttu-id="30104-285">有关详细信息，请参阅 [ALTER INDEX (Transact-SQL)](/sql/t-sql/statements/alter-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="30104-285">For more information, see [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30104-286">另请参阅</span><span class="sxs-lookup"><span data-stu-id="30104-286">See Also</span></span>  
 [<span data-ttu-id="30104-287">Microsoft SQL Server 2000 索引碎片整理最佳实践</span><span class="sxs-lookup"><span data-stu-id="30104-287">Microsoft SQL Server 2000 Index Defragmentation Best Practices</span></span>](https://technet.microsoft.com/library/cc966523.aspx)  
  
  
