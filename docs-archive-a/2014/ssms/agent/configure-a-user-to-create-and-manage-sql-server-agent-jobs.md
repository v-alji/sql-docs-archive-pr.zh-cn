---
title: 配置帐户以创建和管理 SQL Server 代理作业 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, user configuration
- jobs [SQL Server Agent], user configuration
- SQLAgentUserRole database role
- proxy accounts [SQL Server Agent]
ms.assetid: 67897e3e-b7d0-43dd-a2e2-2840ec4dd1ef
author: stevestein
ms.author: sstein
ms.openlocfilehash: 83313389b3b872004fb23b0babdad19cfb5b8e7d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591072"
---
# <a name="configure-a-user-to-create-and-manage-sql-server-agent-jobs"></a><span data-ttu-id="e9261-102">Configure a User to Create and Manage SQL Server Agent Jobs</span><span class="sxs-lookup"><span data-stu-id="e9261-102">Configure a User to Create and Manage SQL Server Agent Jobs</span></span>
  <span data-ttu-id="e9261-103">本主题介绍如何配置用户以创建或执行 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业。</span><span class="sxs-lookup"><span data-stu-id="e9261-103">This topic describes how to configure a user to create or execute [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs.</span></span>  
  
-   <span data-ttu-id="e9261-104">**开始之前：** [安全性](#Security)</span><span class="sxs-lookup"><span data-stu-id="e9261-104">**Before you begin:**  [Security](#Security)</span></span>  
  
-   <span data-ttu-id="e9261-105">**若要配置用户以创建和管理 SQL Server 代理作业，请使用：**  [SQL Server Management Studio](#SSMS)</span><span class="sxs-lookup"><span data-stu-id="e9261-105">**To configure a user to create and manage SQL Server Agent jobs, using:**  [SQL Server Management Studio](#SSMS)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e9261-106">开始之前</span><span class="sxs-lookup"><span data-stu-id="e9261-106">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e9261-107">Security</span><span class="sxs-lookup"><span data-stu-id="e9261-107">Security</span></span>  
 <span data-ttu-id="e9261-108">若要配置用户以创建或执行 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业，必须先将现有 SQL Server 登录名或 msdb 角色添加到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb 数据库中的以下代理固定数据库角色之一： SQLAgentUserRole、SQLAgentReaderRole 或 SQLAgentOperatorRole。</span><span class="sxs-lookup"><span data-stu-id="e9261-108">To configure a user to create or execute [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs, you must first add an existing SQL Server login or msdb role to one of the following [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles in the msdb database: SQLAgentUserRole, SQLAgentReaderRole, or SQLAgentOperatorRole.</span></span>  
  
 <span data-ttu-id="e9261-109">默认情况下，这些数据库角色的成员可以创建各自的作业步骤，这些作业步骤不执行其他作业步骤。</span><span class="sxs-lookup"><span data-stu-id="e9261-109">By default, members of these database roles can create their own job steps that run as themselves.</span></span> <span data-ttu-id="e9261-110">如果这些非管理用户要运行那些执行其他作业步骤类型（例如， [!INCLUDE[ssIS](../../includes/ssis-md.md)] 包）的作业，它们需要对代理帐户具有访问权限。</span><span class="sxs-lookup"><span data-stu-id="e9261-110">If these non-administrative users want to run jobs that execute other job step types (for example, [!INCLUDE[ssIS](../../includes/ssis-md.md)] packages), they will need to have access to a proxy account.</span></span> <span data-ttu-id="e9261-111">sysadmin 固定服务器角色的所有成员都有创建、修改和删除代理帐户的权限。</span><span class="sxs-lookup"><span data-stu-id="e9261-111">All members of the sysadmin fixed server role have permission to create, modify, and delete proxy accounts.</span></span> <span data-ttu-id="e9261-112">有关与这些 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理固定数据库角色相关的权限的详细信息，请参阅 [SQL Server 代理固定数据库角色](sql-server-agent-fixed-database-roles.md)。</span><span class="sxs-lookup"><span data-stu-id="e9261-112">For more information about the permissions that are associated with these [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles, see [SQL Server Agent Fixed Database Roles](sql-server-agent-fixed-database-roles.md).</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e9261-113">权限</span><span class="sxs-lookup"><span data-stu-id="e9261-113">Permissions</span></span>  
 <span data-ttu-id="e9261-114">有关详细信息，请参阅[实现 SQL Server 代理安全性](implement-sql-server-agent-security.md)。</span><span class="sxs-lookup"><span data-stu-id="e9261-114">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="e9261-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e9261-115">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="e9261-116">**将 SQL 登录帐户或 msdb 角色添加到 SQL Server 代理固定数据库角色**</span><span class="sxs-lookup"><span data-stu-id="e9261-116">**To add a SQL login or msdb role to a SQL Server Agent fixed database role**</span></span>  
  
1.  <span data-ttu-id="e9261-117">在 **对象资源管理器**中，展开某个服务器。</span><span class="sxs-lookup"><span data-stu-id="e9261-117">In **Object Explorer**, expand a server.</span></span>  
  
2.  <span data-ttu-id="e9261-118">展开 **“安全性”**，然后展开 **“登录名”**。</span><span class="sxs-lookup"><span data-stu-id="e9261-118">Expand **Security**, and then expand **Logins**.</span></span>  
  
3.  <span data-ttu-id="e9261-119">右键单击要添加到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理固定数据库角色的登录帐户，然后选择“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e9261-119">Right-click the login you wish to add to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database role, and select **Properties**.</span></span>  
  
4.  <span data-ttu-id="e9261-120">在 "**登录属性**" 对话框的 "**用户映射**" 页上，选择包含的行 `msdb` 。</span><span class="sxs-lookup"><span data-stu-id="e9261-120">On the **User Mapping** page of the **Login Properties** dialog box, select the row containing `msdb`.</span></span>  
  
5.  <span data-ttu-id="e9261-121">在 **“数据库角色成员身份: msdb”** 下，选中适当的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理固定数据库角色。</span><span class="sxs-lookup"><span data-stu-id="e9261-121">Under **Database role membership for: msdb**, check the appropriate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database role.</span></span>  
  
 <span data-ttu-id="e9261-122">**配置代理帐户以创建和管理 SQL Server 代理作业步骤**</span><span class="sxs-lookup"><span data-stu-id="e9261-122">**To configure a proxy account to create and manage SQL Server Agent job steps**</span></span>  
  
1.  <span data-ttu-id="e9261-123">在 **对象资源管理器**中，展开某个服务器。</span><span class="sxs-lookup"><span data-stu-id="e9261-123">In **Object Explorer**, expand a server.</span></span>  
  
2.  <span data-ttu-id="e9261-124">展开 **“SQL Server 代理”**。</span><span class="sxs-lookup"><span data-stu-id="e9261-124">Expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="e9261-125">右键单击“代理”\*\*\*\*，再选择“新建代理”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e9261-125">Right-click **Proxies** and select **New Proxy**.</span></span>  
  
4.  <span data-ttu-id="e9261-126">在 **“新建代理帐户”** 对话框的 **“常规”** 页上，指定新代理的代理名称、凭据名称和说明。</span><span class="sxs-lookup"><span data-stu-id="e9261-126">On the **General** page of the **New Proxy Account** dialog, specify the proxy name, credential name, and description for the new proxy.</span></span> <span data-ttu-id="e9261-127">请注意，在创建 SQL Server 代理的代理帐户之前，必须先创建一个凭据。</span><span class="sxs-lookup"><span data-stu-id="e9261-127">Note that you must create a credential first before creating a SQL Server Agent proxy.</span></span> <span data-ttu-id="e9261-128">有关创建凭据的详细信息，请参阅[create a credential](../../relational-databases/security/authentication-access/create-a-credential.md)和[Create credential &#40;transact-sql&#41;](/sql/t-sql/statements/create-credential-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="e9261-128">For more information about creating a credential, see [Create a Credential](../../relational-databases/security/authentication-access/create-a-credential.md) and [CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql).</span></span>  
  
5.  <span data-ttu-id="e9261-129">检查此代理的相应子系统。</span><span class="sxs-lookup"><span data-stu-id="e9261-129">Check the appropriate subsystems for this proxy.</span></span>  
  
6.  <span data-ttu-id="e9261-130">在 **“主体”** 页上，添加或删除登录名或角色，以授予或删除对代理帐户的访问权限。</span><span class="sxs-lookup"><span data-stu-id="e9261-130">On the **Principals** page, add or remove logins or roles to grant or remove access to the proxy account.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9261-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e9261-131">See Also</span></span>  
 [<span data-ttu-id="e9261-132">实现 SQL Server 代理安全性</span><span class="sxs-lookup"><span data-stu-id="e9261-132">Implement SQL Server Agent Security</span></span>](implement-sql-server-agent-security.md)  
  
  
