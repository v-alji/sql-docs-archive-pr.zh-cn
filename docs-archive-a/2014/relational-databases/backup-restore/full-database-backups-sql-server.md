---
title: 完整数据库备份 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full backups [SQL Server]
- backups [SQL Server], database
- backing up databases [SQL Server], full backups
- estimating database backup size
- backing up [SQL Server], size of backup
- database backups [SQL Server], full backups
- size [SQL Server], backups
- database backups [SQL Server], about backing up databases
ms.assetid: 4d933d19-8d21-4aa1-8153-d230cb3a3f99
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ee871b6cabbe6c2b2cb4f444fd1e2d42d711dfbc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689453"
---
# <a name="full-database-backups-sql-server"></a><span data-ttu-id="23ab5-102">完整数据库备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="23ab5-102">Full Database Backups (SQL Server)</span></span>
  <span data-ttu-id="23ab5-103">完整数据库备份可对整个数据库进行备份。</span><span class="sxs-lookup"><span data-stu-id="23ab5-103">A full database backup backs up the whole database.</span></span> <span data-ttu-id="23ab5-104">这包括对部分事务日志进行备份，以便在还原完整数据库备份之后，能够恢复完整数据库备份。</span><span class="sxs-lookup"><span data-stu-id="23ab5-104">This includes part of the transaction log so that the full database can be recovered after a full database backup is restored.</span></span> <span data-ttu-id="23ab5-105">完整数据库备份表示备份完成时的数据库。</span><span class="sxs-lookup"><span data-stu-id="23ab5-105">Full database backups represent the database at the time the backup finished.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="23ab5-106">随着数据库不断增大，完整备份需花费更多时间才能完成，并且需要更多的存储空间。</span><span class="sxs-lookup"><span data-stu-id="23ab5-106">As a database increases in size full database backups take more time to finish and require more storage space.</span></span> <span data-ttu-id="23ab5-107">因此，对于大型数据库而言，您可以用一系列“差异数据库备份”  来补充完整数据库备份。</span><span class="sxs-lookup"><span data-stu-id="23ab5-107">Therefore, for a large database, you might want to supplement a full database backup with a series of *differential database backups*.</span></span> <span data-ttu-id="23ab5-108">有关详细信息，请参阅 [差异备份 (SQL Server)](differential-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="23ab5-108">For more information, see [Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="23ab5-109">针对数据库备份，TRUSTWORTHY 设置为 OFF。</span><span class="sxs-lookup"><span data-stu-id="23ab5-109">TRUSTWORTHY is set to OFF on a database backup.</span></span> <span data-ttu-id="23ab5-110">有关如何将 TRUSTWORTHY 设置为 ON 的详细信息，请参阅 [ALTER DATABASE SET 选项 (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-set-options)。</span><span class="sxs-lookup"><span data-stu-id="23ab5-110">For information about how to set TRUSTWORTHY to ON, see [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span>  
  
 <span data-ttu-id="23ab5-111">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="23ab5-111">**In This Topic:**</span></span>  
  
-   [<span data-ttu-id="23ab5-112">简单恢复模式下的数据库备份</span><span class="sxs-lookup"><span data-stu-id="23ab5-112">Database Backups Under the Simple Recovery Model</span></span>](#DbBuRMs)  
  
-   [<span data-ttu-id="23ab5-113">完整恢复模式下的数据库备份</span><span class="sxs-lookup"><span data-stu-id="23ab5-113">Database Backups Under the Full Recovery Model</span></span>](#DbBuRMf)  
  
-   [<span data-ttu-id="23ab5-114">使用完整数据库备份还原数据库</span><span class="sxs-lookup"><span data-stu-id="23ab5-114">Use a Full Database Backup to Restore the Database</span></span>](#RestoreDbBu)  
  
-   [<span data-ttu-id="23ab5-115">相关任务</span><span class="sxs-lookup"><span data-stu-id="23ab5-115">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="database-backups-under-the-simple-recovery-model"></a><a name="DbBuRMs"></a> <span data-ttu-id="23ab5-116">简单恢复模式下的数据库备份</span><span class="sxs-lookup"><span data-stu-id="23ab5-116">Database Backups Under the Simple Recovery Model</span></span>  
 <span data-ttu-id="23ab5-117">在简单恢复模式下，每次备份后，如果出现严重故障，数据库将有可能丢失工作。</span><span class="sxs-lookup"><span data-stu-id="23ab5-117">Under the simple recovery model, after each backup, the database is exposed to potential work loss if a disaster were to occur.</span></span> <span data-ttu-id="23ab5-118">每次更新都会增加丢失工作的风险，这种情况将一直持续到下一次备份。这时，工作丢失风险将变为零，并开始新一轮的工作丢失风险。</span><span class="sxs-lookup"><span data-stu-id="23ab5-118">The work-loss exposure increases with each update until the next backup, when the work-loss exposure returns to zero and a new cycle of work-loss exposure starts.</span></span> <span data-ttu-id="23ab5-119">备份之间的工作丢失风险随着时间的推移而增加。</span><span class="sxs-lookup"><span data-stu-id="23ab5-119">Work-loss exposure increases over time between backups.</span></span> <span data-ttu-id="23ab5-120">下图显示了仅使用完整数据库备份的备份策略的工作丢失风险。</span><span class="sxs-lookup"><span data-stu-id="23ab5-120">The following illustration shows the work-loss exposure for a backup strategy that uses only full database backups.</span></span>  
  
 <span data-ttu-id="23ab5-121">![显示数据库备份之间的工作丢失风险](../../database-engine/media/bnr-rmsimple-1-fulldb-backups.gif "显示数据库备份之间的工作丢失风险")</span><span class="sxs-lookup"><span data-stu-id="23ab5-121">![Shows work-loss exposure between database backups](../../database-engine/media/bnr-rmsimple-1-fulldb-backups.gif "Shows work-loss exposure between database backups")</span></span>  
  
### <a name="example--tsql"></a><span data-ttu-id="23ab5-122">示例 ([!INCLUDE[tsql](../../../includes/tsql-md.md)])</span><span class="sxs-lookup"><span data-stu-id="23ab5-122">Example ( [!INCLUDE[tsql](../../../includes/tsql-md.md)])</span></span>  
 <span data-ttu-id="23ab5-123">下面的示例说明了如何使用 WITH FORMAT 覆盖任意现有备份并创建新介质集，从而创建一个完整数据库备份。</span><span class="sxs-lookup"><span data-stu-id="23ab5-123">The following example shows how to create a full database backup by using WITH FORMAT to overwrite any existing backups and create a new media set.</span></span>  
  
```  
-- Back up the AdventureWorks2012 database to new media set.  
BACKUP DATABASE AdventureWorks2012  
    TO DISK = 'Z:\SQLServerBackups\AdventureWorksSimpleRM.bak'   
    WITH FORMAT;  
GO  
```  
  
##  <a name="database-backups-under-the-full-recovery-model"></a><a name="DbBuRMf"></a> <span data-ttu-id="23ab5-124">完整恢复模式下的数据库备份</span><span class="sxs-lookup"><span data-stu-id="23ab5-124">Database Backups Under the Full Recovery Model</span></span>  
 <span data-ttu-id="23ab5-125">对于使用完整恢复模式和大容量日志恢复模式的数据库而言，数据库备份是必需的，但并不足够。</span><span class="sxs-lookup"><span data-stu-id="23ab5-125">For databases that use full and bulk-logged recovery, database backups are necessary but not sufficient.</span></span> <span data-ttu-id="23ab5-126">还需要事务日志备份。</span><span class="sxs-lookup"><span data-stu-id="23ab5-126">Transaction log backups are also required.</span></span> <span data-ttu-id="23ab5-127">下图显示了在完整恢复模式下可以使用的复杂性最小的备份策略。</span><span class="sxs-lookup"><span data-stu-id="23ab5-127">The following illustration shows the least complex backup strategy that is possible under the full recovery model.</span></span>  
  
 <span data-ttu-id="23ab5-128">![一系列完整数据库备份和日志备份](../../database-engine/media/bnr-rmfull-1-fulldb-log-backups.gif "一系列完整数据库备份和日志备份")</span><span class="sxs-lookup"><span data-stu-id="23ab5-128">![Series of full database backups and log backups](../../database-engine/media/bnr-rmfull-1-fulldb-log-backups.gif "Series of full database backups and log backups")</span></span>  
  
 <span data-ttu-id="23ab5-129">有关如何创建日志备份的信息，请参阅[事务日志备份 (SQL Server)](transaction-log-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="23ab5-129">For information about how to create log backups, see [Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md).</span></span>  
  
### <a name="example--tsql"></a><span data-ttu-id="23ab5-130">示例 ([!INCLUDE[tsql](../../../includes/tsql-md.md)])</span><span class="sxs-lookup"><span data-stu-id="23ab5-130">Example ( [!INCLUDE[tsql](../../../includes/tsql-md.md)])</span></span>  
 <span data-ttu-id="23ab5-131">下面的示例说明了如何使用 WITH FORMAT 覆盖任意现有备份并创建新介质集，从而创建一个完整数据库备份。</span><span class="sxs-lookup"><span data-stu-id="23ab5-131">The following example shows how to create a full database backup by using WITH FORMAT to overwrite any existing backups and create a new media set.</span></span> <span data-ttu-id="23ab5-132">然后，此示例将备份事务日志。</span><span class="sxs-lookup"><span data-stu-id="23ab5-132">Then, the example backs up the transaction log.</span></span> <span data-ttu-id="23ab5-133">在现实情况下，您必须执行一系列的定期日志备份。</span><span class="sxs-lookup"><span data-stu-id="23ab5-133">In a real-life situation, you would have to perform a series of regular log backups.</span></span> <span data-ttu-id="23ab5-134">在此示例中， [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 示例数据库设置为使用完整恢复模式。</span><span class="sxs-lookup"><span data-stu-id="23ab5-134">For this example, the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database is set to use the full recovery model.</span></span>  
  
```  
USE master;  
ALTER DATABASE AdventureWorks2012 SET RECOVERY FULL;  
GO  
-- Back up the AdventureWorks2012 database to new media set (backup set 1).  
BACKUP DATABASE AdventureWorks2012  
  TO DISK = 'Z:\SQLServerBackups\AdventureWorks2012FullRM.bak'   
  WITH FORMAT;  
GO  
--Create a routine log backup (backup set 2).  
BACKUP LOG AdventureWorks2012 TO DISK = 'Z:\SQLServerBackups\AdventureWorks2012FullRM.bak';  
GO  
```  
  
##  <a name="use-a-full-database-backup-to-restore-the-database"></a><a name="RestoreDbBu"></a> <span data-ttu-id="23ab5-135">使用完整数据库备份还原数据库</span><span class="sxs-lookup"><span data-stu-id="23ab5-135">Use a Full Database Backup to Restore the Database</span></span>  
 <span data-ttu-id="23ab5-136">您可以通过将数据库从完整数据库备份还原到任意位置的方法一步完成整个数据库的重新创建。</span><span class="sxs-lookup"><span data-stu-id="23ab5-136">You can re-create a whole database in one step by restoring the database from a full database backup to any location.</span></span> <span data-ttu-id="23ab5-137">备份中包含了足够的事务日志，这使您能够将数据库恢复到备份完成的时间。</span><span class="sxs-lookup"><span data-stu-id="23ab5-137">Enough of the transaction log is included in the backup to let you recover the database to the time when the backup finished.</span></span> <span data-ttu-id="23ab5-138">还原的数据库将与还原数据库备份完成时的原始数据库状态相符，但不包含任何未提交的事务。</span><span class="sxs-lookup"><span data-stu-id="23ab5-138">The restored database matches the state of the original database when the database backup finished, minus any uncommitted transactions.</span></span> <span data-ttu-id="23ab5-139">在完整恢复模式下，随后应还原所有后续日志备份。</span><span class="sxs-lookup"><span data-stu-id="23ab5-139">Under the full recovery model, you should then restore all subsequent transaction log backups.</span></span> <span data-ttu-id="23ab5-140">恢复数据库后，将回滚未提交的事务。</span><span class="sxs-lookup"><span data-stu-id="23ab5-140">When the database is recovered, uncommitted transactions are rolled back.</span></span>  
  
 <span data-ttu-id="23ab5-141">有关详细信息，请参阅[完整数据库还原（简单恢复模式）](complete-database-restores-simple-recovery-model.md)或[数据库还原（完整恢复模式）](complete-database-restores-full-recovery-model.md)。</span><span class="sxs-lookup"><span data-stu-id="23ab5-141">For more information, see [Complete Database Restores &#40;Simple Recovery Model&#41;](complete-database-restores-simple-recovery-model.md) or [Complete Database Restores &#40;Full Recovery Model&#41;](complete-database-restores-full-recovery-model.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="23ab5-142">相关任务</span><span class="sxs-lookup"><span data-stu-id="23ab5-142">Related Tasks</span></span>  
 <span data-ttu-id="23ab5-143">**创建完整数据库备份**</span><span class="sxs-lookup"><span data-stu-id="23ab5-143">**To create a full database backup**</span></span>  
  
-   [<span data-ttu-id="23ab5-144">创建完整数据库备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="23ab5-144">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](create-a-full-database-backup-sql-server.md)  
  
-   <span data-ttu-id="23ab5-145"><xref:Microsoft.SqlServer.Management.Smo.Backup.SqlBackup%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="23ab5-145"><xref:Microsoft.SqlServer.Management.Smo.Backup.SqlBackup%2A> (SMO)</span></span>  
  
 <span data-ttu-id="23ab5-146">**计划备份作业**</span><span class="sxs-lookup"><span data-stu-id="23ab5-146">**To schedule backup jobs**</span></span>  
  
 [<span data-ttu-id="23ab5-147">使用维护计划向导</span><span class="sxs-lookup"><span data-stu-id="23ab5-147">Use the Maintenance Plan Wizard</span></span>](../maintenance-plans/use-the-maintenance-plan-wizard.md)  
  
## <a name="see-also"></a><span data-ttu-id="23ab5-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="23ab5-148">See Also</span></span>  
 <span data-ttu-id="23ab5-149">[SQL Server 数据库的备份和还原](back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="23ab5-149">[Back Up and Restore of SQL Server Databases](back-up-and-restore-of-sql-server-databases.md) </span></span>  
 <span data-ttu-id="23ab5-150">[备份概述 (SQL Server)](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="23ab5-150">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 [<span data-ttu-id="23ab5-151">备份和还原 Analysis Services 数据库</span><span class="sxs-lookup"><span data-stu-id="23ab5-151">Backup and Restore of Analysis Services Databases</span></span>](https://docs.microsoft.com/analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases)  
  
  
