---
title: 将次要副本添加到可用性组 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], configuring
ms.assetid: 6669dcce-85f9-495f-aadf-7f62cff4a9da
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 498103a781641c72e166c6b11663f5248ae5ccfc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578454"
---
# <a name="add-a-secondary-replica-to-an-availability-group-sql-server"></a><span data-ttu-id="e9f01-102">将辅助副本添加到可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e9f01-102">Add a Secondary Replica to an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="e9f01-103">本主题描述如何使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../../includes/tsql-md.md)]或 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]中的 PowerShell 将辅助副本添加到现有的 AlwaysOn 可用性组。</span><span class="sxs-lookup"><span data-stu-id="e9f01-103">This topic describes how to add a secondary replica to an existing AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
-   <span data-ttu-id="e9f01-104">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="e9f01-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="e9f01-105">先决条件和限制</span><span class="sxs-lookup"><span data-stu-id="e9f01-105">Prerequisites and Restrictions</span></span>](#PrerequisitesRestrictions)  
  
     [<span data-ttu-id="e9f01-106">安全性</span><span class="sxs-lookup"><span data-stu-id="e9f01-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="e9f01-107">**要添加副本，请使用：**</span><span class="sxs-lookup"><span data-stu-id="e9f01-107">**To add a replica, using:**</span></span>  
  
     [<span data-ttu-id="e9f01-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e9f01-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="e9f01-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e9f01-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="e9f01-110">PowerShell</span><span class="sxs-lookup"><span data-stu-id="e9f01-110">PowerShell</span></span>](#PowerShellProcedure)  
  
-   <span data-ttu-id="e9f01-111">**跟进：**  [在添加次要副本之后](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="e9f01-111">**Follow Up:**  [After Adding a Secondary Replica](#FollowUp)</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="e9f01-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="e9f01-112">Before You Begin</span></span>  
 <span data-ttu-id="e9f01-113">我们强烈建议您首先阅读此部分，再尝试创建您的第一个可用性组。</span><span class="sxs-lookup"><span data-stu-id="e9f01-113">We strongly recommend that you read this section before attempting to create your first availability group.</span></span>  
  
##  <a name="prerequisites-and-restrictions"></a><a name="PrerequisitesRestrictions"></a> <span data-ttu-id="e9f01-114">先决条件和限制</span><span class="sxs-lookup"><span data-stu-id="e9f01-114">Prerequisites and Restrictions</span></span>  
  
-   <span data-ttu-id="e9f01-115">您必须连接到承载主副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="e9f01-115">You must be connected to the server instance that hosts the primary replica.</span></span>  
  
 <span data-ttu-id="e9f01-116">有关详细信息，请参阅[针对 AlwaysOn 可用性组的先决条件、限制和建议 (SQL Server)](prereqs-restrictions-recommendations-always-on-availability.md)。</span><span class="sxs-lookup"><span data-stu-id="e9f01-116">For more information, see [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
##  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e9f01-117">Security</span><span class="sxs-lookup"><span data-stu-id="e9f01-117">Security</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e9f01-118">权限</span><span class="sxs-lookup"><span data-stu-id="e9f01-118">Permissions</span></span>  
 <span data-ttu-id="e9f01-119">对可用性组要求 ALTER AVAILABILITY GROUP 权限、CONTROL AVAILABILITY GROUP 权限、ALTER ANY AVAILABILITY GROUP 权限或 CONTROL SERVER 权限。</span><span class="sxs-lookup"><span data-stu-id="e9f01-119">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e9f01-120">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e9f01-120">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="e9f01-121">**添加副本**</span><span class="sxs-lookup"><span data-stu-id="e9f01-121">**To add a replica**</span></span>  
  
1.  <span data-ttu-id="e9f01-122">在对象资源管理器中，连接到承载主副本的服务器实例，然后展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="e9f01-122">In Object Explorer, connect to the server instance that hosts the primary replica, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="e9f01-123">依次展开 **“AlwaysOn 高可用性”** 节点和 **“可用性组”** 节点。</span><span class="sxs-lookup"><span data-stu-id="e9f01-123">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="e9f01-124">右键单击可用性组，然后选择下列命令之一：</span><span class="sxs-lookup"><span data-stu-id="e9f01-124">Right-click the availability group, and select one of the following commands:</span></span>  
  
    -   <span data-ttu-id="e9f01-125">选择 **“添加副本”** 命令可启动“将副本添加到可用性组向导”。</span><span class="sxs-lookup"><span data-stu-id="e9f01-125">Select the **Add Replica** command to launch the Add Replica to Availability Group Wizard.</span></span> <span data-ttu-id="e9f01-126">有关详细信息，请参阅[使用“将副本添加到可用性组向导”(SQL Server Management Studio)](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="e9f01-126">For more information, see [Use the Add Replica to Availability Group Wizard &#40;SQL Server Management Studio&#41;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md).</span></span>  
  
    -   <span data-ttu-id="e9f01-127">或者，选择 **“属性”** 命令以便打开 **“可用性组属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="e9f01-127">Alternatively, select the **Properties** command to open the **Availability Group Properties** dialog box.</span></span> <span data-ttu-id="e9f01-128">用于在此对话框中添加副本的步骤如下所示：</span><span class="sxs-lookup"><span data-stu-id="e9f01-128">The steps for adding a replica in this dialog box are as follows:</span></span>  
  
        1.  <span data-ttu-id="e9f01-129">在对话框的 **“可用性副本”** 窗格中，单击 **“添加”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="e9f01-129">In the **Availability Replicas** pane of the dialog box, click the **Add** button.</span></span> <span data-ttu-id="e9f01-130">这将创建并选择已选中了空白“服务器实例”字段的副本项。</span><span class="sxs-lookup"><span data-stu-id="e9f01-130">This creates and selects a replica entry in which the blank Server Instance field is selected.</span></span>  
  
        2.  <span data-ttu-id="e9f01-131">输入符合用于承载可用性副本的先决条件的服务器实例的名称。</span><span class="sxs-lookup"><span data-stu-id="e9f01-131">Enter the name of a server instance that meets the prerequisites for hosting an availability replica.</span></span>  
  
         <span data-ttu-id="e9f01-132">若要添加其他副本，请重复前面的步骤。</span><span class="sxs-lookup"><span data-stu-id="e9f01-132">To add an additional replicas, repeat the preceding steps.</span></span> <span data-ttu-id="e9f01-133">当您指定完副本后，单击 **“确定”** 以完成此操作。</span><span class="sxs-lookup"><span data-stu-id="e9f01-133">When you are done specifying replicas, click **OK** to complete the operation.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="e9f01-134">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e9f01-134">Using Transact-SQL</span></span>  
 <span data-ttu-id="e9f01-135">**添加副本**</span><span class="sxs-lookup"><span data-stu-id="e9f01-135">**To add a replica**</span></span>  
  
1.  <span data-ttu-id="e9f01-136">连接到承载主副本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="e9f01-136">Connect to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="e9f01-137">通过使用 ALTER AVAILABILITY GROUP 语句的 ADD REPLICA ON 子句将新辅助副本添加到可用性组。</span><span class="sxs-lookup"><span data-stu-id="e9f01-137">Add the new secondary replica to the availability group by using the ADD REPLICA ON clause of the ALTER AVAILABILITY GROUP statement.</span></span> <span data-ttu-id="e9f01-138">在 ADD REPLICA ON 子句中，ENDPOINT_URL、AVAILABILITY_MODE 和 FAILOVER_MODE 选项是必需的。</span><span class="sxs-lookup"><span data-stu-id="e9f01-138">The ENDPOINT_URL, AVAILABILITY_MODE, and FAILOVER_MODE options are required in an ADD REPLICA ON clause.</span></span> <span data-ttu-id="e9f01-139">其他副本选项（BACKUP_PRIORITY、SECONDARY_ROLE、PRIMARY_ROLE 和 SESSION_TIMEOUT）是可选的。</span><span class="sxs-lookup"><span data-stu-id="e9f01-139">The other replica options- BACKUP_PRIORITY, SECONDARY_ROLE, PRIMARY_ROLE, and SESSION_TIMEOUT-are optional.</span></span> <span data-ttu-id="e9f01-140">有关详细信息，请参阅 [ALTER AVAILABILITY GROUP (Transact-SQL)](/sql/t-sql/statements/alter-availability-group-transact-sql)中的 PowerShell 将次要副本添加到现有的 AlwaysOn 可用性组。</span><span class="sxs-lookup"><span data-stu-id="e9f01-140">For more information, see [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql).</span></span>  
  
     <span data-ttu-id="e9f01-141">例如，下面的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句将在 `MyAG` 承载的默认服务器实例（其端点 URL 为 `COMPUTER04`）上创建名为 `TCP://COMPUTER04.Adventure-Works.com:5022'`的可用性组的新副本。</span><span class="sxs-lookup"><span data-stu-id="e9f01-141">For example, the following [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement creates a new replica to an availability group named `MyAG` on the default server instance hosted by `COMPUTER04`, whose endpoint URL is `TCP://COMPUTER04.Adventure-Works.com:5022'`.</span></span> <span data-ttu-id="e9f01-142">此副本支持手动故障转移和异步提交可用性模式。</span><span class="sxs-lookup"><span data-stu-id="e9f01-142">This replica supports manual failover and asynchronous-commit availability mode.</span></span>  
  
    ```sql
    ALTER AVAILABILITY GROUP MyAG ADD REPLICA ON 'COMPUTER04'   
       WITH (  
             ENDPOINT_URL = 'TCP://COMPUTER04.Adventure-Works.com:5022',  
             AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,  
             FAILOVER_MODE = MANUAL  
             );  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="e9f01-143">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e9f01-143">Using PowerShell</span></span>  
 <span data-ttu-id="e9f01-144">**添加副本**</span><span class="sxs-lookup"><span data-stu-id="e9f01-144">**To add a replica**</span></span>  
  
1.  <span data-ttu-id="e9f01-145">将目录 (`cd`) 更改为承载主副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="e9f01-145">Change directory (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="e9f01-146">使用 **New-SqlAvailabilityReplica** cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e9f01-146">Use the **New-SqlAvailabilityReplica** cmdlet.</span></span>  
  
     <span data-ttu-id="e9f01-147">例如，下面的命令将可用性副本添加到名为 `MyAg`的现有可用性组中。</span><span class="sxs-lookup"><span data-stu-id="e9f01-147">For example, the following command adds an availability replica to an existing availability group named `MyAg`.</span></span> <span data-ttu-id="e9f01-148">此副本支持手动故障转移和异步提交可用性模式。</span><span class="sxs-lookup"><span data-stu-id="e9f01-148">This replica supports manual failover and asynchronous-commit availability mode.</span></span> <span data-ttu-id="e9f01-149">在辅助角色中，此副本将支持读访问连接，使您可以将只读处理转移到此副本。</span><span class="sxs-lookup"><span data-stu-id="e9f01-149">In the secondary role, this replica will support read access connections, allowing you to offload read-only processing to this replica.</span></span>  
  
    ```powershell
    $agPath = "SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg"  
    $endpointURL = "TCP://PrimaryServerName.domain.com:5022"  
    $failoverMode = "Manual"  
    $availabilityMode = "AsynchronousCommit"  
    $secondaryReadMode = "AllowAllConnections"  
  
    New-SqlAvailabilityReplica -Name SecondaryServer\Instance `   
    -EndpointUrl $endpointURL `   
    -FailoverMode $failoverMode `   
    -AvailabilityMode $availabilityMode `   
    -ConnectionModeInSecondaryRole $secondaryReadMode `   
    -Path $agPath  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="e9f01-150">若要查看 cmdlet 的语法，请在 `Get-Help` PowerShell 环境中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e9f01-150">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="e9f01-151">有关详细信息，请参阅 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="e9f01-151">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="e9f01-152">**设置和使用 SQL Server PowerShell 提供程序**</span><span class="sxs-lookup"><span data-stu-id="e9f01-152">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="e9f01-153">SQL Server PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="e9f01-153">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="follow-up-after-adding-a-secondary-replica"></a><a name="FollowUp"></a> <span data-ttu-id="e9f01-154">跟进：在添加辅助副本之后</span><span class="sxs-lookup"><span data-stu-id="e9f01-154">Follow Up: After Adding a Secondary Replica</span></span>  
 <span data-ttu-id="e9f01-155">若要为现有可用性组添加副本，您必须执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="e9f01-155">To add a replica for an existing availability group, you must perform the following steps:</span></span>  
  
1.  <span data-ttu-id="e9f01-156">连接到将要承载新辅助副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="e9f01-156">Connect to the server instance that is going to host the new secondary replica.</span></span>  
  
2.  <span data-ttu-id="e9f01-157">将新的辅助副本联接到可用性组。</span><span class="sxs-lookup"><span data-stu-id="e9f01-157">Join the new secondary replica to the availability group.</span></span> <span data-ttu-id="e9f01-158">有关详细信息，请参阅 [将辅助副本联接到可用性组 (SQL Server)](join-a-secondary-replica-to-an-availability-group-sql-server.md)或 PowerShell 将辅助数据库联接到 Always On 可用性组。</span><span class="sxs-lookup"><span data-stu-id="e9f01-158">For more information, see [Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md).</span></span>  
  
3.  <span data-ttu-id="e9f01-159">对于可用性组中的每个数据库，在承载辅助副本的服务器实例上创建辅助数据库。</span><span class="sxs-lookup"><span data-stu-id="e9f01-159">For each database in the availability group, create a secondary database on the server instance that is hosting the secondary replica.</span></span> <span data-ttu-id="e9f01-160">有关详细信息，请参阅 [为可用性组手动准备辅助数据库 (SQL Server)](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)或 PowerShell 将辅助数据库联接到 Always On 可用性组。</span><span class="sxs-lookup"><span data-stu-id="e9f01-160">For more information, see [Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).</span></span>  
  
4.  <span data-ttu-id="e9f01-161">将每个新的辅助数据库联接到可用性组。</span><span class="sxs-lookup"><span data-stu-id="e9f01-161">Join each of the new secondary databases to the availability group.</span></span> <span data-ttu-id="e9f01-162">有关详细信息，请参阅 [将辅助数据库联接到可用性组 (SQL Server)](join-a-secondary-database-to-an-availability-group-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="e9f01-162">For more information, see [Join a Secondary Database to an Availability Group &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="e9f01-163">相关任务</span><span class="sxs-lookup"><span data-stu-id="e9f01-163">Related Tasks</span></span>  
 <span data-ttu-id="e9f01-164">**管理可用性副本**</span><span class="sxs-lookup"><span data-stu-id="e9f01-164">**To manage an availability replica**</span></span>  
  
-   [<span data-ttu-id="e9f01-165">将辅助副本联接到可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e9f01-165">Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="e9f01-166">将次要副本从可用性组删除 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e9f01-166">Remove a Secondary Replica from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-replica-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="e9f01-167">配置对可用性副本的只读访问 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e9f01-167">Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;</span></span>](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="e9f01-168">更改可用性副本的可用性模式 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e9f01-168">Change the Availability Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-availability-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="e9f01-169">更改可用性副本的故障转移模式 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e9f01-169">Change the Failover Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-failover-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="e9f01-170">更改可用性副本的会话超时期限 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e9f01-170">Change the Session-Timeout Period for an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="e9f01-171">更改可用性副本的会话超时期限 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e9f01-171">Change the Session-Timeout Period for an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="e9f01-172">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e9f01-172">See Also</span></span>  
 <span data-ttu-id="e9f01-173">[ALTER AVAILABILITY GROUP (Transact-SQL)](/sql/t-sql/statements/alter-availability-group-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e9f01-173">[ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql) </span></span>  
 <span data-ttu-id="e9f01-174">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e9f01-174">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="e9f01-175">[创建和配置可用性组 (SQL Server)](creation-and-configuration-of-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e9f01-175">[Creation and Configuration of Availability Groups &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="e9f01-176">[使用 AlwaysOn 仪表板 &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="e9f01-176">[Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="e9f01-177">监视可用性组 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e9f01-177">Monitor Availability Groups &#40;Transact-SQL&#41;</span></span>](monitor-availability-groups-transact-sql.md)  
  
  
