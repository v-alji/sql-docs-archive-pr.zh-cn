---
title: 实现 SQL Server 代理安全性 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, security
- security [SQL Server Agent], about security
- security [SQL Server Agent]
- security [SQL Server], SQL Server Agent
ms.assetid: d770d35c-c8de-4e00-9a85-7d03f45a0f0d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8b70449ace66d4e33a547eca1c0b19eafabde5a7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689249"
---
# <a name="implement-sql-server-agent-security"></a><span data-ttu-id="5df78-102">实现 SQL Server 代理安全性</span><span class="sxs-lookup"><span data-stu-id="5df78-102">Implement SQL Server Agent Security</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="5df78-103">代理使数据库管理员能够在一个安全上下文中运行每个作业步骤，这个安全上下文只具有执行该作业步骤所需的权限，这是由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理决定的。</span><span class="sxs-lookup"><span data-stu-id="5df78-103">Agent lets the database administrator run each job step in a security context that has only the permissions required to perform that job step, which is determined by a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent proxy.</span></span> <span data-ttu-id="5df78-104">若要为某个特定的作业步骤设置权限，可以创建一个具有所需权限的代理，然后将该代理分配给该作业步骤。</span><span class="sxs-lookup"><span data-stu-id="5df78-104">To set the permissions for a particular job step, you create a proxy that has the required permissions and then assign that proxy to the job step.</span></span> <span data-ttu-id="5df78-105">一个代理可以指定给多个作业步骤。</span><span class="sxs-lookup"><span data-stu-id="5df78-105">A proxy can be specified for more than one job step.</span></span> <span data-ttu-id="5df78-106">对于需要相同权限的作业步骤，可以使用同一个代理。</span><span class="sxs-lookup"><span data-stu-id="5df78-106">For job steps that require the same permissions, you use the same proxy.</span></span>  
  
 <span data-ttu-id="5df78-107">下面的内容将解释必须为用户授予什么样的数据库角色，他们才能使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理创建或执行作业。</span><span class="sxs-lookup"><span data-stu-id="5df78-107">The following section explains what database role you must grant to users so they can create or execute jobs by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span>  
  
## <a name="granting-access-to-sql-server-agent"></a><span data-ttu-id="5df78-108">授予访问 SQL Server 代理的权限</span><span class="sxs-lookup"><span data-stu-id="5df78-108">Granting Access to SQL Server Agent</span></span>  
 <span data-ttu-id="5df78-109">若要使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理，用户必须是下列一个或多个固定数据库角色的成员：</span><span class="sxs-lookup"><span data-stu-id="5df78-109">To use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, users must be a member of one or more of the following fixed database roles:</span></span>  
  
-   <span data-ttu-id="5df78-110">**SQLAgentUserRole**</span><span class="sxs-lookup"><span data-stu-id="5df78-110">**SQLAgentUserRole**</span></span>  
  
-   <span data-ttu-id="5df78-111">**SQLAgentReaderRole**</span><span class="sxs-lookup"><span data-stu-id="5df78-111">**SQLAgentReaderRole**</span></span>  
  
-   <span data-ttu-id="5df78-112">**SQLAgentOperatorRole**</span><span class="sxs-lookup"><span data-stu-id="5df78-112">**SQLAgentOperatorRole**</span></span>  
  
 <span data-ttu-id="5df78-113">这些角色存储在 **msdb** 数据库中。</span><span class="sxs-lookup"><span data-stu-id="5df78-113">These roles are stored in the **msdb** database.</span></span> <span data-ttu-id="5df78-114">默认情况下，任何用户都不是这些数据库角色的成员。</span><span class="sxs-lookup"><span data-stu-id="5df78-114">By default, no user is a member of these database roles.</span></span> <span data-ttu-id="5df78-115">必须显式授予这些角色中的成员身份。</span><span class="sxs-lookup"><span data-stu-id="5df78-115">Membership in these roles must be granted explicitly.</span></span> <span data-ttu-id="5df78-116">作为 **sysadmin** 固定服务器角色成员的用户可以完全访问 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理，不需要成为这些固定数据库角色的成员便可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理。</span><span class="sxs-lookup"><span data-stu-id="5df78-116">Users who are members of the **sysadmin** fixed server role have full access to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, and do not need to be a member of these fixed database roles to use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="5df78-117">如果某个用户既不是这些数据库角色的成员，也不是 **sysadmin** 角色的成员，那么当他们使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 时，不能访问 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]代理节点。</span><span class="sxs-lookup"><span data-stu-id="5df78-117">If a user is not a member of one of these database roles or of the **sysadmin** role, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent node is not available to them when they connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="5df78-118">这些数据库角色的成员可以查看和执行它们所拥有的作业，还可以创建作为现有代理帐户运行的作业步骤。</span><span class="sxs-lookup"><span data-stu-id="5df78-118">Members of these database roles can view and execute jobs that they own, and create job steps that run as an existing proxy account.</span></span> <span data-ttu-id="5df78-119">有关与每个这些角色关联的特定权限的详细信息，请参阅 [SQL Server 代理固定数据库角色](sql-server-agent-fixed-database-roles.md)。</span><span class="sxs-lookup"><span data-stu-id="5df78-119">For more information about the specific permissions that are associated with each of these roles, see [SQL Server Agent Fixed Database Roles](sql-server-agent-fixed-database-roles.md).</span></span>  
  
 <span data-ttu-id="5df78-120">**sysadmin** 固定服务器角色的成员具有创建、修改和删除代理帐户的权限。</span><span class="sxs-lookup"><span data-stu-id="5df78-120">Members of the **sysadmin** fixed server role have permission to create, modify, and delete proxy accounts.</span></span> <span data-ttu-id="5df78-121">**sysadmin** 角色的成员可以创建作业步骤，无需指定代理，但需作为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务帐户运行，该帐户是用于启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理的帐户。</span><span class="sxs-lookup"><span data-stu-id="5df78-121">Members of the **sysadmin** role have permission to create job steps that do not specify a proxy, but instead run as the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account, which is the account that is used to start [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span>  
  
## <a name="guidelines"></a><span data-ttu-id="5df78-122">准则</span><span class="sxs-lookup"><span data-stu-id="5df78-122">Guidelines</span></span>  
 <span data-ttu-id="5df78-123">遵循下列指导原则可以提高 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理实现的安全性：</span><span class="sxs-lookup"><span data-stu-id="5df78-123">Follow these guidelines to improve the security of your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent implementation:</span></span>  
  
-   <span data-ttu-id="5df78-124">专门为代理创建专用的用户帐户，并且只使用这些代理用户帐户来运行作业步骤。</span><span class="sxs-lookup"><span data-stu-id="5df78-124">Create dedicated user accounts specifically for proxies, and only use these proxy user accounts for running job steps.</span></span>  
  
-   <span data-ttu-id="5df78-125">只为代理用户帐户授予必需的权限。</span><span class="sxs-lookup"><span data-stu-id="5df78-125">Only grant the necessary permissions to proxy user accounts.</span></span> <span data-ttu-id="5df78-126">只授予运行分配给给定代理帐户的作业步骤实际所需的那些权限。</span><span class="sxs-lookup"><span data-stu-id="5df78-126">Grant only those permissions actually required to run the job steps that are assigned to a given proxy account.</span></span>  
  
-   <span data-ttu-id="5df78-127">不要使用作为 Windows [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Administrators **组成员的 Microsoft Windows 帐户运行** 代理服务。</span><span class="sxs-lookup"><span data-stu-id="5df78-127">Do not run the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service under a Microsoft Windows account that is a member of the Windows **Administrators** group.</span></span>  
  
-   <span data-ttu-id="5df78-128">代理仅具有与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 凭据存储区相同的安全性。</span><span class="sxs-lookup"><span data-stu-id="5df78-128">Proxies are only as secure as the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] credential store.</span></span>  
  
-   <span data-ttu-id="5df78-129">如果用户写入操作可对 NT 事件日志进行写入，则用户可通过 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理引发警报。</span><span class="sxs-lookup"><span data-stu-id="5df78-129">If user write operations can write to the NT Event log, they can raise alerts via [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span>  
  
-   <span data-ttu-id="5df78-130">请不要将 NT 管理帐户指定为服务帐户或代理帐户。</span><span class="sxs-lookup"><span data-stu-id="5df78-130">Do not specify the NT Admin account as a service account or proxy account.</span></span>  
  
-   <span data-ttu-id="5df78-131">请注意，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理有权互相访问资产。</span><span class="sxs-lookup"><span data-stu-id="5df78-131">Note that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent have access to each other's assets.</span></span> <span data-ttu-id="5df78-132">这两项服务共享一个进程空间，并且 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务的 sysadmin。</span><span class="sxs-lookup"><span data-stu-id="5df78-132">The two services share a single process space and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent is a sysadmin on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span>  
  
-   <span data-ttu-id="5df78-133">当 TSX 使用 MSX 进行登记时，MSX sysadmins 将获得对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的 TSX 实例的完全控制权。</span><span class="sxs-lookup"><span data-stu-id="5df78-133">When a TSX enlists with an MSX, the MSX sysadmins gets total control over the TSX instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="5df78-134">ACE 是一个扩展插件，不能调用自身。</span><span class="sxs-lookup"><span data-stu-id="5df78-134">ACE is an extension and cannot invoke itself.</span></span> <span data-ttu-id="5df78-135">ACE 由 Chainer ScenarioEngine.exe（也称为 Microsoft.SqlServer.Chainer.Setup.exe）调用，也可由其他主机进程调用。</span><span class="sxs-lookup"><span data-stu-id="5df78-135">ACE is invoked by Chainer ScenarioEngine.exe - also known as Microsoft.SqlServer.Chainer.Setup.exe - or it can be invoked by another host process.</span></span>  
  
-   <span data-ttu-id="5df78-136">ACE 取决于 SSDP 拥有的以下配置 DLL，因为这些 DLL 的 API 是由 ACE 调用的：</span><span class="sxs-lookup"><span data-stu-id="5df78-136">ACE depends on the following configuration DLL's owned by SSDP, because those API's of DLL's are called by ACE:</span></span>  
  
    -   <span data-ttu-id="5df78-137">**SCO** - Microsoft.SqlServer.Configuration.Sco.dll，包括针对虚拟帐户的新 SCO 验证</span><span class="sxs-lookup"><span data-stu-id="5df78-137">**SCO** - Microsoft.SqlServer.Configuration.Sco.dll, including new SCO validations for virtual accounts</span></span>  
  
    -   <span data-ttu-id="5df78-138">**Cluster** - Microsoft.SqlServer.Configuration.Cluster.dll</span><span class="sxs-lookup"><span data-stu-id="5df78-138">**Cluster** - Microsoft.SqlServer.Configuration.Cluster.dll</span></span>  
  
    -   <span data-ttu-id="5df78-139">**SFC** - Microsoft.SqlServer.Configuration.SqlConfigBase.dll</span><span class="sxs-lookup"><span data-stu-id="5df78-139">**SFC** - Microsoft.SqlServer.Configuration.SqlConfigBase.dll</span></span>  
  
    -   <span data-ttu-id="5df78-140">**Extension** - Microsoft.SqlServer.Configuration.ConfigExtension.dll</span><span class="sxs-lookup"><span data-stu-id="5df78-140">**Extension** - Microsoft.SqlServer.Configuration.ConfigExtension.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5df78-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5df78-141">See Also</span></span>  
 <span data-ttu-id="5df78-142">[预定义角色](../../reporting-services/security/role-definitions-predefined-roles.md) </span><span class="sxs-lookup"><span data-stu-id="5df78-142">[Predefined Roles](../../reporting-services/security/role-definitions-predefined-roles.md) </span></span>  
 <span data-ttu-id="5df78-143">[sp_addrolemember &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5df78-143">[sp_addrolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql) </span></span>  
 <span data-ttu-id="5df78-144">[sp_droprolemember &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-droprolemember-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5df78-144">[sp_droprolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-droprolemember-transact-sql) </span></span>  
 [<span data-ttu-id="5df78-145">SQL Server 数据库引擎和 Azure SQL Database 的安全中心</span><span class="sxs-lookup"><span data-stu-id="5df78-145">Security Center for SQL Server Database Engine and Azure SQL Database</span></span>](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
  
