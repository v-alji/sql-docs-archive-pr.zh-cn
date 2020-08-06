---
title: 估计非聚集索引的大小 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- space allocation [SQL Server], index size
- size [SQL Server], tables
- predicting table size [SQL Server]
- table size [SQL Server]
- estimating table size
- clustered indexes, table size
- designing databases [SQL Server], estimating size
- calculating table size
ms.assetid: c183b0e4-ef4c-4bfc-8575-5ac219c25b0a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 097c0e5568ba17b12f83d09e347eb3bf8b0bd7da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691738"
---
# <a name="estimate-the-size-of-a-nonclustered-index"></a><span data-ttu-id="b7db4-102">估计非聚集索引的大小</span><span class="sxs-lookup"><span data-stu-id="b7db4-102">Estimate the Size of a Nonclustered Index</span></span>
  <span data-ttu-id="b7db4-103">按照下列步骤估计存储非聚集索引所需的空间大小：</span><span class="sxs-lookup"><span data-stu-id="b7db4-103">Follow these steps to estimate the amount of space that is required to store a nonclustered index:</span></span>  
  
1.  <span data-ttu-id="b7db4-104">计算步骤 2 和步骤 3 中所用变量的值。</span><span class="sxs-lookup"><span data-stu-id="b7db4-104">Calculate variables for use in steps 2 and 3.</span></span>  
  
2.  <span data-ttu-id="b7db4-105">计算用于存储非聚集索引的叶级中的索引信息的空间。</span><span class="sxs-lookup"><span data-stu-id="b7db4-105">Calculate the space used to store index information in the leaf level of the nonclustered index.</span></span>  
  
3.  <span data-ttu-id="b7db4-106">计算用于存储非聚集索引的非叶级中的索引信息的空间。</span><span class="sxs-lookup"><span data-stu-id="b7db4-106">Calculate the space used to store index information in the non-leaf levels of the nonclustered index.</span></span>  
  
4.  <span data-ttu-id="b7db4-107">对计算出的值求和。</span><span class="sxs-lookup"><span data-stu-id="b7db4-107">Total the calculated values.</span></span>  
  
## <a name="step-1-calculate-variables-for-use-in-steps-2-and-3"></a><span data-ttu-id="b7db4-108">步骤 1。</span><span class="sxs-lookup"><span data-stu-id="b7db4-108">Step 1.</span></span> <span data-ttu-id="b7db4-109">计算步骤 2 和步骤 3 中所用变量的值</span><span class="sxs-lookup"><span data-stu-id="b7db4-109">Calculate Variables for Use in Steps 2 and 3</span></span>  
 <span data-ttu-id="b7db4-110">可使用下列步骤计算所用变量的值以估计存储索引的较高级别所需的空间大小。</span><span class="sxs-lookup"><span data-stu-id="b7db4-110">You can use the following steps to calculate variables that are used to estimate the amount of space that is required to store the upper levels of the index.</span></span>  
  
1.  <span data-ttu-id="b7db4-111">指定表中显示的行数：</span><span class="sxs-lookup"><span data-stu-id="b7db4-111">Specify the number of rows that will be present in the table:</span></span>  
  
     <span data-ttu-id="b7db4-112">***Num_Rows***  = 表中的行数</span><span class="sxs-lookup"><span data-stu-id="b7db4-112">***Num_Rows***  = number of rows in the table</span></span>  
  
2.  <span data-ttu-id="b7db4-113">指定索引键中固定长度和可变长度列的数量，并计算存储所需的空间：</span><span class="sxs-lookup"><span data-stu-id="b7db4-113">Specify the number of fixed-length and variable-length columns in the index key and calculate the space that is required for their storage:</span></span>  
  
     <span data-ttu-id="b7db4-114">索引键列可以包括固定长度和可变长度列。</span><span class="sxs-lookup"><span data-stu-id="b7db4-114">The key columns of an index can include fixed-length and variable-length columns.</span></span> <span data-ttu-id="b7db4-115">若要估计内部级别索引行的大小，请计算每组列在索引行中所占据的空间。</span><span class="sxs-lookup"><span data-stu-id="b7db4-115">To estimate the interior level index row size, calculate the space that each of these groups of columns occupies within the index row.</span></span> <span data-ttu-id="b7db4-116">列的大小取决于数据类型和长度规定。</span><span class="sxs-lookup"><span data-stu-id="b7db4-116">The size of a column depends on the data type and length specification.</span></span>  
  
     <span data-ttu-id="b7db4-117">***Num_Key_Cols***  = 总键列数（固定长度和可变长度）</span><span class="sxs-lookup"><span data-stu-id="b7db4-117">***Num_Key_Cols***  = total number of key columns (fixed-length and variable-length)</span></span>  
  
     <span data-ttu-id="b7db4-118">***Fixed_Key_Size***  = 所有固定长度键列的总字节大小</span><span class="sxs-lookup"><span data-stu-id="b7db4-118">***Fixed_Key_Size***  = total byte size of all fixed-length key columns</span></span>  
  
     <span data-ttu-id="b7db4-119">***Num_Variable_Key_Cols***  = 可变长度键列数</span><span class="sxs-lookup"><span data-stu-id="b7db4-119">***Num_Variable_Key_Cols***  = number of variable-length key columns</span></span>  
  
     <span data-ttu-id="b7db4-120">***Max_Var_Key_Size***  = 所有可变长度键列的最大字节大小</span><span class="sxs-lookup"><span data-stu-id="b7db4-120">***Max_Var_Key_Size***  = maximum byte size of all variable-length key columns</span></span>  
  
3.  <span data-ttu-id="b7db4-121">如果索引不是唯一的，对所需的数据行定位符说明如下：</span><span class="sxs-lookup"><span data-stu-id="b7db4-121">Account for the data row locator that is required if the index is nonunique:</span></span>  
  
     <span data-ttu-id="b7db4-122">如果非聚集索引不是唯一的，数据行定位符将与非聚集索引键组合使用，以便为每一行生成唯一的键值。</span><span class="sxs-lookup"><span data-stu-id="b7db4-122">If the nonclustered index is nonunique, the data row locator is combined with the nonclustered index key to produce a unique key value for every row.</span></span>  
  
     <span data-ttu-id="b7db4-123">如果非聚集索引在堆上，则数据行定位符是堆 RID。</span><span class="sxs-lookup"><span data-stu-id="b7db4-123">If the nonclustered index is over a heap, the data row locator is the heap RID.</span></span> <span data-ttu-id="b7db4-124">其大小是 8 个字节。</span><span class="sxs-lookup"><span data-stu-id="b7db4-124">This is a size of 8 bytes.</span></span>  
  
     <span data-ttu-id="b7db4-125">***Num_Key_Cols***  = ***Num_Key_Cols*** + 1</span><span class="sxs-lookup"><span data-stu-id="b7db4-125">***Num_Key_Cols***  = ***Num_Key_Cols*** + 1</span></span>  
  
     <span data-ttu-id="b7db4-126">***Num_Variable_Key_Cols***  = ***Num_Variable_Key_Cols*** + 1</span><span class="sxs-lookup"><span data-stu-id="b7db4-126">***Num_Variable_Key_Cols***  = ***Num_Variable_Key_Cols*** + 1</span></span>  
  
     <span data-ttu-id="b7db4-127">***Max_Var_Key_Size***  = ***Max_Var_Key_Size*** + 8</span><span class="sxs-lookup"><span data-stu-id="b7db4-127">***Max_Var_Key_Size***  = ***Max_Var_Key_Size*** + 8</span></span>  
  
     <span data-ttu-id="b7db4-128">如果非聚集索引在聚集索引之上，则数据行定位符是聚集键。</span><span class="sxs-lookup"><span data-stu-id="b7db4-128">If the nonclustered index is over a clustered index, the data row locator is the clustering key.</span></span> <span data-ttu-id="b7db4-129">必须与非聚集索引键结合使用的列是聚集键中的以下列：不在非聚集索引键列集中的列。</span><span class="sxs-lookup"><span data-stu-id="b7db4-129">The columns that must be combined with the nonclustered index key are those columns in the clustering key that are not already present in the set of nonclustered index key columns.</span></span>  
  
     <span data-ttu-id="b7db4-130">***Num_Key_Cols***  = ***Num_Key_Cols*** + 不在非群集索引键列集中的群集键列数（如果群集索引不唯一，则 + 1）</span><span class="sxs-lookup"><span data-stu-id="b7db4-130">***Num_Key_Cols***  = ***Num_Key_Cols*** + number of clustering key columns not in the set of nonclustered index key columns (+ 1 if the clustered index is nonunique)</span></span>  
  
     <span data-ttu-id="b7db4-131">***Fixed_Key_Size***  = ***Fixed_Key_Size*** + 不在非群集索引键列集中的固定长度群集键列的总字节大小</span><span class="sxs-lookup"><span data-stu-id="b7db4-131">***Fixed_Key_Size***  = ***Fixed_Key_Size*** + total byte size of fixed-length clustering key columns not in the set of nonclustered index key columns</span></span>  
  
     <span data-ttu-id="b7db4-132">***Num_Variable_Key_Cols***  = ***Num_Variable_Key_Cols*** + 不在非群集索引键列集中的可变长度群集键列数（如果群集索引不唯一，则 + 1）</span><span class="sxs-lookup"><span data-stu-id="b7db4-132">***Num_Variable_Key_Cols***  = ***Num_Variable_Key_Cols*** + number of variable-length clustering key columns not in the set of nonclustered index key columns (+ 1 if the clustered index is nonunique)</span></span>  
  
     <span data-ttu-id="b7db4-133">***Max_Var_Key_Size***  = ***Max_Var_Key_Size*** + 不在非群集索引键列集中的可变长度群集键列的最大字节大小（如果群集索引不唯一，则 + 4）</span><span class="sxs-lookup"><span data-stu-id="b7db4-133">***Max_Var_Key_Size***  = ***Max_Var_Key_Size*** + maximum byte size of variable-length clustering key columns not in the set of nonclustered index key columns (+ 4 if the clustered index is nonunique)</span></span>  
  
4.  <span data-ttu-id="b7db4-134">可以保留行的一部分（称为“空位图”），以管理列的为空性。</span><span class="sxs-lookup"><span data-stu-id="b7db4-134">Part of the row, known as the null bitmap, may be reserved to manage column nullability.</span></span> <span data-ttu-id="b7db4-135">计算其大小：</span><span class="sxs-lookup"><span data-stu-id="b7db4-135">Calculate its size:</span></span>  
  
     <span data-ttu-id="b7db4-136">如果索引键中有可为 Null 的列（包括步骤 1.3 中所述的所有必要的聚集键列），则保留索引行的一部分，以用于 Null 位图。</span><span class="sxs-lookup"><span data-stu-id="b7db4-136">If there are nullable columns in the index key, including any necessary clustering key columns as described in Step 1.3, part of the index row is reserved for the null bitmap.</span></span>  
  
     <span data-ttu-id="b7db4-137">***Index_Null_Bitmap***  = 2 + ((索引行中的列数 + 7) / 8)</span><span class="sxs-lookup"><span data-stu-id="b7db4-137">***Index_Null_Bitmap***  = 2 + ((number of columns in the index row + 7) / 8)</span></span>  
  
     <span data-ttu-id="b7db4-138">仅应使用上述表达式中的整数部分，</span><span class="sxs-lookup"><span data-stu-id="b7db4-138">Only the integer part of the previous expression should be used.</span></span> <span data-ttu-id="b7db4-139">而放弃所有余数。</span><span class="sxs-lookup"><span data-stu-id="b7db4-139">Discard any remainder.</span></span>  
  
     <span data-ttu-id="b7db4-140">如果没有可为 Null 的键列，请将 ***Index_Null_Bitmap*** 设置为 0。</span><span class="sxs-lookup"><span data-stu-id="b7db4-140">If there are no nullable key columns, set ***Index_Null_Bitmap*** to 0.</span></span>  
  
5.  <span data-ttu-id="b7db4-141">计算可变长度数据大小：</span><span class="sxs-lookup"><span data-stu-id="b7db4-141">Calculate the variable length data size:</span></span>  
  
     <span data-ttu-id="b7db4-142">如果索引键中有可变长度的列（包括所有必要的聚集索引键列），请确定存储索引行中的这些列需使用的空间：</span><span class="sxs-lookup"><span data-stu-id="b7db4-142">If there are variable-length columns in the index key, including any necessary clustered index key columns, determine how much space is used to store the columns within the index row:</span></span>  
  
     <span data-ttu-id="b7db4-143">***Variable_Key_Size***  = 2 + (***Num_Variable_Key_Cols*** x 2) + ***Max_Var_Key_Size***</span><span class="sxs-lookup"><span data-stu-id="b7db4-143">***Variable_Key_Size***  = 2 + (***Num_Variable_Key_Cols*** x 2) + ***Max_Var_Key_Size***</span></span>  
  
     <span data-ttu-id="b7db4-144">添加到 ***Max_Var_Key_Size*** 中的字节可用于跟踪每个可变列。此公式假定所有可变长度列均百分之百充满。</span><span class="sxs-lookup"><span data-stu-id="b7db4-144">The bytes added to ***Max_Var_Key_Size*** are for tracking each variable column.This formula assumes that all variable-length columns are 100 percent full.</span></span> <span data-ttu-id="b7db4-145">如果预计可变长度列占用的存储空间比例较低，则可以按照该比例调整 ***Max_Var_Key_Size*** 值，从而对整个表大小得出一个更准确的估计。</span><span class="sxs-lookup"><span data-stu-id="b7db4-145">If you anticipate that a smaller percentage of the variable-length column storage space will be used, you can adjust the ***Max_Var_Key_Size*** value by that percentage to yield a more accurate estimate of the overall table size.</span></span>  
  
     <span data-ttu-id="b7db4-146">如果没有可变长度列，请将 ***Variable_Key_Size*** 设置为 0。</span><span class="sxs-lookup"><span data-stu-id="b7db4-146">If there are no variable-length columns, set ***Variable_Key_Size*** to 0.</span></span>  
  
6.  <span data-ttu-id="b7db4-147">计算索引行大小：</span><span class="sxs-lookup"><span data-stu-id="b7db4-147">Calculate the index row size:</span></span>  
  
     <span data-ttu-id="b7db4-148">***Index_Row_Size***  = ***Fixed_Key_Size*** + ***Variable_Key_Size*** + ***Index_Null_Bitmap*** + 1（对应于索引行的行标题开销）+ 6（对应于子页 ID 指针）</span><span class="sxs-lookup"><span data-stu-id="b7db4-148">***Index_Row_Size***  = ***Fixed_Key_Size*** + ***Variable_Key_Size*** + ***Index_Null_Bitmap*** + 1 (for row header overhead of an index row) + 6 (for the child page ID pointer)</span></span>  
  
7.  <span data-ttu-id="b7db4-149">下一步，计算每页的索引行数（每页有 8096 个可用字节）：</span><span class="sxs-lookup"><span data-stu-id="b7db4-149">Calculate the number of index rows per page (8096 free bytes per page):</span></span>  
  
     <span data-ttu-id="b7db4-150">***Index_Rows_Per_Page***  = 8096 / (***Index_Row_Size*** + 2)</span><span class="sxs-lookup"><span data-stu-id="b7db4-150">***Index_Rows_Per_Page***  = 8096 / (***Index_Row_Size*** + 2)</span></span>  
  
     <span data-ttu-id="b7db4-151">因为索引行不能跨页，所以每页的索引行数应向下舍入到最接近的整数。</span><span class="sxs-lookup"><span data-stu-id="b7db4-151">Because index rows do not span pages, the number of index rows per page should be rounded down to the nearest whole row.</span></span> <span data-ttu-id="b7db4-152">公式中的 2 是计算行数时引入的行大小余量。</span><span class="sxs-lookup"><span data-stu-id="b7db4-152">The 2 in the formula is for the row's entry in the page's slot array.</span></span>  
  
## <a name="step-2-calculate-the-space-used-to-store-index-information-in-the-leaf-level"></a><span data-ttu-id="b7db4-153">步骤 2.</span><span class="sxs-lookup"><span data-stu-id="b7db4-153">Step 2.</span></span> <span data-ttu-id="b7db4-154">计算用于存储叶级中的索引信息的空间</span><span class="sxs-lookup"><span data-stu-id="b7db4-154">Calculate the Space Used to Store Index Information in the Leaf Level</span></span>  
 <span data-ttu-id="b7db4-155">可使用下列步骤估计存储叶级索引所需的空间大小。</span><span class="sxs-lookup"><span data-stu-id="b7db4-155">You can use the following steps to estimate the amount of space that is required to store the leaf level of the index.</span></span> <span data-ttu-id="b7db4-156">需要使用从步骤 1 中保留的值来完成此步骤。</span><span class="sxs-lookup"><span data-stu-id="b7db4-156">You will need the values preserved from Step 1 to complete this step.</span></span>  
  
1.  <span data-ttu-id="b7db4-157">指定叶级的固定长度列和可变长度列的数量，并计算存储这些列所需的空间：</span><span class="sxs-lookup"><span data-stu-id="b7db4-157">Specify the number of fixed-length and variable-length columns at the leaf level and calculate the space that is required for their storage:</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b7db4-158">您可以通过包含索引键列和非键列扩展非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="b7db4-158">You can extend a nonclustered index by including nonkey columns in addition to the index key columns.</span></span> <span data-ttu-id="b7db4-159">这些额外的列只存储在叶级非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="b7db4-159">These additional columns are only stored at the leaf level of the nonclustered index.</span></span> <span data-ttu-id="b7db4-160">有关详细信息，请参阅 [Create Indexes with Included Columns](../indexes/create-indexes-with-included-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="b7db4-160">For more information, see [Create Indexes with Included Columns](../indexes/create-indexes-with-included-columns.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b7db4-161">您可以组合 `varchar`、`nvarchar`、`varbinary` 或 `sql_variant` 列，使得定义的表的总宽度超过 8,060 字节。</span><span class="sxs-lookup"><span data-stu-id="b7db4-161">You can combine `varchar`, `nvarchar`, `varbinary`, or `sql_variant` columns that cause the total defined table width to exceed 8,060 bytes.</span></span> <span data-ttu-id="b7db4-162">对于 `varchar`、`varbinary` 或 `sql_variant` 中的每一列，其长度不能超过 8,000 字节，对于 `nvarchar` 列，不能超过 4,000 字节。</span><span class="sxs-lookup"><span data-stu-id="b7db4-162">The length of each one of these columns must still fall within the limit of 8,000 bytes for a `varchar`, `varbinary`, or `sql_variant` column, and 4,000 bytes for `nvarchar` columns.</span></span> <span data-ttu-id="b7db4-163">但是，表中这些列的组合宽度可超过 8,060 字节的限制。</span><span class="sxs-lookup"><span data-stu-id="b7db4-163">However, their combined widths may exceed the 8,060 byte limit in a table.</span></span> <span data-ttu-id="b7db4-164">这也适用于具有包含列的非聚集索引叶行。</span><span class="sxs-lookup"><span data-stu-id="b7db4-164">This also applies to nonclustered index leaf rows that have included columns.</span></span>  
  
     <span data-ttu-id="b7db4-165">如果非聚集索引没有任何包含列，则使用步骤 1 中的值（包括在步骤 1.3 中进行的任何修改）：</span><span class="sxs-lookup"><span data-stu-id="b7db4-165">If the nonclustered index does not have any included columns, use the values from Step 1, including any modifications determined in Step 1.3:</span></span>  
  
     <span data-ttu-id="b7db4-166">***Num_Leaf_Cols***  = ***Num_Key_Cols***</span><span class="sxs-lookup"><span data-stu-id="b7db4-166">***Num_Leaf_Cols***  = ***Num_Key_Cols***</span></span>  
  
     <span data-ttu-id="b7db4-167">***Fixed_Leaf_Size***  = ***Fixed_Key_Size***</span><span class="sxs-lookup"><span data-stu-id="b7db4-167">***Fixed_Leaf_Size***  = ***Fixed_Key_Size***</span></span>  
  
     <span data-ttu-id="b7db4-168">***Num_Variable_Leaf_Cols***  = ***Num_Variable_Key_Cols***</span><span class="sxs-lookup"><span data-stu-id="b7db4-168">***Num_Variable_Leaf_Cols***  = ***Num_Variable_Key_Cols***</span></span>  
  
     <span data-ttu-id="b7db4-169">***Max_Var_Leaf_Size***  = ***Max_Var_Key_Size***</span><span class="sxs-lookup"><span data-stu-id="b7db4-169">***Max_Var_Leaf_Size***  = ***Max_Var_Key_Size***</span></span>  
  
     <span data-ttu-id="b7db4-170">如果非聚集索引确实具有包含列，则对步骤 1 中的值加上适当的值（包括在步骤 1.3 中进行的任何修改）。</span><span class="sxs-lookup"><span data-stu-id="b7db4-170">If the nonclustered index does have included columns, add the appropriate values to the values from Step 1, including any modifications in Step 1.3.</span></span> <span data-ttu-id="b7db4-171">列的大小取决于数据类型和长度规定。</span><span class="sxs-lookup"><span data-stu-id="b7db4-171">The size of a column depends on the data type and length specification.</span></span> <span data-ttu-id="b7db4-172">有关详细信息，请参阅[数据类型 (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b7db4-172">For more information, see [Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).</span></span>  
  
     <span data-ttu-id="b7db4-173">***Num_Leaf_Cols***  = ***Num_Key_Cols*** + 包含列数</span><span class="sxs-lookup"><span data-stu-id="b7db4-173">***Num_Leaf_Cols***  = ***Num_Key_Cols*** + number of included columns</span></span>  
  
     <span data-ttu-id="b7db4-174">***Fixed_Leaf_Size***  = ***Fixed_Key_Size*** + 固定长度包含列的总字节大小</span><span class="sxs-lookup"><span data-stu-id="b7db4-174">***Fixed_Leaf_Size***  = ***Fixed_Key_Size*** + total byte size of fixed-length included columns</span></span>  
  
     <span data-ttu-id="b7db4-175">***Num_Variable_Leaf_Cols***  = ***Num_Variable_Key_Cols*** + 可变长度包含列数</span><span class="sxs-lookup"><span data-stu-id="b7db4-175">***Num_Variable_Leaf_Cols***  = ***Num_Variable_Key_Cols*** + number of variable-length included columns</span></span>  
  
     <span data-ttu-id="b7db4-176">***Max_Var_Leaf_Size***  = ***Max_Var_Key_Size*** + 可变长度包含列的最大字节大小</span><span class="sxs-lookup"><span data-stu-id="b7db4-176">***Max_Var_Leaf_Size***  = ***Max_Var_Key_Size*** + maximum byte size of variable-length included columns</span></span>  
  
2.  <span data-ttu-id="b7db4-177">数据行定位符说明：</span><span class="sxs-lookup"><span data-stu-id="b7db4-177">Account for the data row locator:</span></span>  
  
     <span data-ttu-id="b7db4-178">如果非聚集索引不是唯一的，则已在步骤 1.3 中考虑了数据行定位符的开销且不需要进行其他的修改。</span><span class="sxs-lookup"><span data-stu-id="b7db4-178">If the nonclustered index is nonunique, the overhead for the data row locator has already been considered in Step 1.3 and no additional modifications are required.</span></span> <span data-ttu-id="b7db4-179">转到下一步。</span><span class="sxs-lookup"><span data-stu-id="b7db4-179">Go to the next step.</span></span>  
  
     <span data-ttu-id="b7db4-180">如果非聚集索引是唯一的，则必须在叶级的所有行中说明数据行定位符。</span><span class="sxs-lookup"><span data-stu-id="b7db4-180">If the nonclustered index is unique, the data row locator must be accounted for in all rows at the leaf level.</span></span>  
  
     <span data-ttu-id="b7db4-181">如果非聚集索引在堆上，则数据行定位符是堆 RID（大小为 8 字节）。</span><span class="sxs-lookup"><span data-stu-id="b7db4-181">If the nonclustered index is over a heap, the data row locator is the heap RID (size 8 bytes).</span></span>  
  
     <span data-ttu-id="b7db4-182">***Num_Leaf_Cols***  = ***Num_Leaf_Cols*** + 1</span><span class="sxs-lookup"><span data-stu-id="b7db4-182">***Num_Leaf_Cols***  = ***Num_Leaf_Cols*** + 1</span></span>  
  
     <span data-ttu-id="b7db4-183">***Num_Variable_Leaf_Cols***  = ***Num_Variable_Leaf_Cols*** + 1</span><span class="sxs-lookup"><span data-stu-id="b7db4-183">***Num_Variable_Leaf_Cols***  = ***Num_Variable_Leaf_Cols*** + 1</span></span>  
  
     <span data-ttu-id="b7db4-184">***Max_Var_Leaf_Size***  = ***Max_Var_Leaf_Size*** + 8</span><span class="sxs-lookup"><span data-stu-id="b7db4-184">***Max_Var_Leaf_Size***  = ***Max_Var_Leaf_Size*** + 8</span></span>  
  
     <span data-ttu-id="b7db4-185">如果非聚集索引在聚集索引之上，则数据行定位符是聚集键。</span><span class="sxs-lookup"><span data-stu-id="b7db4-185">If the nonclustered index is over a clustered index, the data row locator is the clustering key.</span></span> <span data-ttu-id="b7db4-186">必须与非聚集索引键结合使用的列是聚集键中的以下列：不在非聚集索引键列集中的列。</span><span class="sxs-lookup"><span data-stu-id="b7db4-186">The columns that must be combined with the nonclustered index key are those columns in the clustering key that are not already present in the set of nonclustered index key columns.</span></span>  
  
     <span data-ttu-id="b7db4-187">***Num_Leaf_Cols***  = ***Num_Leaf_Cols*** + 不在非群集索引键列集中的群集键列数（如果群集索引不唯一，则 + 1）</span><span class="sxs-lookup"><span data-stu-id="b7db4-187">***Num_Leaf_Cols***  = ***Num_Leaf_Cols*** + number of clustering key columns not in the set of nonclustered index key columns (+ 1 if the clustered index is nonunique)</span></span>  
  
     <span data-ttu-id="b7db4-188">***Fixed_Leaf_Size***  = ***Fixed_Leaf_Size*** + 不在非群集索引键列集中的固定长度群集键列数</span><span class="sxs-lookup"><span data-stu-id="b7db4-188">***Fixed_Leaf_Size***  = ***Fixed_Leaf_Size*** + number of fixed-length clustering key columns not in the set of nonclustered index key columns</span></span>  
  
     <span data-ttu-id="b7db4-189">***Num_Variable_Leaf_Cols***  = ***Num_Variable_Leaf_Cols*** + 不在非群集索引键列集中的可变长度群集键列数（如果群集索引不唯一，则 + 1）</span><span class="sxs-lookup"><span data-stu-id="b7db4-189">***Num_Variable_Leaf_Cols***  = ***Num_Variable_Leaf_Cols*** + number of variable-length clustering key columns not in the set of nonclustered index key columns (+ 1 if the clustered index is nonunique)</span></span>  
  
     <span data-ttu-id="b7db4-190">***Max_Var_Leaf_Size***  = ***Max_Var_Leaf_Size*** + 不在非群集索引键列集中的可变长度群集键列的字节大小（如果群集索引不唯一，则 + 4）</span><span class="sxs-lookup"><span data-stu-id="b7db4-190">***Max_Var_Leaf_Size***  = ***Max_Var_Leaf_Size*** + size in bytes of the variable-length clustering key columns not in the set of nonclustered index key columns (+ 4 if the clustered index is nonunique)</span></span>  
  
3.  <span data-ttu-id="b7db4-191">计算 Null 位图大小：</span><span class="sxs-lookup"><span data-stu-id="b7db4-191">Calculate the null bitmap size:</span></span>  
  
     <span data-ttu-id="b7db4-192">***Leaf_Null_Bitmap***  = 2 + ((***Num_Leaf_Cols*** + 7) / 8)</span><span class="sxs-lookup"><span data-stu-id="b7db4-192">***Leaf_Null_Bitmap***  = 2 + ((***Num_Leaf_Cols*** + 7) / 8)</span></span>  
  
     <span data-ttu-id="b7db4-193">仅应使用上述表达式中的整数部分，</span><span class="sxs-lookup"><span data-stu-id="b7db4-193">Only the integer part of the previous expression should be used.</span></span> <span data-ttu-id="b7db4-194">而放弃所有余数。</span><span class="sxs-lookup"><span data-stu-id="b7db4-194">Discard any remainder.</span></span>  
  
4.  <span data-ttu-id="b7db4-195">计算可变长度数据大小：</span><span class="sxs-lookup"><span data-stu-id="b7db4-195">Calculate the variable length data size:</span></span>  
  
     <span data-ttu-id="b7db4-196">如果索引键中有可变长度的列（包括在以前的步骤 2.2 中所述的所有必要的聚集索引键列），请确定存储索引行中的这些列需使用的空间：</span><span class="sxs-lookup"><span data-stu-id="b7db4-196">If there are variable-length columns in the index key, including any necessary clustering key columns as described previously in Step 2.2, determine how much space is used to store the columns within the index row:</span></span>  
  
     <span data-ttu-id="b7db4-197">***Variable_Leaf_Size***  = 2 + (***Num_Variable_Leaf_Cols*** x 2) + ***Max_Var_Leaf_Size***</span><span class="sxs-lookup"><span data-stu-id="b7db4-197">***Variable_Leaf_Size***  = 2 + (***Num_Variable_Leaf_Cols*** x 2) + ***Max_Var_Leaf_Size***</span></span>  
  
     <span data-ttu-id="b7db4-198">添加到 ***Max_Var_Key_Size*** 中的字节可用于跟踪每个可变列。此公式假定所有可变长度列均百分之百充满。</span><span class="sxs-lookup"><span data-stu-id="b7db4-198">The bytes added to ***Max_Var_Key_Size*** are for tracking each variable column.This formula assumes that all variable-length columns are 100 percent full.</span></span> <span data-ttu-id="b7db4-199">如果预计可变长度列占用的存储空间比例较低，则可以按照该比例调整 ***Max_Var_Leaf_Size*** 值，从而对整个表大小得出一个更准确的估计。</span><span class="sxs-lookup"><span data-stu-id="b7db4-199">If you anticipate that a smaller percentage of the variable-length column storage space will be used, you can adjust the ***Max_Var_Leaf_Size*** value by that percentage to yield a more accurate estimate of the overall table size.</span></span>  
  
     <span data-ttu-id="b7db4-200">如果没有可变长度的列，则将 ***Variable_Leaf_Size*** 设置为 0。</span><span class="sxs-lookup"><span data-stu-id="b7db4-200">If there are no variable-length columns, set ***Variable_Leaf_Size*** to 0.</span></span>  
  
5.  <span data-ttu-id="b7db4-201">计算索引行大小：</span><span class="sxs-lookup"><span data-stu-id="b7db4-201">Calculate the index row size:</span></span>  
  
     <span data-ttu-id="b7db4-202">***Leaf_Row_Size***   = ***Fixed_Leaf_Size***  + ***Variable_Leaf_Size***  + ***Leaf_Null_Bitmap*** + 1 (对于子页面 ID 指针) + 6 (索引行的行标题开销) </span><span class="sxs-lookup"><span data-stu-id="b7db4-202">***Leaf_Row_Size***  = ***Fixed_Leaf_Size*** + ***Variable_Leaf_Size*** + ***Leaf_Null_Bitmap*** + 1 (for row header overhead of an index row) + 6 (for the child page ID pointer)</span></span>  
  
6.  <span data-ttu-id="b7db4-203">下一步，计算每页的索引行数（每页有 8096 个可用字节）：</span><span class="sxs-lookup"><span data-stu-id="b7db4-203">Calculate the number of index rows per page (8096 free bytes per page):</span></span>  
  
     <span data-ttu-id="b7db4-204">***Leaf_Rows_Per_Page***  = 8096 / (***Leaf_Row_Size*** + 2)</span><span class="sxs-lookup"><span data-stu-id="b7db4-204">***Leaf_Rows_Per_Page***  = 8096 / (***Leaf_Row_Size*** + 2)</span></span>  
  
     <span data-ttu-id="b7db4-205">因为索引行不能跨页，所以每页的索引行数应向下舍入到最接近的整数。</span><span class="sxs-lookup"><span data-stu-id="b7db4-205">Because index rows do not span pages, the number of index rows per page should be rounded down to the nearest whole row.</span></span> <span data-ttu-id="b7db4-206">公式中的 2 是计算行数时引入的行大小余量。</span><span class="sxs-lookup"><span data-stu-id="b7db4-206">The 2 in the formula is for the row's entry in the page's slot array.</span></span>  
  
7.  <span data-ttu-id="b7db4-207">根据指定的 [填充因子](../indexes/specify-fill-factor-for-an-index.md) 计算每页保留的空行数：</span><span class="sxs-lookup"><span data-stu-id="b7db4-207">Calculate the number of reserved free rows per page, based on the [fill factor](../indexes/specify-fill-factor-for-an-index.md) specified:</span></span>  
  
     <span data-ttu-id="b7db4-208">***Free_Rows_Per_Page***  = 8096 x ((100 - ***Fill_Factor***) / 100) / (***Leaf_Row_Size*** + 2)</span><span class="sxs-lookup"><span data-stu-id="b7db4-208">***Free_Rows_Per_Page***  = 8096 x ((100 - ***Fill_Factor***) / 100) / (***Leaf_Row_Size*** + 2)</span></span>  
  
     <span data-ttu-id="b7db4-209">计算中使用的填充因子为整数值，而不是百分比。</span><span class="sxs-lookup"><span data-stu-id="b7db4-209">The fill factor used in the calculation is an integer value instead of a percentage.</span></span> <span data-ttu-id="b7db4-210">因为行不跨页，所以每页的行数应向下舍入到最接近的整数。</span><span class="sxs-lookup"><span data-stu-id="b7db4-210">Because rows do not span pages, the number of rows per page should be rounded down to the nearest whole row.</span></span> <span data-ttu-id="b7db4-211">填充因子增大时，每页将存储更多的数据，因此页数将减少。</span><span class="sxs-lookup"><span data-stu-id="b7db4-211">As the fill factor grows, more data will be stored on each page and there will be fewer pages.</span></span> <span data-ttu-id="b7db4-212">公式中的 2 是计算行数时引入的行大小余量。</span><span class="sxs-lookup"><span data-stu-id="b7db4-212">The 2 in the formula is for the row's entry in the page's slot array.</span></span>  
  
8.  <span data-ttu-id="b7db4-213">计算存储所有行所需的页数：</span><span class="sxs-lookup"><span data-stu-id="b7db4-213">Calculate the number of pages required to store all the rows:</span></span>  
  
     <span data-ttu-id="b7db4-214">***Num_Leaf_Pages***  = ***Num_Rows*** / (***Leaf_Rows_Per_Page*** - ***Free_Rows_Per_Page***)</span><span class="sxs-lookup"><span data-stu-id="b7db4-214">***Num_Leaf_Pages***  = ***Num_Rows*** / (***Leaf_Rows_Per_Page*** - ***Free_Rows_Per_Page***)</span></span>  
  
     <span data-ttu-id="b7db4-215">估计的页数应向上舍入到最接近的整数。</span><span class="sxs-lookup"><span data-stu-id="b7db4-215">The number of pages estimated should be rounded up to the nearest whole page.</span></span>  
  
9. <span data-ttu-id="b7db4-216">计算索引的大小（每页总共有 8192 个字节）：</span><span class="sxs-lookup"><span data-stu-id="b7db4-216">Calculate the size of the index (8192 total bytes per page):</span></span>  
  
     <span data-ttu-id="b7db4-217">***Leaf_Space_Used***  = 8192 x ***Num_Leaf_Pages***</span><span class="sxs-lookup"><span data-stu-id="b7db4-217">***Leaf_Space_Used***  = 8192 x ***Num_Leaf_Pages***</span></span>  
  
## <a name="step-3-calculate-the-space-used-to-store-index-information-in-the-non-leaf-levels"></a><span data-ttu-id="b7db4-218">步骤 3.</span><span class="sxs-lookup"><span data-stu-id="b7db4-218">Step 3.</span></span> <span data-ttu-id="b7db4-219">计算用于存储非叶级中的索引信息的空间</span><span class="sxs-lookup"><span data-stu-id="b7db4-219">Calculate the Space Used to Store Index Information in the Non-leaf Levels</span></span>  
 <span data-ttu-id="b7db4-220">按照下列步骤估计存储索引的中间级和根级所需的空间大小。</span><span class="sxs-lookup"><span data-stu-id="b7db4-220">Follow these steps to estimate the amount of space that is required to store the intermediate and root levels of the index.</span></span> <span data-ttu-id="b7db4-221">需要使用从步骤 2 和步骤 3 中保留的值来完成此步骤。</span><span class="sxs-lookup"><span data-stu-id="b7db4-221">You will need the values preserved from steps 2 and 3 to complete this step.</span></span>  
  
1.  <span data-ttu-id="b7db4-222">计算索引中的非叶级数：</span><span class="sxs-lookup"><span data-stu-id="b7db4-222">Calculate the number of non-leaf levels in the index:</span></span>  
  
     <span data-ttu-id="b7db4-223">***非叶级别***= 1 + 日志 Index_Rows_Per_Page (***Num_Leaf_Pages***  /  ***Index_Rows_Per_Page***) </span><span class="sxs-lookup"><span data-stu-id="b7db4-223">***Non-leaf Levels***  = 1 + log Index_Rows_Per_Page (***Num_Leaf_Pages*** / ***Index_Rows_Per_Page***)</span></span>  
  
     <span data-ttu-id="b7db4-224">将此值向上舍入到最接近的整数。</span><span class="sxs-lookup"><span data-stu-id="b7db4-224">Round this value up to the nearest whole number.</span></span> <span data-ttu-id="b7db4-225">此值不包括非聚集索引的叶级别。</span><span class="sxs-lookup"><span data-stu-id="b7db4-225">This value does not include the leaf level of the nonclustered index.</span></span>  
  
2.  <span data-ttu-id="b7db4-226">计算索引中的非叶页数：</span><span class="sxs-lookup"><span data-stu-id="b7db4-226">Calculate the number of non-leaf pages in the index:</span></span>  
  
     <span data-ttu-id="b7db4-227">***Num_Index_Pages*** = ∑ level (***Num_Leaf_Pages/Index_Rows_Per_Page***<sup>级别</sup>) 其中 1 ***<= level <= level***</span><span class="sxs-lookup"><span data-stu-id="b7db4-227">***Num_Index_Pages***  = ∑Level (***Num_Leaf_Pages/Index_Rows_Per_Page***<sup>Level</sup>)where 1 <= Level <= ***Levels***</span></span>  
  
     <span data-ttu-id="b7db4-228">将每个被加数向上舍入到最接近的整数。</span><span class="sxs-lookup"><span data-stu-id="b7db4-228">Round each summand up to the nearest whole number.</span></span> <span data-ttu-id="b7db4-229">由于是个简单示例，请考虑使用 ***Num_Leaf_Pages*** = 1000 和 ***Index_Rows_Per_Page*** = 25 的索引。</span><span class="sxs-lookup"><span data-stu-id="b7db4-229">As a simple example, consider an index where ***Num_Leaf_Pages*** = 1000 and ***Index_Rows_Per_Page*** = 25.</span></span> <span data-ttu-id="b7db4-230">页级别以上的第一个索引级别存储 1000 个索引行，即每个叶页一个索引行，每页可以包括 25 个索引行。</span><span class="sxs-lookup"><span data-stu-id="b7db4-230">The first index level above the leaf level stores 1000 index rows, which is one index row per leaf page, and 25 index rows can fit per page.</span></span> <span data-ttu-id="b7db4-231">这意味着存储这 1000 个索引行需要 40 页。</span><span class="sxs-lookup"><span data-stu-id="b7db4-231">This means that 40 pages are required to store those 1000 index rows.</span></span> <span data-ttu-id="b7db4-232">下一级索引必须存储 40 行。</span><span class="sxs-lookup"><span data-stu-id="b7db4-232">The next level of the index has to store 40 rows.</span></span> <span data-ttu-id="b7db4-233">这意味着需要 2 页。</span><span class="sxs-lookup"><span data-stu-id="b7db4-233">This means that it requires 2 pages.</span></span> <span data-ttu-id="b7db4-234">最后一级索引必须存储 2 行。</span><span class="sxs-lookup"><span data-stu-id="b7db4-234">The final level of the index has to store 2 rows.</span></span> <span data-ttu-id="b7db4-235">这意味着需要 1 页。</span><span class="sxs-lookup"><span data-stu-id="b7db4-235">This means that it requires 1 page.</span></span> <span data-ttu-id="b7db4-236">这就产生了 43 个非叶索引页。</span><span class="sxs-lookup"><span data-stu-id="b7db4-236">This yields 43 non-leaf index pages.</span></span> <span data-ttu-id="b7db4-237">如果将这些数用到前面的公式中，结果如下：</span><span class="sxs-lookup"><span data-stu-id="b7db4-237">When these numbers are used in the previous formulas, the result is as follows:</span></span>  
  
     <span data-ttu-id="b7db4-238">***非 leaf_Levels*** = 1 + log25 (1000/25) = 3</span><span class="sxs-lookup"><span data-stu-id="b7db4-238">***Non-leaf_Levels***  = 1 + log25 (1000 / 25) = 3</span></span>  
  
     <span data-ttu-id="b7db4-239">***Num_Index_Pages*** = 1000/ (25<sup>3</sup>) + 1000/ (25<sup>2</sup>) + 1000/ (25<sup>1</sup>) = 1 + 2 + 40 = 43，这是示例中所述的页数。</span><span class="sxs-lookup"><span data-stu-id="b7db4-239">***Num_Index_Pages*** = 1000/(25<sup>3</sup>)+ 1000/(25<sup>2</sup>) + 1000/(25<sup>1</sup>) = 1 + 2 + 40 = 43, which is the number of pages described in the example.</span></span>  
  
3.  <span data-ttu-id="b7db4-240">计算索引的大小（每页总共有 8192 个字节）：</span><span class="sxs-lookup"><span data-stu-id="b7db4-240">Calculate the size of the index (8192 total bytes per page):</span></span>  
  
     <span data-ttu-id="b7db4-241">***Index_Space_Used***  = 8192 x ***Num_Index_Pages***</span><span class="sxs-lookup"><span data-stu-id="b7db4-241">***Index_Space_Used***  = 8192 x ***Num_Index_Pages***</span></span>  
  
## <a name="step-4-total-the-calculated-values"></a><span data-ttu-id="b7db4-242">步骤 4.</span><span class="sxs-lookup"><span data-stu-id="b7db4-242">Step 4.</span></span> <span data-ttu-id="b7db4-243">对计算出的值求和</span><span class="sxs-lookup"><span data-stu-id="b7db4-243">Total the Calculated Values</span></span>  
 <span data-ttu-id="b7db4-244">对从前面两个步骤中得到的值求和：</span><span class="sxs-lookup"><span data-stu-id="b7db4-244">Total the values obtained from the previous two steps:</span></span>  
  
 <span data-ttu-id="b7db4-245">非群集索引大小（字节）= ***Leaf_Space_Used*** + ***Index_Space_used***</span><span class="sxs-lookup"><span data-stu-id="b7db4-245">Nonclustered index size (bytes) = ***Leaf_Space_Used*** + ***Index_Space_used***</span></span>  
  
 <span data-ttu-id="b7db4-246">此计算不考虑以下因素：</span><span class="sxs-lookup"><span data-stu-id="b7db4-246">This calculation does not consider the following:</span></span>  
  
-   <span data-ttu-id="b7db4-247">分区</span><span class="sxs-lookup"><span data-stu-id="b7db4-247">Partitioning</span></span>  
  
     <span data-ttu-id="b7db4-248">分区的空间开销很小，但是计算复杂。</span><span class="sxs-lookup"><span data-stu-id="b7db4-248">The space overhead from partitioning is minimal, but complex to calculate.</span></span> <span data-ttu-id="b7db4-249">是否包括它并不重要。</span><span class="sxs-lookup"><span data-stu-id="b7db4-249">It is not important to include.</span></span>  
  
-   <span data-ttu-id="b7db4-250">分配页</span><span class="sxs-lookup"><span data-stu-id="b7db4-250">Allocation pages</span></span>  
  
     <span data-ttu-id="b7db4-251">至少有一个 IAM 页用于跟踪为堆分配的页，但是空间开销很小，并且没有算法可以精确地计算出要使用的 IAM 页数。</span><span class="sxs-lookup"><span data-stu-id="b7db4-251">There is at least one IAM page used to track the pages allocated to a heap, but the space overhead is minimal and there is no algorithm to deterministically calculate exactly how many IAM pages will be used.</span></span>  
  
-   <span data-ttu-id="b7db4-252">大型对象 (LOB) 值</span><span class="sxs-lookup"><span data-stu-id="b7db4-252">Large object (LOB) values</span></span>  
  
     <span data-ttu-id="b7db4-253">精确确定存储 LOB 数据类型 `varchar(max)`、`varbinary(max)`、`nvarchar(max)`、`text`、`ntext`、`xml` 和 `image` 值所用的空间量的算法非常复杂。</span><span class="sxs-lookup"><span data-stu-id="b7db4-253">The algorithm to determine exactly how much space will be used to store the LOB data types `varchar(max)`, `varbinary(max)`, `nvarchar(max)`, `text`, `ntext`, `xml`, and `image` values is complex.</span></span> <span data-ttu-id="b7db4-254">只需加上期望的 LOB 值的平均大小，再乘以 ***Num_Rows***，然后将所得结果加到非群集索引的总大小。</span><span class="sxs-lookup"><span data-stu-id="b7db4-254">It is sufficient to just add the average size of the LOB values expected, multiply by ***Num_Rows***, and add that to the total nonclustered index size.</span></span>  
  
-   <span data-ttu-id="b7db4-255">压缩</span><span class="sxs-lookup"><span data-stu-id="b7db4-255">Compression</span></span>  
  
     <span data-ttu-id="b7db4-256">无法预先计算压缩索引的大小。</span><span class="sxs-lookup"><span data-stu-id="b7db4-256">You cannot pre-calculate the size of a compressed index.</span></span>  
  
-   <span data-ttu-id="b7db4-257">稀疏列</span><span class="sxs-lookup"><span data-stu-id="b7db4-257">Sparse columns</span></span>  
  
     <span data-ttu-id="b7db4-258">有关稀疏列的空间要求的信息，请参阅 [Use Sparse Columns](../tables/use-sparse-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="b7db4-258">For information about the space requirements of sparse columns, see [Use Sparse Columns](../tables/use-sparse-columns.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7db4-259">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b7db4-259">See Also</span></span>  
 <span data-ttu-id="b7db4-260">[描述的聚集索引和非聚集索引](../indexes/clustered-and-nonclustered-indexes-described.md) </span><span class="sxs-lookup"><span data-stu-id="b7db4-260">[Clustered and Nonclustered Indexes Described](../indexes/clustered-and-nonclustered-indexes-described.md) </span></span>  
 <span data-ttu-id="b7db4-261">[创建非聚集索引](../indexes/create-nonclustered-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="b7db4-261">[Create Nonclustered Indexes](../indexes/create-nonclustered-indexes.md) </span></span>  
 <span data-ttu-id="b7db4-262">[创建聚集索引](../indexes/create-clustered-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="b7db4-262">[Create Clustered Indexes](../indexes/create-clustered-indexes.md) </span></span>  
 <span data-ttu-id="b7db4-263">[估计表的大小](estimate-the-size-of-a-table.md) </span><span class="sxs-lookup"><span data-stu-id="b7db4-263">[Estimate the Size of a Table](estimate-the-size-of-a-table.md) </span></span>  
 <span data-ttu-id="b7db4-264">[估计聚集索引的大小](estimate-the-size-of-a-clustered-index.md) </span><span class="sxs-lookup"><span data-stu-id="b7db4-264">[Estimate the Size of a Clustered Index](estimate-the-size-of-a-clustered-index.md) </span></span>  
 <span data-ttu-id="b7db4-265">[估计堆的大小](estimate-the-size-of-a-heap.md) </span><span class="sxs-lookup"><span data-stu-id="b7db4-265">[Estimate the Size of a Heap](estimate-the-size-of-a-heap.md) </span></span>  
 [<span data-ttu-id="b7db4-266">估计数据库的大小</span><span class="sxs-lookup"><span data-stu-id="b7db4-266">Estimate the Size of a Database</span></span>](estimate-the-size-of-a-database.md)  
  
  
