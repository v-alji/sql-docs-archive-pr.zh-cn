---
title: 索引磁盘空间示例 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- online index disk space
- disk space [SQL Server], indexes
- index disk space [SQL Server]
- space [SQL Server], indexes
- indexes [SQL Server], disk space requirements
- offline index disk space [SQL Server]
ms.assetid: e5c71f55-0be3-4c93-97e9-7b3455c8f581
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e4a30c6ce986095496a11c41f3102d095e8c632b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586676"
---
# <a name="index-disk-space-example"></a><span data-ttu-id="8a631-102">索引磁盘空间示例</span><span class="sxs-lookup"><span data-stu-id="8a631-102">Index Disk Space Example</span></span>
  <span data-ttu-id="8a631-103">无论什么时候创建、重新生成或删除索引，在相应的文件和文件组中都需要用于存储旧（源）结构和新（目标）结构的磁盘空间。</span><span class="sxs-lookup"><span data-stu-id="8a631-103">Whenever an index is created, rebuilt, or dropped, disk space for both the old (source) and new (target) structures is required in their appropriate files and filegroups.</span></span> <span data-ttu-id="8a631-104">旧的结构只有在提交索引创建事务后才会释放。</span><span class="sxs-lookup"><span data-stu-id="8a631-104">The old structure is not deallocated until the index creation transaction commits.</span></span> <span data-ttu-id="8a631-105">还可能需要附加临时磁盘空间以进行排序操作。</span><span class="sxs-lookup"><span data-stu-id="8a631-105">Additional temporary disk space for sorting operations may also be needed.</span></span> <span data-ttu-id="8a631-106">有关详细信息，请参阅 [Disk Space Requirements for Index DDL Operations](disk-space-requirements-for-index-ddl-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="8a631-106">For more information, see [Disk Space Requirements for Index DDL Operations](disk-space-requirements-for-index-ddl-operations.md).</span></span>  
  
 <span data-ttu-id="8a631-107">在本示例中，将确定创建聚集索引需要的磁盘空间。</span><span class="sxs-lookup"><span data-stu-id="8a631-107">In this example, disk space requirements to create a clustered index are determined.</span></span>  
  
 <span data-ttu-id="8a631-108">创建聚集索引之前假定满足以下条件：</span><span class="sxs-lookup"><span data-stu-id="8a631-108">Assume the following conditions are true before creating the clustered index:</span></span>  
  
-   <span data-ttu-id="8a631-109">现有表（堆）包含 100 万行。</span><span class="sxs-lookup"><span data-stu-id="8a631-109">The existing table (heap) contains 1 million rows.</span></span> <span data-ttu-id="8a631-110">每行长度为 200 字节。</span><span class="sxs-lookup"><span data-stu-id="8a631-110">Each row is 200 bytes long.</span></span>  
  
-   <span data-ttu-id="8a631-111">非聚集索引 A 包含 100 万行。</span><span class="sxs-lookup"><span data-stu-id="8a631-111">Nonclustered index A contains 1 million rows.</span></span> <span data-ttu-id="8a631-112">每行长度为 50 字节。</span><span class="sxs-lookup"><span data-stu-id="8a631-112">Each row is 50 bytes long.</span></span>  
  
-   <span data-ttu-id="8a631-113">非聚集索引 B 包含 100 万行。</span><span class="sxs-lookup"><span data-stu-id="8a631-113">Nonclustered index B contains 1 million rows.</span></span> <span data-ttu-id="8a631-114">每行长度为 80 字节。</span><span class="sxs-lookup"><span data-stu-id="8a631-114">Each row is 80 bytes long.</span></span>  
  
-   <span data-ttu-id="8a631-115">index create memory 选项设置为 2 MB。</span><span class="sxs-lookup"><span data-stu-id="8a631-115">The index create memory option is set to 2 MB.</span></span>  
  
-   <span data-ttu-id="8a631-116">所有现有索引和新索引都使用填充因子值 80。</span><span class="sxs-lookup"><span data-stu-id="8a631-116">A fill factor value of 80 is used for all existing and new indexes.</span></span> <span data-ttu-id="8a631-117">这意味着页的 80% 是满的。</span><span class="sxs-lookup"><span data-stu-id="8a631-117">This means the pages are 80 percent full.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8a631-118">由于创建了聚集索引，必须重新生成这两个非聚集索引来用新聚集索引键替换行指示器。</span><span class="sxs-lookup"><span data-stu-id="8a631-118">As a result of creating a clustered index, the two nonclustered indexes must be rebuilt to replace the row indicator with the new clustered index key.</span></span>  
  
## <a name="disk-space-calculations-for-an-offline-index-operation"></a><span data-ttu-id="8a631-119">脱机索引操作所用的磁盘空间计算</span><span class="sxs-lookup"><span data-stu-id="8a631-119">Disk Space Calculations for an Offline Index Operation</span></span>  
 <span data-ttu-id="8a631-120">在以下步骤中，将计算在索引操作期间使用的临时磁盘空间和用于存储新索引的永久磁盘空间。</span><span class="sxs-lookup"><span data-stu-id="8a631-120">In the following steps, both temporary disk space to be used during the index operation and permanent disk space to store the new indexes are calculated.</span></span> <span data-ttu-id="8a631-121">显示的计算是近似的；结果将向上舍入而且仅考虑索引叶级别的大小。</span><span class="sxs-lookup"><span data-stu-id="8a631-121">The calculations shown are approximate; results are rounded up and consider only the size of index leaf level.</span></span> <span data-ttu-id="8a631-122">代字号 (~) 用来表示近似计算。</span><span class="sxs-lookup"><span data-stu-id="8a631-122">The tilde (~) is used to indicate approximate calculations.</span></span>  
  
1.  <span data-ttu-id="8a631-123">确定源结构的大小。</span><span class="sxs-lookup"><span data-stu-id="8a631-123">Determine the size of the source structures.</span></span>  
  
     <span data-ttu-id="8a631-124">堆：100 万 \* 200 字节 ~ 200 MB</span><span class="sxs-lookup"><span data-stu-id="8a631-124">Heap: 1 million \* 200 bytes ~ 200 MB</span></span>  
  
     <span data-ttu-id="8a631-125">非聚集索引 A：1 百万 \* 50 字节 / 80% ~ 63 MB</span><span class="sxs-lookup"><span data-stu-id="8a631-125">Nonclustered index A: 1 million \* 50 bytes / 80% ~ 63 MB</span></span>  
  
     <span data-ttu-id="8a631-126">非聚集索引 B：1 百万 \* 80 字节 / 80% ~ 100 MB</span><span class="sxs-lookup"><span data-stu-id="8a631-126">Nonclustered index B: 1 million \* 80 bytes / 80% ~ 100 MB</span></span>  
  
     <span data-ttu-id="8a631-127">现有结构的总大小：363 MB</span><span class="sxs-lookup"><span data-stu-id="8a631-127">Total size of existing structures: 363 MB</span></span>  
  
2.  <span data-ttu-id="8a631-128">确定目标索引结构的大小。</span><span class="sxs-lookup"><span data-stu-id="8a631-128">Determine the size of the target index structures.</span></span> <span data-ttu-id="8a631-129">假定新聚集键为 24 字节长（包含一个 uniqueifier）。</span><span class="sxs-lookup"><span data-stu-id="8a631-129">Assume that the new clustered key is 24 bytes long including a uniqueifier.</span></span> <span data-ttu-id="8a631-130">两个非聚集索引的行指示器（8 字节长）将由此聚集键替换。</span><span class="sxs-lookup"><span data-stu-id="8a631-130">The row indicator (8 bytes long) in both nonclustered indexes will be replaced by this clustered key.</span></span>  
  
     <span data-ttu-id="8a631-131">聚集索引：1 百万 \* 200 字节 / 80% ~ 250 MB</span><span class="sxs-lookup"><span data-stu-id="8a631-131">Clustered index: 1 million \* 200 bytes / 80% ~ 250 MB</span></span>  
  
     <span data-ttu-id="8a631-132">非聚集索引 A：1 百万 \* (50 - 8 + 24) 字节 / 80% ~ 83 MB</span><span class="sxs-lookup"><span data-stu-id="8a631-132">Nonclustered index A: 1 million \* (50 - 8 + 24) bytes / 80% ~ 83 MB</span></span>  
  
     <span data-ttu-id="8a631-133">非聚集索引 B：1 百万 \* (80 - 8 + 24) 字节 / 80% ~ 120 MB</span><span class="sxs-lookup"><span data-stu-id="8a631-133">Nonclustered index B: 1 million \* (80 - 8 + 24) bytes / 80% ~ 120 MB</span></span>  
  
     <span data-ttu-id="8a631-134">新结构的总大小：453 MB</span><span class="sxs-lookup"><span data-stu-id="8a631-134">Total size of new structures: 453 MB</span></span>  
  
     <span data-ttu-id="8a631-135">索引操作期间支持源结构和目标结构所需的总磁盘空间为 816 MB (363 + 453)。</span><span class="sxs-lookup"><span data-stu-id="8a631-135">Total disk space required to support both the source and target structures for the duration of the index operation is 816 MB (363 + 453).</span></span> <span data-ttu-id="8a631-136">索引操作提交后将释放当前分配给源结构的空间。</span><span class="sxs-lookup"><span data-stu-id="8a631-136">The space currently allocated to the source structures will be deallocated after the index operation is committed.</span></span>  
  
3.  <span data-ttu-id="8a631-137">确定用于排序的附加临时磁盘空间。</span><span class="sxs-lookup"><span data-stu-id="8a631-137">Determine additional temporary disk space for sorting.</span></span>  
  
     <span data-ttu-id="8a631-138">将显示在 **tempdb** 中排序所用的空间要求（其中 SORT_IN_TEMPDB 设置为 ON）和在目标位置排序所用的空间要求（其中 SORT_IN_TEMPDB 设置为 OFF）。</span><span class="sxs-lookup"><span data-stu-id="8a631-138">Space requirements are shown for sorting in **tempdb** (with SORT_IN_TEMPDB set to ON) and sorting in the target location (with SORT_IN_TEMPDB set to OFF).</span></span>  
  
    1.  <span data-ttu-id="8a631-139">SORT_IN_TEMPDB 设置为 ON 时， **tempdb** 必须有足够磁盘空间以容纳最大的索引（1 百万 \* 200 字节 ~ 200 MB）。</span><span class="sxs-lookup"><span data-stu-id="8a631-139">When SORT_IN_TEMPDB is set to ON, **tempdb** must have sufficient disk space to hold the largest index (1 million \* 200 bytes ~ 200 MB).</span></span> <span data-ttu-id="8a631-140">在排序操作中没有考虑填充因子。</span><span class="sxs-lookup"><span data-stu-id="8a631-140">Fill factor is not considered in the sorting operation.</span></span>  
  
         <span data-ttu-id="8a631-141">**配置 index create memory 服务器配置选项** 值 = 2 MB，附加磁盘空间（在 [tempdb](../../database-engine/configure-windows/configure-the-index-create-memory-server-configuration-option.md) 位置）与其相同。</span><span class="sxs-lookup"><span data-stu-id="8a631-141">Additional disk space (in the **tempdb** location) equal to the [Configure the index create memory Server Configuration Option](../../database-engine/configure-windows/configure-the-index-create-memory-server-configuration-option.md) value = 2 MB.</span></span>  
  
         <span data-ttu-id="8a631-142">将 SORT_IN_TEMPDB 设置为 ON 时临时磁盘空间的总大小 ~ 202 MB。</span><span class="sxs-lookup"><span data-stu-id="8a631-142">Total size of temporary disk space with SORT_IN_TEMPDB set to ON ~ 202 MB.</span></span>  
  
    2.  <span data-ttu-id="8a631-143">SORT_IN_TEMPDB 设置为 OFF（默认值）时，步骤 2 中用于新索引的 250 MB 磁盘空间将用于排序。</span><span class="sxs-lookup"><span data-stu-id="8a631-143">When SORT_IN_TEMPDB is set to OFF (default), the 250 MB of disk space already considered for the new index in step 2 is used for sorting.</span></span>  
  
         <span data-ttu-id="8a631-144">[配置 index create memory 服务器配置选项](../../database-engine/configure-windows/configure-the-index-create-memory-server-configuration-option.md) 值 = 2 MB，附加磁盘空间（在目标位置）与其相同。</span><span class="sxs-lookup"><span data-stu-id="8a631-144">Additional disk space (in the target location) equal to the [Configure the index create memory Server Configuration Option](../../database-engine/configure-windows/configure-the-index-create-memory-server-configuration-option.md) value = 2 MB.</span></span>  
  
         <span data-ttu-id="8a631-145">将 SORT_IN_TEMPDB 设置为 OFF 时临时磁盘空间的总大小 = 2 MB。</span><span class="sxs-lookup"><span data-stu-id="8a631-145">Total size of temporary disk space with SORT_IN_TEMPDB set to OFF = 2 MB.</span></span>  
  
 <span data-ttu-id="8a631-146">使用 **tempdb**时，将一共需要 1018 MB (816 + 202) 来创建聚集索引和非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="8a631-146">Using **tempdb**, a total of 1018 MB (816 + 202) would be needed to create the clustered and nonclustered indexes.</span></span> <span data-ttu-id="8a631-147">虽然使用 **tempdb** 增加了用于创建索引的临时磁盘空间量，但是当 **tempdb** 与用户数据库位于不同的磁盘集上时，它可以减少创建索引所需的时间。</span><span class="sxs-lookup"><span data-stu-id="8a631-147">Although using **tempdb** increases the amount of temporary disk space used to create an index, it may reduce the time that is required to create an index when **tempdb** is on a different set of disks than the user database.</span></span> <span data-ttu-id="8a631-148">有关使用 **tempdb**的详细信息，请参阅 [用于索引的 SORT_IN_TEMPDB 选项](indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="8a631-148">For more information about using **tempdb**, see [SORT_IN_TEMPDB Option For Indexes](indexes.md).</span></span>  
  
 <span data-ttu-id="8a631-149">不使用 **tempdb**时，将一共需要 818 MB (816 + 2) 来创建聚集索引和非聚集索引。</span><span class="sxs-lookup"><span data-stu-id="8a631-149">Without using **tempdb**, a total of 818 MB (816+ 2) would be needed to create the clustered and nonclustered indexes.</span></span>  
  
## <a name="disk-space-calculations-for-an-online-clustered-index-operation"></a><span data-ttu-id="8a631-150">联机聚集索引操作所用的磁盘空间计算</span><span class="sxs-lookup"><span data-stu-id="8a631-150">Disk Space Calculations for an Online Clustered Index Operation</span></span>  
 <span data-ttu-id="8a631-151">联机创建、删除或重新生成聚集索引时，将需要附加磁盘空间以生成和维护临时映射索引。</span><span class="sxs-lookup"><span data-stu-id="8a631-151">When you create, drop, or rebuild a clustered index online, additional disk space is required to build and maintain a temporary mapping index.</span></span> <span data-ttu-id="8a631-152">此临时映射索引包含表中每行的一条记录，其内容包含新旧书签列。</span><span class="sxs-lookup"><span data-stu-id="8a631-152">This temporary mapping index contains one record for each row in the table, and its contents are the union of the old and new bookmark columns.</span></span>  
  
 <span data-ttu-id="8a631-153">若要计算联机聚集索引操作所需的磁盘空间，请按照脱机索引操作显示的步骤操作并将结果添加到以下步骤的结果中。</span><span class="sxs-lookup"><span data-stu-id="8a631-153">To calculate the disk space needed for an online clustered index operation, follow the steps shown for an offline index operation and add those results to the results of the following step.</span></span>  
  
-   <span data-ttu-id="8a631-154">确定临时映射索引的空间。</span><span class="sxs-lookup"><span data-stu-id="8a631-154">Determine space for the temporary mapping index.</span></span>  
  
     <span data-ttu-id="8a631-155">在此示例中，旧书签是堆的行 ID (RID)  (8 个字节) ，而新书签是聚集键 (24 个字节，包括一个 `uniqueifier`) 。</span><span class="sxs-lookup"><span data-stu-id="8a631-155">In this example, the old bookmark is the row ID (RID) of the heap (8 bytes) and the new bookmark is the clustering key (24 bytes including a `uniqueifier`).</span></span> <span data-ttu-id="8a631-156">在新旧书签之间没有重叠的列。</span><span class="sxs-lookup"><span data-stu-id="8a631-156">There are no overlapping columns between the old and new bookmarks.</span></span>  
  
     <span data-ttu-id="8a631-157">临时映射索引大小 = 1 百万 \* (8 字节 + 24 字节) / 80% ~ 40 MB。</span><span class="sxs-lookup"><span data-stu-id="8a631-157">Temporary mapping index size = 1 million \* (8 bytes + 24 bytes) / 80% ~ 40 MB.</span></span>  
  
     <span data-ttu-id="8a631-158">必须将此磁盘空间添加到目标位置所需磁盘空间（如果 SORT_IN_TEMPDB 设置为 OFF），或添加到 **tempdb** （如果 SORT_IN_TEMPDB 设置为 ON）。</span><span class="sxs-lookup"><span data-stu-id="8a631-158">This disk space must be added to the required disk space in the target location if SORT_IN_TEMPDB is set to OFF, or to **tempdb** if SORT_IN_TEMPDB is set to ON.</span></span>  
  
 <span data-ttu-id="8a631-159">有关临时映射索引的详细信息，请参阅 [索引 DDL 操作的磁盘空间要求](disk-space-requirements-for-index-ddl-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="8a631-159">For more information about the temporary mapping index, see [Disk Space Requirements for Index DDL Operations](disk-space-requirements-for-index-ddl-operations.md).</span></span>  
  
## <a name="disk-space-summary"></a><span data-ttu-id="8a631-160">磁盘空间摘要</span><span class="sxs-lookup"><span data-stu-id="8a631-160">Disk Space Summary</span></span>  
 <span data-ttu-id="8a631-161">下表汇总了磁盘空间计算的结果。</span><span class="sxs-lookup"><span data-stu-id="8a631-161">The following table summarizes the results of the disk space calculations.</span></span>  
  
|<span data-ttu-id="8a631-162">索引操作</span><span class="sxs-lookup"><span data-stu-id="8a631-162">Index operation</span></span>|<span data-ttu-id="8a631-163">以下结构的位置所需的磁盘空间</span><span class="sxs-lookup"><span data-stu-id="8a631-163">Disk space requirements for the locations of the following structures</span></span>|  
|---------------------|---------------------------------------------------------------------------|  
|<span data-ttu-id="8a631-164">SORT_IN_TEMPDB = ON 时的脱机索引操作</span><span class="sxs-lookup"><span data-stu-id="8a631-164">Offline index operation with SORT_IN_TEMPDB = ON</span></span>|<span data-ttu-id="8a631-165">操作期间的总空间大小： 1018 MB：</span><span class="sxs-lookup"><span data-stu-id="8a631-165">Total space during the operation: 1018 MB:</span></span><br /><br /> <span data-ttu-id="8a631-166">\- 现有表和索引：363 MB\*</span><span class="sxs-lookup"><span data-stu-id="8a631-166">-Existing table and indexes: 363 MB\*</span></span><br /><br /> -<br />                    <span data-ttu-id="8a631-167">**tempdb**：202 MB\*</span><span class="sxs-lookup"><span data-stu-id="8a631-167">**tempdb**: 202 MB\*</span></span><br /><br /> <span data-ttu-id="8a631-168">\- 新索引：453 MB</span><span class="sxs-lookup"><span data-stu-id="8a631-168">-New indexes: 453 MB</span></span><br /><br /> <span data-ttu-id="8a631-169">操作后所需的总空间大小：453 MB</span><span class="sxs-lookup"><span data-stu-id="8a631-169">Total space required after the operation: 453 MB</span></span>|  
|<span data-ttu-id="8a631-170">SORT_IN_TEMPDB = OFF 时的脱机索引操作</span><span class="sxs-lookup"><span data-stu-id="8a631-170">Offline index operation with SORT_IN_TEMPDB = OFF</span></span>|<span data-ttu-id="8a631-171">操作期间的总空间大小： 816 MB：</span><span class="sxs-lookup"><span data-stu-id="8a631-171">Total space during the operation: 816 MB:</span></span><br /><br /> <span data-ttu-id="8a631-172">\- 现有表和索引：363 MB\*</span><span class="sxs-lookup"><span data-stu-id="8a631-172">-Existing table and indexes: 363 MB\*</span></span><br /><br /> <span data-ttu-id="8a631-173">\- 新索引：453 MB</span><span class="sxs-lookup"><span data-stu-id="8a631-173">-New indexes: 453 MB</span></span><br /><br /> <span data-ttu-id="8a631-174">操作后所需的总空间大小：453 MB</span><span class="sxs-lookup"><span data-stu-id="8a631-174">Total space required after the operation: 453 MB</span></span>|  
|<span data-ttu-id="8a631-175">SORT_IN_TEMPDB = ON 时的联机索引操作</span><span class="sxs-lookup"><span data-stu-id="8a631-175">Online index operation with SORT_IN_TEMPDB = ON</span></span>|<span data-ttu-id="8a631-176">操作期间的总空间大小： 1058 MB：</span><span class="sxs-lookup"><span data-stu-id="8a631-176">Total space during the operation: 1058 MB:</span></span><br /><br /> <span data-ttu-id="8a631-177">\- 现有表和索引：363 MB\*</span><span class="sxs-lookup"><span data-stu-id="8a631-177">-Existing table and indexes: 363 MB\*</span></span><br /><br /> <span data-ttu-id="8a631-178">-**tempdb** (包括映射索引) ： 242 MB \*</span><span class="sxs-lookup"><span data-stu-id="8a631-178">-**tempdb** (includes mapping index): 242 MB\*</span></span><br /><br /> <span data-ttu-id="8a631-179">\- 新索引：453 MB</span><span class="sxs-lookup"><span data-stu-id="8a631-179">-New indexes: 453 MB</span></span><br /><br /> <span data-ttu-id="8a631-180">操作后所需的总空间大小：453 MB</span><span class="sxs-lookup"><span data-stu-id="8a631-180">Total space required after the operation: 453 MB</span></span>|  
|<span data-ttu-id="8a631-181">SORT_IN_TEMPDB = OFF 时的联机索引操作</span><span class="sxs-lookup"><span data-stu-id="8a631-181">Online index operation with SORT_IN_TEMPDB = OFF</span></span>|<span data-ttu-id="8a631-182">操作期间的总空间大小： 856 MB：</span><span class="sxs-lookup"><span data-stu-id="8a631-182">Total space during the operation: 856 MB:</span></span><br /><br /> <span data-ttu-id="8a631-183">\- 现有表和索引：363 MB\*</span><span class="sxs-lookup"><span data-stu-id="8a631-183">-Existing table and indexes: 363 MB\*</span></span><br /><br /> <span data-ttu-id="8a631-184">\- 临时映射索引：40 MB\*</span><span class="sxs-lookup"><span data-stu-id="8a631-184">-Temporary mapping index: 40 MB\*</span></span><br /><br /> <span data-ttu-id="8a631-185">\- 新索引：453 MB</span><span class="sxs-lookup"><span data-stu-id="8a631-185">-New indexes: 453 MB</span></span><br /><br /> <span data-ttu-id="8a631-186">操作后所需的总空间大小：453 MB</span><span class="sxs-lookup"><span data-stu-id="8a631-186">Total space required after the operation: 453 MB</span></span>|  
  
 <span data-ttu-id="8a631-187">\*索引操作提交后将释放此空间。</span><span class="sxs-lookup"><span data-stu-id="8a631-187">\*This space is deallocated after the index operation is committed.</span></span>  
  
 <span data-ttu-id="8a631-188">此示例没有考虑任何 **tempdb** 中所需的附加临时磁盘空间（用于存储并发用户更新和删除操作创建的版本记录）。</span><span class="sxs-lookup"><span data-stu-id="8a631-188">This example does not consider any additional temporary disk space required in **tempdb** for version records created by concurrent user update and delete operations.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="8a631-189">相关内容</span><span class="sxs-lookup"><span data-stu-id="8a631-189">Related Content</span></span>  
 [<span data-ttu-id="8a631-190">索引 DDL 操作的磁盘空间要求</span><span class="sxs-lookup"><span data-stu-id="8a631-190">Disk Space Requirements for Index DDL Operations</span></span>](disk-space-requirements-for-index-ddl-operations.md)  
  
 [<span data-ttu-id="8a631-191">索引操作的事务日志磁盘空间</span><span class="sxs-lookup"><span data-stu-id="8a631-191">Transaction Log Disk Space for Index Operations</span></span>](transaction-log-disk-space-for-index-operations.md)  
  
  
