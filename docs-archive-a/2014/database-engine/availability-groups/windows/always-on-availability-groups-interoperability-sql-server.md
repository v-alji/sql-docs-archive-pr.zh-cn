---
title: AlwaysOn 可用性组：互操作性 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], about
- Availability Groups [SQL Server], interoperability
ms.assetid: daf87f90-2623-42ca-912c-b8f07d210510
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bbd9de348b2e36feefd7efea52dee0b8c13a9f34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578447"
---
# <a name="always-on-availability-groups-interoperability-sql-server"></a><span data-ttu-id="8f87f-102">AlwaysOn 可用性组：互操作性 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="8f87f-102">Always On Availability Groups: Interoperability (SQL Server)</span></span>
  <span data-ttu-id="8f87f-103">本主题说明 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 与 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中其他 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]功能的互操作性。</span><span class="sxs-lookup"><span data-stu-id="8f87f-103">This topic documents interoperability of [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] with other [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] features in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  

  
##  <a name="features-that-interoperate-with-alwayson-availability-groups"></a><a name="Interop"></a><span data-ttu-id="8f87f-104">与 AlwaysOn 可用性组互操作的功能</span><span class="sxs-lookup"><span data-stu-id="8f87f-104">Features That Interoperate with AlwaysOn Availability Groups</span></span>  
 <span data-ttu-id="8f87f-105">下表列出了在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中可与 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 互操作的 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]功能。</span><span class="sxs-lookup"><span data-stu-id="8f87f-105">The following table lists [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] features that interoperate with [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="8f87f-106">\*\*\*\* “详细信息”列中的链接表示给定功能的互操作性注意事项。</span><span class="sxs-lookup"><span data-stu-id="8f87f-106">A link in the **More Information** column indicates that interoperability considerations exist for a given feature.</span></span>  
  
|<span data-ttu-id="8f87f-107">功能</span><span class="sxs-lookup"><span data-stu-id="8f87f-107">Feature</span></span>|<span data-ttu-id="8f87f-108">更多信息</span><span class="sxs-lookup"><span data-stu-id="8f87f-108">More Information</span></span>|  
|-------------|----------------------|  
|<span data-ttu-id="8f87f-109">更改数据捕获</span><span class="sxs-lookup"><span data-stu-id="8f87f-109">Change data capture</span></span>|[<span data-ttu-id="8f87f-110">复制、更改跟踪、更改数据捕获和 AlwaysOn 可用性组 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8f87f-110">Replication, Change Tracking, Change Data Capture, and AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](replicate-track-change-data-capture-always-on-availability.md)|  
|<span data-ttu-id="8f87f-111">Change tracking</span><span class="sxs-lookup"><span data-stu-id="8f87f-111">Change tracking</span></span>|[<span data-ttu-id="8f87f-112">复制、更改跟踪、更改数据捕获和 AlwaysOn 可用性组 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8f87f-112">Replication, Change Tracking, Change Data Capture, and AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](replicate-track-change-data-capture-always-on-availability.md)|  
|<span data-ttu-id="8f87f-113">包含的数据库</span><span class="sxs-lookup"><span data-stu-id="8f87f-113">Contained databases</span></span>|[<span data-ttu-id="8f87f-114">包含的数据库与 AlwaysOn 可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="8f87f-114">Contained Databases with AlwaysOn Availability Groups (SQL Server)</span></span>](always-on-availability-groups-sql-server.md)|  
|<span data-ttu-id="8f87f-115">数据库加密</span><span class="sxs-lookup"><span data-stu-id="8f87f-115">Database encryption</span></span>|[<span data-ttu-id="8f87f-116">SQL Server AlwaysOn 可用性组 &#40;加密数据库&#41;</span><span class="sxs-lookup"><span data-stu-id="8f87f-116">Encrypted Databases with AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](encrypted-databases-with-always-on-availability-groups-sql-server.md)|  
|<span data-ttu-id="8f87f-117">数据库快照</span><span class="sxs-lookup"><span data-stu-id="8f87f-117">Database snapshots</span></span>|[<span data-ttu-id="8f87f-118">具有 AlwaysOn 可用性组 &#40;SQL Server 的数据库快照&#41;</span><span class="sxs-lookup"><span data-stu-id="8f87f-118">Database Snapshots with AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](database-snapshots-with-always-on-availability-groups-sql-server.md)|  
|<span data-ttu-id="8f87f-119">FILESTREAM 和 FileTable</span><span class="sxs-lookup"><span data-stu-id="8f87f-119">FILESTREAM and FileTable</span></span>|[<span data-ttu-id="8f87f-120">FILESTREAM 和 FileTable 与 AlwaysOn 可用性组 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8f87f-120">FILESTREAM and FileTable with AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](filestream-and-filetable-with-always-on-availability-groups-sql-server.md)|  
|<span data-ttu-id="8f87f-121">全文搜索</span><span class="sxs-lookup"><span data-stu-id="8f87f-121">Full-text search</span></span>|<span data-ttu-id="8f87f-122">注意：全文索引与 AlwaysOn 辅助数据库同步。</span><span class="sxs-lookup"><span data-stu-id="8f87f-122">Note: Full-Text indexes are synchronized with AlwaysOn secondary databases.</span></span>|  
|<span data-ttu-id="8f87f-123">日志传送</span><span class="sxs-lookup"><span data-stu-id="8f87f-123">Log shipping</span></span>|[<span data-ttu-id="8f87f-124">从日志传送迁移到 AlwaysOn 可用性组 &#40;SQL Server 的先决条件&#41;</span><span class="sxs-lookup"><span data-stu-id="8f87f-124">Prerequisites for Migrating from Log Shipping to AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](prereqs-migrating-log-shipping-to-always-on-availability-groups.md)|  
|<span data-ttu-id="8f87f-125">远程 Blob 存储区 (RBS)</span><span class="sxs-lookup"><span data-stu-id="8f87f-125">Remote Blob Store (RBS)</span></span>|[<span data-ttu-id="8f87f-126">远程 Blob 存储 &#40;RBS&#41;，AlwaysOn 可用性组 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8f87f-126">Remote Blob Store &#40;RBS&#41; and AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](remote-blob-store-rbs-and-always-on-availability-groups-sql-server.md)|  
|<span data-ttu-id="8f87f-127">复制[AlwaysOn 可用性组 (SQL Server 的复制配置) ](configure-replication-for-always-on-availability-groups-sql-server.md)</span><span class="sxs-lookup"><span data-stu-id="8f87f-127">Replication[Configure Replication for AlwaysOn Availability Groups (SQL Server)](configure-replication-for-always-on-availability-groups-sql-server.md)</span></span><br /><br /> [<span data-ttu-id="8f87f-128">维护 AlwaysOn 发布数据库 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8f87f-128">Maintaining an AlwaysOn Publication Database &#40;SQL Server&#41;</span></span>](maintaining-an-always-on-publication-database-sql-server.md)<br /><br /> [<span data-ttu-id="8f87f-129">复制、更改跟踪、更改数据捕获和 AlwaysOn 可用性组 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8f87f-129">Replication, Change Tracking, Change Data Capture, and AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](replicate-track-change-data-capture-always-on-availability.md)<br /><br /> [<span data-ttu-id="8f87f-130">复制订阅服务器和 AlwaysOn 可用性组 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8f87f-130">Replication Subscribers and AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](replication-subscribers-and-always-on-availability-groups-sql-server.md)|  
|<span data-ttu-id="8f87f-131">Analysis Services</span><span class="sxs-lookup"><span data-stu-id="8f87f-131">Analysis Services</span></span>|[<span data-ttu-id="8f87f-132">Analysis Services 与 AlwaysOn 可用性组</span><span class="sxs-lookup"><span data-stu-id="8f87f-132">Analysis Services with AlwaysOn Availability Groups</span></span>](analysis-services-with-always-on-availability-groups.md)|  
|<span data-ttu-id="8f87f-133">Reporting Services</span><span class="sxs-lookup"><span data-stu-id="8f87f-133">Reporting Services</span></span>|<span data-ttu-id="8f87f-134">使用只读辅助副本作为报告数据源，减少您的读写主副本上的负载。</span><span class="sxs-lookup"><span data-stu-id="8f87f-134">Utilize read only secondary replicas as a reporting data source and reduce the load on your primary read-write replica.</span></span><br /><br /> [<span data-ttu-id="8f87f-135">Reporting Services AlwaysOn 可用性组 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8f87f-135">Reporting Services with AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](reporting-services-with-always-on-availability-groups-sql-server.md)|  
|<span data-ttu-id="8f87f-136">Service Broker</span><span class="sxs-lookup"><span data-stu-id="8f87f-136">Service Broker</span></span>|[<span data-ttu-id="8f87f-137">Service Broker AlwaysOn 可用性组 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8f87f-137">Service Broker with AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](service-broker-with-always-on-availability-groups-sql-server.md)|  
|<span data-ttu-id="8f87f-138">SQL Server 代理</span><span class="sxs-lookup"><span data-stu-id="8f87f-138">SQL Server Agent</span></span>||  
  
##  <a name="features-that-do-not-interoperate-with-alwayson-availability-groups"></a><a name="NoInterop"></a><span data-ttu-id="8f87f-139">不能与 AlwaysOn 可用性组进行互操作的功能</span><span class="sxs-lookup"><span data-stu-id="8f87f-139">Features that Do Not Interoperate with AlwaysOn Availability Groups</span></span>  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] <span data-ttu-id="8f87f-140">不能与以下功能互操作：</span><span class="sxs-lookup"><span data-stu-id="8f87f-140">does not interoperate with the following features:</span></span>  
  
-   <span data-ttu-id="8f87f-141">跨数据库事务/分布式事务</span><span class="sxs-lookup"><span data-stu-id="8f87f-141">Cross-database transactions/distributed transactions</span></span>  
  
     <span data-ttu-id="8f87f-142">有关不支持此类事务原因的信息，请参阅[数据库镜像或 AlwaysOn 可用性组 (SQL Server) 不支持跨数据库事务](transactions-always-on-availability-and-database-mirroring.md)。</span><span class="sxs-lookup"><span data-stu-id="8f87f-142">For information about why such transactions are not supported, see [Cross-Database Transactions Not Supported For Database Mirroring or AlwaysOn Availability Groups &#40;SQL Server&#41;](transactions-always-on-availability-and-database-mirroring.md).</span></span>  
  
-   <span data-ttu-id="8f87f-143">数据库镜像</span><span class="sxs-lookup"><span data-stu-id="8f87f-143">Database mirroring</span></span>  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="8f87f-144">相关内容</span><span class="sxs-lookup"><span data-stu-id="8f87f-144">Related Content</span></span>  
  
-   <span data-ttu-id="8f87f-145">**博客：**</span><span class="sxs-lookup"><span data-stu-id="8f87f-145">**Blogs:**</span></span>  
  
     [<span data-ttu-id="8f87f-146">迁移指南：从之前群集和镜像部署迁移到 SQL Server 2012 故障转移群集和可用性组</span><span class="sxs-lookup"><span data-stu-id="8f87f-146">Migration Guide: Migrating to SQL Server 2012 Failover Clustering and Availability Groups from Prior Clustering and Mirroring Deployments</span></span>](https://blogs.msdn.com/b/sqlalwayson/archive/2012/04/09/now-available-migration-guide-migrating-to-sql-server-2012-failover-clustering-and-availability-groups-from-prior-clustering-and-mirroring-deployments.aspx)  
  
     [<span data-ttu-id="8f87f-147">SQL Server AlwaysOn 团队博客：SQL Server AlwaysOn 官方团队博客</span><span class="sxs-lookup"><span data-stu-id="8f87f-147">SQL Server AlwaysOn Team Blogs: The official SQL Server AlwaysOn Team Blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [<span data-ttu-id="8f87f-148">CSS SQL Server 工程师博客</span><span class="sxs-lookup"><span data-stu-id="8f87f-148">CSS SQL Server Engineers Blogs</span></span>](https://blogs.msdn.com/b/psssql/)  
  
-   <span data-ttu-id="8f87f-149">**白皮书：**</span><span class="sxs-lookup"><span data-stu-id="8f87f-149">**Whitepapers:**</span></span>  
  
     [<span data-ttu-id="8f87f-150">迁移指南：从之前组合数据库镜像和日志传送的部署迁移到 AlwaysOn 可用性组</span><span class="sxs-lookup"><span data-stu-id="8f87f-150">Migration Guide: Migrating to AlwaysOn Availability Groups from Prior Deployments Combining Database Mirroring and Log Shipping</span></span>](https://msdn.microsoft.com/library/jj635217)  
  
     [<span data-ttu-id="8f87f-151">用于高可用性和灾难恢复的 Microsoft SQL Server AlwaysOn 解决方案指南</span><span class="sxs-lookup"><span data-stu-id="8f87f-151">Microsoft SQL Server AlwaysOn Solutions Guide for High Availability and Disaster Recovery</span></span>](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [<span data-ttu-id="8f87f-152">针对 SQL Server 2012 的 Microsoft 白皮书</span><span class="sxs-lookup"><span data-stu-id="8f87f-152">Microsoft White Papers for SQL Server 2012</span></span>](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [<span data-ttu-id="8f87f-153">SQL Server 客户咨询团队白皮书</span><span class="sxs-lookup"><span data-stu-id="8f87f-153">SQL Server Customer Advisory Team Whitepapers</span></span>](http://sqlcat.com/)  
  
## <a name="see-also"></a><span data-ttu-id="8f87f-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8f87f-154">See Also</span></span>  
 <span data-ttu-id="8f87f-155">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8f87f-155">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="8f87f-156">AlwaysOn 可用性组 &#40;SQL Server 的先决条件、限制和建议&#41;</span><span class="sxs-lookup"><span data-stu-id="8f87f-156">Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](prereqs-restrictions-recommendations-always-on-availability.md)  
  
  
