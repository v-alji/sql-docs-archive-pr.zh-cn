---
title: 示例：数据库的段落还原（完整恢复模式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full recovery model [SQL Server], RESTORE example
- piecemeal restores [SQL Server], full recovery model
- restore sequences [SQL Server], piecemeal
ms.assetid: 0a84892d-2f7a-4e77-b2d0-d68b95595210
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5cfccccdbdc0c4fb3b189ee0a9fa3aeaf426578b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691261"
---
# <a name="example-piecemeal-restore-of-database-full-recovery-model"></a><span data-ttu-id="05889-102">示例：数据库的段落还原（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="05889-102">Example: Piecemeal Restore of Database (Full Recovery Model)</span></span>
  <span data-ttu-id="05889-103">段落还原顺序将从主文件组及所有具有读写权限的辅助文件组开始，在文件组级别分阶段还原和恢复数据库。</span><span class="sxs-lookup"><span data-stu-id="05889-103">A piecemeal restore sequence restores and recovers a database in stages at the filegroup level, beginning with the primary and all read-write, secondary filegroups.</span></span>  
  
 <span data-ttu-id="05889-104">在此示例中，灾难发生后，数据库 `adb` 被还原到新计算机。</span><span class="sxs-lookup"><span data-stu-id="05889-104">In this example, database `adb` is restored to a new computer after a disaster.</span></span> <span data-ttu-id="05889-105">该数据库使用完整恢复模式，因此，开始进行还原之前必须先获取数据库的结尾日志备份。</span><span class="sxs-lookup"><span data-stu-id="05889-105">The database is using the full recovery model; therefore, before the restore starts, a tail-log backup must be taken of the database.</span></span> <span data-ttu-id="05889-106">灾难发生之前，所有文件组均处于联机状态。</span><span class="sxs-lookup"><span data-stu-id="05889-106">Before the disaster, all the filegroups are online.</span></span> <span data-ttu-id="05889-107">文件组 `B` 是只读的。</span><span class="sxs-lookup"><span data-stu-id="05889-107">Filegroup `B` is read-only.</span></span> <span data-ttu-id="05889-108">必须还原所有辅助文件组，但这些辅助文件组将按重要性顺序进行还原： `A` （最高）， `C`其次，最后为 `B`。</span><span class="sxs-lookup"><span data-stu-id="05889-108">All of the secondary filegroups must be restored, but they are restored in order of importance: `A` (highest), `C`, and lastly `B`.</span></span> <span data-ttu-id="05889-109">在此示例中，存在四个日志备份，其中包括结尾日志备份。</span><span class="sxs-lookup"><span data-stu-id="05889-109">In this example, there are four log backups, including the tail-log backup.</span></span>  
  
## <a name="tail-log-backup"></a><span data-ttu-id="05889-110">结尾日志备份</span><span class="sxs-lookup"><span data-stu-id="05889-110">Tail-Log Backup</span></span>  
 <span data-ttu-id="05889-111">在还原数据库之前，数据库管理员必须备份日志尾部。</span><span class="sxs-lookup"><span data-stu-id="05889-111">Before restoring the database, the database administrator must back up the tail of the log.</span></span> <span data-ttu-id="05889-112">由于数据库已损坏，因此创建结尾日志备份需要使用 NO_TRUNCATE 选项：</span><span class="sxs-lookup"><span data-stu-id="05889-112">Because the database is damaged, creating the tail-log backup requires using the NO_TRUNCATE option:</span></span>  
  
```  
BACKUP LOG adb TO tailLogBackup WITH NORECOVERY, NO_TRUNCATE  
```  
  
 <span data-ttu-id="05889-113">结尾日志备份是在以下还原顺序中应用的最后一个备份。</span><span class="sxs-lookup"><span data-stu-id="05889-113">The tail-log backup is the last backup that is applied in the following restore sequences.</span></span>  
  
## <a name="restore-sequences"></a><span data-ttu-id="05889-114">还原顺序</span><span class="sxs-lookup"><span data-stu-id="05889-114">Restore Sequences</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="05889-115">联机还原顺序的语法与脱机还原顺序的语法完全相同。</span><span class="sxs-lookup"><span data-stu-id="05889-115">The syntax for an online restore sequence is the same as for an offline restore sequence.</span></span>  
  
1.  <span data-ttu-id="05889-116">部分还原主文件组和辅助文件组 `A`。</span><span class="sxs-lookup"><span data-stu-id="05889-116">Partial restore of the primary and secondary filegroup `A`.</span></span>  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='Primary' FROM backup1   
       WITH PARTIAL, NORECOVERY  
    RESTORE DATABASE adb FILEGROUP='A' FROM backup2   
       WITH NORECOVERY  
    RESTORE LOG adb FROM backup3 WITH NORECOVERY  
    RESTORE LOG adb FROM backup4 WITH NORECOVERY  
    RESTORE LOG adb FROM backup5 WITH NORECOVERY  
    RESTORE LOG adb FROM tailLogBackup WITH RECOVERY  
    ```  
  
2.  <span data-ttu-id="05889-117">对文件组 `C`进行联机还原。</span><span class="sxs-lookup"><span data-stu-id="05889-117">Online restore of filegroup `C`.</span></span>  
  
     <span data-ttu-id="05889-118">此时，主文件组和辅助文件组 `A` 处于联机状态。</span><span class="sxs-lookup"><span data-stu-id="05889-118">At this point, the primary filegroup and secondary filegroup `A` are online.</span></span> <span data-ttu-id="05889-119">文件组 `B` 和 `C` 中的所有文件都处于恢复挂起状态，这两个文件组处于脱机状态。</span><span class="sxs-lookup"><span data-stu-id="05889-119">All the files in filegroups `B` and `C` are recovery pending, and the filegroups are offline.</span></span>  
  
     <span data-ttu-id="05889-120">来自步骤 1 中的最后一条 `RESTORE LOG` 语句的消息指出：由于文件组 `C` 不可用，因此涉及此文件组的事务回滚已延迟。</span><span class="sxs-lookup"><span data-stu-id="05889-120">Messages from the last `RESTORE LOG` statement in step 1 indicate that rollback of transactions that involve filegroup `C` was deferred, because this filegroup is not available.</span></span> <span data-ttu-id="05889-121">可继续执行常规操作，但这些事务将持有锁并且在完成回滚前不会截断日志。</span><span class="sxs-lookup"><span data-stu-id="05889-121">Regular operations can continue, but locks are held by these transactions and log truncation will not occur until the rollback can complete.</span></span>  
  
     <span data-ttu-id="05889-122">在第二个还原顺序中，数据库管理员将还原文件组 `C`：</span><span class="sxs-lookup"><span data-stu-id="05889-122">In the second restore sequence, the database administrator restores filegroup `C`:</span></span>  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='C' FROM backup2a WITH NORECOVERY  
    RESTORE LOG adb FROM backup3 WITH NORECOVERY  
    RESTORE LOG adb FROM backup4 WITH NORECOVERY  
    RESTORE LOG adb FROM backup5 WITH NORECOVERY  
    RESTORE LOG adb FROM tailLogBackup WITH RECOVERY  
    ```  
  
     <span data-ttu-id="05889-123">此时，主文件组和文件组 `A` 以及 `C` 处于联机状态。</span><span class="sxs-lookup"><span data-stu-id="05889-123">At this point the primary and filegroups `A` and `C` are online.</span></span> <span data-ttu-id="05889-124">文件组 `B` 中的文件仍保持恢复挂起状态，而该文件组处于脱机状态。</span><span class="sxs-lookup"><span data-stu-id="05889-124">Files in filegroup `B` remain recovery pending, with the filegroup offline.</span></span> <span data-ttu-id="05889-125">解析延迟的事务后，日志被截断。</span><span class="sxs-lookup"><span data-stu-id="05889-125">Deferred transactions have been resolved, and log truncation occurs.</span></span>  
  
3.  <span data-ttu-id="05889-126">对文件组 `B`进行联机还原。</span><span class="sxs-lookup"><span data-stu-id="05889-126">Online restore of filegroup `B`.</span></span>  
  
     <span data-ttu-id="05889-127">在第三个还原顺序中，数据库管理员将还原文件组 `B`。</span><span class="sxs-lookup"><span data-stu-id="05889-127">In the third restore sequence, the database administrator restores filegroup `B`.</span></span> <span data-ttu-id="05889-128">文件组 `B` 的备份是在该文件组变为只读状态之后进行的，因此，在恢复过程中无需将其前滚。</span><span class="sxs-lookup"><span data-stu-id="05889-128">The backup of filegroup `B` was taken after the filegroup became read-only; therefore, it does not have to be rolled forward during recovery.</span></span>  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='B' FROM backup2b WITH RECOVERY  
    ```  
  
     <span data-ttu-id="05889-129">所有文件组现在都处于联机状态。</span><span class="sxs-lookup"><span data-stu-id="05889-129">All filegroups are now online.</span></span>  
  
## <a name="additional-examples"></a><span data-ttu-id="05889-130">其他示例</span><span class="sxs-lookup"><span data-stu-id="05889-130">Additional Examples</span></span>  
  
-   [<span data-ttu-id="05889-131">示例：数据库的段落还原（简单恢复模式）</span><span class="sxs-lookup"><span data-stu-id="05889-131">Example: Piecemeal Restore of Database &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [<span data-ttu-id="05889-132">示例：仅对某些文件组进行段落还原（简单恢复模式）</span><span class="sxs-lookup"><span data-stu-id="05889-132">Example: Piecemeal Restore of Only Some Filegroups &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [<span data-ttu-id="05889-133">示例：只读文件的联机还原（简单恢复模式）</span><span class="sxs-lookup"><span data-stu-id="05889-133">Example: Online Restore of a Read-Only File &#40;Simple Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [<span data-ttu-id="05889-134">示例：仅对某些文件组进行段落还原（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="05889-134">Example: Piecemeal Restore of Only Some Filegroups &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [<span data-ttu-id="05889-135">示例：读/写文件的联机还原（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="05889-135">Example: Online Restore of a Read-Write File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
-   [<span data-ttu-id="05889-136">示例：只读文件的联机还原（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="05889-136">Example: Online Restore of a Read-Only File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="05889-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="05889-137">See Also</span></span>  
 <span data-ttu-id="05889-138">[BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="05889-138">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="05889-139">[联机还原 (SQL Server)](online-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="05889-139">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span></span>  
 <span data-ttu-id="05889-140">[应用事务日志备份 (SQL Server)](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="05889-140">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 <span data-ttu-id="05889-141">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="05889-141">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="05889-142">段落还原 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="05889-142">Piecemeal Restores &#40;SQL Server&#41;</span></span>](piecemeal-restores-sql-server.md)  
  
  
