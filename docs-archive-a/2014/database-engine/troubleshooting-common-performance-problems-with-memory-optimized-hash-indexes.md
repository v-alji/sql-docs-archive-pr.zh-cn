---
title: 排查内存优化哈希索引的常见性能问题 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 1954a997-7585-4713-81fd-76d429b8d095
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3cef98571edd7736bc45ba8caf17451007a74cf1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87683045"
---
# <a name="troubleshooting-common-performance-problems-with-memory-optimized-hash-indexes"></a><span data-ttu-id="9cf93-102">对内存优化哈希索引的常见性能问题进行故障排除</span><span class="sxs-lookup"><span data-stu-id="9cf93-102">Troubleshooting Common Performance Problems with Memory-Optimized Hash Indexes</span></span>
  <span data-ttu-id="9cf93-103">本主题主要针对解决与哈希索引有关的常见问题。</span><span class="sxs-lookup"><span data-stu-id="9cf93-103">This topic will focus on troubleshooting and working around common issues with hash indexes.</span></span>  
  
## <a name="search-requires-a-subset-of-hash-index-key-columns"></a><span data-ttu-id="9cf93-104">搜索要求哈希索引键列的子集</span><span class="sxs-lookup"><span data-stu-id="9cf93-104">Search Requires a Subset of Hash Index Key Columns</span></span>  
 <span data-ttu-id="9cf93-105">**问题：** 哈希索引需要所有索引键列的值才能计算哈希值，并在哈希表中找到相应的行。</span><span class="sxs-lookup"><span data-stu-id="9cf93-105">**Issue:** Hash indexes require values for all index key columns in order to compute the hash value, and locate the corresponding rows in the hash table.</span></span> <span data-ttu-id="9cf93-106">因此，如果某个查询在 WHERE 子句中仅包含针对索引键的某个子集的相等谓词，[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 将无法使用索引查找在 WHERE 子句中定位与这些谓词相对应的行。</span><span class="sxs-lookup"><span data-stu-id="9cf93-106">Therefore, if a query includes equality predicates for only a subset of the index keys in the WHERE clause, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cannot use an index seek to locate the rows corresponding to the predicates in the WHERE clause.</span></span>  
  
 <span data-ttu-id="9cf93-107">相反，有序索引（例如基于磁盘的非聚集索引和内存优化的非聚集索引）支持在索引键列的子集上的索引查找，只要它们是索引中的首列。</span><span class="sxs-lookup"><span data-stu-id="9cf93-107">In contrast, ordered indexes like the disk-based nonclustered indexes and the memory-optimized nonclustered indexes support index seek on a subset of the index key columns, as long as they are the leading columns in the index.</span></span>  
  
 <span data-ttu-id="9cf93-108">**症状：** 这会导致性能下降，因为 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 需要执行全表扫描，而不是索引查找，这通常是更快的操作。</span><span class="sxs-lookup"><span data-stu-id="9cf93-108">**Symptom:** This results in a performance degradation, as [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] needs to execute full table scans rather than an index seek, which is typically a faster operation.</span></span>  
  
 <span data-ttu-id="9cf93-109">**如何进行故障排除：** 除了性能下降之外，查询计划的检查将显示扫描而不是索引查找。</span><span class="sxs-lookup"><span data-stu-id="9cf93-109">**How to troubleshoot:** Besides the performance degradation, inspection of the query plans will show a scan instead of an index seek.</span></span> <span data-ttu-id="9cf93-110">如果查询相对简单，则对查询文本和索引定义的检查还将显示搜索是否要求索引键列的子集。</span><span class="sxs-lookup"><span data-stu-id="9cf93-110">If the query is fairly simple, inspection of the query text and index definition will also show whether the search requires a subset of the index key columns.</span></span>  
  
 <span data-ttu-id="9cf93-111">请参考下面的表和查询：</span><span class="sxs-lookup"><span data-stu-id="9cf93-111">Consider the following table and query:</span></span>  
  
```sql  
CREATE TABLE [dbo].[od]  
(  
     o_id INT NOT NULL,  
     od_id INT NOT NULL,  
     p_id INT NOT NULL,  
     CONSTRAINT PK_od PRIMARY KEY NONCLUSTERED HASH (o_id, od_id) WITH (BUCKET_COUNT = 10000)  
)  
WITH (MEMORY_OPTIMIZED = ON)  
  
 SELECT p_id  
 FROM dbo.od  
 WHERE o_id=1  
```  
  
 <span data-ttu-id="9cf93-112">该表在两列 (o_id, od_id) 上具有哈希索引，而查询在 (o_id) 上具有相等谓词。</span><span class="sxs-lookup"><span data-stu-id="9cf93-112">The table has a hash index on the two columns (o_id, od_id), while the query has an equality predicate on (o_id).</span></span> <span data-ttu-id="9cf93-113">因为该查询仅在索引键列的子集上具有相等谓词，所以，[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 不能使用 PK_od 执行索引查找操作；[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 而是必须恢复到全文索引扫描。</span><span class="sxs-lookup"><span data-stu-id="9cf93-113">As the query has equality predicates on only a subset of the index key columns, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cannot perform an index seek operation using PK_od; instead, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] has to revert to a full index scan.</span></span>  
  
 <span data-ttu-id="9cf93-114">**解决方法：** 有多种可能的解决方法。</span><span class="sxs-lookup"><span data-stu-id="9cf93-114">**Workarounds:** There are a number of possible workarounds.</span></span> <span data-ttu-id="9cf93-115">例如：</span><span class="sxs-lookup"><span data-stu-id="9cf93-115">For example:</span></span>  
  
-   <span data-ttu-id="9cf93-116">将索引作为非聚集类型而不是非聚集哈希重新创建。</span><span class="sxs-lookup"><span data-stu-id="9cf93-116">Recreate the index as type nonclustered instead of nonclustered hash.</span></span> <span data-ttu-id="9cf93-117">内存优化的非聚集索引是有序的，因此，[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 可对前导索引键列执行索引查找。</span><span class="sxs-lookup"><span data-stu-id="9cf93-117">The memory-optimized nonclustered index is ordered, and thus [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] can perform an index seek on the leading index key columns.</span></span> <span data-ttu-id="9cf93-118">该示例最后生成的主键定义将是 `constraint PK_od primary key nonclustered`。</span><span class="sxs-lookup"><span data-stu-id="9cf93-118">The resulting primary key definition for the example would be `constraint PK_od primary key nonclustered`.</span></span>  
  
-   <span data-ttu-id="9cf93-119">更改当前索引键以便匹配 WHERE 子句中的列。</span><span class="sxs-lookup"><span data-stu-id="9cf93-119">Change the current index key to match the columns in the WHERE clause.</span></span>  
  
-   <span data-ttu-id="9cf93-120">添加与查询的 WHERE 子句中的列匹配的新哈希索引。</span><span class="sxs-lookup"><span data-stu-id="9cf93-120">Add a new hash index that matches with the columns in the WHERE clause of the query.</span></span> <span data-ttu-id="9cf93-121">在该示例中，最后生成的表定义将如下所示：</span><span class="sxs-lookup"><span data-stu-id="9cf93-121">In the example, the resulting table definition would look at follows:</span></span>  
  
    ```sql  
    CREATE TABLE dbo.od  
     ( o_id INT NOT NULL,  
     od_id INT NOT NULL,  
     p_id INT NOT NULL,  
  
     CONSTRAINT PK_od PRIMARY KEY   
     NONCLUSTERED HASH (o_id,od_id) WITH (BUCKET_COUNT=10000),  
  
     INDEX ix_o_id NONCLUSTERED HASH (o_id) WITH (BUCKET_COUNT=10000)  
  
     ) WITH (MEMORY_OPTIMIZED=ON)  
    ```  
  
 <span data-ttu-id="9cf93-122">请注意，如果对于某一给定的索引键值存在许多重复行，则内存优化的哈希索引不会达到最佳性能：在该示例中，如果针对 o_id 列的唯一值的数目远小于该表中的行数，则在 (o_id) 上添加索引并非最佳选择；将索引 index PK_od 的类型从哈希更改为非聚集应该是更好的解决方法。</span><span class="sxs-lookup"><span data-stu-id="9cf93-122">Note that a memory-optimized hash index does not perform optimally if there are a lot of duplicate rows for a given index key value: in the example, if the number of unique values for the column o_id is much smaller than the number of rows in the table, it would not be optimal to add an index on (o_id); instead, changing the type of the index PK_od from hash to nonclustered would be the better solution.</span></span> <span data-ttu-id="9cf93-123">有关详细信息，请参阅 [Determining the Correct Bucket Count for Hash Indexes](../relational-databases/indexes/indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="9cf93-123">For more information, see [Determining the Correct Bucket Count for Hash Indexes](../relational-databases/indexes/indexes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cf93-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9cf93-124">See Also</span></span>  
 [<span data-ttu-id="9cf93-125">内存优化表上的索引</span><span class="sxs-lookup"><span data-stu-id="9cf93-125">Indexes on Memory-Optimized Tables</span></span>](../relational-databases/in-memory-oltp/memory-optimized-tables.md)  
  
  
