---
title: 高可用性解决方案 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- high availability [SQL Server], solutions
- Database Engine [SQL Server], availability
- database availability [SQL Server]
- availability [SQL Server]
- server availability [SQL Server]
ms.assetid: b2eda634-0f8e-4703-801b-7ba895544ff5
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 83e7dde423fadcc0cd7d4d34dd4fd05b460cf453
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586297"
---
# <a name="high-availability-solutions-sql-server"></a><span data-ttu-id="15254-102">高可用性解决方案 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="15254-102">High Availability Solutions (SQL Server)</span></span>
  <span data-ttu-id="15254-103">本主题介绍了几个提高服务器或数据库可用性的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 高可用性解决方案。</span><span class="sxs-lookup"><span data-stu-id="15254-103">This topic introduces several [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] high-availability solutions that improve the availability of servers or databases.</span></span> <span data-ttu-id="15254-104">高可用性解决方案可减少硬件或软件故障造成的影响，保持应用程序的可用性，从而将用户可以察觉到的停机时间减至最少。</span><span class="sxs-lookup"><span data-stu-id="15254-104">A high-availability solution masks the effects of a hardware or software failure and maintains the availability of applications so that the perceived downtime for users is minimized.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="15254-105">有关哪些版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支持给定的高可用性解决方案的信息，请参阅[SQL Server 2014 各个版本支持的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)中的“高可用性 (AlwaysOn)”部分。</span><span class="sxs-lookup"><span data-stu-id="15254-105">For information about which editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] support a given high availability solution, see the "High Availability (AlwaysOn)" section of [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
<span data-ttu-id="15254-106"> ( # RecommendedSolutions) </span><span class="sxs-lookup"><span data-stu-id="15254-106">(#RecommendedSolutions)</span></span>  
  
##  <a name="overview-of-sql-server-high-availability-solutions"></a><a name="TermsAndDefinitions"></a> <span data-ttu-id="15254-107">SQL Server 高可用性解决方案概述</span><span class="sxs-lookup"><span data-stu-id="15254-107">Overview of SQL Server High-Availability Solutions</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="15254-108">提供了几个为服务器或数据库打造高可用性的可选方案。</span><span class="sxs-lookup"><span data-stu-id="15254-108">provides several options for creating high availability for a server or database.</span></span> <span data-ttu-id="15254-109">高可用性可选方案包括：</span><span class="sxs-lookup"><span data-stu-id="15254-109">The high-availability options include the following:</span></span>  
  
 <span data-ttu-id="15254-110">AlwaysOn 故障转移群集实例</span><span class="sxs-lookup"><span data-stu-id="15254-110">AlwaysOn Failover Cluster Instances</span></span>  
 <span data-ttu-id="15254-111">作为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alwayson 产品/服务的一部分，Alwayson 故障转移群集实例利用 Windows Server 故障转移群集 (WSFC) 功能通过冗余在服务器实例级别（*故障转移群集实例* (FCI) 来提供本地高可用性。</span><span class="sxs-lookup"><span data-stu-id="15254-111">As part of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] AlwaysOn offering, AlwaysOn Failover Cluster Instances leverages Windows Server Failover Clustering (WSFC) functionality to provide local high availability through redundancy at the server-instance level-a *failover cluster instance* (FCI).</span></span> <span data-ttu-id="15254-112">FCI 是在 Windows Server 故障转移群集 (WSFC) 节点上和（可能）多个子网中安装的单个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="15254-112">An FCI is a single instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is installed across Windows Server Failover Clustering (WSFC) nodes and, possibly, across multiple subnets.</span></span> <span data-ttu-id="15254-113">在网络中，FCI 显示为在单台计算机上运行的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例，不过它提供了从一个 WSFC 节点到另一个 WSFC 节点的故障转移（如果当前节点不可用）。</span><span class="sxs-lookup"><span data-stu-id="15254-113">On the network, an FCI appears to be an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running on a single computer, but the FCI provides failover from one WSFC node to another if the current node becomes unavailable.</span></span>  
  
 <span data-ttu-id="15254-114">有关详细信息，请参阅 [AlwaysOn 故障转移群集实例 (SQL Server)](windows/always-on-failover-cluster-instances-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="15254-114">For more information, see [AlwaysOn Failover Cluster Instances (SQL Server)](windows/always-on-failover-cluster-instances-sql-server.md).</span></span>  
  
 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]  
 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] <span data-ttu-id="15254-115">是 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 中引入的企业级高可用性和灾难恢复解决方案，可使一个或多个用户数据库的可用性达到最高。</span><span class="sxs-lookup"><span data-stu-id="15254-115">is an enterprise-level high-availability and disaster recovery solution introduced in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] to enable you to maximize availability for one or more user databases.</span></span> [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] <span data-ttu-id="15254-116">要求 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例驻留在 Windows Server 故障转移群集 (WSFC) 节点上。</span><span class="sxs-lookup"><span data-stu-id="15254-116">requires that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances reside on Windows Server Failover Clustering (WSFC) nodes.</span></span> <span data-ttu-id="15254-117">有关详细信息，请参阅[AlwaysOn 可用性组 (SQL Server) ](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="15254-117">For more information, see [AlwaysOn Availability Groups (SQL Server)](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="15254-118">FCI 可利用 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] 提供数据库级别的远程灾难恢复。</span><span class="sxs-lookup"><span data-stu-id="15254-118">An FCI can leverage [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] to provide remote disaster recovery at the database level.</span></span> <span data-ttu-id="15254-119">有关详细信息，请参阅[故障转移群集和 AlwaysOn 可用性组 (SQL Server)](../../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="15254-119">For more information, see [Failover Clustering and AlwaysOn Availability Groups &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md).</span></span>  
  
 <span data-ttu-id="15254-120">数据库镜像</span><span class="sxs-lookup"><span data-stu-id="15254-120">Database mirroring</span></span>  
 > [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] <span data-ttu-id="15254-121">建议改用 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="15254-121">We recommend that you use [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] instead.</span></span>  
  
 <span data-ttu-id="15254-122">数据库镜像是一种解决方案，可提供几乎是瞬时的故障转移，以提高数据库的可用性。</span><span class="sxs-lookup"><span data-stu-id="15254-122">Database mirroring is a solution to increase database availability by supporting almost instantaneous failover.</span></span> <span data-ttu-id="15254-123">数据库镜像可以用来维护相应生产数据库（称为“主体数据库 \*\*”）的单个备用数据库（或“镜像数据库 \*\*”）。</span><span class="sxs-lookup"><span data-stu-id="15254-123">Database mirroring can be used to maintain a single standby database, or *mirror database*, for a corresponding production database that is referred to as the *principal database*.</span></span> <span data-ttu-id="15254-124">有关详细信息，请参阅[数据库镜像 (SQL Server)](../../database-engine/database-mirroring/database-mirroring-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="15254-124">For more information, see [Database Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md).</span></span>  
  
 <span data-ttu-id="15254-125">日志传送</span><span class="sxs-lookup"><span data-stu-id="15254-125">Log shipping</span></span>  
 <span data-ttu-id="15254-126">与 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] 和数据库镜像一样，日志传送是数据库级操作。</span><span class="sxs-lookup"><span data-stu-id="15254-126">Like [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] and database mirroring, log shipping operates at the database level.</span></span> <span data-ttu-id="15254-127">可以使用日志传送来维护单个生产数据库（称为*主数据库*）的一个或多个温备用数据库（称为*辅助数据库*）。</span><span class="sxs-lookup"><span data-stu-id="15254-127">You can use log shipping to maintain one or more warm standby databases (referred to as *secondary databases*) for a single production database that is referred to as the *primary database*.</span></span> <span data-ttu-id="15254-128">有关日志传送的详细信息，请参阅[关于日志传送 (SQL Server)](../../database-engine/log-shipping/about-log-shipping-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="15254-128">For more information about log shipping, see [About Log Shipping &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md).</span></span>  
  
##  <a name="recommended-solutions-for-using-sql-server-to-protect-data"></a><a name="RecommendedSolutions"></a> <span data-ttu-id="15254-129">有关使用 SQL Server 保护数据的建议的解决方案</span><span class="sxs-lookup"><span data-stu-id="15254-129">Recommended Solutions for Using SQL Server to Protect Data</span></span>  
 <span data-ttu-id="15254-130">以下是有关为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 环境提供数据保护的建议：</span><span class="sxs-lookup"><span data-stu-id="15254-130">Our recommendation for providing data protection for your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] environment are as follows:</span></span>  
  
-   <span data-ttu-id="15254-131">对于通过第三方共享磁盘解决方案 (SAN) 进行的数据保护，建议您使用 AlwaysOn 故障转移群集实例。</span><span class="sxs-lookup"><span data-stu-id="15254-131">For data protection through a third-party shared disk solution (a SAN), we recommend that you use AlwaysOn Failover Cluster Instances.</span></span>  
  
-   <span data-ttu-id="15254-132">对于通过 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]进行的数据保护，建议您使用 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="15254-132">For data protection through [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], we recommend that you use [!INCLUDE[ssHADR](../../includes/sshadr-md.md)].</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="15254-133">如果您运行的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本不支持 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]，建议您使用日志传送。</span><span class="sxs-lookup"><span data-stu-id="15254-133">If you are running an edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that does not support [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], we recommend log shipping.</span></span> <span data-ttu-id="15254-134">有关哪些版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支持 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] 的信息，请参阅 [SQL Server 2014 各个版本支持的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)中的“高可用性 (AlwaysOn)”部分。</span><span class="sxs-lookup"><span data-stu-id="15254-134">For information about which editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] support [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], see the "High Availability (AlwaysOn)" section of [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15254-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="15254-135">See Also</span></span>  
 <span data-ttu-id="15254-136">[Windows Server 故障转移群集 (WSFC) 与 SQL Server](windows/windows-server-failover-clustering-wsfc-with-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="15254-136">[Windows Server Failover Clustering &#40;WSFC&#41; with SQL Server](windows/windows-server-failover-clustering-wsfc-with-sql-server.md) </span></span>  
 <span data-ttu-id="15254-137">[数据库镜像：互操作性和共存 &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-interoperability-and-coexistence-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="15254-137">[Database Mirroring: Interoperability and Coexistence &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-interoperability-and-coexistence-sql-server.md) </span></span>  
 [<span data-ttu-id="15254-138">SQL Server 2014 中不推荐使用的数据库引擎功能</span><span class="sxs-lookup"><span data-stu-id="15254-138">Deprecated Database Engine Features in SQL Server 2014</span></span>](../../database-engine/deprecated-database-engine-features-in-sql-server-2016.md)  
  
  
