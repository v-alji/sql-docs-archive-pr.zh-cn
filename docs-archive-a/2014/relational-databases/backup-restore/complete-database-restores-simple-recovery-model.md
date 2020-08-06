---
title: 完整数据库还原（简单恢复模式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- complete database restores
- database restores [SQL Server], complete database
- restoring databases [SQL Server], complete database
- simple recovery model [SQL Server]
- restoring [SQL Server], database
ms.assetid: 49828927-1727-4d1d-9ef5-3de43f68c026
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 67eee8d7d6f44c9ff83795bf2a8bd612309bf0a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591420"
---
# <a name="complete-database-restores-simple-recovery-model"></a><span data-ttu-id="6c139-102">完整数据库还原（简单恢复模式）</span><span class="sxs-lookup"><span data-stu-id="6c139-102">Complete Database Restores (Simple Recovery Model)</span></span>
  <span data-ttu-id="6c139-103">数据库完整还原的目的是还原整个数据库。</span><span class="sxs-lookup"><span data-stu-id="6c139-103">In a complete database restore, the goal is to restore the whole database.</span></span> <span data-ttu-id="6c139-104">整个数据库在还原期间处于脱机状态。</span><span class="sxs-lookup"><span data-stu-id="6c139-104">The whole database is offline for the duration of the restore.</span></span> <span data-ttu-id="6c139-105">在数据库的任何部分变为联机之前，必须将所有数据恢复到同一点，即数据库的所有部分都处于同一时间点并且不存在未提交的事务。</span><span class="sxs-lookup"><span data-stu-id="6c139-105">Before any part of the database can come online, all data is recovered to a consistent point in which all parts of the database are at the same point in time and no uncommitted transactions exist.</span></span>  
  
 <span data-ttu-id="6c139-106">在简单恢复模式下，数据库不能还原到特定备份中的特定时间点。</span><span class="sxs-lookup"><span data-stu-id="6c139-106">Under the simple recovery model, the database cannot be restored to a specific point in time within a specific backup.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6c139-107">建议您不要附加或还原来自未知或不可信源的数据库。</span><span class="sxs-lookup"><span data-stu-id="6c139-107">We recommend that you do not attach or restore databases from unknown or untrusted sources.</span></span> <span data-ttu-id="6c139-108">这些数据库可能包含执行非预期 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 代码的恶意代码，或通过修改架构或物理数据库结构导致错误。</span><span class="sxs-lookup"><span data-stu-id="6c139-108">These databases could contain malicious code that might execute unintended [!INCLUDE[tsql](../../../includes/tsql-md.md)] code or cause errors by modifying the schema or the physical database structure.</span></span> <span data-ttu-id="6c139-109">使用来自未知源或不可信源的数据库前，请在非生产服务器上针对数据库运行 [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) ，然后检查数据库中的代码，例如存储过程或其他用户定义代码。</span><span class="sxs-lookup"><span data-stu-id="6c139-109">Before you use a database from an unknown or untrusted source, run [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) on the database on a nonproduction server and also examine the code, such as stored procedures or other user-defined code, in the database.</span></span>  
  

  
> [!NOTE]  
>  <span data-ttu-id="6c139-110">有关支持从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的早期版本进行备份的信息，请参阅 [RESTORE (Transact-SQL)](/sql/t-sql/statements/restore-statements-transact-sql)中的“兼容性支持”部分。</span><span class="sxs-lookup"><span data-stu-id="6c139-110">For information about support for backups from earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see the "Compatibility Support" section of [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>  
  
##  <a name="overview-of-database-restore-under-the-simple-recovery-model"></a><a name="Overview"></a> <span data-ttu-id="6c139-111">在简单恢复模式下还原数据库的概述</span><span class="sxs-lookup"><span data-stu-id="6c139-111">Overview of Database Restore Under the Simple Recovery Model</span></span>  
 <span data-ttu-id="6c139-112">简单恢复模式下的完整数据库还原只涉及一个或两个 [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 语句，具体取决于是否需要还原差异数据库备份。</span><span class="sxs-lookup"><span data-stu-id="6c139-112">A full database restore under the simple recovery model involves one or two [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) statements, depending on whether you want to restore a differential database backup.</span></span> <span data-ttu-id="6c139-113">如果只使用完整数据库备份，则只需还原最近的备份，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="6c139-113">If you are using only a full database backup, just restore the most recent backup, as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="6c139-114">![仅还原完整数据库备份](../../database-engine/media/bnrr-rmsimple1-fulldbbu.gif "仅还原完整数据库备份")</span><span class="sxs-lookup"><span data-stu-id="6c139-114">![Restoring only a full database backup](../../database-engine/media/bnrr-rmsimple1-fulldbbu.gif "Restoring only a full database backup")</span></span>  
  
 <span data-ttu-id="6c139-115">如果还使用差异数据库备份，则应还原最近的完整数据库备份而不恢复数据库，然后还原最近的差异数据库备份并恢复数据库。</span><span class="sxs-lookup"><span data-stu-id="6c139-115">If you are also using a differential database backup, restore the most recent full database backup without recovering the database, and then restore the most recent differential database backup and recover the database.</span></span> <span data-ttu-id="6c139-116">下图显示了这一过程。</span><span class="sxs-lookup"><span data-stu-id="6c139-116">The following illustration shows this process.</span></span>  
  
 <span data-ttu-id="6c139-117">![还原完整数据库备份和差异数据库备份](../../database-engine/media/bnrr-rmsimple2-diffdbbu.gif "还原完整数据库备份和差异数据库备份")</span><span class="sxs-lookup"><span data-stu-id="6c139-117">![Restoring full and differential database backups](../../database-engine/media/bnrr-rmsimple2-diffdbbu.gif "Restoring full and differential database backups")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6c139-118">如果你计划将数据库备份还原到其它服务器实例，请参阅 [通过备份和还原来复制数据库](../databases/copy-databases-with-backup-and-restore.md)。</span><span class="sxs-lookup"><span data-stu-id="6c139-118">If you plan to restore a database backup onto a different server instance, see [Copy Databases with Backup and Restore](../databases/copy-databases-with-backup-and-restore.md).</span></span>  
  
###  <a name="basic-transact-sql-restore-syntax"></a><a name="TsqlSyntax"></a> <span data-ttu-id="6c139-119">基本 TRANSACT-SQL RESTORE 语法</span><span class="sxs-lookup"><span data-stu-id="6c139-119">Basic Transact-SQL RESTORE Syntax</span></span>  
 <span data-ttu-id="6c139-120">用于还原完整数据库备份的基本 [!INCLUDE[tsql](../../../includes/tsql-md.md)][RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 语法是：</span><span class="sxs-lookup"><span data-stu-id="6c139-120">The basic [!INCLUDE[tsql](../../../includes/tsql-md.md)][RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) syntax for restoring a full database backup is:</span></span>  
  
 <span data-ttu-id="6c139-121">RESTORE DATABASE *database_name* FROM *backup_device* [ WITH NORECOVERY ]</span><span class="sxs-lookup"><span data-stu-id="6c139-121">RESTORE DATABASE *database_name* FROM *backup_device* [ WITH NORECOVERY ]</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6c139-122">如果还打算还原差异数据库备份，则应使用 WITH NORECOVERY。</span><span class="sxs-lookup"><span data-stu-id="6c139-122">Use WITH NORECOVERY if you plan to also restore a differential database backup.</span></span>  
  
 <span data-ttu-id="6c139-123">用于还原数据库备份的 [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 语句的基本语法是：</span><span class="sxs-lookup"><span data-stu-id="6c139-123">The basic [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) syntax for restoring a database backup is:</span></span>  
  
 <span data-ttu-id="6c139-124">RESTORE DATABASE *database_name* FROM *backup_device* WITH RECOVERY</span><span class="sxs-lookup"><span data-stu-id="6c139-124">RESTORE DATABASE *database_name* FROM *backup_device* WITH RECOVERY</span></span>  
  
###  <a name="example-transact-sql"></a><a name="Example"></a> <span data-ttu-id="6c139-125">示例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6c139-125">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="6c139-126">以下示例首先显示如何使用 [BACKUP](/sql/t-sql/statements/backup-transact-sql) 语句来创建 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 数据库的完整数据库备份和差异数据库备份。</span><span class="sxs-lookup"><span data-stu-id="6c139-126">The following example first shows how to use the [BACKUP](/sql/t-sql/statements/backup-transact-sql) statement to create a full database backup and a differential database backup of the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="6c139-127">然后按顺序还原这些备份。</span><span class="sxs-lookup"><span data-stu-id="6c139-127">The example then restores these backups in sequence.</span></span> <span data-ttu-id="6c139-128">将数据库还原到完成差异数据库备份时的状态。</span><span class="sxs-lookup"><span data-stu-id="6c139-128">The database is restored to its state as of the time that the differential database backup finished.</span></span>  
  
 <span data-ttu-id="6c139-129">该示例说明数据库完整还原方案的还原序列中的关键选项。</span><span class="sxs-lookup"><span data-stu-id="6c139-129">The example shows the critical options in a restore sequence for the complete database restore scenario.</span></span> <span data-ttu-id="6c139-130">*还原顺序* 由通过一个或多个还原阶段来移动数据的一个或多个还原操作组成。</span><span class="sxs-lookup"><span data-stu-id="6c139-130">A *restore sequence* consists of one or more restore operations that move data through one or more of the phases of restore.</span></span> <span data-ttu-id="6c139-131">将省略与此目的不相关的语法和详细信息。</span><span class="sxs-lookup"><span data-stu-id="6c139-131">Syntax and details that are not relevant to this purpose are omitted.</span></span> <span data-ttu-id="6c139-132">在恢复数据库时，尽管 RECOVERY 选项是默认值，但为清楚起见，仍建议显式指定该选项。</span><span class="sxs-lookup"><span data-stu-id="6c139-132">When you recover a database, we recommend explicitly specifying the RECOVERY option for clarity, even though it is the default.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6c139-133">此示例以 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) 语句开头，该语句将恢复模式设置为 `SIMPLE`。</span><span class="sxs-lookup"><span data-stu-id="6c139-133">The example starts with an [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) statement that sets the recovery model to `SIMPLE`.</span></span>  
  
```  
USE master;  
--Make sure the database is using the simple recovery model.  
ALTER DATABASE AdventureWorks2012 SET RECOVERY SIMPLE;  
GO  
-- Back up the full AdventureWorks2012 database.  
BACKUP DATABASE AdventureWorks2012   
TO DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak'   
  WITH FORMAT;  
GO  
--Create a differential database backup.  
BACKUP DATABASE AdventureWorks2012   
TO DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak'  
   WITH DIFFERENTIAL;  
GO  
--Restore the full database backup (from backup set 1).  
RESTORE DATABASE AdventureWorks2012   
FROM DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak'   
   WITH FILE=1, NORECOVERY;  
--Restore the differential backup (from backup set 2).  
RESTORE DATABASE AdventureWorks2012   
FROM DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak'   
   WITH FILE=2, RECOVERY;  
GO  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="6c139-134">相关任务</span><span class="sxs-lookup"><span data-stu-id="6c139-134">Related Tasks</span></span>  
 <span data-ttu-id="6c139-135">**还原完整数据库备份**</span><span class="sxs-lookup"><span data-stu-id="6c139-135">**To restore a full database backup**</span></span>  
  
-   [<span data-ttu-id="6c139-136">在简单恢复模式下还原数据库备份 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6c139-136">Restore a Database Backup Under the Simple Recovery Model &#40;Transact-SQL&#41;</span></span>](restore-a-database-backup-under-the-simple-recovery-model-transact-sql.md)  
  
-   [<span data-ttu-id="6c139-137">还原数据库备份 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="6c139-137">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-backup-using-ssms.md)  
  
-   [<span data-ttu-id="6c139-138">将数据库还原到新位置 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6c139-138">Restore a Database to a New Location &#40;SQL Server&#41;</span></span>](restore-a-database-to-a-new-location-sql-server.md)  
  
 <span data-ttu-id="6c139-139">**还原差异数据库备份**</span><span class="sxs-lookup"><span data-stu-id="6c139-139">**To restore a differential database backup**</span></span>  
  
-   [<span data-ttu-id="6c139-140">还原差异数据库备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6c139-140">Restore a Differential Database Backup &#40;SQL Server&#41;</span></span>](restore-a-differential-database-backup-sql-server.md)  
  
 <span data-ttu-id="6c139-141">**使用 SQL Server 管理对象 (SMO) 还原备份**</span><span class="sxs-lookup"><span data-stu-id="6c139-141">**To restore a backup by using SQL Server Management Objects (SMO)**</span></span>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore%2A>  
  

  
## <a name="see-also"></a><span data-ttu-id="6c139-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6c139-142">See Also</span></span>  
 <span data-ttu-id="6c139-143">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6c139-143">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="6c139-144">[BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6c139-144">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="6c139-145">[sp_addumpdevice (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6c139-145">[sp_addumpdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span></span>  
 <span data-ttu-id="6c139-146">[完整数据库备份 (SQL Server)](full-database-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6c139-146">[Full Database Backups &#40;SQL Server&#41;](full-database-backups-sql-server.md) </span></span>  
 <span data-ttu-id="6c139-147">[差异备份 (SQL Server)](differential-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6c139-147">[Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md) </span></span>  
 <span data-ttu-id="6c139-148">[备份概述 (SQL Server)](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6c139-148">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 [<span data-ttu-id="6c139-149">还原和恢复概述 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6c139-149">Restore and Recovery Overview &#40;SQL Server&#41;</span></span>](restore-and-recovery-overview-sql-server.md)  
  
  
