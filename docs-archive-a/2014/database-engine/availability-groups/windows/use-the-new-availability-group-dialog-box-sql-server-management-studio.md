---
title: 使用“新建可用性组”对话框 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], creating
ms.assetid: 1b0a6421-fbd4-4bb4-87ca-657f4782c433
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 811710051089dfeb402e59bf1b7f45d05c84d925
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580377"
---
# <a name="use-the-new-availability-group-dialog-box-sql-server-management-studio"></a><span data-ttu-id="ed149-102">使用“新建可用性组”对话框 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="ed149-102">Use the New Availability Group Dialog Box (SQL Server Management Studio)</span></span>
  <span data-ttu-id="ed149-103">本主题包含有关如何使用 **的** “新建可用性组” [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 对话框在为 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 启用的 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]实例上创建 AlwaysOn 可用性组的信息。</span><span class="sxs-lookup"><span data-stu-id="ed149-103">This topic contains information about how to use the **New Availability Group** dialog box of [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] to create an AlwaysOn availability group on instances of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] that are enabled for [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].</span></span> <span data-ttu-id="ed149-104">“可用性组”  定义一组用户数据库，这些用户数据库将以支持故障转移的单个单元和一组故障转移伙伴（称作“可用性副本” ）的形式进行故障转移。</span><span class="sxs-lookup"><span data-stu-id="ed149-104">An *availability group* defines a set of user databases that will fail over as a single unit and a set of failover partners, known as *availability replicas*, that support failover.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ed149-105">有关可用性组的简介，请参阅 [AlwaysOn 可用性组概述 (SQL Server)](overview-of-always-on-availability-groups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ed149-105">For an introduction to availability groups, see [Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).</span></span>  
  

> [!NOTE]  
>  <span data-ttu-id="ed149-106">有关创建可用性组的替代方法的信息，请参阅本主题后面的 [相关任务](#RelatedTasks)。</span><span class="sxs-lookup"><span data-stu-id="ed149-106">For information about alternative ways to create an availability group, see [Related Tasks](#RelatedTasks), later in this topic.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ed149-107">开始之前</span><span class="sxs-lookup"><span data-stu-id="ed149-107">Before You Begin</span></span>  
 <span data-ttu-id="ed149-108">我们强烈建议您首先阅读此部分，再尝试创建您的第一个可用性组。</span><span class="sxs-lookup"><span data-stu-id="ed149-108">We strongly recommend that you read this section before attempting to create your first availability group.</span></span>  
  
###  <a name="prerequisites"></a><a name="PrerequisitesRestrictions"></a><span data-ttu-id="ed149-109">先决条件</span><span class="sxs-lookup"><span data-stu-id="ed149-109">Prerequisites</span></span>  
  
-   <span data-ttu-id="ed149-110">创建可用性组之前，请先验证承载可用性副本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例位于同一 WSFC 故障转移群集内的不同 Windows Server 故障转移群集 (WSFC) 节点上。</span><span class="sxs-lookup"><span data-stu-id="ed149-110">Before creating an availability group, verify that the instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that host availability replicas reside on different Windows Server Failover Clustering (WSFC) node within the same WSFC failover cluster.</span></span> <span data-ttu-id="ed149-111">此外，还要验证是否为 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 启用了每个服务器实例以及是否满足其他 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 先决条件。</span><span class="sxs-lookup"><span data-stu-id="ed149-111">Also, verify that each of the server instance is enabled for [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] and meets all other [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] prerequisites.</span></span> <span data-ttu-id="ed149-112">有关详细信息，我们强烈建议你参阅[针对 AlwaysOn 可用性组的先决条件、限制和建议 (SQL Server)](prereqs-restrictions-recommendations-always-on-availability.md)。</span><span class="sxs-lookup"><span data-stu-id="ed149-112">For more information, we strongly recommend that you read [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
-   <span data-ttu-id="ed149-113">在创建可用性组之前，请确保将承载可用性副本的每个服务器实例拥有一个功能正常的数据库镜像端点。</span><span class="sxs-lookup"><span data-stu-id="ed149-113">Before you create an availability group, ensure that every server instance that will host an availability replica has a fully functioning database mirroring endpoint.</span></span> <span data-ttu-id="ed149-114">有关详细信息，请参阅 [数据库镜像终结点 (SQL Server)](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ed149-114">For more information, see [The Database Mirroring Endpoint &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md).</span></span>  
  
-   <span data-ttu-id="ed149-115">为了使用 **“新建可用性组”** 对话框，您需要知道将承载可用性副本的服务器实例的名称。</span><span class="sxs-lookup"><span data-stu-id="ed149-115">To use the **New Availability Group** dialog box, you need to know the names of the server instances that will host availability replicas.</span></span> <span data-ttu-id="ed149-116">此外，需要知道要添加到新可用性组的任何数据库的名称，并确保这些数据库满足[针对 AlwaysOn 可用性组的先决条件、限制和建议 (SQL Server)](prereqs-restrictions-recommendations-always-on-availability.md) 中所述的可用性数据库先决条件和限制。</span><span class="sxs-lookup"><span data-stu-id="ed149-116">Also, you need know the names of any databases that you intend to add to your new availability group, and you need to ensure that these databases meet the availability database prerequisites and restrictions described in [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span> <span data-ttu-id="ed149-117">如果输入无效值，新的可用性组将无法工作。</span><span class="sxs-lookup"><span data-stu-id="ed149-117">If you enter invalid values, the new availability group will not work.</span></span>  
  
###  <a name="limitations"></a><a name="Limitations"></a> <span data-ttu-id="ed149-118">限制</span><span class="sxs-lookup"><span data-stu-id="ed149-118">Limitations</span></span>  
 <span data-ttu-id="ed149-119">**“新建可用性组”** 对话框不：</span><span class="sxs-lookup"><span data-stu-id="ed149-119">The **New Availability Group** dialog box does not:</span></span>  
  
-   <span data-ttu-id="ed149-120">创建可用性组侦听器。</span><span class="sxs-lookup"><span data-stu-id="ed149-120">Create an availability group listener.</span></span>  
  
-   <span data-ttu-id="ed149-121">将辅助副本联接到可用性组。</span><span class="sxs-lookup"><span data-stu-id="ed149-121">Join secondary replicas to the availability group.</span></span>  
  
-   <span data-ttu-id="ed149-122">执行初始数据同步。</span><span class="sxs-lookup"><span data-stu-id="ed149-122">Perform initial data synchronization.</span></span>  
  
 <span data-ttu-id="ed149-123">有关这些配置任务的信息，请参阅本话题后面部分的[跟进：在创建可用性组之后](#FollowUp)。</span><span class="sxs-lookup"><span data-stu-id="ed149-123">For information about these configuration tasks, see [Follow Up: After Creating an Availability Group](#FollowUp), later in this topic.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ed149-124">Security</span><span class="sxs-lookup"><span data-stu-id="ed149-124">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ed149-125">权限</span><span class="sxs-lookup"><span data-stu-id="ed149-125">Permissions</span></span>  
 <span data-ttu-id="ed149-126">需要 **sysadmin** 固定服务器角色的成员资格，以及 CREATE AVAILABILITY GROUP 服务器权限、ALTER ANY AVAILABILITY GROUP 权限或 CONTROL SERVER 权限。</span><span class="sxs-lookup"><span data-stu-id="ed149-126">Requires membership in the **sysadmin** fixed server role and either CREATE AVAILABILITY GROUP server permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-the-new-availability-group-dialog-box-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ed149-127">使用“新建可用性组”对话框 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="ed149-127">Using the New Availability Group Dialog Box (SQL Server Management Studio)</span></span>  
 <span data-ttu-id="ed149-128">**创建可用性组**</span><span class="sxs-lookup"><span data-stu-id="ed149-128">**To create an availability group**</span></span>  
  
1.  <span data-ttu-id="ed149-129">在对象资源管理器中，连接到承载主副本的服务器实例，然后单击该服务器名称。</span><span class="sxs-lookup"><span data-stu-id="ed149-129">In Object Explorer, connect to the server instance that hosts the primary replica, and click the server name.</span></span>  
  
2.  <span data-ttu-id="ed149-130">展开 **“AlwaysOn 高可用性”** 节点。</span><span class="sxs-lookup"><span data-stu-id="ed149-130">Expand the **AlwaysOn High Availability** node.</span></span>  
  
3.  <span data-ttu-id="ed149-131">右键单击“可用性组”节点，然后选择“新建可用性组”。</span><span class="sxs-lookup"><span data-stu-id="ed149-131">Right-click the **Availability Groups** node, and select the **New Availability Group** command.</span></span>  
  
4.  <span data-ttu-id="ed149-132">此命令将打开 **“新建可用性组”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="ed149-132">This command opens up the **New Availability Group** dialog box.</span></span>  
  
5.  <span data-ttu-id="ed149-133">使用 **“常规”** 页上的 **“可用性组名称”** 字段，输入新的可用性组的名称。</span><span class="sxs-lookup"><span data-stu-id="ed149-133">On the **General** page, use the **Availability group name** field to enter a name for the new availability group.</span></span> <span data-ttu-id="ed149-134">此名称必须是有效的 SQL Server 标识符，该标识符在 WSFC 群集的所有可用性组中保持唯一。</span><span class="sxs-lookup"><span data-stu-id="ed149-134">This name must be a valid SQL Server identifier that is unique across all availability groups in the WSFC cluster.</span></span> <span data-ttu-id="ed149-135">可用性组名称的最大长度为 128 个字符。</span><span class="sxs-lookup"><span data-stu-id="ed149-135">The maximum length for an availability group name is 128 characters.</span></span>  
  
6.  <span data-ttu-id="ed149-136">在 **“可用性数据库”** 网格中，单击 **“添加”** ，然后输入希望属于此可用性组的本地数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="ed149-136">In the **Availability Databases** grid, click **Add** and enter the name of a local database that you want to belong to this availability group.</span></span> <span data-ttu-id="ed149-137">对要添加的每个数据库重复此操作。</span><span class="sxs-lookup"><span data-stu-id="ed149-137">Repeat this for every database to be added.</span></span> <span data-ttu-id="ed149-138">单击 **“确定”** 后，该对话框将验证指定的数据库是否满足属于可用性组的先决条件。</span><span class="sxs-lookup"><span data-stu-id="ed149-138">When you click **OK**, the dialog will verify whether your specified database meet the prerequisites for belonging to an availability group.</span></span> <span data-ttu-id="ed149-139">有关先决条件的详细信息，请参阅[针对 AlwaysOn 可用性组的先决条件、限制和建议 (SQL Server)](prereqs-restrictions-recommendations-always-on-availability.md)。</span><span class="sxs-lookup"><span data-stu-id="ed149-139">For information about these prerequisites, see [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
7.  <span data-ttu-id="ed149-140">在 **“可用性数据库”** 网格中，单击 **“添加”** ，然后输入要承载辅助副本的服务器实例名称。</span><span class="sxs-lookup"><span data-stu-id="ed149-140">In the **Availability Databases** grid, click **Add** and enter the name of a server instance to host a secondary replica.</span></span> <span data-ttu-id="ed149-141">该对话框将不尝试连接到这些实例。</span><span class="sxs-lookup"><span data-stu-id="ed149-141">The dialog will not attempt to connect to these instances.</span></span> <span data-ttu-id="ed149-142">如果指定不正确的服务器名称，将添加辅助副本，但是您将无法连接到该副本。</span><span class="sxs-lookup"><span data-stu-id="ed149-142">If you specify an incorrect server name, a secondary replica will be added but you will be unable to connect to that replica.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="ed149-143">如果添加了副本但是无法连接到主机服务器实例，可以删除该副本并添加新副本。</span><span class="sxs-lookup"><span data-stu-id="ed149-143">If you have added a replica and cannot connect to the host server instance, you can remove the replica and add a new one.</span></span> <span data-ttu-id="ed149-144">有关详细信息，请参阅[将辅助副本从可用性组删除 (SQL Server)](remove-a-secondary-replica-from-an-availability-group-sql-server.md) 和[将辅助副本添加到可用性组 (SQL Server)](add-a-secondary-replica-to-an-availability-group-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ed149-144">For more information, see [Remove a Secondary Replica from an Availability Group &#40;SQL Server&#41;](remove-a-secondary-replica-from-an-availability-group-sql-server.md) and [Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md).</span></span>  
  
8.  <span data-ttu-id="ed149-145">在对话框的 **“选择页”** 窗格中，单击 **“备份首选项”** 。</span><span class="sxs-lookup"><span data-stu-id="ed149-145">On the **Select a page** pane of the dialog box, click **Backup Preferences**.</span></span> <span data-ttu-id="ed149-146">然后，在 **“备份首选项”** 页上，指定应基于副本角色执行备份的位置并将备份优先级分配给将承载此可用性组的可用性副本的每个服务器实例。</span><span class="sxs-lookup"><span data-stu-id="ed149-146">Then, on the **Backup Preferences** page, specify where backups should occur based on replica role and assign backup priorities to each server instances that will host an availability replica for this availability group.</span></span> <span data-ttu-id="ed149-147">有关详细信息，请参阅[可用性组属性面板：新建可用性组（“备份首选项”页）](availability-group-properties-new-availability-group-backup-preferences-page.md)。</span><span class="sxs-lookup"><span data-stu-id="ed149-147">For more information, see [Availability Group Properties: New Availability Group &#40;Backup Preferences Page&#41;](availability-group-properties-new-availability-group-backup-preferences-page.md).</span></span>  
  
9. <span data-ttu-id="ed149-148">若要创建可用性组，请单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="ed149-148">To create the availability group, click **OK**.</span></span> <span data-ttu-id="ed149-149">这将导致对话框验证指定的数据库是否满足先决条件的要求。</span><span class="sxs-lookup"><span data-stu-id="ed149-149">This causes the dialog to verify whether that specified databases meet the prerequisites.</span></span>  
  
     <span data-ttu-id="ed149-150">要退出对话框而不创建可用性组，请单击 **“取消”** 。</span><span class="sxs-lookup"><span data-stu-id="ed149-150">To exit the dialog box without creating the availability group, click **Cancel**.</span></span>  
  
##  <a name="follow-up-after-using-the-new-availability-group-dialog-box-to-create-an-availability-group"></a><a name="FollowUp"></a> <span data-ttu-id="ed149-151">跟进：在使用“新建可用性组”对话框创建可用性组之后</span><span class="sxs-lookup"><span data-stu-id="ed149-151">Follow Up: After Using the New Availability Group Dialog Box to Create an Availability Group</span></span>  
  
-   <span data-ttu-id="ed149-152">您将需要依次连接到承载可用性组的辅助副本的每个服务器实例并完成以下步骤：</span><span class="sxs-lookup"><span data-stu-id="ed149-152">You will need to connect, in turn, to each server instance that is hosting a secondary replica for the availability group and complete the following steps:</span></span>  
  
    1.  <span data-ttu-id="ed149-153">将辅助副本联接到该可用性组。</span><span class="sxs-lookup"><span data-stu-id="ed149-153">Join the secondary replica to the availability group.</span></span> <span data-ttu-id="ed149-154">有关详细信息，请参阅 [将辅助副本联接到可用性组 (SQL Server)](join-a-secondary-replica-to-an-availability-group-sql-server.md)或 PowerShell 将辅助数据库联接到 Always On 可用性组。</span><span class="sxs-lookup"><span data-stu-id="ed149-154">For more information, see [Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md).</span></span>  
  
    2.  <span data-ttu-id="ed149-155">还原每个主数据库及其事务日志的当前副本（使用 RESTORE WITH NORECOVERY）。</span><span class="sxs-lookup"><span data-stu-id="ed149-155">Restore current backups of each primary database and its transaction log (using RESTORE WITH NORECOVERY).</span></span> <span data-ttu-id="ed149-156">有关详细信息，请参阅 [为可用性组手动准备辅助数据库 (SQL Server)](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)或 PowerShell 将辅助数据库联接到 Always On 可用性组。</span><span class="sxs-lookup"><span data-stu-id="ed149-156">For more information, see [Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).</span></span>  
  
    3.  <span data-ttu-id="ed149-157">立即将每个新准备的辅助数据库加入可用性组。</span><span class="sxs-lookup"><span data-stu-id="ed149-157">Immediately join each newly prepared secondary database to the availability group.</span></span> <span data-ttu-id="ed149-158">有关详细信息，请参阅 [将辅助数据库联接到可用性组 (SQL Server)](join-a-secondary-database-to-an-availability-group-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ed149-158">For more information, see [Join a Secondary Database to an Availability Group &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md).</span></span>  
  
-   <span data-ttu-id="ed149-159">我们建议您为新的可用性组创建可用性组侦听器。</span><span class="sxs-lookup"><span data-stu-id="ed149-159">We recommend that you create an availability group listener for the new availability group.</span></span> <span data-ttu-id="ed149-160">这要求您连接到承载当前主副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="ed149-160">This requires that you be connected to the server instance that hosts the current primary replica.</span></span> <span data-ttu-id="ed149-161">有关详细信息，请参阅 [创建或配置可用性组侦听程序 (SQL Server)](create-or-configure-an-availability-group-listener-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ed149-161">For more information, see [Create or Configure an Availability Group Listener &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="ed149-162">相关任务</span><span class="sxs-lookup"><span data-stu-id="ed149-162">Related Tasks</span></span>  
 <span data-ttu-id="ed149-163">**配置可用性组和副本属性**</span><span class="sxs-lookup"><span data-stu-id="ed149-163">**To configure availability group and replica properties**</span></span>  
  
-   [<span data-ttu-id="ed149-164">更改可用性副本的可用性模式 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ed149-164">Change the Availability Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-availability-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="ed149-165">更改可用性副本的故障转移模式 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ed149-165">Change the Failover Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-failover-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="ed149-166">创建或配置可用性组侦听程序 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ed149-166">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="ed149-167">配置灵活的故障转移策略以控制自动故障转移的条件（AlwaysOn 可用性组）</span><span class="sxs-lookup"><span data-stu-id="ed149-167">Configure the Flexible Failover Policy to Control Conditions for Automatic Failover (AlwaysOn Availability Groups)</span></span>](configure-flexible-automatic-failover-policy.md)  
  
-   [<span data-ttu-id="ed149-168">在添加或修改可用性副本时指定终结点 URL (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ed149-168">Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;</span></span>](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
-   [<span data-ttu-id="ed149-169">配置可用性副本备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ed149-169">Configure Backup on Availability Replicas &#40;SQL Server&#41;</span></span>](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [<span data-ttu-id="ed149-170">配置对可用性副本的只读访问 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ed149-170">Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;</span></span>](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="ed149-171">为可用性组配置只读路由 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ed149-171">Configure Read-Only Routing for an Availability Group &#40;SQL Server&#41;</span></span>](configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="ed149-172">更改可用性副本的会话超时期限 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ed149-172">Change the Session-Timeout Period for an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
 <span data-ttu-id="ed149-173">**完成可用性组配置**</span><span class="sxs-lookup"><span data-stu-id="ed149-173">**To complete availability group configuration**</span></span>  
  
-   [<span data-ttu-id="ed149-174">将辅助副本联接到可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ed149-174">Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="ed149-175">为可用性组手动准备辅助数据库 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ed149-175">Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;</span></span>](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="ed149-176">将辅助数据库联接到可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ed149-176">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="ed149-177">创建或配置可用性组侦听程序 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ed149-177">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
 <span data-ttu-id="ed149-178">**用于创建可用性组的其他方法**</span><span class="sxs-lookup"><span data-stu-id="ed149-178">**Alternative ways to create an availability group**</span></span>  
  
-   [<span data-ttu-id="ed149-179">使用可用性组向导 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="ed149-179">Use the Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="ed149-180">创建可用性组 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ed149-180">Create an Availability Group &#40;Transact-SQL&#41;</span></span>](create-an-availability-group-transact-sql.md)  
  
-   [<span data-ttu-id="ed149-181">创建可用性组 (SQL Server PowerShell)</span><span class="sxs-lookup"><span data-stu-id="ed149-181">Create an Availability Group &#40;SQL Server PowerShell&#41;</span></span>](../../../powershell/sql-server-powershell.md)  
  
 <span data-ttu-id="ed149-182">**启用 AlwaysOn 可用性组**</span><span class="sxs-lookup"><span data-stu-id="ed149-182">**To enable AlwaysOn Availability Groups**</span></span>  
  
-   [<span data-ttu-id="ed149-183">启用和禁用 AlwaysOn 可用性组 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ed149-183">Enable and Disable AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](enable-and-disable-always-on-availability-groups-sql-server.md)  
  
 <span data-ttu-id="ed149-184">**配置数据库镜像端点**</span><span class="sxs-lookup"><span data-stu-id="ed149-184">**To configure a database mirroring endpoint**</span></span>  
  
-   [<span data-ttu-id="ed149-185">为 AlwaysOn 可用性组 &#40;SQL Server PowerShell 创建数据库镜像端点&#41;</span><span class="sxs-lookup"><span data-stu-id="ed149-185">Create a Database Mirroring Endpoint for AlwaysOn Availability Groups &#40;SQL Server PowerShell&#41;</span></span>](database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [<span data-ttu-id="ed149-186">为 Windows 身份验证创建数据库镜像终结点 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ed149-186">Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [<span data-ttu-id="ed149-187">使用数据库镜像终结点证书 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="ed149-187">Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
-   [<span data-ttu-id="ed149-188">在添加或修改可用性副本时指定终结点 URL (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ed149-188">Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;</span></span>](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
 <span data-ttu-id="ed149-189">**解决 AlwaysOn 可用性组配置问题**</span><span class="sxs-lookup"><span data-stu-id="ed149-189">**To troubleshoot AlwaysOn Availability Groups configuration**</span></span>  
  
-   [<span data-ttu-id="ed149-190">) 删除 AlwaysOn 可用性组配置 (SQL Server 的疑难解答</span><span class="sxs-lookup"><span data-stu-id="ed149-190">Troubleshoot AlwaysOn Availability Groups Configuration (SQL Server)deleted</span></span>](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
-   [<span data-ttu-id="ed149-191">排除失败的添加文件操作 &#40;AlwaysOn 可用性组&#41;</span><span class="sxs-lookup"><span data-stu-id="ed149-191">Troubleshoot a Failed Add-File Operation &#40;AlwaysOn Availability Groups&#41;</span></span>](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="ed149-192">相关内容</span><span class="sxs-lookup"><span data-stu-id="ed149-192">Related Content</span></span>  
  
-   [<span data-ttu-id="ed149-193">用于高可用性和灾难恢复的 Microsoft SQL Server AlwaysOn 解决方案指南</span><span class="sxs-lookup"><span data-stu-id="ed149-193">Microsoft SQL Server AlwaysOn Solutions Guide for High Availability and Disaster Recovery</span></span>](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
## <a name="see-also"></a><span data-ttu-id="ed149-194">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ed149-194">See Also</span></span>  
 <span data-ttu-id="ed149-195">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ed149-195">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="ed149-196">[数据库镜像终结点 (SQL Server)](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ed149-196">[The Database Mirroring Endpoint &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md) </span></span>  
 <span data-ttu-id="ed149-197">[可用性组侦听程序、客户端连接和应用程序故障转移 &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span><span class="sxs-lookup"><span data-stu-id="ed149-197">[Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span></span>  
 [<span data-ttu-id="ed149-198">AlwaysOn 可用性组 &#40;SQL Server 的先决条件、限制和建议&#41;</span><span class="sxs-lookup"><span data-stu-id="ed149-198">Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](prereqs-restrictions-recommendations-always-on-availability.md)  
