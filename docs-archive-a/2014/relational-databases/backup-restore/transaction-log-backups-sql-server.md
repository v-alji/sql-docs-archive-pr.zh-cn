---
title: 事务日志备份 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backing up [SQL Server], transaction logs
- transaction log backups [SQL Server], creating
- log backups [SQL Server[
- transaction log backups [SQL Server], sequencing
ms.assetid: f4a44a35-0f44-4a42-91d5-d73ac658a3b0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 752447d6c38a2df0fcbdce72fbba12edd7a9eeb3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690667"
---
# <a name="transaction-log-backups-sql-server"></a><span data-ttu-id="e9871-102">事务日志备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e9871-102">Transaction Log Backups (SQL Server)</span></span>
  <span data-ttu-id="e9871-103">本主题仅与使用完整恢复模式或大容量日志恢复模式的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库相关。</span><span class="sxs-lookup"><span data-stu-id="e9871-103">This topic is relevant only for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases that are using the full or bulk-logged recovery models.</span></span> <span data-ttu-id="e9871-104">本主题讨论备份 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库的事务日志。</span><span class="sxs-lookup"><span data-stu-id="e9871-104">This topic discusses backing up the transaction log of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="e9871-105">在创建任何日志备份之前，您必须至少创建一个完整备份。</span><span class="sxs-lookup"><span data-stu-id="e9871-105">Minimally, you must have created at least one full backup before you can create any log backups.</span></span> <span data-ttu-id="e9871-106">然后，可以随时备份事务日志，除非已备份此日志。</span><span class="sxs-lookup"><span data-stu-id="e9871-106">After that, the transaction log can be backed up at any time unless the log is already being backed up.</span></span> <span data-ttu-id="e9871-107">建议经常执行日志备份，这样既可尽量减少丢失工作的风险，也可以截断事务日志。</span><span class="sxs-lookup"><span data-stu-id="e9871-107">We recommend that you take log backups frequently, both to minimize work loss exposure and to truncate the transaction log.</span></span> <span data-ttu-id="e9871-108">通常，数据库管理员偶尔（如每周）会创建完整数据库备份，还可以选择以较短间隔（如每天）创建一系列差异备份。</span><span class="sxs-lookup"><span data-stu-id="e9871-108">Typically, a database administrator creates a full database backup occasionally, such as weekly, and, optionally, creates a series of differential database backup at a shorter interval, such as daily.</span></span> <span data-ttu-id="e9871-109">与数据库备份无关，数据库管理员可以比较频繁地（例如每隔 10 分钟）创建事务日志备份。</span><span class="sxs-lookup"><span data-stu-id="e9871-109">Independently of the database backups, the database administrator backs up the transaction log at frequent intervals, such as every 10 minutes.</span></span> <span data-ttu-id="e9871-110">对于给定的备份类型，最恰当的备份间隔取决于一系列因素，如数据的重要性、数据库的大小和服务器的工作负荷。</span><span class="sxs-lookup"><span data-stu-id="e9871-110">For a given type of backup, the optimal interval depends on factors such as the importance of the data, the size of the database, and the workload of the server.</span></span>  
  
 <span data-ttu-id="e9871-111">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="e9871-111">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="e9871-112">一系列日志备份的工作原理</span><span class="sxs-lookup"><span data-stu-id="e9871-112">How a Sequence of Log Backups Works</span></span>](#LogBackupSequence)  
  
-   [<span data-ttu-id="e9871-113">建议</span><span class="sxs-lookup"><span data-stu-id="e9871-113">Recommendations</span></span>](#Recommendations)  
  
-   [<span data-ttu-id="e9871-114">相关任务</span><span class="sxs-lookup"><span data-stu-id="e9871-114">Related Tasks</span></span>](#RelatedTasks)  
  
-   [<span data-ttu-id="e9871-115">相关内容</span><span class="sxs-lookup"><span data-stu-id="e9871-115">Related Content</span></span>](#RelatedContent)  
  
##  <a name="how-a-sequence-of-log-backups-works"></a><a name="LogBackupSequence"></a><span data-ttu-id="e9871-116">一系列日志备份的工作原理</span><span class="sxs-lookup"><span data-stu-id="e9871-116">How a Sequence of Log Backups Works</span></span>  
 <span data-ttu-id="e9871-117">事务日志备份“日志链”  的序列与数据备份无关。</span><span class="sxs-lookup"><span data-stu-id="e9871-117">The sequence of transaction log backups *log chain* is independent of data backups.</span></span> <span data-ttu-id="e9871-118">例如，假设有下列事件顺序。</span><span class="sxs-lookup"><span data-stu-id="e9871-118">For example, assume the following sequence of events.</span></span>  
  
|<span data-ttu-id="e9871-119">时间</span><span class="sxs-lookup"><span data-stu-id="e9871-119">Time</span></span>|<span data-ttu-id="e9871-120">事件</span><span class="sxs-lookup"><span data-stu-id="e9871-120">Event</span></span>|  
|----------|-----------|  
|<span data-ttu-id="e9871-121">上午 8:00</span><span class="sxs-lookup"><span data-stu-id="e9871-121">8:00 A.M.</span></span>|<span data-ttu-id="e9871-122">备份数据库。</span><span class="sxs-lookup"><span data-stu-id="e9871-122">Back up database.</span></span>|  
|<span data-ttu-id="e9871-123">中午</span><span class="sxs-lookup"><span data-stu-id="e9871-123">Noon</span></span>|<span data-ttu-id="e9871-124">备份事务日志。</span><span class="sxs-lookup"><span data-stu-id="e9871-124">Back up transaction log.</span></span>|  
|<span data-ttu-id="e9871-125">下午 4:00</span><span class="sxs-lookup"><span data-stu-id="e9871-125">4:00 P.M.</span></span>|<span data-ttu-id="e9871-126">备份事务日志。</span><span class="sxs-lookup"><span data-stu-id="e9871-126">Back up transaction log.</span></span>|  
|<span data-ttu-id="e9871-127">下午 6:00</span><span class="sxs-lookup"><span data-stu-id="e9871-127">6:00 P.M.</span></span>|<span data-ttu-id="e9871-128">备份数据库。</span><span class="sxs-lookup"><span data-stu-id="e9871-128">Back up database.</span></span>|  
|<span data-ttu-id="e9871-129">晚上 8:00</span><span class="sxs-lookup"><span data-stu-id="e9871-129">8:00 P.M.</span></span>|<span data-ttu-id="e9871-130">备份事务日志。</span><span class="sxs-lookup"><span data-stu-id="e9871-130">Back up transaction log.</span></span>|  
  
 <span data-ttu-id="e9871-131">在下午 8:00 创建的事务日志备份</span><span class="sxs-lookup"><span data-stu-id="e9871-131">The transaction log backup created at 8:00 P.M.</span></span> <span data-ttu-id="e9871-132">包含从下午 4:00 到下午 8:00 的事务日志记录，</span><span class="sxs-lookup"><span data-stu-id="e9871-132">contains transaction log records from 4:00 P.M.</span></span> <span data-ttu-id="e9871-133">跨越创建完整数据库备份的时间点（下午 6:00）。</span><span class="sxs-lookup"><span data-stu-id="e9871-133">through 8:00 P.M., spanning the time when the full database backup was created at 6:00 P.M.</span></span> <span data-ttu-id="e9871-134">事务日志备份序列是连续的，从创建初始完整数据库备份的时间（上午 8:00）</span><span class="sxs-lookup"><span data-stu-id="e9871-134">The sequence of transaction log backups is continuous from the initial full database backup created at 8:00 A.M.</span></span> <span data-ttu-id="e9871-135">到创建最后事务日志备份的时间（下午 8:00）。</span><span class="sxs-lookup"><span data-stu-id="e9871-135">to the last transaction log backup created at 8:00 P.M.</span></span> <span data-ttu-id="e9871-136">有关如何应用这些日志备份的信息，请参阅 [应用事务日志备份 (SQL Server)](transaction-log-backups-sql-server.md).中的示例。</span><span class="sxs-lookup"><span data-stu-id="e9871-136">For information about how to apply these log backups, see the example in [Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md).</span></span>  
  
##  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="e9871-137">建议</span><span class="sxs-lookup"><span data-stu-id="e9871-137">Recommendations</span></span>  
  
-   <span data-ttu-id="e9871-138">如果事务日志损坏，则最新有效备份以后执行的工作将丢失。</span><span class="sxs-lookup"><span data-stu-id="e9871-138">If a transaction log is damaged, work that is performed since the most recent valid backup is lost.</span></span> <span data-ttu-id="e9871-139">因此，我们强烈建议您将日志文件存储在容错的存储设备中。</span><span class="sxs-lookup"><span data-stu-id="e9871-139">Therefore we strongly recommend that you put your log files on fault-tolerant storage.</span></span>  
  
-   <span data-ttu-id="e9871-140">如果数据库已损坏，或者你要还原数据库，建议你创建一个 [结尾日志备份](tail-log-backups-sql-server.md) ，使你可以将数据库还原到当前时间点。</span><span class="sxs-lookup"><span data-stu-id="e9871-140">If a database is damaged or you are about to restore the database, we recommend that you create a [tail-log backup](tail-log-backups-sql-server.md) to enable you to restore the database to the current point in time.</span></span>  
  
-   <span data-ttu-id="e9871-141">默认情况下，每个成功的备份操作都会在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志和系统事件日志中添加一个条目。</span><span class="sxs-lookup"><span data-stu-id="e9871-141">By default, every successful backup operation adds an entry in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log and in the system event log.</span></span> <span data-ttu-id="e9871-142">如果非常频繁地备份日志，这些成功消息会迅速累积，从而产生一个巨大的错误日志，这样会使查找其他消息变得非常困难。</span><span class="sxs-lookup"><span data-stu-id="e9871-142">If back up the log very frequently, these success messages accumulate quickly, resulting in huge error logs that can make finding other messages difficult.</span></span> <span data-ttu-id="e9871-143">在这些情况下，如果任何脚本均不依赖于这些日志条目，则可以使用跟踪标志 3226 取消这些条目。</span><span class="sxs-lookup"><span data-stu-id="e9871-143">In such cases you can suppress these log entries by using trace flag 3226 if none of your scripts depend on those entries.</span></span> <span data-ttu-id="e9871-144">有关详细信息，请参阅[跟踪标志 (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="e9871-144">For more information, see [Trace Flags &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="e9871-145">相关任务</span><span class="sxs-lookup"><span data-stu-id="e9871-145">Related Tasks</span></span>  
 <span data-ttu-id="e9871-146">**创建事务日志备份**</span><span class="sxs-lookup"><span data-stu-id="e9871-146">**To create a transaction log backup**</span></span>  
  
-   [<span data-ttu-id="e9871-147">备份事务日志 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e9871-147">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](back-up-a-transaction-log-sql-server.md)  
  
-   <span data-ttu-id="e9871-148"><xref:Microsoft.SqlServer.Management.Smo.Backup.SqlBackup%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="e9871-148"><xref:Microsoft.SqlServer.Management.Smo.Backup.SqlBackup%2A> (SMO)</span></span>  
  
 <span data-ttu-id="e9871-149">若要计划备份作业，请参阅 [Use the Maintenance Plan Wizard](../maintenance-plans/use-the-maintenance-plan-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="e9871-149">To schedule backup jobs, see [Use the Maintenance Plan Wizard](../maintenance-plans/use-the-maintenance-plan-wizard.md).</span></span>  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="e9871-150">相关内容</span><span class="sxs-lookup"><span data-stu-id="e9871-150">Related Content</span></span>  
 <span data-ttu-id="e9871-151">无。</span><span class="sxs-lookup"><span data-stu-id="e9871-151">None.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9871-152">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e9871-152">See Also</span></span>  
 <span data-ttu-id="e9871-153">[事务日志 (SQL Server)](../logs/the-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e9871-153">[The Transaction Log &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md) </span></span>  
 <span data-ttu-id="e9871-154">[SQL Server 数据库的备份和还原](back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="e9871-154">[Back Up and Restore of SQL Server Databases](back-up-and-restore-of-sql-server-databases.md) </span></span>  
 <span data-ttu-id="e9871-155">[结尾日志备份 (SQL Server)](tail-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e9871-155">[Tail-Log Backups &#40;SQL Server&#41;](tail-log-backups-sql-server.md) </span></span>  
 [<span data-ttu-id="e9871-156">应用事务日志备份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e9871-156">Apply Transaction Log Backups &#40;SQL Server&#41;</span></span>](transaction-log-backups-sql-server.md)  
  
  
