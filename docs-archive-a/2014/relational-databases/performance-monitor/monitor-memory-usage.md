---
title: 监视内存使用量 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- tuning databases [SQL Server], memory
- monitoring server performance [SQL Server], memory usage
- isolating memory [SQL Server]
- paging rate [SQL Server]
- memory [SQL Server], monitoring usage
- monitoring [SQL Server], memory usage
- low-memory conditions
- database monitoring [SQL Server], memory usage
- available memory [SQL Server]
- page faults [SQL Server]
- monitoring performance [SQL Server], memory usage
- server performance [SQL Server], memory
ms.assetid: 1aee3933-a11c-4b87-91b7-32f5ea38c87f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1986d9576f9b067cad18f27d4febbf097ed52703
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692859"
---
# <a name="monitor-memory-usage"></a><span data-ttu-id="bf236-102">监视内存使用量</span><span class="sxs-lookup"><span data-stu-id="bf236-102">Monitor Memory Usage</span></span>
  <span data-ttu-id="bf236-103">定期监视 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例以确认内存使用量在正常范围内。</span><span class="sxs-lookup"><span data-stu-id="bf236-103">Monitor an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] periodically to confirm that memory usage is within typical ranges.</span></span>  
  
 <span data-ttu-id="bf236-104">若要监视内存不足的情况，请使用下列对象计数器：</span><span class="sxs-lookup"><span data-stu-id="bf236-104">To monitor for a low-memory condition, use the following object counters:</span></span>  
  
-   <span data-ttu-id="bf236-105">Memory:Available Bytes</span><span class="sxs-lookup"><span data-stu-id="bf236-105">**Memory: Available Bytes**</span></span>  
  
-   <span data-ttu-id="bf236-106">Memory:Pages/sec</span><span class="sxs-lookup"><span data-stu-id="bf236-106">**Memory: Pages/sec**</span></span>  
  
 <span data-ttu-id="bf236-107">**Available Bytes** 计数器指示当前有多少内存（以字节为单位）可供进程使用。</span><span class="sxs-lookup"><span data-stu-id="bf236-107">The **Available Bytes** counter indicates how many bytes of memory are currently available for use by processes.</span></span> <span data-ttu-id="bf236-108">**Pages/sec** 计数器指示由于页错误而从磁盘取回的页数，或由于页错误而写入磁盘以释放工作集空间的页数。</span><span class="sxs-lookup"><span data-stu-id="bf236-108">The **Pages/sec** counter indicates the number of pages that either were retrieved from disk due to hard page faults or written to disk to free space in the working set due to page faults.</span></span>  
  
 <span data-ttu-id="bf236-109">**Available Bytes** 计数器的值低表示计算机总内存不足或应用程序没有释放内存。</span><span class="sxs-lookup"><span data-stu-id="bf236-109">Low values for the **Available Bytes** counter can indicate that there is an overall shortage of memory on the computer or that an application is not releasing memory.</span></span> <span data-ttu-id="bf236-110">**Pages/sec** 计数器的比率高表示分页过多。</span><span class="sxs-lookup"><span data-stu-id="bf236-110">A high rate for the **Pages/sec** counter could indicate excessive paging.</span></span> <span data-ttu-id="bf236-111">监视 **Memory:** Page Faults/sec 计数器以确保磁盘活动不是由分页造成。</span><span class="sxs-lookup"><span data-stu-id="bf236-111">Monitor the **Memory: Page Faults/sec** counter to make sure that the disk activity is not caused by paging.</span></span>  
  
 <span data-ttu-id="bf236-112">分页率偏低（以及由此产生的页错误）是正常的，即使计算机有大量的可用内存。</span><span class="sxs-lookup"><span data-stu-id="bf236-112">A low rate of paging (and hence page faults) is typical, even if the computer has plenty of available memory.</span></span> <span data-ttu-id="bf236-113">Microsoft Windows 虚拟内存管理器 (VMM) 在剪裁 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和其他进程的工作集大小时会收走这些进程的页。</span><span class="sxs-lookup"><span data-stu-id="bf236-113">The Microsoft Windows Virtual Memory Manager (VMM) takes pages from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and other processes as it trims the working-set sizes of those processes.</span></span> <span data-ttu-id="bf236-114">此 VMM 活动会导致页错误。</span><span class="sxs-lookup"><span data-stu-id="bf236-114">This VMM activity tends to cause page faults.</span></span> <span data-ttu-id="bf236-115">若要确定分页过多是由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 还是由另一个进程导致，请监视 **Process:** Page Faults/sec 计数器，该计数器属于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 处理实例。</span><span class="sxs-lookup"><span data-stu-id="bf236-115">To determine whether [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or another process is the cause of excessive paging, monitor the **Process: Page Faults/sec** counter for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process instance.</span></span>  
  
 <span data-ttu-id="bf236-116">有关解决分页过多的详细信息，请参阅 Windows 操作系统文档。</span><span class="sxs-lookup"><span data-stu-id="bf236-116">For more information about resolving excessive paging, see the Windows operating system documentation.</span></span>  
  
## <a name="isolating-memory-used-by-sql-server"></a><span data-ttu-id="bf236-117">隔离 SQL Server 所用的内存</span><span class="sxs-lookup"><span data-stu-id="bf236-117">Isolating Memory Used by SQL Server</span></span>  
 <span data-ttu-id="bf236-118">默认情况下， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将根据可用系统资源动态改变其内存要求。</span><span class="sxs-lookup"><span data-stu-id="bf236-118">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] changes its memory requirements dynamically, on the basis of available system resources.</span></span> <span data-ttu-id="bf236-119">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 需要更多内存，它会查询操作系统以确定是否有可用的空闲物理内存，然后使用可用内存。</span><span class="sxs-lookup"><span data-stu-id="bf236-119">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] needs more memory, it queries the operating system to determine whether free physical memory is available and uses the available memory.</span></span> <span data-ttu-id="bf236-120">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 当前不需要分配给它的内存，它会将内存释放给操作系统。</span><span class="sxs-lookup"><span data-stu-id="bf236-120">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not need the memory currently allocated to it, it releases the memory to the operating system.</span></span> <span data-ttu-id="bf236-121">但是，你可以覆盖此选项通过使用 **minservermemory**和 **maxservermemory** 服务器配置选项来动态使用内存。</span><span class="sxs-lookup"><span data-stu-id="bf236-121">However, you can override the option to dynamically use memory by using the **minservermemory**, and **maxservermemory** server configuration options.</span></span> <span data-ttu-id="bf236-122">有关详细信息，请参阅 [服务器内存选项](../../database-engine/configure-windows/server-memory-server-configuration-options.md)。</span><span class="sxs-lookup"><span data-stu-id="bf236-122">For more information, see [Server Memory Options](../../database-engine/configure-windows/server-memory-server-configuration-options.md).</span></span>  
  
 <span data-ttu-id="bf236-123">若要监视 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用的内存量，请检查下列性能计数器：</span><span class="sxs-lookup"><span data-stu-id="bf236-123">To monitor the amount of memory that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses, examine the following performance counters:</span></span>  
  
-   <span data-ttu-id="bf236-124">Process:Working Set</span><span class="sxs-lookup"><span data-stu-id="bf236-124">**Process: Working Set**</span></span>  
  
-   <span data-ttu-id="bf236-125">SQL Server：**Buffer Manager:Buffer Cache Hit Ratio**</span><span class="sxs-lookup"><span data-stu-id="bf236-125">**SQL Server: Buffer Manager: Buffer Cache Hit Ratio**</span></span>  
  
-   <span data-ttu-id="bf236-126">SQL Server：**Buffer Manager:Database pages**</span><span class="sxs-lookup"><span data-stu-id="bf236-126">**SQL Server: Buffer Manager: Database Pages**</span></span>  
  
-   <span data-ttu-id="bf236-127">SQL Server：**Memory Manager:Total Server Memory (KB)**</span><span class="sxs-lookup"><span data-stu-id="bf236-127">**SQL Server: Memory Manager: Total Server Memory (KB)**</span></span>  
  
 <span data-ttu-id="bf236-128">**WorkingSet** 计数器显示进程所用的内存量。</span><span class="sxs-lookup"><span data-stu-id="bf236-128">The **WorkingSet** counter shows the amount of memory that is used by a process.</span></span> <span data-ttu-id="bf236-129">如果此内存量一直小于 **min server memory** 和 **max server memory** 服务器选项设置的内存量，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 被配置为使用过多内存。</span><span class="sxs-lookup"><span data-stu-id="bf236-129">If this number is consistently below the amount of memory that is set by the **min server memory** and **max server memory** server options, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is configured to use too much memory.</span></span>  
  
 <span data-ttu-id="bf236-130">**Buffer Cache Hit Ratio** 计数器仅适用于应用程序。</span><span class="sxs-lookup"><span data-stu-id="bf236-130">The **Buffer Cache Hit Ratio** counter is specific to an application.</span></span> <span data-ttu-id="bf236-131">但是，90% 或更高的命中率是令人满意的。</span><span class="sxs-lookup"><span data-stu-id="bf236-131">However, a rate of 90 percent or higher is desirable.</span></span> <span data-ttu-id="bf236-132">添加更多内存，直到该值始终大于 90%。</span><span class="sxs-lookup"><span data-stu-id="bf236-132">Add more memory until the value is consistently greater than 90 percent.</span></span> <span data-ttu-id="bf236-133">大于 90% 的值表示数据缓存满足所有数据请求中 90% 以上的请求。</span><span class="sxs-lookup"><span data-stu-id="bf236-133">A value greater than 90 percent indicates that more than 90 percent of all requests for data were satisfied from the data cache.</span></span>  
  
 <span data-ttu-id="bf236-134">如果 **TotalServerMemory (KB)** 计数器值相对于计算机的物理内存量而言一直很高，则可能表示需要更多内存。</span><span class="sxs-lookup"><span data-stu-id="bf236-134">If the **TotalServerMemory (KB)** counter is consistently high compared to the amount of physical memory in the computer, it may indicate that more memory is required.</span></span>  
  
## <a name="determining-current-memory-allocation"></a><span data-ttu-id="bf236-135">确定当前内存分配</span><span class="sxs-lookup"><span data-stu-id="bf236-135">Determining Current Memory Allocation</span></span>  
 <span data-ttu-id="bf236-136">以下查询返回有关当前分配内存的信息。</span><span class="sxs-lookup"><span data-stu-id="bf236-136">The following query returns information about currently allocated memory.</span></span>  
  
```  
SELECT  
(physical_memory_in_use_kb/1024) AS Memory_usedby_Sqlserver_MB,  
(locked_page_allocations_kb/1024) AS Locked_pages_used_Sqlserver_MB,  
(total_virtual_address_space_kb/1024) AS Total_VAS_in_MB,  
process_physical_memory_low,  
process_virtual_memory_low  
FROM sys.dm_os_process_memory;  
```  
  
  
