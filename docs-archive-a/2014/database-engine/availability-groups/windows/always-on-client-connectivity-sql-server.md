---
title: AlwaysOn 客户端连接 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], listeners
- Availability Groups [SQL Server], prerequisites and restrictions
- Availability Groups [SQL Server], client connectivity
ms.assetid: b456448d-1757-48c8-8bbb-2d1c2d6d61e9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 360e448e87b16b6fb97384bb9a85525a864eeef5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585987"
---
# <a name="always-on-client-connectivity-sql-server"></a><span data-ttu-id="d2904-102">AlwaysOn 客户端连接 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="d2904-102">Always On Client Connectivity (SQL Server)</span></span>
  <span data-ttu-id="d2904-103">本主题介绍与 AlwaysOn 可用性组进行客户端连接时的注意事项，包括针对客户端配置和设置的先决条件、限制和建议。</span><span class="sxs-lookup"><span data-stu-id="d2904-103">This topic describes considerations for client connectivity to AlwaysOn Availability Groups, including prerequisites, restrictions, and recommendations for client configurations and settings.</span></span>  
  
 
  
##  <a name="client-connectivity-support"></a><a name="ClientConnSupport"></a> <span data-ttu-id="d2904-104">客户端连接支持</span><span class="sxs-lookup"><span data-stu-id="d2904-104">Client Connectivity Support</span></span>  
 <span data-ttu-id="d2904-105">以下部分提供有关对客户端连接的 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 支持的信息。</span><span class="sxs-lookup"><span data-stu-id="d2904-105">The section below provides information about [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] support for client connectivity.</span></span>  
  
 <span data-ttu-id="d2904-106">**驱动程序支持**</span><span class="sxs-lookup"><span data-stu-id="d2904-106">**Driver Support**</span></span>  
  
 <span data-ttu-id="d2904-107">下表概述了 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]的驱动程序支持：</span><span class="sxs-lookup"><span data-stu-id="d2904-107">The following table summarizes driver support for [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]:</span></span>  
  
|<span data-ttu-id="d2904-108">驱动程序</span><span class="sxs-lookup"><span data-stu-id="d2904-108">Driver</span></span>|<span data-ttu-id="d2904-109">多子网故障转移</span><span class="sxs-lookup"><span data-stu-id="d2904-109">Multi-Subnet Failover</span></span>|<span data-ttu-id="d2904-110">应用程序意向</span><span class="sxs-lookup"><span data-stu-id="d2904-110">Application Intent</span></span>|<span data-ttu-id="d2904-111">只读路由</span><span class="sxs-lookup"><span data-stu-id="d2904-111">Read-Only Routing</span></span>|<span data-ttu-id="d2904-112">多子网故障转移：更快的单子网端点故障转移</span><span class="sxs-lookup"><span data-stu-id="d2904-112">Multi-Subnet Failover: Faster Single Subnet Endpoint Failover</span></span>|<span data-ttu-id="d2904-113">多子网故障转移：SQL 群集实例的命名实例解析</span><span class="sxs-lookup"><span data-stu-id="d2904-113">Multi-Subnet Failover: Named Instance Resolution For SQL Clustered Instances</span></span>|  
|------------|----------------------------|------------------------|------------------------|--------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|<span data-ttu-id="d2904-114">SQL Native Client 11.0 ODBC</span><span class="sxs-lookup"><span data-stu-id="d2904-114">SQL Native Client 11.0 ODBC</span></span>|<span data-ttu-id="d2904-115">是</span><span class="sxs-lookup"><span data-stu-id="d2904-115">Yes</span></span>|<span data-ttu-id="d2904-116">是</span><span class="sxs-lookup"><span data-stu-id="d2904-116">Yes</span></span>|<span data-ttu-id="d2904-117">是</span><span class="sxs-lookup"><span data-stu-id="d2904-117">Yes</span></span>|<span data-ttu-id="d2904-118">是</span><span class="sxs-lookup"><span data-stu-id="d2904-118">Yes</span></span>|<span data-ttu-id="d2904-119">是</span><span class="sxs-lookup"><span data-stu-id="d2904-119">Yes</span></span>|  
|<span data-ttu-id="d2904-120">SQL Native Client 11.0 OLEDB</span><span class="sxs-lookup"><span data-stu-id="d2904-120">SQL Native Client 11.0 OLEDB</span></span>|<span data-ttu-id="d2904-121">否</span><span class="sxs-lookup"><span data-stu-id="d2904-121">No</span></span>|<span data-ttu-id="d2904-122">是</span><span class="sxs-lookup"><span data-stu-id="d2904-122">Yes</span></span>|<span data-ttu-id="d2904-123">是</span><span class="sxs-lookup"><span data-stu-id="d2904-123">Yes</span></span>|<span data-ttu-id="d2904-124">否</span><span class="sxs-lookup"><span data-stu-id="d2904-124">No</span></span>|<span data-ttu-id="d2904-125">否</span><span class="sxs-lookup"><span data-stu-id="d2904-125">No</span></span>|  
|<span data-ttu-id="d2904-126">带有连接修补程序 .NET Framework 4.0 的 ADO.NET**<sup>\*</sup>**</span><span class="sxs-lookup"><span data-stu-id="d2904-126">ADO.NET with .NET Framework 4.0 with connectivity patch**<sup>\*</sup>**</span></span> |<span data-ttu-id="d2904-127">是</span><span class="sxs-lookup"><span data-stu-id="d2904-127">Yes</span></span>|<span data-ttu-id="d2904-128">是</span><span class="sxs-lookup"><span data-stu-id="d2904-128">Yes</span></span>|<span data-ttu-id="d2904-129">是</span><span class="sxs-lookup"><span data-stu-id="d2904-129">Yes</span></span>|<span data-ttu-id="d2904-130">是</span><span class="sxs-lookup"><span data-stu-id="d2904-130">Yes</span></span>|<span data-ttu-id="d2904-131">是</span><span class="sxs-lookup"><span data-stu-id="d2904-131">Yes</span></span>|  
|<span data-ttu-id="d2904-132">带有连接修补程序 .NET Framework 3.5 SP1 的 ADO.NET**<sup>**</sup>\*\*</span><span class="sxs-lookup"><span data-stu-id="d2904-132">ADO.NET with .NET Framework 3.5 SP1 with connectivity patch **<sup>**</sup>\*\*</span></span> |<span data-ttu-id="d2904-133">是</span><span class="sxs-lookup"><span data-stu-id="d2904-133">Yes</span></span>|<span data-ttu-id="d2904-134">是</span><span class="sxs-lookup"><span data-stu-id="d2904-134">Yes</span></span>|<span data-ttu-id="d2904-135">是</span><span class="sxs-lookup"><span data-stu-id="d2904-135">Yes</span></span>|<span data-ttu-id="d2904-136">是</span><span class="sxs-lookup"><span data-stu-id="d2904-136">Yes</span></span>|<span data-ttu-id="d2904-137">是</span><span class="sxs-lookup"><span data-stu-id="d2904-137">Yes</span></span>|  
|<span data-ttu-id="d2904-138">Microsoft JDBC driver 4.0 for SQL Server</span><span class="sxs-lookup"><span data-stu-id="d2904-138">Microsoft JDBC driver 4.0 for SQL Server</span></span>|<span data-ttu-id="d2904-139">是</span><span class="sxs-lookup"><span data-stu-id="d2904-139">Yes</span></span>|<span data-ttu-id="d2904-140">是</span><span class="sxs-lookup"><span data-stu-id="d2904-140">Yes</span></span>|<span data-ttu-id="d2904-141">是</span><span class="sxs-lookup"><span data-stu-id="d2904-141">Yes</span></span>|<span data-ttu-id="d2904-142">是</span><span class="sxs-lookup"><span data-stu-id="d2904-142">Yes</span></span>|<span data-ttu-id="d2904-143">是</span><span class="sxs-lookup"><span data-stu-id="d2904-143">Yes</span></span>|  
  
 <span data-ttu-id="d2904-144">**<sup>\*</sup>** 下载 .NET Framework 4.0 的 ADO .NET 连接修补程序： [https://support.microsoft.com/kb/2600211](https://support.microsoft.com/kb/2600211) 。</span><span class="sxs-lookup"><span data-stu-id="d2904-144">**<sup>\*</sup>**  Download the connectivity patch for ADO .NET with .NET Framework 4.0: [https://support.microsoft.com/kb/2600211](https://support.microsoft.com/kb/2600211).</span></span>  
  
 <span data-ttu-id="d2904-145">**<sup>**</sup>\* \* 下载 .NET Framework 3.5 SP1 的 ADO.NET 的连接修补程序： [https://support.microsoft.com/kb/2654347](https://support.microsoft.com/kb/2654347) 。</span><span class="sxs-lookup"><span data-stu-id="d2904-145">**<sup>**</sup>\*\*  Download the connectivity patch for ADO.NET with .NET Framework 3.5 SP1: [https://support.microsoft.com/kb/2654347](https://support.microsoft.com/kb/2654347).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d2904-146">要连接到一个可用性组侦听器，客户端必须使用 TCP 连接字符串。</span><span class="sxs-lookup"><span data-stu-id="d2904-146">To connect to an availability group listener, a client must use a TCP connection string.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="d2904-147">相关任务</span><span class="sxs-lookup"><span data-stu-id="d2904-147">Related Tasks</span></span>  
  
-   [<span data-ttu-id="d2904-148">创建和配置可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="d2904-148">Creation and Configuration of Availability Groups &#40;SQL Server&#41;</span></span>](creation-and-configuration-of-availability-groups-sql-server.md)  
  
-   [<span data-ttu-id="d2904-149">创建或配置可用性组侦听程序 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="d2904-149">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  

  
## <a name="see-also"></a><span data-ttu-id="d2904-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d2904-150">See Also</span></span>  
 <span data-ttu-id="d2904-151">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d2904-151">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="d2904-152">[故障转移群集和 AlwaysOn 可用性组 &#40;SQL Server&#41;](failover-clustering-and-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d2904-152">[Failover Clustering and AlwaysOn Availability Groups &#40;SQL Server&#41;](failover-clustering-and-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="d2904-153">[AlwaysOn 可用性组 &#40;SQL Server 的先决条件、限制和建议&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="d2904-153">[Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span></span>  
 <span data-ttu-id="d2904-154">[可用性组侦听程序、客户端连接和应用程序故障转移 &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span><span class="sxs-lookup"><span data-stu-id="d2904-154">[Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span></span>  
 <span data-ttu-id="d2904-155">[关于对可用性副本的客户端连接访问 &#40;SQL Server&#41;](about-client-connection-access-to-availability-replicas-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d2904-155">[About Client Connection Access to Availability Replicas &#40;SQL Server&#41;](about-client-connection-access-to-availability-replicas-sql-server.md) </span></span>  
 <span data-ttu-id="d2904-156">[Microsoft SQL Server AlwaysOn 解决方案指南以实现高可用性和灾难恢复](https://go.microsoft.com/fwlink/?LinkId=227600) </span><span class="sxs-lookup"><span data-stu-id="d2904-156">[Microsoft SQL Server AlwaysOn Solutions Guide for High Availability and Disaster Recovery](https://go.microsoft.com/fwlink/?LinkId=227600) </span></span>  
 <span data-ttu-id="d2904-157">[SQL Server AlwaysOn 团队博客：官方 SQL Server AlwaysOn 团队博客](https://blogs.msdn.com/b/sqlalwayson/) </span><span class="sxs-lookup"><span data-stu-id="d2904-157">[SQL Server AlwaysOn Team Blog: The official SQL Server AlwaysOn Team Blog](https://blogs.msdn.com/b/sqlalwayson/) </span></span>  
 <span data-ttu-id="d2904-158">[从运行 Windows Server 2003、Windows Vista、Windows Server 2008、Windows 7 或 Windows Server 2008 R2 的计算机重新建立 IPSec 连接时出现长时间延迟](https://support.microsoft.com/kb/980915) </span><span class="sxs-lookup"><span data-stu-id="d2904-158">[A long time delay occurs when you reconnect an IPSec connection from a computer that is running Windows Server 2003, Windows Vista, Windows Server 2008, Windows 7, or Windows Server 2008 R2](https://support.microsoft.com/kb/980915) </span></span>  
 <span data-ttu-id="d2904-159">[群集服务需要大约 30 秒对 Windows Server 2008 R2 中的 IPv6 IP 地址进行故障转移](https://support.microsoft.com/kb/2578113) </span><span class="sxs-lookup"><span data-stu-id="d2904-159">[The Cluster service takes about 30 seconds to fail over IPv6 IP addresses in Windows Server 2008 R2](https://support.microsoft.com/kb/2578113) </span></span>  
 [<span data-ttu-id="d2904-160">如果群集与应用程序服务器之间不存在路由器，则故障转移操作的速度会很慢</span><span class="sxs-lookup"><span data-stu-id="d2904-160">Slow failover operation if no router exists between the cluster and an application server</span></span>](https://support.microsoft.com/kb/2582281)  
  
  
