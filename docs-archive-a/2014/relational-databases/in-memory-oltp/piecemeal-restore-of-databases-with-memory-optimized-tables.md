---
title: 使用内存优化表的数据库的段落还原 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 732c9721-8dd4-481d-8ff9-1feaaa63f84f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ed23f08d40e23b1d43c1b642f4089fe77646b675
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692404"
---
# <a name="piecemeal-restore-of-databases-with-memory-optimized-tables"></a><span data-ttu-id="e7158-102">使用内存优化表的数据库的段落还原</span><span class="sxs-lookup"><span data-stu-id="e7158-102">Piecemeal Restore of Databases With Memory-Optimized Tables</span></span>
  <span data-ttu-id="e7158-103">使用内存优化表的数据库支持段落还原，但有一个限制（参见下文）。</span><span class="sxs-lookup"><span data-stu-id="e7158-103">Piecemeal restore is supported on databases with memory-optimized tables except for one restriction described below.</span></span> <span data-ttu-id="e7158-104">有关段落备份和还原的详细信息，请参阅 [RESTORE (Transact-SQL)](/sql/t-sql/statements/restore-statements-transact-sql) 和[段落还原 (SQL Server)](../backup-restore/piecemeal-restores-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="e7158-104">For more information about piecemeal backup and restore, see [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) and [Piecemeal Restores &#40;SQL Server&#41;](../backup-restore/piecemeal-restores-sql-server.md).</span></span>  
  
 <span data-ttu-id="e7158-105">内存优化文件组必须同主文件组一起备份和还原：</span><span class="sxs-lookup"><span data-stu-id="e7158-105">A memory-optimized filegroup must be backed up and restored together with the primary filegroup:</span></span>  
  
-   <span data-ttu-id="e7158-106">备份（或还原）主文件组时，必须指定内存优化文件组。</span><span class="sxs-lookup"><span data-stu-id="e7158-106">If you back up (or restore) the primary filegroup you must specify the memory-optimized filegroup.</span></span>  
  
-   <span data-ttu-id="e7158-107">备份（或还原）内存优化文件组时，必须指定主文件组。</span><span class="sxs-lookup"><span data-stu-id="e7158-107">If you backup (or restore) the memory-optimized filegroup you must specify the primary filegroup.</span></span>  
  
 <span data-ttu-id="e7158-108">段落备份和还原的关键方案是，</span><span class="sxs-lookup"><span data-stu-id="e7158-108">Key scenarios for piecemeal backup and restore are,</span></span>  
  
-   <span data-ttu-id="e7158-109">段落备份可减小备份尺寸。</span><span class="sxs-lookup"><span data-stu-id="e7158-109">Piecemeal backup allows you to reduce the size of backup.</span></span> <span data-ttu-id="e7158-110">以下是一些示例：</span><span class="sxs-lookup"><span data-stu-id="e7158-110">Some examples:</span></span>  
  
    -   <span data-ttu-id="e7158-111">配置数据库备份时机，使其在不同时间或不同日期执行，以最大限度地减少对工作负荷的影响。</span><span class="sxs-lookup"><span data-stu-id="e7158-111">Configure the database backup to occur at different times or days to minimize the impact on the workload.</span></span> <span data-ttu-id="e7158-112">有时，由于数据库非常大（ 1 TB 以上），完整数据库备份操作无法在所分配的数据库维护时间内完成。</span><span class="sxs-lookup"><span data-stu-id="e7158-112">One example is a very large database (greater than 1 TB) where a full database backup cannot complete in the time allocated for database maintenance.</span></span> <span data-ttu-id="e7158-113">在这种情况下，可使用段落备份将完整的数据库备份到多个段落备份中。</span><span class="sxs-lookup"><span data-stu-id="e7158-113">In that situation, you can use piecemeal backup to backup the full database in multiple piecemeal backups.</span></span>  
  
    -   <span data-ttu-id="e7158-114">如果文件组标记为只读，则无需在其标记为只读后进行事务日志备份。</span><span class="sxs-lookup"><span data-stu-id="e7158-114">If a filegroup is marked read-only, it does not require a transaction log backup after it was marked read-only.</span></span> <span data-ttu-id="e7158-115">将文件组标记为只读后，可选择只备份该文件组一次。</span><span class="sxs-lookup"><span data-stu-id="e7158-115">You can choose to back up the filegroup only once after marking it read-only.</span></span>  
  
-   <span data-ttu-id="e7158-116">段落还原。</span><span class="sxs-lookup"><span data-stu-id="e7158-116">Piecemeal restore.</span></span>  
  
    -   <span data-ttu-id="e7158-117">段落还原的目的是将数据库的关键部分先行上线（不必待所有数据还原完毕）。</span><span class="sxs-lookup"><span data-stu-id="e7158-117">The goal of a piecemeal restore is to bring the critical parts of database online without waiting for all the data.</span></span> <span data-ttu-id="e7158-118">举个例子，如果某数据库包含分区数据，而较旧的分区很少使用。</span><span class="sxs-lookup"><span data-stu-id="e7158-118">One example is if a database has partitioned data, such that older partitions are only used rarely.</span></span> <span data-ttu-id="e7158-119">则可根据需要还原数据。</span><span class="sxs-lookup"><span data-stu-id="e7158-119">You can restore them only on an as-needed basis.</span></span> <span data-ttu-id="e7158-120">对于包含历史数据等的文件组，亦可如此操作。</span><span class="sxs-lookup"><span data-stu-id="e7158-120">Similar for filegroups that contain, for example, historical data.</span></span>  
  
    -   <span data-ttu-id="e7158-121">使用页修复可通过指定要还原的页来修复页损坏。</span><span class="sxs-lookup"><span data-stu-id="e7158-121">Using page repair, you can fix page corruption by specifically restoring the page.</span></span> <span data-ttu-id="e7158-122">有关详细信息，请参阅[还原页 (SQL Server)](../backup-restore/restore-pages-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="e7158-122">For more information, see [Restore Pages &#40;SQL Server&#41;](../backup-restore/restore-pages-sql-server.md).</span></span>  
  
## <a name="samples"></a><span data-ttu-id="e7158-123">示例</span><span class="sxs-lookup"><span data-stu-id="e7158-123">Samples</span></span>  
 <span data-ttu-id="e7158-124">示例使用下面的架构：</span><span class="sxs-lookup"><span data-stu-id="e7158-124">The examples use the following schema:</span></span>  
  
```  
CREATE DATABASE imoltp  
ON PRIMARY (name = imoltp_primary1, filename = 'c:\data\imoltp_data1.mdf')  
LOG ON (name = imoltp_log, filename = 'c:\data\imoltp_log.ldf')  
GO  
  
ALTER DATABASE imoltp ADD FILE (name = imoltp_primary2, filename = 'c:\data\imoltp_data2.ndf')  
GO  
  
ALTER DATABASE imoltp ADD FILEGROUP imoltp_secondary  
ALTER DATABASE imoltp ADD FILE (name = imoltp_secondary, filename = 'c:\data\imoltp_secondary.ndf') TO FILEGROUP imoltp_secondary  
GO  
  
ALTER DATABASE imoltp ADD FILEGROUP imoltp_mod CONTAINS MEMORY_OPTIMIZED_DATA   
ALTER DATABASE imoltp ADD FILE (name='imoltp_mod1', filename='c:\data\imoltp_mod1') TO FILEGROUP imoltp_mod   
ALTER DATABASE imoltp ADD FILE (name='imoltp_mod2', filename='c:\data\imoltp_mod2') TO FILEGROUP imoltp_mod   
GO  
```  
  
### <a name="backup"></a><span data-ttu-id="e7158-125">备份</span><span class="sxs-lookup"><span data-stu-id="e7158-125">Backup</span></span>  
 <span data-ttu-id="e7158-126">该示例演示如何备份主文件组和内存优化文件组。</span><span class="sxs-lookup"><span data-stu-id="e7158-126">This sample shows how to backup the primary filegroup and the memory-optimized filegroup.</span></span> <span data-ttu-id="e7158-127">必须同时指定主文件组和内存优化文件组。</span><span class="sxs-lookup"><span data-stu-id="e7158-127">You must specify both primary and memory-optimized filegroup together.</span></span>  
  
```  
backup database imoltp filegroup='primary', filegroup='imoltp_mod' to disk='c:\data\imoltp.dmp' with init  
```  
  
 <span data-ttu-id="e7158-128">下面的示例演示：对于不使用内存优化表的数据库，备份主文件组和内存优化文件组以外的文件组时的操作亦大同小异。</span><span class="sxs-lookup"><span data-stu-id="e7158-128">The following sample shows that a back up of filegroup(s) other than primary and memory-optimized filegroup works similar to the databases without memory-optimized tables.</span></span> <span data-ttu-id="e7158-129">下面的命令用于备份辅助文件组</span><span class="sxs-lookup"><span data-stu-id="e7158-129">The following command backups up the secondary filegroup</span></span>  
  
```  
backup database imoltp filegroup='imoltp_secondary' to disk='c:\data\imoltp_secondary.dmp' with init  
```  
  
### <a name="restore"></a><span data-ttu-id="e7158-130">还原</span><span class="sxs-lookup"><span data-stu-id="e7158-130">Restore</span></span>  
 <span data-ttu-id="e7158-131">下面的示例演示如何同时还原主文件组和内存优化文件组。</span><span class="sxs-lookup"><span data-stu-id="e7158-131">The following sample shows how to restore the primary filegroup and memory-optimized filegroup together.</span></span>  
  
```  
restore database imoltp filegroup = 'primary', filegroup = 'imoltp_mod'   
from disk='c:\data\imoltp.dmp' with partial, norecovery  
  
--restore the transaction log  
 RESTORE LOG [imoltp] FROM DISK = N'c:\data\imoltp_log.dmp' WITH  FILE = 1,  NOUNLOAD,  STATS = 10  
GO  
```  
  
 <span data-ttu-id="e7158-132">下一个示例演示：对于不使用内存优化表的数据库，还原主文件组和内存优化文件组以外的文件组时的操作亦大同小异</span><span class="sxs-lookup"><span data-stu-id="e7158-132">The next sample shows that restoring filegroup(s) other than the primary and memory-optimized filegroup works similar to the databases without memory-optimized tables</span></span>  
  
```  
RESTORE DATABASE [imoltp] FILE = N'imoltp_secondary'   
FROM  DISK = N'c:\data\imoltp_secondary.dmp' WITH  FILE = 1,  RECOVERY,  NOUNLOAD,  STATS = 10  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="e7158-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e7158-133">See Also</span></span>  
 [<span data-ttu-id="e7158-134">内存优化表的备份、还原和恢复</span><span class="sxs-lookup"><span data-stu-id="e7158-134">Backup, Restore, and Recovery of Memory-Optimized Tables</span></span>](../../database-engine/backup-restore-and-recovery-of-memory-optimized-tables.md)  
  
  
