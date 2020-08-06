---
title: 使用聚集列存储索引 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
ms.assetid: 5af6b91c-724f-45ac-aff1-7555014914f4
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: afc7da4e28ef7f32ca4a2b4ea762e5a5af442471
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577784"
---
# <a name="using-clustered-columnstore-indexes"></a><span data-ttu-id="a2ce8-102">使用聚集列存储索引</span><span class="sxs-lookup"><span data-stu-id="a2ce8-102">Using Clustered Columnstore Indexes</span></span>
  <span data-ttu-id="a2ce8-103">用于在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 中使用聚集列存储索引的任务。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-103">Tasks for using clustered columnstore indexes in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>

 <span data-ttu-id="a2ce8-104">有关列存储索引的概述，请参阅 [Columnstore Indexes Described](../relational-databases/indexes/columnstore-indexes-described.md)。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-104">For an overview of columnstore indexes, see [Columnstore Indexes Described](../relational-databases/indexes/columnstore-indexes-described.md).</span></span>

 <span data-ttu-id="a2ce8-105">有关聚集列存储索引的信息，请参阅 [Using Clustered Columnstore Indexes](../relational-databases/indexes/indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-105">For information about clustered columnstore indexes, see [Using Clustered Columnstore Indexes](../relational-databases/indexes/indexes.md).</span></span>

## <a name="contents"></a><span data-ttu-id="a2ce8-106">目录</span><span class="sxs-lookup"><span data-stu-id="a2ce8-106">Contents</span></span>

-   [<span data-ttu-id="a2ce8-107">创建聚集列存储索引</span><span class="sxs-lookup"><span data-stu-id="a2ce8-107">Create a Clustered Columnstore Index</span></span>](#create)

-   [<span data-ttu-id="a2ce8-108">删除聚集列存储索引</span><span class="sxs-lookup"><span data-stu-id="a2ce8-108">Drop a Clustered Columnstore Index</span></span>](#drop)

-   [<span data-ttu-id="a2ce8-109">将数据加载到聚集列存储索引中</span><span class="sxs-lookup"><span data-stu-id="a2ce8-109">Load Data into a Clustered Columnstore Index</span></span>](#load)

-   [<span data-ttu-id="a2ce8-110">更改聚集列存储索引中的数据</span><span class="sxs-lookup"><span data-stu-id="a2ce8-110">Change Data in a Clustered Columnstore Index</span></span>](#change)

-   [<span data-ttu-id="a2ce8-111">重新生成聚集列存储索引</span><span class="sxs-lookup"><span data-stu-id="a2ce8-111">Rebuild a Clustered Columnstore Index</span></span>](#rebuild)

-   [<span data-ttu-id="a2ce8-112">重新组织聚集列存储索引</span><span class="sxs-lookup"><span data-stu-id="a2ce8-112">Reorganize a Clustered Columnstore Index</span></span>](#reorganize)

##  <a name="create-a-clustered-columnstore-index"></a><a name="create"></a><span data-ttu-id="a2ce8-113">创建聚集列存储索引</span><span class="sxs-lookup"><span data-stu-id="a2ce8-113">Create a Clustered Columnstore Index</span></span>
 <span data-ttu-id="a2ce8-114">若要创建聚集列存储索引，请先创建一个行存储表作为堆或聚集索引，然后使用[CREATE 聚集列存储索引 &#40;transact-sql&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql)语句将该表转换为聚集列存储索引。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-114">To create a clustered columnstore index, first create a rowstore table as a heap or clustered index, and then use the [CREATE CLUSTERED COLUMNSTORE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql) statement to convert the table to a clustered columnstore index.</span></span> <span data-ttu-id="a2ce8-115">如果您想要让该聚集列存储索引具有与聚集索引相同的名称，则使用 DROP_EXISTING 选项。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-115">If you want the clustered columnstore index to have the same name as the clustered index, use the DROP_EXISTING option.</span></span>

 <span data-ttu-id="a2ce8-116">此示例将一个表作为堆创建，然后将其转换为名为 cci_Simple 的聚集列存储索引。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-116">This example creates a table as a heap and then converts it to a clustered columnstore index named cci_Simple.</span></span> <span data-ttu-id="a2ce8-117">这会将整个表的存储从行存储转换为列存储。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-117">This changes the storage for the entire table from rowstore to columnstore.</span></span>

```
CREATE TABLE T1(
    ProductKey [int] NOT NULL, 
    OrderDateKey [int] NOT NULL, 
    DueDateKey [int] NOT NULL, 
    ShipDateKey [int] NOT NULL);
GO
CREATE CLUSTERED COLUMNSTORE INDEX cci_T1 ON T1;
GO
```

 <span data-ttu-id="a2ce8-118">有关更多示例，请参阅[CREATE 聚集列存储索引 &#40;transact-sql&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql)中的 "示例" 部分。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-118">For more examples, see the Examples section in [CREATE CLUSTERED COLUMNSTORE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql).</span></span>

##  <a name="drop-a-clustered-columnstore-index"></a><a name="drop"></a><span data-ttu-id="a2ce8-119">删除聚集列存储索引</span><span class="sxs-lookup"><span data-stu-id="a2ce8-119">Drop a Clustered Columnstore Index</span></span>
 <span data-ttu-id="a2ce8-120">使用[DROP INDEX &#40;transact-sql&#41;](/sql/t-sql/statements/drop-index-transact-sql)语句删除聚集列存储索引。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-120">Use the [DROP INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql) statement to drop a clustered columnstore index.</span></span> <span data-ttu-id="a2ce8-121">此操作将删除该索引并将列存储表转换为行存储堆。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-121">This operation will drop the index and convert the columnstore table to a rowstore heap.</span></span>

##  <a name="load-data-into-a-clustered-columnstore-index"></a><a name="load"></a><span data-ttu-id="a2ce8-122">将数据加载到聚集列存储索引</span><span class="sxs-lookup"><span data-stu-id="a2ce8-122">Load Data into a Clustered Columnstore Index</span></span>
 <span data-ttu-id="a2ce8-123">您可以使用任何标准加载方法，将数据添加到现有聚集列存储索引。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-123">You can add data to an existing clustered columnstore index by using any of the standard loading methods.</span></span>  <span data-ttu-id="a2ce8-124">例如，bcp 大容量加载工具、Integration Services 和 INSERT .。。选择 "可以将所有数据都加载到聚集列存储索引中"。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-124">For example, the bcp bulk loading tool, Integration Services, and INSERT ... SELECT can all load data into a clustered columnstore index.</span></span>

 <span data-ttu-id="a2ce8-125">聚集列存储索引利用增量存储以便防止在列存储的列段中出现碎片。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-125">Clustered columnstore indexes leverage the deltastore in order to prevent fragmentation of column segments in the columnstore.</span></span>

### <a name="loading-into-a-partitioned-table"></a><span data-ttu-id="a2ce8-126">加载到已分区表中</span><span class="sxs-lookup"><span data-stu-id="a2ce8-126">Loading into a partitioned table</span></span>
 <span data-ttu-id="a2ce8-127">对于已分区数据， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 首先将每一行分配给一个分区，然后对该分区内的数据执行列存储操作。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-127">For partitioned data, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] first assigns each row to a partition, and then performs columnstore operations on the data within the partition.</span></span> <span data-ttu-id="a2ce8-128">每个分区都具有自己的行组以及至少一个增量存储。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-128">Each partition has its own rowgroups and at least one deltastore.</span></span>

### <a name="deltastore-loading-scenarios"></a><span data-ttu-id="a2ce8-129">增量存储加载方案</span><span class="sxs-lookup"><span data-stu-id="a2ce8-129">Deltastore loading scenarios</span></span>
 <span data-ttu-id="a2ce8-130">行在增量存储中累积，直到行数达到行组允许的最大行数。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-130">Rows accumulate in the deltastore until the number of rows is the maximum number of rows allowed for a rowgroup.</span></span> <span data-ttu-id="a2ce8-131">如果增量存储包含每个行组的最大行数， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 则将行组标记为 "已关闭"。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-131">When the deltastore contains the maximum number of rows per rowgroup, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] marks the rowgroup as "CLOSED".</span></span> <span data-ttu-id="a2ce8-132">称为 "元组-移动器" 的后台进程将查找关闭的行组，并将其移到列存储中，其中，行组压缩为列段，列段存储在列存储中。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-132">A background process, called the "tuple-mover", finds the CLOSED rowgroup and moves into the columnstore, where the rowgroup is compressed into column segments and the column segments are stored in the columnstore.</span></span>

 <span data-ttu-id="a2ce8-133">每个聚集列存储索引可以有多个增量存储。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-133">For each clustered columnstore index there can be multiple deltastores.</span></span>

-   <span data-ttu-id="a2ce8-134">如果锁定一个增量存储， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 将尝试获取其他增量存储的锁。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-134">If a deltastore is locked, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] will try to obtain a lock on a different deltastore.</span></span> <span data-ttu-id="a2ce8-135">如果没有可用的增量存储， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 将创建新的增量存储。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-135">If there are no deltastores available, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] will create a new deltastore.</span></span>

-   <span data-ttu-id="a2ce8-136">对于已分区的表，每个分区可以有一个或多个增量存储。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-136">For a partitioned table, there can be one or more deltastores for each partition.</span></span>

 <span data-ttu-id="a2ce8-137">仅对于聚集列存储索引，以下方案说明何时将加载的行直接转到列存储中以及何时将它们转到增量存储中。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-137">For clustered columnstore indexes only, the following scenarios describe when loaded rows go directly to the columnstore or when they go to the deltastore.</span></span>

 <span data-ttu-id="a2ce8-138">在示例中，每个行组可以具有 102,400-1,048,576 行。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-138">In the example, each rowgroup can have 102,400-1,048,576 rows per rowgroup.</span></span>

|<span data-ttu-id="a2ce8-139">要大容量加载的行</span><span class="sxs-lookup"><span data-stu-id="a2ce8-139">Rows to Bulk Load</span></span>|<span data-ttu-id="a2ce8-140">已添加到列存储的行</span><span class="sxs-lookup"><span data-stu-id="a2ce8-140">Rows Added to the Columnstore</span></span>|<span data-ttu-id="a2ce8-141">已添加到增量存储的行</span><span class="sxs-lookup"><span data-stu-id="a2ce8-141">Rows Added to the Deltastore</span></span>|
|-----------------------|-----------------------------------|----------------------------------|
|<span data-ttu-id="a2ce8-142">102,000</span><span class="sxs-lookup"><span data-stu-id="a2ce8-142">102,000</span></span>|<span data-ttu-id="a2ce8-143">0</span><span class="sxs-lookup"><span data-stu-id="a2ce8-143">0</span></span>|<span data-ttu-id="a2ce8-144">102,000</span><span class="sxs-lookup"><span data-stu-id="a2ce8-144">102,000</span></span>|
|<span data-ttu-id="a2ce8-145">145,000</span><span class="sxs-lookup"><span data-stu-id="a2ce8-145">145,000</span></span>|<span data-ttu-id="a2ce8-146">145,000</span><span class="sxs-lookup"><span data-stu-id="a2ce8-146">145,000</span></span><br /><br /> <span data-ttu-id="a2ce8-147">行组大小：145,000</span><span class="sxs-lookup"><span data-stu-id="a2ce8-147">Rowgroup size: 145,000</span></span>|<span data-ttu-id="a2ce8-148">0</span><span class="sxs-lookup"><span data-stu-id="a2ce8-148">0</span></span>|
|<span data-ttu-id="a2ce8-149">1,048,577</span><span class="sxs-lookup"><span data-stu-id="a2ce8-149">1,048,577</span></span>|<span data-ttu-id="a2ce8-150">1,048,576</span><span class="sxs-lookup"><span data-stu-id="a2ce8-150">1,048,576</span></span><br /><br /> <span data-ttu-id="a2ce8-151">行组大小：1,048,576。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-151">Rowgroup size: 1,048,576.</span></span>|<span data-ttu-id="a2ce8-152">1</span><span class="sxs-lookup"><span data-stu-id="a2ce8-152">1</span></span>|
|<span data-ttu-id="a2ce8-153">2,252,152</span><span class="sxs-lookup"><span data-stu-id="a2ce8-153">2,252,152</span></span>|<span data-ttu-id="a2ce8-154">2,252,152</span><span class="sxs-lookup"><span data-stu-id="a2ce8-154">2,252,152</span></span><br /><br /> <span data-ttu-id="a2ce8-155">行组大小：1,048,576、1,048,576、155,000。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-155">Rowgroup sizes: 1,048,576, 1,048,576, 155,000.</span></span>|<span data-ttu-id="a2ce8-156">0</span><span class="sxs-lookup"><span data-stu-id="a2ce8-156">0</span></span>|

 <span data-ttu-id="a2ce8-157">以下示例显示将 1,048,577 行加载到分区的结果。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-157">The following example shows the results of loading 1,048,577 rows into a partition.</span></span> <span data-ttu-id="a2ce8-158">这些结果显示列存储（作为压缩的列段）中的一个 COMPRESSED 行组以及增量存储中的 1 行。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-158">The results show that one COMPRESSED rowgroup in the columnstore (as compressed column segments), and 1 row in the deltastore.</span></span>

```sql
SELECT * FROM sys.column_store_row_groups;
```

 <span data-ttu-id="a2ce8-159">![用于批量加载的行组和增量存储](../../2014/database-engine/media/sql-server-pdw-columnstore-batchload.gif "用于批量加载的行组和增量存储")</span><span class="sxs-lookup"><span data-stu-id="a2ce8-159">![Rowgroup and deltastore for a batch load](../../2014/database-engine/media/sql-server-pdw-columnstore-batchload.gif "Rowgroup and deltastore for a batch load")</span></span>



##  <a name="change-data-in-a-clustered-columnstore-index"></a><a name="change"></a><span data-ttu-id="a2ce8-160">更改聚集列存储索引中的数据</span><span class="sxs-lookup"><span data-stu-id="a2ce8-160">Change Data in a Clustered Columnstore Index</span></span>
 <span data-ttu-id="a2ce8-161">聚集列存储索引支持插入、更新和删除 DML 操作。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-161">Clustered columnstore indexes support insert, update, and delete DML operations.</span></span>

 <span data-ttu-id="a2ce8-162">使用[insert &#40;transact-sql&#41;](/sql/t-sql/statements/insert-transact-sql)插入行。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-162">Use [INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql) to insert a row.</span></span> <span data-ttu-id="a2ce8-163">该行将添加到增量存储中。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-163">The row will be added to the deltastore.</span></span>

 <span data-ttu-id="a2ce8-164">使用 [DELETE (Transact-SQL)](/sql/t-sql/statements/delete-transact-sql) 删除行。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-164">Use [DELETE &#40;Transact-SQL&#41;](/sql/t-sql/statements/delete-transact-sql) to delete a row.</span></span>

-   <span data-ttu-id="a2ce8-165">如果该行在列存储中，[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 将它标记为已逻辑删除但是未回收行的物理存储空间，直到重新生成索引。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-165">If the row is in the columnstore, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] marks the row as logically deleted but does not reclaim the physical storage for the row until the index is rebuilt.</span></span>

-   <span data-ttu-id="a2ce8-166">如果该行在增量存储中，[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 在逻辑上和物理上删除该行。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-166">If the row is in the deltastore, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] logically and physically deletes the row.</span></span>

 <span data-ttu-id="a2ce8-167">使用 [UPDATE (Transact-SQL)](/sql/t-sql/queries/update-transact-sql) 更新行。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-167">Use [UPDATE &#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql) to update a row.</span></span>

-   <span data-ttu-id="a2ce8-168">如果该行在列存储中，[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 将它标记为已逻辑删除，然后将更新的行插入增量存储中。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-168">If the row is in the columnstore, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] marks the row as logically deleted, and then inserts the updated row into the deltastore.</span></span>

-   <span data-ttu-id="a2ce8-169">如果该行在增量存储中，[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 在增量存储中更新它。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-169">If the row is in the deltastore, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] updates the row in the deltastore.</span></span>

##  <a name="rebuild-a-clustered-columnstore-index"></a><a name="rebuild"></a><span data-ttu-id="a2ce8-170">重新生成聚集列存储索引</span><span class="sxs-lookup"><span data-stu-id="a2ce8-170">Rebuild a Clustered Columnstore Index</span></span>
 <span data-ttu-id="a2ce8-171">使用[CREATE 聚集列存储索引 &#40;transact-sql&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql)或[ALTER INDEX &#40;transact-sql&#41;](/sql/t-sql/statements/alter-index-transact-sql)来执行现有聚集列存储索引的完整重新生成。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-171">Use [CREATE CLUSTERED COLUMNSTORE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql) or [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) to perform a full rebuild of an existing clustered columnstore index.</span></span> <span data-ttu-id="a2ce8-172">此外，还可以使用 ALTER INDEX .。。重新生成以重新生成特定分区。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-172">Additionally, you can use ALTER INDEX ... REBUILD to rebuild a specific partition.</span></span>

### <a name="rebuild-process"></a><span data-ttu-id="a2ce8-173">重新生成过程</span><span class="sxs-lookup"><span data-stu-id="a2ce8-173">Rebuild Process</span></span>
 <span data-ttu-id="a2ce8-174">若要重新生成聚集列存储索引，[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 将：</span><span class="sxs-lookup"><span data-stu-id="a2ce8-174">To rebuild a clustered columnstore index, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:</span></span>

-   <span data-ttu-id="a2ce8-175">在重新生成进行时获取表或分区上的排他锁。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-175">Acquires an exclusive lock on the table or partition while the rebuild occurs.</span></span>  <span data-ttu-id="a2ce8-176">在重新生成期间数据“处于脱机状态”并且不可用。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-176">The data is "offline" and unavailable during the rebuild.</span></span>

-   <span data-ttu-id="a2ce8-177">通过物理删除已从表中逻辑上删除的行对列存储进行碎片整理；已删除的字节在物理介质上回收。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-177">Defragments the columnstore by physically deleting rows that have been logically deleted from the table; the deleted bytes are reclaimed on the physical media.</span></span>

-   <span data-ttu-id="a2ce8-178">在重新生成索引前将增量存储区中的行存储数据与列存储区中的数据进行合并。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-178">Merges the rowstore data in the deltastore with the data in the columnstore before it rebuilds the index.</span></span> <span data-ttu-id="a2ce8-179">在重新生成完成后，所有数据都以列存储格式存储，并且增量存储为空。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-179">When the rebuild is finished, all data is stored in columnstore format, and the deltastore is empty.</span></span>

-   <span data-ttu-id="a2ce8-180">将所有数据重新压缩到列存储中。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-180">Re-compresses all data into the columnstore.</span></span> <span data-ttu-id="a2ce8-181">在进行重新生成时存在列存储索引的两个副本。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-181">Two copies of the columnstore index exist while the rebuild is taking place.</span></span> <span data-ttu-id="a2ce8-182">在重新生成完成后， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 将删除原始列存储索引。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-182">When the rebuild is finished, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] deletes the original columnstore index.</span></span>

### <a name="recommendations-for-rebuilding-a-clustered-columnstore-index"></a><span data-ttu-id="a2ce8-183">有关重新生成聚集列存储索引的建议</span><span class="sxs-lookup"><span data-stu-id="a2ce8-183">Recommendations for Rebuilding a Clustered Columnstore Index</span></span>
 <span data-ttu-id="a2ce8-184">重新生成聚集列存储索引适用于删除碎片，并且适用于将所有行都移到列存储中。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-184">Rebuilding a clustered columnstore index is useful for removing fragmentation, and for moving all rows into the columnstore.</span></span> <span data-ttu-id="a2ce8-185">请考虑以下建议：</span><span class="sxs-lookup"><span data-stu-id="a2ce8-185">We have the following recommendations:</span></span>

-   <span data-ttu-id="a2ce8-186">重新生成分区而不是整个表。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-186">Rebuild a partition instead of the entire table.</span></span>

    1.  <span data-ttu-id="a2ce8-187">如果索引很大，并且在重新生成期间需要足够的磁盘空间来存储索引的额外副本，则重新生成整个表将很费时间。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-187">Rebuilding the entire table takes a long time if the index is large, and it requires enough disk space to store an additional copy of the index during the rebuild.</span></span> <span data-ttu-id="a2ce8-188">通常仅需要重新生成最近使用的分区。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-188">Usually it is only necessary to rebuild the most recently used partition.</span></span>

    2.  <span data-ttu-id="a2ce8-189">对于已分区的表，您不需要重新生成整个列存储索引，因为碎片仅可能在最近修改的分区中出现。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-189">For partitioned tables, you do not need to rebuild the entire columnstore index because fragmentation is likely to occur in only the partitions that have been modified recently.</span></span> <span data-ttu-id="a2ce8-190">事实表和大型的维度表通常已分区，以便对表的特定块执行备份和管理操作。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-190">Fact tables and large dimension tables are usually partitioned in order to perform backup and management operations on chunks of the table.</span></span>

-   <span data-ttu-id="a2ce8-191">在执行了大量 DML 操作后重新生成分区</span><span class="sxs-lookup"><span data-stu-id="a2ce8-191">Rebuild a partition after heavy DML operations.</span></span>

     <span data-ttu-id="a2ce8-192">重新生成某一分区将会对该分区进行碎片整理，并且缩小磁盘存储空间。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-192">Rebuilding a partition will defragment the partition and reduce disk storage.</span></span> <span data-ttu-id="a2ce8-193">重新生成将会从列存储中删除标记为要删除的所有行，并且会将所有行从增量存储移到列存储中。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-193">Rebuilding will delete all rows from the columnstore that are marked for deletion, and it will move all rows from the deltastore into the columnstore.</span></span>

-   <span data-ttu-id="a2ce8-194">在加载数据后重新生成分区。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-194">Rebuild a partition after loading data.</span></span>

     <span data-ttu-id="a2ce8-195">这可确保所有数据都存储于列存储中。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-195">This ensures all data is stored in the columnstore.</span></span> <span data-ttu-id="a2ce8-196">如果同时发生多个加载，每个分区可能最终有多个增量存储。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-196">If multiple loads occur at the same time, each partition could end up having multiple deltastores.</span></span> <span data-ttu-id="a2ce8-197">重新生成会将所有增量存储行都移到列存储中。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-197">Rebuilding will move all deltastore rows into the columnstore.</span></span>

##  <a name="reorganize-a-clustered-columnstore-index"></a><a name="reorganize"></a><span data-ttu-id="a2ce8-198">重新组织聚集列存储索引</span><span class="sxs-lookup"><span data-stu-id="a2ce8-198">Reorganize a Clustered Columnstore Index</span></span>
 <span data-ttu-id="a2ce8-199">重新组织聚集列存储索引会将所有已关闭行组都移到列存储中。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-199">Reorganizing a clustered columnstore index moves all CLOSED rowgroups into the columnstore.</span></span> <span data-ttu-id="a2ce8-200">若要执行重新组织，请将[ALTER INDEX &#40;transact-sql&#41;](/sql/t-sql/statements/alter-index-transact-sql)与 "重新组织" 选项一起使用。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-200">To perform a reorganize, use [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)with the REORGANIZE option.</span></span>

 <span data-ttu-id="a2ce8-201">为了将关闭的行组移到列存储中，不需要重新组织索引。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-201">Reorganizing is not required in order to move CLOSED rowgroups into the columnstore.</span></span> <span data-ttu-id="a2ce8-202">元组搬运者进程最终将找到所有关闭的行组并且移动它们。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-202">The tuple-mover process will eventually find all CLOSED rowgroups and move them.</span></span> <span data-ttu-id="a2ce8-203">但是，tuple-mover 是单线程的，因此，对于您的工作负荷来说它移动行组的速度可能不够快。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-203">However, the tuple-mover is single-threaded and might not move rowgroups fast enough for your workload.</span></span>

### <a name="recommendations-for-reorganizing"></a><span data-ttu-id="a2ce8-204">进行重新组织的建议</span><span class="sxs-lookup"><span data-stu-id="a2ce8-204">Recommendations for Reorganizing</span></span>
 <span data-ttu-id="a2ce8-205">何时重新组织聚集列存储索引：</span><span class="sxs-lookup"><span data-stu-id="a2ce8-205">When to reorganize a clustered columnstore index:</span></span>

-   <span data-ttu-id="a2ce8-206">在执行一次或多次数据加载后，为了尽快优化查询性能，需要重新组织聚集列存储索引。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-206">Reorganize a clustered columnstore index after one or more data loads to achieve query performance benefits as quickly as possible.</span></span> <span data-ttu-id="a2ce8-207">重新组织最初需要额外的 CPU 资源来压缩数据，这可能降低整体系统性能。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-207">Reorganizing will initially require additional CPU resources to compress the data, which could slow overall system performance.</span></span> <span data-ttu-id="a2ce8-208">但是，压缩数据后，可以提高查询性能。</span><span class="sxs-lookup"><span data-stu-id="a2ce8-208">However, as soon as the data is compressed, query performance can improve.</span></span>


