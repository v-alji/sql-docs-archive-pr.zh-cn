---
title: 创建可用性组 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], creating
ms.assetid: 8b0a6301-8b79-4415-b608-b40876f30066
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 57a494af168a8f5572bafe93f8fb47b22a954a19
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694564"
---
# <a name="create-an-availability-group-transact-sql"></a><span data-ttu-id="3ab9d-102">创建可用性组 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="3ab9d-102">Create an Availability Group (Transact-SQL)</span></span>
  <span data-ttu-id="3ab9d-103">本主题介绍如何使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 在启用了 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 功能的 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 实例上创建和配置可用性组。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-103">This topic describes how to use [!INCLUDE[tsql](../../../includes/tsql-md.md)] to create and configure an availability group on instances of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] on which the [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] feature is enabled.</span></span> <span data-ttu-id="3ab9d-104">“可用性组”  定义一组用户数据库，这些用户数据库将以支持故障转移的单个单元和一组故障转移伙伴（称作“可用性副本” ）的形式进行故障转移。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-104">An *availability group* defines a set of user databases that will fail over as a single unit and a set of failover partners, known as *availability replicas*, that support failover.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3ab9d-105">有关可用性组的简介，请参阅 [AlwaysOn 可用性组概述 (SQL Server)](overview-of-always-on-availability-groups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-105">For an introduction to availability groups, see [Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).</span></span>  

> [!NOTE]  
>  <span data-ttu-id="3ab9d-106">除了使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)]之外，您还可以使用“创建可用性组”向导或 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-106">As an alternative to using [!INCLUDE[tsql](../../../includes/tsql-md.md)], you can use the Create Availability Group wizard or [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell cmdlets.</span></span> <span data-ttu-id="3ab9d-107">有关详细信息，请参阅 [使用可用性组向导 (SQL Server Management Studio)](use-the-availability-group-wizard-sql-server-management-studio.md)、 [使用“新建可用性组”对话框 (SQL Server Management Studio)](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)或 [创建可用性组 (SQL Server PowerShell)](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-107">For more information, see [Use the Availability Group Wizard &#40;SQL Server Management Studio&#41;](use-the-availability-group-wizard-sql-server-management-studio.md), [Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md), or [Create an Availability Group &#40;SQL Server PowerShell&#41;](../../../powershell/sql-server-powershell.md).</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="3ab9d-108">开始之前</span><span class="sxs-lookup"><span data-stu-id="3ab9d-108">Before You Begin</span></span>  
 <span data-ttu-id="3ab9d-109">我们强烈建议您首先阅读此部分，再尝试创建您的第一个可用性组。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-109">We strongly recommend that you read this section before attempting to create your first availability group.</span></span>  
  
###  <a name="prerequisites-restrictions-and-recommendations"></a><a name="PrerequisitesRestrictions"></a><span data-ttu-id="3ab9d-110">先决条件、限制和建议</span><span class="sxs-lookup"><span data-stu-id="3ab9d-110">Prerequisites, Restrictions, and Recommendations</span></span>  
  
-   <span data-ttu-id="3ab9d-111">创建可用性组之前，请先验证承载可用性副本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例位于同一 WSFC 故障转移群集内的不同 Windows Server 故障转移群集 (WSFC) 节点上。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-111">Before creating an availability group, verify that the instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that host availability replicas reside on different Windows Server Failover Clustering (WSFC) node within the same WSFC failover cluster.</span></span> <span data-ttu-id="3ab9d-112">此外，还请验证每个服务器实例是否都满足所有其他 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 先决条件。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-112">Also, verify that each of the server instance meets all other [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] prerequisites.</span></span> <span data-ttu-id="3ab9d-113">有关详细信息，我们强烈建议你参阅[针对 AlwaysOn 可用性组的先决条件、限制和建议 (SQL Server)](prereqs-restrictions-recommendations-always-on-availability.md)。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-113">For more information, we strongly recommend that you read [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="3ab9d-114">Security</span><span class="sxs-lookup"><span data-stu-id="3ab9d-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="3ab9d-115">权限</span><span class="sxs-lookup"><span data-stu-id="3ab9d-115">Permissions</span></span>  
 <span data-ttu-id="3ab9d-116">需要 **sysadmin** 固定服务器角色的成员资格，以及 CREATE AVAILABILITY GROUP 服务器权限、ALTER ANY AVAILABILITY GROUP 权限或 CONTROL SERVER 权限。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-116">Requires membership in the **sysadmin** fixed server role and either CREATE AVAILABILITY GROUP server permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
###  <a name="summary-of-tasks-and-corresponding-transact-sql-statements"></a><a name="SummaryTsqlStatements"></a><span data-ttu-id="3ab9d-117">任务和相应 Transact-sql 语句摘要</span><span class="sxs-lookup"><span data-stu-id="3ab9d-117">Summary of Tasks and Corresponding Transact-SQL Statements</span></span>  
 <span data-ttu-id="3ab9d-118">下表列出了涉及创建和配置可用性组的基本任务，并且指出了要用于这些任务的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-118">The following table lists the basic tasks involved in creating and configuring an availability group and indicates which [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements to use for these tasks.</span></span> <span data-ttu-id="3ab9d-119">必须按照任务在表中出现的顺序执行 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 任务。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-119">The [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] tasks must be performed in the sequence in which they are presented in the table.</span></span>  
  
|<span data-ttu-id="3ab9d-120">任务</span><span class="sxs-lookup"><span data-stu-id="3ab9d-120">Task</span></span>|<span data-ttu-id="3ab9d-121">Transact-SQL 语句</span><span class="sxs-lookup"><span data-stu-id="3ab9d-121">Transact-SQL Statement(s)</span></span>|<span data-ttu-id="3ab9d-122">执行任务的位置**<sup>\*</sup>**</span><span class="sxs-lookup"><span data-stu-id="3ab9d-122">Where to Perform Task**<sup>\*</sup>**</span></span>|  
|----------|----------------------------------|-------------------------------------------|  
|<span data-ttu-id="3ab9d-123">创建数据库镜像端点（每个 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例一次）</span><span class="sxs-lookup"><span data-stu-id="3ab9d-123">Create database mirroring endpoint (once per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance)</span></span>|<span data-ttu-id="3ab9d-124">[创建终结点终结点](/sql/t-sql/statements/create-endpoint-transact-sql) *...* 对于 DATABASE_MIRRORING</span><span class="sxs-lookup"><span data-stu-id="3ab9d-124">[CREATE ENDPOINT](/sql/t-sql/statements/create-endpoint-transact-sql) *endpointName* ... FOR DATABASE_MIRRORING</span></span>|<span data-ttu-id="3ab9d-125">在缺少数据库镜像端点的每个服务器实例上执行。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-125">Execute on each server instance that lacks database mirroring endpoint.</span></span>|  
|<span data-ttu-id="3ab9d-126">创建可用性组</span><span class="sxs-lookup"><span data-stu-id="3ab9d-126">Create availability group</span></span>|[<span data-ttu-id="3ab9d-127">CREATE AVAILABILITY GROUP</span><span class="sxs-lookup"><span data-stu-id="3ab9d-127">CREATE AVAILABILITY GROUP</span></span>](/sql/t-sql/statements/create-availability-group-transact-sql)|<span data-ttu-id="3ab9d-128">在要承载初始主副本的服务器实例上执行。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-128">Execute on the server instance that is to host the initial primary replica.</span></span>|  
|<span data-ttu-id="3ab9d-129">将辅助副本联接到可用性组</span><span class="sxs-lookup"><span data-stu-id="3ab9d-129">Join secondary replica to availability group</span></span>|<span data-ttu-id="3ab9d-130">[ALTER AVAILABILITY GROUP](join-a-secondary-replica-to-an-availability-group-sql-server.md) *group_name* JOIN</span><span class="sxs-lookup"><span data-stu-id="3ab9d-130">[ALTER AVAILABILITY GROUP](join-a-secondary-replica-to-an-availability-group-sql-server.md) *group_name* JOIN</span></span>|<span data-ttu-id="3ab9d-131">在承载辅助副本的各服务器实例上执行。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-131">Execute on each server instance that hosts a secondary replica.</span></span>|  
|<span data-ttu-id="3ab9d-132">准备辅助数据库</span><span class="sxs-lookup"><span data-stu-id="3ab9d-132">Prepare the secondary database</span></span>|<span data-ttu-id="3ab9d-133">[备份](/sql/t-sql/statements/backup-transact-sql)和[还原](/sql/t-sql/statements/restore-statements-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-133">[BACKUP](/sql/t-sql/statements/backup-transact-sql) and [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>|<span data-ttu-id="3ab9d-134">在承载主副本的服务器实例上创建备份。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-134">Create backups on the server instance that hosts the primary replica.</span></span><br /><br /> <span data-ttu-id="3ab9d-135">使用 RESTORE WITH NORECOVERY 在承载辅助副本的各服务器实例上还原备份。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-135">Restore backups on each server instance that hosts a secondary replica, using RESTORE WITH NORECOVERY.</span></span>|  
|<span data-ttu-id="3ab9d-136">通过将各辅助数据库联接到可用性组，开始数据同步</span><span class="sxs-lookup"><span data-stu-id="3ab9d-136">Start data synchronization by joining each secondary database to availability group</span></span>|<span data-ttu-id="3ab9d-137">[ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) *database_name* SET HADR AVAILABILITY GROUP = *group_name*</span><span class="sxs-lookup"><span data-stu-id="3ab9d-137">[ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) *database_name* SET HADR AVAILABILITY GROUP = *group_name*</span></span>|<span data-ttu-id="3ab9d-138">在承载辅助副本的各服务器实例上执行。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-138">Execute on each server instance that hosts a secondary replica.</span></span>|  
  
 <span data-ttu-id="3ab9d-139">**<sup>\*</sup>** 若要执行给定任务，请连接到指示的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-139">**<sup>\*</sup>**  To perform a given task, connect to the indicated server instance or instances.</span></span>  
  
##  <a name="using-transact-sql-to-create-and-configure-an-availability-group"></a><a name="TsqlProcedure"></a> <span data-ttu-id="3ab9d-140">使用 Transact-SQL 创建和配置可用性组</span><span class="sxs-lookup"><span data-stu-id="3ab9d-140">Using Transact-SQL to Create and Configure an Availability Group</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3ab9d-141"> 有关包含上述各 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句的代码示例的配置过程示例，请参阅 [示例：配置使用 Windows 身份验证的可用性组](#ExampleConfigAGWinAuth)。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-141">For a sample configuration procedure containing code examples of each these [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements, see [Example: Configuring an Availability Group that Uses Windows Authentication](#ExampleConfigAGWinAuth).</span></span>  
  
1.  <span data-ttu-id="3ab9d-142">连接到要承载主副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-142">Connect to the server instance that is to host the primary replica.</span></span>  
  
2.  <span data-ttu-id="3ab9d-143">使用[CREATE AVAILABILITY group](/sql/t-sql/statements/create-availability-group-transact-sql)语句创建可用性组 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-143">Create the availability group by using the [CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] statement.</span></span>  
  
3.  <span data-ttu-id="3ab9d-144">将新的辅助副本联接到可用性组。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-144">Join the new secondary replica to the availability group.</span></span> <span data-ttu-id="3ab9d-145">有关详细信息，请参阅 [将辅助副本联接到可用性组 (SQL Server)](join-a-secondary-replica-to-an-availability-group-sql-server.md)或 PowerShell 将辅助数据库联接到 Always On 可用性组。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-145">For more information, see [Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md).</span></span>  
  
4.  <span data-ttu-id="3ab9d-146">对于可用性组中的每个数据库，通过使用 RESTORE WITH NORECOVERY 还原主数据库的最近的备份，创建辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-146">For each database in the availability group, create a secondary database by restoring recent backups of the primary database, using RESTORE WITH NORECOVERY.</span></span> <span data-ttu-id="3ab9d-147">有关详细信息，请参阅 [示例：使用 Windows 身份验证设置可用性组 (Transact-SQL)](create-an-availability-group-transact-sql.md)，从还原数据库备份的步骤开始。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-147">For more information, see [Example: Setting Up an Availability Group Using Windows Authentication (Transact-SQL)](create-an-availability-group-transact-sql.md), starting with the step that restores the database backup.</span></span>  
  
5.  <span data-ttu-id="3ab9d-148">将每个新的辅助数据库联接到可用性组。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-148">Join every new secondary database to the availability group.</span></span> <span data-ttu-id="3ab9d-149">有关详细信息，请参阅 [将辅助副本联接到可用性组 (SQL Server)](join-a-secondary-replica-to-an-availability-group-sql-server.md)或 PowerShell 将辅助数据库联接到 Always On 可用性组。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-149">For more information, see [Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md).</span></span>  
  
##  <a name="example-configuring-an-availability-group-that-uses-windows-authentication"></a><a name="ExampleConfigAGWinAuth"></a><span data-ttu-id="3ab9d-150">示例：配置使用 Windows 身份验证的可用性组</span><span class="sxs-lookup"><span data-stu-id="3ab9d-150">Example: Configuring an Availability Group that Uses Windows Authentication</span></span>  
 <span data-ttu-id="3ab9d-151">此示例创建一个示例 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 配置过程，该过程使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 设置使用 Windows 身份验证的数据库镜像端点并且创建和配置一个可用性组及其辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-151">This example creates a sample [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] configuration procedure that uses [!INCLUDE[tsql](../../../includes/tsql-md.md)] to set up database mirroring endpoints that use Windows Authentication and to create and configure an availability group and its secondary databases.</span></span>  
  
 <span data-ttu-id="3ab9d-152">此示例包含以下部分：</span><span class="sxs-lookup"><span data-stu-id="3ab9d-152">This example contains the following sections:</span></span>  
  
-   [<span data-ttu-id="3ab9d-153">使用示例配置过程的先决条件</span><span class="sxs-lookup"><span data-stu-id="3ab9d-153">Prerequisites for Using the Sample Configuration Procedure</span></span>](#PrerequisitesForExample)  
  
-   [<span data-ttu-id="3ab9d-154">示例配置过程</span><span class="sxs-lookup"><span data-stu-id="3ab9d-154">Sample Configuration Procedure</span></span>](#SampleProcedure)  
  
-   [<span data-ttu-id="3ab9d-155">示例配置过程的完整代码示例</span><span class="sxs-lookup"><span data-stu-id="3ab9d-155">Complete Code Example for Sample Configuration Procedure</span></span>](#CompleteCodeExample)  
  
###  <a name="prerequisites-for-using-the-sample-configuration-procedure"></a><a name="PrerequisitesForExample"></a><span data-ttu-id="3ab9d-156">使用示例配置过程的先决条件</span><span class="sxs-lookup"><span data-stu-id="3ab9d-156">Prerequisites for Using the Sample Configuration Procedure</span></span>  
 <span data-ttu-id="3ab9d-157">此示例过程具有以下要求：</span><span class="sxs-lookup"><span data-stu-id="3ab9d-157">This sample procedure has the following requirements:</span></span>  
  
-   <span data-ttu-id="3ab9d-158">服务器实例必须支持 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-158">The server instances must support [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].</span></span> <span data-ttu-id="3ab9d-159">有关详细信息，请参阅[针对 AlwaysOn 可用性组的先决条件、限制和建议 (SQL Server)](prereqs-restrictions-recommendations-always-on-availability.md)。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-159">For more information, see [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
-   <span data-ttu-id="3ab9d-160">两个示例数据库 *MyDb1* 和 *MyDb2*必须在将承载主副本的服务器实例上存在。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-160">Two sample databases, *MyDb1* and *MyDb2*, must exist on the server instance that will host the primary replica.</span></span> <span data-ttu-id="3ab9d-161">下面的代码示例创建和配置这两个数据库，并且创建这两个数据库的完整备份。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-161">The following code examples create and configure these two databases and create a full backup of each.</span></span> <span data-ttu-id="3ab9d-162">在您想要创建示例可用性组的服务器实例上执行这些代码示例。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-162">Execute these code examples on the server instance on which you intend to create the sample availability group.</span></span> <span data-ttu-id="3ab9d-163">此服务器实例将承载示例可用性组的初始主副本。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-163">This server instance will host the initial primary replica of the sample availability group.</span></span>  
  
    1.  <span data-ttu-id="3ab9d-164">下面的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 示例创建这些数据库并且将它们更改为使用完整恢复模式：</span><span class="sxs-lookup"><span data-stu-id="3ab9d-164">The following [!INCLUDE[tsql](../../../includes/tsql-md.md)] example creates these databases and alters them to use the full recovery model:</span></span>  
  
        ```sql
        -- Create sample databases:  
        CREATE DATABASE MyDb1;  
        GO  
        ALTER DATABASE MyDb1 SET RECOVERY FULL;  
        GO  
  
        CREATE DATABASE MyDb2;  
        GO  
        ALTER DATABASE MyDb2 SET RECOVERY FULL;  
        GO  
        ```  
  
    2.  <span data-ttu-id="3ab9d-165">下面的代码示例创建 *MyDb1* 和 *MyDb2*的完整数据库备份。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-165">The following code example creates a full database backup of *MyDb1* and *MyDb2*.</span></span> <span data-ttu-id="3ab9d-166">此代码示例使用虚构的备份共享 \\ \\ *FILESERVER* \\ *SQLbackups*。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-166">This code example uses a fictional backup share, \\\\*FILESERVER*\\*SQLbackups*.</span></span>  
  
        ```sql
        -- Backup sample databases:  
        BACKUP DATABASE MyDb1   
        TO DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
            WITH FORMAT  
        GO  
  
        BACKUP DATABASE MyDb2   
        TO DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
            WITH FORMAT  
        GO
        ```  
  
###  <a name="sample-configuration-procedure"></a><a name="SampleProcedure"></a> <span data-ttu-id="3ab9d-167">示例配置过程</span><span class="sxs-lookup"><span data-stu-id="3ab9d-167">Sample Configuration Procedure</span></span>  
 <span data-ttu-id="3ab9d-168">在这个示例配置中，将在两个独立服务器实例上创建可用性副本，这些服务器实例的服务帐户在不同的可信域（`DOMAIN1` 和 `DOMAIN2`）下运行。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-168">In this sample configuration, the availability replica will be created on two stand-alone server instances whose service accounts run under different, but trusted, domains (`DOMAIN1` and `DOMAIN2`).</span></span>  
  
 <span data-ttu-id="3ab9d-169">下表总结了此示例配置中使用的值。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-169">The following table summarizes the values used in this sample configuration.</span></span>  
  
|<span data-ttu-id="3ab9d-170">初始角色</span><span class="sxs-lookup"><span data-stu-id="3ab9d-170">Initial role</span></span>|<span data-ttu-id="3ab9d-171">系统</span><span class="sxs-lookup"><span data-stu-id="3ab9d-171">System</span></span>|<span data-ttu-id="3ab9d-172">主机 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例</span><span class="sxs-lookup"><span data-stu-id="3ab9d-172">Host [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Instance</span></span>|  
|------------------|------------|---------------------------------------------|  
|<span data-ttu-id="3ab9d-173">主</span><span class="sxs-lookup"><span data-stu-id="3ab9d-173">Primary</span></span>|`COMPUTER01`|`AgHostInstance`|  
|<span data-ttu-id="3ab9d-174">辅助副本</span><span class="sxs-lookup"><span data-stu-id="3ab9d-174">Secondary</span></span>|`COMPUTER02`|<span data-ttu-id="3ab9d-175">默认实例。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-175">Default instance.</span></span>|  
  
1.  <span data-ttu-id="3ab9d-176">在你计划创建可用性组的服务器实例（这是 *上名为* 的实例）上创建名为 `AgHostInstance` dbm_endpoint `COMPUTER01`的数据库镜像端点。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-176">Create a database mirroring endpoint named *dbm_endpoint* on the server instance on which you plan to create the availability group (this is an instance named `AgHostInstance` on `COMPUTER01`).</span></span> <span data-ttu-id="3ab9d-177">此端点使用端口 7022。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-177">This endpoint uses port 7022.</span></span> <span data-ttu-id="3ab9d-178">请注意，您要在其上创建可用性组的服务器实例将承载主副本。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-178">Note that the server instance on which you create the availability group will host the primary replica.</span></span>  
  
    ```sql
    -- Create endpoint on server instance that hosts the primary replica:  
    CREATE ENDPOINT dbm_endpoint  
        STATE=STARTED   
        AS TCP (LISTENER_PORT=7022)   
        FOR DATABASE_MIRRORING (ROLE=ALL)  
    GO
    ```  
  
2.  <span data-ttu-id="3ab9d-179">在将承载辅助副本的服务器实例（这是 *上的默认服务器实例）上创建端点* dbm_endpoint `COMPUTER02`。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-179">Create an endpoint *dbm_endpoint* on the server instance that will host the secondary replica (this is the default server instance on `COMPUTER02`).</span></span> <span data-ttu-id="3ab9d-180">此端点使用端口 5022。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-180">This endpoint uses port 5022.</span></span>  
  
    ```sql
    -- Create endpoint on server instance that hosts the secondary replica:   
    CREATE ENDPOINT dbm_endpoint  
        STATE=STARTED   
        AS TCP (LISTENER_PORT=5022)   
        FOR DATABASE_MIRRORING (ROLE=ALL)  
    GO
    ```  
  
3.  > [!NOTE]  
    >  <span data-ttu-id="3ab9d-181">如果要承载您的可用性副本的服务器实例的服务帐户基于相同的域帐户运行，则不需要执行此步骤。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-181">If the service accounts of the server instances that are to host your availability replicas run under the same domain account this step is unnecessary.</span></span> <span data-ttu-id="3ab9d-182">跳过它，直接进入下一步。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-182">Skip it and go directly to the next step.</span></span>  
  
     <span data-ttu-id="3ab9d-183">如果该服务器实例的服务帐户基于不同的域用户运行，则在各服务器实例上，为其他服务器实例创建一个登录名，并且授予此登录名访问本地数据库镜像端点的权限。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-183">If the service accounts of the server instances run under different domain users, on each server instance, create a login for the other server instance and grant this login permission to access the local database mirroring endpoint.</span></span>  
  
     <span data-ttu-id="3ab9d-184">下面的代码示例说明用于创建一个登录名并且向该登录名授予针对某一端点的权限的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-184">The following code example shows the [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements for creating a login and granting it permission on an endpoint.</span></span> <span data-ttu-id="3ab9d-185">远程服务器实例的域帐户在此处表示为 *domain_name*\\*user_name*。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-185">The domain account of the remote server instance is represented here as *domain_name*\\*user_name*.</span></span>  
  
    ```sql
    -- If necessary, create a login for the service account, domain_name\user_name  
    -- of the server instance that will host the other replica:  
    USE master;  
    GO  
    CREATE LOGIN [domain_name\user_name] FROM WINDOWS;  
    GO  
    -- And Grant this login connect permissions on the endpoint:  
    GRANT CONNECT ON ENDPOINT::dbm_endpoint   
       TO [domain_name\user_name];  
    GO  
    ```  
  
4.  <span data-ttu-id="3ab9d-186">在用户数据库驻留的服务器实例上，创建可用性组。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-186">On the server instance where the user databases reside, create the availability group.</span></span>  
  
     <span data-ttu-id="3ab9d-187">下面的代码示例在创建了示例数据库 *MyDb1* 和 *MyDb2* 的服务器实例上创建名为 *MyAG*的可用性组。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-187">The following code example creates an availability group named *MyAG* on the server instance on which the sample databases, *MyDb1* and *MyDb2*, were created.</span></span> <span data-ttu-id="3ab9d-188">首先指定 `AgHostInstance`COMPUTER01 *上的本地服务器实例* 。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-188">The local server instance, `AgHostInstance`, on *COMPUTER01* is specified first.</span></span> <span data-ttu-id="3ab9d-189">该实例将承载初始的主副本。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-189">This instance will host the initial primary replica.</span></span> <span data-ttu-id="3ab9d-190">指定远程服务器实例（ *COMPUTER02*上的默认服务器实例）承载辅助副本。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-190">A remote server instance, the default server instance on *COMPUTER02*, is specified to host a secondary replica.</span></span> <span data-ttu-id="3ab9d-191">将两个可用性副本配置为使用异步提交模式和手动故障转移（对于异步提交副本，手动故障转移意味着强制故障转移可能造成数据丢失）。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-191">Both availability replica are configured to use asynchronous-commit mode with manual failover (for asynchronous-commit replicas manual failover means  forced failover with possible data loss).</span></span>  
  
    ```sql
    -- Create the availability group, MyAG:   
    CREATE AVAILABILITY GROUP MyAG   
       FOR   
          DATABASE MyDB1, MyDB2   
       REPLICA ON   
          'COMPUTER01\AgHostInstance' WITH   
             (  
             ENDPOINT_URL = 'TCP://COMPUTER01.Adventure-Works.com:7022',   
             AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,  
             FAILOVER_MODE = MANUAL  
             ),  
          'COMPUTER02' WITH   
             (  
             ENDPOINT_URL = 'TCP://COMPUTER02.Adventure-Works.com:5022',  
             AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,  
             FAILOVER_MODE = MANUAL  
             );   
    GO  
    ```  
  
     <span data-ttu-id="3ab9d-192">有关创建可用性组的其他 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 代码示例，请参阅 [CREATE AVAILABILITY GROUP (Transact-SQL);](/sql/t-sql/statements/create-availability-group-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="3ab9d-192">For additional [!INCLUDE[tsql](../../../includes/tsql-md.md)] code examples of creating an availability group, see [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-availability-group-transact-sql).</span></span>  
  
5.  <span data-ttu-id="3ab9d-193">在承载辅助副本的服务器实例上，将辅助副本联接到可用性组。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-193">On the server instance that hosts the secondary replica, join the secondary replica to the availability group.</span></span>  
  
     <span data-ttu-id="3ab9d-194">下面的代码示例将 `COMPUTER02` 上的辅助副本联接到 `MyAG` 可用性组。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-194">The following code example joins the secondary replica on `COMPUTER02` to the `MyAG` availability group.</span></span>  
  
    ```sql
    -- On the server instance that hosts the secondary replica,   
    -- join the secondary replica to the availability group:  
    ALTER AVAILABILITY GROUP MyAG JOIN;  
    GO  
    ```  
  
6.  <span data-ttu-id="3ab9d-195">在承载辅助副本的服务器实例上，创建辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-195">On the server instance that hosts the secondary replica, create the secondary databases.</span></span>  
  
     <span data-ttu-id="3ab9d-196">以下代码示例通过使用 RESTORE WITH NORECOVERY 还原数据库备份来创建 *MyDb1* 和 *MyDb2* 辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-196">The following code example creates the *MyDb1* and *MyDb2* secondary databases by restoring database backups using RESTORE WITH NORECOVERY.</span></span>  
  
    ```sql
    -- On the server instance that hosts the secondary replica,   
    -- Restore database backups using the WITH NORECOVERY option:  
    RESTORE DATABASE MyDb1   
        FROM DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
        WITH NORECOVERY  
    GO  
  
    RESTORE DATABASE MyDb2   
        FROM DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
        WITH NORECOVERY  
    GO
    ```  
  
7.  <span data-ttu-id="3ab9d-197">在承载主副本的服务器实例上，备份每个主数据库上的事务日志。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-197">On the server instance that hosts the primary replica, back up the transaction log on each of the primary databases.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="3ab9d-198">在您配置真实的可用性组时，我们建议在进行此日志备份之前，挂起针对您的主数据库的日志备份任务，直到您将相应的辅助数据库联接到该可用性组。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-198">When you are configuring a real availability group, we recommend that, before taking this log backup, you suspend log backup tasks for your primary databases until you have joined the corresponding secondary databases to the availability group.</span></span>  
  
     <span data-ttu-id="3ab9d-199">下面的代码示例在 MyDb1 和 MyDb2 上创建一个事务日志备份。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-199">The following code example creates a transaction log backup on MyDb1 and on MyDb2.</span></span>  
  
    ```sql
    -- On the server instance that hosts the primary replica,   
    -- Backup the transaction log on each primary database:  
    BACKUP LOG MyDb1   
    TO DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
        WITH NOFORMAT  
    GO  
  
    BACKUP LOG MyDb2   
    TO DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
        WITHNOFORMAT  
    GO
    ```  
  
    > [!TIP]  
    >  <span data-ttu-id="3ab9d-200">通常，日志备份必须在每个主数据库上进行，然后在相应的辅助数据库上还原（使用 WITH NORECOVERY）。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-200">Typically, a log backup must be taken on each primary database and then restored on the corresponding secondary database (using WITH NORECOVERY).</span></span> <span data-ttu-id="3ab9d-201">但是，如果数据库刚刚创建而尚未进行日志备份，或者如果恢复模式刚刚从 SIMPLE 更改为 FULL，则不必进行此日志备份。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-201">However, this log backup might be unnecessary if the database has just been created and no log backup has been taken yet or the recovery model has just been changed from SIMPLE to FULL.</span></span>  
  
8.  <span data-ttu-id="3ab9d-202">在承载辅助副本的服务器实例上，将日志备份应用于辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-202">On the server instance that hosts the secondary replica, apply log backups to the secondary databases.</span></span>  
  
     <span data-ttu-id="3ab9d-203">以下代码示例通过使用 RESTORE WITH NORECOVERY 还原数据库备份来将备份应用于 *MyDb1* 和 *MyDb2* 辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-203">The following code example applies backups to *MyDb1* and *MyDb2* secondary databases by restoring database backups using RESTORE WITH NORECOVERY.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="3ab9d-204">在您准备真实的辅助数据库时，需要应用您从其创建了辅助数据库的数据库备份之后发生的每个日志备份，从最早的开始并且始终使用 RESTORE WITH NORECOVERY。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-204">When you are preparing a real secondary database, you need to apply every log backup taken since the database backup from which you created the secondary database, starting with the earliest and always using RESTORE WITH NORECOVERY.</span></span> <span data-ttu-id="3ab9d-205">当然，如果您还原完整和差异数据库备份，则只需应用在差异备份后发生的日志备份。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-205">Of course, if you restore both full and differential database backups, you would only need to apply the log backups taken after the differential backup.</span></span>  
  
    ```sql
    -- Restore the transaction log on each secondary database,  
    -- using the WITH NORECOVERY option:  
    RESTORE LOG MyDb1   
        FROM DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
        WITH FILE=1, NORECOVERY  
    GO  
    RESTORE LOG MyDb2   
        FROM DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
        WITH FILE=1, NORECOVERY  
    GO  
    ```  
  
9. <span data-ttu-id="3ab9d-206">在承载辅助副本的服务器实例上，将新的辅助数据库联接到可用性组。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-206">On the server instance that hosts the secondary replica, join the new secondary databases to the availability group.</span></span>  
  
     <span data-ttu-id="3ab9d-207">下面的代码示例依次将 *MyDb1* 辅助数据库和 *MyDb2* 辅助数据库联接到 *MyAG* 可用性组。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-207">The following code example, joins the *MyDb1* secondary database and then the *MyDb2* secondary databases to the *MyAG* availability group.</span></span>  
  
    ```sql
    -- On the server instance that hosts the secondary replica,   
    -- join each secondary database to the availability group:  
    ALTER DATABASE MyDb1 SET HADR AVAILABILITY GROUP = MyAG;  
    GO  
  
    ALTER DATABASE MyDb2 SET HADR AVAILABILITY GROUP = MyAG;  
    GO
    ```  
  
###  <a name="complete-code-example-for-sample-configuration-procedure"></a><a name="CompleteCodeExample"></a> <span data-ttu-id="3ab9d-208">示例配置过程的完整代码示例</span><span class="sxs-lookup"><span data-stu-id="3ab9d-208">Complete Code Example for Sample Configuration Procedure</span></span>  
 <span data-ttu-id="3ab9d-209">下面的示例合并了示例配置过程的所有步骤中的代码示例。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-209">The following example merges the code examples from all the steps of the sample configuration procedure.</span></span> <span data-ttu-id="3ab9d-210">下表总结了此代码示例中使用的占位符值。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-210">The following table summarized the placeholder values used in this code example.</span></span> <span data-ttu-id="3ab9d-211">有关此代码示例中的步骤的详细信息，请参阅本主题中前面的 [使用示例配置过程的先决条件](#PrerequisitesForExample) 和 [示例配置过程](#SampleProcedure)。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-211">For more information about the steps in this code example, see [Prerequisites for Using the Sample Configuration Procedure](#PrerequisitesForExample) and [Sample Configuration Procedure](#SampleProcedure), earlier in this topic.</span></span>  
  
|<span data-ttu-id="3ab9d-212">占位符</span><span class="sxs-lookup"><span data-stu-id="3ab9d-212">Placeholder</span></span>|<span data-ttu-id="3ab9d-213">说明</span><span class="sxs-lookup"><span data-stu-id="3ab9d-213">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="3ab9d-214">\\\\*FILESERVER*\\*SQLbackups*</span><span class="sxs-lookup"><span data-stu-id="3ab9d-214">\\\\*FILESERVER*\\*SQLbackups*</span></span>|<span data-ttu-id="3ab9d-215">虚构的备份共享。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-215">Fictional backup share.</span></span>|  
|<span data-ttu-id="3ab9d-216">\\\\*FILESERVER*\\*SQLbackups\MyDb1.bak*</span><span class="sxs-lookup"><span data-stu-id="3ab9d-216">\\\\*FILESERVER*\\*SQLbackups\MyDb1.bak*</span></span>|<span data-ttu-id="3ab9d-217">MyDb1 的备份文件。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-217">Backup file for MyDb1.</span></span>|  
|<span data-ttu-id="3ab9d-218">\\\\*FILESERVER*\\*SQLbackups\MyDb2.bak*</span><span class="sxs-lookup"><span data-stu-id="3ab9d-218">\\\\*FILESERVER*\\*SQLbackups\MyDb2.bak*</span></span>|<span data-ttu-id="3ab9d-219">MyDb2 的备份文件。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-219">Backup file for MyDb2.</span></span>|  
|<span data-ttu-id="3ab9d-220">*7022*</span><span class="sxs-lookup"><span data-stu-id="3ab9d-220">*7022*</span></span>|<span data-ttu-id="3ab9d-221">分配给各数据库镜像端点的端口号。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-221">Port number assigned to each database mirroring endpoint.</span></span>|  
|<span data-ttu-id="3ab9d-222">*COMPUTER01\AgHostInstance*</span><span class="sxs-lookup"><span data-stu-id="3ab9d-222">*COMPUTER01\AgHostInstance*</span></span>|<span data-ttu-id="3ab9d-223">承载初始主副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-223">Server instance that hosts the initial primary replica.</span></span>|  
|<span data-ttu-id="3ab9d-224">*COMPUTER02*</span><span class="sxs-lookup"><span data-stu-id="3ab9d-224">*COMPUTER02*</span></span>|<span data-ttu-id="3ab9d-225">承载初始辅助副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-225">Server instance that hosts the initial secondary replica.</span></span> <span data-ttu-id="3ab9d-226">这是 `COMPUTER02`上的默认服务器实例。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-226">This is the default server instance on `COMPUTER02`.</span></span>|  
|<span data-ttu-id="3ab9d-227">*上名为*</span><span class="sxs-lookup"><span data-stu-id="3ab9d-227">*dbm_endpoint*</span></span>|<span data-ttu-id="3ab9d-228">为每个数据库镜像端点指定的名称。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-228">Name specified for each database mirroring endpoint.</span></span>|  
|<span data-ttu-id="3ab9d-229">*MyDb1*</span><span class="sxs-lookup"><span data-stu-id="3ab9d-229">*MyAG*</span></span>|<span data-ttu-id="3ab9d-230">示例可用性组的名称。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-230">Name of sample availability group.</span></span>|  
|<span data-ttu-id="3ab9d-231">*MyDb1*</span><span class="sxs-lookup"><span data-stu-id="3ab9d-231">*MyDb1*</span></span>|<span data-ttu-id="3ab9d-232">第一个示例数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-232">Name of first sample database.</span></span>|  
|<span data-ttu-id="3ab9d-233">*MyDb2*</span><span class="sxs-lookup"><span data-stu-id="3ab9d-233">*MyDb2*</span></span>|<span data-ttu-id="3ab9d-234">第二个示例数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-234">Name of second sample database.</span></span>|  
|<span data-ttu-id="3ab9d-235">*DOMAIN1\user1*</span><span class="sxs-lookup"><span data-stu-id="3ab9d-235">*DOMAIN1\user1*</span></span>|<span data-ttu-id="3ab9d-236">要承载初始主副本的服务器实例的服务帐户。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-236">Service account of the server instance that is to host the initial primary replica.</span></span>|  
|<span data-ttu-id="3ab9d-237">*DOMAIN2\user2*</span><span class="sxs-lookup"><span data-stu-id="3ab9d-237">*DOMAIN2\user2*</span></span>|<span data-ttu-id="3ab9d-238">要承载初始辅助副本的服务器实例的服务帐户。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-238">Service account of the server instance that is to host the initial secondary replica.</span></span>|  
|<span data-ttu-id="3ab9d-239">TCP://*COMPUTER01.Adventure-Works.com*:*7022*</span><span class="sxs-lookup"><span data-stu-id="3ab9d-239">TCP://*COMPUTER01.Adventure-Works.com*:*7022*</span></span>|<span data-ttu-id="3ab9d-240">COMPUTER01 上 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的 AgHostInstance 实例的端点 URL。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-240">Endpoint URL of the AgHostInstance instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on COMPUTER01.</span></span>|  
|<span data-ttu-id="3ab9d-241">TCP://*COMPUTER02.Adventure-Works.com*:*5022*</span><span class="sxs-lookup"><span data-stu-id="3ab9d-241">TCP://*COMPUTER02.Adventure-Works.com*:*5022*</span></span>|<span data-ttu-id="3ab9d-242">COMPUTER02 上 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的默认实例的端点 URL。</span><span class="sxs-lookup"><span data-stu-id="3ab9d-242">Endpoint URL of the default instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on COMPUTER02.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="3ab9d-243">有关创建可用性组的其他 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 代码示例，请参阅 [CREATE AVAILABILITY GROUP (Transact-SQL);](/sql/t-sql/statements/create-availability-group-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="3ab9d-243">For additional [!INCLUDE[tsql](../../../includes/tsql-md.md)] code examples of creating an availability group, see [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-availability-group-transact-sql).</span></span>  
  
```sql
-- on the server instance that will host the primary replica,   
-- create sample databases:  
CREATE DATABASE MyDb1;  
GO  
ALTER DATABASE MyDb1 SET RECOVERY FULL;  
GO  
  
CREATE DATABASE MyDb2;  
GO  
ALTER DATABASE MyDb2 SET RECOVERY FULL;  
GO  
  
-- Backup sample databases:  
BACKUP DATABASE MyDb1   
TO DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
    WITH FORMAT  
GO  
  
BACKUP DATABASE MyDb2   
TO DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
    WITH FORMAT  
GO  
  
-- Create the endpoint on the server instance that will host the primary replica:  
CREATE ENDPOINT dbm_endpoint  
    STATE=STARTED   
    AS TCP (LISTENER_PORT=7022)   
    FOR DATABASE_MIRRORING (ROLE=ALL)  
GO  
  
-- Create the endpoint on the server instance that will host the secondary replica:   
CREATE ENDPOINT dbm_endpoint  
    STATE=STARTED   
    AS TCP (LISTENER_PORT=7022)   
    FOR DATABASE_MIRRORING (ROLE=ALL)  
GO  
  
-- If both service accounts run under the same domain account, skip this step. Otherwise,   
-- On the server instance that will host the primary replica,   
-- create a login for the service account   
-- of the server instance that will host the secondary replica, DOMAIN2\user2,   
-- and grant this login connect permissions on the endpoint:  
USE master;  
GO  
CREATE LOGIN [DOMAIN2\user2] FROM WINDOWS;  
GO  
GRANT CONNECT ON ENDPOINT::dbm_endpoint   
   TO [DOMAIN2\user2];  
GO  
  
-- If both service accounts run under the same domain account, skip this step. Otherwise,   
-- On the server instance that will host the secondary replica,  
-- create a login for the service account   
-- of the server instance that will host the primary replica, DOMAIN1\user1,   
-- and grant this login connect permissions on the endpoint:  
USE master;  
GO  
  
CREATE LOGIN [DOMAIN1\user1] FROM WINDOWS;  
GO  
GRANT CONNECT ON ENDPOINT::dbm_endpoint   
   TO [DOMAIN1\user1];  
GO  
  
-- On the server instance that will host the primary replica,   
-- create the availability group, MyAG:  
CREATE AVAILABILITY GROUP MyAG   
   FOR   
      DATABASE MyDB1, MyDB2   
   REPLICA ON   
      'COMPUTER01\AgHostInstance' WITH   
         (  
         ENDPOINT_URL = 'TCP://COMPUTER01.Adventure-Works.com:7022',  
         AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,  
         FAILOVER_MODE = AUTOMATIC  
         ),  
      'COMPUTER02' WITH   
         (  
         ENDPOINT_URL = 'TCP://COMPUTER02.Adventure-Works.com:7022',  
         AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,  
         FAILOVER_MODE = AUTOMATIC  
         );   
GO  
  
-- On the server instance that hosts the secondary replica,   
-- join the secondary replica to the availability group:  
ALTER AVAILABILITY GROUP MyAG JOIN;  
GO  
  
-- Restore database backups onto this server instance, using RESTORE WITH NORECOVERY:  
RESTORE DATABASE MyDb1   
    FROM DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
    WITH NORECOVERY  
GO  
  
RESTORE DATABASE MyDb2   
    FROM DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
    WITH NORECOVERY  
GO  
  
-- Back up the transaction log on each primary database:  
BACKUP LOG MyDb1   
TO DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
    WITH NOFORMAT  
GO  
  
BACKUP LOG MyDb2   
TO DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
    WITHNOFORMAT  
GO  
  
-- Restore the transaction log on each secondary database,  
-- using the WITH NORECOVERY option:  
RESTORE LOG MyDb1   
    FROM DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
    WITH FILE=1, NORECOVERY  
GO  
RESTORE LOG MyDb2   
    FROM DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
    WITH FILE=1, NORECOVERY  
GO  
  
-- On the server instance that hosts the secondary replica,   
-- join each secondary database to the availability group:  
ALTER DATABASE MyDb1 SET HADR AVAILABILITY GROUP = MyAG;  
GO  
  
ALTER DATABASE MyDb2 SET HADR AVAILABILITY GROUP = MyAG;  
GO
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="3ab9d-244">相关任务</span><span class="sxs-lookup"><span data-stu-id="3ab9d-244">Related Tasks</span></span>  
 <span data-ttu-id="3ab9d-245">**配置可用性组和副本属性**</span><span class="sxs-lookup"><span data-stu-id="3ab9d-245">**To configure availability group and replica properties**</span></span>  
  
-   [<span data-ttu-id="3ab9d-246">更改可用性副本的可用性模式 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="3ab9d-246">Change the Availability Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-availability-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="3ab9d-247">更改可用性副本的故障转移模式 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="3ab9d-247">Change the Failover Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-failover-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="3ab9d-248">创建或配置可用性组侦听程序 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="3ab9d-248">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="3ab9d-249">配置灵活的故障转移策略以控制自动故障转移的条件（AlwaysOn 可用性组）</span><span class="sxs-lookup"><span data-stu-id="3ab9d-249">Configure the Flexible Failover Policy to Control Conditions for Automatic Failover (AlwaysOn Availability Groups)</span></span>](configure-flexible-automatic-failover-policy.md)  
  
-   [<span data-ttu-id="3ab9d-250">在添加或修改可用性副本时指定终结点 URL (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="3ab9d-250">Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;</span></span>](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
-   [<span data-ttu-id="3ab9d-251">配置可用性副本备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="3ab9d-251">Configure Backup on Availability Replicas &#40;SQL Server&#41;</span></span>](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [<span data-ttu-id="3ab9d-252">配置对可用性副本的只读访问 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="3ab9d-252">Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;</span></span>](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="3ab9d-253">为可用性组配置只读路由 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="3ab9d-253">Configure Read-Only Routing for an Availability Group &#40;SQL Server&#41;</span></span>](configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="3ab9d-254">更改可用性副本的会话超时期限 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="3ab9d-254">Change the Session-Timeout Period for an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
 <span data-ttu-id="3ab9d-255">**完成可用性组配置**</span><span class="sxs-lookup"><span data-stu-id="3ab9d-255">**To complete availability group configuration**</span></span>  
  
-   [<span data-ttu-id="3ab9d-256">将辅助副本联接到可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="3ab9d-256">Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="3ab9d-257">为可用性组手动准备辅助数据库 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="3ab9d-257">Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;</span></span>](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="3ab9d-258">将辅助数据库联接到可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="3ab9d-258">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="3ab9d-259">创建或配置可用性组侦听程序 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="3ab9d-259">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
 <span data-ttu-id="3ab9d-260">**用于创建可用性组的其他方法**</span><span class="sxs-lookup"><span data-stu-id="3ab9d-260">**Alternative ways to create an availability group**</span></span>  
  
-   [<span data-ttu-id="3ab9d-261">使用可用性组向导 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="3ab9d-261">Use the Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="3ab9d-262">使用“新建可用性组”对话框 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="3ab9d-262">Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;</span></span>](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="3ab9d-263">创建可用性组 (SQL Server PowerShell)</span><span class="sxs-lookup"><span data-stu-id="3ab9d-263">Create an Availability Group &#40;SQL Server PowerShell&#41;</span></span>](../../../powershell/sql-server-powershell.md)  
  
 <span data-ttu-id="3ab9d-264">**启用 AlwaysOn 可用性组**</span><span class="sxs-lookup"><span data-stu-id="3ab9d-264">**To enable AlwaysOn Availability Groups**</span></span>  
  
-   [<span data-ttu-id="3ab9d-265">启用和禁用 AlwaysOn 可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="3ab9d-265">Enable and Disable AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](enable-and-disable-always-on-availability-groups-sql-server.md)  
  
 <span data-ttu-id="3ab9d-266">**配置数据库镜像端点**</span><span class="sxs-lookup"><span data-stu-id="3ab9d-266">**To configure a database mirroring endpoint**</span></span>  
  
-   [<span data-ttu-id="3ab9d-267">为 AlwaysOn 可用性组 &#40;SQL Server PowerShell 创建数据库镜像端点&#41;</span><span class="sxs-lookup"><span data-stu-id="3ab9d-267">Create a Database Mirroring Endpoint for AlwaysOn Availability Groups &#40;SQL Server PowerShell&#41;</span></span>](database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [<span data-ttu-id="3ab9d-268">为 Windows 身份验证创建数据库镜像终结点 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="3ab9d-268">Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [<span data-ttu-id="3ab9d-269">使用数据库镜像终结点证书 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="3ab9d-269">Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
-   [<span data-ttu-id="3ab9d-270">在添加或修改可用性副本时指定终结点 URL (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="3ab9d-270">Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;</span></span>](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
 <span data-ttu-id="3ab9d-271">**解决 AlwaysOn 可用性组配置问题**</span><span class="sxs-lookup"><span data-stu-id="3ab9d-271">**To troubleshoot AlwaysOn Availability Groups configuration**</span></span>  
  
-   [<span data-ttu-id="3ab9d-272">) 删除 AlwaysOn 可用性组配置 (SQL Server 的疑难解答</span><span class="sxs-lookup"><span data-stu-id="3ab9d-272">Troubleshoot AlwaysOn Availability Groups Configuration (SQL Server)deleted</span></span>](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
-   [<span data-ttu-id="3ab9d-273">排除失败的添加文件操作 &#40;AlwaysOn 可用性组&#41;</span><span class="sxs-lookup"><span data-stu-id="3ab9d-273">Troubleshoot a Failed Add-File Operation &#40;AlwaysOn Availability Groups&#41;</span></span>](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="3ab9d-274">相关内容</span><span class="sxs-lookup"><span data-stu-id="3ab9d-274">Related Content</span></span>  
  
-   <span data-ttu-id="3ab9d-275">**博客：**</span><span class="sxs-lookup"><span data-stu-id="3ab9d-275">**Blogs:**</span></span>  
  
     [<span data-ttu-id="3ab9d-276">AlwaysON - HADRON 学习系列：启用了 HADRON 的数据库的工作线程池用法</span><span class="sxs-lookup"><span data-stu-id="3ab9d-276">AlwaysON - HADRON Learning Series: Worker Pool Usage for HADRON Enabled Databases</span></span>](https://blogs.msdn.com/b/psssql/archive/2012/05/17/alwayson-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
     [<span data-ttu-id="3ab9d-277">SQL Server AlwaysOn 团队博客：SQL Server AlwaysOn 官方团队博客</span><span class="sxs-lookup"><span data-stu-id="3ab9d-277">SQL Server AlwaysOn Team Blogs: The official SQL Server AlwaysOn Team Blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [<span data-ttu-id="3ab9d-278">CSS SQL Server 工程师博客</span><span class="sxs-lookup"><span data-stu-id="3ab9d-278">CSS SQL Server Engineers Blogs</span></span>](https://blogs.msdn.com/b/psssql/)  
  
-   <span data-ttu-id="3ab9d-279">**视频：**</span><span class="sxs-lookup"><span data-stu-id="3ab9d-279">**Videos:**</span></span>  
  
     [<span data-ttu-id="3ab9d-280">Microsoft SQL Server Code-Named "Denali" AlwaysOn 系列，第一部分：介绍下一代高可用性解决方案</span><span class="sxs-lookup"><span data-stu-id="3ab9d-280">Microsoft SQL Server Code-Named "Denali" AlwaysOn Series,Part 1: Introducing the Next Generation High Availability Solution</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [<span data-ttu-id="3ab9d-281">Microsoft SQL Server Code-Named "Denali" AlwaysOn 系列，第二部分：使用 AlwaysOn 生成关键任务高可用性解决方案</span><span class="sxs-lookup"><span data-stu-id="3ab9d-281">Microsoft SQL Server Code-Named "Denali" AlwaysOn Series,Part 2: Building a Mission-Critical High Availability Solution Using AlwaysOn</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   <span data-ttu-id="3ab9d-282">**白皮书：**</span><span class="sxs-lookup"><span data-stu-id="3ab9d-282">**Whitepapers:**</span></span>  
  
     [<span data-ttu-id="3ab9d-283">用于高可用性和灾难恢复的 Microsoft SQL Server AlwaysOn 解决方案指南</span><span class="sxs-lookup"><span data-stu-id="3ab9d-283">Microsoft SQL Server AlwaysOn Solutions Guide for High Availability and Disaster Recovery</span></span>](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [<span data-ttu-id="3ab9d-284">针对 SQL Server 2012 的 Microsoft 白皮书</span><span class="sxs-lookup"><span data-stu-id="3ab9d-284">Microsoft White Papers for SQL Server 2012</span></span>](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [<span data-ttu-id="3ab9d-285">SQL Server 客户咨询团队白皮书</span><span class="sxs-lookup"><span data-stu-id="3ab9d-285">SQL Server Customer Advisory Team Whitepapers</span></span>](http://sqlcat.com/)  
  
## <a name="see-also"></a><span data-ttu-id="3ab9d-286">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3ab9d-286">See Also</span></span>  
 <span data-ttu-id="3ab9d-287">[数据库镜像终结点 (SQL Server)](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3ab9d-287">[The Database Mirroring Endpoint &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md) </span></span>  
 <span data-ttu-id="3ab9d-288">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3ab9d-288">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="3ab9d-289">可用性组侦听程序、客户端连接和应用程序故障转移 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="3ab9d-289">Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;</span></span>](../../listeners-client-connectivity-application-failover.md)   
