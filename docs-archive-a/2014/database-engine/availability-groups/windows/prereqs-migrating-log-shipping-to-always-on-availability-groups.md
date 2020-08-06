---
title: 从日志传送迁移到 AlwaysOn 可用性组 (SQL Server) 的先决条件 |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server], AlwaysOn Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: 2738ce65-205e-4682-92d8-dc7e37c58b2b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 76b50d5af8eb520b3764ff56397c040f2d0d0141
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690804"
---
# <a name="prerequisites-for-migrating-from-log-shipping-to-alwayson-availability-groups-sql-server"></a><span data-ttu-id="a2dc8-102">从日志传送迁移到 AlwaysOn 可用性组的先决条件 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a2dc8-102">Prerequisites for Migrating from Log Shipping to AlwaysOn Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="a2dc8-103">本主题介绍将日志传送主数据库与其一个或多个辅助数据库一起转换为 AlwaysOn 主数据库和辅助数据库的先决条件。</span><span class="sxs-lookup"><span data-stu-id="a2dc8-103">This topic describes the prerequisites for converting a log shipping primary database along with one or more of its secondary databases to an AlwaysOn primary database and secondary database(s).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a2dc8-104">您可将可用性组中的任何主数据库或辅助数据库（可能可读）配置为日志传送主数据库。</span><span class="sxs-lookup"><span data-stu-id="a2dc8-104">You can configure any primary or secondary database (possibly readable) in an availability group as a log shipping primary database.</span></span>  
  
 <span data-ttu-id="a2dc8-105">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="a2dc8-105">**In This Topic:**</span></span>  
  
-   [<span data-ttu-id="a2dc8-106">可用性组先决条件</span><span class="sxs-lookup"><span data-stu-id="a2dc8-106">Availability Group Prerequisites</span></span>](#AGPrereqsRealAddress)  
  
-   [<span data-ttu-id="a2dc8-107">日志传送先决条件</span><span class="sxs-lookup"><span data-stu-id="a2dc8-107">Log Shipping Prerequisites</span></span>](#LogShipPrereqs)  
  
-   [<span data-ttu-id="a2dc8-108">相关任务</span><span class="sxs-lookup"><span data-stu-id="a2dc8-108">Related Tasks</span></span>](#RelatedTasks)  
  
-   [<span data-ttu-id="a2dc8-109">相关内容</span><span class="sxs-lookup"><span data-stu-id="a2dc8-109">Related Content</span></span>](#RelatedContent)  
  
##  <a name="availability-group-prerequisites"></a><a name="AGPrereqsRealAddress"></a><span data-ttu-id="a2dc8-110">可用性组先决条件</span><span class="sxs-lookup"><span data-stu-id="a2dc8-110">Availability Group Prerequisites</span></span>  
 <span data-ttu-id="a2dc8-111">若要允许备份作业在可用性组的主副本上运行，请使用下列 AlwaysOn 可用性组备份设置：</span><span class="sxs-lookup"><span data-stu-id="a2dc8-111">To allow backup jobs to run on the primary replica of the availability group, use the following AlwaysOn Availability Groups backup settings:</span></span>  
  
|<span data-ttu-id="a2dc8-112">Property</span><span class="sxs-lookup"><span data-stu-id="a2dc8-112">Property</span></span>|<span data-ttu-id="a2dc8-113">设置</span><span class="sxs-lookup"><span data-stu-id="a2dc8-113">Setting</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="a2dc8-114">可用性组的自动备份首选项</span><span class="sxs-lookup"><span data-stu-id="a2dc8-114">Automated backup preference of availability group</span></span>|<span data-ttu-id="a2dc8-115">仅在主副本上</span><span class="sxs-lookup"><span data-stu-id="a2dc8-115">Only on the primary replica</span></span>|  
|<span data-ttu-id="a2dc8-116">主副本的备份优先级。</span><span class="sxs-lookup"><span data-stu-id="a2dc8-116">Backup priority of the primary replica.</span></span>|<span data-ttu-id="a2dc8-117">>0</span><span class="sxs-lookup"><span data-stu-id="a2dc8-117">>0</span></span>|  
  
 <span data-ttu-id="a2dc8-118">**有关详细信息：**</span><span class="sxs-lookup"><span data-stu-id="a2dc8-118">**For more information:**</span></span>  
  
 [<span data-ttu-id="a2dc8-119">查看可用性组属性 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a2dc8-119">View Availability Group Properties &#40;SQL Server&#41;</span></span>](view-availability-group-properties-sql-server.md)  
  
 [<span data-ttu-id="a2dc8-120">配置可用性副本备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a2dc8-120">Configure Backup on Availability Replicas &#40;SQL Server&#41;</span></span>](configure-backup-on-availability-replicas-sql-server.md)  
  
##  <a name="log-shipping-prerequisites"></a><a name="LogShipPrereqs"></a> <span data-ttu-id="a2dc8-121">日志传送先决条件</span><span class="sxs-lookup"><span data-stu-id="a2dc8-121">Log Shipping Prerequisites</span></span>  
  
-   <span data-ttu-id="a2dc8-122">日志传送主数据库必须驻留在承载可用性组的初始/当前主副本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例上。</span><span class="sxs-lookup"><span data-stu-id="a2dc8-122">The log shipping primary database must reside on the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosts the initial/current primary replica of the availability group.</span></span>  
  
-   <span data-ttu-id="a2dc8-123">为使某一给定的日志传送辅助数据库可转换为 AlwaysOn 辅助数据库，该数据库必须：</span><span class="sxs-lookup"><span data-stu-id="a2dc8-123">For a given log shipping secondary database to be converted to an AlwaysOn secondary database, it must:</span></span>  
  
    -   <span data-ttu-id="a2dc8-124">使用与主数据库相同的名称。</span><span class="sxs-lookup"><span data-stu-id="a2dc8-124">Use the same name as the primary database.</span></span>  
  
    -   <span data-ttu-id="a2dc8-125">驻留在为可用性组承载辅助副本的服务器实例上。</span><span class="sxs-lookup"><span data-stu-id="a2dc8-125">Reside on a server instance that hosts a secondary replica for the availability group.</span></span>  
  
 <span data-ttu-id="a2dc8-126">在备份作业已在主数据库上运行后，禁用该备份作业；并且在还原作业已在给定辅助数据库上运行后，禁用还原作业。</span><span class="sxs-lookup"><span data-stu-id="a2dc8-126">Once the backup job has run on the primary database, disable the backup job, and once the restore job has run on a given secondary database, disable the restore job.</span></span>  
  
 <span data-ttu-id="a2dc8-127">在您为可用性组创建了所有辅助数据库后，如果您想要在辅助副本上执行备份，则需要重新配置该可用性组的自动备份首选项。</span><span class="sxs-lookup"><span data-stu-id="a2dc8-127">After you have created all the secondary databases for the availability group, if you want to perform backups on secondary replicas, you need to re-configure the automated backup preference of the availability group.</span></span>  
  
 <span data-ttu-id="a2dc8-128">**有关详细信息：**</span><span class="sxs-lookup"><span data-stu-id="a2dc8-128">**For more information:**</span></span>  
  
 <span data-ttu-id="a2dc8-129">[将日志传送配置转换为可用性组](https://blogs.msdn.com/b/sqlalwayson/archive/2012/01/09/converting-a-logshipping-configuration-to-availability-group.aspx) （SQL Server 博客）</span><span class="sxs-lookup"><span data-stu-id="a2dc8-129">[Converting a logshipping configuration to Availability Group](https://blogs.msdn.com/b/sqlalwayson/archive/2012/01/09/converting-a-logshipping-configuration-to-availability-group.aspx) (a SQL Server blog)</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="a2dc8-130">相关任务</span><span class="sxs-lookup"><span data-stu-id="a2dc8-130">Related Tasks</span></span>  
 <span data-ttu-id="a2dc8-131">**日志传送**</span><span class="sxs-lookup"><span data-stu-id="a2dc8-131">**Log shipping**</span></span>  
  
-   [<span data-ttu-id="a2dc8-132">将日志传送升级到 SQL Server 2014 &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="a2dc8-132">Upgrade Log Shipping to SQL Server 2014 &#40;Transact-SQL&#41;</span></span>](../../log-shipping/upgrading-log-shipping-to-sql-server-2016-transact-sql.md)  
  
-   [<span data-ttu-id="a2dc8-133">删除日志传送 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a2dc8-133">Remove Log Shipping &#40;SQL Server&#41;</span></span>](../../log-shipping/remove-log-shipping-sql-server.md)  
  
 <span data-ttu-id="a2dc8-134">**AlwaysOn 可用性组**</span><span class="sxs-lookup"><span data-stu-id="a2dc8-134">**AlwaysOn Availability Groups**</span></span>  
  
-   [<span data-ttu-id="a2dc8-135">使用可用性组向导 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="a2dc8-135">Use the Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="a2dc8-136">使用“新建可用性组”对话框 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="a2dc8-136">Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;</span></span>](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="a2dc8-137">创建可用性组 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a2dc8-137">Create an Availability Group &#40;Transact-SQL&#41;</span></span>](create-an-availability-group-transact-sql.md)  
  
-   [<span data-ttu-id="a2dc8-138">创建可用性组 (SQL Server PowerShell)</span><span class="sxs-lookup"><span data-stu-id="a2dc8-138">Create an Availability Group &#40;SQL Server PowerShell&#41;</span></span>](../../../powershell/sql-server-powershell.md)  
  
-   [<span data-ttu-id="a2dc8-139">将辅助数据库联接到可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a2dc8-139">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="a2dc8-140">配置可用性副本备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a2dc8-140">Configure Backup on Availability Replicas &#40;SQL Server&#41;</span></span>](configure-backup-on-availability-replicas-sql-server.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="a2dc8-141">相关内容</span><span class="sxs-lookup"><span data-stu-id="a2dc8-141">Related Content</span></span>  
  
-   <span data-ttu-id="a2dc8-142">**博客：**</span><span class="sxs-lookup"><span data-stu-id="a2dc8-142">**Blogs:**</span></span>  
  
     [<span data-ttu-id="a2dc8-143">将日志传送配置转换为可用性组</span><span class="sxs-lookup"><span data-stu-id="a2dc8-143">Converting a logshipping configuration to Availability Group</span></span>](https://docs.microsoft.com/archive/blogs/sqlalwayson/converting-a-logshipping-configuration-to-availability-group)  
  
     [<span data-ttu-id="a2dc8-144">将日志传送主数据库和辅助数据库添加到现有可用性组</span><span class="sxs-lookup"><span data-stu-id="a2dc8-144">Add a Log Shipping Primary Database and Secondary Database(s) to an Existing Availability Group</span></span>](https://docs.microsoft.com/archive/blogs/sqlalwayson/add-a-log-shipping-primary-database-and-secondary-databases-to-an-existing-availability-group)  
  
     [<span data-ttu-id="a2dc8-145">SQL Server AlwaysOn 团队博客：SQL Server AlwaysOn 官方团队博客</span><span class="sxs-lookup"><span data-stu-id="a2dc8-145">SQL Server AlwaysOn Team Blogs: The official SQL Server AlwaysOn Team Blog</span></span>](https://docs.microsoft.com/archive/blogs/sqlalwayson/)  
  
     [<span data-ttu-id="a2dc8-146">CSS SQL Server 工程师博客</span><span class="sxs-lookup"><span data-stu-id="a2dc8-146">CSS SQL Server Engineers Blogs</span></span>](https://blogs.msdn.com/b/psssql/)  
  
-   <span data-ttu-id="a2dc8-147">**白皮书：**</span><span class="sxs-lookup"><span data-stu-id="a2dc8-147">**Whitepapers:**</span></span>  
  
     [<span data-ttu-id="a2dc8-148">迁移指南：从之前组合数据库镜像和日志传送的部署迁移到 AlwaysOn 可用性组</span><span class="sxs-lookup"><span data-stu-id="a2dc8-148">Migration Guide: Migrating to AlwaysOn Availability Groups from Prior Deployments Combining Database Mirroring and Log Shipping</span></span>](https://msdn.microsoft.com/library/jj635217)  
  
     [<span data-ttu-id="a2dc8-149">针对 SQL Server 2012 的 Microsoft 白皮书</span><span class="sxs-lookup"><span data-stu-id="a2dc8-149">Microsoft White Papers for SQL Server 2012</span></span>](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [<span data-ttu-id="a2dc8-150">SQL Server 客户咨询团队白皮书</span><span class="sxs-lookup"><span data-stu-id="a2dc8-150">SQL Server Customer Advisory Team Whitepapers</span></span>](http://sqlcat.com/)  
  
## <a name="see-also"></a><span data-ttu-id="a2dc8-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a2dc8-151">See Also</span></span>  
 <span data-ttu-id="a2dc8-152">[关于日志传送 (SQL Server)](../../log-shipping/about-log-shipping-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a2dc8-152">[About Log Shipping &#40;SQL Server&#41;](../../log-shipping/about-log-shipping-sql-server.md) </span></span>  
 <span data-ttu-id="a2dc8-153">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a2dc8-153">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="a2dc8-154">监视可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a2dc8-154">Monitoring of Availability Groups &#40;SQL Server&#41;</span></span>](monitoring-of-availability-groups-sql-server.md)  
  
  
