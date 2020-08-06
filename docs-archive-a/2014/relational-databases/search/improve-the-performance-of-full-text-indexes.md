---
title: 改进全文索引的性能 | Microsoft Docs
ms.custom: ''
ms.date: 04/26/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- performance [SQL Server], full-text search
- full-text queries [SQL Server], performance
- crawls [full-text search]
- full-text indexes [SQL Server], performance
- full-text search [SQL Server], performance
- batches [SQL Server], full-text search
ms.assetid: ef39ef1f-f0b7-4582-8e9c-31d4bd0ad35d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 51b5913e9c3ce65faa5a1fddc5846cc7c94d149f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690476"
---
# <a name="improve-the-performance-of-full-text-indexes"></a><span data-ttu-id="07da8-102">改进全文索引的性能</span><span class="sxs-lookup"><span data-stu-id="07da8-102">Improve the Performance of Full-Text Indexes</span></span>
  <span data-ttu-id="07da8-103">硬件资源（例如内存、磁盘速度、CPU 速度和计算机体系结构）会影响全文索引和全文查询的性能。</span><span class="sxs-lookup"><span data-stu-id="07da8-103">Performance for full-text indexing and full-text queries is influenced by hardware resources, such as memory, disk speed, CPU speed, and machine architecture.</span></span>  
  
##  <a name="common-causes-of-performance-issues"></a><a name="causes"></a><span data-ttu-id="07da8-104">性能问题的常见原因</span><span class="sxs-lookup"><span data-stu-id="07da8-104">Common Causes of Performance Issues</span></span>  
 <span data-ttu-id="07da8-105">导致全文索引性能降低的主要原因是硬件资源的限制：</span><span class="sxs-lookup"><span data-stu-id="07da8-105">The main cause for reduced full-text indexing performance is hardware-resource limits:</span></span>  
  
-   <span data-ttu-id="07da8-106">如果筛选器后台程序主机进程 (fdhost.exe) 或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 进程 (sqlservr.exe) 的 CPU 使用率接近 100%，则 CPU 会成为瓶颈。</span><span class="sxs-lookup"><span data-stu-id="07da8-106">If CPU usage by the filter daemon host process (fdhost.exe) or the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process (sqlservr.exe) is close to 100 percent, the CPU is the bottleneck.</span></span>  
  
-   <span data-ttu-id="07da8-107">如果平均磁盘等待队列长度是磁盘头数量的两倍以上，则磁盘将成为瓶颈。</span><span class="sxs-lookup"><span data-stu-id="07da8-107">If the average disk-waiting queue length is more than two times the number of disk heads, there is a bottleneck on the disk.</span></span> <span data-ttu-id="07da8-108">主要的解决方法是创建独立于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库文件和日志的全文目录。</span><span class="sxs-lookup"><span data-stu-id="07da8-108">The primary workaround is to create full-text catalogs that are separate from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database files and logs.</span></span> <span data-ttu-id="07da8-109">将日志、数据库文件和全文目录分别放在不同的磁盘上。</span><span class="sxs-lookup"><span data-stu-id="07da8-109">Put the logs, database files, and full-text catalogs on separate disks.</span></span> <span data-ttu-id="07da8-110">购买运行速度更快的磁盘和使用 RAID 也能帮助改善索引性能。</span><span class="sxs-lookup"><span data-stu-id="07da8-110">Buying faster disks and using RAID can also help improve indexing performance.</span></span>  
  
-   <span data-ttu-id="07da8-111">如果物理内存不足（3GB 限制），则内存可能是瓶颈。</span><span class="sxs-lookup"><span data-stu-id="07da8-111">If there is a shortage of physical memory (3-GB limit), memory might be the bottleneck.</span></span> <span data-ttu-id="07da8-112">物理内存限制可能存在于所有系统上，而在 32 位系统上，虚拟内存压力可导致全文索引速度降低。</span><span class="sxs-lookup"><span data-stu-id="07da8-112">Physical memory limitations are possible on all systems, and on 32-bit systems, virtual memory pressure can slow down full-text indexing.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="07da8-113">从 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]开始，全文引擎可以使用 AWE 内存，因为全文引擎是 sqlservr.exe 的一部分。</span><span class="sxs-lookup"><span data-stu-id="07da8-113">Beginning in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], the Full-Text Engine can use AWE memory because the Full-Text Engine is part of the sqlservr.exe.</span></span>  
  
 <span data-ttu-id="07da8-114">如果系统没有硬件瓶颈，则全文搜索的索引性能主要取决于以下因素：</span><span class="sxs-lookup"><span data-stu-id="07da8-114">If the system has no hardware bottlenecks, the indexing performance of full-text search mostly depends on the following:</span></span>  
  
-   <span data-ttu-id="07da8-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 创建全文批次花费的时间。</span><span class="sxs-lookup"><span data-stu-id="07da8-115">How long it takes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to create full-text batches.</span></span>  
  
-   <span data-ttu-id="07da8-116">筛选器后台程序能以多快的速度处理这些批次。</span><span class="sxs-lookup"><span data-stu-id="07da8-116">How quickly the filter daemon can consume those batches.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="07da8-117">与完全填充不同，增量、手动和自动更改跟踪填充的设计目的并不是为了最大程度地利用硬件资源以获得更高速度。</span><span class="sxs-lookup"><span data-stu-id="07da8-117">Unlike full population, incremental, manual, and auto change tracking population are not designed to maximize hardware resources to achieve faster speed.</span></span> <span data-ttu-id="07da8-118">因此，这些优化建议可能不会增强全文索引的性能。</span><span class="sxs-lookup"><span data-stu-id="07da8-118">Therefore, these tuning suggestions may not enhance performance for full-text indexing.</span></span>  
  
 <span data-ttu-id="07da8-119">填充完成后，将触发最终的合并过程，以便将索引碎片合并为一个主全文索引。</span><span class="sxs-lookup"><span data-stu-id="07da8-119">When a population has completed, a final merge process is triggered that merges the index fragments together into one master full-text index.</span></span> <span data-ttu-id="07da8-120">由于只需要查询主索引而不需要查询大量索引碎片，因此这将提高查询性能，并且可以使用更好的计分统计信息来得出相关性排名。</span><span class="sxs-lookup"><span data-stu-id="07da8-120">This results in improved query performance since only the master index needs to be queried rather than a number of index fragments, and better scoring statistics may be used for relevance ranking.</span></span> <span data-ttu-id="07da8-121">请注意，由于合并索引碎片时必须读取和写入大量数据，所以主合并可能会耗费大量 I/O，但它不会阻塞传入的查询。</span><span class="sxs-lookup"><span data-stu-id="07da8-121">Note that the master merge can be I/O intensive, because large amounts of data must be written and read when index fragments are merged, though it does not block incoming queries.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="07da8-122">对大量数据进行主合并会创建一个长时间运行的事务，在检查点期间延迟事务日志的截断。</span><span class="sxs-lookup"><span data-stu-id="07da8-122">Master merging a large amount of data can create a long running transaction, delaying truncation of the transaction log during checkpoint.</span></span> <span data-ttu-id="07da8-123">在这种情况下，事务日志可能会在完整恢复模式下显著增长。</span><span class="sxs-lookup"><span data-stu-id="07da8-123">In this case, under the full recovery model, the transaction log might grow significantly.</span></span> <span data-ttu-id="07da8-124">作为最佳做法，在使用完整恢复模式的数据库中重新组织较大的全文索引之前，应确保事务日志中包含足够的空间用于长时间运行的事务。</span><span class="sxs-lookup"><span data-stu-id="07da8-124">As a best practice, before reorganizing a large full-text index in a database that uses the full recovery model, ensure that your transaction log contains sufficient space for a long-running transaction.</span></span> <span data-ttu-id="07da8-125">有关详细信息，请参阅 [管理事务日志文件的大小](../logs/manage-the-size-of-the-transaction-log-file.md)。</span><span class="sxs-lookup"><span data-stu-id="07da8-125">For more information, see [Manage the Size of the Transaction Log File](../logs/manage-the-size-of-the-transaction-log-file.md).</span></span>  
  
  
  
##  <a name="tuning-the-performance-of-full-text-indexes"></a><a name="tuning"></a><span data-ttu-id="07da8-126">优化全文索引的性能</span><span class="sxs-lookup"><span data-stu-id="07da8-126">Tuning the Performance of Full-Text Indexes</span></span>  
 <span data-ttu-id="07da8-127">若要最大限度地提高全文索引的性能，请实施下列最佳做法：</span><span class="sxs-lookup"><span data-stu-id="07da8-127">To maximize the performance of your full-text indexes, implement the following best practices:</span></span>  
  
-   <span data-ttu-id="07da8-128">若要最大程度地使用所有处理器或内核，请将[sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)' `max full-text crawl ranges` ' 设置为系统的 cpu 数。</span><span class="sxs-lookup"><span data-stu-id="07da8-128">To use all processors or cores to the maximum, set [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)'`max full-text crawl ranges`' to the number of CPUs on the system.</span></span> <span data-ttu-id="07da8-129">有关此配置选项的信息，请参阅 [max full-text crawl range 服务器配置选项](../../database-engine/configure-windows/max-full-text-crawl-range-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="07da8-129">For information about this configuration option, see [max full-text crawl range Server Configuration Option](../../database-engine/configure-windows/max-full-text-crawl-range-server-configuration-option.md).</span></span>  
  
-   <span data-ttu-id="07da8-130">请确保基表具有聚集索引。</span><span class="sxs-lookup"><span data-stu-id="07da8-130">Make sure that the base table has a clustered index.</span></span> <span data-ttu-id="07da8-131">对聚集索引的第一列使用整数数据类型。</span><span class="sxs-lookup"><span data-stu-id="07da8-131">Use an integer data type for the first column of the clustered index.</span></span> <span data-ttu-id="07da8-132">避免在聚集索引的第一列使用 GUID。</span><span class="sxs-lookup"><span data-stu-id="07da8-132">Avoid using GUIDs in the first column of the clustered index.</span></span> <span data-ttu-id="07da8-133">对聚集索引执行多范围填充可以产生最高的填充速度。</span><span class="sxs-lookup"><span data-stu-id="07da8-133">A multi-range population on a clustered index can produce the highest population speed.</span></span> <span data-ttu-id="07da8-134">我们建议充当全文键的列采用整数数据类型。</span><span class="sxs-lookup"><span data-stu-id="07da8-134">We recommend that the column serving as the full-text key be an integer data type.</span></span>  
  
-   <span data-ttu-id="07da8-135">使用 [UPDATE STATISTICS](/sql/t-sql/statements/update-statistics-transact-sql) 语句更新基表的统计信息。</span><span class="sxs-lookup"><span data-stu-id="07da8-135">Update the statistics of the base table by using the [UPDATE STATISTICS](/sql/t-sql/statements/update-statistics-transact-sql) statement.</span></span> <span data-ttu-id="07da8-136">更重要的是，更新聚集索引或全文键的统计信息以进行完全填充。</span><span class="sxs-lookup"><span data-stu-id="07da8-136">More important, update the statistics on the clustered index or the full-text key for a full population.</span></span> <span data-ttu-id="07da8-137">这有助于多范围填充在表上生成良好的分区。</span><span class="sxs-lookup"><span data-stu-id="07da8-137">This helps a multi-range population to generate good partitions on the table.</span></span>  
  
-   <span data-ttu-id="07da8-138">如果要提高增量填充的性能，请对 `timestamp` 列生成辅助索引。</span><span class="sxs-lookup"><span data-stu-id="07da8-138">Build a secondary index on a `timestamp` column if you want to improve the performance of incremental population.</span></span>  
  
-   <span data-ttu-id="07da8-139">在大型多 CPU 计算机上执行完全填充之前，建议您通过设置 `max server memory` 值来暂时限制缓冲池的大小，从而留出足够的内存供 fdhost.exe 进程及操作系统使用。</span><span class="sxs-lookup"><span data-stu-id="07da8-139">Before you perform a full population on a large multi-CPU computer, we recommend that you temporarily limit the size of the buffer pool by setting the `max server memory` value to leave enough memory for the fdhost.exe process and operating system use.</span></span> <span data-ttu-id="07da8-140">有关详细信息，请参阅本主题后面的“估计筛选器后台程序宿主进程 (fdhost.exe) 的内存需求量”。</span><span class="sxs-lookup"><span data-stu-id="07da8-140">For more information, see "Estimating the Memory Requirements of the Filter Daemon Host Process (fdhost.exe)," later in this topic.</span></span>  
  
  
  
##  <a name="troubleshooting-the-performance-of-full-populations"></a><a name="full"></a><span data-ttu-id="07da8-141">完全填充的性能疑难解答</span><span class="sxs-lookup"><span data-stu-id="07da8-141">Troubleshooting the Performance of Full Populations</span></span>  
 <span data-ttu-id="07da8-142">若要诊断性能问题，请查看全文爬网日志。</span><span class="sxs-lookup"><span data-stu-id="07da8-142">To diagnose performance problems, look at the full-text crawl logs.</span></span> <span data-ttu-id="07da8-143">有关爬网日志的信息，请参阅 [填充全文索引](../indexes/indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="07da8-143">For information about crawl logs, see [Populate Full-Text Indexes](../indexes/indexes.md).</span></span>  
  
 <span data-ttu-id="07da8-144">如果对完全填充的性能不满意，则建议按顺序执行以下故障排除步骤。</span><span class="sxs-lookup"><span data-stu-id="07da8-144">It is recommended that the following order of troubleshooting be followed if the performance of full populations is not satisfactory.</span></span>  
  
### <a name="physical-memory-usage"></a><span data-ttu-id="07da8-145">物理内存使用量</span><span class="sxs-lookup"><span data-stu-id="07da8-145">Physical Memory Usage</span></span>  
 <span data-ttu-id="07da8-146">在全文填充期间，fdhost.exe 或 sqlservr.exe 的内存有可能不足。</span><span class="sxs-lookup"><span data-stu-id="07da8-146">During a full-text population, it is possible for fdhost.exe or sqlservr.exe to run low on memory or to run out of memory.</span></span> <span data-ttu-id="07da8-147">如果全文爬网日志显示 fdhost.exe 正在反复重新启动，或系统返回错误代码 8007008，则意味着这些进程中的某一个进程内存不足。</span><span class="sxs-lookup"><span data-stu-id="07da8-147">If the full-text crawl log shows that fdhost.exe is being restarted often or that error code 8007008 is being returned it means one of these processes is running out of memory.</span></span> <span data-ttu-id="07da8-148">如果 fdhost.exe 在生成转储（特别是在大型多 CPU 计算机上），则该进程的内存可能不足。</span><span class="sxs-lookup"><span data-stu-id="07da8-148">If fdhost.exe is producing dumps, particularly on large, multi-CPU computers, it might be running out of memory.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="07da8-149">若要获得有关全文爬网所用的内存缓冲区的信息，请参阅 [sys.dm_fts_memory_buffers (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-memory-buffers-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="07da8-149">To obtain information about memory buffers used by a full-text crawl, see [sys.dm_fts_memory_buffers &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-memory-buffers-transact-sql).</span></span>  
  
 <span data-ttu-id="07da8-150">可能的原因如下：</span><span class="sxs-lookup"><span data-stu-id="07da8-150">The possible causes are as follows:</span></span>  
  
-   <span data-ttu-id="07da8-151">如果在完全填充期间可用的物理内存数量是零，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 缓冲池可能正占用系统的大部分物理内存。</span><span class="sxs-lookup"><span data-stu-id="07da8-151">If amount of physical memory that is available during a full population is zero, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] buffer pool might be consuming most of the physical memory on the system.</span></span>  
  
     <span data-ttu-id="07da8-152">sqlservr.exe 进程试图侵占缓冲池的所有可用内存（最大为配置的最大服务器内存）。</span><span class="sxs-lookup"><span data-stu-id="07da8-152">The sqlservr.exe process tries to grab all available memory for the buffer pool, up to the configured maximum server memory.</span></span> <span data-ttu-id="07da8-153">如果分配的 `max server memory` 过大，fdhost.exe 进程可能会面临内存不足的状况及共享内存分配失败。</span><span class="sxs-lookup"><span data-stu-id="07da8-153">If the `max server memory` allocation is too large, out-of-memory conditions and failure to allocate shared memory can occur for the fdhost.exe process.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="07da8-154">在多 CPU 计算机上进行全文填充期间，fdhost.exe 或 sqlservr.exe 之间可能出现缓冲池内存争用。</span><span class="sxs-lookup"><span data-stu-id="07da8-154">During a full-text population on a multi-CPU computer, contention for the buffer pool memory can occur between fdhost.exe or sqlservr.exe.</span></span> <span data-ttu-id="07da8-155">由此造成的共享内存不足会导致批次重试、内存抖动并让 fdhost.exe 进程进行转储。</span><span class="sxs-lookup"><span data-stu-id="07da8-155">The resulting lack of shared memory causes batch retries, memory thrashing, and dumps by the fdhost.exe process.</span></span>  
  
     <span data-ttu-id="07da8-156">可以通过适当设置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 缓冲池的 `max server memory` 值来解决此问题。</span><span class="sxs-lookup"><span data-stu-id="07da8-156">You can solve this problem by setting the `max server memory` value of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] buffer pool appropriately.</span></span> <span data-ttu-id="07da8-157">有关详细信息，请参阅本主题后面的“估计筛选器后台程序宿主进程 (fdhost.exe) 的内存需求量”。</span><span class="sxs-lookup"><span data-stu-id="07da8-157">For more information, see "Estimating the Memory Requirements of the Filter Daemon Host Process (fdhost.exe)," later in this topic.</span></span> <span data-ttu-id="07da8-158">减小用于全文索引的批次大小可能也会有用。</span><span class="sxs-lookup"><span data-stu-id="07da8-158">Reducing the batch size used for full-text indexing may also help.</span></span>  
  
-   <span data-ttu-id="07da8-159">分页问题</span><span class="sxs-lookup"><span data-stu-id="07da8-159">A paging issue</span></span>  
  
     <span data-ttu-id="07da8-160">页文件大小不足也会导致 fdhost.exe 或 sqlservr.exe 的内存不足，例如在具有增长受限的较小页文件的系统上。</span><span class="sxs-lookup"><span data-stu-id="07da8-160">Insufficient page-file size, such as on a system that has a small page file with restricted growth, can also cause the fdhost.exe or sqlservr.exe to run out of memory.</span></span>  
  
     <span data-ttu-id="07da8-161">如果爬网日志未指示存在任何与内存相关的故障，则很可能是因为过度分页导致性能下降。</span><span class="sxs-lookup"><span data-stu-id="07da8-161">If the crawl logs do not indicate any memory-related failures, it is likely that performance is slow due to excessive paging.</span></span>  
  
  
  
### <a name="estimating-the-memory-requirements-of-the-filter-daemon-host-process-fdhostexe"></a><span data-ttu-id="07da8-162">估计筛选器后台程序宿主进程 (fdhost.exe) 的内存需求量</span><span class="sxs-lookup"><span data-stu-id="07da8-162">Estimating the Memory Requirements of the Filter Daemon Host Process (fdhost.exe)</span></span>  
 <span data-ttu-id="07da8-163">进行填充时 fdhost.exe 进程需要的内存量主要取决于它使用的全文爬网范围数、入站共享内存 (ISM) 的大小以及最大 ISM 实例数。</span><span class="sxs-lookup"><span data-stu-id="07da8-163">The amount of memory required by the fdhost.exe process for a population depends mainly on the number of full-text crawl ranges it uses, the size of inbound shared memory (ISM), and the maximum number of ISM instances.</span></span>  
  
 <span data-ttu-id="07da8-164">可以使用下面的公式粗略估算筛选器后台程序宿主占用的内存量（以字节为单位）：</span><span class="sxs-lookup"><span data-stu-id="07da8-164">The amount of memory (in bytes) consumed by the filter daemon host can be roughly estimated by using the following formula:</span></span>  
  
 <span data-ttu-id="07da8-165">*number_of_crawl_ranges* \`ism_size "*max_outstanding_isms* \* 2</span><span class="sxs-lookup"><span data-stu-id="07da8-165">*number_of_crawl_ranges* \`ism_size\`*max_outstanding_isms*\* 2</span></span>  
  
 <span data-ttu-id="07da8-166">上面公式中的变量的默认值如下所示：</span><span class="sxs-lookup"><span data-stu-id="07da8-166">The default values of the variables in the preceding formula are as follows:</span></span>  
  
|<span data-ttu-id="07da8-167">**变量**</span><span class="sxs-lookup"><span data-stu-id="07da8-167">**Variable**</span></span>|<span data-ttu-id="07da8-168">**默认值**</span><span class="sxs-lookup"><span data-stu-id="07da8-168">**Default value**</span></span>|  
|------------------|-----------------------|  
|<span data-ttu-id="07da8-169">*number_of_crawl_ranges*</span><span class="sxs-lookup"><span data-stu-id="07da8-169">*number_of_crawl_ranges*</span></span>|<span data-ttu-id="07da8-170">CPU 数</span><span class="sxs-lookup"><span data-stu-id="07da8-170">The number of CPUs</span></span>|  
|<span data-ttu-id="07da8-171">*ism_size*</span><span class="sxs-lookup"><span data-stu-id="07da8-171">*ism_size*</span></span>|<span data-ttu-id="07da8-172">x86 计算机为 1 MB</span><span class="sxs-lookup"><span data-stu-id="07da8-172">1 MB for x86 computers</span></span><br /><br /> <span data-ttu-id="07da8-173">x64 计算机为 4 MB、8 MB 或 16MB，具体取决于物理内存总量</span><span class="sxs-lookup"><span data-stu-id="07da8-173">4 MB, 8 MB, or 16MB for x64 computers, depending on the total physical memory</span></span>|  
|<span data-ttu-id="07da8-174">*max_outstanding_isms*</span><span class="sxs-lookup"><span data-stu-id="07da8-174">*max_outstanding_isms*</span></span>|<span data-ttu-id="07da8-175">x86 计算机为 25</span><span class="sxs-lookup"><span data-stu-id="07da8-175">25 for x86 computers</span></span><br /><br /> <span data-ttu-id="07da8-176">x64 计算机为 5</span><span class="sxs-lookup"><span data-stu-id="07da8-176">5 for x64 computers</span></span>|  
  
 <span data-ttu-id="07da8-177">下表列出了有关如何估算 fdhost.exe 的内存需求量的准则。</span><span class="sxs-lookup"><span data-stu-id="07da8-177">The following table presents guidelines about how to estimate the memory requirements of fdhost.exe.</span></span> <span data-ttu-id="07da8-178">此表中的公式使用以下值：</span><span class="sxs-lookup"><span data-stu-id="07da8-178">The formulas in this table use the following values:</span></span>  
  
-   <span data-ttu-id="07da8-179">*F*，它是 fdhost.exe 所需内存的估计值（以 MB 为单位）。</span><span class="sxs-lookup"><span data-stu-id="07da8-179">*F*, which is an estimate of memory needed by fdhost.exe (in MB).</span></span>  
  
-   <span data-ttu-id="07da8-180">*T*，它是系统中可用物理内存的总量（以 MB 为单位）。</span><span class="sxs-lookup"><span data-stu-id="07da8-180">*T*, which is the total physical memory available on the system (in MB).</span></span>  
  
-   <span data-ttu-id="07da8-181">*M*，这是最佳 `max server memory` 设置。</span><span class="sxs-lookup"><span data-stu-id="07da8-181">*M*, which is the optimal `max server memory` setting.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="07da8-182">有关公式的基本信息，请参阅下面的<sup>1</sup>、 <sup>2</sup>和<sup>3</sup>。</span><span class="sxs-lookup"><span data-stu-id="07da8-182">For essential information about the formulas, see <sup>1</sup>, <sup>2</sup>, and <sup>3</sup>, below.</span></span>  
  
|<span data-ttu-id="07da8-183">平台</span><span class="sxs-lookup"><span data-stu-id="07da8-183">Platform</span></span>|<span data-ttu-id="07da8-184">估计 fdhost.exe 内存需求（以 MB 为单位）-*F*<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="07da8-184">Estimating fdhost.exe memory requirements in MB-*F*<sup>1</sup></span></span>|<span data-ttu-id="07da8-185">用于计算最大服务器内存的公式-*M*<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="07da8-185">Formula for calculating max server memory-*M*<sup>2</sup></span></span>|  
|--------------|---------------------------------------------------------------------|---------------------------------------------------------------|  
|<span data-ttu-id="07da8-186">x86</span><span class="sxs-lookup"><span data-stu-id="07da8-186">x86</span></span>|<span data-ttu-id="07da8-187">_F_ **=** **&#42;** 50_的爬网范围数_</span><span class="sxs-lookup"><span data-stu-id="07da8-187">_F_ **=** _Number of crawl ranges_ **&#42;** 50</span></span>|<span data-ttu-id="07da8-188">_M_ **= 最小 (** _T_ **，** 2000 **) *`F`* - -** 500</span><span class="sxs-lookup"><span data-stu-id="07da8-188">_M_ **=minimum(** _T_ **,** 2000 **)-*`F`*-** 500</span></span>|  
|<span data-ttu-id="07da8-189">X64</span><span class="sxs-lookup"><span data-stu-id="07da8-189">x64</span></span>|<span data-ttu-id="07da8-190">_F_ **=** **&#42;** 10 **&#42;** 8_的爬网范围数_</span><span class="sxs-lookup"><span data-stu-id="07da8-190">_F_ **=** _Number of crawl ranges_ **&#42;** 10 **&#42;** 8</span></span>|<span data-ttu-id="07da8-191">_M_ **=** _T_ **-** _F_ **-** 500</span><span class="sxs-lookup"><span data-stu-id="07da8-191">_M_ **=** _T_ **-** _F_ **-** 500</span></span>|  
  
 <span data-ttu-id="07da8-192"><sup>1</sup>如果正在进行多个完全填充，则分别计算每个完全填充的 fdhost.exe 内存需求，如*F1*、 *F2*等。</span><span class="sxs-lookup"><span data-stu-id="07da8-192"><sup>1</sup> If multiple full populations are in progress, calculate the fdhost.exe memory requirements of each separately, as *F1*, *F2*, and so forth.</span></span> <span data-ttu-id="07da8-193">然后计算 M 为 T- sigma(_F_i)  。</span><span class="sxs-lookup"><span data-stu-id="07da8-193">Then calculate *M* as _T_**-** sigma **(**_F_i **)**.</span></span>  
  
 <span data-ttu-id="07da8-194"><sup>2</sup> 500 MB 是系统中其他进程所需内存的估计值。</span><span class="sxs-lookup"><span data-stu-id="07da8-194"><sup>2</sup> 500 MB is an estimate of the memory required by other processes in the system.</span></span> <span data-ttu-id="07da8-195">如果系统正在执行其他工作，请相应地增加此值。</span><span class="sxs-lookup"><span data-stu-id="07da8-195">If the system is doing additional work, increase this value accordingly.</span></span>  
  
 <span data-ttu-id="07da8-196"><sup>3</sup> 。对于 x64 平台， *ism_size*假定为 8 MB。</span><span class="sxs-lookup"><span data-stu-id="07da8-196"><sup>3</sup> .*ism_size* is assumed to be 8 MB for x64 platforms.</span></span>  
  
 <span data-ttu-id="07da8-197">**示例：估计 fdhost.exe 的内存需求量**</span><span class="sxs-lookup"><span data-stu-id="07da8-197">**Example: Estimating the Memory Requirements of fdhost.exe**</span></span>  
  
 <span data-ttu-id="07da8-198">此示例针对具有 8GM RAM 和 4 个双核处理器的 AMD64 计算机。</span><span class="sxs-lookup"><span data-stu-id="07da8-198">This example is for an AMD64 computer that has 8GM of RAM and 4 dual core processors.</span></span> <span data-ttu-id="07da8-199">首先计算出 fdhost.exe 所需内存的估计值 -F。</span><span class="sxs-lookup"><span data-stu-id="07da8-199">The first calculation estimates of memory needed by fdhost.exe-*F*.</span></span> <span data-ttu-id="07da8-200">爬网范围数是 `8`。</span><span class="sxs-lookup"><span data-stu-id="07da8-200">The number of crawl ranges is `8`.</span></span>  
  
 `F = 8*10*8=640`  
  
 <span data-ttu-id="07da8-201">下一个计算获取 M 的最佳值 `max server memory` - *M*。</span><span class="sxs-lookup"><span data-stu-id="07da8-201">The next calculation obtains the optimal value for `max server memory`-*M*.</span></span> <span data-ttu-id="07da8-202">*T*此系统上的可用物理内存总量（以 MB 为*单位）为*单位 `8192` 。</span><span class="sxs-lookup"><span data-stu-id="07da8-202">*T*he total physical memory available on this system in MB-*T*-is `8192`.</span></span>  
  
 `M = 8192-640-500=7052`  
  
 <span data-ttu-id="07da8-203">**示例：设置最大服务器内存**</span><span class="sxs-lookup"><span data-stu-id="07da8-203">**Example: Setting max server memory**</span></span>  
  
 <span data-ttu-id="07da8-204">此示例使用[sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)和[重新配置](/sql/t-sql/language-elements/reconfigure-transact-sql) [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句，以便在 `max server memory` 前面的示例中为*M*计算的值设置 `7052` ：</span><span class="sxs-lookup"><span data-stu-id="07da8-204">This example uses the [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) and [RECONFIGURE](/sql/t-sql/language-elements/reconfigure-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] statements to set `max server memory` to the value calculated for *M* in the preceding example, `7052`:</span></span>  
  
```  
USE master;  
GO  
EXEC sp_configure 'max server memory', 7052;  
GO  
RECONFIGURE;  
GO  
```  
  
 <span data-ttu-id="07da8-205">**设置最大服务器内存配置选项**</span><span class="sxs-lookup"><span data-stu-id="07da8-205">**To set the max server memory configuration option**</span></span>  
  
-   [<span data-ttu-id="07da8-206">“服务器内存”服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="07da8-206">Server Memory Server Configuration Options</span></span>](../../database-engine/configure-windows/server-memory-server-configuration-options.md)  
  
  
  
### <a name="factors-that-can-reduce-cpu-consumption"></a><span data-ttu-id="07da8-207">可以降低 CPU 占用率的因素</span><span class="sxs-lookup"><span data-stu-id="07da8-207">Factors that Can Reduce CPU Consumption</span></span>  
 <span data-ttu-id="07da8-208">我们希望当平均 CPU 占用率低于大约 30% 时完全填充的性能不是最佳的。</span><span class="sxs-lookup"><span data-stu-id="07da8-208">We expect that the performance of full populations is not optimal when the average CPU consumption is lower than about 30 percent.</span></span> <span data-ttu-id="07da8-209">本节讨论影响 CPU 占用率的一些因素。</span><span class="sxs-lookup"><span data-stu-id="07da8-209">This section discusses some factors that affect CPU consumption.</span></span>  
  
-   <span data-ttu-id="07da8-210">长时间等待页面</span><span class="sxs-lookup"><span data-stu-id="07da8-210">High wait for pages</span></span>  
  
     <span data-ttu-id="07da8-211">若要了解等待页面的时间是否太长，请执行下面的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句：</span><span class="sxs-lookup"><span data-stu-id="07da8-211">To find out whether a page wait time is high, execute the following [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement:</span></span>  
  
    ```  
    Execute SELECT TOP 10 * FROM sys.dm_os_wait_stats ORDER BY wait_time_ms DESC;  
    ```  
  
     <span data-ttu-id="07da8-212">下表描述了这里需要了解的等待类型。</span><span class="sxs-lookup"><span data-stu-id="07da8-212">The following table describes the wait types of interest here.</span></span>  
  
    |<span data-ttu-id="07da8-213">等待类型</span><span class="sxs-lookup"><span data-stu-id="07da8-213">Wait type</span></span>|<span data-ttu-id="07da8-214">说明</span><span class="sxs-lookup"><span data-stu-id="07da8-214">Description</span></span>|<span data-ttu-id="07da8-215">可能的解决方法</span><span class="sxs-lookup"><span data-stu-id="07da8-215">Possible resolution</span></span>|  
    |---------------|-----------------|-------------------------|  
    |<span data-ttu-id="07da8-216">PAGEIO_LATCH_SH（_EX 或 _UP）</span><span class="sxs-lookup"><span data-stu-id="07da8-216">PAGEIO_LATCH_SH (_EX or _UP)</span></span>|<span data-ttu-id="07da8-217">这可能表明存在 IO 瓶颈，在此情况下通常还会发现平均磁盘队列长度很高。</span><span class="sxs-lookup"><span data-stu-id="07da8-217">This could indicate an IO bottleneck, in which case you would typically also see a high average disk-queue length.</span></span>|<span data-ttu-id="07da8-218">将全文索引移动到其他磁盘上的其他文件组可能有助于减少 IO 瓶颈。</span><span class="sxs-lookup"><span data-stu-id="07da8-218">Moving the full-text index to a different filegroup on a different disk could help reduce the IO bottleneck.</span></span>|  
    |<span data-ttu-id="07da8-219">PAGELATCH_EX（或 _UP）</span><span class="sxs-lookup"><span data-stu-id="07da8-219">PAGELATCH_EX (or _UP)</span></span>|<span data-ttu-id="07da8-220">这可能表明多个正在试图写入相同数据库文件的线程之间存在大量争用现象。</span><span class="sxs-lookup"><span data-stu-id="07da8-220">This could indicate a lot of contention among threads that are trying to write to the same database file.</span></span>|<span data-ttu-id="07da8-221">将文件添加到全文索引所在的文件组可能有助于减轻此类争用。</span><span class="sxs-lookup"><span data-stu-id="07da8-221">Adding files to the filegroup on which the fulltext index resides could help alleviate such contention.</span></span>|  
  
     <span data-ttu-id="07da8-222">有关详细信息，请参阅 [sys.dm_os_wait_stats (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="07da8-222">For more information, see [sys.dm_os_wait_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql).</span></span>  
  
-   <span data-ttu-id="07da8-223">扫描基表的效率很低</span><span class="sxs-lookup"><span data-stu-id="07da8-223">Inefficiencies in scanning the base table</span></span>  
  
     <span data-ttu-id="07da8-224">完全填充将扫描基表，以生成批次。</span><span class="sxs-lookup"><span data-stu-id="07da8-224">A full population scans the base table to produce batches.</span></span> <span data-ttu-id="07da8-225">在下列情况下，这样的表扫描可能很低效：</span><span class="sxs-lookup"><span data-stu-id="07da8-225">This table scanning could be inefficient in the following scenarios:</span></span>  
  
    -   <span data-ttu-id="07da8-226">如果基表有很高百分比的行外列正在建立全文索引，则扫描基表以生成批次可能成为瓶颈。</span><span class="sxs-lookup"><span data-stu-id="07da8-226">If the base table has a high percentage of out-of-row columns that are being full-text indexed, scanning the base table to produce batches might be the bottleneck.</span></span> <span data-ttu-id="07da8-227">在这种情况下，使用 `varchar(max)` 或 `nvarchar(max)` 对较小的数据进行行内移动可能有用。</span><span class="sxs-lookup"><span data-stu-id="07da8-227">In this case, moving the smaller data in-row using `varchar(max)` or `nvarchar(max)` might help.</span></span>  
  
    -   <span data-ttu-id="07da8-228">如果基表非常零碎，扫描可能很低效。</span><span class="sxs-lookup"><span data-stu-id="07da8-228">If the base table is very fragmented, scanning might be inefficient.</span></span> <span data-ttu-id="07da8-229">有关计算行外数据和索引碎片的信息，请参阅 [sys.dm_db_partition_stats (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-partition-stats-transact-sql) 和 [sys.dm_db_index_physical_stats (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="07da8-229">For information about computing out-of-row data and index fragmentation, see [sys.dm_db_partition_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-partition-stats-transact-sql) and [sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql).</span></span>  
  
         <span data-ttu-id="07da8-230">若要减少碎片，可以重新组织或重新生成聚集索引。</span><span class="sxs-lookup"><span data-stu-id="07da8-230">To reduce fragmentation, you can reorganize or rebuild the clustered index.</span></span> <span data-ttu-id="07da8-231">有关详细信息，请参阅 [重新组织和重新生成索引](../indexes/reorganize-and-rebuild-indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="07da8-231">For more information, see [Reorganize and Rebuild Indexes](../indexes/reorganize-and-rebuild-indexes.md).</span></span>  
  
  
  
##  <a name="troubleshooting-slow-indexing-performance-due-to-filters"></a><a name="filters"></a><span data-ttu-id="07da8-232">由于筛选器导致索引编制性能缓慢的疑难解答</span><span class="sxs-lookup"><span data-stu-id="07da8-232">Troubleshooting Slow Indexing Performance Due to Filters</span></span>  
 <span data-ttu-id="07da8-233">在填充全文索引时，全文引擎使用以下两种类型的筛选器：多线程筛选器和单线程筛选器。</span><span class="sxs-lookup"><span data-stu-id="07da8-233">When populating a full-text index, the Full-Text Engine uses two types of filters: multithreaded and single-threaded.</span></span> <span data-ttu-id="07da8-234">有些文档（如 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Word 文档）使用多线程筛选器进行筛选。</span><span class="sxs-lookup"><span data-stu-id="07da8-234">Some documents, such as [!INCLUDE[msCoName](../../includes/msconame-md.md)] Word documents, are filtered using a multithreaded filter.</span></span> <span data-ttu-id="07da8-235">另外一些文档使用单线程筛选器进行筛选，如 Adobe Acrobat 可移植文档格式 (PDF) 文档。</span><span class="sxs-lookup"><span data-stu-id="07da8-235">Other documents, such as Adobe Acrobat Portable Document Format (PDF) documents, are filtered using a single-threaded filter.</span></span>  
  
 <span data-ttu-id="07da8-236">为了安全起见，筛选器是由筛选器后台程序主机进程加载的。</span><span class="sxs-lookup"><span data-stu-id="07da8-236">For security reasons, filters are loaded by filter daemon host processes.</span></span> <span data-ttu-id="07da8-237">服务器实例对所有多线程筛选器使用多线程进程，并对所有单线程筛选器使用单线程进程。</span><span class="sxs-lookup"><span data-stu-id="07da8-237">A server instance uses a multithreaded process for all multithreaded filters and a single-threaded process for all single-threaded filters.</span></span> <span data-ttu-id="07da8-238">如果使用多线程筛选器的文档包含使用单线程筛选器的嵌入文档，全文引擎将启动单线程进程以处理嵌入文档。</span><span class="sxs-lookup"><span data-stu-id="07da8-238">When a document that uses a multithreaded filter contains an embedded document that uses a single-threaded filter, the Full-Text Engine launches a single-threaded process for the embedded document.</span></span> <span data-ttu-id="07da8-239">例如，在遇到包含 PDF 文档的 Word 文档时，全文引擎使用多线程进程来处理 Word 内容，并启动单线程进程以处理 PDF 内容。</span><span class="sxs-lookup"><span data-stu-id="07da8-239">For example, on encountering a Word document that contains a PDF document, the Full-Text Engine uses the multithreaded process for the Word content and launches a single-threaded process for the PDF content.</span></span> <span data-ttu-id="07da8-240">但是，单线程筛选器可能无法在此环境中正常工作，并且可能会破坏筛选进程的稳定性。</span><span class="sxs-lookup"><span data-stu-id="07da8-240">A single-threaded filter might not work well in this environment, however, and could destabilize the filtering process.</span></span> <span data-ttu-id="07da8-241">在某些频繁出现此类嵌入的环境中，它可能会导致筛选进程崩溃。</span><span class="sxs-lookup"><span data-stu-id="07da8-241">In certain circumstances where such embedding is common, destabilization might lead to filtering-process crashes.</span></span> <span data-ttu-id="07da8-242">如果发生这种情况，全文引擎会将任何失败的文档（如包含嵌入 PDF 内容的 Word 文档）重新传送到单线程筛选进程。</span><span class="sxs-lookup"><span data-stu-id="07da8-242">When this occurs, the Full-Text Engine re-routes any failed document (for example, a Word document that contains embedded PDF content) to the single-threaded filtering process.</span></span> <span data-ttu-id="07da8-243">如果频繁进行重新传送，将会导致全文索引进程性能下降。</span><span class="sxs-lookup"><span data-stu-id="07da8-243">If re-routing occurs frequently, it results in performance degradation of the full-text indexing process.</span></span>  
  
 <span data-ttu-id="07da8-244">若要解决该问题，必须将容器文档（此处为 Word 文档）的筛选器标记为单线程筛选器。</span><span class="sxs-lookup"><span data-stu-id="07da8-244">To work around this problem, mark the filter for the container document (Word in this case) as a single-threaded filter.</span></span> <span data-ttu-id="07da8-245">可以更改筛选器注册表值，以便将给定筛选器标记为单线程筛选器。</span><span class="sxs-lookup"><span data-stu-id="07da8-245">You can change the filter registry value to mark a given filter as a single-threaded filter.</span></span> <span data-ttu-id="07da8-246">若要将筛选器标记为单线程筛选器，需要将筛选器的**ThreadingModel**注册表值设置为 `Apartment Threaded` 。</span><span class="sxs-lookup"><span data-stu-id="07da8-246">To mark a filter as a single-threaded filter, you need to set the **ThreadingModel** registry value for the filter to `Apartment Threaded`.</span></span> <span data-ttu-id="07da8-247">有关单线程单元的信息，请参阅白皮书 [了解和使用 COM 线程模型](https://go.microsoft.com/fwlink/?LinkId=209159)。</span><span class="sxs-lookup"><span data-stu-id="07da8-247">For information about single-threaded apartments, see the white paper [Understanding and Using COM Threading Models](https://go.microsoft.com/fwlink/?LinkId=209159).</span></span>  
  
  
  
## <a name="see-also"></a><span data-ttu-id="07da8-248">另请参阅</span><span class="sxs-lookup"><span data-stu-id="07da8-248">See Also</span></span>  
 <span data-ttu-id="07da8-249">[“服务器内存”服务器配置选项](../../database-engine/configure-windows/server-memory-server-configuration-options.md) </span><span class="sxs-lookup"><span data-stu-id="07da8-249">[Server Memory Server Configuration Options](../../database-engine/configure-windows/server-memory-server-configuration-options.md) </span></span>  
 <span data-ttu-id="07da8-250">[max full-text crawl range 服务器配置选项](../../database-engine/configure-windows/max-full-text-crawl-range-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="07da8-250">[max full-text crawl range Server Configuration Option](../../database-engine/configure-windows/max-full-text-crawl-range-server-configuration-option.md) </span></span>  
 <span data-ttu-id="07da8-251">[填充全文索引](populate-full-text-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="07da8-251">[Populate Full-Text Indexes](populate-full-text-indexes.md) </span></span>  
 <span data-ttu-id="07da8-252">[创建和管理全文索引](create-and-manage-full-text-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="07da8-252">[Create and Manage Full-Text Indexes](create-and-manage-full-text-indexes.md) </span></span>  
 <span data-ttu-id="07da8-253">[sys.dm_fts_memory_buffers (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-memory-buffers-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="07da8-253">[sys.dm_fts_memory_buffers &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-memory-buffers-transact-sql) </span></span>  
 <span data-ttu-id="07da8-254">[sys.dm_fts_memory_pools (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-memory-pools-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="07da8-254">[sys.dm_fts_memory_pools &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-memory-pools-transact-sql) </span></span>  
 [<span data-ttu-id="07da8-255">排除全文索引故障</span><span class="sxs-lookup"><span data-stu-id="07da8-255">Troubleshoot Full-Text Indexing</span></span>](troubleshoot-full-text-indexing.md)  
  
  
