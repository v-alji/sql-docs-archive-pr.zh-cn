---
title: 估算内存优化表的内存需求 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 5c5cc1fc-1fdf-4562-9443-272ad9ab5ba8
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5c5218a96d3650cbae22501ab2794b1b553996b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692410"
---
# <a name="estimate-memory-requirements-for-memory-optimized-tables"></a><span data-ttu-id="9697e-102">估算内存优化表的内存需求</span><span class="sxs-lookup"><span data-stu-id="9697e-102">Estimate Memory Requirements for Memory-Optimized Tables</span></span>
  <span data-ttu-id="9697e-103">无论是创建新的 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 内存优化表，还是将现有的基于磁盘的表迁移到内存优化表，都一定要合理估计每个表的内存需求，以便能够将服务器设置为具有足够的内存。</span><span class="sxs-lookup"><span data-stu-id="9697e-103">Whether you are creating a new [!INCLUDE[hek_2](../../includes/hek-2-md.md)] memory-optimized table or migrating an existing disk-based table to a memory-optimized table, it is important to have a reasonable estimate of each table's memory needs so you can provision the server with sufficient memory.</span></span> <span data-ttu-id="9697e-104">本节介绍如何估算使用内存优化表存放数据时所需的内存大小。</span><span class="sxs-lookup"><span data-stu-id="9697e-104">This section describes how to estimate the amount of memory that you need to hold data for a memory-optimized table.</span></span>  
  
 <span data-ttu-id="9697e-105">如果考虑从基于磁盘的表迁移至内存优化表，在继续阅读本主题前，请先阅读主题 [确定表或存储过程是否应移植到内存中 OLTP](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md) ，了解哪类表适合迁移。</span><span class="sxs-lookup"><span data-stu-id="9697e-105">If you are contemplating migrating from disk-based tables to memory-optimized tables, before you proceed in this topic, see the topic [Determining if a Table or Stored Procedure Should Be Ported to In-Memory OLTP](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md) for guidance on which tables are best to migrate.</span></span> <span data-ttu-id="9697e-106">[迁移到内存中 OLTP](migrating-to-in-memory-oltp.md) 下的所有主题均提供了有关从基于磁盘的表迁移至内存优化表的指导。</span><span class="sxs-lookup"><span data-stu-id="9697e-106">All the topics under [Migrating to In-Memory OLTP](migrating-to-in-memory-oltp.md) provide guidance on migrating from disk-based to memory-optimized tables.</span></span>  
  
## <a name="sections-in-this-topic"></a><span data-ttu-id="9697e-107">本主题的内容</span><span class="sxs-lookup"><span data-stu-id="9697e-107">Sections in this topic</span></span>  
  
-   [<span data-ttu-id="9697e-108">内存优化表示例</span><span class="sxs-lookup"><span data-stu-id="9697e-108">Example memory-optimized table</span></span>](#bkmk_ExampleTable)  
  
-   [<span data-ttu-id="9697e-109">表占用的内存</span><span class="sxs-lookup"><span data-stu-id="9697e-109">Memory for the table</span></span>](#bkmk_MemoryForTable)  
  
-   [<span data-ttu-id="9697e-110">索引占用的内存</span><span class="sxs-lookup"><span data-stu-id="9697e-110">Memory for indexes</span></span>](#bkmk_IndexMeemory)  
  
-   [<span data-ttu-id="9697e-111">行版本控制占用的内存</span><span class="sxs-lookup"><span data-stu-id="9697e-111">Memory for row versioning</span></span>](#bkmk_MemoryForRowVersions)  
  
-   [<span data-ttu-id="9697e-112">表变量占用的内存</span><span class="sxs-lookup"><span data-stu-id="9697e-112">Memory for table variables</span></span>](#bkmk_TableVariables)  
  
-   [<span data-ttu-id="9697e-113">表增长占用的内存</span><span class="sxs-lookup"><span data-stu-id="9697e-113">Memory for growth</span></span>](#bkmk_MemoryForGrowth)  
  
##  <a name="example-memory-optimized-table"></a><a name="bkmk_ExampleTable"></a> <span data-ttu-id="9697e-114">内存优化表示例</span><span class="sxs-lookup"><span data-stu-id="9697e-114">Example memory-optimized table</span></span>  
 <span data-ttu-id="9697e-115">考虑以下内存优化的表架构：</span><span class="sxs-lookup"><span data-stu-id="9697e-115">Consider the following memory-optimized table schema:</span></span>  
  
```sql  
  
CREATE TABLE t_hk (  
col1 int NOT NULL PRIMARY KEY NONCLUSTERED,  
col2 int NOT NULL INDEX t1c2_index   
     HASH WITH (bucket_count = 5000000),  
col3 int NOT NULL INDEX t1c3_index   
     HASH WITH (bucket_count = 5000000),  
col4 int NOT NULL INDEX t1c4_index   
     HASH WITH (bucket_count = 5000000),  
col5 int NOT NULL INDEX t1c5_index NONCLUSTERED,  
col6 char (50) NOT NULL,  
col7 char (50) NOT NULL,   
col8 char (30) NOT NULL,   
col9 char (50) NOT NULL  
     WITH (memory_optimized = on)  
GO  
  
```  
  
 <span data-ttu-id="9697e-116">我们将使用该架构来确定此内存优化表所需的最低内存。</span><span class="sxs-lookup"><span data-stu-id="9697e-116">Using this schema we will determine the minimum memory needed for this memory-optimized table.</span></span>  
  
##  <a name="memory-for-the-table"></a><a name="bkmk_MemoryForTable"></a> <span data-ttu-id="9697e-117">表占用的内存</span><span class="sxs-lookup"><span data-stu-id="9697e-117">Memory for the table</span></span>  
 <span data-ttu-id="9697e-118">内存优化表行包含三个部分：</span><span class="sxs-lookup"><span data-stu-id="9697e-118">A memory-optimized table row is comprised of three parts:</span></span>  
  
-   <span data-ttu-id="9697e-119">**时间戳** </span><span class="sxs-lookup"><span data-stu-id="9697e-119">**Timestamps** </span></span>  
    <span data-ttu-id="9697e-120">行标题/时间戳 = 24 个字节。</span><span class="sxs-lookup"><span data-stu-id="9697e-120">Row header/timestamps = 24 bytes.</span></span>  
  
-   <span data-ttu-id="9697e-121">**索引指针** </span><span class="sxs-lookup"><span data-stu-id="9697e-121">**Index pointers** </span></span>  
    <span data-ttu-id="9697e-122">对于表中的每个哈希索引，每行包含一个指向索引中下一行的 8 字节地址指针。</span><span class="sxs-lookup"><span data-stu-id="9697e-122">For each hash index in the table, each row has an 8-byte address pointer to the next row in the index.</span></span>  <span data-ttu-id="9697e-123">因为有 4 个索引，每行将为索引指针分配 32 个字节（每个索引需要一个 8 字节的指针）。</span><span class="sxs-lookup"><span data-stu-id="9697e-123">Since there are 4 indexes, each row will allocate 32 bytes for index pointers (an 8 byte pointer for each index).</span></span>  
  
-   <span data-ttu-id="9697e-124">**数据** </span><span class="sxs-lookup"><span data-stu-id="9697e-124">**Data** </span></span>  
    <span data-ttu-id="9697e-125">行中数据部分的大小由各数据列类型大小的总和决定。</span><span class="sxs-lookup"><span data-stu-id="9697e-125">The size of the data portion of the row is determined by summing the type size for each data column.</span></span>  <span data-ttu-id="9697e-126">示例表中包含五个 4 字节整数、三个 50 字节的字符列和一个 30 字节的字符列。</span><span class="sxs-lookup"><span data-stu-id="9697e-126">In our table we have five 4-byte integers, three 50-byte character columns, and one 30-byte character column.</span></span>  <span data-ttu-id="9697e-127">因此，每行的数据部分为 4 + 4 + 4 + 4 + 4 + 50 + 50 + 30 + 50 共 200 个字节。</span><span class="sxs-lookup"><span data-stu-id="9697e-127">Therefore the data portion of each row is 4 + 4 + 4 + 4 + 4 + 50 + 50 + 30 + 50 or 200 bytes.</span></span>  
  
 <span data-ttu-id="9697e-128">下面是内存优化表中 5,000,000（5 百万）行的大小计算：</span><span class="sxs-lookup"><span data-stu-id="9697e-128">The following is a size computation for 5,000,000 (5 million) rows in a memory-optimized table.</span></span> <span data-ttu-id="9697e-129">按以下方式估计数据行使用的总内存：</span><span class="sxs-lookup"><span data-stu-id="9697e-129">The total memory used by data rows is estimated as follows:</span></span>  
  
 <span data-ttu-id="9697e-130">**表行占用的内存**</span><span class="sxs-lookup"><span data-stu-id="9697e-130">**Memory for the table's rows**</span></span>  
  
 <span data-ttu-id="9697e-131">根据上述计算，内存优化表中每行的大小为 24 + 32 + 200，即 256 个字节。</span><span class="sxs-lookup"><span data-stu-id="9697e-131">From the above calculations, the size of each row in the memory-optimized table is 24 + 32 + 200, or 256 bytes.</span></span>  <span data-ttu-id="9697e-132">总共有 5 百万行，则表将占用 5,000,000 \* 256 字节，共 1,280,000,000 字节 - 大约 1.28 GB。</span><span class="sxs-lookup"><span data-stu-id="9697e-132">Since we have 5 million rows, the table will consume 5,000,000 \* 256 bytes, or 1,280,000,000 bytes - approximately 1.28 GB.</span></span>  
  
##  <a name="memory-for-indexes"></a><a name="bkmk_IndexMeemory"></a> <span data-ttu-id="9697e-133">索引占用的内存</span><span class="sxs-lookup"><span data-stu-id="9697e-133">Memory for indexes</span></span>  
 <span data-ttu-id="9697e-134">**每个哈希索引占用的内存**</span><span class="sxs-lookup"><span data-stu-id="9697e-134">**Memory for each hash index**</span></span>  
  
 <span data-ttu-id="9697e-135">每个哈希索引是一个由 8 字节地址指针组成的哈希数组。</span><span class="sxs-lookup"><span data-stu-id="9697e-135">Each hash index is a hash array of 8-byte address pointers.</span></span>  <span data-ttu-id="9697e-136">该数组的大小最好通过索引中唯一索引键的数目确定，例如：使用唯一 Col2 键的个数作为 t1c2_index 的数组大小。</span><span class="sxs-lookup"><span data-stu-id="9697e-136">The size of the array is best determined by the number of unique index values for that index - e.g., the number of unique Col2 values is a good starting point for the array size for the t1c2_index.</span></span> <span data-ttu-id="9697e-137">哈希数组太大，浪费内存。</span><span class="sxs-lookup"><span data-stu-id="9697e-137">A hash array that is too big wastes memory.</span></span>  <span data-ttu-id="9697e-138">哈希数组太小，又会降低性能（许多索引键经哈希操作后映射至同一索引，导致冲突过多）。</span><span class="sxs-lookup"><span data-stu-id="9697e-138">A hash array that is too small slows performance since there will be too many collisions by index values that hash to the same index.</span></span>  
  
 <span data-ttu-id="9697e-139">哈希索引可实现高速查找，如：</span><span class="sxs-lookup"><span data-stu-id="9697e-139">Hash indexes achieve very fast equality lookups such as:</span></span>  
  
```sql  
  
SELECT * FROM t_hk  
   WHERE Col2 = 3  
  
```  
  
 <span data-ttu-id="9697e-140">非聚集索引在执行范围查找时更快，如：</span><span class="sxs-lookup"><span data-stu-id="9697e-140">Nonclustered indexes are faster for range lookups such as:</span></span>  
  
```sql  
  
SELECT * FROM t_hk  
   WHERE Col2 >= 3  
  
```  
  
 <span data-ttu-id="9697e-141">如果是迁移磁盘表，可使用下面的方法确定索引 t1c2_index 的唯一键的个数。</span><span class="sxs-lookup"><span data-stu-id="9697e-141">If you are migrating a disk-based table you can use the following to determine the number of unique values for the index t1c2_index.</span></span>  
  
```sql  
  
SELECT COUNT(DISTINCT [Col2])  
  FROM t_hk  
  
```  
  
 <span data-ttu-id="9697e-142">如果是创建新表，则需要估算数组大小或在部署前通过测试收集数据。</span><span class="sxs-lookup"><span data-stu-id="9697e-142">If you are creating a new table, you'll need to estimate the array size or gather data from your testing prior to deployment.</span></span>  
  
 <span data-ttu-id="9697e-143">关于 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 内存优化表中哈希索引的工作原理，请参阅 [哈希索引](../../database-engine/hash-indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="9697e-143">For information on how hash indexes work in [!INCLUDE[hek_2](../../includes/hek-2-md.md)] memory-optimized tables, see [Hash Indexes](../../database-engine/hash-indexes.md).</span></span>  
  
 <span data-ttu-id="9697e-144">**注意：** 不能动态更改哈希索引数组大小。</span><span class="sxs-lookup"><span data-stu-id="9697e-144">**Note:** You cannot change the hash index array size on the fly.</span></span> <span data-ttu-id="9697e-145">要更改哈希索引数组的大小，必须删除表，更改 bucket_count 值，然后重新创建表。</span><span class="sxs-lookup"><span data-stu-id="9697e-145">To change the hash index array size you must drop the table, change the bucket_count value and recreate the table.</span></span>  
  
 <span data-ttu-id="9697e-146">**设置哈希索引数组的大小**</span><span class="sxs-lookup"><span data-stu-id="9697e-146">**Setting the hash index array size**</span></span>  
  
 <span data-ttu-id="9697e-147">哈希数组大小由 `(bucket_count= <value>)` 设置，其中 \<value> 为大于零的整数值。</span><span class="sxs-lookup"><span data-stu-id="9697e-147">The hash array size is set by `(bucket_count= <value>)` where \<value> is an integer value greater than zero.</span></span> <span data-ttu-id="9697e-148">如果 \<value> 不为 2 的幂，实际的 bucket_count 将舍入为下一个最近的 2 的幂。</span><span class="sxs-lookup"><span data-stu-id="9697e-148">If \<value> is not a power of 2, the actual bucket_count is rounded up to the next closest power of 2.</span></span>  <span data-ttu-id="9697e-149">在我们的示例表中， (bucket_count = 5000000) ，因为5000000不是2的幂，所以实际 bucket 计数向上舍入到 8388608 (2<sup>23</sup>) 。</span><span class="sxs-lookup"><span data-stu-id="9697e-149">In our example table, (bucket_count = 5000000), since 5,000,000 is not a power of 2, the actual bucket count rounds up to 8,388,608 (2<sup>23</sup>).</span></span>  <span data-ttu-id="9697e-150">在计算此哈希数组所需的内存时，必须使用该值，而非 5,000,000。</span><span class="sxs-lookup"><span data-stu-id="9697e-150">You must use this number, not 5,000,000 when calculating memory needed by the hash array.</span></span>  
  
 <span data-ttu-id="9697e-151">因此，在本示例中，每个哈希数组所需的内存为：</span><span class="sxs-lookup"><span data-stu-id="9697e-151">Thus, in our example, the memory needed for each hash array is:</span></span>  
  
 <span data-ttu-id="9697e-152">8388608 \* 8 = 2<sup>23</sup> \* 8 = 2<sup>23</sup> \* 2<sup>3</sup> = 2<sup>26</sup> = 67108864 或约 64 MB。</span><span class="sxs-lookup"><span data-stu-id="9697e-152">8,388,608 \* 8 = 2<sup>23</sup> \* 8 = 2<sup>23</sup> \* 2<sup>3</sup> = 2<sup>26</sup> = 67,108,864 or approximately 64 MB.</span></span>  
  
 <span data-ttu-id="9697e-153">有三个哈希索引，所以哈希索引占用的内存为 3 \* 64MB = 192MB。</span><span class="sxs-lookup"><span data-stu-id="9697e-153">Since we have three hash indexes, the memory needed for the hash indexes is 3 \* 64MB = 192MB.</span></span>  
  
 <span data-ttu-id="9697e-154">**非聚集索引占用的内存**</span><span class="sxs-lookup"><span data-stu-id="9697e-154">**Memory for nonclustered indexes**</span></span>  
  
 <span data-ttu-id="9697e-155">非聚集索引采用 B 树实现，其内部节点包含索引键和指向后续节点的指针。</span><span class="sxs-lookup"><span data-stu-id="9697e-155">Nonclustered indexes are implemented as BTrees with the inner nodes containing the index value and pointers to subsequent nodes.</span></span>  <span data-ttu-id="9697e-156">叶节点包含索引键和指向内存中表行的指针。</span><span class="sxs-lookup"><span data-stu-id="9697e-156">Leaf nodes contain the index value and a pointer to the table row in memory.</span></span>  
  
 <span data-ttu-id="9697e-157">与哈希索引不同的是，非聚集索引的 Bucket 大小不固定。</span><span class="sxs-lookup"><span data-stu-id="9697e-157">Unlike hash indexes, nonclustered indexes do not have a fixed bucket size.</span></span> <span data-ttu-id="9697e-158">非聚集索引随数据动态扩展/收缩。</span><span class="sxs-lookup"><span data-stu-id="9697e-158">The index grows and shrinks dynamically with the data.</span></span>  
  
 <span data-ttu-id="9697e-159">可按如下方式计算非聚集索引占用的内存：</span><span class="sxs-lookup"><span data-stu-id="9697e-159">Memory needed by nonclustered indexes can be computed as follows:</span></span>  
  
-   <span data-ttu-id="9697e-160">**为非叶节点分配的内存** </span><span class="sxs-lookup"><span data-stu-id="9697e-160">**Memory allocated to non-leaf nodes** </span></span>  
    <span data-ttu-id="9697e-161">对于典型配置，分配给非叶节点的内存只占索引所占用的整个内存的很小的百分比。</span><span class="sxs-lookup"><span data-stu-id="9697e-161">For a typical configuration, the memory allocated to non-leaf nodes is a small percentage of the overall memory taken by the index.</span></span> <span data-ttu-id="9697e-162">其占用的内存少到可以安全地忽略。</span><span class="sxs-lookup"><span data-stu-id="9697e-162">This is so small it can safely be ignored.</span></span>  
  
-   <span data-ttu-id="9697e-163">**叶节点占用的内存** </span><span class="sxs-lookup"><span data-stu-id="9697e-163">**Memory for leaf nodes** </span></span>  
    <span data-ttu-id="9697e-164">叶节点对于表中的每个唯一键都具有 1 行，并且指向具有该唯一键的数据行。</span><span class="sxs-lookup"><span data-stu-id="9697e-164">The leaf nodes have one row for each unique key in the table that points to the data rows with that unique key.</span></span>  <span data-ttu-id="9697e-165">如果多行具有相同的键（即，存在不唯一的非聚集索引），则索引页节点中只有一行指向其中某一行，其他行则相互链接在一起。</span><span class="sxs-lookup"><span data-stu-id="9697e-165">If you have multiple rows with the same key (i.e., you have a non-unique nonclustered index), there is only one row in the index leaf node that points to one of the rows with the other rows linked to each other.</span></span>  <span data-ttu-id="9697e-166">因此，可通过下面的公式估算所需的总内存：</span><span class="sxs-lookup"><span data-stu-id="9697e-166">Thus, the total memory required can be approximated by:</span></span>   
    <span data-ttu-id="9697e-167">非聚集索引所需内存 = （指针大小 + Sum (键列数据类型大小))\* 唯一键行数</span><span class="sxs-lookup"><span data-stu-id="9697e-167">memoryForNonClusteredIndex = (pointerSize + sum(keyColumnDataTypeSizes)) \* rowsWithUniqueKeys</span></span>  
  
 <span data-ttu-id="9697e-168">非聚集索引的最佳应用是范围查找，下面的查询即为例证：</span><span class="sxs-lookup"><span data-stu-id="9697e-168">Nonclustered indexes are best when used for range lookups, as exemplified by the following query:</span></span>  
  
```sql  
  
SELECT * FROM t_hk  
   WHERE c2 > 5  
```  
  
##  <a name="memory-for-row-versioning"></a><a name="bkmk_MemoryForRowVersions"></a> <span data-ttu-id="9697e-169">行版本控制占用的内存</span><span class="sxs-lookup"><span data-stu-id="9697e-169">Memory for row versioning</span></span>  
 <span data-ttu-id="9697e-170">为避免锁定，内存 OLTP 在更新或删除行时采用乐观并发策略。</span><span class="sxs-lookup"><span data-stu-id="9697e-170">To avoid locks, In-Memory OLTP uses optimistic concurrency when updating or deleting rows.</span></span> <span data-ttu-id="9697e-171">也就是说，对某行进行更新时，将额外创建一个该行的版本。</span><span class="sxs-lookup"><span data-stu-id="9697e-171">This means that when a row is updated, an additional version of the row is created.</span></span> <span data-ttu-id="9697e-172">系统将保持旧版本可用，直至可能会用到该版本的所有事务执行完毕为止。</span><span class="sxs-lookup"><span data-stu-id="9697e-172">The system keeps the previous versions available until all transactions that could possibly use the version have finished execution.</span></span> <span data-ttu-id="9697e-173">在删除某行时，系统按与更新操作类似的方式操作，即：保持版本可用，直至不再需要为止。</span><span class="sxs-lookup"><span data-stu-id="9697e-173">When a row is deleted, the system acts in a similar way to an update, keeping the version available until it is no longer necessary.</span></span> <span data-ttu-id="9697e-174">读取和插入操作不会创建额外的行版本。</span><span class="sxs-lookup"><span data-stu-id="9697e-174">Reads and inserts do not create additional row versions.</span></span>  
  
 <span data-ttu-id="9697e-175">在任意时刻，内存中都可能存在一定数量的额外行等待垃圾回收周期释放其内存，因此，必须具有足够的内存来容纳这些额外的行。</span><span class="sxs-lookup"><span data-stu-id="9697e-175">Because there may be a number of additional rows in memory at any time waiting for the garbage collection cycle to release their memory, you must have sufficient memory to accommodate these additional rows.</span></span>  
  
 <span data-ttu-id="9697e-176">可以通过计算每秒的最大行更新数和最大删除数，然后将其乘以事务所用的最长秒数（最少为 1）来估算额外的行数。</span><span class="sxs-lookup"><span data-stu-id="9697e-176">The number of additional rows can be estimated by computing the peak number of row updates and deletions per second, then multiplying that by the number of seconds the longest transaction takes (minimum of 1).</span></span>  
  
 <span data-ttu-id="9697e-177">再用该值乘以行大小即可获得行版本控制所需占用的字节数。</span><span class="sxs-lookup"><span data-stu-id="9697e-177">That value is then multiplied by the row size to get the number of bytes you need for row versioning.</span></span>  
  
 `rowVersions = durationOfLongestTransactionInSeconds * peakNumberOfRowUpdatesOrDeletesPerSecond`  
  
 <span data-ttu-id="9697e-178">陈旧行的内存需求通过将陈旧行的数目乘以内存优化表行的大小来估算 (参见上面) 的表的[内存](#bkmk_MemoryForTable)。</span><span class="sxs-lookup"><span data-stu-id="9697e-178">Memory needs for stale rows is then estimated by multiplying the number of stale rows by the size of a memory-optimized table row (see [Memory for the table](#bkmk_MemoryForTable) above).</span></span>  
  
 `memoryForRowVersions = rowVersions * rowSize`  
  
##  <a name="memory-for-table-variables"></a><a name="bkmk_TableVariables"></a> <span data-ttu-id="9697e-179">表变量占用的内存</span><span class="sxs-lookup"><span data-stu-id="9697e-179">Memory for table variables</span></span>  
 <span data-ttu-id="9697e-180">只有在表变量超出范围时，才能释放表变量占用的内存。</span><span class="sxs-lookup"><span data-stu-id="9697e-180">Memory used for a table variable is released only when the table variable goes out of scope.</span></span> <span data-ttu-id="9697e-181">来自表变量的行（包括作为更新的一部分删除的行）不会进行垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="9697e-181">Deleted rows, including rows deleted as part of an update, from a table variable are not subject to garbage collection.</span></span> <span data-ttu-id="9697e-182">在表变量退出作用域之前不会释放内存。</span><span class="sxs-lookup"><span data-stu-id="9697e-182">No memory is released until the table variable exits scope.</span></span>  
  
 <span data-ttu-id="9697e-183">与过程作用域相反，用于许多事务的在大型 SQL 批处理中定义的表变量可能会占用大量内存。</span><span class="sxs-lookup"><span data-stu-id="9697e-183">Table variables defined in a large SQL batch, as opposed to a procedure scope, which are used in many transactions, can consume a lot of memory.</span></span> <span data-ttu-id="9697e-184">因为不对它们进行垃圾回收，所以，表变量中已删除的行可能会使用大量内存并且降低性能，这是因为读取操作需要扫描已删除的行。</span><span class="sxs-lookup"><span data-stu-id="9697e-184">Because they are not garbage collected, deleted rows in a table variable can consume a lot memory and degrade performance since read operations need to scan past the deleted rows.</span></span>  
  
##  <a name="memory-for-growth"></a><a name="bkmk_MemoryForGrowth"></a> <span data-ttu-id="9697e-185">表增长占用的内存</span><span class="sxs-lookup"><span data-stu-id="9697e-185">Memory for growth</span></span>  
 <span data-ttu-id="9697e-186">上述计算结果为表当前所需的内存。</span><span class="sxs-lookup"><span data-stu-id="9697e-186">The above calculations estimate your memory needs for the table as it currently exists.</span></span> <span data-ttu-id="9697e-187">除该内存大小外，还需对表的增长作出预测并提供充足的内存来满足增长所需。</span><span class="sxs-lookup"><span data-stu-id="9697e-187">In addition to this memory, you need to estimate the growth of the table and provide sufficient memory to accommodate that growth.</span></span>  <span data-ttu-id="9697e-188">例如，如预测表会有 10% 的增长，则需将上述结果乘以 1.1 来算出表所需的总内存。</span><span class="sxs-lookup"><span data-stu-id="9697e-188">For example, if you anticipate 10% growth then you need to multiple the results from above by 1.1 to get the total memory needed for your table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9697e-189">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9697e-189">See Also</span></span>  
 [<span data-ttu-id="9697e-190">迁移到内存中 OLTP</span><span class="sxs-lookup"><span data-stu-id="9697e-190">Migrating to In-Memory OLTP</span></span>](migrating-to-in-memory-oltp.md)  
  
  
