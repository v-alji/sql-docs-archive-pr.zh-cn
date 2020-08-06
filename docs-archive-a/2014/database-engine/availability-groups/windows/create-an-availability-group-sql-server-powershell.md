---
title: 创建可用性组 (SQL Server PowerShell) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], creating
ms.assetid: bc69a7df-20fa-41e1-9301-11317c5270d2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3af9bf896b954e6849c0d491f9ed267655369ccb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694567"
---
# <a name="create-an-availability-group-sql-server-powershell"></a><span data-ttu-id="0e378-102">创建可用性组 (SQL Server PowerShell)</span><span class="sxs-lookup"><span data-stu-id="0e378-102">Create an Availability Group (SQL Server PowerShell)</span></span>
  <span data-ttu-id="0e378-103">本主题说明如何使用 PowerShell cmdlet 在 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]中通过 PowerShell 创建和配置 AlwaysOn 可用性组。</span><span class="sxs-lookup"><span data-stu-id="0e378-103">This topic describes how to use PowerShell cmdlets to create and configure an AlwaysOn availability group by using PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="0e378-104">“可用性组” \*\* 定义一组用户数据库，这些用户数据库将以支持故障转移的单个单元和一组故障转移伙伴（称作“可用性副本” \*\*）的形式进行故障转移。</span><span class="sxs-lookup"><span data-stu-id="0e378-104">An *availability group* defines a set of user databases that will fail over as a single unit and a set of failover partners, known as *availability replicas*, which support failover.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0e378-105">有关可用性组的简介，请参阅 [AlwaysOn 可用性组概述 (SQL Server)](overview-of-always-on-availability-groups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="0e378-105">For an introduction to availability groups, see [Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).</span></span>  

> [!NOTE]  
>  <span data-ttu-id="0e378-106">除了使用 PowerShell cmdlet 之外，您还可以使用“创建可用性组”向导或 [!INCLUDE[tsql](../../../includes/tsql-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0e378-106">As an alternative to using PowerShell cmdlets, you can use the Create Availability Group wizard or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="0e378-107">有关详细信息，请参阅 [使用“新建可用性组”对话框 (SQL Server Management Studio)](use-the-new-availability-group-dialog-box-sql-server-management-studio.md) 或 [创建可用性组 (Transact-SQL)](create-an-availability-group-transact-sql.md)中通过 PowerShell 创建和配置 AlwaysOn 可用性组。</span><span class="sxs-lookup"><span data-stu-id="0e378-107">For more information, see [Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md) or [Create an Availability Group &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md).</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0e378-108">开始之前</span><span class="sxs-lookup"><span data-stu-id="0e378-108">Before You Begin</span></span>  
 <span data-ttu-id="0e378-109">我们强烈建议您首先阅读此部分，再尝试创建您的第一个可用性组。</span><span class="sxs-lookup"><span data-stu-id="0e378-109">We strongly recommend that you read this section before attempting to create your first availability group.</span></span>  
  
###  <a name="prerequisites-restrictions-and-recommendations"></a><a name="PrerequisitesRestrictions"></a> <span data-ttu-id="0e378-110">先决条件、限制和建议</span><span class="sxs-lookup"><span data-stu-id="0e378-110">Prerequisites, Restrictions, and Recommendations</span></span>  
  
-   <span data-ttu-id="0e378-111">创建可用性组之前，请先验证 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 主机实例分别位于单个 WSFC 故障转移群集的不同 Windows Server 故障转移群集 (WSFC) 节点上。</span><span class="sxs-lookup"><span data-stu-id="0e378-111">Before creating an availability group, verify that the host instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] each resides on a different Windows Server Failover Clustering (WSFC) node of a single WSFC failover cluster.</span></span> <span data-ttu-id="0e378-112">此外，还要验证您的服务器实例满足其他服务器实例先决条件，并且其他所有 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]要求都得到满足且您知道有关建议。</span><span class="sxs-lookup"><span data-stu-id="0e378-112">Also, verify that your server instances met the other server-instance prerequisites and that all of the other [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] requirements are meet and that you are aware of the recommendations.</span></span> <span data-ttu-id="0e378-113">有关详细信息，我们强烈建议你参阅[针对 AlwaysOn 可用性组的先决条件、限制和建议 (SQL Server)](prereqs-restrictions-recommendations-always-on-availability.md)。</span><span class="sxs-lookup"><span data-stu-id="0e378-113">For more information, we strongly recommend that you read [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0e378-114">Security</span><span class="sxs-lookup"><span data-stu-id="0e378-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="0e378-115">权限</span><span class="sxs-lookup"><span data-stu-id="0e378-115">Permissions</span></span>  
 <span data-ttu-id="0e378-116">需要 **sysadmin** 固定服务器角色的成员资格，以及 CREATE AVAILABILITY GROUP 服务器权限、ALTER ANY AVAILABILITY GROUP 权限或 CONTROL SERVER 权限。</span><span class="sxs-lookup"><span data-stu-id="0e378-116">Requires membership in the **sysadmin** fixed server role and either CREATE AVAILABILITY GROUP server permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
###  <a name="summary-of-tasks-and-corresponding-powershell-cmdlets"></a><a name="SummaryPSStatements"></a><span data-ttu-id="0e378-117">任务和相应 PowerShell Cmdlet 的摘要</span><span class="sxs-lookup"><span data-stu-id="0e378-117">Summary of Tasks and Corresponding PowerShell Cmdlets</span></span>  
 <span data-ttu-id="0e378-118">下表列出了涉及配置可用性组的基本任务，并且指出了 PowerShell cmdlet 支持的任务。</span><span class="sxs-lookup"><span data-stu-id="0e378-118">The following table lists the basic tasks involved in configuring an availability group and indicates those that are supported by PowerShell cmdlets.</span></span> <span data-ttu-id="0e378-119">必须按照任务在表中出现的顺序执行 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 任务。</span><span class="sxs-lookup"><span data-stu-id="0e378-119">The [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] tasks must be performed in the sequence in which they are presented in the table.</span></span>  
  
|<span data-ttu-id="0e378-120">任务</span><span class="sxs-lookup"><span data-stu-id="0e378-120">Task</span></span>|<span data-ttu-id="0e378-121">PowerShell Cmdlet（如果可用）或 Transact-SQL 语句</span><span class="sxs-lookup"><span data-stu-id="0e378-121">PowerShell Cmdlets (if Available) or Transact-SQL Statement</span></span>|<span data-ttu-id="0e378-122">执行任务的位置**<sup>\*</sup>**</span><span class="sxs-lookup"><span data-stu-id="0e378-122">Where to Perform Task**<sup>\*</sup>**</span></span>|  
|----------|--------------------------------------------------------------------|-------------------------------------------|  
|<span data-ttu-id="0e378-123">创建数据库镜像端点（每个 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例一次）</span><span class="sxs-lookup"><span data-stu-id="0e378-123">Create database mirroring endpoint (once per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance)</span></span>|`New-SqlHadrEndPoint`|<span data-ttu-id="0e378-124">在缺少数据库镜像端点的每个服务器实例上执行。</span><span class="sxs-lookup"><span data-stu-id="0e378-124">Execute on each server instance that lacks database mirroring endpoint.</span></span><br /><br /> <span data-ttu-id="0e378-125">注意：若要更改现有数据库镜像端点，请使用 `Set-SqlHadrEndpoint`。</span><span class="sxs-lookup"><span data-stu-id="0e378-125">Note: To alter an existing database mirroring endpoint, use `Set-SqlHadrEndpoint`.</span></span>|  
|<span data-ttu-id="0e378-126">创建可用性组</span><span class="sxs-lookup"><span data-stu-id="0e378-126">Create availability group</span></span>|<span data-ttu-id="0e378-127">首先，将 `New-SqlAvailabilityReplica` cmdlet 与 `-AsTemplate` 参数一起使用，以便为您计划包括在可用性组中的两个可用性副本中的每一个都创建内存中可用性副本对象。</span><span class="sxs-lookup"><span data-stu-id="0e378-127">First, use the `New-SqlAvailabilityReplica` cmdlet with the `-AsTemplate` parameter to create an in-memory availability-replica object for each of the two availability replicas that you plan to include in the availability group.</span></span><br /><br /> <span data-ttu-id="0e378-128">然后，通过使用 `New-SqlAvailabilityGroup` cmdlet 并引用您的可用性副本对象，创建可用性组。</span><span class="sxs-lookup"><span data-stu-id="0e378-128">Then, create the availability group by using the `New-SqlAvailabilityGroup` cmdlet and referencing your availability-replica objects.</span></span>|<span data-ttu-id="0e378-129">在要承载初始主副本的服务器实例上执行。</span><span class="sxs-lookup"><span data-stu-id="0e378-129">Execute on the server instance that is to host the initial primary replica.</span></span>|  
|<span data-ttu-id="0e378-130">将辅助副本联接到可用性组</span><span class="sxs-lookup"><span data-stu-id="0e378-130">Join secondary replica to availability group</span></span>|`Join-SqlAvailabilityGroup`|<span data-ttu-id="0e378-131">在承载辅助副本的各服务器实例上执行。</span><span class="sxs-lookup"><span data-stu-id="0e378-131">Execute on each server instance that is hosts a secondary replica.</span></span>|  
|<span data-ttu-id="0e378-132">准备辅助数据库</span><span class="sxs-lookup"><span data-stu-id="0e378-132">Prepare the secondary database</span></span>|<span data-ttu-id="0e378-133">`Backup-SqlDatabase` 和 `Restore-SqlDatabase`</span><span class="sxs-lookup"><span data-stu-id="0e378-133">`Backup-SqlDatabase` and `Restore-SqlDatabase`</span></span>|<span data-ttu-id="0e378-134">在承载主副本的服务器实例上创建备份。</span><span class="sxs-lookup"><span data-stu-id="0e378-134">Create backups on the server instance that hosts the primary replica.</span></span><br /><br /> <span data-ttu-id="0e378-135">使用 `NoRecovery` 还原参数在承载辅助副本的各服务器实例上还原备份。</span><span class="sxs-lookup"><span data-stu-id="0e378-135">Restore backups on each server instance that hosts a secondary replica, using the `NoRecovery` restore parameter.</span></span> <span data-ttu-id="0e378-136">如果文件路径在承载主副本和目标辅助副本的计算机之间存在差异，还要使用 `RelocateFile` 还原参数。</span><span class="sxs-lookup"><span data-stu-id="0e378-136">If the file paths differ between the computers that host the primary replica and the target secondary replica, also use the `RelocateFile` restore parameter.</span></span>|  
|<span data-ttu-id="0e378-137">通过将各辅助数据库联接到可用性组，开始数据同步</span><span class="sxs-lookup"><span data-stu-id="0e378-137">Start data synchronization by joining each secondary database to availability group</span></span>|`Add-SqlAvailabilityDatabase`|<span data-ttu-id="0e378-138">在承载辅助副本的各服务器实例上执行。</span><span class="sxs-lookup"><span data-stu-id="0e378-138">Execute on each server instance that hosts a secondary replica.</span></span>|  
  
 <span data-ttu-id="0e378-139">**<sup>\*</sup>** 若要执行给定任务，请将目录 (`cd`) 更改为指示的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="0e378-139">**<sup>\*</sup>**  To perform a given task, change directory (`cd`) to the indicated server instance or instances.</span></span>  
  
###  <a name="to-set-up-and-use-the-sql-server-powershell-provider"></a><a name="PsProviderLinks"></a><span data-ttu-id="0e378-140">设置并使用 SQL Server PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="0e378-140">To Set Up and Use the SQL Server PowerShell Provider</span></span>  
  
-   [<span data-ttu-id="0e378-141">SQL Server PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="0e378-141">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
-   [<span data-ttu-id="0e378-142">Get Help SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="0e378-142">Get Help SQL Server PowerShell</span></span>](../../../powershell/sql-server-powershell.md)  
  
##  <a name="using-powershell-to-create-and-configure-an-availability-group"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="0e378-143">使用 PowerShell 创建和配置可用性组</span><span class="sxs-lookup"><span data-stu-id="0e378-143">Using PowerShell to Create and Configure an Availability Group</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0e378-144">若要查看给定 cmdlet 的语法和示例，请使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell 环境中的 `Get-Help` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0e378-144">To view the syntax and an example of a given cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="0e378-145">有关详细信息，请参阅 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="0e378-145">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
1.  <span data-ttu-id="0e378-146">将目录 (`cd`) 更改为承载主副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="0e378-146">Change directory (`cd`) to the server instance that is to host the primary replica.</span></span>  
  
2.  <span data-ttu-id="0e378-147">为主副本创建内存中可用性副本对象。</span><span class="sxs-lookup"><span data-stu-id="0e378-147">Create an in-memory availability-replica object for the primary replica.</span></span>  
  
3.  <span data-ttu-id="0e378-148">为每个辅助副本创建内存中可用性副本对象。</span><span class="sxs-lookup"><span data-stu-id="0e378-148">Create an in-memory availability-replica object for each of the secondary replicas.</span></span>  
  
4.  <span data-ttu-id="0e378-149">创建可用性组。</span><span class="sxs-lookup"><span data-stu-id="0e378-149">Create the availability group.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0e378-150">可用性组名称的最大长度为 128 个字符。</span><span class="sxs-lookup"><span data-stu-id="0e378-150">The maximum length for an availability group name is 128 characters.</span></span>  
  
5.  <span data-ttu-id="0e378-151">将新的辅助副本联接到可用性组。</span><span class="sxs-lookup"><span data-stu-id="0e378-151">Join the new secondary replica to the availability group.</span></span> <span data-ttu-id="0e378-152">有关详细信息，请参阅 [将辅助副本联接到可用性组 (SQL Server)](join-a-secondary-replica-to-an-availability-group-sql-server.md)或 PowerShell 将辅助数据库联接到 Always On 可用性组。</span><span class="sxs-lookup"><span data-stu-id="0e378-152">For more information, see [Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md).</span></span>  
  
6.  <span data-ttu-id="0e378-153">对于可用性组中的每个数据库，通过使用 RESTORE WITH NORECOVERY 还原主数据库的最近的备份，创建辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="0e378-153">For each database in the availability group, create a secondary database by restoring recent backups of the primary database, using RESTORE WITH NORECOVERY.</span></span>  
  
7.  <span data-ttu-id="0e378-154">将每个新的辅助数据库联接到可用性组。</span><span class="sxs-lookup"><span data-stu-id="0e378-154">Join every new secondary database to the availability group.</span></span> <span data-ttu-id="0e378-155">有关详细信息，请参阅 [将辅助副本联接到可用性组 (SQL Server)](join-a-secondary-replica-to-an-availability-group-sql-server.md)或 PowerShell 将辅助数据库联接到 Always On 可用性组。</span><span class="sxs-lookup"><span data-stu-id="0e378-155">For more information, see [Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md).</span></span>  
  
8.  <span data-ttu-id="0e378-156">或者，使用 Windows `dir` 命令可以验证新的可用性组的内容。</span><span class="sxs-lookup"><span data-stu-id="0e378-156">Optionally, use the Windows `dir` command to verify the contents of the new availability group.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0e378-157">如果服务器实例的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服务帐户基于不同的域用户帐户运行，则在各服务器实例上，为其他服务器实例创建一个登录名，并且授予此登录名对本地数据库镜像端点的 CONNECT 权限。</span><span class="sxs-lookup"><span data-stu-id="0e378-157">If the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service accounts of the server instances run under different domain user accounts, on each server instance, create a login for the other server instance and grant this login CONNECT permission to the local database mirroring endpoint.</span></span>  
  
##  <a name="example-using-powershell-to-create-an-availability-group"></a><a name="ExampleConfigureGroup"></a><span data-ttu-id="0e378-158">示例：使用 PowerShell 创建可用性组</span><span class="sxs-lookup"><span data-stu-id="0e378-158">Example: Using PowerShell to Create an Availability Group</span></span>  
 <span data-ttu-id="0e378-159">下面的 PowerShell 示例创建并配置一个名为 `MyAG` 的简单可用性组，该可用性组具有两个可用性副本和一个可用性数据库。</span><span class="sxs-lookup"><span data-stu-id="0e378-159">The following PowerShell example creates and configures a simple availability group named `MyAG` with two availability replicas and one availability database.</span></span> <span data-ttu-id="0e378-160">示例：</span><span class="sxs-lookup"><span data-stu-id="0e378-160">The example:</span></span>  
  
1.  <span data-ttu-id="0e378-161">备份 `MyDatabase` 及其事务日志。</span><span class="sxs-lookup"><span data-stu-id="0e378-161">Backs up `MyDatabase` and its transaction log.</span></span>  
  
2.  <span data-ttu-id="0e378-162">使用 `-NoRecovery` 选项还原 `MyDatabase` 及其事务日志。</span><span class="sxs-lookup"><span data-stu-id="0e378-162">Restores `MyDatabase` and its transaction log, using the `-NoRecovery` option.</span></span>  
  
3.  <span data-ttu-id="0e378-163">创建主副本的内存中表示形式，它将由 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的本地实例（名为 `PrimaryComputer\Instance`）承载。</span><span class="sxs-lookup"><span data-stu-id="0e378-163">Creates an in-memory representation of the primary replica, which will be hosted by the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (named `PrimaryComputer\Instance`).</span></span>  
  
4.  <span data-ttu-id="0e378-164">创建辅助副本的内存中表示形式，它将由 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的本地实例（名为 `SecondaryComputer\Instance`）承载。</span><span class="sxs-lookup"><span data-stu-id="0e378-164">Creates an in-memory representation of the secondary replica, which will be hosted by an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (named `SecondaryComputer\Instance`).</span></span>  
  
5.  <span data-ttu-id="0e378-165">创建名为 `MyAG`的可用性组。</span><span class="sxs-lookup"><span data-stu-id="0e378-165">Creates an availability group named `MyAG`.</span></span>  
  
6.  <span data-ttu-id="0e378-166">将辅助副本联接到该可用性组。</span><span class="sxs-lookup"><span data-stu-id="0e378-166">Joins the secondary replica to the availability group.</span></span>  
  
7.  <span data-ttu-id="0e378-167">将辅助数据库联接到该可用性组。</span><span class="sxs-lookup"><span data-stu-id="0e378-167">Joins the secondary database to the availability group.</span></span>  
  
```powershell
# Backup my database and its log on the primary  
Backup-SqlDatabase `  
    -Database "MyDatabase" `  
    -BackupFile "\\share\backups\MyDatabase.bak" `  
    -ServerInstance "PrimaryComputer\Instance"  
  
Backup-SqlDatabase `  
    -Database "MyDatabase" `  
    -BackupFile "\\share\backups\MyDatabase.log" `  
    -ServerInstance "PrimaryComputer\Instance" `  
    -BackupAction Log   
  
# Restore the database and log on the secondary (using NO RECOVERY)  
Restore-SqlDatabase `  
    -Database "MyDatabase" `  
    -BackupFile "\\share\backups\MyDatabase.bak" `  
    -ServerInstance "SecondaryComputer\Instance" `  
    -NoRecovery  
  
Restore-SqlDatabase `  
    -Database "MyDatabase" `  
    -BackupFile "\\share\backups\MyDatabase.log" `  
    -ServerInstance "SecondaryComputer\Instance" `  
    -RestoreAction Log `  
    -NoRecovery  
  
# Create an in-memory representation of the primary replica.  
$primaryReplica = New-SqlAvailabilityReplica `  
    -Name "PrimaryComputer\Instance" `  
    -EndpointURL "TCP://PrimaryComputer.domain.com:5022" `  
    -AvailabilityMode "SynchronousCommit" `  
    -FailoverMode "Automatic" `  
    -Version 12 `  
    -AsTemplate  
  
# Create an in-memory representation of the secondary replica.  
$secondaryReplica = New-SqlAvailabilityReplica `  
    -Name "SecondaryComputer\Instance" `  
    -EndpointURL "TCP://SecondaryComputer.domain.com:5022" `  
    -AvailabilityMode "SynchronousCommit" `  
    -FailoverMode "Automatic" `  
    -Version 12 `  
    -AsTemplate  
  
# Create the availability group  
New-SqlAvailabilityGroup `  
    -Name "MyAG" `  
    -Path "SQLSERVER:\SQL\PrimaryComputer\Instance" `  
    -AvailabilityReplica @($primaryReplica,$secondaryReplica) `  
    -Database "MyDatabase"  
  
# Join the secondary replica to the availability group.  
Join-SqlAvailabilityGroup -Path "SQLSERVER:\SQL\SecondaryComputer\Instance" -Name "MyAG"  
  
# Join the secondary database to the availability group.  
Add-SqlAvailabilityDatabase -Path "SQLSERVER:\SQL\SecondaryComputer\Instance\AvailabilityGroups\MyAG" -Database "MyDatabase"  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="0e378-168">相关任务</span><span class="sxs-lookup"><span data-stu-id="0e378-168">Related Tasks</span></span>  
 <span data-ttu-id="0e378-169">**为 AlwaysOn 可用性组配置服务器实例**</span><span class="sxs-lookup"><span data-stu-id="0e378-169">**To configure a server instance for AlwaysOn Availability Groups**</span></span>  
  
-   [<span data-ttu-id="0e378-170">启用和禁用 AlwaysOn 可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0e378-170">Enable and Disable AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](enable-and-disable-always-on-availability-groups-sql-server.md)  
  
-   [<span data-ttu-id="0e378-171">为 AlwaysOn 可用性组 &#40;SQL Server PowerShell 创建数据库镜像端点&#41;</span><span class="sxs-lookup"><span data-stu-id="0e378-171">Create a Database Mirroring Endpoint for AlwaysOn Availability Groups &#40;SQL Server PowerShell&#41;</span></span>](database-mirroring-always-on-availability-groups-powershell.md)  
  
 <span data-ttu-id="0e378-172">**配置可用性组和副本属性**</span><span class="sxs-lookup"><span data-stu-id="0e378-172">**To configure availability group and replica properties**</span></span>  
  
-   [<span data-ttu-id="0e378-173">更改可用性副本的可用性模式 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0e378-173">Change the Availability Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-availability-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="0e378-174">更改可用性副本的故障转移模式 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0e378-174">Change the Failover Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-failover-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="0e378-175">创建或配置可用性组侦听程序 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0e378-175">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="0e378-176">配置灵活的故障转移策略以控制自动故障转移的条件（AlwaysOn 可用性组）</span><span class="sxs-lookup"><span data-stu-id="0e378-176">Configure the Flexible Failover Policy to Control Conditions for Automatic Failover (AlwaysOn Availability Groups)</span></span>](configure-flexible-automatic-failover-policy.md)  
  
-   [<span data-ttu-id="0e378-177">在添加或修改可用性副本时指定终结点 URL (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0e378-177">Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;</span></span>](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
-   [<span data-ttu-id="0e378-178">配置可用性副本备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0e378-178">Configure Backup on Availability Replicas &#40;SQL Server&#41;</span></span>](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [<span data-ttu-id="0e378-179">配置对可用性副本的只读访问 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0e378-179">Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;</span></span>](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="0e378-180">为可用性组配置只读路由 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0e378-180">Configure Read-Only Routing for an Availability Group &#40;SQL Server&#41;</span></span>](configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="0e378-181">更改可用性副本的会话超时期限 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0e378-181">Change the Session-Timeout Period for an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
 <span data-ttu-id="0e378-182">**完成可用性组配置**</span><span class="sxs-lookup"><span data-stu-id="0e378-182">**To complete availability group configuration**</span></span>  
  
-   [<span data-ttu-id="0e378-183">将辅助副本联接到可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0e378-183">Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="0e378-184">为可用性组手动准备辅助数据库 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0e378-184">Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;</span></span>](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="0e378-185">将辅助数据库联接到可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0e378-185">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="0e378-186">创建或配置可用性组侦听程序 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0e378-186">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
 <span data-ttu-id="0e378-187">**用于创建可用性组的其他方法**</span><span class="sxs-lookup"><span data-stu-id="0e378-187">**Alternative ways to create an availability group**</span></span>  
  
-   [<span data-ttu-id="0e378-188">使用可用性组向导 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="0e378-188">Use the Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="0e378-189">使用“新建可用性组”对话框 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="0e378-189">Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;</span></span>](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="0e378-190">创建可用性组 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0e378-190">Create an Availability Group &#40;Transact-SQL&#41;</span></span>](create-an-availability-group-transact-sql.md)  
  
 <span data-ttu-id="0e378-191">**解决 AlwaysOn 可用性组配置问题**</span><span class="sxs-lookup"><span data-stu-id="0e378-191">**To troubleshoot AlwaysOn Availability Groups configuration**</span></span>  
  
-   [<span data-ttu-id="0e378-192">) 删除 AlwaysOn 可用性组配置 (SQL Server 的疑难解答</span><span class="sxs-lookup"><span data-stu-id="0e378-192">Troubleshoot AlwaysOn Availability Groups Configuration (SQL Server)deleted</span></span>](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
-   [<span data-ttu-id="0e378-193">排除失败的添加文件操作 &#40;AlwaysOn 可用性组&#41;</span><span class="sxs-lookup"><span data-stu-id="0e378-193">Troubleshoot a Failed Add-File Operation &#40;AlwaysOn Availability Groups&#41;</span></span>](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="0e378-194">相关内容</span><span class="sxs-lookup"><span data-stu-id="0e378-194">Related Content</span></span>  
  
-   <span data-ttu-id="0e378-195">**博客：**</span><span class="sxs-lookup"><span data-stu-id="0e378-195">**Blogs:**</span></span>  
  
     [<span data-ttu-id="0e378-196">AlwaysON - HADRON 学习系列：启用了 HADRON 的数据库的工作线程池用法</span><span class="sxs-lookup"><span data-stu-id="0e378-196">AlwaysON - HADRON Learning Series: Worker Pool Usage for HADRON Enabled Databases</span></span>](https://blogs.msdn.com/b/psssql/archive/2012/05/17/alwayson-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
     [<span data-ttu-id="0e378-197">使用 SQL Server PowerShell 配置 AlwaysOn</span><span class="sxs-lookup"><span data-stu-id="0e378-197">Configuring AlwaysOn with SQL Server PowerShell</span></span>](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/03/configuring-alwayson-with-sql-server-powershell.aspx)  
  
     [<span data-ttu-id="0e378-198">SQL Server AlwaysOn 团队博客：SQL Server AlwaysOn 官方团队博客</span><span class="sxs-lookup"><span data-stu-id="0e378-198">SQL Server AlwaysOn Team Blogs: The official SQL Server AlwaysOn Team Blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [<span data-ttu-id="0e378-199">CSS SQL Server 工程师博客</span><span class="sxs-lookup"><span data-stu-id="0e378-199">CSS SQL Server Engineers Blogs</span></span>](https://blogs.msdn.com/b/psssql/)  
  
-   <span data-ttu-id="0e378-200">**视频：**</span><span class="sxs-lookup"><span data-stu-id="0e378-200">**Videos:**</span></span>  
  
     [<span data-ttu-id="0e378-201">Microsoft SQL Server Code-Named "Denali" AlwaysOn 系列，第一部分：介绍下一代高可用性解决方案</span><span class="sxs-lookup"><span data-stu-id="0e378-201">Microsoft SQL Server Code-Named "Denali" AlwaysOn Series,Part 1: Introducing the Next Generation High Availability Solution</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [<span data-ttu-id="0e378-202">Microsoft SQL Server Code-Named "Denali" AlwaysOn 系列，第二部分：使用 AlwaysOn 生成关键任务高可用性解决方案</span><span class="sxs-lookup"><span data-stu-id="0e378-202">Microsoft SQL Server Code-Named "Denali" AlwaysOn Series,Part 2: Building a Mission-Critical High Availability Solution Using AlwaysOn</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   <span data-ttu-id="0e378-203">**白皮书：**</span><span class="sxs-lookup"><span data-stu-id="0e378-203">**Whitepapers:**</span></span>  
  
     [<span data-ttu-id="0e378-204">用于高可用性和灾难恢复的 Microsoft SQL Server AlwaysOn 解决方案指南</span><span class="sxs-lookup"><span data-stu-id="0e378-204">Microsoft SQL Server AlwaysOn Solutions Guide for High Availability and Disaster Recovery</span></span>](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [<span data-ttu-id="0e378-205">针对 SQL Server 2012 的 Microsoft 白皮书</span><span class="sxs-lookup"><span data-stu-id="0e378-205">Microsoft White Papers for SQL Server 2012</span></span>](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [<span data-ttu-id="0e378-206">SQL Server 客户咨询团队白皮书</span><span class="sxs-lookup"><span data-stu-id="0e378-206">SQL Server Customer Advisory Team Whitepapers</span></span>](http://sqlcat.com/)  
  
## <a name="see-also"></a><span data-ttu-id="0e378-207">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0e378-207">See Also</span></span>  
 [<span data-ttu-id="0e378-208">数据库镜像终结点 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0e378-208">The Database Mirroring Endpoint &#40;SQL Server&#41;</span></span>](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md)   
