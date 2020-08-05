---
title: 数据库镜像配置故障排除 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], deployment
- endpoints [SQL Server], database mirroring
- database mirroring [SQL Server], troubleshooting
- troubleshooting [SQL Server], database mirroring
ms.assetid: 87d3801b-dc52-419e-9316-8b1f1490946c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0dafd98f721bfc2d2d0dd64a9f97689466529407
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580881"
---
# <a name="troubleshoot-database-mirroring-configuration-sql-server"></a><span data-ttu-id="ddf98-102">数据库镜像配置故障排除 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ddf98-102">Troubleshoot Database Mirroring Configuration (SQL Server)</span></span>
  <span data-ttu-id="ddf98-103">本主题提供有关信息以帮助您解决设置数据库镜像会话时遇到的问题。</span><span class="sxs-lookup"><span data-stu-id="ddf98-103">This topic provides information to help you troubleshoot problems in setting up a database mirroring session.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ddf98-104"> 请确保满足所有 [数据库镜像的先决条件](prerequisites-restrictions-and-recommendations-for-database-mirroring.md)。</span><span class="sxs-lookup"><span data-stu-id="ddf98-104">Ensure that you are meeting all the [prerequisites for database mirroring](prerequisites-restrictions-and-recommendations-for-database-mirroring.md).</span></span>  
  
|<span data-ttu-id="ddf98-105">问题</span><span class="sxs-lookup"><span data-stu-id="ddf98-105">Issue</span></span>|<span data-ttu-id="ddf98-106">摘要</span><span class="sxs-lookup"><span data-stu-id="ddf98-106">Summary</span></span>|  
|-----------|-------------|  
|<span data-ttu-id="ddf98-107">错误消息 1418</span><span class="sxs-lookup"><span data-stu-id="ddf98-107">Error Message 1418</span></span>|<span data-ttu-id="ddf98-108">此 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 消息指示无法到达服务器网络地址或该地址不存在，同时建议您确认网络地址名称并重新发出命令。</span><span class="sxs-lookup"><span data-stu-id="ddf98-108">This [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] message indicates that the server network address cannot be reached or does not exist, and it suggests that you verify the network address name and reissue the command.</span></span> <span data-ttu-id="ddf98-109">有关详细信息，请参阅 [MSSQLSERVER_1418](../../relational-databases/errors-events/mssqlserver-1418-database-engine-error.md) 主题。</span><span class="sxs-lookup"><span data-stu-id="ddf98-109">For more information, see the [MSSQLSERVER_1418](../../relational-databases/errors-events/mssqlserver-1418-database-engine-error.md) topic.</span></span>|  
|[<span data-ttu-id="ddf98-110">帐户</span><span class="sxs-lookup"><span data-stu-id="ddf98-110">Accounts</span></span>](#Accounts)|<span data-ttu-id="ddf98-111">介绍了正确配置运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所用的帐户的相关要求。</span><span class="sxs-lookup"><span data-stu-id="ddf98-111">Discusses requirements for correctly configuring the accounts under which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running.</span></span>|  
|[<span data-ttu-id="ddf98-112">端点</span><span class="sxs-lookup"><span data-stu-id="ddf98-112">Endpoints</span></span>](#Endpoints)|<span data-ttu-id="ddf98-113">介绍了正确配置每个服务器实例的数据库镜像端点的要求。</span><span class="sxs-lookup"><span data-stu-id="ddf98-113">Discusses requirements for correctly configuring the database mirroring endpoint of each server instance.</span></span>|  
|[<span data-ttu-id="ddf98-114">SystemAddress</span><span class="sxs-lookup"><span data-stu-id="ddf98-114">SystemAddress</span></span>](#SystemAddress)|<span data-ttu-id="ddf98-115">概述了在数据库镜像配置中指定服务器实例的系统名称的备选方法。</span><span class="sxs-lookup"><span data-stu-id="ddf98-115">Summarizes the alternatives for specifying the system name of a server instance in a database mirroring configuration.</span></span>|  
|[<span data-ttu-id="ddf98-116">网络访问</span><span class="sxs-lookup"><span data-stu-id="ddf98-116">Network access</span></span>](#NetworkAccess)|<span data-ttu-id="ddf98-117">记录了允许每个服务器实例通过 TCP 访问其他一个或多个服务器实例的端口的要求。</span><span class="sxs-lookup"><span data-stu-id="ddf98-117">Documents the requirement that each the server instance be able to access the ports of the other server instance or instances over TCP.</span></span>|  
|[<span data-ttu-id="ddf98-118">镜像数据库准备</span><span class="sxs-lookup"><span data-stu-id="ddf98-118">Mirror database preparation</span></span>](#MirrorDbPrep)|<span data-ttu-id="ddf98-119">概述了准备镜像数据库以开始镜像的要求。</span><span class="sxs-lookup"><span data-stu-id="ddf98-119">Summarizes the requirements for preparing the mirror database to enable mirroring to start.</span></span>|  
|[<span data-ttu-id="ddf98-120">失败的创建文件操作</span><span class="sxs-lookup"><span data-stu-id="ddf98-120">Failed create-file operation</span></span>](#FailedCreateFileOp)|<span data-ttu-id="ddf98-121">说明如何响应失败的创建文件操作。</span><span class="sxs-lookup"><span data-stu-id="ddf98-121">Describes how to respond to a failed create-file operation.</span></span>|  
|[<span data-ttu-id="ddf98-122">使用 Transact-SQL 开始镜像</span><span class="sxs-lookup"><span data-stu-id="ddf98-122">Starting mirroring by Using Transact-SQL</span></span>](#StartDbm)|<span data-ttu-id="ddf98-123">说明 ALTER DATABASE *database_name* SET PARTNER **='***partner_server***'** 语句所需的顺序。</span><span class="sxs-lookup"><span data-stu-id="ddf98-123">Describes the required order for ALTER DATABASE *database_name* SET PARTNER **='***partner_server***'** statements.</span></span>|  
|[<span data-ttu-id="ddf98-124">跨数据库事务</span><span class="sxs-lookup"><span data-stu-id="ddf98-124">Cross-Database Transactions</span></span>](#CrossDbTxns)|<span data-ttu-id="ddf98-125">自动故障转移可能导致自动不正确地解决有疑问的事务。</span><span class="sxs-lookup"><span data-stu-id="ddf98-125">An automatic failover could lead to automatic and possibly incorrect resolution of in-doubt transactions.</span></span> <span data-ttu-id="ddf98-126">因此，数据库镜像不支持跨数据库事务。</span><span class="sxs-lookup"><span data-stu-id="ddf98-126">For this reason database mirroring does not support cross-database transactions.</span></span>|  
  
##  <a name="accounts"></a><a name="Accounts"></a> <span data-ttu-id="ddf98-127">帐户</span><span class="sxs-lookup"><span data-stu-id="ddf98-127">Accounts</span></span>  
 <span data-ttu-id="ddf98-128">必须正确配置运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所用的帐户。</span><span class="sxs-lookup"><span data-stu-id="ddf98-128">The accounts under which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running must be correctly configured.</span></span>  
  
1.  <span data-ttu-id="ddf98-129">帐户是否具有正确的权限？</span><span class="sxs-lookup"><span data-stu-id="ddf98-129">Do the accounts have the correct permissions?</span></span>  
  
    1.  <span data-ttu-id="ddf98-130">如果这些帐户在相同的域帐户中运行，则会减少配置错误的几率。</span><span class="sxs-lookup"><span data-stu-id="ddf98-130">If the accounts are running in the same domain accounts, the chances of misconfiguration are reduced.</span></span>  
  
    2.  <span data-ttu-id="ddf98-131">如果这些帐户在不同的域中运行或不属于域帐户，则必须在其他计算机的 **master** 中创建一个登录帐户，并且必须授予该登录帐户端点的 CONNECT 权限。</span><span class="sxs-lookup"><span data-stu-id="ddf98-131">If the accounts are running in different domains or are not domain accounts, the login of one account must be created in **master** on the other computer, and that login must be granted CONNECT permissions on the endpoint.</span></span> <span data-ttu-id="ddf98-132">有关详细信息，请参阅 [当数据库在其他服务器实例上可用时管理元数据 (SQL Server)](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ddf98-132">For more information, see [Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md).</span></span> <span data-ttu-id="ddf98-133">这包括网络服务帐户。</span><span class="sxs-lookup"><span data-stu-id="ddf98-133">This includes the Network Service account.</span></span>  
  
2.  <span data-ttu-id="ddf98-134">如果使用本地系统帐户将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 作为服务运行，则必须使用证书进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="ddf98-134">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running as a service that is using the local system account, you must use certificates for authentication.</span></span> <span data-ttu-id="ddf98-135">有关详细信息，请参阅[使用数据库镜像终结点证书 (Transact-SQL)](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="ddf98-135">For more information, see [Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md).</span></span>  
  
##  <a name="endpoints"></a><a name="Endpoints"></a> <span data-ttu-id="ddf98-136">Endpoints</span><span class="sxs-lookup"><span data-stu-id="ddf98-136">Endpoints</span></span>  
 <span data-ttu-id="ddf98-137">必须正确配置端点。</span><span class="sxs-lookup"><span data-stu-id="ddf98-137">Endpoints must be correctly configured.</span></span>  
  
1.  <span data-ttu-id="ddf98-138">确保每个服务器实例（主体服务器、镜像服务器和见证服务器，如果有的话）都有数据库镜像端点。</span><span class="sxs-lookup"><span data-stu-id="ddf98-138">Make sure that each server instance (the principal server, mirror server, and witness, if any) has a database mirroring endpoint.</span></span> <span data-ttu-id="ddf98-139">有关详细信息，请参阅 [sys.database_mirroring_endpoints (Transact SQL)](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)，并根据身份验证的形式，参阅[为 Windows 身份验证创建数据库镜像终结点 (Transact SQL)](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)或 [使用数据库镜像终结点证书 (Transact SQ)](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="ddf98-139">For more information, see [sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql) and, depending on the form of authentication, either [Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md) or [Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md).</span></span>  
  
2.  <span data-ttu-id="ddf98-140">检查端口号是否正确。</span><span class="sxs-lookup"><span data-stu-id="ddf98-140">Check that the port numbers are correct.</span></span>  
  
     <span data-ttu-id="ddf98-141">若要标识当前与服务器实例的数据库镜像终结点关联的端口，请使用 [sys.database_mirroring_endpoints](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql) 和 [sys.tcp_endpoints](/sql/relational-databases/system-catalog-views/sys-tcp-endpoints-transact-sql) 目录视图。</span><span class="sxs-lookup"><span data-stu-id="ddf98-141">To identify the port currently associated with database mirroring endpoint of a server instance, use the [sys.database_mirroring_endpoints](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql) and [sys.tcp_endpoints](/sql/relational-databases/system-catalog-views/sys-tcp-endpoints-transact-sql) catalog views.</span></span>  
  
3.  <span data-ttu-id="ddf98-142">对于难以解释的数据库镜像设置问题，建议您检查每个服务器实例以确定它是否正在侦听相应的端口。</span><span class="sxs-lookup"><span data-stu-id="ddf98-142">For database mirroring setup issues that are difficult to explain, we recommend that you inspect each server instance to determine whether it is listening on the correct ports.</span></span> <span data-ttu-id="ddf98-143">有关验证端口可用性的信息，请参阅 [MSSQLSERVER_1418](../../relational-databases/errors-events/mssqlserver-1418-database-engine-error.md)。</span><span class="sxs-lookup"><span data-stu-id="ddf98-143">For information about verifying port availability, see [MSSQLSERVER_1418](../../relational-databases/errors-events/mssqlserver-1418-database-engine-error.md).</span></span>  
  
4.  <span data-ttu-id="ddf98-144">确保已启动端点 (STATE = STARTED)。</span><span class="sxs-lookup"><span data-stu-id="ddf98-144">Make sure that the endpoints are started (STATE=STARTED).</span></span> <span data-ttu-id="ddf98-145">对于各个服务器实例，使用以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="ddf98-145">On each server instance, use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
    ```  
    SELECT state_desc FROM sys.database_mirroring_endpoints  
    ```  
  
     <span data-ttu-id="ddf98-146">有关 **state_desc** 列的详细信息，请参阅 [sys.database_mirroring_endpoints (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ddf98-146">For more information about the **state_desc** column, see [sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql).</span></span>  
  
     <span data-ttu-id="ddf98-147">若要启动端点，请使用以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="ddf98-147">To start an endpoint, use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
    ```  
    ALTER ENDPOINT Endpoint_Mirroring   
    STATE = STARTED   
    AS TCP (LISTENER_PORT = <port_number>)  
    FOR database_mirroring (ROLE = ALL);  
    GO  
    ```  
  
     <span data-ttu-id="ddf98-148">有关详细信息，请参阅 [ALTER ENDPOINT (Transact-SQL)](/sql/t-sql/statements/alter-endpoint-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ddf98-148">For more information, see [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql).</span></span>  
  
5.  <span data-ttu-id="ddf98-149">检查 ROLE 是否正确。</span><span class="sxs-lookup"><span data-stu-id="ddf98-149">Check that the ROLE is correct.</span></span> <span data-ttu-id="ddf98-150">对每个服务器实例使用以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="ddf98-150">On each server instance use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
    ```  
    SELECT role FROM sys.database_mirroring_endpoints;  
    GO  
    ```  
  
     <span data-ttu-id="ddf98-151">有关详细信息，请参阅 [sys.database_mirroring_endpoints (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ddf98-151">For more information, see [sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql).</span></span>  
  
6.  <span data-ttu-id="ddf98-152">从其他服务器实例的服务帐户登录需要 CONNECT 权限。</span><span class="sxs-lookup"><span data-stu-id="ddf98-152">The login for the service account from the other server instance requires CONNECT permission.</span></span> <span data-ttu-id="ddf98-153">确保其他服务器的登录帐户具有 CONNECT 权限。</span><span class="sxs-lookup"><span data-stu-id="ddf98-153">Make sure that the login from the other server has CONNECT permission.</span></span> <span data-ttu-id="ddf98-154">若要确定哪个登录帐户拥有对端点的 CONNECT 权限，请对每个服务器实例使用以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="ddf98-154">To determine who has CONNECT permission for an endpoint, on each server instance use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
    ```  
    SELECT 'Metadata Check';  
    SELECT EP.name, SP.STATE,   
       CONVERT(nvarchar(38), suser_name(SP.grantor_principal_id))   
          AS GRANTOR,   
       SP.TYPE AS PERMISSION,  
       CONVERT(nvarchar(46),suser_name(SP.grantee_principal_id))   
          AS GRANTEE   
       FROM sys.server_permissions SP , sys.endpoints EP  
       WHERE SP.major_id = EP.endpoint_id  
       ORDER BY Permission,grantor, grantee;   
    GO  
  
    ```  
  
##  <a name="system-address"></a><a name="SystemAddress"></a> <span data-ttu-id="ddf98-155">系统地址</span><span class="sxs-lookup"><span data-stu-id="ddf98-155">System Address</span></span>  
 <span data-ttu-id="ddf98-156">对于数据库镜像配置中服务器实例的系统名称，可以使用明确标识系统的任何名称。</span><span class="sxs-lookup"><span data-stu-id="ddf98-156">For the system name of a server instance in a database mirroring configuration, you can use any name that unambiguously identifies the system.</span></span> <span data-ttu-id="ddf98-157">服务器地址可以是系统名称（如果各系统都在同一个域中）、完全限定域名或 IP 地址（最好是静态 IP 地址）。</span><span class="sxs-lookup"><span data-stu-id="ddf98-157">The server address can be a system name (if the systems are in the same domain), a fully qualified domain name, or an IP address (preferably, a static IP address).</span></span> <span data-ttu-id="ddf98-158">保证使用完全限定域名的有效性。</span><span class="sxs-lookup"><span data-stu-id="ddf98-158">Using the fully qualified domain name is guaranteed to work.</span></span> <span data-ttu-id="ddf98-159">有关详细信息，请参阅 [指定服务器网络地址（数据库镜像）](specify-a-server-network-address-database-mirroring.md)。</span><span class="sxs-lookup"><span data-stu-id="ddf98-159">For more information, see [Specify a Server Network Address &#40;Database Mirroring&#41;](specify-a-server-network-address-database-mirroring.md).</span></span>  
  
##  <a name="network-access"></a><a name="NetworkAccess"></a> <span data-ttu-id="ddf98-160">Network Access</span><span class="sxs-lookup"><span data-stu-id="ddf98-160">Network Access</span></span>  
 <span data-ttu-id="ddf98-161">必须允许每个服务器实例都能通过 TCP 访问其他一个或多个服务器实例的端口。</span><span class="sxs-lookup"><span data-stu-id="ddf98-161">Each server instance must be able to access the ports of the other server instance or instances over TCP.</span></span> <span data-ttu-id="ddf98-162">当服务器实例位于相互不信任的不同域（不可信的域）中时，这尤为重要。</span><span class="sxs-lookup"><span data-stu-id="ddf98-162">This is especially important if the server instances are in different domains that do not trust each other (untrusted domains).</span></span> <span data-ttu-id="ddf98-163">这会限制服务器实例之间大部分的通信。</span><span class="sxs-lookup"><span data-stu-id="ddf98-163">This restricts much of the communication between the server instances.</span></span>  
  
##  <a name="mirror-database-preparation"></a><a name="MirrorDbPrep"></a><span data-ttu-id="ddf98-164">镜像数据库准备</span><span class="sxs-lookup"><span data-stu-id="ddf98-164">Mirror Database Preparation</span></span>  
 <span data-ttu-id="ddf98-165">无论是首次开始镜像还是在删除镜像后再次开始镜像，都要验证镜像数据库是否可以进行镜像。</span><span class="sxs-lookup"><span data-stu-id="ddf98-165">Whether starting mirroring for the first time or starting it again after mirroring was removed, verify that the mirror database is prepared for mirroring.</span></span>  
  
 <span data-ttu-id="ddf98-166">在镜像服务器上创建镜像数据库时，请确保指定相同数据库名称 WITH NORECOVERY 来还原主体数据库备份。</span><span class="sxs-lookup"><span data-stu-id="ddf98-166">When you create the mirror database on the mirror server, make sure that you restore the backup of the principal database specifying the same database name WITH NORECOVERY.</span></span> <span data-ttu-id="ddf98-167">此外，还必须再次使用 WITH NORECOVERY 应用进行该备份之后创建的所有日志备份。</span><span class="sxs-lookup"><span data-stu-id="ddf98-167">Also, all log backups created after that backup was taken must also be applied, again WITH NORECOVERY.</span></span>  
  
 <span data-ttu-id="ddf98-168">另外，我们建议，如有可能，镜像数据库的文件路径（包括驱动器号）应该与主体数据库的路径相同。</span><span class="sxs-lookup"><span data-stu-id="ddf98-168">Also, we recommend that, if it is possible, the file path (including the drive letter) of the mirror database be identical to the path of the principal database.</span></span> <span data-ttu-id="ddf98-169">如果文件路径必须互不相同（例如，如果主体数据库位于“F:”驱动器上，但镜像系统没有“F:”驱动器），则必须在 RESTORE 语句中加入 MOVE 选项。</span><span class="sxs-lookup"><span data-stu-id="ddf98-169">If the file paths must differ, for example, if the principal database is on drive 'F:' but the mirror system lacks an F: drive, you must include the MOVE option in the RESTORE statement.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ddf98-170">如果在创建镜像数据库时移动了数据库文件，则可能导致以后不挂起镜像就无法向数据库添加文件。</span><span class="sxs-lookup"><span data-stu-id="ddf98-170">If you move the database files when you are creating the mirror database, you might be unable to add files to the database later without mirroring being suspended.</span></span>  
  
 <span data-ttu-id="ddf98-171">如果数据库镜像已经停止，则必须将对主体数据库执行的所有后续日志备份应用到镜像数据库中，然后才可以重新启动镜像。</span><span class="sxs-lookup"><span data-stu-id="ddf98-171">If database mirroring has been stopped, all subsequent log backups taken on the principal database must be applied to the mirror database before mirroring can be restarted.</span></span>  
  
 <span data-ttu-id="ddf98-172">有关详细信息，请参阅 [为镜像准备镜像数据库 (SQL Server)](prepare-a-mirror-database-for-mirroring-sql-server.md)的各版本中均未提供见证服务器实例。</span><span class="sxs-lookup"><span data-stu-id="ddf98-172">For more information, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md).</span></span>  
  
##  <a name="failed-create-file-operation"></a><a name="FailedCreateFileOp"></a> <span data-ttu-id="ddf98-173">Failed Create-File Operation</span><span class="sxs-lookup"><span data-stu-id="ddf98-173">Failed Create-File Operation</span></span>  
 <span data-ttu-id="ddf98-174">在不影响镜像会话的情况下添加文件要求该文件路径同时存在于两个服务器上。</span><span class="sxs-lookup"><span data-stu-id="ddf98-174">Adding a file without impacting a mirroring session requires that the path of the file exist on both servers.</span></span> <span data-ttu-id="ddf98-175">因此，如果在创建镜像数据库时移动了数据库文件，则随后在镜像数据库上的添加文件操作可能会失败，并可能会导致镜像挂起。</span><span class="sxs-lookup"><span data-stu-id="ddf98-175">Therefore, if you move the database files when creating the mirror database, a later add-file operation might fail on the mirror database and cause mirroring to be suspended.</span></span>  
  
 <span data-ttu-id="ddf98-176">修复此问题：</span><span class="sxs-lookup"><span data-stu-id="ddf98-176">To fix the problem:</span></span>  
  
1.  <span data-ttu-id="ddf98-177">数据库所有者必须删除此镜像会话，并还原包含所添加文件的文件组的完整备份。</span><span class="sxs-lookup"><span data-stu-id="ddf98-177">The database owner must remove the mirroring session and restore a full backup of the filegroup that contains the added file.</span></span>  
  
2.  <span data-ttu-id="ddf98-178">然后，所有者必须备份主体服务器上包含添加文件操作的日志，并使用 WITH NORECOVERY 和 WITH MOVE 选项在镜像数据库上手动还原此日志备份。</span><span class="sxs-lookup"><span data-stu-id="ddf98-178">The owner must then back up the log containing the add-file operation on the principal server and manually restore the log backup on the mirror database using the WITH NORECOVERY and WITH MOVE options.</span></span> <span data-ttu-id="ddf98-179">执行此操作可在镜像服务器上创建指定的文件路径，并将相应的新文件还原到该位置。</span><span class="sxs-lookup"><span data-stu-id="ddf98-179">Doing this creates the specified file path on the mirror server and restores the new file to that location.</span></span>  
  
3.  <span data-ttu-id="ddf98-180">若要准备数据库以进行新的镜像会话，数据库所有者还必须使用 WITH NO RECOVERY 选项还原主体服务器上所有其他未完成的日志备份。</span><span class="sxs-lookup"><span data-stu-id="ddf98-180">To prepare the database for a new mirroring session, the owner must also restore WITH NO RECOVERY any other outstanding log backups from the principal server.</span></span>  
  
 <span data-ttu-id="ddf98-181">有关详细信息，请参阅[删除数据库镜像 (SQL Server)](database-mirroring-sql-server.md)、[为镜像准备镜像数据库 (SQL Server)](prepare-a-mirror-database-for-mirroring-sql-server.md)、[使用 Windows 身份验证建立数据库镜像会话 (Transact-SQL)](database-mirroring-establish-session-windows-authentication.md)、[使用数据库镜像端点证书 (Transact-SQL)](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)，或[使用 Windows 身份验证建立数据库镜像会话 (SQL Server Management Studio)](establish-database-mirroring-session-windows-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="ddf98-181">For more information, see [Removing Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md), [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md), [Establish a Database Mirroring Session Using Windows Authentication &#40;Transact-SQL&#41;](database-mirroring-establish-session-windows-authentication.md), [Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md), or [Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md).</span></span>  
  
##  <a name="starting-mirroring-by-using-transact-sql"></a><a name="StartDbm"></a><span data-ttu-id="ddf98-182">使用 Transact-sql 开始镜像</span><span class="sxs-lookup"><span data-stu-id="ddf98-182">Starting mirroring by Using Transact-SQL</span></span>  
 <span data-ttu-id="ddf98-183">发出 ALTER DATABASE *database_name* SET PARTNER **='***partner_server***'** 语句的顺序非常关键。</span><span class="sxs-lookup"><span data-stu-id="ddf98-183">The order in which the ALTER DATABASE *database_name* SET PARTNER **='***partner_server***'** statements are issued is very important.</span></span>  
  
1.  <span data-ttu-id="ddf98-184">第一个语句必须在镜像服务器上运行。</span><span class="sxs-lookup"><span data-stu-id="ddf98-184">The first statement must be run on the mirror server.</span></span> <span data-ttu-id="ddf98-185">发出此语句时，镜像服务器不会尝试联系任何其他服务器实例。</span><span class="sxs-lookup"><span data-stu-id="ddf98-185">When this statement is issued, the mirror server does not try to contact any other server instance.</span></span> <span data-ttu-id="ddf98-186">相反，镜像服务器指示其数据库先进行等待，直到主体服务器与镜像服务器建立联系。</span><span class="sxs-lookup"><span data-stu-id="ddf98-186">Instead, the mirror server instructs its database to wait until the mirror server has been contacted by the principal server.</span></span>  
  
2.  <span data-ttu-id="ddf98-187">第二个 ALTER DATABASE 语句必须在主体服务器上运行。</span><span class="sxs-lookup"><span data-stu-id="ddf98-187">The second ALTER DATABASE statement must be run on the principal server.</span></span> <span data-ttu-id="ddf98-188">此语句使主体服务器尝试连接到镜像服务器。</span><span class="sxs-lookup"><span data-stu-id="ddf98-188">This statement causes the principal server to try to connect to the mirror server.</span></span> <span data-ttu-id="ddf98-189">创建此连接之后，镜像服务器随后将尝试通过其他连接与主体服务器建立连接。</span><span class="sxs-lookup"><span data-stu-id="ddf98-189">After that connection is created, the mirror then tries to connect to the principal server on another connection.</span></span>  
  
 <span data-ttu-id="ddf98-190">有关详细信息，请参阅 [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ddf98-190">For more information, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ddf98-191">有关使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 启动镜像的信息，请参阅[使用 Windows 身份验证建立数据库镜像会话 (SQL Server Management Studio)](establish-database-mirroring-session-windows-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="ddf98-191">For information about using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to start mirroring, see [Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md).</span></span>  
  
##  <a name="cross-database-transactions"></a><a name="CrossDbTxns"></a><span data-ttu-id="ddf98-192">跨数据库事务</span><span class="sxs-lookup"><span data-stu-id="ddf98-192">Cross-Database Transactions</span></span>  
 <span data-ttu-id="ddf98-193">在具有自动故障转移功能的高安全性模式下镜像数据库时，自动故障转移可能会导致自动解析并且可能错误解析有疑问的事务。</span><span class="sxs-lookup"><span data-stu-id="ddf98-193">When a database is being mirrored in high-safety mode with automatic failover, an automatic failover could lead to automatic and possibly incorrect resolution of in-doubt transactions.</span></span> <span data-ttu-id="ddf98-194">如果提交跨数据库事务时在任一数据库中进行自动故障转移，则数据库之间可能发生逻辑上的不一致。</span><span class="sxs-lookup"><span data-stu-id="ddf98-194">If an automatic failover occurs on either database while a cross-database transaction is being committed, logical inconsistencies can occur between the databases.</span></span>  
  
 <span data-ttu-id="ddf98-195">自动故障转移可能影响的跨数据库事务类型包括：</span><span class="sxs-lookup"><span data-stu-id="ddf98-195">The types of cross-database transactions that can be affected by an automatic failover include the following:</span></span>  
  
-   <span data-ttu-id="ddf98-196">正在同一 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例中更新多个数据库的事务。</span><span class="sxs-lookup"><span data-stu-id="ddf98-196">A transaction that is updating multiple databases in the same instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="ddf98-197">使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 分布式事务处理协调器 (MS DTC) 的事务。</span><span class="sxs-lookup"><span data-stu-id="ddf98-197">Transactions that use a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC).</span></span>  
  
 <span data-ttu-id="ddf98-198">有关详细信息，请参阅[数据库镜像或 AlwaysOn 可用性组不支持跨数据库事务 (SQL Server)](../availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md)。</span><span class="sxs-lookup"><span data-stu-id="ddf98-198">For more information, see [Cross-Database Transactions Not Supported For Database Mirroring or AlwaysOn Availability Groups &#40;SQL Server&#41;](../availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddf98-199">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ddf98-199">See Also</span></span>  
 <span data-ttu-id="ddf98-200">[设置数据库镜像 (SQL Server)](setting-up-database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ddf98-200">[Setting Up Database Mirroring &#40;SQL Server&#41;](setting-up-database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="ddf98-201">用于数据库镜像和 AlwaysOn 可用性组 &#40;SQL Server 的传输安全&#41;</span><span class="sxs-lookup"><span data-stu-id="ddf98-201">Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](transport-security-database-mirroring-always-on-availability.md)  
  
  
