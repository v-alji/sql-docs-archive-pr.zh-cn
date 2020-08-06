---
title: 查看可用性组侦听器属性 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygrouplistenerproperties.general.f1
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
ms.assetid: aca0d016-3228-40b8-bdc3-285ed6d9b280
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ef7fe316394a030350ceb12a0d1b8e2d48ee1d34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577849"
---
# <a name="view-availability-group-listener-properties-sql-server"></a><span data-ttu-id="33570-102">查看可用性组侦听器属性 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="33570-102">View Availability Group Listener Properties (SQL Server)</span></span>
  <span data-ttu-id="33570-103">本主题说明如何使用 *或* 在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 中查看 AlwaysOn 可用性组侦听器 [!INCLUDE[tsql](../../../includes/tsql-md.md)][!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]的属性。</span><span class="sxs-lookup"><span data-stu-id="33570-103">This topic describes how to view the properties of an AlwaysOn *availability group listener* by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
-   <span data-ttu-id="33570-104">**若要查看侦听器属性，可使用：**</span><span class="sxs-lookup"><span data-stu-id="33570-104">**To view listener properties, using:**</span></span>  
  
     [<span data-ttu-id="33570-105">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="33570-105">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="33570-106">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="33570-106">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="33570-107">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="33570-107">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="33570-108">**查看侦听器属性**</span><span class="sxs-lookup"><span data-stu-id="33570-108">**To view listener properties**</span></span>  
  
1.  <span data-ttu-id="33570-109">在对象资源管理器中，连接到服务器实例（其上承载要查看其侦听器的可用性组的任何可用性副本）。</span><span class="sxs-lookup"><span data-stu-id="33570-109">In Object Explorer, connect to a server instance that hosts any availability replica of the availability group whose listener you want to view.</span></span> <span data-ttu-id="33570-110">单击服务器名称以展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="33570-110">Click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="33570-111">依次展开 **“AlwaysOn 高可用性”** 节点和 **“可用性组”** 节点。</span><span class="sxs-lookup"><span data-stu-id="33570-111">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="33570-112">展开可用性组节点，然后展开 **“可用性组侦听器”** 节点。</span><span class="sxs-lookup"><span data-stu-id="33570-112">Expand the node of the availability group, and expand the **Availability Groups Listeners** node.</span></span>  
  
4.  <span data-ttu-id="33570-113">右键单击要查看的侦听器，然后选择“属性”命令。</span><span class="sxs-lookup"><span data-stu-id="33570-113">Right-click the listener that you want to view, and select the **Properties** command.</span></span>  
  
5.  <span data-ttu-id="33570-114">这将打开 **“可用性组侦听器属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="33570-114">This opens the **Availability Group Listener Properties** dialog box.</span></span> <span data-ttu-id="33570-115">有关详细信息，请参阅本主题后面的 [可用性组侦听程序属性（对话框）](#AgListenerPropertiesDialog)。</span><span class="sxs-lookup"><span data-stu-id="33570-115">For more information, see [Availability Group Listener Properties (Dialog Box)](#AgListenerPropertiesDialog), later in this topic.</span></span>  
  
###  <a name="availability-group-listener-properties-dialog-box"></a><a name="AgListenerPropertiesDialog"></a> <span data-ttu-id="33570-116">可用性组侦听程序属性（对话框）</span><span class="sxs-lookup"><span data-stu-id="33570-116">Availability Group Listener Properties (Dialog Box)</span></span>  
 <span data-ttu-id="33570-117">**侦听器 DNS 名称**</span><span class="sxs-lookup"><span data-stu-id="33570-117">**Listener DNS Name**</span></span>  
 <span data-ttu-id="33570-118">可用性组侦听器的网络名称。</span><span class="sxs-lookup"><span data-stu-id="33570-118">The network name of the availability group listener.</span></span>  
  
 <span data-ttu-id="33570-119">端口</span><span class="sxs-lookup"><span data-stu-id="33570-119">**Port**</span></span>  
 <span data-ttu-id="33570-120">该侦听器使用的 TCP 端口。</span><span class="sxs-lookup"><span data-stu-id="33570-120">The TCP port used by this listener.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="33570-121">如果您连接到主副本，则可以使用此字段来修改侦听器的端口号。</span><span class="sxs-lookup"><span data-stu-id="33570-121">If you are connected the primary replica, you can use this field to modify the port number of the listener.</span></span> <span data-ttu-id="33570-122">这要求针对可用性组的 ALTER AVAILABILITY GROUP 权限、CONTROL AVAILABILITY GROUP 权限、ALTER ANY AVAILABILITY GROUP 权限或 CONTROL SERVER 权限。</span><span class="sxs-lookup"><span data-stu-id="33570-122">This requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
 <span data-ttu-id="33570-123">**网络模式**</span><span class="sxs-lookup"><span data-stu-id="33570-123">**Network Mode**</span></span>  
 <span data-ttu-id="33570-124">指示该侦听器使用的 TCP 协议，选择如下一种：</span><span class="sxs-lookup"><span data-stu-id="33570-124">Indicates the TCP protocol used by the listener, one of:</span></span>  
  
 <span data-ttu-id="33570-125">**DHCP**</span><span class="sxs-lookup"><span data-stu-id="33570-125">**DHCP**</span></span>  
 <span data-ttu-id="33570-126">该侦听器使用运行动态主机配置协议 (DHCP) 的服务器分配的动态 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="33570-126">The listener uses an dynamic IP address that is assigned by a server running the Dynamic Host Configuration Protocol (DHCP).</span></span>  
  
 <span data-ttu-id="33570-127">**静态 IP**</span><span class="sxs-lookup"><span data-stu-id="33570-127">**Static IP**</span></span>  
 <span data-ttu-id="33570-128">侦听器使用一个或多个静态 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="33570-128">The listener uses one or more Static IP addresses.</span></span> <span data-ttu-id="33570-129">若要访问不同的子网，可用性组侦听器必须使用静态 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="33570-129">To access the different subnets, an availability group listener must use static IP addresses.</span></span>  
  
 <span data-ttu-id="33570-130">网格显示侦听器侦听的各个子网以及与该子网关联的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="33570-130">The grid displays each of the subnets on which the listener listens and the IP address associated with that subnet.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="33570-131">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="33570-131">Using Transact-SQL</span></span>  
 <span data-ttu-id="33570-132">**查看侦听器属性**</span><span class="sxs-lookup"><span data-stu-id="33570-132">**To view listener properties**</span></span>  
  
 <span data-ttu-id="33570-133">若要监视可用性组侦听器，请使用以下视图：</span><span class="sxs-lookup"><span data-stu-id="33570-133">To monitor the availability group listeners, use the following views:</span></span>  
  
 [<span data-ttu-id="33570-134">sys.availability_group_listener_ip_addresses</span><span class="sxs-lookup"><span data-stu-id="33570-134">sys.availability_group_listener_ip_addresses</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-group-listener-ip-addresses-transact-sql)  
 <span data-ttu-id="33570-135">针对可用性组侦听器，为当前联机的每个符合标准的虚拟 IP 地址返回一行。</span><span class="sxs-lookup"><span data-stu-id="33570-135">Returns a row for every conformant virtual IP address that is currently online for an availability group listener.</span></span>  
  
 <span data-ttu-id="33570-136">**列名：** listener_id、ip_address、ip_subnet_mask、is_dhcp、network_subnet_ip、network_subnet_prefix_length、network_subnet_ipv4_mask、state、state_desc</span><span class="sxs-lookup"><span data-stu-id="33570-136">**Column names:** listener_id, ip_address, ip_subnet_mask, is_dhcp, network_subnet_ip, network_subnet_prefix_length, network_subnet_ipv4_mask, state, state_desc</span></span>  
  
 [<span data-ttu-id="33570-137">sys.availability_group_listeners</span><span class="sxs-lookup"><span data-stu-id="33570-137">sys.availability_group_listeners</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-group-listeners-transact-sql)  
 <span data-ttu-id="33570-138">对于给定的可用性组，返回零行（指示没有与该可用性组关联的网络名称），或为 WSFC 群集中的每个可用性组侦听器配置返回一行。</span><span class="sxs-lookup"><span data-stu-id="33570-138">For a given availability group, returns either zero rows indicating that no network name is associated with the availability group, or returns a row for each availability-group listener configuration in the WSFC cluster.</span></span>  
  
 <span data-ttu-id="33570-139">**列名：** group_id、listener_id、dns_name、port、is_conformant、ip_configuration_string_from_cluster</span><span class="sxs-lookup"><span data-stu-id="33570-139">**Column names:** group_id, listener_id, dns_name, port, is_conformant, ip_configuration_string_from_cluster</span></span>  
  
 [<span data-ttu-id="33570-140">sys.dm_tcp_listener_states</span><span class="sxs-lookup"><span data-stu-id="33570-140">sys.dm_tcp_listener_states</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-tcp-listener-states-transact-sql)  
 <span data-ttu-id="33570-141">返回包含各个 TCP 侦听器的动态信息的行。</span><span class="sxs-lookup"><span data-stu-id="33570-141">Returns a row containing dynamic-state information for each TCP listener.</span></span>  
  
 <span data-ttu-id="33570-142">**列名：** listener_id、ip_address、is_ipv4、port、type、type_desc、state、state_desc、start_time</span><span class="sxs-lookup"><span data-stu-id="33570-142">**Column names:** listener_id, ip_address, is_ipv4, port, type, type_desc, state, state_desc, start_time</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="33570-143">有关使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 监视你的 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 环境的详细信息，请参阅 [监视可用性组 (Transact-SQL)](monitor-availability-groups-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="33570-143">For more information about using [!INCLUDE[tsql](../../../includes/tsql-md.md)] to monitor your [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] environment, see [Monitor Availability Groups &#40;Transact-SQL&#41;](monitor-availability-groups-transact-sql.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="33570-144">相关任务</span><span class="sxs-lookup"><span data-stu-id="33570-144">Related Tasks</span></span>  
  
-   [<span data-ttu-id="33570-145">创建或配置可用性组侦听程序 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="33570-145">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="33570-146">删除可用性组侦听程序 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="33570-146">Remove an Availability Group Listener &#40;SQL Server&#41;</span></span>](remove-an-availability-group-listener-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="33570-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="33570-147">See Also</span></span>  
 <span data-ttu-id="33570-148">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="33570-148">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="33570-149">[可用性组侦听程序、客户端连接和应用程序故障转移 &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span><span class="sxs-lookup"><span data-stu-id="33570-149">[Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span></span>  
 [<span data-ttu-id="33570-150">监视可用性组 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="33570-150">Monitor Availability Groups &#40;Transact-SQL&#41;</span></span>](monitor-availability-groups-transact-sql.md)  
  
  
