---
title: 监视可用性组 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- dynamic management views [SQL Server], AlwaysOn Availability Groups
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], listeners
- Availability Groups [SQL Server], databases
- catalog views [SQL Server], AlwaysOn Availability Groups
ms.assetid: 881a34de-8461-4811-8c62-322bf7226bed
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 103dd8eef782dfa7a4d13929b0b832dba9bc46e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580381"
---
# <a name="monitor-availability-groups-transact-sql"></a><span data-ttu-id="0d257-102">监视可用性组 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0d257-102">Monitor Availability Groups (Transact-SQL)</span></span>
  <span data-ttu-id="0d257-103">为了使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)]来监视可用性组和副本及关联的数据库， [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 提供了一组目录视图和动态管理视图及服务器属性。</span><span class="sxs-lookup"><span data-stu-id="0d257-103">For monitoring availability groups and replicas and the associated databases by using [!INCLUDE[tsql](../../../includes/tsql-md.md)], [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] provides a set of catalog and dynamic management views and server properties.</span></span> <span data-ttu-id="0d257-104">通过使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)] SELECT 语句，您可以使用这些视图监视可用性组及其副本和数据库。</span><span class="sxs-lookup"><span data-stu-id="0d257-104">Using [!INCLUDE[tsql](../../../includes/tsql-md.md)] SELECT statements, you can use the views to monitor availability groups and their replicas and databases.</span></span> <span data-ttu-id="0d257-105">为给定可用性组返回的信息取决于您连接到的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例承载的是主副本还是辅助副本。</span><span class="sxs-lookup"><span data-stu-id="0d257-105">The information returned for a given availability group depends on whether you are connected to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that is hosting the primary replica or a secondary replica.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="0d257-106">可以使用这些视图的 ID 列来联接很多视图，以便在单个查询中返回多个视图的信息。</span><span class="sxs-lookup"><span data-stu-id="0d257-106">Many of these views can be joined using their ID columns to return information from multiple views in a single query.</span></span>  
  
 
  
##  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="0d257-107">权限</span><span class="sxs-lookup"><span data-stu-id="0d257-107">Permissions</span></span>  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] <span data-ttu-id="0d257-108">目录视图要求具有服务器实例的 VIEW ANY DEFINITION 权限。</span><span class="sxs-lookup"><span data-stu-id="0d257-108">catalog views require VIEW ANY DEFINITION permission on the server instance.</span></span> [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] <span data-ttu-id="0d257-109">动态管理视图要求具有服务器的 VIEW SERVER STATE 权限。</span><span class="sxs-lookup"><span data-stu-id="0d257-109">dynamic management views require VIEW SERVER STATE permission on the server.</span></span>  
  
##  <a name="monitoring-the-alwayson-availability-groups-feature-on-a-server-instance"></a><a name="AoAgFeatureOnSI"></a><span data-ttu-id="0d257-110">监视服务器实例上的 AlwaysOn 可用性组功能</span><span class="sxs-lookup"><span data-stu-id="0d257-110">Monitoring the AlwaysOn Availability Groups Feature on a Server Instance</span></span>  
 <span data-ttu-id="0d257-111">若要监视服务器实例上的 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 功能，请使用以下内置函数：</span><span class="sxs-lookup"><span data-stu-id="0d257-111">To monitor the [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] feature on a server instance, use the following built-in function:</span></span>  
  
 <span data-ttu-id="0d257-112">[SERVERPROPERTY](/sql/t-sql/functions/serverproperty-transact-sql) 函数</span><span class="sxs-lookup"><span data-stu-id="0d257-112">[SERVERPROPERTY](/sql/t-sql/functions/serverproperty-transact-sql) function</span></span>  
 <span data-ttu-id="0d257-113">返回有关是否已启用 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 的服务器属性信息；如果已启用，则返回其在服务器实例上是否启动的信息。</span><span class="sxs-lookup"><span data-stu-id="0d257-113">Returns server property information about whether [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] is enabled and, if so, whether it has started on the server instance.</span></span>  
  
 <span data-ttu-id="0d257-114">**列名：** IsHadrEnabled、HadrManagerStatus</span><span class="sxs-lookup"><span data-stu-id="0d257-114">**Column names:** IsHadrEnabled, HadrManagerStatus</span></span>  
  
##  <a name="monitoring-availability-groups-on-the-wsfc-cluster"></a><a name="WSFC"></a> <span data-ttu-id="0d257-115">监视 WSFC 群集上的可用性组</span><span class="sxs-lookup"><span data-stu-id="0d257-115">Monitoring Availability Groups on the WSFC Cluster</span></span>  
 <span data-ttu-id="0d257-116">若要监视 Windows Server 故障转移群集 (WSFC) 群集（承载启用了 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]的本地服务器实例），请使用以下视图：</span><span class="sxs-lookup"><span data-stu-id="0d257-116">To monitor the Windows Server Failover Clustering (WSFC) cluster that hosts a local server instance that is enabled for [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], use the following views:</span></span>  
  
 [<span data-ttu-id="0d257-117">sys.dm_hadr_cluster</span><span class="sxs-lookup"><span data-stu-id="0d257-117">sys.dm_hadr_cluster</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-transact-sql)  
 <span data-ttu-id="0d257-118">如果承载启用了 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 的 SQL Server 实例的 Windows Server 故障转移群集 (WSFC) 节点具有 WSFC 仲裁，则 **sys.dm_hadr_cluster** 将返回公开群集名称和仲裁信息的一行。</span><span class="sxs-lookup"><span data-stu-id="0d257-118">If the Windows Server Failover Clustering (WSFC) node that hosts an instance of SQL Server with [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] enabled has WSFC quorum, **sys.dm_hadr_cluster** returns a row that exposes the cluster name and information about the quorum.</span></span> <span data-ttu-id="0d257-119">如果 WSFC 节点没有仲裁，则不会返回任何行。</span><span class="sxs-lookup"><span data-stu-id="0d257-119">If the WSFC node has no quorum, no rows are returned.</span></span>  
  
 <span data-ttu-id="0d257-120">**列名：** cluster_name、quorum_type、quorum_type_desc、quorum_state、quorum_state_desc</span><span class="sxs-lookup"><span data-stu-id="0d257-120">**Column names:** cluster_name, quorum_type, quorum_type_desc, quorum_state, quorum_state_desc</span></span>  
  
 [<span data-ttu-id="0d257-121">sys.dm_hadr_cluster_members</span><span class="sxs-lookup"><span data-stu-id="0d257-121">sys.dm_hadr_cluster_members</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-members-transact-sql)  
 <span data-ttu-id="0d257-122">如果承载启用了 AlwaysOn 的 SQL Server 本地实例的 WSFC 节点具有 WSFC 仲裁，则为构成仲裁的每一个成员及各个成员的状态都返回一行。</span><span class="sxs-lookup"><span data-stu-id="0d257-122">If the WSFC node that hosts the local AlwaysOn-enabled instance of SQL Server has WSFC quorum, returns a row for each of the members that constitute the quorum and the state of each of them.</span></span>  
  
 <span data-ttu-id="0d257-123">**列名：** member_name、member_type、member_type_desc、member_state、member_state_desc、number_of_quorum_votes</span><span class="sxs-lookup"><span data-stu-id="0d257-123">**Column names:** member_name, member_type, member_type_desc, member_state, member_state_desc, number_of_quorum_votes</span></span>  
  
 [<span data-ttu-id="0d257-124">sys.dm_hadr_cluster_networks</span><span class="sxs-lookup"><span data-stu-id="0d257-124">sys.dm_hadr_cluster_networks</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-networks-transact-sql)  
 <span data-ttu-id="0d257-125">为每个参与可用性组子网配置的成员都返回一行。</span><span class="sxs-lookup"><span data-stu-id="0d257-125">Returns a row for every member that is participating in an availability group's subnet configuration.</span></span> <span data-ttu-id="0d257-126">您可以使用此动态管理视图来验证为每个可用性副本配置的网络虚拟 IP。</span><span class="sxs-lookup"><span data-stu-id="0d257-126">You can use this dynamic management view to validate the network virtual IP that is configured for each availability replica.</span></span>  
  
 <span data-ttu-id="0d257-127">**列名：** member_name、network_subnet_ip、network_subnet_ipv4_mask、network_subnet_prefix_length、is_public、is_ipv4</span><span class="sxs-lookup"><span data-stu-id="0d257-127">**Column names:** member_name, network_subnet_ip, network_subnet_ipv4_mask, network_subnet_prefix_length, is_public, is_ipv4</span></span>  
  
 <span data-ttu-id="0d257-128">**主键：** member_name + network_subnet_IP + network_subnet_prefix_length</span><span class="sxs-lookup"><span data-stu-id="0d257-128">**Primary key:** member_name + network_subnet_IP + network_subnet_prefix_length</span></span>  
  
 [<span data-ttu-id="0d257-129">sys.dm_hadr_instance_node_map</span><span class="sxs-lookup"><span data-stu-id="0d257-129">sys.dm_hadr_instance_node_map</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-instance-node-map-transact-sql)  
 <span data-ttu-id="0d257-130">对于承载加入其 AlwaysOn 可用性组的可用性副本的每个 SQL Server 实例，将返回承载该服务器实例的 Windows Server 故障转移群集 (WSFC) 节点的名称。</span><span class="sxs-lookup"><span data-stu-id="0d257-130">For every instance of SQL Server that hosts an availability replica that is joined to its AlwaysOn availability group, returns the name of the Windows Server Failover Clustering (WSFC) node that hosts the server instance.</span></span> <span data-ttu-id="0d257-131">此动态管理视图具有以下用法：</span><span class="sxs-lookup"><span data-stu-id="0d257-131">This dynamic management view has the following uses:</span></span>  
  
-   <span data-ttu-id="0d257-132">此动态管理视图对于检测包含承载于同一 WSFC 节点上的多个可用性副本的可用性组很有用，这是一个不受支持的配置，如果可用性组的配置不正确，则在进行 FCI 故障转移后可能出现此配置。</span><span class="sxs-lookup"><span data-stu-id="0d257-132">This dynamic management view is useful for detecting an availability group with multiple availability replicas that are hosted on the same WSFC node, which is an unsupported configuration that could occur after an FCI failover if the availability group is incorrectly configured.</span></span>  
  
-   <span data-ttu-id="0d257-133">当多个 SQL Server 实例承载于同一 WSFC 节点上时，资源 DLL 将使用此动态管理视图来确定要连接到的 SQL Server 实例。</span><span class="sxs-lookup"><span data-stu-id="0d257-133">When multiple SQL Server instances are hosted on the same WSFC node, the Resource DLL uses this dynamic management view to determine the instance of SQL Server to connect to.</span></span>  
  
 <span data-ttu-id="0d257-134">**列名：** ag_resource_id、instance_name、node_name</span><span class="sxs-lookup"><span data-stu-id="0d257-134">**Column names:** ag_resource_id, instance_name, node_name</span></span>  
  
 [<span data-ttu-id="0d257-135">sys.dm_hadr_name_id_map</span><span class="sxs-lookup"><span data-stu-id="0d257-135">sys.dm_hadr_name_id_map</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-name-id-map-transact-sql)  
 <span data-ttu-id="0d257-136">显示 AlwaysOn 可用性组的映射，即当前的 SQL Server 实例已联接到三个唯一 ID：一个可用性组 ID、一个 WSFC 资源 ID 和一个 WSFC 组 ID。</span><span class="sxs-lookup"><span data-stu-id="0d257-136">Shows the mapping of AlwaysOn availability groups that the current instance of SQL Server has joined to three unique IDs: an availability group ID, a WSFC resource ID, and a WSFC Group ID.</span></span> <span data-ttu-id="0d257-137">此映射旨在处理重命名 WSFC 资源/组的情形。</span><span class="sxs-lookup"><span data-stu-id="0d257-137">The purpose of this mapping is to handle the scenario in which the WSFC resource/group is renamed.</span></span>  
  
 <span data-ttu-id="0d257-138">**列名：** ag_name、ag_id、ag_resource_id、ag_group_id</span><span class="sxs-lookup"><span data-stu-id="0d257-138">**Column names:** ag_name, ag_id, ag_resource_id, ag_group_id</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0d257-139">另请参阅本主题后面[监视可用性副本](#AvReplicas)部分的 **sys.dm_hadr_availability_replica_cluster_nodes** 和 **sys.dm_hadr_availability_replica_cluster_states** 以及[监视可用性数据库](#AvDbs)部分的 **sys.availability_databases_cluster** 和 **sys.dm_hadr_database_replica_cluster_states**。</span><span class="sxs-lookup"><span data-stu-id="0d257-139">Also see **sys.dm_hadr_availability_replica_cluster_nodes** and **sys.dm_hadr_availability_replica_cluster_states** in the [Monitoring Availability Replicas](#AvReplicas) section and **sys.availability_databases_cluster** and **sys.dm_hadr_database_replica_cluster_states** in the [Monitoring Availability Databases](#AvDbs) section, later in this topic.</span></span>  
  
 <span data-ttu-id="0d257-140">有关 WSFC 群集和的信息 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] ，请参阅[Windows Server 故障转移群集 &#40;WSFC&#41; 与 SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)和[故障转移群集并 AlwaysOn 可用性组 &#40;](failover-clustering-and-always-on-availability-groups-sql-server.md)SQL Server&#41;。</span><span class="sxs-lookup"><span data-stu-id="0d257-140">For information about WSFC clusters and [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], see [Windows Server Failover Clustering &#40;WSFC&#41; with SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md) and [Failover Clustering and AlwaysOn Availability Groups &#40;SQL Server&#41;](failover-clustering-and-always-on-availability-groups-sql-server.md).</span></span>  
  
##  <a name="monitoring-availability-groups"></a><a name="AvGroups"></a> <span data-ttu-id="0d257-141">监视可用性组</span><span class="sxs-lookup"><span data-stu-id="0d257-141">Monitoring Availability Groups</span></span>  
 <span data-ttu-id="0d257-142">若要监视服务器实例为其承载可用性副本的可用性组，请使用以下视图：</span><span class="sxs-lookup"><span data-stu-id="0d257-142">To monitor the availability groups for which the server instance hosts an availability replica, use the following views:</span></span>  
  
 [<span data-ttu-id="0d257-143">sys.availability_groups</span><span class="sxs-lookup"><span data-stu-id="0d257-143">sys.availability_groups</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-groups-transact-sql)  
 <span data-ttu-id="0d257-144">为 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的本地实例承载其可用性副本的每个可用性组返回一行。</span><span class="sxs-lookup"><span data-stu-id="0d257-144">Returns a row for each availability group for which the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] hosts an availability replica.</span></span> <span data-ttu-id="0d257-145">每一行都包含可用性组元数据的缓存的副本。</span><span class="sxs-lookup"><span data-stu-id="0d257-145">Each row contains a cached copy of the availability group metadata.</span></span>  
  
 <span data-ttu-id="0d257-146">**列名：** group_id、name、resource_id、resource_group_id、failure_condition_level、health_check_timeout、automated_backup_preference、automated_backup_preference_desc</span><span class="sxs-lookup"><span data-stu-id="0d257-146">**Column names:** group_id, name, resource_id, resource_group_id, failure_condition_level, health_check_timeout, automated_backup_preference, automated_backup_preference_desc</span></span>  
  
 [<span data-ttu-id="0d257-147">sys.availability_groups_cluster</span><span class="sxs-lookup"><span data-stu-id="0d257-147">sys.availability_groups_cluster</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-groups-cluster-transact-sql)  
 <span data-ttu-id="0d257-148">为 WSFC 群集中的每个可用性组返回一行。</span><span class="sxs-lookup"><span data-stu-id="0d257-148">Returns a row for each availability group in the WSFC cluster.</span></span> <span data-ttu-id="0d257-149">每一行均包含 Windows Server 故障转移群集 (WSFC) 群集中的可用性组元数据。</span><span class="sxs-lookup"><span data-stu-id="0d257-149">Each row contains the availability group metadata from the Windows Server Failover Clustering (WSFC) cluster.</span></span>  
  
 <span data-ttu-id="0d257-150">**列名：** group_id、name、resource_id、resource_group_id、failure_condition_level、health_check_timeout、automated_backup_preference、automated_backup_preference_desc</span><span class="sxs-lookup"><span data-stu-id="0d257-150">**Column names:** group_id, name, resource_id, resource_group_id, failure_condition_level, health_check_timeout, automated_backup_preference, automated_backup_preference_desc</span></span>  
  
 [<span data-ttu-id="0d257-151">sys.dm_hadr_availability_group_states</span><span class="sxs-lookup"><span data-stu-id="0d257-151">sys.dm_hadr_availability_group_states</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-group-states-transact-sql)  
 <span data-ttu-id="0d257-152">为在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]的本地实例上拥有可用性副本的每个可用性组返回一行。</span><span class="sxs-lookup"><span data-stu-id="0d257-152">Returns a row for each availability group that possesses an availability replica on the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0d257-153">每行显示定义给定可用性组的运行状况的状态。</span><span class="sxs-lookup"><span data-stu-id="0d257-153">Each row displays the states that define the health of a given availability group.</span></span>  
  
 <span data-ttu-id="0d257-154">**列名：** group_id、primary_replica、primary_recovery_health、primary_recovery_health_desc、secondary_recovery_health、secondary_recovery_health_desc、synchronization_health、synchronization_health_desc</span><span class="sxs-lookup"><span data-stu-id="0d257-154">**Column names:** group_id, primary_replica, primary_recovery_health, primary_recovery_health_desc, secondary_recovery_health, secondary_recovery_health_desc, synchronization_health, synchronization_health_desc</span></span>  
  
##  <a name="monitoring-availability-replicas"></a><a name="AvReplicas"></a><span data-ttu-id="0d257-155">监视可用性副本</span><span class="sxs-lookup"><span data-stu-id="0d257-155">Monitoring Availability Replicas</span></span>  
 <span data-ttu-id="0d257-156">若要监视可用性副本，请使用以下视图和系统函数：</span><span class="sxs-lookup"><span data-stu-id="0d257-156">To monitor availability replicas, use the following views and system function:</span></span>  
  
 [<span data-ttu-id="0d257-157">sys.availability_replicas</span><span class="sxs-lookup"><span data-stu-id="0d257-157">sys.availability_replicas</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql)  
 <span data-ttu-id="0d257-158">为 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的本地实例承载其可用性副本的每个可用性组中的每个可用性副本返回一行。</span><span class="sxs-lookup"><span data-stu-id="0d257-158">Returns a row for every availability replica in each availability group for which the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] hosts an availability replica.</span></span>  
  
 <span data-ttu-id="0d257-159">**列名：** replica_id、group_id、replica_metadata_id、replica_server_name、owner_sid、endpoint_url、availability_mode、availability_mode_desc、failover_mode、failover_mode_desc、session_timeout、primary_role_allow_connections、primary_role_allow_connections_desc、secondary_role_allow_connections、secondary_role_allow_connections_desc、create_date、modify_date、backup_priority、read_only_routing_url</span><span class="sxs-lookup"><span data-stu-id="0d257-159">**Column names:** replica_id, group_id, replica_metadata_id, replica_server_name, owner_sid, endpoint_url, availability_mode, availability_mode_desc, failover_mode, failover_mode_desc, session_timeout, primary_role_allow_connections, primary_role_allow_connections_desc, secondary_role_allow_connections, secondary_role_allow_connections_desc, create_date, modify_date, backup_priority, read_only_routing_url</span></span>  
  
 [<span data-ttu-id="0d257-160">sys.availability_read_only_routing_lists</span><span class="sxs-lookup"><span data-stu-id="0d257-160">sys.availability_read_only_routing_lists</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-read-only-routing-lists-transact-sql)  
 <span data-ttu-id="0d257-161">为 WSFC 故障转移群集中 AlwaysOn 可用性组的每个可用性副本的只读路由列表返回一行。</span><span class="sxs-lookup"><span data-stu-id="0d257-161">Returns a row for the read only routing list of each availability replica in an AlwaysOn availability group in the WSFC failover cluster.</span></span>  
  
 <span data-ttu-id="0d257-162">**列名：** replica_id、routing_priority、read_only_replica_id</span><span class="sxs-lookup"><span data-stu-id="0d257-162">**Column names:** replica_id, routing_priority, read_only_replica_id</span></span>  
  
 [<span data-ttu-id="0d257-163">sys.dm_hadr_availability_replica_cluster_nodes</span><span class="sxs-lookup"><span data-stu-id="0d257-163">sys.dm_hadr_availability_replica_cluster_nodes</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-cluster-nodes-transact-sql)  
 <span data-ttu-id="0d257-164">为 Windows Server 故障转移群集 (WSFC) 群集中 AlwaysOn 可用性组的每个可用性副本（不论联接状态如何）都返回一行。</span><span class="sxs-lookup"><span data-stu-id="0d257-164">Returns a row for every availability replica (regardless of join state) of the AlwaysOn availability groups in the Windows Server Failover Clustering (WSFC) cluster.</span></span>  
  
 <span data-ttu-id="0d257-165">**列名：** group_name、replica_server_name、node_name</span><span class="sxs-lookup"><span data-stu-id="0d257-165">**Column names:** group_name, replica_server_name, node_name</span></span>  
  
 [<span data-ttu-id="0d257-166">sys.dm_hadr_availability_replica_cluster_states</span><span class="sxs-lookup"><span data-stu-id="0d257-166">sys.dm_hadr_availability_replica_cluster_states</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-cluster-states-transact-sql)  
 <span data-ttu-id="0d257-167">为 Windows Server 故障转移群集 (WSFC) 群集中所有 AlwaysOn 可用性组（不论副本位于何处）的每个副本（不论联接状态如何）都返回一行。</span><span class="sxs-lookup"><span data-stu-id="0d257-167">Returns a row for each replica (regardless of join state) of all AlwaysOn availability groups (regardless of replica location) in the Windows Server Failover Clustering (WSFC) cluster.</span></span>  
  
 <span data-ttu-id="0d257-168">**列名：** replica_id、replica_server_name、group_id、join_state、join_state_desc</span><span class="sxs-lookup"><span data-stu-id="0d257-168">**Column names:** replica_id, replica_server_name, group_id, join_state, join_state_desc</span></span>  
  
 [<span data-ttu-id="0d257-169">sys.dm_hadr_availability_replica_states</span><span class="sxs-lookup"><span data-stu-id="0d257-169">sys.dm_hadr_availability_replica_states</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-states-transact-sql)  
 <span data-ttu-id="0d257-170">返回一行以显示每个本地可用性副本的状态，并为同一可用性组中的每个远程可用性副本返回一行。</span><span class="sxs-lookup"><span data-stu-id="0d257-170">Returns a row showing the state of each local availability replica and a row for each remote availability replica in the same availability group.</span></span>  
  
 <span data-ttu-id="0d257-171">**列名：** replica_id、group_id、is_local、role、role_desc、operational_state、operational_state_desc、connected_state、connected_state_desc、recovery_health、recovery_health_desc、synchronization_health、synchronization_health_desc、last_connect_error_number、last_connect_error_description 和 last_connect_error_timestamp</span><span class="sxs-lookup"><span data-stu-id="0d257-171">**Column names:** replica_id, group_id, is_local, role, role_desc, operational_state, operational_state_desc, connected_state, connected_state_desc, recovery_health, recovery_health_desc, synchronization_health, synchronization_health_desc, last_connect_error_number, last_connect_error_description, and last_connect_error_timestamp</span></span>  
  
 [<span data-ttu-id="0d257-172">sys.fn_hadr_backup_is_preferred_replica</span><span class="sxs-lookup"><span data-stu-id="0d257-172">sys.fn_hadr_backup_is_preferred_replica</span></span>](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql)  
 <span data-ttu-id="0d257-173">确定当前副本是否为首选备份副本。</span><span class="sxs-lookup"><span data-stu-id="0d257-173">Determines whether the current replica is the preferred backup replica.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0d257-174">有关可用性副本的性能计数器（ **SQLServer:Availability Replica**  性能对象）的信息，请参阅 [SQL Server，可用性副本](../../../relational-databases/performance-monitor/sql-server-availability-replica.md)。</span><span class="sxs-lookup"><span data-stu-id="0d257-174">For information about performance counters for availability replicas (the **SQLServer:Availability Replica**  performance object), see [SQL Server, Availability Replica](../../../relational-databases/performance-monitor/sql-server-availability-replica.md).</span></span>  
  
##  <a name="monitoring-availability-databases"></a><a name="AvDbs"></a><span data-ttu-id="0d257-175">监视可用性数据库</span><span class="sxs-lookup"><span data-stu-id="0d257-175">Monitoring Availability Databases</span></span>  
 <span data-ttu-id="0d257-176">若要监视可用性数据库，请使用以下视图：</span><span class="sxs-lookup"><span data-stu-id="0d257-176">To monitor availability databases, use the following views:</span></span>  
  
 [<span data-ttu-id="0d257-177">监视可用性数据库</span><span class="sxs-lookup"><span data-stu-id="0d257-177">sys.availability_databases_cluster</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-databases-cluster-transact-sql)  
 <span data-ttu-id="0d257-178">为 SQL Server 实例上的每个数据库（作为群集中所有 AlwaysOn 可用性组的一部分）包含一行，不论本地副本数据库是否联接到可用性组。</span><span class="sxs-lookup"><span data-stu-id="0d257-178">Contains one row for each database on the instance of SQL Server that are part of all AlwaysOn Availability Groups in the cluster, regardless of whether the local copy database has been joined to the availability group yet.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0d257-179">将数据库添加到可用性组后，主数据库自动联接到该组。</span><span class="sxs-lookup"><span data-stu-id="0d257-179">When a database is added to an availability group, the primary database is automatically joined to the group.</span></span> <span data-ttu-id="0d257-180">必须在每个辅助副本上准备辅助数据库，之后才能将其联接到可用性组。</span><span class="sxs-lookup"><span data-stu-id="0d257-180">Secondary databases must be prepared on each secondary replica before they can be joined to the availability group.</span></span>  
  
 <span data-ttu-id="0d257-181">**列名：** group_id、group_database_id、database_name</span><span class="sxs-lookup"><span data-stu-id="0d257-181">**Column names:** group_id, group_database_id, database_name</span></span>  
  
 [<span data-ttu-id="0d257-182">sys.databases</span><span class="sxs-lookup"><span data-stu-id="0d257-182">sys.databases</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
 <span data-ttu-id="0d257-183">为 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]实例中的每个数据库都包含一行。</span><span class="sxs-lookup"><span data-stu-id="0d257-183">Contains one row per database in the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0d257-184">如果数据库属于某个可用性副本，该数据库对应的行将显示该副本的 GUID，以及该数据库在其可用性组中的唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="0d257-184">If a database belongs to an availability replica, the row for that database displays the GUID of the replica and the unique identifier of the database within its availability group.</span></span>  
  
 <span data-ttu-id="0d257-185">\*\* [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 列名：\*\* replica_id、group_database_id</span><span class="sxs-lookup"><span data-stu-id="0d257-185">**[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] column names:** replica_id, group_database_id</span></span>  
  
 [<span data-ttu-id="0d257-186">sys.dm_hadr_auto_page_repair</span><span class="sxs-lookup"><span data-stu-id="0d257-186">sys.dm_hadr_auto_page_repair</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-auto-page-repair-transact-sql)  
 <span data-ttu-id="0d257-187">为针对任何可用性数据库（位于服务器实例为任何可用性组承载的可用性副本上）的每一个自动页修复尝试都返回一行。</span><span class="sxs-lookup"><span data-stu-id="0d257-187">Returns a row for every automatic page-repair attempt on any availability database on an availability replica that is hosted for any availability group by the server instance.</span></span> <span data-ttu-id="0d257-188">该视图包含对应于给定主/辅助数据库上最新自动页修复尝试的行，每个数据库最多可对应 100 行。</span><span class="sxs-lookup"><span data-stu-id="0d257-188">This view contains rows for the latest automatic page-repair attempts on a given primary or secondary database, with a maximum of 100 rows per database.</span></span> <span data-ttu-id="0d257-189">只要一个数据库对应的行达到最大值，则它的下个自动页修复尝试对应的行将替换现有的一个项。</span><span class="sxs-lookup"><span data-stu-id="0d257-189">As soon as a database reaches the maximum, the row for its next automatic page-repair attempt replaces one of the existing entries.</span></span>  
  
 <span data-ttu-id="0d257-190">**列名：** database_id、file_id、page_id、error_type、page_status、modification_time</span><span class="sxs-lookup"><span data-stu-id="0d257-190">**Column names:** database_id, file_id, page_id, error_type, page_status, modification_time</span></span>  
  
 [<span data-ttu-id="0d257-191">sys.dm_hadr_database_replica_states</span><span class="sxs-lookup"><span data-stu-id="0d257-191">sys.dm_hadr_database_replica_states</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql)  
 <span data-ttu-id="0d257-192">为参与任何可用性组（ [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的本地实例正承载其可用性副本）的每个数据库返回一行。</span><span class="sxs-lookup"><span data-stu-id="0d257-192">Returns a row for each database that is participating in any availability group for which the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is hosting an availability replica.</span></span>  
  
 <span data-ttu-id="0d257-193">**列名：** database_id、group_id、replica_id、group_database_id、is_local、synchronization_state、synchronization_state_desc、is_commit_participant、synchronization_health、synchronization_health_desc、database_state、database_state_desc、is_suspended、suspend_reason、suspend_reason_desc、recovery_lsn、truncation_lsn、last_sent_lsn、last_sent_time、last_received_lsn、last_received_time、last_hardened_lsn、last_hardened_time、last_redone_lsn、last_redone_time、log_send_queue_size、log_send_rate、redo_queue_size、redo_rate、filestream_send_rate、end_of_log_lsn、last_commit_lsn、last_commit_time、low_water_mark_for_ghosts</span><span class="sxs-lookup"><span data-stu-id="0d257-193">**Column names:** database_id, group_id, replica_id, group_database_id, is_local, synchronization_state, synchronization_state_desc, is_commit_participant, synchronization_health, synchronization_health_desc, database_state, database_state_desc, is_suspended, suspend_reason, suspend_reason_desc, recovery_lsn, truncation_lsn, last_sent_lsn, last_sent_time, last_received_lsn, last_received_time, last_hardened_lsn, last_hardened_time, last_redone_lsn, last_redone_time, log_send_queue_size, log_send_rate, redo_queue_size, redo_rate, filestream_send_rate, end_of_log_lsn, last_commit_lsn, last_commit_time, low_water_mark_for_ghosts</span></span>  
  
 [<span data-ttu-id="0d257-194">sys.dm_hadr_database_replica_cluster_states</span><span class="sxs-lookup"><span data-stu-id="0d257-194">sys.dm_hadr_database_replica_cluster_states</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-cluster-states-transact-sql)  
 <span data-ttu-id="0d257-195">返回一行信息，这些信息旨在让您洞察 WSFC 故障转移群集 (WSFC) 群集上每个可用性组中的可用性数据库的运行状况。</span><span class="sxs-lookup"><span data-stu-id="0d257-195">Returns a row containing information intended to provide you with insight into the health of the availability databases in each availability group on the Windows Server Failover Clustering (WSFC) cluster.</span></span> <span data-ttu-id="0d257-196">此动态管理视图适用于以下情况：计划或响应某一故障转移，或发现可用性组中的哪一个辅助副本正在阻止给定主数据库上的日志截断。</span><span class="sxs-lookup"><span data-stu-id="0d257-196">This dynamic management view is useful when planning or responding to a failover or for discovering which secondary replica in an availability group is holding up log truncation on a given primary database.</span></span>  
  
 <span data-ttu-id="0d257-197">**列名：** replica_id、group_database_id、database_name、is_failover_ready、is_pending_secondary_suspend、is_database_joined、recovery_lsn、truncation_lsn</span><span class="sxs-lookup"><span data-stu-id="0d257-197">**Column names:** replica_id, group_database_id, database_name, is_failover_ready, is_pending_secondary_suspend, is_database_joined, recovery_lsn, truncation_lsn</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0d257-198">主副本位置是可用性组的权威来源。</span><span class="sxs-lookup"><span data-stu-id="0d257-198">The primary replica location is the authoritative source for an availability group.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0d257-199">有关可用性数据库的 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 性能计数器（ **SQLServer:Database Replica** 性能对象）的信息，请参阅 [SQL Server，数据库副本](../../../relational-databases/performance-monitor/sql-server-database-replica.md)。</span><span class="sxs-lookup"><span data-stu-id="0d257-199">For information about the [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] performance counters for availability databases (the **SQLServer:Database Replica** performance object), see [SQL Server, Database Replica](../../../relational-databases/performance-monitor/sql-server-database-replica.md).</span></span> <span data-ttu-id="0d257-200">此外，若要监视可用性数据库上的事务日志活动，请使用以下 SQLServer 计数器 **：数据库**性能对象： "**日志刷新写入时间 (ms) **、**日志刷新次数/秒**、**日志池缓存未命中数/秒**、**日志池磁盘读取次数/秒**和**日志池请求数/秒**。有关详细信息，请参阅[SQL Server，数据库对象](../../../relational-databases/performance-monitor/sql-server-databases-object.md)。</span><span class="sxs-lookup"><span data-stu-id="0d257-200">Also, to monitor transaction-log activity on availability databases, use the following counters of the **SQLServer:Databases** performance object: **Log Flush Write Time (ms)**, **Log Flushes/sec**, **Log Pool Cache Misses/sec**, **Log Pool Disk Reads/sec**, and **Log Pool Requests/sec**. For more information, see [SQL Server, Databases Object](../../../relational-databases/performance-monitor/sql-server-databases-object.md).</span></span>  
  
##  <a name="monitoring-availability-group-listeners"></a><a name="AGlisteners"></a> <span data-ttu-id="0d257-201">监视可用性组侦听器</span><span class="sxs-lookup"><span data-stu-id="0d257-201">Monitoring Availability Group Listeners</span></span>  
 <span data-ttu-id="0d257-202">若要监视 WSFC 群集子网上的可用性组侦听器，请使用以下视图：</span><span class="sxs-lookup"><span data-stu-id="0d257-202">To monitor the availability group listeners on subnets of the WSFC cluster, use the following views:</span></span>  
  
 [<span data-ttu-id="0d257-203">sys.availability_group_listener_ip_addresses</span><span class="sxs-lookup"><span data-stu-id="0d257-203">sys.availability_group_listener_ip_addresses</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-group-listener-ip-addresses-transact-sql)  
 <span data-ttu-id="0d257-204">针对可用性组侦听器，为当前联机的每个符合标准的虚拟 IP 地址返回一行。</span><span class="sxs-lookup"><span data-stu-id="0d257-204">Returns a row for every conformant virtual IP address that is currently online for an availability group listener.</span></span>  
  
 <span data-ttu-id="0d257-205">**列名：** listener_id、ip_address、ip_subnet_mask、is_dhcp、network_subnet_ip、network_subnet_prefix_length、network_subnet_ipv4_mask、state、state_desc</span><span class="sxs-lookup"><span data-stu-id="0d257-205">**Column names:** listener_id, ip_address, ip_subnet_mask, is_dhcp, network_subnet_ip, network_subnet_prefix_length, network_subnet_ipv4_mask, state, state_desc</span></span>  
  
 [<span data-ttu-id="0d257-206">sys.availability_group_listeners</span><span class="sxs-lookup"><span data-stu-id="0d257-206">sys.availability_group_listeners</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-group-listeners-transact-sql)  
 <span data-ttu-id="0d257-207">对于给定的可用性组，返回零行（指示没有与该可用性组关联的网络名称），或为 WSFC 群集中的每个可用性组侦听器配置返回一行。</span><span class="sxs-lookup"><span data-stu-id="0d257-207">For a given availability group, returns either zero rows indicating that no network name is associated with the availability group, or returns a row for each availability-group listener configuration in the WSFC cluster.</span></span>  
  
 <span data-ttu-id="0d257-208">**列名：** group_id、listener_id、dns_name、port、is_conformant、ip_configuration_string_from_cluster</span><span class="sxs-lookup"><span data-stu-id="0d257-208">**Column names:** group_id, listener_id, dns_name, port, is_conformant, ip_configuration_string_from_cluster</span></span>  
  
 [<span data-ttu-id="0d257-209">sys.dm_tcp_listener_states</span><span class="sxs-lookup"><span data-stu-id="0d257-209">sys.dm_tcp_listener_states</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-tcp-listener-states-transact-sql)  
 <span data-ttu-id="0d257-210">返回包含各个 TCP 侦听器的动态信息的行。</span><span class="sxs-lookup"><span data-stu-id="0d257-210">Returns a row containing dynamic-state information for each TCP listener.</span></span>  
  
 <span data-ttu-id="0d257-211">**列名：** listener_id、ip_address、is_ipv4、port、type、type_desc、state、state_desc、start_time</span><span class="sxs-lookup"><span data-stu-id="0d257-211">**Column names:** listener_id, ip_address, is_ipv4, port, type, type_desc, state, state_desc, start_time</span></span>  
  
 <span data-ttu-id="0d257-212">**主键：** listener_id</span><span class="sxs-lookup"><span data-stu-id="0d257-212">**Primary key:** listener_id</span></span>  
  
 <span data-ttu-id="0d257-213">有关可用性组侦听程序的信息，请参阅[可用性组侦听程序、客户端连接和应用程序故障转移 (SQL Server)](../../listeners-client-connectivity-application-failover.md)。</span><span class="sxs-lookup"><span data-stu-id="0d257-213">For information about availability group listeners, see [Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="0d257-214">相关任务</span><span class="sxs-lookup"><span data-stu-id="0d257-214">Related Tasks</span></span>  
 <span data-ttu-id="0d257-215">**AlwaysOn 可用性组监视任务：**</span><span class="sxs-lookup"><span data-stu-id="0d257-215">**AlwaysOn Availability Groups monitoring tasks:**</span></span>  
  
-   [<span data-ttu-id="0d257-216">使用对象资源管理器详细信息监视可用性组 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="0d257-216">Use the Object Explorer Details to Monitor Availability Groups &#40;SQL Server Management Studio&#41;</span></span>](use-object-explorer-details-to-monitor-availability-groups.md)  
  
-   [<span data-ttu-id="0d257-217">查看可用性组属性 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0d257-217">View Availability Group Properties &#40;SQL Server&#41;</span></span>](view-availability-group-properties-sql-server.md)  
  
-   [<span data-ttu-id="0d257-218">查看可用性副本属性 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0d257-218">View Availability Replica Properties &#40;SQL Server&#41;</span></span>](view-availability-replica-properties-sql-server.md)  
  
-   [<span data-ttu-id="0d257-219">查看可用性组侦听程序属性 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0d257-219">View Availability Group Listener Properties &#40;SQL Server&#41;</span></span>](view-availability-group-listener-properties-sql-server.md)  
  
 <span data-ttu-id="0d257-220">**AlwaysOn 可用性组监视参考 (Transact-SQL)：**</span><span class="sxs-lookup"><span data-stu-id="0d257-220">**AlwaysOn Availability Groups monitoring reference (Transact-SQL):**</span></span>  
  
-   [<span data-ttu-id="0d257-221">SERVERPROPERTY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0d257-221">SERVERPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/serverproperty-transact-sql)  
  
-   [<span data-ttu-id="0d257-222">sys.availability_group_listener_ip_addresses (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0d257-222">sys.availability_group_listener_ip_addresses &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-group-listener-ip-addresses-transact-sql)  
  
-   [<span data-ttu-id="0d257-223">sys.availability_group_listeners (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0d257-223">sys.availability_group_listeners &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-group-listeners-transact-sql)  
  
-   [<span data-ttu-id="0d257-224">sys.availability_databases_cluster (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0d257-224">sys.availability_databases_cluster &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-databases-cluster-transact-sql)  
  
-   [<span data-ttu-id="0d257-225">sys.availability_groups (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0d257-225">sys.availability_groups &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-groups-transact-sql)  
  
-   [<span data-ttu-id="0d257-226">sys.availability_read_only_routing_lists (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0d257-226">sys.availability_read_only_routing_lists &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-read-only-routing-lists-transact-sql)  
  
-   [<span data-ttu-id="0d257-227">sys.availability_replicas (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0d257-227">sys.availability_replicas &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql)  
  
-   [<span data-ttu-id="0d257-228">sys.dm_hadr_availability_replica_cluster_nodes (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0d257-228">sys.dm_hadr_availability_replica_cluster_nodes &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-cluster-nodes-transact-sql)  
  
-   [<span data-ttu-id="0d257-229">sys.dm_hadr_availability_replica_cluster_states (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0d257-229">sys.dm_hadr_availability_replica_cluster_states &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-cluster-states-transact-sql)  
  
-   [<span data-ttu-id="0d257-230">sys.database_mirroring_endpoints (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0d257-230">sys.database_mirroring_endpoints &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)  
  
-   [<span data-ttu-id="0d257-231">sys.dm_hadr_auto_page_repair (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0d257-231">sys.dm_hadr_auto_page_repair &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-auto-page-repair-transact-sql)  
  
-   [<span data-ttu-id="0d257-232">sys.dm_hadr_availability_group_states (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0d257-232">sys.dm_hadr_availability_group_states &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-group-states-transact-sql)  
  
-   [<span data-ttu-id="0d257-233">sys.dm_hadr_availability_replica_cluster_states (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0d257-233">sys.dm_hadr_availability_replica_cluster_states &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-cluster-states-transact-sql)  
  
-   [<span data-ttu-id="0d257-234">sys.dm_hadr_availability_replica_states (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0d257-234">sys.dm_hadr_availability_replica_states &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-states-transact-sql)  
  
-   [<span data-ttu-id="0d257-235">sys.dm_hadr_database_replica_states (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0d257-235">sys.dm_hadr_database_replica_states &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql)  
  
-   [<span data-ttu-id="0d257-236">sys.dm_hadr_database_replica_cluster_states (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0d257-236">sys.dm_hadr_database_replica_cluster_states &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-cluster-states-transact-sql)  
  
-   [<span data-ttu-id="0d257-237">sys.dm_hadr_cluster (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0d257-237">sys.dm_hadr_cluster &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-transact-sql)  
  
-   [<span data-ttu-id="0d257-238">sys.dm_hadr_cluster_members (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0d257-238">sys.dm_hadr_cluster_members &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-members-transact-sql)  
  
-   [<span data-ttu-id="0d257-239">sys.dm_hadr_cluster_networks (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0d257-239">sys.dm_hadr_cluster_networks &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-networks-transact-sql)  
  
-   [<span data-ttu-id="0d257-240">sys.dm_hadr_database_replica_cluster_states (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0d257-240">sys.dm_hadr_database_replica_cluster_states &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-cluster-states-transact-sql)  
  
-   [<span data-ttu-id="0d257-241">sys.dm_hadr_database_replica_states (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0d257-241">sys.dm_hadr_database_replica_states &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql)  
  
-   [<span data-ttu-id="0d257-242">sys.dm_hadr_instance_node_map (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0d257-242">sys.dm_hadr_instance_node_map &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-instance-node-map-transact-sql)  
  
-   [<span data-ttu-id="0d257-243">sys.dm_hadr_name_id_map (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0d257-243">sys.dm_hadr_name_id_map &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-name-id-map-transact-sql)  
  
-   [<span data-ttu-id="0d257-244">sys.dm_os_performance_counters (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0d257-244">sys.dm_os_performance_counters &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql)  
  
-   [<span data-ttu-id="0d257-245">sys.dm_tcp_listener_states (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0d257-245">sys.dm_tcp_listener_states &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-tcp-listener-states-transact-sql)  
  
-   [<span data-ttu-id="0d257-246">sys.fn_hadr_backup_is_preferred_replica (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0d257-246">sys.fn_hadr_backup_is_preferred_replica  &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql)  
  
 <span data-ttu-id="0d257-247">**AlwaysOn 性能计数器：**</span><span class="sxs-lookup"><span data-stu-id="0d257-247">**AlwaysOn performance counters:**</span></span>  
  
-   [<span data-ttu-id="0d257-248">SQL Server，可用性副本</span><span class="sxs-lookup"><span data-stu-id="0d257-248">SQL Server, Availability Replica</span></span>](../../../relational-databases/performance-monitor/sql-server-availability-replica.md)  
  
-   [<span data-ttu-id="0d257-249">SQL Server - 数据库副本</span><span class="sxs-lookup"><span data-stu-id="0d257-249">SQL Server, Database Replica</span></span>](../../../relational-databases/performance-monitor/sql-server-database-replica.md)  
  
-   [<span data-ttu-id="0d257-250">SQL Server, Databases Object</span><span class="sxs-lookup"><span data-stu-id="0d257-250">SQL Server, Databases Object</span></span>](../../../relational-databases/performance-monitor/sql-server-databases-object.md)  
  
 <span data-ttu-id="0d257-251">**AlwaysOn 可用性组的基于策略的管理**</span><span class="sxs-lookup"><span data-stu-id="0d257-251">**Policy-based management for AlwaysOn Availability Groups**</span></span>  
  
-   [<span data-ttu-id="0d257-252">使用 AlwaysOn 策略查看可用性组的运行状况 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0d257-252">Use AlwaysOn Policies to View the Health of an Availability Group &#40;SQL Server&#41;</span></span>](use-always-on-policies-to-view-the-health-of-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="0d257-253">使用 AlwaysOn 面板 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="0d257-253">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
## <a name="see-also"></a><span data-ttu-id="0d257-254">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0d257-254">See Also</span></span>  
 <span data-ttu-id="0d257-255">[AlwaysOn 可用性组 (SQL Server) ](always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0d257-255">[AlwaysOn Availability Groups (SQL Server)](always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="0d257-256">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0d257-256">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="0d257-257">监视可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0d257-257">Monitoring of Availability Groups &#40;SQL Server&#41;</span></span>](monitoring-of-availability-groups-sql-server.md)  
  
  
