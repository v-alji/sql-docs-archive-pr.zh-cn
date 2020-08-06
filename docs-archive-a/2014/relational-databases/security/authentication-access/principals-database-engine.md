---
title: 主体（数据库引擎）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.roleproperties.selectroll.f1
- sql12.swb.databaseuser.permissions.user.f1--May use common.permissions
helpviewer_keywords:
- certificates [SQL Server], principals
- roles [SQL Server], principals
- permissions [SQL Server], principals
- '##MS_SQLAuthenticatorCertificate##'
- principals [SQL Server]
- '##MS_SQLResourceSigningCertificate##'
- groups [SQL Server], principals
- '##MS_AgentSigningCertificate##'
- authentication [SQL Server], principals
- schemas [SQL Server], principals
- principals [SQL Server], about principals
- security [SQL Server], principals
- users [SQL Server], principals
- '##MS_SQLReplicationSigningCertificate##'
ms.assetid: 3f7adbf7-6e40-4396-a8ca-71cbb843b5c2
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 808c8516b3ed9e95ea4c724736461cb00923a7fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591209"
---
# <a name="principals-database-engine"></a><span data-ttu-id="2aa08-102">主体（数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="2aa08-102">Principals (Database Engine)</span></span>
  <span data-ttu-id="2aa08-103">“主体” 是可以请求 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 资源的实体。</span><span class="sxs-lookup"><span data-stu-id="2aa08-103">*Principals* are entities that can request [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] resources.</span></span> <span data-ttu-id="2aa08-104">与 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 授权模型的其他组件一样，主体也可以按层次结构排列。</span><span class="sxs-lookup"><span data-stu-id="2aa08-104">Like other components of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] authorization model, principals can be arranged in a hierarchy.</span></span> <span data-ttu-id="2aa08-105">主体的影响范围取决于主体的定义范围：Windows、服务器、数据库；以及主体是不可分割还是集合。</span><span class="sxs-lookup"><span data-stu-id="2aa08-105">The scope of influence of a principal depends on the scope of the definition of the principal: Windows, server, database; and whether the principal is indivisible or a collection.</span></span> <span data-ttu-id="2aa08-106">例如，Windows 登录名就是一个不可分主体，而 Windows 组则是一个集合主体。</span><span class="sxs-lookup"><span data-stu-id="2aa08-106">A Windows Login is an example of an indivisible principal, and a Windows Group is an example of a principal that is a collection.</span></span> <span data-ttu-id="2aa08-107">每个主体都具有一个安全标识符 (SID)。</span><span class="sxs-lookup"><span data-stu-id="2aa08-107">Every principal has a security identifier (SID).</span></span>  
  
 <span data-ttu-id="2aa08-108">**Windows 级别的主体**</span><span class="sxs-lookup"><span data-stu-id="2aa08-108">**Windows-level principals**</span></span>  
  
-   <span data-ttu-id="2aa08-109">Windows 域登录名</span><span class="sxs-lookup"><span data-stu-id="2aa08-109">Windows Domain Login</span></span>  
  
-   <span data-ttu-id="2aa08-110">Windows 本地登录名</span><span class="sxs-lookup"><span data-stu-id="2aa08-110">Windows Local Login</span></span>  
  
 <span data-ttu-id="2aa08-111">**SQL Server** -**级别\*\*\*\*主体**</span><span class="sxs-lookup"><span data-stu-id="2aa08-111">**SQL Server**-**level** **principals**</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="2aa08-112">Id</span><span class="sxs-lookup"><span data-stu-id="2aa08-112">Login</span></span>  
  
-   <span data-ttu-id="2aa08-113">服务器角色</span><span class="sxs-lookup"><span data-stu-id="2aa08-113">Server Role</span></span>  
  
 <span data-ttu-id="2aa08-114">**数据库级的主体**</span><span class="sxs-lookup"><span data-stu-id="2aa08-114">**Database-level principals**</span></span>  
  
-   <span data-ttu-id="2aa08-115">数据库用户</span><span class="sxs-lookup"><span data-stu-id="2aa08-115">Database User</span></span>  
  
-   <span data-ttu-id="2aa08-116">数据库角色</span><span class="sxs-lookup"><span data-stu-id="2aa08-116">Database Role</span></span>  
  
-   <span data-ttu-id="2aa08-117">应用程序角色</span><span class="sxs-lookup"><span data-stu-id="2aa08-117">Application Role</span></span>  
  
## <a name="the-sql-server-sa-login"></a><span data-ttu-id="2aa08-118">SQL Server sa 登录名</span><span class="sxs-lookup"><span data-stu-id="2aa08-118">The SQL Server sa Login</span></span>  
 <span data-ttu-id="2aa08-119">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sa 登录名是服务器级的主体。</span><span class="sxs-lookup"><span data-stu-id="2aa08-119">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sa log in is a server-level principal.</span></span> <span data-ttu-id="2aa08-120">默认情况下，该登录名是在安装实例时创建的。</span><span class="sxs-lookup"><span data-stu-id="2aa08-120">By default, it is created when an instance is installed.</span></span> <span data-ttu-id="2aa08-121">从 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]开始，sa 的默认数据库为“master”。</span><span class="sxs-lookup"><span data-stu-id="2aa08-121">Beginning in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], the default database of sa is master.</span></span> <span data-ttu-id="2aa08-122">这是对早期版本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]的行为的更改。</span><span class="sxs-lookup"><span data-stu-id="2aa08-122">This is a change of behavior from earlier versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="public-database-role"></a><span data-ttu-id="2aa08-123">public 数据库角色</span><span class="sxs-lookup"><span data-stu-id="2aa08-123">public Database Role</span></span>  
 <span data-ttu-id="2aa08-124">每个数据库用户都属于 public 数据库角色。</span><span class="sxs-lookup"><span data-stu-id="2aa08-124">Every database user belongs to the public database role.</span></span> <span data-ttu-id="2aa08-125">当尚未对某个用户授予或拒绝对安全对象的特定权限时，则该用户将继承授予该安全对象的 public 角色的权限。</span><span class="sxs-lookup"><span data-stu-id="2aa08-125">When a user has not been granted or denied specific permissions on a securable, the user inherits the permissions granted to public on that securable.</span></span>  
  
## <a name="information_schema-and-sys"></a><span data-ttu-id="2aa08-126">INFORMATION_SCHEMA 和 sys</span><span class="sxs-lookup"><span data-stu-id="2aa08-126">INFORMATION_SCHEMA and sys</span></span>  
 <span data-ttu-id="2aa08-127">每个数据库都包含两个实体：INFORMATION_SCHEMA 和 sys，它们都作为用户出现在目录视图中。</span><span class="sxs-lookup"><span data-stu-id="2aa08-127">Every database includes two entities that appear as users in catalog views: INFORMATION_SCHEMA and sys.</span></span> <span data-ttu-id="2aa08-128">这两个实体是 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]所必需的。</span><span class="sxs-lookup"><span data-stu-id="2aa08-128">These entities are required by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="2aa08-129">它们不是主体，不能修改或删除它们。</span><span class="sxs-lookup"><span data-stu-id="2aa08-129">They are not principals, and they cannot be modified or dropped.</span></span>  
  
## <a name="certificate-based-sql-server-logins"></a><span data-ttu-id="2aa08-130">基于证书的 SQL Server 登录名</span><span class="sxs-lookup"><span data-stu-id="2aa08-130">Certificate-based SQL Server Logins</span></span>  
 <span data-ttu-id="2aa08-131">名称由双井号 (##) 括起来的服务器主体仅供内部系统使用。</span><span class="sxs-lookup"><span data-stu-id="2aa08-131">Server principals with names enclosed by double hash marks (##) are for internal system use only.</span></span> <span data-ttu-id="2aa08-132">下列主体是在安装 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 时从证书创建的，不应删除。</span><span class="sxs-lookup"><span data-stu-id="2aa08-132">The following principals are created from certificates when [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is installed, and should not be deleted.</span></span>  
  
-   <span data-ttu-id="2aa08-133">\##MS_SQLResourceSigningCertificate##</span><span class="sxs-lookup"><span data-stu-id="2aa08-133">\##MS_SQLResourceSigningCertificate##</span></span>  
  
-   <span data-ttu-id="2aa08-134">\##MS_SQLReplicationSigningCertificate##</span><span class="sxs-lookup"><span data-stu-id="2aa08-134">\##MS_SQLReplicationSigningCertificate##</span></span>  
  
-   <span data-ttu-id="2aa08-135">\##MS_SQLAuthenticatorCertificate##</span><span class="sxs-lookup"><span data-stu-id="2aa08-135">\##MS_SQLAuthenticatorCertificate##</span></span>  
  
-   <span data-ttu-id="2aa08-136">\##MS_AgentSigningCertificate##</span><span class="sxs-lookup"><span data-stu-id="2aa08-136">\##MS_AgentSigningCertificate##</span></span>  
  
-   <span data-ttu-id="2aa08-137">\##MS_PolicyEventProcessingLogin##</span><span class="sxs-lookup"><span data-stu-id="2aa08-137">\##MS_PolicyEventProcessingLogin##</span></span>  
  
-   <span data-ttu-id="2aa08-138">\##MS_PolicySigningCertificate##</span><span class="sxs-lookup"><span data-stu-id="2aa08-138">\##MS_PolicySigningCertificate##</span></span>  
  
-   <span data-ttu-id="2aa08-139">\##MS_PolicyTsqlExecutionLogin##</span><span class="sxs-lookup"><span data-stu-id="2aa08-139">\##MS_PolicyTsqlExecutionLogin##</span></span>  
  
## <a name="the-guest-user"></a><span data-ttu-id="2aa08-140">guest 用户</span><span class="sxs-lookup"><span data-stu-id="2aa08-140">The guest User</span></span>  
 <span data-ttu-id="2aa08-141">每个数据库包括一个 **guest**。</span><span class="sxs-lookup"><span data-stu-id="2aa08-141">Each database includes a **guest**.</span></span> <span data-ttu-id="2aa08-142">授予 **guest** 用户的权限由对数据库具有访问权限，但在数据库中没有用户帐户的用户继承。</span><span class="sxs-lookup"><span data-stu-id="2aa08-142">Permissions granted to the **guest** user are inherited by users who have access to the database, but who do not have a user account in the database.</span></span> <span data-ttu-id="2aa08-143">不能删除**guest**用户，但可通过撤消该用户的权限将其禁用 `CONNECT` 。</span><span class="sxs-lookup"><span data-stu-id="2aa08-143">The **guest** user cannot be dropped, but it can be disabled by revoking it's `CONNECT` permission.</span></span> <span data-ttu-id="2aa08-144">`CONNECT`可以通过 `REVOKE CONNECT FROM GUEST` 在 master 或 tempdb 以外的任何数据库中执行来撤消权限。</span><span class="sxs-lookup"><span data-stu-id="2aa08-144">The `CONNECT` permission can be revoked by executing `REVOKE CONNECT FROM GUEST` within any database other than master or tempdb.</span></span>  
  
## <a name="client-and-database-server"></a><span data-ttu-id="2aa08-145">客户端和数据库服务器</span><span class="sxs-lookup"><span data-stu-id="2aa08-145">Client and Database Server</span></span>  
 <span data-ttu-id="2aa08-146">根据定义，客户端和数据库服务器是安全主体，可以得到保护。</span><span class="sxs-lookup"><span data-stu-id="2aa08-146">By definition, a client and a database server are security principals and can be secured.</span></span> <span data-ttu-id="2aa08-147">在建立安全的网络连接前，这些实体之间可以互相进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="2aa08-147">These entities can be mutually authenticated before a secure network connection is established.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="2aa08-148">支持[Kerberos](https://go.microsoft.com/fwlink/?LinkId=100758)身份验证协议，该协议定义客户端与网络身份验证服务交互的方式。</span><span class="sxs-lookup"><span data-stu-id="2aa08-148">supports the [Kerberos](https://go.microsoft.com/fwlink/?LinkId=100758) authentication protocol, which defines how clients interact with a network authentication service.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="2aa08-149">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="2aa08-149">Related Tasks</span></span>  
 <span data-ttu-id="2aa08-150">下列主题包括在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 联机丛书的本节中：</span><span class="sxs-lookup"><span data-stu-id="2aa08-150">The following topics are included in this section of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Books Online:</span></span>  
  
-   [<span data-ttu-id="2aa08-151">管理登录名、用户和架构操作指南主题</span><span class="sxs-lookup"><span data-stu-id="2aa08-151">Managing Logins, Users, and Schemas How-to Topics</span></span>](managing-logins-users-and-schemas-how-to-topics.md)  
  
-   [<span data-ttu-id="2aa08-152">服务器级角色</span><span class="sxs-lookup"><span data-stu-id="2aa08-152">Server-Level Roles</span></span>](server-level-roles.md)  
  
-   [<span data-ttu-id="2aa08-153">数据库级别的角色</span><span class="sxs-lookup"><span data-stu-id="2aa08-153">Database-Level Roles</span></span>](database-level-roles.md)  
  
-   [<span data-ttu-id="2aa08-154">应用程序角色</span><span class="sxs-lookup"><span data-stu-id="2aa08-154">Application Roles</span></span>](application-roles.md)  
  
## <a name="see-also"></a><span data-ttu-id="2aa08-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2aa08-155">See Also</span></span>  
 <span data-ttu-id="2aa08-156">[保护 SQL Server](../securing-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2aa08-156">[Securing SQL Server](../securing-sql-server.md) </span></span>  
 <span data-ttu-id="2aa08-157">[sys.database_principals (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-database-principals-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2aa08-157">[sys.database_principals &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-principals-transact-sql) </span></span>  
 <span data-ttu-id="2aa08-158">[sys.server_principals (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-server-principals-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2aa08-158">[sys.server_principals &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-principals-transact-sql) </span></span>  
 <span data-ttu-id="2aa08-159">[sys.sql_logins (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-sql-logins-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2aa08-159">[sys.sql_logins &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-logins-transact-sql) </span></span>  
 <span data-ttu-id="2aa08-160">[sys.database_role_members (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-database-role-members-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2aa08-160">[sys.database_role_members &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-role-members-transact-sql) </span></span>  
 <span data-ttu-id="2aa08-161">[服务器级别角色](server-level-roles.md) </span><span class="sxs-lookup"><span data-stu-id="2aa08-161">[Server-Level Roles](server-level-roles.md) </span></span>  
 [<span data-ttu-id="2aa08-162">数据库级别的角色</span><span class="sxs-lookup"><span data-stu-id="2aa08-162">Database-Level Roles</span></span>](database-level-roles.md)  
  
  
