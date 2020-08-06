---
title: 内存优化表中的表和行大小 | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: b0a248a4-4488-4cc8-89fc-46906a8c24a1
author: rothja
ms.author: jroth
ms.openlocfilehash: 74cc40b7d1f2d0132d79d1e9ae15c2321ac9b74a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693862"
---
# <a name="table-and-row-size-in-memory-optimized-tables"></a><span data-ttu-id="6bf9c-102">内存优化表中的表和行大小</span><span class="sxs-lookup"><span data-stu-id="6bf9c-102">Table and Row Size in Memory-Optimized Tables</span></span>
  <span data-ttu-id="6bf9c-103">内存优化表由行和索引的集合组成，其中包含行的指针。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-103">A memory-optimized table consists of a collection of rows and indexes that contain pointers to rows.</span></span> <span data-ttu-id="6bf9c-104">在一个内存优化表中，行不能长于 8,060 字节。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-104">In a memory-optimized table, rows cannot be longer than 8,060 bytes.</span></span> <span data-ttu-id="6bf9c-105">了解内存优化表的大小将帮助您了解计算机是否具有足够的内存。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-105">Understanding the size of a memory-optimized table will help you understand if your computer has enough memory.</span></span>  
  
 <span data-ttu-id="6bf9c-106">有两个原因要计算表和行大小：</span><span class="sxs-lookup"><span data-stu-id="6bf9c-106">There are two reasons for computing table and row size:</span></span>  
  
-   <span data-ttu-id="6bf9c-107">一个表使用多少内存？</span><span class="sxs-lookup"><span data-stu-id="6bf9c-107">How much memory does a table use?</span></span>  
  
    -   <span data-ttu-id="6bf9c-108">表使用的内存量无法精确计算。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-108">The amount of memory used by the table cannot be calculated exactly.</span></span> <span data-ttu-id="6bf9c-109">有很多因素影响使用的内存量。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-109">Many factors affect the amount of memory used.</span></span> <span data-ttu-id="6bf9c-110">例如基于页的内存分配、位置、缓存和填充等因素。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-110">Factors such as page-based memory allocation, locality, caching, and padding.</span></span> <span data-ttu-id="6bf9c-111">还有具有活动事务关联或等待垃圾收集的多个行版本。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-111">Also, multiple versions of rows that either have active transactions associated or that are waiting for garbage collection.</span></span>  
  
    -   <span data-ttu-id="6bf9c-112">表中数据和索引所需的最小大小由下面讨论的 [表大小] 计算给定。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-112">The minimum size required for the data and indexes in the table is given by the calculation for [table size], discussed below.</span></span>  
  
    -   <span data-ttu-id="6bf9c-113">计算内存使用量最好也不过是个近似值，建议您将容量规划包含在部署计划中。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-113">Calculating memory use is at best an approximation and you are advised to include capacity planning in your deployment plans.</span></span>  
  
-   <span data-ttu-id="6bf9c-114">行的数据大小是多少，是否满足 8,060 字节行大小限制？</span><span class="sxs-lookup"><span data-stu-id="6bf9c-114">The data size of a row, and does it fit in the 8,060 byte row size limitation?</span></span> <span data-ttu-id="6bf9c-115">要回答这些问题，需要使用下面讨论的 [行正文大小] 计算。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-115">To answer these questions, use the computation for [row body size], discussed below.</span></span>  
  
 <span data-ttu-id="6bf9c-116">下图是一个包含索引和行的表，因而也就有行标题和正文：</span><span class="sxs-lookup"><span data-stu-id="6bf9c-116">The following figure illustrates a table with indexes and rows, which in turn have row headers and bodies:</span></span>  
  
 <span data-ttu-id="6bf9c-117">![内存优化表。](../../database-engine/media/hekaton-guide-1.gif "内存优化表。")</span><span class="sxs-lookup"><span data-stu-id="6bf9c-117">![Memory optimized table.](../../database-engine/media/hekaton-guide-1.gif "Memory optimized table.")</span></span>  
<span data-ttu-id="6bf9c-118">内存优化表，由索引和行组成。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-118">Memory-optimized table, consisting of indexes and rows.</span></span>  
  
 <span data-ttu-id="6bf9c-119">内存中的表大小（以字节为单位）计算如下：</span><span class="sxs-lookup"><span data-stu-id="6bf9c-119">The in-memory size of a table, in bytes, is computed as follows:</span></span>  
  
```  
[table size] = [size of index 1] + ... + [size of index n] + ([row size] * [row count])  
```  
  
 <span data-ttu-id="6bf9c-120">哈希索引的大小是在表创建时固定下来的，取决于实际 Bucket 计数。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-120">The size of a hash index is fixed at table creation time and depends on the actual bucket count.</span></span> <span data-ttu-id="6bf9c-121">用索引规范指定的 bucket_count 舍入为最近的 2 次幂以获取 [实际 Bucket 计数]。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-121">The bucket_count specified with the index specification is rounded up to the nearest power of 2 to obtain the [actual bucket count].</span></span> <span data-ttu-id="6bf9c-122">例如，如果指定的 bucket_count 为 100000，则索引的 [实际 Bucket 计数] 为 131072。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-122">For example, if the specified bucket_count is 100000, the [actual bucket count] for the index is 131072.</span></span>  
  
```  
[hash index size] = 8 * [actual bucket count]  
```  
  
 <span data-ttu-id="6bf9c-123">行大小是通过添加标题和正文计算的：</span><span class="sxs-lookup"><span data-stu-id="6bf9c-123">The row size is computed by adding the header and the body:</span></span>  
  
```  
[row size] = [row header size] + [actual row body size]  
[row header size] = 24 + 8 * [number of indices]  
```  
  
 <span data-ttu-id="6bf9c-124">**行正文大小**</span><span class="sxs-lookup"><span data-stu-id="6bf9c-124">**Row body size**</span></span>  
  
 <span data-ttu-id="6bf9c-125">[行正文大小] 的计算在下表中讨论。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-125">The calculation of [row body size] is discussed in the following table.</span></span>  
  
 <span data-ttu-id="6bf9c-126">对于行正文大小，有两种不同的计算：计算大小和实际大小。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-126">There are two different computations for row body size: computed size and the actual size:</span></span>  
  
-   <span data-ttu-id="6bf9c-127">计算大小表示为 [计算行正文大小]，用于确定是否超出了 8,060 字节的行大小限制。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-127">The computed size, denoted with [computed row body size], is used to determine if the row size limitation of 8,060 bytes is exceeded.</span></span>  
  
-   <span data-ttu-id="6bf9c-128">实际大小表示为 [实际行正文大小]，是行正文在内存和检查点文件中的实际存储大小。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-128">The actual size, denoted with [actual row body size], is the actual storage size of the row body in memory and in the checkpoint files.</span></span>  
  
 <span data-ttu-id="6bf9c-129">[计算行正文大小] 和 [实际行正文大小] 的计算方式相似。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-129">Both [computed row body size] and [actual row body size] are calculated similarly.</span></span> <span data-ttu-id="6bf9c-130">唯一的区别是 (n)varchar(i) 和 varbinary(i) 列大小的计算，如下表底部所示。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-130">The only difference is the calculation of the size of (n)varchar(i) and varbinary(i) columns, as reflected at the bottom of the following table.</span></span> <span data-ttu-id="6bf9c-131">计算行正文大小使用声明的大小 *i* 作为列大小，而实际行正文大小使用实际数据大小。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-131">The computed row body size uses the declared size *i* as the size of the column, while the actual row body size uses the actual size of the data.</span></span>  
  
 <span data-ttu-id="6bf9c-132">下表介绍行正文大小的计算，公式为 [实际行正文大小] = SUM([浅表类型的大小]) + 2 + 2 \* [深表类型列数]。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-132">The following table describes the calculation of the row body size, given as [actual row body size] = SUM([size of shallow types]) + 2 + 2 \* [number of deep type columns].</span></span>  
  
|<span data-ttu-id="6bf9c-133">部分</span><span class="sxs-lookup"><span data-stu-id="6bf9c-133">Section</span></span>|<span data-ttu-id="6bf9c-134">大小</span><span class="sxs-lookup"><span data-stu-id="6bf9c-134">Size</span></span>|<span data-ttu-id="6bf9c-135">注释</span><span class="sxs-lookup"><span data-stu-id="6bf9c-135">Comments</span></span>|  
|-------------|----------|--------------|  
|<span data-ttu-id="6bf9c-136">浅表类型列</span><span class="sxs-lookup"><span data-stu-id="6bf9c-136">Shallow type columns</span></span>|<span data-ttu-id="6bf9c-137">SUM([浅表类型的大小])</span><span class="sxs-lookup"><span data-stu-id="6bf9c-137">SUM([size of shallow types])</span></span><br /><br /> <span data-ttu-id="6bf9c-138">**各类型的大小如下：**</span><span class="sxs-lookup"><span data-stu-id="6bf9c-138">**Size of the individual types is as follows:**</span></span><br /><br /> <span data-ttu-id="6bf9c-139">Bit &#124; 1</span><span class="sxs-lookup"><span data-stu-id="6bf9c-139">Bit &#124; 1</span></span><br /><br /> <span data-ttu-id="6bf9c-140">Tinyint &#124; 1</span><span class="sxs-lookup"><span data-stu-id="6bf9c-140">Tinyint &#124; 1</span></span><br /><br /> <span data-ttu-id="6bf9c-141">Smallint &#124; 2</span><span class="sxs-lookup"><span data-stu-id="6bf9c-141">Smallint &#124; 2</span></span><br /><br /> <span data-ttu-id="6bf9c-142">Int &#124; 4</span><span class="sxs-lookup"><span data-stu-id="6bf9c-142">Int &#124; 4</span></span><br /><br /> <span data-ttu-id="6bf9c-143">Real &#124; 4</span><span class="sxs-lookup"><span data-stu-id="6bf9c-143">Real &#124; 4</span></span><br /><br /> <span data-ttu-id="6bf9c-144">Smalldatetime &#124; 4</span><span class="sxs-lookup"><span data-stu-id="6bf9c-144">Smalldatetime &#124; 4</span></span><br /><br /> <span data-ttu-id="6bf9c-145">Smallmoney &#124; 4</span><span class="sxs-lookup"><span data-stu-id="6bf9c-145">Smallmoney &#124; 4</span></span><br /><br /> <span data-ttu-id="6bf9c-146">Bigint &#124; 8</span><span class="sxs-lookup"><span data-stu-id="6bf9c-146">Bigint &#124; 8</span></span><br /><br /> <span data-ttu-id="6bf9c-147">Datetime &#124; 8</span><span class="sxs-lookup"><span data-stu-id="6bf9c-147">Datetime &#124; 8</span></span><br /><br /> <span data-ttu-id="6bf9c-148">Datetime2 &#124; 8</span><span class="sxs-lookup"><span data-stu-id="6bf9c-148">Datetime2 &#124; 8</span></span><br /><br /> <span data-ttu-id="6bf9c-149">Float 8</span><span class="sxs-lookup"><span data-stu-id="6bf9c-149">Float 8</span></span><br /><br /> <span data-ttu-id="6bf9c-150">Money 8</span><span class="sxs-lookup"><span data-stu-id="6bf9c-150">Money 8</span></span><br /><br /> <span data-ttu-id="6bf9c-151">数值 (精度 <= 18) &#124; 8</span><span class="sxs-lookup"><span data-stu-id="6bf9c-151">Numeric (precision <=18) &#124; 8</span></span><br /><br /> <span data-ttu-id="6bf9c-152">Time &#124; 8</span><span class="sxs-lookup"><span data-stu-id="6bf9c-152">Time &#124; 8</span></span><br /><br /> <span data-ttu-id="6bf9c-153">数值 (精度>18) &#124; 16</span><span class="sxs-lookup"><span data-stu-id="6bf9c-153">Numeric(precision>18) &#124; 16</span></span><br /><br /> <span data-ttu-id="6bf9c-154">Uniqueidentifier &#124; 16</span><span class="sxs-lookup"><span data-stu-id="6bf9c-154">Uniqueidentifier &#124; 16</span></span>||  
|<span data-ttu-id="6bf9c-155">浅表列填充</span><span class="sxs-lookup"><span data-stu-id="6bf9c-155">Shallow column padding</span></span>|<span data-ttu-id="6bf9c-156">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="6bf9c-156">Possible values are:</span></span><br /><br /> <span data-ttu-id="6bf9c-157">如果存在深表类型列并且浅表列的总数据大小是奇数，则为 1。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-157">1 if there are deep type columns and the total data size of the shallow columns is as odd number.</span></span><br /><br /> <span data-ttu-id="6bf9c-158">否则为 0</span><span class="sxs-lookup"><span data-stu-id="6bf9c-158">0 otherwise</span></span>|<span data-ttu-id="6bf9c-159">深表类型为类型 (var)binary 和 (n)(var)char。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-159">Deep types are the types (var)binary and (n)(var)char.</span></span>|  
|<span data-ttu-id="6bf9c-160">深表类型列的偏移数组</span><span class="sxs-lookup"><span data-stu-id="6bf9c-160">Offset array for deep type columns</span></span>|<span data-ttu-id="6bf9c-161">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="6bf9c-161">Possible values are:</span></span><br /><br /> <span data-ttu-id="6bf9c-162">如果没有深表类型列，则为 0</span><span class="sxs-lookup"><span data-stu-id="6bf9c-162">0 if there are no deep type columns</span></span><br /><br /> <span data-ttu-id="6bf9c-163">否则为 2 + 2 \* [深表类型列数]</span><span class="sxs-lookup"><span data-stu-id="6bf9c-163">2 + 2 \* [number of deep type columns] otherwise</span></span>|<span data-ttu-id="6bf9c-164">深表类型为类型 (var)binary 和 (n)(var)char。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-164">Deep types are the types (var)binary and (n)(var)char.</span></span>|  
|<span data-ttu-id="6bf9c-165">NULL 数组</span><span class="sxs-lookup"><span data-stu-id="6bf9c-165">NULL array</span></span>|<span data-ttu-id="6bf9c-166">[可以为 Null 的列数] / 8，舍入为完整字节。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-166">[number of nullable columns] / 8, rounded up to full bytes.</span></span>|<span data-ttu-id="6bf9c-167">数组每个可以为 Null 的列有一位。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-167">The array has one bit per nullable column.</span></span> <span data-ttu-id="6bf9c-168">这舍入为完整字节。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-168">This is rounded up to full bytes.</span></span>|  
|<span data-ttu-id="6bf9c-169">NULL 数组填充</span><span class="sxs-lookup"><span data-stu-id="6bf9c-169">NULL array padding</span></span>|<span data-ttu-id="6bf9c-170">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="6bf9c-170">Possible values are:</span></span><br /><br /> <span data-ttu-id="6bf9c-171">如果存在深表类型列并且 NULL 数组的大小为奇数字节，则为 1。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-171">1 if there are deep type columns and the size of the NULL array is an odd number of bytes.</span></span><br /><br /> <span data-ttu-id="6bf9c-172">否则为 0</span><span class="sxs-lookup"><span data-stu-id="6bf9c-172">0 otherwise</span></span>|<span data-ttu-id="6bf9c-173">深表类型为类型 (var)binary 和 (n)(var)char。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-173">Deep types are the types (var)binary and (n)(var)char.</span></span>|  
|<span data-ttu-id="6bf9c-174">填充</span><span class="sxs-lookup"><span data-stu-id="6bf9c-174">Padding</span></span>|<span data-ttu-id="6bf9c-175">如果没有深表类型列：0</span><span class="sxs-lookup"><span data-stu-id="6bf9c-175">If there are no deep type columns: 0</span></span><br /><br /> <span data-ttu-id="6bf9c-176">如果有深表类型列，则根据浅表列需要的最大对齐添加 0-7 个填充字节。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-176">If there are deep type columns, 0-7 bytes of padding is added, based on the largest alignment required by a shallow column.</span></span> <span data-ttu-id="6bf9c-177">每个浅表列都需要与上述大小相等的对齐，而 GUID 列需要 1（而不是 16）字节的对齐，数值列始终需要 8（而不是 16）字节的对齐。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-177">Each shallow column requires alignment equal to its size as documented above, except that GUID columns need alignment of 1 byte (not 16) and numeric columns always need alignment of 8 bytes (never 16).</span></span> <span data-ttu-id="6bf9c-178">所有浅表列间使用最大的对齐要求，添加了 0-7 个字节，现在总大小（不带深表类型列）是所需对齐的数倍。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-178">The largest alignment requirement among all shallow columns is used, and 0-7 bytes of padding is added in such a way that the total size so far (without the deep type columns) is a multiple of the required alignment.</span></span>|<span data-ttu-id="6bf9c-179">深表类型为类型 (var)binary 和 (n)(var)char。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-179">Deep types are the types (var)binary and (n)(var)char.</span></span>|  
|<span data-ttu-id="6bf9c-180">固定长度的深表类型列</span><span class="sxs-lookup"><span data-stu-id="6bf9c-180">Fixed-length deep type columns</span></span>|<span data-ttu-id="6bf9c-181">SUM([固定长度深表类型列的大小])</span><span class="sxs-lookup"><span data-stu-id="6bf9c-181">SUM([size of fixed length deep type columns])</span></span><br /><br /> <span data-ttu-id="6bf9c-182">各列大小如下：</span><span class="sxs-lookup"><span data-stu-id="6bf9c-182">The size of each column is as follows:</span></span><br /><br /> <span data-ttu-id="6bf9c-183">对于 char(i) 和 binary(i)，为 i。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-183">i for char(i) and binary(i).</span></span><br /><br /> <span data-ttu-id="6bf9c-184">对于 nchar(i)，为 2 \* i</span><span class="sxs-lookup"><span data-stu-id="6bf9c-184">2 \* i for nchar(i)</span></span>|<span data-ttu-id="6bf9c-185">固定长度深表类型列是类型为 char(i)、nchar(i) 或 binary(i) 的列。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-185">Fixed-length deep type columns are columns of type char(i), nchar(i), or binary(i).</span></span>|  
|<span data-ttu-id="6bf9c-186">可变长度深表类型列 [计算大小]</span><span class="sxs-lookup"><span data-stu-id="6bf9c-186">Variable length deep type columns [computed size]</span></span>|<span data-ttu-id="6bf9c-187">SUM([可变长度深表类型列的计算大小])</span><span class="sxs-lookup"><span data-stu-id="6bf9c-187">SUM([computed size of variable length deep type columns])</span></span><br /><br /> <span data-ttu-id="6bf9c-188">各列的计算大小如下：</span><span class="sxs-lookup"><span data-stu-id="6bf9c-188">The computed size of each column is as follows:</span></span><br /><br /> <span data-ttu-id="6bf9c-189">对于 varchar(i) 和 varbinary(i)，为 i</span><span class="sxs-lookup"><span data-stu-id="6bf9c-189">i for varchar(i) and varbinary(i)</span></span><br /><br /> <span data-ttu-id="6bf9c-190">对于 nvarchar(i)，为 2 \* i</span><span class="sxs-lookup"><span data-stu-id="6bf9c-190">2 \* i for nvarchar(i)</span></span>|<span data-ttu-id="6bf9c-191">此行仅适用于 [计算行正文大小]。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-191">This row only applied to [computed row body size].</span></span><br /><br /> <span data-ttu-id="6bf9c-192">可变长度的深表类型列是类型为 varchar(i)、nvarchar(i) 或 varbinary(i) 的列。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-192">Variable-length deep type columns are columns of type varchar(i), nvarchar(i), or varbinary(i).</span></span> <span data-ttu-id="6bf9c-193">计算大小由列的最大长度 (i) 决定。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-193">The computed size is determined by the max length (i) of the column.</span></span>|  
|<span data-ttu-id="6bf9c-194">可变长度深表类型列 [实际大小]</span><span class="sxs-lookup"><span data-stu-id="6bf9c-194">Variable length deep type columns [actual size]</span></span>|<span data-ttu-id="6bf9c-195">SUM([可变长度深表类型列的实际大小])</span><span class="sxs-lookup"><span data-stu-id="6bf9c-195">SUM([actual size of variable length deep type columns])</span></span><br /><br /> <span data-ttu-id="6bf9c-196">各列的实际大小如下：</span><span class="sxs-lookup"><span data-stu-id="6bf9c-196">The actual size of each column is as follows:</span></span><br /><br /> <span data-ttu-id="6bf9c-197">对于 varchar(i) 为 n，其中 n 是列中存储的字符数。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-197">n, where n is the number of characters stored in the column, for varchar(i).</span></span><br /><br /> <span data-ttu-id="6bf9c-198">对于 nvarchar(i) 为 2 \* n，其中 n 是列中存储的字符数。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-198">2 \* n, where n is the number of characters stored in the column, for nvarchar(i).</span></span><br /><br /> <span data-ttu-id="6bf9c-199">对于 varbinary(i) 为 n，其中 n 是列中存储的字节数。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-199">n, where n is the number of bytes stored in the column, for varbinary(i).</span></span>|<span data-ttu-id="6bf9c-200">此行仅适用于 [实际行正文大小]。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-200">This row only applied to [actual row body size].</span></span><br /><br /> <span data-ttu-id="6bf9c-201">实际大小由相应行中各列存储的数据决定。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-201">The actual size is determined by the data stored in the columns in the row.</span></span>|  
  
##  <a name="row-structure"></a><a name="bkmk_RowStructure"></a> <span data-ttu-id="6bf9c-202">行结构</span><span class="sxs-lookup"><span data-stu-id="6bf9c-202">Row Structure</span></span>  
 <span data-ttu-id="6bf9c-203">内存优化表中的行包含以下组成部分：</span><span class="sxs-lookup"><span data-stu-id="6bf9c-203">The rows in a memory-optimized table have the following components:</span></span>  
  
-   <span data-ttu-id="6bf9c-204">行标题，包含实现行版本控制所必需的时间戳。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-204">The row header contains the timestamp necessary to implement row versioning.</span></span> <span data-ttu-id="6bf9c-205">此外，行标题还包含索引指针，以实现哈希 Bucket 中的行链（如上所述）。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-205">The row header also contains the index pointer to implement the row chaining in the hash buckets (described above).</span></span>  
  
-   <span data-ttu-id="6bf9c-206">行正文，包含实际的列数据，其中包括一些辅助信息，如用于可为 Null 的列的 Null 数组，用于变长数据类型的偏移数组等。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-206">The row body contains the actual column data, which includes some auxiliary information like the null array for nullable columns and the offset array for variable-length data types.</span></span>  
  
 <span data-ttu-id="6bf9c-207">下图展示拥有两个索引的表的行结构：</span><span class="sxs-lookup"><span data-stu-id="6bf9c-207">The following figure illustrates the row structure for a table that has two indexes:</span></span>  
  
 <span data-ttu-id="6bf9c-208">![具有两个索引的表的行结构。](../../database-engine/media/hekaton-tables-4.gif "具有两个索引的表的行结构。")</span><span class="sxs-lookup"><span data-stu-id="6bf9c-208">![Row structure for a table that has two indexes.](../../database-engine/media/hekaton-tables-4.gif "Row structure for a table that has two indexes.")</span></span>  
  
 <span data-ttu-id="6bf9c-209">开始和结束时间戳指示特定行版本的有效时长。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-209">The begin and end timestamps indicate the period in which a particular row version is valid.</span></span> <span data-ttu-id="6bf9c-210">在该时间间隔启动的事务可看到该行版本。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-210">Transactions that start in this interval can see this row version.</span></span> <span data-ttu-id="6bf9c-211">有关详细信息，请参阅[内存优化表中的事务](memory-optimized-tables.md)。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-211">For more details see [Transactions in Memory-Optimized Tables](memory-optimized-tables.md).</span></span>  
  
 <span data-ttu-id="6bf9c-212">索引指针，指向链中属于该哈希 Bucket 的下行。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-212">The index pointers point to the next row in the chain belonging to the hash bucket.</span></span> <span data-ttu-id="6bf9c-213">下图展示一个表结构，其拥有两列（姓名，城市）、两个索引（一个针对姓名列、一个针对城市列）。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-213">The following figure illustrates the structure of a table with two columns (name, city), and with two indexes, one on the column name, and one on the column city.</span></span>  
  
 <span data-ttu-id="6bf9c-214">![具有两个列和索引的表的结构。](../../database-engine/media/hekaton-tables-5.gif "具有两个列和索引的表的结构。")</span><span class="sxs-lookup"><span data-stu-id="6bf9c-214">![Structure of a table with two columns and indexes.](../../database-engine/media/hekaton-tables-5.gif "Structure of a table with two columns and indexes.")</span></span>  
  
 <span data-ttu-id="6bf9c-215">在该图中，姓名 John 和 Jane 经哈希处理放入第一个 Bucket。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-215">In this figure, the names John and Jane are hashed to the first bucket.</span></span> <span data-ttu-id="6bf9c-216">Susan 经哈希处理放入第二个 Bucket。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-216">Susan is hashed to the second bucket.</span></span> <span data-ttu-id="6bf9c-217">城市 Beijing 和 Bogota 经哈希处理放入第一个 Bucket。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-217">The cities Beijing and Bogota are hashed to the first bucket.</span></span> <span data-ttu-id="6bf9c-218">Paris 和 Prague 经哈希处理放入第二个 Bucket。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-218">Paris and Prague are hashed to the second bucket.</span></span>  
  
 <span data-ttu-id="6bf9c-219">因此，针对姓名的哈希索引的链如下所示：</span><span class="sxs-lookup"><span data-stu-id="6bf9c-219">Thus, the chains for the hash index on name are as follows:</span></span>  
  
-   <span data-ttu-id="6bf9c-220">第一个 Bucket：(John, Beijing); (John, Paris); (Jane, Prague)</span><span class="sxs-lookup"><span data-stu-id="6bf9c-220">First bucket: (John, Beijing); (John, Paris); (Jane, Prague)</span></span>  
  
-   <span data-ttu-id="6bf9c-221">第二个 Bucket：(Susan, Bogota)</span><span class="sxs-lookup"><span data-stu-id="6bf9c-221">Second bucket: (Susan, Bogota)</span></span>  
  
 <span data-ttu-id="6bf9c-222">针对城市的索引的链如下所示：</span><span class="sxs-lookup"><span data-stu-id="6bf9c-222">The chains for the index on city are as follows:</span></span>  
  
-   <span data-ttu-id="6bf9c-223">第一个 Bucket：(John, Beijing), (Susan, Bogota)</span><span class="sxs-lookup"><span data-stu-id="6bf9c-223">First bucket: (John, Beijing), (Susan, Bogota)</span></span>  
  
-   <span data-ttu-id="6bf9c-224">第二个 Bucket：(John, Paris), (Jane, Prague)</span><span class="sxs-lookup"><span data-stu-id="6bf9c-224">Second bucket: (John, Paris), (Jane, Prague)</span></span>  
  
 <span data-ttu-id="6bf9c-225">结束时间戳 &#x221e; (无穷) 指示这是当前有效的行版本。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-225">An end timestamp &#x221e; (infinity) indicates that this is the currently valid version of the row.</span></span> <span data-ttu-id="6bf9c-226">该行自该行版本写入以来尚未更新或删除。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-226">The row has not been updated or deleted since this row version was written.</span></span>  
  
 <span data-ttu-id="6bf9c-227">对于大于 200 的时间，该表包含以下行：</span><span class="sxs-lookup"><span data-stu-id="6bf9c-227">For a time greater than 200, the table contains the following rows:</span></span>  
  
|<span data-ttu-id="6bf9c-228">名称</span><span class="sxs-lookup"><span data-stu-id="6bf9c-228">Name</span></span>|<span data-ttu-id="6bf9c-229">城市</span><span class="sxs-lookup"><span data-stu-id="6bf9c-229">City</span></span>|  
|----------|----------|  
|<span data-ttu-id="6bf9c-230">John</span><span class="sxs-lookup"><span data-stu-id="6bf9c-230">John</span></span>|<span data-ttu-id="6bf9c-231">北京</span><span class="sxs-lookup"><span data-stu-id="6bf9c-231">Beijing</span></span>|  
|<span data-ttu-id="6bf9c-232">Jane</span><span class="sxs-lookup"><span data-stu-id="6bf9c-232">Jane</span></span>|<span data-ttu-id="6bf9c-233">Prague</span><span class="sxs-lookup"><span data-stu-id="6bf9c-233">Prague</span></span>|  
  
 <span data-ttu-id="6bf9c-234">但是，开始时间为 100 的任意活动事务都将看到该表的以下版本：</span><span class="sxs-lookup"><span data-stu-id="6bf9c-234">However, any active transaction with begin time 100 will see the following version of the table:</span></span>  
  
|<span data-ttu-id="6bf9c-235">名称</span><span class="sxs-lookup"><span data-stu-id="6bf9c-235">Name</span></span>|<span data-ttu-id="6bf9c-236">城市</span><span class="sxs-lookup"><span data-stu-id="6bf9c-236">City</span></span>|  
|----------|----------|  
|<span data-ttu-id="6bf9c-237">John</span><span class="sxs-lookup"><span data-stu-id="6bf9c-237">John</span></span>|<span data-ttu-id="6bf9c-238">Paris</span><span class="sxs-lookup"><span data-stu-id="6bf9c-238">Paris</span></span>|  
|<span data-ttu-id="6bf9c-239">Jane</span><span class="sxs-lookup"><span data-stu-id="6bf9c-239">Jane</span></span>|<span data-ttu-id="6bf9c-240">Prague</span><span class="sxs-lookup"><span data-stu-id="6bf9c-240">Prague</span></span>|  
|<span data-ttu-id="6bf9c-241">Susan</span><span class="sxs-lookup"><span data-stu-id="6bf9c-241">Susan</span></span>|<span data-ttu-id="6bf9c-242">Bogata</span><span class="sxs-lookup"><span data-stu-id="6bf9c-242">Bogata</span></span>|  
  
##  <a name="example-table-and-row-size-computation"></a><a name="bkmk_ExampleComputation"></a> <span data-ttu-id="6bf9c-243">示例：表和行大小计算</span><span class="sxs-lookup"><span data-stu-id="6bf9c-243">Example: Table and Row Size Computation</span></span>  
 <span data-ttu-id="6bf9c-244">对于哈希索引，实际 Bucket 计数舍入为最近的 2 次幂。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-244">For hash indexes, the actual bucket count is rounded up to the nearest power of 2.</span></span> <span data-ttu-id="6bf9c-245">例如，如果指定的 bucket_count 为 100000，则索引的实际 Bucket 计数为 131072。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-245">For example, if the specified bucket_count is 100000, the actual bucket count for the index is 131072.</span></span>  
  
 <span data-ttu-id="6bf9c-246">考虑具有以下定义的 Orders 表：</span><span class="sxs-lookup"><span data-stu-id="6bf9c-246">Consider an Orders table with the following definition:</span></span>  
  
```sql  
CREATE TABLE dbo.Orders (  
     OrderID int NOT NULL   
           PRIMARY KEY NONCLUSTERED,  
     CustomerID int NOT NULL   
           INDEX IX_CustomerID HASH WITH (BUCKET_COUNT=10000),  
     OrderDate datetime NOT NULL,  
     OrderDescription nvarchar(1000)  
) WITH (MEMORY_OPTIMIZED=ON)  
GO  
```  
  
 <span data-ttu-id="6bf9c-247">请注意，此表有一个哈希索引和一个非聚集索引（主键）。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-247">Notice that this table has one hash index and a nonclustered index (the primary key).</span></span> <span data-ttu-id="6bf9c-248">它还有三个固定长度列和一个可变长度列，其中一列可以为 NULL (OrderDescription)。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-248">It also has three fixed-length columns and one variable-length column, with one of the columns being NULLable (OrderDescription).</span></span> <span data-ttu-id="6bf9c-249">假设 Orders 表有8379行，OrderDescription 列中的值的平均长度为78个字符。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-249">Let's assume the Orders table has 8379 rows, and the average length of the values in the OrderDescription column is 78 characters.</span></span>  
  
 <span data-ttu-id="6bf9c-250">要确定表大小，首先需要确定索引大小。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-250">To determine the table size, first determine the size of the indexes.</span></span> <span data-ttu-id="6bf9c-251">两个索引的 bucket_count 都指定为 10000。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-251">The bucket_count for both indexes is specified as 10000.</span></span> <span data-ttu-id="6bf9c-252">这舍入为最近的 2 次幂：16384。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-252">This is rounded up to the nearest power of 2: 16384.</span></span> <span data-ttu-id="6bf9c-253">因此，Orders 表的索引的总大小为：</span><span class="sxs-lookup"><span data-stu-id="6bf9c-253">Therefore, the total size of the indexes for the Orders table is:</span></span>  
  
```  
8 * 16384 = 131072 bytes  
```  
  
 <span data-ttu-id="6bf9c-254">其余为表数据大小，即</span><span class="sxs-lookup"><span data-stu-id="6bf9c-254">What remains is the table data size, which is,</span></span>  
  
```  
[row size] * [row count] = [row size] * 8379  
```  
  
 <span data-ttu-id="6bf9c-255">（示例表有 8379 行。）现在：</span><span class="sxs-lookup"><span data-stu-id="6bf9c-255">(The example table has 8379 rows.) Now, we have:</span></span>  
  
```  
[row size] = [row header size] + [actual row body size]  
[row header size] = 24 + 8 * [number of indices] = 24 + 8 * 1 = 32 bytes  
```  
  
 <span data-ttu-id="6bf9c-256">接下来，我们计算 [实际行正文大小]：</span><span class="sxs-lookup"><span data-stu-id="6bf9c-256">Next, let's calculate [actual row body size]:</span></span>  
  
-   <span data-ttu-id="6bf9c-257">浅表类型列：</span><span class="sxs-lookup"><span data-stu-id="6bf9c-257">Shallow type columns:</span></span>  
  
    ```  
    SUM([size of shallow types]) = 4 [int] + 4 [int] + 8 [datetime] = 16  
    ```  
  
-   <span data-ttu-id="6bf9c-258">因为总浅表列大小为偶数，所以浅表列填充为 0。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-258">Shallow column padding is 0, as the total shallow column size is even.</span></span>  
  
-   <span data-ttu-id="6bf9c-259">深表类型列的偏移数组：</span><span class="sxs-lookup"><span data-stu-id="6bf9c-259">Offset array for deep type columns:</span></span>  
  
    ```  
    2 + 2 * [number of deep type columns] = 2 + 2 * 1 = 4  
    ```  
  
-   <span data-ttu-id="6bf9c-260">NULL 数组 = 1</span><span class="sxs-lookup"><span data-stu-id="6bf9c-260">NULL array = 1</span></span>  
  
-   <span data-ttu-id="6bf9c-261">Null 数组填充 = 1，因为 Null 数组大小为奇数并且有深表类型列。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-261">NULL array padding = 1, as the NULL array size is odd and there is a deep type column.</span></span>  
  
-   <span data-ttu-id="6bf9c-262">填充</span><span class="sxs-lookup"><span data-stu-id="6bf9c-262">Padding</span></span>  
  
    -   <span data-ttu-id="6bf9c-263">8 是最大对齐要求。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-263">8 is the largest alignment requirement.</span></span>  
  
    -   <span data-ttu-id="6bf9c-264">目前大小为 16 + 0 + 4 + 1 + 1 = 22。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-264">Size so far is 16 + 0 + 4 + 1 + 1 = 22.</span></span>  
  
    -   <span data-ttu-id="6bf9c-265">最接近的 8 的倍数为 24。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-265">Nearest multiple of 8 is 24.</span></span>  
  
    -   <span data-ttu-id="6bf9c-266">总填充为 24 – 22 = 2 字节。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-266">Total padding is 24 - 22 = 2 bytes.</span></span>  
  
-   <span data-ttu-id="6bf9c-267">没有定长深表类型列（定长深表类型列：0。）。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-267">There are no fixed-length deep type columns (Fixed-length deep type columns: 0.).</span></span>  
  
-   <span data-ttu-id="6bf9c-268">深表类型列的实际大小为 2 \* 78 = 156。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-268">The actual size of deep type column is 2 \* 78 = 156.</span></span> <span data-ttu-id="6bf9c-269">唯一的深表类型列 OrderDescription 的类型为 nvarchar。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-269">The single deep type column OrderDescription has type nvarchar.</span></span>  
  
```  
[actual row body size] = 24 + 156 = 180 bytes  
```  
  
 <span data-ttu-id="6bf9c-270">完成计算：</span><span class="sxs-lookup"><span data-stu-id="6bf9c-270">To complete the calculation:</span></span>  
  
```  
[row size] = 32 + 180 = 212 bytes  
[table size] = 8 * 16384 + 212 * 8379 = 131072 + 1776348 = 1907420  
```  
  
 <span data-ttu-id="6bf9c-271">内存中的总表大小约为 2 MB。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-271">Total table size in memory is thus approximately 2 megabytes.</span></span> <span data-ttu-id="6bf9c-272">这不包括内存分配引起的可能开销以及访问此表的事务所需的行版本控制引起的可能开销。</span><span class="sxs-lookup"><span data-stu-id="6bf9c-272">This does not account for potential overhead incurred by memory allocation as well as any row versioning required for the transactions accessing this table.</span></span>  
  
 <span data-ttu-id="6bf9c-273">实际分配的内存和此表及其索引使用的内存可以通过以下查询获得：</span><span class="sxs-lookup"><span data-stu-id="6bf9c-273">The actual memory allocated for and used by this table and its indexes can be obtained through the following query:</span></span>  
  
```sql  
select * from sys.dm_db_xtp_table_memory_stats  
where object_id = object_id('dbo.Orders')  
```  
  
## <a name="see-also"></a><span data-ttu-id="6bf9c-274">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6bf9c-274">See Also</span></span>  
 [<span data-ttu-id="6bf9c-275">Memory-Optimized Tables</span><span class="sxs-lookup"><span data-stu-id="6bf9c-275">Memory-Optimized Tables</span></span>](memory-optimized-tables.md)  
  
  
