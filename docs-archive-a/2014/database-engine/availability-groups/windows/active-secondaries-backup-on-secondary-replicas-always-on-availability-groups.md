---
title: 活动辅助副本：辅助副本上的备份 (Always On 可用性组) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
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
ms.assetid: 82afe51b-71d1-4d5b-b20a-b57afc002405
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0cf899cdbeb1ae4ede6c9196b8eb93a9d9e54f05
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690158"
---
# <a name="active-secondaries-backup-on-secondary-replicas-always-on-availability-groups"></a><span data-ttu-id="2b1f7-102">活动次要副本：次要副本备份（AlwaysOn 可用性组）</span><span class="sxs-lookup"><span data-stu-id="2b1f7-102">Active Secondaries: Backup on Secondary Replicas (Always On Availability Groups)</span></span>
  <span data-ttu-id="2b1f7-103">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 活动辅助功能包括支持在辅助副本上执行备份操作。</span><span class="sxs-lookup"><span data-stu-id="2b1f7-103">The [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] active secondary capabilities include support for performing backup operations on secondary replicas.</span></span> <span data-ttu-id="2b1f7-104">备份操作可能会给 I/O 和 CPU 带来很大的压力（使用备份压缩）。</span><span class="sxs-lookup"><span data-stu-id="2b1f7-104">Backup operations can put significant strain on I/O and CPU (with backup compression).</span></span> <span data-ttu-id="2b1f7-105">将备份负荷转移到已同步或正在同步的辅助副本后，您可以使用承载第一层工作负荷的主副本的服务器实例上的资源。</span><span class="sxs-lookup"><span data-stu-id="2b1f7-105">Offloading backups to a synchronized or synchronizing secondary replica allows you to use the resources on server instance that hosts the primary replica for your tier-1 workloads.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2b1f7-106">在可用性组的主数据库或辅助数据库上不允许 RESTORE 语句。</span><span class="sxs-lookup"><span data-stu-id="2b1f7-106">RESTORE statements are not allowed on either the primary or secondary databases of an availability group.</span></span>  
  
  
  
##  <a name="backup-types-supported-on-secondary-replicas"></a><a name="SupportedBuTypes"></a> <span data-ttu-id="2b1f7-107">辅助副本上支持的备份类型</span><span class="sxs-lookup"><span data-stu-id="2b1f7-107">Backup Types Supported on Secondary Replicas</span></span>  
  
-   <span data-ttu-id="2b1f7-108">`BACKUP DATABASE` 在辅助副本上执行时仅支持数据库、文件或文件组的仅复制完整备份。</span><span class="sxs-lookup"><span data-stu-id="2b1f7-108">`BACKUP DATABASE` supports only copy-only full backups of databases, files, or filegroups when it is executed on secondary replicas.</span></span> <span data-ttu-id="2b1f7-109">请注意，仅复制备份不影响日志链，也不清除差异位图。</span><span class="sxs-lookup"><span data-stu-id="2b1f7-109">Note that copy-only backups do not impact the log chain or clear the differential bitmap.</span></span>  
  
-   <span data-ttu-id="2b1f7-110">辅助副本不支持差异备份。</span><span class="sxs-lookup"><span data-stu-id="2b1f7-110">Differential backups are not supported on secondary replicas.</span></span>  
  
-   <span data-ttu-id="2b1f7-111">**BACKUP LOG** 仅支持常规日志备份（次要副本上的日志备份不支持 COPY_ONLY 选项）。</span><span class="sxs-lookup"><span data-stu-id="2b1f7-111">**BACKUP LOG** supports only regular log backups (the COPY_ONLY option is not supported for log backups on secondary replicas).</span></span>  
  
     <span data-ttu-id="2b1f7-112">对于在任何副本（主副本或辅助副本）上进行的日志备份之间，确保一致的日志链，而与其可用性模式（同步提交或异步提交无关）。</span><span class="sxs-lookup"><span data-stu-id="2b1f7-112">A consistent log chain is ensured across log backups taken on any of the replicas (primary or secondary), irrespective of their availability mode (synchronous-commit or asynchronous-commit).</span></span>  
  
-   <span data-ttu-id="2b1f7-113">若要备份辅助数据库，辅助副本必须能够与主副本进行通信，并且状态必须为 `SYNCHRONIZED` 或 `SYNCHRONIZING`。</span><span class="sxs-lookup"><span data-stu-id="2b1f7-113">To back up a secondary database, a secondary replica must be able to communicate with the primary replica and must be `SYNCHRONIZED` or `SYNCHRONIZING`.</span></span>  
  
##  <a name="configuring-where-backup-jobs-run"></a><a name="WhereBuJobsRun"></a> <span data-ttu-id="2b1f7-114">配置运行备份作业的位置</span><span class="sxs-lookup"><span data-stu-id="2b1f7-114">Configuring Where Backup Jobs Run</span></span>  
 <span data-ttu-id="2b1f7-115">在辅助副本上执行备份以减轻主生产服务器的备份工作负荷非常有好处。</span><span class="sxs-lookup"><span data-stu-id="2b1f7-115">Performing backups on a secondary replica to offload the backup workload from the primary production server is a great benefit.</span></span> <span data-ttu-id="2b1f7-116">但是，对辅助副本执行备份会显著增加用于确定应在何处运行备份作业的过程的复杂性。</span><span class="sxs-lookup"><span data-stu-id="2b1f7-116">However, performing backups on secondary replicas introduce significant complexity to the process of determining where backup jobs should run.</span></span> <span data-ttu-id="2b1f7-117">要解决这个问题，请按如下所示配置备份作业运行的位置：</span><span class="sxs-lookup"><span data-stu-id="2b1f7-117">To address this, configure where backup jobs run as follows:</span></span>  
  
1.  <span data-ttu-id="2b1f7-118">配置可用性组以便指定要对其执行备份的可用性副本。</span><span class="sxs-lookup"><span data-stu-id="2b1f7-118">Configure the availability group to specify which availability replicas where you would prefer backups to be performed.</span></span> <span data-ttu-id="2b1f7-119">有关详细信息，请参阅 [CREATE AVAILABILITY GROUP (Transact-SQL)](/sql/t-sql/statements/create-availability-group-transact-sql) 或 [ALTER AVAILABILITY GROUP (Transact-SQL)](/sql/t-sql/statements/alter-availability-group-transact-sql) 中的 AUTOMATED_BACKUP_PREFERENCE 和 BACKUP_PRIORITY 参数\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2b1f7-119">For more information, see *AUTOMATED_BACKUP_PREFERENCE* and *BACKUP_PRIORITY* parameters in [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-availability-group-transact-sql) or [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql).</span></span>  
  
2.  <span data-ttu-id="2b1f7-120">为承载作为执行备份候选的可用性副本的每个服务器实例上的每个可用性数据库都创建编写了脚本的备份作业。</span><span class="sxs-lookup"><span data-stu-id="2b1f7-120">Create scripted backup jobs for every availability database on every server instance that hosts an availability replica that is a candidate for performing backups.</span></span> <span data-ttu-id="2b1f7-121">有关详细信息，请参阅 [配置可用性副本备份 (SQL Server)](configure-backup-on-availability-replicas-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="2b1f7-121">For more information, see the "Follow Up: After Configuring Backup on Secondary Replicas" section of [Configure Backup on Availability Replicas &#40;SQL Server&#41;](configure-backup-on-availability-replicas-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="2b1f7-122">相关任务</span><span class="sxs-lookup"><span data-stu-id="2b1f7-122">Related Tasks</span></span>  
 <span data-ttu-id="2b1f7-123">**配置辅助副本备份**</span><span class="sxs-lookup"><span data-stu-id="2b1f7-123">**To configure backup on secondary replicas**</span></span>  
  
-   [<span data-ttu-id="2b1f7-124">配置可用性副本备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="2b1f7-124">Configure Backup on Availability Replicas &#40;SQL Server&#41;</span></span>](configure-backup-on-availability-replicas-sql-server.md)  
  
 <span data-ttu-id="2b1f7-125">**确定当前副本是否为首选备份副本**</span><span class="sxs-lookup"><span data-stu-id="2b1f7-125">**To determine whether the current replica is the preferred backup replica**</span></span>  
  
-   [<span data-ttu-id="2b1f7-126">sys.fn_hadr_backup_is_preferred_replica</span><span class="sxs-lookup"><span data-stu-id="2b1f7-126">sys.fn_hadr_backup_is_preferred_replica</span></span>](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql)  
  
 <span data-ttu-id="2b1f7-127">**创建备份日志**</span><span class="sxs-lookup"><span data-stu-id="2b1f7-127">**To create a backup job**</span></span>  
  
-   [<span data-ttu-id="2b1f7-128">使用维护计划向导</span><span class="sxs-lookup"><span data-stu-id="2b1f7-128">Use the Maintenance Plan Wizard</span></span>](../../../relational-databases/maintenance-plans/use-the-maintenance-plan-wizard.md)  
  
-   [<span data-ttu-id="2b1f7-129">执行作业</span><span class="sxs-lookup"><span data-stu-id="2b1f7-129">Implement Jobs</span></span>](../../../ssms/agent/implement-jobs.md)  
  
  
## <a name="see-also"></a><span data-ttu-id="2b1f7-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2b1f7-130">See Also</span></span>  
 <span data-ttu-id="2b1f7-131">[AlwaysOn 可用性组 &#40;SQL Server 概述&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2b1f7-131">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="2b1f7-132">[仅复制备份 (SQL Server)](../../../relational-databases/backup-restore/copy-only-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2b1f7-132">[Copy-Only Backups &#40;SQL Server&#41;](../../../relational-databases/backup-restore/copy-only-backups-sql-server.md) </span></span>  
 <span data-ttu-id="2b1f7-133">[CREATE AVAILABILITY GROUP (Transact-SQL)](/sql/t-sql/statements/create-availability-group-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2b1f7-133">[CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-availability-group-transact-sql) </span></span>  
 [<span data-ttu-id="2b1f7-134">ALTER AVAILABILITY GROUP (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="2b1f7-134">ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-availability-group-transact-sql)  
  
  
