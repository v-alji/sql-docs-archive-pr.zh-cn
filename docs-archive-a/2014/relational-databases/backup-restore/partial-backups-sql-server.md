---
title: 部分备份 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full backups [SQL Server]
- partial backups [SQL Server]
- READ_WRITE_FILEGROUPS option
- database backups [SQL Server], about backing up databases
ms.assetid: fe6b6bb1-38d0-46c4-bab8-31df14e8999c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0c03cf2fb4d3af6fe87459e881e26c48cfacc232
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589177"
---
# <a name="partial-backups-sql-server"></a><span data-ttu-id="97f11-102">部分备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="97f11-102">Partial Backups (SQL Server)</span></span>
  <span data-ttu-id="97f11-103">所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 恢复模式都支持部分备份，因此，本主题与所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库相关。</span><span class="sxs-lookup"><span data-stu-id="97f11-103">All [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] recovery models support partial backups, so this topic is relevant for all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span> <span data-ttu-id="97f11-104">但是，部分备份用于简单恢复模式中，旨在提高对非常大的数据库（包含一个或多个只读文件组）进行备份的灵活性。</span><span class="sxs-lookup"><span data-stu-id="97f11-104">However, partial backups are designed for use under the simple recovery model to improve flexibility for backing up very large databases that contain one or more read-only filegroups.</span></span>  
  
 <span data-ttu-id="97f11-105">部分备份在希望不包括只读文件组时非常有用。</span><span class="sxs-lookup"><span data-stu-id="97f11-105">Partial backups are useful whenever you want to exclude read-only filegroups.</span></span> <span data-ttu-id="97f11-106">“部分备份”  与完整数据库备份类似，但部分备份不包含所有文件组。</span><span class="sxs-lookup"><span data-stu-id="97f11-106">A *partial backup* resembles a full database backup, but a partial backup does not contain all the filegroups.</span></span> <span data-ttu-id="97f11-107">而对于读写数据库，部分备份包含主文件组、每个读写文件组以及（可选）一个或多个只读文件中的数据。</span><span class="sxs-lookup"><span data-stu-id="97f11-107">Instead, for a read-write database, a partial backup contains the data in the primary filegroup, every read-write filegroup, and, optionally, one or more read-only files.</span></span> <span data-ttu-id="97f11-108">只读数据库的部分备份仅包含主文件组。</span><span class="sxs-lookup"><span data-stu-id="97f11-108">A partial backup of a read-only database contains only the primary filegroup.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="97f11-109">如果部分备份后将只读数据库更改为读/写，则可能出现部分备份中所没有的读/写辅助文件组。</span><span class="sxs-lookup"><span data-stu-id="97f11-109">If a read-only database is changed to read/write after a partial backup, there might be read/write secondary filegroups that are not in the partial backup.</span></span> <span data-ttu-id="97f11-110">在这种情况下，如果尝试执行部分差异备份，则备份将失败。</span><span class="sxs-lookup"><span data-stu-id="97f11-110">In this case, if you try to take a differential partial backup, the backup fails.</span></span> <span data-ttu-id="97f11-111">在执行数据库的部分差异备份之前，必须先执行其他部分备份。</span><span class="sxs-lookup"><span data-stu-id="97f11-111">Before you can take a differential partial backup of the database, you must take another partial backup.</span></span> <span data-ttu-id="97f11-112">新的部分备份包含每个读/写辅助文件组，并可用作部分差异备份的基准。</span><span class="sxs-lookup"><span data-stu-id="97f11-112">The new partial backup contains every read/write secondary filegroup and can serve as the base for differential partial backups.</span></span>  
  
 <span data-ttu-id="97f11-113">只读文件组的文件备份可以与部分备份一起使用。</span><span class="sxs-lookup"><span data-stu-id="97f11-113">File backups of read-only filegroups can be combined with partial backups.</span></span> <span data-ttu-id="97f11-114">有关文件备份的信息，请参阅[完整文件备份 (SQL Server)](full-file-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="97f11-114">For information about file backups, see [Full File Backups &#40;SQL Server&#41;](full-file-backups-sql-server.md).</span></span>  
  
 <span data-ttu-id="97f11-115">部分备份可用作部分差异备份的“差异基准”  。</span><span class="sxs-lookup"><span data-stu-id="97f11-115">A partial backup can serve as the *differential base* for differential partial backups.</span></span> <span data-ttu-id="97f11-116">有关详细信息，请参阅 [差异备份 (SQL Server)](differential-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="97f11-116">For more information, see [Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="97f11-117">相关任务</span><span class="sxs-lookup"><span data-stu-id="97f11-117">Related Tasks</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="97f11-118">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或维护计划向导不支持部分备份。</span><span class="sxs-lookup"><span data-stu-id="97f11-118">Partial backups are not supported by [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or the Maintenance Plan Wizard.</span></span>  
  
 <span data-ttu-id="97f11-119">**创建部分备份**</span><span class="sxs-lookup"><span data-stu-id="97f11-119">**To create a partial backup**</span></span>  
  
-   <span data-ttu-id="97f11-120">[BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql)（READ_WRITE_FILEGROUPS；FILEGROUP 选项，如果需要）</span><span class="sxs-lookup"><span data-stu-id="97f11-120">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) (READ_WRITE_FILEGROUPS; FILEGROUP option, if needed)</span></span>  
  
 <span data-ttu-id="97f11-121">**在还原序列中使用部分备份**</span><span class="sxs-lookup"><span data-stu-id="97f11-121">**To use a partial backup in a restore sequence**</span></span>  
  
-   [<span data-ttu-id="97f11-122">示例：数据库的段落还原（简单恢复模式）</span><span class="sxs-lookup"><span data-stu-id="97f11-122">Example: Piecemeal Restore of Database &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [<span data-ttu-id="97f11-123">示例：仅对某些文件组进行段落还原（简单恢复模式）</span><span class="sxs-lookup"><span data-stu-id="97f11-123">Example: Piecemeal Restore of Only Some Filegroups &#40;Simple Recovery Model&#41;</span></span>](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="97f11-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="97f11-124">See Also</span></span>  
 <span data-ttu-id="97f11-125">[备份概述 (SQL Server)](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="97f11-125">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 <span data-ttu-id="97f11-126">[文件还原（简单恢复模式）](file-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="97f11-126">[File Restores &#40;Simple Recovery Model&#41;](file-restores-simple-recovery-model.md) </span></span>  
 [<span data-ttu-id="97f11-127">段落还原 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="97f11-127">Piecemeal Restores &#40;SQL Server&#41;</span></span>](piecemeal-restores-sql-server.md)  
  
  
