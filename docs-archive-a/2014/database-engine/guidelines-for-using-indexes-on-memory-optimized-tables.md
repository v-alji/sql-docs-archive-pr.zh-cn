---
title: 在内存优化表上使用索引的准则 |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
helpviewer_keywords:
- hash indexes
ms.assetid: 16ef63a4-367a-46ac-917d-9eebc81ab29b
author: stevestein
ms.author: sstein
ms.openlocfilehash: f00d643088634c918eb626917eae64a001ce3678
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690032"
---
# <a name="guidelines-for-using-indexes-on-memory-optimized-tables"></a><span data-ttu-id="a088d-102">在内存优化表上使用索引的指导原则</span><span class="sxs-lookup"><span data-stu-id="a088d-102">Guidelines for Using Indexes on Memory-Optimized Tables</span></span>
  <span data-ttu-id="a088d-103">索引用于高效访问 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 表中的数据。</span><span class="sxs-lookup"><span data-stu-id="a088d-103">Indexes are used for efficiently accessing data in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] tables.</span></span> <span data-ttu-id="a088d-104">指定正确索引可以显著提高查询性能。</span><span class="sxs-lookup"><span data-stu-id="a088d-104">Specifying the right indexes can dramatically improve query performance.</span></span> <span data-ttu-id="a088d-105">例如，请考虑以下查询：</span><span class="sxs-lookup"><span data-stu-id="a088d-105">Consider, for example, the query:</span></span>  
  
```sql  
SELECT c1, c2 FROM t WHERE c1 = 1;  
```  
  
 <span data-ttu-id="a088d-106">如果 c1 列上没有索引，则 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 需要扫描整个表 t，然后筛选满足条件 c1=1 的行。</span><span class="sxs-lookup"><span data-stu-id="a088d-106">If there is no index on column c1, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] will need to scan the entire table t, and then filter on the rows that satisfy the condition c1=1.</span></span> <span data-ttu-id="a088d-107">但是，如果 t 在 c1 列上具有索引，则 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 可以直接查找值 1 并对行进行检索。</span><span class="sxs-lookup"><span data-stu-id="a088d-107">However, if t has an index on column c1, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] can seek directly on the value 1 and retrieve the rows.</span></span>  
  
 <span data-ttu-id="a088d-108">针对表中一列或多列搜索具有特定值或值范围的记录时，[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 可以使用这些列上的索引来快速找到对应记录。</span><span class="sxs-lookup"><span data-stu-id="a088d-108">When searching for records that have a specific value, or range of values, for one or more columns in the table, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] can use an index on those columns to quickly locate the corresponding records.</span></span> <span data-ttu-id="a088d-109">基于磁盘的表和内存优化表都会受益于索引。</span><span class="sxs-lookup"><span data-stu-id="a088d-109">Both disk-based and memory-optimized tables benefit from indexes.</span></span> <span data-ttu-id="a088d-110">但是，在使用内存优化的表时，需要考虑索引结构之间的一些区别。</span><span class="sxs-lookup"><span data-stu-id="a088d-110">There are, however, certain differences between index structures that need to be considered when using memory-optimized tables.</span></span> <span data-ttu-id="a088d-111">内存优化表 (索引称为内存优化索引。 ) 一些主要区别：</span><span class="sxs-lookup"><span data-stu-id="a088d-111">(Indexes on memory-optimized tables are referred to as memory-optimized indexes.) Some of the key differences are:</span></span>  
  
-   <span data-ttu-id="a088d-112">必须[CREATE TABLE &#40;transact-sql&#41;](/sql/t-sql/statements/create-table-transact-sql)创建内存优化索引。</span><span class="sxs-lookup"><span data-stu-id="a088d-112">Memory-optimized indexes must be created with [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql).</span></span> <span data-ttu-id="a088d-113">基于磁盘上的索引可以使用 `CREATE TABLE` 和 `CREATE INDEX` 创建。</span><span class="sxs-lookup"><span data-stu-id="a088d-113">Disk-based indexes can be created with `CREATE TABLE` and `CREATE INDEX`.</span></span>  
  
-   <span data-ttu-id="a088d-114">内存优化索引仅存在于内存中。</span><span class="sxs-lookup"><span data-stu-id="a088d-114">Memory-optimized indexes exist only in memory.</span></span> <span data-ttu-id="a088d-115">索引结构在磁盘中不持久化，并且不在事务日志中记录索引操作。</span><span class="sxs-lookup"><span data-stu-id="a088d-115">Index structures are not persisted to disk and index operations are not logged in the transaction log.</span></span> <span data-ttu-id="a088d-116">CREATE TABLE 过程中以及数据库启动过程中，在内存中创建内存优化的表时，将创建索引结构。</span><span class="sxs-lookup"><span data-stu-id="a088d-116">The index structure is created when the memory-optimized table is created in memory, both during CREATE TABLE and during database startup.</span></span>  
  
-   <span data-ttu-id="a088d-117">内存优化索引本质上是覆盖性的。</span><span class="sxs-lookup"><span data-stu-id="a088d-117">Memory-optimized indexes are inherently covering.</span></span> <span data-ttu-id="a088d-118">覆盖表示真正在索引中包括所有列，因此内存优化的表不需要查找书签。</span><span class="sxs-lookup"><span data-stu-id="a088d-118">Covering means that all columns are virtually included in the index and bookmark lookups are not needed for memory-optimized tables.</span></span> <span data-ttu-id="a088d-119">内存优化索引仅包含指向表数据结构中的实际行的内存指针，而不是对主键的引用。</span><span class="sxs-lookup"><span data-stu-id="a088d-119">Rather than a reference to the primary key, memory-optimized indexes simply contain a memory pointer to the actual row in the table data structure.</span></span>  
  
-   <span data-ttu-id="a088d-120">碎片和填充因子不适用于内存优化索引。</span><span class="sxs-lookup"><span data-stu-id="a088d-120">Fragmentation and fillfactor do not apply to memory-optimized indexes.</span></span> <span data-ttu-id="a088d-121">在基于磁盘的索引中，碎片是指无序写入磁盘的 B 树中的页。</span><span class="sxs-lookup"><span data-stu-id="a088d-121">In disk-based indexes, fragmentation refers to pages in the B-tree being written to disk out-of-order.</span></span> <span data-ttu-id="a088d-122">内存优化索引不会写入磁盘或从磁盘读取。</span><span class="sxs-lookup"><span data-stu-id="a088d-122">Memory-optimized indexes are not written to or read from disk.</span></span> <span data-ttu-id="a088d-123">基于磁盘的 B 树索引中的填充因子是指使用实际数据填充物理页结构的程度。</span><span class="sxs-lookup"><span data-stu-id="a088d-123">Fillfactor in disk-based B-tree indexes refers to the degree to which the physical page structures are filled with actual data.</span></span> <span data-ttu-id="a088d-124">内存优化索引结构没有固定大小的页。</span><span class="sxs-lookup"><span data-stu-id="a088d-124">The memory-optimized index structures do not have fixed-size pages.</span></span>  
  
 <span data-ttu-id="a088d-125">内存优化的索引具有以下两种类型：</span><span class="sxs-lookup"><span data-stu-id="a088d-125">There are two types of memory-optimized indexes:</span></span>  
  
-   <span data-ttu-id="a088d-126">非聚集哈希索引，为点查找编制此类索引。</span><span class="sxs-lookup"><span data-stu-id="a088d-126">Nonclustered hash indexes, which are made for point lookups.</span></span> <span data-ttu-id="a088d-127">有关哈希索引的详细信息，请参阅[哈希索引](hash-indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="a088d-127">For more information about hash indexes, see [Hash Indexes](hash-indexes.md).</span></span>  
  
-   <span data-ttu-id="a088d-128">非聚集索引，为范围扫描和有序扫描编制此类索引。</span><span class="sxs-lookup"><span data-stu-id="a088d-128">Nonclustered indexes, which are made for range scans and ordered scans.</span></span>  
  
 <span data-ttu-id="a088d-129">借助于哈希索引，可通过内存中的哈希表来访问数据。</span><span class="sxs-lookup"><span data-stu-id="a088d-129">With a hash index, data is accessed through an in-memory hash table.</span></span> <span data-ttu-id="a088d-130">哈希索引没有页，并且始终为固定大小。</span><span class="sxs-lookup"><span data-stu-id="a088d-130">Hash indexes do not have pages and are always of a fixed size.</span></span> <span data-ttu-id="a088d-131">但是，哈希索引的哈希存储桶可为空，这样会浪费一些空间，但数量有限。</span><span class="sxs-lookup"><span data-stu-id="a088d-131">However, a hash index can have empty hash buckets, which result in limited wasted space.</span></span> <span data-ttu-id="a088d-132">对于使用哈希索引从查询返回的值不进行排序。</span><span class="sxs-lookup"><span data-stu-id="a088d-132">The values returned from a query using a hash index are not sorted.</span></span> <span data-ttu-id="a088d-133">哈希索引为针对相等谓词的索引查找进行优化，还支持完整索引扫描。</span><span class="sxs-lookup"><span data-stu-id="a088d-133">Hash indexes are optimized for index seeks on equality predicates and also support full index scans.</span></span>  
  
 <span data-ttu-id="a088d-134">非聚集索引（而非哈希索引）支持哈希索引支持的所有功能，外加针对不等谓词（例如大于或小于）的查找操作以及排序顺序。</span><span class="sxs-lookup"><span data-stu-id="a088d-134">Nonclustered indexes (not hash indexes) support everything that hash indexes supports plus seek operations on inequality predicates such as greater than or less than, as well as sort order.</span></span> <span data-ttu-id="a088d-135">可以根据索引创建时指定的顺序检索行。</span><span class="sxs-lookup"><span data-stu-id="a088d-135">Rows can be retrieved according to the order specified with index creation.</span></span> <span data-ttu-id="a088d-136">如果索引的排序顺序匹配特定查询所需的排序顺序，例如，如果索引键匹配 ORDER BY 子句，则无需作为查询执行的一部分对行进行排序。</span><span class="sxs-lookup"><span data-stu-id="a088d-136">If the sort order of the index matches the sort order required for a particular query, for example if the index key matches the ORDER BY clause, there is no need to sort the rows as part of query execution.</span></span> <span data-ttu-id="a088d-137">内存优化的非聚集索引是无方向的；它们不支持按与索引的排序顺序反向的排序顺序来检索行。</span><span class="sxs-lookup"><span data-stu-id="a088d-137">Memory-optimized nonclustered indexes are unidirectional; they do not support retrieving rows in a sort order that is the reverse of the sort order of the index.</span></span> <span data-ttu-id="a088d-138">例如，对于被指定为 (c1 ASC) 的一个索引，不可能以反向顺序（如 (c1 DESC)）浏览该索引。</span><span class="sxs-lookup"><span data-stu-id="a088d-138">For example, for an index specified as (c1 ASC), it is not possible to scan the index in reverse order, as (c1 DESC).</span></span>  
  
 <span data-ttu-id="a088d-139">每个索引都会占用内存。</span><span class="sxs-lookup"><span data-stu-id="a088d-139">Each index consumes memory.</span></span> <span data-ttu-id="a088d-140">哈希索引的内存用量固定不变，是存储桶数量的函数。</span><span class="sxs-lookup"><span data-stu-id="a088d-140">Hash indexes consume a fixed amount of memory, which is a function of the bucket count.</span></span> <span data-ttu-id="a088d-141">对于非聚集索引，内存用量是行数和索引键列大小的函数，还有一些其他开销取决于工作负荷。</span><span class="sxs-lookup"><span data-stu-id="a088d-141">For nonclustered indexes, memory consumption is a function of the row count and the size of the index key columns, with some additional overhead depending on the workload.</span></span> <span data-ttu-id="a088d-142">内存优化的索引所用的内存不计入用于在内存优化的表中存储行的内存，并区别于此类内存。</span><span class="sxs-lookup"><span data-stu-id="a088d-142">Memory for memory-optimized indexes is in addition to and separate from the memory used to store rows in memory-optimized tables.</span></span>  
  
 <span data-ttu-id="a088d-143">重复键值始终共享同一哈希桶。</span><span class="sxs-lookup"><span data-stu-id="a088d-143">Duplicate key values always share the same hash bucket.</span></span> <span data-ttu-id="a088d-144">如果一个哈希索引包含了多个重复键值，那么产生的长哈希链会损坏性能。</span><span class="sxs-lookup"><span data-stu-id="a088d-144">If a hash index contains many duplicate key values, the resulting long hash chains will harm performance.</span></span> <span data-ttu-id="a088d-145">发生在任何哈希索引中的哈希冲突将会进一步减弱此方案中的性能。</span><span class="sxs-lookup"><span data-stu-id="a088d-145">Hash collisions, which occur in any hash index, will further reduce performance in this scenario.</span></span> <span data-ttu-id="a088d-146">出于此原因，如果唯一索引键的数目至少为100倍于行计数，则可以通过使 bucket 计数 (至少为唯一索引键的数目的8倍，降低哈希冲突的风险;有关) 的详细信息，请参阅[确定哈希索引的正确存储桶计数](../../2014/database-engine/determining-the-correct-bucket-count-for-hash-indexes.md)，或者可以使用非聚集索引完全消除哈希冲突。</span><span class="sxs-lookup"><span data-stu-id="a088d-146">For that reason, if the number of unique index keys is at least 100 times smaller than the row count, you can reduce the risk of hash collisions by making the bucket count much larger (at least eight times the number of unique index keys; see [Determining the Correct Bucket Count for Hash Indexes](../../2014/database-engine/determining-the-correct-bucket-count-for-hash-indexes.md) for more information) or you can eliminate hash collisions entirely by using a nonclustered index.</span></span>  
  
## <a name="determining-which-indexes-to-use-for-a-memory-optimized-table"></a><span data-ttu-id="a088d-147">确定要用于内存优化表的索引</span><span class="sxs-lookup"><span data-stu-id="a088d-147">Determining Which Indexes to Use for a Memory-Optimized Table</span></span>  
 <span data-ttu-id="a088d-148">每个内存优化的表都必须具有至少一个索引。</span><span class="sxs-lookup"><span data-stu-id="a088d-148">Each memory-optimized table must have at least one index.</span></span> <span data-ttu-id="a088d-149">请注意，每个 PRIMARY KEY 约束都会隐式创建一个索引。</span><span class="sxs-lookup"><span data-stu-id="a088d-149">Note that each PRIMARY KEY constraint implicitly creates an index.</span></span> <span data-ttu-id="a088d-150">因此，如果表中包含主键，则该表具有索引。</span><span class="sxs-lookup"><span data-stu-id="a088d-150">Therefore, if a table has a primary key, it has an index.</span></span> <span data-ttu-id="a088d-151">主键是对持久内存优化表的要求。</span><span class="sxs-lookup"><span data-stu-id="a088d-151">A primary key is a requirement for a durable memory-optimized table.</span></span>  
  
 <span data-ttu-id="a088d-152">查询内存优化的表时，在谓词子句仅包含相等谓词的情况下，哈希索引的性能更好。</span><span class="sxs-lookup"><span data-stu-id="a088d-152">When querying a memory-optimized table, hash indexes perform better when the predicate clause contains only equality predicates.</span></span> <span data-ttu-id="a088d-153">谓词必须包括哈希索引键中的所有列。</span><span class="sxs-lookup"><span data-stu-id="a088d-153">The predicate must include all columns in the hash index key.</span></span> <span data-ttu-id="a088d-154">如果有不等谓词，则哈希索引将恢复为扫描。</span><span class="sxs-lookup"><span data-stu-id="a088d-154">A hash index will revert to a scan given an inequality predicate.</span></span>  
  
 <span data-ttu-id="a088d-155">内存优化的表中的列可以同时为哈希索引和非聚集索引的一部分。</span><span class="sxs-lookup"><span data-stu-id="a088d-155">A column in a memory-optimized table can be part of both a hash index and a nonclustered index.</span></span>  
  
 <span data-ttu-id="a088d-156">在用不等谓词查询内存优化的表时，非聚集索引的性能将高于非聚集哈希索引。</span><span class="sxs-lookup"><span data-stu-id="a088d-156">When querying a memory-optimized table with inequality predicates, nonclustered indexes will perform better than nonclustered hash indexes.</span></span>  
  
 <span data-ttu-id="a088d-157">哈希索引需要键（哈希）才能仔细查找索引。</span><span class="sxs-lookup"><span data-stu-id="a088d-157">The hash index requires a key (to hash) to seek into the index.</span></span> <span data-ttu-id="a088d-158">如果索引键由两列组成，但仅提供第一列，则 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 没有完整的键可进行哈希运算。 </span><span class="sxs-lookup"><span data-stu-id="a088d-158">If an index key consists of two columns and you only provide the first column, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] does not have a complete key to hash.</span></span> <span data-ttu-id="a088d-159">这将产生索引扫描查询计划。</span><span class="sxs-lookup"><span data-stu-id="a088d-159">This will result in an index scan query plan.</span></span> <span data-ttu-id="a088d-160">由用法决定应编制哪些列的索引。</span><span class="sxs-lookup"><span data-stu-id="a088d-160">Usage determines which columns should be indexed.</span></span>  
  
 <span data-ttu-id="a088d-161">当非聚集索引中的列在许多行中的值相同（索引键列有许多重复值）时，更新、插入和删除的性能会降低。</span><span class="sxs-lookup"><span data-stu-id="a088d-161">When a column in a nonclustered index has the same value in many rows (index key columns have a lot of duplicate values), performance can degrade for updates, inserts, and deletions.</span></span>  <span data-ttu-id="a088d-162">在这种情况下提高性能的一种方法是向非聚集索引添加另一列。</span><span class="sxs-lookup"><span data-stu-id="a088d-162">One way to improve performance in this situation is to add another column to the nonclustered index.</span></span>  
  
### <a name="operations-on-memory-optimized-and-disk-based-indexes"></a><span data-ttu-id="a088d-163">针对内存优化表和基于磁盘的表的操作。</span><span class="sxs-lookup"><span data-stu-id="a088d-163">Operations on memory-optimized and disk-based indexes.</span></span>  
  
|<span data-ttu-id="a088d-164">Operation</span><span class="sxs-lookup"><span data-stu-id="a088d-164">Operation</span></span>|<span data-ttu-id="a088d-165">内存优化、非聚集哈希索引</span><span class="sxs-lookup"><span data-stu-id="a088d-165">Memory-optimized, nonclustered hash, index</span></span>|<span data-ttu-id="a088d-166">内存优化的非聚集索引</span><span class="sxs-lookup"><span data-stu-id="a088d-166">Memory-optimized nonclustered index</span></span>|<span data-ttu-id="a088d-167">基于磁盘的索引</span><span class="sxs-lookup"><span data-stu-id="a088d-167">Disk-based index</span></span>|  
|---------------|-------------------------------------------------|------------------------------------------|-----------------------|  
|<span data-ttu-id="a088d-168">索引扫描，检索所有表行。</span><span class="sxs-lookup"><span data-stu-id="a088d-168">Index Scan, retrieve all table rows.</span></span>|<span data-ttu-id="a088d-169">是</span><span class="sxs-lookup"><span data-stu-id="a088d-169">Yes</span></span>|<span data-ttu-id="a088d-170">是</span><span class="sxs-lookup"><span data-stu-id="a088d-170">Yes</span></span>|<span data-ttu-id="a088d-171">是</span><span class="sxs-lookup"><span data-stu-id="a088d-171">Yes</span></span>|  
|<span data-ttu-id="a088d-172">采用相等谓词 (=) 的索引查找。</span><span class="sxs-lookup"><span data-stu-id="a088d-172">Index seek on equality predicate(s) (=).</span></span>|<span data-ttu-id="a088d-173">是</span><span class="sxs-lookup"><span data-stu-id="a088d-173">Yes</span></span><br /><br /> <span data-ttu-id="a088d-174">（需要完整的键。）</span><span class="sxs-lookup"><span data-stu-id="a088d-174">(Full key required.)</span></span>|<span data-ttu-id="a088d-175">是 <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="a088d-175">Yes <sup>1</sup></span></span>|<span data-ttu-id="a088d-176">是</span><span class="sxs-lookup"><span data-stu-id="a088d-176">Yes</span></span>|  
|<span data-ttu-id="a088d-177">对不相等谓词的索引查找 ( # A0，<， \<=, > =，介于) 之间。</span><span class="sxs-lookup"><span data-stu-id="a088d-177">Index seek on inequality predicates (>, <, \<=, >=, BETWEEN).</span></span>|<span data-ttu-id="a088d-178">否（索引扫描中的结果）</span><span class="sxs-lookup"><span data-stu-id="a088d-178">No (results in an index scan)</span></span>|<span data-ttu-id="a088d-179">是 <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="a088d-179">Yes <sup>1</sup></span></span>|<span data-ttu-id="a088d-180">是</span><span class="sxs-lookup"><span data-stu-id="a088d-180">Yes</span></span>|  
|<span data-ttu-id="a088d-181">按与索引定义匹配的排序顺序检索行。</span><span class="sxs-lookup"><span data-stu-id="a088d-181">Retrieve rows in a sort-order matching the index definition.</span></span>|<span data-ttu-id="a088d-182">否</span><span class="sxs-lookup"><span data-stu-id="a088d-182">No</span></span>|<span data-ttu-id="a088d-183">是</span><span class="sxs-lookup"><span data-stu-id="a088d-183">Yes</span></span>|<span data-ttu-id="a088d-184">是</span><span class="sxs-lookup"><span data-stu-id="a088d-184">Yes</span></span>|  
|<span data-ttu-id="a088d-185">按与索引定义相反的排序顺序检索行。</span><span class="sxs-lookup"><span data-stu-id="a088d-185">Retrieve rows in a sort-order matching the reverse of the index definition.</span></span>|<span data-ttu-id="a088d-186">否</span><span class="sxs-lookup"><span data-stu-id="a088d-186">No</span></span>|<span data-ttu-id="a088d-187">否</span><span class="sxs-lookup"><span data-stu-id="a088d-187">No</span></span>|<span data-ttu-id="a088d-188">是</span><span class="sxs-lookup"><span data-stu-id="a088d-188">Yes</span></span>|  
  
 <span data-ttu-id="a088d-189">在表格中，“是”意味着索引能充分地服务需求，而“否”则意味着索引不能用来成功地满足需求。</span><span class="sxs-lookup"><span data-stu-id="a088d-189">In the table, Yes means that the index can adequately service the request and No means that the index cannot be used successfully to satisfy the request.</span></span>  
  
 <span data-ttu-id="a088d-190"><sup>1</sup>对于非聚集内存优化索引，不需要完整的键即可执行索引查找。</span><span class="sxs-lookup"><span data-stu-id="a088d-190"><sup>1</sup> For a nonclustered memory-optimized index, the full key is not required to perform an index seek.</span></span> <span data-ttu-id="a088d-191">即便如此，给定索引键的列顺序后，如果缺少的列后面出现列值，则进行扫描。</span><span class="sxs-lookup"><span data-stu-id="a088d-191">Although, given the column order of the index key, a scan will occur if a value for a column comes after a missing column.</span></span>  
  
## <a name="index-count"></a><span data-ttu-id="a088d-192">索引计数</span><span class="sxs-lookup"><span data-stu-id="a088d-192">Index Count</span></span>  
 <span data-ttu-id="a088d-193">内存优化表可以具有多达 8 个索引，包括通过主键创建的索引。</span><span class="sxs-lookup"><span data-stu-id="a088d-193">A memory-optimized table can have up to 8 indexes, including the index created with the primary key.</span></span>  
  
 <span data-ttu-id="a088d-194">关于在内存优化表上创建的索引数目，请考虑以下几点：</span><span class="sxs-lookup"><span data-stu-id="a088d-194">Regarding the number of indexes created on a memory-optimized table, consider the following:</span></span>  
  
-   <span data-ttu-id="a088d-195">指定创建表时所需的索引。</span><span class="sxs-lookup"><span data-stu-id="a088d-195">Specify the indexes you need when you create the table.</span></span> <span data-ttu-id="a088d-196">不能在创建内存优化表之后再为该表创建索引。</span><span class="sxs-lookup"><span data-stu-id="a088d-196">You cannot create an index for a memory-optimized table after the table is created.</span></span> <span data-ttu-id="a088d-197">如果要向内存优化表添加索引，请删除并重新创建该表。</span><span class="sxs-lookup"><span data-stu-id="a088d-197">If you want to add an index to a memory-optimized table, drop and recreate that table.</span></span>  
  
-   <span data-ttu-id="a088d-198">请勿创建很少使用的索引：</span><span class="sxs-lookup"><span data-stu-id="a088d-198">Do not create an index that you rarely use:</span></span>  
  
     <span data-ttu-id="a088d-199">如果表上的所有索引都经常使用，则垃圾收集效果最好。</span><span class="sxs-lookup"><span data-stu-id="a088d-199">Garbage collection works best if all indexes on the table are frequently used.</span></span> <span data-ttu-id="a088d-200">很少使用的索引可能会导致垃圾收集系统对于旧的版本无法以最佳方式执行。</span><span class="sxs-lookup"><span data-stu-id="a088d-200">Rarely-used indexes may cause the garbage collection system to not perform optimally for old row versions.</span></span>  
  
## <a name="creating-a-memory-optimized-index-code-samples"></a><span data-ttu-id="a088d-201">创建内存优化的索引：代码示例</span><span class="sxs-lookup"><span data-stu-id="a088d-201">Creating a Memory-Optimized Index: Code Samples</span></span>  
 <span data-ttu-id="a088d-202">列级别哈希索引：</span><span class="sxs-lookup"><span data-stu-id="a088d-202">Column level hash index:</span></span>  
  
```sql  
CREATE TABLE t1   
   (c1 INT NOT NULL INDEX idx HASH WITH (BUCKET_COUNT = 100))   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_ONLY)  
```  
  
 <span data-ttu-id="a088d-203">表级别哈希索引：</span><span class="sxs-lookup"><span data-stu-id="a088d-203">Table level hash index:</span></span>  
  
```sql  
CREATE TABLE t1_1   
   (c1 INT NOT NULL,   
   INDEX IDX HASH (c1) WITH (BUCKET_COUNT = 100))   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_ONLY)  
```  
  
 <span data-ttu-id="a088d-204">列级别主键哈希索引：</span><span class="sxs-lookup"><span data-stu-id="a088d-204">Column level primary key hash index:</span></span>  
  
```sql  
CREATE TABLE t2   
   (c1 INT NOT NULL PRIMARY KEY NONCLUSTERED HASH WITH (BUCKET_COUNT = 100))   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)  
```  
  
 <span data-ttu-id="a088d-205">表级别主键哈希索引：</span><span class="sxs-lookup"><span data-stu-id="a088d-205">Table level primary key hash index:</span></span>  
  
```sql  
CREATE TABLE t2_2   
   (c1 INT NOT NULL,   
   PRIMARY KEY NONCLUSTERED HASH (c1) WITH (BUCKET_COUNT = 100))   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)  
```  
  
 <span data-ttu-id="a088d-206">列级非聚集索引：</span><span class="sxs-lookup"><span data-stu-id="a088d-206">Column level nonclustered index:</span></span>  
  
```sql  
CREATE TABLE t3   
   (c1 INT NOT NULL INDEX ID)   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_ONLY)  
```  
  
 <span data-ttu-id="a088d-207">表级非聚集索引：</span><span class="sxs-lookup"><span data-stu-id="a088d-207">Table level nonclustered  index:</span></span>  
  
```sql  
CREATE TABLE t3_3   
   (c1 INT NOT NULL,   
   INDEX IDX NONCLUSTERED (c1))   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_ONLY)  
```  
  
 <span data-ttu-id="a088d-208">列级主键非聚集索引：</span><span class="sxs-lookup"><span data-stu-id="a088d-208">Column level primary key nonclustered  index:</span></span>  
  
```sql  
CREATE TABLE t4   
   (c1 INT NOT NULL PRIMARY KEY NONCLUSTERED)   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)  
```  
  
 <span data-ttu-id="a088d-209">表级主键非聚集索引：</span><span class="sxs-lookup"><span data-stu-id="a088d-209">Table level primary key nonclustered index:</span></span>  
  
```sql  
CREATE TABLE t4_4   
   (c1 INT NOT NULL,   
   PRIMARY KEY NONCLUSTERED (c1))   
   WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)  
```  
  
 <span data-ttu-id="a088d-210">定义列后定义的多列索引：</span><span class="sxs-lookup"><span data-stu-id="a088d-210">Multicolumn index defined after columns are defined:</span></span>  
  
```sql  
create table t (  
       a int not null constraint ta primary key nonclustered,  
       b int not null,  
       c int not null,  
       d int not null,  
       index idx_t_b_c_d nonclustered (b, c asc, d desc)  
) with (memory_optimized = on, durability = SCHEMA_AND_DATA)  
go  
```  
  
## <a name="see-also"></a><span data-ttu-id="a088d-211">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a088d-211">See Also</span></span>  
 <span data-ttu-id="a088d-212">[内存优化表的索引](../relational-databases/in-memory-oltp/memory-optimized-tables.md) </span><span class="sxs-lookup"><span data-stu-id="a088d-212">[Indexes on Memory-Optimized Tables](../relational-databases/in-memory-oltp/memory-optimized-tables.md) </span></span>  
 <span data-ttu-id="a088d-213">[确定哈希索引的正确存储桶计数](../../2014/database-engine/determining-the-correct-bucket-count-for-hash-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="a088d-213">[Determining the Correct Bucket Count for Hash Indexes](../../2014/database-engine/determining-the-correct-bucket-count-for-hash-indexes.md) </span></span>  
 [<span data-ttu-id="a088d-214">哈希索引</span><span class="sxs-lookup"><span data-stu-id="a088d-214">Hash Indexes</span></span>](hash-indexes.md)  
  
  
