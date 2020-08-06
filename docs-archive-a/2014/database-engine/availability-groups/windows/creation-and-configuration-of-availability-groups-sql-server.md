---
title: 创建和配置可用性组 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], creating
ms.assetid: 7f89fab8-6ee2-4273-9de0-e594bfb9407f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bc33da393527c19985f5e7b214ba4bc02dc2f3af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694560"
---
# <a name="creation-and-configuration-of-availability-groups-sql-server"></a><span data-ttu-id="f4f7d-102">创建和配置可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f4f7d-102">Creation and Configuration of Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="f4f7d-103">本节中的主题介绍如何在 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 实例（这些实例驻留在单个 WSFC 故障转移群集内的不同 Windows Server 故障转移群集 (WSFC) 节点上）上部署 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 实现。</span><span class="sxs-lookup"><span data-stu-id="f4f7d-103">The topics in this section explain how to deploy a [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] implementation on instances of [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] that reside on different Windows Server Failover Clustering (WSFC) nodes within a single WSFC failover cluster.</span></span>  
  
 <span data-ttu-id="f4f7d-104">在创建您的第一个可用性组前，我们强烈建议您首先熟悉以下主题中的内容：</span><span class="sxs-lookup"><span data-stu-id="f4f7d-104">Before you create your first availability group, we strongly recommend that you familiarize yourself with the information in the following topics:</span></span>  
  
 [<span data-ttu-id="f4f7d-105">AlwaysOn 可用性组 &#40;SQL Server 的先决条件、限制和建议&#41;</span><span class="sxs-lookup"><span data-stu-id="f4f7d-105">Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](prereqs-restrictions-recommendations-always-on-availability.md)  
 <span data-ttu-id="f4f7d-106">此主题说明针对计算机、WSFC 节点、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]实例、可用性组、副本和数据库的先决条件、限制和建议。</span><span class="sxs-lookup"><span data-stu-id="f4f7d-106">This topic describes the prerequisites, restrictions, and recommendations for computers; WSFC nodes; instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]; availability groups, replicas, and databases.</span></span> <span data-ttu-id="f4f7d-107">此主题还包含有关安全注意事项的信息。</span><span class="sxs-lookup"><span data-stu-id="f4f7d-107">This topic also contains information about security considerations.</span></span>  
  
 [<span data-ttu-id="f4f7d-108">入门 AlwaysOn 可用性组 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f4f7d-108">Getting Started with AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](getting-started-with-always-on-availability-groups-sql-server.md)  
 <span data-ttu-id="f4f7d-109">包含以下相关步骤信息：配置服务器实例、创建可用性组、为客户端连接配置可用性组、管理可用性组和监视可用性组。</span><span class="sxs-lookup"><span data-stu-id="f4f7d-109">Contains information about the steps for configuring a server instance, creating an availability group, configuring the availability group for client connections, managing availability groups, and monitoring availability groups.</span></span>  
  
 
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="f4f7d-110">相关任务</span><span class="sxs-lookup"><span data-stu-id="f4f7d-110">Related Tasks</span></span>  
 <span data-ttu-id="f4f7d-111">**配置 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="f4f7d-111">**To configure a server instance for [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]**</span></span>  
  
-   [<span data-ttu-id="f4f7d-112">启用和禁用 AlwaysOn 可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f4f7d-112">Enable and Disable AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](enable-and-disable-always-on-availability-groups-sql-server.md)  
  
-   [<span data-ttu-id="f4f7d-113">为 AlwaysOn 可用性组 &#40;SQL Server PowerShell 创建数据库镜像端点&#41;</span><span class="sxs-lookup"><span data-stu-id="f4f7d-113">Create a Database Mirroring Endpoint for AlwaysOn Availability Groups &#40;SQL Server PowerShell&#41;</span></span>](database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [<span data-ttu-id="f4f7d-114">为 Windows 身份验证创建数据库镜像终结点 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f4f7d-114">Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [<span data-ttu-id="f4f7d-115">允许数据库镜像终结点使用证书进行出站连接 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f4f7d-115">Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/database-mirroring-use-certificates-for-outbound-connections.md)  
  
 <span data-ttu-id="f4f7d-116">**配置 AlwaysOn 可用性组入门**</span><span class="sxs-lookup"><span data-stu-id="f4f7d-116">**To get started with configuring AlwaysOn Availability Groups**</span></span>  
  
-   [<span data-ttu-id="f4f7d-117">入门 AlwaysOn 可用性组 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f4f7d-117">Getting Started with AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](getting-started-with-always-on-availability-groups-sql-server.md)  
  
 <span data-ttu-id="f4f7d-118">**创建和配置新的可用性组**</span><span class="sxs-lookup"><span data-stu-id="f4f7d-118">**To create and configure a new availability group**</span></span>  
  
-   [<span data-ttu-id="f4f7d-119">使用可用性组向导 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="f4f7d-119">Use the Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="f4f7d-120">创建可用性组 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f4f7d-120">Create an Availability Group &#40;Transact-SQL&#41;</span></span>](create-an-availability-group-transact-sql.md)  
  
-   [<span data-ttu-id="f4f7d-121">创建可用性组 (SQL Server PowerShell)</span><span class="sxs-lookup"><span data-stu-id="f4f7d-121">Create an Availability Group &#40;SQL Server PowerShell&#41;</span></span>](../../../powershell/sql-server-powershell.md)  
  
-   [<span data-ttu-id="f4f7d-122">使用“新建可用性组”对话框 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="f4f7d-122">Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;</span></span>](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="f4f7d-123">在添加或修改可用性副本时指定终结点 URL (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f4f7d-123">Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;</span></span>](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
-   [<span data-ttu-id="f4f7d-124">创建或配置可用性组侦听程序 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f4f7d-124">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="f4f7d-125">配置灵活的故障转移策略以控制自动故障转移的条件（AlwaysOn 可用性组）</span><span class="sxs-lookup"><span data-stu-id="f4f7d-125">Configure the Flexible Failover Policy to Control Conditions for Automatic Failover (AlwaysOn Availability Groups)</span></span>](configure-flexible-automatic-failover-policy.md)  
  
-   [<span data-ttu-id="f4f7d-126">配置可用性副本备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f4f7d-126">Configure Backup on Availability Replicas &#40;SQL Server&#41;</span></span>](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [<span data-ttu-id="f4f7d-127">配置对可用性副本的只读访问 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f4f7d-127">Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;</span></span>](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="f4f7d-128">为可用性组配置只读路由 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f4f7d-128">Configure Read-Only Routing for an Availability Group &#40;SQL Server&#41;</span></span>](configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="f4f7d-129">将辅助副本联接到可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f4f7d-129">Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="f4f7d-130">启动 AlwaysOn 辅助数据库的数据移动 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f4f7d-130">Start Data Movement on an AlwaysOn Secondary Database &#40;SQL Server&#41;</span></span>](start-data-movement-on-an-always-on-secondary-database-sql-server.md)  
  
-   [<span data-ttu-id="f4f7d-131">为可用性组手动准备辅助数据库 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f4f7d-131">Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;</span></span>](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="f4f7d-132">将辅助数据库联接到可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f4f7d-132">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="f4f7d-133">管理可用性组中数据库的登录名和作业 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f4f7d-133">Management of Logins and Jobs for the Databases of an Availability Group &#40;SQL Server&#41;</span></span>](../../logins-and-jobs-for-availability-group-databases.md)  
  
 <span data-ttu-id="f4f7d-134">**排查问题**</span><span class="sxs-lookup"><span data-stu-id="f4f7d-134">**To troubleshoot**</span></span>  
  
-   [<span data-ttu-id="f4f7d-135">) 删除 AlwaysOn 可用性组配置 (SQL Server 的疑难解答</span><span class="sxs-lookup"><span data-stu-id="f4f7d-135">Troubleshoot AlwaysOn Availability Groups Configuration (SQL Server)deleted</span></span>](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
-   [<span data-ttu-id="f4f7d-136">排除失败的添加文件操作 &#40;AlwaysOn 可用性组&#41;</span><span class="sxs-lookup"><span data-stu-id="f4f7d-136">Troubleshoot a Failed Add-File Operation &#40;AlwaysOn Availability Groups&#41;</span></span>](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="f4f7d-137">相关内容</span><span class="sxs-lookup"><span data-stu-id="f4f7d-137">Related Content</span></span>  
  
-   <span data-ttu-id="f4f7d-138">**博客：**</span><span class="sxs-lookup"><span data-stu-id="f4f7d-138">**Blogs:**</span></span>  
  
     [<span data-ttu-id="f4f7d-139">AlwaysON - HADRON 学习系列：启用了 HADRON 的数据库的工作线程池用法</span><span class="sxs-lookup"><span data-stu-id="f4f7d-139">AlwaysON - HADRON Learning Series: Worker Pool Usage for HADRON Enabled Databases</span></span>](https://blogs.msdn.com/b/psssql/archive/2012/05/17/alwayson-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
     [<span data-ttu-id="f4f7d-140">SQL Server AlwaysOn 团队博客：SQL Server AlwaysOn 官方团队博客</span><span class="sxs-lookup"><span data-stu-id="f4f7d-140">SQL Server AlwaysOn Team Blogs: The official SQL Server AlwaysOn Team Blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [<span data-ttu-id="f4f7d-141">CSS SQL Server 工程师博客</span><span class="sxs-lookup"><span data-stu-id="f4f7d-141">CSS SQL Server Engineers Blogs</span></span>](https://blogs.msdn.com/b/psssql/)  
  
-   <span data-ttu-id="f4f7d-142">**视频：**</span><span class="sxs-lookup"><span data-stu-id="f4f7d-142">**Videos:**</span></span>  
  
     [<span data-ttu-id="f4f7d-143">Microsoft SQL Server Code-Named "Denali" AlwaysOn 系列，第一部分：介绍下一代高可用性解决方案</span><span class="sxs-lookup"><span data-stu-id="f4f7d-143">Microsoft SQL Server Code-Named "Denali" AlwaysOn Series,Part 1: Introducing the Next Generation High Availability Solution</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [<span data-ttu-id="f4f7d-144">Microsoft SQL Server Code-Named "Denali" AlwaysOn 系列，第二部分：使用 AlwaysOn 生成关键任务高可用性解决方案</span><span class="sxs-lookup"><span data-stu-id="f4f7d-144">Microsoft SQL Server Code-Named "Denali" AlwaysOn Series,Part 2: Building a Mission-Critical High Availability Solution Using AlwaysOn</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   <span data-ttu-id="f4f7d-145">**白皮书：**</span><span class="sxs-lookup"><span data-stu-id="f4f7d-145">**Whitepapers:**</span></span>  
  
     [<span data-ttu-id="f4f7d-146">用于高可用性和灾难恢复的 Microsoft SQL Server AlwaysOn 解决方案指南</span><span class="sxs-lookup"><span data-stu-id="f4f7d-146">Microsoft SQL Server AlwaysOn Solutions Guide for High Availability and Disaster Recovery</span></span>](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [<span data-ttu-id="f4f7d-147">针对 SQL Server 2012 的 Microsoft 白皮书</span><span class="sxs-lookup"><span data-stu-id="f4f7d-147">Microsoft White Papers for SQL Server 2012</span></span>](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [<span data-ttu-id="f4f7d-148">SQL Server 客户咨询团队白皮书</span><span class="sxs-lookup"><span data-stu-id="f4f7d-148">SQL Server Customer Advisory Team Whitepapers</span></span>](http://sqlcat.com/)  
  
## <a name="see-also"></a><span data-ttu-id="f4f7d-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f4f7d-149">See Also</span></span>  
 <span data-ttu-id="f4f7d-150">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f4f7d-150">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="f4f7d-151">[管理可用性组 &#40;SQL Server&#41;](administration-of-an-availability-group-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f4f7d-151">[Administration of an Availability Group &#40;SQL Server&#41;](administration-of-an-availability-group-sql-server.md) </span></span>  
 <span data-ttu-id="f4f7d-152">[AlwaysOn 可用性组 (SQL Server 的操作问题的 AlwaysOn 策略) ](always-on-policies-for-operational-issues-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="f4f7d-152">[AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md) </span></span>  
 <span data-ttu-id="f4f7d-153">[监视可用性组 (SQL Server)](monitoring-of-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f4f7d-153">[Monitoring of Availability Groups &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="f4f7d-154">AlwaysOn 可用性组：互操作性 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f4f7d-154">AlwaysOn Availability Groups: Interoperability (SQL Server)</span></span>](always-on-availability-groups-interoperability-sql-server.md)  
  
