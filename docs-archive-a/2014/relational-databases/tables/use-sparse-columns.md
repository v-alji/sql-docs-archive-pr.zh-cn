---
title: 使用稀疏列 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- sparse columns, described
- null columns
- sparse columns
ms.assetid: ea7ddb87-f50b-46b6-9f5a-acab222a2ede
author: stevestein
ms.author: sstein
ms.openlocfilehash: b3068ac7a3094605bb809ac84c63766b64fda486
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586562"
---
# <a name="use-sparse-columns"></a><span data-ttu-id="f8391-102">使用稀疏列</span><span class="sxs-lookup"><span data-stu-id="f8391-102">Use Sparse Columns</span></span>
  <span data-ttu-id="f8391-103">稀疏列是对 Null 值采用优化的存储方式的普通列。</span><span class="sxs-lookup"><span data-stu-id="f8391-103">Sparse columns are ordinary columns that have an optimized storage for null values.</span></span> <span data-ttu-id="f8391-104">稀疏列减少了 Null 值的空间需求，但代价是检索非 Null 值的开销增加。</span><span class="sxs-lookup"><span data-stu-id="f8391-104">Sparse columns reduce the space requirements for null values at the cost of more overhead to retrieve nonnull values.</span></span> <span data-ttu-id="f8391-105">当至少能够节省 20% 到 40% 的空间时，才应考虑使用稀疏列。</span><span class="sxs-lookup"><span data-stu-id="f8391-105">Consider using sparse columns when the space saved is at least 20 percent to 40 percent.</span></span> <span data-ttu-id="f8391-106">稀疏列和列集是通过使用 [CREATE TABLE](/sql/t-sql/statements/create-table-transact-sql) 或 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) 语句定义的。</span><span class="sxs-lookup"><span data-stu-id="f8391-106">Sparse columns and column sets are defined by using the [CREATE TABLE](/sql/t-sql/statements/create-table-transact-sql) or [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) statements.</span></span>  
  
 <span data-ttu-id="f8391-107">稀疏列可以与列集和筛选索引一起使用：</span><span class="sxs-lookup"><span data-stu-id="f8391-107">Sparse columns can be used with column sets and filtered indexes:</span></span>  
  
-   <span data-ttu-id="f8391-108">列集</span><span class="sxs-lookup"><span data-stu-id="f8391-108">Column sets</span></span>  
  
     <span data-ttu-id="f8391-109">INSERT、UPDATE 和 DELETE 语句可以通过名称来引用稀疏列。</span><span class="sxs-lookup"><span data-stu-id="f8391-109">INSERT, UPDATE, and DELETE statements can reference the sparse columns by name.</span></span> <span data-ttu-id="f8391-110">但是，您也可以查看并处理表中组合为一个 XML 列的所有稀疏列。</span><span class="sxs-lookup"><span data-stu-id="f8391-110">However, you can also view and work with all the sparse columns of a table that are combined into a single XML column.</span></span> <span data-ttu-id="f8391-111">此列称为列集。</span><span class="sxs-lookup"><span data-stu-id="f8391-111">This column is called a column set.</span></span> <span data-ttu-id="f8391-112">有关列集的详细信息，请参阅 [使用列集](../tables/use-column-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="f8391-112">For more information about column sets, see [Use Column Sets](../tables/use-column-sets.md).</span></span>  
  
-   <span data-ttu-id="f8391-113">筛选索引</span><span class="sxs-lookup"><span data-stu-id="f8391-113">Filtered indexes</span></span>  
  
     <span data-ttu-id="f8391-114">因为稀疏列有许多 Null 值行，所以尤其适用于筛选索引。</span><span class="sxs-lookup"><span data-stu-id="f8391-114">Because sparse columns have many null-valued rows, they are especially appropriate for filtered indexes.</span></span> <span data-ttu-id="f8391-115">稀疏列的筛选索引可以仅仅对已填充值的行编制索引。</span><span class="sxs-lookup"><span data-stu-id="f8391-115">A filtered index on a sparse column can index only the rows that have populated values.</span></span> <span data-ttu-id="f8391-116">这会创建一个更小、更有效的索引。</span><span class="sxs-lookup"><span data-stu-id="f8391-116">This creates a smaller and more efficient index.</span></span> <span data-ttu-id="f8391-117">有关详细信息，请参阅 [Create Filtered Indexes](../indexes/indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="f8391-117">For more information, see [Create Filtered Indexes](../indexes/indexes.md).</span></span>  
  
 <span data-ttu-id="f8391-118">稀疏列和筛选索引使应用程序（如 [!INCLUDE[winSPServ](../../includes/winspserv-md.md)]）可以通过 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]有效地存储和访问大量的用户定义属性。</span><span class="sxs-lookup"><span data-stu-id="f8391-118">Sparse columns and filtered indexes enable applications, such as [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], to efficiently store and access a large number of user-defined properties by using [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="properties-of-sparse-columns"></a><span data-ttu-id="f8391-119">稀疏列的属性</span><span class="sxs-lookup"><span data-stu-id="f8391-119">Properties of Sparse Columns</span></span>  
 <span data-ttu-id="f8391-120">稀疏列具有以下特征：</span><span class="sxs-lookup"><span data-stu-id="f8391-120">Sparse columns have the following characteristics:</span></span>  
  
-   <span data-ttu-id="f8391-121">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 使用列定义中的 SPARSE 关键字来优化该列中的值的存储。</span><span class="sxs-lookup"><span data-stu-id="f8391-121">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] uses the SPARSE keyword in a column definition to optimize the storage of values in that column.</span></span> <span data-ttu-id="f8391-122">因此，当表中的任意行的列值为 NULL 时，该值将不需要存储。</span><span class="sxs-lookup"><span data-stu-id="f8391-122">Therefore, when the column value is NULL for any row in the table, the values require no storage.</span></span>  
  
-   <span data-ttu-id="f8391-123">具有稀疏列的表的目录视图与典型表的目录视图相同。</span><span class="sxs-lookup"><span data-stu-id="f8391-123">Catalog views for a table that has sparse columns are the same as for a typical table.</span></span> <span data-ttu-id="f8391-124">sys.columns 目录视图对于表中的每一列都包含一个对应的行，并包括一个列集（如果定义了列集）。</span><span class="sxs-lookup"><span data-stu-id="f8391-124">The sys.columns catalog view contains a row for each column in the table and includes a column set if one is defined.</span></span>  
  
-   <span data-ttu-id="f8391-125">稀疏列是存储层（而不是逻辑表）的一个属性。</span><span class="sxs-lookup"><span data-stu-id="f8391-125">Sparse columns are a property of the storage layer, rather than the logical table.</span></span> <span data-ttu-id="f8391-126">因此，SELECT…INTO 语句不会将稀疏列属性复制到新表中。</span><span class="sxs-lookup"><span data-stu-id="f8391-126">Therefore a SELECT...INTO statement does not copy over the sparse column property into a new table.</span></span>  
  
-   <span data-ttu-id="f8391-127">COLUMNS_UPDATED 函数返回一个 `varbinary` 值，以指示在 DML 操作期间更新的所有列。</span><span class="sxs-lookup"><span data-stu-id="f8391-127">The COLUMNS_UPDATED function returns a `varbinary` value to indicate all the columns that were updated during a DML action.</span></span> <span data-ttu-id="f8391-128">COLUMNS_UPDATED 函数返回的位如下：</span><span class="sxs-lookup"><span data-stu-id="f8391-128">The bits that are returned by the COLUMNS_UPDATED function are as follows:</span></span>  
  
    -   <span data-ttu-id="f8391-129">显式更新了稀疏列后，该稀疏列的对应位将设置为 1，列集的位将设置为 1。</span><span class="sxs-lookup"><span data-stu-id="f8391-129">When a sparse column is explicitly updated, the corresponding bit for that sparse column is set to 1, and the bit for the column set is set to 1.</span></span>  
  
    -   <span data-ttu-id="f8391-130">显式更新了列集后，列集的位将设置为 1，该表中的所有稀疏列的位将设置为 1。</span><span class="sxs-lookup"><span data-stu-id="f8391-130">When a column set is explicitly updated, the bit for the column set is set to 1, and the bits for all the sparse columns in that table are set to 1.</span></span>  
  
    -   <span data-ttu-id="f8391-131">对于插入操作，所有位都将设置为 1。</span><span class="sxs-lookup"><span data-stu-id="f8391-131">For insert operations, all bits are set to 1.</span></span>  
  
     <span data-ttu-id="f8391-132">有关列集的详细信息，请参阅 [使用列集](../tables/use-column-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="f8391-132">For more information about columns sets, see [Use Column Sets](../tables/use-column-sets.md).</span></span>  
  
 <span data-ttu-id="f8391-133">下面的数据类型不能指定为 SPARSE：</span><span class="sxs-lookup"><span data-stu-id="f8391-133">The following data types cannot be specified as SPARSE:</span></span>  
  
|||  
|-|-|  
|`geography`|`text`|  
|`geometry`|`timestamp`|  
|`image`|`user-defined data types`|  
|`ntext`||  
  
## <a name="estimated-space-savings-by-data-type"></a><span data-ttu-id="f8391-134">按数据类型所估算的空间节省量</span><span class="sxs-lookup"><span data-stu-id="f8391-134">Estimated Space Savings by Data Type</span></span>  
 <span data-ttu-id="f8391-135">相对于未标记为 SPARSE 的相同数据所需的空间，稀疏列在存储非 Null 值时需要的存储空间更多。</span><span class="sxs-lookup"><span data-stu-id="f8391-135">Sparse columns require more storage space for nonnull values than the space required for identical data that is not marked SPARSE.</span></span> <span data-ttu-id="f8391-136">下表说明了每种数据类型的空间使用情况。</span><span class="sxs-lookup"><span data-stu-id="f8391-136">The following tables show the space usage for each data type.</span></span> <span data-ttu-id="f8391-137">**NULL 百分比** 列指示数据必须有多少比例为 NULL，才能实现 40% 的净空间节省。</span><span class="sxs-lookup"><span data-stu-id="f8391-137">The **NULL Percentage** column indicates what percent of the data must be NULL for a net space savings of 40 percent.</span></span>  
  
 <span data-ttu-id="f8391-138">**固定长度的数据类型**</span><span class="sxs-lookup"><span data-stu-id="f8391-138">**Fixed-Length Data Types**</span></span>  
  
|<span data-ttu-id="f8391-139">数据类型</span><span class="sxs-lookup"><span data-stu-id="f8391-139">Data type</span></span>|<span data-ttu-id="f8391-140">非稀疏字节</span><span class="sxs-lookup"><span data-stu-id="f8391-140">Nonsparse bytes</span></span>|<span data-ttu-id="f8391-141">稀疏字节</span><span class="sxs-lookup"><span data-stu-id="f8391-141">Sparse bytes</span></span>|<span data-ttu-id="f8391-142">NULL 百分比</span><span class="sxs-lookup"><span data-stu-id="f8391-142">NULL percentage</span></span>|  
|---------------|---------------------|------------------|---------------------|  
|`bit`|<span data-ttu-id="f8391-143">0.125</span><span class="sxs-lookup"><span data-stu-id="f8391-143">0.125</span></span>|<span data-ttu-id="f8391-144">5</span><span class="sxs-lookup"><span data-stu-id="f8391-144">5</span></span>|<span data-ttu-id="f8391-145">98%</span><span class="sxs-lookup"><span data-stu-id="f8391-145">98%</span></span>|  
|`tinyint`|<span data-ttu-id="f8391-146">1</span><span class="sxs-lookup"><span data-stu-id="f8391-146">1</span></span>|<span data-ttu-id="f8391-147">5</span><span class="sxs-lookup"><span data-stu-id="f8391-147">5</span></span>|<span data-ttu-id="f8391-148">86%</span><span class="sxs-lookup"><span data-stu-id="f8391-148">86%</span></span>|  
|`smallint`|<span data-ttu-id="f8391-149">2</span><span class="sxs-lookup"><span data-stu-id="f8391-149">2</span></span>|<span data-ttu-id="f8391-150">6</span><span class="sxs-lookup"><span data-stu-id="f8391-150">6</span></span>|<span data-ttu-id="f8391-151">76%</span><span class="sxs-lookup"><span data-stu-id="f8391-151">76%</span></span>|  
|`int`|<span data-ttu-id="f8391-152">4</span><span class="sxs-lookup"><span data-stu-id="f8391-152">4</span></span>|<span data-ttu-id="f8391-153">8</span><span class="sxs-lookup"><span data-stu-id="f8391-153">8</span></span>|<span data-ttu-id="f8391-154">64%</span><span class="sxs-lookup"><span data-stu-id="f8391-154">64%</span></span>|  
|`bigint`|<span data-ttu-id="f8391-155">8</span><span class="sxs-lookup"><span data-stu-id="f8391-155">8</span></span>|<span data-ttu-id="f8391-156">12</span><span class="sxs-lookup"><span data-stu-id="f8391-156">12</span></span>|<span data-ttu-id="f8391-157">52%</span><span class="sxs-lookup"><span data-stu-id="f8391-157">52%</span></span>|  
|`real`|<span data-ttu-id="f8391-158">4</span><span class="sxs-lookup"><span data-stu-id="f8391-158">4</span></span>|<span data-ttu-id="f8391-159">8</span><span class="sxs-lookup"><span data-stu-id="f8391-159">8</span></span>|<span data-ttu-id="f8391-160">64%</span><span class="sxs-lookup"><span data-stu-id="f8391-160">64%</span></span>|  
|`float`|<span data-ttu-id="f8391-161">8</span><span class="sxs-lookup"><span data-stu-id="f8391-161">8</span></span>|<span data-ttu-id="f8391-162">12</span><span class="sxs-lookup"><span data-stu-id="f8391-162">12</span></span>|<span data-ttu-id="f8391-163">52%</span><span class="sxs-lookup"><span data-stu-id="f8391-163">52%</span></span>|  
|`smallmoney`|<span data-ttu-id="f8391-164">4</span><span class="sxs-lookup"><span data-stu-id="f8391-164">4</span></span>|<span data-ttu-id="f8391-165">8</span><span class="sxs-lookup"><span data-stu-id="f8391-165">8</span></span>|<span data-ttu-id="f8391-166">64%</span><span class="sxs-lookup"><span data-stu-id="f8391-166">64%</span></span>|  
|`money`|<span data-ttu-id="f8391-167">8</span><span class="sxs-lookup"><span data-stu-id="f8391-167">8</span></span>|<span data-ttu-id="f8391-168">12</span><span class="sxs-lookup"><span data-stu-id="f8391-168">12</span></span>|<span data-ttu-id="f8391-169">52%</span><span class="sxs-lookup"><span data-stu-id="f8391-169">52%</span></span>|  
|`smalldatetime`|<span data-ttu-id="f8391-170">4</span><span class="sxs-lookup"><span data-stu-id="f8391-170">4</span></span>|<span data-ttu-id="f8391-171">8</span><span class="sxs-lookup"><span data-stu-id="f8391-171">8</span></span>|<span data-ttu-id="f8391-172">64%</span><span class="sxs-lookup"><span data-stu-id="f8391-172">64%</span></span>|  
|`datetime`|<span data-ttu-id="f8391-173">8</span><span class="sxs-lookup"><span data-stu-id="f8391-173">8</span></span>|<span data-ttu-id="f8391-174">12</span><span class="sxs-lookup"><span data-stu-id="f8391-174">12</span></span>|<span data-ttu-id="f8391-175">52%</span><span class="sxs-lookup"><span data-stu-id="f8391-175">52%</span></span>|  
|`uniqueidentifier`|<span data-ttu-id="f8391-176">16</span><span class="sxs-lookup"><span data-stu-id="f8391-176">16</span></span>|<span data-ttu-id="f8391-177">20</span><span class="sxs-lookup"><span data-stu-id="f8391-177">20</span></span>|<span data-ttu-id="f8391-178">43%</span><span class="sxs-lookup"><span data-stu-id="f8391-178">43%</span></span>|  
|`date`|<span data-ttu-id="f8391-179">3</span><span class="sxs-lookup"><span data-stu-id="f8391-179">3</span></span>|<span data-ttu-id="f8391-180">7</span><span class="sxs-lookup"><span data-stu-id="f8391-180">7</span></span>|<span data-ttu-id="f8391-181">69%</span><span class="sxs-lookup"><span data-stu-id="f8391-181">69%</span></span>|  
  
 <span data-ttu-id="f8391-182">**精度依赖于长度的数据类型**</span><span class="sxs-lookup"><span data-stu-id="f8391-182">**Precision-Dependent-Length Data Types**</span></span>  
  
|<span data-ttu-id="f8391-183">数据类型</span><span class="sxs-lookup"><span data-stu-id="f8391-183">Data type</span></span>|<span data-ttu-id="f8391-184">非稀疏字节</span><span class="sxs-lookup"><span data-stu-id="f8391-184">Nonsparse bytes</span></span>|<span data-ttu-id="f8391-185">稀疏字节</span><span class="sxs-lookup"><span data-stu-id="f8391-185">Sparse bytes</span></span>|<span data-ttu-id="f8391-186">NULL 百分比</span><span class="sxs-lookup"><span data-stu-id="f8391-186">NULL percentage</span></span>|  
|---------------|---------------------|------------------|---------------------|  
|`datetime2(0)`|<span data-ttu-id="f8391-187">6</span><span class="sxs-lookup"><span data-stu-id="f8391-187">6</span></span>|<span data-ttu-id="f8391-188">10</span><span class="sxs-lookup"><span data-stu-id="f8391-188">10</span></span>|<span data-ttu-id="f8391-189">57%</span><span class="sxs-lookup"><span data-stu-id="f8391-189">57%</span></span>|  
|`datetime2(7)`|<span data-ttu-id="f8391-190">8</span><span class="sxs-lookup"><span data-stu-id="f8391-190">8</span></span>|<span data-ttu-id="f8391-191">12</span><span class="sxs-lookup"><span data-stu-id="f8391-191">12</span></span>|<span data-ttu-id="f8391-192">52%</span><span class="sxs-lookup"><span data-stu-id="f8391-192">52%</span></span>|  
|`time(0)`|<span data-ttu-id="f8391-193">3</span><span class="sxs-lookup"><span data-stu-id="f8391-193">3</span></span>|<span data-ttu-id="f8391-194">7</span><span class="sxs-lookup"><span data-stu-id="f8391-194">7</span></span>|<span data-ttu-id="f8391-195">69%</span><span class="sxs-lookup"><span data-stu-id="f8391-195">69%</span></span>|  
|`time(7)`|<span data-ttu-id="f8391-196">5</span><span class="sxs-lookup"><span data-stu-id="f8391-196">5</span></span>|<span data-ttu-id="f8391-197">9</span><span class="sxs-lookup"><span data-stu-id="f8391-197">9</span></span>|<span data-ttu-id="f8391-198">60%</span><span class="sxs-lookup"><span data-stu-id="f8391-198">60%</span></span>|  
|`datetimetoffset(0)`|<span data-ttu-id="f8391-199">8</span><span class="sxs-lookup"><span data-stu-id="f8391-199">8</span></span>|<span data-ttu-id="f8391-200">12</span><span class="sxs-lookup"><span data-stu-id="f8391-200">12</span></span>|<span data-ttu-id="f8391-201">52%</span><span class="sxs-lookup"><span data-stu-id="f8391-201">52%</span></span>|  
|`datetimetoffset (7)`|<span data-ttu-id="f8391-202">10</span><span class="sxs-lookup"><span data-stu-id="f8391-202">10</span></span>|<span data-ttu-id="f8391-203">14</span><span class="sxs-lookup"><span data-stu-id="f8391-203">14</span></span>|<span data-ttu-id="f8391-204">49%</span><span class="sxs-lookup"><span data-stu-id="f8391-204">49%</span></span>|  
|`decimal/numeric(1,s)`|<span data-ttu-id="f8391-205">5</span><span class="sxs-lookup"><span data-stu-id="f8391-205">5</span></span>|<span data-ttu-id="f8391-206">9</span><span class="sxs-lookup"><span data-stu-id="f8391-206">9</span></span>|<span data-ttu-id="f8391-207">60%</span><span class="sxs-lookup"><span data-stu-id="f8391-207">60%</span></span>|  
|`decimal/numeric(38,s)`|<span data-ttu-id="f8391-208">17</span><span class="sxs-lookup"><span data-stu-id="f8391-208">17</span></span>|<span data-ttu-id="f8391-209">21</span><span class="sxs-lookup"><span data-stu-id="f8391-209">21</span></span>|<span data-ttu-id="f8391-210">42%</span><span class="sxs-lookup"><span data-stu-id="f8391-210">42%</span></span>|  
|`vardecimal(p,s)`|<span data-ttu-id="f8391-211">使用 `decimal` 类型作为保守的估计。</span><span class="sxs-lookup"><span data-stu-id="f8391-211">Use the `decimal` type as a conservative estimate.</span></span>|||  
  
 <span data-ttu-id="f8391-212">**数据依赖长度的数据类型**</span><span class="sxs-lookup"><span data-stu-id="f8391-212">**Data-Dependent-Length Data Types**</span></span>  
  
|<span data-ttu-id="f8391-213">数据类型</span><span class="sxs-lookup"><span data-stu-id="f8391-213">Data type</span></span>|<span data-ttu-id="f8391-214">非稀疏字节</span><span class="sxs-lookup"><span data-stu-id="f8391-214">Nonsparse bytes</span></span>|<span data-ttu-id="f8391-215">稀疏字节</span><span class="sxs-lookup"><span data-stu-id="f8391-215">Sparse bytes</span></span>|<span data-ttu-id="f8391-216">NULL 百分比</span><span class="sxs-lookup"><span data-stu-id="f8391-216">NULL percentage</span></span>|  
|---------------|---------------------|------------------|---------------------|  
|`sql_variant`|<span data-ttu-id="f8391-217">随基础数据类型而异</span><span class="sxs-lookup"><span data-stu-id="f8391-217">Varies with the underlying data type</span></span>|||  
|<span data-ttu-id="f8391-218">`varchar` 或 `char`</span><span class="sxs-lookup"><span data-stu-id="f8391-218">`varchar` or `char`</span></span>|<span data-ttu-id="f8391-219">2\*</span><span class="sxs-lookup"><span data-stu-id="f8391-219">2\*</span></span>|<span data-ttu-id="f8391-220">4\*</span><span class="sxs-lookup"><span data-stu-id="f8391-220">4\*</span></span>|<span data-ttu-id="f8391-221">60%</span><span class="sxs-lookup"><span data-stu-id="f8391-221">60%</span></span>|  
|<span data-ttu-id="f8391-222">`nvarchar` 或 `nchar`</span><span class="sxs-lookup"><span data-stu-id="f8391-222">`nvarchar` or `nchar`</span></span>|<span data-ttu-id="f8391-223">2\*</span><span class="sxs-lookup"><span data-stu-id="f8391-223">2\*</span></span>|<span data-ttu-id="f8391-224">4\*+</span><span class="sxs-lookup"><span data-stu-id="f8391-224">4\*+</span></span>|<span data-ttu-id="f8391-225">60%</span><span class="sxs-lookup"><span data-stu-id="f8391-225">60%</span></span>|  
|<span data-ttu-id="f8391-226">`varbinary` 或 `binary`</span><span class="sxs-lookup"><span data-stu-id="f8391-226">`varbinary` or `binary`</span></span>|<span data-ttu-id="f8391-227">2\*</span><span class="sxs-lookup"><span data-stu-id="f8391-227">2\*</span></span>|<span data-ttu-id="f8391-228">4\*</span><span class="sxs-lookup"><span data-stu-id="f8391-228">4\*</span></span>|<span data-ttu-id="f8391-229">60%</span><span class="sxs-lookup"><span data-stu-id="f8391-229">60%</span></span>|  
|`xml`|<span data-ttu-id="f8391-230">2\*</span><span class="sxs-lookup"><span data-stu-id="f8391-230">2\*</span></span>|<span data-ttu-id="f8391-231">4\*</span><span class="sxs-lookup"><span data-stu-id="f8391-231">4\*</span></span>|<span data-ttu-id="f8391-232">60%</span><span class="sxs-lookup"><span data-stu-id="f8391-232">60%</span></span>|  
|`hierarchyid`|<span data-ttu-id="f8391-233">2\*</span><span class="sxs-lookup"><span data-stu-id="f8391-233">2\*</span></span>|<span data-ttu-id="f8391-234">4\*</span><span class="sxs-lookup"><span data-stu-id="f8391-234">4\*</span></span>|<span data-ttu-id="f8391-235">60%</span><span class="sxs-lookup"><span data-stu-id="f8391-235">60%</span></span>|  
  
 <span data-ttu-id="f8391-236">\*长度等于该类型中包含的数据的平均长度再多出 2 个或 4 个字节。</span><span class="sxs-lookup"><span data-stu-id="f8391-236">\*The length is equal to the average of the data that is contained in the type, plus 2 or 4 bytes.</span></span>  
  
## <a name="in-memory-overhead-required-for-updates-to-sparse-columns"></a><span data-ttu-id="f8391-237">更新稀疏列所需的内存中开销</span><span class="sxs-lookup"><span data-stu-id="f8391-237">In-Memory Overhead Required for Updates to Sparse Columns</span></span>  
 <span data-ttu-id="f8391-238">当使用稀疏列设计表时，请记住，在更新行时，表中的每个非 NULL 值稀疏列需要 2 个字节的额外开销。</span><span class="sxs-lookup"><span data-stu-id="f8391-238">When designing tables with sparse columns, keep in mind that an additional 2 bytes of overhead are required for each non-null sparse column in the table when a row is being updated.</span></span> <span data-ttu-id="f8391-239">由于此额外的内存要求，当总的行大小（包括此内存开销）超过 8019 但没有列可以推送到行外时，更新可能意外失败，错误为 576。</span><span class="sxs-lookup"><span data-stu-id="f8391-239">As a result of this additional memory requirement, updates can fail unexpectedly with error 576 when the total row size, including this memory overhead, exceeds 8019, and no columns can be pushed off the row.</span></span>  
  
 <span data-ttu-id="f8391-240">以具有 600 个 bigint 类型的稀疏列的表为例。</span><span class="sxs-lookup"><span data-stu-id="f8391-240">Consider the example of a table that has 600 sparse columns of type bigint.</span></span> <span data-ttu-id="f8391-241">如果有 571 个非 Null 列，则磁盘上的总大小为 571 \* 12 = 6852 字节。</span><span class="sxs-lookup"><span data-stu-id="f8391-241">If there are 571 non-null columns, then the total size on disk is 571 \* 12 = 6852 bytes.</span></span> <span data-ttu-id="f8391-242">在包含额外行开销和稀疏列标题之后，这会导致增加大约 6895 个字节。</span><span class="sxs-lookup"><span data-stu-id="f8391-242">After including additional row overhead and the sparse column header, this increases to around 6895 bytes.</span></span> <span data-ttu-id="f8391-243">在磁盘上，该页仍有约 1124 字节可用。</span><span class="sxs-lookup"><span data-stu-id="f8391-243">The page still has around 1124 bytes available on disk.</span></span> <span data-ttu-id="f8391-244">这可以给出其他列可以成功更新的印象。</span><span class="sxs-lookup"><span data-stu-id="f8391-244">This can give the impression that additional columns can be updated successfully.</span></span> <span data-ttu-id="f8391-245">但是，在更新过程中，内存中有额外开销，此开销为 2\*(非 NULL 值的稀疏列数目)。</span><span class="sxs-lookup"><span data-stu-id="f8391-245">However, during the update, there is additional overhead in memory which is 2\*(number of non-null sparse columns).</span></span> <span data-ttu-id="f8391-246">在此示例中，包含额外开销 - 2 \* 571 = 1142 字节 - 将磁盘上的行大小增加到约 8037 个字节。</span><span class="sxs-lookup"><span data-stu-id="f8391-246">In this example, including the additional overhead - 2 \* 571 = 1142 bytes - increases the row size on disk to around 8037 bytes.</span></span> <span data-ttu-id="f8391-247">该大小超过最大允许的 8019 个字节。</span><span class="sxs-lookup"><span data-stu-id="f8391-247">This size exceeds the maximum allowed size of 8019 bytes.</span></span> <span data-ttu-id="f8391-248">由于所有列都是固定长度的数据类型，所以无法将其推送到行外。</span><span class="sxs-lookup"><span data-stu-id="f8391-248">Since all the columns are fixed-length data types, they cannot be pushed off the row.</span></span> <span data-ttu-id="f8391-249">因此，更新将会失败，错误为 576。</span><span class="sxs-lookup"><span data-stu-id="f8391-249">As a result, the update fails with the 576 error.</span></span>  
  
## <a name="restrictions-for-using-sparse-columns"></a><span data-ttu-id="f8391-250">使用稀疏列的限制</span><span class="sxs-lookup"><span data-stu-id="f8391-250">Restrictions for Using Sparse Columns</span></span>  
 <span data-ttu-id="f8391-251">稀疏列可以是任何 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型，其行为与任何其他列类似，但有以下限制：</span><span class="sxs-lookup"><span data-stu-id="f8391-251">Sparse columns can be of any [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type and behave like any other column with the following restrictions:</span></span>  
  
-   <span data-ttu-id="f8391-252">稀疏列必须可为 Null，并且不能有 ROWGUIDCOL 或 IDENTITY 属性。</span><span class="sxs-lookup"><span data-stu-id="f8391-252">A sparse column must be nullable and cannot have the ROWGUIDCOL or IDENTITY properties.</span></span> <span data-ttu-id="f8391-253">稀疏列不可以是以下数据类型：`text`、`ntext`、`image`、`timestamp`、用户定义的数据类型、`geometry` 或 `geography`；或者有 FILESTREAM 属性。</span><span class="sxs-lookup"><span data-stu-id="f8391-253">A sparse column cannot be of the following data types: `text`, `ntext`, `image`, `timestamp`, user-defined data type, `geometry`, or `geography`; or have the FILESTREAM attribute.</span></span>  
  
-   <span data-ttu-id="f8391-254">稀疏列不能有默认值。</span><span class="sxs-lookup"><span data-stu-id="f8391-254">A sparse column cannot have a default value.</span></span>  
  
-   <span data-ttu-id="f8391-255">稀疏列不能绑定到规则。</span><span class="sxs-lookup"><span data-stu-id="f8391-255">A sparse column cannot be bound to a rule.</span></span>  
  
-   <span data-ttu-id="f8391-256">虽然计算列可以包含稀疏列，但计算列不能标记为 SPARSE。</span><span class="sxs-lookup"><span data-stu-id="f8391-256">Although a computed column can contain a sparse column, a computed column cannot be marked as SPARSE.</span></span>  
  
-   <span data-ttu-id="f8391-257">稀疏列不能是聚集索引或唯一主键索引的一部分。</span><span class="sxs-lookup"><span data-stu-id="f8391-257">A sparse column cannot be part of a clustered index or a unique primary key index.</span></span> <span data-ttu-id="f8391-258">但是，在稀疏列上定义的持久化和非持久化计算列可以是聚集键的一部分。</span><span class="sxs-lookup"><span data-stu-id="f8391-258">However, both persisted and nonpersisted computed columns that are defined on sparse columns can be part of a clustered key.</span></span>  
  
-   <span data-ttu-id="f8391-259">稀疏列不能用作聚集索引或堆的分区键。</span><span class="sxs-lookup"><span data-stu-id="f8391-259">A sparse column cannot be used as a partition key of a clustered index or heap.</span></span> <span data-ttu-id="f8391-260">但是，稀疏列可以用作非聚集索引的分区键。</span><span class="sxs-lookup"><span data-stu-id="f8391-260">However, a sparse column can be used as the partition key of a nonclustered index.</span></span>  
  
-   <span data-ttu-id="f8391-261">稀疏列不能是用户定义的表类型的一部分，用户定义的表类型用在表变量和表值参数中。</span><span class="sxs-lookup"><span data-stu-id="f8391-261">A sparse column cannot be part of a user-defined table type, which are used in table variables and table-valued parameters.</span></span>  
  
-   <span data-ttu-id="f8391-262">稀疏列与数据压缩不兼容。</span><span class="sxs-lookup"><span data-stu-id="f8391-262">Sparse columns are incompatible with data compression.</span></span> <span data-ttu-id="f8391-263">因此稀疏列不能添加到压缩表，也不可以压缩包含稀疏列的任何表。</span><span class="sxs-lookup"><span data-stu-id="f8391-263">Therefore sparse columns cannot be added to compressed tables, nor can any tables containing sparse columns be compressed.</span></span>  
  
-   <span data-ttu-id="f8391-264">将稀疏列更改为非稀疏列或者将非稀疏列更改为稀疏列都需要更改该列的存储格式。</span><span class="sxs-lookup"><span data-stu-id="f8391-264">Changing a column from sparse to nonsparse or nonsparse to sparse requires changing the storage format of the column.</span></span> <span data-ttu-id="f8391-265">SQL Server 数据库引擎使用以下过程进行这种更改：</span><span class="sxs-lookup"><span data-stu-id="f8391-265">The SQL Server Database Engine uses the following procedure to accomplish this change:</span></span>  
  
    1.  <span data-ttu-id="f8391-266">以新的存储大小和格式向表中添加一个新列。</span><span class="sxs-lookup"><span data-stu-id="f8391-266">Adds a new column to the table in the new storage size and format.</span></span>  
  
    2.  <span data-ttu-id="f8391-267">对于表中的每一行，更新存储在旧列中的值并将值复制到新列中。</span><span class="sxs-lookup"><span data-stu-id="f8391-267">For each row in the table, updates and copies the value stored in the old column to the new column.</span></span>  
  
    3.  <span data-ttu-id="f8391-268">从表架构中删除旧列。</span><span class="sxs-lookup"><span data-stu-id="f8391-268">Removes the old column from the table schema.</span></span>  
  
    4.  <span data-ttu-id="f8391-269">重新生成表（如果没有聚集索引）或重新生成聚集索引以回收旧列所用的空间。</span><span class="sxs-lookup"><span data-stu-id="f8391-269">Rebuilds the table (if there is no clustered index) or rebuilds the clustered index to reclaim space used by the old column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f8391-270">当行中数据的大小超过允许的最大行大小时，步骤 2 将失败。</span><span class="sxs-lookup"><span data-stu-id="f8391-270">Step 2 can fail when the size of the data in the row exceeds the maximum allowable row size.</span></span> <span data-ttu-id="f8391-271">此大小包括存储在旧列中的数据和存储在新列中的已更新数据的大小。</span><span class="sxs-lookup"><span data-stu-id="f8391-271">This size includes the size of the data stored in the old column and the updated data stored in the new column.</span></span> <span data-ttu-id="f8391-272">对于不包含任何稀疏列的表，此限制为 8060 个字节；对于包含稀疏列的表为 8018 个字节。</span><span class="sxs-lookup"><span data-stu-id="f8391-272">This limit is 8060 bytes for tables that do not contain any sparse columns or 8018 bytes for tables that contain sparse columns.</span></span> <span data-ttu-id="f8391-273">即使已将所有合格列推送到行外，仍会出现此错误。</span><span class="sxs-lookup"><span data-stu-id="f8391-273">This error can occur even if all eligible columns have been pushed off-row.</span></span>  
  
-   <span data-ttu-id="f8391-274">将将非稀疏列改为稀疏列时，稀疏列将占用更多的空间来存储非 Null 值。</span><span class="sxs-lookup"><span data-stu-id="f8391-274">When you change a non-sparse column to a sparse column, the sparse column will consume more space for non-null values.</span></span> <span data-ttu-id="f8391-275">当行接近行大小的最大值限制时，操作将失败。</span><span class="sxs-lookup"><span data-stu-id="f8391-275">When a row is close to the maximum row size limit, the operation can fail.</span></span>  
  
## <a name="sql-server-technologies-that-support-sparse-columns"></a><span data-ttu-id="f8391-276">支持稀疏列的 SQL Server 技术</span><span class="sxs-lookup"><span data-stu-id="f8391-276">SQL Server Technologies That Support Sparse Columns</span></span>  
 <span data-ttu-id="f8391-277">本部分介绍下列 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技术如何支持稀疏列：</span><span class="sxs-lookup"><span data-stu-id="f8391-277">This section describes how sparse columns are supported in the following [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technologies:</span></span>  
  
-   <span data-ttu-id="f8391-278">事务复制</span><span class="sxs-lookup"><span data-stu-id="f8391-278">Transactional replication</span></span>  
  
     <span data-ttu-id="f8391-279">事务复制支持稀疏列，但它不支持可以与稀疏列一起使用的列集。</span><span class="sxs-lookup"><span data-stu-id="f8391-279">Transactional replication supports sparse columns, but it does not support column sets, which can be used with sparse columns.</span></span> <span data-ttu-id="f8391-280">有关列集的详细信息，请参阅 [使用列集](../tables/use-column-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="f8391-280">For more information about column sets, see [Use Column Sets](../tables/use-column-sets.md).</span></span>  
  
     <span data-ttu-id="f8391-281">SPARSE 属性的复制由架构选项来决定，架构选项是通过使用 [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) 或者使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的\*\*\*\*“项目属性”对话框来指定的。</span><span class="sxs-lookup"><span data-stu-id="f8391-281">The replication of the SPARSE attribute is determined by a schema option that is specified by using [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) or by using the **Article Properties** dialog box in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="f8391-282">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的早期版本不支持稀疏列。</span><span class="sxs-lookup"><span data-stu-id="f8391-282">Earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] do not support sparse columns.</span></span> <span data-ttu-id="f8391-283">如果必须将数据复制到早期版本，需指定不应复制 SPARSE 属性。</span><span class="sxs-lookup"><span data-stu-id="f8391-283">If you must replicate data to an earlier version, specify that the SPARSE attribute should not be replicated.</span></span>  
  
     <span data-ttu-id="f8391-284">对于发布的表，不能向表中添加任何新的稀疏列，也不能更改现有列的稀疏属性。</span><span class="sxs-lookup"><span data-stu-id="f8391-284">For tables that are published, you cannot add any new sparse columns to a table or change the sparse property of an existing column.</span></span> <span data-ttu-id="f8391-285">如果需要执行此类操作，则应删除然后再重新创建发布。</span><span class="sxs-lookup"><span data-stu-id="f8391-285">If such an operation is required, drop and re-create the publication.</span></span>  
  
-   <span data-ttu-id="f8391-286">合并复制</span><span class="sxs-lookup"><span data-stu-id="f8391-286">Merge replication</span></span>  
  
     <span data-ttu-id="f8391-287">合并复制不支持稀疏列或列集。</span><span class="sxs-lookup"><span data-stu-id="f8391-287">Merge replication does not support sparse columns or column sets.</span></span>  
  
-   <span data-ttu-id="f8391-288">Change tracking</span><span class="sxs-lookup"><span data-stu-id="f8391-288">Change tracking</span></span>  
  
     <span data-ttu-id="f8391-289">更改跟踪支持稀疏列和列集。</span><span class="sxs-lookup"><span data-stu-id="f8391-289">Change tracking supports sparse columns and column sets.</span></span> <span data-ttu-id="f8391-290">当在表中更新列集时，更改跟踪将此视为整个行的更新。</span><span class="sxs-lookup"><span data-stu-id="f8391-290">When a column set is updated in a table, change tracking treats this as an update to the whole row.</span></span> <span data-ttu-id="f8391-291">由于不提供详细的更改跟踪，因此不能获取通过列集更新操作更新的稀疏列的准确集合。</span><span class="sxs-lookup"><span data-stu-id="f8391-291">No detailed change tracking is provided to obtain the exact set of sparse columns that are updated through the column set update operation.</span></span> <span data-ttu-id="f8391-292">如果通过 DML 语句显式更新稀疏列，则这些稀疏列上的更改跟踪将像平常一样工作，并且可以准确地识别出已更改的列的集合。</span><span class="sxs-lookup"><span data-stu-id="f8391-292">If the sparse columns are updated explicitly through a DML statement, change tracking on them will work ordinarily and can identify the exact set of changed columns.</span></span>  
  
-   <span data-ttu-id="f8391-293">更改数据捕获</span><span class="sxs-lookup"><span data-stu-id="f8391-293">Change data capture</span></span>  
  
     <span data-ttu-id="f8391-294">变更数据捕获支持稀疏列，但不支持列集。</span><span class="sxs-lookup"><span data-stu-id="f8391-294">Change data capture supports sparse columns, but it does not support column sets.</span></span>  
  
-   <span data-ttu-id="f8391-295">复制表时，不保留列的稀疏属性。</span><span class="sxs-lookup"><span data-stu-id="f8391-295">The sparse property of a column is not preserved when the table is copied.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="f8391-296">示例</span><span class="sxs-lookup"><span data-stu-id="f8391-296">Examples</span></span>  
 <span data-ttu-id="f8391-297">在本示例中，文档表包含具有 `DocID` 和 `Title`列的公共集合。</span><span class="sxs-lookup"><span data-stu-id="f8391-297">In this example, a document table contains a common set that has the columns `DocID` and `Title`.</span></span> <span data-ttu-id="f8391-298">生产组希望所有生产文档都有一个 `ProductionSpecification` 列和一个 `ProductionLocation` 列。</span><span class="sxs-lookup"><span data-stu-id="f8391-298">The Production group wants a `ProductionSpecification` and `ProductionLocation` column for all production documents.</span></span> <span data-ttu-id="f8391-299">市场组希望所有市场文档都有一个 `MarketingSurveyGroup` 列。</span><span class="sxs-lookup"><span data-stu-id="f8391-299">The Marketing group wants a `MarketingSurveyGroup` column for marketing documents.</span></span> <span data-ttu-id="f8391-300">本示例中的代码创建一个使用稀疏列的表，向该表中插入两行，然后从该表中选择数据。</span><span class="sxs-lookup"><span data-stu-id="f8391-300">The code in this example creates a table that uses sparse columns, inserts two rows into the table, and then selects data from the table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f8391-301">该表只有五列，以便易于显示和读取。</span><span class="sxs-lookup"><span data-stu-id="f8391-301">This table has only five columns to make it easier to display and read.</span></span> <span data-ttu-id="f8391-302">如果设置了 ANSI_NULL_DFLT_ON 选项，则将稀疏列声明为可为 Null 是可选的。</span><span class="sxs-lookup"><span data-stu-id="f8391-302">Declaring the sparse columns to be nullable is optional if the ANSI_NULL_DFLT_ON option is set.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
  
CREATE TABLE DocumentStore  
    (DocID int PRIMARY KEY,  
     Title varchar(200) NOT NULL,  
     ProductionSpecification varchar(20) SPARSE NULL,  
     ProductionLocation smallint SPARSE NULL,  
     MarketingSurveyGroup varchar(20) SPARSE NULL ) ;  
GO  
  
INSERT DocumentStore(DocID, Title, ProductionSpecification, ProductionLocation)  
VALUES (1, 'Tire Spec 1', 'AXZZ217', 27);  
GO  
  
INSERT DocumentStore(DocID, Title, MarketingSurveyGroup)  
VALUES (2, 'Survey 2142', 'Men 25 - 35');  
GO  
```  
  
 <span data-ttu-id="f8391-303">从表中选择所有列会返回普通的结果集。</span><span class="sxs-lookup"><span data-stu-id="f8391-303">To select all the columns from the table returns an ordinary result set.</span></span>  
  
```  
SELECT * FROM DocumentStore ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `DocID  Title        ProductionSpecification  ProductionLocation  MarketingSurveyGroup`  
  
 `1      Tire Spec 1  AXZZ217                  27                  NULL`  
  
 `2      Survey 2142  NULL                     NULL                Men 25-35`  
  
 <span data-ttu-id="f8391-304">因为生产部门对市场数据不感兴趣，所以他们希望使用一个仅仅返回感兴趣的列的列列表，如下面的查询所示。</span><span class="sxs-lookup"><span data-stu-id="f8391-304">Because the Production department is not interested in the marketing data, they want to use a column list that returns only columns of interest, as shown in the following query.</span></span>  
  
```  
SELECT DocID, Title, ProductionSpecification, ProductionLocation   
FROM DocumentStore   
WHERE ProductionSpecification IS NOT NULL ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `DocID  Title        ProductionSpecification  ProductionLocation`  
  
 `1      Tire Spec 1  AXZZ217                  27`  
  
## <a name="see-also"></a><span data-ttu-id="f8391-305">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f8391-305">See Also</span></span>  
 <span data-ttu-id="f8391-306">[使用列集](../tables/use-column-sets.md) </span><span class="sxs-lookup"><span data-stu-id="f8391-306">[Use Column Sets](../tables/use-column-sets.md) </span></span>  
 <span data-ttu-id="f8391-307">[CREATE TABLE (Transact-SQL)](/sql/t-sql/statements/create-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f8391-307">[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) </span></span>  
 <span data-ttu-id="f8391-308">[ALTER TABLE (Transact-SQL)](/sql/t-sql/statements/alter-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f8391-308">[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span></span>  
 [<span data-ttu-id="f8391-309">sys.columns (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f8391-309">sys.columns &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-columns-transact-sql)  
  
  
