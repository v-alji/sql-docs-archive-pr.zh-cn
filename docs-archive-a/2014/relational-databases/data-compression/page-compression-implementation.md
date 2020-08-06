---
title: 页压缩的实现 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- page compression [Database Engine]
- compression [SQL Server], page
ms.assetid: 78c83277-1dbb-4e07-95bd-47b14d2b5cd4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e6edba79d1548d68e60f406d370abd5354a62fcb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589695"
---
# <a name="page-compression-implementation"></a><span data-ttu-id="14f29-102">页压缩的实现</span><span class="sxs-lookup"><span data-stu-id="14f29-102">Page Compression Implementation</span></span>
  <span data-ttu-id="14f29-103">本主题概述了 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 是如何实现页压缩的。</span><span class="sxs-lookup"><span data-stu-id="14f29-103">This topic summarizes how the [!INCLUDE[ssDE](../../includes/ssde-md.md)] implements page compression.</span></span> <span data-ttu-id="14f29-104">此摘要提供了有助于您规划数据所需存储空间的基本信息。</span><span class="sxs-lookup"><span data-stu-id="14f29-104">This summary provides basic information to help you plan the storage space that you need for your data.</span></span>  
  
 <span data-ttu-id="14f29-105">表、表分区、索引和索引分区的页压缩都是类似的。</span><span class="sxs-lookup"><span data-stu-id="14f29-105">Page compression is similar for tables, table partitions, indexes, and index partitions.</span></span> <span data-ttu-id="14f29-106">以下针对表的页压缩的说明同样适用于所有对象类型的页压缩。</span><span class="sxs-lookup"><span data-stu-id="14f29-106">The following description of page compression for a table applies equally to page compression for all object types.</span></span> <span data-ttu-id="14f29-107">以下示例压缩的是字符串，但对于其他数据类型而言，前缀压缩和字典压缩的原理都是相同的。</span><span class="sxs-lookup"><span data-stu-id="14f29-107">The following examples compress character strings, but both prefix and dictionary compression apply the same principles to other data types.</span></span>  
  
 <span data-ttu-id="14f29-108">使用页压缩压缩表和索引的叶级别的过程由按以下顺序进行的三个操作组成：</span><span class="sxs-lookup"><span data-stu-id="14f29-108">Compressing the leaf level of tables and indexes with page compression consists of three operations in the following order:</span></span>  
  
1.  <span data-ttu-id="14f29-109">行压缩</span><span class="sxs-lookup"><span data-stu-id="14f29-109">Row compression</span></span>  
  
2.  <span data-ttu-id="14f29-110">前缀压缩</span><span class="sxs-lookup"><span data-stu-id="14f29-110">Prefix compression</span></span>  
  
3.  <span data-ttu-id="14f29-111">字典压缩</span><span class="sxs-lookup"><span data-stu-id="14f29-111">Dictionary compression</span></span>  
  
 <span data-ttu-id="14f29-112">当使用页压缩时，将仅使用行压缩来压缩索引的非叶级别页。</span><span class="sxs-lookup"><span data-stu-id="14f29-112">When you use page compression, non-leaf-level pages of indexes are compressed by using only row compression.</span></span> <span data-ttu-id="14f29-113">有关行压缩的详细信息，请参阅 [Row Compression Implementation](../data-compression/row-compression-implementation.md)。</span><span class="sxs-lookup"><span data-stu-id="14f29-113">For more information about row compression, see [Row Compression Implementation](../data-compression/row-compression-implementation.md).</span></span>  
  
## <a name="prefix-compression"></a><span data-ttu-id="14f29-114">前缀压缩</span><span class="sxs-lookup"><span data-stu-id="14f29-114">Prefix Compression</span></span>  
 <span data-ttu-id="14f29-115">对于要压缩的每一页，前缀压缩采用以下步骤：</span><span class="sxs-lookup"><span data-stu-id="14f29-115">For each page that is being compressed, prefix compression uses the following steps:</span></span>  
  
1.  <span data-ttu-id="14f29-116">对于每一列，将确定一个值，此值可用于减少每一列中的值的存储空间。</span><span class="sxs-lookup"><span data-stu-id="14f29-116">For each column, a value is identified that can be used to reduce the storage space for the values in each column.</span></span>  
  
2.  <span data-ttu-id="14f29-117">将创建表示每一列的前缀值的行，并将其存储在紧随页头之后的压缩信息 (CI) 结构中。</span><span class="sxs-lookup"><span data-stu-id="14f29-117">A row that represents the prefix values for each column is created and stored in the compression information (CI) structure that immediately follows the page header.</span></span>  
  
3.  <span data-ttu-id="14f29-118">列中重复的前缀值将由指向对应前缀的引用进行替换。</span><span class="sxs-lookup"><span data-stu-id="14f29-118">The repeated prefix values in the column are replaced by a reference to the corresponding prefix.</span></span> <span data-ttu-id="14f29-119">如果行中的值与所选前缀值并不完全匹配，则仍会指示存在部分匹配。</span><span class="sxs-lookup"><span data-stu-id="14f29-119">If the value in a row does not exactly match the selected prefix value, a partial match can still be indicated.</span></span>  
  
 <span data-ttu-id="14f29-120">下图显示了前缀压缩之前表的一个示例页。</span><span class="sxs-lookup"><span data-stu-id="14f29-120">The following illustration shows a sample page of a table before prefix compression.</span></span>  
  
 <span data-ttu-id="14f29-121">![前缀压缩之前的页](../media/skt-tblcompression1c.gif "前缀压缩之前的页")</span><span class="sxs-lookup"><span data-stu-id="14f29-121">![Page before prefix compression](../media/skt-tblcompression1c.gif "Page before prefix compression")</span></span>  
  
 <span data-ttu-id="14f29-122">下图显示的是同一页在前缀压缩之后的样子。</span><span class="sxs-lookup"><span data-stu-id="14f29-122">The following illustration shows the same page after prefix compression.</span></span> <span data-ttu-id="14f29-123">前缀移至页头，列值更改为指向前缀的引用。</span><span class="sxs-lookup"><span data-stu-id="14f29-123">The prefix is moved to the header, and the column values are changed to references to the prefix.</span></span>  
  
 <span data-ttu-id="14f29-124">![前缀压缩之后的页](../media/tblcompression2.gif "前缀压缩之后的页")</span><span class="sxs-lookup"><span data-stu-id="14f29-124">![Page after prefix compression](../media/tblcompression2.gif "Page after prefix compression")</span></span>  
  
 <span data-ttu-id="14f29-125">在第一行的第一列，值 4b 指示为该行显示前缀的前四个字符 (aaab) 和字符 b。</span><span class="sxs-lookup"><span data-stu-id="14f29-125">In the first column of the first row, the value 4b indicates that the first four characters of the prefix (aaab) are present for that row, and also the character b.</span></span> <span data-ttu-id="14f29-126">这样的话，结果值就是 aaabb，这是原始值。</span><span class="sxs-lookup"><span data-stu-id="14f29-126">This makes the resultant value aaabb, which is the original value.</span></span>  
  
## <a name="dictionary-compression"></a><span data-ttu-id="14f29-127">字典压缩</span><span class="sxs-lookup"><span data-stu-id="14f29-127">Dictionary Compression</span></span>  
 <span data-ttu-id="14f29-128">前缀压缩完成后，将应用字典压缩。</span><span class="sxs-lookup"><span data-stu-id="14f29-128">After prefix compression has been completed, dictionary compression is applied.</span></span> <span data-ttu-id="14f29-129">字典压缩搜索页面上任意位置的重复值，然后将它们存储在 CI 区域中。</span><span class="sxs-lookup"><span data-stu-id="14f29-129">Dictionary compression searches for repeated values anywhere on the page, and stores them in the CI area.</span></span> <span data-ttu-id="14f29-130">与前缀压缩不同，字典压缩不局限于一列。</span><span class="sxs-lookup"><span data-stu-id="14f29-130">Unlike prefix compression, dictionary compression is not restricted to one column.</span></span> <span data-ttu-id="14f29-131">字典压缩可以替换页面上任意位置出现的重复值。</span><span class="sxs-lookup"><span data-stu-id="14f29-131">Dictionary compression can replace repeated values that occur anywhere on a page.</span></span> <span data-ttu-id="14f29-132">下图显示的是同一页在字典压缩之后的样子。</span><span class="sxs-lookup"><span data-stu-id="14f29-132">The following illustration shows the same page after dictionary compression.</span></span>  
  
 <span data-ttu-id="14f29-133">![字典压缩之后的页](../media/tblcompression3.gif "字典压缩之后的页")</span><span class="sxs-lookup"><span data-stu-id="14f29-133">![Page after dictionary compression](../media/tblcompression3.gif "Page after dictionary compression")</span></span>  
  
 <span data-ttu-id="14f29-134">请注意，值 4b 已由页的其他列引用。</span><span class="sxs-lookup"><span data-stu-id="14f29-134">Note that the value 4b has been referenced from different columns of the page.</span></span>  
  
## <a name="when-page-compression-occurs"></a><span data-ttu-id="14f29-135">进行页压缩时</span><span class="sxs-lookup"><span data-stu-id="14f29-135">When Page Compression Occurs</span></span>  
 <span data-ttu-id="14f29-136">当创建具有页压缩的新表时，不会进行压缩。</span><span class="sxs-lookup"><span data-stu-id="14f29-136">When a new table is created that has page compression, no compression occurs.</span></span> <span data-ttu-id="14f29-137">但是，表的元数据会指示应使用页压缩。</span><span class="sxs-lookup"><span data-stu-id="14f29-137">However, the metadata for the table indicates that page compression should be used.</span></span> <span data-ttu-id="14f29-138">当将数据添加到第一个数据页时，会对数据进行行压缩。</span><span class="sxs-lookup"><span data-stu-id="14f29-138">As data is added to the first data page, data is row-compressed.</span></span> <span data-ttu-id="14f29-139">因为此页未满，所以无法通过页压缩获得任何益处。</span><span class="sxs-lookup"><span data-stu-id="14f29-139">Because the page is not full, no benefit is gained from page compression.</span></span> <span data-ttu-id="14f29-140">如果页已满，则添加下一行将引导页压缩操作。</span><span class="sxs-lookup"><span data-stu-id="14f29-140">When the page is full, the next row to be added initiates the page compression operation.</span></span> <span data-ttu-id="14f29-141">将查看整个页；计算每一列以进行前缀压缩，然后计算所有列以进行字典压缩。</span><span class="sxs-lookup"><span data-stu-id="14f29-141">The whole page is reviewed; each column is evaluated for prefix compression, and then all columns are evaluated for dictionary compression.</span></span> <span data-ttu-id="14f29-142">如果页压缩已在页上为要添加的行创建了足够的空间，则添加该行，并对数据进行行压缩和页压缩。</span><span class="sxs-lookup"><span data-stu-id="14f29-142">If page compression has created enough room on the page for an additional row, the row is added, and the data is both row- and page-compressed.</span></span> <span data-ttu-id="14f29-143">如果通过页压缩获得的空间减去 CI 结构所需空间之后剩余的空间并不充足，则不会对此页使用页压缩。</span><span class="sxs-lookup"><span data-stu-id="14f29-143">If the space gained by page compression minus the space that is required for the CI structure is not significant, page compression is not used for that page.</span></span> <span data-ttu-id="14f29-144">以后，行将添加到新页上，如果新页中也无法再容纳更多的行，则将再向表中添加一个新页。</span><span class="sxs-lookup"><span data-stu-id="14f29-144">Future rows either fit onto the new page or, if they do not fit, a new page is added to the table.</span></span> <span data-ttu-id="14f29-145">与第一页类似，新页最初也不进行页压缩。</span><span class="sxs-lookup"><span data-stu-id="14f29-145">Similar to the first page, the new page is not at first page-compressed.</span></span>  
  
 <span data-ttu-id="14f29-146">当包含数据的现有表转换为页压缩时，将重新生成和计算每一页。</span><span class="sxs-lookup"><span data-stu-id="14f29-146">When an existing table that contains data is converted to page compression, each page is rebuilt and evaluated.</span></span> <span data-ttu-id="14f29-147">重新生成所有页会导致重新生成表、索引或分区。</span><span class="sxs-lookup"><span data-stu-id="14f29-147">Rebuilding all the pages causes the rebuilding of the table, index, or partition.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14f29-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="14f29-148">See Also</span></span>  
 <span data-ttu-id="14f29-149">[数据压缩](data-compression.md) </span><span class="sxs-lookup"><span data-stu-id="14f29-149">[Data Compression](data-compression.md) </span></span>  
 [<span data-ttu-id="14f29-150">行压缩的实现</span><span class="sxs-lookup"><span data-stu-id="14f29-150">Row Compression Implementation</span></span>](row-compression-implementation.md)  
  
  
