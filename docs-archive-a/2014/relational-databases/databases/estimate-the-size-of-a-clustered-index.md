---
title: 估计聚集索引的大小 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- space allocation [SQL Server], index size
- size [SQL Server], tables
- disk space [SQL Server], indexes
- predicting table size [SQL Server]
- table size [SQL Server]
- estimating table size
- space [SQL Server], indexes
- clustered indexes, table size
- nonclustered indexes [SQL Server], table size
- designing databases [SQL Server], estimating size
- calculating table size
ms.assetid: 2b5137f8-98ad-46b5-9aae-4c980259bf8d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4d224c5ae55cc5ec7690ca0962cbc2130bac22e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693933"
---
# <a name="estimate-the-size-of-a-clustered-index"></a><span data-ttu-id="385cb-102">估计聚集索引的大小</span><span class="sxs-lookup"><span data-stu-id="385cb-102">Estimate the Size of a Clustered Index</span></span>
  <span data-ttu-id="385cb-103">您可以使用下列步骤估计存储聚集索引中的数据所需的空间大小：</span><span class="sxs-lookup"><span data-stu-id="385cb-103">You can use the following steps to estimate the amount of space that is required to store data in a clustered index:</span></span>  
  
1.  <span data-ttu-id="385cb-104">计算存储聚集索引叶级数据所用的空间。</span><span class="sxs-lookup"><span data-stu-id="385cb-104">Calculate the space used to store data in the leaf level of the clustered index.</span></span>  
  
2.  <span data-ttu-id="385cb-105">计算存储聚集索引的索引信息所用的空间。</span><span class="sxs-lookup"><span data-stu-id="385cb-105">Calculate the space used to store index information for the clustered index.</span></span>  
  
3.  <span data-ttu-id="385cb-106">对计算出的值求和。</span><span class="sxs-lookup"><span data-stu-id="385cb-106">Total the calculated values.</span></span>  
  
## <a name="step-1-calculate-the-space-used-to-store-data-in-the-leaf-level"></a><span data-ttu-id="385cb-107">步骤 1。</span><span class="sxs-lookup"><span data-stu-id="385cb-107">Step 1.</span></span> <span data-ttu-id="385cb-108">计算在叶级别存储数据所用的空间</span><span class="sxs-lookup"><span data-stu-id="385cb-108">Calculate the Space Used to Store Data in the Leaf Level</span></span>  
  
1.  <span data-ttu-id="385cb-109">指定表中显示的行数：</span><span class="sxs-lookup"><span data-stu-id="385cb-109">Specify the number of rows that will be present in the table:</span></span>  
  
     <span data-ttu-id="385cb-110">***Num_Rows***  = 表中的行数</span><span class="sxs-lookup"><span data-stu-id="385cb-110">***Num_Rows***  = number of rows in the table</span></span>  
  
2.  <span data-ttu-id="385cb-111">指定固定长度和可变长度列的数量，并计算存储所需的空间：</span><span class="sxs-lookup"><span data-stu-id="385cb-111">Specify the number of fixed-length and variable-length columns and calculate the space that is required for their storage:</span></span>  
  
     <span data-ttu-id="385cb-112">计算每组列在数据行中所占据的空间。</span><span class="sxs-lookup"><span data-stu-id="385cb-112">Calculate the space that each of these groups of columns occupies within the data row.</span></span> <span data-ttu-id="385cb-113">列的大小取决于数据类型和长度规定。</span><span class="sxs-lookup"><span data-stu-id="385cb-113">The size of a column depends on the data type and length specification.</span></span>  
  
     <span data-ttu-id="385cb-114">***Num_Cols***  = 总列数（固定长度和可变长度）</span><span class="sxs-lookup"><span data-stu-id="385cb-114">***Num_Cols***  = total number of columns (fixed-length and variable-length)</span></span>  
  
     <span data-ttu-id="385cb-115">***Fixed_Data_Size***  = 所有固定长度列的总字节大小</span><span class="sxs-lookup"><span data-stu-id="385cb-115">***Fixed_Data_Size***  = total byte size of all fixed-length columns</span></span>  
  
     <span data-ttu-id="385cb-116">***Num_Variable_Cols***  = 可变长度列数</span><span class="sxs-lookup"><span data-stu-id="385cb-116">***Num_Variable_Cols***  = number of variable-length columns</span></span>  
  
     <span data-ttu-id="385cb-117">***Max_Var_Size***  = 所有可变长度列的最大字节大小</span><span class="sxs-lookup"><span data-stu-id="385cb-117">***Max_Var_Size***  = maximum byte size of all variable-length columns</span></span>  
  
3.  <span data-ttu-id="385cb-118">如果聚集索引不唯一，则请说明“唯一标识符  ”列：</span><span class="sxs-lookup"><span data-stu-id="385cb-118">If the clustered index is nonunique, account for the *uniqueifier* column:</span></span>  
  
     <span data-ttu-id="385cb-119">唯一标识符是可为 Null 的可变长度列。</span><span class="sxs-lookup"><span data-stu-id="385cb-119">The uniqueifier is a nullable, variable-length column.</span></span> <span data-ttu-id="385cb-120">在具有非唯一键值的行中，它非 Null 而且大小为 4 个字节。</span><span class="sxs-lookup"><span data-stu-id="385cb-120">It will be nonnull and 4 bytes in size in rows that have nonunique key values.</span></span> <span data-ttu-id="385cb-121">此值是索引键的一部分，用于确保每一行都具有唯一的键值。</span><span class="sxs-lookup"><span data-stu-id="385cb-121">This value is part of the index key and is required to make sure that every row has a unique key value.</span></span>  
  
     <span data-ttu-id="385cb-122">***Num_Cols***  = ***Num_Cols*** + 1</span><span class="sxs-lookup"><span data-stu-id="385cb-122">***Num_Cols***  = ***Num_Cols*** + 1</span></span>  
  
     <span data-ttu-id="385cb-123">***Num_Variable_Cols***  = ***Num_Variable_Cols*** + 1</span><span class="sxs-lookup"><span data-stu-id="385cb-123">***Num_Variable_Cols***  = ***Num_Variable_Cols*** + 1</span></span>  
  
     <span data-ttu-id="385cb-124">***Max_Var_Size***  = ***Max_Var_Size*** + 4</span><span class="sxs-lookup"><span data-stu-id="385cb-124">***Max_Var_Size***  = ***Max_Var_Size*** + 4</span></span>  
  
     <span data-ttu-id="385cb-125">这些修改假定所有值都不是唯一的。</span><span class="sxs-lookup"><span data-stu-id="385cb-125">These modifications assume that all values will be nonunique.</span></span>  
  
4.  <span data-ttu-id="385cb-126">保留行中称为 Null 位图的部分以管理列的为空性。</span><span class="sxs-lookup"><span data-stu-id="385cb-126">Part of the row, known as the null bitmap, is reserved to manage column nullability.</span></span> <span data-ttu-id="385cb-127">计算其大小：</span><span class="sxs-lookup"><span data-stu-id="385cb-127">Calculate its size:</span></span>  
  
     <span data-ttu-id="385cb-128">***Null_Bitmap***  = 2 + ((***Num_Cols*** + 7) / 8)</span><span class="sxs-lookup"><span data-stu-id="385cb-128">***Null_Bitmap***  = 2 + ((***Num_Cols*** + 7) / 8)</span></span>  
  
     <span data-ttu-id="385cb-129">仅使用上述表达式中的整数部分，而放弃所有余数。</span><span class="sxs-lookup"><span data-stu-id="385cb-129">Only the integer part of the previous expression should be used; discard any remainder.</span></span>  
  
5.  <span data-ttu-id="385cb-130">计算可变长度数据的大小：</span><span class="sxs-lookup"><span data-stu-id="385cb-130">Calculate the variable-length data size:</span></span>  
  
     <span data-ttu-id="385cb-131">如果表中有可变长度列，请确定在行中存储这些列需使用的空间：</span><span class="sxs-lookup"><span data-stu-id="385cb-131">If there are variable-length columns in the table, determine how much space is used to store the columns within the row:</span></span>  
  
     <span data-ttu-id="385cb-132">***Variable_Data_Size***  = 2 + (***Num_Variable_Cols*** x 2) + ***Max_Var_Size***</span><span class="sxs-lookup"><span data-stu-id="385cb-132">***Variable_Data_Size***  = 2 + (***Num_Variable_Cols*** x 2) + ***Max_Var_Size***</span></span>  
  
     <span data-ttu-id="385cb-133">添加到 ***Max_Var_Size*** 中的字节用于跟踪每个可变列。</span><span class="sxs-lookup"><span data-stu-id="385cb-133">The bytes added to ***Max_Var_Size*** are for tracking each variable column.</span></span> <span data-ttu-id="385cb-134">此公式假设所有可变长度列均百分之百充满。</span><span class="sxs-lookup"><span data-stu-id="385cb-134">This formula assumes that all variable-length columns are 100 percent full.</span></span> <span data-ttu-id="385cb-135">如果预计可变长度列占用的存储空间比例较低，则可以按照该比例调整 ***Max_Var_Size*** 值，从而对整个表大小得出一个更准确的估计。</span><span class="sxs-lookup"><span data-stu-id="385cb-135">If you anticipate that a smaller percentage of the variable-length column storage space will be used, you can adjust the ***Max_Var_Size*** value by that percentage to yield a more accurate estimate of the overall table size.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="385cb-136">您可以组合 `varchar`、`nvarchar`、`varbinary` 或 `sql_variant` 列，使得定义的表的总宽度超过 8,060 字节。</span><span class="sxs-lookup"><span data-stu-id="385cb-136">You can combine `varchar`, `nvarchar`, `varbinary`, or `sql_variant` columns that cause the total defined table width to exceed 8,060 bytes.</span></span> <span data-ttu-id="385cb-137">对于 `varchar`、`varbinary` 或 `sql_variant` 中的每一列，其长度不能超过 8,000 字节，对于 `nvarchar` 列，不能超过 4,000 字节。</span><span class="sxs-lookup"><span data-stu-id="385cb-137">The length of each one of these columns must still fall within the limit of 8,000 bytes for a `varchar`, `varbinary`, or `sql_variant` column, and 4,000 bytes for `nvarchar` columns.</span></span> <span data-ttu-id="385cb-138">但是，表中这些列的组合宽度可超过 8,060 字节的限制。</span><span class="sxs-lookup"><span data-stu-id="385cb-138">However, their combined widths may exceed the 8,060 byte limit in a table.</span></span>  
  
     <span data-ttu-id="385cb-139">如果没有可变长度列，请将 ***Variable_Data_Size*** 设置为 0。</span><span class="sxs-lookup"><span data-stu-id="385cb-139">If there are no variable-length columns, set ***Variable_Data_Size*** to 0.</span></span>  
  
6.  <span data-ttu-id="385cb-140">计算总的行大小：</span><span class="sxs-lookup"><span data-stu-id="385cb-140">Calculate the total row size:</span></span>  
  
     <span data-ttu-id="385cb-141">***Row_Size***  = ***Fixed_Data_Size*** + ***Variable_Data_Size*** + ***Null_Bitmap*** + 4</span><span class="sxs-lookup"><span data-stu-id="385cb-141">***Row_Size***  = ***Fixed_Data_Size*** + ***Variable_Data_Size*** + ***Null_Bitmap*** + 4</span></span>  
  
     <span data-ttu-id="385cb-142">值 4 是数据行的行标题的开销。</span><span class="sxs-lookup"><span data-stu-id="385cb-142">The value 4 is the row header overhead of a data row.</span></span>  
  
7.  <span data-ttu-id="385cb-143">下一步，计算每页的行数（每页有 8096 个可用字节）：</span><span class="sxs-lookup"><span data-stu-id="385cb-143">Calculate the number of rows per page (8096 free bytes per page):</span></span>  
  
     <span data-ttu-id="385cb-144">***Rows_Per_Page***  = 8096 / (***Row_Size*** + 2)</span><span class="sxs-lookup"><span data-stu-id="385cb-144">***Rows_Per_Page***  = 8096 / (***Row_Size*** + 2)</span></span>  
  
     <span data-ttu-id="385cb-145">因为行不跨页，所以每页的行数应向下舍入到最接近的整数。</span><span class="sxs-lookup"><span data-stu-id="385cb-145">Because rows do not span pages, the number of rows per page should be rounded down to the nearest whole row.</span></span> <span data-ttu-id="385cb-146">公式中的数值 2 是计算行数时引入的行大小余量。</span><span class="sxs-lookup"><span data-stu-id="385cb-146">The value 2 in the formula is for the row's entry in the slot array of the page.</span></span>  
  
8.  <span data-ttu-id="385cb-147">根据指定的 [填充因子](../indexes/specify-fill-factor-for-an-index.md) 计算每页保留的空行数：</span><span class="sxs-lookup"><span data-stu-id="385cb-147">Calculate the number of reserved free rows per page, based on the [fill factor](../indexes/specify-fill-factor-for-an-index.md) specified:</span></span>  
  
     <span data-ttu-id="385cb-148">***Free_Rows_Per_Page***  = 8096 x ((100 - ***Fill_Factor***) / 100) / (***Row_Size*** + 2)</span><span class="sxs-lookup"><span data-stu-id="385cb-148">***Free_Rows_Per_Page***  = 8096 x ((100 - ***Fill_Factor***) / 100) / (***Row_Size*** + 2)</span></span>  
  
     <span data-ttu-id="385cb-149">计算中使用的填充因子为整数值，而不是百分比。</span><span class="sxs-lookup"><span data-stu-id="385cb-149">The fill factor used in the calculation is an integer value instead of a percentage.</span></span> <span data-ttu-id="385cb-150">因为行不跨页，所以每页的行数应向下舍入到最接近的整数。</span><span class="sxs-lookup"><span data-stu-id="385cb-150">Because rows do not span pages, the number of rows per page should be rounded down to the nearest whole row.</span></span> <span data-ttu-id="385cb-151">填充因子增大时，每页将存储更多的数据，因此页数将减少。</span><span class="sxs-lookup"><span data-stu-id="385cb-151">As the fill factor grows, more data will be stored on each page and there will be fewer pages.</span></span> <span data-ttu-id="385cb-152">公式中的数值 2 是计算行数时引入的行大小余量。</span><span class="sxs-lookup"><span data-stu-id="385cb-152">The value 2 in the formula is for the row's entry in the slot array of the page.</span></span>  
  
9. <span data-ttu-id="385cb-153">计算存储所有行所需的页数：</span><span class="sxs-lookup"><span data-stu-id="385cb-153">Calculate the number of pages required to store all the rows:</span></span>  
  
     <span data-ttu-id="385cb-154">***Num_Leaf_Pages***  = ***Num_Rows*** / (***Rows_Per_Page*** - ***Free_Rows_Per_Page***)</span><span class="sxs-lookup"><span data-stu-id="385cb-154">***Num_Leaf_Pages***  = ***Num_Rows*** / (***Rows_Per_Page*** - ***Free_Rows_Per_Page***)</span></span>  
  
     <span data-ttu-id="385cb-155">估计的页数应向上舍入到最接近的整数。</span><span class="sxs-lookup"><span data-stu-id="385cb-155">The number of pages estimated should be rounded up to the nearest whole page.</span></span>  
  
10. <span data-ttu-id="385cb-156">计算在叶级别中存储数据所需的空间大小（每页共有 8192 个字节）：</span><span class="sxs-lookup"><span data-stu-id="385cb-156">Calculate the amount of space that is required to store the data in the leaf level (8192 total bytes per page):</span></span>  
  
     <span data-ttu-id="385cb-157">***Leaf_space_used***  = 8192 x ***Num_Leaf_Pages***</span><span class="sxs-lookup"><span data-stu-id="385cb-157">***Leaf_space_used***  = 8192 x ***Num_Leaf_Pages***</span></span>  
  
## <a name="step-2-calculate-the-space-used-to-store-index-information"></a><span data-ttu-id="385cb-158">步骤 2.</span><span class="sxs-lookup"><span data-stu-id="385cb-158">Step 2.</span></span> <span data-ttu-id="385cb-159">计算存储索引信息所用的空间</span><span class="sxs-lookup"><span data-stu-id="385cb-159">Calculate the Space Used to Store Index Information</span></span>  
 <span data-ttu-id="385cb-160">您可以使用下列步骤估计存储索引的较高级别所需的空间大小：</span><span class="sxs-lookup"><span data-stu-id="385cb-160">You can use the following steps to estimate the amount of space that is required to store the upper levels of the index:</span></span>  
  
1.  <span data-ttu-id="385cb-161">指定索引键中固定长度和可变长度列的数量，并计算存储所需的空间：</span><span class="sxs-lookup"><span data-stu-id="385cb-161">Specify the number of fixed-length and variable-length columns in the index key and calculate the space that is required for their storage:</span></span>  
  
     <span data-ttu-id="385cb-162">索引键列可以包括固定长度和可变长度列。</span><span class="sxs-lookup"><span data-stu-id="385cb-162">The key columns of an index can include fixed-length and variable-length columns.</span></span> <span data-ttu-id="385cb-163">若要估计内部级别索引行的大小，请计算每组列在索引行中所占据的空间。</span><span class="sxs-lookup"><span data-stu-id="385cb-163">To estimate the interior level index row size, calculate the space that each of these groups of columns occupies within the index row.</span></span> <span data-ttu-id="385cb-164">列的大小取决于数据类型和长度规定。</span><span class="sxs-lookup"><span data-stu-id="385cb-164">The size of a column depends on the data type and length specification.</span></span>  
  
     <span data-ttu-id="385cb-165">***Num_Key_Cols***  = 总键列数（固定长度和可变长度）</span><span class="sxs-lookup"><span data-stu-id="385cb-165">***Num_Key_Cols***  = total number of key columns (fixed-length and variable-length)</span></span>  
  
     <span data-ttu-id="385cb-166">***Fixed_Key_Size***  = 所有固定长度键列的总字节大小</span><span class="sxs-lookup"><span data-stu-id="385cb-166">***Fixed_Key_Size***  = total byte size of all fixed-length key columns</span></span>  
  
     <span data-ttu-id="385cb-167">***Num_Variable_Key_Cols***  = 可变长度键列数</span><span class="sxs-lookup"><span data-stu-id="385cb-167">***Num_Variable_Key_Cols***  = number of variable-length key columns</span></span>  
  
     <span data-ttu-id="385cb-168">***Max_Var_Key_Size***  = 所有可变长度键列的最大字节大小</span><span class="sxs-lookup"><span data-stu-id="385cb-168">***Max_Var_Key_Size***  = maximum byte size of all variable-length key columns</span></span>  
  
2.  <span data-ttu-id="385cb-169">如果索引不唯一，则请说明所需的任意唯一标识符：</span><span class="sxs-lookup"><span data-stu-id="385cb-169">Account for any uniqueifier needed if the index is nonunique:</span></span>  
  
     <span data-ttu-id="385cb-170">唯一标识符是可为 Null 的可变长度列。</span><span class="sxs-lookup"><span data-stu-id="385cb-170">The uniqueifier is a nullable, variable-length column.</span></span> <span data-ttu-id="385cb-171">它将是非 Null 的，在具有非唯一索引键值的行中的大小是 4 个字节。</span><span class="sxs-lookup"><span data-stu-id="385cb-171">It will be nonnull and 4 bytes in size in rows that have nonunique index key values.</span></span> <span data-ttu-id="385cb-172">此值是索引键的一部分，用于确保每一行都具有唯一的键值。</span><span class="sxs-lookup"><span data-stu-id="385cb-172">This value is part of the index key and is required to make sure that every row has a unique key value.</span></span>  
  
     <span data-ttu-id="385cb-173">***Num_Key_Cols***  = ***Num_Key_Cols*** + 1</span><span class="sxs-lookup"><span data-stu-id="385cb-173">***Num_Key_Cols***  = ***Num_Key_Cols*** + 1</span></span>  
  
     <span data-ttu-id="385cb-174">***Num_Variable_Key_Cols***  = ***Num_Variable_Key_Cols*** + 1</span><span class="sxs-lookup"><span data-stu-id="385cb-174">***Num_Variable_Key_Cols***  = ***Num_Variable_Key_Cols*** + 1</span></span>  
  
     <span data-ttu-id="385cb-175">***Max_Var_Key_Size***  = ***Max_Var_Key_Size*** + 4</span><span class="sxs-lookup"><span data-stu-id="385cb-175">***Max_Var_Key_Size***  = ***Max_Var_Key_Size*** + 4</span></span>  
  
     <span data-ttu-id="385cb-176">这些修改假定所有值都不是唯一的。</span><span class="sxs-lookup"><span data-stu-id="385cb-176">These modifications assume that all values will be nonunique.</span></span>  
  
3.  <span data-ttu-id="385cb-177">计算 Null 位图大小：</span><span class="sxs-lookup"><span data-stu-id="385cb-177">Calculate the null bitmap size:</span></span>  
  
     <span data-ttu-id="385cb-178">如果索引键中有允许为 Null 的列，则索引行的一部分将为 Null 位图保留。</span><span class="sxs-lookup"><span data-stu-id="385cb-178">If there are nullable columns in the index key, part of the index row is reserved for the null bitmap.</span></span> <span data-ttu-id="385cb-179">计算其大小：</span><span class="sxs-lookup"><span data-stu-id="385cb-179">Calculate its size:</span></span>  
  
     <span data-ttu-id="385cb-180">***Index_Null_Bitmap***  = 2 + ((索引行中的列数 + 7) / 8)</span><span class="sxs-lookup"><span data-stu-id="385cb-180">***Index_Null_Bitmap***  = 2 + ((number of columns in the index row + 7) / 8)</span></span>  
  
     <span data-ttu-id="385cb-181">仅应使用上述表达式中的整数部分，</span><span class="sxs-lookup"><span data-stu-id="385cb-181">Only the integer part of the previous expression should be used.</span></span> <span data-ttu-id="385cb-182">而放弃所有余数。</span><span class="sxs-lookup"><span data-stu-id="385cb-182">Discard any remainder.</span></span>  
  
     <span data-ttu-id="385cb-183">如果没有可为 Null 的键列，请将 ***Index_Null_Bitmap*** 设置为 0。</span><span class="sxs-lookup"><span data-stu-id="385cb-183">If there are no nullable key columns, set ***Index_Null_Bitmap*** to 0.</span></span>  
  
4.  <span data-ttu-id="385cb-184">计算可变长度数据的大小：</span><span class="sxs-lookup"><span data-stu-id="385cb-184">Calculate the variable-length data size:</span></span>  
  
     <span data-ttu-id="385cb-185">如果索引中有可变长度列，请确定在索引行中存储这些列需使用的空间：</span><span class="sxs-lookup"><span data-stu-id="385cb-185">If there are variable-length columns in the index, determine how much space is used to store the columns within the index row:</span></span>  
  
     <span data-ttu-id="385cb-186">***Variable_Key_Size***  = 2 + (***Num_Variable_Key_Cols*** x 2) + ***Max_Var_Key_Size***</span><span class="sxs-lookup"><span data-stu-id="385cb-186">***Variable_Key_Size***  = 2 + (***Num_Variable_Key_Cols*** x 2) + ***Max_Var_Key_Size***</span></span>  
  
     <span data-ttu-id="385cb-187">添加到 ***Max_Var_Key_Size*** 中的字节用于跟踪每个可变长度列。</span><span class="sxs-lookup"><span data-stu-id="385cb-187">The bytes added to ***Max_Var_Key_Size*** are for tracking each variable-length column.</span></span> <span data-ttu-id="385cb-188">此公式假设所有可变长度列均百分之百充满。</span><span class="sxs-lookup"><span data-stu-id="385cb-188">This formula assumes that all variable-length columns are 100 percent full.</span></span> <span data-ttu-id="385cb-189">如果预计可变长度列占用的存储空间比例较低，则可以按照该比例调整 ***Max_Var_Key_Size*** 值，从而对整个表大小得出一个更准确的估计。</span><span class="sxs-lookup"><span data-stu-id="385cb-189">If you anticipate that a smaller percentage of the variable-length column storage space will be used, you can adjust the ***Max_Var_Key_Size*** value by that percentage to yield a more accurate estimate of the overall table size.</span></span>  
  
     <span data-ttu-id="385cb-190">如果没有可变长度列，请将 ***Variable_Key_Size*** 设置为 0。</span><span class="sxs-lookup"><span data-stu-id="385cb-190">If there are no variable-length columns, set ***Variable_Key_Size*** to 0.</span></span>  
  
5.  <span data-ttu-id="385cb-191">计算索引行大小：</span><span class="sxs-lookup"><span data-stu-id="385cb-191">Calculate the index row size:</span></span>  
  
     <span data-ttu-id="385cb-192">***Index_Row_Size***  = ***Fixed_Key_Size*** + ***Variable_Key_Size*** + ***Index_Null_Bitmap*** + 1（对应于索引行的行标题开销）+ 6（对应于子页 ID 指针）</span><span class="sxs-lookup"><span data-stu-id="385cb-192">***Index_Row_Size***  = ***Fixed_Key_Size*** + ***Variable_Key_Size*** + ***Index_Null_Bitmap*** + 1 (for row header overhead of an index row) + 6 (for the child page ID pointer)</span></span>  
  
6.  <span data-ttu-id="385cb-193">下一步，计算每页的索引行数（每页有 8096 个可用字节）：</span><span class="sxs-lookup"><span data-stu-id="385cb-193">Calculate the number of index rows per page (8096 free bytes per page):</span></span>  
  
     <span data-ttu-id="385cb-194">***Index_Rows_Per_Page***  = 8096 / (***Index_Row_Size*** + 2)</span><span class="sxs-lookup"><span data-stu-id="385cb-194">***Index_Rows_Per_Page***  = 8096 / (***Index_Row_Size*** + 2)</span></span>  
  
     <span data-ttu-id="385cb-195">因为索引行不能跨页，所以每页的索引行数应向下舍入到最接近的整数。</span><span class="sxs-lookup"><span data-stu-id="385cb-195">Because index rows do not span pages, the number of index rows per page should be rounded down to the nearest whole row.</span></span> <span data-ttu-id="385cb-196">公式中的 2 是计算行数时引入的行大小余量。</span><span class="sxs-lookup"><span data-stu-id="385cb-196">The 2 in the formula is for the row's entry in the page's slot array.</span></span>  
  
7.  <span data-ttu-id="385cb-197">计算索引中的级别数：</span><span class="sxs-lookup"><span data-stu-id="385cb-197">Calculate the number of levels in the index:</span></span>  
  
     <span data-ttu-id="385cb-198">***非 leaf_Levels*** = 1 + log Index_Rows_Per_Page (***Num_Leaf_Pages***  /  ***Index_Rows_Per_Page***) </span><span class="sxs-lookup"><span data-stu-id="385cb-198">***Non-leaf_Levels***  = 1 + log Index_Rows_Per_Page (***Num_Leaf_Pages*** / ***Index_Rows_Per_Page***)</span></span>  
  
     <span data-ttu-id="385cb-199">将此值向上舍入到最接近的整数。</span><span class="sxs-lookup"><span data-stu-id="385cb-199">Round this value up to the nearest whole number.</span></span> <span data-ttu-id="385cb-200">此值不包括聚集索引的叶级别。</span><span class="sxs-lookup"><span data-stu-id="385cb-200">This value does not include the leaf level of the clustered index.</span></span>  
  
8.  <span data-ttu-id="385cb-201">计算索引中的非叶页数：</span><span class="sxs-lookup"><span data-stu-id="385cb-201">Calculate the number of non-leaf pages in the index:</span></span>  
  
     <span data-ttu-id="385cb-202">***Num_Index_Pages =*** ∑ level \*\*\* (Num_Leaf_Pages/ (Index_Rows_Per_Page***<sup>级别</sup>***) # B3\*\*\*</span><span class="sxs-lookup"><span data-stu-id="385cb-202">***Num_Index_Pages =*** ∑Level ***(Num_Leaf_Pages / (Index_Rows_Per_Page***<sup>Level</sup>***))***</span></span>  
  
     <span data-ttu-id="385cb-203">其中，1 <= Level <= ***Non-leaf_Levels***</span><span class="sxs-lookup"><span data-stu-id="385cb-203">where 1 <= Level <= ***Non-leaf_Levels***</span></span>  
  
     <span data-ttu-id="385cb-204">将每个被加数向上舍入到最接近的整数。</span><span class="sxs-lookup"><span data-stu-id="385cb-204">Round each summand up to the nearest whole number.</span></span> <span data-ttu-id="385cb-205">由于是个简单示例，请考虑使用 ***Num_Leaf_Pages*** = 1000 和 ***Index_Rows_Per_Page*** = 25 的索引。</span><span class="sxs-lookup"><span data-stu-id="385cb-205">As a simple example, consider an index where ***Num_Leaf_Pages*** = 1000 and ***Index_Rows_Per_Page*** = 25.</span></span> <span data-ttu-id="385cb-206">页级别以上的第一个索引级别存储 1000 个索引行，即每个叶页一个索引行，每页可以包括 25 个索引行。</span><span class="sxs-lookup"><span data-stu-id="385cb-206">The first index level above the leaf level stores 1000 index rows, which is one index row per leaf page, and 25 index rows can fit per page.</span></span> <span data-ttu-id="385cb-207">这意味着存储这 1000 个索引行需要 40 页。</span><span class="sxs-lookup"><span data-stu-id="385cb-207">This means that 40 pages are required to store those 1000 index rows.</span></span> <span data-ttu-id="385cb-208">下一级索引必须存储 40 行。</span><span class="sxs-lookup"><span data-stu-id="385cb-208">The next level of the index has to store 40 rows.</span></span> <span data-ttu-id="385cb-209">这意味着需要 2 页。</span><span class="sxs-lookup"><span data-stu-id="385cb-209">This means it requires 2 pages.</span></span> <span data-ttu-id="385cb-210">最后一级索引必须存储 2 行。</span><span class="sxs-lookup"><span data-stu-id="385cb-210">The final level of the index has to store 2 rows.</span></span> <span data-ttu-id="385cb-211">这意味着需要 1 页。</span><span class="sxs-lookup"><span data-stu-id="385cb-211">This means it requires 1 page.</span></span> <span data-ttu-id="385cb-212">这就提供了 43 个非叶索引页。</span><span class="sxs-lookup"><span data-stu-id="385cb-212">This gives 43 non-leaf index pages.</span></span> <span data-ttu-id="385cb-213">如果将这些数用到前面的公式中，结果如下：</span><span class="sxs-lookup"><span data-stu-id="385cb-213">When these numbers are used in the previous formulas, the outcome is as follows:</span></span>  
  
     <span data-ttu-id="385cb-214">***非 leaf_Levels*** = 1 + log25 (1000/25) = 3</span><span class="sxs-lookup"><span data-stu-id="385cb-214">***Non-leaf_Levels***  = 1 + log25 (1000 / 25) = 3</span></span>  
  
     <span data-ttu-id="385cb-215">***Num_Index_Pages*** = 1000/ (25<sup>3</sup>) + 1000/ (25<sup>2</sup>) + 1000/ (25<sup>1</sup>) = 1 + 2 + 40 = 43，这是示例中所述的页数。</span><span class="sxs-lookup"><span data-stu-id="385cb-215">***Num_Index_Pages*** = 1000/(25<sup>3</sup>)+ 1000/(25<sup>2</sup>) + 1000/(25<sup>1</sup>) = 1 + 2 + 40 = 43, which is the number of pages described in the example.</span></span>  
  
9. <span data-ttu-id="385cb-216">计算索引的大小（每页总共有 8192 个字节）：</span><span class="sxs-lookup"><span data-stu-id="385cb-216">Calculate the size of the index (8192 total bytes per page):</span></span>  
  
     <span data-ttu-id="385cb-217">***Index_Space_Used***  = 8192 x ***Num_Index_Pages***</span><span class="sxs-lookup"><span data-stu-id="385cb-217">***Index_Space_Used***  = 8192 x ***Num_Index_Pages***</span></span>  
  
## <a name="step-3-total-the-calculated-values"></a><span data-ttu-id="385cb-218">步骤 3.</span><span class="sxs-lookup"><span data-stu-id="385cb-218">Step 3.</span></span> <span data-ttu-id="385cb-219">对计算出的值求和</span><span class="sxs-lookup"><span data-stu-id="385cb-219">Total the Calculated Values</span></span>  
 <span data-ttu-id="385cb-220">对从前面两个步骤中得到的值求和：</span><span class="sxs-lookup"><span data-stu-id="385cb-220">Total the values obtained from the previous two steps:</span></span>  
  
 <span data-ttu-id="385cb-221">群集索引大小（字节）= ***Leaf_Space_Used*** + ***Index_Space_used***</span><span class="sxs-lookup"><span data-stu-id="385cb-221">Clustered index size (bytes) = ***Leaf_Space_Used*** + ***Index_Space_used***</span></span>  
  
 <span data-ttu-id="385cb-222">此计算不考虑以下因素：</span><span class="sxs-lookup"><span data-stu-id="385cb-222">This calculation does not consider the following:</span></span>  
  
-   <span data-ttu-id="385cb-223">分区</span><span class="sxs-lookup"><span data-stu-id="385cb-223">Partitioning</span></span>  
  
     <span data-ttu-id="385cb-224">分区的空间开销很小，但是计算复杂。</span><span class="sxs-lookup"><span data-stu-id="385cb-224">The space overhead from partitioning is minimal, but complex to calculate.</span></span> <span data-ttu-id="385cb-225">是否包括它并不重要。</span><span class="sxs-lookup"><span data-stu-id="385cb-225">It is not important to include.</span></span>  
  
-   <span data-ttu-id="385cb-226">分配页</span><span class="sxs-lookup"><span data-stu-id="385cb-226">Allocation pages</span></span>  
  
     <span data-ttu-id="385cb-227">至少有一个 IAM 页用于跟踪为堆分配的页，但是空间开销很小，并且没有算法可以精确地计算出要使用的 IAM 页数。</span><span class="sxs-lookup"><span data-stu-id="385cb-227">There is at least one IAM page used to track the pages allocated to a heap, but the space overhead is minimal and there is no algorithm to deterministically calculate exactly how many IAM pages will be used.</span></span>  
  
-   <span data-ttu-id="385cb-228">大型对象 (LOB) 值</span><span class="sxs-lookup"><span data-stu-id="385cb-228">Large object (LOB) values</span></span>  
  
     <span data-ttu-id="385cb-229">精确确定存储 LOB 数据类型 `varchar(max)`、`varbinary(max)`、`nvarchar(max)`、`text`、`ntext`、`xml` 和 `image` 值所用的空间量的算法非常复杂。</span><span class="sxs-lookup"><span data-stu-id="385cb-229">The algorithm to determine exactly how much space will be used to store the LOB data types `varchar(max)`, `varbinary(max)`, `nvarchar(max)`, `text`, `ntext`, `xml`, and `image` values is complex.</span></span> <span data-ttu-id="385cb-230">只需加上所期望的 LOB 值的平均大小，再乘以 ***Num_Rows***，然后再加上群集索引的总大小就可以了。</span><span class="sxs-lookup"><span data-stu-id="385cb-230">It is sufficient to just add the average size of the LOB values that are expected, multiply by ***Num_Rows***, and add that to the total clustered index size.</span></span>  
  
-   <span data-ttu-id="385cb-231">压缩</span><span class="sxs-lookup"><span data-stu-id="385cb-231">Compression</span></span>  
  
     <span data-ttu-id="385cb-232">无法预先计算压缩索引的大小。</span><span class="sxs-lookup"><span data-stu-id="385cb-232">You cannot pre-calculate the size of a compressed index.</span></span>  
  
-   <span data-ttu-id="385cb-233">稀疏列</span><span class="sxs-lookup"><span data-stu-id="385cb-233">Sparse columns</span></span>  
  
     <span data-ttu-id="385cb-234">有关稀疏列的空间要求的信息，请参阅 [Use Sparse Columns](../tables/use-sparse-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="385cb-234">For information about the space requirements of sparse columns, see [Use Sparse Columns](../tables/use-sparse-columns.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="385cb-235">另请参阅</span><span class="sxs-lookup"><span data-stu-id="385cb-235">See Also</span></span>  
 <span data-ttu-id="385cb-236">[描述的聚集索引和非聚集索引](../indexes/clustered-and-nonclustered-indexes-described.md) </span><span class="sxs-lookup"><span data-stu-id="385cb-236">[Clustered and Nonclustered Indexes Described](../indexes/clustered-and-nonclustered-indexes-described.md) </span></span>  
 <span data-ttu-id="385cb-237">[估计表的大小](estimate-the-size-of-a-table.md) </span><span class="sxs-lookup"><span data-stu-id="385cb-237">[Estimate the Size of a Table](estimate-the-size-of-a-table.md) </span></span>  
 <span data-ttu-id="385cb-238">[创建聚集索引](../indexes/create-clustered-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="385cb-238">[Create Clustered Indexes](../indexes/create-clustered-indexes.md) </span></span>  
 <span data-ttu-id="385cb-239">[创建非聚集索引](../indexes/create-nonclustered-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="385cb-239">[Create Nonclustered Indexes](../indexes/create-nonclustered-indexes.md) </span></span>  
 <span data-ttu-id="385cb-240">[估计非聚集索引的大小](estimate-the-size-of-a-nonclustered-index.md) </span><span class="sxs-lookup"><span data-stu-id="385cb-240">[Estimate the Size of a Nonclustered Index](estimate-the-size-of-a-nonclustered-index.md) </span></span>  
 <span data-ttu-id="385cb-241">[估计堆的大小](estimate-the-size-of-a-heap.md) </span><span class="sxs-lookup"><span data-stu-id="385cb-241">[Estimate the Size of a Heap](estimate-the-size-of-a-heap.md) </span></span>  
 [<span data-ttu-id="385cb-242">估计数据库的大小</span><span class="sxs-lookup"><span data-stu-id="385cb-242">Estimate the Size of a Database</span></span>](estimate-the-size-of-a-database.md)  
  
  
