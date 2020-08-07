---
title: 创建服务器角色 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.serverrole.members.f1
- SQL12.SWB.SERVERROLE.GENERAL.F1
- sql12.swb.serverrole.memberships.f1
helpviewer_keywords:
- SERVER ROLE, creating
ms.assetid: 74f19992-8082-4ed7-92a1-04fe676ee82d
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 45c3d5bb9c9c7fdae9abe18ab3cb808cae4c1fa1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589483"
---
# <a name="create-a-server-role"></a><span data-ttu-id="b36dc-102">创建服务器角色</span><span class="sxs-lookup"><span data-stu-id="b36dc-102">Create a Server Role</span></span>
  <span data-ttu-id="b36dc-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中创建新的服务器角色。</span><span class="sxs-lookup"><span data-stu-id="b36dc-103">This topic describes how to create a new server role in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="b36dc-104">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="b36dc-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b36dc-105">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="b36dc-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b36dc-106">限制和局限</span><span class="sxs-lookup"><span data-stu-id="b36dc-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="b36dc-107">安全性</span><span class="sxs-lookup"><span data-stu-id="b36dc-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="b36dc-108">**若要创建新的服务器角色，请使用：**</span><span class="sxs-lookup"><span data-stu-id="b36dc-108">**To create a new server role, using:**</span></span>  
  
     [<span data-ttu-id="b36dc-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b36dc-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="b36dc-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b36dc-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b36dc-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="b36dc-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="b36dc-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="b36dc-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="b36dc-113">不能向服务器角色授予对数据库级安全对象的权限。</span><span class="sxs-lookup"><span data-stu-id="b36dc-113">Server roles cannot be granted permission on database-level securables.</span></span> <span data-ttu-id="b36dc-114">若要创建数据库角色，请参阅 [CREATE ROLE (Transact-SQL)](/sql/t-sql/statements/create-role-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b36dc-114">To create database roles, see [CREATE ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-role-transact-sql).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b36dc-115">Security</span><span class="sxs-lookup"><span data-stu-id="b36dc-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b36dc-116">权限</span><span class="sxs-lookup"><span data-stu-id="b36dc-116">Permissions</span></span>  
  
-   <span data-ttu-id="b36dc-117">要求具有 CREATE SERVER ROLE 权限，或者 sysadmin 固定服务器角色中的成员身份。</span><span class="sxs-lookup"><span data-stu-id="b36dc-117">Requires CREATE SERVER ROLE permission or membership in the sysadmin fixed server role.</span></span>  
  
-   <span data-ttu-id="b36dc-118">还需要针对登录名的 *server_principal* 的 IMPERSONATE 权限、针对用作 *server_principal*的服务器角色的 ALTER 权限或用作 server_principal 的 Windows 组的成员身份。</span><span class="sxs-lookup"><span data-stu-id="b36dc-118">Also requires IMPERSONATE on the *server_principal* for logins, ALTER permission for server roles used as the *server_principal*, or membership in a Windows group that is used as the server_principal.</span></span>  
  
-   <span data-ttu-id="b36dc-119">使用 AUTHORIZATION 选项分配服务器角色所有权时，还需要具有下列权限：</span><span class="sxs-lookup"><span data-stu-id="b36dc-119">When you use the AUTHORIZATION option to assign server role ownership, the following permissions are also required:</span></span>  
  
    -   <span data-ttu-id="b36dc-120">若要将服务器角色的所有权分配给另一个登录名，则需要对该登录名具有 IMPERSONATE 权限。</span><span class="sxs-lookup"><span data-stu-id="b36dc-120">To assign ownership of a server role to another login, requires IMPERSONATE permission on that login.</span></span>  
  
    -   <span data-ttu-id="b36dc-121">若要将服务器角色的所有权分配给另一个服务器角色，则需要具有被分配服务器角色的成员身份或对该服务器角色具有 ALTER 权限。</span><span class="sxs-lookup"><span data-stu-id="b36dc-121">To assign ownership of a server role to another server role, requires membership in the recipient server role or ALTER permission on that server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b36dc-122">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b36dc-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-new-server-role"></a><span data-ttu-id="b36dc-123">创建新的服务器角色</span><span class="sxs-lookup"><span data-stu-id="b36dc-123">To create a new server role</span></span>  
  
1.  <span data-ttu-id="b36dc-124">在“对象资源管理器”中，展开要创建新的服务器角色的服务器。</span><span class="sxs-lookup"><span data-stu-id="b36dc-124">In Object Explorer, expand the server where you want to create the new server role.</span></span>  
  
2.  <span data-ttu-id="b36dc-125">展开 **“安全性”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="b36dc-125">Expand the **Security** folder.</span></span>  
  
3.  <span data-ttu-id="b36dc-126">右键单击“服务器角色”文件夹，然后选择“新建服务器角色…” 。</span><span class="sxs-lookup"><span data-stu-id="b36dc-126">Right-click the **Server Roles** folder and select **New Server Role...**.</span></span>  
  
4.  <span data-ttu-id="b36dc-127">在 "**新建服务器角色-**_server_role_name_ " 对话框中的 "**常规**" 页上，在 "**服务器角色名称**" 框中输入新服务器角色的名称。</span><span class="sxs-lookup"><span data-stu-id="b36dc-127">In the **New Server Role -**_server_role_name_ dialog box, on the **General** page, enter a name for the new server role in the **Server role name** box.</span></span>  
  
5.  <span data-ttu-id="b36dc-128">在 **“所有者”** 框中，输入拥有新角色的服务器主体的名称。</span><span class="sxs-lookup"><span data-stu-id="b36dc-128">In the **Owner** box, enter the name of the server principal that will own the new role.</span></span> <span data-ttu-id="b36dc-129">或者，单击省略号 (…) 打开“选择服务器登录名或角色”对话框 。</span><span class="sxs-lookup"><span data-stu-id="b36dc-129">Alternately, click the ellipsis **(...)** to open the **Select Server Login or Role** dialog box.</span></span>  
  
6.  <span data-ttu-id="b36dc-130">在“安全对象”下，选择一个或多个服务器级别的安全对象。</span><span class="sxs-lookup"><span data-stu-id="b36dc-130">Under **Securables**, select one or more server-level securables.</span></span> <span data-ttu-id="b36dc-131">当选择安全对象时，可以向此服务器角色授予或拒绝针对该安全对象的权限。</span><span class="sxs-lookup"><span data-stu-id="b36dc-131">When a securable is selected, this server role can be granted or denied permissions on that securable.</span></span>  
  
7.  <span data-ttu-id="b36dc-132">在“权限: 显式”框中，选中相应的复选框以针对选定的安全对象授予、授予再授予或拒绝此服务器角色的权限。</span><span class="sxs-lookup"><span data-stu-id="b36dc-132">In the **Permissions: Explicit** box, select the check box to grant, grant with grant, or deny permission to this server role for the selected securables.</span></span> <span data-ttu-id="b36dc-133">如果某个权限无法针对所有选定的安全对象进行授予或拒绝，则该权限将表示为部分选择。</span><span class="sxs-lookup"><span data-stu-id="b36dc-133">If a permission cannot be granted or denied to all of the selected securables, the permission is represented as a partial select.</span></span>  
  
8.  <span data-ttu-id="b36dc-134">在 **“成员”** 页上，使用 **“添加”** 按钮将代表个人或组的登录名添加到新的服务器角色。</span><span class="sxs-lookup"><span data-stu-id="b36dc-134">On the **Members** page, use the **Add** button to add logins that represent individuals or groups to the new server role.</span></span>  
  
9. <span data-ttu-id="b36dc-135">用户定义的服务器角色可以是另一个服务器角色的成员。</span><span class="sxs-lookup"><span data-stu-id="b36dc-135">A user-defined server role can be a member of another server role.</span></span> <span data-ttu-id="b36dc-136">在“成员身份”页上，选中一个复选框以使当前用户定义的服务器角色成为所选服务器角色的成员。</span><span class="sxs-lookup"><span data-stu-id="b36dc-136">On the **Memberships** page, select a check box to make the current user-defined server role a member of a selected server role.</span></span>  
  
10. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="b36dc-137">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b36dc-137">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-new-server-role"></a><span data-ttu-id="b36dc-138">创建新的服务器角色</span><span class="sxs-lookup"><span data-stu-id="b36dc-138">To create a new server role</span></span>  
  
1.  <span data-ttu-id="b36dc-139">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="b36dc-139">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b36dc-140">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="b36dc-140">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b36dc-141">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="b36dc-141">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    --Creates the server role auditors that is owned the securityadmin fixed server role.  
    USE master;  
    CREATE SERVER ROLE auditors AUTHORIZATION securityadmin;  
    GO  
    ```  
  
 <span data-ttu-id="b36dc-142">有关详细信息，请参阅 [CREATE SERVER ROLE (Transact-SQL)](/sql/t-sql/statements/create-server-role-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b36dc-142">For more information, see [CREATE SERVER ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-server-role-transact-sql).</span></span>  
  
  
