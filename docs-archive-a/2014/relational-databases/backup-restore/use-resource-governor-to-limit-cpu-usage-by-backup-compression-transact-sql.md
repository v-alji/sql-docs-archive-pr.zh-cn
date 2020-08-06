---
title: 使用资源调控器限制备份压缩的 CPU 使用率 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backup compression [SQL Server], Resource Governor
- backup compression [SQL Server], CPU usage
- compression [SQL Server], backup compression
- backups [SQL Server], compression
- Resource Governor, backup compression
ms.assetid: 01796551-578d-4425-9b9e-d87210f7ba72
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 19a95cfa5c6780fbdf71ae58bd141aa9aa351efa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693994"
---
# <a name="use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql"></a><span data-ttu-id="808e7-102">使用资源调控器限制备份压缩的 CPU 使用量 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="808e7-102">Use Resource Governor to Limit CPU Usage by Backup Compression (Transact-SQL)</span></span>
  <span data-ttu-id="808e7-103">默认情况下，使用压缩进行备份会显著增加 CPU 的使用，并且压缩进程所消耗的额外 CPU 会对并发操作产生不利影响。</span><span class="sxs-lookup"><span data-stu-id="808e7-103">By default, backing up using compression significantly increases CPU usage, and the additional CPU consumed by the compression process can adversely impact concurrent operations.</span></span> <span data-ttu-id="808e7-104">因此，你可能需要在会话中创建低优先级的压缩备份，当发生 CPU 争用时，此备份的 CPU 使用率受[Resource Governor](../resource-governor/resource-governor.md) 限制。</span><span class="sxs-lookup"><span data-stu-id="808e7-104">Therefore, you might want to create a low-priority compressed backup in a session whose CPU usage is limited by[Resource Governor](../resource-governor/resource-governor.md) when CPU contention occurs.</span></span> <span data-ttu-id="808e7-105">本主题介绍了这样一种方案：通过将特定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用户的会话映射到限制 CPU 使用的资源调控器工作负荷组，来对这些会话进行分类。</span><span class="sxs-lookup"><span data-stu-id="808e7-105">This topic presents a scenario that classifies the sessions of a particular [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user by mapping them to a Resource Governor workload group that limits CPU usage in such cases.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="808e7-106">在具体的资源调控器方案中，会话分类可能基于用户名、应用程序名称或者可以区分连接的其他任何因素。</span><span class="sxs-lookup"><span data-stu-id="808e7-106">In a given Resource Governor scenario, session classification might be based on a user name, an application name, or anything else that can differentiate a connection.</span></span> <span data-ttu-id="808e7-107">有关详细信息，请参阅 [Resource Governor Classifier Function](../resource-governor/resource-governor-classifier-function.md) 和 [Resource Governor Workload Group](../resource-governor/resource-governor-workload-group.md)。</span><span class="sxs-lookup"><span data-stu-id="808e7-107">For more information, see [Resource Governor Classifier Function](../resource-governor/resource-governor-classifier-function.md) and [Resource Governor Workload Group](../resource-governor/resource-governor-workload-group.md).</span></span>  
  
##  <a name="this-topic-contains-the-following-set-of-scenarios-which-are-presented-in-sequence"></a><a name="Top"></a> <span data-ttu-id="808e7-108">本主题包含下面一组方案，将按顺序对它们进行介绍：</span><span class="sxs-lookup"><span data-stu-id="808e7-108">This topic contains the following set of scenarios, which are presented in sequence:</span></span>  
  
1.  [<span data-ttu-id="808e7-109">为低优先级操作设置登录名和用户</span><span class="sxs-lookup"><span data-stu-id="808e7-109">Setting Up a Login and User for Low-Priority Operations</span></span>](#setup_login_and_user)  
  
2.  [<span data-ttu-id="808e7-110">配置资源调控器以限制 CPU 使用</span><span class="sxs-lookup"><span data-stu-id="808e7-110">Configuring Resource Governor to Limit CPU Usage</span></span>](#configure_RG)  
  
3.  [<span data-ttu-id="808e7-111">验证当前会话的分类 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="808e7-111">Verifying the Classification of the Current Session (Transact-SQL)</span></span>](#verifying)  
  
4.  [<span data-ttu-id="808e7-112">使用具有有限 CPU 的会话压缩备份</span><span class="sxs-lookup"><span data-stu-id="808e7-112">Compressing Backups Using a Session with Limited CPU</span></span>](#creating_compressed_backup)  
  
##  <a name="setting-up-a-login-and-user-for-low-priority-operations"></a><a name="setup_login_and_user"></a> <span data-ttu-id="808e7-113">为低优先级操作设置登录名和用户</span><span class="sxs-lookup"><span data-stu-id="808e7-113">Setting Up a Login and User for Low-Priority Operations</span></span>  
 <span data-ttu-id="808e7-114">本主题中的方案需要低优先级的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名和用户。</span><span class="sxs-lookup"><span data-stu-id="808e7-114">The scenario in this topic requires a low-priority [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login and user.</span></span> <span data-ttu-id="808e7-115">将使用用户名对运行于此登录中的会话进行分类，并将它们路由到限制 CPU 使用的资源调控器工作负荷组。</span><span class="sxs-lookup"><span data-stu-id="808e7-115">The user name will be used to classify sessions running in the login and route them to a Resource Governor workload group that limits CPU usage.</span></span>  
  
 <span data-ttu-id="808e7-116">下面的过程介绍了出于此目的设置登录名和用户的步骤，之后给出了 [!INCLUDE[tsql](../../includes/tsql-md.md)] 示例“示例 A：设置登录名和用户 (Transact-SQL)。”</span><span class="sxs-lookup"><span data-stu-id="808e7-116">The following procedure describes the steps for setting up a login and user for this purpose, followed by a [!INCLUDE[tsql](../../includes/tsql-md.md)] example, "Example A: Setting Up a Login and User (Transact-SQL)."</span></span>  
  
### <a name="to-set-up-a-login-and-database-user-for-classifying-sessions"></a><span data-ttu-id="808e7-117">设置用于对会话进行分类的登录名和数据库用户</span><span class="sxs-lookup"><span data-stu-id="808e7-117">To set up a login and database user for classifying sessions</span></span>  
  
1.  <span data-ttu-id="808e7-118">创建一个用于创建低优先级压缩备份的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名。</span><span class="sxs-lookup"><span data-stu-id="808e7-118">Create a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login for creating low-priority compressed backups.</span></span>  
  
     <span data-ttu-id="808e7-119">**创建登录名**</span><span class="sxs-lookup"><span data-stu-id="808e7-119">**To create a login**</span></span>  
  
    -   [<span data-ttu-id="808e7-120">创建登录名</span><span class="sxs-lookup"><span data-stu-id="808e7-120">Create a Login</span></span>](../security/authentication-access/create-a-login.md)  
  
    -   [<span data-ttu-id="808e7-121">CREATE LOGIN &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="808e7-121">CREATE LOGIN &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-login-transact-sql)  
  
2.  <span data-ttu-id="808e7-122">还可以选择对此登录名授予 VIEW SERVER STATE。</span><span class="sxs-lookup"><span data-stu-id="808e7-122">Optionally, grant VIEW SERVER STATE to this login.</span></span>  
  
    -   [<span data-ttu-id="808e7-123">GRANT 系统对象权限 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="808e7-123">GRANT System Object Permissions &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/grant-system-object-permissions-transact-sql)  
  
     <span data-ttu-id="808e7-124">有关详细信息，请参阅 [GRANT 数据库主体权限 (Transact-SQL)](/sql/t-sql/statements/grant-database-principal-permissions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="808e7-124">For more information, see [GRANT Database Principal Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-principal-permissions-transact-sql).</span></span>  
  
3.  <span data-ttu-id="808e7-125">为此登录名创建一个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用户。</span><span class="sxs-lookup"><span data-stu-id="808e7-125">Create a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user for this login.</span></span>  
  
     <span data-ttu-id="808e7-126">**创建用户**</span><span class="sxs-lookup"><span data-stu-id="808e7-126">**To create a user**</span></span>  
  
    -   [<span data-ttu-id="808e7-127">创建数据库用户</span><span class="sxs-lookup"><span data-stu-id="808e7-127">Create a Database User</span></span>](../security/authentication-access/create-a-database-user.md)  
  
    -   [<span data-ttu-id="808e7-128">CREATE USER (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="808e7-128">CREATE USER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-user-transact-sql)  
  
4.  <span data-ttu-id="808e7-129">要使此登录名和用户的会话可以备份给定数据库，应将此用户添加到该数据库的 db_backupoperator 数据库角色。</span><span class="sxs-lookup"><span data-stu-id="808e7-129">To enable sessions of this login and user to back up a given database, add the user to the db_backupoperator database role of that database.</span></span> <span data-ttu-id="808e7-130">对该用户将备份的每个数据库执行此步骤。</span><span class="sxs-lookup"><span data-stu-id="808e7-130">Do this for each database that this user will back up.</span></span> <span data-ttu-id="808e7-131">还可以选择将该用户添加到其他固定数据库角色。</span><span class="sxs-lookup"><span data-stu-id="808e7-131">Optionally, add the user to other fixed database roles.</span></span>  
  
     <span data-ttu-id="808e7-132">**将用户添加到固定数据库角色**</span><span class="sxs-lookup"><span data-stu-id="808e7-132">**To add a user to a fixed database role**</span></span>  
  
    -   [<span data-ttu-id="808e7-133">sp_addrolemember (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="808e7-133">sp_addrolemember &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql)  
  
     <span data-ttu-id="808e7-134">有关详细信息，请参阅 [GRANT 数据库主体权限 (Transact-SQL)](/sql/t-sql/statements/grant-database-principal-permissions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="808e7-134">For more information, see [GRANT Database Principal Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-principal-permissions-transact-sql).</span></span>  
  
### <a name="example-a-setting-up-a-login-and-user-transact-sql"></a><span data-ttu-id="808e7-135">示例 A：设置登录名和用户 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="808e7-135">Example A: Setting Up a Login and User (Transact-SQL)</span></span>  
 <span data-ttu-id="808e7-136">只有当您选择为低优先级备份创建新的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名和用户时，下面的示例才对您有意义。</span><span class="sxs-lookup"><span data-stu-id="808e7-136">The following example is relevant only if you choose to create a new [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login and user for low-priority backups.</span></span> <span data-ttu-id="808e7-137">或者，如果存在适当的登录名和用户，也可以使用现有的登录名和用户。</span><span class="sxs-lookup"><span data-stu-id="808e7-137">Alternatively, you can use an existing login and user, if an appropriate one exists.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="808e7-138">以下示例使用示例登录名和用户名 *domain_name*`\MAX_CPU`。</span><span class="sxs-lookup"><span data-stu-id="808e7-138">The following example uses a sample login and user name, *domain_name*`\MAX_CPU`.</span></span> <span data-ttu-id="808e7-139">将此登录名和用户名替换为您计划在创建低优先级压缩备份时使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名和用户名。</span><span class="sxs-lookup"><span data-stu-id="808e7-139">Replace these with the names of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login and user that you plan to use when creating your low-priority compressed backups.</span></span>  
  
 <span data-ttu-id="808e7-140">此示例为 *domain_name*`\MAX_CPU` Windows 帐户创建一个登录名，然后对该登录名授予 VIEW SERVER STATE 权限。</span><span class="sxs-lookup"><span data-stu-id="808e7-140">This example creates a login for the *domain_name*`\MAX_CPU` Windows account and then grants VIEW SERVER STATE permission to the login.</span></span> <span data-ttu-id="808e7-141">使用此权限，您可以验证登录名的会话的资源调控器分类。</span><span class="sxs-lookup"><span data-stu-id="808e7-141">This permission enables you to verify the Resource Governor classification of sessions of the login.</span></span> <span data-ttu-id="808e7-142">本示例为 *domain_name*`\MAX_CPU` 创建一个用户，并将它添加到 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 示例数据库的 db_backupoperator 固定数据库角色。</span><span class="sxs-lookup"><span data-stu-id="808e7-142">The example then creates a user for *domain_name*`\MAX_CPU` and adds it to the db_backupoperator fixed database role for the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] sample database.</span></span> <span data-ttu-id="808e7-143">此用户名将供资源调控器分类器函数使用。</span><span class="sxs-lookup"><span data-stu-id="808e7-143">This user name will be used by the Resource Governor classifier function.</span></span>  
  
```sql  
-- Create a SQL Server login for low-priority operations  
USE master;  
CREATE LOGIN [domain_name\MAX_CPU] FROM WINDOWS;  
GRANT VIEW SERVER STATE TO [domain_name\MAX_CPU];  
GO  
-- Create a SQL Server user in AdventureWorks2012 for this login  
USE AdventureWorks2012;  
CREATE USER [domain_name\MAX_CPU] FOR LOGIN [domain_name\MAX_CPU];  
EXEC sp_addrolemember 'db_backupoperator', 'domain_name\MAX_CPU';  
GO  
  
```  
  
 <span data-ttu-id="808e7-144">[[返回页首]](#Top)</span><span class="sxs-lookup"><span data-stu-id="808e7-144">[&#91;Top&#93;](#Top)</span></span>  
  
##  <a name="configuring-resource-governor-to-limit-cpu-usage"></a><a name="configure_RG"></a> <span data-ttu-id="808e7-145">配置资源调控器以限制 CPU 使用</span><span class="sxs-lookup"><span data-stu-id="808e7-145">Configuring Resource Governor to Limit CPU Usage</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="808e7-146">确保资源调控器已启用。</span><span class="sxs-lookup"><span data-stu-id="808e7-146">Ensure that Resource Governor is enabled.</span></span> <span data-ttu-id="808e7-147">有关详细信息，请参阅 [启用 Resource Governor](../resource-governor/enable-resource-governor.md)。</span><span class="sxs-lookup"><span data-stu-id="808e7-147">For more information, see [Enable Resource Governor](../resource-governor/enable-resource-governor.md).</span></span>  
  
 <span data-ttu-id="808e7-148">在本资源调控器方案中，配置过程包括以下基本步骤：</span><span class="sxs-lookup"><span data-stu-id="808e7-148">In this Resource Governor scenario, configuration comprises the following basic steps:</span></span>  
  
1.  <span data-ttu-id="808e7-149">创建并配置一个资源调控器资源池，发生 CPU 争用时，该资源池将限制分配给资源池中的请求的最大平均 CPU 带宽。</span><span class="sxs-lookup"><span data-stu-id="808e7-149">Create and configure a Resource Governor resource pool that limits the maximum average CPU bandwidth that will be given to requests in the resource pool when CPU contention occurs.</span></span>  
  
2.  <span data-ttu-id="808e7-150">创建并配置一个使用该池的资源调控器工作负荷组。</span><span class="sxs-lookup"><span data-stu-id="808e7-150">Create and configure a Resource Governor workload group that uses this pool.</span></span>  
  
3.  <span data-ttu-id="808e7-151">创建一个 *分类器函数*，它是一个用户定义函数 (UDF)，其返回值供 Resource Governor 用来对会话进行分类，以便将它们路由到适当的工作负荷组。</span><span class="sxs-lookup"><span data-stu-id="808e7-151">Create a *classifier function*, which is a user-defined function (UDF) whose return values are used by Resource Governor for classifying sessions so that they are routed to the appropriate workload group.</span></span>  
  
4.  <span data-ttu-id="808e7-152">将分类器函数注册到资源调控器。</span><span class="sxs-lookup"><span data-stu-id="808e7-152">Register the classifier function with Resource Governor.</span></span>  
  
5.  <span data-ttu-id="808e7-153">将更改应用于资源调控器内存中配置。</span><span class="sxs-lookup"><span data-stu-id="808e7-153">Apply the changes to the Resource Governor in-memory configuration.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="808e7-154">有关 Resource Governor 资源池、工作负荷组以及分类的信息，请参阅 [Resource Governor](../resource-governor/resource-governor.md)。</span><span class="sxs-lookup"><span data-stu-id="808e7-154">For information about Resource Governor resource pools, workload groups, and classification, see [Resource Governor](../resource-governor/resource-governor.md).</span></span>  
  
 <span data-ttu-id="808e7-155">这些步骤的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句在“配置用于限制 CPU 使用的资源调控器”这一步中介绍，该步骤后面给出了此步骤的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="808e7-155">The [!INCLUDE[tsql](../../includes/tsql-md.md)] statements for these steps are described in the procedure, "To configure Resource Governor for limiting CPU usage," which is followed by a [!INCLUDE[tsql](../../includes/tsql-md.md)] example of the procedure.</span></span>  
  
 <span data-ttu-id="808e7-156">**配置资源调控器 (SQL Server Management Studio)**</span><span class="sxs-lookup"><span data-stu-id="808e7-156">**To configure Resource Governor (SQL Server Management Studio)**</span></span>  
  
-   [<span data-ttu-id="808e7-157">使用模板配置资源调控器</span><span class="sxs-lookup"><span data-stu-id="808e7-157">Configure Resource Governor Using a Template</span></span>](../resource-governor/configure-resource-governor-using-a-template.md)  
  
-   [<span data-ttu-id="808e7-158">创建资源池</span><span class="sxs-lookup"><span data-stu-id="808e7-158">Create a Resource Pool</span></span>](../resource-governor/create-a-resource-pool.md)  
  
-   [<span data-ttu-id="808e7-159">创建工作负荷组</span><span class="sxs-lookup"><span data-stu-id="808e7-159">Create a Workload Group</span></span>](../resource-governor/create-a-workload-group.md)  
  
### <a name="to-configure-resource-governor-for-limiting-cpu-usage-transact-sql"></a><span data-ttu-id="808e7-160">配置用于限制 CPU 使用的资源调控器 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="808e7-160">To configure Resource Governor for limiting CPU usage (Transact-SQL)</span></span>  
  
1.  <span data-ttu-id="808e7-161">发出 [CREATE RESOURCE POOL](/sql/t-sql/statements/create-resource-pool-transact-sql) 语句以创建资源池。</span><span class="sxs-lookup"><span data-stu-id="808e7-161">Issue a [CREATE RESOURCE POOL](/sql/t-sql/statements/create-resource-pool-transact-sql) statement to create a resource pool.</span></span> <span data-ttu-id="808e7-162">此过程的示例使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="808e7-162">The example for this procedure uses the following syntax:</span></span>  
  
     <span data-ttu-id="808e7-163">*CREATE RESOURCE POOL pool_name* WITH ( MAX_CPU_PERCENT = *value* );</span><span class="sxs-lookup"><span data-stu-id="808e7-163">*CREATE RESOURCE POOL pool_name* WITH ( MAX_CPU_PERCENT = *value* );</span></span>  
  
     <span data-ttu-id="808e7-164">*Value* 是 1 到 100 之间的一个整数，它指示最大平均 CPU 带宽的百分比。</span><span class="sxs-lookup"><span data-stu-id="808e7-164">*Value* is an integer from 1 to 100 that indicates the percentage of maximum average CPU bandwidth.</span></span> <span data-ttu-id="808e7-165">实际适合的值取决于具体的环境。</span><span class="sxs-lookup"><span data-stu-id="808e7-165">The appropriate value depends on your environment.</span></span> <span data-ttu-id="808e7-166">为便于说明，本主题中的示例使用 20% (MAX_CPU_PERCENT = 20)。</span><span class="sxs-lookup"><span data-stu-id="808e7-166">For the purpose of illustration, the example in this topic uses 20%  percent (MAX_CPU_PERCENT = 20.)</span></span>  
  
2.  <span data-ttu-id="808e7-167">发出一个 [CREATE WORKLOAD GROUP](/sql/t-sql/statements/create-workload-group-transact-sql) 语句，为你要调控其 CPU 使用的低优先级操作创建一个工作负荷组。</span><span class="sxs-lookup"><span data-stu-id="808e7-167">Issue a [CREATE WORKLOAD GROUP](/sql/t-sql/statements/create-workload-group-transact-sql) statement to create a workload group for low-priority operations whose CPU usage you want to govern.</span></span> <span data-ttu-id="808e7-168">此过程的示例使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="808e7-168">The example for this procedure uses the following syntax:</span></span>  
  
     <span data-ttu-id="808e7-169">CREATE WORKLOAD GROUP *group_name* USING *pool_name*;</span><span class="sxs-lookup"><span data-stu-id="808e7-169">CREATE WORKLOAD GROUP *group_name* USING *pool_name*;</span></span>  
  
3.  <span data-ttu-id="808e7-170">发出一个 [CREATE FUNCTION](/sql/t-sql/statements/create-function-transact-sql) 语句，以创建一个分类器函数，此函数将上一步创建的工作负荷组映射到低优先级登录名的用户。</span><span class="sxs-lookup"><span data-stu-id="808e7-170">Issue a [CREATE FUNCTION](/sql/t-sql/statements/create-function-transact-sql) statement to create a classifier function that maps the workload group created in the preceding step to the user of the low-priority login.</span></span> <span data-ttu-id="808e7-171">此过程的示例使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="808e7-171">The example for this procedure uses the following syntax:</span></span>  
  
     <span data-ttu-id="808e7-172">CREATE FUNCTION [*schema_name*.]*function_name*() RETURNS sysname</span><span class="sxs-lookup"><span data-stu-id="808e7-172">CREATE FUNCTION [*schema_name*.]*function_name*() RETURNS sysname</span></span>  
  
     <span data-ttu-id="808e7-173">WITH SCHEMABINDING</span><span class="sxs-lookup"><span data-stu-id="808e7-173">WITH SCHEMABINDING</span></span>  
  
     <span data-ttu-id="808e7-174">AS</span><span class="sxs-lookup"><span data-stu-id="808e7-174">AS</span></span>  
  
     <span data-ttu-id="808e7-175">BEGIN</span><span class="sxs-lookup"><span data-stu-id="808e7-175">BEGIN</span></span>  
  
     <span data-ttu-id="808e7-176">DECLARE @workload_group_name AS *sysname*</span><span class="sxs-lookup"><span data-stu-id="808e7-176">DECLARE @workload_group_name AS *sysname*</span></span>  
  
     <span data-ttu-id="808e7-177">IF (SUSER_NAME() = '*user_of_low_priority_login*')</span><span class="sxs-lookup"><span data-stu-id="808e7-177">IF (SUSER_NAME() = '*user_of_low_priority_login*')</span></span>  
  
     <span data-ttu-id="808e7-178">SET @workload_group_name = '*workload_group_name*'</span><span class="sxs-lookup"><span data-stu-id="808e7-178">SET @workload_group_name = '*workload_group_name*'</span></span>  
  
     <span data-ttu-id="808e7-179">RETURN @workload_group_name</span><span class="sxs-lookup"><span data-stu-id="808e7-179">RETURN @workload_group_name</span></span>  
  
     <span data-ttu-id="808e7-180">End</span><span class="sxs-lookup"><span data-stu-id="808e7-180">END</span></span>  
  
     <span data-ttu-id="808e7-181">有关该 CREATE FUNCTION 语句的各组成部分的信息，请参阅：</span><span class="sxs-lookup"><span data-stu-id="808e7-181">For information about the components of this CREATE FUNCTION statement, see:</span></span>  
  
    -   [<span data-ttu-id="808e7-182">DECLARE @local_variable (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="808e7-182">DECLARE @local_variable &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/declare-local-variable-transact-sql)  
  
    -   [<span data-ttu-id="808e7-183">SUSER_SNAME (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="808e7-183">SUSER_SNAME &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/suser-sname-transact-sql)  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="808e7-184">SUSER_NAME 仅仅是可用在分类器函数中的几个系统函数中的一个。</span><span class="sxs-lookup"><span data-stu-id="808e7-184">SUSER_NAME is just one of several system functions that can be used in a classifier function.</span></span> <span data-ttu-id="808e7-185">有关详细信息，请参阅 [创建和测试分类器用户定义函数](../resource-governor/create-and-test-a-classifier-user-defined-function.md)。</span><span class="sxs-lookup"><span data-stu-id="808e7-185">For more information, see [Create and Test a Classifier User-Defined Function](../resource-governor/create-and-test-a-classifier-user-defined-function.md).</span></span>  
  
    -   <span data-ttu-id="808e7-186">[SET @local_variable (Transact-SQL)](/sql/t-sql/language-elements/set-local-variable-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="808e7-186">[SET @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/set-local-variable-transact-sql).</span></span>  
  
4.  <span data-ttu-id="808e7-187">发出一个 [ALTER RESOURCE GOVERNOR](/sql/t-sql/statements/alter-resource-governor-transact-sql) 语句，将该分类器函数注册到资源调控器中。</span><span class="sxs-lookup"><span data-stu-id="808e7-187">Issue an [ALTER RESOURCE GOVERNOR](/sql/t-sql/statements/alter-resource-governor-transact-sql) statement to register the classifier function with Resource Governor.</span></span> <span data-ttu-id="808e7-188">此过程的示例使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="808e7-188">The example for this procedure uses the following syntax:</span></span>  
  
     <span data-ttu-id="808e7-189">ALTER RESOURCE GOVERNOR WITH (CLASSIFIER_FUNCTION = *schema_name*.*function_name*);</span><span class="sxs-lookup"><span data-stu-id="808e7-189">ALTER RESOURCE GOVERNOR WITH (CLASSIFIER_FUNCTION = *schema_name*.*function_name*);</span></span>  
  
5.  <span data-ttu-id="808e7-190">再发出一个 ALTER RESOURCE GOVERNOR 语句，将更改应用于资源调控器内存中配置，如下所示：</span><span class="sxs-lookup"><span data-stu-id="808e7-190">Issue a second ALTER RESOURCE GOVERNOR statement to apply the changes to the Resource Governor in-memory configuration, as follows:</span></span>  
  
    ```  
    ALTER RESOURCE GOVERNOR RECONFIGURE;  
    ```  
  
### <a name="example-b-configuring-resource-governor-transact-sql"></a><span data-ttu-id="808e7-191">示例 B：配置资源调控器 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="808e7-191">Example B: Configuring Resource Governor (Transact-SQL)</span></span>  
 <span data-ttu-id="808e7-192">下例在一个事务内执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="808e7-192">The following example performs the following steps within a single transaction:</span></span>  
  
1.  <span data-ttu-id="808e7-193">创建 `pMAX_CPU_PERCENT_20` 资源池。</span><span class="sxs-lookup"><span data-stu-id="808e7-193">Creates the `pMAX_CPU_PERCENT_20` resource pool.</span></span>  
  
2.  <span data-ttu-id="808e7-194">创建 `gMAX_CPU_PERCENT_20` 工作负荷组。</span><span class="sxs-lookup"><span data-stu-id="808e7-194">Creates the `gMAX_CPU_PERCENT_20` workload group.</span></span>  
  
3.  <span data-ttu-id="808e7-195">创建 `rgclassifier_MAX_CPU()` 分类器函数，此函数使用在前一示例中创建的用户名。</span><span class="sxs-lookup"><span data-stu-id="808e7-195">Creates the `rgclassifier_MAX_CPU()` classifier function, which uses the user name created in the preceding example.</span></span>  
  
4.  <span data-ttu-id="808e7-196">将该分类器函数注册到资源调控器。</span><span class="sxs-lookup"><span data-stu-id="808e7-196">Registers the classifier function with Resource Governor.</span></span>  
  
 <span data-ttu-id="808e7-197">提交事务后，本示例将应用 ALTER WORKLOAD GROUP 或 ALTER RESOURCE POOL 语句中请求的配置更改。</span><span class="sxs-lookup"><span data-stu-id="808e7-197">After committing the transaction, the example applies the configuration changes requested in the ALTER WORKLOAD GROUP or ALTER RESOURCE POOL statements.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="808e7-198">以下示例使用示例 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用户的用户名，该用户是在“示例 A：设置登录名和用户 (Transact-SQL)” domain_name`\MAX_CPU` 中创建的  。</span><span class="sxs-lookup"><span data-stu-id="808e7-198">The following example uses the user name of the sample [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user created in "Example A: Setting Up a Login and User (Transact-SQL)," *domain_name*`\MAX_CPU`.</span></span> <span data-ttu-id="808e7-199">将此用户名替换为您计划在创建低优先级压缩备份时使用的登录名的用户名。</span><span class="sxs-lookup"><span data-stu-id="808e7-199">Replace this with the name of the user of the login that you plan to use for creating low-priority compressed backups.</span></span>  
  
```sql  
-- Configure Resource Governor.  
BEGIN TRAN  
USE master;  
-- Create a resource pool that sets the MAX_CPU_PERCENT to 20%.   
CREATE RESOURCE POOL pMAX_CPU_PERCENT_20  
   WITH  
      (MAX_CPU_PERCENT = 20);  
GO  
-- Create a workload group to use this pool.   
CREATE WORKLOAD GROUP gMAX_CPU_PERCENT_20  
USING pMAX_CPU_PERCENT_20;  
GO  
-- Create a classification function.  
-- Note that any request that does not get classified goes into   
-- the 'Default' group.  
CREATE FUNCTION dbo.rgclassifier_MAX_CPU() RETURNS sysname   
WITH SCHEMABINDING  
AS  
BEGIN  
    DECLARE @workload_group_name AS sysname  
      IF (SUSER_NAME() = 'domain_name\MAX_CPU')  
          SET @workload_group_name = 'gMAX_CPU_PERCENT_20'  
    RETURN @workload_group_name  
END;  
GO  
  
-- Register the classifier function with Resource Governor.  
ALTER RESOURCE GOVERNOR WITH (CLASSIFIER_FUNCTION= dbo.rgclassifier_MAX_CPU);  
COMMIT TRAN;  
GO  
-- Start Resource Governor  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
  
```  
  
 <span data-ttu-id="808e7-200">[[返回页首]](#Top)</span><span class="sxs-lookup"><span data-stu-id="808e7-200">[&#91;Top&#93;](#Top)</span></span>  
  
##  <a name="verifying-the-classification-of-the-current-session-transact-sql"></a><a name="verifying"></a> <span data-ttu-id="808e7-201">验证当前会话的分类 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="808e7-201">Verifying the Classification of the Current Session (Transact-SQL)</span></span>  
 <span data-ttu-id="808e7-202">还可以选择使用在分类器函数中指定的用户身份登录，通过在对象资源管理器中发出以下 [SELECT](/sql/t-sql/queries/select-transact-sql) 语句来验证会话分类：</span><span class="sxs-lookup"><span data-stu-id="808e7-202">Optionally, log in as the user that you specified in your classifier function, and verify the session classification by issuing the following [SELECT](/sql/t-sql/queries/select-transact-sql) statement in Object Explorer:</span></span>  
  
```sql  
USE master;  
SELECT sess.session_id, sess.login_name, sess.group_id, grps.name   
FROM sys.dm_exec_sessions AS sess   
JOIN sys.dm_resource_governor_workload_groups AS grps   
    ON sess.group_id = grps.group_id  
WHERE session_id > 50;  
GO  
```  
  
 <span data-ttu-id="808e7-203">在“结果”窗格中，“名称”列应列出你在分类器函数中指定的工作负荷组名称的一个或多个会话  。</span><span class="sxs-lookup"><span data-stu-id="808e7-203">In the results pane, the **name** column should list one or more sessions for the workload-group name that you specified in your classifier function.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="808e7-204">有关此 SELECT 语句调用的动态管理视图的信息，请参阅 [sys.dm_exec_sessions (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql) 和 [sys.dm_resource_governor_workload_groups (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-resource-governor-workload-groups-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="808e7-204">For information about the dynamic management views called by this SELECT statement, see [sys.dm_exec_sessions &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql) and [sys.dm_resource_governor_workload_groups &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-resource-governor-workload-groups-transact-sql).</span></span>  
  
 <span data-ttu-id="808e7-205">[[返回页首]](#Top)</span><span class="sxs-lookup"><span data-stu-id="808e7-205">[&#91;Top&#93;](#Top)</span></span>  
  
##  <a name="compressing-backups-using-a-session-with-limited-cpu"></a><a name="creating_compressed_backup"></a> <span data-ttu-id="808e7-206">使用具有有限 CPU 的会话压缩备份</span><span class="sxs-lookup"><span data-stu-id="808e7-206">Compressing Backups Using a Session with Limited CPU</span></span>  
 <span data-ttu-id="808e7-207">要在限定了最大 CPU 的会话中创建压缩备份，应当以分类器函数中指定的用户身份登录。</span><span class="sxs-lookup"><span data-stu-id="808e7-207">To create a compressed backup in a session with a limited maximum CPU, log in as the user specified in your classifier function.</span></span> <span data-ttu-id="808e7-208">在备份命令中，指定 WITH COMPRESSION ([!INCLUDE[tsql](../../includes/tsql-md.md)]) 或选择 "**压缩备份** (" [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]) "。</span><span class="sxs-lookup"><span data-stu-id="808e7-208">In your backup command, either specify WITH COMPRESSION ([!INCLUDE[tsql](../../includes/tsql-md.md)]) or select **Compress backup** ([!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]).</span></span> <span data-ttu-id="808e7-209">若要创建压缩数据库备份，请参阅[创建完整数据库备份 (SQL Server)](create-a-full-database-backup-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="808e7-209">To create a compressed database backup, see [Create a Full Database Backup &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md).</span></span>  
  
### <a name="example-c-creating-a-compressed-backup-transact-sql"></a><span data-ttu-id="808e7-210">示例 C：创建压缩备份 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="808e7-210">Example C: Creating a Compressed Backup (Transact-SQL)</span></span>  
 <span data-ttu-id="808e7-211">下面的 [BACKUP](/sql/t-sql/statements/backup-transact-sql) 示例在一个采用新格式的备份文件 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 中创建 `Z:\SQLServerBackups\AdvWorksData.bak`数据库的压缩完整备份。</span><span class="sxs-lookup"><span data-stu-id="808e7-211">The following [BACKUP](/sql/t-sql/statements/backup-transact-sql) example creates a compressed full backup of the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database in a newly formatted backup file, `Z:\SQLServerBackups\AdvWorksData.bak`.</span></span>  
  
```sql  
--Run backup statement in the gBackup session.  
BACKUP DATABASE AdventureWorks2012 TO DISK='Z:\SQLServerBackups\AdvWorksData.bak'   
WITH   
   FORMAT,   
   MEDIADESCRIPTION='AdventureWorks2012 Compressed Data Backups'  
   DESCRIPTION='First database backup on AdventureWorks2012 Compressed Data Backups media set'  
   COMPRESSION;  
GO  
```  
  
 <span data-ttu-id="808e7-212">[[返回页首]](#Top)</span><span class="sxs-lookup"><span data-stu-id="808e7-212">[&#91;Top&#93;](#Top)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="808e7-213">另请参阅</span><span class="sxs-lookup"><span data-stu-id="808e7-213">See Also</span></span>  
 <span data-ttu-id="808e7-214">[创建和测试分类器用户定义函数](../resource-governor/create-and-test-a-classifier-user-defined-function.md) </span><span class="sxs-lookup"><span data-stu-id="808e7-214">[Create and Test a Classifier User-Defined Function](../resource-governor/create-and-test-a-classifier-user-defined-function.md) </span></span>  
 [<span data-ttu-id="808e7-215">资源调控器</span><span class="sxs-lookup"><span data-stu-id="808e7-215">Resource Governor</span></span>](../resource-governor/resource-governor.md)  
  
  
