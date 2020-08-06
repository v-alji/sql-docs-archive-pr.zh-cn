---
title: 创建数据库用户 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.DATABASEUSER.GENERAL.F1
- sql12.swb.user.securables.f1
helpviewer_keywords:
- database users, creating
- creating users with Management Studio
- mapping users
- users [SQL Server], creating
- database user additions [SQL Server]
- database users, mapping
- CREATE USER [Management Studio]
- users [SQL Server], adding
- mapping database users
ms.assetid: 782798d3-9552-4514-9f58-e87be4b264e4
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 97fc758c754f5fc8803e988d55147670fc3ff45b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688765"
---
# <a name="create-a-database-user"></a><span data-ttu-id="e4959-102">创建数据库用户</span><span class="sxs-lookup"><span data-stu-id="e4959-102">Create a Database User</span></span>
  <span data-ttu-id="e4959-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中创建映射到某一登录名的数据库用户。</span><span class="sxs-lookup"><span data-stu-id="e4959-103">This topic describes how to create a database user mapped to a login in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="e4959-104">数据库用户是连接到数据库时的登录名的标识。</span><span class="sxs-lookup"><span data-stu-id="e4959-104">The database user is the identity of the login when it is connected to a database.</span></span> <span data-ttu-id="e4959-105">数据库用户可以使用与登录名相同的名称，但这不是必需的。</span><span class="sxs-lookup"><span data-stu-id="e4959-105">The database user can use the same name as the login, but that is not required.</span></span> <span data-ttu-id="e4959-106">本主题假设 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]中已存在登录名。</span><span class="sxs-lookup"><span data-stu-id="e4959-106">This topic assumes that a login already exists in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e4959-107">有关如何创建登录名的信息，请参阅[创建登录名](create-a-login.md)。</span><span class="sxs-lookup"><span data-stu-id="e4959-107">For information about how to create a login, see [Create a Login](create-a-login.md).</span></span>  
  
 <span data-ttu-id="e4959-108">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="e4959-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="e4959-109">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="e4959-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="e4959-110">背景</span><span class="sxs-lookup"><span data-stu-id="e4959-110">Background</span></span>](#Restrictions)  
  
     [<span data-ttu-id="e4959-111">安全性</span><span class="sxs-lookup"><span data-stu-id="e4959-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="e4959-112">**若要创建数据库用户，请使用：**</span><span class="sxs-lookup"><span data-stu-id="e4959-112">**To create a database user, using:**</span></span>  
  
     [<span data-ttu-id="e4959-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e4959-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="e4959-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e4959-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e4959-115">开始之前</span><span class="sxs-lookup"><span data-stu-id="e4959-115">Before You Begin</span></span>  
  
###  <a name="background"></a><a name="Restrictions"></a> <span data-ttu-id="e4959-116">背景</span><span class="sxs-lookup"><span data-stu-id="e4959-116">Background</span></span>  
 <span data-ttu-id="e4959-117">用户是数据库级别安全主体。</span><span class="sxs-lookup"><span data-stu-id="e4959-117">A user is a database level security principal.</span></span> <span data-ttu-id="e4959-118">登录名必须映射到数据库用户才能连接到数据库。</span><span class="sxs-lookup"><span data-stu-id="e4959-118">Logins must be mapped to a database user to connect to a database.</span></span> <span data-ttu-id="e4959-119">一个登录名可以作为不同用户映射到不同的数据库，但在每个数据库中只能作为一个用户进行映射。</span><span class="sxs-lookup"><span data-stu-id="e4959-119">A login can be mapped to different databases as different users but can only be mapped as one user in each database.</span></span> <span data-ttu-id="e4959-120">在部分包含数据库中，可以创建不具有登录名的用户。</span><span class="sxs-lookup"><span data-stu-id="e4959-120">In a partially contained database, a user can be created that does not have a login.</span></span> <span data-ttu-id="e4959-121">有关包含的数据库用户的详细信息，请参阅 [CREATE USER (Transact-SQL)](/sql/t-sql/statements/create-user-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="e4959-121">For more information about contained database users, see [CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql).</span></span> <span data-ttu-id="e4959-122">如果在数据库中启用了 guest 用户，未映射到数据库用户的登录名可作为 guest 用户进入该数据库。</span><span class="sxs-lookup"><span data-stu-id="e4959-122">If the guest user in a database is enabled, a login that is not mapped to a database user can enter the database as the guest user.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e4959-123">guest 用户通常处于禁用状态。</span><span class="sxs-lookup"><span data-stu-id="e4959-123">The guest user is ordinarily disabled.</span></span> <span data-ttu-id="e4959-124">除非有必要，否则不要启用 guest 用户。</span><span class="sxs-lookup"><span data-stu-id="e4959-124">Do not enable the guest user unless it is necessary.</span></span>  
  
 <span data-ttu-id="e4959-125">可以向作为安全主体的用户授予权限。</span><span class="sxs-lookup"><span data-stu-id="e4959-125">As a security principal, permissions can be granted to users.</span></span> <span data-ttu-id="e4959-126">用户的作用域是数据库。</span><span class="sxs-lookup"><span data-stu-id="e4959-126">The scope of a user is the database.</span></span> <span data-ttu-id="e4959-127">若要连接 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]实例上的特定数据库，登录名必须映射到数据库用户。</span><span class="sxs-lookup"><span data-stu-id="e4959-127">To connect to a specific database on the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], a login must be mapped to a database user.</span></span> <span data-ttu-id="e4959-128">数据库内的权限是向数据库用户而不是登录名授予和拒绝授予的。</span><span class="sxs-lookup"><span data-stu-id="e4959-128">Permissions inside the database are granted and denied to the database user, not the login.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e4959-129">Security</span><span class="sxs-lookup"><span data-stu-id="e4959-129">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e4959-130">权限</span><span class="sxs-lookup"><span data-stu-id="e4959-130">Permissions</span></span>  
 <span data-ttu-id="e4959-131">需要对数据库拥有 `ALTER ANY USER` 权限。</span><span class="sxs-lookup"><span data-stu-id="e4959-131">Requires `ALTER ANY USER` permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e4959-132">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e4959-132">Using SQL Server Management Studio</span></span>  
  
##### <a name="to-create-a-database-user"></a><span data-ttu-id="e4959-133">创建数据库用户</span><span class="sxs-lookup"><span data-stu-id="e4959-133">To create a database user</span></span>  
  
1.  <span data-ttu-id="e4959-134">在对象资源管理器中，展开 **“数据库”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="e4959-134">In Object Explorer, expand the **Databases** folder.</span></span>  
  
2.  <span data-ttu-id="e4959-135">展开要在其中创建新数据库用户的数据库。</span><span class="sxs-lookup"><span data-stu-id="e4959-135">Expand the database in which to create the new database user.</span></span>  
  
3.  <span data-ttu-id="e4959-136">右键单击“安全性”文件夹，指向“新建”，然后选择“用户…”  。</span><span class="sxs-lookup"><span data-stu-id="e4959-136">Right-click the **Security** folder, point to **New**, and select **User...**.</span></span>  
  
4.  <span data-ttu-id="e4959-137">在 "**数据库用户-新建**" 对话框的 "**常规**" 页上，从 "**用户类型**" 列表中选择以下用户类型之一 **：带登录名的 sql 用户**、**没有登录名的 sql**用户、**映射到证书**的用户、映射**到非对称密钥**的用户或**Windows 用户**。</span><span class="sxs-lookup"><span data-stu-id="e4959-137">In the **Database User - New** dialog box, on the **General** page, select one of the following user types from the **User type** list: **SQL user with login**, **SQL user without login**, **User mapped to a certificate**, **User mapped to an asymmetric key**, or **Windows user**.</span></span>  
  
5.  <span data-ttu-id="e4959-138">在 **“用户名”** 框中，输入新用户的名称。</span><span class="sxs-lookup"><span data-stu-id="e4959-138">In the **User name** box, enter a name for the new user.</span></span> <span data-ttu-id="e4959-139">如果你从“用户类型”列表中选择了“Windows 用户”，则还可以单击省略号 (…) 打开“选择用户或组”对话框   。</span><span class="sxs-lookup"><span data-stu-id="e4959-139">If you have chosen **Windows user** from the **User type** list, you can also click the ellipsis **(...)** to open the **Select User or Group** dialog box.</span></span>  
  
6.  <span data-ttu-id="e4959-140">在 **“登录名”** 框中，输入用户的登录名。</span><span class="sxs-lookup"><span data-stu-id="e4959-140">In the **Login name** box, enter the login for the user.</span></span> <span data-ttu-id="e4959-141">或者，单击省略号 (…) 以打开“选择登录名”对话框 。</span><span class="sxs-lookup"><span data-stu-id="e4959-141">Alternately, click the ellipsis **(...)** to open the **Select Login** dialog box.</span></span> <span data-ttu-id="e4959-142">如果您从 **“用户类型”** 列表中选择了 **“带登录名的 SQL 用户”** 或 **“Windows 用户”** ，则 **“登录名”** 可用。</span><span class="sxs-lookup"><span data-stu-id="e4959-142">**Login name** is available if you select either **SQL user with login** or **Windows user** from the **User type** list.</span></span>  
  
7.  <span data-ttu-id="e4959-143">在 **“默认架构”** 框中，指定此用户所创建的对象所属的架构。</span><span class="sxs-lookup"><span data-stu-id="e4959-143">In the **Default schema** box, specifies the schema that will own objects created by this user.</span></span> <span data-ttu-id="e4959-144">或者，单击省略号 (…) 以打开“选择架构”对话框 。</span><span class="sxs-lookup"><span data-stu-id="e4959-144">Alternately, click the ellipsis **(...)** to open the **Select Schema** dialog box.</span></span> <span data-ttu-id="e4959-145">如果您从 **“用户类型”** 列表中选择了 **“带登录名的 SQL 用户”** , **“不带登录名的 SQL 用户”** 或 **“Windows 用户”** ，则 **“默认架构”** 可用。</span><span class="sxs-lookup"><span data-stu-id="e4959-145">**Default schema** is available if you select either **SQL user with login**, **SQL user without login**, or **Windows user** from the **User type** list.</span></span>  
  
8.  <span data-ttu-id="e4959-146">在 **“证书名称”** 框中，输入要用于数据库用户的证书。</span><span class="sxs-lookup"><span data-stu-id="e4959-146">In the **Certificate name** box, enter the certificate to be used for the database user.</span></span> <span data-ttu-id="e4959-147">或者，单击省略号 (…) 以打开“选择证书”对话框 。</span><span class="sxs-lookup"><span data-stu-id="e4959-147">Alternately, click the ellipsis **(...)** to open the **Select Certificate** dialog box.</span></span> <span data-ttu-id="e4959-148">如果从 **“用户类型”** 列表中选择了 **“映射到证书的用户”** ，则 **“证书名称”** 可用。</span><span class="sxs-lookup"><span data-stu-id="e4959-148">**Certificate name** is available if you select **User mapped to a certificate** from the **User type** list.</span></span>  
  
9. <span data-ttu-id="e4959-149">在“非对称密钥名称” \*\*\*\*  框中，输入要用于数据库用户的密钥。</span><span class="sxs-lookup"><span data-stu-id="e4959-149">In the **Asymmetric key name**  box, enter the key to be used for the database user.</span></span> <span data-ttu-id="e4959-150">或者，单击省略号 (…) 以打开“选择非对称密钥”对话框 。</span><span class="sxs-lookup"><span data-stu-id="e4959-150">Alternately, click the ellipsis **(...)** to open the **Select Asymmetric Key** dialog box.</span></span> <span data-ttu-id="e4959-151">如果从 **“用户类型”** 列表中选择了 **“映射到非对称密钥的用户”** ，则 **“非对称密钥名称”** 可用。</span><span class="sxs-lookup"><span data-stu-id="e4959-151">**Asymmetric key name** is available if you select **User mapped to an asymmetric key** from the **User type** list.</span></span>  
  
10. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="additional-options"></a><span data-ttu-id="e4959-152">其他选项</span><span class="sxs-lookup"><span data-stu-id="e4959-152">Additional Options</span></span>  
 <span data-ttu-id="e4959-153">“数据库用户 - 新建”对话框还提供了四个其他页上的选项：“拥有的架构”、“成员身份”、“安全对象”和“扩展属性”   。</span><span class="sxs-lookup"><span data-stu-id="e4959-153">The **Database User - New** dialog box also offers options on four additional pages: **Owned Schemas**, **Membership**, **Securables**, and **Extended Properties**.</span></span>  
  
-   <span data-ttu-id="e4959-154">**“拥有的架构”** 页列出了可由新的数据库用户拥有的所有可能的架构。</span><span class="sxs-lookup"><span data-stu-id="e4959-154">The **Owned Schemas** page lists all possible schemas that can be owned by the new database user.</span></span> <span data-ttu-id="e4959-155">若要向数据库用户添加架构或者从数据库用户中删除架构，请在 **“此用户拥有的架构”** 下选中或取消选中架构旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="e4959-155">To add schemas to or remove them from a database user, under **Schemas owned by this user**, select or clear the check boxes next to the schemas.</span></span>  
  
-   <span data-ttu-id="e4959-156">**“成员身份”** 页列出了可由新的数据库用户拥有的所有可能的数据库成员身份角色。</span><span class="sxs-lookup"><span data-stu-id="e4959-156">The **Membership** page lists all possible database membership roles that can be owned by the new database user.</span></span> <span data-ttu-id="e4959-157">若要向数据库用户添加角色或者从数据库用户中删除角色，请在 **“数据库角色成员身份”** 下选中或取消选中角色旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="e4959-157">To add roles to or remove them from a database user, under **Database role membership**, select or clear the check boxes next to the roles.</span></span>  
  
-   <span data-ttu-id="e4959-158">**“安全对象”** 页将列出所有可能的安全对象以及可授予登录名的针对这些安全对象的权限。</span><span class="sxs-lookup"><span data-stu-id="e4959-158">The **Securables** page lists all possible securables and the permissions on those securables that can be granted to the login.</span></span>  
  
-   <span data-ttu-id="e4959-159">**“扩展属性”** 页允许您向数据库用户添加自定义属性。</span><span class="sxs-lookup"><span data-stu-id="e4959-159">The **Extended properties** page allows you to add custom properties to database users.</span></span> <span data-ttu-id="e4959-160">此页还提供以下选项：</span><span class="sxs-lookup"><span data-stu-id="e4959-160">The following options are available on this page.</span></span>  
  
     <span data-ttu-id="e4959-161">**Database**</span><span class="sxs-lookup"><span data-stu-id="e4959-161">**Database**</span></span>  
     <span data-ttu-id="e4959-162">显示所选数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="e4959-162">Displays the name of the selected database.</span></span> <span data-ttu-id="e4959-163">此字段为只读。</span><span class="sxs-lookup"><span data-stu-id="e4959-163">This field is read-only.</span></span>  
  
     <span data-ttu-id="e4959-164">**排序规则**</span><span class="sxs-lookup"><span data-stu-id="e4959-164">**Collation**</span></span>  
     <span data-ttu-id="e4959-165">显示用于所选数据库的排序规则。</span><span class="sxs-lookup"><span data-stu-id="e4959-165">Displays the collation used for the selected database.</span></span> <span data-ttu-id="e4959-166">此字段为只读。</span><span class="sxs-lookup"><span data-stu-id="e4959-166">This field is read-only.</span></span>  
  
     <span data-ttu-id="e4959-167">**属性**</span><span class="sxs-lookup"><span data-stu-id="e4959-167">**Properties**</span></span>  
     <span data-ttu-id="e4959-168">查看或指定对象的扩展属性。</span><span class="sxs-lookup"><span data-stu-id="e4959-168">View or specify the extended properties for the object.</span></span> <span data-ttu-id="e4959-169">每个扩展属性都由与该对象关联的元数据的名称/值对组成。</span><span class="sxs-lookup"><span data-stu-id="e4959-169">Each extended property consists of a name/value pair of metadata associated with the object.</span></span>  
  
     <span data-ttu-id="e4959-170">**省略号 (...)**</span><span class="sxs-lookup"><span data-stu-id="e4959-170">**Ellipsis (...)**</span></span>  
     <span data-ttu-id="e4959-171">单击“值”后面的省略号 (…) 按钮可打开“已扩展属性的值”对话框  。</span><span class="sxs-lookup"><span data-stu-id="e4959-171">Click the ellipsis **(...)** after **Value** to open the **Value for Extended Property** dialog box.</span></span> <span data-ttu-id="e4959-172">在这一较大的范围中键入或查看扩展属性的值。</span><span class="sxs-lookup"><span data-stu-id="e4959-172">Type or view the value of the extended property in this larger location.</span></span> <span data-ttu-id="e4959-173">有关详细信息，请参阅 [“扩展属性的值”对话框](../../databases/value-for-extended-property-dialog-box.md)。</span><span class="sxs-lookup"><span data-stu-id="e4959-173">For more information, see [Value for Extended Property Dialog Box](../../databases/value-for-extended-property-dialog-box.md).</span></span>  
  
     <span data-ttu-id="e4959-174">**删除**</span><span class="sxs-lookup"><span data-stu-id="e4959-174">**Delete**</span></span>  
     <span data-ttu-id="e4959-175">删除所选扩展属性。</span><span class="sxs-lookup"><span data-stu-id="e4959-175">Removes the selected extended property.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="e4959-176">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e4959-176">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-database-user"></a><span data-ttu-id="e4959-177">创建数据库用户</span><span class="sxs-lookup"><span data-stu-id="e4959-177">To create a database user</span></span>  
  
1.  <span data-ttu-id="e4959-178">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="e4959-178">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e4959-179">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="e4959-179">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e4959-180">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="e4959-180">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Creates the login AbolrousHazem with password '340$Uuxwp7Mcxo7Khy'.  
    CREATE LOGIN AbolrousHazem   
        WITH PASSWORD = '340$Uuxwp7Mcxo7Khy';  
    GO  
  
    -- Creates a database user for the login created above.  
    CREATE USER AbolrousHazem FOR LOGIN AbolrousHazem;  
    GO  
    ```  
  
 <span data-ttu-id="e4959-181">有关详细信息，请参阅 [CREATE USER (Transact-SQL)](/sql/t-sql/statements/create-user-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="e4959-181">For more information, see [CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4959-182">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e4959-182">See Also</span></span>  
 [<span data-ttu-id="e4959-183">主体（数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="e4959-183">Principals &#40;Database Engine&#41;</span></span>](principals-database-engine.md)  
  
  
