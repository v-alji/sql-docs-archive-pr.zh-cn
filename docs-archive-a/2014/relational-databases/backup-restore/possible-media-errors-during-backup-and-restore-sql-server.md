---
title: 在备份和还原期间可能的介质错误 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- media errors [SQL Server]
- CONTINUE_AFTER_ERROR option
- errors [SQL Server], backups
- backups [SQL Server], errors
- RESTORE VERIFYONLY statement
- backup media [SQL Server], error management
- page checksums [SQL Server]
- backup checksums [SQL Server]
- backing up [SQL Server], media errors
- RESTORE statement, media errors
- NO_CHECKSUM option
- checksums [SQL Server]
ms.assetid: 83a27b29-1191-4f8d-9648-6e6be73a9b7c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 15691c513aad6027be1063ef566ebdf245ebcc8c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691760"
---
# <a name="possible-media-errors-during-backup-and-restore-sql-server"></a><span data-ttu-id="0483d-102">在备份和还原期间可能的介质错误 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0483d-102">Possible Media Errors During Backup and Restore (SQL Server)</span></span>
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="0483d-103">允许您在恢复数据库时不必顾及检测到的错误。</span><span class="sxs-lookup"><span data-stu-id="0483d-103">gives you the option of recovering a database despite detected errors.</span></span> <span data-ttu-id="0483d-104">一个重要的新错误检测机制是创建备份校验和（可选），可以通过备份操作创建并通过还原操作验证。</span><span class="sxs-lookup"><span data-stu-id="0483d-104">An important new error-detection mechanism is the optional creation of a backup checksum that can be created by a backup operation and validated by a restore operation.</span></span> <span data-ttu-id="0483d-105">您可以控制操作是否检查错误，以及遇到错误时是停止操作还是继续操作。</span><span class="sxs-lookup"><span data-stu-id="0483d-105">You can control whether an operation checks for errors and whether the operation stops or continues on encountering an error.</span></span> <span data-ttu-id="0483d-106">如果备份包含备份校验和，则 RESTORE 和 RESTORE VERIFYONLY 语句可以检查错误。</span><span class="sxs-lookup"><span data-stu-id="0483d-106">If a backup contains a backup checksum, RESTORE and RESTORE VERIFYONLY statements can check for errors.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0483d-107">镜像备份最多提供 4 个介质集的副本（镜像），提供备用副本以便从损坏介质导致的错误中恢复。</span><span class="sxs-lookup"><span data-stu-id="0483d-107">Mirrored backups provide up to four copies (mirrors) of a media set, providing alternative copies for recovering from errors caused by damaged media.</span></span> <span data-ttu-id="0483d-108">有关详细信息，请参阅本主题后面的 [镜像备份媒体集 (SQL Server)](mirrored-backup-media-sets-sql-server.md)不熟悉的读者。</span><span class="sxs-lookup"><span data-stu-id="0483d-108">For more information, see [Mirrored Backup Media Sets &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md).</span></span>  
  
  
  
##  <a name="backup-checksums"></a><a name="BckChecksums"></a> <span data-ttu-id="0483d-109">备份校验和</span><span class="sxs-lookup"><span data-stu-id="0483d-109">Backup Checksums</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="0483d-110">支持三种校验和：页校验和、日志块校验和以及备份校验和。</span><span class="sxs-lookup"><span data-stu-id="0483d-110">supports three types of checksums: a checksum on pages, a checksum in log blocks, and a backup checksum.</span></span> <span data-ttu-id="0483d-111">生成备份校验和时，BACKUP 将验证从数据库读取的数据是否与数据库中存在的任意校验和或页残缺指示一致。</span><span class="sxs-lookup"><span data-stu-id="0483d-111">When generating a backup checksum, BACKUP verifies that the data read from the database is consistent with any checksum or torn-page indication that is present in the database.</span></span>  
  
 <span data-ttu-id="0483d-112">BACKUP 语句选择性地计算备份流的备份校验和；如果给定页上存在页校验和或残缺页信息，则当备份该页时，BACKUP 还将验证它的校验和、残缺页状态以及 ID。</span><span class="sxs-lookup"><span data-stu-id="0483d-112">The BACKUP statement optionally computes a backup checksum on the backup stream; if page-checksum or torn-page information is present on a given page, when backing up the page, BACKUP also verifies the checksum and torn-page status and the page ID, of the page.</span></span> <span data-ttu-id="0483d-113">创建备份校验和时，备份操作不会向页中添加任何校验和。</span><span class="sxs-lookup"><span data-stu-id="0483d-113">When creating a backup checksum, a backup operation does not add any checksums to pages.</span></span> <span data-ttu-id="0483d-114">将在这些页位于数据库中时对其进行备份，备份不会修改这些页。</span><span class="sxs-lookup"><span data-stu-id="0483d-114">Pages are backed up as they exist in the database, and the pages are unmodified by backup.</span></span>  
  
 <span data-ttu-id="0483d-115">由于验证和生成备份校验和引起的开销，使用备份校验和会对性能造成潜在的影响。</span><span class="sxs-lookup"><span data-stu-id="0483d-115">Due to the overhead verifying and generating backup checksums, using backup checksums poses a potential performance impact.</span></span> <span data-ttu-id="0483d-116">工作负荷和备份吞吐量都可能受到影响。</span><span class="sxs-lookup"><span data-stu-id="0483d-116">Both the workload and the backup throughput may be affected.</span></span> <span data-ttu-id="0483d-117">因此，不是必须使用备份校验和。</span><span class="sxs-lookup"><span data-stu-id="0483d-117">Therefore, using backup checksums is optional.</span></span> <span data-ttu-id="0483d-118">如果决定在备份过程中生成校验和，请仔细监视由此引起的 CPU 开销以及对系统中任何并发工作负荷造成的影响。</span><span class="sxs-lookup"><span data-stu-id="0483d-118">When deciding to generate checksums during a backup, carefully monitor the CPU overhead incurred as well as the impact on any concurrent workload on the system.</span></span>  
  
 <span data-ttu-id="0483d-119">BACKUP 永远不会修改磁盘上的源页面和页面内容。</span><span class="sxs-lookup"><span data-stu-id="0483d-119">BACKUP never modifies the source page on disk nor the contents of a page.</span></span>  
  
 <span data-ttu-id="0483d-120">在启用备份校验和后，备份操作将执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="0483d-120">When backup checksums are enabled, a backup operation performs the following steps:</span></span>  
  
1.  <span data-ttu-id="0483d-121">向备份介质写入页之前，备份操作将验证页级信息（页校验和或页残缺检测）是否存在。</span><span class="sxs-lookup"><span data-stu-id="0483d-121">Before writing a page to the backup media, the backup operation verifies the page-level information (page checksum or torn page detection), if either exists.</span></span> <span data-ttu-id="0483d-122">如果两者都不存在，则备份无法验证页。</span><span class="sxs-lookup"><span data-stu-id="0483d-122">If neither exists, backup cannot verify the page.</span></span> <span data-ttu-id="0483d-123">将按原样包含未经验证的页，并且其内容将添加到总备份校验和中。</span><span class="sxs-lookup"><span data-stu-id="0483d-123">Unverified the pages are included as is, and their contents are added to the overall backup checksum.</span></span>  
  
     <span data-ttu-id="0483d-124">如果备份操作在验证过程中遇到页错误，备份将失败。</span><span class="sxs-lookup"><span data-stu-id="0483d-124">If the backup operation encounters a page error during verification, the backup fails.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0483d-125">有关页校验和及页残缺检测的详细信息，请参阅 ALTER DATABASE 语句的 PAGE_VERIFY 选项。</span><span class="sxs-lookup"><span data-stu-id="0483d-125">For more information about page checksums and torn page detection, see the PAGE_VERIFY option of the ALTER DATABASE statement.</span></span> <span data-ttu-id="0483d-126">有关详细信息，请参阅 [ALTER DATABASE SET 选项 (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-set-options)。</span><span class="sxs-lookup"><span data-stu-id="0483d-126">For more information, see [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span>  
  
2.  <span data-ttu-id="0483d-127">无论是否存在页校验和，BACKUP 都会为备份流生成一个单独的备份校验和。</span><span class="sxs-lookup"><span data-stu-id="0483d-127">Regardless of whether page checksums are present, BACKUP generates a separate backup checksum for the backup streams.</span></span> <span data-ttu-id="0483d-128">还原操作可使用（可选）备份校验和来验证该备份是否损坏。</span><span class="sxs-lookup"><span data-stu-id="0483d-128">Restore operations can optionally use the backup checksum to validate that the backup is not corrupted.</span></span> <span data-ttu-id="0483d-129">备份校验和存储在备份介质上，而不是存储在数据库页上。</span><span class="sxs-lookup"><span data-stu-id="0483d-129">The backup checksum is stored on the backup media, not on the database pages.</span></span> <span data-ttu-id="0483d-130">备份校验还可根据需要在还原时使用。</span><span class="sxs-lookup"><span data-stu-id="0483d-130">The backup checksum can optionally be used at restore time.</span></span>  
  
3.  <span data-ttu-id="0483d-131">备份集标记为包含备份校验和（在 **msdb..backupset** 的 **has_backup_checksums**列中）。</span><span class="sxs-lookup"><span data-stu-id="0483d-131">The backup set is flagged as containing backup checksums (in the **has_backup_checksums** column of **msdb..backupset)**.</span></span> <span data-ttu-id="0483d-132">有关详细信息，请参阅 [backupset (Transact-SQL)](/sql/relational-databases/system-tables/backupset-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="0483d-132">For more information, see [backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql).</span></span>  
  
 <span data-ttu-id="0483d-133">在还原操作过程中，如果备份介质中存在备份校验和，则默认情况下，RESTORE 和 RESTORE VERIFYONLY 语句都将验证备份校验和及页校验和。</span><span class="sxs-lookup"><span data-stu-id="0483d-133">During a restore operation, if backup checksums are present on the backup media, by default, both the RESTORE and RESTORE VERIFYONLY statements verify the backup checksums and page checksums.</span></span> <span data-ttu-id="0483d-134">如果不存在备份校验和，则这两种还原操作直接执行，而不会进行验证；这是因为没有备份校验和，还原无法可靠地验证页校验和。</span><span class="sxs-lookup"><span data-stu-id="0483d-134">If there is no backup checksum, either restore operation proceeds without any verification; this is because without a backup checksum, restore cannot reliably verify page checksums.</span></span>  
  
## <a name="response-to-page-checksum-errors-during-a-backup-or-restore-operation"></a><span data-ttu-id="0483d-135">在备份或还原操作过程中响应页校验和错误</span><span class="sxs-lookup"><span data-stu-id="0483d-135">Response to Page Checksum Errors During a Backup or Restore Operation</span></span>  
 <span data-ttu-id="0483d-136">默认情况下，在遇到页校验和错误后，BACKUP 或 RESTORE 操作将失败，而 RESTORE VERIFYONLY 操作将继续。</span><span class="sxs-lookup"><span data-stu-id="0483d-136">By default, after encountering a page checksum error, a BACKUP or RESTORE operation fails and a RESTORE VERIFYONLY operation continues.</span></span> <span data-ttu-id="0483d-137">但是，您可以控制某一给定操作在遇到错误时是失败还是尽可能继续。</span><span class="sxs-lookup"><span data-stu-id="0483d-137">However, you can control whether a given operation fails on encountering an error or continues as best it can.</span></span>  
  
 <span data-ttu-id="0483d-138">如果 BACKUP 操作在遇到错误后将继续，则该操作将执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="0483d-138">If a BACKUP operation continues after encountering errors, the operation performs the following steps:</span></span>  
  
1.  <span data-ttu-id="0483d-139">将备份介质中的备份集标记为包含错误，并跟踪 **msdb** 数据库中 **suspect_pages** 表中的页。</span><span class="sxs-lookup"><span data-stu-id="0483d-139">Flags the backup set on the backup media as containing errors and tracks the page in the **suspect_pages** table in the **msdb** database.</span></span> <span data-ttu-id="0483d-140">有关详细信息，请参阅 [suspect_pages (Transact-SQL)](/sql/relational-databases/system-tables/suspect-pages-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="0483d-140">For more information, see [suspect_pages &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/suspect-pages-transact-sql).</span></span>  
  
2.  <span data-ttu-id="0483d-141">记录 SQL Server 错误日志中的错误。</span><span class="sxs-lookup"><span data-stu-id="0483d-141">Logs the error in the SQL Server error log.</span></span>  
  
3.  <span data-ttu-id="0483d-142">将备份集标记为包含此类型的错误（在 **msdb.backupset** 的 **is_damaged**列中）。</span><span class="sxs-lookup"><span data-stu-id="0483d-142">Marks the backup set as containing this type of error (in the **is_damaged** column of **msdb.backupset)**.</span></span> <span data-ttu-id="0483d-143">有关详细信息，请参阅 [backupset (Transact-SQL)](/sql/relational-databases/system-tables/backupset-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="0483d-143">For more information, see [backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql).</span></span>  
  
4.  <span data-ttu-id="0483d-144">发出一条消息，说明已成功生成备份，但备份中包含页错误。</span><span class="sxs-lookup"><span data-stu-id="0483d-144">Issues a message that the backup was successfully generated, but contains page errors.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="0483d-145">相关任务</span><span class="sxs-lookup"><span data-stu-id="0483d-145">Related Tasks</span></span>  
 <span data-ttu-id="0483d-146">**启用或禁用备份校验和**</span><span class="sxs-lookup"><span data-stu-id="0483d-146">**To enable or disable backup checksums**</span></span>  
  
-   [<span data-ttu-id="0483d-147">在备份或还原期间启用或禁用备份校验和 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0483d-147">Enable or Disable Backup Checksums During Backup or Restore &#40;SQL Server&#41;</span></span>](enable-or-disable-backup-checksums-during-backup-or-restore-sql-server.md)  
  
 <span data-ttu-id="0483d-148">**控制备份操作期间的错误响应**</span><span class="sxs-lookup"><span data-stu-id="0483d-148">**To control the response to a error during a backup operation**</span></span>  
  
-   [<span data-ttu-id="0483d-149">指定备份或还原操作在遇到错误后是继续还是停止 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0483d-149">Specify Whether a Backup or Restore Operation Continues or Stops After Encountering an Error &#40;SQL Server&#41;</span></span>](specify-if-backup-or-restore-continues-or-stops-after-error.md)  
  
## <a name="see-also"></a><span data-ttu-id="0483d-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0483d-150">See Also</span></span>  
 <span data-ttu-id="0483d-151">[ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0483d-151">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="0483d-152">[BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0483d-152">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="0483d-153">[backupset (Transact-SQL)](/sql/relational-databases/system-tables/backupset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0483d-153">[backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span></span>  
 <span data-ttu-id="0483d-154">[镜像备份媒体集 (SQL Server)](mirrored-backup-media-sets-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0483d-154">[Mirrored Backup Media Sets &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md) </span></span>  
 <span data-ttu-id="0483d-155">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0483d-155">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="0483d-156">RESTORE VERIFYONLY (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0483d-156">RESTORE VERIFYONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql)  
  
  
