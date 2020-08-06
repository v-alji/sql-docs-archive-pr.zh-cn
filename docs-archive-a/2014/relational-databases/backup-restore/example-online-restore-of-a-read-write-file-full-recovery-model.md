---
title: 示例：读/写文件的联机还原（完整恢复模式）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full recovery model [SQL Server], RESTORE example
- online restores [SQL Server], full recovery model
- restore sequences [SQL Server], online
ms.assetid: 0dbeda81-1464-44ba-9011-914900096368
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5b99a3d97644c2a5f104173457f30fc5b3fd7188
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578265"
---
# <a name="example-online-restore-of-a-read-write-file-full-recovery-model"></a><span data-ttu-id="5433f-102">示例：读/写文件的联机还原（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="5433f-102">Example: Online Restore of a Read-Write File (Full Recovery Model)</span></span>
  <span data-ttu-id="5433f-103">本主题与完整恢复模式下包含多个文件或文件组的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库相关。</span><span class="sxs-lookup"><span data-stu-id="5433f-103">This topic is relevant for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases under the full recovery model that contain multiple files or filegroups.</span></span>  
  
 <span data-ttu-id="5433f-104">在此示例中，名为 `adb`的数据库（使用完整恢复模式）包含三个文件组。</span><span class="sxs-lookup"><span data-stu-id="5433f-104">In this example, a database named `adb`, which uses the full recovery model, contains three filegroups.</span></span> <span data-ttu-id="5433f-105">文件组 `A` 为读/写文件组，文件组 `B` 和文件组 `C` 为只读文件组。</span><span class="sxs-lookup"><span data-stu-id="5433f-105">Filegroup `A` is read/write, and filegroup `B` and filegroup `C` are read-only.</span></span> <span data-ttu-id="5433f-106">最初，所有文件组都处于联机状态。</span><span class="sxs-lookup"><span data-stu-id="5433f-106">Initially, all of the filegroups are online.</span></span>  
  
 <span data-ttu-id="5433f-107">文件组 `a1` 中的文件 `A` 似乎已损坏，数据库管理员决定在数据库处于联机状态时还原该文件。</span><span class="sxs-lookup"><span data-stu-id="5433f-107">File `a1` in filegroup `A` appears to be damaged, and the database administrator decides to restore it while the database remains online.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5433f-108">在简单恢复模式下，不允许联机还原读/写数据。</span><span class="sxs-lookup"><span data-stu-id="5433f-108">Under the simple recovery model, online restore of read/write data is not allowed.</span></span>  
  
## <a name="restore-sequences"></a><span data-ttu-id="5433f-109">还原顺序</span><span class="sxs-lookup"><span data-stu-id="5433f-109">Restore Sequences</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5433f-110">联机还原顺序的语法与脱机还原顺序的语法完全相同。</span><span class="sxs-lookup"><span data-stu-id="5433f-110">The syntax for an online restore sequence is the same as for an offline restore sequence.</span></span>  
  
1.  <span data-ttu-id="5433f-111">联机还原文件 `a1`。</span><span class="sxs-lookup"><span data-stu-id="5433f-111">Online restore of file `a1`.</span></span>  
  
    ```  
    RESTORE DATABASE adb FILE='a1' FROM backup   
    WITH NORECOVERY;  
    ```  
  
     <span data-ttu-id="5433f-112">此时，文件 a1 处于 RESTORING 状态，文件组 A 处于脱机状态。</span><span class="sxs-lookup"><span data-stu-id="5433f-112">At this point, file a1 is in the RESTORING state, and filegroup A is offline.</span></span>  
  
2.  <span data-ttu-id="5433f-113">完成文件还原之后，数据库管理员进行新的日志备份以确保捕获到该文件脱机时的点。</span><span class="sxs-lookup"><span data-stu-id="5433f-113">After restoring the file, the database administrator takes a new log backup to make sure that the point at which the file went offline is captured.</span></span>  
  
    ```  
    BACKUP LOG adb TO log_backup3;   
    ```  
  
3.  <span data-ttu-id="5433f-114">联机还原日志备份。</span><span class="sxs-lookup"><span data-stu-id="5433f-114">Online restore of log backups.</span></span>  
  
     <span data-ttu-id="5433f-115">管理员还原自从还原了文件备份后一直到获得最新日志备份（在步骤 2 中创建的*log_backup3*）所进行的所有日志备份。</span><span class="sxs-lookup"><span data-stu-id="5433f-115">The administrator restores all the log backups taken since the restored file backup, ending with the latest log backup (*log_backup3*, taken in step 2).</span></span> <span data-ttu-id="5433f-116">还原最后一个备份之后，应当恢复数据库。</span><span class="sxs-lookup"><span data-stu-id="5433f-116">After the last backup is restored, the database is recovered.</span></span>  
  
    ```  
    RESTORE LOG adb FROM log_backup1 WITH NORECOVERY;  
    RESTORE LOG adb FROM log_backup2 WITH NORECOVERY;  
    RESTORE LOG adb FROM log_backup3 WITH NORECOVERY;  
    RESTORE LOG adb WITH RECOVERY;  
    ```  
  
     <span data-ttu-id="5433f-117">文件 `a1` 现处于联机状态。</span><span class="sxs-lookup"><span data-stu-id="5433f-117">File `a1` is now online.</span></span>  
  
## <a name="additional-examples"></a><span data-ttu-id="5433f-118">其他示例</span><span class="sxs-lookup"><span data-stu-id="5433f-118">Additional Examples</span></span>  
  
-   [<span data-ttu-id="5433f-119">示例：数据库的段落还原（简单恢复模式）</span><span class="sxs-lookup"><span data-stu-id="5433f-119">Example: Piecemeal Restore of Database &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [<span data-ttu-id="5433f-120">示例：仅对某些文件组进行段落还原（简单恢复模式）</span><span class="sxs-lookup"><span data-stu-id="5433f-120">Example: Piecemeal Restore of Only Some Filegroups &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [<span data-ttu-id="5433f-121">示例：只读文件的联机还原（简单恢复模式）</span><span class="sxs-lookup"><span data-stu-id="5433f-121">Example: Online Restore of a Read-Only File &#40;Simple Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [<span data-ttu-id="5433f-122">示例：数据库的段落还原（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="5433f-122">Example: Piecemeal Restore of Database &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [<span data-ttu-id="5433f-123">示例：仅对某些文件组进行段落还原（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="5433f-123">Example: Piecemeal Restore of Only Some Filegroups &#40;Full Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [<span data-ttu-id="5433f-124">示例：只读文件的联机还原（完整恢复模式）</span><span class="sxs-lookup"><span data-stu-id="5433f-124">Example: Online Restore of a Read-Only File &#40;Full Recovery Model&#41;</span></span>](example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="5433f-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5433f-125">See Also</span></span>  
 <span data-ttu-id="5433f-126">[联机还原 (SQL Server)](online-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="5433f-126">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span></span>  
 <span data-ttu-id="5433f-127">[段落还原 (SQL Server)](piecemeal-restores-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="5433f-127">[Piecemeal Restores &#40;SQL Server&#41;](piecemeal-restores-sql-server.md) </span></span>  
 <span data-ttu-id="5433f-128">[BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5433f-128">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="5433f-129">[还原和恢复概述 (SQL Server)](restore-and-recovery-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="5433f-129">[Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span></span>  
 <span data-ttu-id="5433f-130">[应用事务日志备份 (SQL Server)](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="5433f-130">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 [<span data-ttu-id="5433f-131">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5433f-131">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
