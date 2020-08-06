---
title: Attunity 适用于 Oracle 的更改数据捕获服务的用户角色 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: be0ec384-e03b-4483-96ca-02b289804d6a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e694da0cfd8645fe594b049b6dc2394b55d1bb55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691326"
---
# <a name="user-roles-for-change-data-capture-service-for-oracle-by-attunity"></a><span data-ttu-id="50492-102">使用 Change Data Capture Service for Oracle by Attunity 的角色</span><span class="sxs-lookup"><span data-stu-id="50492-102">User Roles for Change Data Capture Service for Oracle by Attunity</span></span>
  <span data-ttu-id="50492-103">本节介绍 Change Data Capture Service for Oracle by Attunity 的用户角色。</span><span class="sxs-lookup"><span data-stu-id="50492-103">This section describes the user roles for the Change Data Capture Service for Oracle by Attunity.</span></span> <span data-ttu-id="50492-104">介绍的角色包括 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库角色、Windows 角色或 Oracle 数据库角色。</span><span class="sxs-lookup"><span data-stu-id="50492-104">The roles described are [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database roles, Windows roles, or Oracle database roles.</span></span>  
  
## <a name="windows-user-roles"></a><span data-ttu-id="50492-105">Windows 用户角色</span><span class="sxs-lookup"><span data-stu-id="50492-105">Windows User Roles</span></span>  
 <span data-ttu-id="50492-106">下面的内容介绍 Oracle CDC 服务所使用的 Windows 用户角色。</span><span class="sxs-lookup"><span data-stu-id="50492-106">The following describes the Windows user roles used by the Oracle CDC Service.</span></span>  
  
### <a name="computer-administrator-oracle-cdc-service"></a><span data-ttu-id="50492-107">计算机管理员：Oracle CDC 服务</span><span class="sxs-lookup"><span data-stu-id="50492-107">Computer Administrator: Oracle CDC Service</span></span>  
 <span data-ttu-id="50492-108">计算机管理员是负责创建和维护计算机上的 CDC 服务的 Windows 用户。</span><span class="sxs-lookup"><span data-stu-id="50492-108">The computer administrator is a Windows user responsible for creating and maintaining the CDC Service on the computer.</span></span> <span data-ttu-id="50492-109">此用户必须属于本地计算机管理员组。</span><span class="sxs-lookup"><span data-stu-id="50492-109">This user must belong to the group of local machine administrators.</span></span>  
  
 <span data-ttu-id="50492-110">Oracle CDC 服务计算机管理员执行的任务包括：</span><span class="sxs-lookup"><span data-stu-id="50492-110">The tasks performed by the Oracle CDC Service Computer Administrator include:</span></span>  
  
-   <span data-ttu-id="50492-111">安装 Oracle CDC 服务软件</span><span class="sxs-lookup"><span data-stu-id="50492-111">Installing the CDC Service for Oracle software</span></span>  
  
-   <span data-ttu-id="50492-112">创建 Oracle CDC Windows 服务</span><span class="sxs-lookup"><span data-stu-id="50492-112">Creating an Oracle CDC Windows service</span></span>  
  
-   <span data-ttu-id="50492-113">设置与目标 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的 CDC 服务连接（连接字符串和凭据）</span><span class="sxs-lookup"><span data-stu-id="50492-113">Setting up the CDC Service connection to the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance (connection string and credentials)</span></span>  
  
-   <span data-ttu-id="50492-114">确保使用 CDC 服务主密码来保护 Oracle 日志挖掘凭据</span><span class="sxs-lookup"><span data-stu-id="50492-114">Ensuring that the CDC Service Master Password with which Oracle log mining credentials are protected</span></span>  
  
-   <span data-ttu-id="50492-115">删除 CDC 服务 Windows 服务</span><span class="sxs-lookup"><span data-stu-id="50492-115">Deleting a CDC Service Windows service</span></span>  
  
-   <span data-ttu-id="50492-116">卸载 Oracle CDC 服务软件</span><span class="sxs-lookup"><span data-stu-id="50492-116">Uninstalling the CDC Service for Oracle software</span></span>  
  
-   <span data-ttu-id="50492-117">维护 Oracle CDC 服务软件（例如，安装更新）</span><span class="sxs-lookup"><span data-stu-id="50492-117">Maintaining the CDC Service for Oracle software (for example, installing updates)</span></span>  
  
-   <span data-ttu-id="50492-118">启动和停止 CDC 服务 Windows 服务</span><span class="sxs-lookup"><span data-stu-id="50492-118">Starting and stopping a CDC Service Windows service</span></span>  
  
 <span data-ttu-id="50492-119">在使用 Microsoft 故障转移群集之类的高可用性配置时，计算机管理员必须具有其他职责和权限，例如：</span><span class="sxs-lookup"><span data-stu-id="50492-119">When working with high-availability configurations, such as Microsoft failover clusters, the computer administrator must have additional responsibilities and permissions such as:</span></span>  
  
-   <span data-ttu-id="50492-120">所有群集节点上 Oracle CDC 服务软件的安装和维护。</span><span class="sxs-lookup"><span data-stu-id="50492-120">Installation and maintenance of the CDC Service for Oracle software on all cluster nodes.</span></span>  
  
-   <span data-ttu-id="50492-121">为不同群集节点上的 CDC 服务的 Windows 服务定义一般群集服务资源。</span><span class="sxs-lookup"><span data-stu-id="50492-121">Defining generic cluster service resources for the CDC Service' Windows service on the various cluster nodes.</span></span>  
  
-   <span data-ttu-id="50492-122">充当授权为安装了 Oracle CDC 服务的计算机上的管理员的计算机管理员。</span><span class="sxs-lookup"><span data-stu-id="50492-122">Acting as the computer administrator authorized as an administrator on the computer where the CDC Service for Oracle is installed.</span></span> <span data-ttu-id="50492-123">此人士安装 Oracle CDC 服务并且使用 CDC 服务配置控制台为本地计算机上的 Oracle 配置 CDC 服务。</span><span class="sxs-lookup"><span data-stu-id="50492-123">This person installs the CDC Service for Oracle and uses the CDC Service Configuration Console to configure a CDC Service for Oracle on a local computer.</span></span>  
  
### <a name="service-account-oracle-cdc-service"></a><span data-ttu-id="50492-124">服务帐户：Oracle CDC 服务</span><span class="sxs-lookup"><span data-stu-id="50492-124">Service Account: Oracle CDC Service</span></span>  
 <span data-ttu-id="50492-125">这是 Oracle CDC 服务的 Windows 服务帐户，作为运行 Oracle CDC 服务的 Windows 帐户（服务帐户）。</span><span class="sxs-lookup"><span data-stu-id="50492-125">This is Oracle CDC Service Windows Service Account is a Windows account used for running the Oracle CDC Service (the Service Account).</span></span>  
  
 <span data-ttu-id="50492-126">该服务帐户唯一必需的权限是能够使用 Oracle 客户端和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 本机客户端 ODBC 访问接口。</span><span class="sxs-lookup"><span data-stu-id="50492-126">The only required privilege necessary for the service account is to be able to use the Oracle client and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native client ODBC provider.</span></span> <span data-ttu-id="50492-127">此帐户无需访问文件，除非特定的访问接口需要（例如，如果 Oracle 客户端连接字符串引用 **tnsnames.ora** 文件中的 Oracle 数据库实例，则该服务帐户必须可读访问该文件）。</span><span class="sxs-lookup"><span data-stu-id="50492-127">This account does not need to access files unless required by specific providers (for example, if the Oracle client connection string references Oracle database instances in a **tnsnames.ora** file, then that file must be read-accessible to the service account).</span></span>  
  
 <span data-ttu-id="50492-128">在 Windows Vista 或 Windows Server 2008 上创建 Oracle CDC 服务时，默认服务帐户是 NETWORK SERVICE 帐户。</span><span class="sxs-lookup"><span data-stu-id="50492-128">When creating an Oracle CDC Service on Windows Vista or Windows Server 2008, the default service account is the NETWORK SERVICE account.</span></span>  
  
 <span data-ttu-id="50492-129">在 Windows 7、Windows Server 2008 R2 和更高版本中，默认服务帐户是 NT Service\\<service-name>。</span><span class="sxs-lookup"><span data-stu-id="50492-129">On Windows 7, Windows Server 2008 R2 and later, the default service account is NT Service\\<service-name>.</span></span>  
  
 <span data-ttu-id="50492-130">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 运行在其他计算机上或者是群集 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例并且服务需要使用 Windows 身份验证连接到目标 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 时，该服务帐户应该是域帐户。</span><span class="sxs-lookup"><span data-stu-id="50492-130">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] runs on another machine or is a clustered [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance and there the service needs to connect to the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Windows authentication, then the service account should be a domain account.</span></span>  
  
## <a name="sql-server-user-roles"></a><span data-ttu-id="50492-131">SQL Server 用户角色</span><span class="sxs-lookup"><span data-stu-id="50492-131">SQL Server User Roles</span></span>  
 <span data-ttu-id="50492-132">下面的内容介绍 Oracle CDC 服务所使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用户角色。</span><span class="sxs-lookup"><span data-stu-id="50492-132">The following describes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user roles used by the Oracle CDC Service.</span></span>  
  
### <a name="oracle-cdc-service-administrator"></a><span data-ttu-id="50492-133">Oracle CDC 服务管理员</span><span class="sxs-lookup"><span data-stu-id="50492-133">Oracle CDC Service Administrator</span></span>  
 <span data-ttu-id="50492-134">CDC 服务管理员是对目标 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例中的 Oracle CDC 服务项目具有完全控制权限的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用户。</span><span class="sxs-lookup"><span data-stu-id="50492-134">The CDC Service Administrator is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user with full control over the Oracle CDC Service artifacts in the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="50492-135">CDC 服务管理员使用 Oracle CDC 设计器控制台来设计 Oracle CDC 实例。</span><span class="sxs-lookup"><span data-stu-id="50492-135">The CDC Service Administrator uses the Oracle CDC Designer Console to design Oracle CDC Instances.</span></span>  
  
 <span data-ttu-id="50492-136">应向 CDC 服务管理员授予 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 固定服务器角色 **public** 和 **dbcreator**。</span><span class="sxs-lookup"><span data-stu-id="50492-136">The CDC Service Administrator should be granted the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fixed server roles **public** and **dbcreator**.</span></span>  
  
 <span data-ttu-id="50492-137">CDC 服务管理员执行的任务包括：</span><span class="sxs-lookup"><span data-stu-id="50492-137">The tasks performed by the CDC Service Administrator include:</span></span>  
  
-   <span data-ttu-id="50492-138">准备 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例以便承载 Oracle CDC 实例（即 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库）。</span><span class="sxs-lookup"><span data-stu-id="50492-138">Preparing a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance to host Oracle CDC Instances (which are [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases).</span></span> <span data-ttu-id="50492-139">在此任务中，将在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例中创建一个称为 MSXDBCDC 的特殊数据库。</span><span class="sxs-lookup"><span data-stu-id="50492-139">In this task, a special database called MSXDBCDC is created in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
-   <span data-ttu-id="50492-140">创建 Oracle CDC 实例 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="50492-140">Creating an Oracle CDC Instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="50492-141">任务包括为 CDC 启用新创建的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库，这要求 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator (**sysadmin**)。</span><span class="sxs-lookup"><span data-stu-id="50492-141">Task includes enabling the newly created [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database for CDC, which requires a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator (**sysadmin**).</span></span>  
  
-   <span data-ttu-id="50492-142">设计 Oracle CDC 实例。</span><span class="sxs-lookup"><span data-stu-id="50492-142">Designing an Oracle CDC Instance.</span></span> <span data-ttu-id="50492-143">此任务包括提供有关源 Oracle 数据库和捕获表的信息，这要求 Oracle 数据库管理员。</span><span class="sxs-lookup"><span data-stu-id="50492-143">This task includes providing information about the source Oracle database and captured tables, which requires an Oracle database administrator.</span></span>  
  
-   <span data-ttu-id="50492-144">随着时间的推移维护 Oracle CDC 实例，其中包括添加/删除捕获实例和更新配置。</span><span class="sxs-lookup"><span data-stu-id="50492-144">Maintaining the Oracle CDC Instance over time, which includes adding/removing capture instances and updating configuration.</span></span>  
  
-   <span data-ttu-id="50492-145">启用或禁用 Oracle CDC 实例。</span><span class="sxs-lookup"><span data-stu-id="50492-145">Enabling or disabling an Oracle CDC Instance.</span></span>  
  
-   <span data-ttu-id="50492-146">监视 Oracle CDC 实例的状态。</span><span class="sxs-lookup"><span data-stu-id="50492-146">Monitoring the state of an Oracle CDC Instance.</span></span>  
  
-   <span data-ttu-id="50492-147">解决影响 Oracle CDC 实例的问题。</span><span class="sxs-lookup"><span data-stu-id="50492-147">Troubleshooting issues that affect the Oracle CDC Instance.</span></span>  
  
 <span data-ttu-id="50492-148">CDC 服务管理员是（至少最初是）与 Oracle CDC 实例相关联的 **CDC 数据库的** db_owner [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 固定数据库角色。</span><span class="sxs-lookup"><span data-stu-id="50492-148">The CDC Service Administrator is, at least initially, in the **db_owner** fixed database role for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC database associated with the Oracle CDC Instance.</span></span> <span data-ttu-id="50492-149">这使得 CDC 服务管理员有权访问在 CDC 数据库中存储的更改数据。</span><span class="sxs-lookup"><span data-stu-id="50492-149">This gives the CDC Service Administrator access to the change data stored in the CDC database.</span></span> <span data-ttu-id="50492-150">一旦创建，CDC 数据库的 **db_owner** 角色可以分配给其他可执上面所列所有任务（准备 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例并创建另一个 Oracle CDC 实例除外）的用户。</span><span class="sxs-lookup"><span data-stu-id="50492-150">Once created, the **db_owner** role of the CDC database can be assigned to a different user who can carry out all of the tasks listed above except for preparing a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance and creating another Oracle CDC Instance).</span></span>  
  
 <span data-ttu-id="50492-151">CDC 服务管理员无需知道在创建 Oracle CDC Windows 服务时指定的主密码。</span><span class="sxs-lookup"><span data-stu-id="50492-151">The CDC Service Administrator does not need to know the master password specified with the creation of the Oracle CDC Windows service.</span></span>  
  
### <a name="system-administrator"></a><span data-ttu-id="50492-152">系统管理员</span><span class="sxs-lookup"><span data-stu-id="50492-152">System Administrator</span></span>  
 <span data-ttu-id="50492-153">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系统管理员是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用户，并且应被授予与 Oracle CDC 服务关联的 **实例上的固定服务器** sysadmin [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 角色。</span><span class="sxs-lookup"><span data-stu-id="50492-153">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user and should be granted the fixed server **sysadmin** role on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance associated with the Oracle CDC Service(s).</span></span>  
  
 <span data-ttu-id="50492-154">只有一个由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系统管理员执行的 Oracle CDC 特定的任务，该任务是为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC 启用针对 Oracle CDC 实例的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="50492-154">There is only one Oracle CDC specific task that carried out with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] System Administrator and that is to enable the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database for an Oracle CDC Instance for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC.</span></span> <span data-ttu-id="50492-155">此任务是在创建新的 Oracle CDC 实例时使用 Oracle CDC 设计器控制台执行的。</span><span class="sxs-lookup"><span data-stu-id="50492-155">This task is performed using the Oracle CDC Designer console when creating a new Oracle CDC Instance.</span></span>  
  
### <a name="oracle-cdc-service-user"></a><span data-ttu-id="50492-156">Oracle CDC 服务用户</span><span class="sxs-lookup"><span data-stu-id="50492-156">Oracle CDC Service User</span></span>  
 <span data-ttu-id="50492-157">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC 服务帐户是一个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名，Oracle CDC 服务使用该登录名对 MSXDBCDC 以及该服务处理的所有 Oracle CDC 实例（CDC 数据库）执行其工作。</span><span class="sxs-lookup"><span data-stu-id="50492-157">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC Service user is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login which is used by the Oracle CDC Service to perform its work against the MSXDBCDC and all of the Oracle CDC Instances (CDC databases) handled by this service.</span></span>  
  
 <span data-ttu-id="50492-158">应向 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC 服务用户授予以下权限：</span><span class="sxs-lookup"><span data-stu-id="50492-158">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC Service user should be granted the following:</span></span>  
  
-   <span data-ttu-id="50492-159">针对服务器处理的所有 CDC 数据库的固定数据库角色 **db_dlladmin** **db_datareader** **db_datawriter** 的成员。</span><span class="sxs-lookup"><span data-stu-id="50492-159">Member of the fixed database roles **db_dlladmin**, **db_datareader**, and **db_datawriter** for all CDC databases handled by the server.</span></span>  
  
-   <span data-ttu-id="50492-160">MSXDBCDC 数据库的固定数据库角色 **db_datareader** 和 **db_datawriter** 的成员。</span><span class="sxs-lookup"><span data-stu-id="50492-160">Member of the fixed database roles **db_datareader** and **db_datawriter** for the MSXDBCDC database.</span></span>  
  
 <span data-ttu-id="50492-161">因为 Oracle CDC 服务使用单个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名来处理所有 CDC 数据库和 MSXDBCDC 数据库，所以，应该在所有这些数据库中映射该登录名。</span><span class="sxs-lookup"><span data-stu-id="50492-161">Because the Oracle CDC Service uses a single [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to work with all CDC databases and the MSXDBCDC database, this login should be mapped in all of these databases.</span></span>  
  
### <a name="oracle-cdc-change-consumer"></a><span data-ttu-id="50492-162">Oracle CDC 更改使用者</span><span class="sxs-lookup"><span data-stu-id="50492-162">Oracle CDC Change Consumer</span></span>  
 <span data-ttu-id="50492-163">Oracle CDC 更改使用者是一种 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用户，此类用户使用在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC 实例数据库的 CDC 表中存储的更改。</span><span class="sxs-lookup"><span data-stu-id="50492-163">The Oracle CDC Change Consumer is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user that consumes changes stored in the CDC tables in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC Instance database.</span></span>  
  
 <span data-ttu-id="50492-164">此用户确定通过 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC 基础结构生成的 CDC 函数访问各 CDC 表所需的用户角色。</span><span class="sxs-lookup"><span data-stu-id="50492-164">This user determines the user role that is required for accessing each of the CDC tables through the CDC functions generated by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC infrastructure.</span></span> <span data-ttu-id="50492-165">如果在指定捕获实例时未指定任何用户角色，则对更改的访问将限制为 CDC 数据库的 **db_owner** 固定数据库角色的成员。</span><span class="sxs-lookup"><span data-stu-id="50492-165">If no user role is specified when a capture instance is specified, access to the changes is limited to the member of the **db_owner** fixed database role of the CDC database.</span></span>  
  
## <a name="oracle-user-roles"></a><span data-ttu-id="50492-166">Oracle 用户角色</span><span class="sxs-lookup"><span data-stu-id="50492-166">Oracle User Roles</span></span>  
 <span data-ttu-id="50492-167">下面的内容介绍 Oracle CDC 服务所使用的 Oracle 用户角色。</span><span class="sxs-lookup"><span data-stu-id="50492-167">The following describes the Oracle user roles used by the Oracle CDC Service.</span></span>  
  
### <a name="database-administrator-dba"></a><span data-ttu-id="50492-168">数据库管理员 (DBA)</span><span class="sxs-lookup"><span data-stu-id="50492-168">Database Administrator (DBA)</span></span>  
 <span data-ttu-id="50492-169">Oracle 数据库管理员 (DBA) 是 Oracle 数据库用户。</span><span class="sxs-lookup"><span data-stu-id="50492-169">The Oracle database administrator (DBA) is an Oracle database user.</span></span> <span data-ttu-id="50492-170">Oracle DBA 执行的任务包括：</span><span class="sxs-lookup"><span data-stu-id="50492-170">The tasks performed by the Oracle DBA include:</span></span>  
  
-   <span data-ttu-id="50492-171">对源 Oracle 数据库进行设置以便在 ARCHIVELOG 模式下工作。</span><span class="sxs-lookup"><span data-stu-id="50492-171">Setting the source Oracle database to work in ARCHIVELOG mode.</span></span>  
  
-   <span data-ttu-id="50492-172">设置具有所需权限的日志挖掘用户。</span><span class="sxs-lookup"><span data-stu-id="50492-172">Setting up a log mining user with the required permissions.</span></span>  
  
-   <span data-ttu-id="50492-173">为捕获表设置补充日志记录。</span><span class="sxs-lookup"><span data-stu-id="50492-173">Setting supplemental logging for captured tables.</span></span>  
  
-   <span data-ttu-id="50492-174">帮助还原已存档的不再可用的事务日志文件，以便可以对它们进行处理。</span><span class="sxs-lookup"><span data-stu-id="50492-174">Helping to restore archived transaction log files no longer available so they can be processed.</span></span>  
  
 <span data-ttu-id="50492-175">Oracle 数据库管理员可以获取需要运行的 Oracle SQL 脚本，以便可以在运行它们之前进行评估。</span><span class="sxs-lookup"><span data-stu-id="50492-175">The Oracle database administrator can get Oracle SQL scripts that need to run so they can be evaluated before running them.</span></span> <span data-ttu-id="50492-176">Oracle 数据库管理员还可以直接从 Oracle CDC 设计器控制台运行 Oracle SQL 脚本。</span><span class="sxs-lookup"><span data-stu-id="50492-176">The Oracle database administrator can also directly run Oracle SQL scripts from the Oracle CDC Designer console.</span></span>  
  
 <span data-ttu-id="50492-177">如果 Oracle 数据库管理员选择使用 Oracle CDC 设计器控制台，则管理员的凭据不保存，只有使用它们的上下文（对话框）除外。</span><span class="sxs-lookup"><span data-stu-id="50492-177">If the Oracle database administrator chooses to use the Oracle CDC Designer console, administrator's credentials are not kept except for the context (dialog) in which they were used.</span></span>  
  
 <span data-ttu-id="50492-178">Oracle 数据库管理员与 Oracle CDC 服务管理员协调工作来配置 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC 实例。</span><span class="sxs-lookup"><span data-stu-id="50492-178">The Oracle database administrator works in coordination with the Oracle CDC Service administrator on the configuration of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC Instances.</span></span>  
  
### <a name="log-mining-user"></a><span data-ttu-id="50492-179">日志挖掘用户</span><span class="sxs-lookup"><span data-stu-id="50492-179">Log Mining User</span></span>  
 <span data-ttu-id="50492-180">Oracle 日志挖掘用户是一种特殊的 Oracle 数据库用户，此类用户被授予访问和处理 Oracle 事务日志所需的权限。</span><span class="sxs-lookup"><span data-stu-id="50492-180">The Oracle Log Miner user is a special Oracle database user that is granted the required privileges for accessing and processing the Oracle transaction logs.</span></span>  
  
 <span data-ttu-id="50492-181">此用户的凭据使用非对称密钥加密存储于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC 实例数据库中。</span><span class="sxs-lookup"><span data-stu-id="50492-181">The credentials for this user are stored in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC Instance database using asymmetric key encryption.</span></span> <span data-ttu-id="50492-182">它们仅对于 Oracle CDC 服务是可访问的，对于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC 实例数据库所有者则无法访问。</span><span class="sxs-lookup"><span data-stu-id="50492-182">They are accessible only to the Oracle CDC Service but not to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Oracle CDC Instance database owner.</span></span>  
  
 <span data-ttu-id="50492-183">下表描述应向日志挖掘用户授予的所需权限：</span><span class="sxs-lookup"><span data-stu-id="50492-183">The following list describes the required privileges of the log mining user should be granted:</span></span>  
  
-   <span data-ttu-id="50492-184">SELECT on \<any-captured-table></span><span class="sxs-lookup"><span data-stu-id="50492-184">SELECT on \<any-captured-table></span></span>  
  
-   <span data-ttu-id="50492-185">SELECT ANY TRANSACTION</span><span class="sxs-lookup"><span data-stu-id="50492-185">SELECT ANY TRANSACTION</span></span>  
  
-   <span data-ttu-id="50492-186">EXECUTE on DBMS_LOGMNR</span><span class="sxs-lookup"><span data-stu-id="50492-186">EXECUTE on DBMS_LOGMNR</span></span>  
  
-   <span data-ttu-id="50492-187">SELECT on V$LOGMNR_CONTENTS</span><span class="sxs-lookup"><span data-stu-id="50492-187">SELECT on V$LOGMNR_CONTENTS</span></span>  
  
-   <span data-ttu-id="50492-188">SELECT on V$ARCHIVED_LOG</span><span class="sxs-lookup"><span data-stu-id="50492-188">SELECT on V$ARCHIVED_LOG</span></span>  
  
-   <span data-ttu-id="50492-189">SELECT on V$LOG</span><span class="sxs-lookup"><span data-stu-id="50492-189">SELECT on V$LOG</span></span>  
  
-   <span data-ttu-id="50492-190">SELECT on V$LOGFILE</span><span class="sxs-lookup"><span data-stu-id="50492-190">SELECT on V$LOGFILE</span></span>  
  
-   <span data-ttu-id="50492-191">SELECT on V$DATABASE</span><span class="sxs-lookup"><span data-stu-id="50492-191">SELECT on V$DATABASE</span></span>  
  
-   <span data-ttu-id="50492-192">SELECT on V$THREAD</span><span class="sxs-lookup"><span data-stu-id="50492-192">SELECT on V$THREAD</span></span>  
  
-   <span data-ttu-id="50492-193">SELECT on V$PARAMETER</span><span class="sxs-lookup"><span data-stu-id="50492-193">SELECT on V$PARAMETER</span></span>  
  
-   <span data-ttu-id="50492-194">SELECT on DBA_REGISTRY</span><span class="sxs-lookup"><span data-stu-id="50492-194">SELECT on DBA_REGISTRY</span></span>  
  
-   <span data-ttu-id="50492-195">SELECT on ALL_INDEXES</span><span class="sxs-lookup"><span data-stu-id="50492-195">SELECT on ALL_INDEXES</span></span>  
  
-   <span data-ttu-id="50492-196">SELECT on ALL_OBJECTS</span><span class="sxs-lookup"><span data-stu-id="50492-196">SELECT on ALL_OBJECTS</span></span>  
  
-   <span data-ttu-id="50492-197">SELECT on DBA_OBJECTS</span><span class="sxs-lookup"><span data-stu-id="50492-197">SELECT on DBA_OBJECTS</span></span>  
  
-   <span data-ttu-id="50492-198">SELECT on ALL_TABLES</span><span class="sxs-lookup"><span data-stu-id="50492-198">SELECT on ALL_TABLES</span></span>  
  
 <span data-ttu-id="50492-199">如果无法将上述任何权限授予 V$xxx，则应向其授予 V $xxx。</span><span class="sxs-lookup"><span data-stu-id="50492-199">If any of these privileges cannot be granted to a V$xxx, then they should be granted to the V $xxx.</span></span>  
  
### <a name="schema-user"></a><span data-ttu-id="50492-200">架构用户</span><span class="sxs-lookup"><span data-stu-id="50492-200">Schema User</span></span>  
 <span data-ttu-id="50492-201">Oracle 架构用户是对要捕获的 Oracle 表的架构具有读访问权限的 Oracle 用户。</span><span class="sxs-lookup"><span data-stu-id="50492-201">The Oracle Schema User is an Oracle user with read access to the schema of the Oracle tables to be captured.</span></span> <span data-ttu-id="50492-202">在使用 Oracle CDC 设计器控制台检索 Oracle 架构的列表、要捕获的表及其列、索引和密钥时此用户是必需的。</span><span class="sxs-lookup"><span data-stu-id="50492-202">This user is necessary when working with the Oracle CDC Designer console to retrieve the list of Oracle schema, tables to be captured and their columns, indexes and keys.</span></span>  
  
 <span data-ttu-id="50492-203">永远不会存储此用户的凭据。</span><span class="sxs-lookup"><span data-stu-id="50492-203">The credentials for this user are never stored.</span></span> <span data-ttu-id="50492-204">每当需要这些凭据时 CDC 设计器控制台将请求这些凭据，并且将为其余的用户界面会话保存它们。</span><span class="sxs-lookup"><span data-stu-id="50492-204">They are requested by the CDC Designer console each time they are needed and they are kept for the rest of the UI sessions.</span></span>  
  
  
