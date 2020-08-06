---
title: 索引 DDL 操作的磁盘空间要求 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- disk space [SQL Server], indexes
- index disk space [SQL Server]
- space [SQL Server], indexes
- indexes [SQL Server], disk space requirements
- temporary disk space [SQL Server]
ms.assetid: 35930826-c870-44c1-a966-a6a4638f62ef
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4ac25fc1555d6b6cfd8ee97b50d261cf5788f587
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590806"
---
# <a name="disk-space-requirements-for-index-ddl-operations"></a><span data-ttu-id="6edaf-102">Disk Space Requirements for Index DDL Operations</span><span class="sxs-lookup"><span data-stu-id="6edaf-102">Disk Space Requirements for Index DDL Operations</span></span>
  <span data-ttu-id="6edaf-103">磁盘空间是创建、重新生成或删除索引时所需考虑的重要因素。</span><span class="sxs-lookup"><span data-stu-id="6edaf-103">Disk space is an important consideration when you create, rebuild, or drop indexes.</span></span> <span data-ttu-id="6edaf-104">磁盘空间不足会降低性能，甚至导致索引操作失败。</span><span class="sxs-lookup"><span data-stu-id="6edaf-104">Inadequate disk space can degrade performance or even cause the index operation to fail.</span></span> <span data-ttu-id="6edaf-105">本主题提供了有助于确定索引数据定义语言 (DDL) 操作所需的磁盘空间量的一般信息。</span><span class="sxs-lookup"><span data-stu-id="6edaf-105">This topic provides general information that can help you determine the amount of disk space required for index data definition language (DDL) operations.</span></span>  
  
## <a name="index-operations-that-require-no-additional-disk-space"></a><span data-ttu-id="6edaf-106">不需要额外的磁盘空间的索引操作</span><span class="sxs-lookup"><span data-stu-id="6edaf-106">Index Operations That Require No Additional Disk Space</span></span>  
 <span data-ttu-id="6edaf-107">以下索引操作不需要额外的磁盘空间：</span><span class="sxs-lookup"><span data-stu-id="6edaf-107">The following index operations require no additional disk space:</span></span>  
  
-   <span data-ttu-id="6edaf-108">ALTER INDEX REORGANIZE（但是需要日志空间）。</span><span class="sxs-lookup"><span data-stu-id="6edaf-108">ALTER INDEX REORGANIZE; however, log space is required.</span></span>  
  
-   <span data-ttu-id="6edaf-109">DROP INDEX（当删除非聚集索引时）。</span><span class="sxs-lookup"><span data-stu-id="6edaf-109">DROP INDEX when you are dropping a nonclustered index.</span></span>  
  
-   <span data-ttu-id="6edaf-110">DROP INDEX（当删除脱机聚集索引而没有指定 MOVE TO 子句并且不存在非聚集索引时）。</span><span class="sxs-lookup"><span data-stu-id="6edaf-110">DROP INDEX when you are dropping a clustered index offline without specifying the MOVE TO clause and nonclustered indexes do not exist.</span></span>  
  
-   <span data-ttu-id="6edaf-111">CREATE TABLE（PRIMARY KEY 或 UNIQUE 约束）</span><span class="sxs-lookup"><span data-stu-id="6edaf-111">CREATE TABLE (PRIMARY KEY or UNIQUE constraints)</span></span>  
  
## <a name="index-operations-that-require-additional-disk-space"></a><span data-ttu-id="6edaf-112">需要额外的磁盘空间的索引操作</span><span class="sxs-lookup"><span data-stu-id="6edaf-112">Index Operations That Require Additional Disk Space</span></span>  
 <span data-ttu-id="6edaf-113">其他所有 DDL 操作都需要在操作期间使用额外的临时磁盘空间，并需要永久磁盘空间来存储新的索引结构。</span><span class="sxs-lookup"><span data-stu-id="6edaf-113">All other index DDL operations require additional temporary disk space to use during the operation, and permanent disk space to store the new index structure or structures.</span></span>  
  
 <span data-ttu-id="6edaf-114">创建新的索引结构后，旧（源）结构和新（目标）结构在其相应的文件或文件组中都需要一定的磁盘空间。</span><span class="sxs-lookup"><span data-stu-id="6edaf-114">When a new index structure is created, disk space for both the old (source) and new (target) structures is required in their appropriate files and filegroups.</span></span> <span data-ttu-id="6edaf-115">旧的结构只有在提交索引创建事务后才会释放。</span><span class="sxs-lookup"><span data-stu-id="6edaf-115">The old structure is not deallocated until the index creation transaction commits.</span></span>  
  
 <span data-ttu-id="6edaf-116">以下索引 DDL 操作将创建新的索引结构并需要额外的磁盘空间：</span><span class="sxs-lookup"><span data-stu-id="6edaf-116">The following index DDL operations create new index structures and require additional disk space:</span></span>  
  
-   <span data-ttu-id="6edaf-117">CREATE INDEX</span><span class="sxs-lookup"><span data-stu-id="6edaf-117">CREATE INDEX</span></span>  
  
-   <span data-ttu-id="6edaf-118">CREATE INDEX WITH DROP_EXISTING</span><span class="sxs-lookup"><span data-stu-id="6edaf-118">CREATE INDEX WITH DROP_EXISTING</span></span>  
  
-   <span data-ttu-id="6edaf-119">ALTER INDEX REBUILD</span><span class="sxs-lookup"><span data-stu-id="6edaf-119">ALTER INDEX REBUILD</span></span>  
  
-   <span data-ttu-id="6edaf-120">ALTER TABLE ADD CONSTRAINT（PRIMARY KEY 或 UNIQUE 约束）</span><span class="sxs-lookup"><span data-stu-id="6edaf-120">ALTER TABLE ADD CONSTRAINT (PRIMARY KEY or UNIQUE)</span></span>  
  
-   <span data-ttu-id="6edaf-121">ALTER TABLE DROP CONSTRAINT（PRIMARY KEY 或 UNIQUE）（当约束基于聚集索引时）</span><span class="sxs-lookup"><span data-stu-id="6edaf-121">ALTER TABLE DROP CONSTRAINT (PRIMARY KEY or UNIQUE) when the constraint is based on a clustered index</span></span>  
  
-   <span data-ttu-id="6edaf-122">DROP INDEX MOVE TO（仅适用于聚集索引。）</span><span class="sxs-lookup"><span data-stu-id="6edaf-122">DROP INDEX MOVE TO (Applies only to clustered indexes.)</span></span>  
  
## <a name="temporary-disk-space-for-sorting"></a><span data-ttu-id="6edaf-123">进行排序所需的临时磁盘空间</span><span class="sxs-lookup"><span data-stu-id="6edaf-123">Temporary Disk Space for Sorting</span></span>  
 <span data-ttu-id="6edaf-124">除了源结构和目标结构所需的磁盘空间以外，还需要一定的临时磁盘空间以进行排序，除非查询优化器找到了不需要进行排序的执行计划。</span><span class="sxs-lookup"><span data-stu-id="6edaf-124">Besides the disk space required for the source and target structures, temporary disk space is required for sorting, unless the query optimizer finds an execution plan that does not require sorting.</span></span>  
  
 <span data-ttu-id="6edaf-125">如果需要进行排序，则每次创建一个新索引时都要进行排序。</span><span class="sxs-lookup"><span data-stu-id="6edaf-125">If sorting is required, sorting occurs one new index at a time.</span></span> <span data-ttu-id="6edaf-126">例如，在单个语句中重新生成聚集索引和相关联的非聚集索引时，将逐个对索引进行排序。</span><span class="sxs-lookup"><span data-stu-id="6edaf-126">For example, when you rebuild a clustered index and associated nonclustered indexes within a single statement, the indexes are sorted one after the other.</span></span> <span data-ttu-id="6edaf-127">因此，进行排序所需的额外的临时磁盘空间只需与操作中最大的索引一样大。</span><span class="sxs-lookup"><span data-stu-id="6edaf-127">Therefore, the additional temporary disk space that is required for sorting only has to be as large as the largest index in the operation.</span></span> <span data-ttu-id="6edaf-128">这个最大索引几乎总是聚集索引。</span><span class="sxs-lookup"><span data-stu-id="6edaf-128">This is almost always the clustered index.</span></span>  
  
 <span data-ttu-id="6edaf-129">如果将 SORT_IN_TEMPDB 选项设置为 ON，则最大索引必须可由 **tempdb**容纳。</span><span class="sxs-lookup"><span data-stu-id="6edaf-129">If the SORT_IN_TEMPDB option is set to ON, the largest index must fit into **tempdb**.</span></span> <span data-ttu-id="6edaf-130">虽然此选项会增加用于创建索引的临时磁盘空间量，但是如果 **tempdb** 与用户数据库位于不同的磁盘集上时，此选项可减少创建索引所需的时间。</span><span class="sxs-lookup"><span data-stu-id="6edaf-130">Although this option increases the amount of temporary disk space that is used to create an index, it may reduce the time that is required to create an index when **tempdb** is on a set of disks different from the user database.</span></span>  
  
 <span data-ttu-id="6edaf-131">如果 SORT_IN_TEMPDB 设置为 OFF（默认值），则每个索引（包括已分区索引）都将在其目标磁盘空间中进行排序；只有新的索引结构需要占用磁盘空间。</span><span class="sxs-lookup"><span data-stu-id="6edaf-131">If SORT_IN_TEMPDB is set to OFF (the default) each index, including partitioned indexes, is sorted in its destination disk space; and only the disk space for the new index structures is required.</span></span>  
  
 <span data-ttu-id="6edaf-132">有关计算磁盘空间的示例，请参阅 [Index Disk Space Example](index-disk-space-example.md)。</span><span class="sxs-lookup"><span data-stu-id="6edaf-132">For an example of calculating disk space, see [Index Disk Space Example](index-disk-space-example.md).</span></span>  
  
## <a name="temporary-disk-space-for-online-index-operations"></a><span data-ttu-id="6edaf-133">联机索引操作所需的临时磁盘空间</span><span class="sxs-lookup"><span data-stu-id="6edaf-133">Temporary Disk Space for Online Index Operations</span></span>  
 <span data-ttu-id="6edaf-134">执行联机索引操作时，需要额外的临时磁盘空间。</span><span class="sxs-lookup"><span data-stu-id="6edaf-134">When you perform index operations online, additional temporary disk space is required.</span></span>  
  
 <span data-ttu-id="6edaf-135">如果联机创建、重新生成或删除了聚集索引，将创建临时非聚集索引以便把旧书签映射到新书签。</span><span class="sxs-lookup"><span data-stu-id="6edaf-135">If a clustered index is created, rebuilt, or dropped online, a temporary nonclustered index is created to map old bookmarks to new bookmarks.</span></span> <span data-ttu-id="6edaf-136">如果将 SORT_IN_TEMPDB 选项设置为 ON，则将在 **tempdb**中创建此临时索引。</span><span class="sxs-lookup"><span data-stu-id="6edaf-136">If the SORT_IN_TEMPDB option is set to ON, this temporary index is created in **tempdb**.</span></span> <span data-ttu-id="6edaf-137">如果 SORT_IN_TEMPDB 设置为 OFF，将使用与目标索引相同的文件组或分区方案。</span><span class="sxs-lookup"><span data-stu-id="6edaf-137">If SORT_IN_TEMPDB is set to OFF, the same filegroup or partition scheme as the target index is used.</span></span> <span data-ttu-id="6edaf-138">临时映射索引针对表中的每行包含一个记录，其内容为新旧书签列，其中包括 uniqueifier 和记录标识符，并且仅包括两种书签中使用的任何列的单个副本。</span><span class="sxs-lookup"><span data-stu-id="6edaf-138">The temporary mapping index contains one record for each row in the table, and its contents is the union of the old and new bookmark columns, including uniqueifiers and record identifiers and including only a single copy of any column used in both bookmarks.</span></span> <span data-ttu-id="6edaf-139">有关联机索引操作的详细信息，请参阅 [联机执行索引操作](perform-index-operations-online.md)。</span><span class="sxs-lookup"><span data-stu-id="6edaf-139">For more information about online index operations, see [Perform Index Operations Online](perform-index-operations-online.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6edaf-140">不能为 DROP INDEX 语句设置 SORT_IN_TEMPDB 选项。</span><span class="sxs-lookup"><span data-stu-id="6edaf-140">The SORT_IN_TEMPDB option cannot be set for DROP INDEX statements.</span></span> <span data-ttu-id="6edaf-141">临时映射索引始终与目标索引创建在同一文件组或分区方案中。</span><span class="sxs-lookup"><span data-stu-id="6edaf-141">The temporary mapping index is always created in the same filegroup or partition scheme as the target index.</span></span>  
  
 <span data-ttu-id="6edaf-142">联机索引操作使用行版本控制来使索引操作不受其他事务所做的修改的影响。</span><span class="sxs-lookup"><span data-stu-id="6edaf-142">Online index operations use row versioning to isolate the index operation from the effects of modifications made by other transactions.</span></span> <span data-ttu-id="6edaf-143">这就不需要对已经读取的行请求共享锁。</span><span class="sxs-lookup"><span data-stu-id="6edaf-143">This avoids the need for requesting share locks on rows that have been read.</span></span> <span data-ttu-id="6edaf-144">在联机索引操作期间，并发的用户更新和删除操作需要一定的空间以用于 **tempdb**中的版本记录。</span><span class="sxs-lookup"><span data-stu-id="6edaf-144">Concurrent user update and delete operations during online index operations require space for version records in **tempdb**.</span></span> <span data-ttu-id="6edaf-145">有关详细信息，请参阅 [联机索引操作](perform-index-operations-online.md) 。</span><span class="sxs-lookup"><span data-stu-id="6edaf-145">For more information, see [Perform Index Operations Online](perform-index-operations-online.md) .</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="6edaf-146">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="6edaf-146">Related Tasks</span></span>  
 [<span data-ttu-id="6edaf-147">索引磁盘空间示例</span><span class="sxs-lookup"><span data-stu-id="6edaf-147">Index Disk Space Example</span></span>](index-disk-space-example.md)  
  
 [<span data-ttu-id="6edaf-148">索引操作的事务日志磁盘空间</span><span class="sxs-lookup"><span data-stu-id="6edaf-148">Transaction Log Disk Space for Index Operations</span></span>](transaction-log-disk-space-for-index-operations.md)  
  
 [<span data-ttu-id="6edaf-149">估计表的大小</span><span class="sxs-lookup"><span data-stu-id="6edaf-149">Estimate the Size of a Table</span></span>](../databases/estimate-the-size-of-a-table.md)  
  
 [<span data-ttu-id="6edaf-150">估计聚集索引的大小</span><span class="sxs-lookup"><span data-stu-id="6edaf-150">Estimate the Size of a Clustered Index</span></span>](../databases/estimate-the-size-of-a-clustered-index.md)  
  
 [<span data-ttu-id="6edaf-151">估计非聚集索引的大小</span><span class="sxs-lookup"><span data-stu-id="6edaf-151">Estimate the Size of a Nonclustered Index</span></span>](../databases/estimate-the-size-of-a-nonclustered-index.md)  
  
 [<span data-ttu-id="6edaf-152">估计堆的大小</span><span class="sxs-lookup"><span data-stu-id="6edaf-152">Estimate the Size of a Heap</span></span>](../databases/estimate-the-size-of-a-heap.md)  
  
## <a name="related-content"></a><span data-ttu-id="6edaf-153">相关内容</span><span class="sxs-lookup"><span data-stu-id="6edaf-153">Related Content</span></span>  
 [<span data-ttu-id="6edaf-154">CREATE INDEX (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6edaf-154">CREATE INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-index-transact-sql)  
  
 [<span data-ttu-id="6edaf-155">ALTER INDEX (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6edaf-155">ALTER INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-index-transact-sql)  
  
 [<span data-ttu-id="6edaf-156">DROP INDEX (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6edaf-156">DROP INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-index-transact-sql)  
  
 [<span data-ttu-id="6edaf-157">为索引指定填充因子</span><span class="sxs-lookup"><span data-stu-id="6edaf-157">Specify Fill Factor for an Index</span></span>](specify-fill-factor-for-an-index.md)  
  
 [<span data-ttu-id="6edaf-158">重新组织和重新生成索引</span><span class="sxs-lookup"><span data-stu-id="6edaf-158">Reorganize and Rebuild Indexes</span></span>](indexes.md)  
  
  
