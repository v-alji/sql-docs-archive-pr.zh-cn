---
title: SQL Server 索引设计指南 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: b856ee9a-49e7-4fab-a88d-48a633fce269
author: rothja
ms.author: jroth
ms.openlocfilehash: 1f5ad72413fe71004fb1c5f125969b984db815d3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577944"
---
# <a name="sql-server-index-design-guide"></a><span data-ttu-id="05d9d-102">SQL Server 索引设计指南</span><span class="sxs-lookup"><span data-stu-id="05d9d-102">SQL Server Index Design Guide</span></span>

  <span data-ttu-id="05d9d-103">索引设计不佳和缺少索引是提高数据库和应用程序性能的主要障碍。</span><span class="sxs-lookup"><span data-stu-id="05d9d-103">Poorly designed indexes and a lack of indexes are primary sources of database application bottlenecks.</span></span> <span data-ttu-id="05d9d-104">设计高效的索引对于获得良好的数据库和应用程序性能极为重要。</span><span class="sxs-lookup"><span data-stu-id="05d9d-104">Designing efficient indexes is paramount to achieving good database and application performance.</span></span> <span data-ttu-id="05d9d-105">本 SQL Server 索引设计指南包含帮助您设计高效索引以满足应用程序需要的信息和最佳实践。</span><span class="sxs-lookup"><span data-stu-id="05d9d-105">This SQL Server index design guide contains information and best practices to help you design effective indexes to meet the needs of your application.</span></span>  
  
<span data-ttu-id="05d9d-106">**适用**于： [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] 到（除非另有 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 说明）。</span><span class="sxs-lookup"><span data-stu-id="05d9d-106">**Applies to**: [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] through [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] unless noted otherwise.</span></span>  
  
 <span data-ttu-id="05d9d-107">本指南假定读者对 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]中提供的索引类型有一般了解。</span><span class="sxs-lookup"><span data-stu-id="05d9d-107">This guide assumes the reader has a general understanding of the index types available in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="05d9d-108">有关索引类型的一般说明，请参阅 [索引类型](../relational-databases/indexes/indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="05d9d-108">For a general description of index types, see [Index Types](../relational-databases/indexes/indexes.md).</span></span>  
  
##  <a name="in-this-guide"></a><a name="Top"></a><span data-ttu-id="05d9d-109">本指南中</span><span class="sxs-lookup"><span data-stu-id="05d9d-109">In This Guide</span></span>  

 [<span data-ttu-id="05d9d-110">索引设计基础知识</span><span class="sxs-lookup"><span data-stu-id="05d9d-110">Index Design Basics</span></span>](#Basics)  
  
 [<span data-ttu-id="05d9d-111">常规索引设计指南</span><span class="sxs-lookup"><span data-stu-id="05d9d-111">General Index Design Guidelines</span></span>](#General_Design)  
  
 [<span data-ttu-id="05d9d-112">聚集索引设计指南</span><span class="sxs-lookup"><span data-stu-id="05d9d-112">Clustered Index Design Guidelines</span></span>](#Clustered)  
  
 [<span data-ttu-id="05d9d-113">非聚集索引设计指南</span><span class="sxs-lookup"><span data-stu-id="05d9d-113">Nonclustered Index Design Guidelines</span></span>](#Nonclustered)  
  
 [<span data-ttu-id="05d9d-114">唯一索引设计指南</span><span class="sxs-lookup"><span data-stu-id="05d9d-114">Unique Index Design Guidelines</span></span>](#Unique)  
  
 [<span data-ttu-id="05d9d-115">筛选索引设计指南</span><span class="sxs-lookup"><span data-stu-id="05d9d-115">Filtered Index Design Guidelines</span></span>](#Filtered)  
  
 [<span data-ttu-id="05d9d-116">其他阅读材料</span><span class="sxs-lookup"><span data-stu-id="05d9d-116">Additional Reading</span></span>](#Additional_Reading)  
  
##  <a name="index-design-basics"></a><a name="Basics"></a> <span data-ttu-id="05d9d-117">索引设计基础知识</span><span class="sxs-lookup"><span data-stu-id="05d9d-117">Index Design Basics</span></span>  

 <span data-ttu-id="05d9d-118">索引是与表或视图关联的磁盘上结构，可以加快从表或视图中检索行的速度。</span><span class="sxs-lookup"><span data-stu-id="05d9d-118">An index is an on-disk structure associated with a table or view that speeds retrieval of rows from the table or view.</span></span> <span data-ttu-id="05d9d-119">索引包含由表或视图中的一列或多列生成的键。</span><span class="sxs-lookup"><span data-stu-id="05d9d-119">An index contains keys built from one or more columns in the table or view.</span></span> <span data-ttu-id="05d9d-120">这些键存储在一个结构（B 树）中，使 SQL Server 可以快速高效地找到与键值关联的行。</span><span class="sxs-lookup"><span data-stu-id="05d9d-120">These keys are stored in a structure (B-tree) that enables SQL Server to find the row or rows associated with the key values quickly and efficiently.</span></span>  
  
 <span data-ttu-id="05d9d-121">为数据库及其工作负荷选择正确的索引是一项需要在查询速度与更新所需开销之间取得平衡的复杂任务。</span><span class="sxs-lookup"><span data-stu-id="05d9d-121">The selection of the right indexes for a database and its workload is a complex balancing act between query speed and update cost.</span></span> <span data-ttu-id="05d9d-122">如果索引较窄，或者说索引关键字中只有很少的几列，则需要的磁盘空间和维护开销都较少。</span><span class="sxs-lookup"><span data-stu-id="05d9d-122">Narrow indexes, or indexes with few columns in the index key, require less disk space and maintenance overhead.</span></span> <span data-ttu-id="05d9d-123">而另一方面，宽索引可覆盖更多的查询。</span><span class="sxs-lookup"><span data-stu-id="05d9d-123">Wide indexes, on the other hand, cover more queries.</span></span> <span data-ttu-id="05d9d-124">您可能需要试验若干不同的设计，才能找到最有效的索引。</span><span class="sxs-lookup"><span data-stu-id="05d9d-124">You may have to experiment with several different designs before finding the most efficient index.</span></span> <span data-ttu-id="05d9d-125">可以添加、修改和删除索引而不影响数据库架构或应用程序设计。</span><span class="sxs-lookup"><span data-stu-id="05d9d-125">Indexes can be added, modified, and dropped without affecting the database schema or application design.</span></span> <span data-ttu-id="05d9d-126">因此，应试验多个不同的索引而无需犹豫。</span><span class="sxs-lookup"><span data-stu-id="05d9d-126">Therefore, you should not hesitate to experiment with different indexes.</span></span>  
  
 <span data-ttu-id="05d9d-127">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 中的查询优化器可在大多数情况下可靠地选择最高效的索引。</span><span class="sxs-lookup"><span data-stu-id="05d9d-127">The query optimizer in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] reliably chooses the most effective index in the vast majority of cases.</span></span> <span data-ttu-id="05d9d-128">总体索引设计策略应为查询优化器提供可供选择的多个索引，并依赖查询优化器做出正确的决定。</span><span class="sxs-lookup"><span data-stu-id="05d9d-128">Your overall index design strategy should provide a variety of indexes for the query optimizer to choose from and trust it to make the right decision.</span></span> <span data-ttu-id="05d9d-129">这在多种情况下可减少分析时间并获得良好的性能。</span><span class="sxs-lookup"><span data-stu-id="05d9d-129">This reduces analysis time and produces good performance over a variety of situations.</span></span> <span data-ttu-id="05d9d-130">若要查看查询优化器对特定查询使用的索引，请在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中的“查询”菜单上选择“包括实际的执行计划”。</span><span class="sxs-lookup"><span data-stu-id="05d9d-130">To see which indexes the query optimizer uses for a specific query, in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], on the **Query** menu, select **Include Actual Execution Plan**.</span></span>  
  
 <span data-ttu-id="05d9d-131">不要总是将索引的使用等同于良好的性能，或者将良好的性能等同于索引的高效使用。</span><span class="sxs-lookup"><span data-stu-id="05d9d-131">Do not always equate index usage with good performance, and good performance with efficient index use.</span></span> <span data-ttu-id="05d9d-132">如果只要使用索引就能获得最佳性能，那查询优化器的工作就简单了。</span><span class="sxs-lookup"><span data-stu-id="05d9d-132">If using an index always helped produce the best performance, the job of the query optimizer would be simple.</span></span> <span data-ttu-id="05d9d-133">但事实上，不正确的索引选择并不能获得最佳性能。</span><span class="sxs-lookup"><span data-stu-id="05d9d-133">In reality, an incorrect index choice can cause less than optimal performance.</span></span> <span data-ttu-id="05d9d-134">因此，查询优化器的任务是只在索引或索引组合能提高性能时才选择它，而在索引检索有碍性能时则避免使用它。</span><span class="sxs-lookup"><span data-stu-id="05d9d-134">Therefore, the task of the query optimizer is to select an index, or combination of indexes, only when it will improve performance, and to avoid indexed retrieval when it will hinder performance.</span></span>  
  
### <a name="index-design-tasks"></a><span data-ttu-id="05d9d-135">索引设计任务</span><span class="sxs-lookup"><span data-stu-id="05d9d-135">Index Design Tasks</span></span>  

 <span data-ttu-id="05d9d-136">建议的索引设计策略包括以下任务：</span><span class="sxs-lookup"><span data-stu-id="05d9d-136">The follow tasks make up our recommended strategy for designing indexes:</span></span>  
  
1.  <span data-ttu-id="05d9d-137">了解数据库本身的特征。</span><span class="sxs-lookup"><span data-stu-id="05d9d-137">Understand the characteristics of the database itself.</span></span> <span data-ttu-id="05d9d-138">例如，它是频繁修改数据的联机事务处理 (OLTP) 数据库，还是主要包含只读数据且必须快速处理大型数据集的决策支持系统 (DSS) 或数据仓库 (OLAP) 数据库？</span><span class="sxs-lookup"><span data-stu-id="05d9d-138">For example, is it an online transaction processing (OLTP) database with frequent data modifications, or a Decision Support System (DSS) or data warehousing (OLAP) database that contains primarily read-only data and must process very large data sets quickly.</span></span> <span data-ttu-id="05d9d-139">在 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]中， *xVelocity 内存优化的列存储* 索引尤其适用于典型的数据仓库数据集。</span><span class="sxs-lookup"><span data-stu-id="05d9d-139">In [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], *xVelocity memory optimized columnstore* index is especially appropriate for typical data warehousing data sets.</span></span> <span data-ttu-id="05d9d-140">列存储索引可以通过为常见数据仓库查询（如筛选、聚合、分组和星型联接查询）提供更快的性能，以转变用户的数据仓库体验。</span><span class="sxs-lookup"><span data-stu-id="05d9d-140">Columnstore indexes can transform the data warehousing experience for users by enabling faster performance for common data warehousing queries such as filtering, aggregating, grouping, and star-join queries.</span></span> <span data-ttu-id="05d9d-141">有关详细信息，请参阅[描述的列存储索引](../relational-databases/indexes/columnstore-indexes-described.md)。</span><span class="sxs-lookup"><span data-stu-id="05d9d-141">For more information, see [Columnstore Indexes Described](../relational-databases/indexes/columnstore-indexes-described.md).</span></span>  
  
2.  <span data-ttu-id="05d9d-142">了解最常用的查询的特征。</span><span class="sxs-lookup"><span data-stu-id="05d9d-142">Understand the characteristics of the most frequently used queries.</span></span> <span data-ttu-id="05d9d-143">例如，了解到最常用的查询联接两个或多个表将有助于决定要使用的最佳索引类型。</span><span class="sxs-lookup"><span data-stu-id="05d9d-143">For example, knowing that a frequently used query joins two or more tables will help you determine the best type of indexes to use.</span></span>  
  
3.  <span data-ttu-id="05d9d-144">了解查询中使用的列的特征。</span><span class="sxs-lookup"><span data-stu-id="05d9d-144">Understand the characteristics of the columns used in the queries.</span></span> <span data-ttu-id="05d9d-145">例如，某个索引对于含有整数数据类型同时还是唯一的或非空的列是理想索引。</span><span class="sxs-lookup"><span data-stu-id="05d9d-145">For example, an index is ideal for columns that have an integer data type and are also unique or nonnull columns.</span></span> <span data-ttu-id="05d9d-146">对于具有定义完善的数据子集的列，您可以在 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] 和更高版本中使用筛选索引。</span><span class="sxs-lookup"><span data-stu-id="05d9d-146">For columns that have well-defined subsets of data, you can use a filtered index in [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] and higher versions.</span></span> <span data-ttu-id="05d9d-147">有关详细信息，请参阅本指南中的 [筛选索引设计指南](#Filtered) 。</span><span class="sxs-lookup"><span data-stu-id="05d9d-147">For more information, see [Filtered Index Design Guidelines](#Filtered) in this guide.</span></span>  
  
4.  <span data-ttu-id="05d9d-148">确定哪些索引选项可在创建或维护索引时提高性能。</span><span class="sxs-lookup"><span data-stu-id="05d9d-148">Determine which index options might enhance performance when the index is created or maintained.</span></span> <span data-ttu-id="05d9d-149">例如，对现有某个大型表创建聚集索引将会受益于 ONLINE 索引选项。</span><span class="sxs-lookup"><span data-stu-id="05d9d-149">For example, creating a clustered index on an existing large table would benefit from the ONLINE index option.</span></span> <span data-ttu-id="05d9d-150">ONLINE 选项允许在创建索引或重新生成索引时继续对基础数据执行并发活动。</span><span class="sxs-lookup"><span data-stu-id="05d9d-150">The ONLINE option allows for concurrent activity on the underlying data to continue while the index is being created or rebuilt.</span></span> <span data-ttu-id="05d9d-151">有关详细信息，请参阅 [设置索引选项](../relational-databases/indexes/set-index-options.md)。</span><span class="sxs-lookup"><span data-stu-id="05d9d-151">For more information, see [Set Index Options](../relational-databases/indexes/set-index-options.md).</span></span>  
  
5.  <span data-ttu-id="05d9d-152">确定索引的最佳存储位置。</span><span class="sxs-lookup"><span data-stu-id="05d9d-152">Determine the optimal storage location for the index.</span></span> <span data-ttu-id="05d9d-153">非聚集索引可以与基础表存储在同一个文件组中，也可以存储在不同的文件组中。</span><span class="sxs-lookup"><span data-stu-id="05d9d-153">A nonclustered index can be stored in the same filegroup as the underlying table, or on a different filegroup.</span></span> <span data-ttu-id="05d9d-154">索引的存储位置可通过提高磁盘 I/O 性能来提高查询性能。</span><span class="sxs-lookup"><span data-stu-id="05d9d-154">The storage location of indexes can improve query performance by increasing disk I/O performance.</span></span> <span data-ttu-id="05d9d-155">例如，将非聚集索引存储在表文件组所在磁盘以外的某个磁盘上的一个文件组中可以提高性能，因为可以同时读取多个磁盘。</span><span class="sxs-lookup"><span data-stu-id="05d9d-155">For example, storing a nonclustered index on a filegroup that is on a different disk than the table filegroup can improve performance because multiple disks can be read at the same time.</span></span>  
  
     <span data-ttu-id="05d9d-156">或者，聚集索引和非聚集索引也可以使用跨越多个文件组的分区方案。</span><span class="sxs-lookup"><span data-stu-id="05d9d-156">Alternatively, clustered and nonclustered indexes can use a partition scheme across multiple filegroups.</span></span> <span data-ttu-id="05d9d-157">在维护整个集合的完整性时，使用分区可以快速而有效地访问或管理数据子集，从而使大型表或索引更易于管理。</span><span class="sxs-lookup"><span data-stu-id="05d9d-157">Partitioning makes large tables or indexes more manageable by letting you access or manage subsets of data quickly and efficiently, while maintaining the integrity of the overall collection.</span></span> <span data-ttu-id="05d9d-158">有关详细信息，请参阅 [Partitioned Tables and Indexes](../relational-databases/partitions/partitioned-tables-and-indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="05d9d-158">For more information, see [Partitioned Tables and Indexes](../relational-databases/partitions/partitioned-tables-and-indexes.md).</span></span> <span data-ttu-id="05d9d-159">在考虑分区时，应确定是否应对齐索引，即，是按实质上与表相同的方式进行分区，还是单独分区。</span><span class="sxs-lookup"><span data-stu-id="05d9d-159">When you consider partitioning, determine whether the index should be aligned, that is, partitioned in essentially the same manner as the table, or partitioned independently.</span></span>  
  
##  <a name="general-index-design-guidelines"></a><a name="General_Design"></a> <span data-ttu-id="05d9d-160">常规索引设计指南</span><span class="sxs-lookup"><span data-stu-id="05d9d-160">General Index Design Guidelines</span></span>  

 <span data-ttu-id="05d9d-161">经验丰富的数据库管理员能够设计出好的索引集，但是，即使对于不特别复杂的数据库和工作负荷来说，这项任务也十分复杂、耗时和易于出错。</span><span class="sxs-lookup"><span data-stu-id="05d9d-161">Experienced database administrators can design a good set of indexes, but this task is very complex, time-consuming, and error-prone even for moderately complex databases and workloads.</span></span> <span data-ttu-id="05d9d-162">了解数据库、查询和数据列的特征可以帮助您设计出最佳索引。</span><span class="sxs-lookup"><span data-stu-id="05d9d-162">Understanding the characteristics of your database, queries, and data columns can help you design optimal indexes.</span></span>  
  
### <a name="database-considerations"></a><span data-ttu-id="05d9d-163">数据库注意事项</span><span class="sxs-lookup"><span data-stu-id="05d9d-163">Database Considerations</span></span>  

 <span data-ttu-id="05d9d-164">设计索引时，应考虑以下数据库准则：</span><span class="sxs-lookup"><span data-stu-id="05d9d-164">When you design an index, consider the following database guidelines:</span></span>  
  
-   <span data-ttu-id="05d9d-165">对表编制大量索引会影响 INSERT、UPDATE、DELETE 和 MERGE 语句的性能，因为当表中的数据更改时，所有索引都须进行适当的调整。</span><span class="sxs-lookup"><span data-stu-id="05d9d-165">Large numbers of indexes on a table affect the performance of INSERT, UPDATE, DELETE, and MERGE statements because all indexes must be adjusted appropriately as data in the table changes.</span></span> <span data-ttu-id="05d9d-166">例如，如果某个列在几个索引中使用且您执行修改该列数据的 UPDATE 语句，则必须更新包含该列的每个索引以及基础的基表（堆或聚集索引）中的该列。</span><span class="sxs-lookup"><span data-stu-id="05d9d-166">For example, if a column is used in several indexes and you execute an UPDATE statement that modifies that column's data, each index that contains that column must be updated as well as the column in the underlying base table (heap or clustered index).</span></span>  
  
    -   <span data-ttu-id="05d9d-167">避免对经常更新的表进行过多的索引，并且索引应保持较窄，就是说，列要尽可能少。</span><span class="sxs-lookup"><span data-stu-id="05d9d-167">Avoid over-indexing heavily updated tables and keep indexes narrow, that is, with as few columns as possible.</span></span>  
  
    -   <span data-ttu-id="05d9d-168">使用多个索引可以提高更新少而数据量大的查询的性能。</span><span class="sxs-lookup"><span data-stu-id="05d9d-168">Use many indexes to improve query performance on tables with low update requirements, but large volumes of data.</span></span> <span data-ttu-id="05d9d-169">大量索引可以提高不修改数据的查询（例如 SELECT 语句）的性能，因为查询优化器有更多的索引可供选择，从而可以确定最快的访问方法。</span><span class="sxs-lookup"><span data-stu-id="05d9d-169">Large numbers of indexes can help the performance of queries that do not modify data, such as SELECT statements, because the query optimizer has more indexes to choose from to determine the fastest access method.</span></span>  
  
-   <span data-ttu-id="05d9d-170">对小表进行索引可能不会产生优化效果，因为查询优化器在遍历用于搜索数据的索引时，花费的时间可能比执行简单的表扫描还长。</span><span class="sxs-lookup"><span data-stu-id="05d9d-170">Indexing small tables may not be optimal because it can take the query optimizer longer to traverse the index searching for data than to perform a simple table scan.</span></span> <span data-ttu-id="05d9d-171">因此，小表的索引可能从来不用，但仍必须在表中的数据更改时进行维护。</span><span class="sxs-lookup"><span data-stu-id="05d9d-171">Therefore, indexes on small tables might never be used, but must still be maintained as data in the table changes.</span></span>  
  
-   <span data-ttu-id="05d9d-172">视图包含聚合、表联接或聚合和联接的组合时，视图的索引可以显著地提升性能。</span><span class="sxs-lookup"><span data-stu-id="05d9d-172">Indexes on views can provide significant performance gains when the view contains aggregations, table joins, or a combination of aggregations and joins.</span></span> <span data-ttu-id="05d9d-173">若要使查询优化器使用视图，并不一定非要在查询中显式引用该视图。</span><span class="sxs-lookup"><span data-stu-id="05d9d-173">The view does not have to be explicitly referenced in the query for the query optimizer to use it.</span></span>  
  
-   <span data-ttu-id="05d9d-174">使用数据库引擎优化顾问来分析数据库并生成索引建议。</span><span class="sxs-lookup"><span data-stu-id="05d9d-174">Use the Database Engine Tuning Advisor to analyze your database and make index recommendations.</span></span> <span data-ttu-id="05d9d-175">有关详细信息，请参阅 [Database Engine Tuning Advisor](../relational-databases/performance/database-engine-tuning-advisor.md)。</span><span class="sxs-lookup"><span data-stu-id="05d9d-175">For more information, see [Database Engine Tuning Advisor](../relational-databases/performance/database-engine-tuning-advisor.md).</span></span>  
  
### <a name="query-considerations"></a><span data-ttu-id="05d9d-176">查询注意事项</span><span class="sxs-lookup"><span data-stu-id="05d9d-176">Query Considerations</span></span>  

 <span data-ttu-id="05d9d-177">设计索引时，应考虑以下查询准则：</span><span class="sxs-lookup"><span data-stu-id="05d9d-177">When you design an index, consider the following query guidelines:</span></span>  
  
-   <span data-ttu-id="05d9d-178">为经常用于查询中的谓词和联接条件的列创建非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="05d9d-178">Create nonclustered indexes on the columns that are frequently used in predicates and join conditions in queries.</span></span> <span data-ttu-id="05d9d-179">但是，应避免添加不必要的列。</span><span class="sxs-lookup"><span data-stu-id="05d9d-179">However, you should avoid adding unnecessary columns.</span></span> <span data-ttu-id="05d9d-180">添加太多索引列可能对磁盘空间和索引维护性能产生负面影响。</span><span class="sxs-lookup"><span data-stu-id="05d9d-180">Adding too many index columns can adversely affect disk space and index maintenance performance.</span></span>  
  
-   <span data-ttu-id="05d9d-181">涵盖索引可以提高查询性能，因为符合查询要求的全部数据都存在于索引本身中。</span><span class="sxs-lookup"><span data-stu-id="05d9d-181">Covering indexes can improve query performance because all the data needed to meet the requirements of the query exists within the index itself.</span></span> <span data-ttu-id="05d9d-182">也就是说，只需要索引页，而不需要表的数据页或聚集索引来检索所需数据，因此，减少了总体磁盘 I/O。</span><span class="sxs-lookup"><span data-stu-id="05d9d-182">That is, only the index pages, and not the data pages of the table or clustered index, are required to retrieve the requested data; therefore, reducing overall disk I/O.</span></span> <span data-ttu-id="05d9d-183">例如，对某一表（其中对列 **a** 、 **b** 和 **c**创建了组合索引）的列 **a**和 **b** 的查询，仅仅从该索引本身就可以检索指定数据。</span><span class="sxs-lookup"><span data-stu-id="05d9d-183">For example, a query of columns **a** and **b** on a table that has a composite index created on columns **a**, **b**, and **c** can retrieve the specified data from the index alone.</span></span>  
  
-   <span data-ttu-id="05d9d-184">将插入或修改尽可能多的行的查询写入单个语句内，而不要使用多个查询更新相同的行。</span><span class="sxs-lookup"><span data-stu-id="05d9d-184">Write queries that insert or modify as many rows as possible in a single statement, instead of using multiple queries to update the same rows.</span></span> <span data-ttu-id="05d9d-185">仅使用一个语句，就可以利用优化的索引维护。</span><span class="sxs-lookup"><span data-stu-id="05d9d-185">By using only one statement, optimized index maintenance could be exploited.</span></span>  
  
-   <span data-ttu-id="05d9d-186">评估查询类型以及如何在查询中使用列。</span><span class="sxs-lookup"><span data-stu-id="05d9d-186">Evaluate the query type and how columns are used in the query.</span></span> <span data-ttu-id="05d9d-187">例如，在完全匹配查询类型中使用的列就适合用于非聚集索引或聚集索引。</span><span class="sxs-lookup"><span data-stu-id="05d9d-187">For example, a column used in an exact-match query type would be a good candidate for a nonclustered or clustered index.</span></span>  
  
### <a name="column-considerations"></a><span data-ttu-id="05d9d-188">列注意事项</span><span class="sxs-lookup"><span data-stu-id="05d9d-188">Column Considerations</span></span>  

 <span data-ttu-id="05d9d-189">设计索引时，应考虑以下列准则：</span><span class="sxs-lookup"><span data-stu-id="05d9d-189">When you design an index consider the following column guidelines:</span></span>  
  
-   <span data-ttu-id="05d9d-190">对于聚集索引，请保持较短的索引键长度。</span><span class="sxs-lookup"><span data-stu-id="05d9d-190">Keep the length of the index key short for clustered indexes.</span></span> <span data-ttu-id="05d9d-191">另外，对唯一列或非空列创建聚集索引可以使聚集索引获益。</span><span class="sxs-lookup"><span data-stu-id="05d9d-191">Additionally, clustered indexes benefit from being created on unique or nonnull columns.</span></span>  
  
-   <span data-ttu-id="05d9d-192">不能将 `ntext`、`text`、`image`、`varchar(max)`、`nvarchar(max)` 和 `varbinary(max)` 数据类型的列指定为索引键列。</span><span class="sxs-lookup"><span data-stu-id="05d9d-192">Columns that are of the `ntext`, `text`, `image`, `varchar(max)`, `nvarchar(max)`, and `varbinary(max)` data types cannot be specified as index key columns.</span></span> <span data-ttu-id="05d9d-193">不过，`varchar(max)`、`nvarchar(max)`、`varbinary(max)` 和 `xml` 数据类型的列可以作为非键索引列参与非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="05d9d-193">However, `varchar(max)`, `nvarchar(max)`, `varbinary(max)`, and `xml` data types can participate in a nonclustered index as nonkey index columns.</span></span> <span data-ttu-id="05d9d-194">有关详细信息，请参阅本指南中的 [具有包含列的索引](#Included_Columns)。</span><span class="sxs-lookup"><span data-stu-id="05d9d-194">For more information, see the section ['Index with Included Columns](#Included_Columns)' in this guide.</span></span>  
  
-   <span data-ttu-id="05d9d-195">`xml` 数据类型的列只能在 XML 索引中用作键列。</span><span class="sxs-lookup"><span data-stu-id="05d9d-195">An `xml` data type can only be a key column only in an XML index.</span></span> <span data-ttu-id="05d9d-196">有关详细信息，请参阅 [XML 索引 (SQL Server)](../relational-databases/xml/xml-indexes-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="05d9d-196">For more information, see [XML Indexes &#40;SQL Server&#41;](../relational-databases/xml/xml-indexes-sql-server.md).</span></span> <span data-ttu-id="05d9d-197">SQL Server 2012 SP1 引入了称作选择性 XML 索引的一种新的 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="05d9d-197">SQL Server 2012 SP1 introduces a new type of XML index known as a Selective XML Index.</span></span> <span data-ttu-id="05d9d-198">这个新的索引可提高 SQL Server 中针对作为 XML 存储的数据的查询性能，从而通过降低索引本身的存储成本来加快大型 XML 数据工作负荷的索引编制和改进可伸缩性。</span><span class="sxs-lookup"><span data-stu-id="05d9d-198">This new index can improve querying performance over data stored as XML in SQL Server, allow for much faster indexing of large XML data workloads, and improve scalability by reducing storage costs of the index itself.</span></span> <span data-ttu-id="05d9d-199">有关详细信息，请参阅[选择性 XML 索引 (SXI)](../relational-databases/xml/selective-xml-indexes-sxi.md)。</span><span class="sxs-lookup"><span data-stu-id="05d9d-199">For more information, see [Selective XML Indexes &#40;SXI&#41;](../relational-databases/xml/selective-xml-indexes-sxi.md).</span></span>  
  
-   <span data-ttu-id="05d9d-200">检查列的唯一性。</span><span class="sxs-lookup"><span data-stu-id="05d9d-200">Examine column uniqueness.</span></span> <span data-ttu-id="05d9d-201">在同一个列组合的唯一索引而不是非唯一索引提供了有关使索引更有用的查询优化器的附加信息。</span><span class="sxs-lookup"><span data-stu-id="05d9d-201">A unique index instead of a nonunique index on the same combination of columns provides additional information for the query optimizer that makes the index more useful.</span></span> <span data-ttu-id="05d9d-202">有关详细信息，请参阅本指南中的 [唯一索引设计指南](#Unique) 。</span><span class="sxs-lookup"><span data-stu-id="05d9d-202">For more information, see [Unique Index Design Guidelines](#Unique) in this guide.</span></span>  
  
-   <span data-ttu-id="05d9d-203">在列中检查数据分布。</span><span class="sxs-lookup"><span data-stu-id="05d9d-203">Examine data distribution in the column.</span></span> <span data-ttu-id="05d9d-204">通常情况下，为包含很少唯一值的列创建索引或在这样的列上执行联接将导致长时间运行的查询。</span><span class="sxs-lookup"><span data-stu-id="05d9d-204">Frequently, a long-running query is caused by indexing a column with few unique values, or by performing a join on such a column.</span></span> <span data-ttu-id="05d9d-205">这是数据和查询的基本问题，通常不识别这种情况就无法解决这类问题。</span><span class="sxs-lookup"><span data-stu-id="05d9d-205">This is a fundamental problem with the data and query, and generally cannot be resolved without identifying this situation.</span></span> <span data-ttu-id="05d9d-206">例如，如果物理电话簿按姓的字母顺序排序，而城市里所有人的姓都是 Smith 或 Jones，则无法快速找到某个人。</span><span class="sxs-lookup"><span data-stu-id="05d9d-206">For example, a physical telephone directory sorted alphabetically on last name will not expedite locating a person if all people in the city are named Smith or Jones.</span></span> <span data-ttu-id="05d9d-207">有关数据分布的详细信息，请参阅 [统计信息](../relational-databases/statistics/statistics.md)。</span><span class="sxs-lookup"><span data-stu-id="05d9d-207">For more information about data distribution, see [Statistics](../relational-databases/statistics/statistics.md).</span></span>  
  
-   <span data-ttu-id="05d9d-208">考虑对具有定义完善的子集的列（例如，稀疏列、大部分值为 NULL 的列、含各类值的列以及含不同范围的值的列）使用筛选索引。</span><span class="sxs-lookup"><span data-stu-id="05d9d-208">Consider using filtered indexes on columns that have well-defined subsets, for example sparse columns, columns with mostly NULL values, columns with categories of values, and columns with distinct ranges of values.</span></span> <span data-ttu-id="05d9d-209">设计良好的筛选索引可以提高查询性能，降低索引维护成本和存储成本。</span><span class="sxs-lookup"><span data-stu-id="05d9d-209">A well-designed filtered index can improve query performance, reduce index maintenance costs, and reduce storage costs.</span></span>  
  
-   <span data-ttu-id="05d9d-210">如果索引包含多个列，则应考虑列的顺序。</span><span class="sxs-lookup"><span data-stu-id="05d9d-210">Consider the order of the columns if the index will contain multiple columns.</span></span> <span data-ttu-id="05d9d-211">用于等于 (=)、大于 (>)、小于 (<) 或 BETWEEN 搜索条件的 WHERE 子句或者参与联接的列应该放在最前面。</span><span class="sxs-lookup"><span data-stu-id="05d9d-211">The column that is used in the WHERE clause in an equal to (=), greater than (>), less than (<), or BETWEEN search condition, or participates in a join, should be placed first.</span></span> <span data-ttu-id="05d9d-212">其他列应该基于其非重复级别进行排序，就是说，从最不重复的列到最重复的列。</span><span class="sxs-lookup"><span data-stu-id="05d9d-212">Additional columns should be ordered based on their level of distinctness, that is, from the most distinct to the least distinct.</span></span>  
  
     <span data-ttu-id="05d9d-213">例如，如果将索引定义为 `LastName`、 `FirstName` ，则该索引在搜索条件为 `WHERE LastName = 'Smith'` 或 `WHERE LastName = Smith AND FirstName LIKE 'J%'`时将很有用。</span><span class="sxs-lookup"><span data-stu-id="05d9d-213">For example, if the index is defined as `LastName`, `FirstName` the index will be useful when the search criterion is `WHERE LastName = 'Smith'` or `WHERE LastName = Smith AND FirstName LIKE 'J%'`.</span></span> <span data-ttu-id="05d9d-214">不过，查询优化器不会将此索引用于基于 `FirstName (WHERE FirstName = 'Jane')`而搜索的查询。</span><span class="sxs-lookup"><span data-stu-id="05d9d-214">However, the query optimizer would not use the index for a query that searched only on `FirstName (WHERE FirstName = 'Jane')`.</span></span>  
  
-   <span data-ttu-id="05d9d-215">考虑对计算列进行索引。</span><span class="sxs-lookup"><span data-stu-id="05d9d-215">Consider indexing computed columns.</span></span> <span data-ttu-id="05d9d-216">有关详细信息，请参阅 [计算列上的索引](../relational-databases/indexes/indexes-on-computed-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="05d9d-216">For more information, see [Indexes on Computed Columns](../relational-databases/indexes/indexes-on-computed-columns.md).</span></span>  
  
### <a name="index-characteristics"></a><span data-ttu-id="05d9d-217">索引的特征</span><span class="sxs-lookup"><span data-stu-id="05d9d-217">Index Characteristics</span></span>  

 <span data-ttu-id="05d9d-218">在确定某一索引适合某一查询之后，可以选择最适合具体情况的索引类型。</span><span class="sxs-lookup"><span data-stu-id="05d9d-218">After you have determined that an index is appropriate for a query, you can select the type of index that best fits your situation.</span></span> <span data-ttu-id="05d9d-219">索引包含以下特性：</span><span class="sxs-lookup"><span data-stu-id="05d9d-219">Index characteristics include the following:</span></span>  
  
-   <span data-ttu-id="05d9d-220">聚集还是非聚集</span><span class="sxs-lookup"><span data-stu-id="05d9d-220">Clustered versus nonclustered</span></span>  
  
-   <span data-ttu-id="05d9d-221">唯一还是非唯一</span><span class="sxs-lookup"><span data-stu-id="05d9d-221">Unique versus nonunique</span></span>  
  
-   <span data-ttu-id="05d9d-222">单列还是多列</span><span class="sxs-lookup"><span data-stu-id="05d9d-222">Single column versus multicolumn</span></span>  
  
-   <span data-ttu-id="05d9d-223">索引中的列是升序排序还是降序排序</span><span class="sxs-lookup"><span data-stu-id="05d9d-223">Ascending or descending order on the columns in the index</span></span>  
  
-   <span data-ttu-id="05d9d-224">非聚集索引是全表还是经过筛选</span><span class="sxs-lookup"><span data-stu-id="05d9d-224">Full-table versus filtered for nonclustered indexes</span></span>  
  
 <span data-ttu-id="05d9d-225">您也可以通过设置选项（例如 FILLFACTOR）自定义索引的初始存储特征以优化其性能或维护。</span><span class="sxs-lookup"><span data-stu-id="05d9d-225">You can also customize the initial storage characteristics of the index to optimize its performance or maintenance by setting an option such as FILLFACTOR.</span></span> <span data-ttu-id="05d9d-226">而且，通过使用文件组或分区方案可以确定索引存储位置来优化性能。</span><span class="sxs-lookup"><span data-stu-id="05d9d-226">Also, you can determine the index storage location by using filegroups or partition schemes to optimize performance.</span></span>  
  
###  <a name="index-placement-on-filegroups-or-partitions-schemes"></a><a name="Index_placement"></a> <span data-ttu-id="05d9d-227">文件组或分区方案的索引设置</span><span class="sxs-lookup"><span data-stu-id="05d9d-227">Index Placement on Filegroups or Partitions Schemes</span></span>  

 <span data-ttu-id="05d9d-228">开发索引设计策略时，应该考虑在与数据库相关联的文件组上放置索引。</span><span class="sxs-lookup"><span data-stu-id="05d9d-228">As you develop your index design strategy, you should consider the placement of the indexes on the filegroups associated with the database.</span></span> <span data-ttu-id="05d9d-229">仔细选择文件组或分区方案可以改进查询性能。</span><span class="sxs-lookup"><span data-stu-id="05d9d-229">Careful selection of the filegroup or partition scheme can improve query performance.</span></span>  
  
 <span data-ttu-id="05d9d-230">默认情况下，索引存储在基表所在的文件组上，该索引即在该基表上创建。</span><span class="sxs-lookup"><span data-stu-id="05d9d-230">By default, indexes are stored in the same filegroup as the base table on which the index is created.</span></span> <span data-ttu-id="05d9d-231">非分区聚集索引和基表始终在同一个文件组中。</span><span class="sxs-lookup"><span data-stu-id="05d9d-231">A nonpartitioned clustered index and the base table always reside in the same filegroup.</span></span> <span data-ttu-id="05d9d-232">但是，您可以执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="05d9d-232">However, you can do the following:</span></span>  
  
-   <span data-ttu-id="05d9d-233">为除基表或聚集索引的文件组之外的文件组创建非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="05d9d-233">Create nonclustered indexes on a filegroup other than the filegroup of the base table or clustered index.</span></span>  
  
-   <span data-ttu-id="05d9d-234">对要涵盖多个文件组的聚集和非聚集索引进行分区。</span><span class="sxs-lookup"><span data-stu-id="05d9d-234">Partition clustered and nonclustered indexes to span multiple filegroups.</span></span>  
  
-   <span data-ttu-id="05d9d-235">通过删除聚集索引并在 DROP INDEX 语句的 MOVE TO 子句中指定新的文件组或分区方案，或者在 CREATE INDEX 语句中使用 DROP_EXISTING 子句，将表从一个文件组移至另一个文件组。</span><span class="sxs-lookup"><span data-stu-id="05d9d-235">Move a table from one filegroup to another by dropping the clustered index and specifying a new filegroup or partition scheme in the MOVE TO clause of the DROP INDEX statement or by using the CREATE INDEX statement with the DROP_EXISTING clause.</span></span>  
  
 <span data-ttu-id="05d9d-236">通过对其他文件组创建非聚集索引，可以在文件组通过自带的控制器使用不同的物理驱动器时实现性能提升。</span><span class="sxs-lookup"><span data-stu-id="05d9d-236">By creating the nonclustered index on a different filegroup, you can achieve performance gains if the filegroups are using different physical drives with their own controllers.</span></span> <span data-ttu-id="05d9d-237">这样一来，数据和索引信息即可由多个磁头并行读取。</span><span class="sxs-lookup"><span data-stu-id="05d9d-237">Data and index information can then be read in parallel by the multiple disk heads.</span></span> <span data-ttu-id="05d9d-238">例如，如果文件组 `Table_A` 的 `f1` 和文件组 `Index_A` 的 `f2` 都由同一个查询使用，就可无争夺地充分使用这两个文件组，因此可以实现性能提升。</span><span class="sxs-lookup"><span data-stu-id="05d9d-238">For example, if `Table_A` on filegroup `f1` and `Index_A` on filegroup `f2` are both being used by the same query, performance gains can be achieved because both filegroups are being fully used without contention.</span></span> <span data-ttu-id="05d9d-239">但是，如果 `Table_A` 由查询扫描而没有引用 `Index_A` ，则仅使用文件组 `f1` 。</span><span class="sxs-lookup"><span data-stu-id="05d9d-239">However, if `Table_A` is scanned by the query but `Index_A` is not referenced, only filegroup `f1` is used.</span></span> <span data-ttu-id="05d9d-240">这不会引起性能提升。</span><span class="sxs-lookup"><span data-stu-id="05d9d-240">This creates no performance gain.</span></span>  
  
 <span data-ttu-id="05d9d-241">由于无法预测将要发生的访问类型以及访问时间，因此更好的办法可能是展开所有文件组中的表和索引。</span><span class="sxs-lookup"><span data-stu-id="05d9d-241">Because you cannot predict what type of access will occur and when it will occur, it could be a better decision to spread your tables and indexes across all filegroups.</span></span> <span data-ttu-id="05d9d-242">这将保证能够访问所有磁盘，因为所有数据和索引在所有磁盘上均匀展开，不受访问数据的方式的限制。</span><span class="sxs-lookup"><span data-stu-id="05d9d-242">This would guarantee that all disks are being accessed because all data and indexes are spread evenly across all disks, regardless of which way the data is accessed.</span></span> <span data-ttu-id="05d9d-243">这对系统管理员来说也是更简单的方法。</span><span class="sxs-lookup"><span data-stu-id="05d9d-243">This is also a simpler approach for system administrators.</span></span>  
  
#### <a name="partitions-across-multiple-filegroups"></a><span data-ttu-id="05d9d-244">在多个文件组中分区</span><span class="sxs-lookup"><span data-stu-id="05d9d-244">Partitions Across Multiple Filegroups</span></span>  

 <span data-ttu-id="05d9d-245">还可以考虑在多个文件组中对聚集和非聚集索引分区。</span><span class="sxs-lookup"><span data-stu-id="05d9d-245">You can also consider partitioning clustered and nonclustered indexes across multiple filegroups.</span></span> <span data-ttu-id="05d9d-246">根据分区函数，对已分区的索引进行水平分区或按行分区。</span><span class="sxs-lookup"><span data-stu-id="05d9d-246">Partitioned indexes are partitioned horizontally, or by row, based on a partition function.</span></span> <span data-ttu-id="05d9d-247">分区函数定义如何根据某些列（称为分区依据列）的值将每一行映射到一组分区。</span><span class="sxs-lookup"><span data-stu-id="05d9d-247">The partition function defines how each row is mapped to a set of partitions based on the values of certain columns, called partitioning columns.</span></span> <span data-ttu-id="05d9d-248">分区方案将分区映射指定给一组文件组。</span><span class="sxs-lookup"><span data-stu-id="05d9d-248">A partition scheme specifies the mapping of the partitions to a set of filegroups.</span></span>  
  
 <span data-ttu-id="05d9d-249">对索引进行分区有以下优点：</span><span class="sxs-lookup"><span data-stu-id="05d9d-249">Partitioning an index can provide the following benefits:</span></span>  
  
-   <span data-ttu-id="05d9d-250">提供使大型索引更易管理的可伸缩系统。</span><span class="sxs-lookup"><span data-stu-id="05d9d-250">Provide scalable systems that make large indexes more manageable.</span></span> <span data-ttu-id="05d9d-251">例如，OLTP 系统可以实现处理大型索引的可识别分区的应用程序。</span><span class="sxs-lookup"><span data-stu-id="05d9d-251">OLTP systems, for example, can implement partition-aware applications that deal with large indexes.</span></span>  
  
-   <span data-ttu-id="05d9d-252">使查询运行得更快、更有效。</span><span class="sxs-lookup"><span data-stu-id="05d9d-252">Make queries run faster and more efficiently.</span></span> <span data-ttu-id="05d9d-253">当查询访问索引的几个分区时，查询优化器同时可以处理各个分区，但不包括不受该查询影响的分区。</span><span class="sxs-lookup"><span data-stu-id="05d9d-253">When queries access several partitions of an index, the query optimizer can process individual partitions at the same time and exclude partitions that are not affected by the query.</span></span>  
  
 <span data-ttu-id="05d9d-254">有关详细信息，请参阅 [Partitioned Tables and Indexes](../relational-databases/partitions/partitioned-tables-and-indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="05d9d-254">For more information, see [Partitioned Tables and Indexes](../relational-databases/partitions/partitioned-tables-and-indexes.md).</span></span>  
  
###  <a name="index-sort-order-design-guidelines"></a><a name="Sort_Order"></a> <span data-ttu-id="05d9d-255">索引排序顺序设计指南</span><span class="sxs-lookup"><span data-stu-id="05d9d-255">Index Sort Order Design Guidelines</span></span>  

 <span data-ttu-id="05d9d-256">定义索引时，应该考虑索引键列的数据是按升序还是按降序存储。</span><span class="sxs-lookup"><span data-stu-id="05d9d-256">When defining indexes, you should consider whether the data for the index key column should be stored in ascending or descending order.</span></span> <span data-ttu-id="05d9d-257">升序是默认设置，保持与 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]早期版本的兼容性。</span><span class="sxs-lookup"><span data-stu-id="05d9d-257">Ascending is the default and maintains compatibility with earlier versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="05d9d-258">CREATE INDEX、CREATE TABLE 和 ALTER TABLE 语句的语法在索引和约束中的各列上支持关键字 ASC（升序）和 DESC（降序）：</span><span class="sxs-lookup"><span data-stu-id="05d9d-258">The syntax of the CREATE INDEX, CREATE TABLE, and ALTER TABLE statements supports the keywords ASC (ascending) and DESC (descending) on individual columns in indexes and constraints.</span></span>  
  
 <span data-ttu-id="05d9d-259">当引用表的查询包含用以指定索引中键列的不同方向的 ORDER BY 子句时，指定键值存储在该索引中的顺序很有用。</span><span class="sxs-lookup"><span data-stu-id="05d9d-259">Specifying the order in which key values are stored in an index is useful when queries referencing the table have ORDER BY clauses that specify different directions for the key column or columns in that index.</span></span> <span data-ttu-id="05d9d-260">在这些情况下，索引就无需在查询计划中使用 SORT 运算符。因此，使得查询更有效。</span><span class="sxs-lookup"><span data-stu-id="05d9d-260">In these cases, the index can remove the need for a SORT operator in the query plan; therefore, this makes the query more efficient.</span></span> <span data-ttu-id="05d9d-261">例如， [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 采购部门的买方不得不评估他们从供应商处购买的产品的质量。</span><span class="sxs-lookup"><span data-stu-id="05d9d-261">For example, the buyers in the [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] purchasing department have to evaluate the quality of products they purchase from vendors.</span></span> <span data-ttu-id="05d9d-262">买方倾向于查验那些由具有高拒绝率的供应商发送的产品。</span><span class="sxs-lookup"><span data-stu-id="05d9d-262">The buyers are most interested in finding products sent by these vendors with a high rejection rate.</span></span> <span data-ttu-id="05d9d-263">检索数据以满足此条件需要将 `RejectedQty` 表中的 `Purchasing.PurchaseOrderDetail` 列按降序（由大到小）排序，并且将 `ProductID` 列按升序（由小到大）排序，如下列查询所示。</span><span class="sxs-lookup"><span data-stu-id="05d9d-263">As shown in the following query, retrieving the data to meet this criteria requires the `RejectedQty` column in the `Purchasing.PurchaseOrderDetail` table to be sorted in descending order (large to small) and the `ProductID` column to be sorted in ascending order (small to large).</span></span>  
  
```sql
SELECT RejectedQty, ((RejectedQty/OrderQty)*100) AS RejectionRate,  
    ProductID, DueDate  
FROM Purchasing.PurchaseOrderDetail  
ORDER BY RejectedQty DESC, ProductID ASC;  
```  
  
 <span data-ttu-id="05d9d-264">此查询的下列执行计划显示了查询优化器使用 SORT 运算符按 ORDER BY 子句指定的顺序返回结果集。</span><span class="sxs-lookup"><span data-stu-id="05d9d-264">The following execution plan for this query shows that the query optimizer used a SORT operator to return the result set in the order specified by the ORDER BY clause.</span></span>  
  
 <span data-ttu-id="05d9d-265">![执行计划显示使用了 SORT 运算符。](media/indexsort1.gif "执行计划显示使用了 SORT 运算符。")</span><span class="sxs-lookup"><span data-stu-id="05d9d-265">![Execution plan shows a SORT operator is used.](media/indexsort1.gif "Execution plan shows a SORT operator is used.")</span></span>  
  
 <span data-ttu-id="05d9d-266">如果使用与查询的 ORDER BY 子句中的键列匹配的键列创建索引，则无需在查询计划中使用 SORT 运算符，从而使查询计划更有效。</span><span class="sxs-lookup"><span data-stu-id="05d9d-266">If an index is created with key columns that match those in the ORDER BY clause in the query, the SORT operator can be eliminated in the query plan and the query plan is more efficient.</span></span>  
  
```sql
CREATE NONCLUSTERED INDEX IX_PurchaseOrderDetail_RejectedQty  
ON Purchasing.PurchaseOrderDetail  
    (RejectedQty DESC, ProductID ASC, DueDate, OrderQty);  
```  
  
 <span data-ttu-id="05d9d-267">再次执行查询后，下列执行计划显示未使用 SORT 运算符，而使用了新创建的非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="05d9d-267">After the query is executed again, the following execution plan shows that the SORT operator has been eliminated and the newly created nonclustered index is used.</span></span>  
  
 <span data-ttu-id="05d9d-268">![执行计划显示未使用 SORT 运算符](media/insertsort2.gif "执行计划显示未使用 SORT 运算符")</span><span class="sxs-lookup"><span data-stu-id="05d9d-268">![Execution plan shows a SORT operator is not used](media/insertsort2.gif "Execution plan shows a SORT operator is not used")</span></span>  
  
 <span data-ttu-id="05d9d-269">[!INCLUDE[ssDE](../includes/ssde-md.md)] 可以在两个方向上同样有效地移动。</span><span class="sxs-lookup"><span data-stu-id="05d9d-269">The [!INCLUDE[ssDE](../includes/ssde-md.md)] can move equally efficiently in either direction.</span></span> <span data-ttu-id="05d9d-270">对于一个在 ORDER BY 子句中列的排序方向倒排的查询，仍然可以使用定义为 `(RejectedQty DESC, ProductID ASC)` 的索引。</span><span class="sxs-lookup"><span data-stu-id="05d9d-270">An index defined as `(RejectedQty DESC, ProductID ASC)` can still be used for a query in which the sort direction of the columns in the ORDER BY clause are reversed.</span></span> <span data-ttu-id="05d9d-271">例如，包含 ORDER BY 子句 `ORDER BY RejectedQty ASC, ProductID DESC` 的查询可以使用该索引。</span><span class="sxs-lookup"><span data-stu-id="05d9d-271">For example, a query with the ORDER BY clause `ORDER BY RejectedQty ASC, ProductID DESC` can use the index.</span></span>  
  
 <span data-ttu-id="05d9d-272">只可以为键列指定排序顺序。</span><span class="sxs-lookup"><span data-stu-id="05d9d-272">Sort order can be specified only for key columns.</span></span> <span data-ttu-id="05d9d-273">[sys.index_columns](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql) 目录视图和 INDEXKEY_PROPERTY 函数报告索引列是按升序还是降序存储。</span><span class="sxs-lookup"><span data-stu-id="05d9d-273">The [sys.index_columns](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql) catalog view and the INDEXKEY_PROPERTY function report whether an index column is stored in ascending or descending order.</span></span>  
  
 <span data-ttu-id="05d9d-274">[本指南中与 "](#Top) ![返回页首" 链接一起使用的箭头图标](media/uparrow16x16.gif "用于返回页首链接的箭头图标")</span><span class="sxs-lookup"><span data-stu-id="05d9d-274">![Arrow icon used with Back to Top link](media/uparrow16x16.gif "Arrow icon used with Back to Top link") [In This Guide](#Top)</span></span>  
  
##  <a name="clustered-index-design-guidelines"></a><a name="Clustered"></a> <span data-ttu-id="05d9d-275">聚集索引设计指南</span><span class="sxs-lookup"><span data-stu-id="05d9d-275">Clustered Index Design Guidelines</span></span>  

 <span data-ttu-id="05d9d-276">聚集索引基于数据行的键值在表内排序和存储这些数据行。</span><span class="sxs-lookup"><span data-stu-id="05d9d-276">Clustered indexes sort and store the data rows in the table based on their key values.</span></span> <span data-ttu-id="05d9d-277">每个表只能有一个聚集索引，因为数据行本身只能按一个顺序存储。</span><span class="sxs-lookup"><span data-stu-id="05d9d-277">There can only be one clustered index per table, because the data rows themselves can only be sorted in one order.</span></span> <span data-ttu-id="05d9d-278">每个表几乎都对列定义聚集索引来实现下列功能：</span><span class="sxs-lookup"><span data-stu-id="05d9d-278">With few exceptions, every table should have a clustered index defined on the column, or columns, that offer the following:</span></span>  
  
-   <span data-ttu-id="05d9d-279">可用于经常使用的查询。</span><span class="sxs-lookup"><span data-stu-id="05d9d-279">Can be used for frequently used queries.</span></span>  
  
-   <span data-ttu-id="05d9d-280">提供高度唯一性。</span><span class="sxs-lookup"><span data-stu-id="05d9d-280">Provide a high degree of uniqueness.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="05d9d-281">创建 PRIMARY KEY 约束时，将在列上自动创建唯一索引。</span><span class="sxs-lookup"><span data-stu-id="05d9d-281">When you create a PRIMARY KEY constraint, a unique index on the column, or columns, is automatically created.</span></span> <span data-ttu-id="05d9d-282">默认情况下，此索引是聚集索引，但是在创建约束时，可以指定创建非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="05d9d-282">By default, this index is clustered; however, you can specify a nonclustered index when you create the constraint.</span></span>  
  
-   <span data-ttu-id="05d9d-283">可用于范围查询。</span><span class="sxs-lookup"><span data-stu-id="05d9d-283">Can be used in range queries.</span></span>  
  
 <span data-ttu-id="05d9d-284">如果未使用 UNIQUE 属性创建聚集索引，将向 [!INCLUDE[ssDE](../includes/ssde-md.md)] 表自动添加一个4字节的 uniquifier> 列。</span><span class="sxs-lookup"><span data-stu-id="05d9d-284">If the clustered index is not created with the UNIQUE property, the [!INCLUDE[ssDE](../includes/ssde-md.md)] automatically adds a 4-byte uniquifier column to the table.</span></span> <span data-ttu-id="05d9d-285">需要时， [!INCLUDE[ssDE](../includes/ssde-md.md)] 会自动将 uniquifier> 值添加到行中，以使每个键唯一。</span><span class="sxs-lookup"><span data-stu-id="05d9d-285">When it is required, the [!INCLUDE[ssDE](../includes/ssde-md.md)] automatically adds a uniquifier value to a row to make each key unique.</span></span> <span data-ttu-id="05d9d-286">此列和列值供内部使用，用户不能查看或访问。</span><span class="sxs-lookup"><span data-stu-id="05d9d-286">This column and its values are used internally and cannot be seen or accessed by users.</span></span>  
  
### <a name="clustered-index-architecture"></a><span data-ttu-id="05d9d-287">聚集索引体系结构</span><span class="sxs-lookup"><span data-stu-id="05d9d-287">Clustered Index Architecture</span></span>  

 <span data-ttu-id="05d9d-288">在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]中，索引是按 B 树结构进行组织的。</span><span class="sxs-lookup"><span data-stu-id="05d9d-288">In [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], indexes are organized as B-trees.</span></span> <span data-ttu-id="05d9d-289">索引 B 树中的每一页称为一个索引节点。</span><span class="sxs-lookup"><span data-stu-id="05d9d-289">Each page in an index B-tree is called an index node.</span></span> <span data-ttu-id="05d9d-290">B 树的顶端节点称为根节点。</span><span class="sxs-lookup"><span data-stu-id="05d9d-290">The top node of the B-tree is called the root node.</span></span> <span data-ttu-id="05d9d-291">索引中的底层节点称为叶节点。</span><span class="sxs-lookup"><span data-stu-id="05d9d-291">The bottom nodes in the index are called the leaf nodes.</span></span> <span data-ttu-id="05d9d-292">根节点与叶节点之间的任何索引级别统称为中间级。</span><span class="sxs-lookup"><span data-stu-id="05d9d-292">Any index levels between the root and the leaf nodes are collectively known as intermediate levels.</span></span> <span data-ttu-id="05d9d-293">在聚集索引中，叶节点包含基础表的数据页。</span><span class="sxs-lookup"><span data-stu-id="05d9d-293">In a clustered index, the leaf nodes contain the data pages of the underlying table.</span></span> <span data-ttu-id="05d9d-294">根节点和中间级节点包含存有索引行的索引页。</span><span class="sxs-lookup"><span data-stu-id="05d9d-294">The root and intermediate level nodes contain index pages holding index rows.</span></span> <span data-ttu-id="05d9d-295">每个索引行包含一个键值和一个指针，该指针指向 B 树上的某一中间级页或叶级索引中的某个数据行。</span><span class="sxs-lookup"><span data-stu-id="05d9d-295">Each index row contains a key value and a pointer to either an intermediate level page in the B-tree, or a data row in the leaf level of the index.</span></span> <span data-ttu-id="05d9d-296">每级索引中的页均被链接在双向链接列表中。</span><span class="sxs-lookup"><span data-stu-id="05d9d-296">The pages in each level of the index are linked in a doubly-linked list.</span></span>  
  
 <span data-ttu-id="05d9d-297">聚集索引在 [sys.partitions](/sql/relational-databases/system-catalog-views/sys-partitions-transact-sql)中有一行，其中，索引使用的每个分区的 **index_id** = 1。</span><span class="sxs-lookup"><span data-stu-id="05d9d-297">Clustered indexes have one row in [sys.partitions](/sql/relational-databases/system-catalog-views/sys-partitions-transact-sql), with **index_id** = 1 for each partition used by the index.</span></span> <span data-ttu-id="05d9d-298">默认情况下，聚集索引有单个分区。</span><span class="sxs-lookup"><span data-stu-id="05d9d-298">By default, a clustered index has a single partition.</span></span> <span data-ttu-id="05d9d-299">当聚集索引有多个分区时，每个分区都有一个包含该特定分区相关数据的 B 树结构。</span><span class="sxs-lookup"><span data-stu-id="05d9d-299">When a clustered index has multiple partitions, each partition has a B-tree structure that contains the data for that specific partition.</span></span> <span data-ttu-id="05d9d-300">例如，如果聚集索引有四个分区，就有四个 B 树结构，每个分区中有一个 B 树结构。</span><span class="sxs-lookup"><span data-stu-id="05d9d-300">For example, if a clustered index has four partitions, there are four B-tree structures; one in each partition.</span></span>  
  
 <span data-ttu-id="05d9d-301">根据聚集索引中的数据类型，每个聚集索引结构将有一个或多个分配单元，将在这些单元中存储和管理特定分区的相关数据。</span><span class="sxs-lookup"><span data-stu-id="05d9d-301">Depending on the data types in the clustered index, each clustered index structure will have one or more allocation units in which to store and manage the data for a specific partition.</span></span> <span data-ttu-id="05d9d-302">每个聚集索引的每个分区中至少有一个 IN_ROW_DATA 分配单元。</span><span class="sxs-lookup"><span data-stu-id="05d9d-302">At a minimum, each clustered index will have one IN_ROW_DATA allocation unit per partition.</span></span> <span data-ttu-id="05d9d-303">如果聚集索引包含大型对象 (LOB) 列，则它的每个分区中还会有一个 LOB_DATA 分配单元。</span><span class="sxs-lookup"><span data-stu-id="05d9d-303">The clustered index will also have one LOB_DATA allocation unit per partition if it contains large object (LOB) columns.</span></span> <span data-ttu-id="05d9d-304">如果聚集索引包含的变量长度列超过 8,060 字节的行大小限制，则它的每个分区中还会有一个 ROW_OVERFLOW_DATA 分配单元。</span><span class="sxs-lookup"><span data-stu-id="05d9d-304">It will also have one ROW_OVERFLOW_DATA allocation unit per partition if it contains variable length columns that exceed the 8,060 byte row size limit.</span></span>  
  
 <span data-ttu-id="05d9d-305">数据链内的页和行将按聚集索引键值进行排序。</span><span class="sxs-lookup"><span data-stu-id="05d9d-305">The pages in the data chain and the rows in them are ordered on the value of the clustered index key.</span></span> <span data-ttu-id="05d9d-306">所有插入操作都在所插入行中的键值与现有行中的排序顺序相匹配时执行。</span><span class="sxs-lookup"><span data-stu-id="05d9d-306">All inserts are made at the point where the key value in the inserted row fits in the ordering sequence among existing rows.</span></span>  
  
 <span data-ttu-id="05d9d-307">下图显式了聚集索引单个分区中的结构。</span><span class="sxs-lookup"><span data-stu-id="05d9d-307">This illustration shows the structure of a clustered index in a single partition.</span></span>  
  
 <span data-ttu-id="05d9d-308">![聚集索引的级别](media/bokind2.gif "聚集索引的级别")</span><span class="sxs-lookup"><span data-stu-id="05d9d-308">![Levels of a clustered index](media/bokind2.gif "Levels of a clustered index")</span></span>  
  
### <a name="query-considerations"></a><span data-ttu-id="05d9d-309">查询注意事项</span><span class="sxs-lookup"><span data-stu-id="05d9d-309">Query Considerations</span></span>  

 <span data-ttu-id="05d9d-310">在创建聚集索引之前，应先了解数据是如何被访问的。</span><span class="sxs-lookup"><span data-stu-id="05d9d-310">Before you create clustered indexes, understand how your data will be accessed.</span></span> <span data-ttu-id="05d9d-311">考虑对具有以下特点的查询使用聚集索引：</span><span class="sxs-lookup"><span data-stu-id="05d9d-311">Consider using a clustered index for queries that do the following:</span></span>  
  
-   <span data-ttu-id="05d9d-312">使用运算符（如 BETWEEN、>、>=、< 和 <=）返回一系列值。</span><span class="sxs-lookup"><span data-stu-id="05d9d-312">Return a range of values by using operators such as BETWEEN, >, >=, <, and <=.</span></span>  
  
     <span data-ttu-id="05d9d-313">使用聚集索引找到包含第一个值的行后，便可以确保包含后续索引值的行物理相邻。</span><span class="sxs-lookup"><span data-stu-id="05d9d-313">After the row with the first value is found by using the clustered index, rows with subsequent indexed values are guaranteed to be physically adjacent.</span></span> <span data-ttu-id="05d9d-314">例如，如果某个查询在一系列销售订单号间检索记录， `SalesOrderNumber` 列的聚集索引可快速定位包含起始销售订单号的行，然后检索表中所有连续的行，直到检索到最后的销售订单号。</span><span class="sxs-lookup"><span data-stu-id="05d9d-314">For example, if a query retrieves records between a range of sales order numbers, a clustered index on the column `SalesOrderNumber` can quickly locate the row that contains the starting sales order number, and then retrieve all successive rows in the table until the last sales order number is reached.</span></span>  
  
-   <span data-ttu-id="05d9d-315">返回大型结果集。</span><span class="sxs-lookup"><span data-stu-id="05d9d-315">Return large result sets.</span></span>  
  
-   <span data-ttu-id="05d9d-316">使用 JOIN 子句；一般情况下，使用该子句的是外键列。</span><span class="sxs-lookup"><span data-stu-id="05d9d-316">Use JOIN clauses; typically these are foreign key columns.</span></span>  
  
-   <span data-ttu-id="05d9d-317">使用 ORDER BY 或 GROUP BY 子句。</span><span class="sxs-lookup"><span data-stu-id="05d9d-317">Use ORDER BY, or GROUP BY clauses.</span></span>  
  
     <span data-ttu-id="05d9d-318">在 ORDER BY 或 GROUP BY 子句中指定的列的索引，可以使 [!INCLUDE[ssDE](../includes/ssde-md.md)] 不必对数据进行排序，因为这些行已经排序。</span><span class="sxs-lookup"><span data-stu-id="05d9d-318">An index on the columns specified in the ORDER BY or GROUP BY clause may remove the need for the [!INCLUDE[ssDE](../includes/ssde-md.md)] to sort the data, because the rows are already sorted.</span></span> <span data-ttu-id="05d9d-319">这会有助于提升查询性能。</span><span class="sxs-lookup"><span data-stu-id="05d9d-319">This improves query performance.</span></span>  
  
### <a name="column-considerations"></a><span data-ttu-id="05d9d-320">列注意事项</span><span class="sxs-lookup"><span data-stu-id="05d9d-320">Column Considerations</span></span>  

 <span data-ttu-id="05d9d-321">一般情况下，定义聚集索引键时使用的列越少越好。</span><span class="sxs-lookup"><span data-stu-id="05d9d-321">Generally, you should define the clustered index key with as few columns as possible.</span></span> <span data-ttu-id="05d9d-322">考虑具有下列一个或多个属性的列：</span><span class="sxs-lookup"><span data-stu-id="05d9d-322">Consider columns that have one or more of the following attributes:</span></span>  
  
-   <span data-ttu-id="05d9d-323">唯一或包含许多不重复的值</span><span class="sxs-lookup"><span data-stu-id="05d9d-323">Are unique or contain many distinct values</span></span>  
  
     <span data-ttu-id="05d9d-324">例如，雇员 ID 唯一地标识雇员。</span><span class="sxs-lookup"><span data-stu-id="05d9d-324">For example, an employee ID uniquely identifies employees.</span></span> <span data-ttu-id="05d9d-325">`EmployeeID` 列的聚集索引或 PRIMARY KEY 约束将改善基于雇员 ID 号搜索雇员信息的查询的性能。</span><span class="sxs-lookup"><span data-stu-id="05d9d-325">A clustered index or PRIMARY KEY constraint on the `EmployeeID` column would improve the performance of queries that search for employee information based on the employee ID number.</span></span> <span data-ttu-id="05d9d-326">另外，可对 `LastName`、 `FirstName`、 `MiddleName` 列创建聚集索引，因为经常以这种方式分组和查询雇员记录，而且这些列的组合还可提供高区分度。</span><span class="sxs-lookup"><span data-stu-id="05d9d-326">Alternatively, a clustered index could be created on `LastName`, `FirstName`, `MiddleName` because employee records are frequently grouped and queried in this way, and the combination of these columns would still provide a high degree of difference.</span></span>  
  
-   <span data-ttu-id="05d9d-327">按顺序被访问</span><span class="sxs-lookup"><span data-stu-id="05d9d-327">Are accessed sequentially</span></span>  
  
     <span data-ttu-id="05d9d-328">例如，产品 ID 唯一地标识 `Production.Product` 数据库的 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 表中的产品。</span><span class="sxs-lookup"><span data-stu-id="05d9d-328">For example, a product ID uniquely identifies products in the `Production.Product` table in the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="05d9d-329">在其中指定顺序搜索的查询（如 `WHERE ProductID BETWEEN 980 and 999`）将从 `ProductID`的聚集索引受益。</span><span class="sxs-lookup"><span data-stu-id="05d9d-329">Queries in which a sequential search is specified, such as `WHERE ProductID BETWEEN 980 and 999`, would benefit from a clustered index on `ProductID`.</span></span> <span data-ttu-id="05d9d-330">这是因为行将按该键列的排序顺序存储。</span><span class="sxs-lookup"><span data-stu-id="05d9d-330">This is because the rows would be stored in sorted order on that key column.</span></span>  
  
-   <span data-ttu-id="05d9d-331">定义为 IDENTITY。</span><span class="sxs-lookup"><span data-stu-id="05d9d-331">Defined as IDENTITY.</span></span>  
  
-   <span data-ttu-id="05d9d-332">经常用于对表中检索到的数据进行排序。</span><span class="sxs-lookup"><span data-stu-id="05d9d-332">Used frequently to sort the data retrieved from a table.</span></span>  
  
     <span data-ttu-id="05d9d-333">按该列对表进行聚集（即物理排序）是一个好方法，它可以在每次查询该列时节省排序操作的成本。</span><span class="sxs-lookup"><span data-stu-id="05d9d-333">It can be a good idea to cluster, that is physically sort, the table on that column to save the cost of a sort operation every time the column is queried.</span></span>  
  
 <span data-ttu-id="05d9d-334">聚集索引不适用于具有下列属性的列：</span><span class="sxs-lookup"><span data-stu-id="05d9d-334">Clustered indexes are not a good choice for the following attributes:</span></span>  
  
-   <span data-ttu-id="05d9d-335">频繁更改的列</span><span class="sxs-lookup"><span data-stu-id="05d9d-335">Columns that undergo frequent changes</span></span>  
  
     <span data-ttu-id="05d9d-336">这将导致整行移动，因为 [!INCLUDE[ssDE](../includes/ssde-md.md)] 必须按物理顺序保留行的数据值。</span><span class="sxs-lookup"><span data-stu-id="05d9d-336">This causes the whole row to move, because the [!INCLUDE[ssDE](../includes/ssde-md.md)] must keep the data values of a row in physical order.</span></span> <span data-ttu-id="05d9d-337">这一点要特别注意，因为在大容量事务处理系统中数据通常是可变的。</span><span class="sxs-lookup"><span data-stu-id="05d9d-337">This is an important consideration in high-volume transaction processing systems in which data is typically volatile.</span></span>  
  
-   <span data-ttu-id="05d9d-338">宽键</span><span class="sxs-lookup"><span data-stu-id="05d9d-338">Wide keys</span></span>  
  
     <span data-ttu-id="05d9d-339">宽键是若干列或若干大型列的组合。</span><span class="sxs-lookup"><span data-stu-id="05d9d-339">Wide keys are a composite of several columns or several large-size columns.</span></span> <span data-ttu-id="05d9d-340">所有非聚集索引将聚集索引中的键值用作查找键。</span><span class="sxs-lookup"><span data-stu-id="05d9d-340">The key values from the clustered index are used by all nonclustered indexes as lookup keys.</span></span> <span data-ttu-id="05d9d-341">为同一表定义的任何非聚集索引都将增大许多，这是因为非聚集索引项包含聚集键，同时也包含为此非聚集索引定义的键列。</span><span class="sxs-lookup"><span data-stu-id="05d9d-341">Any nonclustered indexes defined on the same table will be significantly larger because the nonclustered index entries contain the clustering key and also the key columns defined for that nonclustered index.</span></span>  
  
 <span data-ttu-id="05d9d-342">[本指南中与 "](#Top) ![返回页首" 链接一起使用的箭头图标](media/uparrow16x16.gif "用于返回页首链接的箭头图标")</span><span class="sxs-lookup"><span data-stu-id="05d9d-342">![Arrow icon used with Back to Top link](media/uparrow16x16.gif "Arrow icon used with Back to Top link") [In This Guide](#Top)</span></span>  
  
##  <a name="nonclustered-index-design-guidelines"></a><a name="Nonclustered"></a> <span data-ttu-id="05d9d-343">非聚集索引设计指南</span><span class="sxs-lookup"><span data-stu-id="05d9d-343">Nonclustered Index Design Guidelines</span></span>  

 <span data-ttu-id="05d9d-344">非聚集索引包含索引键值和指向表数据存储位置的行定位器。</span><span class="sxs-lookup"><span data-stu-id="05d9d-344">A nonclustered index contains the index key values and row locators that point to the storage location of the table data.</span></span> <span data-ttu-id="05d9d-345">可以对表或索引视图创建多个非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="05d9d-345">You can create multiple nonclustered indexes on a table or indexed view.</span></span> <span data-ttu-id="05d9d-346">通常，设计非聚集索引是为改善经常使用的、没有建立聚集索引的查询的性能。</span><span class="sxs-lookup"><span data-stu-id="05d9d-346">Generally, nonclustered indexes should be designed to improve the performance of frequently used queries that are not covered by the clustered index.</span></span>  
  
 <span data-ttu-id="05d9d-347">与使用书中索引的方式相似，查询优化器在搜索数据值时，先搜索非聚集索引以找到数据值在表中的位置，然后直接从该位置检索数据。</span><span class="sxs-lookup"><span data-stu-id="05d9d-347">Similar to the way you use an index in a book, the query optimizer searches for a data value by searching the nonclustered index to find the location of the data value in the table and then retrieves the data directly from that location.</span></span> <span data-ttu-id="05d9d-348">这使非聚集索引成为完全匹配查询的最佳选择，因为索引包含说明查询所搜索的数据值在表中的精确位置的项。</span><span class="sxs-lookup"><span data-stu-id="05d9d-348">This makes nonclustered indexes the optimal choice for exact match queries because the index contains entries describing the exact location in the table of the data values being searched for in the queries.</span></span> <span data-ttu-id="05d9d-349">例如，为了从 `HumanResources. Employee` 表中查询向特定经理负责的所有雇员，查询优化器可能使用非聚集索引 `IX_Employee_ManagerID`；它以 `ManagerID` 作为其键列。</span><span class="sxs-lookup"><span data-stu-id="05d9d-349">For example, to query the `HumanResources. Employee` table for all employees that report to a specific manager, the query optimizer might use the nonclustered index `IX_Employee_ManagerID`; this has `ManagerID` as its key column.</span></span> <span data-ttu-id="05d9d-350">查询优化器能快速找出索引中与指定 `ManagerID`匹配的所有项。</span><span class="sxs-lookup"><span data-stu-id="05d9d-350">The query optimizer can quickly find all entries in the index that match the specified `ManagerID`.</span></span> <span data-ttu-id="05d9d-351">每个索引项都指向表或聚集索引中准确的页和行，其中可以找到相应的数据。</span><span class="sxs-lookup"><span data-stu-id="05d9d-351">Each index entry points to the exact page and row in the table, or clustered index, in which the corresponding data can be found.</span></span> <span data-ttu-id="05d9d-352">在查询优化器在索引中找到所有项之后，它可以直接转到准确的页和行进行数据检索。</span><span class="sxs-lookup"><span data-stu-id="05d9d-352">After the query optimizer finds all entries in the index, it can go directly to the exact page and row to retrieve the data.</span></span>  
  
### <a name="nonclustered-index-architecture"></a><span data-ttu-id="05d9d-353">非聚集索引体系结构</span><span class="sxs-lookup"><span data-stu-id="05d9d-353">Nonclustered Index Architecture</span></span>  

 <span data-ttu-id="05d9d-354">非聚集索引与聚集索引具有相同的 B 树结构，它们之间的显著差别在于以下两点：</span><span class="sxs-lookup"><span data-stu-id="05d9d-354">Nonclustered indexes have the same B-tree structure as clustered indexes, except for the following significant differences:</span></span>  
  
-   <span data-ttu-id="05d9d-355">基础表的数据行不按非聚集键的顺序排序和存储。</span><span class="sxs-lookup"><span data-stu-id="05d9d-355">The data rows of the underlying table are not sorted and stored in order based on their nonclustered keys.</span></span>  
  
-   <span data-ttu-id="05d9d-356">非聚集索引的叶层是由索引页而不是由数据页组成。</span><span class="sxs-lookup"><span data-stu-id="05d9d-356">The leaf layer of a nonclustered index is made up of index pages instead of data pages.</span></span>  
  
 <span data-ttu-id="05d9d-357">非聚集索引行中的行定位器或是指向行的指针，或是行的聚集索引键，如下所述：</span><span class="sxs-lookup"><span data-stu-id="05d9d-357">The row locators in nonclustered index rows are either a pointer to a row or are a clustered index key for a row, as described in the following:</span></span>  
  
-   <span data-ttu-id="05d9d-358">如果表是堆（意味着该表没有聚集索引），则行定位器是指向行的指针。</span><span class="sxs-lookup"><span data-stu-id="05d9d-358">If the table is a heap, which means it does not have a clustered index, the row locator is a pointer to the row.</span></span> <span data-ttu-id="05d9d-359">该指针由文件标识符 (ID)、页码和页上的行数生成。</span><span class="sxs-lookup"><span data-stu-id="05d9d-359">The pointer is built from the file identifier (ID), page number, and number of the row on the page.</span></span> <span data-ttu-id="05d9d-360">整个指针称为行 ID (RID)。</span><span class="sxs-lookup"><span data-stu-id="05d9d-360">The whole pointer is known as a Row ID (RID).</span></span>  
  
-   <span data-ttu-id="05d9d-361">如果表有聚集索引或索引视图上有聚集索引，则行定位器是行的聚集索引键。</span><span class="sxs-lookup"><span data-stu-id="05d9d-361">If the table has a clustered index, or the index is on an indexed view, the row locator is the clustered index key for the row.</span></span>  
  
 <span data-ttu-id="05d9d-362">对于索引使用的每个分区，非聚集索引在 **index_id** >1 的 [sys.partitions](/sql/relational-databases/system-catalog-views/sys-partitions-transact-sql) 中都有对应的一行。</span><span class="sxs-lookup"><span data-stu-id="05d9d-362">Nonclustered indexes have one row in [sys.partitions](/sql/relational-databases/system-catalog-views/sys-partitions-transact-sql) with **index_id** >1 for each partition used by the index.</span></span> <span data-ttu-id="05d9d-363">默认情况下，一个非聚集索引有单个分区。</span><span class="sxs-lookup"><span data-stu-id="05d9d-363">By default, a nonclustered index has a single partition.</span></span> <span data-ttu-id="05d9d-364">如果一个非聚集索引有多个分区，则每个分区都有一个包含该特定分区的索引行的 B 树结构。</span><span class="sxs-lookup"><span data-stu-id="05d9d-364">When a nonclustered index has multiple partitions, each partition has a B-tree structure that contains the index rows for that specific partition.</span></span> <span data-ttu-id="05d9d-365">例如，如果一个非聚集索引有四个分区，那么就有四个 B 树结构，每个分区中一个。</span><span class="sxs-lookup"><span data-stu-id="05d9d-365">For example, if a nonclustered index has four partitions, there are four B-tree structures, with one in each partition.</span></span>  
  
 <span data-ttu-id="05d9d-366">根据非聚集索引中数据类型的不同，每个非聚集索引结构会有一个或多个分配单元，在其中存储和管理特定分区的数据。</span><span class="sxs-lookup"><span data-stu-id="05d9d-366">Depending on the data types in the nonclustered index, each nonclustered index structure will have one or more allocation units in which to store and manage the data for a specific partition.</span></span> <span data-ttu-id="05d9d-367">每个非聚集索引至少有一个针对每个分区的 IN_ROW_DATA 分配单元（存储索引 B 树页）。</span><span class="sxs-lookup"><span data-stu-id="05d9d-367">At a minimum, each nonclustered index will have one IN_ROW_DATA allocation unit per partition that stores the index B-tree pages.</span></span> <span data-ttu-id="05d9d-368">如果非聚集索引包含大型对象 (LOB) 列，则还有一个针对每个分区的 LOB_DATA 分配单元。</span><span class="sxs-lookup"><span data-stu-id="05d9d-368">The nonclustered index will also have one LOB_DATA allocation unit per partition if it contains large object (LOB) columns .</span></span> <span data-ttu-id="05d9d-369">此外，如果非聚集索引包含的可变长度列超过 8,060 字节行大小限制，则还有一个针对每个分区的 ROW_OVERFLOW_DATA 分配单元。</span><span class="sxs-lookup"><span data-stu-id="05d9d-369">Additionally, it will have one ROW_OVERFLOW_DATA allocation unit per partition if it contains variable length columns that exceed the 8,060 byte row size limit.</span></span>  
  
 <span data-ttu-id="05d9d-370">下图说明了单个分区中的非聚集索引结构。</span><span class="sxs-lookup"><span data-stu-id="05d9d-370">The following illustration shows the structure of a nonclustered index in a single partition.</span></span>  
  
 <span data-ttu-id="05d9d-371">![非聚集索引的级别](media/bokind1.gif "非聚集索引的级别")</span><span class="sxs-lookup"><span data-stu-id="05d9d-371">![Levels of a nonclustered index](media/bokind1.gif "Levels of a nonclustered index")</span></span>  
  
### <a name="database-considerations"></a><span data-ttu-id="05d9d-372">数据库注意事项</span><span class="sxs-lookup"><span data-stu-id="05d9d-372">Database Considerations</span></span>  

 <span data-ttu-id="05d9d-373">设计非聚集索引时需要注意数据库的特征。</span><span class="sxs-lookup"><span data-stu-id="05d9d-373">Consider the characteristics of the database when designing nonclustered indexes.</span></span>  
  
-   <span data-ttu-id="05d9d-374">更新要求较低但包含大量数据的数据库或表可以从许多非聚集索引中获益从而改善查询性能。</span><span class="sxs-lookup"><span data-stu-id="05d9d-374">Databases or tables with low update requirements, but large volumes of data can benefit from many nonclustered indexes to improve query performance.</span></span> <span data-ttu-id="05d9d-375">与全表非聚集索引相比，考虑为定义完善的数据子集创建筛选索引可以提高查询性能、降低索引存储开销并减少索引维护开销。</span><span class="sxs-lookup"><span data-stu-id="05d9d-375">Consider creating filtered indexes for well-defined subsets of data to improve query performance, reduce index storage costs, and reduce index maintenance costs compared with full-table nonclustered indexes.</span></span>  
  
     <span data-ttu-id="05d9d-376">决策支持系统应用程序和主要包含只读数据的数据库可以从许多非聚集索引中获益。</span><span class="sxs-lookup"><span data-stu-id="05d9d-376">Decision Support System applications and databases that contain primarily read-only data can benefit from many nonclustered indexes.</span></span> <span data-ttu-id="05d9d-377">查询优化器具有更多可供选择的索引用来确定最快的访问方法，并且数据库的低更新特征意味着索引维护不会降低性能。</span><span class="sxs-lookup"><span data-stu-id="05d9d-377">The query optimizer has more indexes to choose from to determine the fastest access method, and the low update characteristics of the database mean index maintenance will not impede performance.</span></span>  
  
-   <span data-ttu-id="05d9d-378">联机事务处理应用程序和包含大量更新表的数据库应避免使用过多的索引。</span><span class="sxs-lookup"><span data-stu-id="05d9d-378">Online Transaction Processing applications and databases that contain heavily updated tables should avoid over-indexing.</span></span> <span data-ttu-id="05d9d-379">此外，索引应该是窄的，即列越少越好。</span><span class="sxs-lookup"><span data-stu-id="05d9d-379">Additionally, indexes should be narrow, that is, with as few columns as possible.</span></span>  
  
     <span data-ttu-id="05d9d-380">对表编制大量索引会影响 INSERT、UPDATE、DELETE 和 MERGE 语句的性能，因为当表中的数据更改时，所有索引都须进行适当的调整。</span><span class="sxs-lookup"><span data-stu-id="05d9d-380">Large numbers of indexes on a table affect the performance of INSERT, UPDATE, DELETE, and MERGE  statements because all indexes must be adjusted appropriately as data in the table changes.</span></span>  
  
### <a name="query-considerations"></a><span data-ttu-id="05d9d-381">查询注意事项</span><span class="sxs-lookup"><span data-stu-id="05d9d-381">Query Considerations</span></span>  

 <span data-ttu-id="05d9d-382">在创建非聚集索引之前，应先了解访问数据的方式。</span><span class="sxs-lookup"><span data-stu-id="05d9d-382">Before you create nonclustered indexes, you should understand how your data will be accessed.</span></span> <span data-ttu-id="05d9d-383">考虑对具有以下属性的查询使用非聚集索引：</span><span class="sxs-lookup"><span data-stu-id="05d9d-383">Consider using a nonclustered index for queries that have the following attributes:</span></span>  
  
-   <span data-ttu-id="05d9d-384">使用 JOIN 或 GROUP BY 子句。</span><span class="sxs-lookup"><span data-stu-id="05d9d-384">Use JOIN or GROUP BY clauses.</span></span>  
  
     <span data-ttu-id="05d9d-385">应为联接和分组操作中所涉及的列创建多个非聚集索引，为任何外键列创建一个聚集索引。</span><span class="sxs-lookup"><span data-stu-id="05d9d-385">Create multiple nonclustered indexes on columns involved in join and grouping operations, and a clustered index on any foreign key columns.</span></span>  
  
-   <span data-ttu-id="05d9d-386">不返回大型结果集的查询。</span><span class="sxs-lookup"><span data-stu-id="05d9d-386">Queries that do not return large result sets.</span></span>  
  
     <span data-ttu-id="05d9d-387">创建筛选索引以覆盖从大型表中返回定义完善的行子集的查询。</span><span class="sxs-lookup"><span data-stu-id="05d9d-387">Create filtered indexes to cover queries that return a well-defined subset of rows from a large table.</span></span>  
  
-   <span data-ttu-id="05d9d-388">包含经常包含在查询的搜索条件（例如返回完全匹配的 WHERE 子句）中的列。</span><span class="sxs-lookup"><span data-stu-id="05d9d-388">Contain columns frequently involved in search conditions of a query, such as WHERE clause, that return exact matches.</span></span>  
  
### <a name="column-considerations"></a><span data-ttu-id="05d9d-389">列注意事项</span><span class="sxs-lookup"><span data-stu-id="05d9d-389">Column Considerations</span></span>  

 <span data-ttu-id="05d9d-390">考虑具有以下一个或多个属性的列：</span><span class="sxs-lookup"><span data-stu-id="05d9d-390">Consider columns that have one or more of these attributes:</span></span>  
  
-   <span data-ttu-id="05d9d-391">覆盖查询。</span><span class="sxs-lookup"><span data-stu-id="05d9d-391">Cover the query.</span></span>  
  
     <span data-ttu-id="05d9d-392">当索引包含查询中的所有列时，性能可以提升。</span><span class="sxs-lookup"><span data-stu-id="05d9d-392">Performance gains are achieved when the index contains all columns in the query.</span></span> <span data-ttu-id="05d9d-393">查询优化器可以找到索引内的所有列值；不会访问表或聚集索引数据，这样就减少了磁盘 I/O 操作。</span><span class="sxs-lookup"><span data-stu-id="05d9d-393">The query optimizer can locate all the column values within the index; table or clustered index data is not accessed resulting in fewer disk I/O operations.</span></span> <span data-ttu-id="05d9d-394">使用具有包含列的索引来添加覆盖列，而不是创建宽索引键。</span><span class="sxs-lookup"><span data-stu-id="05d9d-394">Use index with included columns to add covering columns instead of creating a wide index key.</span></span>  
  
     <span data-ttu-id="05d9d-395">如果表有聚集索引，则该聚集索引中定义的列将自动追加到表上每个非聚集索引的末端。</span><span class="sxs-lookup"><span data-stu-id="05d9d-395">If the table has a clustered index, the column or columns defined in the clustered index are automatically appended to the end of each nonclustered index on the table.</span></span> <span data-ttu-id="05d9d-396">这可以生成覆盖查询，而不用在非聚集索引定义中指定聚集索引列。</span><span class="sxs-lookup"><span data-stu-id="05d9d-396">This can produce a covered query without specifying the clustered index columns in the definition of the nonclustered index.</span></span> <span data-ttu-id="05d9d-397">例如，如果一个表在 `C`列上有聚集索引，则 `B` 和 `A` 列的非聚集索引将具有其自己的键值列 `B`、 `A`和 `C`。</span><span class="sxs-lookup"><span data-stu-id="05d9d-397">For example, if a table has a clustered index on column `C`, a nonclustered index on columns `B` and `A` will have as its key values columns `B`, `A`, and `C`.</span></span>  
  
-   <span data-ttu-id="05d9d-398">大量非重复值，如姓氏和名字的组合（前提是聚集索引被用于其他列）。</span><span class="sxs-lookup"><span data-stu-id="05d9d-398">Lots of distinct values, such as a combination of last name and first name, if a clustered index is used for other columns.</span></span>  
  
     <span data-ttu-id="05d9d-399">如果只有很少的非重复值，例如仅有 1 和 0，则大多数查询将不使用索引，因为此时表扫描通常更有效。</span><span class="sxs-lookup"><span data-stu-id="05d9d-399">If there are very few distinct values, such as only 1 and 0, most queries will not use the index because a table scan is generally more efficient.</span></span> <span data-ttu-id="05d9d-400">对于这种类型的数据，应考虑对仅出现在少数行中的非重复值创建筛选索引。</span><span class="sxs-lookup"><span data-stu-id="05d9d-400">For this type of data, consider creating a filtered index on a distinct value that only occurs in a small number of rows.</span></span> <span data-ttu-id="05d9d-401">例如，如果大部分值都是 0，则查询优化器可以对包含 1 的数据行使用筛选查询。</span><span class="sxs-lookup"><span data-stu-id="05d9d-401">For example, if most of the values are 0, the query optimizer might use a filtered index for the data rows that contain 1.</span></span>  
  
####  <a name="use-included-columns-to-extend-nonclustered-indexes"></a><a name="Included_Columns"></a> <span data-ttu-id="05d9d-402">使用包含列扩展非聚集索引</span><span class="sxs-lookup"><span data-stu-id="05d9d-402">Use Included Columns to Extend Nonclustered Indexes</span></span>  

 <span data-ttu-id="05d9d-403">您可以通过将非键列添加到非聚集索引的叶级，扩展非聚集索引的功能。</span><span class="sxs-lookup"><span data-stu-id="05d9d-403">You can extend the functionality of nonclustered indexes by adding nonkey columns to the leaf level of the nonclustered index.</span></span> <span data-ttu-id="05d9d-404">通过包含非键列，可以创建覆盖更多查询的非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="05d9d-404">By including nonkey columns, you can create nonclustered indexes that cover more queries.</span></span> <span data-ttu-id="05d9d-405">这是因为非键列具有下列优点：</span><span class="sxs-lookup"><span data-stu-id="05d9d-405">This is because the nonkey columns have the following benefits:</span></span>  
  
-   <span data-ttu-id="05d9d-406">它们可以是不允许作为索引键列的数据类型。</span><span class="sxs-lookup"><span data-stu-id="05d9d-406">They can be data types not allowed as index key columns.</span></span>  
  
-   <span data-ttu-id="05d9d-407">在计算索引键列数或索引键大小时， [!INCLUDE[ssDE](../includes/ssde-md.md)] 不考虑它们。</span><span class="sxs-lookup"><span data-stu-id="05d9d-407">They are not considered by the [!INCLUDE[ssDE](../includes/ssde-md.md)] when calculating the number of index key columns or index key size.</span></span>  
  
 <span data-ttu-id="05d9d-408">当查询中的所有列都作为键列或非键列包含在索引中时，带有包含性非键列的索引可以显著提高查询性能。</span><span class="sxs-lookup"><span data-stu-id="05d9d-408">An index with included nonkey columns can significantly improve query performance when all columns in the query are included in the index either as key or nonkey columns.</span></span> <span data-ttu-id="05d9d-409">这样可以实现性能提升，因为查询优化器可以在索引中找到所有列值；不访问表或聚集索引数据，从而减少磁盘 I/O 操作。</span><span class="sxs-lookup"><span data-stu-id="05d9d-409">Performance gains are achieved because the query optimizer can locate all the column values within the index; table or clustered index data is not accessed resulting in fewer disk I/O operations.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="05d9d-410">当索引包含查询引用的所有列时，它通常称为“覆盖查询”。</span><span class="sxs-lookup"><span data-stu-id="05d9d-410">When an index contains all the columns referenced by the query it is typically referred to as covering the query.</span></span>  
  
 <span data-ttu-id="05d9d-411">键列存储在索引的所有级别中，而非键列仅存储在叶级别中。</span><span class="sxs-lookup"><span data-stu-id="05d9d-411">While key columns are stored at all levels of the index, nonkey columns are stored only at the leaf level.</span></span>  
  
##### <a name="using-included-columns-to-avoid-size-limits"></a><span data-ttu-id="05d9d-412">使用包含列以避免大小限制</span><span class="sxs-lookup"><span data-stu-id="05d9d-412">Using Included Columns to Avoid Size Limits</span></span>  

 <span data-ttu-id="05d9d-413">可以将非键列包含在非聚集索引中，以避免超过当前索引大小的限制（最大键列数为 16，最大索引键大小为 900 字节）。</span><span class="sxs-lookup"><span data-stu-id="05d9d-413">You can include nonkey columns in a nonclustered index to avoid exceeding the current index size limitations of a maximum of 16 key columns and a maximum index key size of 900 bytes.</span></span> <span data-ttu-id="05d9d-414">[!INCLUDE[ssDE](../includes/ssde-md.md)] 计算索引键列数或索引键大小时，不考虑非键列。</span><span class="sxs-lookup"><span data-stu-id="05d9d-414">The [!INCLUDE[ssDE](../includes/ssde-md.md)] does not consider nonkey columns when calculating the number of index key columns or index key size.</span></span>  
  
 <span data-ttu-id="05d9d-415">例如，假设要为 `Document` 表中的以下列建立索引：</span><span class="sxs-lookup"><span data-stu-id="05d9d-415">For example, assume that you want to index the following columns in the `Document` table:</span></span>  
  
 `Title nvarchar(50)`  
  
 `Revision nchar(5)`  
  
 `FileName nvarchar(400)`  
  
 <span data-ttu-id="05d9d-416">因为 `nchar` 和 `nvarchar` 数据类型的每个字符需要 2 个字节，所以包含这三列的索引将超出 900 字节的大小限制 10 个字节 (455 \* 2)。</span><span class="sxs-lookup"><span data-stu-id="05d9d-416">Because the `nchar` and `nvarchar` data types require 2 bytes for each character, an index that contains these three columns would exceed the 900 byte size limitation by 10 bytes (455 \* 2).</span></span> <span data-ttu-id="05d9d-417">使用 `INCLUDE` 语句的 `CREATE INDEX` 子句，可以将索引键定义为 (`Title, Revision`)，将 `FileName` 定义为非键列。</span><span class="sxs-lookup"><span data-stu-id="05d9d-417">By using the `INCLUDE` clause of the `CREATE INDEX` statement, the index key could be defined as (`Title, Revision`) and `FileName` defined as a nonkey column.</span></span> <span data-ttu-id="05d9d-418">这样，索引键大小将为 110 个字节 (55 \* 2)，并且索引仍将包含所需的所有列。</span><span class="sxs-lookup"><span data-stu-id="05d9d-418">In this way, the index key size would be 110 bytes (55 \* 2), and the index would still contain all the required columns.</span></span> <span data-ttu-id="05d9d-419">下面的语句就创建了这样的索引。</span><span class="sxs-lookup"><span data-stu-id="05d9d-419">The following statement creates such an index.</span></span>  
  
```sql
CREATE INDEX IX_Document_Title   
ON Production.Document (Title, Revision)   
INCLUDE (FileName);   
```  
  
##### <a name="index-with-included-columns-guidelines"></a><span data-ttu-id="05d9d-420">带有包含列的索引准则</span><span class="sxs-lookup"><span data-stu-id="05d9d-420">Index with Included Columns Guidelines</span></span>  

 <span data-ttu-id="05d9d-421">设计带有包含列的非聚集索引时，请考虑下列准则：</span><span class="sxs-lookup"><span data-stu-id="05d9d-421">When you design nonclustered indexes with included columns consider the following guidelines:</span></span>  
  
-   <span data-ttu-id="05d9d-422">在 CREATE INDEX 语句的 INCLUDE 子句中定义非键列。</span><span class="sxs-lookup"><span data-stu-id="05d9d-422">Nonkey columns are defined in the INCLUDE clause of the CREATE INDEX statement.</span></span>  
  
-   <span data-ttu-id="05d9d-423">只能对表或索引视图的非聚集索引定义非键列。</span><span class="sxs-lookup"><span data-stu-id="05d9d-423">Nonkey columns can only be defined on nonclustered indexes on tables or indexed views.</span></span>  
  
-   <span data-ttu-id="05d9d-424">除 `text`、`ntext` 和 `image` 之外，允许所有数据类型。</span><span class="sxs-lookup"><span data-stu-id="05d9d-424">All data types are allowed except `text`, `ntext`, and `image`.</span></span>  
  
-   <span data-ttu-id="05d9d-425">精确或不精确的确定性计算列都可以是包含列。</span><span class="sxs-lookup"><span data-stu-id="05d9d-425">Computed columns that are deterministic and either precise or imprecise can be included columns.</span></span> <span data-ttu-id="05d9d-426">有关详细信息，请参阅 [计算列上的索引](../relational-databases/indexes/indexes-on-computed-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="05d9d-426">For more information, see [Indexes on Computed Columns](../relational-databases/indexes/indexes-on-computed-columns.md).</span></span>  
  
-   <span data-ttu-id="05d9d-427">与键列一样，只要允许将计算列数据类型作为非键索引列，从 `image`、`ntext` 和 `text` 数据类型派生的计算列就可以作为非键（包含性）列。</span><span class="sxs-lookup"><span data-stu-id="05d9d-427">As with key columns, computed columns derived from `image`, `ntext`, and `text` data types can be nonkey (included) columns as long as the computed column data type is allowed as a nonkey index column.</span></span>  
  
-   <span data-ttu-id="05d9d-428">不能同时在 INCLUDE 列表和键列列表中指定列名。</span><span class="sxs-lookup"><span data-stu-id="05d9d-428">Column names cannot be specified in both the INCLUDE list and in the key column list.</span></span>  
  
-   <span data-ttu-id="05d9d-429">INCLUDE 列表中的列名不能重复。</span><span class="sxs-lookup"><span data-stu-id="05d9d-429">Column names cannot be repeated in the INCLUDE list.</span></span>  
  
##### <a name="column-size-guidelines"></a><span data-ttu-id="05d9d-430">列大小准则</span><span class="sxs-lookup"><span data-stu-id="05d9d-430">Column Size Guidelines</span></span>  
  
-   <span data-ttu-id="05d9d-431">必须至少定义一个键列。</span><span class="sxs-lookup"><span data-stu-id="05d9d-431">At least one key column must be defined.</span></span> <span data-ttu-id="05d9d-432">最大非键列数为 1023 列。</span><span class="sxs-lookup"><span data-stu-id="05d9d-432">The maximum number of nonkey columns is 1023 columns.</span></span> <span data-ttu-id="05d9d-433">也就是最大的表列数减 1。</span><span class="sxs-lookup"><span data-stu-id="05d9d-433">This is the maximum number of table columns minus 1.</span></span>  
  
-   <span data-ttu-id="05d9d-434">索引键列（不包括非键）必须遵守现有索引大小的限制（最大键列数为 16，总索引键大小为 900 字节）。</span><span class="sxs-lookup"><span data-stu-id="05d9d-434">Index key columns, excluding nonkeys, must follow the existing index size restrictions of 16 key columns maximum, and a total index key size of 900 bytes.</span></span>  
  
-   <span data-ttu-id="05d9d-435">所有非键列的总大小只受 INCLUDE 子句中所指定列的大小限制；例如，`varchar(max)` 列限制为 2 GB。</span><span class="sxs-lookup"><span data-stu-id="05d9d-435">The total size of all nonkey columns is limited only by the size of the columns specified in the INCLUDE clause; for example, `varchar(max)` columns are limited to 2 GB.</span></span>  
  
##### <a name="column-modification-guidelines"></a><span data-ttu-id="05d9d-436">列修改准则</span><span class="sxs-lookup"><span data-stu-id="05d9d-436">Column Modification Guidelines</span></span>  

 <span data-ttu-id="05d9d-437">修改已定义为包含列的表列时，要受下列限制：</span><span class="sxs-lookup"><span data-stu-id="05d9d-437">When you modify a table column that has been defined as an included column, the following restrictions apply:</span></span>  
  
-   <span data-ttu-id="05d9d-438">除非先删除索引，否则无法从表中删除非键列。</span><span class="sxs-lookup"><span data-stu-id="05d9d-438">Nonkey columns cannot be dropped from the table unless the index is dropped first.</span></span>  
  
-   <span data-ttu-id="05d9d-439">除进行下列更改外，不能对非键列进行其他更改：</span><span class="sxs-lookup"><span data-stu-id="05d9d-439">Nonkey columns cannot be changed, except to do the following:</span></span>  
  
    -   <span data-ttu-id="05d9d-440">将列的为空性从 NOT NULL 改为 NULL。</span><span class="sxs-lookup"><span data-stu-id="05d9d-440">Change the nullability of the column from NOT NULL to NULL.</span></span>  
  
    -   <span data-ttu-id="05d9d-441">增加 `varchar`、`nvarchar` 或 `varbinary` 列的长度。</span><span class="sxs-lookup"><span data-stu-id="05d9d-441">Increase the length of `varchar`, `nvarchar`, or `varbinary` columns.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="05d9d-442">这些列修改限制也适用于索引键列。</span><span class="sxs-lookup"><span data-stu-id="05d9d-442">These column modification restrictions also apply to index key columns.</span></span>  
  
##### <a name="design-recommendations"></a><span data-ttu-id="05d9d-443">设计建议</span><span class="sxs-lookup"><span data-stu-id="05d9d-443">Design Recommendations</span></span>  

 <span data-ttu-id="05d9d-444">重新设计索引键大小较大的非聚集索引，以便只有用于搜索和查找的列为键列。</span><span class="sxs-lookup"><span data-stu-id="05d9d-444">Redesign nonclustered indexes with a large index key size so that only columns used for searching and lookups are key columns.</span></span> <span data-ttu-id="05d9d-445">将覆盖查询的所有其他列设置为包含性非键列。</span><span class="sxs-lookup"><span data-stu-id="05d9d-445">Make all other columns that cover the query included nonkey columns.</span></span> <span data-ttu-id="05d9d-446">这样，将具有覆盖查询所需的所有列，但索引键本身较小，而且效率高。</span><span class="sxs-lookup"><span data-stu-id="05d9d-446">In this way, you will have all columns needed to cover the query, but the index key itself is small and efficient.</span></span>  
  
 <span data-ttu-id="05d9d-447">例如，假设要设计覆盖下列查询的索引。</span><span class="sxs-lookup"><span data-stu-id="05d9d-447">For example, assume that you want to design an index to cover the following query.</span></span>  
  
```sql
SELECT AddressLine1, AddressLine2, City, StateProvinceID, PostalCode  
FROM Person.Address  
WHERE PostalCode BETWEEN N'98000' and N'99999';  
```  
  
 <span data-ttu-id="05d9d-448">若要覆盖查询，必须在索引中定义每列。</span><span class="sxs-lookup"><span data-stu-id="05d9d-448">To cover the query, each column must be defined in the index.</span></span> <span data-ttu-id="05d9d-449">尽管可以将所有列定义为键列，但键大小为 334 字节。</span><span class="sxs-lookup"><span data-stu-id="05d9d-449">Although you could define all columns as key columns, the key size would be 334 bytes.</span></span> <span data-ttu-id="05d9d-450">因为实际上用作搜索条件的唯一列是 `PostalCode` 列（长度为 30 字节），所以更好的索引设计应该将 `PostalCode` 定义为键列并包含作为非键列的所有其他列。</span><span class="sxs-lookup"><span data-stu-id="05d9d-450">Because the only column actually used as search criteria is the `PostalCode` column, having a length of 30 bytes, a better index design would define `PostalCode` as the key column and include all other columns as nonkey columns.</span></span>  
  
 <span data-ttu-id="05d9d-451">下面的语句创建了一个覆盖查询的带有包含列的索引。</span><span class="sxs-lookup"><span data-stu-id="05d9d-451">The following statement creates an index with included columns to cover the query.</span></span>  
  
```sql
CREATE INDEX IX_Address_PostalCode  
ON Person.Address (PostalCode)  
INCLUDE (AddressLine1, AddressLine2, City, StateProvinceID);  
```  
  
##### <a name="performance-considerations"></a><span data-ttu-id="05d9d-452">性能注意事项</span><span class="sxs-lookup"><span data-stu-id="05d9d-452">Performance Considerations</span></span>  

 <span data-ttu-id="05d9d-453">避免添加不必要的列。</span><span class="sxs-lookup"><span data-stu-id="05d9d-453">Avoid adding unnecessary columns.</span></span> <span data-ttu-id="05d9d-454">添加过多的索引列（键列或非键列）会对性能产生下列影响：</span><span class="sxs-lookup"><span data-stu-id="05d9d-454">Adding too many index columns, key or nonkey, can have the following performance implications:</span></span>  
  
-   <span data-ttu-id="05d9d-455">一页上能容纳的索引行将更少。</span><span class="sxs-lookup"><span data-stu-id="05d9d-455">Fewer index rows will fit on a page.</span></span> <span data-ttu-id="05d9d-456">这样会使 I/O 增加并降低缓存效率。</span><span class="sxs-lookup"><span data-stu-id="05d9d-456">This could create I/O increases and reduced cache efficiency.</span></span>  
  
-   <span data-ttu-id="05d9d-457">需要更多的磁盘空间来存储索引。</span><span class="sxs-lookup"><span data-stu-id="05d9d-457">More disk space will be required to store the index.</span></span> <span data-ttu-id="05d9d-458">特别是，将 `varchar(max)`、`nvarchar(max)`、`varbinary(max)` 或 `xml` 数据类型添加为非键索引列会显著增加磁盘空间要求。</span><span class="sxs-lookup"><span data-stu-id="05d9d-458">In particular, adding `varchar(max)`, `nvarchar(max)`, `varbinary(max)`, or `xml` data types as nonkey index columns may significantly increase disk space requirements.</span></span> <span data-ttu-id="05d9d-459">这是因为列值被复制到了索引叶级别。</span><span class="sxs-lookup"><span data-stu-id="05d9d-459">This is because the column values are copied into the index leaf level.</span></span> <span data-ttu-id="05d9d-460">因此，它们既驻留在索引中，也驻留在基表中。</span><span class="sxs-lookup"><span data-stu-id="05d9d-460">Therefore, they reside in both the index and the base table.</span></span>  
  
-   <span data-ttu-id="05d9d-461">索引维护可能会增加对基础表或索引视图执行修改、插入、更新或删除操作所需的时间。</span><span class="sxs-lookup"><span data-stu-id="05d9d-461">Index maintenance may increase the time that it takes to perform modifications, inserts, updates, or deletes, to the underlying table or indexed view.</span></span>  
  
 <span data-ttu-id="05d9d-462">您应该确定修改数据时在查询性能上的提升是否超过了对性能的影响，以及是否需要额外的磁盘空间要求。</span><span class="sxs-lookup"><span data-stu-id="05d9d-462">You will have to determine whether the gains in query performance outweigh the affect to performance during data modification and in additional disk space requirements.</span></span>  
  
 <span data-ttu-id="05d9d-463">[本指南中与 "](#Top) ![返回页首" 链接一起使用的箭头图标](media/uparrow16x16.gif "用于返回页首链接的箭头图标")</span><span class="sxs-lookup"><span data-stu-id="05d9d-463">![Arrow icon used with Back to Top link](media/uparrow16x16.gif "Arrow icon used with Back to Top link") [In This Guide](#Top)</span></span>  
  
##  <a name="unique-index-design-guidelines"></a><a name="Unique"></a> <span data-ttu-id="05d9d-464">唯一索引设计指南</span><span class="sxs-lookup"><span data-stu-id="05d9d-464">Unique Index Design Guidelines</span></span>  

 <span data-ttu-id="05d9d-465">唯一索引能够保证索引键中不包含重复的值，从而使表中的每一行从某种方式上具有唯一性。</span><span class="sxs-lookup"><span data-stu-id="05d9d-465">A unique index guarantees that the index key contains no duplicate values and therefore every row in the table is in some way unique.</span></span> <span data-ttu-id="05d9d-466">只有当唯一性是数据本身的特征时，指定唯一索引才有意义。</span><span class="sxs-lookup"><span data-stu-id="05d9d-466">Specifying a unique index makes sense only when uniqueness is a characteristic of the data itself.</span></span> <span data-ttu-id="05d9d-467">例如，如果要确保 `NationalIDNumber` 表中 `HumanResources.Employee` 列的值是唯一的，当主键为 `EmployeeID`时，对 `NationalIDNumber` 列创建 UNIQUE 约束。</span><span class="sxs-lookup"><span data-stu-id="05d9d-467">For example, if you want to make sure that the values in the `NationalIDNumber` column in the `HumanResources.Employee` table are unique, when the primary key is `EmployeeID`, create a UNIQUE constraint on the `NationalIDNumber` column.</span></span> <span data-ttu-id="05d9d-468">如果用户尝试在该列中为多个雇员输入相同的值，将显示错误消息并且不能输入重复的值。</span><span class="sxs-lookup"><span data-stu-id="05d9d-468">If the user tries to enter the same value in that column for more than one employee, an error message is displayed and the duplicate value is not entered.</span></span>  
  
 <span data-ttu-id="05d9d-469">使用多列唯一索引，索引能够保证索引键中值的每个组合都是唯一的。</span><span class="sxs-lookup"><span data-stu-id="05d9d-469">With multicolumn unique indexes, the index guarantees that each combination of values in the index key is unique.</span></span> <span data-ttu-id="05d9d-470">例如，如果为 `LastName`、 `FirstName`和 `MiddleName` 列的组合创建了唯一索引，则表中的任意两行都不会有这些列值的相同组合。</span><span class="sxs-lookup"><span data-stu-id="05d9d-470">For example, if a unique index is created on a combination of `LastName`, `FirstName`, and `MiddleName` columns, no two rows in the table could have the same combination of values for these columns.</span></span>  
  
 <span data-ttu-id="05d9d-471">聚集索引和非聚集索引都可以是唯一的。</span><span class="sxs-lookup"><span data-stu-id="05d9d-471">Both clustered and nonclustered indexes can be unique.</span></span> <span data-ttu-id="05d9d-472">只要列中的数据是唯一的，就可以为同一个表创建一个唯一聚集索引和多个唯一非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="05d9d-472">Provided that the data in the column is unique, you can create both a unique clustered index and multiple unique nonclustered indexes on the same table.</span></span>  
  
 <span data-ttu-id="05d9d-473">唯一索引的优点包括下列几点：</span><span class="sxs-lookup"><span data-stu-id="05d9d-473">The benefits of unique indexes include the following:</span></span>  
  
-   <span data-ttu-id="05d9d-474">能够确保定义的列的数据完整性。</span><span class="sxs-lookup"><span data-stu-id="05d9d-474">Data integrity of the defined columns is ensured.</span></span>  
  
-   <span data-ttu-id="05d9d-475">提供了对查询优化器有用的附加信息。</span><span class="sxs-lookup"><span data-stu-id="05d9d-475">Additional information helpful to the query optimizer is provided.</span></span>  
  
 <span data-ttu-id="05d9d-476">创建 PRIMARY KEY 或 UNIQUE 约束会自动为指定的列创建唯一索引。</span><span class="sxs-lookup"><span data-stu-id="05d9d-476">Creating a PRIMARY KEY or UNIQUE constraint automatically creates a unique index on the specified columns.</span></span> <span data-ttu-id="05d9d-477">创建 UNIQUE 约束和创建独立于约束的唯一索引没有明显的区别。</span><span class="sxs-lookup"><span data-stu-id="05d9d-477">There are no significant differences between creating a UNIQUE constraint and creating a unique index independent of a constraint.</span></span> <span data-ttu-id="05d9d-478">数据验证的方式是相同的，而且查询优化器不会区分唯一索引是由约束创建的还是手动创建的。</span><span class="sxs-lookup"><span data-stu-id="05d9d-478">Data validation occurs in the same manner and the query optimizer does not differentiate between a unique index created by a constraint or manually created.</span></span> <span data-ttu-id="05d9d-479">但是，如果您的目的是要实现数据完整性，则应为列创建 UNIQUE 或 PRIMARY KEY 约束。</span><span class="sxs-lookup"><span data-stu-id="05d9d-479">However, you should create a UNIQUE or PRIMARY KEY constraint on the column when data integrity is the objective.</span></span> <span data-ttu-id="05d9d-480">这样做才能使索引的目标明确。</span><span class="sxs-lookup"><span data-stu-id="05d9d-480">By doing this the objective of the index will be clear.</span></span>  
  
### <a name="considerations"></a><span data-ttu-id="05d9d-481">注意事项</span><span class="sxs-lookup"><span data-stu-id="05d9d-481">Considerations</span></span>  
  
-   <span data-ttu-id="05d9d-482">如果数据中存在重复的键值，则不能创建唯一索引、UNIQUE 约束或 PRIMARY KEY 约束。</span><span class="sxs-lookup"><span data-stu-id="05d9d-482">A unique index, UNIQUE constraint, or PRIMARY KEY constraint cannot be created if duplicate key values exist in the data.</span></span>  
  
-   <span data-ttu-id="05d9d-483">如果数据是唯一的并且您希望强制实现唯一性，则为相同的列组合创建唯一索引而不是非唯一索引可以为查询优化器提供附加信息，从而生成更有效的执行计划。</span><span class="sxs-lookup"><span data-stu-id="05d9d-483">If the data is unique and you want uniqueness enforced, creating a unique index instead of a nonunique index on the same combination of columns provides additional information for the query optimizer that can produce more efficient execution plans.</span></span> <span data-ttu-id="05d9d-484">在这种情况下，建议创建唯一索引（最好通过创建 UNIQUE 约束来创建）。</span><span class="sxs-lookup"><span data-stu-id="05d9d-484">Creating a unique index (preferably by creating a UNIQUE constraint) is recommended in this case.</span></span>  
  
-   <span data-ttu-id="05d9d-485">唯一非聚集索引可以包括包含性非键列。</span><span class="sxs-lookup"><span data-stu-id="05d9d-485">A unique nonclustered index can contain included nonkey columns.</span></span> <span data-ttu-id="05d9d-486">有关详细信息，请参阅 [具有包含列的索引](#Included_Columns)。</span><span class="sxs-lookup"><span data-stu-id="05d9d-486">For more information, see [Index with Included Columns](#Included_Columns).</span></span>  
  
 <span data-ttu-id="05d9d-487">[本指南中与 "](#Top) ![返回页首" 链接一起使用的箭头图标](media/uparrow16x16.gif "用于返回页首链接的箭头图标")</span><span class="sxs-lookup"><span data-stu-id="05d9d-487">![Arrow icon used with Back to Top link](media/uparrow16x16.gif "Arrow icon used with Back to Top link") [In This Guide](#Top)</span></span>  
  
##  <a name="filtered-index-design-guidelines"></a><a name="Filtered"></a> <span data-ttu-id="05d9d-488">筛选索引设计指南</span><span class="sxs-lookup"><span data-stu-id="05d9d-488">Filtered Index Design Guidelines</span></span>  

 <span data-ttu-id="05d9d-489">筛选索引是一种经过优化的非聚集索引，尤其适用于涵盖从定义完善的数据子集中选择数据的查询。</span><span class="sxs-lookup"><span data-stu-id="05d9d-489">A filtered index is an optimized nonclustered index, especially suited to cover queries that select from a well-defined subset of data.</span></span> <span data-ttu-id="05d9d-490">筛选索引使用筛选谓词对表中的部分行进行索引。</span><span class="sxs-lookup"><span data-stu-id="05d9d-490">It uses a filter predicate to index a portion of rows in the table.</span></span> <span data-ttu-id="05d9d-491">与全表索引相比，设计良好的筛选索引可以提高查询性能、减少索引维护开销并可降低索引存储开销。</span><span class="sxs-lookup"><span data-stu-id="05d9d-491">A well-designed filtered index can improve query performance, reduce index maintenance costs, and reduce index storage costs compared with full-table indexes.</span></span>  
  
||  
|-|  
|<span data-ttu-id="05d9d-492">**适用范围**： [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] 到 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="05d9d-492">**Applies to**: [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] through [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span>|  
  
 <span data-ttu-id="05d9d-493">筛选索引与全表索引相比具有以下优点：</span><span class="sxs-lookup"><span data-stu-id="05d9d-493">Filtered indexes can provide the following advantages over full-table indexes:</span></span>  
  
-   <span data-ttu-id="05d9d-494">**提高了查询性能和计划质量**</span><span class="sxs-lookup"><span data-stu-id="05d9d-494">**Improved query performance and plan quality**</span></span>  
  
     <span data-ttu-id="05d9d-495">设计良好的筛选索引可以提高查询性能和执行计划质量，因为它比全表非聚集索引小并且具有经过筛选的统计信息。</span><span class="sxs-lookup"><span data-stu-id="05d9d-495">A well-designed filtered index improves query performance and execution plan quality because it is smaller than a full-table nonclustered index and has filtered statistics.</span></span> <span data-ttu-id="05d9d-496">与全表统计信息相比，经过筛选的统计信息更加准确，因为它们只涵盖筛选索引中的行。</span><span class="sxs-lookup"><span data-stu-id="05d9d-496">The filtered statistics are more accurate than full-table statistics because they cover only the rows in the filtered index.</span></span>  
  
-   <span data-ttu-id="05d9d-497">**减少了索引维护开销**</span><span class="sxs-lookup"><span data-stu-id="05d9d-497">**Reduced index maintenance costs**</span></span>  
  
     <span data-ttu-id="05d9d-498">仅在数据操作语言 (DML) 语句对索引中的数据产生影响时，才对索引进行维护。</span><span class="sxs-lookup"><span data-stu-id="05d9d-498">An index is maintained only when data manipulation language (DML) statements affect the data in the index.</span></span> <span data-ttu-id="05d9d-499">与全表非聚集索引相比，筛选索引减少了索引维护开销，因为它更小并且仅在对索引中的数据产生影响时才进行维护。</span><span class="sxs-lookup"><span data-stu-id="05d9d-499">A filtered index reduces index maintenance costs compared with a full-table nonclustered index because it is smaller and is only maintained when the data in the index is affected.</span></span> <span data-ttu-id="05d9d-500">筛选索引的数量可以非常多，特别是在其中包含很少受影响的数据时。</span><span class="sxs-lookup"><span data-stu-id="05d9d-500">It is possible to have a large number of filtered indexes, especially when they contain data that is affected infrequently.</span></span> <span data-ttu-id="05d9d-501">同样，如果筛选索引只包含频繁受影响的数据，则索引大小较小时可以减少更新统计信息的开销。</span><span class="sxs-lookup"><span data-stu-id="05d9d-501">Similarly, if a filtered index contains only the frequently affected data, the smaller size of the index reduces the cost of updating the statistics.</span></span>  
  
-   <span data-ttu-id="05d9d-502">**减少了索引存储开销**</span><span class="sxs-lookup"><span data-stu-id="05d9d-502">**Reduced index storage costs**</span></span>  
  
     <span data-ttu-id="05d9d-503">在没必要创建全表索引时，创建筛选索引可以减少非聚集索引的磁盘存储开销。</span><span class="sxs-lookup"><span data-stu-id="05d9d-503">Creating a filtered index can reduce disk storage for nonclustered indexes when a full-table index is not necessary.</span></span> <span data-ttu-id="05d9d-504">可以使用多个筛选索引替换一个全表非聚集索引而不会明显增加存储需求。</span><span class="sxs-lookup"><span data-stu-id="05d9d-504">You can replace a full-table nonclustered index with multiple filtered indexes without significantly increasing the storage requirements.</span></span>  
  
 <span data-ttu-id="05d9d-505">列中包含查询在 SELECT 语句中引用的定义完善的数据子集时，筛选索引很有用。</span><span class="sxs-lookup"><span data-stu-id="05d9d-505">Filtered indexes are useful when columns contain well-defined subsets of data that queries reference in SELECT statements.</span></span> <span data-ttu-id="05d9d-506">示例如下：</span><span class="sxs-lookup"><span data-stu-id="05d9d-506">Examples are:</span></span>  
  
-   <span data-ttu-id="05d9d-507">仅包含少量非 NULL 值的稀疏列。</span><span class="sxs-lookup"><span data-stu-id="05d9d-507">Sparse columns that contain only a few non-NULL values.</span></span>  
  
-   <span data-ttu-id="05d9d-508">包含多种类别的数据的异类列。</span><span class="sxs-lookup"><span data-stu-id="05d9d-508">Heterogeneous columns that contain categories of data.</span></span>  
  
-   <span data-ttu-id="05d9d-509">包含多个范围的值（如美元金额、时间和日期）的列。</span><span class="sxs-lookup"><span data-stu-id="05d9d-509">Columns that contain ranges of values such as dollar amounts, time, and dates.</span></span>  
  
-   <span data-ttu-id="05d9d-510">由列值的简单比较逻辑定义的表分区。</span><span class="sxs-lookup"><span data-stu-id="05d9d-510">Table partitions that are defined by simple comparison logic for column values.</span></span>  
  
 <span data-ttu-id="05d9d-511">如果索引中的行数与全表索引相比较少时，筛选索引减少的维护开销最为明显。</span><span class="sxs-lookup"><span data-stu-id="05d9d-511">Reduced maintenance costs for filtered indexes are most noticeable when the number of rows in the index is small compared with a full-table index.</span></span> <span data-ttu-id="05d9d-512">如果筛选索引包含表中的大部分行，则与全表索引相比，其维护开销可能更高。</span><span class="sxs-lookup"><span data-stu-id="05d9d-512">If the filtered index includes most of the rows in the table, it could cost more to maintain than a full-table index.</span></span> <span data-ttu-id="05d9d-513">在这种情况下，应使用全表索引而不是筛选索引。</span><span class="sxs-lookup"><span data-stu-id="05d9d-513">In this case, you should use a full-table index instead of a filtered index.</span></span>  
  
 <span data-ttu-id="05d9d-514">筛选索引是针对一个表定义的，仅支持简单比较运算符。</span><span class="sxs-lookup"><span data-stu-id="05d9d-514">Filtered indexes are defined on one table and only support simple comparison operators.</span></span> <span data-ttu-id="05d9d-515">如果需要引用多个表或具有复杂逻辑的筛选表达式，则应创建视图。</span><span class="sxs-lookup"><span data-stu-id="05d9d-515">If you need a filter expression that references multiple tables or has complex logic, you should create a view.</span></span>  
  
### <a name="design-considerations"></a><span data-ttu-id="05d9d-516">设计注意事项</span><span class="sxs-lookup"><span data-stu-id="05d9d-516">Design Considerations</span></span>  

 <span data-ttu-id="05d9d-517">为了设计有效的筛选索引，必须了解应用程序使用哪些查询以及这些查询与您的数据子集有何关联。</span><span class="sxs-lookup"><span data-stu-id="05d9d-517">In order to design effective filtered indexes, it is important to understand what queries your application uses and how they relate to subsets of your data.</span></span> <span data-ttu-id="05d9d-518">例如，所含值中大部分为 NULL 的列、含异类类别的值的列以及含不同范围的值的列都属于具有定义完善的子集的数据。</span><span class="sxs-lookup"><span data-stu-id="05d9d-518">Some examples of data that have well-defined subsets are columns with mostly NULL values, columns with heterogeneous categories of values and columns with distinct ranges of values.</span></span> <span data-ttu-id="05d9d-519">以下设计注意事项提供了筛选索引优于全表索引的各种情况。</span><span class="sxs-lookup"><span data-stu-id="05d9d-519">The following design considerations give a variety of scenarios for when a filtered index can provide advantages over full-table indexes.</span></span>  
  
#### <a name="filtered-indexes-for-subsets-of-data"></a><span data-ttu-id="05d9d-520">数据子集的筛选索引</span><span class="sxs-lookup"><span data-stu-id="05d9d-520">Filtered Indexes for Subsets of Data</span></span>  

 <span data-ttu-id="05d9d-521">在列中只有少量相关值需要查询时，可以针对值的子集创建筛选索引。</span><span class="sxs-lookup"><span data-stu-id="05d9d-521">When a column only has a small number of relevant values for queries, you can create a filtered index on the subset of values.</span></span> <span data-ttu-id="05d9d-522">例如，当列中的值大部分为 NULL 并且查询只从非 NULL 值中进行选择时，可以为非 NULL 数据行创建筛选索引。</span><span class="sxs-lookup"><span data-stu-id="05d9d-522">For example, when the values in a column are mostly NULL and the query selects only from the non-NULL values, you can create a filtered index for the non-NULL data rows.</span></span> <span data-ttu-id="05d9d-523">由此得到的索引与对相同键列定义的全表非聚集索引相比，前者更小且维护开销更低。</span><span class="sxs-lookup"><span data-stu-id="05d9d-523">The resulting index will be smaller and cost less to maintain than a full-table nonclustered index defined on the same key columns.</span></span>  
  
 <span data-ttu-id="05d9d-524">例如， `AdventureWorks2012` 数据库中有一个包含了 2679 行的 `Production.BillOfMaterials` 表。</span><span class="sxs-lookup"><span data-stu-id="05d9d-524">For example, the `AdventureWorks2012` database has a `Production.BillOfMaterials` table with 2679 rows.</span></span> <span data-ttu-id="05d9d-525">`EndDate` 列只有 199 行包含非 NULL 值，其他的 2480 行均包含 NULL。</span><span class="sxs-lookup"><span data-stu-id="05d9d-525">The `EndDate` column has only 199 rows that contain a non-NULL value and the other 2480 rows contain NULL.</span></span> <span data-ttu-id="05d9d-526">下面的筛选索引将涵盖这样的查询：返回在该索引中定义的列的查询，以及只选择 `EndDate`中具有非 NULL 值的行的查询。</span><span class="sxs-lookup"><span data-stu-id="05d9d-526">The following filtered index would cover queries that return the columns defined in the index and that select only rows with a non-NULL value for `EndDate`.</span></span>  
  
```sql
CREATE NONCLUSTERED INDEX FIBillOfMaterialsWithEndDate  
    ON Production.BillOfMaterials (ComponentID, StartDate)  
    WHERE EndDate IS NOT NULL ;  
GO  
```  
  
 <span data-ttu-id="05d9d-527">筛选索引 `FIBillOfMaterialsWithEndDate` 对下面的查询有效。</span><span class="sxs-lookup"><span data-stu-id="05d9d-527">The filtered index `FIBillOfMaterialsWithEndDate` is valid for the following query.</span></span> <span data-ttu-id="05d9d-528">您可以显示查询执行计划，以确定查询优化器是否使用了该筛选索引。</span><span class="sxs-lookup"><span data-stu-id="05d9d-528">You can display the query execution plan to determine if the query optimizer used the filtered index.</span></span>  
  
```sql
SELECT ProductAssemblyID, ComponentID, StartDate   
FROM Production.BillOfMaterials  
WHERE EndDate IS NOT NULL   
    AND ComponentID = 5   
    AND StartDate > '20080101' ;  
```  
  
 <span data-ttu-id="05d9d-529">有关如何创建筛选索引以及如何定义筛选索引谓词表达式的详细信息，请参阅 [创建筛选索引](../relational-databases/indexes/create-filtered-indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="05d9d-529">For more information about how to create filtered indexes and how to define the filtered index predicate expression, see [Create Filtered Indexes](../relational-databases/indexes/create-filtered-indexes.md).</span></span>  
  
#### <a name="filtered-indexes-for-heterogeneous-data"></a><span data-ttu-id="05d9d-530">异类数据的筛选索引</span><span class="sxs-lookup"><span data-stu-id="05d9d-530">Filtered Indexes for Heterogeneous Data</span></span>  

 <span data-ttu-id="05d9d-531">表中含有异类数据行时，可以为一种或多种类别的数据创建筛选索引。</span><span class="sxs-lookup"><span data-stu-id="05d9d-531">When a table has heterogeneous data rows, you can create a filtered index for one or more categories of data.</span></span>  
  
 <span data-ttu-id="05d9d-532">例如，为 `Production.Product` 表中列出的每种产品均分配了一个 `ProductSubcategoryID`，后者又与 Bikes、Components、Clothing 或 Accessories 产品类别相关联。</span><span class="sxs-lookup"><span data-stu-id="05d9d-532">For example, the products listed in the `Production.Product` table are each assigned to a `ProductSubcategoryID`, which are in turn associated with the product categories Bikes, Components, Clothing, or Accessories.</span></span> <span data-ttu-id="05d9d-533">这些类别是异类类别，因为它们在 `Production.Product` 表中的列值并不是紧密相关的。</span><span class="sxs-lookup"><span data-stu-id="05d9d-533">These categories are heterogeneous because their column values in the `Production.Product` table are not closely correlated.</span></span> <span data-ttu-id="05d9d-534">例如，对于每种产品类别，列 `Color`、 `ReorderPoint`、 `ListPrice`、 `Weight`、 `Class`和 `Style` 均具有唯一特征。</span><span class="sxs-lookup"><span data-stu-id="05d9d-534">For example, the columns `Color`, `ReorderPoint`, `ListPrice`, `Weight`, `Class`, and `Style` have unique characteristics for each product category.</span></span> <span data-ttu-id="05d9d-535">假设会经常查询具有子类别 27-36（包含端点）的 Accessories。</span><span class="sxs-lookup"><span data-stu-id="05d9d-535">Suppose that there are frequent queries for accessories which have subcategories between 27 and 36 inclusive.</span></span> <span data-ttu-id="05d9d-536">通过对 Accessories 子类别创建筛选索引，可以提高对 Accessories 的查询的性能，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="05d9d-536">You can improve the performance of queries for accessories by creating a filtered index on the accessories subcategories as shown in the following example.</span></span>  
  
```sql
CREATE NONCLUSTERED INDEX FIProductAccessories  
    ON Production.Product (ProductSubcategoryID, ListPrice)   
        Include (Name)  
WHERE ProductSubcategoryID >= 27 AND ProductSubcategoryID <= 36;
```  
  
 <span data-ttu-id="05d9d-537">筛选索引 `FIProductAccessories` 涵盖下面的查询，因为查询</span><span class="sxs-lookup"><span data-stu-id="05d9d-537">The filtered index `FIProductAccessories` covers the following query because the query</span></span>  
  
 <span data-ttu-id="05d9d-538">结果包含在该索引中，并且查询计划不包括基表查找。</span><span class="sxs-lookup"><span data-stu-id="05d9d-538">results are contained in the index and the query plan does not include a base table lookup.</span></span> <span data-ttu-id="05d9d-539">例如，查询谓词表达式 `ProductSubcategoryID = 33` 是筛选索引谓词 `ProductSubcategoryID >= 27` 和 `ProductSubcategoryID <= 36`的子集，查询谓词中的 `ProductSubcategoryID` 和 `ListPrice` 列全都是索引中的键列，并且名称作为包含列存储在索引的叶级别。</span><span class="sxs-lookup"><span data-stu-id="05d9d-539">For example, the query predicate expression `ProductSubcategoryID = 33` is a subset of the filtered index predicate `ProductSubcategoryID >= 27` and `ProductSubcategoryID <= 36`, the `ProductSubcategoryID` and `ListPrice` columns in the query predicate are both key columns in the index, and name is stored in the leaf level of the index as an included column.</span></span>  
  
```sql
SELECT Name, ProductSubcategoryID, ListPrice  
FROM Production.Product  
WHERE ProductSubcategoryID = 33 AND ListPrice > 25.00 ;  
```  
  
#### <a name="key-columns"></a><span data-ttu-id="05d9d-540">键列</span><span class="sxs-lookup"><span data-stu-id="05d9d-540">Key Columns</span></span>  

 <span data-ttu-id="05d9d-541">最好在筛选索引定义中包含少量的键或包含列，并且只包含查询优化器为查询执行计划选择筛选索引所需的列。</span><span class="sxs-lookup"><span data-stu-id="05d9d-541">It is a best practice to include a small number of key or included columns in a filtered index definition, and to incorporate only the columns that are necessary for the query optimizer to choose the filtered index for the query execution plan.</span></span> <span data-ttu-id="05d9d-542">无论某一筛选索引是否涵盖了查询，查询优化器都可以为查询选择此筛选索引。</span><span class="sxs-lookup"><span data-stu-id="05d9d-542">The query optimizer can choose a filtered index for the query regardless of whether it does or does not cover the query.</span></span> <span data-ttu-id="05d9d-543">但是，如果某一筛选索引涵盖了查询，则查询优化器更有可能选择此筛选索引。</span><span class="sxs-lookup"><span data-stu-id="05d9d-543">However, the query optimizer is more likely to choose a filtered index if it covers the query.</span></span>  
  
 <span data-ttu-id="05d9d-544">在某些情况下，筛选索引涵盖查询，但没有将筛选索引表达式中的列作为键或包含列包括在筛选索引定义中。</span><span class="sxs-lookup"><span data-stu-id="05d9d-544">In some cases, a filtered index covers the query without including the columns in the filtered index expression as key or included columns in the filtered index definition.</span></span> <span data-ttu-id="05d9d-545">以下准则说明了筛选索引表达式中的列何时应为筛选索引定义中的键或包含列。</span><span class="sxs-lookup"><span data-stu-id="05d9d-545">The following guidelines explain when a column in the filtered index expression should be a key or included column in the filtered index definition.</span></span> <span data-ttu-id="05d9d-546">这些示例引用了此前创建的筛选索引 `FIBillOfMaterialsWithEndDate` 。</span><span class="sxs-lookup"><span data-stu-id="05d9d-546">The examples refer to the filtered index, `FIBillOfMaterialsWithEndDate` that was created previously.</span></span>  
  
 <span data-ttu-id="05d9d-547">如果筛选索引表达式等效于查询谓词并且查询并未在查询结果中返回筛选索引表达式中的列，则筛选索引表达式中的列不需要作为筛选索引定义中的键或包含列。</span><span class="sxs-lookup"><span data-stu-id="05d9d-547">A column in the filtered index expression does not need to be a key or included column in the filtered index definition if the filtered index expression is equivalent to the query predicate and the query does not return the column in the filtered index expression with the query results.</span></span> <span data-ttu-id="05d9d-548">例如， `FIBillOfMaterialsWithEndDate` 涵盖下面的查询，因为查询谓词等效于筛选表达式，并且查询结果中未返回 `EndDate` 。</span><span class="sxs-lookup"><span data-stu-id="05d9d-548">For example, `FIBillOfMaterialsWithEndDate` covers the following query because the query predicate is equivalent to the filter expression, and `EndDate` is not returned with the query results.</span></span> <span data-ttu-id="05d9d-549">`FIBillOfMaterialsWithEndDate` 不需要将 `EndDate` 作为筛选索引定义中的键或包含列。</span><span class="sxs-lookup"><span data-stu-id="05d9d-549">`FIBillOfMaterialsWithEndDate` does not need `EndDate` as a key or included column in the filtered index definition.</span></span>  
  
```sql
SELECT ComponentID, StartDate FROM Production.BillOfMaterials  
WHERE EndDate IS NOT NULL;   
```  
  
 <span data-ttu-id="05d9d-550">如果查询谓词在不与筛选索引表达式等效的比较中使用了筛选索引表达式中的某列，则该列应为筛选索引定义中的键或包含列。</span><span class="sxs-lookup"><span data-stu-id="05d9d-550">A column in the filtered index expression should be a key or included column in the filtered index definition if the query predicate uses the column in a comparison that is not equivalent to the filtered index expression.</span></span> <span data-ttu-id="05d9d-551">例如， `FIBillOfMaterialsWithEndDate` 对下面的查询有效，因为它从筛选索引中选择了行的子集。</span><span class="sxs-lookup"><span data-stu-id="05d9d-551">For example, `FIBillOfMaterialsWithEndDate` is valid for the following query because it selects a subset of rows from the filtered index.</span></span> <span data-ttu-id="05d9d-552">但是，它不涵盖下面的查询，因为在比较 `EndDate` 中使用了 `EndDate > '20040101'`，此比较不与筛选索引表达式等效。</span><span class="sxs-lookup"><span data-stu-id="05d9d-552">However, it does not cover the following query because `EndDate` is used in the comparison `EndDate > '20040101'`, which is not equivalent to the filtered index expression.</span></span> <span data-ttu-id="05d9d-553">查询处理器在不查找 `EndDate`值的情况下无法执行此查询。</span><span class="sxs-lookup"><span data-stu-id="05d9d-553">The query processor cannot execute this query without looking up the values of `EndDate`.</span></span> <span data-ttu-id="05d9d-554">因此， `EndDate` 应为筛选索引定义中的键或包含列。</span><span class="sxs-lookup"><span data-stu-id="05d9d-554">Therefore, `EndDate` should be a key or included column in the filtered index definition.</span></span>  
  
```sql
SELECT ComponentID, StartDate FROM Production.BillOfMaterials  
WHERE EndDate > '20040101';   
```  
  
 <span data-ttu-id="05d9d-555">如果筛选索引表达式中的某列在查询结果集中，则该列应为筛选索引定义中的键或包含列。</span><span class="sxs-lookup"><span data-stu-id="05d9d-555">A column in the filtered index expression should be a key or included column in the filtered index definition if the column is in the query result set.</span></span> <span data-ttu-id="05d9d-556">例如， `FIBillOfMaterialsWithEndDate` 不涵盖下面的查询，因为它在查询结果中返回了 `EndDate` 列。</span><span class="sxs-lookup"><span data-stu-id="05d9d-556">For example, `FIBillOfMaterialsWithEndDate` does not cover the following query because it returns the `EndDate` column in the query results.</span></span> <span data-ttu-id="05d9d-557">因此， `EndDate` 应为筛选索引定义中的键或包含列。</span><span class="sxs-lookup"><span data-stu-id="05d9d-557">Therefore, `EndDate` should be a key or included column in the filtered index definition.</span></span>  
  
```sql
SELECT ComponentID, StartDate, EndDate FROM Production.BillOfMaterials  
WHERE EndDate IS NOT NULL;  
```  
  
 <span data-ttu-id="05d9d-558">表的聚集索引键不需要是筛选索引定义中的键或包含列。</span><span class="sxs-lookup"><span data-stu-id="05d9d-558">The clustered index key of the table does not need to be a key or included column in the filtered index definition.</span></span> <span data-ttu-id="05d9d-559">聚集索引键自动包含在所有非聚集索引（包括筛选索引）中。</span><span class="sxs-lookup"><span data-stu-id="05d9d-559">The clustered index key is automatically included in all nonclustered indexes, including filtered indexes.</span></span>  
  
#### <a name="data-conversion-operators-in-the-filter-predicate"></a><span data-ttu-id="05d9d-560">筛选谓词中的数据转换运算符</span><span class="sxs-lookup"><span data-stu-id="05d9d-560">Data Conversion Operators in the Filter Predicate</span></span>  

 <span data-ttu-id="05d9d-561">如果筛选索引结果的筛选索引表达式中指定的比较运算符会导致隐式或显式数据转换，则转换发生在比较运算符的左边时，会出现错误。</span><span class="sxs-lookup"><span data-stu-id="05d9d-561">If the comparison operator specified in the filtered index expression of the filtered index results in an implicit or explicit data conversion, an error will occur if the conversion occurs on the left side of a comparison operator.</span></span> <span data-ttu-id="05d9d-562">解决方法是在比较运算符的右边编写包含数据转换运算符（CAST 或 CONVERT）的筛选索引表达式。</span><span class="sxs-lookup"><span data-stu-id="05d9d-562">A solution is to write the filtered index expression with the data conversion operator (CAST or CONVERT) on the right side of the comparison operator.</span></span>  
  
 <span data-ttu-id="05d9d-563">下面的示例创建一个包含多种数据类型的表。</span><span class="sxs-lookup"><span data-stu-id="05d9d-563">The following example creates a table with a variety of data types.</span></span>  
  
```sql
USE AdventureWorks2012;  
GO  
CREATE TABLE dbo.TestTable (a int, b varbinary(4));  
```  
  
 <span data-ttu-id="05d9d-564">在下面的筛选索引定义中，列 `b` 隐式转换为整数数据类型，以便与常量 1 进行比较。</span><span class="sxs-lookup"><span data-stu-id="05d9d-564">In the following filtered index definition, column `b` is implicitly converted to an integer data type for the purpose of comparing it to the constant 1.</span></span> <span data-ttu-id="05d9d-565">因为转换发生在筛选谓词中运算符的左边，所以这会生成错误消息 10611。</span><span class="sxs-lookup"><span data-stu-id="05d9d-565">This generates error message 10611 because the conversion occurs on the left hand side of the operator in the filtered predicate.</span></span>  
  
```sql
CREATE NONCLUSTERED INDEX TestTabIndex ON dbo.TestTable(a,b)  
WHERE b = 1;  
```  
  
 <span data-ttu-id="05d9d-566">解决方法是将右侧的常量转换为与列 `b`的类型相同的类型，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="05d9d-566">The solution is to convert the constant on the right hand side to be of the same type as column `b`, as seen in the following example:</span></span>  
  
```sql
CREATE INDEX TestTabIndex ON dbo.TestTable(a,b)  
WHERE b = CONVERT(Varbinary(4), 1);  
```  
  
 <span data-ttu-id="05d9d-567">将数据转换从比较运算符的左边移动到右边可能会改变转换的含义。</span><span class="sxs-lookup"><span data-stu-id="05d9d-567">Moving the data conversion from the left side to the right side of a comparison operator might change the meaning of the conversion.</span></span> <span data-ttu-id="05d9d-568">在上例中，将 CONVERT 运算符添加到右边时，相应的比较从整数比较更改为 `varbinary` 比较。</span><span class="sxs-lookup"><span data-stu-id="05d9d-568">In the above example, when the CONVERT operator was added to the right side, the comparison changed from an integer comparison to a `varbinary` comparison.</span></span>  
  
 <span data-ttu-id="05d9d-569">[本指南中与 "](#Top) ![返回页首" 链接一起使用的箭头图标](media/uparrow16x16.gif "用于返回页首链接的箭头图标")</span><span class="sxs-lookup"><span data-stu-id="05d9d-569">![Arrow icon used with Back to Top link](media/uparrow16x16.gif "Arrow icon used with Back to Top link") [In This Guide](#Top)</span></span>  
  
##  <a name="additional-reading"></a><a name="Additional_Reading"></a> <span data-ttu-id="05d9d-570">其他阅读主题</span><span class="sxs-lookup"><span data-stu-id="05d9d-570">Additional Reading</span></span>  

 <span data-ttu-id="05d9d-571">[使用 SQL Server 2008 索引视图提高性能](https://msdn.microsoft.com/library/dd171921(v=sql.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="05d9d-571">[Improving Performance with SQL Server 2008 Indexed Views](https://msdn.microsoft.com/library/dd171921(v=sql.100).aspx)</span></span>  
  
 [<span data-ttu-id="05d9d-572">Partitioned Tables and Indexes</span><span class="sxs-lookup"><span data-stu-id="05d9d-572">Partitioned Tables and Indexes</span></span>](../relational-databases/partitions/partitioned-tables-and-indexes.md)  
  
  
