---
title: 数据收集器的安全性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- data collection [SQL Server]
- security [data collector]
- data collector [SQL Server], security
ms.assetid: e75d6975-641e-440a-a642-cb39a583359a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c89f1658f6ae1b5bd79de96f20222b0b19529df2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578902"
---
# <a name="data-collector-security"></a><span data-ttu-id="8bb1a-102">数据收集器的安全性</span><span class="sxs-lookup"><span data-stu-id="8bb1a-102">Data Collector Security</span></span>
  <span data-ttu-id="8bb1a-103">数据收集器使用由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理实现的基于角色的安全模式。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-103">The data collector uses the role-based security model implemented by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="8bb1a-104">在此模式下，数据库管理员能够在只拥有执行相应任务所需的权限的安全上下文中运行各种数据收集器任务。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-104">This model lets the database administrator run the various data collector tasks in a security context that has only the permissions required to perform that task.</span></span> <span data-ttu-id="8bb1a-105">执行涉及内部表的操作时也采用这种方法，内部表只能通过存储过程或视图进行访问。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-105">This approach is also used for operations involving internal tables, which can only be accessed by using a stored procedure or view.</span></span> <span data-ttu-id="8bb1a-106">不会向内部表授予任何权限。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-106">No permissions are granted to internal tables.</span></span> <span data-ttu-id="8bb1a-107">但是，还要对使用存储过程或视图访问表的用户进行权限检查。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-107">Instead, permissions are checked on the user of the stored procedure or view that is used to access a table.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8bb1a-108">此安全模式的另一个关键点是同心权限。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-108">Another key aspect of this security model is concentric permissions.</span></span> <span data-ttu-id="8bb1a-109">在同心权限下，特权较高的角色继承特权较低的角色对对象（包括警报、运算符、作业、计划和代理）的权限。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-109">Under concentric permissions, more privileged roles inherit the permissions of less privileged roles on objects (including alerts, operators, jobs, schedules, and proxies).</span></span> <span data-ttu-id="8bb1a-110">有关详细信息，请参阅 [SQL Server Agent Fixed Database Roles](../../ssms/agent/sql-server-agent-fixed-database-roles.md)。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-110">For more information, see [SQL Server Agent Fixed Database Roles](../../ssms/agent/sql-server-agent-fixed-database-roles.md).</span></span>  
  
 <span data-ttu-id="8bb1a-111">以下各部分对数据收集安全性作了一般性介绍，还介绍了为使用户能够配置和使用数据收集器并执行与管理数据仓库关联的任务而必须授予他们的角色。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-111">The following sections describe data collection security in general, as well as the roles you must grant to users so they can configure and use the data collector, and carry out tasks associated with the management data warehouse.</span></span>  
  
## <a name="general-security"></a><span data-ttu-id="8bb1a-112">一般安全性</span><span class="sxs-lookup"><span data-stu-id="8bb1a-112">General Security</span></span>  
 <span data-ttu-id="8bb1a-113">数据收集器的安装应依照指定用于 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]的明文标准进行。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-113">The data collector is installed according to the documented standards specified for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
### <a name="network-security"></a><span data-ttu-id="8bb1a-114">网络安全</span><span class="sxs-lookup"><span data-stu-id="8bb1a-114">Network Security</span></span>  
 <span data-ttu-id="8bb1a-115">可以在目标实例、与配置服务器关联的关系实例、正在运行的收集组以及承载管理数据仓库的服务器之间传递敏感信息。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-115">Sensitive information can be passed between target instances, the relational instance associated with the configuration server, the collection sets that are running, and the server that hosts the management data warehouse.</span></span>  
  
 <span data-ttu-id="8bb1a-116">为保护通过网络传输的所有数据，实施了标准安全机制，如针对 [!INCLUDE[tsql](../../includes/tsql-md.md)]的协议加密。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-116">To protect any data that is transferred over a network, the standard security mechanisms are implemented, such as protocol encryption for [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
## <a name="permissions-for-configuring-and-using-the-data-collector"></a><span data-ttu-id="8bb1a-117">用于配置和使用数据收集器的权限</span><span class="sxs-lookup"><span data-stu-id="8bb1a-117">Permissions for Configuring and Using the Data Collector</span></span>  
 <span data-ttu-id="8bb1a-118">用户必须是为数据收集器提供的一个或多个固定数据库角色的成员，具体的角色取决于任务。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-118">Depending on the task, users must be members of one or more of the fixed database roles provided for the data collector.</span></span> <span data-ttu-id="8bb1a-119">按照从最高特权访问到最低特权访问的顺序，角色如下所示：</span><span class="sxs-lookup"><span data-stu-id="8bb1a-119">In order of most-privileged to least-privileged access, the roles are as follows:</span></span>  
  
-   `dc_admin`  
  
-   <span data-ttu-id="8bb1a-120">**dc_operator**</span><span class="sxs-lookup"><span data-stu-id="8bb1a-120">**dc_operator**</span></span>  
  
-   <span data-ttu-id="8bb1a-121">**dc_proxy**</span><span class="sxs-lookup"><span data-stu-id="8bb1a-121">**dc_proxy**</span></span>  
  
 <span data-ttu-id="8bb1a-122">这些角色存储在 msdb 数据库中。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-122">These roles are stored in the msdb database.</span></span> <span data-ttu-id="8bb1a-123">默认情况下，任何用户都不是这些数据库角色的成员。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-123">By default, no user is a member of these database roles.</span></span> <span data-ttu-id="8bb1a-124">这些角色的用户成员资格必须显式授予。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-124">User membership in these roles must be granted explicitly.</span></span>  
  
 <span data-ttu-id="8bb1a-125">作为 `sysadmin` 固定服务器角色成员的用户具有对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理对象和数据收集器视图的完全访问权限。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-125">Users who are members of the `sysadmin` fixed server role have full access to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent objects and data collector views.</span></span> <span data-ttu-id="8bb1a-126">但是，需要将这些用户显式添加到数据收集器角色中。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-126">However, they need to be explicitly added to data collector roles.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8bb1a-127">db_ssisadmin 角色和 dc_admin 角色的成员可以将其特权提升为 sysadmin。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-127">Members of the db_ssisadmin role and the dc_admin role may be able to elevate their privileges to sysadmin.</span></span> <span data-ttu-id="8bb1a-128">因为这些角色可以修改 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包，而 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理的 sysadmin 安全上下文可以执行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 包，所以可以实现特权提升。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-128">This elevation of privilege can occur because these roles can modify [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages and [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages can be executed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using the sysadmin security context of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="8bb1a-129">若要在运行维护计划、数据收集组和其他 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包时防止此权限提升，请将运行包的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业配置为使用具有有限权限的代理帐户，或只将 sysadmin 成员添加到 db_ssisadmin 和 dc_admin 角色。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-129">To guard against this elevation of privilege when running maintenance plans, data collection sets, and other [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages, configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs that run packages to use a proxy account with limited privileges or only add sysadmin members to the db_ssisadmin and dc_admin roles.</span></span>  
  
### <a name="dc_admin-role"></a><span data-ttu-id="8bb1a-130">dc_admin 角色</span><span class="sxs-lookup"><span data-stu-id="8bb1a-130">dc_admin Role</span></span>  
 <span data-ttu-id="8bb1a-131">分配到该角色的用户 `dc_admin` 具有完全权限的管理员访问权限 (创建、读取、更新和删除服务器实例上的数据收集器配置) 。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-131">Users assigned to the `dc_admin` role have full administrator access (Create, Read, Update, and Delete) to the data collector configuration on a server instance.</span></span> <span data-ttu-id="8bb1a-132">此角色的成员可执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="8bb1a-132">Members of this role can perform the following operations:</span></span>  
  
-   <span data-ttu-id="8bb1a-133">设置收集器级别的属性。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-133">Set collector-level properties.</span></span>  
  
-   <span data-ttu-id="8bb1a-134">添加新收集组。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-134">Add new collection sets.</span></span>  
  
-   <span data-ttu-id="8bb1a-135">安装新的收集类型。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-135">Install new collection types.</span></span>  
  
-   <span data-ttu-id="8bb1a-136">执行 **dc_operator** 角色有权执行的所有操作。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-136">Perform all the operations permitted to the **dc_operator** role.</span></span>  
  
 <span data-ttu-id="8bb1a-137">`dc_admin`角色是以下角色的成员：</span><span class="sxs-lookup"><span data-stu-id="8bb1a-137">The `dc_admin` role is a member of the following roles:</span></span>  
  
-   <span data-ttu-id="8bb1a-138">**SQLAgentUserRole**。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-138">**SQLAgentUserRole**.</span></span> <span data-ttu-id="8bb1a-139">创建计划和运行作业时需要此角色。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-139">This role is required to create schedules and run jobs.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8bb1a-140">为数据收集器创建的代理必须授予对的访问权限， `dc_admin` 才能在需要代理的任何作业步骤中创建和使用这些代理。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-140">Proxies created for the data collector must grant access to `dc_admin` to create them and use them in any job steps that require a proxy.</span></span>  
  
-   <span data-ttu-id="8bb1a-141">**dc_operator**。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-141">**dc_operator**.</span></span> <span data-ttu-id="8bb1a-142">的成员 `dc_admin` 继承赋予**dc_operator**的权限。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-142">Members of `dc_admin` inherit the permissions given to **dc_operator**.</span></span>  
  
### <a name="dc_operator-role"></a><span data-ttu-id="8bb1a-143">dc_operator 角色</span><span class="sxs-lookup"><span data-stu-id="8bb1a-143">dc_operator Role</span></span>  
 <span data-ttu-id="8bb1a-144">**dc_operator** 角色的成员拥有读取和更新访问权限。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-144">Members of the **dc_operator** role have Read and Update access.</span></span> <span data-ttu-id="8bb1a-145">此角色支持与运行和配置收集组相关的操作任务。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-145">This role supports operations tasks related to running and configuring collection sets.</span></span> <span data-ttu-id="8bb1a-146">此角色的成员可执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="8bb1a-146">Members of this role can perform the following operations:</span></span>  
  
-   <span data-ttu-id="8bb1a-147">启动或停止收集组。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-147">Start or stop a collection set.</span></span>  
  
-   <span data-ttu-id="8bb1a-148">枚举现有的收集组。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-148">Enumerate existing collection sets.</span></span>  
  
-   <span data-ttu-id="8bb1a-149">查看与收集组关联的详细信息（例如收集项和收集频率）。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-149">View the detailed information (for example, collection items, and collection frequency) associated with a collection set.</span></span>  
  
-   <span data-ttu-id="8bb1a-150">更改现有收集组的上载频率。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-150">Change the upload frequency for existing collection sets.</span></span>  
  
-   <span data-ttu-id="8bb1a-151">更改属于现有收集组的收集项的收集频率。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-151">Change the collection frequency for collection items that are part of an existing collection set.</span></span>  
  
 <span data-ttu-id="8bb1a-152">**dc_operator** 角色是枚举和查看数据收集器包所需的以下角色的成员：</span><span class="sxs-lookup"><span data-stu-id="8bb1a-152">The **dc_operator** role is a member of the following roles that are required for enumerating and viewing data collector packages:</span></span>  
  
-   <span data-ttu-id="8bb1a-153">**db_ssisltduser**</span><span class="sxs-lookup"><span data-stu-id="8bb1a-153">**db_ssisltduser**</span></span>  
  
-   <span data-ttu-id="8bb1a-154">**db_ssisoperator**</span><span class="sxs-lookup"><span data-stu-id="8bb1a-154">**db_ssisoperator**</span></span>  
  
 <span data-ttu-id="8bb1a-155">有关详细信息，请参阅 [Integration Services Roles（SSIS 服务）](../../integration-services/security/integration-services-roles-ssis-service.md)。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-155">For more information, see [Integration Services Roles &#40;SSIS Service&#41;](../../integration-services/security/integration-services-roles-ssis-service.md).</span></span>  
  
### <a name="dc_proxy-role"></a><span data-ttu-id="8bb1a-156">dc_proxy 角色</span><span class="sxs-lookup"><span data-stu-id="8bb1a-156">dc_proxy Role</span></span>  
 <span data-ttu-id="8bb1a-157">**dc_proxy** 角色的成员对数据收集器收集组和收集器级别的属性拥有读取访问权限。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-157">Members of the **dc_proxy** role have Read access to data collector collection sets and collector-level properties.</span></span> <span data-ttu-id="8bb1a-158">此角色的成员还可以执行它们所拥有的作业和创建以现有代理帐户运行的作业步骤。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-158">Members of this role can also execute jobs that they own and create job steps that run as an existing proxy account.</span></span>  
  
 <span data-ttu-id="8bb1a-159">此角色的成员可执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="8bb1a-159">Members of this role can perform the following operations:</span></span>  
  
-   <span data-ttu-id="8bb1a-160">查看收集组配置信息（例如收集项的输入参数以及这些项的收集频率）。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-160">View collection set configuration information (for example, input parameters for collection items, and the collection frequency for these items).</span></span>  
  
-   <span data-ttu-id="8bb1a-161">获取只能由已签名的存储过程访问的内部加密信息（例如用于上载数据的数据仓库连接信息）。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-161">Obtain internal encrypted information that can only be accessed by a signed stored procedure (for example, data warehouse connection information used for data uploads).</span></span>  
  
-   <span data-ttu-id="8bb1a-162">记录收集组的运行时事件。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-162">Log collection-set run-time events.</span></span>  
  
 <span data-ttu-id="8bb1a-163">**dc_proxy** 角色是枚举和查看数据收集器包所需的以下角色的成员：</span><span class="sxs-lookup"><span data-stu-id="8bb1a-163">The **dc_proxy** role is a member of the following roles that are required for enumerating and viewing data collector packages:</span></span>  
  
-   <span data-ttu-id="8bb1a-164">**db_ssisltduser**。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-164">**db_ssisltduser**.</span></span>  
  
-   <span data-ttu-id="8bb1a-165">**db_ssisoperator**</span><span class="sxs-lookup"><span data-stu-id="8bb1a-165">**db_ssisoperator**</span></span>  
  
 <span data-ttu-id="8bb1a-166">有关详细信息，请参阅 [Integration Services Roles（SSIS 服务）](../../integration-services/security/integration-services-roles-ssis-service.md)。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-166">For more information, see [Integration Services Roles &#40;SSIS Service&#41;](../../integration-services/security/integration-services-roles-ssis-service.md).</span></span>  
  
## <a name="permissions-for-configuring-and-using-the-management-data-warehouse"></a><span data-ttu-id="8bb1a-167">用于配置和使用管理数据仓库的权限</span><span class="sxs-lookup"><span data-stu-id="8bb1a-167">Permissions for Configuring and Using the Management Data Warehouse</span></span>  
 <span data-ttu-id="8bb1a-168">用户必须是为访问管理数据仓库而提供的一个或多个固定数据库角色的成员，具体的角色取决于任务。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-168">Depending on the task, users must be members of one or more of the fixed database roles provided for accessing the management data warehouse.</span></span> <span data-ttu-id="8bb1a-169">按照从最高特权访问到最低特权访问的顺序，角色如下所示：</span><span class="sxs-lookup"><span data-stu-id="8bb1a-169">In order of most-privileged to least-privileged access, the roles are as follows:</span></span>  
  
-   <span data-ttu-id="8bb1a-170">**mdw_admin**</span><span class="sxs-lookup"><span data-stu-id="8bb1a-170">**mdw_admin**</span></span>  
  
-   <span data-ttu-id="8bb1a-171">**mdw_writer**</span><span class="sxs-lookup"><span data-stu-id="8bb1a-171">**mdw_writer**</span></span>  
  
-   <span data-ttu-id="8bb1a-172">**mdw_reader**</span><span class="sxs-lookup"><span data-stu-id="8bb1a-172">**mdw_reader**</span></span>  
  
 <span data-ttu-id="8bb1a-173">这些角色存储在 msdb 数据库中。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-173">These roles are stored in the msdb database.</span></span> <span data-ttu-id="8bb1a-174">默认情况下，任何用户都不是这些数据库角色的成员。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-174">By default, no user is a member of these database roles.</span></span> <span data-ttu-id="8bb1a-175">这些角色的用户成员资格必须显式授予。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-175">User membership in these roles must be granted explicitly.</span></span>  
  
 <span data-ttu-id="8bb1a-176">作为 `sysadmin` 固定服务器角色成员的用户拥有对数据收集器视图的完全访问权限。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-176">Users who are members of the `sysadmin` fixed server role have full access to data collector views.</span></span> <span data-ttu-id="8bb1a-177">但是，需要将这些用户显式添加到数据库角色以执行其他操作。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-177">However, they need to be explicitly added to database roles to perform other operations.</span></span>  
  
### <a name="mdw_admin-role"></a><span data-ttu-id="8bb1a-178">mdw_admin 角色</span><span class="sxs-lookup"><span data-stu-id="8bb1a-178">mdw_admin Role</span></span>  
 <span data-ttu-id="8bb1a-179">**mdw_admin** 角色的成员对管理数据仓库拥有读取、写入、更新和删除访问权限。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-179">Members of the **mdw_admin** role have Read, Write, Update, and Delete access to the management data warehouse.</span></span>  
  
 <span data-ttu-id="8bb1a-180">此角色的成员可执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="8bb1a-180">Members of this role can perform the following operations:</span></span>  
  
-   <span data-ttu-id="8bb1a-181">在需要时更改管理数据仓库的架构（例如在安装新的收集类型时添加新表）。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-181">Change the management data warehouse schema when required (for example, adding a new table when a new collection type is installed).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8bb1a-182">如果架构发生更改，用户还必须是角色的成员 `dc_admin` 才能安装新的收集器类型，因为此操作需要在 msdb 中更新数据收集器配置的权限。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-182">Where there is a schema change, the user must also be a member of the `dc_admin` role to install a new collector type, since this action requires permission to update the data collector configuration in msdb.</span></span>  
  
-   <span data-ttu-id="8bb1a-183">对管理数据仓库运行维护作业（例如存档或清除）。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-183">Run maintenance jobs on the management data warehouse, such as archive or cleanup.</span></span>  
  
### <a name="mdw_writer-role"></a><span data-ttu-id="8bb1a-184">mdw_writer 角色</span><span class="sxs-lookup"><span data-stu-id="8bb1a-184">mdw_writer Role</span></span>  
 <span data-ttu-id="8bb1a-185">**mdw_writer** 角色的成员可向管理数据仓库上载和写入数据。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-185">Members of the **mdw_writer** role can upload and write data to the management data warehouse.</span></span> <span data-ttu-id="8bb1a-186">将数据存储到管理数据仓库中的任何数据收集器都必须是此角色的成员。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-186">Any data collector that stores data in the management data warehouse has to be a member of this role.</span></span>  
  
### <a name="mdw_reader-role"></a><span data-ttu-id="8bb1a-187">mdw_reader 角色</span><span class="sxs-lookup"><span data-stu-id="8bb1a-187">mdw_reader Role</span></span>  
 <span data-ttu-id="8bb1a-188">**mdw_reader** 角色的成员对管理数据仓库拥有读取访问权限。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-188">Members of the **mdw_reader** role have Read access to the management data warehouse.</span></span> <span data-ttu-id="8bb1a-189">由于此角色的用途在于通过提供对历史数据的访问来支持故障排除，因此该角色的成员无法查看管理数据仓库架构的其他元素。</span><span class="sxs-lookup"><span data-stu-id="8bb1a-189">Because the purpose of this role is to support troubleshooting by providing access to historical data, members of this role cannot view other elements of the management data warehouse schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bb1a-190">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8bb1a-190">See Also</span></span>  
 [<span data-ttu-id="8bb1a-191">实现 SQL Server 代理安全性</span><span class="sxs-lookup"><span data-stu-id="8bb1a-191">Implement SQL Server Agent Security</span></span>](../../ssms/agent/implement-sql-server-agent-security.md)  
  
  
