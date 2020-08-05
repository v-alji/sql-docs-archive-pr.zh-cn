---
title: 延迟的事务 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- I/O [SQL Server], database recovery
- restoring pages [SQL Server]
- deferred transactions
- modifying transaction deferred state
ms.assetid: 6fc0f9b6-d3ea-4971-9f27-d0195d1ff718
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 188a0409fbad3f12283adacafbfcb5f176650b72
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581333"
---
# <a name="deferred-transactions-sql-server"></a><span data-ttu-id="6a1dd-102">延迟的事务 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6a1dd-102">Deferred Transactions (SQL Server)</span></span>
  <span data-ttu-id="6a1dd-103">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 企业版中，如果在数据库启动过程中回滚（撤消）所需的数据处于脱机状态，则损坏的事务可能延迟。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-103">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise, a corrupted transaction can become deferred if data required by rollback (undo) is offline during database startup.</span></span> <span data-ttu-id="6a1dd-104">“延迟的事务”  是指前滚阶段结束时未提交的事务或遇到错误而无法回滚的事务。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-104">A *deferred transaction* is a transaction that is uncommitted when the roll forward phase finishes and that has encountered an error that prevents it from being rolled back.</span></span> <span data-ttu-id="6a1dd-105">因为无法回滚事务，所以事务将延迟。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-105">Because the transaction cannot be rolled back, it is deferred.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6a1dd-106">仅在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise 中才会延迟损坏的事务。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-106">Corrupted transactions are deferred only in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise.</span></span> <span data-ttu-id="6a1dd-107">在其他版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中，事务损坏将导致启动失败。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-107">In other editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], a corrupted transaction causes startup to fail.</span></span>  
  
 <span data-ttu-id="6a1dd-108">一般来说，如果前滚数据库时遇到 I/O 错误而无法读取事务所需的页面，则将导致事务延迟。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-108">Generally, a deferred transaction occurs because, while the database was being rolled forward, an I/O error prevented reading a page that was required by the transaction.</span></span> <span data-ttu-id="6a1dd-109">但是，文件级的错误也会导致延迟的事务。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-109">However, an error at the file level can also cause deferred transactions.</span></span> <span data-ttu-id="6a1dd-110">如果部分还原顺序在某点停止，在该点上必须对事务进行回滚而事务所需的数据处于脱机状态，这亦会导致事务延迟。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-110">A deferred transaction can also occur when a partial restore sequence stops at a point at which transaction rollback is necessary and a transaction requires data that is offline.</span></span>  
  
 <span data-ttu-id="6a1dd-111">如果用户事务在回滚过程中遇到 I/O 错误，则会导致整个数据库脱机。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-111">User transactions that are rolling back and hit an I/O error cause the whole database to go offline.</span></span> <span data-ttu-id="6a1dd-112">当数据库恢复联机时，重做操作将重新获得它曾持有的所有锁，并尝试回滚所有未提交的事务。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-112">When the database is brought back online, the redo reacquires all the locks it had and tries to roll back all the uncommitted transactions.</span></span> <span data-ttu-id="6a1dd-113">事务所修改的所有数据都将保持适当锁定的状态，直到可以回滚事务时为止。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-113">All data modified by a transaction remains appropriately locked until the transaction can roll back.</span></span> <span data-ttu-id="6a1dd-114">在修复损坏并重新启动数据库时，或通过联机还原在数据库保持联机的同时解决了延迟的事务时，无法回滚的事务将放弃其持有的锁。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-114">Transactions that cannot be rolled back will give up their locks when the corruption is fixed and the database restarted or, after an online restore, when the deferred transactions are resolved while the database remains online.</span></span> <span data-ttu-id="6a1dd-115">在此之前，延迟的事务可持有锁，以防止对整个数据库执行某些操作。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-115">Until that point, a deferred transaction can hold locks that prevent certain operations on the database as a whole.</span></span> <span data-ttu-id="6a1dd-116">例如，如果延迟的事务包含 CREATE TABLE 指令，则在解决延迟的事务之前，任何用户都无法创建表。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-116">For example, if a deferred transaction contains a CREATE TABLE instruction, no user can create a table until the deferred transaction has been resolved.</span></span>  
  
 <span data-ttu-id="6a1dd-117">如果段落还原将数据库恢复到某个点，在该点上有一个或多个活动事务会影响尚未还原并处于脱机状态的文件组，则将发生事务延迟。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-117">Deferred transaction can also occur because a piecemeal restore recovers a database to a point at which one or more active transactions are affecting a filegroup that has not yet been restored and is offline.</span></span> <span data-ttu-id="6a1dd-118">因为无法回滚事务，所以事务将延迟。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-118">Because the transactions cannot be rolled back, they become deferred.</span></span>  
  
 <span data-ttu-id="6a1dd-119">下表列出了导致数据库执行恢复的操作以及发生 I/O 问题的后果。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-119">The following table lists the actions that cause a database to perform recovery and the outcome if an I/O problem occurs.</span></span>  
  
|<span data-ttu-id="6a1dd-120">操作</span><span class="sxs-lookup"><span data-stu-id="6a1dd-120">Action</span></span>|<span data-ttu-id="6a1dd-121">解决方法（如果遇到 I/O 问题或所需数据处于脱机状态）</span><span class="sxs-lookup"><span data-stu-id="6a1dd-121">Resolution (if I/O problems occur or required data is offline)</span></span>|  
|------------|-----------------------------------------------------------------------|  
|<span data-ttu-id="6a1dd-122">服务器启动</span><span class="sxs-lookup"><span data-stu-id="6a1dd-122">Server start</span></span>|<span data-ttu-id="6a1dd-123">延迟的事务</span><span class="sxs-lookup"><span data-stu-id="6a1dd-123">Deferred transaction</span></span>|  
|<span data-ttu-id="6a1dd-124">还原</span><span class="sxs-lookup"><span data-stu-id="6a1dd-124">Restore</span></span>|<span data-ttu-id="6a1dd-125">延迟的事务</span><span class="sxs-lookup"><span data-stu-id="6a1dd-125">Deferred transaction</span></span>|  
|<span data-ttu-id="6a1dd-126">附加</span><span class="sxs-lookup"><span data-stu-id="6a1dd-126">Attach</span></span>|<span data-ttu-id="6a1dd-127">附加失败</span><span class="sxs-lookup"><span data-stu-id="6a1dd-127">Attach fails</span></span>|  
|<span data-ttu-id="6a1dd-128">自动重新启动</span><span class="sxs-lookup"><span data-stu-id="6a1dd-128">Autorestart</span></span>|<span data-ttu-id="6a1dd-129">延迟的事务</span><span class="sxs-lookup"><span data-stu-id="6a1dd-129">Deferred transaction</span></span>|  
|<span data-ttu-id="6a1dd-130">创建数据库或数据库快照</span><span class="sxs-lookup"><span data-stu-id="6a1dd-130">Create database or database snapshot</span></span>|<span data-ttu-id="6a1dd-131">创建失败</span><span class="sxs-lookup"><span data-stu-id="6a1dd-131">Creation fails</span></span>|  
|<span data-ttu-id="6a1dd-132">在数据库镜像上执行的重做操作</span><span class="sxs-lookup"><span data-stu-id="6a1dd-132">Redo on database mirroring</span></span>|<span data-ttu-id="6a1dd-133">延迟的事务</span><span class="sxs-lookup"><span data-stu-id="6a1dd-133">Deferred transaction</span></span>|  
|<span data-ttu-id="6a1dd-134">文件组脱机</span><span class="sxs-lookup"><span data-stu-id="6a1dd-134">Filegroup is offline</span></span>|<span data-ttu-id="6a1dd-135">延迟的事务</span><span class="sxs-lookup"><span data-stu-id="6a1dd-135">Deferred transaction</span></span>|  
  
## <a name="moving-a-transaction-out-of-the-deferred-state"></a><span data-ttu-id="6a1dd-136">将事务移出 DEFERRED 状态</span><span class="sxs-lookup"><span data-stu-id="6a1dd-136">Moving a Transaction Out of the DEFERRED State</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6a1dd-137">延迟的事务会使事务日志保持活动状态。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-137">Deferred transactions keep the transaction log active.</span></span> <span data-ttu-id="6a1dd-138">在延迟的事务脱离延迟状态之前无法截断包含这些事务的虚拟日志文件。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-138">A virtual log file that contains any deferred transactions cannot be truncated until those transactions are moved out of the deferred state.</span></span> <span data-ttu-id="6a1dd-139">有关日志截断的详细信息，请参阅[事务日志 (SQL Server)](../logs/the-transaction-log-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-139">For more information about log truncation, see [The Transaction Log &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md).</span></span>  
  
 <span data-ttu-id="6a1dd-140">若要使事务脱离延迟状态，数据库必须在没有任何 I/O 错误的情况下顺利启动。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-140">To move the transaction out of the deferred state, the database must start cleanly without any I/O errors.</span></span> <span data-ttu-id="6a1dd-141">如果存在延迟的事务，则必须修复 I/O 错误源。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-141">If deferred transactions exist, you must fix the source of the I/O errors.</span></span> <span data-ttu-id="6a1dd-142">下面便是可用的解决方案，它们按照通常尝试执行的顺序列出：</span><span class="sxs-lookup"><span data-stu-id="6a1dd-142">The available solutions, listed in the order in which they are typically tried, are as follows:</span></span>  
  
-   <span data-ttu-id="6a1dd-143">重新启动数据库。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-143">Restart the database.</span></span> <span data-ttu-id="6a1dd-144">如果问题是暂时的，数据库应该会启动，而且没有延迟的事务。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-144">If the problem was transient, the database should start without deferred transactions.</span></span>  
  
-   <span data-ttu-id="6a1dd-145">如果事务由于文件组脱机而延迟，请将文件组重新联机。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-145">If the transactions were deferred because a filegroup was offline, bring the filegroup back online.</span></span>  
  
     <span data-ttu-id="6a1dd-146">若要使脱机文件组恢复联机，请使用以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句：</span><span class="sxs-lookup"><span data-stu-id="6a1dd-146">To bring an offline filegroup back online, use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
    ```  
    RESTORE DATABASE database_name FILEGROUP=<filegroup_name>  
    ```  
  
-   <span data-ttu-id="6a1dd-147">还原数据库。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-147">Restore the database.</span></span> <span data-ttu-id="6a1dd-148">进行联机还原后，将解决所有延迟的事务。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-148">After an online restore, any deferred transactions are resolved.</span></span>  
  
     <span data-ttu-id="6a1dd-149">在完整恢复模式或大容量日志恢复模式下，如果延迟的事务仅仅是由少量的损坏页引起的，则可以通过联机页面还原解决这些错误（如果支持）。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-149">Under the full or bulk-logged recovery model, if the deferred transactions were caused by only a few corrupted pages, an online page restore might resolve the errors (where supported).</span></span>  
  
-   <span data-ttu-id="6a1dd-150">如果不再需要因脱机状态而导致事务延迟的文件组，请使这样的脱机文件组失效。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-150">If you are no longer require a filegroup whose offline status is causing deferred transactions, make the offline filegroup defunct.</span></span> <span data-ttu-id="6a1dd-151">这样的文件组失效之后，由于这些文件组的脱机而延迟的事务将脱离延迟状态。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-151">Transactions that were deferred because the filegroup was offline are moved out of the deferred state after the filegroup becomes defunct.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="6a1dd-152">从不恢复失效的文件组。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-152">A defunct filegroup can never be recovered.</span></span>  
  
     <span data-ttu-id="6a1dd-153">有关详细信息，请参阅 [删除失效文件组 (SQL Server)](remove-defunct-filegroups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-153">For more information, see [Remove Defunct Filegroups &#40;SQL Server&#41;](remove-defunct-filegroups-sql-server.md).</span></span>  
  
-   <span data-ttu-id="6a1dd-154">如果由于页的错误而致使事务延迟，并且没有数据库的完好备份，请按照以下步骤修复数据库：</span><span class="sxs-lookup"><span data-stu-id="6a1dd-154">If transactions were deferred because of a bad page and if a good backup of the database does not exist, use the following process to repair the database:</span></span>  
  
    -   <span data-ttu-id="6a1dd-155">首先通过执行以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句将数据库置为紧急模式：</span><span class="sxs-lookup"><span data-stu-id="6a1dd-155">First put the database into emergency mode by executing the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
        ```  
        ALTER DATABASE <database_name> SET EMERGENCY  
        ```  
  
         <span data-ttu-id="6a1dd-156">有关紧急模式的信息，请参阅 [Database States](../databases/database-states.md)。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-156">For information about emergency mode, see [Database States](../databases/database-states.md).</span></span>  
  
    -   <span data-ttu-id="6a1dd-157">然后，通过在以下 DBCC 语句之一中使用 DBCC REPAIR_ALLOW_DATA_LOSS 选项修复数据库：[DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)、[DBCC CHECKALLOC](/sql/t-sql/database-console-commands/dbcc-checkalloc-transact-sql) 或 [DBCC CHECKTABLE](/sql/t-sql/database-console-commands/dbcc-checktable-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-157">Then, repair the database by using the DBCC REPAIR_ALLOW_DATA_LOSS option in one of the following DBCC statements: [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql), [DBCC CHECKALLOC](/sql/t-sql/database-console-commands/dbcc-checkalloc-transact-sql), or [DBCC CHECKTABLE](/sql/t-sql/database-console-commands/dbcc-checktable-transact-sql).</span></span>  
  
         <span data-ttu-id="6a1dd-158">在遇到错误的页时，DBCC 将释放该页并修复所有相关错误。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-158">When DBCC encounters the bad page, DBCC deallocates it and repairs any related errors.</span></span> <span data-ttu-id="6a1dd-159">此方法可以使数据库重新联机并处于物理上一致的状态。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-159">This approach enables the database to be brought back online in a physically consistent state.</span></span> <span data-ttu-id="6a1dd-160">但是，还可能会丢失其他数据；因此，应在不得已的情况下才使用此方法。</span><span class="sxs-lookup"><span data-stu-id="6a1dd-160">However, additional data might also be lost; therefore, this approach should be used as a last resort.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a1dd-161">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6a1dd-161">See Also</span></span>  
 <span data-ttu-id="6a1dd-162">[还原和恢复概述 (SQL Server)](restore-and-recovery-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6a1dd-162">[Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span></span>  
 <span data-ttu-id="6a1dd-163">[删除失效文件组 (SQL Server)](remove-defunct-filegroups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6a1dd-163">[Remove Defunct Filegroups &#40;SQL Server&#41;](remove-defunct-filegroups-sql-server.md) </span></span>  
 <span data-ttu-id="6a1dd-164">[文件还原（完整恢复模式）](file-restores-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="6a1dd-164">[File Restores &#40;Full Recovery Model&#41;](file-restores-full-recovery-model.md) </span></span>  
 <span data-ttu-id="6a1dd-165">[文件还原（简单恢复模式）](file-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="6a1dd-165">[File Restores &#40;Simple Recovery Model&#41;](file-restores-simple-recovery-model.md) </span></span>  
 <span data-ttu-id="6a1dd-166">[还原页 (SQL Server)](restore-pages-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6a1dd-166">[Restore Pages &#40;SQL Server&#41;](restore-pages-sql-server.md) </span></span>  
 <span data-ttu-id="6a1dd-167">[段落还原 (SQL Server)](piecemeal-restores-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6a1dd-167">[Piecemeal Restores &#40;SQL Server&#41;](piecemeal-restores-sql-server.md) </span></span>  
 <span data-ttu-id="6a1dd-168">[ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6a1dd-168">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 [<span data-ttu-id="6a1dd-169">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6a1dd-169">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
