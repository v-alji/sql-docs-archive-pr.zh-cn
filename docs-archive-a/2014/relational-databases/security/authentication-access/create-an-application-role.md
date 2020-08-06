---
title: 创建应用程序角色 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.approle.general.f1
helpviewer_keywords:
- application roles [SQL Server], creating
ms.assetid: 6b8da1f5-3d8e-4f88-b111-b915788b06f1
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 51272dad57558cdb771f9b98a2f5e5b3da7609cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589481"
---
# <a name="create-an-application-role"></a><span data-ttu-id="23069-102">创建应用程序角色</span><span class="sxs-lookup"><span data-stu-id="23069-102">Create an Application Role</span></span>
  <span data-ttu-id="23069-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中创建应用程序角色。</span><span class="sxs-lookup"><span data-stu-id="23069-103">This topic describes how to create an application role in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="23069-104">应用程序角色可限制用户通过除特定应用程序之外的其他方式访问数据库。</span><span class="sxs-lookup"><span data-stu-id="23069-104">Application roles restrict user access to a database except through specific applications.</span></span> <span data-ttu-id="23069-105">应用程序角色不包含任何用户，因此，在选择 **“应用程序角色”** 时不会显示 **“角色成员”** 列表。</span><span class="sxs-lookup"><span data-stu-id="23069-105">Application roles have no users, so the **Role Members** list is not displayed when **Application role** is selected.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="23069-106">当设置应用程序角色密码时，将检查密码复杂性。</span><span class="sxs-lookup"><span data-stu-id="23069-106">Password complexity is checked when application role passwords are set.</span></span> <span data-ttu-id="23069-107">调用应用程序角色的应用程序必须存储其密码。</span><span class="sxs-lookup"><span data-stu-id="23069-107">Applications that invoke application roles must store their passwords.</span></span> <span data-ttu-id="23069-108">而且应当始终以加密的形式存储应用程序角色密码。</span><span class="sxs-lookup"><span data-stu-id="23069-108">Application role passwords should always be stored encrypted.</span></span>  
  
 <span data-ttu-id="23069-109">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="23069-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="23069-110">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="23069-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="23069-111">安全性</span><span class="sxs-lookup"><span data-stu-id="23069-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="23069-112">**若要创建应用程序角色，请使用：**</span><span class="sxs-lookup"><span data-stu-id="23069-112">**To create an application role, using:**</span></span>  
  
     [<span data-ttu-id="23069-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="23069-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="23069-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="23069-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="23069-115">开始之前</span><span class="sxs-lookup"><span data-stu-id="23069-115">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="23069-116">Security</span><span class="sxs-lookup"><span data-stu-id="23069-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="23069-117">权限</span><span class="sxs-lookup"><span data-stu-id="23069-117">Permissions</span></span>  
 <span data-ttu-id="23069-118">需要对数据库具有 ALTER ANY APPLICATION ROLE 权限。</span><span class="sxs-lookup"><span data-stu-id="23069-118">Requires ALTER ANY APPLICATION ROLE permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="23069-119">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="23069-119">Using SQL Server Management Studio</span></span>  
  
##### <a name="to-create-an-application-role"></a><span data-ttu-id="23069-120">创建应用程序角色</span><span class="sxs-lookup"><span data-stu-id="23069-120">To create an application role</span></span>  
  
1.  <span data-ttu-id="23069-121">在“对象资源管理器”中，展开要创建应用程序角色的数据库。</span><span class="sxs-lookup"><span data-stu-id="23069-121">In Object Explorer, expand the database where you want to create an application role.</span></span>  
  
2.  <span data-ttu-id="23069-122">展开 **“安全性”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="23069-122">Expand the **Security** folder.</span></span>  
  
3.  <span data-ttu-id="23069-123">展开 **“角色”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="23069-123">Expand the **Roles** folder.</span></span>  
  
4.  <span data-ttu-id="23069-124">右键单击“应用程序角色”文件夹，然后选择“新建应用程序角色…” 。</span><span class="sxs-lookup"><span data-stu-id="23069-124">Right-click the **Application Roles** folder and select **New Application Role...**.</span></span>  
  
5.  <span data-ttu-id="23069-125">在“常规”页的“应用程序角色 - 新建”对话框中，在“角色名称”框中输入新的应用程序角色的新名称  。</span><span class="sxs-lookup"><span data-stu-id="23069-125">In the **Application Role - New** dialog box, on the **General Page**, enter the new name of the new application role in the **Role name** box.</span></span>  
  
6.  <span data-ttu-id="23069-126">在 **“默认架构”** 框中，通过输入对象名称指定将拥有此角色创建的对象的架构。</span><span class="sxs-lookup"><span data-stu-id="23069-126">In the **Default Schema** box, specify the schema that will own objects created by this role by entering the object names.</span></span> <span data-ttu-id="23069-127">或者，单击省略号“(…)”以打开“定位架构”对话框 。</span><span class="sxs-lookup"><span data-stu-id="23069-127">Alternately, click the ellipsis **(...)** to open the **Locate Schema** dialog box.</span></span>  
  
7.  <span data-ttu-id="23069-128">在 **“密码”** 框中，输入新角色的密码。</span><span class="sxs-lookup"><span data-stu-id="23069-128">In the **Password** box, enter a password for the new role.</span></span> <span data-ttu-id="23069-129">在“确认密码”框中再次输入该密码。</span><span class="sxs-lookup"><span data-stu-id="23069-129">Enter that password again into the **Confirm Password** box.</span></span>  
  
8.  <span data-ttu-id="23069-130">在 **“此角色拥有的架构”** ，选择或查看此角色将拥有的架构。</span><span class="sxs-lookup"><span data-stu-id="23069-130">Under **Schemas owned by this role**, select or view schemas that will be owned by this role.</span></span> <span data-ttu-id="23069-131">架构只能由一个架构或角色拥有。</span><span class="sxs-lookup"><span data-stu-id="23069-131">A schema can be owned by only one schema or role.</span></span>  
  
9. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="additional-options"></a><span data-ttu-id="23069-132">其他选项</span><span class="sxs-lookup"><span data-stu-id="23069-132">Additional Options</span></span>  
 <span data-ttu-id="23069-133">“应用程序角色 - 新建”对话框还在两个其他页上提供了选项：“安全对象”和“扩展属性” 。</span><span class="sxs-lookup"><span data-stu-id="23069-133">The **Application Role - New** dialog box also offers options on two additional pages: **Securables** and **Extended Properties**.</span></span>  
  
-   <span data-ttu-id="23069-134">**“安全对象”** 页将列出所有可能的安全对象以及可授予登录名的针对这些安全对象的权限。</span><span class="sxs-lookup"><span data-stu-id="23069-134">The **Securables** page lists all possible securables and the permissions on those securables that can be granted to the login.</span></span>  
  
-   <span data-ttu-id="23069-135">**“扩展属性”** 页允许您向数据库用户添加自定义属性。</span><span class="sxs-lookup"><span data-stu-id="23069-135">The **Extended properties** page allows you to add custom properties to database users.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="23069-136">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="23069-136">Using Transact-SQL</span></span>  
  
#### <a name="to-create-an-application-role"></a><span data-ttu-id="23069-137">创建应用程序角色</span><span class="sxs-lookup"><span data-stu-id="23069-137">To create an application role</span></span>  
  
1.  <span data-ttu-id="23069-138">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="23069-138">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="23069-139">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="23069-139">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="23069-140">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="23069-140">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Creates an application role called "weekly_receipts" that has the password "987Gbv876sPYY5m23" and "Sales" as its default schema.  
  
    CREATE APPLICATION ROLE weekly_receipts   
        WITH PASSWORD = '987G^bv876sPY)Y5m23'   
        , DEFAULT_SCHEMA = Sales;  
    GO  
    ```  
  
 <span data-ttu-id="23069-141">有关详细信息，请参阅 [CREATE APPLICATION ROLE (Transact-SQL) ](/sql/t-sql/statements/create-application-role-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="23069-141">For more information, see [CREATE APPLICATION ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-application-role-transact-sql).</span></span>  
  
  
