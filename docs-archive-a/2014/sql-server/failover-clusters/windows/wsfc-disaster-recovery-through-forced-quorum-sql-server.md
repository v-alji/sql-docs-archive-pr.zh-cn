---
title: 通过强制仲裁进行 WSFC 灾难恢复 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], WSFC clusters
- quorum [SQL Server], AlwaysOn and WSFC quorum
- failover clustering [SQL Server], AlwaysOn Availability Groups
ms.assetid: 6cefdc18-899e-410c-9ae4-d6080f724046
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b2c9399472c6e67c9e2121a008f9283ba05943da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586250"
---
# <a name="wsfc-disaster-recovery-through-forced-quorum-sql-server"></a><span data-ttu-id="51ec6-102">通过强制仲裁进行 WSFC 灾难恢复 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="51ec6-102">WSFC Disaster Recovery through Forced Quorum (SQL Server)</span></span>
  <span data-ttu-id="51ec6-103">仲裁故障通常由涉及 WSFC 群集中的多个节点的系统性灾难、持久性通信故障或配置错误引起的。</span><span class="sxs-lookup"><span data-stu-id="51ec6-103">Quorum failure is usually caused by a systemic disaster, or a persistent communications failure, or a misconfiguration involving several nodes in the WSFC cluster.</span></span>  <span data-ttu-id="51ec6-104">从仲裁故障恢复需要手动干预。</span><span class="sxs-lookup"><span data-stu-id="51ec6-104">Manual intervention is required to recovery from a quorum failure.</span></span>  
  
-   <span data-ttu-id="51ec6-105">**准备工作：**  [先决条件](#Prerequisites)、[安全性](#Security)</span><span class="sxs-lookup"><span data-stu-id="51ec6-105">**Before you start:**  [Prerequisites](#Prerequisites), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="51ec6-106">通过强制仲裁过程进行 WSFC 灾难恢复\*\*\*\* [通过强制仲裁过程进行 WSFC 灾难恢复](#Main)</span><span class="sxs-lookup"><span data-stu-id="51ec6-106">**WSFC Disaster Recovery through the Forced Quorum Procedure** [WSFC Disaster Recovery through the Forced Quorum Procedure](#Main)</span></span>  
  
-   [<span data-ttu-id="51ec6-107">相关任务</span><span class="sxs-lookup"><span data-stu-id="51ec6-107">Related Tasks</span></span>](#RelatedTasks)  
  
-   [<span data-ttu-id="51ec6-108">相关内容</span><span class="sxs-lookup"><span data-stu-id="51ec6-108">Related Content</span></span>](#RelatedContent)  
  
##  <a name="before-you-start"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="51ec6-109">开始之前</span><span class="sxs-lookup"><span data-stu-id="51ec6-109">Before You Start</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="51ec6-110">先决条件</span><span class="sxs-lookup"><span data-stu-id="51ec6-110">Prerequisites</span></span>  
 <span data-ttu-id="51ec6-111">强制仲裁过程假定在仲裁失败前存在运行状况正常的仲裁。</span><span class="sxs-lookup"><span data-stu-id="51ec6-111">The Forced Quorum Procedure assumes that a healthy quorum existed before the quorum failure.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="51ec6-112">用户应熟悉 Windows Server 故障转移群集、WSFC 仲裁模型、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]的概念和交互方式，以及环境特定的部署配置。</span><span class="sxs-lookup"><span data-stu-id="51ec6-112">The user should be well-informed on the concepts and interactions of Windows Server Failover Clustering, WSFC Quorum Models, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], and the environment's specific deployment configuration.</span></span>  
>   
>  <span data-ttu-id="51ec6-113">有关详细信息，请参阅：  [Windows Server 故障转移群集 (WSFC) 与 SQL Server](https://msdn.microsoft.com/library/hh270278\(v=SQL.110\).aspx)和 [WSFC 仲裁模式和投票配置 (SQL Server)](https://msdn.microsoft.com/library/hh270280\(v=SQL.110\).aspx)</span><span class="sxs-lookup"><span data-stu-id="51ec6-113">For more information, see:  [Windows Server Failover Clustering (WSFC) with SQL Server](https://msdn.microsoft.com/library/hh270278\(v=SQL.110\).aspx), [WSFC Quorum Modes and Voting Configuration (SQL Server)](https://msdn.microsoft.com/library/hh270280\(v=SQL.110\).aspx)</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="51ec6-114">Security</span><span class="sxs-lookup"><span data-stu-id="51ec6-114">Security</span></span>  
 <span data-ttu-id="51ec6-115">用户必须是一个域帐户，该帐户是每个 WSFC 群集节点上本地 Administrators 组的成员。</span><span class="sxs-lookup"><span data-stu-id="51ec6-115">The user must be a domain account that is member of the local Administrators group on each node of the WSFC cluster.</span></span>  
  
##  <a name="wsfc-disaster-recovery-through-the-forced-quorum-procedure"></a><a name="Main"></a> <span data-ttu-id="51ec6-116">通过强制仲裁过程进行 WSFC 灾难恢复</span><span class="sxs-lookup"><span data-stu-id="51ec6-116">WSFC Disaster Recovery through the Forced Quorum Procedure</span></span>  
 <span data-ttu-id="51ec6-117">请注意，仲裁故障将会使 WSFC 群集中的所有群集服务、SQL Server 实例和 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]设为脱机，这是因为该群集的配置无法确保节点级容错。</span><span class="sxs-lookup"><span data-stu-id="51ec6-117">Remember that quorum failure will cause all clustered services, SQL Server instances, and [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], in the WSFC cluster to be set offline, because the cluster, as configured, cannot ensure node-level fault tolerance.</span></span>  <span data-ttu-id="51ec6-118">仲裁故障意味着 WSFC 群集中的运行状况投票节点不再满足仲裁模型要求。</span><span class="sxs-lookup"><span data-stu-id="51ec6-118">A quorum failure means that healthy voting nodes in the WSFC cluster no longer satisfy the quorum model.</span></span> <span data-ttu-id="51ec6-119">一些节点可能已完全失败，而另一些节点可能只是关闭了 WSFC 服务并且除失去与仲裁通信的能力之外其他方面运行状况良好。</span><span class="sxs-lookup"><span data-stu-id="51ec6-119">Some nodes may have failed completely, and some may have just shut down the WSFC service and are otherwise healthy, except for the loss of the ability to communicate with a quorum.</span></span>  
  
 <span data-ttu-id="51ec6-120">若要使 WSFC 群集重新联机，您必须消除现有配置下仲裁故障的根源，根据需要恢复受影响的数据库，并且您可能需要在 WSFC 群集中重新配置其余的节点以反映现存的群集拓扑。</span><span class="sxs-lookup"><span data-stu-id="51ec6-120">To bring the WSFC cluster back online, you must correct the root cause of the quorum failure under the existing configuration, recover the affected databases as needed, and you may want to reconfigure the remaining nodes in the WSFC cluster to reflect the surviving cluster topology.</span></span>  
  
 <span data-ttu-id="51ec6-121">\*\* 您可以在 WSFC 群集节点上使用“强制仲裁”过程来覆盖使该群集脱机的安全控制。</span><span class="sxs-lookup"><span data-stu-id="51ec6-121">You can use the *forced quorum* procedure on a WSFC cluster node to override the safety controls that took the cluster offline.</span></span>  <span data-ttu-id="51ec6-122">这样做可有效地通知 WSFC 群集挂起仲裁投票检查，并使您能够在该群集中的任意节点上将 WSFC 群集资源和 SQL Server 重新联机。</span><span class="sxs-lookup"><span data-stu-id="51ec6-122">This effectively tells the cluster to suspend the quorum voting checks, and lets you bring the WSFC cluster resources and SQL Server back online on any of the nodes in the cluster.</span></span>  
  
 <span data-ttu-id="51ec6-123">此类型的灾难恢复过程应包含以下步骤：</span><span class="sxs-lookup"><span data-stu-id="51ec6-123">This type of disaster recovery process should include the following steps:</span></span>  
  
#### <a name="to-recover-from-quorum-failure"></a><span data-ttu-id="51ec6-124">从仲裁故障中恢复：</span><span class="sxs-lookup"><span data-stu-id="51ec6-124">To Recover from Quorum Failure:</span></span>  
  
1.  <span data-ttu-id="51ec6-125">**确定故障的范围。**</span><span class="sxs-lookup"><span data-stu-id="51ec6-125">**Determine the scope of the failure.**</span></span> <span data-ttu-id="51ec6-126">确定哪些可用性组或 SQL Server 实例是不响应的，哪些群集节点处于联机状态且可在灾后使用，并检查 Windows 事件日志和 SQL Server 系统日志。</span><span class="sxs-lookup"><span data-stu-id="51ec6-126">Identify which availability groups or SQL Server instances are non-responsive, which cluster nodes are online and available for post-disaster use, and examine the Windows event logs and the SQL Server system logs.</span></span>  <span data-ttu-id="51ec6-127">在可行的情况下，您应保留取证数据和系统日志以供未来分析使用。</span><span class="sxs-lookup"><span data-stu-id="51ec6-127">Where practical, you should preserve forensic data and system logs for later analysis.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="51ec6-128">在 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]的响应实例上，可以通过查询 [sys.dm_hadr_availability_group_states](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-group-states-transact-sql) 动态管理视图 (DMV)，获取有关在本地服务器实例上拥有可用性副本的可用性组的运行状况信息。</span><span class="sxs-lookup"><span data-stu-id="51ec6-128">On a responsive instance of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], you can obtain information about the health of availability groups that possess an availability replica on the local server instance by querying the [sys.dm_hadr_availability_group_states](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-group-states-transact-sql) dynamic management view (DMV).</span></span>  
  
2.  <span data-ttu-id="51ec6-129">**在单一节点上使用强制仲裁来启动 WSFC 群集。**</span><span class="sxs-lookup"><span data-stu-id="51ec6-129">**Start the WSFC cluster by using forced quorum on a single node.**</span></span> <span data-ttu-id="51ec6-130">确定组件故障数最少的一个节点（已关闭 WSFC 群集服务的节点除外）。</span><span class="sxs-lookup"><span data-stu-id="51ec6-130">Identify a node with a minimal number of component failures, other than that the WSFC cluster service was shut down.</span></span>  <span data-ttu-id="51ec6-131">确认此节点能够与其他大多数节点进行通信。</span><span class="sxs-lookup"><span data-stu-id="51ec6-131">Verify that this node can communicate with a majority of the other nodes.</span></span>  
  
     <span data-ttu-id="51ec6-132">在此节点上，使用强制仲裁过程来手动强制群集联机。</span><span class="sxs-lookup"><span data-stu-id="51ec6-132">On this node, manually force the cluster to come online using the forced quorum procedure.</span></span>  <span data-ttu-id="51ec6-133">为了最大程度地减少可能丢失的数据，应选择一个最后承载可用性组主副本的节点。</span><span class="sxs-lookup"><span data-stu-id="51ec6-133">To minimize potential data loss, select a node that was last hosting an availability group primary replica.</span></span>  
  
     <span data-ttu-id="51ec6-134">有关详细信息，请参阅：  [在无仲裁情况下强制启动 WSFC 群集](https://msdn.microsoft.com/library/hh270275\(v=SQL.110\).aspx)</span><span class="sxs-lookup"><span data-stu-id="51ec6-134">For more information, see:  [Force a WSFC Cluster to Start Without a Quorum](https://msdn.microsoft.com/library/hh270275\(v=SQL.110\).aspx)</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="51ec6-135">在逻辑 WSFC 群集获得大多数投票并自动转换到操作的常规仲裁模式之前，强制仲裁设置会在群集范围内阻止仲裁检查。</span><span class="sxs-lookup"><span data-stu-id="51ec6-135">The forced quorum setting has a cluster-wide affect to block quorum checks until the logical WSFC cluster achieves a majority of votes and automatically transitions to a regular quorum mode of operation.</span></span>  
  
3.  <span data-ttu-id="51ec6-136">**逐一在每个其他方面运行正常的节点上正常启动 WSFC 服务。**</span><span class="sxs-lookup"><span data-stu-id="51ec6-136">**Start the WSFC service normally on each otherwise healthy node, one at a time.**</span></span> <span data-ttu-id="51ec6-137">当您在其他节点上启动该群集服务时，您无需指定强制仲裁选项。</span><span class="sxs-lookup"><span data-stu-id="51ec6-137">You do not have to specify the forced quorum option when you start the cluster service on the other nodes.</span></span>  
  
     <span data-ttu-id="51ec6-138">随着每个节点上的 WSFC 服务重新联机，该服务会与其他运行状态正常的节点进行协商以同步新的群集配置状态。</span><span class="sxs-lookup"><span data-stu-id="51ec6-138">As the WSFC service on each node comes back online, it negotiates with the other healthy nodes to synchronize the new cluster configuration state.</span></span>  <span data-ttu-id="51ec6-139">记住一次只能在一个节点上执行此操作，以避免在解析群集的上一个已知状态时出现潜在的争用情况。</span><span class="sxs-lookup"><span data-stu-id="51ec6-139">Remember to do this one node at a time to prevent potential race conditions in resolving the last known state of the cluster.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="51ec6-140">确保您启动的每个节点都能够与其他刚刚联机的节点通信。</span><span class="sxs-lookup"><span data-stu-id="51ec6-140">Ensure that each node that you start can communicate with the other newly online nodes.</span></span>  <span data-ttu-id="51ec6-141">应考虑在其他节点上禁用 WSFC 服务。</span><span class="sxs-lookup"><span data-stu-id="51ec6-141">Consider disabling the WSFC service on the other nodes.</span></span>  <span data-ttu-id="51ec6-142">否则，您将会面临创建多个仲裁节点集（即“裂脑”情形）的风险。</span><span class="sxs-lookup"><span data-stu-id="51ec6-142">Otherwise,  you run the risk of creating more than one quorum node set; that is a split-brain scenario.</span></span> <span data-ttu-id="51ec6-143">如果您在步骤 1 中的调查结果很准确，则应该不会发生这种情况。</span><span class="sxs-lookup"><span data-stu-id="51ec6-143">If your findings in step 1 were accurate, this should not occur.</span></span>  
  
4.  <span data-ttu-id="51ec6-144">**应用新的仲裁模式和节点投票配置。**</span><span class="sxs-lookup"><span data-stu-id="51ec6-144">**Apply new quorum mode and node vote configuration.**</span></span> <span data-ttu-id="51ec6-145">如果强制仲裁成功地重新启动了群集中的所有节点并且仲裁故障的根源得到了消除，则更改为原始仲裁模式并且不需要节点投票配置。</span><span class="sxs-lookup"><span data-stu-id="51ec6-145">If forcing quorum successfully restarted all the nodes in the cluster and the root cause of the quorum failure has been corrected, changes to the original quorum mode and node vote configuration are unnecessary.</span></span>  
  
     <span data-ttu-id="51ec6-146">否则，您应评估新恢复的群集节点和可用性副本拓扑，并相应地更改每个节点的仲裁模式和投票分配。</span><span class="sxs-lookup"><span data-stu-id="51ec6-146">Otherwise, you should evaluate the newly recovered cluster node and availability replica topology, and change the quorum mode and vote assignments for each node as appropriate.</span></span> <span data-ttu-id="51ec6-147">应将未恢复的节点设置为脱机，或将其节点投票设置为零。</span><span class="sxs-lookup"><span data-stu-id="51ec6-147">Un-recovered nodes should be set offline or have their node votes set to zero.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="51ec6-148">此时，群集中的节点和 SQL Server 实例可能看起来已恢复回正常操作。</span><span class="sxs-lookup"><span data-stu-id="51ec6-148">At this point, the nodes and SQL Server instances in the cluster may appear to be restored back to regular operation.</span></span>  <span data-ttu-id="51ec6-149">但是，可能仍然不存在运行状况正常的仲裁。</span><span class="sxs-lookup"><span data-stu-id="51ec6-149">However, a healthy quorum may still not exist.</span></span>  <span data-ttu-id="51ec6-150">使用故障转移群集管理器或 SQL Server Management Studio 中的 AlwaysOn 面板或适当的 DMV 来确认仲裁已恢复正常。</span><span class="sxs-lookup"><span data-stu-id="51ec6-150">Using the Failover Cluster Manager, or the AlwaysOn Dashboard within SQL Server Management Studio, or the appropriate DMVs, verify that a quorum has been restored.</span></span>  
  
5.  <span data-ttu-id="51ec6-151">**根据需要恢复可用性组数据库副本。**</span><span class="sxs-lookup"><span data-stu-id="51ec6-151">**Recover availability group database replicas as needed.**</span></span> <span data-ttu-id="51ec6-152">非可用性组数据库应会作为常规 SQL Server 启动过程的一部分自行恢复和联机。</span><span class="sxs-lookup"><span data-stu-id="51ec6-152">Non-availability group databases should recover and come back online on their own as part of the regular SQL Server startup process.</span></span>  
  
     <span data-ttu-id="51ec6-153">通过按照以下顺序将可用性组副本重新联机可以最大程度地减少可能丢失的数据并缩短恢复时间：主副本、同步辅助副本和异步辅助副本。</span><span class="sxs-lookup"><span data-stu-id="51ec6-153">You can minimize potential data loss and recovery time for the availability group replicas by bringing them back online in this sequence:  primary replica, synchronous secondary replicas, asynchronous secondary replicas.</span></span>  
  
6.  <span data-ttu-id="51ec6-154">**修复或替换失败的组件并重新验证群集。**</span><span class="sxs-lookup"><span data-stu-id="51ec6-154">**Repair or replace failed components and re-validate cluster.**</span></span> <span data-ttu-id="51ec6-155">从最初的灾难和仲裁故障中恢复之后，您应修复或替换失败的节点并对相关的 WSFC 和 AlwaysOn 配置进行相应地调整。</span><span class="sxs-lookup"><span data-stu-id="51ec6-155">Now that you have recovered from the initial disaster and quorum failure, you should repair or replace the failed nodes and adjust related WSFC and AlwaysOn configurations accordingly.</span></span>  <span data-ttu-id="51ec6-156">这可以包括删除可用性组副本、使节点从群集中退出或者在节点上平展并重新安装软件。</span><span class="sxs-lookup"><span data-stu-id="51ec6-156">This can include dropping availability group replicas, evicting nodes from the cluster, or flattening and re-installing software on a node.</span></span>  
  
     <span data-ttu-id="51ec6-157">您必须修复或删除所有失败的可用性副本。</span><span class="sxs-lookup"><span data-stu-id="51ec6-157">You must repair or remove all failed availability replicas.</span></span>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="51ec6-158">将不会截断超过最后一个可用性副本的上一个已知点的事务日志。</span><span class="sxs-lookup"><span data-stu-id="51ec6-158">will not truncate the transaction log past the last known point of the farthest behind availability replica.</span></span>   <span data-ttu-id="51ec6-159">如果没有在可用性组中修复或删除某个失败的副本，则事务日志将会增长，因而您将面临其他副本的事务日志空间不足的风险。</span><span class="sxs-lookup"><span data-stu-id="51ec6-159">If a failed replica is not repaired or removed from the availability group, the transaction logs will grow and you will run the risk of running out of transaction log space on the other replicas.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="51ec6-160">如果您在某一可用性组侦听器在 WSFC 群集上存在时运行 WSFC 验证配置向导，该向导将生成以下不正确的警告消息：</span><span class="sxs-lookup"><span data-stu-id="51ec6-160">If you run the WSFC Validate a Configuration Wizard when an availability group listener exists on the WSFC cluster, the wizard generates the following incorrect warning message:</span></span>  
    >   
    >  <span data-ttu-id="51ec6-161">“网络名称 ‘Name:<network_name>’ 的 RegisterAllProviderIP 属性设为 1。对于当前群集配置，该值应设为 0。”</span><span class="sxs-lookup"><span data-stu-id="51ec6-161">"The RegisterAllProviderIP property for network name 'Name:<network_name>' is set to 1 For the current cluster configuration this value should be set to 0."</span></span>  
    >   
    >  <span data-ttu-id="51ec6-162">请忽略此消息。</span><span class="sxs-lookup"><span data-stu-id="51ec6-162">Please ignore this message.</span></span>  
  
7.  <span data-ttu-id="51ec6-163">**根据需要，重复步骤 4。**</span><span class="sxs-lookup"><span data-stu-id="51ec6-163">**Repeat step 4 as needed.**</span></span> <span data-ttu-id="51ec6-164">目标是重新建立适当级别的容错和高可用性以实现正常的操作。</span><span class="sxs-lookup"><span data-stu-id="51ec6-164">The goal is to re-establish the appropriate level of fault tolerance and high availability for healthy operations.</span></span>  
  
8.  <span data-ttu-id="51ec6-165">**进行 RPO/RTO 分析。**</span><span class="sxs-lookup"><span data-stu-id="51ec6-165">**Conduct RPO/RTO analysis.**</span></span> <span data-ttu-id="51ec6-166">您应分析 SQL Server 系统日志、数据库时间戳和 Windows 事件日志，以确定故障的根源，并记录实际的恢复点和恢复时间经验。</span><span class="sxs-lookup"><span data-stu-id="51ec6-166">You should analyze SQL Server system logs, database timestamps, and Windows event logs to determine root cause of the failure, and to document actual recovery point and recovery time experiences.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="51ec6-167">相关任务</span><span class="sxs-lookup"><span data-stu-id="51ec6-167">Related Tasks</span></span>  
  
-   [<span data-ttu-id="51ec6-168">在无仲裁情况下强制启动 WSFC 群集</span><span class="sxs-lookup"><span data-stu-id="51ec6-168">Force a WSFC Cluster to Start Without a Quorum</span></span>](force-a-wsfc-cluster-to-start-without-a-quorum.md)  
  
-   [<span data-ttu-id="51ec6-169">执行可用性组的强制手动故障转移 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="51ec6-169">Perform a Forced Manual Failover of an Availability Group &#40;SQL Server&#41;</span></span>](../../../database-engine/availability-groups/windows/perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="51ec6-170">查看群集仲裁 NodeWeight 设置</span><span class="sxs-lookup"><span data-stu-id="51ec6-170">View Cluster Quorum NodeWeight Settings</span></span>](view-cluster-quorum-nodeweight-settings.md)  
  
-   [<span data-ttu-id="51ec6-171">配置群集仲裁 NodeWeight 设置</span><span class="sxs-lookup"><span data-stu-id="51ec6-171">Configure Cluster Quorum NodeWeight Settings</span></span>](configure-cluster-quorum-nodeweight-settings.md)  
  
-   [<span data-ttu-id="51ec6-172">使用 AlwaysOn 面板 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="51ec6-172">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md) 
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="51ec6-173">相关内容</span><span class="sxs-lookup"><span data-stu-id="51ec6-173">Related Content</span></span>  
  
-   <span data-ttu-id="51ec6-174">[查看故障转移群集的事件和日志](https://technet.microsoft.com/library/cc772342\(WS.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="51ec6-174">[View Events and Logs for a Failover Cluster](https://technet.microsoft.com/library/cc772342\(WS.10\).aspx)</span></span>  
  
-   [<span data-ttu-id="51ec6-175">Get-ClusterLog 故障转移群集 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="51ec6-175">Get-ClusterLog Failover Cluster Cmdlet</span></span>](https://technet.microsoft.com/library/ee461045.aspx)  
  
## <a name="see-also"></a><span data-ttu-id="51ec6-176">另请参阅</span><span class="sxs-lookup"><span data-stu-id="51ec6-176">See Also</span></span>  
 [<span data-ttu-id="51ec6-177">Windows Server 故障转移群集 (WSFC) 与 SQL Server</span><span class="sxs-lookup"><span data-stu-id="51ec6-177">Windows Server Failover Clustering &#40;WSFC&#41; with SQL Server</span></span>](windows-server-failover-clustering-wsfc-with-sql-server.md)  
  
  
