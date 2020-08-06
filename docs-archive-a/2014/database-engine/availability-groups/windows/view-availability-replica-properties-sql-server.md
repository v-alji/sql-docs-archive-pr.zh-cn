---
title: 查看可用性副本属性 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- ', policies'
ms.assetid: 14fed3c4-8ecc-4e1c-931d-a7ec1e9f9e90
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6ca7b0508907b4d86c9ee627438a3f18e1b01fdc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690148"
---
# <a name="view-availability-replica-properties-sql-server"></a><span data-ttu-id="6055d-102">查看可用性副本属性 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6055d-102">View Availability Replica Properties (SQL Server)</span></span>
  <span data-ttu-id="6055d-103">本主题介绍如何通过使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 中的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 或 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]查看 AlwaysOn 可用性组的可用性副本属性。</span><span class="sxs-lookup"><span data-stu-id="6055d-103">This topic describes how to view the properties of an availability replica for an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6055d-104">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6055d-104">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="6055d-105">**查看和更改可用性副本的属性**</span><span class="sxs-lookup"><span data-stu-id="6055d-105">**To view and change properties an availability replica**</span></span>  
  
1.  <span data-ttu-id="6055d-106">在对象资源管理器中，连接到承载主副本的服务器实例，然后展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="6055d-106">In Object Explorer, connect to the server instance that hosts the primary replica, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="6055d-107">依次展开 **“AlwaysOn 高可用性”** 节点和 **“可用性组”** 节点。</span><span class="sxs-lookup"><span data-stu-id="6055d-107">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="6055d-108">展开可用性副本所属的可用性组，然后展开 **“可用性副本”** 节点。</span><span class="sxs-lookup"><span data-stu-id="6055d-108">Expand the availability group to which the availability replica belongs, and expand the **Availability Replicas** node.</span></span>  
  
4.  <span data-ttu-id="6055d-109">右键单击要查看其属性的可用性副本，然后选择“属性”\*\*\*\* 命令。</span><span class="sxs-lookup"><span data-stu-id="6055d-109">Right-click the availability replica whose properties you want to view, and select the **Properties** command.</span></span>  
  
5.  <span data-ttu-id="6055d-110">在 **“可用性副本属性”** 对话框中，使用 **“常规”** 页查看该副本的属性。</span><span class="sxs-lookup"><span data-stu-id="6055d-110">In the **Availability Replica Properties** dialog box, use the **General** page to view the properties of this replica.</span></span> <span data-ttu-id="6055d-111">如果连接到主副本，您可以更改下列属性：可用性模式、故障转移模式、主角色的连接访问权限、辅助角色（可读取的辅助副本）的读取访问权限以及会话超时值。</span><span class="sxs-lookup"><span data-stu-id="6055d-111">If you are connected to the primary replica, you can change the following properties: availability mode, failover mode, connection access for the primary role, read-access for the secondary role (readable-secondary), and the session-timeout value.</span></span> <span data-ttu-id="6055d-112">有关详细信息，请参阅 " [&#40;常规" 页面&#41;的可用性副本属性](availability-replica-properties-general-page.md)。</span><span class="sxs-lookup"><span data-stu-id="6055d-112">For more information, see  [Availability Replica Properties &#40;General Page&#41;](availability-replica-properties-general-page.md).</span></span>  
  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="6055d-113">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6055d-113">Using Transact-SQL</span></span>  
 <span data-ttu-id="6055d-114">**查看可用性副本的属性和状态**</span><span class="sxs-lookup"><span data-stu-id="6055d-114">**To view properties and states of availability replicas**</span></span>  
  
 <span data-ttu-id="6055d-115">若要查看可用性副本的属性和状态，请使用以下视图和系统函数：</span><span class="sxs-lookup"><span data-stu-id="6055d-115">To view the properties and states of availability replicas, use the following views and system function:</span></span>  
  
 [<span data-ttu-id="6055d-116">sys.availability_replicas</span><span class="sxs-lookup"><span data-stu-id="6055d-116">sys.availability_replicas</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql)  
 <span data-ttu-id="6055d-117">为 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的本地实例承载其可用性副本的每个可用性组中的每个可用性副本返回一行。</span><span class="sxs-lookup"><span data-stu-id="6055d-117">Returns a row for every availability replica in each availability group for which the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] hosts an availability replica.</span></span>  
  
 <span data-ttu-id="6055d-118">**列名：** replica_id、group_id、replica_metadata_id、replica_server_name、owner_sid、endpoint_url、availability_mode、availability_mode_desc、failover_mode、failover_mode_desc、session_timeout、primary_role_allow_connections、primary_role_allow_connections_desc、secondary_role_allow_connections、secondary_role_allow_connections_desc、create_date、modify_date、backup_priority、read_only_routing_url</span><span class="sxs-lookup"><span data-stu-id="6055d-118">**Column names:** replica_id, group_id, replica_metadata_id, replica_server_name, owner_sid, endpoint_url, availability_mode, availability_mode_desc, failover_mode, failover_mode_desc, session_timeout, primary_role_allow_connections, primary_role_allow_connections_desc, secondary_role_allow_connections, secondary_role_allow_connections_desc, create_date, modify_date, backup_priority, read_only_routing_url</span></span>  
  
 [<span data-ttu-id="6055d-119">sys.availability_read_only_routing_lists</span><span class="sxs-lookup"><span data-stu-id="6055d-119">sys.availability_read_only_routing_lists</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-read-only-routing-lists-transact-sql)  
 <span data-ttu-id="6055d-120">为 WSFC 故障转移群集中 AlwaysOn 可用性组的每个可用性副本的只读路由列表返回一行。</span><span class="sxs-lookup"><span data-stu-id="6055d-120">Returns a row for the read only routing list of each availability replica in an AlwaysOn availability group in the WSFC failover cluster.</span></span>  
  
 <span data-ttu-id="6055d-121">**列名：** replica_id、routing_priority、read_only_replica_id</span><span class="sxs-lookup"><span data-stu-id="6055d-121">**Column names:** replica_id, routing_priority, read_only_replica_id</span></span>  
  
 [<span data-ttu-id="6055d-122">sys.dm_hadr_availability_replica_cluster_nodes</span><span class="sxs-lookup"><span data-stu-id="6055d-122">sys.dm_hadr_availability_replica_cluster_nodes</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-cluster-nodes-transact-sql)  
 <span data-ttu-id="6055d-123">为 Windows Server 故障转移群集 (WSFC) 群集中 AlwaysOn 可用性组的每个可用性副本（不论联接状态如何）都返回一行。</span><span class="sxs-lookup"><span data-stu-id="6055d-123">Returns a row for every availability replica (regardless of join state) of the AlwaysOn availability groups in the Windows Server Failover Clustering (WSFC) cluster.</span></span>  
  
 <span data-ttu-id="6055d-124">**列名：** group_name、replica_server_name、node_name</span><span class="sxs-lookup"><span data-stu-id="6055d-124">**Column names:** group_name, replica_server_name, node_name</span></span>  
  
 [<span data-ttu-id="6055d-125">sys.dm_hadr_availability_replica_cluster_states</span><span class="sxs-lookup"><span data-stu-id="6055d-125">sys.dm_hadr_availability_replica_cluster_states</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-cluster-states-transact-sql)  
 <span data-ttu-id="6055d-126">为 Windows Server 故障转移群集 (WSFC) 群集中所有 AlwaysOn 可用性组（不论副本位于何处）的每个副本（不论联接状态如何）都返回一行。</span><span class="sxs-lookup"><span data-stu-id="6055d-126">Returns a row for each replica (regardless of join state) of all AlwaysOn availability groups (regardless of replica location) in the Windows Server Failover Clustering (WSFC) cluster.</span></span>  
  
 <span data-ttu-id="6055d-127">**列名：** replica_id、replica_server_name、group_id、join_state、join_state_desc</span><span class="sxs-lookup"><span data-stu-id="6055d-127">**Column names:** replica_id, replica_server_name, group_id, join_state, join_state_desc</span></span>  
  
 [<span data-ttu-id="6055d-128">sys.dm_hadr_availability_replica_states</span><span class="sxs-lookup"><span data-stu-id="6055d-128">sys.dm_hadr_availability_replica_states</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-states-transact-sql)  
 <span data-ttu-id="6055d-129">返回一行以显示每个本地可用性副本的状态，并为同一可用性组中的每个远程可用性副本返回一行。</span><span class="sxs-lookup"><span data-stu-id="6055d-129">Returns a row showing the state of each local availability replica and a row for each remote availability replica in the same availability group.</span></span>  
  
 <span data-ttu-id="6055d-130">**列名：** replica_id、group_id、is_local、role、role_desc、operational_state、operational_state_desc、connected_state、connected_state_desc、recovery_health、recovery_health_desc、synchronization_health、synchronization_health_desc、last_connect_error_number、last_connect_error_description 和 last_connect_error_timestamp</span><span class="sxs-lookup"><span data-stu-id="6055d-130">**Column names:** replica_id, group_id, is_local, role, role_desc, operational_state, operational_state_desc, connected_state, connected_state_desc, recovery_health, recovery_health_desc, synchronization_health, synchronization_health_desc, last_connect_error_number, last_connect_error_description, and last_connect_error_timestamp</span></span>  
  
 [<span data-ttu-id="6055d-131">sys.fn_hadr_backup_is_preferred_replica</span><span class="sxs-lookup"><span data-stu-id="6055d-131">sys.fn_hadr_backup_is_preferred_replica</span></span>](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql)  
 <span data-ttu-id="6055d-132">确定当前副本是否为首选备份副本。</span><span class="sxs-lookup"><span data-stu-id="6055d-132">Determines whether the current replica is the preferred backup replica.</span></span> <span data-ttu-id="6055d-133">如果当前服务器实例上的数据库是首选副本，则返回 1。</span><span class="sxs-lookup"><span data-stu-id="6055d-133">Returns 1 if the database on the current server instance is the preferred replica.</span></span> <span data-ttu-id="6055d-134">否则，返回 0。</span><span class="sxs-lookup"><span data-stu-id="6055d-134">Otherwise, it returns 0.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6055d-135">有关可用性副本的性能计数器（ **SQLServer:Availability Replica**  性能对象）的信息，请参阅 [SQL Server，可用性副本](../../../relational-databases/performance-monitor/sql-server-availability-replica.md)。</span><span class="sxs-lookup"><span data-stu-id="6055d-135">For information about performance counters for availability replicas (the **SQLServer:Availability Replica**  performance object), see [SQL Server, Availability Replica](../../../relational-databases/performance-monitor/sql-server-availability-replica.md).</span></span>  
  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="6055d-136">相关任务</span><span class="sxs-lookup"><span data-stu-id="6055d-136">Related Tasks</span></span>  
 <span data-ttu-id="6055d-137">**查看有关可用性组的信息**</span><span class="sxs-lookup"><span data-stu-id="6055d-137">**To view information about availability groups**</span></span>  
  
-   [<span data-ttu-id="6055d-138">查看可用性组属性 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6055d-138">View Availability Group Properties &#40;SQL Server&#41;</span></span>](view-availability-group-properties-sql-server.md)  
  
-   [<span data-ttu-id="6055d-139">查看可用性组侦听程序属性 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6055d-139">View Availability Group Listener Properties &#40;SQL Server&#41;</span></span>](view-availability-group-listener-properties-sql-server.md)  
  
-   [<span data-ttu-id="6055d-140">AlwaysOn 可用性组 &#40;SQL Server 的操作问题的 AlwaysOn 策略&#41;</span><span class="sxs-lookup"><span data-stu-id="6055d-140">AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](always-on-policies-for-operational-issues-always-on-availability.md)
  
-   [<span data-ttu-id="6055d-141">使用 AlwaysOn 面板 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="6055d-141">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="6055d-142">监视可用性组 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6055d-142">Monitor Availability Groups &#40;Transact-SQL&#41;</span></span>](monitor-availability-groups-transact-sql.md)  
  
 <span data-ttu-id="6055d-143">**管理可用性副本**</span><span class="sxs-lookup"><span data-stu-id="6055d-143">**To manage availability replicas**</span></span>  
  
-   [<span data-ttu-id="6055d-144">将辅助副本添加到可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6055d-144">Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="6055d-145">将辅助副本联接到可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6055d-145">Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="6055d-146">配置对可用性副本的只读访问 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6055d-146">Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;</span></span>](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="6055d-147">更改可用性副本的可用性模式 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6055d-147">Change the Availability Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-availability-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="6055d-148">更改可用性副本的故障转移模式 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6055d-148">Change the Failover Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-failover-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="6055d-149">更改可用性副本的会话超时期限 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6055d-149">Change the Session-Timeout Period for an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="6055d-150">将次要副本从可用性组删除 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6055d-150">Remove a Secondary Replica from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-replica-from-an-availability-group-sql-server.md)  
  
 <span data-ttu-id="6055d-151">**管理可用性数据库**</span><span class="sxs-lookup"><span data-stu-id="6055d-151">**To manage an availability database**</span></span>  
  
-   [<span data-ttu-id="6055d-152">将数据库添加到可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6055d-152">Add a Database to an Availability Group &#40;SQL Server&#41;</span></span>](availability-group-add-a-database.md)  
  
-   [<span data-ttu-id="6055d-153">将辅助数据库联接到可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6055d-153">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="6055d-154">挂起可用性数据库 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6055d-154">Suspend an Availability Database &#40;SQL Server&#41;</span></span>](suspend-an-availability-database-sql-server.md)  
  
-   [<span data-ttu-id="6055d-155">恢复可用性数据库 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6055d-155">Resume an Availability Database &#40;SQL Server&#41;</span></span>](resume-an-availability-database-sql-server.md)  
  
-   [<span data-ttu-id="6055d-156">将辅助数据库从可用性组删除 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6055d-156">Remove a Secondary Database from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-database-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="6055d-157">将主数据库从可用性组删除 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6055d-157">Remove a Primary Database from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-primary-database-from-an-availability-group-sql-server.md)  
  
  
## <a name="see-also"></a><span data-ttu-id="6055d-158">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6055d-158">See Also</span></span>  
 <span data-ttu-id="6055d-159">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6055d-159">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="6055d-160">[&#40;Transact-sql 监视可用性组&#41;](monitor-availability-groups-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="6055d-160">[Monitor Availability Groups &#40;Transact-SQL&#41;](monitor-availability-groups-transact-sql.md) </span></span>  
 <span data-ttu-id="6055d-161">[AlwaysOn 可用性组 &#40;SQL Server 的操作问题的 AlwaysOn 策略&#41;](always-on-policies-for-operational-issues-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="6055d-161">[AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups &#40;SQL Server&#41;](always-on-policies-for-operational-issues-always-on-availability.md) </span></span>  
 [<span data-ttu-id="6055d-162">管理可用性组 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="6055d-162">Administration of an Availability Group &#40;SQL Server&#41;</span></span>](administration-of-an-availability-group-sql-server.md)  
  
  
