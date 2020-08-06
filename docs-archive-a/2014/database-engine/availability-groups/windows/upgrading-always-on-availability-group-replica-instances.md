---
title: 升级和更新可用性组服务器，停机时间和数据丢失最少 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: f670af56-dbcc-4309-9119-f919dcad8a65
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6bac882b93016a430fbcace2d590e6cc087123d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693474"
---
# <a name="upgrade-and-update-of-availability-group-servers-with-minimal-downtime-and-data-loss"></a><span data-ttu-id="a342e-102">在停机时间和数据丢失最少的情况下升级和更新可用性组服务器</span><span class="sxs-lookup"><span data-stu-id="a342e-102">Upgrade and Update of Availability Group Servers with Minimal Downtime and Data Loss</span></span>
  <span data-ttu-id="a342e-103">将服务器实例从 SQL Server 2012 更新或升级到 Service Pack 或更高版本时，您可以通过执行顺序更新或升级将可用性组的停机时间降低到一个手动故障转移所需的时间。</span><span class="sxs-lookup"><span data-stu-id="a342e-103">When updating or upgrading server instances from SQL Server 2012 to a service pack or a newer version, you can reduce downtime for an availability group to only a single manual failover by performing a sequential update or upgrade.</span></span> <span data-ttu-id="a342e-104">对于升级 SQL Server 版本，它称为“滚动升级”；对于使用修复程序或 Service Pack 更新当前 SQL Server 版本，它称为“滚动更新”。</span><span class="sxs-lookup"><span data-stu-id="a342e-104">For upgrading SQL Server versions, it is known as rolling upgrade; for updating the current SQL Server version with hotfixes or service packs, it is known as rolling update.</span></span>  
  
 <span data-ttu-id="a342e-105">此主题仅讨论 SQL Server 升级/更新。</span><span class="sxs-lookup"><span data-stu-id="a342e-105">This topic limits the discussion to SQL Server upgrades/updates only.</span></span> <span data-ttu-id="a342e-106">有关运行高度可用 SQL Server 实例的操作系统相关升级/更新，请参阅[用于操作系统升级的 AlwaysOn 可用性组的跨群集迁移](https://msdn.microsoft.com/library/jj873730.aspx)</span><span class="sxs-lookup"><span data-stu-id="a342e-106">For operating system-related upgrades/updates that the highly-available SQL Server instances are running on, see [Cross-cluster Migration of AlwaysOn Availability Groups for Operating System Upgrades](https://msdn.microsoft.com/library/jj873730.aspx)</span></span>  
  
## <a name="rolling-upgradeupdate-best-practices-for-alwayson-availability-groups"></a><span data-ttu-id="a342e-107">AlwaysOn 可用性组的滚动升级/更新最佳做法</span><span class="sxs-lookup"><span data-stu-id="a342e-107">Rolling Upgrade/Update Best Practices for AlwaysOn Availability Groups</span></span>  
 <span data-ttu-id="a342e-108">在执行服务器升级/更新时应遵循以下最佳做法以尽量减小可用性组的停机时间和数据丢失量：</span><span class="sxs-lookup"><span data-stu-id="a342e-108">The following best practices should be observed when performing server upgrades/updates in order to minimize downtime and data loss for your availability groups:</span></span>  
  
-   <span data-ttu-id="a342e-109">在启动滚动升级/更新前，</span><span class="sxs-lookup"><span data-stu-id="a342e-109">Before starting the rolling upgrade/update,</span></span>  
  
    -   <span data-ttu-id="a342e-110">至少对一个同步提交副本执行实际手动故障转移</span><span class="sxs-lookup"><span data-stu-id="a342e-110">Perform a practice manual failover on at least one of your synchronous-commit replicas</span></span>  
  
    -   <span data-ttu-id="a342e-111">通过对每个可用性数据库执行完整数据库备份来保护您的数据</span><span class="sxs-lookup"><span data-stu-id="a342e-111">Protect your data by performing a full database backup on every availability database</span></span>  
  
    -   <span data-ttu-id="a342e-112">在每个可用性数据库上运行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="a342e-112">Run DBCC CHECKDB on every availability database</span></span>  
  
-   <span data-ttu-id="a342e-113">始终首先升级/更新远程辅助副本节点，然后升级/更新本地辅助副本节点，最后升级/更新主副本节点。</span><span class="sxs-lookup"><span data-stu-id="a342e-113">Always upgrade/update the remote secondary replica nodes first, then local secondary replica nodes next, and the primary replica node last.</span></span>  
  
-   <span data-ttu-id="a342e-114">无法在正在升级的数据库中执行备份。</span><span class="sxs-lookup"><span data-stu-id="a342e-114">Backups cannot occur on a database that is in the process of being upgraded.</span></span>  <span data-ttu-id="a342e-115">在升级辅助副本之前，请将自动备份首选项配置为仅在主副本上运行备份。</span><span class="sxs-lookup"><span data-stu-id="a342e-115">Prior to upgrading the secondary replicas, configure the automated backup preference to run backups only on the primary replica.</span></span>  <span data-ttu-id="a342e-116">在升级主副本之前，修改此设置以仅对辅助副本运行备份。</span><span class="sxs-lookup"><span data-stu-id="a342e-116">Prior to upgrading the primary replica, modify this setting to run backups only on the secondary replicas.</span></span>  
  
-   <span data-ttu-id="a342e-117">要防止可用性组在升级/更新过程中执行意外的故障转移，请在开始前从所有同步提交副本中删除可用性故障转移。</span><span class="sxs-lookup"><span data-stu-id="a342e-117">To prevent the availability group from unintended failovers during the upgrade/update process, remove availability failover from all synchronous-commit replicas before you begin.</span></span>  
  
-   <span data-ttu-id="a342e-118">在没有首先将可用性组故障转移到具有辅助副本的已升级节点上前，不要升级主副本节点。</span><span class="sxs-lookup"><span data-stu-id="a342e-118">Do not upgrade the primary replica node before failing over the availability group to an upgraded node with a secondary replica first.</span></span> <span data-ttu-id="a342e-119">否则，在主副本上进行升级/更新期间，客户端应用程序的停机时间可能更长。</span><span class="sxs-lookup"><span data-stu-id="a342e-119">Otherwise, client applications may suffer extended downtime during the upgrade/update on the primary replica.</span></span>  
  
-   <span data-ttu-id="a342e-120">始终将可用性组故障转移到同步提交的辅助副本节点。</span><span class="sxs-lookup"><span data-stu-id="a342e-120">Always fail over the availability group to a synchronous-commit secondary replica node.</span></span> <span data-ttu-id="a342e-121">如果故障转移到异步提交的辅助副本，数据库将发生数据丢失，且数据移动自动挂起，直到您手动恢复数据移动。</span><span class="sxs-lookup"><span data-stu-id="a342e-121">If you fail over to an asynchronous-commit secondary replica, the databases will suffer data loss, and data movement is automatically suspended until you manually resume data movement.</span></span>  
  
-   <span data-ttu-id="a342e-122">在没有升级/更新任何其他辅助副本节点前，不要升级/更新主副本节点。</span><span class="sxs-lookup"><span data-stu-id="a342e-122">Do not upgrade/update the primary replica node before upgrading/updating any other secondary replica nodes.</span></span> <span data-ttu-id="a342e-123">已升级的主副本不再将日志传送到尚未升级到同一版本的任何辅助副本。</span><span class="sxs-lookup"><span data-stu-id="a342e-123">An upgraded primary replica can no longer ship logs to any secondary replica that has not yet been upgraded to the same version.</span></span> <span data-ttu-id="a342e-124">在挂起到辅助副本的数据移动时，对于该副本无法进行自动故障转移，且您的可用性数据库很可能发生数据丢失。</span><span class="sxs-lookup"><span data-stu-id="a342e-124">When data movement to a secondary replica is suspended, no automatic failover can occur for that replica, and your availability databases are vulnerable to data loss.</span></span>  
  
-   <span data-ttu-id="a342e-125">在故障转移可用性组前，请验证故障转移目标的同步状态为 SYNCHRONIZED。</span><span class="sxs-lookup"><span data-stu-id="a342e-125">Before failing over an availability group, verify that the synchronization state of the failover target is SYNCHRONIZED.</span></span>  
  
## <a name="rolling-upgradeupdate-process"></a><span data-ttu-id="a342e-126">滚动升级/更新过程</span><span class="sxs-lookup"><span data-stu-id="a342e-126">Rolling Upgrade/Update Process</span></span>  
 <span data-ttu-id="a342e-127">实际上，确切的过程取决于一些因素，如可用性组的部署拓扑和每个副本的提交模式。</span><span class="sxs-lookup"><span data-stu-id="a342e-127">In practice, the exact process will depend on factors such as the deployment topology of your availability groups and the commit mode of each replica.</span></span> <span data-ttu-id="a342e-128">但是在最简单的方案中，滚动升级/更新是涉及以下步骤的多阶段过程：</span><span class="sxs-lookup"><span data-stu-id="a342e-128">But in the simplest scenario, a rolling upgrade/update is a multi-stage process that in its simplest form involves the following steps:</span></span>  
  
 <span data-ttu-id="a342e-129">![HADR 方案中的可用性组升级](../../media/alwaysonupgrade-ag-hadr.gif "HADR 方案中的可用性组升级")</span><span class="sxs-lookup"><span data-stu-id="a342e-129">![Availability Group Upgrade in HADR Scenario](../../media/alwaysonupgrade-ag-hadr.gif "Availability Group Upgrade in HADR Scenario")</span></span>  
  
1.  <span data-ttu-id="a342e-130">在所有同步提交的副本上删除自动故障转移</span><span class="sxs-lookup"><span data-stu-id="a342e-130">Remove automatic failover on all synchronous-commit replicas</span></span>  
  
2.  <span data-ttu-id="a342e-131">升级/更新运行异步提交辅助副本的所有远程服务器实例</span><span class="sxs-lookup"><span data-stu-id="a342e-131">Upgrade/update all remote server instances running asynchronous-commit secondary replicas</span></span>  
  
3.  <span data-ttu-id="a342e-132">升级/更新当前未运行主副本的所有本地服务器实例</span><span class="sxs-lookup"><span data-stu-id="a342e-132">Upgrade/update the all local server instances that are not currently running the primary replica</span></span>  
  
4.  <span data-ttu-id="a342e-133">将可用性组手动故障转移到同步提交的辅助副本</span><span class="sxs-lookup"><span data-stu-id="a342e-133">Manually fail over the availability group to a synchronous-commit secondary replica</span></span>  
  
5.  <span data-ttu-id="a342e-134">升级/更新以前承载主副本的服务器实例</span><span class="sxs-lookup"><span data-stu-id="a342e-134">Upgrade/update the server instance that formerly hosted the primary replica</span></span>  
  
6.  <span data-ttu-id="a342e-135">根据需要配置自动故障转移伙伴</span><span class="sxs-lookup"><span data-stu-id="a342e-135">Configure automatic failover partners as desired</span></span>  
  
 <span data-ttu-id="a342e-136">如果需要，您可以执行额外的手动故障转移以将可用性组恢复到原始配置。</span><span class="sxs-lookup"><span data-stu-id="a342e-136">If necessary, you can perform an extra manual failover to return the availability group to its original configuration.</span></span>  
  
## <a name="availability-group-with-one-remote-secondary-replica"></a><span data-ttu-id="a342e-137">具有一个远程辅助副本的可用性组</span><span class="sxs-lookup"><span data-stu-id="a342e-137">Availability Group with One Remote Secondary Replica</span></span>  
 <span data-ttu-id="a342e-138">如果您仅为灾难恢复部署了一个可用性组，可能需要将该可用性组故障转移到异步提交的辅助副本。</span><span class="sxs-lookup"><span data-stu-id="a342e-138">If you have deployed an availability group only for disaster recovery, you may need to fail over the availability group to an asynchronous-commit secondary replica.</span></span> <span data-ttu-id="a342e-139">这样的配置如下图所示：</span><span class="sxs-lookup"><span data-stu-id="a342e-139">Such configuration is illustrated by the following figure:</span></span>  
  
 <span data-ttu-id="a342e-140">![DR 方案中的可用性组升级](../../media/agupgrade-ag-dr.gif "DR 方案中的可用性组升级")</span><span class="sxs-lookup"><span data-stu-id="a342e-140">![Availability Group Upgrade in DR Scenario](../../media/agupgrade-ag-dr.gif "Availability Group Upgrade in DR Scenario")</span></span>  
  
 <span data-ttu-id="a342e-141">在此情况下，在滚动升级/更新期间必须将可用性组故障转移到异步提交的辅助副本。</span><span class="sxs-lookup"><span data-stu-id="a342e-141">In this situation, you must fail over the availability group to the asynchronous-commit secondary replica during the rolling upgrade/update.</span></span> <span data-ttu-id="a342e-142">要防止数据丢失，请在故障转移可用性组前将提交模式更改为同步提交并等待辅助副本同步。</span><span class="sxs-lookup"><span data-stu-id="a342e-142">To prevent data loss, change the commit mode to synchronous commit and wait for the secondary replica to be synchronized before you fail over the availability group.</span></span> <span data-ttu-id="a342e-143">因此，滚动升级/更新过程可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="a342e-143">Therefore, the rolling upgrade/update process may look as follows:</span></span>  
  
1.  <span data-ttu-id="a342e-144">升级/更新远程服务器</span><span class="sxs-lookup"><span data-stu-id="a342e-144">Upgrade/update the remote server</span></span>  
  
2.  <span data-ttu-id="a342e-145">将提交模式更改为同步提交</span><span class="sxs-lookup"><span data-stu-id="a342e-145">Change the commit mode to synchronous commit</span></span>  
  
3.  <span data-ttu-id="a342e-146">等待直到同步状态为 SYNCHRONIZED</span><span class="sxs-lookup"><span data-stu-id="a342e-146">Wait until synchronization state is SYNCHRONIZED</span></span>  
  
4.  <span data-ttu-id="a342e-147">将可用性组故障转移到远程站点</span><span class="sxs-lookup"><span data-stu-id="a342e-147">Fail over the availability group to the remote site</span></span>  
  
5.  <span data-ttu-id="a342e-148">升级/更新本地（主站点）服务器</span><span class="sxs-lookup"><span data-stu-id="a342e-148">Upgrade/update the local (primary site) server</span></span>  
  
6.  <span data-ttu-id="a342e-149">将可用性组故障转移到主站点</span><span class="sxs-lookup"><span data-stu-id="a342e-149">Fail over the availability group to the primary site</span></span>  
  
7.  <span data-ttu-id="a342e-150">将提交模式更改为异步提交</span><span class="sxs-lookup"><span data-stu-id="a342e-150">Change the commit mode to asynchronous commit</span></span>  
  
 <span data-ttu-id="a342e-151">因为同步提交模式不是用于数据同步到远程站点的建议设置，客户端应用程序可能发现在设置更改后，数据库延迟时间立即增加。</span><span class="sxs-lookup"><span data-stu-id="a342e-151">Since the synchronous-commit mode is not a recommended setting for data synchronization to a remote site, client applications may notice an immediate increase in database latency after the setting change.</span></span> <span data-ttu-id="a342e-152">此外，执行故障转移将导致丢弃所有未确认的日志消息。</span><span class="sxs-lookup"><span data-stu-id="a342e-152">Moreover, performing a failover will cause all unacknowledged log messages to be discarded.</span></span> <span data-ttu-id="a342e-153">由于两个站点之间的高网络延迟，丢弃的日志消息量可能很大，这导致客户端经历大量事务失败。</span><span class="sxs-lookup"><span data-stu-id="a342e-153">The amount of discarded log messages can be quite large due to the high network latency between the two sites, causing clients to experience a high volume of transactional failure.</span></span> <span data-ttu-id="a342e-154">您可以通过执行以下操作之一来尽量降低对客户端应用程序的影响：</span><span class="sxs-lookup"><span data-stu-id="a342e-154">You can minimize impact to client applications by doing the following:</span></span>  
  
-   <span data-ttu-id="a342e-155">在低客户端流量期间认真选择一个维护窗口</span><span class="sxs-lookup"><span data-stu-id="a342e-155">Carefully select a maintenance window during low client traffic</span></span>  
  
-   <span data-ttu-id="a342e-156">在主站点上升级/更新 SQL Server 时，将可用性模式改回异步提交，在准备好再次故障转移到主站点时再将其恢复为同步提交</span><span class="sxs-lookup"><span data-stu-id="a342e-156">While upgrading/updating SQL Server on the primary site, change the availability mode back to asynchronous commit, then revert to synchronous commit when you are ready to fail over to the primary site again</span></span>  
  
## <a name="availability-group-with-failover-cluster-instance-nodes"></a><span data-ttu-id="a342e-157">具有故障转移群集实例节点的可用性组</span><span class="sxs-lookup"><span data-stu-id="a342e-157">Availability Group with Failover Cluster Instance Nodes</span></span>  
 <span data-ttu-id="a342e-158">如果可用性组包含故障转移群集实例 (FCI) 节点，您应在升级/更新活动节点前升级/更新不活动的节点。</span><span class="sxs-lookup"><span data-stu-id="a342e-158">If an availability group contains failover cluster instance (FCI) nodes, you should upgrade/update the inactive nodes before you upgrade/update the active nodes.</span></span> <span data-ttu-id="a342e-159">下图显示一个常见的可用性组方案（它包含 FCI 用于本地高可用性且用于远程灾难恢复的 FCI 之间采用异步提交模式）和升级顺序。</span><span class="sxs-lookup"><span data-stu-id="a342e-159">The figure below illustrates a common availability group scenario with FCIs for local high availability and asynchronous commit between the FCIs for remote disaster recovery, and the upgrade sequence.</span></span>  
  
 <span data-ttu-id="a342e-160">![具有 FCI 的可用性组升级](../../media/agupgrade-ag-fci-dr.gif "具有 FCI 的可用性组升级")</span><span class="sxs-lookup"><span data-stu-id="a342e-160">![Availability Group Upgrade with FCIs](../../media/agupgrade-ag-fci-dr.gif "Availability Group Upgrade with FCIs")</span></span>  
  
1.  <span data-ttu-id="a342e-161">升级/更新 REMOTE2</span><span class="sxs-lookup"><span data-stu-id="a342e-161">Upgrade/update REMOTE2</span></span>  
  
2.  <span data-ttu-id="a342e-162">将 FCI2 故障转移到 REMOTE2</span><span class="sxs-lookup"><span data-stu-id="a342e-162">Fail over FCI2 to REMOTE2</span></span>  
  
3.  <span data-ttu-id="a342e-163">升级/更新 REMOTE1</span><span class="sxs-lookup"><span data-stu-id="a342e-163">Upgrade/update REMOTE1</span></span>  
  
4.  <span data-ttu-id="a342e-164">升级/更新 PRIMARY2</span><span class="sxs-lookup"><span data-stu-id="a342e-164">Upgrade/update PRIMARY2</span></span>  
  
5.  <span data-ttu-id="a342e-165">将 FCI1 故障转移到 PRIMARY2</span><span class="sxs-lookup"><span data-stu-id="a342e-165">Fail over FCI1 to PRIMARY2</span></span>  
  
6.  <span data-ttu-id="a342e-166">升级/更新 PRIMARY1</span><span class="sxs-lookup"><span data-stu-id="a342e-166">Upgrade/update PRIMARY1</span></span>  
  
## <a name="upgradeupdate-sql-server-instances-with-multiple-availability-groups"></a><span data-ttu-id="a342e-167">升级/更新具有多个可用性组的 SQL Server 实例</span><span class="sxs-lookup"><span data-stu-id="a342e-167">Upgrade/Update SQL Server Instances with Multiple Availability Groups</span></span>  
 <span data-ttu-id="a342e-168">如果您正在单独的服务器节点（活动/活动配置）上运行包含主副本的多个可用性组，则升级/更新路径涉及更多故障转移步骤以在过程中保持高可用性。</span><span class="sxs-lookup"><span data-stu-id="a342e-168">If you are running multiple availability groups with primary replicas on separate server nodes (an Active/Active configuration), the upgrade/update path involves more failover steps to preserve high availability in the process.</span></span> <span data-ttu-id="a342e-169">假定您正在三个服务器节点上运行三个可用性组（如下表所示），所有辅助副本正在同步提交模式下运行。</span><span class="sxs-lookup"><span data-stu-id="a342e-169">Suppose you are running three availability groups on three server nodes as shown in the following table, and all secondary replicas are running in synchronous-commit mode.</span></span>  
  
|<span data-ttu-id="a342e-170">可用性组</span><span class="sxs-lookup"><span data-stu-id="a342e-170">Availability Group</span></span>|<span data-ttu-id="a342e-171">Node1</span><span class="sxs-lookup"><span data-stu-id="a342e-171">Node1</span></span>|<span data-ttu-id="a342e-172">Node2</span><span class="sxs-lookup"><span data-stu-id="a342e-172">Node2</span></span>|<span data-ttu-id="a342e-173">Node3</span><span class="sxs-lookup"><span data-stu-id="a342e-173">Node3</span></span>|  
|------------------------|-----------|-----------|-----------|  
|<span data-ttu-id="a342e-174">AG1</span><span class="sxs-lookup"><span data-stu-id="a342e-174">AG1</span></span>|<span data-ttu-id="a342e-175">主</span><span class="sxs-lookup"><span data-stu-id="a342e-175">Primary</span></span>|||  
|<span data-ttu-id="a342e-176">AG2</span><span class="sxs-lookup"><span data-stu-id="a342e-176">AG2</span></span>||<span data-ttu-id="a342e-177">主</span><span class="sxs-lookup"><span data-stu-id="a342e-177">Primary</span></span>||  
|<span data-ttu-id="a342e-178">AG3</span><span class="sxs-lookup"><span data-stu-id="a342e-178">AG3</span></span>|||<span data-ttu-id="a342e-179">主</span><span class="sxs-lookup"><span data-stu-id="a342e-179">Primary</span></span>|  
  
 <span data-ttu-id="a342e-180">按以下顺序执行负载平衡的滚动升级/更新可能在您的情况下是合适的：</span><span class="sxs-lookup"><span data-stu-id="a342e-180">It may be appropriate in your situation to perform a load-balanced rolling upgrade/update in the following sequence:</span></span>  
  
1.  <span data-ttu-id="a342e-181">将 AG2 故障转移到 Node3（以空出 Node2）</span><span class="sxs-lookup"><span data-stu-id="a342e-181">Fail over AG2 to Node3 (to free up Node2)</span></span>  
  
2.  <span data-ttu-id="a342e-182">升级/更新 Node2</span><span class="sxs-lookup"><span data-stu-id="a342e-182">Upgrade/update Node2</span></span>  
  
3.  <span data-ttu-id="a342e-183">将 AG1 故障转移到 Node2（以空出 Node1）</span><span class="sxs-lookup"><span data-stu-id="a342e-183">Fail over AG1 to Node2 (to free up Node1)</span></span>  
  
4.  <span data-ttu-id="a342e-184">升级/更新 Node1</span><span class="sxs-lookup"><span data-stu-id="a342e-184">Upgrade/update Node1</span></span>  
  
5.  <span data-ttu-id="a342e-185">将 AG2 和 AG3 故障转移到 Node1（以空出 Node3）</span><span class="sxs-lookup"><span data-stu-id="a342e-185">Fail over both AG2 and AG3 to Node1 (to free up Node3)</span></span>  
  
6.  <span data-ttu-id="a342e-186">升级/更新 Node3</span><span class="sxs-lookup"><span data-stu-id="a342e-186">Upgrade/update Node3</span></span>  
  
7.  <span data-ttu-id="a342e-187">将 AG3 故障转移到 Node3</span><span class="sxs-lookup"><span data-stu-id="a342e-187">Fail over AG3 to Node3</span></span>  
  
 <span data-ttu-id="a342e-188">此升级/更新顺序具有每个可用性组小于两个故障转移的平均停机时间。</span><span class="sxs-lookup"><span data-stu-id="a342e-188">This upgrade/update sequence has an average downtime of less than two failovers per availability group.</span></span> <span data-ttu-id="a342e-189">最终配置如下表所示。</span><span class="sxs-lookup"><span data-stu-id="a342e-189">The resulting configuration is shown in the table below.</span></span>  
  
|<span data-ttu-id="a342e-190">可用性组</span><span class="sxs-lookup"><span data-stu-id="a342e-190">Availability Group</span></span>|<span data-ttu-id="a342e-191">Node1</span><span class="sxs-lookup"><span data-stu-id="a342e-191">Node1</span></span>|<span data-ttu-id="a342e-192">Node2</span><span class="sxs-lookup"><span data-stu-id="a342e-192">Node2</span></span>|<span data-ttu-id="a342e-193">Node3</span><span class="sxs-lookup"><span data-stu-id="a342e-193">Node3</span></span>|  
|------------------------|-----------|-----------|-----------|  
|<span data-ttu-id="a342e-194">AG1</span><span class="sxs-lookup"><span data-stu-id="a342e-194">AG1</span></span>||<span data-ttu-id="a342e-195">主</span><span class="sxs-lookup"><span data-stu-id="a342e-195">Primary</span></span>||  
|<span data-ttu-id="a342e-196">AG2</span><span class="sxs-lookup"><span data-stu-id="a342e-196">AG2</span></span>|<span data-ttu-id="a342e-197">主</span><span class="sxs-lookup"><span data-stu-id="a342e-197">Primary</span></span>|||  
|<span data-ttu-id="a342e-198">AG3</span><span class="sxs-lookup"><span data-stu-id="a342e-198">AG3</span></span>|||<span data-ttu-id="a342e-199">主</span><span class="sxs-lookup"><span data-stu-id="a342e-199">Primary</span></span>|  
  
 <span data-ttu-id="a342e-200">根据您的特定实现，您的升级/更新路径可能不同，客户端应用程序经历的停机时间也可能不同。</span><span class="sxs-lookup"><span data-stu-id="a342e-200">Based on your specific implementation, your upgrade/update path may vary, and the downtime that client applications experience may vary as well.</span></span>  
  
  
