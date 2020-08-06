---
title: 堆（没有聚集索引的表）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- heaps
ms.assetid: df5c4dfb-d372-4d0f-859a-a2d2533ee0d7
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2a39bac2e0352f2adc7749e980d5cc91044f8ab2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590802"
---
# <a name="heaps-tables-without-clustered-indexes"></a><span data-ttu-id="738bb-102">堆（没有聚集索引的表）</span><span class="sxs-lookup"><span data-stu-id="738bb-102">Heaps (Tables without Clustered Indexes)</span></span>
  <span data-ttu-id="738bb-103">堆是不含聚集索引的表。</span><span class="sxs-lookup"><span data-stu-id="738bb-103">A heap is a table without a clustered index.</span></span> <span data-ttu-id="738bb-104">可在存储为堆的表上创建一个或多个非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="738bb-104">One or more nonclustered indexes can be created on tables stored as a heap.</span></span> <span data-ttu-id="738bb-105">数据存储于堆中并且无需指定顺序。</span><span class="sxs-lookup"><span data-stu-id="738bb-105">Data is stored in the heap without specifying an order.</span></span> <span data-ttu-id="738bb-106">通常，数据最初以行插入表时的顺序存储，但 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 可能会在堆中四处移动数据，以便高效地存储行；因此，无法预测数据顺序。</span><span class="sxs-lookup"><span data-stu-id="738bb-106">Usually data is initially stored in the order in which is the rows are inserted into the table, but the [!INCLUDE[ssDE](../../includes/ssde-md.md)] can move data around in the heap to store the rows efficiently; so the data order cannot be predicted.</span></span> <span data-ttu-id="738bb-107">若要确保从堆返回的行的顺序，您必须使用 `ORDER BY` 子句。</span><span class="sxs-lookup"><span data-stu-id="738bb-107">To guarantee the order of rows returned from a heap, you must use the `ORDER BY` clause.</span></span> <span data-ttu-id="738bb-108">若要指定用于存储行的顺序，请对表创建聚集索引，以便表不是堆。</span><span class="sxs-lookup"><span data-stu-id="738bb-108">To specify the order for storage of the rows, create a clustered index on the table, so that the table is not a heap.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="738bb-109">有时候可能有必要将表保留为堆，而不是创建聚集索引，但高效率地使用堆需要较高的技能。</span><span class="sxs-lookup"><span data-stu-id="738bb-109">There are sometimes good reasons to leave a table as a heap instead of creating a clustered index, but using heaps effectively is an advanced skill.</span></span> <span data-ttu-id="738bb-110">大多数表应该具有仔细选择的聚集索引，除非有足够的理由将表保留为堆。</span><span class="sxs-lookup"><span data-stu-id="738bb-110">Most tables should have a carefully chosen clustered index unless a good reason exists for leaving the table as a heap.</span></span>  
  
## <a name="when-to-use-a-heap"></a><span data-ttu-id="738bb-111">何时使用堆</span><span class="sxs-lookup"><span data-stu-id="738bb-111">When to Use a Heap</span></span>  
 <span data-ttu-id="738bb-112">如果某个表是堆并且不具有任何非聚集索引，则必须检查整个表（表扫描）以便找到任何行。</span><span class="sxs-lookup"><span data-stu-id="738bb-112">If a table is a heap and does not have any nonclustered indexes, then the entire table must be examined (a table scan) to find any row.</span></span> <span data-ttu-id="738bb-113">这在表很小（例如公司 12 个地区办事处的列表）时是可接受的。</span><span class="sxs-lookup"><span data-stu-id="738bb-113">This can be acceptable when the table is tiny, such as a list of the 12 regional offices of a company.</span></span>  
  
 <span data-ttu-id="738bb-114">在将某个表存储为堆时，通过引用由文件号、数据页码和页上的槽构成的行标识符 (RID)，标识单独行。</span><span class="sxs-lookup"><span data-stu-id="738bb-114">When a table is stored as a heap, individual rows are identified by reference to a row identifier (RID) consisting of the file number, data page number, and slot on the page.</span></span> <span data-ttu-id="738bb-115">行 ID 是一个小且高效的结构。</span><span class="sxs-lookup"><span data-stu-id="738bb-115">The row id is a small and efficient structure.</span></span> <span data-ttu-id="738bb-116">有时候，在数据始终通过非聚集索引访问并且 RID 小于聚集索引键时，数据结构设计师会使用堆。</span><span class="sxs-lookup"><span data-stu-id="738bb-116">Sometimes data architects use heaps when data is always accessed through nonclustered indexes and the RID is smaller than a clustered index key.</span></span>  
  
## <a name="when-not-to-use-a-heap"></a><span data-ttu-id="738bb-117">何时不使用堆</span><span class="sxs-lookup"><span data-stu-id="738bb-117">When Not to Use a Heap</span></span>  
 <span data-ttu-id="738bb-118">在经常以排序后的顺序返回数据时，不要使用堆。</span><span class="sxs-lookup"><span data-stu-id="738bb-118">Do not use a heap when the data is frequently returned in a sorted order.</span></span> <span data-ttu-id="738bb-119">排序列上的聚集索引可以避免排序操作。</span><span class="sxs-lookup"><span data-stu-id="738bb-119">A clustered index on the sorting column could avoid the sorting operation.</span></span>  
  
 <span data-ttu-id="738bb-120">在数据经常组合在一起时，不要使用堆。</span><span class="sxs-lookup"><span data-stu-id="738bb-120">Do not use a heap when the data is frequently grouped together.</span></span> <span data-ttu-id="738bb-121">数据必须首先进行排序，然后才能分组，并且排序列上的聚集索引可以避免排序操作。</span><span class="sxs-lookup"><span data-stu-id="738bb-121">Data must be sorted before it is grouped, and a clustered index on the sorting column could avoid the sorting operation.</span></span>  
  
 <span data-ttu-id="738bb-122">在经常从表查询数据范围时，不要使用堆。</span><span class="sxs-lookup"><span data-stu-id="738bb-122">Do not use a heap when ranges of data are frequently queried from the table.</span></span>  <span data-ttu-id="738bb-123">范围列上的聚集索引将避免对整个堆进行排序。</span><span class="sxs-lookup"><span data-stu-id="738bb-123">A clustered index on the range column will avoid sorting the entire heap.</span></span>  
  
 <span data-ttu-id="738bb-124">在不存在非聚集索引并且表比较大时，不要使用堆。</span><span class="sxs-lookup"><span data-stu-id="738bb-124">Do not use a heap when there are no nonclustered indexes and the table is large.</span></span> <span data-ttu-id="738bb-125">在某一堆中，若要找到任何行，必须读取该堆的所有行。</span><span class="sxs-lookup"><span data-stu-id="738bb-125">In a heap, all rows of the heap must be read to find any row.</span></span>  
  
## <a name="managing-heaps"></a><span data-ttu-id="738bb-126">管理堆</span><span class="sxs-lookup"><span data-stu-id="738bb-126">Managing Heaps</span></span>  
 <span data-ttu-id="738bb-127">若要创建堆，请创建没有聚集索引的表。</span><span class="sxs-lookup"><span data-stu-id="738bb-127">To create a heap, create a table without a clustered index.</span></span> <span data-ttu-id="738bb-128">如果表已具有某一聚集索引，则删除该聚集索引以便将该表返回到某一堆。</span><span class="sxs-lookup"><span data-stu-id="738bb-128">If a table already has a clustered index, drop the clustered index to return the table to a heap.</span></span>  
  
 <span data-ttu-id="738bb-129">若要删除堆，请在该堆上创建聚集索引。</span><span class="sxs-lookup"><span data-stu-id="738bb-129">To remove a heap, create a clustered index on the heap.</span></span>  
  
 <span data-ttu-id="738bb-130">若要重新生成堆以便回收浪费的空间，请在该堆上创建一个聚集索引，然后删除该聚集索引。</span><span class="sxs-lookup"><span data-stu-id="738bb-130">To rebuild a heap to reclaim wasted space, create a clustered index on the heap, and then drop that clustered index.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="738bb-131">创建或删除聚集索引要求重写整个表。</span><span class="sxs-lookup"><span data-stu-id="738bb-131">Creating or dropping clustered indexes requires rewriting the entire table.</span></span> <span data-ttu-id="738bb-132">如果该表具有非聚集索引，则只要更改聚集索引，就必须全都重新创建所有非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="738bb-132">If the table has nonclustered indexes, all the nonclustered indexes must all be recreated whenever the clustered index is changed.</span></span> <span data-ttu-id="738bb-133">因此，从堆更改为聚集索引结构或反之可能占用大量时间，并且要求足够的磁盘空间以便对 tempdb 中的数据重新进行排序。</span><span class="sxs-lookup"><span data-stu-id="738bb-133">Therefore, changing from a heap to a clustered index structure or back can take a lot of time and require disk space for reordering data in tempdb.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="738bb-134">相关内容</span><span class="sxs-lookup"><span data-stu-id="738bb-134">Related Content</span></span>  
 [<span data-ttu-id="738bb-135">CREATE INDEX (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="738bb-135">CREATE INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-index-transact-sql)  
  
 [<span data-ttu-id="738bb-136">DROP INDEX (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="738bb-136">DROP INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-index-transact-sql)  
  
 [<span data-ttu-id="738bb-137">描述的聚集索引和非聚集索引</span><span class="sxs-lookup"><span data-stu-id="738bb-137">Clustered and Nonclustered Indexes Described</span></span>](clustered-and-nonclustered-indexes-described.md)  
  
  
