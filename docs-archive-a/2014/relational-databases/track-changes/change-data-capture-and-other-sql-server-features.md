---
title: 变更数据捕获和其他 SQL Server 功能 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- change data capture [SQL Server], other SQL Server features and
ms.assetid: 7dfcb362-1904-4578-8274-da16681a960e
author: rothja
ms.author: jroth
ms.openlocfilehash: acafd5ba49bec92fd4c6b93c4163affaa42ab7f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588385"
---
# <a name="change-data-capture-and-other-sql-server-features"></a><span data-ttu-id="bbbe5-102">变更数据捕获和其他 SQL Server 功能</span><span class="sxs-lookup"><span data-stu-id="bbbe5-102">Change Data Capture and Other SQL Server Features</span></span>
  <span data-ttu-id="bbbe5-103">本主题说明下列功能如何与变更数据捕获交互：</span><span class="sxs-lookup"><span data-stu-id="bbbe5-103">This topic describes how the following features interact with change data capture:</span></span>  
  
-   [<span data-ttu-id="bbbe5-104">Change tracking</span><span class="sxs-lookup"><span data-stu-id="bbbe5-104">Change tracking</span></span>](#ChangeTracking)  
  
-   [<span data-ttu-id="bbbe5-105">数据库镜像</span><span class="sxs-lookup"><span data-stu-id="bbbe5-105">Database mirroring</span></span>](#DatabaseMirroring)  
  
-   [<span data-ttu-id="bbbe5-106">事务复制</span><span class="sxs-lookup"><span data-stu-id="bbbe5-106">Transactional replication</span></span>](#TransReplication)  
  
-   [<span data-ttu-id="bbbe5-107">还原或附加启用了变更数据捕获的数据库</span><span class="sxs-lookup"><span data-stu-id="bbbe5-107">Restoring or Attaching a Database Enabled for Change Data Capture</span></span>](#RestoreOrAttach)  
  
##  <a name="change-tracking"></a><a name="ChangeTracking"></a> <span data-ttu-id="bbbe5-108">更改跟踪</span><span class="sxs-lookup"><span data-stu-id="bbbe5-108">Change Tracking</span></span>  
 <span data-ttu-id="bbbe5-109">可以对同一数据库启用变更数据捕获和 [更改跟踪](about-change-tracking-sql-server.md) 。</span><span class="sxs-lookup"><span data-stu-id="bbbe5-109">Change data capture and [change tracking](about-change-tracking-sql-server.md) can be enabled on the same database.</span></span> <span data-ttu-id="bbbe5-110">没有特殊的注意事项。</span><span class="sxs-lookup"><span data-stu-id="bbbe5-110">No special considerations are required.</span></span> <span data-ttu-id="bbbe5-111">有关详细信息，请参阅[处理更改跟踪 (SQL Server)](work-with-change-tracking-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="bbbe5-111">For more information, see [Work with Change Tracking &#40;SQL Server&#41;](work-with-change-tracking-sql-server.md).</span></span>  
  
##  <a name="database-mirroring"></a><a name="DatabaseMirroring"></a> <span data-ttu-id="bbbe5-112">数据库镜像</span><span class="sxs-lookup"><span data-stu-id="bbbe5-112">Database Mirroring</span></span>  
 <span data-ttu-id="bbbe5-113">可以对启用变更数据捕获的数据库进行镜像。</span><span class="sxs-lookup"><span data-stu-id="bbbe5-113">A database that is enabled for change data capture can be mirrored.</span></span> <span data-ttu-id="bbbe5-114">为确保捕获和清除操作可在故障转移之后自动发生，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="bbbe5-114">To ensure that capture and cleanup happen automatically after a failover, follow these steps:</span></span>  
  
1.  <span data-ttu-id="bbbe5-115">确保在新的主体服务器实例上运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理。</span><span class="sxs-lookup"><span data-stu-id="bbbe5-115">Ensure that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent is running on the new principal server instance.</span></span>  
  
2.  <span data-ttu-id="bbbe5-116">在新的主体数据库（以前的镜像数据库）上创建捕获作业和清除作业。</span><span class="sxs-lookup"><span data-stu-id="bbbe5-116">Create the capture job and cleanup job on the new principal database (the former mirror database).</span></span> <span data-ttu-id="bbbe5-117">若要创建作业，请使用 [sp_cdc_add_job](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql) 存储过程。</span><span class="sxs-lookup"><span data-stu-id="bbbe5-117">To create the jobs, use the [sp_cdc_add_job](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql) stored procedure.</span></span>  
  
 <span data-ttu-id="bbbe5-118">若要查看清除作业或捕获作业的当前配置，请在新的主体服务器实例上使用 [sys.sp_cdc_help_jobs](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-help-jobs-transact-sql) 存储过程。</span><span class="sxs-lookup"><span data-stu-id="bbbe5-118">To view the current configuration of a cleanup or capture job, use the [sys.sp_cdc_help_jobs](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-help-jobs-transact-sql) stored procedure on the new principal server instance.</span></span> <span data-ttu-id="bbbe5-119">对于给定数据库，捕获作业名为 cdc。*database_name*_capture，清除作业名为 cdc。*database_name*_cleanup，其中*database_name*是数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="bbbe5-119">For a given database, the capture job is named cdc.*database_name*_capture, and the cleanup job is named cdc.*database_name*_cleanup, where *database_name* is the name of the database.</span></span>  
  
 <span data-ttu-id="bbbe5-120">若要更改作业的配置，请使用 [sys.sp_cdc_change_job](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-change-job-transact-sql) 存储过程。</span><span class="sxs-lookup"><span data-stu-id="bbbe5-120">To change the configuration of a job, use the [sys.sp_cdc_change_job](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-change-job-transact-sql) stored procedure.</span></span>  
  
 <span data-ttu-id="bbbe5-121">有关数据库镜像的信息，请参阅[数据库镜像 (SQL Server)](../../database-engine/database-mirroring/database-mirroring-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="bbbe5-121">For information about database mirroring, see [Database Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md).</span></span>  
  
##  <a name="transactional-replication"></a><a name="TransReplication"></a><span data-ttu-id="bbbe5-122">事务复制</span><span class="sxs-lookup"><span data-stu-id="bbbe5-122">Transactional Replication</span></span>  
 <span data-ttu-id="bbbe5-123">变更数据捕获和事务复制可以共存于同一数据库中，但在启用这两项功能后，更改表的填充处理方式将发生变化。</span><span class="sxs-lookup"><span data-stu-id="bbbe5-123">Change data capture and transactional replication can coexist in the same database, but population of the change tables is handled differently when both features are enabled.</span></span> <span data-ttu-id="bbbe5-124">变更数据捕获和事务复制始终使用相同的过程 [sp_replcmds](/sql/relational-databases/system-stored-procedures/sp-replcmds-transact-sql)从事务日志读取更改。</span><span class="sxs-lookup"><span data-stu-id="bbbe5-124">Change data capture and transactional replication always use the same procedure, [sp_replcmds](/sql/relational-databases/system-stored-procedures/sp-replcmds-transact-sql), to read changes from the transaction log.</span></span> <span data-ttu-id="bbbe5-125">当单独启用变更数据捕获时， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业会调用 `sp_replcmds` 。</span><span class="sxs-lookup"><span data-stu-id="bbbe5-125">When change data capture is enabled on its own, a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job calls `sp_replcmds`.</span></span> <span data-ttu-id="bbbe5-126">在同一数据库上同时启用这两个功能时，日志读取器代理调用 `sp_replcmds` 。</span><span class="sxs-lookup"><span data-stu-id="bbbe5-126">When both features are enabled on the same database, the Log Reader Agent calls `sp_replcmds`.</span></span> <span data-ttu-id="bbbe5-127">此代理将填充更改表和分发数据库表。</span><span class="sxs-lookup"><span data-stu-id="bbbe5-127">This agent populates both the change tables and the distribution database tables.</span></span> <span data-ttu-id="bbbe5-128">有关详细信息，请参阅 [Replication Log Reader Agent](../replication/agents/replication-log-reader-agent.md)。</span><span class="sxs-lookup"><span data-stu-id="bbbe5-128">For more information, see [Replication Log Reader Agent](../replication/agents/replication-log-reader-agent.md).</span></span>  
  
 <span data-ttu-id="bbbe5-129">假设为 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库启用了变更数据捕获，并为捕获启用了两个表。</span><span class="sxs-lookup"><span data-stu-id="bbbe5-129">Consider a scenario in which change data capture is enabled on the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database, and two tables are enabled for capture.</span></span> <span data-ttu-id="bbbe5-130">为了填充更改表，捕获作业将调用 `sp_replcmds` 。</span><span class="sxs-lookup"><span data-stu-id="bbbe5-130">To populate the change tables, the capture job calls `sp_replcmds`.</span></span> <span data-ttu-id="bbbe5-131">此外，还为该数据库启用了事务复制，并会创建发布。</span><span class="sxs-lookup"><span data-stu-id="bbbe5-131">The database is enabled for transactional replication, and a publication is created.</span></span> <span data-ttu-id="bbbe5-132">此时，将为该数据库创建日志读取器代理，并删除捕获作业。</span><span class="sxs-lookup"><span data-stu-id="bbbe5-132">Now, the Log Reader Agent is created for the database and the capture job is deleted.</span></span> <span data-ttu-id="bbbe5-133">日志读取器代理继续从提交到更改表的最后一个日志序列号开始扫描日志。</span><span class="sxs-lookup"><span data-stu-id="bbbe5-133">The Log Reader Agent continues to scan the log from the last log sequence number that was committed to the change table.</span></span> <span data-ttu-id="bbbe5-134">这样将确保更改表中的数据一致性。</span><span class="sxs-lookup"><span data-stu-id="bbbe5-134">This ensures data consistency in the change tables.</span></span> <span data-ttu-id="bbbe5-135">如果在此数据库中禁用事务复制，则会删除日志读取器代理，并重新创建捕获作业。</span><span class="sxs-lookup"><span data-stu-id="bbbe5-135">If transactional replication is disabled in this database, the Log Reader Agent is removed and the capture job is re-created.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bbbe5-136">当日志读取器代理同时用于变更数据捕获和事务复制时，复制的更改将首先写入分发数据库。</span><span class="sxs-lookup"><span data-stu-id="bbbe5-136">When the Log Reader Agent is used for both change data capture and transactional replication, replicated changes are first written to the distribution database.</span></span> <span data-ttu-id="bbbe5-137">然后，捕获的更改会写入更改表。</span><span class="sxs-lookup"><span data-stu-id="bbbe5-137">Then, captured changes are written to the change tables.</span></span> <span data-ttu-id="bbbe5-138">两项操作会一起提交。</span><span class="sxs-lookup"><span data-stu-id="bbbe5-138">Both operations are committed together.</span></span> <span data-ttu-id="bbbe5-139">如果在写入分发数据库时有任何滞后时间，则在更改显示在更改表中之前，将有对应的滞后时间。</span><span class="sxs-lookup"><span data-stu-id="bbbe5-139">If there is any latency in writing to the distribution database, there will be a corresponding latency before changes appear in the change tables.</span></span>  
  
 <span data-ttu-id="bbbe5-140">在启用了变更数据捕获的情况下，无法使用事务性复制的 **proc exec** 选项。</span><span class="sxs-lookup"><span data-stu-id="bbbe5-140">The **proc exec** option of transactional replication is not available when change data capture is enabled.</span></span>  
  
##  <a name="restoring-or-attaching-a-database-enabled-for-change-data-capture"></a><a name="RestoreOrAttach"></a><span data-ttu-id="bbbe5-141">还原或附加启用了变更数据捕获的数据库</span><span class="sxs-lookup"><span data-stu-id="bbbe5-141">Restoring or Attaching a Database Enabled for Change Data Capture</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="bbbe5-142">使用以下逻辑确定还原或附加数据库后变更数据捕获是否继续保持启用状态：</span><span class="sxs-lookup"><span data-stu-id="bbbe5-142">uses the following logic to determine if change data capture remains enabled after a database is restored or attached:</span></span>  
  
-   <span data-ttu-id="bbbe5-143">如果数据库以同一数据库名称还原到同一服务器，变更数据捕获将保持启用状态。</span><span class="sxs-lookup"><span data-stu-id="bbbe5-143">If a database is restored to the same server with the same database name, change data capture remains enabled.</span></span>  
  
-   <span data-ttu-id="bbbe5-144">如果数据库还原到其他服务器，默认情况下将禁用变更数据捕获，并删除所有相关的元数据。</span><span class="sxs-lookup"><span data-stu-id="bbbe5-144">If a database is restored to another server, by default change data capture is disabled and all related metadata is deleted.</span></span>  
  
     <span data-ttu-id="bbbe5-145">若要保留变更数据捕获，还原数据库时请使用 `KEEP_CDC` 选项。</span><span class="sxs-lookup"><span data-stu-id="bbbe5-145">To retain change data capture, use the `KEEP_CDC` option when restoring the database.</span></span> <span data-ttu-id="bbbe5-146">有关此选项的详细信息，请参阅 [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="bbbe5-146">For more information about this option, see [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>  
  
-   <span data-ttu-id="bbbe5-147">如果数据库在分离后附加到同一服务器或其他服务器，变更数据捕获将保持启用状态。</span><span class="sxs-lookup"><span data-stu-id="bbbe5-147">If a database is detached and attached to the same server or another server, change data capture remains enabled.</span></span>  
  
-   <span data-ttu-id="bbbe5-148">如果使用选项将数据库附加或还原 `KEEP_CDC` 到 enterprise 以外的任何版本，操作将被阻止，因为变更数据捕获需要 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] enterprise。</span><span class="sxs-lookup"><span data-stu-id="bbbe5-148">If a database is attached or restored with the `KEEP_CDC` option to any edition other than Enterprise, the operation is blocked because change data capture requires [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise.</span></span> <span data-ttu-id="bbbe5-149">将显示错误消息 934：</span><span class="sxs-lookup"><span data-stu-id="bbbe5-149">Error message 934 is displayed:</span></span>  
  
     `SQL Server cannot load database '%.*ls' because change data capture is enabled. The currently installed edition of SQL Server does not support change data capture. Either disable change data capture in the database by using a supported edition of SQL Server, or upgrade the instance to one that supports change data capture.`  
  
 <span data-ttu-id="bbbe5-150">可以使用 [sys.sp_cdc_disable_db](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-disable-db-transact-sql) 从还原或附加的数据库中删除变更数据捕获。</span><span class="sxs-lookup"><span data-stu-id="bbbe5-150">You can use [sys.sp_cdc_disable_db](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-disable-db-transact-sql) to remove change data capture from a restored or attached database.</span></span>  
  
## <a name="change-data-capture-and-alwayson"></a><span data-ttu-id="bbbe5-151">变更数据捕获和 AlwaysON</span><span class="sxs-lookup"><span data-stu-id="bbbe5-151">Change Data Capture and AlwaysON</span></span>  
 <span data-ttu-id="bbbe5-152">使用 AlwaysOn 时，应在辅助副本上更改枚举以减少主副本的磁盘负荷。</span><span class="sxs-lookup"><span data-stu-id="bbbe5-152">When you use AlwaysON, change enumeration should be done on the Secondary replication to reduce the disk load on the primary.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbbe5-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bbbe5-153">See Also</span></span>  
 [<span data-ttu-id="bbbe5-154">管理和监视变更数据捕获 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="bbbe5-154">Administer and Monitor Change Data Capture &#40;SQL Server&#41;</span></span>](../track-changes/administer-and-monitor-change-data-capture-sql-server.md)  
  
  
