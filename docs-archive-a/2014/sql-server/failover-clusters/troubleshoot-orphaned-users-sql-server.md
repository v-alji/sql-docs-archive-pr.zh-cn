---
title: 孤立用户故障排除 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- orphaned users [SQL Server]
- logins [SQL Server], orphaned users
- troubleshooting [SQL Server], user accounts
- user accounts [SQL Server], orphaned users
- failover [SQL Server], managing metadata
- database mirroring [SQL Server], metadata
- users [SQL Server], orphaned
ms.assetid: 11eefa97-a31f-4359-ba5b-e92328224133
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5df714d818949b921ff2236e50d58913eab0e0db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586277"
---
# <a name="troubleshoot-orphaned-users-sql-server"></a><span data-ttu-id="39271-102">孤立用户故障排除 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="39271-102">Troubleshoot Orphaned Users (SQL Server)</span></span>
  <span data-ttu-id="39271-103">要登录到 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例，主体必须有一个有效的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名。</span><span class="sxs-lookup"><span data-stu-id="39271-103">To log into an instance of Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], a principal must have a valid [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span> <span data-ttu-id="39271-104">在身份验证过程中会使用此登录名，以验证是否允许主体连接到该 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="39271-104">This login is used in the authentication process that verifies whether the principal is allowed to connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="39271-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]服务器实例上的登录名在**server_principals**目录视图和**sys.sys登录**兼容性视图中可见。</span><span class="sxs-lookup"><span data-stu-id="39271-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins on a server instance are visible in the **sys.server_principals** catalog view and the **sys.syslogins** compatibility view.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="39271-106">登录名使用映射到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名的数据库用户访问各个数据库。</span><span class="sxs-lookup"><span data-stu-id="39271-106">logins access individual databases using a database user that is mapped to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span> <span data-ttu-id="39271-107">此规则有两种例外情况：</span><span class="sxs-lookup"><span data-stu-id="39271-107">There are two exceptions to this rule:</span></span>  
  
-   <span data-ttu-id="39271-108">guest 帐户。</span><span class="sxs-lookup"><span data-stu-id="39271-108">The guest account.</span></span>  
  
     <span data-ttu-id="39271-109">这个帐户在数据库中启用后，能够使未映射到数据库用户的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名作为 guest 用户进入数据库。</span><span class="sxs-lookup"><span data-stu-id="39271-109">This is an account that, when enabled in the database, enables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins that are not mapped to a database user to enter the database as the guest user.</span></span>  
  
-   <span data-ttu-id="39271-110">Microsoft Windows 组成员身份。</span><span class="sxs-lookup"><span data-stu-id="39271-110">Microsoft Windows group memberships.</span></span>  
  
     <span data-ttu-id="39271-111">如果某 Windows 用户是 Windows 组的成员，并且此组也是数据库中的用户，则基于该 Windows 用户创建的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名可以进入数据库。</span><span class="sxs-lookup"><span data-stu-id="39271-111">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login created from a Windows user can enter a database if the Windows user is a member of a Windows group that is also a user in the database.</span></span>  
  
 <span data-ttu-id="39271-112">有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名与数据库用户的映射关系的信息存储在数据库中。</span><span class="sxs-lookup"><span data-stu-id="39271-112">Information about the mapping of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to a database user is stored within the database.</span></span> <span data-ttu-id="39271-113">其中包括数据库用户的名称以及对应 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名的 SID。</span><span class="sxs-lookup"><span data-stu-id="39271-113">It includes the name of the database user and the SID of the corresponding [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span> <span data-ttu-id="39271-114">该数据库用户的权限用于在数据库中进行授权。</span><span class="sxs-lookup"><span data-stu-id="39271-114">The permissions of this database user are used for authorization in the database.</span></span>  
  
 <span data-ttu-id="39271-115">在服务器实例上未定义或错误定义了其相应 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名的数据库用户无法登录到实例。</span><span class="sxs-lookup"><span data-stu-id="39271-115">A database user for which the corresponding [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login is undefined or is incorrectly defined on a server instance cannot log in to the instance.</span></span> <span data-ttu-id="39271-116">这样的用户被称为此服务器实例上的数据库的“孤立用户” \*\* 。</span><span class="sxs-lookup"><span data-stu-id="39271-116">Such a user is said to be an *orphaned user* of the database on that server instance.</span></span> <span data-ttu-id="39271-117">如果删除了对应的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名，则数据库用户可能会变为孤立用户。</span><span class="sxs-lookup"><span data-stu-id="39271-117">A database user can become orphaned if the corresponding [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login is dropped.</span></span> <span data-ttu-id="39271-118">另外，在数据库还原或附加到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的其他实例之后，数据库用户也可能变为孤立用户。</span><span class="sxs-lookup"><span data-stu-id="39271-118">Also, a database user can become orphaned after a database is restored or attached to a different instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="39271-119">如果未在新服务器实例中提供数据库用户映射到的 SID，则该用户可能变为孤立用户。</span><span class="sxs-lookup"><span data-stu-id="39271-119">Orphaning can happen if the database user is mapped to a SID that is not present in the new server instance.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="39271-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]除非在数据库中启用了**guest** ，否则登录名无法访问其缺少相应的数据库用户的数据库。</span><span class="sxs-lookup"><span data-stu-id="39271-120">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login cannot access a database in which it lacks a corresponding database user unless **guest** is enabled in that database.</span></span> <span data-ttu-id="39271-121">有关创建数据库用户帐户的信息，请参阅[CREATE user &#40;transact-sql&#41;](/sql/t-sql/statements/create-user-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="39271-121">For information about creating a database user account, see [CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql).</span></span>  
  
## <a name="to-detect-orphaned-users"></a><span data-ttu-id="39271-122">检测孤立用户</span><span class="sxs-lookup"><span data-stu-id="39271-122">To Detect Orphaned Users</span></span>  
 <span data-ttu-id="39271-123">若要检测孤立用户，请执行下列 Transact-SQL 语句：</span><span class="sxs-lookup"><span data-stu-id="39271-123">To detect orphaned users, execute the following Transact-SQL statements:</span></span>  
  
```  
USE <database_name>;  
GO;   
sp_change_users_login @Action='Report';  
GO;  
```  
  
 <span data-ttu-id="39271-124">输出中列出了当前数据库中未链接到任何 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名的用户以及对应的安全标识符 (SID)。</span><span class="sxs-lookup"><span data-stu-id="39271-124">The output lists the users and corresponding security identifiers (SID) in the current database that are not linked to any [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span> <span data-ttu-id="39271-125">有关详细信息，请参阅[&#40;transact-sql&#41;sp_change_users_login ](/sql/relational-databases/system-stored-procedures/sp-change-users-login-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="39271-125">For more information, see [sp_change_users_login &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-change-users-login-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="39271-126">**sp_change_users_login**不能与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 通过 Windows 创建的登录名一起使用。</span><span class="sxs-lookup"><span data-stu-id="39271-126">**sp_change_users_login** cannot be used with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins that are created from Windows.</span></span>  
  
## <a name="to-resolve-an-orphaned-user"></a><span data-ttu-id="39271-127">解决孤立用户问题</span><span class="sxs-lookup"><span data-stu-id="39271-127">To Resolve an Orphaned User</span></span>  
 <span data-ttu-id="39271-128">若要解决孤立用户问题，请执行以下过程：</span><span class="sxs-lookup"><span data-stu-id="39271-128">To resolve an orphaned user, use the following procedure:</span></span>  
  
1.  <span data-ttu-id="39271-129">以下命令将 *<>login_name*指定的服务器登录帐户与 *<database_user>* 指定的数据库用户重新链接。</span><span class="sxs-lookup"><span data-stu-id="39271-129">The following command relinks the server login account specified by *<login_name>* with the database user specified by *<database_user>*.</span></span>  
  
    ```  
    USE <database_name>;  
    GO  
    sp_change_users_login @Action='update_one', @UserNamePattern='<database_user>', @LoginName='<login_name>';  
    GO  
  
    ```  
  
     <span data-ttu-id="39271-130">有关详细信息，请参阅[&#40;transact-sql&#41;sp_change_users_login ](/sql/relational-databases/system-stored-procedures/sp-change-users-login-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="39271-130">For more information, see [sp_change_users_login &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-change-users-login-transact-sql).</span></span>  
  
2.  <span data-ttu-id="39271-131">运行上述步骤中的代码后，该用户就可以访问数据库了。</span><span class="sxs-lookup"><span data-stu-id="39271-131">After you run the code in the preceding step, the user can access the database.</span></span> <span data-ttu-id="39271-132">然后，用户可以使用**sp_password**存储过程来更改 *<login_name>* 登录帐户的密码，如下所示：</span><span class="sxs-lookup"><span data-stu-id="39271-132">The user then can alter the password of the *<login_name>* login account by using the **sp_password** stored procedure, as follows:</span></span>  
  
    ```  
    USE master   
    GO  
    sp_password @old=NULL, @new='password', @loginame='<login_name>';  
    GO  
    ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="39271-133">只有具有 ALTER ANY LOGIN 权限的登录帐户才能更改其他用户的登录密码。</span><span class="sxs-lookup"><span data-stu-id="39271-133">Only logins with the ALTER ANY LOGIN permission can change the password of another user's login.</span></span> <span data-ttu-id="39271-134">但是，只有 **sysadmin** 角色的成员才能修改 **sysadmin** 角色成员的密码。</span><span class="sxs-lookup"><span data-stu-id="39271-134">However, only members of the **sysadmin** role can modify passwords of **sysadmin** role members.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="39271-135">不能将**sp_password**用于 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 帐户。</span><span class="sxs-lookup"><span data-stu-id="39271-135">**sp_password** cannot be used for [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows accounts.</span></span> <span data-ttu-id="39271-136">通过 Windows 网络帐户连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的用户是由 Windows 进行身份验证的，因此其密码只能在 Windows 中更改。</span><span class="sxs-lookup"><span data-stu-id="39271-136">Users connecting to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] through their Windows network account are authenticated by Windows; therefore, their passwords can only be changed in Windows.</span></span>  
  
     <span data-ttu-id="39271-137">有关详细信息，请参阅[&#40;transact-sql&#41;sp_password ](/sql/relational-databases/system-stored-procedures/sp-password-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="39271-137">For more information, see [sp_password &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-password-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39271-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="39271-138">See Also</span></span>  
 <span data-ttu-id="39271-139">[CREATE USER (Transact-SQL)](/sql/t-sql/statements/create-user-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="39271-139">[CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql) </span></span>  
 <span data-ttu-id="39271-140">[CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="39271-140">[CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql) </span></span>  
 <span data-ttu-id="39271-141">[sp_change_users_login &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-change-users-login-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="39271-141">[sp_change_users_login &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-change-users-login-transact-sql) </span></span>  
 <span data-ttu-id="39271-142">[sp_addlogin (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addlogin-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="39271-142">[sp_addlogin &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogin-transact-sql) </span></span>  
 <span data-ttu-id="39271-143">[sp_grantlogin &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-grantlogin-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="39271-143">[sp_grantlogin &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-grantlogin-transact-sql) </span></span>  
 <span data-ttu-id="39271-144">[sp_password &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-password-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="39271-144">[sp_password &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-password-transact-sql) </span></span>  
 <span data-ttu-id="39271-145">[sys.sys用户 &#40;Transact-sql&#41;](/sql/relational-databases/system-compatibility-views/sys-sysusers-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="39271-145">[sys.sysusers &#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-sysusers-transact-sql) </span></span>  
 [<span data-ttu-id="39271-146">Transact-sql&#41;sys.sys登录名 &#40;</span><span class="sxs-lookup"><span data-stu-id="39271-146">sys.syslogins &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-compatibility-views/sys-syslogins-transact-sql)  
  
  
