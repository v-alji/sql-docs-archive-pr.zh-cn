---
title: WSFC 仲裁模式和投票配置 (SQL Server) | Microsoft Docs
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
ms.assetid: ca0d59ef-25f0-4047-9130-e2282d058283
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6b1d5ad992c59f252f485f2d65451a72f150bef8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586249"
---
# <a name="wsfc-quorum-modes-and-voting-configuration-sql-server"></a><span data-ttu-id="93eef-102">WSFC 仲裁模式和投票配置 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="93eef-102">WSFC Quorum Modes and Voting Configuration (SQL Server)</span></span>
  <span data-ttu-id="93eef-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 和 AlwaysOn 故障转移群集实例 (FCI) 都利用 Windows Server 故障转移群集 (WSFC) 来作为平台技术。</span><span class="sxs-lookup"><span data-stu-id="93eef-103">Both [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] and AlwaysOn Failover Cluster Instances (FCI) take advantage of Windows Server Failover Clustering (WSFC) as a platform technology.</span></span>  <span data-ttu-id="93eef-104">WSFC 使用一种基于仲裁的方法来监视群集的整体运行状况，并且最大限度地提高节点级别的容错能力。</span><span class="sxs-lookup"><span data-stu-id="93eef-104">WSFC uses a quorum-based approach to monitoring overall cluster health and maximize node-level fault tolerance.</span></span> <span data-ttu-id="93eef-105">理解 WSFC 仲裁模式和节点投票配置对于 AlwaysOn 高可用性和灾难恢复解决方案的设计、操作和故障排除十分重要。</span><span class="sxs-lookup"><span data-stu-id="93eef-105">A fundamental understanding of WSFC quorum modes and node voting configuration is very important to designing, operating, and troubleshooting your AlwaysOn high availability and disaster recovery solution.</span></span>  
  
 <span data-ttu-id="93eef-106">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="93eef-106">**In this topic:**</span></span>  
  
-   [<span data-ttu-id="93eef-107">仲裁的群集运行状况检测</span><span class="sxs-lookup"><span data-stu-id="93eef-107">Cluster Health Detection by Quorum</span></span>](#ClusterHealthDetectionbyQuorum)  
  
-   [<span data-ttu-id="93eef-108">仲裁模式</span><span class="sxs-lookup"><span data-stu-id="93eef-108">Quorum Modes</span></span>](#QuorumModes)  
  
-   [<span data-ttu-id="93eef-109">投票和非投票节点</span><span class="sxs-lookup"><span data-stu-id="93eef-109">Voting and Non-Voting Nodes</span></span>](#VotingandNonVotingNodes)  
  
-   [<span data-ttu-id="93eef-110">建议的仲裁投票调整</span><span class="sxs-lookup"><span data-stu-id="93eef-110">Recommended Adjustments to Quorum Voting</span></span>](#RecommendedAdjustmentstoQuorumVoting)  
  
-   [<span data-ttu-id="93eef-111">相关任务</span><span class="sxs-lookup"><span data-stu-id="93eef-111">Related Tasks</span></span>](#RelatedTasks)  
  
-   [<span data-ttu-id="93eef-112">相关内容</span><span class="sxs-lookup"><span data-stu-id="93eef-112">Related Content</span></span>](#RelatedContent)  
  
##  <a name="cluster-health-detection-by-quorum"></a><a name="ClusterHealthDetectionbyQuorum"></a> <span data-ttu-id="93eef-113">由仲裁进行的群集运行状况检测</span><span class="sxs-lookup"><span data-stu-id="93eef-113">Cluster Health Detection by Quorum</span></span>  
 <span data-ttu-id="93eef-114">WSFC 群集中的每个节点都参与周期性信号通信，以便与其他节点共享该节点的运行状况。</span><span class="sxs-lookup"><span data-stu-id="93eef-114">Each node in a WSFC cluster participates in periodic heartbeat communication to share the node's health status with the other nodes.</span></span> <span data-ttu-id="93eef-115">未响应的节点被认为是处于故障状态。</span><span class="sxs-lookup"><span data-stu-id="93eef-115">Unresponsive nodes are considered to be in a failed state.</span></span>  
  
 <span data-ttu-id="93eef-116">\*\* “仲裁”节点集是 WSFC 群集中的大多数投票节点和见证服务器。</span><span class="sxs-lookup"><span data-stu-id="93eef-116">A *quorum* node set is a majority of the voting nodes and witnesses in the WSFC cluster.</span></span> <span data-ttu-id="93eef-117">\*\* WSFC 群集的总体运行状况和状态是由定期“仲裁投票”确定的。</span><span class="sxs-lookup"><span data-stu-id="93eef-117">The overall health and status of a WSFC cluster is determined by a periodic *quorum vote*.</span></span>  <span data-ttu-id="93eef-118">仲裁的存在意味着群集运行状况正常，且能提供节点级别的容错能力。</span><span class="sxs-lookup"><span data-stu-id="93eef-118">The presence of a quorum means that the cluster is healthy and able to provide node-level fault tolerance.</span></span>  
  
 <span data-ttu-id="93eef-119">没有仲裁并不指示群集未在正常状况下运行。</span><span class="sxs-lookup"><span data-stu-id="93eef-119">The absence of a quorum indicates that the cluster is not healthy.</span></span>  <span data-ttu-id="93eef-120">必须维护整体 WSFC 群集运行状况，以便确保运行状况辅助节点可用于要故障转移到的主节点。</span><span class="sxs-lookup"><span data-stu-id="93eef-120">Overall WSFC cluster health must be maintained in order to ensure that healthy secondary nodes are available for primary nodes to fail over to.</span></span>  <span data-ttu-id="93eef-121">如果仲裁投票失败，作为一项预防措施，WSFC 群集将被设为脱机。</span><span class="sxs-lookup"><span data-stu-id="93eef-121">If the quorum vote fails, the WSFC cluster will be set offline as a precautionary measure.</span></span>  <span data-ttu-id="93eef-122">这也将导致停止所有向群集注册的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="93eef-122">This will also cause all [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instances registered with the cluster to be stopped.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="93eef-123">如果 WSFC 群集因为仲裁失败而被设为脱机，则需要手动干预以便将其重新联机。</span><span class="sxs-lookup"><span data-stu-id="93eef-123">If a WSFC cluster is set offline because of quorum failure, manual intervention is required to bring it back online.</span></span>  
>   
>  <span data-ttu-id="93eef-124">有关详细信息，请参阅： [通过强制仲裁进行 WSFC 灾难恢复 (SQL Server)](wsfc-disaster-recovery-through-forced-quorum-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="93eef-124">For more information, see: [WSFC Disaster Recovery through Forced Quorum &#40;SQL Server&#41;](wsfc-disaster-recovery-through-forced-quorum-sql-server.md).</span></span>  
  
##  <a name="quorum-modes"></a><a name="QuorumModes"></a><span data-ttu-id="93eef-125">仲裁模式</span><span class="sxs-lookup"><span data-stu-id="93eef-125">Quorum Modes</span></span>  
 <span data-ttu-id="93eef-126">\*\* “仲裁模式”是在 WSFC 群集级别配置的，指示用于仲裁投票的方法。</span><span class="sxs-lookup"><span data-stu-id="93eef-126">A *quorum mode* is configured at the WSFC cluster level that dictates the methodology used for quorum voting.</span></span>  <span data-ttu-id="93eef-127">故障转移群集管理器实用工具将会基于群集中的节点数来建议仲裁模式。</span><span class="sxs-lookup"><span data-stu-id="93eef-127">The Failover Cluster Manager utility will recommend a quorum mode based on the number of nodes in the cluster.</span></span>  
  
 <span data-ttu-id="93eef-128">以下仲裁模式可用于确定构成投票仲裁的元素：</span><span class="sxs-lookup"><span data-stu-id="93eef-128">The following quorum modes can be used to determine what constitutes a quorum of votes:</span></span>  
  
-   <span data-ttu-id="93eef-129">**节点多数。**</span><span class="sxs-lookup"><span data-stu-id="93eef-129">**Node Majority.**</span></span> <span data-ttu-id="93eef-130">群集中超过一半的投票节点必须投票赞成群集处于正常状态。</span><span class="sxs-lookup"><span data-stu-id="93eef-130">More than one-half of the voting nodes in the cluster must vote affirmatively for the cluster to be healthy.</span></span>  
  
-   <span data-ttu-id="93eef-131">**节点和文件共享的大多数。**</span><span class="sxs-lookup"><span data-stu-id="93eef-131">**Node and File Share Majority.**</span></span> <span data-ttu-id="93eef-132">与节点的大多数仲裁模式相似，只有远程文件共享也配置为投票见证除外，并且从任何节点到该共享的连接也作为赞成投票计数。</span><span class="sxs-lookup"><span data-stu-id="93eef-132">Similar to Node Majority quorum mode, except that a remote file share is also configured as a voting witness, and connectivity from any node to that share is also counted as an affirmative vote.</span></span>  <span data-ttu-id="93eef-133">超过一半的可能投票必须赞成群集处于正常状态。</span><span class="sxs-lookup"><span data-stu-id="93eef-133">More than one-half of the possible votes must be affirmative for the cluster to be healthy.</span></span>  
  
     <span data-ttu-id="93eef-134">作为最佳实践，见证文件共享不应驻留在该群集中的任何节点上，必须它应该对于该群集中的所有节点都是可见的。</span><span class="sxs-lookup"><span data-stu-id="93eef-134">As a best practice, the witness file share should not reside on any node in the cluster, and it should be visible to all nodes in the cluster.</span></span>  
  
-   <span data-ttu-id="93eef-135">**节点和磁盘多数。**</span><span class="sxs-lookup"><span data-stu-id="93eef-135">**Node and Disk Majority.**</span></span> <span data-ttu-id="93eef-136">与节点的大多数仲裁模式相似，只有共享磁盘群集资源也指定为投票见证除外，并且从任何节点到该共享磁盘的连接也作为赞成投票计数。</span><span class="sxs-lookup"><span data-stu-id="93eef-136">Similar to Node Majority quorum mode, except that a shared disk cluster resource is also designated as a voting witness, and connectivity from any node to that shared disk is also counted as an affirmative vote.</span></span>  <span data-ttu-id="93eef-137">超过一半的可能投票必须赞成群集处于正常状态。</span><span class="sxs-lookup"><span data-stu-id="93eef-137">More than one-half of the possible votes must be affirmative for the cluster to be healthy.</span></span>  
  
-   <span data-ttu-id="93eef-138">**仅磁盘。**</span><span class="sxs-lookup"><span data-stu-id="93eef-138">**Disk Only.**</span></span> <span data-ttu-id="93eef-139">共享磁盘群集资源指定为见证，并且从任何节点到该共享磁盘的连接也作为赞成投票计数。</span><span class="sxs-lookup"><span data-stu-id="93eef-139">A shared disk cluster resource is designated as a witness, and connectivity by any node to that shared disk is counted as an affirmative vote.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="93eef-140">在将非对称存储配置用于 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]时，如果您具有奇数数目的投票节点，则通常应该使用节点的大多数仲裁模式；如果您具有偶数数目的投票节点，则通常应该使用节点和文件共享的大多数仲裁模式。</span><span class="sxs-lookup"><span data-stu-id="93eef-140">When using an asymmetric storage configuration for [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], you should generally use the Node Majority quorum mode when you have an odd number of voting nodes, or the Node and File Share Majority quorum mode when you have an even number of voting nodes.</span></span>  
  
##  <a name="voting-and-non-voting-nodes"></a><a name="VotingandNonVotingNodes"></a> <span data-ttu-id="93eef-141">投票和非投票节点</span><span class="sxs-lookup"><span data-stu-id="93eef-141">Voting and Non-Voting Nodes</span></span>  
 <span data-ttu-id="93eef-142">默认情况下，WSFC 群集中的每个节点都作为群集仲裁的成员包括；每个节点都具有用于确定群集整体运行状况的单个投票，并且每个节点都将持续尝试建立仲裁。</span><span class="sxs-lookup"><span data-stu-id="93eef-142">By default, each node in the WSFC cluster is included as a member of the cluster quorum; each node has a single vote in determining the overall cluster health, and each node will continuously attempt to establish a quorum.</span></span>  <span data-ttu-id="93eef-143">\*\* 到目前为止对仲裁的论述已谨慎地将对群集运行状况进行投票的一组 WSFC 群集节点划分为“投票节点”。</span><span class="sxs-lookup"><span data-stu-id="93eef-143">The quorum discussion to this point has carefully qualified the set of WSFC cluster nodes that vote on cluster health as *voting nodes*.</span></span>  
  
 <span data-ttu-id="93eef-144">在一个 WSFC 群集中没有单独的节点可以明确确定该群集作为一个整体是正常运行还是非正常运行。</span><span class="sxs-lookup"><span data-stu-id="93eef-144">No individual node in a WSFC cluster can definitively determine that the cluster as a whole is healthy or unhealthy.</span></span>  <span data-ttu-id="93eef-145">在任意给定时刻，从各节点的角度来说，其他一些节点可能好像脱机，或者好像处于故障转移中，或者好像由于网络通信失败而无法响应。</span><span class="sxs-lookup"><span data-stu-id="93eef-145">At any given moment, from the perspective of each node, some of the other nodes may appear to be offline, or appear to be in the process of failover, or appear unresponsive due to a network communication failure.</span></span>  <span data-ttu-id="93eef-146">仲裁投票的一个关键功能是确定 WSFC 群集中每个节点的明显表现出来的状态是否真的就是这些节点的实际状态。</span><span class="sxs-lookup"><span data-stu-id="93eef-146">A key function of the quorum vote is to determine whether the apparent state of each of node in the WSFC cluster is indeed that actual state of those nodes.</span></span>  
  
 <span data-ttu-id="93eef-147">对于除了“仅限磁盘”之外的所有仲裁模式，仲裁投票的效力取决于群集中所有投票节点之间的可靠的通信。</span><span class="sxs-lookup"><span data-stu-id="93eef-147">For all of the quorum models except 'Disk Only', the effectiveness of a quorum vote depends on reliable communications between all of the voting nodes in the cluster.</span></span> <span data-ttu-id="93eef-148">同一物理子网上各节点之间的网络通信应被视为可靠的；应该信任仲裁投票。</span><span class="sxs-lookup"><span data-stu-id="93eef-148">Network communications between nodes on the same physical subnet should be considered reliable; the quorum vote should be trusted.</span></span>  
  
 <span data-ttu-id="93eef-149">但是，如果其他子网上的节点在仲裁投票中被视为不可响应的，但它实际上处于联机状态并且正常运行，则很可能是因为子网之间网络通信失败。</span><span class="sxs-lookup"><span data-stu-id="93eef-149">However, if a node on another subnet is seen as non-responsive in a quorum vote, but it is actually online and otherwise healthy, that is most likely due to a network communications failure between subnets.</span></span>  <span data-ttu-id="93eef-150">根据群集拓扑结构、仲裁模式和故障转移策略配置，该网络通信失败可能会有效地创建超过一组（或一个子组）的投票节点。</span><span class="sxs-lookup"><span data-stu-id="93eef-150">Depending upon the cluster topology, quorum mode, and failover policy configuration, that network communications failure may effectively create more than one set (or subset) of voting nodes.</span></span>  
  
 <span data-ttu-id="93eef-151">当多个子组的投票节点能够建立自己的仲裁时，这称作\*\* 分区情况。</span><span class="sxs-lookup"><span data-stu-id="93eef-151">When more than one subset of voting nodes is able to establish a quorum on its own, that is known as a *split-brain scenario*.</span></span>  <span data-ttu-id="93eef-152">在这种情况下，单独仲裁中的节点可能具有不同的行为方式，并有互相冲突。</span><span class="sxs-lookup"><span data-stu-id="93eef-152">In such a scenario, the nodes in the separate quorums may behave differently, and in conflict with one another.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="93eef-153">此裂脑情况仅在系统管理员手动执行强制的仲裁操作时或者在非常罕见的情况（如强制故障转移）时才可能出现；并且显式细分仲裁节点组。</span><span class="sxs-lookup"><span data-stu-id="93eef-153">The split-brain scenario is only possible when a system administrator manually performs a forced quorum operation, or in very rare circumstances, a forced failover; explicitly subdividing the quorum node set.</span></span>  
  
 <span data-ttu-id="93eef-154">为了简化仲裁配置和增加正常运行时间，可能需要调整每个节点的“NodeWeight”设置，以便为进行仲裁而计算票数时不包括该节点的投票\*\*。</span><span class="sxs-lookup"><span data-stu-id="93eef-154">In order to simplify your quorum configuration and increase up-time, you may want to adjust each node's *NodeWeight* setting so that the node's vote is not counted towards the quorum.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="93eef-155">为了使用 NodeWeight 设置，必须将以下修补程序应用到 WSFC 群集中的所有服务器：</span><span class="sxs-lookup"><span data-stu-id="93eef-155">In order to use NodeWeight settings, the following hotfix must be applied to all servers in the WSFC cluster:</span></span>  
>   
>  <span data-ttu-id="93eef-156">[KB2494036](https://support.microsoft.com/kb/2494036)：提供了一个修补程序，可让你配置在和中没有仲裁投票的群集节点 [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)][!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93eef-156">[KB2494036](https://support.microsoft.com/kb/2494036): A hotfix is available to let you configure a cluster node that does not have quorum votes in [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] and in [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)]</span></span>  
  
##  <a name="recommended-adjustments-to-quorum-voting"></a><a name="RecommendedAdjustmentstoQuorumVoting"></a> <span data-ttu-id="93eef-157">建议的仲裁投票调整</span><span class="sxs-lookup"><span data-stu-id="93eef-157">Recommended Adjustments to Quorum Voting</span></span>  
 <span data-ttu-id="93eef-158">在启用或禁用某一给定 WSFC 节点的投票时，应遵循以下准则：</span><span class="sxs-lookup"><span data-stu-id="93eef-158">When enabling or disabling a given WSFC node's vote, follow these guidelines:</span></span>  
  
-   <span data-ttu-id="93eef-159">**默认为不投票。**</span><span class="sxs-lookup"><span data-stu-id="93eef-159">**No vote by default.**</span></span> <span data-ttu-id="93eef-160">假定在没有明确理由的情况下每个节点都不应投票。</span><span class="sxs-lookup"><span data-stu-id="93eef-160">Assume that each node should not vote without explicit justification.</span></span>  
  
-   <span data-ttu-id="93eef-161">**包括所有的主副本。**</span><span class="sxs-lookup"><span data-stu-id="93eef-161">**Include all primary replicas.**</span></span> <span data-ttu-id="93eef-162">承载可用性组主副本或作为 FCI 的首选所有者的每个 WSFC 节点都应具有一票。</span><span class="sxs-lookup"><span data-stu-id="93eef-162">Each WSFC node that hosts an availability group primary replica or is the preferred owner of an FCI should have a vote.</span></span>  
  
-   <span data-ttu-id="93eef-163">**包括可能的自动故障转移所有者。**</span><span class="sxs-lookup"><span data-stu-id="93eef-163">**Include possible automatic failover owners.**</span></span> <span data-ttu-id="93eef-164">可作为自动可用性组故障转移或 FCI 故障转移的结果承载主副本的每个节点都应具有一票。</span><span class="sxs-lookup"><span data-stu-id="93eef-164">Each node that could host a primary replica, as the result of an automatic availability group failover or FCI failover, should have a vote.</span></span> <span data-ttu-id="93eef-165">如果在 WSFC 群集中只有一个可用性组并且可用性副本仅由独立实例承载，则此规则仅包括作为自动故障转移目标的辅助副本。</span><span class="sxs-lookup"><span data-stu-id="93eef-165">If there is only one availability group in the WSFC cluster and availability replicas are hosted only by standalone instances, this rule includes only the secondary replica that is the automatic failover target.</span></span>  
  
-   <span data-ttu-id="93eef-166">**不包括辅助站点节点。**</span><span class="sxs-lookup"><span data-stu-id="93eef-166">**Exclude secondary site nodes.**</span></span> <span data-ttu-id="93eef-167">通常，不要向驻留在辅助灾难恢复站点的 WSFC 节点投票。</span><span class="sxs-lookup"><span data-stu-id="93eef-167">In general, do not give votes to WSFC nodes that reside at a secondary disaster recovery site.</span></span>  <span data-ttu-id="93eef-168">在主站点不存在任何问题时，您不会希望辅助站点中的节点参与到令群集脱机的决策中来。</span><span class="sxs-lookup"><span data-stu-id="93eef-168">You do not want nodes in the secondary site to contribute to a decision to take the cluster offline when there is nothing wrong with the primary site.</span></span>  
  
-   <span data-ttu-id="93eef-169">**奇数数目的投票。**</span><span class="sxs-lookup"><span data-stu-id="93eef-169">**Odd number of votes.**</span></span> <span data-ttu-id="93eef-170">如果需要，将见证文件共享、见证节点或见证磁盘添加到群集并且调整仲裁模式以便防止群集仲裁中出现可能的等同值。</span><span class="sxs-lookup"><span data-stu-id="93eef-170">If necessary, add a witness file share, a witness node, or a witness disk to the cluster and adjust the quorum mode to prevent possible ties in the quorum vote.</span></span>  
  
-   <span data-ttu-id="93eef-171">**故障转移后重新评估投票分配。**</span><span class="sxs-lookup"><span data-stu-id="93eef-171">**Re-assess vote assignments post-failover.**</span></span> <span data-ttu-id="93eef-172">您不希望故障转移到不支持运行状况仲裁的群集配置。</span><span class="sxs-lookup"><span data-stu-id="93eef-172">You do not want to fail over into a cluster configuration that does not support a healthy quorum.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="93eef-173">在验证 WSFC 仲裁投票配置时，如果以下任何条件成立，AlwaysOn 可用性组向导将显示一个警告。</span><span class="sxs-lookup"><span data-stu-id="93eef-173">When validating WSFC quorum vote configuration, the AlwaysOn Availability Group Wizard shows a warning if any of the following conditions are true:</span></span>  
> 
>  -   <span data-ttu-id="93eef-174">承载主副本的群集节点不具有投票</span><span class="sxs-lookup"><span data-stu-id="93eef-174">The cluster node that hosts the primary replica does not have a vote</span></span>  
> -   <span data-ttu-id="93eef-175">辅助副本配置用于自动故障转移并且其群集节点不具有投票。</span><span class="sxs-lookup"><span data-stu-id="93eef-175">A secondary replica is configured for automatic failover and its cluster node does not have a vote.</span></span>  
> -   <span data-ttu-id="93eef-176">[KB2494036](https://support.microsoft.com/kb/2494036) 未安装在承载可用性副本的所有群集节点上。</span><span class="sxs-lookup"><span data-stu-id="93eef-176">[KB2494036](https://support.microsoft.com/kb/2494036) is not installed on all cluster nodes that host availability replicas.</span></span> <span data-ttu-id="93eef-177">此修补程序是在多站点部署中为群集节点添加或删除投票所必需的。</span><span class="sxs-lookup"><span data-stu-id="93eef-177">This patch is required to add or remove votes for cluster nodes in multi-site deployments.</span></span> <span data-ttu-id="93eef-178">但在单站点部署中，此修补程序通常不是必需的并且您可以放心地忽略该警告。</span><span class="sxs-lookup"><span data-stu-id="93eef-178">However, in single-site deployments, it is usually not required and you may safely ignore the warning.</span></span>  
> 
> [!TIP]
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="93eef-179">公开若干系统动态管理视图 (DMV)，可帮助你管理 WSFC 群集配置和节点仲裁投票相关的设置。</span><span class="sxs-lookup"><span data-stu-id="93eef-179">exposes several system dynamic management views (DMVs) that can help you manage settings related WSFC cluster configuration and node quorum voting.</span></span>  
> 
>  <span data-ttu-id="93eef-180">有关详细信息，请参阅：[sys.dm_hadr_cluster](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-transact-sql)[sys.dm_hadr_cluster_members](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-members-transact-sql)[sys.dm_os_cluster_nodes](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-nodes-transact-sql) 和 [sys.dm_hadr_cluster_networks](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-networks-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="93eef-180">For more information, see:  [sys.dm_hadr_cluster](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-transact-sql), [sys.dm_hadr_cluster_members](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-members-transact-sql), [sys.dm_os_cluster_nodes](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-nodes-transact-sql), [sys.dm_hadr_cluster_networks](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-networks-transact-sql)</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="93eef-181">相关任务</span><span class="sxs-lookup"><span data-stu-id="93eef-181">Related Tasks</span></span>  
  
-   [<span data-ttu-id="93eef-182">查看群集仲裁 NodeWeight 设置</span><span class="sxs-lookup"><span data-stu-id="93eef-182">View Cluster Quorum NodeWeight Settings</span></span>](view-cluster-quorum-nodeweight-settings.md)  
  
-   [<span data-ttu-id="93eef-183">配置群集仲裁 NodeWeight 设置</span><span class="sxs-lookup"><span data-stu-id="93eef-183">Configure Cluster Quorum NodeWeight Settings</span></span>](configure-cluster-quorum-nodeweight-settings.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="93eef-184">相关内容</span><span class="sxs-lookup"><span data-stu-id="93eef-184">Related Content</span></span>  
  
-   [<span data-ttu-id="93eef-185">用于高可用性和灾难恢复的 Microsoft SQL Server AlwaysOn 解决方案指南</span><span class="sxs-lookup"><span data-stu-id="93eef-185">Microsoft SQL Server AlwaysOn Solutions Guide for High Availability and Disaster Recovery</span></span>](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
-   [<span data-ttu-id="93eef-186">AlwaysOn 可用性组向导中的仲裁投票配置检查</span><span class="sxs-lookup"><span data-stu-id="93eef-186">Quorum vote configuration check in AlwaysOn Availability Group Wizards</span></span>](https://blogs.msdn.com/b/sqlalwayson/archive/2012/03/13/quorum-vote-configuration-check-in-alwayson-availability-group-wizards-andy-jing.aspx)  
  
-   <span data-ttu-id="93eef-187">[Windows Server 技术：故障转移群集](https://technet.microsoft.com/library/cc732488\(v=WS.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="93eef-187">[Windows Server Technologies:  Failover Clusters](https://technet.microsoft.com/library/cc732488\(v=WS.10\).aspx)</span></span>  
  
-   <span data-ttu-id="93eef-188">[故障转移群集分步指南：配置故障转移群集中的仲裁](https://technet.microsoft.com/library/cc770620\(WS.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="93eef-188">[Failover Cluster Step-by-Step Guide: Configuring the Quorum in a Failover Cluster](https://technet.microsoft.com/library/cc770620\(WS.10\).aspx)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93eef-189">另请参阅</span><span class="sxs-lookup"><span data-stu-id="93eef-189">See Also</span></span>  
 <span data-ttu-id="93eef-190">[通过强制仲裁 &#40;SQL Server 进行 WSFC 灾难恢复&#41;](wsfc-disaster-recovery-through-forced-quorum-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="93eef-190">[WSFC Disaster Recovery through Forced Quorum &#40;SQL Server&#41;](wsfc-disaster-recovery-through-forced-quorum-sql-server.md) </span></span>  
 [<span data-ttu-id="93eef-191">Windows Server 故障转移群集 (WSFC) 与 SQL Server</span><span class="sxs-lookup"><span data-stu-id="93eef-191">Windows Server Failover Clustering &#40;WSFC&#41; with SQL Server</span></span>](windows-server-failover-clustering-wsfc-with-sql-server.md)  
  
  
