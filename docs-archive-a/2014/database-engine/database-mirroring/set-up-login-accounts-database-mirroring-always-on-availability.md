---
title: 设置用于数据库镜像或 AlwaysOn 可用性组 (SQL Server) 的登录帐户 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], deployment
- logins [SQL Server], database mirroring
ms.assetid: e9f5287b-1325-4cda-88a6-19eaaa52a652
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d149016dabd0239bd76eadc8655b6752afd916d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690100"
---
# <a name="set-up-login-accounts-for-database-mirroring-or-alwayson-availability-groups-sql-server"></a><span data-ttu-id="29ee4-102">设置数据库镜像或 AlwaysOn 可用性组的登录帐户 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="29ee4-102">Set Up Login Accounts for Database Mirroring or AlwaysOn Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="29ee4-103">为了使两个服务器实例能够连接到彼此的[数据库镜像端点](the-database-mirroring-endpoint-sql-server.md)，每个实例的登录帐户都要具有访问另一实例的权限。</span><span class="sxs-lookup"><span data-stu-id="29ee4-103">For two server instances to connect to each other's [database mirroring endpoint](the-database-mirroring-endpoint-sql-server.md) point, the login account of each instance requires access to the other instance.</span></span> <span data-ttu-id="29ee4-104">每个登录帐户还要具有可以连接到另一实例的数据库镜像端点的权限。</span><span class="sxs-lookup"><span data-stu-id="29ee4-104">Also, each login account requires connect permission to the Database Mirroring endpoint of the other instance.</span></span>  
  
 <span data-ttu-id="29ee4-105">此要求的影响取决于服务器实例是否使用相同的域用户帐户运行：</span><span class="sxs-lookup"><span data-stu-id="29ee4-105">The impact of this requirement depends on whether the server instances run as the same domain user account:</span></span>  
  
-   <span data-ttu-id="29ee4-106">\*\*\*\* 如果服务器实例使用相同的域用户帐户运行，则正确的用户登录名将自动存在于全部两个 master 数据库中。</span><span class="sxs-lookup"><span data-stu-id="29ee4-106">If the server instances run as the same domain user account, the correct user logins exist automatically in both **master** databases.</span></span> <span data-ttu-id="29ee4-107">这样可简化数据库镜像和 AlwaysOn 可用性组的安全配置。</span><span class="sxs-lookup"><span data-stu-id="29ee4-107">This simplifies the security configuration for Database Mirroring and AlwaysOn Availability Groups.</span></span>  
  
-   <span data-ttu-id="29ee4-108">如果服务器实例使用不同的用户帐户运行，则在承载镜像服务器的服务器实例上或承载辅助副本的每个服务器实例上都必须手动复制承载主体服务器或主要副本的服务器实例上的用户登录名。</span><span class="sxs-lookup"><span data-stu-id="29ee4-108">If the server instances run as different user accounts, user logins on the server instance that hosts the principal server or primary replica must be manually reproduced on the server instance that hosts the mirror server or on every server instance that hosts a secondary replica.</span></span> <span data-ttu-id="29ee4-109">有关详细信息，请参阅本主题后面的[为不同帐户创建登录名](#CreateLogin)和[授予连接权限](#GrantConnect)。</span><span class="sxs-lookup"><span data-stu-id="29ee4-109">For more information, see [Create a Login for a Different Account](#CreateLogin) and [Grant Connect Permission](#GrantConnect), later in this topic.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="29ee4-110">要创建更安全的环境，请考虑为每个服务器实例使用单独的域帐户。</span><span class="sxs-lookup"><span data-stu-id="29ee4-110">To create a more secure environment, consider using separate domain accounts for each server instance.</span></span>  
  
##  <a name="create-a-login-for-a-different-account"></a><a name="CreateLogin"></a><span data-ttu-id="29ee4-111">为不同帐户创建登录名</span><span class="sxs-lookup"><span data-stu-id="29ee4-111">Create a Login for a Different Account</span></span>  
 <span data-ttu-id="29ee4-112">如果两个服务器实例作为不同的帐户运行，则系统管理员必须使用 CREATE LOGIN [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句针对每个服务器实例为远程实例的启动服务帐户创建一个登录名。</span><span class="sxs-lookup"><span data-stu-id="29ee4-112">If two server instances run as different accounts, the system administrator must use the CREATE LOGIN [!INCLUDE[tsql](../../includes/tsql-md.md)] statement to create a login for the startup service account of the remote instance for each server instance.</span></span> <span data-ttu-id="29ee4-113">有关详细信息，请参阅 [CREATE LOGIN (Transact-SQL)](/sql/t-sql/statements/create-login-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="29ee4-113">For more information, see [CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="29ee4-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 如果使用非域帐户运行 ，则必须使用证书。</span><span class="sxs-lookup"><span data-stu-id="29ee4-114">If you run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] under a non-domain account, you must use certificates.</span></span> <span data-ttu-id="29ee4-115">有关详细信息，请参阅[使用数据库镜像终结点证书 (Transact-SQL)](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="29ee4-115">For more information, see [Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md).</span></span>  
  
 <span data-ttu-id="29ee4-116">例如，若要使 loginA 下运行的服务器实例 sqlA 连接到在 loginB 下运行的服务器实例 sqlB，则 sqlB 上必须存在 loginA 且 sqlA 上必须存在 loginB。</span><span class="sxs-lookup"><span data-stu-id="29ee4-116">For example, for the server instance sqlA, which runs under loginA, to connect to the server instance sqlB, which runs under loginB, loginA must exist on sqlB, and loginB must exist on sqlA.</span></span> <span data-ttu-id="29ee4-117">此外，对于包含见证服务器实例 (sqlC) 且三个服务器实例运行在不同域帐户下的数据库镜像会话，必须创建下列登录帐户：</span><span class="sxs-lookup"><span data-stu-id="29ee4-117">In addition, for a database mirroring session that includes a witness server instance (sqlC) and in which the three server instances run under different domain accounts, the following logins must be created:</span></span>  
  
|<span data-ttu-id="29ee4-118">所在实例...</span><span class="sxs-lookup"><span data-stu-id="29ee4-118">On instance...</span></span>|<span data-ttu-id="29ee4-119">创建登录帐户并将连接权限授予...</span><span class="sxs-lookup"><span data-stu-id="29ee4-119">Create logins for and grant connection permission to ...</span></span>|  
|--------------------|--------------------------------------------------------------|  
|<span data-ttu-id="29ee4-120">sqlA</span><span class="sxs-lookup"><span data-stu-id="29ee4-120">sqlA</span></span>|<span data-ttu-id="29ee4-121">sqlB 和 sqlC</span><span class="sxs-lookup"><span data-stu-id="29ee4-121">sqlB and sqlC</span></span>|  
|<span data-ttu-id="29ee4-122">sqlB</span><span class="sxs-lookup"><span data-stu-id="29ee4-122">sqlB</span></span>|<span data-ttu-id="29ee4-123">sqlA 和 sqlC</span><span class="sxs-lookup"><span data-stu-id="29ee4-123">sqlA and sqlC</span></span>|  
|<span data-ttu-id="29ee4-124">sqlC</span><span class="sxs-lookup"><span data-stu-id="29ee4-124">sqlC</span></span>|<span data-ttu-id="29ee4-125">sqlA 和 sqlB</span><span class="sxs-lookup"><span data-stu-id="29ee4-125">sqlA and sqlB</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="29ee4-126">可以使用计算机帐户（而不是域用户）连接网络服务帐户。</span><span class="sxs-lookup"><span data-stu-id="29ee4-126">It is possible to connect with the network service account by using the machine account instead of a domain user.</span></span> <span data-ttu-id="29ee4-127">如果使用的是计算机帐户，则必须将其作为用户添加到其他服务器实例上。</span><span class="sxs-lookup"><span data-stu-id="29ee4-127">If the machine account is used, it must be added as a user on the other server instance.</span></span>  
  
##  <a name="grant-connect-permission"></a><a name="GrantConnect"></a><span data-ttu-id="29ee4-128">Grant Connect 权限</span><span class="sxs-lookup"><span data-stu-id="29ee4-128">Grant Connect Permission</span></span>  
 <span data-ttu-id="29ee4-129">在服务器实例上创建登录帐户后，必须授予登录帐户连接到服务器实例的数据库镜像端点的权限。</span><span class="sxs-lookup"><span data-stu-id="29ee4-129">Once a login has been created on a server instance, the login must be granted permission to connect to the database mirroring endpoint of the server instance.</span></span> <span data-ttu-id="29ee4-130">系统管理员使用 GRANT [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句授予连接权限。</span><span class="sxs-lookup"><span data-stu-id="29ee4-130">The system administrator grants the connect permission using a GRANT [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="29ee4-131">有关详细信息，请参阅 [GRANT (Transact-SQL)](/sql/t-sql/statements/grant-transact-sql)的信息。</span><span class="sxs-lookup"><span data-stu-id="29ee4-131">For more information, see [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="29ee4-132">相关任务</span><span class="sxs-lookup"><span data-stu-id="29ee4-132">Related Tasks</span></span>  
  
-   [<span data-ttu-id="29ee4-133">创建登录名</span><span class="sxs-lookup"><span data-stu-id="29ee4-133">Create a Login</span></span>](../../relational-databases/security/authentication-access/create-a-login.md)  
  
-   <span data-ttu-id="29ee4-134">[允许使用 Windows 身份验证 &#40;SQL Server&#41;对数据库镜像端点进行网络访问](../database-mirroring-allow-network-access-windows-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="29ee4-134">[Allow Network Access to a Database Mirroring Endpoint Using Windows Authentication &#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md).</span></span>  
  
-   [<span data-ttu-id="29ee4-135">使用数据库镜像终结点证书 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="29ee4-135">Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;</span></span>](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="29ee4-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="29ee4-136">See Also</span></span>  
 <span data-ttu-id="29ee4-137">[数据库镜像终结点 (SQL Server)](the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="29ee4-137">[The Database Mirroring Endpoint &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span></span>  
 <span data-ttu-id="29ee4-138">[数据库镜像配置故障排除 (SQL Server)](troubleshoot-database-mirroring-configuration-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="29ee4-138">[Troubleshoot Database Mirroring Configuration &#40;SQL Server&#41;](troubleshoot-database-mirroring-configuration-sql-server.md) </span></span>  
 [<span data-ttu-id="29ee4-139">AlwaysOn 可用性组配置 &#40;SQL Server&#41;疑难解答</span><span class="sxs-lookup"><span data-stu-id="29ee4-139">Troubleshoot AlwaysOn Availability Groups Configuration &#40;SQL Server&#41;</span></span>](../availability-groups/windows/troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
  
