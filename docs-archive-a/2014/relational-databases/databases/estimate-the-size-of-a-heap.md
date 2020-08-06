---
title: 估计堆的大小 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- disk space [SQL Server], indexes
- estimating heap size
- size [SQL Server], heap
- space [SQL Server], indexes
- heaps
ms.assetid: 81fd5ec9-ce0f-4c2c-8ba0-6c483cea6c75
author: stevestein
ms.author: sstein
ms.openlocfilehash: f32432d07a9731d849ceb793daf209cfc505b0ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591364"
---
# <a name="estimate-the-size-of-a-heap"></a><span data-ttu-id="9a496-102">估计堆的大小</span><span class="sxs-lookup"><span data-stu-id="9a496-102">Estimate the Size of a Heap</span></span>
  <span data-ttu-id="9a496-103">可以使用以下步骤估计在堆中存储数据所需的空间量：</span><span class="sxs-lookup"><span data-stu-id="9a496-103">You can use the following steps to estimate the amount of space that is required to store data in a heap:</span></span>  
  
1.  <span data-ttu-id="9a496-104">指定表中显示的行数：</span><span class="sxs-lookup"><span data-stu-id="9a496-104">Specify the number of rows that will be present in the table:</span></span>  
  
     <span data-ttu-id="9a496-105">***Num_Rows***  = 表中的行数</span><span class="sxs-lookup"><span data-stu-id="9a496-105">***Num_Rows***  = number of rows in the table</span></span>  
  
2.  <span data-ttu-id="9a496-106">指定固定长度和可变长度列的数量，并计算存储所需的空间：</span><span class="sxs-lookup"><span data-stu-id="9a496-106">Specify the number of fixed-length and variable-length columns and calculate the space that is required for their storage:</span></span>  
  
     <span data-ttu-id="9a496-107">计算每组列在数据行中所占据的空间。</span><span class="sxs-lookup"><span data-stu-id="9a496-107">Calculate the space that each of these groups of columns occupies within the data row.</span></span> <span data-ttu-id="9a496-108">列的大小取决于数据类型和长度规定。</span><span class="sxs-lookup"><span data-stu-id="9a496-108">The size of a column depends on the data type and length specification.</span></span>  
  
     <span data-ttu-id="9a496-109">***Num_Cols***  = 总列数（固定长度和可变长度）</span><span class="sxs-lookup"><span data-stu-id="9a496-109">***Num_Cols***  = total number of columns (fixed-length and variable-length)</span></span>  
  
     <span data-ttu-id="9a496-110">***Fixed_Data_Size***  = 所有固定长度列的总字节大小</span><span class="sxs-lookup"><span data-stu-id="9a496-110">***Fixed_Data_Size***  = total byte size of all fixed-length columns</span></span>  
  
     <span data-ttu-id="9a496-111">***Num_Variable_Cols***  = 可变长度列数</span><span class="sxs-lookup"><span data-stu-id="9a496-111">***Num_Variable_Cols***  = number of variable-length columns</span></span>  
  
     <span data-ttu-id="9a496-112">Max_Var_Size  = 所有可变长度列的最大总字节大小</span><span class="sxs-lookup"><span data-stu-id="9a496-112">***Max_Var_Size***  = maximum total byte size of all variable-length columns</span></span>  
  
3.  <span data-ttu-id="9a496-113">保留行中称为 Null 位图的部分以管理列的为空性。</span><span class="sxs-lookup"><span data-stu-id="9a496-113">Part of the row, known as the null bitmap, is reserved to manage column nullability.</span></span> <span data-ttu-id="9a496-114">计算其大小：</span><span class="sxs-lookup"><span data-stu-id="9a496-114">Calculate its size:</span></span>  
  
     <span data-ttu-id="9a496-115">***Null_Bitmap***  = 2 + ((***Num_Cols*** + 7) / 8)</span><span class="sxs-lookup"><span data-stu-id="9a496-115">***Null_Bitmap***  = 2 + ((***Num_Cols*** + 7) / 8)</span></span>  
  
     <span data-ttu-id="9a496-116">只应使用该表达式的整数部分。</span><span class="sxs-lookup"><span data-stu-id="9a496-116">Only the integer part of this expression should be used.</span></span> <span data-ttu-id="9a496-117">而放弃所有余数。</span><span class="sxs-lookup"><span data-stu-id="9a496-117">Discard any remainder.</span></span>  
  
4.  <span data-ttu-id="9a496-118">计算可变长度数据的大小：</span><span class="sxs-lookup"><span data-stu-id="9a496-118">Calculate the variable-length data size:</span></span>  
  
     <span data-ttu-id="9a496-119">如果表中有可变长度列，请确定在行中存储这些列需使用的空间：</span><span class="sxs-lookup"><span data-stu-id="9a496-119">If there are variable-length columns in the table, determine how much space is used to store the columns within the row:</span></span>  
  
     <span data-ttu-id="9a496-120">***Variable_Data_Size***  = 2 + (***Num_Variable_Cols*** x 2) + ***Max_Var_Size***</span><span class="sxs-lookup"><span data-stu-id="9a496-120">***Variable_Data_Size***  = 2 + (***Num_Variable_Cols*** x 2) + ***Max_Var_Size***</span></span>  
  
     <span data-ttu-id="9a496-121">添加到***Max_Var_Size***中的字节用于跟踪每个可变长度列。</span><span class="sxs-lookup"><span data-stu-id="9a496-121">The bytes added to ***Max_Var_Size*** are for tracking each variable-length column.</span></span> <span data-ttu-id="9a496-122">此公式假设所有可变长度列均百分之百充满。</span><span class="sxs-lookup"><span data-stu-id="9a496-122">This formula assumes that all variable-length columns are 100 percent full.</span></span> <span data-ttu-id="9a496-123">如果预计可变长度列占用的存储空间比例较低，则可以按照该比例调整 ***Max_Var_Size*** 值，从而对整个表大小得出一个更准确的估计。</span><span class="sxs-lookup"><span data-stu-id="9a496-123">If you anticipate that a smaller percentage of the variable-length column storage space will be used, you can adjust the ***Max_Var_Size*** value by that percentage to yield a more accurate estimate of the overall table size.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9a496-124">您可以组合 `varchar`、`nvarchar`、`varbinary` 或 `sql_variant` 列，使得定义的表的总宽度超过 8,060 字节。</span><span class="sxs-lookup"><span data-stu-id="9a496-124">You can combine `varchar`, `nvarchar`, `varbinary`, or `sql_variant` columns that cause the total defined table width to exceed 8,060 bytes.</span></span> <span data-ttu-id="9a496-125">对于 `varchar` 、或列，这些列中每一列的长度仍必须在8000字节以内 `nvarchar,``varbinary` `sql_variant` 。</span><span class="sxs-lookup"><span data-stu-id="9a496-125">The length of each one of these columns must still fall within the limit of 8,000 bytes for a `varchar`, `nvarchar,``varbinary`, or `sql_variant` column.</span></span> <span data-ttu-id="9a496-126">但是，表中这些列的组合宽度可超过 8,060 字节的限制。</span><span class="sxs-lookup"><span data-stu-id="9a496-126">However, their combined widths may exceed the 8,060 byte limit in a table.</span></span>  
  
     <span data-ttu-id="9a496-127">如果没有可变长度列，请将 ***Variable_Data_Size*** 设置为 0。</span><span class="sxs-lookup"><span data-stu-id="9a496-127">If there are no variable-length columns, set ***Variable_Data_Size*** to 0.</span></span>  
  
5.  <span data-ttu-id="9a496-128">计算总的行大小：</span><span class="sxs-lookup"><span data-stu-id="9a496-128">Calculate the total row size:</span></span>  
  
     <span data-ttu-id="9a496-129">***Row_Size***  = ***Fixed_Data_Size*** + ***Variable_Data_Size*** + ***Null_Bitmap*** + 4</span><span class="sxs-lookup"><span data-stu-id="9a496-129">***Row_Size***  = ***Fixed_Data_Size*** + ***Variable_Data_Size*** + ***Null_Bitmap*** + 4</span></span>  
  
     <span data-ttu-id="9a496-130">公式中的值 4 是数据行的行标题开销。</span><span class="sxs-lookup"><span data-stu-id="9a496-130">The value 4 in the formula is the row header overhead of the data row.</span></span>  
  
6.  <span data-ttu-id="9a496-131">下一步，计算每页的行数（每页有 8096 个可用字节）：</span><span class="sxs-lookup"><span data-stu-id="9a496-131">Calculate the number of rows per page (8096 free bytes per page):</span></span>  
  
     <span data-ttu-id="9a496-132">***Rows_Per_Page***  = 8096 / (***Row_Size*** + 2)</span><span class="sxs-lookup"><span data-stu-id="9a496-132">***Rows_Per_Page***  = 8096 / (***Row_Size*** + 2)</span></span>  
  
     <span data-ttu-id="9a496-133">因为行不跨页，所以每页的行数应向下舍入到最接近的整数。</span><span class="sxs-lookup"><span data-stu-id="9a496-133">Because rows do not span pages, the number of rows per page should be rounded down to the nearest whole row.</span></span> <span data-ttu-id="9a496-134">公式中的数值 2 是计算行数时引入的行大小余量。</span><span class="sxs-lookup"><span data-stu-id="9a496-134">The value 2 in the formula is for the row's entry in the slot array of the page.</span></span>  
  
7.  <span data-ttu-id="9a496-135">计算存储所有行所需的页数：</span><span class="sxs-lookup"><span data-stu-id="9a496-135">Calculate the number of pages required to store all the rows:</span></span>  
  
     <span data-ttu-id="9a496-136">***Num_Pages***   = ***Num_Rows***  / ***Rows_Per_Page***</span><span class="sxs-lookup"><span data-stu-id="9a496-136">***Num_Pages***  = ***Num_Rows*** / ***Rows_Per_Page***</span></span>  
  
     <span data-ttu-id="9a496-137">估计的页数应向上舍入到最接近的整数。</span><span class="sxs-lookup"><span data-stu-id="9a496-137">The number of pages estimated should be rounded up to the nearest whole page.</span></span>  
  
8.  <span data-ttu-id="9a496-138">计算在堆中存储数据所需的空间量（每页的总字节为 8192）：</span><span class="sxs-lookup"><span data-stu-id="9a496-138">Calculate the amount of space that is required to store the data in the heap (8192 total bytes per page):</span></span>  
  
     <span data-ttu-id="9a496-139">堆大小 (字节) = 8192 x ***Num_Pages***</span><span class="sxs-lookup"><span data-stu-id="9a496-139">Heap size (bytes) = 8192 x ***Num_Pages***</span></span>  
  
 <span data-ttu-id="9a496-140">此计算不考虑以下因素：</span><span class="sxs-lookup"><span data-stu-id="9a496-140">This calculation does not consider the following:</span></span>  
  
-   <span data-ttu-id="9a496-141">分区</span><span class="sxs-lookup"><span data-stu-id="9a496-141">Partitioning</span></span>  
  
     <span data-ttu-id="9a496-142">分区的空间开销很小，但是计算复杂。</span><span class="sxs-lookup"><span data-stu-id="9a496-142">The space overhead from partitioning is minimal, but complex to calculate.</span></span> <span data-ttu-id="9a496-143">是否包括它并不重要。</span><span class="sxs-lookup"><span data-stu-id="9a496-143">It is not important to include.</span></span>  
  
-   <span data-ttu-id="9a496-144">分配页</span><span class="sxs-lookup"><span data-stu-id="9a496-144">Allocation pages</span></span>  
  
     <span data-ttu-id="9a496-145">至少有一个 IAM 页用于跟踪为堆分配的页，但是空间开销很小，并且没有算法可以精确地计算出要使用的 IAM 页数。</span><span class="sxs-lookup"><span data-stu-id="9a496-145">There is at least one IAM page used to track the pages allocated to a heap, but the space overhead is minimal and there is no algorithm to deterministically calculate exactly how many IAM pages will be used.</span></span>  
  
-   <span data-ttu-id="9a496-146">大型对象 (LOB) 值</span><span class="sxs-lookup"><span data-stu-id="9a496-146">Large object (LOB) values</span></span>  
  
     <span data-ttu-id="9a496-147">确定用于存储 LOB 数据类型 `varchar(max)` 、、 `varbinary(max)` `nvarchar(max)` 、 `text` 、 **ntextxml**和值的确切空间量的算法 `image` 非常复杂。</span><span class="sxs-lookup"><span data-stu-id="9a496-147">The algorithm to determine exactly how much space will be used to store the LOB data types `varchar(max)`, `varbinary(max)`, `nvarchar(max)`, `text`, **ntextxml**, and `image` values is complex.</span></span> <span data-ttu-id="9a496-148">只添加所期望的 LOB 值的平均大小就足够了，然后将其添加至总的堆大小中。</span><span class="sxs-lookup"><span data-stu-id="9a496-148">It is sufficient to just add the average size of the LOB values that are expected and add that to the total heap size.</span></span>  
  
-   <span data-ttu-id="9a496-149">压缩</span><span class="sxs-lookup"><span data-stu-id="9a496-149">Compression</span></span>  
  
     <span data-ttu-id="9a496-150">无法预先计算压缩堆的大小。</span><span class="sxs-lookup"><span data-stu-id="9a496-150">You cannot pre-calculate the size of a compressed heap.</span></span>  
  
-   <span data-ttu-id="9a496-151">稀疏列</span><span class="sxs-lookup"><span data-stu-id="9a496-151">Sparse columns</span></span>  
  
     <span data-ttu-id="9a496-152">有关稀疏列的空间要求的信息，请参阅 [Use Sparse Columns](../tables/use-sparse-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="9a496-152">For information about the space requirements of sparse columns, see [Use Sparse Columns](../tables/use-sparse-columns.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a496-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9a496-153">See Also</span></span>  
 <span data-ttu-id="9a496-154">[堆（没有聚集索引的表）](../indexes/heaps-tables-without-clustered-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="9a496-154">[Heaps &#40;Tables without Clustered Indexes&#41;](../indexes/heaps-tables-without-clustered-indexes.md) </span></span>  
 <span data-ttu-id="9a496-155">[描述的聚集索引和非聚集索引](../indexes/clustered-and-nonclustered-indexes-described.md) </span><span class="sxs-lookup"><span data-stu-id="9a496-155">[Clustered and Nonclustered Indexes Described](../indexes/clustered-and-nonclustered-indexes-described.md) </span></span>  
 <span data-ttu-id="9a496-156">[创建聚集索引](../indexes/create-clustered-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="9a496-156">[Create Clustered Indexes](../indexes/create-clustered-indexes.md) </span></span>  
 <span data-ttu-id="9a496-157">[创建非聚集索引](../indexes/create-nonclustered-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="9a496-157">[Create Nonclustered Indexes](../indexes/create-nonclustered-indexes.md) </span></span>  
 <span data-ttu-id="9a496-158">[估计表的大小](estimate-the-size-of-a-table.md) </span><span class="sxs-lookup"><span data-stu-id="9a496-158">[Estimate the Size of a Table](estimate-the-size-of-a-table.md) </span></span>  
 <span data-ttu-id="9a496-159">[估计聚集索引的大小](estimate-the-size-of-a-clustered-index.md) </span><span class="sxs-lookup"><span data-stu-id="9a496-159">[Estimate the Size of a Clustered Index](estimate-the-size-of-a-clustered-index.md) </span></span>  
 <span data-ttu-id="9a496-160">[估计非聚集索引的大小](estimate-the-size-of-a-nonclustered-index.md) </span><span class="sxs-lookup"><span data-stu-id="9a496-160">[Estimate the Size of a Nonclustered Index](estimate-the-size-of-a-nonclustered-index.md) </span></span>  
 [<span data-ttu-id="9a496-161">估计数据库的大小</span><span class="sxs-lookup"><span data-stu-id="9a496-161">Estimate the Size of a Database</span></span>](estimate-the-size-of-a-database.md)  
  
  
