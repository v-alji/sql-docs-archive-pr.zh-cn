---
title: 将数据库恢复到数据库快照 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- database snapshots [SQL Server], reverting to
- reverting databases
ms.assetid: 8f74dd31-c9ca-4537-8760-0c7648f0787d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1c78da3d7c559309c0563760e7062f01cf784648
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581286"
---
# <a name="revert-a-database-to-a-database-snapshot"></a><span data-ttu-id="57254-102">将数据库恢复到数据库快照</span><span class="sxs-lookup"><span data-stu-id="57254-102">Revert a Database to a Database Snapshot</span></span>
  <span data-ttu-id="57254-103">如果联机数据库中的数据损坏，在某些情况下，将数据库恢复到发生损坏之前的数据库快照可能是一种合适的替代方案，替代从备份中还原数据库。</span><span class="sxs-lookup"><span data-stu-id="57254-103">If data in an online database becomes damaged, in some cases, reverting the database to a database snapshot that predates the damage might be an appropriate alternative to restoring the database from a backup.</span></span> <span data-ttu-id="57254-104">例如，通过恢复数据库可能会有助于从最近出现的严重用户错误（如删除的表）中恢复。</span><span class="sxs-lookup"><span data-stu-id="57254-104">For example, reverting a database might be useful for reverse a recent serious user error, such as a dropped table.</span></span> <span data-ttu-id="57254-105">但是，在该快照创建以后进行的所有更改都会丢失。</span><span class="sxs-lookup"><span data-stu-id="57254-105">However, all changes made after the snapshot was created are lost.</span></span>  
  
-   <span data-ttu-id="57254-106">**开始之前：**</span><span class="sxs-lookup"><span data-stu-id="57254-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="57254-107">限制和局限</span><span class="sxs-lookup"><span data-stu-id="57254-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="57254-108">先决条件</span><span class="sxs-lookup"><span data-stu-id="57254-108">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="57254-109">安全性</span><span class="sxs-lookup"><span data-stu-id="57254-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="57254-110">**若要将数据库恢复到数据库快照，请使用：** [Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="57254-110">**To Revert a Database to a Database Snapshot, using:**  [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="57254-111">开始之前</span><span class="sxs-lookup"><span data-stu-id="57254-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="57254-112">限制和局限</span><span class="sxs-lookup"><span data-stu-id="57254-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="57254-113">下列情况不支持恢复：</span><span class="sxs-lookup"><span data-stu-id="57254-113">Reverting is unsupported under the following conditions:</span></span>  
  
-   <span data-ttu-id="57254-114">数据库当前肯定只有一个数据库快照，并且您计划恢复到该快照。</span><span class="sxs-lookup"><span data-stu-id="57254-114">The database must currently have only one database snapshot, to which you plan to revert.</span></span>  
  
-   <span data-ttu-id="57254-115">数据库中存在任何只读或压缩的文件组。</span><span class="sxs-lookup"><span data-stu-id="57254-115">Any read-only or compressed filegroups exist in the database.</span></span>  
  
-   <span data-ttu-id="57254-116">数据库中有快照创建时联机而现在却脱机的任何文件。</span><span class="sxs-lookup"><span data-stu-id="57254-116">Any files are now offline but were online when the snapshot was created.</span></span>  
  
 <span data-ttu-id="57254-117">在恢复数据库之前，请考虑以下限制：</span><span class="sxs-lookup"><span data-stu-id="57254-117">Before reverting a database, consider the following limitations:</span></span>  
  
-   <span data-ttu-id="57254-118">恢复并不适用于介质恢复。</span><span class="sxs-lookup"><span data-stu-id="57254-118">Reverting is not intended for media recovery.</span></span> <span data-ttu-id="57254-119">.</span><span class="sxs-lookup"><span data-stu-id="57254-119">.</span></span> <span data-ttu-id="57254-120">数据库快照是不完整的数据库文件副本，因此，如果数据库或数据库快照损坏，则不可能从快照进行恢复。</span><span class="sxs-lookup"><span data-stu-id="57254-120">A database snapshot is an incomplete copy of the database files, so if either the database or the database snapshot is corrupted, reverting from a snapshot is likely to be impossible.</span></span> <span data-ttu-id="57254-121">另外，如果损坏的话，即便可以恢复，也可能无法更正该问题。</span><span class="sxs-lookup"><span data-stu-id="57254-121">Furthermore, even when it is possible, reverting in the event of corruption is unlikely to correct the problem.</span></span> <span data-ttu-id="57254-122">因此，定期执行备份并对还原计划进行测试对于保护数据库至关重要。</span><span class="sxs-lookup"><span data-stu-id="57254-122">Therefore, taking regular backups and testing your restore plan are essential to protect a database.</span></span> <span data-ttu-id="57254-123">有关详细信息，请参阅 [SQL Server 数据库的备份和还原](../backup-restore/back-up-and-restore-of-sql-server-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="57254-123">For more information, see [Back Up and Restore of SQL Server Databases](../backup-restore/back-up-and-restore-of-sql-server-databases.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="57254-124">如果需要能够将源数据库还原至创建数据库快照的时点，请使用完整恢复模式并实施允许您执行该操作的备份策略。</span><span class="sxs-lookup"><span data-stu-id="57254-124">If you need to be able to restore the source database to the point in time at which you created a database snapshot, use the full recovery model and implement a backup policy that enables you to do that.</span></span>  
  
-   <span data-ttu-id="57254-125">原始的源数据库会被恢复后的数据库覆盖，因此该快照创建后的所有数据库更新都会丢失。</span><span class="sxs-lookup"><span data-stu-id="57254-125">The original source database is overwritten by the reverted database, so any updates to the database since the snapshot's creation are lost.</span></span>  
  
-   <span data-ttu-id="57254-126">恢复操作还会覆盖旧日志文件并重新生成日志。</span><span class="sxs-lookup"><span data-stu-id="57254-126">The revert operation also overwrites the old log file and rebuilds the log.</span></span> <span data-ttu-id="57254-127">因此，无法将恢复后的数据库前滚至发生用户错误的点。</span><span class="sxs-lookup"><span data-stu-id="57254-127">Consequently, you cannot roll the reverted database forward to the point of user error.</span></span> <span data-ttu-id="57254-128">所以，建议您在恢复数据库之前备份日志。</span><span class="sxs-lookup"><span data-stu-id="57254-128">Therefore, we recommend that you back up the log before reverting a database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="57254-129">虽然不能还原原始日志以便将数据库前滚，但是可以使用原始日志文件中的信息来重新构造丢失的数据。</span><span class="sxs-lookup"><span data-stu-id="57254-129">Although you cannot restore the original log to roll forward the database, the information in the original log file can be useful for reconstructing lost data.</span></span>  
  
-   <span data-ttu-id="57254-130">恢复操作会打断日志备份链。</span><span class="sxs-lookup"><span data-stu-id="57254-130">Reverting breaks the log backup chain.</span></span> <span data-ttu-id="57254-131">因此，必须首先进行完整的数据库备份或文件备份，然后才能够进行恢复后的数据库的日志备份。</span><span class="sxs-lookup"><span data-stu-id="57254-131">Therefore, before you can take log backups of the reverted database, you must first take a full database backup or file backup.</span></span> <span data-ttu-id="57254-132">建议您进行完整的数据库备份。</span><span class="sxs-lookup"><span data-stu-id="57254-132">We recommend a full database backup.</span></span>  
  
-   <span data-ttu-id="57254-133">在执行恢复操作的过程中，快照和源数据库都不可用。</span><span class="sxs-lookup"><span data-stu-id="57254-133">During a revert operation, both the snapshot and the source database are unavailable.</span></span> <span data-ttu-id="57254-134">源数据库和快照都将被标记为“正在还原”。</span><span class="sxs-lookup"><span data-stu-id="57254-134">The source database and snapshot are both marked "In restore."</span></span> <span data-ttu-id="57254-135">如果在执行恢复操作的过程中出现错误，则当数据库再次启动时，恢复操作将会尝试完成恢复。</span><span class="sxs-lookup"><span data-stu-id="57254-135">If an error occurs during the revert operation, when the database starts up again, the revert operation will try to finish reverting.</span></span>  
  
-   <span data-ttu-id="57254-136">恢复后的数据库的元数据与创建快照时的元数据相同。</span><span class="sxs-lookup"><span data-stu-id="57254-136">The metadata of a reverted database is the same as the metadata at the time of the snapshot.</span></span>  
  
-   <span data-ttu-id="57254-137">恢复操作会删除所有的全文目录。</span><span class="sxs-lookup"><span data-stu-id="57254-137">Reverting drops all the full-text catalogs.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a><span data-ttu-id="57254-138">先决条件</span><span class="sxs-lookup"><span data-stu-id="57254-138">Prerequisites</span></span>  
 <span data-ttu-id="57254-139">确保源数据库与数据库快照满足以下先决条件：</span><span class="sxs-lookup"><span data-stu-id="57254-139">Ensure that the source database and database snapshot meet the following prerequisites:</span></span>  
  
-   <span data-ttu-id="57254-140">确认数据库没有损坏。</span><span class="sxs-lookup"><span data-stu-id="57254-140">Verify that the database has not become corrupted.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="57254-141">如果数据库已损坏，您将需要从备份中还原它。</span><span class="sxs-lookup"><span data-stu-id="57254-141">If the database has been corrupted, you will need to restore it from backups.</span></span> <span data-ttu-id="57254-142">有关详细信息，请参阅[完整数据库还原（简单恢复模式）](../backup-restore/complete-database-restores-simple-recovery-model.md)或[数据库还原（完整恢复模式）](../backup-restore/complete-database-restores-full-recovery-model.md)。</span><span class="sxs-lookup"><span data-stu-id="57254-142">For more information, see [Complete Database Restores &#40;Simple Recovery Model&#41;](../backup-restore/complete-database-restores-simple-recovery-model.md) or [Complete Database Restores &#40;Full Recovery Model&#41;](../backup-restore/complete-database-restores-full-recovery-model.md).</span></span>  
  
-   <span data-ttu-id="57254-143">标识在发生错误之前新近创建的快照。</span><span class="sxs-lookup"><span data-stu-id="57254-143">Identify a recent snapshot that was created before the error.</span></span> <span data-ttu-id="57254-144">有关详细信息，请参阅 [查看数据库快照 (SQL Server)](view-a-database-snapshot-sql-server.md)中查看数据库快照。</span><span class="sxs-lookup"><span data-stu-id="57254-144">For more information, see [View a Database Snapshot &#40;SQL Server&#41;](view-a-database-snapshot-sql-server.md).</span></span>  
  
-   <span data-ttu-id="57254-145">删除当前数据库中存在的任何其他快照。</span><span class="sxs-lookup"><span data-stu-id="57254-145">Drop any other snapshots that currently exist on the database.</span></span> <span data-ttu-id="57254-146">有关详细信息，请参阅 [删除数据库快照 (Transact-SQL)](drop-a-database-snapshot-transact-sql.md)实例。</span><span class="sxs-lookup"><span data-stu-id="57254-146">For more information, see [Drop a Database Snapshot &#40;Transact-SQL&#41;](drop-a-database-snapshot-transact-sql.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="57254-147">Security</span><span class="sxs-lookup"><span data-stu-id="57254-147">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="57254-148">权限</span><span class="sxs-lookup"><span data-stu-id="57254-148">Permissions</span></span>  
 <span data-ttu-id="57254-149">任何具有源数据库 RESTORE DATABASE 权限的用户都可以将其恢复至创建数据库快照时的状态。</span><span class="sxs-lookup"><span data-stu-id="57254-149">Any user who has RESTORE DATABASE permissions on the source database can revert it to its state when a database snapshot was created.</span></span>  
  
##  <a name="how-to-revert-a-database-to-a-database-snapshot-using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="57254-150">如何将数据库恢复到数据库快照（使用 Transact-SQL）</span><span class="sxs-lookup"><span data-stu-id="57254-150">How to Revert a Database to a Database Snapshot (Using Transact-SQL)</span></span>  
 <span data-ttu-id="57254-151">**将数据库恢复到数据库快照**</span><span class="sxs-lookup"><span data-stu-id="57254-151">**To revert a database to a database snapshot**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="57254-152">有关此过程的示例，请参阅本节后面的 [示例 (Transact-SQL)](#TsqlExample)。</span><span class="sxs-lookup"><span data-stu-id="57254-152">For an example of this procedure, see [Examples (Transact-SQL)](#TsqlExample), later in this section.</span></span>  
  
1.  <span data-ttu-id="57254-153">标识要将数据库恢复到的数据库快照。</span><span class="sxs-lookup"><span data-stu-id="57254-153">Identify the database snapshot to which you want to revert the database.</span></span> <span data-ttu-id="57254-154">你可以在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的一个数据库上查看快照（请参阅 [查看数据库快照 (SQL Server)](view-a-database-snapshot-sql-server.md)）。</span><span class="sxs-lookup"><span data-stu-id="57254-154">You can view the snapshots on a database in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] (see [View a Database Snapshot &#40;SQL Server&#41;](view-a-database-snapshot-sql-server.md)).</span></span> <span data-ttu-id="57254-155">此外，还可以在 **sys.databases (Transact-SQL)** 目录视图的 [sys.databases (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) 列中找到某个视图的源数据库。</span><span class="sxs-lookup"><span data-stu-id="57254-155">Also, you can identify the source database of a view from the **source_database_id** column of the [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) catalog view.</span></span>  
  
2.  <span data-ttu-id="57254-156">删除其他任何数据库快照。</span><span class="sxs-lookup"><span data-stu-id="57254-156">Drop any other database snapshots.</span></span>  
  
     <span data-ttu-id="57254-157">有关删除快照的信息，请参阅 [删除数据库快照 (Transact-SQL)](drop-a-database-snapshot-transact-sql.md).</span><span class="sxs-lookup"><span data-stu-id="57254-157">For information on dropping snapshots, see [Drop a Database Snapshot &#40;Transact-SQL&#41;](drop-a-database-snapshot-transact-sql.md).</span></span> <span data-ttu-id="57254-158">如果数据库使用完整恢复模式，则在执行恢复之前，应先备份日志。</span><span class="sxs-lookup"><span data-stu-id="57254-158">If the database uses the full recovery model, before reverting, you should back up the log.</span></span> <span data-ttu-id="57254-159">有关详细信息，请参阅[备份事务日志 (SQL Server)](../backup-restore/back-up-a-transaction-log-sql-server.md) 或[在数据库损坏时备份事务日志 (SQL Server)](../backup-restore/back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="57254-159">For more information, see [Back Up a Transaction Log &#40;SQL Server&#41;](../backup-restore/back-up-a-transaction-log-sql-server.md) or [Back Up the Transaction Log When the Database Is Damaged &#40;SQL Server&#41;](../backup-restore/back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md).</span></span>  
  
3.  <span data-ttu-id="57254-160">执行恢复操作。</span><span class="sxs-lookup"><span data-stu-id="57254-160">Perform the revert operation.</span></span>  
  
     <span data-ttu-id="57254-161">恢复操作要求对源数据库具有 RESTORE DATABASE 权限。</span><span class="sxs-lookup"><span data-stu-id="57254-161">A revert operation requires RESTORE DATABASE permissions on the source database.</span></span> <span data-ttu-id="57254-162">若要恢复数据库，请使用下列 Transact-SQL 语句：</span><span class="sxs-lookup"><span data-stu-id="57254-162">To revert the database, use the following Transact-SQL statement:</span></span>  
  
     <span data-ttu-id="57254-163">RESTORE DATABASE *database_name* FROM DATABASE_SNAPSHOT **=** _database_snapshot_name_</span><span class="sxs-lookup"><span data-stu-id="57254-163">RESTORE DATABASE *database_name* FROM DATABASE_SNAPSHOT **=**_database_snapshot_name_</span></span>  
  
     <span data-ttu-id="57254-164">其中， *database_name* 是源数据库的名称， *database_snapshot_name* 是要将数据库恢复到的快照的名称。</span><span class="sxs-lookup"><span data-stu-id="57254-164">Where *database_name* is the source database and *database_snapshot_name* is the name of the snapshot to which you want to revert the database.</span></span> <span data-ttu-id="57254-165">注意，必须在此语句中指定快照名称而非备份设备。</span><span class="sxs-lookup"><span data-stu-id="57254-165">Notice that in this statement, you must specify a snapshot name rather than a backup device.</span></span>  
  
     <span data-ttu-id="57254-166">有关详细信息，请参阅 [RESTORE (Transact-SQL)](/sql/t-sql/statements/restore-statements-transact-sql)备份。</span><span class="sxs-lookup"><span data-stu-id="57254-166">For more information, see [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="57254-167">在恢复操作过程中，快照和源数据库都不可用。</span><span class="sxs-lookup"><span data-stu-id="57254-167">During the revert operation, both the snapshot and the source database are unavailable.</span></span> <span data-ttu-id="57254-168">源数据库和快照都标记为“还原中”。</span><span class="sxs-lookup"><span data-stu-id="57254-168">The source database and snapshot are both marked as "In restore."</span></span> <span data-ttu-id="57254-169">如果在恢复操作期间发生错误，则数据库在重新启动后，将尝试完成恢复操作。</span><span class="sxs-lookup"><span data-stu-id="57254-169">If an error occurs during the revert operation, it will try to finish reverting when the database starts up again.</span></span>  
  
4.  <span data-ttu-id="57254-170">如果创建数据库快照后数据库所有者发生了变化，您最好更新恢复的数据库的数据库所有者。</span><span class="sxs-lookup"><span data-stu-id="57254-170">If the database owner changed since creation of the database snapshot, you may want to update the database owner of the reverted database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="57254-171">已恢复的数据库将保留数据库快照的权限和配置（例如，数据库所有者和恢复模式）。</span><span class="sxs-lookup"><span data-stu-id="57254-171">The reverted database retains the permissions and configuration (such as database owner and recovery model) of the database snapshot.</span></span>  
  
5.  <span data-ttu-id="57254-172">启动数据库。</span><span class="sxs-lookup"><span data-stu-id="57254-172">Start the database.</span></span>  
  
6.  <span data-ttu-id="57254-173">尤其在使用完整（或大容量日志）恢复模式时，可以选择备份恢复后的数据库。</span><span class="sxs-lookup"><span data-stu-id="57254-173">Optionally, back up the reverted database, especially if it uses the full (or bulk-logged) recovery model.</span></span> <span data-ttu-id="57254-174">备份数据库，请参阅[创建完整数据库备份 (SQL Server)](../backup-restore/create-a-full-database-backup-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="57254-174">To back up a database, see [Create a Full Database Backup &#40;SQL Server&#41;](../backup-restore/create-a-full-database-backup-sql-server.md).</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="57254-175">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="57254-175">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="57254-176">本节包含演示如何将数据库恢复到数据库快照的以下示例：</span><span class="sxs-lookup"><span data-stu-id="57254-176">This section contains the following examples of reverting a database to a database snapshot:</span></span>  
  
-   <span data-ttu-id="57254-177">A.</span><span class="sxs-lookup"><span data-stu-id="57254-177">A.</span></span> [<span data-ttu-id="57254-178">恢复 AdventureWorks 数据库的快照</span><span class="sxs-lookup"><span data-stu-id="57254-178">Reverting a snapshot on the AdventureWorks database</span></span>](#Reverting_AW)  
  
-   <span data-ttu-id="57254-179">B.</span><span class="sxs-lookup"><span data-stu-id="57254-179">B.</span></span> [<span data-ttu-id="57254-180">恢复 Sales 数据库的快照</span><span class="sxs-lookup"><span data-stu-id="57254-180">Reverting a snapshot on the Sales database</span></span>](#Reverting_Sales)  
  
####  <a name="a-reverting-a-snapshot-on-the-adventureworks-database"></a><a name="Reverting_AW"></a> <span data-ttu-id="57254-181">A.</span><span class="sxs-lookup"><span data-stu-id="57254-181">A.</span></span> <span data-ttu-id="57254-182">恢复 AdventureWorks 数据库的快照</span><span class="sxs-lookup"><span data-stu-id="57254-182">Reverting a snapshot on the AdventureWorks database</span></span>  
 <span data-ttu-id="57254-183">此示例假定 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库当前只存在一个快照。</span><span class="sxs-lookup"><span data-stu-id="57254-183">This example assumes that only one snapshot currently exists on the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="57254-184">有关在此创建数据库要恢复到的快照的示例，请参阅 [创建数据库快照 (Transact-SQL)](create-a-database-snapshot-transact-sql.md).</span><span class="sxs-lookup"><span data-stu-id="57254-184">For the example that creates the snapshot to which the database is reverted here, see [Create a Database Snapshot &#40;Transact-SQL&#41;](create-a-database-snapshot-transact-sql.md).</span></span>  
  
```  
USE master;  
-- Reverting AdventureWorks to AdventureWorks_dbss1800  
RESTORE DATABASE AdventureWorks from   
DATABASE_SNAPSHOT = 'AdventureWorks_dbss1800';  
GO  
```  
  
####  <a name="b-reverting-a-snapshot-on-the-sales-database"></a><a name="Reverting_Sales"></a> <span data-ttu-id="57254-185">B.</span><span class="sxs-lookup"><span data-stu-id="57254-185">B.</span></span> <span data-ttu-id="57254-186">恢复 Sales 数据库的快照</span><span class="sxs-lookup"><span data-stu-id="57254-186">Reverting a snapshot on the Sales database</span></span>  
 <span data-ttu-id="57254-187">此示例假定在 **Sales** 数据库当前存在两个快照： **sales_snapshot0600** 和 **sales_snapshot1200**。</span><span class="sxs-lookup"><span data-stu-id="57254-187">This example assumes that two snapshots currently exist on the **Sales** database: **sales_snapshot0600** and **sales_snapshot1200**.</span></span> <span data-ttu-id="57254-188">此示例删除了较旧的快照并将数据库恢复到较新的快照。</span><span class="sxs-lookup"><span data-stu-id="57254-188">The example deletes the older of the snapshots and reverts the database to the more recent snapshot.</span></span>  
  
 <span data-ttu-id="57254-189">有关用于创建此示例所基于的示例数据库和快照的代码，请参阅：</span><span class="sxs-lookup"><span data-stu-id="57254-189">For the code for creating the sample database and snapshots on which this example depends, see:</span></span>  
  
-   <span data-ttu-id="57254-190">有关 **Sales** 数据库和 **sales_snapshot0600** 快照，请参阅 [CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql) 中的“使用文件组创建数据库”和“创建数据库快照”。</span><span class="sxs-lookup"><span data-stu-id="57254-190">For the **Sales** database and the **sales_snapshot0600** snapshot, see "Creating a database with filegroups" and "Creating a database snapshot" in [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql).</span></span>  
  
-   <span data-ttu-id="57254-191">有关 **sales_snapshot1200** 快照，请参阅 [创建数据库快照 (Transact-SQL)](create-a-database-snapshot-transact-sql.md).</span><span class="sxs-lookup"><span data-stu-id="57254-191">For the **sales_snapshot1200** snapshot, see "Creating a snapshot on the Sales database" in [Create a Database Snapshot &#40;Transact-SQL&#41;](create-a-database-snapshot-transact-sql.md).</span></span>  
  
```  
--Test to see if sales_snapshot0600 exists and if it   
-- does, delete it.  
IF EXISTS (SELECT dbid FROM sys.databases  
    WHERE NAME='sales_snapshot0600')  
    DROP DATABASE SalesSnapshot0600;  
GO  
-- Reverting Sales to sales_snapshot1200  
USE master;  
RESTORE DATABASE Sales FROM DATABASE_SNAPSHOT = 'sales_snapshot1200';  
GO  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="57254-192">相关任务</span><span class="sxs-lookup"><span data-stu-id="57254-192">Related Tasks</span></span>  
  
-   [<span data-ttu-id="57254-193">创建数据库快照 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="57254-193">Create a Database Snapshot &#40;Transact-SQL&#41;</span></span>](create-a-database-snapshot-transact-sql.md)  
  
-   [<span data-ttu-id="57254-194">查看数据库快照 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="57254-194">View a Database Snapshot &#40;SQL Server&#41;</span></span>](view-a-database-snapshot-sql-server.md)  
  
-   [<span data-ttu-id="57254-195">删除数据库快照 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="57254-195">Drop a Database Snapshot &#40;Transact-SQL&#41;</span></span>](drop-a-database-snapshot-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="57254-196">另请参阅</span><span class="sxs-lookup"><span data-stu-id="57254-196">See Also</span></span>  
 <span data-ttu-id="57254-197">[数据库快照 (SQL Server)](database-snapshots-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="57254-197">[Database Snapshots &#40;SQL Server&#41;](database-snapshots-sql-server.md) </span></span>  
 <span data-ttu-id="57254-198">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="57254-198">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="57254-199">[sys.databases (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="57254-199">[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span></span>  
 [<span data-ttu-id="57254-200">数据库镜像和数据库快照 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="57254-200">Database Mirroring and Database Snapshots &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/database-mirroring-and-database-snapshots-sql-server.md)  
  
  
