---
title: 确定哈希索引的正确存储桶计数 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 6d1ac280-87db-4bd8-ad43-54353647d8b5
author: stevestein
ms.author: sstein
ms.openlocfilehash: e0579a98e3302b6944f68ca449d3e7cda0ecc01d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579747"
---
# <a name="determining-the-correct-bucket-count-for-hash-indexes"></a><span data-ttu-id="8d533-102">决定哈希索引的正确存储桶数</span><span class="sxs-lookup"><span data-stu-id="8d533-102">Determining the Correct Bucket Count for Hash Indexes</span></span>
  <span data-ttu-id="8d533-103">在您创建内存优化表时，必须为 `BUCKET_COUNT` 参数指定值。</span><span class="sxs-lookup"><span data-stu-id="8d533-103">You must specify a value for the `BUCKET_COUNT` parameter when you create the memory-optimized table.</span></span> <span data-ttu-id="8d533-104">本主题将提出一些建议，帮助您为 `BUCKET_COUNT` 参数确定适当的值。</span><span class="sxs-lookup"><span data-stu-id="8d533-104">This topic makes recommendations for determining the appropriate value for the `BUCKET_COUNT` parameter.</span></span> <span data-ttu-id="8d533-105">如果您无法确定实际 Bucket 计数，则改用非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="8d533-105">If you cannot determine the correct bucket count, use a nonclustered index instead.</span></span>  <span data-ttu-id="8d533-106">不正确的 `BUCKET_COUNT` 值（特别是过低的值）可能会显著影响工作负荷性能以及数据库的恢复时间。</span><span class="sxs-lookup"><span data-stu-id="8d533-106">An incorrect `BUCKET_COUNT` value, especially one that is too low, can significantly impact workload performance, as well as recovery time of the database.</span></span> <span data-ttu-id="8d533-107">最好将 Bucket 计数估计得高一些。</span><span class="sxs-lookup"><span data-stu-id="8d533-107">It is better to overestimate the bucket count.</span></span>  
  
 <span data-ttu-id="8d533-108">重复的索引键会降低哈希索引性能，因为键已哈希处理至同一个 Bucket，导致该 Bucket 的链增加。</span><span class="sxs-lookup"><span data-stu-id="8d533-108">Duplicate index keys can decrease performance with a hash index because the keys are hashed to the same bucket, causing that bucket's chain to increase.</span></span>  
  
 <span data-ttu-id="8d533-109">有关非聚集哈希索引的详细信息，请参阅 [Hash Indexes](hash-indexes.md) 和 [Guidelines for Using Indexes on Memory-Optimized Tables](../relational-databases/in-memory-oltp/memory-optimized-tables.md)。</span><span class="sxs-lookup"><span data-stu-id="8d533-109">For more information about nonclustered hash indexes, see [Hash Indexes](hash-indexes.md) and [Guidelines for Using Indexes on Memory-Optimized Tables](../relational-databases/in-memory-oltp/memory-optimized-tables.md).</span></span>  
  
 <span data-ttu-id="8d533-110">将为内存优化表上的每个哈希索引分配一个哈希表。</span><span class="sxs-lookup"><span data-stu-id="8d533-110">One hash table is allocated for each hash index on a memory-optimized table.</span></span> <span data-ttu-id="8d533-111">为索引分配的哈希表的大小由 `BUCKET_COUNT` CREATE TABLE 中的参数指定[&#40;transact-sql&#41;](/sql/t-sql/statements/create-table-transact-sql)或[&#40;TRANSACT-SQL&#41;的 CREATE 类型](/sql/t-sql/statements/create-type-transact-sql)中。</span><span class="sxs-lookup"><span data-stu-id="8d533-111">The size of the hash table allocated for an index is specified by the `BUCKET_COUNT` parameter in [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) or [CREATE TYPE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-type-transact-sql).</span></span> <span data-ttu-id="8d533-112">Bucket 数将在内部舍入到 2 的下一次幂。</span><span class="sxs-lookup"><span data-stu-id="8d533-112">The bucket count will internally be rounded up to the next power of two.</span></span> <span data-ttu-id="8d533-113">例如，指定 300,000 的 Bucket 计数将导致 524,288 的实际 Bucket 计数。</span><span class="sxs-lookup"><span data-stu-id="8d533-113">For example, specifying a bucket count of 300,000 will result in an actual bucket count of 524,288.</span></span>  
  
 <span data-ttu-id="8d533-114">有关 Bucket 计数的文章和视频链接，请参阅 [如何确定哈希索引（内存 OLTP）的正确 Bucket 计数](https://www.mssqltips.com/sqlservertip/3104/determine-bucketcount-for-hash-indexes-for-sql-server-memory-optimized-tables/)。</span><span class="sxs-lookup"><span data-stu-id="8d533-114">For links to an article and video on bucket count, see [How to determine the right bucket count for hash indexes (In-Memory OLTP)](https://www.mssqltips.com/sqlservertip/3104/determine-bucketcount-for-hash-indexes-for-sql-server-memory-optimized-tables/).</span></span>  
  
## <a name="recommendations"></a><span data-ttu-id="8d533-115">建议</span><span class="sxs-lookup"><span data-stu-id="8d533-115">Recommendations</span></span>  
 <span data-ttu-id="8d533-116">在大多数情况下，Bucket 计数应该介于索引键中非重复值数目的 1 到 2 倍之间。</span><span class="sxs-lookup"><span data-stu-id="8d533-116">In most cases the bucket count should be between 1 and 2 times the number of distinct values in the index key.</span></span> <span data-ttu-id="8d533-117">如果索引键包含许多重复值，且平均而言对于每个索引键值超过 10 行，则改用非聚集索引</span><span class="sxs-lookup"><span data-stu-id="8d533-117">If the index key contains a lot of duplicate values, on average there are more than 10 rows for each index key value, use a nonclustered index instead</span></span>  
  
 <span data-ttu-id="8d533-118">您不见得始终都能够预测到某个特定索引键可能具有或将具有多少个值。</span><span class="sxs-lookup"><span data-stu-id="8d533-118">You may not always be able to predict how many values a particular index key may have or will have.</span></span> <span data-ttu-id="8d533-119">如果 `BUCKET_COUNT` 值处于实际键值数目的 5 倍之内，性能就应该是可接受的。</span><span class="sxs-lookup"><span data-stu-id="8d533-119">Performance should be acceptable if the `BUCKET_COUNT` value is within 5 times of the actual number of key values.</span></span>  
  
 <span data-ttu-id="8d533-120">若要确定现有数据中唯一索引键的数目，请使用与下面的示例相似的查询：</span><span class="sxs-lookup"><span data-stu-id="8d533-120">To determine the number of unique index keys in existing data, use queries similar to the following examples:</span></span>  
  
### <a name="primary-key-and-unique-indexes"></a><span data-ttu-id="8d533-121">主键和唯一索引</span><span class="sxs-lookup"><span data-stu-id="8d533-121">Primary Key and Unique Indexes</span></span>  
 <span data-ttu-id="8d533-122">因为主键索引是唯一的，所以，键中非重复值的数目与表中的行数相对应。</span><span class="sxs-lookup"><span data-stu-id="8d533-122">Because the primary key index is unique, the number of distinct values in the key corresponds to the number of rows in the table.</span></span> <span data-ttu-id="8d533-123">对于 AdventureWorks 数据库的表 Sales.SalesOrderDetail 中 (SalesOrderID, SalesOrderDetailID) 上的示例主键，发出以下查询以便计算非重复主键值的数目，该数目与表中的行数相对应：</span><span class="sxs-lookup"><span data-stu-id="8d533-123">For an example primary key on (SalesOrderID, SalesOrderDetailID) in the table Sales.SalesOrderDetail in the AdventureWorks database, issue the following query to calculate the number of distinct primary key values, which corresponds to the number of rows in the table:</span></span>  
  
```sql  
SELECT COUNT(*) AS [row count]   
FROM Sales.SalesOrderDetail  
```  
  
 <span data-ttu-id="8d533-124">此查询显示 121,317 的行计数。</span><span class="sxs-lookup"><span data-stu-id="8d533-124">This query shows a row count of 121,317.</span></span> <span data-ttu-id="8d533-125">如果行计数不会显著更改，则使用桶计数 240,000。</span><span class="sxs-lookup"><span data-stu-id="8d533-125">Use a bucket count of 240,000 if the row count will not change significantly.</span></span> <span data-ttu-id="8d533-126">如果表中的销售订单数可能会变成原来的四倍，则使用桶计数 480,000。</span><span class="sxs-lookup"><span data-stu-id="8d533-126">Use a bucket count of 480,000 if the number of sales orders in the table is expected to quadruple.</span></span>  
  
### <a name="non-unique-indexes"></a><span data-ttu-id="8d533-127">非唯一索引</span><span class="sxs-lookup"><span data-stu-id="8d533-127">Non-Unique Indexes</span></span>  
 <span data-ttu-id="8d533-128">对于其他索引，例如 (SpecialOfferID, ProductID) 上的多列索引，发出以下查询以便确定唯一索引键值的数目：</span><span class="sxs-lookup"><span data-stu-id="8d533-128">For other indexes, for example a multi-column index on (SpecialOfferID, ProductID), issue the following query to determine the number of unique index key values:</span></span>  
  
```sql  
SELECT COUNT(*) AS [SpecialOfferID_ProductID index key count]  
FROM   
   (SELECT DISTINCT SpecialOfferID, ProductID   
    FROM Sales.SalesOrderDetail) t  
```  
  
 <span data-ttu-id="8d533-129">此查询返回 (SpecialOfferID, ProductID) 的索引键计数 484，指示应使用非聚集索引而不是非聚集哈希索引。</span><span class="sxs-lookup"><span data-stu-id="8d533-129">This query returns an index key count for (SpecialOfferID, ProductID) of 484, indicating a that a nonclustered index should be used instead of a nonclustered hash index.</span></span>  
  
### <a name="determining-the-number-of-duplicates"></a><span data-ttu-id="8d533-130">确定重复项的数目</span><span class="sxs-lookup"><span data-stu-id="8d533-130">Determining the Number of Duplicates</span></span>  
 <span data-ttu-id="8d533-131">若要确定某一索引键值的重复值的平均数目，请用总行数除以唯一索引键的数目。</span><span class="sxs-lookup"><span data-stu-id="8d533-131">To determine the average number of duplicate values for an index key value, divide the total number of rows by the number of unique index keys.</span></span>  
  
 <span data-ttu-id="8d533-132">对于 (SpecialOfferID, ProductID) 上的示例索引，这导致 121317 / 484 = 251。</span><span class="sxs-lookup"><span data-stu-id="8d533-132">For the example index on (SpecialOfferID, ProductID), this leads to 121317 / 484 = 251.</span></span> <span data-ttu-id="8d533-133">这意味着索引键值具有平均值 251，并因此应该是一个非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="8d533-133">This means index key values have an average of 251, and thus this should be a nonclustered index.</span></span>  
  
## <a name="troubleshooting-the-bucket-count"></a><span data-ttu-id="8d533-134">Bucket 计数故障排除</span><span class="sxs-lookup"><span data-stu-id="8d533-134">Troubleshooting the Bucket Count</span></span>  
 <span data-ttu-id="8d533-135">若要解决内存优化表中的 bucket 计数问题，请使用[sys. dm_db_xtp_hash_index_stats &#40;transact-sql&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-hash-index-stats-transact-sql)获取有关空 bucket 和行链长度的统计信息。</span><span class="sxs-lookup"><span data-stu-id="8d533-135">To troubleshoot bucket count issues in memory-optimized tables, use [sys.dm_db_xtp_hash_index_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-hash-index-stats-transact-sql) to obtain statistics about the empty buckets and the length of row chains.</span></span> <span data-ttu-id="8d533-136">可以使用下面的查询获取与当前数据库中所有哈希索引有关的统计信息。</span><span class="sxs-lookup"><span data-stu-id="8d533-136">The following query can be used to obtain statistics about all the hash indexes in the current database.</span></span> <span data-ttu-id="8d533-137">如果数据库中有大型表，查询可能会用几分钟时间运行。</span><span class="sxs-lookup"><span data-stu-id="8d533-137">The query can take several minutes to run if there are large tables in the database.</span></span>  
  
```sql  
SELECT   
   object_name(hs.object_id) AS 'object name',   
   i.name as 'index name',   
   hs.total_bucket_count,  
   hs.empty_bucket_count,  
   floor((cast(empty_bucket_count as float)/total_bucket_count) * 100) AS 'empty_bucket_percent',  
   hs.avg_chain_length,   
   hs.max_chain_length  
FROM sys.dm_db_xtp_hash_index_stats AS hs   
   JOIN sys.indexes AS i   
   ON hs.object_id=i.object_id AND hs.index_id=i.index_id  
```  
  
 <span data-ttu-id="8d533-138">用于评估哈希索引运行状况的两个关键指标是：</span><span class="sxs-lookup"><span data-stu-id="8d533-138">The two key indicators of hash index health are:</span></span>  
  
 <span data-ttu-id="8d533-139">*empty_bucket_percent*</span><span class="sxs-lookup"><span data-stu-id="8d533-139">*empty_bucket_percent*</span></span>  
 <span data-ttu-id="8d533-140">*empty_bucket_percent* 指示哈希索引中空 Bucket 的数目。</span><span class="sxs-lookup"><span data-stu-id="8d533-140">*empty_bucket_percent* indicates the number of empty buckets in the hash index.</span></span>  
  
 <span data-ttu-id="8d533-141">如果 *empty_bucket_percent* 小于 10%，则该 Bucket 计数可能过低。</span><span class="sxs-lookup"><span data-stu-id="8d533-141">If *empty_bucket_percent* is less than 10 percent, the bucket count is likely to be too low.</span></span> <span data-ttu-id="8d533-142">理想状态下， *empty_bucket_percent* 应该为 33% 或更高。</span><span class="sxs-lookup"><span data-stu-id="8d533-142">Ideally, the *empty_bucket_percent* should be 33 percent or greater.</span></span> <span data-ttu-id="8d533-143">如果 Bucket 计数与索引键值的数目匹配，则由于哈希分布，大约 1/3 的 Bucket 是空的。</span><span class="sxs-lookup"><span data-stu-id="8d533-143">If the bucket count matches the number of index key values, about 1/3 of the buckets is empty, due to hash distribution.</span></span>  
  
 <span data-ttu-id="8d533-144">*avg_chain_length*</span><span class="sxs-lookup"><span data-stu-id="8d533-144">*avg_chain_length*</span></span>  
 <span data-ttu-id="8d533-145">*avg_chain_length* 指示哈希桶中行链的平均长度。</span><span class="sxs-lookup"><span data-stu-id="8d533-145">*avg_chain_length* indicates the average length of the row chains in the hash buckets.</span></span>  
  
 <span data-ttu-id="8d533-146">如果 *avg_chain_length* 大于 10 并且 *empty_bucket_percent* 大于 10%，则可能有许多重复索引键值并且非聚集索引可能更适合。</span><span class="sxs-lookup"><span data-stu-id="8d533-146">If *avg_chain_length* is greater than 10 and *empty_bucket_percent* is greater than 10 percent, there likely are many duplicate index key values and a nonclustered index would be more appropriate.</span></span> <span data-ttu-id="8d533-147">理想的平均链长度应该是 1。</span><span class="sxs-lookup"><span data-stu-id="8d533-147">An average chain length of 1 is ideal.</span></span>  
  
 <span data-ttu-id="8d533-148">有两个因素会影响链长度：</span><span class="sxs-lookup"><span data-stu-id="8d533-148">There are two factors that impact the chain length:</span></span>  
  
1.  <span data-ttu-id="8d533-149">重复项；所有重复行在哈希索引中都属于相同链。</span><span class="sxs-lookup"><span data-stu-id="8d533-149">Duplicates; all duplicate rows are part of the same chain in the hash index.</span></span>  
  
2.  <span data-ttu-id="8d533-150">多个键值映射到相同的 Bucket。</span><span class="sxs-lookup"><span data-stu-id="8d533-150">Multiple key values map to the same bucket.</span></span> <span data-ttu-id="8d533-151">桶计数越低，映射多个值的 Bucket 就越多。</span><span class="sxs-lookup"><span data-stu-id="8d533-151">The lower the bucket count, the more buckets that will have multiple values mapped to them.</span></span>  
  
 <span data-ttu-id="8d533-152">例如，考虑以下表和脚本以便在表中插入示例行：</span><span class="sxs-lookup"><span data-stu-id="8d533-152">As an example, consider the following table and script to insert sample rows in the table:</span></span>  
  
```sql  
CREATE TABLE [Sales].[SalesOrderHeader_test]  
(  
   [SalesOrderID] [uniqueidentifier] NOT NULL DEFAULT (newid()),  
   [OrderSequence] int NOT NULL,  
   [OrderDate] [datetime2](7) NOT NULL,  
   [Status] [tinyint] NOT NULL,  
  
PRIMARY KEY NONCLUSTERED HASH ([SalesOrderID]) WITH ( BUCKET_COUNT = 262144 ),  
INDEX IX_OrderSequence HASH (OrderSequence) WITH ( BUCKET_COUNT = 20000),  
INDEX IX_Status HASH ([Status]) WITH ( BUCKET_COUNT = 8),  
INDEX IX_OrderDate NONCLUSTERED ([OrderDate] ASC),  
)WITH ( MEMORY_OPTIMIZED = ON , DURABILITY = SCHEMA_AND_DATA )  
GO  
  
DECLARE @i int = 0  
BEGIN TRAN  
WHILE @i < 262144  
BEGIN  
   INSERT Sales.SalesOrderHeader_test (OrderSequence, OrderDate, [Status]) VALUES (@i, sysdatetime(), @i % 8)  
   SET @i += 1  
END  
COMMIT  
GO  
```  
  
 <span data-ttu-id="8d533-153">该脚本在表中插入 262,144 行。</span><span class="sxs-lookup"><span data-stu-id="8d533-153">The script inserts 262,144 rows in the table.</span></span> <span data-ttu-id="8d533-154">它在主键索引和 IX_OrderSequence 中插入唯一值。</span><span class="sxs-lookup"><span data-stu-id="8d533-154">It inserts unique values in the primary key index and in IX_OrderSequence.</span></span> <span data-ttu-id="8d533-155">它在索引 IX_Status 中插入许多重复值：该脚本仅生成 8 个非重复值。</span><span class="sxs-lookup"><span data-stu-id="8d533-155">It inserts a lot of duplicate values in the index IX_Status: the script only generates 8 distinct values.</span></span>  
  
 <span data-ttu-id="8d533-156">该 BUCKET_COUNT 故障排除查询的输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="8d533-156">The output of the BUCKET_COUNT troubleshooting query is as follows:</span></span>  
  
|<span data-ttu-id="8d533-157">索引名称</span><span class="sxs-lookup"><span data-stu-id="8d533-157">index name</span></span>|<span data-ttu-id="8d533-158">total_bucket_count</span><span class="sxs-lookup"><span data-stu-id="8d533-158">total_bucket_count</span></span>|<span data-ttu-id="8d533-159">empty_bucket_count</span><span class="sxs-lookup"><span data-stu-id="8d533-159">empty_bucket_count</span></span>|<span data-ttu-id="8d533-160">empty_bucket_percent</span><span class="sxs-lookup"><span data-stu-id="8d533-160">empty_bucket_percent</span></span>|<span data-ttu-id="8d533-161">avg_chain_length</span><span class="sxs-lookup"><span data-stu-id="8d533-161">avg_chain_length</span></span>|<span data-ttu-id="8d533-162">max_chain_length</span><span class="sxs-lookup"><span data-stu-id="8d533-162">max_chain_length</span></span>|  
|----------------|--------------------------|--------------------------|----------------------------|------------------------|------------------------|  
|<span data-ttu-id="8d533-163">IX_Status</span><span class="sxs-lookup"><span data-stu-id="8d533-163">IX_Status</span></span>|<span data-ttu-id="8d533-164">8</span><span class="sxs-lookup"><span data-stu-id="8d533-164">8</span></span>|<span data-ttu-id="8d533-165">4</span><span class="sxs-lookup"><span data-stu-id="8d533-165">4</span></span>|<span data-ttu-id="8d533-166">50</span><span class="sxs-lookup"><span data-stu-id="8d533-166">50</span></span>|<span data-ttu-id="8d533-167">65536</span><span class="sxs-lookup"><span data-stu-id="8d533-167">65536</span></span>|<span data-ttu-id="8d533-168">65536</span><span class="sxs-lookup"><span data-stu-id="8d533-168">65536</span></span>|  
|<span data-ttu-id="8d533-169">IX_OrderSequence</span><span class="sxs-lookup"><span data-stu-id="8d533-169">IX_OrderSequence</span></span>|<span data-ttu-id="8d533-170">32768</span><span class="sxs-lookup"><span data-stu-id="8d533-170">32768</span></span>|<span data-ttu-id="8d533-171">13</span><span class="sxs-lookup"><span data-stu-id="8d533-171">13</span></span>|<span data-ttu-id="8d533-172">0</span><span class="sxs-lookup"><span data-stu-id="8d533-172">0</span></span>|<span data-ttu-id="8d533-173">8</span><span class="sxs-lookup"><span data-stu-id="8d533-173">8</span></span>|<span data-ttu-id="8d533-174">26</span><span class="sxs-lookup"><span data-stu-id="8d533-174">26</span></span>|  
|<span data-ttu-id="8d533-175">PK_SalesOrd_B14003C3F8FB3364</span><span class="sxs-lookup"><span data-stu-id="8d533-175">PK_SalesOrd_B14003C3F8FB3364</span></span>|<span data-ttu-id="8d533-176">262144</span><span class="sxs-lookup"><span data-stu-id="8d533-176">262144</span></span>|<span data-ttu-id="8d533-177">96319</span><span class="sxs-lookup"><span data-stu-id="8d533-177">96319</span></span>|<span data-ttu-id="8d533-178">36</span><span class="sxs-lookup"><span data-stu-id="8d533-178">36</span></span>|<span data-ttu-id="8d533-179">1</span><span class="sxs-lookup"><span data-stu-id="8d533-179">1</span></span>|<span data-ttu-id="8d533-180">8</span><span class="sxs-lookup"><span data-stu-id="8d533-180">8</span></span>|  
  
 <span data-ttu-id="8d533-181">考虑此表上的三个哈希索引：</span><span class="sxs-lookup"><span data-stu-id="8d533-181">Consider the three hash indexes on this table:</span></span>  
  
-   <span data-ttu-id="8d533-182">IX_Status：50% 的 Bucket 是空的，这很好。</span><span class="sxs-lookup"><span data-stu-id="8d533-182">IX_Status: 50 percent of the buckets are empty, which is good.</span></span> <span data-ttu-id="8d533-183">但是，平均链长非常高 (65,536)。</span><span class="sxs-lookup"><span data-stu-id="8d533-183">However, the average chain length is very high (65,536).</span></span> <span data-ttu-id="8d533-184">这指示存在大量重复值。</span><span class="sxs-lookup"><span data-stu-id="8d533-184">This indicates a large number of duplicate values.</span></span> <span data-ttu-id="8d533-185">因此，在此情况下使用非聚集哈希索引是不恰当的。</span><span class="sxs-lookup"><span data-stu-id="8d533-185">Therefore, using a nonclustered hash index is not appropriate in this case.</span></span> <span data-ttu-id="8d533-186">应改用非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="8d533-186">A nonclustered index should be used instead.</span></span>  
  
-   <span data-ttu-id="8d533-187">IX_OrderSequence：0% 的 Bucket 是空的，这太低了。</span><span class="sxs-lookup"><span data-stu-id="8d533-187">IX_OrderSequence: 0 percent of the buckets are empty, which is too low.</span></span> <span data-ttu-id="8d533-188">此外，平均链长度是 8。</span><span class="sxs-lookup"><span data-stu-id="8d533-188">In addition, the average chain length is 8.</span></span> <span data-ttu-id="8d533-189">因为此索引中的值是唯一的，所以，这意味着平均而言 8 个值映射到每个 Bucket。</span><span class="sxs-lookup"><span data-stu-id="8d533-189">As the values in this index are unique, this means on average 8 values are mapped to each bucket.</span></span> <span data-ttu-id="8d533-190">应增加 Bucket 计数。</span><span class="sxs-lookup"><span data-stu-id="8d533-190">The bucket count should be increased.</span></span> <span data-ttu-id="8d533-191">因为索引键具有 262,144 个唯一值，所以，Bucket 计数应至少为 262,144。</span><span class="sxs-lookup"><span data-stu-id="8d533-191">As the index key has 262,144 unique values, the bucket count should be at least 262,144.</span></span> <span data-ttu-id="8d533-192">如果预期将来会出现增长，则该数目还应该更高。</span><span class="sxs-lookup"><span data-stu-id="8d533-192">If future growth is expected, the number should be higher.</span></span>  
  
-   <span data-ttu-id="8d533-193">主键索引 (PK__SalesOrder ) ：36% 的 bucket 是空的，这很好。</span><span class="sxs-lookup"><span data-stu-id="8d533-193">Primary key index (PK__SalesOrder...): 36 percent of the buckets are empty, which is good.</span></span> <span data-ttu-id="8d533-194">此外，平均链长度为 1，这也不错。</span><span class="sxs-lookup"><span data-stu-id="8d533-194">In addition the average chain length is 1, which is also good.</span></span> <span data-ttu-id="8d533-195">无需进行更改。</span><span class="sxs-lookup"><span data-stu-id="8d533-195">No change needed.</span></span>  
  
 <span data-ttu-id="8d533-196">有关排除与内存优化哈希索引有关的问题的详细信息，请参阅 [Troubleshooting Common Performance Problems with Memory-Optimized Hash Indexes](../../2014/database-engine/troubleshooting-common-performance-problems-with-memory-optimized-hash-indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="8d533-196">For more information on troubleshooting issues with your memory-optimized hash indexes, see [Troubleshooting Common Performance Problems with Memory-Optimized Hash Indexes](../../2014/database-engine/troubleshooting-common-performance-problems-with-memory-optimized-hash-indexes.md).</span></span>  
  
## <a name="detailed-considerations-for-further-optimization"></a><span data-ttu-id="8d533-197">为进一步优化需要周全考虑的方面</span><span class="sxs-lookup"><span data-stu-id="8d533-197">Detailed Considerations for Further Optimization</span></span>  
 <span data-ttu-id="8d533-198">本节概述为优化 Bucket 计数而需要进一步考虑的方面。</span><span class="sxs-lookup"><span data-stu-id="8d533-198">This section outlines further considerations for optimizing the bucket count.</span></span>  
  
 <span data-ttu-id="8d533-199">若要实现哈希索引的最佳性能，应平衡分配给哈希表的内存量和索引键中非重复值的数目。</span><span class="sxs-lookup"><span data-stu-id="8d533-199">To achieve the best performance for hash indexes, balance the amount of memory allocated to the hash table and the number of distinct values in the index key.</span></span> <span data-ttu-id="8d533-200">还需要对点查找和表扫描间的性能进行平衡：</span><span class="sxs-lookup"><span data-stu-id="8d533-200">There is also a balance between the performance of point lookups and table scans:</span></span>  
  
-   <span data-ttu-id="8d533-201">Bucket 计数值越大，索引中存在的空 Bucket 就越多。</span><span class="sxs-lookup"><span data-stu-id="8d533-201">The higher the bucket count value, the more empty buckets there will be in the index.</span></span> <span data-ttu-id="8d533-202">这会影响内存使用情况（每个 Bucket 8 个字节）和表扫描的性能，因为将在表扫描期间对每个 Bucket 进行扫描。</span><span class="sxs-lookup"><span data-stu-id="8d533-202">This has an impact on memory usage (8 bytes per bucket) and the performance of table scans, as each bucket is scanned as part of a table scan.</span></span>  
  
-   <span data-ttu-id="8d533-203">Bucket 计数越低，分配给单个 Bucket 的值就越多。</span><span class="sxs-lookup"><span data-stu-id="8d533-203">The lower the bucket count, the more values are assigned to a single bucket.</span></span> <span data-ttu-id="8d533-204">这会降低点查找和插入的性能，因为 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 可能需要遍历单个 Bucket 中的多个值才能找到搜索谓词指定的值。</span><span class="sxs-lookup"><span data-stu-id="8d533-204">This decreases performance for point lookups and inserts, because [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] may need to traverse several values in a single bucket to find the value specified by the search predicate.</span></span>  
  
 <span data-ttu-id="8d533-205">如果 Bucket 计数显著低于唯一索引键数，则许多值将映射到每个 Bucket。</span><span class="sxs-lookup"><span data-stu-id="8d533-205">If the bucket count is significantly lower than the number of unique index keys, many values will map to each bucket.</span></span> <span data-ttu-id="8d533-206">这会减少大部分 DML 操作（尤其是查找个别索引键的点查找操作）和插入操作的性能。</span><span class="sxs-lookup"><span data-stu-id="8d533-206">This degrades performance of most DML operations, particularly point lookups (lookups of individual index keys) and insert operations.</span></span> <span data-ttu-id="8d533-207">例如，包含相等谓词（与 WHERE 子句中的索引键列匹配）的 SELECT 查询、UPDATE 和 DELETE 操作的性能可能较差。</span><span class="sxs-lookup"><span data-stu-id="8d533-207">For example, you may see poor performance of SELECT queries and, UPDATE and DELETE operations with equality predicates matching the index key columns in the WHERE clause.</span></span> <span data-ttu-id="8d533-208">较低的 Bucket 计数还将影响数据库的恢复时间，因为在数据库启动时会重新创建这些索引。</span><span class="sxs-lookup"><span data-stu-id="8d533-208">A low bucket count will also affect the recovery time of the database, as the indexes are recreated on database startup.</span></span>  
  
### <a name="duplicate-index-key-values"></a><span data-ttu-id="8d533-209">重复的索引键值</span><span class="sxs-lookup"><span data-stu-id="8d533-209">Duplicate Index Key Values</span></span>  
 <span data-ttu-id="8d533-210">重复值可能增加对哈希冲突的性能影响。</span><span class="sxs-lookup"><span data-stu-id="8d533-210">Duplicate values can increase the performance impact of hash collisions.</span></span> <span data-ttu-id="8d533-211">如果每个索引键的重复项的数目较低，则上述性能影响通常不是问题。</span><span class="sxs-lookup"><span data-stu-id="8d533-211">This is usually not a problem if each index key has a low number of duplicates.</span></span> <span data-ttu-id="8d533-212">但是，如果表中唯一索引键的数目和行数之间的差异变得非常大，则该影响可能就会是问题。</span><span class="sxs-lookup"><span data-stu-id="8d533-212">But this can be a problem if the discrepancy between the number of unique index keys and the number of rows in the tables becomes very large.</span></span>  
  
 <span data-ttu-id="8d533-213">具有相同索引键的所有行将进入同一个重复链。</span><span class="sxs-lookup"><span data-stu-id="8d533-213">All rows with the same index key will go into the same duplicate chain.</span></span> <span data-ttu-id="8d533-214">如果多个索引键由于哈希冲突处于同一个 Bucket 中，则索引扫描程序将始终需要扫描整个重复链以便找到第一个值，然后才能相对于第二个值定位第一行。</span><span class="sxs-lookup"><span data-stu-id="8d533-214">If multiple index keys are in the same bucket due to a hash collision, index scanners always need to scan the full duplicate chain for the first value before they can locate the first row corresponding to the second value.</span></span> <span data-ttu-id="8d533-215">重复键还使得垃圾收集更难以定位行。</span><span class="sxs-lookup"><span data-stu-id="8d533-215">Duplicate keys also make it more difficult for garbage collection to locate the row.</span></span> <span data-ttu-id="8d533-216">例如，假设任意键有 1,000 个重复项并删除了一行，则垃圾收集器需要扫描 1,000 个重复项，从索引中取消该行的链接。</span><span class="sxs-lookup"><span data-stu-id="8d533-216">For example, if there are 1,000 duplicates for any key and one of the rows is deleted, the garbage collector needs to scan the chain of 1,000 duplicates to unlink the row from the index.</span></span> <span data-ttu-id="8d533-217">即使发现该删除行的查询使用更高效的索引（主键索引）来定位行，也要遵循上述方法，因为垃圾收集器需要从每个索引取消链接。</span><span class="sxs-lookup"><span data-stu-id="8d533-217">This is true even if the query that found the delete used a more efficient index (a primary key index) to locate the row, because the garbage collector needs to unlink from every index</span></span>  
  
 <span data-ttu-id="8d533-218">对于哈希索引，可通过两种方式减少重复索引键值导致的工作量：</span><span class="sxs-lookup"><span data-stu-id="8d533-218">For hash indexes, there are two ways to reduce the work caused by duplicate index key values:</span></span>  
  
-   <span data-ttu-id="8d533-219">改用非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="8d533-219">Use a nonclustered index instead.</span></span> <span data-ttu-id="8d533-220">您可以向索引键添加列来减少重复项，而不需要对应用程序做任何更改。</span><span class="sxs-lookup"><span data-stu-id="8d533-220">You can decrease the duplicates by adding columns to the index key without requiring any changes to the application.</span></span>  
  
-   <span data-ttu-id="8d533-221">为索引指定非常高的 Bucket 计数。</span><span class="sxs-lookup"><span data-stu-id="8d533-221">Specify a very high bucket count for the index.</span></span> <span data-ttu-id="8d533-222">例如，可达到唯一索引键数目的 20 到 100 倍。</span><span class="sxs-lookup"><span data-stu-id="8d533-222">For example, 20-to-100 times the number of unique index keys.</span></span> <span data-ttu-id="8d533-223">这将减少哈希冲突。</span><span class="sxs-lookup"><span data-stu-id="8d533-223">This will reduce hash collisions.</span></span>  
  
### <a name="small-tables"></a><span data-ttu-id="8d533-224">小型表</span><span class="sxs-lookup"><span data-stu-id="8d533-224">Small Tables</span></span>  
 <span data-ttu-id="8d533-225">对于较小的表，内存使用量通常不是问题，因为与数据库的总体大小相比，索引的大小通常较小。</span><span class="sxs-lookup"><span data-stu-id="8d533-225">For smaller tables, memory utilization is usually not a concern, as the size of the index will be small compared to the overall size of the database.</span></span>  
  
 <span data-ttu-id="8d533-226">您现在必须基于想要的性能类型进行选择：</span><span class="sxs-lookup"><span data-stu-id="8d533-226">You must now make a choice based on the kind of performance you want:</span></span>  
  
-   <span data-ttu-id="8d533-227">如果在索引上对性能起到关键作用的操作主要是点查找和/或插入操作，则为了降低哈希冲突的可能性，较高的 Bucket 计数应该更合适。</span><span class="sxs-lookup"><span data-stu-id="8d533-227">If the performance-critical operations on the index are predominantly point lookups and/or insert operations, a higher bucket count would be appropriate to reduce the likelihood of hash collisions.</span></span> <span data-ttu-id="8d533-228">最好选择三倍于行数甚至更高的计数。</span><span class="sxs-lookup"><span data-stu-id="8d533-228">Three times the number of rows or even more would be the best option.</span></span>  
  
-   <span data-ttu-id="8d533-229">如果全文检索扫描是对性能起着主要作用的操作，则使用接近于索引键值实际数目的 Bucket 计数。</span><span class="sxs-lookup"><span data-stu-id="8d533-229">If full index scans are the predominant performance-critical operations, use a bucket count that is close to the actual number of index key values.</span></span>  
  
### <a name="big-tables"></a><span data-ttu-id="8d533-230">大型表</span><span class="sxs-lookup"><span data-stu-id="8d533-230">Big Tables</span></span>  
 <span data-ttu-id="8d533-231">对于大型表，内存使用量可能成问题。</span><span class="sxs-lookup"><span data-stu-id="8d533-231">For large tables, memory utilization could become a concern.</span></span> <span data-ttu-id="8d533-232">例如，对于具有4个哈希索引的250000000行表，其中每个索引的 bucket 计数为1000000000，哈希表的开销为4个索引 \* 1000000000 bucket \* 8 字节 = 32 gb 内存使用率。</span><span class="sxs-lookup"><span data-stu-id="8d533-232">For example, with a 250 million row table that has 4 hash indexes, each with a bucket count of one billion, the overhead for the hash tables is 4 indexes \* 1 billion buckets \* 8 bytes = 32 gigabytes of memory utilization.</span></span> <span data-ttu-id="8d533-233">在为每个索引选择 2.5 亿的 Bucket 计数时，针对哈希表的总开销将是 8 GB。</span><span class="sxs-lookup"><span data-stu-id="8d533-233">When choosing a bucket count of 250 million for each of the indexes, the total overhead for the hash tables will be 8 gigabytes.</span></span> <span data-ttu-id="8d533-234">请注意，这是除了8字节的内存使用量外，每个索引每个索引将添加到每个单独的行中，这是此方案中的 8 gb (4 \* 个索引8字节 \* 250000000 行) 。</span><span class="sxs-lookup"><span data-stu-id="8d533-234">Note that this is in addition to the 8 bytes of memory usage each index adds to each individual row, which is 8 gigabytes in this scenario (4 indexes \* 8 bytes \* 250 million rows).</span></span>  
  
 <span data-ttu-id="8d533-235">全表扫描通常不是影响 OLTP 工作负荷的关键因素。</span><span class="sxs-lookup"><span data-stu-id="8d533-235">Full table scans are not usually in the performance-critical path for OLTP workloads.</span></span> <span data-ttu-id="8d533-236">因此，需要在内存使用量与点查找和插入操作的性能之间进行权衡：</span><span class="sxs-lookup"><span data-stu-id="8d533-236">Therefore, the choice is between memory utilization versus performance of point lookup and insert operations:</span></span>  
  
-   <span data-ttu-id="8d533-237">如果内存使用量是问题，则选择接近于索引键值数目的 Bucket 计数。</span><span class="sxs-lookup"><span data-stu-id="8d533-237">If memory utilization is a concern, choose a bucket count close to the number of index key values.</span></span> <span data-ttu-id="8d533-238">该 Bucket 计数不应显著小于索引键值数，因为这会影响大多数 DML 操作以及在服务器重新启动后恢复数据库所需的时间。</span><span class="sxs-lookup"><span data-stu-id="8d533-238">The bucket count should not be significantly lower than the number of index key values, as this impacts most DML operations as well the time it takes to recover the database after server restart.</span></span>  
  
-   <span data-ttu-id="8d533-239">在优化点查找的性能时，Bucket 计数最好是唯一索引值的两倍甚至三倍。</span><span class="sxs-lookup"><span data-stu-id="8d533-239">When optimizing the performance for point lookups, a higher bucket count of two or even three times the number of unique index values would be appropriate.</span></span> <span data-ttu-id="8d533-240">较高的 Bucket 计数意味着内存使用量的增加，并且也意味着全文检索扫描所需时间的增加。</span><span class="sxs-lookup"><span data-stu-id="8d533-240">A higher bucket count would mean an increased memory utilization and an increase in the time required for a full index scan.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d533-241">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8d533-241">See Also</span></span>  
 [<span data-ttu-id="8d533-242">内存优化表上的索引</span><span class="sxs-lookup"><span data-stu-id="8d533-242">Indexes on Memory-Optimized Tables</span></span>](../../2014/database-engine/indexes-on-memory-optimized-tables.md)  
  
  
