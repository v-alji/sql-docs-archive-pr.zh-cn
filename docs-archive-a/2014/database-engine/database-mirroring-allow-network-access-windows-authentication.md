---
title: 对数据库镜像端点进行网络访问
description: 了解如何允许 windows authenticatino 网络访问数据库镜像端点 SQL Server。
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Windows authentication [SQL Server]
- database mirroring [SQL Server], security
ms.assetid: 28c8fec5-5feb-4c84-8d72-f2bd1ae3b40d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0d1d8786d128ef2cc99fe571e33f89c4c4e7699c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589210"
---
# <a name="allow-network-access-to-a-database-mirroring-endpoint-using-windows-authentication-sql-server"></a><span data-ttu-id="8efb5-103">允许使用 Windows 身份验证对数据库镜像端点进行网络访问 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="8efb5-103">Allow Network Access to a Database Mirroring Endpoint Using Windows Authentication (SQL Server)</span></span>
  <span data-ttu-id="8efb5-104">将 Windows 身份验证用于连接两个 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例的数据库镜像端点在以下条件下要求手动配置登录帐户：</span><span class="sxs-lookup"><span data-stu-id="8efb5-104">Using Windows Authentication for connecting the database mirroring endpoints of two instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] requires manual configuration of login accounts under the following conditions:</span></span>  
  
-   <span data-ttu-id="8efb5-105">如果 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的实例基于不同的域帐户（在相同的域或受信任的域中）作为服务运行，则必须在每个远程服务器实例上的 **master** 中创建各帐户的登录名，并且必须授予该登录帐户对端点的 CONNECT 权限。</span><span class="sxs-lookup"><span data-stu-id="8efb5-105">If the instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] run as services under different domain accounts (in the same or trusted domains), the login of each account must be created in **master** on each of the remote server instances and that login must be granted CONNECT permissions on the endpoint.</span></span>  
  
-   <span data-ttu-id="8efb5-106">如果 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例作为网络服务帐户运行，则必须在每个远程服务器实例上的 master 中创建各主机帐户 (DomainName\\ComputerName$) \*\* 的登录名，并且必须授予该登录帐户对端点的 CONNECT 权限。</span><span class="sxs-lookup"><span data-stu-id="8efb5-106">If the instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] run as the Network Service account, the login of the each host computer account (*DomainName***\\***ComputerName$*) must be created in **master** on each of the remote server instances and that login must be granted CONNECT permissions on the endpoint.</span></span> <span data-ttu-id="8efb5-107">其原因在于，基于网络服务帐户运行的服务器实例使用主机的域帐户进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="8efb5-107">This is because a server instance running under the Network Service account authenticates using the domain account of the host computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8efb5-108">确保每个服务器实例都有一个端点。</span><span class="sxs-lookup"><span data-stu-id="8efb5-108">Ensure that an endpoint exists for each of the server instances.</span></span> <span data-ttu-id="8efb5-109">有关详细信息，请参阅 [为 Windows 身份验证创建数据库镜像终结点 (Transact-SQL)](database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="8efb5-109">For more information, see [Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md).</span></span>  
  
### <a name="to-configure-logins-for-windows-authentication"></a><span data-ttu-id="8efb5-110">为 Windows 身份验证配置登录名</span><span class="sxs-lookup"><span data-stu-id="8efb5-110">To configure logins for Windows Authentication</span></span>  
  
1.  <span data-ttu-id="8efb5-111">对于每个 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]实例的用户帐户，在其他 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]实例上创建一个登录名。</span><span class="sxs-lookup"><span data-stu-id="8efb5-111">For the user account of each instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], create a login on the other instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="8efb5-112">将 [CREATE LOGIN](/sql/t-sql/statements/create-login-transact-sql) 语句与 FROM WINDOWS 子句一起使用。</span><span class="sxs-lookup"><span data-stu-id="8efb5-112">Use a [CREATE LOGIN](/sql/t-sql/statements/create-login-transact-sql) statement with the FROM WINDOWS clause.</span></span>  
  
     <span data-ttu-id="8efb5-113">有关详细信息，请参阅 [创建登录名](../relational-databases/security/authentication-access/create-a-login.md)。</span><span class="sxs-lookup"><span data-stu-id="8efb5-113">For more information, see [Create a Login](../relational-databases/security/authentication-access/create-a-login.md).</span></span>  
  
2.  <span data-ttu-id="8efb5-114">另外，为了确保登录用户对端点具有访问权限，请使用 [GRANT](/sql/t-sql/statements/grant-transact-sql) 语句为登录授予对端点的连接权限。</span><span class="sxs-lookup"><span data-stu-id="8efb5-114">Also, to ensure that the login user has access to the endpoint, use the [GRANT](/sql/t-sql/statements/grant-transact-sql) statement to grant connect permissions on the endpoint to the login.</span></span> <span data-ttu-id="8efb5-115">注意，如果用户是管理员，则无需授予对端点的连接权限。</span><span class="sxs-lookup"><span data-stu-id="8efb5-115">Note that granting connect permissions to the endpoint is unnecessary if the user is an Administrator.</span></span>  
  
     <span data-ttu-id="8efb5-116">有关详细信息，请参阅 [Grant a Permission to a Principal](../relational-databases/security/authentication-access/grant-a-permission-to-a-principal.md)。</span><span class="sxs-lookup"><span data-stu-id="8efb5-116">For more information, see [Grant a Permission to a Principal](../relational-databases/security/authentication-access/grant-a-permission-to-a-principal.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8efb5-117">示例</span><span class="sxs-lookup"><span data-stu-id="8efb5-117">Example</span></span>  
 <span data-ttu-id="8efb5-118">下面的 [!INCLUDE[tsql](../includes/tsql-md.md)] 示例为属于 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 域的 `Otheruser` 用户帐户创建了一个 `Adomain`登录名。</span><span class="sxs-lookup"><span data-stu-id="8efb5-118">The following [!INCLUDE[tsql](../includes/tsql-md.md)] example creates a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] login for a user account named `Otheruser` that belongs to a domain called `Adomain`.</span></span> <span data-ttu-id="8efb5-119">并授予了此用户对预先存在的 `Mirroring_Endpoint`数据库镜像端点的连接权限。</span><span class="sxs-lookup"><span data-stu-id="8efb5-119">The example then grants this user connect permissions to a pre-existing database mirroring endpoint named `Mirroring_Endpoint`.</span></span>  
  
```  
USE master;  
GO  
CREATE LOGIN [Adomain\Otheruser] FROM WINDOWS;  
GO  
GRANT CONNECT on ENDPOINT::Mirroring_Endpoint TO [Adomain\Otheruser];  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="8efb5-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8efb5-120">See Also</span></span>  
 <span data-ttu-id="8efb5-121">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8efb5-121">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="8efb5-122">[数据库镜像 (SQL Server)](database-mirroring/database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8efb5-122">[Database Mirroring &#40;SQL Server&#41;](database-mirroring/database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="8efb5-123">[用于数据库镜像和 AlwaysOn 可用性组 &#40;SQL Server 的传输安全&#41;](database-mirroring/transport-security-database-mirroring-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="8efb5-123">[Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;](database-mirroring/transport-security-database-mirroring-always-on-availability.md) </span></span>  
 [<span data-ttu-id="8efb5-124">数据库镜像终结点 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="8efb5-124">The Database Mirroring Endpoint &#40;SQL Server&#41;</span></span>](database-mirroring/the-database-mirroring-endpoint-sql-server.md)  
  
  
