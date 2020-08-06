---
title: 示例：数据库的段落还原（简单恢复模式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- piecemeal restores [SQL Server], simple recovery model
- restore sequences [SQL Server], piecemeal
- simple recovery model [SQL Server], RESTORE examples
ms.assetid: 9834b14a-4e56-4654-b190-c2a38624b6b4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 69de84fa2ff3a853eb9926549ad4859d2f1ae38e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691260"
---
# <a name="example-piecemeal-restore-of-database-simple-recovery-model"></a><span data-ttu-id="9339b-102">示例：数据库的段落还原（简单恢复模式）</span><span class="sxs-lookup"><span data-stu-id="9339b-102">Example: Piecemeal Restore of Database (Simple Recovery Model)</span></span>
  <span data-ttu-id="9339b-103">段落还原顺序将从主文件组和所有读写辅助文件组开始，按文件组级别分阶段还原和恢复数据库。</span><span class="sxs-lookup"><span data-stu-id="9339b-103">A piecemeal restore sequence restores and recovers a database in stages at the filegroup level, starting with the primary and all read/write, secondary filegroups.</span></span>  
  
 <span data-ttu-id="9339b-104">在此示例中，灾难发生后，数据库 `adb` 被还原到新计算机。</span><span class="sxs-lookup"><span data-stu-id="9339b-104">In this example, database `adb` is restored to a new computer after a disaster.</span></span> <span data-ttu-id="9339b-105">数据库使用的是简单恢复模式。</span><span class="sxs-lookup"><span data-stu-id="9339b-105">The database is using the simple recovery model.</span></span> <span data-ttu-id="9339b-106">灾难发生之前，所有文件组均处于联机状态。</span><span class="sxs-lookup"><span data-stu-id="9339b-106">Before the disaster, all the filegroups are online.</span></span> <span data-ttu-id="9339b-107">文件组 `A` 和 `C` 是可读/写的，文件组 `B` 是只读的。</span><span class="sxs-lookup"><span data-stu-id="9339b-107">Filegroups `A` and `C` are read/write, and filegroup `B` is read-only.</span></span> <span data-ttu-id="9339b-108">文件组 `B` 在最新部分备份之前变为只读的，该文件组包含主文件组和读/写辅助文件组 `A` 和 `C`。</span><span class="sxs-lookup"><span data-stu-id="9339b-108">Filegroup `B` became read-only before the most recent partial backup, which contains the primary filegroup and the read/write secondary filegroups, `A` and `C`.</span></span> <span data-ttu-id="9339b-109">文件组 `B` 变为只读后，对文件组 `B` 进行了单独的文件备份。</span><span class="sxs-lookup"><span data-stu-id="9339b-109">After filegroup `B` became read-only, a separate file backup of filegroup `B` was taken.</span></span>  
  
## <a name="restore-sequences"></a><span data-ttu-id="9339b-110">还原顺序</span><span class="sxs-lookup"><span data-stu-id="9339b-110">Restore Sequences</span></span>  
  
1.  <span data-ttu-id="9339b-111">主文件组以及文件组 `A` 和 `C`的部分还原。</span><span class="sxs-lookup"><span data-stu-id="9339b-111">Partial restore of the primary and filegroups `A` and `C`.</span></span>  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='A',FILEGROUP='C'   
       FROM partial_backup   
       WITH PARTIAL, RECOVERY;  
  
    ```  
  
     <span data-ttu-id="9339b-112">此时，主文件组以及文件组 `A` 和 `C` 处于联机状态。</span><span class="sxs-lookup"><span data-stu-id="9339b-112">At this point, the primary and filegroups `A` and `C` are online.</span></span> <span data-ttu-id="9339b-113">文件组 `B` 中的所有文件都处于恢复挂起状态，该文件组处于脱机状态。</span><span class="sxs-lookup"><span data-stu-id="9339b-113">All files in filegroup `B` are recovery pending, and the filegroup is offline.</span></span>  
  
2.  <span data-ttu-id="9339b-114">对文件组 `B`进行联机还原。</span><span class="sxs-lookup"><span data-stu-id="9339b-114">Online restore of filegroup `B`.</span></span>  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='B' FROM backup WITH RECOVERY;  
  
    ```  
  
     <span data-ttu-id="9339b-115">所有文件组现在都处于联机状态。</span><span class="sxs-lookup"><span data-stu-id="9339b-115">All filegroups are now online.</span></span>  
  
## <a name="additional-examples"></a><span data-ttu-id="9339b-116">其他示例</span><span class="sxs-lookup"><span data-stu-id="9339b-116">Additional Examples</span></span>  
  
-   [<span data-ttu-id="9339b-117">示例：仅对某些文件组进行段落还原（简单恢复模式）</span><span class="sxs-lookup"><span data-stu-id="9339b-117">Example: Piecemeal Restore of Only Some Filegroups &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [<span data-ttu-id="9339b-118">示例：只读文件的联机还原（简单恢复模式）</span><span class="sxs-lookup"><span data-stu-id="9339b-118">Example: Online Restore of a Read-Only File &#40;Simple Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [<span data-ttu-id="9339b-119">示例：数据库的段落还原（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="9339b-119">Example: Piecemeal Restore of Database &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [<span data-ttu-id="9339b-120">示例：仅对某些文件组进行段落还原（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="9339b-120">Example: Piecemeal Restore of Only Some Filegroups &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [<span data-ttu-id="9339b-121">示例：读/写文件的联机还原（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="9339b-121">Example: Online Restore of a Read-Write File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
-   [<span data-ttu-id="9339b-122">示例：只读文件的联机还原（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="9339b-122">Example: Online Restore of a Read-Only File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="9339b-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9339b-123">See Also</span></span>  
 <span data-ttu-id="9339b-124">[联机还原 (SQL Server)](online-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9339b-124">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span></span>  
 <span data-ttu-id="9339b-125">[BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9339b-125">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="9339b-126">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9339b-126">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="9339b-127">段落还原 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9339b-127">Piecemeal Restores &#40;SQL Server&#41;</span></span>](piecemeal-restores-sql-server.md)  
  
  
