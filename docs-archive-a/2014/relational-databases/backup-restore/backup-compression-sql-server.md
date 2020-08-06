---
title: 备份压缩 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server], backup compression
- backup compression [SQL Server], about backup compression
- compression [SQL Server], backup compression
- backups [SQL Server], compression
- backing up [SQL Server], backup compression
- backup compression [SQL Server]
ms.assetid: 05bc9c4f-3947-4dd4-b823-db77519bd4d2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3291a858d8ef037e7cca92eb2e6abb19aec4da8e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578268"
---
# <a name="backup-compression-sql-server"></a><span data-ttu-id="0e6f6-102">备份压缩 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0e6f6-102">Backup Compression (SQL Server)</span></span>
  <span data-ttu-id="0e6f6-103">本主题介绍 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 备份的压缩，包括限制、压缩备份时的性能折中、备份压缩的配置以及压缩率。</span><span class="sxs-lookup"><span data-stu-id="0e6f6-103">This topic describes the compression of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backups, including restrictions, performance trade-off of compressing backups, the configuration of backup compression, and the compression ratio.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0e6f6-104">有关支持备份压缩的版本的信息 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，请参阅[SQL Server 2014 的各个版本支持的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="0e6f6-104">For information which editions of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] support backup compression, see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span> <span data-ttu-id="0e6f6-105">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 的每个版本和更高版本都可以还原已压缩的备份。</span><span class="sxs-lookup"><span data-stu-id="0e6f6-105">Every edition of [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and later can restore a compressed backup.</span></span>  
  
  
##  <a name="benefits"></a><a name="Benefits"></a> <span data-ttu-id="0e6f6-106">优势</span><span class="sxs-lookup"><span data-stu-id="0e6f6-106">Benefits</span></span>  
  
-   <span data-ttu-id="0e6f6-107">因为相同数据的压缩的备份比未压缩备份小，所以压缩备份所需的设备 I/O 通常较少，因此通常可大大提高备份速度。</span><span class="sxs-lookup"><span data-stu-id="0e6f6-107">Because a compressed backup is smaller than an uncompressed backup of the same data, compressing a backup typically requires less device I/O and therefore usually increases backup speed significantly.</span></span>  
  
     <span data-ttu-id="0e6f6-108">有关详细信息，请参阅本主题后面的 [压缩备份的性能影响](#PerfImpact)。</span><span class="sxs-lookup"><span data-stu-id="0e6f6-108">For more information, see [Performance Impact of Compressing Backups](#PerfImpact), later in this topic.</span></span>  
  
  
##  <a name="restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="0e6f6-109">限制</span><span class="sxs-lookup"><span data-stu-id="0e6f6-109">Restrictions</span></span>  
 <span data-ttu-id="0e6f6-110">压缩的备份具有以下限制条件：</span><span class="sxs-lookup"><span data-stu-id="0e6f6-110">The following restrictions apply to compressed backups:</span></span>  
  
-   <span data-ttu-id="0e6f6-111">压缩的备份和未压缩的备份不能共存于一个介质集中。</span><span class="sxs-lookup"><span data-stu-id="0e6f6-111">Compressed and uncompressed backups cannot co-exist in a media set.</span></span>  
  
-   <span data-ttu-id="0e6f6-112">早期版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 无法读取压缩的备份。</span><span class="sxs-lookup"><span data-stu-id="0e6f6-112">Previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot read compressed backups.</span></span>  
  
-   <span data-ttu-id="0e6f6-113">NTbackup 无法共享包含压缩的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 备份的磁带。</span><span class="sxs-lookup"><span data-stu-id="0e6f6-113">NTbackups cannot share a tape with compressed [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backups.</span></span>  
  
  
##  <a name="performance-impact-of-compressing-backups"></a><a name="PerfImpact"></a> <span data-ttu-id="0e6f6-114">压缩备份的性能影响</span><span class="sxs-lookup"><span data-stu-id="0e6f6-114">Performance Impact of Compressing Backups</span></span>  
 <span data-ttu-id="0e6f6-115">默认情况下，压缩会显著增加 CPU 的使用，并且压缩进程所消耗的额外 CPU 可能会对并发操作产生不利影响。</span><span class="sxs-lookup"><span data-stu-id="0e6f6-115">By default, compression significantly increases CPU usage, and the additional CPU consumed by the compression process might adversely impact concurrent operations.</span></span> <span data-ttu-id="0e6f6-116">因此，你可能需要在会话中创建低优先级的压缩备份，其 CPU 使用率受[资源调控器](../resource-governor/resource-governor.md)限制。</span><span class="sxs-lookup"><span data-stu-id="0e6f6-116">Therefore, you might want to create low-priority compressed backups in a session whose CPU usage is limited by[Resource Governor](../resource-governor/resource-governor.md).</span></span> <span data-ttu-id="0e6f6-117">有关详细信息，请参阅本主题后面的 [使用资源调控器限制备份压缩的 CPU 使用量 (Transact-SQL)](use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md)限制。</span><span class="sxs-lookup"><span data-stu-id="0e6f6-117">For more information, see [Use Resource Governor to Limit CPU Usage by Backup Compression &#40;Transact-SQL&#41;](use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md).</span></span>  
  
 <span data-ttu-id="0e6f6-118">若要很好地了解备份 I/O 的性能表现，可以通过评估以下类型的性能计数器来分别考察进入设备或来自设备的备份 I/O：</span><span class="sxs-lookup"><span data-stu-id="0e6f6-118">To obtain a good picture of your backup I/O performance, you can isolate the backup I/O to or from devices by evaluating the following sorts of performance counters:</span></span>  
  
-   <span data-ttu-id="0e6f6-119">Windows I/O 性能计数器，例如物理磁盘计数器</span><span class="sxs-lookup"><span data-stu-id="0e6f6-119">Windows I/O performance counters, such as the physical-disk counters</span></span>  
  
-   <span data-ttu-id="0e6f6-120">**SQLServer:备份设备** 对象的 [设备吞吐量（字节/秒）](../performance-monitor/sql-server-backup-device-object.md) 计数器</span><span class="sxs-lookup"><span data-stu-id="0e6f6-120">The **Device Throughput Bytes/sec** counter of the [SQLServer:Backup Device](../performance-monitor/sql-server-backup-device-object.md) object</span></span>  
  
-   <span data-ttu-id="0e6f6-121">**SQLServer:数据库** 对象的 [备份/还原吞吐量/秒](../performance-monitor/sql-server-databases-object.md) 计数器</span><span class="sxs-lookup"><span data-stu-id="0e6f6-121">The **Backup/Restore Throughput/sec** counter of the [SQLServer:Databases](../performance-monitor/sql-server-databases-object.md) object</span></span>  
  
 <span data-ttu-id="0e6f6-122">有关 Windows 计数器的信息，请参阅 Windows 帮助。</span><span class="sxs-lookup"><span data-stu-id="0e6f6-122">For information about Windows counters, see Windows help.</span></span> <span data-ttu-id="0e6f6-123">有关如何使用 SQL Server 计数器的信息，请参阅 [使用 SQL Server 对象](../performance-monitor/use-sql-server-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="0e6f6-123">For information about how to work with SQL Server counters, see [Use SQL Server Objects](../performance-monitor/use-sql-server-objects.md).</span></span>  
  
  
##  <a name="calculate-the-compression-ratio-of-a-compressed-backup"></a><a name="CompressionRatio"></a> <span data-ttu-id="0e6f6-124">计算压缩的备份的压缩率</span><span class="sxs-lookup"><span data-stu-id="0e6f6-124">Calculate the Compression Ratio of a Compressed Backup</span></span>  
 <span data-ttu-id="0e6f6-125">若要计算备份的压缩率，请使用 **backupset** 历史记录表的 **backup_size** 列和 [compressed_backup_size](/sql/relational-databases/system-tables/backupset-transact-sql) 列中有关此备份的值，如下所示：</span><span class="sxs-lookup"><span data-stu-id="0e6f6-125">To calculate the compression ratio of a backup, use the values for the backup in the **backup_size** and **compressed_backup_size** columns of the [backupset](/sql/relational-databases/system-tables/backupset-transact-sql) history table, as follows:</span></span>  
  
 <span data-ttu-id="0e6f6-126">**backup_size**:**compressed_backup_size**</span><span class="sxs-lookup"><span data-stu-id="0e6f6-126">**backup_size**:**compressed_backup_size**</span></span>  
  
 <span data-ttu-id="0e6f6-127">例如，3:1 的压缩率表明您可以节省大约 66% 的磁盘空间。</span><span class="sxs-lookup"><span data-stu-id="0e6f6-127">For example, a 3:1 compression ratio indicates that you are saving about 66% on disk space.</span></span> <span data-ttu-id="0e6f6-128">若要查询这些列，可以使用以下 Transact-SQL 语句：</span><span class="sxs-lookup"><span data-stu-id="0e6f6-128">To query on these columns, you can use the following Transact-SQL statement:</span></span>  
  
```  
SELECT backup_size/compressed_backup_size FROM msdb..backupset;  
```  
  
 <span data-ttu-id="0e6f6-129">压缩备份的压缩率取决于所压缩的数据。</span><span class="sxs-lookup"><span data-stu-id="0e6f6-129">The compression ratio of a compressed backup depends on the data that has been compressed.</span></span> <span data-ttu-id="0e6f6-130">有多种因素会影响所获得的压缩率。</span><span class="sxs-lookup"><span data-stu-id="0e6f6-130">A variety of factors can impact the compression ratio obtained.</span></span> <span data-ttu-id="0e6f6-131">主要因素包括：</span><span class="sxs-lookup"><span data-stu-id="0e6f6-131">Major factors include:</span></span>  
  
-   <span data-ttu-id="0e6f6-132">数据类型。</span><span class="sxs-lookup"><span data-stu-id="0e6f6-132">The type of data.</span></span>  
  
     <span data-ttu-id="0e6f6-133">字符数据的压缩率要高于其他类型的数据。</span><span class="sxs-lookup"><span data-stu-id="0e6f6-133">Character data compresses more than other types of data.</span></span>  
  
-   <span data-ttu-id="0e6f6-134">页面上各行间数据的一致性。</span><span class="sxs-lookup"><span data-stu-id="0e6f6-134">The consistency of the data among rows on a page.</span></span>  
  
     <span data-ttu-id="0e6f6-135">通常，如果某页包含多个行，而其中的某个字段包含相同的值，则该值可获得较大的压缩。</span><span class="sxs-lookup"><span data-stu-id="0e6f6-135">Typically, if a page contains several rows in which a field contains the same value, significant compression might occur for that value.</span></span> <span data-ttu-id="0e6f6-136">相反，对于包含随机数据或者每页只有一个很大的行的数据库，压缩备份的大小几乎与未压缩的备份相同。</span><span class="sxs-lookup"><span data-stu-id="0e6f6-136">In contrast, for a database that contains random data or that contains only one large row per page, a compressed backup would be almost as large as an uncompressed backup.</span></span>  
  
-   <span data-ttu-id="0e6f6-137">数据是否加密。</span><span class="sxs-lookup"><span data-stu-id="0e6f6-137">Whether the data is encrypted.</span></span>  
  
     <span data-ttu-id="0e6f6-138">与未加密数据相比，同样的加密数据的压缩率要小得多。</span><span class="sxs-lookup"><span data-stu-id="0e6f6-138">Encrypted data compresses significantly less than equivalent unencrypted data.</span></span> <span data-ttu-id="0e6f6-139">如果使用透明数据加密来加密整个数据库，则压缩备份不会将数据库大小减小很多，甚至根本不会减小。</span><span class="sxs-lookup"><span data-stu-id="0e6f6-139">If transparent data encryption is used to encrypt an entire database, compressing backups might not reduce their size by much, if at all.</span></span>  
  
-   <span data-ttu-id="0e6f6-140">数据库是否压缩。</span><span class="sxs-lookup"><span data-stu-id="0e6f6-140">Whether the database is compressed.</span></span>  
  
     <span data-ttu-id="0e6f6-141">如果压缩数据库，则压缩备份不会将大小减小很多，甚至根本不会减小。</span><span class="sxs-lookup"><span data-stu-id="0e6f6-141">If the database is compressed, compressing backups might not reduce their size by much, if at all.</span></span>  
  
  
##  <a name="allocation-of-space-for-the-backup-file"></a><a name="Allocation"></a> <span data-ttu-id="0e6f6-142">为备份文件分配空间</span><span class="sxs-lookup"><span data-stu-id="0e6f6-142">Allocation of Space for the Backup File</span></span>  
 <span data-ttu-id="0e6f6-143">对于压缩的备份，最终备份文件的大小取决于数据可压缩程度，这在备份操作完成之前是未知的。</span><span class="sxs-lookup"><span data-stu-id="0e6f6-143">For compressed backups, the size of the final backup file depends on how compressible the data is, and this is unknown before the backup operation finishes.</span></span>  <span data-ttu-id="0e6f6-144">因此，默认情况下，在使用压缩备份数据库时，数据库引擎将预先分配算法用于备份文件。</span><span class="sxs-lookup"><span data-stu-id="0e6f6-144">Therefore, by default, when backing up a database using compression, the Database Engine uses a pre-allocation algorithm for the backup file.</span></span> <span data-ttu-id="0e6f6-145">此算法为备份文件预先分配数据库大小的预定义的百分比。</span><span class="sxs-lookup"><span data-stu-id="0e6f6-145">This algorithm pre-allocates a predefined percentage of the size of the database for the backup file.</span></span> <span data-ttu-id="0e6f6-146">如果在备份操作过程中需要更多空间，则数据库引擎会增大该文件。</span><span class="sxs-lookup"><span data-stu-id="0e6f6-146">If more space is needed during the backup operation, the Database Engine grows the file.</span></span> <span data-ttu-id="0e6f6-147">如果最终大小小于分配的空间，则在备份操作结束时，数据库引擎会将该文件收缩到备份的实际的最终大小。</span><span class="sxs-lookup"><span data-stu-id="0e6f6-147">If the final size is less than the allocated space, at the end of the backup operation, the Database Engine shrinks the file to the actual final size of the backup.</span></span>  
  
 <span data-ttu-id="0e6f6-148">若要允许备份文件仅在需要时增大以便达到其最终大小，则使用跟踪标志 3042。</span><span class="sxs-lookup"><span data-stu-id="0e6f6-148">To allow the backup file to grow only as needed to reach its final size, use trace flag 3042.</span></span> <span data-ttu-id="0e6f6-149">跟踪标志 3042 导致备份操作绕过默认的备份压缩预先分配算法。</span><span class="sxs-lookup"><span data-stu-id="0e6f6-149">Trace flag 3042 causes the backup operation to bypass the default backup compression pre-allocation algorithm.</span></span> <span data-ttu-id="0e6f6-150">如果您需要仅分配压缩的备份所需的实际大小以便节约空间，则此跟踪标志将很有用。</span><span class="sxs-lookup"><span data-stu-id="0e6f6-150">This trace flag is useful if you need to save on space by allocating only the actual size required for the compressed backup.</span></span> <span data-ttu-id="0e6f6-151">但是，使用此跟踪标志可能会导致轻微的性能损失（在备份操作期间损失可能会增加）。</span><span class="sxs-lookup"><span data-stu-id="0e6f6-151">However, using this trace flag might cause a slight performance penalty (a possible increase in the duration of the backup operation).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="0e6f6-152">相关任务</span><span class="sxs-lookup"><span data-stu-id="0e6f6-152">Related Tasks</span></span>  
  
-   [<span data-ttu-id="0e6f6-153">配置备份压缩 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0e6f6-153">Configure Backup Compression &#40;SQL Server&#41;</span></span>](backup-compression-sql-server.md)  
  
-   [<span data-ttu-id="0e6f6-154">查看或配置 backup compression default 服务器配置选项</span><span class="sxs-lookup"><span data-stu-id="0e6f6-154">View or Configure the backup compression default Server Configuration Option</span></span>](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)  
  
-   [<span data-ttu-id="0e6f6-155">使用资源调控器限制备份压缩的 CPU 使用量 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0e6f6-155">Use Resource Governor to Limit CPU Usage by Backup Compression &#40;Transact-SQL&#41;</span></span>](use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md)  
  
-   [<span data-ttu-id="0e6f6-156">DBCC TRACEON (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0e6f6-156">DBCC TRACEON &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-traceon-transact-sql)  
  
-   [<span data-ttu-id="0e6f6-157">DBCC TRACEOFF (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0e6f6-157">DBCC TRACEOFF &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-traceoff-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="0e6f6-158">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0e6f6-158">See Also</span></span>  
 <span data-ttu-id="0e6f6-159">[备份概述 (SQL Server)](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0e6f6-159">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 [<span data-ttu-id="0e6f6-160">跟踪标志 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0e6f6-160">Trace Flags &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)  
  
  
