---
title: 恢复数据库但不还原数据 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- restoring [SQL Server], recovery-only
- recovery-only scenario [SQL Server]
- restoring databases [SQL Server], recovery-only
- recovery [SQL Server], recovery-only
- database recovery [SQL Server]
- database restores [SQL Server], recovery-only
- recovery [SQL Server], without restoring data
ms.assetid: 7e8fa620-315d-4e10-a718-23fa5171c09e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 04e4f78e51adb803bb65530c0b3b903aa7f76419
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589175"
---
# <a name="recover-a-database-without-restoring-data-transact-sql"></a><span data-ttu-id="bf3f1-102">恢复数据库但不还原数据 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="bf3f1-102">Recover a Database Without Restoring Data (Transact-SQL)</span></span>
  <span data-ttu-id="bf3f1-103">通常，恢复数据库之前，将还原 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库中的所有数据。</span><span class="sxs-lookup"><span data-stu-id="bf3f1-103">Usually, all of the data in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database is restored before the database is recovered.</span></span> <span data-ttu-id="bf3f1-104">但是，还原操作可以恢复数据库而不实际还原备份；例如，恢复那些与数据库一致的只读文件时。</span><span class="sxs-lookup"><span data-stu-id="bf3f1-104">However, a restore operation can recover a database without actually restoring a backup; for example, when recovering a read-only file that is consistent with the database.</span></span> <span data-ttu-id="bf3f1-105">这称为仅恢复还原。</span><span class="sxs-lookup"><span data-stu-id="bf3f1-105">This is referred to as a *recovery-only restore*.</span></span> <span data-ttu-id="bf3f1-106">当脱机数据已与数据库一致且只需变为可用时，仅恢复还原操作将完成恢复数据库并使数据联机。</span><span class="sxs-lookup"><span data-stu-id="bf3f1-106">When offline data is already consistent with the database and needs only to be made available, a recovery-only restore operation completes the recovery of the database and bring the data online.</span></span>  
  
 <span data-ttu-id="bf3f1-107">仅恢复还原可以针对整个数据库或一个或多个文件或文件组进行。</span><span class="sxs-lookup"><span data-stu-id="bf3f1-107">A recovery-only restore can occur for a whole database or for one or more a files or filegroups.</span></span>  
  
## <a name="recovery-only-database-restore"></a><span data-ttu-id="bf3f1-108">仅恢复数据库还原</span><span class="sxs-lookup"><span data-stu-id="bf3f1-108">Recovery-Only Database Restore</span></span>  
 <span data-ttu-id="bf3f1-109">在以下情况下仅恢复数据库还原十分有用：</span><span class="sxs-lookup"><span data-stu-id="bf3f1-109">A recovery-only database restore can be useful in the following situations:</span></span>  
  
-   <span data-ttu-id="bf3f1-110">您未在还原位于还原顺序中的最后备份时恢复数据库，现在希望恢复该数据库并使其联机。</span><span class="sxs-lookup"><span data-stu-id="bf3f1-110">You did not recover the database when restoring the last backup in a restore sequence, and you now want to recover the database to bring it online.</span></span>  
  
-   <span data-ttu-id="bf3f1-111">数据库处于备用模式，但您希望在不应用其他日志备份的情况下可以更新数据库。</span><span class="sxs-lookup"><span data-stu-id="bf3f1-111">The database is in standby mode, and you want to make the database updatable without applying another log backup.</span></span>  
  
 <span data-ttu-id="bf3f1-112">仅恢复数据库还原的 [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 语法是：</span><span class="sxs-lookup"><span data-stu-id="bf3f1-112">The [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) syntax for a recovery-only database restore is as follows:</span></span>  
  
 <span data-ttu-id="bf3f1-113">RESTORE DATABASE *database_name* WITH RECOVERY</span><span class="sxs-lookup"><span data-stu-id="bf3f1-113">RESTORE DATABASE *database_name* WITH RECOVERY</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bf3f1-114">未使用 FROM = \<*backup_device>\* 子句进行仅恢复还原，因为不需要任何备份。</span><span class="sxs-lookup"><span data-stu-id="bf3f1-114">The FROM **=** \<*backup_device>\* clause is not used for recovery-only restores because no backup is necessary.</span></span>  
  
 <span data-ttu-id="bf3f1-115">**示例**</span><span class="sxs-lookup"><span data-stu-id="bf3f1-115">**Example**</span></span>  
  
 <span data-ttu-id="bf3f1-116">以下示例在还原操作中恢复 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 示例数据库而不还原数据。</span><span class="sxs-lookup"><span data-stu-id="bf3f1-116">The following example recovers the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database in a restore operation without restoring data.</span></span>  
  
```  
-- Restore database using WITH RECOVERY.  
RESTORE DATABASE AdventureWorks2012  
   WITH RECOVERY  
```  
  
## <a name="recovery-only-file-restore"></a><span data-ttu-id="bf3f1-117">仅恢复文件还原</span><span class="sxs-lookup"><span data-stu-id="bf3f1-117">Recovery-Only File Restore</span></span>  
 <span data-ttu-id="bf3f1-118">在以下情况下仅恢复文件还原十分有用：</span><span class="sxs-lookup"><span data-stu-id="bf3f1-118">A recovery-only file restore can be useful in the following situation:</span></span>  
  
 <span data-ttu-id="bf3f1-119">数据库按段落进行还原。</span><span class="sxs-lookup"><span data-stu-id="bf3f1-119">A database is restored piecemeal.</span></span> <span data-ttu-id="bf3f1-120">完成主文件组的还原之后，一个或多个未还原的文件变为与新数据库的状态一致，这也许是因为这些文件最近始终是只读的。</span><span class="sxs-lookup"><span data-stu-id="bf3f1-120">After restore of the primary filegroup is complete, one or more of the unrestored files are consistent with the new database state, perhaps because it has been read-only for some time.</span></span> <span data-ttu-id="bf3f1-121">只需恢复这些文件即可；无需复制数据。</span><span class="sxs-lookup"><span data-stu-id="bf3f1-121">These files only have to be recovered; data copying is unnecessary.</span></span>  
  
 <span data-ttu-id="bf3f1-122">仅恢复还原操作将脱机文件组中的数据变为联机状态；不会有数据复制、重做或撤消这些阶段。</span><span class="sxs-lookup"><span data-stu-id="bf3f1-122">A recovery-only restore operation brings the data in the offline filegroup online; no data-copy, redo, or undo phase occurs.</span></span> <span data-ttu-id="bf3f1-123">有关还原阶段的信息，请参阅[还原和恢复概述 (SQL Server) ](restore-and-recovery-overview-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="bf3f1-123">For information about the phases of restore, see [Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md).</span></span>  
  
 <span data-ttu-id="bf3f1-124">仅恢复文件还原的 [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 语法是：</span><span class="sxs-lookup"><span data-stu-id="bf3f1-124">The [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) syntax for a recovery-only file restore is:</span></span>  
  
 <span data-ttu-id="bf3f1-125">*Database_name* {FILE **=** _logical_file_name_还原数据库 |FILEGROUP **=** _logical_filegroup_name_ } [ **，**.。。*n* ] 与恢复</span><span class="sxs-lookup"><span data-stu-id="bf3f1-125">RESTORE DATABASE *database_name* { FILE **=**_logical_file_name_ | FILEGROUP **=**_logical_filegroup_name_ }[ **,**...*n* ] WITH RECOVERY</span></span>  
  
 <span data-ttu-id="bf3f1-126">**示例**</span><span class="sxs-lookup"><span data-stu-id="bf3f1-126">**Example**</span></span>  
  
 <span data-ttu-id="bf3f1-127">以下示例显示了 `SalesGroup2`数据库中辅助文件组 `Sales` 中文件的仅恢复文件还原。</span><span class="sxs-lookup"><span data-stu-id="bf3f1-127">The following example illustrates a recovery-only file restore of the files in a secondary filegroup, `SalesGroup2`, in the `Sales` database.</span></span> <span data-ttu-id="bf3f1-128">已在段落还原的初始步骤中还原了主文件组，并且 `SalesGroup2` 与还原的主文件组一致。</span><span class="sxs-lookup"><span data-stu-id="bf3f1-128">The primary filegroup has already been restored as the initial step of a piecemeal restore, and `SalesGroup2` is consistent with the restored primary filegroup.</span></span> <span data-ttu-id="bf3f1-129">只需一条语句即可恢复此文件组并使其变为联机状态。</span><span class="sxs-lookup"><span data-stu-id="bf3f1-129">Recovering this filegroup and bringing it online requires only a single statement.</span></span>  
  
```  
RESTORE DATABASE Sales FILEGROUP=SalesGroup2 WITH RECOVERY;  
```  
  
## <a name="examples-of-completing-a-piecemeal-restore-scenario-with-a-recovery-only-restore"></a><span data-ttu-id="bf3f1-130">使用仅恢复还原完成段落还原方案的示例</span><span class="sxs-lookup"><span data-stu-id="bf3f1-130">Examples of Completing a Piecemeal Restore Scenario with a Recovery-Only Restore</span></span>  
 <span data-ttu-id="bf3f1-131">**简单恢复模式**</span><span class="sxs-lookup"><span data-stu-id="bf3f1-131">**Simple recovery model**</span></span>  
  
-   [<span data-ttu-id="bf3f1-132">示例：数据库的段落还原（简单恢复模式）</span><span class="sxs-lookup"><span data-stu-id="bf3f1-132">Example: Piecemeal Restore of Database &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [<span data-ttu-id="bf3f1-133">示例：仅对某些文件组进行段落还原（简单恢复模式）</span><span class="sxs-lookup"><span data-stu-id="bf3f1-133">Example: Piecemeal Restore of Only Some Filegroups &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
 <span data-ttu-id="bf3f1-134">**完整恢复模式**</span><span class="sxs-lookup"><span data-stu-id="bf3f1-134">**Full recovery model**</span></span>  
  
-   [<span data-ttu-id="bf3f1-135">示例：数据库的段落还原（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="bf3f1-135">Example: Piecemeal Restore of Database &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [<span data-ttu-id="bf3f1-136">示例：仅对某些文件组进行段落还原（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="bf3f1-136">Example: Piecemeal Restore of Only Some Filegroups &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore%2A>  
  
## <a name="see-also"></a><span data-ttu-id="bf3f1-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bf3f1-137">See Also</span></span>  
 <span data-ttu-id="bf3f1-138">[联机还原 (SQL Server)](online-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="bf3f1-138">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span></span>  
 <span data-ttu-id="bf3f1-139">[段落还原 (SQL Server)](piecemeal-restores-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="bf3f1-139">[Piecemeal Restores &#40;SQL Server&#41;](piecemeal-restores-sql-server.md) </span></span>  
 <span data-ttu-id="bf3f1-140">[文件还原（简单恢复模式）](file-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="bf3f1-140">[File Restores &#40;Simple Recovery Model&#41;](file-restores-simple-recovery-model.md) </span></span>  
 <span data-ttu-id="bf3f1-141">[文件还原（完整恢复模式）](file-restores-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="bf3f1-141">[File Restores &#40;Full Recovery Model&#41;](file-restores-full-recovery-model.md) </span></span>  
 [<span data-ttu-id="bf3f1-142">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bf3f1-142">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
