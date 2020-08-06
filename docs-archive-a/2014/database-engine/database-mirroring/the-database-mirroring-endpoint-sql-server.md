---
title: 数据库镜像端点 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], deployment
- database mirroring [SQL Server], endpoint
- endpoints [SQL Server], AlwaysOn Availability Groups
- endpoints [SQL Server], database mirroring
- Availability Groups [SQL Server], endpoint
ms.assetid: 39332dc5-678e-4650-9217-6aa3cdc41635
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5d9728ad642d978378305a21de4b6a9db068c397
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591564"
---
# <a name="the-database-mirroring-endpoint-sql-server"></a><span data-ttu-id="f1ac2-102">数据库镜像端点 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f1ac2-102">The Database Mirroring Endpoint (SQL Server)</span></span>
  <span data-ttu-id="f1ac2-103">若要参与 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] 或数据库镜像，服务器实例需要有自己专用的“数据库镜像端点” 。</span><span class="sxs-lookup"><span data-stu-id="f1ac2-103">To participate in [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] or database mirroring a server instance requires its own, dedicated *database mirroring endpoint*.</span></span> <span data-ttu-id="f1ac2-104">此端点用途特殊，专门用于接收来自其他服务器实例的这些连接。</span><span class="sxs-lookup"><span data-stu-id="f1ac2-104">This endpoint is a special-purpose endpoint that is used exclusively to receive connections from other server instances.</span></span> <span data-ttu-id="f1ac2-105">在某一给定服务器实例上，与任何其他服务器实例的每个 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] 或数据库镜像连接都使用单个数据库镜像端点。</span><span class="sxs-lookup"><span data-stu-id="f1ac2-105">On a given server instance, every [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] or database mirroring connection to any other server instance uses a single database mirroring endpoint.</span></span>  
  
 <span data-ttu-id="f1ac2-106">数据库镜像端点使用传输控制协议 (TCP) 在参与数据库镜像会话或承载可用性副本的服务器实例之间发送和接收消息。</span><span class="sxs-lookup"><span data-stu-id="f1ac2-106">Database mirroring endpoints use Transmission Control Protocol (TCP) to send and receive messages between the server instances participating database mirroring sessions or hosting availability replicas.</span></span> <span data-ttu-id="f1ac2-107">数据库镜像端点在唯一的 TCP 端口号上进行侦听。</span><span class="sxs-lookup"><span data-stu-id="f1ac2-107">The database mirroring endpoint listens on a unique TCP port number.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f1ac2-108">客户端与主体服务器或主副本的连接不使用数据库镜像端点。</span><span class="sxs-lookup"><span data-stu-id="f1ac2-108">Client connections to a principal server or primary replica do not use the database mirroring endpoint.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f1ac2-109">后续版本的 Microsoft SQL Server 将删除数据库镜像功能。</span><span class="sxs-lookup"><span data-stu-id="f1ac2-109">The database mirroring feature will be removed in a future version of Microsoft SQL Server.</span></span> <span data-ttu-id="f1ac2-110">请避免在新的开发工作中使用该功能，并着手修改当前还在使用数据库镜像的应用程序，以便改用 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="f1ac2-110">Avoid using this feature in new development work, and plan to modify applications that currently use database mirroring to use [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] instead.</span></span>  
  
  
##  <a name="server-network-address"></a><a name="ServerNetworkAddress"></a> <span data-ttu-id="f1ac2-111">服务器网络地址</span><span class="sxs-lookup"><span data-stu-id="f1ac2-111">Server Network Address</span></span>  
 <span data-ttu-id="f1ac2-112">服务器实例的网络地址（其“服务器网络地址”或“终结点 URL”）包含其端点的端口号，以及主机的系统名称和域名。</span><span class="sxs-lookup"><span data-stu-id="f1ac2-112">The network address of a server instance (its *server network address* or *Endpoint URL*) contains the port number of its endpoint, as well as the system and domain name of its host computer.</span></span> <span data-ttu-id="f1ac2-113">端口号唯一标识特定的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="f1ac2-113">The port number uniquely identifies a specific server instance.</span></span>  
  
 <span data-ttu-id="f1ac2-114">下图具体说明了如何将同一服务器上的两个服务器实例进行唯一标识。</span><span class="sxs-lookup"><span data-stu-id="f1ac2-114">The following figure illustrates how two server instances on the same server are uniquely identified.</span></span> <span data-ttu-id="f1ac2-115">两个服务器实例的服务器网络地址均包含相同的系统名称 `MYSYSTEM`和域名 `Adventure-Works.MyDomain.com`。</span><span class="sxs-lookup"><span data-stu-id="f1ac2-115">The server network addresses of both server instances contain the same system name, `MYSYSTEM`, and domain name, `Adventure-Works.MyDomain.com`.</span></span> <span data-ttu-id="f1ac2-116">若要使系统能够路由到服务器实例的连接，服务器网络地址需要包括与特定服务器实例的镜像端点相关联的端口号。</span><span class="sxs-lookup"><span data-stu-id="f1ac2-116">To enable the system to route connections to a server instance, a server network address includes the port number associated with the mirroring endpoint of a particular server instance.</span></span>  
  
 <span data-ttu-id="f1ac2-117">![默认实例的服务器网络地址](../media/dbm-2-instances-ports-1-system.gif "默认实例的服务器网络地址")</span><span class="sxs-lookup"><span data-stu-id="f1ac2-117">![Server network addresses of a default instance](../media/dbm-2-instances-ports-1-system.gif "Server network addresses of a default instance")</span></span>  
  
 <span data-ttu-id="f1ac2-118">默认情况下， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例不包含数据库镜像端点。</span><span class="sxs-lookup"><span data-stu-id="f1ac2-118">By default, an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not contain a database mirroring endpoint.</span></span> <span data-ttu-id="f1ac2-119">在建立数据库镜像会话时，必须手动创建它们。</span><span class="sxs-lookup"><span data-stu-id="f1ac2-119">These must be created manually as part of setting up a database mirroring session.</span></span> <span data-ttu-id="f1ac2-120">系统管理员必须在将要参与数据库镜像的每个服务器实例中分别创建端点。</span><span class="sxs-lookup"><span data-stu-id="f1ac2-120">The system administrator must create a separate endpoint in each server instance that is to participate in database mirroring.</span></span> <span data-ttu-id="f1ac2-121">请注意，如果某一给定计算机上的多个服务器实例要求数据库镜像端点，则为每个端点都指定不同的端口号。</span><span class="sxs-lookup"><span data-stu-id="f1ac2-121">Note that if more than one server instance on a given computer requires a database mirroring endpoint, specify a different port number for each endpoint.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f1ac2-122">如果运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的计算机具有防火墙，则防火墙配置必须允许端点中指定的端口的传入和发送连接。</span><span class="sxs-lookup"><span data-stu-id="f1ac2-122">If the computer running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has a firewall, the firewall configuration must allow both incoming and outgoing connections for the port specified in the endpoint.</span></span>  
  
 <span data-ttu-id="f1ac2-123">对于数据库镜像和 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]，身份验证和加密在端点配置。</span><span class="sxs-lookup"><span data-stu-id="f1ac2-123">For database mirroring and [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], authentication and encryption are configured on the endpoint.</span></span> <span data-ttu-id="f1ac2-124">有关详细信息，请参阅[数据库镜像的传输安全性和 AlwaysOn 可用性组 &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md)。</span><span class="sxs-lookup"><span data-stu-id="f1ac2-124">For more information, see [Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f1ac2-125">请勿重新配置正在使用的数据库镜像端点。</span><span class="sxs-lookup"><span data-stu-id="f1ac2-125">Do not reconfigure an in-use database mirroring endpoint.</span></span> <span data-ttu-id="f1ac2-126">服务器实例使用彼此的端点来了解其他系统的状态。</span><span class="sxs-lookup"><span data-stu-id="f1ac2-126">The server instances use each other's endpoints to learn the state of the other systems.</span></span> <span data-ttu-id="f1ac2-127">如果重新配置端点，则可能会重新启动此端点，从而导致其他服务器实例出现错误。</span><span class="sxs-lookup"><span data-stu-id="f1ac2-127">If the endpoint is reconfigured, it might restart, which can appear to be an error to the other server instances.</span></span> <span data-ttu-id="f1ac2-128">这对于自动故障转移模式尤为重要，在此模式下，在伙伴上重新配置端点可能会导致故障转移。</span><span class="sxs-lookup"><span data-stu-id="f1ac2-128">This is particularly important for automatic failover mode, in which reconfiguring the endpoint on a partner could cause a failover to occur.</span></span>  
  
  
##  <a name="determining-the-authentication-type-for-a-database-mirroring-endpoint"></a><a name="EndpointAuthenticationTypes"></a> <span data-ttu-id="f1ac2-129">为数据库镜像端点确定身份验证类型</span><span class="sxs-lookup"><span data-stu-id="f1ac2-129">Determining the Authentication Type for a Database Mirroring Endpoint</span></span>  
 <span data-ttu-id="f1ac2-130">理解您的服务器实例的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务帐户将确定您可以将何种类型的身份验证用于数据库镜像端点十分重要，下面将阐释这一点：</span><span class="sxs-lookup"><span data-stu-id="f1ac2-130">It is important to understand that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service accounts of your server instances determine what type of authentication you can use for your database mirroring endpoints, as follows:</span></span>  
  
-   <span data-ttu-id="f1ac2-131">如果每个服务器实例都在某一域服务帐户下运行，则您可以将 Windows 身份验证用于您的数据库镜像端点。</span><span class="sxs-lookup"><span data-stu-id="f1ac2-131">If every server instance is running under a domain service account, you can use Windows Authentication for your database mirroring endpoints.</span></span> <span data-ttu-id="f1ac2-132">如果所有服务器实例使用相同的域用户帐户运行，则正确的用户登录名将自动存在于全部两个 **master** 数据库中。</span><span class="sxs-lookup"><span data-stu-id="f1ac2-132">If all the server instances run as the same domain user account, the correct user logins exist automatically in both **master** databases.</span></span> <span data-ttu-id="f1ac2-133">这样可简化可用性数据库的安全配置并建议这样做。</span><span class="sxs-lookup"><span data-stu-id="f1ac2-133">This simplifies the security configuration for the availability databases and is recommended.</span></span>  
  
     <span data-ttu-id="f1ac2-134">如果为某一可用性组托管可用性副本的任何服务器实例以不同的帐户身份运行，则必须在其他服务器实例上的 **master** 中创建每个登录帐户。</span><span class="sxs-lookup"><span data-stu-id="f1ac2-134">If any server instances that are hosting the availability replicas for an availability group run as different accounts, the login each account must be created in **master** on the other server instance.</span></span> <span data-ttu-id="f1ac2-135">然后，必须向该登录名授予 CONNECT 权限，以便连接到该服务器实例的数据库镜像端点。</span><span class="sxs-lookup"><span data-stu-id="f1ac2-135">Then, that login must be granted CONNECT permissions to connect to the database mirroring endpoint of that server instance.</span></span> <span data-ttu-id="f1ac2-136">有关详细信息，请[&#40;SQL Server&#41;为数据库镜像或 AlwaysOn 可用性组设置登录帐户](set-up-login-accounts-database-mirroring-always-on-availability.md)。</span><span class="sxs-lookup"><span data-stu-id="f1ac2-136">For more information, [Set Up Login Accounts for Database Mirroring or AlwaysOn Availability Groups &#40;SQL Server&#41;](set-up-login-accounts-database-mirroring-always-on-availability.md).</span></span>  
  
     <span data-ttu-id="f1ac2-137">如果您的服务器实例使用 Windows 身份验证，则您可以通过使用 [!INCLUDE[tsql](../../includes/tsql-md.md)]、PowerShell 或新建可用性组向导创建数据库镜像端点。</span><span class="sxs-lookup"><span data-stu-id="f1ac2-137">If your server instances use Windows Authentication, you can create database mirroring endpoints by using [!INCLUDE[tsql](../../includes/tsql-md.md)], PowerShell, or the New Availability Group Wizard.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f1ac2-138">如果要承载可用性副本的服务器实例缺少数据库镜像端点，则新建可用性组向导可以自动创建使用 Windows 身份验证的数据库镜像端点。</span><span class="sxs-lookup"><span data-stu-id="f1ac2-138">If a server instance that is to host an availability replica lacks a database mirroring endpoint, the New Availability Group Wizard can automatically create a database mirroring endpoint that uses Windows Authentication.</span></span> <span data-ttu-id="f1ac2-139">有关详细信息，请参阅[使用可用性组向导 (SQL Server Management Studio)](../availability-groups/windows/use-the-availability-group-wizard-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="f1ac2-139">For more information, see [Use the Availability Group Wizard &#40;SQL Server Management Studio&#41;](../availability-groups/windows/use-the-availability-group-wizard-sql-server-management-studio.md).</span></span>  
  
-   <span data-ttu-id="f1ac2-140">如果任何服务器实例正在以内置帐户（例如 Local System、Local Service 或 Network Service）或非域帐户运行，则您必须使用证书来进行端点身份验证。</span><span class="sxs-lookup"><span data-stu-id="f1ac2-140">If any server instance is running under a built-in account, such as Local System, Local Service, or Network Service, or a nondomain account, you must use certificates for endpoint authentication.</span></span> <span data-ttu-id="f1ac2-141">如果您正在使用证书来用于您的数据库镜像端点，则您的系统管理员必须配置每个服务器实例，以在出站连接和进站连接中使用证书。</span><span class="sxs-lookup"><span data-stu-id="f1ac2-141">If you are using certificates for your database mirroring endpoints, your system administrator must configure each server instance to use certificates on both outbound and inbound connections.</span></span>  
  
     <span data-ttu-id="f1ac2-142">没有使用证书来配置数据库镜像安全性的任何自动方法。</span><span class="sxs-lookup"><span data-stu-id="f1ac2-142">There is no automated method for configuring database mirroring security using certificates.</span></span> <span data-ttu-id="f1ac2-143">您将需要使用 CREATE ENDPOINT [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句或 `New-SqlHadrEndpoint` PowerShell cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f1ac2-143">You will need to use either CREATE ENDPOINT [!INCLUDE[tsql](../../includes/tsql-md.md)] statement or the `New-SqlHadrEndpoint` PowerShell cmdlet.</span></span> <span data-ttu-id="f1ac2-144">有关详细信息，请参阅 [CREATE ENDPOINT (Transact-SQL)](/sql/t-sql/statements/create-endpoint-transact-sql)的信息。</span><span class="sxs-lookup"><span data-stu-id="f1ac2-144">For more information, see [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql).</span></span> <span data-ttu-id="f1ac2-145">有关在服务器实例上启用证书身份验证的信息，请参阅[将证书用于数据库镜像端点 &#40;transact-sql&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="f1ac2-145">For information about enabling certificate authentication on a server instance, see [Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md).</span></span>  
  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="f1ac2-146">相关任务</span><span class="sxs-lookup"><span data-stu-id="f1ac2-146">Related Tasks</span></span>  

### <a name="to-configure-a-database-mirroring-endpoint"></a><span data-ttu-id="f1ac2-147">配置数据库镜像端点</span><span class="sxs-lookup"><span data-stu-id="f1ac2-147">To Configure a Database Mirroring Endpoint</span></span>
  
-   [<span data-ttu-id="f1ac2-148">为 Windows 身份验证创建数据库镜像终结点 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f1ac2-148">Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;</span></span>](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [<span data-ttu-id="f1ac2-149">使用数据库镜像终结点证书 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f1ac2-149">Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;</span></span>](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
    -   [<span data-ttu-id="f1ac2-150">允许数据库镜像终结点使用证书进行出站连接 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f1ac2-150">Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;</span></span>](database-mirroring-use-certificates-for-outbound-connections.md)  
  
    -   [<span data-ttu-id="f1ac2-151">允许数据库镜像终结点将证书用于入站连接 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f1ac2-151">Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;</span></span>](database-mirroring-use-certificates-for-inbound-connections.md)  
  
-   [<span data-ttu-id="f1ac2-152">指定服务器网络地址（数据库镜像）</span><span class="sxs-lookup"><span data-stu-id="f1ac2-152">Specify a Server Network Address &#40;Database Mirroring&#41;</span></span>](specify-a-server-network-address-database-mirroring.md)  
  
-   [<span data-ttu-id="f1ac2-153">在添加或修改可用性副本时指定终结点 URL (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f1ac2-153">Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;</span></span>](../availability-groups/windows/specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
-   [<span data-ttu-id="f1ac2-154">使用可用性组向导 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="f1ac2-154">Use the Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](../../ssms/sql-server-management-studio-ssms.md)  
  
 <span data-ttu-id="f1ac2-155">**查看有关数据库镜像端点的信息**</span><span class="sxs-lookup"><span data-stu-id="f1ac2-155">**To View Information About the Database Mirroring Endpoint**</span></span>  
  
-   [<span data-ttu-id="f1ac2-156">sys.database_mirroring_endpoints (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f1ac2-156">sys.database_mirroring_endpoints &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)  
  
  
## <a name="see-also"></a><span data-ttu-id="f1ac2-157">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f1ac2-157">See Also</span></span>  
 <span data-ttu-id="f1ac2-158">[用于数据库镜像和 AlwaysOn 可用性组 &#40;SQL Server 的传输安全&#41;](transport-security-database-mirroring-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="f1ac2-158">[Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md) </span></span>  
 <span data-ttu-id="f1ac2-159">[数据库镜像配置故障排除 (SQL Server)](troubleshoot-database-mirroring-configuration-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f1ac2-159">[Troubleshoot Database Mirroring Configuration &#40;SQL Server&#41;](troubleshoot-database-mirroring-configuration-sql-server.md) </span></span>  
 <span data-ttu-id="f1ac2-160">[sys. dm_hadr_availability_replica_states &#40;Transact-sql&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-states-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f1ac2-160">[sys.dm_hadr_availability_replica_states &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-states-transact-sql) </span></span>  
 [<span data-ttu-id="f1ac2-161">sys.dm_db_mirroring_connections (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f1ac2-161">sys.dm_db_mirroring_connections &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/database-mirroring-sys-dm-db-mirroring-connections)  
