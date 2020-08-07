---
title: 创建 SQL Server 代理程序代理 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- proxies [SQL Server Agent], creating
ms.assetid: 142e0c55-a8b9-4669-be49-b9dc602d5988
author: stevestein
ms.author: sstein
ms.openlocfilehash: a7582aef38d57b15de968d96357e56c1974d733e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588813"
---
# <a name="create-a-sql-server-agent-proxy"></a><span data-ttu-id="e890c-102">创建 SQL Server 代理的代理帐户</span><span class="sxs-lookup"><span data-stu-id="e890c-102">Create a SQL Server Agent Proxy</span></span>
  <span data-ttu-id="e890c-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中创建 SQL Server 代理的代理。</span><span class="sxs-lookup"><span data-stu-id="e890c-103">This topic describes how to create a SQL Server Agent proxy in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="e890c-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理的代理帐户定义作业步骤可以运行的安全上下文。</span><span class="sxs-lookup"><span data-stu-id="e890c-104">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent proxy account defines a security context in which a job step can run.</span></span> <span data-ttu-id="e890c-105">每个代理对应于一个安全凭据。</span><span class="sxs-lookup"><span data-stu-id="e890c-105">Each proxy corresponds to a security credential.</span></span> <span data-ttu-id="e890c-106">若要设置特定作业步骤的权限，请创建一个具有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理子系统所需权限的代理，再将该代理分配给该作业步骤。</span><span class="sxs-lookup"><span data-stu-id="e890c-106">To set permissions for a particular job step, create a proxy that has the required permissions for a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent subsystem, and then assign that proxy to the job step.</span></span>  
  
 <span data-ttu-id="e890c-107">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="e890c-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="e890c-108">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="e890c-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="e890c-109">限制和局限</span><span class="sxs-lookup"><span data-stu-id="e890c-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="e890c-110">安全性</span><span class="sxs-lookup"><span data-stu-id="e890c-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="e890c-111">**若要创建 SQL Server 代理的代理帐户，请使用：**</span><span class="sxs-lookup"><span data-stu-id="e890c-111">**To create a SQL Server Agent proxy, using:**</span></span>  
  
     [<span data-ttu-id="e890c-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e890c-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="e890c-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e890c-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e890c-114">开始之前</span><span class="sxs-lookup"><span data-stu-id="e890c-114">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="e890c-115">限制和局限</span><span class="sxs-lookup"><span data-stu-id="e890c-115">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="e890c-116">如果没有凭据，那么在创建代理之前必须先创建凭据。</span><span class="sxs-lookup"><span data-stu-id="e890c-116">You must create a credential before you create a proxy if one is not already available.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="e890c-117">代理的代理帐户使用凭据存储 Windows 用户帐户的相关信息。</span><span class="sxs-lookup"><span data-stu-id="e890c-117">Agent proxies use credentials to store information about Windows user accounts.</span></span> <span data-ttu-id="e890c-118">凭据中指定的用户必须对正在运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的计算机具有“以批处理作业登录”权限。</span><span class="sxs-lookup"><span data-stu-id="e890c-118">The user specified in the credential must have "Log on as a batch job" permission on the computer on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="e890c-119">代理检查代理帐户的子系统访问权限，并在每次运行作业步骤时向代理帐户授予访问权限。</span><span class="sxs-lookup"><span data-stu-id="e890c-119">Agent checks subsystem access for a proxy and gives access to the proxy each time the job step runs.</span></span> <span data-ttu-id="e890c-120">如果代理对子系统不再具有访问权限，则作业步骤将失败。</span><span class="sxs-lookup"><span data-stu-id="e890c-120">If the proxy no longer has access to the subsystem, the job step fails.</span></span> <span data-ttu-id="e890c-121">否则，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理将模拟代理帐户中指定的用户并运行作业步骤。</span><span class="sxs-lookup"><span data-stu-id="e890c-121">Otherwise, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent impersonates the user that is specified in the proxy and runs the job step.</span></span>  
  
-   <span data-ttu-id="e890c-122">创建代理帐户不会更改凭据中指定的用户对代理帐户具有的权限。</span><span class="sxs-lookup"><span data-stu-id="e890c-122">Creation of a proxy does not change the permissions for the user that is specified in the credential for the proxy.</span></span> <span data-ttu-id="e890c-123">例如，您可以为不具有连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例的权限的用户创建代理帐户。</span><span class="sxs-lookup"><span data-stu-id="e890c-123">For example, you can create a proxy for a user that does not have permission to connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e890c-124">在这种情况下，使用该代理帐户的作业步骤无法连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e890c-124">In this case, job steps that use that proxy are unable to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="e890c-125">如果用户的登录帐户具有访问代理帐户的权限，或者用户属于具有访问代理帐户的权限的任何角色，则用户可以在作业步骤中使用代理帐户。</span><span class="sxs-lookup"><span data-stu-id="e890c-125">If the login for the user has access to the proxy, or the user belongs to any role with access to the proxy, the user can use the proxy in a job step.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e890c-126">Security</span><span class="sxs-lookup"><span data-stu-id="e890c-126">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e890c-127">权限</span><span class="sxs-lookup"><span data-stu-id="e890c-127">Permissions</span></span>  
  
-   <span data-ttu-id="e890c-128">只有 **sysadmin** 固定服务器角色的成员才有权创建、修改或删除代理帐户。</span><span class="sxs-lookup"><span data-stu-id="e890c-128">Only members of the **sysadmin** fixed server role have permission to create, modify, or delete proxy accounts.</span></span> <span data-ttu-id="e890c-129">必须将不属于 **sysadmin** 固定服务器角色的成员的用户添加到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **数据库中的以下** 代理固定数据库角色之一，才能使用代理： **SQLAgentUserRole**、 **SQLAgentReaderRole**或 **SQLAgentOperatorRole**。</span><span class="sxs-lookup"><span data-stu-id="e890c-129">Users who are not members of the **sysadmin** fixed server role must be added to one of the following [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles in the **msdb** database to use proxies: **SQLAgentUserRole**, **SQLAgentReaderRole**, or **SQLAgentOperatorRole**.</span></span>  
  
-   <span data-ttu-id="e890c-130">如果除了代理之外还需要创建凭据，则要求 `ALTER ANY CREDENTIAL` 权限。</span><span class="sxs-lookup"><span data-stu-id="e890c-130">Requires `ALTER ANY CREDENTIAL` permission if creating a credential in addition to the proxy.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e890c-131">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e890c-131">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-sql-server-agent-proxy"></a><span data-ttu-id="e890c-132">创建 SQL Server 代理的代理帐户</span><span class="sxs-lookup"><span data-stu-id="e890c-132">To create a SQL Server Agent proxy</span></span>  
  
1.  <span data-ttu-id="e890c-133">在 **“对象资源管理器”** 中，单击加号以展开要在 SQL Server 代理上创建代理的服务器。</span><span class="sxs-lookup"><span data-stu-id="e890c-133">In **Object Explorer**, click the plus sign to expand the server where you want to create a proxy on SQL Server Agent.</span></span>  
  
2.  <span data-ttu-id="e890c-134">单击加号以展开 **“SQL Server 代理”**。</span><span class="sxs-lookup"><span data-stu-id="e890c-134">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="e890c-135">右键单击“代理”\*\*\*\* 文件夹，然后选择“新建代理”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e890c-135">Right-click the **Proxies** folder and select **New Proxy**.</span></span>  
  
4.  <span data-ttu-id="e890c-136">在 **“新建代理帐户”** 对话框的 **“常规”** 页中，在 **“代理名称”** 框中输入代理帐户的名称。</span><span class="sxs-lookup"><span data-stu-id="e890c-136">On the **New Proxy Account** dialog box, on the **General** page, enter the name of the proxy account in the **Proxy name** box.</span></span>  
  
5.  <span data-ttu-id="e890c-137">在 **“凭据名称”** 框中，输入代理帐户将使用的安全凭据的名称。</span><span class="sxs-lookup"><span data-stu-id="e890c-137">In the **Credential name** box, enter the name of the security credential that the proxy account will use.</span></span>  
  
6.  <span data-ttu-id="e890c-138">在 **“说明”** 框中输入对代理帐户的说明。</span><span class="sxs-lookup"><span data-stu-id="e890c-138">In the **Description** box, enter a description for the proxy account</span></span>  
  
7.  <span data-ttu-id="e890c-139">在 **“对以下子系统有效”** 之下，为此代理选择适当的子系统。</span><span class="sxs-lookup"><span data-stu-id="e890c-139">Under **Active to the following subsystems**, select the appropriate subsystem or subsystems for this proxy.</span></span>  
  
8.  <span data-ttu-id="e890c-140">在 **“主体”** 页上，添加或删除登录名或角色，以授予或删除对代理帐户的访问权限。</span><span class="sxs-lookup"><span data-stu-id="e890c-140">On the **Principals** page, add or remove logins or roles to grant or remove access to the proxy account.</span></span>  
  
9. <span data-ttu-id="e890c-141">完成后，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="e890c-141">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="e890c-142">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e890c-142">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-sql-server-agent-proxy"></a><span data-ttu-id="e890c-143">创建 SQL Server 代理的代理帐户</span><span class="sxs-lookup"><span data-stu-id="e890c-143">To create a SQL Server Agent proxy</span></span>  
  
1.  <span data-ttu-id="e890c-144">在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。</span><span class="sxs-lookup"><span data-stu-id="e890c-144">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e890c-145">在标准菜单栏上，单击 **“新建查询”** 。</span><span class="sxs-lookup"><span data-stu-id="e890c-145">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e890c-146">将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。</span><span class="sxs-lookup"><span data-stu-id="e890c-146">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- creates credential CatalogApplicationCredential  
    USE msdb ;  
    GO  
    CREATE CREDENTIAL CatalogApplicationCredential WITH IDENTITY = 'REDMOND/TestUser',   
        SECRET = 'G3$1o)lkJ8HNd!';  
    GO  
    -- creates proxy "Catalog application proxy" and assigns the credential 'CatalogApplicationCredential' to it.  
    EXEC dbo.sp_add_proxy  
        @proxy_name = 'Catalog application proxy',  
        @enabled = 1,  
        @description = 'Maintenance tasks on catalog application.',  
        @credential_name = 'CatalogApplicationCredential' ;  
    GO  
    -- grants the proxy "Catalog application proxy" access to the ActiveX Scripting subsystem.  
    EXEC dbo.sp_grant_proxy_to_subsystem  
        @proxy_name = N'Catalog application proxy',  
        @subsystem_id = 2 ;  
    GO  
    ```  
  
 <span data-ttu-id="e890c-147">有关详细信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="e890c-147">For more information, see:</span></span>  
  
-   [<span data-ttu-id="e890c-148">CREATE CREDENTIAL &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e890c-148">CREATE CREDENTIAL &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-credential-transact-sql)  
  
-   [<span data-ttu-id="e890c-149">sp_add_proxy &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="e890c-149">sp_add_proxy &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-proxy-transact-sql)  
  
-   [<span data-ttu-id="e890c-150">sp_grant_proxy_to_subsystem &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="e890c-150">sp_grant_proxy_to_subsystem &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-grant-proxy-to-subsystem-transact-sql)  
  
  
