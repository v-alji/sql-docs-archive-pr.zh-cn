---
title: SQL Server:Buffer Node | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Buffer Node
- Buffer Node object
ms.assetid: fd3f9f0f-7c38-4cfd-a0c5-ee93dd52d9a5
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 14659e4c1191e2260bccdbcd612f510770913629
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589514"
---
# <a name="sql-serverbuffer-node"></a><span data-ttu-id="2074e-102">SQL Server:Buffer Node</span><span class="sxs-lookup"><span data-stu-id="2074e-102">SQL Server:Buffer Node</span></span>
  <span data-ttu-id="2074e-103">**Buffer Node** 对象提供了对 **Buffer Manager** 对象所提供的计数器进行补充的计数器。</span><span class="sxs-lookup"><span data-stu-id="2074e-103">The **Buffer Node** object provides counters that complement counters provided by the **Buffer Manager** object.</span></span> <span data-ttu-id="2074e-104">通过它，您可以监视每个非一致性内存访问 (NUMA) 节点的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 缓冲池页分布。</span><span class="sxs-lookup"><span data-stu-id="2074e-104">It allows you to monitor the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] buffer pool page distribution for each non-uniform memory access (NUMA) node.</span></span> <span data-ttu-id="2074e-105">对于正在使用的每个 NUMA 节点，都有一个 **Buffer Node** 对象实例。</span><span class="sxs-lookup"><span data-stu-id="2074e-105">There is an instance of the **Buffer Node** object for each NUMA node in use.</span></span> <span data-ttu-id="2074e-106">在非 NUMA 体系结构上，将存在一个单独的 **Buffer Node** 对象实例。</span><span class="sxs-lookup"><span data-stu-id="2074e-106">On non-NUMA architecture, there will be a single instance of the **Buffer Node** object.</span></span>  
  
## <a name="buffer-node-performance-objects"></a><span data-ttu-id="2074e-107">缓冲区节点性能对象</span><span class="sxs-lookup"><span data-stu-id="2074e-107">Buffer Node Performance Objects</span></span>  
 <span data-ttu-id="2074e-108">此表说明了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Buffer Node 性能对象。</span><span class="sxs-lookup"><span data-stu-id="2074e-108">This table describes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Buffer Node** performance objects.</span></span>  
  
|<span data-ttu-id="2074e-109">SQL Server Buffer Node 计数器</span><span class="sxs-lookup"><span data-stu-id="2074e-109">SQL Server Buffer Node counters</span></span>|<span data-ttu-id="2074e-110">说明</span><span class="sxs-lookup"><span data-stu-id="2074e-110">Description</span></span>|  
|-------------------------------------|-----------------|  
|<span data-ttu-id="2074e-111">**Database pages**</span><span class="sxs-lookup"><span data-stu-id="2074e-111">**Database pages**</span></span>|<span data-ttu-id="2074e-112">指示此节点的缓冲池中包含数据库内容的页数。</span><span class="sxs-lookup"><span data-stu-id="2074e-112">Indicates the number of pages in the buffer pool on this node with database content.</span></span>|  
|<span data-ttu-id="2074e-113">**Page life expectancy**</span><span class="sxs-lookup"><span data-stu-id="2074e-113">**Page life expectancy**</span></span>|<span data-ttu-id="2074e-114">指示某页在没有引用的情况下，在此节点的缓冲池中停留的最小时间（秒）。</span><span class="sxs-lookup"><span data-stu-id="2074e-114">Indicates the minimum number of seconds a page will stay in the buffer pool on this node without references.</span></span>|  
|<span data-ttu-id="2074e-115">**Local Node page lookups/sec**</span><span class="sxs-lookup"><span data-stu-id="2074e-115">**Local Node page lookups/sec**</span></span>|<span data-ttu-id="2074e-116">指示从此节点发出并从此节点获得结果的查找请求数。</span><span class="sxs-lookup"><span data-stu-id="2074e-116">Indicates the number of lookup requests from this node which were satisfied from this node.</span></span>|  
|<span data-ttu-id="2074e-117">**Remote Note page lookups/sec**</span><span class="sxs-lookup"><span data-stu-id="2074e-117">**Remote Note page lookups/sec**</span></span>|<span data-ttu-id="2074e-118">指示从此节点发出但从其他节点获得结果的查找请求数。</span><span class="sxs-lookup"><span data-stu-id="2074e-118">Indicates the number of lookup requests from this node which were satisfied from other nodes.</span></span>|  
  
 <span data-ttu-id="2074e-119">如果 SQL Server 在非 NUMA 硬件上运行，则 **Buffer Node** 和 **Buffer Manager** 对象的计数器应该匹配。</span><span class="sxs-lookup"><span data-stu-id="2074e-119">If SQL Server is running on non-NUMA hardware, the counters of **Buffer Node** and **Buffer Manager** objects should match.</span></span>  
  
 <span data-ttu-id="2074e-120">在 NUMA 硬件上，所有 **Buffer Node** 的相应计数器的总和应该与所有 **Buffer Manager**的相应计数器的总和匹配。</span><span class="sxs-lookup"><span data-stu-id="2074e-120">On NUMA hardware, sums of respective counters of all **Buffer Nodes** should match their counterparts of **Buffer Manager**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2074e-121">由于计数器具有动态性以及抽样准确性有所偏差，计数器的值与总和可能不会精确匹配。</span><span class="sxs-lookup"><span data-stu-id="2074e-121">The counter values and sums may not match precisely due to the dynamic nature of the counters and the sampling accuracy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2074e-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2074e-122">See Also</span></span>  
 <span data-ttu-id="2074e-123">[SQL Server Buffer Manager 对象](sql-server-buffer-manager-object.md) </span><span class="sxs-lookup"><span data-stu-id="2074e-123">[SQL Server, Buffer Manager Object](sql-server-buffer-manager-object.md) </span></span>  
 <span data-ttu-id="2074e-124">[“服务器内存”服务器配置选项](../../database-engine/configure-windows/server-memory-server-configuration-options.md) </span><span class="sxs-lookup"><span data-stu-id="2074e-124">[Server Memory Server Configuration Options](../../database-engine/configure-windows/server-memory-server-configuration-options.md) </span></span>  
 <span data-ttu-id="2074e-125">[监视资源使用情况（系统监视器）](monitor-resource-usage-system-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="2074e-125">[Monitor Resource Usage &#40;System Monitor&#41;](monitor-resource-usage-system-monitor.md) </span></span>  
 [<span data-ttu-id="2074e-126">sys.dm_os_performance_counters (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="2074e-126">sys.dm_os_performance_counters &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql)  
  
  
