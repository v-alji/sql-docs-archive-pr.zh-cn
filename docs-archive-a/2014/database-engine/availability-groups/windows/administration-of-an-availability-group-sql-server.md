---
title: 管理可用性组 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], managing
ms.assetid: 0b7542fa-235e-413d-81bf-3eff9ee07480
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d2cac9a34fe71c11f71ec47bbb6d690199869fef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578449"
---
# <a name="administration-of-an-availability-group-sql-server"></a><span data-ttu-id="883c4-102">管理可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="883c4-102">Administration of an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="883c4-103">在 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 中管理现有 AlwaysOn 可用性组涉及以下一个或多个任务：</span><span class="sxs-lookup"><span data-stu-id="883c4-103">Managing an existing AlwaysOn availability group in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] involves one or more of the following tasks:</span></span>  
  
-   <span data-ttu-id="883c4-104">更改现有可用性副本的属性以便更改客户端连接访问（用于配置可读的辅助副本）等，更改其故障转移模式、可用性模式或会话超时设置。</span><span class="sxs-lookup"><span data-stu-id="883c4-104">Altering the properties of an existing availability replica, for example to change client connection access (for configuring readable secondary replicas), changing its failover mode, availability mode, or session timeout setting.</span></span>  
  
-   <span data-ttu-id="883c4-105">添加或删除辅助副本。</span><span class="sxs-lookup"><span data-stu-id="883c4-105">Adding or removing secondary replicas.</span></span>  
  
-   <span data-ttu-id="883c4-106">添加或删除数据库。</span><span class="sxs-lookup"><span data-stu-id="883c4-106">Adding or removing a database.</span></span>  
  
-   <span data-ttu-id="883c4-107">暂停或恢复数据库。</span><span class="sxs-lookup"><span data-stu-id="883c4-107">Suspending or resuming a database.</span></span>  
  
-   <span data-ttu-id="883c4-108">执行计划的手动故障转移（手动故障转移**）或强制手动故障转移（强制故障转移**）。</span><span class="sxs-lookup"><span data-stu-id="883c4-108">Performing a planned manual failover (a *manual failover*) or a forced manual failover (a *forced failover*).</span></span>  
  
-   <span data-ttu-id="883c4-109">创建和配置可用性组侦听器。</span><span class="sxs-lookup"><span data-stu-id="883c4-109">Creating or configuring an availability group listener.</span></span>  
  
-   <span data-ttu-id="883c4-110">为某一给定可用性组管理 [可读次要副本](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) 。</span><span class="sxs-lookup"><span data-stu-id="883c4-110">Managing [readable secondary replicas](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) for a given availability group.</span></span> <span data-ttu-id="883c4-111">这涉及在以辅助角色运行时将一个或多个副本配置为只读访问以及配置只读路由。</span><span class="sxs-lookup"><span data-stu-id="883c4-111">This involves configuring one or more replicas to read-only access when running under the secondary role, and configuring read-only routing.</span></span>  
  
-   <span data-ttu-id="883c4-112">为某一给定可用性组管理 [次要副本上的备份](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md) 。</span><span class="sxs-lookup"><span data-stu-id="883c4-112">Managing [backups on secondary replicas](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md) for a given availability group.</span></span> <span data-ttu-id="883c4-113">这涉及配置您希望运行备份作业的位置，然后编写备份作业脚本，以便实现您的备份首选项。</span><span class="sxs-lookup"><span data-stu-id="883c4-113">This involves configuring where you prefer that backup jobs run and then scripting backup jobs to implement your backup preference.</span></span> <span data-ttu-id="883c4-114">在承载可用性副本的每个 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例上，对于可用性组中的每个数据库，您都需要为备份作业编写脚本。</span><span class="sxs-lookup"><span data-stu-id="883c4-114">you need to script backup jobs for every database in the availability group on every instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosts an availability replica.</span></span>  
  
-   <span data-ttu-id="883c4-115">删除可用性组。</span><span class="sxs-lookup"><span data-stu-id="883c4-115">Deleting an availability group.</span></span>  
  
-   <span data-ttu-id="883c4-116">针对操作系统升级的 AlwaysOn 可用性组的跨群集迁移</span><span class="sxs-lookup"><span data-stu-id="883c4-116">Cross-cluster migration of AlwaysOn Availability Groups for OS upgrade</span></span>  
  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="883c4-117">相关任务</span><span class="sxs-lookup"><span data-stu-id="883c4-117">Related Tasks</span></span>  
 <span data-ttu-id="883c4-118">**配置现有的可用性组**</span><span class="sxs-lookup"><span data-stu-id="883c4-118">**To configure an existing availability group**</span></span>  
  
-   [<span data-ttu-id="883c4-119">将辅助副本添加到可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="883c4-119">Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="883c4-120">将次要副本从可用性组删除 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="883c4-120">Remove a Secondary Replica from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-replica-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="883c4-121">将数据库添加到可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="883c4-121">Add a Database to an Availability Group &#40;SQL Server&#41;</span></span>](availability-group-add-a-database.md)  
  
-   [<span data-ttu-id="883c4-122">将辅助数据库从可用性组删除 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="883c4-122">Remove a Secondary Database from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-database-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="883c4-123">将主数据库从可用性组删除 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="883c4-123">Remove a Primary Database from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-primary-database-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="883c4-124">配置灵活的故障转移策略以控制自动故障转移的条件 &#40;AlwaysOn 可用性组&#41;</span><span class="sxs-lookup"><span data-stu-id="883c4-124">Configure the Flexible Failover Policy to Control Conditions for Automatic Failover &#40;AlwaysOn Availability Groups&#41;</span></span>](configure-flexible-automatic-failover-policy.md)  
  
 <span data-ttu-id="883c4-125">**管理可用性组**</span><span class="sxs-lookup"><span data-stu-id="883c4-125">**To manage an availability group**</span></span>  
  
-   [<span data-ttu-id="883c4-126">配置可用性副本备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="883c4-126">Configure Backup on Availability Replicas &#40;SQL Server&#41;</span></span>](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [<span data-ttu-id="883c4-127">执行可用性组的计划手动故障转移 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="883c4-127">Perform a Planned Manual Failover of an Availability Group &#40;SQL Server&#41;</span></span>](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="883c4-128">执行可用性组的强制手动故障转移 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="883c4-128">Perform a Forced Manual Failover of an Availability Group &#40;SQL Server&#41;</span></span>](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="883c4-129">删除可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="883c4-129">Remove an Availability Group &#40;SQL Server&#41;</span></span>](remove-an-availability-group-sql-server.md)  
  
 <span data-ttu-id="883c4-130">**管理可用性副本**</span><span class="sxs-lookup"><span data-stu-id="883c4-130">**To manage an availability replica**</span></span>  
  
-   [<span data-ttu-id="883c4-131">将辅助副本添加到可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="883c4-131">Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="883c4-132">将辅助副本联接到可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="883c4-132">Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="883c4-133">将次要副本从可用性组删除 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="883c4-133">Remove a Secondary Replica from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-replica-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="883c4-134">更改可用性副本的可用性模式 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="883c4-134">Change the Availability Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-availability-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="883c4-135">更改可用性副本的故障转移模式 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="883c4-135">Change the Failover Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-failover-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="883c4-136">配置可用性副本备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="883c4-136">Configure Backup on Availability Replicas &#40;SQL Server&#41;</span></span>](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [<span data-ttu-id="883c4-137">配置对可用性副本的只读访问 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="883c4-137">Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;</span></span>](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="883c4-138">为可用性组配置只读路由 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="883c4-138">Configure Read-Only Routing for an Availability Group &#40;SQL Server&#41;</span></span>](configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="883c4-139">更改可用性副本的会话超时期限 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="883c4-139">Change the Session-Timeout Period for an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
 <span data-ttu-id="883c4-140">**管理可用性数据库**</span><span class="sxs-lookup"><span data-stu-id="883c4-140">**To manage an availability database**</span></span>  
  
-   [<span data-ttu-id="883c4-141">将数据库添加到可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="883c4-141">Add a Database to an Availability Group &#40;SQL Server&#41;</span></span>](availability-group-add-a-database.md)  
  
-   [<span data-ttu-id="883c4-142">将辅助数据库联接到可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="883c4-142">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="883c4-143">将主数据库从可用性组删除 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="883c4-143">Remove a Primary Database from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-primary-database-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="883c4-144">将辅助数据库从可用性组删除 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="883c4-144">Remove a Secondary Database from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-database-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="883c4-145">挂起可用性数据库 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="883c4-145">Suspend an Availability Database &#40;SQL Server&#41;</span></span>](suspend-an-availability-database-sql-server.md)  
  
-   [<span data-ttu-id="883c4-146">恢复可用性数据库 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="883c4-146">Resume an Availability Database &#40;SQL Server&#41;</span></span>](resume-an-availability-database-sql-server.md)  
  
 <span data-ttu-id="883c4-147">**监视可用性组**</span><span class="sxs-lookup"><span data-stu-id="883c4-147">**To monitor an availability group**</span></span>  
  
-   [<span data-ttu-id="883c4-148">监视可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="883c4-148">Monitoring of Availability Groups &#40;SQL Server&#41;</span></span>](monitoring-of-availability-groups-sql-server.md)  
  
 <span data-ttu-id="883c4-149">**为了支持将可用性组迁移到新的 WSFC 群集（跨群集迁移）**</span><span class="sxs-lookup"><span data-stu-id="883c4-149">**To support migrating availability groups to a new WSFC cluster (cross-cluster migration)**</span></span>  
  
-   [<span data-ttu-id="883c4-150">更改服务器实例的 HADR 群集上下文 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="883c4-150">Change the HADR Cluster Context of Server Instance &#40;SQL Server&#41;</span></span>](change-the-hadr-cluster-context-of-server-instance-sql-server.md)  
  
-   [<span data-ttu-id="883c4-151">使可用性组脱机 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="883c4-151">Take an Availability Group Offline &#40;SQL Server&#41;</span></span>](../../take-an-availability-group-offline-sql-server.md)  
  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="883c4-152">相关内容</span><span class="sxs-lookup"><span data-stu-id="883c4-152">Related Content</span></span>  
  
-   <span data-ttu-id="883c4-153">**博客：**</span><span class="sxs-lookup"><span data-stu-id="883c4-153">**Blogs:**</span></span>  
  
     [<span data-ttu-id="883c4-154">SQL Server AlwaysOn 团队博客：SQL Server AlwaysOn 官方团队博客</span><span class="sxs-lookup"><span data-stu-id="883c4-154">SQL Server AlwaysOn Team Blogs: The official SQL Server AlwaysOn Team Blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [<span data-ttu-id="883c4-155">CSS SQL Server 工程师博客</span><span class="sxs-lookup"><span data-stu-id="883c4-155">CSS SQL Server Engineers Blogs</span></span>](https://blogs.msdn.com/b/psssql/)  
  
-   <span data-ttu-id="883c4-156">**视频：**</span><span class="sxs-lookup"><span data-stu-id="883c4-156">**Videos:**</span></span>  
  
     [<span data-ttu-id="883c4-157">Microsoft SQL Server Code-Named "Denali" AlwaysOn 系列，第一部分：介绍下一代高可用性解决方案</span><span class="sxs-lookup"><span data-stu-id="883c4-157">Microsoft SQL Server Code-Named "Denali" AlwaysOn Series,Part 1: Introducing the Next Generation High Availability Solution</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [<span data-ttu-id="883c4-158">Microsoft SQL Server Code-Named "Denali" AlwaysOn 系列，第二部分：使用 AlwaysOn 生成关键任务高可用性解决方案</span><span class="sxs-lookup"><span data-stu-id="883c4-158">Microsoft SQL Server Code-Named "Denali" AlwaysOn Series,Part 2: Building a Mission-Critical High Availability Solution Using AlwaysOn</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   <span data-ttu-id="883c4-159">**白皮书：**</span><span class="sxs-lookup"><span data-stu-id="883c4-159">**White papers:**</span></span>  
  
     [<span data-ttu-id="883c4-160">针对 SQL Server 2012 的 Microsoft 白皮书</span><span class="sxs-lookup"><span data-stu-id="883c4-160">Microsoft White Papers for SQL Server 2012</span></span>](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [<span data-ttu-id="883c4-161">SQL Server 客户咨询团队白皮书</span><span class="sxs-lookup"><span data-stu-id="883c4-161">SQL Server Customer Advisory Team Whitepapers</span></span>](http://sqlcat.com/)  
  
  
## <a name="see-also"></a><span data-ttu-id="883c4-162">另请参阅</span><span class="sxs-lookup"><span data-stu-id="883c4-162">See Also</span></span>  
 <span data-ttu-id="883c4-163">[AlwaysOn 可用性组 &#40;SQL Server&#41;](always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="883c4-163">[AlwaysOn Availability Groups &#40;SQL Server&#41;](always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="883c4-164">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="883c4-164">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="883c4-165">配置 AlwaysOn 可用性组 &#40;SQL Server 的服务器实例&#41;</span><span class="sxs-lookup"><span data-stu-id="883c4-165">Configuration of a Server Instance for AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](configuration-of-a-server-instance-for-always-on-availability-groups-sql-server.md)  
 <span data-ttu-id="883c4-166">[创建和配置可用性组 (SQL Server)](creation-and-configuration-of-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="883c4-166">[Creation and Configuration of Availability Groups &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="883c4-167">[活动辅助副本：可读辅助副本 &#40;AlwaysOn 可用性组&#41;](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="883c4-167">[Active Secondaries: Readable Secondary Replicas &#40;AlwaysOn Availability Groups&#41;](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) </span></span>  
 [<span data-ttu-id="883c4-168">活动辅助副本：辅助副本上的备份 &#40;AlwaysOn 可用性组&#41;</span><span class="sxs-lookup"><span data-stu-id="883c4-168">Active Secondaries: Backup on Secondary Replicas &#40;AlwaysOn Availability Groups&#41;</span></span>](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md)  
 <span data-ttu-id="883c4-169">[可用性组侦听程序、客户端连接和应用程序故障转移 &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span><span class="sxs-lookup"><span data-stu-id="883c4-169">[Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span></span>  
 <span data-ttu-id="883c4-170">[AlwaysOn 可用性组 &#40;SQL Server 的操作问题的 AlwaysOn 策略&#41;](always-on-policies-for-operational-issues-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="883c4-170">[AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups &#40;SQL Server&#41;](always-on-policies-for-operational-issues-always-on-availability.md) </span></span>  
 <span data-ttu-id="883c4-171">[监视可用性组 (SQL Server)](monitoring-of-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="883c4-171">[Monitoring of Availability Groups &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="883c4-172">[AlwaysOn 可用性组：互操作性 &#40;SQL Server&#41;](always-on-availability-groups-interoperability-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="883c4-172">[AlwaysOn Availability Groups: Interoperability &#40;SQL Server&#41;](always-on-availability-groups-interoperability-sql-server.md) </span></span>  
 <span data-ttu-id="883c4-173">[AlwaysOn 可用性组 &#40;SQL Server 的 Transact-sql 语句概述&#41;](transact-sql-statements-for-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="883c4-173">[Overview of Transact-SQL Statements for AlwaysOn Availability Groups &#40;SQL Server&#41;](transact-sql-statements-for-always-on-availability-groups.md) </span></span>  
 [<span data-ttu-id="883c4-174">适用于 AlwaysOn 可用性组 &#40;SQL Server 的 PowerShell Cmdlet 概述&#41;</span><span class="sxs-lookup"><span data-stu-id="883c4-174">Overview of PowerShell Cmdlets for AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-powershell-cmdlets-for-always-on-availability-groups-sql-server.md)  
  
