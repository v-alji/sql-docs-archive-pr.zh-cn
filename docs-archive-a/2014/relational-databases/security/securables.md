---
title: 安全对象 | Microsoft Docs
ms.custom: ''
ms.date: 10/14/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.roleproperties.selectobject.f1
helpviewer_keywords:
- securables [SQL Server]
- schemas [SQL Server], securables
- database securables [SQL Server]
- hierarchies [SQL Server], securables
- server securables [SQL Server]
ms.assetid: bfa748f0-70b0-453c-870a-04b7b205b9ff
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: ff2aaba72e2e5489694d31b35e594622c099acab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688740"
---
# <a name="securables"></a><span data-ttu-id="8eb92-102">安全对象</span><span class="sxs-lookup"><span data-stu-id="8eb92-102">Securables</span></span>
  <span data-ttu-id="8eb92-103">安全对象是 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 授权系统控制对其进行访问的资源。</span><span class="sxs-lookup"><span data-stu-id="8eb92-103">Securables are the resources to which the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] authorization system regulates access.</span></span> <span data-ttu-id="8eb92-104">例如，表是安全对象。</span><span class="sxs-lookup"><span data-stu-id="8eb92-104">For example, a table is a securable.</span></span> <span data-ttu-id="8eb92-105">通过创建可以为自己设置安全性的名为“范围”的嵌套层次结构，可以将某些安全对象包含在其他安全对象中。</span><span class="sxs-lookup"><span data-stu-id="8eb92-105">Some securables can be contained within others, creating nested hierarchies called "scopes" that can themselves be secured.</span></span> <span data-ttu-id="8eb92-106">安全对象范围有 **服务器**、 **数据库**和 **架构**。</span><span class="sxs-lookup"><span data-stu-id="8eb92-106">The securable scopes are **server**, **database**, and **schema**.</span></span>  
  
## <a name="securable-scope-server"></a><span data-ttu-id="8eb92-107">安全对象范围：服务器</span><span class="sxs-lookup"><span data-stu-id="8eb92-107">Securable scope: Server</span></span>  
 <span data-ttu-id="8eb92-108">**服务器** 安全对象范围包含以下安全对象：</span><span class="sxs-lookup"><span data-stu-id="8eb92-108">The **server** securable scope contains the following securables:</span></span>  
  
-   <span data-ttu-id="8eb92-109">可用性组 (availability group)</span><span class="sxs-lookup"><span data-stu-id="8eb92-109">Availability group</span></span>  
  
-   <span data-ttu-id="8eb92-110">端点</span><span class="sxs-lookup"><span data-stu-id="8eb92-110">Endpoint</span></span>  
  
-   <span data-ttu-id="8eb92-111">登录</span><span class="sxs-lookup"><span data-stu-id="8eb92-111">Login</span></span>  
  
-   <span data-ttu-id="8eb92-112">服务器角色</span><span class="sxs-lookup"><span data-stu-id="8eb92-112">Server role</span></span>  
  
-   <span data-ttu-id="8eb92-113">数据库</span><span class="sxs-lookup"><span data-stu-id="8eb92-113">Database</span></span>  
  
## <a name="securable-scope-database"></a><span data-ttu-id="8eb92-114">安全对象范围：数据库</span><span class="sxs-lookup"><span data-stu-id="8eb92-114">Securable scope: Database</span></span>  
 <span data-ttu-id="8eb92-115">**数据库** 安全对象范围包含以下安全对象：</span><span class="sxs-lookup"><span data-stu-id="8eb92-115">The **database** securable scope contains the following securables:</span></span>  
  
-   <span data-ttu-id="8eb92-116">应用程序角色</span><span class="sxs-lookup"><span data-stu-id="8eb92-116">Application role</span></span>  
  
-   <span data-ttu-id="8eb92-117">Assembly</span><span class="sxs-lookup"><span data-stu-id="8eb92-117">Assembly</span></span>  
  
-   <span data-ttu-id="8eb92-118">非对称密钥</span><span class="sxs-lookup"><span data-stu-id="8eb92-118">Asymmetric key</span></span>  
  
-   <span data-ttu-id="8eb92-119">证书</span><span class="sxs-lookup"><span data-stu-id="8eb92-119">Certificate</span></span>  
  
-   <span data-ttu-id="8eb92-120">合约</span><span class="sxs-lookup"><span data-stu-id="8eb92-120">Contract</span></span>  
  
-   <span data-ttu-id="8eb92-121">全文目录</span><span class="sxs-lookup"><span data-stu-id="8eb92-121">Fulltext catalog</span></span>  
  
-   <span data-ttu-id="8eb92-122">全文非索引字表</span><span class="sxs-lookup"><span data-stu-id="8eb92-122">Fulltext stoplist</span></span>  
  
-   <span data-ttu-id="8eb92-123">消息类型</span><span class="sxs-lookup"><span data-stu-id="8eb92-123">Message type</span></span>  
  
-   <span data-ttu-id="8eb92-124">远程服务绑定</span><span class="sxs-lookup"><span data-stu-id="8eb92-124">Remote Service Binding</span></span>  
  
-   <span data-ttu-id="8eb92-125">（数据库）角色</span><span class="sxs-lookup"><span data-stu-id="8eb92-125">(Database) Role</span></span>  
  
-   <span data-ttu-id="8eb92-126">路由</span><span class="sxs-lookup"><span data-stu-id="8eb92-126">Route</span></span>  
  
-   <span data-ttu-id="8eb92-127">架构</span><span class="sxs-lookup"><span data-stu-id="8eb92-127">Schema</span></span>  
  
-   <span data-ttu-id="8eb92-128">搜索属性列表</span><span class="sxs-lookup"><span data-stu-id="8eb92-128">Search property list</span></span>  
  
-   <span data-ttu-id="8eb92-129">服务</span><span class="sxs-lookup"><span data-stu-id="8eb92-129">Service</span></span>  
  
-   <span data-ttu-id="8eb92-130">对称密钥</span><span class="sxs-lookup"><span data-stu-id="8eb92-130">Symmetric key</span></span>  
  
-   <span data-ttu-id="8eb92-131">用户</span><span class="sxs-lookup"><span data-stu-id="8eb92-131">User</span></span>  
  
## <a name="securable-scope-schema"></a><span data-ttu-id="8eb92-132">安全对象范围：架构</span><span class="sxs-lookup"><span data-stu-id="8eb92-132">Securable scope: Schema</span></span>  
 <span data-ttu-id="8eb92-133">**架构** 安全对象范围包含以下安全对象：</span><span class="sxs-lookup"><span data-stu-id="8eb92-133">The **schema** securable scope contains the following securables:</span></span>  
  
-   <span data-ttu-id="8eb92-134">类型</span><span class="sxs-lookup"><span data-stu-id="8eb92-134">Type</span></span>  
  
-   <span data-ttu-id="8eb92-135">XML 架构集合</span><span class="sxs-lookup"><span data-stu-id="8eb92-135">XML schema collection</span></span>  
  
-   <span data-ttu-id="8eb92-136">对象 - 对象类包含以下成员：</span><span class="sxs-lookup"><span data-stu-id="8eb92-136">Object - The object class has the following members:</span></span>  
  
    -   <span data-ttu-id="8eb92-137">聚合</span><span class="sxs-lookup"><span data-stu-id="8eb92-137">Aggregate</span></span>  
  
    -   <span data-ttu-id="8eb92-138">函数</span><span class="sxs-lookup"><span data-stu-id="8eb92-138">Function</span></span>  
  
    -   <span data-ttu-id="8eb92-139">过程</span><span class="sxs-lookup"><span data-stu-id="8eb92-139">Procedure</span></span>  
  
    -   <span data-ttu-id="8eb92-140">队列</span><span class="sxs-lookup"><span data-stu-id="8eb92-140">Queue</span></span>  
  
    -   <span data-ttu-id="8eb92-141">同义词</span><span class="sxs-lookup"><span data-stu-id="8eb92-141">Synonym</span></span>  
  
    -   <span data-ttu-id="8eb92-142">表</span><span class="sxs-lookup"><span data-stu-id="8eb92-142">Table</span></span>  
  
    -   <span data-ttu-id="8eb92-143">查看</span><span class="sxs-lookup"><span data-stu-id="8eb92-143">View</span></span>  
  
## <a name="controlling-access-to-a-securable"></a><span data-ttu-id="8eb92-144">控制对安全对象的访问</span><span class="sxs-lookup"><span data-stu-id="8eb92-144">Controlling Access to a Securable</span></span>  
 <span data-ttu-id="8eb92-145">接收对安全对象的权限的实体称为主体。</span><span class="sxs-lookup"><span data-stu-id="8eb92-145">The entity that receives permission to a securable is called a principal.</span></span> <span data-ttu-id="8eb92-146">最常见的主体是登录名和数据库用户。</span><span class="sxs-lookup"><span data-stu-id="8eb92-146">The most common principals are logins and database users.</span></span> <span data-ttu-id="8eb92-147">对安全对象的访问通过授予或拒绝权限进行控制，或者通过将登录名和用户添加到有权访问的角色进行控制。</span><span class="sxs-lookup"><span data-stu-id="8eb92-147">Access to securables is controlled by granting or denying permissions, or by adding logins and user to roles which have access.</span></span> <span data-ttu-id="8eb92-148">有关控制权限的信息，请参阅 [GRANT (Transact-SQL)](/sql/t-sql/statements/grant-transact-sql)、[REVOKE (Transact-SQL)](/sql/t-sql/statements/revoke-transact-sql)、[DENY (Transact-SQL)](/sql/t-sql/statements/deny-transact-sql)、[sp_addrolemember (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql) 和 [sp_droprolemember (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-droprolemember-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="8eb92-148">For information about controlling permissions, see [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql), [REVOKE &#40;Transact-SQL&#41;](/sql/t-sql/statements/revoke-transact-sql), [DENY &#40;Transact-SQL&#41;](/sql/t-sql/statements/deny-transact-sql), [sp_addrolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql), and [sp_droprolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-droprolemember-transact-sql).</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="8eb92-149">安装期间授予系统对象的默认权限已针对可能的威胁进行了仔细评估，并且作为强化 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安装的一部分，无需进行更改。</span><span class="sxs-lookup"><span data-stu-id="8eb92-149">The default permissions that are granted to system objects at the time of setup are carefully evaluated against possible threats and need not be altered as part of hardening the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installation.</span></span> <span data-ttu-id="8eb92-150">对系统对象权限的任何更改都可能限制或破坏功能，并且可能让你的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安装处于不受支持的状态。</span><span class="sxs-lookup"><span data-stu-id="8eb92-150">Any changes to the permissions on the system objects could limit or break the functionality and could potentially leave your [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installation in an unsupported state.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="8eb92-151">相关内容</span><span class="sxs-lookup"><span data-stu-id="8eb92-151">Related Content</span></span>  
 [<span data-ttu-id="8eb92-152">保护 SQL Server</span><span class="sxs-lookup"><span data-stu-id="8eb92-152">Securing SQL Server</span></span>](securing-sql-server.md)  
  
 [<span data-ttu-id="8eb92-153">sys.database_principals (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="8eb92-153">sys.database_principals &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-database-principals-transact-sql)  
  
 [<span data-ttu-id="8eb92-154">sys.database_role_members (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="8eb92-154">sys.database_role_members &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-database-role-members-transact-sql)  
  
 [<span data-ttu-id="8eb92-155">sys.server_principals (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="8eb92-155">sys.server_principals &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-server-principals-transact-sql)  
  
 [<span data-ttu-id="8eb92-156">sys.server_role_members (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="8eb92-156">sys.server_role_members &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-server-role-members-transact-sql)  
  
 [<span data-ttu-id="8eb92-157">sys.sql_logins (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="8eb92-157">sys.sql_logins &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-sql-logins-transact-sql)  
  
  
