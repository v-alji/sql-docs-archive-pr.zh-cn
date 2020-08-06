---
title: 哈希索引 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: f4bdc9c1-7922-4fac-8183-d11ec58fec4e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 05b8d1e3a5d92078cc2ec3fe7cd5b6d3fb5b47c9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693452"
---
# <a name="hash-indexes"></a><span data-ttu-id="8489d-102">哈希索引</span><span class="sxs-lookup"><span data-stu-id="8489d-102">Hash Indexes</span></span>
  <span data-ttu-id="8489d-103">索引用作内存优化表的入口点。</span><span class="sxs-lookup"><span data-stu-id="8489d-103">Indexes are used as entry points for memory-optimized tables.</span></span> <span data-ttu-id="8489d-104">从表读取行需要借助索引在内存中定位数据。</span><span class="sxs-lookup"><span data-stu-id="8489d-104">Reading rows from a table requires an index to locate the data in memory.</span></span>  
  
 <span data-ttu-id="8489d-105">哈希索引包含以数组形式组织的 Bucket 集合。</span><span class="sxs-lookup"><span data-stu-id="8489d-105">A hash index consists of a collection of buckets organized in an array.</span></span> <span data-ttu-id="8489d-106">哈希函数将索引键映射到哈希索引中对应的 Bucket。</span><span class="sxs-lookup"><span data-stu-id="8489d-106">A hash function maps index keys to corresponding buckets in the hash index.</span></span> <span data-ttu-id="8489d-107">下图展示映射到哈希索引中三个不同 Bucket 的三个索引键。</span><span class="sxs-lookup"><span data-stu-id="8489d-107">The following figure shows three index keys that are mapped to three different buckets in the hash index.</span></span> <span data-ttu-id="8489d-108">出于演示目的，哈希函数的名称为 f(x)。</span><span class="sxs-lookup"><span data-stu-id="8489d-108">For illustration purposes the hash function name is f(x).</span></span>  
  
 <span data-ttu-id="8489d-109">![映射到不同 Bucket 的索引键。](../../2014/database-engine/media/hekaton-tables-2.gif "映射到不同 Bucket 的索引键。")</span><span class="sxs-lookup"><span data-stu-id="8489d-109">![Index keys mapped to different buckets.](../../2014/database-engine/media/hekaton-tables-2.gif "Index keys mapped to different buckets.")</span></span>  
  
 <span data-ttu-id="8489d-110">用于哈希索引的哈希函数具有以下特征：</span><span class="sxs-lookup"><span data-stu-id="8489d-110">The hashing function used for hash indexes has the following characteristics:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="8489d-111">拥有一个用于所有哈希索引的哈希函数。</span><span class="sxs-lookup"><span data-stu-id="8489d-111">has one hash function that is used for all hash indexes.</span></span>  
  
-   <span data-ttu-id="8489d-112">哈希函数具有确定性。</span><span class="sxs-lookup"><span data-stu-id="8489d-112">The hash function is deterministic.</span></span> <span data-ttu-id="8489d-113">同一索引键始终映射到哈希索引中的同一 Bucket。</span><span class="sxs-lookup"><span data-stu-id="8489d-113">The same index key is always mapped to the same bucket in the hash index.</span></span>  
  
-   <span data-ttu-id="8489d-114">多个索引键可能映射到同一个哈希 Bucket。</span><span class="sxs-lookup"><span data-stu-id="8489d-114">Multiple index keys may be mapped to the same hash bucket.</span></span>  
  
-   <span data-ttu-id="8489d-115">哈希函数经过均衡处理，这意味着索引键值在哈希桶上的分布通常符合泊松分布。</span><span class="sxs-lookup"><span data-stu-id="8489d-115">The hash function is balanced, meaning that the distribution of index key values over hash buckets typically follows a Poisson distribution.</span></span>  
  
     <span data-ttu-id="8489d-116">泊松分布并非均匀分布。</span><span class="sxs-lookup"><span data-stu-id="8489d-116">Poisson distribution is not an even distribution.</span></span> <span data-ttu-id="8489d-117">索引键值并非均匀地分布在哈希 Bucket中。</span><span class="sxs-lookup"><span data-stu-id="8489d-117">Index key values are not evenly distributed in the hash buckets.</span></span> <span data-ttu-id="8489d-118">例如，对于*n*个哈希桶上的*n*个不同索引键的泊松分布会生成大约一个第三个空的存储桶，第三个存储桶包含一个索引键，另一个包含两个索引键。</span><span class="sxs-lookup"><span data-stu-id="8489d-118">For example, a Poisson distribution of *n* distinct index keys over *n* hash buckets results in approximately one third empty buckets, one third of the buckets containing one index key, and the other third containing two index keys.</span></span> <span data-ttu-id="8489d-119">少量 Bucket 将包含两个以上的键。</span><span class="sxs-lookup"><span data-stu-id="8489d-119">A small number of buckets will contain more than two keys.</span></span>  
  
 <span data-ttu-id="8489d-120">如果两个索引键映射到同一个哈希 Bucket，则产生哈希冲突。</span><span class="sxs-lookup"><span data-stu-id="8489d-120">If two index keys are mapped to the same hash bucket, there is a hash collision.</span></span> <span data-ttu-id="8489d-121">大量哈希冲突可影响读取操作的性能。</span><span class="sxs-lookup"><span data-stu-id="8489d-121">A large number of hash collisions can have a performance impact on read operations.</span></span>  
  
 <span data-ttu-id="8489d-122">内存哈希索引结构包含一个内存指针数组。</span><span class="sxs-lookup"><span data-stu-id="8489d-122">The in-memory hash index structure consists of an array of memory pointers.</span></span> <span data-ttu-id="8489d-123">每个 Bucket 映射到该数组中的一个偏移位置。</span><span class="sxs-lookup"><span data-stu-id="8489d-123">Each bucket maps to an offset in this array.</span></span> <span data-ttu-id="8489d-124">数组中的每个 Bucket 指向该哈希 Bucket 中的第一行。</span><span class="sxs-lookup"><span data-stu-id="8489d-124">Each bucket in the array points to the first row in that hash bucket.</span></span> <span data-ttu-id="8489d-125">Bucket 中的每行指向下行，因而形成了每个哈希 Bucket 的行链，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="8489d-125">Each row in the bucket points to the next row, thus resulting in a chain of rows for each hash bucket, as illustrated in the following figure.</span></span>  
  
 <span data-ttu-id="8489d-126">![内存中哈希索引结构。](../../2014/database-engine/media/hekaton-tables-3.gif "内存中哈希索引结构。")</span><span class="sxs-lookup"><span data-stu-id="8489d-126">![The in-memory hash index structure.](../../2014/database-engine/media/hekaton-tables-3.gif "The in-memory hash index structure.")</span></span>  
  
 <span data-ttu-id="8489d-127">该图有三个包含行的 Bucket。</span><span class="sxs-lookup"><span data-stu-id="8489d-127">The figure has three buckets with rows.</span></span> <span data-ttu-id="8489d-128">顶部的第二个 Bucket 包含三个红色行。</span><span class="sxs-lookup"><span data-stu-id="8489d-128">The second bucket from the top contains the three red rows.</span></span> <span data-ttu-id="8489d-129">第四个 Bucket 包含一个蓝色行。</span><span class="sxs-lookup"><span data-stu-id="8489d-129">The fourth bucket contains the single blue row.</span></span> <span data-ttu-id="8489d-130">底部的 Bucket 包含两个绿色行。</span><span class="sxs-lookup"><span data-stu-id="8489d-130">The bottom bucket contains the two green rows.</span></span> <span data-ttu-id="8489d-131">这些可能是同一行的不同版本。</span><span class="sxs-lookup"><span data-stu-id="8489d-131">These could be different versions of the same row.</span></span>  
  
 <span data-ttu-id="8489d-132">有关内存优化表的索引的详细信息，请参阅[在内存优化表上使用索引的准则](../relational-databases/in-memory-oltp/memory-optimized-tables.md)。</span><span class="sxs-lookup"><span data-stu-id="8489d-132">For more information about indexes for memory-optimized tables, see [Guidelines for Using Indexes on Memory-Optimized Tables](../relational-databases/in-memory-oltp/memory-optimized-tables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8489d-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8489d-133">See Also</span></span>  
 [<span data-ttu-id="8489d-134">内存优化表上的索引</span><span class="sxs-lookup"><span data-stu-id="8489d-134">Indexes on Memory-Optimized Tables</span></span>](../../2014/database-engine/indexes-on-memory-optimized-tables.md)  
  
  
