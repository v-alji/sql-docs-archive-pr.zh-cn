---
title: 配置可用性副本备份 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- backup priority
- backup on secondary replicas
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], backup on secondary replicas
- active secondary replicas [SQL Server], backup on
- automated backup preference
- Availability Groups [SQL Server], active secondary replicas
ms.assetid: 74bc40bb-9f57-44e4-8988-1d69c0585eb6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 91a781d957eb2f5a81d323fc3c65c93e34945c12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693492"
---
# <a name="configure-backup-on-availability-replicas-sql-server"></a><span data-ttu-id="bdfa8-102">配置可用性副本备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="bdfa8-102">Configure Backup on Availability Replicas (SQL Server)</span></span>
  <span data-ttu-id="bdfa8-103">本主题说明如何通过在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]中使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)]、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]或 PowerShell 配置 AlwaysOn 可用性组的辅助副本的备份。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-103">This topic describes how to configure backup on secondary replicas for an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bdfa8-104">有关辅助副本备份的介绍，请参阅[活动辅助副本：辅助副本上的备份 (AlwaysOn 可用性组) ](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-104">For an introduction to backup on secondary replicas, see [Active Secondaries: Backup on Secondary Replicas (AlwaysOn Availability Groups)](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md).</span></span>  
  
 
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="bdfa8-105">开始之前</span><span class="sxs-lookup"><span data-stu-id="bdfa8-105">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="bdfa8-106">先决条件</span><span class="sxs-lookup"><span data-stu-id="bdfa8-106">Prerequisites</span></span>  
 <span data-ttu-id="bdfa8-107">您必须连接到承载主副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-107">You must be connected to the server instance that hosts the primary replica.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="bdfa8-108">Security</span><span class="sxs-lookup"><span data-stu-id="bdfa8-108">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="bdfa8-109">权限</span><span class="sxs-lookup"><span data-stu-id="bdfa8-109">Permissions</span></span>  
  
|<span data-ttu-id="bdfa8-110">任务</span><span class="sxs-lookup"><span data-stu-id="bdfa8-110">Task</span></span>|<span data-ttu-id="bdfa8-111">权限</span><span class="sxs-lookup"><span data-stu-id="bdfa8-111">Permissions</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="bdfa8-112">创建可用性组时配置辅助副本备份</span><span class="sxs-lookup"><span data-stu-id="bdfa8-112">To configure backup on secondary replicas when creating an availability group</span></span>|<span data-ttu-id="bdfa8-113">需要 **sysadmin** 固定服务器角色的成员资格，以及 CREATE AVAILABILITY GROUP 服务器权限、ALTER ANY AVAILABILITY GROUP 权限或 CONTROL SERVER 权限。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-113">Requires membership in the **sysadmin** fixed server role and either CREATE AVAILABILITY GROUP server permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>|  
|<span data-ttu-id="bdfa8-114">修改可用性组或可用性副本</span><span class="sxs-lookup"><span data-stu-id="bdfa8-114">To modify an availability group or availability replica</span></span>|<span data-ttu-id="bdfa8-115">对可用性组要求 ALTER AVAILABILITY GROUP 权限、CONTROL AVAILABILITY GROUP 权限、ALTER ANY AVAILABILITY GROUP 权限或 CONTROL SERVER 权限。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-115">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>|  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="bdfa8-116">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="bdfa8-116">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="bdfa8-117">**配置辅助副本备份**</span><span class="sxs-lookup"><span data-stu-id="bdfa8-117">**To configure backup on secondary replicas**</span></span>  
  
1.  <span data-ttu-id="bdfa8-118">在对象资源管理器中，连接到承载主副本的服务器实例，然后单击服务器名称以便展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-118">In Object Explorer, connect to the server instance that hosts the primary replica, and click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="bdfa8-119">依次展开 **“AlwaysOn 高可用性”** 节点和 **“可用性组”** 节点。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-119">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="bdfa8-120">单击要为其配置备份首选项的可用性组，然后选择 **“属性”** 命令。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-120">Click the availability group whose backup preferences you want to configure, and select the **Properties** command.</span></span>  
  
4.  <span data-ttu-id="bdfa8-121">在 **“可用性组属性”** 对话框中，选择 **“备份首选项”** 页。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-121">In the **Availability Group Properties** dialog box, select **Backup Preferences** page.</span></span>  
  
5.  <span data-ttu-id="bdfa8-122">在 **“应在何处进行备份?”** 面板中，选择可用性组的下列自动备份首选项之一：</span><span class="sxs-lookup"><span data-stu-id="bdfa8-122">On the **Where should backups occur?** panel, select the automated backup preference for the availability group, one of:</span></span>  
  
     <span data-ttu-id="bdfa8-123">**优先辅助**</span><span class="sxs-lookup"><span data-stu-id="bdfa8-123">**Prefer Secondary**</span></span>  
     <span data-ttu-id="bdfa8-124">指定备份应在辅助副本上发生，但在主副本是唯一联机的副本时除外。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-124">Specifies that backups should occur on a secondary replica except when the primary replica is the only replica online.</span></span> <span data-ttu-id="bdfa8-125">在该情况下，备份应在主副本上发生。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-125">In that case, the backup should occur on the primary replica.</span></span> <span data-ttu-id="bdfa8-126">这是默认选项。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-126">This is the default option.</span></span>  
  
     <span data-ttu-id="bdfa8-127">**仅辅助**</span><span class="sxs-lookup"><span data-stu-id="bdfa8-127">**Secondary only**</span></span>  
     <span data-ttu-id="bdfa8-128">指定备份应该永远不会在主副本上执行。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-128">Specifies that backups should never be performed on the primary replica.</span></span> <span data-ttu-id="bdfa8-129">如果主副本是唯一的联机副本，则备份应不会发生。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-129">If the primary replica is the only replica online, the backup should not occur.</span></span>  
  
     `Primary`  
     <span data-ttu-id="bdfa8-130">指定备份应该始终在主副本上发生。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-130">Specifies that the backups should always occur on the primary replica.</span></span> <span data-ttu-id="bdfa8-131">如果您需要在对辅助副本运行备份时不支持的备份功能，例如创建差异备份，此选项将很有用。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-131">This option is useful if you need backup features, such as creating differential backups, that are not supported when backup is run on a secondary replica.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="bdfa8-132">如果您计划使用日志传送为可用性组准备任何辅助数据库，请将自动备份首选项设置为`Primary`，直到准备好所有辅助数据库并将其加入可用性组。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-132">If you plan to use log shipping to prepare any secondary databases for an availability group, set the automated backup preference to `Primary` until all the secondary databases have been prepared and joined to the availability group.</span></span>  
  
     <span data-ttu-id="bdfa8-133">**任何副本**</span><span class="sxs-lookup"><span data-stu-id="bdfa8-133">**Any Replica**</span></span>  
     <span data-ttu-id="bdfa8-134">指定您希望在选择要执行备份的副本时备份作业将忽略可用性副本的角色。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-134">Specifies that you prefer that backup jobs ignore the role of the availability replicas when choosing the replica to perform backups.</span></span> <span data-ttu-id="bdfa8-135">请注意，备份作业可能评估其他因素，例如每个可用性副本的备份优先级及其操作状态和已连接状态。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-135">Note backup jobs might evaluate other factors such as backup priority of each availability replica in combination with its operational state and connected state.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="bdfa8-136">没有强制的自动备份首选项设置。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-136">There is no enforcement of the automated backup preference setting.</span></span> <span data-ttu-id="bdfa8-137">对此首选项的解释取决于您为给定可用性组中的数据库撰写备份作业脚本的逻辑（如果有）。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-137">The interpretation of this preference depends on the logic, if any, that you script into backup jobs for the databases in a given availability group.</span></span> <span data-ttu-id="bdfa8-138">自动备份首选项设置对即席备份没有影响。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-138">The automated backup preference setting has no impact on ad-hoc backups.</span></span> <span data-ttu-id="bdfa8-139">有关详细信息，请参阅本主题后面的 [跟进：配置辅助副本备份之后](#FollowUp) 。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-139">For more information, see [Follow Up: After Configuring Backup on Secondary Replicas](#FollowUp) later in this topic.</span></span>  
  
6.  <span data-ttu-id="bdfa8-140">使用 **“副本备份优先级”** 网格更改可用性副本的备份优先级。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-140">Use the **Replica backup priorities** grid to change the backup priority of the availability replicas.</span></span> <span data-ttu-id="bdfa8-141">此网格将显示每个承载可用性组的副本的服务器实例的当前备份优先级。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-141">This grid displays the current backup priority of each server instance that hosts a replica for the availability group.</span></span> <span data-ttu-id="bdfa8-142">网格列如下所示：</span><span class="sxs-lookup"><span data-stu-id="bdfa8-142">The grid columns are as follows:</span></span>  
  
     <span data-ttu-id="bdfa8-143">**服务器实例**</span><span class="sxs-lookup"><span data-stu-id="bdfa8-143">**Server Instance**</span></span>  
     <span data-ttu-id="bdfa8-144">承载可用性副本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-144">The name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosts the availability replica.</span></span>  
  
     <span data-ttu-id="bdfa8-145">**备份优先级(最低 = 1，最高 = 100)**</span><span class="sxs-lookup"><span data-stu-id="bdfa8-145">**Backup Priority (Lowest=1, Highest=100)**</span></span>  
     <span data-ttu-id="bdfa8-146">指定相对于同一可用性组中的其他副本，在此副本上执行备份的优先级。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-146">Specifies your priority for performing backups on this replica relative to the other replicas in the same availability group.</span></span> <span data-ttu-id="bdfa8-147">该值是范围 0..100 中的整数。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-147">The value is an integer in the range of 0..100.</span></span> <span data-ttu-id="bdfa8-148">1 表示最低优先级，100 表示最高优先级。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-148">1 indicates the lowest priority, and 100 indicates the highest priority.</span></span> <span data-ttu-id="bdfa8-149">如果“备份优先级”\*\*\*\*= 1，则仅在当前没有更高优先级的可用性副本可用时，才选择此可用性副本来执行备份。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-149">If **Backup Priority** = 1, the availability replica would be chosen for performing backups only if no higher priority availability replicas are currently available.</span></span>  
  
     <span data-ttu-id="bdfa8-150">**排除副本**</span><span class="sxs-lookup"><span data-stu-id="bdfa8-150">**Exclude Replica**</span></span>  
     <span data-ttu-id="bdfa8-151">如果从不希望选择此可用性副本来执行备份，请选择此选项。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-151">Select if you never want this availability replica to be chosen for performing backups.</span></span> <span data-ttu-id="bdfa8-152">例如，这对于您永远不希望备份故障转移到的远程可用性副本十分有用。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-152">This is useful, for example, for a remote availability replica to which you never want backups to fail over.</span></span>  
  
7.  <span data-ttu-id="bdfa8-153">若要提交更改，请单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-153">To commit your changes, click **OK**.</span></span>  
  
 <span data-ttu-id="bdfa8-154">**用于访问“备份首选项”页的其他方法**</span><span class="sxs-lookup"><span data-stu-id="bdfa8-154">**Alternative ways to access the Backup Preferences page**</span></span>  
  
-   [<span data-ttu-id="bdfa8-155">使用“新建可用性组”对话框 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="bdfa8-155">Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;</span></span>](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="bdfa8-156">使用“将副本添加到可用性组向导”(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="bdfa8-156">Use the Add Replica to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="bdfa8-157">使用“新建可用性组”对话框 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="bdfa8-157">Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;</span></span>](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="bdfa8-158">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="bdfa8-158">Using Transact-SQL</span></span>  
 <span data-ttu-id="bdfa8-159">**配置辅助副本备份**</span><span class="sxs-lookup"><span data-stu-id="bdfa8-159">**To configure backup on secondary replicas**</span></span>  
  
1.  <span data-ttu-id="bdfa8-160">连接到承载主副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-160">Connect to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="bdfa8-161">对于新的可用性组，请使用 [CREATE AVAILABILITY GROUP (Transact-SQL)](/sql/t-sql/statements/create-availability-group-transact-sql) 语句。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-161">For a new availability group, use the [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-availability-group-transact-sql) statement.</span></span> <span data-ttu-id="bdfa8-162">如果要修改现有可用性组，请使用 [ALTER AVAILABILITY GROUP (Transact-SQL)](/sql/t-sql/statements/alter-availability-group-transact-sql) 语句。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-162">If you are modifying an existing availability group, use the [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql) statement.</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="bdfa8-163">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="bdfa8-163">Using PowerShell</span></span>  

### <a name="to-configure-backup-on-secondary-replicas"></a><span data-ttu-id="bdfa8-164">配置辅助副本备份</span><span class="sxs-lookup"><span data-stu-id="bdfa8-164">To configure backup on secondary replicas</span></span>
  
1.  <span data-ttu-id="bdfa8-165">将默认的 (`cd`) 设置为承载主副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-165">Set default (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="bdfa8-166">（可选）配置要添加或修改的每个可用性副本的备份优先级。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-166">Optionally, configure the backup priority of each availability replica that you are adding or modifying.</span></span> <span data-ttu-id="bdfa8-167">此优先级由承载主副本的服务器实例用来确定哪一副本应该用于针对可用性组中某一数据库的自动备份请求（选择具有最高优先级的副本）。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-167">This priority is used by the server instance that hosts the primary replica to decide which replica should service an automated backup request on a database in the availability group (the replica with highest priority is chosen).</span></span> <span data-ttu-id="bdfa8-168">该优先级可以是 0 和 100 之间（含 0 和 100）的任何数字。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-168">This priority can be any number between 0 and 100, inclusive.</span></span> <span data-ttu-id="bdfa8-169">优先级 0 指示副本不应视作支持备份请求的候选。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-169">A priority of 0 indicates that the replica should not be considered as a candidate for servicing backup requests.</span></span>  <span data-ttu-id="bdfa8-170">默认设置为 50。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-170">The default setting is 50.</span></span>  
  
     <span data-ttu-id="bdfa8-171">在将可用性副本添加到可用性组中时，请使用 `New-SqlAvailabilityReplica` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-171">When adding an availability replica to an availability group, use the `New-SqlAvailabilityReplica` cmdlet.</span></span> <span data-ttu-id="bdfa8-172">在修改现有可用性副本时，请使用 `Set-SqlAvailabilityReplica` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-172">When modifying an existing availability replica, use the `Set-SqlAvailabilityReplica` cmdlet.</span></span> <span data-ttu-id="bdfa8-173">在任一情况下，指定 `BackupPriority` *n*参数，其中*n*是从0到100的值。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-173">In either case, specify the `BackupPriority`*n* parameter, where *n* is a value from 0 to 100.</span></span>  
  
     <span data-ttu-id="bdfa8-174">例如，以下命令会将可用性副本 `MyReplica` 的备份优先级设置为 `60`。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-174">For example, the following command sets the backup priority of the availability replica `MyReplica` to `60`.</span></span>  
  
    ```powershell
    Set-SqlAvailabilityReplica -BackupPriority 60 -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg\AvailabilityReplicas\MyReplica  
    ```  
  
3.  <span data-ttu-id="bdfa8-175">（可选）配置要创建或修改的可用性组的自动备份首选项。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-175">Optionally, configure the automated backup preference for the availability group that you are creating  or modifying.</span></span> <span data-ttu-id="bdfa8-176">此首选项指示在选择执行备份的位置时备份作业应该如何评估主副本。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-176">This preference indicates how a backup job should evaluate the primary replica when choosing where to perform backups.</span></span> <span data-ttu-id="bdfa8-177">默认设置是首选辅助副本。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-177">The default setting is to prefer secondary replicas.</span></span>  
  
     <span data-ttu-id="bdfa8-178">创建可用性组时，使用 `New-SqlAvailabilityGroup` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-178">When creating an availability group, use the `New-SqlAvailabilityGroup` cmdlet.</span></span> <span data-ttu-id="bdfa8-179">修改现有可用性组时，使用 `Set-SqlAvailabilityGroup` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-179">When modifying an existing availability group, use the `Set-SqlAvailabilityGroup` cmdlet.</span></span> <span data-ttu-id="bdfa8-180">在任一情况下，指定 `AutomatedBackupPreference` 参数。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-180">In either case, specify the `AutomatedBackupPreference` parameter.</span></span>  
  
     <span data-ttu-id="bdfa8-181">其中：</span><span class="sxs-lookup"><span data-stu-id="bdfa8-181">where,</span></span>  
  
     `Primary`  
     <span data-ttu-id="bdfa8-182">指定备份应该始终在主副本上发生。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-182">Specifies that the backups should always occur on the primary replica.</span></span> <span data-ttu-id="bdfa8-183">如果您需要在对辅助副本运行备份时不支持的备份功能，例如创建差异备份，此选项将很有用。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-183">This option is useful if you need backup features, such as creating differential backups, that are not supported when backup is run on a secondary replica.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="bdfa8-184">如果您计划使用日志传送为可用性组准备任何辅助数据库，请将自动备份首选项设置为`Primary`，直到准备好所有辅助数据库并将其加入可用性组。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-184">If you plan to use log shipping to prepare any secondary databases for an availability group, set the automated backup preference to `Primary` until all the secondary databases have been prepared and joined to the availability group.</span></span>  
  
     `SecondaryOnly`  
     <span data-ttu-id="bdfa8-185">指定备份应该永远不会在主副本上执行。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-185">Specifies that backups should never be performed on the primary replica.</span></span> <span data-ttu-id="bdfa8-186">如果主副本是唯一的联机副本，则备份应不会发生。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-186">If the primary replica is the only replica online, the backup should not occur.</span></span>  
  
     `Secondary`  
     <span data-ttu-id="bdfa8-187">指定备份应在辅助副本上发生，但在主副本是唯一联机的副本时除外。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-187">Specifies that backups should occur on a secondary replica except when the primary replica is the only replica online.</span></span> <span data-ttu-id="bdfa8-188">在该情况下，备份应在主副本上发生。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-188">In that case, the backup should occur on the primary replica.</span></span> <span data-ttu-id="bdfa8-189">此选项为默认行为。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-189">This is the default behavior.</span></span>  
  
     `None`  
     <span data-ttu-id="bdfa8-190">指定您希望在选择要执行备份的副本时备份作业将忽略可用性副本的角色。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-190">Specifies that you prefer that backup jobs ignore the role of the availability replicas when choosing the replica to perform backups.</span></span> <span data-ttu-id="bdfa8-191">请注意，备份作业可能评估其他因素，例如每个可用性副本的备份优先级及其操作状态和已连接状态。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-191">Note backup jobs might evaluate other factors such as backup priority of each availability replica in combination with its operational state and  connected state.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="bdfa8-192">没有强制的 `AutomatedBackupPreference`。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-192">There is no enforcement of `AutomatedBackupPreference`.</span></span> <span data-ttu-id="bdfa8-193">对此首选项的解释取决于您为给定可用性组中的数据库撰写备份作业脚本的逻辑（如果有）。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-193">The interpretation of this preference depends on the logic, if any, that you script into backup jobs for the databases in a given availability group.</span></span> <span data-ttu-id="bdfa8-194">自动备份首选项设置对即席备份没有影响。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-194">The automated backup preference setting has no impact on ad-hoc backups.</span></span> <span data-ttu-id="bdfa8-195">有关详细信息，请参阅本主题后面的 [跟进：配置辅助副本备份之后](#FollowUp) 。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-195">For more information, see [Follow Up: After Configuring Backup on Secondary Replicas](#FollowUp) later in this topic.</span></span>  
  
     <span data-ttu-id="bdfa8-196">例如，以下命令会将可用性组 `MyAg` 的 `AutomatedBackupPreference` 属性设置为 `SecondaryOnly`。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-196">For example, the following command sets the `AutomatedBackupPreference` property on the availability group `MyAg` to `SecondaryOnly`.</span></span> <span data-ttu-id="bdfa8-197">此可用性组中的数据库自动备份将永远不会在主副本上发生，但将重定向到具有最高备份优先级设置的辅助副本。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-197">Automated backups of databases in this availability group will never occur on the primary replica, but will be redirected to the secondary replica with the highest backup priority setting.</span></span>  
  
    ```powershell
    Set-SqlAvailabilityGroup -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg `  
     -AutomatedBackupPreference SecondaryOnly  
    ```  
  
> [!NOTE]  
>  <span data-ttu-id="bdfa8-198">若要查看 cmdlet 的语法，请在 `Get-Help` PowerShell 环境中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-198">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="bdfa8-199">有关详细信息，请参阅 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-199">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
<span data-ttu-id="bdfa8-200">若要设置并使用 SQL Server PowerShell 提供程序，请参阅[SQL Server PowerShell 提供程序](../../../powershell/sql-server-powershell-provider.md)，并[SQL Server PowerShell 获取帮助](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-200">To set up and use the SQL Server PowerShell provider, see [SQL Server PowerShell Provider](../../../powershell/sql-server-powershell-provider.md) and [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>
  
##  <a name="follow-up-after-configuring-backup-on-secondary-replicas"></a><a name="FollowUp"></a><span data-ttu-id="bdfa8-201">跟进：配置辅助副本备份之后</span><span class="sxs-lookup"><span data-stu-id="bdfa8-201">Follow Up: After Configuring Backup on Secondary Replicas</span></span>  
 <span data-ttu-id="bdfa8-202">若要为某一给定可用性组考虑使用自动备份首选项，则对于承载备份优先级大于零 (>0) 的可用性副本的每个服务器实例，您需要为该可用性组中的数据库的备份作业编写脚本。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-202">To take the automated backup preference into account for a given availability group, on each server instance that hosts an availability replica whose backup priority is greater than zero (>0), you need to script backup jobs for the databases in the availability group.</span></span> <span data-ttu-id="bdfa8-203">若要确定当前副本是否为首选备份副本，请在备份脚本中使用 [sys.fn_hadr_backup_is_preferred_replica](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql) 函数。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-203">To determine whether the current replica is the preferred backup replica, use the [sys.fn_hadr_backup_is_preferred_replica](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql) function in your backup script.</span></span> <span data-ttu-id="bdfa8-204">如果当前服务器实例承载的可用性副本是用于备份的首选副本，则此函数将返回 1。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-204">If the availability replica that is hosted by the current server instance is the preferred replica for backups, this function returns 1.</span></span> <span data-ttu-id="bdfa8-205">否则，该函数返回 0。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-205">If not, the function returns 0.</span></span> <span data-ttu-id="bdfa8-206">通过对查询此函数的每个可用性副本运行简单的脚本，可以确定哪个副本应运行给定的备份作业。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-206">By running a simple script on each availability replica that queries this function, you can determine which replica should run a given backup job.</span></span> <span data-ttu-id="bdfa8-207">例如，备份作业脚本的典型代码段如下所示：</span><span class="sxs-lookup"><span data-stu-id="bdfa8-207">For example, a typical snippet of a backup-job script would look like:</span></span>  
  
```  
IF (NOT sys.fn_hadr_backup_is_preferred_replica(@DBNAME))  
BEGIN  
      Select 'This is not the preferred replica, exiting with success';  
      RETURN 0 - This is a normal, expected condition, so the script returns success  
END  
BACKUP DATABASE @DBNAME TO DISK=<disk>  
   WITH COPY_ONLY;  
```  
  
 <span data-ttu-id="bdfa8-208">通过使用此逻辑编写备份作业脚本，可以在同一个计划中安排对每个可用性副本运行的作业。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-208">Scripting a backup job with this logic enables you to schedule the job to run on every availability replica on the same schedule.</span></span> <span data-ttu-id="bdfa8-209">上述每个作业都应该查看相同数据以便确定哪一作业应该运行，因此，实际上只有一个计划作业将前进到备份阶段。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-209">Each of these jobs looks at the same data to determine which job should run, so only one of the scheduled job actually proceeds to the backup stage.</span></span>  <span data-ttu-id="bdfa8-210">在发生故障转移时，无需修改任何脚本或作业。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-210">In the event of a failover, none of the scripts or jobs needs to be modified.</span></span> <span data-ttu-id="bdfa8-211">此外，如果重新配置可用性组以便添加可用性副本，则管理备份作业只需复制或计划备份作业即可。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-211">Also, if you reconfigure an availability group to add an availability replica, managing the backup job requires simply copying or scheduling the backup job.</span></span> <span data-ttu-id="bdfa8-212">如果您删除可用性副本，只需从承载该副本的服务器实例上删除备份作业即可。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-212">If you remove an availability replica, simply delete the backup job from the server instance that hosted that replica.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="bdfa8-213">如果使用[维护计划向导](../../../relational-databases/maintenance-plans/use-the-maintenance-plan-wizard.md)创建某个给定的备份作业，该作业将自动包括调用和校验 **sys.fn_hadr_backup_is_preferred_replica** 函数的脚本逻辑。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-213">If you use the[Maintenance Plan Wizard](../../../relational-databases/maintenance-plans/use-the-maintenance-plan-wizard.md)to create a given backup job, the job will automatically include the scripting logic that calls and checks the **sys.fn_hadr_backup_is_preferred_replica** function.</span></span> <span data-ttu-id="bdfa8-214">但是，备份作业不会返回“这不是首选副本…”消息。请确保在托管可用性组的可用性副本的每个服务器实例上为每个可用性数据库创建作业。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-214">However, the backup job will not return the "This is not the preferred replica..." message.Be sure to create the job(s) for each availability database on every server instance that hosts an availability replica for the availability group.</span></span>  
  
##  <a name="to-obtain-information-about-backup-preference-settings"></a><a name="ForInfoAboutBuPref"></a><span data-ttu-id="bdfa8-215">获取有关备份首选项设置的信息</span><span class="sxs-lookup"><span data-stu-id="bdfa8-215">To Obtain Information About Backup Preference Settings</span></span>  
 <span data-ttu-id="bdfa8-216">以下内容对于获取辅助副本备份的相关信息很有用。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-216">The following are useful for obtaining information that is relevant for backup on secondary.</span></span>  
  
|<span data-ttu-id="bdfa8-217">查看</span><span class="sxs-lookup"><span data-stu-id="bdfa8-217">View</span></span>|<span data-ttu-id="bdfa8-218">信息</span><span class="sxs-lookup"><span data-stu-id="bdfa8-218">Information</span></span>|<span data-ttu-id="bdfa8-219">相关列</span><span class="sxs-lookup"><span data-stu-id="bdfa8-219">Relevant Columns</span></span>|  
|----------|-----------------|----------------------|  
|[<span data-ttu-id="bdfa8-220">sys.fn_hadr_backup_is_preferred_replica</span><span class="sxs-lookup"><span data-stu-id="bdfa8-220">sys.fn_hadr_backup_is_preferred_replica</span></span>](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql)|<span data-ttu-id="bdfa8-221">当前副本是否为首选备份副本？</span><span class="sxs-lookup"><span data-stu-id="bdfa8-221">Is the current replica the preferred backup replica?</span></span>|<span data-ttu-id="bdfa8-222">不适用。</span><span class="sxs-lookup"><span data-stu-id="bdfa8-222">Not applicable.</span></span>|  
|[<span data-ttu-id="bdfa8-223">sys.availability_groups</span><span class="sxs-lookup"><span data-stu-id="bdfa8-223">sys.availability_groups</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-groups-transact-sql)|<span data-ttu-id="bdfa8-224">自动备份首选项</span><span class="sxs-lookup"><span data-stu-id="bdfa8-224">Automated backup preference</span></span>|<span data-ttu-id="bdfa8-225">**automated_backup_preference**</span><span class="sxs-lookup"><span data-stu-id="bdfa8-225">**automated_backup_preference**</span></span><br /><br /> <span data-ttu-id="bdfa8-226">**automated_backup_preference_desc**</span><span class="sxs-lookup"><span data-stu-id="bdfa8-226">**automated_backup_preference_desc**</span></span>|  
|[<span data-ttu-id="bdfa8-227">sys.availability_replicas</span><span class="sxs-lookup"><span data-stu-id="bdfa8-227">sys.availability_replicas</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql)|<span data-ttu-id="bdfa8-228">给定可用性副本的备份优先级</span><span class="sxs-lookup"><span data-stu-id="bdfa8-228">Backup priority of a given availability replica</span></span>|<span data-ttu-id="bdfa8-229">**backup_priority**</span><span class="sxs-lookup"><span data-stu-id="bdfa8-229">**backup_priority**</span></span>|  
|[<span data-ttu-id="bdfa8-230">sys.dm_hadr_availability_replica_states</span><span class="sxs-lookup"><span data-stu-id="bdfa8-230">sys.dm_hadr_availability_replica_states</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-states-transact-sql)|<span data-ttu-id="bdfa8-231">是否为服务器实例的本地副本？</span><span class="sxs-lookup"><span data-stu-id="bdfa8-231">Is replica local to the server instance?</span></span><br /><br /> <span data-ttu-id="bdfa8-232">当前角色</span><span class="sxs-lookup"><span data-stu-id="bdfa8-232">Current role</span></span><br /><br /> <span data-ttu-id="bdfa8-233">操作状态</span><span class="sxs-lookup"><span data-stu-id="bdfa8-233">Operational state</span></span><br /><br /> <span data-ttu-id="bdfa8-234">连接状态</span><span class="sxs-lookup"><span data-stu-id="bdfa8-234">Connected state</span></span><br /><br /> <span data-ttu-id="bdfa8-235">可用性副本的同步运行状况</span><span class="sxs-lookup"><span data-stu-id="bdfa8-235">Synchronization health of an availability replica</span></span>|<span data-ttu-id="bdfa8-236">**is_local**</span><span class="sxs-lookup"><span data-stu-id="bdfa8-236">**is_local**</span></span><br /><br /> <span data-ttu-id="bdfa8-237">**role**、 **role_desc**</span><span class="sxs-lookup"><span data-stu-id="bdfa8-237">**role**, **role_desc**</span></span><br /><br /> <span data-ttu-id="bdfa8-238">**operational_state**、 **operational_state_desc**</span><span class="sxs-lookup"><span data-stu-id="bdfa8-238">**operational_state**, **operational_state_desc**</span></span><br /><br /> <span data-ttu-id="bdfa8-239">**connected_state**、 **connected_state_desc**</span><span class="sxs-lookup"><span data-stu-id="bdfa8-239">**connected_state**, **connected_state_desc**</span></span><br /><br /> <span data-ttu-id="bdfa8-240">**synchronization_health**、 **synchronization_health_desc**</span><span class="sxs-lookup"><span data-stu-id="bdfa8-240">**synchronization_health**, **synchronization_health_desc**</span></span>|  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="bdfa8-241">相关内容</span><span class="sxs-lookup"><span data-stu-id="bdfa8-241">Related Content</span></span>  
  
-   [<span data-ttu-id="bdfa8-242">用于高可用性和灾难恢复的 Microsoft SQL Server AlwaysOn 解决方案指南</span><span class="sxs-lookup"><span data-stu-id="bdfa8-242">Microsoft SQL Server AlwaysOn Solutions Guide for High Availability and Disaster Recovery</span></span>](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
-   [<span data-ttu-id="bdfa8-243">SQL Server AlwaysOn 团队博客：SQL Server AlwaysOn 官方团队博客</span><span class="sxs-lookup"><span data-stu-id="bdfa8-243">SQL Server AlwaysOn Team Blog: The official SQL Server AlwaysOn Team Blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
## <a name="see-also"></a><span data-ttu-id="bdfa8-244">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bdfa8-244">See Also</span></span>  
 <span data-ttu-id="bdfa8-245">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="bdfa8-245">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="bdfa8-246">活动辅助副本：辅助副本备份（AlwaysOn 可用性组）</span><span class="sxs-lookup"><span data-stu-id="bdfa8-246">Active Secondaries: Backup on Secondary Replicas (AlwaysOn Availability Groups)</span></span>](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md) 
