---
title: 创建登录名 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.LOGIN.SERVERROLES.F1
- sql12.swb.login.databaseaccess.f1
- sql12.swb.login.general.f1
- sql12.swb.login.effectivepermissions.f1
- sql12.swb.login.status.f1
helpviewer_keywords:
- authentication [SQL Server], logins
- logins [SQL Server], creating
- creating logins with Management Studio
- Create login [SQL Server]
- SQL Server logins
ms.assetid: fb163e47-1546-4682-abaa-8c9494e9ddc7
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: e476880103a69ae016c6720f36e26ef884db6f5d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688763"
---
# <a name="create-a-login"></a><span data-ttu-id="d468d-102">创建一个登录名</span><span class="sxs-lookup"><span data-stu-id="d468d-102">Create a Login</span></span>
  <span data-ttu-id="d468d-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中创建登录名。</span><span class="sxs-lookup"><span data-stu-id="d468d-103">This topic describes how to create a login in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="d468d-104">登录名是连接 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]实例的个人或进程的标识。</span><span class="sxs-lookup"><span data-stu-id="d468d-104">A login is the identity of the person or process that is connecting to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="d468d-105">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="d468d-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="d468d-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="d468d-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="d468d-107">背景</span><span class="sxs-lookup"><span data-stu-id="d468d-107">Background</span></span>](#Background)  
  
     [<span data-ttu-id="d468d-108">安全性</span><span class="sxs-lookup"><span data-stu-id="d468d-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="d468d-109">**若要创建登录名，可使用**</span><span class="sxs-lookup"><span data-stu-id="d468d-109">**To create a login, using:**</span></span>  
  
     [<span data-ttu-id="d468d-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d468d-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="d468d-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d468d-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="d468d-112">**跟进：**  [在创建登录名后采取的步骤](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="d468d-112">**Follow Up:**  [Steps to take after you create a login](#FollowUp)</span></span>  
  
##  <a name="background"></a><a name="Background"></a> <span data-ttu-id="d468d-113">背景</span><span class="sxs-lookup"><span data-stu-id="d468d-113">Background</span></span>  
 <span data-ttu-id="d468d-114">登录名是一个可由安全系统进行身份验证的安全主体或实体。</span><span class="sxs-lookup"><span data-stu-id="d468d-114">A login is a security principal, or an entity that can be authenticated by a secure system.</span></span> <span data-ttu-id="d468d-115">用户需要使用登录名连接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d468d-115">Users need a login to connect to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d468d-116">您可基于 Windows 主体（例如，域用户或 Windows 域组）创建登录名，或者也可创建一个并非基于 Windows 主体的登录名（例如， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登录名）。</span><span class="sxs-lookup"><span data-stu-id="d468d-116">You can create a login based on a Windows principal (such as a domain user or a Windows domain group) or you can create a login that is not based on a Windows principal (such as an [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] login).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d468d-117">若要使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 身份验证，[!INCLUDE[ssDE](../../../includes/ssde-md.md)]必须使用混合模式身份验证。</span><span class="sxs-lookup"><span data-stu-id="d468d-117">To use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication, the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] must use mixed mode authentication.</span></span> <span data-ttu-id="d468d-118">有关详细信息，请参阅 [选择身份验证模式](../choose-an-authentication-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="d468d-118">For more information, see [Choose an Authentication Mode](../choose-an-authentication-mode.md).</span></span>  
  
 <span data-ttu-id="d468d-119">可以向作为安全主体的登录名授予权限。</span><span class="sxs-lookup"><span data-stu-id="d468d-119">As a security principal, permissions can be granted to logins.</span></span> <span data-ttu-id="d468d-120">登录名的作用域是整个 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d468d-120">The scope of a login is the whole [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span> <span data-ttu-id="d468d-121">若要连接 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]实例上的特定数据库，登录名必须映射到数据库用户。</span><span class="sxs-lookup"><span data-stu-id="d468d-121">To connect to a specific database on the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], a login must be mapped to a database user.</span></span> <span data-ttu-id="d468d-122">数据库内的权限是向数据库用户而不是登录名授予和拒绝授予的。</span><span class="sxs-lookup"><span data-stu-id="d468d-122">Permissions inside the database are granted and denied to the database user, not the login.</span></span> <span data-ttu-id="d468d-123">可将作用域为整个 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例的权限（例如 `CREATE ENDPOINT` 权限）授予一个登录名。</span><span class="sxs-lookup"><span data-stu-id="d468d-123">Permissions that have the scope of the whole instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (for example, the `CREATE ENDPOINT` permission) can be granted to a login.</span></span>  
  
##  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d468d-124">Security</span><span class="sxs-lookup"><span data-stu-id="d468d-124">Security</span></span>  
  
### <a name="permissions"></a><span data-ttu-id="d468d-125">权限</span><span class="sxs-lookup"><span data-stu-id="d468d-125">Permissions</span></span>  
 <span data-ttu-id="d468d-126">需要拥有服务器上的 `ALTER ANY LOGIN` 或 `ALTER LOGIN` 权限。</span><span class="sxs-lookup"><span data-stu-id="d468d-126">Requires `ALTER ANY LOGIN` or `ALTER LOGIN` permission on the server.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="d468d-127">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d468d-127">Using SQL Server Management Studio</span></span>  
  
##### <a name="to-create-a-sql-server-login"></a><span data-ttu-id="d468d-128">创建 SQL Server 登录名</span><span class="sxs-lookup"><span data-stu-id="d468d-128">To create a SQL Server login</span></span>  
  
1.  <span data-ttu-id="d468d-129">在对象资源管理器中，展开要在其中创建新登录名的服务器实例的文件夹。</span><span class="sxs-lookup"><span data-stu-id="d468d-129">In Object Explorer, expand the folder of the server instance in which you want to create the new login.</span></span>  
  
2.  <span data-ttu-id="d468d-130">右键单击“安全性”文件夹，指向“新建”，然后选择“登录名…”  。</span><span class="sxs-lookup"><span data-stu-id="d468d-130">Right-click the **Security** folder, point to **New**, and select **Login...**.</span></span>  
  
3.  <span data-ttu-id="d468d-131">在“登录名 - 新建”对话框的“常规”页中，在“登录名”框中输入用户的名称  。</span><span class="sxs-lookup"><span data-stu-id="d468d-131">In the **Login - New** dialog box, on the **General** page, enter the name of a user in the **Login name** box.</span></span> <span data-ttu-id="d468d-132">或者，单击“搜索…”以打开“选择用户或组”对话框 。</span><span class="sxs-lookup"><span data-stu-id="d468d-132">Alternately, click **Search...** to open the **Select User or Group** dialog box.</span></span>  
  
     <span data-ttu-id="d468d-133">如果单击“搜索…”：</span><span class="sxs-lookup"><span data-stu-id="d468d-133">If you click **Search...**:</span></span>  
  
    1.  <span data-ttu-id="d468d-134">在“选择此对象类型”下，单击“对象类型…”以打开“对象类型”对话框，并选择以下任意或全部选项：  “内置安全主体”、“组”和“用户”  。</span><span class="sxs-lookup"><span data-stu-id="d468d-134">Under **Select this object type**, click **Object Types...** to open the **Object Types** dialog box and select any or all of the following: **Built-in security principals**, **Groups**, and **Users**.</span></span> <span data-ttu-id="d468d-135">默认情况下，将选中“内置安全主体”和“用户”。</span><span class="sxs-lookup"><span data-stu-id="d468d-135">**Built-in security principals** and **Users** are selected by default.</span></span> <span data-ttu-id="d468d-136">完成后，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="d468d-136">When finished, click **OK**.</span></span>  
  
    2.  <span data-ttu-id="d468d-137">在“从此位置”下，单击“位置…”以打开“位置”对话框，并选择一个可用的服务器位置  。</span><span class="sxs-lookup"><span data-stu-id="d468d-137">Under **From this location**, click **Locations...** to open the **Locations** dialog box and select one of the available server locations.</span></span> <span data-ttu-id="d468d-138">完成后，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="d468d-138">When finished, click **OK**.</span></span>  
  
    3.  <span data-ttu-id="d468d-139">在“输入要选择的对象名称（示例）”下，输入你想要查找的用户或组名。</span><span class="sxs-lookup"><span data-stu-id="d468d-139">Under **Enter the object name to select (examples)**, enter the user or group name that you want to find.</span></span> <span data-ttu-id="d468d-140">有关详细信息，请参阅 [“选择用户、计算机或组”对话框](https://technet.microsoft.com/library/cc771712.aspx)。</span><span class="sxs-lookup"><span data-stu-id="d468d-140">For more information, see [Select Users, Computers, or Groups Dialog Box](https://technet.microsoft.com/library/cc771712.aspx).</span></span>  
  
    4.  <span data-ttu-id="d468d-141">单击“高级…”以显示更多高级搜索选项。</span><span class="sxs-lookup"><span data-stu-id="d468d-141">Click **Advanced...** for more advanced search options.</span></span> <span data-ttu-id="d468d-142">有关详细信息，请参阅 [选择“用户”、“计算机”或“组”对话框 - 高级页面](https://technet.microsoft.com/library/cc733110.aspx)。</span><span class="sxs-lookup"><span data-stu-id="d468d-142">For more information, see [Select Users, Computers, or Groups Dialog Box - Advanced Page](https://technet.microsoft.com/library/cc733110.aspx).</span></span>  
  
    5.  <span data-ttu-id="d468d-143">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="d468d-143">Click **OK**.</span></span>  
  
4.  <span data-ttu-id="d468d-144">若要基于 Windows 主体创建一个登录名，请选择 **“Windows 身份验证”** 。</span><span class="sxs-lookup"><span data-stu-id="d468d-144">To create a login based on a Windows principal, select **Windows authentication**.</span></span> <span data-ttu-id="d468d-145">这是默认选项。</span><span class="sxs-lookup"><span data-stu-id="d468d-145">This is the default selection.</span></span>  
  
5.  <span data-ttu-id="d468d-146">若要创建一个保存在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据库中的登录名，请选择 **“SQL Server 身份验证”** 。</span><span class="sxs-lookup"><span data-stu-id="d468d-146">To create a login that is saved on a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database, select **SQL Server authentication**.</span></span>  
  
    1.  <span data-ttu-id="d468d-147">在“密码”框中，输入新用户的密码。</span><span class="sxs-lookup"><span data-stu-id="d468d-147">In the **Password** box, enter a password for the new user.</span></span> <span data-ttu-id="d468d-148">在“确认密码”框中再次输入该密码。</span><span class="sxs-lookup"><span data-stu-id="d468d-148">Enter that password again into the **Confirm Password** box.</span></span>  
  
    2.  <span data-ttu-id="d468d-149">在更改现有密码时，选择 **“指定旧密码”** ，然后在 **“旧密码”** 框中键入旧密码。</span><span class="sxs-lookup"><span data-stu-id="d468d-149">When changing an existing password, select **Specify old password**, and then type the old password in the **Old password** box.</span></span>  
  
    3.  <span data-ttu-id="d468d-150">若要强制实施有关复杂性和强制执行的密码策略选项，请选择 **“强制实施密码策略”** 。</span><span class="sxs-lookup"><span data-stu-id="d468d-150">To enforce password policy options for complexity and enforcement, select **Enforce password policy**.</span></span> <span data-ttu-id="d468d-151">有关详细信息，请参阅 [Password Policy](../password-policy.md)。</span><span class="sxs-lookup"><span data-stu-id="d468d-151">For more information, see [Password Policy](../password-policy.md).</span></span> <span data-ttu-id="d468d-152">选中 **“SQL Server 身份验证”** 时，这是默认选项。</span><span class="sxs-lookup"><span data-stu-id="d468d-152">This is a default option when **SQL Server authentication** is selected.</span></span>  
  
    4.  <span data-ttu-id="d468d-153">若要强制实施有关过期的密码策略选项，请选中 **“强制密码过期”** 。</span><span class="sxs-lookup"><span data-stu-id="d468d-153">To enforce password policy options for expiration, select **Enforce password expiration**.</span></span> <span data-ttu-id="d468d-154">必须选择 **“强制实施密码策略”** 才能启用此复选框。</span><span class="sxs-lookup"><span data-stu-id="d468d-154">**Enforce password policy** must be selected to enable this checkbox.</span></span> <span data-ttu-id="d468d-155">选中 **“SQL Server 身份验证”** 时，这是默认选项。</span><span class="sxs-lookup"><span data-stu-id="d468d-155">This is a default option when **SQL Server authentication** is selected.</span></span>  
  
    5.  <span data-ttu-id="d468d-156">若要在首次使用登录名后强制用户创建新密码，请选择 **“用户在下次登录时必须更改密码”** 。</span><span class="sxs-lookup"><span data-stu-id="d468d-156">To force the user to create a new password after the first time the login is used, select **User must change password at next login**.</span></span> <span data-ttu-id="d468d-157">必须选择 **“强制密码过期”** 才能启用此复选框。</span><span class="sxs-lookup"><span data-stu-id="d468d-157">**Enforce password expiration** must be selected to enable this checkbox.</span></span> <span data-ttu-id="d468d-158">选中 **“SQL Server 身份验证”** 时，这是默认选项。</span><span class="sxs-lookup"><span data-stu-id="d468d-158">This is a default option when **SQL Server authentication** is selected.</span></span>  
  
6.  <span data-ttu-id="d468d-159">若要将登录名与独立的安全性证书相关联，请选择“映射到证书”，然后再从列表中选择现有证书的名称。</span><span class="sxs-lookup"><span data-stu-id="d468d-159">To associate the login with a stand-alone security certificate, select **Mapped to certificate** and then select the name of an existing certificate from the list.</span></span>  
  
7.  <span data-ttu-id="d468d-160">若要将登录名与独立的非对称密钥相关联，请选择“映射到非对称密钥”，然后再从列表中选择现有密钥的名称。</span><span class="sxs-lookup"><span data-stu-id="d468d-160">To associate the login with a stand-alone asymmetric key, select **Mapped to asymmetric key** to, and then select the name of an existing key from the list.</span></span>  
  
8.  <span data-ttu-id="d468d-161">若要将登录名与安全凭据相关联，请选中 **“映射到凭据”** 复选框，然后再从列表中选择现有凭据或单击 **“添加”** 以创建新的凭据。</span><span class="sxs-lookup"><span data-stu-id="d468d-161">To associate the login with a security credential, select the **Mapped to Credential** check box, and then either select an existing credential from the list or click **Add** to create a new credential.</span></span> <span data-ttu-id="d468d-162">若要从登录名删除与某个安全凭据的映射，请从 **“映射的凭据”** 中选择该凭据，然后单击 **“删除”** 。</span><span class="sxs-lookup"><span data-stu-id="d468d-162">To remove a mapping to a security credential from the login, select the credential from **Mapped Credentials** and click **Remove**.</span></span> <span data-ttu-id="d468d-163">有关常规凭据的详细信息，请参阅[凭据（数据库引擎）](credentials-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="d468d-163">For more information about credentials in general, see [Credentials &#40;Database Engine&#41;](credentials-database-engine.md).</span></span>  
  
9. <span data-ttu-id="d468d-164">从 **“默认数据库”** 列表中，选择登录名的默认数据库。</span><span class="sxs-lookup"><span data-stu-id="d468d-164">From the **Default database** list, select a default database for the login.</span></span> <span data-ttu-id="d468d-165">**“Master”** 是此选项的默认值。</span><span class="sxs-lookup"><span data-stu-id="d468d-165">**Master** is the default for this option.</span></span>  
  
10. <span data-ttu-id="d468d-166">从 **“默认语言”** 列表中，选择登录名的默认语言。</span><span class="sxs-lookup"><span data-stu-id="d468d-166">From the **Default language** list, select a default language for the login.</span></span>  
  
11. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="additional-options"></a><span data-ttu-id="d468d-167">其他选项</span><span class="sxs-lookup"><span data-stu-id="d468d-167">Additional Options</span></span>  
 <span data-ttu-id="d468d-168">“登录名 - 新建”对话框中还提供了其他四个页面上选项：“服务器角色”、“用户映射”、“安全对象”和“状态”   。</span><span class="sxs-lookup"><span data-stu-id="d468d-168">The **Login - New** dialog box also offers options on four additional pages: **Server Roles**, **User Mapping**, **Securables**, and **Status**.</span></span>  
  
### <a name="server-roles"></a><span data-ttu-id="d468d-169">“服务器角色”</span><span class="sxs-lookup"><span data-stu-id="d468d-169">Server Roles</span></span>  
 <span data-ttu-id="d468d-170">**“服务器角色”** 页将列出可分配给新登录名的所有可能的角色。</span><span class="sxs-lookup"><span data-stu-id="d468d-170">The **Server Roles** page lists all possible roles that can be assigned to the new login.</span></span> <span data-ttu-id="d468d-171">提供了以下选项：</span><span class="sxs-lookup"><span data-stu-id="d468d-171">The following options are available:</span></span>  
  
 <span data-ttu-id="d468d-172">“bulkadmin”复选框</span><span class="sxs-lookup"><span data-stu-id="d468d-172">**bulkadmin** check box</span></span>  
 <span data-ttu-id="d468d-173">**bulkadmin** 固定服务器角色的成员可以运行 BULK INSERT 语句。</span><span class="sxs-lookup"><span data-stu-id="d468d-173">Members of the **bulkadmin** fixed server role can run the BULK INSERT statement.</span></span>  
  
 <span data-ttu-id="d468d-174">“dbcreator”复选框</span><span class="sxs-lookup"><span data-stu-id="d468d-174">**dbcreator** check box</span></span>  
 <span data-ttu-id="d468d-175">**dbcreator** 固定服务器角色的成员可以创建、更改、删除和还原任何数据库。</span><span class="sxs-lookup"><span data-stu-id="d468d-175">Members of the **dbcreator** fixed server role can create, alter, drop, and restore any database.</span></span>  
  
 <span data-ttu-id="d468d-176">“diskadmin”复选框</span><span class="sxs-lookup"><span data-stu-id="d468d-176">**diskadmin** check box</span></span>  
 <span data-ttu-id="d468d-177">**diskadmin** 固定服务器角色的成员可以管理磁盘文件。</span><span class="sxs-lookup"><span data-stu-id="d468d-177">Members of the **diskadmin** fixed server role can manage disk files.</span></span>  
  
 <span data-ttu-id="d468d-178">“processadmin”复选框</span><span class="sxs-lookup"><span data-stu-id="d468d-178">**processadmin** check box</span></span>  
 <span data-ttu-id="d468d-179">**processadmin** 固定服务器角色的成员可以终止在 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]实例中运行的进程。</span><span class="sxs-lookup"><span data-stu-id="d468d-179">Members of the **processadmin** fixed server role can terminate processes running in an instance of the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
 <span data-ttu-id="d468d-180">“public”复选框</span><span class="sxs-lookup"><span data-stu-id="d468d-180">**public** check box</span></span>  
 <span data-ttu-id="d468d-181">默认情况下，所有 SQL Server 用户、组和角色都属于 **public** 固定服务器角色。</span><span class="sxs-lookup"><span data-stu-id="d468d-181">All SQL Server users, groups, and roles belong to the **public** fixed server role by default.</span></span>  
  
 <span data-ttu-id="d468d-182">“securityadmin”复选框</span><span class="sxs-lookup"><span data-stu-id="d468d-182">**securityadmin** check box</span></span>  
 <span data-ttu-id="d468d-183">**securityadmin** 固定服务器角色的成员可以管理登录名及其属性。</span><span class="sxs-lookup"><span data-stu-id="d468d-183">Members of the **securityadmin** fixed server role manage logins and their properties.</span></span> <span data-ttu-id="d468d-184">他们可以 GRANT、DENY 和 REVOKE 服务器级别的权限。</span><span class="sxs-lookup"><span data-stu-id="d468d-184">They can GRANT, DENY, and REVOKE server-level permissions.</span></span> <span data-ttu-id="d468d-185">他们还可以 GRANT、DENY 和 REVOKE 数据库级别的权限。</span><span class="sxs-lookup"><span data-stu-id="d468d-185">They can also GRANT, DENY, and REVOKE database-level permissions.</span></span> <span data-ttu-id="d468d-186">此外，他们还可以重置 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登录名的密码。</span><span class="sxs-lookup"><span data-stu-id="d468d-186">Additionally, they can reset passwords for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] logins.</span></span>  
  
 <span data-ttu-id="d468d-187">“serveradmin”复选框</span><span class="sxs-lookup"><span data-stu-id="d468d-187">**serveradmin** check box</span></span>  
 <span data-ttu-id="d468d-188">**serveradmin** 固定服务器角色的成员可以更改服务器范围的配置选项和关闭服务器。</span><span class="sxs-lookup"><span data-stu-id="d468d-188">Members of the **serveradmin** fixed server role can change server-wide configuration options and shut down the server.</span></span>  
  
 <span data-ttu-id="d468d-189">“setupadmin”复选框</span><span class="sxs-lookup"><span data-stu-id="d468d-189">**setupadmin** check box</span></span>  
 <span data-ttu-id="d468d-190">**setupadmin** 固定服务器角色成员可以添加和删除链接服务器，并可以执行某些系统存储过程。</span><span class="sxs-lookup"><span data-stu-id="d468d-190">Members of the **setupadmin** fixed server role can add and remove linked servers, and they can execute some system stored procedures.</span></span>  
  
 <span data-ttu-id="d468d-191">“sysadmin”复选框</span><span class="sxs-lookup"><span data-stu-id="d468d-191">**sysadmin** check box</span></span>  
 <span data-ttu-id="d468d-192">**sysadmin** 固定服务器角色的成员可以在 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]中执行任何活动。</span><span class="sxs-lookup"><span data-stu-id="d468d-192">Members of the **sysadmin** fixed server role can perform any activity in the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
### <a name="user-mapping"></a><span data-ttu-id="d468d-193">用户映射</span><span class="sxs-lookup"><span data-stu-id="d468d-193">User Mapping</span></span>  
 <span data-ttu-id="d468d-194">**“用户映射”** 页将列出可应用于登录名的所有可能的数据库以及这些数据库上的数据库角色成员身份。</span><span class="sxs-lookup"><span data-stu-id="d468d-194">The **User Mapping** page lists all possible databases and the database role memberships on those databases that can be applied to the login.</span></span> <span data-ttu-id="d468d-195">选定的数据库将确定对登录名可用的角色成员身份。</span><span class="sxs-lookup"><span data-stu-id="d468d-195">The databases selected determine the role memberships that are available for the login.</span></span> <span data-ttu-id="d468d-196">此页还将提供以下选项：</span><span class="sxs-lookup"><span data-stu-id="d468d-196">The following options are available on this page:</span></span>  
  
 <span data-ttu-id="d468d-197">**映射到此登录名的用户**</span><span class="sxs-lookup"><span data-stu-id="d468d-197">**Users mapped to this login**</span></span>  
 <span data-ttu-id="d468d-198">选择此登录名可以访问的数据库。</span><span class="sxs-lookup"><span data-stu-id="d468d-198">Select the databases that this login can access.</span></span> <span data-ttu-id="d468d-199">选择某个数据库时，其有效的数据库角色将会显示在“数据库角色成员身份: _database_name_”窗格中。</span><span class="sxs-lookup"><span data-stu-id="d468d-199">When you select a database, its valid database roles are displayed in the **Database role membership for:** _database_name_ pane.</span></span>  
  
 <span data-ttu-id="d468d-200">**Map**</span><span class="sxs-lookup"><span data-stu-id="d468d-200">**Map**</span></span>  
 <span data-ttu-id="d468d-201">允许登录名访问下面列出的数据库。</span><span class="sxs-lookup"><span data-stu-id="d468d-201">Allow the login to access the databases listed below.</span></span>  
  
 <span data-ttu-id="d468d-202">**Database**</span><span class="sxs-lookup"><span data-stu-id="d468d-202">**Database**</span></span>  
 <span data-ttu-id="d468d-203">列出服务器上可用的数据库。</span><span class="sxs-lookup"><span data-stu-id="d468d-203">Lists the databases available on the server.</span></span>  
  
 <span data-ttu-id="d468d-204">**用户**</span><span class="sxs-lookup"><span data-stu-id="d468d-204">**User**</span></span>  
 <span data-ttu-id="d468d-205">指定要映射到登录名的数据库用户。</span><span class="sxs-lookup"><span data-stu-id="d468d-205">Specify a database user to map to the login.</span></span> <span data-ttu-id="d468d-206">默认情况下，数据库用户名与登录名相同。</span><span class="sxs-lookup"><span data-stu-id="d468d-206">By default, the database user has the same name as the login.</span></span>  
  
 <span data-ttu-id="d468d-207">**默认架构**</span><span class="sxs-lookup"><span data-stu-id="d468d-207">**Default Schema**</span></span>  
 <span data-ttu-id="d468d-208">指定用户的默认架构。</span><span class="sxs-lookup"><span data-stu-id="d468d-208">Specifies the default schema of the user.</span></span> <span data-ttu-id="d468d-209">首次创建用户时，其默认架构是 **dbo**。</span><span class="sxs-lookup"><span data-stu-id="d468d-209">When a user is first created, its default schema is **dbo**.</span></span> <span data-ttu-id="d468d-210">可以指定并不存在的默认架构。</span><span class="sxs-lookup"><span data-stu-id="d468d-210">It is possible to specify a default schema that does not yet exist.</span></span> <span data-ttu-id="d468d-211">对于已映射到 Windows 组、证书或非对称密钥的用户，无法为其指定默认架构。</span><span class="sxs-lookup"><span data-stu-id="d468d-211">You cannot specify a default schema for a user that is mapped to a Windows group, a certificate, or an asymmetric key.</span></span>  
  
 <span data-ttu-id="d468d-212">已启用 Guest 帐户：_database_name_</span><span class="sxs-lookup"><span data-stu-id="d468d-212">**Guest account enabled for:**  _database_name_</span></span>  
 <span data-ttu-id="d468d-213">只读属性，指示所选数据库是否已启用 Guest 帐户。</span><span class="sxs-lookup"><span data-stu-id="d468d-213">Read-only attribute indicating whether the Guest account is enabled on the selected database.</span></span> <span data-ttu-id="d468d-214">可使用 Guest 帐户的 **“登录属性”** 对话框的 **“状态”** 页来启用或禁用 Guest 帐户。</span><span class="sxs-lookup"><span data-stu-id="d468d-214">Use the **Status** page of the **Login Properties** dialog box of the Guest account to enable or disable the Guest account.</span></span>  
  
 <span data-ttu-id="d468d-215">数据库角色成员身份：_database_name_</span><span class="sxs-lookup"><span data-stu-id="d468d-215">**Database role membership for:**  _database_name_</span></span>  
 <span data-ttu-id="d468d-216">选择用户在指定数据库中的角色。</span><span class="sxs-lookup"><span data-stu-id="d468d-216">Select the roles for the user in the specified database.</span></span> <span data-ttu-id="d468d-217">在每个数据库中，所有用户都是 **public** 角色的成员，并且不能被删除。</span><span class="sxs-lookup"><span data-stu-id="d468d-217">All users are members of the **public** role in every database and cannot be removed.</span></span> <span data-ttu-id="d468d-218">有关数据库角色的详细信息，请参阅 [数据库级别的角色](database-level-roles.md)。</span><span class="sxs-lookup"><span data-stu-id="d468d-218">For more information about database roles, see [Database-Level Roles](database-level-roles.md).</span></span>  
  
### <a name="securables"></a><span data-ttu-id="d468d-219">安全对象</span><span class="sxs-lookup"><span data-stu-id="d468d-219">Securables</span></span>  
 <span data-ttu-id="d468d-220">**“安全对象”** 页将列出所有可能的安全对象以及可授予登录名的针对这些安全对象的权限。</span><span class="sxs-lookup"><span data-stu-id="d468d-220">The **Securables** page lists all possible securables and the permissions on those securables that can be granted to the login.</span></span> <span data-ttu-id="d468d-221">此页还将提供以下选项：</span><span class="sxs-lookup"><span data-stu-id="d468d-221">The following options are available on this page:</span></span>  
  
 <span data-ttu-id="d468d-222">**上部网格**</span><span class="sxs-lookup"><span data-stu-id="d468d-222">**Upper Grid**</span></span>  
 <span data-ttu-id="d468d-223">包含一个或多个可以为其设置权限的项目。</span><span class="sxs-lookup"><span data-stu-id="d468d-223">Contains one or more items for which permissions can be set.</span></span> <span data-ttu-id="d468d-224">上部网格中显示的列会根据主体或安全对象的不同而变化。</span><span class="sxs-lookup"><span data-stu-id="d468d-224">The columns that are displayed in the upper grid vary depending on the principal or securable.</span></span>  
  
 <span data-ttu-id="d468d-225">向上部网格中添加项目：</span><span class="sxs-lookup"><span data-stu-id="d468d-225">To add items to the upper grid:</span></span>  
  
1.  <span data-ttu-id="d468d-226">单击 **“搜索”** 。</span><span class="sxs-lookup"><span data-stu-id="d468d-226">Click **Search**.</span></span>  
  
2.  <span data-ttu-id="d468d-227">在 "**添加对象**" 对话框中，选择下列选项之一： "**特定对象 ...**"、 **"类型的所有对象**..." 或 **"服务器**_server_name_"。</span><span class="sxs-lookup"><span data-stu-id="d468d-227">In the **Add Objects** dialog box, select one of the following options: **Specific objects...**, **All objects of the types...**, or **The server**_server_name_.</span></span> [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
    > [!NOTE]  
    >  <span data-ttu-id="d468d-228">选择**服务器**_server_name_会自动用所有服务器的安全对象填充上部网格。</span><span class="sxs-lookup"><span data-stu-id="d468d-228">Selecting **The server**_server_name_ automatically fills the upper grid with all of that servers' securable objects.</span></span>  
  
3.  <span data-ttu-id="d468d-229">如果选择“特定对象…”：</span><span class="sxs-lookup"><span data-stu-id="d468d-229">If you select **Specific objects...**:</span></span>  
  
    1.  <span data-ttu-id="d468d-230">在“选择对象”对话框中的“选择这些对象类型”下，单击“对象类型…”  。</span><span class="sxs-lookup"><span data-stu-id="d468d-230">In the **Select Objects** dialog box, under **Select these object types**, click **Object Types...**.</span></span>  
  
    2.  <span data-ttu-id="d468d-231">在“选择对象类型”对话框中，选择以下任意或全部对象类型：“端点”、“登录名”、“服务器”、“可用性组”和“服务器角色”    。</span><span class="sxs-lookup"><span data-stu-id="d468d-231">In the **Select Object Types** dialog box, select any or all of the following object types: **Endpoints**, **Logins**, **Servers**, **Availability Groups**, and **Server roles**.</span></span> [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
    3.  <span data-ttu-id="d468d-232">在“输入要选择的对象名称(示例)”下，单击“浏览…” 。</span><span class="sxs-lookup"><span data-stu-id="d468d-232">Under **Enter the object names to select (examples)**, click **Browse...**.</span></span>  
  
    4.  <span data-ttu-id="d468d-233">在 **“查找对象”** 对话框中，选择您在 **“选择对象类型”** 对话框中选择的类型的任何可用对象，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="d468d-233">In the **Browse for Objects** dialog box, select any of the available objects of the type that you selected in the **Select Object Types** dialog box, and then click **OK**.</span></span>  
  
    5.  <span data-ttu-id="d468d-234">在 **“选择对象”** 对话框中，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="d468d-234">In the **Select Objects** dialog box, click **OK**.</span></span>  
  
4.  <span data-ttu-id="d468d-235">如果选择“所有类型的对象…”，请在“选择对象类型”对话框中，选择以下任意或全部对象类型： “端点”、“登录名”、“服务器”、“可用性组”和“服务器角色”    。</span><span class="sxs-lookup"><span data-stu-id="d468d-235">If you select **All objects of the types...**, in the **Select Object Types** dialog box, select any or all of the following object types: **Endpoints**, **Logins**, **Servers**, **Availability Groups**, and **Server roles**.</span></span> [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
 <span data-ttu-id="d468d-236">**名称**</span><span class="sxs-lookup"><span data-stu-id="d468d-236">**Name**</span></span>  
 <span data-ttu-id="d468d-237">添加到网格中的每个主体或安全对象的名称。</span><span class="sxs-lookup"><span data-stu-id="d468d-237">The name of each principal or securable that is added to the grid.</span></span>  
  
 <span data-ttu-id="d468d-238">类型</span><span class="sxs-lookup"><span data-stu-id="d468d-238">**Type**</span></span>  
 <span data-ttu-id="d468d-239">描述每个项目的类型。</span><span class="sxs-lookup"><span data-stu-id="d468d-239">Describes the type of each item.</span></span>  
  
 <span data-ttu-id="d468d-240">**“显式”选项卡**</span><span class="sxs-lookup"><span data-stu-id="d468d-240">**Explicit Tab**</span></span>  
 <span data-ttu-id="d468d-241">列出了上部网格中选定的安全对象的可能权限。</span><span class="sxs-lookup"><span data-stu-id="d468d-241">Lists the possible permissions for the securable that are selected in the upper grid.</span></span> <span data-ttu-id="d468d-242">并非所有选项均用于任何显式权限。</span><span class="sxs-lookup"><span data-stu-id="d468d-242">Not all options are available for all explicit permissions.</span></span>  
  
 <span data-ttu-id="d468d-243">**权限**</span><span class="sxs-lookup"><span data-stu-id="d468d-243">**Permissions**</span></span>  
 <span data-ttu-id="d468d-244">权限的名称。</span><span class="sxs-lookup"><span data-stu-id="d468d-244">The name of the permission.</span></span>  
  
 <span data-ttu-id="d468d-245">**授权者**</span><span class="sxs-lookup"><span data-stu-id="d468d-245">**Grantor**</span></span>  
 <span data-ttu-id="d468d-246">授予该权限的主体。</span><span class="sxs-lookup"><span data-stu-id="d468d-246">The principal that granted the permission.</span></span>  
  
 <span data-ttu-id="d468d-247">**授予**</span><span class="sxs-lookup"><span data-stu-id="d468d-247">**Grant**</span></span>  
 <span data-ttu-id="d468d-248">选中该选项可以将此权限授予该登录名。</span><span class="sxs-lookup"><span data-stu-id="d468d-248">Select to grant this permission to the login.</span></span> <span data-ttu-id="d468d-249">清除该选项将撤消此权限。</span><span class="sxs-lookup"><span data-stu-id="d468d-249">Clear to revoke this permission.</span></span>  
  
 <span data-ttu-id="d468d-250">**具有授予权限**</span><span class="sxs-lookup"><span data-stu-id="d468d-250">**With Grant**</span></span>  
 <span data-ttu-id="d468d-251">反映所列权限的 WITH GRANT 选项的状态。</span><span class="sxs-lookup"><span data-stu-id="d468d-251">Reflects the state of the WITH GRANT option for the listed permission.</span></span> <span data-ttu-id="d468d-252">此框是只读的。</span><span class="sxs-lookup"><span data-stu-id="d468d-252">This box is read-only.</span></span> <span data-ttu-id="d468d-253">若要应用此权限，请使用 [GRANT](/sql/t-sql/statements/grant-transact-sql) 语句。</span><span class="sxs-lookup"><span data-stu-id="d468d-253">To apply this permission, use the [GRANT](/sql/t-sql/statements/grant-transact-sql) statement.</span></span>  
  
 <span data-ttu-id="d468d-254">**拒绝**</span><span class="sxs-lookup"><span data-stu-id="d468d-254">**Deny**</span></span>  
 <span data-ttu-id="d468d-255">选中该选项可以拒绝该登录名具有该权限。</span><span class="sxs-lookup"><span data-stu-id="d468d-255">Select to deny this permission to the login.</span></span> <span data-ttu-id="d468d-256">清除该选项将撤消此权限。</span><span class="sxs-lookup"><span data-stu-id="d468d-256">Clear to revoke this permission.</span></span>  
  
### <a name="status"></a><span data-ttu-id="d468d-257">状态</span><span class="sxs-lookup"><span data-stu-id="d468d-257">Status</span></span>  
 <span data-ttu-id="d468d-258">**“状态”** 页将列出可对选定的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登录名配置的一些身份验证和授权选项。</span><span class="sxs-lookup"><span data-stu-id="d468d-258">The **Status** page lists some of the authentication and authorization options that can be configured on the selected [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] login.</span></span>  
  
 <span data-ttu-id="d468d-259">此页还将提供以下选项：</span><span class="sxs-lookup"><span data-stu-id="d468d-259">The following options are available on this page:</span></span>  
  
 <span data-ttu-id="d468d-260">**连接到数据库引擎的权限**</span><span class="sxs-lookup"><span data-stu-id="d468d-260">**Permission to connect to database engine**</span></span>  
 <span data-ttu-id="d468d-261">当使用此设置时，应将所选登录名视为可授予或拒绝授予其对安全对象的访问权限的主体。</span><span class="sxs-lookup"><span data-stu-id="d468d-261">When you work with this setting, you should think of the selected login as a principal that can be granted or denied permission on a securable.</span></span>  
  
 <span data-ttu-id="d468d-262">如果选择 **“授予”** ，将向登录名授予 CONNECT SQL 权限。</span><span class="sxs-lookup"><span data-stu-id="d468d-262">Select **Grant** to grant CONNECT SQL permission to the login.</span></span> <span data-ttu-id="d468d-263">如果选择 **“拒绝”** ，将拒绝向登录名授予 CONNECT SQL 权限。</span><span class="sxs-lookup"><span data-stu-id="d468d-263">Select **Deny** to deny CONNECT SQL to the login.</span></span>  
  
 <span data-ttu-id="d468d-264">**登录**</span><span class="sxs-lookup"><span data-stu-id="d468d-264">**Login**</span></span>  
 <span data-ttu-id="d468d-265">当使用此设置时，应将所选登录名视为表中的记录。</span><span class="sxs-lookup"><span data-stu-id="d468d-265">When you work with this setting, you should think of the selected login as a record in a table.</span></span> <span data-ttu-id="d468d-266">对此处列出的值的更改将应用于该记录。</span><span class="sxs-lookup"><span data-stu-id="d468d-266">Changes to the values listed here will be applied to the record.</span></span>  
  
 <span data-ttu-id="d468d-267">已禁用的登录名继续作为记录存在。</span><span class="sxs-lookup"><span data-stu-id="d468d-267">A login that has been disabled continues to exist as a record.</span></span> <span data-ttu-id="d468d-268">但是如果它尝试连接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]，则登录名将不能通过身份验证。</span><span class="sxs-lookup"><span data-stu-id="d468d-268">But if it tries to connect to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the login will not be authenticated.</span></span>  
  
 <span data-ttu-id="d468d-269">选择此选项以启用或禁用此登录名。</span><span class="sxs-lookup"><span data-stu-id="d468d-269">Select this option to enable or disable this login.</span></span> <span data-ttu-id="d468d-270">此选项将 ALTER LOGIN 语句与 ENABLE 或者 DISABLE 选项配合使用。</span><span class="sxs-lookup"><span data-stu-id="d468d-270">This option uses the ALTER LOGIN statement with the either ENABLE or DISABLE option.</span></span>  
  
 <span data-ttu-id="d468d-271">**SQL Server 身份验证**</span><span class="sxs-lookup"><span data-stu-id="d468d-271">**SQL Server Authentication**</span></span>  
 <span data-ttu-id="d468d-272">仅当所选的登录名使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 身份验证进行连接并且登录名已锁定时，复选框“登录名已锁定”才可用。该设置是只读的。</span><span class="sxs-lookup"><span data-stu-id="d468d-272">The check box **Login is locked out** is only available if the selected login connects using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication and the login has been locked out. This setting is read-only.</span></span> <span data-ttu-id="d468d-273">若要解除对已锁定登录名的锁定，请执行带 UNLOCK 选项的 ALTER LOGIN。</span><span class="sxs-lookup"><span data-stu-id="d468d-273">To unlock a login that is locked out, execute ALTER LOGIN with the UNLOCK option.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="d468d-274">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d468d-274">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-login-using-windows-authentication"></a><span data-ttu-id="d468d-275">创建使用 Windows 身份验证的登录名</span><span class="sxs-lookup"><span data-stu-id="d468d-275">To create a login using Windows Authentication</span></span>  
  
1.  <span data-ttu-id="d468d-276">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="d468d-276">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="d468d-277">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="d468d-277">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d468d-278">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="d468d-278">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Create a login for SQL Server by specifying a server name and a Windows domain account name.  
  
    CREATE LOGIN [<domainName>\<loginName>] FROM WINDOWS;  
    GO  
  
    ```  
  
#### <a name="to-create-a-login-using-sql-server-authentication"></a><span data-ttu-id="d468d-279">创建使用 SQL Server 身份验证的登录名</span><span class="sxs-lookup"><span data-stu-id="d468d-279">To create a login using SQL Server Authentication</span></span>  
  
1.  <span data-ttu-id="d468d-280">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="d468d-280">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="d468d-281">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="d468d-281">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d468d-282">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="d468d-282">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Creates the user "shcooper" for SQL Server using the security credential "RestrictedFaculty"   
    -- The user login starts with the password "Baz1nga," but that password must be changed after the first login.  
  
    CREATE LOGIN shcooper   
       WITH PASSWORD = 'Baz1nga' MUST_CHANGE,  
       CREDENTIAL = RestrictedFaculty;  
    GO  
  
    ```  
  
 <span data-ttu-id="d468d-283">有关详细信息，请参阅 [CREATE LOGIN (Transact-SQL)](/sql/t-sql/statements/create-login-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="d468d-283">For more information, see [CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql).</span></span>  
  
##  <a name="follow-up-steps-to-take-after-you-create-a-login"></a><a name="FollowUp"></a> <span data-ttu-id="d468d-284">跟进：在创建登录名后采取的步骤</span><span class="sxs-lookup"><span data-stu-id="d468d-284">Follow Up: Steps to take after you create a login</span></span>  
 <span data-ttu-id="d468d-285">创建登录名后，该登录名可连接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]，但不一定有执行任何有用工作的充分权限。</span><span class="sxs-lookup"><span data-stu-id="d468d-285">After creating a login, the login can connect to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], but does not necessarily have sufficient permission to perform any useful work.</span></span> <span data-ttu-id="d468d-286">下面的列表提供了指向常见登录操作的链接。</span><span class="sxs-lookup"><span data-stu-id="d468d-286">The following list provides links to common login actions.</span></span>  
  
-   <span data-ttu-id="d468d-287">若要将登录名加入某一角色，请参阅 [加入角色](join-a-role.md)。</span><span class="sxs-lookup"><span data-stu-id="d468d-287">To have the login join a role, see [Join a Role](join-a-role.md).</span></span>  
  
-   <span data-ttu-id="d468d-288">若要授权登录名使用数据库，请参阅 [创建数据库用户](../authentication-access/create-a-database-user.md)。</span><span class="sxs-lookup"><span data-stu-id="d468d-288">To authorize a login to use a database, see [Create a Database User](../authentication-access/create-a-database-user.md).</span></span>  
  
-   <span data-ttu-id="d468d-289">若要向登录名授予权限，请参阅 [向主体授予权限](grant-a-permission-to-a-principal.md)。</span><span class="sxs-lookup"><span data-stu-id="d468d-289">To grant a permission to a login, see [Grant a Permission to a Principal](grant-a-permission-to-a-principal.md).</span></span>  
  
  
