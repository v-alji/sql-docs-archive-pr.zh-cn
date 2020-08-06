---
title: 示例：仅对某些文件组进行段落还原（简单恢复模式）| Microsoft Docs
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
ms.assetid: d7ad026c-5355-4308-9560-0dc843940d4f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8254ac96a269b6fb433759e5a649bf9df1b7feac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693996"
---
# <a name="example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model"></a><span data-ttu-id="459ea-102">示例：仅对某些文件组进行段落还原（简单恢复模式）</span><span class="sxs-lookup"><span data-stu-id="459ea-102">Example: Piecemeal Restore of Only Some Filegroups (Simple Recovery Model)</span></span>
  <span data-ttu-id="459ea-103">本主题针对采用简单恢复模式并包含只读文件组的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="459ea-103">This topic is relevant for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases under the simple recovery model that contain a read-only filegroup.</span></span>  
  
 <span data-ttu-id="459ea-104">段落还原顺序在文件组级别分阶段还原和恢复数据库，并从主文件组和所有读写辅助文件组开始还原和恢复。</span><span class="sxs-lookup"><span data-stu-id="459ea-104">A piecemeal restore sequence restores and recovers a database in stages at the filegroup level, beginning with the primary and all read/write, secondary filegroups.</span></span>  
  
 <span data-ttu-id="459ea-105">在此示例中，使用简单恢复模式的名为 `adb`的数据库包含三个文件组。</span><span class="sxs-lookup"><span data-stu-id="459ea-105">In this example, a database named `adb`, which uses the simple recovery model, contains three filegroups.</span></span> <span data-ttu-id="459ea-106">文件组 `A` 为读/写文件组，文件组 `B` 和文件组 `C` 为只读文件组。</span><span class="sxs-lookup"><span data-stu-id="459ea-106">Filegroup `A` is read/write, and filegroup `B` and filegroup `C` are read-only.</span></span> <span data-ttu-id="459ea-107">最初，所有文件组都处于联机状态。</span><span class="sxs-lookup"><span data-stu-id="459ea-107">Initially, all of the filegroups are online.</span></span>  
  
 <span data-ttu-id="459ea-108">数据库 `B` 的主文件组和文件组 `adb` 显示为已损坏；因此数据库管理员决定使用段落还原顺序还原这些文件组。</span><span class="sxs-lookup"><span data-stu-id="459ea-108">The primary and filegroup `B` of database `adb` appear to be damaged; therefore, the database administrator decides to restore them by using a piecemeal restore sequence.</span></span> <span data-ttu-id="459ea-109">在简单恢复模式下，所有读/写文件组都必须从同一个部分备份还原。</span><span class="sxs-lookup"><span data-stu-id="459ea-109">Under the simple recovery model, all read/write filegroups must be restored from the same partial backup.</span></span> <span data-ttu-id="459ea-110">尽管文件组 `A` 未损坏，但它也必须随主文件组一起还原，以确保它们保持一致（数据库将还原到在上一次部分备份结束时定义的时点）。</span><span class="sxs-lookup"><span data-stu-id="459ea-110">Although filegroup `A` is intact, it must be restored with the primary filegroup to make sure that they are consistent (the database will be restored to the point in time defined by the end of the last partial backup).</span></span> <span data-ttu-id="459ea-111">文件组 `C` 未损坏，但必须对其进行恢复才能使其联机。</span><span class="sxs-lookup"><span data-stu-id="459ea-111">Filegroup `C` is intact, but it must be recovered to bring it online.</span></span> <span data-ttu-id="459ea-112">尽管文件组 `B`已损坏，但它包含的关键数据比文件组 `C`包含的关键数据要少；因此将最后还原 `B` 。</span><span class="sxs-lookup"><span data-stu-id="459ea-112">Filegroup `B`, although damaged, contains less critical data than Filegroup `C`; therefore, `B` will be restored last.</span></span>  
  
## <a name="restore-sequences"></a><span data-ttu-id="459ea-113">还原顺序</span><span class="sxs-lookup"><span data-stu-id="459ea-113">Restore Sequences</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="459ea-114">联机还原顺序的语法与脱机还原顺序的语法完全相同。</span><span class="sxs-lookup"><span data-stu-id="459ea-114">The syntax for an online restore sequence is the same as for an offline restore sequence.</span></span>  
  
1.  <span data-ttu-id="459ea-115">从部分备份中部分还原主文件组和文件组 `A` 。</span><span class="sxs-lookup"><span data-stu-id="459ea-115">Partial restore of the primary and filegroup `A` from a partial backup.</span></span>  
  
    ```  
    RESTORE DATABASE adb READ_WRITE_FILEGROUPS FROM partial_backup   
    WITH PARTIAL, RECOVERY  
    ```  
  
     <span data-ttu-id="459ea-116">此时，主文件组和文件组 `A` 处于联机状态。</span><span class="sxs-lookup"><span data-stu-id="459ea-116">At this point the primary filegroup and filegroup `A` are online.</span></span> <span data-ttu-id="459ea-117">文件组 `B` 和 `C` 中的文件处于恢复挂起状态，而文件组处于脱机状态。</span><span class="sxs-lookup"><span data-stu-id="459ea-117">Files in filegroups `B` and `C` are recovery pending, and the filegroups are offline.</span></span>  
  
2.  <span data-ttu-id="459ea-118">文件组 `C`的联机还原。</span><span class="sxs-lookup"><span data-stu-id="459ea-118">Online recovery of filegroup `C`.</span></span>  
  
     <span data-ttu-id="459ea-119">文件组 `C` 处于一致状态，这是因为，尽管数据库已通过还原及时恢复，但上面还原的部分备份是在文件组 `C` 成为只读文件组后进行的。</span><span class="sxs-lookup"><span data-stu-id="459ea-119">Filegroup `C` is consistent because the partial backup that was restored above was taken after filegroup `C` became read-only, although the database was taken back in time by the restore.</span></span> <span data-ttu-id="459ea-120">数据库管理员将恢复文件组 `C`（但不会还原该文件组）以使其联机。</span><span class="sxs-lookup"><span data-stu-id="459ea-120">The database administrator recovers the filegroup `C`, without restoring it, to bring it online.</span></span>  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='C' WITH RECOVERY  
    ```  
  
     <span data-ttu-id="459ea-121">此时，主文件组和文件组 `A` 以及 `C` 处于联机状态。</span><span class="sxs-lookup"><span data-stu-id="459ea-121">At this point the primary and filegroups `A` and `C` are online.</span></span> <span data-ttu-id="459ea-122">文件组 B 中的文件将保持恢复挂起状态，而该文件组处于脱机状态。</span><span class="sxs-lookup"><span data-stu-id="459ea-122">Files in filegroupB remain recovery pending, with the filegroup offline.</span></span>  
  
3.  <span data-ttu-id="459ea-123">文件组 的联机还原。 `B.`</span><span class="sxs-lookup"><span data-stu-id="459ea-123">Online restore of filegroup `B.`</span></span>  
  
     <span data-ttu-id="459ea-124">必须还原文件组 `B` 中的文件。</span><span class="sxs-lookup"><span data-stu-id="459ea-124">Files in filegroup `B` must be restored.</span></span> <span data-ttu-id="459ea-125">数据库管理员在文件组 `B` 变为只读文件组之后，且在进行部分备份之前还原文件组 `B` 的备份。</span><span class="sxs-lookup"><span data-stu-id="459ea-125">The database administrator restores the backup of filegroup `B` taken after filegroup `B` became read-only and before the partial backup.</span></span>  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='B' FROM backup   
    WITH RECOVERY  
    ```  
  
     <span data-ttu-id="459ea-126">所有文件组现在都处于联机状态。</span><span class="sxs-lookup"><span data-stu-id="459ea-126">All filegroups are now online.</span></span>  
  
## <a name="additional-examples"></a><span data-ttu-id="459ea-127">其他示例</span><span class="sxs-lookup"><span data-stu-id="459ea-127">Additional Examples</span></span>  
  
-   [<span data-ttu-id="459ea-128">示例：数据库的段落还原（简单恢复模式）</span><span class="sxs-lookup"><span data-stu-id="459ea-128">Example: Piecemeal Restore of Database &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [<span data-ttu-id="459ea-129">示例：只读文件的联机还原（简单恢复模式）</span><span class="sxs-lookup"><span data-stu-id="459ea-129">Example: Online Restore of a Read-Only File &#40;Simple Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [<span data-ttu-id="459ea-130">示例：数据库的段落还原（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="459ea-130">Example: Piecemeal Restore of Database &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [<span data-ttu-id="459ea-131">示例：仅对某些文件组进行段落还原（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="459ea-131">Example: Piecemeal Restore of Only Some Filegroups &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [<span data-ttu-id="459ea-132">示例：读/写文件的联机还原（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="459ea-132">Example: Online Restore of a Read-Write File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
-   [<span data-ttu-id="459ea-133">示例：只读文件的联机还原（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="459ea-133">Example: Online Restore of a Read-Only File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="459ea-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="459ea-134">See Also</span></span>  
 <span data-ttu-id="459ea-135">[联机还原 (SQL Server)](online-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="459ea-135">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span></span>  
 <span data-ttu-id="459ea-136">[BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="459ea-136">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="459ea-137">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="459ea-137">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="459ea-138">段落还原 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="459ea-138">Piecemeal Restores &#40;SQL Server&#41;</span></span>](piecemeal-restores-sql-server.md)  
  
  
