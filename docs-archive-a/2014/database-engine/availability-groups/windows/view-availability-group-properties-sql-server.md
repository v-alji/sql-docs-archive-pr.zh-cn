---
title: 查看可用性组属性 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server]
ms.assetid: 61243c87-bd62-4510-863f-2a8f347caf1f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b7d1f57a9bd29b6c65160ec9a163bc77dfca48b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580375"
---
# <a name="view-availability-group-properties-sql-server"></a><span data-ttu-id="91033-102">查看可用性组属性 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="91033-102">View Availability Group Properties (SQL Server)</span></span>
  <span data-ttu-id="91033-103">本主题说明如何通过使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 中的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 或 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]查看 AlwaysOn 可用性组的属性。</span><span class="sxs-lookup"><span data-stu-id="91033-103">This topic describes how to view the properties of an availability group for an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  

  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="91033-104">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="91033-104">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="91033-105">**查看和更改可用性组的属性**</span><span class="sxs-lookup"><span data-stu-id="91033-105">**To view and change the properties an availability group**</span></span>  
  
1.  <span data-ttu-id="91033-106">在对象资源管理器中，连接到承载主副本的服务器实例，然后展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="91033-106">In Object Explorer, connect to the server instance that hosts the primary replica, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="91033-107">依次展开 **“AlwaysOn 高可用性”** 节点和 **“可用性组”** 节点。</span><span class="sxs-lookup"><span data-stu-id="91033-107">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="91033-108">右键单击要查看其属性的可用性组，然后选择“属性”\*\*\*\* 命令。</span><span class="sxs-lookup"><span data-stu-id="91033-108">Right-click the availability group whose properties you want to view, and select the **Properties** command.</span></span>  
  
4.  <span data-ttu-id="91033-109">在 **“可用性组属性”** 对话框中，使用 **“常规”** 和 **“备份首选项”** 页查看所选可用性组的属性，在某些情况下，还可以更改这些属性。</span><span class="sxs-lookup"><span data-stu-id="91033-109">In the **Availability Group Properties** dialog box, use the **General** and **Backup Preferences** pages to view and, in some cases, change properties of the selected availability group.</span></span> <span data-ttu-id="91033-110">有关详细信息，请参阅[可用性组属性和新建可用性组（“常规”页）](availability-group-properties-new-availability-group-general-page.md)和[可用性组属性：新建可用性组（“备份首选项”页）](availability-group-properties-new-availability-group-backup-preferences-page.md)。</span><span class="sxs-lookup"><span data-stu-id="91033-110">For more information, see [Availability Group Properties and New Availability Group &#40;General Page&#41;](availability-group-properties-new-availability-group-general-page.md) and [Availability Group Properties: New Availability Group &#40;Backup Preferences Page&#41;](availability-group-properties-new-availability-group-backup-preferences-page.md).</span></span>  
  
     <span data-ttu-id="91033-111">使用 **“权限”** 页可以查看当前登录名、角色以及与可用性组关联的显式权限。</span><span class="sxs-lookup"><span data-stu-id="91033-111">Use the **Permissions** page to view the current logins, roles, and explicit permissions associated with the availability group.</span></span> <span data-ttu-id="91033-112">有关详细信息，请参阅 [Permissions or Securables Page](../../../relational-databases/security/permissions-or-securables-page.md)。</span><span class="sxs-lookup"><span data-stu-id="91033-112">For more information, see [Permissions or Securables Page](../../../relational-databases/security/permissions-or-securables-page.md).</span></span>  
  

  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="91033-113">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="91033-113">Using Transact-SQL</span></span>  
 <span data-ttu-id="91033-114">**查看可用性组的属性和状态**</span><span class="sxs-lookup"><span data-stu-id="91033-114">**To view the properties and state of an availability group**</span></span>  
  
 <span data-ttu-id="91033-115">若要查询服务器实例为其承载可用性副本的可用性组的属性和状态，请使用以下视图：</span><span class="sxs-lookup"><span data-stu-id="91033-115">To query the properties and states of the availability groups for which the server instance hosts an availability replica, use the following views:</span></span>  
  
 [<span data-ttu-id="91033-116">sys.availability_groups</span><span class="sxs-lookup"><span data-stu-id="91033-116">sys.availability_groups</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-groups-transact-sql)  
 <span data-ttu-id="91033-117">为 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的本地实例承载其可用性副本的每个可用性组返回一行。</span><span class="sxs-lookup"><span data-stu-id="91033-117">Returns a row for each availability group for which the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] hosts an availability replica.</span></span> <span data-ttu-id="91033-118">每一行都包含可用性组元数据的缓存的副本。</span><span class="sxs-lookup"><span data-stu-id="91033-118">Each row contains a cached copy of the availability group metadata.</span></span>  
  
 <span data-ttu-id="91033-119">**列名：** group_id、name、resource_id、resource_group_id、failure_condition_level、health_check_timeout、automated_backup_preference、automated_backup_preference_desc</span><span class="sxs-lookup"><span data-stu-id="91033-119">**Column names:** group_id, name, resource_id, resource_group_id, failure_condition_level, health_check_timeout, automated_backup_preference, automated_backup_preference_desc</span></span>  
  
 [<span data-ttu-id="91033-120">sys.availability_groups_cluster</span><span class="sxs-lookup"><span data-stu-id="91033-120">sys.availability_groups_cluster</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-groups-cluster-transact-sql)  
 <span data-ttu-id="91033-121">为 WSFC 群集中的每个可用性组返回一行。</span><span class="sxs-lookup"><span data-stu-id="91033-121">Returns a row for each availability group in the WSFC cluster.</span></span> <span data-ttu-id="91033-122">每一行均包含 Windows Server 故障转移群集 (WSFC) 群集中的可用性组元数据。</span><span class="sxs-lookup"><span data-stu-id="91033-122">Each row contains the availability group metadata from the Windows Server Failover Clustering (WSFC) cluster.</span></span>  
  
 <span data-ttu-id="91033-123">**列名：** group_id、name、resource_id、resource_group_id、failure_condition_level、health_check_timeout、automated_backup_preference、automated_backup_preference_desc</span><span class="sxs-lookup"><span data-stu-id="91033-123">**Column names:** group_id, name, resource_id, resource_group_id, failure_condition_level, health_check_timeout, automated_backup_preference, automated_backup_preference_desc</span></span>  
  
 [<span data-ttu-id="91033-124">sys.dm_hadr_availability_group_states</span><span class="sxs-lookup"><span data-stu-id="91033-124">sys.dm_hadr_availability_group_states</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-group-states-transact-sql)  
 <span data-ttu-id="91033-125">为在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]的本地实例上拥有可用性副本的每个可用性组返回一行。</span><span class="sxs-lookup"><span data-stu-id="91033-125">Returns a row for each availability group that possesses an availability replica on the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="91033-126">每行显示定义给定可用性组的运行状况的状态。</span><span class="sxs-lookup"><span data-stu-id="91033-126">Each row displays the states that define the health of a given availability group.</span></span>  
  
 <span data-ttu-id="91033-127">**列名：** group_id、primary_replica、primary_recovery_health、primary_recovery_health_desc、secondary_recovery_health、secondary_recovery_health_desc、synchronization_health、synchronization_health_desc</span><span class="sxs-lookup"><span data-stu-id="91033-127">**Column names:** group_id, primary_replica, primary_recovery_health, primary_recovery_health_desc, secondary_recovery_health, secondary_recovery_health_desc, synchronization_health, synchronization_health_desc</span></span>  
  

  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="91033-128">相关任务</span><span class="sxs-lookup"><span data-stu-id="91033-128">Related Tasks</span></span>  
 <span data-ttu-id="91033-129">**查看有关可用性组的信息**</span><span class="sxs-lookup"><span data-stu-id="91033-129">**To view information about availability groups**</span></span>  
  
-   [<span data-ttu-id="91033-130">查看可用性副本属性 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="91033-130">View Availability Replica Properties &#40;SQL Server&#41;</span></span>](view-availability-replica-properties-sql-server.md)  
  
-   [<span data-ttu-id="91033-131">查看可用性组侦听程序属性 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="91033-131">View Availability Group Listener Properties &#40;SQL Server&#41;</span></span>](view-availability-group-listener-properties-sql-server.md)  
  
-   [<span data-ttu-id="91033-132">AlwaysOn 可用性组 &#40;SQL Server 的操作问题的 AlwaysOn 策略&#41;</span><span class="sxs-lookup"><span data-stu-id="91033-132">AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](always-on-policies-for-operational-issues-always-on-availability.md)
  
-   [<span data-ttu-id="91033-133">使用 AlwaysOn 面板 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="91033-133">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="91033-134">监视可用性组 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="91033-134">Monitor Availability Groups &#40;Transact-SQL&#41;</span></span>](monitor-availability-groups-transact-sql.md)  
  
 <span data-ttu-id="91033-135">**配置现有的可用性组**</span><span class="sxs-lookup"><span data-stu-id="91033-135">**To configure an existing availability group**</span></span>  
  
-   [<span data-ttu-id="91033-136">将辅助副本添加到可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="91033-136">Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="91033-137">将次要副本从可用性组删除 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="91033-137">Remove a Secondary Replica from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-replica-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="91033-138">将数据库添加到可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="91033-138">Add a Database to an Availability Group &#40;SQL Server&#41;</span></span>](availability-group-add-a-database.md)  
  
-   [<span data-ttu-id="91033-139">将辅助数据库从可用性组删除 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="91033-139">Remove a Secondary Database from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-database-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="91033-140">创建或配置可用性组侦听程序 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="91033-140">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="91033-141">删除可用性组侦听程序 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="91033-141">Remove an Availability Group Listener &#40;SQL Server&#41;</span></span>](remove-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="91033-142">将主数据库从可用性组删除 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="91033-142">Remove a Primary Database from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-primary-database-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="91033-143">删除可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="91033-143">Remove an Availability Group &#40;SQL Server&#41;</span></span>](remove-an-availability-group-sql-server.md)  
  
 <span data-ttu-id="91033-144">**对可用性组执行手动故障转移**</span><span class="sxs-lookup"><span data-stu-id="91033-144">**To manually fail over an availability group**</span></span>  
  
-   [<span data-ttu-id="91033-145">执行可用性组的计划手动故障转移 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="91033-145">Perform a Planned Manual Failover of an Availability Group &#40;SQL Server&#41;</span></span>](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="91033-146">执行可用性组的强制手动故障转移 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="91033-146">Perform a Forced Manual Failover of an Availability Group &#40;SQL Server&#41;</span></span>](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)  
  

  
## <a name="see-also"></a><span data-ttu-id="91033-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="91033-147">See Also</span></span>  
 <span data-ttu-id="91033-148">[AlwaysOn 可用性组 &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) [监视可用性组的概述 &#40;Transact-sql&#41;](monitor-availability-groups-transact-sql.md) [AlwaysOn 策略 AlwaysOn 可用性组的操作问题](always-on-policies-for-operational-issues-always-on-availability.md)&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="91033-148">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) [Monitor Availability Groups &#40;Transact-SQL&#41;](monitor-availability-groups-transact-sql.md) [AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups &#40;SQL Server&#41;](always-on-policies-for-operational-issues-always-on-availability.md)</span></span> 
  
  
