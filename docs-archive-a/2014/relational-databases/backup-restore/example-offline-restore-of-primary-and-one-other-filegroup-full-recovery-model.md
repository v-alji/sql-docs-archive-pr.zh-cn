---
title: 示例：主文件组和一个其他文件组的脱机还原 (完整恢复模式) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full recovery model [SQL Server], RESTORE example
- offline restores [SQL Server]
- restore sequences [SQL Server], offline
ms.assetid: 7d6c50eb-dc84-4d66-855a-0b5f1bd89737
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6f845927fdd74fba476139fccbf9a5fa112d434e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590219"
---
# <a name="example-offline-restore-of-primary-and-one-other-filegroup-full-recovery-model"></a><span data-ttu-id="a35af-102">示例：主文件组和一个其他文件组的脱机还原（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="a35af-102">Example: Offline Restore of Primary and One Other Filegroup (Full Recovery Model)</span></span>
  <span data-ttu-id="a35af-103">本主题仅与完整恢复模式下包含多个文件组的数据库有关。</span><span class="sxs-lookup"><span data-stu-id="a35af-103">This topic is relevant only for databases under the full recovery model that contain multiple filegroups.</span></span>  
  
 <span data-ttu-id="a35af-104">在此示例中，名为 `adb` 的数据库包含三个文件组。</span><span class="sxs-lookup"><span data-stu-id="a35af-104">In this example, a database named `adb` contains three filegroups.</span></span> <span data-ttu-id="a35af-105">文件组 `A` 和 `C` 是可读/写的，文件组 `B` 是只读的。</span><span class="sxs-lookup"><span data-stu-id="a35af-105">Filegroups `A` and `C` are read/write, and filegroup `B` is read-only.</span></span> <span data-ttu-id="a35af-106">主文件组和文件组 `B` 受损，但文件组 `A` 和 `C` 完好无损。</span><span class="sxs-lookup"><span data-stu-id="a35af-106">The primary filegroup and filegroup `B` are damaged, but filegroups `A` and `C` are intact.</span></span> <span data-ttu-id="a35af-107">发生灾难性事件前所有文件组都处于联机状态。</span><span class="sxs-lookup"><span data-stu-id="a35af-107">Before the disaster, all the filegroups were online.</span></span>  
  
 <span data-ttu-id="a35af-108">数据库管理员决定还原和恢复主文件组及文件组 `B`。</span><span class="sxs-lookup"><span data-stu-id="a35af-108">The database administrator decides to restore and recover the primary filegroup and filegroup `B`.</span></span> <span data-ttu-id="a35af-109">该数据库使用完整恢复模式，因此，开始进行还原之前必须先获取数据库的结尾日志备份。</span><span class="sxs-lookup"><span data-stu-id="a35af-109">The database is using the full recovery model; therefore, before the restore starts, a tail-log backup must be taken of the database.</span></span> <span data-ttu-id="a35af-110">数据库变为联机后，文件组 `A` 和 `C` 将自动变为联机状态。</span><span class="sxs-lookup"><span data-stu-id="a35af-110">When the database comes on line, Filegroups `A` and `C` are automatically brought online.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a35af-111">只读文件的脱机还原顺序的步骤比联机还原要少。</span><span class="sxs-lookup"><span data-stu-id="a35af-111">The offline restore sequence has fewer steps than an online restore of a read-only file.</span></span> <span data-ttu-id="a35af-112">有关示例，请参阅[示例：只读文件的联机还原（完整恢复模式）](example-online-restore-of-a-read-only-file-full-recovery-model.md)。</span><span class="sxs-lookup"><span data-stu-id="a35af-112">For an example, see [Example: Online Restore of a Read-Only File &#40;Full Recovery Model&#41;](example-online-restore-of-a-read-only-file-full-recovery-model.md).</span></span> <span data-ttu-id="a35af-113">但是，整个数据库在执行还原顺序期间处于脱机状态。</span><span class="sxs-lookup"><span data-stu-id="a35af-113">However, the whole database is offline for the duration of the sequence.</span></span>  
  
## <a name="tail-log-backup"></a><span data-ttu-id="a35af-114">结尾日志备份</span><span class="sxs-lookup"><span data-stu-id="a35af-114">Tail-Log Backup</span></span>  
 <span data-ttu-id="a35af-115">在还原数据库之前，数据库管理员必须备份日志尾部。</span><span class="sxs-lookup"><span data-stu-id="a35af-115">Before restoring the database, the database administrator must back up the tail of the log.</span></span> <span data-ttu-id="a35af-116">由于数据库已损坏，因此创建结尾日志备份需要使用 NO_TRUNCATE 选项：</span><span class="sxs-lookup"><span data-stu-id="a35af-116">Because the database is damaged, creating the tail-log backup requires using the NO_TRUNCATE option:</span></span>  
  
```  
BACKUP LOG adb TO tailLogBackup   
   WITH NORECOVERY, NO_TRUNCATE  
```  
  
 <span data-ttu-id="a35af-117">结尾日志备份是在以下还原顺序中应用的最后一个备份。</span><span class="sxs-lookup"><span data-stu-id="a35af-117">The tail-log backup is the last backup that is applied in the following restore sequences.</span></span>  
  
## <a name="restore-sequence"></a><span data-ttu-id="a35af-118">还原顺序</span><span class="sxs-lookup"><span data-stu-id="a35af-118">Restore Sequence</span></span>  
 <span data-ttu-id="a35af-119">若要还原主文件组和文件组 `B`，数据库管理员可使用不带 PARTIAL 选项的还原顺序，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a35af-119">To restore the primary filegroup and filegroup `B`, the database administrator uses a restore sequence without the PARTIAL option, as follows:</span></span>  
  
```  
RESTORE DATABASE adb FILEGROUP='Primary' FROM backup1   
WITH NORECOVERY  
RESTORE DATABASE adb FILEGROUP='B' FROM backup2   
WITH NORECOVERY  
RESTORE LOG adb FROM backup3 WITH NORECOVERY  
RESTORE LOG adb FROM backup4 WITH NORECOVERY  
RESTORE LOG adb FROM backup5 WITH NORECOVERY  
RESTORE LOG adb FROM tailLogBackup WITH RECOVERY  
```  
  
 <span data-ttu-id="a35af-120">未还原的文件将自动变为联机状态。</span><span class="sxs-lookup"><span data-stu-id="a35af-120">The files that are not restored are automatically brought online.</span></span> <span data-ttu-id="a35af-121">此时，所有文件组都处于联机状态。</span><span class="sxs-lookup"><span data-stu-id="a35af-121">All the filegroups are now online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a35af-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a35af-122">See Also</span></span>  
 <span data-ttu-id="a35af-123">[联机还原 (SQL Server)](online-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a35af-123">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span></span>  
 <span data-ttu-id="a35af-124">[段落还原 (SQL Server)](piecemeal-restores-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a35af-124">[Piecemeal Restores &#40;SQL Server&#41;](piecemeal-restores-sql-server.md) </span></span>  
 <span data-ttu-id="a35af-125">[文件还原（完整恢复模式）](file-restores-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="a35af-125">[File Restores &#40;Full Recovery Model&#41;](file-restores-full-recovery-model.md) </span></span>  
 <span data-ttu-id="a35af-126">[应用事务日志备份 (SQL Server)](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a35af-126">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 [<span data-ttu-id="a35af-127">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a35af-127">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
