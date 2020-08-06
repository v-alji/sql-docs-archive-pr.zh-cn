---
title: Always On 可用性组的服务器实例的配置 (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], server instance
- Availability Groups [SQL Server], about
ms.assetid: fad8db32-593e-49d5-989c-39eb8399c416
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3392e6189b687516e627d847acceedb165141117
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693495"
---
# <a name="configuration-of-a-server-instance-for-always-on-availability-groups-sql-server"></a><span data-ttu-id="92290-102">为 AlwaysOn 可用性组配置服务器实例 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="92290-102">Configuration of a Server Instance for Always On Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="92290-103">本主题包含的信息涉及配置 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例以在 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 中提供支持 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]的要求。</span><span class="sxs-lookup"><span data-stu-id="92290-103">This topic contains information about the requirements for configuring an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to support [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="92290-104">有关针对 Windows Server 故障转移群集 (WSFC) 节点的 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 先决条件和限制以及 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的实例的基本信息，请参阅[针对 AlwaysOn 可用性组的先决条件、限制和建议 (SQL Server)](prereqs-restrictions-recommendations-always-on-availability.md)。</span><span class="sxs-lookup"><span data-stu-id="92290-104">For essential information about [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] prerequisites and restrictions for Windows Server Failover Clustering (WSFC) nodes and for instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], see [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
 
  
##  <a name="terms-and-definitions"></a><a name="TermsAndDefinitions"></a> <span data-ttu-id="92290-105">术语和定义</span><span class="sxs-lookup"><span data-stu-id="92290-105">Terms and Definitions</span></span>  
  
 <span data-ttu-id="92290-106">提供替代数据库镜像的企业级方案的高可用性和灾难恢复解决方案。</span><span class="sxs-lookup"><span data-stu-id="92290-106">A high-availability and disaster-recovery solution that provides an enterprise-level replacement for database mirroring.</span></span> <span data-ttu-id="92290-107">*可用性组*支持故障转移的一组离散的用户数据库（称为*可用性数据库*）的故障转移环境。</span><span class="sxs-lookup"><span data-stu-id="92290-107">An *availability group* supports a failover environment for a discrete set of user databases, known as *availability databases*, that fail over together.</span></span>  
  
 <span data-ttu-id="92290-108">可用性副本</span><span class="sxs-lookup"><span data-stu-id="92290-108">availability replica</span></span>  
 <span data-ttu-id="92290-109">可用性组的实例化，该可用性组由特定的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例承载，该实例维护属于该可用性组的每个可用性数据库的本地副本。</span><span class="sxs-lookup"><span data-stu-id="92290-109">An instantiation of an availability group that is hosted by a specific instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and that maintains a local copy of each availability database that belongs to the availability group.</span></span> <span data-ttu-id="92290-110">\*\* 存在两种类型的可用性副本：一个“主副本” \*\* 和一至四个“辅助副本”。</span><span class="sxs-lookup"><span data-stu-id="92290-110">Two types of availability replicas exist: a single *primary replica* and one to four *secondary replicas*.</span></span> <span data-ttu-id="92290-111">承载给定可用性组的可用性副本的服务器实例必须位于单个 Windows Server 故障转移群集 (WSFC) 群集的不同节点上。</span><span class="sxs-lookup"><span data-stu-id="92290-111">The server instances that host the availability replicas for a given availability group must reside on different nodes of a single Windows Server Failover Clustering (WSFC) cluster.</span></span>  
  
 [<span data-ttu-id="92290-112">数据库镜像端点</span><span class="sxs-lookup"><span data-stu-id="92290-112">database mirroring endpoint</span></span>](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md)  
 <span data-ttu-id="92290-113">端点就是一个 SQL Server 对象，它支持 SQL Server 在网络中通信。</span><span class="sxs-lookup"><span data-stu-id="92290-113">An endpoint is a SQL Server object that enables SQL Server to communicate over the network.</span></span> <span data-ttu-id="92290-114">若要参与数据库镜像和/或 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] ，服务器实例需要一个特殊的专用端点。</span><span class="sxs-lookup"><span data-stu-id="92290-114">To participate in database mirroring and/or [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] a server instance requires a special, dedicated endpoint.</span></span> <span data-ttu-id="92290-115">服务器实例上所有的镜像和可用性组连接都使用相同的数据库镜像端点。</span><span class="sxs-lookup"><span data-stu-id="92290-115">All mirroring and availability group connections on a server instance use the same database mirroring endpoint.</span></span> <span data-ttu-id="92290-116">此端点用途特殊，专门用于接收来自其他服务器实例的这些连接。</span><span class="sxs-lookup"><span data-stu-id="92290-116">This endpoint is a special-purpose endpoint used exclusively to receive these connections from other server instances.</span></span>  
  
##  <a name="to-configure-a-server-instance-to-support-alwayson-availability-groups"></a><a name="ConfigSI"></a><span data-ttu-id="92290-117">配置服务器实例以支持 AlwaysOn 可用性组</span><span class="sxs-lookup"><span data-stu-id="92290-117">To Configure a Server Instance to Support AlwaysOn Availability Groups</span></span>  
 <span data-ttu-id="92290-118">要支持 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]，服务器实例必须位于承载可用性组的 WSFC 故障转移群集的某个节点上，启用 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 并且占有一个数据库镜像端点。</span><span class="sxs-lookup"><span data-stu-id="92290-118">To support [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], a server instance must reside on a node in the WSFC failover cluster that hosts the availability group, be [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] enabled, and possess a database mirroring endpoint.</span></span>  
  
1.  <span data-ttu-id="92290-119">在要参与一个或多个可用性组的每个服务器实例上都启用 AlwaysOn 可用性组功能。</span><span class="sxs-lookup"><span data-stu-id="92290-119">Enable the AlwaysOn Availability Groups feature on every server instance that is to participate in one or more availability groups.</span></span> <span data-ttu-id="92290-120">一个给定服务器实例只能为一个给定可用性组承载单个可用性副本。</span><span class="sxs-lookup"><span data-stu-id="92290-120">A given server instance can host only a single availability replica for a given availability group.</span></span>  
  
2.  <span data-ttu-id="92290-121">确保服务器实例拥有数据库镜像端点。</span><span class="sxs-lookup"><span data-stu-id="92290-121">Ensure that the server instance possesses a database mirroring endpoint.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="92290-122">相关任务</span><span class="sxs-lookup"><span data-stu-id="92290-122">Related Tasks</span></span>  
 <span data-ttu-id="92290-123">**启用 AlwaysOn 可用性组**</span><span class="sxs-lookup"><span data-stu-id="92290-123">**To enable AlwaysOn Availability Groups**</span></span>  
  
-   [<span data-ttu-id="92290-124">启用和禁用 AlwaysOn 可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="92290-124">Enable and Disable AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](enable-and-disable-always-on-availability-groups-sql-server.md)  
  
 <span data-ttu-id="92290-125">**确定数据库镜像端点是否存在**</span><span class="sxs-lookup"><span data-stu-id="92290-125">**To determine whether a database mirroring endpoint exists**</span></span>  
  
-   [<span data-ttu-id="92290-126">sys.database_mirroring_endpoints (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="92290-126">sys.database_mirroring_endpoints &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)  
  
 <span data-ttu-id="92290-127">**创建数据库镜像端点**</span><span class="sxs-lookup"><span data-stu-id="92290-127">**To create a database mirroring endpoint**</span></span>  
  
-   [<span data-ttu-id="92290-128">为 AlwaysOn 可用性组 &#40;SQL Server PowerShell 创建数据库镜像端点&#41;</span><span class="sxs-lookup"><span data-stu-id="92290-128">Create a Database Mirroring Endpoint for AlwaysOn Availability Groups &#40;SQL Server PowerShell&#41;</span></span>](database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [<span data-ttu-id="92290-129">为 Windows 身份验证创建数据库镜像终结点 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="92290-129">Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [<span data-ttu-id="92290-130">允许数据库镜像终结点使用证书进行出站连接 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="92290-130">Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/database-mirroring-use-certificates-for-outbound-connections.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="92290-131">相关内容</span><span class="sxs-lookup"><span data-stu-id="92290-131">Related Content</span></span>  
  
-   <span data-ttu-id="92290-132">**博客：**</span><span class="sxs-lookup"><span data-stu-id="92290-132">**Blogs:**</span></span>  
  
     [<span data-ttu-id="92290-133">AlwaysON - HADRON 学习系列：启用了 HADRON 的数据库的工作线程池用法</span><span class="sxs-lookup"><span data-stu-id="92290-133">AlwaysON - HADRON Learning Series: Worker Pool Usage for HADRON Enabled Databases</span></span>](https://blogs.msdn.com/b/psssql/archive/2012/05/17/alwayson-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
     [<span data-ttu-id="92290-134">SQL Server AlwaysOn 团队博客：SQL Server AlwaysOn 官方团队博客</span><span class="sxs-lookup"><span data-stu-id="92290-134">SQL Server AlwaysOn Team Blogs: The official SQL Server AlwaysOn Team Blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [<span data-ttu-id="92290-135">CSS SQL Server 工程师博客</span><span class="sxs-lookup"><span data-stu-id="92290-135">CSS SQL Server Engineers Blogs</span></span>](https://blogs.msdn.com/b/psssql/)  
  
-   <span data-ttu-id="92290-136">**视频：**</span><span class="sxs-lookup"><span data-stu-id="92290-136">**Videos:**</span></span>  
  
     [<span data-ttu-id="92290-137">Microsoft SQL Server Code-Named "Denali" AlwaysOn 系列，第一部分：介绍下一代高可用性解决方案</span><span class="sxs-lookup"><span data-stu-id="92290-137">Microsoft SQL Server Code-Named "Denali" AlwaysOn Series,Part 1: Introducing the Next Generation High Availability Solution</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [<span data-ttu-id="92290-138">Microsoft SQL Server Code-Named "Denali" AlwaysOn 系列，第二部分：使用 AlwaysOn 生成关键任务高可用性解决方案</span><span class="sxs-lookup"><span data-stu-id="92290-138">Microsoft SQL Server Code-Named "Denali" AlwaysOn Series,Part 2: Building a Mission-Critical High Availability Solution Using AlwaysOn</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   <span data-ttu-id="92290-139">**白皮书：**</span><span class="sxs-lookup"><span data-stu-id="92290-139">**Whitepapers:**</span></span>  
  
     [<span data-ttu-id="92290-140">用于高可用性和灾难恢复的 Microsoft SQL Server AlwaysOn 解决方案指南</span><span class="sxs-lookup"><span data-stu-id="92290-140">Microsoft SQL Server AlwaysOn Solutions Guide for High Availability and Disaster Recovery</span></span>](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [<span data-ttu-id="92290-141">针对 SQL Server 2012 的 Microsoft 白皮书</span><span class="sxs-lookup"><span data-stu-id="92290-141">Microsoft White Papers for SQL Server 2012</span></span>](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [<span data-ttu-id="92290-142">SQL Server 客户咨询团队白皮书</span><span class="sxs-lookup"><span data-stu-id="92290-142">SQL Server Customer Advisory Team Whitepapers</span></span>](http://sqlcat.com/)  
  
## <a name="see-also"></a><span data-ttu-id="92290-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="92290-143">See Also</span></span>  
 <span data-ttu-id="92290-144">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="92290-144">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="92290-145">[AlwaysOn 可用性组 &#40;SQL Server 的先决条件、限制和建议&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="92290-145">[Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span></span>  
 <span data-ttu-id="92290-146">[数据库镜像终结点 (SQL Server)](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="92290-146">[The Database Mirroring Endpoint &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md) </span></span>  
 <span data-ttu-id="92290-147">[AlwaysOn 可用性组：互操作性 (SQL Server) ](always-on-availability-groups-interoperability-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="92290-147">[AlwaysOn Availability Groups: Interoperability (SQL Server)](always-on-availability-groups-interoperability-sql-server.md) </span></span>  
 <span data-ttu-id="92290-148">[故障转移群集和 AlwaysOn 可用性组 &#40;SQL Server&#41;](failover-clustering-and-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="92290-148">[Failover Clustering and AlwaysOn Availability Groups &#40;SQL Server&#41;](failover-clustering-and-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="92290-149">[Windows Server 故障转移群集 (WSFC) 与 SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="92290-149">[Windows Server Failover Clustering &#40;WSFC&#41; with SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md) </span></span>  
 [<span data-ttu-id="92290-150">AlwaysOn 故障转移群集实例</span><span class="sxs-lookup"><span data-stu-id="92290-150">AlwaysOn Failover Cluster Instances</span></span>](../../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md)  
  
