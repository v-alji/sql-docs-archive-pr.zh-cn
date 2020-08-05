---
title: 数据库分离和附加 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- upgrading databases
- databases [SQL Server], detaching
- detach database [SQL Server]
- databases [SQL Server], attaching
- removing databases
- transaction logs [SQL Server], detaching
- databases [SQL Server], removing
- restoring [SQL Server], attached databases
- transaction logs [SQL Server], attaching
- differential backups, after detaching
- moving databases
- attach database [SQL Server]
- detaching databases [SQL Server]
- differential base [SQL Server]
- attaching databases [SQL Server]
- databases [SQL Server], moving
ms.assetid: d0de0639-bc54-464e-98b1-6af22a27eb86
author: stevestein
ms.author: sstein
ms.openlocfilehash: 54eeeec995e390b71ce8871b680c26138fc88783
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581310"
---
# <a name="database-detach-and-attach-sql-server"></a><span data-ttu-id="78b9d-102">数据库分离和附加 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="78b9d-102">Database Detach and Attach (SQL Server)</span></span>
  <span data-ttu-id="78b9d-103">可以分离数据库的数据和事务日志文件，然后将它们重新附加到同一或其他 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例。</span><span class="sxs-lookup"><span data-stu-id="78b9d-103">The data and transaction log files of a database can be detached and then reattached to the same or another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="78b9d-104">如果要将数据库更改到同一计算机的不同 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例或要移动数据库，分离和附加数据库会很有用。</span><span class="sxs-lookup"><span data-stu-id="78b9d-104">Detaching and attaching a database is useful if you want to change the database to a different instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on the same computer or to move the database.</span></span>  
  
 <span data-ttu-id="78b9d-105">在 64 位和 32 位环境中，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 磁盘存储格式均相同。</span><span class="sxs-lookup"><span data-stu-id="78b9d-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on-disk storage format is the same in the 64-bit and 32-bit environments.</span></span> <span data-ttu-id="78b9d-106">因此，可以将 32 位环境中的数据库附加到 64 位环境中，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="78b9d-106">Therefore, attach works across 32-bit and 64-bit environments.</span></span>  <span data-ttu-id="78b9d-107">从运行在某个环境中的服务器实例上分离的数据库可以附加到运行在另一个环境中的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="78b9d-107">A database detached from a server instance running in one environment can be attached on a server instance that runs in another environment.</span></span>  
  
  
  
##  <a name="security"></a><a name="Security"></a> <span data-ttu-id="78b9d-108">Security</span><span class="sxs-lookup"><span data-stu-id="78b9d-108">Security</span></span>  
 <span data-ttu-id="78b9d-109">文件访问权限可在很多数据库操作过程中设置，其中包括分离或附加数据库。</span><span class="sxs-lookup"><span data-stu-id="78b9d-109">File access permissions are set during a number of database operations, including detaching or attaching a database.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="78b9d-110">建议您不要附加或还原来自未知或不可信源的数据库。</span><span class="sxs-lookup"><span data-stu-id="78b9d-110">We recommend that you do not attach or restore databases from unknown or untrusted sources.</span></span> <span data-ttu-id="78b9d-111">此类数据库可能包含恶意代码，这些代码可能会执行非预期的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 代码，或者通过修改架构或物理数据库结构导致错误。</span><span class="sxs-lookup"><span data-stu-id="78b9d-111">Such databases could contain malicious code that might execute unintended [!INCLUDE[tsql](../../includes/tsql-md.md)] code or cause errors by modifying the schema or the physical database structure.</span></span> <span data-ttu-id="78b9d-112">使用来自未知源或不可信源的数据库前，请在非生产服务器上针对数据库运行 [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) ，然后检查数据库中的代码，例如存储过程或其他用户定义代码。</span><span class="sxs-lookup"><span data-stu-id="78b9d-112">Before you use a database from an unknown or untrusted source, run [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) on the database on a nonproduction server and also examine the code, such as stored procedures or other user-defined code, in the database.</span></span>  
  
##  <a name="detaching-a-database"></a><a name="DetachDb"></a> <span data-ttu-id="78b9d-113">分离数据库</span><span class="sxs-lookup"><span data-stu-id="78b9d-113">Detaching a Database</span></span>  
 <span data-ttu-id="78b9d-114">分离数据库是指将数据库从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例中删除，但使数据库在其数据文件和事务日志文件中保持不变。</span><span class="sxs-lookup"><span data-stu-id="78b9d-114">Detaching a database removes it from the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] but leaves the database intact within its data files and transaction log files.</span></span> <span data-ttu-id="78b9d-115">之后，就可以使用这些文件将数据库附加到任何 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例，包括分离该数据库的服务器。</span><span class="sxs-lookup"><span data-stu-id="78b9d-115">These files can then be used to attach the database to any instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], including the server from which the database was detached.</span></span>  
  
 <span data-ttu-id="78b9d-116">如果存在下列任何情况，则不能分离数据库：</span><span class="sxs-lookup"><span data-stu-id="78b9d-116">You cannot detach a database if any of the following are true:</span></span>  
  
-   <span data-ttu-id="78b9d-117">已复制并发布数据库。</span><span class="sxs-lookup"><span data-stu-id="78b9d-117">The database is replicated and published.</span></span> <span data-ttu-id="78b9d-118">如果进行复制，则数据库必须是未发布的。</span><span class="sxs-lookup"><span data-stu-id="78b9d-118">If replicated, the database must be unpublished.</span></span> <span data-ttu-id="78b9d-119">必须通过运行 [sp_replicationdboption](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql)禁用发布后，才能分离数据库。</span><span class="sxs-lookup"><span data-stu-id="78b9d-119">Before you can detach it, you must disable publishing by running [sp_replicationdboption](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="78b9d-120">如果无法使用 **sp_replicationdboption**，可以通过运行 [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql)删除复制。</span><span class="sxs-lookup"><span data-stu-id="78b9d-120">If you cannot use **sp_replicationdboption**, you can remove replication by running [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql).</span></span>  
  
-   <span data-ttu-id="78b9d-121">数据库中存在数据库快照。</span><span class="sxs-lookup"><span data-stu-id="78b9d-121">A database snapshot exists on the database.</span></span>  
  
     <span data-ttu-id="78b9d-122">必须首先删除所有数据库快照，然后才能分离数据库。</span><span class="sxs-lookup"><span data-stu-id="78b9d-122">Before you can detach the database, you must drop all of its snapshots.</span></span> <span data-ttu-id="78b9d-123">有关详细信息，请参阅 [删除数据库快照 (Transact-SQL)](drop-a-database-snapshot-transact-sql.md)实例。</span><span class="sxs-lookup"><span data-stu-id="78b9d-123">For more information, see [Drop a Database Snapshot &#40;Transact-SQL&#41;](drop-a-database-snapshot-transact-sql.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="78b9d-124">不能分离或附加数据库快照。</span><span class="sxs-lookup"><span data-stu-id="78b9d-124">A database snapshot cannot be detached or attached.</span></span>  
  
-   <span data-ttu-id="78b9d-125">该数据库正在某个数据库镜像会话中进行镜像。</span><span class="sxs-lookup"><span data-stu-id="78b9d-125">The database is being mirrored in a database mirroring session.</span></span>  
  
     <span data-ttu-id="78b9d-126">除非终止该会话，否则无法分离该数据库。</span><span class="sxs-lookup"><span data-stu-id="78b9d-126">The database cannot be detached unless the session is terminated.</span></span> <span data-ttu-id="78b9d-127">有关详细信息，请参阅 [删除数据库镜像 (SQL Server)](../../database-engine/database-mirroring/database-mirroring-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="78b9d-127">For more information, see [Removing Database Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md).</span></span>  
  
-   <span data-ttu-id="78b9d-128">数据库处于可疑状态。</span><span class="sxs-lookup"><span data-stu-id="78b9d-128">The database is suspect.</span></span> <span data-ttu-id="78b9d-129">无法分离可疑数据库；必须将数据库设为紧急模式，才能对其进行分离。</span><span class="sxs-lookup"><span data-stu-id="78b9d-129">A suspect database cannot be detached; before you can detach it, you must put it into emergency mode.</span></span> <span data-ttu-id="78b9d-130">有关如何将数据库置于紧急模式下的详细信息，请参阅 [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="78b9d-130">For more information about how to put a database into emergency mode, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
-   <span data-ttu-id="78b9d-131">数据库为系统数据库。</span><span class="sxs-lookup"><span data-stu-id="78b9d-131">The database is a system database.</span></span>  
  
### <a name="backup-and-restore-and-detach"></a><span data-ttu-id="78b9d-132">备份、还原及分离</span><span class="sxs-lookup"><span data-stu-id="78b9d-132">Backup and Restore and Detach</span></span>  
 <span data-ttu-id="78b9d-133">分离只读数据库将会丢失有关差异备份的差异基准的信息。</span><span class="sxs-lookup"><span data-stu-id="78b9d-133">Detaching a read-only database loses information about the differential bases of differential backups.</span></span> <span data-ttu-id="78b9d-134">有关详细信息，请参阅 [差异备份 (SQL Server)](../backup-restore/differential-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="78b9d-134">For more information, see [Differential Backups &#40;SQL Server&#41;](../backup-restore/differential-backups-sql-server.md).</span></span>  
  
### <a name="responding-to-detach-errors"></a><span data-ttu-id="78b9d-135">响应分离错误</span><span class="sxs-lookup"><span data-stu-id="78b9d-135">Responding to Detach Errors</span></span>  
 <span data-ttu-id="78b9d-136">分离数据库时生成的错误会阻止完全关闭数据库和重新生成事务日志。</span><span class="sxs-lookup"><span data-stu-id="78b9d-136">Errors produced while detaching a database can prevent the database from closing cleanly and the transaction log from being rebuilt.</span></span> <span data-ttu-id="78b9d-137">收到错误消息后，请执行下列更正操作：</span><span class="sxs-lookup"><span data-stu-id="78b9d-137">If you receive an error message, perform the following corrective actions:</span></span>  
  
1.  <span data-ttu-id="78b9d-138">重新附加与数据库关联的所有文件，而不仅仅是主文件。</span><span class="sxs-lookup"><span data-stu-id="78b9d-138">Reattach all files associated with the database, not just the primary file.</span></span>  
  
2.  <span data-ttu-id="78b9d-139">解决导致生成错误消息的问题。</span><span class="sxs-lookup"><span data-stu-id="78b9d-139">Resolve the problem that caused the error message.</span></span>  
  
3.  <span data-ttu-id="78b9d-140">再次分离数据库。</span><span class="sxs-lookup"><span data-stu-id="78b9d-140">Detach the database again.</span></span>  
  
##  <a name="attaching-a-database"></a><a name="AttachDb"></a> <span data-ttu-id="78b9d-141">附加数据库</span><span class="sxs-lookup"><span data-stu-id="78b9d-141">Attaching a Database</span></span>  
 <span data-ttu-id="78b9d-142">您可以附加复制的或分离的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="78b9d-142">You can attach a copied or detached [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="78b9d-143">附加 [!INCLUDE[ssVersion2005](../../includes/sscurrent-md.md)] 服务器实例时，会将目录文件从其以前的位置与其他数据库文件一起附加，这与中相同 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="78b9d-143">When you attach a [!INCLUDE[ssVersion2005](../../includes/sscurrent-md.md)] server instance, the catalog files are attached from their previous location along with the other database files, the same as in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="78b9d-144">有关详细信息，请参阅 [全文搜索升级](../search/upgrade-full-text-search.md)。</span><span class="sxs-lookup"><span data-stu-id="78b9d-144">For more information, see [Upgrade Full-Text Search](../search/upgrade-full-text-search.md).</span></span>  
  
 <span data-ttu-id="78b9d-145">附加数据库时，所有数据文件（MDF 文件和 NDF 文件）都必须可用。</span><span class="sxs-lookup"><span data-stu-id="78b9d-145">When you attach a database, all data files (MDF and NDF files) must be available.</span></span> <span data-ttu-id="78b9d-146">如果任何数据文件的路径不同于首次创建数据库或上次附加数据库时的路径，则必须指定文件的当前路径。</span><span class="sxs-lookup"><span data-stu-id="78b9d-146">If any data file has a different path from when the database was first created or last attached, you must specify the current path of the file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="78b9d-147">如果附加的主数据文件是只读的，则 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 假定数据库也是只读的。</span><span class="sxs-lookup"><span data-stu-id="78b9d-147">If the primary data file being attached is read-only, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] assumes that the database is read-only.</span></span>  
  
 <span data-ttu-id="78b9d-148">当加密的数据库首次附加到实例时 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，数据库所有者必须通过执行下面的语句打开数据库的主密钥：通过密码 = **' *`password`* '** 打开主密钥解密。</span><span class="sxs-lookup"><span data-stu-id="78b9d-148">When an encrypted database is first attached to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the database owner must open the master key of the database by executing the following statement: OPEN MASTER KEY DECRYPTION BY PASSWORD = **'*`password`*'**.</span></span> <span data-ttu-id="78b9d-149">建议您通过执行下面的语句对主密钥启用自动解密：ALTER MASTER KEY ADD ENCRYPTION BY SERVICE MASTER KEY。</span><span class="sxs-lookup"><span data-stu-id="78b9d-149">We recommend that you enable automatic decryption of the master key by executing the following statement: ALTER MASTER KEY ADD ENCRYPTION BY SERVICE MASTER KEY.</span></span> <span data-ttu-id="78b9d-150">有关详细信息，请参阅 [CREATE MASTER KEY (Transact-SQL)](/sql/t-sql/statements/create-master-key-transact-sql) 和 [ALTER MASTER KEY (Transact-SQL)](/sql/t-sql/statements/alter-master-key-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="78b9d-150">For more information, see [CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql) and [ALTER MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-master-key-transact-sql).</span></span>  
  
 <span data-ttu-id="78b9d-151">附加日志文件的要求在某些方面取决于数据库是读写的还是只读的，如下所示：</span><span class="sxs-lookup"><span data-stu-id="78b9d-151">The requirement for attaching log files depends partly on whether the database is read-write or read-only, as follows:</span></span>  
  
-   <span data-ttu-id="78b9d-152">对于读写数据库，通常可以附加新位置中的日志文件。</span><span class="sxs-lookup"><span data-stu-id="78b9d-152">For a read-write database, you can usually attach a log file in a new location.</span></span> <span data-ttu-id="78b9d-153">不过，在某些情况下，重新附加数据库需要使用其现有的日志文件。</span><span class="sxs-lookup"><span data-stu-id="78b9d-153">However, in some cases, reattaching a database requires its existing log files.</span></span> <span data-ttu-id="78b9d-154">因此，请务必保留所有分离的日志文件，直到在不需要这些日志文件的情况下成功附加了数据库。</span><span class="sxs-lookup"><span data-stu-id="78b9d-154">Therefore, it is important to always keep all the detached log files until the database has been successfully attached without them.</span></span>  
  
     <span data-ttu-id="78b9d-155">如果读写数据库具有单个日志文件，并且您没有为该日志文件指定新位置，附加操作将在旧位置中查找该文件。</span><span class="sxs-lookup"><span data-stu-id="78b9d-155">If a read-write database has a single log file and you do not specify a new location for the log file, the attach operation looks in the old location for the file.</span></span> <span data-ttu-id="78b9d-156">如果找到了旧日志文件，则无论数据库上次是否完全关闭，都将使用该文件。</span><span class="sxs-lookup"><span data-stu-id="78b9d-156">If it is found, the old log file is used, regardless of whether the database was shut down cleanly.</span></span> <span data-ttu-id="78b9d-157">但是，如果未找到旧文件日志，数据库上次是完全关闭且现在没有活动日志链，则附加操作将尝试为数据库创建新的日志文件。</span><span class="sxs-lookup"><span data-stu-id="78b9d-157">However, if the old log file is not found and if the database was shut down cleanly and has no active log chain, the attach operation attempts to build a new log file for the database.</span></span>  
  
-   <span data-ttu-id="78b9d-158">如果附加的主数据文件是只读的，则 [!INCLUDE[ssDE](../../includes/ssnoversion-md.md)] 无法更新主文件中存储的日志位置。</span><span class="sxs-lookup"><span data-stu-id="78b9d-158">If the primary data file being attached is read-only, the [!INCLUDE[ssDE](../../includes/ssnoversion-md.md)] cannot update the log location stored in the primary file.</span></span>  
  
  
  
###  <a name="metadata-changes-on-attaching-a-database"></a><a name="Metadata"></a> <span data-ttu-id="78b9d-159">附加数据库时的元数据更改</span><span class="sxs-lookup"><span data-stu-id="78b9d-159">Metadata Changes on Attaching a Database</span></span>  
 <span data-ttu-id="78b9d-160">分离再重新附加只读数据库后，会丢失有关当前差异基准的备份信息。</span><span class="sxs-lookup"><span data-stu-id="78b9d-160">When a read-only database is detached and then reattached, the backup information about the current differential base is lost.</span></span> <span data-ttu-id="78b9d-161">“差异基准”  是数据库或其文件或文件组子集中所有数据的最新完整备份。</span><span class="sxs-lookup"><span data-stu-id="78b9d-161">The *differential base* is the most recent full backup of all the data in the database or in a subset of the files or filegroups of the database.</span></span> <span data-ttu-id="78b9d-162">如果没有基准备份信息， **master** 数据库会变得与只读数据库不同步，这样之后进行的差异备份可能会产生意外结果。</span><span class="sxs-lookup"><span data-stu-id="78b9d-162">Without the base-backup information, the **master** database becomes unsynchronized with the read-only database, so differential backups taken thereafter may provide unexpected results.</span></span> <span data-ttu-id="78b9d-163">因此，如果对只读数据库使用差异备份，在重新附加数据库后，应通过进行完整备份来建立新的差异基准。</span><span class="sxs-lookup"><span data-stu-id="78b9d-163">Therefore, if you are using differential backups with a read-only database, you should establish a new differential base by taking a full backup after you reattach the database.</span></span> <span data-ttu-id="78b9d-164">有关差异备份的信息，请参阅[差异备份 (SQL Server)](../backup-restore/differential-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="78b9d-164">For information about differential backups, see [Differential Backups &#40;SQL Server&#41;](../backup-restore/differential-backups-sql-server.md).</span></span>  
  
 <span data-ttu-id="78b9d-165">附加时，数据库会启动。</span><span class="sxs-lookup"><span data-stu-id="78b9d-165">On attach, database startup occurs.</span></span> <span data-ttu-id="78b9d-166">通常，附加数据库时会将数据库重置为它分离或复制时的状态。</span><span class="sxs-lookup"><span data-stu-id="78b9d-166">Generally, attaching a database places it in the same state that it was in when it was detached or copied.</span></span> <span data-ttu-id="78b9d-167">但是，附加和分离操作都会禁用数据库的跨数据库所有权链接。</span><span class="sxs-lookup"><span data-stu-id="78b9d-167">However, attach-and-detach operations both disable cross-database ownership chaining for the database.</span></span> <span data-ttu-id="78b9d-168">有关如何启用链接的详细信息，请参阅 [cross db ownership chaining 服务器配置选项](../../database-engine/configure-windows/cross-db-ownership-chaining-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="78b9d-168">For information about how to enable chaining, see [cross db ownership chaining Server Configuration Option](../../database-engine/configure-windows/cross-db-ownership-chaining-server-configuration-option.md).</span></span> <span data-ttu-id="78b9d-169">此外，附加数据库时，TRUSTWORTHY 均设置为 OFF。</span><span class="sxs-lookup"><span data-stu-id="78b9d-169">Also, TRUSTWORTHY is set to OFF whenever the database is attached.</span></span> <span data-ttu-id="78b9d-170">有关如何将 TRUSTWORTHY 设置为 ON 的详细信息，请参阅 [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="78b9d-170">For information about how to set TRUSTWORTHY to ON, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
### <a name="backup-and-restore-and-attach"></a><span data-ttu-id="78b9d-171">备份、还原及附加</span><span class="sxs-lookup"><span data-stu-id="78b9d-171">Backup and Restore and Attach</span></span>  
 <span data-ttu-id="78b9d-172">与任何完全或部分脱机的数据库一样，不能附加正在还原文件的数据库。</span><span class="sxs-lookup"><span data-stu-id="78b9d-172">Like any database that is fully or partially offline, a database with restoring files cannot be attached.</span></span> <span data-ttu-id="78b9d-173">如果停止了还原顺序，则可以附加数据库。</span><span class="sxs-lookup"><span data-stu-id="78b9d-173">If you stop the restore sequence, you can attach the database.</span></span> <span data-ttu-id="78b9d-174">然后，可以重新启动还原顺序。</span><span class="sxs-lookup"><span data-stu-id="78b9d-174">Then, you can restart the restore sequence.</span></span>  
  
###  <a name="attaching-a-database-to-another-server-instance"></a><a name="OtherServerInstance"></a> <span data-ttu-id="78b9d-175">将数据库附加到其他服务器实例</span><span class="sxs-lookup"><span data-stu-id="78b9d-175">Attaching a Database to Another Server Instance</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="78b9d-176">无法在早期版本的 SQL Server 中附加由较新版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 创建的数据库。</span><span class="sxs-lookup"><span data-stu-id="78b9d-176">A database created by a more recent version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot be attached in earlier versions.</span></span>  
  
 <span data-ttu-id="78b9d-177">将数据库附加到其他服务器实例时，为了给用户和应用程序提供一致的体验，您最好在其他服务器实例上为数据库重新创建部分或全部元数据（例如登录名和作业）。</span><span class="sxs-lookup"><span data-stu-id="78b9d-177">When you attach a database onto another server instance, to provide a consistent experience to users and applications, you might have to re-create some or all of the metadata for the database, such as logins and jobs, on the other server instance.</span></span> <span data-ttu-id="78b9d-178">有关详细信息，请参阅 [当数据库在其他服务器实例上可用时管理元数据 (SQL Server)](manage-metadata-when-making-a-database-available-on-another-server.md)。</span><span class="sxs-lookup"><span data-stu-id="78b9d-178">For more information, see [Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](manage-metadata-when-making-a-database-available-on-another-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="78b9d-179">相关任务</span><span class="sxs-lookup"><span data-stu-id="78b9d-179">Related Tasks</span></span>  
 <span data-ttu-id="78b9d-180">**分离数据库**</span><span class="sxs-lookup"><span data-stu-id="78b9d-180">**To detach a database**</span></span>  
  
-   [<span data-ttu-id="78b9d-181">sp_detach_db (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="78b9d-181">sp_detach_db &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-detach-db-transact-sql)  
  
-   [<span data-ttu-id="78b9d-182">分离数据库</span><span class="sxs-lookup"><span data-stu-id="78b9d-182">Detach a Database</span></span>](detach-a-database.md)  
  
 <span data-ttu-id="78b9d-183">**附加数据库**</span><span class="sxs-lookup"><span data-stu-id="78b9d-183">**To attach a database**</span></span>  
  
-   [<span data-ttu-id="78b9d-184">CREATE DATABASE (SQL Server Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="78b9d-184">CREATE DATABASE &#40;SQL Server Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
-   [<span data-ttu-id="78b9d-185">附加数据库</span><span class="sxs-lookup"><span data-stu-id="78b9d-185">Attach a Database</span></span>](attach-a-database.md)  
  
-   [<span data-ttu-id="78b9d-186">sp_attach_db (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="78b9d-186">sp_attach_db &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-attach-db-transact-sql)  
  
-   [<span data-ttu-id="78b9d-187">sp_attach_single_file_db (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="78b9d-187">sp_attach_single_file_db &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-attach-single-file-db-transact-sql)  
  
 <span data-ttu-id="78b9d-188">**使用分离和附加操作升级数据库**</span><span class="sxs-lookup"><span data-stu-id="78b9d-188">**To upgrade a database using detach and attach operations**</span></span>  
  
-   [<span data-ttu-id="78b9d-189">使用分离和附加来升级数据库 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="78b9d-189">Upgrade a Database Using Detach and Attach &#40;Transact-SQL&#41;</span></span>](upgrade-a-database-using-detach-and-attach-transact-sql.md)  
  
 <span data-ttu-id="78b9d-190">**使用分离和附加操作移动数据库**</span><span class="sxs-lookup"><span data-stu-id="78b9d-190">**To move a database using detach and attach operations**</span></span>  
  
-   [<span data-ttu-id="78b9d-191">使用分离和附加来移动数据库 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="78b9d-191">Move a Database Using Detach and Attach &#40;Transact-SQL&#41;</span></span>](move-a-database-using-detach-and-attach-transact-sql.md)  
  
 <span data-ttu-id="78b9d-192">**删除数据库快照**</span><span class="sxs-lookup"><span data-stu-id="78b9d-192">**To delete a database snapshot**</span></span>  
  
-   [<span data-ttu-id="78b9d-193">删除数据库快照 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="78b9d-193">Drop a Database Snapshot &#40;Transact-SQL&#41;</span></span>](drop-a-database-snapshot-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="78b9d-194">另请参阅</span><span class="sxs-lookup"><span data-stu-id="78b9d-194">See Also</span></span>  
 [<span data-ttu-id="78b9d-195">数据库文件和文件组</span><span class="sxs-lookup"><span data-stu-id="78b9d-195">Database Files and Filegroups</span></span>](database-files-and-filegroups.md)  
  
  
