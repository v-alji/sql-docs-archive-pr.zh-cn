---
title: 创建凭据 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- credentials [SQL Server], creating
- authentication [SQL Server], credentials
- logins [SQL Server], credentials
ms.assetid: c1e77e91-2a69-40d9-b8b3-97cffc710586
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 23221424699449ac3775b0e805bb02ae0ad233f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688770"
---
# <a name="create-a-credential"></a><span data-ttu-id="2c4cd-102">创建凭据</span><span class="sxs-lookup"><span data-stu-id="2c4cd-102">Create a Credential</span></span>
  <span data-ttu-id="2c4cd-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中创建凭据。</span><span class="sxs-lookup"><span data-stu-id="2c4cd-103">This topic describes how to create a credential in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="2c4cd-104">凭据是 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 身份验证用户在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]外部的身份标识。</span><span class="sxs-lookup"><span data-stu-id="2c4cd-104">Credentials provide a way to allow [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication users to have an identity outside of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="2c4cd-105">主要用于执行具有 EXTERNAL_ACCESS 权限集的程序集中的代码。</span><span class="sxs-lookup"><span data-stu-id="2c4cd-105">This is primarily used to execute code in Assemblies with EXTERNAL_ACCESS permission set.</span></span> <span data-ttu-id="2c4cd-106">当 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 身份验证用户需要访问域资源（例如存储备份的文件位置）时，也可以使用凭据。</span><span class="sxs-lookup"><span data-stu-id="2c4cd-106">Credentials can also be used when a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication user needs access to a domain resource, such as a file location to store a backup.</span></span>  
  
 <span data-ttu-id="2c4cd-107">可以将一个凭据同时映射到多个 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登录名。</span><span class="sxs-lookup"><span data-stu-id="2c4cd-107">A credential can be mapped to several [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] logins at the same time.</span></span> <span data-ttu-id="2c4cd-108">一个 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登录名一次只能映射到一个凭据。</span><span class="sxs-lookup"><span data-stu-id="2c4cd-108">A [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] login can only be mapped to one credential at a time.</span></span> <span data-ttu-id="2c4cd-109">在创建凭据之后，可以使用“登录属性”（“常规”页）将登录名映射到凭据。</span><span class="sxs-lookup"><span data-stu-id="2c4cd-109">After a credential is created, use the **Login Properties (General Page)** to map a login to a credential.</span></span>  
  
 <span data-ttu-id="2c4cd-110">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="2c4cd-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="2c4cd-111">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="2c4cd-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="2c4cd-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="2c4cd-112">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="2c4cd-113">安全性</span><span class="sxs-lookup"><span data-stu-id="2c4cd-113">Security</span></span>](#Security)  
  
-   <span data-ttu-id="2c4cd-114">**若要创建凭据，可使用：**</span><span class="sxs-lookup"><span data-stu-id="2c4cd-114">**To create a credential, using:**</span></span>  
  
     [<span data-ttu-id="2c4cd-115">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2c4cd-115">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="2c4cd-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2c4cd-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2c4cd-117">开始之前</span><span class="sxs-lookup"><span data-stu-id="2c4cd-117">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="2c4cd-118">限制和局限</span><span class="sxs-lookup"><span data-stu-id="2c4cd-118">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="2c4cd-119">如果该提供程序没有任何登录名映射的凭据，则使用映射到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服务帐户的凭据。</span><span class="sxs-lookup"><span data-stu-id="2c4cd-119">If there is no login mapped credential for the provider, the credential mapped to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service account is used.</span></span>  
  
-   <span data-ttu-id="2c4cd-120">一个登录名可以有多个映射的凭据，只要它们用于不同的提供程序即可。</span><span class="sxs-lookup"><span data-stu-id="2c4cd-120">A login can have multiple credentials mapped to it as long as they are used with distinctive providers.</span></span> <span data-ttu-id="2c4cd-121">每个登录名的每个提供程序只能有一个映射的凭据。</span><span class="sxs-lookup"><span data-stu-id="2c4cd-121">There must be only one mapped credential per provider per login.</span></span> <span data-ttu-id="2c4cd-122">相同的凭据可以映射到其他登录名。</span><span class="sxs-lookup"><span data-stu-id="2c4cd-122">The same credential can be mapped to other logins.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="2c4cd-123">Security</span><span class="sxs-lookup"><span data-stu-id="2c4cd-123">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="2c4cd-124">权限</span><span class="sxs-lookup"><span data-stu-id="2c4cd-124">Permissions</span></span>  
 <span data-ttu-id="2c4cd-125">必须具有 ALTER ANY CREDENTIAL 权限才能创建或修改凭据，并且必须具有 ALTER ANY LOGIN 权限才能将登录名映射到凭据。</span><span class="sxs-lookup"><span data-stu-id="2c4cd-125">Requires ALTER ANY CREDENTIAL permission to create or modify a credential and ALTER ANY LOGIN permission to map a login to a credential.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2c4cd-126">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2c4cd-126">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-credential"></a><span data-ttu-id="2c4cd-127">创建凭据</span><span class="sxs-lookup"><span data-stu-id="2c4cd-127">To create a credential</span></span>  
  
1.  <span data-ttu-id="2c4cd-128">在对象资源管理器中，展开“安全性”  文件夹。</span><span class="sxs-lookup"><span data-stu-id="2c4cd-128">In Object Explorer, expand  the **Security** folder.</span></span>  
  
2.  <span data-ttu-id="2c4cd-129">右键单击“凭据”文件夹，然后选择“新建凭据…” 。</span><span class="sxs-lookup"><span data-stu-id="2c4cd-129">Right-click the **Credentials** folder and select **New Credential...**.</span></span>  
  
3.  <span data-ttu-id="2c4cd-130">在 **“新建凭据”** 对话框中的 **“凭据名称”** 框中，键入凭据的名称。</span><span class="sxs-lookup"><span data-stu-id="2c4cd-130">In the **New Credential** dialog box, in the **Credential Name** box, type a name for the credential.</span></span>  
  
4.  <span data-ttu-id="2c4cd-131">在“标识”框中，键入用于传出连接的帐户名称（在离开 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的上下文时）。</span><span class="sxs-lookup"><span data-stu-id="2c4cd-131">In the **Identity** box, type the name of the account used for outgoing connections (when leaving the context of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]).</span></span> <span data-ttu-id="2c4cd-132">通常为 Windows 用户帐户，但标识可以为其他类型的帐户。</span><span class="sxs-lookup"><span data-stu-id="2c4cd-132">Typically, this will be a Windows user account, but the identity can be an account of another type.</span></span>  
  
     <span data-ttu-id="2c4cd-133">或者，单击省略号“(…)”打开“选择用户或组”对话框 。</span><span class="sxs-lookup"><span data-stu-id="2c4cd-133">Alternately, click the ellipsis **(...)** to open the **Select User or Group** dialog box.</span></span>  
  
5.  <span data-ttu-id="2c4cd-134">在 **“密码”** 和 **“确认密码”** 框中，键入 **“标识”** 框中指定的帐户的密码。</span><span class="sxs-lookup"><span data-stu-id="2c4cd-134">In the **Password** and **Confirm password** boxes, type the password of the account specified in the **Identity** box.</span></span> <span data-ttu-id="2c4cd-135">如果 **“标识”** 为 Windows 用户帐户，则密码为 Windows 密码。</span><span class="sxs-lookup"><span data-stu-id="2c4cd-135">If **Identity** is a Windows user account, this is the Windows password.</span></span> <span data-ttu-id="2c4cd-136">如果不需要密码， **“密码”** 可为空。</span><span class="sxs-lookup"><span data-stu-id="2c4cd-136">The **Password** can be blank, if no password is required.</span></span>  
  
6.  <span data-ttu-id="2c4cd-137">选择“使用加密提供程序”将凭据设置为由可扩展的密钥管理 (EKM) 提供程序验证。</span><span class="sxs-lookup"><span data-stu-id="2c4cd-137">Select **Use Encryption Provider** to set the credential to be verified by an Extensible Key Management (EKM) Provider.</span></span> <span data-ttu-id="2c4cd-138">有关详细信息，请参阅[可扩展的密钥管理 (EKM)](../encryption/extensible-key-management-ekm.md)</span><span class="sxs-lookup"><span data-stu-id="2c4cd-138">For more information, see [Extensible Key Management &#40;EKM&#41;](../encryption/extensible-key-management-ekm.md)</span></span>  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="2c4cd-139">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2c4cd-139">Using Transact-SQL</span></span>  
  
###  <a name="to-create-a-credential"></a><a name="Credential"></a><span data-ttu-id="2c4cd-140">创建凭据</span><span class="sxs-lookup"><span data-stu-id="2c4cd-140">To create a credential</span></span>  
  
1.  <span data-ttu-id="2c4cd-141">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="2c4cd-141">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="2c4cd-142">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="2c4cd-142">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="2c4cd-143">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="2c4cd-143">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Creates the credential called "AlterEgo.".   
    -- The credential contains the Windows user "Mary5" and a password.  
    CREATE CREDENTIAL AlterEgo WITH IDENTITY = 'Mary5',   
        SECRET = '<EnterStrongPasswordHere>';  
    GO  
    ```  
  
 <span data-ttu-id="2c4cd-144">有关详细信息，请参阅 [CREATE CREDENTIAL (Transact-SQL)](/sql/t-sql/statements/create-credential-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2c4cd-144">For more information, see [CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql).</span></span>  
  
  
