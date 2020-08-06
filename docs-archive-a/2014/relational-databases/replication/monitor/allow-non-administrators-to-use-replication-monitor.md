---
title: 允许非管理员使用复制监视器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Replication Monitor, non-administrators access
ms.assetid: 1cf21d9e-831d-41a1-a5a0-83ff6d22fa86
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f4a7699c555086d627e4c3a52ea70acf931ea1af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580134"
---
# <a name="allow-non-administrators-to-use-replication-monitor"></a><span data-ttu-id="0be49-102">允许非管理员使用复制监视器</span><span class="sxs-lookup"><span data-stu-id="0be49-102">Allow Non-Administrators to Use Replication Monitor</span></span>
  <span data-ttu-id="0be49-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中允许非管理员使用复制监视器。</span><span class="sxs-lookup"><span data-stu-id="0be49-103">This topic describes how to allow non-administrators to use Replication Monitor in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="0be49-104">属于下列角色成员的用户可以使用复制监视器：</span><span class="sxs-lookup"><span data-stu-id="0be49-104">Replication Monitor can be used by users who are members of the following roles:</span></span>  
  
-   <span data-ttu-id="0be49-105">**sysadmin** 固定服务器角色。</span><span class="sxs-lookup"><span data-stu-id="0be49-105">The **sysadmin** fixed server role.</span></span>  
  
     <span data-ttu-id="0be49-106">这些用户可以监视复制，并对更改复制属性（如代理计划、代理配置文件等）拥有完全控制权。</span><span class="sxs-lookup"><span data-stu-id="0be49-106">These users can monitor replication and have full control over changing replication properties such as agent schedules, agent profiles, and so on.</span></span>  
  
-   <span data-ttu-id="0be49-107">`replmonitor`分发数据库中的数据库角色。</span><span class="sxs-lookup"><span data-stu-id="0be49-107">The `replmonitor` database role in the distribution database.</span></span>  
  
     <span data-ttu-id="0be49-108">这些用户可以监视复制，但不能更改任何复制属性。</span><span class="sxs-lookup"><span data-stu-id="0be49-108">These users can monitor replication, but cannot change any replication properties.</span></span>  
  
 <span data-ttu-id="0be49-109">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="0be49-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="0be49-110">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="0be49-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="0be49-111">安全性</span><span class="sxs-lookup"><span data-stu-id="0be49-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="0be49-112">**允许非管理员使用复制监视器，使用：**</span><span class="sxs-lookup"><span data-stu-id="0be49-112">**To allow non-administrators to use Replication Monitor, using:**</span></span>  
  
     [<span data-ttu-id="0be49-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0be49-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="0be49-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0be49-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0be49-115">开始之前</span><span class="sxs-lookup"><span data-stu-id="0be49-115">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0be49-116">Security</span><span class="sxs-lookup"><span data-stu-id="0be49-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="0be49-117">权限</span><span class="sxs-lookup"><span data-stu-id="0be49-117">Permissions</span></span>  
 <span data-ttu-id="0be49-118">若要允许非管理员使用复制监视器， **sysadmin**固定服务器角色的成员必须将用户添加到分发数据库，并将该用户分配给该 `replmonitor` 角色。</span><span class="sxs-lookup"><span data-stu-id="0be49-118">To allow non-administrators to use Replication Monitor, a member of the **sysadmin** fixed server role must add the user to the distribution database and assign that user to the `replmonitor` role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="0be49-119">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0be49-119">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-allow-non-administrators-to-use-replication-monitor"></a><span data-ttu-id="0be49-120">允许非管理员使用复制监视器</span><span class="sxs-lookup"><span data-stu-id="0be49-120">To allow non-administrators to use Replication Monitor</span></span>  
  
1.  <span data-ttu-id="0be49-121">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]中，连接到分发服务器，然后展开服务器节点。</span><span class="sxs-lookup"><span data-stu-id="0be49-121">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], connect to the Distributor, and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="0be49-122">依次展开 **“数据库”**、 **“系统数据库”** 和分发数据库（默认名称为 **distribution** ）。</span><span class="sxs-lookup"><span data-stu-id="0be49-122">Expand **Databases**, expand **System Databases**, and then expand the distribution database (named **distribution** by default).</span></span>  
  
3.  <span data-ttu-id="0be49-123">展开 **“安全性”**，右键单击 **“用户”**，然后单击 **“新建用户”**。</span><span class="sxs-lookup"><span data-stu-id="0be49-123">Expand **Security**, right-click **Users**, and then click **New User**.</span></span>  
  
4.  <span data-ttu-id="0be49-124">输入用户名和用户的登录名。</span><span class="sxs-lookup"><span data-stu-id="0be49-124">Enter a user name and login for the user.</span></span>  
  
5.  <span data-ttu-id="0be49-125">选择的默认架构 `replmonitor` 。</span><span class="sxs-lookup"><span data-stu-id="0be49-125">Select a default schema of `replmonitor`.</span></span>  
  
6.  <span data-ttu-id="0be49-126">选中 " `replmonitor` **数据库角色成员身份**" 网格中的复选框。</span><span class="sxs-lookup"><span data-stu-id="0be49-126">Select the `replmonitor` check box in the **Database role membership** grid.</span></span>  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="0be49-127">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0be49-127">Using Transact-SQL</span></span>  
  
#### <a name="to-add-a-user-to-the-replmonitor-fixed-database-role"></a><span data-ttu-id="0be49-128">将用户添加到 replmonitor 固定数据库角色</span><span class="sxs-lookup"><span data-stu-id="0be49-128">To add a user to the replmonitor fixed database role</span></span>  
  
1.  <span data-ttu-id="0be49-129">在分发服务器上，对分发数据库执行 [sp_helpuser &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpuser-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="0be49-129">At the Distributor on the distribution database, execute [sp_helpuser &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpuser-transact-sql).</span></span> <span data-ttu-id="0be49-130">如果结果集中未列出该用户 `UserName` ，则必须使用[CREATE User &#40;transact-sql&#41;](/sql/t-sql/statements/create-user-transact-sql)语句授予该用户访问分发数据库的权限。</span><span class="sxs-lookup"><span data-stu-id="0be49-130">If the user is not listed in `UserName` in the result set, the user must be granted access to the distribution database using the [CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql) statement.</span></span>  
  
2.  <span data-ttu-id="0be49-131">在分发服务器上，对分发数据库执行[sp_helprolemember &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-helprolemember-transact-sql)，并 `replmonitor` 为参数指定值 **@rolename** 。</span><span class="sxs-lookup"><span data-stu-id="0be49-131">At the Distributor on the distribution database, execute [sp_helprolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helprolemember-transact-sql), specifying a value of `replmonitor` for the **@rolename** parameter.</span></span> <span data-ttu-id="0be49-132">如果用户已在结果集中的中列出 `MemberName` ，则该用户已属于此角色。</span><span class="sxs-lookup"><span data-stu-id="0be49-132">If the user is listed in `MemberName` in the result set, the user already belongs to this role.</span></span>  
  
3.  <span data-ttu-id="0be49-133">如果用户不属于 `replmonitor` 角色，请在分发服务器上的分发数据库中执行[Sp_addrolemember &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="0be49-133">If the user does not belong to the `replmonitor` role, execute [sp_addrolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql) at the Distributor on the distribution database.</span></span> <span data-ttu-id="0be49-134">将的值指定 `replmonitor` 为 **@rolename** ，并指定 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 要为其添加的数据库用户或 Windows 登录名 **@membername** 。</span><span class="sxs-lookup"><span data-stu-id="0be49-134">Specify a value of `replmonitor` for **@rolename** and the name of the database user or the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows login being added for **@membername**.</span></span>  
  
#### <a name="to-remove-a-user-from-the-replmonitor-fixed-database-role"></a><span data-ttu-id="0be49-135">从 replmonitor 固定数据库角色中删除用户</span><span class="sxs-lookup"><span data-stu-id="0be49-135">To remove a user from the replmonitor fixed database role</span></span>  
  
1.  <span data-ttu-id="0be49-136">若要验证用户是否属于该 `replmonitor` 角色，请在分发服务器上的分发数据库中执行[Sp_helprolemember &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-helprolemember-transact-sql) ，并将的值指定 `replmonitor` 为 **@rolename** 。</span><span class="sxs-lookup"><span data-stu-id="0be49-136">To verify that the user belongs to the `replmonitor` role, execute [sp_helprolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helprolemember-transact-sql) at the Distributor on the distribution database, and specify a value of `replmonitor` for **@rolename**.</span></span> <span data-ttu-id="0be49-137">如果在结果集中的 `MemberName` 中未列出此用户，则此用户当前不属于此角色。</span><span class="sxs-lookup"><span data-stu-id="0be49-137">If the user is not listed in `MemberName` in the result set, the user does not currently belong to this role.</span></span>  
  
2.  <span data-ttu-id="0be49-138">如果用户属于 `replmonitor` 角色，请在分发服务器上的分发数据库中执行[Sp_droprolemember &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-droprolemember-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="0be49-138">If the user does belong to the `replmonitor` role, execute [sp_droprolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-droprolemember-transact-sql) at the Distributor on the distribution database.</span></span> <span data-ttu-id="0be49-139">将的值指定 `replmonitor` 为 **@rolename** ，并指定要删除的数据库用户或 Windows 登录名 **@membername** 。</span><span class="sxs-lookup"><span data-stu-id="0be49-139">Specify a value of `replmonitor` for **@rolename** and the name of the database user or the Windows login being removed for **@membername**.</span></span>  
  
  
