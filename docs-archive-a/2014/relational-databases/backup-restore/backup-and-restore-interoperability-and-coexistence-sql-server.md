---
title: 备份和还原：互操作性和共存 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- file restores [SQL Server], related features
- restoring [SQL Server], files
- restoring files [SQL Server], related features
- backups [SQL Server], files or filegroups
- file backups [SQL Server], related features
ms.assetid: 69f212b8-edcd-4c5d-8a8a-679ced33c128
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: cd78e5f1e85510ec7a14548280a616a9b32aec55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576847"
---
# <a name="backup-and-restore-interoperability-and-coexistence-sql-server"></a><span data-ttu-id="de605-102">备份和还原：互操作性和共存 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="de605-102">Backup and Restore: Interoperability and Coexistence (SQL Server)</span></span>
  <span data-ttu-id="de605-103">本主题描述 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中若干功能的备份和还原注意事项。</span><span class="sxs-lookup"><span data-stu-id="de605-103">This topic describes backup-and-restore considerations for several features in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="de605-104">这些功能包括：文件还原和数据库启动、联机还原和禁用的索引、数据库镜像以及段落还原和全文索引。</span><span class="sxs-lookup"><span data-stu-id="de605-104">These features include: file restore and database startup, online restore and disabled indexes, database mirroring, and piecemeal restore and full-text indexes.</span></span>  
  
 <span data-ttu-id="de605-105">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="de605-105">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="de605-106">文件还原和数据库启动</span><span class="sxs-lookup"><span data-stu-id="de605-106">File Restore and Database Startup</span></span>](#FileRestoreAndDbStartup)  
  
-   [<span data-ttu-id="de605-107">联机还原和禁用的索引</span><span class="sxs-lookup"><span data-stu-id="de605-107">Online Restore and Disabled Indexes</span></span>](#OnlineRestoreAndDisabledIndexes)  
  
-   [<span data-ttu-id="de605-108">数据库镜像以及备份和还原</span><span class="sxs-lookup"><span data-stu-id="de605-108">Database Mirroring and Backup and Restore</span></span>](#DbMandBnR)  
  
-   [<span data-ttu-id="de605-109">段落还原和全文索引</span><span class="sxs-lookup"><span data-stu-id="de605-109">Piecemeal Restore and Full-Text Indexes</span></span>](#PiecemealAndFTIndexes)  
  
-   [<span data-ttu-id="de605-110">文件备份、还原和压缩</span><span class="sxs-lookup"><span data-stu-id="de605-110">File Backup and Restore and Compression</span></span>](#FileBnRandCompression)  
  
-   [<span data-ttu-id="de605-111">相关任务</span><span class="sxs-lookup"><span data-stu-id="de605-111">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="file-restore-and-database-startup"></a><a name="FileRestoreAndDbStartup"></a> <span data-ttu-id="de605-112">文件还原和数据库启动</span><span class="sxs-lookup"><span data-stu-id="de605-112">File Restore and Database Startup</span></span>  
 <span data-ttu-id="de605-113">本节仅与包含多个文件组的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库相关。</span><span class="sxs-lookup"><span data-stu-id="de605-113">This section is relevant only for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases that have multiple filegroups.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="de605-114">数据库启动时，只有其文件在数据库关闭时处于联机状态的文件组能够恢复并处于联机状态。</span><span class="sxs-lookup"><span data-stu-id="de605-114">When a database is started, only filegroups whose files were online when the database was closed are recovered and brought online.</span></span>  
  
 <span data-ttu-id="de605-115">如果数据库启动过程中出现问题，恢复将失败且数据库被标记为 SUSPECT。</span><span class="sxs-lookup"><span data-stu-id="de605-115">If a problem is encountered during database startup, recovery fails, and the database is marked as SUSPECT.</span></span> <span data-ttu-id="de605-116">如果可以将问题隔离到单个文件或多个文件，则数据库管理员可以使文件脱机并尝试重新启动数据库。</span><span class="sxs-lookup"><span data-stu-id="de605-116">If the problem can be isolated to a file or files, the database administrator can take the files offline and try to restart the database.</span></span> <span data-ttu-id="de605-117">若要使文件脱机，可以使用下列 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) 语句：</span><span class="sxs-lookup"><span data-stu-id="de605-117">To take a file offline, you can use the following [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) statement:</span></span>  
  
 <span data-ttu-id="de605-118">ALTER DATABASE *database_name*修改文件 (name **= ' *`filename`* '**，OFFLINE) </span><span class="sxs-lookup"><span data-stu-id="de605-118">ALTER DATABASE *database_name* MODIFY FILE (NAME **='*`filename`*'**, OFFLINE)</span></span>  
  
 <span data-ttu-id="de605-119">如果数据库成功启动，则任何包含脱机文件的文件组将保持脱机状态。</span><span class="sxs-lookup"><span data-stu-id="de605-119">If startup succeeds, any filegroup that contains an offline file remains offline.</span></span>  
  
##  <a name="online-restore-and-disabled-indexes"></a><a name="OnlineRestoreAndDisabledIndexes"></a> <span data-ttu-id="de605-120">联机还原和禁用的索引</span><span class="sxs-lookup"><span data-stu-id="de605-120">Online Restore and Disabled Indexes</span></span>  
 <span data-ttu-id="de605-121">本节仅适用于包含多个文件组的数据库；在简单恢复模式下，适用于至少包含一个只读文件组的数据库。</span><span class="sxs-lookup"><span data-stu-id="de605-121">This section is relevant only for databases that have multiple filegroups and, for the simple recovery model, at least one read-only filegroup.</span></span>  
  
 <span data-ttu-id="de605-122">在此类情况下，当数据库处于联机状态时，仅当包含索引任意部分的所有文件组均联机时，才能创建、删除、启用或禁用索引。</span><span class="sxs-lookup"><span data-stu-id="de605-122">In these cases, when a database is online, the index can be created, dropped, enabled or disabled only if all filegroups holding any part of the index are online.</span></span>  
  
 <span data-ttu-id="de605-123">有关还原脱机文件组的信息，请参阅[联机还原 (SQL Server)](online-restore-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="de605-123">For information about restoring offline filegroups, see [Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md).</span></span>  
  
##  <a name="database-mirroring-and-backup-and-restore"></a><a name="DbMandBnR"></a> <span data-ttu-id="de605-124">数据库镜像以及备份和还原</span><span class="sxs-lookup"><span data-stu-id="de605-124">Database Mirroring and Backup and Restore</span></span>  
 <span data-ttu-id="de605-125">本节仅与包含多个文件组的完整模式数据库有关。</span><span class="sxs-lookup"><span data-stu-id="de605-125">This section is relevant only for full-model databases that have multiple filegroups.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="de605-126">后续版本的 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]将删除数据库镜像功能。</span><span class="sxs-lookup"><span data-stu-id="de605-126">The database mirroring feature will be removed in a future version of Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="de605-127">请避免在新的开发工作中使用该功能，并着手修改当前还在使用该功能的应用程序。</span><span class="sxs-lookup"><span data-stu-id="de605-127">Avoid using this feature in new development work, and plan to modify applications that currently use this feature.</span></span> <span data-ttu-id="de605-128">请改用 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="de605-128">Use [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] instead.</span></span>  
  
 <span data-ttu-id="de605-129">“数据库镜像”是一种提高数据库可用性的解决方案。</span><span class="sxs-lookup"><span data-stu-id="de605-129">Database mirroring is a solution for increasing database availability.</span></span> <span data-ttu-id="de605-130">镜像基于每个数据库实现，并且只适用于使用完整恢复模式的数据库。</span><span class="sxs-lookup"><span data-stu-id="de605-130">Mirroring is implemented on a per-database basis and works only with databases that use the full recovery model.</span></span> <span data-ttu-id="de605-131">有关详细信息，请参阅[数据库镜像 (SQL Server)](../../database-engine/database-mirroring/database-mirroring-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="de605-131">For more information, see [Database Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="de605-132">若要分发数据库中部分文件组的副本，请使用复制：仅复制文件组中您要复制到其他服务器的那些对象。</span><span class="sxs-lookup"><span data-stu-id="de605-132">To distribute copies of a subset of the filegroups in a database, use replication: replicate only those objects in the filegroups you want to copy to other servers.</span></span> <span data-ttu-id="de605-133">有关复制的详细信息，请参阅 [SQL Server 复制](../../relational-databases/replication/sql-server-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="de605-133">For more information about replication, see [SQL Server Replication](../../relational-databases/replication/sql-server-replication.md).</span></span>  
  
### <a name="creating-the-mirror-database"></a><span data-ttu-id="de605-134">创建镜像数据库</span><span class="sxs-lookup"><span data-stu-id="de605-134">Creating the Mirror Database</span></span>  
 <span data-ttu-id="de605-135">镜像数据库是通过还原 (WITH NORECOVERY) 镜像服务器上主体数据库的备份创建的。</span><span class="sxs-lookup"><span data-stu-id="de605-135">The mirror database is created by restoring, WITH NORECOVERY, backups of the principal database on the mirror server.</span></span> <span data-ttu-id="de605-136">还原后的数据库必须保持相同的数据库名称。</span><span class="sxs-lookup"><span data-stu-id="de605-136">The restore must keep the same database name.</span></span> <span data-ttu-id="de605-137">有关详细信息，请参阅 [为镜像准备镜像数据库 (SQL Server)](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md)的各版本中均未提供见证服务器实例。</span><span class="sxs-lookup"><span data-stu-id="de605-137">For more information, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md).</span></span>  
  
 <span data-ttu-id="de605-138">您可以使用段落还原顺序在支持镜像数据库的地方创建镜像数据库。</span><span class="sxs-lookup"><span data-stu-id="de605-138">You can create the mirror database by using use a piecemeal restore sequence, where supported.</span></span> <span data-ttu-id="de605-139">但是，在开始镜像之前，必须还原所有文件组后才能，通常还必须还原日志备份以保证镜像数据库的时间与原始数据库的时间足够接近。</span><span class="sxs-lookup"><span data-stu-id="de605-139">However, you cannot start mirroring until you have restored all the filegroups and, typically, restored log backups to get the mirror database close enough in time with the principal database.</span></span> <span data-ttu-id="de605-140">有关详细信息，请参阅[段落还原 (SQL Server)](piecemeal-restores-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="de605-140">For more information, see [Piecemeal Restores &#40;SQL Server&#41;](piecemeal-restores-sql-server.md).</span></span>  
  
### <a name="restrictions-on-backup-and-restore-during-mirroring"></a><span data-ttu-id="de605-141">镜像期间备份和还原的限制</span><span class="sxs-lookup"><span data-stu-id="de605-141">Restrictions on Backup and Restore During Mirroring</span></span>  
 <span data-ttu-id="de605-142">数据库镜像会话活动时，将应用以下限制：</span><span class="sxs-lookup"><span data-stu-id="de605-142">While a database mirroring session is active, the following restrictions apply:</span></span>  
  
-   <span data-ttu-id="de605-143">不允许备份和还原镜像数据库。</span><span class="sxs-lookup"><span data-stu-id="de605-143">Backup and restore of the mirror database are not allowed.</span></span>  
  
-   <span data-ttu-id="de605-144">允许备份主体数据库，但不允许 BACKUP LOG WITH NORECOVERY。</span><span class="sxs-lookup"><span data-stu-id="de605-144">Backup of the principal database is allowed, but BACKUP LOG WITH NORECOVERY is not allowed.</span></span>  
  
-   <span data-ttu-id="de605-145">不允许还原主体数据库。</span><span class="sxs-lookup"><span data-stu-id="de605-145">Restoring the principal database is not allowed.</span></span>  
  
##  <a name="piecemeal-restore-and-full-text-indexes"></a><a name="PiecemealAndFTIndexes"></a> <span data-ttu-id="de605-146">段落还原和全文索引</span><span class="sxs-lookup"><span data-stu-id="de605-146">Piecemeal Restore and Full-Text Indexes</span></span>  
 <span data-ttu-id="de605-147">本节仅与包含多个文件组的数据库有关；对于简单模式数据库，仅与只读文件组有关。</span><span class="sxs-lookup"><span data-stu-id="de605-147">This section is relevant only for databases that contain multiple filegroups and, for the simple-model databases, only for read-only filegroups.</span></span>  
  
 <span data-ttu-id="de605-148">全文索引存储在数据库文件组中，受段落还原的影响。</span><span class="sxs-lookup"><span data-stu-id="de605-148">Full-text indexes are stored in database filegroups and can be affected by a piecemeal restore.</span></span> <span data-ttu-id="de605-149">如果全文索引与任何关联的表数据位于同一文件组中，则段落还原将按预期的方式工作。</span><span class="sxs-lookup"><span data-stu-id="de605-149">If the full-text index resides in the same filegroup as any of the associated table data, piecemeal restore works as expected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="de605-150">若要查看包含全文索引的文件组的文件组 ID，请选择 [sys.fulltext_indexes](/sql/relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql)的 data_space_id 列。</span><span class="sxs-lookup"><span data-stu-id="de605-150">To view the filegroup ID of the filegroup that contains a full-text index, select the data_space_id column of [sys.fulltext_indexes](/sql/relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql).</span></span>  
  
### <a name="full-text-indexes-and-tables-in-separate-filegroups"></a><span data-ttu-id="de605-151">全文索引和表在不同的文件组中</span><span class="sxs-lookup"><span data-stu-id="de605-151">Full-Text Indexes and Tables in Separate Filegroups</span></span>  
 <span data-ttu-id="de605-152">如果全文索引与所有关联的表数据位于不同的文件组中，则段落还原的行为取决于哪个文件组首先还原并变为联机：</span><span class="sxs-lookup"><span data-stu-id="de605-152">If a full-text index resides in a separate filegroup from all of the associated table data, the behavior of piecemeal restore depends on which of the filegroups is restored and brought online first:</span></span>  
  
-   <span data-ttu-id="de605-153">如果包含全文索引的文件组先于包含关联表数据的文件组还原并变为联机，则在全文索引联机后，全文搜索将按预期的方式工作。</span><span class="sxs-lookup"><span data-stu-id="de605-153">If the filegroup that contains the full-text index is restored and brought online before the filegroups that contain the associated table data, full-text search works as expected as soon as the full-text index is online.</span></span>  
  
-   <span data-ttu-id="de605-154">如果包含表数据的文件组先于包含全文索引的文件组还原并变为联机，则全文行为可能会受到影响。</span><span class="sxs-lookup"><span data-stu-id="de605-154">If the filegroup that contains the table data is restored and brought online before the filegroup that contains the full-text index, full-text behavior might be affected.</span></span> <span data-ttu-id="de605-155">这是因为在索引联机之前，触发填充、重新生成目录或者重新组织目录的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句会失败。</span><span class="sxs-lookup"><span data-stu-id="de605-155">This is because [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that trigger a population, rebuild the catalog, or reorganize the catalog fail until the index is brought online.</span></span> <span data-ttu-id="de605-156">这些语句包括 CREATE FULLTEXT INDEX、ALTER FULLTEXT INDEX、DROP FULLTEXT INDEX 和 ALTER FULLTEXT CATALOG。</span><span class="sxs-lookup"><span data-stu-id="de605-156">These statements include CREATE FULLTEXT INDEX, ALTER FULLTEXT INDEX, DROP FULLTEXT INDEX, and ALTER FULLTEXT CATALOG.</span></span>  
  
     <span data-ttu-id="de605-157">在这种情况下，下列因素就至关重要：</span><span class="sxs-lookup"><span data-stu-id="de605-157">In this case, the following factors are significant:</span></span>  
  
    -   <span data-ttu-id="de605-158">如果全文索引具有更改跟踪，则在索引文件组联机之前，用户 DML 会失败。</span><span class="sxs-lookup"><span data-stu-id="de605-158">If the full-text index has change tracking, user DML will fail until the index filegroup is brought online.</span></span> <span data-ttu-id="de605-159">在索引文件组联机之前，删除操作也会失败。</span><span class="sxs-lookup"><span data-stu-id="de605-159">Delete operation will also fail until the index filegroup is online.</span></span>  
  
    -   <span data-ttu-id="de605-160">不管是否有跟踪更改，由于索引不可用，全文查询都会失败。</span><span class="sxs-lookup"><span data-stu-id="de605-160">Regardless of change tracking, full-text queries fail because the index is not available.</span></span> <span data-ttu-id="de605-161">如果在包含全文索引的文件组脱机时尝试全文查询，则会返回错误。</span><span class="sxs-lookup"><span data-stu-id="de605-161">If a full-text query is tried when the filegroup that contains the full-text index is offline, an error is returned.</span></span>  
  
    -   <span data-ttu-id="de605-162">状态函数（如 FULLTEXTCATALOGPROPERTY）只有在不必访问全文索引时才会成功。</span><span class="sxs-lookup"><span data-stu-id="de605-162">Status functions (such as FULLTEXTCATALOGPROPERTY) succeed only when they do not have to access full-text index.</span></span> <span data-ttu-id="de605-163">例如，访问任何联机的全文元数据都会成功，但 **uniquekeycount, itemcount** 会失败。</span><span class="sxs-lookup"><span data-stu-id="de605-163">For example, access to any online full-text metadata would succeed, but **uniquekeycount, itemcount** would fail.</span></span>  
  
     <span data-ttu-id="de605-164">在全文索引文件组还原并变为联机之后，目录数据和表数据将一致。</span><span class="sxs-lookup"><span data-stu-id="de605-164">After the full-text index filegroup is restored and brought online, the index data and table data are consistent.</span></span>  
  
 <span data-ttu-id="de605-165">在基表文件组和全文索引文件组均联机后，将立即恢复所有暂停的全文填充。</span><span class="sxs-lookup"><span data-stu-id="de605-165">As soon as both the base table filegroup and the full-text index filegroup are online, any paused full-text population is resumed.</span></span>  
  
##  <a name="file-backup-and-restore-and-compression"></a><a name="FileBnRandCompression"></a> <span data-ttu-id="de605-166">文件备份、还原和压缩</span><span class="sxs-lookup"><span data-stu-id="de605-166">File Backup and Restore and Compression</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="de605-167">支持对只读文件组和只读数据库进行 NTFS 文件系统数据压缩。</span><span class="sxs-lookup"><span data-stu-id="de605-167">supports NTFS file system data compression of read-only filegroups and read-only databases.</span></span>  
  
 <span data-ttu-id="de605-168">压缩的 NTFS 文件支持还原只读文件组中的文件。</span><span class="sxs-lookup"><span data-stu-id="de605-168">Restoring files in a read-only filegroup is supported on compressed NTFS files.</span></span> <span data-ttu-id="de605-169">这些文件组的备份和还原实质上与任何只读文件组相同，但下列情况除外：</span><span class="sxs-lookup"><span data-stu-id="de605-169">Backup and restore of these filegroups works essentially as it would for any read-only filegroup, with the following exceptions:</span></span>  
  
-   <span data-ttu-id="de605-170">将读写文件（包括读写数据库的主文件或日志文件）还原为压缩卷会失败并显示错误。</span><span class="sxs-lookup"><span data-stu-id="de605-170">Restoring a read-write file (including the primary or log files of a read-write database) to a compressed volume fails and displays an error.</span></span>  
  
-   <span data-ttu-id="de605-171">但是，将只读数据库还原为压缩卷是允许的。</span><span class="sxs-lookup"><span data-stu-id="de605-171">Restoring a read-only database to a compressed volume is allowed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="de605-172">读/写数据库的日志文件决不要放在压缩文件系统中。</span><span class="sxs-lookup"><span data-stu-id="de605-172">Log files of read/write databases should never be placed on compressed file systems.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="de605-173">相关任务</span><span class="sxs-lookup"><span data-stu-id="de605-173">Related Tasks</span></span>  
  
-   [<span data-ttu-id="de605-174">为镜像准备镜像数据库 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="de605-174">Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md)  
  
-   [<span data-ttu-id="de605-175">备份和还原全文目录和索引</span><span class="sxs-lookup"><span data-stu-id="de605-175">Back Up and Restore Full-Text Catalogs and Indexes</span></span>](../search/back-up-and-restore-full-text-catalogs-and-indexes.md)  
  
## <a name="see-also"></a><span data-ttu-id="de605-176">另请参阅</span><span class="sxs-lookup"><span data-stu-id="de605-176">See Also</span></span>  
 <span data-ttu-id="de605-177">[SQL Server 数据库的备份和还原](back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="de605-177">[Back Up and Restore of SQL Server Databases](back-up-and-restore-of-sql-server-databases.md) </span></span>  
 <span data-ttu-id="de605-178">[备份和还原复制的数据库](../replication/administration/back-up-and-restore-replicated-databases.md) </span><span class="sxs-lookup"><span data-stu-id="de605-178">[Back Up and Restore Replicated Databases](../replication/administration/back-up-and-restore-replicated-databases.md) </span></span>  
 [<span data-ttu-id="de605-179">活动辅助副本：辅助副本上的备份 &#40;AlwaysOn 可用性组&#41;</span><span class="sxs-lookup"><span data-stu-id="de605-179">Active Secondaries: Backup on Secondary Replicas &#40;AlwaysOn Availability Groups&#41;</span></span>](../../database-engine/availability-groups/windows/active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md)  
  
  
