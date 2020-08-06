---
title: 执行可用性组的计划手动故障转移 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.manualfailover.f1
helpviewer_keywords:
- Availability Groups [SQL Server], failover
- failover [SQL Server], AlwaysOn Availability Groups
ms.assetid: 419f655d-3f9a-4e7d-90b9-f0bab47b3178
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c62942eaa8f4ab4472bca5c7123e5999eb069216
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690810"
---
# <a name="perform-a-planned-manual-failover-of-an-availability-group-sql-server"></a><span data-ttu-id="99d7c-102">执行可用性组的计划手动故障转移 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="99d7c-102">Perform a Planned Manual Failover of an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="99d7c-103">本主题介绍如何通过在中使用、或 PowerShell 来执行无数据丢失的手动故障转移 (AlwaysOn 可用性组上的*计划的手动故障转移*) [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../../includes/tsql-md.md)] [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="99d7c-103">This topic describes how to perform a manual failover without data loss (a *planned manual failover*) on an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="99d7c-104">可用性组在可用性副本级别进行故障转移。</span><span class="sxs-lookup"><span data-stu-id="99d7c-104">An availability group fails over at the level of an availability replica.</span></span> <span data-ttu-id="99d7c-105">计划的手动故障转移（类似于任何 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 故障转移）将辅助副本转换为主角色，同时将以前的主副本转换为辅助角色。</span><span class="sxs-lookup"><span data-stu-id="99d7c-105">A planned manual failover, like any [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] failover, transitions a secondary replica to primary role and, concurrently, transitions the former primary replica to the secondary role.</span></span>  
  
 <span data-ttu-id="99d7c-106">仅当主副本和目标辅助副本在同步提交模式下运行且当前同步时，才支持计划的手动故障转移，这种故障转移保留加入到目标辅助副本上的可用性组的辅助数据库中的所有数据。</span><span class="sxs-lookup"><span data-stu-id="99d7c-106">A planned manual failover, which is supported only when the primary replica and the target secondary replica are running in synchronous-commit mode and are currently synchronized, preserves all the data in the secondary databases that are joined to the availability group on the target secondary replica.</span></span> <span data-ttu-id="99d7c-107">一旦以前的主副本转换为辅助角色，其数据库将变成辅助数据库，并开始与新的主数据库进行同步。</span><span class="sxs-lookup"><span data-stu-id="99d7c-107">Once the former primary replica transitions to the secondary role, its databases become secondary databases and begin synchronizing with the new primary databases.</span></span> <span data-ttu-id="99d7c-108">在将其全部转换为 SYNCHRONIZED 状态之后，新的辅助副本将变成适于充当将来计划的手动故障转移的目标。</span><span class="sxs-lookup"><span data-stu-id="99d7c-108">After they all transition into the SYNCHRONIZED state, the new secondary replica becomes eligible to serve as the target of a future planned manual failover.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="99d7c-109">如果辅助副本和主副本都配置为自动故障转移模式，则一旦辅助副本同步，该副本还可以充当自动故障转移的目标。</span><span class="sxs-lookup"><span data-stu-id="99d7c-109">If the secondary and primary replicas are both configured for automatic failover mode, once the secondary replica is synchronized, it can also serve as the target for an automatic failover.</span></span> <span data-ttu-id="99d7c-110">有关详细信息，请参阅[可用性模式（AlwaysOn 可用性组）](availability-modes-always-on-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="99d7c-110">For more information, see [Availability Modes &#40;AlwaysOn Availability Groups&#41;](availability-modes-always-on-availability-groups.md).</span></span>  
  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="99d7c-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="99d7c-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="99d7c-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="99d7c-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="99d7c-113">故障转移命令将在目标辅助副本接受它之后立即返回。</span><span class="sxs-lookup"><span data-stu-id="99d7c-113">A failover command returns as soon as the target secondary replica has accepted the command.</span></span> <span data-ttu-id="99d7c-114">但是，在可用性组完成故障转移之后，数据库恢复操作将以异步方式执行。</span><span class="sxs-lookup"><span data-stu-id="99d7c-114">However, database recovery occurs asynchronously after the availability group has finished failing over.</span></span>  
  
-   <span data-ttu-id="99d7c-115">故障转移时，不维护可用性组中数据库间的跨数据库一致性。</span><span class="sxs-lookup"><span data-stu-id="99d7c-115">Cross-database consistency across databases within the availability group is not maintained on failover.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="99d7c-116">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 不支持跨数据库事务和分布式事务。</span><span class="sxs-lookup"><span data-stu-id="99d7c-116">Cross-database transactions and distributed transactions are not supported by [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].</span></span> <span data-ttu-id="99d7c-117">有关详细信息，请参阅[数据库镜像或 AlwaysOn 可用性组不支持跨数据库事务 (SQL Server)](transactions-always-on-availability-and-database-mirroring.md)。</span><span class="sxs-lookup"><span data-stu-id="99d7c-117">For more information, see [Cross-Database Transactions Not Supported For Database Mirroring or AlwaysOn Availability Groups &#40;SQL Server&#41;](transactions-always-on-availability-and-database-mirroring.md).</span></span>  
  
###  <a name="prerequisites-and-restrictions"></a><a name="Prerequisites"></a> <span data-ttu-id="99d7c-118">先决条件和限制</span><span class="sxs-lookup"><span data-stu-id="99d7c-118">Prerequisites and Restrictions</span></span>  
  
-   <span data-ttu-id="99d7c-119">目标辅助副本和主副本必须同时在同步提交可用性模式下运行。</span><span class="sxs-lookup"><span data-stu-id="99d7c-119">The target secondary replica and the primary replica must both be running in synchronous-commit availability mode.</span></span>  
  
-   <span data-ttu-id="99d7c-120">目标辅助副本当前必须与主副本同步。</span><span class="sxs-lookup"><span data-stu-id="99d7c-120">The target secondary replica must currently be synchronized with the primary replica.</span></span> <span data-ttu-id="99d7c-121">这要求此辅助副本上的所有辅助数据库必须已加入到可用性组，并与其对应的主数据库同步（即本地辅助数据库必须为 SYNCHRONIZED）。</span><span class="sxs-lookup"><span data-stu-id="99d7c-121">This requires that all the secondary databases on this secondary replica must have been joined to the availability group and be synchronized with their corresponding primary databases (that is, the local secondary databases must be SYNCHRONIZED).</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="99d7c-122">若要确定次要副本的故障转移就绪状态，请查询 [sys.dm_hadr_database_cluster_states](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-cluster-states-transact-sql) 动态管理视图中的 **is_failover_ready** 列，或查看 [AlwaysOn 组面板](use-the-always-on-dashboard-sql-server-management-studio.md)的“故障转移就绪”\*\*\*\* 列。</span><span class="sxs-lookup"><span data-stu-id="99d7c-122">To determine the failover readiness of an secondary replica, query the **is_failover_ready** column in the [sys.dm_hadr_database_cluster_states](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-cluster-states-transact-sql) dynamic management view, or look at the **Failover Readiness** column of the [AlwaysOn Group Dashboard](use-the-always-on-dashboard-sql-server-management-studio.md).</span></span>  
  
-   <span data-ttu-id="99d7c-123">只有目标辅助副本支持该任务。</span><span class="sxs-lookup"><span data-stu-id="99d7c-123">This task is supported only on the target secondary replica.</span></span> <span data-ttu-id="99d7c-124">您必须连接到承载目标辅助副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="99d7c-124">You must be connected to the server instance that hosts the target secondary replica.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="99d7c-125">Security</span><span class="sxs-lookup"><span data-stu-id="99d7c-125">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="99d7c-126">权限</span><span class="sxs-lookup"><span data-stu-id="99d7c-126">Permissions</span></span>  
 <span data-ttu-id="99d7c-127">对可用性组要求 ALTER AVAILABILITY GROUP 权限、CONTROL AVAILABILITY GROUP 权限、ALTER ANY AVAILABILITY GROUP 权限或 CONTROL SERVER 权限。</span><span class="sxs-lookup"><span data-stu-id="99d7c-127">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="99d7c-128">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="99d7c-128">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="99d7c-129">**对可用性组执行手动故障转移**</span><span class="sxs-lookup"><span data-stu-id="99d7c-129">**To manually fail over an availability group**</span></span>  
  
1.  <span data-ttu-id="99d7c-130">在对象资源管理器中，连接到承载着需要进行故障转移的可用性组的一个辅助副本的服务器实例，然后展开服务器树。</span><span class="sxs-lookup"><span data-stu-id="99d7c-130">In Object Explorer, connect to a server instance that hosts a secondary replica of the availability group that needs to be failed over, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="99d7c-131">依次展开 **“AlwaysOn 高可用性”** 节点和 **“可用性组”** 节点。</span><span class="sxs-lookup"><span data-stu-id="99d7c-131">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="99d7c-132">右键单击要进行故障转移的可用性组，然后选择“故障转移”  命令。</span><span class="sxs-lookup"><span data-stu-id="99d7c-132">Right-click the availability group to be failed over, and select the **Failover** command.</span></span>  
  
4.  <span data-ttu-id="99d7c-133">这将启动“故障转移可用性组向导”。</span><span class="sxs-lookup"><span data-stu-id="99d7c-133">This launches the Failover Availability Group Wizard.</span></span> <span data-ttu-id="99d7c-134">有关详细信息，请参阅本主题后面的 [使用故障转移可用性组向导 (SQL Server Management Studio)](use-the-fail-over-availability-group-wizard-sql-server-management-studio.md)或 PowerShell 对 AlwaysOn 可用性组执行强制故障转移（可能会丢失数据）。</span><span class="sxs-lookup"><span data-stu-id="99d7c-134">For more information, see [Use the Fail Over Availability Group Wizard &#40;SQL Server Management Studio&#41;](use-the-fail-over-availability-group-wizard-sql-server-management-studio.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="99d7c-135">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="99d7c-135">Using Transact-SQL</span></span>  
 <span data-ttu-id="99d7c-136">**对可用性组执行手动故障转移**</span><span class="sxs-lookup"><span data-stu-id="99d7c-136">**To manually fail over an availability group**</span></span>  
  
1.  <span data-ttu-id="99d7c-137">连接到承载目标辅助副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="99d7c-137">Connect to the server instance that hosts the target secondary replica.</span></span>  
  
2.  <span data-ttu-id="99d7c-138">按如下所示使用 [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) 语句：</span><span class="sxs-lookup"><span data-stu-id="99d7c-138">Use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) statement, as follows:</span></span>  
  
     <span data-ttu-id="99d7c-139">ALTER AVAILABILITY GROUP *group_name* FAILOVER</span><span class="sxs-lookup"><span data-stu-id="99d7c-139">ALTER AVAILABILITY GROUP *group_name* FAILOVER</span></span>  
  
     <span data-ttu-id="99d7c-140">其中， *group_name* 是可用性组的名称。</span><span class="sxs-lookup"><span data-stu-id="99d7c-140">where *group_name* is the name of the availability group.</span></span>  
  
     <span data-ttu-id="99d7c-141">下面的示例将*MyAg*可用性组手动故障转移到连接的辅助副本。</span><span class="sxs-lookup"><span data-stu-id="99d7c-141">The following example manually fails over the *MyAg* availability group to the connected secondary replica.</span></span>  
  
    ```sql
    ALTER AVAILABILITY GROUP MyAg FAILOVER;  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="99d7c-142">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="99d7c-142">Using PowerShell</span></span>  
 <span data-ttu-id="99d7c-143">**对可用性组执行手动故障转移**</span><span class="sxs-lookup"><span data-stu-id="99d7c-143">**To manually fail over an availability group**</span></span>  
  
1.  <span data-ttu-id="99d7c-144">将目录 (`cd`) 更改为承载目标辅助副本的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="99d7c-144">Change directory (`cd`) to the server instance that hosts the target secondary replica.</span></span>  
  
2.  <span data-ttu-id="99d7c-145">使用 `Switch-SqlAvailabilityGroup` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="99d7c-145">Use the `Switch-SqlAvailabilityGroup` cmdlet.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="99d7c-146">若要查看 cmdlet 的语法，请在 `Get-Help` PowerShell 环境中使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] cmdlet。</span><span class="sxs-lookup"><span data-stu-id="99d7c-146">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] PowerShell environment.</span></span> <span data-ttu-id="99d7c-147">有关详细信息，请参阅 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="99d7c-147">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
     <span data-ttu-id="99d7c-148">下面的示例将*MyAg*可用性组手动故障转移到具有指定路径的辅助副本。</span><span class="sxs-lookup"><span data-stu-id="99d7c-148">The following example manually fails over the *MyAg* availability group to the secondary replica with the specified path.</span></span>  
  
    ```powershell
    Switch-SqlAvailabilityGroup -Path SQLSERVER:\Sql\SecondaryServer\InstanceName\AvailabilityGroups\MyAg  
    ```  
  
 <span data-ttu-id="99d7c-149">**设置和使用 SQL Server PowerShell 提供程序**</span><span class="sxs-lookup"><span data-stu-id="99d7c-149">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="99d7c-150">SQL Server PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="99d7c-150">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
-   [<span data-ttu-id="99d7c-151">Get Help SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="99d7c-151">Get Help SQL Server PowerShell</span></span>](../../../powershell/sql-server-powershell.md)  
  
##  <a name="follow-up-after-manually-failing-over-an-availability-group"></a><a name="FollowUp"></a><span data-ttu-id="99d7c-152">跟进：在对可用性组进行手动故障转移后</span><span class="sxs-lookup"><span data-stu-id="99d7c-152">Follow Up: After Manually Failing Over an Availability Group</span></span>  
 <span data-ttu-id="99d7c-153">如果您故障转移到可用性组的 [!INCLUDE[ssFosAuto](../../../includes/ssfosauto-md.md)] 之外，则调整 WSFC 节点的仲裁投票以反映新的可用性组配置。</span><span class="sxs-lookup"><span data-stu-id="99d7c-153">If you failed over outside of the [!INCLUDE[ssFosAuto](../../../includes/ssfosauto-md.md)] of the availability group, adjust the quorum votes of the WSFC nodes to reflect your new availability group configuration.</span></span> <span data-ttu-id="99d7c-154">有关详细信息，请参阅 [Windows Server 故障转移群集 (WSFC) 与 SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="99d7c-154">For more information, see [Windows Server Failover Clustering &#40;WSFC&#41; with SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99d7c-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="99d7c-155">See Also</span></span>  
 <span data-ttu-id="99d7c-156">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="99d7c-156">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="99d7c-157">[故障转移和故障转移模式 &#40;AlwaysOn 可用性组&#41;](failover-and-failover-modes-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="99d7c-157">[Failover and Failover Modes &#40;AlwaysOn Availability Groups&#41;](failover-and-failover-modes-always-on-availability-groups.md) </span></span>  
 [<span data-ttu-id="99d7c-158">执行可用性组的强制手动故障转移 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="99d7c-158">Perform a Forced Manual Failover of an Availability Group &#40;SQL Server&#41;</span></span>](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)  
