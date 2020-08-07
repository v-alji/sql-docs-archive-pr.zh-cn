---
title: 为可用性组配置只读路由 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 10/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- read-only routing
- Availability Groups [SQL Server], readable secondary replicas
- Availability Groups [SQL Server], read-only routing
- readable secondary replicas
- Availability Groups [SQL Server], client connectivity
- Availability Groups [SQL Server], active secondary replicas
ms.assetid: 7bd89ddd-0403-4930-a5eb-3c78718533d4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2d51d1db75caa29814a01fc1f49bfdd49b403c3d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588698"
---
# <a name="configure-read-only-routing-for-an-availability-group-sql-server"></a><span data-ttu-id="1c913-102">为可用性组配置只读路由 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="1c913-102">Configure Read-Only Routing for an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="1c913-103">若要配置 AlwaysOn 可用性组以便在 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]中支持只读路由，您可以使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 或 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="1c913-103">To configure an AlwaysOn availability group to support read-only routing in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], you can use either [!INCLUDE[tsql](../../../includes/tsql-md.md)] or PowerShell.</span></span> <span data-ttu-id="1c913-104">\*\* “只读路由”指的是 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 将符合条件的只读连接请求路由到可用的 AlwaysOn [可读辅助副本](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) （即，配置为在辅助角色下运行时允许只读工作负荷的副本）的能力。</span><span class="sxs-lookup"><span data-stu-id="1c913-104">*Read-only routing* refers to the ability of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to route qualifying read-only connection requests to an available AlwaysOn [readable secondary replica](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) (that is, a replica that is configured to allow read-only workloads when running under the secondary role).</span></span> <span data-ttu-id="1c913-105">为支持只读路由，可用性组必须具备 [可用性组侦听器](../../listeners-client-connectivity-application-failover.md)。</span><span class="sxs-lookup"><span data-stu-id="1c913-105">To support read-only routing, the availability group must possess an [availability group listener](../../listeners-client-connectivity-application-failover.md).</span></span> <span data-ttu-id="1c913-106">只读客户端必须将其连接请求定向到此侦听器，并且客户端的连接字符串必须将应用程序意向指定为“只读”。</span><span class="sxs-lookup"><span data-stu-id="1c913-106">Read-only clients must direct their connection requests to this listener, and the client's connection strings must specify the application intent as "read-only."</span></span> <span data-ttu-id="1c913-107">也就是说，它们必须是 *读意向连接请求*。</span><span class="sxs-lookup"><span data-stu-id="1c913-107">That is, they must be *read-intent connection requests*.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1c913-108">有关如何配置可读次要副本的信息，请参阅 [配置对可用性副本的只读访问 (SQL Server)](configure-read-only-access-on-an-availability-replica-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="1c913-108">For information about how to configure a readable secondary replica, see [Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;](configure-read-only-access-on-an-availability-replica-sql-server.md).</span></span>

> [!NOTE]
>  <span data-ttu-id="1c913-109">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]不支持配置只读路由。</span><span class="sxs-lookup"><span data-stu-id="1c913-109">Configuring read-only routing is not supported by [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1c913-110">开始之前</span><span class="sxs-lookup"><span data-stu-id="1c913-110">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="1c913-111">先决条件</span><span class="sxs-lookup"><span data-stu-id="1c913-111">Prerequisites</span></span>  
  
-   <span data-ttu-id="1c913-112">可用性组必须拥有可用性组侦听器。</span><span class="sxs-lookup"><span data-stu-id="1c913-112">The availability group must possess an availability group listener.</span></span> <span data-ttu-id="1c913-113">有关详细信息，请参阅 [创建或配置可用性组侦听程序 (SQL Server)](create-or-configure-an-availability-group-listener-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="1c913-113">For more information, see [Create or Configure an Availability Group Listener &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md).</span></span>  
  
-   <span data-ttu-id="1c913-114">必须将一个或多个可用性副本配置为接受辅助角色中的只读 (即，为可[读辅助副本](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) (AlwaysOn% 20Availability% 20Groups \)) # A3。</span><span class="sxs-lookup"><span data-stu-id="1c913-114">One or more availability replicas must be configured to accept read-only in the secondary role (that is, to be [readable secondary replicas](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)(AlwaysOn%20Availability%20Groups\).md)).</span></span> <span data-ttu-id="1c913-115">有关详细信息，请参阅 [配置对可用性副本的只读访问 (SQL Server)](configure-read-only-access-on-an-availability-replica-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="1c913-115">For more information, see [Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;](configure-read-only-access-on-an-availability-replica-sql-server.md).</span></span>  
  
-   <span data-ttu-id="1c913-116">您必须连接到承载当前主副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="1c913-116">You must be connected to the server instance that hosts the current primary replica.</span></span>  
  
###  <a name="what-replica-properties-do-you-need-to-configure-to-support-read-only-routing"></a><a name="RORReplicaProperties"></a> <span data-ttu-id="1c913-117">为支持只读路由，您需要配置哪些副本属性？</span><span class="sxs-lookup"><span data-stu-id="1c913-117">What Replica Properties Do you Need to Configure to Support Read-Only Routing?</span></span>  
  
-   <span data-ttu-id="1c913-118">对于要支持只读路由的每个可读次要副本，你需要指定 *只读路由 URL*。</span><span class="sxs-lookup"><span data-stu-id="1c913-118">For each readable secondary replica that is to support read-only routing, you need to specify a *read-only routing URL*.</span></span> <span data-ttu-id="1c913-119">此 URL 仅在本地副本在辅助角色下运行时起作用。</span><span class="sxs-lookup"><span data-stu-id="1c913-119">This URL takes effect only when the local replica is running under the secondary role.</span></span> <span data-ttu-id="1c913-120">必须根据需要在逐个副本的基础上指定只读路由 URL。</span><span class="sxs-lookup"><span data-stu-id="1c913-120">The read-only routing URL must be specified on a replica-by-replica basis, as needed.</span></span> <span data-ttu-id="1c913-121">每个只读路由 URL 都用于将读意向请求路由到一个特定的可读辅助副本。</span><span class="sxs-lookup"><span data-stu-id="1c913-121">Each read-only routing URL is used for routing read-intent connection requests to a specific readable secondary replica.</span></span> <span data-ttu-id="1c913-122">通常，向每个可读辅助副本分配一个只读路由 URL。</span><span class="sxs-lookup"><span data-stu-id="1c913-122">Typically, every readable secondary replica is assigned a read-only routing URL.</span></span>  
  
     <span data-ttu-id="1c913-123">有关计算可用性副本的只读路由 URL 的信息，请参阅 [计算 AlwaysOn 的 read_only_routing_url](https://docs.microsoft.com/archive/blogs/mattn/calculating-read_only_routing_url-for-alwayson)。</span><span class="sxs-lookup"><span data-stu-id="1c913-123">For information about calculating the read-only routing URL for an availability replica, see [Calculating read_only_routing_url for AlwaysOn](https://docs.microsoft.com/archive/blogs/mattn/calculating-read_only_routing_url-for-alwayson).</span></span>  
  
-   <span data-ttu-id="1c913-124">对于要在其作为主要副本时支持只读路由的每个可用性副本，都需要指定一个 *只读路由列表*。</span><span class="sxs-lookup"><span data-stu-id="1c913-124">For each availability replica that you want to support read-only routing when it is the primary replica, you need to specify a *read-only routing list*.</span></span> <span data-ttu-id="1c913-125">一个给定的只读路由列表仅在本地副本在主角色下运行时才起作用。</span><span class="sxs-lookup"><span data-stu-id="1c913-125">A given read-only routing list takes effect only when the local replica is running under the primary role.</span></span> <span data-ttu-id="1c913-126">必须根据需要在逐个副本的基础上指定此列表。</span><span class="sxs-lookup"><span data-stu-id="1c913-126">This list must be specified on a replica-by-replica basis, as needed.</span></span> <span data-ttu-id="1c913-127">通常，每个只读路由列表中将包含各只读路由 URL，并且在列表的末尾具有本地副本的 URL。</span><span class="sxs-lookup"><span data-stu-id="1c913-127">Typically, each read-only routing list would contain every read-only routing URL, with the URL of the local replica at the end of the list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1c913-128">读意向连接请求将被路由到当前主副本的只读路由列表上的第一个可用可读辅助副本。</span><span class="sxs-lookup"><span data-stu-id="1c913-128">Read-intent connection requests are routed to the first available readable secondary on the read-only routing list of the current primary replica.</span></span> <span data-ttu-id="1c913-129">没有负载平衡。</span><span class="sxs-lookup"><span data-stu-id="1c913-129">There is no load balancing.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1c913-130">有关可用性组侦听程序的信息，以及只读路由的详细信息，请参阅 [可用性组侦听程序、客户端连接和应用程序故障转移 (SQL Server)](../../listeners-client-connectivity-application-failover.md)。</span><span class="sxs-lookup"><span data-stu-id="1c913-130">For information about availability group listeners and more information about read-only routing, see [Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1c913-131">Security</span><span class="sxs-lookup"><span data-stu-id="1c913-131">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1c913-132">权限</span><span class="sxs-lookup"><span data-stu-id="1c913-132">Permissions</span></span>  
  
|<span data-ttu-id="1c913-133">任务</span><span class="sxs-lookup"><span data-stu-id="1c913-133">Task</span></span>|<span data-ttu-id="1c913-134">权限</span><span class="sxs-lookup"><span data-stu-id="1c913-134">Permissions</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="1c913-135">在创建可用性组时配置副本</span><span class="sxs-lookup"><span data-stu-id="1c913-135">To configure replicas when creating an availability group</span></span>|<span data-ttu-id="1c913-136">需要 **sysadmin** 固定服务器角色的成员资格，以及 CREATE AVAILABILITY GROUP 服务器权限、ALTER ANY AVAILABILITY GROUP 权限或 CONTROL SERVER 权限。</span><span class="sxs-lookup"><span data-stu-id="1c913-136">Requires membership in the **sysadmin** fixed server role and either CREATE AVAILABILITY GROUP server permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>|  
|<span data-ttu-id="1c913-137">修改可用性副本</span><span class="sxs-lookup"><span data-stu-id="1c913-137">To modify an availability replica</span></span>|<span data-ttu-id="1c913-138">对可用性组要求 ALTER AVAILABILITY GROUP 权限、CONTROL AVAILABILITY GROUP 权限、ALTER ANY AVAILABILITY GROUP 权限或 CONTROL SERVER 权限。</span><span class="sxs-lookup"><span data-stu-id="1c913-138">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>|  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="1c913-139">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1c913-139">Using Transact-SQL</span></span>  
 <span data-ttu-id="1c913-140">**配置只读路由**</span><span class="sxs-lookup"><span data-stu-id="1c913-140">**To Configure read-only routing**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1c913-141">有关代码示例，请参阅本节后面的 [示例 (Transact-SQL)](#TsqlExample)。</span><span class="sxs-lookup"><span data-stu-id="1c913-141">For a code example, see [Example (Transact-SQL)](#TsqlExample), later in this section.</span></span>  
  
1.  <span data-ttu-id="1c913-142">连接到承载主副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="1c913-142">Connect to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="1c913-143">若要指定的是新可用性组的副本，请使用 [CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="1c913-143">If you are specifying a replica for a new availability group, use the [CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="1c913-144">如果要添加或修改现有可用性组的副本，请使用[ALTER AVAILABILITY group](/sql/t-sql/statements/alter-availability-group-transact-sql) [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="1c913-144">If you are adding or modifying a replica for an existing availability group, use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] statement.</span></span>  
  
    -   <span data-ttu-id="1c913-145">若要配置辅助角色的只读路由，请在 ADD REPLICA 或 MODIFY REPLICA WITH 子句中指定 SECONDARY_ROLE 选项，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1c913-145">To configure read-only routing for the secondary role, in the ADD REPLICA or MODIFY REPLICA WITH clause, specify the SECONDARY_ROLE option, as follows:</span></span>  
  
         <span data-ttu-id="1c913-146">SECONDARY_ROLE \*\* (\*\* READ_ONLY_ROUTING_URL **= "** TCP \*\*：// *`system-address`* ： *`port`* " ) \*\*</span><span class="sxs-lookup"><span data-stu-id="1c913-146">SECONDARY_ROLE **(** READ_ONLY_ROUTING_URL **='** TCP **://*`system-address`*:*`port`*')**</span></span>  
  
         <span data-ttu-id="1c913-147">只读路由 URL 的参数如下所示：</span><span class="sxs-lookup"><span data-stu-id="1c913-147">The parameters of the read-only routing URL are as follows:</span></span>  
  
         <span data-ttu-id="1c913-148">*system-address*</span><span class="sxs-lookup"><span data-stu-id="1c913-148">*system-address*</span></span>  
         <span data-ttu-id="1c913-149">一个字符串，例如系统名称、完全限定的域名或 IP 地址，它们明确标识了目标计算机系统。</span><span class="sxs-lookup"><span data-stu-id="1c913-149">Is a string, such as a system name, a fully qualified domain name, or an IP address, that unambiguously identifies the destination computer system.</span></span>  
  
         <span data-ttu-id="1c913-150">*port*</span><span class="sxs-lookup"><span data-stu-id="1c913-150">*port*</span></span>  
         <span data-ttu-id="1c913-151">一个端口号，由 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例的数据库引擎使用。</span><span class="sxs-lookup"><span data-stu-id="1c913-151">Is a port number that is used by the Database Engine of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance.</span></span>  
  
         <span data-ttu-id="1c913-152">例如：   `SECONDARY_ROLE (READ_ONLY_ROUTING_URL = N'TCP://COMPUTER01.contoso.com:1433')`</span><span class="sxs-lookup"><span data-stu-id="1c913-152">For example:   `SECONDARY_ROLE (READ_ONLY_ROUTING_URL = N'TCP://COMPUTER01.contoso.com:1433')`</span></span>  
  
         <span data-ttu-id="1c913-153">如果副本已配置为允许只读连接，则在 MODIFY REPLICA 子句中，ALLOW_CONNECTIONS 是可选的。</span><span class="sxs-lookup"><span data-stu-id="1c913-153">In a MODIFY REPLICA clause the ALLOW_CONNECTIONS is optional if the replica is already configured to allow read-only connections.</span></span>  
  
         <span data-ttu-id="1c913-154">有关详细信息，请参阅 [计算 AlwaysOn 的 read_only_routing_url](https://docs.microsoft.com/archive/blogs/mattn/calculating-read_only_routing_url-for-alwayson)。</span><span class="sxs-lookup"><span data-stu-id="1c913-154">For more information, see [Calculating read_only_routing_url for AlwaysOn](https://docs.microsoft.com/archive/blogs/mattn/calculating-read_only_routing_url-for-alwayson).</span></span>  
  
    -   <span data-ttu-id="1c913-155">若要配置主角色的只读路由，请在 ADD REPLICA 或 MODIFY REPLICA WITH 子句中指定 PRIMARY_ROLE 选项，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1c913-155">To configure read-only routing for the primary role, in the ADD REPLICA or MODIFY REPLICA WITH clause, specify the PRIMARY_ROLE option, as follows:</span></span>  
  
         <span data-ttu-id="1c913-156">PRIMARY_ROLE \*\* (\*\* READ_ONLY_ROUTING_LIST **= ( " *`server`* "** [ **，**.。。*n* ] **) # B3**</span><span class="sxs-lookup"><span data-stu-id="1c913-156">PRIMARY_ROLE **(** READ_ONLY_ROUTING_LIST **=('*`server`*'** [ **,**...*n* ] **))**</span></span>  
  
         <span data-ttu-id="1c913-157">其中， *server* 标识一个托管可用性组中的只读次要副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="1c913-157">where, *server* identifies a server instance that hosts a read-only secondary replica in the availability group.</span></span>  
  
         <span data-ttu-id="1c913-158">例如：   `PRIMARY_ROLE (READ_ONLY_ROUTING_LIST=('Server1','Server2'))`</span><span class="sxs-lookup"><span data-stu-id="1c913-158">For example:   `PRIMARY_ROLE (READ_ONLY_ROUTING_LIST=('Server1','Server2'))`</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="1c913-159">您必须先设置只读路由 URL，然后才能配置只读路由列表。</span><span class="sxs-lookup"><span data-stu-id="1c913-159">You must set the read-only routing URL before configuring the read-only routing list.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="1c913-160">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="1c913-160">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="1c913-161">以下示例将修改现有可用性组 `AG1` 的两个可用性副本以支持只读路由（如果其中一个副本拥有主角色）。</span><span class="sxs-lookup"><span data-stu-id="1c913-161">The following example modifies two availability replicas of an existing availability group, `AG1` to support read-only routing if one of these replicas currently owns the primary role.</span></span> <span data-ttu-id="1c913-162">为了标识承载可用性副本的服务器实例，此示例指定了实例名称 `COMPUTER01` 和 `COMPUTER02`。</span><span class="sxs-lookup"><span data-stu-id="1c913-162">To identify the server instances that host the availability replica, this example specifies the instance names-`COMPUTER01` and `COMPUTER02`.</span></span>  
  
```sql
ALTER AVAILABILITY GROUP [AG1]  
 MODIFY REPLICA ON  
N'COMPUTER01' WITH   
(SECONDARY_ROLE (ALLOW_CONNECTIONS = READ_ONLY));  
ALTER AVAILABILITY GROUP [AG1]  
 MODIFY REPLICA ON  
N'COMPUTER01' WITH   
(SECONDARY_ROLE (READ_ONLY_ROUTING_URL = N'TCP://COMPUTER01.contoso.com:1433'));  
  
ALTER AVAILABILITY GROUP [AG1]  
 MODIFY REPLICA ON  
N'COMPUTER02' WITH   
(SECONDARY_ROLE (ALLOW_CONNECTIONS = READ_ONLY));  
ALTER AVAILABILITY GROUP [AG1]  
 MODIFY REPLICA ON  
N'COMPUTER02' WITH   
(SECONDARY_ROLE (READ_ONLY_ROUTING_URL = N'TCP://COMPUTER02.contoso.com:1433'));  
  
ALTER AVAILABILITY GROUP [AG1]   
MODIFY REPLICA ON  
N'COMPUTER01' WITH   
(PRIMARY_ROLE (READ_ONLY_ROUTING_LIST=('COMPUTER02','COMPUTER01')));  
  
ALTER AVAILABILITY GROUP [AG1]   
MODIFY REPLICA ON  
N'COMPUTER02' WITH   
(PRIMARY_ROLE (READ_ONLY_ROUTING_LIST=('COMPUTER01','COMPUTER02')));  
GO
```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="1c913-163">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="1c913-163">Using PowerShell</span></span>  

### <a name="to-configure-read-only-routing"></a><span data-ttu-id="1c913-164">配置只读路由</span><span class="sxs-lookup"><span data-stu-id="1c913-164">To Configure read-only routing</span></span>
  
> [!NOTE]  
>  <span data-ttu-id="1c913-165">有关代码示例，请参阅本节后面的 [示例 (PowerShell)](#PSExample)。</span><span class="sxs-lookup"><span data-stu-id="1c913-165">For a code example, see [Example (PowerShell)](#PSExample), later in this section.</span></span>  
  
1.  <span data-ttu-id="1c913-166">将默认的 (`cd`) 设置为承载主副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="1c913-166">Set default (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="1c913-167">在将可用性副本添加到可用性组中时，请使用 `New-SqlAvailabilityReplica` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1c913-167">When adding an availability replica to an availability group, use the `New-SqlAvailabilityReplica` cmdlet.</span></span> <span data-ttu-id="1c913-168">在修改现有可用性副本时，请使用 `Set-SqlAvailabilityReplica` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1c913-168">When modifying an existing availability replica, use the `Set-SqlAvailabilityReplica` cmdlet.</span></span> <span data-ttu-id="1c913-169">相关参数如下：</span><span class="sxs-lookup"><span data-stu-id="1c913-169">The relevant parameters are as follows:</span></span>  
  
    -   <span data-ttu-id="1c913-170">若要为辅助角色配置只读路由，请指定**ReadonlyRoutingConnectionUrl " *`url`* "** 参数。</span><span class="sxs-lookup"><span data-stu-id="1c913-170">To configure read-only routing for the secondary role, specify the **ReadonlyRoutingConnectionUrl"*`url`*"** parameter.</span></span>  
  
         <span data-ttu-id="1c913-171">其中， *url* 是当路由到副本时要用于建立只读连接的连接完全限定域名 (FQDN) 和端口。</span><span class="sxs-lookup"><span data-stu-id="1c913-171">where, *url* is the connectivity fully-qualified domain name (FQDN) and port to use when routing to the replica for read-only connections.</span></span> <span data-ttu-id="1c913-172">例如：`-ReadonlyRoutingConnectionUrl "TCP://DBSERVER8.manufacturing.Adventure-Works.com:7024"`</span><span class="sxs-lookup"><span data-stu-id="1c913-172">For example:  `-ReadonlyRoutingConnectionUrl "TCP://DBSERVER8.manufacturing.Adventure-Works.com:7024"`</span></span>  
  
         <span data-ttu-id="1c913-173">有关详细信息，请参阅 [计算 AlwaysOn 的 read_only_routing_url](https://docs.microsoft.com/archive/blogs/mattn/calculating-read_only_routing_url-for-alwayson)。</span><span class="sxs-lookup"><span data-stu-id="1c913-173">For more information, see [Calculating read_only_routing_url for AlwaysOn](https://docs.microsoft.com/archive/blogs/mattn/calculating-read_only_routing_url-for-alwayson).</span></span>  
  
    -   <span data-ttu-id="1c913-174">若要为主要角色配置连接访问，请指定**ReadonlyRoutingList " *`server`* "** [ **，**.。。*n* ]，其中，*服务器*标识一个承载可用性组中的只读次要副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="1c913-174">To configure connection access for the primary role, specify **ReadonlyRoutingList"*`server`*"** [ **,**...*n* ], where *server* identifies a server instance that hosts a read-only secondary replica in the availability group.</span></span> <span data-ttu-id="1c913-175">例如：`-ReadOnlyRoutingList "SecondaryServer","PrimaryServer"`</span><span class="sxs-lookup"><span data-stu-id="1c913-175">For example:  `-ReadOnlyRoutingList "SecondaryServer","PrimaryServer"`</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="1c913-176">您必须先设置副本的只读路由 URL，然后才能为其配置只读路由列表。</span><span class="sxs-lookup"><span data-stu-id="1c913-176">You must set the read-only routing URL of a replica before configuring its read-only routing list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1c913-177">若要查看 cmdlet 的语法，请在 `Get-Help` PowerShell 环境中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1c913-177">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="1c913-178">有关详细信息，请参阅 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="1c913-178">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
<span data-ttu-id="1c913-179">若要设置并使用 SQL Server PowerShell 提供程序，请参阅[SQL Server PowerShell 提供程序](../../../powershell/sql-server-powershell-provider.md)，并[SQL Server PowerShell 获取帮助](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="1c913-179">To set up and use the SQL Server PowerShell provider, see [SQL Server PowerShell Provider](../../../powershell/sql-server-powershell-provider.md) and [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>
  
###  <a name="example-powershell"></a><a name="PSExample"></a> <span data-ttu-id="1c913-180">示例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="1c913-180">Example (PowerShell)</span></span>  
 <span data-ttu-id="1c913-181">以下示例在可用性组中配置主副本和一个辅助副本以进行只读路由。</span><span class="sxs-lookup"><span data-stu-id="1c913-181">The following example configures the primary replica and one secondary replica in an availability group for read-only routing.</span></span> <span data-ttu-id="1c913-182">首先，该示例将向每个副本分配一个只读路由 URL。</span><span class="sxs-lookup"><span data-stu-id="1c913-182">First, the example assigns a read-only routing URL to each replica.</span></span> <span data-ttu-id="1c913-183">然后，在主副本上设置只读路由列表。</span><span class="sxs-lookup"><span data-stu-id="1c913-183">Then it sets the read-only routing list on the primary replica.</span></span> <span data-ttu-id="1c913-184">连接字符串中的设置了“ReadOnly”属性的连接将被重定向到辅助副本。</span><span class="sxs-lookup"><span data-stu-id="1c913-184">Connections with the "ReadOnly" property set in the connection string will be redirected to the secondary replica.</span></span> <span data-ttu-id="1c913-185">如果此辅助副本不可读（由 `ConnectionModeInSecondaryRole` 设置确定），则连接将被定向回主副本。</span><span class="sxs-lookup"><span data-stu-id="1c913-185">If this secondary replica is not readable (as determined by the `ConnectionModeInSecondaryRole` setting), the connection will be directed back to the primary replica.</span></span>  
  
```powershell
Set-Location SQLSERVER:\SQL\PrimaryServer\default\AvailabilityGroups\MyAg  
$primaryReplica = Get-Item "AvailabilityReplicas\PrimaryServer"  
$secondaryReplica = Get-Item "AvailabilityReplicas\SecondaryServer"  
  
Set-SqlAvailabilityReplica -ReadOnlyRoutingConnectionUrl "TCP://PrimaryServer.domain.com:1433" -InputObject $primaryReplica  
Set-SqlAvailabilityReplica -ReadOnlyRoutingConnectionUrl "TCP://SecondaryServer.domain.com:1433" -InputObject $secondaryReplica  
Set-SqlAvailabilityReplica -ReadOnlyRoutingList "SecondaryServer","PrimaryServer" -InputObject $primaryReplica  
```  
  
##  <a name="follow-up-after-configuring-read-only-routing"></a><a name="FollowUp"></a> <span data-ttu-id="1c913-186">跟进：配置只读路由之后</span><span class="sxs-lookup"><span data-stu-id="1c913-186">Follow Up: After Configuring Read-Only Routing</span></span>  
 <span data-ttu-id="1c913-187">在这两种角色中配置当前主副本和可读辅助副本以支持只读路由后，可读辅助副本可接收/读取来自通过可用性组侦听器连接的客户端的读意向连接。</span><span class="sxs-lookup"><span data-stu-id="1c913-187">Once the current primary replica and the readable secondary replicas are configured to support read-only routing in both roles, the readable secondary replicas can receive read read-intent connection requests from clients that connect via the availability group listener.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="1c913-188">使用[Bcp 实用工具](../../../tools/bcp-utility.md)或[sqlcmd 实用工具](../../../tools/sqlcmd-utility.md)时，可以通过指定开关来指定对启用了只读访问权限的任何辅助副本的只读访问 `-K ReadOnly` 。</span><span class="sxs-lookup"><span data-stu-id="1c913-188">When using the [bcp Utility](../../../tools/bcp-utility.md) or [sqlcmd Utility](../../../tools/sqlcmd-utility.md), you can specify read-only access to any secondary replica that is enabled for read-only access by specifying the `-K ReadOnly` switch.</span></span>  
  
###  <a name="requirements-and-recommendations-for-client-connection-strings"></a><a name="ConnStringReqsRecs"></a> <span data-ttu-id="1c913-189">针对客户端连接字符串的要求和建议</span><span class="sxs-lookup"><span data-stu-id="1c913-189">Requirements and Recommendations for Client Connection-Strings</span></span>  
 <span data-ttu-id="1c913-190">对于要使用只读路由的客户端应用程序，其连接字符串必须满足以下要求：</span><span class="sxs-lookup"><span data-stu-id="1c913-190">For a client application to use read-only routing, its connection string must satisfy the following requirements:</span></span>  
  
-   <span data-ttu-id="1c913-191">使用 TCP 协议。</span><span class="sxs-lookup"><span data-stu-id="1c913-191">Use the TCP protocol.</span></span>  
  
-   <span data-ttu-id="1c913-192">将应用程序意向特性/属性设置为只读。</span><span class="sxs-lookup"><span data-stu-id="1c913-192">Set the application intent attribute/property to readonly.</span></span>  
  
-   <span data-ttu-id="1c913-193">引用配置为支持只读路由的可用性组的侦听器。</span><span class="sxs-lookup"><span data-stu-id="1c913-193">Reference the listener of an availability group that is configured to support read-only routing.</span></span>  
  
-   <span data-ttu-id="1c913-194">引用该可用性组中的数据库。</span><span class="sxs-lookup"><span data-stu-id="1c913-194">Reference a database in that availability group.</span></span>  
  
 <span data-ttu-id="1c913-195">此外，建议连接字符串启用多子网故障转移，这将支持每个子网上的每个副本的并行客户端线程。</span><span class="sxs-lookup"><span data-stu-id="1c913-195">In addition, we recommend that connection strings enable multi-subnet failover, which supports a parallel client thread for each replica on each subnet.</span></span> <span data-ttu-id="1c913-196">这将最大程度地减小故障转移后的客户端重新连接时间。</span><span class="sxs-lookup"><span data-stu-id="1c913-196">This minimizes client reconnection time after a failover.</span></span>  
  
 <span data-ttu-id="1c913-197">连接字符串的语法取决于应用程序正在使用的 SQL Server 提供程序。</span><span class="sxs-lookup"><span data-stu-id="1c913-197">The syntax for a connection string depends on the SQL Server provider an application is using.</span></span> <span data-ttu-id="1c913-198">以下用于 SQL Server 的 .NET Framework 数据访问接口 4.0.2 的示例连接字符串说明了使用只读路由时所需的和建议的连接字符串的部分。</span><span class="sxs-lookup"><span data-stu-id="1c913-198">The following example connection string for the .NET Framework Data Provider 4.0.2 for SQL Server illustrates the parts of a connection string that are required and recommended to work for read-only routing.</span></span>  
  
```  
Server=tcp:MyAgListener,1433;Database=Db1;IntegratedSecurity=SSPI;ApplicationIntent=ReadOnly;MultiSubnetFailover=True  
```  
  
 <span data-ttu-id="1c913-199">有关只读应用程序意向和只读路由器详细信息，请参阅 [可用性组侦听程序、客户端连接和应用程序故障转移 (SQL Server)](../../listeners-client-connectivity-application-failover.md)。</span><span class="sxs-lookup"><span data-stu-id="1c913-199">For more information about read-only application intent and read-only routing, see [Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md).</span></span>  
  
### <a name="if-read-only-routing-is-not-working-correctly"></a><span data-ttu-id="1c913-200">如果只读路由未正确工作</span><span class="sxs-lookup"><span data-stu-id="1c913-200">If Read-Only Routing is Not Working Correctly</span></span>  
 <span data-ttu-id="1c913-201">有关解决只读路由配置问题的信息，请参阅 [只读路由未正确工作](troubleshoot-always-on-availability-groups-configuration-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="1c913-201">For information about troubleshooting a read-only routing configuration, see [Read-Only Routing is Not Working Correctly](troubleshoot-always-on-availability-groups-configuration-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="1c913-202">相关任务</span><span class="sxs-lookup"><span data-stu-id="1c913-202">Related Tasks</span></span>  

### <a name="to-view-read-only-routing-configurations"></a><span data-ttu-id="1c913-203">查看只读路由配置</span><span class="sxs-lookup"><span data-stu-id="1c913-203">To view read-only routing configurations</span></span>
  
-   [<span data-ttu-id="1c913-204">sys.availability_read_only_routing_lists (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="1c913-204">sys.availability_read_only_routing_lists &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-read-only-routing-lists-transact-sql)  
  
-   <span data-ttu-id="1c913-205">[sys.availability_replicas (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql)（**read_only_routing_url** 列）</span><span class="sxs-lookup"><span data-stu-id="1c913-205">[sys.availability_replicas &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql) (**read_only_routing_url** column)</span></span>  
  
### <a name="to-configure-client-connection-access"></a><span data-ttu-id="1c913-206">配置客户端连接访问</span><span class="sxs-lookup"><span data-stu-id="1c913-206">To configure client connection access</span></span>
  
-   [<span data-ttu-id="1c913-207">创建或配置可用性组侦听程序 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="1c913-207">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="1c913-208">配置对可用性副本的只读访问 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="1c913-208">Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;</span></span>](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
### <a name="to-use-connection-strings-in-applications"></a><span data-ttu-id="1c913-209">在应用程序中使用连接字符串</span><span class="sxs-lookup"><span data-stu-id="1c913-209">To use connection strings in applications</span></span>
  
-   [<span data-ttu-id="1c913-210">对高可用性、灾难恢复的 SQL Server Native Client 支持</span><span class="sxs-lookup"><span data-stu-id="1c913-210">SQL Server Native Client Support for High Availability, Disaster Recovery</span></span>](../../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)  
  
-   [<span data-ttu-id="1c913-211">将连接字符串关键字用于 SQL Server 本机客户端</span><span class="sxs-lookup"><span data-stu-id="1c913-211">Using Connection String Keywords with SQL Server Native Client</span></span>](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="1c913-212">相关内容</span><span class="sxs-lookup"><span data-stu-id="1c913-212">Related Content</span></span>  
  
-   <span data-ttu-id="1c913-213">**博客：**</span><span class="sxs-lookup"><span data-stu-id="1c913-213">**Blogs:**</span></span>  
  
     [<span data-ttu-id="1c913-214">计算 AlwaysOn 的 read_only_routing_url</span><span class="sxs-lookup"><span data-stu-id="1c913-214">Calculating read_only_routing_url for AlwaysOn</span></span>](https://docs.microsoft.com/archive/blogs/mattn/calculating-read_only_routing_url-for-alwayson)  
  
     [<span data-ttu-id="1c913-215">SQL Server AlwaysOn 团队博客：SQL Server AlwaysOn 官方团队博客</span><span class="sxs-lookup"><span data-stu-id="1c913-215">SQL Server AlwaysOn Team Blogs: The official SQL Server AlwaysOn Team Blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [<span data-ttu-id="1c913-216">CSS SQL Server 工程师博客</span><span class="sxs-lookup"><span data-stu-id="1c913-216">CSS SQL Server Engineers Blogs</span></span>](https://blogs.msdn.com/b/psssql/)  
  
-   <span data-ttu-id="1c913-217">**白皮书：**</span><span class="sxs-lookup"><span data-stu-id="1c913-217">**White papers:**</span></span>  
  
     [<span data-ttu-id="1c913-218">针对 SQL Server 2012 的 Microsoft 白皮书</span><span class="sxs-lookup"><span data-stu-id="1c913-218">Microsoft White Papers for SQL Server 2012</span></span>](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [<span data-ttu-id="1c913-219">SQL Server 客户咨询团队白皮书</span><span class="sxs-lookup"><span data-stu-id="1c913-219">SQL Server Customer Advisory Team Whitepapers</span></span>](http://sqlcat.com/)  
  
## <a name="see-also"></a><span data-ttu-id="1c913-220">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1c913-220">See Also</span></span>  
 <span data-ttu-id="1c913-221">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1c913-221">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="1c913-222">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1c913-222">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="1c913-223">[活动辅助副本：可读辅助副本 (AlwaysOn 可用性组) ](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="1c913-223">[Active Secondaries: Readable Secondary Replicas (AlwaysOn Availability Groups)](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) </span></span>  
 <span data-ttu-id="1c913-224">[关于对可用性副本的客户端连接访问 &#40;SQL Server&#41;](about-client-connection-access-to-availability-replicas-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1c913-224">[About Client Connection Access to Availability Replicas &#40;SQL Server&#41;](about-client-connection-access-to-availability-replicas-sql-server.md) </span></span>  
 [<span data-ttu-id="1c913-225">可用性组侦听程序、客户端连接和应用程序故障转移 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="1c913-225">Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;</span></span>](../../listeners-client-connectivity-application-failover.md)  
