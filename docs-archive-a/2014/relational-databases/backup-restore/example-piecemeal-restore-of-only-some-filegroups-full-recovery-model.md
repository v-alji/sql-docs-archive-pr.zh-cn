---
title: 示例：仅对某些文件组进行段落还原（完整恢复模式）| Microsoft Docs
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
ms.assetid: bced4b54-e819-472b-b784-c72e14e72a0b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b3cb1a5ea33a5016c99fdf1f5a7f4e892c045b59
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693997"
---
# <a name="example-piecemeal-restore-of-only-some-filegroups-full-recovery-model"></a><span data-ttu-id="e217e-102">示例：仅对某些文件组进行段落还原（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="e217e-102">Example: Piecemeal Restore of Only Some Filegroups (Full Recovery Model)</span></span>
  <span data-ttu-id="e217e-103">本主题与完整恢复模式下包含多个文件或文件组的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库相关。</span><span class="sxs-lookup"><span data-stu-id="e217e-103">This topic is relevant for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases under the full recovery model that contain multiple files or filegroups.</span></span>  
  
 <span data-ttu-id="e217e-104">段落还原顺序将从主文件组和所有读写辅助文件组开始，按文件组级别分阶段还原和恢复数据库。</span><span class="sxs-lookup"><span data-stu-id="e217e-104">A piecemeal restore sequence restores and recovers a database in stages at the filegroup level, starting with the primary and all read/write, secondary filegroups.</span></span>  
  
 <span data-ttu-id="e217e-105">在此示例中，名为 `adb`的数据库（使用完整恢复模式）包含三个文件组。</span><span class="sxs-lookup"><span data-stu-id="e217e-105">In this example, a database named `adb`, which uses the full recovery model, contains three filegroups.</span></span> <span data-ttu-id="e217e-106">文件组 `A` 为读/写文件组，文件组 `B` 和文件组 `C` 为只读文件组。</span><span class="sxs-lookup"><span data-stu-id="e217e-106">Filegroup `A` is read/write, and filegroup `B` and filegroup `C` are read-only.</span></span> <span data-ttu-id="e217e-107">最初，所有文件组都处于联机状态。</span><span class="sxs-lookup"><span data-stu-id="e217e-107">Initially, all of the filegroups are online.</span></span>  
  
 <span data-ttu-id="e217e-108">数据库 `B` 的主文件组和文件组 `adb` 显示为已损坏。</span><span class="sxs-lookup"><span data-stu-id="e217e-108">The primary and filegroup `B` of database `adb` appear to be damaged.</span></span> <span data-ttu-id="e217e-109">主文件组很小，可以快速还原。</span><span class="sxs-lookup"><span data-stu-id="e217e-109">The primary filegroup is fairly small and can be restored quickly.</span></span> <span data-ttu-id="e217e-110">数据库管理员决定使用段落还原顺序还原这些文件组。</span><span class="sxs-lookup"><span data-stu-id="e217e-110">The database administrator decides to restore them by using a piecemeal restore sequence.</span></span> <span data-ttu-id="e217e-111">首先，还原主文件组和后续事务日志，并恢复数据库。</span><span class="sxs-lookup"><span data-stu-id="e217e-111">First, the primary filegroup and the subsequent transaction logs are restored the database is recovered.</span></span>  
  
 <span data-ttu-id="e217e-112">完好的文件组 `A` 和 `C` 包含关键数据。</span><span class="sxs-lookup"><span data-stu-id="e217e-112">The intact filegroups `A` and `C` contain critical data.</span></span> <span data-ttu-id="e217e-113">因此，接着对它们进行还原，以尽快使它们处于联机状态。</span><span class="sxs-lookup"><span data-stu-id="e217e-113">Therefore, they will be recovered next to bring them online as quickly as possible.</span></span> <span data-ttu-id="e217e-114">最后，还原和恢复损坏的辅助文件组 `B`。</span><span class="sxs-lookup"><span data-stu-id="e217e-114">Finally, the damaged secondary filegroup, `B`, is restored and recovered.</span></span>  
  
## <a name="restore-sequences"></a><span data-ttu-id="e217e-115">还原顺序：</span><span class="sxs-lookup"><span data-stu-id="e217e-115">Restore Sequences:</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e217e-116">联机还原顺序的语法与脱机还原顺序的语法完全相同。</span><span class="sxs-lookup"><span data-stu-id="e217e-116">The syntax for an online restore sequence is the same as for an offline restore sequence.</span></span>  
  
1.  <span data-ttu-id="e217e-117">创建数据库 `adb`的结尾日志备份。</span><span class="sxs-lookup"><span data-stu-id="e217e-117">Create a tail log backup of database `adb`.</span></span> <span data-ttu-id="e217e-118">此步骤对于使完好文件组 `A` 和 `C` 与数据库恢复点保持同步至关重要。</span><span class="sxs-lookup"><span data-stu-id="e217e-118">This step is essential to make the intact filegroups `A` and `C` current with the recovery point of the database.</span></span>  
  
    ```  
    BACKUP LOG adb TO tailLogBackup WITH NORECOVERY  
    ```  
  
2.  <span data-ttu-id="e217e-119">对主文件组进行部分还原。</span><span class="sxs-lookup"><span data-stu-id="e217e-119">Partial restore of the primary filegroup.</span></span>  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='Primary' FROM backup   
    WITH PARTIAL, NORECOVERY  
    RESTORE LOG adb FROM backup1 WITH NORECOVERY  
    RESTORE LOG adb FROM backup2 WITH NORECOVERY  
    RESTORE LOG adb FROM backup3 WITH NORECOVERY  
    RESTORE LOG adb FROM tailLogBackup WITH RECOVERY  
    ```  
  
     <span data-ttu-id="e217e-120">此时主文件组处于联机状态。</span><span class="sxs-lookup"><span data-stu-id="e217e-120">At this point the primary is online.</span></span> <span data-ttu-id="e217e-121">文件组 `A`、 `B`和 `C` 中的文件处于恢复挂起状态，这几个文件组则处于脱机状态。</span><span class="sxs-lookup"><span data-stu-id="e217e-121">Files in filegroups `A`, `B`, and `C` are recovery pending, and the filegroups are offline.</span></span>  
  
3.  <span data-ttu-id="e217e-122">对文件组 `A` 和 `C`进行联机还原。</span><span class="sxs-lookup"><span data-stu-id="e217e-122">Online restore of filegroups `A` and `C`.</span></span>  
  
     <span data-ttu-id="e217e-123">由于这些文件组中的数据并没有损坏，因此不需要从备份中还原这些文件组，但需要恢复以使它们联机。</span><span class="sxs-lookup"><span data-stu-id="e217e-123">Because their data is undamaged, these filegroups do not have to be restored from a backup, but they do have to be recovered to bring them online.</span></span>  
  
     <span data-ttu-id="e217e-124">数据库管理员立即恢复 `A` 和 `C` 。</span><span class="sxs-lookup"><span data-stu-id="e217e-124">The database administrator recovers `A` and `C` immediately.</span></span>  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='A', FILEGROUP='C' WITH RECOVERY  
    ```  
  
     <span data-ttu-id="e217e-125">此时，主文件组和文件组 `A` 以及 `C` 处于联机状态。</span><span class="sxs-lookup"><span data-stu-id="e217e-125">At this point the primary and filegroups `A` and `C` are online.</span></span> <span data-ttu-id="e217e-126">文件组 `B` 中的文件仍保持恢复挂起状态，而该文件组处于脱机状态。</span><span class="sxs-lookup"><span data-stu-id="e217e-126">Files in filegroup `B` remain recovery pending, with the filegroup offline.</span></span>  
  
4.  <span data-ttu-id="e217e-127">对文件组 `B`进行联机还原。</span><span class="sxs-lookup"><span data-stu-id="e217e-127">Online restore of filegroup `B`.</span></span>  
  
     <span data-ttu-id="e217e-128">在随后的任意时间还原文件组 `B` 中的文件。</span><span class="sxs-lookup"><span data-stu-id="e217e-128">Files in filegroup `B` are restored any time thereafter.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e217e-129">文件组 `B` 的备份是在该文件组成为只读以后进行的；因此，不需要前滚这些文件。</span><span class="sxs-lookup"><span data-stu-id="e217e-129">The backup of filegroup `B` was taken after the filegroup became read-only; therefore, these files do not have to be rolled forward.</span></span>  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='B' FROM backup WITH RECOVERY  
    ```  
  
     <span data-ttu-id="e217e-130">所有文件组现在都处于联机状态。</span><span class="sxs-lookup"><span data-stu-id="e217e-130">All filegroups are now online.</span></span>  
  
## <a name="additional-examples"></a><span data-ttu-id="e217e-131">其他示例</span><span class="sxs-lookup"><span data-stu-id="e217e-131">Additional Examples</span></span>  
  
-   [<span data-ttu-id="e217e-132">示例：数据库的段落还原（简单恢复模式）</span><span class="sxs-lookup"><span data-stu-id="e217e-132">Example: Piecemeal Restore of Database &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [<span data-ttu-id="e217e-133">示例：仅对某些文件组进行段落还原（简单恢复模式）</span><span class="sxs-lookup"><span data-stu-id="e217e-133">Example: Piecemeal Restore of Only Some Filegroups &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [<span data-ttu-id="e217e-134">示例：只读文件的联机还原（简单恢复模式）</span><span class="sxs-lookup"><span data-stu-id="e217e-134">Example: Online Restore of a Read-Only File &#40;Simple Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [<span data-ttu-id="e217e-135">示例：数据库的段落还原（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="e217e-135">Example: Piecemeal Restore of Database &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [<span data-ttu-id="e217e-136">示例：读/写文件的联机还原（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="e217e-136">Example: Online Restore of a Read-Write File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
-   [<span data-ttu-id="e217e-137">示例：只读文件的联机还原（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="e217e-137">Example: Online Restore of a Read-Only File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="e217e-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e217e-138">See Also</span></span>  
 <span data-ttu-id="e217e-139">[BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e217e-139">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="e217e-140">[联机还原 (SQL Server)](online-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e217e-140">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span></span>  
 <span data-ttu-id="e217e-141">[应用事务日志备份 (SQL Server)](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e217e-141">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 <span data-ttu-id="e217e-142">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e217e-142">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="e217e-143">段落还原 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e217e-143">Piecemeal Restores &#40;SQL Server&#41;</span></span>](piecemeal-restores-sql-server.md)  
  
  
