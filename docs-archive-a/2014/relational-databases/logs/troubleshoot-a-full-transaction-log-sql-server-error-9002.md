---
title: 解决事务日志已满的问题（SQL Server 错误 9002）| Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], full
- troubleshooting [SQL Server], full transaction log
- 9002 (Database Engine error)
- transaction logs [SQL Server], truncation
- backing up transaction logs [SQL Server], full logs
- transaction logs [SQL Server], full log
- full transaction logs [SQL Server]
ms.assetid: 0f23aa84-475d-40df-bed3-c923f8c1b520
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d03e259bd0aff8fce02558dbe08efb56748493c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577629"
---
# <a name="troubleshoot-a-full-transaction-log-sql-server-error-9002"></a><span data-ttu-id="de2a5-102">解决事务日志已满的问题（SQL Server 错误 9002）</span><span class="sxs-lookup"><span data-stu-id="de2a5-102">Troubleshoot a Full Transaction Log (SQL Server Error 9002)</span></span>
  <span data-ttu-id="de2a5-103">本主题讨论对已满事务日志可以采取的几种应对措施，并就以后如何避免出现已满事务日志给出建议。</span><span class="sxs-lookup"><span data-stu-id="de2a5-103">This topic discusses possible responses to a full transaction log and suggests how to avoid it in the future.</span></span> <span data-ttu-id="de2a5-104">如果事务日志已满，则 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 会发出 9002 错误。</span><span class="sxs-lookup"><span data-stu-id="de2a5-104">When the transaction log becomes full, [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] issues a 9002 error.</span></span> <span data-ttu-id="de2a5-105">当数据库联机或恢复时，日志可能会满。</span><span class="sxs-lookup"><span data-stu-id="de2a5-105">The log can fill when the database is online or in recovery.</span></span> <span data-ttu-id="de2a5-106">如果日志在数据库处于联机状态时已满，则该数据库仍会保持联机状态，但只能读取，不能更新。</span><span class="sxs-lookup"><span data-stu-id="de2a5-106">If the log fills while the database is online, the database remains online but can only be read, not updated.</span></span> <span data-ttu-id="de2a5-107">如果恢复过程中日志已满，则 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 将数据库标记为 RESOURCE PENDING。</span><span class="sxs-lookup"><span data-stu-id="de2a5-107">If the log fills during recovery, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] marks the database as RESOURCE PENDING.</span></span> <span data-ttu-id="de2a5-108">不管哪种情况，都需要用户执行操作才能使日志空间可用。</span><span class="sxs-lookup"><span data-stu-id="de2a5-108">In either case, user action is required to make log space available.</span></span>  
  
## <a name="responding-to-a-full-transaction-log"></a><span data-ttu-id="de2a5-109">应对已满事务日志</span><span class="sxs-lookup"><span data-stu-id="de2a5-109">Responding to a Full Transaction Log</span></span>  
 <span data-ttu-id="de2a5-110">正确响应已满事务日志在某种程度上取决于导致日志已满的情况。</span><span class="sxs-lookup"><span data-stu-id="de2a5-110">The appropriate response to a full transaction log depends partly on what condition or conditions caused the log to fill.</span></span> <span data-ttu-id="de2a5-111">若要在给定情况下查找阻止日志截断的原因，请使用 **sys.database** 目录视图的 **log_reuse_wait** 列和 **log_reuse_wait_desc** 列。</span><span class="sxs-lookup"><span data-stu-id="de2a5-111">To discover what is preventing log truncation in a given case, use the **log_reuse_wait** and **log_reuse_wait_desc** columns of the **sys.database** catalog view.</span></span> <span data-ttu-id="de2a5-112">有关详细信息，请参阅 [sys.databases (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="de2a5-112">For more information, see [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql).</span></span> <span data-ttu-id="de2a5-113">有关延迟日志截断的因素的说明，请参阅[事务日志 (SQL Server)](the-transaction-log-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="de2a5-113">For descriptions of factors that can delay log truncation, see [The Transaction Log &#40;SQL Server&#41;](the-transaction-log-sql-server.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="de2a5-114">如果数据库在恢复过程中出现 9002 错误，则在解决此问题后，可使用 ALTER DATABASE *database_name* SET ONLINE 恢复数据库。</span><span class="sxs-lookup"><span data-stu-id="de2a5-114">If the database was in recovery when the 9002 error occurred, after resolving the problem, recover the database by using ALTER DATABASE *database_name* SET ONLINE.</span></span>  
  
 <span data-ttu-id="de2a5-115">响应已满事务日志的备选方法包括：</span><span class="sxs-lookup"><span data-stu-id="de2a5-115">Alternatives for responding to a full transaction log include:</span></span>  
  
-   <span data-ttu-id="de2a5-116">备份日志。</span><span class="sxs-lookup"><span data-stu-id="de2a5-116">Backing up the log.</span></span>  
  
-   <span data-ttu-id="de2a5-117">释放磁盘空间以便日志可以自动增长。</span><span class="sxs-lookup"><span data-stu-id="de2a5-117">Freeing disk space so that the log can automatically grow.</span></span>  
  
-   <span data-ttu-id="de2a5-118">将日志文件移到具有足够空间的磁盘驱动器。</span><span class="sxs-lookup"><span data-stu-id="de2a5-118">Moving the log file to a disk drive with sufficient space.</span></span>  
  
-   <span data-ttu-id="de2a5-119">增加日志文件的大小。</span><span class="sxs-lookup"><span data-stu-id="de2a5-119">Increasing the size of a log file.</span></span>  
  
-   <span data-ttu-id="de2a5-120">在其他磁盘上添加日志文件。</span><span class="sxs-lookup"><span data-stu-id="de2a5-120">Adding a log file on a different disk.</span></span>  
  
-   <span data-ttu-id="de2a5-121">完成或取消长时间运行的事务。</span><span class="sxs-lookup"><span data-stu-id="de2a5-121">Completing or killing a long-running transaction.</span></span>  
  
 <span data-ttu-id="de2a5-122">下列部分介绍了这些备选方法。</span><span class="sxs-lookup"><span data-stu-id="de2a5-122">These alternatives are discussed in the following sections.</span></span> <span data-ttu-id="de2a5-123">请选择最适用于您情况的响应。</span><span class="sxs-lookup"><span data-stu-id="de2a5-123">Choose a response that fits your situation best.</span></span>  
  
### <a name="backing-up-the-log"></a><span data-ttu-id="de2a5-124">备份日志</span><span class="sxs-lookup"><span data-stu-id="de2a5-124">Backing up the Log</span></span>  
 <span data-ttu-id="de2a5-125">在完整恢复模式或大容量日志恢复模式下，如果最近尚未备份事务日志，则请立即进行备份以免发生日志截断。</span><span class="sxs-lookup"><span data-stu-id="de2a5-125">Under the full recovery model or bulk-logged recovery model, if the transaction log has not been backed up recently, backup might be what is preventing log truncation.</span></span> <span data-ttu-id="de2a5-126">如果从未备份日志，则必须创建两个日志备份，以允许[!INCLUDE[ssDE](../../includes/ssde-md.md)]将日志截断到上次的备份点。</span><span class="sxs-lookup"><span data-stu-id="de2a5-126">If the log has never been backed up, you must create two log backups to permit the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to truncate the log to the point of the last backup.</span></span> <span data-ttu-id="de2a5-127">截断日志可释放空间以供新的日志记录使用。</span><span class="sxs-lookup"><span data-stu-id="de2a5-127">Truncating the log frees space for new log records.</span></span> <span data-ttu-id="de2a5-128">若要防止日志再次填满，请经常执行日志备份。</span><span class="sxs-lookup"><span data-stu-id="de2a5-128">To keep the log from filling up again, take log backups frequently.</span></span>  
  
 <span data-ttu-id="de2a5-129">**创建事务日志备份**</span><span class="sxs-lookup"><span data-stu-id="de2a5-129">**To create a transaction log backup**</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="de2a5-130">如果数据库已损坏，请参阅[结尾日志备份 (SQL Server)](../backup-restore/tail-log-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="de2a5-130">If the database is damaged, see [Tail-Log Backups &#40;SQL Server&#41;](../backup-restore/tail-log-backups-sql-server.md).</span></span>  
  
-   [<span data-ttu-id="de2a5-131">备份事务日志 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="de2a5-131">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](../backup-restore/back-up-a-transaction-log-sql-server.md)  
  
-   <span data-ttu-id="de2a5-132"><xref:Microsoft.SqlServer.Management.Smo.Backup.SqlBackup%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="de2a5-132"><xref:Microsoft.SqlServer.Management.Smo.Backup.SqlBackup%2A> (SMO)</span></span>  
  
### <a name="freeing-disk-space"></a><span data-ttu-id="de2a5-133">释放磁盘空间</span><span class="sxs-lookup"><span data-stu-id="de2a5-133">Freeing Disk Space</span></span>  
 <span data-ttu-id="de2a5-134">您可以通过删除或移动其他文件的方法来释放包含数据库事务日志文件的磁盘驱动器上的磁盘空间。</span><span class="sxs-lookup"><span data-stu-id="de2a5-134">You might be able to free disk space on the disk drive that contains the transaction log file for the database by deleting or moving other files.</span></span> <span data-ttu-id="de2a5-135">释放磁盘空间后，恢复系统将自动扩大日志文件。</span><span class="sxs-lookup"><span data-stu-id="de2a5-135">The freed disk space allows the recovery system to enlarge the log file automatically.</span></span>  
  
### <a name="moving-the-log-file-to-a-different-disk"></a><span data-ttu-id="de2a5-136">将日志文件移至其他磁盘</span><span class="sxs-lookup"><span data-stu-id="de2a5-136">Moving the Log File to a Different Disk</span></span>  
 <span data-ttu-id="de2a5-137">如果在当前包含日志文件的驱动器上无法释放足够的磁盘空间，请考虑将该文件移至空间充足的其他驱动器上。</span><span class="sxs-lookup"><span data-stu-id="de2a5-137">If you cannot free enough disk space on the drive that currently contains the log file, consider moving the file to another drive with sufficient space.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="de2a5-138">日志文件决不要放在压缩文件系统中。</span><span class="sxs-lookup"><span data-stu-id="de2a5-138">Log files should never be placed on compressed file systems.</span></span>  
  
 <span data-ttu-id="de2a5-139">**移动日志文件**</span><span class="sxs-lookup"><span data-stu-id="de2a5-139">**To move a log file**</span></span>  
  
-   [<span data-ttu-id="de2a5-140">移动数据库文件</span><span class="sxs-lookup"><span data-stu-id="de2a5-140">Move Database Files</span></span>](../databases/move-database-files.md)  
  
### <a name="increasing-the-size-of-a-log-file"></a><span data-ttu-id="de2a5-141">增加日志文件的大小</span><span class="sxs-lookup"><span data-stu-id="de2a5-141">Increasing the Size of a Log File</span></span>  
 <span data-ttu-id="de2a5-142">如果日志磁盘上具有可用空间，则可以增加日志文件的大小。</span><span class="sxs-lookup"><span data-stu-id="de2a5-142">If space is available on the log disk, you can increase the size of the log file.</span></span> <span data-ttu-id="de2a5-143">日志文件的最大大小是每个日志文件 2 TB。</span><span class="sxs-lookup"><span data-stu-id="de2a5-143">The maximum size for log files is two terabytes (TB) per log file.</span></span>  
  
 <span data-ttu-id="de2a5-144">**增加文件大小**</span><span class="sxs-lookup"><span data-stu-id="de2a5-144">**To increase the file size**</span></span>  
  
 <span data-ttu-id="de2a5-145">如果禁用自动增长，数据库处于联机状态，并且磁盘上有足够的可用空间，则可采用以下方法之一：</span><span class="sxs-lookup"><span data-stu-id="de2a5-145">If autogrow is disabled, the database is online, and sufficient space is available on the disk, either:</span></span>  
  
-   <span data-ttu-id="de2a5-146">手动增加文件大小以生成单个增量。</span><span class="sxs-lookup"><span data-stu-id="de2a5-146">Manually increase the file size to produce a single growth increment.</span></span>  
  
-   <span data-ttu-id="de2a5-147">使用 ALTER DATABASE 语句启用自动增长以针对 FILEGROWTH 选项设置非零增量。</span><span class="sxs-lookup"><span data-stu-id="de2a5-147">Turn on autogrow by using the ALTER DATABASE statement to set a non-zero growth increment for the FILEGROWTH option.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="de2a5-148">不管哪种情况，如果已达到当前大小限制，则应增加 MAXSIZE 值。</span><span class="sxs-lookup"><span data-stu-id="de2a5-148">In either case, if the current size limit has been reached, increase the MAXSIZE value.</span></span>  
  
### <a name="adding-a-log-file-on-a-different-disk"></a><span data-ttu-id="de2a5-149">在其他磁盘上添加日志文件</span><span class="sxs-lookup"><span data-stu-id="de2a5-149">Adding a Log File on a Different Disk</span></span>  
 <span data-ttu-id="de2a5-150">使用 ALTER DATABASE <database_name> ADD LOG FILE，向具有足够空间的其他磁盘上的数据库中添加新日志文件。</span><span class="sxs-lookup"><span data-stu-id="de2a5-150">Add a new log file to the database on a different disk that has sufficient space by using ALTER DATABASE <database_name> ADD LOG FILE.</span></span>  
  
 <span data-ttu-id="de2a5-151">**添加日志文件**</span><span class="sxs-lookup"><span data-stu-id="de2a5-151">**To add a log file**</span></span>  
  
-   [<span data-ttu-id="de2a5-152">向数据库中添加数据文件或日志文件</span><span class="sxs-lookup"><span data-stu-id="de2a5-152">Add Data or Log Files to a Database</span></span>](../databases/add-data-or-log-files-to-a-database.md)  
  
## <a name="see-also"></a><span data-ttu-id="de2a5-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="de2a5-153">See Also</span></span>  
 <span data-ttu-id="de2a5-154">[ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="de2a5-154">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="de2a5-155">[管理事务日志文件的大小](manage-the-size-of-the-transaction-log-file.md) </span><span class="sxs-lookup"><span data-stu-id="de2a5-155">[Manage the Size of the Transaction Log File](manage-the-size-of-the-transaction-log-file.md) </span></span>  
 <span data-ttu-id="de2a5-156">[事务日志备份 (SQL Server)](../backup-restore/transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="de2a5-156">[Transaction Log Backups &#40;SQL Server&#41;](../backup-restore/transaction-log-backups-sql-server.md) </span></span>  
 [<span data-ttu-id="de2a5-157">sp_add_log_file_recover_suspect_db (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="de2a5-157">sp_add_log_file_recover_suspect_db &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-log-file-recover-suspect-db-transact-sql)  
  
  
