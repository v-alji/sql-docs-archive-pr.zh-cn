---
title: 加入角色 | Microsoft Docs
ms.custom: ''
ms.date: 07/14/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.DATABASEUSER.MEMBERSHIP.F1
helpviewer_keywords:
- adding a member to a role
- join a role
ms.assetid: 05c8d10d-5823-46c6-8b1a-81722da6a42b
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 58e8c071672c8c3afba8d6c424488899dcf76be7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578759"
---
# <a name="join-a-role"></a><span data-ttu-id="a0b9c-102">加入角色</span><span class="sxs-lookup"><span data-stu-id="a0b9c-102">Join a Role</span></span>
  <span data-ttu-id="a0b9c-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中向登录名和数据库用户分配角色。</span><span class="sxs-lookup"><span data-stu-id="a0b9c-103">This topic describes how to assign roles to logins and database users in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="a0b9c-104">可使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中的角色高效地管理权限。</span><span class="sxs-lookup"><span data-stu-id="a0b9c-104">Use roles in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to efficiently manage permissions.</span></span> <span data-ttu-id="a0b9c-105">将权限分配给角色，然后在角色中添加和删除用户以及登录名。</span><span class="sxs-lookup"><span data-stu-id="a0b9c-105">Assign permissions to roles, and then add and remove users and logins to the roles.</span></span> <span data-ttu-id="a0b9c-106">通过使用角色，不必针对各个用户单独维护权限。</span><span class="sxs-lookup"><span data-stu-id="a0b9c-106">By using roles, permissions do not have to be individually maintained for each user.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="a0b9c-107">支持四种类型的角色。</span><span class="sxs-lookup"><span data-stu-id="a0b9c-107">supports four types of roles.</span></span>  
  
-   <span data-ttu-id="a0b9c-108">固定服务器角色</span><span class="sxs-lookup"><span data-stu-id="a0b9c-108">Fixed server roles</span></span>  
  
-   <span data-ttu-id="a0b9c-109">用户定义的服务器角色</span><span class="sxs-lookup"><span data-stu-id="a0b9c-109">User-defined server roles</span></span>  
  
-   <span data-ttu-id="a0b9c-110">固定的数据库角色</span><span class="sxs-lookup"><span data-stu-id="a0b9c-110">Fixed database roles</span></span>  
  
-   <span data-ttu-id="a0b9c-111">用户定义的数据库角色</span><span class="sxs-lookup"><span data-stu-id="a0b9c-111">User-defined database roles</span></span>  
  
 <span data-ttu-id="a0b9c-112">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]中会自动提供固定角色。</span><span class="sxs-lookup"><span data-stu-id="a0b9c-112">The fixed roles are automatically available in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a0b9c-113">固定角色具有完成常见任务必需的权限。</span><span class="sxs-lookup"><span data-stu-id="a0b9c-113">Fixed roles have the necessary permissions to accomplish common tasks.</span></span> <span data-ttu-id="a0b9c-114">有关固定角色的详细信息，请参阅以下链接。</span><span class="sxs-lookup"><span data-stu-id="a0b9c-114">For more information about fixed roles, see the following links.</span></span> <span data-ttu-id="a0b9c-115">用户定义的角色由您创建，并可使用选择的权限进行自定义。</span><span class="sxs-lookup"><span data-stu-id="a0b9c-115">User-defined roles are created by you, and can be customized with the permissions that you select.</span></span> <span data-ttu-id="a0b9c-116">有关用户定义角色的详细信息，请参阅以下链接。</span><span class="sxs-lookup"><span data-stu-id="a0b9c-116">For more information about user-defined roles, see the following links.</span></span>  
  
 <span data-ttu-id="a0b9c-117">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="a0b9c-117">**In This Topic**</span></span>  
  
-   <span data-ttu-id="a0b9c-118">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="a0b9c-118">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="a0b9c-119">限制和局限</span><span class="sxs-lookup"><span data-stu-id="a0b9c-119">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="a0b9c-120">安全性</span><span class="sxs-lookup"><span data-stu-id="a0b9c-120">Security</span></span>](#Security)  
  
-   <span data-ttu-id="a0b9c-121">**若要向登录名和数据库用户分配角色，请使用：**</span><span class="sxs-lookup"><span data-stu-id="a0b9c-121">**To assign roles to logins and database users, using:**</span></span>  
  
     [<span data-ttu-id="a0b9c-122">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a0b9c-122">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="a0b9c-123">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a0b9c-123">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a0b9c-124">开始之前</span><span class="sxs-lookup"><span data-stu-id="a0b9c-124">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="a0b9c-125">限制和局限</span><span class="sxs-lookup"><span data-stu-id="a0b9c-125">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="a0b9c-126">更改数据库角色的名称不会更改角色的 ID 号、所有者或权限。</span><span class="sxs-lookup"><span data-stu-id="a0b9c-126">Changing the name of a database role does not change ID number, owner, or permissions of the role.</span></span>  
  
-   <span data-ttu-id="a0b9c-127">在 sys.database_role_members 和 sys.database_principals 目录视图中可以查看数据库角色。</span><span class="sxs-lookup"><span data-stu-id="a0b9c-127">Database roles are visible in the sys.database_role_members and sys.database_principals catalog views.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a0b9c-128">Security</span><span class="sxs-lookup"><span data-stu-id="a0b9c-128">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a0b9c-129">权限</span><span class="sxs-lookup"><span data-stu-id="a0b9c-129">Permissions</span></span>  
 <span data-ttu-id="a0b9c-130">需要 `ALTER ANY ROLE` 对数据库的权限、 `ALTER` 对角色的权限或**db_securityadmin**的成员身份。</span><span class="sxs-lookup"><span data-stu-id="a0b9c-130">Requires `ALTER ANY ROLE` permission on the database, `ALTER` permission on the role, or membership in **db_securityadmin**.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a0b9c-131">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a0b9c-131">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-add-a-member-to-a-fixed-server-role"></a><span data-ttu-id="a0b9c-132">向固定服务器角色添加成员</span><span class="sxs-lookup"><span data-stu-id="a0b9c-132">To add a member to a fixed server role</span></span>  
  
1.  <span data-ttu-id="a0b9c-133">在“对象资源管理器”中，展开要在其中编辑固定服务器角色的服务器。</span><span class="sxs-lookup"><span data-stu-id="a0b9c-133">In Object Explorer, expand the server in which you want to edit a fixed server role.</span></span>  
  
2.  <span data-ttu-id="a0b9c-134">展开 **“安全性”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="a0b9c-134">Expand the **Security** folder.</span></span>  
  
3.  <span data-ttu-id="a0b9c-135">展开 **“服务器角色”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="a0b9c-135">Expand the **Server Roles** folder</span></span>  
  
4.  <span data-ttu-id="a0b9c-136">右键单击要编辑的角色，然后选择“属性”。</span><span class="sxs-lookup"><span data-stu-id="a0b9c-136">Right-click the role you want to edit and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="a0b9c-137">在 "**服务器角色属性-**_server_role_name_ " 对话框的 "**成员**" 页上，单击 "**添加**"。</span><span class="sxs-lookup"><span data-stu-id="a0b9c-137">In the **Server Role Properties -**_server_role_name_ dialog box, on the **Members** page, click **Add**.</span></span>  
  
6.  <span data-ttu-id="a0b9c-138">在“选择服务器登录名或角色”对话框的“输入要选择的对象名称(示例)”下，输入要添加到该服务器角色的登录名或服务器角色。</span><span class="sxs-lookup"><span data-stu-id="a0b9c-138">In the **Select Server Login or Role** dialog box, under **Enter the object names to select (examples)**, enter the login or server role to add to this server role.</span></span> <span data-ttu-id="a0b9c-139">或者，单击“浏览...”，然后在“浏览对象”对话框中选择任意对象或所有可用对象 。</span><span class="sxs-lookup"><span data-stu-id="a0b9c-139">Alternately, click **Browse...** and select any or all of the available objects in the **Browse for Objects** dialog box.</span></span> <span data-ttu-id="a0b9c-140">单击 **"确定"** 以返回到 "**服务器角色属性-**_server_role_name_ " 对话框。</span><span class="sxs-lookup"><span data-stu-id="a0b9c-140">Click **OK** to return to the **Server Role Properties -**_server_role_name_ dialog box.</span></span>  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-add-a-member-to-a-user-defined-database-role"></a><span data-ttu-id="a0b9c-141">向用户定义的数据库角色添加成员</span><span class="sxs-lookup"><span data-stu-id="a0b9c-141">To add a member to a user-defined database role</span></span>  
  
1.  <span data-ttu-id="a0b9c-142">在“对象资源管理器”中，展开要在其中编辑用户定义的数据库角色的服务器。</span><span class="sxs-lookup"><span data-stu-id="a0b9c-142">In Object Explorer, expand the server in which you want to edit a user-defined database role.</span></span>  
  
2.  <span data-ttu-id="a0b9c-143">展开 **“数据库”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="a0b9c-143">Expand the **Databases** folder.</span></span>  
  
3.  <span data-ttu-id="a0b9c-144">展开要在其中编辑用户定义的数据库角色的数据库。</span><span class="sxs-lookup"><span data-stu-id="a0b9c-144">Expand the database in which you want to edit a user-defined database role.</span></span>  
  
4.  <span data-ttu-id="a0b9c-145">展开 **“安全性”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="a0b9c-145">Expand the **Security** folder.</span></span>  
  
5.  <span data-ttu-id="a0b9c-146">展开 **“角色”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="a0b9c-146">Expand the **Roles** folder.</span></span>  
  
6.  <span data-ttu-id="a0b9c-147">展开 **“服务器角色”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="a0b9c-147">Expand the **Server Roles** folder.</span></span>  
  
7.  <span data-ttu-id="a0b9c-148">右键单击要编辑的角色，然后选择“属性”。</span><span class="sxs-lookup"><span data-stu-id="a0b9c-148">Right-click the role you want to edit and select **Properties**.</span></span>  
  
8.  <span data-ttu-id="a0b9c-149">在 "**数据库角色属性-**_database_role_name_ " 对话框的 "**常规**" 页中，单击 "**添加**"。</span><span class="sxs-lookup"><span data-stu-id="a0b9c-149">In the **Database Role Properties -**_database_role_name_ dialog box, in the **General** page, click **Add**.</span></span>  
  
9. <span data-ttu-id="a0b9c-150">在“选择数据库用户或角色”对话框的“输入要选择的对象名称(示例)”下，输入要添加到该数据库角色的登录名或数据库角色。</span><span class="sxs-lookup"><span data-stu-id="a0b9c-150">In the **Select Database User or Role** dialog box, under **Enter the object names to select (examples)**, enter the login or database role to add to this database role.</span></span> <span data-ttu-id="a0b9c-151">或者，单击“浏览...”，然后在“浏览对象”对话框中选择任意对象或所有可用对象 。</span><span class="sxs-lookup"><span data-stu-id="a0b9c-151">Alternately, click **Browse...** and select any or all of the available objects in the **Browse for Objects** dialog box.</span></span> <span data-ttu-id="a0b9c-152">单击 **"确定"** 以返回 "**数据库角色属性-**_database_role_name_ " 对话框。</span><span class="sxs-lookup"><span data-stu-id="a0b9c-152">Click **OK** to return to the **Database Role Properties -**_database_role_name_ dialog box.</span></span>  
  
10. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a0b9c-153">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a0b9c-153">Using Transact-SQL</span></span>  
  
#### <a name="to-add-a-member-to-a-fixed-server-role"></a><span data-ttu-id="a0b9c-154">向固定服务器角色添加成员</span><span class="sxs-lookup"><span data-stu-id="a0b9c-154">To add a member to a fixed server role</span></span>  
  
1.  <span data-ttu-id="a0b9c-155">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="a0b9c-155">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="a0b9c-156">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="a0b9c-156">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="a0b9c-157">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="a0b9c-157">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    ALTER SERVER ROLE diskadmin ADD MEMBER [Domain\Juan] ;  
    GO  
    ```  
  
 <span data-ttu-id="a0b9c-158">有关详细信息，请参阅 [ALTER ROLE (Transact-SQL)](/sql/t-sql/statements/alter-role-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a0b9c-158">For more information, see [ALTER ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-role-transact-sql).</span></span>  
  
#### <a name="to-add-a-member-to-a-user-defined-database-role"></a><span data-ttu-id="a0b9c-159">向用户定义的数据库角色添加成员</span><span class="sxs-lookup"><span data-stu-id="a0b9c-159">To add a member to a user-defined database role</span></span>  
  
1.  <span data-ttu-id="a0b9c-160">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="a0b9c-160">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="a0b9c-161">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="a0b9c-161">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="a0b9c-162">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="a0b9c-162">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    ALTER ROLE Marketing ADD MEMBER [Domain\Juan] ;  
    GO  
    ```  
  
 <span data-ttu-id="a0b9c-163">有关详细信息，请参阅 [sp_addrolemember (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a0b9c-163">For more information, see [sp_addrolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0b9c-164">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a0b9c-164">See Also</span></span>  
 <span data-ttu-id="a0b9c-165">[服务器级别角色](server-level-roles.md) </span><span class="sxs-lookup"><span data-stu-id="a0b9c-165">[Server-Level Roles](server-level-roles.md) </span></span>  
 <span data-ttu-id="a0b9c-166">[数据库级别的角色](../authentication-access/database-level-roles.md) </span><span class="sxs-lookup"><span data-stu-id="a0b9c-166">[Database-Level Roles](../authentication-access/database-level-roles.md) </span></span>  
 [<span data-ttu-id="a0b9c-167">应用程序角色</span><span class="sxs-lookup"><span data-stu-id="a0b9c-167">Application Roles</span></span>](../authentication-access/application-roles.md)  
  
  
