---
title: Service Broker，AlwaysOn 可用性组 (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Service Broker, AlwaysOn Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: 881c20e5-1c99-44eb-b393-09fc5ea0f122
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: da179219363422c4ec242d29be61f35dd1609823
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586983"
---
# <a name="service-broker-with-alwayson-availability-groups-sql-server"></a><span data-ttu-id="6cf1d-102">Service Broker 与 AlwaysOn 可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6cf1d-102">Service Broker with AlwaysOn Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="6cf1d-103">本主题包含有关配置 Service Broker 以便用于 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 中的 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]的信息。</span><span class="sxs-lookup"><span data-stu-id="6cf1d-103">This topic contains information about configuring Service Broker to work with [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="6cf1d-104">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="6cf1d-104">**In This Topic:**</span></span>  
  
-   [<span data-ttu-id="6cf1d-105">可用性组中的服务接收远程消息的要求</span><span class="sxs-lookup"><span data-stu-id="6cf1d-105">Requirements for a Service in an Availability Group to Receive Remote Messages</span></span>](#ReceiveRemoteMessages)  
  
-   [<span data-ttu-id="6cf1d-106">向可用性组中的远程服务发送消息的要求</span><span class="sxs-lookup"><span data-stu-id="6cf1d-106">Requirements for Sending Messages to a Remote Service in an Availability Group</span></span>](#SendRemoteMessages)  
  
##  <a name="requirements-for-a-service-in-an-availability-group-to-receive-remote-messages"></a><a name="ReceiveRemoteMessages"></a> <span data-ttu-id="6cf1d-107">可用性组中的服务接收远程消息的要求</span><span class="sxs-lookup"><span data-stu-id="6cf1d-107">Requirements for a Service in an Availability Group to Receive Remote Messages</span></span>  
  
1.  <span data-ttu-id="6cf1d-108">**确保可用性组拥有侦听器。**</span><span class="sxs-lookup"><span data-stu-id="6cf1d-108">**Ensure that the availability group possesses a listener.**</span></span>  
  
     <span data-ttu-id="6cf1d-109">有关详细信息，请参阅 [创建或配置可用性组侦听程序 (SQL Server)](create-or-configure-an-availability-group-listener-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="6cf1d-109">For more information, see [Create or Configure an Availability Group Listener &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="6cf1d-110">**确保 Service Broker 端点存在并已正确配置。**</span><span class="sxs-lookup"><span data-stu-id="6cf1d-110">**Ensure that the Service Broker endpoint exists and is correctly configured.**</span></span>  
  
     <span data-ttu-id="6cf1d-111">在为可用性组承载可用性副本的每个 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例上，按如下方式配置 Service Broker 端点：</span><span class="sxs-lookup"><span data-stu-id="6cf1d-111">On every instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosts an availability replica for the availability group, configure the Service Broker endpoint, as follows:</span></span>  
  
    -   <span data-ttu-id="6cf1d-112">将 LISTENER_IP 设置为“ALL”。</span><span class="sxs-lookup"><span data-stu-id="6cf1d-112">Set LISTENER_IP to 'ALL'.</span></span> <span data-ttu-id="6cf1d-113">此设置启用绑定到可用性组侦听器的所有有效 IP 地址上的连接。</span><span class="sxs-lookup"><span data-stu-id="6cf1d-113">This setting enables connections on any valid IP address that is bound to the availability group listener.</span></span>  
  
    -   <span data-ttu-id="6cf1d-114">在所有主机服务器实例上，将 Service Broker PORT 设置为同一端口号。</span><span class="sxs-lookup"><span data-stu-id="6cf1d-114">Set the Service Broker PORT to the same port number on all the host server instances.</span></span>  
  
        > [!TIP]  
        >  <span data-ttu-id="6cf1d-115">若要查看给定服务器实例上的 Service Broker 断点的端口号，请查询 [sys.tcp_endpoints](/sql/relational-databases/system-catalog-views/sys-tcp-endpoints-transact-sql) 目录视图的“端口”列，其中 **type_desc** = 'SERVICE_BROKER'。</span><span class="sxs-lookup"><span data-stu-id="6cf1d-115">To view the port number of the Service Broker endpoint on a given server instance, query the **port** column of the [sys.tcp_endpoints](/sql/relational-databases/system-catalog-views/sys-tcp-endpoints-transact-sql) catalog view, where **type_desc** = 'SERVICE_BROKER'.</span></span>  
  
     <span data-ttu-id="6cf1d-116">下面的示例创建经过 Windows 身份验证的 Service Broker 端点，该端点使用默认 Service Broker 端口 (4022) 并侦听所有有效的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="6cf1d-116">The following example creates a Windows authenticated Service Broker endpoint that uses the default Service Broker port (4022) and listens to all valid IP addresses.</span></span>  
  
    ```  
    CREATE ENDPOINT [SSBEndpoint]  
        STATE = STARTED  
        AS TCP  (LISTENER_PORT = 4022, LISTENER_IP = ALL )  
        FOR SERVICE_BROKER (AUTHENTICATION = WINDOWS)  
    ```  
  
     <span data-ttu-id="6cf1d-117">有关详细信息，请参阅 [CREATE ENDPOINT (Transact-SQL)](/sql/t-sql/statements/create-endpoint-transact-sql)的信息。</span><span class="sxs-lookup"><span data-stu-id="6cf1d-117">For more information, see [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql).</span></span>  
  
3.  <span data-ttu-id="6cf1d-118">**授予针对端点的 CONNECT 权限。**</span><span class="sxs-lookup"><span data-stu-id="6cf1d-118">**Grant CONNECT permission on the endpoint.**</span></span>  
  
     <span data-ttu-id="6cf1d-119">向 PUBLIC 或某个登录名授予 Service Broker 端点的 CONNECT 权限。</span><span class="sxs-lookup"><span data-stu-id="6cf1d-119">Grant CONNECT permission on the Service Broker endpoint either to PUBLIC or to a login.</span></span>  
  
     <span data-ttu-id="6cf1d-120">下面的示例向 PUBLIC 授予名为 `broker_endpoint` 的 Service Broker 端点的连接权限。</span><span class="sxs-lookup"><span data-stu-id="6cf1d-120">The following example grants the connection on a Service Broker endpoint named `broker_endpoint` to PUBLIC.</span></span>  
  
    ```  
    GRANT CONNECT ON ENDPOINT::[broker_endpoint] TO [PUBLIC]  
    ```  
  
     <span data-ttu-id="6cf1d-121">有关详细信息，请参阅 [GRANT (Transact-SQL)](/sql/t-sql/statements/grant-transact-sql)的信息。</span><span class="sxs-lookup"><span data-stu-id="6cf1d-121">For more information, see [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql).</span></span>  
  
4.  <span data-ttu-id="6cf1d-122">**确保 msdb 包含 AutoCreatedLocal 路由或指向特定服务的路由。**</span><span class="sxs-lookup"><span data-stu-id="6cf1d-122">**Ensure that msdb contains either an AutoCreatedLocal route or a route to the specific service.**</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6cf1d-123">默认情况下，每个用户数据库（包括 **msdb**）都包含路由 **AutoCreatedLocal**。</span><span class="sxs-lookup"><span data-stu-id="6cf1d-123">By default, each user database, including **msdb**, contains the route **AutoCreatedLocal**.</span></span> <span data-ttu-id="6cf1d-124">此路由匹配任何的服务名称和 Broker 实例，并指定消息应在当前实例中传递。</span><span class="sxs-lookup"><span data-stu-id="6cf1d-124">This route matches any service name and broker instance and specifies that the message should be delivered within the current instance.</span></span> <span data-ttu-id="6cf1d-125">相比显式指定与远程实例通信的特定服务的路由，**AutoCreatedLocal** 的优先级较低。</span><span class="sxs-lookup"><span data-stu-id="6cf1d-125">**AutoCreatedLocal** has lower priority than routes that explicitly specify a specific service that communicates with a remote instance.</span></span>  
  
     <span data-ttu-id="6cf1d-126">有关创建路由的信息，请参阅 [Service Broker 路由示例](https://msdn.microsoft.com/library/ms166090\(SQL.105\).aspx) （在 [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] 版的联机丛书中）和 [CREATE ROUTE (Transact SQL)](/sql/t-sql/statements/create-route-transact-sql)的信息。</span><span class="sxs-lookup"><span data-stu-id="6cf1d-126">For information about creating routes, see [Service Broker Routing Examples](https://msdn.microsoft.com/library/ms166090\(SQL.105\).aspx) (in the [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] version of Books Online) and [CREATE ROUTE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-route-transact-sql).</span></span>  
  
##  <a name="requirements-for-sending-messages-to-a-remote-service-in-an-availability-group"></a><a name="SendRemoteMessages"></a> <span data-ttu-id="6cf1d-127">向可用性组中的远程服务发送消息的要求</span><span class="sxs-lookup"><span data-stu-id="6cf1d-127">Requirements for Sending Messages to a Remote Service in an Availability Group</span></span>  
  
1.  <span data-ttu-id="6cf1d-128">**创建指向目标服务的路由。**</span><span class="sxs-lookup"><span data-stu-id="6cf1d-128">**Create a route to the target service.**</span></span>  
  
     <span data-ttu-id="6cf1d-129">按如下方式配置路由：</span><span class="sxs-lookup"><span data-stu-id="6cf1d-129">Configure the route as follows:</span></span>  
  
    -   <span data-ttu-id="6cf1d-130">将 ADDRESS 设置为承载服务数据库的可用性组的侦听器 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="6cf1d-130">Set ADDRESS to the listener IP address of availability group that hosts the service database.</span></span>  
  
    -   <span data-ttu-id="6cf1d-131">将 PORT 设置为您在每个远程 SQL Server 实例的 Service Broker 端点中指定的端口。</span><span class="sxs-lookup"><span data-stu-id="6cf1d-131">Set PORT to the port that you specified in the Service Broker endpoint of each of the remote SQL Server instances.</span></span>  
  
     <span data-ttu-id="6cf1d-132">下面的示例为 `RouteToTargetService` 服务创建一个名为 `ISBNLookupRequestService` 的路由。</span><span class="sxs-lookup"><span data-stu-id="6cf1d-132">The following example creates a route named `RouteToTargetService` for the `ISBNLookupRequestService` service.</span></span> <span data-ttu-id="6cf1d-133">该路由的目标为可用性组侦听器 `MyAgListener`，它使用端口 4022。</span><span class="sxs-lookup"><span data-stu-id="6cf1d-133">The route targets the availability group listener, `MyAgListener`, which uses port 4022.</span></span>  
  
    ```  
    CREATE ROUTE [RouteToTargetService] WITH   
    SERVICE_NAME = 'ISBNLookupRequestService',   
    ADDRESS = 'TCP://MyAgListener:4022';  
  
    ```  
  
     <span data-ttu-id="6cf1d-134">有关详细信息，请参阅 [CREATE ROUTE (Transact SQL)](/sql/t-sql/statements/create-route-transact-sql)的信息。</span><span class="sxs-lookup"><span data-stu-id="6cf1d-134">For more information, see [CREATE ROUTE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-route-transact-sql).</span></span>  
  
2.  <span data-ttu-id="6cf1d-135">**确保 msdb 包含 AutoCreatedLocal 路由或指向特定服务的路由。**</span><span class="sxs-lookup"><span data-stu-id="6cf1d-135">**Ensure that msdb contains either an AutoCreatedLocal route or a route to the specific service.**</span></span> <span data-ttu-id="6cf1d-136">（有关详细信息，请参阅本主题前面的 [可用性组中的服务接收远程消息的要求](#ReceiveRemoteMessages)。）</span><span class="sxs-lookup"><span data-stu-id="6cf1d-136">(For more information, see [Requirements for a Service in an Availability Group to Receive Remote Messages](#ReceiveRemoteMessages), earlier in this topic.)</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="6cf1d-137">相关任务</span><span class="sxs-lookup"><span data-stu-id="6cf1d-137">Related Tasks</span></span>  
  
-   [<span data-ttu-id="6cf1d-138">CREATE ENDPOINT (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6cf1d-138">CREATE ENDPOINT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-endpoint-transact-sql)  
  
-   [<span data-ttu-id="6cf1d-139">CREATE ROUTE (Transact SQL)</span><span class="sxs-lookup"><span data-stu-id="6cf1d-139">CREATE ROUTE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-route-transact-sql)  
  
-   [<span data-ttu-id="6cf1d-140">GRANT (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6cf1d-140">GRANT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/grant-transact-sql)  
  
-   <span data-ttu-id="6cf1d-141">[创建或配置可用性组侦听程序 (SQL Server)](create-or-configure-an-availability-group-listener-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="6cf1d-141">[Create or Configure an Availability Group Listener &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md).</span></span>  
  
-   [<span data-ttu-id="6cf1d-142">创建和配置可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6cf1d-142">Creation and Configuration of Availability Groups &#40;SQL Server&#41;</span></span>](creation-and-configuration-of-availability-groups-sql-server.md)  
  
-   [<span data-ttu-id="6cf1d-143">设置用于数据库镜像或 AlwaysOn 可用性组 &#40;SQL Server 的登录帐户&#41;</span><span class="sxs-lookup"><span data-stu-id="6cf1d-143">Set Up Login Accounts for Database Mirroring or AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](../../database-mirroring/set-up-login-accounts-database-mirroring-always-on-availability.md)  
  
## <a name="see-also"></a><span data-ttu-id="6cf1d-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6cf1d-144">See Also</span></span>  
 <span data-ttu-id="6cf1d-145">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6cf1d-145">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="6cf1d-146">[可用性组侦听程序、客户端连接和应用程序故障转移 &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span><span class="sxs-lookup"><span data-stu-id="6cf1d-146">[Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span></span>  
 [<span data-ttu-id="6cf1d-147">SQL Server Service Broker</span><span class="sxs-lookup"><span data-stu-id="6cf1d-147">SQL Server Service Broker</span></span>](../../configure-windows/sql-server-service-broker.md)  
  
  
