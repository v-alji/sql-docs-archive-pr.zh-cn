---
title: 对内存中 OLTP 数据库的高可用性支持 | Microsoft Docs
ms.custom: ''
ms.date: 10/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 2113a916-3b1e-496c-8650-7f495e492510
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 092f2b8158bb35286a09103ea645b2aeb1374fc7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692409"
---
# <a name="high-availability-support-for-in-memory-oltp-databases"></a><span data-ttu-id="31dcb-102">对内存中 OLTP 数据库的高可用性支持</span><span class="sxs-lookup"><span data-stu-id="31dcb-102">High Availability Support for In-Memory OLTP databases</span></span>
  <span data-ttu-id="31dcb-103">包含内存优化表的数据库（无论是否使用本机编译的存储过程）完全支持用于 AlwaysOn 可用性组。</span><span class="sxs-lookup"><span data-stu-id="31dcb-103">Databases containing memory-optimized tables, with or without native compiled stored procedures, are fully supported with AlwaysOn Availability Groups.</span></span>  <span data-ttu-id="31dcb-104">对于包含 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 对象的数据库和不包含这些对象的数据库，在配置和支持上没有任何区别，</span><span class="sxs-lookup"><span data-stu-id="31dcb-104">There is no difference in the configuration and support for databases which contain [!INCLUDE[hek_2](../../includes/hek-2-md.md)] objects as compared to those without,</span></span>  
  
## <a name="alwayson-availability-groups-and-in-memory-oltp-databases"></a><span data-ttu-id="31dcb-105">AlwaysOn 可用性组和内存中 OLTP 数据库</span><span class="sxs-lookup"><span data-stu-id="31dcb-105">AlwaysOn Availability Groups and In-Memory OLTP Databases</span></span>  
 <span data-ttu-id="31dcb-106">通过使用 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 组件配置数据库来提供以下内容：</span><span class="sxs-lookup"><span data-stu-id="31dcb-106">Configuring databases with [!INCLUDE[hek_2](../../includes/hek-2-md.md)] components provides the following:</span></span>  
  
-   <span data-ttu-id="31dcb-107">**完全集成的体验** </span><span class="sxs-lookup"><span data-stu-id="31dcb-107">**A fully integrated experience** </span></span>  
    <span data-ttu-id="31dcb-108">你可以使用相同的向导配置包含内存优化表的数据库，该向导具有对同步和异步次要副本的相同级别的支持。</span><span class="sxs-lookup"><span data-stu-id="31dcb-108">You can configure your databases containing memory-optimized tables using the same wizard with the same level of support for both synchronous and asynchronous secondary replicas.</span></span> <span data-ttu-id="31dcb-109">此外，在 SQL Server Management Studio 中使用熟悉的 AlwaysOn 仪表板提供运行状况监视。</span><span class="sxs-lookup"><span data-stu-id="31dcb-109">Additionally, health monitoring is provided using the familiar AlwaysOn dashboard in SQL Server Management Studio.</span></span>  
  
-   <span data-ttu-id="31dcb-110">**可比较的故障转移时间** </span><span class="sxs-lookup"><span data-stu-id="31dcb-110">**Comparable Failover time** </span></span>  
    <span data-ttu-id="31dcb-111">次要副本维持持久内存优化表的内存中状态。</span><span class="sxs-lookup"><span data-stu-id="31dcb-111">Secondary replicas maintain the in-memory state of the durable memory-optimized tables.</span></span> <span data-ttu-id="31dcb-112">在发生自动或强制故障转移时，由于不需要恢复，因此故障转移到新的主副本的时间相当于故障转移到基于磁盘的表的时间。</span><span class="sxs-lookup"><span data-stu-id="31dcb-112">In the event of automatic or forced failover, the time to failover to the new primary is comparable to disk-bases tables as no recovery is needed.</span></span> <span data-ttu-id="31dcb-113">创建为 SCHEMA_ONLY 的内存优化表在此配置中受支持。</span><span class="sxs-lookup"><span data-stu-id="31dcb-113">Memory-optimized tables created as SCHEMA_ONLY are supported in this configuration.</span></span> <span data-ttu-id="31dcb-114">但是，由于未对这些表的更改进行日志记录，因此辅助副本上的这些表中不会存在任何数据。</span><span class="sxs-lookup"><span data-stu-id="31dcb-114">However changes to these tables are not logged and therefore no data will exist in these tables on the secondary replica.</span></span>  
  
-   <span data-ttu-id="31dcb-115">**可读取辅助角色** </span><span class="sxs-lookup"><span data-stu-id="31dcb-115">**Readable Secondary** </span></span>  
    <span data-ttu-id="31dcb-116">你可以访问和查询次要副本上的内存优化表（如果已针对读取访问进行配置）。</span><span class="sxs-lookup"><span data-stu-id="31dcb-116">You can access and query memory-optimized tables on the secondary replica if it has been configured for read access.</span></span> <span data-ttu-id="31dcb-117">有关详细信息，请参阅[活动次要副本：可读次要副本（AlwaysOn 可用性组）](../../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="31dcb-117">For more information see [Active Secondaries: Readable Secondary Replicas (AlwaysOn Availability Groups)](../../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md).</span></span>  
  
## <a name="failover-clustering-instance-fci-and-in-memory-oltp-databases"></a><span data-ttu-id="31dcb-118">故障转移群集实例 (FCI) 和内存中 OLTP 数据库</span><span class="sxs-lookup"><span data-stu-id="31dcb-118">Failover Clustering Instance (FCI) and In-Memory OLTP Databases</span></span>  
 <span data-ttu-id="31dcb-119">若要在共享存储配置中实现高可用性，则可以在具有一个或多个带有内存优化表的数据库的实例上，设置故障转移群集。</span><span class="sxs-lookup"><span data-stu-id="31dcb-119">To achieve high-availability in a shared-storage configuration, you can setup failover clustering on instances with one or more database with memory-optimized tables.</span></span> <span data-ttu-id="31dcb-120">你需要在设置 FCI 时考虑以下因素。</span><span class="sxs-lookup"><span data-stu-id="31dcb-120">You need to consider the following factors as part of setting up an FCI.</span></span>  
  
-   <span data-ttu-id="31dcb-121">**恢复时间目标** </span><span class="sxs-lookup"><span data-stu-id="31dcb-121">**Recovery Time Objective** </span></span>  
    <span data-ttu-id="31dcb-122">故障转移时间可能会更长，因为内存优化表必须在数据库变为可用之前加载到内存中。</span><span class="sxs-lookup"><span data-stu-id="31dcb-122">Failover time will likely to be higher as the memory-optimized tables must be loaded into memory before the database is made available.</span></span>  
  
-   <span data-ttu-id="31dcb-123">**SCHEMA_ONLY 表** </span><span class="sxs-lookup"><span data-stu-id="31dcb-123">**SCHEMA_ONLY tables** </span></span>  
    <span data-ttu-id="31dcb-124">请注意，SCHEMA_ONLY 表将在故障转移后为空，并且没有行。</span><span class="sxs-lookup"><span data-stu-id="31dcb-124">Be aware that SCHEMA_ONLY tables will be empty with no rows after the failover.</span></span> <span data-ttu-id="31dcb-125">这是由应用程序设计和定义的。</span><span class="sxs-lookup"><span data-stu-id="31dcb-125">This is as designed and defined by the application.</span></span> <span data-ttu-id="31dcb-126">这与你重启带有一个或多个 SCHEMA_ONLY 表的 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 数据库时的行为完全相同。</span><span class="sxs-lookup"><span data-stu-id="31dcb-126">This is exactly the same behavior when you restart an [!INCLUDE[hek_2](../../includes/hek-2-md.md)] database with one or more SCHEMA_ONLY tables.</span></span>  
  
## <a name="support-for-transaction-replication-in-in-memory-oltp"></a><span data-ttu-id="31dcb-127">对内存中 OLTP 中的事务复制的支持</span><span class="sxs-lookup"><span data-stu-id="31dcb-127">Support for transaction replication in In-Memory OLTP</span></span>  
 <span data-ttu-id="31dcb-128">充当事务复制订阅服务器的表（不包括对等事务复制）可以配置为内存优化表。</span><span class="sxs-lookup"><span data-stu-id="31dcb-128">Tables acting as transactional replication subscribers, excluding Peer-to-peer transactional replication, can be configured as memory-optimized tables.</span></span> <span data-ttu-id="31dcb-129">其他复制配置与内存优化表不兼容。</span><span class="sxs-lookup"><span data-stu-id="31dcb-129">Other replication configurations are not compatible with memory-optimized tables.</span></span>  <span data-ttu-id="31dcb-130">有关详细信息，请参阅 [复制到内存优化表订阅服务器](../replication/replication-to-memory-optimized-table-subscribers.md)。</span><span class="sxs-lookup"><span data-stu-id="31dcb-130">For more information see [Replication to Memory-Optimized Table Subscribers](../replication/replication-to-memory-optimized-table-subscribers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31dcb-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="31dcb-131">See Also</span></span>  
 <span data-ttu-id="31dcb-132">[AlwaysOn 可用性组 (SQL Server) ](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="31dcb-132">[AlwaysOn Availability Groups (SQL Server)](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="31dcb-133">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="31dcb-133">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="31dcb-134">[活动辅助副本：可读辅助副本 &#40;AlwaysOn 可用性组&#41;](../../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="31dcb-134">[Active Secondaries: Readable Secondary Replicas &#40;AlwaysOn Availability Groups&#41;](../../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) </span></span>  
 [<span data-ttu-id="31dcb-135">复制到内存优化表订阅服务器</span><span class="sxs-lookup"><span data-stu-id="31dcb-135">Replication to Memory-Optimized Table Subscribers</span></span>](../replication/replication-to-memory-optimized-table-subscribers.md)  
  
  
