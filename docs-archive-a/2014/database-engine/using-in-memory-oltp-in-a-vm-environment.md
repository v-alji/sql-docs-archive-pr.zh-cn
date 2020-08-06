---
title: 在虚拟机环境中使用内存中 OLTP |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 27ec7eb3-3a24-41db-aa65-2f206514c6f9
author: stevestein
ms.author: sstein
ms.openlocfilehash: 83cf785fbcd2df9449d61e328e3bf8e374a6656d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689577"
---
# <a name="using-in-memory-oltp-in-a-vm-environment"></a><span data-ttu-id="f87c1-102">在虚拟机环境下使用内存中 OLTP</span><span class="sxs-lookup"><span data-stu-id="f87c1-102">Using In-Memory OLTP in a VM Environment</span></span>
  <span data-ttu-id="f87c1-103">服务器虚拟化可以帮助你改进应用程序配置、维护、可用性和备份/恢复流程，进而降低 IT 资本和运营成本并提高 IT 效率。</span><span class="sxs-lookup"><span data-stu-id="f87c1-103">Server virtualization can help you lower IT capital and operational costs and attain greater IT efficiency with improved application provisioning, maintenance, availability, and backup/recovery processes.</span></span> <span data-ttu-id="f87c1-104">由于近年来的技术进步，可以更轻松地使用虚拟化来合并复杂的数据库工作负载。</span><span class="sxs-lookup"><span data-stu-id="f87c1-104">With recent technological advances, complex database workloads can be more readily consolidated using virtualization.</span></span> <span data-ttu-id="f87c1-105">本主题说明了在虚拟化环境中使用 [!INCLUDE[hek_1](../includes/hek-1-md.md)] 的最佳做法。</span><span class="sxs-lookup"><span data-stu-id="f87c1-105">This topic covers best practices for using [!INCLUDE[hek_1](../includes/hek-1-md.md)] in a virtualized environment.</span></span>  
  
##  <a name="memory-pre-allocation"></a><a name="bkmk_memoryPreAllocation"></a><span data-ttu-id="f87c1-106">内存预分配</span><span class="sxs-lookup"><span data-stu-id="f87c1-106">Memory pre-allocation</span></span>  
 <span data-ttu-id="f87c1-107">对于虚拟化环境中的内存，更好的性能和增强的支持是两个重要的注意事项。</span><span class="sxs-lookup"><span data-stu-id="f87c1-107">For memory in a virtualized environment, better performance and enhanced support are essential considerations.</span></span> <span data-ttu-id="f87c1-108">您必须能够根据不同虚拟机的要求（高峰负载和非高峰负载）快速将内存分配到虚拟机，同时确保不浪费内存。</span><span class="sxs-lookup"><span data-stu-id="f87c1-108">You must be able to both quickly allocate memory to virtual machines depending on their requirements (peak and off-peak loads) and ensure that the memory is not wasted.</span></span> <span data-ttu-id="f87c1-109">通过 Hyper-V 动态内存功能，可以更灵活地在主机上运行的虚拟机之间分配和管理内存。</span><span class="sxs-lookup"><span data-stu-id="f87c1-109">The Hyper-V Dynamic Memory feature increases agility in how the memory is allocated and managed between virtual machines running on a host.</span></span>  
  
 <span data-ttu-id="f87c1-110">当虚拟化带有内存优化表的数据库时，需要修改一些用于虚拟化和管理 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的最佳做法。</span><span class="sxs-lookup"><span data-stu-id="f87c1-110">Some best practices for virtualizing and managing [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] need to be modified when virtualizing a database with memory-optimized tables.</span></span> <span data-ttu-id="f87c1-111">对于不带有内存优化表的数据库，可遵循两个最佳做法：</span><span class="sxs-lookup"><span data-stu-id="f87c1-111">Without memory-optimized tables, two of the best practices are:</span></span>  
  
-   <span data-ttu-id="f87c1-112">如果使用 MIN_SERVER_MEMORY，最好只分配需要的内存量，以便保留足够内存以用于其他进程（从而避免分页）。</span><span class="sxs-lookup"><span data-stu-id="f87c1-112">If you use MIN_SERVER_MEMORY, it is better to assign only the amount of memory that is required so sufficient memory remains for other processes (thereby avoiding paging).</span></span>  
  
-   <span data-ttu-id="f87c1-113">不要将内存预先分配值设置得过高。</span><span class="sxs-lookup"><span data-stu-id="f87c1-113">Do not set the memory pre-allocation value too high.</span></span> <span data-ttu-id="f87c1-114">否则，其他进程可能无法在需要时获得足够内存，这可能会导致内存分页。</span><span class="sxs-lookup"><span data-stu-id="f87c1-114">Otherwise, other processes may not get sufficient memory at the time when they require it, and this can result in memory paging.</span></span>  
  
 <span data-ttu-id="f87c1-115">如果在数据库带有内存优化表时遵循上述做法，尝试还原和恢复数据库可能会导致数据库处于“恢复挂起”状态，即使你拥有可恢复数据库的足够内存时也是如此。</span><span class="sxs-lookup"><span data-stu-id="f87c1-115">If you follow the above practices for a database with memory-optimized tables, an attempt to restore and recover a database could result in the database being in a "Recovery Pending" state, even if you have sufficient memory to recover the database.</span></span> <span data-ttu-id="f87c1-116">原因在于，与动态内存分配功能将内存分配至数据库相比， [!INCLUDE[hek_2](../includes/hek-2-md.md)] 在启动时以更主动的方式将数据存入内存。</span><span class="sxs-lookup"><span data-stu-id="f87c1-116">The reason for this is that, when starting up, [!INCLUDE[hek_2](../includes/hek-2-md.md)] brings data into memory more aggressively than dynamic memory allocation allocates memory to the database.</span></span>  
  
 <span data-ttu-id="f87c1-117">**解决方法**</span><span class="sxs-lookup"><span data-stu-id="f87c1-117">**Resolution**</span></span>  
  
 <span data-ttu-id="f87c1-118">要缓解此问题，请将足够内存预先分配至数据库以恢复或重新启动数据库，而不要分配最小值，依靠动态内存在需要时分配更多内存。</span><span class="sxs-lookup"><span data-stu-id="f87c1-118">To mitigate this, pre-allocate sufficient memory to the database to recover or restart the database, not a minimum value relying on dynamic memory to provide the additional memory when needed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f87c1-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f87c1-119">See Also</span></span>  
 [<span data-ttu-id="f87c1-120">内存中 OLTP（内存中优化）</span><span class="sxs-lookup"><span data-stu-id="f87c1-120">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
