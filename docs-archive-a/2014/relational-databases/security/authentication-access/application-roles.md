---
title: 应用程序角色 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- application roles [SQL Server], about application roles
- principals [SQL Server], application roles
- credentials [SQL Server], roles
- application roles [SQL Server]
- roles [SQL Server], application
- permissions [SQL Server], roles
- users [SQL Server], application roles
- authentication [SQL Server], roles
- groups [SQL Server], roles
ms.assetid: dca18b8a-ca03-4b7f-9a46-8474d5b66f76
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: f2fcc7b1e333bb42a00675da5bb9fd559d1c34f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578763"
---
# <a name="application-roles"></a><span data-ttu-id="09ed8-102">应用程序角色</span><span class="sxs-lookup"><span data-stu-id="09ed8-102">Application Roles</span></span>
  <span data-ttu-id="09ed8-103">应用程序角色是一个数据库主体，它使应用程序能够用其自身的、类似用户的权限来运行。</span><span class="sxs-lookup"><span data-stu-id="09ed8-103">An application role is a database principal that enables an application to run with its own, user-like permissions.</span></span> <span data-ttu-id="09ed8-104">使用应用程序角色，可以只允许通过特定应用程序连接的用户访问特定数据。</span><span class="sxs-lookup"><span data-stu-id="09ed8-104">You can use application roles to enable access to specific data to only those users who connect through a particular application.</span></span> <span data-ttu-id="09ed8-105">与数据库角色不同的是，应用程序角色默认情况下不包含任何成员，而且是非活动的。</span><span class="sxs-lookup"><span data-stu-id="09ed8-105">Unlike database roles, application roles contain no members and are inactive by default.</span></span> <span data-ttu-id="09ed8-106">应用程序角色使用两种身份验证模式。</span><span class="sxs-lookup"><span data-stu-id="09ed8-106">Application roles work with both authentication modes.</span></span> <span data-ttu-id="09ed8-107">可以使用 **sp_setapprole**启用应用程序角色，该过程需要密码。</span><span class="sxs-lookup"><span data-stu-id="09ed8-107">Application roles are enabled by using **sp_setapprole**, which requires a password.</span></span> <span data-ttu-id="09ed8-108">因为应用程序角色是数据库级主体，所以它们只能通过其他数据库中为 **guest**授予的权限来访问这些数据库。</span><span class="sxs-lookup"><span data-stu-id="09ed8-108">Because application roles are a database-level principal, they can access other databases only through permissions granted in those databases to **guest**.</span></span> <span data-ttu-id="09ed8-109">因此，其他数据库中的应用程序角色将无法访问任何已禁用 **guest** 的数据库。</span><span class="sxs-lookup"><span data-stu-id="09ed8-109">Therefore, any database in which **guest** has been disabled will be inaccessible to application roles in other databases.</span></span>  
  
 <span data-ttu-id="09ed8-110">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]中，应用程序角色无法访问服务器级元数据，因为它们不与服务器级主体关联。</span><span class="sxs-lookup"><span data-stu-id="09ed8-110">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], application roles cannot access server-level metadata because they are not associated with a server-level principal.</span></span> <span data-ttu-id="09ed8-111">若要禁用此限制，从而允许应用程序角色访问服务器级元数据，请设置全局标志 4616。</span><span class="sxs-lookup"><span data-stu-id="09ed8-111">To disable this restriction and thereby allow application roles to access server-level metadata, set the global flag 4616.</span></span> <span data-ttu-id="09ed8-112">有关详细信息，请参阅[跟踪标志 (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql) 和 [DBCC TRACEON (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-traceon-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="09ed8-112">For more information, see [Trace Flags &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql) and [DBCC TRACEON &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-transact-sql).</span></span>  
  
## <a name="connecting-with-an-application-role"></a><span data-ttu-id="09ed8-113">连接应用程序角色</span><span class="sxs-lookup"><span data-stu-id="09ed8-113">Connecting with an Application Role</span></span>  
 <span data-ttu-id="09ed8-114">应用程序角色切换安全上下文的过程包括下列步骤：</span><span class="sxs-lookup"><span data-stu-id="09ed8-114">The following steps make up the process by which an application role switches security contexts:</span></span>  
  
1.  <span data-ttu-id="09ed8-115">用户执行客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="09ed8-115">A user executes a client application.</span></span>  
  
2.  <span data-ttu-id="09ed8-116">客户端应用程序作为用户连接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="09ed8-116">The client application connects to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] as the user.</span></span>  
  
3.  <span data-ttu-id="09ed8-117">然后应用程序用一个只有它才知道的密码执行 **sp_setapprole** 存储过程。</span><span class="sxs-lookup"><span data-stu-id="09ed8-117">The application then executes the **sp_setapprole** stored procedure with a password known only to the application.</span></span>  
  
4.  <span data-ttu-id="09ed8-118">如果应用程序角色名称和密码都有效，则启用应用程序角色。</span><span class="sxs-lookup"><span data-stu-id="09ed8-118">If the application role name and password are valid, the application role is enabled.</span></span>  
  
5.  <span data-ttu-id="09ed8-119">此时，连接将失去用户权限，而获得应用程序角色权限。</span><span class="sxs-lookup"><span data-stu-id="09ed8-119">At this point the connection loses the permissions of the user and assumes the permissions of the application role.</span></span>  
  
 <span data-ttu-id="09ed8-120">通过应用程序角色获得的权限在连接期间始终有效。</span><span class="sxs-lookup"><span data-stu-id="09ed8-120">The permissions acquired through the application role remain in effect for the duration of the connection.</span></span>  
  
 <span data-ttu-id="09ed8-121">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]的早期版本中，用户若要在启动应用程序角色后重新获取其原始安全上下文，唯一的方法就是断开 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]连接，然后再重新连接。</span><span class="sxs-lookup"><span data-stu-id="09ed8-121">In earlier versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the only way for a user to reacquire its original security context after starting an application role is to disconnect and reconnect to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="09ed8-122">从 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]开始， **sp_setapprole** 有了一个可创建 Cookie 的选项。</span><span class="sxs-lookup"><span data-stu-id="09ed8-122">Beginning with [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], **sp_setapprole** has an option that creates a cookie.</span></span> <span data-ttu-id="09ed8-123">Cookie 包含启用应用程序角色之前的上下文信息。</span><span class="sxs-lookup"><span data-stu-id="09ed8-123">The cookie contains context information before the application role is enabled.</span></span> <span data-ttu-id="09ed8-124">**sp_unsetapprole** 可以使用此 Cookie 将会话还原到其原始上下文。</span><span class="sxs-lookup"><span data-stu-id="09ed8-124">The cookie can be used by **sp_unsetapprole** to revert the session to its original context.</span></span> <span data-ttu-id="09ed8-125">有关此新选项和示例的信息，请参阅 [sp_setapprole (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-setapprole-transact-sql)授予的权限来访问这些数据库。</span><span class="sxs-lookup"><span data-stu-id="09ed8-125">For information about this new option and an example, see [sp_setapprole &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-setapprole-transact-sql).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="09ed8-126">**SqlClient** 不支持 ODBC **encrypt**选项。</span><span class="sxs-lookup"><span data-stu-id="09ed8-126">The ODBC **encrypt** option is not supported by **SqlClient**.</span></span> <span data-ttu-id="09ed8-127">通过网络传输机密信息时，请使用安全套接字层 (SSL) 或 IPSec 对通道进行加密。</span><span class="sxs-lookup"><span data-stu-id="09ed8-127">When you are transmitting confidential information over a network, use Secure Sockets Layer (SSL) or IPsec to encrypt the channel.</span></span> <span data-ttu-id="09ed8-128">如果必须使凭据在客户端应用程序中持久化，请使用加密 API 函数来加密凭据。</span><span class="sxs-lookup"><span data-stu-id="09ed8-128">If you must persist credentials in the client application, encrypt the credentials by using the crypto API functions.</span></span> <span data-ttu-id="09ed8-129">在 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 及更高版本中，参数 *password* 将作为单向哈希进行存储。</span><span class="sxs-lookup"><span data-stu-id="09ed8-129">In [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] and later versions, the parameter *password* is stored as a one-way hash.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="09ed8-130">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="09ed8-130">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="09ed8-131">创建应用程序角色。</span><span class="sxs-lookup"><span data-stu-id="09ed8-131">Create an application role.</span></span>|<span data-ttu-id="09ed8-132">[创建应用程序角色](create-an-application-role.md)和 [CREATE APPLICATION ROLE (Transact-SQL)](/sql/t-sql/statements/create-application-role-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="09ed8-132">[Create an Application Role](create-an-application-role.md) and [CREATE APPLICATION ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-application-role-transact-sql)</span></span>|  
|<span data-ttu-id="09ed8-133">更改应用程序角色。</span><span class="sxs-lookup"><span data-stu-id="09ed8-133">Alter an application role.</span></span>|[<span data-ttu-id="09ed8-134">ALTER APPLICATION ROLE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="09ed8-134">ALTER APPLICATION ROLE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-application-role-transact-sql)|  
|<span data-ttu-id="09ed8-135">删除应用程序角色。</span><span class="sxs-lookup"><span data-stu-id="09ed8-135">Delete an application role.</span></span>|[<span data-ttu-id="09ed8-136">DROP APPLICATION ROLE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="09ed8-136">DROP APPLICATION ROLE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-application-role-transact-sql)|  
|<span data-ttu-id="09ed8-137">使用应用程序角色。</span><span class="sxs-lookup"><span data-stu-id="09ed8-137">Using an application role.</span></span>|[<span data-ttu-id="09ed8-138">sp_setapprole (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="09ed8-138">sp_setapprole &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-setapprole-transact-sql)|  
  
## <a name="see-also"></a><span data-ttu-id="09ed8-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="09ed8-139">See Also</span></span>  
 [<span data-ttu-id="09ed8-140">保护 SQL Server</span><span class="sxs-lookup"><span data-stu-id="09ed8-140">Securing SQL Server</span></span>](../securing-sql-server.md)  
  
  
