---
title: 内存优化的文件组 | Microsoft Docs
ms.custom: ''
ms.date: 11/19/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 14106cc9-816b-493a-bcb9-fe66a1cd4630
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a4ab6423159d0ba5a27af152cc5578905f57eec6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590805"
---
# <a name="the-memory-optimized-filegroup"></a><span data-ttu-id="0953c-102">内存优化的文件组</span><span class="sxs-lookup"><span data-stu-id="0953c-102">The Memory Optimized Filegroup</span></span>
  <span data-ttu-id="0953c-103">若要创建内存优化表，必须首先创建内存优化的文件组。</span><span class="sxs-lookup"><span data-stu-id="0953c-103">To create memory-optimized tables, you must first create a memory-optimized filegroup.</span></span> <span data-ttu-id="0953c-104">内存优化的文件组容纳一个或多个容器。</span><span class="sxs-lookup"><span data-stu-id="0953c-104">The memory-optimized filegroup holds one or more containers.</span></span> <span data-ttu-id="0953c-105">每个容器都包含数据文件或差异文件，或是同时包含两者。</span><span class="sxs-lookup"><span data-stu-id="0953c-105">Each container contains data files or delta files or both.</span></span>  
  
 <span data-ttu-id="0953c-106">即使 `SCHEMA_ONLY` 表中的数据行未保留，并且内存优化表和本机编译的存储过程中的元数据存储在传统目录中，[!INCLUDE[hek_2](../../includes/hek-2-md.md)] 引擎仍需要 `SCHEMA_ONLY` 内存优化表的内存优化的文件组来提供针对带内存优化表的数据库的一致体验。</span><span class="sxs-lookup"><span data-stu-id="0953c-106">Even though data rows from `SCHEMA_ONLY` tables are not persisted and the metadata for memory-optimized tables and natively compiled stored procedures is stored in the traditional catalogs, the [!INCLUDE[hek_2](../../includes/hek-2-md.md)] engine still requires a memory-optimized filegroup for `SCHEMA_ONLY` memory-optimized tables to provide a uniform experience for databases with memory-optimized tables.</span></span>  
  
 <span data-ttu-id="0953c-107">内存优化的文件组基于文件流文件组，具有以下差异：</span><span class="sxs-lookup"><span data-stu-id="0953c-107">The memory-optimized filegroup is based on filestream filegroup, with the following differences:</span></span>  
  
-   <span data-ttu-id="0953c-108">只能为每个数据库创建一个内存优化的文件组。</span><span class="sxs-lookup"><span data-stu-id="0953c-108">You can only create one memory-optimized filegroup per database.</span></span> <span data-ttu-id="0953c-109">您需要将文件组显式标记为包含 memory_optimized_data。</span><span class="sxs-lookup"><span data-stu-id="0953c-109">You need to explicitly mark the filegroup as containing memory_optimized_data.</span></span> <span data-ttu-id="0953c-110">可以在创建数据库时创建文件组，也可以稍后添加文件组：</span><span class="sxs-lookup"><span data-stu-id="0953c-110">You can create the filegroup when you create the database or you can add it later:</span></span>  
  
    ```sql  
    ALTER DATABASE imoltp ADD FILEGROUP imoltp_mod CONTAINS MEMORY_OPTIMIZED_DATA  
    ```  
  
-   <span data-ttu-id="0953c-111">您需要将一个或多个容器添加到 MEMORY_OPTIMIZED_DATA 文件组。</span><span class="sxs-lookup"><span data-stu-id="0953c-111">You need to add one or more containers to the MEMORY_OPTIMIZED_DATA filegroup.</span></span> <span data-ttu-id="0953c-112">例如：</span><span class="sxs-lookup"><span data-stu-id="0953c-112">For example:</span></span>  
  
    ```sql  
    ALTER DATABASE imoltp ADD FILE (name='imoltp_mod1', filename='c:\data\imoltp_mod1') TO FILEGROUP imoltp_mod  
    ```  
  
-   <span data-ttu-id="0953c-113">你无需启用文件流（[启用和配置 FILESTREAM](../blob/enable-and-configure-filestream.md)）来创建内存优化文件组。</span><span class="sxs-lookup"><span data-stu-id="0953c-113">You do not need to enable filestream ([Enable and Configure FILESTREAM](../blob/enable-and-configure-filestream.md)) to create a memory-optimized filegroup.</span></span> <span data-ttu-id="0953c-114">通过 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 引擎完成与文件流的映射。</span><span class="sxs-lookup"><span data-stu-id="0953c-114">The mapping to filestream is done by the [!INCLUDE[hek_2](../../includes/hek-2-md.md)] engine.</span></span>  
  
-   <span data-ttu-id="0953c-115">可以将新容器添加到内存优化的文件组。</span><span class="sxs-lookup"><span data-stu-id="0953c-115">You can add new containers to a memory-optimized filegroup.</span></span> <span data-ttu-id="0953c-116">你可能需要一个新容器来扩展持久内存优化表所需的存储，还可以在多个容器之间分配 i/o。</span><span class="sxs-lookup"><span data-stu-id="0953c-116">You may need a new container to expand the storage needed for durable memory-optimized table and also to distribute I/O across multiple containers.</span></span>  
  
-   <span data-ttu-id="0953c-117">在 AlwaysOn 可用性组配置中优化与内存优化的文件组相关的数据移动。</span><span class="sxs-lookup"><span data-stu-id="0953c-117">Data movement with a memory-optimized filegroup is optimized in an AlwaysOn Availability Group configuration.</span></span> <span data-ttu-id="0953c-118">与发送到辅助副本的文件流文件不同，内存优化的文件组中的检查点文件（数据文件和差异文件）不会发送到辅助副本。</span><span class="sxs-lookup"><span data-stu-id="0953c-118">Unlike filestream files that are sent to secondary replicas, the checkpoint files (both data and delta) within the memory-optimized filegroup are not sent to secondary replicas.</span></span> <span data-ttu-id="0953c-119">使用辅助副本上的事务日志构造数据文件和差异文件。</span><span class="sxs-lookup"><span data-stu-id="0953c-119">The data and delta files are constructed using the transaction log on the secondary replica.</span></span>  
  
<span data-ttu-id="0953c-120">以下是内存优化的文件组的限制：</span><span class="sxs-lookup"><span data-stu-id="0953c-120">The following limitations of memory-optimized filegroup,</span></span>  
  
-   <span data-ttu-id="0953c-121">创建内存优化的文件组后，您只能通过删除数据库来删除它。</span><span class="sxs-lookup"><span data-stu-id="0953c-121">Once you create a memory-optimized filegroup, you can only remove it by dropping the database.</span></span> <span data-ttu-id="0953c-122">在生产环境中，您不太可能需要删除内存优化的文件组。</span><span class="sxs-lookup"><span data-stu-id="0953c-122">In a production environment, it is unlikely that you will need to remove the memory-optimized filegroup.</span></span>  
  
-   <span data-ttu-id="0953c-123">在内存优化的文件组中，您无法删除非空容器或将数据和差异文件对移至另一个容器。</span><span class="sxs-lookup"><span data-stu-id="0953c-123">You cannot drop a non-empty container or move data and delta file pairs to another container in the memory-optimized filegroup.</span></span>  
  
## <a name="configuring-a-memory-optimized-filegroup"></a><span data-ttu-id="0953c-124">配置内存优化的文件组</span><span class="sxs-lookup"><span data-stu-id="0953c-124">Configuring a Memory-Optimized Filegroup</span></span>  
<span data-ttu-id="0953c-125">请考虑在内存优化的文件组中创建多个容器，并在不同的驱动器上分配这些容器以实现更多带宽来将数据流式传输到内存中。</span><span class="sxs-lookup"><span data-stu-id="0953c-125">Consider creating multiple containers in the memory-optimized filegroup and distribute them on different drives to achieve more bandwidth to stream the data into memory.</span></span>  
  
<span data-ttu-id="0953c-126">在配置存储时，您必须提供大小为持久内存优化表大小的四倍的可用磁盘空间。</span><span class="sxs-lookup"><span data-stu-id="0953c-126">When configuring storage, you must provide free disk space that is four times the size of durable memory-optimized tables.</span></span> <span data-ttu-id="0953c-127">请确保 i/o 子系统支持工作负荷所需的 IOPS。</span><span class="sxs-lookup"><span data-stu-id="0953c-127">Ensure that your I/O subsystem supports the required IOPS for your workload.</span></span> <span data-ttu-id="0953c-128">如果按给定的 IOPS 填充数据和差异文件对，则您需要考虑按 3 倍的 IOPS 来进行存储和合并操作。</span><span class="sxs-lookup"><span data-stu-id="0953c-128">If data and delta file pairs are populated at a given IOPS, you need three times that IOPS to account for storing and merge operations.</span></span> <span data-ttu-id="0953c-129">可以通过将一个或多个容器添加到内存优化的文件组来增加存储容量和 IOPS。</span><span class="sxs-lookup"><span data-stu-id="0953c-129">You can add storage capacity and IOPS by adding one or more containers to the memory-optimized filegroup.</span></span>  
  
<span data-ttu-id="0953c-130">在具有多个容器和多个驱动器的情况下，采用循环法将数据和差异文件分配到容器中。</span><span class="sxs-lookup"><span data-stu-id="0953c-130">In a multiple container, multiple drive scenario, data and delta files are allocated in a round-robin fashion into containers.</span></span> <span data-ttu-id="0953c-131">从第一个容器中分配第一个数据文件，并从下一个容器中分配差异文件，随后按此分配模式重复操作。</span><span class="sxs-lookup"><span data-stu-id="0953c-131">The first data file is allocated from the first container and the delta file is allocated from the next container and this allocation pattern repeats.</span></span> <span data-ttu-id="0953c-132">如果您有奇数个驱动器，并且每个驱动器均映射到一个容器，则此分配方案将跨容器均匀分配数据和差异文件。</span><span class="sxs-lookup"><span data-stu-id="0953c-132">This allocation scheme distributes data and delta files evenly across containers if you have an odd number of drives, each mapped to one container.</span></span> <span data-ttu-id="0953c-133">但是，如果您有偶数个驱动器，并且每个驱动器均映射到一个容器，则可能会导致存储不均衡，其中数据文件映射到奇数个驱动器，而差异文件映射到偶数个驱动器。</span><span class="sxs-lookup"><span data-stu-id="0953c-133">However, if you have an even number of drives, each mapped to a container, it can result in imbalanced storage with data files mapped to odd drives and delta files mapped to even drives.</span></span> <span data-ttu-id="0953c-134">若要在恢复时获取平衡的 i/o 流，请考虑将数据和差异文件对放置在相同的轴/存储上，如以下示例中所述。</span><span class="sxs-lookup"><span data-stu-id="0953c-134">To obtain a balanced stream of I/O on recovery, consider placing pairs of data and delta files on the same spindles/storage as described in the example below.</span></span>  

> [!CAUTION]
> <span data-ttu-id="0953c-135">如果为内存优化文件组设置了 `MAXSIZE` 值，且检查点文件超过容器的最大大小，则数据库将变为 SUSPECT 状态。</span><span class="sxs-lookup"><span data-stu-id="0953c-135">If a `MAXSIZE` value is set for the memory-optimized filegroup, and checkpoint files exceed the max size of the container, then the database will become SUSPECT.</span></span>   
> <span data-ttu-id="0953c-136">在这种情况下，不要尝试将数据库设置为“OFFLINE”和“ONLINE”，这将导致数据库处于 RECOVERY_PENDING 状态。</span><span class="sxs-lookup"><span data-stu-id="0953c-136">In this case do not attempt to set the database OFFLINE and ONLINE, causing the database to stay in RECOVERY_PENDING state.</span></span>
  
### <a name="example"></a><span data-ttu-id="0953c-137">示例</span><span class="sxs-lookup"><span data-stu-id="0953c-137">Example</span></span> 
<span data-ttu-id="0953c-138">假设有一个包含两个容器的内存优化文件组：驱动器 X 上的容器1和驱动器 Y 上的容器2。</span><span class="sxs-lookup"><span data-stu-id="0953c-138">Consider a memory-optimized filegroup with two containers: container 1 on drive X and container 2 on drives Y.</span></span>  
<span data-ttu-id="0953c-139">由于采用循环法分配数据文件和差异文件，因此容器 1 将只包含数据文件，容器 2 将只包含差异文件，这会导致存储的持久性和每秒输入/输出操作数失衡，因为数据文件要比差异文件大得多。</span><span class="sxs-lookup"><span data-stu-id="0953c-139">Since the allocation of data and delta files is done in round-robin fashion, container 1 will only have data files and container 2 will only have delta files, which leads to imbalanced persistence for storage as well as input/output operations per second, as data files are significantly larger than the delta files.</span></span>    
<span data-ttu-id="0953c-140">若要跨驱动器 X 和 Y 统一分布数据和差异文件，请创建四个容器而不是两个，并将前两个容器映射到驱动器 X，并将接下来的两个容器映射到驱动器 Y。</span><span class="sxs-lookup"><span data-stu-id="0953c-140">To distribute data and delta files uniformly across drives X and Y, create four containers instead of two, and map the first two containers to drive X and the next two containers to drive Y.</span></span>  
<span data-ttu-id="0953c-141">对于轮循机制分配，第一个数据和第一个差异文件将分别从第1个和第2个容器（映射到驱动器 X）分配。</span><span class="sxs-lookup"><span data-stu-id="0953c-141">With round-robin allocation, the first data and first delta file will be allocated from container-1 and container-2 respectively, which are mapped to drive X.</span></span>   
<span data-ttu-id="0953c-142">同样，接下来的数据和差异文件将从映射到驱动器 Y 的第3个容器和第4个容器进行分配。这样就可以统一地跨两个驱动器分发数据和差异文件。</span><span class="sxs-lookup"><span data-stu-id="0953c-142">Similarly, the next data and delta file will be allocated from container-3 and container-4 which are mapped to drive Y. This allows distributing data and delta files across two drives uniformly.</span></span>  
 
  
## <a name="see-also"></a><span data-ttu-id="0953c-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0953c-143">See Also</span></span>  
<span data-ttu-id="0953c-144">[创建和管理用于内存优化对象的存储](creating-and-managing-storage-for-memory-optimized-objects.md)   </span><span class="sxs-lookup"><span data-stu-id="0953c-144">[Creating and Managing Storage for Memory-Optimized Objects](creating-and-managing-storage-for-memory-optimized-objects.md)   </span></span>  
[<span data-ttu-id="0953c-145">数据库文件和文件组</span><span class="sxs-lookup"><span data-stu-id="0953c-145">Database Files and Filegroups</span></span>](../../relational-databases/databases/database-files-and-filegroups.md)    
  
