---
title: 在无仲裁情况下强制启动 WSFC 群集 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], WSFC clusters
- quorum [SQL Server], AlwaysOn and WSFC quorum
ms.assetid: 4a121375-7424-4444-b876-baefa8fe9015
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b6f2110b706de015d0c7b19475b335908c118267
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586258"
---
# <a name="force-a-wsfc-cluster-to-start-without-a-quorum"></a><span data-ttu-id="f0bdb-102">在无仲裁情况下强制启动 WSFC 群集</span><span class="sxs-lookup"><span data-stu-id="f0bdb-102">Force a WSFC Cluster to Start Without a Quorum</span></span>
  <span data-ttu-id="f0bdb-103">本主题说明如何在无仲裁情况下强制启动 Windows Server 故障转移群集 (WSFC) 群集节点。</span><span class="sxs-lookup"><span data-stu-id="f0bdb-103">This topic describes how to force a Windows Server Failover Clustering (WSFC) cluster node to start without a quorum.</span></span>  <span data-ttu-id="f0bdb-104">在灾难恢复和多子网方案中，可能需要它来为 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 故障转移群集实例恢复数据和完全重建高可用性。</span><span class="sxs-lookup"><span data-stu-id="f0bdb-104">This may be required in disaster recovery and multi-subnet scenarios to recover data and fully re-establish high-availability for [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Failover Cluster Instances.</span></span>  
  
-   <span data-ttu-id="f0bdb-105">**准备工作：**  [建议](#Recommendations)、[安全性](#Security)</span><span class="sxs-lookup"><span data-stu-id="f0bdb-105">**Before you start:**  [Recommendations](#Recommendations), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="f0bdb-106">**若要在无仲裁情况下强制启动群集，请使用：**  [使用故障转移群集管理器](#FailoverClusterManagerProcedure)、[使用 Powershell](#PowerShellProcedure)、[使用 Net.exe](#CommandPromptProcedure)</span><span class="sxs-lookup"><span data-stu-id="f0bdb-106">**To force a cluster to start without a quorum using:**  [Using Failover Cluster Manager](#FailoverClusterManagerProcedure), [Using Powershell](#PowerShellProcedure), [Using Net.exe](#CommandPromptProcedure)</span></span>  
  
-   <span data-ttu-id="f0bdb-107">**跟进：**  [跟进：在无仲裁情况下强制启动群集后](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="f0bdb-107">**Follow up:**  [Follow Up: After Forcing Cluster to Start without a Quorum](#FollowUp)</span></span>  
  
##  <a name="before-you-start"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f0bdb-108">开始之前</span><span class="sxs-lookup"><span data-stu-id="f0bdb-108">Before You Start</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="f0bdb-109">建议</span><span class="sxs-lookup"><span data-stu-id="f0bdb-109">Recommendations</span></span>  
 <span data-ttu-id="f0bdb-110">除了明确指出的情况外，从 WSFC 群集中的任意节点执行时，本主题中的步骤都应适用。</span><span class="sxs-lookup"><span data-stu-id="f0bdb-110">Except where explicitly directed, the procedures in this topic should work if you execute them from any node in the WSFC cluster.</span></span>  <span data-ttu-id="f0bdb-111">但是，通过从要在无仲裁情况下强制启动的节点执行这些步骤，可能获得更好的效果并避免网络问题。</span><span class="sxs-lookup"><span data-stu-id="f0bdb-111">However, you may obtain better results, and avoid networking issues, by executing these steps from the node that you intend to force to start without a quorum.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f0bdb-112">Security</span><span class="sxs-lookup"><span data-stu-id="f0bdb-112">Security</span></span>  
 <span data-ttu-id="f0bdb-113">用户必须是一个域帐户，该帐户是每个 WSFC 群集节点上本地 Administrators 组的成员。</span><span class="sxs-lookup"><span data-stu-id="f0bdb-113">The user must be a domain account that is member of the local Administrators group on each node of the WSFC cluster.</span></span>  
  
##  <a name="using-failover-cluster-manager"></a><a name="FailoverClusterManagerProcedure"></a> <span data-ttu-id="f0bdb-114">使用故障转移群集管理器</span><span class="sxs-lookup"><span data-stu-id="f0bdb-114">Using Failover Cluster Manager</span></span>  
  
##### <a name="to-force-a-cluster-to-start-without-a-quorum"></a><span data-ttu-id="f0bdb-115">在无仲裁情况下强制启动群集</span><span class="sxs-lookup"><span data-stu-id="f0bdb-115">To force a cluster to start without a quorum</span></span>  
  
1.  <span data-ttu-id="f0bdb-116">打开故障转移群集管理器并连接到所需的群集节点，以强制联机。</span><span class="sxs-lookup"><span data-stu-id="f0bdb-116">Open a Failover Cluster Manager and connect to the desired cluster node to force online.</span></span>  
  
2.  <span data-ttu-id="f0bdb-117">在 "**操作**" 窗格中，单击 "**强制群集启动**"，然后单击 **"是" "强制群集启动**"。</span><span class="sxs-lookup"><span data-stu-id="f0bdb-117">In the **Actions** pane, click **Force Cluster Start**, and then click **Yes - Force my cluster to start**.</span></span>  
  
3.  <span data-ttu-id="f0bdb-118">在左窗格中，在 **“故障转移群集管理器”** 树中单击该群集名称。</span><span class="sxs-lookup"><span data-stu-id="f0bdb-118">In the left pane, in the **Failover Cluster Manager** tree, click the cluster name.</span></span>  
  
4.  <span data-ttu-id="f0bdb-119">在摘要窗格中，确认当前 **“仲裁配置”** 值为  **“警告: 群集正在 ForceQuorum 状态下运行”**。</span><span class="sxs-lookup"><span data-stu-id="f0bdb-119">In the summary pane, confirm that the current **Quorum Configuration** value is:  **Warning: Cluster is running in ForceQuorum state**.</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a><span data-ttu-id="f0bdb-120">使用 Powershell</span><span class="sxs-lookup"><span data-stu-id="f0bdb-120">Using Powershell</span></span>  
  
##### <a name="to-force-a-cluster-to-start-without-a-quorum"></a><span data-ttu-id="f0bdb-121">在无仲裁情况下强制启动群集</span><span class="sxs-lookup"><span data-stu-id="f0bdb-121">To force a cluster to start without a quorum</span></span>  
  
1.  <span data-ttu-id="f0bdb-122">通过 **“以管理员身份运行”** 启动提升的 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="f0bdb-122">Start an elevated Windows PowerShell via **Run as Administrator**.</span></span>  
  
2.  <span data-ttu-id="f0bdb-123">导入 `FailoverClusters` 模块以启用群集 commandlet。</span><span class="sxs-lookup"><span data-stu-id="f0bdb-123">Import the `FailoverClusters` module to enable cluster commandlets.</span></span>  
  
3.  <span data-ttu-id="f0bdb-124">使用 `Stop-ClusterNode` 以确保群集服务已停止。</span><span class="sxs-lookup"><span data-stu-id="f0bdb-124">Use `Stop-ClusterNode` to make sure that the cluster service is stopped.</span></span>  
  
4.  <span data-ttu-id="f0bdb-125">将 `Start-ClusterNode` 和 `-FixQuorum` 结合使用以强制启动群集服务。</span><span class="sxs-lookup"><span data-stu-id="f0bdb-125">Use `Start-ClusterNode` with `-FixQuorum` to force the cluster service to start.</span></span>  
  
5.  <span data-ttu-id="f0bdb-126">将 `Get-ClusterNode` 和 `-Propery NodeWieght = 1` 结合使用以设置确保节点是仲裁的投票成员的值。</span><span class="sxs-lookup"><span data-stu-id="f0bdb-126">Use `Get-ClusterNode` with `-Propery NodeWieght = 1` to set the value the guarantees that the node is a voting member of the quorum.</span></span>  
  
6.  <span data-ttu-id="f0bdb-127">以可读格式输出群集节点属性。</span><span class="sxs-lookup"><span data-stu-id="f0bdb-127">Output the cluster node properties in a readable format.</span></span>  
  
### <a name="example-powershell"></a><span data-ttu-id="f0bdb-128">示例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="f0bdb-128">Example (Powershell)</span></span>  
 <span data-ttu-id="f0bdb-129">下面的示例在无仲裁情况下强制启动 AlwaysOnSrv02 节点群集服务，设置 `NodeWeight = 1`，然后枚举新强制的节点的群集节点状态。</span><span class="sxs-lookup"><span data-stu-id="f0bdb-129">The following example forces the AlwaysOnSrv02 node cluster service to start without a quorum, sets the `NodeWeight = 1`, and then enumerates cluster node status from the newly forced node.</span></span>  
  
```powershell  
Import-Module FailoverClusters  
  
$node = "AlwaysOnSrv02"  
Stop-ClusterNode -Name $node  
Start-ClusterNode -Name $node -FixQuorum  
  
(Get-ClusterNode $node).NodeWeight = 1  
  
$nodes = Get-ClusterNode -Cluster $node  
$nodes | Format-Table -property NodeName, State, NodeWeight
```  
  
##  <a name="using-netexe"></a><a name="CommandPromptProcedure"></a> <span data-ttu-id="f0bdb-130">使用 Net.exe</span><span class="sxs-lookup"><span data-stu-id="f0bdb-130">Using Net.exe</span></span>  
  
### <a name="to-force-a-cluster-to-start-without-a-quorum"></a><span data-ttu-id="f0bdb-131">在无仲裁情况下强制启动群集</span><span class="sxs-lookup"><span data-stu-id="f0bdb-131">To force a cluster to start without a quorum</span></span>  
  
1.  <span data-ttu-id="f0bdb-132">使用远程桌面连接到所需的群集节点，以强制联机。</span><span class="sxs-lookup"><span data-stu-id="f0bdb-132">Use Remote Desktop to connect to the desired cluster node to force online.</span></span>  
  
2.  <span data-ttu-id="f0bdb-133">通过 **“以管理员身份运行”** 启动提升的命令提示符。</span><span class="sxs-lookup"><span data-stu-id="f0bdb-133">Start an elevated Command Prompt via **Run as Administrator**.</span></span>  
  
3.  <span data-ttu-id="f0bdb-134">使用 **net.exe** 以确保本地群集服务已停止。</span><span class="sxs-lookup"><span data-stu-id="f0bdb-134">Use **net.exe** to make sure that the local cluster service is stopped.</span></span>  
  
4.  <span data-ttu-id="f0bdb-135">将 **net.exe** 和 `/forcequorum` 结合使用以强制启动本地群集服务。</span><span class="sxs-lookup"><span data-stu-id="f0bdb-135">Use **net.exe** with `/forcequorum` to force the local cluster service to start.</span></span>  
  
### <a name="example-netexe"></a><span data-ttu-id="f0bdb-136">示例 (Net.exe)</span><span class="sxs-lookup"><span data-stu-id="f0bdb-136">Example (Net.exe)</span></span>  
 <span data-ttu-id="f0bdb-137">下面的示例在无仲裁情况下强制启动一个节点群集服务，设置 `NodeWeight = 1`，然后枚举新强制的节点的群集节点状态。</span><span class="sxs-lookup"><span data-stu-id="f0bdb-137">The following example forces a node cluster service to start without a quorum, sets the `NodeWeight = 1`, and then enumerates cluster node status from the newly forced node.</span></span>  
  
```cmd
net.exe stop clussvc  
net.exe start clussvc /forcequorum  
```  
  
##  <a name="follow-up-after-forcing-cluster-to-start-without-a-quorum"></a><a name="FollowUp"></a><span data-ttu-id="f0bdb-138">跟进：在无仲裁情况下强制启动群集后</span><span class="sxs-lookup"><span data-stu-id="f0bdb-138">Follow Up: After Forcing Cluster to Start without a Quorum</span></span>  
  
-   <span data-ttu-id="f0bdb-139">在使其他节点重新联机前，必须重新计算和重新配置 NodeWeight 值以正确构造新的仲裁。</span><span class="sxs-lookup"><span data-stu-id="f0bdb-139">You must re-evaluate and reconfigure NodeWeight values to correctly construct a new quorum before bringing other nodes back online.</span></span> <span data-ttu-id="f0bdb-140">否则，该群集可能再次脱机。</span><span class="sxs-lookup"><span data-stu-id="f0bdb-140">Otherwise, the cluster may go back offline again.</span></span>  
  
     <span data-ttu-id="f0bdb-141">有关详细信息，请参阅 [WSFC 仲裁模式和投票配置 (SQL Server)](wsfc-quorum-modes-and-voting-configuration-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="f0bdb-141">For more information, see [WSFC Quorum Modes and Voting Configuration &#40;SQL Server&#41;](wsfc-quorum-modes-and-voting-configuration-sql-server.md).</span></span>  
  
-   <span data-ttu-id="f0bdb-142">如果出现意外的仲裁失败，本主题所述的步骤仅仅是使 WSFC 群集重新联机中的一个步骤。</span><span class="sxs-lookup"><span data-stu-id="f0bdb-142">The procedures in this topic are only one step in bringing the WSFC cluster back online if an un-planned quorum failure were to occur.</span></span>  <span data-ttu-id="f0bdb-143">您可能还要执行其他步骤来阻止其他 WSFC 群集节点干扰新的仲裁配置。</span><span class="sxs-lookup"><span data-stu-id="f0bdb-143">You may also want to take additional steps to prevent other WSFC cluster nodes from interfering with the new quorum configuration.</span></span>  
  
-   <span data-ttu-id="f0bdb-144">其他 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 功能（如 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]、数据库镜像和日志传送）可能也需要执行后续操作来恢复数据和完全重建高可用性。</span><span class="sxs-lookup"><span data-stu-id="f0bdb-144">Other [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] features such as [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], database mirroring, and log shipping may also require subsequent actions to recover data and to fully re-establish high-availability.</span></span>  
  
     <span data-ttu-id="f0bdb-145">**有关详细信息：**</span><span class="sxs-lookup"><span data-stu-id="f0bdb-145">**For more information:**</span></span>  
  
     [<span data-ttu-id="f0bdb-146">执行可用性组的强制手动故障转移 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f0bdb-146">Perform a Forced Manual Failover of an Availability Group &#40;SQL Server&#41;</span></span>](../../../database-engine/availability-groups/windows/perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)  
  
     [<span data-ttu-id="f0bdb-147">在数据库镜像会话中强制服务 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f0bdb-147">Force Service in a Database Mirroring Session &#40;Transact-SQL&#41;</span></span>](../../../database-engine/database-mirroring/force-service-in-a-database-mirroring-session-transact-sql.md)  
  
     [<span data-ttu-id="f0bdb-148">故障转移到日志传送辅助服务器 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f0bdb-148">Fail Over to a Log Shipping Secondary &#40;SQL Server&#41;</span></span>](../../../database-engine/log-shipping/fail-over-to-a-log-shipping-secondary-sql-server.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="f0bdb-149">相关内容</span><span class="sxs-lookup"><span data-stu-id="f0bdb-149">Related Content</span></span>  
  
-   <span data-ttu-id="f0bdb-150">[查看故障转移群集的事件和日志](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772342(v=ws.11))</span><span class="sxs-lookup"><span data-stu-id="f0bdb-150">[View Events and Logs for a Failover Cluster](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772342(v=ws.11))</span></span>  
  
-   [<span data-ttu-id="f0bdb-151">Get-ClusterLog 故障转移群集 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="f0bdb-151">Get-ClusterLog Failover Cluster Cmdlet</span></span>](https://technet.microsoft.com/library/ee461045.aspx)  
  
## <a name="see-also"></a><span data-ttu-id="f0bdb-152">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f0bdb-152">See Also</span></span>  
 <span data-ttu-id="f0bdb-153">[通过强制仲裁 &#40;SQL Server 进行 WSFC 灾难恢复&#41;](wsfc-disaster-recovery-through-forced-quorum-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f0bdb-153">[WSFC Disaster Recovery through Forced Quorum &#40;SQL Server&#41;](wsfc-disaster-recovery-through-forced-quorum-sql-server.md) </span></span>  
 <span data-ttu-id="f0bdb-154">[配置群集仲裁 NodeWeight 设置](configure-cluster-quorum-nodeweight-settings.md) </span><span class="sxs-lookup"><span data-stu-id="f0bdb-154">[Configure Cluster Quorum NodeWeight Settings](configure-cluster-quorum-nodeweight-settings.md) </span></span>  
 <span data-ttu-id="f0bdb-155">[Windows PowerShell 中按任务焦点列出的故障转移群集 Cmdlet](https://technet.microsoft.com/library/ee619761\(WS.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="f0bdb-155">[Failover Cluster Cmdlets in Windows PowerShell Listed by Task Focus](https://technet.microsoft.com/library/ee619761\(WS.10\).aspx)</span></span>  
