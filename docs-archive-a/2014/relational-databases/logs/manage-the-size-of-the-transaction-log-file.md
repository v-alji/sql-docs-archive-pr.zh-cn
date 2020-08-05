---
title: 管理事务日志文件的大小 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- transaction logs [SQL Server], size management
ms.assetid: 3a70e606-303f-47a8-96d4-2456a18d4297
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 219ba0605d60bab0b13675f7f9f7ff01cace5755
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580729"
---
# <a name="manage-the-size-of-the-transaction-log-file"></a><span data-ttu-id="fcf1b-102">管理事务日志文件的大小</span><span class="sxs-lookup"><span data-stu-id="fcf1b-102">Manage the Size of the Transaction Log File</span></span>
  <span data-ttu-id="fcf1b-103">在某些情况下，物理收缩或扩展 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库的事务日志的物理日志文件非常有用。</span><span class="sxs-lookup"><span data-stu-id="fcf1b-103">In some cases, it can be useful to physically shrink or expand the physical log file of the transaction log of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="fcf1b-104">本主题包含与下列各项有关的信息：如何监视 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 事务日志大小、收缩事务日志、添加或扩大事务日志文件、优化 **tempdb** 事务日志增长率以及控制事务日志文件的增长。</span><span class="sxs-lookup"><span data-stu-id="fcf1b-104">This topic contains information about how to monitor the size of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] transaction log, shrink the transaction log, add or enlarge a transaction log file, optimize the **tempdb** transaction log growth rate, and control the growth of a transaction log file.</span></span>  
  
  
##  <a name="monitor-log-space-use"></a><a name="MonitorSpaceUse"></a><span data-ttu-id="fcf1b-105">监视日志空间使用情况</span><span class="sxs-lookup"><span data-stu-id="fcf1b-105">Monitor Log Space Use</span></span>  
 <span data-ttu-id="fcf1b-106">可以使用 DBCC SQLPERF (LOGSPACE) 监视日志空间使用情况。</span><span class="sxs-lookup"><span data-stu-id="fcf1b-106">You can monitor log space use by using DBCC SQLPERF (LOGSPACE).</span></span> <span data-ttu-id="fcf1b-107">此命令返回有关当前使用的日志空间量的信息，并指示何时需要截断事务日志。</span><span class="sxs-lookup"><span data-stu-id="fcf1b-107">This command returns information about the amount of log space currently used and indicates when the transaction log is in need of truncation.</span></span> <span data-ttu-id="fcf1b-108">有关详细信息，请参阅 [DBCC SQLPERF (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-sqlperf-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="fcf1b-108">For more information, see [DBCC SQLPERF &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-sqlperf-transact-sql).</span></span> <span data-ttu-id="fcf1b-109">若要了解有关日志文件的当前大小、最大大小以及此文件的自动增长选项的信息，还可以在 **sys.database_files** 中针对此日志文件使用 **size**、**max_size** 和 **growth** 等列。</span><span class="sxs-lookup"><span data-stu-id="fcf1b-109">For information about the current size of a log file, its maximum size, and the autogrow option for the file, you can also use the **size**, **max_size**, and **growth** columns for that log file in **sys.database_files**.</span></span> <span data-ttu-id="fcf1b-110">有关详细信息，请参阅 [sys.database_files (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="fcf1b-110">For more information, see [sys.database_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="fcf1b-111">建议避免日志磁盘重载。</span><span class="sxs-lookup"><span data-stu-id="fcf1b-111">We recommend that you avoid overloading the log disk.</span></span>  
  
  
##  <a name="shrink-the-size-of-the-log-file"></a><a name="ShrinkSize"></a><span data-ttu-id="fcf1b-112">缩小日志文件的大小</span><span class="sxs-lookup"><span data-stu-id="fcf1b-112">Shrink the Size of the Log File</span></span>  
 <span data-ttu-id="fcf1b-113">若要减少物理日志文件的物理大小，则必须收缩日志文件。</span><span class="sxs-lookup"><span data-stu-id="fcf1b-113">To reduce the physical size of a physical log file, you must shrink the log file.</span></span> <span data-ttu-id="fcf1b-114">如果您知道事务日志文件包含将不需要的未使用空间，则此方法很有用。</span><span class="sxs-lookup"><span data-stu-id="fcf1b-114">This is useful if you know that a transaction log file contains unused space that you will not be needing.</span></span> <span data-ttu-id="fcf1b-115">仅当数据库处于联机状态，而且至少一个虚拟日志文件可用时，才会发生收缩日志文件。</span><span class="sxs-lookup"><span data-stu-id="fcf1b-115">Shrinking a log file can occur only while the database is online and, also, at least one virtual log file is free.</span></span> <span data-ttu-id="fcf1b-116">在某些情况下，直到下一个日志截断后，才能收缩日志。</span><span class="sxs-lookup"><span data-stu-id="fcf1b-116">In some cases, shrinking the log may not be possible until after the next log truncation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fcf1b-117">能够延长虚拟日志文件活动时间的因素（如长时间运行的事务）可以限制甚至阻止日志收缩。</span><span class="sxs-lookup"><span data-stu-id="fcf1b-117">Factors, such as a long-running transaction, that keep virtual log files active for an extended period can restrict log shrinkage or even prevent the log from shrinking at all.</span></span> <span data-ttu-id="fcf1b-118">有关延迟日志截断的因素的信息，请参阅[事务日志 (SQL Server)](the-transaction-log-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="fcf1b-118">For information about factors that can delay log truncation, see [The Transaction Log &#40;SQL Server&#41;](the-transaction-log-sql-server.md).</span></span>  
  
 <span data-ttu-id="fcf1b-119">收缩日志文件可删除一个或多个不包含逻辑日志任何部分的虚拟日志文件（即“不活动的虚拟日志文件” \*\*）。</span><span class="sxs-lookup"><span data-stu-id="fcf1b-119">Shrinking a log file removes one or more virtual log files that do not hold any part of the logical log (that is, *inactive virtual log files*).</span></span> <span data-ttu-id="fcf1b-120">在收缩事务日志文件时，将从日志文件的末端删除足够的不活动虚拟日志文件，以便将日志减小到接近目标大小。</span><span class="sxs-lookup"><span data-stu-id="fcf1b-120">When a transaction log file is shrunk, enough inactive virtual log files are removed from the end of the log file to reduce the log to approximately the target size.</span></span>  
  
 <span data-ttu-id="fcf1b-121">**收缩日志文件（而不收缩数据库文件）**</span><span class="sxs-lookup"><span data-stu-id="fcf1b-121">**To shrink a log file (without shrinking database files)**</span></span>  
  
-   [<span data-ttu-id="fcf1b-122">DBCC SHRINKFILE (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="fcf1b-122">DBCC SHRINKFILE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-shrinkfile-transact-sql)  
  
-   [<span data-ttu-id="fcf1b-123">收缩文件</span><span class="sxs-lookup"><span data-stu-id="fcf1b-123">Shrink a File</span></span>](../databases/shrink-a-file.md)  
  
 <span data-ttu-id="fcf1b-124">**监视日志文件收缩事件**</span><span class="sxs-lookup"><span data-stu-id="fcf1b-124">**To monitor log-file shrink events**</span></span>  
  
-   <span data-ttu-id="fcf1b-125">[Log File Auto Shrink Event Class](../event-classes/log-file-auto-shrink-event-class.md)。</span><span class="sxs-lookup"><span data-stu-id="fcf1b-125">[Log File Auto Shrink Event Class](../event-classes/log-file-auto-shrink-event-class.md).</span></span>  
  
 `To monitor log space`  
  
-   [<span data-ttu-id="fcf1b-126">DBCC SQLPERF (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="fcf1b-126">DBCC SQLPERF &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-sqlperf-transact-sql)  
  
-   <span data-ttu-id="fcf1b-127">[sys.database_files (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql)（请参阅日志文件或文件的 **size**、**max_size** 和 **growth** 列。）</span><span class="sxs-lookup"><span data-stu-id="fcf1b-127">[sys.database_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) (See the **size**, **max_size**, and **growth** columns for the log file or files.)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fcf1b-128">收缩数据库和日志文件可以设置为自动发生。</span><span class="sxs-lookup"><span data-stu-id="fcf1b-128">Shrinking database and log files can be set to occur automatically.</span></span> <span data-ttu-id="fcf1b-129">但是，我们建议不使用自动收缩，且 `autoshrink` 数据库属性默认情况下设置为 FALSE。</span><span class="sxs-lookup"><span data-stu-id="fcf1b-129">However, we recommend against automatic shrinking, and the `autoshrink` database property is set to FALSE by default.</span></span> <span data-ttu-id="fcf1b-130">如果 `autoshrink` 设置为 TRUE，则仅当其空间的 25% 以上未使用时，自动收缩才会减少文件的大小。</span><span class="sxs-lookup"><span data-stu-id="fcf1b-130">If `autoshrink` is set to TRUE, automatic shrinking reduces the size of a file only when more than 25 percent of its space is unused.</span></span> <span data-ttu-id="fcf1b-131">文件将收缩至未使用空间占文件 25% 的大小，或者收缩至文件的原始大小，以两者中较大者为准。</span><span class="sxs-lookup"><span data-stu-id="fcf1b-131">The file is shrunk either to the size at which only 25 percent of the file is unused space or to the original size of the file, whichever is larger.</span></span> <span data-ttu-id="fcf1b-132">有关更改属性设置的信息 `autoshrink` ，请参阅[查看或更改数据库的属性](../databases/view-or-change-the-properties-of-a-database.md)-使用 "**选项**" 页上的 "**自动收缩**" 属性或 "[更改数据库集选项" &#40;transact-sql&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)-使用 AUTO_SHRINK 选项。</span><span class="sxs-lookup"><span data-stu-id="fcf1b-132">For information about changing the setting of the `autoshrink` property, see [View or Change the Properties of a Database](../databases/view-or-change-the-properties-of-a-database.md)-use the **Auto Shrink** property on the **Options** page-or [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)-use the AUTO_SHRINK option.</span></span>  
  
  
##  <a name="add-or-enlarge-a-log-file"></a><a name="AddOrEnlarge"></a><span data-ttu-id="fcf1b-133">添加或扩大日志文件</span><span class="sxs-lookup"><span data-stu-id="fcf1b-133">Add or Enlarge a Log File</span></span>  
 <span data-ttu-id="fcf1b-134">可以通过扩大现有的日志文件（如果磁盘空间允许）或将日志文件添加至数据库（尤其是其他磁盘上的数据库）来获得空间。</span><span class="sxs-lookup"><span data-stu-id="fcf1b-134">Alternatively, you can gain space by enlarging the existing log file (if disk space permits) or by adding a log file to the database, typically on a different disk.</span></span>  
  
-   <span data-ttu-id="fcf1b-135">若要将日志文件添加至数据库，请使用 ALTER DATABASE 语句的 ADD LOG FILE 子句。</span><span class="sxs-lookup"><span data-stu-id="fcf1b-135">To add a log file to the database, use the ADD LOG FILE clause of the ALTER DATABASE statement.</span></span> <span data-ttu-id="fcf1b-136">添加日志文件可以使日志获得空间。</span><span class="sxs-lookup"><span data-stu-id="fcf1b-136">Adding a log file allows the log to grow.</span></span>  
  
-   <span data-ttu-id="fcf1b-137">若要扩大日志文件，请使用 ALTER DATABASE 语句的 MODIFY FILE 子句，并指定 SIZE 和 MAXSIZE 语法。</span><span class="sxs-lookup"><span data-stu-id="fcf1b-137">To enlarge the log file, use the MODIFY FILE clause of the ALTER DATABASE statement, specifying the SIZE and MAXSIZE syntax.</span></span> <span data-ttu-id="fcf1b-138">有关详细信息，请参阅 [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="fcf1b-138">For more information, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
  
##  <a name="optimize-the-size-of-the-tempdb-transaction-log"></a><a name="tempdbOptimize"></a><span data-ttu-id="fcf1b-139">优化 tempdb 事务日志的大小</span><span class="sxs-lookup"><span data-stu-id="fcf1b-139">Optimize the Size of the tempdb Transaction Log</span></span>  
 <span data-ttu-id="fcf1b-140">重新启动服务器实例可以将 **tempdb** 数据库的事务日志调整到自动增长之前的原始大小。</span><span class="sxs-lookup"><span data-stu-id="fcf1b-140">Restarting a server instance resizes the transaction log of the **tempdb** database to its original, pre-autogrow size.</span></span> <span data-ttu-id="fcf1b-141">这会降低 **tempdb** 事务日志的性能。</span><span class="sxs-lookup"><span data-stu-id="fcf1b-141">This can reduce the performance of the **tempdb** transaction log.</span></span> <span data-ttu-id="fcf1b-142">您可以通过在启动或重新启动服务器实例之后增加 **tempdb** 事务日志的大小来避免此开销。</span><span class="sxs-lookup"><span data-stu-id="fcf1b-142">You can avoid this overhead by increasing the size of the **tempdb** transaction log after starting or restarting the server instance.</span></span> <span data-ttu-id="fcf1b-143">有关详细信息，请参阅 [tempdb Database](../databases/tempdb-database.md)。</span><span class="sxs-lookup"><span data-stu-id="fcf1b-143">For more information, see [tempdb Database](../databases/tempdb-database.md).</span></span>  
  
  
##  <a name="control-the-growth-of-a-transaction-log-file"></a><a name="ControlGrowth"></a><span data-ttu-id="fcf1b-144">控制事务日志文件的增长</span><span class="sxs-lookup"><span data-stu-id="fcf1b-144">Control the Growth of a Transaction Log File</span></span>  
 <span data-ttu-id="fcf1b-145">可使用 [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql) 语句管理事务日志文件的增长。</span><span class="sxs-lookup"><span data-stu-id="fcf1b-145">You can use the [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) statement to manage the growth of a transaction log file.</span></span> <span data-ttu-id="fcf1b-146">注意以下事项：</span><span class="sxs-lookup"><span data-stu-id="fcf1b-146">Note the following:</span></span>  
  
-   <span data-ttu-id="fcf1b-147">若要更改当前文件大小（以 KB、MB、GB 和 TB 为单位），请使用 SIZE 选项。</span><span class="sxs-lookup"><span data-stu-id="fcf1b-147">To change the current file size in KB, MB, GB, and TB units, use the SIZE option.</span></span>  
  
-   <span data-ttu-id="fcf1b-148">若要更改增量，请使用 FILEGROWTH 选项。</span><span class="sxs-lookup"><span data-stu-id="fcf1b-148">To change the growth increment, use the FILEGROWTH option.</span></span> <span data-ttu-id="fcf1b-149">如果值为 0，则表明自动增长已设置为关闭，且不允许增加空间。</span><span class="sxs-lookup"><span data-stu-id="fcf1b-149">A value of 0 indicates that automatic growth is set to off and no additional space is permitted.</span></span> <span data-ttu-id="fcf1b-150">日志文件的小幅度自动增长量可能降低性能。</span><span class="sxs-lookup"><span data-stu-id="fcf1b-150">A small autogrowth increment on a log file can reduce performance.</span></span> <span data-ttu-id="fcf1b-151">因此，为了避免经常向日志文件中扩充内容，应该采用足够大的文件增量。</span><span class="sxs-lookup"><span data-stu-id="fcf1b-151">The file growth increment on a log file should be sufficiently large to avoid frequent expansion.</span></span> <span data-ttu-id="fcf1b-152">通常，采用 10% 的默认增量较为合适。</span><span class="sxs-lookup"><span data-stu-id="fcf1b-152">The default growth increment of 10 percent is generally suitable.</span></span>  
  
     <span data-ttu-id="fcf1b-153">有关更改日志文件的文件增长属性的信息，请参阅[ALTER DATABASE &#40;transact-sql&#41;](/sql/t-sql/statements/alter-database-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="fcf1b-153">For information on changing the file-growth property on a log file, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
-   <span data-ttu-id="fcf1b-154">若要控制日志文件的最大大小（以 KB、MB、GB 和 TB 为单位）或将增长设置为 UNLIMITED，请使用 MAXSIZE 选项。</span><span class="sxs-lookup"><span data-stu-id="fcf1b-154">To control the maximum the size of a log file in KB, MB, GB, and TB units or to set growth to UNLIMITED, use the MAXSIZE option.</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="fcf1b-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fcf1b-155">See Also</span></span>  
 <span data-ttu-id="fcf1b-156">[BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="fcf1b-156">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 [<span data-ttu-id="fcf1b-157">解决事务日志已满的问题（SQL Server 错误 9002）</span><span class="sxs-lookup"><span data-stu-id="fcf1b-157">Troubleshoot a Full Transaction Log &#40;SQL Server Error 9002&#41;</span></span>](troubleshoot-a-full-transaction-log-sql-server-error-9002.md)  
  
  
